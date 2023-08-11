---
title: "Redis 教程"
date: 2023-08-07T21:13:39+08:00
---

## redis 客户端

`redis` 客户端二进制名为`redis-cli`

输入redis可以进入下面的shell的环境
![png](redis-cli.png)

注意此时需要保证服务端是启动的

![png](redis-server.png)

通过set和get能够设置的缓存的变量和进行变量的获取

```shell
127.0.0.1:6379> set mykey "hello world"
OK
127.0.0.1:6379> get mykey
"hello world"
127.0.0.1:6379> 
```

- h: 指定server域名 
- p: 指定端口
- a: 指定password


## redis 变量

### 1. 字符串
redis 的字符串用于存储序列化的字符，包括文本，序列化的对象等。

redis的key值默认被当作是字符串

使用mset和mget可以进行键值对的批量化匹配。

```shell
127.0.0.1:6379> mset boy1 aa boy2 bb boy3 cc
OK
127.0.0.1:6379> mget boy1 boy2 boy3
1) "aa"
2) "bb"
3) "cc"
```


### 2. json

如果你直接使用的是slack-server，那么可能无法使用到JSON的相关功能，需要使用redis-stack或者添加json模块。

总体来说使用json和其他类型并没有太多的不同

```shell
JSON.SET/GET/DEL <key> $ '"<value>"'
```



### 3. list

redis 中的list通常被用来实现队列和栈或者进行队列的管理

- LPUSH: 向队列的头部添加元素
- RPUSH: 向队列的尾部添加元素
- LLEN：返回队列的长度
- LRANGE：获取到特定长度范围内的元素


### 4. sets

sets是一个无序的唯一变量的集合，可以用于追踪唯一性的东西或者展示关系

- SADD：向set中添加一个新成员
- SREM：从set中删除一个新成员
- SCARD：获得到set的大小

同时对于多个set之间可以执行运算操作，


### 5. zsets

zsets是一个有序的集合

## 5. 和数据交互

### 5.1 FT(full-text search)



