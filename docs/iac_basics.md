# Infrastructure as Code (IaC) basics

This document provides some basic information related to IaC and associated concepts.

> NOTE: This document do not outlines all the concepts of IaC, but only talks about the absolutely required ones.

<br />

## What is IaC?

IaC is all about provisioning, configuring and maintaining the infra resources through code. 

Now why do we need code to do all these activities? We need because, with code, we can apply all the engineering and delivery best practices (for example, reliability, resiliency, reusability, testability, maintainability etc.) from our industry's experiences of product and application development.

<br />

## Declarative vs Imperative Programming Models

Declarative way of programming defines the final result / state of the infra and the tooling like `Terraform`, `CloudFormation` etc takes care of reaching to that final result / state.

Imperative way is more of defininig the granular steps / instructions which the tool should follow to achieve the final result / state. Tools like `Ansible`, `Chef` support both declarative and imperative programming styles.

> NOTE: Tools like `Ansible`, `Chef`, `Puppet` are primarily used for configuration management instead of infra provisioning.

As imperative way is more instructions based the scope of reusability of the same set of instructions over and over on the same infra resources is very minimal. Also keeping the imperative steps up-to-date with evolving infra (Configuration Drifts) is quite challenging especially when it comes to maintaining the current state of the infra resource. 

Even though declarative approach solves the afore mentioned challenges in quite easy way through State Management, it is also a burden to maintain the current state of the infra resource. However the major advantage of declarative approach is its ability to amend the infra resources with a new state in a easy, understandable and simple langugage. Also declarative approach is idempotent, it always takes the infra to the same defined state.

IMO, both the approaches suits different usecases of the system design especially with varying scale and complexity of the system. Personally I recommend declarative programming model for maintaining infra resources.

<br />

## What is Terraform?

Terraform is an open-source infrastructure-as-code tool created by HashiCorp. We use declarative programming configuration known as HashiCorp Configuration Language, or optionally JSON, to define, provision and maintain the infrastructure (typically cloud infra).

Few of its key capabilities are - 
 
 - Compose infrastructure as code
 - Supports all major cloud providers
 - Create workflows with relevant CI/CD tooling
 - Automate IT operations (rollforward, rollback, backup etc.) through CLI
 - State managemnent (including Remote) of infra
 - Integrated security and compliance controls
 - Apply engineering best practices to infra operations
 - Eases incremental infra changes
 - Improves testability of infra
 - Enhances reliability of infra confiuguration
 - Reusability of infra code through modules
 - Simplifies complex infra topologies (K8s, mulit-cloud, networking etc)
 - Provides secret protection and rotation
 - Define policies for infra
 - Compatibility with programming languages like C#, GO etc.
 - Support for Plugins and Cloud Development Kit (CDK)
 - Available as Terraform Cloud and Enterprise (with Sentinel)
 - Provides pre-build and ready to use catalog through Terraform Registry 

