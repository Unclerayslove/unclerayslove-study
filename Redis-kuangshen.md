**==NoSQL：Not only SQL==**

# NoSQL的四大分类：

## KV键值对

- 新浪：Redis

- 美团：Redis+Tair
- 阿里、百度：Redistribution+memecache

## 文档型数据库（bson格式和json一样）

- MongoDB（一般必须要掌握）
  - 基本分布式文件存储的数据库，C++编写，主要用来处理大量的文档
  - 介于关系型数据库和非关系型数据中间的产品。MongoDB是非关系型数据库中功能最丰富，最像关系型数据库的！
- ConyhDB

## 列存储数据库

- HBase
- 分布式文件系统

## 图关系数据库

- 他不是存图形的，放的是关系。比图：朋友圈社交网络、广告推荐！
- Neo4j，InfoGrid

# Redis入门

## 概述

> 什么是Redis？

Redis（**Re**mote **Di**ctionary **S**erver )，即远程字典服务，是一个开源的使用ANSI [C语言](https://baike.baidu.com/item/C语言)编写、支持网络、可基于内存亦可持久化的日志型、Key-Value[数据库](https://baike.baidu.com/item/数据库/103728)，并提供多种语言的API。

免费和开源！是当下最热门的NoSQL技术之一！也被人们称之为结构化数据库！

> Redis能干嘛？

1. 内存存储、持久化，内存中是断电即失，所以说持久化很重要（rdb、aof）
2. 效率高，可以用于高速缓存
3. 发布订阅系统
4. 地图信息分析
5. 计时器、计数器（浏览量、点赞数等）
6. ......

> 特性

1. 多样的数据类型
2. 持久化
3. 集群
4. 事务
5. .......



Redis推荐都是在Linux服务器上搭建的！

## Windows安装

1、下载安装包：https://github.com/microsoftarchive/redis/releases（如果被禁止，那就去找百度网盘吧）

2、下载完毕得到压缩包

3、解压到自己电脑上的环境目录下就可以了（作为程序员，环境目录一定要工工整整：如D:\Environment，这个目录下放所有的环境配置文件或者软件）；Redis十分的小，只有5M

![image-20201018155724586](C:\Users\mi\AppData\Roaming\Typora\typora-user-images\image-20201018155724586.png)

4、开启Redis，双击运行服务即可

5、使用Redis客户端来连接redis

Windows下使用简单，但Redis推荐我们使用Linux去开发使用

## Linux安装

1、下载安装包！`redis-5.0.8.tar.gz`

2、上传到远程服务器（比如一般是/home目录下）；可以选择mv到/opt目录下（临时文件）解压Redis的安装包

```bash
/home/user【用户名】   
```

3、进入解压后的文件，可以看到Redis的配置文件

```bash
cd redis-5.0.8
# 有标准的配置文件redis.conf 以及其他文件
# 解压之后只是一个程序，没有redis-server rdis-cli 需要安装后才有
```

4、基本的环境安装

~~~bash
yum install gcc-c++（有gcc就不用安装）

# 
make
make install（确认安装）
~~~

5、redis的默认安装路径`/usr/local/bin`

6、将redis配置文件（解压路径下的redis.conf）。复制到我们当前目录下（需要使用的目录下，对副本进行操作，而不修改原生的配置文件，比如：myconfig/）

7、 redis默认不是后台启动的，修改配置文件！

在redis.conf配置文件中有一个`daemonize`（守护进程，即后台进程）属性，默认是`no`；改成`yes`

8、启动Redis服务

切换到默认安装目录下`/usr/local/bin`

~~~bash
cd /usr/local/bin
redis-server myconfig/redis.conf #通过指定的配置文件启动服务

~~~

9、使用redis-cli进行连接测试

~~~bash
redis-cli -p 6379 #连接客户端
~~~

10、查看redis进程是否开启

~~~bash
ps -ef | grep redis
~~~

11、如何关闭Redis服务呢？`shutdown`

~~~bash
 # redis-cli shutdown
 # 在连接客户端的情况下，shutdown，然后exit推出
 # 或者通过ps -ef|grep redis 查看进程端口号， 用kill -9 进程pid
~~~



## 测试性能

**redis-benchmark**是一个压力测试工具

官方自带的性能测试工具

相关博客：https://www.cnblogs.com/williamjie/p/11303965.html

~~~bash
#压测命令
redis-benchmark -h 127.0.0.1 -p 6379 -c 50 -n 10000
~~~



## 基础的知识

redis默认有16个数据库

index 0-15

select index 切换数据库

dbsize 查看数据库大小

清除当前数据库 ：flushdb  

清空全部数据库内容： flushall



> Redis是单线程的

Redis是很快的，官方表示，Redis是基于内存操作，CPU不是Redis性能瓶颈。Redis的瓶颈是根据机器的内存和网络带宽，既然可以使用单线程来实现，就使用单线程了

Redis是C语言写的，官方提供的数据为：100_000+的QPS，这个不必Memecache差

Redis为什么单线程还这么快？

1、误区1：高性能的服务器一定是多线程的？

2、误区2：多线程（CPU上下文会切换）一定比单线程效率高！

CPU > 内存 > 硬盘的速度要有所了解

核心：redis是将所有的数据全部放在==内存==中的，所以说使用单线程去操作效率就是高的，多线程（CPU上下文会切换：耗时的操作！！！），对于内存系统来说，如果没有上下文切换效率就是最高的！ 多次读写都是在一个CPU上的，在内存情况下，这个就是最佳的方案



# 五大数据类型

> 官网文档

![image-20201018220152572](C:\Users\mi\AppData\Roaming\Typora\typora-user-images\image-20201018220152572.png)

全段翻译：

Redis是一个开源（BSD许可），内存中的数据结构存储，用作**数据库**、**缓存**和**消息中间件（MQ）**。它支持数据结构，如字符串、哈希、列表、集合、带范围查询的排序集、位图、超日志、带有radius查询和流的地理空间索引。**Redis内置了复制、Lua脚本、LRU逐出、事务和不同级别的磁盘持久性**，并通过Redis Sentinel和Redis Cluster自动分区来提供高可用性。了解更多

## Redis-key

```bash
keys *

set key value

get key

#判断key是否存在
exists key [key...]

#移除数据库的某个值：
move key db

expire key seconds

ttl key #查看当前key的过期剩余时间

type key #查看当前key的类型
```



## String

~~~bash
#追加字符串
append key value #如果当前key不存在就相当于set一个key
#字符长度
strlen key
#截取字符串
getrange key start end
#替换
setrange key offset value
# 自增 +1
incr key
# 自减 -1
decr key
# 设定指定的增长量
incrby key increment # 比如可以设置步长
# 设定指定的减量
decrby key decrement

# 字符串范围range
getrange key start end # getrange key 0 -1  相当于 get key

# 替换！！
setrange key offset value # 替换指定位置开始的字符串！！

#setex(set with expire) 设置过期时间
setex key seconds value
#setnx(set if not expire)不存在设置（分布式锁中常常用到）
setnx key value

#批量设置，同时设置多个值
mset key value [key value ...]
msetnx #是一个原子性的操作，要么全部成功，要么全部失败
#同时获取多个值
mget key [key ...]


# 对象
set user:1 {name:zhangsan,age:3}#设置一个user:1对象，值为json字符串来保存一个对象

#先获取在设置
getset key value#如果不存在值，则返回nil；如果存在值，获取原来的值，并设置新的值
~~~

数据结构是相通的

String类似的使用场景：value除了是我们的字符串还可以是我们的数字

- 计数器
- 统计多单位的数量 如：uid:999999:follow 0 
- 粉丝数
- 对象缓存存储

## List

基本的数据类型，列表

在redis里面，我们可以把list完成 栈、队列、阻塞队列！

所有的list命令都是用L开头的

```bash
Lpush key value [value ...]#将一个值或多个值，插入到列表的头部（左边）；类似于 数据结构栈 先进后出

Rpush key value [value ...]#将一个值或多个值，插入到列表的尾部（右边）；类似于 数据结构队列 先进先出

Lrange key start stop #获取全部 lrange key 0 -1

############################################################################
Lpop key	#移除列表的第一个元素

Rpop key	#移除列表的最后一个元素

############################################################################

Lindex key index	#通过下标index获取列表的某一个值

Llen	#返回列表的长度

############################################################################
Lrem key count value	#移除list集合中指定个数的value（因为list集合可以有重复的值）	

############################################################################
trim 修剪  list 截断

Ltrim key start stop		#截取指定的长度，这个list已经被改变了，截断了只剩下截取的元素
############################################################################
RpopLpush source destination	#移除列表的最后一个元素，将它移动到新的列表中

############################################################################
Lset 将列表中指定下标的值替换为另外一个值，更新操作
Lset key index value	#如果不存在列表我们去更新就会报错（如果索引越界也会报错）

#pivot 支点 中心轴
Linsert key before|after pivot value	#将某个具体的值插入到指定的某个元素前面或者后面


```

> 小结

- 它实际上是一个链表（双端），before Node after ， left， right 都可以插入值
- 如果key不存在，创建新的链表
- 如果key存在，新增内容
- 如果移除了所有值，空链表，也代表不存在
- 在两边插入或者改动值，效率最高（O(1)）中间元素，相对来说效率会低一点

消息队列（Lpush  Rpop）  左边插入，右边获取 ，  栈（Lpush Lpop 先进后出）

## Set

Set命令以S开头；Set集合中的元素是不重复的

~~~bash
Sadd key member [member ...]	#向set中添加元素

Smembers key	#查看指定set的所有值

Sismember key member	#判断某个元素是否在set中

Scard key	#获取set集合中的内容元素个数

Srem key member [member ...]	#移除set中的某个元素/多个元素

############################################################################
set 无序不重复集合。抽随机！
Srandmember key	#随机抽选出一个元素

Srandmember key [count]	#随机抽选出指定个数的元素

删除指定的key 随机删除key
spop key [count] #随机删除一些set集合中的元素


smove source destination member	#将一个指定的值，移动到另外一个set集合

############################################################################
数字集合类：
 - 差集
 - 交集
 - 并集
 
sdiff key [key ...]		#差集 A与B的差集：A-B   B与A的差集：B-A

sinter key [key ...]	#交集	共同好友就可以这样实现

sunion key [key ...]	#并集

~~~

微博，A用户将所有关注的人放在一个set集合中！将他的粉丝也放在一个set集合中！

共同关注，共同爱好，二度好友（六度分割理论）



## Hash

Map集合，key-map！这时候这个值是一个map集合！本质和String类型没有太大区别，还是一个简单的<key-value>！

以h开头

~~~bash
hset key field value
hget key field

hmset key field value [field value ...]	#向哈希中设置多个字段值
hmget key field [field ...]	#获取哈希中多个字段的值

hgetall key	#获取哈希中的所有值

hdel key field [field ...]	#删除哈希指定key字段，对应的value也消失了

hlen key	#获取哈希表的字段数量

hexists key field	#判断哈希中的key 的字段是否存在

############################################################################
hkeys key	# 只获取所有的field
hvals key	# 只获取所有的value

hincrby key filed increment	#指定增量
hincrby myhash filed1 5

hsetnx key field value	#如果不存在则可以设置/如果存在则不能设置<可用于分布式锁>

# 例如保存一个用户信息
hset user:1 name leipei age 25
~~~

hash变更的数据user name age，尤其是用户信息之类的，经常变动的信息！hash更适合于对象的存储， String更加适合字符串存储！



## Zset

在set的基础上，增加了一个值，set k1 v1 zset k1 score1 v1

~~~bash
zadd key [NX|XX] [CN] [INCR] score member [score member ...]

#示例
zadd key 1 one
zadd key 2 two 3 three	#添加多个值

zrangebyscore key min max [withscores]	#从小到大排序 -inf +inf 正无穷——负无穷

zrevrange key start stop [withscores]	#从大到小排序
zrevrange key 0 -1

zrem key member [member ...]	#移除某个元素

zcard key	#获取有序集合中的个数

zcount key min max	#获取指定区间的成员数量

~~~

带权重进行判断！比如 普通消息：1，重要消息：2

排行榜应用实现，取Top N测试



# 三种特殊数据类型

## geospatial 地理位置

朋友的地位，附近的人，打车距离计算

Redis的Geo在Redis3.2版本就推出了

可以查询一些测试数据

```bash
#添加地理位置	
GEOADD key longitude latitude member [longitude latitude member ...]   
# 规则：两级无法直接添加，我们一般会下载城市数据，直接通过java程序一次性导入
# 参数：key 经度 纬度 名称
geoadd china:city 116.40 39.90 beijing

#获取指定的城市的 经度和纬度
GEOPOS key member [member ...]

#获取两地之间的距离  unit单位可以是m：米 km：千米 mi：英里 ft：英尺
GEODIST key member1 member2 [unit]
```

> georadius 以给定的经纬度为中心，找出某一半径内的元素

我附近的人？（手机定位，获取所有附近的人的地址，定位）通过半径来查询！

~~~bash
# 以这个经纬度为中心，寻找以radius为半径的方圆范围内的数据
GEORADIUS key longitude latitude radius m|km|ft|mi [WITHCOORD] [WITHDIST] [WITHHASH] [COUNT count] [ASC|DE 

#找出位于指定元素周围的其他元素
GEORADIUSBYMEMBER key member radius m|km|ft|mi [WITHCOORD] [WITHDIST] [WITHHASH] [COUNT count] [ASC|DESC] 

#返回11个字符的geohash字符串
GEOHASH key member [member ...]

#geospatial底层本质还是zset数据结构，所以可以用zset的相关命令

~~~



## hyperloglog

> 什么是基数？

A={1,3,5,7,8,7,8}

B={1,3,5,7,8,}

基数（不重复的元素） =  5，可以接受误差

> 简介

Redis2.8.9版本就更新了Hyperloglog数据结构

Redis Hyperloglog 基数统计的算法

有点：占用的内存是固定的，2^64不同的元素的计数，只需要废12kb内存！如果从内存的角度出发的话，Hyperloglog比较合适

**网页的UV（以恶个人访问一个网站多次，但是还是算作一个人）**

传统的方式，set保存用户的ID，然后就可以统计set元素中的数量作为标准判断

这个方式如果保存大量的用户id，就会比较麻烦！我们的目的是为了计数，而不是保存用户id；

0.81% 的错误率，但是可以接受

~~~bash
# 创建一组元素
PFADD key element [element ...]

# 统计key中的基数数量
PFCOUNT key [key ...]

# 合并
PFMERGE destkey sourcekey [sourcekey ...]  


# 底层是string类型 可以用string相关的命令
~~~



## bitmaps

> 位存储   存储 0 1
>

比如统计疫情感染人数： 0未感染 1感染 

统计用户信息，活跃：不活跃   登录：未登录

打卡：365天打卡，两个状态的都可以使用Bitmaps

Bitmaps位图，数据结构！都是操作二进制位来进行记录，就只有0和1两个状态

365 = 365bit 1字节=8bit 64字节左右

~~~bash
#
SETBIT key offset value

# 栗子：使用bitmaps来记录 周一到周日的打卡
# 周一：1 周二：0 周三：0  周四：1 ....
127.0.0.1:6379> SETBIT sign 0 1
(integer) 0
127.0.0.1:6379> SETBIT sign 1 0
(integer) 0
127.0.0.1:6379> SETBIT sign 2 0
(integer) 0
127.0.0.1:6379> SETBIT sign 3 1
(integer) 0
127.0.0.1:6379> SETBIT sign 4 1
(integer) 0
127.0.0.1:6379> SETBIT sign 5 0
(integer) 0
127.0.0.1:6379> SETBIT sign 6 1
(integer) 0

# 查看某一天是否有打卡
GETBIT key offset
127.0.0.1:6379> GETBIT sign 3
(integer) 1

#统计打卡天数
BITCOUNT key [start end]

~~~



# 事务

MySQL：ACID

要么全部成功，要么全部失败

**Redis单条命令是保证原子性的，但是事务不保证原子性！**

Redis事务本质：一组命令的集合！！一个事务中的所有命令都会被序列化，在事务执行过程中，会按照顺序执行！

一次性、顺序性、排他性！执行一系列的命令

~~~
------- 队列 set set set 执行-------
~~~

**Redis事务没有隔离级别的概念！！**

所有的命令在事务中，并没有直接被执行！只有发起执行命令的时候才会执行！Exec

redis的事务：

- 开启事务（multi）
- 命令入队（...）
- 执行事务（exec）

> 正常执行事务

~~~bash
#开启事务后，set key value  就会先进入队列 ，此时并没有真正的执行；等到执行exec命令后，再执行
127.0.0.1:6379> MULTI	# 开启事务
OK
# 命令入队
127.0.0.1:6379> set k1 v1
QUEUED
127.0.0.1:6379> get k1
QUEUED
127.0.0.1:6379> set k2 v2
QUEUED
127.0.0.1:6379> EXEC	#执行事务
1) OK
2) "v1"
3) OK
127.0.0.1:6379> get k1
"v1"
127.0.0.1:6379> get k2
"v2"
127.0.0.1:6379> keys 8
(empty list or set)
127.0.0.1:6379> KEYS *
1) "k2"
2) "k1"
127.0.0.1:6379> 
~~~

