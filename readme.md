# Lloyd's Blog

基于Hugo + PaperMod主题的个人博客，部署在Zeabur平台。

## �� 写作流程

### 1. 创建新文章 (Page Bundle方式)

使用Hugo命令创建新文章，每篇文章都有独立的文件夹：

```bash
# 基本语法
hugo new posts/文章名称/index.md

# 具体示例
hugo new posts/ai-tutorial/index.md
hugo new posts/docker-guide/index.md
hugo new posts/thoughts-2024/index.md
```

创建后的文章结构：

```
content/posts/
└── ai-tutorial/           # 文章文件夹
    └── index.md          # 文章内容文件
```

### 2. 添加图片和资源

每篇文章都有独立的文件夹，可以直接添加图片和资源：

```bash
content/posts/ai-tutorial/
├── index.md              # 文章内容
├── cover.jpg             # 封面图片
├── diagram.png           # 示意图
└── assets/               # 资源文件夹
    ├── screenshot1.png
    └── code-example.txt
```

在文章中引用图片：
```markdown
# 同目录下的图片
![封面图片](cover.jpg)

# assets文件夹中的图片  
![截图](assets/screenshot1.png)

# 带图片说明
{{< figure src="diagram.png" caption="系统架构图" >}}
```

### 3. 编辑文章

新创建的文章会自动使用 `archetypes/default.md` 模板，包含以下结构：

```toml
+++
date = '2025-05-24T22:30:00+08:00'  # 自动生成当前时间
draft = true                        # 默认为草稿状态
title = 
```

### 4. 发布文章

编辑完成后，将 `draft = true` 改为 `draft = false`，然后推送到GitHub：

```bash
git add .
git commit -m "新增文章: 你的文章标题"
git push origin master
```

Zeabur会自动检测并重新部署你的博客。

## 🎨 文章模板自定义

### 模板文件位置

文章模板位于 `archetypes/default.md`，你可以根据需要自定义这个模板。

### Front Matter 参数详解

#### 必需参数
- **`title`**: 文章标题
- **`date`**: 发布日期（自动生成）
- **`draft`**: 草稿状态（true=草稿，false=发布）

#### 可选参数
- **`description`**: 文章描述（用于SEO和摘要）
- **`tags`**: 文章标签（数组格式）
- **`categories`**: 文章分类（数组格式）
- **`author`**: 作者名称
- **`cover`**: 封面图片路径
- **`weight`**: 文章权重（用于排序）

#### PaperMod主题专用参数
- **`ShowToc`**: 是否显示目录（true/false）
- **`TocOpen`**: 目录是否默认展开（true/false）
- **`searchHidden`**: 是否在搜索中隐藏（true/false）
- **`ShowReadingTime`**: 显示阅读时间（true/false）
- **`ShowShareButtons`**: 显示分享按钮（true/false）
- **`ShowPostNavLinks`**: 显示上下篇导航（true/false）
- **`ShowBreadCrumbs`**: 显示面包屑导航（true/false）
- **`editPost`**: 编辑文章链接配置

### 自定义模板示例

你可以修改 `archetypes/default.md` 来自定义模板：

```markdown
+++
date = '{{ .Date }}'
draft = true
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
description = "请填写文章描述..."
tags = []
categories = []
author = "Lloyd"
cover = ""
ShowToc = true
TocOpen = false
searchHidden = false
ShowReadingTime = true
ShowShareButtons = false
ShowPostNavLinks = true
+++

## 概述

简要介绍这篇文章的主要内容...

## 详细内容

### 核心要点

- 要点1
- 要点2
- 要点3

### 代码示例

```语言
// 代码示例
```

## 结论

总结文章的主要观点...

---

> 💡 **提示**: 记得将 `draft` 改为 `false` 来发布文章！
```

### 创建特定类型模板

你还可以为不同类型的文章创建专门的模板：

```bash
# 创建技术文章模板
# 在 archetypes/ 目录下创建 tech.md

# 使用特定模板创建文章
hugo new --kind tech posts/my-tech-post.md
```

## 📁 内容组织结构

```
content/
├── posts/              # 博客文章
│   ├── my-first-post.md
│   └── hugo-tutorial.md
├── about/              # 关于页面
│   └── index.md
└── search/             # 搜索页面
    └── index.md
```

## 📷 图片和资源管理

### 添加图片

1. **方法一：使用static目录**
   ```
   static/images/my-image.jpg
   ```
   在文章中引用：
   ```markdown
   ![图片描述](/images/my-image.jpg)
   ```

2. **方法二：页面捆绑包（推荐）**
   ```
   content/posts/my-post/
   ├── index.md
   ├── featured.jpg
   └── diagram.png
   ```
   在文章中引用：
   ```markdown
   ![图片描述](featured.jpg)
   ```

### 文件下载

将可下载文件放在 `static/files/` 目录：
```markdown
[下载PDF](/files/document.pdf)
```

## 🔍 高级写作技巧

### 数学公式

支持LaTeX数学公式：
```markdown
行内公式：$E = mc^2$

块级公式：
$$
\sum_{i=1}^{n} x_i = x_1 + x_2 + \cdots + x_n
$$
```

### 代码高亮

支持多种编程语言语法高亮：

````markdown
```python
def hello_world():
    print("Hello, World!")
```

```bash
# Shell命令
hugo server -D
```
````

### 提示框和引用

```markdown
> 💡 **提示**: 这是一个提示框

> ⚠️ **警告**: 这是一个警告框

> ✅ **成功**: 这是一个成功提示
```

---

## 🚀 技术配置

### 本地开发

```bash
# 克隆仓库
git clone https://github.com/LloydS827/cavai_blog.git
cd cavai_blog

# 安装Hugo (选择你的系统)
# macOS: brew install hugo
# Windows: choco install hugo-extended  
# Linux: sudo snap install hugo

# 启动本地服务器
hugo server -D
# 访问 http://localhost:1313
```

### Zeabur部署

**自动部署**：推送到GitHub后Zeabur自动构建部署
- 访问 [Zeabur](https://zeabur.com)
- 连接GitHub仓库：`LloydS827/cavai_blog`
- 自动检测Hugo项目并部署

### 项目结构

```
cavai_blog/
├── content/          # 文章内容
├── static/           # 静态资源  
├── themes/           # Hugo主题
├── archetypes/       # 文章模板
├── layouts/          # 自定义布局
├── assets/           # 资源文件
└── hugo.yml          # Hugo配置
```

### 主要配置文件

- **`hugo.yml`**: Hugo网站配置
- **`archetypes/default.md`**: 默认文章模板

---

## 📞 联系方式

- **GitHub**: [@LloydS827](https://github.com/lloyds827)
- **Email**: sunguangji827@hotmail.com
- **Blog**: [访问博客](https://your-project.zeabur.app)

## 📄 许可证

MIT License

---

> **📝 快速开始**: 运行 `hugo new posts/my-first-post.md` 创建你的第一篇文章！