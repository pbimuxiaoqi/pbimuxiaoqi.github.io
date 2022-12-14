---
created: 2022-06-19
tags: 外部工具 数据源 rest-api
subject:
importance: 2
skilled: 5
status:
author:
url: https://www.wolai.com/muxiaoqi/voKA5NKyW6LpWWrLhJqWfW
cover: 
---

之前花了很大的篇幅来介绍REST API，但其实对新手不友好，特别是还是写M代码，那有没有一个工具可以不用写代码呢？既然这样问，当然是有了，国外大神早就写了一个自定义连接器来方便使用。说起来搜到这个还是因为想写本关于PowerBI的开源书（只是更系统分类文章而已），所以搜了下Power Query的操作，结果发现了作者的博客，原来他还是第一版《M Is for (Data) Monkey》译者，第二版的联合作者。

作者博客如下：

https://www.thepoweruser.com

github资源链接如下：

https://github.com/migueesc123/PowerBIRESTAPI


下载文件后，只需要把后缀是mez的文件放入到以下文件夹即可([Documents]\Power BI Desktop\Custom Connectors)，其中Power BI API文件夹下是源码，里面有具体的pq代码，感兴趣的可以看下，其中使用的方便和上篇文章介绍的类似[[PowerBI 使用M函数调用Rest Api]]。

![](https://secure2.wostatic.cn/static/cqBDYiNvzwzJDsNmK9a3mS/image.png?auth_key=1655639324-3SUbXtmQgtpjbWpZbb4o6m-0-576ce10ac7b57a2bfee83a76e6cdc253)

![](https://secure2.wostatic.cn/static/3Sb7CzYjatzXpF7KVr4cut/image.png?auth_key=1655639334-6ELxZfptR9WMRRfVyi42EC-0-354c38521648481448b3addfb6dfe9b6)

之后需要在选项和设置—安全性—数据扩展—允许任何扩展

![](https://secure2.wostatic.cn/static/4qhTuDQYtVcHKdMLtYApUF/image.png?auth_key=1655639341-7FPhFs3jHZtnLkvKJePE4i-0-84fde8d1f1251c2efcb20b86b8820f4c)

重启PowerBI之后就可以在连接器里看到REST API的连接器了

![](https://secure2.wostatic.cn/static/q8y62bgYB5Znru96jCaibr/image.png?auth_key=1655639348-c1HawXPRSW5oB4yGCfe8Pt-0-6cc9d9878a331c7d5b868e41472611fe)

作者已经写好了很多接口的调用，选择选择需要的接口导入数据就好，并且作者对原始的数据做已经做好了处理，不需要再重新命名之类的。

![](https://secure2.wostatic.cn/static/6mRiqta4uNu7M1STevMypt/image.png?auth_key=1655639356-2Cg8EjcsnSri6M83wKr15c-0-c47e44d2dc331aaa2f6db835391a4db9)

比如我导入了工作区的信息后如下，不能说很省事，只能说太省事了。

![](https://secure2.wostatic.cn/static/p3Sk2srBVMX2n9wNm8Xi3G/image.png?auth_key=1655639365-gp3i8JhUivzh4s411kKY1d-0-cde5dbbe83c2a2338f701033fb9dceb7)

如果需要发布到云端，并可以设置自动刷新，还需要再配置下网关，打开网关连接器，选择连接器，选择刚放入连接器的文件夹就好。

![](https://secure2.wostatic.cn/static/rGjT9NRt6TQ8BaBfiEot4h/image.png?auth_key=1655639373-qAhd2XKYXSvSrX8LAW2K6r-0-4e6f770e7015c6ee90f65c222c118f36)