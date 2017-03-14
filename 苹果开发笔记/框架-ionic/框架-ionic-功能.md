
# facebook
ionic native - Facebook

## 步骤
1.在fb开发者中心创建项目
2.设置 - 添加ios平台 - bundleid - save
3.安装插件：$ ionic plugin add 插件目录路径 --variable APP_ID="574935876028959" --variable APP_NAME="JiepengZhengDevExtend"

## 注意
无需改config.xml

账号：有账号
插件：有比较新的插件，插件支持分享与登录
ionic cloud登录支持：支持
分享集成：系统分享-有，有分享扩展能增强自带分享功能
分享范围：系统分享-能分享到我的时间线，好友，小组
分享内容：系统分享-message/subject不能通过传值获取要手动输入；url与图片只能选其一，多图不能用数组包含，同时含有图片和url时只发送url；


# twitter
ionic native - Twitter

## 步骤
1.在twitter开发者中心创建app - Keys and Access Tokens - 获取key和secret
2.在Fabric - twitter - 选择ios平台 - install - 输入key和secret - 在下面显示的代码获取FABRIC_KEY
3.安装插件：$ ionic plugin add 插件目录路径 --variable FABRIC_KEY=0f17f142ae9c150b548604e0bd966b712280f6b1

## 注意
要在项目的根config.xml插入key、secret，代码查看插件github说明，build会自动build到Staging下的config.xml
必须系统或者客户端登录了才能登录，否则提示401

账号：有账号
插件：未知
ionic cloud登录支持：支持
分享集成：系统分享-有
分享范围：系统分享-只有关注与被关注关系，只能分享到首页不能分享给指定朋友
分享内容：系统分享-只能发送一张图，且不能被数组包含

# google plus
ionic native - GooglePlus

## 步骤
1.创建项目/选择已有项目
方式1.在add google service页面创建项目（输入app name / bundleid）
方式2.在GoogleAPIsConsole - 所有项目 创建项目（输入app name）
注意：不能在firebase创建项目，因为无法配置google分析

2.开启登录和分析功能
在add google service 选择已创建项目的app name及对应的bundleid
勾选登录和分析功能
则在GoogleAPIsConsole - 项目 - 凭据，会自动生成API密钥、Oauth2.0客户端ID、Oauth同意屏幕

3.下载GoogleService-Info.plist

4.安装插件
在GoogleService-Info.plist找REVERSED_CLIENT_ID(很长的一串)
安装插件：$ ionic plugin add 插件目录路径 --variable REVERSED_CLIENT_ID=xxxx

## 注意
无需改config.xml
安装插件后会在Resources创建xxx.entitlemetns，无需在意
REVERSED_CLIENT_ID必须跟类型为ios的Oauth2.0客户端ID一样，否则登录会提示400不允许xx类型登录，如果不一样可能是因为有多余的ID，删除多余的再下载GoogleService-Info.plist就好

账号：有账号
插件：有比较新的插件，但插件只支持登录
ionic cloud登录支持：不支持
分享集成：系统分享-无，有分享扩展，但任何情况下返回后界面会卡死，需要下拉上拉系统界面或者home返回后才有可能恢复
分享范围：系统分享-只能关注收藏集，不能关注用户；可以分享到不同圈子，无法分享到某个用户
分享内容：系统分享-只分享url时会显示url对应页面，同时分享url与图片时url只会显示为链接，图片不能被数组包含


# google分析
ionic native - GoogleAnalytics

## 步骤
1.创建项目/选择已有项目，与集成google plus一样

2.开启登录和分析，与集成google plus一样

3.下载GoogleService-Info.plist，与集成google plus一样

4.安装插件
安装插件：$ ionic plugin add 插件目录路径
在GoogleService-Info.plist找TRACKING_ID，代码初始化用

