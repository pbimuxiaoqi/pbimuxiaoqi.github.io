---
created: 2022-05-15
tags: 权限 
subject: 权限管理
importance: 5
skilled: 5
status:
url:
cover: 
---

企业报表中，不可避免的要遇到权限管理的问题，上次有介绍到PowerBI中报表页权限的控制，这次做一个小结，介绍更多权限管理里中可能遇到的情况及解决方案。

先来看最简单的方案，某公司在业务线分为国内和国外，相应的某些人只能看国内的业务数据，某些人只能看国外的。

数据模型如下

![](https://secure2.wostatic.cn/static/vvuwAq3cWa6aoURXSxNG5v/image.png?auth_key=1652598389-fakXuVE5eBmhjwfekRJqg-0-1af1da797773f12b292d6ec09f8b77f4)

实现起来也比较简单，我们只需要建两个角色

![](https://secure2.wostatic.cn/static/kt9zodMKM4FXBxGPfKfvZt/image.png?auth_key=1652598446-4G5mYHKBAnqt4spHdUJixh-0-a37fe2aacdf77c9f601314889198e34b)

先前演示的时候都是直接在桌面端演示的，昨天有介绍怎么申请开发者账号，所以今天发布到web端看下具体效果

1、授权访问报表

![](https://secure2.wostatic.cn/static/qrDTzmNRfXgdegZePUxk18/image.png?auth_key=1652598463-i5GzwTQxFrPhjHChz6A5h1-0-06fb50c2c0347cd77980fdffaf4a5a21)

2、数据集—安全性—给角色添加用户，将用户分配到不同角色里

![](https://secure2.wostatic.cn/static/grKfvvLGnhSuFNbatyimXh/image.png?auth_key=1652598472-b1fnye1fPGgaBQpUk313pv-0-84160daa26beed6b6fedf593dfc5cf54)

3、查看效果

![](https://secure2.wostatic.cn/static/31YMqoxDgv3mz83c1D3QaJ/image.png?auth_key=1652598482-9qE1TJWe2DQRTKRqHEa58d-0-f91c88751b4747e046394c4137ecc5ba)

可以看到这两个非管理员权限的用户都只能看到对应权限的数据，注意，这里我们还有个用户是管理员，它是不受权限管理的控制的，这里需要特别注意。

![](https://secure2.wostatic.cn/static/j7EZN3oyc1S9CdTgbd2qEJ/image.png?auth_key=1652598493-iYgQtP7BzNj6Vvk3RgXjjB-0-00e7252528c24b7831d47e5e6e6e8b41)

这是最简单的实现权限管理的方式，如果我们有很多的业务大区，每个大区下又有很多人，采用这种方式也可以，但是后续就需要花费大量的时间来维护了。

接下来看另外一种情况，有公司内有很多业务员，业务员只能看自己的数据，模型如下

![](https://secure2.wostatic.cn/static/nFMydBdGJhWgB8cr85uuDC/image.png?auth_key=1652598503-2UrQCMqCtXgcqmZipYzh87-0-2cf5b8d743b1901ffa4c7b2e0f55abd3)

这种情况还是很简单，只需要控制业务员表的就行了。

![](https://secure2.wostatic.cn/static/89gyYCFugjyJe1pYpmCz9i/image.png?auth_key=1652598513-eFTf3tJrEaNwHGo6jsdFQL-0-dc363864336c1109e6b2881266f89717)

再来个稍微复杂的情况，现在公司内还是有很多业务员，每个业务员只能看自己的数据，但要求经理可以看到下面所有业务人员的数据，那我们该怎么做呢？