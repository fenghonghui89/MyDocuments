
# 介绍
Mou
作者罗晨，现在1.0已经要收费，但官网上还是有免费的0.8提供下载。可以导出html和pdf，cmd+r显示常用markdown语法很方便，用户体验不错。

MacDown
作者Tzu-ping Chung，跟Mou的作者就是否抄袭有个争论。开源markdown编辑器，到目前为止一直有更新
。可以导出html和pdf，用户体验也不错。

Atom
google的一个开源项目，类似Sublime Text，可以用多种语言开发，功能很强大。类似Sublime Text的插件管理功能，而且是绝大部分是图形化界面。Atom默认支持gfm，google对markdown的扩展，搭配几款markdown插件非常爽。目前我一般就是用Atom写markdown文档的。

Typora
朋友介绍的一款轻巧免费的markdown编辑器，它没有右边的预览界面，取而代之的是在编辑界面实时显示效果

# 快捷键

- cmd+r:显示目录树
- alt+shift+s:显示当前可用的snip
- cmd+shift+p:打开包选择器
- cmd+\:打开左侧目录树

# 常用插件

markdown-preview-opener 自动打开预览
markdown-scroll-sync 预览自动滚动
markdown-toc 方便给文章插入目录树（经常不响应）
markdown-writer 方便写作，例如快速插入图片
Pretty JSON 格式化json内容
docblockr 方便写注释
block-comment 注释语句 Ctrl + Alt + Cmd + /
atom-beautify
atom-ternjs
simplified-chinese-menu atom汉化菜单
language-markdown
angularjs



# snippet技巧

- 以下snip为gfm用，多个snip的起始水平位置要对齐，否则不生效
- alt+shift+s:显示当前可用的snip

```
'.source.gfm':


  'Unordered List':
    'prefix': 'ul'
    'body': """
- $1
- $2
- $3
    """

  'Ordered List':
    'prefix': 'ol'
    'body': """
1. $1
2. $2
3. $3
    """

    '五个空行':
      'prefix': 'br'
      'body': """
&ensp;
&ensp;
&ensp;
&ensp;
&ensp;
      """

  'example1':
    'prefix': 'myex1'
    'body': """
Hello, My name is ${1:name},<br\>
I am ${2:age}
    """

  'example2':
    'prefix': 'myex2'
    'body': """
  Hello, My name is ${1:name},\n
  I am ${2:age}
      """
```
