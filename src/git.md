#### Git --- Distributed revision control system

- 查看某一部分命令手册（e.g. `git clone`）

```bash
$ man git clone
or
$ git help clone
```

配置git (in .gitconfig)
```bash
$ git config --global user.name 'YourName'
$ git config --global user.email 'you@yourdomain.example.com'
```

##### Creating a new repository

```bash
$ mkdir project
$ cd project
$ git init
```

Git 在称为"the index"的暂存区域中维护树内容的快照。

更新the index

```bash
$ git add path/to/file		# add new/modified file to the index
$ git rm path/to/file		# remove a file from the index
$ git diff --cache		# 显示HEAD与the index文件的区别
$ git diff			# 显示working tree和index file的区别
```


###### Branch

一个branch是仓库的一个开发线，branch head则指分支的最新commit。

Git可记录多个branches的开发，每个branch有一个指向最新commit的HEAD。

Git使用`.git/HEAD`文件来记录当前分支。

- branch常用指令

```bash
$ git branch    # 列出所有branch
$ git branch <brname>    # 创建名为brname的分支，其分支头指向当前分支位置
$ git branch <brname> <start-point> # 同上，不过分支头指向start-point(branch name/tag)
$ git branch -d <brname>  # 删除brname分支，若分支未完全合并到上游分支或包含在当前分支，则删除失败
$ git branch -D <brname> # 强制删除分支

```



- 查看项目参照表tags

```bash
$ git tag -l
v2.6.11
v2.6.12
v2.6.13
...
```

- git switch

```bash
$ git switch -c <branch> v2.6.13 # 创建一个新的指向某个版本分支头（branch head），并切换分支。
$ git switch --detach v2.6.17 # 不创建新分支检查旧版本tag/commit
```
---

###### Commit

项目历史中的每次改变都是一次commit.

- 查看当前分支最新的commit

```bash
$ git show
commit 17cf781661e6d38f737f15f53ab552f1e95960d7  // SHA-1 id, object name
Author:
Date:
    Reasons
$ git show fb47ddb2	# 显示特定commit
$ git show HEAD^	# HEAD的parent commit
$ git show HEAD^^	# HEAD的grandparent commit
$ git show HEAD~4	# HEAD的四世祖commit
```

查看仓库发展历史

```bash
$ gitk
or
$ git log v2.5..	# commits since v2.5
$ git log --since="2 weeks ago"
$ git log -p		# show patches
```

创建一个tag

```bash
$ git tag stable-1 1b2e1d63ff		# for commit 1b2e1d63ff
```

查看旧版本文件

```bash
$ git show v2.5:fs/locks.c
```

##### Merge

合并两个不同的开发分支

```bash
$ git merge branchname		# Merge branch branchname into the current branch
```

##### Revert

创建一个新的提交恢复先前的更改

```bash
$ git revert HEAD	# Create a new commit which undoes the change in HEAD.
```

##### Further Reading
[Git User Manual](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/user-manual.html)
