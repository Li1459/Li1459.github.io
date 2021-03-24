## IoC(控制反转)

是面向对象编程中一种设计原则，可以用来减低计数器代码之间的耦合度。其中最常见的方式叫做依赖注入（Dependency Injection，简称DI），还有一种方式叫“依赖查找”（Dependency Lookup）。通过控制反转，对象在被创建的时候，有一个调控系统内所有对象的外界实体将其所依赖的对象的引用传递给它。也可以说依赖被注入到对象中。

## DI（依赖注入）

是指程序运行过程中，如果需要调用另一个对象协助时，无须在代码中创建被调用者，而是依赖于外部注入。Spring的依赖注入对调用者和被调用者机会没有任何要求，完全支持对POJP之间依赖关系的管理。

依赖注入分为设值注入和构造注入。

当某个角色(可能是一个Java实例，调用者)需要另一个角色(另一个Java实例，被调用者)的协助时，在传统的程序设计过程中，通常由调用者来创建被调用者的实例。但在Spring里，创建被调用者的工作不再由调用者来完成，因此称为控制反转;创建被调用者 实例的工作通常由Spring容器来完成，然后注入调用者，因此也称为依赖注入。

## AOP（面向切面编程）

在软件业，AOP为Aspect Oriented Programming的缩写，意为：面向切面编程，通过预编译方式和运行期动态代理实现程序功能的统一维护的一种技术。AOP是OOP的延续，是软件开发中的一个热点，也是Spring框架中的一个重要内容，是函数式编程的一种衍生范型。利用AOP可以对业务逻辑的各个部分进行隔离，从而使得业务逻辑各部分之间的耦合度降低，提高程序的可重用性，同时提高了开发的效率。


## Spring

Spring是一个开源框架。

目的：它是为了解决企业应用开发的复杂性而创建的。

Spring的用途不仅仅限于服务器端的开发，从简单性、可测试性和松耦合的角度而言，任何Java应用都可以从Spring中受益。

## SpringMVC

是一种web框架。

## SpringMVC运行流程

