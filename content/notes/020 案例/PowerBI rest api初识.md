---
created: 2022-06-19
tags: rest-api 
subject:
importance: 3
skilled: 3
status:
author:
url: https://www.wolai.com/muxiaoqi/fsCNaqrmoCyhtTEnLMMC4U
cover: 
---
连笔记软件都在谈api的现在，如果某个软件没有开放api会被用户瞧不起。国际大厂巨硬肯定也是有开放相关产品的api的，只不过对于不同付费的用户做了次数上的限制。具体详情可参考可官方文档

[Groups - Get Groups - REST API (Power BI Power BI REST APIs) | Microsoft Docs](https://docs.microsoft.com/en-us/rest/api/power-bi/groups/get-groups)

这里有点需要注意，因为国内版的PowerBI是世纪互联代理的，所以在接口方面会存在些差异，具体差异如下：

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

api有了，我们可以用api做些什么呢？这个玩法就比较多了，比如更自由地刷新数据集。

![](https://s2.loli.net/2022/06/20/6y3Ph5Eqs2KYrC7.png)



我们先在官方提供的环境测试下效果，搜索Refresh Dataset, 然后点击试用，然后登录自己的账号就好

![](https://s2.loli.net/2022/06/21/KHjh9gPU1Qz56Ti.png)




看上面api我们需要传入数据集的datasetid,我们可以在以下位置获取，当然也可以通过api的方式获取所有工作区下的所有数据集的datasetid,这里我们先手动获取

![](https://s2.loli.net/2022/06/21/5YUw8FEx1hd4iOR.png)




填入dataset之后点击运行，如果响应代码为202，说明执行成功，返回PowerBI数据集页面，会发现数据集确实已刷新。

![](https://s2.loli.net/2022/06/21/8mgqj3MXxrVKhaD.png)



![](https://s2.loli.net/2022/06/21/4zv3fiecX8YFORq.png)




接下来我们在PowerBI中尝试调用api来获取所有的工作区，数据源选择从web,高级，填入刚才页面里的token信息

![](https://s2.loli.net/2022/06/21/LomStYnaOwx1ds3.png)



确定之后，就可以看到我们所有的工作区信息了。

![](https://s2.loli.net/2022/06/21/lvT7YnPhwAZbQ6E.png)



但是这又有一个问题，这样获取的token信息是有效期，其实官方文档一开始就给出了方法，需要我们创建一个应用。具体怎么使用下次再介绍，还没有PowerBI账户的用户可以参考以下文章

[[PowerBI开发者账号申请，不限license]]

## 扩展阅读

[[PowerBI REST API 进阶]]