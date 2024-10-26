# R语言提纲

## 1 基本语法

### 1.1 准备工作

`getwd()` 输出当前工作目录的绝对路径

`file.create() `创建文件

`setwd()` 切换工作目录

在 RStudio 中回到工作目录：Files -> More -> Go To Working Directory

保存工作空间：Session -> Save Workspace As

加载工作空间：Session -> Load Workspace

### 1.2 常用函数和指令

`install.package() `安装程序包

```R
install.packages("BiocManager")
BiocManager::install(c("trackViewer"))
```

`library() `载入程序包

`ls()` 查看当前工作区所有变量

`remove(..., list = character()) `删除指定变量

`View() `查看指定变量的值

`?xxx` 查看帮助，示例：`is.numeric`

`print() `将内容打印到屏幕上

`Ctrl + L` RStudio 清空控制台

`Ctrl + Shift + A` RStudio 格式化选中的代码

### 1.3 数据类型

- 数值型 numeric

  - 整型 integer

    末尾加L（CSV文件导入的正好相反）

  - 浮点型 double

    默认（CSV文件导入的正好相反）

- 字符型 character

- 逻辑型 logical

- 复数型 complex

判断类型：`is.xxx()`，示例：`is.numeric()`

转换类型：`as.xxx()`，示例：`as.numeric()`

类型升档：logical < integer < double < character

### 1.4 数据结构

#### 1.4.1 向量、矩阵、数组 

- 元素类型相同
- 访问指定的行和列，示例：

​	`votes[row, column]`

​	可缺省。

​	可用 `:` 表示范围。

- `unique()` 去重

#### 1.4.2 数据框

- `data.frame() `创建一个数据框
- 使用列名访问指定列得到一个向量，示例：

​	`votes$candidate`

​	总结：从 1 开始计数，只有列名，没有行名（所谓行名只是行的序号，且无法通过 $ 访问特定的行）。

- 用以上两种方式访问一整列都会返回一个向量。

- 使用以下方式会得到一个数据框，而非一个向量：

​	`votes[1]`

- 新增一个列，示例：

  `votes$total <- votes$poll + votes$mail`

- `colnames() `获取列名

  `rownames()` 获取行名（所谓行名只是行的序号）

- `ncol() `获取列数

  `nrow() `获取行数

- `with() `在某个数据框的环境下执行指定的语句

#### 1.4.3 因子

- `factor(x = character(), levels, labels = levels, exclude = NA)`

  示例：

  ```R
  factor(
      votes$Q21,
      labels = c("?", "Yes", "No", "Unsure/Undecided"),
      exclude = c(-1)
  )
  ```

#### 1.4.4 列表

一些变量的有序集合

- 元素类型可以不同
- `list()` 创建列表
- 提供 R 分析结果输出包装： 输出一个变量， 这个变量包括回归系数、预测值、残差、检验结果等等一系列不能放到规则形状数据结构中的内容。 
- 实际上，数据框也是列表的一种， 但是数据框要求各列等长， 而列表不要求。数据框可以理解为每一个元素都是等长向量的列表。

### 1.5 四则运算、常用的数学函数

- `+` 加
- `-` 减
- `*` 乘
- `/` 除
- `sum()` 求和
- `ceiling()` 向上取整
- `sign()`  判断符号
- `abs()` 求绝对值
- `log()` 对数函数
- `sin()` 正弦函数
- `polyroot()` 求函数零点

注意：以上符号和函数大多都支持向量运算

### 1.6 自定义函数

语法：`函数名 <- function(形式参数表) 函数体`

示例：

```R
sum <- function(a, b) {
	a + b
}
```

### 1.7 程序控制结构

- 表达式

  R 是一个表达式语言, 其任何一个语句都可以看成是一个表达式。 表达式之间以分号分隔或用换行分隔。 表达式可以续行, 只要前一行不是完整表达式（比如末尾是加减乘除等运算符, 或有未配对的括号）则下一行为上一行的继续。 若干个表达式可以放在一起组成一个复合表达式, 作为一个表达式使用，复合表达式的值为最后一个表达式的值， 组合用大括号表示, 如：

  ```R
  {
    x <- 15
    x
  }
  ```

