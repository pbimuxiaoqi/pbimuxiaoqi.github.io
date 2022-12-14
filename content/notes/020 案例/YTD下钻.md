---
tags: 下钻
created: 2021-11-19
score:
importance:
subject: 
---

```js
Sales Value = SUM('Sales'[Sales])
```

```js
YTD Sales = CALCULATE([Sales Value], DATESYTD('Date'[Date]))
```

主要用到下面这个度量
用到两个函数[[CROSSFILTER]], [[CONTAINS]]
```js
SalesIgnoringDate =
var CurrentDateFromSales =
CALCULATE(
	SELECTEDVALUE('Sales'[Date]),
		CROSSFILTER(
		'Date'[Date],
		Sales[Date],
		None
	)
)
return
IF(
	CONTAINS(
		DATESYTD('Date'[Date]),
		'Date'[Date],
		CurrentDateFromSales
	),
	CALCULATE(
		[Sales Value],
		CROSSFILTER(
		'Date'[Date],
		Sales[Date],
		None)
	)
)
```



下钻到月度明细页，明细页用SalesIgnoringDate

![[Pasted image 20211119164030.png]]