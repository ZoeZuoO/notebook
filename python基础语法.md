# python基础语法

#### 编码

Python 3 源码文件以 **UTF-8** 编码，所有字符串都是 unicode 字符串

为源文件指定编码：

```python
# -*- coding: cp-1252 -*-
```

#### 标识符

* 第一个字符必须是字母表中字母或下划线 **_** 。
* 标识符的其他的部分由字母、数字和下划线组成。
* 标识符对大小写敏感。

#### **逻辑运算符**

内部优先级：not>and>or

外部优先级：算数>比较>逻辑

#### 成员运算符

in：存在

not in：不存在

不可拆分数据类型不能用成员运算符，数值类型就是一种不可拆分的类型

#### python保留字

可查看keyword模块查看关键字

```python
>>> import keyword
>>> keyword.kwlist
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

#### 注释

Python中单行注释以 **#** 开头
多行注释可以用多个 # 号，还有 ''' 和 """

#### 多行语句

* 可使用反斜杠**\\**连接

* 在 [], {}, 或 () 中的多行语句，不需要使用反斜杠 **\\**

*  同一行显示多条语句时，语句之间用分号**;**分割

#### import 与 from...import

在 python 用 **import** 或者 **from...import** 来导入相应的模块。

将整个模块(somemodule)导入，格式为： **import somemodule**

从某个模块中导入某个函数,格式为： **from somemodule import somefunction**

从某个模块中导入多个函数,格式为： **from somemodule import firstfunc, secondfunc, thirdfunc**

将某个模块中的全部函数导入，格式为： **from somemodule import ***

## 空行

函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。

空行与代码缩进不同，空行并不是 Python 语法的一部分。书写时不插入空行，Python 解释器运行也不会出错。但是空行的作用在于分隔两段不同功能或含义的代码，便于日后代码的维护或重构。

**记住：**空行也是程序代码的一部分。

## 赋值

*号 将多个值给到一个变量[数据类型]

![image-20221125170240035](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221125170240035.png)

![image-20221117152802651](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221117152802651.png)

## python标准数据类型

* Python 中的变量不需要声明。每个变量在使用前都必须赋值，变量赋值以后该变量才会被创建。

* string、list 和 tuple 都属于 sequence（序列）

#### 不可变数据类型：

1. ### **数字Number类型**

   python中数字有四种类型：**整数、布尔型、浮点数和复数**。

   -   **int** (整数), 如 1, 只有一种整数类型 int，表示为长整型，没有 python2 中的 Long。
   -   **bool** (布尔), 如 True。
   -   **float** (浮点数), 如 1.23、3E-2

   * **complex** (复数)：,如 1 + 2j、 1.1 + 2.2j，复数由实数部分和虚数部分构成，可以用a + bj,或者complex(a,b)表示， 复数的实部a和虚部b都是浮点型

   **注意：** 

   1. 内置的 **type() 函数**和**instance()函数**可以用来查询变量所指的对象类型

   * isinstance 和 type 的区别在于：

     * type()不会认为子类是一种父类类型。

     * isinstance()会认为子类是一种父类类型。

   2. Python3 中，bool 是 int 的子类，True 和 False 可以和数字相加，* **True==1、False==0** *会返回* **True***，但可以通过* **is** *来判断类型。*

   当你指定一个值时，Number 对象就会被创建：

   ```python
   var1 = 1
   ```

   也可以使用del语句删除一些对象引用。

   del语句的语法是：

   ```python
   del var
   del var_a, var_b
   ```

   **数值运算**：

   ```python
   >>> 2 / 4  # 除法，得到一个浮点数
   0.5
   >>> 2 // 4 # 除法，得到一个整数
   0
   >>> 2 ** 5 # 乘方
   32
   ```

   

2. ### **字符串（String）类型**：属于特殊的元组类型

   1. Python 中的字符串不能改变。

   **引号：**

   1. Python 中单引号 **'** 和双引号 **"** 使用完全相同。
   2. 使用三引号(**'''** 或 **"""**)可以指定一个多行字符串。

   **转义：**

   1. 转义符 **\\**
   2. 反斜杠可以用来转义，使用 **r** 可以让反斜杠不发生转义。 如 **r"this is a line with \n"** 则 **\n** 会显示，并不是换行。 r 指 raw，即 raw string，会自动将反斜杠转义。

   ![image-20221127120939180](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127120939180.png)

   ![image-20221127121034286](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127121034286.png)

   **字符串连接：**

   1. 字符串可以用 **+** 运算符连接在一起，用 ***** 运算符重复。

   **字符串索引：**

   1. Python 中的字符串有两种索引方式，从左往右以 **0** 开始，从右往左以 **-1** 开始。

   **字符串类型：**

   1. Python 没有单独的字符类型，一个字符就是长度为 1 的字符串。

   **字符串截取：**

   1. 字符串的截取的语法格式如下：**变量[头下标:尾下标:步长]**

   **将字符串填充入指定列方法**

   1.  string自带方法
   2.  Template方法

   **将值转化为字符串**

   1. str()：适于人阅读
   2. repr()：供解释器读取的形式

   **字符串类型的格式化**                                 

   ![image-20221123125731646](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221123125731646.png)

   ![image-20221123125631901](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221123125631901.png)

   ![image-20221123125904134](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221123125904134.png)

   ![image-20221123130105926](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221123130105926.png)

3. ### **Tuple**：属于序列类型

   * 元组的元素一旦被创建则**不能修改**，但可包含可变的对象，比如list
   * 元组写在小括号 **()** 里，元素之间用逗号隔开
   * 元组中的元素类型也可以不相同
   * 可被索引
   * 可被截取
   * 字符串可看作一种特殊的元组
   * 构造包含 0 个或 1 个元素的元组**需要注意特殊语法规则**

   ```python
   tuple = ( 'abcd', 786 , 2.23, 'runoob', 70.2  )
   tup1 = ()    # 空元组
   tup2 = (20,) # 一个元素，需要在元素后添加逗号
   ```

![image-20221127120955326](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127120955326.png)

![image-20221127121028070](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127121028070.png)

#### 可变数据类型：

1. ### **List**：属于序列类型

   * 列表中的元素是可以改变的

   * 列表是写在方括号 **[]** 之间、用逗号分隔开

   * 列表是有序的对象集合

   * 列表中元素的类型可以不相同，它支持数字，字符串甚至可以包含列表（所谓嵌套）。

   * ```
     变量[头下标:尾下标]
     ```

     索引值以 **0** 为开始值，**-1** 为从末尾的开始位置。

   * 未使用[]或list()定义列表，仅使用赋值，则等于重新命名，不等于重新创建了一个列表
     
   * List 内置方法：例如 append()、pop() 

   * 列表同样可以被索引和截取，列表被截取后返回一个包含所需元素的新列表

   ```python
    # inputWords[-1::-1] 有三个参数
       # 第一个参数 -1 表示最后一个元素
       # 第二个参数为空，表示移动到列表末尾
       # 第三个参数为步长，-1 表示逆向
       inputWords=inputWords[-1::-1]
   ```

   **列表推导式**

   ```python
   [表达式 for 变量 in 列表] 
   [out_exp_res for out_exp in input_list]
   
   或者 
   
   [表达式 for 变量 in 列表 if 条件]
   [out_exp_res for out_exp in input_list if condition]
   ```

   ![image-20221127120959464](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127120959464.png)

   ![image-20221127121023250](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127121023250.png)

   ![image-20221127121719991](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127121719991.png)

   ![image-20221127121840653](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127121840653.png)

   序列类型应用场景：

   1. 元素遍历

   ![image-20221127122055632](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127122055632.png)

   2. 数据保护

   ![image-20221127122120654](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127122120654.png)

2. ### **Set**：集合

   * **无序**的**不重复元素**序列。
   * 可以使用大括号 **{ }** 或者 **set()** 函数创建集合
   * **若是空集合则必须用set()**
   * 输出集合时，重复的元素会被自动去掉

   **添加元素**

   * s.add(x)，如果元素已存在，则不进行任何操作
   * s.update(x)，参数可以是列表，元组，字典

   **移除元素**

   * s.remove(x)，如果元素不存在，则会发生错误
   * s.discard(x)，如果元素不存在，不会发生错误

   **随机删除集合中的一个元素**

   s.pop()，set 集合的 pop 方法会对集合进行无序的排列，然后将这个无序排列集合的左面第一个元素进行删除。

   **计算集合元素个数**

   len(s)

   **清空集合**

   s.clear()

   **判断元素是否在集合中存在**

   x in s

   **集合推导式**

   ```python
   >>> a = {x for x in 'abracadabra' if x not in 'abc'}
   >>> a
   {'r', 'd'}
   ```

   ![image-20221127115907405](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127115907405.png)

   ![image-20221127115927998](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127115927998.png)

   ![image-20221127120104129](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127120104129.png)

   ![image-20221127120155159](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127120155159.png)

   while的方式遍历集合：

   ![image-20221127120337062](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127120337062.png)

   集合类型应用场景：

   1. 包含关系比较

   ![image-20221127120558170](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127120558170.png)

   2. 数据去重

   ![image-20221127120630458](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127120630458.png)

3. ### **Dictionary**

   * 字典用 **{ }** 标识，它是一个无序的 **键(key) : 值(value)** 的集合，字典是无序的对象集合
   * 键(key)必须使用不可变类型
   * 在同一个字典中，键(key)必须是唯一的
   * 字典类型也有一些内置的函数，例如 clear()、keys()、values() 等

   ```python
   print (tinydict.keys())   # 输出所有键
   print (tinydict.values()) # 输出所有值
   >>> dict([('Runoob', 1), ('Google', 2), ('Taobao', 3)])
   {'Runoob': 1, 'Google': 2, 'Taobao': 3}
   >>> {x: x**2 for x in (2, 4, 6)}
   {2: 4, 4: 16, 6: 36}
   >>> dict(Runoob=1, Google=2, Taobao=3)
   {'Runoob': 1, 'Google': 2, 'Taobao': 3}
   ```

   **字典推导式**
   
   ```python
   { key_expr: value_expr for value in collection }
   
   或
   
   { key_expr: value_expr for value in collection if condition }
   ```
   
   ![image-20221123124052619](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221123124052619.png)
   
   ![image-20221123124242164](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221123124242164.png)

### python输入

input()

### python输出

**print** 默认输出是换行的，如果要实现不换行需要在变量末尾加上 **end=""**

```python
print( x, end=" " )
```

1. **输出值方法**：

1. 表达式语句
2. print()
3. write()——sys.stdout

2. end **关键字**

关键字end可以用于将结果输出到同一行，或者在输出的末尾添加不同的字符

```python
print(b, end=',')
```

3. **对输出做更多格式控制**

1. str.format()
2. 自行处理，字符串切割与连接

### 条件控制

if语句的关键字为：**if – elif – else**

**while 循环**

Python 中 while 语句的一般形式：

```python
while 判断条件(condition)：
    执行语句(statements)……
