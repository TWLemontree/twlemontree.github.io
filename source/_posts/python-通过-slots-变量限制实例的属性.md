---
title: Python笔记-通过__slots__变量限制实例的属性
date: 2018-02-27 15:50:46
tags: python
---

## 前言
Python 是一门动态语言，当我们定义一个类，并创建了一个类的实例后，我们可以给该实例绑定任何属性和方法。然而某些情况下，我们并不想这样。假设我们定义了一个鸵鸟类，别人在使用他时添加了一个“飞”的方法，或者“会飞”的属性，这显然是不合理的。我们需要对实例进行一些限制，使其不能随心所欲的添加属性或者方法。

```python
# 演示程序，python的实例对象可以随心所欲的添加属性或方法
from types import MethodType


class TestClass(object):
    '''这是一个测试类，不实现任何功能'''
    pass


def test_func(self):
    '''这个方法即将要添加到实例对象中'''
    print("----test_func----")


t = TestClass()
t.name = "name"
print(t.name)
# 给实例对象添加的方法，类的其它实例对象无法使用
# 如果想其它实例对象也可使用该方法，应该讲方法添加给类
# TestClass.test_func = test_func 
t.test_func = MethodType(test_func, t) 
t.test_func()
```

## 通过 __slots__ 限制实例对像
Python 运行在定义 class 的时候，定义一个特殊的变量 __slots__ ，来限制该 class 实例能添加的属性

```python
class TestClass(object):
    __slots__ = ["name", "age"]


t = TestClass()
t.name = 'lemontree'
t.age = 23
t.addr = 'LY' 
```

从运行结果来看，我们可以动态的添加 name 属性和 age 属性，但是当添加 addr 属性时就会报错（AttributeError）。

## 注意
__slots__ 定义的属性仅对当前类实例起作用，对继承的子类是不起作用的。除非也在子类中定义 __slots__ ，这样，子类实例允许定义的属性就是自身的 __slots__ 加上父类的 __slots__ 。

## 参考文献
[廖雪峰的官方网站（使用__slots__）](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/00143186739713011a09b63dcbd42cc87f907a778b3ac73000)
