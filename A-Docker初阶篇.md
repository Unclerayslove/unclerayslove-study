# 基本介绍

分析：

JavaEE	Java	SringMVC/SpringBoot/Mybatis

Docker	Go	Swarm/Compose/Machine/mesos/k8s/-----CI/CD	jenkins整合

将正确的环境打个包，变成镜像Image，这样就可以拉取到其他的服务器上，有一模一样的环境了；达到应用程序跨平台间的无缝接轨运行

Docker的主要理念：Build，Ship and Run Any App，Anywhere。Linux容器技术【Linux Containers，缩写为LXC】的出现解决了这样一个问题，而Docker就是在他的基础上发展过来的。

**一句话：解决了运行环境和配置问题软件容器，方便做持续集成并有助于整体发布的容器虚拟化技术**

由于虚拟机技术存在一些缺点【启动分钟级、占用大量资源等】，Linux发展出了另一种虚拟化技术：Linux容器【Linux Containers，缩写为LXC】

**Linux容器不是模拟一个完整的操作系统，而是对进程进行隔离。**不需要捆绑一整套操作系统



安装前提条件：Docker运行在CentOS 7上，要求系统64位、系统内核版本为3.10以上【uname -r 查看系统内核版本】

```shell
# 查看系统内核版本
uname -r
3.10.0-862.el7.x86_64

# 查看系统版本
cat /etc/redhat-release
CentOS Linux release 7.5.1804 (Core)

```



Docker的架构图

![基本组成](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210514161127.png)



## Docker的基本组成

**镜像（image）：**

docker镜像好比是一个模板，可以通过这个模板来创建容器服务，如 tomcat镜像===>run===>tomcat01容器（提供服务器）/tomcat02，通过这个镜像可以创建多个容器（最终服务运行或者项目运行就是在容器中的）。

就好比一个java的.Class文件，类模板 通过这个模板可以生成多个实例

**容器（container）：**

Docker利用容器技术，独立运行一个或者一个组应用，通过镜像来创建的【容器是用镜像创建的运行实例】

容器：启动、停止、删除

可以把这个容器理解为一个简单的linux系统（包括root用户权限、进程空间、用户空间和网络空间等）和运行在其中的应用程序

容器的定义和镜像几乎一模一样，也是一堆层的统一视角，唯一区别在于容器的最上面

**仓库（repository）：**

仓库就是存放镜像的地方

仓库为公有仓库和私有仓库

Docker Hub

阿里云  网易云 华为云 都有容器服务器



## 安装Docker

```shell
# 1、如果有旧的版本 先卸载
yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine       
# 2、需要的安装包
yum install -y yum-utils

# 3、设置镜像的仓库
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo #默认是从国外的十分慢 这里改成国内的
# 推荐使用阿里云的 十分快
yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
    
# 4、安装docker相关的内容 docker-ce 社区版 ee是企业版 推荐使用ce
# 这是安装最新的docker版本
yum install docker-ce docker-ce-cli containerd.io  
# 根据需要也可以安装指定的版本
yum install docker-ce-<VERSION_STRING> docker-ce-cli-<VERSION_STRING> containerd.io

# 5、启动docker  可以通过docker version检查是否启动成功
systemctl start docker
systemctl restart docker
# 开机自启动  不是root用户 加sudo
sudo systemctl enable docker
# 查看docker的状态
systemctl status docker

```



```shell
# 6、启动hello-world进行测试
docker run hello-world
```

会先去pull镜像，然后启动，打印hello world



```bash
# 8、查看一下下载的hello-world 镜像
docker images

```

![image-20210514161635712](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210514161637.png)

REPOSITORY：镜像来自于哪个仓库

TAG：版本标记，latest表示最后版本

IMAGE ID：镜像的ID

CREATED：创建时间

SIZE：镜像大小



**了解：卸载Docker**

```bash
# 1、卸载依赖
yum remove docker-ce docker-ce-cli containerd.io

# 2、删除资源
rm -rf /var/lib/docker

# /var/lib/docker  是docker的默认工作路径

```

![image-20210514162306307](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210514162308.png)



## 阿里云镜像加速

1、在阿里云官网找到：

注册账号，找到镜像加速

2、配置使用

```bash
# 执行以下命令即可
sudo mkdir -p /etc/docker

sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://o1d594w0.mirror.aliyuncs.com"]
}
EOF

sudo systemctl daemon-reload
 
sudo systemctl restart docker
```



## Docker是怎么工作的

Docker是一个Client-Server结构的系统，Docker的守护进程运行在主机上【宿主机】。通过Socket从客户端访问

DockerServer接收到Docker-Client的指令，就会执行这个命令。

![工作流程](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210514162745.png)

容器，是一个运行时环境，就是我们前面说到的集装箱



![img](https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3029876800,3884924252&fm=26&gp=0.jpg)



**Docker为什么比VM快？**

1、Docker有着比虚拟机更少的抽象层【在宿主机上不需要Hypervisor、Guest OS，只需要一个Docker Engine 引擎即可】

2、Docker利用的是宿主机的内核，VM需要是Guest OS【客户操作系统，即VM虚拟机里面的系统】

3、Docker启动容器是秒级的；虚机是分钟级的

