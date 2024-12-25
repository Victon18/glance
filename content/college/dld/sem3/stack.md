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

# Addressing modes
* Specifies a rule for interpreting or modifying the address field of the
instruction (before the operand is actually referenced)
* Variety of addressing modes
	- to give programming flexibility to the user
	- to use the bits in the address field of the
## TYPES OF ADDRESSING MODES

Implied Mode
---
Address of the operands are specified implicitly in the instruction
- No need to specify address in the instruction
- Ex: CMA(Complement the accumulator)
-
---
Immediate Mode
---
Instead of specifying the address of the operand, the instruction contains the operand itself.

---
Direct Address Mode
---
Instruction specifies the memory address which can be used directly to get the operand.

---
Indirect Addressing Mode
---
The address field of an instruction specifies the address of a memory location that contains the address of the operand.

---
Register Mode
---
Address specified in the instruction is the register address

---
Register Indirect Mode
---
- Instruction specifies a register which contains the memory address of the operand
-
---
Auto-increment
---
Same as the Register Indirect, but when the address in the register is used to access memory, the value in the register is incremented after the execution of the
instruction.

Auto-decrement
---
Same as the Register Indirect, but when the address in the register is used to access memory, the value in the register is decremented before the execution of the instruction.

---
Relative Addressing Modes
---
The Address fields of an instruction specifies the part of the address (abbreviated address) which can be used along with a PC to calculate the address of the operand
EA = PC + IR(address)
- Address field of the instruction is short
- Large physical memory can be accessed with a small number of address bits

Indexed Addressing Mode
---
XR: Index Register:
- EA = XR + IR(address)
---
Base Register Addressing Mode
---
BAR: Base Address Register:
- EA = BAR + IR(address)

## example
R1 = 98
XR = 3
Relative address = PC + address
Index address = XR + address
PC = programm Counter having next instruction address(52)

| add | cont |
| --- | ---- |
| 50 | Load to AC/ Mode     |
| 51 | Address = 100     |
| 52 | Next Instruction     |
| ---- | ---    |
| 97 | 450     |
| 98 | 700     |
| 99 | 810     |
| 100 | 105     |
| 101 | 32     |
| 102 | 45     |
| 103 | 65     |
| 104 | 75     |
| 105 | 500     |
| 152 | 70    |

| Address Mode  | Effective address | Contents of Effective Address |
| ------------- | ----------------- | ----------------------------- |
| Direct        | 100               | 105                           |
| Indirect      | 105               | 500                           |
| Immediate     | -                 | 100                           |
| Relative      | 152               | 70                            |
| Indexed       | 103               | 65                            |
| Reegister dir | -                 | 98                            |
| Register in-  | 98                | 700                           |
| Auto-incr     | 100;101           | -105;35                       |
| Auto-decr     | 100;99            | 105;800                       |
