<h5>mybatis

#{}和\${}的区别是什么

${}是Properties的变量占位符，是静态文本替换。

#{}是sql的参数占位符，Mybatis会将sql中的#{}替换为?

Xml 映射文件中，除了常见的 select|insert|update|delete 标签之外，还有哪些标签？

答 `<resultMap>` `parameterMap` `sql` `include` `selectkey` 

`trim|where|set|foreach|if|choose|when|otherwise|bind`

`sql`为sql片段标签，

`include`标签引入sql片段，

`selectKey`为不支持自增的主键生成策略的标签

dao接口的工作原理，接口里的方法，参数不同能够重载吗?

将Mapper接口和xml的namespace的值对应，接口的方法名就是MappedStatement的id值，接口里面的参数就是传递给sql的参数。

MyBatis 是如何进行分页的？分页插件的原理是什么？

分页插件的基本原理是使用拦截的原理，重写sql的原理

<h5>springboot

springboot的好处

1.springboot是快速整合spring+springMVC的框架

2.springboot是自动装配的，不需要spring一样写,xml文件

3.启动容器方便通过main方法启动。

4.通过application.yml配置全局文件

springboot自动装配原理

SpringBoot在启动时会扫描外部原因jar包中的META-INF/spring.factories文件，将文件中的配置类型的信息加载到Spring容器。

自动装配可以简单的理解为通过注解或者是简单的配置。就能在springboot的帮助下实现某块功能。

@EnableAutoConfigration=>{AutoConfigurationImportSelector.class}=>{

interface ImportSelector=>{

selectImports[获取所有符合条件的类的全限定类名，这些类需要被加载到 IoC 容器中]

=>{

getAutoConfigurationEntry()[1.获取所有字段配置类名2.从META-INF/spring.factories加载自动配置类]

}

}

}

步骤

1.判断自动装配是否打开，

2.用于获取`EnableAutoConfiguration`注解中的 `exclude`[class] 和 `excludeName`[string]。

3.获取需要自动装配的所有配置类，读取`META-INF/spring.factories`

4.筛选，`@ConditionalOnXXX` 中的所有条件都满足，该类才会生效。

创建starter工程。

1.创建工程

2.引入 Spring Boot 相关依赖

3.创建`ThreadPoolAutoConfiguration`

4.工程的 resources 包下创建`META-INF/spring.factories`文件

总结：

Spring Boot 通过`@EnableAutoConfiguration`开启自动装配，通过 SpringFactoriesLoader 最终加载`META-INF/spring.factories`中的自动配置类实现自动装配，自动配置类其实就是通过`@Conditional`按需加载的配置类，想要其生效必须引入`spring-boot-starter-xxx`包实现起步依赖







springboot常用注解

SpringBootApplication[ `@Configuration`、`@EnableAutoConfiguration`、`@ComponentScan`]

@Autowired

`@Component`,`@Repository`,`@Service`, `@Controller`

@RestController[`@Controller``@ResponseBody`]

@Scope[]

@Configuration

@GetMapping("users")

@PostMapping("users")

@PathVariable

@RequestParam

@RequestBody

@Value("${property}")

@ConfigurationProperties[@ConfigurationProperties(prefix = "library")]

@PropertySource[读取指定 properties 文件]

`@Email` 被注释的元素必须是 Email 格式。

`@NotBlank` 被注释的字符串非 null，并且必须包含一个非空白字符

@Validated校验方法参数[@Max]

`@ControllerAdvice` :注解定义全局异常处理类

`@ExceptionHandler` :注解声明异常处理方法

`@Entity`声明一个类对应一个数据库实体。

`@Table` 设置表名

 @Id

 @GeneratedValue(strategy = GenerationType.IDENTITY)[主键声明策略]

@Column(name = "user_name", nullable = false, length=32)[声明字段]

@OneToOne` 声明一对一关系

`@OneToMany` 声明一对多关系

@ManyToOne` 声明多对一关系

`@ManyToMany` 声明多对多关系

  `@Transactional`事务







<h5>Spring 事务总结

什么是事务

事务是逻辑逻辑上的一组操作，要么都执行，要么都不执行。

