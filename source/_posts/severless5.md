---
title: severless 无服务架构简析5 - Serverless业界发展与应用
date: 2017-01-08 00:45:01
categories: 架构
description: 无服务架构简析 Serverless业界发展与应用
tags:
- severless
- 无服务
- 无服务架构
- function

---

## 亚马逊AWS Lambda这种框架在2014年AWS re:Invent大会上宣布，它是如今市面上最早、最成熟、稳定的serverless框架之一。这项服务最初支持Node.js，现在支持Java和Python。十多项AWS服务与Lambda集成起来，而且名单只会越来越长。移动和物联网开发人员之所以喜欢Lambda，是由于它带来了强大功能和灵活性。它与Alexa Skills Kit紧密集成，成为在为Amazon Echo开发语音激发的应用程序的开发人员当中最受青睐的平台。亚马逊提供交互式控制台和命令行工具，以便上传和管理代码片段。## Microsoft Azure Functions

![Azure Functions](https://ww4.sinaimg.cn/large/006tNbRwgw1fbik7svz49j30yw0gcdjr.jpg)在2016年4月份举行的Build大会上，微软宣布了Azure Functions预览版，这是一个根据需求运行代码的服务。Azure Functions意味着微软已经进入日益流行的、由Amazon、 Google、IBM等主导的事件驱动无服务器计算领域。Azure Functions让开发人员可以发布基于外部触发执行的代码，而不用考虑准备计算或存储资源。这些函数——使用C#、JavaScript、Bash、F#、PHP、PowerShell或PHP编写——通常表现为短期异步任务。在一篇有关预览版发布的博文中，微软将“数据处理”作为发布这类服务的一个重要原因。## FaceBook ParseParse是一个完整的 iOS,android 后端支持平台，它可以让开发者完成忘掉服务器端的事情，包含了 schema free 的数据存储和云代码（CloudCode）。其数据存储服务涵盖了结构化的对象存储和非结构化的文件存储（也包括 CDN），并且，Parse 提供了完善的账户系统和数据访问控制，而且提供了强大的数据关联（一对一、一对多、多对多等）和查询能力。除此之外，由于定位于通用的后台服务，所以在标准化 API 之外，Parse 也提供了方法让开发者可以定制自己的商业逻辑。他们的做法是建立一个 node.js 容器，让开发者使用 javascript 这种广为人知的前端语言来完成数据整合、计算，再将结果返回给客户端。具体如下图所示：## Google Cloud Functions谷歌站在微服务模式的最前沿。除了有力推动Kubernetes外，这家公司还投资于AWS Lambda竞争对手：Cloud Functions，该架构可在其公共云基础设施上运行。不过Google Cloud Functions仍处于初期预览阶段，作为在谷歌计算引擎（Google Compute Engine）上运行的容器来托管。该平台只支持Node.js，不过预计在将来会添加更多的语言。只有几项服务与Cloud Functions进行了集成，比如Google Cloud Storage和Google Cloud Pub/Sub。考虑到谷歌API的覆盖面颇为广泛，该支持会支持另外多项服务，比如Gmail、Cloud Messaging、Maps及其他服务。## Iron.io虽然Iron.io从不以serverless computing平台的姿态示人，但是自2012年以来它就支持这种概念和框架。其中一些早期产品（比如IronQueue、IronWorker和IronCache）鼓励开发人员拿来代码后，即可在公共云中托管的Iron.io管理型平台中运行。最近，Iron.io拥抱Docker，并集成现有的服务，提供一种连贯完整的微服务平台。Iron.io的serverless computing平台其代号为Project Kratos，旨在将AWS Lambda引入到企业，又没有厂商锁定现象。Project Kratos可以在包括公共云和私有云在内的多个环境下，运行包装成Docker容器的现有AWS Lambda功能。## IBM OpenWhisIBM OpenWhisk在最近的InterConnect大会上宣布，这是一种可替代AWS Lambda的开源框架。除了支持Node.js外，OpenWhisk还可以运行用Swift编写的代码片段。该服务在将来可能会支持更多的语言。这种框架最出色的地方在于，开发人员可以将它安装在运行Ubuntu的本地机器上。Mac OS X和Windows开发人员可以使用Vagrant设备，将它安装并运行起来。该服务与IBM Bluemix即基于CloudFoundry的PaaS环境集成起来。除了可以调用Bluemix服务外，该框架还可与支持Webhook的任何第三方服务集成起来。开发人员可以使用CLI来管理OpenWhisk框架。      ## Serverless Framework虽然Serverless不是一种独立框架，但旨在简化开发和部署AWS Lambda应用程序的工作。这种开源框架最初名为JAWS，一亮相就引起了开发人员的关注。亚马逊邀请开发人员在上一届re:Invent大会上展示该框架。Serverless作为node.js NPM模块来提供，填补了AWS Lambda存在的许多缺口。它提供了多个样板模板，可以迅速启动AWS Lambda的开发。借助诸多插件，这种框架让用户很容易将AWS服务与其他第三方服务集成起来。## 系列总结

> 云已经并将继续是IT基础设施和软件开发中的重要游戏规则。软件开发人员需要考虑他们如何最大限度地利用云平台来获得竞争优势。
> Serverless架构是开发人员和组织思考，研究和采用的最新进展。随着开发人员接受AWS Lambda等计算服务，这将是一个令人兴奋的架构新转变。今天有无服务器应用程序，支持数千用户和执行复杂的操作，其中包括重要任务，如视频编码和数据处理等。在许多情况下，无服务器架构可以比传统模型实现更好的结果，并且实现起来更便宜，更快。
> 还需要降低与运行基础设施和开展传统软件系统相关的复杂性和成本。减少基础架构维护所需的成本和时间以及可扩展性的好处是组织和开发人员考虑无服务器架构的理由。在未来几年内，推送无服务器后端可能会加速。
> 在本系列中，我们了解了什么是无服务器架构，并与传统架构进行比较。我们研究了核心原则，并考虑了与这种架构相关的一些挑战。