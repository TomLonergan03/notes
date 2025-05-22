We will use this system of equations throughout the lecture:
$$
\begin{aligned}
x+2y+z&=2\\
3x+8y+z&=12\\
4y+z&=2
\end{aligned}
$$
Which gives us a matrix:
$$
A=\begin{bmatrix}
1&2&1\\
3&8&1\\
0&4&1
\end{bmatrix}
$$
and a vector:
$$
b=\begin{bmatrix}
2\\
12\\
2
\end{bmatrix}
$$
# Gaussian elimination
**Gaussian elimination** is a process for solving a system of linear equations. To perform it, we want to to eliminate variables from each equation by adding and subtracting multiples of equations.

Using our example, the first step will be to **augment** $A$ with $b$:, giving us:
$$
\begin{bmatrix}
1&2&1&2\\
3&8&1&12\\
0&4&1&2
\end{bmatrix}
$$
eliminate the $3x$ from the second equation using the first equation. The $x$ entry of the first equation is known as the **pivot**. We do this by multiplying all terms of the first equation by $3$ (so that we have $3x+...$) then subtracting that result ($3x+6y+3z=6$) from the second equation:
$$
\begin{bmatrix}
1&2&1&2\\
3&8&1&12\\
0&4&1&2
\end{bmatrix}
\rightarrow
\begin{bmatrix}
1&2&1&2\\
0&2&-2&6\\
0&4&1&2
\end{bmatrix}
$$
We now can try to eliminate the $x$ term from row 3, but as it is already zero we don't need to do anything.

We can then repeat the same process to eliminate the $4y$ from row 3 using row 2:
$$
\begin{bmatrix}
1&2&1&2\\
0&2&-2&6\\
0&4&1&2
\end{bmatrix}
\rightarrow
\begin{bmatrix}
1&2&1&2\\
0&2&-2&6\\
0&0&5&-10
\end{bmatrix}
$$
If we remove the column we took from $b$ we are left with the **upper triangular matrix**: ^bc2e13
$$
u=\begin{bmatrix}
1&2&1\\
0&2&-2\\
0&0&5
\end{bmatrix}
$$
And we can now use the resulting system to solve for $x,y,z$ (a process known as **back substitution**):
$$
\begin{aligned}
x+2y+z&=2\\
2y-2z&=6\\
5z&=-10
\\\\&\downarrow\\\\
x+2y+z&=2\\
2y-2z&=6\\
z&=-2
\\\\&\downarrow\\\\
x+2y+z&=2\\
2y&=2\\
z&=-2
\\\\&\downarrow\\\\
x+2y+z&=2\\
y&=1\\
z&=-2
\\\\&\downarrow\\\\
x&=2\\
y&=1\\
z&=-2
\end{aligned}
$$
## Failure cases
We have a couple of cases where this is less straightforward:
1. If a row has a zero in the pivot (e.g. $\begin{bmatrix}1&2&1\\0&0&-2\\0&4&1\end{bmatrix}$), but a lower row has a non-zero entry in the pivot column, we can exchange the rows and continue.
2. If a row has a zero in the pivot but we have no possible row exchanges, then the matrix is **uninvertable** (to be discussed further later) and there is no solution.
# As matrix operations
We want to know what operations we performed on the matrix during elimination. As we saw [[Lecture 1 - The geometry of linear equations|last time]], multiplying a matrix by a column vector gives us (for an example vector $A\cdot\begin{bmatrix}1\\2\\3\end{bmatrix}$) 1 times the first column of $A$, 2 times the second column of $A$, and 3 times the third. 

The equivalent is true for multiplying a row vector *by* a matrix (notice that this has the row vector on the left), so the vector $\begin{bmatrix}1&2&3\end{bmatrix}\cdot A$ will give us 1 times the first row of $A$, 2 times the second, and 3 times the third.

This is also true for multiplying a matrix by a matrix, so if we have a matrix multiplication we will get a linear combination of rows:
$$
\begin{bmatrix}
1&0&0\\
-3&1&0\\
0&0&1
\end{bmatrix}
\begin{bmatrix}
1&2&1\\
3&8&1\\
0&4&1
\end{bmatrix}
=
\begin{bmatrix}
1&2&1\\
0&2&-2\\
0&4&1
\end{bmatrix}
$$
This left matrix ($E_{21}$ for *elimination of row 2, column 1*) is the equivalent of the first operation we performed during elimination.

We can then make a matrix $E_{32}$:
$$
\begin{bmatrix}
1&0&0\\
0&1&0\\
0&-2&1
\end{bmatrix}
\begin{bmatrix}
1&2&1\\
0&2&-2\\
0&4&1
\end{bmatrix}
=
\begin{bmatrix}
1&2&1\\
0&2&-2\\
0&0&5
\end{bmatrix}
$$

With these two elimination matrices, we can produce a final matrix that describes the entire elimination process:
$$
\begin{aligned}
U&=E_{32\ }(E_{21\ }A)\\
&=(E_{32\ }E_{21\ })A\\
&=\left(\begin{bmatrix}
1&0&0\\
0&1&0\\
0&-2&1
\end{bmatrix}
\begin{bmatrix}
1&0&0\\
-3&1&0\\
0&0&1
\end{bmatrix}
\right)
A\\
\end{aligned}
$$
Giving us a single elimination matrix:
$$
E=\begin{bmatrix}
1&0&0\\
-3&1&0\\
6&-2&1
\end{bmatrix}
$$
# Identity matrices
When any matrix is multiplied with the **identity matrix**, no change occurs. Identity matrices only exist for square matrices, and consist of zeros with a line of ones down the diagonal, e.g. the 3x3 identity matrix is:
$$
\begin{bmatrix}
1&0&0\\
0&1&0\\
0&0&1\\
\end{bmatrix}
$$

# Permutation matrices
As an aside, if we have to do a row exchange, this is represented by a **permutation matrix**, e.g.
$$
\begin{bmatrix}
1&0&0\\
0&0&1\\
0&1&0
\end{bmatrix}
A
$$
This will swap rows 2 and 3 (think row 2 gets 1 times row 3, while row 3 gets one times row 2, or by performing the equivalent row exchange on an identity matrix).

Likewise, we can do column exchanges using a right multiplication (as left multiplications affect rows while right multiplications affect columns), e.g.
$$
A
\begin{bmatrix}
1&0&0\\
0&0&1\\
0&1&0
\end{bmatrix}
$$
This will swap columns 2 and 3 of $A$.

Permutation matrices are closed under multiplication, i.e. if we take any two permutation matrices and multiply them together, the result will simply be another permutation matrix.