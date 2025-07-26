---
title: 如何快速的合并多个 Excel 工作簿成为一个工作簿？
createTime: 2025/07/23 17:05:17
permalink: /littletrick/h1w8zpd3/
---
全文10000+字，前方高能，干货预警！作为一位办公狂人，花了一个周末的时间整理了 5 种不同工具场合下Excel 工作簿合并的技巧，借着这个话题分享给大家，收藏的同时不要忘记点赞呀~

这 5 个场景涵盖了：PQ合并、WPS合并、csv合并、Mac系统下合并、Python脚本合并、合并工作簿中指定的Sheet等，几乎你能想到的场合我都整理了。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382381302-e65d5cf7-93f2-4e15-b5d8-18d271d7c2ec.png)

另外本文中所有的工具+练习文件+代码，在回答中全部提供了，下载的版本一会我会整理发布出来，希望对你有帮助呀~

另外如果想系统学习 PQ，也可以看下这门课程：[Power Query实战-M函数入门到进阶（数据处理/清洗/采集）](https://link.zhihu.com/?target=https%3A//ke.mongjoy.com/course/4)

## 01、Power Query合并技巧
Power Query 简称 PQ，这是一个 Excel 2016 及以上版本内置的插件，2010~2013 版本可以通过安装插件来实现，通过 PQ 可以不写任何代码实现多种合并：多工作簿、多Sheet表、指定工作簿、指定Sheet表。

当然使用 PQ 的优缺点也非常明显，也整理出来了：

1. 优点：不写/几乎不写任何代码可以实现合并、一分钟即可上手、效率高
2. 缺点：不兼容WPS/Excel 2010以下版本/Excel For Mac，没法合并成多个Sheet表
3. 适合：使用高版本，数据规律的小伙伴

### 1.1 工作簿下的多个Sheet表合并
先从简单的开始，首先是简单的单份工作簿下的多个Sheet表一键合并成一份数据，例如一份工作簿里存放了多个班级的成绩单，需要将所有成绩合并到一起：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382381367-1de09527-d0f7-494b-b3d7-0cfb3dc8af12.png)

这类数据的特征也非常明显：只有一份工作簿、Sheet表数据结构一模一样。

这个时候就可以优先考虑使用 Excel 自带的 Power Query 来进行合并，方法兼容 Excel 2010 或者以上版本，WPS 和 Excel For Mac 均不支持。

① 新建一张工作簿，然后点击「数据」选项卡下「获取数据」，找到「来自文件-从工作簿」，选择需要合并的工作簿，如下：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382381358-692bb76c-e1bd-4ad7-bae1-621fbdf2f8aa.png)

部分 Excel 版本的名字并不叫「获取数据」，不过大致意思类似，统一都在「数据」选项卡下。

② 这时 Excel 会弹窗提示我们要选择导入哪些 Sheet，直接选中「文件名」然后点击「转换数据」将整份文件导入到 PQ 中：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382381312-d6919737-3a30-4950-b37e-a62f324cb2c5.png)

点击「Data」这一列，可以发现，数据虽然导入进来的，但是并没有标题行，可以点击编辑栏，将null 修改成 True 即可。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382381392-7b1c7270-fb03-4ee2-9137-c824ad6241a6.png)

③ 现在 PQ 中会有 4 条记录，代表我们导入的 4 张 Sheet 表，同时多了很多乱七八糟的信息，选中「Data」列，右击选择「删除其他列」，如下：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382383038-ab65c562-dd62-47fb-9533-f26e0ddde705.png)

⑤ 最后一步直接将「Data」列展开，主要不要勾选「使用原始列名作为前缀」，现在数据就成功合并了，如下：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382383027-b3d2fdba-6546-4066-b104-d992d8876df3.png)

展开后，点击「关闭并上载」即可将数据导出到 Excel 中，是不是非常简单。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382383839-73db6a10-6858-4995-bf95-7f55773f3697.png)

而且利用 PQ 导出的数据，优点也非常明显，操作简单+数据改动只需要一键刷新即可更新，例如当我们更新了一年一班的数据后，直接右击点击「刷新」即可。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382383880-3d6b6d0b-5e4a-4b52-a7e7-b48f501eb2ec.png)

