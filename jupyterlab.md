# JupyterLab 基本使用介绍


## 安装

注意：JupyterLab 需要 Python 3

### 安装方法一：使用 pip 安装

```
pip install jupyterlab
```

### 安装方法二：使用 conda 安装

```
conda install -c conda-forge -n {env_name} jupyterlab
```

### 安装方法三：使用 conda env 配置文件安装

创建一个 conda env 配置文件，文件名为 environment.yml，内容为：

```yml
name: jupyterlabenv
channels:
  - conda-forge
dependencies:
  - jupyterlab
```

其中的 name 项可以根据需要修改

然后执行 conda env create -f environment.yml 即可建立一个有 jupyterlab 的名为 jupyterlabenv 的 conda env

然后执行：

```
conda activate jupyterlabenv
jupyter lab
```

就可以运行 jupyterlab