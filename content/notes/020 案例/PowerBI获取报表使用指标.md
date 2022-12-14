---
created: 2022-06-19
tags: 管理员 xmla 外部工具  powerbi-helper 
subject: 功能
importance: 2
skilled: 5
status:
author:
url: https://www.wolai.com/muxiaoqi/wAqrh6STaS6oSiARHX7jSD
cover: 
---

很多时候IT管理员想要查看报表的使用指标，从而统计出哪些报表使用率高，哪些用户使用率高。有好几种方法可以实现上述需求，可根据实际情况采用最合适的方案。

### 工作区中查看

进入工作区后，选择我们要查看使用指标的报表，选择查看使用指标

![](https://secure2.wostatic.cn/static/eofRDhxHwpSmYsTRgbwmC1/image.png?auth_key=1655636707-wH42hkYhTvHHgfRNnXb6Dp-0-57cfe9e9e9ed01f254a2712b5ac01ff0)

稍等片刻会进入到微软自动生成的使用指标报告，默认是最近30天的，无法查看再久远的数据。

![image.png (1524×628) (wostatic.cn)](https://secure2.wostatic.cn/static/5C7BobR3aHifPKHemz9QNv/image.png?auth_key=1655993195-p7ebq7mH11gBukUDDN8Aqw-0-0d97547fe74b1606f930cbcfb597eb1f)

我们也可以在打开某张报表后查看使用指标，具体操作如下

![image.png (1027×283) (wostatic.cn)](https://secure2.wostatic.cn/static/pzFr7jRj4HVnskRei9fpGh/image.png?auth_key=1655993203-mD7ksnpoeGqyGnNmVpBnoY-0-6b85ea67cfdb21f93effd108b8f08cc4)

### PowerBI数据集

这个实际上依赖于上面我们查看使用指标时生成的数据集，可以看到有很多使用指标的数据集，选择最新的，然后就可以更自由地打造自己需要的使用指标报表

![image.png (1050×550) (wostatic.cn)](https://secure2.wostatic.cn/static/wCez7SS4xw8sVykMcyCTGg/image.png?auth_key=1655993213-bRBsRbFD6TKs1xSe7F5ytC-0-d8d9dcc0567e176abcd4aa5b6c05ba69)

![image.png (874×493) (wostatic.cn)](https://secure2.wostatic.cn/static/2LL5y69ucBcBgnqJMykywi/image.png?auth_key=1655993221-uEzZUgaEMZGJsy1pw24Ybn-0-a819963103b748354ebe720caabbadc8)

### 审核日志

要使用该功能需要具有管理员权限，这里可以筛选日志类型和用户等，可以根据需要来筛选，然后查询结果可以导出以供其他分析使用。当然，如果想要自动化的下载，可查看官方文档

[Power BI Cmdlets reference | Microsoft Docs](https://docs.microsoft.com/zh-cn/powershell/power-bi/overview?view=powerbi-ps)

![image.png (926×385) (wostatic.cn)](https://secure2.wostatic.cn/static/qqBPAcLWN2BDZbyBtmEmdn/image.png?auth_key=1655993229-8NBMQmZZNV5vPkDgNEJHSL-0-48e090467149c361531b485207a9e0ac)

![image.png (1530×623) (wostatic.cn)](https://secure2.wostatic.cn/static/4NXTcRydTy9nWBgaVycDgm/image.png?auth_key=1655993240-h2YnTL7vLvMpkMi7bVDMcD-0-f1687ea336d4a3874cd4ee6a07915e8b)

### Power BI Helper

外部工具Power BI Helper也提供了下载审核日志的功能，要使用该功能需要创建一个应用，可参考以下内容

PowerBI REST API 进阶

Power BI模型优化利器之Power BI Helper

![image.png (1196×1008) (wostatic.cn)](https://secure2.wostatic.cn/static/8DYYtdy5H2d9FN66X58VYv/image.png?auth_key=1655993250-rGg53HSWdWdTp3kZs8zLWs-0-a269c688c8b548961312fd7a3d9c08eb)

## REST API

官方文档

[Admin - Get Activity Events - REST API (Power BI Power BI REST APIs) | Microsoft Docs](https://docs.microsoft.com/en-us/rest/api/power-bi/admin/get-activity-events)

如果想在PowerBI中使用REST API来获取数据，可参考以下文章

PowerBI 使用M函数调用Rest Api

毕竟还要写M代码，那有没有更简单的使用方式呢，当然是有的，已经有国外大佬将这些打包成的自定义连接器，PowerBI REST API 自定义连接器

![image.png (579×354) (wostatic.cn)](https://secure2.wostatic.cn/static/9TWmxN1kwJfq1eAQnxgeoc/image.png?auth_key=1655993258-myEmAePEbSrgdxKmHwicDq-0-cdc5c2d5b3da694121fe46d17005c803)

![image.png (849×630) (wostatic.cn)](https://secure2.wostatic.cn/static/koeKWokCJz3cXMWd42Cbgw/image.png?auth_key=1655993267-f1Q2wf9mZH8Wuu3D1Pxy4A-0-df3b68c8043057509420481683c7dda2)

## Azure云数据工厂

这个方案需要付费，好吧，所以并未实际使用过该方案，如果对该方案感兴趣，可参考以下博文

[使用数据工厂提取 Power BI 活动日志 – justB 智能](https://justb.dk/blog/2021/02/extracting-the-power-bi-activity-log-with-data-factory/)