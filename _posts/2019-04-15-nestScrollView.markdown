---
layout: post
title:  "2019-04-15 nestScrollView"
date:   2019-04-15 12:11:30 +0800


1. 主要作用嵌套滑动

2. scrollview 的底层 采用 view.scrollTo 和 view.scrollBy进行滚动展示

3. scrollTo的原理是让画布滚动

view.updateDisplayListIfDirty

canvas.translate(-mScrollX, -mScrollY);

