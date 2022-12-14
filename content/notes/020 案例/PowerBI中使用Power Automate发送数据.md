---
created: 2022-06-25
tags: autoomate 其他
subject: 其他
importance: 2
skilled: 5
status:
author:
url: https://www.wolai.com/muxiaoqi/CmrggAFM89ubBtuvjCzvk
cover: 
---
一说到全家桶大家首先想到的可能是某基，也可能是某度。今天我要说的是巨硬，继分页报表之后，Power Automate也被集成到了PowerBI，这就增加了更多的可玩性与可能。

比如，最近的项目中就遇到甲方爸爸要求再看报表中数据时，看到某个数据有问题需要记录下来，然后方便开会时讨论该问题数据。只是两点要求:

一，不需要跳转到其他系统录入

二，方便查看。

PowerBI表示无能为力，只能转身向Power  Platform家族的其他成员求助，Automate站了出来，说这简单，让我来。

  

本次案例使用的是PowerBI自带的示例数据，且为了简化流程事前已经在onedrive中建好了一个表，这里要注意，这是一个表。

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84PVyvfY883acaUzym8KW7V9babjerL7tXoSw5llQrCH1JzMCAInBITTOZoax7Lw1gfUXXEhrJJGyA/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

接下来就完全是在PowerBI中操作了，新建一个Power Automate视觉对象并将需要存储的字段拖入

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84PVyvfY883acaUzym8KW7V9K7XmIlYjiayTL9zLJv0uWtbhID2UDxicLOaibibFwlAwCZWmboBRn6iaB0w/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

接下来右上方占击编辑

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84PVyvfY883acaUzym8KW7V9GxtbsQLLpZhwbgdZPCibnZQHI264ErDCAjvNXTlz2PsLapibTwE3StCw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

新建一个空的工作流

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84PVyvfY883acaUzym8KW7V976X6454m4QYhsNy1ic5ibkwWVSMepa6KB298XJHlw7uI70ugjnxicmM7A/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

插入新的步骤，选择Excel Online > 在表中插入新行，然后选择刚新建的excel文件，并一一对应字段值

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84PVyvfY883acaUzym8KW7V9aIWChMCbtl1wf1g3u6dPcBGUcqgCs7QfyPYXvoZo7NibZeDNUqicIeuQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

  

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84PVyvfY883acaUzym8KW7V9wRJicMyhzUNll6QyjpqlQ5XRT7SjJTbok0UZEzOpvks0eqZl6p9ia3iaA/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/TyDRib9iao84PVyvfY883acaUzym8KW7V9PETHxT53faDEZFYicUic9Rr8j1lpJwiaBnicJylAedEx0Zp2GmbXQfbWPg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

保存并应用，返回报表，选中图中某个值，然后点击应用（桌面文件需要按Ctrl）

![图片](https://mmbiz.qpic.cn/mmbiz_gif/TyDRib9iao84PVyvfY883acaUzym8KW7V9m1z8YvscDdLDwlYwVm9bgVjedHkdnueSO2duVt7G6cTbKQASxPvI8g/640?wx_fmt=gif&wxfrom=5&wx_lazy=1)

可以看到数据已经写入文件了，当然这里因为只是演示功能，工作流做的很是简单，比如我们在插入数据时还可以创建一个teams聊天窗口，将数据发给相关的负责人，也可把PowerBI数据集刷新也加进来了。