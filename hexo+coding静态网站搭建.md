---
title: 'hexo+coding静态网站搭建'
href: '2018-07-18-hexo-start'
categories: 前端
date: 2018-07-18 15:50:12
tags:
  - hexo
keywords: hexo, 静态网站, github
---
使用hexo和git来实现一个 **免费** 的静态博客网站.
<!--more-->

# 1.搭建 hexo 环境
## 1.1. 使用 hexo 需要安装 **nodejs** 
> 推荐使用 **nvm** 进行安装

## 1.2. hexo主题以及静态网站的部署则需要安装 **git**
> hexo 会生成静态网站的代码,上传到git仓库.启动page服务.

## 1.3. 安装好以上插件之后，进行 **hexo** 的安装
>npm install -g hexo-cli //hexo 所需要的脚手架

# 2. hexo 本地安装
## 2.1. hexo 初始化
```
$ hexo init <folder>
$ cd <folder>
$ npm install
```
以上为初始化 hexo ,并对hexo所需要的一些基本插件进行安装.

### _config.yml
网站的配置信息，您可以在此配置大部分的参数。
### package.json
hexo 或是主题 所需要的插件,都会保存在 package.json 里面,仅限于你已经 npm install name --save 的插件

## 2.2. hexo 配置
* title	网站标题 
* subtitle	网站副标题
* description	网站描述
* author	您的名字
* language	网站使用的语言 主要是 主题中所提供的语言文件名称
* timezone	网站时区。Hexo 默认使用您电脑的时区。时区列表。比如说：America/New_York, Japan, 和 UTC 。
* description主要用于SEO，告诉搜索引擎一个关于您站点的简单描述，通常建议在其中包含您网站的关键词。author参数用于主题显示文章的作者。
* url	网址	
* root	网站根目录	
* permalink hexo生成的文章所对应路径:year/:month/:day/:title/
* permalink_defaults	永久链接中各部分的默认值	
*  skip_render	跳过指定文件的渲染，您可使用 glob 表达式来匹配路径。	

## 2.3. hexo 主题
> 使用 hexo 不仅仅是免费,而且还有许多好看的主题. 你可以在官方主题网站,也可以在搜索引擎上去搜索,都会有使用教程
# 3. hexo 线上部署
> 如果仅仅是想要部署到 git 上,只需要 配置 _config.yml 的 deploy 参数,然后使用 **hexo d** 就可以部署到git了.然后启用 **git pages** 服务. 然而这种方式存在很多的不方便.每次都要手动输入命令 **hexo g** 来生成静态页面, **hexo d** 来发布页面.而且更换电脑之后，还要重复进行上面的操作。在参考了很多的文章之后，使用了 **travis-ci** 来进行 自动进行上面的这些操作.
## 3.1 travis-ci 持续集成
> 以下travis的内容参考 [基于 Hexo 的全自动博客构建部署系统](http://kchen.cc/2016/11/12/hexo-instructions/#Travis-%E5%92%8C-Hexo) 

* travis 不需要单独注册，直接使用 github账号登录即可。然后勾选上 博客 的repository

* 安装 Travis CML 因为需要git需要添加公钥才能进行push操作，所以安装 travis cml 来加密私钥并在 travis 时进行 git 的 push。

* 首先必须有 Ruby 1.9.3 以上，检查了版本之后，安装 Travis，检查版本即可：
```
ruby -v
gem install travis -v 1.8.4 --no-rdoc --no-ri
travis version

travis login
```
* 配置 travis 在博客根目录下添加 Travis CI 所需要的配置文件 **.travis.yml**，以下是我的配置文件的内容：
```
language: node_js
node_js: v8.11.3
cache:
  apt: true
  directories:
  - node_modules
before_install:
- openssl aes-256-cbc -K $encrypted_3d66e7a0a5ec_key -iv $encrypted_3d66e7a0a5ec_iv -in ./.travis/github_rsa.enc -out ~/.ssh/github_rsa -d
- chmod 600 ~/.ssh/github_rsa
- eval $(ssh-agent)
- ssh-add ~/.ssh/github_rsa
- cp .travis/ssh_config ~/.ssh/config
# 配置 git 替换为自己的信息
- git config --global user.name 'hr1ycfl'
- git config --global user.email '1900427303@qq.com'
- export TZ='Asia/Shanghai'
install:
- npm install -g cnpm --registry=https://registry.npm.taobao.org
- cnpm install
before_script:
- sed -i 's/baiduUrlToken/${baiduUrlToken}/' ./_config.yml
script:
- hexo clean
- hexo g
- hexo d
branches:
  only:
  - master
notifications:
  email:
  - oneal.wang@foxmail.com
  on_success: change
  on_failure: always
```
* 在博客目录配置 .travis 存放 所需要的文件 
```
mkdir .travis && cd .travis
travis encrypt-file ~/.ssh/github_rsa
```
* **github_rsa**为你自己私钥文件的名称 现在 ls 命令查看一下 .travis 目录应该只有 id_rsa.enc 这一个文件才对。然后我们再在当前目录下新建一个 ssh_config 用来配置 Travis 上的 SSH Client。
```
Host *
  User git
  StrictHostKeyChecking no
  IdentityFile ~/.ssh/github_rsa
  IdentitiesOnly yes
```
* 现在，我们在 Travis 网站，博客项目的设置（项目右上角）里可以看到两个用于解密私钥的环境变量：

* 把这两个环境变量名复制到上面的 .travis.yaml 文件里替换相应部分：
```
before_install: - openssl aes-256-cbc -K encrypted_3d66e7a0a5ec_key -iv $encrypted_3d66e7a0a5ec_iv -in ./.travis/github_rsa.enc -out ~/.ssh/github_rsa -d
```
* 现在就可以进行博客源文件的提交 可以参考 [我的博客构建源文件](https://github.com/hr1ycfl/blog-source)。

## 3.2 开启 pages 服务
上面的提交只是博客源代码的提交，在 **hexo d** 的时候进行的是 博客静态网站的部署，是基于网站中 **_config.yml** deploy 中配置来进行部署。
部署过之后，只需要开启 github 或是 coding 的 pages 服务，就已经完成了一个静态博客的搭建。


