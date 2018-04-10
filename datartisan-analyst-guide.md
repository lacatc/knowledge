# 数据分析Python相关工具基本使用梳理

> Datartian Analyst Guide

## 一些基础知识

- 操作系统
  - 三大：Windows, macOS, Linux家族（包括各种发行版）

- 操作系统的基准
  - 贴近实际工业应用
  - 类 Linux
  - 事实标准 Ubuntu Server
    - 版本 16.04 18.04

- Windows 的问题
  - 很多地方与（比如路径的 / 与 \）与 linux 差异很大
  - 中文等非英文字符，编码有历史遗留问题，且没有好的办法，需要非常清晰的了解各种边角情况才能处理好，无用功
  - 奇怪问题多，主要是受复杂外部环境影响

- Linux 家族的问题
  - 太多的发行版
  - 复杂
  - 几乎所有的图形用户界面都很难用
    - 不稳定
    - 用户使用交互思路独特，不好用
    - 中文等支持很差

- macOS 的问题
  - 苹果官方的出发点为普通家庭、工作而设计，没有考虑科研等专业需要
  - 很多概念与一直接触的 windows 不一样，需要另外理解
  - AppleID，不强制，但是没有没法使用 App Store 方便下载软件

- 其他的问题：
  - 学习成本，都不小
  - 开源软件本身的问题，一题多解，解决思路变化快，生态不稳定

- 为什么我们推荐使用 macOS
  - 省事
  - 与 Linux 相似
  - 图形界面方便、好用

## macOS 命令使用

- Kernel 与 Shell

- 宏观的 Shell
  - 所有用户直接接触，用来操作电脑的接触物
  - 图形界面
  - 命令行

- 一半意义上的 Shell
  - 命令行

- macOS 里 Terminal.app 是什么？
  - 是苹果图像界面（Shell）中的一个程序，用来运行命令 shell

- 命令行 shell
  - *nix x
  - bash
  - zsh

- 所以 Terminal.app 里可以运行着 bash zsh 或其他说明 shell

- 日常命令
  - 什么是命令：
    - 就是运行在命令行中的程序
  - pwd
  - ls
  - cd
    - .
    - ..
  - cp
  - mv
  - mkdir
  - which
  - rm
  - head
  - tail
  - 多用帮助 (--help, man, google)
  - macOS 特有的
    - open

- homebrew
  - 外部软件包管理工具
  - 命令行工具，命令是 brew
  - 开源社区做的，并非苹果官方
  - 方便的安装、管理第三方工具

- zsh
  - 通过 homebrew 安装
  - 安装 oh-my-zsh，复制官网的安装连接即可

## python 相关

- Python 发行版
  - 官方 2.x 2.7 2.7.14
  - 官方 3.x 3.6 3.6.5
  - 官方版本也可以说是 CPython，注意不要和另外一个东西搞混 cython
  - jython-*
  - ironpython-*
  - pypy-*
  - ...

- 集成包
  - anaconda 集成包，比较特别的存在
    - anaconda2、anaconda3：并没有大的差别，差别在于默认的自带的解释器的版本，但是一班会使用 conda，与默认解释器版本无关

- 多Python版本管理
  - 是指 python 解释器不同实现版本的多版本
  - pyenv

- 多python环境管理
  - virtualenv
    - 2.x ：pip install virtualenv
    - 3.x 官方 python3 已经自带

- 独立说一下 conda
  - 是 anaconda 系的独立管理版本、环境的工具
  - conda 建立的 env 是包括连解释器版本（只是官方版本）

- 第三方包的安装
  - pip
    - 包的源是 pypi，由 python 官方维护的第三方包的收录库，可以随意自行提交
    - easy_install 已经非常老旧，无视

## 专业的工作环境搭建

当拿到一台新装系统的 mac 电脑：

> * 安装过程中已经建立好了电脑系统用户
> * 连接上了互联网

- 打开 terminal.app
- 安装 homebrew，按照提示操作即可
- 通过 homebrew 安装 pyenv
- 通过 pyenv 安装、管理所需要的 python 版本


## 比较专业的工作环境搭建

- 正常安装 anaconda（或 miniconda）工具
- 使用附带的 conda 工具创建独立的 conda env
- 使用 conda 来管理包

需要明白的：
- conda 环境可以有独立的python解释器版本
- 使用 conda 安装包，通过 anaconda 的包的源，非 pypi
- conda 的包，囊扩的不仅是 python 的包，conda 可以统一管理很多软件、包、类库，类似 homebrew


## 肯定会很麻烦的工作环境搭建

- 安装 python 官网下载的
- 双击安装，下一步
- 系统内混杂多个解释器，使用的时候也不知道是哪个解释器在生效
- 不明所以的修改过系统环境变量 PATH 等，导致奇怪的行为


## git 使用

- git 是什么
  - git 是一个代码（*文本）的版本管理工具

- 为什么使用 git 这么重要
  - 通过对于变化的管理
  - 协作的基础
  - 事实标准

- 日常使用思路
  - 基本命令
    - git init
    - git add
    - git commit
    - git clone
    - git remote
    - git push
    - git pull
  - 基于 Git 的托管服务平台的使用
    - Github
    - Bitbucket