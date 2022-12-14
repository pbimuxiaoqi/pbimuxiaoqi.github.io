---
created: 2022-06-19
tags: 外部工具 tabular-editor 模型翻译 
subject:
importance: 4
skilled:  3
status:
author:
url: https://www.wolai.com/muxiaoqi/mZrmuBhonH7oTa489MgQKn
cover: 
---
在上一篇文[[PowerBI使用Tabular Editor翻译报表模型]]有介绍怎么使用Tabular Editor来翻译报表模型文件，在文章最后说随着模型越来越复杂，表和度量越来越多，以及为了方便后期维护，需要使用文件来维护模型翻译的配置信息。

这就需要将表模型结构和度量值都导出来，这在先前的文件中已有介绍，可以回顾
[[用报表说明PowerBI报表]]，
[[Power BI模型优化利器之Power BI Helper]]

这里通过扩展工具Power BI Helper来导出数据。

![](https://secure2.wostatic.cn/static/6caTydu7d3nGxxWHcbGTjB/image.png?auth_key=1655642273-49akjtTjNrVxNi2An1oWtj-0-2994d04889fd34f9499b915dc9465efa)

在正式开始前，我们先来看下怎么在Tabular Editor中使用代码来进行模型翻译，比如我们要增加zh的翻译，可以运行以下代码

```C#
Model.AddTranslation("zh");

```

如果我们要给zh下的column1进行翻译，可以运行以下代码

```C#
Model.Tables["Table"].Columns["Column1"].TranslatedNames["zh"]="姓名";
```

![](https://secure2.wostatic.cn/static/bnysxRei3SMnSkd6ePCFUj/image.png?auth_key=1655642282-ueTdbZeZuujadWtN6acbTm-0-f23c97c308f0cf1428981e4b8ad67a26)

上面两段代码很简单，但就是这两段很简单的代码，可以让我们的工作后期维护起来很方便，现在打开先前导出的模型数据，稍做整理为如下

![](https://secure2.wostatic.cn/static/cFPCPZdZ7GgNHz4JdBxRZx/image.png?auth_key=1655642289-mcpRp88hTBH8s9fKvbQqnP-0-79af129ce9a970becfe41cab286d116a)

![](https://secure2.wostatic.cn/static/9RV9ZV8CfVhHnm4xwiVbGq/image.png?auth_key=1655642297-kEBkQ65bQiuokFHuuXYaKH-0-475b763119d5802aac09d4ac9669b87c)

这样我们就可以很直观地查看每一个对象的翻译情况了，后期维护起来方便很多了，当然还可以根据需要加上版本管理什么的，现在我们就可以把这些代码直接复制过去，然后批量运行运行，点击保存。

![](https://secure2.wostatic.cn/static/tLrues1q9vcnh89EsPoWar/image.png?auth_key=1655642305-dq2znrLRxaQ65B87KqAAym-0-3594e68a1eee6f1d61b707ee72f75533)

然后就是发布到web端修改显示语言来查看对应的效果了。

![](https://secure2.wostatic.cn/static/teTx5XKRUwxFvTwDzktUDy/image.png?auth_key=1655642313-2aQznoJgbw7FmHcJ7kcVgs-0-ac678dad9fe906e30e2c0368e9268790)

### 翻译度量

```js
Model.Tables["Measure"].Measures["Sales"].TranslatedNames["zh"]="销售额";
```

### 翻译度量值文件夹

```js
Model.Tables["Measure"].Measures["Sales"].TranslatedDisplayFolders["zh"]="销售额";
```

## 参考资料

[Analysis Services 表格模型中的翻译 | Microsoft Docs](https://docs.microsoft.com/zh-cn/analysis-services/tabular-models/translations-in-tabular-models-analysis-services?view=asallproducts-allversions)

[Useful script snippets | Tabular Editor Documentation](https://docs.tabulareditor.com/te2/Useful-script-snippets.html)

[How to speed up metadata translations in Power BI | THE SELF-SERVICE-BI BLOG (ssbi-blog.de)](https://ssbi-blog.de/blog/technical-topics-english/how-to-speed-up-metadata-translations-in-power-bi/)

[Power BI 添加翻译以重命名列 – XMLA、TOM、C# – 车轮上的数据 – Steve & Kristyna Hughes (wordpress.com)](https://dataonwheels.wordpress.com/2021/11/12/power-bi-adding-translations-to-rename-columns-xmla-tom-c/)