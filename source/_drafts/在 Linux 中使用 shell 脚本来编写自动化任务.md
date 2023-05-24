---
abbrlink: ''
categories: []
date: '2023-05-24T17:56:56.697089+08:00'
tags:
- shell
- Linux
title: 在 Linux 中使用 shell 脚本来编写自动化任务
updated: 2023-5-24T18:7:10.196+8:0
---
## 1.使用标准输出（stdout）捕获控制台输出

在 shell 脚本中，你可以使用类似的方法将命令的标准输出捕获到变量中。例如，如果你想要将 `ls` 命令的输出保存到名为 `output` 的变量中，可以使用以下命令：

```
output=$(ls)
```

要输出多个变量的值，可以将它们一起传递给 `echo` 命令，并使用空格或其他分隔符将它们分开。例如，以下代码输出了变量 `name` 和 `age` 的值：

```
echo $name is nameis$age years old.
```

## 报错信息

**XXXXXXX.sh:行8: $'\r'：未找到命令**

### 解决方法

这个错误通常是由于脚本文件的格式问题引起的，可能是在 Windows 系统上编辑的脚本在 Linux 上执行时出现的问题。

在 Windows 系统上，文本文件通常使用回车符（`\r`）和换行符（`\n`）来表示行的结束，而在 Linux 系统上，只使用换行符（`\n`）来表示行的结束。因此，在将 Windows 上的脚本文件复制到 Linux 上时，可能会出现回车符被错误解释的问题，导致出现类似 `$'\r'：未找到命令` 的错误。

要解决这个问题，你可以使用一些文本编辑器（例如 Notepad++、Sublime Text 等）来将脚本文件转换为 Linux 上的格式。在 Notepad++ 中，你可以选择 "Edit -> EOL Conversion -> Unix (LF)" 来将脚本文件转换为 Linux 上的格式。

![](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305241805739.png)

也可以在 Linux 系统上使用下面的命令来将脚本文件转换为 Linux 上的格式：

```
sed -i 's/\r//' XXXXXXX.sh
```
