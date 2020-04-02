# `jupyter-notebook` 入门指南
之前我们安装 `anaconda3` 时，会默认安装 `jupyter-notebook` 基于 web 交互式笔记本，支持多种语言，支持我们在线共享程序文档，编写代码，统计模型，数值模拟，机器学习等

# 打开方式
第一种：使用 `cmd` 控制台窗体，输入以下命令
```
jupyter notebook
```
![](./imgs/chapter-four/jupyter-notebook.png)

第二种：直接点击 `jupyter notebook` 打开

![](./imgs/chapter-four/start.png)


# `jupyter notebook` 主面板

![](./imgs/chapter-four/say.png)

打开 `jupyter notebook` 主面板我们可以看到，左边下拉框展示

1. `Folder` 文件夹目录，你可以创建目录，删除目录等
2. `All Notebooks` 所有的 `notebook` 笔记本 
3. `Running` 正在运行中的 `notebook`
4. `Files` 文件，你可以创建，删除，修改文件等
5. `Clusters` 由 `IPython parallel` 包提供，用于并行计算

我们可以通过主面板右侧 `new` 选择 `python 3`,创建 `notebook`

![](./imgs/chapter-four/new.png)

会生成一个 `notebook` 面板

![](./imgs/chapter-four/python3-test.png)

### 1. file 文件

选项          |    功能                         |  
-----------   |-----------------------------------|
`New Notebook` | 新建一个 `notebook`
`Open ...` | 再新的页面中打开主面板
`Make a copy` | 复制当前 `notebook`
`Rename ...` | `notebook` 重命名
`Save and Checkpoint` | 将当前 `notebook` 状态存为一个 `checkpoint`
`Revert to Checkpoint` | 恢复到此前存过的 `checkpoint`
`print preview` | 打印预览
`download as` | 下载 `notebook` 保存为某种类型文件
`close and halt` | 停止运行并退出该 `notebook`



### 2. edit 编辑

选项 | 功能
----| ---|
`Cut Cells` | 剪切单元
`Copy Cells` | 复制单元
`Paste Cells Above` | 在当前单元上方粘贴上复制内容
`Paste Cells Below` | 在当前单元格下方粘贴复制的内容
`Paste Cells & Replace` | 替换当前的单元为复制的单元
`Delete Cells` | 删除单元
`Undo Delete Cells` | 撤回删除操作
`Split Cell` | 从鼠标位置处拆分当前单元为两个单元
`Merge Cell Above` | 当前单元和上方单元合并
`Merge Cell Below` | 当前单元和下方单元合并
`Move Cell Up` | 当前单元上移一层
`Move Cell Down` | 当前单元下移一层
`Edit Notebook Metadata` | 编辑 `notebook` 的元数据
`Find And Replace` | 查找并替换


### 3. view 查看
选项 | 功能 |
----| ----|
`Toggle Header` | 隐藏/显示 `Jupyter notebook` 的 `logo`和名称
`Toggle Toolbar` | 隐藏/显示 `Jupyter notebook` 的工具条
`Cell Toolbar` | 更改单元展示样式

### 4. insert 插入
选项 | 功能 |
----| -----|
`insert Cell Above` | 在单元格上方插入
`insert Cell Below` | 在单元格下方插入

### 5. cell 单元格
选项 | 功能 |
----| ----|
`Run Cells` | 运行单元内代码
`Run Cells And Select Below` | 运行单元内代码并将光标移动到下一个单元
`Run Cells And Insert Below` | 运行单元内代码并在下方新建一个单元格
`Run All` | 运行所有单元代码
`Run All Above` | 运行该单元（不含）上方所有单元内的代码
`Run All Below` | 运行该单元（含）下方所有单元内的代码
`Cell Type` | 选择单元内容属性
`Current Outputs` | 对当前单元输出的结果进行隐藏/显示/滚动/清除
`All Outputs` | 对所有单元输出的结果进行隐藏/显示/滚动/清除

### 6. kernel 内核
选项 | 功能
---| ---|
`Interrupt` | 中断与内核链接
`Restart` | 重启内核
`Restart & Clear Output` | 重启内核并清空现有输出结果
`Restart & Run All` | 重启内核并重新运行 `notebook` 中所有代码
`Reconnect` | 重新链接到内核
`Change Kernel` | 切花内核


### 7. help 帮助
选项 | 功能
----| ----|
`User Interface Tour` | 用户使用指南，非常棒的功能，带你全面了解 `notebook`
`Keyboard Shortcuts` | 快捷键大全
`Notebook Help` | `notebook` 使用指南
`Markdown` | `Markdown` 使用指南
`Python pandas` | 各类使用指南
`About` | 关于 `Jupyter Notebook` 的一些信息


# 尝试代码

我们可以尝试输入以下代码
```python
import matplotlib.pyplot as plt
import numpy as np
x = np.linspace(0, 5, 10)
y = x ** 2
axes.set_xlabel('x')
axes.set_ylabel('y')
axes.set_title('title');
```

![](./imgs/chapter-four/code.png)

# 共享代码

![](./imgs/chapter-four/download.png)