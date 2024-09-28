# General Register Organization

- When a large number of registers are included in the CPU,
it is most efficient to connect them through a common bus system.

Control Word
---
SELA, SELB, SELD OPR are control word.
Control Word  is of 14 bit

|SELA|SELB|SELD|OPR|
|-|-|-|-|
|3 bit|3 bit|3 bit|5 bit|


Operation of Control Unit
---
- The control unit directs the information flow through the registers and ALU
by selecting various components in the system

- Example: R1 -> R2 + R3
    1. MUX A selector (SELA): BUS A <- R2
    2. MUX B selector (SELB): BUS B <- R3
    3. ALU operation selector (OPR): ALU to ADD
    4. Decoder destination selector (SELD): R1 <- Output Bus

Encoding of register selection fields
---

| Binary Code | SELA      | SELB      | SELD       |
| ----------- | --------- | --------- | ---------- |
| -           | **Input** | **Input** | **Output** |
| 001         | R1        | R1        | R1         |
| 010         | R2        | R2        | R2         |
| 011         | R3        | R3        | R3         |
| 100         | R4        | R4        | R4         |
| 101         | R5        | R5        | R5         |
| 110         | R6        | R6        | R6         |
| 111         | R7        | R7        | R7         |

# ALU Unit
Encoding of ALU operations
---

|OPR select|Operation|Symbol|
|-|-|-|
|00000|Transfer A|TSFA|
|00001|Increment A|INCA|
|00010|ADD A+B|ADD|
|00101|SUBTRACT A-B|SUB|
|00110|DECREMENT A|DECA|
|01000|AND A and B|AND|
|01010|OR A and B|OR|
|01010|OR A and B|OR|
|01100|XOR A and B|XOR|
|01110|COMPLIMENT A|COMA|
|10000|SHIFT RIGHT A|SHRA|
|11000|SHIFT LEFT A|SHLA|


