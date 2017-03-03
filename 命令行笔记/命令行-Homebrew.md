

# < 常用配置流程 >

- 系统自带ruby，可先安装Homebrew
- 用Homebrew更新ruby，ruby自带gem
- 安装nvm，用nvm安装nodejs，nodejs自带npm
- 用npm安装其他需要用到的框架，因为大多数框架都是nodejs环境下的




# < homebrew(mac软件管理工具) >

## 安装homebrew
看官方教程

## 卸载homebrew
看官方github F&Q

## 更新homebrew（更新软件包的前提）
brew update

## brew doctor
可以查看相关Homebrew的错误及解决方法，例如brew update无法运行，brew下载node后无法使用等

## brew link node
例如，如果brew下载node后无法使用，可能是因为/usr/local没有创建对应的链接，用该命令可以修复

## 安装/卸载/更新软件
brew install/uninstall/upgrade ruby
注意安装的默认是最新版，如果要指定版本安装，自行搜索方法

## 查看brew安装的软件包
brew list

## 清理不需要的版本极其安装包缓存
brew cleanup

## 查看指定软件包的信息 包括版本/依赖
brew info node

## 搜索包 可以显示匹配的包 个别包有多个版本的话也会显示
brew search node 会显示node@4 node@5 node@6..

## 查看所有tap（homebrew专门存放某些库的地方）
brew tap

## 跳转到某个tap
brew tap homebrew/versions

## 列出某个tap下指定类型的库有哪些，例如node
brew install homebrew/versions/node

## 安装某个tap下某个库，例如node4-lts
brew install homebrew/versions/node4-lts


## 参考
https://zhuanlan.zhihu.com/p/22598799
http://blog.udock.cn/2017/01/05/%E6%9B%BF%E6%8D%A2Homebrew%E5%9B%BD%E5%86%85%E6%BA%90/ 更新源
默认的源
origin	https://github.com/Homebrew/brew (fetch)
origin	https://github.com/Homebrew/brew (push)

## 共用参数
--dry-run 只显示条目不进行操作
