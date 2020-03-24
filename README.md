

# Spring Boot 简介

Spring Boot 是所有基于 Spring 开发的项目的起点。Spring Boot 的设计是为了让你尽可能快的跑起来 Spring 应用程序并且尽可能减少你的配置文件。SpringBoot不是什么新的框架，它只是默认配置了很多框架的使用方式。

 Spring Boot设计目的是用来简化spring应用的初始化环境搭建以及开发过程。 嵌入tomcat服务器,无需部署war文件。
 
Spring Boot并不是spring功能的增强，而是提供了一种快速使用spring的方式。
说明：jdk1.7 使用spring boot 2.0以下版本，  jdk1.8 使用spring boot 2.0以上版本   
## 微服务框架
Spring Boot
Spring Data
Spring Cloud
## 以前使用spring开发web的方式
1:创建web项目，导入相关jar包
2:创建web.xml文件，创建application.xml,springmvc.xml配置文件
3:编写控制器Controller
4:需要部署web项目到服务器 tomcat
 开发起来比较麻烦
## Spring Boot 启动器介绍
1.Spring Boot 启动器其实就是一个jar包集合
2.spring boot将很多的jar包放入到不同的启动器中,   用什么启动器，就注入对应启动的jar包。
3.Spring boot 一共提供了44个启动器。常用的有:

 1. spring-boot-starter-web 
 	支持全栈是的web开发（web项目开发）
 	包括：tomcat和spring springmvc 等jar
 2. spring-boot-starter-jdbc 
	支持spring以jdbc方式操作数据库的jar包集合
 3. spring-boot-starter-redis 
 	 支持redis数据库操作的jar
 4. spring-boot-starter-test
 	 支持常规的测试依赖的jar包括junit,spring-test的jar等
 5. spring-boot-starter-log4j 
 支持log4j日志框架jar
 6. spring-boot-starter-aop
     支持面向切面编程的jar，包括spring-aop,apectj等
## 如何创建一个helloword的SpringBoot项目
 1. 创建 Maven project 项目（IDEA）![在这里插入图片描述](https://img-blog.csdnimg.cn/20200324232123958.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2pva2VyZGoyMzM=,size_16,color_FFFFFF,t_70)
 不用勾选创建骨架，点下一步Next
 2. 根据个人需求配置groupid、Artifact、version
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020032423222449.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2pva2VyZGoyMzM=,size_16,color_FFFFFF,t_70)
3. 选择项目存放目录
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200324232407104.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2pva2VyZGoyMzM=,size_16,color_FFFFFF,t_70)
4. 打开pom.xml引入依赖启动器
	

```java
	<!--引入springboot父项目依赖-->
	<parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.2.4.RELEASE</version>
    </parent>
     <dependencies>
        <!--引入springboot web启动器-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>
```
5. 在/src/main/java目录下创建包 新建springboot的启动类
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200324233419926.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2pva2VyZGoyMzM=,size_16,color_FFFFFF,t_70)
代码如下：

```java
@SpringBootApplication //springboot启动类的注解 判断此项目是springboot项目
public class SpringBootApplicationRun {
    public static void main(String[] args) {
        SpringApplication.run(SpringBootApplicationRun.class,args);
    }
}

```
6. 创建前端控制器controller ，由于是springboot项目，所以不需要配置web.xml、springmvc.xml

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200324233830293.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2pva2VyZGoyMzM=,size_16,color_FFFFFF,t_70)
  代码如下：
  

```java
@RestController  //@RestController= @@Controller + @ResponseBody
public class controller {
    
    @RequestMapping("/helloword")
    public String helloword(){
        return "helloword";
    }
}
```
注意启动类和控制器类的位置：
*启动类和控制器可以位于同一个包下，或启动类位于控制器上一级包下。
但是启动类不能放在控制器的平级包或子包下。
原因：启动器启动时从当前包下以及子包下查找使用的组件。（上级包或不同包的话无法找到）*

7. 运行springboot启动类 浏览器输入 localhost:8080/helloword
点击SpringBootApplicationRun![启动](https://img-blog.csdnimg.cn/20200324234302397.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2pva2VyZGoyMzM=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020032423443223.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2pva2VyZGoyMzM=,size_16,color_FFFFFF,t_70)
