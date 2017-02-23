

# 创建项目
$ ionic start MyIonic2Project tutorial --v2
模板
tabs : a simple 3 tab layout 默认
sidemenu: a layout with a swipable menu on the side
blank: a bare starter with a single page
super: starter project with over 14 ready to use page designs
tutorial: a guided starter project


# 目录架构
./src/index.html
项目主入口，执行设置脚本和css以及自举，外部js文件在这里导入

src/app/app.module.ts
app的主入口
会为它设置各种参数，包括：app加载的第一个组件，bootstrap，声明有哪些页面

src/app/app.component.ts
app加载的第一个组件
它通常是一个空壳，而其他组件(例如页面)则被加载到它上面
会为它设置用哪个模板(src/app/app.html)


src/app/app.html
app.component.ts的模板，也是app的主要模板
