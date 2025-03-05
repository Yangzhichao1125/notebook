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

3.jvm调优主要看哪些指标，如何调优
4.redis分布锁是怎么实现的
5.volatile的原理
sprinhboot的自动装配原理，有自己写过starter吗，想要实现一个starter，需要哪些核心组件
redis的使用场景，sorted set你在什么场景下使用过
redis的分布式锁有了解过吗
有mysql的优化经验吗
事务了解吗，有实际使用过吗，什么场景需要使用事务。
了解设计模式吗，你说说单例模式有哪些实现方式，单例对象会被回收吗？
你了解jvm的垃圾回收吗，有几种垃圾回收算法
1. HashMap为什么使用红黑树，对比二叉平衡树，对比二叉树
2. MySQL为什么使用B+树
3. MySQL慢SQL发现机制及优化思路
4. MySQL事务隔离级别
5. 如果有模糊查询的需求怎么处理
6. 数据刷到ES后是否一定能够查询到
7. RocketMQ消息队列与消费者相关