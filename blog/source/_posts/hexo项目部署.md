---
title: hexo项目部署
date: 2018-07-25 15:59:24
tags:
---
# github 相关设置

## 安装git
安装包见群文件
## 新建ssh key
1.在桌面右键选择git bash here
2.创建本地ssh key，输入如下命令：
```
ssh-keygen -t rsa -c "邮箱"
```
回车，然后记录下ssh的默认保存路劲，
3.后续一路回车，知道出现很多泡沫
4.打开ssh默认保存路径，找到id-rsa.pub文件，复制里面的内容备用
## 注册github
1.打开[github](https:www.github.com)点击右上角sign up注册个人账号
2.点击头像右侧倒三角，悬着settings按钮
3.选择左侧ssh and gpk keys
4.点击右侧 添加ssh key按钮
  title素以，下方粘贴创建好的ssh key
5.点击下方creat ssh按钮

## 验证ssh key
1.命令行输入
```
ssh -T git@github.com
```
回车，如果是第一次的会提示是否成功continue，输入yes就会看到：you ve successfully 就表示已经成功连上github
2.验证github用户名
```
git config --global user。name "用户名"
```
3.验证邮箱
```
git config --global user.email "邮箱"
```

## 测试本地链接github
1.点击github主页头像左侧+，选择new repository
2.创建一个仓库，取名随意比如abc
3.创建成功后，复制提示代码：
```
echo "# abc" >> README.md
git init


```
4.在桌面创建任意文件夹，并打开
5.右键git bush here
6.右键past刚才复制的代码回车
7.根据提示登录github账号
8.个别情况需要在命令行窗口验证github用户名
9.刷新github的abc仓库，如果本地文件存在，证明链接无误
  否则删除文件夹内的所有文件，重复步骤4~8
# 推送本地博客到github
## 配置hexo的-config。yml文件
1.打开博客项目根目录的-config.yml文件
2.在文件底部配置如下：
```
deploy:
  type: git
  repository: https://github.com/mkk123456789/mkk123456789.github.io
```
并且保存
3.安装deploy依赖包（仅需操作一次）
在blog所在路径依次输入如下命令回车
```
npm install hexo-deployer-git --save
```
4.添加域名解析文件
在vscode工具里面，选中更目录的source文件，右键悬着新建文件（new file），取名位CNAME，打开该文件，填入自己的域名，不带www也不带http，如：baidu，com保存即可

5.在blog所在路径一次输入如下命令
清除缓存
```
hexo clean
```
编译博客文件
```
hexo g
```
上传代码
```
hexo d
```
## 域名解析
1.打开i阿里云域名控制中心
2.选中自己购买的域名，，点击右侧解析
3.删除已有的解析记录值
4.点击新建按钮添加三条记录值

记录类型|主机记录|解析线路|记录值
-|-|-|-
CNAME|WWW|默认|用户名。github.io
A|@|默认|192.30.252.153
A|@|默认|192.30.252.154