## 删除，查看
谷歌分析项目管理页 - 管理 - 媒体资源
媒体资源：相当于在这个开发者账号下创建的一个项目，对应一个bundleid，但删除项目后不会删除这个媒体资源。重新创建项目，开启分析服务时，可以重新选择这个媒体资源，TRACKING_ID不变。
删除媒体资源：谷歌分析管理页 - 管理 - 选择一个媒体资源 - 媒体资源设置


# gcm推送(ionic native)
ionic native - Push

## 步骤
1.在GoogleAPIsConsole找到对应项目的项目编号（注意不是项目ID），安装插件和初始化时有用
2.根据插件github步骤安装，注意要先在根config.xml写入插件信息再安装，否则无法成功安装插件
```
<plugin name="phonegap-plugin-push" spec="1.10.0">
    <param name="SENDER_ID" value="695797427081" />
</plugin>
注意spec版本号
```
3.安装插件$ ionic plugin add phonegap-plugin-push --variable SENDER_ID=695797427081

## 注意
第一次运行如果不允许推送 以后运行的时候 初始化的对象也依然存在



# fcm推送
cordova插件 - cordova-plugin-fcm "FCMPlugin"
版本：2.1.1
是否收费：免费

## 步骤
1.创建项目/选择已有项目，与集成google plus一样

2.导入到firebase
在firebase创建项目页面导入google项目，进入firebase项目管理界面
在项目配置 - 您的应用 - ios应用 下载GoogleService-Info.plist

3.上传证书
在firebase项目配置 - 云消息传递 - iOS 应用配置 上传推送证书

4.安装插件
GoogleService-Info.plist文件放入cordova项目根目录，再安装插件

5.配置项目
xcode项目setting - capabilities 打开push开关


## 注意
导出证书：钥匙串 - 登录 - 我的证书 - 对应bundleid的cer - 不要选择cer下的p12，而是直接选择cer导出
订阅新主题 最长一天后主题生效
安装后要FCMPlugin.getToken一次才能用

## 删除
在firebase删除项目后，google dev那里的项目也会跟着被删除，但注意，谷歌项目管理页里 - 凭据 里面的的密钥和id是不会自动删除的





# vimeo
账号：只能用国外邮箱注册
插件：无
ionic cloud登录支持：不支持
分享集成：系统分享-自带
分享范围：系统分享-
分享内容：系统分享-

# instagram
账号：有账号
插件：有一年前插件
ionic cloud登录支持：支持
分享集成：系统分享-有，如果有安装客户端，当分享内容为一张图片时可出现在系统自带里面；或者通过url scheme打开客户端但无法传参
分享范围：系统分享-只有首页  
分享内容：系统分享-只能分享一张图,message只能放到UIPasteboard，提示用户在instagram客户端粘贴
分享sdk：无

# YouTube
账号：有账号，只能用gmail邮箱登录
插件：无ios插件
ionic cloud登录支持：不支持
分享集成：系统分享-如果分享的是视频，且有安装客户端，则会出现在系统分享列表，但不知为何会提示youtube不可用
分享范围：系统分享-
分享内容：系统分享-

# 分享
ionic native - SocialSharing
注意：
ionic native自带的分享插件.m要修改url编码代码，否则无法分享url

# 系统信息
ionic native - AppVersion
ionic native - Device

# 二维码 相册 拍照
ionic native - BarcodeScanner
ionic native - ImagePicker
ionic native - Camera
注意：
Camera插件依赖cordova-plugin-compat，如果无法安装可能是因为无法在线安装cordova-plugin-compat，那么手动安装即可

# 本地推送
ionic native - LocalNotifications,Notification

# 定位
ionic native - Geolocation,Geoposition,PositionError
ionic native - BackgroundGeolocation

# 网络监测
ionic native - Network

# 支付
ionic native - PayPal,PayPalConfiguration,PayPalPayment
注意：
PayPal插件依赖card.io.cordova.mobilesdk

# In App Browser
ionic native - ThemeableBrowser
注意：
图片是引用放入到xcode项目里的图片 要注意图片尺寸大小

ionic native - InAppBrowser
