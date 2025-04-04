# Orthogonal Complement

```{div} bigidea
The orthogonal complement $U^{\perp}$ of a subspace $U$ is the collection of all vectors which are orthogonal to every vector in $U$.
```

```{image} /img/02_02_01.png
:width: 100%
:align: center
```

## Orthogonal Vectors

```{div} definition
The **inner product** of vectors $\boldsymbol{x}, \boldsymbol{y} \in \mathbb{R}^n$ is

$$
\langle \boldsymbol{x} , \boldsymbol{y} \rangle = \sum_{k=1}^n x_k y_k = x_1y_1 + \cdots + x_ny_n
$$
```

```{div} note
Let's summarize various properties of the inner product:

The inner product is symmetric: $\langle \boldsymbol{x} , \boldsymbol{y} \rangle = \langle \boldsymbol{y} , \boldsymbol{x} \rangle$ for all $\boldsymbol{x}, \boldsymbol{y} \in \mathbb{R}^n$.

The inner product of column vectors is the same as matrix multiplication:

$$
\langle \boldsymbol{x} , \boldsymbol{y} \rangle = \boldsymbol{x}^T \boldsymbol{y} =
\begin{bmatrix} x_1 & \cdots & x_n \end{bmatrix} \begin{bmatrix} y_1 \\ \vdots \\ y_n \end{bmatrix}
$$

The inner product satisfies the usual distributive rules of multiplication:

$$
\langle \boldsymbol{x} ,  c \boldsymbol{y} + d \boldsymbol{z} \rangle = c \langle \boldsymbol{x} , \boldsymbol{y} \rangle + d \langle \boldsymbol{x} , \boldsymbol{z} \rangle
$$

for all $c,d \in \mathbb{R}$ and $\boldsymbol{x} , \boldsymbol{y} , \boldsymbol{z} \in \mathbb{R}^n$.

The square root of the inner product of a vector $\boldsymbol{x}$ with itself is equal to the 2-norm

$$
\sqrt{ \langle \boldsymbol{x} , \boldsymbol{x} \rangle } = \| \boldsymbol{x} \|
$$

We can also write the inner product in terms of the angle between vectors

$$
\langle \boldsymbol{x} , \boldsymbol{y} \rangle = \| \boldsymbol{x} \| \| \boldsymbol{y} \| \cos \theta \hspace{10mm} 0 \leq \theta \leq \pi
$$

Let $A$ be a $m \times n$ matrix, let $\boldsymbol{u} \in \mathbb{R}^n$ and let $\boldsymbol{v} \in \mathbb{R}^m$. Then

$$
\langle A \boldsymbol{u} , \boldsymbol{v} \rangle = \langle \boldsymbol{u} , A^T \boldsymbol{v} \rangle
$$

```

```{div} definition
Vectors $\boldsymbol{x}, \boldsymbol{y} \in \mathbb{R}^n$ are **orthogonal** if $\langle \boldsymbol{x} , \boldsymbol{y} \rangle = 0$. More generally, vectors $\boldsymbol{x}_1, \dots, \boldsymbol{x}_m \in \mathbb{R}^n$ are **orthogonal** if $\langle \boldsymbol{x}_i , \boldsymbol{x}_j \rangle = 0$ for all $i \not= j$. In other words, each $\boldsymbol{x}_i$ is orthogonal to every other vector $\boldsymbol{x}_j$ in the set. Furthermore, vectors $\boldsymbol{x}_1, \dots, \boldsymbol{x}_m \in \mathbb{R}^n$ are **orthonormal** if they are orthogonal and each is a unit vector, $\| \boldsymbol{x}_k \| = 1$, $k=1,\dots,m$.
```

```{div} note
Vectors $\boldsymbol{x}, \boldsymbol{y} \in \mathbb{R}^n$ are orthogonal if and only if the acute angle between $\boldsymbol{x}$ and $\boldsymbol{y}$ is $\pi/2$ radians (or 90 degrees).
```

```{div} theorem
Let $\boldsymbol{x}_1, \dots, \boldsymbol{x}_m \in \mathbb{R}^n$ be orthogonal. Then

$$
\| \boldsymbol{x}_1 + \cdots + \boldsymbol{x}_m \|^2 = \| \boldsymbol{x}_1 \|^2 + \cdots + \| \boldsymbol{x}_m \|^2
$$

This is called the **Pythagorean theorem**.

---

*Proof*. Compute the left side of the equation using orthogonality $\langle \boldsymbol{x}_i , \boldsymbol{x}_i \rangle = 0$ if $i \not= j$

$$
\begin{align*}
\| \boldsymbol{x}_1 + \cdots + \boldsymbol{x}_m \|^2 &= \langle \boldsymbol{x}_1 + \cdots + \boldsymbol{x}_m ,\boldsymbol{x}_1 + \cdots + \boldsymbol{x}_m \rangle \\
&= \sum_{i=1}^m \sum_{j=1}^m \langle \boldsymbol{x}_i , \boldsymbol{x}_j \rangle \\
&= \sum_{i=1}^m \langle \boldsymbol{x}_i , \boldsymbol{x}_i \rangle \\
&= \| \boldsymbol{x}_1 \|^2 + \cdots + \| \boldsymbol{x}_m \|^2
\end{align*}
$$

**Note:** This collapse of a double sum to a single sum is one of the ways that orthogonality becomes a powerful tool in applied linear algebra.
```

