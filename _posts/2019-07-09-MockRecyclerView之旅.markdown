---
layout: post
title:  "2019-07-09-MockRecyclerView之旅.markdown"
date:   2019-07-09 12:11:30 +0800

本文试图以ViewGroup为基础,以RecyclerView源码为原型,用简化的方式
完成RecyclerView的各项功能,项目以上传到github,方便大家以此为基础
研究RecyclerView更深层次知识.

1. 显示
主要流程如下:
1)在RecyclerView的onMeasure中根据需求从Recycler中获取View
2)对子View进行measure和layout操作
(子view的measure和layout不必和父View的对应)
主要涉及类:
1)RecyclerView
提供addView方法,使用onMeasure/onLayout驱动界面展示.
2)Recycler
使用Adapter提供View对象
3)LinearLayoutManager
对View进行布局

2. 滚动

3. 点击

4. View复用

##### 遗留问题
offsetTopAndBottom 和 原来的滚动有什么区别,各有什么优缺点


