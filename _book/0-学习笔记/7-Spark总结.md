# 关于检查点机制的实验

写 AFS 任务错误，关于Checkpoint 总结：
- 如果挂的时间没有很久，你又可以接受追数据的时间成本，那么可以什么都不改，直接重提任务；
- 如果挂的时间太久了，checkpoint中的offset过期了，那么删除checkpoint、删除 DIR 中的_spark_metadata，然后重提任务

写 bigpipe 的任务：
写ES， 写Palo，等等最好也是更换checkpoint
因为每次插入Palo对应一个唯一的label，lable相同的插入操作会被认为是同义词插入，数据只保留一份，咱们用的API生成label的规则是基于checkpoint的



# 业务总结

Push指标计算的意义：固定配额下，提高push的点击率，对高点击用户发更多的PUSH，拉高点击量。App调动起来的分类：push调起，运营调起，主动调起。


## 业务消息的组织架构
厂内的日志传输工具 Minos -> 消息队列pipe -> Spark / Flink -> other.

- 日志中台：先收集数据到磁盘，在转存到 消息队列
- 性能中台：获取 消息队列 中数据（最原始的数据），pipe中的数据保留时间是有限的，一般为几个小时到数天。
  - 转存到 AFS（原始数据转存）
  - park 处理完毕
    - Doris：小量级数据
    - ES：大量级数据



# 技术

## 实时计算的框架
关于数据准确性，各种框架如何保证的？
- 丢失：
- 重复：
- 数据准确性：Exactly-once（Flink, StructrueStreaming)、At-least-once、At-most-once


## Kafka
pipe：主题，一个业务对应一个pipe
pipelet：pipe中的独立数据管道，当pipe流量上涨时可以通过增加pipelet数来进行扩容。类似增加Partition数量。

- broker
  - 状态：是不需要状态的。Consumer自己保存自己的状态

- Consumer 
  - 广播和多播：广播是每个消费者都要收到，每个消费者都有一个消费者就OK。单播：对消费者划分不同的消费组就OK。

Producer消息路由：
Producer发送消息到broker时，会根据Paritition机制选择将其存储到哪一个Partition，相当于BigPipe中的 pipelet_number


## 日常追问的问题
那实时的点位，就是会有微微的延迟, 实时点位90分位值也就4秒钟左右
非实时的点位，也不会到60分钟，是这个意思是吗。90分位值3分多钟



## spark_shell 去乱码
--conf spark.driver.extraJavaOptions=" -Dfile.encoding=utf-8 " \
--conf spark.executor.extraJavaOptions=" -Dfile.encoding=utf-8 " \


