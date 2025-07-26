---
title: github操作流程
createTime: 2025/07/24 16:10:42
permalink: /littletrick/kphv4ccg/
---
1. 创建私有仓库  
    点击右上角的 **+** 按钮，选择 **New repository**

![](https://cdn.nlark.com/yuque/0/2025/png/683747/1742869130338-49f4d227-f53b-4254-a348-613558c55d7a.png)

![](https://cdn.nlark.com/yuque/0/2025/png/683747/1742869130596-41f5203a-975a-4e52-b7d2-0654c571e6c0.png)

1. 安装git终端

[https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git](https://git-scm.com/book/zh/v2/%25E8%25B5%25B7%25E6%25AD%25A5-%25E5%25AE%2589%25E8%25A3%2585-Git)

![](https://cdn.nlark.com/yuque/0/2025/png/683747/1742869131052-813b5edd-80cd-4e62-a8f7-08397235b523.png)

打开自动下载：[https://git-scm.com/download/win](https://git-scm.com/download/win)

  
3、配置 GitHub 认证

使用最新的githubToken方式

1. 点击github个人头像  
    2、点击setting
2. 跳转后左侧最下方Developer settings点击  
    4、跳转后选择左侧Personal access tokens -> tokens
3. 点击屏幕中间的generate new token 生成token（**一定要保存好生成的token**）

![](https://cdn.nlark.com/yuque/0/2025/png/683747/1742869131368-ccb2d13f-7162-451e-98fa-2f8682dff122.png)

### 1 填写 Token 描述和选择所需的权限，通常你需要选择 repo 权限来进行代码推送和拉取  
![](https://cdn.nlark.com/yuque/0/2025/png/683747/1742869131672-79f0839f-7131-4030-a78c-8787c225789e.png)

### ![](https://cdn.nlark.com/yuque/0/2025/png/683747/1742869131947-9ae4be46-a262-49fe-a1af-3b861c18eb34.png)

### Permissions你点开每一项，都给设置成读和写的权限![](https://cdn.nlark.com/yuque/0/2025/png/683747/1742869132255-b7e0ba62-fe7d-45c3-a546-5cff5b66d65d.png)

然后直接生成 generate token

![](https://cdn.nlark.com/yuque/0/2025/png/683747/1742869132653-885ae752-ea3a-435d-a0f8-e5ca454291e5.png)

**切记后续找不到这个token，点击复制保存好**，

7、配置你本地的git客户端

在你存储代码的目录下，右键选择open git bash here，打开终端，然后回到你的github刚才创建的私有库中：

![](https://cdn.nlark.com/yuque/0/2025/png/683747/1742869132956-db8f28aa-28fb-4535-b3b8-e1e1a070a808.png)

然后在终端直接git clone [https://github.com/JianhaoCoding/test_case.git](https://github.com/JianhaoCoding/test_case.git) 就是你复制的那个链接，然后**cd** 到这个目录下

系统会提示你输入 GitHub 的用户名和密码：

1、输入 GitHub 的 **用户名**。

2、在输入 **密码** 时，直接粘贴你之前生成的 **GitHub Token**，这将替代密码

8、修改代码后提交流程：

git add .  
git commit -m "描述一下你修改的信息(不重要，abc都行，只是标记一下你改动了什么)"

git push origin master 推送代码到仓库

第一次推送或者没有缓存认证信息，系统会提示你输入 GitHub 用户名和token，它显示的让你输入密码，不用输入密码直接用刚才生成的token，用户名就是你注册github的时候的邮箱或者手机

1. 避免每次操作都输入用户名和 Token，你可以配置 Git 让它缓存

git config --global credential.helper cache（最好用这个因为token会过期）

永不过期的：git config --global credential.helper store

1. 更新代码,估计你用不到基本  
    git fetch  
    git pull origin master