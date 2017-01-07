---
title: Linux快速笔记
date: 2016-03-15 23:19:29
categories: Linux
description: Linux快速笔记；Linux常用命令；Linux常用目录位置；
tags: 
- Linux
- 笔记
- 备忘
- 面试

---

### Linux快速笔记

![Linux](https://ww2.sinaimg.cn/large/006tNbRwgw1fbik9pxmh0j30iw082q3h.jpg)

`ln -s source linkName`

建立软链接，**-s** 是symbolic link的意思，很多时候可能会认不清source和linkName的顺序，这时候可以把**-s** 当做"source"的意思。

`chown -R git:git folder`

设置一堆文件的所有者，比如服务器apache的www目录，要给www用户相应的权限。

`chmod -R 777 foder`

设置一堆文件的权限，比如.ssh中保存的authorized_keys文件；7代表二进制的111，分别代表读、写以及执行。

`ls -lh`

相当于ll

`tail -f file`

持续查看文件结尾

`which`

定位可执行文件位置

```
alias 'll=ls -hl'`
alias
```
查看或设置命令别名

`locate php.ini`

快速定位文件，尤其是配置文件

`grep`

快速文本朝找命令

`awk '{print $1}'`

按照分隔符分割每一行字符串并输出，默认分隔符是空格与TAB

`scp -r /path/filename username@servername:/path -p 22`

命令中服务器路径和本地路径可以交换

`tar`

解压：tar -x(必有，代表解压; c 代表压缩)z(代表gzip格式; j refers to bz2)v(可选，输出信息)f(必有，选择被解压文件) file.tar.gz 

`unzip xxx.zip -d newfolder`

zip解压缩

`netstat -t(tcp)u(udp)n(number)p(program name)l(listen)`

netstat -l(listening or a refers to all)t(tcp or u refers to udp)p(program)
netstat -n(using number format for ip)e(extend info)t(tcp)                    

`find /folder -name fileName [-type f]`

搜索文件

`wc -l`

find /folder -type f -name fileName [-maxdepth 0] | wc -l #文件数量

`file`

return file type, x64 etc.

`history`

命令操作历史

`last`

用户登录历史

`env`

env | grep ORACLE

`uname -a`

查看系统信息

`ps -ef(every process) | grep xxx`

查看进程

`fdisk -l`

查看所有可用于挂载的磁盘

`fdisk /dev/xvdb `

为这个磁盘建立分区表（注意：每个物理盘需要先在第一个sector建立分区表，然后每个分区进行格式化，然后挂载使用）这个命令结束后，硬盘“/dev/xvdb”会变成几个分区”/dev/xvdb1 …"

`df -h`

查看磁盘挂载情况，磁盘使用率

`du -h --max-depth=1 /folder_path` 

查看文件夹大小

`du -sh /folder` 

查看仅指定文件夹大小

`mount -t vfat /dev/XXX /folder`

挂载需提前创建目标目录

#### Linux常用目录

cat /etc/issue 查看系统版本

/etc/ssh/sshd_config 修改服务器ssh端口号

/etc/hosts hosts

/etc/hostname hostname // command

/etc/network/interfaces 修改网络配置 

/etc/resolv.conf nameserver 202.96.128.86

/etc/init.d/network restart

/etc/issue 系统版本号

/etc/passwd 用户列表以及登陆shell设置