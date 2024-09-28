# Beta and Gamma function
1.  first

----

$$\large
\beta(m,n)=\int_{0}^{1}x^{m-1}(1-x)^{n-1}dx

$$

----
2.  second

----

$$\large
\Gamma n=\begin{cases}
(n-1)! &\text{n = natural number}\\
(n-1)\;\Gamma(n-1) &\text{n = fractional number}
\end{cases}

$$

----
3.  third

----

$$\large
\beta(m,n)=\frac{\Gamma m\; \Gamma n}{\Gamma (m+n)}

$$

----
4.  fourth

----

$$\large
\Gamma n=\int_{0}^{\infty}e^{-x}x^{n-1}dx

$$

----
5.  fifth

----

$$\large
\beta(m,n)=\int_{0}^{\infty}\frac{x^{m-1}}{(1+x)^{m+n}}dx

$$

----
6.  sixth

----

$$\LARGE
\int_{0}^{\frac{\pi}{2}}\sin^{m}\theta\cos^{n}\theta\;d\theta

$$

----
7.  seventh

----

$$\large
\Gamma n\;\Gamma(1-n)=\frac{\pi}{\sin(n\pi)}

$$

----
# Error 
$$\large
\begin{align}
\text{Error (E)}&=\text{Ture value}-\text{Approximate value}\\
E &= |X-X'|
\end{align}
$$
### types
1. Absolute  Error ($\Large E_{a}$)
	-  Absolute  Error  = True value - Approximate value
	$$\LARGE
	E_{a} = |X-X'|
	$$
1. Relative  Error  ($\Large E_{n}$)
	- Relative  Error  = $\Large\frac{\text{Absolute Error}}{\text{True Error}}$
	$$\LARGE
	E_{r} = |\frac{X-X'}{X}|
	$$
1. Percentage  Error  ($\Large E_{p}$)
	- Percentage Error = $\text{Realtive Error}\times 100$ 
	$$\LARGE
	E_{r} = |\frac{X-X'}{X}|\times 100\%
	$$
# double and triple integration

Limit with constant should always be outside of limit with variable therefore 
interchange limits and interchange  derivatives as well
$$\LARGE
\begin{align}
&\int^{x^{2}}_{0}[\int^{1}_{0}(x^{2}+y^{2})dx]dy\\\\
&\text{After interchnage}\\\\
&\int^{1}_{0}[\int^{x^{2}}_{0}(x^{2}+y^{2})dy]dx\\\\
\end{align}
$$

