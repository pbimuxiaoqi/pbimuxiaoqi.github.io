---
created: 2022-06-19
tags: 外部工具 
subject:
importance:
skilled:
status:
author:
url: https://www.wolai.com/muxiaoqi/o9Hm9TqkCqv4eJF6v1iygL
cover: 
---
PowerBI是目前最好的BI工具，也是最好的BI解决方案，更是最好的BI软件生态，但这不是说它已经很完美了，而是相对于竞品而言，事实上PowerBI还有很多需要改进的地方。

Python是目前最好的数据科学语言，虽然有前辈R,也是后来的Julia，但挡不住Python社区的强大，有太多功能强大的库，短短的代码就可实现了其他语言需要写很长很长的功能。

那么，PowerBI如果遇到Python会擦出怎样的火花呢？

## 数据处理

虽然PowerBI有Power Query加持可以做轻量的ETL，但是还是可能会遇到无法处理的情况，但时候Python可能是所有解决方案中上手最简单的，Python有两个强大的库可以用来清洗数据Numpy和Pandas。

![image.png (1027×731) (wostatic.cn)](https://secure2.wostatic.cn/static/cnHVCcWNKHDtUknsdPHokz/image.png?auth_key=1655993675-d3UMDmhWGqrVshBradZJMz-0-485fb81d6771f7c354c58355c2e88b40)

## 导出数据

PowerBI对数据导出是有限制的，当我们想导出更多的数据的时候，当然分页报表会是最好的选择，但是这需要高级容量工作区才行，对于没有高级容量工作区的其实就可以借助于Python了。虽然XMLA方式也是高级容量工作区才有的功能，但是Python可以连接本地PowerBI文件的里的数据集，从而将数据导出到CSV中，CSV是没有行数限制。

## 可视化

PowerBI有几百个图表，可能还是无法满足我们的需求，虽然它支持Python视觉对象，但是PowerBI中的Python视觉对象并不是所有的都支持，比如我最喜欢的pyecharts。(google colab、deepnote、 飞桨都有提供Jupyter Notebook环境来供使用，基本可满足个人使用场景)

![image.png (1602×969) (wostatic.cn)](https://secure2.wostatic.cn/static/fzZ2g49EGLJGRrWDQk1E5S/image.png?auth_key=1655993685-cWYeheC9oNRzUAcNQBdNXs-0-911963f2dca9164d8f76eb23a56436aa)

## 数据刷新

前面也写过很多文章来介绍PowerBI REST API，借助于Python还可以刷新数据，而且通过接口刷新数据是没有次数限制的，这样就可以做到一个伪实时的报表，不过在刷新数据时要注意不要造成任务堵塞。

![image.png (1170×551) (wostatic.cn)](https://secure2.wostatic.cn/static/Q2yNEb5VGQT5rz6WPRHjH/image.png?auth_key=1655993694-79sCFRzhKzwxdLGWcJqFpr-0-8953acf3f43534781f820fd4aedd0761)

## 发送邮件

这个其实是朋友给提的一个需求，客户想每个月把报表中数据分发给相应的供应商，这些供应商是没有他们域内的PowerBI账号的，前面也说了，Python可以通过XLMA或者本地文件的方式连接报表中的数据集，那么就可以写个Python脚本来连接数据集然后把数据分发给不同的客户。

当然还可以把发送邮件的脚本嵌入到报表中，比如日报中连续3天销售同比是下降的就发送邮件，只是第一次是触发发送邮件操作。

## 参考

[数据集 - 执行查询 - REST API（Power BI Power BI REST API） |微软文档 (microsoft.com)](https://docs.microsoft.com/en-us/rest/api/power-bi/datasets/execute-queries)

[Refresh a Power BI Dataset with Python – PBI Guy (pbi-guy.com)](https://pbi-guy.com/2022/01/07/refresh-a-power-bi-dataset-with-python/)

[Python 作为 Power BI Desktop 的"外部工具"：第 1 部分 - DataVeld](https://dataveld.com/2020/07/20/python-as-an-external-tool-for-power-bi-desktop-part-1/)

[Refresh All Your Power BI Datasets with Python (morioh.com)](https://morioh.com/p/05d571b62d36)

[通过 Python Jupyter Notebook 中的 XMLA Endpoint 访问 Power BI 数据集|桑迪普·帕瓦尔 (pawarbi.github.io)](https://pawarbi.github.io/blog/ppu/xmla/powerbi_premium/premium/python/jupyter_notebook/2020/12/11/Accessing-Power-BI-Datasets-via-XMLA-Endpoint-in-Python-Jupyter-Notebook.html)