Host OS(主人操作系统）就是安装在你硬件设备上的系统，而Guest OS(客人操作系统）则是安装在虚拟机（VM）上面的系统。

Hypervisor：**虚拟机监视器**，是用来建立与执行[虚拟机器](https://baike.baidu.com/item/虚拟机器)的软件、固件或硬件。

![img](https://upload-images.jianshu.io/upload_images/12979420-a562cd670f2b8b02?imageMogr2/auto-orient/strip|imageView2/2/w/529/format/webp)



所以说,新建一个容器的时候,docker不需要像虚拟机一样重新安装一个操作系统内核,虚拟机是加载Guest OS,分钟级别的,而docker是利用宿主机的操作系统,省略了这个复杂的过程



# Docker的常用命令

## 帮助命令

```shell
docker version      #显示docker的版本信息
docker info			#显示docker的系统信息，包括镜像和容器的数量
docker 命令 --help   #万能帮助命令

```

帮助文档地址：https://docs.docker.com/engine/reference/commandline



## 镜像命令

### **docker images** 查看所有本地的主机上的镜像

```shell
[root@localhost /]# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hello-world         latest              bf756fb1ae65        5 months ago        13.3kB

# 解释
REPOSITORY	镜像的仓库源
TAG			镜像的标签
IMAGE ID	镜像的id
CREATED		镜像的创建时间
SIZE		镜像的大小

# 可选项
  -a, --all             # 列出所有的镜像【含中间镜像层】--镜像就类似千层饼，一层裹一层，我们可操作的就是最外面的一层
      --digests         Show digests
  -f, --filter filter   Filter output based on conditions provided
      --format string   Pretty-print images using a Go template
      --no-trunc        Don't truncate output
  -q, --quiet           # 只显示镜像的id  常用
  --digests				# 显示镜像的摘要信息
  --no-trunc			# 显示完整的镜像信息【完整的IMAGE ID 64位  一般只截取12位】
  
  docker images -aq #显示所有的镜像id

```

### **docker search 搜索镜像**

```shell
[root@localhost /]# docker search mysql
NAME           DESCRIPTION                                 STARS    OFFICIAL  AUTOMATED      
mysql       MySQL is a widely used, open-source relation…   9592     [OK]                
mariadb     MariaDB is a community-developed fork of MyS…   3486     [OK] 

# 可选项，通过搜藏来过滤
--filter=STARS=3000   # 搜索出来的镜像就是STARS大于3000的

-s
docker search -s number 镜像名	# 可以过滤掉stars小于number的镜像
--no-trunc	# 显示完整的镜像描述
--automated	# 只列出automated build【自动构建】类型的镜像

```

### **docker pull 下载镜像**

```shell
  -a, --all-tags                Download all tagged images in the repository
      --disable-content-trust   Skip image verification (default true)
      --platform string         Set platform if server is multi-platform capable
  -q, --quiet                   Suppress verbose output

# 下载镜像   docker pull 镜像名[:tag]  加版本 可选
[root@localhost /]# docker pull mysql
Using default tag: latest  # 如果不写tag 默认就是latest 最新版本
latest: Pulling from library/mysql
afb6ec6fdc1c: Pull complete  # 分层下载 docker images的核心 联合文件系统
0bdc5971ba40: Pull complete 
97ae94a2c729: Pull complete 
f777521d340e: Pull complete 
1393ff7fc871: Pull complete 
a499b89994d9: Pull complete 
7ebe8eefbafe: Pull complete 
597069368ef1: Pull complete 
ce39a5501878: Pull complete 
7d545bca14bf: Pull complete 
211e5bb2ae7b: Pull complete 
5914e537c077: Pull complete 
Digest: sha256:a31a277d8d39450220c722c1302a345c84206e7fd4cdb619e7face046e89031d #签名 最终得到这个镜像 最外面的一层
Status: Downloaded newer image for mysql:latest	# 标签
docker.io/library/mysql:latest  #真实地址

# 两者等价
docker pull mysql
docker pull docker.io/library/mysql:latest

# 指定版本下载
[root@localhost /]# docker pull mysql:5.7
5.7: Pulling from library/mysql
afb6ec6fdc1c: Already exists 
0bdc5971ba40: Already exists 
97ae94a2c729: Already exists 
f777521d340e: Already exists 
1393ff7fc871: Already exists 
a499b89994d9: Already exists 
7ebe8eefbafe: Already exists 
4eec965ae405: Pull complete 
a531a782d709: Pull complete 
270aeddb45e3: Pull complete 
b25569b61008: Pull complete 
Digest: sha256:d16d9ef7a4ecb29efcd1ba46d5a82bda3c28bd18c0f1e3b86ba54816211e1ac4
Status: Downloaded newer image for mysql:5.7
docker.io/library/mysql:5.7

```



![img](https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3668085801,3647900076&fm=26&gp=0.jpg)



### **docker rmi 删除镜像**

```shell
-f # 表示强制删除
# 因为镜像是分层的，所以删除的时候也是分层删除
docker rmi -f 镜像id  # 删除指定的镜像

docker rmi -f 镜像id 镜像id 镜像id # 删除多个镜像

docker rmi -f $(docker images -qa) # 删除全部的镜像

```



## 容器命令

**说明：有了镜像才可以创建容器，linux，下载一个centOS镜像来测试学习**

```shell
# 先拉取一个镜像
docker pull centos
```

### docker run [OPTIONS] image 新建容器并启动

```shell
docker run [可选参数] image  命令参数
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]	# COMMAND表示以什么命名启动 比如/bin/bash方式
# 参数说明
--name="Name"    # 容器名字  比如tomcat01 tomcat02 用来区分容器
-d               # 以后台方式运行
-it				 # 使用交互方式运行，进入容器查看内容 i：interactive交互模式运行容器  t：terminal 为容器重新分配一个伪输入终端
-p  			 # 指定容器的端口 -p 8080:8080
	-p ip:主机端口:容器端口
	-p 主机端口:容器端口（常用）
	-p 容器端口
	容器端口
-P  			 # 大写的P：随机指定端口

# 测试 启动并进入容器  /bin/bash：表示新建一个bash
[root@localhost /]# docker run -it centos /bin/bash
[root@1c7d2988e677 /]# ls   查看容器内的centos 基础版本 很多命令都是不完善的
bin  etc   lib	  lost+found  mnt  proc  run   srv  tmp  var
dev  home  lib64  media       opt  root  sbin  sys  usr

# 从容器中退回主机
[root@1c7d2988e677 /]# exit
exit

```

### docker ps [OPTIONS] 列出所有运行的容器

```shell
docker ps	# 列出当前正在运行的容器

-l	# last 列出上一个运行的容器
-a  # all 列出当前正在运行的容器 并带出历史运行的容器
-n	# number 列出上n次运行的容器 docker ps -n 3
-q	# 列出容器的ID

docker ps -a
[root@localhost /]# docker ps -a
CONTAINER ID    IMAGE        COMMAND       CREATED            STATUS                       PORTS        NAMES
1c7d2988e677    centos     "/bin/bash"   5 minutes ago    Exited (0) About a minute ago              frosty_booth
a39cfe3dd482   hello-world   "/hello"     2 hours ago      Exited (0) 2 hours ago                  hungry_mendeleev

# docker container ls 列出容器 命令 可以通过--help查看其他命令 
docker container stop docker-demo
docker container rm docker-demo

```

### 退出容器

~~~shell
exit		# 容器停止并退出
Ctrl+P+Q	# 容器不停止退出
~~~

### 停止/重启容器命名

~~~shell
# 停止容器命令
docker stop 容器id/容器名   或者  docker kill 容器id		# 强行杀掉
# 重启容器命令 根据docker ps -a 列出历史启动容器，选择需要的容器重启
docker start CONTAINERid
docker restart CONTAINERid
~~~

### 删除容器

~~~shell
docker rm [OPTIONS] CONTAINER [CONTAINER...]
-f # 强制删除
# 删除容器 docker ps -aq 列出所有容器id
docker rm containerId # 删除指定容器 

# 删除全部容器 加 -f 表示强制删除
docker rm -f $(docker ps -aq) 
docker ps -aq | xargs docker rm
~~~



## 常用其他命令

### 后台启动命令--启动守护式容器

```shell
# 后台启动命令 
docker run -d 镜像名
[root@localhost /]# docker run -d centos

# 问题docker ps 发现centos停止了

# 常见的坑：docker 容器使用后台运行 就必须要有一个前台进程，docker发现没有应用 就会自动停止。
# 容器运行的命令如果不是那些 一直挂起的命令（比如运行top，tail），就是会自动退出的。---这也是docker的机制，不浪费资源
# 所以最佳的解决方案是，将你要运行的容器以前台进程的形式运行

# 所以想要以后台方式运行并且不让容器自动停止 可以使用以下组合命令 -d 后台启动 -it 交互模式
docker run -dit 镜像名 /bin/bash

```

### 查看日志命令docker logs

```shell
docker logs 容器id	# 打印全部日志
docker logs -f -t --tail n[行数] 容器id
-f # 跟随最新的日志打印
-t # 加入时间戳
--tail n # 显示最后多少条

```

### 查看容器中的进程信息docker top

~~~shell
docker top 容器id

[root@localhost ~]# docker top 77d297e2e487
UID           PID         PPID          C        STIME          TTY           TIME               CMD
root          72077       72059         0        7月01           pts/0         00:01:23           java -jar /app.jar
root          75259       72059         0        7月01           pts/1         00:00:00           /bin/bash
UID 	# 用户ID		User Identification
PID 	# 进程ID		Process Identification
PPID	# 父进程ID	   Parent process ID

# 为什么可以使用top命令 ，因为可以把 docker容器看作是一个简易版的 Linux环境

~~~

### 查看镜像的元数据---容器内部细节docker inspect

镜像元数据的一些详解？？

~~~shell
# 查看元数据命令
docker inspect 容器id

# 测试
[root@localhost /]# docker inspect 841a3a922056
[
    {
    	# 容器id 能发现命令中的id只是这里面的一小部分
        "Id": "841a3a922056b8457e1283b8441edd0b8a10dd41e678890e5c23db0c68439547",
        # 创建时间
        "Created": "2020-06-09T02:34:14.239219132Z",
        # 交互前台路径
        "Path": "/bin/bash",
        # 携带参数
        "Args": [],
        # 容器状态
        "State": {
            "Status": "exited",	#当前容器已退出
            "Running": false,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 0,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2020-06-09T02:34:17.821193052Z",
            "FinishedAt": "2020-06-09T02:34:17.929737095Z"
        },
        # 镜像来源
        "Image": "sha256:470671670cac686c7cf0081e0b37da2e9f4f768ddc5f6a26102ccd1c6954c1ee",
        "ResolvConfPath": "/var/lib/docker/containers/841a3a922056b8457e1283b8441edd0b8a10dd41e678890e5c23db0c68439547/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/841a3a922056b8457e1283b8441edd0b8a10dd41e678890e5c23db0c68439547/hostname",
        "HostsPath": "/var/lib/docker/containers/841a3a922056b8457e1283b8441edd0b8a10dd41e678890e5c23db0c68439547/hosts",
        "LogPath": "/var/lib/docker/containers/841a3a922056b8457e1283b8441edd0b8a10dd41e678890e5c23db0c68439547/841a3a922056b8457e1283b8441edd0b8a10dd41e678890e5c23db0c68439547-json.log",
        "Name": "/wizardly_leavitt",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        # 主机配置
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "CapAdd": null,
            "CapDrop": null,
            "Capabilities": null,
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "ConsoleSize": [
                0,
                0
            ],
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": null,
            "BlkioDeviceWriteBps": null,
            "BlkioDeviceReadIOps": null,
            "BlkioDeviceWriteIOps": null,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "KernelMemory": 0,
            "KernelMemoryTCP": 0,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/e35ad11b8f9ba114f8159c9c27a15af4f860a2b3109126107fd210e846b80bbe-init/diff:/var/lib/docker/overlay2/b0f79a51d756cfe6a858140417bc4e90378bdc0208afc32d48273ac62c01297f/diff",
                "MergedDir": "/var/lib/docker/overlay2/e35ad11b8f9ba114f8159c9c27a15af4f860a2b3109126107fd210e846b80bbe/merged",
                "UpperDir": "/var/lib/docker/overlay2/e35ad11b8f9ba114f8159c9c27a15af4f860a2b3109126107fd210e846b80bbe/diff",
                "WorkDir": "/var/lib/docker/overlay2/e35ad11b8f9ba114f8159c9c27a15af4f860a2b3109126107fd210e846b80bbe/work"
            },
            "Name": "overlay2"
        },
        # 挂在信息
        "Mounts": [],
        # 基本配置
        "Config": {
            "Hostname": "841a3a922056",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            # 环境变量
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            # 命令行
            "Cmd": [
                "/bin/bash"
            ],
            "Image": "centos",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {
                "org.label-schema.build-date": "20200114",
                "org.label-schema.license": "GPLv2",
                "org.label-schema.name": "CentOS Base Image",
                "org.label-schema.schema-version": "1.0",
                "org.label-schema.vendor": "CentOS",
                "org.opencontainers.image.created": "2020-01-14 00:00:00-08:00",
                "org.opencontainers.image.licenses": "GPL-2.0-only",
                "org.opencontainers.image.title": "CentOS Base Image",
                "org.opencontainers.image.vendor": "CentOS"
            }
        },
        # 网络设置
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "0f420b4d304fd12ceaa2175089c94bac13727044e1b634be4fafa94558d78e87",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {},
            "SandboxKey": "/var/run/docker/netns/0f420b4d304f",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "",
            "Gateway": "",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "",
            "IPPrefixLen": 0,
            "IPv6Gateway": "",
            "MacAddress": "",
            "Networks": {
            	# 当前使用的网络工作模式
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "8c9cf5e51f2aa58fb54e977e67381fcc1644853a385ee93ac4f4ae663e00dfbe",
                    "EndpointID": "",
                    "Gateway": "",
                    "IPAddress": "",
                    "IPPrefixLen": 0,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "",
                    "DriverOpts": null
                }
            }
        }
    }
]
~~~



### 进入当前正在运行的容器docker exec/docker attach

~~~shell
# 我们容器通常都是使用后台方式 -d运行的，需要进入容器 修改一些配置  怎么进入？？
使用 exec
# 命令   it：使用交互的方式进入容器查看  /bin/bash 表示新建一个bash
docker exec -it 容器id bashShell【/bin/bash】

# 测试
[root@localhost /]# docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
675ae391a071        centos              "/bin/bash"         51 seconds ago      Up 49 seconds                           great_kilby
[root@localhost /]# docker exec -it 675ae391a071 /bin/bash
[root@675ae391a071 /]# ls
bin  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
[root@675ae391a071 /]# ps -ef
UID         PID   PPID  C STIME TTY          TIME CMD
root          1      0  0 02:55 pts/0    00:00:00 /bin/bash
root         17      0  0 02:57 pts/1    00:00:00 /bin/bash
root         31     17  0 02:57 pts/1    00:00:00 ps -ef

# 方式二
docker attach 容器id
# 测试
[root@localhost /]# docker attach 675ae391a071
正在执行当前的代码


# docker exec  		进入容器后开启一个新的终端 /bin/bash 可以在里面操作（常用）
# docker attach   	进入容器正在执行的终端 不会启动新的进程，如果exit退出，那么容器也将退出停止

~~~

### 从容器内拷贝文件到主机上docker cp

~~~shell
docker cp 容器id:容器内路径 目的的主机路径

docker cp xxx.tar.gz 启动的容器名:/路径
# 如 docker cp jdk-8u224-linux-x64.tar.gz mycentos:/root

~~~

## 小结

### Docker命令汇总

![小结](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210514160948.png)



~~~sh
Commands:
  attach      Attach local standard input, output, and error streams to a running container
  build       Build an image from a Dockerfile
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  diff        Inspect changes to files or directories on a container's filesystem
  events      Get real time events from the server
  exec        Run a command in a running container
  export      Export a container's filesystem as a tar archive
  history     Show the history of an image
  images      List images
  import      Import the contents from a tarball to create a filesystem image
  info        Display system-wide information
  inspect     Return low-level information on Docker objects
  kill        Kill one or more running containers
  load        Load an image from a tar archive or STDIN
  login       Log in to a Docker registry
  logout      Log out from a Docker registry
  logs        Fetch the logs of a container
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  ps          List containers
  pull        Pull an image or a repository from a registry
  push        Push an image or a repository to a registry
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  rmi         Remove one or more images
  run         Run a command in a new container
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  search      Search the Docker Hub for images
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers
  update      Update configuration of one or more containers
  version     Show the Docker version information
  wait        Block until one or more containers stop, then print their exit codes

~~~



## 测试练习

### 部署Nginx

~~~shell
# 1、搜索镜像 docker search nginx
# 2、拉取镜像 docker pull nginx
# 3、查看镜像 docker images
# 4、启动镜像容器 docker run -d --name nginx01 -p 8888:80 nginx

[root@localhost ~]# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
nginx               latest              4392e5dad77d        6 days ago          132MB
mysql               latest              30f937e841c8        2 weeks ago         541MB
centos              latest              470671670cac        4 months ago        237MB

