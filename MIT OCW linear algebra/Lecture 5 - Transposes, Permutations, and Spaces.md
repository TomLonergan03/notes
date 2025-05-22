# Permutations and A=LU
Our existing [[Lecture 4 - Factorisation into A=LU#Factorisation|factorisation approach]] assumes no [[Lecture 2 - Elimination with Matrices#Permutation matrices|row exchanges]] occur. To account for permutations, we change our factorisation equation to
$$
PA=LU
$$
where $P$ is the permutation matrix that performs all needed row exchanges. We can perform the same factorisation approach, and just determine which permutation of rows we used giving us the value of $P$.

The inverse of a permutation is equivalent to the transpose of that permutation:
$$
P^{-1}=P^T
$$
# Symmetric matrices
A **symmetric matrix** is a matrix where $A^T=A$, e.g:
$$
\begin{bmatrix}
3&-1&7\\
-1&2&9\\
7&9&4
\end{bmatrix}
$$
We can produce a symmetric matrix from any matrix multiplied by its transpose, $R^TR$, e.g.
$$
\begin{bmatrix}
1&3\\
2&3\\
4&1
\end{bmatrix}
\begin{bmatrix}
1&2&4\\
3&3&1
\end{bmatrix}
=\begin{bmatrix}
10&11&7\\
11&13&11\\
7&11&17
\end{bmatrix}
$$
This is as when we calculate $C_{ij}$, we combine row $i$ with column $j$, whereas when we calculate $C_{ji}$ we combine row $j$ with column $i$, and by the definition of transposition a transposed matrix is produced by swapping rows and columns, so row $i$ of the original matrix will be identical to column $i$ of the transposed matrix.

Another way to look at it is if we have $R^TR$ and take the transposition, we will get $R^TR$. This is because, like [[Lecture 3 - Multiplication and Inverse Matrices#Inverses|inverses]], the transpose of a combination of matrices is the transpose of each individual matrix, with the order reversed, so $(R^TR)^T$ becomes $R^T(R^T)^T=R^TR$.
# Vector spaces
**Vector spaces** consist of collections of vectors. These vectors can be added together, and multiplied by scalars, along with some other conditions. An example of a vector space is $R^2$, consisting of all 2-dimensional real vectors (such as $\begin{bmatrix}3\\2\end{bmatrix}$, $\begin{bmatrix}0\\0\end{bmatrix}$, $\begin{bmatrix}\pi\\e\end{bmatrix}$) and is the classic $x$-$y$ plane. $R^n$ is a vector space containing all vectors with $n$ components.

If we add any two vectors in a vector space the resultant vector will also be in that vector space, and if we multiply a vector by any scalar value the resultant vector will be in the same vector space.
## Axioms
The following eight axioms must be satisfied for every vector $u,v,w$ in a vector space $V$ over all scalars $a,b$:
- **Associativity** of vector addition: $u+(v+w)=(u+v)+w$.
- **Commutativity** of vector addition: $u+v=v+u$.
- **Identity** of vector addition: there exists an element $\mathbf{0}\in V$ (the **zero vector**) such that $v+\mathbf{0}=v$ for all $v\in V$.
- **Inverse elements** of vector addition: for every $v\in V$ there exists an element $-v\in V$ (the **additive inverse** of $v$) such that $v+(-v)=\mathbf{0}$.
- **Compatibility** of scalar multiplication: $a(bv)=(ab)v$
- **Identity** of scalar multiplication: $1v=v$
- **Distributivity** of scalar multiplication over vector addition: $a(u+v)=au+av$
- **Distributivity** of scalar multiplication over scalar addition: $(a+b)v=av+bv$
# Subspaces
A **subspace** is a vector space that is contained within another vector space.

A subspace of $R^2$ could be formed by any single vector within $R^2$ along with all scalar multiples of that vector. This subspace is essentially a line through $R^2$ with all points on that line being in the subspace, as adding any pair of vectors on the line will result in another vector on the line, and multiplying a vector on the line by any scalar will produce another vector on the line. This subspace will contain $\mathbf{0}$, as 0 times the vector will equal $\mathbf{0}$, and so must all subspaces contain $\mathbf{0}$.

The subspaces of $R^2$ consist of:
1. All of $R^2$.
2. Any line through $\begin{bmatrix}0\\0\end{bmatrix}$, and can be called $\mathbf{L}$ for line. (This is not the same as $R^1$ as though the subspace is a line, like $R^1$, the vectors in the subspace still have 2 components).
3. The zero vector only (can be called $\mathbf{Z}$ for zero).

Similarly the subspaces of $R^3$ are all of $R^3$, a plane through the origin, a line through the origin, and the origin alone, and so on through higher dimensional vector spaces.

If we have a matrix:
$$
A=\begin{bmatrix}
1&3\\
2&3\\
4&1
\end{bmatrix}
$$
we can use it to create a subspace from $R^3$ (as it has 2 columns with 3 items each). This subspace consists of all combinations and scalar multiplications of both columns of the matrix, forming a plane through the origin. This subspace is the **column space** formed by the matrix.