---
created: 2022-06-19
tags: 外部工具 Bravo 日期表
subject: 
importance: 5
skilled: 5
status:
author:
url: https://www.wolai.com/muxiaoqi/qCMfedarbUzcZWAX3Pjrbq
cover: 
---
https://bravo.bi/

SQLBI终于对PowerBI外部工具出手了—Bravo，虽然它没有Dax Studio、Tabular Editor 那般强大，但真的是新手友好。目前官方介绍的主要有4个方面的功能，接下来我们就一起来看下这些功能

## 分析数据模型内存占用

这是一打开工具就展现的页面，可以查看模型中每个的内存占用情况，不仅可以直观地看出每张表的大小，也能看出占总数据的百分比，在右侧的树状图还列出了占用较的列名。虽然以上这些数据都可以通过dax studio 中DMV语句来查看，不过还是Bravo的界面更加直观些，也更友好。

![](https://secure2.wostatic.cn/static/6Mefo4iAcrzq9UTcjdMYqH/image.png?auth_key=1655628316-iJLHuwgXdVTUs6Yxn6DxW5-0-ce171b15cf17aa706c8786134e83d6d5)

## 格式化度量值

以前也有人在基于SQLBI的接口的基础上出过格式化度量的外部插件，但体验并不好，Tabular Editor3上格式化度量效果倒是挺好，但无奈收费太高，所以很多时间还是去[Dax Formatter](https://www.daxformatter.com/)网页端进行格式化，但需要一个个复制，也挺麻烦的。

在Bravo中可以直接全选度量值然后进行格式化

![](https://secure2.wostatic.cn/static/9cfHTbfx8TLHXp29Fqo9ZV/image.png?auth_key=1655628322-dKiweX5uyUrMXJcJjZ8mTz-0-1e195401a0fb911abfe77a4ca0ce1c42)

## 轻松创建日期表

日期表作为BI报表中最基础的数据，我们经常要根据不同的报表需求创建不同的日期表，可能就需要保存好多日期表的模板，但是使用Bravo就可以轻松创建出满足不同需求的日期表，不仅可以选择日期表的起始时间，还可以选择显示假期，只是目前还不支持中国的节假日，希望在以后的更新中除了中持中文外，也可以支持中国的节假日。

![](https://secure2.wostatic.cn/static/iGdHty7ianFQoeX3XcxmSh/image.png?auth_key=1655628330-daoRbyPPLVVjB54zuUE5BK-0-1b8443384697176fbec6f9803837e324)

![](https://secure2.wostatic.cn/static/7jGpZqx9kcxui2QsP4nzTr/image.png?auth_key=1655628338-rMijjLZ7P1SqhL1Zt9gt9G-0-9a2501740f6938e91ab5301d683e3217)

在生成日期表时，还有一个重磅功能，就是生成时间智能相关的度量，并按文件夹存放，这点不要太小白友好 ，在[[PowerBI快速生成多个度量值]]中介绍过使用Tabular Editor快速生成多个度量，但是需要写C#代码来实现，老实说不看例子，现在让我盲写我也是写不出的，但使用Bravo我们完全不用去关心C#代码的问题，只需要选择需要生成时间智能的度量值，然后点击生成就好了。

![](https://secure2.wostatic.cn/static/mixGYwVeaQecncucx1DNAE/image.png?auth_key=1655628345-cf3PGYBACfG89qQXs7Xr9K-0-d08de522cd9b346aa92e505c8381a3ad)

可以看到已经按文件夹存放了，虽然计算组也可以快速生成同环比这些指标，但是计算组并不是所有的情况都最适用。Bravo这个功能无疑是懒人必备。

![](https://secure2.wostatic.cn/static/aZJG5WBWhmxWMRrEMwpm2o/image.png?auth_key=1655628352-x6yA3rSWZX4bvWwHYhA6Kg-0-a9be0c589a65bc693b21a2826078a01b)

## 导出数据

这大概是很多业务人员的需求了，他们更愿意在Excel中来二次处理数据，而PowerBI中导出数据是有行数限制的，很多外部工具都有导出数据的功能，其中我最喜欢的是Dax Studio,不止是可以全量的导出为csv，也可以导出数据到SQL数据库，但是Bravo的导出数据功能无疑更加简单直观，没有太复杂地功能，只满足最基本的需求。另外如果针对于云端报表也可以使用python连接数据集来处理([[使用Python连接PowerBI数据集]])。

![](https://secure2.wostatic.cn/static/aSMjL3Q9GaEiymF5zLLU1S/image.png?auth_key=1655628359-izo1UB31TjGeZi5aV9cbkD-0-d163269eb3b889a130425f12af40fa29)