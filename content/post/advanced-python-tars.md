---
title: "[ 原创 ] Python开发进阶之浅析Tars"
date: 2016-05-30T20:00:00+08:00
tags: ["devops", "python", "tars"]
categories: ["python"]
comments: false
showMeta: false
showAction: false
---

已经转岗Python开发有一段时间了，对于现在团队的核心产品发布系统Tars的源码也读了一点，始终没有做出很好的总结，想来如今是时候了。这个系列将会介绍几个核心的亮点feature，并由此讲讲关于Python开发的一些个人观点。当然，代码都不是我写的，纯粹是学习`大牛之作的笔记总结`罢了。
在这第一篇里，鄙人将介绍一下关于Tars发布系统的一些设计和抽象。

<!--more-->

### 需求分析？

据鄙人所知道，发布系统的需求大概是：

* 装配好应用语言SDK及Web Server等；
* 应用的打包和配置；
* 路由或者服务发现策略的变更（一般即更新代码服务的拉入拉出）；
* Pull代码并安装(下载包、解压代码、配置等)到server上；
* 健康监测；
* 灰度和必要的容错等.

那么，以Ansible为例，可能据此实现发布系统的思路便是编写一个个的role，然后分别完成上述的需求。那么，仅仅这样就够了吗？我们只需要编写简单的调用Ansible的脚本编排一下任务的调用就能实现发布的需求了？

从某种意义上来说，也许是的，但如果你想将发布系统做的健壮和容错的话（主要原因即应用发布足够复杂），仅仅这样自然是不够的。

比如说，我们想针对xx应用点火时间设置为xx分钟，又或者我们想灵活控制发布时的一些参数，比如调用Ansible（或Saltstack）操作超时的配置等等。如果想要优雅地管控这些需求，那么抽象出来一些组件则显得尤为重要了。

以Tars为例，它的pipeline是这样的：

![tars-pipeline](/images/2016/May/tars-pipeline-1.png)

从最初机器的上线装配，到代码开发完毕，再到构建包->下载代码到机器->安装和配置及启动服务->健康监测和冒烟测试->拉入集群，整个流程主要以Tars为核心调度器，涉及与多个组件的交互。

### 状态机

从上面的pipeline中，我们不难发现，发布一个应用时的操作步骤可能会很多，并且每一个步骤都有可能面临出错的境遇（毕竟外部系统都是不可靠的@~@）。

对于这个问题，Tars给出的解决方案便是“将每个步骤抽象成一个个原子性的task”，然后利用状态机驱使发布过程。这样一来，每个操作都做成是一个状态性的Job（state job），而不是简单的命令操作（从命令式开发到声明\状态式开发本身就已经是大势所趋~），retry以及状态切换等特性的实现都不再是难事了！

#### django-fsm & celery task chain

那么怎么用Py实现这样的逻辑呢？

首先，关于状态机，Tars选择的是[django-fsm](https://github.com/kmmbvnr/django-fsm)这个类库，简单来说，该类库提供了一个transition的decorator，帮助实现django model层面的状态机，该decorator有以下几个参数：

* field：映射的状态字段；
* source：限制的源状态；
* target：将会跳转的目标状态；
* condition：限制条件；
* ...(其他参数可以通过上面的链接查看具体的官方文档)

这样的话，Tars便可以根据它的需求，编织出一张状态机切换图，然后依照不同的发布策略，抽象出不同的Mixin并可以灵活的编排起来，比如`_BrakeFSMixin`、`FortFSMixin`、`TargetFSMixin `、`BatchFSMixin`等等。

其次，光有状态机对于发布逻辑的状态控制还不够，我们还得有一个具体的执行器，实现对各个外部组件的调用与反馈，然后切换发布状态。针对这一块，Tars选择的是消费Celery的[task chain](http://docs.celeryproject.org/en/latest/userguide/canvas.html#chains)特性，这样便能做到将这些task做成一个连起来的chain，而且celery支持通过信号完成中断等功能，配合状态机即可实现一个完整的task pipeline。限于篇幅，鄙人这里便不再过多讲述细节，tars核心组件预计今年也将开源，欢迎关注。

### 结语

OK，第一篇文章就暂告一段落了，接下来的文章中，鄙人将就Tars产品的一些py开发技巧和造的一些轮子做一些简单介绍，敬请关注~