是不是非常简单，来看下 PQ 生成的完整代码，如果觉得每次操作都麻烦，也可以打开 Excel 的 PQ 编辑器，直接将代码粘贴进去，也可以运行：

let     源 = Excel.Workbook(File.Contents("C:\Users\zh\Desktop\学习技巧\excel-文件合并\合并文件\各班级成绩单.xlsx"), true, true),     筛选的行 = Table.SelectRows(源, (x) => x[Kind] = "Sheet"),     删除的其他列 = Table.SelectColumns(筛选的行,{"Data", "Item"}),     展开数据 = Table.ExpandTableColumn(删除的其他列, "Data", {"班级", "学号", "姓名", "语文成绩", "数学成绩", "英语成绩"}, {"班级", "学号", "姓名", "语文成绩", "数学成绩", "英语成绩"}),     重命名的列 = Table.RenameColumns(展开数据,{{"Item", "工作表名"}}) in     重命名的列

另外如果想合并工作簿下指定的工作表，在 PQ 中也可以通过筛选的方式来解决，例如只合并“一年一班”和“一年二班”的数据，筛选「工作表名称」列即可。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382384190-c1ebb28b-f0a5-484f-bbe0-d3b0060ba43e.png)

是不是非常简单，以往需要复制粘贴 N 次的操作，现在一键就可以搞定，而且还可以随时刷新。

### 1.2 多工作簿下的多Sheet表合并
接下来演示的就是如何将文件夹内的多个工作簿下的多个Sheet表合并成一张，使用 PQ 来解决 N 个文件/数据合并成 1 个工作表，只能说超级简单！

也就是这个问题的解决技巧，虽然看到有知友分享了，还是来补充下，例如下方：需要将多个年级下多个班级的成绩单全部合并到一起。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382385337-f1f965bf-e9cb-48ff-b80c-944db1f18a7f.png)

打开 Excel 选择「数据」选项卡下的「获取数据-从文件夹」，导入我们需要合并的文件夹。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382385383-681639e9-29a9-4305-ab3d-db9a5ae602df.png)

点击「转换数据」后，由于文件夹中存在 .doc 等非 Excel 文档，我们还需要筛选掉非 Excel 文档，操作也很简单，和 Excel 中的筛选没有差别：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382385665-8565533b-8414-47f3-bb62-2262fb2a4478.png)

选中 Content 和 Name 列，右击选择「删除其他列」，如下：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382386232-a6600627-3096-4757-9dea-9627d14e499c.png)

接下来将数据提取出来，选择「添加列」选项卡下的「自定义列」，命名为“数据提取”，录入以下公式，这个函数的含义也非常简单，根据 Content 列提取内容。

= Excel.Workbook([Content], true)

现在每份文件里的数据都被提取出来了，操作演示如下：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382386545-a83ea5a3-b9d1-441b-897d-ae8a71cb548b.png)

由于我们只要合并工作表，文档里的智能表、透视表等不参与合并，所以需要进一步筛选，将刚刚生成的列公式修改为如下：

= Table.AddColumn(删除的其他列, "提取数据", (x) => Table.SelectRows(         Excel.Workbook(x[Content], true),         (y) => y[Kind] = "Sheet"     ))

操作演示如下，现在就将所有的 Sheet 文件全部提取出来了。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382386902-514fc696-d4a2-4637-8a83-e58ceda470f0.png)

接下来只要依次将多层数据展开，我们的数据就合并成功了，是不是非常简单。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382387100-a5ed3fe9-6a90-4012-8f73-e23aab7fa912.png)

当然在展开的过程中会产生很多新列，只要将无用的列全部删除即可，最后导出来的数据就长这个样子，如下：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382387338-24ba4b29-9761-4d55-80e5-1a11f571b0ab.png)

如果想合并指定的工作簿+工作表，也可以通过筛选的方式来限制，这里就不再重复演示了。

## 02. VBA合并技巧
在 Excel 中除了 PQ 是数据处理利器，VBA 也是一个超强的自动化处理工具，作为一款图灵完备的编程语言，VBA 除了难学些，在 Excel 功能应用于自动化中几乎没有对手。

本节来分享利用 VBA 来合并工作簿的一些技巧，涵盖：合并一张工作簿中的多张 Sheet、合并多张工作簿中的多张工作表等。

当然 VBA 合并也有不少优缺点：

