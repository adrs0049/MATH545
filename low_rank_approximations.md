# Low Rank Approximations

```{div} Big Idea
Real world data is often very high-dimensional. However, correlations between observed features makes it so that it lies close to some low-dimensional subspace. This subspace allows for compressing the data into low dimensions which is computationally easy to work with.
```

## Representing Data as Matrices and Vectors

In Data Analysis and ML, data points with many attributes is stored and interpreted as a *high dimensional vector* with real valued entries.

Henceforth, we represent data points $\boldsymbol{x_1}, \boldsymbol{x_2}, \boldsymbol{x_3}, \ldots, \boldsymbol{x_p} \in \R^d$, 
and a dataset contains datapoints stacked column wise as $\boldsymbol{X} \in \R^{d \times n}$ where the $i$-th column is the $i$-th datapoint.

We want to find a lossy compression $\boldsymbol{x_1}, \boldsymbol{x_2}, \boldsymbol{x_3}, \ldots, \boldsymbol{x_p} \in \R^d \to \tilde{x}_1, \ldots, \tilde{x}_n \in \R^m, m \ll d$ such that the low dimensional points preserve important relationships between $\boldsymbol{x}_1, \ldots, \boldsymbol{x}_n$.

## Johnson-Lindenstrauss Lemma
One of the most common tasks performed in high dimension regimes is that of nearest neighbour search, i.e., given a point $\boldsymbol x \in \R^D$, find points $\boldsymbol y$ such that $\|\boldsymbol{y - x}\| \le R$ for some positive parameter $R$. It is desirable to perform this computation in a low dimensional space. In Data Science, this preprocessing is referred to as 'embedding' the data in low dimensional space

**Theorem:**
Given a set of points $\boldsymbol{x}_{1}, \ldots, \boldsymbol{x}_n \in \R^d$
and tolerance $0 < \varepsilon < 1$, there exists a linear map $M : \R^d \to  \R^m$ such that $m = O(\frac{\log n}{\varepsilon^2})$, and denoting $\tilde{x}_i = M\boldsymbol{x}_i$,
$$ \forall\, i,j \: : \:(1-\varepsilon) \| \boldsymbol{x}_i - \boldsymbol{x}_j \| \le \| \tilde{x}_i - \tilde{x}_j \| \le (1+\varepsilon) \|\boldsymbol{x}_i - \boldsymbol{x}_j\| $$

**Note**: Such an embedding, where pairwise distances are preserved is called a low-distortion embedding. Additionally, if matrix $M$ is chosen such that each entry is i.i.d. random sampled from the Gaussian distribution
$\mathcal{N}(0, 1/m)$, the theorem result is true with high probability.

