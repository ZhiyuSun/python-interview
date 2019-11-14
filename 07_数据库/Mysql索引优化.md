# mysql索引

## 为什么需要索引

- 索引是数据表中一个或者多个列进行排序的数据结构
- 索引能够大幅提升检索速度
- 创建、更新索引本身也会耗费空间和时间

## B-树，B+树

### 连接

- 内连接（inner join）：两个表都存在匹配时，才会返回匹配行
- 外连接（left join right join）：返回一个表的行，即使另一个没有匹配
- 全连接（full join）: 只要某一个表存在匹配就返回

**内连接**

select * from A inner join B on a.id = b.id

**外连接**

select * from A left join B on a.id = b.id
