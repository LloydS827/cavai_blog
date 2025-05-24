# CavAI Blog

🚀 **基于Hugo + PaperMod主题的现代化个人博客，部署在Tencent EdgeOne Pages**

[![部署状态](https://img.shields.io/badge/部署-EdgeOne%20Pages-success)](https://cavaiblog.edgeone.app/)
[![Hugo](https://img.shields.io/badge/Hugo-v0.120+-blue.svg)](https://gohugo.io/)
[![主题](https://img.shields.io/badge/主题-PaperMod-purple.svg)](https://github.com/adityatelange/hugo-PaperMod)

## 📖 项目概述

CavAI Blog 是一个专注于AI教育和技术分享的个人博客平台。采用现代化的静态网站生成技术，提供快速、安全、优雅的阅读体验。

**🌐 在线访问**: [https://cavaiblog.edgeone.app/](https://cavaiblog.edgeone.app/)

## ⚡ 技术栈

- **静态网站生成器**: [Hugo](https://gohugo.io/) (v0.120+)
- **主题**: [PaperMod](https://github.com/adityatelange/hugo-PaperMod)
- **部署平台**: [Tencent EdgeOne Pages](https://edgeone.ai/)
- **版本控制**: GitHub
- **CI/CD**: GitHub Actions (构建验证)
- **域名**: EdgeOne提供的自定义域名

## 🚀 部署配置

### EdgeOne Pages 配置

本项目使用 Tencent EdgeOne Pages 自动部署，配置如下：

| 配置项 | 值 |
|--------|-----|
| **代码仓库** | `lloyds827/lloyds827.github.io` |
| **分支** | `master` |
| **框架** | `Hugo` / `Other` |
| **构建命令** | `hugo --minify` |
| **输出目录** | `public` |
| **安装命令** | *(留空)* |
| **Node.js版本** | `18+` |

### 环境变量 (可选)
```
HUGO_VERSION=0.120.0
HUGO_ENV=production
```

### 自动部署流程

1. **推送代码** → GitHub master分支
2. **EdgeOne检测** → 自动拉取最新代码
3. **Hugo构建** → 执行 `hugo --minify`
4. **部署上线** → 更新到CDN节点
5. **访问网站** → 通过EdgeOne域名访问

## ✍️ 写作指南

### 快速开始

```bash
# 1. 克隆项目
git clone https://github.com/lloyds827/lloyds827.github.io.git
cd lloyds827.github.io

# 2. 创建新文章
hugo new posts/my-article/index.md

# 3. 编辑文章
# 将 draft: true 改为 draft: false

# 4. 本地预览
hugo server -D

# 5. 发布文章
git add .
git commit -m "新增文章：文章标题"
git push origin master
```

### 文章结构 (Page Bundle)

推荐使用Page Bundle方式组织文章，每篇文章都有独立的文件夹：

```
content/posts/
└── my-article/           # 文章目录
    ├── index.md         # 文章内容
    ├── cover.jpg        # 封面图片
    ├── image1.png       # 文章图片
    └── assets/          # 其他资源
        └── diagram.svg
```

### Front Matter 模板

```yaml
---
title: "文章标题"
date: 2025-05-24T23:30:00+08:00
draft: false
description: "文章简介，用于SEO和摘要"
tags: ["AI", "教育", "技术"]
categories: ["技术分享"]
author: "Lloyd Sun"
cover: "cover.jpg"
ShowToc: true
TocOpen: false
searchHidden: false
ShowReadingTime: true
ShowShareButtons: false
ShowPostNavLinks: true
ShowBreadCrumbs: false
---

## 文章内容

在这里编写文章内容...
```

### 图片使用

```markdown
# 同目录图片
![封面](cover.jpg)

# 带说明的图片
{{< figure src="image1.png" caption="图片说明" >}}

# 资源文件夹中的图片
![图表](assets/diagram.svg)
```

### 代码高亮

````markdown
```python
def hello_world():
    print("Hello, World!")
```

```bash
hugo server --port 1313 --bind 0.0.0.0
```
````

### 数学公式

```markdown
# 行内公式
这是一个公式：$E = mc^2$

# 块级公式
$$
\sum_{i=1}^{n} x_i = \frac{1}{n}\sum_{i=1}^{n} y_i
$$
```

## 🛠️ 本地开发

### 环境要求

- **Hugo**: v0.120.0 或更高版本 (Extended版本)
- **Git**: 用于版本控制
- **操作系统**: Windows / macOS / Linux

### 安装Hugo

```bash
# macOS (使用Homebrew)
brew install hugo

# Windows (使用Chocolatey)
choco install hugo-extended

# Windows (使用Scoop)
scoop install hugo-extended

# Linux (使用Snap)
sudo snap install hugo
```

### 本地运行

```bash
# 启动开发服务器
hugo server -D

# 自定义端口
hugo server -D --port 8080

# 绑定所有地址 (用于局域网访问)
hugo server -D --bind 0.0.0.0
```

### 构建生产版本

```bash
# 构建静态文件到public目录
hugo --minify

# 构建并清理输出目录
hugo --minify --cleanDestinationDir
```

## 📁 项目结构

```
lloyds827.github.io/
├── archetypes/          # 文章模板
│   └── default.md      
├── assets/              # 资源文件 (SCSS, JS等)
├── content/             # 网站内容
│   ├── posts/          # 博客文章
│   ├── about/          # 关于页面
│   └── search/         # 搜索页面
├── layouts/             # 自定义布局模板
├── static/              # 静态资源 (图片, CSS, JS等)
│   └── logo.png        
├── themes/              # Hugo主题
│   └── PaperMod/       # PaperMod主题 (Git子模块)
├── .github/             # GitHub相关配置
├── .gitignore           # Git忽略文件
├── hugo.yml             # Hugo网站配置
└── README.md            # 项目说明
```

## ⚙️ 配置文件

### hugo.yml 核心配置

```yaml
baseURL: "https://cavaiblog.edgeone.app/"
title: "CavAI"
theme: "PaperMod"
hasCJKLanguage: true
relativeURLs: true
canonifyURLs: false

params:
  env: production
  author: "Lloyd Sun"
  defaultTheme: auto
  ShowReadingTime: true
  ShowCodeCopyButtons: true
  ShowWordCount: true
  UseHugoToc: true
```

## 🔍 功能特性

- ✅ **响应式设计** - 完美适配桌面端和移动端
- ✅ **暗黑模式** - 自动切换主题
- ✅ **全文搜索** - 基于JSON索引的快速搜索
- ✅ **代码高亮** - 支持多种编程语言
- ✅ **数学公式** - LaTeX数学公式渲染
- ✅ **SEO优化** - 完整的元数据和结构化数据
- ✅ **RSS订阅** - 自动生成RSS feed
- ✅ **阅读时间** - 智能估算文章阅读时间
- ✅ **目录导航** - 自动生成文章目录
- ✅ **面包屑** - 清晰的导航路径
- ✅ **社交分享** - 支持多平台分享
- ✅ **CDN加速** - EdgeOne全球CDN网络

## 🚨 故障排除

### 常见问题

#### 1. EdgeOne部署404错误

**解决方案**:
- 确认构建命令为：`hugo --minify`
- 确认输出目录为：`public`
- 确认baseURL配置正确
- 等待5-10分钟让CDN缓存刷新

#### 2. 主题未加载

```bash
# 初始化并更新子模块
git submodule init
git submodule update --recursive
```

#### 3. 本地构建失败

```bash
# 检查Hugo版本
hugo version

# 清理并重新构建
rm -rf public/
hugo --minify
```

### 调试方法

```bash
# 详细构建日志
hugo --verbose --log

# 检查配置
hugo config

# 验证内容
hugo list all
```

## 🎯 性能优化

- **静态生成** - 所有页面预先生成，加载速度极快
- **图片优化** - 自动压缩和格式转换
- **代码分割** - CSS和JS按需加载
- **CDN缓存** - EdgeOne全球节点缓存
- **Gzip压缩** - 自动压缩传输内容
- **懒加载** - 图片和内容懒加载

## 🔐 安全特性

- **HTTPS** - 全站HTTPS加密
- **CSP** - 内容安全策略
- **静态部署** - 无服务器安全风险
- **CDN防护** - EdgeOne DDoS防护

## 📊 分析与监控

- **性能监控** - EdgeOne内置分析
- **访问统计** - 实时访问数据
- **错误追踪** - 自动错误监控
- **SEO报告** - 搜索引擎优化报告

## 🤝 贡献指南

欢迎提交Issue和Pull Request：

1. Fork项目
2. 创建功能分支：`git checkout -b feature/amazing-feature`
3. 提交更改：`git commit -m 'Add amazing feature'`
4. 推送分支：`git push origin feature/amazing-feature`
5. 提交Pull Request

## 📄 许可证

本项目基于 MIT 许可证开源 - 查看 [LICENSE](LICENSE) 文件了解详情

## 📞 联系方式

- **作者**: Lloyd Sun
- **邮箱**: sunguangji827@hotmail.com
- **GitHub**: [@lloyds827](https://github.com/lloyds827)
- **博客**: [https://cavaiblog.edgeone.app/](https://cavaiblog.edgeone.app/)

---

<div align="center">

**⭐ 如果这个项目对你有帮助，请给个Star支持一下！ ⭐**

Made with ❤️ by [Lloyd Sun](https://github.com/lloyds827)

</div>