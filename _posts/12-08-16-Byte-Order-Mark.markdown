---
layout: post
title: Byte Order Mark(比特序标记)
excerpt: ”特征符”或”字节顺序标记（byte-order mark，BOM）”用来识别文件中使用的编码和字节顺序（big-endian或little-endian）。
published: true
---

为了识别 Unicode 文件，Microsoft建议所有的 Unicode 文件应该以 ZERO WIDTH NOBREAK SPACE字符开头。这作为一个”特征符”或”字节顺序标记（byte-order mark，BOM）”来识别文件中使用的编码和字节顺序（big-endian或little-endian）。

fwrite($fp,"\xEF\xBB\xBF");//Utf-8
