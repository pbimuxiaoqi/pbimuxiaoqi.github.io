---
created: 2022-06-19
tags: 其他 
subject:
importance: 2
skilled: 5
status:
author:
url: https://www.wolai.com/muxiaoqi/gHK4EzVjn5MxWo9Am4peLR
cover: 
---

这里也先强调下原则：

-   能够在上游就对数据做处理的一定要在上游处理
-   上游没办法处理的在Power Query中处理
-   最后才是计算表或计算列来处理

熟悉PowerBI的都知道，它不止是一个BI工具，它更是一套BI解决方案，包含了BI的各个过程，以下是它和传统的SQL Server 报表进行比较，可以看到PowerBI算是集微软众多产品的特长于一身，特别是现在PowerBI又和Power Apps、Power Automate等其它产品进行了集成，又向BI生态迈出一大步。

| 类别         | **SQL Server ** | **Power BI**                     |
| ------------ | --------------- | -------------------------------- |
| **数据**加载 | SSIS            | Power BI Query Editor            |
| **数据**模型 | SSAS (SSDT)     | Power BI Query Editor / Power BI |
| 指标         | SSAS (SSDT)     | DAX                              |
| **报表**     | SSRS            | Power BI                         |
| **分**发     | SharePoint      | PowerBI Server                   |

PowerBI功能这么多，肯定是要使用的，比如一些没有IT支持的项目，分析师就可以使用PowerBI中PQ功能进行简单的ETL操作，事实上在我初次接触PowerBI时，我也时常用它来做它来做一些ETL操作，这确实很方便。在这之前我都是用Python来清洗数据，之后再导入到数据库中或者导出成CSV文件继而让PowerBI使用。

可是，随着做的项目越来越多，项目越来越大，反而越来越不建议使用PowerBI来进行数据清洗了，因为这些清洗后的干净数据只存在于PowerBI文件中，并没有在数据仓库中，下一次若要使用这些数据做其他分析，还要再清洗一遍。

当然，这还不是最为严重的问题，最为严重的问题是，基于某一数据我们做了很多小的分析报告，当有一天想要把这些报告统一起来到一个文件时，可能会发现先前所谓的干净数据只是相对于当前文件而方的。举个简单的例子，
| 报表名 | 源数据         | 清洗后         |
| ------ | -------------- | -------------- |
| 测试A  | （小明，001）  | （小明， 001） |
| 测试B  | （小王， 002） | （小王， 001） |
| 测试C  | （小明，001）  | （小明， 002） |
| 测试D  | （小明，001）  | （小张，002）  |


其实，上面这个例子，情况还算是比较好解决的，因为所有报表使用的都是一个来源，只是清洗成了不同的样子；还有可能这些报表数据只是格式相同，但来源不同的库，就像这样。

![image.png (961×587) (wostatic.cn)](https://secure2.wostatic.cn/static/ryGGNgaZNa6NsHHzp7cDDy/image.png?auth_key=1655993330-bWpwNMZWZwQ74Jcd9TZRhi-0-d86ea3f96fd2da072f40f63a31b5cbd2)


特别是如果这些数据又做用来维度表使用时，那简直是一个灾难。

通常企业级BI数据流程架构如下，PoewerBI只做数据呈现，随着PowerBI数据集，部分项目也会在PowerBI中进行数据建模，从而达到前后端分离的目的。不管是哪一种，都不会在PowerBI中进行大量的数据清洗操作，都是需要使用数仓中干净的数据。

![](https://secure2.wostatic.cn/static/ryGGNgaZNa6NsHHzp7cDDy/image.png?auth_key=1655634385-buJcQ88rB8FUNzeerJCcMp-0-0d2789a3a1ca2c735b590b2d14a1da2a)

今天的内容可能有些枯燥，加上文笔有限，如果没有在项目中踩过类似的坑，可能很难理解，不过还是要再次强调下，企业级项目中不推荐在PowerBI中进行大量的数据清洗操作，PowerBI连接的就应该是最干净的数据。