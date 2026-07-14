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
## 4. 装饰器
```python
#函数本身也是对象，可以对对象进行编程
#在执行log的时候定义一个wrapper并返回，替换其中的func
#再次执行时实现对函数的修改以及调用原函数
#执行装饰器之后的now.__name__将变成wrapper
import functools
def log(func):
    @functools.wraps(func)
    def wrapper(*args, **kw):
        print('call %s():' % func.__name__)
        return func(*args, **kw)
    return wrapper
#使用装饰器
@log
def now():
    print('2024-6-1')
>>> now()
call now():
2024-6-1
#相当于
#因为会调用原函数，所以指向变化了但是原函数执行保留
now = log(now)
#如果装饰器带参数
import functools
def log(text):
    def decorator(func):
        @functools.wraps(func)
        def wrapper(*args, **kw):
            print('%s %s():' % (text, func.__name__))
            return func(*args, **kw)
        return wrapper
    return decorator
#相当于
#先执行log('execute')再返回函数作用于now
>>> now = log('execute')(now)
```
## 5. 偏函数
```python
#当函数的参数个数太多，需要简化时，使用functools.partial可以创建一个新的函数，这个新函数可以固定住原函数的部分参数，从而在调用时更简单。
int2 = functools.partial(int, base=2)
#相当于
kw = { 'base': 2 }
int('10010', **kw)
#如果本身不含关键字参数，会看做可变参数的一部分，即每次输入参数都有这个值
max2 = functools.partial(max, 10)
#相当于
args = (10, 5, 6, 7)
max(*args)
```
# 6. 模块
```python
#一个.py文件就是一个模块
#当模块命名冲突，添加顶层包名
#包内必须包含__innit__.py文件，同样也是一个模块，就是顶层包名同名的模块
mycompany
 ├─ web
 │  ├─ __init__.py
 │  ├─ utils.py
 │  └─ www.py
 ├─ __init__.py
 ├─ abc.py
 └─ utils.py
```
## 1. 使用模块
```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

' a test module '

__author__ = 'Michael Liao'

import sys

def test():
    args = sys.argv
    if len(args)==1:
        print('Hello, world!')
    elif len(args)==2:
        print('Hello, %s!' % args[1])
    else:
        print('Too many arguments!')

if __name__=='__main__':
    test()

#_前缀函数看做不应该被别人引用，但实际上是可以引用的，只是编程规范
def _private_1(name):
    return 'Hello, %s' % name

def _private_2(name):
    return 'Hi, %s' % name

def greeting(name):
    if len(name) > 3:
        return _private_1(name)
    else:
        return _private_2(name)
```
## 2. 安装第三方模块
```bash
pip3 install Pillow
#或者安装anaconda有常见的包
```
```python
#模块搜索路径
#相当于寻找模块的环境变量，存储在sys.path中
>>> import sys
>>> sys.path
['', '/Library/Frameworks/Python.framework/Versions/3.6/lib/python36.zip', '/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6', ..., '/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/site-packages']
#添加自己的path
#只在运行时生效
>>> import sys
>>> sys.path.append('/Users/michael/my_py_scripts')
#永久添加PYTHONPATH
```
# 7. 面向对象编程
## 1. 类和实例
```python
#class定义类关键字
#(object)类继承的对象，object是所有类的继承对象
#__init__方法绑定属性，第一个参数永远是self，绑定的是实例的属性，而不是类的属性
class Student(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score
>>> bart = Student('Bart Simpson', 59)
>>> bart.name
'Bart Simpson'
>>> bart.score
59
#数据封装
>>> def print_score(std):
...     print('%s: %s' % (std.name, std.score))
...
>>> print_score(bart)
Bart Simpson: 59
#对于Student实例本身就拥有这些数据，可以内部定义函数
class Student(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score

    def print_score(self):
        print('%s: %s' % (self.name, self.score))
#本身实例的属性是__dict__字典动态存储的，可以给统一类下的不同实体添加或删除属性
class Student:
    def __init__(self, name, score):
        self.name = name
        self.score = score

bart = Student('Bart Simpson', 59)
lisa = Student('Lisa Simpson', 87)
# 查看实例的属性字典
print(bart.__dict__)  # {'name': 'Bart Simpson', 'score': 59}
print(lisa.__dict__)  # {'name': 'Lisa Simpson', 'score': 87}
# 只给bart添加age属性
bart.age = 8
print(bart.__dict__)  # {'name': 'Bart Simpson', 'score': 59, 'age': 8}
print(lisa.__dict__)  # {'name': 'Lisa Simpson', 'score': 87}  # 没有age
#可以限制绑定的属性在class定义类的时候
__slots__ = ('name', 'score')  # 只允许这两个属性
```
## 2. 访问限制
```python
#__私有变量不允许外部访问
class Student(object):
    def __init__(self, name, score):
        self.__name = name
        self.__score = score

    def print_score(self):
        print('%s: %s' % (self.__name, self.__score))
>>> bart = Student('Bart Simpson', 59)
>>> bart.__name
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'Student' object has no attribute '__name'
#但是可以通过方法访问和修改私有变量
class Student(object):
    ...

    def get_name(self):
        return self.__name

    def get_score(self):
        return self.__score
    def set_score(self,score):
        self.__score=score
#_只是不建议访问，没有强制
#不能直接访问__name是因为Python解释器对外把__name变量改成了_Student__name，所以，仍然可以通过_Student__name来访问__name变量
>>> bart._Student__name
'Bart Simpson'
#对应的，如果访问原有的__name会创建一个新的属性
、>>> bart.__name = 'New Name' # 设置__name变量！
>>> bart.__name
'New Name'
```
## 3. 继承和多态
```python
#数学集合上，子类是父类的子集，但是，从数据类型上，子类继承父类的所有方法和属性，并且可以定义自己独立的属性和方法
#子类定义同名方法会覆盖父类的方法
>>> isinstance(a, list)
True
>>> isinstance(b, Animal)
True
>>> isinstance(c, Dog)
True
#子类继承父类的所有数据类型
>>> isinstance(c, Animal)
True
#对于接受父类的函数，因为子类一定继承父类的方法，虽然不一定重新定义自己的方法，但是存在方法可以调用
def run_twice(animal):
    animal.run()
    animal.run()
>>> run_twice(Animal())
Animal is running...
Animal is running...
>>> run_twice(Dog())
Dog is running...
Dog is running...
#对于静态语言来说一定要传入animal类型数据，但是对于动态语言只需要传入的实例有run()这个方法即可，长得像就认为是
```
## 4. 获取对象信息
```python
#type()
>>> type(123)
<class 'int'>
#指向函数或者类
>>> type(abs)
<class 'builtin_function_or_method'>
>>> type(a)
<class '__main__.Animal'>
#除去基本数据类型外，引用types模块
>>> import types
>>> type(fn)==types.FunctionType
True
>>> type(abs)==types.BuiltinFunctionType
True
>>> type(lambda x: x)==types.LambdaType
True
>>> type((x for x in range(10)))==types.GeneratorType
True
#对于class使用isinstace()，瞒住数学集合的子类父类关系
#判断多个类型中的一种
>>> isinstance([1, 2, 3], (list, tuple))
True
>>> isinstance((1, 2, 3), (list, tuple))
True
#dir()获取class的属性和方法
>>> dir('ABC')
['__add__', '__class__',..., '__subclasshook__', 'capitalize', 'casefold',..., 'zfill']
#类似__xxx__的属性和方法在Python中都是有特殊用途的，比如__len__方法返回长度。在Python中，如果你调用len()函数试图获取一个对象的长度，实际上，在len()函数内部，它自动去调用该对象的__len__()方法，所以，下面的代码是等价的：
>>> len('ABC')
3
>>> 'ABC'.__len__()
3
#getattr() setattr() hasattr()
>>> hasattr(obj, 'x') # 有属性'x'吗？
True
>>> obj.x
9
>>> hasattr(obj, 'y') # 有属性'y'吗？
False
>>> setattr(obj, 'y', 19) # 设置一个属性'y'
>>> hasattr(obj, 'y') # 有属性'y'吗？
True
>>> getattr(obj, 'y') # 获取属性'y'
19
>>> obj.y # 获取属性'y'
19
>>> getattr(obj, 'z', 404) # 获取属性'z'，如果不存在，返回默认值404
404>>> hasattr(obj, 'power') # 有属性'power'吗？
True
>>> getattr(obj, 'power') # 获取属性'power'
<bound method MyObject.power of <__main__.MyObject object at 0x10077a6a0>>
>>> fn = getattr(obj, 'power') # 获取属性'power'并赋值到变量fn
>>> fn # fn指向obj.power
<bound method MyObject.power of <__main__.MyObject object at 0x10077a6a0>>
>>> fn() # 调用fn()与调用obj.power()是一样的
81
```
## 5. 实例属性和类属性
```python
#给实例绑定属性
class Student(object):
    def __init__(self, name):
        self.name = name

s = Student('Bob')
s.score = 90
#给类绑定属性
class Student(object):
    name = 'Student'
#类属性是类所有，同类所有实例共享一个类属性
#是在animal->dog->puppy的多一层分类
>>> class Student(object):
...     name = 'Student'
...
>>> s = Student() # 创建实例s
>>> print(s.name) # 打印name属性，因为实例并没有name属性，所以会继续查找class的name属性
Student
>>> print(Student.name) # 打印类的name属性
Student
>>> s.name = 'Michael' # 给实例绑定name属性
>>> print(s.name) # 由于实例属性优先级比类属性高，因此，它会屏蔽掉类的name属性
Michael
>>> print(Student.name) # 但是类属性并未消失，用Student.name仍然可以访问
Student
>>> del s.name # 如果删除实例的name属性
>>> print(s.name) # 再次调用s.name，由于实例的name属性没有找到，类的name属性就显示出来了
Student
```
# 8. 面对对象的高级编程
## 1. __slots__
```python
#给实例绑定新方法
>>> def set_age(self, age): # 定义一个函数作为实例方法
...     self.age = age
...
>>> from types import MethodType
>>> s.set_age = MethodType(set_age, s) # 给实例绑定一个方法
>>> s.set_age(25) # 调用实例方法
>>> s.age # 测试结果
25
#给类绑定新方法
>>> def set_score(self, score):
...     self.score = score
...
>>> Student.set_score = set_score
#__slots__定义允许绑定的属性名称
#仅对当前类实例起作用，对继承子类不起作用
#当仅当子类和父类都使用__slots__的时候，子类才继承并且最终是两者__slots__的并集
```
## 2. @property
```python
#优化方法内部的对数据的检查
#@property实现将方法转化为属性，并且能够直接读取，可读
#@birth.setter实现方法的修改，可写
class Student(object):
    @property
    def birth(self):
        return self._birth

    @birth.setter
    def birth(self, value):
        self._birth = value

    @property
    def age(self):
        return 2015 - self._birth
```
## 3. 多重继承
```python
class Dog(Mammal, RunnableMixIn, CarnivorousMixIn):
    pass
```
## 4. 定制类
```python
#__str__
#创建实例之后的返回值
class Student(object):
    def __init__(self, name):
        self.name = name
    def __str__(self):
        return 'Student object (name=%s)' % self.name
    __repr__ = __str__
>>>Student('Tom')
Student objetc (name=Tom)
#__iter__
#返回一个迭代对象（自身）
class Fib(object):
    def __init__(self):
        self.a, self.b = 0, 1 # 初始化两个计数器a，b

    def __iter__(self):
        return self # 实例本身就是迭代对象，故返回自己

    def __next__(self):
        self.a, self.b = self.b, self.a + self.b # 计算下一个值
        if self.a > 100000: # 退出循环的条件
            raise StopIteration()
        return self.a # 返回下一个值
#创建的可迭代对象
>>> for n in Fib():
...     print(n)
...
1
1
2
3
5
...
46368
75025
#__getitem__
#实现下标访问
class Fib(object):
    def __getitem__(self, n):
        a, b = 1, 1
        for x in range(n):
            a, b = b, a + b
        return a
#要实现list的slice需要对其进行更复杂的操作
#__getattr__
#不同于前面的getattr()函数直接在属性和方法中查找，这里只有在找不到的情况下才进入
#常用于链式调用
class Chain(object):
    def __init__(self, path=''):
        self._path = path

    def __getattr__(self, path):
        return Chain('%s/%s' % (self._path, path))

    def __str__(self):
        return self._path

    __repr__ = __str__
#每访问一级因为没找到而创建一级
>>> Chain().status.user.timeline.list
'/status/user/timeline/list'
#__call__
#将实例本身转化为方法调用，不同于class()是创建一个实例
class Student(object):
    def __init__(self, name):
        self.name = name

    def __call__(self):
        print('My name is %s.' % self.name)
>>> s = Student('Michael')
>>> s() # self参数不要传入
My name is Michael.
#判断是否是一个可调用方法
>>> callable(Student())
True
>>> callable(max)
True
>>> callable([1, 2, 3])
False
```
## 5. 枚举类
```python
#定义一个class类，每个常量都是class的唯一实例
#默认member.value是1开始
from enum import Enum
Month = Enum('Month', ('Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'))
#更精准控制枚举类
from enum import Enum, unique
@unique
class Weekday(Enum):
    Sun = 0 # Sun的value被设定为0
    Mon = 1
    Tue = 2
    Wed = 3
    Thu = 4
    Fri = 5
    Sat = 6
#输出
#name是key名，member是成员，虽然member.name==name
#name用于过程的字典遍历，member用于对象
>>>for name, member in Month.__members__.items():
    print(name, '=>', member, ',', member.value)
Jan => Month.Jan , 1
Feb => Month.Feb , 2
```
## 6. 使用元类
```python
#使用type()创建类
#类明，继承父类，dict字典
>>> def fn(self, name='world'): # 先定义函数
...     print('Hello, %s.' % name)
...
>>> Hello = type('Hello', (object,), dict(hello=fn)) # 创建Hello clas

def create_model(table_name, fields):
    """动态创建数据模型类"""
    # 动态生成 __init__ 方法
    def __init__(self, **kwargs):
        for key, value in kwargs.items():
            setattr(self, key, value)
    # 动态生成 __repr__ 方法
    def __repr__(self):
        attrs = ', '.join(f"{k}={v}" for k, v in self.__dict__.items())
        return f"{table_name}({attrs})"
    # 创建类
    return type(table_name, (), {
        '__init__': __init__,
        '__repr__': __repr__,
        'table_name': table_name,
        **fields  # 添加字段作为类属性
    })
# 使用
User = create_model('User', {
    'id': int,
    'name': str,
    'email': str
})
user = User(id=1, name='Alice', email='alice@example.com')
print(user)             # User(id=1, name=Alice, email=alice@example.com)
print(user.table_name)  # User
```
# 9. 错误，调试和测试
## 1. 错误处理
<a>https://docs.python.org/3/library/exceptions.html#exception-hierarchy</a>

