

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [svn](#svn)
		- [常见问题](#常见问题)
- [git](#git)
	- [启用git](#启用git)
	- [查看记录](#查看记录)
	- [提交修改到暂存区](#提交修改到暂存区)
	- [提交暂存区所有修改到本地当前分支](#提交暂存区所有修改到本地当前分支)
	- [推送提交](#推送提交)
	- [恢复](#恢复)
	- [分支操作](#分支操作)
	- [仓库关联](#仓库关联)
	- [常见问题](#常见问题)
		- [处于new版本 - 选择过去的某个a版本](#处于new版本-选择过去的某个a版本)
		- [删除远程仓库的某些/某个版本](#删除远程仓库的某些某个版本)
		- [忽略文件，使文件不被git管理](#忽略文件使文件不被git管理)
		- [git知识点](#git知识点)

<!-- /TOC -->


# svn
### 常见问题
- svn冲突 提示xxx.xcodeproj无法解析 把== <<< 等地方删除 然后显示包文件 把mine/r111/r....删除
- 要在project所在文件夹创建对应文件夹，才能在项目中创建文件夹
- 如果提示文件冲突无法上传，找到冲突的地方，打开文件夹，会有几个.mine .rxxx .rxxx文件 删除就可以了
http://blog.csdn.net/huanghuanghbc/article/details/8559968





# git

## 启用git
命令|作用
:-|:-
git init|把某个目录变成git可管理的仓库

## 自定义git
git config --global color.ui true|git输出日志时显示颜色
git check-ignore -v Firebase.h|检查针对某个文件的.gitignore规则是否有错

## 配置别名

git config [-global] alias.xxx '要代替的内容'
注：-global 全局配置 不写则默认针对当前仓库有效
例子：
$ git config alias.br branch
git br -a 相当于git branch - a

每个仓库的Git配置文件都放在.git/config文件中，别名就在[alias]后面，要删除别名，直接把对应的行删掉即可；而当前用户的Git配置文件放在用户主目录下的一个隐藏文件.gitconfig中

git config alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"|






## 查看记录
命令|作用
:-|:-
git remote show origin|查看远程分支相关信息
git log|查看所有提交
git log --pretty=oneline|只显示版本号和说明
git log --graph|查看分支合并图
git log --abbrev-commit|版本号显示为短字符串的版本号
git log --pretty=oneline --graph --abbrev-commit|短版本号+说明+分支合并图
git status|查看状态，例如显示有文件新增、删除或者待提交，并提示推荐操作
git diff|查看当前分支当前修改的内容
git diff (commit) -- (file)|查看当前分支指定版本指定文件的修改
git reflog|查看过往的每一次操作（提交、回滚等），可以查看到版本号

## 提交修改到暂存区
命令|作用
:-|:-
git add xxx.txt|把工作区中指定文件的修改（增删改）提交到暂存区

## 提交暂存区所有修改到本地当前分支
git commit -m "xxx"|撰写说明，提交暂存区中所有修改到本地当前分支
git rm xxx.txt|删除文件并提交修改到暂存区。该文件只能是已加入到git里面，且未经修改和暂存的。
git rm -f xxx.txt|强制删除文件并提交修改到暂存区。该文件为已加入到git里面，且已经被修改或暂存的。


## 将本地分支的更新，推送到远程主机
```
格式：git push <远程主机名> <本地分支名>:<远程分支名>

```
命令（origin:主机名，dev:分支名）|作用
:-|:-
git push|如果当前分支只有一个追踪分支，那么主机名、本地分支名、远程分支名都可以省略
git push origin dev|省略远程分支名，将本地的master分支推送到origin主机的master分支,如果后者不存在，则会被新建
git push origin :dev|如果省略本地分支名，则表示删除指定的远程分支，因为这等同于推送一个空的本地分支到远程分支
git push origin --delete dev|等同于上面
git push origin|如果当前分支与远程分支之间存在追踪关系，则本地分支和远程分支都可以省略。该命令表示，将当前分支推送到origin主机的对应分支
git push --all origin| 不管是否存在对应的远程分支，将本地的所有分支都推送到远程主机，如果没有对应的远程分支则会自动创建
git push --force| 强制推送 应该尽量避免使用
git push -u origin dev|如果当前分支与多个主机存在追踪关系，则可以使用-u选项指定一个默认主机，这样后面就可以不加任何参数使用git push
git push origin --tags|git push不会推送标签(tag)，除非使用–tags选项


## 取回远程主机某个分支的更新，再与本地的指定分支合并
```
格式：git pull <远程主机名> <远程分支名>:<本地分支名>
```
命令（origin:主机名，next:远程分支名）|作用
:-|:-
git pull origin next:master|取回origin主机的next分支，与本地的master分支合并
git pull origin next|取回origin/next分支，再与当前分支合并
git pull origin|本地的当前分支自动与对应的origin主机”追踪分支”(remote-tracking branch)进行合并
git pull|当前分支自动与唯一一个追踪分支进行合并
git pull --rebase <远程主机名> <远程分支名>:<本地分支名>|如果合并需要采用rebase模式，可以使用–rebase选项



## 恢复
HEAD（最新版本） / HEAD^（上一个版本） / HEAD~1（上一个版本） / c86d14（某个版本号）

工作区有改动 未提交到暂存区
rm xxx.txt|当工作区有新增文件时可用，删除文件（即丢弃工作区修改）。因为文件未加入到git所以没有修改提交到暂存区。
git checkout -- xxx.txt|当工作区的某文件被修改或者被删除时可用，丢弃工作区修改。其实是用版本库里的版本替换工作区的版本。

提交到暂存区，未提交到本地分支
git reset xxx.txt|丢弃暂存区中指定文件的修改，工作区的修改不变

提交到本地分支 未提交到远端
git reset xxx.txt|无变化
git reset --hard xxx.txt 报错 无效
git reset HEAD xxx.txt|无变化
git reset HEAD~1 xxx.txt |暂存区为上一个版本，工作区为当前版本，如果把工作区修改提交到暂存区，则互相抵消，无变化
git reset HEAD^ xxx.txt |暂存区为上一个版本，工作区为当前版本，如果把工作区修改提交到暂存区，则互相抵消，无变化
git reset c86d14 xxx.txt 暂存区为指定版本，工作区为当前版本，如果把工作区修改提交到暂存区，则互相抵消，无变化
git reset HEAD~1 |当前本地分支回退到a-1版本，丢弃暂存区修改(即没有暂存区修改)，工作区为当前版本
git reset HEAD^ 当前本地分支回退到a-1版本，丢弃暂存区修改(即没有暂存区修改)，工作区为当前版本
git reset c86d14 | 当前本地分支回退到指定版本，丢弃暂存区修改(即没有暂存区修改)，工作区为当前版本

提交到本地分支 已提交到远端
git reset xxx.txt|无变化
git reset --hard xxx.txt 报错 无效
git reset HEAD xxx.txt|无变化
git reset HEAD~1 xxx.txt |暂存区为上一个版本，工作区为当前版本，如果把工作区修改提交到暂存区，则互相抵消，无变化
git reset HEAD^ xxx.txt |暂存区为上一个版本，工作区为当前版本，如果把工作区修改提交到暂存区，则互相抵消，无变化
git reset c86d14 xxx.txt 暂存区为指定版本，工作区为当前版本，如果把工作区修改提交到暂存区，则互相抵消，无变化
git reset HEAD~1 |当前本地分支回退到a-1版本，丢弃暂存区修改，工作区为当前版本
git reset HEAD^ 当前本地分支回退到a-1版本，丢弃暂存区修改，工作区为当前版本
git reset c86d14 | 当前本地分支回退到指定版本，丢弃暂存区修改，工作区为当前版本


## 分支操作
命令|作用
:-|:-
git branch|查看本地当前分支
git branch dev|创建本地分支
git branch -a|显示本地和远程分支
git branch -r|只显示远程分支
git branch -d dev|删除本地指定分支（该分支已经合并到主分支）
git branch -D dev|删除本地指定分支（该分支还没合并到主分支）
git branch --set-upstream dev origin/dev|指定本地分支dev对应远程分支origin/dev
git checkout dev|切换到指定本地分支
git checkout -b dev|创建并切换到指定本地分支
git merge dev|合并指定分支到当前分支
git merge --abort|取消合并分支
git merge dev --no-ff -m "merge with no-ff"|强制禁用Fast forward模式，并写入信息，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息


## 仓库关联
命令|作用
:-|:-
git remote -v|查看远程仓库信息
git remote add origin (ssh url/https url/git url)|与远端仓库关联 origin可自定义
git remote rm origin|解除与远端仓库的关联
git clone (ssh url/https url/git url)|克隆远端仓库到本地



## 保存当前工作状态

情景：在dev开发中途，需要紧急修复master上的bug，必须暂停dev的开发

命令|作用
:-|:-
git stash|保存当前本地分支的工作状态到stash
git stash list|查看被保存的所有工作状态
git stash pop|恢复工作状态，同时把stash内容也删除
git stash apply|恢复工作状态，但不删除stash内容
git stash drop|删除stash内容


## 标签
命令|作用
:-|:-
git tag|查看标签列表，排序是按字母排序的
git tag v0.1 54f7329|给指定commit打标签，省略commit名则默认打在最新的commit上
git tag -a v0.1 -m "version 0.1 released" 3628164|打标签，-a指定标签名，-m指定说明文字
git show v0.1|查看某个标签对应的commit，可查看到说明文字
git tag -d v0.1|删除本地commit的某个标签
git push origin v1.0|推送本地某个标签到远程
git push origin --tags|一次性推送全部尚未推送到远程的本地标签
git push origin :refs/tags/v0.9|删除远程某个标签，注意要先删除本地的对应标签


## rebase变基
类似于合并分支，区别是：
情景：同事a在dev分支上修改并提交到本地，主管b在master分支上修改并提交到远程
合并分支：合并后，master分支包含master自己的更新内容和dev分支的更新内容，但dev分支只包含dev自己的更新内容
变基：变基后，master分支包含master自己的更新内容，dev包含master分支的更新内容和dev自己的更新内容

操作：
$ git checkout dev 跳到dev分支
$ git rebase master 执行变基
$ git rebase --continue 如果变基过程中有冲突，解决冲突后git add，但不用git commit，然后执行git rebase --continue
$ git rebase --abort 终止rebase的行动，并且dev分支会回到rebase开始前的状态



## 常见问题
### 处于new版本 - 选择过去的某个a版本
- 提交回滚：提交a版本的相反，即如果a版本是添加了某两个文件，则提交的是删除那两个文件
- 将master重置到某次提交
  - 软合并 - 保持所有本地改动：本地索引会回滚到a版本，提示落后多少个版本，内容是new版本的内容且已经缓存，直接拉取可以恢复到new版本
  - 混合合并 - 保持工作副本但重置索引：本地索引会回滚到a版本，提示落后多少个版本，内容是new版本的内容但还没缓存，缓存并拉取才可以恢复到new版本
  - 强行合并：索引和内容为a版本，提示落后多少个版本，直接拉取可以恢复到new版本

### 删除远程仓库的某些/某个版本
- 先选择错误版本之前的某个版本，右键，强行合并，刷新，会提示落后x个版本，然后命令行cd到对应项目目录下，执行git push -f完成。注意会把之间的所有提交全部删除，不管远程还是本地
- 如果只是想删除其中一个版本而不是全部，用“提交回滚”

### 忽略文件，使文件不被git管理
- 打开全局的忽略列表文件或者指定仓库的忽略列表文件（一般都是.gitignore），添加要被忽略的文件名，如果指定某种后缀的文件，用*.xxx(后缀)
- 如果决定要忽略前，已经添加该文件到git，除了要修改忽略列表文件，还需要cd到项目目录下，执行命令git rm --cached xxx，删除该文件<br/>
  如果是SourceTree做客户端，则在提交文件修改时，选择文件 - 右键 - 取消跟踪（效果即是提交一个删除该文件的修改），并修改忽略列表文件

### git知识点
- master分支可以删除
- HEAD严格来说不是指向提交，而是指向master，master才是指向提交的，所以，HEAD指向的就是当前分支。
当我们创建新的分支，例如dev时，Git新建了一个指针叫dev，指向master相同的提交，再把HEAD指向dev，就表示当前分支在dev上。

### 多人协作
1. 首先，可以试图用git push origin branch-name推送自己的修改；
2. 如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
3. 如果合并有冲突，则解决冲突，并在本地提交；
4. 没有冲突或者解决掉冲突后，再用git push origin branch-name推送就能成功！
5. 如果git pull提示“no tracking information”，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream branch-name origin/branch-name。
