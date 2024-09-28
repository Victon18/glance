# Binary (Array) Multiplier:
---
Multiplication of binary numbers is performed in the same way as multiplication of decimal numbers.
The multiplicand is multiplied by each bit of the multiplier, starting from the least significant bit.
# booth algorithm

- Booth algorithm gives a procedure for multiplying binary integers in signed-2’s complement representation.
- Booth algorithm requires examination of the multiplier bits and shifting of the partial product.
- Prior to the shifting, the multiplicand may be added to the partial product,
subtracted from the partial product, or left unchanged according to the following rules:
    1. The multiplicand is subtracted from the partial product
    upon encountering the first least significant 1 in a string of 1's in the multiplier.
    2. The multiplicand is added to the partial product
    upon encountering the first 0 (provided that there was a previous 1) in a string of 0's in the multiplier.
    3. The partial product does not change when the multiplier bit is identical to the previous multiplier bit.
- The algorithm works for positive or negative multipliers in 2's complement representation.
This is because a negative multiplier ends with a string of 1's and the last operation will be a subtraction of the appropriate weight.

Hardware Implementation of booth's algorithm
---

1. The sequence counter SC is initially set to a number equal to the number of bits in the multiplier.
2. The counter is decremented by 1 after forming each partial product.
3. When the content of the counter reaches zero, the product is formed and the process stops.
4. The multiplier and multiplicand are stored in the `QR` and `BR` registers respectively.
5. $Q_{n}$ designates the least significant bit of the multiplier in register `QR`.
6. An extra flip-flop $Q_{n+1}$is appended to `QR` to facilitate a double bit inspection of the multiplier.

Example (-15)X-8

-5  -> BR = 1011
    $\overline{BR}+1$ = 0101
-7 -> $Q_{R}$ = 1001 in two's compliment

| $Q_{n}$ | $Q_{n+1}$ | AC       | BR & $\overline{BR}+1$ | $Q_{R}$ | $Q_{n+1}$ | SC  |
| ------- | --------- | -------- | ---------------------- | ------- | --------- | --- |
| -       | -         | -        | 00000                  | 1001    | 0         | 100 |
| 1       | 0         | subtract | 0000+0101=0101         | -       | -         | -   |
| -       | -         | ashr     | 0010                   | 1100    | 1         | 011 |
| 0       | 1         | add      | 0010+1011=1101         | -       | -         | -   |
| -       | -         | ashr     | 1110                   | 1110    | 0         | 010 |
| 0       | 0         | ashr     | 1111                   | 0111    | 0         | 001 |
| 1       | 0         | subtract | 1111+0101=0100         | -       | -         | -   |
| -       | -         | ashr     | 0010                   | 0011    | 1         | 000 |

hence the answer is = 00100011 -> 35
