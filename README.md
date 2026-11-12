# YuQi0704.github.io

基于 Jekyll + GitHub Pages 的个人博客，侧边栏带自动生成的 Recent Posts。

## 目录结构

```
.
├── _config.yml            # 站点配置（标题、描述、作者）
├── _layouts/
│   ├── default.html       # 全站布局（顶栏 + 正文 + 侧边栏）
│   └── post.html          # 文章页布局
├── _includes/
│   └── sidebar.html       # Recent Posts 侧边栏
├── _posts/                # 文章：YYYY-MM-DD-标题.md
├── assets/css/style.css   # 样式（含标题省略号）
├── index.html             # 首页文章列表
├── about.md               # 关于页
└── 404.html
```

## 发布到 GitHub Pages

### 方式一：命令行

1. 在 GitHub 新建仓库，名称必须是 **`YuQi0704.github.io`**，选 Public，**不要**勾选初始化 README。
2. 在本目录执行：

```bash
git remote add origin https://github.com/YuQi0704/YuQi0704.github.io.git
git push -u origin main
```

3. 打开仓库 **Settings → Pages**：
   - Source 选 **Deploy from a branch**
   - Branch 选 **main**，目录选 **/(root)**
   - 保存后等 1–2 分钟
4. 访问 <https://yuqi0704.github.io>。

### 方式二：GitHub Desktop

1. 打开 GitHub Desktop → **File → Add local repository**，选择本目录。
2. 点 **Publish repository**，仓库名改成 `YuQi0704.github.io`，取消勾选 “Keep this code private”。
3. 之后的步骤同上（Settings → Pages）。

## 写一篇新文章

在 `_posts/` 下新建 `YYYY-MM-DD-标题.md`：

```yaml
---
title: "文章标题"
date: 2026-11-12 10:00:00 +0800
categories: [随笔]
---

正文……
```

提交并推送后自动构建，侧边栏 Recent Posts 会自动更新（取最新 6 篇）。

## 修改侧边栏

- 显示数量：`_includes/sidebar.html` 里的 `limit:6`。
- 标题截断：`assets/css/style.css` 里的 `.recent-posts a`（`text-overflow: ellipsis`）。
- 站点标题 / 描述：`_config.yml`。

## 本地预览（可选）

需要安装 Ruby 和 Bundler：

```bash
bundle install
bundle exec jekyll serve
```

然后打开 <http://127.0.0.1:4000>。不装也行，推送到 GitHub 后由 Pages 自动构建。
