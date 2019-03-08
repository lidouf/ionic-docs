# Ionic Native
Ionic Native是一个Cordova插件的管理套件，它使任何Ionic应用添加原生功能更为方便。

这些文档适用于使用>=4.0.0的Ionic框架版本的应用。对于老版的Ionic v3版本项目，[请参见这里](http://ionicframework.com/docs/v3/native/)。

Ionic Native在两个分发版中可以使用：社区版和企业版。

## 社区版
Ionic Native CE是一套开源的插件，由社区贡献者进行维护。
Ionic不负责维护，修正，提升，或者对这些插件功能提供任何担保。

## 企业版
对于那些需要专用的原生插件支持，修正，提升，或者需要实现指导的团队，可以选择Ionic Native EE。

<div class="native-ee-pricing">
  <div class="table-wrap">
    <table>
      <thead>
        <tr>
          <td>
            <span class="native-ee-pricing-table">Features</span>
          </td>
          <th>
            <div class="plan-wrap"> 
              <span class="native-ee-pricing-table">Community Edition</span>
              <div class="price">$0/mo </div>
            </div>
          </th>
          <th>
            <div class="plan-wrap">
              <span class="native-ee-pricing-table">Enterprise Edition</span>
              <div class="price" data-toggle="billing-team">
                Contact Us</div>
            </div>
          </th>
        </tr>
      </thead>
      <tbody>
        <tr class="stripe">
          <th>
            Maintainer
          </th>
          <td>OSS Community</td>
          <td>Ionic</td>
        </tr>
        <tr>
          <th>
            Regular Release Cycles & Updates
          </th>
          <td>No</td>
          <td><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M186.301 339.893L96 249.461l-32 30.507L186.301 402 448 140.506 416 110z"/></svg></td>
        </tr>
        <tr class="stripe">
          <th>
            Support SLA & Ticketing System
          </th>
          <td>No</td>
          <td><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M186.301 339.893L96 249.461l-32 30.507L186.301 402 448 140.506 416 110z"/></svg></td>
        </tr>
        <tr>
          <th>
            Advisory & Support
          </th>
          <td>No</td>
          <td><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M186.301 339.893L96 249.461l-32 30.507L186.301 402 448 140.506 416 110z"/></svg></td>
        </tr>
        <tr class="stripe">
          <th>
            Security & Bug fixes 
          </th>
          <td>OSS Community</td>
          <td><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M186.301 339.893L96 249.461l-32 30.507L186.301 402 448 140.506 416 110z"/></svg></td>
        </tr>
        <tr>
          <th>
            Implementation Guidance
          </th>
          <td>No</td>
          <td><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M186.301 339.893L96 249.461l-32 30.507L186.301 402 448 140.506 416 110z"/></svg></td>
        </tr>
        <tr class="stripe">
          <th>
            Guaranteed SLA
          </th>
          <td>No</td>
          <td><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M186.301 339.893L96 249.461l-32 30.507L186.301 402 448 140.506 416 110z"/></svg></td>
        </tr>
        <tr>
          <th>
            <a href="native/native-core">Native Core</a>
          </th>
          <td>No</td>
          <td><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M186.301 339.893L96 249.461l-32 30.507L186.301 402 448 140.506 416 110z"/></svg></td>
        </tr>
        <tr>
          <th></th>
          <td></td>
          <td><a class="btn"
                href="https://ionicframework.com/sales?product_of_interest=Ionic%20Enterprise%20Engine">Contact Us</a></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

## Usage
所有插件都有两个组件--原生代码(Cordova)和JavaScript代码。
Cordova插件同样同样以`Promise`或`Observable`进行封装，这样可以提供通用的插件接口。
下面以不同框架下使用相机插件进行举例。

## Angular
通过`@NgModule`引入插件，将它加入到Providers列表。对于Angular来说，引入路径必须以`/ngx`结尾。Angular的更改侦测会自动处理。

```typescript
// app.module.ts
import { Camera } from '@ionic-native/camera/ngx';

...

@NgModule({
  ...

  providers: [
    ...
    Camera
    ...
  ]
  ...
})
export class AppModule { }
```

当插件声明完成后，则可以象其它服务一样被引用以及注入：

```typescript
// camera.service.ts
import { Injectable } from '@angular/core';
import { Camera, CameraOptions } from '@ionic-native/camera/ngx';

@Injectable({
  providedIn: 'root'
})
export class PhotoService {
  constructor(private camera: Camera) { }

  takePicture() {
    const options: CameraOptions = {
      quality: 100,
      destinationType: this.camera.DestinationType.DATA_URL,
      encodingType: this.camera.EncodingType.JPEG,
      mediaType: this.camera.MediaType.PICTURE
    }
    
    this.camera.getPicture(options).then((imageData) => {
      // Do something with the new photo
      
    }, (err) => {
     // Handle error
     console.log("Camera issue: " + err);
    });
  }
}
```

## Vanilla JavaScript
Ionic Native同样可以用于vanilla JavaScript应用，它使用ES2015+和/或TypeScript。要使用任何插件，从合适的包里面使用静态方法引入class：

```js
import { Camera } from '@ionic-native/camera';

document.addEventListener('deviceready', () => {
  Camera.getPicture()
    .then(data => console.log('Took a picture!', data))
    .catch(e => console.log('Error occurred while taking a picture', e));
});
```