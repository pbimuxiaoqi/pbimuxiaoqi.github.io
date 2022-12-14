---
created: 2022-06-19
tags: 管理员 其他
subject: 功能
importance:
skilled:
status:
author:
url: https://www.wolai.com/muxiaoqi/8NHdUsydADZspzJC6oPMTR
cover: 
---

Excel作为一个像素级的BI工具或者小型数据库有着其不可替代的场景，但是随着企业BI的发展，BI工具肯定需要进行统一，那怎么让这部分Excel用户转为PowerBI用户呢？

新建一个Excel文件，插入—数据透视表—PowerBI中的数据透视表

![image.png (833×439) (wostatic.cn)](https://secure2.wostatic.cn/static/haDFGaZSW1w14ChZLSuMVD/image.png?auth_key=1655993515-5KcW5R6vhnVXsNutDuq4K9-0-ade480b9979cd939ed6be42614767f24)

选择一个数据集

![image.png (465×626) (wostatic.cn)](https://secure2.wostatic.cn/static/8PyNcyDHiXRMq27BsGysgT/image.png?auth_key=1655993523-tQBhbcEKVmf9YUza6aCb9Y-0-e9c56cc9fc26aba4c4a6620f990a2c8c)

然后随便拖一个透视表出来

![image.png (1273×442) (wostatic.cn)](https://secure2.wostatic.cn/static/w8pRFwV5LXKb6bZez8DnxL/image.png?auth_key=1655993531-byVhFnRZ3XptQkgcq2bbsG-0-7159c210b2adac0356c777dc9c4234ee)

如果我们想要图表展现，选择透视表数据，然后选择想要的图表

![image.png (665×408) (wostatic.cn)](https://secure2.wostatic.cn/static/f5vT64ysaNLALPguX4DPbS/image.png?auth_key=1655993538-oKj3Pz6F5UptQnAbsqZ7Po-0-bcb611b8ecbb1fec954ef2433606d6de)

效果如下，点击保存。

![image.png (606×572) (wostatic.cn)](https://secure2.wostatic.cn/static/qr2FPtNiSy7bZyr99dXUtx/image.png?auth_key=1655993547-uWuK4yQAVXVrDfUR4HGtPu-0-ace6769a296e7d63a7f6b1b8bc3176c4)

回到PowerBI Server端，新建—数据集—文件—ondrive(sharepoint也行)—在PowerBI中查看连接管理Excel

![image.png (343×353) (wostatic.cn)](https://secure2.wostatic.cn/static/dYppMgH8LXJ9EgJm8Ms6Kp/image.png?auth_key=1655993557-oRcmtYRSQ25jgAwh7xZhFv-0-034ece332dcd109412ac4d05f791c7a8)

![image.png (1147×438) (wostatic.cn)](https://secure2.wostatic.cn/static/oJL1BLY26AQewaJvaACxen/image.png?auth_key=1655993565-4mtZ7GfXKCeMNAFA5BF2f7-0-dae2e56d70c5dca0da997c6b026836d8)

![image.png (1210×637) (wostatic.cn)](https://secure2.wostatic.cn/static/8kmRFnSkhPvFQGedLULXjh/image.png?auth_key=1655993574-sZmmSehtvdPY4XbXF8e54Z-0-c391562475e865f963bd541ff91aa2e7)

这样我们就能在PowerBI中管理Excel报表了，不过当需要编辑时仍需要返回Excel中修改，Excel修改后，PowerBI也可查看修改后的效果。

![image.png (834×689) (wostatic.cn)](https://secure2.wostatic.cn/static/mFgpDsFxThkJuWCBC6Pfc/image.png?auth_key=1655993582-mVNoaiv5ekCk9X2BnRnEMf-0-21f51e46dff5f5df0d650c7c1a5c3cf7)

虽然方案上也许还不够完美，但是能够在一个统一的地方管理查看报表还是很有必要的，这也是做过很多客户的BI项目，他们通常会在OA里提供一个统一的入口来切换其他系统。当然如果要查看Echarts等非微软系的报表，这种方案就不行了，如果用的是PowerBI Embedded,则可以开发一个统一的门户来统一管理这些不同类型的报表。