---
title: 用 Hello 搭建属于自己的免费博客
description: 本文是关于 hexo + gitpage 静态博客的搭建，还有一些插件的使用。程序员怎么能没有自己博客呢！
---

## 前言
笔者之前的博客系统是基于~~WordPress~~, 一开始用的是阿里的服务器搭的， 后来觉得服务器维护起来实在太麻烦，再者每个月的服务器费用平时工作太忙也没有好好使用，就感觉很浪费钱(虽然只要50块，但是50块买炸鸡不香吗)。后来就买了一个虚拟空间放博客。后来什么原因又要重新备案，而且虚拟空间有限， 放图片也是个问题呢，真是不想折腾。
虽然不怎么折腾博客， 但是日常的笔记一直在写，用的是**有道云笔记**。不过有道的只支持基本的**Markdown**，真是很遗憾 。
我想既然这样为啥不搭一个静态博客呢，还能在网上访问到，你说是吧。如果你也和我一样，那么 hexo 也适合你， 本文章会教你基于**gitPage**和**hexo**搭建免费的个人博客。闲话少叙，砸们开始吧。
你可以访问[**Hexo官网**](https://hexo.io/) 查看介绍     [**Hexo文档**](https://hexo.io/docs/)  [**GitHub仓库地址**](https://github.com/hexojs/hexo/issues).
## 预备
首先我已默认你已经注册了 [**GayHub**](https://github.com). 没有的大胸弟自行点击注册哦。:v:


## 配置GitPage
1. 首先登陆GitHub新建一个项目
![new-repo](hello-world/new-repo.jpg)
2. 填写以你的用户名命名的仓库 
![new-blog](hello-world/new-blog.jpg)
3. 点击**setting**, 往下拉到 **GitHub Pages** 你可以看到, 根据提示我们首先添加一些内容到这个仓库
![git-page](hello-world/git-page.jpg)

``` bash
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)

### 那要怎么给博客添加图片呢
#### so easy 👌 只需短短2步:
1. 配置博客目录下的 _config.yml 文件查找 **post_asset_folder** 并把它改成**true**, 这样在你建立文件时，Hexo会自动建立一个与文章同名的文件夹
2. 在博客根目录执行以下命令安装插件
```
  npm install hexo-asset-image --save // 介系一个阔以上传本地图片的插件
```
#### 尝试以下看成功了没:
1. 依次运行命令`hexo n mysql删库到跑路` 试试看吧, 如果一切妥当， 那么在 `source/_post` 目录之下除了 **mysql删库到跑路.md** 的文件外还有一个同名的文件夹
2. 在该文件夹下随便放一张你的帅照 **ShuaiZhao.jpg** , 然后在**mysql删库到跑路.md**文件中引入:
```
  ![ShuaiZhao](mysql删库到跑路/ShuaiZhao.jpg)
```
3. 运行`hexo clean ` , `hexo g`,`hexo s` 瞅瞅。看成功没。 没能成功？ 快去搜索一下插件兼容是不是有问题。我反正是阔以的。   
4. 没成功也没关系哈, 你也可以在图窗或者云空间上放置图片， 在文章里`![图片](http://img-url)` 即可。

### 最后来给你的博客加点欢乐的元素————开启emoji之旅 😍🤣
#### 安装
命令如下
```
npm un hexo-renderer-marked --save
npm i hexo-renderer-markdown-it --save
npm install markdown-it-emoji --save
```
#### 配置
修改 Hexo 站点配置文件 _config.yml 文件添加如下代码
```
## markdown 渲染引擎配置，默认是hexo-renderer-marked，这个插件渲染速度更快，且有新特性
markdown:
  render:
    html: true
    xhtmlOut: false
    breaks: true
    linkify: true
    typographer: true
    quotes: '“”‘’'
  plugins:
    - markdown-it-footnote
    - markdown-it-sup
    - markdown-it-sub
    - markdown-it-abbr
    - markdown-it-emoji
  anchors:
    level: 2
    collisionSuffix: 'v'
    permalink: true
    permalinkClass: header-anchor
```

