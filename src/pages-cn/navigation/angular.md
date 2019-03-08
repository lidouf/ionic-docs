---
previousText: ''
previousUrl: ''
nextText: ''
nextUrl: ''
contributors:
  - mhartington
---

# Angular导航

本指南涵盖路由如何工作以及使用Ionic和Angular如何构建应用。


Angular路由是Angular应用程序中最重要的库。如果没有它，应用只能够是单视图/单页面的，当浏览器刷新的时候也不能维护它们的导航状态。
通过Angular路由，我们可以创建可链接的富应用，并且拥有丰富的动画（当然配套的要使用Ionic）。让我们先瞧瞧Angular的路由以及如何在Ionic应用中如何配置它。

## 简单路由

对于多数应用来说，经常需要某些类型的路由。最基础的配置看起来像这样：

```typescript

import { RouterModule } from '@angular/router';

@NgModule({
  imports: [
  ...
  RouterModule.forRoot([
    { path: '', component: LoginComponent },
    { path: 'detail', component: DetailComponent },
  ])
  ],
})
```

这里面最简单的细节就是查询path/component。当应用加载时，路由器通过读取用户想要加载的URL开始。在我们的示例中，路由器查询`''`，它实际就是我们的index路由。对于此，我们载`LoginComponent`。相当直接是不是。路径匹配组件的模式继续进行，直到路由配置里面的所有条目都进行完毕。但如果我们想在初始加载时加载不同的路径怎么搞？

## 处理重定向

对于上面的问题我们可以使用路由重定向。重定向与普通路由对象一样工作，但包括了一些不同的键。

```typescript
[
  { path: '', redirectTo: 'login', pathMatch: 'full' },
  { path: 'login', component: LoginComponent },
  { path: 'detail', component: DetailComponent }
];
```

在我们的重定向中，我们在应用中查找index路径。如果我们加载了它，我们重定向到`login`路由。最后一个键`pathMatch`是必需的，它告诉路由器以什么方式去查找路径。

因为我们使用的是`full`，它告诉路由器我们需要比较完整路径，即使是以类似`/route1/route2/route3`的方式结尾。假定我们有：

```typescript
{ path: '/route1/route2/route3', redirectTo: 'login', pathMatch: 'full' },
{ path: 'login', component: LoginComponent },
```

加载`/route1/route2/route3`就会重定向，但如果加载的是`/route1/route2/route4`，则不会重定向，因为路径并不完全匹配。

但是，如果我们有：

```typescript
{ path: '/route1/route2', redirectTo: 'login', pathMatch: 'prefix' },
{ path: 'login', component: LoginComponent },
```

然后载`/route1/route2/route3`和`/route1/route2/route4`，两个都会重定向，因为`pathMatch: 'prefix'`仅仅只是匹配路径的一部分。

## 导航到不同路径

说说路由还好，但它到底如何导航到指定的路由的？要了解些，我们可以使用`routerLink`指令，让我们回到最先的简单路由设置来说明：

```ts
RouterModule.forRoot([
  { path: '', component: LoginComponent },
  { path: 'detail', component: DetailComponent }
]);
```

在`LoginComponent`里面，我们使用下面的HTML导航到具体的路由。

```html
<ion-header>
  <ion-toolbar>
    <ion-title>Login</ion-title>
  </ion-toolbar>
</ion-header>

<ion-content padding>
  <ion-button [routerLink]="['/detail']">Go to detail</ion-button>
</ion-content>
```

这里最重要的部分是`ion-button`和`routerLink`指令。RouterLink运行起来与标准的`href`类似，但不需要象它一样使用字符串URL，它可以是一个数组，数组可以提供更多更复杂的路径。

我们也可以按程序的方式在应用中使用路由器API。

```typescript
import { Component } from '@angular/core';
import { Router } from '@angular/router';

@Component({
  ...
})
export class LoginComponent {

  constructor(private router: Router){}

  navigate(){
    this.router.navigate(['/detail'])
  }
}
```

两种方案提供相同的机制，根据场景选择使用。

> 相对URL导航说明：当前阶段，因为要支持多导航栈，相对URL某种程度上还不支持。

## 懒加载路由

当前我们路由设置方案是将它们全部包含在根模块下面的app.module，这并不完美。而路由器允许组件在它们自己的域中独立运行。


```typescript

import { RouterModule } from '@angular/router';

@NgModule({
  imports: [
  ...
  RouterModule.forRoot([
    { path: '', redirectTo: 'login', pathMatch: 'full' },
    { path: 'login', loadChildren: './login/login.module#LoginModule' },
    { path: 'detail', loadChildren: './detail/detail.module#DetailModule' }
  ])
  ],
})
```

同样类似，`loadChildren`属性提供了一种方案，它引用一个字符串取代直接使用模块。为了达成这个目的，因此我们需要为各自组件创建一个模块。


```typescript
...
import { RouterModule } from '@angular/router';
import { LoginComponent } from './login.component';

@NgModule({
  imports: [
  ...
  RouterModule.forChild([
    { path: '', component: LoginComponent },
  ])
  ],
})
```

> 我们将一些额外的内容略掉了，只保留了必要的部分。


这里我们有一个典型的Angular模块设置，伴随有一个RouterModule引用，但我们现在使用`forChild`，并且在设置中声明该组件。通过这个设置，当我们运行构建时，会为两个组件都生成独立的chunks，login组件和detail组件。

## 使用Tab

使用Tab，Angular路由器提供机制给Ionic使其可以知道应该加载哪个组件，但ionic对于tab组件实际上做了非常繁重的工作处理。让我们看个简单的例子。


```ts
const routes: Routes = [
  {
    path: 'tabs',
    component: TabsPage,
    children: [
      {
        path: 'tab1',
        children: [
          {
            path: '',
            loadChildren: '../tab1/tab1.module#Tab1PageModule'
          }
        ]
      },
      {
        path: '',
        redirectTo: '/tabs/tab1',
        pathMatch: 'full'
      }
    ]
  },
  {
    path: '',
    redirectTo: '/tabs/tab1',
    pathMatch: 'full'
  }
];
```

这里面我们有一个加载的"tabs"路径。在本例中，我们称之为"tabs"，但这个路径的名称是可以进行更改的。它可以叫做任何适合你应用的名字。在那个路由对象中，我们也可以定义一个子路由。在本例中，最顶层的子路由"tab1"即是我们的“总店”，它可以加载其它的子路由。对于本例来讲，我们只有一个子路由，它会象新组件一样被加载。该tab的页面代码如下：

```html

<ion-tabs>

  <ion-tab-bar slot="bottom">

    <ion-tab-button tab="tab1">
      <ion-icon name="flash"></ion-icon>
      <ion-label>Tab One</ion-label>
    </ion-tab-button>

  </ion-tab-bar>

</ion-tabs>
```

如果你以前使用过Ionic构建过应用，感觉应该很熟悉。我们创建一个`ion-tabs`组件，提供一个`ion-tab-bar`。`ion-tab-bar`提供一个`ion-tab-button`，它有一个`tab`属性关联到路由配置里面的tab"总店"上。注意最新版的`@ionic/angular`不再需要`<ion-tab>`，取而代之开发者可以完全自由的自定义tab工具栏，唯一的真相源在路由器的配置中。 





