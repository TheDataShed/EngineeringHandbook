# Terraform

[Terraform](https://www.terraform.io/) is an infrastructure-as-code tool
developed by [HashiCorp](https://www.hashicorp.com/).

At The Data Shed, this has become the de facto standard tool for provisioning
infrastructure on our projects. Thanks to its declarative language and
extensibility through
"[providers](https://www.terraform.io/language/providers)" for every possible
service, it is both versatile and highly maintainable.

## Versions

Terraform reached a stable 1.0 version only
[relatively recently](https://www.hashicorp.com/blog/announcing-hashicorp-terraform-1-0-general-availability).
While Terraform does now offer a stability guarantee, all projects:

- SHOULD aim to use the most recent version and provide an upgrade path to
  maintain this;
- MUST define an upgrade path if on an older version.

## Code Style

All Terraform code MUST be formatted as per the provided standard (this may
change when upgrading versions and this MUST be considered when doing so):

```sh
terraform fmt
```

This MUST be enforced in any CI/CD pipelines.

## Static Code Analysis

There are several tools available for static code analysis, whether for linting
or more thorough Static Application Security Testing.

- [`terraform validate`](https://www.terraform.io/cli/commands/validate)
- [`checkov`](https://github.com/bridgecrewio/checkov)
- [`terrascan`](https://github.com/accurics/terrascan)
- [`tflint`](https://github.com/terraform-linters/tflint)
- [`tfsec`](https://github.com/aquasecurity/tfsec)

In some cases these tools will suggest actions inappropriate for a particular
project; each, however, can allow these rules to be ignored. Where this
happens, there MUST be appropriate explanation.

Any project using Terraform SHOULD integrate these into their development
workflows. Where any issues are flagged, any project MUST provide a path for
remedial action.

## `pre-commit`

As with all other languages and frameworks, projects SHOULD make use of the
[`pre-commit`](https://pre-commit.com/) framework.

With regard to Terraform, there are some specific hooks which can be used:

- [`pre-commit-terraform`](https://github.com/antonbabenko/pre-commit-terraform):
  this has hooks for several of the aforementioned tools (and many more.)
- [`checkov`](https://github.com/bridgecrewio/checkov): although
  `pre-commit-terraform` includes a hook for `checkov`, this manages
  installation of the binary too, making it simpler to use.
