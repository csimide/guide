---
tags: [heading, numbering]
---
# 如何为每一级标题指定不同的编号格式？

类似问题：如何从二级标题开始编号？

为了方便起见，推荐使用 `numbly` 包。`numbly` 包的用法是，`numbly(1级编号格式, 2级编号格式, 3级编号格式, ...)`。按顺序写出每一级编号的格式，然后把其中的编号换成 `{层级:格式}` 即可，省略格式默认使用阿拉伯数字。不需要编号的层级使用 `none`。

例如，我想实现

```
第1章 背景
1.1 引言
(a) 问题
(b) 目标
1.2 方法
...
```

让我们分析一下，1 级标题使用了 1 级编号，2 级标题使用了 1 级编号和 2 级编号，3 级标题只使用了 3 级编号并使用小写字母格式（`a`）。于是对应的设置如下：

```typst
#import "@preview/numbly:0.1.0": numbly
#set heading(numbering: numbly(
  "第{1}章",
  "{1}.{2}",
  "({3:a})",
))

= 背景
== 引言
=== 问题
=== 目标
== 方法

```
