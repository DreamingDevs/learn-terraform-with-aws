# Understanding the basics of Terraform

This document shares the basic information and knowledge of Terraform. Basics are going to be basics, so no hands-on labs are present in this document. Feel free to quickly skim through the doc.

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

## Terraform Fmt

`fmt` command is used to format the terraform configuration files with canonical format and style. It is used to bring consistency across all terraform files to follow the terraform recommended style practices.

It is used to fix the indentation issues, aligning assignment `equals to` spaces etc. However it will not remove empty lines, upper to lower case etc. This command also supports previewing the changes. 

Usage of the command - 

```
terraform fmt -recursive
```

> NOTE: This is not a mandatory command which needs to executed, but I recommend to execute it as part of the automations to maintain consistent style.

<br />



