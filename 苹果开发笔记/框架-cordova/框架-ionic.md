

# 快速手册
命令|含义
:-|:-|
inoic serve |启动网络服务 用浏览器打开网页
ionic start MyIonic2Project tutorial --v2 |创建v2版本 带侧栏
ionic platform add ios |添加平台
ionic emulate ios |用模拟器运行
ionic info |查看相关组件及版本

# 杂
ionic 发请求没有请求头 httprequestwithappid
cordova filecache插件都是js做主体

更新ionic：先npm uninstall -g ionic 再npm install -g ionic
添加平台前先ionic serve一次 否则添加平台后可能没有页面
js写在./scr/index.html下，一般会自动build到./www/index.html，然后再build到platforms/平台/www/index.html，这样js才能生效。
如果js方法提示没定义，可能是没有自动build到./www/index.html
页面UI更改后，pc浏览器会自动刷新，不用重新ionic serve，但app不会，需要ionic build ios才会同步到app