1. 优点：写好的工具可以直接使用，无任何学习成本；
2. 缺点：兼容性不好，不支持 Mac 系统，自己写代码需要扎实的基础；

### 2.1 合并工作簿中的多张工作表
首先依旧是合并某张工作簿下的所有工作表，这里也写了一段代码分享给大家，先来看下实现效果，例如：想要将“各班级成绩单”下的所有工作表合并到新的一张工作表中。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382388336-60e50fa2-eb64-4ad2-803f-a1c0bb7fdb27.png)

只需要打开这个 VBA 合并工具，点击「一键合并」，然后选择这一份需要合并的文档，即可一键完成合并，如下：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382388469-4dc5753b-95e3-489b-b12a-c1c88311007a.png)

代码也粘贴给大家了，不需要理解代码的含义，只需要知道如何将代码粘贴到自己的文件中快速使用即可，代码如下：

```vb
Sub mergeSht()
    '新建一个对话框对象
    Dim wb As Workbook, newWb
    Dim path
    
    With Application.FileDialog(msoFileDialogFilePicker)
        .AllowMultiSelect = False
        '单选择
        .Filters.Clear
        '清除文件过滤器
        .Filters.Add "Excel Files", "*.xls;*.xlsx"
        '设置两个文件过滤器
        If .Show = -1 Then
            'FileDialog 对象的 Show 方法显示对话框，并且返回 -1（如果您按 OK）和 0（如果您按 Cancel）。
            MsgBox "您选择的文件是：" & .SelectedItems(1)
            path = .SelectedItems(1)
        End If
    End With
    
    Set wb = Workbooks.Open(path)
    ' 关闭屏幕刷新
    Application.ScreenUpdating = False
    ' 创建新工作簿
    Set newWb = Application.Workbooks.Add
    
    For j = 1 To wb.Sheets.Count
        X = newWb.Sheets(1).Range("A100000").End(xlUp).Row
        wb.Sheets(j).UsedRange.Copy newWb.Sheets(1).Cells(X, 1) '复制内容
    Next
    newWb.Sheets(1).Range("B1").Select
    newWb.Sheets(1).Name = "合并"
    Application.ScreenUpdating = True
    wb.Close
    MsgBox "工作簿下的全部工作表已经合并完毕！", vbInformation, "提示"
End Sub
```

是不是非常简单呢？这里默认将所有数据全部合并进去了，如果只想合并一个表头数据，修改数据的范围从第 2 行开始即可。

当然如果只想合并某些指定的工作表，可以在合并复制之前使用 if 语句判断，例如只想合并工作表名中包含“芒种课堂”的数据，可以添加补充下面的代码：

dim shtName /*工作表名字*/ if InStr(shtName, "芒种课堂") then     /*工作表名字包含芒种课堂，可以进行合并*/     /*这里放置合并的代码*/ endif

这里由于篇幅原因，就不将完整代码罗列出来了，这些集成的小工具，下午找个时间分享出来给大家，点个赞+收藏，不要错过了哦~

### 2.1 合并多张工作簿下的所有工作表
使用 VBA 合并文件对比 PQ 合并的最大的好处就是写好代码后，点击一个按钮就可以直接使用了，不需要去修改任何代码，使用写好的 VBA 小工具，没有任何成本。

分享的这段 VBA 代码，可以一键将当前文件目录下的所有 Excel 文件里的所有工作表全部进行合并，例如下方想将二年级所有的成绩单进行合并汇总，将工具放到该目录下。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382388805-4cf8a3a8-1664-46ea-83e2-e16532ea35a6.png)

然后点击「一键合并当前目录所有Excel」即可快速合并，标题也默认只引用一张表里的数据，同时在最后一列还标记了这条数据的来源，如下：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382389196-2f713a6f-a426-4761-9aee-51f499ae6472.png)

是不是非常爽，背后的 VBA 代码其实不用理解，只需要下载好这个工具，哪里需要合并就往哪里扔即可，当然这个 VBA 工具我也分享给大家了，希望对大家有所帮助~

