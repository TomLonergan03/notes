The fundamental problem of linear algebra is to solve systems of linear equations. We will start with the case where we have $n$ linear equations, and $n$ unknowns.

If we have a system of linear equations:
$$
\begin{aligned}
2x-y&=0\\
-x+2y&=3
\end{aligned}
$$
We can convert this system into a number of matrices and vectors:
$$
\begin{bmatrix}
2&-1\\
-1&2
\end{bmatrix}
\begin{bmatrix}
x\\
y
\end{bmatrix}
=
\begin{bmatrix}
0\\
3
\end{bmatrix}
$$
We will call these matrices $A$, $\mathbf{x}$, and $b$ respectively.
# Row view
We can look at the system row-by-row, with each equation separately. As we have two unknowns, we can plot each of these equations as 2D lines, where each line shows all the values for $x$ and $y$ which satisfy that specific equation:
```desmos-graph
left=-5; right=5; top=5; bottom=-5;
---
2x-y=0
-x+2y=3
```

Here, we can see the point $(0,0)$ (the **origin**) satisfies the first equation (the blue line) as if $x=0,y=0$ then $2x-y=2\cdot0-0=0$, and the point $(-1,1)$ satisfies the second equation (the green line). We can also see there is only 1 point that satisfies both equations, $(1,2)$.
# Column view
Instead of focusing on each individual row, we can instead look at it as columns, and create this equation:
$$
x\begin{bmatrix}2\\-1\end{bmatrix}+y\begin{bmatrix}-1\\2\end{bmatrix}=\begin{bmatrix}0\\3\end{bmatrix}
$$
Now, we are asking for a **linear combination** of the columns, such that we take some quantity of the first column and some quantity of the second, and produce the resulting column.

We can then visualise these vectors:
```desmos-graph
left=-5; right=5; top=5; bottom=-5;
---
(0,0)|blue
(2,-1)|label:Vector x, (2,-1)|blue
y=-0.5x|0<x<2|blue
(0,0)|red
(-1,2)|label:Vector y, (-1,2)|red
y=-2x|-1<x<0|red
(0,0)|purple
(0,3)|purple|label:Target vector (0,3)
x=0|0<y<3|purple
```

And now, we create linear combinations of these vectors by placing them nose to tail, e.g. to use the solution to the system of $x=1,y=2$ we produce:
```desmos-graph
left=-5; right=5; top=5; bottom=-5;
---
(0,0)|blue
(2,-1)|label:Vector x, (2,-1)|blue
y=-0.5x|0<x<2|blue|dashed
(2,-1)|red
(1,1)|label:Vector y, (1,1)|red
(1,1)|red
(0,3)|label:Vector y, (0,3)|red
y=-2x+3|0<x<2|red|dashed
(0,0)|purple
(0,3)|purple|label:Result vector (0,3)
x=0|0<y<3|purple
```
We can see that if we take one $x$ vector, then 2 $y$ vectors, we end up at the same place as our target vector.
# Matrix view
If we have a larger value of $n$ it becomes difficult to plot the various equations to find a solution graphically. If we create a new system:
$$
\begin{matrix}
2x&-y& &=0\\
-x&+2y&-z&=-1\\
&-3y&+4z&=4
\end{matrix}
$$
When we plot a system of 2 equations, we get a 2 dimensional space with lines describing all the points that solve each equation. In a system of 3 equations, we will have a 3 dimensional space with planes describing the points that solve each equation. The intersection of any two (non-parallel) planes in that space will be a line, then the third plane with that line will be a single point, the solution to the equation. This is already difficult to solve graphically, and should we have higher dimensional systems it becomes practically impossible to solve graphically, so we will abandon the row method at this point.

We can put the system into matrix form:
$$
A=\begin{bmatrix}
2&-1&0\\
-1&2&-1\\
0&-3&4
\end{bmatrix},\ \ \ b=\begin{bmatrix}
0\\-1\\4
\end{bmatrix}
$$
Then convert it to a column view:
$$
x\begin{bmatrix}2\\-1\\0\end{bmatrix}+y\begin{bmatrix}-1\\2\\-3\end{bmatrix}+z\begin{bmatrix}0\\-1\\4\end{bmatrix}=\begin{bmatrix}0\\-1\\4\end{bmatrix}
$$
Again, this is hard to solve graphically, but we can see that our column for $z$ is equal to the resultant vector, so we have the solution $x=0,\ y=0,\ z=1$.
# Unsolvable systems
An important question for linear algebra is "can I solve $A\mathbf{x}=b$ for every value of $b$?" Or in algebraic terms, do the linear combinations of the columns fill 3-D space?

This depends on the value of $A$. If we have a 3 dimensional system, and all column vectors are in the same plane, then there is no way to "break out" of that plane, as any combination of the columns will also lie in the same plane. Generalising this idea to any dimension, if we have $n$ equations and $n$ unknowns, if all the columns are **independent** (i.e each column cannot be created using a linear combination of other columns) then the system will be solvable.
# Multiplying matrices and vectors
Given a system of equations in matrix form $A\mathbf{x}=b$, an obvious question is "how do we multiply $A$ and $\mathbf{x}$?"

We will use these values:
$$
\begin{bmatrix}
2&5\\
1&3
\end{bmatrix}
\begin{bmatrix}
1\\
2
\end{bmatrix}
$$
One way to solve this is by columns, so the above equation can be viewed as "take 1 of the first column, and 2 of the second column, and add them up".
$$
\begin{bmatrix}
2&5\\
1&3
\end{bmatrix}
\begin{bmatrix}
1\\
2
\end{bmatrix}
=1
\begin{bmatrix}
2\\
1
\end{bmatrix}
+2
\begin{bmatrix}
5\\
3
\end{bmatrix}
=
\begin{bmatrix}
2+2\cdot5\\
1+2\cdot3
\end{bmatrix}
=
\begin{bmatrix}
12\\
7
\end{bmatrix}
$$

Essentially, **$A\mathbf{x}$ is a linear combination of the columns of $A$**.