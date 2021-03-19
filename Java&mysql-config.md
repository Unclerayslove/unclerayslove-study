# JDK多版本配置

## Windows—推荐默认就行

除非你想改jdk的安装路径，或者是你不想用公共jre，不然一直下一步就行。

### 环境变量配置

此电脑 --- 属性 -- 高级系统设置 -- 环境变量 -- 系统变量 -- 新建

#### 1.配置JAVA_HOME

`JAVA9_HOME =jdk1.9的安装路径`

`JAVA8_HOME =jdk1.8的安装路径`

`JAVA_HOME = %JAVA8_HOME%`

两个%表示引用变量的值，直接用JAVA_HOME，就能表示一连串长的安装路径。

JAVA_HOME的作用是确定java的家在哪儿，配置好后，电脑就能找到Java的安装目录了。如果你不配置JAVA_HOME，计算机就会以为你没安装。

#### 2.配置Path

在系统变量中找到`Path`，选择`编辑`，然后`新建`，将`%JAVA_HOME%\bin`复制进去

配置Path的目的是让电脑找到jdk的bin目录，这个目录你可以打开看一下，比如我们常用的javac.exe、java.exe、javah.exe，其实都是在这个目录里。也就是说，如果你不设置Path变量，那么在使用相关的命令时，比如敲个javac ，计算机压根就不识别。

#### 3.配置CLASSPATH

系统变量 -- 新建--变量名`CLASSPATH`--变量值`.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;`(点别忽略)，`dt.jar`和`tools.jar`启动时加载的 

其实1.5之后不用再设置classpath了,不信的话你可以删掉，直接用cmd查看版本，一样可以。之所以还设置，是考虑向下兼容的问题。CLASSPATH的目的是标明默认的类路径。我们在使用java命令来执行java程序的时候，就是通过类路径来告诉java命令在哪些路径下去寻找class文件的。我们可以在执行java命令时，通过-classpath参数来告诉java命令类路径。如果没指定的话，java命令就会使用CLASSPATH环境变量指定的类路径。

如果你以后还想装其他版本的jdk，那就再新建一个，比如 JAVA10_HOME，后面跟Java10的安装路径

当你想用Java10进行开发时，把`JAVA_HOME`后面的值改成`%JAVA10_HOME%`就行。其他版本的以此类推。



## Linux

### 解压

1.上传下载的压缩包到指定路径，比如：/usr/local/java，cd /usr/local/java

2.解压：tar zxvf 压缩包名称 （例如：`tar zxvf jdk-8u191-linux-x64.tar.gz`）后面的名称可以只输入一个`tar zxvf j`，然后使用Tab按键自动补全文件名

3.删除压缩包：rm -f 压缩包名称 （例如 `rm -f jdk-8u191-linux-x64.tar.gz`）

### 环境变量配置

1.编辑/etc/profile文件
 `vim /etc/profile`

2.按`Insert`或者`I`键，切换成编辑模式。找到内容末尾，按图片输入下面一段话。在`unset i`的前面输入

```bash
export JAVA_HOME=/usr/local/java/jdk1.8.0_191 #解压后路径
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin
#（！！！注意：JAVA_HOME的路径是你实际解压后的JDK的路径，千万别写错了）
```

3.按`Esc`退出编辑模式，输入`:wq`保存并退出

4.生效环境变量
 对于/etc/profile编写完成之后是不够的，还需要最后一个步骤，就是让刚刚我们修改的文件变成有效起来，所以我们再输入一个命令，让修改生效。生效命令：`source /etc/profile`

验证是否成功：java -version



# MySQL配置-Windows

## 解压安装步骤

- 下载压缩文件解压

- 配置环境变量：在系统环境Path下添加：mysql安装文件下面的bin文件夹下

- 配置【压缩版没有则新建】my.ini文件，这是一个配置文件

- ```ini
  # mysql根目录
  basedir="D:\Environment\mysql-5.7.23\"
  # 放所有数据库的data目录
  datadir="D:\Environment\mysql-5.7.23\data"
  port=3306
  ```

- 启管理员模式的CMD，切换到mysql下的bin目录，然后输入`mysqld -install`（安装mysql）——往注册表里面注册服务mysqlServer；

  - 执行`mysqld --remove`（卸载安装）

- 再输入`mysqld --initialize-insecure --user=mysql`初始化数据文件或者继续执行`mysqld --initialize --user=root --console`命令初始化数据

- 执行`net start mysql`启动服务（执行`net stop mysql`关闭服务）

- 用命令行进入用户界面 `mysql -u root -p`

