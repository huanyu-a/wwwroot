---
title: Photoshop批量替换文字并导出图片
createTime: 2025/07/23 17:10:45
permalink: /littletrick/xit3l6tm/
tags:
  - 文本处理
  - ps
---
在制作图片物料的时候，有时会碰到需要制作大量内容格式一致，但部分文字或图片不同的图片，这里我们使用PS的变量功能

**物料准备**：准备好需要替换的图片和文字，使用excel制作出需要替换的内容，第一行name和pic是变量名，下面分别是对应需要替换的文字和图片地址，使用txt文本制作也可以

![](https://cdn.nlark.com/yuque/0/2020/png/683747/1606817370203-64c1f5b1-ac39-4cde-9c53-71eaa18c8e2b.png)

**模板制作**：用PS把模板做好，这里我做了三个图层，文字图层是替换文字的地方，图片图层是替换图片的，给图片曾做了一个矩形蒙版，这样能保证显示的图片大小一致

![](https://cdn.nlark.com/yuque/0/2020/png/683747/1606817370218-703915a4-1aaf-4787-8854-37ba44574e93.png)

**设定变量**：PS 图像 > 变量 > 定义

![](https://cdn.nlark.com/yuque/0/2020/png/683747/1606817370208-09d21e91-31d3-428a-94d2-ab00f18124f3.png)

**选定图层“城市”，勾选文本替换，名称为“name”，选定图层“图片”，勾选像素替换，名称为“pic”，这里使用的名称就是上面excel表格中使用的变量名**

![](https://cdn.nlark.com/yuque/0/2020/png/683747/1606817370241-7ed8fb6d-8ab5-43f7-b7e6-ae48475c38c1.png)

![](https://cdn.nlark.com/yuque/0/2020/png/683747/1606817370264-f73ed28e-1d13-4090-aa6c-c5b9b1bf0dce.png)

**切换到数据组，导入变量文本**

![](https://cdn.nlark.com/yuque/0/2020/png/683747/1606817370239-67e9431c-e0c3-46d4-aa42-ace701bb73e3.png)

**勾选预览后可以看到效果图**

![](https://cdn.nlark.com/yuque/0/2020/png/683747/1606817370262-db4e1d3a-cf50-4b3c-874d-02d897faf30b.png)

**生成文件** PS 文件 > 导出 > 数据组作为文件

![](https://cdn.nlark.com/yuque/0/2020/png/683747/1606817370322-2ea02877-05cc-4a67-a406-d274a02a3725.png)

至此，我们就得到了不同内容的psd文件，再使用ps 文件 > 脚本 > 图像处理器，或者文件 > 自动 > 批处理，得到jpg图片

![](https://cdn.nlark.com/yuque/0/2020/png/683747/1606817370297-d2863a6c-3e60-4305-9543-7e99952d07d4.png)

最终效果图

![](https://cdn.nlark.com/yuque/0/2020/png/683747/1606817370320-4e46f79c-6872-4810-abd6-a5880902e7ea.png)

