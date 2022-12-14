---
created: 2022-06-19
tags: 工具 azure-data-studio
subject:
importance: 1
skilled: 3
status:
author:
url: https://www.wolai.com/muxiaoqi/iwAxGN3xw3ev3KXQxVmRz9
cover: 
---

如果你是Jupyter notebook的重度用户，同时又是SQL的轻度用户，那么一定不要错过Azure Data Stuio。

它是一个跨平台的数据库工具，可以在Windows、Mac、Linux上使用。既然是一个数据管理工具，自然少不了和微软自家的SSMS(SQL Server Management Studio)来进行比较了，这里直接引用官方的介绍：

**如为以下情况，请使用 Azure Data Studio：**

-   主要是编辑或执行查询。
-   需要能够快速绘图和直观显示结果集。
-   可通过集成终端使用 sqlcmd 或 PowerShell 执行大多数管理任务。
-   对向导的使用需求较少。
-   不需要实施深层次的管理或平台配置。
-   需要在 macOS 或 Linux 上运行。

**如为以下情况，请使用 SQL Server Management Studio：**

-   需要实施复杂的管理或平台配置。
-   要实施安全管理，包括用户管理、漏洞评估和安全功能配置。
-   需要使用性能优化顾问和仪表板。
-   使用数据库关系图和表设计器。
-   需要访问经过注册的服务器。
-   需要利用实时查询统计信息或客户端统计信息。

![](https://secure2.wostatic.cn/static/KM42ehJRHkzdHJEN7BJGQ/image.png?auth_key=1655633812-sZPYSjWBUwDCHsN9n31Kpe-0-df192ad963718c07824e311b529bb8cb)

![](https://secure2.wostatic.cn/static/pVcSDy3LiYNHVCFKya1Uoa/image.png?auth_key=1655633818-fs4zZhAZ8JtXJUp8o8Lern-0-082c7b9218012ab22bb802f1bae9e6a1)

当然如果只是能运行sql命令和简单的可视化，那么Navicat会是更好的选择，毕竟Navicat可以管理几乎所有的主流数据库，并且现在也支持做可视化报表了

![](https://secure2.wostatic.cn/static/sf35uWv3yi7bfTQPc1WdTC/image.png?auth_key=1655633827-ieqNpd6QE8Jtg7ZFvUGSJ9-0-ead40cd448db1efc448986904dfbc13d)

## 支持python和R

那么Azure Data Studio 还有哪些功能呢？支持Python，这是我最喜欢的功能了，毕竟早已习惯了在Jupyter Notebook中写Python代码，可以实时看到代码的运行效果。另外前面也介绍过使用Python连接PowerBI数据集，那这就多了更多的可玩性。但是仍有些不足，如果每个Notebook只能指定一种语言，而不能不同命令行不同的执行语言。

![](https://secure2.wostatic.cn/static/3YuTmFixiuDedu43zwrTMU/image.png?auth_key=1655633839-vr9uj19MPxJ8G8scHctRdY-0-b5e9bae2c973a5107a20f4fe3144f586)

## 丰富的扩展

这大概是微软家产品的必备功能了，也不知道是不是因为程序员懒得把这些功能集成到软件本身，所以通过才支持安装扩展的方式，让其他人来开发，但确实是方便了我们这些普通用户。

![](https://secure2.wostatic.cn/static/myJW91jnUV6dUeGy2QZn92/image.png?auth_key=1655633846-d4xW13XdcG6quDEipCy3WT-0-13b4c00e9b8166d9d7fe7ce34a3524d6)

## 参考

[下载并安装 Azure Data Studio - Azure Data Studio | Microsoft Docs](https://docs.microsoft.com/zh-cn/sql/azure-data-studio/download-azure-data-studio?view=sql-server-ver15)

[什么是 Azure Data Studio - Azure Data Studio | Microsoft Docs](https://docs.microsoft.com/zh-cn/sql/azure-data-studio/what-is-azure-data-studio?view=sql-server-ver15)

## 提醒
> <font color="red">若直接安装扩展报错，则下载后，通过本地文件安装</font> 