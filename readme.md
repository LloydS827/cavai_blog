# CavAI Blog

🚀 **基于Hugo + PaperMod主题的现代化个人博客**

[![部署状态](https://img.shields.io/badge/部署-Netlify-success)](https://cavai.cn/)
[![Hugo](https://img.shields.io/badge/Hugo-v0.120+-blue.svg)](https://gohugo.io/)
[![主题](https://img.shields.io/badge/主题-PaperMod-purple.svg)](https://github.com/adityatelange/hugo-PaperMod)

## 🌐 网站地址

**主站**: [cavai.cn](https://cavai.cn/) (master分支)

## 🚀 快速开始

### 1. 克隆项目并设置分支

```bash
# 克隆项目
git clone git@github.com:LloydS827/cavai_blog.git
cd cavai_blog

# 切换到draft分支进行日常写作
git checkout draft

# 设置默认推送到当前分支
git config push.default current
```

### 2. 日常写作流程 (draft分支)

```bash
# 确保在draft分支
git checkout draft

# 创建新文章 (推荐使用Page Bundle方式)
hugo new posts/文章标题/index.md
# 或者简单方式
hugo new posts/文章标题.md

# 本地预览
hugo server
```

### 3. 编辑文章

**Front Matter 模板**:
```yaml
---
date = '{{ .Date }}'
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
description = ""
author = "Lloyd Sun"
ShowToc = true
ShowReadingTime = true
ShowPostNavLinks = true

TocOpen = false
searchHidden = false
ShowShareButtons = false
ShowBreadCrumbs = false
draft = false
---
```

### 4. 提交到draft分支

```bash
# 提交到draft分支
git add .
git commit -m "新增文章：文章标题"
git push  # 自动推送到draft分支
```

### 5. 发布文章 (同步到master)

当文章准备好发布时，有两种方式同步到master分支：

#### 方法1: 本地操作
```bash
# 切换到master分支
git checkout master

# 合并draft分支的更改
git merge draft

# 推送到master分支触发生产部署
git push origin master

# 切换回draft分支继续写作
git checkout draft
```

#### 方法2: GitHub操作 (推荐)
```bash
# 在GitHub上创建Pull Request: draft → master
# 1. 访问GitHub仓库页面
# 2. 点击"Compare & pull request"
# 3. 选择 base: master ← compare: draft
# 4. 审查更改后合并PR
```

**⚡ 发布后约2-5分钟自动部署到 [cavai.cn](https://cavai.cn/)**

## 🔄 工作流程优势

- **安全性**: 所有新内容先在draft分支测试
- **预览**: 可以在分支部署环境预览效果 (如果启用)
- **版本控制**: 清晰的发布历史
- **回滚**: 出问题时可以快速回滚master分支
- **协作**: 支持通过PR进行代码审查

## 📁 推荐的文章组织方式 (Page Bundle)

```
content/posts/
└── my-article/           # 文章目录
    ├── index.md         # 文章内容
    └── assets/          # 图片&其他资源
        └── diagram.svg
        └── image1.png
```

## ⚡ 技术栈

- **静态网站生成器**: [Hugo](https://gohugo.io/) (v0.120+)
- **主题**: [PaperMod](https://github.com/adityatelange/hugo-PaperMod)
- **部署平台**: [Netlify](https://www.netlify.com/)
- **版本控制**: GitHub
- **CI/CD**: Netlify自动构建
- **域名**: cavai.cn (阿里云)

## 🚀 自动部署配置

### Netlify 配置

| 配置项 | 值 |
|--------|-----|
| **代码仓库** | `lloyds827/lloyds827.github.io` |
| **生产分支** | `master` |
| **预览分支** | `draft` (可选) |
| **构建命令** | `hugo` |
| **发布目录** | `public` |
| **Hugo版本** | `0.147.0` |（）


### 部署流程

#### 生产部署 (master分支)
1. **推送代码** → GitHub master分支
2. **Netlify检测** → 自动拉取最新代码
4. **部署上线** → 更新到 [cavai.cn](https://cavai.cn/)

## 🛠️ 本地开发环境

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

### 本地开发命令

```bash
# 启动开发服务器 (包含草稿)
hugo server -D

# 自定义端口
hugo server -D --port 8080

# 绑定所有地址 (用于局域网访问)
hugo server -D --bind 0.0.0.0

# 构建生产版本
hugo --minify
```

## ✨ 功能特性

- ✅ **响应式设计** - 完美适配桌面端和移动端
- ✅ **暗黑模式** - 自动切换主题
- ✅ **全文搜索** - 基于JSON索引的快速搜索
- ✅ **代码高亮** - 支持多种编程语言
- ✅ **数学公式** - LaTeX数学公式渲染
- ✅ **SEO优化** - 完整的元数据和结构化数据
- ✅ **RSS订阅** - 自动生成RSS feed
- ✅ **阅读时间** - 智能估算文章阅读时间
- ✅ **目录导航** - 自动生成文章目录
- ✅ **CDN加速** - Netlify全球CDN网络
- ✅ **自定义域名** - 绑定个人域名cavai.cn

## 📖 项目概述

CavAI Blog 是一个专注于AI教育和技术分享的个人博客平台。采用现代化的静态网站生成技术，提供快速、安全、优雅的阅读体验。

## 📁 项目结构

```
cavai_blog/
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
baseURL: "https://cavai.cn/"
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

## ✍️ 写作指南

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

### 自定义组件

```markdown
# 带说明的图片
{{< figure src="image1.png" caption="图片说明" >}}
```

## 🚨 故障排除

### 常见问题

#### 1. Netlify部署失败

**解决方案**:
- 确认构建命令为：`hugo --minify`
- 确认发布目录为：`public`
- 确认Hugo版本设置正确
- 检查Netlify构建日志中的错误信息
- 确认baseURL配置正确: `https://cavai.cn/`

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
- **CDN缓存** - Netlify全球节点缓存
- **Gzip压缩** - 自动压缩传输内容
- **自定义域名** - 专业的品牌形象

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
- **博客**: [https://cavai.cn/](https://cavai.cn/)

---

<div align="center">

**⭐ 如果这个项目对你有帮助，请给个Star支持一下！ ⭐**

Made with ❤️ by [Lloyd Sun](https://github.com/lloyds827)

</div>