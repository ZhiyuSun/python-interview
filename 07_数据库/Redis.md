
# redis

## 缓存

- 缓解关系数据库（Mysql）并发访问的压力：热点数据
- 减少响应时间：内存IO速度比磁盘快
- 提升吞吐量：Redis等内存数据库单机就可以支撑很大并发

## 数据类型

- string：用来实现简单的kv键值对存储，比如计数器
- list：实现双向链表，比如用户的关注，粉丝列表
- hash：用来存储彼此相关信息的键值对
- set：存储不重复元素，比如用户的关注着
- sorted set：实时信息排行榜

## 持久化方式

- 快照方式：把数据快照放在磁盘二进制文件中，dump,.rdb
- AOF：每一个写命令追加到appendonly.aof中

## redis事务

- 将多个请求打包，一次性、按序执行多个命令的机制
- redis通过MULTI,EXEC,WATCH等命令实现事务功能
- python redis-py pipeline=conn.pipeline(transaction=True)

## 分布式锁

- 使用setnx实现加锁，可以同时通过expire添加超时时间
- 锁的value值可以使用一个随机的uuid或者特定的命名
- 释放锁的时候，通过uuid判断是否是该锁，是则执行释放锁

## 缓存使用模式

- cache aside：同时更新缓存和数据库
- read/write through：先更新缓存，缓存负责同步更新数据库
- write behind caching：先更新缓存，缓存定期异步更新数据库

## 缓存穿透，缓存击穿，缓存雪崩