> 放弃事务

~~~bash
DISCARD	#取消事务后，事务队列中的命令不会执行
~~~

> 监控！Watch（面试常问！）

**悲观锁：**

- 很悲观，认为什么时候都会出问题，无论做什么都会加锁！

**乐观锁：**

- 很乐观，认为什么时候都不会出现问题，所以不会上锁！更新数据的时候去判断一下，在此期间是否有人修改过这个数据，比如像MySQL的version！
- 获取version
- 更新的时候比较version

> Redis的监视测试

正常执行成功！

~~~bash
127.0.0.1:6379> set money 100
OK
127.0.0.1:6379> set out 0
OK
127.0.0.1:6379> WATCH money	# 监视 money 对象
OK
127.0.0.1:6379> MULTI	# 事务正常结束， 数据期间没有发生变动，这个时候就正常执行成功
OK
127.0.0.1:6379> DECRBY money 20
QUEUED
127.0.0.1:6379> INCRBY out 20
QUEUED
127.0.0.1:6379> EXEC
1) (integer) 80
2) (integer) 20

~~~

测试多线程修改值，使用watch可以当作redis的乐观锁操作！

~~~bash
# 线程1
127.0.0.1:6379> WATCH money	# 监视 money 
OK
127.0.0.1:6379> MULTI
OK
127.0.0.1:6379> DECRBY money 10
QUEUED
127.0.0.1:6379> INCRBY out 10
QUEUED
127.0.0.1:6379> EXEC	# 执行之前，另外一个线程，修改了我们的值，这个时候，就会导致事务执行失败！
(nil)

