
<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [安装网上插件](#安装网上插件)
- [自定义插件并安装](#自定义插件并安装)

<!-- /TOC -->

# 安装网上插件

- 1.安装插件 参数：平台 平台对应的项目路径 插件名称

```
$ plugman install --platform ios --project cordova/MyApp/platforms/ios/ --plugin cordova-plugin-device
```
必须cd到指定项目目录下，或者指定项目的指定平台下 该命令会添加插件到所有平台
```
$ cordova plugin add cordova-plugin-console cordova-plugin-device
```

- 2.删除插件 参数：平台 平台对应的项目路径 插件名称

```
$ plugman uninstall --platform ios --project Desktop/cordova/MyApp/platforms/ios/ --plugin cordova-plugin-dialogs
```
当前路径用./表示


- 3.查看已添加插件

```
$ cordova plugin list
```


# 自定义插件并安装

- 1.创建插件

```
$ plugman create --name HelloPlugin --plugin_id cordova-plugin-helloPlugin --plugin_version 1.0 --path Desktop/ --variable Author=HanyFeng --variable description=HanyHelloPlugin
```
名称 id 版本号 生成路径 可选变量如作者或描述

- 2.cd到插件目录 添加平台

```
$ plugman platform add --platform_name ios
```

- 3.安装插件

```
$ cordova plugin add cordova-plugin-console cordova-plugin-device
$ cordova plugin add /Users/hanyfeng/Desktop/cordova/EchoPlugin
```
  - 必须cd到指定项目目录下，或者指定项目的指定平台下 该命令会添加插件到所有平台
  - 删除插件：cordova plugin list查看插件id,然后cordova plugin remove 插件id（不是名称）
