---
layout: post
title:  "2019-11-26-sqlite和flutter.markdown"
date:   2019-11-26 12:11:30 +0800

1. 使用第三方工具简化执行sql的流程

dependencies:
  sqflite: ^1.1.0

2. 下载sqlite工具进行本地数据模拟
1) 下载两个文件包
2) 将两个文件包解压到一个文件目录下
直接运行sqlite3.exe,进行直接命令的测试
使用命令行运行sqlite3
3. 下载可视化工具sqlite Expert Professianal
创建数据库

4. 关注sqlit和mysql的区别
sqlit功能更少,类型和语法有挺多区别的.

5. 错误的语句,在运行时会直接报错

6. 相关站点: sqlite官网, https://www.sqlite.org/index.html
7. sqlite和mysql的区别
sqlite无需配置,没有权限,没有服务端
sqlite中一个库就是一个文件,拷贝这个文件,即可将其转移到其他地方
sqlite有众多语言支持,可以跨平台使用,也可以用在简单的后台场景,支持多进程读,不支持多线程写.
sqlite对插入数据几乎没有限制,你可以在int列插入String
sqlite插入数据比较慢,批量插入需要走事务来提升速度.
8. sqlite简易使用
https://www.sqlite.org/cli.html
关键词以及内容详解 https://www.sqlite.org/lang.html
常见问题 https://www.sqlite.org/faq.html
9. 快速入门示例
      CREATE TABLE [orderItem] ([id] INTEGER NOT NULL ON CONFLICT REPLACE
      PRIMARY KEY AUTOINCREMENT, [orderId] INTEGER, [goodsId] INTEGER, [num] INTEGER);

      CREATE INDEX [orderId_index] ON [orderItem] ([orderId]);

      insert into [main].[main] values(1, 'ga');
10. 简洁获取语句方法
使用可视化工具创建表,添加表的内容,然后查看导出语句


https://github.com/tekartik/sqflite
https://blog.csdn.net/weixin_42380257/article/details/81360237
https://www.zhihu.com/question/26820442
 
 
    