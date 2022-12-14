---
created: 2022-06-19
tags: rest-api m 
subject:
importance: 3
skilled: 3
status:
author:
url: https://www.wolai.com/muxiaoqi/nuJfhCTrKX4yZigK52YrTu
cover: 
---

前面有介绍过Rest Api的使用，[[PowerBI rest api初识]],[[PowerBI REST API 进阶]],但是应该还是有人不知道如果使用M语言来获取Token,如果还不知道怎么创建应用的，可以去看先前的文章，应用创建完之后，需要用到client_id,如下图

![](https://secure2.wostatic.cn/static/hh5jvEjMYjb4VrAPJY2VQu/image.png?auth_key=1655639749-cc9JyqeejYs7bwMJ52nGH-0-6ed1de9ad808f1b2c107e84d35d049c9)

来看一下Postman中运行的效果，可以正常获取到token

![](https://secure2.wostatic.cn/static/5LmgvTB5QR1okZHvTffMUi/image.png?auth_key=1655991789-jjrZBA1yLbuYTm9jahJ4zR-0-e11284cd15e08fa61cdfe09ca31463fb)



## 需要用到的url

```Python
Authority Url
https://login.microsoftonline.com/common/（国际）
https://login.partner.microsoftonline.cn/common/(国内)

Resource Url
https://analysis.windows.net/powerbi/api （国际）
https://analysis.chinacloudapi.cn/powerbi/api （国内）

Api Url
https://api.powerbi.com （国际）
https://api.powerbi.cn （国内）

Access Token URL
https://login.microsoftonline.com/common/oauth2/token（国际）
https://login.partner.microsoftonline.cn/common/oauth2/token （国内）
```

## 方法一

那么接下来就在PowerBI中使用M语言来实现，进入到PQ页面，新建数据源—空查询，body部分只是用是&符把刚postman中的参数和值连接起来，

![](https://secure2.wostatic.cn/static/qtUBvMWSGzp954gTZBVATn/image.png?auth_key=1655991855-6XcWnT5cBw474pGFxjuL1f-0-378206a4c65b65ba67aa60b7ef5b1d4d))

上面body部分很长，阅读起来可能会很麻烦，也可以使用下面的方法，

![](https://secure2.wostatic.cn/static/gU2SN8hctXrRRLddHSRusy/image.png?auth_key=1655991877-qWnhdMdV4mtgapav75YK9L-0-412047ac6692b4fa77445e59f4c8ac4b)

![](https://secure2.wostatic.cn/static/4SzQsxq1Jvz3CXFrk3nC3m/image.png?auth_key=1655991902-i8kjcvSS8dwMn9hH4zKfdX-0-a1e61f3cb94a6a278cb36ee5217b7499)

使用上面两种写法都可以获取token，但还存在一个问题，就是使用了用户名和密码，对于很多公司可能强制3个月或者更短的周期就要换一次密码，所以接下来介绍另外一种方法。

## 方法二

这里接口和方法一稍有不同是原先common部分替换成了tenantId,然后grant_type换成了client_credentials

另外还用到了secrets,还没有创建的话，需要创建一个。值只在第一次创建时可见，所以创建完记得保存，此外,secrets现在同样有有效期了，不过时间可以设置的长一些，目前最长是两年。

![](https://secure2.wostatic.cn/static/j59Rkfu5R3JbRBm3dC9woZ/image.png?auth_key=1655991968-rWvnYxhbwZr28XjeLwgzy3-0-9fa78c9282a0435b39acb7da059b078e)

之后代码其实和方法一就类似了

![](https://secure2.wostatic.cn/static/8j92FQUUtC5am3Ed3qqUed/image.png?auth_key=1655991982-vTwXtzX8nFGV25STec8Rhm-0-91991d12751734ad8ebf0a5672d59583)

获取了token，就可以传递到其他查询中来用，这里一次查询了多个Api的数据，方法也很简单，使用expand=将四个接口组合起来，这样就可以请求一次就获取4个接口的数据了。

![](https://secure2.wostatic.cn/static/v4pqr5B444NjgVGfDm1HQX/image.png?auth_key=1655991997-v6FinkXauRxxFzDJXDyDyz-0-0be11ab2bbba62fecb8855f7b6e48cda)

为了代码简单，上面代码并未展开结果，手动把结果展开就好，

![](https://secure2.wostatic.cn/static/izhqRAzisPR39wYoukCPf3/image.png?auth_key=1655992074-vgNXiRJ58EwdpD4HuYDwMf-0-b13c8b66b25cdda86152f848456d468a)

至此，我们就可以通过在PQ里写M语言来获取包括工作区、报表名称、数据集、用户的相关信息了。