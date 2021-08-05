# shell

## 如何查找特定的文件

find 

find path [options] params

作用：在指定目录下查找文件

find -name "target3.java"
当前目录递归寻找该目录

find / -name "target3.java"
从根目录递归寻找该文件

find ~ -name "target*"  模糊查询
find ~ -iname "target*"  忽略大小写

man find

## 检索文件内容

grep

grep [options] pattern file

查找文件里符合条件的字符串

grep "mooc" target*

## 管道操作符 |

可将指令连接起来，前一个指令的输出作为后一个指令的输入

find ~ | grep "target"

使用管道注意点：
- 只处理前一个命令正确输出，不处理错误输出
- 右边命令必须能够接收标准输入流，否则传递过程中数据会被抛弃
- sed,awk,grep,cur,head,top,less,more,wc,join,sort,split等

grep 'xxx\[true\]' xx.log | grep -o 'engine\[[0-9a-z]*\]'

ps -ef | grep tomcat

ps -ef | grep tomcat | grep -v "grep"  过滤掉包含grep的内容

## 对文件内容做统计
awk
数据抽取和统计

## 批量替换文件内容
sed

适用于对文本的行内容进行处理

