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
#对于数字
s=input('birthdaty:')
birthday=int(s)
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
#str是不可变对象，对其进行操作会返回一个新的值，但是不改变原来的变量值
>>> a = 'abc'
>>> b = a.replace('a', 'A')
>>> b
'Abc'
>>> a
'abc'
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
#可以使用-1表示倒数第一个元素，同理-n
>>>classmates[0]
'Michael'
#但是python是面向对象的语言，更多有面向对象的方法
#只有list是可变对象，基于list的dict和set也是可变对象
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
4. 条件判断
```python
#完整形式
if <条件判断1>:
    <执行1>
elif <条件判断2>:
    <执行2>
elif <条件判断3>:
    <执行3>
else:
    <执行4>
#if判断条件简写
#只需x非零数值，非空字符串，非空list，非空tuple即为true
if x:
    print('True')
```
5. 模式匹配
```python
#复杂匹配
age = 15
match age:
    case x if x < 10:
        print(f'< 10 years old: {x}')
    case 10:
        print('10 years old.')
    case 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18:
        print('11~18 years old.')
    case 19:
        print('19 years old.')
    case _: #匹配到其他情况
        print('not sure.')
#匹配列表
args = ['gcc', 'hello.c', 'world.c']
# args = ['clean']
# args = ['gcc']
match args:
    # 如果仅出现gcc，报错:
    case ['gcc']:
        print('gcc: missing source file(s).')
    # 出现gcc，且至少指定了一个文件:
    case ['gcc', file1, *files]:
        print('gcc compile: ' + file1 + ', ' + ', '.join(files))
    # 仅出现clean:
    case ['clean']:
        print('clean')
    case _:
        print('invalid command.')
```
6. 循环
```python 
#for in循环
#顺序遍历list中的所有元素
names = ['Michael', 'Bob', 'Tracy']
for name in names:
    print(name)
#range()生成整数序列
>>> list(range(5))
[0, 1, 2, 3, 4]
#range也可以不转化为list就直接使用
sum = 0
for x in range(101):
    sum = sum + x
print(sum)

#while循环
sum = 0
n = 99
while n > 0:
    sum = sum + n
    n = n - 2
print(sum)

#break退出循环
n = 1
while n <= 100:
    if n > 10: # 当n = 11时，条件满足，执行break语句
        break # break语句会结束当前循环
    print(n)
    n = n + 1
print('END')

#continue退出当前循环进行下一次循环
n = 0
while n < 10:
    n = n + 1
    if n % 2 == 0: # 如果n是偶数，执行continue语句
        continue # continue语句会直接继续下一轮循环，后续的print()语句不会执行
    print(n)
```
7. dict和set
```python
#初始化定义键值对
#value不局限于数值，但是key不能是元素可变的list
>>> d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}
#对于dict的list格式变量值是其value而不是作为key的list格式元素
>>> d['Michael']
95
#get()如果key不存在，返回none（不显示）
>>> d.get('Thomas')
>>> d.get('Thomas', -1)
-1
#增加key
#增删都是对list格式元素定义或者删除
>>> d['Adam'] = 67
>>> d['Adam']
67
#删除key
>>> d.pop('Bob')
75
>>> d
{'Michael': 95, 'Tracy': 85}

#set集合
#提供list作为输入集合
>>> s = set([1, 2, 3])
>>> s
{1, 2, 3}
#保持数学集合上的无序性，非重复性
>>> s = {1, 1, 2, 2, 3, 3}
>>> s
{1, 2, 3}
#添加元素
>>> s.add(4)
>>> s
{1, 2, 3, 4}
>>> s.add(4)
>>> s
{1, 2, 3, 4}
#删除元素
>>> s.remove(4)
>>> s
{1, 2, 3}
#交并运算
>>> s1 = {1, 2, 3}
>>> s2 = {2, 3, 4}
>>> s1 & s2
{2, 3}
>>> s1 | s2
{1, 2, 3, 4}
```
# 3. 函数
1. 定义函数
```python
def my_abs(x):
    if x >= 0:
        return x
    else:
        return -x

print(my_abs(-99))
#导入
from abstest import my_abs
#空函数
def nop():
    pass  #作为占位符
#return返回值可以是tuple，实现多值返回
import math
def move(x, y, step, angle=0):
    nx = x + step * math.cos(angle)
    ny = y - step * math.sin(angle)
    return nx, ny
>>> r = move(100, 100, 60, math.pi / 6)
>>> print(r)
(151.96152422706632, 70.0)
```
2. 函数的参数
```python
#位置参数作为占位符
#默认参数在def的时候已经创建并且作用范围是def函数之内
#对于默认参数是list，对其修改后，下次调用的输入参数就是修改后的值，不会重复赋初值，所以默认参数不使用可变对象
def power(x, n=2):
    s = 1
    while n > 0:
        n = n - 1
        s = s * x
    return s
#多默认值
def enroll(name, gender, age=6, city='Beijing'):
    print('name:', name)
    print('gender:', gender)
    print('age:', age)
    print('city:', city)
#紧接着位置参数的默认参数不需要指定参数
enroll('Bob', 'M', 7)
enroll('Adam', 'M', city='Tianjin')
#可变参数
#对于传入位置参数是list或者tuple进行优化
#在调用时自动组装为tuple
def calc(numbers):
    sum = 0
    for n in numbers:
        sum = sum + n * n
    return sum
>>> calc([1, 2, 3])
14
>>> calc((1, 3, 5, 7))
84
#优化后
#*list相当于list的具体元素
def calc(*numbers):
    sum = 0
    for n in numbers:
        sum = sum + n * n
    return sum
>>> calc(1, 2)
5
>>> calc()
0
#如果已经有一个list或者tuple和可变参数函数
>>> nums = [1, 2, 3]
>>> calc(*nums)
14
#关键字参数
#对于传入参数自动组装dict
#可以不输入关键字参数
def person(name, age, **kw):
    print('name:', name, 'age:', age, 'other:', kw)
>>> person('Bob', 35, city='Beijing')
name: Bob age: 35 other: {'city': 'Beijing'}
>>> person('Adam', 45, gender='M', job='Engineer')
name: Adam age: 45 other: {'gender': 'M', 'job': 'Engineer'}
#**不看作二级取值，而是看作dict的专用的取键值对
>>> extra = {'city': 'Beijing', 'job': 'Engineer'}
>>> person('Jack', 24, **extra)
name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}
#命名关键字参数
#*作为分隔符，后面传入的关键字必须是指定的key
def person(name, age, *, city, job):
    print(name, age, city, job)
>>> person('Jack', 24, city='Beijing', job='Engineer')
Jack 24 Beijing Engineer
#如果传入参数包含可变参数，可以省略*，因为可变参数后面的输入参数如果不是键值对，将被判定为可变参数的一部分，那么关键字参数没有输入，报错
def person(name, age, *args, city, job):
    print(name, age, args, city, job)
#可以在关键字命名时设置缺省值
def person(name, age, *, city='Beijing', job):
    print(name, age, city, job)
>>> person('Jack', 24, job='Engineer')
Jack 24 Beijing Engineer
#参数组合
#位置参数，默认参数，可变参数，命名关键字参数，关键字参数
def f2(a, b, c=0, *, d, **kw):
    print('a =', a, 'b =', b, 'c =', c, 'd =', d, 'kw =', kw)
```
# 4. 高级特性
1. 切片
```python
#针对list取前n个元素使用n下标循环的方式优化
>>> L = ['Michael', 'Sarah', 'Tracy', 'Bob', 'Jack']
>>> r = []
>>> n = 3
>>> for i in range(n):
...     r.append(L[i])
... 
>>> r
['Michael', 'Sarah', 'Tracy']
#优化后
#从索引0开始到索引3不包括3
#前后两个值的差值即取出的元素个数
>>> L[0:3]
['Michael', 'Sarah', 'Tracy']
#第一个索引是0可省略
>>> L[:3]
#同理list[-1]可以使用负数
#[:]整个list
#tuple也是一种list，得到的依旧是tuple
#字符串也是可以看做一种list，可以对其进行切片
```
2. 迭代
```python
#可用于for in 的数据类型包括
#集合数据类型，list tuple dict set str
#generator包括生成器和带yield的generator function
#这两类可以直接作用于for的对象统称为Iterable
#判断是否是可迭代对象
>>> from collections.abc import Iterable
>>> isinstance('abc', Iterable) # str是否可迭代
True
>>> isinstance([1,2,3], Iterable) # list是否可迭代
True
>>> isinstance(123, Iterable) # 整数是否可迭代
False

#给定一个list或者tuple，使用for in来遍历
#不局限于有下标的list tuple
##用于dict
###默认迭代key
>>> d = {'a': 1, 'b': 2, 'c': 3}
>>> for key in d:
...     print(key)
...
a
c
b
###迭代value
>>> for value in d.values()
###迭代键值对
>>> for k,v in d,items()
##用于str
>>> for ch in 'ABC':
...     print(ch)
...
A
B
C
#同时迭代索引和元素本身
>>> for i, value in enumerate(['A', 'B', 'C']): #enumerate将list变为索引-元素对
...     print(i, value)
...
0 A
1 B
2 C
```
3. 列表生成式
```python
#同样是从1开始到11结束，不包括11
>>> list(range(1, 11))
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
#含参数遍历
>>> [x * x for x in range(1, 11)]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
#两层循环遍历
>>> [m + n for m in 'ABC' for n in 'XYZ']
['AX', 'AY', 'AZ', 'BX', 'BY', 'BZ', 'CX', 'CY', 'CZ']
#过滤遍历，无else
>>> [x * x for x in range(1, 11) if x % 2 == 0]
[4, 16, 36, 64, 100]
#条件遍历，是遍历后的条件处理，要求覆盖全部结果
>>> [x if x % 2 == 0 else -x for x in range(1, 11)]
[-1, 2, -3, 4, -5, 6, -7, 8, -9, 10]
```
4. 生成器
```python
#generator相较于列表生成式，只保留算法，而不直接存储数据
>>> L = [x * x for x in range(10)]
>>> L
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
>>> g = (x * x for x in range(10))
>>> g
<generator object <genexpr> at 0x1022ef630>
#generator也是可迭代对象
#for in代替next(g)
>>> g = (x * x for x in range(10))
>>> for n in g:
...     print(n)
... 
0
1
4
9
16
25
36
49
64
81
#当算法复杂的时候，可以使用函数生成generator
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        print(b)
        a, b = b, a + b
        n = n + 1
    return 'done'
#将prin(b)改为yield(b)
#该函数调用返回一个generator
#并且遇到yield就返回，等待下一次next()从yield继续执行
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b, a + b
        n = n + 1
    return 'done'
#对于next(odd())是每次都创建一个新的对象
#同样可以使用for in代替
>>> o = odd()
>>> next(o)
step 1
1
>>> next(o)
step 2
3
>>> next(o)
step 3
5
>>> next(o)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```
5. 迭代器
```python
#可以被next()调用并返回下一个值的对象叫做迭代器Iterator
#是惰性序列，可以表示数学上的无穷大小的集合
#Iterable中只有生成器是Iterator对象，其余集合类对象需要iter()转换
>>> isinstance(iter([]), Iterator)
True
#判断是否Iterator
>>> isinstance([],Iterator)
False
```
# 5. 函数式编程
## 1. 高阶函数
```python
#变量能指向函数，而函数能接受变量
def add(x, y, f):
    return f(x) + f(y)
```
1. map/reduce
```python
#map()传入两个参数，第一个是函数，第二个是Iterable，将函数依次作用于Iterable并输出Iterator
#Iterator是惰性序列，需要强迫获取其所有结果需要list()
>>> def f(x):
...     return x * x
...
>>> r = map(f, [1, 2, 3, 4, 5, 6, 7, 8, 9])
>>> list(r)
[1, 4, 9, 16, 25, 36, 49, 64, 81]
#reduce()传入两个参数，第一个是接受两个参数的函数，第二个是Iterable，将函数依次作用于Iterable并输出作为结果，和下一个Iterable一起作为参数传入
reduce(f, [x1, x2, x3, x4]) = f(f(f(x1, x2), x3), x4)

>>> from functools import reduce
>>> def add(x, y):
...     return x + y
...
>>> reduce(add, [1, 3, 5, 7, 9])
25
```
2. filter
```python
#将函数作用于Iterable上，根据返回值判断是都保留，得到的是Iterator惰性序列，需要list()
def is_odd(n):
    return n % 2 == 1
list(filter(is_odd, [1, 2, 4, 5, 6, 9, 10, 15]))
# 结果: [1, 5, 9, 15]
```
3. sorted
```python
#直接排序
>>> sorted([36, 5, -12, 9, -21])
[-21, -12, 5, 9, 36]
#key函数定义排序
#先根据key函数map()之后，根据新的序列排序，再返回对应原始序列的元素
>>> sorted([36, 5, -12, 9, -21], key=abs)
[5, 9, -12, -21, 36]
#字符串排序按照ASCII码大小
>>> sorted(['bob', 'about', 'Zoo', 'Credit'])
['Credit', 'Zoo', 'about', 'bob']
#如果忽略大小写问题
>>> sorted(['bob', 'about', 'Zoo', 'Credit'], key=str.lower)
['about', 'bob', 'Credit', 'Zoo']
#如果翻转顺序
>>> sorted(['bob', 'about', 'Zoo', 'Credit'], key=str.lower, reverse=True)
['Zoo', 'Credit', 'bob', 'about']
```
## 2. 返回函数
1. 闭包
```python
#函数作为返回值
#返回的函数并没有立即执行，而是直到自身被调用
#除去内部函数的传入参数作为占位符替换外，其余返回函数内使用的变量会随着变化而变化
def count():
    fs = []
    for i in range(1, 4):
        def f():
             return i*i
        fs.append(f)
    return fs
f1, f2, f3 = count()
>>> f1()
9
>>> f2()
9
>>> f3()
9

def count():
    def f(j):
        def g():
            return j*j
        return g
    fs = []
    for i in range(1, 4):
        fs.append(f(i)) # f(i)立刻被执行，因此i的当前值被传入f()，j的值被i替换
    return fs
```
2. nonlocal
```python
#内层函数引用外部函数变量正常，到那时对其操作报错
#但是对外层变量操作，解释器会将其作为内层函数的局部变量，会因未定义而报错
#需要对内层函数引用的外层变量进行nonlocal声明
def inc():
    x = 0
    def fn():
        nonlocal x
        x = x + 1
        return x
    return fn

f = inc()
print(f()) # 1
print(f()) # 2
```
## 3. 匿名函数
```python
#lambda只能有一个表达式，不用return
>>> list(map(lambda x: x * x, [1, 2, 3, 4, 5, 6, 7, 8, 9]))
[1, 4, 9, 16, 25, 36, 49, 64, 81]
```