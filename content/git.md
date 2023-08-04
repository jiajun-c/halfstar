---
title: "Git 入门"
date: 2023-08-04T19:29:46+08:00
---

# 1. git介绍

git是一套高效的版本管理工具，最早是因为bitkeeper同linux社区结束了合作关系，导致linus开始开发一套自己的版本管理工具。

# 2. git的基本原理

## 2.1 git完整性

在保存到git之前，需要对数据进行内容的检验和计算，git使用的sha-1算法计算检验和，该检验和由40个字符串组成作为指纹字符串进行标识。


## 2.2 文件状态

git中的文件有三种状态
- commited：已经被提交
- staged：修改被暂存
- modified：被修改

## 2.3 git 配置

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

```