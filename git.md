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


