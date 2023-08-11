---
title: "Paper summmary of Mapreduce"
date: 2023-08-11T10:39:28+08:00
---

## 1. Abstract

MapReduce 是由google公司的研究人员开发的编程模型，其灵感来自于函数式语言中的map和reduce函数。

其主要思路是使用多个map函数将分片后的数据处理为一个中间产物，再由reduce函数将中间产物合并为最终的结果。

## 2. 编程模型

用户编写map和reduce函数，对于map函数，其使用string类型的key, value作为参数进行传递

伪代码如下所示

```shell
map(String key, String value):
    for each work w in value:
        EmitIntermediate(w, "1")

reduce(String key, Iterator values):
    int result = 0;
    for each v in values:
        result += ParseInt(v)
    Emit(AsString(result))
```


## 3. 实现
![mr](mr.png)

这篇论文中的实现环境是在google中通用的编程环境
- 2-4GB的x86机器
- 正常的商用网络(100GB/s)
- 一个集群中有上百甚至上千个机器
- 存储由廉价的磁盘提供
- 用户向调度系统提交任务，每个任务由一系列工具组成

下面是运行过程中的情况说明

- 首先在用户端将任务切分为16MB到64MB的大小，随后将程序拷贝到集群中的机器上
- 其中一份程序是特殊的，被称为是master，其他的被称为是workers，由master进行任务的分配
- 被指定映射任务的需要读取所分配的数据进行读取后再进行处理，并将其缓存到内存-
- 周期性的，缓存的对会被写入到本地的R个地址空间，同时将这些地址空间告知周围的workers
- 当一个工作者被master告知进行这些中间结果的存在后，将会对其进行读取并使用rpc读取远程的结果，并通过排序将相同的key放到一起
- reduce 工作者遍历所有排序好的中间数据，将数据传递给reduce函数进行最终的处理
- 处理完成后结束函数调用


### 3.1 异常处理

#### 3.1.1 工作者失败

master会周期性地ping各个工作者，如果在一个限定的时间内都没有返回，那么master将标记其为失败，同时由于该工作者失败，导致其上的数据也是不可以被获取到的

#### 3.2.2 master失败

当master失败时，如果在只有一个master的情况需要重新开始。


