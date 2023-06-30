# Version-Control Policies

## TL;DR

- changes which are tightly coupled MUST exist in the same commit.
- to be accepted into the main branch, commits MUST adhere to any agreed
  standards.
- pull-/merge-requests are invariably a workflow on top of your commit history
  and not the same thing.

## Branches

Typically, we follow the
[GitHub Flow](https://guides.github.com/introduction/flow/) pattern; we branch
from, and merge back into, a main branch (by contemporary convention[^1], this
is usually called `main`.)

Projects MUST define a branching policy.

Projects SHOULD define a convention for branch names. The aim is to convey as
much information as possible at a glance: this can avoid questions as to the
intended purpose of changes on a branch.

An example would be the branches created when using Jira's integration with
version controls systems: this is the
[_slug_](https://en.wikipedia.org/wiki/Clean_URL#Slug) version of a ticket's
title. In doing so, it couples the branch to the ticket and conveys as much
information as is contained in the title.

Projects CAN opt to use traditional prefixes such as `feature/` or `bugfix/`.

## Pull-/Merge-Requests and/or Code Review

We need to make the distinction between the development process and the _merge_
process.

That is, during development—as per the above—any changes exist on an isolated
branch, away from the main branch. During this time **_anything goes_**.

Committing frequently, to avoid the possibility of losing either changes or the
context thereof, is _highly_ encouraged. Similarly, _pushing_ those commits
frequently to a remote repository, avoiding the local branch as a single point
of failure, is equally encouraged. However, before being accepted to merge into
the main branch:

- the number of commits MUST be reduced to the minimum sensible number.
- all submitted commits MUST adhere to an agreed format.

### Commit Format

We do not prescribe a specific format[^2]. However…

Projects MUST define an agreed format for commit messages.

Project MUST enforce that format.

By defining and adhering to a standard format:

- as much information can be conveyed to readers as is possible.
- structure lends itself to tooling and automation.

### Number of Commits

Making many frequent commits can aid the development process, allowing for quick
reversion of changes or providing context to the developer. The commit history
of the main branch, however, should be more meaningful and each commit should
ideally pertain to a logical group of changes, in order to:

- convey the purpose of a group of changes to future developers;
- allow a complete set of changes to be reverted in a single step: good code is
  easy to remove.

We do not prescribe a specific way to alter the commit history of a development
branch[^3].

## Footnotes

[^1]:
    both historically and presently, certain systems use different names: `MAIN`
    is used by _CVS_, _Git_ previously used `master` (inherited from use by its
    predecessor, _Bitkeeper_), _Subversion_ and others use `trunk`.

[^2]:
    one standard for commit messages is
    [_Conventional Commits_](https://www.conventionalcommits.org/). Tools, such
    as [`commitizen`](https://github.com/commitizen-tools/commitizen), exist
    which can parse commits formatted as per Conventional Commits and perform a
    variety of actions (e.g. version bumping.)

[^3]: two possibilities are `git rebase` or `git reset`:

    - `git reset --soft main`, for instance, will move the current `HEAD` back
      to that of `main` _while leaving local changes in place_. Those changes
      can then be committed in a considered manner and grouped as necessary.
    - `git rebase --interactive main` will allow you to optionally choose which
      commits to retain or alter since the divergence from `main`. _Note_: if
      `main` has changes since the point the branch was created or if there are
      numerous commits, this may not be the ideal solution.

    See also Kubernetes' documentation on how to
    [squash commits](https://www.kubernetes.dev/docs/guide/github-workflow/#squash-commits)
    for a useful guide.
