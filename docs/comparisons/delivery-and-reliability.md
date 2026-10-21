# Delivery and Reliability: Common Comparisons

**Navigation:** [Home](../../README.md) | [Topic Index](../index.md) | [Comparisons](index.md)

## Git and GitHub

Git is version-control software that records repository history. GitHub is a hosted service built around Git repositories, adding collaboration features such as pull requests, issues, and workflows. Git also works without GitHub; using GitHub does not change Git's role as a version-control system.

## CI, Continuous Delivery, and Continuous Deployment

| Practice | What it means | Release gate |
|---|---|---|
| Continuous Integration (CI) | Integrate changes frequently and run automated checks. | Checks report whether changes are healthy. |
| Continuous Delivery | Keep changes in a deployable state. | Production release may require an explicit decision. |
| Continuous Deployment | Automatically release each qualifying change to production. | Automated rules and checks are the release gate. |

*CD* is ambiguous; expand it. A workflow that builds and tests code is CI even if it never deploys.

## Reliability and Availability

Availability is the proportion of time a service is usable under a defined measurement. Reliability is whether it performs the intended function correctly over time. A service that responds quickly but returns incorrect data may be available and unreliable. Measurement windows and user-visible criteria matter.

## Virtual Machine and Container

| Virtual machine | Container |
|---|---|
| Emulates a computer platform and usually runs a guest OS kernel. | Packages and isolates processes; common containers share the host kernel. |
| Provides a separate guest OS boundary, with platform-specific overhead and controls. | Starts quickly and packages application dependencies, but is not a separate kernel by default. |
| Example: run a Linux guest on a Windows host. | Example: run an isolated service process from an image on a Linux host. |

Neither term by itself guarantees security or isolation strength. Configuration, host, hypervisor, kernel, and privileges matter.
