# Git Cheatsheet

![Git Meme!](assets/images/gitmeme.jpeg)

## **Welcome!**

Version control is the essence of engineering here at the Shed. Git is a free
version control system that's responsible for everything GitHub related that
happens locally on your computer. This cheatsheet features the most important
and commonly used Git commands for easy reference.

## **Cheatsheet includes:**

    1. Installation & GUI
    2. Setup
    3. Setup & Init
    4. Stage & Snapshot
    5. Branch & Merge
    6. Inspect & Compare
    7. Tracking Path Changes
    8. Ignoring Patterns
    9. Share & Update
    10. Rewrite History
    11. Temporary Commits

## **Installation & GUI**

With platform specific installers for Git, GitHub also provides the ease of
staying up-to-date with the latest releases of the command line tool while
providing a graphical user interface for day-to-day interaction, review, and
repository synchronisation.

You can download Git for Windows and Mac [here](https://desktop.github.com/).

---

## **SETUP**

---

Configuring user information used across all local repositories.

_Set a name that is identifiable you when review version history_.

    git config --global user.name “[firstname lastname]”

_Set an email address_.

    git config --global user.email “[valid-email]”

## **SETUP & INIT**

Below are commands for initializing and cloning repositories.

_Initialise an existing directory as a Git repository_.

    git init

_Retrieve an entire repository from a hosted location via URL_.

    git clone [url]

---

## **STAGE & SNAPSHOT**

---

Working with snapshots and the Git staging area.

_Show modified files in working directory, staged for your next commit_.

    git status

_Add a file as it looks now to your next commit (stage)_.

    git add [file]

_Add everything your next commit_.

    git add *

_Commit your staged content as a new commit snapshot_.

    git commit -m “[descriptive message]”

_Upload any changes to your local repository to your remote repository_.

    git push

_Upload any changes to your local repository to your remote repository,
rewriting the git history (index)_.

    git push -f

_Unstage a file while retaining the changes in working directory_.

    git reset [file]

_Diff of what is changed but not staged_.

    git diff

_Diff of what is staged but not yet commited_.

    git diff --staged

---

## **BRANCH & MERGE**

---

Isolating work in branches, changing context, and integrating changes.

_List your branches. a\*will appear next to the currently active branch\._

    git branch

_Create a new branch_.

    git branch [branch-name]

_Switch to another branch and check it out into your working directory_.

    git checkout

_Switch to the specified branch. Creates the branch in your local repository if
it doesn't already exist_.

    git checkout -b [branch_name]

_Merge the specified branch’s history into the current one_.

    git merge [branch]

_Show all commits in the current branch’s history_.

    git log

---

## **INSPECT & COMPARE**

---

Examining logs, diffs and object information.

_Show the commit history for the currently active branch_.

    git log

_Show the commits on branchA that are not on branchB_.

    git log branchB..branchA

_Show the commits that changed file, even across renames_.

    git log --follow [file]

_Get the author of a commit_.

    git blame [commit_hash]

_Show the diff of what is in branchA that is not in branchB_.

    git diff branchB...branchA

_Show any object in Git in human-readable format_.

    git show [SHA]

---

## **TRACKING PATH CHANGES**

---

Versioning file removes and path changes.

_Delete the file from project and stage the removal for commit_.

    git rm [file]

_Change an existing file path and stage the move_.

    git mv [existing-path] [new-path]

_Show all commit logs with indication of any paths that moved_.

    git log --stat -M

---

## **IGNORING PATTERNS**

---

Preventing unintentional staging or commiting of files.

_Save a file with desired paterns as .gitignore with either direct string
matches or wildcard globs_.

    logs/
    *.notes
    pattern*/

_System wide ignore patern for all local repositories_.

    git config --global core.excludesfile [file]

---

## **SHARE & UPDATE**

---

Retrieving updates from another repository and updating local repos.

_Add a git URL as an alias_.

    git remote add [alias] [url]

_Fetch down all the branches from that Git remote_.

    git fetch [alias]

_Merge a remote branch into your current branch to bring it up to date_.

    git merge [alias]/[branch]

_Transmit local branch commits to the remote repository branch_.

    git push [alias] [branch]

_Fetch and merge any commits from the tracking remote branch_.

    git pull

---

## **REWRITE HISTORY**

---

Rewriting branches, updating commits and clearing history.

_Apply any commits of current branch ahead of specified one_.

    git rebase [branch]

_Clear staging area, rewrite working tree from specified commit_.

    git reset --hard [commit]

---

## **TEMPORARY COMMITS**

---

Temporarily store modified, tracked files in order to change branches.

_Save modified and staged changes_.

    git stash

_List stack-order of stashed file changes_.

    git stash list

_Write working from top of stash stack_.

    git stash pop

_Discard the changes from top of stash stack_.

    git stash drop
