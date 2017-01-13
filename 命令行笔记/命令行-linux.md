
# 命令

命令|参数|作用
:-|:-|:-
cat|filename|一次显示整个文件
|> filename|创建一个文件
|file1 file2 > file|将几个文件合并为一个文件
cd|~|返回到用户根目录
|..|返回到上一级目录
|~/.Trash|进入回收站
pwd||显示当前路径
mkdir|filename|创建文件夹
ls|-ah|显示全部隐藏文件
|-l|查看权限
ctrl+c||跳过当前输入的命令 重新输入 会终止当前进程
which brew||查看某个命令的安装路径
rm |-r 文件名| 删除文件
sudo|passwd root |设置root密码
|-i |进入root用户
exit||退出当前用户

# 编写与运行脚本
- 1.用vim写好脚本并保存为xx.sh
- 2.命令行下执行脚本 ./xx.sh
- 注：如果提示Permission denied没有权限，则运行命令chmod 777 xx.sh修改文件权限


# 其他
当前路径用./表示
