---
created: 2022-10-16
tags: 分享
subject: 功能
importance: 2
skilled: 4
status:
author:
url: https://www.wolai.com/muxiaoqi/cUnRtcic1Ma4rQUdQpaZu8
cover: 
---

```dataview
list 
without id
url
where file.name = this.file.name
```

PowerBI支持将数据集共享给外部来宾用户，具体细节可查看官方文档

[在外部组织中与来宾用户共享 Power BI 就地数据集 (预览版) - Power BI | Microsoft Learn](https://learn.microsoft.com/zh-cn/power-bi/collaborate-share/service-dataset-external-org-share-about)

此外，官方预览功能中用户也可以使用来自组织外部的数据集在PowerBI Desktop中创建报表，

[Microsoft Ignite 2022: Do more with enterprise self-service business intelligence | Microsoft Power BI 博客 | Microsoft Power BI](https://powerbi.microsoft.com/zh-cn/blog/microsoft-ignite-2022-do-more-with-enterprise-self-service-business-intelligence/)

但是目前还不支持在PowerBI桌面端中使用外部共享的数据集来创建报表，但是在使用数据集在Server中创建报表还是支持的。

![](https://secure2.wostatic.cn/static/p8GECRhdwgjYT3tYgGJXps/image.png?auth_key=1666009278-rZnRx1A89Bm1jFJZm8CAT7-0-fcb8f5aee5fcb95bcdf31838b368e44f)

接下来我们来看下怎么将报表或数据共享给外部用户。

## 允许 Azure Active Directory 来宾用户访问 Power BI

启用此设置可允许 Azure Active Directory 企业到企业 (Azure AD B2B) 来宾用户访问 Power BI。 如果禁用此设置，则来宾用户尝试访问 Power BI 时会收到错误。 为整个组织禁用此设置的操作还将阻止用户邀请来宾加入你的组织。 使用“特定安全组”选项控制哪些来宾用户可以访问 Power BI

![](https://secure2.wostatic.cn/static/6tvXm13NA14b7RXvifA6aT/image.png?auth_key=1666009278-aiTeJkmDk9kdvza7oCULhX-0-08d1b3b18c8f69bd3bda22b1965f2c11)

## 邀请外部用户访问组织

![](https://secure2.wostatic.cn/static/uVxt8ZmK8u26MCohJvBkCS/image.png?auth_key=1666009278-7o5rv3vEhTMbBvGPo154LE-0-07c1ffdfe08f8b052b07ef4a565f8a0d)

## 添加外部租户（跨云）

如果不需要跨云分享这一步可以省略，

[配置 B2B 直连跨租户访问 - Azure AD - Microsoft Entra | Microsoft Learn](https://learn.microsoft.com/zh-cn/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

访问azure门户

```js
portal.azure.com   // 国际
portal.azure.cn    // 国内
```

依次访问 Azure Active Directory，External Identities， Cross-tenant access settings, Organizational settings

![](https://secure2.wostatic.cn/static/26ZxyWB2seNWZusv5ZyWPE/image.png?auth_key=1666009278-hYSLymnTAGigkRNHyWDNK7-0-1a4245aa23cb1f11697b508c4a3057b8)

添加外部域，这里可以直接输入外部域的域名来添加，也可以输入外部域的ID,

![](https://secure2.wostatic.cn/static/7AU3uGgnDqft6xer8nDE6C/image.png?auth_key=1666009278-ojSSyd5rJq9LSr2SUgoN2u-0-4aa9c7970a1c96557d67233598ee972a)

域的Tenant ID可在预览页查看

![](https://secure2.wostatic.cn/static/d37axYWXeSWPQiaLb8t9vK/image.png?auth_key=1666009278-e72xetvdzJGr7qwZC6sRKk-0-d1cc23c13ab61cff505b4c50b42756c3)

## 添加来宾用户

切换到Azure Active Directory，Groups，

![](https://secure2.wostatic.cn/static/bP5JYkKNUhGmPbSMavJaJo/image.png?auth_key=1666009278-3oZH3bWjBAXrXwow3SbJyc-0-bfdd5f14f055a54245ab52fbae592501)

这里我们可以新建一个外部用户组方便统一管理，类型选择Security

![](https://secure2.wostatic.cn/static/ovXfXaTtUVof2uqvc8c1Lo/image.png?auth_key=1666009278-rNbNEpS2f3vkEYLK3U5Cjx-0-92f2b89fc6ae3d9c0d8c5746b80087ea)

之后我们添加来宾用户即可，需要注意的是这里添加外部用户时会发来宾用户发送一个邀请邮件，需要对方确认后，然后再次添加

![](https://secure2.wostatic.cn/static/fRYQHGjVjwJfvvMhuYCfcV/image.png?auth_key=1666009278-f2LcMGfwsFUe2f8tMunf4n-0-b3a05b93a75cecaaf1151073b684a507)

## 分享报表或数据集

当需要将报表分享给外部人员时，点击分享按钮后，切换为特定人员，并设置好需要给到的权限，这里还需要注意，如果报表进行了权限设置，别忘了数据集安全设置里也添加下

![](https://secure2.wostatic.cn/static/ovdf1yxJ36qYvmJBvgJ3wK/image.png?auth_key=1666009278-pvKCzQnF1oxqfv34xB132t-0-e05e41c9bff42a70503ead4573aa73b0)

输入外部人员邮箱，这里会发现添加的外部用户会多个后缀来区分

![](https://secure2.wostatic.cn/static/q69k12EeGxvPWGPe1LkZq1/image.png?auth_key=1666009278-oJvizRxWretrx2YERmRzob-0-df470069aa6eb13c6ba5eac4cf6efdb8)

回到outlook可以看到有收到邮件，点击进去即可查看报表

![](https://secure2.wostatic.cn/static/k6ERuqbgYVP1YzkQy3QEuJ/image.png?auth_key=1666009278-fJhPx7Ej88ntu2rwopWiL5-0-1b097af358b4ea516ad07798f8d35d51)

查看报表的时候会发现链接会有不同，比如使用来宾账户查看刚分享的报表，左上角其实是我主账号的信息

![](https://secure2.wostatic.cn/static/buzdw8hSPDoAUEPEKa8GGT/image.png?auth_key=1666009278-uGs8B6eR7zXuRnWb8ZLw54-0-be0179dcc0f10cd60945dece3d98ad96)

如果门户设置中允许下载报表文件，那么通过这种方式分享的报表来宾账户也是可以下载的

![](https://secure2.wostatic.cn/static/qUvQm31S6VnFAKUkcMwAx5/image.png?auth_key=1666009278-94dzd56vCtreF7k14R9Jxv-0-f098f6a644916b21d9a818e6a75da03f)

## 分享数据集

如果不想共享报表给对方，只想共享数据集，可以点进数据集后，点击上方的共享按钮

![](https://secure2.wostatic.cn/static/7UsevvhYfa6pkinK495hFM/image.png?auth_key=1666009278-3GpfZGg951wMJP2SXAftfx-0-cfadfad806aa8686196b6f55e93532f2)

然后选择上方文件，设置

![](https://secure2.wostatic.cn/static/sEoPZkCfECRW8o5HDtDHgK/image.png?auth_key=1666009278-9NP8YftinrWF8xPij2fUq9-0-54e2193e7752ffd3bfcc338c011b9aec)

打开数据集的外部共享

![](https://secure2.wostatic.cn/static/7CiSxwTQWzKmoyqaa2YXzM/image.png?auth_key=1666009278-gcURTDKuDQZpDuAhtzkJ4D-0-ffdb4fc5ccb540a38a7327b3abb4ca66)

使用来宾账户登陆就可以在首页的来自外部组织下看到当前分享给该账号的所有文件

![](https://secure2.wostatic.cn/static/3171Vme9qrqzoNFfo9L4Ro/image.png?auth_key=1666009278-krpi1Cf57eV3C93NUGE2hm-0-645dc3ed9b895ea1e06351444dce25ca)

点击该数据集，就可以在server端使用该数据集创建报表，注意通过这种方式分享的数据集，来宾用户是无法下载原始报表文件及他自己使用该数据集创建的报表文件的

![](https://secure2.wostatic.cn/static/qWss3Xs6ycu3zMLvB843xk/image.png?auth_key=1666009279-etsjvBJt8gsyCbHWJF2Ln9-0-b5edc9b290d4ff545115e1770cde2977)

## 分享工作区

当然除了分享报表和数据集，也是可以直接分享工作区的。

![](https://secure2.wostatic.cn/static/iPkophR4ir3qmtEcFPywBE/image.png?auth_key=1666009603-cxnbCNSQBLFCaPSao7mhW-0-818a638fb1031a6bdaa6fe19cbaed473)

## 许可

当然这个功能的前提是要有相应的许可，具体可查看官方的说明

[使用 Azure AD B2B 将内容分发给外部来宾用户 - Power BI | Microsoft Learn](https://learn.microsoft.com/zh-cn/power-bi/enterprise/service-admin-azure-ad-b2b#enable-access)

想提前体验该功能的，可申请开发者账号进行测试

PowerBI开发者账号申请，不限license

## 总结

目前还没办法在PowerBI Desktop中使用来自外部组织的数据集创建报表，但可以在Server端创建，这个功能对于普通企业来说可能用不到，但对于一些数据服务商还是很有用的，三方用户可以使用他们构建的数据模型来搭建前端报表而不法知道具体指标的算法，增加用户体验的同时，又不会泄露相关指标算法。