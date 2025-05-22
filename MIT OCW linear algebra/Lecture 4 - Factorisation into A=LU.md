# Combining inverses
If we have [[Lecture 3 - Multiplication and Inverse Matrices#Inverses|invertible]] matrices $A$ and $B$, and we multiply them together, we can find the inverse of $AB$, $(AB)^{-1}$, by multiplying the inverses in the reverse order, so $(AB)^{-1}=B^{-1}A^{-1}$.
# Transposition
A matrix $A$ can be transposed to produce $A^T$ by swapping its rows and columns. For a $n\times n$ square matrix this produces another $n\times n$ square matrix, while a $n\times m$ matrix will produce a $m\times n$ matrix.

E.g.
$$
\begin{bmatrix}
a&b&c\\
d&e&f\\
g&h&i
\end{bmatrix}^T
=
\begin{bmatrix}
a&d&g\\
b&e&h\\
c&f&i
\end{bmatrix}
$$
## Inverse of transpositions
If we have a matrix $A$ with an inverse $A^{-1}$, the inverse of $A^T$ will be $(A^{-1})^T$.
# Factorisation
If we have a 2x2 matrix $A=\begin{bmatrix}2&1\\8&7\end{bmatrix}$ then we can perform [[Lecture 2 - Elimination with Matrices#Gaussian elimination|elimination]] to get $E_{21}$ and $U$:
$$
\begin{aligned}
E_{21}A&=U\\
\begin{bmatrix}
1&0\\
-4&1
\end{bmatrix}
\begin{bmatrix}
2&1\\
8&7
\end{bmatrix}
&=\begin{bmatrix}
2&1\\
0&3
\end{bmatrix}
\end{aligned}
$$
We then want to produce an $L$ such that $A=LU$. As $E_{21}A=U$, $L=E_{21}^{-1}$, so:
$$
\begin{aligned}
A&=LU\\
A&=E_{21}^{-1}U\\
\begin{bmatrix}
2&1\\
8&7
\end{bmatrix}
&=\begin{bmatrix}
1&0\\
4&1
\end{bmatrix}
\begin{bmatrix}
2&1\\
0&3
\end{bmatrix}\\
L&=\begin{bmatrix}
1&0\\
4&1
\end{bmatrix}
\end{aligned}
$$
$L$ is the **lower triangular matrix**, and where the [[Lecture 2 - Elimination with Matrices#^bc2e13|upper triangular]] has the pivots on the diagonal, the lower triangular has ones on the diagonal.

We can go one step further and separate out the pivots entirely by dividing each row by the pivot value, to get:
$$
\begin{bmatrix}
2&1\\
8&7
\end{bmatrix}
=\begin{bmatrix}
1&0\\
4&1
\end{bmatrix}
\begin{bmatrix}
2&0\\
0&3
\end{bmatrix}
\begin{bmatrix}
1&\frac{1}{2}\\
0&1
\end{bmatrix}
$$

3x3 matrices are a little more complex, as we have more elimination steps:
$$
E_{32}E_{31}E_{21}A=U
$$
so we then use the rule for combining inverses to get:
$$
A=E_{21}^{-1}E_{31}^{-1}E_{32}^{-1}U
$$
so $L=E_{21}^{-1}E_{31}^{-1}E_{32}^{-1}$.

Larger matrices will be factorised similarly, and in all these cases we are assuming no [[Lecture 2 - Elimination with Matrices#Permutation matrices|permutations]] are needed for elimination.