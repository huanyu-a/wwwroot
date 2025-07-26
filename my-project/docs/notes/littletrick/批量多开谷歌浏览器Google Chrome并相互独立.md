---
title: 批量多开谷歌浏览器Google Chrome并相互独立
createTime: 2025/07/23 17:09:52
permalink: /littletrick/6icft0uy/
tags:
  - 浏览器
  - Chrome
  - 多开
---
**前言：**

按照此教程多开后的Google浏览器可以实现相互的独立性，每个浏览器上收藏的书签、增加的拓展程序都可以实现独立性并可实现独立记忆性，完全可以实现同时操作几十个账户

![](https://cdn.nlark.com/yuque/0/2024/webp/683747/1717552069069-8a03f8cf-a95b-4d26-9157-9c7b2e4da86f.webp)

![](https://cdn.nlark.com/yuque/0/2024/webp/683747/1717552069145-fcddca4c-9305-4dea-ac6c-da583ec7d943.webp)

一、安装正版Google浏览器

1：安装位置最好选择非C盘，以D盘示例：[https://www.google.com/intl/zh-CN/chrome/](https://link.zhihu.com/?target=https%3A//www.google.com/intl/zh-CN/chrome/)

**二、分身制作**

1、找到你安装Google浏览器的所在目录，选择chrome，单机鼠标右键创建为**快捷方式**

![](https://cdn.nlark.com/yuque/0/2024/webp/683747/1717552069113-af2cbe6b-8f74-40b5-b139-421199d5f313.webp)

![](https://cdn.nlark.com/yuque/0/2024/webp/683747/1717552069290-bc790d4c-0ea8-46b3-9409-95fb2ddbd310.webp)

2：在D盘单独创建一个文件夹，命名为**撸毛浏览器**（命名是你的自由），然后复制chrome快捷方式粘贴到**撸毛浏览器**所在文件夹内，你需要多少个浏览器就粘贴多少个，把每个浏览器都以编号命名

![](https://cdn.nlark.com/yuque/0/2024/webp/683747/1717552069345-86872eaf-2c8d-4ca6-89b9-7a8c2f64c7c4.webp)

3：鼠标右键点击“1-1”，选择**属性**

![](https://cdn.nlark.com/yuque/0/2024/webp/683747/1717552069635-e2da20cc-e0eb-4ee6-a0a4-820ff46d02ee.webp)

4：在**目标（T）**的数值后面输入 **--user-data-dir=D：gugeduokai\1**

**意思就是用户的数据新建一个在D盘上，后面的文件夹可以是真实存在也可以是没有的，然后点击确定； **如果需要手把手教

**注意：--user-data-dir前面是有一个空格的！**

![](https://cdn.nlark.com/yuque/0/2024/webp/683747/1717552069545-7da0159e-e18c-45e0-b3f5-f46dcfdacede.webp)

5：将**目标（T）的数值最后面的\1改成**\2（对应命名过的浏览器 如\1=1-1、\2=1-2 ），再点击确定，接下来依次修改对应浏览器的属性即可

![](https://cdn.nlark.com/yuque/0/2024/webp/683747/1717552069585-d204665d-b64e-4bab-86aa-099ea733e548.webp)

6：双击鼠标左键打开各个浏览器一遍，如下图则表示多开设置成功

![](https://cdn.nlark.com/yuque/0/2024/webp/683747/1717552069767-9b0efcf9-007f-40da-9bf7-fd00f834148f.webp)

**三、批量加载原配置**

注释：此配置可以解决所有多开浏览器共同所需的配置（如100个浏览器共同需要一个插件、一个书签并相互独立）

1：回到Google浏览器安装目录，双击鼠标左键打开**D：gugeduokai**文件

![](https://cdn.nlark.com/yuque/0/2024/webp/683747/1717552069833-345689fb-d8e0-43f4-865c-5aeff2df157a.webp)

2：**D：gugeduokai**内会看到你刚刚设置的所有多开浏览器文件夹（如看不见哪个编号则表示你没有打开过那个浏览器，回到**撸毛浏览器**文件夹内打开一次该编号的浏览器即可显示在**D：gugeduokai**文件夹内）

![](https://cdn.nlark.com/yuque/0/2024/webp/683747/1717552069905-d6e5b140-decb-4786-81d6-038d66394e8a.webp)

3：回到**撸毛浏览器**双击鼠标左键打开1-1，设置所有多开浏览器共同需要的插件、书签等内容。可使用MetaMask一套助记词批量生成100个地址，后面所有打开的浏览器可独立记忆相应编号地址，从而达到一个助记词不同浏览器操作不同地址的目的

![](https://cdn.nlark.com/yuque/0/2024/webp/683747/1717552070107-72675791-dd32-4575-b583-c1110d334301.webp)

4：回到**D：gugeduokai**内，打开“1”文件夹找到**Default**，单击鼠标右键复制，然后依次将**Default**粘贴到所有编号文件夹内替换原有**Default**

![](https://cdn.nlark.com/yuque/0/2024/webp/683747/1717552070058-b10338a3-d70b-4485-b0c9-604c86eda6d6.webp)

5：再次打开浏览器可以看到，两边的内容已经一致了，可以看右上角的插件，还有书签

![](https://cdn.nlark.com/yuque/0/2024/webp/683747/1717552070383-0800a7fb-e2bd-4991-b7f1-b1eb2e01508c.webp)