事务能否生效数据库引擎是否支持事务是关键(innodb)

事务的ACID

A原子性:一个事务中的所有操作，要么成功，要么回滚。

一致性:事务结束后，数据库的完整性没有被破坏。

隔离性:防止多个·事务并发执行时由于交叉执行而导致的数据的移植性·。隔离级别:未提交读（Read uncommitted）、提交读（read committed）、可重复读（repeatable read）和串行化（Serializable）

持久性(Durability):事务处理结束后，堆数据的修改就是永久的。

mysql怎么保证原子性：

恢复机制是通过回滚日志(undo log)。

编程式事务隔离(很少用)。

```java
@Autowired
private TransactionTemplate transactionTemplate;
transactionTemplate.execute(new TransactionCallbackWithoutResult() {
    
}
```

声明式事务管理

@Transactional

3个重要的接口:

PlatformTransactionManager： （平台）事务管理器，Spring 事务策略的核心。

TransactionDefinition： 事务定义信息(事务隔离级别、传播行为、超时、只读、回滚规则)。

TransactionStatus： 事务运行状态。

什么是事务属性呢？

隔离级别：

传播行为

回滚规则

是否只读

事务超时

事务传播行为？

事务的传播行为是解决业务层之间相互调用的事务问题。

TransactionDefinition.PROPAGATION_REQUIRED(默认事务)如果当前存在事务则加入事务，如果没有事务就新建一个一个事务。

TransactionDefinition.PROPAGATION_REQUIRES_NEW：

@Transactional使用详解：

方法：推荐使用在方法上，该注解只能用于public方法上，否则不生效。

@Transaction事务注解原理：

@Transactional的工作机制是基于AOP实现的，AOP又是使用动态代理实现的，如果目标对象实现了接口，默认情况下会采用JDK动态代理。

没有目标对象没有是实现接口会使用CGLIB动态代理。

如果一个类或者是一个类中的public方法被标注@Transactional注解的话，Spring容器就会启动的时候为其创建一个代理类。在调用被@Transational类中的invoke()方法。这个方法的作用就是正在目标方法之前开启事务·，方法执行过程中如果出现异常的时候就回滚事务，方法调用完成之后提交事务。



SpringAop自调用问题

若同一类中没有使用@Transactional注解的方法内部调用有@Teansactional注解方法。有@Transacional方法的事务会失效。

解决办法就是避免同一类中自调用或者使用 AspectJ 取代 Spring AOP 代理

注意事项

- `@Transactional` 注解只有作用到 public 方法上事务才生效，不推荐在接口上使用；
- 避免同一个类中调用 `@Transactional` 注解的方法，这样会导致事务失效；
- 正确的设置 `@Transactional` 的 `rollbackFor` 和 `propagation` 属性，否则事务可能会回滚失败;
- 被 `@Transactional` 注解的方法所在的类必须被 Spring 管理，否则不生效；
- 底层使用的数据库必须支持事务机制，否则不生效；



rollbackFor=Exception.class

读未提交 脏读 幻读 不可重复读

读已提交 幻读 不可重复读

可重复读 不可重复读

序列化  (完全服从 ACID 的隔离级别) (严重影响程序的性能)

@Transactional(rollbackFor = Exception.class)注解了解吗？

如果不配置的话，事务只会在遇到RuntimeException才会回滚事务。(Exception[非运行时异常时也回滚])









<h5>Spring

一款开源的轻量的Java开发框架。(IOC与AOP)。方便整合其他框架。

spring最核心的思想就是不重谢

 IOC控制反转：

原本在程序中手动创建对象的控制权，交由 Spring 框架来管理。

IOC容器是Spring用来实现IOC的载体，IOC容器实际上就是个Map(key,value)Map中存放了各种对象。

AOP：面向切面编程，能够将哪些与业务无关，却为业务模块所共同调用的逻辑与责任(事务处理，日志管理，权限管理)封装起来，编译减少系统的重复代码，降低模块之间的耦合，有利于未来达到可扩展性和维护性。

Spring AOP就是基于动态代理，

