---
layout: post
title:  "2019-01-24-FastLayout学习"
date:   2019-01-24 12:11:30 +0800

---

* FastLayout https://github.com/FabianTerhorst/FastLayout

是一个帮助你快速初始化xml文件的工具.

* 原理

从xml中获取ViewGroup对象并缓存,以空间换时间,加速下一次加载xml的速度.

1) 从xml中获取布局信息,并生成java文件存入cache中

2) 当用户使用时,从cache中获取缓存的clone对象,进行使用

* 缺点

1) 在android中从xml中生成java文件,花费时间不长;layout时间没有省略

2) 生成的java对象为浅复制对象,跟直接使用同一个对象区别不大.没有实际应用价值









