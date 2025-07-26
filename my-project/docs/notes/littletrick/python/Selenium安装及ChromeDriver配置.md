---
title: Selenium安装及ChromeDriver配置
createTime: 2025/07/24 16:10:59
permalink: /littletrick/zeg3i76c/
---
**基本概念**

**Selenium是什么？**

Selenium是用于Web应用程序测试的工具。Selenium可以直接运行在浏览器中，模拟用户在浏览器中的各种操作，包括但不限于点击、复制、填写等。

有时，我们需要在浏览器上进行重复多次的操作。例如不断地点击“下一页”按钮获得新的内容，或者是将本地的内容复制粘贴到网页中等等。这些枯燥费事的操作可以通过Selenium模拟我们的行为而完成。

**ChromeDriver是什么？**

Selenium支持多种浏览器，包括ie、Firefox、Chrome等等。不同的浏览器与Selenium之间进行通信的载体不同，ChromeDriver就是Chrome浏览器与Selenium进行通信的载体。

本文主要介绍用Python调用Selenium及ChromeDriver的方法。

---

**安装步骤**

1.安装Python的Selenium库：

打开cmd，输入

```
pip install selenium
```

2.安装Chrome浏览器后，确定Chrome的版本：【设置】-【关于Chrome】中查看，例如图中Chrome的版本是90.0.4430.212

![](https://cdn.nlark.com/yuque/0/2023/webp/683747/1683168428231-074a87b0-d19c-4311-9c01-4102524c880f.webp)

3.安装Chromedriver：从镜像索引网站中下载与Chrome相同版本的Chromedriver。网站地址为：[https://npm.taobao.org/mirrors/chromedriver/](https://npm.taobao.org/mirrors/chromedriver/)

[https://googlechromelabs.github.io/chrome-for-testing/](https://googlechromelabs.github.io/chrome-for-testing/)

![](https://cdn.nlark.com/yuque/0/2023/webp/683747/1683168428219-58ddc4b1-e4e9-4d13-a398-5f974945e90c.webp)

将Chromedriver下载后，解压到Python所在的目录。

![](https://cdn.nlark.com/yuque/0/2023/webp/683747/1683168428491-88c03036-e32b-42d0-8391-ba548aacfdb4.webp)

4.测试安装是否成功：

在Python的IDE中执行：

```
from selenium import webdriver
browser = webdriver.Chrome()
browser.get('https://mail.163.com')
```

如果弹出Chrome窗口，说明安装成功

![](https://cdn.nlark.com/yuque/0/2023/webp/683747/1683168429573-a0e8d3e9-01b7-4196-83c9-f6dd1d6a0234.webp)

---

**运用案例**

Selenium安装及ChromeDriver配置只是使用Selenium的基础工作。为了充分运用Selenium，还需要用到定位、操作等等知识。以下代码用于模拟用户登陆163邮箱，作为Python使用Selenium的简单案例介绍。

```
#导入时间库和selenium库
import time
from selenium import webdriver
#加载Chrome
browser = webdriver.Chrome()
#登陆163邮箱
browser.get('https://mail.163.com')
#程序暂停3秒钟，等待页面完全加载
time.sleep(3)
#分别在user和key中输入自己的用户名和邮箱密码
user = 'XXXXXX'
key = 'kkkkkkkk'

browser.switch_to.frame(0)
#模拟在网页上输入用户名
browser.find_element_by_name("email").clear()
browser.find_element_by_name("email").send_keys(user)
#模拟在网页上输入邮箱密码
browser.find_element_by_name("password").clear()
browser.find_element_by_name("password").send_keys(key)
#模拟在网页上点击【登陆】按钮
browser.find_element_by_id("dologin").click()
```