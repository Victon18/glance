# Half Adder
- it adds two bits number together
- 2 inputs(A, B), 2 output(Carry, Sum)

|A|B|C|S|
|-|-|-|-|
|0|0|0|0|
|0|1|0|1|
|1|0|0|1|
|1|1|1|0|

for S:

|**A\B**|**$\overline{B}$**|**B**|
|-|-|-|
|**$\overline{A}$**|-|1|
|**A**|1|-|

$\large S = A \oplus B$

for C:

| **A\B**            | **$\overline{B}$** | **B** |
| ------------------ | ------------------ | ----- |
| **$\overline{A}$** | -                  | -     |
| **A**              | -                  | 1     |

C = A.B

![[HA.png]]

# Full Adder
- It is used for the purpose of adding two single bit numbers with a carry.
- Thus, full adder has the ability t perform the addition of three bits.
- 3 input (A, B, $C_{in}$) 2 output (Carry $C_{out}$, Sum)

|A|B|$C_{in}$|$C_{out}$|S|
|-|-|-|-|-|
|0|0|0|0|0|
|0|0|1|0|1|
|0|1|0|0|1|
|0|1|1|1|0|
|1|0|0|0|1|
|1|0|1|1|0|
|1|1|0|1|0|
|1|1|1|1|1|

for S:

|**A\B$C_{in}$**|**$\overline{B}\overline{C_{in}}$**|**$\overline{B}C_{in}$**|$BC_{in}$|$B\overline{C_{in}}$|
|-|-|-|-|-|
|**$\overline{A}$**|-|1|-|1|
|**A**|1|-|1|-|

$\large S = A \oplus B \oplus C_{in}$

for C:


| **A\B$C_{in}$**    | **$\overline{B}\overline{C_{in}}$** | **$\overline{B}C_{in}$** | $BC_{in}$ | $B\overline{C_{in}}$ |
| ------------------ | ----------------------------------- | ------------------------ | --------- | -------------------- |
| **$\overline{A}$** | -                                   | -                        | 1         | -                    |
| **A**              | -                                   | 1                        | 1         | 1                    |

C = AB + B$C_{in}$ + $C_{in}A$

![[FA.png]]

#### Full - adder using Half - adder
![[HA-FA.png]]
# Half Subtractor
- it subtract two bits number together
- 2 inputs(A, B), 2 output(Difference, Borrow)

|A|B|D|b|
|-|-|-|-|
|0|0|0|0|
|0|1|1|1|
|1|0|1|0|
|1|1|0|0|

for D:

|**A\B**|**$\overline{B}$**|**B**|
|-|-|-|
|**$\overline{A}$**|-|1|
|**A**|1|-|

$\large S = A \oplus B$

for C:

| **A\B**            | **$\overline{B}$** | **B** |
| ------------------ | ------------------ | ----- |
| **$\overline{A}$** | -                  | 1     |
| **A**              | -                  | -     |

C = $\overline{A}$.B

![[HS.png]]

# Full Subtractor
- It is used for the purpose of subtracting two single bit numbers with a borrow.
- Thus, full adder has the ability to perform the subtraction: of three bits.
- 3 input (A, B, $B_{in}$) 2 output (Borrow $B_{out}$, Difference)

|A|B|$B_{in}$|$B_{out}$|D|
|-|-|-|-|-|
|0|0|0|0|0|
|0|0|1|1|1|
|0|1|0|1|1|
|0|1|1|1|0|
|1|0|0|0|1|
|1|0|1|0|0|
|1|1|0|0|0|
|1|1|1|1|1|

for S:

|**A\B$B_{in}$**|**$\overline{B}\overline{B_{in}}$**|**$\overline{B}B_{in}$**|$BB_{in}$|$B\overline{B_{in}}$|
|-|-|-|-|-|
|**$\overline{A}$**|-|1|-|1|
|**A**|1|-|1|-|

$\large S = A \oplus B \oplus B_{in}$

for C:


| **A\B$B_{in}$**    | **$\overline{B}\overline{B_{in}}$** | **$\overline{B}B_{in}$** | $BB_{in}$ | $B\overline{B_{in}}$ |
| ------------------ | ----------------------------------- | ------------------------ | --------- | -------------------- |
| **$\overline{A}$** | -                                   | 1                        | 1         | 1                    |
| **A**              | -                                   | -                        | 1         | -                    |

$B_{out}$ = $\overline{A}$B + ($\overline{A}B)B_{in}$

![[FS.png]]
# Binary Multiplier

$\large A = A_{1}A_{0}$ 
$\large B = B_{1}B_{0}$

![[mult.png]]