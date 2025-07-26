---
title: EXCEL如何随机生成时间？EXCEL随机生成时间的方法
createTime: 2025/07/23 17:05:05
permalink: /littletrick/7kjlgejs/
---
<font style="color:rgb(74, 74, 74);">EXCEL怎样随机生成时间?两个日期之间又如何自动生成顺序的日期?小编在这里一 一说下操作方法。</font>

<font style="color:rgb(74, 74, 74);">方法/步骤</font>

<font style="color:rgb(74, 74, 74);">1.先说下如何随机生成时间</font>

<font style="color:rgb(74, 74, 74);">比如，要随机生成从2:00:00到2:10:00之间的时间;显示在A1到A10单元格。</font>

<font style="color:rgb(74, 74, 74);">选中A1到A10单元格。</font>

<font style="color:rgb(74, 74, 74);">2.在编辑栏内输入公式：=TEXT(RAND()*("00:10")+"2:00:00"，"HH:MM:SS")</font>

<font style="color:rgb(74, 74, 74);">3.再按键盘的CTRL+回车键;</font>

<font style="color:rgb(74, 74, 74);">4.A1到A10单元格即同时显示出从2:00:00到2:10:00这个时间段的随机时间;</font>

<font style="color:rgb(74, 74, 74);">5.接着来说下，在两个日期内自动生成顺序的日期</font>

<font style="color:rgb(74, 74, 74);">比如，A1单元格显示起始日期2016/12/1;A10单元格显示结束日期2016/12/10;现在要在A2到A9单元格自动显示出这两个日期内所有日期并按顺序排列。</font>

<font style="color:rgb(74, 74, 74);">6.选中A2到A9单元格，然后，在编辑栏中输入公式：=IF(A$1+ROW(A1)</font>

<font style="color:rgb(74, 74, 74);">7.再按键盘的CTRL+回车键;A2到A9单元格即同时显示出日期;日期是按顺序排列的。</font>

