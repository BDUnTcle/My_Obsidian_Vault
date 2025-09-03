---
create date: 2024-03-08
modification date: 2024-03-08T13:01:00
tags:
  - Obsidian
  - 计算机工具学习
type: LearningNote
---
# 重要概念
## Metadata
dataview 通过检索一些基本数据来实现对笔记的全局搜索，这些在 dataview 中被称作 metadata，它包括这些：
- tags
- propery 中的其他属性
- 笔记中的 inline fields，`[key \:\: value]
## Query
[DQL详细定义文档](https://blacksmithgu.github.io/obsidian-dataview/queries/structure/)

# Learn by practice
> 创建一个 List, 显示一些笔记
> 1. 【-"附件"】 表示除了"附件"目录
```
LIST 
FROM -"附件" AND -"Excalidraw"
WHERE file.mday = date(this.file.cday) 
```

>在一个 List 中使用Group区分不同来源的笔记

```
LIST rows.file.type
FROM -"附件" AND -"Excalidraw"
WHERE file. Mday = date (this. File. Cday) 
GROUP BY type
```