# -d 代表后台运行
# --name 给容器命名
# -p 宿主机端口:容器内部端口
[root@localhost ~]# docker run -d --name nginx01 -p 3344:80 nginx
d76797b94e743d9134b67225ed9f8a102c994da7eb0c960770a1c405e373c7c9
[root@localhost ~]# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                  NAMES
d76797b94e74        nginx               "/docker-entrypoint.…"   11 seconds ago      Up 8 seconds        0.0.0.0:3344->80/tcp   nginx01
675ae391a071        centos              "/bin/bash"              3 hours ago         Up 3 hours                                 great_kilby
[root@localhost ~]# curl localhost:3344

# 进入容器  这是别人制作好的容器，可以查看默认的nginx 配置
[root@localhost ~]# docker exec -it nginx01 /bin/bash
root@d76797b94e74:/# whereis nginx
nginx: /usr/sbin/nginx /usr/lib/nginx /etc/nginx /usr/share/nginx
root@d76797b94e74:/# cd /etc/nginx/
root@d76797b94e74:/etc/nginx# ls
conf.d	fastcgi_params	koi-utf  koi-win  mime.types  modules  nginx.conf  scgi_params	uwsgi_params  win-utf
root@d76797b94e74:/etc/nginx# cd conf.d/ 
# cd到conf.d 目录下 有一个默认的配置文件
root@d76797b94e74:/etc/nginx/conf.d# ls
default.conf
~~~

**端口暴露的概念**

![端口暴露](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210514163021.png)



### 部署tomcat

~~~shell
# 官方的使用
docker run -it --rm tomcat:9.0

# 我们之前的启动都是后台，停止了容器之后，还能查到  docker run -it --rm 一般用来测试 用完即删除   --rm 用完即删

# 初期使用 还是先下载 再启动
docker pull tomcat:9.0

# 启动运行
docker run -d -p 3355:8080 --name tomcat01 tomcat

# 测试访问没有问题
# 进入容器
docker exec -it tomcat01 /bin/bash

# 发现问题：1、linux命令少了 2、没有webapps 阿里云镜像的原因， 默认是最小的镜像，所有不必要都剔除掉
# 保证最小可运行的环境
~~~

思考问题：我们以后要部署项目，如果每次都要进入到容器是不是很麻烦？我们要是可以在容器外部提供一个映射路径，比如：webapps，我们在外部放置项目，就自动同步到内部就好了



# Docker镜像

## Docker镜像是什么？ UnionFS（联合文件系统）

镜像是一种轻量级、可执行的独立软件包，用来打包软件运行环境和基于运行环境的开发软件，它包含运行某个软件所需的所有内容，包括代码、运行时、库、环境变量和配置文件。

Union文件系统(UnionFS) 是一种分层、轻量级并且高性能的文件系统，他**支持对文件系统的修改作为一次提交来层层的叠加**，同时可以将不同目录挂载到同一个虚拟文件系统下（unite several directories into a single virtual filesystem）。Union文件系统是Docker镜像的基础。镜像可以通过分层来进行集成，基于基础镜像（没有父镜像），可以制作各种具体的应用镜像。

特性：一次同时加载多个文件系统，但从外面看起来，只能看到一个文件系统你那个，联合加载会把各层文件系统叠加起来，这样最终的文件系统会包含所有底层文件和目录。



## Docker镜像加载原理

docker 的镜像实际上由一层一层的文件系统组成，这种层级的文件系统UnionFS。

bootfs(boot file system，根文件系统) 主要包含bootloader和kernel，bootloader 主要是引导加载kernel，Linux刚启动时会加载bootfs文件系统，**在Docker镜像的最底层是bootfs**。这一层与我们典型的Linux/Unix系统是一样的，包含boot加载器和内核。当boot加载完成之后整个内核就存在内存中了，此时内存的使用权已由bootfs转交给内核，此时系统也会卸载bootfs。

roorfs （root file system），在bootfs之上。包含的就是典型Linux系统中的 /dev ，/proc，/bin ，/etx 等标准的目录和文件。rootfs就是各种不同的操作系统发行版。比如Ubuntu，Centos等等。

![镜像加载原理](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210514163219.png)

对于一个精简的OS，rootfs可以很小，只需要包括最基本的命令、工具和程序库就可以了，因为底层直接用Host（宿主机）的kernel，自己只需要提供rootfs就行了，由此可见对于不同的Linux发行版，bootfs基本是一致的，rootfs会有差别，因此不同的发行版可以公用bootfs。



![img](https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=2584226687,1601050733&fm=26&gp=0.jpg)



分层的镜像

Docker 镜像联合文件系统分层，Tomcat镜像示例

![img](https://img2018.cnblogs.com/blog/1185883/201907/1185883-20190705114018923-574032187.png)

为什么Docker镜像要采用这种分层结构呢

采用这种分层结构最大的一个好处就是共享资源，比如有多个镜像都从相同的base镜像构建而来，那么宿主机只需要在磁盘上保存一份base镜像，同时内存中也只需要加载一份base镜像，就可以为所有容器服务了。而且镜像的每一层都可以被共享。



特点

docker 镜像都是只读的，当容器启动时，一个新的可写层被加载到镜像的顶部。这一层通常被称作 “容器层” ，“容器层” 之下的都叫镜像层。



## docker commit镜像

~~~shell
# 提交正在运行容器的副本成为一个新的镜像 提交到本地；提交完成后 可用docker images命令查看
docker commit 

# 命令和git原理类似
docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]
	-a, --author string: 提交的作者名称
	-c, --change list: 使用Dockerfile指令来创建镜像【对创建的映像应用Dockerfile指令】
	-m, --message string: 提交信息
	-p, --pause: 在commit时，将容器暂停
docker commit -m="提交的描述信息" -a="提交的作者" 容器id xxx/目标镜像名:[TAG] # xxx/这是前缀【类似于包名 便于区别】

# 先设置镜像标签【docker hub有示例】
# 推送到远程仓库上去 需要dockerhub【或者阿里云】的用户名和密码
docker login(回车，输入帐号和密码)

docker push myimages:tag


# 镜像打包
1、docker save -o /root/xxx.tar或者xxx.tar.gz # 镜像打包
2、scp xxx.tar 其他服务器ip:/root	# 将打包的镜像上传到其他的服务器上
3、docker load -i /root/xxx.tar # 导入镜像

# 容器打包  
1、docker export -o /root/xxxname.tar xxxname	# 容器打包
2、docker import xxxname.tar 容器name:tag	#导入容器


~~~



**=====================================以上算是入门了==========================================**



# 容器数据卷【volume】

## 什么是容器数据卷

容器内数据直接映射到本地宿主机。

**docker的理念**

将应用和环境打包成一个镜像

数据？如果数据都在容器中，那么我们容器删除，数据就会丢失   ==需求：==数据可以持久化

MySQL 容器删了 删库跑路   ==需求==MySQL数据可以存储在本地

如何解决？容器之间有一个数据共享技术！Docker容器中产生的数据，同步到本地！

这就是卷技术。 目录的挂载，将我们容器内的目录，挂载到Liunx上面



使用 volume 有四大优势：

- volume 可以在容器之间以及容器和主机之间共享和重用。
- volume 在某一挂载的位置被修改，所有使用该 volume 的地方都会同时更新。
- volume 的更新不会影响镜像。
- volume 会一直存在，直到没有任何容器使用它，才能使用 `docker volume rm [volumes名字]` 命令删除。


作者：yongxinz
链接：https://juejin.cn/post/6844904201340846093
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



**总结一句话：容器的持久化和同步操作！容器间也是可以数据共享的！**

作用：

1、实现容器数据的可持久化

2、容器数据同步【类似于vue的双向绑定，一边更改数据，另一边也会更改】

文章链接：https://juejin.im/post/5ef8a4b6f265da22c8569fae

## 使用数据卷【Data Volumes】

### 方式一：启动容器时直接使用命令来挂载 -v

~~~shell
docker run -dit -v /宿主机绝对路径目录:/容器内目录 镜像名

# 测试
[root@localhost /]# docker run -it -v /home/ceshi:/home centos /bin/bash
/myDataVolume:/dataVolumeContainer

# 启动起来后 回到linux目录 通过 docker inspect 容器id 查看
docker inspect containerId
[root@localhost ~]# docker inspect 3ae551380c79
"Mounts": [
            {
                "Type": "bind",
                "Source": "/home/ceshi",   	#主机内地址
                "Destination": "/home",		#docker容器内地址
                "Mode": "",
                "RW": true,
                "Propagation": "rprivate"
            }
        ],

# 使用容器卷的好处：以后修改只需要在本地修改即可，容器内会自动同步

1、容器和宿主机之间的数据共享
2、容器退出后，主机修改数据后数据依然能同步【再次启动该容器】----有点类似于redis的rdb和aof，重启之后做一个数据的拉取【硬盘--内存】
3、命令（带权限）----docker run it -v /宿主机绝对路径目录:/容器内目录:ro 镜像名 # ro：Read-only  容器内只能读取不能修改，主机可以RW

~~~

数据卷挂载后，宿主机和容器的数据是共享

### 方式二：使用DockerFile构建镜像时来添加

是什么？用java来对比  就是类似于java文件的编译源码 class文件

JavaEE Hello.java		------------>		Hello.class

Docker images			------------>		DockerFile  是镜像这个模板的描述文件，有自己的语法

~~~shell
# 示例 在宿主机/home/dockerfile目录下建一个Dockerfile文件
FROM centos
VOLUME ["/dataVolumeContainer1","/dataVolumeContainer2"]
CMD echo "finished,-----------success1"	# echo 用于字符串的输出，echo输出打印命令
CMD /bin/bash

等同于 docker run -it -v /host1:/dataVolumeContainer1 -v /host2:/dataVolumeContainer2 /bin/bash

# 在dockerfile目录下 构建镜像
docker build -f /dockerfile/Dockerfile -t uncleray/centos .

# 构建成功后，启动这个容器 docker inspect 容器id 查看 宿主机挂载的默认目录  对应两个
"Mounts": [
            {
                "Type": "volume",
                "Name": "6d323c666dc2f057eb6ea9420c951ec3d42914d2562627b66091710a66762660",
                "Source": "/var/lib/docker/volumes/6d323c666dc2f057eb6ea9420c951ec3d42914d2562627b66091710a66762660/_data",
                "Destination": "/dataVolumeContainer1",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            },
            {
                "Type": "volume",
                "Name": "4d80790798f235e8611f644dcd233e3ac7a99947e504884b48747ccb587d5862",
                "Source": "/var/lib/docker/volumes/4d80790798f235e8611f644dcd233e3ac7a99947e504884b48747ccb587d5862/_data",
                "Destination": "/dataVolumeContainer2",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            }
        ],


~~~

## 数据卷容器【Data Volume Containers】

使用特定容器维护数据卷

### 命令：--volumes-from

是什么？

命名的容器挂载数据卷，其他容器通过挂载这个（父容器）实现数据共享，挂载数据卷的容器，称之为 数据卷容器。

容器间传递共享（`--volumes-from`）

~~~shell
# 示例
1、启动doc01为父容器
docker run -it --name dc01 uncleray/centos
[root@d4d8301632b5 /]# cd dataVolumeContainer2
[root@d4d8301632b5 dataVolumeContainer2]# touch dc01_add.txt

