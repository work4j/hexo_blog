---
title: MQ的基本概念
date: 2018/6/12 10:00:00
tags:
- MQ
- RabbitMQ
- 中间件
---

## MQ的基本概念

1. **MQ概述**

   MQ全称 Message Queue（消息队列），是在消息的传输过程中保存消息的容器。多用于分布式系统直接进行通信。

   - MQ，消息队列，存储消息的中间件
   - 分布式系统通信两种方式：直接远程调用 和 借助第三方（MQ就是）完成间接通信
   - 发送方成为生产者，接收方称为消费者

2. **MQ的优势和劣势**

   优势：

   - 应用解耦（系统的耦合性越高，容错性就越低，可维护性就越低，**提高系统容错性和可维护性**）
   - 异步提速（**提升用户体验和系统吞吐量**，即单位时间内处理请求的数目）
   - 削峰填谷（可以**提高系统稳定性**）

   劣势：

   - 系统可用性降低
   - 系统复杂度提高
   - 一致性问题

   既然MQ有优势也有劣势，那么使用MQ需要满足什么条件呢？

   1. 