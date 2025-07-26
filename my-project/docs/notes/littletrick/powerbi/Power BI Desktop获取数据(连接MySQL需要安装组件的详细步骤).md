---
title: Power BI Desktop获取数据(连接MySQL需要安装组件的详细步骤)
createTime: 2025/07/23 16:53:05
permalink: /littletrick/m2ytluiv/
---
### <font style="color:#48b378;">Power BI Desktop获取数据</font>
主界面

![](https://s2.51cto.com/images/blog/202306/01161528_647853a0e2c6b98996.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

获取数据非常简单，支持的数据来源非常全面，点击获取数据，更多...，就可以从不同来源获取数据。其中连接MySQL获取数据需要安装其他组件。



在学习Power BI之前建议大家先学习MySQL，因为少量数据的时候基本上excel就可以，但是企业中我们通常数据来源于数据库，而最为通用的sql语句便是MySQL的语句，包括分布式集群等的查询sql，和mysql基本一致。作者整理的MySQL教程[ 《数据分析与运营-MySQL篇》](https://mp.weixin.qq.com/s?__biz=MzI1NTEyODAxOA==&mid=2247488736&idx=2&sn=4f9199ea78577c2eb17c288914d73dc2&chksm=ea3bec5ddd4c654b9707fec105d5e29bf8402519d1236eccdc8fd63e232182ed268543dc05b2&scene=21#wechat_redirect)大家也可以免费下载学习。

### <font style="color:#48b378;"> 从MySQL数据库中获取数据</font>


![](https://s2.51cto.com/images/blog/202306/01161529_647853a131f9f33986.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

提示需要其他组件，点击了解详细信息

![](https://s2.51cto.com/images/blog/202306/01161529_647853a15290031940.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

跳转到网页，点击下载

![](https://s2.51cto.com/images/blog/202306/01161529_647853a19130421561.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

点击下载

![](https://s2.51cto.com/images/blog/202306/01161529_647853a1b95922105.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

下载完成，点击安装（需要注意的是，如果你的mysql没有配置好环境变量，那么此插件需要安装到当前你的MySQL目录才能生效）

![](https://s2.51cto.com/images/blog/202306/01161529_647853a1dc0cb66752.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

![](https://s2.51cto.com/images/blog/202306/01161530_647853a2124404968.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

![](https://s2.51cto.com/images/blog/202306/01161530_647853a23eaeb69411.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

![](https://s2.51cto.com/images/blog/202306/01161530_647853a26889889989.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

![](https://s2.51cto.com/images/blog/202306/01161530_647853a2910bd93486.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

安装结束，重启Power BI，连接MySQL数据库

![](https://s2.51cto.com/images/blog/202306/01161530_647853a2c1d4426914.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

![](https://s2.51cto.com/images/blog/202306/01161530_647853a2e56f255256.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

![](https://s2.51cto.com/images/blog/202306/01161531_647853a30f78285333.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

![](https://s2.51cto.com/images/blog/202306/01161531_647853a33162543817.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

连接成功

![](https://s2.51cto.com/images/blog/202306/01161531_647853a3527b580406.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

这样数据中的表我们都可以看到，后续可以选择需要分析处理的表进行使用。



到此，Power BI Desktop获取数据就到这里了，大家可以进一步摸索。更多内容点击关注





