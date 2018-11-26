﻿# MQ-Q:[OS-Q消息组件](https://github.com/OS-Q/MQ-Q) 

MQ-Q用于

[![sites](OS-Q/OS-Q.png)](http://www.OS-Q.com)

#### 更多关于：[OS-Q](https://github.com/OS-Q/OS-Q) 可访问 www.OS-Q.com

---

# MQ

消息总线（Message Queue），后文称MQ，是一种跨进程的通信机制，用于上下游传递消息。

## 简介

在互联网架构中，MQ是一种非常常见的上下游“逻辑解耦+物理解耦”的消息通信服务。

使用了MQ之后，消息发送上游只需要依赖MQ，逻辑上和物理上都不用依赖其他服务。

---

#### MQ优点

* 处理高并发情况，变成异步处理

* 松耦合，对MQ的调用不依赖于任何其它应用，没有任何依赖或者时序要求。

* 在任何应用程序中以接近零的消耗，不需要任何其他依赖就可以链接的库，能运行在任何操作系统上，并能用任何编程语言开展。

---

#### MQ缺点

* 消息传递路径更长，消息时延增加

* 上位设备无法知道下位设备的执行结果

* 不丢不重难以同时保证消息，可靠性和重复性互为矛盾


---

## 项目组成


### [RabbitMQ](https://github.com/OS-Q/RabbitMQ) 

 RabbitMQ是一个在AMQP基础上完成的，可复用的企业消息系统，用erlang语言开发，遵循Mozilla Public License开源协议。选定为云端平台组件

#### 概念说明：

- Broker：简单来说就是消息队列服务器实体。
- Exchange：消息交换机，它指定消息按什么规则，路由到哪个队列。
- Queue：消息队列载体，每个消息都会被投入到一个或多个队列。
- Binding：绑定，它的作用就是把exchange和queue按照路由规则绑定起来。
- Routing Key：路由关键字，exchange根据这个关键字进行消息投递。
- vhost：虚拟主机，一个broker里可以开设多个vhost，用作不同用户的权限分离。
- producer：消息生产者，就是投递消息的程序。
- consumer：消息消费者，就是接受消息的程序。
- channel：消息通道，在客户端的每个连接里，可建立多个channel，每个channel代表一个会话任务。


---

### [ZeroMQ](https://github.com/OS-Q/ZeroMQ) 

ZeroMQ号称是“史上最快的消息队列”，基于c语言开发的，实时流处理sorm的task之间的通信就是用的zeroMQ。选定为边缘端平台组件

ZMQ(ZeroMQ简称)是一个简单好用的传输层，像框架一样的一个socket library，他使得Socket编程更加简单、简洁和性能更高。是一个消息处理队列库，可在多个线程、内核和主机盒之间弹性伸缩。

特点： 高到离谱的吞吐量、可自行开发持久化、支持数据量较小的持久化、不过只是保存到内存中。 
除了点对点 即：请求-应答模式 是一对一 、不可有消息丢失 、其他都没有对消息丢失做强烈的保证、 
官方给出的观点：我们希望消息的尽快送达、而不介意消息的丢失

zeromq的目标是成为网络协议栈的一部分、进而进军linux 内核 、所以与Rabbit Active 有着本质以及目标的区别

---

### client

目录包括不同平台的client代码，用于测试云端MQ环境是否正常

---

##  锻造最美之器

##  www.OS-Q.com     |    qitas@qitas.cn



## Mosquitto

Mosquitto is an open source implementation of a server for version 3.1 and
3.1.1 of the MQTT protocol. It also includes a C and C++ client library, and
the `mosquitto_pub` and `mosquitto_sub` utilities for publishing and
subscribing.

Then use `mosquitto_sub` to subscribe to a topic:

    mosquitto_sub -t 'test/topic' -v

And to publish a message:

    mosquitto_pub -t 'test/topic' -m 'hello world'
