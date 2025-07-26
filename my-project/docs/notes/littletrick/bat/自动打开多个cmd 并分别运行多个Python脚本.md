---
title: 自动打开多个cmd 并分别运行多个Python脚本
createTime: 2025/07/23 16:51:40
permalink: /littletrick/qep2w2j2/
---
### <font style="color:rgb(33, 37, 41);">如果需要在运行时保持窗口打开：</font>
`cmd /k`<font style="color:rgb(33, 37, 41);"> 将在脚本运行完后保持窗口打开，这样你可以查看输出。如果不需要保持窗口打开，可以将 </font>`/k`<font style="color:rgb(33, 37, 41);"> 替换为 </font>`/c`<font style="color:rgb(33, 37, 41);">：</font>

```plain
@echo off
start cmd /k python dropdown_collector.py
start cmd /k python related_collector.py
exit
```