2、dc02 继承自dc01
docker run -it --name dc02 --volumes-from dc01 uncleray/centos
[root@8c81dd9aab98 /]# cd dataVolumeContainer2
[root@8c81dd9aab98 dataVolumeContainer2]# ls
dc01_add.txt
# 发现 dc02的dataVolumeContainer2中也有了dc01_add.txt这个文件，说明数据共享成功

3、dc03 继承自dc01
docker run -it --name dc03 --volumes-from dc01 uncleray/centos
[root@4101ab06444b /]# cd dataVolumeContainer2
[root@4101ab06444b dataVolumeContainer2]# ls
dc01_add.txt  dc02_add.txt
# 发现 dc03的dataVolumeContainer2中也有了dc01_add.txt和dc01_add.txt这两个文件，说明数据共享成功

4、ctrl+P+Q退出之后，再次进入到dc01
[root@localhost /]# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS              PORTS                    NAMES
4101ab06444b        uncleray/centos     "/bin/sh -c /bin/bash"   About a minute ago   Up About a minute                            dc03
8c81dd9aab98        uncleray/centos     "/bin/sh -c /bin/bash"   4 minutes ago        Up 4 minutes                                 dc02
d4d8301632b5        uncleray/centos     "/bin/sh -c /bin/bash"   10 minutes ago       Up 10 minutes                                dc01
[root@localhost /]# docker attach dc01
[root@d4d8301632b5 dataVolumeContainer2]# ls
dc01_add.txt  dc02_add.txt  dc03_add.txt
# 发现dc01也有了创建的所有文件，结论：容器之间既达到了继承，又达到了数据共享的效果


5、把dc01容器（父容器）删除之后，dc02/dc03的数据是否还在呢？
答案：数据还在
此时在dc02容器中touch dc02_update.txt文件后，因为dc01父容器已经被删除，那么dc03是否有这个数据文件呢？
答案：完全还在，因为数据的共享是ok的

# ！！！结论：容器之间配置信息的传递，数据卷的生命周期一直持续到没有容器使用它为止。
~~~

**结论：容器之间配置信息的传递，数据卷的生命周期一直持续到没有容器使用它为止。**



## 实战：安装MySQL

思考：MySQL的数据持久化的问题 

~~~shell
# 获取镜像
[root@localhost ~]# docker pull mysql:5.7

# 运行容器 需要做数据挂载  安装启动mysql 需要配置密码 需要注意
# 官方测试 -e MYSQL_ROOT_PASSWORD=my-secret-pw

-v 卷挂载
-e 环境配置
--name 镜像名字
[root@localhost ~]# docker run -d -p 3310:3306 -v /home/mysql/conf:/etc/mysql/conf.d -v /home/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 --name mysql01 mysql:5.7

# 启动成功之后 本地使用sqlyog 连接成功

# 即使将容器删除 挂载到本地的数据卷依旧没有丢失 这就实现了容器数据化持久功能

~~~

## 具名和匿名挂载

~~~shell
# 匿名挂载  -v  【volume】
# 匿名挂载 -v 只写了容器内的路径 没有写容器外的路径
-v 容器内路径
-P 随机给一个端口
如：docker run -d -P -v /etc/nginx --name nginx01 nginx
# 挂载的容器卷是一个随机名字
DRIVER    VOLUME NAME
local     047ae3c363056e261afeefca37bd74fde95627bf4bcabc887776ba61b3fb53e1

# 具名挂载 -P：随机映射端口
如：docker run -d -P -v juming-nginx:/etc/nginx --name nginx02 nginx
docker volume ls # 可以查看数据卷，这时挂载的容器卷就是我们命名的名字
DRIVER    VOLUME NAME
local	  juming-nginx

# 查看一下这个卷 挂载的目录
docker volume inspect 数据卷名称
docker volume inspect juming-nginx

# 所有的docker容器内的卷 没有指定目录的情况下都是在 /var/lib/docker/volumes/xxxx/_data 下

# 我们通过具名挂载可以方便的找到我们的 一个卷 大多数情况下在使用 具名挂载

# 如何确定是你匿名挂载 、具名挂载还是指定路径挂载
-v 容器内路径		 # 匿名挂载
-v 卷名:容器内路径	    # 具名挂载
-v /宿主机路径:容器内路径 #指定路径挂载


Mount：挂载
Mountpoint：挂载点
~~~

Docker指定目录挂载、具名挂载、匿名挂载：https://blog.csdn.net/weixin_44231148/article/details/114446492

拓展：

~~~shell
# 加一个ro/rw  只读/读写  改变读写权限

docker run -d -P --name nginx02 -v juming-nginx:/etc/nginx:ro nginx
docker run -d -P --name nginx02 -v juming-nginx:/etc/nginx:rw nginx

# ro 只要看到ro说明这个路径只能通过宿主机来操作，容器内部无法操作
~~~

## 初始Dockerfile

Dockerfile就是用来构建docker镜像的构建文件 命令脚本 

通过这个脚本可以生成镜像，镜像是一层一层的 脚本是一个个的命令 每个命令都是一层

~~~shell
# 创建一个dockerfile文件 名字可以随机 建议 Dockerfile 官方默认命名，build的时候可以自动找到这个文件构建
# 文件中的内容：指令 参数
FROM centos

VOLUME ["volume01","volume02"]

CMD echo "----end----"
CMD /bin/bash
# 这里的每个命令 就是镜像的一层

# 查看文件命令
cat filename 
~~~



# DockerFile

## DockerFIle介绍

**Dockerfile就是用来构建docker镜像的构建文件！ 命令参数脚本**

构建步骤：

1、编写一个dockerfile 文件

2、docker build 构建成为一个镜像

3、docker run 运行镜像

4、docker push 发布镜像（DockerHub、阿里云镜像仓库）

**可以在官网搜索一个镜像点进去，选择一个镜像版本，进入到dockerhub，会有详细的Dockerfile** 

官方镜像都是基础包，很多功能都没有，所以我们通常需要自己搭建自己的镜像

比如自己想要一个centos的镜像，希望带环境：centos + jdk8 + tomcat + MySQL + Redis等。那就自己制作一个镜像



## 环境介绍

**1.Dockerfile中所用的所有文件一定要和Dockerfile文件在同一级父目录下，可以为Dockerfile父目录的子目录**
**2.Dockerfile中相对路径默认都是Dockerfile所在的目录**
**3.Dockerfile中一定要惜字如金，能写到一行的指令，一定要写到一行，原因是分层构建，联合挂载这个特性。**
**Dockerfile中每一条指令被视为一层**
**4.Dockerfile中指明大写（约定俗成）**



## DockerFile构建过程

**基础知识：**

1、每个保留关键字（指令）都必须是大写字母

2、执行从上到下顺序执行

3、# 表示注释

4、每一个指令都会创建一个新的镜像层，并提交

![Dockerfile构建过程](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210514164016.png)



dockerfile是面向开发的，我们以后要发布项目，做镜像，就需要编写dockerfile文件，这个文件十分简单

Docker镜像逐渐成为企业交付的标准 必须要掌握

步骤：开发、部署、运维。。。缺一不可

DockerFile：构建文件，定义了一切的步骤！类似于源代码

DockerImages：通过DockerFile构建生成的镜像，最终发布和运行的产品。原来是一个jar、war

DockerContainer：容器就是镜像运行起来提供服务

## DockerFile的保留字指令[DSL语法]

以前的话我们就是使用别人的，现在我们知道了这些命令后 我们来练习写一个自己的镜像

~~~shell
FROM			# 基础镜像 一切从这里开始构建 如：centos
MAINTAINER		# 镜像是谁写的 姓名+邮箱  【maintainer：维修人员】
ENV				# 构建的时候设置环境变量
RUN				# 镜像构建的时候需要运行的命令
ADD				# 拷贝压缩文件+解压缩----将宿主机目录下的文件拷贝进镜像且ADD命令会自动处理URL和解压tar压缩包
COPY			# 类似ADD命令，将我们的文件和目录拷贝到镜像中----只是拷贝 COPY src dest 或者 COPY ["src","dest"]。将从构建上下文目录中<源路径>的文件/目录复制到新的一层镜像内的<目标路径>位置
WORKDIR			# 指定在创建容器后，终端默认登录进来的工作目录
VOLUME			# 挂载的目录----容器数据卷
EXPOSE			# 保留端口配置。EXPOSE命令只是声明了容器应该打开的端口并没有实际上将它打开!
CMD				# 【容器启动时执行】COMMAND 指定这个容器启动的时候要运行的命令----可以有多个CMD指令，但是只有最后一个会生效，CMD会被docker run之后的参数替代
ENTRYPOINT		# 【容器启动时执行】指定这个容器启动的时候要运行的命令----可以追加命令
ONBUILD			# 当构建一个被继承Dockerfile 这个时候就会运行 ONBUILD的指令 触发指令

~~~

EXPOSE：EXPOSE在dockerfile中暴露出容器将要提供服务所开放的端口。run的时候直接 docker run -d --net=host  image:tag 这样可以不手动-p指定端口映射关系，更简洁了，从而使EXPOSE发挥最大的作用。而不是简单的随机映射宿主机&&起到注释作用。

而这么做不灵活点在于宿主机的端口被EXPOSE固定。如果宿主机端口被其他进程占用，就port already in use了。





## 练习

~~~dockerfile
# 指定基础镜像开始，scratch：空镜像，如果要自己完全制作一个Linux系统镜像，可以选择从这个空镜像开始。
# 可以是alpine【阿尔派：最小基础镜像】，Alpine Linux 是一个社区开发的面向安全应用的轻量级Linux发行版
# debian【通用的操作系统】 “Debian” 常指Debian GNU/Linux
# centos/fedora/ubuntu
FROM centos:7	#基于centos 7 版本
MAINTAINER mycentos<979803156@qq.com>

#ADD
#COPY
# 执行yum命令安装一些功能或命令
RUN yum install -y vim
RUN yum install -y ll
RUN yum install -y net-tools

ENV MYPATH /usr/local
WORKDIR $MYPATH

CMD /bin/bash
~~~



## 实战测试

Dockers Hub 中99%镜像都是从这个基础镜像过来的 `FROM scratch`，然后配置需要的软件和配置来进行构建

比如这个centos镜像的构建

![image-20210516103608171](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516103609.png)

~~~dockerfile
  
FROM scratch	#最基层的镜像，从零开始
ADD centos-7-x86_64-docker.tar.xz /	#add添加一个centos的压缩包

LABEL \
    org.label-schema.schema-version="1.0" \
    org.label-schema.name="CentOS Base Image" \
    org.label-schema.vendor="CentOS" \
    org.label-schema.license="GPLv2" \
    org.label-schema.build-date="20201113" \
    org.opencontainers.image.title="CentOS Base Image" \
    org.opencontainers.image.vendor="CentOS" \
    org.opencontainers.image.licenses="GPL-2.0-only" \
    org.opencontainers.image.created="2020-11-13 00:00:00+00:00"

CMD ["/bin/bash"]
~~~



### 创建一个自制版的centos

~~~shell
# 1、编写Dockerfile的文件  所用到的文件一定要在与Dockerfile文件同级目录下
[root@localhost dockerfile]# vim mydockerfile-centos
# 引入基础镜像
FROM centos	# 从官方的centos开始
# 指定作者 一般姓名+邮箱
MAINTAINER leipei<979803156@qq.com>

ENV MYPATH /usr/local
WORKDIR $MYPATH

