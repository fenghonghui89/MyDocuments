
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
|-l [文件]|查看当前目录下所有文件或指定文件的权限/用户/组/目录等信息，具体看http://blog.csdn.net/jenminzhang/article/details/9816853
ctrl+c||跳过当前输入的命令 重新输入 会终止当前进程
which brew||查看某个包的安装路径
rm |-r 文件名| 删除文件
sudo|passwd root |设置root密码
|-i |进入root用户
exit||退出当前用户
chown|[选项]... [所有者][:[组]] 文件...|修改文件的所有者和组 例如chown hany:staff test.txt
|-c |显示更改的部分的信息
|-f |忽略错误信息
|-h |修复符号链接
|-R |处理指定目录以及其子目录下的所有文件
|-v |显示详细的处理信息
chmod|[选项]..[权限]文件...|修改文件权限 例如chmod 777 test.txt 选项同chown，具体看http://www.cnblogs.com/zdz8207/p/3793246.html
man|[命令]|查看某个命令的使用手册 例如man node

# 编写与运行脚本
- 1.用vim写好脚本并保存为xx.sh
- 2.命令行下执行脚本 ./xx.sh
- 注：如果提示Permission denied没有权限，则运行命令chmod 777 xx.sh修改文件权限


# 其他
当前路径用./表示

查看软件是不是sudo安装的？
which node 查看node安装目录，然后cd到该目录下运行ls -l查看用户

ls -l下wheel staff admin分组的区别
staff是所有用户的分组
wheel下的用户才有权限su成root用户
admin下的用户具有root权限

cat /etc/sudoers 查看分组权限 需要su
cat /etc/group 查看有什么分组 需要su
