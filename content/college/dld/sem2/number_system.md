# number system
some basic number system are:-

1. binary (base = 2): 0,1
2. octal (base = 8): 0 -> 7
3. hexadecimal (base = 16):  0 -> F
4. decimal (base = 10 : 0 -> 9

| Decimal | Binary | Octal | Hexadecimal |
| ------- | ------ | ----- | ----------- |
| 0       | 0000   | 0     | 0           |
| 1       | 0001   | 1     | 1           |
| 2       | 0010   | 2     | 2           |
| 3       | 0011   | 3     | 3           |
| 4       | 0100   | 4     | 4           |
| 5       | 0101   | 5     | 5           |
| 6       | 0110   | 6     | 6           |
| 7       | 0111   | 7     | 7           |
| 8       | 1000   | 10    | 8           |
| 9       | 1001   | 11    | 9           |
| 10      | 1010   | 12    | A           |
| 11      | 1011   | 13    | B           |
| 12      | 1100   | 14    | C           |
| 13      | 1101   | 15    | D           |
| 14      | 1110   | 16    | E           |
| 15      | 1111   | 17    | F           |

### Number Base conversions
1. binary to octal
---

| Binary | Octal |
| ------ | ----- |
| 000    | 0     |
| 001    | 1     |
| 010    | 2     |
| 011    | 3     |
| 100    | 4     |
| 101    | 5     |
| 110    | 6     |
| 111    | 7     |
Example: 1000100101 -> 1045
001 -> 1
000 -> 0
100 -> 4
101 -> 5

2. octal to binary
---
example : 654 -> 110101100
6 -> 110
5 -> 101
4 -> 100

3. binary to hex
---

| Binary | Hex |
| ------ | --- |
| 0000   | 0   |
| 0001   | 1   |
| 0010   | 2   |
| 0011   | 3   |
| 0100   | 4   |
| 0101   | 5   |
| 0110   | 6   |
| 0111   | 7   |
| 1000   | 8   |
| 1001   | 9   |
| 1010   | A   |
| 1011   | B   |
| 1100   | C   |
| 1101   | D   |
| 1110   | E   |
| 1111   | F   |
example: 10010110101111 -> 25AF
0010 -> 2
0101 -> 5
1010 -> A
1111 -> F

4. hex to binary
---
example : 654A -> 0110010101001010
6 -> 0110
5 -> 0101
4 -> 0100
A -> 1010

5. Binary to Decimal
-----
$1001.01_{2} = [ ( 1 ) × 2^{3}] + [ ( 0 ) × 2^{2}] + [ ( 0 ) × 2^{1}] + [ ( 1 ) × 2^{0}] + [ ( 0 ) × 2^{-1}] + [( 1 ) × 2^{-2}]$
$1001.01_{2} = [ 1 × 8 ] + [ 0 × 4 ] + [ 0 × 2 ] + [ 1 × 1 ] + [ 0 × 0.5 ] + [ 1 × 0.25 ]$
$1001.01_{2} = 9.25_{10}$

6. octal to decimal
----
$4057.06_{8}=4x8^{3}+0x8^{2}+5x8^{1}+7x8^{0}+0x8^{-1}+6x8^{-2}$
$=2048+0+40+7+0+0.0937$
$=2095.0937_{10}$

7. hex to decimal
----
$5C7_{16}=(5x16^{2})+(C x16^{1})+ (7 x16^{0})$
$=1280+192+7$
$=147_{10}$

8. decimal to binary
---
37810 to octal: Successive division:
8 |  378
8 | 47 ---> 2
8 | 5 ---> 7
   0 ---> 5
$\large=572_{8}$
0.9310 to octal :
0.93x8=7.44
0.44x8=3.52
0.53x8=4.16
0.16x8=1.28
$\large=0.7341_{8}$
$\large378.93_{10}=572.7341_{8}$

9. decimal to hex
----
2598.67510
16 |2598
16 |162 --->6
    10 ---> 2
$\large= A26_{16}$

0.67510=0.675x16 ---> 10.8
= 0.800x16 ---> 12.8 ↓
= 0.800x16 ---> 12.8
= 0.800x16 ---> 12.8
$\large=0.ACCC_{16}$
$2598.675_{10} = A26.ACCC_{16}$

10. decimal to binary
----
11. octal to hex
---
 $\large756.603_{8}$

| 7    | 5    | 6    | .   | 6    | 0       | 3    |
| ---- | ---- | ---- | --- | ---- | ------- | ---- |
| 111  | 101  | 110  | .   | 110  | 000 011 |      |
| 0001 | 1110 | 1110 | .   | 1100 | 0001    | 1000 |
| 1    | E    | E    | .   | C    | 1       | 8    |
13. hex to octal

|B |9 |F |. |A |E|-|-|
|-|-|-|-|-|-|-|-|
|1011 |1001 |1111 |. |1010 |1110|-|-|
|101 |110 |011 |111 |. |101 |011 |100|
|5 |6 |3 |7 |.| 5 |3| 4|

Complements
----
1. 1's compliment
2. 2's compliment
3. 9's compliment
4.  10's compliment

Signed and unsigned number
-----

| Decimal | Sign 2‘s comp form Sign | 1‘s comp form Sign | mag form |
| ------- | ----------------------- | ------------------ | -------- |
| +7      | 0111                    | 0111               | 0111     |
| +6      | 0110                    | 0110               | 0110     |
| +5      | 0101                    | 0101               | 0101     |
| +4      | 0100                    | 0100               | 0100     |
| +3      | 0011                    | 0011               | 0011     |
| +2      | 0010                    | 0010               | 0010     |
| +1      | 0011                    | 0011               | 0011     |
| +0      | 0000                    | 0000               | 0000     |
| -0      | --                      | 1111               | 1000     |
| -1      | 1111                    | 1110               | 1001     |
| -2      | 1110                    | 1101               | 1010     |
| -3      | 1101                    | 1100               | 1011     |
| -4      | 1100                    | 1011               | 1100     |
| -5      | 1011                    | 1010               | 1101     |
| -6      | 1010                    | 1001               | 1110     |
| -7      | 1001                    | 1000               | 1111     |
| -8      | 1000                    | --                 | --       |

# Binary codes
1. Weighted Binary codes
----
Weighted binary codes are those which obey the positional weighting principles, each position of the number represents a specific weight.
The binary counting sequence is an example.

- 8421 BCD code ( Natural BCD code):
---
Each decimal digit 0 through 9 is coded by a 4 bit binary no. called natural binary codes.
Because of the 8,4,2,1 weights attached to it.


2. Non weighted codes
---
Non weighted codes are codes that are not positionally weighted.
That is, each position within the binary number is not assigned a fixed value.
Ex: Excess-3 code

- Excess-3 Code
---
Excess-3 is a non weighted code used to express decimal numbers.
The code derives its name from the fact that each binary code is the corresponding 8421 code plus 0011(3).

- Gray Code
---
The gray code belongs to a class of codes called minimum change codes, in which only one bit in the code changes when moving from one code to the next.
The Gray code is non-weighted code, as the position of bit does not contain any weight.

| 1 bit | 2 bit | 3 bit | 4 bit | Decimal | 4 bit binary |
| ----- | ----- | ----- | ----- | ------- | ------------ |
| 0     | 00    | 000   | 0000  | 0       | 0000         |
| 1     | 01    | 001   | 0001  | 1       | 0001         |
| -     | 11    | 011   | 0011  | 2       | 0010         |
| -     | 10    | 010   | 0010  | 3       | 0011         |
| -     | -     | 110   | 0110  | 4       | 0100         |
| -     | -     | 111   | 0111  | 5       | 0101         |
| -     | -     | 101   | 0101  | 6       | 0110         |
| -     | -     | 110   | 0100  | 7       | 0111         |
| -     | -     | -     | 1100  | 8       | 1000         |
| -     | -     | -     | 1101  | 9       | 1001         |
| -     | -     | -     | 1111  | 10      | 1010         |
| -     | -     | -     | 1110  | 11      | 1011         |
| -     | -     | -     | 1010  | 12      | 1100         |
| -     | -     | -     | 1011  | 13      | 1101         |
| -     | -     | -     | 1001  | 14      | 1110         |
| -     | -     | -     | 1000  | 15      | 1111         |

Binary to Gray Conversion
---

1. Gray Code MSB is binary code MSB.
2. Gray Code MSB-1 is the XOR of binary code MSB and MSB-1.
3. MSB-2 bit of gray code is XOR of MSB-1 and MSB-2 bit of binary code.
4. MSB-N bit of gray code is XOR of MSB-N-1 and MSB-N bit of binary code.

(11001)B = (10101)G
1  ---> 1
1 XOR 1 ---> 0
1 XOR 0 ---> 1
0 XOR 0 ---> 0
0 XOR 1 ---> 1

- Gray to Binary

1. Gray Code MSB is binary  code MSB.
2. Gray Code MSB-1 is the XOR of binary code MSB and MSB-1.
3. MSB-2 bit of gray code is XOR of previous result  and MSB-2 bit of binary code.
4. MSB-N bit of gray code is XOR of previous result  and MSB-N bit of binary code.

(10101)G = (11001)B
1 ---> 1
1 XOR 0 ---> 1
1 XOR  1 ---> 0
0 XOR 0 ---> 0
0 XOR 1 ---> 1


# Error detection
Parity
---

| Decimal | 8421 code | Odd parity | Even parity |
| ------- | --------- | ---------- | ----------- |
| 0       | 0000      | 1          | 0           |
| 1       | 0001      | 0          | 1           |
| 2       | 0010      | 0          | 1           |
| 3       | 0011      | 1          | 0           |
| 4       | 0100      | 0          | 1           |
| 5       | 0100      | 1          | 0           |
| 6       | 0110      | 1          | 0           |
| 7       | 0111      | 0          | 1           |
| 8       | 1000      | 0          | 1           |
| 9       | 1001      | 1          | 0           |
Hamming code
---

| P8  | D7  | D6  | D5  | P4  | D3  | P2  | P1  |
| --- | --- | --- | --- | --- | --- | --- | --- |

$P1 = D3 \oplus D5 \oplus D7$
$P2 = D3 \oplus D6 \oplus D7$
$P4 = D5 \oplus D6 \oplus D7$

parity bit
---
Floating point imprecision
---

- Explicit
----
$\large(-1)^{s}*0.M*2^{E}$

- Implicit
----
$\large(-1)^{s}*1.M*2^{E}$