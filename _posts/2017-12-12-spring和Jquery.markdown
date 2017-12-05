---
layout: post
title:  "2017-12-12-spring和Jquery"
date:   2017-12-12 16:51:30 +0800

---
* 当Spring不开启任何设置时,Jquery不能通过CORS的方式请求Spring服务.
  Spring使用@CrossOrigin 配置在请求方法上,可以允许Jquery请求具体方法
  Spring设置全局WebMvcConfigurer可以让全部服务允许Jquery请求.
  https://spring.io/blog/2015/06/08/cors-support-in-spring-framework

 * .find() .end() .siblings() .removeClass() .addClass()函数
 .find():查找出所有符合条件的元素.
 .end(): 前一个对象重置为原始对象 ('ul.first')
 .siblings():该元素的同胞元素(不包含自己)
 $('li.third-item').siblings().css('background-color', 'green'); // 其他平级的li
 <script>$('ul.first').find('.bar').css('background-color', 'red')
       .end().find('.foo').css('background-color', 'green');</script>

       $(this).siblings().removeClass()//兄弟们请变蓝
                       .end().addClass("cur");//换我来变白色
* build.js 中的module 相当于一个要处理的js文件

* 在引用js文件时,要考虑引用顺序
````
<script type="text/javascript" src="../../lib/forala_editor/js/languages/zh_cn.js"></script>
````
上面这段代码要放到其他js之下,否则执行出错.


