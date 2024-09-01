# Boolean Algebra

|Postulate|name|(a)|(b)|
|-|-|-|-|
|Postulate 2|-|$\large x+0=x$|$\large x.1=x$|
|Postulate 5|-|$\large x+\overline{x}=1$|$\large x.\overline{x}=0$|
|Theorem 1|-|$\large x+x=x$|$\large x.x=x$|
|Theorem 2|-|$\large x+1=1$|$\large x.0=0$|
|Theorem 3|involution|$\large \overline{\overline{x}} = x$|-|
|Theorem 3|commutative|$\large x+y=y+x$|$\large xy=yx$|
|Theorem 4|associative|$\large x+(y+z)=(x+y)+z$|$\large x(yz)=(xy)z$|
|Theorem 4|distributive|$\large x(y+z)=xy+xz$|$\large x+yz=(x+y)(y+z)$|
|Theorem 5|De morgan|$\large \overline{(x+y)}=\overline{x}.\overline{y}$|$\large \overline{xy}=\overline{x}+\overline{y}$|
|Theorem 6|absorption|$\large x+xy=x$|$\large x(x+y)=x$|

# Canonical and Standard Forms

- Literal: A variable or its complement
- Product term: literals connected by •
- Sum term: literals connected by +
- Minterm: a product term in which all the variables appear exactly once, either complemented or uncomplemented.
- Maxterm: a sum term in which all the variables appear exactly once, either complemented or uncomplemented.
- Canonical form: Boolean functions expressed as a sum of Minterms or product of Maxterms are said to be in canonical form.

1. Minterms and Maxterms
---

| x   | y   | z   | Minterm     | Maxterm       |
| --- | --- | --- | ----------- | ------------- |
| 0   | 0   | 0   | x’y’z’ = m0 | x+y+z = M0    |
| 0   | 0   | 1   | x’y’z = m1  | x+y+z’ = M1   |
| 0   | 1   | 0   | x’yz’ = m2  | x+y’+z = M2   |
| 0   | 1   | 1   | x’yz = m3   | x+y’+z’= M3   |
| 1   | 0   | 0   | xy’z’ = m4  | x’+y+z = M4   |
| 1   | 0   | 1   | xy’z = m5   | x’+y+z’ = M5  |
| 1   | 1   | 0   | xyz’ = m6   | x’+y’+z = M6  |
| 1   | 1   | 1   | xyz = m7    | x’+y’+z’ = M7 |

2. Sum-of-Minterms and Product-of- Maxterms
3.  Product and Sum terms
4. Sum-of-Products (SOP) and Product-of-Sums (POS)
----
- f1(a,b,c) = ∑ m(1,2,4,6), where ∑ indicates that this is a sum-of-products form, and m(1,2,4,6) indicates that the minterms to be included are m1, m2, m4, andm6.
- f1(a,b,c) = ∏ M(0,3,5,7), where ∏ indicates that this is a product-of-sums form, and M(0,3,5,7) indicates that the maxterms to be included are M0, M3, M5, andM7.
- Since mj = Mj’ for any j,
- ∑ m(1,2,4,6) = ∏ M(0,3,5,7) = f1(a,b,c)
- converaion POS to SOP:
    Replace ∑ with ∏ (or vice versa) and replace those j’s that appeared in the original form with those that do not.
    Example:
    - f1(a,b,c)= a’b’c + a’bc’ + ab’c’ + abc’
        = m1 + m2 + m4 + m6
        = ∑(1,2,4,6)
        = ∏(0,3,5,7)
        = (a+b+c)•(a+b’+c’)•(a’+b+c’)•(a’+b’+c’)


# Kmap

# Logic gates
### Basic
#### AND
A,B -> AB

|X|Y|F|
|-|-|-|
|0|0|0|
|0|1|0|
|1|0|0|
|1|1|1|

#### OR
A,B -> A+B

|X|Y|F|
|-|-|-|
|0|0|0|
|0|1|1|
|1|0|1|
|1|1|1|

#### NOT
A -> $\overline{A}$

|X|F|
|-|-|
|0|1|
|1|0|

#### Buffer
A -> A

|X|F|
|-|-|
|0|0|
|1|1|

### Universal
#### NAND
A,B -> $\overline{AB}$

|X|Y|F|
|-|-|-|
|0|0|1|
|0|1|1|
|1|0|1|
|1|1|0|

#### NOR
A,B -> $\overline{A+B}$

|X|Y|F|
|-|-|-|
|0|0|1|
|0|1|0|
|1|0|0|
|1|1|1|

### Exclusive
####  XOR
A,B -> A XOR B = $A\overline{B}+\overline{A}B$

| X   | Y   | F   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 0   |
Properties of Xor

- XOR (also $\oplus$) : the “not-equal” function
- $XOR(X,Y) = X Y = \overline{X}Y + X\overline{Y}$
- Identities:
	- $X \oplus 0 = X$
	- $X \oplus 1 = \overline{X}$
	- $X \oplus X = 0$
	- $X \oplus \overline{X} = 1$
- Properties:
	- $X \oplus Y = Y \oplus X$
	- $(X \oplus Y) \oplus W = X \oplus ( Y \oplus W)$
#### XNOR
A,B -> $\overline{A \oplus B }$ = $\overline{A\overline{B}}+\overline{\overline{A}B}$ = $(\overline{A}+B)(A\overline+{B})$

|X|Y|F|
|-|-|-|
|0|0|1|
|0|1|0|
|1|0|0|
|1|1|1|

# Gate implementation
## NAND
###  NOT gate using NAND Gate
Single input NAND gate is equal to NOT gate
![[N-NAND.png]]
### AND gate using NAND Gate
![[A-NAND.png]]
### OR gate using NAND
![[0-NAND.png]]
### XOR using NAND
### XNOR using NAND
## NOR
### NOT using NOR
![[N-OR.png]]
### OR using NOR
![[O-NOR.png]]
### AND using NOR
![[A-NOR.png]]
### XOR using NOR
### XNOR using NOR
