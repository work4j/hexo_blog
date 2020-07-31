---
title: Java面试题汇总（四）Redis
date: 2019-03-13 11:43:51
tags:
- java
- 面试题
- 面试
- Redis
---

## [Java面试题汇总](/2019/03/13/java面试/Java面试题汇总/)（四）Redis

#### Redis和Memecache有什么区别？

Redis支持

#### 为什么Redis能这么快？

#### Redis的使用场景都有哪些？

1. 缓存
2. 计数器
3. 排行榜，去top n个数据
4. pub、sub发布订阅构建实时消息系统
5. 构建消息队列
6. 精确的设置过期时间
7. 各数据类型的应用场景：
   - String：缓存、限流、计数器、分布式锁、分布式Session
   - Hash：存储用户信息、用户主页访问量、组合查询
   - List：微博关注人时间轴列表、简单队列
   - Set：赞、踩、标签、好友关系
   - Zset：排行榜