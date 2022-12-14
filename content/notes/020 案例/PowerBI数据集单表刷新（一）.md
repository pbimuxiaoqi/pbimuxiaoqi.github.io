---
tags: 单表刷新 xmla
created: 2022-05-11
importance: 3
skilled: 5
subject: 
url: https://www.wolai.com/muxiaoqi/cDag7uJctcfdRmj9j8ptUU
cover: 
---
随着时间的推移，PowerBI的数据集会越来越大，这样刷新不仅会占用很多的时间，甚至是需要占用很多的服务器资源。但，其实也许这么庞大的数据集，数据有更新的也许只有其中一张表或某几张表，在PowerBI桌面版我们是很容易做这个操作，那么当报表发布到云端之后呢？

事实上，云端我们同样是可以对数据集进行单表刷新的，只是微软做了限制，需要有高级容量工作区，具体可参考官方文档。

接来来，我们来一起看下效果，首先需要打开XMLA设置，在管理门户>Premium Per User

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84NO2Cfnyk7V3MCibgGxicvEkUwicS1ffD1AcYiaNiarqsAbia1zZQlU29AEYfHFxh4O3kk5Fj7Jv97tje7A/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

回到工作区，设置>高级版，复制工作区连接

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84NO2Cfnyk7V3MCibgGxicvEkU1yjNKnhSW3iczMaINibOFCmWh50CMS7kGSYcnLeXaWt68bVTPJKRj3Ng/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

打开SSDT,新建连接，填入工作区连接信息及账户密码，登录后可以看到工作区内的所有数据集信息

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84NO2Cfnyk7V3MCibgGxicvEkUhoRQTDPQDiags2wF9NgLMQU4gpDib0SdHdnxBUhdE4Y7hibH1Ul3ZIjcw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84NO2Cfnyk7V3MCibgGxicvEkUdUwvBRfiazfJ4RdhcPXEQnbvibR1JggFFmGnuqWFaRGTjVonkX5Ch0Kw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

选中一个数据集，右键选择Process Table >Mode(Process Full) > Script

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84NO2Cfnyk7V3MCibgGxicvEkUxM8S4icKRzpCodcyneibXIJkicGfpFgyMWibphLEIRN9onQeM7h7CnxiaWg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

会看到如下信息，信息很简单包含我们要单独刷新的表的数据集名称及表名称，还有刷新方式，点击运行

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84NO2Cfnyk7V3MCibgGxicvEkUVMLfSNLaJq22BnU9FSVzVVP6FCicg0908ckXmr33qaZFLye8cp1w3fA/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

运行成功

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84NO2Cfnyk7V3MCibgGxicvEkUBDrCPBk9P8lLA2v7RTngTMqEZicBeYePR7o9Cr6MucMHic2TK9yjTTPw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

回到工作区，可以看到数据集已刷新，但事实上只是刷新了其中的Customer。

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84NO2Cfnyk7V3MCibgGxicvEkUP5PzXmicraroeqsZIPc2wmplgPy61OHDJ2I7yovGibRZQPuaLyib0NOOQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

既然这个方法是可行，那么我们就可以通过PowerBI Shell、python、C#或者在Azure创建任务流来触发单表刷新的操作，让流程更自动化。
