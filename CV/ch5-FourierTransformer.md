---
marp: true
---

Prelim for Imperial College London
COMP60006 Computer Vision 24/25 Lecture 4
# 5. Fourier Transform / 傅立叶变换

Kevin Merton
31 Oct 2024

---

## Material

- <https://github.com/KevinNote/Imperial-Prelim/CV>

---

## 基本思路

傅立叶变换（FT）：将信号转换为由多个正弦、余弦波组成的频域信号

$$
f(x) = a_0 + \sum_{n=1}^{\infty} [a_n \cos(nx) + b_n \sin(nx)]
$$

---

## 为什么我们可以进行 FT？

考虑向量空间中我们使用一组标准正交基（Normal Orthogonal Basis）来表示该空间中的任意向量。

标准正交基为：
- 正交 Orthogonal：$\forall i\neq j. \mathbf{x}_i \cdot \mathbf{x}_j = 0$  
  i.e., $\mathbf{x}_i \perp \mathbf{x}_j$
- 标准 Normal：$\mathbf{x}_i \cdot \mathbf{x}_i = 1$
  i.e, $\forall i. \|\mathbf{x}_i\| = 1$

例如三维空间中一组标准正交基为：

$$
\begin{cases}
\mathbf{x}_1 = [1, 0, 0] \\
\mathbf{x}_2 = [0, 1, 0] \\
\mathbf{x}_3 = [0, 0, 1]
\end{cases}
$$

---

## 为什么我们可以进行 FT？

考虑线性代数中的性质：

如果有一组标准正交基，其 span 成的空间中的任意向量 $\mathbf{v}$，则 $\mathbf{v}$ 可以被这组基唯一表示。

就是说：对于这组正交基 span 成的空间中的任意一点都可以使用系数乘以这组基的线性组合来表示：

$$
\mathbf{v} = \sum_{i=1}^{n} \alpha_i \mathbf{x}_i
$$

---

## 为什么我们可以进行 FT？

$$
\mathbf{v} = \sum_{i=1}^{n} \alpha_i \mathbf{x}_i
$$

如果我们考虑 $\mathbf{v}$ 是一个信号，$\mathbf{x}_i$ 是正弦、余弦波， $\alpha_i$ 就是频域中的系数。 

那么对于任意信号，我们都可以使用正弦、余弦波的线性组合来表示。

---

## 正弦波和余弦波是正交的吗？

为了证明信号可以被正弦、余弦波表示，我们需要证明正弦、余弦波是正交的。

即需要证明如下：

$$
\begin{cases}
    \forall n \neq m. \int_{0}^{2\pi} \cos(nx) \cos(mx) dx = 0 \\
    \forall n \neq m. \int_{0}^{2\pi} \sin(nx) \sin(mx) dx = 0 \\
    \forall n \neq m. \int_{0}^{2\pi} \cos(nx) \sin(mx) dx = 0 \\
    \forall n. \int_{0}^{2\pi} \sin(nx) \sin(nx) dx = c \\
    \forall n. \int_{0}^{2\pi} \cos(nx) \cos(nx) dx = c \\
\end{cases}
$$

其中 $c$ 是一个常数。

这里不证明 $\int_{0}^{2\pi} \sin(nx) \sin(nx) dx = 1$ 是因为如果我们可以证明其为正交，那么我们可以通过归一化（乘上一个系数）来得到 $c=1$。 