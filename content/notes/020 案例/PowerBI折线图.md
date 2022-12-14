---
created: 2022-06-19
tags: 折线图 异常值 AI
subject: 可视化
importance: 5
skilled: 4
status:
author:
url:
https://www.wolai.com/muxiaoqi/62r2fUe9gaMuVecPU5gMFG
cover: 
---

你有没有见过这样的拆线图呢，阴影区域是目标销售额的上下限区间，虚线是目标销售额，实线是实际的销售额，显示开关标记的是销售额相对于目标超额10%以下的。

![image.png (958×440) (wostatic.cn)](https://secure2.wostatic.cn/static/foWFGuVRfvpGfkjGCXSfCG/image.png?auth_key=1655992813-xsv6U6Qy9Tdc6Rixkc3CF4-0-7a81c5c80a38983bb2b87cc9e1cbed7c)

在以前要做这样的一份折线图，还是很麻烦，可是随着PowerBI的更新，原生图表也加入了越来越多的内容，今天就一起来体验下原生拆线图的进阶玩法。

## 简单拆线图

我们先来拖一个最简单的折线图，眼尖的可能已经看出来了，X轴并没有显示出所有的月份，而且X轴是从0开始的，幼儿园的小朋友都知道月份是从1开始的，PowerBI当然也知道，不过需要你来告诉它。

![image.png (1103×438) (wostatic.cn)](https://secure2.wostatic.cn/static/igy6jnk9pfVrMB7rkXgyrf/image.png?auth_key=1655992821-ifkhFFsBetUZxbqyyiMaCw-0-12d3c053c8a75a188fc853c5a2f94464)

选择设置视觉对象格式—X轴，修改X轴的类型为类别，此时X轴已经包含了所有月份，但是顺序有点乱，从图形可以看出是按销售额降序排列的，所以我们还需要修改下排序方式。

![image.png (1113×602) (wostatic.cn)](https://secure2.wostatic.cn/static/rNoYGtK8wHedz2iqHJtdmW/image.png?auth_key=1655992830-vidz2UxwPeHNacTsiPhwh7-0-6d7a767d0739788eecaccdd9da2fc03a)

点击折线图右上方的更多选项—排列轴，按月份升序排序

![image.png (1240×444) (wostatic.cn)](https://secure2.wostatic.cn/static/2kk9D2af15d3WFGZpu9PsY/image.png?auth_key=1655992838-d7ZsfRA9vEV6d8vEGvWKHc-0-091cdc3cf115f4d757e8f4f364f8194e)

这样我们就得到一份相对规整的最简单的折线图了

![image.png (731×304) (wostatic.cn)](https://secure2.wostatic.cn/static/iLWGVg7WsHfcEsZRifgXDT/image.png?auth_key=1655992847-oQPo8ojtQzDW4SLVeKcZM7-0-d36fc016e8ca345bbfed2fb4211e11b3)

## 进阶拆线图

上面的折线图无论是X轴还是Y轴都只有一个值，那如果X轴有多个值呢，比如年份和月份，这里直接使用了层次结构，层次结构的创建也很简单，这里就不再赘述。如果有不会的可查看PowerBI创建层次结构

![image.png (1212×556) (wostatic.cn)](https://secure2.wostatic.cn/static/21CZanDVTrb4rLDsdaZjwR/image.png?auth_key=1655992858-fGLAghQNaAR1Vrb8Wo35qE-0-a73ee8a0d1af5fe5d7dcc292e4a64b94)

这里折线图还有一个问题，就是X轴因为信息太多字体都倾斜，解决这个也很简单，关闭X轴的连接标签即可。

![image.png (1175×582) (wostatic.cn)](https://secure2.wostatic.cn/static/eWDCBixMXGwoMqVH39F3EV/image.png?auth_key=1655992868-XBP4niUoeu21BsFhoxEcu-0-63b1fc36ea5d303b4218a583413a32fb)

![image.png (1155×421) (wostatic.cn)](https://secure2.wostatic.cn/static/hNpVu5NBVPYM4tBVNG55nV/image.png?auth_key=1655992878-dmtLqxAxDfa6apsomawSwb-0-edc4fe32464f1135439eb40a8d004f0f)

如果还想调整X轴的风格线，只需在网格线中调整

![image.png (1152×423) (wostatic.cn)](https://secure2.wostatic.cn/static/b5TqUHSDvZaMUR7uPnqqCq/image.png?auth_key=1655992888-9kBoR77WhKBrJk5U68WZRF-0-df0995b3e225c835f7b2ca78f80818b0)

## 误差线

这个功能其实是三月份的更新中就加入的，也就是文章一开始看到的那张图，用的其实就是误差线，

为了动态控制，这里新建了一个参数，另外需要用到以下度量

```js
Upper = [Plan] * [上下限 值]

```

```js
Lower = [Plan] * -[上下限 值]

```

```js
Label = 
IF( 
    [Sales Amt] < [Plan] * 0.8 || [Sales Amt] > [Plan] * 1.1 ,
    [Sales Amt]
)
```

选择最右边的格式选项，会看到这里其实有很多功能，比如添加平均值线，中值线等等，这些都是以前就有的功能，设置起来也相对简单。我们找到误差线，应用于销售额，然后分别放置上下限度量，因为度量值写法的原因，这里与度量的关系要选择相对。效果如下

![image.png (1208×989) (wostatic.cn)](https://secure2.wostatic.cn/static/9CryEuRBY8aUb4xdq4r8ib/image.png?auth_key=1655992915-e85iDPCdtQH1Ws7GDiwPSk-0-ddb98e2feb97b0e8bfca49d4c81c7b49)

当然我们还可以选择显示为条形图，也可设置阴影区域的颜色。

接下来，就是添加目标销售额，并将其调整为虚线

![image.png (1171×593) (wostatic.cn)](https://secure2.wostatic.cn/static/w92B7bsnoF1JoSFykSkvYW/image.png?auth_key=1655992931-ryyaTiYqPxoEJ167Daw5pN-0-323fce3f04f3c362bd6bbfc306b1ecdc)

接下来就是标签的显示了，这里需要再定义一个新的度量,当小于目标值的80%或者高于目标值的110%就显示标记，因为太高或太低在真实生产中可以算是异常值，需要找下原因的。

```js
Label = 
IF( 
    [Sales Amt] < [Plan] * 0.8 || [Sales Amt] > [Plan] * 1.1 ,
    [Sales Amt]
)
```

这里要注意一定要将Label放到最上面，然后设置只有Label显示标记即可。

![image.png (1199×480) (wostatic.cn)](https://secure2.wostatic.cn/static/8virZSs3jmy8mM2ZYnQPE1/image.png?auth_key=1655992944-oMHB5gMS1u3guF2NzNa1Dg-0-e28701a1bec7fed74ecca6f2bcb966c3)

![image.png (1222×582) (wostatic.cn)](https://secure2.wostatic.cn/static/mQHB1kE2SEAxsbEadcaE9V/image.png?auth_key=1655992955-vQawmJoQATqGBAuh3XAUdr-0-dd76faa9ba924b4c9e5f0afceebc3354)

## 异常值

这个算是PowerBI AI功能中的一个，它会根据历史数据对未来数据有一个预测的上下限，然后超出上下限的会被标注为异常。但这里对放到X轴的数据有要求：

-   日期类型的值
-   日期层次结构的值（这个只有在打开自带的时间智能时才会有）

![image.png (1185×506) (wostatic.cn)](https://secure2.wostatic.cn/static/bybhaccX5hD3KesKrWYg5g/image.png?auth_key=1655992968-szFBxrQuTHujV2KAESCTRz-0-fb3a2a58484849c7611f12b85570510c)

将X轴换成日期字段，就可以使用查找异常功能了，

![image.png (1496×735) (wostatic.cn)](https://secure2.wostatic.cn/static/tmcCnL6Lb5K6e57P1H6iiv/image.png?auth_key=1655992978-vEEtmdtfaiYAZ2Q6pPwUv2-0-08b57e577e8de852cfce1e5ec1f76edc)

但这里又遇到了一个错误，就是当点击某个异常点来分析时出错，发布到云端仍然错误，查找官方文档，出没发现问题。

![image.png (1064×479) (wostatic.cn)](https://secure2.wostatic.cn/static/wJTSxXgKmr7nUmjmoQoHtt/image.png?auth_key=1655992987-BoCzrNR7vsKdQv3puJSBC-0-b2284e8380c5c0efe6df2dde1bf19c2a)

最后，实在是无奈之下打开了自动的时间智能

![image.png (551×548) (wostatic.cn)](https://secure2.wostatic.cn/static/kAX6oBwYZszLtpCtrTmkTV/image.png?auth_key=1655992996-jpzWWBMsieHkDLWcqkNXpu-0-8bcd89f5dc0cfb30078eb5ec4d97fc1e)

然后，重新拖放一张折线图，本地运行仍然出错。

![image.png (1390×473) (wostatic.cn)](https://secure2.wostatic.cn/static/fFizg7TaNhKdMx8xLE86o9/image.png?auth_key=1655993005-9UFU9xHTQNBz2Pn5TKkN6a-0-cf71a7f71fbb7a303ca220e118236ad2)

发布到云端，再来看结果。只能说就很微软。

![image.png (1667×895) (wostatic.cn)](https://secure2.wostatic.cn/static/kWTR8eS8Sqk6g4vVgYqh6C/image.png?auth_key=1655993013-2weudu1WEPgEWRsUHtaxyC-0-a8987774545cef3212e9839c9f14dd26)

## 预测

预测和查找异常是不能同时使用的，预测时可以选择向后预测的长度等，但具体是怎么预测的我们并不知道，老板问起来也不好回答，所以常用的预测可能还是用历史同比法预测会好些，简单易理解。

![image.png (991×424) (wostatic.cn)](https://secure2.wostatic.cn/static/9ykRQBuVjETC5cbYS5P27U/image.png?auth_key=1655993023-nSk3vH7ffaXcUidzQnjwGv-0-1bbfbca95ea42dda0b1dca9dbc67e027)

## 总结

折线图作为PowerBI的的内置图表，应该是用的相对较多的图表之一了，微软已经赋予了它很多功能，虽然某些功能暂时体验下来效果并不是很好，但全靠同行衬托，目前没有能和PowerBI势均力敌的产品，希望国产BI软件可以早日出现在Gartner的魔力象限中，也希望微软在出新功能的同时，别忘了修补各种Bug。

## 参考

[异常情况检测教程 - Power BI | Microsoft Docs](https://docs.microsoft.com/zh-cn/power-bi/visuals/power-bi-visualization-anomaly-detection)

[见解 - Power BI |微软文档 (microsoft.com)](https://docs.microsoft.com/en-us/power-bi/create-reports/insights#considerations-and-limitations)