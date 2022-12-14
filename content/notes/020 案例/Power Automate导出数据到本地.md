---
created: 2022-06-25
tags: autoomate 
subject: 
importance:
skilled:
status:
author:
url: https://www.wolai.com/muxiaoqi/kLif62NKDRF9bfFt6sWtnz
cover: 
---

在上一篇[[PowerBI中导出数据方法汇总]]导出数据时有介绍可以介绍到可以借助于Automate来下载数据,在[[PowerBI中使用Power Automate发送数据]]中有介绍怎么导出数据到OneDrive中，今天就再来介绍下怎么下载数据到本地。

第一步仍然是在PowerBI中创建一个Automate对象，并将想要下载到数据加进来。

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicTL2QPLiaGRTxERRsYLzOB1RA1zDLOLxtDngWDBsBn6BIM5Ssh0rx6Qg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

接下来，点击右上角标头，选择编辑，进入到编辑页面后选择新建即时云端流

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicPKF5krtr5WCnM2puKnLjhibbk9XKr1v20CvK9CwcO4YvDBrYOqs6hRw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

接下来就是创建一个csv文件，用于存储数据，直接搜索csv即可。

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicrHlR8tg6p0FY3iaHteQRTe3YibuPibv3cPhV8ewxdwtUibwY3aZC3T9ZYg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

选择数据，这里列我们选择自动就好，如果想要重新命名列，或只导出某几列的数据，也可以点击左下的advanced options

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicuV5FGGhOWmMPqiblSvKgvMEMWBoJHT9uC5zU9BHwL6XKr3GtzIDiaibPg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

接下来创建文件，选择file system后，选择创建文件

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicfAOgYLTibicSvliatcfulPIO03MLgVyXyGBhkAo7mOqeWsM3nW7wgT43Q/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicoQAdoEgu1PU968xNfR3yia9UKkXgZxNa4RrtEUZz1Z7G8npoIibeAYBg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

文件内容选择上一步输出的表就行，文件名可以随便取一个，也可以写在动态文件名，配置完之后应用即可。

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicW7r6FeUCkExxKyZ1rM9QWpM6XbsSFeEMnblGuZnicKaEia2PHSDmicxPQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

如果此前没有创建过连接器的话，在选择file system后还会让先创建一个连接器，当然即使以前创建过我们也可以继续新建

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicoeAiaor0gTIqg1vLPVwzrpYX9zzUQjibMcAEyX1XZQe8dgsEiar5PkauQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

在配置连接器的时候也要确保已经在本机上配置过网关，且需要本机的名称及开机密码

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicjE6oqexNXpM7Ap9FD4WJrPSZT5hialBia5s1f17J5tLOFvNLe2KiavpjA/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

返回报表页查看效果

![图片](https://mmbiz.qpic.cn/mmbiz_gif/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicFibaIe9OFP5ib7YkMjHS1EhCY5UeKmwiavtibicugRVBAC5TlazffdjN1UA/640?wx_fmt=gif&wxfrom=5&wx_lazy=1)

## 应用场景

上述这个例子其实是有些简单的，甚至是有些鸡肋，因为如果是发布云端，且共享给别人后，别人点击后是下载到网关所在的电脑，连Onedrive都不没有的公司会有单独的网关服务器吗？额，这是一个问题。。。所以如果网关是装在个人电脑上的，那文件位置设置为坚果云等本地同步的文件夹里是最好的选择。

另外automate也可以运行dax查询，配合触发器，就可以定时发送或者下载报表中的相关数据，比如月初发送上月数据，周一发送上周数据等等。

所以，还是那句**PowerBI是个可厉害的BI产品，同时它也是个很强大的BI生态**。

还没有powerbi 账号或automate许可的，可查看[[PowerBI开发者账号申请，不限license]]

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84MTP6LGCVMJzVpo8jsibuibeicBpaCVLbrLovPHvGicWA6AT02IqgnN0mQg7s6X2QFgibEibbdPd8OGLQ7w/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)