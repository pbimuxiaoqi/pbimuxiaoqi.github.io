---
created: 2022-05-15
tags: 权限
subject: 权限管理
importance: 5
skilled: 5
status:
url:
cover: 
---

先来回顾下在上篇文章时留下的问题，一个公司内部有很多业务员，分别归属于不同人的经理，现在要求业务员只能看到自己的数据，但是经理可以看到下面所有业务员的数据。

我们先来分析下这个问题，这个问题其实就是传播链路的问题，借用百科的组织架构图来看可能会更清楚些，比如账务审计部所在的链路就是：公司总裁办>总经理>常务副总>财务审计部，他之前的所有组织都有应该有权限看到他下面所有的数据。如果我们再给这条传播链路中的每个角色一个唯一编号，比如上面的链路是1>2>3>4。

![](https://secure2.wostatic.cn/static/7PDnDiZxgfAFT4YynNEQsH/image.png?auth_key=1652598623-gjcY1FkPk7BjtioExYrTTs-0-8699a34fd996fd7d691bf945da657220)

这个思路我们可以在PowerBI中应用，我们需要先构造一张组织架构表

![](https://secure2.wostatic.cn/static/wyhSnzJqREdTpVJKpdgBD9/image.png?auth_key=1652598633-aTnQESbQAM9bj1EudUm6JK-0-8bf2271fe31d1921c98cd0ffbabd35f9)

其中层级为计算列，这里主要用到了PATH这个函数，详细用法见[PATH - DAX Guide](https://dax.guide/path/)，公式如下：

```js
层级 = PATH('权限控制'[业务员编码], '权限控制'[主管编码] )
```

和原先的业务人员表建立双向关系

![](https://secure2.wostatic.cn/static/qoc4xRifpCTs8T4dHf1JNg/image.png?auth_key=1652598643-7Q3eNJYMD81XxkPSMkkKm7-0-6ba5c3f1ed1034b06856b502d2cbb2fa)

接下来是角色权限的控制，我们只需要去控制权限控制表就好了。PATHCONTAINS的详细用法见[PATHCONTAINS - DAX Guide](https://dax.guide/pathcontains/)

```js
PATHCONTAINS (
 '权限控制'[层级],
  MAXX(
    FILTER(
      '权限控制', 
      '权限控制'[邮箱]= USERPRINCIPALNAME()
    ),
   '权限控制'[主管编码]
  )
)
```

![](https://secure2.wostatic.cn/static/dQg5b6yDvrc6JH3faPKEwC/image.png?auth_key=1652598656-d9PF53wrqWYZR4LfqS72vS-0-349330405533a8ac904ad263a830dba6)

接下来我们通过实际效果来解释这段代码

![](https://secure2.wostatic.cn/static/oQGpWohbBrjDMBJLhGq46M/image.png?auth_key=1652598668-2ynqAbP9CkJVS3eHFnk2o6-0-256df511676269b50bbd5c517ace402b)

相信看到效果后，代码已经不用解释了，上述代码作用很简单把包含当前查看者编码的所有记录都筛选出来。

---

我们在工作中遇到的实际情况肯定要比文章中的要复杂的多，有时因为模型的限制，我们写起起来可能要更复杂的多，但是遇到问题时不要怕，静下心来仔细想想怎么把那未知的问题转换为我们已知的问题，一步步拆解，可能就会变得相对来说容易些。