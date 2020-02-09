---
layout: post
title:  "2019-07-31-MockDialogAndPhoneWindow.markdown"
date:   2019-07-31 12:11:30 +0800


本项目以Window为基础,以AlertDialog源码和PhoneWindow为原型,用简化的方式
完成AlertDialog的各项功能,源码已上传到github:https://github.com/shuhuaxie/MockDialogAndPhoneWindow.
脑图网址:http://naotu.baidu.com/file/ef8c63e1523ba6fd81af3eef2fc7497a?token=92a6474c6631b4ee (建议在电脑上阅读)

###功能概要和实现流程

1. 显示

    * WindowManager.addView添加需要展示的界面
    
    * Dialog在show时,才将生成Layout添加到DecorView中,然后打包到WindowManager中

2. 返回键

    * DecorView.dispatchKeyEvent事件分发
    
    * WindowManager.removeViewImmediate执行实际的关闭操作

3. 修改UI

    PhoneWindow.generateLayout设置添加到WindowManager的参数,使界面居中背景半透明

4. 点击边缘关闭

    DecorView.dispatchTouchEvent
5. 其他

    事件分发的基本流程是
    
    WindowManager->DecorView->Activity/Dialog->ContentView