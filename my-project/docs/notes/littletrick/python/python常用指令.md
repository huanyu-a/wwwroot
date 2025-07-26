---
title: python常用指令
createTime: 2025/07/24 16:11:19
permalink: /littletrick/qe87hvfe/
---
1. **创建新环境**：如果你的 Anaconda 或 Miniconda 中没有你想要的 Python 版本，你可以创建一个新的虚拟环境，并在其中安装特定版本的 Python。假设你想要降级到 Python 3.10，你可以使用以下命令创建一个名为 **py310** 的环境：

```
conda create -n py310 python=3.10
conda create -n py309 python=3.09
```

2. **激活环境**：创建环境后，激活这个新环境：

```
conda activate py310
conda activate python
conda activate pythonjb
conda activate py309
```

3. **验证版本**：验证 Python 版本是否正确：

```
python --version
```

这样就完成了 Python 版本的降级。你可以在新的环境中继续进行工作，使用 Python 3.10 运行你的程序。

pip3 install db