# Continuous integration & delivery

CI/CD is used across all projects at the Data Shed as a way of streamlining
deployments, automatically testing code and protecting failing tests from
bypassing merge pipelines.

The variety of work that comes through the Shed varies from project to project.
Having clients with different tech stacks and subscriptions to various providers
means not every pipeline looks the same. The Data Shed still applies the same
general set of functional tooling across projects even though the tools
themselves may differ in implementation. The Shed seeks to automate version
control, packaging, testing, formatting, and linting code. The Data Shed makes
heavy use of [terraform](../standards/terraform-standards.md)

Tools used in the past:

- CircleCI
- Github Actions
- Terraform
- Terragrunt
- Gitlab Runners
- Bitbucket

--8<-- "includes/acronyms.md"
