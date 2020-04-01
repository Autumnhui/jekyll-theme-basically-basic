---
author: Autumnhui
layout: post
title:  📒Python数据分析第二周笔记
date:   2020-03-30
categories:
     - Python数据分析
---

# 📒Python数据分析第二周笔记

## 🔍1.Pandas模块的介绍

> Pandas是一个强大的分析结构化数据的工具集；它的使用基础是Numpy（提供高性能的矩阵运算）；用于数据挖掘和数据分析，同时也提供数据清洗功能。[中文文档](https://www.pypandas.cn/)

总的来说，pandas就是Python中用来处理数据（json、excel、csv...等数据文件）的模块，它非常强大，并且可以将数据输出以可视化的数据图像、表格（数据帧）等。

## 📊2.Pandas处理数据

### ✂️2.1常用的处理方式

在pandas中我们常用的处理数据的方式是使用 `pandas.DataFrame() ` 进行表格型数据结构的创建，里面包含”行“(index/row)和”列“(columns)，数据可以来源列表，嵌套的字典也可以创建DataFrame。（外层字典的键作为列，内层键作为索引）

通常来说:
- 竖的列（columns)放变数(variables)
- 横的行（row）放观察（observations）

<b>小细节</b>
- pd.DataFrame 的主流参数是 *字典*
- 该字典的键keys是由变数构成，相当於表格中一行行的标题
- 该字典的值values是由观察的列表构成，相当於表格中一行行的数据
- 表格真的要是表格, 该字典的每个观察的列表数量必需齐一

### 🧬2.2 DataFrame的结构

示例代码：

```
框框 = pd.DataFrame ( {
        "变数X": ["观察X1", "观察X2", "观察X3", "观察X4"],
        "变数Y": ["观察Y1", "观察Y2", "观察Y3", "观察Y4"],
        "变数Z": ["观察Z1", "观察Z2", "观察Z3", "观察Z4"],
      } )
display (框框)
```

可见，我们的DataFrame的结构是很明显的，以来便于数据处理者更直观明了去处理，二来结构性的东西看起来也更舒服。（记得数据后面的”,“）

### 🔌2.3 DataFrame取值

1.取值最简单的方法是类似字典的"dict[]"直接取值，代码如下：

`框框 ["变数X"] `

输出结果为

```
0    观察X1
1    观察X2
2    观察X3
3    观察X4
Name: 变数X, dtype: object
```

2. 使用.values进行取值，代码如下：

`框框 ["变数X"].values`

输出结果为

`array(['观察X1', '观察X2', '观察X3', '观察X4'], dtype=object)`

3. 使用.index进行索引，代码如下

`框框 ["变数X"].index`

输出结果为

`RangeIndex(start=0, stop=4, step=1)`

如果将其转换成列表：

`list(框框 ["变数X"].index)`

就输出为

`[0, 1, 2, 3]`

4.使用.loc['']进行取值，相当于进行标签索引。

在此补充.loc[]函数的两种使用方法，当.loc['a']意思为索引行'a'的数据；当.loc[1]为索引第一行的数据。

也可以同时输出行列：
`框框.loc[[1,3],['变数X’,'变数Y']]`
表示取1，3行的变数X,变数Y中的所有值。*若为[1:3]则代表第一行到第三行。*

