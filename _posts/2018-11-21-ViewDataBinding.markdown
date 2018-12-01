---
layout: post
title:  "2018-11-21-ViewDataBinding"
date:   2018-11-21 12:11:30 +0800

---

* ViewDataBinding使用
1.gradle文件中
 android{
 //增加
 dataBinding {
         enabled = true
     }
     }
2.xml文件增加layout主标签
3.build
4.使用/build/generated/data_binding_base_class_source_out/debug/dataBindingGenBaseClassesDebug/out/
中生成的文件
var bind: ActivityTestBinding = ActivityTestBinding.inflate(layoutInflater)
bind.setLifecycleOwner(this)
setContentView(bind.root)
* 作用
去掉了findViewById，所有的View对象可以使用ViewDataBinding直接获取

* 加入viewmodel更加灵活的控制View的交互（内容显示和点击事件）

* 参考资料：




