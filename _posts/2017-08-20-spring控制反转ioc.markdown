---
layout: post
title:  "spring控制反转ioc"
date:   2017-08-20 16:51:30 +0800

---
* 读取xml、properties、yaml
* 根据配置文件填充内置对象,并放到mapper容器里,供系统使用
* 加载spring内部jar和第三方jar，根据配置文件修改其初始化值
* 加载用户代码,并根据注解将内置对象注入用户代码。

-- 反射和注解的深入学习

-- 惯例做法,每一个第三方jar有一个property模板文件方便在spring中通过配置和映射为一个新的用户自定义模板


内置第三方jar的配置方式
1.Tomcat
1)设置property
2)通过@Configuration方式 @Bean 函数 读取配置文件返回Tomcat实例.
3)更新tomcat配置文件,启动tomcat
2.velocity
1)设置property
2)设置网页相关
3.elastic-job-lite
1)spring.schemas 设置自定义xml文件格式
2)spring.handlers 设置xml处理
3)启动


大java执行流程
代码->编译->运行
代码准确性提示,预编译,注解,打jar包,jar包meta-info解析,不同jar包内容逐个启动,属性设置

spring默认接受的文件
1)mete-info
增加自定义xml格式和响应的处理:
spring.handers  spring.schemas 示例elastic-job-lite-spring-2.0.4
增加spring初始化流程监听(获取Environment属性值,启动jar)
spring.factories 示例:spring-boot-autoconfigure-1.4.3.RELEASE.jar
管理项目依赖和导入
spring.provides  /spring-boot-starter-1.4.3.RELEASE.jar

抓获野生模板引擎
freemarker thymeleaf beetl(听说很差)
架构需要良好的错误提示信息