# 通过yum 命令 安装一些命令 如 vim ll 等
RUN yum -y install vim
RUN yum -y install ll
RUN yum -y install net-tools

EXPOSE 80

CMD echo $MYPATH
CMD echo "---end---"
CMD /bin/bash

# 2、通过这个文件构建镜像
docker build . # 该命令会在当前目录下寻找Dockerfile文件，并自动完成构建；注意最后有一个点 .  这个点代表当前目录
-t xxx # 表示给构建完成的镜像取一个名字
-f # 表示DockerFile的文件路径（如果是官方命名：Dockerfile，可以不加 -f 会自动识别构建）

docker build -f mydockerfile-centos -t mycentos:0.1 .
[root@localhost dockerfile]# docker build -f mydockerfile-centos -t mycentos:0.1 .
# 命令 docker build -f dockerfile文件路径 -t 镜像名:[tag]
Successfully built 3c765e6c3c76
Successfully tagged mycentos:0.1

# 如果出现IPv4 forwarding is disabled. Networking will not work 这样的问题 解决办法：重启network和docker服务
systemctl restart network && systemctl restart docker

# 3、测试运行
原生版本的centos 没有vim、ifconfig 等命令 并且默认是root目录

增强之后的版本 有这些命令 并且设置了初始工作目录为 /usr/local
~~~



我们可以列出本地进行变更历史

~~~shell
docker history 镜像id
# 顺着加载，倒着执行。就像java的方法执行 压栈
~~~

![image-20210516105020399](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516105021.png)

那么通过这个命令，我们平时拿到镜像 可以研究一下它是怎么做的

**CMD 和 ENTRYPOINT 区别**

~~~shell
CMD						# 指定这个容器启动的时候要运行的命令 只有最后一个会生效 可被替代
ENTRYPOINT				# 指定这个容器启动的时候要运行的命令 可以追加命令
~~~

**测试CMD**

~~~shell
# 编写dockerfile文件
[root@localhost dockerfile]# vim dockerfile-cmd-test
FROM centos
CMD ["ls","-a"]

# 构建镜像
[root@localhost dockerfile]# docker build -f dockerfile-cmd-test -t cmdtest .
Sending build context to Docker daemon  3.072kB
Step 1/2 : FROM centos
 ---> 470671670cac
Step 2/2 : CMD ["ls","-a"]
 ---> Running in 5b52d021b77b
Removing intermediate container 5b52d021b77b
 ---> 76f9d91df0d5
Successfully built 76f9d91df0d5
Successfully tagged cmdtest:latest

# run运行 发现我们的ls -a命令生效了
[root@localhost dockerfile]# docker run 76f9d91df0d5
.
..
.dockerenv
bin
dev
etc
home
lib
lib64
lost+found
media
mnt
opt
proc
root
run
sbin
srv
sys
tmp
usr
var

# 想追加一个命令 -l  ls -al
[root@localhost dockerfile]# docker run 76f9d91df0d5 -l
docker: Error response from daemon: OCI runtime create failed: container_linux.go:349: starting container process caused "exec: \"-l\": executable file not found in $PATH": unknown.

# cmd的清理下 -l 替换了CMD ["ls","-a"] 命令， -l不是命令 所以报错
~~~

**测试ENTRYPOINT**

~~~shell
[root@localhost dockerfile]# vim dockerfile-cmd-entrypoint
FROM centos
ENTRYPOINT ["ls","-a"]


[root@localhost dockerfile]# docker build -f dockerfile-cmd-entrypoint -t entrypoint-test .
Sending build context to Docker daemon  4.096kB
Step 1/2 : FROM centos
 ---> 470671670cac
Step 2/2 : ENTRYPOINT ["ls","-a"]
 ---> Running in 67eba98ca9af
Removing intermediate container 67eba98ca9af
 ---> e3fede49255a
Successfully built e3fede49255a
Successfully tagged entrypoint-test:latest
[root@localhost dockerfile]# docker run e3fede49255a
.
..
.dockerenv
bin
dev
etc
home
lib
lib64
lost+found
media
mnt
opt
proc
root
run
sbin
srv
sys
tmp
usr
var

# 我们的追加命令，是直接拼接在我们的ENTRYPOINT 命令的后面的
[root@localhost dockerfile]# docker run e3fede49255a -l
total 0
drwxr-xr-x.   1 root root   6 Jun 11 09:16 .
drwxr-xr-x.   1 root root   6 Jun 11 09:16 ..
-rwxr-xr-x.   1 root root   0 Jun 11 09:16 .dockerenv
lrwxrwxrwx.   1 root root   7 May 11  2019 bin -> usr/bin
drwxr-xr-x.   5 root root 340 Jun 11 09:16 dev
drwxr-xr-x.   1 root root  66 Jun 11 09:16 etc
drwxr-xr-x.   2 root root   6 May 11  2019 home
lrwxrwxrwx.   1 root root   7 May 11  2019 lib -> usr/lib
lrwxrwxrwx.   1 root root   9 May 11  2019 lib64 -> usr/lib64
drwx------.   2 root root   6 Jan 13 21:48 lost+found
drwxr-xr-x.   2 root root   6 May 11  2019 media
drwxr-xr-x.   2 root root   6 May 11  2019 mnt
drwxr-xr-x.   2 root root   6 May 11  2019 opt
dr-xr-xr-x. 237 root root   0 Jun 11 09:16 proc
dr-xr-x---.   2 root root 162 Jan 13 21:49 root
drwxr-xr-x.  11 root root 163 Jan 13 21:49 run
lrwxrwxrwx.   1 root root   8 May 11  2019 sbin -> usr/sbin
drwxr-xr-x.   2 root root   6 May 11  2019 srv
dr-xr-xr-x.  13 root root   0 May 27 04:32 sys
drwxrwxrwt.   7 root root 145 Jan 13 21:49 tmp
drwxr-xr-x.  12 root root 144 Jan 13 21:49 usr
drwxr-xr-x.  20 root root 262 Jan 13 21:49 var

~~~

Dockerfile中很多命令都十分地相似，我们需要了解他们的区别，最好的学习就是对比他们然后测试效果！



### 实战：Tomcat镜像

**1、准备镜像文件 tomcat压缩包，jdk的压缩包**  

```shell
# 我自己的路径为 /home/leipei/build/tomcat 将压缩包放在这个目录下   一般解压会自动把解压后的文件放在/usr/local/目录下
[root@localhost tomcat]# pwd
/home/leipei/build/tomcat

touch file            #创建一个名为“file”的新的空白文件
touch readme.txt
```

**2、编写dockerfile文件，官方命名 `Dockerfile`，build会自动寻找这个文件，就不需要`-f`指定了。**

~~~dockerfile
FROM centos
MAINTAINER leipei<979803156@qq.com>

# 拷贝文件之后 并且重命名了
COPY readme.txt /usr/local/cincontainer.txt

# 添加压缩包 拷贝过去后会自动解压
ADD jdk-8u241-linux-x64.tar.gz /usr/local/
ADD apache-tomcat-9.0.22.tar.gz /usr/local/

# 运行指定的命令
RUN yum -y install vim

# 配置环境变量
ENV MYPATH /usr/local
# 指定当前工作目录，相当于cd  cd /usr/local
WORKDIR $MYPATH	#工作目录

# JDK环境变量配置  使用变量的方式为 $varname	${varname}	${varname:-default value}	${varname:+default value}
# 第一种和第二种相同 第三种表示当变量不存在使用-号后面的值 第四种表示当变量存在时使用+号后面的值（当然不存在也是使用后面的值）
ENV JAVA_HOME /usr/local/jdk1.8.0_241
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
# tomcat环境变量配置
ENV CATALINA_HOME /usr/local/apache-tomcat-9.0.22
ENV CATALINA_BASE /usr/local/apache-tomcat-9.0.22
ENV PATH $PATH:$JAVA_HOME/bin:$CATALINA_HOME/lib:$CATALINA_HOME/bin
# 容器运行时监听的端口
# EXPOSE 8080
# 启动时运行tomcat
# ENTRYPOINT ["/usr/local/apache-tomcat-9.0.22/bin/startup.sh"]
# CMD ["/usr/local/apache-tomcat-9.0.22/bin/startup.sh","run"]
# 容器启动时默认命令或参数 CMD ["executable","param1","param2"]或CMD ["param1","param2"]或CMD command param1 param2
CMD /usr/local/apache-tomcat-9.0.22/bin/startup.sh && tail -F /usr/local/apache-tomcat-9.0.22/bin/logs/catalina.out

# 不要把RUN和CMD搞混了。
# RUN是构件容器时就运行的命令以及提交运行结果
# CMD是容器启动时执行的命令，在构件时并不运行，构件时紧紧指定了这个命令到底是个什么样子

~~~

**3、构建镜像**

~~~shell
# 在当前这个目录下构建
[root@localhost tomcat]# pwd
/home/leipei/build/tomcat
[root@localhost tomcat]# ls -l
总用量 200668
-rw-r--r--. 1 root root  10929702 6月  12 10:13 apache-tomcat-9.0.22.tar.gz
-rw-r--r--. 1 root root       642 7月   2 17:56 Dockerfile
-rw-r--r--. 1 root root 194545143 6月  12 10:49 jdk-8u241-linux-x64.tar.gz
-rw-r--r--. 1 root root         0 6月  12 10:25 readme.txt
drwxr-xr-x. 3 root root        53 6月  12 14:30 test
drwxr-xr-x. 2 root root       197 6月  23 10:36 tomcatlogs

# 构建镜像命令，因为此处我的DockerFile文件命名是默认的Dockerfile【注意小写】，所以build时自动找到这个文件去构建。如果是自定义命名，则需要加-f参数，给出全路径如：-f /home/leipei/build/tomcat/xxxDockerfile
docker build -t uncleray/tomcat .

~~~

4、启动镜像

~~~shell
# -d以后台方式启动，-p端口映射为9090 --name给容器取一个名字 -v容器数据卷的挂载   \表示连接符
docker run -d -p 9090:8080 --name myt9 \
-v /home/leipei/build/tomcat/test:/usr/local/apache-tomcat-9.0.22/webapps/test \
-v /home/leipei/build/tomcat/tomcatlogs/:/usr/local/apache-tomcat-9.0.22/logs uncleray/tomcat9

# 因为我们是后台启动 可以通过docker exec 容器id ls -l 等命令查看
[root@localhost ~]# docker exec 5cc201685841 ls -l apache-tomcat-9.0.22/webapps
total 8
drwxr-x---.  3 root root 4096 Jul  4  2019 ROOT
drwxr-x---. 14 root root 4096 Jul  4  2019 docs
drwxr-x---.  6 root root   83 Jul  4  2019 examples
drwxr-x---.  5 root root   87 Jul  4  2019 host-manager
drwxr-x---.  5 root root  103 Jul  4  2019 manager
drwxr-xr-x.  3 root root   53 Jun 12 06:30 test

# 想要以伪终端交互方式进入容器的话 可以使用下面命令
docker exec -it 5cc201685841 /bin/bash
~~~



5、访问测试

6、发布项目（由于做了卷挂载，直接在本地编写项目就可以发布了）

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://java.sun.com/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://java.sun.com/xml/ns/javaee
                             http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd"
         version="2.5">

</web-app>
~~~

~~~jsp
<%@ page language="java" contentType="text/html; charset=utf-8"
    pageEncoding="utf-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>hello,leipei</title>
