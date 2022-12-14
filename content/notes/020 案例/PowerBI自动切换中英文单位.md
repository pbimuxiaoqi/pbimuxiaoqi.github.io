---
created: 2022-06-19
tags: 计算组 字符格式化 单位
subject: 案例
importance: 4
skilled: 4
status:
author:
url: https://www.wolai.com/muxiaoqi/6sTvhdQJbv5kmVnWfv2fxE
cover: 
---

通常我们在做报表的时候，会给报表设置一个统一的单位，比如百万，这样整个报表的数据看起来就比较规整，但是这样也会出现另一个问题，比如某个值是100，那这样格式化后显示就是0，但事实上它并不是0，只是值相对比较小而已。那有没有一个方法可以根据数值的大小自动来显示单位呢？

答案是肯定的，也正是很多人想到的那样，用计算组。

先来回顾下，在计算组出来之前我们是怎么来切换报表的单位的。首先会新建一张单位表

```js
Unit = 
SELECTCOLUMNS(
{
    ( "None" , 1 ) , 
    ( "K" , 1000 ) , 
    ( "W" , 10000 ) ,
    ( "M" , 1000000)
} , "Name" , [Value1] , "Value" , [Value2] )
```

新建度量如下：

```js
Sales Amount := SUMX ( Sales, Sales[Quantity] * Sales[Unit Price] )

Sales Amount Unit = [Sales Amount] / SELECTEDVALUE( 'Unit'[Value], 1 )

```

图表显示效果如下：

![image.png (714×388) (wostatic.cn)](https://secure2.wostatic.cn/static/rp9visP3uf8zsCh9o3nG3Y/image.png?auth_key=1655993084-pBUFJhHnTXVEWDgTjEvWZM-0-30f89e55df63105291c40addb075c950)

可以看到数据已经显示了根据选择的单位进行了格式化显示，但是这样会存在一个问题，比如我们导出数据，那么导出的数据也是除以10000后的，但是文件中并没有标注该值的单位，这有可能引起不必要的问题。

![image.png (538×251) (wostatic.cn)](https://secure2.wostatic.cn/static/mNY4FXTmvL4DxBaWAHCiKZ/image.png?auth_key=1655993096-axqZ8sRejwxKvZnv2dm8Qg-0-4ef0307d6c5a8033d50c90747e70d150)

接下来就是今天的重点了，使用计算组来对数值的显示进行格式化，打开Tabular Editor,右键新建一个计算组

![image.png (1140×460) (wostatic.cn)](https://secure2.wostatic.cn/static/m6YrF8c6MvqD9iRrqJbP8a/image.png?auth_key=1655993104-8PrUD3EV9FQ5E3KiBwoCM6-0-ab3ec1b83b65fdbbcf0d0dfe55757725)

![image.png (786×387) (wostatic.cn)](https://secure2.wostatic.cn/static/t2bKqy7Gj6xXi1CBYYoA5F/image.png?auth_key=1655993111-b8E4DsELQjSqy7c3UmK8Lc-0-c6fb990af13075606b343d2ffdad33e3)

效果如下：

![image.png (625×324) (wostatic.cn)](https://secure2.wostatic.cn/static/botXqCoDGJhjVs7jtP84YW/image.png?auth_key=1655993120-gsFGh2Ri8pVPnpX7nfJvCo-0-57df705610915081c38e4d1484f12c15)

导出数据效果如下，数据还是未格式化前的样子。

![image.png (365×234) (wostatic.cn)](https://secure2.wostatic.cn/static/dgSEyj9bFdws4rYJ8XfhPp/image.png?auth_key=1655993129-uccT89SBfVzBJbdVX5wnMY-0-4caed09577922d2c7f31b7158af87a92)

再来看上面计算组中的格式表达的写法,其实原理也很简单，用到了自定义格式字符，具体可见官方文档

[FORMAT 函数 (DAX) - DAX | Microsoft Docs](https://docs.microsoft.com/zh-cn/dax/format-function-dax)

-   （,）千分位符
-   （.）小数点占位符
-   （#）占位符，有值时才显示
-   （0）占位符，有值时显示该值，无值时显示为0

```js
VAR V = SELECTEDMEASURE ()
VAR F =
IF(
    SWITCH (
        TRUE (),
        V >= 1E9, "##0,,,.00 G",
        V >= 1E6, "##0,,.00 M",
        V >= 1E3, "##0,.00 K",
        "0.00"
    )
)
RETURN
    F
```

上面代码无论数值是否带有小数，都会保留两位小数，若要自适应当数值是整数时显示为整数，有小数位时才保留小数，可修改为如下：

```js
VAR V = SELECTEDMEASURE ()
VAR F =
    SWITCH (
        TRUE (),
        V >= 1E9, "##0,,,.## G",  
        V >= 1E6, "##0,,.## M",
        V >= 1E3, "##0,.## K",   
        "0.##"
    )
RETURN
    F
```

这时，我们可以做进一步的变形，从而做到单位进行中英文的的切换。

![image.png (698×336) (wostatic.cn)](https://secure2.wostatic.cn/static/9anrvNqxMQRaUse1vD6vMh/image.png?auth_key=1655993144-t6dyfD6NpkpX4ZpsqxSbnH-0-a2d41f3ac89be645927bcc19020dfb1d)

这时，也许有人会问，如果有是百分比的度量呢，接下来进一步改进格式表达式

```js
VAR V = SELECTEDMEASURE ()
VAR F =
IF(
    SEARCH( "%", SELECTEDMEASURENAME(), 1, 0) = 0,
    SWITCH (
        TRUE (),
        V >= 1E9, "##0,,,.00 G",
        V >= 1E6, "##0,,.00 M",
        V >= 1E3, "##0,.00 K",
        "0.00"
    ),
    "0.00%"
)
RETURN
    F
```

![image.png (774×365) (wostatic.cn)](https://secure2.wostatic.cn/static/nmm2DRXmXsr9EfS6iyyWaf/image.png?auth_key=1655993156-mkyKvzTGAytMpjpRwciVd6-0-4af7dbd2523ddbce0c0419c02ca2c2a0)

## 扩展阅读

[[控制度量值显示格式]]

[[控制计算组中的格式表达式]]

[[日期列的常见格式]]