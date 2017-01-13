

# 注意事项
```
如果项目是通过cordova命令创建的，则尽可能用自带的AppDelegate类和MainViewController类，否则有可能插件无法响应

MainViewController不要遵循UIWebView协议

如果cordova默认项目运行后提示设备连接中，即显示灰色，可能是插件js代码问题，例如包多了一层

用safari的开发模式调试，提示错误：TypeError:xxx is not a function. 可能是网页调用的方法名写错了，例如wechatPay写成wechaPay
用safari的开发模式调试，提示错误：ReferenceError: Can't find variable: Tpage 可能是网页调用的对象名写错了，例如Tpages.aliPay写成Tpage.aliPay

如果项目接入cordova，但网页内容是放在服务器上面的，则无法触发插件，必须把网页内容放到项目内才有效
```




# 快速手册

## 插件

命令|含义
:-|:-|
cordova plugin list |查项目用到的插件
cordova plugin add 插件路径 |安装自定义插件
cordova plugin remove 插件id |移除插件
plugman create --name HelloPlugin --plugin_id cordova-plugin-helloPlugin --plugin_version 1.0 --path Desktop/ --variable Author=HanyFeng --variable description=HanyHelloPlugin |创建自定义插件（名称 id 版本号 生成路径 可选变量如作者或描述）

## 创建项目

命令|含义
:-|:-|
cordova create Desktop/cordova/hello com.example.hello “HelloWorld" |创建项目（生成路径 bundled 项目名称）
cordova platform add ios |给项目添加指定平台
cordova prepare # or "cordova build” |编译
cordova run ios --device |真机运行
cordova run ios --emulator --target=iPhone-5 |模拟器运行

## 通用

命令|含义
:-|:-|
cordova info |查看项目信息
