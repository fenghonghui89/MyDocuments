

# 添加删除插件

```

用plugman安装插件 参数：平台 平台对应的项目路径 插件名称
$ plugman install --platform ios --project cordova/MyApp/platforms/ios/ --plugin cordova-plugin-device

用plugman删除插件 参数：平台 平台对应的项目路径 插件名称
$ plugman uninstall --platform ios --project Desktop/cordova/MyApp/platforms/ios/ --plugin cordova-plugin-dialogs


手动安装插件
必须cd到指定项目目录下，或者指定项目的指定平台下 该命令会添加插件到所有平台
$ cordova plugin add cordova-plugin-console cordova-plugin-device

手动删除插件
cordova plugin list查看插件id,然后cordova plugin remove 插件id（不是名称）

查看已添加插件
$ cordova plugin list
```