另外也将代码粘贴给大家，使用时直接将代码复制到 VBA [编辑器](https://www.zhihu.com/search?q=%E7%BC%96%E8%BE%91%E5%99%A8&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2135040401%7D)中，按F5执行即可，如下：

```vb
Sub 合并目录所有工作簿全部工作表()
    Dim MP, MN, AW, Wbn, wn, Wb As Workbook, i, a, b, d, c, e
    Application.ScreenUpdating = False
    MP = ActiveWorkbook.Path
    MN = Dir(MP & "\" & "*.xlsx")
    AW = ActiveWorkbook.Name
    Num = 0
    e = 1
    Do While MN <> ""
        If MN <> AW Then
            Set Wb = Workbooks.Open(MP & "\" & MN)
                a = a + 1
                With Workbooks(1).ActiveSheet
                    For i = 1 To Sheets.Count
                    If Sheets(i).Range("a1") <> "" Then
                        Wb.Sheets(i).Range("a1").Resize(1, Sheets(i).UsedRange.Columns.Count).Copy .Cells(1, 1)
                        d = Wb.Sheets(i).UsedRange.Columns.Count
                        c = Wb.Sheets(i).UsedRange.Rows.Count - 1
                        wn = Wb.Sheets(i).Name
                        .Cells(1, d + 1) = "表名"
                        .Cells(e + 1, d + 1).Resize(c, 1) = MN & wn
                        e = e + c
                        Wb.Sheets(i).Range("a2").Resize(c, d).Copy .Cells(.Range("a1048576").End(xlUp).Row + 1, 1)
            End If
        Next
        Wbn = Wbn & Chr(13) & Wb.Name
        Wb.Close False
    End With
End If
MN = Dir
Loop
Range("a1").Select
Application.ScreenUpdating = True
MsgBox "共合并了" & a & "个工作薄下全部工作表。如下：" & Chr(13) & Wbn, vbInformation, "提示"
End Sub
```

另外如果想要利用 VBA 合并指定工作簿名或者指定工作表名，需要如何操作呢？其实也超级简单，在读取数据的时候做多一个判断即可。

例如：想要合并工作簿名字包含“芒种课堂”关键词的文件，只需要在合并代码前做多一个判断：

dim wbName /*工作簿名字*/ if InStr(wbName, "芒种课堂") then     /*工作簿名字包含芒种课堂，可以进行合并*/ endif

同理，如果是只合并工作表名包含指定关键词的表，代码也是一模一样的，内层读取数据时多嵌套一层 if 判断语句即可，由于篇幅问题，这里就不放完整代码出来了，这些工具都可以在下面这个链接里下载。

当然如果不会写代码也可以使用，利用上面的 VBA 代码合并后，筛选「新增的列」，筛选后将数据复制出来，也能轻松实现筛选指定工作簿+工作表的功能。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382389797-e1ef6edf-4ac6-4718-880e-327a204e0e3e.png)

  


## 03. WPS合并技巧
上面分享的几个技巧都是在 Excel 中才能使用，其实在新版的 WPS 中，也支持快速合并/拆分了，不过这个功能需要会员才能使用。

WPS 中支持合并/拆分的种类也非常多，例如：按行合并、多工作簿合并、同名工作表重组工作簿、按相同列内容匹配两表数据、多个文档合并成一个文档。

WPS 合并优缺点：

1. 优点：操作简单、无任何学习成本、兼容 Win + Mac、合并种类多；
2. 缺点：除了轻微氪金，好像还行？

### 3.1 按行合并多个工作表内容
首先是将一张工作簿中的多个工作表一键合并，使用 WPS 打开文件，右击任意一张 Sheet 表，找到「合并表格」下的「按行合并」，WPS 会设置弹窗，然后勾选需要合并的 Sheet 表：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382390010-62a73b62-ab9a-453a-93ba-5aea074d8691.png)

这里还有一个配置点，即设置成第 2 行开始合并，否则合并时会将标题也统一合并进去，最后点击「合并」即可将选中的工作表合并到另外一张新的工作簿中。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382390275-e1fb7dde-f5f2-4b72-a004-b60eb5d96968.png)

使用 WPS 合并后，会产生「报告」和「总表」两张新 Sheet 表，其中「报告」表里能看到合并引用了那些数据，并将数据范围也标识出来了，非常智能。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382390600-d52c36d5-1cb3-4a77-b327-c047fa5f3373.png)

