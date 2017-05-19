---
layout: post
title:  "Spring-Quartz"
date:   2017-05-10 16:51:30 +0800

---
* 迁移Spring界面
使用springboot不要将<spring.version>3.1.3.RELEASE</spring.version>放入properties中

```java
package hello;

import org.springframework.boot.*;
import org.springframework.boot.autoconfigure.*;
import org.springframework.stereotype.*;
import org.springframework.web.bind.annotation.*;

@Controller
@EnableAutoConfiguration
public class SampleController {

    @RequestMapping("/")
    @ResponseBody
    String home() {
        return "Hello World!";
    }

    public static void main(String[] args) throws Exception {
        SpringApplication.run(SampleController.class, args);
    }
}
```
* run SampleController.main 启动服务
* http://localhost:8080/访问服务
* 修改上面的文件为application文件

```java

@SpringBootApplication
public class MainClass {
    public static void main(String[] args) throws Exception {
        SpringApplication.run(MainClass.class, args);
    }
}
```
* 新建一个RestController
```java

@RestController
public class GreetingCont{
    @RequestMapping("/greeting")
        public Greet greeting(@RequestParam(value="name", defaultValue="World") String name) {
            return new Greet(counter.incrementAndGet(),
                    String.format(template, name));
        }
}
```

<br>

