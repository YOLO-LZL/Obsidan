---
title: 字节-商业平台-实习-Java三面
source: https://ls8sck0zrg.feishu.cn/wiki/wikcndm1Q1I2ZO3FA1jru5hcACb
created: 2026-05-23
source_updated: 2024-11-25
tags:
  - clippings
  - 面经
  - 字节
  - Java
---

# 字节-商业平台-实习-Java三面

> [!info]
> 来源：[飞书云文档](https://ls8sck0zrg.feishu.cn/wiki/wikcndm1Q1I2ZO3FA1jru5hcACb)
> 最近修改：2024-11-25
> 整理时间：2026-05-23
> 说明：已去除飞书侧边栏与评论区噪音，按 Markdown 做轻度整理。

## 整理摘要

这是一场字节跳动商业平台/广告投放方向的 Java 后端实习三面，时长约 70 分钟。面试内容主要分为四块：

1. 实习项目追问，重点围绕 RabbitMQ 的选型与顺序性保证。
2. Java 基础，重点围绕线程池设计、线程池状态流转、线程状态以及为什么需要线程池。
3. SQL 设计题，给定学生、老师、课程、学生选课四张表，要求查询老师一天课程安排和学生一周课程安排。
4. 算法题，两道题分别是“无重复字符的最长子串”和“滑动窗口的最大值”。

## 背景介绍

- 时长：70 分钟
- 面试公司：字节跳动
- 部门：商业平台 / 广告投放
- 岗位类型：实习招聘
- 第几面：三面
- 方向：后端开发
- 语言：Java
- 投递渠道：HR 转部门

## 问题记录

### 1）实习项目问题（7 分钟）

1. 为什么要采用 RabbitMQ 处理预警库存？
   回答：本项目 MQ 的 QPS 要求不高，没有采用其他 MQ 进行服务；再加上团队之前项目普遍采用 RabbitMQ，因此为了缩小学习成本，并没有采用其他 MQ 做对比。

2. RabbitMQ 怎么保证消息顺序性？
   回答：RabbitMQ 的队列天然保证顺序性。对顺序要求严格的同类消息，放到同一个队列中。

3. 如果同类消息数量过多，是都放在同一个队列中吗？
   回答：可以把消息放到多个队列中，类似 TCP 的机制，对消息进行编号。收到 500 编号的消息时，如果之前的消息还没收到，就先存到缓冲区，等前面的消息到达后再按顺序消费。

### 2）基础知识面试（10 分钟）

1. Java 的线程池怎么设计的？
   回答：会有一个 `list` 集合存放很多 `worker` 线程，这些 `worker` 会不断从阻塞队列中获取任务并执行。核心可以概括为：核心线程、阻塞队列、最大线程数、拒绝策略。

2. 为什么会有最大线程数的设置？
   回答：会有一些突发情况导致任务量变多，所以需要最大线程数来兜底。

3. 线程池的状态？
   回答：`running -> shutdown -> stop -> tining -> TERMINATED`

4. 线程池状态怎么流转？
   回答：
   - 变成 `shutdown`：执行 `shutdown()`
   - 变成 `stop`：执行 `shutdownNow()`
   - 变成 `tining`：所有任务已处理完
   - 变成 `TERMINATED`：线程池调度结束

5. 线程状态的流转？
   回答：
   - 新建状态（New）：线程对象被创建后
   - 阻塞状态（Blocked）：等待监视器锁
   - 等待状态（Waiting）：等待另外一个线程的特定操作
   - 超时等待（Timed Waiting）：等待特定的时间
   - 运行状态（Running）：线程获取 CPU 权限进行执行，需要注意线程只能从就绪状态进入运行状态
   - 死亡状态（Dead）：线程执行完毕或者因异常退出 `run()` 方法，生命周期结束

6. 为什么 Java 要设计线程池？
   回答：为了对线程进行统一管理、分配和销毁，更充分地利用资源。

### 3）SQL 设计题（35 分钟）

回答：具体设计过程忘了，设计题这部分“有点崩”。

原文补充了 4 张表：

- 学生表
- 老师表
- 课程表
- 学生选课表

使用这个数据库设计，可以查询老师一天的课程安排，以及学生一周的课程安排和上课时间地点。原文给出的 SQL 如下：

```sql
-- 查询老师一天的课程安排
SELECT c.name AS course_name, c.start_time, c.end_time, c.location
FROM course c
WHERE c.teacher_id = <teacher_id> AND DATE(c.start_time) = <date>;

-- 查询学生一周的课程安排及上课时间地点
SELECT c.name AS course_name, c.start_time, c.end_time, c.location
FROM course c
JOIN student_course sc ON c.id = sc.course_id
WHERE sc.student_id = <student_id>
  AND c.start_time >= <start_of_week>
  AND c.end_time <= <end_of_week>;
```

其中：

- `<teacher_id>` 表示老师 ID
- `<date>` 表示要查询的日期
- `<student_id>` 表示学生 ID
- `<start_of_week>` 和 `<end_of_week>` 分别表示一周的开始和结束时间

### 4）算法（18 分钟，两道）

- 无重复字符的最长子串
- 滑动窗口的最大值

回答：都写出来了。

## 备注

- 原文中线程池状态写作 `tining`，评论区有人补充应为 `tidying`。
- 原文包含评论区内容，这里未收录。
