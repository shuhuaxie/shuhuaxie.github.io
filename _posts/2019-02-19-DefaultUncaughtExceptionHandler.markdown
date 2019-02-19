---
layout: post
title:  "2019-02-19-DefaultUncaughtExceptionHandler"
date:   2019-02-09 12:11:30 +0800

---


1. 主线程如果出现空指针异常会直接崩溃,如果带了DefaultUncaughtExceptionHandler会导致App卡死

2. 子线程如果出现异常也会崩溃,如果带了DefaultUncaughtExceptionHandler,只是子线程崩溃关闭.

3. bugly可以和DefaultUncaughtExceptionHandler和平相处,先写自己的,后调用bugly