Spring AOP 会使用 **JDK Proxy**，去创建代理对象，而对于没有实现接口的对象，就无法使用 JDK Proxy 去进行代理了，这时候 Spring AOP 会使用 **Cglib** 生成一个被代理对象的子类来作为代理，

 AspectJ 

SpringAop属于运行时增强，而AspectJ时编译时增强。

Spring Aop基于代理。AspectJ基于字节码操作。

AspectJ 比SpringAop块。



SpringBean

Beam指的就是被IOC容器管理的类。



将类声明为Bean的注解有哪些。

@Component

@Repository

@Service

@Controller



@Component 和 @Bean 的区别是什么？

@Component注解作用与类，@Bean作用与方法。

@Component通过路径扫描来装载到IOC容器。

@Bean通常是我们在标有好注解方法中定义产生这个方法的定义了Bean。

@Bean注解比@Compent的注解的自定义性更强一些，很多地方只能使用@Bean来注册Bean。

注入 Bean 的注解有哪些?

@Autowired

@Resource

@Inject



@Autowired注入方式是ByType。工具接口的类型去注入接口的实现。

如果一个接口存在多个实现类，Bytype就无法注入增强的对象。

@Resource （也能ByType）ByName(根据姓名去配置注入接口的实现)

`@Resource`属于 JDK 提供的注解，默认注入方式为 `byName`。如果无法通过名称匹配到对应的 Bean 的话，注入方式会变为`byType`。

我们还是建议通过 `@Qualifier` +`@Autowired`注解来显示指定名称而不是依赖变量的名称

- `@Autowired` 是 Spring 提供的注解，`@Resource` 是 JDK 提供的注解。
- `Autowired` 默认的注入方式为`byType`（根据类型进行匹配），`@Resource`默认注入方式为 `byName`（根据名称进行匹配）。
- 当一个接口存在多个实现类的情况下，`@Autowired` 和`@Resource`都需要通过名称才能正确匹配到对应的 Bean。`Autowired` 可以通过 `@Qualifier` 注解来显示指定名称，`@Resource`可以通过 `name` 属性来显示指定名称。

Bean 的作用域有哪些?

singleton（单列）(默认)

prototype(每一次请求都会创建一个bean)

request:每一次 HTTP 请求都会产生一个新的 bean，该 bean 仅在当前 HTTP request 内有效

session:每一次来自新 session 的 HTTP 请求都会产生一个新的 bean，该 bean 仅在当前 HTTP session 内有效

global-session:全局 session 作用域，仅仅在基于 portlet 的 web 应用中才有意义，Spring5 已经没有了。



如何配置 bean 的作用域呢

xml 方式：

```xml
<bean id="..." class="..." scope="singleton"></bean>
```

```java
@Bean
@Scope(value = ConfigurableBeanFactory.SCOPE_PROTOTYPE)
public Person personPrototype() {
    return new Person();
}
```

Bean 的生命周期了解么?

Bean容器找到配置文件SpringBean的定义。SpringBeanDefination

Beab容器例如Java Reflection API 创建一个Bean的实列。

如果设计到属性值，利用set()方法设置属性值。

如果Bean实现了BeanNameAware接口，调用setBeanName（）方法，传入bean的名字。

如果Bean实现了BeanCloassLoaderAware的接口。调用setBeanClassLoader()方法，传入ClassLoader对象实列。

如果Bean实现BeanFactoryAware接口就调用setBeanFactory()方法传入BeanFactory实列

与上面的类似，如果实现了其他 `*.Aware`接口，就调用相应的方法

如果有和加载这个Bean的Spring容器相关的BeanPostProcessor对象。执行postProcessBeforeInitalization()方法。

如果Bean出现InitaliazingBean接口，执行afterPropertiesSet()ff1,

如果Bean中在配置文件中定义init-method属性，执行指定方法。

如果有和加载这个Bean容器相关的BeanPostProcessor对象，执行postProcessAfterInitaliztion()方法。

当要销毁Bean的时候，如果Bean实现了DisposableBean接口，执行destroy()方法。

当要销毁Bean的时候，如果Bean在配置文件中的定义包含destroy-method属性，执行指定方法。

与之比较类似的中文版本:

