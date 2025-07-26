---
title: WebDriver object has no attribute find_element_by_xpaths解决办法
createTime: 2025/07/24 16:10:51
permalink: /littletrick/odthgnhe/
---
用Python+selenium写爬虫的时候，网上常用的“find_element_by_xpaths”方法报错，代码如下：

```python
driver = webdriver.Chrome()
test_poet1 = driver.find_element_by_xpaths(r'//*[@id="new"]/div[1]/div[2]')
```

报错内容是：

```python
'WebDriver' object has no attribute 'find_element_by_xpaths'
```

解决办法是，换用

```python
from selenium.webdriver.common.by import By
test_poet1 = driver.find_element(By.XPATH,r'//*[@id="new"]/div[1]/div[2]')
```

没有测试，但估计以下函数都变成相同的使用方式了

![](https://cdn.nlark.com/yuque/0/2023/png/683747/1686289930922-1e058756-a03f-4b87-ae14-dc581cb414f6.png)