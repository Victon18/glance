# Linear-Algebra
- Study of lines in high-dimensional space
- Helps in solving unknown within the system of linear equations.

# Vector
---
- defines by its magnitude and its direction
- It has a initial point and a terminal point
- $\begin{bmatrix}a\\b\end{bmatrix}$ is vector's standard position.
- The positional vector has a initial position (0, 0) and terminal position (a, b) which is equal to $[a-0, b-0]$

Magnitude of vector
-----
- denoted by $|V|$ and can be found by using Pythagoras theorem of x,y of the positional vector

Addition of vector
-----
$$\LARGE
\begin{align}
\vec{a} &=  \begin{bmatrix}2\\3\end{bmatrix};
\vec{b} =  \begin{bmatrix}4\\5\end{bmatrix} \\
\vec{a}+\vec{b} &= \begin{bmatrix}6\\8\end{bmatrix}
\end{align}
$$

scalar-vector product
-----
Scalar = it's just an integer
Scale your vector
$$\LARGE
\begin{align}
c\cdot\vec{v} &=  \begin{bmatrix}cv_{1}\\cv_{2}\end{bmatrix}\\
2\cdot \begin{bmatrix}2\\3\end{bmatrix} &=  \begin{bmatrix}4\\6\end{bmatrix}
\end{align}
$$

vector-vector product
-----
$$\LARGE
\begin{align}
\vec{a} &=  \begin{bmatrix}2\\3\end{bmatrix};
\vec{b} =  \begin{bmatrix}4\\5\end{bmatrix} \\
\vec{a}\times\vec{b} &= \begin{bmatrix}8\\15\end{bmatrix}
\end{align}
$$

Transpose of vector
---
row becomes column and vice versa
$$\LARGE
\vec{x} =  \begin{bmatrix}x1\\x2\\\dots\\xm\end{bmatrix}^{T}  =  \begin{bmatrix}x1,x2,\dots,xm\end{bmatrix}
$$

Multiplying two vectors
----
- Dot Product
- Cross Product
- Linear Combination

Linear dependence and independence
----
- A set of vector is said to be linear independent if no vector can be represented as linear combination of the remaining vectors.
- A set of vector is said to be linear dependent if a vector can be represented as linear combination.

Span
---
- Set of all possible linear combination of a given group of vector is called as the span of vectors
- eg: $\begin{bmatrix}-5\\2\end{bmatrix} = \begin{bmatrix}-5\\0 \end{bmatrix};\begin{bmatrix}0\\2 \end{bmatrix}$

Norm
----
- **L2 Norm**: Euclidian Norm, calculates the disance form the origin
$\LARGE ||x||_{2} = \sqrt{\overset{n}{\underset{r = 1}{\Sigma}}|x_{r}|}$
- **L1 Norm**: Manhattan distance, calculates the sum of absolute values
$\LARGE |x|_{1} =\overset{n}{\underset{r = 1}{\Sigma}}|x_{r}|$
- **Max Norm**: distance by taking out the max element
$\LARGE ||x||_{\infty} = max_{i}|x_{i}|$

eg: $\begin{bmatrix}2\\5\\9\end{bmatrix} = 9$

Othogonal Vector
---
Two vectors if they are perpendicular to each other they are orthogonal vector
$a \cdot b = 0$ ; cross product

# Matrices
- rectangular array or tabular data comprised of rows and columns can be represented in matrices

Scalar-Matrix product
----
$$
2\cdot\begin{bmatrix}3&2\\2&4\end{bmatrix}=\begin{bmatrix}6&4\\4&8\end{bmatrix}
$$

Matrix Addition
----
A+B = C
$$\begin{bmatrix}2&3&2\\2&4&3\end{bmatrix}+\begin{bmatrix}2&3&2\\2&4&3\end{bmatrix}=\begin{bmatrix}4&6&4\\4&8&4\end{bmatrix}$$

Properties
---
- Commutative Property:
---
A+B = B+A
- Assosiative Property
---
A+(B+C)=(A+B)+C

- Dimension should be same

### Operations on matrices
Matrix-Matix Multiplication
---
- number of columns of the first matrix must be equal to the number of rows of of the second matrix

