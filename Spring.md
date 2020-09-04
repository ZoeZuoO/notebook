# Spring   -119

容器（可以管理所有的组件（类））框架

### jar包一览 

三个一组：

-sources：源码

![1-1](https://github.com/ZoeZuoO/PictureBed/blob/master/1.png)

### spring的模块划分：

[^1]: 绿色表示模块，黑色表示由哪些jar包组成

![1-2](https://github.com/ZoeZuoO/PictureBed/blob/master/2.png)

* Test：Spring单元测试模块

* Core Container：核心容器（IOC）

* AOP+Aspects：面向切面编程

* DAta Access：数据访问/集成---访问数据库

  * 数据：
    * JDBC 访问数据库
    * ORM 对象关系映射（Object Relationship Mapping）
    * TX 事务

  * 集成:
    * OX(xml)M
    * JMS

* Web：Spring 开发web应用模块

  * servlet：与原生web相关
  * webmvc：开发web项目的
  * porlet：开发web应用的组件集成

## IOC和AOP

### IOC（容器）14-60

* 作用：整合其他框架

* ***控制反转***：Inversion of control。主动的new资源变为被动的接收资源

  * 控制：资源的获取方式

    *  主动式（要什么资源都自己创建即可）

      全部自己new出来

      ![1-3](https://github.com/ZoeZuoO/PictureBed/blob/master/3.png)

    * 被动式：交给容器创建和设置我们需要的资源

      ![1-4](https://github.com/ZoeZuoO/PictureBed/blob/master/4.png)

  * 容器：管理所有的组件（有功能的类），在一个类中需要用到另一些类时，容器帮我们把另一些类的对象创建出来，并赋值过去，我们直接接收，使用就可以

* ***依赖注入***：Dependency Injection

  * 容器知道哪个组件运行的时候，需要另一个组件，通过反射的形式，将容器中准备好的对象注入（利用反射给属性赋值）到运行的组件中
  
* **框架编写流程：**

  * 导包

    * spring运行的时候依赖日志包，commons-logging（Apache）

  * 写配置

    * spring的配置文件中，集合了spring的ioc容器管理的所有组件	

  * 测试

  * ------

    注意！！！(eclipse版)

    * src等所有源码包的东西都会编译合并到**类路径**下面
      * java：/bin/
      * web：/WEB-INF/classes/
    * 一定要导包commons-logging
    * 先导包再创建配置文件
    * spring的容器接管了标志了s的类
    * IOC容器的接口：ApplicationContext
      1. new ClassPathXMLApplicationContext();//IOC容器的配置文件在类路径下面
      2. FileSystemXmlApplicationContext();//IOC容器的配置文件在磁盘路径下面
    * 容器中对象的创建在容器创建完成的时候就已经创建
    * 同一个组件在IOC容器中是单实例的，容器启动完成都已经创建准备好的
    * 容器中如果没有这个组件，获取组件会报NoSuchBeanDefinitionException
    * IOC 容器在创建这个组件对象的时候，（property）会利用setter方法为JavaBean的属性进行赋值
    * JavaBean的属性名是由getter/setter方法决定的

#### 练习

* **从IOC 容器中获取bean的实例**

  1. ioc.getBean(Person.Class)---只能获取到一个对象
  2. ioc.getBean("id名称",Class)

* **调用有参构造器进行创建对象并赋值**

  <constractor-arg name="" value="" index="" type=""></constractor-arg>

  1. 有几个参数，就有几个该标签

  2. 也可以省略name属性，但要按照顺序构造器参数的位置

  3. 可以用index为参数指定索引，从0开始
  4. type指定参数的Java类型

* **通过p名称空间为bean赋值**

  1. 导入p名称空间

  2. <bean p:xxxx>写带前缀的标签/属性

     *（奇怪的知识：xml---可扩展的标记语言）*

* **为各种属性赋值**

  * **使用null值**
    1. 默认引用类型就是null，基本类型是默认值
    2. 要在<property>标签体中进行复杂的赋值:<null/>
 
 
- **ref引用内部Bean**

  - ref 代表引用外面的一个值，相当于ioc.getBean()

- **引用外部Bean**

  - 相当于new了一个对象

  

  ```
  <property name="">
  	<!--这属于内部bean，不能被获取到，用id也获取不到，只能内部使用-->
  	<bean class="">
  		<property>...</property>
  	</bean>
  </property>	
  
  	<!--list属性赋值-->
  <property name="">
  	<list></list>
  </property>
  
  	<!--map属性赋值-->
  <property name="">	
      <map>
          <entry key="" value=""></entry>
          <entry key="">
              <bean>
                  <property></property>	
              </bean>
          </entry>
      </map>
  </property>
  
  <property name="">
      <!--private Properties properties;-->
   	<props>
   	<!--等于new Properties();所有的k=v都是String，值直接写在标签体中即可-->
   		<prop key="name>zoe</prop>
   	</props>
  </property>
  ```

![image](https://github.com/ZoeZuoO/notebook/blob/master/images/1-1.png)

* **util名称空间**创建集合类型的bean，方便引用

  * ```xml
    相当于new LinkedHashMap<>()
    <util:map id="">
    	<!--添加元素-->
    </util:map>
    ```

  * 还有util:list等

* **级联属性（属性的属性）赋值**
![image](https://github.com/ZoeZuoO/PictureBed/blob/master/5.png)

### AOP（面向切面编程）61-82

主要用来写声明式事务--->首先学习spring操作数据库---spring-jdbcTemplate

# Spring MVC 120-229

# Mybatis 230-276

