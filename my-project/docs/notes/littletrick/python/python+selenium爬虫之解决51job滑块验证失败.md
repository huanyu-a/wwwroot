---
title: python+selenium爬虫之解决51job滑块验证失败
createTime: 2025/07/24 16:11:08
permalink: /littletrick/dh51b86u/
---
rt，最近公司又有爬虫任务，这次爬虫难度比以往都更大，且一个滑块就卡了我一天多时间，途中尝试了无数的方法，最后发现问题的关键在于两点；当然更关键的，还是在于问题的精准定位。特将本次踩坑之旅记录于此

---

问题描述

很简单，滑块验证界面可以滑动，但滑动后出现如下界面：

问题分析

出现该状况的因素有两种：
```
1. **_window.navigator.webdriver_**在selenium模式下是true，但非selenium模式下是undefined或false（我的浏览器是false），该结果通过网页点击F12，然后到Console中查询可得

2. Chrome浏览器驱动文件（对windows而言就是对应版本的chromedriver.exe）中的【特征字符串】被网站截获，判断出是爬虫所为
```

---

具体而言，以上两种问题会导致不同的后果：

- 问题1/2同时存在：selenium遇到的滑块界面，不论是用代码模拟滑动还是你自己用手去滑动，都会出现上述失败图片
- 问题1解决、2仍存在：selenium遇到的滑块界面，用人手动滑可通过，代码模拟滑动就会出现上述失败图片；或只要代码模拟在滑块页面有过任意操作（不限于点击、右键、滚轮等），就会被发现是爬虫行为，此时不论是人手动还是代码模拟都会出现上述失败图片。

这两点是我后来一点点踩坑摸索出来的，具体原因网上有人解读，我就不班门弄斧了，咱们还是先解决问题嘛！So...

问题解决
```
1. 解决问题1（**_window.navigator.webdriver_**在selenium模式下是true）：
```

Python中，在使用selenium获取driver对象时，加上这句：options.add_argument("--disable-blink-features=AutomationControlled")，即：

```
options = webdriver.ChromeOptions()
options.add_argument("--disable-blink-features=AutomationControlled")  # 就是这一行告诉chrome去掉了webdriver痕迹，令navigator.webdriver=false，极其关键
# 还有其他options配置，此处和问题无关，略去
driver = webdriver.Chrome(options=options)
```

2. 解决chromedriver的特征字符串被网站识别、并被反爬的问题：

在windows下，使用16进制编辑器（如notepad++安装插件HexEditor，网上有不少工具使用和下载说明）；Linux/MacOS下，用以下命令行安装hexedit

```
yum install hexedit # Centos
brew install hexedit # Mac


打开Chromedriver文件（win上是Chromedriver.exe），查找并替换**$cdc_lasutopfhvcZLmcfl**为等量字符的内容（例如**$cxx_lasutopfhvcZLmcfl**），保存再重启浏览器。该问题即解决。
```