$$
\begin{align}
\begin{bmatrix}
         a_{11} & a_{12} & \cdots & a_{1n}\\
         a_{21} & a_{22} & \cdots & a_{2n}\\
         \vdots & \vdots & \ddots & \vdots\\
         a_{m1} & a_{m2} & \cdots & a_{mn}
     \end{bmatrix}
     \times
     \begin{bmatrix}
         b_{11} & b_{12} & \cdots & b_{1p}\\
         b_{21} & b_{22} & \cdots & b_{2p}\\
         \vdots & \vdots & \ddots & \vdots\\
         b_{n1} & b_{n2} & \cdots & b_{np}
     \end{bmatrix}
      =
     \begin{bmatrix}
         c_{11} & c_{12} & \cdots & c_{1p}\\
         c_{21} & c_{22} & \cdots & c_{2p}\\
         \vdots & \vdots & \ddots & \vdots\\
         c_{m1} & c_{m2} & \cdots & c_{mp}
     \end{bmatrix}\\ \\
     C=
     \begin{bmatrix}
         a_{11}+b_{11}+\cdots+a_{1n}b_{n1} & a_{12}+b_{12}+\cdots+a_{1n}b_{n2} & \cdots & a_{11}+b_{1p}+\cdots+a_{1n}b_{1np}\\
         a_{21}+b_{21}+\cdots+a_{2n}b_{n1} &a_{21}+b_{12}+\cdots+a_{2n}b_{n2} & \cdots & a_{21}+b_{1p}+\cdots+a_{2n}b_{np}\\
         \vdots & \vdots & \ddots & \vdots\\
         a_{m1}+b_{11}+\cdots+a_{mn}b_{n1} & a_{m1}+b_{12}+\cdots+a_{mn}b_{n2} & \cdots & a_{m1}+b_{1p}+\cdots+a_{mn}b_{np}
     \end{bmatrix}
\end{align}
$$
$$\LARGE
c_{ij}= a_{i1} b_{1j} + a_{i2} b_{2j} +\cdots+ a_{in} + b_{nj} = \sum_{k=1}^n a_{ik}b_{kj}
$$

Matix - vector product
----
$$
A=\begin{bmatrix}2&6\\3&4\\2&2\end{bmatrix}\cdot
v=\begin{bmatrix}2\\3\end{bmatrix}
s=\begin{bmatrix}4+18\\6+12\\4+6\end{bmatrix}
=\begin{bmatrix}22\\18\\10\end{bmatrix}
$$

Transpose of the matrix
---
- it flips it over the daigonal
- rows become column and column become rows

$$
\begin{align}
A&=\begin{bmatrix}1&2\\3&4\end{bmatrix}\\
A^{T}&=\begin{bmatrix}2&2\\2&4\end{bmatrix}
\end{align}
$$

### Types of matrix

Symmetric matrix
---
If the original matrix is equal to its transpose

$$
\begin{align}
A&=\begin{bmatrix}0&4&7\\4&0&3\\7&3&0\end{bmatrix}\\
A^{T}&=\begin{bmatrix}0&4&7\\4&0&3\\7&3&0\end{bmatrix}
\end{align}
$$


Skew-Symmetric matrix
---
If the original matrix is equal to its negative-transpose

$$
\begin{align}
A&=\begin{bmatrix}0&4&7\\-4&0&-3\\-7&3&0\end{bmatrix}\\
A^{T}&=\begin{bmatrix}0&-4&-7\\4&0&3\\7&-3&0\end{bmatrix}
\end{align}
$$



Identity matrix
---
all diagonal elements are 1 and remaining are 0

$$
A=\begin{bmatrix}1&0&0\\0&1&0\\0&0&1\end{bmatrix}\\
$$

Determinant of a Matrix
----
The determinant is a scalar value that is a function of the entire series of a matrix. It gives the area under the shape
It is denoted by |A|.

$$\large|A|=\begin{bmatrix}a&b\\c&d\end{bmatrix}=ad-bc$$

Similarly,
$$\large
\begin{align}
|A|&=\begin{bmatrix}a&b&c\\d&e&f\\g&h&i\end{bmatrix}=a\begin{bmatrix}e&f\\h&i\end{bmatrix}-
b\begin{bmatrix}d&f\\g&i\end{bmatrix}+
c\begin{bmatrix}d&e\\g&h\end{bmatrix}\\
&=aei+bfg+cdh-ceg-bdi-afh
\end{align}
$$

Cofactor, Minor of matrix
---
- Minor is group of two rows or columns formed (square matrix) from the original matrix by hiding the rows and column of the element we want to find about.
- Its required for calculating the matrix cofactor.

eg:

$$\Large
\begin{align}
\begin{bmatrix}1&4&7\\3&0&5\\-1&9&11\end{bmatrix}\\
Minor(M_{2,3})&=det\begin{bmatrix}1&4\\-1&9\end{bmatrix}=9-(-4)=13\\
Cofactor(C_{2,3})&=(-1^{2+3})\times M_{2,3}=-13\\
det(A)&=\overset{n}{\underset{i=1}{\Sigma}}a_{ij}(-1)^{i+1}M_{ij}
\end{align}
$$

Adjugate of matrix
----
The adjugate of square matrix is just the transpose of it's cofactor matrix.

Inverse Matrix
----
1. Calculate the minors of all elements of matrix A
2. Compute the cofactor of all elements of matrix A
3. Take out the adjoint of A by taking out transpose of matrix A
4. Multiply the adjoint of A by reciprocal of det(A)