</head>
<body>
	Hello World!!!<br/>
    <%
    	System.out.println("---my test web logs----");
    %>
</body>
</html>
~~~

访问：http://192.168.146.132:9090/test/ 即可成功

以后开发的步骤：需要掌握Dockerfile的编写！我们之后的一切都是使用docker镜像来发布运行！



## 发布自己的镜像

**DockerHub**

1、地址：https://hub.docker.com/ 注册自己的帐号

2、确定这个帐号可以登录

3、在我们的服务器上提交自己的镜像

~~~shell
[root@localhost tomcat]# docker login --help

Usage:	docker login [OPTIONS] [SERVER]

Log in to a Docker registry.
If no server is specified, the default is defined by the daemon.

Options:
  -p, --password string   Password
      --password-stdin    Take the password from stdin
  -u, --username string   Username

~~~

4、登陆完毕后可以提交镜像了



**阿里云镜像服务**

1、登陆阿里云

2、找到容器镜像服务

3、创建命令空间

4、创建容器镜像

## 小结

**Docker整体流程**

![img](http://hbimg.b0.upaiyun.com/3d7083fa7d291a90b05822583933224958a2af4d9067-6N1RKd_fw658)



# Docker常用安装

## 安装MySQL

~~~shell
docker pull mysql:5.7

docker run -d -p 3310:3306 \
-v /home/mysql/conf:/etc/mysql/conf.d \
-v /home/mysql/logs:/logs \
-v /home/mysql/data:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=123456 \
--name mysql mysql:5.7

启动成功后，以交互模式进入mysql容器
docker exec -it mysql /bin/bash
输入密码进行连接
mysql -uroot -p # 连接mysql数据库
连接成功后
show databases; # 显示所有数据库
use mysql;		# 使用某个mysql数据库
show tables;	# 显示数据库表结构
就可以编写相关的SQL语句

# PS：当然也可以通过连接工具去连接数据库，如SQLyog、Navicat等

~~~



## 安装Redis

~~~shell
docker pull redis:3.2

docker run -d -p 6379:6379 \
-v /home/myredis/data:/data \
-v /home/myredis/conf/redis.conf:/usr/local/etc/redis/redis.conf \
-d redis:3.2 redis-server /usr/local/etc/redis/redis.conf \
--appendonly yes	# 开启AOF

在宿主机/home/myredis/conf/redis.conf目录下新建redis.conf配置文件 

# 使用redis客户端连接
docker exec -it 9d15410ea79f redis-cli
set leipei 24
exit或者shutdown 退出客户端连接
# 检测数据是否持久化
进入到/home/myredis目录 有一个data目录
cd data，有一个appendonly.aof文件 这就是保存的持久化数据
[root@localhost data]# ls -l
总用量 4
-rw-r--r--. 1 polkitd input 56 7月   3 15:40 appendonly.aof
[root@localhost data]# cat appendonly.aof 
*2
$6
SELECT
$1
0
*3
$3
set
$6
leipei
$2
24

~~~

# 本地镜像推送到阿里云

流程如图：

![image-20200703160252979](C:\Users\Uncle\AppData\Roaming\Typora\typora-user-images\image-20200703160252979.png)



~~~shell
docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]
  -a, --author string    Author (e.g., "John Hannibal Smith <hannibal@a-team.com>")
  -c, --change list      Apply Dockerfile instruction to the created image
  -m, --message string   Commit message
  -p, --pause            Pause container during commit (default true)

docker commit -a xxx -m "xxxx" 容器id 镜像名:tag

~~~



1、创建镜像仓库，选择本地仓库

![image-20200703161422647](C:\Users\Uncle\AppData\Roaming\Typora\typora-user-images\image-20200703161422647.png)

2、进行提交并推送 commit/push

~~~shell
docker login --username=unclerayslove registry.cn-chengdu.aliyuncs.com
用于登录的用户名为阿里云账号全名，密码为开通服务时设置的密码。
您可以在访问凭证页面修改凭证密码。

docker tag [ImageId] registry.cn-chengdu.aliyuncs.com/unclerayslove/mycentos:[镜像版本号]

docker push registry.cn-chengdu.aliyuncs.com/unclerayslove/mycentos:[镜像版本号]
~~~



私有仓库registry

~~~shell
docker pull registry

docker run -d -p 5000:5000 --restart always --name registry registry:2


docker pull ubuntu
docker tag ubuntu localhost:5000/ubuntu
docker push localhost:5000/ubuntu
~~~







# Docker网络（铺垫 容器编排 集群部署）

## 理解Docker0

**通过ip addr 查看网卡信息**

~~~shell
# 进入容器内部，查看容器的内部网络地址 ip addr
root@eb62116:/root/dockerfile>ip addr
# lo：本机回环地址 127.0.0.1
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
# ens192：服务器真实地址【内网地址】
2: ens192: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:50:56:a6:2c:cd brd ff:ff:ff:ff:ff:ff
    inet 10.1.62.116/24 brd 10.1.62.255 scope global noprefixroute ens192
       valid_lft forever preferred_lft forever
    inet6 2001:470:8287:602:6126:6ddc:ac6f:351c/64 scope global noprefixroute dynamic 
       valid_lft 2591910sec preferred_lft 604710sec
    inet6 fe80::c766:a165:1984:44ae/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
# docker0地址
3: docker0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:2f:57:c3:65 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
    inet6 fe80::42:2fff:fe57:c365/64 scope link 
       valid_lft forever preferred_lft forever
4: br-c8edf3491258: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:a3:7a:0f:48 brd ff:ff:ff:ff:ff:ff
    inet 172.18.0.1/16 brd 172.18.255.255 scope global br-c8edf3491258
       valid_lft forever preferred_lft forever
20: veth992b422@if19: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 56:a7:a0:8c:64:94 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet6 fe80::54a7:a0ff:fe8c:6494/64 scope link 
       valid_lft forever preferred_lft forever

# 
~~~

三个网络，代表三种不同的环境

思考：docker是如何处理容器网络访问的？

比如启动了两个容器，一个tomcat容器，一个是MySQL容器，那么tomcat是如何访问到mysql的呢？是怎么连接的呢？



**查看容器内的网络地址**

~~~shell
# 现在来启动一个tomcat容器看看
root@eb62116:/root/dockerfile>docker run -d -P --name tomcat01 tomcat
c7014a35b6c375b61aab20998ea6f4a1b4f1777f497b6e076b45a5a1d69e64ef

# 查看容器内的网络地址信息， ip addr， 发现容器启动的时候会得到一个eth0@if42 这样的ip地址，是docker分配的
root@eb62116:/root/dockerfile>docker exec -it tomcat01 ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
41: eth0@if42: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:ac:11:00:02 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 172.17.0.2/16 brd 172.17.255.255 scope global eth0
       valid_lft forever preferred_lft forever
root@eb62116:/root/dockerfile>

# 思考：linux 服务器 能不能 ping 通容器内部？
root@eb62116:/root/dockerfile>ping 172.17.0.2
PING 172.17.0.2 (172.17.0.2) 56(84) bytes of data.
64 bytes from 172.17.0.2: icmp_seq=1 ttl=64 time=0.063 ms
64 bytes from 172.17.0.2: icmp_seq=2 ttl=64 time=0.045 ms
64 bytes from 172.17.0.2: icmp_seq=3 ttl=64 time=0.053 ms
64 bytes from 172.17.0.2: icmp_seq=4 ttl=64 time=0.047 ms
# Linux 可以ping通 docker容器内部


~~~

> 原理

1、我们每启动一个docker容器，docker就会给docker容器分配一个ip，我们只要安装了docker，就会有一个网卡docker0【这是安装docker自带的】

桥接模式，使用的技术是 veth-pair技术

当我们启动一个容器后，再次测试 ip addr，发现了多了一个42：veth5649344@if41，跟容器内41: eth0@if42惊人的相似

![image-20210516174423865](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516174426.png)

2、再启动一个容器测试

发现，又多了一对网卡，而且还是成对的出现

![image-20210516175323853](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516175325.png)

进入到tomcat02容器，发现也有一对 43  44  网卡

![image-20210516175714279](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516175717.png)

我们发现这个容器中的网卡，都是一对对的，这就是veth-pair技术，一对虚拟的设备接口，一端连着协议，一端彼此相连

正因为有这个特性，veth-pair充当一个桥梁，连接各种虚拟网络设备

3、测试下tomcat01和tomcat02能否ping通

是能ping通的

~~~shell
root@eb62116:/root/dockerfile>docker exec -it tomcat02 ping 172.17.0.2
PING 172.17.0.2 (172.17.0.2) 56(84) bytes of data.
64 bytes from 172.17.0.2: icmp_seq=1 ttl=64 time=0.174 ms
64 bytes from 172.17.0.2: icmp_seq=2 ttl=64 time=0.059 ms
64 bytes from 172.17.0.2: icmp_seq=3 ttl=64 time=0.060 ms

# 结论：容器和容器之间是可以互相ping通的
~~~



网络模型图

tomcat01和tomcat02是共用的一个路由器，也就是我们的docker0

所有容器不指定网络的情况下，都是docker0路由的，docker会给我们的容器分配一个默认的可用IP

![image-20210516200525715](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516200526.png)

Docker使用的是Linux的桥接，宿主机中是一个Docker容器的网桥 docker0。

![image-20210516201135812](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516201137.png)

Docker中的所有的网络接口都是虚拟的，虚拟的转发效率高！（内网传递文件）

只要容器删除，对应网桥一对就没了！

![image-20210516204915356](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516204916.png)

## --link

> 思考一个场景：我们编写了一个微服务，会绑定一个database-url=ip，项目不重启，数据库ip换掉了，我们希望可以处理这个问题，可以用名字来进行访问容器？

~~~bash
root@eb62116:/root/dockerfile>docker exec -it tomcat01 ping tomcat02
ping: tomcat02: Name or service not known
root@eb62116:/root/dockerfile>

# 如何解决呢？
# 发现通过--link 就可以解决网络连通问题
root@eb62116:/root/dockerfile>docker run -d -P --name tomcat03 --link tomcat02 tomcat
714f49e51202fac269421521f5ce94fa02ff7174f23e57876d08f599a3069136
root@eb62116:/root/dockerfile>docker exec -it tomcat03 ping tomcat02
PING tomcat02 (172.17.0.3) 56(84) bytes of data.
64 bytes from tomcat02 (172.17.0.3): icmp_seq=1 ttl=64 time=0.109 ms
64 bytes from tomcat02 (172.17.0.3): icmp_seq=2 ttl=64 time=0.062 ms
64 bytes from tomcat02 (172.17.0.3): icmp_seq=3 ttl=64 time=0.062 ms
64 bytes from tomcat02 (172.17.0.3): icmp_seq=4 ttl=64 time=0.056 ms

# 反向可以ping通吗？ 不行
root@eb62116:/root/dockerfile>docker exec -it tomcat02 ping tomcat03
ping: tomcat03: Name or service not known
~~~

探究： 可以通过docker network inspect [network id]查看

![image-20210516205058695](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516205100.png)

我们进入tomcat03容器内查看hosts文件，其实这个tomcat03就是在本地配置了tomcat02的配置

