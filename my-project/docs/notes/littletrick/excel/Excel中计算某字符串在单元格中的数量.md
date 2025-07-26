---
title: Excel中计算某字符串在单元格中的数量
createTime: 2025/07/23 17:01:04
permalink: /littletrick/ezq3liqy/
---
```java
=(LEN(C2)-LEN(SUBSTITUTE(C2,"<p>","")))/3
```

```java
=(LEN(C2)-LEN(SUBSTITUTE(C2,"<h3>","")))/4
```

```java
=(LEN(C2)-LEN(SUBSTITUTE(C2,"<p>","")))/3-(LEN(C2)-LEN(SUBSTITUTE(C2,"</p>","")))/4
```

```java
=(LEN(C2)-LEN(SUBSTITUTE(C2,"<h3>","")))/4-(LEN(C2)-LEN(SUBSTITUTE(C2,"</h3>","")))/5
```

这两个可以计算内容中标签对是否完整，结果为0就是完整的，不为0就是有问题的