# 线程2
127.0.0.1:6379> get money
"80"
127.0.0.1:6379> set money 1000
OK
127.0.0.1:6379> 
~~~

如果修改失败，获取最新的值就好

~~~bash
127.0.0.1:6379> UNWATCH	# 1、如果发现事务执行失败，就通过unwatch先解锁
OK
127.0.0.1:6379> WATCH money	#2、获取最新的值，再次监视， 相当于select version
OK
127.0.0.1:6379> MULTI
OK
127.0.0.1:6379> DECRBY money 1
QUEUED
127.0.0.1:6379> INCRBY money 1
QUEUED
127.0.0.1:6379> EXEC	# 3、对比监视的值是否发生了变化，如果没有变化，那么可以执行成功；如果变了就执行失败！
1) (integer) 999
2) (integer) 1000
~~~

# Jedis

我们要使用Java来操作Redis

> 什么是Jedis？ 是Redis官方推荐的java连接开发工具！使用Java操作Redis中间件！如果你要使用Java操作Redis，那么一定要对Jedis十分的熟悉！

知其然并知其所以然，授人以渔！

> 测试

1、导入对应的依赖

~~~xml
<!--导入jedis的包-->
    <dependencies>
        <dependency>
            <groupId>redis.clients</groupId>
            <artifactId>jedis</artifactId>
            <version>3.2.0</version>
        </dependency>
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>fastjson</artifactId>
            <version>1.2.68</version>
        </dependency>
    </dependencies>
~~~

2、编码测试：

- 连接数据库
- 操作命令
- 断开连接

~~~java
package com.uncle;

import redis.clients.jedis.Jedis;

/**
 * @program: uncle-ray
 * @description:
 * @author: lei pei
 * @create: 2020-11-01 10:51
 */
public class TestPing {
    public static void main(String[] args) {
        // 1、new Jedis对象即可
        Jedis jedis = new Jedis("127.0.0.1", 6379);
        // jedis 所有的命令就是我们之前学习的所有指令
        System.out.println(jedis.ping());
    }
}

~~~

## 常用的API

String

List

Set

Hash

Zset

> 所有的api命令。就是我们对应的上面学习的指令，一个都没有变化！



# SpringBoot整合

SpringBoot操作数据：Spring-Data，比如

- Spring-Data JDBC
- Spring-Data JPA
- Spring-Data MongoDB
- Spring-Data Redis

SpringData也是和SpringBoot齐名的项目！

说明：在SpringBoot2.x之后，原来使用的jedis被替换为了lettuce

jedis：采用的直连，多个线程操作的话，是不安全的，如果想要避免不安全的，使用jedis pool连接池！！！更像BIO模式，是同步阻塞的

lettuce：底层采用netty，实例可以在多个线程中进行共享，不存在线程不安全的情况！可以减少线程数量了，更像NIO模式，是同步非阻塞的（多路复用）

## 源码分析

SpringBoot的spring-boot-autoconfigure的所有配置类，都有一个自动配置类	 `RedisAutoConfiguration`

自动配置类都会绑定一个properties配置文件	`RedisProperties`

~~~java
@Configuration(proxyBeanMethods = false)
@ConditionalOnClass(RedisOperations.class)
@EnableConfigurationProperties(RedisProperties.class)
@Import({ LettuceConnectionConfiguration.class, JedisConnectionConfiguration.class })
public class RedisAutoConfiguration {

	@Bean
	@ConditionalOnMissingBean(name = "redisTemplate")//我们可以自己定义一个redisTemplate来替换这个默认的！！
	public RedisTemplate<Object, Object> redisTemplate(RedisConnectionFactory redisConnectionFactory)
			throws UnknownHostException {
        // 默认的 RedisTemplate 没有过多的设置，redis对象都是需要序列化！比如Dubbo的实体也需要序列化
        // 两个泛型都是 <Object,Object>的类型，我们后面使用需要强制转换<String,Object>
		RedisTemplate<Object, Object> template = new RedisTemplate<>();
		template.setConnectionFactory(redisConnectionFactory);
		return template;
	}

	@Bean
	@ConditionalOnMissingBean// 由于String 是redis中最常使用的类型，所以说单独提出来了一个bean！
	public StringRedisTemplate stringRedisTemplate(RedisConnectionFactory redisConnectionFactory)
			throws UnknownHostException {
		StringRedisTemplate template = new StringRedisTemplate();
		template.setConnectionFactory(redisConnectionFactory);
		return template;
	}

}
~~~

> 整合测试一下

1、导入依赖

~~~xml
<!--redis整合-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-redis</artifactId>
</dependency>
~~~

2、配置连接

~~~yaml
# 配置redis
spring:
  redis:
    host: 127.0.0.1
    port: 6379
~~~

3、测试！

~~~java
   @Autowired
    RedisTemplate redisTemplate;

    @Test
    void contextLoads() {
        // redisTemplate    操作不同的数据类型，api和我们的指令是一样的
        // redisTemplate.opsForValue()  操作字符串 类似String
        // redisTemplate.opsForList()   操作List 类似List
        // redisTemplate.opsForSet()    操作Set 类似Set，无序集合
        // redisTemplate.opsForHash()   操作Hash 哈希
        // redisTemplate.opsForZSet()   操作ZSet 有序集合
        // redisTemplate.opsForGeo()    操作地理位置 范围查询
        // redisTemplate.opsForHyperLogLog()    操作超日志，比如基数统计

        // 除了基本的操作，我们常用的方法都是可以直接通过redisTemplate操作，比如事务，和基本的CURD

        // 获取redis的连接对象
//        RedisConnection connection = redisTemplate.getConnectionFactory().getConnection();
//        System.out.println(connection);
        //org.springframework.data.redis.connection.lettuce.LettuceConnection@33060020
//        connection.flushDb();
//        connection.flushAll();

        redisTemplate.opsForValue().set("myKey","叔叔大法好");
        Object myKey = redisTemplate.opsForValue().get("myKey");
        System.out.println(myKey);

    }
~~~

## 序列化的问题

redisTemplate默认是使用的jdk自带的序列化（JdkSerializationRedisSerializer），但在日常工作中，我们可以更多使用Json来传输数据，因此因为我们自定义JSON格式的序列化

如果传输的是一个对象，那么所有的对象都是需要序列化的，所以工作中所有pojo类都需要进行序列化；否则运行时会报错！！！

我们来编写一个自己的RedisTemplate

~~~java
@Configuration
public class RedisConfig {
    // 这是一个固定模板，拿来就可以直接使用
    // 自己定义一个 RedisTemplate
    @Bean
    public RedisTemplate<String, Object> redisTemplate(RedisConnectionFactory redisConnectionFactory)
            throws UnknownHostException {
        // 我们为了开发方便，一般直接使用<String, Object>类型
        RedisTemplate<String, Object> template = new RedisTemplate<>();
        // 连接工厂
        template.setConnectionFactory(redisConnectionFactory);

        // 配置具体的序列化方式 比如这里使用Json解析所有的对象
        Jackson2JsonRedisSerializer jackson2JsonRedisSerializer = new Jackson2JsonRedisSerializer(Object.class);
        ObjectMapper om = new ObjectMapper();
        om.setVisibility(PropertyAccessor.ALL, JsonAutoDetect.Visibility.ANY);
        // 因为enableDefaultTyping已经弃用了，这是使用activateDefaultTyping来代替
        om.activateDefaultTyping(
                LaissezFaireSubTypeValidator.instance,
                ObjectMapper.DefaultTyping.NON_FINAL,
                JsonTypeInfo.As.WRAPPER_ARRAY);
        jackson2JsonRedisSerializer.setObjectMapper(om);

        // String 的序列化
        StringRedisSerializer stringRedisSerializer = new StringRedisSerializer();
        // key和hash的key采用String的序列化方式
        template.setKeySerializer(stringRedisSerializer);
        template.setHashKeySerializer(stringRedisSerializer);

        // value和hash的value采用Jackson的序列化方式
        template.setValueSerializer(jackson2JsonRedisSerializer);
        template.setHashValueSerializer(jackson2JsonRedisSerializer);
        template.afterPropertiesSet();

        return template;
    }

}
~~~

