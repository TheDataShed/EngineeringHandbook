# Continuous Integration & Delivery

> Continuous integration and delivery bridges the gaps between development and
> operation activities and teams by enforcing automation in building, testing
> and deployment of applications. CI/CD services compile the incremental code
> changes made by developers, then link and package them into software
> deliverables. Automated tests verify the software functionality, and automated
> deployment services deliver them to end users. The aim is to increase early
> defect discovery, increase productivity, and provide faster release cycles.
> The process contrasts with traditional methods where a collection of software
> updates were integrated into one large batch before deploying the newer
> version. Modern-day DevOps practices involve continuous development,
> continuous testing, continuous integration, continuous deployment and
> continuous monitoring of software applications throughout its development life
> cycle. The CI/CD practice, or CI/CD pipeline, forms the backbone of modern day
> DevOps operations. [[1](https://en.wikipedia.org/wiki/CI/CD)]

CI/CD is used across all projects at The Data Shed as a way of streamlining
deployments, automatically testing code and protecting failing tests from
bypassing merge pipelines.

The variety of work that comes through The Shed varies from project to project.
Having clients with different tech stacks and subscriptions to various providers
means not every pipeline looks the same. The Data Shed still applies the same
general set of functional tooling across projects even though the tools
themselves may differ in implementation. The Shed seeks to automate version
control, packaging, testing, formatting, and linting code.

Tools used in the past:

- Azure DevOps
- Bitbucket
- CircleCI
- Github Actions
- Gitlab Runners
- Jenkins
- [Terraform](../standards/terraform-standards.md)
- Terragrunt

--8<-- "includes/acronyms.md"
