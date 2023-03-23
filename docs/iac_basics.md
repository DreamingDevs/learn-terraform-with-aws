# Infrastructure as Code (IaC) basics

This document provides some basic information related to IaC and associated concepts.

> NOTE: This document do not outlines all the concepts of IaC, but only talks about the absolutely required ones.

<br />

## What is IaC?

IaC is all about provisioning, configuring and maintaining the infra resources through code. 

Now why do we need code to do all these activities? We need because, with code, we can apply all the engineering and delivery best practices (for example, reliability, resiliency, reusability, testability, maintainability etc.) from our industry's experiences of product and application development.

<br />

## Declarative vs Imperative Programming Models

Declarative way of programming defines the final result / state of the infra and the tooling like Terraform takes care of reaching to that final result / state.

Imperative way is more of defininig the granular steps / instructions which the tool should follow to achieve the final result / state.

As imperative way is more instructions based the scope of reusability of the same set of instructions over and over on the same infra resources is very minimal. Also keeping the imperative steps up-to-date with evolving infra is quite challenging especially when it comes to maintaining the current state of the infra resource. 

Even though declarative approach solves the afore mentioned challenges in quite easy way, it gets burdened to maintain the current state of the infra resource. However the major advantage of declarative approach is its ability to amend the infra resources with a new state in a easy, understandable and simple langugage.

IMO, both the approaches suits different usecases of the system design especially with varying scale and complexity of the system. Personally I recommend declarative programming model for maintaining infra resources.