所有的redis操作，其实对于java开发人员来说，十分的简单，更重要是要去理解redis的思想和每一种数据结构的用处和作用场景！！！

# Redis.conf详解

启动的时候，就通过配置文件来启动的

> 单位

配置文件 unit单位 对大小写不敏感             

> 网络 NETWORK

~~~bash
bind 127.0.0.1		#绑定IP   如果其他服务器想要访问，则bind 对应服务器的ip
protected-mode yes	#保护模式
port 6379			#端口
~~~



> 通用 GENERAL

~~~bash
daemonize yes #以守护进程的方式运行，默认是no，我们需要自己开启为yes
pidfile /var/run/redis_6379.pid #如果以后台的方式运行，我们就需要指定一个pid文件

#日志
# Specify the server verbosity level.
# This can be one of:
# debug (a lot of information, useful for development/testing)
# verbose (many rarely useful info, but not a mess like the debug level)
# notice (moderately verbose, what you want in production probably)
# warning (only very important / critical messages are logged)
loglevel notice
logfile "" 		#日志的文件位置名
databases 16 	#数据库的数量，默认是16个数据库
always-show-logo yes	#是否总是显示LOGO

~~~

> 快照 SNAPSHOTTING

持久化，在规定的时间内，执行了多少次操作，则会持久化到文件 .rdb .aof中

redis是内存数据库，如果没有持久化，那么数据断电即失

~~~bash
# 如果900秒，如果至少有1个key进行了修改，我们就进行持久化操作！
save 900 1
save 300 10
save 60 10000

stop-writes-on-bgsave-error yes	#持久化如果出错，是否需要继续工作，默认开启
rdbcompression yes	# 是否压缩 rdb 文件，需要消耗一些cpu资源
rdbchecksum yes		# 保存rdb文件的时候，进行错误的检查校验
dir ./	#rdb 文件保存的目录
~~~



> 主从复制 REPLICATION

replication



> 安全 SECURITY

可以在这里设置redis的密码，默认是没有密码

设置密码后需要认证，auth

~~~bash
#	设置密码
requirepass foobared

auth 认证登录
~~~



> 限制 LIMITS

```bash
maxclients 10000		# 设置能连接上redis的最大客户端的数量
maxmemory <bytes>		# redis配置最大的内存容量
maxmemory-policy noeviction	# 内存到达上限之后的处理策略；类似于线程池拒绝策略
	# 比如移除一些过期的key
	# 报错
# volatile-lru -> remove the key with an expire set using an LRU algorithm
# allkeys-lru -> remove any key according to the LRU algorithm
# volatile-random -> remove a random key with an expire set
# allkeys-random -> remove a random key, any key
# volatile-ttl -> remove the key with the nearest expire time (minor TTL)
# noeviction -> don't expire at all, just return an error on write operations
```



> aof配置 APPEND ONLY MODE模式

~~~bash
appendonly no	#默认是不开启aof模式的，默认是使用rdb方式持久化的，在大部分所有的情况下，rdb完全够用
appendfilename "appendonly.aof"	#aof持久化的文件名称

# appendfsync always	# 每次修改都会 sync
appendfsync everysec	# 每秒执行一次  sync
# appendfsync no		# 不执行 sync
~~~



# Redis持久化

博客详解：https://baijiahao.baidu.com/s?id=1654694618189745916&wfr=spider&for=pc

面试和工作，持久化都是重点！

Redis是内存数据库，如果不 将内存中的数据库状态保存到磁盘，那么一旦服务器进程退出，服务器中的数据库状态也会消失

。所以Redis提供了持久化功能！！

## RDB（Redis DataBase）

> 什么是RDB



![img](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1604304474302&di=f46728fd966537b7a85359b1cc7544fe&imgtype=0&src=http%3A%2F%2Fimg-blog.csdnimg.cn%2F20200806122033485.png%3Fx-oss-process%3Dimage%2Fwatermark%2Ctype_ZmFuZ3poZW5naGVpdGk%2Cshadow_10%2Ctext_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1dvb19ob21l%2Csize_16%2Ccolor_FFFFFF%2Ct_70)

在指定的时间间隔内将内存中的数据集快照写入磁盘，也就是行话讲的Snapshot快照，它恢复时是将快照文件直接读到内存里。

Redis会单独创建（fork）一个子进程来进行持久化，会先将数据写入到一个临时文件中，待持久化过程都结束了，再用这个临时文件替换上次持久化好的文件。整个过程中，主进程是不进行任何IO操作的。这就确保了极高的性能。如果需要进行大规模数据的恢复，且对于数据恢复的完整性不是非常敏感，那RDB方式要比AOF方式更加的高效。RDB的缺点是最后一次持久化后的数据可能丢失。我们默认的就是RDB，一般情况下不需要修改这个配置！

有时候在生产环境我们会将这个文件进行备份！

==rdb保存的文件时dump.rdb==  都是在我们的配置文件快照中配置的

> 触发机制

1、sava的规则满足的情况下，会自动触发rdb规则！！

2、执行flushall命令，也会触发我们的rdb规则！

3、退出redis，也会产生rdb文件！

备份就会自动生成一个dump.rdb文件

> 如何恢复rdb文件！

1、只需要将rdb文件放在我们redis启动目录就可以，redis启动的时候会自动检查dump.rdb恢复其中的数据！

2、查看需要存在的位置

~~~bash
config get dir
"dir"
"/usr/local/bin"	#如果在这个目录下存在 dump.rdb文件，启动就会自动恢复其中的数据
~~~

> 几乎就它自己默认的配置就够用了，但是我们还是需要去学习！

有点：

1、适合大规模的数据恢复！dump.rdb

2、对数据的完整性不高！

缺点：

1、需要一定的时间间隔进行操作！如果redis意外宕机了，这个最后一次修改的数据就没有了！

2、fork子进程的时候，会占用一定的内存空间！



## AOF（Append Only File）

追加文件，将我们所有的命令都记录下来，history，恢复的时候就把这个文件全部再执行一遍！

> 是什么

![img](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1604305346550&di=61fe1344d59f6e5297b05f8028f31188&imgtype=0&src=http%3A%2F%2Fimg-blog.csdnimg.cn%2F20200806160506162.png%3Fx-oss-process%3Dimage%2Fwatermark%2Ctype_ZmFuZ3poZW5naGVpdGk%2Cshadow_10%2Ctext_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1dvb19ob21l%2Csize_16%2Ccolor_FFFFFF%2Ct_70)

以日志的形式记录每个写操作，将Redis执行过的所有指令记录下来（读操作不记录），只许追加文件但不可以改写文件，redis启动之初会读取该文件重新构建数据，换言之，redis重启的话就根据日志文件的内容将写指令从前到后执行一次以完成数据的恢复工作！

==AOF保存的是appendonly.aof文件==

默认是不开启的，需要手动开启配置，将appendonly 由no改为yes就开启了

> 重写规则说明

aof默认就是文件的无限追加，文件会越来越大！

```bash
auto-aof-rewrite-percentage 100
auto-aof-rewrite-min-size 64mb
```

如果aof文件大于64m，太大了！redis就会fork一个新的进程来将我们的文件进行重写！

AOF文件重写是把Redis进程内的数据转化为==写命令==同步到新AOF文件的过程

重写 aof 后 为什么么可以变小：

- 清除了一些无效命令 eg. del srem
- 进程内超时的数据不再写入 aof 文件
- 多条写命令可以合并为批量写命令 eg. lpush list v1 lpush list v2 lpush list v3 合并为一条写入命令 lpush list v1 v2 v

redis aof重写机制：https://blog.csdn.net/Andy86869/article/details/89005638

> 优点和缺点

~~~bash
appendonly no	#默认是不开启aof模式的，默认是使用rdb方式持久化的，在大部分所有的情况下，rdb完全够用
appendfilename "appendonly.aof"	#aof持久化的文件名称

# appendfsync always	# 每次修改都会 sync
appendfsync everysec	# 每秒执行一次  sync
# appendfsync no		# 不执行 sync

# rewrite 重写
~~~

优点：

1、每一次修改都同步，文件的完整性会更好！

