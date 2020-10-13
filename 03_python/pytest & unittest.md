# 单元测试

- 什么是单元测试
- 单元测试的价值
- 单元测试的难点
- 单元测试的覆盖率
  - 语句覆盖
  - 判断覆盖
  - 条件覆盖
  - 路径覆盖



## 代码覆盖率

- 代码覆盖率也被用于自动化测试和手工测试，来度量测试是否全面的标准之一
- 应用覆盖率的思想增强测试用例设计





# Unittest

## 编写规范

- `import unittest`
- 必须继承`unittest.TestCase`
- 测试方法必须`test_`开头
- 模块名字，类名没有要求



## `setup`  & `tearDown`

- 基于测试方法级别的`setUp & tearDown`
  - 每执行一个测试方法时都会执行一次`setup & tearDown`
  - 注意`setUp & tearDown`书写

- 基于类级别的`setUpClass & tearDownClass`
  - 执行这个类列所有测试方法，只执行一次`setUp & tearDown`
  - 定义时，声明类方法`@classmethod`

- 机遇模块级别的`setUpModule & tearDownModule`
  - 执行此模块里所有类的测试方法，只执行一次`setUp & tearDown`
  - 在类外定义`def setUpModule`

- 注意不同级别定义方式不同



## 生成测试报告

- `htmltestrunner`





# `pytest`

## 优势

- 简单灵活，像写python代码一样写测试用例
- 为测试方法输入不同参数化
- 自动重试失败测试用例
- 支持allure2测试报告
- 很多第三方插件，且可以自定义
  - http://plugincompat.herokuapp.com/



## 编写规范

- 测试文件以`test_`开头，或者`_test`结尾（二选一）
- 测试类以`Test`开头，且不能带有`__init__`方法
- 测试函数以`test_`开头



## 第三方插件

- 安装
  - `pip3 install pytest-sugar`

- `pytest-sugar`
- `pytest-assume`
- `pytest-ordering`
- `pytest-selenium`
- `pytest-play`
- `pytest-rerunfailures`
- `pytest-allure`
- `pytest-datadir`
- `pytest-datafiles`



**建议使用版本pytest3.8.0**



## 执行

- 命令行
  - `> pytest test_example.py`



## pytest参数化

```python
#test_parameters.py
import pytest
@pytest.mark.parametrize("
x,y", [
    (3+5, 8),
    (2+4, 6),
    (6*9, 42),
])
def test_add(x, y):
    assert x == y

```

- 使用时，参数名和变量名必须对应



## `pytest-assume`

```python
import pytest
def test_multiple_assert():
    pytest.assume(1 == 2)
    pytest.assume(2 == 2)
    pytest.assume(3 == 2)
```



- 遇到判断失败的用例时，也会继续执行



## `pytest-rerunfails`

> web、app自动化测试中，进场出现超时导致的失败用例



- 使用方法
  - `pytest --reruns 3 test_example.py`
  - `pytest -s --reruns 3 test_example.py`



## `pytest-ordering`

> 上下测试用例页面切换有依赖关系
>
> 修改页面信息，依赖于前面已经创建好的信息



![](.\image\pytest-ordering.png)





## `pytest`练习

```python
#pytest_practice.py
#! /usr/bin/env python
#coding=utf-8
import random
def bubble_sort(nums):
    for i in range(len(nums)-1):
        for j in range(len(nums)-i-1):
            if nums[j] > nums[j+1]:
                nums[j], nums[j+1] = nums[j+1], nums[j]
    return random.choice([nums,None,10])

```



![](.\image\pytest插件.png)





##  `allure`

version==2.7





# 作业

![](.\image\作业.png)

建议使用python/shell分别完成

`import subprocess`

`import glob`

`import os`

glob和os中都有可以递归查找目录下文件的方法