- 进入界面后，更改root密码 `update mysql.user set authentication_string=password('123456') where user='root' and Host='localhost';`（最后输入`flush privileges;`，刷新权限）

- 再次登录 `mysql -uroot -p123456`

## 压缩包版MySQL卸载

~~~bash
mysql -V #查看版本命令

# 停止MySQL服务
net stop mysql

# 删除服务
mysqld -remove mysql【服务名】

#删除MySQL文件

#删除注册表信息
开始->运行-> regedit，进入注册表
~~~



my.ini配置

~~~ini
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8 
[mysqld]
#设置3306端口
port = 3306 
# 设置mysql的安装目录
basedir=F:\Program Files\Environment\mysql-5.7.30-winx64
# 设置mysql数据库的数据的存放目录
datadir=F:\Program Files\Environment\mysql-5.7.30-winx64\data
# 允许最大连接数
max_connections=200
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB

# 跳过表验证
# skip-grant-tables
~~~





~~~shell
# 1、卸载【首次安装不需要卸载】
F:\Program Files\Environment\mysql-5.7.30-winx64\bin>mysqld --remove
Service successfully removed.

# 2、
F:\Program Files\Environment\mysql-5.7.30-winx64\bin>mysqld --initialize

F:\Program Files\Environment\mysql-5.7.30-winx64\bin>mysqld --install
Service successfully installed.

F:\Program Files\Environment\mysql-5.7.30-winx64\bin>net start mysql
MySQL 服务正在启动 .
MySQL 服务已经启动成功。


