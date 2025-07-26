---
title: Excel判断某一列有相同文本内容,在另一列自动填充递增序号
createTime: 2025/07/23 17:05:46
permalink: /littletrick/m5krk4q8/
---
Excel判断某一列(如B列)有相同文本内容,在另一列(如C列)自动填充递增序号

输入公式:

=IF(COUNTIF(B:B,B1)=1,B1,COUNTIF(B$1:B1,B1))

