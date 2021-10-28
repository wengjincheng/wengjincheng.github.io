---
title: "Git 在工作中常用的操作"
date: 2021-10-28T21:38:23+08:00
draft: false
---

## git 分支的建立

``` shell
git checkout -b branchname
```

## 撤销修改

``` shell
git checkout -f // 撤销所有未commit的修改，会导致改动删除

git reset --soft HEAD^ // 撤销当前最新commit，保留改动，改动还在暂存区

git reset --mixed HEAD^ // 撤销当前最新commit 和 add, 保留改动 (这是默认操作)

git reset --hard HEAD^ // 撤销当前最新commit 和 add, 不保留改动
```

## 查询本地和远程分支


``` shell
git branch // 查询本地分支

git branch -r // 查看远程分支
```

## 重命名本地分支

``` shell
git branch -m oldname newname
```

## 删除本地分支/远程分支

``` shell
git branch -d branchname // 删除本地分支

git push origin --delete branchname // 删除远程分支
```

## 更新远程分支列表
``` shell
git remote update origin --prune
```

## 查询&修改本地commit记录

``` shell
git log // 查询

git commit --amend // 修改最新的commit记录
```

## 放弃已有commit 跳转至指定commit 

``` shell
git reset --hard commitname // 这个commit之后的commits都会被删除
```

## 查询本地tag 、创建tag、推送tag远程

``` shell
git tag // 查询本地tag

git tag <tagname> // 创建tag

git push origin <tagname> // 推送tag至远程
```

### 参考

- https://www.cnblogs.com/lfxiao/p/9378763.html
- https://git-scm.com/docs/git-reset

