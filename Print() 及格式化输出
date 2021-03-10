# Print() 及格式化输出



## Print() 

### 语法：

**print**(`*objects`, `sep=' '`, `end='\n'`, `file=sys.stdout`, `flush=False`)  

将 objects 打印到 file 指定的文本流，以 sep 分隔并在末尾加上 end 。   

* `objects`：为复数，表示可以一次输出多个对象。输出多个对象时，需要用逗号分隔。如果没有给出 objects，则 print() 将只写入 end，即输出一个换行。
* `sep`：用来分隔（_**sep**erate_）多个对象，可以在''内指定分隔符或分隔的内容，如果忽略该项，则使用默认值：`空格`。
* `end`：用来设定以什么结尾。默认值是`换行符` \n。也可以对sep，end赋值，如：sep = s,但s必须为字符串类型的变量。
* `file`：要写入的文件对象。参数必须是一个具有 write(string) 方法的对象；如果参数不存在或为 None，则将使用 sys.stdout。由于要打印的参数会被转换为文本字符串，因此 print() 不能用于二进制模式的文件对象。 对于这些对象，应改用 file.write(...)。
* `flush`：输出是否被缓存通常决定于 file，但如果 flush 关键字参数为真值，流会被强制刷新。

注： sep, end, file 和 flush 如果存在，它们必须以关键字参数的形式给出。所有`非关键字`参数都会被转换为字符串，就像是执行了 str() 一样，并会被写入到流。

print输出的是字符串，所以内部使用单引号''、双引号""、三单双引号''' ''' / “”“ ”“”，跟字符串string是一样的。



### `sep` 和 `end` 的调用

简单举几个例子说明这两个的调用情况

```python
>>> a=123
>>> b="Hello World"
>>> s = ' -- '
>>> print(a, b)
>>> print(a, b, sep = s)
123 Hello World      # 此时没有跨行输出，只调用了sep = ' '的默认值空格，没有调用end
123 -- Hello World   # s是字符串变量，可以调用, 注意不要写成sep = 's'

>>> l = [1,2,3]
>>> for i in range(len(l)):
>>>     print(i, sep = '++', end = ' | ')   # 只调用了end，没有调用sep
0 | 1 | 2 | 

>>> print("Duan""Yixuan")
>>> # 等同于print("Duan"+"Yixuan")，即将两个字符串进行拼接，拼接后即视为一个对象，不调用 end 和 sep
>>> print("Duan","Yixuan")
DuanYixuan
Duan Yixuan
```

从上面代码可以发现，`sep`主要用来分隔***多个对象***，而对于list（列表）等变量而言，只调用`end`，即使list内含有多个元素，也仍是***单个对象***。



## 格式化输出  

数据或内容的输出，经常会涉及到各个类型的数据，包括但不限于：数值型，布尔型，列表变量，字典变量...都可以直接输出。当需要同时输出多种类型的数据时，需要先用格式化符号指明输出的类型及位置，然后在第二个%后面输出指定的变量。

print 常和格式化输出一起使用。

### 1. 占位符介绍 %

目前常用的占位符写法有三种：**%**、**format**、**f表达式**。使用占位符，能够高效地实现字符串的拼接。这种高效、简便在循环结构中更加明显。优点：

- 将字符串中用到的变量集中在一起，方便查找和修改
- 避免了反复使用引号，导致的引号对应识别困难和出错
- 能够更直观的识别句子要表达的内容



#### 1.1  字符串格式化操作符  **%**

