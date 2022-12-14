---
created: 2022-06-19
tags: M查询 
subject: 功能
importance: 3
skilled: 4
status:
author:
url: https://www.wolai.com/muxiaoqi/s3yZ3wAZqPbEmMZHMcD7Lv

---
https://docs.microsoft.com/zh-cn/power-bi/connect-data/desktop-dynamic-m-query-parameters

PowerBI在4月的更新中正式加了动态M参数，官方说这非常适用于那些那些需要在不牺牲报表交互的情况下提升查询性能的用户。然而事实上这个功能只支持DirectQuery连接的数据源。然而因为性能的关系，其实是在商业报表中我们一般是不建议采用这种方式，虽然直连可以实现伪实时更新，但是不支持复杂的计算，很难满足业务需求。

先不说应用场景，我们还是来体验下这个功能。

## 导入数据

首先采用DirectQuery方式导入两张表，这里使用的是官方的示例数据，如果还没下载该示例数据库的用户可到官方下载：

[AdventureWorks sample databases（AdventureWorks 示例数据库） - SQL Server | Microsoft Docs](https://docs.microsoft.com/zh-cn/sql/samples/adventureworks-install-configure?view=sql-server-ver15&tabs=ssms)

![](https://s2.loli.net/2022/06/21/sjHqbhAIyO7PXlz.png)


## 新建参数

在新建参数前我们先来做一个操作，只保留销售表前100行的数据，这样接下来就会方便我们应用参数值

![](https://s2.loli.net/2022/06/21/DP47u2TjyABbNZx.png)

新建一个参数，注意这里我们使用的其实是文本类型。

![](https://s2.loli.net/2022/06/21/2r7Szaj8BLumpe1.png)


在销售表中应用参数，选中销售表，选择高级编辑器，替换为刚建立的参数，因为我们前面参数创建的是文本，所以这里需要加一步，将参数转成数字。

![](https://s2.loli.net/2022/06/21/2r7Szaj8BLumpe1.png)

既然是动态查询，那我们肯定还需要一张还切换查询显示的行数的，所以接下来新建一张表，这里就直接输入数据就好了。这里我们新建的做为切片器用的表里TopN列是文本，这也是为什么前面我们参数也是文本的原因，因为后面还要将该列与参数进行绑定。

![](https://s2.loli.net/2022/06/21/M8nIJshYLkX2RcF.png)


因为最终我们还需要使用TopN中的值来传递到销售表的查询中去，所以还需要对销售表的代表进行改造，（本来想设置为选择More时是全部数据的，但不好录制gif，就改成了1）

![](https://s2.loli.net/2022/06/21/COfSj34Y6mIalJc.png)


关闭并应用回到前端页面

## 配置参数表

切换到模型视图，选中TopN表，选择TopN列，然后高级，绑定到参数，选择我们创建的Top参数。

![](https://s2.loli.net/2022/06/21/COfSj34Y6mIalJc.png)

回到画布，查看效果

![](https://secure2.wostatic.cn/static/iZBywUiDGjKAbhZPFroh2K/%E5%8A%A8%E7%94%BB.gif?auth_key=1655818107-bCMB9o7nYoGZ8LcSUjsR8h-0-f4c84e0fdbb5da0e9893160bb16546a7)

## 扩展阅读

[[PowerBI管道部署]]