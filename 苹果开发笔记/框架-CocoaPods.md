
## 安装cocoapods
1.$ sudo gem install cocoapods
npm上面没有cocoapods，因为cocoapods是基于ruby的
sudo gem install cocoapods --pre 安装测试版
```
执行完install命令半天没反应
这有可能是因为Ruby的默认源使用的是cocoapods.org，国内访问这个网址有时候会有问题
网上的一种解决方案是将远替换成淘宝的，替换方式如下：
$ gem sources --remove https://rubygems.org/
//等有反应之后再敲入以下命令
$ gem sources -a https://ruby.taobao.org/

要想验证是否替换成功了，可以执行$ gem sources -l查看

gem是管理Ruby库和程序的标准包，如果它的版本过低也可能导致安装失败，解决方案自然是升级gem
```

2.$ pod setup



## 更新cocoapods
如果安装的时候使用了sudo，升级的时候一样需要使用该关键字，不然升级完了以后又会出现路径不匹配问题
$ sudo gem install cocoapods


## 设置cocoapods使用的仓库
查看cocoapod使用的仓库，默认是https://github.com/CocoaPods/Specs.git
pod repo

如果嫌速度慢，可以移除默认的仓库，添加新的速度更快的库
pod repo remove master
pod repo add master http://git.oschina.net/akuandev/Specs.git

更新设置
pod repo update


## 使用cocoapods管理项目
1.进入项目根目录，创建Podfile文件：touch Podfile，或者用pod init命令自动创建

2.编辑Podfile
```
platform :ios
target 'CocopodsTest' do
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
--verbose:显示更多debug信息
--no-repo-update:不升级cocoapods的Specs库，提升速度



## 其他
移除cocoapods对项目的管理，即还原项目
pod deintegrate

查看某个库在cocoapods中的信息
pod search Cordova

查看运行环境及项目信息，会显示Podfile
pod env


如果你在安装一个第三方库之前，想要先试用一下，就可以使用try命令。只需要在try的后面加上你想试用的第三方的名称即可
pod try AFNetworking

安装过程中，CocoPods会使用递归来分析所有的需求，并且建立一个代码相关性的图，最后将Podfile序列化为Podfile.lock
比如，如果两个库都需要使用AFNetworking，CocoaPods会确定一个同时能被这两库使用的版本，然后将同一个安装版本链接到两个不同的库中。
