# INTRO
in combinational circuit the output only depends upon the present input whereas
in sequential cicuit the output not only depends upon its present input but also its previous input and output

# Magnitude Comaparator

- Compares two bits
-  Let A and B be two (one bits) - 2 inputs
- outputs:
	- $\large y_{0}$ (A=B)
	-  $\large y_{1}$ (A>B)
	- $\large y_{2}$ (A<B)

| A   | B   | $\large y_{0}$ | $\large y_{1}$ | $\large y_{2}$ |
| --- | --- | -------------- | -------------- | -------------- |
| 0   | 0   | 1              | 0              | 0              |
| 0   | 1   | 0              | 0              | 1              |
| 1   | 0   | 0              | 1              | 0              |
| 1   | 1   | 1              | 0              | 0              |
 
$\LARGE  y_{0} = \overline{A}.\overline{B}+AB$ 
$\LARGE y_{1} = A.\overline{B}$
$\LARGE  y_{2} = \overline{A}.B$

# Multiplexer (MUX)
It is a combinational logic circuit with multiple inputs and single output.
It is also known as many to one or parallel to serial converter

- It has '$2^{n}$' inputs, '1' output and 'n' select lines
According to the status of the select lines anyone of the input from $2^{n}$ inputs will be connected or passed to the output

## 2:1 MUX
Number of input = 2 = $2^{n}$, n=1
output = 1
number of select lines  = 1

$\LARGE y = \overline{S}D_{0} + SD_{1}$

| S   | y       |
| --- | ------- |
| 0   | $D_{0}$ |
| 1   | $D_{1}$ |

![[2_1.png]]

## 4:1 MUX
Select lines = 2 ($S_{1}$ and $S_{0}$)
Inputs = 4, ($D_{0}$, $D_{1}$, $D_{2}$, $D_{3}$)

$\LARGE y = \overline{S_{1}} \overline{S_{0}} D_{0} + \overline{S_{1}} S_{0} D_{1} + S_{1} \overline{S_{0}} D_{2} + S_{1} S_{0} D_{3}$

| $S_{1}$ | $S_{0}$ | y   |
| ------- | ------- | --- |
| 0       | 0       | D0  |
| 0       | 1       | D1  |
| 1       | 0       | D2  |
| 1       | 1       | D3  |
![[4_1.png]]
## 8:1 MUX

# DEMUX
it is  a combinational logic circuit with single input and $2^{n}$ output with 'n' select

| $S_{1}$ | $S_{0}$ | y0  | y1  | y2  | y3  |
| ------- | ------- | --- | --- | --- | --- |
| 0       | 0       | D   | 0   | 0   | 0   |
| 0       | 1       | 0   | D   | 0   | 0   |
| 1       | 0       | 0   | 0   | D   | 0   |
| 1       | 1       | 0   | 0   | 0   | D   |

# decoder and encoder

1. both are multiple input of multiple output device.
2. decoder converts 'n' line of input to '$2^{n}$' line of output whereas
encoder converts '$2_{n}$' line o inputs to 'n' line of output

Encoder (Data compress), Decoder (Data expands)

Application of decoder
To convert binary to octal, hexadecimal, decimal

Application of encoder
To convert octal, hexadecimal, decimal to binary
# Decoder

It is used to decode the input signal received at the receiver
n inputs -> $2^{n}$ outputs
## 2:4 decoder

| A   | $A_{0}$ | $D_{0}$ | $D_{1}$ | $D_{2}$ | $D_{3}$ |
| --- | ------- | ------- | ------- | ------- | ------- |
| 0   | 0       | 1       | 0       | 0       | 0       |
| 0   | 1       | 0       | 1       | 0       | 0       |
| 1   | 0       | 0       | 0       | 1       | 0       |
| 1   | 1       | 0       | 0       | 0       | 1       |

According to combinations of input only one output from $2^{n}$outputs will be active high (1)

$D_{0}$ = $\overline{A_{1}} \overline{A_{0}}$
$D_{1}$ = $\overline{A_{1}} A_{0}$
$D_{2}$ = $A_{1} \overline{A_{0}}$
$D_{3}$ = $A_{1} A_{0}$

## 3:8 decoder
input = 3, output = 8

