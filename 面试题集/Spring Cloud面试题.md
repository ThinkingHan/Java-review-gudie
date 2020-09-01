# Contanct Me

如果觉得看起来比较麻烦，需要PDF版本，或是需要更多学习资料，都可以加上QQ群领取

>本群由我创立，目前已将群主权限交由合作方便于进行日常管理，介意的朋友们在GitHub上看最新版就好了
>
>> 这份笔记资料是会免费提供的，特地向你们保证…毕竟还是要恰饭的嘛…

祝愿每一位有追求的Java开发同胞都能进大厂拿高薪！

## QQ群

Java架构交流QQ群：**930254941**  （备注一下GitHub，免得被认成打无良广告的）

快捷加群方式：[点击此处加入群聊Java架构交流群](https://jq.qq.com/?_wv=1027&k=Xu0ju5PW)

![](https://upload-images.jianshu.io/upload_images/11474088-f15f3310f6b7610f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


>PS：
>
>>平常很忙，找小夕小姐姐领取就好了，免费获取的！

![](https://upload-images.jianshu.io/upload_images/11474088-d4fa503624f05687.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

------

## 前言

**来分享一下面试必备的Spring Cloud问题解析！**用XMind画了一张导图记录**Spring Cloud**的学习笔记和一些面试解析（源文件对部分节点有详细备注和参考资料，**欢迎关注我的公众号：以Java架构赢天下 后台发送【导图】拿下载链接，已经完善更新）：****

![2020备战阿里Java岗，这20道SpringCloud面试解析不懂，等通知吧](http://p3.pstatp.com/large/pgc-image/827bdc3d84314d998fc5633710defa48)



## **1.什么是微服务**

1. 微服务是一种架构⻛格，也是一种服务；
2. 微服务的颗粒⽐较⼩，⼀个⼤型复杂软件应⽤由多个微服务组成，⽐如Netflix⽬前由500多的微服务组成；
3. 它采用UNIX设计的哲学，每种服务只做⼀件事，是一种松耦合的能够被独⽴开发和部署的⽆状态化服务（独⽴扩展、升级和可替换）。

## **2. 微服务之间是如何独立通讯的**

1. Dubbo 使用的是 RPC 通信，⼆进制传输，占⽤带宽⼩；
2. Spring Cloud 使⽤的是 HTTP RESTFul ⽅式。

![2020备战阿里Java岗，这20道SpringCloud面试解析不懂，等通知吧](http://p3.pstatp.com/large/pgc-image/b392b4ad84b2487eb632f9d1ad0dcb1c)



## **3. springcloud和dubbo有哪些区别**

1. Dubbo具有调度、发现、监控、治理等功能，⽀持相当丰富的服务治理能力。Dubbo架构下，注册中⼼对等集群，并会缓存服务列表已被数据库失效时继续提供发现功能，本身的服务发现结构有很强的可⽤性与健壮性，⾜够⽀持⾼访问量的⽹站。
2. 虽然Dubbo ⽀持短连接⼤数据量的服务提供模式，但绝大多数情况下都是使⽤⻓连接⼩数据量的模式提供服务使用的。所以，对于类似于电商等同步调⽤场景多并且能⽀撑搭建Dubbo 这套⽐较复杂环境的成本的产品⽽⾔，Dubbo 确实是一个可以考虑的选择。但如果产品业务中由于后台业务逻辑复杂、时间⻓⽽导致异步逻辑⽐较多的话，可能Dubbo 并不合适。同时，对于⼈⼿不⾜的初创产品⽽⾔，这么重的架构维护起来也不是很方便。
3. Spring Cloud由众多⼦项⽬组成，如Spring Cloud Config、Spring Cloud Netflix、Spring Cloud Consul 等，提供了搭建分布式系统及微服务常用的⼯具，如配置管理、服务发现、断路器、智能路由、微代理、控制总线、一次性token、全局锁、选主、分布式会话和集群状态等，满足了构建微服务所需的所有解决⽅案。⽐如使⽤Spring Cloud Config 可以实现统⼀配置中⼼，对配置进⾏统⼀管理；使⽤Spring Cloud Netflix 可以实现Netflix 组件的功能 - 服务发现（Eureka）、智能路由（Zuul）、客户端负载均衡（Ribbon）。
4. Dubbo 提供了各种 Filter，对于上述中“⽆”的要素，可以通过扩展 Filter 来完善。
5. dubbo的开发难度较⼤，原因是dubbo的jar包依赖问题很多⼤型⼯程⽆法解决。

![2020备战阿里Java岗，这20道SpringCloud面试解析不懂，等通知吧](http://p9.pstatp.com/large/pgc-image/d8f6598a96fd4bfcb418aeebe2edd0c0)



## **4. springboot和springcloud认识**

- Spring Boot 是 Spring 的⼀套快速配置脚⼿架，可以基于Spring Boot 快速开发单个微服务，Spring Cloud是一个基于Spring Boot实现的云应⽤开发⼯具；
- Spring Boot专注于快速、⽅便集成的单个微服务个体，Spring Cloud关注全局的服务治理框架；
- Spring Boot使⽤了默认⼤于配置的理念，很多集成⽅案已经帮你选择好了，能不配置就不配置；
- Spring Cloud很⼤的⼀部分是基于Spring Boot来实现，可以不基于Spring Boot吗？不可以。

## 5. 什么是服务熔断，什么是服务降级

**服务熔断：**

如果检查出来频繁超时，就把consumer调⽤provider的请求，直接短路掉，不实际调⽤，⽽是直接返回⼀个mock的值。

**服务降级：**

**consumer 端：**consumer 如果发现某个provider出现异常情况，⽐如，经常超时(可能是熔断引起的降级)，数据错误，这时，consumer可以采取⼀定的策略，降级provider的逻辑，基本的有直接返回固定的数据。

**provider 端：**当provider 发现流量激增的时候，为了保护⾃身的稳定性，也可能考虑降级服务。

1.直接给consumer返回固定数据

2.需要实时写⼊数据库的，先缓存到队列⾥，异步写⼊数据库。

## **6. 微服务的优缺点**

**优点：**

- 单⼀职责：每个微服务仅负责⾃⼰业务领域的功能；
- ⾃治：⼀个微服务就是⼀个独⽴的实体，它可以独⽴部署、升级，服务与服务之间通过REST等形式的标准接⼝进⾏通信，并且⼀个微服务实例可以被替换成另⼀种实现，⽽对其它的微服务不产⽣影响。
- 逻辑清晰：微服务单⼀职责特性使微服务看起来逻辑清晰，易于维护。
- 简化部署：单系统中修改⼀处需要部署整个系统，⽽微服务中修改⼀处可单独部署⼀个服务
- 可扩展：应对系统业务增长的⽅法通常采用横向（Scale out）或纵向（Scale up）的⽅向进⾏扩展。分布式系统中通常要采⽤Scale out的⽅式进⾏扩展。
- 灵活组合：
- 技术异构：不同的服务之间，可以根据⾃⼰的业务特点选择不通的技术架构，如数据库等。

**缺点：**

- **复杂度⾼：**服务调⽤要考虑被调⽤⽅故障、过载、消息丢失等各种异常情况，代码逻辑更加复杂；对于微服务间的事务性操作，因为不同的微服务采⽤了不同的数据库，将⽆法利⽤数据库本身的事务机制保证⼀致性，需要引⼊⼆阶段提交等技术。
- **运维复杂：**系统由多个独⽴运⾏的微服务构成，需要⼀个设计良好的监控系统对各个微服务的运⾏状态进⾏监控。运维⼈员需要对系统有细致的了解才对够更好的运维系统。
- **通信延迟：**微服务之间调⽤会有时间损耗，造成通信延迟。

## 7. 使⽤中碰到的坑

- **超时：**确保Hystrix超时时间配置为⻓于配置的Ribbon超时时间
- **feign path：**feign客户端在部署时若有contextpath应该设置 path="/***"来匹配你的服务名。
- **版本：**springboot和springcloud版本要兼容。

## **8. 列举微服务技术栈**

- 服务⽹关Zuul
- 服务注册发现Eureka+Ribbon
- 服务配置中⼼Apollo
- 认证授权中⼼Spring Security OAuth2
- 服务框架Spring Boot
- 数据总线Kafka
- ⽇志监控ELK
- 调⽤链监控CAT
- Metrics监控KairosDB
- 健康检查和告警ZMon
- 限流熔断和流聚合Hystrix/Turbine

## **9. eureka和zookeeper都可以提供服务的注册与发现功能，他们的区别**

**Zookeeper保证CP**

当向注册中⼼查询服务列表时，我们可以容忍注册中⼼返回的是⼏分钟以前的注册信息，但不能接受服务直接down掉不可⽤。也就是说，服务注册功能对可⽤性的要求要⾼于⼀致性。但是zk会出现这样⼀种情况，当master节点因为⽹络故障与其他节点失去联系时，剩余节点会重新进⾏leader选举。问题在于，选举leader的时间太⻓，30 ~ 120s, 且选举期间整个zk集群都是不可⽤的，这就导致在选举期间注册服务瘫痪。在云部署的环境下，因⽹络问题使得zk集群失去master节点是较⼤概率会发⽣的事，虽然服务能够最终恢复，但是漫⻓的选举时间导致的注册⻓期不可⽤是不能容忍的。

**Eureka保证AP**

Eureka看明⽩了这⼀点，因此在设计时就优先保证可⽤性。Eureka各个节点都是平等的，⼏个节点挂掉不会影响正常节点的⼯作，剩余的节点依然可以提供注册和查询服务。⽽Eureka的客户端在向某个Eureka注册或如果发现连接失败，则会⾃动切换⾄其它节点，只要有⼀台Eureka还在，就能保证注册服务可⽤(保证可⽤性)，只不过查到的信息可能不是最新的(不保证强⼀致性)。除此之外，Eureka还有⼀种⾃我保护机制，如果在15分钟内超过85%的节点都没有正常的⼼跳，那么Eureka就认为客户端与注册中⼼出现了⽹络故障，**此时会出现以下⼏种情况：**

1. Eureka不再从注册列表中移除因为⻓时间没收到⼼跳⽽应该过期的服务
2. Eureka仍然能够接受新服务的注册和查询请求，但是不会被同步到其它节点上(即保证当前节点依然可⽤)
3. 当⽹络稳定时，当前实例新的注册信息会被同步到其它节点中

**因此， Eureka可以很好的应对因⽹络故障导致部分节点失去联系的情况，⽽不会像zookeeper那样使整个注册服务瘫痪。**

## **10. eureka服务注册与发现原理**

- 每30s发送⼼跳检测重新进⾏租约，如果客户端不能多次更新租约，它将在90s内从服务器注册中⼼移除。
- 注册信息和更新会被复制到其他Eureka 节点，来⾃任何区域的客户端可以查找到注册中⼼信息，每30s发⽣⼀次复制来定位他们的服务，并进⾏远程调⽤。
- 客户端还可以缓存⼀些服务实例信息，所以即使Eureka全挂掉，客户端也是可以定位到服务地址的。

![2020备战阿里Java岗，这20道SpringCloud面试解析不懂，等通知吧](http://p3.pstatp.com/large/pgc-image/760dbe42c99847a8851567fe1c26e37d)



## **11. dubbo服务注册与发现原理**

![2020备战阿里Java岗，这20道SpringCloud面试解析不懂，等通知吧](http://p3.pstatp.com/large/pgc-image/c311d4d00a1049d5b1ba0d01b58b85d3)



![2020备战阿里Java岗，这20道SpringCloud面试解析不懂，等通知吧](http://p1.pstatp.com/large/pgc-image/12ac18f472744e6697a6d8e8c4dc8c43)



**调⽤关系说明：**

1. 服务容器负责启动,加载,运⾏服务提供者。
2. 服务提供者在启动时,向注册中⼼注册⾃⼰提供的服务。
3. 服务消费者在启动时,向注册中⼼订阅⾃⼰所需的服务。
4. 注册中⼼返回服务提供者地址列表给消费者,如果有变更,注册中⼼将基于⻓连接推送变更数据给消费者。
5. 服务消费者,从提供者地址列表中,基于软负载均衡算法,选⼀台提供者进⾏调⽤,如果调⽤失败,再选另⼀台调⽤。
6. 服务消费者和提供者,在内存中累计调⽤次数和调⽤时间,定时每分钟发送⼀次统计数据到监控中⼼。

## **12. 限流**

### **1、http限流：我们使⽤nginx的limitzone来完成：**

```
//这个表示使⽤ip进⾏限流 zone名称为req_one 分配了10m 空间使⽤漏桶算法 每秒钟允许1个请求
limit_req_zone $binary_remote_addr zone=req_one:10m rate=1r/s; //这边burst表示可以瞬间超过20个请求 由于没有noDelay参数因此需要排队 如果超过这20个那么直接返回503
limit_req zone=req_three burst=20;
```

### **2、dubbo限流：dubbo提供了多个和请求相关的filter：ActiveLimitFilter ExecuteLimitFilter TPSLimiterFilter**

**1. ActiveLimitFilter：**

```
@Activate(group = Constants.CONSUMER, value = Constants.ACTIVES_KEY)
```

作⽤于客户端，主要作⽤是控制客户端⽅法的并发度；

当超过了指定的active值之后该请求将等待前⾯的请求完成【何时结束呢？依赖于该⽅法的timeout 如果没有设置timeout的话可能就是多个请求⼀直被阻塞然后等待随机唤醒。

**2. ExecuteLimitFilter：**

```
@Activate(group = Constants.PROVIDER, value = Constants.EXECUTES_KEY)
```

作⽤于服务端，⼀旦超出指定的数⽬直接报错 其实是指在服务端的并⾏度【需要注意这些都是指的是在单台服务上⽽不是整个服务集群】

**3. TPSLimiterFilter：**

```
@Activate(group = Constants.PROVIDER, value = Constants.TPS_LIMIT_RATE_KEY)
```

- 作⽤于服务端，控制⼀段时间内的请求数；
- 默认情况下取得tps.interval字段表示请求间隔 如果⽆法找到则使⽤60s 根据tps字段表示允许调⽤次数。
- 使⽤AtomicInteger表示允许调⽤的次数 每次调⽤减少1次当结果⼩于0之后返回不允许调⽤

### **3、springcloud限流：**

1.我们可以通过semaphore.maxConcurrentRequests,coreSize,maxQueueSize和queueSizeRejectionThreshold设置信号量模式下的最⼤并发量、线程池⼤⼩、缓冲区⼤⼩和缓冲区降级阈值。

```
#不设置缓冲区，当请求数超过coreSize时直接降级
hystrix.threadpool.userThreadPool.maxQueueSize=-1 #超时时间⼤于我们的timeout接⼝返回时间
hystrix.command.userCommandKey.execution.isolation.thread.timeoutInMilliseconds=15000
```

这个时候我们连续多次请求/user/command/timeout接⼝，在第⼀个请求还没有成功返回时，查看输出⽇志可以发现只有第⼀个请求正常的进⼊到user-service的接⼝中，其它请求会直接返回降级信息。这样我们就实现了对服务请求的限流。

**2.漏桶算法：**⽔（请求）先进⼊到漏桶⾥，漏桶以⼀定的速度出⽔，当⽔流⼊速度过⼤会直接溢出，可以看出漏桶算法能强⾏限制数据的传输速率。

![2020备战阿里Java岗，这20道SpringCloud面试解析不懂，等通知吧](http://p1.pstatp.com/large/pgc-image/a32eed6ba1ad40d6928bdacace20103e)



**3.令牌桶算法：**除了要求能够限制数据的平均传输速率外，还要求允许某种程度的突发传输。这时候漏桶算法可能就不合适了，令牌桶算法更为适合。**如图所示，令牌桶算法的原理是系统会以⼀个恒定的速度往桶⾥放⼊令牌，⽽如果请求需要被处理，则需要先从桶⾥获取⼀个令牌，当桶⾥没有令牌可取时，则拒绝服务。**

![2020备战阿里Java岗，这20道SpringCloud面试解析不懂，等通知吧](http://p3.pstatp.com/large/pgc-image/7692c1da8cdc417b99d6ee0004de20b2)



### **4、redis计数器限流；**

## 13. springcloud核⼼组件及其作⽤，以及springcloud⼯作原理：

![2020备战阿里Java岗，这20道SpringCloud面试解析不懂，等通知吧](http://p1.pstatp.com/large/pgc-image/3da84a69bc9d40f1834aa7d61d968ac1)



**springcloud由以下⼏个核⼼组件构成：**

- **Eureka：**各个服务启动时，Eureka Client都会将服务注册到Eureka Server，并且Eureka Client还可以反过来从Eureka Server拉取注册表，从⽽知道其他服务在哪⾥
- **Ribbon：**服务间发起请求的时候，基于Ribbon做负载均衡，从⼀个服务的多台机器中选择⼀台
- **Feign：**基于Feign的动态代理机制，根据注解和选择的机器，拼接请求URL地址，发起请求
- **Hystrix：**发起请求是通过Hystrix的线程池来⾛的，不同的服务⾛不同的线程池，实现了不同服务调⽤的隔离，避免了服务雪崩的问题
- **Zuul：**如果前端、移动端要调⽤后端系统，统⼀从Zuul⽹关进⼊，由Zuul⽹关转发请求给对应的服务

## 14. eureka的缺点：

某个服务不可⽤时，各个Eureka Client不能及时的知道，需要1~3个⼼跳周期才能感知，但是，由于基于Netflix的服务调⽤端都会使⽤Hystrix来容错和降级，当服务调⽤不可⽤时Hystrix也能及时感知到，通过熔断机制来降级服务调⽤，因此弥补了基于客户端服务发现的时效性的缺点。

## 15. eureka缓存机制：

![2020备战阿里Java岗，这20道SpringCloud面试解析不懂，等通知吧](http://p1.pstatp.com/large/pgc-image/f47b18e721984745b47cbbada0be18fa)



- **第⼀层缓存：**readOnlyCacheMap，本质上是ConcurrentHashMap：这是⼀个JVM的CurrentHashMap只读缓存，这个主要是为了供客户端获取注册信息时使⽤，其缓存更新，依赖于定时器的更新，通过和readWriteCacheMap 的值做对⽐，如果数据不⼀致，则以readWriteCacheMap 的数据为准。readOnlyCacheMap 缓存更新的定时器时间间隔，默认为30秒
- **第⼆层缓存：**readWriteCacheMap，本质上是Guava缓存：此处存放的是最终的缓存， 当服务下线，过期，注册，状态变更，都会来清除这个缓存⾥⾯的数据。 然后通过CacheLoader进⾏缓存加载，在进⾏readWriteCacheMap.get(key)的时候，⾸先看这个缓存⾥⾯有没有该数据，如果没有则通过CacheLoader的load⽅法去加载，加载成功之后将数据放⼊缓存，同时返回数据。 readWriteCacheMap 缓存过期时间，默认为 180 秒 。
- **缓存机制：**设置了⼀个每30秒执⾏⼀次的定时任务，定时去服务端获取注册信息。获取之后，存⼊本地内存。

## 16. 熔断的原理，以及如何恢复？

![2020备战阿里Java岗，这20道SpringCloud面试解析不懂，等通知吧](http://p9.pstatp.com/large/pgc-image/d82552c82c9344cf849d52a219f318fc)



**a. 服务的健康状况 = 请求失败数 / 请求总数.**

熔断器开关由关闭到打开的状态转换是通过当前服务健康状况和设定阈值⽐较决定的.

- 当熔断器开关关闭时, 请求被允许通过熔断器. 如果当前健康状况⾼于设定阈值, 开关继续保持关闭. 如果当前健康状况低于设定阈值, 开关则切换为打开状态.
- 当熔断器开关打开时, 请求被禁⽌通过.
- 当熔断器开关处于打开状态, 经过⼀段时间后, 熔断器会⾃动进⼊半开状态, 这时熔断器只允许⼀个请求通过. 当该请求调⽤成功时, 熔断器恢复到关闭状态. 若该请求失败, 熔断器继续保持打开状态, 接下来的请求被禁⽌通过.

熔断器的开关能保证服务调⽤者在调⽤异常服务时, 快速返回结果, 避免⼤量的同步等待. 并且熔断器能在⼀段时间后继续侦测请求执⾏结果, 提供恢复服务调⽤的可能。

## 17. 服务雪崩？

**简介：**服务雪崩效应是⼀种因服务提供者的不可⽤导致服务调⽤者的不可⽤,并将不可⽤逐渐放⼤的过程.

![2020备战阿里Java岗，这20道SpringCloud面试解析不懂，等通知吧](http://p1.pstatp.com/large/pgc-image/2d33f78547644117814d7f82167f386f)



**形成原因：**

- 服务提供者不可
- 重试加⼤流量
- 服务调⽤者不可⽤

**采⽤策略：**

- 流量控制
- 改进缓存模式
- 服务⾃动扩容
- 服务调⽤者降级服务

## 18. 什么是 Hystrix 断路器？我们需要它吗？

由于某些原因，employee-consumer 公开服务会引发异常。在这种情况下使用 Hystrix 我们定义了一个回退方法。如果在公开服务中发生异常，则回退方法返回一些默认值

![2020备战阿里Java岗，这20道SpringCloud面试解析不懂，等通知吧](http://p3.pstatp.com/large/pgc-image/1295bb52dce241f1895e4d2a44eca754)



中断，并且员工使用者将一起跳过 firtsPage 方法，并直接调用回退方法。 断路器的目的是给第一页方法或第一页方法可能调用的其他方法留出时间，并导致异常恢复。可能发生的情况是，在负载较小的情况下，导致异常的问题有更好的恢复机会 。

![2020备战阿里Java岗，这20道SpringCloud面试解析不懂，等通知吧](http://p1.pstatp.com/large/pgc-image/d176634898da400fbe7e9dd6f1084e48)



## 19. 多个消费者调⽤同⼀接⼝，eruka默认的分配⽅式是什么？

- RoundRobinRule:轮询策略，Ribbon以轮询的⽅式选择服务器，这个是默认值。所以示例中所启动的两个服务会被循环访问;
- RandomRule:随机选择，也就是说Ribbon会随机从服务器列表中选择⼀个进⾏访问;
- BestAvailableRule:最⼤可⽤策略，即先过滤出故障服务器后，选择⼀个当前并发请求数最⼩的;
- WeightedResponseTimeRule:带有加权的轮询策略，对各个服务器响应时间进⾏加权处理，然后在采⽤轮询的⽅式来获取相应的服务器;
- AvailabilityFilteringRule:可⽤过滤策略，先过滤出故障的或并发请求⼤于阈值⼀部分服务实例，然后再以线性轮询的⽅式从过滤后的实例清单中选出⼀个;
- ZoneAvoidanceRule:区域感知策略，先使⽤主过滤条件（区域负载器，选择最优区域）对所有实例过滤并返回过滤后的实例清单，依次使⽤次过滤条件列表中的过滤条件对主过滤条件的结果进⾏过滤，判断最⼩过滤数（默认1）和最⼩过滤百分⽐（默认0），最后对满⾜条件的服务器则使⽤RoundRobinRule(轮询⽅式)选择⼀个服务器实例。

## **20. 接⼝限流⽅法？**

- 限制 总并发数（⽐如 数据库连接池、线程池）

1. 限制 瞬时并发数（如 nginx 的 limit_conn 模块，⽤来限制 瞬时并发连接数）
2. 限制 时间窗⼝内的平均速率（如 Guava 的 RateLimiter、nginx 的 limit_req模块，限制每秒的平均速率）
3. 限制 远程接⼝ 调⽤速率
4. 限制 MQ 的消费速率
5. 可以根据⽹络连接数、⽹络流量、CPU或内存负载等来限流

## 微信公众号

**码农清风**

![](https://upload-images.jianshu.io/upload_images/11474088-febaefa23584b47f.gif?imageMogr2/auto-orient/strip)