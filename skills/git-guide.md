# Git 基本使用指南

## 基本概念明确

- 版本管理软件
- 中心式版本管理软件、分布式版本管理软件
- Git
- Git 库托管服务，Github、Bitbucket、自建
- 文本文件
- 二进制文件

## 为什么要使用 Git ？

- 使用文件版本管理软件高效的管理文件的变化
- 使用文件版本管理软件高效的进行文件变化操作的协作
- Git 是当前使用最广泛的版本管理软件，以及事实标准

## Git 的问题

- 概念多
- 很复杂，高级操作很复杂
- 命令行操作为核心（其他工具软件可以看做也是通过命令行操作）

## 核心概念

- Repository: 仓库，简称 repo

- Local Repository：仓库区（或本地仓库）
  - Workspace：工作区
  - Stage：暂存区

- Commit: 提交

- Branch: 分支
  - 默认的分支叫 master

- Remote：远程仓库
  - clone 建立的库，clone 的源库，会自动成为一个 remote ，名字叫 origin

Tips:

- 库，具象化就是一个文件夹
- 库，抽象化就是一棵树
- 一个 commit 就是对一系列文件操作的记录
- 版本变化的依据是文件的变化以及文件内容的变化
- 一半而言，对于文本文件，git 可以做到行级的变化版本记录
- 但是对于其他二进制文件，只能做到文件整体变化的版本记录（并不绝对）
- 版本变化的一般扩散路径为：
  - 本地工作区 Local Workspace
  - 本地仓库  Local Repo
  - 自己的远程仓库 Origin Remote Repo
  - 团队的远程仓库 Main Remote Repo

![](_images/git-repo.png)

## 使用指南（重要）

* 以 macOS 系统为例 *

### git 安装

在 macOS 中，没有内置 git，但是安装 git 很方便

打开一个 Terminal.app 窗口，执行 git ，如果系统中没有 git 就会开始安装程序，选择确定，然后等待即可。

### 配置 git

**必要**

> 制定 --global ，系统级配置，只需要配置一次

```
git config --global user.name "GuoPeng"
git config --global user.email "guopeng@datartisan.com"
```

### 创建 git 库

创建一个 git 库有两种方法：

1. 新建一个库

进入想要创建为库的目录

```
cd {somedir}
```

创建为 git 库

```
git init
```

2. 从其他的已经存在的库 clone 过来

```
git clone {src_repo} [dst_dir]
```

范例： git clone https://github.com/Datartisan/knowledge  ，注意：此时 dst_dir 即为 knowledge 文件夹名字与源库名字一致

> 使用 git clone 创建的库，其名为 origin 的 remote 会被自动设置为源地址

### 查看当前 git 库状态

```
git status
```

### 让文件的修改进入 stage

```
git add {file}
```

### 从 stage 中拿掉文件

```
git rm --cached {file}
```

### 提交版本

```
git commit -m "这里是提交说明，必须要写"
```

> 提交说明书写要求：
> 1. 必须要写
> 2. 要有意义，不能乱写
> 3. 可以写的又臭又长，但是不能写的不清不楚

### 查看分支

```
git branch
```

### 建立分支

```
git branch {branch_name}
```

### 切换分支

```
git checkout {branch_name}
```

### 从其他分支合并修改提交

```
git merge {branch_name}
```

### 增加 Remote

```
git remote add {remote_name} {remote_path}
```

### 查看所有的 Remote

```
git remote -v
```

### 获取 Remote 的变动信息，本地不做其他处理

```
git fetch {remote_name}
```

### 获取 Remote 的变动信息，且与本地当前分支进行合并（merge）

```
git pull {remote_name}
```

### 将当前库的变动推送到某 Remote

```
git push {remote_name}
```


## 图形界面使用指南（必须要在了解了命令行git使用以后再学习）

git 图形界面工具首推 sourcetree

注意：

0. 一定要在了解命令行使用的基础之上子再去使用 sourcetree，sourcetree 的功能与命令行几乎一致
1. sourcetree 是免费的，但是需要有 bitbucket 账户才可以使用

## 总结一下需要了解的 git 操作：

- git init
- git clone
- git add
- git rm --cached {file}
- git commit -m
- git branch
- git checkout
- git merge
- git remote add
- git remote -v
- git fetch
- git pull
- git push

## **要求**

- 使用工作邮箱，注册 github 、 bitbucket 账号

- 学习 try.github.io 课程


## （Optional）实际协作过程中的使用的“三库模型”

前提：

- 需要依赖 Git 库托管服务（如 Github、Bitbucket）




## 参考资料

http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html

https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000