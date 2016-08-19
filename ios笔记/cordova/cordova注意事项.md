
# 注意事项

- 用cordova新建的项目，在默认的页面上添加按钮点击没反应？

```
<meta http-equiv="Content-Security-Policy" content="default-src 'self' data: gap: https://ssl.gstatic.com 'unsafe-eval'; style-src 'self' 'unsafe-inline'; media-src *”>
```
把这一句注释掉


- 如果项目是通过cordova命令创建的，则尽可能用自带的AppDelegate类和MainViewController类，否则有可能插件无法响应

- MainViewController不要遵循UIWebView协议

- 如果cordova默认项目运行后提示设备连接中，即显示灰色，可能是插件js代码问题，例如包多了一层
