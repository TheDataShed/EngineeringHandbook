# Git Practices

This guide is meant to set up some handy git configuration options and/or tools
that should help you get set up quickly. This section will need to be filled in
more for other operating systems as and when available.

## Flight Rules

Flight Rules is a fantastic GitHub repository which has a plethora of
information about Git and all its quirks with various guides of how to do almost
anything you may ever need to do in Git.

You can find [flight-rules here](https://github.com/k88hudson/git-flight-rules).

## Initial Setup

### SSH Keys

If you do not have one already, it is always handy to have an ssh key pair
generated on your device that allows you to push and pull from origin without
the need to enter a password. This keypair will also be added to your
github/gitlab account so it's worth setting up.

To generate a new key pair:

#### SSH on Linux

```bash
ssh-keygen -t ed25519 -C "<email-address>"

# Verify it's there.
ls -la ~/.ssh
```

You should see your key listed there. The .pub file is what you will want to add
to your gitlab/github account under ssh keys.

#### SSH On Mac

```bash
ssh-keygen -t ed25519 -C "<email-address>"

# verify it's there.
ls -la ~/.ssh
```

Add the contents of `~/.ssh/id_ed25519` to your GitHub account under SSH keys.

Use the following instructions to set your SSH key in your Git Config. Use
`--global` to set this globally or omit `--global` for this to be repo specific.

```bash
nano ~/.ssh/config
```

Add the following lines to the file:

```text
Host github.com
  User git
  Hostname github.com
  IdentityFile ~/.ssh/id_ed25519
```

You should now be able to use the SSH key(s) to authenticate with GitHub.

#### SSH on Windows

### GPG Keys

Having a gpg key pair for your work address will allow you to sign commits and
tags.

#### GPG on Linux

```bash
gpg --full-generate-key
```

Make sure that your email address is the one you will set as your git commit
email address. Add the public key to your github/gitlab account.

#### GPG on Mac

You will need [Homebrew](https://brew.sh/) in order to install `gpg` on your
Mac.

Install `gpg`:

```bash
brew install gpg
```

Generate your key:

```bash
gpg --full-generate-key
```

_Tip: It's a good idea to use **LastPass** to generate and store your private
key passphrase. If you ever need to re-export your private key, you'll need the
passphrase._

Follow the prompts to generate your key. Ensure the email address you use is the
same email address you will use for your Git commits.

Export the keys to file(s). The below commands will export both your public and
private keys to your home directory:

```bash
gpg --list-secret-keys
gpg --output public.pgp --armor --export <your email address>
gpg --output private.pgp --armor --export-secret-key <your email address>
```

Sometimes, you may need to update a `gpg` setting so that commits can be signed
successfully by `gpg` on Mac.

```bash
export GPG_TTY=$(tty)
```

You can test if this has worked with:

```bash
echo "test" | gpg --clearsign
```

Add the public key from `public.pgp` to your GitHub/GitLab account under "GPG
Keys".

Once the public key is added to your account, follow the instructions in the
[Configuration](#configuration) section below to configure your GPG key for use
with Git.

## Optional Tools

### GUI

- PyCharm: GitToolBox
- VS Code: Gitlens plugin
- Sublime Merge
- GitKraken

### TUI

These are git tools you can call from your command line

- LazyGit: [LazyGit](https://github.com/jesseduffield/lazygit)
- Tig: [Tig](https://jonas.github.io/tig/)

### Other

These are some other tools that don't quite fit in the two options above

- Neovim: [Neogit](https://github.com/TimUntersberger/neogit)
- Emacs: [Magit](https://magit.vc/)
- Rust diff tool: [Delta](https://github.com/dandavison/delta)

## Configuration

This section deals with options in the `.git/config` file that make your commits
look _pristine_!

You can set the following options through the command line. Pass the --global
flag if you want to set these as the default otherwise remove the flag to have
it be repo specific

Set your name and email address so the commit can be attributed to yourself:

```bash
git config --global user.name "<First> <Last>"
git config --global user.email "<email address>"
```

```bash
# Find out your key id
gpg --list-keys <your-email-address-from-above>

git config --global user.signingkey <KEYID from above command>
git config --global commit.gpgsign true
git config --global tag.gpgSign true
```

Set your .git/config to below to reap the benefits of git delta diffs These can
also go in your home directory .gitconfig file for it to cascade.

```toml
[core]
    pager = delta

[interactive]
    diffFilter = delta --color-only

[delta]
    navigate = true  # use n and N to move between diff sections

[merge]
    conflictstyle = diff3

[diff]
    colorMoved = default
```

_NB: Be careful not to overwrite existing Git config options._

## Pre-Commit Hooks

Pre commit hooks can be super useful to make sure that your project gets
whatever validation you may want before a commit is approved.

You can get started with pre-commit [here](https://pre-commit.com/)

Here is an example pre-commit config for a python project.

```yaml
# See https://pre-commit.com for more information
# See https://pre-commit.com/hooks.html for more hooks
default_language_version:
  python: python3.9

exclude: "^$"

fail_fast: false

repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v3.2.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml
      - id: check-json
      - id: detect-private-key
      - id: check-added-large-files
        args: ["--maxkb", "3_000"]
      - id: check-merge-conflict
      - id: check-docstring-first
  # Python import sorting
  - repo: https://github.com/pycqa/isort
    rev: 5.10.1
    hooks:
      - id: isort
        name: isort (python)
        args: ["--profile", "black", "--filter-files"]
  # Python formatting
  - repo: https://github.com/psf/black
    rev: 21.12b0
    hooks:
      - id: black

  # Python linting/syntax checking
  - repo: https://github.com/pycqa/flake8
    rev: "4.0.1" # pick a git hash / tag to point to
    hooks:
      - id: flake8

  # Commit message
  - repo: https://github.com/commitizen-tools/commitizen
    rev: "v2.20.3"
    hooks:
      - id: commitizen
        stages: [commit-msg]

  # Python check docstrings
  - repo: https://github.com/pycqa/pydocstyle
    rev: 6.1.1 # pick a git hash / tag to point to
    hooks:
      - id: pydocstyle
        args:
          - --ignore=D100,D203,D406,D407,D212
```

## Underused Features

### Git Worktrees

If you find yourself switching and stashing code very frequently, you may find
that managing your stashes becomes a job itself. There is a handy feature that
you can use to get around this called worktrees which effectively creates a dir
per branch (or worktree).

You can read about worktrees here:

- [docs/git-worktree](https://git-scm.com/docs/git-worktree)

```bash
git worktree add [-f] [--detach] [--checkout] [-b <new-branch>] <path>
git worktree list [-v | --porcelain]
git worktree lock [--reason <string>] <worktree>
git worktree move <worktree> <new-path>
git worktree prune [-n] [-v] [--expire <expire>]
git worktree remove [-f] <worktree>
git worktree repair [<path>...]
git worktree unlock <worktree>
```
