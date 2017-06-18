## 说明

1. 完美运行
2. 结构清晰明了。

## 运行示例

欢迎页面：http://localhost:8080/
页面展示：http://localhost:8080/user/showUser?id=1
JSON：http://localhost:8080/user/test?id=1

## 参考

SSM框架——详细整合教程（Spring+SpringMVC+MyBatis）：http://blog.csdn.net/gebitan505/article/details/44455235/

## 备注

```
Spring是一个轻量级的控制反转（IoC）和面向切面（AOP）的容器框架

Spring MVC属于SpringFrameWork的后续产品，已经融合在Spring Web Flow里面。Spring MVC 分离了控制器、模型对象、分派器以及处理程序对象的角色，这种分离让它们更容易进行定制。

MyBatis 本是apache的一个开源项目iBatis, 2010年这个项目由apache software foundation 迁移到了google code，并且改名为MyBatis 。MyBatis是一个基于Java的持久层框架。iBATIS提供的持久层框架包括SQL Maps和Data Access Objects（DAO）MyBatis 消除了几乎所有的JDBC代码和参数的手工设置以及结果集的检索。MyBatis 使用简单的 XML或注解用于配置和原始映射，将接口和 Java 的POJOs（Plain Old Java Objects，普通的 Java对象）映射成数据库中的记录。

web.xml
context-param mybatis，spring加载
filter 配置utf8,过滤监听
servlet SpringMVC配置文件 入口映射
其他，session超时

spring-mybatis.xml
数据库相关
context:component-scan 自动扫描包下面所有文件
bean PropertyPlaceholderConfigurer  classpath:jdbc.properties引入数据库连接字符串配置文件
bean  dataSource这里也要写数据库连接字符串，配置连接池BasicDataSource
bean，sqlSessionFactory，spring和MyBatis完美整合，关联dataSource，连接mapperLocations（xml的mapper文件路径用/）；MapperScannerConfigurer配置basePackage，对应dao路径；transactionManager事务管理，需要ref dataSource

spring-mvc.xml
上下文相关
context:component-scan 自动扫描该包控制类
bean  mappingJacksonHttpMessageConverter 避免IE执行AJAX时，返回JSON出现下载文件；自动注解AnnotationMethodHandlerAdapter；定义跳转的文件的前后缀InternalResourceViewResolver

mybatis
insert <trim prefix="(" suffix=")" suffixOverrides="," >挺好，有啥插啥，不过写的也多；

log4j配置
1. 引入jar，配置log4j.properties
2. 需要log的java中写	private static Logger logger = Logger.getLogger(TestMyBatis.class) 即可
```