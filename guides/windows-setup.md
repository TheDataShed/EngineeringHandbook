# Initial Set-up for Windows Users

## Git

...

### Git Configuration

This should go in your `~/.gitconfig` file:

```ini
[core]
        editor = \"${LOCALAPPDATA}\\Programs\\Microsoft VS Code\\bin\\code\" --wait
[user]
        name = <FULL NAME>
        email = <EMAIL>@thedatashed.co.uk
[init]
        defaultBranch = main
[push]
        autoSetupRemote = true
```

### Bash Configuration

Shove this in your `~/.bash_profile` file:

```text
HISTFILESIZE=10000
HISTIGNORE=ls:ll
HISTCONTROL=erasedups:ignorespace
HISTIGNORE="export *"
```

## Python

You can install a number of different versions on Python on...

## Visual Studio Code

### Extensions

#### Python Specific

- [Python (`ms-python.python`)](https://marketplace.visualstudio.com/items?itemName=ms-python.python):
  IntelliSense (Pylance), Linting, Debugging (multi-threaded, remote), Jupyter
  Notebooks, code formatting, refactoring, unit tests, and more
- [Pylance (`ms-python.vscode-pylance`)](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance):
  A performant, feature-rich language server for Python in VS Code
- [Black Formatter (`ms-python.black-formatter`)](https://marketplace.visualstudio.com/items?itemName=ms-python.black-formatter):
  Formatting support for python files using `black`
- [isort (`ms-python.isort`)](https://marketplace.visualstudio.com/items?itemName=ms-python.isort):
  Import Organization support for Python files using `isort`
- [autoDocstring - Python Docstring Generator (`njpwerner.autodocstring`)](https://marketplace.visualstudio.com/items?itemName=njpwerner.autodocstring):
  Generates python docstrings automatically

#### T'others

- [indent-rainbow (`oderwat.indent-rainbow`)](https://marketplace.visualstudio.com/items?itemName=oderwat.indent-rainbow):
  Makes indentation easier to read
- [Catppuccin for VSCode (`Catppuccin.catppuccin-vsc`)](https://marketplace.visualstudio.com/items?itemName=Catppuccin.catppuccin-vsc):
  🦌 Soothing pastel theme for VSCode
- [markdownlint `DavidAnson.vscode-markdownlint`](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint):
  Markdown linting and style checking for Visual Studio Code
- [Markdown Preview Mermaid Support (`bierner.markdown-mermaid`)](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-mermaid):
  Adds Mermaid diagram and flowchart support to VS Code's builtin markdown
  preview

### Settings

Some snippets to add to your `settings.json` file:

```json
{
    "telemetry.telemetryLevel": "off",
    "files.autoSave": "onFocusChange",
    "terminal.integrated.defaultProfile.windows": "Git Bash",
    "python.defaultInterpreterPath": "./.venv/Scripts/python.exe",
    "[python]": {
        "editor.defaultFormatter": "ms-python.black-formatter",
        "editor.formatOnSave": true,
        "editor.codeActionsOnSave": {
            "source.organizeImports": true
        },
    },
    "python.terminal.activateEnvironment": true,
    "python.terminal.activateEnvInCurrentTerminal": true,
    "python.analysis.extraPaths": [
        "./src"
    ],
    "isort.importStrategy": "fromEnvironment",
    "autoDocstring.docstringFormat": "sphinx",
    "autoDocstring.startOnNewLine": true,
    "workbench.colorTheme": "Catppuccin Mocha",
    "markdown.validate.enabled": true,
    ...
}
```

Obviously these are just preferences, but a good start point that you're more
than welcome to change.

### Bash Profile

Here's a couple of snippets to add to your bash profile (`~/.bashrc`) aimed at
making your life a bit easier:

```sh
DEFAULT_PYTHON_VERSION=3.10
DEFAULT_PYTHON_VENV="./.venv"

function venva () {
  source $DEFAULT_PYTHON_VENV/Scripts/activate
}

function dovenv () {
  if [ -z "$1" ]
  then
    version=$DEFAULT_PYTHON_VERSION
  else
    version=$1
  fi

  py -$version -m venv $DEFAULT_PYTHON_VENV && venva
}

cd() {
  builtin cd "$1"

  # When you cd into a folder that contains $DEFAULT_PYTHON_VENV
  [[ -d $DEFAULT_PYTHON_VENV ]] && [[ ! $VIRTUAL_ENV ]] && venva

  # When you cd into a folder that doesn't have
  [[ ! -d $DEFAULT_PYTHON_VENV ]] && [[ $VIRTUAL_ENV ]] && deactivate
}
```

This assumes you use Git Bash as your default terminal when working with Python
(which I recommend).
