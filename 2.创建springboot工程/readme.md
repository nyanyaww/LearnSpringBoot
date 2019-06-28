# 创建springboot工程

## ~~~通过maven工程进行创建~~~

~~~我使用了idea作为我java的集成编译环境，jdk是1.8的。~~~

~~~为了加快maven的构建需要修改了setting.xml的配置文件。~~~

```xml
<mirrors>
  <!-- mirror
   | Specifies a repository mirror site to use instead of a given repository. The repository that
   | this mirror serves has an ID that matches the mirrorOf element of this mirror. IDs are used
   | for inheritance and direct lookup purposes, and must be unique across the set of mirrors.
   |
  <mirror>
    <id>mirrorId</id>
    <mirrorOf>repositoryId</mirrorOf>
    <name>Human Readable Name for this Mirror.</name>
    <url>http://my.repository.com/repo/path</url>
  </mirror>
   -->
   <mirror>
    <id>alimaven</id>
    <name>aliyun maven</name>
    <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
    <mirrorOf>central</mirrorOf>
  </mirror>
</mirrors>
```

## 通过spring initilizr创建

这是使用了idea来创建spring-boot项目，相当简单，具体创建的过程我就不写了。

### 1. xml文件

创建之后pom.xml是用来导入依赖jar包的。比较重要的下面这两段配置文件。

```xml
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.1.6.RELEASE</version>
    <relativePath/>
</parent>
```

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>
</dependencies>
```

### 2. java文件

```java
package com.nyanyaww.springboot2helloworld;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class Springboot2HelloworldApplication {

    public static void main(String[] args) {
        SpringApplication.run(Springboot2HelloworldApplication.class, args);
    }
}
```

实际上这些文件都是在创建的时候都自己配置好了的，本身是不需要我们去修改的。

## 调试结果

```cmd
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::        (v2.1.6.RELEASE)

2019-06-28 20:59:53.858  INFO 3536 --- [           main] c.n.s.Springboot2HelloworldApplication   : Starting Springboot2HelloworldApplication on DESKTOP-JHH68H7 with PID 3536 (started by lcs in G:\source code\java\springboot2-helloworld)
2019-06-28 20:59:53.861  INFO 3536 --- [           main] c.n.s.Springboot2HelloworldApplication   : No active profile set, falling back to default profiles: default
2019-06-28 20:59:54.710  INFO 3536 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port(s): 8080 (http)
2019-06-28 20:59:54.749  INFO 3536 --- [           main] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2019-06-28 20:59:54.749  INFO 3536 --- [           main] org.apache.catalina.core.StandardEngine  : Starting Servlet engine: [Apache Tomcat/9.0.21]
2019-06-28 20:59:54.831  INFO 3536 --- [           main] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2019-06-28 20:59:54.831  INFO 3536 --- [           main] o.s.web.context.ContextLoader            : Root WebApplicationContext: initialization completed in 923 ms
2019-06-28 20:59:54.991  INFO 3536 --- [           main] o.s.s.concurrent.ThreadPoolTaskExecutor  : Initializing ExecutorService 'applicationTaskExecutor'
2019-06-28 20:59:55.121 ERROR 3536 --- [           main] org.apache.catalina.util.LifecycleBase   : Failed to start component [Connector[HTTP/1.1-8080]]

org.apache.catalina.LifecycleException: Protocol handler start failed
at org.apache.catalina.connector.Connector.startInternal(Connector.java:1008) ~[tomcat-embed-core-9.0.21.jar:9.0.21]
at org.apache.catalina.util.LifecycleBase.start(LifecycleBase.java:183) ~[tomcat-embed-core-9.0.21.jar:9.0.21]
at org.apache.catalina.core.StandardService.addConnector(StandardService.java:227) [tomcat-embed-core-9.0.21.jar:9.0.21]
	at org.springframework.boot.web.embedded.tomcat.TomcatWebServer.addPreviouslyRemovedConnectors(TomcatWebServer.java:263) [spring-boot-2.1.6.RELEASE.jar:2.1.6.RELEASE]
	at org.springframework.boot.web.embedded.tomcat.TomcatWebServer.start(TomcatWebServer.java:195) [spring-boot-2.1.6.RELEASE.jar:2.1.6.RELEASE]
	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.startWebServer(ServletWebServerApplicationContext.java:296) [spring-boot-2.1.6.RELEASE.jar:2.1.6.RELEASE]
	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.finishRefresh(ServletWebServerApplicationContext.java:162) [spring-boot-2.1.6.RELEASE.jar:2.1.6.RELEASE]
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:552) [spring-context-5.1.8.RELEASE.jar:5.1.8.RELEASE]
	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:140) [spring-boot-2.1.6.RELEASE.jar:2.1.6.RELEASE]
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:742) [spring-boot-2.1.6.RELEASE.jar:2.1.6.RELEASE]
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:389) [spring-boot-2.1.6.RELEASE.jar:2.1.6.RELEASE]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:311) [spring-boot-2.1.6.RELEASE.jar:2.1.6.RELEASE]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1213) [spring-boot-2.1.6.RELEASE.jar:2.1.6.RELEASE]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1202) [spring-boot-2.1.6.RELEASE.jar:2.1.6.RELEASE]
	at com.nyanyaww.springboot2helloworld.Springboot2HelloworldApplication.main(Springboot2HelloworldApplication.java:10) [classes/:na]
