---
created: 2022-06-19
tags: 外部工具 xmla 数据集
subject: 
importance: 3
skilled: 3
status:
author:
url: https://www.wolai.com/muxiaoqi/qwmAgJ4hEbaHhgTrqKfhru
cover: 
---
前面在介绍过当[[PowerBI遇到了Python]]会擦出怎样的火花，那么今天就来介绍下使用Python来连接PowerBI数据集。

## adodbapi库

首先安装这个库

```Python
pip install adodbapi
```

### 连接工作区中数据

如果是高级容量工作区，则可以通过直接连接线上工作区中的数据集，数据集的连接字符串获取方式可参考

[[PowerBI数据集单表刷新（一）]],这里还有点要注意，连接方式中并没有指定账号信息，运行代码时会弹框让填写账号和密码。

![](https://secure2.wostatic.cn/static/UShYYD7zbc63TeuSnD3ZE/image.png?auth_key=1655628626-3gZjL2AdQRkdaMZ4w43YUt-0-aec4b4bd569aaf20a93f57e6502b3b66)

### 连接本地文件

使用dax studio来获取报表文件的连接信息

![](https://secure2.wostatic.cn/static/mrvpTBjgTxackVXnZzw6AC/image.png?auth_key=1655628649-jKUFEXe4ehhBSVoo3W1ABa-0-ad1e1ab3480012c433bd3d9d9b10ef07)

其实，不仅可以运行dax查询语句，也可以运行DMV,详细可参考[[PowerBI 中使用DMV获取数据]]

![](https://secure2.wostatic.cn/static/gDwMrqfb9dBbwVgztMVZRv/image.png?auth_key=1655628656-fMhSBEdjmQF2az4wub2Tet-0-882c6429b975a4c0db772a9940b2a411)

虽然，我们如果是高级容量工作区则可以使用XMLA方式连接数据集，但这种方式对性能有一定要求。所以更推荐使用连接本地文件的方式。

## pythonnet

这是另一个库，也可实现类似的功能，

先安装，如果pip安装有问题，可从附件下载解压后，进解压目录安装

```Python
pip install pythonnet
```

![](https://secure2.wostatic.cn/static/w22y7oEzQM1TBgQ3vXLBdD/image.png?auth_key=1655628664-sdUpp65BdV6qzDxkuCAjQE-0-ba1a6b41ea58c2722b89515a17c85abb)

另外有国外大牛封装了一个库[ssas_api](https://github.com/yehoshuadimarsky/python-ssas)可供使用，可从附件下载下来放到代码所在目录或者直接放到python.exe的根目录，我是使用的anaconda安装的，所以直接放在了anaconda的安装目录

![](https://secure2.wostatic.cn/static/rqzRYxivJHuKae3MgkvEtW/image.png?auth_key=1655628672-tyWcrMdLSvNRxdhJt6FBqg-0-2f145dc96a4a9566ab575dc21b3f39d3)

### 查看工作区中所有数据集信息

![](https://secure2.wostatic.cn/static/sxgkamuacDuUjdTKs9L3gY/image.png?auth_key=1655628680-bjHzg4TdUeoo7yAyVwqkgF-0-0245be239680b964a4994f9a43682c25)

### 连接本地文件

当然，这个库也可以连接本地文件

![](https://secure2.wostatic.cn/static/4BNBbxpoLBzS8QsC6WEA47/image.png?auth_key=1655628687-bwT5oER2e4WZttRz1vBtxf-0-07b26470863c4ff3fb49ee754a853e82)

## 总结

这里也是举了两个简单的例子，借助于这两个库还可以做很多事情，比如导出数据，比如和seaborn等其他可视化库结合使用做可视化等等，这具体要看你的需求是什么了。工具就在这里，要看我们怎么使用了。

## 参考

[Jupyter as an External Tool for Power BI Desktop (Python Part 4) - DataVeld](https://dataveld.com/2020/08/17/jupyter-as-an-external-tool-for-power-bi-desktop-python-part-4/)

[pythonnet/pythonnet: Python for .NET is a package that gives Python programmers nearly seamless integration with the .NET Common Language Runtime (CLR) and provides a powerful application scripting tool for .NET developers. (github.com)](https://github.com/pythonnet/pythonnet)

[yehoshuadimarsky/python-ssas: A proof of concept to integrate Python and Microsoft Analysis Services (github.com)](https://github.com/yehoshuadimarsky/python-ssas)