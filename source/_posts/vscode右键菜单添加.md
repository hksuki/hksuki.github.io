---
title: vscode右键菜单添加
date: 2018-10-18 11:08:47
category: 实用技术
tags: 
- 实用技术
- 杂七杂八
---

重装vscode之后，发现没有在此处打开文件夹的功能。查了下资料，发现可以这样解决。

```r
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\Background\shell\VSCode]
@="Open VSCode Here"
"Icon"="vscode path"

[HKEY_CLASSES_ROOT\Directory\Background\shell\VSCode\command]
@="vscode path ."

[HKEY_CLASSES_ROOT\Directory\shell\VSCode]
@="Open VSCode Here"
"Icon"="vscode path"

[HKEY_CLASSES_ROOT\Directory\shell\VSCode\command]
@="vscode path %1"
```

将上述文件保存，配置好vscode的路径信息，然后将其保存为`reg`文件。