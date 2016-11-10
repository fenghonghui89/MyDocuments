

# 简介
收费方式有两种，一种是发布版本，20美金/一个月/每app，一种是企业级，要联系销售
发布版本比免费版本多分析功能，以及其他基础功能的按量收费
企业级有SLA、热修复，一小时团队会议，额外付费支持等


# 快速手册
命令|含义
:-|:-|
inoic serve |启动网络服务 用浏览器打开网页
ionic start MyIonic2Project tutorial --v2 |创建v2版本 带侧栏
ionic platform add ios |添加平台
ionic emulate ios |用模拟器运行
ionic info |查看相关组件及版本


# 杂
ionic 发请求没有请求头 httpRequestWithAppId
cordova filecache插件都是js做主体

更新ionic：先npm uninstall -g ionic 再npm install -g ionic

添加平台前先ionic serve一次，否则添加平台后可能没有页面，如果还是没有，就remove平台从新add平台

js写在./scr/index.html下，一般会自动build到./www/index.html，然后再build到platforms/平台/www/index.html，这样js才能生效。
如果js方法提示没定义，可能是没有自动build到./www/index.html，暂时可以把js文件放到www文件夹下，直接在./www/index.html调用
页面UI更改后，pc浏览器会自动刷新，不用重新ionic serve，但app不会，需要ionic build ios才会同步到app

在page.html调用page.ts的方法
```
pages.ts:
import { Component } from '@angular/core';
import { FacebookAuth, User } from '@ionic/cloud-angular';

@Component({
  templateUrl: 'hello-ionic.html'
})
export class HelloIonicPage {

  constructor(public facebookAuth: FacebookAuth, public user: User) {

  }

  login(){
    console.log('login..');
    this.facebookAuth.login().then();
  }

  logout(){
    console.log('logout');
    this.facebookAuth.logout();
  }

  myAlert(){
    const full_name = this.user.social.facebook.data.full_name;
    const uid = this.user.social.facebook.uid;
    alert("this is alert.."+full_name+" "+uid);
  }
}

page.html:
<p>
   <button ion-button color="primary" (click)="myAlert()">myAlert()</button>
 </p>
```

# 使用ionic cloud
1.项目下$ npm install @ionic/cloud-angular --save
2.项目下$ ionic io init，就会在ionic账号后台创建app，以及在ionic.config.json文件写入appid
3.在src/app/app.module.ts下加入如下代码：定义CloudSettings， 加入到CloudModule.forRoot()
```
import { CloudSettings, CloudModule } from '@ionic/cloud-angular';

const cloudSettings: CloudSettings = {
  'core': {
    'app_id': 'APP_ID'
  }
};

@NgModule({
  declarations: [ ... ],
  imports: [
    IonicModule.forRoot(MyApp),
    CloudModule.forRoot(cloudSettings)
  ],
  bootstrap: [IonicApp],
  entryComponents: [ ... ],
  providers: [ ... ]
})
export class AppModule {}
```

# 使用ionic cloud auth
http://docs.ionic.io/services/auth/ 点击平台跳转到对应平台的接入教程
facebook native auth 要先到cordova搜索下载facebook的plugin
In-App Browser则按照教程安装cordova-plugin-inappbrowser


# ionic native
ionic native自带的分享插件.m要修改url编码代码，否则无法分享url
