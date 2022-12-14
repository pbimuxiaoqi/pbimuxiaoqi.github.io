---
created: 2022-06-19
tags: RLS 排名 
subject: 权限
importance: 3
skilled: 4
status:
author:
url: https://www.wolai.com/muxiaoqi/6uTBDY1j5eQvCDGuAL9awr
cover: 
---

RLS,行级别权限控制前面已经介绍过，相信大家已经很熟悉了，在应用RLS后，每个用户只能看到自己权限内的数据这是毋庸置疑的，可是，这往往也会带来一些问题，比如某个人只有上海的数据权限，但是他也需要看到全国的总完成情况，那应该怎么做呢？

这种时通常是新建一张全国数据的计算表，不受权限控制，然后不同权限的不同用户就都能看到全国的完成情况了。

那么，又有一种情况，排名呢？不同角色进来后看到的仍然是全国数据的排名，但看到不非权限下地区的具体数值。同样地可以通过写计算表来实现，但是今天来介绍另外一种方案。

先来看数据模型，模型比较简单，只有三张表

![](https://img-blog.csdnimg.cn/img_convert/056688622c2c09caa0fcea4d43ddd835.png)

```js
Sales = SUM( 'FactSales'[sales])

  
Rank by Province base =
RANKX( ALL( 'DimProvince'[province] ), [Sales])

```

新建一个角色

![](https://img-blog.csdnimg.cn/img_convert/2491745132e26fd0c149883f56f7aefe.png)

查看效果会发现只能查看河南的数据，又因为因能查看河南的数据，所以排名是1

![](https://img-blog.csdnimg.cn/img_convert/23eefd6bd2df1f68db893e848dafcb00.png)

为了实现我们想要的效果，我们需要做一些改变

去掉双向安全筛选

![](https://img-blog.csdnimg.cn/img_convert/7d2ef5fef011599989cdfdf03659af73.png)

新增一个辅助列，前面模型其实已经加好

![](https://img-blog.csdnimg.cn/img_convert/b5d86503aa6678b1b70df745fbe9fbec.png)

这时再来查看效果，仍然无法得到我们想要的结果，继续下一步操作

![](https://img-blog.csdnimg.cn/img_convert/02e0a6a7995507aba54c0895f32107ec.png)

修改度量值,页面添加筛选器，这时我们就可以得到想要的结果了

```
Rank by Province =
RANKX( 
  ALL( 'DimProvince'[province] ), 
  CALCULATE( [Sales], ALL( 'DimUser'[index] ))
)

```

![](https://img-blog.csdnimg.cn/img_convert/db098a3affa9cdf108da1817f4dfa57a.png)