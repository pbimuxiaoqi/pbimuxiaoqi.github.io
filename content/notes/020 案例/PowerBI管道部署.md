---
created: 2022-06-19
tags: 管道 管理员
subject: 功能
importance:
skilled:
status:
author:
url:
cover: 
---
熟悉软件开发的人经常会用到三个环境：开发->测试->生产，同样的PowerBI也很给我们提供了类似的方式——管道，通过创建参数来快速切换不同环境的数据库。

要使用这个功能也很简单，只不过在报表文件时我们就需要把数据库连接信息参数化，

1、pq界面，视图-始终允许

![](https://imgedit.newrank.cn/edit/upload/photo/2021/08/10/e7b63174dc934c979236d875fddb967a.jpg)

![](https://imgedit.newrank.cn/edit/upload/photo/2021/08/10/8edb35393e374d10b3f8efde64721ca7.jpg)

![](https://imgedit.newrank.cn/edit/upload/photo/2021/08/10/d827ffb6e082447cb117716b064d5d98.jpg)

3、修改完成后上传报告并配置网关,网关的配置这里不再做过多的讲解。

4、接下来是创建管道

![](https://imgedit.newrank.cn/edit/upload/photo/2021/08/10/cda260be14144833902c8d90c8e58798.jpg)

![](https://imgedit.newrank.cn/edit/upload/photo/2021/08/10/a74df383c87b4998ab23390be3608200.jpg)

![](https://imgedit.newrank.cn/edit/upload/photo/2021/08/10/36cedf8d6f9a4e5ca79363a3ff8326e2.jpg)

后面部署到生产也是同样的操作，这个操作很简单，开发中却可以省却我们很多人力，且让PowerBI报表的部署更加自动化。

---

![](https://imgedit.newrank.cn/edit/upload/photo/2021/08/07/78cb3b5075684ae2873f76c20187501b.jpg)

## 更多
[[PowerBI Server端管理数据网关]]