```python
#当我们认为某些代码可能会出错时，就可以用try来运行这段代码，如果执行出错，则后续代码不会继续执行，而是直接跳转至错误处理代码，即except语句块，执行完except后，如果有finally语句块，则执行finally语句块，至此，执行完毕。如果没有错误，执行else
#错误自身也是一个class，子类排在父类后面会被拦截
#跨级多层调用，只要内层调用的函数报错就会被捕获
try:
    print('try...')
    r = 10 / int('2')
    print('result:', r)
except ValueError as e:
    print('ValueError:', e)
except ZeroDivisionError as e:
    print('ZeroDivisionError:', e)
else:
    print('no error!')
finally:
    print('finally...')
print('END')
#错误定位
#但是不会终止而是执行到return
def main():
    try:
        bar('0')
    except Exception as e:
        logging.exception(e)
#抛出错误
#需要自己定义一个类继承
class FooError(ValueError):
    pass
def foo(s):
    n = int(s)
    if n==0:
        raise ValueError('invalid value: %s' % s)
    return 10 / n
def bar():
    try:
        foo('0')
    except ValueError as e:
        print('ValueError!')
        raise   #继续上抛，当前函数无法处理错误，而捕获错误的目的是记录
bar()
#可以在上抛的时候转化逻辑
try:
    10 / 0
except ZeroDivisionError:
    raise ValueError('input error!')
```
## 2. 调试
```python
#assert断言代替print调试输出
#表达式应该是True，否则抛出AssertionError
def foo(s):
    n = int(s)
    assert n != 0, 'n is zero!'
    return 10 / n
def main():
    foo('0')
#关闭assert
$ python -O err.py
Traceback (most recent call last):
  ...
ZeroDivisionError: division by zero
#logging输出错误到日志
#debug info warning error
#设置高等级，低等级不起作用
import logging
logging.basicConfig(level=logging.INFO)
s = '0'
n = int(s)
logging.info('n = %d' % n)
print(10 / n)
#定义到文件输出
import logging
# 基础配置：输出到文件
logging.basicConfig(
    level=logging.INFO,
    filename='app.log',  # 输出到文件
    filemode='a',        # 'a'追加，'w'覆盖
    format='%(asctime)s - %(levelname)s - %(message)s'
)
logging.info("这条日志会写入文件 app.log")
```
## 3. 单元测试
```python
#为实现某一函数模块的正常运行，增加的测试文件
#测试模块的方法必须是test_开始
import unittest
from mydict import Dict
class TestDict(unittest.TestCase):
    def test_init(self):
        d = Dict(a=1, b='test')
        self.assertEqual(d.a, 1)
        self.assertEqual(d.b, 'test')
        self.assertTrue(isinstance(d, dict))
    def test_key(self):
        d = Dict()
        d['key'] = 'value'
        self.assertEqual(d.key, 'value')
    def test_attr(self):
        d = Dict()
        d.key = 'value'
        self.assertTrue('key' in d)
        self.assertEqual(d['key'], 'value')
    def test_keyerror(self):
        d = Dict()
        with self.assertRaises(KeyError):
            value = d['empty']
    def test_attrerror(self):
        d = Dict()
        with self.assertRaises(AttributeError):
            value = d.empty
#运行测试单元
$ python -m unittest mydict_tes
#每个测试方法开始和结束都会分别执行setUp()和tearDown()
class TestDict(unittest.TestCase):
    def setUp(self):
        print('setUp...')
    def tearDown(self):
        print('tearDown...')
```
## 4. 文档测试
```python
#用命令行交互的形式显示输入和输出
#作为测试和示例
# mydict2.py
class Dict(dict):
    '''
    Simple dict but also support access as x.y style.

    >>> d1 = Dict()
    >>> d1['x'] = 100
    >>> d1.x
    100
    >>> d1.y = 200
    >>> d1['y']
    200
    >>> d2 = Dict(a=1, b=2, c='3')
    >>> d2.c
    '3'
    >>> d2['empty']
    Traceback (most recent call last):
        ...
    KeyError: 'empty'
    >>> d2.empty
    Traceback (most recent call last):
        ...
    AttributeError: 'Dict' object has no attribute 'empty'
    '''
    def __init__(self, **kw):
        super(Dict, self).__init__(**kw)

    def __getattr__(self, key):
        try:
            return self[key]
        except KeyError:
            raise AttributeError(r"'Dict' object has no attribute '%s'" % key)

    def __setattr__(self, key, value):
        self[key] = value
if __name__=='__main__':
    import doctest
    doctest.testmod()
```
# 10. IO编程
## 1. 文件读写
```python
#以r模式打开一个文件对象
#默认UTF-8文本
>>> f = open('/Users/michael/test.txt', 'r')
#调用方法，输出str
>>>f.read()
'Hello'
#关闭文件
>>>f.close()
#但是文件读写可能出现IOError
#文件读写出错将不执行f.close
with open('/path/to/file', 'r') as f:
    print(f.read())
#如果文件很小，read()一次性读取最方便；如果不能确定文件大小，反复调用read(size)比较保险；如果是配置文件，调用readlines()最方便：
for line in f.readlines():
    print(line.strip()) # 把末尾的'\n'删掉
#读取二进制文本文件
>>> f = open('/Users/michael/test.jpg', 'rb')
>>> f.read()
b'\xff\xd8\xff\xe1\x00\x18Exif\x00\x00...' # 十六进制表示的字节
#读取非UTF-8文本
#遇到错误编码的处理方式
>>> f = open('/Users/michael/gbk.txt', 'r', encoding='gbk', errors='ignore')
>>> f.read()
'测试'
#写文件同样使用with
with open('/Users/michael/test.txt', 'w') as f:
    f.write('Hello, world!')
```
## 2. StringIO和BytesIO
```python
#在内存中读写
>>> from io import StringIO
>>> f = StringIO()
>>> f.write('hello')
5
>>> f.write(' ')
1
>>> f.write('world!')
6
>>> print(f.getvalue())
hello world!
#也可以整个输入然后逐行输出
>>> from io import StringIO
>>> f = StringIO('Hello!\nHi!\nGoodbye!')
>>> while True:
...     s = f.readline()
...     if s == '':
...         break
...     print(s.strip())
...
Hello!
Hi!
Goodbye!
#BytesIO
>>> from io import BytesIO
>>> f = BytesIO()
>>> f.write('中文'.encode('utf-8'))
6
>>> print(f.getvalue())
b'\xe4\xb8\xad\xe6\x96\x87'
#同样初始化之后读写
>>> from io import BytesIO
>>> f = BytesIO(b'\xe4\xb8\xad\xe6\x96\x87')
>>> f.read()
b'\xe4\xb8\xad\xe6\x96\x87'
```
## 3. 操作文件和目录
```python
#os模块的基本功能
#nt是win，posix是其他
>>> import os
>>> os.name # 操作系统类型
'posix'
#环境变量
>>> os.environ
environ({'VERSIONER_PYTHON_PREFER_32_BIT': 'no', 'TERM_PROGRAM_VERSION': '326', 'LOGNAME': 'michael', 'USER': 'michael', 'PATH': '/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin:/opt/X11/bin:/usr/local/mysql/bin', ...})
#获取某个环境变量的值
>>> os.environ.get('PATH')
'/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin:/opt/X11/bin:/usr/local/mysql/bin'
>>> os.environ.get('x', 'default')
'default'
# 查看当前目录的绝对路径:
>>> os.path.abspath('.')
'/Users/michael'
# 拼接目录，把新的完整路径表示出来:
#拼接分离都是对字符串进行操作，不需要文件真实存在
>>> os.path.join('/Users/michael', 'testdir')
'/Users/michael/testdir'
#分离路径
>>> os.path.split('/Users/michael/testdir/file.txt')
('/Users/michael/testdir', 'file.txt')
#获取文件扩展名
>>> os.path.splitstext('/path/to/file.txt')
('/path/to/file','.txt')
# 创建一个目录:
>>> os.mkdir('/Users/michael/testdir')
# 删掉一个目录:
>>> os.rmdir('/Users/michael/testdir')
# 对文件重命名:
>>> os.rename('test.txt', 'test.py')
# 删掉文件:
>>> os.remove('test.py')
#没有删除文件，可以import shutil实现copyfile()
#获取所有文件
>>> [x for x in os.listdir('.') if os.path.isdir(x)]
['.lein', '.local', '.m2', '.npm', '.ssh', '.Trash', '.vim', 'Applications', 'Desktop', ...]
#对于for in的解读
import os
# 列表推导式（简洁）
dirs1 = [x for x in os.listdir('.') if os.path.isdir(x)]
# 普通for循环（易读）
dirs2 = []
for x in os.listdir('.'):
    if os.path.isdir(x):
        dirs2.append(x)
#获取.py文件，splitext输出两个元素，取下标1
>>>[x for x in os.listdir('.') if os.path.isfile(x) and os.path.splitext(x)[1]=='.py']
['apis.py', 'config.py', 'models.py', 'pymonitor.py', 'test_db.py', 'urls.py', 'wsgiapp.py']
```
## 4. 序列化
```python
#将内存的数据转化为可存储对象
#将任意对象序列化为bytes
>>> import pickle
>>> d = dict(name='Bob', age=20, score=88)
>>> pickle.dumps(d)
b'\x80\x03}q\x00(X\x03\x00\x00\x00ageq\x01K\x14X\x05\x00\x00\x00scoreq\x02KXX\x04\x00\x00\x00nameq\x03X\x03\x00\x00\x00Bobq\x04u.'
#将对象序列化后写入文件
>>> f = open('dump.txt', 'wb')
>>> pickle.dump(d, f)
>>> f.close()
#从文件中反序列化
>>> f=open('dump.txt',rb)
>>> d=pickle.load(f)
>>> f.close()
>>> d
'输出内容'
#json实现不同语言间的数据传输
>>> import json
>>> d = dict(name='Bob', age=20, score=88)
>>> json.dumps(d)
'{"age": 20, "score": 88, "name": "Bob"}'
>>> json_str = '{"age": 20, "score": 88, "name": "Bob"}'
>>> json.loads(json_str)
{'age': 20, 'score': 88, 'name': 'Bob'} #因为dict在py 和json都是{}表示，掐面的dict是强制tuple转化来的
#将实例对象转化为json序列
#obj.__dict__就是存储了实例的所有属性和方法的字典
def studen2dict(std):
    return {
        'name':std.name,
        'age':std.age,
        'score':std.score
    }
>>>print(json.dumps(s,defalut=student2dict))
>>>print(json.dumps(s,default=lambda obj:obj.__dict__))
#反序列化，对于传入一个dict转化为实例
def dict2student(d):
    return Student(d['name'], d['age'], d['score'])
>>> json_str = '{"age": 20, "score": 88, "name": "Bob"}'
>>> print(json.loads(json_str, object_hook=dict2student))
<__main__.Student object at 0x10cd3c190>
```
# 11. 进程和线程
## 1. 多进程
```python
#os.fork()从自身返回值开始复制两份
#一份父进程，返回值是子进程id
#一份子进程，返回值是0
#后续代码都要分别在两个进程中执行
#所以即使只有一个if判断，也是两个执行
#getpid获取自身id，getppid获取父进程id
import os
print('Process (%s) start...' % os.getpid())
# Only works on Unix/Linux/macOS:
pid = os.fork()
if pid == 0:
    print('I am child process (%s) and my parent is %s.' % (os.getpid(), os.getppid()))
else:
    print('I (%s) just created a child process (%s).' % (os.getpid(), pid))
#multiprocessing模块实现跨平台的多版本进程
#传入子进程要执行的函数和参数
from multiprocessing import Process
import os
# 子进程要执行的代码
def run_proc(name):
    print('Run child process %s (%s)...' % (name, os.getpid()))
if __name__=='__main__':
    print('Parent process %s.' % os.getpid())
    p = Process(target=run_proc, args=('test',))
    print('Child process will start.')
    p.start()
    p.join()
    print('Child process end.')
#进程池创建大量子进程
#创建池子，即限定当前并行的任务数
#apply创建任务
#close不再接受创建的任务
#join等待任务完成，即同步
from multiprocessing import Pool
import os,time,random
def vtask(param):
    print(param)
if __name__=='__name__':
    p=Pool(4)
    for i in range(5):
        p.apply_async(vtask,args=(i,))      #apply_async()方法传入第二个参数是命名关键字，并且这里传入tuple只有一个参数，所以(i,)
    p.close()
    p.join()
#subprocess
#创建子进程是外部进程
#subprocess.run()
import subprocess
result = subprocess.run(
    args=['echo', 'Hello World'],   # 命令和参数列表
    capture_output=True,            # 捕获输出
    text=True,                      # 以文本模式返回（否则是bytes）
    timeout=10,                     # 超时时间（秒）
    check=True,                     # 返回值非0时抛出CalledProcessError
    shell=False,                    # 是否通过shell执行
    env=None,                       # 环境变量
    cwd='/tmp',                     # 工作目录
    input='some input',             # 标准输入内容
    encoding='utf-8'                # 编码方式
)
#subprocess.Popen()和somminicate()
#实现创建子进程并且通信输入输出
import subprocess
proc = subprocess.Popen(
    args=['python3', 'script.py'],  # 命令
    stdin=subprocess.PIPE,          # 标准输入管道
    stdout=subprocess.PIPE,         # 标准输出管道
    stderr=subprocess.PIPE,         # 标准错误管道
    text=True,                      # 文本模式
    bufsize=1,                      # 行缓冲
    cwd='/path/to/dir',             # 工作目录
    env={'PATH': '/usr/bin'},       # 环境变量
    universal_newlines=True,        # 文本模式（Python 3.6+）
    shell=False,                    # 不使用shell
    preexec_fn=None,                # 子进程前执行函数（Unix）
    close_fds=True                  # 关闭文件描述符
)
stdout, stderr = proc.communicate(input="Hello World\n")
#进程间通信
#使用multiprocess的Process创建进程
from multiprocessing import Process, Queue
import os, time, random
def write(q):
    print('Process to write: %s' % os.getpid())
    for value in ['A', 'B', 'C']:
        print('Put %s to queue...' % value)
        q.put(value)
        time.sleep(random.random())
def read(q):
    print('Process to read: %s' % os.getpid())
    while True:
        value = q.get(True)
        print('Get %s from queue.' % value)
if __name__=='__main__':
    # 父进程创建Queue，并传给各个子进程：
    q = Queue()
    pw = Process(target=write, args=(q,))
    pr = Process(target=read, args=(q,))
    # 启动子进程pw，写入:
    pw.start()
    # 启动子进程pr，读取:
    pr.start()
    # 等待pw结束:
    pw.join()
    # pr进程里是死循环，无法等待其结束，只能强行终止:
    pr.terminate()
```
## 2. 多线程
```python
#python的线程是真实的posix thread
#threading模块
#自动创建的主线程是MainThreads
import threading 
def worker(args):
    pass
t=threading.Thread(target=worker,args=(1,))
t.start()
t.join()
#多进程中同名变量各自拷贝一份而不影响
#多线程中同名变量共享
#使用try finally不是为实现获取锁异常的阻塞，而是解决成功获取后，执行代码有错而导致后续release不执行的死锁，所以release一定执行
balance = 0
lock = threading.Lock()
def run_thread(n):
    for i in range(100000):
        # 先要获取锁:
        lock.acquire()
        try:
            # 放心地改吧:
            change_it(n)
        finally:
            # 改完了一定要释放锁:
            lock.release()
#要实现多核同时运行，是创建多个进程，同一进程内多线程是GIL锁而线程并发运行
```
## 3. ThreadLocal
```python
#ThreadLocal.xxx相当于在各自线程里绑定各变量而不相互影响
#在a线程是ThreadLocal.xxx==1，在b线程是ThreadLocal.xxx==2
import threading
# 创建全局ThreadLocal对象:
local_school = threading.local()
def process_student():
    # 获取当前线程关联的student:
    std = local_school.student
    print('Hello, %s (in %s)' % (std, threading.current_thread().name))
def process_thread(name):
    # 绑定ThreadLocal的student:
    local_school.student = name
    process_student()
t1 = threading.Thread(target= process_thread, args=('Alice',), name='Thread-A')
t2 = threading.Thread(target= process_thread, args=('Bob',), name='Thread-B')
t1.start()
t2.start()
t1.join()
t2.join()
```
## 4. 分布式进程
```python
#实现多主机线程通信
# task_master.py
#创建QueueManager类继承BaseManager，并注册queue对象，回调函数是lambda
#创建实例
#start()
#通过注册的queue访问
#shutdown()关闭
import random, time, queue
from multiprocessing.managers import BaseManager
# 发送任务的队列:
task_queue = queue.Queue()
# 接收结果的队列:
result_queue = queue.Queue()
# 从BaseManager继承的QueueManager:
class QueueManager(BaseManager):
    pass
# 把两个Queue都注册到网络上, callable参数关联了Queue对象:
QueueManager.register('get_task_queue', callable=lambda: task_queue)
QueueManager.register('get_result_queue', callable=lambda: result_queue)
# 绑定端口5000, 设置验证码'abc':
manager = QueueManager(address=('', 5000), authkey=b'abc')
# 启动Queue:
manager.start()
# 获得通过网络访问的Queue对象:
task = manager.get_task_queue()
result = manager.get_result_queue()
# 放几个任务进去:
for i in range(10):
    n = random.randint(0, 10000)
    print('Put task %d...' % n)
    task.put(n)
# 从result队列读取结果:
print('Try get results...')
for i in range(10):
    r = result.get(timeout=10)
    print('Result: %s' % r)
# 关闭:
manager.shutdown()
print('master exit.')

# task_worker.py
import time, sys, queue
from multiprocessing.managers import BaseManager
# 创建类似的QueueManager:
class QueueManager(BaseManager):
    pass
# 由于这个QueueManager只从网络上获取Queue，所以注册时只提供名字:
QueueManager.register('get_task_queue')
QueueManager.register('get_result_queue')
# 连接到服务器，也就是运行task_master.py的机器:
server_addr = '127.0.0.1'
print('Connect to server %s...' % server_addr)
# 端口和验证码注意保持与task_master.py设置的完全一致:
m = QueueManager(address=(server_addr, 5000), authkey=b'abc')
# 从网络连接:
m.connect()
# 获取Queue的对象:
task = m.get_task_queue()
result = m.get_result_queue()
# 从task队列取任务,并把结果写入result队列:
for i in range(10):
    try:
        n = task.get(timeout=1)
        print('run task %d * %d...' % (n, n))
        r = '%d * %d = %d' % (n, n, n*n)
        time.sleep(1)
        result.put(r)
    except Queue.Empty:
        print('task queue is empty.')
# 处理结束:
print('worker exit.')
```
# 12. 正则表达式
1. \d可以匹配一个数字，\w可以匹配一个字母或数字，.可以匹配任意字符
2. *表示任意个字符（包括0个），用+表示至少一个字符，用?表示0个或1个字符，用{n}表示n个字符，用{n,m}表示n-m个字符，如 \d{3}\s+\d{3,8}
3. '-'是特殊字符，在正则表达式中，要用'\'转义
4. [0-9a-zA-Z\_]可以匹配一个数字、字母或者下划线
5. ^表示行开始，$表示行结束
```python
#表示正则表达式
>>> import re
>>> re.match(r'^\d{3}\-\d{3,8}$', '010-12345')
<_sre.SRE_Match object; span=(0, 9), match='010-12345'>
>>> re.match(r'^\d{3}\-\d{3,8}$', '010 12345')
>>>
#正则表达式的切割，默认不保留分隔符
>>> re.split(r'\s+', 'a b   c')
['a', 'b', 'c']
>>> re.split(r'[\s\,]+', 'a,b, c  d')
['a', 'b', 'c', 'd']
>>> re.split(r'[\s\,\;]+', 'a,b;; c  d')
['a', 'b', 'c', 'd']
#但是切割使用的分组就会保留，因为作为分组的一部分
text = ',a,b,'
# 不保留
re.split(r'[,;]+', text)    # 输出: ['', 'a', 'b', '']  # 开头和结尾产生空字符串
# 保留
re.split(r'([,;]+)', text)  # 输出: ['', ',', 'a', ',', 'b', ',', '']
#分组
>>> m = re.match(r'^(\d{3})-(\d{3,8})$', '010-12345')
>>> m
<_sre.SRE_Match object; span=(0, 9), match='010-12345'>
>>> m.group(0)  #自身
'010-12345'
>>> m.group(1)
'010'
>>> m.group(2)
'12345'
>>> t = '19:05:30'
>>> m = re.match(r'^(0[0-9]|1[0-9]|2[0-3]|[0-9])\:(0[0-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9]|[0-9])\:(0[0-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9]|[0-9])$', t)
>>> m.groups()
('19', '05', '30')
#非贪婪匹配，尽可能少的匹配字符，尽可能让后面的多匹配字符
>>> re.match(r'^(\d+?)(0*)$', '102300').groups()
('1023', '00')
#正则表达式要重复使用，则提前编译
>>> import re
# 编译:
>>> re_telephone = re.compile(r'^(\d{3})-(\d{3,8})$')
# 使用：
>>> re_telephone.match('010-12345').groups()
('010', '12345')
>>> re_telephone.match('010-8086').groups()
('010', '8086')
```
# 13. 常用内建模块
## 1. datetime
```python
#获取当前日期
>>> from datetime import datetime   #导入模块中的指定类
>>> now=datetime.now()
>>> print(now)
2015-05-18 16:28:07.198690
>>> print(type(now))
<class 'datetime.datetime'>
#获取制定日期时间
>>> dt =datetime(2026,7,14,10,55)
>>> print(dt)
2026-07-14 10:55:00
#timestamp和时区没有关系，而是统一的
>>> dt.timestamp
xxx.0
>>> t=12322332232.0
>>> print(datetime.fromtimestap(t))
#输入str转化为datetime
>>> cday=datetime.strptime('2026-07-14 11:01:00','%Y-%m-%d %H:%M:%S')
#datetime转化为str
>>> from datetime import datetime
>>> now = datetime.now()
>>> print(now.strftime('%a, %b %d %H:%M'))
Mon, May 05 16:28
#datetime加减
>>> from datetime import datetime, timedelta
>>> now = datetime.now()
>>> now
datetime.datetime(2015, 5, 18, 16, 57, 3, 540997)
>>> now + timedelta(hours=10)
datetime.datetime(2015, 5, 19, 2, 57, 3, 540997)
>>> now - timedelta(days=1)
datetime.datetime(2015, 5, 17, 16, 57, 3, 540997)
>>> now + timedelta(days=2, hours=12)
datetime.datetime(2015, 5, 21, 4, 57, 3, 540997)
```
## 2. collections
```python
#为加强tuple的可读性，引入namedtuple并且元素的引用可以使用元素名，类似与c的结构体
#创建的类是tuple的子类
>>> from collecions import namedtuple
>>> Point=namedtuple('Point',['x','y'])
>>> p=Piont(1,2)
>>> p.x
1
#list可以实现指定位置pop和append，但是默认是从尾部开始，指定位置执行内部的开销大
#deque实现双向列表，可以leftpop和leftappend
>>> from collections import deque
>>> q = deque(['a', 'b', 'c'])
>>> q.append('x')
>>> q.appendleft('y')
>>> q
deque(['y', 'a', 'b', 'c', 'x'])
#使用dict，当其不存在的值添加默认
#本质上是不存在的key调用函数，而函数返回一个值
>>> from collections import defaultdict
>>> dd = defaultdict(lambda: 'N/A')
>>> dd['key1'] = 'abc'
>>> dd['key1'] # key1存在
'abc'
>>> dd['key2'] # key2不存在，返回默认值
'N/A'
#为实现dict有序
>>> from collections import OrderedDict
>>> d = dict([('a', 1), ('b', 2), ('c', 3)])
>>> d # dict的Key是无序的，依据哈希算法访问
{'a': 1, 'c': 3, 'b': 2}
>>> od = OrderedDict([('a', 1), ('b', 2), ('c', 3)])
>>> od # OrderedDict的Key是有序的，和插入顺序保持一致
OrderedDict([('a', 1), ('b', 2), ('c', 3)])
#二维dict，实现参数组的分类，例如在多个环境中寻找变量的值
from collections import ChainMap
import os, argparse
# 构造缺省参数:
defaults = {
    'color': 'red',
    'user': 'guest'
}
# 构造命令行参数:
parser = argparse.ArgumentParser()
parser.add_argument('-u', '--user')
parser.add_argument('-c', '--color')
namespace = parser.parse_args()
command_line_args = { k: v for k, v in vars(namespace).items() if v }
# 组合成ChainMap:
combined = ChainMap(command_line_args, os.environ, defaults)
# 打印参数:
print('color=%s' % combined['color'])
print('user=%s' % combined['user'])
#counter直接计数
>>> from collections import Counter
>>> c = Counter('programming')
>>> for ch in 'programming':
...     c[ch] = c[ch] + 1
...
>>> c
Counter({'g': 2, 'm': 2, 'r': 2, 'a': 1, 'i': 1, 'o': 1, 'n': 1, 'p': 1})
>>> c.update('hello') # 也可以一次性update
>>> c
Counter({'r': 2, 'o': 2, 'g': 2, 'm': 2, 'l': 2, 'p': 1, 'a': 1, 'i': 1, 'n': 1, 'h': 1, 'e': 1})

```