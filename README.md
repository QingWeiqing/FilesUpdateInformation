# FilesUpdateInformation ReadmeFile

​	文件更新信息生成器。Readme文件。

## 基本功能概述

​	当多个制作者共同在一个存储空间上工作时，可以使用该工具快速生成“文件列表”和“文件更新日志”。“文件更新日志”可以记录操作者在特定文件夹内做出的修改（仅包含修改时间，不包含具体修改内容）、移动、删除、新建等指令。

​	该工具不是实时记录日志的，而是在每次运行时将现有文件与已有的最新“文件列表”进行对比，在日志中以附加形式写入简要的文件变动，最后再次生成一个新的文件列表（.csv格式）。

## 使用说明

1. 使用任意编辑器打开源代码。

2. 修改其中的基本属性信息。
3. 编译并运行。

## 源代码说明

### 文件树的用词

​	在最初的构想中，程序将以模拟文件树的形式存储并对比所有文件信息，但因实现难度较大而放弃。因此在源代码及其注释中，部分语句错误地使用了“文件树”(File_Tree)来说明和定义“文件列表”。

### 类型判断结论

​	在源代码中预留了多个文件类型判断结论。不过当前代码中仅使用了"删除""新建""更新""移动"。

```
# 0 不变
# 1 删除
# 2 新建
# 3 更新
# 4 移动
# 5 移动且更新
# 6 回朔
# 7 移动且回朔
# -1 留空
```

​	这是因为不同设备和文件同步工具对"创建时间"和"修改时间"的标注较为混乱。其混乱主要体现在：

1. 不同设备系统中新纪元时间、时间存储方式的不同。
2. 同步工具、传输工具在修改文件时可能会对"创建时间"作出更改。
3. 若按照"修改时间"或"创建时间"确定不同文件名称的文件是否相同，则在同一时刻传输文件可能会导致程序误判。

## 仍未解决的BUG

​	当日志文件路径中没有.csv文件时，程序将会报错。

​	当存在同名的文件被删除时，日志中不会作出记录。
