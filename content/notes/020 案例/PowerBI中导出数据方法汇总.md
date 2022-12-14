---
created: 2022-06-25
tags: 外部工具 dax-studio 
subject: 其他
importance: 1
skilled: 5
status:
author:
url: https://www.wolai.com/muxiaoqi/m7ioaxPjYUx5UJsLqdPqKj
cover: 
---

虽然BI的目的是将人从做数中解脱出来，可终逃不过业务人员需要将数据导出到Excel然后自己做数据的命运，所以用户最常见的一个也是最刚需的一个问题就是怎么导出数据。今天就汇总下可以导出PowerBI报表中数据的几种方法。

## 视觉对象标头

首先需要确保这个功能是否关闭，如果勾选了隐藏视觉对象标头，在本地打开pbi文件时不会有任何影响，但是在server端阅读报表时点击图表右上角不会再出现标头。

![](https://mmbiz.qlogo.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicKFibAeM7siaQUDanMeCVdt9icvhUYsiakPbgYwHoUF8fgZLentW4NjIRFw/0?wx_fmt=png)

选中想要导出数据的图表，右上角图表标头—更多选项—导出数据，这种方法有数据限制，具体可阅读官方文档，

从 Power BI 可视化效果导出数据 - Power BI | Microsoft Docs[1]

![](https://mmbiz.qlogo.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicMgvH0FxbBicnetb7KiczUddlLFuhicr5CXic7uvbW1MFEqibHHa5icQdhJ9g/0?wx_fmt=png)

## 复制表

如果需要整表导出，可以在数据视图，选中需要导出数据的表，右键—复制表，然后粘贴到文件里即可。这种方法

![](https://mmbiz.qlogo.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicxVibYTpicfrZ05t9SCG3IDxnB1xrSOO1nOmUDktQ6bnJvRN0ibL8EbKNg/0?wx_fmt=png)

## DAX Studio导出

### 整表导出

使用EVALUATE关键字+表名，可以对数据进行整表导出为csv文件

![](https://mmbiz.qlogo.cn/mmbiz_gif/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicCOdicWstzTP434bOmNFrLOVFU2fTTIxt7hZp0vStg10KH1zJqmUmB6g/0?wx_fmt=gif)

### 图表数据导出

如果我们导出的是报表中某个超出限制的图表上的数据，仍然可以使用dax studio,可以直接在dax studio中书写查询代码，当然也可以把pbi报表中图表上的查询语句复制过来。

导航栏，选择视图—性能分析器—开始记录—刷新视觉对象，然后复制相关图表的查询语句

![](https://mmbiz.qlogo.cn/mmbiz_gif/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeiciahZaryy1bzAIYNGMXhuiaEOIiax4hPtxZ9zFULGkuibAsLYibBfDibZ8SSA/0?wx_fmt=gif)

将代码粘贴到dax studio中，会发现代码和我们在powerbi中写的dax代码会有些不同，但不影响阅读，同上导出整表的步骤，运行代码导出数据即可。

![](https://mmbiz.qlogo.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicbHmqAcyPgib9uO2EMTVbgH4l2MI66Av77paHLEQSodsfDs8S4npfErA/0?wx_fmt=png)

### 导出所有表

仍然是在dax studio中，切换到Advance—Export Data，之后可以选择将数据导出到Csv或数据库。

![](https://mmbiz.qlogo.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeic2dtw50gy5wTBMgcs1fM0qRNpcYiaYV2Lav8tssicbQSBRWlq4b4TMiaqA/0?wx_fmt=png)

![](https://mmbiz.qlogo.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicZMJCrEWlMciawfsAC4EpQg8wxNntAsohhU7Y0e0lfBvsp21bymjYBCw/0?wx_fmt=png)

## Power BI Exporter

如果是需要将pbi文件中的数据全部导出，也可使用Power BI Exporter，它虽然没有dax studio那么强大，对于导出报表中的数据来说却更方便，只需要在文件中点击一下即可

文件地址：

Power BI Exporter – Data Vizioner[2]

![](https://mmbiz.qlogo.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicefxwePYxRzHWGwia5rO2TiacTgUALqqS8iczOBuTztIibuFoFmO4Lmg39Q/0?wx_fmt=png)

当然，还有其他一些外部工具可以导出数据，比如Power BI Helper 等等。

## Power Automate

可以在pbi报表中加入Power Automate,通过点击按钮的方式来将数据下载到One drive或者本地，

具体可查看[[powerbi中使用power automate]]

![](https://mmbiz.qlogo.cn/mmbiz_gif/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicgwbzOjw0MxSlnE5RwiaKDoVThb229rk2ywXgqNdAXHicCvvL93kyMlcw/0?wx_fmt=gif)

## Python

当然也可以使用Python连接PowerBI数据集，从而导出想要地数据，具体可查看
[[当PowerBI遇到了Python]]
[[使用Python连接PowerBI数据集]]

![](https://mmbiz.qlogo.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicGc5IleTAyvTfjZfichWcWvAgdibZgqRibHhibLxvCsVGeiaQxOBotByhOVw/0?wx_fmt=png)

## Excel连接PowerBI数据集

如果导出数据的目的是在excel中查看的话，那么可以直接在excel中连接powerbi数据集，然后将想要的数据拖到数据透视表即可

![](https://mmbiz.qlogo.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicONyBQcJGv18Vrov4icQv5UJbtBzqGXKkFJFNN2iaeLDaBNTBkgyibr24w/0?wx_fmt=png)


引用链接  

`[1]` 从 Power BI 可视化效果导出数据 - Power BI | Microsoft Docs: _https://docs.microsoft.com/zh-cn/power-bi/visuals/power-bi-visualization-export-data?tabs=dashboard_  
`[2]` Power BI Exporter – Data Vizioner: _https://www.datavizioner.com/power-bi-exporter/_