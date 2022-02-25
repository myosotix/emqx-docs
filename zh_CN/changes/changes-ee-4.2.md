---
# 编写日期
date: 2020-02-07 17:15:26
# 作者 Github 名称
author: wivwiv
# 关键字
keywords:
# 描述
description:
# 分类
category: 
# 引用
ref:
---

# 版本发布

## 4.2.11 版本

*发布日期: 2022-03-TODO*

### 重要

我们在 4.2.11 中修复了 License 总连接数计算的 Bug，License 将正确地检查集群的总连接数，而非错误地仅检查每个节点上的连接数。

请计划升级的用户注意此变化可能导致的客户端达到 License 限制而无法连接的可能性。

### 增强

### 重要修复

### 次要修复

## 4.2.10 版本

*发布日期: 2022-01-13*

### 增强

- 更新规则引擎 Action 时不再会清空 Action 的统计指标
- 支持配置是否转发为 Payload 为空的保留消息，以适应仍在使用 MQTT v3.1 的用户，相关配置项为 `retainer.stop_publish_clear_msg`
- 优化内置访问控制文件模块的使用交互
- 将 `max_topic_levels` 配置项的默认值更改为 128，以前它没有限制（配置为 0），这可能是潜在的 DoS 威胁
- 改进了接收到 Proxy Protocol 报文但 `proxy_protocol` 配置项未开启时的错误日志内容

### 重要修复

- 修复规则引擎保存数据到 MySQL 时可能出现较高失败率的问题
- 修复 RocketMQ 异步写入时数据乱码问题
- 修复 RocketMQ 统计指标不准的问题
- 修复规则引擎 MongoDB 离线消息功能中 Max Returned Count 选项无法使用的问题
- 修复资源健康检查可能堵塞创建过程的问题

### 次要修复

- 修复代理订阅模块中的 Retain Handling 订阅选项无法配置为 2 的问题
- 修复使用会话创建时间筛选得到的客户端列表不准确的问题
- 修复 Dashboard 节点详情页中的 Erlang VM 内存计算错误的问题
- 移除已经失效的运行时可配置项，支持更多的运行时可配置项

## 4.2.9 版本

*发布日期: 2021-11-17*

### 增强

- 改进客户端踢除机制

### 重要修复

- 修复集群间调用可能导致客户端进程失去响应的问题
- 修复 Modules 多次启停后报错的问题
- 修复锁释放可能在某些情况下导致客户端进程崩溃的问题

### 次要修复

- 修复 MongoDB 资源不支持域名的问题
- 修复 MongoDB 认证模块的一些问题
- 修复包含 "\\" 字符的 Client ID 无法进行模糊搜索的问题
- 修复可变字节整数可能大于 4 字节的问题
- 修复可能重复添加相同 Module 的问题
- 修复 Dashboard 修改 Action 相关配置后，实际已生效，但前端未刷新显示的问题

## 4.2.8 版本

*发布日期: 2021-09-29*

- 修复 规则引擎 同步批量写入到 SQL Server 失败的问题
- 修复 规则引擎 无法创建 Oracle 资源的问题
- 修复 多语言协议解析 异常情况下无法停止的问题
- 修复 创建 LDAP Auth 认证模块失败的问题
- 修复 JT/T808 网关 解析位置上报中自定义字段无法解析的问题
- 修复 规则引擎 离线消息 在某些情况下接收后无法删除的问题
- 修复 规则引擎 关闭规则后资源无法释放的问题
- 增强 离线消息保存到 Redis 支持清除残留数据
- 修复客户端搜索时，输入错误的数据格式时，后端返回的错误码不清晰的问题
- 修复 MQTT-SN 客户端连接后，客户端的协议名称显示不正确的问题
- 修复有几率出现的客户端进程卡死，导致某些客户端无法连接的问题
- 修复 proxy-protocol 开启后客户端无法接入的问题。
- 修复 proxy-protocol 开启后客户端页面显示 Socket 类型不正确的问题
- 修复集群下，跨节点调用 exproto 的 ConnectionAdapter 内方法，报告 "Connection process is not alive" 的问题
- 修复了 Kafka 客户端在网络波动中导致僵死的 Bug
- Webhook 支持 Pipelining 开关，默认关闭
- 新增 acl.conf 对 ipaddrs 的支持
- 优化 exproto 客户端连接断开，大量无用日志的打印问题

## 4.2.7 版本

*发布日期: 2021-06-17*

