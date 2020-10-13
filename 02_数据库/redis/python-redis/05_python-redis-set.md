# set

> 不允许重复的列表

## 操作

### 增

- `sadd(name, values)`







---

### 查

- `scard(name)`
    - 获取name对应的集合中元素个数

- `smembers(name)`
    - 查看name所有成员

- `sismember(name, value)`
    - 判断value是否在name集合中

- `srandmember(name, nums)`
    - 随机取name中的nums个元素

- `sdiff(key, *args)`
    - 差值
    - 不太会用

- `sinter(key, *args)`
    - 交集
    - 不太会用

- `r.sunion(key, *args)`
    - 并集



-----

### 改





----

### 删

- `s.pop(name)`
    - 从name中弹出一个元素，并将其返回

- `srem(name, values)`
    - 在name中删除某些值，成功返回删除个数
    - values不在name中返回0





---

## 应用场景

> 因为set堆放的是一堆不重复值的集合。所以可以做全局去重的功能。
>
> 另外，就是利用交集、并集、差集等操作，可以计算共同喜好，全部的喜好，自己独有的喜好等功能。