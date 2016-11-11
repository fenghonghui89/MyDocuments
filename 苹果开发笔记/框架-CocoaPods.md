
## 安装
1.$ sudo gem install cocoapods
npm上面没有cocoapods，因为cocoapods是基于ruby的
sudo gem install cocoapods --pre 安装测试版
```
执行完install命令半天没反应
这有可能是因为Ruby的默认源使用的是cocoapods.org，国内访问这个网址有时候会有问题，网上的一种解决方案是将远替换成淘宝的，替换方式如下：
$ gem sources --remove https://rubygems.org/
//等有反应之后再敲入以下命令
$ gem sources -a https://ruby.taobao.org/

要想验证是否替换成功了，可以执行：
$ gem sources -l

正常的输出是：
*** CURRENT SOURCES ***
https://ruby.taobao.org/
```
```
gem版本过老
gem是管理Ruby库和程序的标准包，如果它的版本过低也可能导致安装失败，解决方案自然是升级gem，执行下述命令即可：
$ sudo gem update --system
```

2.$ pod setup


## 更新
如果安装的时候使用了sudo，升级的时候一样需要使用该关键字，不然升级完了以后又会出现路径不匹配问题
$ sudo gem install cocoapods



## 使用
1.进入项目根目录，创建Podfile文件：touch Podfile

2.编辑Podfile
```
platform :ios
target ‘CocopodsTest’ do
pod 'Reachability',  '~> 3.0.0'
pod 'SBJson', '~> 4.0.0'

platform :ios, '7.0'
pod 'AFNetworking', '~> 2.0'
end
```

3.进入项目根目录，执行导入命令：
pod install - 会按照Podfile文件安装指定版本
pod update - 如果Podfile文件没有指定版本 会安装最新版本
pod install --verbose --no-repo-update
pod update --verbose --no-repo-update
