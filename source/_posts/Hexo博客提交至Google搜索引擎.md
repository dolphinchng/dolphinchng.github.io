---
date: 2018-1-12 20:23:09 
update: 2018-2-12 20:12:03
title: Hexo博客提交至Google搜索引擎
tags: 
categories: seo
comments: false
---
## 验证你的网站是否被谷歌搜索收录

在谷歌搜索中搜索一下内容：

```
site:你的网站地址
```



如果显示结果为**找不到符合搜尋字詞**则表示你的网站没有被谷歌收录！反之，结果包含你的网站页面，则代表你的网站已被谷歌收录。

## 提交网站到谷歌搜索引擎

登陆 [**Google网站站长**](https://www.google.com/webmasters/) 点击SEARCH CONSOLE按钮，进入后你将看见以下画面。
![](http://ww1.sinaimg.cn/large/bf4c214dgy1fxwxshuw3ij20v508emz3.jpg)
点击添加属性，填入你的网站地址。

![](http://ww1.sinaimg.cn/large/bf4c214dgy1fxwxtawy76j20od0bumzn.jpg)
之后呢，Google会提出通过几种方式验证你对网站的所有权，选择推荐方式通过“html验证”，下载“html验证文件”，拷贝到`你的本地博客hexo/ sources/` 下。

![](http://ww1.sinaimg.cn/large/bf4c214dgy1fxwxqid2qij20lp0f5jx5.jpg)
**注意**：hexo在部署source 文件夹下markdown语法格式的文件成html格式时（本身文件格式就是html格式），都会遵守固有的html布局格式，**所以后面Google验证html文件时，此时的“html验证文件”已经不是原本下载的文件，变成遵守固有布局的html文件**，为了正常验证步骤进行，部署服务器前必须先打开“html验证文件“，加入以下内容，让固有的html布局失效。

```
layout: false
---
```



部属到GitHub远程仓库。

```
hexo g -d
```



本地操作完成后，继续返回到网站页面，点击验证，成功！
![](http://ww1.sinaimg.cn/large/bf4c214dgy1fxwxup991cj20nc0bxmz1.jpg)

## 生成站点地图

在本地Hexo博客根目录下安装sitemap生成插件

```
npm install hexo-generator-sitemap --save
npm install hexo-generator-baidu-sitemap --save  //不想被百度收录可以不安装
```



编辑站点目录下的_config.yml配置文件，添加以下字段：

```
# 自动生成sitemap
sitemap:
  path: sitemap.xml
```



部署到远程仓库

```
$ hexo g -d
```



这时在远程仓库根目录就可以看到`sitemap.xml`文件了。
返回[谷歌站点地图](https://www.google.com/webmasters/tools/home?hl=zh-CN)，选择已经验证过的站点，在抓取 -> 站点地图 中，右上角可看到 添加 / 测试站点地图，添加 sitemap.xml 的链接。

![](http://ww1.sinaimg.cn/large/bf4c214dgy1fxwxv6l9zuj211g0de42b.jpg)
提交站点地图成功！

![](http://ww1.sinaimg.cn/large/bf4c214dgy1fxwxw9htx9j211l0go43f.jpg)

## 等待谷歌收录

相信谷歌的效率，不出几个小时你的文章马山就能被搜索引擎收录！

## 测试

在谷歌搜索中搜索你的网站主页或者文章标题，出现即可。

## 引用

这里特地感谢这些文章的帮助。
1.[Hexo博客之后续SEO优化](https://www.jianshu.com/p/c20bb9df1867)
2.[Hexo 博客搜索 SEO 优化 – 谷歌篇](https://fedoryx.github.io/Hexo-%E5%8D%9A%E5%AE%A2%E6%90%9C%E7%B4%A2-SEO-%E4%BC%98%E5%8C%96-%E8%B0%B7%E6%AD%8C%E7%AF%87/)