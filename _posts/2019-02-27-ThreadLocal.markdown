---
layout: post
title:  "2019-02-27-ThreadLocal"
date:   2019-02-27 12:11:30 +0800


1. ThreadLocal 可以维护线程内共享的变量

ThreadLocal<Boolean> isOfThread = new ThreadLocal<>();

这种值每一个线程单独维护

2. 原理

每个线程 都维护一个 ThreadLocal.ThreadLocalMap
此Map内部是一个Entry数组.Entry保存新定义ThreadLocal即isOfThread和Value的对应(ThreadLocal为弱引用)
Map使用ThreadLocal的hash值映射数组位置,映射后会使用isOfThread(key)进行进一步确认.



