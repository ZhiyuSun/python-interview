# mysql

## 事务

- 事务是数据库并发控制的基本单位
- 事务可以看做是一系列SQL语句的集合
- 事务必须要么全部执行成功，要么全部执行失败

## ACID

- 原子性（Atomicity）: 一个事务中所有操作全部完成或失败
- 一致性（Consistency）: 事务开始和结束之后数据完整性没有被破坏
- 隔离性（Isolation）: 允许多个事务同时对数据库修改和读写
- 持久性（Durability）: 事务结束之后，修改是永久的不会丢失

## 乐观锁，悲观锁

- 悲观锁是先获取锁再进行操做。一锁二查三更新。select for update
- 乐观锁先修改，更新的时候发现数据已经变了就回滚。check and set
- 使需要根据响应速度、冲突频率、重试代价来判断使用哪一种

## musql常用类型

char/varchar/tinytext/text
tinyint/smallint/mediumint/int/sigint/float/double
date/datetime/timestamp

## InnoDB vs MyISAM

- MyISAM不支持事务，InnoDB支持事务
- MyISAM不支持外键，InnoDB支持外键
- MyISAM只支持表锁，InnoDB支持行锁和表锁


2021.01.05更新
- MyISAM是非事务安全的，而InnoDB是事务安全的
- MyISAM锁的粒度是表级的，而InnoDB支持行级锁
- MyISAM支持全文类型索引，而InnoDB不支持全文索引
- MyISAM相对简单，效率上要优于InnoDB，小型应用可以考虑使用MyISAM
- MyISAM表保存成文件形式，跨平台使用更加方便

参考资料：https://juejin.cn/post/6903101301429796871

## 参考资料

《『MySQL』深入理解事务的来龙去脉》

https://juejin.im/post/5cbc049de51d456e7b372089