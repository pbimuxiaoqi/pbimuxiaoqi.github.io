---
created: 2022-06-19
tags: dmv xmla dax-studio 外部工具 
subject:
importance: 4
skilled: 4
status:
author:
url: https://www.wolai.com/muxiaoqi/teRj8HdP5JwoYLvedwA8Fi
cover: 
---

最近手上有件工作着实挺无聊的，在Excel统计用户及相关报表权限信息,因为历史遗留原因，在好多地方都有统计，然后统计的还都不全，这维护起来就挺难受，虽然不难，但很无聊，所以就想明明报表里有权限的信息，后台有用户的信息和用户报表的权限信息，为啥还要手工再去维护实时性这么差的Excel呢？

用户的基本信息和用户对应的报表角色信息可以找后台要，给开一个只读账号，在视图里把数据组合起来就好，那报表里具体角色的权限语句呢？

-   Dax studio中使用DMV功能导出来
-   Power BI Helper 中导出来（[[Power BI模型优化利器之Power BI Helper]]）
-   Document Model 中导出来（[[用报表说明PowerBI报表]]）

但是，问题又来了，通过以上三个工具并不能实时获取数据，需要打开报表手动导出来，十几份报告，每一次更新报告都要重新导出着实是太麻烦了。

有没有办法可以实时获取呢，这时，首先想到的其实还是通过DMV模型获取，因为Power BI Helper 和Document Model底层都是通过C#代码来获取这些信息的，这对于我来说是有困难的，这时想到了通过SSMS连接工作区时是可以看到数据集的角色等信息的啊（[[PowerBI数据集单表刷新（一）]]），其中也有使用XMLA，通过Tabular Editor来刷新数据，那理论上PowerBI里也是可以实时获取这些信息的

先来看下通过DMV查看权限语句的表达式

![](https://secure2.wostatic.cn/static/84FHbUvqBmy1dYMyJr6vBc/image.png?auth_key=1655628984-h2uLWzA1XrJUnuRw5ZP3m5-0-10231065eba4c875b3a6803685f0a492)

接下来在PowerBI中使用DMV查询，先获取工作区连接信息

![](https://secure2.wostatic.cn/static/c3SJxACxDrcJpA4A5689b5/image.png?auth_key=1655628991-ep3xQHaHHMeaFN2MawYtkp-0-930f1ac01ed1465a2893a8a47b8f996a)

接下来在PowerBI中连接数据源，服务器填写工作区连接，数据库填写报表的数据集名称

![](https://secure2.wostatic.cn/static/nMDcQjjSgisbcYtKHRvU4w/image.png?auth_key=1655628998-o7NE4YZmGoDZCrStyKsouF-0-b019cac0a53e1e780e160f281f52477f)

登录账号

![](https://secure2.wostatic.cn/static/e6TY7RvMcEWSou9CWfNXma/image.png?auth_key=1655629008-nkvJ5MEYoJC5eGRT3nZaks-0-89ef377b7f8c5faa80794cd5eda4494a)

接下来就可以看到数据了

![](https://secure2.wostatic.cn/static/wTG9t5Hvy9X6eDPwqAgzbK/image.png?auth_key=1655629016-2dbGNiSSQ51y7bNybgpMWu-0-2f88b1ad86791bcece7ea0ec30164a16)

但是这里只用权限表达式，没有相应的表和角色信息，所以还需要导入其他信息，代码如下

```JavaScript
select * from $SYSTEM.TMSCHEMA_TABLES

select * from $SYSTEM.TMSCHEMA_ROLES

```

这些语句也没必要记，在Dax studio中通过关键字查询然后试一下结果就好了

![](https://secure2.wostatic.cn/static/btJmWT7BcWyfrdq9nmunfj/image.png?auth_key=1655629023-ecXJwyGAyfzWvHhzpv6vNP-0-a1561cd16895ecdd565beeb499a3415c)

至此我们就导入完成了报表中权限部分需要的信息

![](https://secure2.wostatic.cn/static/a2KSFRP5XrL3KRJohizHzL/image.png?auth_key=1655629030-tsAN7EQJ6x1WuyXdGTwCa2-0-77de505b042ce5063b3020de635141a0)

## Power Shell中使用

[自动执行 Power BI 表达式文档|作者：Martijn Lentink |中等 (medium.com)](https://medium.com/@martijnlentink/automate-your-power-bi-documentation-33951525c381)

## 官方文档

[动态管理视图 (DMV) Analysis Services | Microsoft Docs](https://docs.microsoft.com/zh-cn/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services?view=asallproducts-allversions)

[在 Power BI 中使用 XMLA 终结点连接和管理数据集 - Power BI | Microsoft Docs](https://docs.microsoft.com/zh-cn/power-bi/admin/service-premium-connect-tools)