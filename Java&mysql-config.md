# JDK多版本配置

## JDK安装——推荐默认就行

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





# MySQL配置

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

