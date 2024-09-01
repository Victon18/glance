# shift registers
register is a kind of memory

# serial in and serial out register (SISO)
## 4 bit shift register

example -> 1011

| CP  | Q0  | Q1  | Q2  | Q3  | status   |
| --- | --- | --- | --- | --- | -------- |
| -   | 0   | 0   | 0   | 0   | empty    |
| 1st | 1   | 0   | 0   | 0   | storing  |
| 2nd | 1   | 1   | 0   | 0   | storing  |
| 3rd | 0   | 1   | 1   | 0   | storing  |
| 4th | 1   | 0   | 1   | 1   | stored   |
| 5th | 0   | 1   | 0   | 1   | removing |
| 6th | 0   | 0   | 1   | 0   | removing |
| 7th | 0   | 0   | 0   | 1   | removing |
| 8th | 0   | 0   | 0   | 0   | empty    |

we need 'n' clock cycle for data in ; n = no of bits in data

![[SISO.png]]

# serial in parallel out (SIPO)

![[SIPO.png]]


| CP  | Q0  | Q1  | Q2  | Q3  | status           |
| --- | --- | --- | --- | --- | ---------------- |
| -   | 0   | 0   | 0   | 0   | empty            |
| 1st | 1   | 0   | 0   | 0   | storing          |
| 2nd | 1   | 1   | 0   | 0   | storing          |
| 3rd | 0   | 1   | 1   | 0   | storing          |
| 4th | 1   | 0   | 1   | 1   | stored           |
| 5th | 0   | 0   | 0   | 0   | parallel-removed |

# parallel in serial out (PISO)

![[PISO.png]]

example -> 1101

| CP  | Q0  | Q1  | Q2  | Q3  | status          |
| --- | --- | --- | --- | --- | --------------- |
| -   | 0   | 0   | 0   | 0   | empty           |
| 1st | 1   | 1   | 0   | 1   | parallel-stored |
| 2nd | 0   | 1   | 1   | 0   | removing        |
| 3rd | 0   | 0   | 1   | 0   | removing        |
| 4th | 0   | 0   | 0   | 1   | removing        |
| 5th | 0   | 0   | 0   | 0   | empty           |

(n+1) cycle for in and out data

# parallel in parallel out (PIPO)

![[PIPO.png]]


| CP  | Q0  | Q1  | Q2  | Q3  | status           |
| --- | --- | --- | --- | --- | ---------------- |
| -   | 0   | 0   | 0   | 0   | empty            |
| 4th | 1   | 0   | 1   | 1   | parallel-stored  |
| 8th | 0   | 0   | 0   | 0   | parallel-removed |

# universal shift register

A -> Shift the data to the right
B -> Shift the data to the left
C -> parrallel in parallel out
D -> Hold operation

| S1  | S0  | operation   |
| --- | --- | ----------- |
| 0   | 0   | hold        |
| 0   | 1   | shift right |
| 1   | 0   | shift left  |
| 1   | 1   | PIPO        |

![[USR.png]]
