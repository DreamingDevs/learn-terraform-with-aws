## Create an AWS Account

<br />

 - Navigate to [Create an AWS Account](https://portal.aws.amazon.com/billing/signup#/start/email) page. 
 - Enter a valid email id and root username. Proceed to verify the email id.
 - Provide contact and address information.
 - Enter Credit / Debit card information for billing purpose. Proceed to verify the card details through the respective bank's authentication system (typically OTP).
    - A nominal fee of 2 INR (Indian currency) will be deducted to verify the authenticity of the card.
    - Going forward card will not charged if the usage is within the limits of free tier. But once exceeded, card will be charged based on usage.
 - Confirm the identity by entering mobile no. and verifying it with OTP.
 - Lastly select the `Basic Support - Free plan` as we only need this AWS account of executing our exercises.

<br />

Let's enable MFA for our root user. Login at [AWS Console](https://console.aws.amazon.com/) with root user email and password. Go to IAM resource (through global search in AWS console).

<br />

![IAM Root user MFA](../images/iam_root_user_mfa.png "IAM Root user MFA")

<br />

Proceed with the next flow of steps to enable MFA through apps like Google Authenticator, OKTA Verify, Duo Security etc.

<br />

![IAM Root user MFA Enabled](../images/iam_root_user_mfa_enabled.png "IAM Root user MFA Enabled")

<br /> 


## Create an IAM user group, user, role, and policy to provide access to Terraform

<br />

When we created an AWS account, a root user account was provisioned for us. This account has the highest possible privileges, through which it can administer the entire AWS account. Hence leveraging the root user account for specific activities like IaC automations, etc., is highly unadvisable. We will create an appropriate IAM user with a specific role and policies with limited privileges that can be used for IaC automations through Terraform.

> NOTE: We can leverage Terraform to create the IAM user, role, and policies. However, as this is the first step towards setting up Terraform, we will proceed to manually create the required AWS resources. Later in this repo, when we work on the IAM user related automations, we will revisit and address this tech debt.

> NOTE: To keep things simple, we will create a policy which will provide limited access to S3 service. This can be extended to all other services which `tf_user` needs to access.

Let's get started by creating an IAM user group at the [AWS Console](https://console.aws.amazon.com/).

- Enter `tf_user_group` as name for the group
- No additional configuration is required, proceed to create the group

<br />

Created `tf_user_group`.

<br />

![Created IAM Terraform User Group](../images/iam_tf_user_group_created.png "Created IAM Terraform User Group")

<br />

Now lets proceed to create an IAM user.

- Enter `tf_user` as name
- Associate the `tf_user` with `tf_user_group`
- No additional configuration is required, review and create the user

<br />

Created `tf_user`.

<br />

![IAM Terraform user created](../images/iam_tf_user_created.png "Review and create Terraform user")

<br />

Let's enable access keys for `tf_user` using which Terraform can access AWS and maintain resources. 

- Navigate to `Security Credentials` section of `tf_user`
- Select `create access key` option
- Select `Command Line Interface (CLI)` as the use case
- Create access key
- Copy the generated Access key and Secret. **Store them in a SECURE PLACE**.
   - We will use these credentials in a while.

<br />

![IAM Terraform user with Access Key](../images/iam_tf_user_with_access_key.png "IAM Terraform user with Access Key")

<br />

As the next step, we will create an AWS Policy. This policy will only have least possible privileges which are absolutely required for terraform activities. This way we can limit the overall access of terraform user to AWS resources.

> NOTE: As already mentioned aboved, to keep things simple, we will create a policy which will provide limited access to S3 service. This can be extended to all other services which `tf_user` needs to access.

- Select `JSON` option after selecting the `Create policy`.
- Enter below JSON which will 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "tfPolicy",
            "Effect": "Allow",
            "Action": [
                "s3:CreateBucket",
                "s3:ListBucket",
                "s3:DeleteBucketPolicy",
                "s3:GetBucketPolicy",
                "s3:PutObject",
                "s3:GetObject",
                "s3:PutBucketPolicy",
                "s3:DeleteAccessPointPolicy",
                "s3:DeleteObject",
                "s3:PutAccessPointPolicy",
                "s3:GetAccessPointPolicy",
                "s3:DeleteBucket",
                "s3:GetObjectVersion"
            ],
            "Resource": "*"
        }
    ]
}
```
- Review and create by entering `tf_policy` as name (`description` and `tags` are optional). 

<br />

![IAM Terraform user policy created](../images/iam_tf_user_policy_created.png "IAM Terraform user policy created")

<br /> 

Now we will proceed to create an IAM Role which our `tf_user` can assume for provisioning and maintaining AWS resources. The IAM role will have the `tf_policy` attached to it for providing access to `tf_user`.

- Select `Custom trust policy`
- Enter below statement as the policy.

```
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "tf_assume_role",
			"Effect": "Allow",
			"Principal": {
				"AWS": "arn:aws:iam::XXXXXXXXXXXX:user/tf_user"
			},
			"Action": "sts:AssumeRole"
		}
	]
}
```
- Select `tf_policy` in Add permissions section.
- Create role by entering `tf_role` as the name (`description` and `tags` are optional). 

<br />

![IAM Terraform user role created](../images/iam_tf_user_role_created_1.png "IAM Terraform user role created")

<br />

![IAM Terraform user role created](../images/iam_tf_user_role_created_2.png "IAM Terraform user role created")