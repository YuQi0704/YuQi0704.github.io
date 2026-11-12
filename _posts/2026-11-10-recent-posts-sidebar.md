---
title: "给博客加上 Recent Posts 侧边栏"
date: 2026-11-10 20:30:00 +0800
categories: [折腾]
---

侧边栏的 **Recent Posts** 不是手写的，也不是前端 JS 请求接口，而是 Jekyll 在构建时自动生成的：读取 `site.posts`，按发布日期倒序，取前 6 篇，渲染成列表。

## 模板

`_includes/sidebar.html` 里核心就这几行：

{% raw %}
```liquid
<ul class="recent-posts">
  {% for post in site.posts limit:6 %}
  <li>
    <a href="{{ post.url | relative_url }}" title="{{ post.title | escape }}">{{ post.title }}</a>
    <time>{{ post.date | date: "%Y-%m-%d" }}</time>
  </li>
  {% endfor %}
</ul>
```
{% endraw %}

Jekyll 的 `site.posts` 默认就是最新在前，所以不需要额外排序。

## 标题过长怎么截断

截图里 `How I Made Mole a S...` 那种效果，不需要 JavaScript，也不需要后端截字符串，CSS 就行：

```css
.recent-posts li {
  display: flex;
  gap: 10px;
  min-width: 0;
}

.recent-posts a {
  flex: 1;
  min-width: 0;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.recent-posts time {
  flex: none;
}
```

关键点是 `min-width: 0`——flex 子项默认不会小于内容宽度，不写这一句标题就不会被压缩，省略号也不会出现。

## 为什么不用 JS

文章总数不多时，构建时一次性算好最省事：页面打开就是纯静态 HTML，没有接口请求、没有闪烁，也不依赖脚本是否加载成功。以后文章很多、需要搜索或分页，再考虑前端方案也不迟。
