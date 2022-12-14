---
created: 2022-06-19
tags: 外部工具  tabular-editor 
subject: 
importance: 2
skilled: 4
status:
author:
url: https://www.wolai.com/muxiaoqi/vxJZj2b97WqHF9eQbimtpw
cover: 
---

怎么创建度量值，我们都很熟悉，把度量值变成KPI，很多人可能会比较陌生，毕竟PowerBI客户端本身是不支持这个功能的，还是需要借助外部工具来实现。其实实现起来也比较简单，只需要用到Tabular Editor。

1、外部工具中打开Tabular Editor,选择要变成KPI的度量值，右键新键KPI，可以看到有三个KPI相关的表达式可供我们创建。

![](https://secure2.wostatic.cn/static/8s2Mavn4gLAAEMrDSubGP1/image.png?auth_key=1655642003-eAxnQSTxDvH5i9JkLzW7iH-0-89f3543a5da6d51c75d60f65fb24e5a0)

![](https://secure2.wostatic.cn/static/wNQyJ6XKSi2KPetBDZqx7W/image.png?auth_key=1655642009-nR83fq3pFEBJcCj85Bvppx-0-9a21e0ce4e16a21e5ec797bf2b9991dd)

2、先写状态的表达式

```js
VAR Rate = [MOM Sales Amount %]
VAR Result =
    SWITCH (
        True,
        Rate > 0, 1,
        Rate < 0, -1,
        0
    )
RETURN
    IF (
        NOT ISBLANK ( [Sales Amount] ),
        Result
    )
    
```

3、下拉选择状态表达式的图标样式

![](https://secure2.wostatic.cn/static/vKYMk86WQCFDvWQo5hY6s5/image.png?auth_key=1655642018-a4BMKqksyG9maxBkQdzHP9-0-1fd53b21bf7cd80ec15d35c72075dbc6)

4、点击保存返回PowerBI文件查看效果，可以看到Sales Amount前面多了一个小图标，且展开后会分为值、目标、状态

![](https://secure2.wostatic.cn/static/9G4KzWbjeMSDA9mvv1yFvh/image.png?auth_key=1655642029-d9oTkEKdExAyjGbLnYSX6q-0-ad966be8d3b86662c6e1c35b18848278)

5、继续写其他两个表达式，因为样例数据中没有Target这个字段，所以出于演示目的Target Expression为如下：

```js
[LM Sales Amount] * 1.1
```

Trend Expression的表达式如下：

```js
VAR SalesPY =
    CALCULATE (
        [Sales Amount],
        DATEADD ('Date'[Date], -1, Year)
    )
VAR Result =
    SWITCH (
        TRUE,
        [Sales Amount] > SalesPY, 1,
        [Sales Amount] < SalesPY, -1,
        0
    )
RETURN
    IF (
        NOT ISBLANK ( [Sales Amount] ) 
        && NOT ISBLANK ( SalesPY ) ,
        Result
    )
```

同样设置他们的显示格式或图标样式

![](https://secure2.wostatic.cn/static/i2a7JiLFvmaW4K56hjujzy/image.png?auth_key=1655642038-bixPN6d6FwKUKPj6C6on6C-0-467cc85dfe6bb5ee18dadfe34f3fd172)

6、返回PowerBI查看最终效果

![](https://secure2.wostatic.cn/static/eYD3iXtgXM51soLicPToA4/image.png?auth_key=1655642046-x8QECRb5xNe2ChKeEoBPQ4-0-31de614eb10aab66917b33e89a85aba4)