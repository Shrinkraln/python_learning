---
title: Python 学习笔记
description: Python 基础语法与练习记录
tags: ['python']
pubDate: 2026-06-29
---



# 1. 第一个python程序

```python
#win上
python3 hello.py
#linux上，可以转化为可执行程序
chmod a+x hello.py
./hello.py


#输出，逗号输出为空格，第一个输出为字符串，第二个是直接打印数值输出
print('100+200=',300)
#对于变量，终端输入变量名即可输出变量值
>>> classmates = ['Michael', 'Bob', 'Tracy']
>>> classmates
['Michael', 'Bob', 'Tracy']
#输入，输入的是字符串，但是py的数据类型是动态的
name=input('plz enter:')
```

# 2. py基础
1. 数据类型和变量
```python
#使用4个空格的缩进区分代码块
a=100
if a>=0:
    print(a)
else:
    print(-a)
end 


#直接处理的数据变量
#整数
a=-100
#浮点数，包括科学技术
a=1.2e-5
#字符串
'abc'	#'a' 'b' 'c'
"I'm OK"	#'I' "'" 'm' ' ' 'O' 'K'六个
'I\'m\"OK\"!' #使用转义符
r'\\\\t\'		#r表示字符串里面的字符不转义
'''test
for
py'''			#输出多行
#布尔值
true false	#逻辑与或非转化为and or not
#空值
None


#运算
/		#得到结果是浮点数，但是c只得到整数
//		#得到结果是整数部分
```
2. 字符串和编码
```python
#计算机底层unicode编码，显示utf-8编码
#获取字符串的整数表示，即unicode编码的十进制值
ord('A')    #65
#逆运算
chr(65)     #'A'
#如果知道字符的编码值
'\u4e2d\u6587'  #'中文'
#unicode中一个字符对应多个字节,b表示为一个字节长度的字符
#不是强制转化，而是内存存储默认是unicode，如果只需表示一个字节使用d
#将输入数据转化为byte，编码为指定bytes
#发展方向是ASCII -> unicode ->UTF-8
>>> 'ABC'.encode('ascii')
b'ABC'
>>> '中文'.encode('utf-8')
b'\xe4\xb8\xad\xe6\x96\x87'
>>> '中文'.encode('ascii')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
UnicodeEncodeError: 'ascii' codec can't encode characters in position 0-1: ordinal not in range(128)
#逆运算，解码
>>> b'ABC'.decode('ascii')
'ABC'
>>> b'\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8')
'中文'
#有无法解码的字节将报错
>>> b'\xe4\xb8\xad\xff'.decode('utf-8')
Traceback (most recent call last):
  ...
UnicodeDecodeError: 'utf-8' codec can't decode byte 0xff in position 3: invalid start byte
#可以忽略字节
>>> b'\xe4\xb8\xad\xff'.decode('utf-8', errors='ignore')
'中'
#获取字符数，对于byte是获取字节数，因为本身是一个字符一个字节对应
>>>len('ABC')  
3
>>> len(b'\xe4\xb8\xad\xe6\x96\x87')
6
>>> len('中文'.encode('utf-8'))
6
#格式化输入输出
#%s会全部强制转化为字符串格式
>>> 'Hello, %s' % 'world'
'Hello, world'
>>> 'Hi, %s, you have $%d.' % ('Michael', 1000000)
'Hi, Michael, you have $1000000.'
#f-string是可以用变量名作为占位符
>>> r = 2.5
>>> s = 3.14 * r ** 2
>>> print(f'The area of a circle with radius {r} is {s:.2f}')
The area of a circle with radius 2.5 is 19.62
```
```python
#指定UTF-8编码
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
```
3. list和tuple
```python
#列表list
>>> classmates = ['Michael', 'Bob', 'Tracy']
>>> classmates
['Michael', 'Bob', 'Tracy']
#列表元素个数
>>>len(classmates)
3
#下标同理数组
>>>classmates[0]
'Michael'
#但是python是面向对象的语言，更多有面向对象的方法
#尾插
>>> classmates.append('Adam')
>>> classmates
['Michael', 'Bob', 'Tracy', 'Adam']
#指定插入，其余后移
>>> classmates.insert(1, 'Jack')
>>> classmates
['Michael', 'Jack', 'Bob', 'Tracy', 'Adam']
#尾删
>>> classmates.pop()
'Adam'
>>> classmates
['Michael', 'Jack', 'Bob', 'Tracy']
#指定删除
>>> classmates.pop(1)
'Jack'
>>> classmates
['Michael', 'Bob', 'Tracy']
#直接修改替换
>>> classmates[1] = 'Sarah'
>>> classmates
['Michael', 'Sarah', 'Tracy']
#列表里的元素数据类型可以不同
>>> L = ['Apple', 123, True]
#嵌套list
>>> s = ['python', 'java', ['asp', 'php'], 'scheme']
>>> len(s)
4
#多维列表,s[2][0]或者p[0]
>>> p = ['asp', 'php']
>>> s = ['python', 'java', p, 'scheme']

#元组tuple，数据初始化不能修改
>>> t = (1, 2)
>>> t
(1, 2)
#一个元素
>>> t = (1,)
>>> t
(1,)
#空
>>> t = ()
>>> t
()
#tuple嵌套list,可以改变list的元素，但是不能改变tuple，如果tuple使用的是list变量名就是tuple变量名不能变
>>> t = ('a', 'b', ['A', 'B'])
>>> t[2][0] = 'X'
>>> t[2][1] = 'Y'
>>> t
('a', 'b', ['X', 'Y'])

```