```

你可以使用 **CTRL+C** 来退出当前的无限循环

**while 循环使用 else 语句**

如果 while 后面的条件语句为 false 时，则执行 else 的语句块。

语法格式如下：

```python
while <expr>:
    <statement(s)>
else:
    <additional_statement(s)>
```

**for 语句**

Python for 循环可以遍历任何可迭代对象，如一个列表或者一个字符串。

for循环的一般格式如下：

```python
for <variable> in <sequence>:
    <statements>
else:
    <statements>
```

**range()函数**

* 如果你需要遍历数字序列，可以使用内置range()函数。它会生成数列：

  ```python
  for i in range(5):
  ...     print(i)
  ...
  0
  1
  2
  3
  4
  ```

* 也可以使用range指定区间的值：

  ```python
  for i in range(5,9) :    
      print(i)      
      
  5 
  6 
  7 
  8
  ```

* 也可以使range以指定数字开始并指定不同的增量(甚至可以是负数，有时这也叫做'步长'):

  ```python
  for i in range(0, 10, 3) :    
  print(i)      
  
  0 
  3 
  6 
  9
  ```

**pass 语句**

Python pass是空语句，是为了保持程序结构的完整性。

pass 不做任何事情，一般用做占位语句

### python迭代器

迭代器有两个基本的方法：**iter()** 和 **next()**。

**创建一个迭代器**

把一个类作为一个迭代器使用需要在类中实现两个方法

```python
__iter__()和__next__()
```

**StopIteration**

StopIteration 异常用于标识迭代的完成，防止出现无限循环的情况，在 __next__() 方法中我们可以设置在完成指定循环次数后触发 StopIteration 异常来结束迭代。

在 Python 中，使用了 yield 的函数被称为生成器（generator）

**生成器**

跟普通函数不同的是，生成器是一个返回迭代器的函数，只能用于迭代操作，更简单点理解生成器就是一个迭代器。

在调用生成器运行的过程中，每次遇到 yield 时函数会暂停并保存当前所有的运行信息，返回 yield 的值, 并在下一次执行 next() 方法时从当前位置继续运行。

调用一个生成器函数，返回的是一个迭代器对象。

## 模块

import

from... import

from … import *：引入的其它来源的命名，很可能覆盖了已有的定义。不要经常使用

## __name__属性

一个模块被另一个程序第一次引入时，其主程序将运行。如果我们想在模块被引入时，模块中的某一程序块不执行，我们可以用__name__属性来使该程序块仅在该模块自身运行时执行。

 每个模块都有一个__name__属性，当其值是'__main__'时，表明该模块自身在运行，否则是被引入。

## dir() 函数

内置的函数 dir() 可以找到模块内定义的所有名称。以一个字符串列表的形式返回

如果没有给定参数，那么 dir() 函数会罗列出当前定义的所有名称

## 包

目录只有包含一个叫做 __init__.py 的文件才会被认作是一个包

最简单的情况，放一个空的 :file:__init__.py就可以了。当然这个文件中也可以包含一些初始化代码或者为（将在后面介绍的） __all__变量赋值。

## GET请求

1. 带参数的请求
2. 携带Session参数
3. 请求Prepared Request

## lambda函数

![image-20221123125123536](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221123125123536.png)

## 函数

函数的表示：def定义

![image-20221123125319773](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221123125319773.png)

## Time库

![image-20221123130258692](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221123130258692.png)

## random库

1.random库是使用随机数的python标准库

2.伪随机数：采用梅森旋转算法生成的伪随机序列中元素

使用方法：Import random

基本随机数函数：

1.seed，初始化给定的随机数种子，默认为当前系统时间

random.seed(10) #产生种子10对应的序列

2.random，生成一个[0.0,1.0)之间的随机小数

random.random()

默认的种子是：当前调用第一次random函数所对应的系统时间

扩展随机数函数：

1.randint(a,b),生成一个[a,b]之间的整数

2.randrange(m,n,[,k]),生成一个[m,n)之间以k为步长的随机整数

3.gettrandbits(k) 生成一个k比特长的随机整数

4.uniform(a,b)生成一个[a,b]之间的随机小数，小数点后16位精度

5.choice(seq)，从序列seq中随机选择一个元素

6.shuffle(seq)将序列seq中元素随机排列，返回打乱后的序列

蒙特卡罗方法：

![蒙 特 卡 罗 方 法 ](file:///C:/Users/Administrator/AppData/Local/Packages/Microsoft.Office.OneNote_8wekyb3d8bbwe/TempState/msohtmlclip/clip_image001.png)

## Pyinstaller

![image-20221123131017529](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221123131017529.png)

![image-20221123131148124](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221123131148124.png)

## jieba库

中文分词第三方库

**安装**：pip install jieba

**三种模式：**

精确模式（最常使用）：把文本精确的切分开，不存在冗余单词

全模式：把文本中所有可能的词语都扫描出来，有冗余

搜索引擎模式：在精确模式基础上，对长词再次切分

**常用函数：**

![image-20221127122632244](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127122632244.png)

![image-20221127122617552](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221127122617552.png)