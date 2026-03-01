### 1、 如果让你实现一个rpc, 你会考虑哪个点？ 
代理（简单易用）
协议：tcp，协议规则（请求头，状态码）
序列化，反序列化： JSON、XML、Thrift版本兼容
服务发现
负载均衡
重试机制
超时处理
身份验证
监控和日志
兼容性
拓展性

3: kafka如何做动态起停，如何做各个环境隔离？ 
###  2、如果让你设计一个线程池，你会如何处理？
核心7个参数
核心线程数
最大线程数
线程空闲时间
时间单位
任务队列

线程工厂（线程名称，优先级）
拒绝策略

### 3、spring事务的失效场景
方法没用public，事务只对public方法代理
自身调用，也没有代理
异常，事务只回滚runtimeException和error，其他不会滚
数据库，不支持事务，如mysql 的 MyISAM
传播行为配置错误
事务中使用多线程


### 4、springcloud有哪些核心组件
zuul
euraka
open feign
ribbon
Hystrix

### 5、kafka如何保证可靠性消费
生产者：ack确认机制，重试机制，消息幂等性配置
kafka集群：副本机制，数据持久化，ISR机制
消费者：偏移量手动提交，接口幂等，故障恢复

### 6、redis有哪些数据类型
String：缓存，计数器，分布式锁
hash：存储对象，缓存对象
list：消息队列，消息列表（评论，消息，文章）
set：去重，集合好友交集
sorted set：排行榜，热门商品
bitmap：二进制数组


### 7、mysql的buff pool作用
加速数据读取
减少磁盘IO
优化数据写入，先改缓存池，后持久化到磁盘
支持事务，commit才更新到磁盘
缓存索引数据


### 8.mysql事务的acid是怎么实现的
Atomicity： undo log 事务回滚
Consistency： redo undo 事务隔离机制实现
isolation：事务隔离级别，锁，MVCC实现
durability：redo log 将数据刷新到磁盘

### 9.jvm调优主要看哪些指标，如何调优
内存调优
垃圾收集器调优

### 10.redis分布锁是怎么实现的
简单的：setNx + watchdog
复杂的：redLock
redisson：hash+lua + watchdog，redLock可选



### 11.volatile的原理
内存模型
读屏障
写屏障
禁止指令重排
保证可见性，顺序性
不保证原子性

### 12、springboot的自动装配原理，有自己写过starter吗，想要实现一个starter，需要哪些核心组件
1、@EnableAutoConfigration
2、mata-inf/spirng.factories
3、条件注解，@ConditionOnClass

---

1、自动配置类，@Configuration
2、属性类，关联yml
3、mata-inf注册配置类
4、pom引入第三方依赖


### 13、有mysql的优化经验吗
数据类型
索引优化
连表查询

### 14、事务了解吗，有实际使用过吗，什么场景需要使用事务。
库存扣减
redis预热，mq消息，数据库扣减。回滚

### 15、了解设计模式吗，你说说单例模式有哪些实现方式，单例对象会被回收吗？
静态引用的存在，通常不会被垃圾回收。但如果单例模式被破坏，或者相关类被卸载等特殊情况发生，单例对象就有可能被垃圾回收器回收。


### 16、你了解jvm的垃圾回收吗，有几种垃圾回收算法
标记清除
标记整理
复制
分区算法G1


### 17、MySQL慢SQL发现机制及优化思路
- **减少 JOIN 的数据量**：在子查询中提前过滤子表数据，避免大表全量 JOIN。
- **利用索引加速过滤**：若子查询的过滤条件能命中索引，可快速缩小结果集。

### 18、如果有模糊查询的需求怎么处理
右模糊
ES
逆序手机号，有查询
