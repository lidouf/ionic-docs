---
nextText: 'Core concepts'
nextUrl: '/docs/intro/concepts'
---

# 什么是Ionic框架？

<!-- TOC goes here -->

- 目标
- 协议
- Ionic命令行程序
- 框架兼容性
- Ionic框架V4+
- Ionic Appflow
- 生态系统

Ionic框架是一个开源的UI工具包，它使用web技术(HTML,CSS和JavaScript)来构建高性能和高质量的移动和桌面app。


Ionic框架聚焦于前端用户体验，以及UI互动（控制，互动，手势，动画）。它易于学习，并且能够与其它的库或框架很好的进行整合，比方说Angular，也能够脱离前端框架以脚本的方式独立使用。

目前，Ionic框架官方整合了<a href="https://angular.io/" target="_blank">Angular</a>，但同时也支持`Vue`和`React`进行开发。如果你想在扎入Ionic框架之前了解更多的信息，我们创建了一个<a href="https://youtu.be/p3AN3igqiRc" target="_blank">视频</a>帮助你了解相关的基础。


## 目标

### 跨平台

支持以先进的Web App方式构建和部署跨平台的app，例如原生iOS，Android，桌面，以及web本身－－所有这些基于一套代码。`Write once, run anywhere.`

### 基于Web标准

Ionic框架构建在可信赖的[标准化web技术](/docs/faq/glossary#web-standards)之上：HTML, CSS和JavaScript，使用现代的Web API，例如自定义元素(Custom Element)和影子DOM(Shadow Dom)。正是因为此，Ionic组件才拥有稳定的API，区别于普通的单平台组件的突发奇想。

### 漂亮的设计

干净，简单，功能强大。Ionic框架被设计成跨全平台工作，开箱即用，且界面美观。由预设计组件，原型代码段，交互范例，以及一个令人惊叹（还可扩展）的基本主题开始。

### 简洁

Ionic框架的设计思路就是简洁，所以创建Ionic应用是很享受的，易于学习，任何人只要有web开发相关的技能就可以入门。

## 协议

Ionic框架是一个免费开源项目，在<a href="https://opensource.org/licenses/MIT" target="_blank">MIT协议</a>许可下发布。这意味着它可以在个人和商业项目中自由使用。其它的一些流行项目如`jQuery`和`Ruby on Rails`同样也使用MIT协议。

本文档内容（可以在<a href="https://github.com/ionic-team/ionic-docs" target="_blank">ionic-docs仓库</a>中找到)则是使用[Apache 2协议](https://www.apache.org/licenses/LICENSE-2.0)。

## Ionic命令行程序

官方提供的[Ionic命令行程序](/docs/cli)，或者叫命令行接口，是一个快速构建Ionic应用的工具，它还给Ionic开发人员提供了数个非常有用的命令。除安装和更新Ionic之外，命令行程序还提供了一个内建的开发服务器，构建和开发工具，以及更多的东西。如果你是[Ionic Appflow](#ionic-appflow)会员，命令行程序还可以用于云端构建和部署，以及账号管理。


## 框架兼容性

Ionic过去的版本与Angular绑得较紧，V4版的框架进行了重构，它可以按独立的Web组件库进行运行，与其它最新的JavaScript框架，比方说Angular进行整合。Ionic可以成功用于其它多数的前端框架，包括React和Vue，虽然有些框架可能需要一些辅助手段才能实现完全的Web组件支持。

### JavaScript

Ionic 4最主要的一个目标就是摆脱对任意一种单一框架的硬性需求进行运行。这意味着核心组件可以在一个Web页面中以一个脚本标签的形式独立进行运行。虽然对于大的团队和项目使用框架会更好一些，但现在也能够在一些单页面甚至部分环境比方说WordPress中以库的形式独立使用Ionic框架。

### Angular

Angular一直以为都是让Ionic展现强大力量的中坚。虽然核心组件已经被重构为可以以独立Web组件库的形式运行，不过使用`@ionic/angular`包依然可以轻松的整合Angular生态系统。`@ionic/angular`包括了所有Angular开发者所期望在Ionic 2/3中能保留的功能，以及Angular所集成的核心库，例如Angular router。

### 未来支持

未来的版本将会支持其它的一些框架。官方当前的绑定可以支持Vue和React。虽然其中的一些组件只能运行某些框架。

## Ionic框架V4+

Ionic框架V4框架是一个主版本，项目对应的技术和兼容性主要聚焦在性能，兼容性以及全局的扩展能力。虽然V4版本依然通过`@ionic/angular`包与Angular进行深度的整合，但框架现在是相对独立的，也就意味着它可以与其它JavaScript框架(Vue, React, Preact等等)进行整合，或者完全独立运行。

因为遵循了Web标准，V4版本允许Ionic核心信赖于现代浏览器的标准组件模型，取代框架自身的模型。这样能够缩短加载时间，获得更好的性能，以及更少的编码。

## Ionic Appflow

为了帮助用户管理Ionic应用的整个生命周期，我们还提供了一个产品级别的商业app平台，称之为<a href="https://ionicframework.com/appflow" target="_blank">Ionic Appflow</a>，它是独立于开源框架之外的。

Ionic Appflow协助开发者及团队编译原生应用，构建和部署即时的代码更新至Ionic应用，通过一个集中后台实现。也可以选择可选的付费升级获得更多的高级特性，例如工作流的动画展示，单点登陆(SSO)访问连接的服务和整合。
 
Appflow需要一个<a href="https://dashboard.ionicframework.com/signup" target="_blank">Ionic账号</a>，伴随一个免费的“起步”计划给那些对此感兴趣的人。


## 生态系统

Ionic框架由一个全职的核心团队活跃开发和维护，其生态系统由一个开发者/贡献者国际社区主导，负责它的成长和接纳。开发者以及公司无论是小范围还是大规模应用Ionic，都可以构建和生成令人惊艳的应用运行于任何平台。

### 加入社区

有数百万的Ionic开发人员遍布于全球的200多个国家。下面一些途径可以加入：

* <a href="https://forum.ionicframework.com/" target="_blank">论坛:</a>提问以及分享想法的好地方。
* <a href="https://ionicworldwide.herokuapp.com/" target="_blank">Slack:</a>开发人员实时会议和聊天的地方。
* <a href="https://twitter.com/Ionicframework" target="_blank">Twitter:</a>我们发布更新以及从Ionic社区分享内容的地方。
* <a href="https://github.com/ionic-team/ionic" target="_blank">GitHub:</a>这里上报bug或请求新功能，创建问题。同时也欢迎公共联系。
* <a href="https://ionicframework.com/contributors" target="_blank">内容贡献:</a>撰写技术博客或分享你与社区的故事。

