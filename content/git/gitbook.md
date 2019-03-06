# 用gitbook做笔记

## 一、gitbook基本用法
### 1.1 安装gitbook
全局安装gitbook-cli
```
npm i -g gitbook-cli
```
### 1.2 初始化项目
新建一个文件夹，并初始化
```
mkdir gitbookdir
cd gitbookdir
gitbook init
```
初始化之后会生成两个文件：
1、README.md，笔记首页
2、SUMMARY.md，笔记目录索引
### 1.3 启动本地服务
```
gitbook serve
```
启动一个本地服务，打开localhost:4000就可以看到这个笔记了

## 二、gitbook部署到github
### 2.1 把笔记保存到github
建一个github仓库，注意不用将编译目录_book添加进版本库，使用.gitignore文件忽略_book目录
### 2.2 把笔记编译成html
为了部署方便，新建content目录，将markdown文件都移进去，运行
```
gitbook build ./content ./docs
```
就会生成docs编译目录。
方便下次编译，可以把项目变成一个nodejs项目，运行
```
npm init -y
```
会生成package.json，添加
```
"scripts": {
    "build": "gitbook build ./content ./docs"
},  
```
下次只要执行 npm run build 即可
### 2.3 部署到github pages
将docs目录也添加到github仓库，通过github pages服务，可以把编译后的html部署到公网
