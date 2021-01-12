# Java基础

## 基本数据

- byte/8
- char/16
- short/16
- int/32
- float/32
- long/64
- double/64
- boolean/~

### 自动装箱自动拆箱
### 缓存池

## String

String 被声明为 final，因此它不可被继承。

### String, StringBuffer and StringBuilder

1. 可变性

String 不可变
StringBuffer 和 StringBuilder 可变

2. 线程安全

String 不可变，因此是线程安全的
StringBuilder 不是线程安全的
StringBuffer 是线程安全的，内部使用 synchronized 进行同步

## 运算

### 参数传递

Java 的参数是以值传递的形式传入方法中，而不是引用传递。

### float与double

### 隐式类型转换

### switch

## 关键字

### final