| $A_{2}$ | $A_{1}$ | $A_{0}$ | $D_{0}$ | $D_{1}$ | $D_{2}$ | $D_{3}$ | $D_{4}$ | $D_{5}$ | $D_{6}$ | $D_{7}$ |
| ------- | ------- | ------- | ------- | ------- | ------- | ------- | ------- | ------- | ------- | ------- |
| 0       | 0       | 0       | 1       | 0       | 0       | 0       | 0       | 0       | 0       | 0       |
| 0       | 0       | 1       | 0       | 1       | 0       | 0       | 0       | 0       | 0       | 0       |
| 0       | 1       | 0       | 0       | 0       | 1       | 0       | 0       | 0       | 0       | 0       |
| 0       | 1       | 1       | 0       | 0       | 0       | 1       | 0       | 0       | 0       | 0       |
| 1       | 0       | 0       | 0       | 0       | 0       | 0       | 1       | 0       | 0       | 0       |
| 1       | 0       | 1       | 0       | 0       | 0       | 0       | 0       | 1       | 0       | 0       |
| 1       | 1       | 0       | 0       | 0       | 0       | 0       | 0       | 0       | 1       | 0       |
| 1       | 1       | 1       | 0       | 0       | 0       | 0       | 0       | 0       | 0       | 1       |

## active low decoder

In active high -> 0 represents there is no signal; 1 represents signal is present
In active low -> 1 represents there is no signal; 0 represents signal is present

| $A_{1}$ | $A_{0}$ | $D_{0}$ | $D_{1}$ | $D_{2}$ | $D_{3}$ |
| ------- | ------- | ------- | ------- | ------- | ------- |
| 0       | 0       | 0       | 1       | 1       | 1       |
| 0       | 1       | 1       | 0       | 1       | 1       |
| 1       | 0       | 1       | 1       | 0       | 1       |
| 1       | 1       | 1       | 1       | 1       | 0       |

$\large D_{0} = A_{1} A_{0}$
$\large D_{1} = A_{1} \overline{A_{0}}$
$\large D_{2} = \overline{A_{1}} A_{0}$
$\large D_{3} = \overline{A_{1}} \overline{A_{0}}$

## Decoder with enable input

| E   | $A_{1}$ | $A_{0}$ | $D_{0}$ | $D_{1}$ | $D_{2}$ | $D_{3}$ |
| --- | ------- | ------- | ------- | ------- | ------- | ------- |
| 1   | X       | X       | 0       | 0       | 0       | 0       |
| 0   | 0       | 0       | 1       | 0       | 0       | 0       |
| 0   | 0       | 1       | 0       | 1       | 0       | 0       |
| 0   | 1       | 0       | 0       | 0       | 1       | 0       |
| 0   | 1       | 1       | 0       | 0       | 0       | 1       |

- When enable input E = 1, all the outputs of decoder are 0
- Whenever enable input = 0, the decoder circuit will work as intended

# Priority Encoder
- It is an encoder circuit that includes the priority function

<table border="1px">
    <tr>
        <th colspan="4"> Inputs</th>
        <th colspan="3">Output</th>
        <tr><th>D<sub>0</th><th>D<sub>1</th><th>D<sub>2</th><th>D<sub>3</th><th>X</th><th>Y</th><th>V</th></tr>
        <tr><td>0</td><td>0</td><td>0</td><td>0</td><td>X</td><td>X</td><td>0</td></tr>
        <tr><td>1</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>1</td></tr>
        <tr><td>X</td><td>1</td><td>0</td><td>0</td><td>0</td><td>1</td><td>1</td></tr>
        <tr><td>X</td><td>X</td><td>1</td><td>0</td><td>1</td><td>0</td><td>1</td></tr>
        <tr><td>X</td><td>X</td><td>X</td><td>1</td><td>1</td><td>1</td><td>1</td></tr>
    </tr>

Priority order = $D_{3}$ > $D_{2}$ > $D_{1}$ > $D_{0}$
therefore output = $D_{2}$ + $D_{3}$ (for x)
performs same for y|V

# sequential logic circuit
If consists of combinational circuit to which strong elements are connected to form a feedback path

