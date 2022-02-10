# CheatSheet

- [CheatSheet](#cheatsheet)
  - [Clone new repository](#clone-new-repository)
  - [Abort all changes on current branch](#abort-all-changes-on-current-branch)
  - [Cherry pick changes without auto commit](#cherry-pick-changes-without-auto-commit)
  - [Create new branch with checkout](#create-new-branch-with-checkout)
  - [Delete local branch](#delete-local-branch)
  - [Uncommit last N commits (keep changes)](#uncommit-last-n-commits-keep-changes)
  - [Merge master to develop afeter commit to master only](#merge-master-to-develop-afeter-commit-to-master-only)
  - [Resolve Conflicts on pull request](#resolve-conflicts-on-pull-request)
  - [Update feature branch with the latest commits of develop branch](#update-feature-branch-with-the-latest-commits-of-develop-branch)

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

```bash
# uncommit one last commit
git reset --soft HEAD~1

# uncommit two last commits
git reset --soft HEAD~2

# uncommit N last commits
git reset --soft HEAD~<number of commits to uncommit>
```

## Merge master to develop after commit to master only

```bash
# get the latest version of master
git checkout master
git pull

# get the latest version of develop
git checkout develop
git pull

# merge master into develop
git merge master

# push the merge
git push
```

## Resolve Conflicts on pull request

```bash
# swtich to the branch that I'm merging to some other branch
git checkout <source branch>

# pull for the target branch that I'm merging into
git pull origin <target branch>

# 1. open solution in the VSCode
# 2. go to the conflict files
# 3. resolve (accept current or incoming or show differences and make changes manualy)

# afte resolving conflicts
git commit -m "Resolve merge conflicts"
git push
```

## Update feature branch with the latest commits of develop branch

```bash
# go to the feature branch
git fetch origin develop:develop

# merge changes into the feature branch
git merge develop
```

