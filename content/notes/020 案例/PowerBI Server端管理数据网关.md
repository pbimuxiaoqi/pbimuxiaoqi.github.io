---
created: 2022-06-19
tags: 网关
subject: 功能
importance: 3
skilled: 5
status:
author:
url:
https://www.wolai.com/muxiaoqi/oLKE54VFUw295BxCjx4aXy
cover: 
---

作为企业PowerBI的管理员，日常工作除了分发报表，可能就是管理网关了，目前国际版的Server端已经更新了网关管理的页面，但是入口没变，仍然是设置—管理网关。

![](https://s2.loli.net/2022/06/21/Fz8tPhxCpY5dSiO.png)

## 新建数据源

进入管理网关页面后，左上角有一个新建按钮，点击新建即可创建新的数据源

![](https://s2.loli.net/2022/06/21/85NSqa1s23QUG9t.png)


在选择数据源之前需要先选择网关群集，和命名数据源名称

![](https://s2.loli.net/2022/06/21/85NSqa1s23QUG9t.png)

## 数据源管理

也可以管理数据源，设置数据源的验证信息等。

![](https://s2.loli.net/2022/06/21/xfei7aIkOPlAVX3.png)


也可以管理数据源所性的用户，增加或删除用户，修改用户的数据源权限。

![](https://s2.loli.net/2022/06/21/iwQGZJYnLsebVpH.png)


当然，还有最后一个操作，删除数据源，这个操作一定要慎重，如果报表还在使用中，这对企业来说将是一个灾难。

## 网关管理

在右上方我们可以切换网关的模式，通常企业报表我们是不建议创建个人模式的网关，因为个人模式只能你自己的账号使用。

![](https://s2.loli.net/2022/06/21/iwQGZJYnLsebVpH.png)

同样的网关管关管理也具有三个最基础的功能：设置（个人模式的网关没有该功能），管理用户，删除

![](https://s2.loli.net/2022/06/21/y9HhjFBCOmSA4i5.png)


### 设置网关信息

除了设置网关的一些说明信息外，还可以设置是否允许用户自定义的数据集连接器通过网关刷新数据，在PowerBI REST API 自定义连接器中我们有介绍到使用第三方的连接器来获取REST API的信息。

![](https://s2.loli.net/2022/06/21/INokKQrzfYXct9m.png)


### 管理用户

除了增加删除用户外，还可以对用户的权限和数据源类型进行设置。

![](https://s2.loli.net/2022/06/21/INokKQrzfYXct9m.png)

### 删除网关

同样，该操作也一定要慎重，虽然删除网关后报表还可以正常访问，但会影响报表的刷新，特别是对于销售日报等有实时性要求的报表。

## 虚拟网关

创建虚拟网关需要选择订阅，因为我是开发者账号，并没有开通任何付费订阅，不能演示该功能，感兴趣的可以查看官方文档

[什么是虚拟网络 (VNet) 数据网关（预览） | Microsoft Docs](https://docs.microsoft.com/zh-cn/data-integration/vnet/overview)