![[seq.png]]
## two sequential logic circuit are there
1. Synchronous sequential circuit
---
- A sequential circuit whose output changes with input at discrete time called synchronous sequences
- It uses a clock signal as an input to the memory element

![[Sseq.png]]

2. Asynchronous sequential circuit
---
- The sequences circuit whose output changes with the sequence of input

![[Aseq.png]]

for combinational circuit -> Y (output) = f (input)
for sequential circuit -> Y (output) = f (input, previous output)

## Clock signal
clock signal is a train of pulses with 0 and 1 at certain class interval.

f = $\LARGE \frac{1}{T} = 1 MH_Z$
T = 10$^{-6}$ sec

1. When CLK = 1 -> signal will change
- In level triggered sequential circuit the variation in the output occurs according to the input only when clock equal to 1
2. When CLK from 0 to 1
- Changes in the output occurs according to the input only when the clock signal varies from 0 to 1
3. When CLK changes from 1 to 0

# Memory element
There are 2 types of memory element :-
1. LATCHES
2. FLIP-FLOP
The memory element is able to store 1-bit data that may be 0 or 1. Therefore, they are called bistable multivibrator
## latches
### SR Latch
the SR latch is also known as Set - Reset latch

--NOR BASED SR Latch--
Both NOR have S,R -> Input
2 Input -> 2 output as feedback path
if i input = 1; then output = 0

| S   | R   | Q   | $\overline{Q}$ | condition |
| --- | --- | --- | -------------- | --------- |
| 1   | 0   | 1   | 0              | set       |
| 0   | 0   | 1   | 0              | previous  |
| 0   | 1   | 0   | 1              | reset     |
| 0   | 0   | 0   | 1              | previous  |
| 1   | 1   | X   | X              | forbidden |

![[SR.png]]

--Characteristic Table--

| S   | R   | Q        | $\overline{Q}$ | condition   |
| --- | --- | -------- | -------------- | ----------- |
| 0   | 0   | previous | previous       | -           |
| 0   | 1   | 0        | 1              | -           |
| 1   | 0   | 1        | 0              | -           |
| 1   | 1   | X        | X              | not allowed |

--NAND BASED SR LATCH--

![[ASR.png]]

| S   | R   | Q   | $\overline{Q}$ | condition |
| --- | --- | --- | -------------- | --------- |
| 0   | 1   | 1   | 0              | set       |
| 1   | 1   | 1   | 0              | previous  |
| 1   | 0   | 0   | 1              | reset     |
| 0   | 0   | X   | X              | forbidden |

it is also known as active low latch because at S = 0, the latch set occurs

### D LATCH
D -> (DATA) LATCH

![[D.png]]

| D   | Q   | $\overline{Q}$ |
| --- | --- | -------------- |
| 0   | 1   | 0              |
| 1   | 0   | 1              |

### S-R flip-flop/ SR clocked latch

on intentional change in input may cause unwanted change in the memory.
Therefore a signal known as clock or clock pulse is used in S-R latch.
This circuit is known as clock S-R Latch or S-R flip-flop.

When clock is low irrespective of the input output is always gives the previous output ie acts as a memory
when the memory data is to be modified clock signal is made high and respective inputs has to be provided.

when CP = 0, output = previous output
when CP = 1, normal SR Latch

| CP  | S   | R   | Q        | $\overline{Q}$ | condition |
| --- | --- | --- | -------- | -------------- | --------- |
| 0   | X   | X   | previous | previous       | memory    |
| 1   | 0   | 1   | 0        | 1              | reset     |
| 1   | 1   | 0   | 1        | 0              | set       |
| 1   | 0   | 0   | previous | previous       | -         |
| 1   | 1   | 1   | NA       | NA             | -         |

--Transition Table--

| $Q_{n}$ | $Q_{n+1}$ | S   | R   |
| ------- | --------- | --- | --- |
| 0       | 0         | 0   | X   |
| 0       | 1         | 1   | 0   |
| 1       | 0         | 0   | 1   |
| 1       | 1         | X   | 0   |

--Characteristic Table--

