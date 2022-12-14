---
tags: NPS
created: 2021-11-20
score: 2
importance:
subject:
---

数据模型如下
![[Pasted image 20211120230507.png]]

首先需要对客户进行打分, 这里用的是平均分
```js
NPS 打分 = AVERAGEX( 'NPS-客户' , 'NPS-客户'[评分] )
```

客户利润率
```js
NPS 利润率 = 
DIVIDE( SUM( '订单'[利润] ) , SUM( '订单'[销售额] ) )
```
接下来就可以对客户进行分类
```js
NPS 客户类型 =
VAR Score = [NPS 打分]
VAR ProfitMarginType = IF( [NPS 利润率] >= 0 , "重要" , "一般" )
VAR NPSType = 
SWITCH( TRUE() ,
	Score >=9 , "推介型" ,
	Score >=7 , "消极满意型" ,
	"贬低型"
)

RETURN ProfitMarginType & NPSType
```
之后就可以求不同类型的客户人数了,因为客户类型其实是根据客户评分得来的，所以它和客户表是有关联的
```js
NPS 客户人数 = 
CALCULATE( 
	COUNTROWS( '客户' ) , 
	FILTER( 
		'客户', 
		[NPS 客户类型] = SELECTEDVALUE( 'NPS 客户分类'[分类名称] ) 
	) 
)
```

接下来其实就可以求不同类型的客户的占比了
```js
NPS 客户人数 % = DIVIDE( [NPS 客户人数] , COUNTROWS( '客户' ) )
```

最后算按类别的打分
```js
NPS 打分 按 类别 = 
IF( 
	[NPS 客户类型] = SELECTEDVALUE( 'NPS 客户分类'[分类名称] ) , 
	[NPS 打分] , 
	BLANK() 
)
```