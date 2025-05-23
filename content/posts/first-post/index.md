---
title: "My Test Article"
date: "2024-03-30"
---
## TEST-Blog

![image-20250523201408210](./image-20250523201408210.png)

This is for rendering-test only. 

## 文本格式示例

这是**粗体文本**，这是*斜体文本*，这是~~删除线文本~~，这是`行内代码`。

> 这是一段引用内容，可以用来突出重要的信息或引用他人的观点。
> 
> 引用可以包含多个段落。

### 列表示例

无序列表：

- 第一项
- 第二项
  - 嵌套项
  - 另一个嵌套项
- 第三项

有序列表：

1. 第一步
2. 第二步
3. 第三步

任务列表：

- [x] 已完成任务
- [ ] 待完成任务
- [ ] 另一个待完成任务

## 代码示例

### 行内代码

在 Python 中，我们可以使用 `print("Hello, World!")` 输出一段文本。

### 代码块

下面是一段 Python 代码示例：

```python
def fibonacci(n):
    """返回斐波那契数列的前n个数"""
    fib_sequence = [0, 1]
    if n <= 2:
        return fib_sequence[:n]
    
    for i in range(2, n):
        next_number = fib_sequence[i-1] + fib_sequence[i-2]
        fib_sequence.append(next_number)
    
    return fib_sequence

# 测试函数
print(fibonacci(10))  # 输出: [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

下面是一段 JavaScript 代码示例：



## 数学公式

### 行内公式

质能守恒方程 $E=mc^2$ 是爱因斯坦最著名的公式之一。

### 块级公式

下面是一些数学公式示例：

贝叶斯定理：

$$P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}$$

欧拉公式：

$$e^{i\pi} + 1 = 0$$

高斯分布概率密度函数：

$$f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2}$$

矩阵乘法：

$$
\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}
\begin{pmatrix}
e & f \\
g & h
\end{pmatrix} =
\begin{pmatrix}
ae + bg & af + bh \\
ce + dg & cf + dh
\end{pmatrix}
$$

## 表格示例

| 姓名 | 年龄 | 职业 |
|------|------|------|
| 张三 | 28   | 软件工程师 |
| 李四 | 32   | 数据分析师 |
| 王五 | 45   | 产品经理 |

