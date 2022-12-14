---
created: 2022-05-26
tags: 嵌入
subject:  
importance: 2
skilled: 4
status:
author:
url: https://www.wolai.com/mTCkX9aLYQf9Uo5d4XNK9c
cover: 
---

硬件产品上华为一直在提它可以万物互联，而软件上微软也是一直在致力于搭建生态，可以不同软件应用间互相连接嵌入。这不微软官方终于支持PowerBI嵌入ppt中了，那截止目前，PowerBI已经可以嵌入outlook、excel、ppt中。可以看先前文章的介绍[[PowerBI你进入500强企业的敲门砖]]

但其实在官方支持之前已经有其他第三方的扩展是支持把PowerBI报表嵌入到PPT中的，接下来我们就介绍下这几种不同的方式

## Microsoft Power BI

一如名字，这是微软官方的可以嵌入PowerBI的插件，没什么可犹豫的，点击添加

![](https://secure2.wostatic.cn/static/tS3hByM2dUYDKo7TrZtejj/image.png?auth_key=1653545077-39UjKJ9yk6sYC1vtCskidf-0-797a93db6f9690cb7a65014538ae127b)

安装完之后点击插件会看到如下内容，画线外需要填入报表的链接

![](https://secure2.wostatic.cn/static/2s6KqDKN26fpmGn6PksPoe/image.png?auth_key=1653545067-b3p1TLNbQbLRB4sjB8dvQX-0-a70246988530dae47e713b7113bd7c9d)

我们回到浏览器复制想要嵌入的报表页面的链接，然后粘贴到上面的位置

![](https://secure2.wostatic.cn/static/fwsvqdbYMyJcq8i8LhDNi/image.png?auth_key=1653545056-tWurwmcWM2yBpUFp4rSntu-0-16cd010ea76cd52771e44f01cde32645)

效果如下，不仅可以做正常的交互，还可以作为静态图片展示。

![](https://secure2.wostatic.cn/static/o6AhywDuvpUNeDzy7Y1jHS/%E5%8A%A8%E7%94%BB.gif?auth_key=1653544898-3d3embYcenboMTyHsfS2QM-0-6712f1835cd30719e4a79b37f7ded678)

但是这个方式也会有问题，比如是直接加载过来整个页面，而不是某个图表，多数情况下，PPT中每页只需要一个多几个图表的，所以，目前针对这样的需求可能就需要单独开发页面，就像下面这样一个页面只有一张图表（也可以使用PowerBI Tiles插件，不过这个插件是付费的）

![](https://secure2.wostatic.cn/static/q8wEZzHdKxms9ozknqPCNB/image.png?auth_key=1653545030-kA6yaaoL14yyL8R4hxrvsd-0-16f613fee0ce5b46b72f3e8d8331cf53)

关于更多的内容也可以阅读官方的介绍 （目前的嵌入方式和官方写的可能不一样）

[Tell a story with your data. Announcing the all-new Power BI integration for PowerPoint. | Microsoft Power BI Blog | Microsoft Power BI](https://powerbi.microsoft.com/en-us/blog/tell-a-story-with-your-data-announcing-the-all-new-power-bi-integration-for-powerpoint/)

## Web Viewer

这个大概是最早的PPT中嵌入PowerBI报表的方式，本质上其实是嵌入网页内容，而且是需要必须将报表发布的公网才可以嵌入，非常不推荐这种方式

![](https://secure2.wostatic.cn/static/gX5DXqna3Vtz4spcGriF17/image.png?auth_key=1653545014-6GRSzeV8b2YUPXxSRc1Xz3-0-a26f7c54d0add5d96306fa43cf3aff54)

## PowerBI Tites

即使是现在，微软官方也出了嵌入PowerBI报表的插件，我仍想说这是目前为止功能最强的插件，基本上没有缺点，除了收费。有需要的可以去官网了解详情

[PowerBI Tiles Pro](https://powerbitiles.com/Pro)

但是使用这个插件需要进行授权读取工作区等的信息，所以通过它就可以在PPT里任意修改嵌入的报表，并且可以选定只嵌入报表页的某个图，了解过PowerBI Embedded的应该知道，通过代码我们是可以只调取报表页的某一个图表。通过PowerBI Tiles不需要我们写代码就可以轻松实现该功能。

只是限制会更加明显，因为插件保存的是账号的信息，会有安全上的隐患，这点上来说还是官方的最好，虽然功能少，但最安全。

![](https://secure2.wostatic.cn/static/9EmUi5YgXH7QBQsgiNRQ7S/image.png?auth_key=1653544996-9EwtiFuUfRYjZV5MnG98q9-0-dae33fb80ae9dfa701d2c29ab465b872)

本次微软大会更新了很多内容，接下来也会分不同的模块一起来探索学习这些功能，有兴趣的可以先看官方的文档

[借助 Microsoft Power BI |实现企业分析的民主化Microsoft Power BI Blog |Microsoft Power BI](https://powerbi.microsoft.com/en-us/blog/democratize-enterprise-analytics-with-microsoft-power-bi/)