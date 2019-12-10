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

https://medium.com/dartlang/dart-asynchronous-programming-isolates-and-event-loops-bffc3e296a6a

 
 
    