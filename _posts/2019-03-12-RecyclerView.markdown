---
layout: post
title:  "2019-03-12-RecyclerView"
date:   2019-03-12 12:11:30 +0800

1. RecyclerView

2. RecyclerView.LayoutManager

    1) ChildHelper
        修改 getChildAt, getChildCount, ignore hidden children
        * Bucket
            记录二进制数据的链表,每一个位代表一个值.
            使用了求二进制数中1的个数算法 Long.bitCount(long i)
    2) 
3. RecyclerView.Adapter

4. RecyclerView.SmoothScroller

   RecyclerView.SmoothScroller.Action 代表一次移动,记录移动距离
        recyclerView.jumpToPositionForSmoothScroller
        recyclerView.mViewFlinger.smoothScrollBy
        
5. RecyclerView.ViewFlinger
    
6. OverScroller
        OverScroller.SplineOverScroller
7. Scroller
    Math.log / Math.hypot
    滑动数值生成封装类,内置滚动插值器,支持普通滚动和fling
    
8. ViewConfiguration
     /**
         * The coefficient of friction applied to flings/scrolls.
         */
     private static final float SCROLL_FRICTION = 0.015f;






