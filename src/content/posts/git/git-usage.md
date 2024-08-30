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

## check&change commit

``` shell
git log // check

git commit --amend // change latest commit
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

### refers

- https://www.cnblogs.com/lfxiao/p/9378763.html
- https://git-scm.com/docs/git-reset


