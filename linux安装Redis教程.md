# Linux Install Redis

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

