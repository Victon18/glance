# machine

![[q1.png]]

derive the state diagram from the given logic circuit

- d flip flop
- no of flip-flop = 1
- no of states = 2
- inouts = x,y
- output = A
- flip-flop output = A

1. find expression for input of flip-flop and system output

$D_{A} = x \oplus y \oplus A,A = D_{A}$

2. characteristic equation

$Q_{n+1} = D, A_{n+1} = D_{A}$

3. $A_{n+1} = D_{A} = x \oplus y \oplus A$

4. state table

| Present state | Input | -   | Next state |
| ------------- | ----- | --- | ---------- |
| An            | x     | y   | An+1       |
| 0             | 0     | 0   | 0          |
| 0             | 0     | 1   | 1          |
| 0             | 1     | 0   | 1          |
| 0             | 1     | 1   | 0          |
| 1             | 0     | 0   | 1          |
| 1             | 0     | 1   | 0          |
| 1             | 1     | 0   | 0          |
| 1             | 1     | 1   | 1          |

ques2.

![[q13.png]]

2 flip-flop, no of state = $2^{2}$ =4
input of system = x
output of system = y

1. find the expression of flip-flop
	a) for input
		$\large D_{A} = A_{x} + B_{x} = x(A+B)$
		$\large D_{B} = \overline{A}x$ 
	 b) for output
		 $\large y = (A+B)\overline{x}$
1. characteristic equation of D flip-flop
		$\large Q_{n-1} = D$
1. Next state

$A_{n+1} = D_{A} = X(A+B)$
$B_{n+1} = D_{B} = \overline{A}X$

4. state table

| Present state | -   | Input | Next state | -    | output |
| ------------- | --- | ----- | ---------- | ---- | ------ |
| An            | Bn  | x     | An+1       | Bn+1 | y      |
| 0             | 0   | 0     | 0          | 0    | 0      |
| 0             | 0   | 1     | 0          | 1    | 0      |
| 0             | 1   | 0     | 0          | 0    | 1      |
| 0             | 1   | 1     | 1          | 1    | 0      |
| 1             | 0   | 0     | 0          | 0    | 1      |
| 1             | 0   | 1     | 1          | 0    | 0      |
| 1             | 1   | 0     | 0          | 0    | 1      |
| 1             | 1   | 1     | 1          | 0    | 0      |

![[SD.png]]