.loc & .iloc 两种函数的详细讲解见[博客](https://www.cnblogs.com/ghllfl/p/8481576.html)

## 📷Pandas读取数据

pandas可以直接调用方法来读取数据文件（如excel、tsv、csv等），方法如下：

```
pd.read_csv("路径档案名", encoding="utf8") #读csv

pd.read_csv("路径档案名", encoding="utf8", sep="\t") #读tsv，注意与csv不同的是间隔符sep为'\t'

pd.read_excel("路径档案名", sheet_name="分页名称") #可以加上sheet_name为分表名
```

#### 🔋补充

关于Pandas的DataFrame常用的方法有几种([参考来源](https://www.cnblogs.com/shixp/p/10761594.html))：

- head() >>>用于查看数据的前5行
- info() >>>用于快速查看数据的描述，例如总行数，每个属性的类型以及非空值的数量
- value_counts() >>>查看某一列数据中都有哪些类别，以及每个类别中数据的数量。
- describe() >>>显示数值属性的概括，count 是数据的数量；mean, min, max 分别表示平均值，最小以及最大值；std 是标准差，用来揭示数据分散度；25% 50% 75% 对应分位数
- reset_index() >>>用于生成新的索引 id。因为一旦数据发生合并，其索引 id 仍然引用原来的，这样 id 会重复。使用此方法后，生成新的按照顺序的 id，原来的索引 id 会变成列名为 index 的一列。若将参数 drop 的值设为 True，则 index 这一列会被删除。

## 🔪Pandas的DataFrame的切片方法

> 👨‍🏫以下为课堂笔记示例代码。

####  列子集
```python

df.loc[]
df.iloc[]
df.set_index()
df.head(n)
df.tail(n)
df.nlargest(n, '变量') # 最大 ， n是多少个
df.nsmallest(n, '变量') # 最小
df[df.估值（亿人民币）> 10]
```

#### 行子集
```python

#  行子集
df[['变量X','变量Y','变量Z']] #可以拿来重新排序
df[['变量X']]
df['变量X']
```

#### 列+行子集
```python

#  行子集
df.loc[:,['变量X':'变量Z']]    # 注意中括号里的: 和 ,的使用
df.iloc[:,[1,2,5]]
df.loc[df['变量X']>10, ['变量X','变量Z'] ]   
```

 <b> 📒</b>
> 行、列串列，先行再列

df["排名","企业名称","估值（亿人民币）"]].df.xxxx()

---

在这里课上讲的并不是很清楚，在网路上查询了相关的内容，总结的比较好的有如下两个博客内容。*示例代码在本周ipynb文件中2.3处。*

1. [小白的总结](https://www.cnblogs.com/ywjfx/p/10837021.html)
2. [Asher117的总结](https://blog.csdn.net/asher117/article/details/83656584)

感谢两位的详细叙述。

## 👨‍🎨Pandas还能出图

对于由阿拉伯数字组成的数据，人类的视觉性化让我们更加喜欢看图，即便它或许有些许难懂。相较于数字而言，直观的图像更能让我们感受到数据的力量。

pandas的DataFrame能使用plot方法进行数据图像的绘制，让我们能够更清楚的去理解数据，去探究数据的价值，带来更多的信息。

但是关于plot画图，课上提及也并不详细，相关博客中的讲解受益更多。详见[marsggbo的博客](https://www.cnblogs.com/marsggbo/p/11765143.html)

## 🔫进阶处理数据

### 🧨数据行/列处理

对于数据表，我们在Excel中可以通过整行、整列去处理表格中的内容。同样，pandas的DataFrame也可以做到做行列的数据处理，通过行列转换、增加行/列得到新的数据框。

示例代码：

```

df['新变量'] = df['变量X'] + df['变量Y']
df['新变量'] = [ 转换(x) for x in df['变量Y'] ]     # 列表推导转换

```

### 💣数据计算

求和？计数？平均值？最大/小值？pandas的DataFrame统统能给你搞定。

示例代码：

```

df.describe()
df.describe(include=all)

df.count()
df.sum()

df.min()
df.max()
df.mean()
df.median()

df.var()
df.std()
```

---

[📦点击查看源码](https://github.com/Autumnhui/Learn_PythonDA/blob/master/Record%20of%20Learning/week02/20%E6%98%A5_pandas_week02.ipynb)

### 一些关于pandas的资料.

1.[pandas基础](https://github.com/Autumnhui/Learn_PythonDA/blob/master/Record%20of%20Learning/week02/Python%E6%95%B0%E6%8D%AE%E7%A7%91%E5%AD%A6%E9%80%9F%E6%9F%A5%E8%A1%A8%20-%20Pandas%20%E5%9F%BA%E7%A1%80.pdf)
2.[pandas进阶](https://github.com/Autumnhui/Learn_PythonDA/blob/master/Record%20of%20Learning/week02/Python%E6%95%B0%E6%8D%AE%E7%A7%91%E5%AD%A6%E9%80%9F%E6%9F%A5%E8%A1%A8%20-%20Pandas%20%E8%BF%9B%E9%98%B6.pdf)