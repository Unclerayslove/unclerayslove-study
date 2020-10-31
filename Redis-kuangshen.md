NoSQL：not only SQL

# NoSQL的四大分类：

**KV键值对：**

- 新浪：Redis

- 美团：Redis+Tair
- 阿里、百度：Redistribution+memecache

**文档型数据库（bson格式和json一样）：**

- MongoDB（一般必须要掌握）
  - 基本分布式文件存储的数据库，C++编写，主要用来处理大量的文档
  - 介于关系型数据库和非关系型数据中间的产品。MongoDB是非关系型数据库中功能最丰富，最像关系型数据库的！
- ConyhDB

**列存储数据库：**

- HBase
- 分布式文件系统

**图关系数据库：**

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

1、下载安装包！`redis-6.0.8.tar.gz`

2、上传到远程服务器（比如一般是/home目录下）；可以选择mv到/opt目录下（临时文件）解压Redis的安装包

3、进入解压后的文件，可以看到Redis的配置文件

4、基本的环境安装

~~~bash
yum install gcc-c++

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
 #在连接客户端的情况下，shutdown，然后exit推出
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

0-15

select index 切换数据库

dbsize 查看数据库大小

清除当前数据库 ：flushdb  

清空全部数据库内容： flushall



> Redis是单线程的

Redis是很快的，官方表示，Redis是基于内存操作，CPU不是Redis性能瓶颈。Redis的瓶颈是根据机器的内存和网络带宽，既然可以使用单线程来实现，就使用单线程了

Redis是C语言写的，官方提供的数据为：100000+的QPS，这个不必Memecache差

Redis为什么单线程还这么快？

1、误区1：高性能的服务器一定是多线程的？

2、误区2：多线程（CPU上下文会切换）一定比单线程效率高！

CPU > 内存 > 硬盘的速度要有所了解

核心：redis是将所有的数据全部放在内存中的，所以说使用单线程去操作效率就是高的，多线程（CPU上下文会切换：耗时的操作！！！），对于内存系统来说，如果没有上下文切换效率就是最高的！ 多次读写都是在一个CPU上的，在内存情况下，这个就是最佳的方案



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



incr key

decr key

incr key number

decr key number

getrange key start end  

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
 
sdiff key [key ...]		#差集

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











# Jedis

# SpringBoot整合

# Redis.conf详解

# Redis持久化

# Redis发布订阅

# Redis主从复制

# Redis缓存穿透和雪崩

