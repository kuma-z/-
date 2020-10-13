# list

## 存储方式

| name |       | list            |
| ---: | :---: | :-------------- |
|   n1 | ————> | [v11, v12, ...] |
|   n2 | ————> | [v21, v22, ...] |

---



## 操作

### 增

- `lpush(name, values)`
    - 每个新的元素都添加到列表最左边
    - `rpush(name, values)`





---

### 查

- `llen(name)`

- `lindex(name)`
- `lrange(name, start, end)`



---

### 改

- `lpushx(name, value)`
    - name已存在，添加value到列表最左边
    - `rpush(name, value)`

- `linsert(name, where, refvalue, value)`
    - where，BFFORE or AFTER
    - refvalue，标杆值
    - value，要插入的数据

- `lset(name, index, value)`
    - 对index位重新赋值







----

### 删

- `lrem(name, value, num)`
    - value，要删除的值
    - num
        - num=0，删除列表中所有指定值
        - num=2，从前向后，删除两个
        - num=-2，从后向前，删除两个

- `lpop(name)`
    - 左侧区第一个元素，移除并返回
    - `rpop(name)`

- `ltrime(name, start, end)`
    - name列表中移除没有在start-end之间的值





---

## 应用场景

> 使用List的数据结构，可以做简单的消息队列的功能。另外还有一个就是，可以利用lrange命令，做基于redis的分页功能，性能极佳，用户体验好。本人还用一个场景，很合适---取行情信息。就也是个生产者和消费者的场景。LIST可以很好的完成排队，先进先出的原则。

