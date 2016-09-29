

# 命令

commit:HEAD^ / HEAD~1 / 上一个版本号

## 查看
命令|参数|作用
:-|:-|:-
git branch|无参数|查看当前分支
|(branchName)|创建分支
|-a|同时显示远程分支
|-r|只显示远程分支
|-d|删除分支
git log|无参数|查看所有提交
|--pretty=oneline|只显示版本号和说明
|--graph|查看分支合并图
|--abbrev-commit|只显示短字符串的版本号
git status|无参数|查看状态
git diff|无参数|查看当前分支当前修改的内容
|(commit) -- (file)|查看当前分支指定版本指定文件的修改
git reflog|无参数|查看过往的每一次操作（提交、回滚等），可以查看到版本号

命令|参数|作用
:-|:-|:-
git push|-f| 强制提交
git init|无参数|把某个目录变成git可管理的仓库
git commit|-m "xxx"|写说明并提交更改
git add|(filename)|添加工作区改动到暂存区
git rm|(filename)|删除文件并提交到暂存区
git reset| --hard (commit) |当前分支回退到某个版本
|HEAD (file)|丢弃暂存区修改
git checkout|-- (file)|丢弃工作区修改
|-b (branchName)|创建并切换到指定分支
|(branchName)|切换到指定分支
git remote|add origin (ssh url/https url)|与远端仓库关联 origin可自定义
git remote|rm origin|解除与远端仓库的关联
git clone|(ssh url/https url)|克隆远端仓库到本地
git merge|(branchName)|合并指定分支到当前分支