F:\Program Files\Environment\mysql-5.7.30-winx64\bin>mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.7.30 MySQL Community Server (GPL)

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> use mysql
Database changed
mysql> update mysql.user set authentication_string=password('123456') where user='root';
Query OK, 1 row affected, 1 warning (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 1

mysql> exit
Bye

F:\Program Files\Environment\mysql-5.7.30-winx64\bin>net stop mysql
MySQL 服务正在停止.
MySQL 服务已成功停止。

F:\Program Files\Environment\mysql-5.7.30-winx64\bin>net start mysql
MySQL 服务正在启动 .
MySQL 服务已经启动成功。


~~~

如果出现密码过期

~~~shell
F:\Program Files\Environment\mysql-5.7.30-winx64\bin>mysql -u root -p
Enter password: ******#原密码
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 3
Server version: 5.7.30

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> use mysql
# 错误提示：更改密码
ERROR 1820 (HY000): You must reset your password using ALTER USER statement before executing this statement.
# 更改密码语句
mysql> alter user 'root'@'localhost' identified by '12345678';
Query OK, 0 rows affected (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)

mysql> exit
Bye
~~~







## [mysql 5.7 压缩包安装教程](https://www.cnblogs.com/misscai/p/11026987.html)

**前言 ： 避免之前装的MySQL影响**

　　**首先进入dos窗口执行**

　　**sc delete mysql**   

　　**删除已有的mysql服务**

> **(一) 下载MySQL5.7 版本压缩包**

　　网址

　　https://dev.mysql.com/downloads/mysql/

　　![img](https://img2018.cnblogs.com/blog/1460613/201906/1460613-20190615110849645-2030916358.png)

 

> **(二)解压到自己想要放的目录**

　　我放在了F盘

　　**F:\Program Files\Environment\mysql-5.7.30-winx64**

　　**在这个目录下新建 data文件夹 和 my.ini文件 如下图所示**

　　**![img](https://img2018.cnblogs.com/blog/1460613/201906/1460613-20190615111204230-1401280674.png)**

　　 **用记事本打开my.ini  放入如下代码（basedir 和 datadir 的路径根据自己设置）。** 

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```ini
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8 
[mysqld]
#设置3306端口
port = 3306 
# 设置mysql的安装目录
basedir=F:\Program Files\Environment\mysql-5.7.30-winx64
# 设置mysql数据库的数据的存放目录
datadir=F:\Program Files\Environment\mysql-5.7.30-winx64\data

# 允许最大连接数
max_connections=200
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
skip-grant-tables
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

> **(三) 在环境变量里加入mysql的bin 路径**

　　**![img](https://img2018.cnblogs.com/blog/1460613/201906/1460613-20190615111720440-311179450.png)**

　　![img](https://img2018.cnblogs.com/blog/1460613/201906/1460613-20190615111805859-1829617923.png)

 

> **(四) 用管理员打开命令窗口**

　　**1 切换到mysql 的bin目录。**　

　　    **(1) 输入mysqld --initialize**

　　　　**![img](https://img2018.cnblogs.com/blog/1460613/201906/1460613-20190616144951734-223485393.png)**

　　　　**如果此处报错 Can't create/write to file 。。**

　　    **将my.ini文件如二 中的 basedir 和 datadir 路径见引号和双斜杠**　

　　　　**# 设置mysql的安装目录**
　　　　**basedir="D:\\tool\\Mysql\\mysql-5.7.26-winx64"**
　　　　**# 设置mysql数据库的数据的存放目录**
　　　　**datadir="D:\\tool\\Mysql\\mysql-5.7.26-winx64\\data"**

　　    **(2) 输入 mysqld --install**

　　　　**![img](https://img2018.cnblogs.com/blog/1460613/201906/1460613-20190616143456911-1894764195.png)**

　　　   **(3\**) 输入 net start mysql     启动服务\****

 　    **(4) 输入mysql -u root -p 回车 不用输入密码  继续回车进入数据库**

　　**2 输入 use mysql**

　　**3 输入 update mysql.user set authentication_string=password('12345678') where user='root';    设置数据库密码 适用于mysql 5.7版本**

　　**4 将修改 mysql中的 my.ini文件 删掉最后一行的代码（跳过表验证）**skip-grant-tables

　　**5 重启服务（要切换到mysql的bin目录！！！！！！！！）**  

　　　　**net stop mysql**

　　　　**net start mysql**

 

　　**![img](https://img2018.cnblogs.com/blog/1460613/201906/1460613-20190615112100278-1134652250.png)**

 

　　**这样MySQL就安装成功了！！！！！**



# MySQL8.0安装-Linux

参考博文：https://blog.csdn.net/qq_40596317/article/details/112917094

## mysql8.0 版本特性与介绍

相关文献地址
https://dev.mysql.com/doc/
mysql server 文献页
https://dev.mysql.com/doc/refman/8.0/en/

1、性能提升级。官方表示MySQL 8.0 的速度要比 MySQL 5.7 快 2 倍。MySQL 8.0 在读/写工作负载、IO 密集型工作负载、以及高竞争工作负载时相比MySQL5.7有更好的性能

2、更强的NoSQL文档支持。MySQL 从 5.7 版本开始提供 NoSQL 存储功能，目前在 8.0 版本中这部分功能也得到了更大的改进。该项功能消除了对独立的 NoSQL 文档数据库的需求，而 MySQL 文档存储也为 schema-less 模式的 JSON 文档提供了多文档事务支持和完整的 ACID 合规性。

3、窗口函数。也就是在满足某种条件的记录集合上执行的特殊函数。它可以用来实现若干新的查询方式。窗口函数与 SUM()、COUNT() 这种集合函数类似，但它不会将多行查询结果合并为一行，而 是将结果放回多行当中。即窗口函数不需要 GROUP BY。窗口函数的使用，将大大提高相关的分析型场景的效率。

4、UTF-8编码。从MySQL8.0开始，使用utf8mb4 作来MySQL的默认字符集，并支持 Unicode 9，默认字符集将从 latin1 改为 utf8mb4，默认定序collation将从latin1_swedish_ci 改为 utf8mb4_800_ci_ai；

5、隐藏索引。可以将索引通过命令设置为 隐藏 或 显示。对于被 隐藏 的索引，它不会被查询优化器所使用，我们可以使用这一功能，对相关的查询进行性能调试，通过 隐藏 或 显示，分析数据库性能差异的原因，同时也可以去除无效的索引。

```sql
--隐藏一个索引：
ALTER TABLE TABLENAME ALTER INDEX IDXNAME INVISIBLE;

--恢复显示该索引
ALTER TABLE TABLENAME ALTER INDEX IDXNAME VISIBLE;

```

6、持久化设置。MySQL8.0 新增 SET PERSIST 的命令，该命令的配置值保存到数据目录下的mysqld-auto.cnf文件中，待重启后，读取该文件，用其中的配置覆盖缺省的配置文件，补充了SET GLOBAL 命令只能临时生效的不足；
命令的使下如：

```sql
--恢复显示该索引
SET PERSIST max_connections = 400;
```

7、重构 BLOB。重构 BLOB 加速了片段读取/更新操作，可以加速 JSON 数据的操作。大幅改进了对 JSON 的支持，添加了基于路径查询参数从 JSON 字段中抽取数据的 JSON_EXTRACT() 函数，以及用于将数据分别组合到 JSON 数组和对象中的 JSON_ARRAYAGG() 和 JSON_OBJECTAGG() 聚合函数。

8、事务性数据字典。完全脱离了 MyISAM 存储引擎，真正将数据字典放到了 InnoDB 中的一些表中，不再需要 FRM、TRG、PAR 等文件；Information Schema 现在以数据字典表的一个视图出现。也就是原则上可以不需要 MyISAM 数据表类型，系统表都可以放到 InnoDB 之中。

9、SQL 角色。可以创建角色，给用户设置或去除角色，大大方便权限的管理。

其实还有很多相关特性，这里只是挑了些个人觉得比较重要的，要了解更多的信息，可以通过上述的文档链接查看。



## 1.上传文件到指定文件夹下并解压

下载压缩包：mysql-8.0.23-linux-glibc2.12-x86_64.tar.xz，上传到指定目录，如：/opt/mysql

~~~bash
cd   /opt/mysql
tar -xvf mysql-8.0.23-linux-glibc2.12-x86_64.tar.xz
mv mysql-8.0.23-linux-glibc2.12-x86_64 mysql-8.0.23  # 解压出来的文件夹名称较长，此处我们可以稍做修改

~~~

## 2.创建用户组以及用户和密码 并授权

~~~bash
#创建用户组以及用户和密码
groupadd mysql
useradd -g mysql mysql

#授权用户 （如：下列配置my.cnf 时指定的目录都需给mysql 用户授权）
chown -R mysql.mysql /opt/mysql/mysql-8.0.23
~~~

## 3.初始化基础信息 （切记切记 设置不区分大小写得在初始化时设置）

~~~bash
#创建 data 数据存储目录【在解压后的mysql-8.0.23目录下】
mkdir data 
#切换到bin 目录下
cd bin
#初始化基础信息  切记切记切记mysql8 一定要在初始化时设置 不区分大小写，不然后续修改和删除重装没区别
#初始化后在原始my.con下lower_case_table_names = 1 是无效的，所以一定要在初始化时加上  --lower-case-table-names=1
./mysqld --user=mysql --basedir=/opt/mysql/mysql-8.0.23 --datadir=/opt/mysql/mysql-8.0.23/data/ --initialize --lower-case-table-names=1

~~~

![img](https://img-blog.csdnimg.cn/20210121144514220.png)

得到系统初始化随机默认密码，此处得记录下密码，后续操作需要（敲黑板）

## 4.编辑my.cnf文件

my.cnf 还有很多可设置属性，详情请查看官方文档，此处仅设置主要参数
配置my.cnf 的文件路径 文件夹必须存在（不存在文件时，启动会提示文件不存在）

~~~bash
 #设置mysql的安装目录
basedir=/opt/mysql/mysql-8.0.23
 #设置mysql数据库的数据的存放目录  
datadir=/opt/mysql/mysql-8.0.23/data
 #设置客户端默认字符集
character-set-server=UTF8MB4
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
#设置是否区分大小写（初始化后此参数在这里也必须存在）
lower_case_table_names=1
# 默认使用“mysql_native_password”插件认证
default_authentication_plugin=mysql_native_password
#注释mysqld_safe 下的所有配置  系统会输出到   datadir目录下
#[mysqld_safe]
#log-error=/var/log/mysqld.log
#pid-file=/var/run/mysqld/mysqld.pid

~~~

## 5.添加mysqld服务到系统 授权以及添加服务

~~~bash
#进入主目录
cd /opt/mysql/mysql-8.0.23
#添加mysqld服务到系统
cp -a ./support-files/mysql.server /etc/init.d/mysql
#授权以及添加服务
chmod +x /etc/init.d/mysql
chkconfig --add mysql
~~~

## 6.启动服务 建立服务同步连接

~~~bash
service mysql start  #服务启动
service mysql status  #查看服务状态
service mysql stop  #停止服务
service mysql restart  #重启服务
~~~

当个别小伙伴启动服务的时候可能会提示文件夹没有权限 ，日志在 datadir 下可查看 设置mysql 权限即可

如：

```bash
chown -R mysql:mysql   /opt/mysql/mysql-8.0.23/data
```


建立服务同步连接（不明白 ln -s 的小伙伴可以百度查询一下该命令的作用 ）

```bash
ln -s /opt/mysql/mysql-8.0.23/bin/mysql /usr/bin
```

## 7.登录mysql 并修改密码

这里的登录密码就是第三步初始化获得的随机密码

~~~bash
#进入mysql 控台
mysql -uroot -p
#修改密码
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '你的密码';   
#刷新权限
flush privileges;  
~~~

## 8.配置外网连接授权

~~~bash
 #选择mysql数据库
 use mysql;
 #修改root 用户的连接地址现在  localhost 为本机 也可指定固定ip 此处 % 开启所有ip访问
 update user set host='%' where user='root';
 #刷新权限
 flush privileges;
~~~

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210121152406584.png)

## 9.退出控台 外网远程连接测试 (安装完毕)

```bash
exit
```





















