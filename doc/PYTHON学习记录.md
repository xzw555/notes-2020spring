# 2020.0330
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [2020.0330](#20200330)
  - [python特点](#python特点)
  - [面对对象的思维方式](#面对对象的思维方式)
  - [Pycharm安装](#pycharm安装)
- [2020.0331](#20200331)
- [2020.0402](#20200402)
- [2020.0403](#20200403)
- [2020.0404](#20200404)
    - [Linux常用命令](#linux常用命令)
- [2020.0406](#20200406)
    - [python学习记录](#python学习记录)
      - [python基本语法](#python基本语法)
      - [python变量类型](#python变量类型)
    - [运算符](#运算符)
    - [常用语句](#常用语句)
- [2020.0419](#20200419)
    - [日期和时间](#日期和时间)
    - [函数](#函数)
    - [python文件I/O](#python文件io)
    - [文件专题编程练习](#文件专题编程练习)
      - [os包](#os包)

<!-- /code_chunk_output -->
## python特点
* Python是完全面向对象的语言
  * 函数、模块、数字、字符串都是对象，在Python中一切皆对象
  * 完全支持继承、重载、多重继承
  * 支持重载运算符，也支持泛型设计
* Python拥有一个强大的标准库，Python语言的核心只包含数字、字符串、列表、字典、文件
等常见类型和函数，而由Python标准库提供了系统管理、网络通信、文本处理、数据库接口、图形系统、XML处理
等额外的功能
* Python社区提供了大量的第三方模块，使用方式与标准库类似，它们功能覆盖科学计算、人工智能、机器学习、web开发、数据库接口、图形系统多个领域

## 面对对象的思维方式
* 面向对象是一种思维方式
* 要解决一个问题，首先考虑由**谁**来做，怎么做事情是**谁**的职责
  * 对象就是 **谁**
* 要解决复杂的问题，就可以找多个不同的对象，各司其职，共同实现，最终完成需求
## Pycharm安装
* 下载python解释器3.8.1，虽然只有28M左右，但是下载的很慢，
点自动安装路径，不然要手动配置环境，然后打开cmd，输入python回车，查看是否安装成功，输入pip list查看版本，按指示升级了pip
* 安装pycharm后，点do not import settings, 社区版不需要激活
* 点create new project，改location为D盘，最后一个反斜杠后是创建的文件名firsttry，点new environment using, inherit global site-packages, make available to all projects,创建虚拟环境venv(方便以后删除，防止装坏系统) existing interpreter 是选择已有的环境。
* 点左边project下firsttry，其下级出现venv，里面可以看到python.exe等。点击firsttry,右键，new，python file，name自己定义(demo1)，输入
```bash
print('hello,world')
```
右键->run firsttry->底部出现运行结果
* 查看设置/改变字体等操作
  * file->settings->project firsttry->project interpreter可以看到项目的环境路径，可以看到pip和setuptools，想安装第三方的包可用右侧的加号或者cmd进行安装
  * file->settings->editor->font->size可以改字体
* 注意，如果把第三方包安装到本地环境下，虚拟环境中是无法使用第三方库的，运行项目的时候要看清选的是哪个环境

# 2020.0331

* 下载大的文件或者安装包用chrome不要用edge，edge无法改动默认下载路径，会下载到C盘用户的曾孙文件夹中，不好找
* python变量不需要声明就能使用，也不必指定数据类型，会根据变量值设定数据类型
* 多个变量可以一起指定变量值：
```bash
a = b = c = 20  #abc值为20，类型为int
```
* **#** 是python的注释符号，相当于c中的 **//**

# 2020.0402

* githubs上可创建public or private repository，repository中要建立branch，相当于master的复制(?),在其中可以编写README.md
* \t,\n等含义与c相同，\是转义字符
* ASCII码，Unicode和可变长编码UTF-8；计算机内存中统一用Unicode，保存到硬盘或者传输的时候，用UTF-8；用记事本编辑的时候，从文件读取的UTF-8字符被转换为Unicode字符到内存里，编辑完成后，保存时再把Unicode转换为UTF-8保存到文件；浏览网页时，服务器会把动态生成的Unicode内容转换为UTF-8再传输到浏览器；
Python 3版本中，字符串是以Unicode编码的，Python3的字符串支持多语言，但2不支持
对单个字符，ord()函数获取字符的整数表示，chr()把编码转换为对应的字符：
```bash
print(ord('中'))
print(chr(25991))
结果：
20013
文
```
* Unicode表示的str通过encode()可编码为指定的bytes
只有纯英文的str可以用ASCII编码为bytes；反过来，从网络或磁盘上读取了字节流，那么读到的数据就是bytes。要把bytes变为str，就需要用decode()方法
```bash
print('ABC'.encode('ascii'))
print(b'ABC'.decode('ascii'))
```
* len()函数计算的是str的字符数，如果换成bytes，len()函数就计算字节数：
```bash
print(len(b'ABC'))
3
print(len(b'\xe4\xb8\xad\xe6\x96\x87'))
6
print(len('中文'.encode('utf-8')))
6
```
* 若源代码中包含中文，保存源代码时，就需要指定保存为UTF-8编码。当Python解释器读取源代码时，为了让它按UTF-8编码读取，通常在文件开头写上这两行：
```bash
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
```
第一行注释是为了告诉Linux/OS X系统(windows?)，这是一个Python可执行程序，Windows系统会忽略这个注释；
第二行注释是为了告诉Python解释器，按照UTF-8编码读取源代码，否则，你在源代码中写的中文输出可能会有乱码。
* 与c中printf功能比较，用%输出格式化的字符串
```bash
print('Hello, %s' % 'world')
结果'Hello, world'
print('Hi, %s, you have $%d.' % ('Michael', 1000000))
结果：'Hi, Michael, you have $1000000.'
```
* 若没有特殊业务要求，牢记仅使用UTF-8编码。

# 2020.0403
* ctrl alt t打开Linux终端/terminal
* .appimage文件是新型的打包软件，它可以解决Linux上面的依赖问题，右键-属性-permission-execute点allow，然后双击该文件即可运行
* 在terminal输入firefox即可打开火狐
* 下载并安装chrome后，在终端/terminal输入google-chrome即可运行
* terminal中输入 cd +文件夹/文件名即可打开对应文件，cd..即返回上级文件夹eg.
```
xu@xu-VLT-WX0:~$ cd Downloads
xu@xu-VLT-WX0:~/Downloads$ cd ..
xu@xu-VLT-WX0:~$ 
```
但要注意文件名大小写，否则无法打开
* terminal中输入ls查看home中所有文件夹, ls是**l**i**s**t的缩写
  输入touch 1.txt在home中创建名为1.txt的文件
  输入info 1.txt，更详细的说明文档
  输入mkdir xxx，创建名为xxx的directory 
  输入rm -rf xxx 强制删除xxx
  输入rm -rf 1.txt 强制删除1.txt
* 命令格式
命令 -选项 参数 eg. ls -la /etc
  * 有多个选项时，可以写在一起
  * 两个特殊的目录 **.**和 **..**分别代表当前目录和当前目录的父目录
* 命令权限
  * 只有root可以执行的命令，放在/sbin or /usr/sbin目录下
  * 所有用户都可执行的命令放在/bin or /usr/bin下
  * 在Linux中所有东西都是一个文件，命令也是一种二进制文件 bin-binary(二进制)
# 2020.0404
### Linux常用命令
* 文件处理命令ls
  * 所在路径 /bin/ls
  * 功能：显示目录文件
  * 语法：ls 选项[-ald] [文件或目录]
    * -a(all的缩写) 显示所有文件，包括隐藏文件eg. ls -a /test
    * -l(long) 详细信息显示，如文件类型eg. 输入ls -l /  显示：
      **drwxr-xr-x 2 root root 4096 12-01 20:52 bin**
      **前十**个字符分成d   rwx   r-x   r-x   来看
      **d**即该文件的类型
      * 常见文件类型
        **d** 目录directory
        **-**  二进制文件
        **l** 软链接文件link

      三种权限：r-read读、w-write写、x-execute执行
      rwx表示三种权限都有，r-x表示缺w权限

      | rwx | r-x | r-x |
      | --- | --- | ---|
      |所有者o|所属组g|其他人o|
      |user/owner |group|others|
      所以d后面的九个字符依次给出所有者，所属组和其他人的权限
      |**2**|root|root|4096|12-01 20:52|bin|
      |---|---|---|---|---|---|
      |硬链接数|所有者|所属组|文件大小(不准确)|创建/最后修改时间|目录/文件名称|
      数据块 block 默认512字节 (block是存储单位，linux中很多不以k为单位)
    * -d(directory) 查看目录属性/权限eg. 输入ls -d /
    ls -l只能看到根目录下子目录的详细信息，不能看到根目录自己的信息
    * **选项可以多个合并在一起使用**，如可以输入 ls -ld / 或者ls -ld /test之类的
* 文件处理命令 cd (**c**hange **d**irectory)
  * 所在路径 shell内置命令
  * 功能：切换目录
  * 语法：cd[目录]
  cd / 切换到根目录
  cd ..切换到上一级目录
* 文件处理命令 pwd(**p**rint **w**orking **d**irectory)
  * 所在路径 /bin/pwd(之后bin中的命令省略此条)
  * 功能：查看当前工作目录
  * 语法：pwd
  经常pwd和cd配合使用
* 文件处理命令 touch
  * 功能：创建空文件
  * 语法：touch [文件名]
* 文件处理命令 mkdir(**m**a**k**e **dir**ectories)
  * 功能：在当前目录下创建新目录
  * 语法：mkdir [目录名]
  mkdir -p [多层目录]
  ```bash
  mkdir -p xzw/a/b/c #同时创建abc三个目录，不加-p会报错
* 文件处理命令 cp(**c**o**p**y)
  * 功能：复制文件或目录
  * 语法：cp -R [源文件或目录][目的目录]  只有复制目录需要加-R，复制文件不用
  ```bash
  cp /dir1/file1 /dir2/file2 /xzw #将dir1的file1，dir2的file2放入xzw中
  ls /xzw   #查看xzw中的文件
  xzw文件夹中会出现file1,file2
  cp -R /dir1 /xzw #将目录dir1复制到xzw下
  ```
* Ctrl+C 终止命令
* 文件处理命令 mv(move)
  * 功能 移动文件，更名
  * 语法：mv [源文件目录][目的目录]
  ```bash
  mv file1 file3 #将file1改名为file3
  mv file2 dir4 #将file2移动到目录4
  mv /test/testfile /xzw/file.test #将test中的文件testfile移动到xzw并改名为file.test
  ```
* 文件处理命令 rm(remove)
  * 功能：删除文件
  * 语法：rm -r [文件或目录]
  * rm -f [文件] 直接删除文件，省去询问是否确定删除 (f是force的意思)
  rm -rf [目录] 直接删除目录，若没有-rf，目录里每个文件会一个个询问是否删除
* 文件处理命令 cat(con**cat**enate and display files)
  * 功能：显示文件内容
  * 语法：cat [文件名]
  ```bash
  cat /xzw/file1
  ```
# 2020.0406
### python学习记录
#### python基本语法
* print语法
  * print输出是默认换行的，要实现不换行要加，end=''，比如
  print('a', end='')
  print('b')
  输出就是ab
  要实现一个print里多行打印加三引号
```bash
num = 3; i = 1; j = 3
print ('%d 等于 %d * %d' % (num,i,j)) #输出 3 等于 1 * 3
print(r'''hello
...你好吗
...我很好''')
print('hello \
world')
print('this is',
      'the third')
print('this is','the fourth')
print('this is','the fiveth \
sentence,','great!')
print(type('s'))
print(1/3)
cqwert=10 #定义变量cqwert
print(cqwert)
print(type(cqwert))
print(cqwert) #输入c会显示含有c的变量，再输入q就只剩这个变量了，按tab可自动补全变量名
x=7
if x<100.9:
    print("x<100.9")
if x<7:
    print("x<7")
    print('x>7') #此时这两行都不打印
if x<7:
    print("x<7")
print('x>7') #此行被打印，所以一定注意缩进
```
* python标识符
  * 标识符由字母、数字、下划线组成
  * 标识符可以包括英文、数字以及下划线(_)，但**不能以数字开头**
  * 以下划线开头的标识符是有特殊意义的。以单下划线开头 _foo 的代表不能直接访问的类属性，需通过类提供的接口进行访问，不能用 from xxx import * 而导入。
  以双下划线开头的 __foo 代表类的私有成员，以双下划线开头和结尾的 __foo__ 代表 Python 里特殊方法专用的标识，如 __init__() 代表类的构造函数。
* python保留字符
  * 除了C语言中常见的那些，还有assert、import、lambda、global、yield，from
* 行和缩进
  * IndentationError: unindent does not match any outer indentation level错误表明，使用的缩进方式不一致
* 多行语句
  * 一般以新行语句作为语句的结束符
  * 可以使用斜杠（ \）将一行的语句分为多行显示，语句中包含 [], {} 或 () 括号就不需要使用多行连接符
  ```bash
  total = item_one + \                        days = ['Monday', 'Tuesday', 'Wednesday',
        item_two + \                                  'Thursday', 'Friday']
        item_three
  ```
* python引号
  * 可以使用引号( ' )、双引号( " )、三引号( ''' 或 """ ) 来表示字符串，引号的开始与结束必须的相同类型的。 
其中三引号可以由多行组成，编写多行文本的快捷语法，常用于文档字符串
* python空行
  * 非强制性，约定俗成的
  * 函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。
* 同行显示多条语句
  * 语句间加; 但是行尾不用加
* 多个语句构成代码组
  * 缩进相同的一组语句构成一个代码块，称之代码组。
像if、while、def和class这样的复合语句，首行以关键字开始，以冒号:结束，该行之后的一行或多行代码构成代码组
我们将首行及后面的代码组称为一个子句(clause)
#### python变量类型
* 变量赋值
  * Python 中的变量赋值不需要类型声明，其他同C
* 多个变量赋值
  * Python允许你同时为多个变量赋值。例如：
  ```bash
    a = b = c = 1 
    a, b, c = 1, 2, "john" #两个整型对象 1 和 2 分别分配给变量 a 和 b，字符串对象 "john" 分配给变量 c
  ```
* 标准数据类型
  * Python有五个标准的数据类型：
    Numbers（数字）
    String（字符串）
    List（列表）
    Tuple（元组）
    Dictionary（字典）

* Numbers（数字）
  * 四种数字类型
    int（有符号整型） 
    float（浮点型） 
    complex（复数）
    |int|float|complex|
    |---|---|---|
    |1|32.3e+18|1+2.2j|
  * python2中存在long类型，但是python3中归到int了
  * Python支持复数,可以用 a + bj,或者 complex(a,b) 表示, a 和 b 都是浮点型
  * 可以使用del语句删除一些对象的引用
  ```bash
  var1 = 1
  var2 = 10 
  del var1, var2  #删除var1，var2对number对象的引用，此后再引用var1会报错，直到另一个值被赋给它
  # del语句操作某个对象的时候, 并不是直接将该对象在内存中删除, 而是将该对象的引用计数-1
  x = y = 1
  print(x,y)
  del x
  print(y) #y可以被正常打印，因为只取消了x对数据对象 1 的引用

* String（字符串）
  * 由数字、字母、下划线组成的一串字符
  * 字串列表有2种取值顺序:
    * 从左到右索引默认0开始的，最大范围是字符串长度少1
    * 从右到左索引默认-1开始的，最大范围是字符串开头,以'SAO'为例
      |S|A|O|
      |---|---|---|
      |0|1|2|
      |-3|-2|-1|
  * 如果要实现从字符串中获取一段子字符串的话，可以使用 [头下标:尾下标] 来截取相应的字符串，其中下标是从 0 开始算起，可以是正数或负数(从右往左索引)，下标可以为空表示取到头或尾。
  [头下标:尾下标] 获取的子字符串包含头下标的字符，但不包含尾下标的字符(相当于左开右闭的区间)
  若省略尾下标默认输出之后的全部字符
  * 加号（+）是字符串连接运算符，星号（*）是重复操作
  ```bash
  s = 'abcdef'
  d = s[1:6]
  print (d) #打印bcdef，如果d=s[1:5],f不会被打印
  a = s[1:-2] #表示打印1到-2间的字符，且不包括-2位置的字符
  print (a) #打印bcd
  print (s + "TEST") # 输出 abcdefTEST
  print (s[1:3]*2 + 'TEST') #输出 bcbcTEST
  ```
  * Python列表截取可以接收第三个参数，参数作用是截取的步长，
    以下实例在索引 1 到索引 4 的位置并设置为步长为 2（间隔一个位置）来截取字符串
  ```bash
  l = ['a','b','c','d','e']
  print (l[1:4:2]) #输出结果 ['a', 'c']
  ```
* List（列表）
  * 列表可以完成大多数集合类的数据结构实现。它支持字符，数字，字符串甚至可以包含列表(即嵌套)
  * 列表用 [ ] 标识，是 python 最通用的复合数据类型
  * 列表中值的切割也可以用到变量 [头下标:尾下标] ，就可以截取相应的列表，从左到右索引默认 0 开始，从右到左索引默认 -1 开始，下标可以为空表示取到头或尾
  ```bash
  list = [ 'runoob', 786 , 2.23, 'john', 70.2 ] #什么都能放进去
  tinylist = [123, 'john']
  print(list)
  print(list[0])
  print(list[1:4] + tinylist)
  print(tinylist*2)
  运行结果:
  ['runoob', 786, 2.23, 'john', 70.2]
  runoob
  [786, 2.23, 'john', 123, 'john']
  [123, 'john', 123, 'john']
  ```
* Tuple（元组）
  * 元组是另一个数据类型，类似于 List（列表）。
  * 元组用 () 标识。内部元素用逗号隔开。但是元组不能二次赋值，相当于只读列表
  用法和list差不多
  * 只有1个元素的tuple定义时必须加一个逗号 **,**来消除歧义
  ```bash
  tuple = ( 'runoob', 786 , 2.23, 'john', 70.2 )
  list = [ 'runoob', 786 , 2.23, 'john', 70.2 ]
  tuple[2] = 1000 #非法
  list[0] = 1000 #合法，注意python中变量无类型，可以随便引用不同数据类型的对象
  ```
  下面看一个可以改变的tuple
  ```bash
  t = ('a', 'b', ['A', 'B'])
  t[2][0] = 'X'
  t[2][1] = 'Y'
  print (t)   #运行结果：
  ('a', 'b', ['X', 'Y'])
  ```
![](2020-04-06-15-37-50.png)   ![](2020-04-06-15-38-48.png)
* Dictionary（字典）
  * 字典(dictionary)是除列表以外最灵活的内置数据结构类型。列表是有序的对象集合，字典是无序的对象集合。
    两者之间的区别在于:字典当中的元素是通过键来存取的，而不是通过偏移存取(list和tuple,string都通过偏移)
  * 字典用"{ }"标识。字典由键(key)和它对应的值value组成
* 数据类型转换
  * 类似于c中的强制类型转换，如
  * int(x,[base]),long(x,[base]),float(x),str(x)等

### 运算符
* 运算符种类：算术运算符，比较运算符，赋值运算符，逻辑运算符，位运算符，成员运算符
  身份运算符
* 算术运算符
  * 与c中不同：两个整数相除赋值给a，a为浮点型，eg. a = 1/2 ,则a=0.5；a = 2/1, ,则a=2.0
* 比较运算符
  * eg. >,<,==,!=,>=,<= 同c
  * python2中<>也表示不等于，3中已废弃
* 赋值运算符
  * =,+=,-=,*=,/=,%= 用法同c
  * //= 取整除运算符 c//=a 即 c = c//a    **= 幂赋值运算符
* 位运算符：略
* 逻辑运算符
  |运算符|逻辑表达式|描述|
  |---|---|---|
  |and|x and y|布尔"与"，如果 x 为 False，x and y 返回 False，否则它返回 y 的计算值|
  |or|x or y|布尔"或"，如果 x 是非 0，它返回 x 的值，否则它返回 y 的计算值|
  |not|not x|布尔"非"， 如果 x 为 True，返回 False 。如果 x 为 False，它返回 True|
```bash
a = 10; b = 20
if a and b:
  print(1)
else :
  print(0)
```
* 成员运算符
|运算符|描述|
  |---|---|
|in|若在指定的list/tuple/string中找到值返回True,否则返回False|
|not in|若在指定的list/tuple/string中未找到值返回True,否则返回False|
```bash
t = "123"
a = "1"
if a in t:
    print(1)
else:
    print(0) 结果输出 1
```
* 身份运算符
![](2020-04-06-16-49-14.png)
  * is 与 == 区别：
  is 用于判断两个变量引用对象是否为同一个(同一块内存空间)， == 用于判断引用变量的值是否相等。
  ```bash
  x = [2]
  y = [2]
  print(id(x))
  print(id(y))
  if x is y:
    print(1)
  if x == y:
    print(2)
  OUTPUT:
  1506962239936
  1506993269696
  2
  ```
### 常用语句
* 语句类型
  * 条件语句
  * 循环语句
    * while循环
    * for循环
    * 循环嵌套
  * 循环控制语句
    * break语句
    * continue语句
    * pass语句
* 条件语句
  * Python指定任何非0和非空（null）值为true，0 或者 null为false
  * 格式
  ```bash
  if 判断条件：
    执行语句……
  else ：
    执行语句……
  ```
* while循环
  * 格式
  ```bash
  while 判断条件(condition)：
    执行语句(statements)……
  ```
  * while ... else 有点像switch里的default
  ```bash
  count = 0
  while count < 5:
      print count, " is  less than 5"
      count = count + 1
  else:
      print count, " is not less than 5"
  ```
* for循环
  * 语法
  ```bash
  for iterating_var in sequence:
      statements(s)
  ```
  ```bash
  for letter in 'Python':     # 第一个实例
      print ('当前字母 :', letter)
  fruits = ['banana', 'apple']
  for fruit in fruits:        # 第二个实例
      print ('当前水果 :', fruit)
  for index in range(len(fruits)): #函数len()返回列表长度,range见下图
      print ('当前水果 :', fruits[index])
  输出结果：
  当前字母 : P
  ...略
  当前字母 : n
  当前水果 : banana
  当前水果 : apple
  当前水果 : banana
  当前水果 : apple
  ```
![](2020-04-06-18-00-51.png)
  * for else循环
  与while else类似
* 循环嵌套：格式如下
```bash
for iterating_var in sequence:
   for iterating_var in sequence:
      statements(s)
   statements(s)
```
* break语句
  * break语句用在while和for循环中，除了不用加;其他同c
* continue语句
  * continue 跳出本次循环，而break跳出整个循环
  continue 用来告诉Python跳过当前循环的剩余语句，然后继续进行下一轮循环,continue语句用在while和for循环中
  比如循环打印奇数，可以用continue跳过偶数
* pass语句
  * pass 一般用于占位置。因为不能写空循环或者空程序
    在 Python 中有时候会看到一个 def 函数:
    ```bash
    def sample(n_samples):
    pass
    ```
    该处的 pass 便是占据一个位置，因为如果定义一个空函数程序会报错，
    当你没有想好函数的内容是可以用 pass 填充，使程序可以正常运行。

# 2020.0419
### 日期和时间
* time 模块下有很多函数可以转换常见日期格式，如函数time.time()用于获取当前时间戳
```python
import time #引入time模块
ticks = time.time() #获取当前时间戳
print(ticks)#每个时间戳都以自从1970年1月1日午夜经过了多少秒来表示
import datetime
i = datetime.datetime.now()
print ("当前的日期和时间是 %s" % i)
print ("ISO格式的日期和时间是 %s" % i.isoformat() )
print ("当前的年份是 %s" %i.year)
print ("当前的月份是 %s" %i.month)
print ("当前的日期是  %s" %i.day)
print ("dd/mm/yyyy 格式是  %s/%s/%s" % (i.day, i.month, i.year) )
print ("当前小时是 %s" %i.hour)
print ("当前分钟是 %s" %i.minute)
print ("当前秒是  %s" %i.second)
结果：
1587317343.8574755
当前的日期和时间是 2020-04-20 01:29:03.857475
ISO格式的日期和时间是 2020-04-20T01:29:03.857475
当前的年份是 2020
当前的月份是 4
当前的日期是  20
dd/mm/yyyy 格式是  20/4/2020
当前小时是 1
当前分钟是 29
当前秒是  3
```
### 函数
* 定义一个函数
  * 函数代码块以 def 关键词开头，后接函数标识符名称和圆括号()。
  * 传入的参数和自变量放圆括号中间，圆括号间可以用于定义参数。
  * 函数的第一行语句可以选择性地使用文档字符串—用于存放函数说明。
  * 函数内容以冒号起始，并且缩进
  * return [表达式] 结束函数，选择性地返回一个值给调用方，不带表达式的return相当于返回 None
格式：
```bash
def functionname( parameters ):
   "函数_文档字符串"
   function_suite
   return [expression]
例：
def printme(str):
    "打印传入的字符串" 
    print(str)
    return
printme("调用用户自定义函数")
结果：
调用用户自定义函数
(""字符串作用和函数注释差不多，感觉和#加注释没区别)
```
* 可更改(mutable)对象与不可更改(immutable)对象
	* 不可变类型 strings,tuples和numbers
	在fun(a)内部修改a的值，不会影响a本身
	* 可变类型 list, dict
	修改后外部的a也会受影响
python中一切都是对象，严格意义上不能说是值传递还是引用传递，应该说是传不可变对象还是可变对象

```bash
def changeme(mylist):
	“修改传入的列表”
	mylist.append([1,2,3,4]) #append会在数组后加上相应元素
	print(“函数内取值：”,mylist)
	return

mylist=[10,20,30]
changeme(mylist)
print(“函数外取值”,mylist)
```
* 参数
	* 必备参数
	* 关键字参数
	```bash
	def printme(str,age):
		print(str,age)
		return
	printme(age=50,str=‘namika’)
	```
	* 默认参数
	* 不定长参数
	```bash
	def functionname([formal_args], *var_args_tuple):
		function_suite
		return [expression]
	#加*号的变量名存放所有未命名的变量参数
	```
	* 匿名函数
	lambda [arg1 [,arg2,...argn]]: expression #只能写一行
	```bash
	sum=lambda arg1,arg2: arg1+arg2
	#调用sum函数
	print(“相加后的值：”,sum(10,20))
  ```
	* 变量作用域
		* 全局变量：定义在函数外的变量
		* 局部变量
	###  python模块
	* 模块(module)是一个python文件，以.py结尾
	模块能使你有逻辑地组织python代码段
	* 模块的引入 import
	```bash
	import os #导入标准库os
	import module_name #python会从两个地方找这个模块，一个是sys.path,一般安装的python库的目录都可以在sys.path中找到(前提是已经将库的安装目录添加到环境变量中)，另一个是运行文件所在的目录
	# 建立两个文件demo1.py ,demo2.py
	demo1.py：
	import os 
	import demo2
	demo2.printself()
	
	demo2.py:
	print(1)
	def printself():
		print(‘in demo2’)
	输出结果：
	1
	demo2
	```
  * import用法二
  ```bash
  from package_name import module_name #把模块族构成的集合成称为包(package)
  在demo1.py所在的文件夹(file)fisttry下新建名叫branch1的package
  再在branch1下新建文件demo3.py
  如何在m1中导入m3.py?看更改后的demo1.py：
  ```bash
  from branch import demo3
  demo3.printSelf()
  ```
  * 相对导入和绝对导入
  from . import module_name。导入和自己同目录下的模块。
  from .package_name import module_name。导入和自己同目录的包的模块。
  from .. import module_name。导入上级目录的模块。
  from ..package_name import module_name。导入位于上级目录下的包的模块。
  还可以有更多的**.** ，每多一个点就多往上一层目录
  * import其他用法
  import moudle_name as alias：有些module_name比较长，可以用as改名，如import numpy as np。
  from module_name import function_name, variable_name, class_name。上面导入的都是整个模块，有时候只想使用模块中的某些函数、某些变量、某些类，就可以用这种写法。使用逗号可以导入模块中的多个元素
  * dir()函数
    * 当给dir()提供一个模块名字时，它返回在那个模块中定义的名字的列表。当没有为其提供参数时, 它返回当前模块中定义的名字的列表
    ```bash
    import math
    content = dir(math)
    print content
    ```
  * python的PATH变量
  * 全局变量在函数内调用时需要global一下
  ```bash
  Money = 2000
  def AddMoney():
    global Money
    Money = Money + 1
  ```
  * globals(),locals(),reload()函数
    * globals()和locals()返回全局和局部命名空间里的名字。
    在函数内部调用 locals()，返回的是所有能在该函数里访问的命名。
    在函数内部调用 globals()，返回的是所有在该函数里能访问的全局名字。
    返回类型都是字典
    * 当一个模块被导入到一个脚本，模块顶层部分的代码只会被执行一次。
    因此，如果想重新执行模块里顶层部分的代码，用reload()，该函数会重新导入之前导入过的模块
  * python中的包(package)
    * 包是一个分层次的文件目录结构，它定义了一个由模块及子包，和子包下的子包等组成的Python的应用环境。
    简单来说，包就是文件夹(file)，但该文件夹下必须存在 __ init__.py 文件, 该文件的内容可以为空。__ init__.py 用于标识当前文件夹是一个包。
### python文件I/O
* 基本的I/O函数：(INPUT,OUTPUT)
  * print
  * ~~raw_input :从标准输入读取一个行并返回一个字符串(去掉结尾的换行符)~~ python3中与input合并
  * input :与raw_input类似,可以接收一个Python表达式作为输入，并将运算结果返回
  * open :类似c中的fopen
  * close() 
  * write() :fwrite
  * read()  :fread
  * tell() 文件定位
  * rename() 
  * remove() 删除文件
  * os中的
    * mkdir() 创建新目录
    * chdir() 改变目录
    * getcwd() 显示当前工作目录
    * rmdir() 删除目录
#### os包
* 用remove()删除指定文件
```python
import os
file = "newfile1.txt"
if os.path.exists(file):
    os.remove(file)
else:
    print(file + "文件未找到")
```
删除失败,为什么?(newfile1.txt和exercise存放在同一文件夹C:\Users\24284\PycharmProjects下)
原因:应该将newfile1.txt放在exercise文件夹里
* 用mkdir()创建指定目录
```python
from os import mkdir
mkdir ("mydir")
```
在exercise下创建了名叫mydir的目录
但是用上面的方法无法删除mydir目录,为什么?
* 用rmdir()删除目录(前提是目录为空)
```python
import os
dir = "mydir"
if os.path.exists(dir):
    os.rmdir(dir)
else:
    print(dir + "目录不存在")
```
成功删除mydir目录
* system方法
```python
import os
cur_path=os.path.dirname(__file__) #获得当前文件的绝对路径
os.system('cls') #清屏,但是清屏失败,出来了一个乱码
os.system("mkdir dir2") #创建dir2目录,这个和直接os.mkdir("dir2")有什么区别?
os.system("copy ossystem.py dir2\copyfile.py") #文件复制
file=cur_path + "\dir2\copyfile.py"
os.system("notepad" + file)  #用记事本打开copyfile.py文件.失败,出来的也是乱码
```
#### shutil包
* 将shutil.py文件复制为newfile.py
```python
import os,shutil
cur_path=os.path.dirname(__file__)
destfile = cur_path + "\\" + "newfile.py"
shutil.copy('shutil.py', destfile)
运行出错
Traceback (most recent call last):
  File "C:/Users/24284/PycharmProjects/exercise/fileopen.py", line 4, in <module>
    shutil.copy('shutil.py', destfile)
  File "D:\python3.8\lib\shutil.py", line 409, in copy
    copyfile(src, dst, follow_symlinks=follow_symlinks)
  File "D:\python3.8\lib\shutil.py", line 259, in copyfile
    with open(src, 'rb') as fsrc, open(dst, 'wb') as fdst:
FileNotFoundError: [Errno 2] No such file or directory: 'shutil.py'
```
#### glob包
```python
import glob
files = glob.glob("glob.py") + glob.glob("os*.py") + glob.glob("*.txt")
for file in files
    print(file)
出错
File "C:/Users/24284/PycharmProjects/exercise/fileopen.py", line 3
    for file in files
                    ^
SyntaxError: invalid syntax
```
### 文件专题编程练习
* 打开并修改文件
```python
#将content写入file1.txt文件
content='''Hello python
中文
Welcome
'''
f=open('file1.txt','w')
f.write(content)
f.close()
#打印file.txt文件
f=open('file1.txt','r')
for line in f:
    print(line,end="")
f.close()
```
* open详细介绍
```python
# open(filename[,mode][,encode])
# filename 文件名; mode打开模式; encode 指定文件编码模式
#windows中文默认是cp936,即ANSI编码
#可以用下列编码获得当前操作系统的默认编码
import locale
print(locale.getpreferredencoding())
f = open('file1.txt','r',encoding='cp936')
for line in f:
    print(line,end='')
#end=''让print函数不会在字符串末尾添加一个换行符，而是添加一个空字符串
f.close()
结果:
cp936
Hello python
中文
Welcome
奇怪的是建了个UTF-8编码的file2.txt后,用encoding='cp936'依旧可以打开,没报错
```
* read详细介绍
```python
f = open('file2.txt','r',encoding = 'cp936')
str1 = f.read(2)
print(str1)
f.close()
结果:
11 #file2中存储了11,编码是UTF-8
但是encoding='UTF-8'打开file1却失败了
file1是ANSI编码
```
上网查如何用python看文件的编码模式,发现要下载chardet包,第一次install失败
关掉pycharm,用管理员模式运行之后再安装就成功了
但是chardet查出的文件格式是KOI8-R,语言是Russian...
```python
import chardet
data = open('file1.txt','rb').read()
print(chardet.detect(data))
{'encoding': 'KOI8-R', 'confidence': 0.682639754276994, 'language': 'Russian'}
```
* 用txt文件存储账号和密码
```python
import ast #ast包中的literal_eval可进行类型转换
data = dict()
f = open('password.txt','r',encoding='KOI8-R')
filedata = f.read()
data = ast.literal_eval(filedata) #with语句结束后会自动关闭文件
f.close()
print(data)
结果:
{'chiou': '1234', 'David': '0800'}
但是用with语句就会报错
with open('file1.txt','r') as f
    for line in f
        print(line,end='')
报错信息:File "C:/Users/24284/PycharmProjects/exercise/fileopen.py", line 1
    with open('file1.txt','r') as f
                                  ^
SyntaxError: invalid syntax
```
* 账号/密码管理
```python
def menu():
    os.system("cls")
    print("账号/密码管理系统")
    print("-------------------")
    print("1.输入账号/密码")
    print("2.显示账号/密码")
    print("3.修改密码")
    print("4.删除账号/密码")
    print("0.结束程序")
    print("------------------")

def ReadData():
    f=open("password.txt",'r',encoding='UTF-8-sig')
    filedata=f.read()
    if filedata != "":
        data = ast.literal_eval(filedata)
        return data
    else: return dict() #返回一个空字典
    f.close()

def disp_data():
    print("账号\t密码")
    print("================")
    for key in data:
        print("{}\t{}".format(key,data[key]))
    input("按任意键返回主菜单")

def input_data():
    while True:
        name=input("请输入账号(Enter=>停止输入)")
        if name=="": break;
        if name in data:
            print("{}账号已存在!".format(name))
            continue
        password=input("请输入密码")
        data[name]=password
        f = open('password.txt','w',encoding='UTF-8-sig')
        f.write(str(data))
        print("{}保存完毕".format(name))

def edit_data():
    while True:
        name=input("请输入要修改的账号(enter=>停止输入)")
        if name=="":break
        if not name in data:
            print("{}账号不存在".format(name))
            continue
        print("原密码为:{}".format(data[name]))
        password=input("请输入新密码")
        data[name]=password
        f=open('password.txt','w',encoding='UTF-8-sig')
        f.write(str(data))
        input("密码更改完毕,请按任意键返回主菜单")
        break

def delete_data():
    while True:
        name=input("请输入要删除的账号(enter=>停止输入)")
        if name=="": break
        if not name in data:
            print("{}账号不存在!".format(name))
            continue
        print("确定删除{}的数据!:".format(name))
        yn=input("(Y/N)?")
        if(yn=='Y' or yn=='y'):
            del data[name]
            f=open("password.txt",'w',encoding='UTF-8-sig')
            f.write(str(data))
            input("已删除完毕,按任意键返回主菜单")
            break
###主程序###
import os,ast
data=dict()

data=ReadData() #读取文本后转换为dict
while True:
    menu()
    choice = int(input("请输入您的选择:"))
    print()
    if choice == 1:
        input_data()
    elif choice==2:
        disp_data()
    elif choice==3:
        edit_data()
    elif choice==4:
        delete_data()
    else:
        break

print("程序执行完毕")
```

### 类和对象
面对对象技术简介:
* 面对对象三大特点:
  * 数据封装
  * 继承
  * 多态
* 类(class):描述具有相同的属性和方法的对象的集合,定义了该集合中每个对象所共有的属性和方法,对象是类的实例.
class Student(object):
  pass
class后紧跟的是类名,通常是大写开头的单词,object表示该类是从哪个类继承下来的
若没有合适的继承类,就使用object类,这是所有类都会继承的类
定义好之后就可以根据Student类创建出Student的实例,创建实例是通过
类名+()实现的
bart = Student()
bart指向的就是Student的实例,可以给实例绑定属性,比如给bart绑定name属性
bart.name = 'Bart Simpson'
