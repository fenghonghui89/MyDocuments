
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

# 各分区用途
/boot(200MB-500MB)存放启动Linux系统所必需的文件，包括内核文件、启动菜单配置文件等
/(根)
/home 存放所有普通系统用户的默认工作目录（宿主目录）
/var(variable) 存放系统中经常需要变化的一些文件（如系统日志文件、用户邮箱目录等）
/usr(UNIX Software Resource)(>2G)
/tmp 存放系统运行过程中使用的一些临时文件
/opt 第三方软件程序和工具
swap是交换文件系统（一般为物理内存的1.5到2倍，必须独立分区，物理内存大于8G可以不设这个交换分区）

/usr/X11 存放X window的目录
/usr/bin 众多的应用程序
/usr/sbin 超级用户的一些管理程序
/usr/doc linux文档
/usr/include linux下开发和编译应用程序所需要的头文件
/usr/lib 常用的动态链接库和软件包的配置文件
/usr/man 帮助文档
/usr/src 源代码，linux内核的源代码就放在/usr/src/linux里
/usr/local/bin 本地增加的命令
/usr/local/lib 本地增加的库

/bin 二进制可执行命令
/dev 设备特殊文件
/etc 系统管理和配置文件
/etc/rc.d 启动的配置文件和脚本


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