~~~bash
root@eb62116:/var/lib/docker>docker exec -it tomcat03 cat /etc/hosts
127.0.0.1	localhost
::1	localhost ip6-localhost ip6-loopback
fe00::0	ip6-localnet
ff00::0	ip6-mcastprefix
ff02::1	ip6-allnodes
ff02::2	ip6-allrouters
172.17.0.3	tomcat02 9f4a4663ecaf		# 这里配置了tomcat02的配置
172.17.0.4	714f49e51202

~~~

`--link`就是我们在hosts配置中增加了一个 172.17.0.3 tomcat02 9f4a4663ecaf

现在Docker已经不建议使用 `--link`了

我们应该是自定义网络！不使用docker0

docker0问题：不支持容器名连接访问



## 自定义网络

容器互联

> 查看所有的docker网络

![image-20210516210601742](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516210602.png)

网络模式：

1、bridge：桥接  docker0（默认，自己创建也是用bridge 模式）

2、none：不配置网络

3、host：和宿主机共享网络

4、container：容器网络连通！（用的少，局限很大）

测试

~~~shell
# 直接启动命令， --net bridge，而这个就是我们的docker0【默认给我们加上这个参数，我们也可以修改名称】
docker run -d -P --name tomcat01 --net bridge tomcat

# docker特点： 默认，域名不能访问

# 自定义一个网络
# --driver bridge 桥接
# --subnet 192.168.0.0/16 子网	范围：192.168.0.2  ——  192.168.255.255
# --gateway 192.168.0.1 网关
root@eb62116:/root/dockerfile>docker network create --driver bridge --subnet 192.168.0.0/16 --gateway 192.168.0.1 mynet
8579691f0f6e0493bb1e7f02b508de442b4b65fce0bbce7b0eccd06ad73780f1

root@eb62116:/root/dockerfile>docker network ls
NETWORK ID     NAME                     DRIVER    SCOPE
bee534912d8f   bridge                   bridge    local
c8edf3491258   docker-compose_default   bridge    local
ad7c214eab5e   host                     host      local
8579691f0f6e   mynet                    bridge    local   # 自定义的网络
3caba1d5949b   none                     null      local
root@eb62116:/root/dockerfile>

~~~

我们自己的网络就创建好了

![image-20210516220243113](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516220244.png)



