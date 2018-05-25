# 数据分析项目范例

## 前提

- 了解 anaconda 、 conda 环境
- 了解 jupyter notebook、lab 基本使用
- 了解 markdown
- 了解 git 基本使用
- 了解 git 库托管服务

## 对于新项目的数据分析项目工作步骤

Tips:

- 一个工作项目总的文件类型：
  - readme.md ，必要， markdown 格式，介绍项目以及必要的说明
  - environment.yml，conda 使用的环境描述，用来快速搭建环境
  - *.ipynb，分析过程的 notebook 文件
  - *.md，文档，markdown 格式
  - *.html 由 ipynb 导出的报告
  - 数据文件，csv、pickle 等


### 1. 新建分析项目文件夹

本范例以分析泰坦尼克乘客获救情况数据为示范展开


Tips:

- 目录名要有意义，可以用中文名

```
mkdir titanic-passengers-data-analysis
```

### 2. 将此目录创建为版本库

```
cd titanic-passengers-data-analysis
git init
```

### 3. 创建 readme.md 文件，编写必要的说明

### 4. 进行相关工作

### 5. 在工程中有 git 的操作


## 对于参与到已有的数据分析项目工作步骤

### 1. 在版本库托管平台进行 fork 操作

### 2. 个人远端库 clone 到本地开始操作

## 对于希望使用三库模型进行协助的：

- 如果核心库已经存在，既直接参与即可
- 如果核心库还不存在，则在 Tower 上给管理员安排任务去建立核心库