**Proof:** Beyond the scope of Math 545, but a useful concept! Reading: Section 2.7 of [Foundations of Data Science](https://www.cs.cornell.edu/jeh/book.pdf)

**Takeaway:** The matrix $M$ always exists, is independent of observed data, and is invariant, allowing for parallel processing of data, and reduces data dimensionality significantly: suppose $n = 1,000,000$, $\varepsilon = 0.05$, then $m \approx 5530$.


## Low-Rank Approximation
Another class of compression method derives from the singular value decompositions of a matrix.

Recall the SVD expansion: Let $A$ be a $m \times n$ matrix such that $\mathrm{rank}(A) = r$ and $A = P \Sigma Q^T$ be the singular value decomposition. Then

$$
A = \sum_{i=1}^r \sigma_i \boldsymbol{p}_i \boldsymbol{q}_i^T = \sigma_1 \boldsymbol{p}_1 \boldsymbol{q}_1^T + \cdots + \sigma_r \boldsymbol{p}_r \boldsymbol{q}_r^T
$$

where $\boldsymbol{p}_1,\dots,\boldsymbol{p}_r$ are the first $r$ columns of $P$, and $\boldsymbol{q}_1,\dots,\boldsymbol{q}_r$ are the first $r$ columns of $Q$.

We shall now extend this notion to matrices of high rank.
Henceforth, let $A$ be a $m\times n$ matrix, with high rank. Define the $k$-rank approximation of $A$ as
$$
A_k = \sum_{i=1}^k \sigma_i \boldsymbol{p}_i \boldsymbol{q}_i^T = \sigma_1 \boldsymbol{p}_1 \boldsymbol{q}_1^T + \cdots + \sigma_k \boldsymbol{p}_k \boldsymbol{q}_k^T
$$

Theorem: $\|A - A_k\|_2 = \sigma_{k+1}$

Proof:
See that $A - A_k = \sum_{i=k+1}^n \sigma_i\boldsymbol{p}_i\boldsymbol{q}_i^T$. We shall consider a vector in the domain of $A$ as $\boldsymbol{q}$, which can be expressed as a linear combination of all the right singular vectors as $\boldsymbol{q} = \sum_{j=1}^n c_j \boldsymbol{q}_j$. Let us consider maximizing the norm
$$
\begin{aligned}
\max_{\|q\| = 1} \|(A-A_k)q\| &= \max_{\|q\| = 1} \Big\|\sum_{i=k+1}^{n} 
\sigma_i \boldsymbol{p}_i\boldsymbol{q}_i^T \sum_{j=1}^n c_n \boldsymbol{q}_j\Big\| \\
&= \max_{\|q\| = 1} \Big\| \sum_{i=k+1}^n c_i \sigma_i \boldsymbol{p}_i\Big\|\\
&= \max_{\|q\|=1} \sqrt{\sum_{i=k+1}^n c_i^2 \sigma_i^2}
\end{aligned}
$$
under the constraint $\|q\|^2 = 1 = \sum_{i=1}^n c_i^2$ since all the $\boldsymbol{q}_i$ are orthonormal. The norm is maximized precisely when $c_{k+1} = 1$ and rest all $c_i$, $i > k+1$ are zero. Thus, 
$$
\|A - A_k\|^2 = \max_{\|q\| = 1} \|(A - A_k)q\|_2^2 = \sigma_{k+1}^2
$$

Theorem: $A_k$ is the rank $k$ fit to $A$, i.e., $\|A - A_k\|\le \|A-B\|$ where $B$ is any matrix of rank $\le k$.

Proof:
If $A$ is rank $k$ or less, $A = A_k$ and $\|A - A_k\|=0$, which is the minimizer of the norm. This is the simple case. Next, consider a matrix $A$ greater than $k$ and a matrix $B$ of rank at most $k$. The dimension of the nullspace of $B$ is $\ge n-k$ by Rank-Nullity. Consider a unit vector in $N[B]$ which is also contained in the span of $\{\boldsymbol{q}_1, \ldots, \boldsymbol{q}_{k+1}\}$, named $w$. Since $Bw$ = 0, 
$$
\begin{aligned}
\|(A-B) w\|^2 &\ge \|Aw\|^2 = \Big\|\sum_{i=1}^n \sigma_i \boldsymbol{p}_i \boldsymbol{q}_i^T w \Big\|^2 \\
&= \sum_{i=1}^n \sigma_i^2 \langle \boldsymbol{q}_i, w \rangle^2 \\
&=\sum_{i=1}^{k+1} \sigma_i^2 \langle \boldsymbol{q}_i, w \rangle^2 \\
&\ge \sigma_{k+1}^2 \sum_{i=1}^{k+1}\langle \boldsymbol{q}_i, w \rangle^2  = \sigma_{k+1}^2\\
&= \|A - A_k\|^2
\end{aligned}
$$

What does this mean? 

Suppose we have a dataset $X$ with datapoints stacked columnwise. We can analyze the spectral plot of $X$, i.e., a plot of $\sigma_i$ v.s. $i$, a short tail indicates that the rank $k$ approximation is a good fit for the dataset.

See that for the MNIST dataset consisting of 10000 columns each of 784 rows each, the spectrum decays very fast. Thus, an approximation of rank 100 should suffice in capturing most of the essential information of the data.   
![pic alt](../img/mnist_spec.png  "Spectrum of MNIST data")

See that in this case, there is no decay in the spectrum, whereby a low-rank approximation is not suited for approximating Gaussian noise.

![pic alt](../img/rand_spec.png "Spectrum of Gaussian Noise")