![Spring Bean 生命周期](https://images.xiaozhuanlan.com/photo/2019/b5d264565657a5395c2781081a7483e1.jpg)



<h5>Spring MVC

MVC是模型，视图，控制器的简写，其核心思想是通过将业务逻辑。数据，显示分离来组织代码。是Spring实现web的一种设计模式

Spring MVC 下我们一般把后端项目分为 Service 层（处理业务）、Dao 层（数据库操作）、Entity 层（实体类）、Controller 层(控制层，返回数据给前台页面)

流程:

客户端发送请求，直接请求到DispatcherServlet(前端处理器)。

DispatcherServlet会根据请求信息调用HandlerMapping(映射处理器d)，解析请求到后端处理器(Controller)

3.到达后端处理器，开始后HandlerAdapter(处理适配器)[通过反射执行业务逻辑],它会根据Handler老调用真正的处理器开处理请求，并处理相应的业务逻辑。

4.处理器处理业务完成之后，会返回以恶搞ModelAndView对象。Model是返回的数据对象，View是个逻辑上的view（return a）

5.视图解析器(ViewResovler)会根据逻辑view找到真正view(视图)。

8.DisPaterServlet把返回的Model传给View(视图渲染)。

8.把View返回给请求者。



Spring 框架中用到了哪些设计模式

工厂设计模式:BeanFactory、ApplicationContext创建Bean

代理模式:SpringAOP功能的实现。

单例模式:Spring中的Bean默认都素单单例。

模板方法模式:Spring中的JDBCTemplete。







<h5>JPA

@Transient (使用注解避免被持久化)





<h5>SpringCloud

微服务系统架构一战式解决方案，服务发现注册，配置中心，信息总线，负载均衡，断路器，数据监控。





服务发现框架--Eureka

功能：服务发现、服务提供者，服务消费者，服务中介，服务注册[在注册的时候，需要向注册中心提供元数据。]

服务续约[eurek客户端会每隔30s发一次心跳续约]

获取注册列表信息，服务下线，服务剔除





负载均衡Ribbon[负载均衡器]

什么是RestTemplete

RestTemplate`是`Spring提供的一个访问 Http 服务的客户端类。

Nginx是集中式的负载均衡[就是将所有请求都集中起来，然后进行负载均衡]。

ribbon [在客户端进行负载均衡才进行请求的]

Ribbon 的几种负载均衡算法[轮询，随机，重试，加权轮询]



Open Feign[远程调用]

不用写RestTemplete，可以像写接口一样去调用其他服务的接口。





Hystrix[熔断与降级]

阻塞崩溃:[主要是被调用的服务网络阻塞，造成调用者阻塞，从而引发一些列的系统故障]

熔断：在指定的时间窗内，请求的失败率到达设置值，系统就会通过断路器直接将此请求链路断开。

```java
@HystrixCommand(
    commandProperties = {@HystrixProperty(name = "execution.isolation.thread.timeoutInMilliseconds",value = "1200")}
)
public List<Xxx> getXxxx() {
    // ...省略代码逻辑
}
```

降级:降级是为了更好的用户体验，当一个方法调用异常时，通过执行另一种代码逻辑来给用户友好的回复。[超时]

```java
@HystrixCommand(fallbackMethod = "getHystrixNews")
@GetMapping("/get/news")
public News getNews(@PathVariable("id") int id) {
    // 调用新闻系统的获取新闻api 代码逻辑省略
}
//
public News getHystrixNews(@PathVariable("id") int id) {
    // 做服务降级
    // 返回当前人数太多，请稍后查看
}
```





微服务网关--Zuul[路由和过滤器]

将网关注册到注册中心

```yml
server:
  port: 9000
eureka:
  client:
    service-url:
      # 这里只要注册 Eureka 就行了
      defaultZone: http://localhost:9997/eureka
```

统一前缀

```yml
zuul:
  prefix: /zuul
```



路由策略

```yml
zuul:
  routes:
    consumer1: /FrancisQ1/**
    consumer2: /FrancisQ2/**
```

服务名屏蔽

```yml
zuul:
  ignore-services: "*"
```

路径屏蔽

```yml
zuul:
  ignore-patterns: **/auto/**
```

​	敏感请求头屏蔽[ `Cookie`、`Set-Cookie`]





Zuul 的过滤功能:

```java
// 加入Spring容器
@Component
public class PreRequestFilter extends ZuulFilter {
    // 返回过滤器类型 这里是前置过滤器
    @Override
    public String filterType() {
        return FilterConstants.PRE_TYPE;
    }
    // 指定过滤顺序 越小越先执行，这里第一个执行
    // 当然不是只真正第一个 在Zuul内置中有其他过滤器会先执行
    // 那是写死的 比如 SERVLET_DETECTION_FILTER_ORDER = -3
    @Override
    public int filterOrder() {
        return 0;
    }
    // 什么时候该进行过滤
    // 这里我们可以进行一些判断，这样我们就可以过滤掉一些不符合规定的请求等等
    @Override
    public boolean shouldFilter() {
        return true;
    }
    // 如果过滤器允许通过则怎么进行处理
    @Override
    public Object run() throws ZuulException {
        // 这里我设置了全局的RequestContext并记录了请求开始时间
        RequestContext ctx = RequestContext.getCurrentContext();
        ctx.set("startTime", System.currentTimeMillis());
        return null;
    }
}
```



```java
// lombok的日志
@Slf4j
// 加入 Spring 容器
@Component
public class AccessLogFilter extends ZuulFilter {
    // 指定该过滤器的过滤类型
    // 此时是后置过滤器
    @Override
    public String filterType() {
        return FilterConstants.POST_TYPE;
    }
    // SEND_RESPONSE_FILTER_ORDER 是最后一个过滤器
    // 我们此过滤器在它之前执行
    @Override
    public int filterOrder() {
        return FilterConstants.SEND_RESPONSE_FILTER_ORDER - 1;
    }
    @Override
    public boolean shouldFilter() {
        return true;
    }
    // 过滤时执行的策略
    @Override
    public Object run() throws ZuulException {
        RequestContext context = RequestContext.getCurrentContext();
        HttpServletRequest request = context.getRequest();
        // 从RequestContext获取原先的开始时间 并通过它计算整个时间间隔
        Long startTime = (Long) context.get("startTime");
        // 这里我可以获取HttpServletRequest来获取URI并且打印出来
        String uri = request.getRequestURI();
        long duration = System.currentTimeMillis() - startTime;
        log.info("uri: " + uri + ", duration: " + duration / 100 + "ms");
        return null;
    }
}
```

令牌桶限流[如果里面没有满那么就会以一定 **固定的速率** 会往里面放令牌，一个请求过来首先要从桶中获取令牌，如果没有获取到，那么这个请求就拒绝，如果获取到那么就放行]

```java
package com.lgq.zuul.filter;

import com.google.common.util.concurrent.RateLimiter;
import com.netflix.zuul.ZuulFilter;
import com.netflix.zuul.context.RequestContext;
import com.netflix.zuul.exception.ZuulException;
import lombok.extern.slf4j.Slf4j;
import org.springframework.cloud.netflix.zuul.filters.support.FilterConstants;
import org.springframework.stereotype.Component;

@Component
@Slf4j
public class RouteFilter extends ZuulFilter {
    // 定义一个令牌桶，每秒产生2个令牌，即每秒最多处理2个请求
    private static final RateLimiter RATE_LIMITER = RateLimiter.create(2);
    @Override
    public String filterType() {
        return FilterConstants.PRE_TYPE;
    }

    @Override
    public int filterOrder() {
        return -5;
    }

    @Override
    public Object run() throws ZuulException {
        log.info("放行");
        return null;
    }

    @Override
    public boolean shouldFilter() {
        RequestContext context = RequestContext.getCurrentContext();
        if(!RATE_LIMITER.tryAcquire()) {
            log.warn("访问量超载");
            // 指定当前请求未通过过滤
            context.setSendZuulResponse(false);
            // 向客户端返回响应码429，请求数量过多
            context.setResponseStatusCode(429);
            return false;
        }
        return true;
    }
}
```



管理配置Config[可以修改配置文件的]



SpringCloudBus[消息总线]

<img src="https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/2019-11/springcloud-bus-s213dsfsd.jpg" style="zoom:50%;" />

