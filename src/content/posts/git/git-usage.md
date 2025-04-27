---
title: Git Usage
published: 2024-08-04
description: 'List the common git usage'
image: './git-usage.webp'
tags: ['Git']
category: 'Git'
draft: false 
---

## create new branch

``` shell
git checkout -b branchname

git checkout -b <local-branch-name> <origin-branch-name> // create a local branch of remote branch
```

## revoke operations

There are two methods to revoke git commits or changes -> git reset and git revert.

### git reset

git reset will move the HEAD to you want. And it will rewrite the git history.

**Very Very note: do not use this command on commits which have been shared with other developers.If you want to do revoke such commits, use git revert.**

``` shell
git checkout -f // revoke all uncommit changes, but do delete these changes

git reset --soft HEAD^ // revoke latest commit, kepp changes but in stagging space

git reset --mixed HEAD^ // revoke latest commit and add, kepp changes (default)

git reset --hard HEAD^ // revoke latest commit and add. do not keep changes
```

### git revert

git revert will revert commits, and do not delete history commits, it will create a new commit to revert the changes.This feature can make sure the git history is readable.

```shell
// basic usage; you can revert multiple commit once
git revert <commit-hash>

/**
revert merge request
very note: -m 1 mean you want to revert the changes (from featute branch)and keep the main branch 
**/

git revert -m 1 <merge request commit hash>
```

## check local and remote branch


``` shell
git branch // local

git branch -r // remote
```

## rename local branch

``` shell
git branch -m oldname newname
```

## delete local/remote branch

``` shell
git branch -d branchname // local

git push origin --delete branchname // remote
```

## update remote branch list
``` shell
git remote update origin --prune
```

## change commit message/ melt commits into one

``` shell
git log // check

// change latest commit message or add changes into last commit(will effect other repos, do not suggest in the branch that cooperate with other people)
git commit --amend // change latest commit

// use rebase command
git rebase -i HEAD~3 // deal recent 3 commits

// then edit in editor(it will show auto)
pick abc123 First commit message
squash def456 Second commit message
squash ghi789 Third commit message

// If you want to keep other commit, such as third commit
pick ghi789 Third commit message (this is the one you want to keep)
squash abc123 First commit message
squash def456 Second commit message
```

## discard commits

``` shell
git reset --hard commitname // head will target this commit and all commits after this commit will be deleted
```

## Tags

``` shell
git tag // check local tag

git tag <tagname> // create tag

git push origin <tagname> // push tag to remote
```

## view commit history and changes

```shell
git log
git log --oneline // see the history with clean mode
git log --graph // see the history with the branch ui
git show <commit-id hash> // see the changes of commit
```

## stash branch code

```shell

git stash save "commit message" // stash the changes
git stash pop // get the changes from stash and delete this stash
git stash list // check the stash list
git stash drop stash@{0} // delete the stash
git stash clear // clear all stash
git stash --keep-index // only stash work space not staging space

```

### refers

- https://www.cnblogs.com/lfxiao/p/9378763.html
- https://git-scm.com/docs/git-reset