2、每秒同步一次，可能只会丢失一秒的数据

3、从不同步，效率最高的！

缺点：

1、相对于数据文件来说，aof远远大于rdb，修复的速度也比rdb慢！

2、AOF运行效率也要比RDB慢，所有我们redis默认的配置就是rdb持久化！



## 扩展

1、RDB持久化方式能够在指定的时间间隔内对你的数据进行快照存储！

2、AOF持久化方式记录每次对服务器==写的操作==，当服务器重启的时候会重新执行这些命令来恢复原始的数据，AOF命令以Redis协议追加保存每次写的操作到文件末尾，Redis还能对AOF文件进行后台重写，使得AOF文件的体积不至于过大（默认超过64mb）

3、==只做缓存，如果你只希望你的数据在服务器运行的时候存在，你也可以不使用任何持久化==

4、同时开启两种持久化方式

- 在这种情况下，当redis重启的时候会优先载入AOF文件来恢复原始的数据，因为在通常情况下AOF文件保存的数据集要比RDB文件保存的数据集要完整。
- RDB的数据不实时，同时使用两者时服务器重启也只会找AOF文件，那要不要只使用AOF呢？作者建议不要，因为RDB更适合用于备份数据库（AOF在不断变化，不好备份），快速重启，而且不会有AOF可能潜在的BUG，留着作为一个万一的手段。

5、性能建议

- 因为RDB文件只用作后备用途，建议只在Slave（从服务）上持久化RDB文件，而且只要15分钟备份一次就够了，只保留 `save 900 1` 这条规则。
- 如果Enable AOF，好处是最恶劣情况下也只会丢失不超过两秒数据，启动脚本较简单只load自己的AOF文件就可以了，代价一是带来了持续的IO，二是AOF rewrite的最后将rewrite过程中产生的新数据写到新文件造成的阻塞几乎是不可避免的。只要硬盘许可，应该尽量减少AOF rewrite的频率，AOF重写的基础大小默认值64M太小了，可以设到5G以上，默认超过原大小100%大小重写可以改到适当的数值。
- 如果不Enable AOF，仅靠Master-Slave Replication 实现高可用性也可以，能省掉一大笔IO开销，也减少rewrite时带来的系统波动。代价是如果Master/Slave同时倒掉，会丢失十几分钟的数据，启动脚本也要比较两个Master/Slave中的RDB文件，载入较新的那个，微博就是这种架构。



# Redis发布订阅

Redis发布订阅（pub/sub）是一种==消息通信模式==：发送者（pub）发送消息，订阅者（sub）接受消息。

Redis客户端可以订阅任意数量的频道。

订阅/发布消息图：

第一个：消息发送者，第二个：频道，第三个：消息订阅者！

![img](https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=862089970,2078447295&fm=26&gp=0.jpg)

------

下图展示了频道 channel1 ， 以及订阅这个频道的三个客户端 —— client2 、 client5 和 client1 之间的关系：

<img src="https://img-blog.csdnimg.cn/20200924215943362.png#pic_center" alt="在这里插入图片描述" style="zoom:150%;" />

当有新消息通过 PUBLISH 命令发送给频道 channel1 时，这个消息就会被发送给订阅它的三个客户端：

<img src="https://img-blog.csdnimg.cn/20200924215952210.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpc2VuMDEwNzAxMDc=,size_16,color_FFFFFF,t_70#pic_center" alt="在这里插入图片描述" style="zoom:150%;" />

------

> 命令

| 命令                                   | 描述                               |
| -------------------------------------- | ---------------------------------- |
| PSUBSCRIBE pattern [pattern…]          | 订阅一个或多个符合给定模式的频道。 |
| PUNSUBSCRIBE pattern [pattern…]        | 退订一个或多个符合给定模式的频道。 |
| PUBSUB subcommand [argument[argument]] | 查看订阅与发布系统状态。           |
| PUBLISH channel message                | 向指定频道发布消息                 |
| SUBSCRIBE channel [channel…]           | 订阅给定的一个或多个频道。         |
| UNSUBSCRIBE channel [channel…]         | 退订一个或多个频道                 |

------

> 测试

订阅端：

~~~bash
127.0.0.1:6379> SUBSCRIBE uncle
Reading messages... (press Ctrl-C to quit)
1) "subscribe"
2) "uncle"
3) (integer) 1
# 等待读取推送的消息
1) "message"	#消息
2) "uncle"		#哪个频道的消息
3) "love"		#消息的具体内容
1) "message"
2) "uncle"
3) "hello redis"

~~~

发送端：

~~~bash
127.0.0.1:6379> PUBLISH uncle "love"	#发布者发布消息
(integer) 1
127.0.0.1:6379> PUBLISH uncle "hello redis"
(integer) 1
127.0.0.1:6379> 
~~~

> 原理

Redis是使用C实现的，通过分析Redis源码里的pubsub.c文件，了解发布和订阅机制的底层实现，借此加深对Redis的理解。

Redis通过PUBLISH、SUBSCRIBE和PSUBSCRIBE等命令实现发布和订阅功能。

通过SUBSCRIBE命令订阅某频道后，redis-server里维护了一个字典，字典的键就是一个个channel，而字典的值则是一个链表，链表中保存了所有订阅这个channel的客户端。SUBSCRIBE命令的关键，就是将客户端添加到给定channel的订阅链表中。

通过PUBLISH命令向订阅者发送消息，redis-server会使用给定的频道作为键，在它所维护的channel字典中查找记录了订阅这个频道的所有客户端的链表，遍历这个链表，将消息发布给所有订阅者。

Pub/Sub从字面上理解就是发布（Publish）与订阅（Subcribe），在Redis中，你可以设定某一个key值进行消息发布及消息订阅，当一个key值进行了消息发布后，所有订阅它的客户端都会收到相应的消息。这一功能最明显的用法就是用作实时消息系统，比如普通的即时聊天、群聊等功能。

使用场景：

1、实时消息系统

2、实时聊天！（频道当作聊天室，将信息回显给所有人即可）

3、订阅，关注系统都是可以的

稍微复杂的场景我们就会使用 消息中间件（MQ）——这是专业的



# Redis主从复制

## 概念

主从复制，是指将一台Redis服务器的数据，复制到其他的Redis服务器。前者称为主节点（master/leader），后者称为从节点（slave/follower）；==数据的复制是单向的，只能由主节点到从节点。==Master以写为主，Slave以读为主。

==默认情况下，每台Redis服务器都是主节点。==

且一个主节点可以有多个从节点（或者没有从节点），但一个从节点只能有一个主节点

**主从复制的作用主要包括：**