| $Q_{n}$ | S   | R   | $Q_{n+1}$ |
| ------- | --- | --- | --------- |
| 0       | 0   | 0   | 0         |
| 0       | 0   | 1   | 0         |
| 0       | 1   | 0   | 1         |
| 0       | 1   | 1   | X         |
| 1       | 0   | 0   | 1         |
| 1       | 0   | 1   | 0         |
| 1       | 1   | 0   | 1         |
| 1       | 1   | 1   | X         |

Characteristic equation
$$
\LARGE Q_{n+1} = S + Q_n\overline{R}
$$

![[SRFF.png]]
2
### D flip-flop

| CP  | D   | Q        | $\overline{Q}$ |
| --- | --- | -------- | -------------- |
| 0   | X   | previous | previous       |
| 1   | 0   | 0        | 1              |
| 1   | 1   | 1        | 0              |

--Transition Table--

| $Q_{n}$ | $Q_{n+1}$ | D   |
| ------- | --------- | --- |
| 0       | 0         | 0   |
| 0       | 1         | 1   |
| 1       | 0         | 0   |
| 1       | 1         | 1   |

![[DFF.png]]
### JK flip-flop

J-K flip-flop is same as the S-R flip-flop,
Only the difference is undefined state is replaced with the coompliment of the previous state

| CP  | J   | K   | Q              | $\overline{Q}$ | condition  |
| --- | --- | --- | -------------- | -------------- | ---------- |
| 0   | X   | X   | previous       | previous       | -          |
| 1   | 1   | 0   | 1              | 0              | Set        |
| 1   | 0   | 1   | 0              | 1              | Reset      |
| 1   | 0   | 0   | previous       | previous       | -          |
| 1   | 1   | 1   | $\overline{Q}$ | Q              | Compliment |

--Transition Table--

| $Q_{n}$ | $Q_{n+1}$ | J   | K   |
| ------- | --------- | --- | --- |
| 0       | 0         | 0   | X   |
| 0       | 1         | 1   | X   |
| 1       | 0         | X   | 1   |
| 1       | 1         | X   | 0   |

--Characteristic Table--

| $Q_{n}$ | J   | K   | $Q_{n+1}$ |
| ------- | --- | --- | --------- |
| 0       | 0   | 0   | 0         |
| 0       | 0   | 1   | 0         |
| 0       | 1   | 0   | 1         |
| 0       | 1   | 1   | 1         |
| 1       | 0   | 0   | 1         |
| 1       | 0   | 1   | 0         |
| 1       | 1   | 0   | 1         |
| 1       | 1   | 1   | 0         |

Characteristic equation
$$
\LARGE Q_{n+1} = J\overline{Q_n} + Q_n\overline{K}
$$

![[JK.png]]

### T flip-flop
(Toggle) flip-flop

| CP  | T   | Q              | $\overline{Q}$ | condition  |
| --- | --- | -------------- | -------------- | ---------- |
| 0   | X   | previous       | previous       | memory     |
| 1   | 0   | previous       | previous       | memory     |
| 1   | 1   | $\overline{Q}$ | Q              | compliment |

--Transition Table--

| $Q_{n}$ | $Q_{n+1}$ | T   |
| ------- | --------- | --- |
| 0       | 0         | 0   |
| 0       | 1         | 1   |
| 1       | 0         | 1   |
| 1       | 1         | 0   |

--Characteristic Table--

| $Q_{n}$ | T   | $Q_{n+1}$ |
| ------- | --- | --------- |
| 0       | 0   | 0         |
| 0       | 1   | 1         |
| 1       | 0   | 1         |
| 1       | 1   | 0         |

Characteristic equation
$$
\LARGE Q_{n+1} = T\overline{Q_n} + Q_n\overline{T}
$$

![[TFF.png]]

![[T.png]]

# conversion of flip-flops
## D -> S-R flip-flop
During the conversion of flip-flop a combination circuit is used to combine the desired input of the flip-flop to the given input of the flip-flop

--Characteristic table--

| S   | R   | $Q_{n}$ | $Q_{n+1}$ | D   |
| --- | --- | ------- | --------- | --- |
| 0   | 0   | 0       | 0         | 0   |
| 0   | 0   | 1       | 1         | 1   |
| 0   | 1   | 0       | 0         | 0   |
| 0   | 1   | 1       | 0         | 0   |
| 1   | 0   | 0       | 1         | 1   |
| 1   | 0   | 1       | 1         | 1   |
| 1   | 1   | 0       | X         | X   |
| 1   | 1   | 1       | X         | X   |