「[总表](https://www.zhihu.com/search?q=%E6%80%BB%E8%A1%A8&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2135040401%7D)」里除了原始数据，还会新增一列，用于存放这条数据的工作簿+工作表名，如下：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382390872-6a501701-27cc-4160-8982-3f704b71d01a.png)

这个功能除了能合并同张工作簿下的 Sheet 表，也可以合并多张工作簿下的 Sheet ，操作也很简单，在选择文件的时候，点击右上角的「添加文件」，将其他需要合并的文件一起添加进来即可。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382392948-c0119918-6fbb-4b26-a92e-6c795be65a56.png)

既然能合并，那么肯定能拆分，在 WPS 中与这个功能相对应的就是「按照内容拆分」，我们可以依据某列，快速将单张 Sheet 的内容快速拆分到多张 Sheet 上。

操作也很简单，右击「总表」，选择「拆分表格」下的「按照内容拆分」，如下。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382393231-5b39365e-ad76-4c00-82d1-92eaedd41709.png)

选择拆分依据为「B列」，然后将数据拆分到「不同的新工作表」中，最后点击「开始拆分」即可一键将数据拆分，非常简单。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382394396-10f17d86-779e-4453-b807-35c459bd1a17.png)

另外这个功能其实利用透视表的「分页筛选」也能模仿实现，不过使用起来没有 WPS 这么流畅。

### 3.2 按行合并同名工作表内容
除了合并工作簿中多张 Sheet 表外，如果想合并多张工作簿中同名工作表，WPS 也可以轻松解决，这里我们以合并 2020 和 2021 年三四月的工资表为例。

两份文件结构一模一样，Sheet 表名以月份进行命名，原始数据如下所示。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382394463-7172a631-dee7-4102-95b2-5e355e3ae250.png)

打开其中一份文件，右击 Sheet 表，选择「合并表格」下的「合并同名工作表内容」，如下。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382394567-2aaff804-1147-4f25-9544-4039b512e20b.png)

选择「添加文件」将 2020 年的数据也添加进来，勾选「全选」，由于原始数据是从第 5 行开始的，这里需要修改下数据合并的行数为 5。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382394834-b0c1b382-d573-46ca-b575-09943f86a450.png)

操作完成后，导入的工作簿中，只要是同名的 Sheet 全部会被拼接到一起。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382396092-151642e8-d7da-4266-b00d-0e1cbe97fb06.png)

不过这个合并技巧也有缺陷，只能识别表头，如果表格结尾有页尾数据，WPS 并不会识别出来，一样会全部合并进去，例如下方将签字栏目多次合并到文件中：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382396511-4d6d63fe-9a7c-4d31-adfd-e5caeec88461.png)

不过都是小问题了，通过多个表逐个筛选即可解决问题。

### 3.3 多工作簿合并成一个工作簿
另外如果只是想将所有的工作簿全部拼接到一起，利用 WPS 也可以轻松实现，例如想将各班级的所有成绩单全部汇总到一起，避免来回切换工作簿的繁琐。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382396428-528be29d-f963-4b5a-9726-b8f928409b69.png)

和前面两个技巧不一样，多工作簿合并成一个工作簿可以忽略 Sheet 的表名进行合并，打开任意一个需要合并的文件，右击 Sheet 表，选择「多工作簿合并」，将需要合并的工作簿添加到进来。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382396719-38d1f367-9f2b-4ede-bb05-e0c76c25ad65.png)

勾选需要合并的 Sheet 表，同时在底下的「选项」配置中，还可以配置工作表表名，例如：添加文件名后缀、添加文件名前缀等。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382397346-7943eadf-07a7-4893-8152-068b01421cd2.png)

点击「开始合并」，稍等片刻即可合并完毕，是不是非常简单。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382397896-9e0deff3-b0b3-4772-b1a3-db9969b3b8ba.png)

现在工作簿下所有的 Sheet 就被合并到一份工作簿中并独立存在，如果是想将他们全部拼接在一张 Sheet 表中，可以参考下 3.1 的使用技巧。

同样既然是将多张 Sheet 合并成一份，拆分起来也非常简单，右击 Sheet 表，找到「拆分表格」下的「按照工作表拆分」，如下。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382398468-c9c14f44-fe46-4692-8407-3a7cfacdc2a9.png)

勾选需要拆分的 Sheet 表，并配置保存位置，点击「开始拆分」则可以一键将合并后的数据全部分离成为一个个独立的文件。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382398936-b0f2c6b4-7708-4257-aa6d-248f4da7abb2.png)

