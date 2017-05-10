---
layout: post
title:  "intellij+MVN创建简单java项目"
date:   2017-05-10 16:51:30 +0800

---
* 使用intellij创建空项目
* 创建mvn model
* 修改iml文件
```xml
    <content url="file://$MODULE_DIR$" >
        <sourceFolder url="file://$MODULE_DIR$/src/main/java" isTestSource="false" />
        <sourceFolder url="file://$MODULE_DIR$/src/main/resources" type="java-resource" />
        <sourceFolder url="file://$MODULE_DIR$/src/test/java" isTestSource="true" />
        <excludeFolder url="file://$MODULE_DIR$/target" />
    </content>
    
```
* 新建文件夹和文件com.test.hello.java
* 新增代码
```java
public static void main(String... args){
              System.out.println("xx");
    }

```
<br>