## Orthogonal Subspaces

```{div} definition
Let $U_1 \subseteq \mathbb{R}^n$ and $U_2 \subseteq \mathbb{R}^n$ be subspaces. Then $U_1$ and $U_2$ are **orthogonal** if $\langle \boldsymbol{x}_1 , \boldsymbol{x}_2 \rangle = 0$ for all $\boldsymbol{x}_1 \in U_1$ and $\boldsymbol{x}_2 \in U_2$. If $U_1$ and $U_2$ are orthogonal subspaces, then we write $U_1 \perp U_2$.
```

```{div} theorem
Let $\{ \boldsymbol{u}_1,\dots,\boldsymbol{u}_m \}$ be a basis of a subspace $U_1 \subseteq \mathbb{R}^n$ and let $\{ \boldsymbol{v}_1,\dots,\boldsymbol{v}_{\ell} \}$ be a basis of a subspace $U_2 \subseteq \mathbb{R}^n$. Then $U_1 \perp U_2$ if and only if $\langle \boldsymbol{u}_i , \boldsymbol{v}_j \rangle = 0$ for all $i,j$. In other words, every $\boldsymbol{u}_i$ in the basis of $U_1$ is orthogonal to each $\boldsymbol{v}_j$ in the basis of $U_2$.
```

````{div} example
Let $U_1 \subset \mathbb{R}^3$ and $U_2 \subset \mathbb{R}^3$ be 2-dimensional subspaces (planes). Is it possible that $U_1 \perp U_2$?

```{dropdown} Solution

No.

```
````

## Orthogonal Complement

```{div} definition
Let $U \subseteq \mathbb{R}^n$ be a subspace. The **orthogonal complement of $U$** is

$$
U^{\perp} = \{ \boldsymbol{x} \in \mathbb{R}^n : \langle \boldsymbol{x} , \boldsymbol{y} \rangle = 0 \text{ for all } \boldsymbol{y} \in U \}
$$
```

```{div} note
<p>

* If $U \subseteq \mathbb{R}^n$ is any subspace then $U = (U^{\perp})^{\perp}$ and also $U \cap U^{\perp} = \{ \boldsymbol{0} \}$.
* $\{ \boldsymbol{0} \}^{\perp} = \mathbb{R}^n$.

</p>

```

```{div} theorem
Let $U \subseteq \mathbb{R}^n$ be a subspace. Then $U^{\perp} \subseteq \mathbb{R}^n$ is a subspace.

---

*Proof*. Let us verify that $U^{\perp}$ satisfies the properties of a subspace.

Clearly $\langle \boldsymbol{0} , \boldsymbol{x} \rangle = 0$ for all $\boldsymbol{x} \in U$ therefore $\boldsymbol{0} \in U^{\perp}$.

Let $\boldsymbol{x}_1,\boldsymbol{x}_2 \in U^{\perp}$. Then

$$
\langle \boldsymbol{x}_1 + \boldsymbol{x}_2 , \boldsymbol{y} \rangle = \langle \boldsymbol{x}_1 , \boldsymbol{y} \rangle + \langle \boldsymbol{x}_2 , \boldsymbol{y} \rangle = 0 + 0 = 0
$$

for all $\boldsymbol{y} \in U$ therefore $\boldsymbol{x}_1 + \boldsymbol{x}_2 \in U^{\perp}$.

Let $c \in \mathbb{R}$ and $\boldsymbol{x} \in U^{\perp}$. Then

$$
\langle c\boldsymbol{x} , \boldsymbol{y} \rangle = c \langle \boldsymbol{x} , \boldsymbol{y} \rangle = c(0) = 0
$$

for all $\boldsymbol{y} \in U$ therefore $c \boldsymbol{x} \in U^{\perp}$.

Therefore $U^{\perp}$ is a subspace.
```

````{div} example
Compute ${U}^{\perp}$ complement where $U = \mathrm{span}\left\{ \begin{bmatrix} 1 \\ 2 \\ 5 \end{bmatrix}, \begin{bmatrix} 1 \\ 4 \\ 1\end{bmatrix}\right\}$

