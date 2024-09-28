# stack organisation
works in LIFO (Last In First Out)

## Notations
1. Infix notation
	A+B
1. Prefix notation (Polish notation)
    +AB
2. Postfix notation (Reverse Polish notation)
    AB+

Example

---
1.
$\large \frac{A-B\times(\frac{C}{D})}{E\times F + (G+H)}$

In postfix notations

$\large ABCD/\times-EF\times GH++/$

Diagram

----
2.
$\large \frac{A}{B}+\frac{C}{D}+\frac{Q-R+H}{A\times B}$


In postfix notations

$\large AB/CD/+HQR-+AB\times/+$

A=121; B= 3; C=108; D=9; H=6; Q=10; R=2


Diagram

---

# address instruction
### 3 address
X=(A+B)(C+D)

ADD R1,A,B : $\large R_{1}\to M[A]+M[B]$
ADD R2,C,D : $\large R_{2}\to M[C]+M[D]$
MUL X,R1,R2 : $\large M[X]\to R_{1}\times R_{2}$

### 2 address
X=(A+B)(C+D)

MOV R1,A : $\large R_{1}\to M[A]$
ADD R1,B : $\large R_{1}\to R_{1}+M[B]$
MOV R2,C : $\large R_{2}\to M[C]$
ADD R2,D : $\large R_{1}\to R_{2}+M[D]$
*error*
MUL R1,R1,R2 : $\large R_{1}\to R_{1}R_{2}$
MOV X,R1 : $\large X\to M[R_{1}]$

### 1 address
X=(A+B)(C+D)
LOAD(AC)
AC <- `M[A]`
Add B AC <- AC+`M[B]`
STORE(T) `M[T]`<- AC
AC <- `M[C]`
Add D AC <- AC+`M[D]`
Mul AC<-AC+`M[T]`

### 0 address
PUSH(A) TOS <-A
PUSH(B) TOS <-B
Add TOS <- A+B
PUSH(C) TOS <-C
PUSH(D) TOS <-D
Add TOS <- C+D
Mul TOS <- (A+B)(C+D)
POP(X) TOS <- `M[x]`

