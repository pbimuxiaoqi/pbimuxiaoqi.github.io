---
created: 2022-06-19
tags: 数据市场
subject: 功能
importance: 3
skilled: 5
status:
author:
url: https://www.wolai.com/muxiaoqi/nW3skLDfTivccPgX5u1fg6
cover: 
---

这次微软大会主要带来了在三个重磅功能，集成PPT、指标、数据市场，在昨天的文章中已经介绍了怎么把PowerBI报表嵌入PPT报告中（[[PowerBI嵌入PPT]]），今天就一起来看一下数据市场，目前数据市场（预览版）已经在国际版上线，国内世纪互联版可能还要继续等一段时间，毕竟这是Server端的功能，没那么快可以迁移到国内。另外需要注意的是这个功能只支持高级容量工作区，如果你只是pro用户，则可以试用ppu，然后创建一个高级容量工作区，如果还没有账号，则可以参考[[PowerBI开发者账号申请，不限license]]。

## 连接数据

首先打开工作区，新建—数据市场

![](https://secure2.wostatic.cn/static/299HPBsJ8Xux8sJw9Nbw59/image.png?auth_key=1655613215-nWKiQcyu64md9LRSCyHqLt-0-d2f181ad70e9a04efd0bfa83248b603e)

点击后会看到如下界面，这个界面相信大家都很熟悉，这桌面端打开一个新的PBI文件时的样子，这里我们选择从另一个源获取数据

![](https://secure2.wostatic.cn/static/cRAVADmJGyJiREdTVCqBAf/image.png?auth_key=1655613222-aRYDBWXgWYCSnAFJUUXU1A-0-8186c1bcec5110faf8ae656f8e1fd9c7)

虽然界面和桌面端可能不大一样，但看到Power Query，简直不要太亲切

![](https://secure2.wostatic.cn/static/eMGKe2vkc7EjjTYieMLkNq/image.png?auth_key=1655613229-6UeU9Swu1i8yt6eP52gcPi-0-f7ae8e2a96b2674a7bc1527da9407aed)

这里我选择的是本机的sql server（需要提前创建网关，）

![](https://secure2.wostatic.cn/static/7Zp32fktJU38qrNXUV74mp/image.png?auth_key=1655613235-2MmUWKaU4Y59NSdMGtWvqt-0-ccdc5a86a44cab24e5b36825d07971e6)

加载相关表，然后转换数据

![](https://secure2.wostatic.cn/static/4JEhWLUeRFRonz2dtZEFT3/image.png?auth_key=1655613243-7q7Eq8qVRSuf7Gb6Xwq5Ha-0-abed2ef57c00014dc4c8ffde85c78e93)

这个界面肯定就更亲切了，简直是和PowerBI中的Power Query界面一模一样，这里我们不做任何修改，直接保存。

![](https://secure2.wostatic.cn/static/6nPbWqhKNVxD5o5RUFYvZs/image.png?auth_key=1655613249-dLLWHEankttVjxUY4VXS42-0-7b696113e93ea1a5bd4176e3790f1b64)

## 创建模型

### 修改关系

加载完数据后，在左下方可以进行功能区的切换，先切换到视图，这里可以修改模型的关系，这里已经自动创建好了关系我们不需要修改，如果需要修改，方法和在PowerBI中也是一样的。

![](https://secure2.wostatic.cn/static/avtfAMZyvkPYivmzanrBth/image.png?auth_key=1655613257-2gBdpF6gxPTcTQDRcoS5uo-0-fdffa253926f83d9e554455ac945ed36)

### 运行SQL

这个是数据市场独有的功能，它带一个完整的sql编辑器可供运行sql查询 ，运行结果可以直接在excel中打开。

![](https://secure2.wostatic.cn/static/fy7Sr7JSd5i3cdhMz2LW9z/image.png?auth_key=1655613265-uavDyAWJzexguFBYwGKTx2-0-6914649fff0f2ee9a7010687402c4746)

### 新建Query

这个功能是基于可视化的Power Query操作来创建查询，只是目前还未上线

![](https://secure2.wostatic.cn/static/oZmGNfrzXhsfj72Ry5j9D/image.png?auth_key=1655613273-n326q5hrejzZ8hN8pew8UX-0-38afb9997fa7f727e68c6875ac6a1c59)

官方演示效果如下

![](https://secure2.wostatic.cn/static/8acBU6LAp79BKkFu8jcbkB/image.png?auth_key=1655613281-tEWd849yco2HJ39FgrBGqj-0-b24eb4b388fc8d512d928163d8946180)

### 新建度量

sql都支持了，没理由不支持书写DAX啊，我们可以使用dax来构建指标，并可以设置指标所在的文件夹与格式

![](https://secure2.wostatic.cn/static/6tqW9HWphB1BY2wkL3hVAp/image.png?auth_key=1655613288-bTC965BcmbcZ6GMJpViZaJ-0-c9afd976e0d090cd6c54a3247b32b8fe)

### 设置角色

简单构建好数据模型后，接下来就是分发数据了，同桌面端一样，我们可以根据用户类型创建角色，不同角色分配不同的用户。

![](https://secure2.wostatic.cn/static/eBS65BuLwHoRtDqVQ6pu7S/image.png?auth_key=1655613295-neBoGKsNX9QZxNVsTG6JVt-0-35beecf14d0e6c9b1951b25795b1a538)

分配用户

![](https://secure2.wostatic.cn/static/5QwGfYNDATDVDNZtHs4cv2/image.png?auth_key=1655613302-vf8thFqTFhdmUWbJHUfEYY-0-9d97e959c649cdf88823133215a525b6)

回到工作区，重命名数据市场，默认的名称是一串字符不好区分，我们需要重新命名

![](https://secure2.wostatic.cn/static/xfAddWeYsmQCWCwb6ygwzC/image.png?auth_key=1655613308-tPJAQKASaVj6vfezgRFc9F-0-ff6dc98229ee7429df8eff076c39158d)

## 使用数据市场

在工作区中可以切换到数据市场来找到我们创建的数据市场，同样也可以在数据中心筛选数据市场，来查看所有的数据市场

![](https://secure2.wostatic.cn/static/epKncA2Z7QwusDtvPWA62u/image.png?auth_key=1655613315-c6j5VE2T6cNC2SnYUWVSTz-0-05ba3c3f934910038248c43e5a3c0f97)

点击去数据市场的详细页面会发现和数据集的详情页基本一致，可以看到它所属的工作区，也可以创建报表，还可以共享给其他人，当然，这里多了一个sql连接字符串

![](https://secure2.wostatic.cn/static/tZGbd6J38AKW7MzzywW1Q3/image.png?auth_key=1655613323-bu8E2GwMUnpJc6qTHTNgAJ-0-3ee2858f2421b73169adff7ac663cba8)

### SSMS连接数据市场

进入到数据市场的设置页面，然后复制连接字符串

![](https://secure2.wostatic.cn/static/iW77CwfxYxYQ7Tt13z3SLv/image.png?auth_key=1655613330-t5dEJJviFHYNDHoKRUmSLx-0-710c14ece41b8e8fd3e9eed621156ae6)

![](https://secure2.wostatic.cn/static/acr9AvEpGev6krDeSRr9pW/image.png?auth_key=1655613338-iqeYVj9cXNY7D4sHpUTxD7-0-a59f7f5544a0820ae93707c0b339acc6)

打开SSMS,连接数据市场，使用PowerBI账号进行身份认证

![](https://secure2.wostatic.cn/static/oU4fdJhrM3CNvkhrGB1o9o/image.png?auth_key=1655613346-ofscZsbtcv5LnX3w2F57Q7-0-e995656fe35663b8d14dd58368ac4f72)

接下来就可以像操作sql数据库一样查询数据了。

![](https://secure2.wostatic.cn/static/5Z6J2p6V63GqcW256aK6P5/image.png?auth_key=1655613353-oTTyC7gGxy5QwGRtRsWs1W-0-0b15022ced75a1cc47630a3cbbc91146)

### 创建报表

选择创建报表，然后我们可以进入到创建报表页面了，这个界面和桌面端基本是一样的，而且是server端早就有的功能，就不再详细展开了。

![](https://secure2.wostatic.cn/static/qAH1HkRf5qQBbV7E6Nnnux/image.png?auth_key=1655613360-nMLeRp5WURYmFeTx46ESCS-0-3e17947daeae665044147fcd0a6878ac)

## 总结

这确实是一个很重磅的功能，但是对于PowerBI人员来说又不算是新功能，因为都是我们熟悉的功能，只不过现在集成到Server端了，至于它的企业级应用场景还需要进一步的探索，当然，可能对于大数mac用户来说，终于不用在虚拟机里写dax了。