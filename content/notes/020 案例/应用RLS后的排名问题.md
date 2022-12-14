---
tags: RLS
created: 2021-11-12
score: 4
importance:
subject: RLS
---

RLS,行级别权限控制前面已经介绍过，相信大家已经很熟悉了，在应用RLS后，每个用户只能看到自己权限内的数据这是毋庸置疑的，可是，这往往也会带来一些问题，比如某个人只有上海的数据权限，但是他也需要看到全国的总完成情况，那应该怎么做呢？
 这种时通常是新建一张全国数据的计算表，不受权限控制，然后不同权限的不同用户就都能看到全国的完成情况了。
 那么，又有一种情况，排名呢？不同角色进来后看到的仍然是全国数据的排名，但看到不非权限下地区的具体数值。同样地可以通过写计算表来实现，但是今天来介绍另外一种方案。
 先来看数据模型，模型比较简单，只有三张表
 ![[Pasted image 20211114205247.png]]
 基础度量如下
```js
Sales = SUM( 'FactSales'[sales])

Rank by Province base =
RANKX( ALL( 'DimProvince'[province] ), [Sales])
```
新建一个角色 
![[Pasted image 20211114210449.png]]
查看效果会发现只能查看河南的数据，又因为因能查看河南的数据，所以排名是1
![[Pasted image 20211114210648.png]]
为了实现我们想要的效果，我们需要做一些改变
去掉双向安全筛选
![[Pasted image 20211114210856.png]]
新增一个辅助列
![[Pasted image 20211114210940.png]]
这时再来查看效果，仍然无法得到我们想要的结果，继续下一步操作
![[Pasted image 20211114211100.png]]
修改度量值,页面添加筛选器，这时我们就可以得到想要的结果了
```js
Rank by Province =
RANKX( ALL( 'DimProvince'[province] ), CALCULATE( [Sales], ALL( 'DimUser'[index] )))
```
![[Pasted image 20211114211313.png]]

---

