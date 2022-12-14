---
created: 2022-06-19
tags: 主题
subject: 可视化
importance: 4
skilled: 3
status:
author:
url: https://www.wolai.com/muxiaoqi/8yPKqmkEnSqH683Hj8q43j
cover: 
---

今天是教师节，首先祝老师们节日快乐。

实际工作中，我们可能会遇到这样的情况，PowerBI报表中的计算逻辑开发只用了很短的时间，可是UI样式却调了一版又一版，以前常常听做UI的同学报怨说产品经理连原型图都不给我，让我出样式，我都出了几百版了，然后最后用的我最开始的版本。以至于当时网上总时流传着sa了产品经理祭天。

最近在调报表UI的时候就把自己坑了一把，害的自己重复劳动了很久。所以今天就来总结下调报表UI时给自己挖的坑。

---

1.  不要先调好报表后再去总结主题配置，而是要一开始就去配置主题，不然后手动配置的内容应用主题后不会发生变化
2.  参见第1条
3.  参见第1条

废话了这么多，到底应该怎么配置主题呢？这时候首推全球最大交友网站github，已经有国外网友在很久已经就已经总结好了默认图表的主题配置，真的是long long ago

https://github.com/deldersveld/PowerBI-ThemeTemplates

![](https://secure2.wostatic.cn/static/c9mBPoshtVadYPvN7yAUj5/image.png?auth_key=1655817710-pVL5DcMD1yNjL1tL1enR1J-0-4a76ae76c345ed5c99436c6efbcaf6a4)


每一个图表的配置信息都是一个单独的json文件，比如打开Card.json (这里是用浏览器打开的效果，网址是[www.json.cn](https://json.cn)),可以看到我们可以设置这么多的属性。

![](https://secure2.wostatic.cn/static/r4CVq8WH8JKmux27nRkbSk/image.png?auth_key=1655817742-5Wc9omVsk695QPoX7Lsx95-0-6bbf479d6fa789c6dc7dc5cd4416e87e))

那么问题又来了，光默认图表都那么多，怎么可能所有的属性都记住呢。其实一开始写公众号文章时就有分享收集的PowerBI资源里就有在线设置主题的网址链接。

```js
https://themes.powerbi.tips/properties
```

![](https://secure2.wostatic.cn/static/qvDMEwtLbDxVPjrTF5QhyR/image.png?auth_key=1655817784-eaXJCyF2XsDfj35uERsdXC-0-80e4db9f9029fd21e7d9373907faaf91))

图中带*的部分是一些全局通用的配置，比如我们想给所有的图表元素都加一个背景色，那么可以直接在全局配置里设置；如果又有些图表的背景色和全局里设置的背景色不一样，那么下面单独点击这个图表，再设置一次就会覆盖全局的效果。比如下图中的代码，全局的配置时设置了一个背景色，然后页面背景又设置了另一个颜色。

![](https://secure2.wostatic.cn/static/uV6RYEnPDF5VUt81i11zvk/image.png?auth_key=1655817809-poveCo4YKNEmJFmTpeocwD-0-3628e9da906ec8bbe50f5b3044db8afc)

这里，再提一下页面的配置，上面两种方式中都未提示页面主题的配置，我们在PowerBI中打开自定义主题会发现页面只能调整页面壁纸和背景。

![](https://secure2.wostatic.cn/static/crqSbTQRGDDRhuaS4bMmW7/image.png?auth_key=1655817829-qdMKBZLNMRvc7pkLfPnnHK-0-0004e2dd1f02609cde68685d2c14d30b)

比如下面这串代码，就分别设置了页面的背景和壁纸

```JSON
"page":{
            "*":{
                "background": [{
                    "show": true,
                    "color": {
                        "solid": {
                            "color": "#FFFFFF"
                        }
                    },
                    "transparency": 0
                }],

                "outspace":[{
                    "show": true,
                    "color": {
                        "solid": {
                            "color": "#000000"
                        }
                    },
                    "transparency": 0
                }]
            }
        }
```

如果我们想设置图表也可以，不过图片就需要转成Base64了,同样网上有很多免费的web工具可以使用，比如下面这个

```JSON
https://c.runoob.com/front-end/59/     //图片转base64
```

转码之后就可以套用如下配置。

```JSON
"page":{
  "*":{
    "outspace":[{
        "image":{
          "name":"image",
          "scaling":"Fit",
          "url":"图片转base64后的代码"
        },
        "transparency":90
      }]
  }
}
```

---