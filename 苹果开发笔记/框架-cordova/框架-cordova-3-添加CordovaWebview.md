
#添加cordova-webview

## 1.把cordova文件移入到已有项目
- 1.已有项目Demo，用cordova create命令新建一个项目，添加ios平台，cordova  build


- 2.进入新项目的ios平台项目下,拷贝以下文件/文件夹到Demo项目

```
文件夹cordova
文件夹CordovaLib
文件夹platform_www
文件夹www（cordova默认自带网页文件夹）
文件config.xml（在B项目的文件目录下）
```

- 3.完成以下操作

```
将CordovaLib.xcodeproj添加到Demo工程中，选择Create groups
将www文件夹添加到Demo工程中，选择Create folder references
将config.xml文件添加到Demo工程中，选择Create groups
```
注：以上三个都不勾选copy items if need，config.xml的信息修改为Demo工程对应的信息
config.xml要放在最外层目录，如果放在工程目录内，cordova会提示该项目不是cordova 项目

- 4.other linker flags 添加-ObjC -all_load

- 5.Build Phases->Target Dependencies添加CordovaLib

- 6.Link Binary With Librarys添加下列库

```
libCordova.a
MobileCoreServices
AssetsLibrary
CoreLocation.framework
CoreGraphics.framework
```

- 7.Header Search Paths添加以下环境变量

```
"$(TARGET_BUILD_DIR)/usr/local/lib/include"        
"$(OBJROOT)/UninstalledProducts/include"
"$(OBJROOT)/UninstalledProducts/$(PLATFORM_NAME)/include"
"$(BUILT_PRODUCTS_DIR)”
```

- 8.在需要使用的地方，添加cordova webview

```
CDVViewController *viewController = [CDVViewController new];
viewController.view.frame = [UIScreen mainScreen].bounds;
[self.view addSubview:viewController.view];
self.viewController = viewController;//注意必须提升生命周期，否则会崩溃
```

## 2.用cocoapods给项目添加cordova
参考:http://www.jianshu.com/p/f47ac618ba44





# 注意事项

以默认网页调试为例，所有修改涉及的文件，可以从“通过cordova创建的新项目”里面拷贝过来，但注意要拷贝正确，以及做适当修改

修改以下文件
- 1.cordova_plugins.js - 添加插件相关数据，注意插件与插件之间要有逗号，不要有多余插件的代码
- 2.www -> plugins 下添加插件相关文件，注意插件.js文件里面的代码要被cordova.define包住
- 3.把插件.h .m文件拷贝到工程目录下，并且引用到项目中，修改这些文件的代码会直接生效
- 4.config.xml添加插件相关信息
- 5.完成，调试插件跟以往一样，如果正常，默认网页会显示网页已准备
