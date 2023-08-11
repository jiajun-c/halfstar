---
title: "Kafka 入门"
date: 2023-08-09T20:42:19+08:00
---

# Kafka 安装

推荐从官网上下载kafka的压缩包进行解压。

将解压后的目录放入到/usr/local 下，随后设置PATH和kafka的环境变量

```shell
  /usr/local/apache-zookeeper-3.8.2-bin
$ls
bin  conf  docs  lib  LICENSE.txt  logs  NOTICE.txt  README.md  README_packaging.md
```

设置环境变量
```shell
export ZOOKEEPER_HOME=/usr/local/apache-zookeeper-3.5.6-bin
export PATH=$PATH:$ZOOKEEPER_HOME/bin:$ZOOKEEPER_HOME/conf
```

需要在conf下面添加一个zoo.cfg对zookeeper进行配置。

`zkServer.sh start `

![zookper](zookper.png)

