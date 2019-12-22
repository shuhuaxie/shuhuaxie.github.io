---
layout: post
title:  "2019-12-10-java Metaspace.markdown"
date:   2019-12-10 12:11:30 +0800

1. java虚拟机内存空间包括
PC程序计数器 本地栈 虚拟机栈 方法区 和 堆.
在HotSpot虚拟机中,METHOD AREA我们可以认为等同于持久代（PermGen）
其中方法区 包含 类信息,静态变量和常量池,即时编译后的代码
常量池包括静态常量池和运行时常量池.在jdk7版本之前归于方法区,之后放到堆中.
在jdk8中,HotSpot整个废弃持久代,使用Metaspace
2. 特点
Metaspace并不在虚拟机内存中而是使用本地内存。避免了持久代内存溢出的问题
Metaspace的初始化内存一般是20M,最大可以到4G.

 
 
    