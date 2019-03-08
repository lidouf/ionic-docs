---
previousText: '什么是Ionic框架'
previousUrl: '/docs/intro'
nextText: '浏览器支持'
nextUrl: '/docs/intro/browser-support'
---

# 核心概念

对于那些完全没有接触过Ionic应用开发的新手来说，对于它的核心哲学，概念以及项目所涉及的工具有一个高层级的理解是非常有用的。在冲入复杂的主题之前，我们先了解一下Ionic框架的基础是什么，以及它是如何工作的。


## UI组件

Ionic框架是一个UI组件库，它包括了可复用的元素，用于构建应用程序的代码块。Ionic组件基于[web标准](/docs/faq/glossary#web-standards)使用HTML, CSS和JavaScript进行构建。 虽然组件是预先构建的，但它们被设计成从集成到高度自定义，所以应用可以将组件做成他们自己的，允许每个应用都有自己独特的外观和感觉。更者，Ionic组件可以非常容易的将外观主题应用到整个应用。要获取更多关于自定义外观的信息，请参阅[主题](/docs/theming/basics)。


## 平台连续性

平台连续性是Ionic框架内置的一个特性，它允许应用使用同一套代码适用多个平台。每个Ionic组件会根据应用运行的平台自动适应所在平台的外观。例如，苹果设备，比方说iPhone和iPad，使用苹果自己的<a href="https://www.apple.com/ios" target="_blank">iOS设计语言</a>。同样的，安卓设备使用Google的设计语言<a href="https://material.io/guidelines/" target="_blank">材料设计</a>。

通过不同平台之间精细的设计更改，用户可以在应用上获得熟悉的用户体验。从苹果的App Store上下载的Ionic应用会使用iOS主题，而从安卓商店上下载的Ionic应用则会是对应的Material设计主题。对于浏览器里面运行的渐进式Web应用(PWA)，Ionic默认使用Material Design主题。另外，在特定场景下决定使用什么平台完全是可以配置的。关于平台连续性的相关信息可以在[主题](/docs/theming/basics)里面找到。


## 导航

传统的web应用使用线性历史，意味着用户在前进到一个页面后可以点击后台按钮退回到上一页。举个例来说，在Wikipedia上点击前进或者后退就是依赖于浏览器的线性历史堆栈。

作为对比，移动应用则经常使用并行，“非线性”导航。例如，标签卡界面中的每个标签则各自拥有独立的导航堆栈，这样确保用户在不同标签之间切换时永远不会丢失位置。

Ionic应用涵盖了这种移动导航模式，支持并行导航历史，并且能够嵌套，同时维护web开发者熟悉的浏览器样式的导航概念。 

对于使用Angular和`@ionic/angular`所构建的应用，我们推荐每个使用Ionic4 Angular应用使用随包发行的<a href="https://angular.io/guide/router" target="_blank">Angular路由</a>。
以前版本的的Ionic随包带有我们自己的自定义路由，但为了提供最好的工具和开发体验，我们已经将其从移除，转向推荐使用框架推荐的路由。


## 原生访问

使用web技术所构建的应用（比如Ionic应用）令人惊叹的一个特性就是可以在任意平台上虚拟运行：桌面计算机，手机，平板，汽车，冰箱，以及更多！Ionic应用使用的是同一套代码，能够运行在众多平台是因为它基于web标准和通用API，它们可以在这些平台上共享。

Ionic使用得最多的一个特性是构建一个应用可以同时在<a href="https://www.apple.com/ios/app-store/" target="_blank">App Store</a>和<a href="https://play.google.com/" target="_blank">Play Store</a>上进行下载。iOS和安卓SDK都提供了"[web views](/docs/building/webview)"，可以用来渲染Ionic应用，同时还允许<i>完整的</i>原生SDK访问。

类似<a href="https://capacitor.ionicframework.com/" target="_blank">Capacitor</a>和<a href="https://cordova.apache.org/" target="_blank">Cordova</a>的项目给了Ionic应用访问原生SDK的能力。这意味着开发者使用普通的web开发工具能够快速的构建应用，同时还能够访问原生的特性，比方说重力计，相机，GPS，等等。 

## 主题

Ionic框架在内核中使用<a href="https://developer.mozilla.org/en-US/docs/Web/CSS" target="_blank">CSS</a>，可以利用其提供的<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_variables" target="_blank">CSS属性（变量）</a>的灵活性。它使得我们只需要遵循web标准就可以非常容易的设计一个看起来不错的应用出来。我们提供了一套默认的配色，开发者直接使用就可以做出不错的效果来，但我们依然鼓励覆盖它们依据品牌、公司或想要的颜色模板来设计自己的配色方案。从应用程序的背景色到文字的颜色，所有的这一切都是可以自己定义的。更多关于应用主题的信息可以在[主题](/docs/theming/basics)找到。
