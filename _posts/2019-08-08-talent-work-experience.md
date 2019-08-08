---
layout: post
title: 'arachni 环境搭建问题'
categories: arachni
tags: arachni ruby linux work
author: thorleishen
---

* content
{:toc}
## 前言

工作之际遇到的arachni环境搭配的坑



## 问题一

linux安装sqlite3问题，将一台已经安装好的sqlite3移植到另一台机器上，只需要将/usr/bin目录下的可执行文件sqlite3移到另一台机器上的/usr/bin目录下就可以（有些机器的可执行sqlite3文件在/usr/local/bin目录下），并使用ruby连接sqlite3数据库时，报错找不到libsqlite3.so.0文件

解决办法如下：

```linux
# 通过find命令查找已经安装的linux机器上libsqlite3.so.0
find / -name libsqlite3.so.0
# 将上面查找到的文件移植到另一台机器上，注：libsqlite3.so.0文件是libsqlite3.so.0.8.8软链接文件
```

再次执行连接数据库的操作时，报错，还是找不到libsqlite.3.so.0文件

```linux
# 使用ldd &{dir}/libsqlite3.so.0，dir即报错的路径，并在安装好的机器执行同样的命令，比较两者之间区别
# 最后会发现libsqlite3.so.0文件的指向路径，并对比两个机器的源文件之间的差别
# 通过修改软连接指向的文件（即指向相同的文件）
ln -s /usr/lib/aarxxxx...xxx/libsqlite3.so.0.8.8 /usr/lib/libsqlite3.so.0 # 实际以自己安装的路径为主
```

再次执行就OK了😁



## 问题二

ruby安装环境问题，通过将ruby.tar.gz包解压到根目录

```linux
# 解压ruby包到根目录命令
tar -zvxf rubyxxx.tar.gz -C /
```

执行ruby -v，看到ruby相应的版本信息，但执行gem list时，报错：找不到libruby.so.0文件

```linux
# 通过将/usr/lib路径下的libruby.so.0文件移到/usr/lib/bin目录下
cp /usr/lib/libruby.so* /usr/lib/bin
```

再次执行gem list，出现安装的依赖包说明问题已经解决

![](D:\Downloads\4bb43ae1272f7aa1b04e905196ebe33a.jpg)

## 学习

- 误删/usr/lib/araxxx/libm.so.0文件，导致系统有些命令不能使用，报错：找不到libm.so.0，在不清楚文件有什么作用的时候，应该选择备份一份，养成良好的习惯
- sqlite3离线安装

```linux
# 解压离线安装文件sqlite3-xxx.tar.gz
tar -zvxf sqlite3-xxx.tar.gz  // tar -zvxf sqlite3-xxx.tar.gz /opt
# 进入到sqlite3-xxx文件
cd sqlite3-xxx
# 选择安装路径，并编译安装
./configure --prefix=/opt/sqlite
make
make install
```



## 自我认识

搭建环境，看似简单，但是由于不同的系统依赖的环境不一样，导致很多配置文件需要修改，也说明自己知识的匮乏，对linux命令还不够熟悉，并且对ruby的环境不够熟悉；也说明自己的进步空间很大，加油！！！

