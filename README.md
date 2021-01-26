利用空余时间整理了一份《Java面试进阶核心知识点笔记》，初衷也很简单，就是希望在面试的时候能够帮助到大家，减轻大家的负担和节省时间。

之前有分享过这份知识点笔记的初稿，现在又对知识点笔记进行了一定的优化。于是有了现在的V2.0版本的面试手册。当然除了在线版还有本地文档版本


>部分内容收集整理于网络，在此也再次感谢所有内容产出者的贡献！
>
>> **如果觉得看起来比较麻烦，需要PDF版本，或是需要更多学习资料、面试资料，进阶、架构资料，都可以加上[QQ群](#contanct-me)领取。祝愿每一位有追求的Java开发同胞都能进大厂拿高薪！**

Java架构交流QQ群：**930254941**  （备注一下GitHub，免得被认成打无良广告的）

快捷加群方式：[点击此处加入群聊Java架构交流群](https://jq.qq.com/?_wv=1027&k=Xu0ju5PW)

![](https://upload-images.jianshu.io/upload_images/11474088-f15f3310f6b7610f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# Java-review-Gudie
【Java快速面试指南目录】Java基础、异常、集合、并发编程、JVM、Spring全家桶、MyBatis、Redis、数据库、中间件MQ、Dubbo、Linux、Tomcat、ZooKeeper、Netty等等。包含了作为一个Java工程师在面试中需要用到或者可能用到的绝大部分知识。欢迎大家阅读，持续更新中…

| 序号 | 内容               | 链接地址                                 |
| ---- | ------------------ | ---------------------------------------- |
| 1    | **Java基础**       | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/Java%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 2    | **Java集合容器**   | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/Java%E9%9B%86%E5%90%88%E5%AE%B9%E5%99%A8%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 3    | **Java异常**       | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/Java%E5%BC%82%E5%B8%B8%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 4    | **并发编程**       | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/Java%E5%B9%B6%E5%8F%91%E7%BC%96%E7%A8%8B%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 5    | **JVM**            | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/JVM%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 6    | **Spring**         | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/Spring%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 7    | **Spring MVC**     | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/SpringMVC%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 8    | **Spring Boot**    | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/SpringBoot%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 9    | **Spring Cloud**   | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/Spring%20Cloud%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 10   | **MyBatis**        | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/MyBatis%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 11   | **Redis**          | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/Redis%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 12   | **MySQL**          | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/MySQL%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 13   | **RabbitMQ**       | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/RabbitMQ%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 14   | **Dubbo**          | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/Dubbo%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 15   | **Linux**          | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/Linux%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 16   | **Tomcat**         | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/Tomcat%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 17   | **ZooKeeper**      | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/zookeeper%E9%9D%A2%E8%AF%95.md) |
| 18   | **Netty**          | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/Netty%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 19   | **架构设计**       | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/%E6%9E%B6%E6%9E%84%E8%AE%BE%E8%AE%A1%26%E5%88%86%E5%B8%83%E5%BC%8F%26%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 20   | **大厂数据库**     | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/%E5%A4%A7%E5%8E%82%E6%95%B0%E6%8D%AE%E5%BA%93%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 21   | **设计模式**       | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F.md) |
| 22   | **计算机网络基础** | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C%E5%9F%BA%E7%A1%80.md) |
| 23   | **常见面试算法题** | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/%E5%B8%B8%E8%A7%81%E9%9D%A2%E8%AF%95%E7%AE%97%E6%B3%95%E9%A2%98.md) |
| 24   | **Kafka**          | [:mag:点击直达](https://github.com/ThinkingHan/Java-review-gudie/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%98%E9%9B%86/Kafka%E9%9D%A2%E8%AF%95%E9%A2%98.md) |
| 25   | **完整离线版**     | [:mag:点击直达](#完整离线版) |

# 完整离线版

![](https://upload-images.jianshu.io/upload_images/11474088-47be2144bb66cd11.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

------

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
>>平常很忙，加小夕小姐姐微信领取就好了，免费获取的！

![](https://upload-images.jianshu.io/upload_images/11474088-d4fa503624f05687.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 微信公众号

**阿风的架构笔记**

![](https://upload-images.jianshu.io/upload_images/11474088-91d39d0545be561d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
