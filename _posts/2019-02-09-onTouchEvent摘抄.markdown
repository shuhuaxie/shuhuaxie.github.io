---
layout: post
title:  "2019-02-09-onTouchEvent摘抄"
date:   2019-02-09 12:11:30 +0800

---

  1、首先执行父控件的dispatchTouchEvent------->父控件的onInterceptTouchEvent，if父控件返回true，触摸事件不会传递给子view，直接调用父控件的onTouchEvent。
  
  
  2、首先执行父控件的dispatchTouchEvent------->父控件的onInterceptTouchEvent，if父控件返回false------>传递给子view的onTouchEvent，if子view返回false.
  ------->事件传递给父控件的onTouchEvent，子控件的onTouchEvent触摸事件消失，后续的move和up不会再执行了
  
  
  3、首先执行父控件的dispatchTouchEvent------->父控件的onInterceptTouchEvent，if父控件返回false------>传递给子view的onTouchEvent，if子view返回true.
  ------->事件不会传递给父控件的onTouchEvent，子控件的onTouchEvent触摸事件还保留了，当move或者up的时候，触摸流程事件如第二条前面的部分，先执行父控件的
  dispatchTouchEvent和onInterceptTouchEvent，然后根据情况再执行子控件的move或者up事件。

       --------------------- 
       作者：ctluo111 
       来源：CSDN 
       原文：https://blog.csdn.net/ctluo111/article/details/41349357 
       版权声明：本文为博主原创文章，转载请附上博文链接！








