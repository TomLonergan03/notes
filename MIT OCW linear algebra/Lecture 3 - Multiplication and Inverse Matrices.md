When multiplying matrices, they must either both be square and of the same size, or otherwise, for $C=AB$, if $A$ is $m\times n$ then $B$ must be $n\times p$ for any $p$, producing a matrix $C$ with dimensions $m\times p$.

There are a number of ways to perform matrix multiplication for matrices $C=AB$:
1. Each entry in $C$ at $(i,j)$ can be found by taking the dot product of row $i$ of $A$ with row $j$ of $B$. e.g. to find $C_{34}$ for 2 4x4 matrices, $C_{34}=A_{31}B_{14}+A_{32}B_{24}+...=\Sigma^n_{k=1}a_{3k}b_{k4}$.
2. Each column in $C$ is equivalent to performing a multiplication of $A$ times that column in $B$, so $C_1=AB_1$.
3. Each row in $C$ is equivalent to performing a multiplication of that row in $A$ times $B$, so $C_1=A_1B$.
4. $C$ is equal to the sum of the columns of $A$ times the rows of $B$, i.e. the first column of $A$ times the first row of $B$, plus the second column times the second row, and so on.
5. If we divide $A$ and $B$ up into blocks (giving us $A=\begin{bmatrix}A_1&A_2\\A_3&A_4\end{bmatrix}$ and $B=\begin{bmatrix}B_1&B_2\\B_3&B_4\end{bmatrix}$), then we can combine those "submatrices" to produce the overall result in the same manner as in method 1, so $C_1=A_1B_1+A_2B_3$.
# Inverses
A matrix can have an inverse $A^{-1}$ such that $A^{-1}A=I$ or $AA^{-1}=I$. For square matrices $A^{-1}A=AA^{-1}=I$, while rectangular matrices may have one or many left inverses or right inverses.

We can find an inverse:
$$
\begin{bmatrix}
1&3\\
2&7
\end{bmatrix}
\begin{bmatrix}
a&c\\
b&d
\end{bmatrix}
=
\begin{bmatrix}
1&0\\
0&1
\end{bmatrix}
$$
Using multiplication method 2 from above, we can produce the following:
$$
\begin{aligned}
\begin{bmatrix}
1&3\\
2&7
\end{bmatrix}
\begin{bmatrix}
a\\
b
\end{bmatrix}
&=
\begin{bmatrix}
1\\
0
\end{bmatrix}\\
\begin{bmatrix}
1&3\\
2&7
\end{bmatrix}
\begin{bmatrix}
c\\
d
\end{bmatrix}
&=
\begin{bmatrix}
0\\
1
\end{bmatrix}
\end{aligned}
$$
And now we can see that this is just two systems of linear equations, which can be solved using [[Lecture 2 - Elimination with Matrices#Gaussian elimination|Gaussian elimination]]. We can use a faster approach using **Gauss-Jordan elimination**, which allows for multiple solutions to be found at the same time by augmenting the matrix with both right hand sides:
$$
\begin{bmatrix}
1&3&|&1&0\\
2&7&|&0&1
\end{bmatrix}
$$
Now, we perform elimination, but instead of stopping once we're in upper triangular form we continue until the left is the identity matrix:
$$
\begin{aligned}
&\begin{bmatrix}
1&3&|&1&0\\
2&7&|&0&1
\end{bmatrix}\\
&\ \ \ \ \ \ \ \ \ \ \ \ \downarrow\\
&\begin{bmatrix}
1&3&|&1&0\\
0&1&|&-2&1
\end{bmatrix}\\
&\ \ \ \ \ \ \ \ \ \ \ \ \downarrow\\
&\begin{bmatrix}
1&0&|&7&-3\\
0&1&|&-2&1
\end{bmatrix}\\
\end{aligned}\\
$$
and will then find that the right hand side is the inverse, so
$$
\begin{bmatrix}
1&3\\
2&7
\end{bmatrix}^{-1}
=
\begin{bmatrix}
7&-3\\
-2&1
\end{bmatrix}
$$
This is the case as when we perform elimination on $\begin{bmatrix}A&I\end{bmatrix}$, we are building an elimination matrix $E$ (although we never explicitly worked out its values). This means that $EA=I$, which means that $E=A^{-1}$, and as we have $I$ along for the ride, $E\begin{bmatrix}A&I\end{bmatrix}=\begin{bmatrix}I&A^{-1}\end{bmatrix}$.
## Non-invertible matrices
Matrices do not always have inverses. A matrix will not have an inverse if there exists a non-zero vector $\mathbf{x}$ such that $A\mathbf{x}=\mathbf{0}$. E.g. for a matrix $\begin{bmatrix}1&3\\2&6\end{bmatrix}$ we can find a vector $\begin{bmatrix}3\\-1\end{bmatrix}$, and:
$$
\begin{bmatrix}
1&3\\
2&6\end{bmatrix}
\begin{bmatrix}
3\\
-1
\end{bmatrix}
=
\begin{bmatrix}
0\\
0
\end{bmatrix}
$$
so the matrix is uninvertible.

This is true as if $A\mathbf{x}=\mathbf{0}$, and if $A^{-1}$ does exist, then if we do
$$
A^{-1}A\mathbf{x}=\mathbf{0}
$$
we would find that $\textbf{x}=\textbf{0}=\begin{bmatrix}3\\-1\end{bmatrix}$, which is a contradiction.