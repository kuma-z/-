# yaml

## 语法规则

- 基本语法
    - 1.大小写敏感
    - 2.使用缩进表示层级关系
    - 3.不允许使用 TAB 键来缩进，只允许使用空格键来缩进
    - 4.缩进的空格数量不重要
    - 5.使用"#"来表示注释
- 数据格式
    - 对象：键值对的集合，又称映射 (mapping) / 哈希（hashes）/ 字典 (dictionary)
    - 数组: 一组按次序排列的值，又称序列 (sequence) / 列表 (list)
    - 纯量 (scalars) ：单个的，不可再分的值
- python调用
    - `pip install pyyaml`
- 



## yaml与python

对象

```python
yaml
name:test
    
python
{"name" : "test"}


yaml
person: {name: nemo, sex: 男}

python
{'person': {'name': 'nemo', 'sex': '男'}}


```



数组

```python
yaml
- cat
- dog
- fish

python
['cat', 'dog', 'fish']


yaml
- 
    - cat
    - dog
-
    - fish

python
[ [ 'cat', 'dog' ], [ 'fish' ] ]


yaml
animal: ['dog', 'cat']
    
python
{ animal: [ 'dog', 'cat' ] }
```

纯量

```python
yaml
    number: 15.01
    string: hi
    bool: true
    nothing: ~
    date: 2018-01-01
    time: 2018-01-01 12:12:12

python
    {
        'number': 15.01, 
        'string': 'hi',
        'bool': True, 
        'nothing': None, 
        'date': datetime.date(2018, 1, 1), 
        'time': datetime.datetime(2018, 1, 1, 12, 12, 12)
    }
```



### 引用

- 锚点`&`和别名`*`，可以用来引用
    - `&`用来建立锚点（`defaults`），
    - `<<`表示合并到当前数据，`*`用来引用锚点。
- 

```yaml
defaults: &defaults
  adapter:  postgres
  host:     localhost

development:
  database: myapp_development
  <<: *defaults

test:
  database: myapp_test
  <<: *defaults

================等同于===================

defaults:
  adapter:  postgres
  host:     localhost

development:
  database: myapp_development
  adapter:  postgres
  host:     localhost

test:
  database: myapp_test
  adapter:  postgres
  host:     localhost
```