```{dropdown} Solution

The basis vectors for the subspace $U$ are the vector $u_1$ and $u_2$ (in the above definition).
By the last theorem in the previous section, we must find the basis vector for $U^{\perp} = \mathrm{span}\left\{ w \right\}$,
so that $u_1^T w = 0$ and $u_2^T w = 0$. These are two linear equations, which we can write as a linear system

$$
\begin{pmatrix} u_1^T \\ u_2^T \end{pmatrix} \begin{pmatrix} w_1 \\ w_2 \\ w_3 \end{pmatrix} = 0
\quad\iff\quad
\begin{pmatrix} 1 & 2 & 5 \\ 1 & 4 & 1 \end{pmatrix} \begin{pmatrix} w_1 \\ w_2 \\ w_3 \end{pmatrix} = 0
$$

Row reducing we find that

$$
    w = \begin{pmatrix} -9 \\ 2 \\ 1 \end{pmatrix}.
$$

<!---
First compute the nullspace of $W$

$$
\begin{bmatrix} 1 & 2 & 5 \\ 1 & 4 & 1 \end{bmatrix}
\longrightarrow
\begin{bmatrix} 1 & 2 & 5 \\ 0 & 2 & -4 \end{bmatrix}
\longrightarrow
\begin{bmatrix} 1 & 2 & 5 \\ 0 & 1 & -2 \end{bmatrix}
\longrightarrow
\begin{bmatrix} 1 & 0 & 9 \\ 0 & 1 & -2 \end{bmatrix}
$$

This means that

$$
N[W] = \mathrm{span}\left\{\begin{bmatrix} -9 \\ 2 \\ 1 \end{bmatrix}\right\},
\quad\mbox{and}\quad
{W}^{\perp} = \mathrm{span}\left\{\begin{bmatrix} -9 \\ 2 \\ 1 \end{bmatrix}\right\}.
$$

Finally we verify orthogonality:

$$
\begin{bmatrix} 1 & 2 & 5 \end{bmatrix}\begin{bmatrix} -9 \\ 2 \\ 1 \end{bmatrix}=0,
\quad\mbox{and}\quad
\begin{bmatrix} 1 & 4 & 1 \end{bmatrix}\begin{bmatrix} -9 \\ 2 \\ 1 \end{bmatrix}=0.
$$
--->

```
````

## Exercises

````{div} exercise
Determine whether the statement is **True** or **False**.

* Let $U \subseteq \mathbb{R}^n$ be a subspace. If $\boldsymbol{u} \in \mathbb{R}^n$ such that $\boldsymbol{u} \not= 0$ then either $\boldsymbol{u} \in U$ or $\boldsymbol{u} \in U^{\perp}$.
* Let $L_1 \subset \mathbb{R}^2$ be a line through the origin. There is a unique line $L_2 \subset \mathbb{R}^2$ through the origin such that $L_1 \perp L_2$.
* Let $L_1 \subset \mathbb{R}^3$ be a line through the origin. There is a unique line $L_2 \subset \mathbb{R}^3$ through the origin such that $L_1 \perp L_2$.
* Let $U_1 \subset \mathbb{R}^4$ be a 2-dimensional subspace. There is a unique 2-dimensional subspace $U_2 \subset \mathbb{R}^4$ through the origin such that $U_1 \perp U_2$.

```{dropdown} Solution
* False, counterexample: let U=span$\left\{\begin{bmatrix} 1 \\ 0 \end{bmatrix}\right\}$ is a subspace of $\mathbb{R}^2$, then ${U}^{\perp}$=span$\left\{\begin{bmatrix} 0 \\ 1 \end{bmatrix}\right\}$. But the vector u = $\begin{bmatrix} 1 \\ 1 \end{bmatrix}$ $\in \mathbb{R}^2$ is $u \notin U$ and $u \notin {U}^{\perp}$. However since $\mathbb{R}^2 = U \oplus {U}^{\perp}$, we can decompose every vector in $\mathbb{R}^2$ into a component that lies in $U$ and a component that lies in ${U}^{\perp}$.
* True, $\mathbb{R}^2$ is a plane, so you can draw a line perpendicular to any line in $\mathbb{R}^2$ but only one.
* False, consider the intersection of the xyz axis.
* True, the dimension of the orthogonal complement is also 2 which implies it is uniquely determined by finding two vectors perpendicular to every vector in the original subspace.
```

````

````{div} exercise
Determine whether the statement is **True** or **False**.

* If $A^TA$ is a diagonal matrix, then the columns of $A$ are orthogonal.
* If $AA^T$ is a diagonal matrix, then the columns of $A$ are orthogonal.
* If $A^TA$ is a diagonal matrix, then the rows of $A$ are orthogonal.
* If $AA^T$ is a diagonal matrix, then the rows of $A$ are orthogonal.

```{dropdown} Solution
* True, because if A^TA is diagonal, the inner product of difference columns with themselves are nonzero because A^TA represents the inner product of the columns of A with themselves.
* False, AA^T being diagonal does not necessarily mean that the columns of A are orthogonal.
* False, A^TA being diagonal does not necessarily mean that the rows of A are orthogonal.
* True, by the same reasoning as the first question.
```
````

````{div} exercise
Determine whether the statement is **True** or **False**.

Let $\boldsymbol{u}_1,\boldsymbol{u}_2,\boldsymbol{u}_3 \in \mathbb{R}^3$ be nonzero vectors. If $\boldsymbol{u}_1$ is orthogonal to $\boldsymbol{u}_2$, and $\boldsymbol{u}_2$ is orthogonal to $\boldsymbol{u}_3$ then $\boldsymbol{u}_1$ is orthogonal to $\boldsymbol{u}_3$.

```{dropdown} Solution
False, consider a vector pointing in -x, another in +x, and a third in +y.
```
````

