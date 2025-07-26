---
title: Excel中多单元格及自定义字符合并同一单元格
createTime: 2025/07/23 17:05:37
permalink: /littletrick/3mdt8fty/
---
所用函数：CONCATENATE、<font style="color:rgb(51, 51, 51);">CONCAT</font>



<font style="color:rgb(51, 51, 51);">【用途】将多个区域或字符串中的文本组合起来。 早期版本的 Excel 使用CONCATENATE 函数。</font>

<font style="color:rgb(51, 51, 51);">【语法】CONCAT(text1, [text2],…)</font>

<font style="color:rgb(51, 51, 51);">【参数】</font>

<font style="color:rgb(51, 51, 51);">text1，要连接的文本项。 字符串或字符串数组，如单元格区域；</font>

<font style="color:rgb(51, 51, 51);">[文本2] ， ...：可选，要连接的其他文本项。 文本项最多可以有 253 个文本参数。 每个参数可以是一个字符串或字符串数组，如单元格区域。</font>

<font style="color:rgb(51, 51, 51);">【备注】</font>

<font style="color:rgb(51, 51, 51);">如果结果字符串超过 32767 个字符（单元格限制），则 CONCAT 返回 #VALUE! 错误。</font>

<font style="color:rgb(51, 51, 51);">示例中我们在E2单元格输入公式：=CONCAT(A2:D2)，回车键确认，再选中E2单元格，鼠标双击单元格右下角，完成整列文本合并。</font>

![](https://cdn.nlark.com/yuque/0/2022/jpeg/683747/1646798011248-d2edea23-6bd2-40d1-8075-9f84f9fed529.jpeg)

  
 

