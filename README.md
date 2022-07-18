# GIT CheatSheet

- [CheatSheet](#cheatsheet)
  - [Clone new repository](#clone-new-repository)
  - [Abort all changes on current branch](#abort-all-changes-on-current-branch)
  - [Cherry pick changes without auto commit](#cherry-pick-changes-without-auto-commit)
  - [Create new branch with checkout](#create-new-branch-with-checkout)
  - [Delete local branch](#delete-local-branch)
  - [Uncommit last N commits (keep changes)](#uncommit-last-n-commits-keep-changes)
  - [Merge master to develop afeter commit to master only](#merge-master-to-develop-after-commit-to-master-only)
  - [Resolve Conflicts on pull request](#resolve-conflicts-on-pull-request)
  - [Update feature branch with the latest commits of develop branch](#update-feature-branch-with-the-latest-commits-of-develop-branch)
  - [Stash changes created on "wrong" feature branch and apply them on the "right" one](#stash-changes-created-on-wrong-feature-branch-and-apply-them-on-the-right-one)
  - [Undo uncommited changes](#undo-uncommited-changes)
  - [Move uncommited changes to another branch](#Move-uncommited-changes-to-another-branch)
  - [Re-push develop branch after accidental deletion via PR develop into masters](#Re-push-develop-branch-after-accidental-deletion-via-PR-develop-into-masters)

## Clone new repository

> clones repo into newly created subfolder

```
git clone <url>
```

## Abort all changes on current branch

```bash
git reset --hard HEAD
```

```bash
git reset --hard origin/<branch name>
```

## Cherry pick changes without auto commit

```bash
git cherry-pick <commit id> -n
```

## Create new branch with checkout

```bash
git checkout -b <branch name>
```

## Delete local branch

```bash
git branch -d <branch name>
```

## Uncommit last N commits (keep changes)

Uncommit one last commit

```bash
git reset --soft HEAD~1
```

Uncommit two last commits

```bash
git reset --soft HEAD~2
```

Uncommit N last commits

```bash
git reset --soft HEAD~<number of commits to uncommit>
```

## Merge master to develop after commit to master only

Get the latest version of master
```bash
git checkout master
git pull
```

Get the latest version of develop

```bash
git checkout develop
git pull
```

Merge master into develop

```bash
git merge master
```

Push the merge

```bash
git push
```

## Resolve Conflicts on pull request

Swtich to the branch that I'm merging to some other branch

```bash
git checkout <source branch>
```

Pull for the target branch that I'm merging into

```bash
git pull origin <target branch>
```

1. open solution in the VSCode
2. go to the conflict files
3. resolve (accept current or incoming or show differences and make changes manualy)

After resolving conflicts

```bash
git commit -m "Resolve merge conflicts"
git push
```

## Update feature branch with the latest commits of develop branch

Go to the feature branch

```bash
git fetch origin develop:develop
```

Merge changes into the feature branch

```bash
git merge develop
```

## Stash changes created on wrong feature branch and apply them on the right one

On the "wrong" branch

```bash
git stash
```

Go to the "right" branch

```bash
git stash pop <index of the last stash>
```

Show list of all stashes

```bash
git stash list
```

## Undo uncommited changes

This will unstage all files you might have staged with `git add`

```bash
git reset
```

This will revert all local uncommitted changes (should be executed in repo root)

```bash
git checkout .
```

You can also revert uncommitted changes only to particular file or directory

```bash
git checkout <some_dir|file.txt>
```

Yet another way to revert all uncommitted changes (longer to type, but works from any subdirectory)

```bash
git reset --hard HEAD
```

This will remove all local untracked files, so only git tracked files remain

```bash
git clean -fdx
```
> WARNING: -x will also remove all ignored files, including ones specified by .gitignore! You may want to use -n for preview of files to be deleted.

To sum it up: executing commands below is basically equivalent to fresh git clone from original source (but it does not re-download anything, so is much faster)

```bash
git reset
git checkout .
git clean -fdx
```

## Move uncommited changes to another branch

```bash
git stash
git checkout <correct-branch>
git stash pop
```

> Note: No need to use stash command. Uncommitted changes do not belong to any branch so just use `git checkout -b <new-branch>`

## Re-push develop branch after accidental deletion via PR develop into masters

> find last merge commit e.g. 53172fe2fa71ace8d6f2a1442cba026da9c9345f

```bash
git fetch
git checkout 53172fe2fa71ace8d6f2a1442cba026da9c9345f
git checkout -b develop
git push
```
