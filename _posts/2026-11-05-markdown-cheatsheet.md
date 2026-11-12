---
title: "我常用的 Markdown 写法"
date: 2026-11-05 09:20:00 +0800
categories: [笔记]
---

记一下平时写博客最常用的 Markdown 语法，忘了就翻这篇。

## 标题与强调

```markdown
# 一级标题
## 二级标题

**加粗**、*斜体*、`行内代码`
```

## 列表

```markdown
- 无序列表
- 第二项
  - 嵌套一项

1. 有序列表
2. 第二项
```

## 链接与图片

```markdown
[链接文字](https://example.com)
![图片说明](/assets/img/photo.jpg)
```

## 引用

> 引用一段话。
> 第二行。

## 代码块

用三个反引号包起来，后面写语言名可以高亮：

````markdown
```python
def hello():
    print("hello")
```
````

## 表格

```markdown
| 项目 | 说明 |
| --- | --- |
| Jekyll | 静态站点生成器 |
| GitHub Pages | 免费托管 |
```

暂时就这些，够用了。
