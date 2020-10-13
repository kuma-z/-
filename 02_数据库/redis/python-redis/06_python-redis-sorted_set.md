# sorted set

> 有序集合，在集合的基础上，为每元素排序；元素的排序需要根据另外一个值来进行比较，所以，对于有序集合，每一个元素有两个值，即：值和分数，分数专门用来做排序。



## 操作



### 增

- `zadd(name, *args, **kwargs)`
    - `zadd("zz",{"n1":1,"n2":2,"n3":3,"n4":4})`

- 





---

### 查

- `zcard(name)`，获取元素数量
- `zcount(name, min, max)`，获取name中分数在[min，max]之间的元素数量
- `zrange( name, start, end, desc=False, withscores=False, score_cast_func=float)`
    - 按照索引范围获取对应有序集合元素
    - `withscores`，是否获取元素分数，默认只获取值
    - `score_case_func`，对分数进行数据转换的函数

- `zscore(name, value)`，获取name中value的分数
- `zrank(name, value)`
    - 获取value在name中的排行，从0开始
    - `zrevrank(name, value)`，从大到小排序
- 





----

### 改

- `zincrby(name, value, amount)`，自增name中value值的分数
- `zinterstore(dest, keys, aggregate=None)`
    - 获取两个有序集合的交集，如果遇到相同值不同分数，则按照aggregate进行操作
    - `aggregate = SUM or MIN or MAX`
- `zunionstore(dest, keys, aggregate=None)`,获取两个有序集合的并集，如果遇到相同值不同分数，则按照aggregate进行操作





---

### 删

- `zrem(name, values)`，删除name中的values
- `zremrangebyrank(name, min, max)`，根据排行范围删除
- `zremrangebyscore(name, min, max)`，根据分数范围删除
- 





---



## 应用场景

> sorted set多了一个权重参数score,集合中的元素能够按score进行排列。可以做排行榜应用，取TOP N操作。