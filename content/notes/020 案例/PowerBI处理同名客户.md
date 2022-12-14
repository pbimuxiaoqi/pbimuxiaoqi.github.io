---
created: 2022-05-29
tags: 同名 聚合 排序
subject:
importance:
skilled:
status:
author:
url: https://www.wolai.com/muxiaoqi/ceD5TBoAuS6fiSMDndEk2k
cover: 
---

有时候我们会处理两个或两个以上实体名称相同的情况，本例以客户名称为例，在数据中会存储客户的名称和客户代码，客户代码是唯一标识。

假设存在下面这样的数据

![](https://secure2.wostatic.cn/static/5zy4x3h9SdKHCmP1ApWAAS/image.png?auth_key=1653839466-sVxXAA5qraHnfYjJEJkmAx-0-c0208da54b8e953b6b022db778940d0d)

如果我们去掉客户代码，PowerBI会根据客户名称进行聚合，从而错误的显示数据

![](https://secure2.wostatic.cn/static/u86hSM38Zu6423moK5JmY2/image.png?auth_key=1653839478-mqKukvEAGi417QTgS1EUnk-0-c2c953d42011f45ca4b0e18d468f143b)

一种常规的做法的将客户代码和客户姓名列合并

![](https://secure2.wostatic.cn/static/rFPRDySQ4ae7WrDz5asWLt/image.png?auth_key=1653839488-tHPsomEbqRUye9XFnxubwy-0-315ac6f6cd190dc5c9c90c1bd716ae77)

我们还可以使用另外一种方式来使名称看上去唯一，同时又不改变现有客户名称列，我们可以使用[zero-width space](https://en.wikipedia.org/wiki/Whitespace_character)，此案例我们使用Unicode 8204

新建计算列

```js
Name Unique =
VAR CustomersWithSameName =
    CALCULATETABLE (
        SUMMARIZE ( Customer, Customer[Customer Code], Customer[Name] ),
        ALLEXCEPT ( Customer, Customer[Name] )
    )
VAR Ranking =
    RANKX ( CustomersWithSameName, Customer[Customer Code],, ASC, DENSE )
VAR Blanks =
    REPT ( UNICHAR ( 8204 ), Ranking - 1 )
VAR Result = Customer[Name] & Blanks
RETURN
    Result
```

但是示例数据中其实是有385条个没有客户名称的数据的，这样最后一个空数据其实有385个空格，但是好在显示上就一个空格，然后我们还可以通过原有的客户姓名列来过虑空客户或名称有相同的客户

新建计算列

```js
# Duplicates = 
CALCULATE( COUNTROWS( Customer ), ALLEXCEPT( Customer, Customer[Name] ) )
```

还可以这样

![](https://secure2.wostatic.cn/static/mJUjAVXqPMompgeX1hsqtx/image.png?auth_key=1653839502-i7MoAfHbrXbDjDG1hiZJPE-0-b76a54cba8bf331be1ebbdd2c48844e3)