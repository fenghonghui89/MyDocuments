


# 安装cordova
```
1.安装环境
安装ruby（默认系统自带一个版本） — 安装Homebrew — 用Homebrew安装node.js

2.安装调试工具 cordova
$ sudo npm install -g ios-sim
$ sudo npm install -g ios-deploy --unsafe-perm=true
$ npm install -g plugman
$ npm install -g cordova
附：https://github.com/phonegap/ios-deploy iOS-deploy安装教程
```


# 创建项目
```
1.创建项目
$ cordova create Desktop/cordova/hello com.example.hello “HelloWorld"
生成路径 bundled 项目名称

2.添加平台
$ cd hello
$ cordova platform add ios
```


# 编译 运行
```
编译
cordova build ios --device --debug/release --prod
* 编译后会在以下路径生成ipa:/Users/hanyfeng/Desktop/Ionic2DemoBase/platforms/ios/build/device/Ionic2Demo.ipa
* 如果编译dev报错，可能要在build setting选择dev team
* --prod 压缩main.js,提升启动速度
* 默认不带参数build模拟器版本

运行
真机：$ cordova run ios --device
模拟器：$ cordova run ios --emulator --target=iPhone-5
```


# 更新cordova 查看cordov版本及信息 更新平台
```
see The Command-Line Interface

Update your project to the latest version of Cordova:
$ cordova platform update [ios/android]
```
