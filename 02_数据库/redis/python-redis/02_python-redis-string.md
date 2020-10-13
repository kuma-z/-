# `string`类型

> 字符串类型是 Redis 中最为基础的数据存储类型，它在 Redis 中是二进制安全的，也就是byte类型
> 最大容量是512M。

## 存储方法

| name |       | value |
| ---: | :---: | :---- |
|   n1 | ————> | v1    |
|   n2 | ————> | v2    |
|   n3 | ————> | v3    |
|   n4 | ————> | v4    |

---

## 操作

### `set(name, value, ex=None, px=None, nx=False, xx=False)`

> 在Redis中设置值，默认，不存在则创建，存在则修改
> 参数：
>      ex，过期时间（秒）
>      px，过期时间（毫秒）
>      nx，如果设置为True，则只有name不存在时，当前set操作才执行
>      xx，如果设置为True，则只有name存在时，岗前set操作才执行

---

### 增

- `set(name, value, ex=None, px=None, nx=False, xx=False)`

```python
r.set('foo', 'bar')
r.set('foo', 'bar', ex=10)
r.set('foo', 'bar', px=10000)
```

- `setnx(name, value)`
    - name不存在时，执行添加

- `setex(name, value, time)`
    - time为过期时间
    - 时间格式：s 或 timedelta对象

- `psetex(name, time_ms, value)`
    - time_ms为过期时间
    - 时间格式：ms 或 timedelta对象

- `mset(*args, **kwargs)`
    - `mset({'k1': 'v1', 'k2': 'v2'})`

---

### 查

- `get(name)`
- `mget(keys, *args)`
    - `mget(key1, key2)`
    - `mget({key1, key2})`

- `getrange(name, start, end)`
    - 获取name的子序列

- `strlen(name)`
    - 获取name长度





---

### 改

- `getset(name, new_value)`
    - 获取原值，并赋新值

- `setrange(name, offset, value)`
    - 修改内容过长则向后添加

- `incr(name, amount=1)`
    - 自增，默认1

- `incrbyfloat(name, amount=1.0)`
    - 自增，默认1.0

- `decr(name, amount=1)`
    - 自减，默认1

- `append(name, value)`
    - 将value添加到name值后，没有则新建
    - 返回修改后长度



----

### 删



---



## 应用场景

> 最常规的set/get操作，value可以是String也可以是数字。一般**做一些复杂的计数功能的缓存**，比如减少库存。