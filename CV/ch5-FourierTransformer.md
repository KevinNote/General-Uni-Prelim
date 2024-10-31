---
marp: true
---

Prelim for Imperial College London
COMP60006 Computer Vision
# 5. Fourier Transform / 傅立叶变换

<p>
Kevin Merton
<br>
31 Oct 2024
</p>

---

## Material

- <https://github.com/KevinNote/Imperial-Prelim/CV>

---

## 基本思路

傅立叶变换：将信号转换为由多个正弦、余弦波组成的频域信号

$$
f(x) = a_0 + \sum_{n=1}^{\infty} [a_n \cos(nx) + b_n \sin(nx)]
$$

---

## 为什么我们可以进行 FT？

考虑向量空间中我们使用一组标准正交基（Normal Orthogonal Basis）来表示该空间中的任意向量。

标准正交基为：
- 正交：$\forall i\neq j. \mathbf{x}_i \cdot \mathbf{x}_j = 0$
- 标准：$\mathbf{x}_i \cdot \mathbf{x}_i = 1$
  或者表述为：$\forall i. \|\mathbf{x}_i\| = 1$

例如三维空间中一组标准正交基为：

$$
\begin{cases}
\mathbf{x}_1 = [1, 0, 0] \\
\mathbf{x}_2 = [0, 1, 0] \\
\mathbf{x}_3 = [0, 0, 1]
\end{cases}
$$