> 参考文献：[% (String Formatting Operator)](https://python-reference.readthedocs.io/en/latest/docs/str/formatting.html#string-formatting-operator)

`%` 的**详细语法格式**如下： %\[key]\[flags]\[width]\[.precision][length type]conversion type % values

- `%`: 	必备项，它标记占位符的开始。
- `key`: 可选项，映射的键，由带括号的字符序列组成，一般用于后面的values是是字典的场景。
- `flags`: 可选项，转换标志(Conversion flags), 会影响某些转换类型的结果。
- `width`: 可选项，最小字段宽度。如果指定为“\*”（星号），则实际宽度从值中元组的下一个元素读取，要转换的对象位于最小字段宽度和可选精度之后。*
- `precision`: 可选项，精度，写法为.precision（点+精度）。如果指定为“*”（星号），则实际宽度从值中元组的下一个元素读取，要转换的值位于精度之后。
  length type: 可选项，长度修改器。
- `conversion type`: 必备项，转换类型，也标记占位符的开始。



#### 1.2 Conversion Types：

%\[key]\[flags]\[width]\[.precision][length type]**`conversion type`** % values

| 符号        | 描述                                  | 符号    | 描述                                                       |
| :---------- | :------------------------------------ | ------- | ---------------------------------------------------------- |
| `d`/`i`/`u` | 整数，i、u都是过时的用法，与d相同     | `c`     | 单个字符(接受整数或单个字符串)。                           |
| `s`         | 字符串(使用`str()`转换任何Python对象) | `r`     | 字符串(使用`repr()`转换任何Python对象)，                   |
| `f`/`F`     | 浮点十进制格式                        | `%`     | 不转换参数，结果中会出现' % '字符                          |
| `o`         | 八进制数                              | `x`/`X` | 十六进制数 / （大写）                                      |
| `e`/`E`     | 用科学计数法表示的浮点指数格式。      | `g`/`G` | 浮点格式。指数小于-4或不小于精度则用指数格式，否则用十进制 |

```python
# 不使用占位符
>>> name = "小明" 
>>> age = 4 
>>> print("可爱的" + name + ", 今年" + str(age) + "岁了")

# 使用占位符
>>> print('可爱的%s, 今年%d岁了' % (name, age))

# 不使用print也是可以的，但只能在控制台(Console)使用
# 在脚本中使用，既不报错，也不输出
>>> "可爱的" + name + ", 今年" + str(age) + "岁了"
>>> '可爱的%s, 今年%d岁了' % (name, age)
```

其中 `%s`、`%d` 便是占位符，顾名思义，其作用就是替后面的变量站住这个位置，并指定输出类型，字符串后面的%是一个特殊的操作符，该操作符会将后面的变量值替换掉前面字符串中的占位符。



#### 1.3 precision

写法为**`.precision`（点+精度）。不设置的话，`浮点数`默认精度值是6。

%\[key]\[flags]\[width]\[**`.precision`**][length type]conversion type % values

```python
>>> '%f' % 3.14     # 默认精度值是6.
'3.140000'
>>> '%.2f' % 3.14	# 设定精度为2
'3.14'
```



#### 1.4 width

设置字段的最小占位宽度，默认右对齐，内容不够时使用空格填充，一般和`flags`连用。

%\[key]\[flags]\[**`width`**]\[.precision][length type]conversion type % values

#### 1.5 flags:

%\[key]\[**`flags`**]\[width]\[.precision][length type]conversion type % values

| 符号  | 功能                                                         |
| :---- | :----------------------------------------------------------- |
| *     | 定义宽度或者小数点精度                                       |
| -     | 用做左对齐                                                   |
| +     | 用做右对齐，在正数前面显示加号( + )                          |
| 空格  | 在正数前面显示空格                                           |
| #     | 在八进制数前面显示零('0')，在十六进制前面显示'0x'或者'0X'(取决于用的是'x'还是'X') |
| 0     | 显示的数字前面填充'0'而不是默认的空格                        |
| %     | '%%'输出一个单一的'%'                                        |
| (var) | 映射变量(字典参数)                                           |
| m.n.  | m 是显示的最小总宽度,n 是小数点后的位数(如果可用的话)        |

示例：`#`

```python
>>> "%x" % 17	# 得到的是十六进制的11：1*16+1 = 17
'11'
>>> "%#x" % 17	# 添加#后，十六进制的11前面出现了0x，避免与十进制的11混淆
'0x11'
>>> "%#X" % 17	# X变为大写
'0X11'
>>>"%#o" % 17	# 八进制同理
'0o21'
```

示例 `+` / `-` / `0`

```python
>>> "%d" % 1
'1'
>>> "%03d" % 1	# 指定宽度为3，数字前面用0填充
'001'
>>> "%-5d" % 1	# 宽度为5，左对齐
'1    '
>>> "%0-5d" % 1	# 左对齐时，如果存在0填充，则0被覆盖
'1    '
>>>"%0+5d" % 1	# 1向右对其，前面除+号外，用0填充
'+0001'
>>>"% +5d" % 1	# 使用空格，得到的不是'+   1'
'   +1'
>>>"% +5d" % -1
'   -1'
```

#### 1.6 key

%\[**`key`**]\[flags]\[width]\[.precision][length type]conversion type % values

在使用上述关键字进行输出时，一定要注意关键词的顺序。当右边的参数是一个字典(或其他映射类型)时，字符串中的格式必须包含一个***括号中的映射键***，该映射键插入到' % '字符后面的字典中。映射键从映射中选择要格式化的值。例如:

```python
>>> dct = {'foo': 10, 'bar': 20}	# dict 是python中的关键字，尽量避免重名
>>> # 关键字的顺序为key -> conversion type
>>> "%(foo)s" % dct    # foo是字典dct中的key键值，对应的value为10
'10'
    
>>> print '%(language)s has %(number)03d quote types.' % \
>>> ...       {"language": "Python", "number": 2}
Python has 002 quote types.
```



##### 1.7 格式化输出示例

**`进制转换`**：以指定格式输出内容：格式化输出16进制(`%x`)，十进制(`%d`)，八进制(`%o`)整数

```python
>>> nHex = 0xFF	# 转换为16、10、8进制，注意：0XFF=ff，省略了16进制的开头0X，并且小写了
>>> print("nHex = %x,nDec = %d,nOct = %o" %(nHex,nHex,nHex))
nHex = ff,nDec = 255,nOct = 377
>>> '%x' % 27   # 16进制中a=10,b=11,1b表示1*16+11=27
'1b'
>>> '%o' % 27	# 8进制，3*8+3=27
'33'
>>> '%#o' % 27	# %后添加#会显示8进制的开头0o
'0o33'
```

**`格式转换`**：实际上很多类型都可以转换为字符串%s，这里不做过多介绍

```python
>>> "%s  %d  %d" % ("hello", 3, 3.1415)	# 浮点型3.1415被转换为整型
'hello  3  3'
>>> "%s  %.3f  %f" % ("hello", 3, 3.1415)	# 整型3被转换为浮点型，并保留3个精度
'hello  3.000  3.141500'

>>> for i in range(65,70):
>>>     print('%d=%c; ' % (i,i), end=' ')	# 将整数转换为相应的unicode字符。
65=A;  66=B;  67=C;  68=D;  69=E; 
```

**`批量混合输出`**：同时输出多个类型的数据

```python
>>> name = ['老大', '老二', '老三']
>>> age = [12, 8, 6]
>>> for i in range(len(name)):
>>>     print('%s 已经 %d 岁了' % (name[i], age[i]))
老大 已经 12 岁了
老二 已经 8 岁了
老三 已经 6 岁了
```



### 2. format

> 参考文献：[Format String Syntax](https://docs.python.org/3.6/library/string.html#format-string-syntax)

格式字符串包含用花括号{}括起来的“替换字段”。没有包含在大括号中的任何内容都被认为是字面文本，它被原样复制到输出中。如果需要在字面文本中包含大括号字符，可以通过双引号进行转义:{{和}}。

#### 2.1 语法

下面是一个多层语法的嵌套，具体可理解为（其他以此类推）：

- [ ] replacement_field
  - [ ] field_name
    - [ ] arg_name. attribute_name
    - [ ] arg_name[ element_index ]

```
replacement_field ::=  "{" [field_name] ["!" conversion] [":" format_spec] "}"
field_name        ::=  arg_name ("." attribute_name | "[" element_index "]")*
arg_name          ::=  [identifier | digit+]  # 按位置访问参数
attribute_name    ::=  identifier             # 访问对象的属性参数
element_index     ::=  digit+ | index_string  # 下标访问
index_string      ::=  <any source character except "]"> +

conversion        ::=  "r" | "s" | "a"	

format_spec     ::=  [[fill][align][sign][#][0][width][grouping_option][.precision][type]
fill            ::=  <any character>
align           ::=  "<" | ">" | "^" | "=" ：左右居中对齐、将填充放在符号(如果有)之后数字之前
sign            ::=  "+" | "-" | " "
width           ::=  digit+
grouping_option ::=  "_" | ","
precision       ::=  digit+
type            ::=  "b" | "c" | "d" | "e" | "E" | "f" | "F" | "g" | "G" | "n" | "o" | "s" | "x" | "X" | "%" 
```



#### 2.2  按位置访问参数:

```python
>>> '{0}, {1}, {2}'.format('a', 'b', 'c')
'a, b, c'
>>> '{}, {}, {}'.format('a', 'b', 'c')  	# 索引默认按照升序
'a, b, c'
>>> '{2}, {1}, {0}'.format('a', 'b', 'c')	# 数字即为元组的索引
'c, b, a'
>>> '{2}, {1}, {0}'.format(*'abc')      	# 对参数序列进行拆包
'c, b, a'
>>> '{0}{1}{0}'.format('A', '-')   			# 参数的索引可以重复
'A-A'
```

#### 2.3 按名称访问参数:

```python
>>> "Stu info： {name} {age}".format(name="Lihua", age=24)
'Stu info： Lihua 24'
>>> stu = {'name': 'Lihua', 'age': '24'}		# 字典需要根据key访问其value
>>> 'Stu info: {name}, {age}'.format(**stu)
'Stu info: Lihua, 24'
```

#### 2.4 访问对象的属性参数:

```python
>>> c = 3-5j
>>> ('复数 {0} 由实部 {0.real} '
...  '和虚部 {0.imag}组成').format(c)
 '复数 (3-5j) 由实部 3.0 和虚部 -5.0组成'

>>> class Point:	# 多种语句组合，实现更复杂的功能
...     def __init__(self, x, y):
...         self.x, self.y = x, y
...     def __str__(self):
...         return 'Point({self.x}, {self.y})'.format(self=self)
...
>>> str(Point(4, 2))
'Point(4, 2)'
```

#### 2.5 访问参数的项目:

```python
>>> X = [1,2]		# 变量需为序列类型，能被索引
>>> Y = (3,4)		# 比如元组或列表
>>> 'x1: {0[0]};  x2: {0[1]}; y1: {1[0]};  y2: {1[1]}'.format(X,Y)
'x1: 1;  x2: 2; y1: 3;  y2: 4'
```

#### 2.6 `%s` 和`%r`:

这俩好像没什么区别，在 % 那有介绍

```python
>>> "repr() shows quotes: {!r}; str() doesn't: {!s}".format('test1', 'test2')
"repr() shows quotes: 'test1'; str() doesn't: test2"
```

#### 2.7对齐文本并指定宽度:

```python
>>> '{:<10}'.format('左对齐')
'左对齐       '
>>> '{:>10}'.format('右对齐')
'       右对齐'
>>> '{:^10}'.format('居中')
'    居中    '
>>> '{:*^10}'.format('居中')  # 使用*填充
'****居中****'
```

#### 2.8 替换`%+f`， `%-f`和`% f`，并指定一个符号:

```python
>>> '{:+.2f}; {:+.3f}'.format(3.14, -3.14)  # 正号不改变数字的负号
'+3.14; -3.140'
>>> '{: f}; {: f}'.format(3.14, -3.14)  	# sign为空格时，正数的正号变为空格
' 3.140000; -3.140000'
>>> '{:-f}; {:-f}'.format(3.14, -3.14)		# sign为-时，正数前面什么也没有
'3.140000; -3.140000'
```

#### 2.9 进制转换

format还支持二进制数，貌似%不支持

```python
>>> "int: {0:d};  hex: {0:x};  oct: {0:o};  bin: {0:b}".format(42)
'int: 42;  hex: 2a;  oct: 52;  bin: 101010'
# 加#号后，显示进制的开头，大小写同上
>>> "int: {0:d};  hex: {0:#X};  oct: {0:#o};  bin: {0:#b}".format(42)
'int: 42;  hex: 0X2A;  oct: 0o52;  bin: 0b101010'
```

#### 2.10 使用逗号作为千位分隔符:

```python
>>> '{:,}'.format(1234567890)
'1,234,567,890'
>>> '{:_}'.format(1234567890)
'1_234_567_890'
```

#### 2.11 百分数

```python
>>> 'a= {:.2%}'.format(12.516/100)
'a= 12.52%'
```

#### 2.12 使用特定类型的格式:

```python
>>> import datetime
>>> d = datetime.datetime(2010, 7, 4, 12, 15, 58)
>>> '{:%Y-%m-%d %H:%M:%S}'.format(d)
'2010-07-04 12:15:58'

>>> '{:%y-%m-%d %h:%m:%S}'.format(d)
# 改为小写之后，y略去了20，而h，m出现了异常，S则报错
'10-07-04 Jul:07:06'
```

#### 2.13 嵌套参数和更复杂的例子:

```python
>>> for align, text in zip('<^>', ['left', 'center', 'right']):
>>>     print('{0:{fill}{align}16}'.format(text, fill=align, align=align))
'left<<<<<<<<<<<<'		# 这里执行了一个参数传递：text='left',fill='<',align='<'
'^^^^^center^^^^^'		# 这里等同：'{0:^^16}'.format('center')
'>>>>>>>>>>>right'		# ,text='right'，长度为1，下标为0，width=16
>>>
>>> octets = [192, 168, 0, 1]
>>> '{:02X}{:02X}{:02X}{:02X}'.format(*octets)	#192=C0,168=A8
'C0A80001'			# 将十进制的192转换为2位的16进制，然后进行字符串拼接
>>> int(_, 16)		# 是对字符串'C0A80001'按照16进制的规则转换为10进制的整数
3232235521
>>>
>>> width = 5
>>> for num in range(5,12): 
...     for base in 'dXob':		# 依然是参数传递
...         print('{0:{width}{base}}'.format(num, base=base, width=width), end=' ')
...     print()

    5     5     5   101		# print('{0:5d}'.format(5))
    6     6     6   110		# 其中：每列分别采用10,16,8,2进制对数字进行转换
    7     7     7   111		# 每行第一列均为10进制，得数字本身5:12
    8     8    10  1000		# 如本行10是按照8进制对8进行转换，逢8进1 8=1*8+0
    9     9    11  1001		# 本行11则为9=1*8+1
   10     A    12  1010
   11     B    13  1011
```



###### 两个小建议：

> 多看看官方文档，对语法的理解会更深一点，知道平时的用法是怎么来的，更进一步的，了解Python的调用逻辑，语法习惯，运行方式是什么样的；
>
> 知道并不代表就会用了，还是需要多用多思考，多总结，熟能生巧，游刃有余。