![img](https://images2015.cnblogs.com/blog/249993/201612/249993-20161212142542042-2117679195.jpg)1、 用户发送请求至前端控制器DispatcherServlet。

2、 DispatcherServlet收到请求调用HandlerMapping处理器映射器。

3、 处理器映射器找到具体的处理器(可以根据xml配置、注解进行查找)，生成处理器对象及处理器拦截器(如果有则生成)一并返回给DispatcherServlet。

4、 DispatcherServlet调用HandlerAdapter处理器适配器。

5、 HandlerAdapter经过适配调用具体的处理器(Controller，也叫后端控制器)。

6、 Controller执行完成返回ModelAndView。

7、 HandlerAdapter将controller执行结果ModelAndView返回给DispatcherServlet。

8、 DispatcherServlet将ModelAndView传给ViewReslover视图解析器。

9、 ViewReslover解析后返回具体View。

10、DispatcherServlet根据View进行渲染视图（即将模型数据填充至视图中）。

11、 DispatcherServlet响应用户。

## MyBatis

### 1.什么是mybatis
​    1.mybatis是一个半ORM对象关系映射框架，内部封装了JDBC，开发时只需要关注sql本身，避免了加载驱动，创建连接，创建statement等过程，程序员直接编写原生的sql语句，可以严格控制sql的性能，拥有比较好的灵活性
​    2.mybatis可以使用xml或者注解来配置和映射原生信息，将实体映射成数据库中的记录，避免了所有jdbc代码和手动设置参数以及获取结果集

### 2.mybatis的优点
​    1.基于sql语句编程，相当灵活，不会对应用程序和数据库造成任何影响，sql写在xml中，减少了与程序中代码的耦合，便于统一管理，提供xml标签，支持编写动态sql，可重用
​    2.与jdbc相比，减少了50%以上的代码量，不需要手动开关连接
​    3.很好的与各种数据库兼容（因为mybatis封装的是jdbc，所以jdbc支持的数据库mybtis就支持）
​    4.很好的与spring兼容

### 3.mybatis的缺点
​    1.sql语句编写的工作量大，尤其是当字段多、关联表多时
​    2.sql语句依赖于数据库，导致移植性比较差，不能随意更换数据库

### 4.mybatis适用场合
​    1.mybatis专注于sql本身，是一个灵活的dao层解决方案
​    2.对性能的要求较高，或者需求比较多变的项目是不错的选择

### 5.mybatis和Hibernate的区别
​    1.mybatis不是一个完全的ORM框架，因为需要自己写sql
​    2.mybatis编写原生态的sql，灵活度高，适合对关系数据模型要求不高的软件开发，因为这类软件需求频繁，能迅速跟着改变。但是mybatis因为灵活度高无法做到数据库无关性，如果需要实现支持多种数据库的软件，则需要定义多套sql映射文件，工作量大。

## 6.#{}和${}的区别
​    1.#{}时预编译处理，${}是字符串替换。预编译是提前对sql语句进行编译，而其后注入的参数不会再进行sql编译。
​    2.mybatis在处理#{}时，会将sql中的#{}替换为？号，调用preparedStatement的set方法来赋值；在处理${}时就是将它替换为变量的值
​    3.#{}能有效防止sql注入，提高系统的安全性

## 7.当实体类中的属性名和表中的字段名不一样时如何处理
​    1.通过在查询的sql语句中定义字段名的别名让字段名的别名和属性名一致
​        select a_id id from orders.
​    2.通过映射字段名和实体类属性名的一一对应关系
​        property为实体类属性名，column为数据表中的属性名
​        用id来映射主键字段   <id property="id" column="order_id"/>
​        用result来映射非主键字段   <result property="no" column="order_no"/>

## 8.模糊查询like怎么写？
​    1.Java代码中给查询数据加上"%"
​    2.mapper文件中使用 like name "%" #{xxx} "%"
## 9.通常一个xml映射文件，都会写一个dao接口与之对应，这个dao接口的工作原理是什么？
​    dao接口即为mapper接口，接口的全限定名称即为映射文件中的namespace的值
​    接口的方法名，就是映射文件中Mapper的statement的id值
​    接口方法内的参数就是传递给sql的参数
​    Mapper接口是没有实现类的，当调用接口方法时，接口全限定名+方法名拼接字符串作为key值，可唯一定位一个MapperStatement。每一个标签都会被解析为一个MapperStatement对象
​    如：com.StudentDao.findId,可以找到namespace为com.StudentDao下面id为findId的MapperStatement

## 10.如何获取自动生成的(主)键值？
​    insert方法总是返回一个int值，这个值代表的是插入的行数
​    如果采用自增长策略，自动生成的键值在insert方法执行完后可以被设置到传入的参数对象中
​    在insert标签上加入 usegeneratedkeys="true" keyproperty="id"

## 11.如何在mapper中传递多个参数？
​    1.用#{0}代表接受dao中的第一个参数，用#{1}代表接受dao中的第二个参数，不够直观，容易出错
​    2.使用@Param注解  user selectuser（@param（“username”）String name）
​    3.将多个参数封装成map集合
## 12.mybatis动态sql有什么用？执行原理？有哪些动态sql？
​    mybatis动态sql可以在xml映射文件内，以标签的形式编写动态sql，执行原理是根据表达式的值完成逻辑判断并动态拼接sql的功能
​    trim    if    where    foreach    set    choose    when    otherwise    bind
​    if标签,当test标签的值为true时，会将其包含的sql片段拼接到其所在的sql语句中
​    where标签，在有查询条件时，可以自动添加where子句(1=1)
​    foreach标签，用于对数组和集合的遍历
## 13.mybati的xml中，不同的xml映射文件，id是否能重复？
​    不同的xml如果配置了namespace，那么id可以重复；如果没有配置namespace，那么id不可重复

## 14.mybatis实现一对一的几种方式？
​    联合查询：几个表联合查询，只查询一次，通过在resultMap里面配置association节点配置一对一的类
​    嵌套查询：先查一个表，根据这个表里面的结果的外键id，再去另外一个表里面查询数据，也是通过association配置，但另外一个表的查询通过select属性配置

## 15.mybatis实现一对多的几种方式？
​    联合查询：几个表联合查询，只查询一次，通过在resultMap里面配置collection节点配置一对多的类
​    嵌套查询：先查一个表，根据这个表里面的结果的外键id，再去另外一个表里面查询数据，也是通过collection配置，但另外一个表的查询通过select属性配置

## 16.mybatis是否支持延迟加载？实现原理是什么
​    mybatis仅支持association关联对象和collection关联集合对象的延迟加载。在配置文件中可以配置是否启用延迟加载lazyLoadingEnabled=true
## 17.mybatis的一二级缓存
​    一级缓存：作用域为SQLSession，默认开启。在同一个SQLSession中，执行相同的SQL查询，第一次查询数据库并写在缓存中，第二次直接从缓存读取。当中间执行了增删改的操作，会清空缓存。内部缓存使用hahsMap，key作为hahscode+statementID+sql语句，value为查询出来的结果映射成的Java对象
​    二级缓存：作用域为sessionfactory，以namespace为单位(即Mapper.xml文件)，不同namespace下的操作互不影响。例如在Usermapper中有很多针对user表的操作，但是在deptmapper中还有针对user表单的操作，会导致user在两个命名空间下数据不一致；在Usermapper中做了刷新缓存的操作，但是deptmapper中缓存依然有效，如果针对user的单表查询，使用缓存的结果可能会不正确，读到脏数据。

## 18.mybatis是如何进行分页的？
​    mybatis使用RowBounds对象进行分页，它是针对ResultSet结果集执行的内存分页而不是物理分页，可以在sql内书写带有物理分页的参数来完成物理分页功能，也可以使用分页插件来完成物理分页

## 19.什么是orm？
​    即对象关系映射，是一种数据持久化技术。它在对象模型和关系型数据库直接建立起对应关系，并且提供一种机制，通过JavaBean对象去操作数据库表的数据。

## 20.为什么使用redis做缓存不用mybatis？
​    redis将缓存保存在内存，读写速度快，并发能力强
​    支持存储的数据类型更加丰富
​    支持集群(主从复制、负载均衡)
​    支持持久化(快照：将某一时刻所有数据写入硬盘，默认开启持久化方式，bgsave；AOF只追加日志文件：将所有客户端执行的写命令记录到日志文件中)