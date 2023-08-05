---
title: "Git 入门"
date: 2023-08-04T19:29:46+08:00
---

## 1. git介绍

git是一套高效的版本管理工具，最早是因为bitkeeper同linux社区结束了合作关系，导致linus开始开发一套自己的版本管理工具。

## 2. git的基本原理

### 2.1 git完整性

在保存到git之前，需要对数据进行内容的检验和计算，git使用的sha-1算法计算检验和，该检验和由40个字符串组成作为指纹字符串进行标识。


### 2.2 文件状态

git中的文件有三种状态
- commited：已经被提交
- staged：修改被暂存
- modified：被修改

### 2.3 git 配置

git的配置文件在`/etc/gitconfig`和`~/.gitconfig` 中，前者是对系统适用的配置文件，后者是对用户适用的配置文件

下面是一个用户配置文件的例子，用于配置编辑器等

```shell
[user]
	email = chengjiajun20@gmail.com
    name = jiajunCheng

[core]
    editor = vim
[https]
	postBuffer = 1048576000
[http]
	postBuffer = 357286400
```

为了对git进行配置，可以选择直接编辑此配置文件，也可以使用命令行进行配置

```shell
git config --global user.name "jiajunCheng"
```

如果要查看配置的信息 `git config --list`


## 3. git基础使用

### 3.1 初始化仓库

初始化为git仓库
```shell
git init
```

添加修改的文件

```shell
git add .
```

进行commit
```shell
git commit -m "the commit message"
```

### 3.2 查看仓库状态

使用`git status` 可以查看仓库的状态，显示文件所在分支等情况

```shell
git status
```

### 3.3 忽略某些文件

使用`.gitignore`可以忽略文件使得其不被git所追踪

```shell
# 忽略所有满足通配符的文件
*.a

# 将文件设置为例外
!lib.a

# 忽略根目录下的a.txt
/a.txt

# 忽略build文件夹下的所有文件
build/
```

### 3.4 查看历史

通过`git log` 可以查看历史信息等


### 3.5 撤销修改

撤销最后一次的修改
```shell
git commit --amend
```

### 3.6 远程仓库的管理

查看远程的情况
```shell
git remote -v 
```

添加一个远程的源
```shell
git remote add >remote name> <remote url>
```

### 3.6 标签管理

查看标签
```shell
git tag
```

新建标签

```shell
git tag -a <tag name> -m <tag message>
```

如果不需要添加信息，可以直接使用`git tag <tag name>`即可


后期对某个commit加上tag
```shell
git tag -a <tag name> <commit version> 
```

tag默认不会被push到远端，所以需要使用

```shell
git push <remote name> --tags
```

## 4. git 分支

### 4.1 分支合并

最简单的是使用merge进行处理，如果没有冲突的话
```shell
git merge <branch name>
```

### 4.2 分支删除

```shell
git branch -d <branch name>
```

### 4.3 分支冲突

```shell
git mergetool <file name>
```

### 4.4 使用变基的方式进行合并

rebase是git中的一个重要的操作，使用rebase可以将部分分支的修改直接添加到当前分支上。

假设dev分支和main分支起源于同一个commit，dev分支在此时进行了commit，main分支也进行了commit，如果此时需要将dev的修改合并到main分支上，那么此时可以

```shell
git checkout dev
git rebase main
git checkout main
git merge dev
```

使用变基的方法需要注意的是避免对已经存储远端的提交历史进行操作

## 5. 服务器上的git

### 5.1 基于本地协议

git在进行clone的时候可以使用本地的文件路径作为远端的url进行使用


### 5.2 ssh协议

可以在前面指明使用ssh或者是使用 user@server的方式即可进行处理


### 5.3 http协议

只需要把裸的git仓库文件放到http服务的根目录下并设置一个特定的post-update(hook)即可搞定



## 6. 分布式git

### 6.1 集中式工作流

只有一个核心仓库，每个人向其中提交代码，并从远端拉取他人的修改，是最常见的工作模式

### 6.2 集成管理员工作模式

每个成员对应一个远程的仓库，还有一个远程的总仓库从这些远程仓库中获取更新。

### 6.3 司令官与副官工作流


### 6.4 cherry-pick 获取commit

```shell
git cherry <commit version>
```

## 7. git工具

### 7.1 交互式git

使用`git add -i` 可以使得git进入交互式的shell模式

```shell
> git add -i 
           staged     unstaged path
  1:    unchanged       +65/-6 content/git.md

*** Commands ***
  1: status       2: update       3: revert       4: add untracked
  5: patch        6: diff         7: quit         8: help
What now> 1
           staged     unstaged path
  1:    unchanged       +65/-6 content/git.md
```

### 7.2 暂存

有时候在当前分支上做了一些修改但是不希望进行commit又希望切换到其他的分支上，那么此时可以使用`git stash`进行暂存

回到当前分支继续开发可以使用`git stash pop`, 如果想放弃这些修改，可以使用`git stash drop`

### 7.3 子模块

```shell
git submodule add <repo url>
```

克隆带子项目的仓库

```shell
git clone <repo url>
cd <repo>
# 初始化子模块
git submodule init 
```

更新子模块

```shell
git submodule update
```
