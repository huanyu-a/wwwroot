---
title: 在 Windows 系统上批量终止软件进程
createTime: 2025/07/23 16:52:00
permalink: /littletrick/wlajp1il/
---
要在 Windows 系统上批量终止软件进程，可以使用批处理脚本（Batch Script）结合 `taskkill` 命令来实现。

单条cmd指令，例如：<font style="color:rgb(33, 37, 41);">要在命令提示符（CMD）中批量终止所有 Chrome 进程，可以使用 </font>`taskkill`<font style="color:rgb(33, 37, 41);"> 命令。</font>

```plain
taskkill /F /IM chrome.exe /T
```

以下是编写批处理脚本的步骤：

1. **打开记事本**：
    - 打开系统上的记事本应用。
2. **编写批处理脚本**：

```plain
@echo off
taskkill /F /IM 进程名1.exe
taskkill /F /IM 进程名2.exe
taskkill /F /IM 进程名3.exe
echo 进程已终止。
pause
```

说明：

    - 输入以下内容以创建一个批处理脚本。确保替换掉`进程名1.exe`、`进程名2.exe`等为你需要终止的实际进程名称。
    - `/F` 参数用于强制结束进程。
    - `/IM` 参数后跟的是进程的名称（不包括路径）。
3. **保存文件**：
    - 将文件保存为 `.bat` 扩展名，比如 `terminate_processes.bat`。
4. **运行批处理脚本**：
    - 双击该 `.bat` 文件运行它。可以用管理员权限运行以确保结束所有需要的进程。

注意事项：

+ 运行此脚本会强制终止进程，请确保进程终止不会导致数据丢失。
+ 作为进一步的管理工具，你可以将此脚本作为计划任务在系统启动或特定时间运行。
+ 如果不确定进程名称或是否可以安全地终止它，可以使用任务管理器或命令行工具 `tasklist` 命令检查正在运行的进程。



单条cmd指令

