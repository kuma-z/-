# hash

## 存储模式

| name |       | hash                                  |
| ---: | :---: | ------------------------------------- |
|   n1 | ————> | k1 -> v1 <br />k2 -> v2<br />k3 -> v3 |
|   n2 | ————> | k1 -> v1 <br />k2 -> v2<br />k3 -> v3 |
|      |       |                                       |

## 操作

### 增

- `hset(name, key, value)`
- `hmset(name, mapping)`
    - `mapping = {k1:v1, k2:v2}`



----

### 查

- `hget(name,key)`

- `hgetall(name)`

- `hmget(name, *keys)`
    - `hmget('abc', ['a', 'b'])`
    - `hmget('abc', 'a', 'b')`

- `hlen(name)`
    - 返回name中键值对个数

- `hkeys(name)`
- `hvals(name)`
- ``hexists(name, key)`
- `hscan_iter(name, match=None, count=None)`
    - 利用yield封装hscan创建生成器，实现分批去redis中获取数据
    - match，匹配指定key，默认None 表示所有的key
    - count，每次分片最少获取个数，默认None表示采用Redis的默认分片个数
    - 返回结果是`tuple`



---

### 改

- `hincrby(name, key, amount=1)`
- `hincrbyfloat(name, key, amount=1.0)`





---

### 删

- `hdel(name, *keys)`





----

## 应用场景

> 这里value存放的是结构化的对象，比较方便的就是操作其中的某个字段。博主在做单点登录的时候，就是用这种数据结构存储用户信息，以cookieId作为key，设置30分钟为缓存过期时间，能很好的模拟出类似session的效果。