### 3.4 基于同名工作表重组工作簿
除了上面的这 3 种常规的合并，WPS 还可以快速将多个工作簿中同名的 Sheet 分别单独提取成一份文档，例如上面的工资表案例，2020和2021年的文档里均有 3 月和 4 月的数据。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382399214-9d19214a-1e5e-4ed8-8eac-86fda735a275.png)

想单独将 3 月和 4 月的数据放到一份工作表里，操作也非常简单，打开任意一份需要合并的文件，右击工作表，选择「合并表格」下的「基于同名工作表重组工作簿」，导入你需要操作的文件并选择需要操作的工作表。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382399366-544faf03-abf9-4cc8-88b2-b0bdfe02397f.png)

配置好「保存位置」后，点击「开始重组」即可实现拆分重组。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382399751-9ba9d1ce-152e-4b9e-a166-c79b8b57abe1.png)

重组文件后，会生成一份「报告」文档，在这里你能看到所有重组的文档记录，打开重组的工作簿，可以发现所有的同名工作表全部合并到一起了，并且工作表的名字变成了工作簿名。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382400880-3de46cc8-bdac-427d-b903-ebc8e98a2178.png)

是不是非常快，对于重组成多表，PQ 是一点办法都没，而使用 VBA 学习成本太高，这块 WPS 实在太香了！轻度氪金换来效率的极致提升。

### 3.5 多个文档合并成一个文档
这也是 WPS 提供的最后一个合并功能，一键将多个文档合并成一个文档，既然叫「合并文档」，也就意味着这个功能不仅能合并 Excel，对 Word、PPT、PDF类的文档也可以一键合并。

右击工作表，选择「合并表格」下的「多个文档合并成一个文档」，在这里可以导入 Excel、Word、PPT 甚至 PDF 文档，如下：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382401309-ef18f88e-6e4c-4875-b7c9-08285cc55c5f.png)

点击「下一步」可以进行其他配置，例如：合并的页面范围，这个小工具的合并是以页数范围作为标准的，这样可以兼容 Word、PPT 和 PDF，同时配置好输出名称+目录，即可一键合并。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382401448-c513d580-4b32-49ec-9146-a20b8df6aa84.png)

稍等片刻后，选中的工作簿就被合并到一起了，和 3.3 的技巧看起来没有差别。

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382401569-f2e59d52-5ffd-4212-85ad-df836441950a.png)

不过 3.3 的技巧只能合并 Excel 工作簿，而这里可以合并其他的文档类，下次拼接 Word、PDF 再也不需要一页一页去复制粘贴了，使用 WPS 轻松搞定。

## 04. CSV/命令行合并技巧
另外除了 .xlsx 和 .xls 之外，Excel 也可以导出 .csv 格式的数据，如果需要合并的文件恰好是 csv 文件，那么技巧就会更简单一些，利用命令行即可轻松实现合并，例如下方数据：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382401508-6bdd233d-bd1e-4717-9279-784f49601446.png)

csv 文件本身可以看成是 xlsx 文件的缩略版，可以看成是存储数据的文本文件，不存储任何样式、公式、并且默认只有一张表，数据与数据之间使用逗号和换行符分隔。

当我们使用记事本打开 csv 就可以看到类似这样的数据结构：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382402594-36f59445-0f03-48f6-ad1e-29fb066d9f6d.png)

既然是一份文本数据，那么就可以考虑直接使用命令行来合并，而且超级简单。

找到合并的文件夹，点击「编辑栏」，输入命令“cmd”后回车，打开命令窗口，如下：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382402940-c2e31c28-f740-45b6-881c-437d90b5dae1.png)

然后输入下面的 Bash 命令：

```python
cat *.csv > all.csv
```

