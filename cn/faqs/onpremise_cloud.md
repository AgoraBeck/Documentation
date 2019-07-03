
---
title: 本地服务端录制和云端录制有什么区别
description: 
platform: All Platforms,Linux
updatedAt: Mon Jul 01 2019 15:19:41 GMT+0800 (CST)
---
# 本地服务端录制和云端录制有什么区别
Agora 本地服务端录制 SDK 需要部署在 Linux 服务器上，Agora 云端录制无需部署 Linux 服务器，减轻了研发和运维的压力，更轻量便捷。下表列出这两种方案的区别：

|          | 本地服务端录制                       | 云端录制                                  |
| :------- | :----------------------------------- | :---------------------------------------- |
| 部署方式 | 私有化部署                           | Agora 公有云                              |
| 易用性   | 需要集成 SDK，需要部署 Linux 服务器  | 支持 RESTful API，不需要部署 Linux 服务器 |
| 运维     | 自行运维                             | 包含在云端录制服务中                      |
| 扩展性   | 在扩容时需要准备服务器资源并部署上线 | 实时扩容                                  |
| 可靠性   | 取决于你的开发能力                   | 文件自动上传，异常自动恢复                |