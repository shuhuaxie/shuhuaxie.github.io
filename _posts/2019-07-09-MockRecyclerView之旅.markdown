---
layout: post
title:  "2019-07-09-MockRecyclerView之旅.markdown"
date:   2019-07-09 12:11:30 +0800

本文试图以ViewGroup为基础,以RecyclerView源码为原型,用简化的方式
完成RecyclerView的各项功能,项目已上传到github:https://github.com/shuhuaxie/MockRecyclerView
,方便大家以此为基础研究RecyclerView更深层次知识.
脑图网址:http://naotu.baidu.com/file/b726e52cf4aad52a0bb32b07999257fc?token=c10091e420401e16
(建议在电脑上阅读)
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
onTouch事件分发
offsetTopAndBottom执行实际的

3. 点击
onInterceptTouchEvent来正确的处理点击和滑动的逻辑

4. View复用
初次显示界面使用onLayoutChildren
滚动界面使用scrollBy,阻止了Layout和measure
添加View到合适的相对位置,去掉不能看到的View,
然后使用offsetTopAndBottom滑动内部的界面


