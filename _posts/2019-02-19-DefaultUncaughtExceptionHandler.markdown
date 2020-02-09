---
layout: post
title:  "2019-02-19-DefaultUncaughtExceptionHandler"
date:   2019-02-19 12:11:30 +0800

---


1. android主/子线程如果出现空指针异常会直接崩溃,

android的RuntimeInit中设置了Handler,此handler会捕捉所有线程异常,弹出错误提示,关闭Application

2. 在android中如果带了DefaultUncaughtExceptionHandler,只是子线程崩溃关闭.

android线程由于出现异常且没有被捕捉,走到Handler,导致Looper被破坏,不能响应点击事件出现ANR.

3. bugly可以和DefaultUncaughtExceptionHandler和平相处,先写自己的,后调用bugly,bugly会在处理

异常后,加载原来的Handler


延伸:
* 语言层面异常和虚拟机的关系

* 异常和线程/进程间的关系

* kotlin异常


