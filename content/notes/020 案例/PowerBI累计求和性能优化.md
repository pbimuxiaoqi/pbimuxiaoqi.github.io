---
created: 2022-06-19
tags:
subject:
importance:
skilled:
status:
author:
url: https://www.wolai.com/muxiaoqi/5hxJ7xTyso6C6DcE1rUvcS
cover: 
---


其实不管什么何种语言的开发，性能优化都是必不可少的。比如某水果手机，明明运行内存才4G却比运行内存12G或者更高的安卓还要流畅，因为系统和软件优化做的好。同样的，要想让PowerBI报表达到更好的展现效果，我们也需要做一些优化，而这些优化操作是有规律可循的。

作为优化操作的开篇，先讲一个累加求和的优化，这也是我们在ABC模型中常用的优化方法。

已经存在基础度量值Sales Amount

```js
Sales Amount =  
SUMX ( Sales, Sales[Quantity] * Sales[Net Price] )
```

接下来对产品的销售额求累加和，通常我们计算累加和的思路都是筛选出Sales Amount大于等于当前产品销售额的表，然后再求总计，代码如下：

```js
Cumulated Sales = 
VAR CurrentProductSales = [Sales Amount]
VAR BetterProducts =
    FILTER (
        ALL('Product'),
        [Sales Amount] >= CurrentProductSales
    )
VAR Result =
    CALCULATE(
        [Sales Amount],
        BetterProducts
    )
RETURN
    Result
```

这样写没有任何问题，可以得到正确正确答案，我们来看下性能

![](https://imgedit.newrank.cn/edit/upload/photo/2021/08/09/350497d7c8be4815ab01f0d33ede2d7e.jpg)

结果并不能让人满意，如果数据量变大，这个结果会更糟糕，那么我们应该如何优化呢？

先来看一道简单的数学题，1+2+3...+100等于多少，你可能会脱口而出5050，但我们最开始是怎么快速得到这个值的呢？没错，（1+100）*100/2，通过首尾相加的方法减少了我们去累加计算的次数，同样借助于这个思想我们可以进行相应的代码优化。

-   先对产品表进行聚合，算出每个商品的销售额
-   再对聚合后的表进行移动累计计算

```js
Cumulated Sales 2 = 
VAR OfferSum =
    ADDCOLUMNS (
        ALLSELECTED ( 'Product'[Product Name] ),
        "@Amt", [Sales Amount]
    )
VAR CurrentOfferAmount = [Sales Amount]
VAR BetterProducts =
    FILTER (
        OfferSum,
        [@Amt] >= CurrentOfferAmount
    )
RETURN
    SUMX (
        BetterProducts,
        [@Amt]
    )
```

具体表现如何呢，我们来看结果

![](https://imgedit.newrank.cn/edit/upload/photo/2021/08/09/9bdeeafd7b744f51bae1e8b5d27c1cf8.jpg)

性能有了提升。

让我们来回顾下优化的思路，<font color="red">减少迭代</font>，这很有用，特别是在做其他更复杂的性能优化的时候，得到的性能提升甚至是几十倍上百倍。