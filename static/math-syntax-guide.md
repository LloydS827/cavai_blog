# 数学公式写作规范（Hugo + MathJax v3）

适用范围：本博客（主题 PaperMod），`layouts/partials/extend_head.html` 已启用 MathJax v3（tex-svg-full + ams）。本文给出可稳定渲染的 LaTeX 数学写法与惯例，避免“Misplaced &”“矩阵渲染成一行”等问题。

## 分隔符与基本规则

- 行内公式：`$ ... $` 或 `\(...\)`。示例：`$a^2+b^2=c^2$`
- 块级公式：`$$ ... $$` 或 `\[ ... \]`，前后各保留一空行。示例：

```tex
$$
E=mc^2
$$
```

- 避免将大型结构（矩阵、对齐环境等）放在行内，用块级公式代替。
- 在中文与 `$...$` 相邻时，建议在两侧留一个空格，减少 Markdown 误判为强调的概率。

## 常用结构写法

### 分式、根号、上下标

```tex
$$
\frac{a+b}{c},\quad \sqrt{1-x^2},\quad x_i^2,\quad e^{i\pi}+1=0
$$
```

### 向量与粗体

```tex
$$
\vec{x},\; \mathbf{A},\; \boldsymbol{\theta}
$$
```

### 文本与中文

数学环境内的文本请用 `\text{...}`：

```tex
$$
f(x)=\begin{cases}
1, & \text{当 } x>0 \\
0, & \text{否则}
\end{cases}
$$
```

### 矩阵（推荐 bmatrix/pmatrix）

- 列用 `&` 分隔；行用换行符。
- 为避免在 Markdown 处理链中被吞掉，本站建议在 Markdown 源文件里使用“四个反斜杠”来表示数学里的换行，即写作 `\\\\`，最终到 MathJax 会成为 `\\`（一个数学换行）。

```tex
$$
\begin{bmatrix}
a & b \\\\
c & d
\end{bmatrix}
\quad
\begin{pmatrix}
a & b & c \\\\
d & e & f
\end{pmatrix}
$$
```

> 说明：若你确认所在段落不会吞掉反斜杠，也可以直接用 `\\`。但在列表/引用等复杂 Markdown 场景，`\\\\` 更稳健。

### 线性代数常见表示

```tex
$$
\mathbf{A}\,\vec{x}=\vec{b},\quad
\det(\mathbf{A}),\quad
\mathbf{A}^{-1},\quad
\operatorname{rank}(\mathbf{A})
$$
```

### 对齐（多行等号对齐）

`ams` 包已启用，可使用 `aligned` 或 `align`。推荐在块级中用 `aligned`：

```tex
$$
\begin{aligned}
ax+by&=c \\\\
dx+ey&=f
\end{aligned}
$$
```

## 兼容与替代建议

- 不要使用老式的 `\matrix{...}`，改用 `bmatrix/pmatrix/array`。
- 正文里的“与”请不要写作 `&`，这会被数学环境当成列分隔符。写中文“与”，或在数学环境中写 `\text{与}`。
- 若需要数组排版而非数学矩阵，使用 Markdown 表格，不要在行内用 `&` 对齐。

## 常见问题与排错

- 公式原样显示（未渲染）：
  - 检查分隔符是否成对；块级前后是否留空行；是否被包在代码块/内联代码中。
- Misplaced &：
  - 你在数学环境外使用了 `&`；或矩阵中缺少成对的 `&`/换行，检查每一行列数是否一致。
- 矩阵被渲染成一行：
  - 未使用块级分隔符；`ams` 包未启用（本站已启用）；换行被 Markdown 吞掉。请将行末写成 `\\\\`，并确保使用 `$$...$$` 或 `\[...\]`。
- 行内公式影响段落排版：
  - 大型公式放到块级；在 `$...$` 两侧留一个空格。

## 页面与全局设置

- 站点全局已打开 `params.math = true`；如需单页关闭/开启，可在文章 Front Matter 中设置：

```toml
math = true  # 或 false
```

## 最佳实践清单

- 使用 `$...$`（行内）与 `$$...$$`（块级）；大型结构只用块级。
- 矩阵与对齐：列用 `&`，行末用 `\\\\`；必要时优先 `bmatrix/pmatrix`。
- 文本说明用 `\text{...}`；正文不要用 `&` 表示“与”。
- 复杂段落前后留空行，减少 Markdown 干扰。
- 预览以站点为准（Typora/VSCode 预览与线上渲染器可能不同）。

---

如遇未覆盖的问题，优先将出错的最小示例附在 Issue/PR 中，便于复现与修正。