K map

| S\R$Q_{n}$ | 00  | 01  | 11  | 10  |
| ---------- | --- | --- | --- | --- |
| **0**      | 0   | 1   | 0   | 0   |
| **1**      | 1   | 1   | 1   | 1   |

$$
\LARGE D = S + \overline{R} Q_{n}
$$
![[DSR.png]]

## SR -> JK flip-flop

| J   | K   | Qn  | Qn+1 | S   | R   |
| --- | --- | --- | ---- | --- | --- |
| 0   | 0   | 0   | 0    | 0   | X   |
| 0   | 0   | 1   | 1    | X   | 0   |
| 0   | 1   | 0   | 0    | 0   | X   |
| 0   | 1   | 1   | 0    | 0   | 1   |
| 1   | 0   | 0   | 1    | 1   | 0   |
| 1   | 0   | 1   | 1    | X   | 0   |
| 1   | 1   | 0   | 1    | 1   | 0   |
| 1   | 1   | 1   | 0    | 0   | 1   |


for S

| J\K$Q_{n}$ | 00  | 01  | 11  | 10  |
| ---------- | --- | --- | --- | --- |
| **0**      | 0   | X   | 0   | 0   |
| **1**      | 1   | X   | 0   | 1   |

$\LARGE J\overline{Q_{n}}$

for R

| J\K$Q_{n}$ | 00  | 01  | 11  | 10  |
| ---------- | --- | --- | --- | --- |
| **0**      | X   | 0   | 1   | X   |
| **1**      | 0   | 0   | 1   | 1   |

$\LARGE KQ_{n}$

![[SR-JK.png]]

## JK -> SR flip-flop

| S   | R   | Qn  | Qn+1 | J   | K   |
| --- | --- | --- | ---- | --- | --- |
| 0   | 0   | 0   | 0    | 0   | X   |
| 0   | 0   | 1   | 1    | X   | 0   |
| 0   | 1   | 0   | 0    | 0   | X   |
| 0   | 1   | 1   | 0    | X   | 1   |
| 1   | 0   | 0   | 1    | 1   | X   |
| 1   | 0   | 1   | 1    | X   | 0   |
| 1   | 1   | 0   | X    | X   | X   |
| 1   | 1   | 1   | X    | X   | X   |


for J

| S\R$Q_{n}$ | 00  | 01  | 11  | 10  |
| ---------- | --- | --- | --- | --- |
| **0**      | 0   | X   | X   | 0   |
| **1**      | 1   | X   | X   | X   |

**S**

for K

| S\R$Q_{n}$ | 00  | 01  | 11  | 10  |
| ---------- | --- | --- | --- | --- |
| **0**      | X   | 0   | 1   | X   |
| **1**      | X   | 0   | X   | X   |

**R**

![[JK-SR.png]]

## D -> J-K flip-flop
During the conversion of flip-flop a combination circuit is used to combine the desired input of the flip-flop to the given input of the flip-flop

--Characteristic table--

| J   | K   | $Q_{n}$ | $Q_{n+1}$ | D   |
| --- | --- | ------- | --------- | --- |
| 0   | 0   | 0       | 0         | 0   |
| 0   | 0   | 1       | 1         | 1   |
| 0   | 1   | 0       | 0         | 0   |
| 0   | 1   | 1       | 0         | 0   |
| 1   | 0   | 0       | 1         | 1   |
| 1   | 0   | 1       | 1         | 1   |
| 1   | 1   | 0       | 1         | 1   |
| 1   | 1   | 1       | 0         | 0   |


for D

| J\K$Q_{n}$ | 00  | 01  | 11  | 10  |
| ---------- | --- | --- | --- | --- |
| **0**      | 0   | 1   | 0   | 0   |
| **1**      | 1   | 1   | 0   | 1   |

$\LARGE \overline{K}Q_{n} + J\overline{Q_{n}}$

![[DJK.png]]

## traggering of flip-flop
In level tragegred the chnage in the input will be reflected in the output
