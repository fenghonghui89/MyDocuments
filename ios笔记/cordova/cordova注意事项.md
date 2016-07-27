
# 注意事项

- 1.用cordova新建的项目，在默认的页面上添加按钮点击没反应？

```
<meta http-equiv="Content-Security-Policy" content="default-src 'self' data: gap: https://ssl.gstatic.com 'unsafe-eval'; style-src 'self' 'unsafe-inline'; media-src *”>
```
把这一句注释掉


- 2.如果项目是通过cordova命令创建的，则尽可能用自带的AppDelegate类和MainViewController类，否则有可能插件无法响应

- 3.MainViewController不要遵循UIWebView协议
