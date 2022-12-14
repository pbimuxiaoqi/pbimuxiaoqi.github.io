---
created: 2022-06-19
tags: 矩阵
subject: 可视化
importance: 3
skilled: 5
status:
author:
url: https://www.wolai.com/muxiaoqi/6WnGz7HZYYgCWAgAXgdq5C
cover: 
---
在Excel中我们可以很容易地对所有列设置为统一的列宽，然而PowerBI中矩阵并没有给我们提供这样的功能，但我们仍然可以通过一些小技巧来实现。

假设我们需要在矩阵中按月份展示各品类的销售额，因为销售额的大小或月份名称的不同，各列的宽度也不同，看上去会比较乱。可能有人会手动去调整每列的宽度从而让看上去大概是一样的（刚学PowerBI时我就是这么做的），因为PowerBI没办法做到很精确地调整每列的像素宽度，所以即使手动调整也没有办法做到每列宽度都一样，而且手动调整实工作量实在是太大了。

![](https://secure2.wostatic.cn/static/v6NPtAP2nyVwuR8wXDcDuj/image.png?auth_key=1655641890-iDrKPGHWEEmVhZMt6b263T-0-8ff3b1c28abbb9ded703e7b32a9fed1e)

接下来就演示怎么快速地统一设置列宽。

1、新建一个度量值，最好是比销售额总计还要大的值

```js
widths = 1234567890
```

2、把widths放入到矩阵中，然后关掉列标题的自动调整列宽大小

![](https://secure2.wostatic.cn/static/8qhEgju9NkdvRQQra9LbnY/image.png?auth_key=1655992403-hc69qiNi9i52j3VAPNBJ3J-0-051a6f3e3806e2a60c3dc2a7ecaf9abd)

![](https://secure2.wostatic.cn/static/hC5qQNAvfAq56LtuMmbd53/image.png?auth_key=1655992423-vHSwX2YMo9rQbFZjsM71DU-0-6911886a3ba66a9e43cda952769a51e5)

3、将widths替换为销售额

![](https://secure2.wostatic.cn/static/woQbQqEcKBzYn6Lrp1F6MQ/image.png?auth_key=1655992436-5Gw6WVhXuNAPRDJessGbyN-0-a09059decf27bcaf9bd47227e57778e8)

这时再看矩阵，每列都是统一的宽度了。

上面的例子是因为值的宽度不统一，那如果值的宽度也统一的，能不能也这样统一设置呢？

比如，我们要展现下面的矩阵，就不能用上面的方法来调整列宽。

![](https://secure2.wostatic.cn/static/b3zAEa2x4xTZ1fZYBEScgV/image.png?auth_key=1655992454-riR9QueySFYqUyKzQiiYRv-0-e87cd43b1cc5ebbec52f9d4190f24d21)

但，如果列标题是日期格式，仍然可以统一设置，比如下图，值很小，但是列标题很宽，就造成每列很宽

![](https://secure2.wostatic.cn/static/hx8AqrfrfvtgQvTo7A5owt/image.png?auth_key=1655641928-5gNyP9RWANxQfrtEuzU1nL-0-ec72d97c8b079991e9181453ce67a725)

方法大致和上面一样，只不过这次是选择日期列，然后修改日期列的显示格式为mmdd,然后取消列标题的自动调整列宽，并打开自动换行。

![](https://secure2.wostatic.cn/static/hx8AqrfrfvtgQvTo7A5owt/image.png?auth_key=1655992474-9rC54NVXL4zH6wyv1u499E-0-3d23d7365ae45cbe5e1c7ede02e831e5)

之后继续修改日期列的格式为YYYYMMDD,从而实现统一调整列宽的效果

![](https://secure2.wostatic.cn/static/pTx8rt5Nw2JatZL3svftkS/image.png?auth_key=1655992489-4e5zzvje3XuFhFxanGjzwF-0-d069b89538e99beeeeaa7adb423cb44e)