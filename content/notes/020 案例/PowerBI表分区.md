---
tags: 刷新 表分区 xmla
created: 2022-05-11
import: 3
skilled: 3
subject: 数据刷新
url: 
https://www.wolai.com/muxiaoqi/hwi5h4ccyFr2UHq6Q2s7Hy
cover: 
---

https://docs.microsoft.com/zh-cn/power-bi/connect-data/incremental-refresh-xmla

我们已经知道高级容量工作区是可以单表刷新的（[[PowerBI数据集单表刷新（一）]]），那么如果我们想要刷新的只是这张表的某一部分数据呢？肯定很多人已经想到了增量刷新。[[增加刷新]]是通过创建RangeStart和RangeEnd两个参数，应用参数筛选数据后在前端页面再设置增量刷新的策略。应用增量刷新后，数据表其实是分了好多区。更多增量刷新相关可以参考官网
  https://docs.microsoft.com/zh-cn/power-bi/connect-data/incremental-refresh-overview

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVIjy7TpxYAeaPvGOYABiaYW4rXn74qJljpicxHaeKB5Ekbdwiadlyibs15A/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

那么，我们可以不按时间来对数据分区吗？答案肯定是可以的，只是相对设置增量刷新步骤上会有些不同。

我们将报表发布到云端，然后通过Tabluar Editor来连接模型（xmla功能目前只支持高级容量工作区，如果想体验该功能的可参考PowerBI开发者账号申请，不限license，基本上可以无限体验PPU,也就是可以无限用高级容量工作区）

## 增加分区

### **Tabular Editor增加分区**
打开Tabular Editor,连接PowerBI账号

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVkGkfqWX99zUtjUDVpaBAtblxNwJe22IhrY9Hog2SEzLYq7Yp2oSQBw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

工作区连接信息可以Server端打开工作区后，设置—高级查看，但基本上是

-   国际：powerbi://api.powerbi.com/v1.0/myorg/{工作区名称}
    
-   国内：powerbi://api.powerbi.cn/v1.0/myorg/{工作区名称}
    

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVibmohibXrG5mkUMLuSvibrWaAKjml3BZ8KGWdK0xwASGyRKgicFK8Cpia8Q/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

输入账号信息

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVeq7F1iamDVcglpYh24MVVLn5mj1hImwibMOicAVqZGmgWW9j3DVE5wokA/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

选择我们要使用的模型

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVNmkrHemqLsYmZp4Ddqibfia5WC4oTqNnBWgYjRpKicwRmrgaleuuCaFyQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

可以看到事实表现在只有一个分区

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVGuf2KJvEh2ZD1Nbb3cPTHziaoVAiccxYwfNB8ZAaRtjr2xicibkWx90Xmw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

接下来我们按PromotionKey来对数据进行分区，M语言好的可以直接在Tabular Editor这里修改表达式，如果你像我一样对M不是很熟悉，可以回到PowerBI的PQ界面，对数据进行操作后再复制代码过来。

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVtjOBtNC93ulRNepu81q3FQKEwHUNicfnTeIKHnvQibomqEonRNZpNgvw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

pq界面过滤数据

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVWHbFO50S1F3UxJRZk5ibJFVTOKufKw2vMw71uhticypnDlHibwCXIeZeQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

复制pq代码

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVaDzjg3uKMaEAOxS7MH3YKVrAJiaFth1qQRqw9Kwia90VmcD0IDrP8bcw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

右键，新建分区，粘贴代码，然后多建几个分区，并修改相应的过滤代码，从而可以包括PromotionKey的所有值

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVTzuWDEnicZj5NMbb95kuTrJ8icHX9CoMRV7rtKU4zdU18LuN3FaZbjuQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

最终如下，这里需要注意：出于演示目的，默认的分区我们并没有删除，待会再讲为什么需要删除默认的分区。

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVYnv37W8m3ibu9GlibEqOjxQUJSTic4TvwNhD1L2EQ1ic8gGa2t9RU1AgUw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

一切都设置好后，点击保存

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBViaF2auOgxW1uzB9VAlv57fL4L0GFQ2HABaRfCAAurAJuvKDeyuSicJqw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)


### **SSMS增加分区**

打开分区面板，然后选择新建即可新建分区，相应的也可以对分区进行修改和删除。

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVOL10HpKjPwP6C2DNndicGeG1le2kxnb92QfBZeYApUyJQqiaxs3Bk7dg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)


## **刷新分区**

打开ssms，新建Analysis Services连接，填写对应信息

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVPug7q2ibB27AsZibh0YKjb0R6rECRrdKPalT5bC8uuY6yF4kdTmJULIQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

选择刚设置的数据表，然后查看分区

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVDG5eQEIwf9WPeXiayhY1FKu7E5pPmoueTzvHxw1OiaR3y59TUoFFllyQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVeNZCsV8hF8N6ianKcCuISj9IoJN3VKOf0uAgvyLslxoXR7APqQv6aSQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

发现除了默认分区，其他分区并没有数据，我们选择进程，然后刷新分区数据，这里就可以实现只刷新某个分区的数据了，我们先刷新所有。

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVeETbib7bKqBahypaOX4tygAaGM8NRsf0O7EkISKtHo9VVhJOYWxzd4g/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

刷新完之后会发现默认分区仍然是所有数据，所以**如果要对数据进行分区，一定要删除默认的分区**。

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBVUFWuo4S4SrSH7hAia8y66d4kSUULwfBibE4pwsCAkTsriaDQBvSBXNib4A/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84N6Siaol7IuASiaRejPeAibkBV4QtU949mPpCxiciaHNrpatgJeaSN1Zaf0BFo0HcIDMMOicnHlW7mXEqQQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

## **总结**

当数据集很大的时候，我们是需要只针对变化大的事实表进行单表刷新就好了，如果事实表中又只是某种类型的数据有变动，就可以通过创建分区，只刷新这个分区的数据，从而节省资源消耗，加快刷新时间。