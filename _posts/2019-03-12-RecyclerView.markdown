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

9. mRecyclerView.mViewInfoStore
    重要layout信息
    ViewInfoStore 
        mLayoutHolderMap
        mOldChangedHolders
        
10. RecyclerViewDataObserver/AdapterDataObserver
    adapter数据变化监听.
    
11. AdapterHelper

12. ScrollingView

13. Recycler 和 RecycledViewPool

addViewInt 
证明:
// view 在 childViews 列表中 (每次layout会带上它)
// view 仅仅在缓存中 比如 ScrapViews(缺少View 找他要)


1) 初步建立显示界面
dispatchLayoutStep2()
public void onLayoutChildren
fill(RecyclerView.Recycler recycler, LayoutState layoutState,
    循环语句while ((layoutState.mInfinite || remainingSpace > 0) && layoutState.hasMore(state)) {
layoutChunk
    子View layout:this.layoutDecoratedWithMargins(view, left, top, right, bottom);
           child.layout
layoutState.next(recycler);
    添加到布局中 addView
recycler.getViewForPosition(mCurrentPosition);
tryGetViewHolderForPositionByDeadline  
    创建 holder = mAdapter.createViewHolder(RecyclerView.this, type);
    绑定 tryBindViewHolderByDeadline(holder, offsetPosition, position, deadlineNs);

删除View
removeAndRecycleViewAt
  this.removeViewAt(index);

mAttachedScrap

mChangedScrap

mCachedViews

mUnmodifiableAttachedScrap

mRecyclerPool

2) View的缓存,复用和回收

onLayoutChildren

detachAndScrapAttachedViews



//fill 在简单滚动(View内容不变)会不会调用
// 简单滚动 事件传递(scrollBy)



