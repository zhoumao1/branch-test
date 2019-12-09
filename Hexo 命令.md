[toc]

# Hexo 命令

npm install hexo -g #安装Hexo
npm update hexo -g #升级 
hexo init #初始化博客

命令简写

| 命令                                     | 含义                                         |
| ---------------------------------------- | -------------------------------------------- |
| hexo n "我的博客" == hexo new "我的博客" | 新建文章                                     |
| hexo g == hexo generate                  | 生成                                         |
| hexo s == hexo server                    | 启动服务预览                                 |
| hexo d == hexo deploy                    | 部署                                         |
| hexo server                              | Hexo会监视文件变动并自动更新，无须重启服务器 |
| hexo server -s                           | 静态模式                                     |
| hexo server -p 5000                      | 更改端口                                     |
| hexo server -i 192.168.1.1               | 自定义 IP                                    |
| hexo clean                               | 清除缓存，若是网页正常情况下可以忽略这条命令 |

```yml
---
title: postName #文章页面上的显示名称，一般是中文
date: 2013-12-02 15:30:16 #文章生成时间，一般不改，当然也可以任意修改
categories: 默认分类 #分类
tags: [tag1,tag2,tag3] #文章标签，可空，多标签请用格式，注意:后面有个空格
description:  #附加一段文章摘要，字数最好在140字以内，会出现在meta的description里面
---

以下是正文
```

### 那么`hexo new page 'postName'`命令和`hexo new 'postName'`有什么区别呢？

```shell
hexo new page "my-second-blog"
```

生成如下：

![img](Hexo%20%E5%91%BD%E4%BB%A4.assets/20160823_184852_854_6502.png)

最终部署时生成：`hexo\public\my-second-blog\index.html`，但是它不会作为文章出现在博文目录。

### 如何让博文列表不显示全部内容

默认情况下，生成的博文目录会显示全部的文章内容，如何设置文章摘要的长度呢？

答案是在合适的位置加上``即可，例如：

```yml
# 前言

使用github pages服务搭建博客的好处有：

1. 全是静态文件，访问速度快；
2. 免费方便，不用花一分钱就可以搭建一个自由的个人博客，不需要服务器不需要后台；
3. 可以随意绑定自己的域名，不仔细看的话根本看不出来你的网站是基于github的；

<!--more-->

4. 数据绝对安全，基于github的版本管理，想恢复到哪个历史版本都行；
5. 博客内容可以轻松打包、转移、发布到其它平台；
6. 等等；
```

最终效果

 ![img](Hexo%20%E5%91%BD%E4%BB%A4.assets/20160823_184633_653_1893.png) 