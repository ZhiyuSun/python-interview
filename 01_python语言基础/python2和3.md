# python2和3

## python2和python3

- print成为函数
- 编码问题。python3不再有unicode对象，默认str就是unicode
- 除法变化。python3除号返回浮点数，如果要返回整数，应使用//
- 类型注解。帮助IDE实现类型检查
- 优化的super()方便直接调用父类函数。Python3.x 和 Python2.x 的一个区别是: Python 3 可以使用直接使用 super().xxx 代替 super(Class, self).xxx :
- 高级解包操作。a, b, *rest = range(10)
- keyword only arguments。限定关键字参数
- chained exceptions。python3重新抛出异常不会丢失栈信息
- 一切返回迭代器。range, zip, map, dict.values, etc. are all iterators
- 性能优化等。。。

## 习题 

### python2和python3的对比

1. print函数

print语句没有了，取而代之的是print()函数。

2. unicode

Python 2 有 ASCII str() 类型，unicode() 是单独的，不是 byte 类型。
现在， 在 Python 3，我们最终有了 Unicode (utf-8) 字符串，以及一个字节类：byte 和 bytearrays。
Python3.X 源码文件默认使用utf-8编码

3. 除法

python3除号返回浮点数，如果要返回整数，应使用//

4. 异常

捕获异常的语法由 except exc, var 改为 except exc as var。

5. 数据类型

一切返回迭代器。range, zip, map, dict.values, etc. are all iterators


## 参考资料

python2和python3中调用父类方法

https://cloud.tencent.com/developer/article/1365782
https://www.runoob.com/python/python-func-super.html

