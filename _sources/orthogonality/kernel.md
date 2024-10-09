# The nullspace and range

```{div} bigidea
The Rank-Nullity Theorem describes the dimensions of the nullspace and range of a matrix.
```

## The Nullspace

```{div} definition
The **nullspace** of a $m \times n$ matrix $A$ is

$$
N(A) = \{ \boldsymbol{x} \in \mathbb{R}^n : A\boldsymbol{x} = \boldsymbol{0} \}
$$
```

```{div} theorem
Let $A$ be a $m \times n$ matrix. The nullspace $N(A)$ is a subspace of $\mathbb{R}^n$.
```

```{div} theorem
Let $A$ be a $m \times n$ matrix and let $A = LU$ be the LU decomposition (if it exists). Then $N(A) = N(U)$.
```

## The Range

```{div} definition
The **range** of a $m \times n$ matrix $A$ is:

$$
R(A) = \{ A \boldsymbol{x} : \boldsymbol{x} \in \mathbb{R}^n \}
$$

The range of $A$ is also called **image** or **column space** of $A$.
```

```{div} note
Matrix multiplication can be written as

$$
A \boldsymbol{x} = \begin{bmatrix} & & \\ \boldsymbol{a}_1 & \cdots & \boldsymbol{a}_n \\ & & \end{bmatrix} \begin{bmatrix} x_1 \\ \vdots \\ x_n \end{bmatrix} = x_1 \boldsymbol{a}_1 + \cdots + x_n \boldsymbol{a}_n
$$

Therefore the range of $A$ is the equal to the span of the columns

$$
R(A) = \mathrm{span} \{ \boldsymbol{a}_1 , \dots, \boldsymbol{a}_n \}
$$

and that's why $R(A)$ is sometimes called the column space.
```

```{div} theorem
Let $A$ be a $m \times n$ matrix. The range $R(A)$ is a subspace of $\mathbb{R}^m$.
```

```{div} theorem
Let $A$ be an $m \times n$ matrix. Then

$$
\dim (R(A)) = \mathrm{rank}(A)
$$

---

*Proof*. The rank of $A$ is the number of nonzero rows in the row echelon form of $A$. The dimension of $R(A)$ is the number of linearly independent columns in $A$ which is also equal to the number of nonzero rows in $A$.
```

```{div} theorem
Let $A = PLUQ$ be the LU decomposition of $A$ computed with row-swaps ($P$) and column-swaps ($Q$) and let $r = \mathrm{rank}(A)$. Then

$$
R(A) = \mathrm{span} \{ \boldsymbol{\ell}_1 , \dots , \boldsymbol{\ell}_r \}
$$

where $\boldsymbol{\ell}_1 , \dots , \boldsymbol{\ell}_r$ are the first $r$ columns of $L$. In particular, $\boldsymbol{\ell}_1 , \dots , \boldsymbol{\ell}_r$ is a basis of $R(A)$.

---

*Proof*. If $\mathrm{rank}(A) = r$ then only the first $r$ entries of the vector $U \boldsymbol{x}$ are nonzero

$$
U \boldsymbol{x} = \begin{bmatrix} * & * & \cdots & * \\ 0 & \ddots & \ddots & \vdots \\ \vdots & \ddots & * & * \\ 0 & \cdots & 0 & 0 \end{bmatrix} \boldsymbol{x} = \begin{bmatrix} * \\ \vdots \\ * \\ 0 \end{bmatrix}
$$

**Note**, that this particular form of the matrix $U$ is only guaranteed when you do **full pivoting** i.e. both row and column swaps. Therefore

$$
LU \boldsymbol{x} = \begin{bmatrix} & & \\ \boldsymbol{\ell}_1 & \cdots & \boldsymbol{\ell}_n \\ & & \end{bmatrix} \begin{bmatrix} * \\ \vdots \\ * \\ 0 \end{bmatrix} = (*) \boldsymbol{\ell}_1 + \cdots + (*) \boldsymbol{\ell}_r
$$
```






## Rank-Nullity Theorem

```{div} theorem
Let $A$ be an $m \times n$ matrix. Then

$$
\dim(R(A)) + \dim(N(A)) = n
$$

---

*Proof*. The dimension of $N(A)$ is equal to the number of columns of the row echelon form of $A$ *without* a leading nonzero entry, and $\mathrm{rank}(A) = \dim(R(A))$ is equal to the number of columns of the row echelon form of $A$ *with* a leading nonzero entry, and there are $n$ total columns.
```


## Exercises

````{div} exercise
Let $A = LU$ be the LU decomposition of $A$. Determine whether the statement is **True** or **False**.

* $N(A) = N(U)$
* $\dim (N(A)) = \dim (N(U))$
* $R(A) = R(U)$
* $\dim (R(A)) = \dim (R(U))$

```{dropdown} Solution
* True
* True
* False
* True
```

````
