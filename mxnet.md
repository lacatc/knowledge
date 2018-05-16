# MXNet

## 安装

MXNet 官网上关于安装部分的说明感觉不是很好，

当前，最好的安装 mxnet 的方法是通过 anaconda 的 conda 来进行安装

具体：

1. 建立一个独立的环境来安装 mxnet，这个环境命名为 mxnetenv

```
conda create -n mxnetenv
```

2. 安装 mxnet

```
conda insatll -n mxnetenv mxnet
```

安装完毕

验证是否安装成功：

1. 激活环境

```
source activate mxnetenv
```

2. 运行解释器

```
python
```

3. 测试导入

```
import mxnet
```

如果没有保存，证明安装成功