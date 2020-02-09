---
layout: post
title:  "2019-05-20-ScrollView"
date:   2019-05-20 12:11:30 +0800

* 继承自FrameLayout,仅有一个子View

* ScrollView的滚动实现
1) 点击的传递
    onInterceptTouchEvent
    onTouchEvent
        dispatchNestedScroll
        mVelocityTracker
        
2) 滚动内容的实现
    onLayout
        scrollTo(mScrollX, mScrollY);

示例: 
https://github.com/shuhuaxie/nestScroll/blob/master/app/src/main/java/com/example/gs/testnestscroll/myview/CustomScrollView.java





