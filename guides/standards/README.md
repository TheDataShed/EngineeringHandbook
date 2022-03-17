# Standards

This is the single source of truth for coding and naming standards at The Data
Shed.

- [Python](/guides/standards/python-standards.md)
- [SQL](/guides/standards/sql-standards.md) #TODO
- [Terraform](/guides/standards/terraform-standards.md)

## General

While the above describe standards and tooling appropriate to each language or
framework, there are some which apply to all projects.

## `pre-commit`

Git [hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks) are a
means by which automated action can be taken for certain events in the Git
lifecycle.

[`pre-commit`](https://pre-commit.com/) is a framework for managing a variety
of tools, specifically for the
[`pre-commit`](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks#_committing_workflow_hooks)
hook.

- all projects SHOULD make use of `pre-commit`;
- any project using `pre-commit` MUST make use of its
  [`autoupdate`](https://pre-commit.com/#updating-hooks-automatically) feature;
- any project using `pre-commit` MUST
  [run all hooks](https://pre-commit.com/#usage) as part of the CI/CD pipeline.

There are some tools which SHOULD be used on every project, where appropriate:

- [`markdownlint-cli`](https://github.com/igorshubovych/markdownlint-cli): most
  projects have a `README.md` and such documents should be validated by
  [`markdownlint`](https://github.com/DavidAnson/markdownlint);
- [`detect-secrets`](https://github.com/Yelp/detect-secrets): needless to say,
  the accidental addition of sensitive data to a project should be avoided;
- [`gitleaks`](https://github.com/zricethezav/gitleaks/): similar to
  `detect-secrets`, this aims to prevent to accidental addition of sensitive
  values.
