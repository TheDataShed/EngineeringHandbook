# Git

We're using Git for version control. When creating any new projects always add a
`.gitignore` file; entries for that file can be gleaned from
[https://www.gitignore.io/](https://www.gitignore.io/). Line ending must always
be Unix-style.

## Branches

We largely follow the
[GitHub Flow](https://guides.github.com/introduction/flow/) pattern; we branch
from, and merge back into, `main`. The naming convention for branches should
follow JIRA's, but contain either a `feature/` or `bugfix/` prefix (i.e. a Story
with reference GP-0 and with a title Code & Source Control would correspond to a
branch `feature/GP-0-code-source-control`).

## Merges

Submit Only a Single Commit for Merging. While frequent, smaller commits are an
excellent idea during the development process, it can make the project's history
difficult to navigate if they are included in the commit history of the main
branch.

In order to keep a project's Git log easy to parse,we require that the final
form of any submission be a single commit. To reduce a number of commits to a
single, final one you can do one of the following:

1. Squash your feature branch's commits down to ideally a single commit;
2. Reset your feature branch to the same state as the main branch and add the
   changes back as a single commit.
3. If absolutely required, a few discreets change-sets (there will always be
   exceptions; _"a foolish consistency is the hobgoblin of little minds."_)

For instance, prior to raising a pull-request to merge a feature into `main`,
you can see the changes made on just your branch with (after making sure your
local `main` branch is up to date, of course):

git log main.. This will show a list of those commits on your current branch
which are not in `main`:

```git
commit 5098ae08bc39f4928cde1102134dc112d6280e27
Author: Roger G. Coram <roger@thedatashed.co.uk>
Date: Tue May 23 11:48:32 2017 +0100

    Added shiny, new endpoint.

commit 2fa9cd9212b391d70fd63fc2722eae80144159b4
Author: Roger G. Coram <roger@thedatashed.co.uk>
Date: Tue May 22 10:18:31 2017 +0100

    Typo.

commit b787a81c32997fd39a5f4c0188363902d3586e7b
Author: Roger G. Coram <roger@thedatashed.co.uk>
Date: Tue May 20 08:28:51 2017 +0100

    Minor change.

```

Here we have 3 commits which we should merge into a single commit.

### Git Rebase

git rebase The first option is to use Git's interactive-rebase command to squash
each commit into a single, final one, optionally retaining the commit messages
from each.

Note the below differs from git merge --squash insofar as this will result in an
merge (i.e. will display a message in `git log --merges`) whereas `--squash`
will result in a single, standard commit message (i.e. will display a message in
`git log --no-merges`).

The start the interactive rebase:

```bash
git rebase -i main
```

This will bring up an interactive editor wherein we can squash our commits
(note: you can also achieve the same thing by `git rebase -i HEAD~3` but the
above is a more clear representation of intent):

```git
pick 5098ae0 Added shiny, new endpoint.
pick 2fa9cd9 Typo.
pick b787a81 Minor change.
Here, replace the word pick with squash (or simply s) in all but the top line:

pick 5098ae0 Added shiny, new endpoint.
squash 2fa9cd9 Typo
squash b787a81 Minor change.
```

Save your changes and git will prompt you to enter a new message for the new,
squashed commits.

The new, single commit can be view by repeating the command:

```bash
git log main ..
```

### Git Reset

Alternatively, you can simply undo the Git commit history of your feature branch
while retaining the changes you have made:

`git reset --soft main` Running the above will remove all Git commits you have
made on your feature branch, back to the point at which it deviated from the
`main` branch. However, the changes to your files remain intact. You can now git
add the affected files and make a new, single commit.

Note that the `--soft` is very important: the alternative, `--hard`, not only
removes the Git commits but your changes also.
