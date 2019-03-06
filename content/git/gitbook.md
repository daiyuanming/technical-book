# 用gitbook做笔记

## 一、gitbook基本用法
### 1.1 安装gitbook
全局安装 gitbook-cli，运行
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
启动一个本地服务，打开 localhost:4000 就可以看到这个笔记了

## 二、gitbook部署到github
### 2.1 把笔记保存到github
新建一个 github 仓库，注意不用将编译目录 _book 添加进版本库，使用 .gitignore 文件忽略 _book 目录
### 2.2 把笔记编译成html
为了部署方便，新建 content 目录，将 markdown 文件都移进去，运行
```
gitbook build ./content ./docs
```
就会生成 docs 编译目录。
方便下次编译，可以把项目变成一个 nodejs 项目，运行
```
npm init -y
```
会生成 package.json，添加
```
"scripts": {
    "build": "gitbook build ./content ./docs"
},  
```
下次只要执行 npm run build 即可
### 2.3 部署到github pages
将 docs 目录也添加到 github 仓库，通过 github pages 服务，可以把编译后的 html 部署到公网
配置 github pages 服务，通过 settings > github pages，将 Source 设置为 master branch /docs folder，意思就是 master 分支的 docs 文件夹。
然后通过 https://{yourname}.github.io/{repositoryname}/ 就可以通过公网访问笔记了