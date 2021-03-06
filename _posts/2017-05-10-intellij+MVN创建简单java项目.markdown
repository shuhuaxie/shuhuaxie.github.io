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
package com.test;

public class hello {
public static void main(String... args){
              System.out.println("xx");
    }
}
```

* 现在可以在IDE内run hello.main了，同时可以进行mvn compile和package任务了
* 新增mvn内容可以使用java -jar运行jar包

```xml
    <build>
            <plugins>
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-shade-plugin</artifactId>
                    <version>1.2.1</version>
                    <executions>
                        <execution>
                            <phase>package</phase>
                            <goals>
                                <goal>shade</goal>
                            </goals>
                            <configuration>
                                <transformers>
                                    <transformer implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
                                        <mainClass>com.test.hello</mainClass>
                                    </transformer>
                                </transformers>
                            </configuration>
                        </execution>
                    </executions>
                </plugin>
            </plugins>
        </build>
    
```
* mvn dependency:tree 查看jar包依赖

* mvn 包损坏,点击 右边的 Maven Projects然后点击 左上角的reimport 按钮(刷新)

* 出现String过长问题,将Java Compiler改为Eclipse;出现注解无法编译的重新改回为javac;

* intelliJ可以恢复误删除的代码, VCS->History->Show History
<br>

* 依赖注解的项目设置
Intellij idea开发的话需要安装Lombok plugin，
同时设置 Setting -> Compiler -> Annotation Processors -> Enable annotation processing勾选。

