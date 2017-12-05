---
layout: post
title:  "2017-12-12-spring和Jquery"
date:   2017-12-12 16:51:30 +0800

---
* 当Spring不开启任何设置时,Jquery不能通过CORS的方式请求Spring服务.
  Spring使用@CrossOrigin 配置在请求方法上,可以允许Jquery请求具体方法
  Spring设置全局WebMvcConfigurer可以让全部服务允许Jquery请求.
  https://spring.io/blog/2015/06/08/cors-support-in-spring-framework

* 在引用js文件时,要考虑引用顺序
````
<script type="text/javascript" src="../../lib/forala_editor/js/languages/zh_cn.js"></script>
````
上面这段代码要放到其他js之下,否则执行出错.

