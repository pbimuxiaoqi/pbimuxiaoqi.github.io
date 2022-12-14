---
created: 2022-06-19
tags: 动态轴 
subject:
importance: 4
skilled: 5
status:
author:
url: https://www.wolai.com/muxiaoqi/uDNG4zJUoyHAQ3UMvi5qLv
cover: 
---

有时为了节省报告页面空间，或者业务人员的特殊需求，需要图表的维度可以动态切换，比如筛选器选择产品类别时，X轴显示的是产品的类别，而当筛选器选择姓名时，则X轴显示的是客户的姓名。

## 书签

创建两个书签来切换不同的图表，这应该是相对来说最简单的方法了，虽然原理上并不是动态坐标轴，但是结果上看还是相同的。

方法很简单，就不再写详细过程，创建两个书签来切换不同的图表即可。

![](https://secure2.wostatic.cn/static/55eTNT1LoNRxDG3ErmHCWV/%E5%8A%A8%E7%94%BB.gif?auth_key=1655638074-fcTshS2SPS9KUh4ZpLX98c-0-110941c8e8efa30140d1ce689c66ccbf)

可是，这样会有一些问题，比如数据量很大，或者需要动态切换的图表很大，工作量就会变大，甚至会让报告变慢。

## 组合一张新的辅助表

还是回到问题本身，我们想通过筛选器来切换坐标轴的值，其实可以想像出筛选器字段来坐标轴字段来源于一张表。所以，上述问题只需要存在这样一张表：两个字段，一个字段是类型，只有两个值产品类别和客户姓名，另一个字段是对应的值。

构造计算表如下，不需要和其他表建立任何关系

```js
Category and Customer = 
UNION(
    SELECTCOLUMNS( VALUES( 'Product'[EnglishProductCategoryName]), "Value", [EnglishProductCategoryName], "Type", "Category" ),
    SELECTCOLUMNS( VALUES( 'Customer'[First Name] ), "Value", [First Name], "Type", "Customer" )
)
```

、

![](https://secure2.wostatic.cn/static/o9zqv8tvmpMyacWctY4tba/image.png?auth_key=1655992200-4QdqRjxHpJusi1HoSiXWPF-0-2588429343d367fe45d14ceb485042f5)

这样，我们就可以通过筛选器来切换坐标轴的值了，只是这里还不没有结束，还需要将计算表与维度表关联起来，不然无法正确显示相应度量，这里方法也很简单，只需要选择不同类别时建立不同的虚拟关系即可

```js
Sales Amount.Show = 
var x = SELECTEDVALUE( 'Category and Customer'[Type] )
var result = 
    SWITCH(
        x,
        "Category", CALCULATE( [Sales Amount], TREATAS( VALUES('Category and Customer'[Value]),'Product'[EnglishProductCategoryName] ) ),
        "Customer", CALCULATE( [Sales Amount], TREATAS( VALUES('Category and Customer'[Value]),'Customer'[First Name] ) ) 
    )
return 
    result
```

![](https://secure2.wostatic.cn/static/jD5qsP3odS64eKMNTp3bbo/%E5%8A%A8%E7%94%BB.gif?auth_key=1655992194-aTfhrhC7uDuki66eKXRKPb-0-5db47f50a76ff775b8af52943d476fd6)

这里，也可能改用计算组来实现，创建两个计算项如下

![][](https://secure2.wostatic.cn/static/4kDvwsV9auvoLxtyRmWKfY/image.png?auth_key=1655992252-43sbD496cVpt9DpX4wQFKx-0-e4dc02a3c1faeecc2d27411dd66a9ebd)

![](https://secure2.wostatic.cn/static/rRTeLjnEDkifzbsvM9ipU/image.png?auth_key=1655992266-vTZpYehLF3qLMgPTe8nhYk-0-9f421fbf28c3f7e70e10bdda47f8bff5)

使用计算组，也省去了如果需要动态切换的度量值太多还需要再写一个融合度量值的情况，比较推荐计算组的写法。

## 年季月切换

再来看另一个问题，既然产品类别和客户名称可能通过维护一张辅助表来实现，那坐标轴年度、季度、月度切换也是一样的，另外因为它是和日期相关的，所有还必须存在一列是日期列，此外为了显示效果，也需要两个排序列。如下图所示

![](https://secure2.wostatic.cn/static/mZtqthW6knt9XMBdhZoFWj/image.png?auth_key=1655992284-f6TuNEzGReLchVi4GKgF3B-0-aaf5b7f9e9415c1200b71654eb193d45)

构造起来也比较简单，只需要分别构造年度、季度等五张表，最后组合起来就可以了。

```js
DatesPeriod = 
VAR _datetable = 'Date' 
VAR _Year = 
ADDCOLUMNS( 
    SELECTCOLUMNS( _datetable , "Range" , "Y" &  [CalendarYear] , "Date" , [Full Date] ) , 
    "RangeOrderBy" , YEAR( [Date] ),
    "Type" , "Year" ,
    "TypeOrderBy" , 1
)
VAR _Quarter = 
ADDCOLUMNS( 
    SELECTCOLUMNS( _datetable , "Range" , "Y" & FORMAT( [Full Date] , "YYYY\QQ" ) , "Date" , [Full Date] ) , 
    "RangeOrderBy" , YEAR( [Date] ) * 100 + QUARTER( [Date] ) ,
    "Type" , "Quarter" ,
    "TypeOrderBy" , 2
)
VAR _Month = 
ADDCOLUMNS( 
    SELECTCOLUMNS( _datetable , "Range" , "Y" & FORMAT( [Full Date] , "YYYY\MMM" )  , "Date" , [Full Date] ) ,
    "RangeOrderBy" , YEAR( [Date] ) * 100 + MONTH( [Date] ), 
    "Type" , "Month" , 
    "TypeOrderBy" , 3  
)
VAR _Week = 
ADDCOLUMNS( 
    SELECTCOLUMNS( _datetable , "Range" , "Y" & [CalendarYear] & "W" & WEEKNUM( [Full Date], 2 ) , "Date" , [Full Date] ) ,
    "RangeOrderBy" , YEAR( [Date] ) * 100 + WEEKNUM( [Date], 2 ) , 
    "Type" , "Week" , 
    "TypeOrderBy" , 4 
)
VAR _Date = 
ADDCOLUMNS( 
    SELECTCOLUMNS( _datetable , "Range" , FORMAT( [Full Date] , "YYYY/MM/DD" ) , "Date" , [Full Date] ), 
    "RangeOrderBy" , [Date] , 
    "Type" , "Day" , 
    "TypeOrderBy" , 5  )
RETURN UNION( _Year , _Quarter,  _Month , _Week, _Date )
```

![](https://secure2.wostatic.cn/static/5BoBjTj3LNGv2rtcTeseRe/%E5%8A%A8%E7%94%BB.gif?auth_key=1655992194-ddziL2vqF4VanzVYx1YZLJ-0-3f6e6aa0fec617f95ac605c6c3039f28)

## 进阶
[[PowerBI字段参数#动态坐标轴]]