Caused by: java.net.BindException: Address already in use: bind
	at sun.nio.ch.Net.bind0(Native Method) ~[na:1.8.0_144]
	at sun.nio.ch.Net.bind(Net.java:433) ~[na:1.8.0_144]
	at sun.nio.ch.Net.bind(Net.java:425) ~[na:1.8.0_144]
	at sun.nio.ch.ServerSocketChannelImpl.bind(ServerSocketChannelImpl.java:223) ~[na:1.8.0_144]
	at sun.nio.ch.ServerSocketAdaptor.bind(ServerSocketAdaptor.java:74) ~[na:1.8.0_144]
	at org.apache.tomcat.util.net.NioEndpoint.initServerSocket(NioEndpoint.java:230) ~[tomcat-embed-core-9.0.21.jar:9.0.21]
	at org.apache.tomcat.util.net.NioEndpoint.bind(NioEndpoint.java:213) ~[tomcat-embed-core-9.0.21.jar:9.0.21]
	at org.apache.tomcat.util.net.AbstractEndpoint.bindWithCleanup(AbstractEndpoint.java:1124) ~[tomcat-embed-core-9.0.21.jar:9.0.21]
at org.apache.tomcat.util.net.AbstractEndpoint.start(AbstractEndpoint.java:1210) ~[tomcat-embed-core-9.0.21.jar:9.0.21]
	at org.apache.coyote.AbstractProtocol.start(AbstractProtocol.java:585) ~[tomcat-embed-core-9.0.21.jar:9.0.21]
	at org.apache.catalina.connector.Connector.startInternal(Connector.java:1005) ~[tomcat-embed-core-9.0.21.jar:9.0.21]
	... 14 common frames omitted

2019-06-28 20:59:55.124  INFO 3536 --- [           main] o.apache.catalina.core.StandardService   : Stopping service [Tomcat]
2019-06-28 20:59:55.133  INFO 3536 --- [           main] ConditionEvaluationReportLoggingListener : 

Error starting ApplicationContext. To display the conditions report re-run your application with 'debug' enabled.
2019-06-28 20:59:55.135 ERROR 3536 --- [           main] o.s.b.d.LoggingFailureAnalysisReporter   : 

***************************
APPLICATION FAILED TO START
***************************

Description:

The Tomcat connector configured to listen on port 8080 failed to start. The port may already be in use or the connector may be misconfigured.

Action:

Verify the connector's configuration, identify and stop any process that's listening on port 8080, or configure this application to listen on another port.

2019-06-28 20:59:55.137  INFO 3536 --- [           main] o.s.s.concurrent.ThreadPoolTaskExecutor  : Shutting down ExecutorService 'applicationTaskExecutor'

Process finished with exit code 1
```

非常奇怪，我们遇到了这个报错，事实上我们分析一下，是端口号被占用了。

```cmd
2019-06-28 20:59:55.121 ERROR 3536 --- [           main] org.apache.catalina.util.LifecycleBase   : Failed to start component [Connector[HTTP/1.1-8080]]
```

8080端口被占用了，我们改成9090就好了。

调整代码如下

```java
package com.nyanyaww.springboot2helloworld;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.boot.web.server.WebServerFactoryCustomizer;
import org.springframework.boot.web.servlet.server.ConfigurableServletWebServerFactory;

@SpringBootApplication
public class Springboot2HelloworldApplication implements WebServerFactoryCustomizer<ConfigurableServletWebServerFactory> {

    @Override
    public void customize(ConfigurableServletWebServerFactory factory) {
        factory.setPort(9090);
    }
    public static void main(String[] args) {
        SpringApplication.run(Springboot2HelloworldApplication.class, args);
    }
}
```

具体是调用了`WebServerFactoryCustomizer<ConfigurableServletWebServerFactory>`接口，重写`customize(ConfigurableServletWebServerFactory factory)`方法，修改端口号就可以了。
