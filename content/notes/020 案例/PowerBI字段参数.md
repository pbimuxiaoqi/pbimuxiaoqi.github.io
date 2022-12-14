---
created: 2022-06-19
tags: 字段参数 动态轴 动态列
subject: 功能
importance: 5
skilled: 4
status:
author:
url:
https://www.wolai.com/muxiaoqi/2FiNQi6k3NUYW6yD1KApkD
cover: 
---


在五月份的PowerBI更新中，PowerBI删除了很多好用的功能，确实是很是不解，不过好在带来了一个不错的功能，字段参数

为了使用该功能，首先我们需要启用字段参数，文件—选项和设置—预览功能

![](https://secure2.wostatic.cn/static/wr2tyYRjwG7Yha4zhejkk4/image.png?auth_key=1653117071-iDikgrdMHvkUqaTGbKvRVm-0-0e825644668d30e4aee5726f27f2d05b)

## 动态坐标轴

字段参数的第一功能肯定是可以更方便的创建动态坐标轴的图表了，在这个功能出现之前我们想要实现动态坐标轴，要先创建一张计算表，然后当选中不同类型的字段的时候度量值中再使用不同的虚拟关系，从而实现动态的效果，而这一次PowerBI直接从底面帮我们实现了这个功能，

### 新建字段参数

切换到建模—新建参数—字段
![](https://secure2.wostatic.cn/static/3PegtNEDvr3mcuoBZt7n82/image.png?auth_key=1653117086-2fB6EkQFCCSh2qN4D2HTvw-0-ef66ae3c0f1bddc34b4aedff7047c68a)


选中我们需要的字段 ，可以是同一张表的，也可以是不同表的，当然不同表的字段才更有意义。

![](https://secure2.wostatic.cn/static/3sW4ACAfzfbMFAxHynSpjS/image.png?auth_key=1653117095-v5ZXiSxAp5PFeC1PhGd2pj-0-d0382dd872f5a0797e485d83eced6bc5)

将参数拖动到轴上，就可以直接实现动态切换的效果了

![](https://secure2.wostatic.cn/static/ansceg9EigReMbAR3YWkWe/image.png?auth_key=1653117104-wmzkC2K1oJdxmkmwHWwS5z-0-731b74366c220ebb5c5f77811ea1ac61)

这里我们并不需要再去创建新的度量来判断该使用哪种虚拟关系了，全都为PowerBI来为我们做了，事实上字段参数也可以理解为是一张计算表，官方这个列名的翻译我们先不吐槽，可以看出来这其实是个常见的计算表的写法：字段类型，类型排序，类型值

![](https://secure2.wostatic.cn/static/qLXrnVt32n4uz4rdEAfBve/image.png?auth_key=1653117113-4JjFPXAyagZc8n39CCkCZo-0-4e506c0808851e4cbc10867f8375f30f)


切换到视图—性能分析器，记录分析后，将代码复制到Dax Studio中查看，可以看到底层其实是帮我们建立虚拟关系的。
![](https://secure2.wostatic.cn/static/r2upujbnuShQUY1EKat7NU/image.png?auth_key=1653117125-rQwyC2KkVPSoypicVwFNNg-0-d0c3ea110b3f8f438432a757d10e91e8)

## 动态度量

有了动态字段的切换，自然是少不了动态切换度量的，同样的在之前我们想创建一个动态切换的度量值也是需要先创建一个计算表的，后来有了计算组也可以轻松创建动态切换的度量值，通过字段参数，会更加简单的实现该功能。同样的方法创建字段参数，只是这一次我们选择度量值。

![](https://secure2.wostatic.cn/static/oXzQGuUTDD3v19vTCr3ZP1/image.png?auth_key=1653117135-o1QkGarTSyAZsAAwQTBzPY-0-2d4131ff9194a76cdf5b512c438db22f)

然后将度量字段放到图表的值中，眼尖的朋友可能已经发现了问题，销售额和同比并列显示了，这样根本无法看出增长率。

![](https://secure2.wostatic.cn/static/r4iaLPcxVuMnCD4K3xEoTT/image.png?auth_key=1653117496-ekdgDq9bhsDsN4taX8R4Ci-0-fa9e7c849cc509f5ea5f8908e0872070)

我们将度量参数拆分为两个，一个包含销售额和销售量，另一个分别包含其同比增长率，倒是解决了上面的问题。但还是会有Bug，比如当我们选择销售额时，另一个字段参数还是可能会误选为销量的同比。

![](https://secure2.wostatic.cn/static/tDkEVRAdjgovHnXTvR7ZKv/image.png?auth_key=1653117510-hwcQGYxnCX49ujuUUKDM5r-0-04bb4e5975e257914b6b7847ee03ec3c)

我们再创建一张计算表，用来区分度量值的类型

![](https://secure2.wostatic.cn/static/sDKza7BFi2SXABJjyKYH6/image.png?auth_key=1653117521-xwSNSke1YxBCEnZQ5Q2kD4-0-b74612287920163d20da80dc1da8ee58)

修改字段参数表，增加类型列

![](https://secure2.wostatic.cn/static/mq8bRhzsh5LCRY6dX9ZVju/image.png?auth_key=1653117530-6PxPE8K8WP1jjXzFx2w2iZ-0-3317539ddd5feb784df2d17a8d3cdf21)

字段参数表和计算表之间创建关系

![](https://secure2.wostatic.cn/static/pnnfDAGzmdqxKBACq4Ganq/image.png?auth_key=1653117544-8WvD3T243ppnb8B9tuvaga-0-f7168ef8655cff77f6ca4cfbce4319bf)

这样就可以解决上面的问题了，但又带来了新的问题。这是因为PowerBI的切片器是有记忆功能的，但这就是PowerBI啊，这样你为了修改一个Bug又改出了N个Bug的过程真的令人着迷。所以我们一定要慎用这个功能，对于非PowerBI开发人员使用时可能会觉得很疑惑。

![](https://secure2.wostatic.cn/static/wqZQEp6sYpkbZ8cp41ie9V/%E5%8A%A8%E7%94%BB.gif?auth_key=1653116815-eMGiEHd7M64TskoE1Eay56-0-edde9a5bbeb411a98f37b7d94809740a)

## 动态列名
```js
参数 2 =

var cur = [Version.Hospital.Cur]

var last = [Version.Hospital.Last]

var diff = "diff"

return

{

("医院销售额.cur", NAMEOF('指标'[医院销售额.cur]), 0, "销售额"),

( "医院销售量.Cur", NAMEOF('指标'[医院销售量.Cur]), 1, "销售量"),

("医院销售行数.cur", NAMEOF('指标'[医院销售行数.cur]), 2, "行数"),

( "医院销售额.Last", NAMEOF('指标'[医院销售额.Last]), 3, "销售额"),

("医院销售量.Last", NAMEOF('指标'[医院销售量.Last]), 4, "销售量"),

( "医院销售行数.Last", NAMEOF('指标'[医院销售行数.Last]), 5, "行数"),

("医院销售额.diff", NAMEOF('指标'[医院销售额.diff]), 6, "销售额"),

("医院销售量.diff", NAMEOF('指标'[医院销售量.diff]), 7, "销售量"),

( "医院销售行数.diff", NAMEOF('指标'[医院销售行数.diff]), 8, "行数")

}
```

