---
layout: post
title:  "2019-02-24-SparseArray"
date:   2019-02-24 12:11:30 +0800


1. 简介

此为Android平台特有对象
当HashMap的key为int时,可以用SparseArray来替换HashMap

2. 原理

内部是一个存储映射的数组,一个存储真实数据的数组
查找:通过二分查找的方法在存址数组寻找相同的key值,找到后到存值数组取真实数据
插入:查找到后直接替换,否则需要对数组进行耗时的迁移赋值操作.// 迁移System.arraycopy

[1,6,8]
["1","6","8"]

3. 和HashMap差异
HashMap 内部由散列数组和链表组成,查找和存储效率高,但是占用空间比SparseArray大
因为在数组数据比较少的时候,性能影响不大,推荐使用SparseArray,减少内存占用

4. RecyclerView使用了SparseArray

参考:
https://www.cnblogs.com/RGogoing/p/5095168.html

