# CheatSheet

- [CheatSheet](#cheatsheet)
  - [Clone new repository](#clone-new-repository)
  - [Abort all changes on current branch](#abort-all-changes-on-current-branch)
  - [Cherry pick changes without auto commit](#cherry-pick-changes-without-auto-commit)
  - [Create new branch with checkout](#create-new-branch-with-checkout)
  - [Delete local branch](#delete-local-branch)
  - [Uncommit last N commits (keep changes)](#uncommit-last-n-commits-keep-changes)

## Clone new repository

> clones repo into newly created subfolder

`git clone <url>`

## Abort all changes on current branch

`git reset --hard HEAD`
`git reset --hard origin/<branch name>`

## Cherry pick changes without auto commit

`git cherry-pick <commit id> -n`

## Create new branch with checkout

`git checkout -b <branch name>`

## Delete local branch

`git branch -d <branch name>`

## Uncommit last N commits (keep changes)

`git reset --soft HEAD~1`
`git reset --soft HEAD~2`
`git reset --soft HEAD~<number of commits to uncommit>`