~~~shell
root@eb62116:/var/lib/docker>docker run -d -P --name tomcat-net-01 --network mynet tomcat
75e94ca5634f0fcc48a2abe7666b41dda1b560d5f357008bdbb95ac4e77d7933
root@eb62116:/var/lib/docker>docker run -d -P --name tomcat-net-02 --network mynet tomcat
d8c6f4b29411f667c5d6d9df28dc7d406f1fd3c1c7dede7197e6c853a1886ed9
root@eb62116:/var/lib/docker>docker network inspect mynet 
[
    {
        "Name": "mynet",
        "Id": "8579691f0f6e0493bb1e7f02b508de442b4b65fce0bbce7b0eccd06ad73780f1",
        "Created": "2021-05-16T21:22:16.756448565+08:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "192.168.0.0/16",
                    "Gateway": "192.168.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "75e94ca5634f0fcc48a2abe7666b41dda1b560d5f357008bdbb95ac4e77d7933": {
                "Name": "tomcat-net-01",
                "EndpointID": "cbd8a5fe8d3c76c43b2574517338370735c20d6f10abb7a2ed21259990418853",
                "MacAddress": "02:42:c0:a8:00:02",
                "IPv4Address": "192.168.0.2/16",
                "IPv6Address": ""
            },
            "d8c6f4b29411f667c5d6d9df28dc7d406f1fd3c1c7dede7197e6c853a1886ed9": {
                "Name": "tomcat-net-02",
                "EndpointID": "4935be31e72288ebaa2a2a84c833ebd06786a0fe7dde1bc9c92d54ec07c250a0",
                "MacAddress": "02:42:c0:a8:00:03",
                "IPv4Address": "192.168.0.3/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]

# 再次测试 ping 连接
# 发现 通过 ip 和 容器名 都能ping通
root@eb62116:/root/dockerfile>docker exec -it tomcat-net-01 ping 192.168.0.3
PING 192.168.0.3 (192.168.0.3) 56(84) bytes of data.
64 bytes from 192.168.0.3: icmp_seq=1 ttl=64 time=0.089 ms
64 bytes from 192.168.0.3: icmp_seq=2 ttl=64 time=0.050 ms
^C
--- 192.168.0.3 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.050/0.069/0.089/0.021 ms
#不使用 --link 也可以ping名字了
root@eb62116:/root/dockerfile>docker exec -it tomcat-net-01 ping tomcat-net-02 
PING tomcat-net-02 (192.168.0.3) 56(84) bytes of data.
64 bytes from tomcat-net-02.mynet (192.168.0.3): icmp_seq=1 ttl=64 time=0.043 ms
64 bytes from tomcat-net-02.mynet (192.168.0.3): icmp_seq=2 ttl=64 time=0.070 ms
64 bytes from tomcat-net-02.mynet (192.168.0.3): icmp_seq=3 ttl=64 time=0.053 ms

~~~

==我们自定义的网络docker都已经帮我们维护好了对应的关系，推荐我们平时这样使用网络==

好处： 如redis集群  MySQL集群

不同的集群使用不同的网络，保证集群都是安全和健康的



## 网络连通

将使用不同网络的容器，连接到另一个网络上，这样两个容器之间就打通了

如 A容器是docker0默认网络，B容器是自定义网络mynet，此时A容器是不能访问（ping不通）B容器的；但是当我们通过命令：docker network connect mynet A容器后，等于连接了A容器到mynet网络下，这时两个容器就能根据服务名ping通了【相互ping通】。

![image-20210516221548528](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516221550.png)

![image-20210516221702428](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516221704.png)

```shell
#测试打通 tomcat01  到 mynet网络
docker network connect mynet tomcat01
#连通之后，docker network inspect mynet 查看，发现就是将tomcat01 放到了mynet网络下

#官方说法：一个容器 两个ip地址！  如：阿里云服务 ， 公网ip 私网ip
```

![image-20210516222209111](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516222210.png)

~~~shell
# 成功 ping通
root@eb62116:/var/lib/docker>docker exec -it tomcat01 ping tomcat-net-01
PING tomcat-net-01 (192.168.0.2) 56(84) bytes of data.
64 bytes from tomcat-net-01.mynet (192.168.0.2): icmp_seq=1 ttl=64 time=0.060 ms
64 bytes from tomcat-net-01.mynet (192.168.0.2): icmp_seq=2 ttl=64 time=0.052 ms
64 bytes from tomcat-net-01.mynet (192.168.0.2): icmp_seq=3 ttl=64 time=0.049 ms
64 bytes from tomcat-net-01.mynet (192.168.0.2): icmp_seq=4 ttl=64 time=0.050 ms
~~~

结论：假设要跨网络操作别人，就需要使用docker network connect 连通



## 实战：部署Redis集群

![image-20210516222747699](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516222749.png)

~~~shell
#1、创建一个redis网卡
docker network create --subnet 172.38.0.0/16 redis
--subnet #表示网段的子网，  /16 表示有16位为网络号 16位为主机号
A类	0		0-127
B类	10		128-191
C类	110		192-223

# 2、shell脚本 创建六个redis配置,  直接复制到Linux窗口 执行即可
for port in $(seq 1 6);\
do \
mkdir -p /mydata/redis/node-${port}/conf
touch /mydata/redis/node-${port}/conf/redis.conf
cat << EOF >> /mydata/redis/node-${port}/conf/redis.conf
port 6379
# 绑定ip， 因为保护模式protected-mode yes 是默认开启得
bind 0.0.0.0
# 开启集群模式
cluster-enabled yes
# 集群节点信息配置文件
cluster-config-file nodes.conf
# 集群节点 连接超时时间
cluster-node-timeout 5000
# 集群节点 IP，填写宿主机的 IP
cluster-announce-ip 172.38.0.1${port}
# 集群节点映射端口
cluster-announce-port 6379
# 集群节点总线端口
cluster-announce-bus-port 16379
# 开启AOF持久化模式
appendonly yes
EOF
done


# 3、启动redis
docker run -d -p 6371:6379 -p 16371:16379 --name redis-1 -v /mydata/redis/node-1/data:/data -v /mydata/redis/node-1/conf/redis.conf:/etc/redis/redis.conf --net redis --ip 172.38.0.11 redis:5.0.9-alpine3.11 redis-server /etc/redis/redis.conf

docker run -d -p 6372:6379 -p 16372:16379 --name redis-2 -v /mydata/redis/node-2/data:/data -v /mydata/redis/node-2/conf/redis.conf:/etc/redis/redis.conf --net redis --ip 172.38.0.12 redis:5.0.9-alpine3.11 redis-server /etc/redis/redis.conf

docker run -d -p 6373:6379 -p 16373:16379 --name redis-3 -v /mydata/redis/node-3/data:/data -v /mydata/redis/node-3/conf/redis.conf:/etc/redis/redis.conf --net redis --ip 172.38.0.13 redis:5.0.9-alpine3.11 redis-server /etc/redis/redis.conf

docker run -d -p 6374:6379 -p 16374:16379 --name redis-4 -v /mydata/redis/node-4/data:/data -v /mydata/redis/node-4/conf/redis.conf:/etc/redis/redis.conf --net redis --ip 172.38.0.14 redis:5.0.9-alpine3.11 redis-server /etc/redis/redis.conf

docker run -d -p 6375:6379 -p 16375:16379 --name redis-5 -v /mydata/redis/node-5/data:/data -v /mydata/redis/node-5/conf/redis.conf:/etc/redis/redis.conf --net redis --ip 172.38.0.15 redis:5.0.9-alpine3.11 redis-server /etc/redis/redis.conf

docker run -d -p 6376:6379 -p 16376:16379 --name redis-6 -v /mydata/redis/node-6/data:/data -v /mydata/redis/node-6/conf/redis.conf:/etc/redis/redis.conf --net redis --ip 172.38.0.16 redis:5.0.9-alpine3.11 redis-server /etc/redis/redis.conf

## 或者通过脚本运行六个redis
for port in $(seq 1 6);\
do \
docker run -d -p 637${port}:6379 -p 1637${port}:16379 --name redis-${port} \
-v /mydata/redis/node-${port}/data:/data \
-v /mydata/redis/node-${port}/conf/redis.conf:/etc/redis/redis.conf \
--net redis --ip 172.38.0.1${port} redis:5.0.9-alpine3.11 redis-server /etc/redis/redis.conf
done

## 6个redis启动成功后，则开始搭建集群
# 4、进入到redis-1容器内
docker exec -it redis-1 /bin/sh #redis默认没有bash
## 通过redis-cli --cluster 命令创建集群
/data # redis-cli --cluster create 172.38.0.11:6379 172.38.0.12:6379 172.38.0.13:6379 172.38.0.14:6379 172.38.0.15:6379 172.38.0.16:6379  --cluster-replicas 1
	--cluster-replicas <arg>      #从节点个数

## Redis Cluster 在5.0之后取消了ruby脚本 redis-trib.rb的支持（手动命令行添加集群的方式不变），集合到redis-cli里，避免了再安装ruby的相关环境。直接使用redis-clit的参数--cluster 来取代。为方便自己后面查询就说明下如何使用该命令进行Cluster的创建和管理，关于Cluster的相关说明可以查看官网或则Redis Cluster部署、管理和测试。

>>> Performing hash slots allocation on 6 nodes...
Master[0] -> Slots 0 - 5460			#哈希槽 slot
Master[1] -> Slots 5461 - 10922		#哈希槽
Master[2] -> Slots 10923 - 16383	#哈希槽
Adding replica 172.38.0.15:6379 to 172.38.0.11:6379
Adding replica 172.38.0.16:6379 to 172.38.0.12:6379
Adding replica 172.38.0.14:6379 to 172.38.0.13:6379
M: ab7d216d42093667f55b858b9bf7045ec917e95c 172.38.0.11:6379
   slots:[0-5460] (5461 slots) master
M: 189c82efb4619a1b28e4cfd714fac5f565d940ee 172.38.0.12:6379
   slots:[5461-10922] (5462 slots) master
M: a4f3de9212d9c7a9beddf4072ecba371f99dfc45 172.38.0.13:6379
   slots:[10923-16383] (5461 slots) master
S: 570fcb41b358d8198d8a5768eee1c27f9b07b17c 172.38.0.14:6379
   replicates a4f3de9212d9c7a9beddf4072ecba371f99dfc45
S: 274900886cc5fa3dae46578e22d46c4b5e9de0e8 172.38.0.15:6379
   replicates ab7d216d42093667f55b858b9bf7045ec917e95c
S: 13d7f71edb92aa3d5aa3a2e3116c083791b885ad 172.38.0.16:6379
   replicates 189c82efb4619a1b28e4cfd714fac5f565d940ee
Can I set the above configuration? (type 'yes' to accept): yes
>>> Nodes configuration updated
>>> Assign a different config epoch to each node
>>> Sending CLUSTER MEET messages to join the cluster
Waiting for the cluster to join
...
>>> Performing Cluster Check (using node 172.38.0.11:6379)
M: ab7d216d42093667f55b858b9bf7045ec917e95c 172.38.0.11:6379
   slots:[0-5460] (5461 slots) master
   1 additional replica(s)
S: 274900886cc5fa3dae46578e22d46c4b5e9de0e8 172.38.0.15:6379
   slots: (0 slots) slave
   replicates ab7d216d42093667f55b858b9bf7045ec917e95c
M: 189c82efb4619a1b28e4cfd714fac5f565d940ee 172.38.0.12:6379
   slots:[5461-10922] (5462 slots) master
   1 additional replica(s)
M: a4f3de9212d9c7a9beddf4072ecba371f99dfc45 172.38.0.13:6379
   slots:[10923-16383] (5461 slots) master
   1 additional replica(s)
S: 13d7f71edb92aa3d5aa3a2e3116c083791b885ad 172.38.0.16:6379
   slots: (0 slots) slave
   replicates 189c82efb4619a1b28e4cfd714fac5f565d940ee
S: 570fcb41b358d8198d8a5768eee1c27f9b07b17c 172.38.0.14:6379
   slots: (0 slots) slave
   replicates a4f3de9212d9c7a9beddf4072ecba371f99dfc45
[OK] All nodes agree about slots configuration.
>>> Check for open slots...
>>> Check slots coverage...
[OK] All 16384 slots covered.

## 进入reids客户端   -c 集群模式进入
redis-cli -c
cluster-nodes	#查看集群节点信息

~~~

docker搭建redis集群完成！！

![image-20210516231622953](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210516231624.png)



集群节点信息解释：

![image-20210518112717128](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210518112719.png)

1、id：节点 ID，一个40个字符的随机字符串，当一个节点被创建时不会再发生变化（除非使用CLUSTER RESET HARD）。

2、ip:port：客户端与节点通信使用的地址

3、flags：逗号列表分隔的标志：myself，master，slave，fail?，fail，handshake，noaddr，noflags等

4、master：如果节点是slave，并且已知master节点，则这里列出master节点ID,否则的话这里列出”-“。

5、ping-sent：最近一次发送ping的时间，这个时间是一个unix毫秒时间戳，0代表没有发送过。

6、pong-recv：最近一次收到pong的时间，使用unix时间戳表示。

7、config-epoch：节点的epoch值（or of the current master if the node is a slave）。每当节点发生失败切换时，都会创建一个新的，独特的，递增的epoch。如果多个节点竞争同一个哈希槽时，epoch值更高的节点会抢夺到。

8、link-state：node-to-node集群总线使用的链接的状态，我们使用这个链接与集群中其他节点进行通信.值可以是 connected 和 disconnected。

9、slot：散列槽号或范围。哈希槽值或者一个哈希槽范围. 从第9个参数开始，后面最多可能有16384个 数(limit never reached)。代表当前节点可以提供服务的所有哈希槽值。如果只是一个值,那就是只有一个槽会被使用。如果是一个范围，这个值表示为起始槽-结束槽，节点将处理包括起始槽和结束槽在内的所有哈希槽。





# SpringBoot微服务打包Docker镜像

1、构建springboot项目

2、打包应用

3、编写Dockerfile

打包SpringBoot很方便，直接打成一个可执行jar，因此只需要一个jdk的环境即可。将打包的jar和config一级lib等拷贝到同一目录下，并在这个目录下编写Dockerfile文件

~~~dockerfile
## 1、基础的方式
FROM java:8
COPY *.jar /app.jar		#拷贝 并重新命名
COPY config/ /config/
COPY lib/ /lib/
EXPOSE 8024
CMD ["--server.port=8024"]	#启动容器时会追加在ENTRYPOINT后面
ENTRYPOINT ["java","-jar","app.jar"]


# 将所有文件放在同一目录下，比如/home目录，为了在启动容器时能java -jar能找这些文件，所以需要配置工作目录WORKDIR，在容器启动时，就会进入到这个目录
## 2、将文件拷贝到容器内指定目录，并配置工作目录即可
FROM java:8
COPY *.jar /home/app.jar
COPY config/ /home/config/
COPY lib/ /home/lib/
EXPOSE 8024
WORKDIR /home
CMD ["--server.port=8024"]
ENTRYPOINT ["java","-jar","app.jar"]


## 3、添加VOLUME，这种方式是匿名挂载【通过docker inspect 容器id可查看】其效果是在主机 /var/lib/docker/volumes 目录下创建了一个临时文件，并链接到容器的/home/otis/config
FROM java:8
COPY *.jar /home/otis/app.jar
COPY config/ /home/otis/config/
COPY lib/ /home/otis/lib/
EXPOSE 8024
WORKDIR /home/otis
# 通过 VOLUME 指令创建的挂载点，无法指定主机上对应的目录，是自动生成的。因此这个挂载路径是容器内的路径
VOLUME ["/home/otis/config","/home/otis/lib","/home/otis/logs"]

CMD ["--server.port=8024"]
ENTRYPOINT ["java","-jar","app.jar"]



## 4、如果要明确挂载路径，则通过在启动容器时 -v 进行路径挂载
docker run -d -p 8024:8024 -v /home/omc/omc-backend/docker-otis/logs:/home/otis/logs

~~~

对于 CMD 和 ENTRYPOINT 的设计而言，多数情况下它们应该是单独使用的。当然，有一个例外是 CMD 为 ENTRYPOINT 提供默认的可选参数。

- 如果 ENTRYPOINT 使用了 shell 模式，CMD 指令会被忽略。
- 如果 ENTRYPOINT 使用了 exec 模式，CMD 指定的内容被追加为 ENTRYPOINT 指定命令的参数。
- 如果 ENTRYPOINT 使用了 exec 模式，CMD 也应该使用 exec 模式。

![CMD&ENTRYPOINT](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210517113304.png)

ENTRYPOINT和CMD同时存在时, docker把CMD的命令拼接到ENTRYPOINT命令之后



4、构建镜像

~~~shell
# 1.复制jar和Dockerfile到服务器
# 2.构建镜像
docker build -t xxxxx:xx  .
~~~



5、发布运行



IDEA直连Docker

1、IDEA下载Docker插件【一般这个插件会默认下载】

2、修改服务器的docker配置

~~~shell
## 1、修改docker服务文件
vi  /lib/systemd/system/docker.service

# 2、在 ExecStart 开头的这一行末尾添加 -H tcp://0.0.0.0:2375
ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock -H tcp://0.0.0.0:2375

## 这种方式也可以。 将原来的ExecStart前面加上#号注释掉，然后再下面追加一行
ExecStart=/usr/bin/dockerd    -H tcp://0.0.0.0:2375    -H unix:///var/run/docker.sock
 
## 3、重新加载配置
systemctl daemon-reload 
## 重启docker服务
systemctl restart docker.service
## 可以合并成一个执行
systemctl daemon-reload && systemctl restart docker

## 4、如果没有关闭防火墙，则需要开放端口
firewall-cmd --zone=public --add-port=2375/tcp --permanent

~~~

3、在IDEA中连接Docker。在Services中配置，点击+ 连接Dockers Connection，Name：取一个名字，TCP socket：输入安装docker的服务器ip，完成点击ok即有左侧Docker的服务了。

![img](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210517180334.png)



Docker 配置的三种方式

![image-20210517181455798](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210517181457.png)

Docker-Image配置

![image-20210518163130544](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210518163132.png)

Dockerfile的方式

![image-20210518163637974](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210518163639.png)





1、不配置Maven，需要自己先正常Maven打包，然后通过编写Dockerfile文件，进行创建镜像 和启动容器

2、配置Maven【添加 docker-maven-plugin 插件依赖，进行相关配置】

~~~xml

<plugin>
    <groupId>com.spotify</groupId>
    <artifactId>docker-maven-plugin</artifactId>
    <version>1.0.0</version>

    <!--将插件绑定在某个phase执行-->
    <executions>
        <execution>
            <id>build-image</id>
            <!--将插件绑定在package这个phase上。也就是说，用户只需执行mvn package ，就会自动执行mvn docker:build-->
            <phase>package</phase>
            <goals>
                <goal>build</goal>
            </goals>
        </execution>
    </executions>

    <configuration>
        <!--指定生成的镜像名-->
        <imageName>zdadmin/${project.artifactId}</imageName>
        <!--指定标签-->
        <imageTags>
            <imageTag>latest</imageTag>
        </imageTags>

        <!-- 指定 Dockerfile 路径  ${project.basedir}：项目根路径下-->
        <dockerDirectory>${project.basedir}</dockerDirectory>

        <!--指定远程 docker api地址-->
        <dockerHost>https://xxx.xxx.xxx.xxx:2376</dockerHost>

        <!-- 这里是复制 war 包到 docker 容器指定目录配置 -->
        <resources>
            <resource>
                <targetPath>/</targetPath>
                <!--war 包所在的路径  此处配置的 即对应 target 目录-->
                <directory>${project.build.directory}</directory>
                <!-- 需要包含的 jar包 ，这里对应的是 Dockerfile中添加的文件名　-->
                <include>${project.build.finalName}.war</include>
            </resource>
        </resources>

        <!-- 以下两行是为了docker push到DockerHub使用的。 -->
        <serverId>docker-hub</serverId>
        <registryUrl>https://index.docker.io/v1</registryUrl>
    </configuration>
</plugin>
~~~





# 参考博文

https://blog.csdn.net/weixin_43591980/article/details/106272050

https://blog.csdn.net/weixin_43591980/article/details/106316094























