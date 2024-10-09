# Subspaces

```{div} bigidea
Subspaces of $\mathbb{R}^n$ include lines, planes and hyperplanes through the origin. A basis of a subspace is a linearly independent set of spanning vectors. The Rank-Nullity Theorem describes the dimensions of the nullspace and range of a matrix.
```

```{image} /img/02_01_01.png
:width: 100%
:align: center
```

## Subspaces

```{div} definition
A subset $U \subseteq \mathbb{R}^n$ is a **subspace** if:

1. $U$ contains the zero vector $\boldsymbol{0}$
2. $\boldsymbol{u}_1 + \boldsymbol{u}_2 \in U$ for all $\boldsymbol{u}_1,\boldsymbol{u}_2 \in U$
3. $c \boldsymbol{u} \in U$ for all $c \in \mathbb{R},\boldsymbol{u} \in U$

Condition 2 is called **closed under addition**. Condition 3 is called **closed under scalar multiplication**. Condition 3 with $c=0$ implies Condition 1.
```

```{div} example
<p>

* The zero subspace $\{ \boldsymbol{0} \}$ and the entire space $\mathbb{R}^n$ are both subspaces of $\mathbb{R}^n$.
* Subspaces of $\mathbb{R}^2$ include any line through the origin.
* Subspaces of $\mathbb{R}^3$ include any line or plane through the origin.
* In general, subspaces of $\mathbb{R}^n$ are hyperplanes of any dimension through the origin.

</p>
```

````{div} example
Consider the set

$$
U = \left\{ \begin{bmatrix} x \\ y \end{bmatrix} : y \geq 0 \right\}
$$

Is $U \subset \mathbb{R}^2$ a subspace?

```{dropdown} Solution

Then $U$ contains the zero vector

$$
\boldsymbol{0} = \begin{bmatrix} 0 \\ 0 \end{bmatrix} \in U
$$

and $U$ is closed under addition since

$$
\boldsymbol{u}_1 + \boldsymbol{u}_2 = \begin{bmatrix} x_1 \\ y_1 \end{bmatrix} + \begin{bmatrix} x_2 \\ y_2 \end{bmatrix} = \begin{bmatrix} x_1 + x_2 \\ y_1 + y_2 \end{bmatrix} \in U
$$

because $y_1 + y_2 \geq 0$ since $y_1 \geq 0$ and $y_2 \geq 0$. However $U$ is not closed under scalar multiplication because

$$
(-1) \begin{bmatrix} 1 \\ 1 \end{bmatrix} = \begin{bmatrix} -1 \\ -1 \end{bmatrix} \not\in U
$$

Therefore $U$ is not a subspace of $\mathbb{R}^2$.
```
````

## Linear Independence and Span

```{div} definition
A **linear combination** of vectors $\boldsymbol{u}_1,\dots,\boldsymbol{u}_m \in \mathbb{R}^n$ is a vector

$$
c_1 \boldsymbol{u}_1 + \cdots + c_m \boldsymbol{u}_m
$$

where $c_1,\dots,c_m \in \mathbb{R}$. The **span** of vectors $\boldsymbol{u}_1,\dots,\boldsymbol{u}_m \in \mathbb{R}^n$ is the set of all linear combinations

$$
\mathrm{span} \{ \boldsymbol{u}_1 , \dots , \boldsymbol{u}_m \} = \{ c_1 \boldsymbol{u}_1 + \cdots + c_m \boldsymbol{u}_m \in \mathbb{R}^n : c_1,\dots,c_m \in \mathbb{R} \}
$$
```

```{div} theorem
Let $\boldsymbol{u}_1 , \dots , \boldsymbol{u}_m \in \mathbb{R}^n$. Then $\mathrm{span} \{ \boldsymbol{u}_1 , \dots , \boldsymbol{u}_m \}$ is a subspace of $\mathbb{R}^n$.
```

```{div} example
The span of a single nonzero vector $\boldsymbol{u}$ is a line with direction $\boldsymbol{u}$. The span of two nonzero vectors $\boldsymbol{u}$ and $\boldsymbol{v}$ is a plane as long as $\boldsymbol{u}$ and $\boldsymbol{v}$ are not colinear.
```

```{div} definition
A set of vectors $\{ \boldsymbol{u}_1,\dots,\boldsymbol{u}_m \} \subset \mathbb{R}^n$ forms a **linearly independent** set if the vectors satisfy the property:

$$
c_1 \boldsymbol{u}_1 + \cdots + c_m \boldsymbol{u}_m = \boldsymbol{0} \hspace{5mm} \text{if and only if} \hspace{5mm} c_1 = \cdots = c_m = 0
$$

In other words, $\{ \boldsymbol{u}_1,\dots,\boldsymbol{u}_m \}$ is a linearly independent set if no vector in the set can be expressed as a linear combination of the others.
```

