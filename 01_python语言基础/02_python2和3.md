# python2和3

## python2和python3

- print成为函数
- 编码问题。python3不再有unicode对象，默认str就是unicode
- 除法变化。python3除号返回浮点数，如果要返回整数，应使用//
- 类型注解。帮助IDE实现类型检查
- 优化的super()方便直接调用父类函数
- 高级解包操作。a, b, *rest = range(10)
- keyword only arguments。限定关键字参数
- chained exceptions。python3重新抛出异常不会丢失栈信息
- 一切返回迭代器。range, zip, map, dict.values, etc. are all iterators
- 性能优化等。。。
