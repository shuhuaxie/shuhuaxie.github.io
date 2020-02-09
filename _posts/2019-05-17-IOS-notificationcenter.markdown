---
layout: post
title:  "2019-05-17-IOS-notificationcenter"
date:   2019-05-17 12:11:30 +0800
```
NotificationCenter.default.addObserver(self, selector: #selector(notifyUpdateTodayData),
                                       name: Notification.Name.notifyUpdateTodayData, object: nil)
  ```
* API 网址
https://developer.apple.com/documentation/foundation/nsnotificationcenter/1415360-addobserver?language=objc

self 代表当前对象,#selector 设置回调函数,name 通过
extension Notification.Name { 设置的固定成员变量,用来标记Message类型.

* NotificationCenter 是App内置类,可以用来发送广播或者发送消息,在低版本需要remove

* GCD 多核并发
iOS中处理多核并发的技术有两种分别是：`Grand Central Dispatch`（以下简称`GCD`）和`NSOperationQueue`框架。iOS开发的老司机们在程序开发中处理多个任务同时执行的时候，一定都会使用到这两个框架，而且GCD依靠它简洁的语法和对block的运用一直很受大家的青睐。

```
DispatchQueue.main.asyncAfter(deadline: .now() + 60) {
```
* 条件编译
https://blog.csdn.net/oiken/article/details/62237432

* pushViewController
有NavigationController导航栏的话，使用[self.navigationController  pushViewController:animated:];和[self.navigationController popViewControllerAnimated:];来进行视图切换。pushViewController是进入到下一个视图，popViewController是返回到上一视图。
没有NavigationController导航栏的话，使用[self presentViewController:animated:completion:];和[self dismissViewControllerAnimated:completion:];具体是使用可以从文档中详细了解。

* ViewController 类比于Activity,可以自己初始化又类似于Fragment.

```
numbers.map({
    (number: Int) -> Int in
    let result = 3 * number
    return result
})

numbers.map({
    (nType) in
})
```

引用:
https://www.jianshu.com/p/737233208d40




