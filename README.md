# MTH211_Final
## Overview

### Understanding Rank
A matrix has rank k if its columns (or its rows) span a subspace of dimension k (i.e. there are k pivots in the RREF). However we have some equivalent definitions.

- Rank-0: Zero matrix
- Rank-1: All rows are multiples of each other, $A=uv^T$.

Example of Rank-1: $$u=
\begin{pmatrix}
  x \\
  y \\
  z
\end{pmatrix}
$$ and $v^T=(a,b,c)$ so $uv^T=\pmatrix{ax&bx&cx \\ ay&by&cy \\ az&bz&cz}$ $\leftarrow$ every column is a multiple of $u$ and every row is a multiple of $v$

- Rank- $k$: $A=\sum\limits_{i=1}^{k}u_iv_i^T$, $A=YZ^T$ where $Y$ is $m\times k$, $Z^T$ is $k\times n$

### Low-Rank Approximation
A given matrix $A$ has a large dimension $m\times n$ ($mn$ elements) but using $A=YZ^T$ we get two matrices with $mk+nk$ elements. If $k$ is small then we have much fewer elements.

### Singular Value Decomposition
Singular Value Decomposition works for general matrices. Basically, any $m\times n$ matrix $A$ can be written as $A=USV^T$ where:

- $U$: $m\times m$ orthogonal matrix (left singular vectors)
- $V$: $n\times n$ orthogonal matrix (right singular vectors)
- $S$: $m\times n$ diagonal matrix with non-negative entries (called singular values)

We can calculate SVD for a given matrix in Matlab using the command `[U,S,V] = svd(A)`

Singular Values($\sigma$) are the square root of a $A^TA$'s positive nonzero eigenvalues. The values of the main diagonal of matrix $S$ are the singular values.

SVD expresses $A$ as a weighted sum of rank-1 components ordered by importance ($s_1\geq s_2\geq \cdots \geq s_r$).

### Computing Low-Rank Approximations
Rank-$k$ approximation:
- Keep only the top $k$ singular values and vectors:
$$A_k=\sum\limits_{i=1}^ks_iu_iv_i=U_kS_kV_k^T$$
Where:

$U_k$ is first $k$ columns of $U$,

$S_k$ is $k\times k$ diagonal matrix of top singular values,

$V_k$ is first $k$ columns of $V$

### Choosing $k$
Choose $k$ such that:
$$\frac{\sum\limits_{i=1}^ks_i^2}{\sum\limits_{j=1}^{\text{min}(m,n)}s_j^2}\geq 0.9$$
