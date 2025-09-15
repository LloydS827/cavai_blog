# CavAI Blog

基于 Hugo + PaperMod 的个人博客，部署于 GitHub Pages，域名 `cavai.cn`。

## 访问

- 线上地址：https://cavai.cn/

## 环境

- 安装 Hugo Extended（建议使用官方二进制或包管理器）。
- 主题位于 `themes/PaperMod`。

## 内容组织（Page Bundle 推荐）

```
content/posts/
└── my-post/
    ├── index.md      # 文章
    └── assets/       # 配图/附件（可选）
```

## 写作与发布（核心）

1) 新建文章

```bash
hugo new posts/文章标题/index.md
```

2) Front Matter 模板（最小可用）

```yaml
---
title: "文章标题"
date: {{ .Date }}
description: ""
tags: []
categories: []
draft: true
ShowToc: true
ShowReadingTime: true
---
```

3) 本地预览（包含草稿）

```bash
hugo server -D
```

4) 插图与资源

- 将图片放在文章目录（同级 `index.md`）或其 `assets/` 下，文章内直接相对引用：
  - Markdown：`![说明](image.png)`
  - Figure 短代码：`{{< figure src="image.png" caption="说明" >}}`

5) 发布文章（GitHub Pages）

- 将 `draft: false`，提交并推送到发布分支即可触发页面更新。
- 个人习惯（二选一）：
  - 方案A：在 `draft` 分支写作 → 合并到 `master` 发布：

```bash
# 写作
git checkout draft
git add . && git commit -m "post: 文章标题"
git push

# 发布
git checkout master
git merge draft
git push
```

  - 方案B：直接在 `master` 写作并推送（更快，但无预览分支）。

## 常用命令速查

```bash
# 新建文章
hugo new posts/标题/index.md

# 预览（含草稿）
hugo server -D

# 生产构建
hugo --minify
```

## 备注

- 站点配置：`hugo.yml`（包含 PaperMod 主题参数）。
- 如需更换主题或全局样式，优先在 `layouts/` 与 `assets/` 中扩展/覆盖。