1、数据冗余：主从复制实现了数据的==热备份==（热备份是在数据库运行的情况下，采用archivelog mode方式备份数据库的方法。即热备份是系统处于正常运转状态下的[备份](https://baike.baidu.com/item/备份/4249315)。），是持久化之外的一种数据冗余方式。

2、故障恢复：当主节点出现问题时，可以由从节点提供服务，实现快速的故障恢复；实际上是一种服务的冗余。

3、负载均衡：在主从复制的基础上，配合读写分离，可以由主节点提供==写服务==，由从节点提供==读服务==（即写Redis数据时应用连接主节点，读Redis数据时应用连接从节点），分担服务器负载；尤其是在==写少读多==的场景下，通过多个从节点分担读负载，可以大大提高Redis服务器的并发量。

4、高可用（集群）基石：除了上述作用以外，主从复制还是哨兵和集群能够实施的基础，因此说主次复制是Redis高可用的基础。



一般来说，要将Redis运用于工程项目中，只使用一台Redis是万万不能的（宕机），原因如下：

1、从结构上，单个Redis服务器会发生单点故障，并且一台服务器需要处理所有的请求负载，压力较大；

2、从容量上，单个Redis服务器内存容量有限，就算一台Redis服务器内存容量为256G，也不能将所有内存用作Redis存储内存，一般来说，==单台Redis最大使用内存不应该超过20G。==

电商网站上的商品，一般都是一次上传，无数次浏览的，说专业点也就是“多读少写”。

对于这种场景，我们可以使用如下这种架构：

![img](https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=4200046827,1072688053&fm=26&gp=0.jpg)

主从复制，读写分离！80%的情况下都是在进行读操作！将读操作在从机上操作，减缓服务器的压力！架构中经常使用！

只要在公司中，主从复制就是必须要使用的，因为在真实的项目中不可能单机使用Redis！

一主二从：本地搭建一个伪集群

## 环境配置

只配置从库，不用配置主库！

~~~bash
# 启动redis服务，并打开客户端
./redis-server redis.cong
./redis-cli

127.0.0.1:6379> info replication	#查看当前库的信息
# Replication
role:master			#角色 master
connected_slaves:0	#没有从机
master_replid:3a34d3b6c869865e5f735b382039b6bf9bec6331
master_replid2:0000000000000000000000000000000000000000
master_repl_offset:0
second_repl_offset:-1
repl_backlog_active:0
repl_backlog_size:1048576
repl_backlog_first_byte_offset:0
repl_backlog_histlen:0
127.0.0.1:6379> 
~~~

复制3个配置文件，然后修改对应的信息

1、端口

2、pid名字

3、log文件名字

4、dump.rdb名字

~~~bash
[root@unclerayslove bin]# ls
dump.rdb  redis-benchmark  redis-check-aof  redis-check-rdb  redis-cli  redis.conf  redis-sentinel  redis-server
[root@unclerayslove bin]# ps -ef|grep redis
root     122406      1  0 23:10 ?        00:00:00 ./redis-server 127.0.0.1:6379
root     122476      1  0 23:10 ?        00:00:00 ./redis-server 127.0.0.1:6380
root     122506      1  0 23:11 ?        00:00:00 ./redis-server 127.0.0.1:6381
root     122530 121540  0 23:11 pts/4    00:00:00 grep --color=auto redis
[root@unclerayslove bin]# 
~~~



## 一主二从

==默认情况下，每台Redis服务器都是主节点==；我们一般情况下只用配置从机就好了

认老大！！！一主（79）二从（80、81）

真实的主从配置应该在配置文件中，这样的话是永久的，我们这里使用的是命令，是暂时的！

```bash
# 如果要永久生效，在redis.conf配置文件中配置一下信息

################################# REPLICATION #################################

# Master-Replica replication. Use replicaof to make a Redis instance a copy of
# another Redis server. A few things to understand ASAP about Redis replication.
#
#   +------------------+      +---------------+
#   |      Master      | ---> |    Replica    |
#   | (receive writes) |      |  (exact copy) |
#   +------------------+      +---------------+
#
# 1) Redis replication is asynchronous, but you can configure a master to
#    stop accepting writes if it appears to be not connected with at least
#    a given number of replicas.
# 2) Redis replicas are able to perform a partial resynchronization with the
#    master if the replication link is lost for a relatively small amount of
#    time. You may want to configure the replication backlog size (see the next
#    sections of this file) with a sensible value depending on your needs.
# 3) Replication is automatic and does not need user intervention. After a
#    network partition replicas automatically try to reconnect to masters
#    and resynchronize with them.
#
replicaof <masterip> <masterport>

```

> 细节

主机负责写，从机不能写只能读！主机中的所有信息和数据，都会自动被从机保存！

~~~bash
127.0.0.1:6381> set k1 v1
(error) READONLY You can't write against a read only replica. #从机写的时候就会报错
127.0.0.1:6381> 

~~~

测试：主机断开连接，从机依旧连接到主机的，但是没有写操作，这个时候，主机如果回来了，从机依旧可以直接获取到主机写的信息！——这是保证集群高可用性！！

如果是使用命令行slaveof，来配置的主从，这个时候从机如果重启了，就会变回主机！只要变为从机，立马就会从主机中获取值！

> 复制原理

Slave启动成功连接到Master后会发送一个sync同步命令

Master接到命令，启动后台的存盘进程，同事收集所有接收到的用于修改数据集的命令，在后台进程执行完毕之后，==master将传送整个数据文件到slave，并完成一次完全同步。==

==全量复制==：当slave服务在接收到数据库文件数据后，将其存盘并加载到内存中。

==增量复制==：Master继续将新的所有收集到的修改命令依次传给slave，完成同步！

但是只要是重新连接master，一次完全同步（全量复制）将被自动执行！我们的数据一定可以在从机中看到！



~~~bash
slaveof host port #配置从机命令
127.0.0.1:6380> SLAVEOF 127.0.0.1 6379
OK
127.0.0.1:6380> INFO replication
# Replication
role:slave
master_host:127.0.0.1
master_port:6379
master_link_status:up
master_last_io_seconds_ago:8
master_sync_in_progress:0
slave_repl_offset:0
slave_priority:100
slave_read_only:1
connected_slaves:0
master_replid:7a8434fef68c9b29113bf6350602ced204904e35
master_replid2:0000000000000000000000000000000000000000
master_repl_offset:0
second_repl_offset:-1
repl_backlog_active:1
repl_backlog_size:1048576
repl_backlog_first_byte_offset:1
repl_backlog_histlen:0
127.0.0.1:6380> 

# 在主机中查看
127.0.0.1:6379> info replication
# Replication
role:master
connected_slaves:1	#多了一个从机
slave0:ip=127.0.0.1,port=6380,state=online,offset=154,lag=0
master_replid:7a8434fef68c9b29113bf6350602ced204904e35
master_replid2:0000000000000000000000000000000000000000
master_repl_offset:154
second_repl_offset:-1
repl_backlog_active:1
repl_backlog_size:1048576
repl_backlog_first_byte_offset:1
repl_backlog_histlen:154
127.0.0.1:6379> 

# 启动三个redis服务
[root@unclerayslove bin]# ./redis-cli -p 6379
127.0.0.1:6379> info replication
# Replication
role:master
connected_slaves:0
master_replid:5986c73365940f37424a3930da088d9e820de0ae
master_replid2:0000000000000000000000000000000000000000
master_repl_offset:0
second_repl_offset:-1
repl_backlog_active:0
repl_backlog_size:1048576
repl_backlog_first_byte_offset:0
repl_backlog_histlen:0
127.0.0.1:6379> 
###########################################################

[root@unclerayslove bin]# ./redis-cli -p 6380
127.0.0.1:6380> info replication
# Replication
role:master
connected_slaves:0
master_replid:b5326fafcfd12c74b9644768b58549dfe5be527f
master_replid2:0000000000000000000000000000000000000000
master_repl_offset:0
second_repl_offset:-1
repl_backlog_active:0
repl_backlog_size:1048576
repl_backlog_first_byte_offset:0
repl_backlog_histlen:0
127.0.0.1:6380> 
###########################################################

[root@unclerayslove bin]# ./redis-cli -p 6381
127.0.0.1:6381> info replication
# Replication
role:master
connected_slaves:0
master_replid:b5766023ef5668e9bb3b27a8a2204a1e1e69a167
master_replid2:0000000000000000000000000000000000000000
master_repl_offset:0
second_repl_offset:-1
repl_backlog_active:0
repl_backlog_size:1048576
repl_backlog_first_byte_offset:0
repl_backlog_histlen:0
127.0.0.1:6381> 
~~~



> 如果没有老大了，这个时候能不能选择一个老大出来呢？？手动！！！

谋朝篡位

如果主机断开了连接，我们可以使用`SLAVEOF no one`让自己变成主机！其他的节点就可以手动连接到最新的这个主节点（手动）！如果这个时候老大修复了，那就重新连接！！



## 哨兵模式（sentinel）

（自动选举老大的模式）

> 概述

主从切换技术的方式是：当主服务器宕机后，需要手动把一台从服务器切换为主服务器，这就需要人工干预，费事费力，还会造成一段时间内服务不可用。这不是一种推荐的方式，更多时候，我们优先考虑哨兵模式。Redis从2.8开始正是提供了Sentinel（哨兵）架构来解决这个问题。

谋朝篡位的自动版，能够后台监控主机是否故障，如果故障了根据票数自动将从库转换为主库。

哨兵模式是一种特殊的模式。首先Redistribution提供了哨兵的命令，哨兵是一个独立的进程，作为进程，它会独立运行。其原理是**哨兵通过发送命令，等待Redis服务器响应，从而监控运行的多个Redis实例**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200924220203813.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpc2VuMDEwNzAxMDc=,size_16,color_FFFFFF,t_70#pic_center)

这里的哨兵有两个作用

- 通过发送命令，让Redis服务器返回监控其运行状态，包括主服务器和从服务器。
- 当哨兵监测到master宕机，会自动将slave切换成master，然后通过==发布订阅模式==通知其他的从服务器，修改配置文件，让他们切换主机。

然而一个哨兵进程对Redis服务器进行监控，可能会出现问题，为此，我们可以使用多个哨兵进行监控。各个哨兵之间还会进行监控，这样就形成了多哨兵模式。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200924220217342.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpc2VuMDEwNzAxMDc=,size_16,color_FFFFFF,t_70#pic_center)

假设主服务器宕机，哨兵1先检测到这个结果，系统并不会马上进行failover[故障转移]过程，仅仅是哨兵1主观的认为主服务器不可用，这个现象称为**主观下线**。当后面的哨兵也检测到主服务器不可用，并且数量达到一定值时，那么哨兵之间就会进行一次投票，投票的结果由一个哨兵发起，进行failover[故障转移]操作。切换成功后，就会通过发布订阅模式，让各个哨兵把自己监控的从服务器实现切换主机，这个过程称为**客观下线**。



> 测试！

目前是一从二主模式！

1、配置哨兵配置文件sentinel.conf

~~~bash
# sentinel monitor 被监控的名称 host port 1
sentinel monitor myredis 127.0.0.1 6379 1

告诉sentinel去监听地址为ip:port的一个master，这里的master-name可以自定义，quorum是一个数字，指明当有多少个sentinel认为一个master失效时，master才算真正失效。master-name只能包含英文字母，数字，和“.-_”这三个字符需要注意的是master-ip 要写真实的ip地址而不要用回环地址（127.0.0.1）。
~~~

后面的这个数字1，代表主机挂了，slave投票看让谁接替成为主机，票数最多的，就会成为主机！

2、启动哨兵

~~~bash
# 启动哨兵
redis-sentinel config/sentinel.conf
~~~

~~~bash
[root@unclerayslove bin]# redis-sentinel config/sentinel.conf 
93060:X 07 Nov 2020 16:04:26.844 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
93060:X 07 Nov 2020 16:04:26.844 # Redis version=5.0.5, bits=64, commit=00000000, modified=0, pid=93060, just started
93060:X 07 Nov 2020 16:04:26.844 # Configuration loaded
93060:X 07 Nov 2020 16:04:26.846 * Increased maximum number of open files to 10032 (it was originally set to 1024).
                _._                                                  
           _.-``__ ''-._                                             
      _.-``    `.  `_.  ''-._           Redis 5.0.5 (00000000/0) 64 bit
  .-`` .-```.  ```\/    _.,_ ''-._                                   
 (    '      ,       .-`  | `,    )     Running in sentinel mode
 |`-._`-...-` __...-.``-._|'` _.-'|     Port: 26379
 |    `-._   `._    /     _.-'    |     PID: 93060
  `-._    `-._  `-./  _.-'    _.-'                                   
 |`-._`-._    `-.__.-'    _.-'_.-'|                                  
 |    `-._`-._        _.-'_.-'    |           http://redis.io        
  `-._    `-._`-.__.-'_.-'    _.-'                                   
 |`-._`-._    `-.__.-'    _.-'_.-'|                                  
 |    `-._`-._        _.-'_.-'    |                                  
  `-._    `-._`-.__.-'_.-'    _.-'                                   
      `-._    `-.__.-'    _.-'                                       
          `-._        _.-'                                           
              `-.__.-'                                               

93060:X 07 Nov 2020 16:04:26.924 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
93060:X 07 Nov 2020 16:04:26.932 # Sentinel ID is 2b02bb2a7193fbe13d414f533d4cc92f2df81adc
93060:X 07 Nov 2020 16:04:26.932 # +monitor master myredis 127.0.0.1 6379 quorum 1
93060:X 07 Nov 2020 16:04:27.007 * +slave slave 127.0.0.1:6380 127.0.0.1 6380 @ myredis 127.0.0.1 6379
93060:X 07 Nov 2020 16:04:27.011 * +slave slave 127.0.0.1:6381 127.0.0.1 6381 @ myredis 127.0.0.1 6379

~~~

shutdown 6379的主机后，过一会，哨兵会发送心跳包监测主机是否还存活，如果宕机，则随机另选一个服务器作为主机（这里面有一个投票算法！——选举算法）https://blog.csdn.net/weixin_44324174/article/details/108939199

这个选举了6381作为新的主机

~~~bash
93060:X 07 Nov 2020 16:06:18.098 # +sdown master myredis 127.0.0.1 6379
93060:X 07 Nov 2020 16:06:18.098 # +odown master myredis 127.0.0.1 6379 #quorum 1/1
93060:X 07 Nov 2020 16:06:18.098 # +new-epoch 1
93060:X 07 Nov 2020 16:06:18.098 # +try-failover master myredis 127.0.0.1 6379
93060:X 07 Nov 2020 16:06:18.101 # +vote-for-leader 2b02bb2a7193fbe13d414f533d4cc92f2df81adc 1
93060:X 07 Nov 2020 16:06:18.101 # +elected-leader master myredis 127.0.0.1 6379
93060:X 07 Nov 2020 16:06:18.101 # +failover-state-select-slave master myredis 127.0.0.1 6379
93060:X 07 Nov 2020 16:06:18.178 # +selected-slave slave 127.0.0.1:6381 127.0.0.1 6381 @ myredis 127.0.0.1 6379
93060:X 07 Nov 2020 16:06:18.178 * +failover-state-send-slaveof-noone slave 127.0.0.1:6381 127.0.0.1 6381 @ myredis 127.0.0.1 6379
93060:X 07 Nov 2020 16:06:18.262 * +failover-state-wait-promotion slave 127.0.0.1:6381 127.0.0.1 6381 @ myredis 127.0.0.1 6379
93060:X 07 Nov 2020 16:06:19.134 # +promoted-slave slave 127.0.0.1:6381 127.0.0.1 6381 @ myredis 127.0.0.1 6379
93060:X 07 Nov 2020 16:06:19.134 # +failover-state-reconf-slaves master myredis 127.0.0.1 6379
93060:X 07 Nov 2020 16:06:19.223 * +slave-reconf-sent slave 127.0.0.1:6380 127.0.0.1 6380 @ myredis 127.0.0.1 6379
93060:X 07 Nov 2020 16:06:20.201 * +slave-reconf-inprog slave 127.0.0.1:6380 127.0.0.1 6380 @ myredis 127.0.0.1 6379
93060:X 07 Nov 2020 16:06:21.254 * +slave-reconf-done slave 127.0.0.1:6380 127.0.0.1 6380 @ myredis 127.0.0.1 6379
93060:X 07 Nov 2020 16:06:21.325 # +failover-end master myredis 127.0.0.1 6379
93060:X 07 Nov 2020 16:06:21.325 # +switch-master myredis 127.0.0.1 6379 127.0.0.1 6381
93060:X 07 Nov 2020 16:06:21.325 * +slave slave 127.0.0.1:6380 127.0.0.1 6380 @ myredis 127.0.0.1 6381
93060:X 07 Nov 2020 16:06:21.325 * +slave slave 127.0.0.1:6379 127.0.0.1 6379 @ myredis 127.0.0.1 6381
93060:X 07 Nov 2020 16:06:51.334 # +sdown slave 127.0.0.1:6379 127.0.0.1 6379 @ myredis 127.0.0.1 6381

~~~

如果主机此时回来了，只能归并到新的主机下，当作从机，这就是哨兵模式的规则！！！

~~~bash
127.0.0.1:6381> info replication
# Replication
role:master
connected_slaves:2
slave0:ip=127.0.0.1,port=6380,state=online,offset=369820,lag=1
slave1:ip=127.0.0.1,port=6379,state=online,offset=369820,lag=1
master_replid:9acb7736a3c80b36e8795f92f60917fafaf89bd9
master_replid2:7a8434fef68c9b29113bf6350602ced204904e35
master_repl_offset:369820
second_repl_offset:328251
repl_backlog_active:1
repl_backlog_size:1048576
repl_backlog_first_byte_offset:239
repl_backlog_histlen:369582

~~~

> 哨兵模式

优点：

1、哨兵集群，基于主从复制模式，所有的主从配置优点，它全有

2、主从可以切换，故障可以转移，系统的可用性就会更好

3、哨兵模式就是主从模式的升级，手动到自动，更加健壮！

缺点：

1、Redis不好在线扩容，集群容量一旦到达上限，在线扩容就十分麻烦！

2、实现哨兵模式的配置其实是很麻烦的，里面有很多选择！

> 哨兵模式的全部配置

~~~bash
# Example sentinel.conf
 
# 哨兵sentinel实例运行的端口 默认26379     如果有哨兵集群，我们还需要配置每个 哨兵端口
port 26379
 
# 哨兵sentinel的工作目录
dir /tmp
 
# 哨兵sentinel监控的redis主节点的 ip port 
# master-name  可以自己命名的主节点名字 只能由字母A-z、数字0-9 、这三个字符".-_"组成。
# quorum[法定人数] 当这些quorum个数sentinel哨兵认为master主节点失联 那么这时 客观上认为主节点失联了
# sentinel monitor <master-name> <ip> <redis-port> <quorum>
sentinel monitor mymaster 127.0.0.1 6379 2
 
# 当在Redis实例中开启了requirepass foobared 授权密码 这样所有连接Redis实例的客户端都要提供密码
# 设置哨兵sentinel 连接主从的密码 注意必须为主从设置一样的验证密码
# sentinel auth-pass <master-name> <password>
sentinel auth-pass mymaster MySUPER--secret-0123passw0rd
 
 
# 指定多少毫秒之后 主节点没有应答哨兵sentinel 此时 哨兵主观上认为主节点下线 默认30秒
# sentinel down-after-milliseconds <master-name> <milliseconds>
sentinel down-after-milliseconds mymaster 30000
 
# 这个配置项指定了在发生failover主备切换时最多可以有多少个slave同时对新的master进行 同步，
这个数字越小，完成failover所需的时间就越长，
但是如果这个数字越大，就意味着越 多的slave因为replication而不可用。
可以通过将这个值设为 1 来保证每次只有一个slave 处于不能处理命令请求的状态。
# sentinel parallel-syncs <master-name> <numslaves>
sentinel parallel-syncs mymaster 1
 
 
 
# 故障转移的超时时间 failover-timeout 可以用在以下这些方面： 
#1. 同一个sentinel对同一个master两次failover之间的间隔时间。
#2. 当一个slave从一个错误的master那里同步数据开始计算时间。直到slave被纠正为向正确的master那里同步数据时。
#3.当想要取消一个正在进行的failover所需要的时间。  
#4.当进行failover时，配置所有slaves指向新的master所需的最大时间。不过，即使过了这个超时，slaves依然会被正确配置为指向master，但是就不按parallel-syncs所配置的规则来了
# 默认三分钟
# sentinel failover-timeout <master-name> <milliseconds>
sentinel failover-timeout mymaster 180000
 
# SCRIPTS EXECUTION
 
#配置当某一事件发生时所需要执行的脚本，可以通过脚本来通知管理员，例如当系统运行不正常时发邮件通知相关人员。
#对于脚本的运行结果有以下规则：
#若脚本执行后返回1，那么该脚本稍后将会被再次执行，重复次数目前默认为10
#若脚本执行后返回2，或者比2更高的一个返回值，脚本将不会重复执行。
#如果脚本在执行过程中由于收到系统中断信号被终止了，则同返回值为1时的行为相同。
#一个脚本的最大执行时间为60s，如果超过这个时间，脚本将会被一个SIGKILL信号终止，之后重新执行。
 
#通知型脚本:当sentinel有任何警告级别的事件发生时（比如说redis实例的主观失效和客观失效等等），将会去调用这个脚本，
#这时这个脚本应该通过邮件，SMS等方式去通知系统管理员关于系统不正常运行的信息。调用该脚本时，将传给脚本两个参数，
#一个是事件的类型，
#一个是事件的描述。
#如果sentinel.conf配置文件中配置了这个脚本路径，那么必须保证这个脚本存在于这个路径，并且是可执行的，否则sentinel无法正常启动成功。
#通知脚本
# sentinel notification-script <master-name> <script-path>
  sentinel notification-script mymaster /var/redis/notify.sh
 
# 客户端重新配置主节点参数脚本
# 当一个master由于failover而发生改变时，这个脚本将会被调用，通知相关的客户端关于master地址已经发生改变的信息。
# 以下参数将会在调用脚本时传给脚本:
# <master-name> <role> <state> <from-ip> <from-port> <to-ip> <to-port>
# 目前<state>总是“failover”,
# <role>是“leader”或者“observer”中的一个。 
# 参数 from-ip, from-port, to-ip, to-port是用来和旧的master和新的master(即旧的slave)通信的
# 这个脚本应该是通用的，能被多次调用，不是针对性的。
# sentinel client-reconfig-script <master-name> <script-path>
sentinel client-reconfig-script mymaster /var/redis/reconfig.sh	#一般都是由运维来配置！！

~~~



# Redis缓存穿透和雪崩（面试高频，工作常用）

这里不会详细的去分析解决方案的底层

Redis缓存的使用，极大的提升了应用程序的性能和效率，特别是数据查询方面。但同时，它也带来了一些问题。其中，最要害的问题，就是==数据的一致性问题==(事务在运行时不能保证原子性)，从严格意义上讲，这个问题无解。如果对数据的一致性要求很高，那么就不能使用缓存。
另外的一些典型问题就是，==缓存穿透==、==缓存雪崩==和==缓存击穿==。目前，业界也都有比较流行的解决方案。

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020092422031948.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpc2VuMDEwNzAxMDc=,size_16,color_FFFFFF,t_70#pic_center)



## 缓存穿透（查不到）

> 概念

缓存穿透的概念很简单，用户想要查询一个数据，发现rdis内存数据库没有，也就是缓存没有命中，于是向持久层数据库查询。发现也没有，于是本次查询失败。当用户很多的时候，缓存都没有命中（比如 秒杀！！），于是都去请求了持久层数据库。这会给持久层数据库造成很大的压力，这时候就相当于出现了缓存穿透。

> 解决方案

**布隆过滤器**

布隆过滤器是一种==数据结构==，对所有可能查询的参数以hash形式存储，在控制层先进行校验，不符合则丢弃，从而避免了对底层存储系统的查询压力。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200924220329941.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpc2VuMDEwNzAxMDc=,size_16,color_FFFFFF,t_70#pic_center)

**缓存空对象**

当存储层不命中后，即使返回的空对象也将其缓存起来，同时会设置一个过期时间，之后再访问这个数据将会从缓存中获取，保护了后端数据源。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200924220342915.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpc2VuMDEwNzAxMDc=,size_16,color_FFFFFF,t_70#pic_center)

但是这种方法会存在两个问题：

1、如果空值能够被缓存起来，这就意味着缓存需要更多的空间存储更多的键，因为这当中可能会有很多的空值的键；
2、即使对空值设置了过期时间，还是会存在缓存层和存储层的数据会有一段时间窗口的不一致，这对于需要保持一致性的业务会有影响



## 缓存击穿（量太大，缓存过期！）

> 概述

这里需要注意和缓存穿透的区别，缓存击穿，是指一个key非常热点，在不停的扛着大并发，大并发集中对这一个点进行访问，当这个key在失效的瞬间，持续的大并发就穿破缓存，直接请求数据库，就像一个屏障上凿开了一个洞。

当某个key在过期的瞬间，有大量的请求并发访问，这类数据一般是热点数据，由于缓存过期，会同时访问数据库来查询最新数据，并且回写缓存，会导致数据库瞬间压力过大。

相较于缓存穿透，缓存击穿的目的性更强，一个存在的key，在缓存过期的一刻，同时有大量的请求，这些请求都会击穿到DB，造成瞬时DB请求量大、压力骤增。这就是缓存被击穿，只是针对其中某个key的缓存不可用而导致击穿，但是其他的key依然可以使用缓存响应。

比如热搜排行上，一个热点新闻被同时大量访问就可能导致缓存击穿。比如微博热搜导致宕机多次了

> 解决方案

**1.设置热点数据永不过期**
这样就不会出现热点数据过期的情况，但是当Redis内存空间满的时候也会清理部分数据，而且此种方案会占用空间，一旦热点数据多了起来，就会占用部分空间。

**2.加互斥锁(分布式锁)**
在访问key之前，采用SETNX（set if not exists）来设置另一个短期key来锁住当前key的访问，访问结束再删除该短期key。保证同时刻只有一个线程访问。这样对锁的要求就十分高。



## 缓存雪崩

雪山发生雪崩时，没有一片雪花是无辜的！！

> 概念

缓存雪崩，是指在某一个时间段，缓存集中过期失效。或者Redis宕机！

产生雪崩的原因之一，比如马上就要到双十一零点，很快就会迎来一波抢购，这波商品时间比较集中的放入了缓存，假设缓存一个小时。那么到了凌晨一点钟的时候，这批商品的缓存就都过期了。而对这批商品的访问查询，都落到了数据库上，对于数据库而言，就会产生周期性的压力波峰。于是所有的请求都会达到存储层，存储层的调用量会爆增，造成存储层也会挂掉的情况。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200924220357661.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpc2VuMDEwNzAxMDc=,size_16,color_FFFFFF,t_70#pic_center)

其实集中过期，倒不是非常致命，比较致命的缓存雪崩，是缓存服务器某个节点宕机或断网。因为自然形成的缓存雪崩，一定是在某个时间段集中创建缓存，这个时候，数据库也是可以顶住压力的。无非就是对数据库产生周期性的压力而已。而缓存服务节点的宕机，对数据库服务器造成的压力是不可预知的，很有可能瞬间就把数据库压垮。

双十一：停掉一些服务，（保证主要的服务可用）；比如退款，在这一天是不支持的（服务是关闭的）；

> 解决方案

**redis高可用**

这个思想的含义是，既然redis有可能挂掉，那我多增设几台redis，这样一台挂掉之后其他的还可以继续工作，其实就是搭建的==集群==。（异地多活！）

**限流降级**

这个解决方案的思想是，在缓存失效后，通过==加锁或者队列来控制读数据库写缓存的线程数量==。比如对某个key只允许一个线程查询数据和写缓存，其他线程等待。

**数据预热**

数据加热的含义就是在正式部署之前，我先把可能的数据预先访问一遍，这样部分可能大量访问的数据就会加载到缓存中。在即将发生大并发访问前手动触发加载缓存不同的key，设置不同的过期时间，让缓存失效的时间点尽量均匀。









