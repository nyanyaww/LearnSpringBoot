# 什么是SpringBoot

## 概述

SpringBoot是一个快速开发框架，用于整合第三方常用框架的，相比传统框架需要编写许多的xml相比。SpringBoot使用了注解化的方式，简化xml的配置，内嵌http服务器（TomCat、Jetty）。使用Maven继承方式进行项目的配置，使用java命令来运行项目（传统是打成war包，启动web.xml）。注意，SpringBoot没有web.xml，java -jar xxx.main运行。

## SpringBoot和SpringCloud

SpringCloud是目前完整的微服务框架，更多是实现通讯的。SpringBoot在于可以整合第三方常用框架。

## SpringBoot和SpringMVC

SpringMVC是SpringBoot Web组件，但是却不需要写springmvc.xml。我觉得关系应该是SpringBoot＞SpringMVC。
