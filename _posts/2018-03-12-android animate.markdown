---
layout: post
title:  "2017-03-12-animate"
date:   2017-03-12 12:11:30 +0800

---

Activity启动
1)主要由ActivityThread类实现
通过静态main方法,初始化Looper和handler,创建ActivityThread实例.
实例化的ActivityThread会通过handler来中转消息,实现activity的launch create stop resume等操作.
在launch过程中调用activity 的 attach方法,为activity增加window(PhoneWindow)和decorView,实现activity的显示.
在ActivityThread 的handleResumeActivity中 window进行了addView操作,在此为decorView设置父view
window

View onDraw

hardwareAcceleratedCanvas
①每一个窗口对应一个ViewRootImpl，每个ViewRootImpl都对应唯一的一个ThreadedRenderer、一个RootRenderNode、一个RenderProxy对象。
②一个RenderProxy对象又对应一个CanvasContext对象。
③一个CanvasContext又对应一个OpenGLRenderer对象。
④一个拥有窗口的进程，必然有且只有一个RenderThread子线程。

2) animation 主要在draw方法中执行. ObjectAnimator 主要通过handler定时修改View属性,从外部修改.



test commit


