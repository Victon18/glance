
single variable calculus
----
- It is a relationship between two things, in which one depends on other
- Its like input given to a function and output given by the same function
$$\LARGE
\begin{align}
f(x) &= x^{2} \\
f(x_{1},x_{2},x_{3}) &= 2\times x_{1},2\times x_{2},2\times x_{3} \\
f(1,2,3) &= 2,4,6
\end{align}
$$
- **Domain** = set of all inputs in a function; "Independent variables"
- **Range** = set of all output in a function; "Dependent variables"

composite functions
-----

$$\large
\begin{align}
f(x) &= x^{2} \\
g(x) &= 5x-8 \\
f(g(3)) &= ?\\
g(3) &= 5\times 3 - 8 = 7 \\
f(7) &= (7)^{2} = 49
\end{align}
$$

# Slope

$$\LARGE
Slope =\dfrac{rise}{run} =\dfrac{y_{2}-y_{1}}{x_{2}-x_{1}}
$$

Slope-intercept
----
$$\LARGE
y = slope\times x+y-intercept
y = mx+b(for straight line)
$$
y-intersept ---> point where equation's line intersects y-axis
x-intersept ---> point where equation's line intersects x-axis

Parabolic graph
----
- $\LARGE f(x) = x^{2}$
- Function is symmetric with respect to y-axis
- It's a even function (power is even
- Differentiable and Continuous function

```desmos-graph
top=10; left=-10; right = 10; bottom=-2
---
y=x^{2}
```

Absolute graph
----
$\LARGE f(x) = |x|$
- Function is symmetric with respect to y-axis
- Non-differentiable and Continuous function

```desmos-graph
top=10; left=-10; right = 10; bottom=-2
---
y=\abs(x)
```
# Trigonometry

| $\theta$      | $0\degree$ | $30\degree$          | $45\degree$          | $60\degree$          | $90\degree$      | $180\degree$ | $270\degree$     | $360\degree$ |
| ------------- | ---------- | -------------------- | -------------------- | -------------------- | ---------------- | ------------ | ---------------- | ------------ |
| -             | 0 rad      | $\frac{\pi}{6}$      | $\frac{\pi}{4}$      | $\frac{\pi}{3}$      | -$\frac{\pi}{2}$ | $\pi$        | $\frac{3\pi}{2}$ | $2\pi$       |
| $sin\theta$   | 0          | $\frac{1}{2}$        | $\frac{\sqrt{2}}{2}$ | $\frac{\sqrt{3}}{2}$ | 1                | 0            | -1               | 0            |
| $cos\theta$   | 1          | $\frac{\sqrt{3}}{2}$ | $\frac{\sqrt{2}}{2}$ | $\frac{1}{2}$        | 0                | -1           | 0                | 1            |
| $tan\theta$   | 0          | $\frac{1}{\sqrt{3}}$ | 1                    | $\sqrt{3}$           | -                | 0            | -                | 0            |
| $cot\theta$   | -          | $\sqrt{3}$           | 1                    | $\frac{1}{\sqrt{3}}$ | 0                | -            | 0                | -            |
| $sec\theta$   | 1          | $\frac{2}{\sqrt{3}}$ | $\sqrt{2}$           | 2                    | -                | -1           | -                | 1            |
| $cosec\theta$ | -          | 2                    | $\sqrt{2}$           | $\frac{2}{\sqrt{3}}$ |                  | -            | -1               | -            |

- Right angle triangle
---
Hypotenuse --> Longest side
Adjacent --> Side adjacent to the angle
Perpendicular --> side opposite to the angle


- Sine
----
$\Large\frac{opposite}{hypotenuse}$

- Cosine
----
$\Large\frac{adjacent}{hypotenuse}$

- Tangent
----
$\Large\frac{opposite}{adjacent}$

- Secant
----
$\Large\frac{1}{Cosine}$

$\Large\frac{hypotenuse}{adjacent}$

- Cosecant
----
$\Large\frac{1}{Sine}$

$\Large\frac{hypotenuse}{perpendicular}$

- Cotangent
----
$\Large\frac{1}{Tangent}$

$\large\frac{adjacent}{opposite}$

Unit Circle
---
![[circle.jpg]]

# Limits
- Limits describe the behavior of a function at a particular point, rather than the value of the function at that point.
- Limit of a function of some x-values "c" to  the height of the function gets closer and closer to c from the left and right side