稍等片刻之后，就可以看到所有的 csv 文件全部被合并到“[all.csv](https://www.zhihu.com/search?q=all.csv&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2135040401%7D)”文件中，如下：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382403187-4fb8fd56-f82e-41dc-a07b-5f964834c65a.png)

简单解释下这句代码的含义，即将所有的 csv 数据统一拷贝到“all.csv”文件中，这个命令适用于所有文本型的文件，将 csv 换成 txt 也支持。

打开合并后的文件，如下所示，所有的数据包括标题全部合并到一起了，还需要通过筛选来清除多余的标题，操作也非常简单：

![](https://cdn.nlark.com/yuque/0/2022/png/683747/1649382403980-f55cabe1-9950-4c10-906b-12c14455344b.png)

另外上面的这个命令是 Windows 的童鞋使用的，如果是 Mac 的小伙伴，可以改成这个命令：

```python
cat *.csv > all.csv
```

同样也可以实现将多个 csv 合并到一个文件中，使用命令行来合并数据优缺点也非常明显：

1. 优点：操作简单，兼容Windows/Mac，速度快，且无需其他软件支撑；
2. 缺点：只适用于文本类文件，xlsx不支持该操作，只能合并csv中的一张表，无法拼接多张表；

## 05. Python合并数据
作为日常使用频率最高的编程语言，利用 Python 来合并数据也异常简单，毕竟绝大部分功能通过安装第三方包就可以快速解决。

小北也分享了几段代码用于合并 Excel 文件，涵盖：合并工作簿中的多个工作表、合并工作簿中指定的工作表、合并文件夹下的所有工作簿等。

使用的第 3 方包有：pandas、openpyxl，版本诶 Python 3，兼容 Windows+Mac 系统，代码如下：

```python
# -*- coding: utf-8 -*-
"""
Created on Thu Sep 16 23:30:06 2021

@author: 86043
"""
def concat_child(filename):
    """ 
    一个表格中多个子表数据合并 
    filename：文件路径及名称
    """
    import openpyxl
    import pandas as pd
    #filename = '多子表合并.xlsx'
    wb = openpyxl.load_workbook(filename)
    # 获取workbook中所有的表格
    sheets = wb.sheetnames  
    all_data = pd.DataFrame()
    for s in sheets:
        sheet_df = pd.read_excel(filename, sheet_name=s)
        all_data = pd.concat([all_data, sheet_df])
        # 索引重排序
        all_data = all_data.reset_index(drop=True)
        return all_data
    
    def concat_amdchild(filename, sheetnames):
        """ 
        指定一个表格中某些子表数据合并 
        filename：文件路径及名称
        sheetnames：子表的名称（列表）
        """
        import openpyxl
        import pandas as pd
        #filename = '多子表合并.xlsx'
        all_data = pd.DataFrame()
        for s in sheetnames:
            sheet_df = pd.read_excel(filename, sheet_name=s)
            all_data = pd.concat([all_data, sheet_df])
            # 索引重排序
            all_data = all_data.reset_index(drop=True)
            return all_data
        
        def concat_allfile_tables(path):
            """ 
            文件夹下多个表格中的数据合并 
            path：文件夹的绝对路径
            """
            import os
            import pandas as pd
            #path = r'C:\Users\86043\Desktop\多表合并'
            os.chdir(path)
            all_data = pd.DataFrame()
            for root,dirs,files in os.walk(path):
                
                for f in files:
                    if '.xlsx' in f:
                        print(f)
                        sheet_df = concat_child(f)
                        all_data = pd.concat([all_data, sheet_df])
                        # 索引重排序
                        all_data = all_data.reset_index(drop=True)
                        return all_data
                    
                    def write_data(filename, data):
                        data.to_excel(filename)
                        
                        # 一个表格中多个子表数据合并 
                        filename = r'C:\Users\86043\Desktop\多子表合并.xlsx'
                        all_data = concat_child(filename)
                        
                        # 指定一个表格中某些子表数据合并
                        filename = r'C:\Users\86043\Desktop\多子表合并.xlsx'
                        all_data = concat_amdchild(filename, ['Sheet1', 'Sheet2'])
                        
                        # 文件夹下多个表格中的数据合并 
                        path = r'C:\Users\86043\Desktop\多表合并'
all_data = concat_allfile_tables(path)
```

代码里共有 3 个函数，用法分别如下：

1. 调用 concat_child 并传入文件路径，快速合并工作簿下的所有工作表；
2. 调用 concat_amdchild 并传入文件路径+需要合并的表名，合并工作簿下的指定表；
3. 调用 concat_allfile_tables 并传入文件夹路径，合并指定文件夹下的所有工作簿；

是不是非常简单呢？当然 Python 除了做成黑乎乎的窗口外，还可以做成 GUI 的可视化窗口，通过可视化窗口来选择文件、文件夹进行合并，先占个位，哪天来补上去。

