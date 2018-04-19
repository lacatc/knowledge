# Anaconda 基本使用说明

Anaconda Usage Guide

> 以 macOS 系统为例

## 安装

- 下载 Anaconda 安装包

- 建议安装 Anaconda3 的最新版本

Tips:

> - 官网下载地址： https://www.anaconda.com/download/
> - 如果在官网下载速度太慢，可以选择 Anaconda 的中国地区镜像，比如清华大学镜像， 下载地址： https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/

关于 Anaconda 镜像：

Anaconda 的资源镜像一般不仅包含 Anaconda 各个版本的安装包下载，也会包含各个 conda 包源（channels）
所以安装 conda 源上的包也可以使用国内镜像加速


- 双击安装
  - 安装过程比较简单，无需另外进行设置，不断下一步就好，有步骤需要键入用户密码以便安装程序可以进行系统操作。
  - 安装程序会自动修改 .bash_profile 文件，配置 PATH 环境变量

- 测试安装是否成功

  - 打开 terminal.app各个
  - 执行 `python -V`，观察返回结果，有 Anaconda 字样
  - 执行 `which python`。看到返回 /miniconda3/bin/python ，就是安装成功了


## （Optional）包下载源国内镜像配置，用以提高第三方 conda 包的安装速度

配置所有可以用的清华大学的源地址
```
## 核心 channel
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/

## 拓展 channel
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/

## 第三方 channel
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/menpo/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
```

## miniconda 的使用

因为 Anaconda 安装包会默认包含 300 多个科学计算、数据分析相关包，所以安装包比较大

所以如果用不大那么多 Anaconda 默认集成的包，且又不希望下载安装占用太多的硬盘空间，且习惯使用 conda env ，那么 miniconda 就是很好的选择。

所以可以理解为 miniconda 就是一个只提供 conda 相关操作的安装包，如果需要另外的第三方包，还需要另外自行安装

下载：

- 可以选择 miniconda3-lastest 版本

  - 官网下载 https://conda.io/miniconda.html
  - 国内镜像站下载（速度较快 https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/

- 安装
  - 安装过程比较简单，无需另外进行设置，不断下一步就好，有步骤需要键入用户密码以便安装程序可以进行系统操作。
  - 安装程序会自动修改 .bash_profile 文件，配置 PATH 环境变量

- 验证是否安装成功
  - 打开一个新的 Terminal.app 窗口
  - 执行 python -V，观察返回结果，看到有 Anaconda 字样的就是安装成功了
  - 执行 which python ，看到返回 /miniconda3/bin/python ，就是安装成功了

## conda

### 是什么

介绍：

Conda is an open source package management system and environment management system that runs on Windows, macOS and Linux. Conda quickly installs, runs and updates packages and their dependencies.

Package, dependency and environment management for any language—Python, R, Ruby, Lua, Scala, Java, JavaScript, C/ C++, FORTRAN.

总结：

- 包管理工具、环境管理工具
- 不光是管理 Python 包，也可以管理其他包
- 支持多种操作系统 macOS、Windows、Linux


### conda 的环境管理

conda 环境是什么？

- 一系列确定的包，组成的可以相互独立存在的运行环境
- 需要使用环境的时候需要激活环境
- 不需要使用环境的使用可以关闭环境

为什么需要环境管理？

- 因为在做不同的数据分析事务的时候所需要的包不一样，或者包的版本不一样，如果都在一个环境中处理会引起很多冲突

查看当前已有的环境：

```
conda env list
```

环境的创建：

```
conda env create -n {需要创建环境的名字} [新的环境中软件包的要求]
```

通过“环境的描述文件”来创建新环境：

建立环境描述文件： environment.yml

内容为：
```yml
name: jupyterlabenv
channels:
  - conda-forge
dependencies:
  - jupyterlab
```

> 具体描述文件的写法可以查阅文档

```
conda env create -f environment.yml
```

这样就可以安装好一个名为 jupyterlabenv ，且有 jupyterlab 包的环境

既通过上述环境描述文件安装环境等同于，以下操作的组合：

```
conda env create -n jupyterlabenv
conda install -n jupyterlabenv jupyterlabs
```


激活环境：

```
source activate {环境名字}
```


退出当前环境（停止激活当前环境）：

```
source deactivate
```

环境的销毁：

```
conda env remove -n {需要创建环境的名字}
```

### conda 的包管理

conda 的包是什么？

- 既一系列的程序，可供其他程序使用或者直接使用

从哪里下载安装？

- 从 anaconda 软件源（或者成为 conda 软件源）上下载安装，也就是从 channel 上下载
  - anaconda 官方会维护一个软件源， https://anaconda.org/anaconda/
  - 第三方亦可提供符合 conda 规范的软件源
    - conda-forge https://conda-forge.org/
    - etc.
  - 每一个独立的软件源就是 channel

- 如果 anaconda 软件源上没有，既无法安装

包的安装：

```
conda install -n {环境名} {包名}
```

默认的环境为 base 既安装以后就有的环境

包的卸载：

```
conda remove -n {环境名} {包名}
```

