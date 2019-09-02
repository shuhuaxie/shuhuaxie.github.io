---
layout: post
title:  "2019-07-08-MockRecyclerView之旅.markdown"
date:   2019-07-08 12:11:30 +0800

最近写了一个项目试图以ViewGroup为基础,以RecyclerView源码为原型,用简化的方式
完成RecyclerView的各项功能,源码已上传到github:https://github.com/shuhuaxie/MockRecyclerView,方便大家以此为基础研究RecyclerView更深层次知识.
方便大家以此为基础研究RecyclerView更深层次知识.
脑图网址:http://naotu.baidu.com/file/b726e52cf4aad52a0bb32b07999257fc?token=c10091e420401e16
(建议在电脑上阅读)
1. 显示

    描述: 在onLayout中从缓存中获取ViewHolder或者通过用户的onCreateViewHolder
新建ViewHolder,在bindView后测量View的大小并add到RecyclerView中,循环加载填充满
RecyclerView或者取出全部Item.
    其中AttachedScrap主要应对重复的layout,在界面不变时仅执行scrapView和unscrapView方法

    主要流程如下:

* 在RecyclerView的onMeasure中根据需求从Recycler中获取View

* 对子View进行measure和layout操作(子view的measure和layout不必和父View的对应)

    主要涉及类:

* RecyclerView

    提供addView方法,使用onMeasure/onLayout驱动界面展示.
* Recycler

    使用Adapter提供View对象
* LinearLayoutManager

    对View进行布局


2. 滚动

    描述: 通过onTouch事件获取滚动距离,根据滚动距离按照比例进行子View的移动
子View通过offsetTopAndBottom实现,是轻量级界面操作,不触发scheduleTraverse

    主要流程如下:
    onTouch事件分发
    
    offsetTopAndBottom执行实际的

3. 点击

    描述: 默认子view带点击事件,RecyclerView无法滚动,因为onTouchEvent的分发
    是单责任链模式.解决办法是onDown事件需要父View和子View同时接受.
    这时会发生滚动后依然触发子View点击事件.
    解决办法是在确定父View处理时,拦截onUp事件否则放行onUp事件.
onInterceptTouchEvent来正确的处理点击和滑动的逻辑

4. View复用

    描述: 屏蔽了onLayout调用,通过fill的动态布局填充缺失的View,然后将未添加到界面的View
进行remove回收.新加入的View根据老的状态(子View的top属性)进行动态布局,然后统一进行增量的移动.
 
5. notifyDataSetChanged

    描述: 将界面上的View标记invalid,在layout时,先使用AnchorInfo标记第一个可见View
    的position和偏移量,然后根据这些值重新进行layout操作,所有的view都会根据标记位重新绑定.
    


