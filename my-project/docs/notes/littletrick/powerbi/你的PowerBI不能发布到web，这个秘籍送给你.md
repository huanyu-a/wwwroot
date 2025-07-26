---
title: 你的PowerBI不能发布到web，这个秘籍送给你
createTime: 2025/07/23 16:53:33
permalink: /littletrick/u0cdbpqj/
---
<font style="color:rgb(25, 25, 25);">正常情况下大家应该已经上班了，但这个突如其来的延长假期，你是不是感到很无聊、以及焦虑，其实在家安安静静的学习提升也不错，让自己提前进入工作状态。</font>

<font style="color:rgb(25, 25, 25);">比如趁这段时间里认真学习一下PowerBI，有什么问题也可以随时在知识星球中向我提问。</font>

<font style="color:rgb(25, 25, 25);">这两天有不少人后台问我，</font>**<font style="color:rgb(25, 25, 25);">PowerBI账户不能发布了怎么办？</font>**

<font style="color:rgb(25, 25, 25);">很多人应该也已经发现了，现在你想在PowerBI服务中，将报表发布到web时，会弹出这一条信息：</font>

![](https://cdn.nlark.com/yuque/0/2021/png/683747/1624327602901-af38c0d6-e587-47a3-8438-2778cfc36526.png)

<font style="color:rgb(25, 25, 25);">如果你们有管理员，让管理员在门户中设置一下就行了，设置方法如下：</font>

![](https://cdn.nlark.com/yuque/0/2021/png/683747/1624327618669-01f58b5b-0a2f-4a1a-a075-b02fece89279.png)

<font style="color:rgb(25, 25, 25);">但是，如果你之前是用个人邮箱免费注册的，你的界面不会有“租户设置”，因为你不是管理员，</font>

![](https://cdn.nlark.com/yuque/0/2021/png/683747/1624327610218-5511c0fb-4f89-46a3-b60d-bd9b8cc604c3.png)

<font style="color:rgb(25, 25, 25);">并且你也很可能找不到管理员，这怎么办呢？</font>

<font style="color:rgb(25, 25, 25);">这里给你介绍一个超级方法，让你不仅能免费拥有一个账户，并且你就是这个账户的管理员，你可以自己决定是否发布到web。</font>

<font style="color:rgb(25, 25, 25);">下面是操作步骤：</font>

**<font style="color:rgb(25, 25, 25);">1，注册Azure账户</font>**

<font style="color:rgb(25, 25, 25);">网址：https://portal.azure.com</font>

![](https://cdn.nlark.com/yuque/0/2021/png/683747/1624327611092-443f4d79-5adc-42db-ab04-24f9d2aa703a.png)

<font style="color:rgb(25, 25, 25);">这个没有企业邮箱的限制，使用个人邮箱就可以注册。</font>

**<font style="color:rgb(25, 25, 25);">2，新建资源</font>**

![](https://cdn.nlark.com/yuque/0/2021/png/683747/1624327626034-22700d04-0014-4bb5-8f4d-28c70d74b7ea.png)

<font style="color:rgb(25, 25, 25);">↑ 点击新建资源</font>

![](https://cdn.nlark.com/yuque/0/2021/png/683747/1624327616118-abe9cce8-24c1-4b3d-bff4-928f83e842c9.png)

<font style="color:rgb(25, 25, 25);">↑ 搜索Azure Active Directory</font>

![](https://cdn.nlark.com/yuque/0/2021/png/683747/1624327621762-0efa9693-4922-4602-81f6-a960f6c9403b.png)

<font style="color:rgb(25, 25, 25);">↑ 点击创建</font>

![](https://cdn.nlark.com/yuque/0/2021/png/683747/1624327625147-e1f488d2-7950-4fd8-853f-99f6557ac31c.png)

<font style="color:rgb(25, 25, 25);">↑ 输入组织名和初始域名</font>

<font style="color:rgb(25, 25, 25);">这里可以任意输入你想要的域名，只要别人没有使用过就行，然后稍等片刻，注册完成，点击“此处”管理新目录 。</font>

**<font style="color:rgb(25, 25, 25);">3，新建用户</font>**

![](https://cdn.nlark.com/yuque/0/2021/png/683747/1624327626296-c0e0cd8d-814f-416c-92ec-3ef140b110a3.png)

<font style="color:rgb(25, 25, 25);">↑ 点击“用户”</font>

![](https://cdn.nlark.com/yuque/0/2021/png/683747/1624327630207-cd3e7526-5487-4a58-b603-dfd1f3db077e.png)

<font style="color:rgb(25, 25, 25);">↑ 新建用户</font>

![](https://cdn.nlark.com/yuque/0/2021/png/683747/1624327632525-13182dc3-379d-4c1d-bb61-d839b7b958b7.png)

<font style="color:rgb(25, 25, 25);">↑ 输入用户名</font>

<font style="color:rgb(25, 25, 25);">此处的密码可以自动生成，也可以自己新建密码，它就是第一次登录的密码。</font>

![](https://cdn.nlark.com/yuque/0/2021/png/683747/1624327652596-3b927d15-cf4c-4179-8395-476ad38b9792.png)

<font style="color:rgb(25, 25, 25);">↑ 分配权限</font>

<font style="color:rgb(25, 25, 25);">这里权限非常多，你可以先设置一个全局权限，其他的以后慢慢研究。</font>

<font style="color:rgb(25, 25, 25);">到这里账户注册完成，并且拥有管理员权限，进入PowerBI服务中（app.powerbi.com),使用这个账户登录就行了，</font>

![](https://cdn.nlark.com/yuque/0/2021/png/683747/1624327631276-8a0eeaae-2b97-48c5-850d-2d7b2c662b6b.png)

![](https://cdn.nlark.com/yuque/0/2021/png/683747/1624327650334-4af2d5e8-f0de-4809-8852-09e299e248a7.png)

<font style="color:rgb(25, 25, 25);">你想怎么发布到Web都可以，这个账户你也可以激活60天的Pro服务。</font>

<font style="color:rgb(25, 25, 25);">到这里，是不是看出来了，这个方法完全免费，甚至不用到处找企业邮箱，就能让你可以拥有一个权限十足的PowerBI管理员账户。</font>

<font style="color:rgb(25, 25, 25);">此方法仅供个人Power BI学习之用，实际工作使用时如有敏感数据，请自行购买PowerBI相关服务。</font>

