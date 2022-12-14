---
created: 2022-06-19
tags: 外部工具 tabular-editor 
subject:
importance: 3
skilled: 3
status:
author:
url: https://www.wolai.com/muxiaoqi/km8xm1UqtKCQrrdBWTPLpP
cover: 
---

一说到快速创建多个度量值，很多人首先想到的应该是计算组，计算组确实很强大，相当于自定义了一个通用模板函数，然后把基础度量值当作参数传入。计算组虽然强大，并不是所有的场景都适用，那还有没有其他的方法来快速创建多个度量呢？

答案是肯定的，有，不然也不会在此废话这么多。同写计算组时一样，还是需要借助于Tabular Editor,且实现思想和计算组如出一辙。

打开Tabular Editor,选择Advanced Scripting

![](https://mmbiz.qpic.cn/mmbiz_jpg/TyDRib9iao84OjBYXrrWp8xxIqmJKr4o1icOID7wwkCCAibiaK1BbXic13STcThg2tuHb4fCddzia7VrIuib04waWEpxNg/640?wx_fmt=jpeg)

这时候就可以来写我们的模板函数，原理也很简单，最外层是一个循环，列表里的值是我们所选的基础度量值，循环里是类似计算组中每个计算项的写法，具体可见下面例子

![](https://mmbiz.qpic.cn/mmbiz_jpg/TyDRib9iao84OjBYXrrWp8xxIqmJKr4o1icHjFMkFf2I1R6mN4Wxibmd3zpFbe1VLltR1odyiaJ6ctzafgU6m4x9JkQ/640?wx_fmt=jpeg)

然后，只要选中我们要用到的基础度量值，然后点击运行即可，效果见下图

![](https://mmbiz.qpic.cn/mmbiz_gif/TyDRib9iao84OjBYXrrWp8xxIqmJKr4o1icZ996C2mZjhuFwNXHibJCdxe3p1PArjESBFPlA7tiaF3jsDFycYeXM7hw/640?wx_fmt=gif)

