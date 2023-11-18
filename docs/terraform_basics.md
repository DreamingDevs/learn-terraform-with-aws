# Understanding the basics of Terraform

This document shares the basic information and knowledge of Terraform. Basics are going to be basics, so no hands-on labs are present in this document. Feel free to quickly skim through the doc.

<br />

## Providers

A provider in Terraform is an abstraction of the upstream API using which we can interact with different cloud providers and SaaS platforms. Providers enable Terraform with different `resource` types which can be managed at target platform. Providers are typically managed by - Hashicorp (official), Partners (verified organization), and community groups.

When we execute `terraform init`, providers are downloaded (if not exists) to `.terraform` directory. Following is the provider configuration for AWS provider.

`required_providers` section is required for the providers which are managed by partners and community. It is used to specify source and version information of the provider. We can still use this configuration with hashicorp providers as well.

NOTE: Provider version is different from Terraform version. Provider versions keep changing based on the cadence of cloud providers and SaaS platforms. 

We can configure the provider with the `profile` from the `shared_config_files` and `shared_credentials_files` which provides required configuration and credentials for provider to work.

```
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}

provider "aws" {
  shared_config_files      = ["${pathexpand("~/.aws/config")}"]
  shared_credentials_files = ["${pathexpand("~/.aws/credentials")}"]
  profile                  = "development"

  assume_role {
    role_arn = "arn:aws:iam::XXXXXXXXXXXX:role/tf_role"
  }
}
```

<br />

## Terraform Init

`init` is used to prepare the terraform working directory by identifying, fetching and resolving all dependencies of our terraform code. 

Usage of the command - 

```
terraform init
```

Primary activities of init are - 

- Backend Initialization
    - Creates a state file at the backend to keep track of current state of the infra. There are options in this command to resolve conflicting states. This command creates state files at both local working directory and remote backend (typically a S3 bucket).
- Module Installation
    - Installs modules which are not present in the working directory. This command can also force to reload all the modules.
- Plugin Installation
    - Doanload all the dependent plugins, for example Azure, AWS providers. The plugins (latest or specific version) can be downloaded from terraform registry or from any source which can be specified.

We can always run this command multiple times, but it is recommended to run it only when any of above mentioned aspects undergo a change.

<br />

## Terraform Plan

`plan` creates an execution plan and previews the changes which are going to be applied by Terraform at the target infra provider. 

When we issue plan command, Terraform fetches the current state from remote provider and compares it with the latest configuration files. Finally the command proposes the list of changes which needs to be applied to make the remote objects match the latest configuration.

NOTE: 
- `-out=file` option is used to output the plan to a file.
- `-destroy` option is used to create a plan to destroy all remote objects that currently exist.
- `-refresh-only` option is used to update the state file to match changes from the remote provider.

```
-- Display the plan
terraform plan

-- Output the plan to a file
terraform plan -out=tf.plan
terraform show -no-color tf.plan > tfplan.txt
```

<br />

## Terraform Apply

<br />

## Terraform Destroy

<br />

## Terraform Fmt

`fmt` command is used to format the terraform configuration files with canonical format and style. It is used to bring consistency across all terraform files to follow the terraform recommended style practices.

It is used to fix the indentation issues, aligning assignment `equals to` spaces etc. However it will not remove empty lines, upper to lower case etc. This command also supports previewing the changes. 

Usage of the command - 

```
terraform fmt -recursive
```

> NOTE: This is not a mandatory command which needs to executed, but I recommend to execute it as part of the automations to maintain consistent style.

<br />



