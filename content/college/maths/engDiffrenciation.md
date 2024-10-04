# calculation of nth order derivative
1.$\large x^{m}$.
$$\large
\frac{d^{m}}{dx^{m}}(x^{m}) = m!
$$
2. $\large (ax+b)^{m}$,where n<m.
$$\large
y_{n}=m(m-1)(m-2)(m-3)\dots(m-n+1)(ax+b)^{m-n}\cdot a^{n}
$$
3. $\large \frac{1}{(ax+b)^{m}}[x\neq-\frac{b}{a}]$.
$$\large
y_{n}=(-1)^{n}\frac{(m+n-1)!}{(m-1)!}\frac{a^n}{(ax+b)^{m+n}}
$$
4. $\large \log(ax+b)$.
$$\large
y_{n}=\frac{(-1)^{n-1}(n-1)!a^{n}}{(ax+b)^{n}}
$$
5. $\large a^{mx}$
$$
y_{n}=m^{n}\cdot a^{mx}(\log a)^{n}
$$

6. $\large e^{mx}$

$$
y_{n}=m^{n}\cdot e^{mx}
$$
6. $\large \sin(ax+b)$.
$$\large
y_{n} = a^{n}\sin[ax+b+n\frac{\pi}{2}]
$$
7. $\large \cos(ax+b)$.
$$\large
y_{n} = a^{n}\cos[ax+b+n\frac{\pi}{2}]
$$
8. the nth differential co-efficient of $\large e^{ax}\sin(bx+C)$
$\large r = \sqrt{a^{2}+b^{2}};\phi=tan^{-1}\frac{b}{a}$
$$\large
y_{n} = r^{n}e^{ax}\cdot\sin[bx+c+n\cdot\phi]
$$

9. the nth differential co-efficient of $\large e^{ax}\cos(bx+C)$
$\large r = \sqrt{a^{2}+b^{2}};\phi=tan^{-1}\frac{b}{a}$
$$\large
y_{n} = r^{n}e^{ax}\cdot\cos[bx+c+n\cdot\phi]
$$
# partial derivative
### first order partial derivative
function with respect to x treating y as constant
$$\large
\frac{\delta z}{\delta x} = \lim_{h\to 0}\frac{f(x+h,y)-f(x,y)}{h}
$$
similarly , derivative of z, with respect to y treating x as a constant

$$\large
\frac{\delta z}{\delta y} = \lim_{k\to 0}\frac{f(x,y+k)-f(x,y)}{k}
$$
### ordinary derivative
if z is function of 2 or more independent variables, then the partial derivative of z w.r.t anyone of the independent variables is ordinary derivative of z w.r.t that variables, treating all other variables as constant.
### higher order derivative

1. $\large f_{xx} = \frac{\delta}{\delta x}(\frac{\delta z}{\delta x}) = \frac{\delta^{2} z}{\delta x^{2}}$
2. . $\large f_{yy} = \frac{\delta}{\delta y}(\frac{\delta z}{\delta y}) = \frac{\delta^{2} z}{\delta y^{2}}$
3. . $\large f_{xy} = \frac{\delta}{\delta x}(\frac{\delta z}{\delta y}) = \frac{\delta^{2} z}{\delta x \delta y}$
4. . $\large f_{yx} = \frac{\delta}{\delta y}(\frac{\delta z}{\delta x}) = \frac{\delta^{2} z}{\delta y \delta x}$
In general
$$\large
\frac{\delta^{2}z}{\delta x \delta y} = \frac{\delta^{2}z}{\delta y \delta x}
$$
# homogeneous functions
test for homogeneous functions is
$$\large
\begin{align}
f(x,y);x\to xt;y\to yt\\
f(tx,ty) = t^{n}f(x,y)
\end{align}
$$
here n is the degree of the function

