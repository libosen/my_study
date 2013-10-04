伯乐在线 git 学习笔记
====================

[Git 入门系列教程](http://blog.jobbole.com/25775/)
## 安装 Git
[git 官网](http://got-scm.com)
### Linxu 平台
* yum install git-core
* apt-get install git-core

### Mac 平台
* [图形化安装器](http://code.google.com/p/git-osx-installer)
* sudo port install git-core +svn +doc +bash_completion +gitweb
* brew install git

### Windows 平台
* [msysGit](http://code.google.com/p/msysgit)

## 配置 Git

### 用户信息
* git config --global user.name 'Zhang Jinglin'
* git config --global user.email 'zhangjinglin@gmail.com'

### 查看配置信息
* git config --list

### 获取帮助
* git help
* git help config

## Git 基础

### 在工作目录初始化仓库
* git init
    * git add *.c
    * git add README
    * git commit -m 'Initial project version'

### 从仓库克隆
> git clone git://github.com/zhangjinglin/my_study.git
>> git clone git://github.com/zhangjinglin/my_study.git MyStudy

### 检查当前文件状态
> git status

### 跟踪新文件
> git add README

### 忽略某些文件
> .gitignore
>>\# 此为注释
>> \*.a      \# 忽略所有.a 结尾的文件
>> !lib.a   \# 但 lib.a 除外
>> /TODO    \# 仅仅忽略项目根目录下的TODO文件，不包括subdir/TODO
>> build/   \# 忽略build/目录下的所有文件
>> doc/*.txt   \# 忽略doc/notes.txt 但不包括doc/server/arch.txt

### 查看更新了什么
> git diff

### 提交更新
> git commit
>> git commit -m '更新说明'

### 跳过暂存直接更新
> git commit -a -m '提交说明'

### 移除文件
> git rm README

### 移动文件
> git mv file_from file_to

### 查看提交历史
> git log
>> -p 展开显示每次提交的差异内容
>> -2 仅显示最近2次更新
>> --stat 仅显示更改行数

### 撤销最后一次提交
> git commit --amend

### 取消已经暂存的文件
> git reset HEAD

### 取消对某一个文件的修改
> git checkout -- xxxxx

### 查看当前的远程仓库
> git remote
>> git remote -v

### 添加远程仓库
> git remote add origin https://github.com/zhangjinglin/my_study.git

### 从远程仓库抓取数据
> git fetch [remote-name]

### 推送数据到远程仓库
> git push origin master

### 查看远程仓库信息
> git remote show origin


