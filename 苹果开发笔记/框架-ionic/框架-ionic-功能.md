
# 第三方登录
ionic native - facebook
$ ionic plugin add /Users/hanyfeng/SourceTree/OSC_ThirdLibrary/CordovaPlugins/cordova-plugin-facebook4-master --variable APP_ID="574935876028959" --variable APP_NAME="JiepengZhengDevExtend"
步骤：
在fb开发者中心创建项目
设置 - 添加ios平台 - bundleid - save
注意：
无需改config.xml

ionic native - twitter
$ ionic plugin add /Users/hanyfeng/SourceTree/OSC_ThirdLibrary/CordovaPlugins/twitter-connect-plugin-master --variable FABRIC_KEY=0f17f142ae9c150b548604e0bd966b712280f6b1
步骤：
在twitter开发者中心创建app - setting - 获取key和secret
在Fabric - twitter - 选择ios平台 - install - 输入key和secret - 在下面显示的代码获取FABRIC_KEY
注意：
要在项目的根config.xml插入key、secret，代码查看插件github说明，build会自动build到Staging下的config.xml
必须系统或者客户端登录了才能登录，否则提示401


ionic native - google plus
$ ionic plugin add /Users/hanyfeng/Desktop/Foreign/cordova-plugin-googleplus-master --variable REVERSED_CLIENT_ID=com.googleusercontent.apps.248388499336-ujsi7snjevikn95iv0h209lnac4kcdue
步骤：
在firebase创建项目，添加ios平台
下载GoogleService-Info.plist，里面有REVERSED_CLIENT_ID
注意：
无需改config.xml
安装插件后会在Resources创建xxx.entitlemetns，无需在意
或者按照google analytics的做法创建项目后下载GoogleService-Info.plist，里面有REVERSED_CLIENT_ID；如果之后导入到firebase，在fb删除项目后，google dev那里的项目也会跟着被删除

# 分析
ionic native - google analytics
$ ionic plugin add /Users/hanyfeng/Desktop/Foreign/google-analytics-plugin-master
步骤：
google developer - 所有产品 - 分析 - google analytics - 选择平台 - 移动应用 - ios - 获取infoplist - 创建项目，勾选登录和分析，生成
导入到firebase平台，为fcm推送做准备，并下载GoogleService-Info.plist文件，里面有TRACKING_ID，初始化时使用
注意：
查看已创建项目信息：按照上面的步骤进入创建项目页面，下拉选择已创建项目和和bundleid，下一步，就会看到项目信息
控制台：谷歌搜索“google analytics 媒体资源”
媒体资源：相当于在这个开发者账号下创建的一个项目，但删除项目后不会删除这个媒体资源。重新创建项目，开启分析服务时，可以重新选择这个媒体资源，TRACKING_ID不变。

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

# 远程推送
cordova插件 - cordova-plugin-fcm "FCMPlugin"
版本：2.1.1
是否收费：免费
步骤：
GoogleService-Info.plist文件放入cordova项目根目录，再安装插件
证书制作参考官方文档(文档 - 开发 - 云消息推送)，注意最后导出时不要选择cer下的p12，而是直接选择cer导出
上传证书到firebase控制台
