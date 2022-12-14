---
created: 2022-06-19
tags: 矩阵
subject: 可视化
importance:
skilled:
status:
author:
url: https://www.wolai.com/muxiaoqi/gEwA2qChQjThxy8QJTN22n
cover: 
---
这是一个真实的事件，就是前几天老板在看新媒体同事发布的文章中的表格时没仔细看，误以为是数据错了，问还能不能修改文章里的数据，不能的话直接删掉把影响降到最低，

新媒体同事做的表格大概就是这样

![](https://secure2.wostatic.cn/static/4C8hz2Bgmih5J82x7Qexbb/image.png?auth_key=1655635681-rUkbybhhkpPweHdAJqJRKU-0-e2d9860bfb7862c9ccebef0ad0c19dc7)

因为第一列命名就是销售，中国又在很后面，就很自然地以为第一列销售就是中国的值，进而得出这是错误的数据的结论，然后。。。

那么我们应该怎么设计一个可读性更强的表格呢？

比如下面这个表格，这是PowerBI中默认的设置，可以看到列总计其实是在最后面的，符合人们从左到右的阅读习惯，不会误把第一列的当成的某个子类别的值

![](https://secure2.wostatic.cn/static/edEFr9cW8AJ5ALteTQhAvV/image.png?auth_key=1655635692-5WLm6fbcJ7YsecRE7K1oWC-0-b9903ce025bf409f0da019a6d146b544)

但是，可读性还是不够强，因为这里存在了很多列，我们可以对列进行背景色设置，默认的是渐变的效果，有些人可能会觉得太过花哨了，那我们可以按列设置间隔色

![](https://secure2.wostatic.cn/static/tQ1YZGrnuEKkHyvQcUdE3r/image.png?auth_key=1655635701-i9XxXmPFfgB2tzM3k9fNYF-0-032c8aaa841c27cf57a8b65e9b22441b)

需要如下度量值 ，最终效果如下, 这里用到了MOD函数，它返回余数

-   因为矩阵中列值放的是国家名，所以这里先新建变量对国家进行排序
-   然后根据排名判断所属的颜色

```js
Color = 
var RankS = RANKX( 
    ALLSELECTED( 'Geography'[SpanishCountryRegionName] ), 
    'Geography'[SpanishCountryRegionName], 
    SELECTEDVALUE( 'Geography'[SpanishCountryRegionName] ), 
)
var Result = 
IF( 
    MOD( RankS, 2 ),
    "#DCC7E1",
    "white"
)
return
Result
```

![](https://secure2.wostatic.cn/static/uV6oiJcM86H325uz9Ks3cK/image.png?auth_key=1655635711-fAoV7J9LGUiKKoEt1u97YF-0-5fef1c4222451b6b6e4893ab5b329482)

数据看上去仍然有些拥挤，我们再调整下样式，选择差异最小

![](https://secure2.wostatic.cn/static/b8hKwPH1BnsSNvK4zewyHa/image.png?auth_key=1655635722-mZ8mL4YNuZnZFn8CoPx4fG-0-15177e9d547d1acbb0faf8ec176635d5)

接下来再调整下网络的属性，调整行填充及文本大小

![](https://secure2.wostatic.cn/static/4QoMkHJwY1bBoL5cePRVNP/image.png?auth_key=1655635730-zB71Js91PUmPyHKpUbqd7-0-ce3f07f67832e71f670c1b154e3d9170)

最后再设置行标题的边框为仅右侧，列标题的边框仅底部

![](https://secure2.wostatic.cn/static/kCvMqKXmngsLkaX8Dig3zL/image.png?auth_key=1655635740-oURzkJSnHC9wrkKdrYB3ki-0-b3902194a7e36cbe3d12f7d5630e5ff1)

这里其实还些问题，水平风格太粗了，但是老版的格式窗格是没办法将水平风格宽度设置为0的，新式的可以，具体如下。

![](https://secure2.wostatic.cn/static/iC4cx9VbRC6V4pU78hGkig/image.png?auth_key=1655635749-d5oegx9p3Dtqz9WKLMwc23-0-22c6f7d3e477a2bd8b566053c049a710)

新格式窗格需要在预览功能中开启(六月更新已正式加入，且无法切换为旧版的格式窗格)

![](https://secure2.wostatic.cn/static/233EVyBoKeV3m2bwrisun3/image.png?auth_key=1655635758-4bHkadcyZdz9mrZPS97DWr-0-22f151abe6fc80a83bd904bee82a9493)

到这里基本上就结束了，当然可以设置的属性还有很多，比如列标题加粗和居中等等，背景色也可以只设置需要重点关注的国家。就像下面这样，这里只是提供一个方法或者说是思路，为了不让用户由于主观意识产生错误的判断，需要对数据颜色做些特殊处理。

![](https://secure2.wostatic.cn/static/dwpfR5BPPScqaWeReH3vwZ/image.png?auth_key=1655635780-8Kj5ji6muacYMjEZFxBtSQ-0-d813b2a0018ed0cedd932b7a1b88bb72)