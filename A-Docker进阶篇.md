官网：https://docs.docker.com/compose/install/

# Docker Compose

## 简介

Dockerfile——》build——》run  手动操作，单个容器！！如果是启动多个容器，很麻烦，效率低！！！

比如微服务——100个，一个个手动去启动，要命！！！



Docker Compose 可以轻松高效管理容器，定义运行多个容器

> 官方介绍

定义、运行多个容器

使用YAML file 配置文件

single command。命令有哪些？

Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration. To learn more about all the features of Compose, see [the list of features](https://docs.docker.com/compose/#features).



所有的环境都可以使用Compose

Compose works in all environments: production, staging, development, testing, as well as CI workflows. You can learn more about each case in [Common Use Cases](https://docs.docker.com/compose/#common-use-cases).

使用Compose的三步骤：

Using Compose is basically a three-step process:

1. Define your app’s environment with a `Dockerfile` so it can be reproduced anywhere.
   - Dockerfile保证我们的项目在任何地方可以运行
2. Define the services that make up your app in `docker-compose.yml` so they can be run together in an isolated environment.
   - services  什么是服务
   - docker-compose.yml！这个文件怎么写？
3. Run `docker compose up` and the [Docker compose command](https://docs.docker.com/compose/cli-command/) starts and runs your entire app. You can alternatively run `docker-compose up` using the docker-compose binary.
   - docker-compose up 命令启动项目

作用：批量容器编排



> 自己理解

Compose是Docker官方的开源项目。需要安装！！

Dockerfile让程序在任何地方运行。 比如 web服务、redis、mysql、nginx。。多个容器

Compose

```yaml
version: "3.9"  # optional since v1.27.0
services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - .:/code
      - logvolume01:/var/log
    links:
      - redis
  redis:
    image: redis
volumes:
  logvolume01: {}
```

docker-compse up 100个服务

Compose：重要的概念

- 服务services，就是容器，或者说应用。（如 web、redis、mysql。。。）
- 项目project。一组关联的容器。（所有的容器启动起来，是一个完整的项目）



## 安装

官方文档

![image-20210518204355637](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210518204356.png)



~~~shell
# 这个地址可能有点慢
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

## 使用 国内的镜像，更快
curl -L https://get.daocloud.io/docker/compose/releases/download/1.29.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose

## 授权
chmod +x /usr/local/bin/docker-compose
~~~



默认的服务名  文件名_ 服务名_num

## yaml规则

docker-compose.yml  核心

https://docs.docker.com/compose/compose-file/

~~~yaml
# 3层
version: ''	#版本
services: 	#服务
  服务1: web
    # 服务配置
    images
    build
    network
    ......
  服务2: redis
    ......
  服务3: redis
  
# 其他配置  网络/卷、全局规则
volumes:
networks:
config
~~~



![image-20210518221029990](https://raw.githubusercontent.com/Unclerayslove/picture/main/img/20210518221031.png)



workpress



https://docs.docker.com/engine/swarm/



















































