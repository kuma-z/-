https://www.cnblogs.com/pyedu/p/12452407.html

# Redis

> redis is an open source (BSD licensed), in-memory data structure store used as a database
>
> nosql: not only sql
>
> 官网：redis.io
>
> 在线演练：try.redis.io



## 关系型 & 非关系型

> 关系型
> 1、数据存放在表中，表之间有关系
> 2、通用的SQL操作语言
> 3、大部分支持事务
>
> 非关系型
> 1、没有数据表的概念，不同nosql数据库存放数据位置不同
> 2、没有通用的操作语言
> 3、基本不支持事务，redis支持简单事务

## 支持

- strings
- hashes
- lists
- set
- zset——stored sets with range queriers
- bitmaps
- .....



## 使用

#### set / get / del，存储/获取/删除数据项

```sql
set name test

get name

del name
```



#### type，获取类型

```sql
type name
```



#### incr，数字+1

```sql
set connections 10

-- 为了保证线程安全，官方建议使用incr进行+1操作
incr connections

> (integer) 11

get connections

> "11"
```



#### expire/ttl，设置过期时间/显示剩余过期时间

```sql
set cookie jfa;lkw312
expire cookie 100
ttl cookie
```



#### list列表

##### rpush/lpush/lrange，添加列表值（右/左）/从左到右打印列表值

```sql
rpush lists aaa
rpush lists bbb
lpush lists ccc

lrange lists 0 -1
> 1)"ccc"
> 2)"aaa"
> 3)"bbb"
```



##### llen，返回列表长度

```sql
llen lists
```



##### lpop/rpop，弹出列表值

> 返回弹出值

```sql
lpop lists
rpop lists
```



#### set集合

#### sadd，集合添加数据

```sql
sadd sets aaa
sadd sets bbb
sadd sets ccc
```



#### srem，集合删除数据

```sql
srem sets bbb
-- 成功返回1 无数据返回0
```





#### sismember，判断集合中是否存在该数据

```sql
sismember sets aaa
-- 存在返回1，否则返回0
```





#### smembers，显示集合中所有元素

```sql
sembers sets
> "ccc"
> "aaa"
```





#### sunion，返回所有集合中元素（不重复显示）

```sql
sunion set1 set2 ....
```





### 有序结合

#### zadd

```sql
zadd zset1 1 aaa
zadd zset1 2 bbb
zadd zset1 3 ccc
-- 通过序号1，2，3进行排序
```



#### zrange

```sql
zrange zset1 0 -1
```



### hash

> key-value，结构数据

#### hset

```sql
hset user:1000 name aaa
hset user:1000 email aaa@aaa.com
hset user:1000 passwd aaapass
```



#### hmset

```sql
hmset user:1001 user bbb email bbb@bbb.com pass bbbpass
```



#### hget

```sql
hget user:1000 name
```



#### hgetall

```sql
hgetall user:1000

1) "name"
2) "aaa"
3) "email"
4) "aaa@aaa.com"
5) "passwd"
6) "aaapass"
```



#### hincrby

```sql
hset user:1000 age 18
hincrby user:1000 age 3
-- age+3
```



#### hdel

```sql
hdel user:1000 age
```























