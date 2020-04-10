# 2020.0330
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
  * print输出是默认换行的，要实现不换行要加逗号，要实现一个print里多行打印加三引号
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