- 分支

- 循环

## 2 实际应用

### 2.1 数据导入

#### 2.1.1 用户手动输入

`readline()`

#### 2.1.2 导入 CSV 文件

- `read.table(file, header = FALSE, sep = "")`

  示例：

  ```R
  votes <- read.table(
  	"votes.csv",
  	sep = ",",
  	header = TRUE
  )
  ```

- `read.csv(file)`

​	`file` the name of the file which the data are to be read from. It can also be a complete URL. 

​	示例：

​	`votes <- read.csv("votes.csv")`

​	`votes <- read.csv("https://github.com/fivethirtyeight/data/raw/master/non-voters/nonvoters_data.csv")`

#### 2.1.3 导入 Excel 表格

### 2.2 数据处理

#### 2.2.1 缺失值处理

- 特殊值
  - `Inf`, `-Inf` infinity ，无穷大
  - `NA` not available ，不可用
  - `NaN` not a number ，不是数字
  - `NULL` 

### 2.3 绘图

### 2.4 数据分析

### 2.5 数据导出

#### 导出 CSV 文件

`write.csv(x, file = "", row.names = TRUE)`

## 3 未来学习方向

### 3.1 tidyverse



### 3.2 面向对象

[R语言面向对象编程：理解R中的S3与S4类](https://baijiahao.baidu.com/s?id=1808593094025260804&wfr=spider&for=pc)

S3 类是 R 语言中最简单的面向对象编程机制，其本质上是一种命名约定，而不是严格定义的类系统。

`Bioconductor` 社区是以 `S4` 对象作为基础框架，只接受 `S4` 定义的 `R` 包。

[R 面向对象编程（一）](https://zhuanlan.zhihu.com/p/358532080)

[R 面向对象编程（二）](https://zhuanlan.zhihu.com/p/358783073)

#### 3.2.1 S3

S3是 R 中第一个也是最简单的 OOP（Object-Oriented Programming，面向对象编程）系统，广泛存在于早期开发的 R 包中，也是 CRAN 包最常用的系统。

S3 的实现基于泛型函数机制，即函数根据传入对象的类型来决定调用哪个方法。

在 S3 中，除了 `NULL` 以外， R 的变量都可以看成是对象， 都可以有属性。 在 R 语言中， 属性是把变量看成对象后， 除了其存储内容之外的其它附加信息。

- 构建对象的方式

  - 使用 `attr(x, which)` 给变量 x 添加一个名为 class 的属性。

  - 使用 `structure()` ，示例：

    ```R
    > b <- structure(2, class='foo')
    > b
    [1] 2
    attr(,"class")
    [1] "foo"
    > otype(b)
    [1] "S3"
    ```

  - 为 `class(x)` 赋值，示例：

    ```R
    > x <- list(a=1)
    > class(x)
    [1] "list"
    > otype(x)
    [1] "base"
    
    > class(x) <- 'foo'
    > class(x)
    [1] "foo"
    > otype(x)
    [1] "S3"
    ```

- 使用 `class()` 获取或修改对象的类型

- `attributes()` 读取对象的所有属性

- `attr(x, which)` 读取或定义 x 的 which 属性

  `attr(x, 'class')` 也可以查看 x 的属性，可以起到和 `class(x)` 相同的作用。

  只要给变量添加一个名为 class 的属性，就可将该变量变为 S3 类型的对象。

- 用 sloop 包的 `otype()` 判断某一变量是何种对象

  示例：

  ```R
  > library(sloop) # 引入sloop包
  > a = 1
  > otype(a) # 没有添加任何属性的变量属于base类型
  [1] "base"
  > attr(a, "label") <- "hello world." # 添加名为class之外的属性后依然属于base类型
  > a
  [1] 1
  attr(,"label")
  [1] "hello world."
  > otype(a)
  [1] "base"
  > attr(a, "class") <- "whatever" # 添加名为class的属性后属于S3类型
  > a
  [1] 1
  attr(,"label")
  [1] "hello world."
  attr(,"class")
  [1] "whatever"
  > otype(a)
  [1] "S3"
  ```

- 还可以将类属性设置为向量，为 `S3` 对象指定多个类型，示例：

  ```R
  > c <- structure(3, class=c('bar', 'foo'))
  > class(c)
  [1] "bar" "foo"
  > otype(c)
  [1] "S3"
  ```

- `UseMethod()` 创建一个泛型函数，示例：

  ```R
  person <- function(x, ...) {
    UseMethod('person')
  }
  ```

- `person.xxx` 定义名为 `xxx` 的方法

  `person.default` 定义默认方法，示例：

  ```R
  person.default <- function(x, ...) {
    print("I am human.")
  }
  
  person.sing <- function(x, ...) {
    print("I can sing")
  }
  
  person.name <- function(x, ...) {
    print(paste0("My name is ", x))
  }
  ```

  验证泛型函数：

  ```R
  > a <- structure("tom", class='sing') # 定义一个class属性为"sing"的变量
  > person.sing(a) # 将该对象a传入person中
  [1] "I can sing"
  ```

  可以看到，调用了 `person.sing()` 方法。

  再尝试其他类型：

  ```R
  > b <- structure("tom", class='name')
  > person(b)
  [1] "My name is tom"
  > person("joy")
  [1] "I am human."
  ```

  可以看到，给`person()`函数输入不同类型的对象就会自动调用相应的方法，对于未指定的类型，会调用`person.default()`方法。这就是泛型函数。

### 3.3 Bioc中的Ranges类

`getClass()` 获取类的所在包、属性、父类、子类，属于S4类

IRanges和GRanges都是S4类

- IRanges

IRanges Extends: Class "Ranges", by class "IPosRanges", distance 3

- GRanges

GRanges Extends: Class "Ranges", by class "GenomicRanges", distance 2

10个基因组ranges，以|为界分为左右两块区域：
 左边：数据【必选】基因组坐标信息(seqnames, ranges, strand)；用granges(gr) 查看
 右边：元数据【可选】基因的注释信息(score, GC 等)； 用mcols(gr)查看，用 mcols(gr)$score 查看具体的元数据项
 元数据：描述一个文件特征的系统数据，如访问权限、文件拥有者以及文件数据块的分布信息等等
 width() 统计基因组序列长度分布；length() 计算行数；names() 查看最前列的名称

## 参考网站

[北京大学：R语言教程](https://www.math.pku.edu.cn/teachers/lidf/docs/Rbook/html/_Rbook/index.html)

[Bilibili：哈佛大学 R语言编程入门2024|CS50R Introduction to Programming with R](https://www.bilibili.com/video/BV1Vw4m1e75r/?p=2&spm_id_from=pageDriver&vd_source=b3328ecaea4c890b0870cbe5c6c5e30c)

[微信小程序科研七点半：有了这个R包再也不用PPT绘制基因结构和变异位置](https://mp.weixin.qq.com/s/bcUphx5t01zk1oSpQWNK4A)

- GRange

[知乎：IRanges包学习笔记](https://zhuanlan.zhihu.com/p/384853636)

[简书：bioconductor入门第二弹--GRanges概述](https://www.jianshu.com/p/4ea1ac971517)

[简书：【必学Bioconductor包300个】GenomicRanges](https://www.jianshu.com/p/addde37b7b48)

[Bioconductor官网：GenomicRanges](https://bioconductor.org/packages/release/bioc/html/GenomicRanges.html)

- Rle

[PLoB：R/BioC序列处理之五：Rle和Ranges](https://www.plob.org/article/7594.html)

- maftools

[简书：maftools画棒棒糖图 （Lollipop chart）-基因突变可视化](https://www.jianshu.com/p/7c9dd33deda3)

[知乎：maftools癌症体细胞变异(突变)分析工具学习](https://zhuanlan.zhihu.com/p/717782250)

## 实用工具

Typora

Snipaste

[通义千问](https://tongyi.aliyun.com/qianwen/?spm=5176.28103460&code=33wdenjgi9&utm_content=se_1019048260&st=null)
