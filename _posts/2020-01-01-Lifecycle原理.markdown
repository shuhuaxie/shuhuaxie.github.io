---
layout: post
title:  "2020-01-01-Lifecycle原理.markdown"
date:   2020-01-01 12:11:30 +0800

1. Activity 如何建立lifeCycle
系统自建
2. View如何建立lifeCycle
需要手动设置

LiveData 监听者需要带生命周期,可以根据生命周期去掉观察者关联
ViewModel 存储数据,通过ViewModelProviders获取,带有简单的生命周期,
其生命周期不是很重要,同时需要注意和View,Activity等解耦
ViewDataBinding 需要设置生命周期和连接Data对象,在生命周期的onStart
进行Bind操作,为xml中的data设值,为view中的对象传值


    
    
