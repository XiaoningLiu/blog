---
title: Shadowsocks on Ubuntu 16
date: 2017-01-06 19:38:00
categories: 工具
description: 
tags: 
- shadowsocks
- 科学上网
- 工具
- 翻墙
- Great File Wall
- GFW
- 网络
- 自启动

---

![shadowsocks](http://wechatair.azureedge.net/wp-content/uploads/2017/01/unnamed.png)

**导读**：Shadowsocks 是一种简便快捷的代理工具，其优异的性能可以在配置很低的机器中流畅运行，因此受到广泛的欢迎。以下是在一台全新的 Ubuntu Server 中使用 apt-get 安装并搭建 Shadowsocks Server 的过程。

本文将涉及如下的要点：

* apt-get 的使用
* shadowsocks config 配置文件的配置
* shadowsocks 服务的启动

## 安装与配置步骤

### 步骤一 使用 apt-get 安装 Shadowsocks Server
```
sudo apt update
sudo apt install shadowsocks
```

### 步骤二 创建配置文件

配置文件包含了 Shadowsocks 服务所需要的简便配置，比如加密方式与密码设置等。值得注意的是，Shadowsocks 可以不需要配置文件运行，在没有配置文件的情况下，密码等信息需要作为配置参数的形式在启动服务时传递。

为方便重复利用配置文件，可以建立配置文件，并将配置文件放置在当前用户目录下面。

```
cd ~
vim ss.config
```

在创建的 ss.config 的文件中，加入如下内容，内容以 json 格式存储，注意最后一行没有逗号。

```
{
    "server":"0.0.0.0",
    "server_port":4433,
    "local_port":4433,
    "password":"123123123",
    "timeout":600,
    "method":"aes-256-cfb",
    "auth": true
}
```

### 步骤三 启动服务

使用 apt-get 安装好 Shadowsocks Server 之后，可以直接使用 ssserver 命令启动服务。

```
ssserver -c ~/ss.config -d start
```

命令中的参数 -c 指的是配置文件的路径，这里指向了当前用户目录(~)下的 ss.config 文件。参数 -d 指的是使用 daemon 的方式启动，即可以在后台运行 Shadowsocks 服务。

### 步骤四 设置自启动

按上面的步骤配置好之后，如果遇到服务器的重新启动，那么我们需要手工登录到服务器重新运行上面的命令。我们可以将上面的命令配置到系统启动的脚本中免除手工操作的繁琐步骤。

首先，定位 ssserver 的绝对路径，可以通过 locate 命令实现。

```
myss@myss:~$ locate ssserver
/usr/local/bin/ssserver
```

另外，定位 rc.local 脚本文件的位置，可以在其中加入系统启动时候的脚本命令。

```
myss@myss:~$ locate rc.local
/etc/rc.local
```

打开 rc.local 在其中加入自动启动 Shadowsocks ssserver 服务的命令。

```
sudo vim /etc/rc.local
```

在 exit 0 行之前，加入如下命令，保存退出。

```
/usr/local/bin/ssserver -c /home/myss/ss.config -d start
```


## 问题调试

如果配置好之后不能正常连接应该怎么查找故障？这里介绍 linux 中常见的命令来辅助定位故障。

### 确认端口已经监听

上述 ss.config 配置文件中，我们使用了 4433 端口作为监听端口，因此我们使用网络调试命令查看端口是否正常打开。

```
netstat -tpn
```

netstat 命令可以查看当前系统网络连接的状况，其中四个参数的含义如下：

* -t 代表查找 TCP 的通信连接，因为 Shadowsocks 的服务是基于 TCP 协议。
* 参数 -p 代表显示对应端口占用的程序。
* 参数 -n 代表以数字的形式显示端口号码，这里我们需要寻找 4433 端口是否存在。

```
myss@myss:~$ netstat -tnp
(No info could be read for "-p": geteuid()=1000 but you should be root.)
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name  TIME_WAIT   -               
tcp        0    460 10.0.0.4:22             183.195.251.236:56598   ESTABLISHED -               
tcp        0      0 10.0.0.4:4433           58.196.146.219:59475        TIME_WAIT   -     
```

如上所示，4433端口已经处于 TCP 的等待状态，说明端口已经正常打开，端口没有问题。如果没有寻找到 4433 端口，那么说明 ssserver 的服务没有正常启动。可以按照下述方法，动态的查看 ssserver 的日志。

### 使用交互式方式查看日志

我们去掉 -d 参数，直接启动 ssserver，这样可以查看启动时候的日志，根据提示的错误信息，我们可以针对性的解决问题。

```
ssserver -c ~/ss.config
```

2017-01-06


