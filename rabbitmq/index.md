#### 交换机  Exchange

- ###### Default Exchange  没定义时队列默认以队列名称作为路由键绑定

- Direct Exchange 直接交换根据消息路由键将消息传送到队列，消息在消费者之间而不是在队列之间进行负载平衡

  ![exchange delivering messages to  queues based on routing key](https://www.rabbitmq.com/img/tutorials/intro/exchange-direct.png)

- Fanout Exchange 将消息路由到绑定到它的所有队列，并且忽略路由键，非常适合消息的广播路由

  ![exchange delivering messages to three queues](https://www.rabbitmq.com/img/tutorials/intro/exchange-fanout.png)

- Topic Exchange 主题交换类型通常用于实现各种发布/订阅模式变体。路由键可以带*或者#用于匹配

  ![img](https://upload-images.jianshu.io/upload_images/14474902-65d0ce58c08322a4.png?imageMogr2/auto-orient/strip|imageView2/2/w/424/format/webp)

- Headers Exchange 

#### 集群

- 通过配置文件加入集群
- 通过基于DNS的发现
- 手动使用rabbitmqctl
- 所有数据/状态都在所有节点之间复制，例如交换机，队列结构等，但是队列信息不复制
- 旧版本通过镜像队列进行复制，一般不会有全部的镜像队列有副本，故障转移时优先选最早加入集群的节点
- 新版本通过Quorum [ˈkwɔːrəm] 队列进行复制，基于[Raft 共识算法](https://raft.github.io/)实现持久的、复制的 FIFO 队列，都可配置复制因子，默认存在两份副本

#### 消息持久化、防止丢失

- 开启手动确认
- 交换机与队列设置为持久化的
- 防止重复消息，消费者做幂等处理

#### 高可用

- 队列设置成quorum类型
- RabbitMQ集群部署