eg:
$$\large
f(x)=x^{2};y(x)\begin{cases}x^{2};x\neq2\\1;x=2\end{cases}
$$

```desmos-graph
top=10; left=-10; right = 10; bottom=-2
---
f(x)=\left\{1.9<x<2.1:2,x^{2}\right\}
```

right:

| x        | 1.9  | 1.99   | 1.999    |
| -------- | ---- | ------ | -------- |
| **g(x)** | 3.61 | 3.9601 | 3.996001 |

It is getting closer to 4.

$\Large\underset{x=2}{\lim}g(x)=4$

left:

| x        | 2.1 | 2.01   | 2.001    |
| -------- | --- | ------ | -------- |
| **g(x)** | 4.1 | 4.0401 | 4.004001 |

It is getting closer to 4

$\Large\underset{x=2}{\lim}g(x)=4$

Since both tend to 4 this is the answer

Continuous Function
---
function which has no hole or break

Piece-wise Function (non-continuous )
---
function which has hole or break

Limit of continuous function
----
For a continuous function the limit is $-\infty \to \infty$

```desmos-graph
f(x)=x^3
```


One side limit
---
Some functions have one side limit

No limit
---
$$\Large
\underset{x\to c^{-}}{\lim}\neq\underset{x\to c^{+}}{\lim}
$$

eg:

```desmos-graph
top=10; left=-10; right = 10; bottom=-2
---
f(x)=\left\{-0.1<x:x^{2},\cos(x)\right\}
```

right: $\large\underset{x=0}{\lim}g(x)=0$
left: $\large\underset{x=0}{\lim}g(x)=1$

Thus limit does not exist

Formulas
----
1. Check continuous by substitution
---
$$
\large\underset{x\to3}{\lim}x^{2}-10=3^{2}-10=9-10=-1
$$

2. Hit and trial
----
$$
\large\underset{x\to5}{\lim}\frac{x^{2}-25}{x-5}=\frac{5^{2}-25}{5-5}=\frac{0}{0}=undefined
$$

hence for this we will use hit and trial

right:

| x     | 4.9 | 4.99 | 4.999 |
| ----- | --- | ---- | ----- |
| **y** | 9.9 | 9.99 | 9.999 |

It is getting closer to 10.

$\Large\underset{x=2}{\lim}g(x)=4$

left:

| x     | 5.1  | 5.01  | 5.001  |
| ----- | ---- | ----- | ------ |
| **y** | 10.1 | 10.01 | 10.001 |

It is getting closer to 10

thus answer is 10

3. Factorization
----
Fractorization

$$\large
\begin{align}
\underset{x\to5}{\lim}\frac{x^{2}-25}{x-5}&=\frac{x^{2}-5^{2}}{x-5}\\
&=\frac{\cancel{(x-5)}(x+5)}{\cancel{x-5}}=x+5\\
&=5+5=10
\end{align}
$$

Rationalization
$$\large
\begin{align}
\underset{x\to4}{\lim}\frac{\sqrt{x}-2}{x-4}=\frac{\sqrt{x}-2}{x-4}\times\frac{\sqrt{x}+2}{\sqrt{x}+2}\\
&=\frac{(\sqrt{x})^{2}-2^{2}}{(x-4)(\sqrt{x}+2)}\\
&=\frac{\cancel{x-4}}{\cancel{(x-4)}(\sqrt{x}+2)}=\frac{1}{\sqrt{x}+2}\\
&=\frac{1}{\sqrt{4}+2}= \frac{1}{2+2}=\frac{1}{4}
\end{align}
$$

- Sandwich theorem
---
eg:
$$\large
\begin{align}
f(x)=\underset{x=0}{\lim}\sin{x}=0\\
g(x)=\underset{x=0}{\lim}\tan{x}=0\\
h(x)=\underset{x=0}{\lim}|x|=0\\
f(x)=g(x)=h(x)
\end{align}
$$

```desmos-graph
f\left(x\right)=\tan\left(x\right)
f\left(x\right)=\sin\left(x\right)
f\left(x\right)=x
```

# continuity
to check is a function is countinous at a perticular value of limit

# differentiation
A derivative is a measure of how much something changes with respect to something else

Notations
$$\large
\frac{df(x)}{dx}=\frac{dy}{dx}=f'(x)=y'
$$

differentiation quoteint
---

![[diff.png]]

- limiting the points of graph to meet each other at the same point
- converting secant to tangent

