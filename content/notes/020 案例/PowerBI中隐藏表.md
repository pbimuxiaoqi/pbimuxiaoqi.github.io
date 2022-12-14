---
created: 2022-06-19
tags: 外部工具 tabular-editor  隐藏表
subject:
importance: 3
skilled: 4
status:
author:
url:
https://www.wolai.com/muxiaoqi/87UXXZ1g1XWCQHzMbd4JvQ
cover: 
---

有时可能会将模型的权限开放给用户，让用户直连模型然后自主分析，这同时也会涉及到一个问题，有些表并不想让用户看到，

比如最常见是财务报本中成本表不会给其他用户权限查看。但是不同的隐藏方式，实际效果是不同的，

-   如果是通过PowerBI数据集连接，建议是在Tabular中隐藏掉
-   如果是通过SSAS连接，直接在SSAS中隐藏掉就好

### PowerBI文件中隐藏

在文件中隐藏后仍然可以查看到表数据的，

![](https://s2.loli.net/2022/06/21/UO8LyeDA5uCQMBr.png)


即便我们是通过PowerBI数据集连接，仍然可以看到数据

![](https://s2.loli.net/2022/06/21/er74p2PZjoWl1xL.png)


### SSAS中隐藏

直连表格模型，会发现无法查看隐藏的表

![](https://s2.loli.net/2022/06/21/Ak9Z7jtrGCb3Nh4.png)


![](https://s2.loli.net/2022/06/21/ths9VcyJeN47bxR.png)


### Tabular Editor中隐藏

即使回到原始PBI文件，也无法查看到该表，但是由于表被隐藏，和该表有关的度量值中表会高亮显示，但不影响度量值的运行

![](https://s2.loli.net/2022/06/21/2LR6hW9TigwStKf.png)


![](https://s2.loli.net/2022/06/21/2LR6hW9TigwStKf.png)

连接PowerBI数据集查看效果

![](https://s2.loli.net/2022/06/21/d3a5MxFE4NVbOXn.png)
