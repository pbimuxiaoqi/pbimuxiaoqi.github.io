---
created: 2022-05-15
tags: 权限 列权限 ols 
subject: 权限
importance: 5
skilled: 5
status:
url: https://www.wolai.com/muxiaoqi/f77hiGUaR1KjxXpa4eVeFK
cover: 
---
前面已经介绍过行级别权限控制和页权限控制，今天介绍下列权限控制（OLS）

[[PowerBI权限管理入门篇]]
[[PowerBI权限管理进阶（一）]]
[[报表导航页权限控制]]
[[使用行级别权限实现列权限控制]]

同样的OLS也需要借助于Tabular Editor，首先需要注意的是OLS暂时是不支持DAX表达式的，所有如果某些列需要设置权限，则需要在不同的角色中控制。

假设我们要隐藏Internet Sales表中的TotalProductCost列，我们先创建一个角色A

![](https://s2.loli.net/2022/05/15/F6xHO3apJyVlmz1.png)


外部工具打开Tabular Editor，依次打开Internet Sales表的TotalProductCost属性面板，设置Object Level Security的属性为None,点击保存。

![](https://s2.loli.net/2022/05/15/H9rRW7uXDY8JEAl.png)


回到报表以角色A身份查看，会发现在Internet Sales表中已经看不到TotalProductCost列，但是我们的报表却报错了，因为表格中我们使用了引用这一列的度量值，而角色A是没有这一列的权限的，所以就直接报错了，这点体验上确实很不好，如果没有权限报表上应该是不显示该列的值或者返回一个默认值。

```js
Product Cost = SUM('Internet Sales'[TotalProductCost])
```

![](https://s2.loli.net/2022/05/15/H9rRW7uXDY8JEAl.png)

那么，有没有办法来达到我们上面想要的效果呢？要做到这点那么首先就要可以判断出哪些人有权限来查看该字段，哪些人没权限查看，我们构造一张角色权限表，其中UserType代表是否有权限，1代表有，2代表无。

![](https://s2.loli.net/2022/05/15/QFZEUCWuvgczOkS.png)


接下来重构Product Cost度量值，先获取当前角色类型，然后根据角色类型判断要显示会么样的数据

```js
Product Cost.Show = 
VAR UserType = LOOKUPVALUE( 'User'[UserType], 'User'[Email], USERNAME() )
VAR TotalCost = SUM( 'Internet Sales'[TotalProductCost] )
VAR Result = IF( UserType = 2 && NOT ISBLANK( TotalCost ),  "No Premission", TotalCost )
RETURN Result
```

再来看下效果，这里还有点要注意，要在报表中将TotalProductCost列隐藏

![](https://s2.loli.net/2022/05/15/S8Vg9xNZ7ptuMWT.png)


![](https://s2.loli.net/2022/05/15/S8Vg9xNZ7ptuMWT.png)

这样我们就实现了OLS的功能，现在我们来总结下

-   当某一列需要在图表元素上对不同角色隐藏或显示时，最好是通过度量值判断角色是否有权限实现，并在原表中隐藏该列
-   当某一列需要对不同角色隐藏或显示且该列没有在报表上使用，则可使用自带的OLS通过Tabular Editor来管理