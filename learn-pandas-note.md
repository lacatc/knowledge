## 用于记录学习 ***pandas*** 过程中所遇到常见函数使用方法
* 建议通过学习《利用 python 进行数据分析》来学习 *pandas*

### [merge](http://www.jianshu.com/p/b07bc5c650ea)
```
merge(left, right, how='inner', on=None, left_on=None, right_on=None,
      left_index=False, right_index=False, sort=True,
      suffixes=('_x', '_y'), copy=True, indicator=False) 
```
* 参数说明

1. left与right：两个不同的DataFrame
2. how：指的是合并(连接)的方式有inner(内连接),left(左外连接),right(右外连接),outer(全外连接);默认为inner
3. on : 指的是用于连接的列索引名称。必须存在右右两个DataFrame对象中，如果没有指定且其他参数也未指定则以两个DataFrame的列名交集做为连接键
4. left_on：左则DataFrame中用作连接键的列名;这个参数中左右列名不相同，但代表的含义相同时非常有用。
5. right_on：右则DataFrame中用作 连接键的列名
6. left_index：使用左则DataFrame中的行索引做为连接键
7. right_index：使用右则DataFrame中的行索引做为连接键
8. sort：默认为True，将合并的数据进行排序。在大多数情况下设置为False可以提高性能
9. suffixes：字符串值组成的元组，用于指定当左右DataFrame存在相同列名时在列名后面附加的后缀名称，默认为('_x','_y')
10. copy：默认为True,总是将数据复制到数据结构中；大多数情况下设置为False可以提高性能
11. indicator：增加了一个显示合并数据中来源情况；如只来自己于左边(left_only)、两者(both)

### [groupby](http://blog.csdn.net/leonis_v/article/details/51832916)
pandas提供了一个灵活高效的groupby功能，它使你能以一种自然的方式对数据集进行切片、切块、摘要等操作。根据一个或多个键（可以是函数、数组或DataFrame列名）拆分pandas对象。计算分组摘要统计，如计数、平均值、标准差，或用户自定义函数。对DataFrame的列应用各种各样的函数。应用组内转换或其他运算，如规格化、线性回归、排名或选取子集等。计算透视表或交叉表。执行分位数分析以及其他分组分析。