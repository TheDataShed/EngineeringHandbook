# Git Cheatsheet

![Git Meme!](assets/images/gitmeme.jpeg)

## **Welcome!**

Version control is the essence of engineering here at the Shed. Git is a free version control system that's responsible for everything GitHub related that happens locally on your computer. This cheatsheet features the most important and commonly used Git commands for easy reference.

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

With platform specific installers for Git, GitHub also provides the ease of staying up-to-date with the latest releases of the command line tool while providing a graphical user interface for day-to-day interaction, review, and repository synchronisation.

You can download Git for Windows and Mac [here](https://desktop.github.com/).

---
## **SETUP**
----
Configuring user information used across all local repositories.

*Using the command below, you can set a name that is identifiable you when review version history*.

```  
git config --global user.name “[firstname lastname]”
```

*Set an email address*.

```
git config --global user.email “[valid-email]”
```

## **SETUP & INIT**

Below are commands for initializing and cloning repositories.

*Initialise an existing directory as a Git repository*.
```
git init
```
*Retrieve an entire repository from a hosted location via URL*.
```
git clone [url]
```
----
## **STAGE & SNAPSHOT**
---
Working with snapshots and the Git staging area.

*Show modified files in working directory, staged for your next commit*.
```
git status
```
*Add a file as it looks now to your next commit (stage)*.
```
git add [file]
```

*Add everything your next commit*.
```
git add *
```
*Commit your staged content as a new commit snapshot*.
```
git commit -m “[descriptive message]”
```

*Upload any changes to your local repository to your remote repository*.
```
git push
```

*Upload any changes to your local repository to your remote repository, rewriting the git history (index)*.
```
git push -f   !---- USE WITH CAUTION ----!
```


*Unstage a file while retaining the changes in working directory*.
```
git reset [file]
```
*Diff of what is changed but not staged*.
```
git diff
```

*Diff of what is staged but not yet commited*.
```
git diff --staged
```



----
## **BRANCH & MERGE**
----
Isolating work in branches, changing context, and integrating changes.

*List your branches. a * will appear next to the currently active branch*.
```
git branch
```

*Create a new branch*.
```
git branch [branch-name]
```


*Switch to another branch and check it out into your working directory*.
```
git checkout
```

*Switch to the specified branch. Creates the branch in your local repository if it doesn't already exist*.
```
git checkout -b [branch_name]
```

*Merge the specified branch’s history into the current one*.
```
git merge [branch]
```

*Show all commits in the current branch’s history*.
```
git log
```
----------
## **INSPECT & COMPARE**
----------
Examining logs, diffs and object information.

*Show the commit history for the currently active branch*.
```
git log 
```

*Show the commits on branchA that are not on branchB*.
```
git log branchB..branchA
```

*Show the commits that changed file, even across renames*.
```
git log --follow [file]
```

*Get the author of a commit*.
```
git blame [commit_hash]
```

*Show the diff of what is in branchA that is not in branchB*.
```
git diff branchB...branchA
```

*Show any object in Git in human-readable format*.
```
git show [SHA]
```
----------
## **TRACKING PATH CHANGES**
----------
Versioning file removes and path changes.

*Delete the file from project and stage the removal for commit*.
```
git rm [file]
```

*Change an existing file path and stage the move*.
```
git mv [existing-path] [new-path]
```

*Show all commit logs with indication of any paths that moved*.
```
git log --stat -M
```

----------
## **IGNORING PATTERNS**
----------
Preventing unintentional staging or commiting of files.


*Save a file with desired paterns as .gitignore with either direct string
matches or wildcard globs*.
```
logs/
*.notes
pattern*/
```

*System wide ignore patern for all local repositories*.
```
git config --global core.excludesfile [file]
```

----------
## **SHARE & UPDATE**
----------
Retrieving updates from another repository and updating local repos.


*Add a git URL as an alias*.
```
git remote add [alias] [url]
```

*Fetch down all the branches from that Git remote*.
```
git fetch [alias]
```

*Merge a remote branch into your current branch to bring it up to date*.
```
git merge [alias]/[branch]
```
*Transmit local branch commits to the remote repository branch*.
```
git push [alias] [branch]
```

*Fetch and merge any commits from the tracking remote branch*.
```
git pull
```
----------
## **REWRITE HISTORY**
----------
Rewriting branches, updating commits and clearing history.

*Apply any commits of current branch ahead of specified one*.
```
git rebase [branch]
```
*Clear staging area, rewrite working tree from specified commit*.
```
git reset --hard [commit]      !--- USE WITH CAUTION ---!
```

----------
## **TEMPORARY COMMITS**
----------
Temporarily store modified, tracked files in order to change branches.

*Save modified and staged changes*.
```
git stash
```

*List stack-order of stashed file changes*.
```
git stash list
```

*Write working from top of stash stack*.
```
git stash pop
```

*Discard the changes from top of stash stack*.
```
git stash drop
```
