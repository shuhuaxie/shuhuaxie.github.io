---
layout: post
title:  "2019-12-10-dart isolate.markdown"
date:   2019-12-10 12:11:30 +0800

1. isolate 孤立的,独立的

2. isolate有独立的内存和event loop

3. Dio如何使用isolate,他网络请求运行在什么isolate中.跟flutter平台中的四个Runner有什么关系,(io Runner)

4. isolate如何管理,需要缓存吗.

window的点击事件是如何传递给isolate的.直接回调是不是运行在native的线程中,怎么传递给dart的isolate.

5. 优势
1) 内存分配和回收不需要加锁
2) 当线程不操作数据时,内存不会被改变
3) 在flutter中有大量Widget需要回收,在dart中速度很快

6. 生命周期

7. 权限控制
Isolate对象允许其他isolate控制、监听它所代表的isolate的事件循环，例如当这个isolate发生未捕获错误时，
可以暂停(pause)此isolate或获取(addErrorListener)错误信息。

controlPort识别并授予对isolate控制的权限，pauseCapability和terminateCapability会对某些控制操作
进行权限保护。例如，暂停(pause)一个无pauseCapability的Isolate对象是不生效的。

由spawn操作创建的Isolate对象具有控制接口(control port)和控制该对象的能力(capability)。当然， 用
Isolate.Isolate构造方法创建的Isolate对象可以不必带有这些能力。


https://medium.com/dartlang/dart-asynchronous-programming-isolates-and-event-loops-bffc3e296a6a
https://www.jianshu.com/p/342942606325
https://blog.csdn.net/w411207/article/details/80026649

 
 
    