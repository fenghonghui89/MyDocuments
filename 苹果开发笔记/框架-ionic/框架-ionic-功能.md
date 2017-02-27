
# facebook
ionic native - facebook
$ ionic plugin add 插件目录路径 --variable APP_ID="574935876028959" --variable APP_NAME="JiepengZhengDevExtend"
步骤：
在fb开发者中心创建项目
设置 - 添加ios平台 - bundleid - save
注意：
无需改config.xml


# twitter
ionic native - twitter
$ ionic plugin add 插件目录路径 --variable FABRIC_KEY=0f17f142ae9c150b548604e0bd966b712280f6b1
步骤：
在twitter开发者中心创建app - Keys and Access Tokens - 获取key和secret
在Fabric - twitter - 选择ios平台 - install - 输入key和secret - 在下面显示的代码获取FABRIC_KEY
注意：
要在项目的根config.xml插入key、secret，代码查看插件github说明，build会自动build到Staging下的config.xml
必须系统或者客户端登录了才能登录，否则提示401



# google plus + google 分析 + fcm推送

ionic native - google plus
$ ionic plugin add 插件目录路径 --variable REVERSED_CLIENT_ID=xxxx

ionic native - google analytics
$ ionic plugin add 插件目录路径

cordova插件 - cordova-plugin-fcm "FCMPlugin"
版本：2.1.1
是否收费：免费


步骤：
1.创建项目/选择已有项目
方式1.在add google service页面创建项目（输入app name / bundleid）
方式2.在GoogleAPIsConsole - 所有项目 创建项目（输入app name）
注意：
不能在firebase创建项目，因为无法配置google分析

2.开启登录和分析
在add google service 选择已创建项目的app name及对应的bundleid
勾选登录和分析功能
则在GoogleAPIsConsole - 项目 - 凭据，会自动生成API密钥、Oauth2.0客户端ID、Oauth同意屏幕

3.导入到firebase
在firebase创建项目页面导入google项目，进入firebase项目管理界面
在项目配置 - 您的应用 - ios应用 下载GoogleService-Info.plist

4.google plus
在GoogleService-Info.plist找REVERSED_CLIENT_ID，安装插件
无需改config.xml
安装插件后会在Resources创建xxx.entitlemetns，无需在意
注意：
REVERSED_CLIENT_ID必须跟类型为ios的Oauth2.0客户端ID一样，否则登录会提示400不允许xx类型登录，如果不一样可能是因为有多余的ID，删除多余的再下载GoogleService-Info.plist就好

5.google 分析
安装插件
在GoogleService-Info.plist找TRACKING_ID，代码初始化用

6.fcm推送
在firebase项目配置 - 云消息传递 - iOS 应用配置 上传推送证书
GoogleService-Info.plist文件放入cordova项目根目录，再安装插件
注意：
导出证书：钥匙串 - 登录 - 我的证书 - 对应bundleid的cer - 不要选择cer下的p12，而是直接选择cer导出

7.删除 查看
在firebase删除项目后，google dev那里的项目也会跟着被删除，但注意，谷歌项目管理页里 - 凭据 里面的的密钥和id是不会自动删除的
谷歌分析项目管理页 - 管理 - 媒体资源
媒体资源：相当于在这个开发者账号下创建的一个项目，对应一个bundleid，但删除项目后不会删除这个媒体资源。重新创建项目，开启分析服务时，可以重新选择这个媒体资源，TRACKING_ID不变。
删除媒体资源：谷歌分析管理页 - 管理 - 选择一个媒体资源 - 媒体资源设置

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