- 修复 规则引擎 数据保存到 OpenTSDB 异常情况下无法写入的问题
- 修复 特殊情况下无法在 Dashboard 进行热配置问题
- 修复 MQTT-SN 协议 Clean Session 为 false 的客户端在恢复 session 时 topicid 丢失的问题
- 修复 MQTT-SN 在异常情况下客户端卡死问题
- 修复 规则引擎 数据转发到 WebServer SSL 配置无法生效的问题
- 修复 模块 Kafka 消费组 SSL 配置无法生效的问题
- 修复 规则引擎 编辑资源导致资源列表无法显示的问题
- 增强 导入 license 失败的异常处理

## 4.2.6 版本

*发布日期: 2021-04-29*

- 修复 特殊情况下模块停止后无法启动的问题
- 修复 告警列表时间格式问题
- 修复 MQTT-SN客户端异常下线Will message没有发送的问题
- 修复 MQTT-SN 客户端重连且cleansession=false情况下PUBLISH和REGACK的顺序错乱问题
- 修复 Dashboard 中部分显示错误的问题
- 更新 Log 默认输出在 File中

## 4.2.5 版本

*发布日期: 2021-03-10*

- 修复 Pulsar 消费组解析批量消息错误的问题
- 修复 MQTT 协议 异常情况下无法解析的问题
- 修复 Dashboard 订阅列表异常情况下显示错误的问题
- 修复 规则引擎 处理单进程的批量消息性能问题

## 4.2.4 版本

*发布日期: 2021-02-18*

- 新增 规则引擎 更新资源逻辑
- 新增 规则引擎 数据桥接到kafka支持配置缓存大小
- 修复 AUTH_HTTP 长连接在达到 Keepalive 超时时长或最大请求数时被断开导致请求丢失的情况
- 修复 WebHook SSL 证书配置问题
- 修复 AuthRedis 重连失败的问题
- 修复 创建kafka消费组时检查 MQTT Topic格式问题
- 优化 主题统计页面移动到模块管理页面中

## 4.2.3 版本

*发布日期: 2020-12-25*

- 新增 GT/T32960 协议接入
- 新增 规则引擎 SQL语句支持二进制数据操作函数
- 调整 规则引擎/模块 界面参数统一
- 优化 LWM2M接入流程
- 优化 WebHook 插件性能
- 修复 规则引擎 redis sentinel 模式创建资源失败

## 4.2.2 版本

*发布日期: 2020-12-10*

- 优化 AuthHttp 性能问题
- 新增 规则引擎 数据保存到 Oracle
- 新增 规则引擎 数据保存到 DolphinDB
- 新增 规则引擎 数据保存到 MS SQL server
- 增强 规则引擎 数据保存 支持 同步和异步方式
- 修复 规则引擎 动作异步模式计数不准的问题
- 新增 SSL 支持配置CA证书的 depth
- 修复 在热升级中的异常问题

## 4.2.1 版本

*发布日期: 2020-11-16*

- 新增 Dashboard 模块页面支持管理mqtt增强认证
- 新增 Dashboard 模块页面支持管理lwm2m客户端
- 新增 redis资源支持配置SSL参数
- 新增 auth_jwt支持JWKs
- 新增 订阅者TCP繁忙时触发告警消息
- 新增 规则引擎 数据桥接到kafka 支持ACK策略配置
- 优化 Dashboard监控页面
- 优化 emqx_exporto性能
- 优化 emqx_exhook性能
- 修复 dashboard中，编辑动作，动作类型不对
- 修复 规则引擎-资源错字
- 修复 集群情况下导入导出恢复失败问题
- 修复 规则引擎 MySQL资源无法使用域名问题
- 修复 数据桥接到kafka 出现message too large的问题

## 4.2.0 版本

*发布日期: 2020-10-13*

- 规则引擎 Mysql/MongoDB/Cassandra/PGsql 资源支持IPV6和SSL连接
- 规则引擎 "资源" 支持上传证书
- 规则引擎 "动作" 分组
- 修复 InfluxDB 不支持有下划线字符
- 支持更多的插件通过 Dashboard 模块进行配置和启动
- 支持更多的参数热配置
- 支持小版本号之间的热升级
- 移除emqx_auth_username和emqx_auth_clientid插件
- 重构emqx_auth_mnesia,兼容老版本emqx_auth_username和emqx_auth_clientid的数据导入
- emqx主配置文件拆分,并且支持 include 配置文件