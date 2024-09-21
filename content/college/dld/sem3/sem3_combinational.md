# 4 bit adder
## ripple adder
- to add more than two bits
- generates a carry and a sum bit

|$C_{3}$|$C_{2}$|$C_{1}$|$C_{in}$|
|--|--|--|--|
|$A_{3}$|$A_{2}$|$A_{1}$|$A_{0}$|
|$B_{3}$|$B_{2}$|$B_{1}$|$B_{0}$|
|~|~|~|~|
|$S_{3}$|$S_{2}$|$S_{1}$|$S_{0}$|
|$C_{4}$|~|~|~|

###  disadvantage
- there is a massive delay in calculations with larger bits.
- Each of the full adder takes time to calculate and generate carry
- the last full adder has to wait for the previous adder's generated carry

![[ripAdder.png]]

## adder and subtractor
Note -> for subtraction we assume that subtractor is greater than subtractent
1. subtraction using addition
    - to perform subtraction using adding we can use an external XOR circuit
    - we have to perform a 2's compliment first and then add ignoring the last carry over
    - to performing a 2's compliment we have to reverse all digits and add 1.
----
2. creating a CTRL input
    - pass this as an input in all digits XOR
    - when high it will reverse all digits
    - pass CTRL as $C_{in}$ for performing the addition of high required for 2's compliment
3. ignore $C_{4}$ in case of subtraction

![[add-sub.png]]

## Look ahead carry

- this circuit removes disadvantages from ripple carry adder
- it predicts two types of carry based on the digits entered
- these two types of carry are given beforehand so that all adder can perform calculation simultaneously

1. Generated carry $G_{n}$
---
- It means the carry will be produced regardless of the last carry being 0 or 1
- 1 & 1 are the only digits

2. Propagated carry $P_{n}$
---
- It means the carry will be dependent on the last carry input
- 1 & 0 and 0 & 1 are the digits

$$ \Large
\begin {align}
C_{n+1} &= G_{n}+C_{n}P_{n}\\
C_{1} &= G_{0}\\
C_{2} &= G_{1}+G_{0}P_{1}\\
C_{3} &= G_{2}+G_{1}P_{2}+G_{0}P_{1}P_{2}\\
C_{4} &= G_{3}+G_{2}P_{3}+G_{1}P_{2}P_{3}+G_{0}P_{1}P_{2}P_{3}\\
\end {align}
$$


![[CLA.png]]
