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

作为一个后端开发人员，不只是要求开发人员需要掌握 Redis，也要求运维人员也要懂 Redis。由于 Redis 的运用广泛，我们也知道它的重要性，至此面试中经常被问到。
**用XMind画了一张导图记录Redis的学习笔记和一些面试解析及视频链接（源文件对部分节点有详细备注和参考资料，欢迎关注我的公众号：以Java架构赢天下 后台发送【Redis】拿下载链接，已经完善更新）：**
![](https://upload-images.jianshu.io/upload_images/11474088-409a2bc6e3f17f9a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## **一、Redis数据结构相关**
### **1.Redis 支持的数据类型**

**String字符串**

>**格式:**set key value
>string类型是二进制安全的。意思是redis的string可以包含任何数据。比如jpg图片或者序列化的对象 。
>string类型是Redis最基本的数据类型，一个键最大能存储512MB。

 **Hash（哈希）**

>**格式:** hmset name  key1 value1 key2 value2
>Redis hash 是一个键值(key=>value)对集合。
>Redis hash是一个string类型的field和value的映射表，hash特别适合用于存储对象。

 **List（列表）**
>Redis 列表是简单的字符串列表，按照插入顺序排序。你可以添加一个元素到列表的头部（左边）或者尾部（右边）
>**格式:**lpush  name  value
>在 key 对应 list 的头部添加字符串元素
>**格式:**rpush  name  value
>在 key 对应 list 的尾部添加字符串元素
>**格式:**lrem name  index
>key 对应 list 中删除 count 个和 value 相同的元素
>**格式:**llen name  
>返回 key 对应 list 的长度

**Set（集合）**

>**格式:**sadd  name  value
>Redis的Set是string类型的无序集合。
>集合是通过哈希表实现的，所以添加，删除，查找的复杂度都是O(1)。

**zset(sorted set：有序集合)**

>**格式:**zadd  name score value
>Redis zset 和 set 一样也是string类型元素的集合,且不允许重复的成员。
>不同的是每个元素都会关联一个double类型的分数。redis正是通过分数来为集合中的成员进行从小到大的排序。
>zset的成员是唯一的,但分数(score)却可以重复。

![](https://upload-images.jianshu.io/upload_images/11474088-6e4ca14ebdc13dc6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### **2.Redis有哪些常用的命令？**
[Redis命令大全](https://www.redis.net.cn/order/)

### **3.Redis有哪些应用场景**
[面试题：Redis的应用场景核心设计，看完面试不在慌！](https://juejin.im/post/5e675a88f265da5741121540)

## 二、Redis事务
### 1.**什么是事务**

Redis 中的事务是一组命令的集合，是 Redis 的最小执行单位，一个事务要么都执行，要么都不执行。**带有以下三个重要的保证：**
1. 批量操作在发送 EXEC 命令前被放入队列缓存。
1. 收到 EXEC 命令后进入事务执行，事务中任意命令执行失败，其余的命令依然被执行。
1. 在事务执行过程，其他客户端提交的命令请求不会插入到事务执行命令序列中。

**Redis 事务的原理是**先将属于一个事务的命令发送给 Redis，然后依次执行这些命令。

### **2.为什么redis事务不具备原子性**
>单个 Redis 命令的执行是原子性的，但 Redis 没有在事务上增加任何维持原子性的机制，所以 Redis 事务的执行并不是原子性的。
>事务可以理解为一个打包的批量执行脚本，但批量指令并非原子化的操作，中间某条指令的失败不会导致前面已做指令的回滚，也不会造成后续的指令不做。

### **3. Redis 事务相关命令有哪些？**
>**DISCARD：**取消事务，放弃执行事务块内的所有命令。
>**EXEC：**执行所有事务块内的命令。
>**MULTI：**标记一个事务块的开始。
>**WATCH:**Redis Watch 命令用于监视一个(或多个) key ，如果在事务执行之前这个(或这些) key 被其他命令所改动，那么事务将被打断
>**UNWATCH ：**取消 WATCH 命令对所有 key 的监视。

## 三、Redis持久化和缓存管理
### **1.Redis持久化是什么？**
>用一句话可以将持久化概括为：将数据(如内存中的对象)保存到可永久保存的存储设备中。
>持久化的主要应用是将内存中的对象存储在数据库中，或者存储在磁盘文件中、 XML 数据文件中等等。
>也可以从如下两个层面来理解持久化：
>**应用层：**如果关闭( Close )你的应用，然后重新启动则先前的数据依然存在。
>**系统层：**如果关闭( Shut Down )你的系统(电脑)，然后重新启动则先前的数据依然存在。

### **2.Redis 持久化机制有哪些？**

>Redis 提供两种方式进行持久化。
>**RDB 持久化：**原理是将 Reids 在内存中的数据库记录定时 dump 到磁盘上的 RDB 持久化。
>**AOF（append only file）持久化：**原理是将 Redis 的操作日志以追加的方式写入文件。

### **3.Redis 持久化机制 AOF 和 RDB 有什么区别？**

aof，rdb是两种 redis持久化的机制。用于crash后，redis的恢复。
**rdb的特性如下：**
- fork一个进程，遍历hash table，利用copy on write，把整个db dump保存下来。
- save, shutdown, slave 命令会触发这个操作。
- 粒度比较大，如果save, shutdown, slave 之前crash了，则中间的操作没办法恢复。

**aof有如下特性：**
- 把写操作指令，持续的写到一个类似日志文件里。（类似于从postgresql等数据库导出sql一样，只记录写操作）
- 粒度较小，crash之后，只有crash之前没有来得及做日志的操作没办法恢复。

**两种区别就是，**一个是持续的用日志记录写操作，crash后利用日志恢复；一个是平时写操作的时候不触发写，只有手动提交save命令，或者是关闭命令时，才触发备份操作。
选择的标准，就是看系统是愿意牺牲一些性能，换取更高的缓存一致性（aof），还是愿意写操作频繁的时候，不启用备份来换取更高的性能，待手动运行save的时候，再做备份（rdb）。rdb这个就更有些 eventually consistent的意思了。

### **4.RDB和AOF 持久化机制的优缺点**

**RDB优点**
- RDB 是紧凑的二进制文件，比较适合备份，全量复制等场景
- RDB 恢复数据远快于 AOF

**RDB缺点**
- RDB 无法实现实时或者秒级持久化；
- 新老版本无法兼容 RDB 格式。

**AOF优点**
- 可以更好地保护数据不丢失；
- appen-only 模式写入性能比较高；
- 适合做灾难性的误删除紧急恢复。

**AOF缺点：**
- 对于同一份文件，AOF 文件要比 RDB 快照大；
- AOF 开启后，会对写的 QPS 有所影响，相对于 RDB 来说 写 QPS 要下降；
- 数据库恢复比较慢， 不合适做冷备。

### **5.Redis 淘汰策略有哪些？**

Redis的内存淘汰策略是指在Redis的用于缓存的内存不足时，怎么处理需要新写入且需要申请额外空间的数据。

**Redis 的缓存淘汰策略有：**
>**noeviction：**当内存不足以容纳新写入数据时，新写入操作会报错。
>**allkeys-lru:**当内存不足以容纳新写入数据时，在键空间中，移除最近最少使用的key。
>**allkeys-random:**当内存不足以容纳新写入数据时，在键空间中，随机移除某个key。
>**volatile-lru:**当内存不足以容纳新写入数据时，在设置了过期时间的键空间中，移除最近最少使用的key。
>**volatile-random:**当内存不足以容纳新写入数据时，在设置了过期时间的键空间中，随机移除某个key。

### **6.Redis 缓存失效策略有哪些？**

**定时过期策略**

每个设置过期时间的key都需要创建一个定时器，到过期时间就会立即清除。该策略可以立即清除过期的数据，对内存很友好；但是会占用大量的CPU资源去处理过期的数据，从而影响缓存的响应时间和吞吐量。

**惰性过期策略**

只有当访问一个key时，才会判断该key是否已过期，过期则清除。该策略可以最大化地节省CPU资源，却对内存非常不友好。极端情况可能出现大量的过期key没有再次被访问，从而不会被清除，占用大量内存。

**定期过期策略**

每隔一定的时间，会扫描一定数量的数据库的expires字典中一定数量的key，并清除其中已过期的key。该策略是前两者的一个折中方案。通过调整定时扫描的时间间隔和每次扫描的限定耗时，可以在不同情况下使得CPU和内存资源达到最优的平衡效果。

**Redis中同时使用了惰性过期和定期过期两种过期策略。**

所谓定期删除，指的是 redis 默认是每隔 100ms 就随机抽取一些设置了过期时间的 key，检查其是否过期，如果过期就删除。

**假设 redis 里放了 10w 个 key，都设置了过期时间，**你每隔几百毫秒，就检查 10w 个 key，那 redis 基本上就死了，cpu 负载会很高的，消耗在你的检查过期 key 上了。**注意，**这里可不是每隔 100ms 就遍历所有的设置过期时间的 key，那样就是一场性能上的灾难。实际上 redis 是每隔 100ms 随机抽取一些 key 来检查和删除的。

**但是问题是，定期删除可能会导致很多过期 key 到了时间并没有被删除掉，那咋整呢？**所以就是惰性删除了。这就是说，在你获取某个 key 的时候，redis 会检查一下 ，这个 key 如果设置了过期时间那么是否过期了？如果过期了此时就会删除，不会给你返回任何东西。

**获取 key 的时候，如果此时 key 已经过期，就删除，不会返回任何东西。**但是实际上这还是有问题的，如果定期删除漏掉了很多过期 key，然后你也没及时去查，也就没走惰性删除，此时会怎么样？如果大量过期 key 堆积在内存里，导致 redis 内存块耗尽了，咋整？**答案是：走内存淘汰机制。**

## 四、Redis缓存异常方案

![](https://upload-images.jianshu.io/upload_images/11474088-d3276378ebe8a058.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### **1.缓存雪崩**

#### **1.1、什么是缓存雪崩？**

如果缓存集中在一段时间内失效，发生大量的缓存穿透，所有的查询都落在数据库上，造成了缓存雪崩由于原有缓存失效，新缓存未到期间所有原本应该访问缓存的请求都去查询数据库了，而对数据库CPU和内存造成巨大压力，严重的会造成数据库宕机。

举例来说， 我们在准备一项抢购的促销运营活动，活动期间将带来大量的商品信息、库存等相关信息的查询。 为了避免商品数据库的压力，将商品数据放入缓存中存储。 不巧的是，抢购活动期间，大量的热门商品缓存同时失效过期了，导致很大的查询流量落到了数据库之上。对于数据库来说造成很大的压力。

#### **1.2、有什么解决方案来防止缓存雪崩？**

> **1、加锁排队**
>
> mutex互斥锁解决，Redis的SETNX去set一个mutex key，当操作返回成功时，再进行加载数据库的操作并回设缓存，否则，就重试整个get缓存的方法
>
> **2、数据预热**
>
> 缓存预热就是系统上线后，将相关的缓存数据直接加载到缓存系统。这样就可以避免在用户请求的时候，先查询数据库，然后再将数据缓存的问题。用户直接查询事先被预热的缓存数据。可以通过缓存reload机制，预先去更新缓存，再即将发生大并发访问前手动触发加载缓存不同的key
>
> **3、双层缓存策略**
>
> C1为原始缓存，C2为拷贝缓存，C1失效时，可以访问C2，C1缓存失效时间设置为短期，C2设置为长期
>
> **4、定时更新缓存策略**
>
> 实效性要求不高的缓存，容器启动初始化加载，采用定时任务更新或移除缓存
>
> **5、设置不同的过期时间，让缓存失效的时间点尽量均匀**

### **2.缓存预热**

#### **2.1.什么是缓存预热**

缓存预热就是系统上线后，将相关的缓存数据直接加载到缓存系统。这样就可以避免在用户请求的时候，先查询数据库，然后再将数据缓存的问题。**用户直接查询事先被预热的缓存数据。如图所示：**

![](https://upload-images.jianshu.io/upload_images/11474088-95aa0d0d1e375adb?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如果不进行预热， 那么 Redis 初识状态数据为空，系统上线初期，对于高并发的流量，都会访问到数据库中， 对数据库造成流量的压力。

#### **2.2.有什么解决方案？**

1.  数据量不大的时候，工程启动的时候进行加载缓存动作；
2.  数据量大的时候，设置一个定时任务脚本，进行缓存的刷新；
3.  数据量太大的时候，优先保证热点数据进行提前加载到缓存。

### **3.缓存穿透**

#### **3.1、什么是缓存穿透？**

缓存穿透是指用户查询数据，在数据库没有，自然在缓存中也不会有。这样就导致用户查询的时候，在缓存中找不到对应key的value，每次都要去数据库再查询一遍，然后返回空（相当于进行了两次无用的查询）。这样请求就绕过缓存直接查数据库

#### **3.2、有什么解决方案来防止缓存穿透？**

> **1、缓存空对象**
>
> 简单粗暴的方法，如果一个查询返回的数据为空（不管是数据不存在，还是系统故障），我们仍然把这个空结果进行缓存，但它的过期时间会很短，最长不超过五分钟。
>
> **2、布隆过滤器**
>
> **优势：**占用内存空间很小，位存储；性能特别高，使用key的hash判断key存不存在
> 将所有可能存在的数据哈希到一个足够大的bitmap中，一个一定不存在的数据会被 这个bitmap拦截掉，从而避免了对底层存储系统的查询压力

### **4.缓存降级**

降级的情况，就是缓存失效或者缓存服务挂掉的情况下，我们也不去访问数据库。我们直接访问内存部分数据缓存或者直接返回默认数据。

**举例来说：**

> 对于应用的首页，一般是访问量非常大的地方，首页里面往往包含了部分推荐商品的展示信息。这些推荐商品都会放到缓存中进行存储，同时我们为了避免缓存的异常情况，对热点商品数据也存储到了内存中。同时内存中还保留了一些默认的商品信息。如下图所示：

![](https://upload-images.jianshu.io/upload_images/11474088-ed755e56c92703f8?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

降级一般是有损的操作，所以尽量减少降级对于业务的影响程度。

###**5.缓存击穿**

#### **5.1、什么是缓存击穿？**

缓存击穿是指缓存中没有但数据库中有的数据（一般是缓存时间到期），这时由于并发用户特别多，同时读缓存没读到数据，又同时去数据库去取数据，引起数据库压力瞬间增大，造成过大压力

#### **5.2、会带来什么问题**

会造成某一时刻数据库请求量过大，压力剧增

#### **5.3、如何解决**

##### **5.3.1.使用互斥锁(mutex key)**
这种解决方案思路比较简单，就是只让一个线程构建缓存，其他线程等待构建缓存的线程执行完，重新从缓存获取数据就可以了。 如果是单机，可以用synchronized或者lock来处理，如果是分布式环境可以用分布式锁就可以了（分布式锁，可以用memcache的add, redis的setnx, zookeeper的添加节点操作）。
![](https://upload-images.jianshu.io/upload_images/11474088-0b556254199dec9a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### **5.3.2."永远不过期"**

1. 从redis上看，确实没有设置过期时间，这就保证了，不会出现热点key过期问题，也就是“物理”不过期。
2. 从功能上看，如果不过期，那不就成静态的了吗？所以我们把过期时间存在key对应的value里，如果发现要过期了，通过一个后台的异步线程进行缓存的构建，也就是“逻辑”过期
![](https://upload-images.jianshu.io/upload_images/11474088-05ba12eea39351bc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### **5.3.3.缓存屏障**
该方法类似于方法一：使用countDownLatch和atomicInteger.compareAndSet()方法实现轻量级锁
```
class MyCache{

    private ConcurrentHashMap<String, String> map;

    private CountDownLatch countDownLatch;

    private AtomicInteger atomicInteger;

    public MyCache(ConcurrentHashMap<String, String> map, CountDownLatch countDownLatch,
                   AtomicInteger atomicInteger) {
        this.map = map;
        this.countDownLatch = countDownLatch;
        this.atomicInteger = atomicInteger;
    }

    public String get(String key){

        String value = map.get(key);
        if (value != null){
            System.out.println(Thread.currentThread().getName()+"\t 线程获取value值 value="+value);
            return value;
        }
        // 如果没获取到值
        // 首先尝试获取token，然后去查询db，初始化化缓存；
        // 如果没有获取到token，超时等待
        if (atomicInteger.compareAndSet(0,1)){
            System.out.println(Thread.currentThread().getName()+"\t 线程获取token");
            return null;
        }

        // 其他线程超时等待
        try {
            System.out.println(Thread.currentThread().getName()+"\t 线程没有获取token，等待中。。。");
            countDownLatch.await();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        // 初始化缓存成功，等待线程被唤醒
        // 等待线程等待超时，自动唤醒
        System.out.println(Thread.currentThread().getName()+"\t 线程被唤醒，获取value ="+map.get("key"));
        return map.get(key);
    }

    public void put(String key, String value){

        try {
            Thread.sleep(2000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        map.put(key, value);

        // 更新状态
        atomicInteger.compareAndSet(1, 2);

        // 通知其他线程
        countDownLatch.countDown();
        System.out.println();
        System.out.println(Thread.currentThread().getName()+"\t 线程初始化缓存成功！value ="+map.get("key"));
    }

}

class MyThread implements Runnable{

    private MyCache myCache;

    public MyThread(MyCache myCache) {
        this.myCache = myCache;
    }

    @Override
    public void run() {
        String value = myCache.get("key");
        if (value == null){
            myCache.put("key","value");
        }

    }
}

public class CountDownLatchDemo {
    public static void main(String[] args) {

        MyCache myCache = new MyCache(new ConcurrentHashMap<>(), new CountDownLatch(1), new AtomicInteger(0));

        MyThread myThread = new MyThread(myCache);

        ExecutorService executorService = Executors.newFixedThreadPool(5);
        for (int i = 0; i < 5; i++) {
            executorService.execute(myThread);
        }
    }
}
```
## 五、Redis集群架构

### **1.实现主从复制的两种方式**

#### **1.1slaveof命令**
- 建立主从命令：slaveof ip port
- 取消主从命令：slaveof no one

#### **1.2.redis.conf配置文件配置**
- 格式：slaveof ip port
- 从节点只读：slave-read-only yes #配置只读

### **2.复制过程了解吗，讲一讲**

1. 从节点执行 slaveof 命令。  
1. 从节点只是保存了 slaveof 命令中主节点的信息，并没有立即发起复制。      
1. 从节点内部的定时任务发现有主节点的信息，开始使用 socket 连接主节点。    
1. 连接建立成功后，发送 ping 命令，希望得到 pong 命令响应，否则会进行重连。 
1. 如果主节点设置了权限，那么就需要进行权限验证，如果验证失败，复制终止。       
1. 权限验证通过后，进行数据同步，这是耗时最长的操作，主节点将把所有的数据全部发送给从节点。 
1. 当主节点把当前的数据同步给从节点后，便完成了复制的建立流程。接下来，主节点就会持续的把写命令发送给从节点，保证主从数据一致性。

### **3.redis的主从结构**

>主从结构一是可以进行冗余备份,二是可以实现读写分离
>**主从复制**
>冗余备份(还可以称为:主从复制,数据冗余,数据备份,可以实现容灾快速恢复)
>持久化保证了即使redis服务重启也会丢失数据，因为redis服务重启后会将硬盘上持久化的数据恢复到内存中，但是当redis服务器的硬盘损坏了可能会导致数据丢失，如果通过redis的主从复制机制就可以避免这种单点故障. 例如:我们搭建一个主叫做redis0,两个从,分别叫做redis1和redis2,即使一台redis服务器宕机其它两台redis服务也可以继续提供服务。主redis中的数据和从redis上的数据保持实时同步，当主redis写入数据时通过主从复制机制会复制到两个从redis服务上。
>1.一个Master可以有多个Slave,不仅主服务器可以有从服务器，从服务器也可以有自己的从服务器
>2.复制在Master端是非阻塞模式的，这意味着即便是多个Slave执行首次同步时，Master依然可以提供查询服务；
>3.复制在Slave端也是非阻塞模式的：如果你在redis.conf做了设置，Slave在执行首次同步的时候仍可以使用旧数据集提供查询；你也可以配置为当Master与Slave失去联系时，让Slave返回客户端一个错误提示；
>4.当Slave要删掉旧的数据集，并重新加载新版数据时，Slave会阻塞连接请求
>**读写分离**
>主从架构中，可以考虑关闭主服务器的数据持久化功能，只让从服务器进行持久化，这样可以提高主服务器的处理性能。从服务器通常被设置为只读模式，这样可以避免从服务器的数据被误修改。

### **4.什么是Redis 慢查询？怎么配置？**
>慢查询就是指，系统执行命令之后，计算统计每条指令执行的时间，如果执行时间超过设置的阈值，就说明该命令为慢指令。
>**Redis 慢查询配置参数为：**
>slowlog-log-slower-than：设置慢查询定义阈值，超过这个阈值就是慢查询。单位为微妙，默认为 10000。
>slowlog-max-len：慢查询的日志列表的最大长度，当慢查询日志列表处于最大长度的时候，最早插入的一个命令将从列表中移除。

### **5.Redis 有哪些架构模式？讲讲各自的特点**

主从模式，一般是一个主节点，一或多个从节点，为了保证我们的主节点宕机后，数据不丢失，我们将主节点的数据备份到从节点，从节点并不进行实际操作，只做实时同步操作，并不能起到高并发的目的。

![](https://upload-images.jianshu.io/upload_images/11474088-105b06979be3c851.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

哨兵模式，一个哨兵集群和一组主从架构组成。比主从更好的是当我们的主节点宕机以后，哨兵会主动选举出一个主节点继续向外提供服务。

![](https://upload-images.jianshu.io/upload_images/11474088-4d7071b29c120a9e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

集群架构，由很多个小主从聚集在一起，一起向外提供服务的，将16384个卡槽切分存储，并不是一个强一致性的集群架构，每一个小主从节点内会存在选举机制，保证对外的高可用架构。

## **六、Redis分布式锁**

有时候讲出来的更通俗
[Redis分布式锁正确实现视频讲解](https://www.bilibili.com/video/av90214360)

## 微信公众号

**码农清风**

![](https://upload-images.jianshu.io/upload_images/11474088-febaefa23584b47f.gif?imageMogr2/auto-orient/strip)