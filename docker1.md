**[ 自建的网站](https://www.kuangstudy.com/)**

**[b站原视频](https://www.bilibili.com/video/BV1og4y1q7M4?vd_source=345a382f2c86d3441cc342a80fc25545 )**

**码云 [gitee](https://gitee.com/kuangstudy)**

**公众号**

目录生成语法：vscode插件markdown in all

----
- [前言](#前言)
- [一、Docker概述](#一docker概述)
  - [1. Docker为什么出现](#1-docker为什么出现)
  - [2. Docker的历史](#2-docker的历史)
  - [3. Docker能做什么](#3-docker能做什么)
- [二、Docker安装](#二docker安装)
  - [1. Docker的基本组成](#1-docker的基本组成)
  - [2. 安装Docker](#2-安装docker)
  - [3. 阿里云镜像加速](#3-阿里云镜像加速)
  - [4. 回顾hello-world流程](#4-回顾hello-world流程)
  - [5. 底层原理](#5-底层原理)
- [三、Docker的常用命令](#三docker的常用命令)
  - [1. 帮助命令](#1-帮助命令)
  - [2. 镜像命令](#2-镜像命令)
    - [dokcer images](#dokcer-images)
    - [docker search](#docker-search)
    - [docker pull](#docker-pull)
    - [docker rmi](#docker-rmi)
  - [3. 容器命令](#3-容器命令)
    - [新建容器并启动](#新建容器并启动)
    - [列出所有运行的容器](#列出所有运行的容器)
    - [退出容器](#退出容器)
    - [删除容器](#删除容器)
    - [启动和停止容器的操作](#启动和停止容器的操作)
  - [4. 常用其他命令](#4-常用其他命令)
    - [后台启动容器](#后台启动容器)
    - [查看日志](#查看日志)
    - [查看容器中进程的信息](#查看容器中进程的信息)
    - [查看镜像的元数据](#查看镜像的元数据)
    - [进入当前正在运行的容器](#进入当前正在运行的容器)
    - [从容器内拷贝文件到主机上](#从容器内拷贝文件到主机上)
  - [5. 小结](#5-小结)
  - [6. 作业练习](#6-作业练习)
    - [docker安装nginx](#docker安装nginx)
    - [docker安装tomcat](#docker安装tomcat)
    - [部署ES+kibana](#部署eskibana)
  - [7. 可视化](#7-可视化)
    - [什么是portainer ?](#什么是portainer-)
- [四、Docker镜像讲解](#四docker镜像讲解)
  - [1. 镜像是什么](#1-镜像是什么)
  - [2. Docker镜像加速原理](#2-docker镜像加速原理)
    - [UnionFS（联合文件系统）](#unionfs联合文件系统)
    - [Docker镜像加载原型](#docker镜像加载原型)
  - [3. 分层理解](#3-分层理解)
    - [分层的镜像](#分层的镜像)
    - [特点](#特点)
  - [4. commit镜像](#4-commit镜像)
    - [实战测试](#实战测试)
- [五、容器数据卷](#五容器数据卷)
  - [1. 什么是容器数据卷](#1-什么是容器数据卷)
  - [2. 使用数据卷](#2-使用数据卷)
    - [直接使用命令来挂载：-v](#直接使用命令来挂载-v)
  - [3. 实战：安装mysql](#3-实战安装mysql)
  - [4. 匿名和具名挂载](#4-匿名和具名挂载)
  - [5. 初识Dockerfile](#5-初识dockerfile)
  - [6. 数据卷容器](#6-数据卷容器)
- [六、DockerFile](#六dockerfile)
  - [1. DockerFile介绍](#1-dockerfile介绍)
  - [2. DockerFile的构建过程](#2-dockerfile的构建过程)
    - [基础知识](#基础知识)
  - [3. DockerFile的命令](#3-dockerfile的命令)
  - [4. 实战测试](#4-实战测试)
  - [5. 制作tomcat镜像](#5-制作tomcat镜像)
  - [6. 发布自己的镜像](#6-发布自己的镜像)
    - [1. 发布到dockerhub上](#1-发布到dockerhub上)
    - [2. 发布到阿里云镜像服务上](#2-发布到阿里云镜像服务上)
  - [7. 小结](#7-小结)
- [七、Docker网络](#七docker网络)
  - [1. 理解docker0](#1-理解docker0)
    - [测试](#测试)
    - [原理](#原理)
  - [2. --link](#2---link)
    - [思考一个场景（高可用）](#思考一个场景高可用)
  - [3. 自定义网络](#3-自定义网络)
    - [查看所有的docker网络](#查看所有的docker网络)
    - [网络模式](#网络模式)
    - [测试](#测试-1)
  - [4. 网络连通](#4-网络连通)
  - [5. 实战：部署redis集群](#5-实战部署redis集群)
- [八、SpringBoot微服务打包docker镜像](#八springboot微服务打包docker镜像)

# 前言

给大家分享《三体》中的一句话，很有感触：弱小和无知不是生存的障碍，傲慢才是。

- Docker概述
- Docker安装
- Docker命令
	- 镜像命令
	- 容器命令
	- 操作命令
	- …
- Docker镜像！
- 容器数据卷！
- DockerFile·Docker网络原理
- IDEA整合Docker
- Docker Compose
- Docker Swarm
- CI\CDJenkins

# 一、Docker概述
## 1. Docker为什么出现
一款产品：开发--上线  两套环境（应用环境，应用配置）
开发---运维。问题：我在我的电脑上可以运行！版本更新，导致服务不可用！对于运维来说，考验就十分大？
环境配置是十分的麻烦，每一个机器都要部署环境（集群Redis、ES、Hadoop...）费时费力。
发布一个项目（jar +（Redis MySQL jdk ES）），项目能不能都带上环境安装打包！
之前在服务器配置一个应用的环境Redis MySQL jdk ES Hadoop，配置超麻烦了，不能够跨平台。
Windows开发，最后发布到Linux:
- 传统：开发jar，运维来做！
- 现在：开发打包部署上线，一套流程做完！

java --- apk -- 发布（应用商店）---张三使用apk---安装即可用！
java --- jar（环境）--- 打包项目带上环境（镜像）---（Docker仓库：商店）---下载我们发布的镜像--直接运行即可！

**Docker给以上的问题，提出了解决方案！**

Docker的思想就来自于集装箱！
隔离：Docker核心思想！打包装箱！每个箱子是互相隔离的。


`本质：所有的技术都是因为出现了一些问题，我们需要去解决，才去学习。`

## 2. Docker的历史
2010年，几个搞IT的年轻人，就在美国成立了一家公司**dotcloud**做一些pass的云计算服务！
LXC有关的容器技术！他们将自己的技术（容器化技术）命名就是Docker！
Docker刚刚诞生的时候，没有引起行业的注意！（dotCloud就活不下去）
**开源**（开放源代码）
2013年，Docker开源！
Docker越来越多的人发现了docker的优点！就火了，Docker每个月都会更新一个版本！
2014年4月9日，Docker1.0发布！
Docker为什么这么火？**十分的轻巧**
在容器技术出来之前，我们都是使用虚拟机技术！
虚拟机：在window中装一个Vmware，通过这个软件我们可以虚拟出来一台或者多台电脑！（很笨重）
虚拟机也是属于虚拟化技术，Docker容器技术，也是一种虚拟化技术！
```java
vm：隔离，需要开启多个虚拟机！linux centos原生镜像（一个电脑！）需要几个G内存空间，开启需要几分钟！
docker：隔离，镜像（最核心的环境4m内存）十分的小巧，运行镜像就可以了！小巧！几个M或KB的内存空间，秒级启动！
```
&gt; 聊聊Doker

Docker是基于Go语言开发的！开源项目！
官网：https://www.docker.com/
文档地址：https://docs.docker.com/
Doker镜像仓库地址：https://hub.docker.com/

## 3. Docker能做什么
&gt; 之前的虚拟机技术

![](https://img-blog.csdnimg.cn/img_convert/e440c7d10ff2727fd6d5465fb6ef4988.jpeg)
虚拟机技术缺点：
1、资源占用十分多
2、冗余步骤多
3、启动很慢！

&gt; 容器化技术

**容器化技术不是模拟的一个完整的操作系统**
![](https://img-blog.csdnimg.cn/img_convert/47a51e0d5fddebea74e86fbc49c90812.jpeg)

比较Docker和虚拟机技术的不同：
- 传统虚拟机，虚拟出一条硬件，运行一个完整的操作系统，然后在这个系统上安装和运行软件。
- 容器内的应用直接运行在宿主机的内核中，容器是没有自己的内核的，也没有虚拟我们的硬件，所以就轻便了。
- 每个容器间是互相隔离，每个容器内都有一个属于自己的文件系统，互不影响。

&gt; Devops（开发、运维）

**应用更快速的交付和部署**

传统：一堆帮助文档，安装程序!
Docker：打包镜像发布测试，一键运行!

**更便捷的升级和扩缩容**

使用了Docker之后，我们部署应用就和搭积木一样！
项目打包为一个镜像，扩展服务器A！服务器B!

**更简单的系统运维**

在容器化之后，我们的开发，测试环境都是高度一致的。

**更高效的计算资源利用**

Docker是内核级别的虚拟化，可以在一个物理机上可以运行很多的容器实例！服务器的性能可以被压榨到极致。
只要学不死，就往死里学！

# 二、Docker安装
## 1. Docker的基本组成
![](https://img-blog.csdnimg.cn/img_convert/03e39bfb64ffd63d93e4baee45358500.jpeg)
**镜像（image）：**
docker镜像就好比是一个模板，可以通过这个模板来创建容器服务，tomcat镜像===&gt;run==&gt;tomcat01容器（提供服务器），通过这个镜像可以创建多个容器（最终服务运行或者项目运行就是在容器中的）。

**容器（container）：**
Docker利用容器技术，独立运行一个或者一个组应用，通过镜像来创建的。
启动，停止，删除，基本命令！
目前就可以把这个容器理解为就是一个简易的linux系统

**仓库（repository）：**
仓库就是存放镜像的地方！
仓库分为公有仓库和私有仓库！
Docker Hub（默认是国外的）阿里云.…都有容器服务器（配置镜像加速！）

## 2. 安装Docker
&gt; 环境准备

1. 需要会一点点的Linux的基础
2. CentOS7
3. 我们使用Xshell连接远程服务器进行操作

&gt; 环境查看

````shell
# 系统内核是 3.10 以上的
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# uname -r
3.10.0-1160.66.1.el7.x86_64
````
```shell
# 查看系统版本
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# cat /etc/os-release
NAME=&quot;CentOS Linux&quot;
VERSION=&quot;7 (Core)&quot;
ID=&quot;centos&quot;
ID_LIKE=&quot;rhel fedora&quot;
VERSION_ID=&quot;7&quot;
PRETTY_NAME=&quot;CentOS Linux 7 (Core)&quot;
ANSI_COLOR=&quot;0;31&quot;
CPE_NAME=&quot;cpe:/o:centos:centos:7&quot;
HOME_URL=&quot;https://www.centos.org/&quot;
BUG_REPORT_URL=&quot;https://bugs.centos.org/&quot;

CENTOS_MANTISBT_PROJECT=&quot;CentOS-7&quot;
CENTOS_MANTISBT_PROJECT_VERSION=&quot;7&quot;
REDHAT_SUPPORT_PRODUCT=&quot;centos&quot;
REDHAT_SUPPORT_PRODUCT_VERSION=&quot;7&quot;
```

&gt; 安装

查看文档：https://docs.docker.com/ （https://docs.docker.com/engine/install/centos/）

```shell
# 1.卸载旧的版本
yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
# 2.需要的安装包
yum install -y yum-utils
# 3.设置镜像的仓库
yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo # 默认是从国外的。

yum-config-manager \
    --add-repo \
    http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo # 推荐使用阿里云的。


# 安装容器之前，更新yum软件包索引。
yum makecache fast
# 4.安装容器相关的。docker-ce（社区版）docker-ee（企业版）
yum install docker-ce docker-ce-cli containerd.io
# 5.启动docker
systemctl start docker
# 6.使用docker version查看是否安装成功
```
![](https://img-blog.csdnimg.cn/img_convert/2a1f4bd8256c5eeb757fbb7df38fd525.jpeg)
```shell
# 7.测试hello-world
docker run hello-world
```
![](https://img-blog.csdnimg.cn/img_convert/109805f24d08cd2e1056bfaec01c3057.jpeg)
```shell
# 8.查看一下下载的这个hello-world镜像
```

&gt; 了解：卸载docker

```shell
# 1.卸载依赖
yum remove docker-ce docker-ce-cli containerd.io
# 2.删除资源
rm -rf /var/lib/docker
rm -rf /var/lib/containerd

# /var/lib/docker  docker的默认工作路径
```
## 3. 阿里云镜像加速
1. 登录阿里云，找到容器服务。
2. 找到镜像加速地址。
3. 配置使用。
四个命令，依次执行即可：
```shell
sudo mkdir -p /etc/docker
```
```shell
sudo tee /etc/docker/daemon.json &lt;&lt;-&#39;EOF&#39;
{
  &quot;registry-mirrors&quot;: [&quot;https://xxx.xxx.xxx.com&quot;]
}
EOF
```
```shell
sudo systemctl daemon-reload
```
```shell
sudo systemctl restart docker
```

## 4. 回顾hello-world流程
![在这里插入图片描述](https://img-blog.csdnimg.cn/c8b2bd1485db459a97484e3ca6b4c3c1.jpeg)
## 5. 底层原理
Docker是怎么工作的？
Docker 是一个Client-Server结构的系统，Docker的守护进程运行在主机上。通过Socket从客户端访问！
DockerServer 接收到Docker-Client的指令，就会执行这个命令！
![在这里插入图片描述](https://img-blog.csdnimg.cn/61c3a5a753d54241b4632f8aeae737ea.png)
**Docker为什么比VM快？**
1、Docker有着比虚拟机更少的抽象层。
2、docker利用的是宿主机的内核，vm需要是Guest OS。
![在这里插入图片描述](https://img-blog.csdnimg.cn/63afc76d81d74f429f983f306e4621d0.png)
所以说，新建一个容器的时候，docker不需要像虚拟机一样重新加载一个操作系统内核，避免引导。
虚拟机是加载GuestOS，分钟级别的，而docker是利用宿主机的操作系统，省略了这个复杂的过程，秒级！
# 三、Docker的常用命令
## 1. 帮助命令
```powershell
docker version		# 显示docker的版本信息
docker info		  	# 显示docker的系统信息，包括镜像和容器的数量
docker 命令 --help 		# 帮助命令
```
帮助文档的地址：https://docs.docker.com/reference/

## 2. 镜像命令
### dokcer images
查看所有本地的主机上的镜像

```powershell
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker images
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
hello-world   latest    feb5d9fea6a5   10 months ago   13.3kB
# 解释
REPOSITORY	镜像的仓库源
TAG			镜像的标签
IMAGE ID	镜像的id
CREATED		镜像的创建时间
SIZE		镜像的大小
# 命令参数可选项
 -a, --all         # 显示所有镜像 (docker images -a)
 -q, --quiet       # 仅显示镜像id (docker images -q)
```
### docker search
搜索镜像

```powershell
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker search mysql
NAME                           DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
mysql                          MySQL is a widely used, open-source relation…   12940     [OK]
mariadb                        MariaDB Server is a high performing open sou…   4957      [OK]
phpmyadmin                     phpMyAdmin - A web interface for MySQL and M…   587       [OK]
percona                        Percona Server is a fork of the MySQL relati…   582       [OK]
# 解释
# 命令参数可选项 (通过搜索来过滤)
--filter=STARS=3000 	# 搜索出来的镜像就是stars大于3000的

[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker search mysql --filter=STARS=3000
NAME      DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
mysql     MySQL is a widely used, open-source relation…   12941     [OK]
mariadb   MariaDB Server is a high performing open sou…   4957      [OK]

```
### docker pull
下载镜像

```powershell
# 下载镜像：docker pull 镜像名[:tag]
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker pull mysql
Using default tag: latest			# 如果不写tag，默认就是latest，最新的版本
latest: Pulling from library/mysql
72a69066d2fe: Pull complete			# 分层下载，docker image的核心，联合文件下载
93619dbc5b36: Pull complete
99da31dd6142: Pull complete
626033c43d70: Pull complete
37d5d7efb64e: Pull complete
ac563158d721: Pull complete
d2ba16033dad: Pull complete
688ba7d5c01a: Pull complete
00e060b6d11d: Pull complete
1c04857f594f: Pull complete
4d7cfa90e6ea: Pull complete
e0431212d27d: Pull complete
Digest: sha256:e9027fe4d91c0153429607251656806cc784e914937271037f7738bd5b8e7709 #签名
Status: Downloaded newer image for mysql:latest
docker.io/library/mysql:latest		# 真实地址

# 两个命令是等价的
docker pull mysql
docker pull docker.io/library/mysql:latest
# 指定版本下载

[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker pull mysql:5.7
5.7: Pulling from library/mysql
72a69066d2fe: Already exists		# 联合文件下载，已经存在的资源可以共用
93619dbc5b36: Already exists
99da31dd6142: Already exists
626033c43d70: Already exists
37d5d7efb64e: Already exists
ac563158d721: Already exists
d2ba16033dad: Already exists
0ceb82207cd7: Pull complete
37f2405cae96: Pull complete
e2482e017e53: Pull complete
70deed891d42: Pull complete
Digest: sha256:f2ad209efe9c67104167fc609cca6973c8422939491c9345270175a300419f94
Status: Downloaded newer image for mysql:5.7
docker.io/library/mysql:5.7
```
### docker rmi
删除镜像

```powershell
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker rmi -f 镜像id					# 删除指定的镜像
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker rmi -f 镜像id 镜像id 镜像id	# 删除多个镜像（空格分隔）
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker rmi -f $(docker images -aq)	# 删除全部的镜像
```

## 3. 容器命令
说明：我们有了镜像才可以创建容器，linux，下载一个centos 镜像来测试学习。

```powershell
docker pull centos
```

### 新建容器并启动

```powershell
docker run [可选参数] image
# 参数说明
--name=&quot;name&quot;		容器名字：用来区分容器
-d					后台方式运行：相当于nohup
-it					使用交互式运行：进入容器查看内容
-p					指定容器的端口（四种方式）小写字母p
	-p ip:主机端口：容器端口
	-p 主机端口：容器端口
	-p 容器端口
	容器端口
-P 					随机指定端口（大写字母P）
# 测试：启动并进入容器
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker run -it centos /bin/bash
[root@526c31d2c298 /]# ls		# 查看容器内的centos（基础版本，很多命令都是不完善的）
bin  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var

# 从容器中退回到主机
[root@526c31d2c298 /]# exit
exit
[root@iZbp13qr3mm4ucsjumrlgqZ /]# ls
bin  boot  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var  www
```
### 列出所有运行的容器

```powershell
docker ps	# 列出当前正在运行的容器
# 命令参数可选项
-a		# 列出当前正在运行的容器+历史运行过的容器
-n=?	# 显示最近创建的容器（可以指定显示几条，比如-n=1）
-q		# 只显示容器的编号

[root@iZbp13qr3mm4ucsjumrlgqZ /]# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
[root@iZbp13qr3mm4ucsjumrlgqZ /]# docker ps -a
CONTAINER ID   IMAGE          COMMAND       CREATED         STATUS                     PORTS     NAMES
526c31d2c298   centos         &quot;/bin/bash&quot;   4 minutes ago   Exited (0) 2 minutes ago             optimistic_allen
ce0eb11fbf8a   feb5d9fea6a5   &quot;/hello&quot;      4 hours ago     Exited (0) 4 hours ago               keen_ellis
[root@iZbp13qr3mm4ucsjumrlgqZ /]# docker ps -a -n=1
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS                     PORTS     NAMES
526c31d2c298   centos    &quot;/bin/bash&quot;   5 minutes ago   Exited (0) 3 minutes ago             optimistic_allen
```
### 退出容器
```powershell
exit		# 容器直接停止，并退出
ctrl+P+Q	# 容器不停止，退出

[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker run -it centos /bin/bash
[root@c5d61aa9d7df /]# [root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
c5d61aa9d7df   centos    &quot;/bin/bash&quot;   56 seconds ago   Up 55 seconds             kind_clarke
[root@iZbp13qr3mm4ucsjumrlgqZ ~]#
```

### 删除容器
```powershell
docker rm 容器id					# 删除容器（不能删除正在运行的容器）如果要强制删除：docker rm -f 容器id
docker rm -f $(docker ps -aq)		# 删除全部容器
docker ps -a -q|xargs docker rm		# 删除所有容器
```
### 启动和停止容器的操作

```powershell
docker start 容器id		# 启动容器
docker restart 容器id	# 重启容器
docker stop 容器id		# 停止当前正在运行的容器
docker kill 容器id		# 强制停止当前容器
```
## 4. 常用其他命令
### 后台启动容器
```powershell
# 命令docker run -d 镜像名
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker run -d centos
# 问题：docker ps发现centos停止了

# 常见的坑：docker容器使用后台运行，就必须要有要一个前台进程，docker发现没有应用，就会自动停止。
# 比如：nginx，容器启动后，发现自己没有提供服务，就会立刻停止，就是没有程序了
```
### 查看日志

```powershell
docker logs -tf --tail 容器id
# 自己编写一段shell脚本
docker run -d centos /bin/sh -c &quot;while true;do echo kuangshen;sleep 1;done&quot;


[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker logs -tf  容器id
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker logs -tf --tail 10  容器id

# 显示日志
-tf						# 显示日志
--tail number	# 要显示的日志条数
```
### 查看容器中进程的信息
```powershell
# 命令 docker top 容器id 
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker top 88d23bcbe1f2
UID                 PID                 PPID                C                   STIME               TTY                 TIME                CMD
root                21212               21193               0                   16:23               ?                   00:00:00            
root                21600               21212               0                   16:29               ?                   00:00:00            
```
### 查看镜像的元数据

```powershell
# 命令docker inspect 容器id
[
    {
        &quot;Id&quot;: &quot;88d23bcbe1f28e1f8ae5d2b63fa8d57d2abcbdacf193db05852f4f74a95b9ffe&quot;,
        &quot;Created&quot;: &quot;2022-07-29T08:23:56.862239223Z&quot;,
        &quot;Path&quot;: &quot;/bin/sh&quot;,
        &quot;Args&quot;: [
            &quot;-c&quot;,
            &quot;while true;do echo kuangshen;sleep 1;done&quot;
        ],
        &quot;State&quot;: {
            &quot;Status&quot;: &quot;running&quot;,
            &quot;Running&quot;: true,
            &quot;Paused&quot;: false,
            &quot;Restarting&quot;: false,
            &quot;OOMKilled&quot;: false,
            &quot;Dead&quot;: false,
            &quot;Pid&quot;: 21212,
            &quot;ExitCode&quot;: 0,
            &quot;Error&quot;: &quot;&quot;,
            &quot;StartedAt&quot;: &quot;2022-07-29T08:23:57.109766809Z&quot;,
            &quot;FinishedAt&quot;: &quot;0001-01-01T00:00:00Z&quot;
        },
        &quot;Image&quot;: &quot;sha256:5d0da3dc976460b72c77d94c8a1ad043720b0416bfc16c52c45d4847e53fadb6&quot;,
        &quot;ResolvConfPath&quot;: &quot;/var/lib/docker/containers/88d23bcbe1f28e1f8ae5d2b63fa8d57d2abcbdacf193db05852f4f74a95b9ffe/resolv.conf&quot;,
        &quot;HostnamePath&quot;: &quot;/var/lib/docker/containers/88d23bcbe1f28e1f8ae5d2b63fa8d57d2abcbdacf193db05852f4f74a95b9ffe/hostname&quot;,
        &quot;HostsPath&quot;: &quot;/var/lib/docker/containers/88d23bcbe1f28e1f8ae5d2b63fa8d57d2abcbdacf193db05852f4f74a95b9ffe/hosts&quot;,
        &quot;LogPath&quot;: &quot;/var/lib/docker/containers/88d23bcbe1f28e1f8ae5d2b63fa8d57d2abcbdacf193db05852f4f74a95b9ffe/88d23bcbe1f28e1f8ae5d2b63fa8d57d2abcbdacf193db05852f4f74a95b9ffe-json.log&quot;,
        &quot;Name&quot;: &quot;/silly_lichterman&quot;,
        &quot;RestartCount&quot;: 0,
        &quot;Driver&quot;: &quot;overlay2&quot;,
        &quot;Platform&quot;: &quot;linux&quot;,
        &quot;MountLabel&quot;: &quot;&quot;,
        &quot;ProcessLabel&quot;: &quot;&quot;,
        &quot;AppArmorProfile&quot;: &quot;&quot;,
        &quot;ExecIDs&quot;: null,
        &quot;HostConfig&quot;: {
            &quot;Binds&quot;: null,
            &quot;ContainerIDFile&quot;: &quot;&quot;,
            &quot;LogConfig&quot;: {
                &quot;Type&quot;: &quot;json-file&quot;,
                &quot;Config&quot;: {}
            },
            &quot;NetworkMode&quot;: &quot;default&quot;,
            &quot;PortBindings&quot;: {},
            &quot;RestartPolicy&quot;: {
                &quot;Name&quot;: &quot;no&quot;,
                &quot;MaximumRetryCount&quot;: 0
            },
            &quot;AutoRemove&quot;: false,
            &quot;VolumeDriver&quot;: &quot;&quot;,
            &quot;VolumesFrom&quot;: null,
            &quot;CapAdd&quot;: null,
            &quot;CapDrop&quot;: null,
            &quot;CgroupnsMode&quot;: &quot;host&quot;,
            &quot;Dns&quot;: [],
            &quot;DnsOptions&quot;: [],
            &quot;DnsSearch&quot;: [],
            &quot;ExtraHosts&quot;: null,
            &quot;GroupAdd&quot;: null,
            &quot;IpcMode&quot;: &quot;private&quot;,
            &quot;Cgroup&quot;: &quot;&quot;,
            &quot;Links&quot;: null,
            &quot;OomScoreAdj&quot;: 0,
            &quot;PidMode&quot;: &quot;&quot;,
            &quot;Privileged&quot;: false,
            &quot;PublishAllPorts&quot;: false,
            &quot;ReadonlyRootfs&quot;: false,
            &quot;SecurityOpt&quot;: null,
            &quot;UTSMode&quot;: &quot;&quot;,
            &quot;UsernsMode&quot;: &quot;&quot;,
            &quot;ShmSize&quot;: 67108864,
            &quot;Runtime&quot;: &quot;runc&quot;,
            &quot;ConsoleSize&quot;: [
                0,
                0
            ],
            &quot;Isolation&quot;: &quot;&quot;,
            &quot;CpuShares&quot;: 0,
            &quot;Memory&quot;: 0,
            &quot;NanoCpus&quot;: 0,
            &quot;CgroupParent&quot;: &quot;&quot;,
            &quot;BlkioWeight&quot;: 0,
            &quot;BlkioWeightDevice&quot;: [],
            &quot;BlkioDeviceReadBps&quot;: null,
            &quot;BlkioDeviceWriteBps&quot;: null,
            &quot;BlkioDeviceReadIOps&quot;: null,
            &quot;BlkioDeviceWriteIOps&quot;: null,
            &quot;CpuPeriod&quot;: 0,
            &quot;CpuQuota&quot;: 0,
            &quot;CpuRealtimePeriod&quot;: 0,
            &quot;CpuRealtimeRuntime&quot;: 0,
            &quot;CpusetCpus&quot;: &quot;&quot;,
            &quot;CpusetMems&quot;: &quot;&quot;,
            &quot;Devices&quot;: [],
            &quot;DeviceCgroupRules&quot;: null,
            &quot;DeviceRequests&quot;: null,
            &quot;KernelMemory&quot;: 0,
            &quot;KernelMemoryTCP&quot;: 0,
            &quot;MemoryReservation&quot;: 0,
            &quot;MemorySwap&quot;: 0,
            &quot;MemorySwappiness&quot;: null,
            &quot;OomKillDisable&quot;: false,
            &quot;PidsLimit&quot;: null,
            &quot;Ulimits&quot;: null,
            &quot;CpuCount&quot;: 0,
            &quot;CpuPercent&quot;: 0,
            &quot;IOMaximumIOps&quot;: 0,
            &quot;IOMaximumBandwidth&quot;: 0,
            &quot;MaskedPaths&quot;: [
                &quot;/proc/asound&quot;,
                &quot;/proc/acpi&quot;,
                &quot;/proc/kcore&quot;,
                &quot;/proc/keys&quot;,
                &quot;/proc/latency_stats&quot;,
                &quot;/proc/timer_list&quot;,
                &quot;/proc/timer_stats&quot;,
                &quot;/proc/sched_debug&quot;,
                &quot;/proc/scsi&quot;,
                &quot;/sys/firmware&quot;
            ],
            &quot;ReadonlyPaths&quot;: [
                &quot;/proc/bus&quot;,
                &quot;/proc/fs&quot;,
                &quot;/proc/irq&quot;,
                &quot;/proc/sys&quot;,
                &quot;/proc/sysrq-trigger&quot;
            ]
        },
        &quot;GraphDriver&quot;: {
            &quot;Data&quot;: {
                &quot;LowerDir&quot;: &quot;/var/lib/docker/overlay2/59b088d44f6e67f4ed336de44d19a5784c1a13fa856760bd2b166c4a4d421e2b-init/diff:/var/lib/docker/overlay2/7fc43e24b63e4656ab7e7718d3e4ef5297fe82509452be305a01605a7cdc3b97/diff&quot;,
                &quot;MergedDir&quot;: &quot;/var/lib/docker/overlay2/59b088d44f6e67f4ed336de44d19a5784c1a13fa856760bd2b166c4a4d421e2b/merged&quot;,
                &quot;UpperDir&quot;: &quot;/var/lib/docker/overlay2/59b088d44f6e67f4ed336de44d19a5784c1a13fa856760bd2b166c4a4d421e2b/diff&quot;,
                &quot;WorkDir&quot;: &quot;/var/lib/docker/overlay2/59b088d44f6e67f4ed336de44d19a5784c1a13fa856760bd2b166c4a4d421e2b/work&quot;
            },
            &quot;Name&quot;: &quot;overlay2&quot;
        },
        &quot;Mounts&quot;: [],
        &quot;Config&quot;: {
            &quot;Hostname&quot;: &quot;88d23bcbe1f2&quot;,
            &quot;Domainname&quot;: &quot;&quot;,
            &quot;User&quot;: &quot;&quot;,
            &quot;AttachStdin&quot;: false,
            &quot;AttachStdout&quot;: false,
            &quot;AttachStderr&quot;: false,
            &quot;Tty&quot;: false,
            &quot;OpenStdin&quot;: false,
            &quot;StdinOnce&quot;: false,
            &quot;Env&quot;: [
                &quot;PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin&quot;
            ],
            &quot;Cmd&quot;: [
                &quot;/bin/sh&quot;,
                &quot;-c&quot;,
                &quot;while true;do echo kuangshen;sleep 1;done&quot;
            ],
            &quot;Image&quot;: &quot;centos&quot;,
            &quot;Volumes&quot;: null,
            &quot;WorkingDir&quot;: &quot;&quot;,
            &quot;Entrypoint&quot;: null,
            &quot;OnBuild&quot;: null,
            &quot;Labels&quot;: {
                &quot;org.label-schema.build-date&quot;: &quot;20210915&quot;,
                &quot;org.label-schema.license&quot;: &quot;GPLv2&quot;,
                &quot;org.label-schema.name&quot;: &quot;CentOS Base Image&quot;,
                &quot;org.label-schema.schema-version&quot;: &quot;1.0&quot;,
                &quot;org.label-schema.vendor&quot;: &quot;CentOS&quot;
            }
        },
        &quot;NetworkSettings&quot;: {
            &quot;Bridge&quot;: &quot;&quot;,
            &quot;SandboxID&quot;: &quot;bfc28d2ba671adfe5c93325173b93c335d50d8b017eed4fdce2ab75410d6ac2e&quot;,
            &quot;HairpinMode&quot;: false,
            &quot;LinkLocalIPv6Address&quot;: &quot;&quot;,
            &quot;LinkLocalIPv6PrefixLen&quot;: 0,
            &quot;Ports&quot;: {},
            &quot;SandboxKey&quot;: &quot;/var/run/docker/netns/bfc28d2ba671&quot;,
            &quot;SecondaryIPAddresses&quot;: null,
            &quot;SecondaryIPv6Addresses&quot;: null,
            &quot;EndpointID&quot;: &quot;ad0252d454e751e2c5ecef24e64c32b0884c53242925bd66e9e5dbf5542af179&quot;,
            &quot;Gateway&quot;: &quot;172.17.0.1&quot;,
            &quot;GlobalIPv6Address&quot;: &quot;&quot;,
            &quot;GlobalIPv6PrefixLen&quot;: 0,
            &quot;IPAddress&quot;: &quot;172.17.0.2&quot;,
            &quot;IPPrefixLen&quot;: 16,
            &quot;IPv6Gateway&quot;: &quot;&quot;,
            &quot;MacAddress&quot;: &quot;02:42:ac:11:00:02&quot;,
            &quot;Networks&quot;: {
                &quot;bridge&quot;: {
                    &quot;IPAMConfig&quot;: null,
                    &quot;Links&quot;: null,
                    &quot;Aliases&quot;: null,
                    &quot;NetworkID&quot;: &quot;7254ffccbdf53e0c72c1d19252980f04fa65153ea3c7ca72af55cfac504cbe3f&quot;,
                    &quot;EndpointID&quot;: &quot;ad0252d454e751e2c5ecef24e64c32b0884c53242925bd66e9e5dbf5542af179&quot;,
                    &quot;Gateway&quot;: &quot;172.17.0.1&quot;,
                    &quot;IPAddress&quot;: &quot;172.17.0.2&quot;,
                    &quot;IPPrefixLen&quot;: 16,
                    &quot;IPv6Gateway&quot;: &quot;&quot;,
                    &quot;GlobalIPv6Address&quot;: &quot;&quot;,
                    &quot;GlobalIPv6PrefixLen&quot;: 0,
                    &quot;MacAddress&quot;: &quot;02:42:ac:11:00:02&quot;,
                    &quot;DriverOpts&quot;: null
                }
            }
        }
    }
]
```
### 进入当前正在运行的容器

```powershell
# 我们通常容器都是使用后台方式运行的，需要进入容器，修改一些配置
# 命令
docker exec -it 容器id /bin/bash

# 测试
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS     NAMES
88d23bcbe1f2   centos    &quot;/bin/sh -c &#39;while t…&quot;   13 minutes ago   Up 13 minutes             silly_lichterman
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker exec -it 88d23bcbe1f2 /bin/bash
[root@88d23bcbe1f2 /]# ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 08:23 ?        00:00:00 /bin/sh -c while true;do echo kuangshen;sleep 1;done
root       841     0  0 08:37 pts/0    00:00:00 /bin/bash
root       858     1  0 08:37 ?        00:00:00 /usr/bin/coreutils --coreutils-prog-shebang=sleep /usr/bin/sleep 1
root       859   841  0 08:37 pts/0    00:00:00 ps -ef

# 方式二
docker attach 容器id
# 测试
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker attach 88d23bcbe1f2
正在执行当前的代码...

# docker exec		# 进入容器后开启一个新的终端，可以再里面操作（常用）
# docker attach		# 进入容器正在执行的终端，不会启动新的进程。
```
### 从容器内拷贝文件到主机上

```powershell
docker cp 容器id:容器内路径 目的主机的路径

[root@iZbp13qr3mm4ucsjumrlgqZ home]# ll
total 0
[root@iZbp13qr3mm4ucsjumrlgqZ home]# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
[root@iZbp13qr3mm4ucsjumrlgqZ home]# docker run -it centos /bin/bash
[root@6eda31ad7987 /]# [root@iZbp13qr3mm4ucsjumrlgqZ home]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
6eda31ad7987   centos    &quot;/bin/bash&quot;   17 seconds ago   Up 16 seconds             stoic_kepler
# 进入到容器内部
[root@iZbp13qr3mm4ucsjumrlgqZ home]# docker attach 6eda31ad7987
[root@6eda31ad7987 /]# ls
bin  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
[root@6eda31ad7987 /]# cd /home/
[root@6eda31ad7987 home]# ls
# 在容器的/home路径下创建test.java文件
[root@6eda31ad7987 home]# touch test.java
[root@6eda31ad7987 home]# ls
test.java
[root@6eda31ad7987 home]# exit
exit
[root@iZbp13qr3mm4ucsjumrlgqZ home]# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
[root@iZbp13qr3mm4ucsjumrlgqZ home]# docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED              STATUS                      PORTS     NAMES
6eda31ad7987   centos    &quot;/bin/bash&quot;   About a minute ago   Exited (0) 28 seconds ago             stoic_kepler
# 将文件拷贝出来到主机上（在主机上执行该命令）
[root@iZbp13qr3mm4ucsjumrlgqZ home]# docker cp 6eda31ad7987:/home/test.java /home
[root@iZbp13qr3mm4ucsjumrlgqZ home]# ls
test.java

# 拷贝是一个手动过程，未来我们使用 -v 卷的技术，可以实现，自动同步（容器内的/home路径和主机上的/home路径打通）
```
## 5. 小结
![在这里插入图片描述](https://img-blog.csdnimg.cn/383865dd59f64bd88cbe6b4a56f1315c.png)
## 6. 作业练习
### docker安装nginx
1. 搜索镜像：docker search nginx		(建议去dockerHub上去搜索)
2. 下载镜像：docker pull nginx
3. 启动nginx：
	```powershell
	# -d 后台运行
	# --name=&quot;nginx01&quot;	给容器命名
	# -p 宿主机端口:容器内部端口
	[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker run -d --name=&quot;nginx-1&quot; -p 3344:80 nginx
	6e02190a50bc8d79653ffa88f6b5c143d79c5ac3257d5d5ed6a01247980fb48a
	[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker ps
	CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                                   NAMES
	6e02190a50bc   nginx     &quot;/docker-entrypoint.…&quot;   18 seconds ago   Up 17 seconds   0.0.0.0:3344-&gt;80/tcp, :::3344-&gt;80/tcp   nginx-1
	
	# 进入容器
	[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker exec -it a1e130aa184d /bin/bash
	root@a1e130aa184d:/# whereis nginx
	nginx: /usr/sbin/nginx /usr/lib/nginx /etc/nginx /usr/share/nginx
	root@a1e130aa184d:/# cd /etc/nginx/
	root@a1e130aa184d:/etc/nginx# ls
	conf.d  fastcgi_params  mime.types  modules  nginx.conf  scgi_params  uwsgi_params
	```

4. 本机测试

	```powershell
	[root@iZbp13qr3mm4ucsjumrlgqZ ~]# curl localhost:3344
	&lt;!DOCTYPE html&gt;
	&lt;html&gt;
	&lt;head&gt;
	&lt;title&gt;Welcome to nginx!&lt;/title&gt;
	&lt;style&gt;
	html { color-scheme: light dark; }
	body { width: 35em; margin: 0 auto;
	font-family: Tahoma, Verdana, Arial, sans-serif; }
	&lt;/style&gt;
	&lt;/head&gt;
	&lt;body&gt;
	&lt;h1&gt;Welcome to nginx!&lt;/h1&gt;
	&lt;p&gt;If you see this page, the nginx web server is successfully installed and
	working. Further configuration is required.&lt;/p&gt;
	
	&lt;p&gt;For online documentation and support please refer to
	&lt;a href=&quot;http://nginx.org/&quot;&gt;nginx.org&lt;/a&gt;.&lt;br/&gt;
	Commercial support is available at
	&lt;a href=&quot;http://nginx.com/&quot;&gt;nginx.com&lt;/a&gt;.&lt;/p&gt;
	
	&lt;p&gt;&lt;em&gt;Thank you for using nginx.&lt;/em&gt;&lt;/p&gt;
	&lt;/body&gt;
	&lt;/html&gt;
	```
	

&gt; 端口暴露的概念

![在这里插入图片描述](https://img-blog.csdnimg.cn/c07e77f5e7f0487182b3ffd0881adfff.png)
`思考问题：我们每次改动nginx配置文件，都需要进入容器内部？十分的麻烦，我要是可以在容器外部提供一个映射路径，达到在容器外修改文件名，容器内部就可以自动修改？-v 数据卷`

### docker安装tomcat

```powershell
# 官方的使用
docker run -it --rm tomcat

# 我们之前的启动都是后台，停止了容器之后，容器还是可以查到docker run -it --rm，一般用来测试，用完就删除。

# 下载
docker pull tomcat

# 启动运行
docker run -d --name=&quot;tomcat01&quot; -p 3355:8080 tomcat

# 测试访问没有问题，但是找不到资源
# 进入容器，有一个webapps文件夹和webapps.dist文件夹
docker exec -it tomcat01 /bin/bash
# webapps文件夹下没有资源，资源都在webapp.dist文件夹下
root@35eb825661e0:/usr/local/tomcat# ls
BUILDING.txt  CONTRIBUTING.md  LICENSE  NOTICE  README.md  RELEASE-NOTES  RUNNING.txt  bin  conf  lib  logs  native-jni-lib  temp  webapps  webapps.dist  work

# 发现问题：（阿里云镜像的原因：默认是最小的镜像，所有不必要的都剔除掉）保证最小可运行的环境
# 1、Linux命令少了。
# 2、没有webapps文件夹。

# 没有webapps文件夹，发现有一个webapps.dist文件夹，资源在webapps.dist文件夹下；
# 把webapps.dist文件夹下的文件复制到webapps文件夹下，就可以访问成功。
root@35eb825661e0:/usr/local/tomcat# cp -r webapps.dist/* webapps
```
思考问题：我们以后要部署项目，如果每次都要进入容器是不是十分麻烦？我要是可以在容器外部提供一个映射路径，webapps，我们在外部放置项目，就自动同步到内部就好了！

### 部署ES+kibana

```powershell
# es暴露的端口很多！
# es十分的耗内存！
# es的数据一般需要放置到安全目录！挂载

# 下载启动elasticsearch
docker run -d --name elasticsearch -p 9200:9200 -p 9300:9300 -e &quot;discovery.type=single-node&quot; elasticsearch:7.6.2

# 启动了linux就卡住了，es是十分耗内存的（1核2G）
# 查看cpu的状态
docker stats 
# 测试一下es是成功的
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# curl localhost:9200
{
  &quot;name&quot; : &quot;7ed338b2a87c&quot;,
  &quot;cluster_name&quot; : &quot;docker-cluster&quot;,
  &quot;cluster_uuid&quot; : &quot;enAVpI1oQoW4tLmafuWcnw&quot;,
  &quot;version&quot; : {
    &quot;number&quot; : &quot;7.6.2&quot;,
    &quot;build_flavor&quot; : &quot;default&quot;,
    &quot;build_type&quot; : &quot;docker&quot;,
    &quot;build_hash&quot; : &quot;ef48eb35cf30adf4db14086e8aabd07ef6fb113f&quot;,
    &quot;build_date&quot; : &quot;2020-03-26T06:34:37.794943Z&quot;,
    &quot;build_snapshot&quot; : false,
    &quot;lucene_version&quot; : &quot;8.4.0&quot;,
    &quot;minimum_wire_compatibility_version&quot; : &quot;6.8.0&quot;,
    &quot;minimum_index_compatibility_version&quot; : &quot;6.0.0-beta1&quot;
  },
  &quot;tagline&quot; : &quot;You Know, for Search&quot;
}
# 赶紧关闭，增加内存的限制，修改配置文件-e环境配置修改
docker run -d --name elasticsearch -p 9200:9200 -p 9300:9300 -e &quot;discovery.type=single-node&quot; -e ES_JAVA_OPTS=&quot;-Xms64m -Xmx512m&quot; elasticsearch:7.6.2
# 可以访问成功；查看cpu状态
```
作业：使用kibana连接es？思考网络如何才能连接过去！
![在这里插入图片描述](https://img-blog.csdnimg.cn/db499d541e114a53a896c928fb5e8167.png)
## 7. 可视化
- portainer（先用这个）
	

```powershell
docker run -d -p 8088:9000 --restart=always -v /var/run/docker.sock:/var/run/docker.sock --privileged=true portainer/portainer
```

- Rancher（CI/CD时再用这个）

### 什么是portainer ?
Docker图形化界面管理工具！提供一个后台面板供我们操作！

```powershell
# 启动运行
docker run -d -p 8088:9000 --restart=always -v /var/run/docker.sock:/var/run/docker.sock --privileged=true portainer/portainer
```
访问测试：http://ip:8088
![在这里插入图片描述](https://img-blog.csdnimg.cn/d97228af6226442ca7a4c627479f74c5.png)
选择本地的：Local
![在这里插入图片描述](https://img-blog.csdnimg.cn/22c80e1b155640398dd3f3c9da9998a7.png)
进入之后的面板
![在这里插入图片描述](https://img-blog.csdnimg.cn/87ab76e133a948fbbf1909ecae20df1b.png)
# 四、Docker镜像讲解
## 1. 镜像是什么
镜像是一种轻量级、可执行的独立软件包，用来打包软件运行环境和基于运行环境开发的软件，它包含运行某个软件所需的所有内容，包括代码、运行时、库、环境变量和配置文件。
所有的应用，直接打包docker镜像，就可以直接跑起来！
如何得到镜像：
- 从远程仓库下载
- 朋友拷贝给你
- 自己制作一个镜像DockerFile

## 2. Docker镜像加速原理
### UnionFS（联合文件系统）
我们下载的时候看到的一层层就是这个！
UnionFS（联合文件系统）：Union文件系统（UnionFS）是一种分层、轻量级并且高性能的文件系统，它支持对文件系统的修改作为一次提交来一层层的叠加，同时可以将不同目录挂载到同一个虚拟文件系统下（unite several directories into a single virtual filesystem）。Union 文件系统是Docker 镜像的基础。镜像可以通过分层来进行继承，基于基础镜像（没有父镜像），可以制作各种具体的应用镜像。

特性：一次同时加载多个文件系统，但从外面看起来，只能看到一个文件系统，联合加载会把各层文件系统叠加起来，这样最终的文件系统会包含所有底层的文件和目录。

### Docker镜像加载原型
docker的镜像实际上由一层一层的文件系统组成，这种层级的文件系统UnionFS。

bootfs（boot file system）主要包含bootloader和kernel，bootloader主要是引导加载kernel，Linux刚启动时会加载bootfs文件系统，在Docker镜像的最底层是bootfs。这一层与我们典型的Linux/Unix系统是一样的，包含boot加载器和内核。当boot加载完成之后整个内核就都在内存中了，此时内存的使用权已由bootfs转交给内核，此时系统也会卸载bootfs。

rootfs（root file system），在bootfs之上。包含的就是典型Linux系统中的/dev，/proc，/bin，/etc等标准目录和文件。
rootfs就是各种不同的操作系统发行版，比如Ubuntu，Centos等等。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2979b1cb9ae24cf8b1f3e92bc1c7d666.png)
平时我们安装进虚拟机的CentOS都是好几个G，为什么Docker这里才200M？
![在这里插入图片描述](https://img-blog.csdnimg.cn/0e3b0e98c314470fa59d15419aaa4681.png)
对于一个精简的OS，rootfs可以很小，只需要包含最基本的命令，工具和程序库就可以了，因为底层直接用Host的kernel，自己只需要提供rootfs就可以了。
由此可见对于不同的linux发行版，bootfs基本是一致的，rootfs会有差别，因此不同的发行版可以公用bootfs。
（虚拟机是分钟级，容器是秒级！）
## 3. 分层理解
### 分层的镜像
我们可以去下载一个镜像，注意观察下载的日志输出，可以看到是一层一层的在下载！
![在这里插入图片描述](https://img-blog.csdnimg.cn/db130ea8682d484bbac8333f69773752.png)
思考：为什么Docker镜像要采用这种分层的结构呢？
最大的好处，我觉得莫过于是资源共享了！比如有多个镜像都从相同的Base镜像构建而来，那么宿主机只需在磁盘上保留一份base镜像，同时内存中也只需要加载一份base镜像，这样就可以为所有的容器服务了，而且镜像的每一层都可以被共享。
查看镜像分层的方式可以通过 docker image inspect命令！

```powershell
[
		// ......
        &quot;RootFS&quot;: {
            &quot;Type&quot;: &quot;layers&quot;,
            &quot;Layers&quot;: [
                &quot;sha256:2edcec3590a4ec7f40cf0743c15d78fb39d8326bc029073b41ef9727da6c851f&quot;,
                &quot;sha256:9b24afeb7c2f21e50a686ead025823cd2c6e9730c013ca77ad5f115c079b57cb&quot;,
                &quot;sha256:4b8e2801e0f956a4220c32e2c8b0a590e6f9bd2420ec65453685246b82766ea1&quot;,
                &quot;sha256:529cdb636f61e95ab91a62a51526a84fd7314d6aab0d414040796150b4522372&quot;,
                &quot;sha256:9975392591f2777d6bf4d9919ad1b2c9afa12f9a9b4d260f45025ec3cc9b18ed&quot;,
                &quot;sha256:8e5669d8329116b8444b9bbb1663dda568ede12d3dbcce950199b582f6e94952&quot;
            ]
        },
        &quot;Metadata&quot;: {
            &quot;LastTagTime&quot;: &quot;0001-01-01T00:00:00Z&quot;
        }
    }
]
```
**理解：**
所有的Docker 镜像都起始于一个基础镜像层，当进行修改或增加新的内容时，就会在当前镜像层之上，创建新的镜像层。
举一个简单的例子，假如基于Ubuntu Linux 16.04创建一个新的镜像，这就是新镜像的第一层；如果在该镜像中添加Python包，就会在基础镜像层之上创建第二个镜像层；如果继续添加一个安全补丁，就会创建第三个镜像层。
该镜像当前已经包含3个镜像层，如下图所示（这只是一个用于演示的很简单的例子）。
![在这里插入图片描述](https://img-blog.csdnimg.cn/9863930d17ed4093b9183fa4bb7470e6.png)
在添加额外的镜像层的同时，镜像始终保持是当前所有镜像的组合，理解这一点非常重要。下图中举了一个简单的例子，每个镜像层包含3个文件，而镜像包含了来自两个镜像层的6个文件。
![在这里插入图片描述](https://img-blog.csdnimg.cn/7ef963ba3271426885fdb033e3f27a12.png)
上图中的镜像层跟之前图中的略有区别，主要目的是便于展示文件。
下图中展示了一个稍微复杂的三层镜像，在外部看来整个镜像只有6个文件，这是因为最上层中的文件7是文件5的一个更新版本。
![在这里插入图片描述](https://img-blog.csdnimg.cn/4635178e0b794754939c5e5f602ea2e4.png)
这种情况下，上层镜像层中的文件覆盖了底层镜像层中的文件。这样就使得文件的更新版本作为一个新镜像层添加到镜像当中。
Docker通过存储引擎（新版本采用快照机制）的方式来实现镜像层堆栈，并保证多镜像层对外展示为统一的文件系统。
Linux上可用的存储引擎有AUFS、Overlay2、Device Mapper、Btrfs以及ZFS。顾名思义，每种存储引擎都基于Linux中对应的文件系统或者块设备技术，并且每种存储引擎都有其独有的性能特点。
Docker在Windows 上仅支持 windowsfilter一种存储引擎，该引擎基于NTFS文件系统之上实现了分层和CoW[1]。
下图展示了与系统显示相同的三层镜像。所有镜像层堆叠并合并，对外提供统一的视图。
![在这里插入图片描述](https://img-blog.csdnimg.cn/765f1e60ff06464d98bd33391ce50891.png)
### 特点
Docker镜像都是只读的，当容器启动时，一个新的可写层被加载到镜像的顶部！
这一层就是我们通常说的容器层，容器之下的都叫镜像层！
![在这里插入图片描述](https://img-blog.csdnimg.cn/8144d08138314609907009189cf18080.png)
## 4. commit镜像

```powershell
# 提交容器成为一个新的副本
docker commit
# 命令和git原理类似
docker commit -m=&quot;提交的描述信息&quot; -a=&quot;作者&quot; 容器id 目标镜像名:[TAG]
```
### 实战测试

```powershell
# 1.启动一个默认的tomcat。
# 2.发现这个默认的tomcat是没有webapps应用，镜像的原因，官方的镜像默认webapps下面是没有文件的。
# 3.我自己拷贝进去了基本的文件。
# 4.将我们操作过的容器通过commit提交为一个镜像！我们以后就使用我们修改过的镜像即可，这就是我们自己的一个修改的镜像。
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/1e67b5e250ac491d91191c1d12361217.png)

学习方式说明：理解概念，但是一定要实践，最后实践和理论相结合一次搞定这个知识如果你想要保存当前容器的状态，就可以通过commit来提交，获得一个镜像，就好比我们以前学习VM时候，快照！到了这里才算是入门Dokcer！
# 五、容器数据卷
## 1. 什么是容器数据卷
**docker的理念回顾**
将应用和环境打包成一个镜像！
数据？如果数据都在容器中，那么我们容器删除，数据就会丢失！（需求：数据可以持久化）
MySQL，容器删了，删库跑路！（需求：MySQL数据可以存储在本地）
容器之间可以有一个数据共享的技术！Docker容器中产生的数据，同步到本地！
这就是卷技术！目录的挂载，将我们容器内的目录，挂载到Linux主机上面！
![在这里插入图片描述](https://img-blog.csdnimg.cn/1a3836dc6eb64763a2a001bf60dcfdc0.png)
`总结一句话：容器的持久化和同步操作！容器间也是可以数据共享的！`

## 2. 使用数据卷
### 直接使用命令来挂载：-v

```powershell
docker run -it -v 主机目录:容器内目录 镜像名 /bin/bash
# 测试，查看容器信息
docker inspect 容器id
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/04bf1adef71a42c3943c11df5725a91b.png)
测试文件的同步：
在容器的/home文件夹下，新建test.java文件，会同步到主机的/home/ceshi文件夹下。
`删除操作也是同步的；双向绑定，保证两边文件夹下的数据始终是一直的。`

![在这里插入图片描述](https://img-blog.csdnimg.cn/a8164d32aef9493caae71107d983fa84.png)
再来测试：
停止容器后，在主机的/home/ceshi文件夹下，修改文件或新增文件，启动容器，查看容器的/home文件夹，发现容器内的数据依旧是同步的
1. 停止容器。
2. 宿主机上修改文件。
3. 启动容器。
4. 容器内的数据依旧是同步的。
![在这里插入图片描述](https://img-blog.csdnimg.cn/3afc0b10472f4095821c4ade058edfa1.png)
好处：我们以后修改只需要在本地修改即可，容器内会自动同步！|

## 3. 实战：安装mysql

```powershell
# 获取镜像
docker pull mysql:5.7
# 运行容器，需要做数据目录挂载。（安装启动mysql，注意：需要配置密码）
# 官方启动mysql
docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag
# 我们启动mysql（-e是环境配置）
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker run -d -p 7777:3306 -v /home/mysql/conf:/etc/mysql/conf.d -v /home/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 --name mysql01 mysql:5.7

# 启动成功之后，我们在本地使用navicat来接测试一下。
# navicat连接到服务器的7777端口和容器内的3306映射，这个时候我们就可以连接上了！
# 在本地测试创建一个数据库，查看一下我们映射的路径是否ok！（OK的）
```
如果我们将容器删除：
![在这里插入图片描述](https://img-blog.csdnimg.cn/bce7ab0857224804b502ef82504cc1da.png)

发现，我们挂载到本地的数据卷依旧没有丢失，这就实现了容器数据持久化功能！

## 4. 匿名和具名挂载

```powershell
# 匿名挂载
docker run -d -p --name nginx01 -v /etc/nginx nginx
# 查看所有的volume的情况
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker volume ls
DRIVER    VOLUME NAME
local     964b8e505f12f65fb23fd21f05cfa9ecd6c2c6b2ca89c0e44f168bb017dfabd6
# 这种就是匿名挂载：我们在-v挂载目录时，只写了容器内的路径，没有写容器外的路径。

# 具名挂载
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker run -d -p 3344:80 --name nginx02 -v juming-nginx:/etc/nginx nginx
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker volume ls
DRIVER    VOLUME NAME
local     964b8e505f12f65fb23fd21f05cfa9ecd6c2c6b2ca89c0e44f168bb017dfabd6
local     juming-nginx
# 通过 -v 卷名:容器内的路径（具名挂载）
# 查看一下这个卷
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/e214799a7d3d4fabaf627f5ce947aa45.png)
所有的docker容器内的卷，没有指定目录的情况下都是在`/var/lib/docker/volumes/xxxx/_data&quot;`（xxxx是卷名）
我们通过具名挂载可以方便的找到我们的一个卷，`大多数情况在使用的具名挂载`

```powershell
# 如何确定是具名挂载，还是匿名挂载，还是指定路径挂载
-v 容器内的路径				# 匿名挂载
-v 卷名:容器内的路径		# 具名挂载
-v /宿主机路径:容器内路径	# 指定路径挂载
```
拓展：

```powershell
# 通过 -v 容器内的路径:ro	rw	改变读写权限
ro	read only	# 只读
rw	read write	# 可读可写

# 一旦设置了容器权限，容器对我们挂载出来的内容就有了限定。
docker run -d -p 3344:80 --name nginx02 -v juming-nginx:/etc/nginx:ro nginx
docker run -d -p 3344:80 --name nginx02 -v juming-nginx:/etc/nginx:rw nginx
# 只要看到ro就说明这个路径只能通过宿主机来操作，容器内部是无法操作！
```
## 5. 初识Dockerfile
Dockerfile就是用来构建 docker 镜像的构建命令！命令脚本！先体验一下！
通过这个脚本可以生成镜像，镜像是一层一层的，脚本一个一个的命令，每个命令都是一层！

```powershell
# 创建一个dockerfile文件，名字可以随机，建议dockerfile
# 文件中的内容：指令都是大写
FROM centos
VOLUME [&quot;volume01&quot;,&quot;volume02&quot;]
CMD echo &quot;-----end-----&quot;
CMD /bin/bash
# 这里的每个命令，就是镜像的一层。

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/8c3eddc6cd9b415e9382c41976080a5e.png)
启动自己写的容器：
![在这里插入图片描述](https://img-blog.csdnimg.cn/48134489ae4646aa90190744fe507435.png)
这个卷和外部一定有一个同步的目录！
![在这里插入图片描述](https://img-blog.csdnimg.cn/7c09b250f26549e7a8d505549c902802.png)
查看一下卷挂载的路径：docker inspect 容器id
![在这里插入图片描述](https://img-blog.csdnimg.cn/ccf82d7d7ccb4433962014e2bd85a091.png)
测试一下文件是否同步出去：在容器的volume01文件夹下创建文件，查看宿主机对应目录是否同步成功。
`这种方式我们未来使用的十分多，因为我们通常会构建自己的镜像！`
如果构建镜像时候没有挂载卷，就需要自己手动镜像挂载目录！

## 6. 数据卷容器
多个mysql同步数据
![在这里插入图片描述](https://img-blog.csdnimg.cn/83ae90d4016d4b58a3f7008d1a980247.png)

```powershell
# 启动3个容器，通过我们刚才自己的写镜像启动。
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/53263e57bd3342e3bb56d168a30db360.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/79088a4ed27e47b9a77fb71e3988e740.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/d0c73f1f20d6455f92169b81dafc6778.png)

```powershell
# 测试：可以删除docker01，查看一下docker02和docker03是否还可以访问这个文件
# 测试依旧可以访问
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/11127a59728f4994975e379b34bea768.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/993d33e1120c4fc8a643772daf2b1041.png)
多个mysql实现数据共享：

```powershell
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker run -d -p 7777:3306 -v /home/mysql/conf:/etc/mysql/conf.d -v /home/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 --name mysql01 mysql:5.7

[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker run -d -p 7777:3306 -e MYSQL_ROOT_PASSWORD=123456 --name mysql02 --volumes-from mysql01 mysql:5.7

# 这个时候，可以实现两个容器数据同步！
```
结论：
容器之间配置信息的传递，数据卷容器的生命同期一直持续到没有容器使用为止。
但是一旦你持久化到了本地，这个时候，本地的数据是不会删除的！

# 六、DockerFile
## 1. DockerFile介绍
dockerfile是用来构建docker镜像的文件！命令参数脚本！
构建步骤：
1、编写一个dockerfile文件
2、docker build 构建成为一个镜像
3、docker run运行镜像
4、docker push发布镜像（DockerHub、阿里云镜像仓库！）
查看一下官方是怎么做的？
![在这里插入图片描述](https://img-blog.csdnimg.cn/14043f8e717c4ae2b4e80a6ff03496dc.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/e489fa9a6e564c95b4a015751612b76e.png)
## 2. DockerFile的构建过程
### 基础知识
1、每个保留关键字（指令）都是必须是大写字母
2、执行从上到下顺序执行
3、# 表示注释
4、每一个指令都会创建提交一个新的镜像层，并提交！
![在这里插入图片描述](https://img-blog.csdnimg.cn/c17459384d6d494181b6e344b9cf3f7b.png)
dockerfile是面向开发的，我们以后要发布项目，做镜像，就需要编写dockerfile文件，这个文件十分简单！
Docker镜像逐渐成为企业交付的标准，必须要掌握！
步骤：开发，部署，运维。。。缺一不可！|
DockerFile：构建文件，定义了一切的步骤，源代码。
Dockerlmages：通过DockerFile构建生成的镜像，最终发布和运行的产品。
Docker容器：容器就是镜像运行起来提供服务的。

## 3. DockerFile的命令
以前的话我们就是使用别人的，现在我们知道了这些指令后，我们来练习自己写一个镜像！
```shell
FROM		# 基础镜像，一切从这里开始构建
MAINTAINER	# 镜像是谁写的：姓名+邮箱
RUN			# 镜像构建的时候需要运行的命令
ADD			# 步骤：tomcat镜像，这个tomcat压缩包！添加内容
WORKDIR		# 镜像的工作目录
VOLUME		# 挂载的目录
EXPOSE		# 暴露端口配置
CMD			# 指定这个容器启动的时候要运行的命令，只有最后一个会生效，可被替代
ENTRYPOINT	# 指定这个容器启动的时候要运行的命令，可以追加命令
ONBUILD		# 当构建一个被继承DockerFile这个时候就会运行ONBUILD的指令。触发指令。
COPY		# 类似ADD，将我们文件拷贝到镜像中
ENV			# 构建的时候设置环境变量！
```
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/03/kuangstudyd150327c-9e51-48ab-8867-dee808407452.jpg)

## 4. 实战测试
Docker Hub中99%镜像都是从这个基础镜像过来的FROM scratch，然后配置需要的软件和配置来进行的构建。
```shell
# 1. 编写dockerfile的文件
FROM centos:7
MAINTAINER sywl&lt;xxx@qq.com&gt;

ENV MYPATH /usr/local
WORKDIR $MYPATH

RUN yum -y install vim
RUN yum -y install net-tools

EXPOSE 80

CMD echo $MYPATH
CMD echo &quot;-----end-----&quot;
CMD /bin/bash

# 2. 通过这个文件构建镜像
# 命令：docker build -f dockerfile文件路径 -t 镜像名:[tag]
docker build -f mydockerfile-centos -t mycentos:0.1 .

Successfully built 285c2064af01
Successfully tagged mycentos:0.1

# 3. 测试运行
```
对比：
之前的原生的centos7：
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/03/kuangstudy3e59f341-6850-445c-a1bc-330c574a781c.jpg)
我们增加之后的镜像：
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/03/kuangstudye10e7d39-2971-4e5e-ae7e-6646b3a97a35.jpg)
我们可以列出本地进行的变更历史：docker history 镜像id
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/03/kuangstudy62d94e6e-5f92-4f5e-aa5b-be3574e4ac6b.jpg)

&gt; CMD和ENTRYPOINT区别

```shell
CMD            # 指定这个容器启动的时候要运行的命令，只有最后一个会生效，可被替代
ENTRYPOINT     # 指定这个容器启动的时候要运行的命令，可以追加命令
```
测试CMD
```shell
# 1. 编写dockerfile文件
[root@iZbp13qr3mm4ucsjumrlgqZ dockerfile]# vim mydockerfile-cmd-test
[root@iZbp13qr3mm4ucsjumrlgqZ dockerfile]# cat mydockerfile-cmd-test
FROM centos:7
CMD [&quot;ls&quot;,&quot;-a&quot;]
# 2. 构建镜像
[root@iZbp13qr3mm4ucsjumrlgqZ dockerfile]# docker build -f mydockerfile-cmd-test -t cmdtest .
# 3. run运行，发现我们的&quot;ls -a&quot;命令生效、执行
```
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/03/kuangstudy3d3be186-424a-4bb4-a51d-198cc4d7f3fa.jpg)
```shell
# 4. 我们先追加一个命令&quot;l&quot;,构成&quot;ls -al&quot;命令，发现报错
[root@iZbp13qr3mm4ucsjumrlgqZ dockerfile]# docker run ec0d2dd226b3 -l
docker: Error response from daemon: failed to create shim task: OCI runtime create failed: runc create failed: unable to start container process: exec: &quot;-l&quot;: executable file not found in $PATH: unknown.
ERRO[0000] error waiting for container: context canceled

# 原因：CMD命令的情况下，&quot;-l&quot;替换了CMD[&quot;1s&quot;，&quot;-a&quot;]命令，因为&quot;-l&quot;不是命令，所以报错！
```

测试ENTRYPOINT
```shell
# 1. 编写dockerfile文件
[root@iZbp13qr3mm4ucsjumrlgqZ dockerfile]# vim mydockerfile-entrypoint-test
[root@iZbp13qr3mm4ucsjumrlgqZ dockerfile]# cat mydockerfile-entrypoint-test
FROM centos:7
ENTRYPOINT [&quot;ls&quot;,&quot;-a&quot;]
# 2. 构建镜像
[root@iZbp13qr3mm4ucsjumrlgqZ dockerfile]# docker build -f mydockerfile-entrypoint-test -t entrypointtest .
# 3. run运行，发现我们的&quot;ls -a&quot;命令生效、执行
```
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/03/kuangstudy537f09c7-32d2-413d-a54e-43265671a20e.jpg)
```shell
# 4. 我们先追加一个命令&quot;l&quot;,构成&quot;ls -al&quot;命令，发现命令生效、执行
```
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/03/kuangstudyf20ca8a9-1475-46ae-8597-cb9ed618538a.jpg)
```shell
# 原因：ENTRYPOINT命令的情况下，&quot;-l&quot;追加在ENTRYPOINT [&quot;1s&quot;，&quot;-a&quot;]命令后面，得到&quot;ls -al&quot;的命令，所以命令正常执行！
# （我们的追加命令，是直接拼接在我们的ENTRYPOINT命令的后面）
```

## 5. 制作tomcat镜像
1. 准备镜像文件：tomcat压缩包，jdk的压缩包！
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/03/kuangstudy3b8c3159-7579-42b9-99d7-8d10b48187e0.jpg)

2. 编写dockerfile文件，官方命名**Dockerfile**，build会自动寻找这个文件，就不需要-f指定文件名了！

	```shell
	FROM centos:7
	MAINTAINER sywl&lt;xxxx@qq.com&gt;

	COPY readme.txt /usr/local/readme.txt

	ADD jdk-8u271-linux-x64.tar.gz /usr/local/
	ADD apache-tomcat-9.0.5.tar.gz /usr/local/

	RUN yum -y install vim

	ENV MYPATH /usr/local
	WORKDIR $MYPATH

	ENV JAVA_HOME /usr/local/jdk1.8.0_271
	ENV CLASS_PATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
	ENV CATALINA_HOME /usr/local/apache-tomcat-9.0.5
	ENV CATALINA_BASH /usr/local/apache-tomcat-9.0.5
	ENV PATH $PATH:$JAVA_HOME/bin:$CATALINA_HOME/lib:$CATALINA_HOME/bin

	EXPOSE 8080

	CMD /usr/local/apache-tomcat-9.0.5/bin/startup.sh &amp;&amp; tail -F /usr/local/apache-tomcat-9.0.5/bin/logs/catalina.out
	```

3. 构建镜像
```shell
docker build --name diytomcat .
```
4. 启动镜像
```shell
[root@iZbp13qr3mm4ucsjumrlgqZ tomcat]# docker run -d -p 3355:8080 --name sywltomcat -v /home/sywl/build/tomcat/test:/usr/local/apache-tomcat-9.0.5/webapps/test -v /home/sywl/build/tomcat/tomcatlog:/usr/local/apache-tomcat-9.0.5/logs diytomcat
```
5. 访问测试
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/03/kuangstudyb6900457-27f2-448e-be54-6069b4f9783f.jpg)
6. 发布项目（由于做了卷挂载，我们直接在本地test文件夹下编写项目就可以发布了！）
```shell
# /home/sywl/build/tomcat/test/WEB-INF/web.xml文件
&lt;?xml version=&quot;1.0&quot; encoding=&quot;UTF-8&quot;?&gt;
&lt;web-app xmlns=&quot;http://java.sun.com/xml/ns/javaee&quot;
		xmlns:xsi=&quot;http://www.w3.org/2001/XMLSchema-instance&quot;
		xsi:schemaLocation=&quot;http://java.sun.com/xml/ns/javaee  http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd&quot;
		version=&quot;2.5&quot;&gt;
&lt;/web-app&gt;
```
```shell
# /home/sywl/build/tomcat/test/index.jsp文件
&lt;%@ page language=&quot;java&quot; contentType=&quot;text/html; charset=UTF-8&quot;
    pageEncoding=&quot;UTF-8&quot;%&gt;
&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;meta charset=&quot;utf-8&quot;&gt;
&lt;title&gt;hello,sywl&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
Hello World!&lt;br/&gt;
&lt;%
System.out.println(&quot;----my web test----&quot;);
%&gt;
&lt;/body&gt;
&lt;/html&gt;
```
发现：项目部署成功，可以直接访问ok！（ip地址:3355/test）
我们以后开发的步骤：需要掌握Dokcerfile的编写！我们之后的一切都是使用docker镜像来发布运行！

## 6. 发布自己的镜像
### 1. 发布到dockerhub上
1. https://hub.docker.com/ 注册自己的账号
2. 确定这个账号可以登录
3. 在我们服务器上提交自己的镜像
	```shell
	[root@iZbp13qr3mm4ucsjumrlgqZ tomcat]# docker login --help
	
	Usage:  docker login [OPTIONS] [SERVER]
	
	Log in to a Docker registry.
	If no server is specified, the default is defined by the daemon.
	
	Options:
	  -p, --password string   Password
		  --password-stdin    Take the password from stdin
	  -u, --username string   Username
	
	```
4. 登录完毕后就可以提交镜像了，就是一步： docker push
	```shell
	# 登录命令
	[root@iZbp13qr3mm4ucsjumrlgqZ tomcat]# docker login -u xxxx
	Password:
	WARNING! Your password will be stored unencrypted in /root/.docker/config.json.
	Configure a credential helper to remove this warning. See
	https://docs.docker.com/engine/reference/commandline/login/#credentials-store
	
	Login Succeeded
	
	# push镜像出现的问题？
	[root@iZbp13qr3mm4ucsjumrlgqZ tomcat]# docker push sunyiwenlong/diytomcat
	The push refers to repository [docker.io/sunyiwenlong/diytomcat]
	An image does not exist locally with the tag: sunyiwenlong/diytomcat
	
	# 解决，增加一个tag
	[root@iZbp13qr3mm4ucsjumrlgqZ tomcat]# docker tag 6a5eb12e1252 账号id/tomcat:1.0
	
	# docker push即可；自己发布的镜像尽量带上版本号
	[root@iZbp13qr3mm4ucsjumrlgqZ tomcat]# docker push 账号id/tomcat:1.0
	```
	
### 2. 发布到阿里云镜像服务上
1. 登录阿里云账号
2. 找到镜像容器服务
3. 创建命名空间（一个账号只能创建3个命名空间）
4. 创建镜像仓库
5. 浏览相关操作命令

## 7. 小结
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudy54d489fe-7e68-4cd4-af88-c935858260fd.jpg)

# 七、Docker网络
## 1. 理解docker0
### 测试
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudydee80493-070a-4d74-88b2-816d0bce1f3b.jpg)
有三个网络
```shell
# 问题：docker是如何处理容器网络访问的？
```
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudy21a89436-12e0-4cad-947d-77eefb762997.jpg)
```shell
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker run -d -P --name tomcat01 tomcat

# 查看容器的内部网络地址ip addr，发现容器启动的时候会得到一个eth0@if119的ip地址（docker分配的）
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker exec -it tomcat01 ip addr
1: lo: &lt;LOOPBACK,UP,LOWER_UP&gt; mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
118: eth0@if119: &lt;BROADCAST,MULTICAST,UP,LOWER_UP&gt; mtu 1500 qdisc noqueue state UP group default
    link/ether 02:42:ac:11:00:02 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 172.17.0.2/16 brd 172.17.255.255 scope global eth0
       valid_lft forever preferred_lft forever

# 思考：liunx能不能ping通容器内部？（linux可以ping通容器内部）
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# ping 172.17.0.2
PING 172.17.0.2 (172.17.0.2) 56(84) bytes of data.
64 bytes from 172.17.0.2: icmp_seq=1 ttl=64 time=0.059 ms
64 bytes from 172.17.0.2: icmp_seq=2 ttl=64 time=0.046 ms
64 bytes from 172.17.0.2: icmp_seq=3 ttl=64 time=0.057 ms
64 bytes from 172.17.0.2: icmp_seq=4 ttl=64 time=0.045 ms
```

### 原理
1. 我们每启动一个docker容器，docker就会给docker容器分配一个ip，我们只要安装了ddcker，就会有一个网卡docker0
	（桥接模式，使用的技术是veth-pair技术）
	再次测试：
	![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudy7134bffc-5262-4393-a6a0-42b27b89e906.png)
2. 在启动一个容器测试，发现又多了一对网卡。
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudya5d90c2d-5be3-4c92-b72e-b8aa1f68324e.jpg)
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudye5aa04a0-d3fe-42a1-9143-ff5809597941.jpg)
```shell
# 我们发现这个容器带来网卡，都是一对对的。
# veth-pair 就是一对的虚拟设备接口，他们都是成对出现的，一端连着协议，一端彼此相连。
# 正因为有这个特性，evth-pair充当一个桥梁，连接各种虚拟网络设备的。
# openstack，Docker容器之间的连接，OVS的连接，都是使用veth-pair技术。
```

3. 我们来测试下tomcat01和tomcat02是否可以ping通！（可以ping通）
	```shell
	[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker exec -it tomcat02 ping 172.17.0.2
	PING 172.17.0.2 (172.17.0.2) 56(84) bytes of data.
	64 bytes from 172.17.0.2: icmp_seq=1 ttl=64 time=0.094 ms
	64 bytes from 172.17.0.2: icmp_seq=2 ttl=64 time=0.055 ms
	
	# 结论：容器和容器之间是可以互相ping通的！
	```
	绘制一个网络模型图
	![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudye5054f76-0675-4c98-a969-4d2826c95e10.jpg)
	结论：tomcat01和tomcat02是公用的一个路由器，dockero。
	所有的容器不指定网络的情况下，都是docker0路由的，docker会给我们的容器分配一个默认的可用IP

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudy1a3f75b3-decf-4b88-9d35-c02d029c5f7d.jpg)
Docker中的所有的网络接口都是虚拟的。虚拟的转发效率高！（内网传递文件！）
只要容器删除，对应网桥一对就没了！
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudy0a4781e6-e272-4e1f-a184-ffe7d6ff1692.jpg)

## 2. --link
### 思考一个场景（高可用）
我们编写了一个微服务，database url=ip:，项目不重启，数据库ip换掉了，我们希望可以处理这个问题，可以名字来进行访问容器？

```shell
# 通过服务名ping不通；如何解决？
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker exec -it tomcat02 ping tomcat01
ping: tomcat01: Name or service not known

# 通过--link可以解决网络连接问题。
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker run -d -P --name tomcat03 --link tomcat02 tomcat:7.0
2393eecb870e5755068ea8b7d8bdcdd0f1ff110534c3359384413677c651bec4
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker exec -it tomcat03 ping tomcat02
PING tomcat02 (172.17.0.3) 56(84) bytes of data.
64 bytes from tomcat02 (172.17.0.3): icmp_seq=1 ttl=64 time=0.085 ms
64 bytes from tomcat02 (172.17.0.3): icmp_seq=2 ttl=64 time=0.055 ms

# 反向可以ping通吗？（不可以）
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker exec -it tomcat02 ping tomcat03
ping: tomcat03: Name or service not known
```
探究：docker network inspect networkID (docker network ls可以查看networkID)
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudyb4c2cdd5-23f7-4cd0-bbdc-a6c843187c99.jpg)
其实这个tomcat03就是在本地配置了tomcat02的配置？
```shell
# 查看
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker exec -it tomcat03 cat /etc/hosts
127.0.0.1       localhost
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
172.17.0.3      tomcat02 20398a94efa7
172.17.0.4      2393eecb870e
```
本质探究：--link 就是我们在hosts配置中增加了一个&quot;172.17.0.3      tomcat02 20398a94efa7&quot;
我们现在玩Docker已经不建议使用--link了！
自定义网络！不适用docker0！
docker0问题：他不支持容器名连接访问！

## 3. 自定义网络
### 查看所有的docker网络
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudyaea52932-a8b4-413d-9176-e4902b77c55a.jpg)
### 网络模式
bridge：桥接 docker（默认，自己创建也使用bridge桥接模式）
none：不配置网络
host：和主机共享网络
container：容器网络连通！（用的少！局限很大）
### 测试
```shell
# 我们直接启动的命令--net bridge（这个就是我们的docker0）；默认带上这个参数的，以下两种启动方式效果一致。
docker run -d -P --name tomcat01 tomcat
docker run -d -P --name tomcato1 --het bridge tomcat

# docker0特点：默认，域名不能访问，--1ink可以打通连接！
# 我们可以自定义一个网络！
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker network create --driver bridge --subnet 192.168.0.0/16 --gateway 192.168.0.1 mynet
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker network ls
NETWORK ID     NAME      DRIVER    SCOPE
7254ffccbdf5   bridge    bridge    local
45610891738f   host      host      local
266acd66473c   mynet     bridge    local
7795cbc2686c   none      null      local
```
我们自己的网络就创建好了
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudy5d3a6b5a-ff82-4bcb-9255-6755c473a5bd.jpg)
启动两个容器测试：
```shell
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker run -d -P --name tomcat-net-01 --net mynet tomcat:7.0
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker run -d -P --name tomcat-net-02 --net mynet tomcat:7.0
```
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudy0973705a-9efc-453a-a1b8-9d9f544c0254.jpg)
```shell
# 不使用--link，ping名字也可以ping通。tomcat-net-01 ping tomcat-net-02可以ping通
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker exec -it tomcat-net-01 ping tomcat-net-02
PING tomcat-net-02 (192.168.0.3) 56(84) bytes of data.
64 bytes from tomcat-net-02.mynet (192.168.0.3): icmp_seq=1 ttl=64 time=0.067 ms
64 bytes from tomcat-net-02.mynet (192.168.0.3): icmp_seq=2 ttl=64 time=0.056 ms
# 不使用--link，ping名字也可以ping通。tomcat-net-02 ping tomcat-net-01可以ping通
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker exec -it tomcat-net-02 ping tomcat-net-01
PING tomcat-net-01 (192.168.0.2) 56(84) bytes of data.
64 bytes from tomcat-net-01.mynet (192.168.0.2): icmp_seq=1 ttl=64 time=0.050 ms
64 bytes from tomcat-net-01.mynet (192.168.0.2): icmp_seq=2 ttl=64 time=0.056 ms
```
我们自定义的网络docker都已经帮我们维护好了对应的关系，**推荐我们平时这样使用网络**！
redis -不同的集群使用不同的网络，保证集群是安全和健康的
mysql -不同的集群使用不同的网络，保证集群是安全和健康的

## 4. 网络连通
```shell
# tomcat01在docker0网络下，tomcat-net-01在mynet网络下；
# tomcat01 ping tomcat-net-01是ping不通的
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker exec -it tomcat01 ping tomcat-net-01
ping: tomcat-net-01: Name or service not known
```
容器和mynet网络需要打通
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudy06b13128-bb64-478b-8f97-5aff19bc2536.jpg)
打通命令
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudyec3a2bcc-43e6-4081-ae71-55e6c425c046.jpg)
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudyd5ffaf3c-8422-4bc4-bd4e-69350ced4496.jpg)

```shell
# 测试：打通tomcat01连接mynet
docker network connect mynet tomcat01

# 连通之后就是将tomcat01放到了mynet网络下
# 一个容器两个ip地址！I
# 阿里云服务：公网ip和私网ip
```
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/08/04/kuangstudy08a7cb91-60d2-4d96-a468-a289267e8a12.jpg)
```shell
# 连接ok
[root@iZbp13qr3mm4ucsjumrlgqZ ~]# docker exec -it tomcat01 ping tomcat-net-01
PING tomcat-net-01 (192.168.0.2) 56(84) bytes of data.
64 bytes from tomcat-net-01.mynet (192.168.0.2): icmp_seq=1 ttl=64 time=0.065 ms
64 bytes from tomcat-net-01.mynet (192.168.0.2): icmp_seq=2 ttl=64 time=0.052 ms
```
结论：假设要跨网络操作别人，就需要使用docker network connect连通！。。。。

## 5. 实战：部署redis集群

# 八、SpringBoot微服务打包docker镜像
