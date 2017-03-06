


# < nvm - nodejs版本管理工具 >

## 安装
看官方git
注意安装完要重启终端 不然不会生效

## 更新
无需卸载，从新安装即可？

## 卸载
看官方git最后
to remove, delete, or uninstall nvm - just remove the `$NVM_DIR` folder (usually `~/.nvm`)






# < node.js运行环境 >

## 安装/更新
建议用nvm安装和管理
nvm ls-remote
nvm install 6.10.0

官网下载pkg安装包安装是root用户的 会影响其他包的使用 例如appium
homebrew可以安装最新版nodejs，但无法很好安装旧版本nodejs，也对nvm支持不好


## 卸载

nvm安装：
则用nvm卸载即可

官网下载包安装的卸载方法：
- 在/usr/local/lib中，删除所有node和node_modules的文件夹
- 在/usr/local/bin中, 删除所有node的可执行文件
- 在/usr/local/include， 删除所有node和node_modules的文件夹
- 检查~/中所有的local/lib/include文件夹, 删除里面所有node和node_modules
- 最后运行以下代码
```
sudo rm /usr/local/bin/npm
sudo rm /usr/local/share/man/man1/node.1
sudo rm /usr/local/lib/dtrace/node.d
sudo rm -rf ~/.npm
sudo rm -rf ~/.node-gyp
sudo rm /opt/local/bin/node
sudo rm /opt/local/include/node
sudo rm -rf /opt/local/lib/node_modules

http://www.zhihu.com/question/27389115/answer/36434788
```







# < npm - nodjs包管理工具 >

## 安装、卸载、更新npm
安装：安装nodejs则自带npm
卸载：卸载nodejs
更新：npm update npm

## 安装、卸载、更新包
npm install/uninstall/update xxx@3.10.1 -g/或其他参数
如果没有参数可能会提示找不到目录 npm自身更新也是用上面的命令

## 查看通过npm安装的包
npm list -g -depth 0

## 查看npm仓库上某个包的信息，可通过该方式知道npm上有没有这个包
npm view ios-sim

## 清除多余的npm包
npm prune

## 缓存清除
npm cache clean [-g]

## 查看/修改 npm配置
查看：npm config ls -l 全局则加-g
修改/获取/还原：npm config set/get/delete registry

## 添加registry
sudo npm set registry http://47.88.151.151:43437 -g
或者用nrm添加

## 安装nrm - npm registry 管理工具
npm install -g -nrm
http://cnodejs.org/topic/5326e78c434e04172c006826

## 其他
解决shasum check failed for错误
http://www.ithao123.cn/content-41081.html

## 常用npm包
cnpm
