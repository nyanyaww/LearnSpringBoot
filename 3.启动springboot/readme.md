# 如何启动springboot项目

对于上一节`2.创建springboot工程`的端口的修改后来我发现可以直接修改`resource\application.properties`文件，只需要在这个文件里面添加`server.port=9090`就可以了，不需要调用繁琐的接口方法。

那么，怎么正确的启动一个springboot项目呢？

我认为最好的办法是这个样子的。

首先文件的目录是

+ com
  + nyanyaww
    + controller
      + TestController.java
    + App.java

在`someController.java`里面我们是这么写的，完全不关心运行的事情，只考虑比如要返回json格式。

```java
@RestController
public class TestController {

    @RequestMapping("/testIndex")
    public String index() {
        return "hello test";
    }
}
```

在`App.java`里面我们使用了`SpringBootApplication`注解

```java
@SpringBootApplication
public class App {
    public static void main(String[] args) {
        SpringApplication.run(App.class, args);
    }
}
```

这种启动方法的重点是要让App.java放在最外层的包，这样就可以扫描到所有的子包了。
