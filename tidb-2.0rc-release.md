---
title: TiDB 2.0 RC1 Release
author: ['PingCAP']
date: 2018-03-09
summary: 2018 年 3 月 9 日，TiDB 发布 2.0 RC1 版。该版本在上一版的基础上，对 MySQL 兼容性、系统稳定性和优化器做了很多改进。
tags: ['TiDB']
---

2018 年 3 月 9 日，TiDB 发布 2.0 RC1 版。该版本在上一版的基础上，对 MySQL 兼容性、系统稳定性和优化器做了很多改进。

## TiDB

+ 支持限制单条 SQL 语句使用内存的大小，减少程序 OOM 风险

+ 支持下推流式聚合算子到 TiKV

+ 支持配置文件的合法性检测

+ 支持 HTTP API 获取 TiDB 参数信息

+ Parser 兼容更多 MySQL 语法

+ 提升对 Navicat 的兼容性

+ 优化器提升，提取多个 OR 条件的公共表达式，选取更优执行计划

+ 优化器提升，在更多场景下将子查询转换成 Join 算子，选取更优查询计划

+ 使用 Batch 方式 Resolve Lock，提升垃圾回收速度

+ 修复 Boolean 类型的字段长度，提升兼容性

+ 优化 Add Index 操作，所有的读写操作采用低优先级，减小对在线业务的影响

## PD

+ 优化检查 Region 状态的代码逻辑，提升程序性能

+ 优化异常情况下日志信息输出，便于调试

+ 修复监控中关于 TiKV 节点磁盘空间不足情况的统计

+ 修复开启 TLS 时健康检查接口误报的问题

+ 修复同时添加副本数量可能超过配置阈值的问题，提升程序稳定性

## TiKV

+ 修复 PD leader 切换， gRPC call 没被 cancel 的问题

+ 对重要配置进行保护，第一次设置之后不允许变更

+ 增加获取 metrics 的 gRPC API

+ 启动时候，检查是否使用 SSD

+ 使用 ReadPool 优化读性能，raw get 测试性能提升 30%

+ 完善 metrics，优化 metrics 的使用

源码地址：[https://github.com/pingcap/tidb](https://github.com/pingcap/tidb)

**如今，在社区和 PingCAP 技术团队的共同努力下，TiDB 2.0 RC1 版已发布，在此感谢社区小伙伴们长久以来的参与和贡献。**



> 作为世界级开源的分布式关系型数据库，TiDB 灵感来自于 Google Spanner/F1，具备『分布式强一致性事务、在线弹性水平扩展、故障自恢复的高可用、跨数据中心多活』等核心特性。TiDB 于 2015 年 5 月在 GitHub 创建，同年 12 月发布 Alpha 版本，而后于 2016 年 6 月发布 Beta 版，12 月发布 RC1 版， 2017 年 3 月发布 RC2 版，6 月发布 RC3 版，8 月发布 RC4 版，10 月发版 TiDB 1.0，并在 2018 年 2 月发版 1.1 Beta。