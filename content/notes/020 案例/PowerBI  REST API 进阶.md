---
created: 2022-06-19
tags: rest-api 
subject:
importance: 3 
skilled: 3
status:
author:
url: https://www.wolai.com/muxiaoqi/tjA5ygPzL1x4E4LmUVv3mi
cover: 
---

上篇文章有简单介绍REST API的用法，最后遗留了一个问题，就是获取的token是有时效性的，怎么才能保证每次请求时都能拿到最的token呢，其实也很简单了，只需要先创建一个应用，

```js
https://dev.powerbi.com/apps  国际
https://dev.powerbi.cn/apps  国内

```

选择我们需要的权限即可

![](https://s2.loli.net/2022/06/20/3tSgasQZ5L2E8IX.png)


点击注册后会得到一个应用ID,后面我们需要用到。

![](https://s2.loli.net/2022/06/20/s5RJ8xuBrdh9f2o.png)


这时候还没结束，我们还需要去azure的管理中心做些操作，同样

```js
https://portal.azure.com/  国际
https://portal.azure.com/  国内

```

搜索App registrations

![](https://s2.loli.net/2022/06/20/OHhyRNle5AmLbG3.png)


点击进入刚才创建的应用

![](https://s2.loli.net/2022/06/20/PlwMnatFkGs8R5Z.png)


之后进行授权操作，依次点击API permissions > Add a permission > Power BI Service > Delegated permissions > Tenant > Tenant.Read.All,最终授权给当前用户。

![](https://s2.loli.net/2022/06/20/RoK3rinzaMhcUYQ.png)


![](https://s2.loli.net/2022/06/20/kaxrsLEbgAPc6IM.png)


![](https://s2.loli.net/2022/06/20/kaxrsLEbgAPc6IM.png)

![](https://s2.loli.net/2022/06/20/q3UbMNHBhGIiacw.png)


之后我们来测试下，这里是用python来测试，也可以使用其他语言或Postman，可以看到已经可以拿到token了

![](https://s2.loli.net/2022/06/20/9Lbg6WJD8P1RAks.png)


接下来就是通过这种方式使用REST API来构建一个属于我们自己的管理中心了。