# mysql索引

## 索引是什么

官方文档写了索引的作用和没有索引会带来全表扫描，非常费时间。Indexes are used to find rows with specific column values quickly. Without an index, MySQL must begin with the first row and then read through the entire table to find the relevant rows.
简单的说索引是提高查询速度。这个很好理解，就像是以前的英文词典，找单词如果没有前面目录的话，效率很低，得全文找一遍。

## 为什么需要索引

- 索引是数据表中一个或者多个列进行排序的数据结构
- 索引能够大幅提升检索速度
- 创建、更新索引本身也会耗费空间和时间

## 索引的实现原理

要搞清楚索引的实现原理，先看看索引的底层实现，MySQL索引大部分采用B-Tree实现，B-Tree又有B-树和B+树。还有一些使用Hash索引。

### 二叉搜索树

理解二叉搜索树，对于后面理解B-和B+树很有帮助，因为这2种有些特性跟二叉搜索树很像。二叉搜索树的特点是左孩子的值小于父亲节点的值，父亲节点的值小于右孩子的值，即按二叉树的中序遍历，刚好是一个按小到大排序的。二叉搜索树的查找就可以使用二分查找，如果要查找10，因为10比27小，所以往左孩子找，10<14，还在左孩子找。最坏的情况下，查找的次数等于树的高度。


### B-树，B+树

## 连接

- 内连接（inner join）：两个表都存在匹配时，才会返回匹配行
- 外连接（left join right join）：返回一个表的行，即使另一个没有匹配
- 全连接（full join）: 只要某一个表存在匹配就返回

**内连接**

select * from A inner join B on a.id = b.id

**外连接**

select * from A left join B on a.id = b.id


## 参考资料

https://juejin.im/post/5c754718e51d4525f05461b8
https://juejin.im/post/5c8bd3ebf265da2db2797d92
https://juejin.im/post/5c7a8f2e6fb9a049cd54e8ff
