

# macOS

## mac键盘符号

![](http://o9ivu69va.bkt.clouddn.com/mac%E9%94%AE%E7%9B%98%E7%AC%A6%E5%8F%B7.png)


## 查看/隐藏 隐藏文件
$ defaults write com.apple.finder AppleShowAllFiles -bool true
$ defaults write com.apple.finder AppleShowAllFiles -bool false

## 查看mac版本
$ sw_vers

## 创建别名
vi ~/.bash_profile

alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

source ~/.bash_profile

## mac下ls命令文件类型用颜色区别
vi ~/.bash_profile
光标移动到最后添加alias ls='ls -hG'
source ~/.bash_profile



# iOS

ios10开始全部要求网络请求默认全部是https 如果网站是https网站 要安装证书才能访问
具体做法是 网站做一个页面供用户下载证书 然后用户先访问该页面 会自动提示安装证书
