# 自动化测试相关

- 测试框架：Unittest/pytest（推荐）/nose、allure（报告）
- 接口自动化：requests（推荐）/httprunner
- app/web自动化：appium/selenium
- 性能：locust
- 设计模式PageObject（POM）、poium
- 测试开发：django/flask





# 基本语法

## 环境建立

- 安装python
  - 环境变量
- 安装pip，如果没有自带
- 修改pip原
  - `c:\ProgramData\pip\pip.ini`

- 安装IDE
  - pycharm
  - vscode



## 基本数据类型

- 数字类型
  - 整数，int
  - 长整型，long
  - 浮点型，float
- 字符串，string
  - 不可变，有序
- 列表，list
  - 可变，有序
- 元组，tuple
  - 固定长度不可变
- 字典，dictionary
  - 无序
- 集合，set
  - 无重复
- 布尔。bool



## 数据类型转换

- `type`函数
- 字符串与整型
  - `int(s[, base])`
  - `str(x)`
- 整型转浮点型
  - `float(i)`
- 列表元组互转
  - `tuple(l)`
  - `list(t)`
- 嵌套元组转字典
  - `dict(s)`

- `eval(str)`，判断字符串是否有效





## 基本运算符

### 算术运算符

- +、-、*、/
- %，取模
- **，幂运算
- //，取整除



### 比较运算符

- ==、！=
- <、>、>=、<=



### 赋值运算符

- =、+=、-=、*=、/=



### 逻辑运算符

- and
- or
- not



### 成员运算符

- in 、not in





## 流程控制

- `if`
  - `if ... `
  - `if ... else ...`
  - `if ... elif ... else ...`

- `for`
  - `for ... in ...    `

- `while`
- `break & continue`
  - `break，跳出当前循环`
  - `continue，跳出本次循环`



---

## 数据类型

### 字符串

- 字符串连接
  - `str1 + str2`

- 字符串重复输出
  - `str1 * n`
- 索引
  - `str[i]`
- 切片
  - `str[i: j]`，左闭右开
- 原始字符串
  - 所有的字符串都是直接按照字⾯的意思来使⽤，没有转义特殊或不能打印的字符
  - `s = r'abd\ndef'`
- 格式化输出
  - `a = 'test'   b = f'123{a}123'`



### 列表

> 有序的
>
> 可变的
>
> 不可哈希的
>
> 可变的对象是不可哈希的

- 增
  - `l.append(n)`
  - `l.extend(l2)`
      - 等价于`l=l+l2`
  - `l.insert(index, a)`
- 删
  - `l.pop()`
  - `l.remove(n)`
      - 只删除第一次
  - `del l[i]`
  - `l.clear()`
- 改
  - `l.insert(2, 'd')`
- 查
  - `l.reverse()`
  - `l.sort([key])`
      - `a.sort(key=lambda x:x[1])`
  - `l.index(n)`
  - `l.count(a)`

- 索引 & 切片
    - `list[start:stop:interval]`

- `in` & `not in`
- 列表与数字
    - `[2]*3 ==> [2,2,2]`

- 列表生成式
    - `a=[i for i in range(50) if i&1]`

- 列表=>栈
    - `l.append(n)`，O(!)
    - `l.pop()`，O(1)
    - 可以高效实现栈

- 插入元素性能分析
    - 时间复杂地O(n)
    - ***涉及频繁插入元素操作不适合用列表***

- 深浅拷贝
    - 浅拷贝，`list.copy()`
        - 只拷贝表面一层
        - 涉及嵌套时，修改拷贝列表嵌套字符，源列表也会受影响
    - 深拷贝，`copy.deepcopy()`
        - 全面拷贝



---

### 元组









---

### 字典

- 增
  - `d["key"] = value`
- 删
  - `del d['key']`
- 改
  - `d['key'] = new_value`
- 查
  - `d.get('key')`，key不存在则返回空







---

### 集合









---



## 

