---
layout: post
title:  "2019-12-13-dart const.markdown"
date:   2019-12-13 12:11:30 +0800

1. const修饰成员变量
对象的状态完全可以在编译期间确定，并且完全是不可变的。
# 限制
1) Dart内置数据类型的值(int double bool String List Map等等)进行赋值,而且运行时不可变
2) const构造函数创建的对象
2. const是可传递的
如果你有一个final修饰的成员变量，这个成员变量包含了一个集合，那么这个集合仍然是可变的。
3. 相同的const变量不会在内存中重复创建

4. const修饰构造函数
构造参数必须是final类型

 
 
    