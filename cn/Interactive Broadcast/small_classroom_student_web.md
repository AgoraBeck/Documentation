
---
title: 学生端实现
description: 
platform: Web
updatedAt: Tue Mar 10 2020 06:28:42 GMT+0800 (CST)
---
# 学生端实现
本文展示如何在 Web 平台实现学生端相关功能。

## 基础流程图

参考下图，在你的项目中实现学生端的登录登出功能。

![](https://web-cdn.agora.io/docs-files/1579595729792)

## 集成指引

根据下表链接，下载对应的 SDK，参考集成文档的步骤将 SDK 集成到你的项目中。


| 产品 | SDK 下载 | 集成文档 |
| ---------------- | ---------------- | ---------------- | 
| [RTC (Real-time Communication) SDK](https://docs.agora.io/cn/Interactive%20Broadcast/product_live?platform=All%20Platforms)      | [ Web 视频互动直播 SDK](https://docs.agora.io/cn/Interactive%20Broadcast/downloads)      | [实现互动直播](https://docs.agora.io/cn/Interactive%20Broadcast/start_live_web?platform=Web) |
| [RTM (Real-time Messaging) SDK](https://docs.agora.io/cn/Real-time-Messaging/product_rtm?platform=All%20Platforms) | [Web 实时消息 SDK](https://docs.agora.io/cn/Real-time-Messaging/downloads) | [收发点对点消息和频道消息](https://docs.agora.io/cn/Real-time-Messaging/messaging_web?platform=Web) |
| [白板](https://developer.netless.link/docs/javascript/overview/js-outline/) | [SDK 集成](https://developer.netless.link/docs/javascript/guide/js-sdk/) | [白板快速开始](https://developer.netless.link/docs/javascript/quick-start/js-precondition/) |


## 核心 API 时序图

参考下图时序，搭配使用 Native SDK 和 RTM SDK 在你的项目中实现基础的实时音视频和实时消息功能。

![](https://web-cdn.agora.io/docs-files/1581329701467)

## 核心 API 参考

- RTM SDK

| API | 实现功能 |
| ---------------- | ---------------- |
| [createInstance](https://docs.agora.io/cn/Real-time-Messaging/API%20Reference/RTM_web/modules/agorartm.html#createinstance)     | 创建并返回一个 RtmClient 实例。      |
| [login](https://docs.agora.io/cn/Real-time-Messaging/API%20Reference/RTM_web/classes/rtmclient.html#login) | 登录 Agora RTM 系统。登录后你可以使用 RTM 的核心业务逻辑。
| [createChannel](https://docs.agora.io/cn/Real-time-Messaging/API%20Reference/RTM_web/classes/rtmclient.html#createchannel) | 创建 Agora RTM 频道。一个 RtmClient 可以创建多个频道。 |
| [join](https://docs.agora.io/cn/Real-time-Messaging/API%20Reference/RTM_web/classes/rtmchannel.html#join) | 加入 Agora RTM 频道。|
| [getChannelAttributes](https://docs.agora.io/cn/Real-time-Messaging/API%20Reference/RTM_web/classes/rtmclient.html#getchannelattributes) | 获取指定频道的频道属性。 |
| [queryPeersOnlineStatus](https://docs.agora.io/cn/Real-time-Messaging/API%20Reference/RTM_web/classes/rtmclient.html#querypeersonlinestatus) | 查询指定用户的在线状态。 |
| [sendMessage](https://docs.agora.io/cn/Real-time-Messaging/API%20Reference/RTM_web/classes/rtmchannel.html#sendmessage)  | 发送频道消息。成功发送后，频道内所有用户都能收到。 |
| [leave](https://docs.agora.io/cn/Real-time-Messaging/API%20Reference/RTM_web/classes/rtmchannel.html#leave) | 离开 RTM 频道。 |

- Native SDK

| API | 实现功能 |
| ---------------- | ---------------- |
| [createClient](https://docs.agora.io/cn/Interactive%20Broadcast/API%20Reference/web/globals.html#createclient)        | 创建客户端。      |
[Client.init](https://docs.agora.io/cn/Interactive%20Broadcast/API%20Reference/web/interfaces/agorartc.client.html#init) | 初始化客户端对象。 |
| [Client.setClientRole](https://docs.agora.io/cn/Interactive%20Broadcast/API%20Reference/web/interfaces/agorartc.client.html#setclientrole) | 设置直播场景下的用户角色。本场景中，我们将学生的用户角色设为主播，可以与同为主播的老师进行互动。 |
[Client.join](https://docs.agora.io/cn/Interactive%20Broadcast/API%20Reference/web/interfaces/agorartc.client.html#join) | 加入 Agora RTC 频道。 |
| [Client.on](https://docs.agora.io/cn/Interactive%20Broadcast/API%20Reference/web/interfaces/agorartc.client.html#on)("stream-added") | 远端音视频已添加。 |
| [createStream](https://docs.agora.io/cn/Interactive%20Broadcast/API%20Reference/web/globals.html#createstream) | 创建并返回音视频流对象。 |
| [Stream.init](https://docs.agora.io/cn/Interactive%20Broadcast/API%20Reference/web/interfaces/agorartc.stream.html#init) | 初始化音视频对象。 |
| [Client.publish](https://docs.agora.io/cn/Interactive%20Broadcast/API%20Reference/web/interfaces/agorartc.client.html#publish) | 发布本地音视频流至 SD-RTN。 |
| [Client.subscribe](https://docs.agora.io/cn/Interactive%20Broadcast/API%20Reference/web/interfaces/agorartc.client.html#subscribe) | 订阅远端音视频流。|
| [Stream.play](https://docs.agora.io/cn/Interactive%20Broadcast/API%20Reference/web/interfaces/agorartc.stream.html#play) | 播放音、视频流。|
| [Client.leave](https://docs.agora.io/cn/Interactive%20Broadcast/API%20Reference/web/interfaces/agorartc.client.html#leave) | 离开 RTC 频道。 |

## 附加功能

除基础的实时音视频和实时消息功能外，你还可以参考下文，在项目中实现更多教育场景的附加功能。


<details>
<summary>网络质量监测</summary>
你可以通过使用 Native SDK 的 <code>on("network-quality")</code> 回调，实时监控通话中每个用户的网络上下行 last mile 网络质量。
更多质量透明相关方法，可参考如下文档：
<li><a href="https://docs.agora.io/cn/Interactive%20Broadcast/lastmile_quality_web?platform=Web">通话前网络质量探测</a></li>
<li><a href="https://docs.agora.io/cn/Interactive%20Broadcast/in-call_quality_web?platform=Web">通话中质量监测</a></li>
</details>
<details>
<summary>关闭本地音视频</summary>
你可以通过调用 Native SDK 的如下方法，实现相关功能：
	<li>调用 <code>muteAudio</code> 或 <code>unmuteAudio</code>关闭或重新开启本地音频。</li>
	<li>调用 <code>muteVideo</code> 或 <code>unmuteVideo</code> 关闭或重新开启本地视频。</li>
</details>

<details>
<summary>白板</summary>
参考下列常用功能文档，在你的项目中实现白板相关功能。
	<li><a href="https://developer.netless.link/docs/javascript/features/js-document/">文档转换</a></li>
	<li><a href="https://developer.netless.link/docs/javascript/features/js-state/">状态监听</a></li>
	<li><a href="https://developer-en.netless.link/docs/javascript/features/js-tools/">使用教具</a></li>
	<li><a href="https://developer-en.netless.link/docs/javascript/features/js-view/">视角操作</a></li>
	<li><a href="https://developer.netless.link/docs/javascript/features/js-operation/">白板操作</a></li>
	<li><a href="https://developer.netless.link/docs/javascript/features/js-scenes/">页面（场景）管理</a></li>
</details>


## 开源示例项目

我们也在 GitHub 上提供了互动直播大课的[开源示例项目](https://github.com/AgoraIO-Usecase/eEducation)，你也可以前往下载，或查看其中的源代码。
