---
title: 超级简单连接mysql和excel的方法
createTime: 2025/07/23 17:05:26
permalink: /littletrick/b0en1vi2/
---
mysql数据库查询得结果要手动导出才能用EXCEL打开，如果有数据更新了，WTF？！那又得再导出一份xlxs？想想是不是觉得反效率得事情？  
今天就连接mysql数据库和excel，实现数据同步！给大家介绍一种简单得办法，再也不用反复导导导数据！！！！

😄先po出流程图![](https://cdn.nlark.com/yuque/0/2022/png/683747/1647067300622-0175d6d5-abdf-4af6-917f-6528fa5446e6.png)

第一步：
1.1下载mysql的obdc  
1.2官方网址：https://dev.mysql.com/downloads/connector/odbc/  
1.3版本：看自己的电脑配置，如果是64位的话，选Windows (x86, 64-bit) 就可以了  
1.4安装完毕

科普：①obdc是Open Database Connectivity的缩写，意为开放式数据库连接，实现有结构差异的数据库结构之间的连接，相当于是数据库的一种统一接口。  
②MSI Installer是microsoft installe，是微软格式的安装包，一般为程序的安装软件。

第二步：
这一步的话目的是连接mysql和mysql obdc  
1.1打开下载好的obdc，以管理员的身份运行，会按顺序弹出以下的窗口![](https://cdn.nlark.com/yuque/0/2022/png/683747/1647067300347-42c6f4a9-d43b-4275-bf30-aafde5caf99c.png)![](https://cdn.nlark.com/yuque/0/2022/png/683747/1647067300336-29da6d04-50c1-43fa-a7c5-12070923ca2d.png)  
![](https://cdn.nlark.com/yuque/0/2022/png/683747/1647067300421-e99c31c9-6d87-4c58-8bc7-3eeb782a2fad.png)  
![](https://cdn.nlark.com/yuque/0/2022/png/683747/1647067300313-98dcc121-9cb3-4c97-ada6-c9f76805a3ac.png)  
到这步了，就说明我们的mysql和 obdc已经连接成功了，那我们下一步就开始搞定[excel](https://so.csdn.net/so/search?q=excel&spm=1001.2101.3001.7020)

第三步
这一步的目的是把mysql和excel连接起来  
1.1打开excel（我的版本是2019）  
  
![](https://cdn.nlark.com/yuque/0/2022/png/683747/1647067302971-70ff8c2a-e942-48d7-9878-b7b2abeee5ac.png)  
![](https://cdn.nlark.com/yuque/0/2022/png/683747/1647067302625-fa1686b8-9515-4f2e-8c00-40d694232485.png)

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1647067302975-deabae1e-7189-4716-939c-13fd8267f246.png)  
![](https://cdn.nlark.com/yuque/0/2022/png/683747/1647067303030-0649ed22-31fa-4315-9cca-2555a84eec7a.png)

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1647067303544-4e8cd038-bebb-43a3-9ea3-bbc2094cd3a8.png)

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1647067303948-0c1ad8ab-7444-46d3-8ab9-fe16cd43fafc.png)  
![](https://cdn.nlark.com/yuque/0/2022/png/683747/1647067304172-6083693d-dfbc-48b4-85a8-6b96cfcede02.png)

最后！！！！最后！！！如果你想让表跟着你数据库的内容更新的话！！！  
我们就一定要刷新！  
![](https://cdn.nlark.com/yuque/0/2022/png/683747/1647067304222-45fe9481-c897-4d38-be2f-60a574b3b647.png)

以上，希望对各位有所帮助😆 看完给俺点个赞呗！

