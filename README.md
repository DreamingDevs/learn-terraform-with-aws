# Learn Terraform with AWS

Few of the basic details related to Infrastructure as Code (IaC) which might serve as a quick refresher of basic concepts.

<br />

| Learning Day | Read about... | 
|--|--|
| Day 0 | [What is IaC?](./docs/iac_basics.md#what-is-iac) <br /> Let's get some basics... |
| Day 0 | [Declarative vs Imperative Programming Models](./docs/iac_basics.md#declarative-vs-imperative-programming-models) <br /> This is pretty much important stuff, do not skip. |
| Day 0 | [What is Terraform?](./docs/iac_basics.md#what-is-terraform) <br /> Get some quick insights on what is it all about Terraform. |

<br />

Let's get started by setting up our local development environment with development tools. Instructions are based for macOS.

<br />

| Learning Day | Let's get started... | 
|--|--|
| Day 0 | [Development Tools Setup](./docs/dev_machine_setup.md#development-tools-setup) <br /> You will have to set these up for sure. |
| Day 0 | [Terminal Setup](./docs/dev_machine_setup.md#terminal-setup) <br /> Do not get bothered, completely optional, skip if you want. |

<br />

Are you looking forward to create an AWS account to get started with Terraform? Follow through my below experiences.

<br />

| Learning Day | Setting up AWS account... | 
|--|--|
| Day 1 | [Create an AWS Account](./docs/aws_setup.md#create-an-aws-account) <br /> This is required for learning, so create it.|
| Day 1 | [Create an IAM user group, user, role, and policy to provide access to Terraform](./docs/aws_setup.md#create-an-iam-user-group-user-role-and-policy-to-provide-access-to-terraform) <br /> How do we test our IAM User and related configuration? Take a pause, for now review the concepts of this section and understand them. We will test our IAM User tomorrow.|
| Day 1 | [Configure Terraform with AWS Credentials](./docs/aws_setup.md#configure-terraform-with-aws-credentials) <br /> Let's configure Terraform on our local machine with the IAM User credentials which we created in previous section.|
| Day 1 | [Setup shared configuration for Terraform](./docs/aws_setup.md#setup-shared-configuration-for-terraform) <br /> Let's setup the shared configuration for terraform on our local machine.|

<br />

Enjoying the flow so far? Finding it useful? Let's continue to the next phase. With you having successfully completed the first basic Terraform execution, we will now focus on the basics of Terraform.

<br />

| Learning Day | Sorting out Terraform basics... | 
|--|--|
| Day 4 | [terraform init](./docs/terraform_basics.md#terraform-init) <br /> Initialize the terraform project working directory with all depedencies. |
| Day 4 | [terraform fmt](./docs/terraform_basics.md#terraform-fmt) <br /> Format the terraform config files with canonical format and style. |