```{div} note
How do we know if a set of vectors $\{ \boldsymbol{u}_1,\dots,\boldsymbol{u}_m \}$ is linearly independent? Create a matrix where the columns are the given vectors

$$
A = \begin{bmatrix} & & \\ \boldsymbol{u_1} & \cdots & \boldsymbol{u_m} \\ & & \end{bmatrix}
$$

Then $\{ \boldsymbol{u}_1,\dots,\boldsymbol{u}_m \}$ is a linearly independent set if and only if the linear system $A \boldsymbol{x} = \boldsymbol{0}$ has only the trivial solution $\boldsymbol{x} = \boldsymbol{0}$.
```

## Basis and Dimension

```{div} definition
Let $U \subseteq \mathbb{R}^n$ be a subspace. A set of vectors $\{ \boldsymbol{u}_1 , \dots , \boldsymbol{u}_m \}$ forms a **basis** of $U$ if:

1. $\{ \boldsymbol{u}_1 , \dots , \boldsymbol{u}_m \}$ is a linearly independent set
2. $\mathrm{span} \{ \boldsymbol{u}_1 , \dots , \boldsymbol{u}_m \} = U$

The **dimension** of $U$ is the number $m$ of vectors in a basis.
```


```{div} note
Note that the first condition in the preceding definition guarantees that basis are **minimal** i.e. contain the smallest number of vectors which span the vectorspace $U$.
```

## Exercises

````{div} exercise
Determine whether or not the set

$$
U = \left\{ \begin{bmatrix} a \\ b \\ c \end{bmatrix} : abc = 0 \right\}
$$

is a subspace of $\mathbb{R}^3$.

```{dropdown} Solution
$U$ is not a subspace because it is not closed under vector addition.
```

````

````{div} exercise
Determine whether $\mathrm{span} \{ \boldsymbol{u}_1 , \boldsymbol{u}_2 \} = \mathrm{span} \{ \boldsymbol{u}_3 , \boldsymbol{u}_4 \}$ where

$$
\boldsymbol{u}_1 = \left[ \begin{array}{r} 2 \\ -3 \\ 1 \\ -1 \end{array} \right] \hspace{10mm}
\boldsymbol{u}_2 = \left[ \begin{array}{r} -5 \\ 1 \\ 2 \\ -2 \end{array} \right] \hspace{10mm}
\boldsymbol{u}_3 = \left[ \begin{array}{r} -1 \\ -5 \\ 4 \\ -4 \end{array} \right] \hspace{10mm}
\boldsymbol{u}_4 = \left[ \begin{array}{r} 3 \\ -11 \\ 6 \\ -10 \end{array} \right]
$$

```{dropdown} Solution
$\mathrm{span} \{ \boldsymbol{u}_1 , \boldsymbol{u}_2 \} \ne \mathrm{span} \{ \boldsymbol{u}_3 , \boldsymbol{u}_4 \}$ since $\boldsymbol{u}_1,\boldsymbol{u}_2,\boldsymbol{u}_4$ are linearly independent.
```

````

````{div} exercise
Let $U = \mathrm{span} \{ \boldsymbol{u}_1 , \boldsymbol{u}_2 , \boldsymbol{u}_3 , \boldsymbol{u}_4 \} \subseteq \mathbb{R}^4$ where

$$
\boldsymbol{u}_1 = \left[ \begin{array}{r} 2 \\ 4 \\ 4 \\ 2 \end{array} \right] \hspace{10mm}
\boldsymbol{u}_2 = \left[ \begin{array}{r} 3 \\ 5 \\ 3 \\ 1 \end{array} \right] \hspace{10mm}
\boldsymbol{u}_3 = \left[ \begin{array}{r} 3 \\ 3 \\ -1 \\ -11 \end{array} \right] \hspace{10mm}
\boldsymbol{u}_4 = \left[ \begin{array}{r} 0 \\ 3 \\ 11 \\ -2 \end{array} \right]
$$

* Find a basis and the dimension of $U$.
* Is $\{ \boldsymbol{u}_1 , \boldsymbol{u}_3 , \boldsymbol{u}_4 \}$ a basis of $U$? Explain.

```{dropdown} Solution
$\dim(U) = 3$ and $\{ \boldsymbol{u}_1 , \boldsymbol{u}_3 , \boldsymbol{u}_4 \}$ also forms a basis of $U$.
```

````