# euler's theorem
### homogeneous
u is homogeneous function of degree n
1.  first derivative
$$\large
x\frac{\delta u}{\delta x}+y\frac{\delta u}{\delta y} = nu
$$
---
2. second derivative
$$\large
x^{2}\frac{\delta^{2}u}{\delta x^{2}}+y^{2}\frac{\delta^{2}u}{\delta y^{2}}+2xy\frac{\delta^{2}u}{\delta x\delta y} = n(n-1)u
$$

### non-homogeneous
u is the function of non-homogeneous function
F(u) is the non-homogeneous part of the function
1. first derivative
$$\large
\begin{align}
x\frac{\delta F(u)}{\delta x}+y\frac{\delta F(u)}{\delta y}=nF(u)\\
x\frac{\delta u}{\delta x}+y\frac{\delta u}{\delta y}=n\frac{F(u)}{F'(u)}
\end{align}
$$
---
3. second derivative
$\phi(u)=n\frac{F(u)}{F'(u)}$
$$\large
\begin{align}
x^{2}\frac{\delta^{2}u}{\delta x^{2}}+y^{2}\frac{\delta^{2}u}{\delta y^{2}}+2xy\frac{\delta^{2}u}{\delta x\delta y} = \phi(u)(\phi'(u)-1)
\end{align}
$$

# composite function
## differentiation of composite functions
1. single variable
if u is composite function of t, defined by relations $u=f(x,y);x=\phi(t),y=\psi(t)$
$$\large
\frac{du}{dt}=\frac{\delta u}{\delta x}\cdot\frac{dx}{dt}+\frac{\delta u}{\delta y}\cdot\frac{dy}{dt}
$$
---
2. two variables


# taylor series
1. let f(x+h) be a function of h (x being independent of h)
$$\large
f(x+h)=f(x)+hf'(x)+\frac{h^{2}}{2!}f''(x)+\frac{h^{3}}{3!}f'''(x)+\dots+\frac{h^{n}}{n!}f^{n}(x)
$$
---
2. function of two variables
$$\large
\begin{align}
f(x+h,y+k)=f(x,y)+(hf_{x}+kf_{y})+\frac{1}{2!}(h^{2}f_{xx}+k^{2}f_{yy}+2hkf_{xy})\\
+\frac{1}{3!}(h^{3}f_{xxx}+k^{3}f_{yyy}+3h^{2}kf_{xxy}+3hk^{2}f_{xyy})+\dots
\end{align}
$$
# maclaurin theorem
$$\large
f(x)=f(0)+xf'(0)+\frac{x^{2}}{2!}f''(0)+\frac{x^{3}}{3!}f'''(0)+\dots+\frac{x^{n}}{n!}f^{n}(0)
$$

---
2. function of two variables
$$\large
\begin{align}
f(x,y)=f(0,0)+(xf_{x}(0,0)+yf_{y}(0,0))+\frac{1}{2!}(x^{2}f_{xx}(0,0)+y^{2}f_{yy}(0,0)+2xyf_{xy})\\
+\frac{1}{3!}(h^{3}f_{xxx}+k^{3}f_{yyy}+3h^{2}kf_{xxy}+3hk^{2}f_{xyy})+\dots
\end{align}
$$

# Jacobian's theorem

If $u_{1},u_{2},\dots,u_{n}$ are the functions of independent variables $x_{1},x_{2},\dots,x_{n}$
then the determiner is called jacobian or functional determinant of $u_{1},u_{2},\dots,u_{n}$
with respect to $x_{1},x_{2},\dots,x_{n}$


$$\large
\frac{\delta (u_{1},u_{2},\dots,u_{n})}{\delta (x_{1},x_{2},\dots,x_{n})}
= \begin{bmatrix}\frac{\delta u_{1}}{\delta x_{1}}&\frac{\delta u_{1}}{\delta x_{2}}
\dots\frac{\delta u_{1}}{\delta x_{n}}\\\frac{\delta u_{2}}{\delta x_{1}}&
\frac{\delta u_{2}}{\delta x_{2}}\dots\frac{\delta u_{2}}{\delta x_{n}}\
\\\dots&\dots\\\frac{\delta u_{n}}{\delta x_{1}}&\frac{\delta u_{n}}{\delta x_{2}}
\dots\frac{\delta u_{n}}{\delta x_{n}}\end{bmatrix}
$$

## implicit function

If $u_{1},u_{2}$ and $u_{3}$ are the implicit functions of $x_{1},x_{2},x_{3}$ 
$F_{1}(u_{1},u_{2},u_{3},x_{1},x_{2},x_{3})=0$
$F_{2}(u_{1},u_{2},u_{3},x_{1},x_{2},x_{3})=0$
$F_{3}(u_{1},u_{2},u_{3},x_{1},x_{2},x_{3})=0$
then, 
$$\LARGE
\frac{\delta(u_{1},u_{2},u_{3})}{\delta(x_{1},x_{2},x_{3})} = 
(-1)^{3}[\frac{\frac{\delta(F_{1},F_{2},F_{3})}{\delta(x_{1},x_{2},x_{3})}}{
\frac{\delta(F_{1},F_{2},F_{3})}{\delta(u_{1},u_{2},u_{3})}}]
$$

## functional dependence

$$\LARGE
\begin{align}
\frac{\delta (u_{1},u_{2},\dots,u_{n})}{\delta (x_{1},x_{2},\dots,x_{n})} = 0; dependent\\
\frac{\delta (u_{1},u_{2},\dots,u_{n})}{\delta (x_{1},x_{2},\dots,x_{n})} \neq 0; independent\\
\end{align}
$$
if there is an functional dependency then we fill find equation of u with respect to v

# Maxima and Minima

Also referred as extrema of a function 
## whole derivatives
1. if x is function of y then take 2nd order derivative of the function 
2. take critical point of function i.e. make x = 0
Then,
$$\large
\begin{align}
\frac{d^{2}y}{dx^{2}} &\gt 0\;\to minima\\
\frac{d^{2}y}{dx^{2}} &\lt 0\;\to maxima\\
\frac{d^{2}y}{dx^{2}} &= 0\;\to\text{neither minima nor maxima}\\
\end{align}
$$
## partial derivative
Let,
- p = $\LARGE \frac{\delta z}{\delta x}$
- q = $\LARGE \frac{\delta z}{\delta y}$
Using taylor's series
- r = $\LARGE \frac{\delta^{2} z}{\delta x^{2}}$
- t = $\LARGE \frac{\delta^{2} z}{\delta y^{2}}$
- s = $\LARGE \frac{\delta^{2} z}{\delta x\delta y}$\
Then, at critical points

$$\large
\begin{align}
rt-s^{2}\gt 0\;\&\;r\gt 0\;\to minima\\
rt-s^{2}\gt 0\;\&\;r\lt 0\;\to maxima\\
rt-s^{2}\lt 0\to \text{no extreme values}\\
\end{align}
$$
### lanrange

It is used to find the maximum and minimum values of a function of three or more variables when the variables are not independent but are connected by some given relation 

the lanrange function is
$F(x,y,z)=f(x,y,z)+\lambda\phi(x,y,z)$
---
$$\large
\begin{align}
(\frac{\delta f}{\delta x}+\lambda\frac{\delta \phi}{\delta x})dx+
(\frac{\delta f}{\delta y}+\lambda\frac{\delta \phi}{\delta y})dy+
(\frac{\delta f}{\delta z}+\lambda\frac{\delta \phi}{\delta z})dz&=0\\
\frac{\delta f}{\delta x}+\lambda\frac{\delta \phi}{\delta x}=0;
\frac{\delta f}{\delta y}+\lambda\frac{\delta \phi}{\delta y}=0;
\frac{\delta f}{\delta z}+\lambda\frac{\delta \phi}{\delta z}=0;
\end{align}
$$


