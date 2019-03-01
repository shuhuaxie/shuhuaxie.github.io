---
layout: post
title:  "2019-02-28-WindowManagerService"
date:   2019-02-28 12:11:30 +0800

1. 功能

管理windowmanager,进行App屏幕展示工作

2. 流程

WindowManagerService运行在SystemServer进程中,负责接收App的绘制请求.
App初始化后打开Activity.Activity会创建Window和WindowManager.
Window承载ViewRootImpl(View树)内容.WindowManager管理Window.
WindowManagerService获取IBinder获取Window内容,将其放置在Surface上,
由SurfaceFlinger组织排列顺序后展示到屏幕上.

* 在markdown中添加流程图 

https://github.com/knsv/mermaid

* 参考文档

https://blog.csdn.net/wf_fln/article/details/78593080

https://blog.csdn.net/freekiteyu/article/details/79408969

https://www.jianshu.com/p/5e2efbaa2949








