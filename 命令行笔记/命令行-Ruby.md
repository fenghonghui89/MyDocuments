

# < rvm(ruby版本管理工具)>
更多命令可以查看官方github

## 安装rvm
```
curl命令下载安装 - \curl -sSL https://get.rvm.io | bash -s stable
安装后按照提示 - source /Users/hanyfeng/.rvm/scripts/rvm
```

## 卸载rvm
rvm implode

## 安装/卸载对应版本ruby
rvm install/uninstall 2.2.0

## 使用某版本ruby
rvm use 2.2.0
rvm use 2.2.0 --default





# < ruby运行环境 >

## 安装、更新ruby
可选，mac默认已经安装ruby，如需安装可通过Homebrew或者rvm安装
经过测试可以用homebrew安装更新ruby

## 卸载ruby
按照安装途径选择对应的卸载方式，都卸载了的话会恢复到系统自带的版本





# < gem >

## 更新gem
sudo gem update --system

## 安装gem上的包
$ sudo gem install cocoapods

## 更新gem上的包
$ sudo gem update cocoapods
The update command will update your gems to the latest version.
The update command does not remove the previous version. Use the cleanup command to remove old versions.

## 查看gem上某个包的信息
$ gem search -d cocoapods

## 卸载gem上的包
gem uninstall cocoapods

## 清除所有包旧版本，保留最新版本
gem cleanup

## 查看gem的环境
gem environment

## 查看gem资源
gem source

## gem添加或删除配置源
gem sources -a url
gem sources -r url

## 列出本地名字含d的包
gem list