$$\LARGE
\frac{df(x)}{dx}=\underset{h\to0}{\lim}\frac{f(x+h)-f(x)}{h}
$$

eg: $\large f(x)=\frac{1}{4}x^{2}$

$$\large
\begin{align}
f(x)&=\frac{1}{4}x^{2}=\underset{h\to0}{\lim}\frac{\frac{1}{4}(x+h)^{2}-\frac{1}{4}x^{2}}{h}\\
&=\underset{h\to0}{\lim}\frac{\frac{1}{4}(x^{2}+2xh+h^{2})-\frac{1}{4}x^{2}}{h}\\
&=\underset{h\to0}{\lim}\frac{\cancel{\frac{1}{4}x^{2}}+\frac{2xh}{4}+\frac{h^{2}}{4}- \cancel{\frac{1}{4}x^{2}}}{h}\\
&=\underset{h\to0}{\lim}\frac{\frac{2xh}{4}+\frac{h^{2}}{4}}{h}\\
&=\underset{h\to0}{\lim}\frac{2xh+h^{2}}{\frac{4}{h}}\\
&=\underset{h\to0}{\lim}\frac{\cancel{h}(2x+h)}{\frac{4}{\cancel{h}}}\\
&=\underset{h\to0}{\lim}\frac{2x+ha}{4}\\
&=\frac{2x+0}{4}\\
&=\frac{\cancel{2}x}{\cancel{4}}\\
&=\frac{x}{2}\\
\end{align}
$$

Rules
----
1. The constant rule
---
differentiation of a constant is 0:

$$\LARGE
\frac{df(c)}{dx}=0
$$

2. Power rule
---
differentiation of exponetial function is:

$$\LARGE
\frac{df(x^{n})}{dx}=nx^{n-1}
$$

3. The constant multiple rule
----
For a function of x with coefficient and exponential power the differentiation is product of coefficient and exponential of x

$$\LARGE
\frac{df(cx^{n})}{dx}=c\times \frac{x^{n}}{dx}=c\times nx^{n-1}
$$

4. The sum rule
----
for multiple funcitons with addition in between calculate each one separately and add if possible.

$$\LARGE
\begin{align}
f(x)&=x^6+x^5+x^4+x^3+x^2+x+10\\
&=6x^{5}+5x^{4}+4x^{3}+3x^{2}+2x+1+0\\
&=6x^{5}+5x^{4}+4x^{3}+3x^{2}+2x+1
\end{align}
$$

Differentiation of Trignometric function
---
$$\LARGE
\begin{align}
\frac{d\sin x}{dx}=\cos x\\
\frac{d\cos x}{dx}=-\sin x\\
\frac{d\tan x}{dx}=\sec^{2} x\\
\frac{d\cot x}{dx}=-\csc^{2} x\\
\frac{d\sec x}{dx}=\sec x\cdot \tan x\\
\frac{d\csc x}{dx}=-\csc x\cdot \cot x\\
\end{align}
$$

Differentiation of exponential function
---
differentiation of exponential  function itself only:

$$\LARGE
\frac{df(e^{x})}{dx}=e^{x}
$$

Differentiation of logrithmic function
---
$\LARGE ln(x)=\log_{e}x$
$$\LARGE
\begin{align}
\frac{d[ln(x)]}{dx}&=\frac{1}{x}\\
\frac{d[log_{10}(x)]}{dx}&=\frac{\frac{1}{x}}{xln(10)}\\
\frac{d[log_{2}(x)]}{dx}&=\frac{\frac{1}{x}}{xln(2)}\\
\end{align}
$$

Power Rule
---
$$\LARGE
\begin{align}
\frac{d[f(x)\cdot g(x)]}{dx} = \frac{df(x)}{dx}\cdot g(x)+f(x)\cdot\frac{dg(x)}{dx}
\end{align}
$$

Quotient Rule
---
$$\LARGE
\begin{align}
\frac{d[\frac{f(x)}{g(x)}]}{dx} =\frac{g(x)\cdot\frac{df(x)}{dx}-f(x)\cdot\frac{dg(x)}{dx}}{(g(x))^{2}}
\end{align}
$$

Chain rule of differentiation
-----
Diffentiate from outside function and move towards inside

$$\LARGE
f(g(x))=f(x).g(x)
$$

eg:
$$\large
\begin{align}
\frac{dy}{dx}&=\sin(x^{2}-3x)\\
&=\cos(x^{2}-3x)\cdot(2x-3)
\end{align}
$$
