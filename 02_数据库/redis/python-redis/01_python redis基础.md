#  python redis

> `pip install redis`



## 链接redis

```python
import redis

r = redis.Redis(host="localhost", port=6379, db=0)
r.set('foo', 'bar')
r.get('foo')
```

> 使用connection pool来管理对一个redis server的所有连接，**避免每次建立、释放连接的开销**。默认，每个Redis实例都会维护一个自己的连接池。可以直接建立一个连接池，然后作为参数Redis，这样就**可以实现多个Redis实例共享一个连接池**。

```python
import redis

pool = redis.ConnectionPool(host='127.0.0.1', port=6379)
r = redis.Redis(connection_pool=pool)
r.set('foo', 'bar')
r.get('foo')
```

## 操作

- `exists(name)`
- `delete(name)`
- `type(name)`
- `keys(pattern)`
    - 获取符合pattern规则的key

- `randomkey()`
- `rename(old_name, new_name)`
- `dbsize()`
    - 获取当前数据库中key的数目

- `expire(name, time)`
    - time单位s

- `ttl(name)`
    - -1为永不过期

- `move(name, db)`
    - 将key移到其他数据库

- `flushdb()`
    - 删除当前数据库的所有key
    - **慎用**

- `flushall()`
    - 删除所有数据库的所有key
    - **慎用**





## 管道

> redis-py默认在执行每次请求都会创建（连接池申请连接）和断开（归还连接池）一次连接操作，如果想要在一次请求中指定多个命令，则可以使用pipline实现一次请求指定多个命令，并且默认情况下一次pipline 是原子性操作。



```python
import redis
  
pool = redis.ConnectionPool(host='10.211.55.4', port=6379)
r = redis.Redis(connection_pool=pool)
# pipe = r.pipeline(transaction=False)
pipe = r.pipeline(transaction=True)
  
pipe.set('name', 'alex')
pipe.set('role', 'sb')
  
pipe.execute()
```

