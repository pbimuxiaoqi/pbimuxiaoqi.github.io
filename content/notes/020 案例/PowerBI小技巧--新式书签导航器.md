---
created: 2022-06-19
tags: 书签
subject: 功能
importance: 3
skilled: 3
status:
author:
url: https://www.wolai.com/muxiaoqi/75PdXBySa95CDEKQJcqC7d
cover: 
---
在11月份的更新中，微软带来了新的书签和页面导航，同事之间戏称这是因为快过年了，这是BI部门要赶KPI了，今天就来体验下，新版的书签导航到底怎样。

先来回顾下之前页面存在多个书签时是怎么做的。通常是插入一个空白按钮，然后设置按钮格式窗格里操作属性为书签并选择要跳转到的书签。

![](https://secure2.wostatic.cn/static/iqrEuuR25vvfJwVMVgWFzL/image.png?auth_key=1655639454-bg3ZBciD5xndEtbrTup69b-0-127761ff80673f17b638aeede6655cd6)

效果如下

![动画.gif (1090×718) (wostatic.cn)](https://secure2.wostatic.cn/static/qbjqaQ4FB19XVvbY9TG53/%E5%8A%A8%E7%94%BB.gif?auth_key=1655992562-mQJuuxYEzPxcrHesgw2V4g-0-efc71f4085610da7296645ef267e18d5)

这只是最简单的效果，如果是为了好看，比如AB在选中和未选中时都要用不同的状态来区分，这就要再增加两个按钮了，并根据当前书签的状态有选择的隐藏其他两个按钮。这样设置起来就很麻烦，特别是页面上有大量书签时。

接下来就是今天的主角了，新式书签导航器，插入—按钮—书签导航器

![image.png (930×568) (wostatic.cn)](https://secure2.wostatic.cn/static/mrnW9f8sLsyjEvEdyh84eo/image.png?auth_key=1655992586-sN2zgPZRZWVqyUDmEbhBgq-0-7525ff211676c54388b1a6bdf043bd61)

这时会发现其他页面的书签也进来了，

![image.png (1186×498) (wostatic.cn)](https://secure2.wostatic.cn/static/jWGVyLT6vUormsArfGahnU/image.png?auth_key=1655992602-3yZhyB2hdrMRpUXBFvttpt-0-52bc8757ccaf6dee36ee028cc5fda849)

那有没有办法只显示当前页面的书签呢？显然微软的工程师也是考虑到了这一点的，方法也很简单，对书签创建分组（同样当页面图表元素过多时，也建议对元素进行分组管理，并且设置下元素的名称以方便区分）在书签窗格同时选中多个书签然后进行分组，然后设置书签导航器的书签属性为刚设置的分组。

![image.png (1022×688) (wostatic.cn)](https://secure2.wostatic.cn/static/5tSmabCdeMazsXZknLeEED/image.png?auth_key=1655992612-jXL6orHFf4FVT1ra8wpB4S-0-b779f1e131c3d1e135fb73780d3921e8)

效果如下

![动画1.gif (1090×718) (wostatic.cn)](https://secure2.wostatic.cn/static/5jeJqbyDuGgTs36piyZgVZ/%E5%8A%A8%E7%94%BB1.gif?auth_key=1655992562-nSW52JY2TZn3VH5iJMHC8Y-0-df41cf6b492b7a344c63327122746841)

效果和切片器是类似的，可以很明显的看出当前选中的是哪个书签。因为当前页面只有两个书签，其实还可再设置下默认书签，这样可以进一步节省页面的空间。

方法也很简单，同样是设置书签属性，允许取消选择—选择默认书签

![image.png (961×618) (wostatic.cn)](https://secure2.wostatic.cn/static/pcqjS1sGwMvkrMg7dDPzhX/image.png?auth_key=1655992629-eRmHzih8BAJTuFSwAsoW4s-0-bcfc3be0056538ff4566d8cadfbebdc4)

效果如下

![动画2.gif (1090×718) (wostatic.cn)](https://secure2.wostatic.cn/static/8GDPxP9ggjkTPaXD7Fc8fP/%E5%8A%A8%E7%94%BB2.gif?auth_key=1655992562-i5P9FFNcHkh7Y8cY2Cwz5f-0-a79697aa711536028d619aa0be8d764e)

当然我们也可以更改默认的形状，也可能通过设置旋转角度等变化成想要的形状。

![image.png (811×606) (wostatic.cn)](https://secure2.wostatic.cn/static/mDrNsTfWmSN3VxE67gx4ir/image.png?auth_key=1655992648-aZAqXNy9taPFQJnChtEpi9-0-143cc6fca9776e783a6617df8849d150)

但是，微软还是没有带来导航窗格的锁定，当画面很长时，还是无法固定显示导航器。