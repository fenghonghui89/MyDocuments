





# 创建自定义插件
```

1.创建插件
$ plugman create --name HelloPlugin --plugin_id cordova-plugin-helloPlugin --plugin_version 1.0 --path Desktop/ --variable Author=HanyFeng --variable description=HanyHelloPlugin
名称 id 版本号 生成路径 可选变量如作者或描述

2.cd到插件目录 添加平台
$ plugman platform add --platform_name ios

```




# 插件关键文件编写

插件文件架构：
```
UMSharePlugin
|-plugin.xml
|-scr
  |-ios
    |-放.m/.h
|-www
  |-放js

```

编写plugin.xml：
```
  <?xml version='1.0' encoding='utf-8'?>
  <plugin id="com.tpages.social" version="1" xmlns="http://apache.org/cordova/ns/plugins/1.0" xmlns:android="http://schemas.android.com/apk/res/android">
      <name>DGC_Social_Plugin</name>
      <AUTHOR>HanyFeng</AUTHOR>
      <DESCRIPTION>DGC 社会化插件</DESCRIPTION>
      <js-module name="DGCSocialPlugin" src="www/DGCSocialPlugin.js">
          <clobbers target="Tpages.SocialPlugin" />  /*html调用插件时的对象名*/
      </js-module>
      <platform name="ios">
          <config-file parent="/*" target="config.xml">
              <feature name="DGCSocialPlugin">
                  <param name="ios-package" value="DGCSocialPlugin" />
              </feature>
          </config-file>
          <source-file src="src/ios/DGCSocialPlugin.m" />
      </platform>
  </plugin>  
```

项目目录 - 指定平台 - cordova_plugins.js
```
{
        "id": "cordova-plugin-UMSharePlugin.UMSharePlugin",
        "file": "plugins/cordova-plugin-UMSharePlugin/www/UMSharePlugin.js",
        "pluginId": "cordova-plugin-UMSharePlugin",
        "clobbers": [
            "UMSharePlugin"
        ]
}
```
