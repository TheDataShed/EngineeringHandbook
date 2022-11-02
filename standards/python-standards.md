---
tags:
  - standards
---

# Python

Python is becoming more ubiquitous across The Data Shed engineering space, often
the first choice of language for a new project.

The purpose of this page is to outline some best practices for Python
development across t'Shed in order to facilitate standardisation and whatnot.

We should push these standards where we own the project.

For non-Shed-owned projects we should aim to follow existing standards set out
🤷‍♂️

## Version

### Python 3

The default version you should use is the latest currently supported across all
3 major cloud providers
([Azure](https://docs.microsoft.com/en-us/azure/azure-functions/functions-reference-python?tabs=asgi%2Cazurecli-linux%2Capplication-level#python-version),
[AWS](https://docs.aws.amazon.com/lambda/latest/dg/lambda-python.html),
[GCP](https://cloud.google.com/functions/docs/concepts/python-runtime).) At the
time of writing, this is **3.9**.

If your project does not currently use this version then you need to schedule a
work item to upgrade. The version should be maintained as per the above and this
should be accommodated in every project roadmap.

### Python 2

**Never 2**. Shedders don't let Shedders use Python 2.

## Install

While Python is pre-installed or easily available in many operating systems, we
recommend: [`pyenv`](https://github.com/pyenv/pyenv).

**Note**: it should be installed using the
[`pyenv-installer`](https://github.com/pyenv/pyenv-installer) tool.

See the `pyenv`
[documentation](https://github.com/pyenv/pyenv#choosing-the-python-version) on
managing multiple Python versions for different projects.

### Virtual Environments

For managing virtual environments using `pyenv`, use the
[`pyenv-virtualenv`](https://github.com/pyenv/pyenv-virtualenv) plugin.
**Note**: this is installed by default when using the above `pyenv-installer`
tool.

See the `pyenv-virtualenv`
[documentation](https://github.com/pyenv/pyenv-virtualenv#activate-virtualenv)
on managing multiple virtual environments for different projects.

## Formatting

We should aim for consistency and predictability across our Python code.

### Black

Python code should be formatted using
[`black`](https://pypi.org/project/black/), using the latest
[stable](https://black.readthedocs.io/en/stable/the_black_code_style/index.html#stability-policy)
version.
[`Flake8`](https://flake8.pycqa.org/en/latest/) can be a useful tool for this.  

### Isort

Imports should be ordered as per [`isort`](https://pypi.org/project/isort/) (see
also the
[`black` compatibility guide](https://pycqa.github.io/isort/docs/configuration/black_compatibility.html).)
It effectively requires passing `--profile black` to the isort command in your
editor config.

Stick to the default 88 character length. It's easier to maintain across
projects and it's handy when splitting a window or terminal for editing and
still being able to see all the text in both files. In conjunction with isort,
we go from:

From:

```py
from statistics import mean
import typing as t


numbers = [1, 2, 4,
        2,10, 12]


def calculate_mean(numbers:t.List[t.Union[int,float]]) :
    return     mean(numbers)

```

To:

```py
import typing as t
from statistics import mean

numbers = [1, 2, 4, 2, 10, 12]


def calculate_mean(numbers: t.List[t.Union[int, float]]):
    return mean(numbers)
```

### Existing Projects

When introducing `black` to a new project (or upgrading to a more recent
version), make any formatting changes in an isolated merge-/pull-request. Don't
confuse formatting with changes in logic.

### Docstrings

- [Sphinx/Rst](https://sphinx-rtd-tutorial.readthedocs.io/en/latest/docstrings.html)
  style docstrings

[`darglint`](https://github.com/terrencepreilly/darglint) is a useful tool for
verifying that docstrings match the expected style (It works with both Sphinx
and Google style docstrings). It also adds Flake8 linting of doc strings if you
read the documentation on how to enable that.
[PEP-257](http://www.python.org/dev/peps/pep-0257/)

## Dependency Checking

- [`safety`](https://pyup.io/safety/) will check whether a Python project's
  dependencies have any known vulnerabilities.
  - **Note**: the free version of `safety` is only updated monthly and as such
    carries some risk. Alternative suggestions are encouraged.
- If a project is hosted on GitHub, their own
  [Dependabot](https://github.com/dependabot) should be used for the same
  purpose.

## Testing

[`pytest`](https://docs.pytest.org/) should be used for all new projects.

Existing projects should plan to migrate to `pytest` though this can be
facilitated by
[running any existing `unittest` tests with `pytest`](https://docs.pytest.org/en/6.2.x/unittest.html).
All new tests, however, should use `pytest`.

### Coverage

- the `pytest` plugin [`pytest-cov`](https://github.com/pytest-dev/pytest-cov)
  should be used to measure code coverage, ideally on all projects;
- [`diff_cover`](https://github.com/Bachmann1234/diff_cover) is suitable for
  existing projects, enforcing the required degree of test coverage for _only
  those lines changed_.

### Static Analysis

- [`bandit`](https://github.com/PyCQA/bandit) is a tool for identifying common
  security issues in Python and should be adopted into all relevant assurance
  pipelines.
- [`pytest-mypy`](https://github.com/dbader/pytest-mypy) can be used for static
  type-checking via [`mypy`](http://mypy-lang.org/).
- [`flake8`](https://flake8.pycqa.org/en/latest/) can be used for fast and
  generally fast errors with your code.

## `gitignore`

[`.gitignore`](https://www.toptal.com/developers/gitignore/api/windows,linux,macos,vim,emacs,sublimetext,intellij,pycharm,visualstudiocode,python)
file as provided by [gitignore.io](https://gitignore.io/).

The above should be used and any updates reflected in the template for all to
use.

Although [GitHub](https://github.com/github/gitignore) provides similar
templates, they are more specific, missing many of the ancillary files added by
OSs, IDEs, etc.

## Requirements

[`pip`](https://github.com/pypa/pip), making sure to update regularly to the
latest version.

Specifically, use the `python3 -m pip` variant for calling the `pip` module
directly.

## Other Asides

Some of the following fall outside the scope of this document but are included
until such time as similar documents exist to replace these next headings.

Others, such as the use of type hints in Python code, are currently only
recommendations, though this may change as tooling gains more adoption.

### README

All projects must include a README which is formatted as per the
[CommonMark](https://commonmark.org/) specification and validated using
[`markdownlint`](https://github.com/DavidAnson/markdownlint) (or
[`markdownlint-cli`](https://github.com/igorshubovych/markdownlint-cli)).

### `pre-commit`

[`pre-commit`](https://pre-commit.com/) is a framework for managing pre-commit
hooks in variety of languages, including pre-configured hooks for many of the
above tools. Its use is _highly_ encouraged.

### Type Hints

Use of type hints using Python's
[`typing`](https://docs.python.org/3/library/typing.html) module is _highly_
encouraged.

## Integrated Desktop Environments (IDEs)

Common IDEs include:

- [Visual Studio Code](https://code.visualstudio.com/).
  - see also the
    [PyLance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)
    plugin.
- [PyCharm](https://www.jetbrains.com/pycharm/).
- [Neovim](https://github.com/neovim/neovim/). For IntelliSense/IDE like
  environment check out Michael Park's neovim config:
  [here](https://gitlab.com/of_jorts/dotfiles/-/tree/main/nvim/.config/nvim)

## Data Shed Python Cookie-Cutter

If all of this is overwhelming and there are too many things to manage, you can
use a cookie-cutter curated to include the above. This can be found here:

[Data Shed Cookie Cutter Python](https://github.com/TheDataShed/cookiecutter-pypackage)

It also includes a Data Shed badge.

### Quickstart

Install the latest Cookiecutter if you haven't installed it yet (this requires
Cookiecutter 1.4.0 or higher)

```bash
pip install -U cookiecutter

cookiecutter https://github.com/TheDataShed/cookiecutter-pypackage.git
```

--8<-- "includes/acronyms.md"
