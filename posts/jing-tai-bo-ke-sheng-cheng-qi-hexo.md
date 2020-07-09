---
title: '静态博客生成器 - Hexo'
date: 2020-07-09 18:45:01
tags: []
published: true
hideInList: false
feature: 
isTop: false
---

今天我们来看看Hexo是什么东西！！

## 什么是Hexo
官方说Hexo是一个快速、简洁且高效的博客框架，使用Markdown引擎解析文章，几秒内就可以生成一个静态网站。

OK，官方都这么说了，那咱试试。

## 机器配置
- MacBook Pro (15-inch, 2019)
- macOS Catalina 10.15.5
- node v13.12.0
- git  v2.24.3

## 安装
安装Hexo前提要安装好`Node.js`、`Git`，需要安装的同学请参考各官方的或者在百度上搜索哈，我想既然想用Hexo搭建网站，这些知识还是必要的。
ok，咱们继续。

### 全局hexo安装
```shell
 $ npm install -g hexo-cli # 全局安装
```

### 初始化目录
```shell
# $targetDir 是创建docs的目录
$ mkdir docs &&  hexo init docs 
$ cd docs && npm init # or yarn 
```
hexo 初始化好了，咱们看下目录结构。
```shell
 # 我是用yarn安装的。
├── _config.yml # 网站配置信息
├── node_modules # node 依赖包
├── package.json # 应用程序信息
├── scaffolds # 模板文件夹
├── source # 资源文件夹
├── themes # 主题文件夹
└── yarn.lock # 记录 yarn 安装依赖的版本
```

### 启动
OK，初始化好了之后，该跑起来了。
```shell
# hexo3.0吧服务器独立成模块了，必须安装才能使用 `hexo server`
$ cd docs
$ npm install hexo-server # 安装服务器 # or yarn add hexo-server
$ hexo server
# 当看到这信息时表示启动成功了，打开`http://localhost:4000`就可以看到网站了。
# => INFO  Start processing
# => INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
````

### 生成静态文件
```shell
$ hexo generate
```
当目录中生成`public`目录时表示已经生成成功啦！接下我们要做的就是部署到 `Github Pages`

### 部署

- 创建 GitHub 账号，并创建一个仓库 Token。点击[GitHub](https://github.com/)，进行注册。登录 GitHub 之后，点击[这里](https://github.com/settings/tokens/new)创建一个 Token，勾选上 repo 的相关权限即可。生成之后记得把 Token 复制到你的本地，因为一旦关闭网页将不能再看到它。

![](https://zenghongpeng.github.io/ruban.github.io/post-images/1594306458475.png)

- **创建仓库，存放构建后的网站文件**。创建一个公开仓库，名为**用户名.github.io**。（将用户名替换为你的 GitHub 用户名）

![](https://zenghongpeng.github.io/ruban.github.io/post-images/1594306591575.png)

- 安装`hexo-deployer-git`
```shell
$ npm install hexo-deployer-git 
```
- 打开**_config.yml**进行配置

```shell
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https://用户名.github.io/hexo.github.io/
root: /用户名.github.io/

# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: https://github.com/用户名/hexo.github.io # 这是第二步创建的仓库
  branch: gh-pages
  token: 'xxxx' # 这里是第一步生成的Token
```

- 运行 `hexo clean && hexo deploy `
```shell
$ hexo clean && hexo deploy # 部署 过程中可能会提示输入用户名和token 
```

- ok 看看那是否部署上去了。
![](https://zenghongpeng.github.io/ruban.github.io/post-images/1594307406513.png)

部署成功，但是别着急，还有最后一步要配置。
在仓库下找到`Settings`, 点击进入之后，找到`GitHub Pages`， 在`Source`中选择`gh-pages`分支. 访问`https://用户名.github.io/hexo.github.io/`

![](https://zenghongpeng.github.io/ruban.github.io/post-images/1594309747382.png)

![](https://zenghongpeng.github.io/ruban.github.io/post-images/1594309786962.png)

部署好的[网站](https://zenghongpeng.github.io/hexo.github.io/)
[源码](https://github.com/zenghongpeng/archive/tree/master/hexo-docs)












