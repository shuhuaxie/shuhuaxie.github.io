---
layout: post
title:  "2019-07-29-在android中执行java程序.markdown"
date:   2019-07-29 12:11:30 +0800

1. 使用javac或者ecj 编译java代码

javac -source 1.6 -target 1.6  test_main.java

2. 使用dx生成可执行jar包

E:\SDK\build-tools\22.0.1\dx.bat  --dex --output=test.jar com/test_main.class

3. 使用dalvikvm运行jar程序
 dalvikvm -cp /data/local/share/test.jar com.test_main
 
DONE!!!
另:推荐一个连接本地命令行的神器:Termux

参考文档
https://blog.csdn.net/u013320868/article/details/51324538
https://blog.csdn.net/csm_qz/article/details/50444933


