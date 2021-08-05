# IO

## 如何提升并发能力

一些常见的提升并发能力的方式
- 多线程模型，创建新的线程处理请求
- 多进程模型，创建新的进程处理请求
- IO多路复用，实现单进程同时处理多个socket请求

- 线程/进程创建开销比较大，可以用线程池方式解决
- 线程和进程比较占用资源，难以同时创建太多

## 什么是IO多路复用

操作系统提供的同时监听多个socket的机制
- 为了实现高并发需要一种机制并发处理多个socket
- Linux常见的是select/poll/epoll
- 可以使用单线程单进程处理多个socket

两个过程：
- 内核等待数据
- 数据从内核拷贝到用户进程

## IO相关

- BIO：同步阻塞式调用
- NIO：同步非阻塞。（Java中广泛应用）
select
- AIO：异步IO。

BIO(blockio):InputStream和OutputStream，Reader和writer

NIO(nonblock-io):构建多路复用的，同步非阻塞的IO操作
- nio-channels
- nio-buffer
- nio-selector
nio的底层用了IO多路复用

AIO：基于事件和回调机制

BIO、NIO、AIO对比
属性\模型       阻塞BIO     非阻塞NIO       异步AIO
blocking        阻塞并同步  非阻塞但同步    非阻塞并异步
线程数          1:1         1:N             0:N
复杂度          简单        较复杂          复杂
吞吐量          低          高              高

## 五种IO

前四种都是同步

同步阻塞IO： 去饭馆吃饭 去了之后都在门口等着不能离开 
同步非阻塞IO： 去了饭馆吃饭  就可以去干别的了 时不时回来看看
同步阻塞IO复用：去了饭馆门口，饭馆有个服务员，付服务员 有位了就让你进去
同步非阻塞信号驱动： 去了饭馆吃饭 去了之后领个号 就可以去干别的了 到你了 直接微信给你弹消息让你来
异步IO模型： 你去签个到 就去干别的了 做好了 直接找你去送过来

## select和epoll的区别

- 数量上限
- 轮询 or 回调

select模型

应用程序——select——解除阻塞——循环遍历查找收到读信号的连接——socket recv
select缺陷：1024数组个数的限制，遍历轮询触发找到真正有信号的socket连接

epoll模型

epoll改进：没有1024数组个数的限制.异步回调的方式去执行handler操作
应用程序——epoll，socket连接handler——触发handler回调机制——handler

epoll性能比select强很多，nginx就是epoll模型

Java面试里面有三种的比较，讲的还挺好的
有很多图，还有对比

select、epoll、epoll的区别
- 支持一个进程所能打开的最大连接数。
    - select：单个进程所能打开的最大连接数由FD_SETSIZE宏定义，其大小是32个整数的大小（在32位的机器上，大小是32*32,64位机器上FD_SETSIZE为32*64）,我们可以对其进行修改，然后重新编译内核，但是性能无法保证，需要做进一步测试
    - poll：本质上与select没有区别，但是它没有最大连接数的限制，原因是它是基于链表来存储的
    - epoll：虽然连接数有上限，但是很大，1G内存的机器上可以打开10万左右的连接
- FD剧增后带来的IO效率问题
    - select：因为每次调用时都会对连接进行线性遍历，所以随着FD的增加会造成遍历速度的线性下降的性能问题
    - poll：同上
    - epoll：由于epoll是根据每个fd上的callback函数来实现的，只有活跃的socket才会主动调用callback，所以在活跃socket较少的情况下，使用epoll不会有线性下降的性能问题，但是所有socket都很活跃的情况下，可能会有性能问题。
- 消息传递方式
    - select：内核需要将消息传递到用户空间，需要内核的拷贝动作
    - poll：同上
    - epoll：通过内核和用户空间共享一块内存来实现，性能较高


## 我的整理

两个步骤：
- 等待返回数据
- 数据从内核复制到用户空间



## 参考资料

慕课网Java面试
小林coding
http://www.cyc2018.xyz/%E8%AE%A1%E7%AE%97%E6%9C%BA%E5%9F%BA%E7%A1%80/Socket/Socket.html#%E5%BC%82%E6%AD%A5-i-o
https://segmentfault.com/a/1190000003063859


一篇讲的很好的关于Java NIO和IO模型的文字
https://www.cnblogs.com/ljl150/p/12642726.html

美团技术团队,NIO浅析
https://tech.meituan.com/2016/11/04/nio.html