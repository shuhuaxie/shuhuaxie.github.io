---
layout: post
title:  "2019-12-11-dart extension.markdown"
date:   2019-12-10 12:11:30 +0800

1. 在dart2.6版本加入extension功能
//flutter 1.12.13
2. 类似于静态方法,可以用于var不能用于dynamic,执行效率高

3. extension可以使用泛型

4. 支持 getters, setters, and operators, 间接支持成员变量


2. 测试
 void main() {
   BaseFun().sayName();
   2.sayName();
 }

 extension exNum on num {
   void sayName() {
     print("say..:" + toString());
   }
 }

 extension exFun on BaseFun {
   void sayName() {
     print("say..:" + getName());
   }
 }

 class BaseFun {
   String getName() {
     return "fun_name";
   }
 }

 3. 系统类或者用户自定义类都可以使用extension扩展功能

 4. extension不能带成员变量,只能带静态变量

 5. 引用第三方辅助extension,需要手动import,例如
 import 'package:time/time.dart';

 
 
    