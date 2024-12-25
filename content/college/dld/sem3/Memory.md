# Memory Hierarchy
- Memory stores instruction and data

1. Main Memory(RAM)
---
- Memory that communicates directly with the CPU

|Static|Dynamic|
|-|-|
|Transistor|Seperate capacitors|
|Faster|Slower|
|Expensive|Cheap|
|Does not require refreshing |Refreshing to retain data|
|Used in cache memory|Used in main memory|

---
2. Auxiliary Memory
---
- Devices that provide backup
- Magnetic disks and tapes are most common aux memory
- These store system programs, large data set and other backup information
---
3. Registers
---
- Hold data for immediate CPU instruction
- These have faster access time
---
4. Cache Memory
---
- Very special high speed memory to increase the processing time
---
# Memory management system
- Supervises the flow of data between auxiliary and main memory
# Chips
## RAM  Chip
- Size of RAM = 128 word X 8 data bits
- 128 words = 2^{7}; Address bit = 7
- Bidirectional data bus allows transfer of data from
    1. Memory -> CPU during read operation
    2. CPU -> Memory during write operation
- High impedence state behaves like an open cicuit, output does not carry a signal and has no logic signification.

|CS1|CS2|RD|WR|Memory function|State of data bus|
|-|-|-|-|-|-|
|0|0|X|X|Inhibit|High impedence|
|0|1|X|X|Inhibit|High impedence|
|1|0|0|0|Inhibit|High impedence|
|1|0|0|1|Write|Input data to RAM|
|1|0|1|X|Read|Output data from RAM|
|1|0|0|0|Inhibit|High impedence|

## ROM Chip
- Size of ROM = 512 word X 8 data bits
- 512 words = 2^{9}; Address bit = 9
- Data bus is only in output mode cause ROM only read.
- For same size chip, there are more bits ROM, bcuz internal binary cells occupy less space.
- Chip is only enabled when CS = 1 and CS = 0. It will do read operation.

# Memory address map
- Assume computer needs 1024 bytes of memory (1024 X 8 )
- ie RAM(512 byte) + ROM(512 byte){1024/2=512}
- 11 -> 16 are always 0.

$$\large
\begin{align}
\text{No. of RAM chips}=\frac{\text{Total capacity of RAM}}{\text{Capacity of single chip}}=\frac{512}{128} = 4 chips\\
\text{No. of ROM chips}=\frac{\text{Total capacity of ROM}}{\text{Capacity of single chip}}=\frac{512}{512} = 1 chips\\
\end{align}
$$

<table>
<tr><td>Component</td><td>Decimal address</td><td>Hexadeciaml address</td>
<td colspan="10">Address bar</td></tr>
<tr><td>-</td><td>-</td><td>-</td><td>10</td><td>9</td><td>8</td><td>7</td><td>6</td><td>5</td>
<td>4</td><td>3</td><td>2</td><td>1</td></tr>
<tr><td>RAM1</td><td>000-127</td><td>0000-007f</td><td>0</td><td>0</td><td>0</td><td>X</td>
<td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr>
<tr><td>RAM2</td><td>128-225</td><td>0080-00ff</td><td>0</td><td>0</td><td>1</td><td>X</td>
<td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr>
<tr><td>RAM3</td><td>256-383</td><td>0100-017f</td><td>0</td><td>1</td><td>0</td><td>X</td>
<td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr>
<tr><td>RAM4</td><td>384-511</td><td>0180-01ff</td><td>0</td><td>1</td><td>1</td><td>X</td>
<td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr>
<tr><td>ROM</td><td>512-1024</td><td>0200-03ff</td><td>1</td><td>X</td><td>X</td><td>X</td>
<td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr>
</table>

# Cache Memory
- It is a very fast memory
- It keeps the most frequently assecced instance and data
## Terminolgy
- Hit :- If CPU finds the word in the cache
- Miss :- If the CPU cannot find the word in the cache
- Hit ratio
----
- The ratio of number  of pages hits divided by the total CPU reference to the memory
----
- Miss ratio
---
- The ratio of number  of pages miss divided by the total CPU reference to the memory
----
- Average Access Time
---
$\large \text{average access time}=H\times T_{c}+(1-H)(T_{c}+T_{m})

- `H` = Hit ratio
- $T_{c}$ = Time access of cache
- $T_{m}$ = Time access of main memory

---
- Effective Access Time

## Types of Mapping of cache memory
- The transformation of data from main memory to cache memory
- Sub parts in main memory = blocks
- Sub parts in main memory = line
- If a line is previously taken up by a memory block when a new block needs to be loaded, the old block is trashed.
- Physical address consiists of Block number + Block offset(size)
### Example
- Suppose 128 words of main memory is to be mapped with 16 words chache memory (4 word in each block).
- words are minimum addressable unit of memory
- No of blocks = $\frac{128}{4}$=32 blocks (ie 0-31)
- Line size = Block size
- No of lines = $\frac{\text{word of cache}}{\text{line size}}=\frac{16}{4}$=4 lines
- Physical address size = log total words in MM = 128 = $2^{7}$ = 7 bits
- 7 bits = 5 bits block number + 2 bits block offset as 2 bits can represent 4 words

### Direct Mapping
- we assign each memory block to a specific line in the cache.
- An address space is split into two parts index field and a tag field.
- The cache is used to store the tag field whereas the rest is stored in the main memory.
- Direct mapping`s performance is directly proportional to the Hit ratio.
----
- `i = j%m`
- i = cache line number
- j = main memory block number
- m = number of lines in the cache(4)
----
#### exmaple
- for above example
$$
B_{0}\mod4=0;B_{2}%4=2;B_{4}%4=0
$$

- Block 0 resides in line 0 ; block 2 resides in line 2; Block 4 resides in line 4
- Physical address to cache address
    - Block number + Block offset --> Tag + Line number + Block offset
    - 7 bits = 5 block no + 2 block offset -->  3 bits tag + 2 bits line no + 2 bit block offset
- let tag number be 010 and line no be 00 so content in cache is
    1. 010 00 00 --> Word 32 -> 3rd tag; 0th line; 0th word
    2. 010 00 01 --> Word 33 -> 3rd tag; 0th line; 1th word
    3. 010 00 10 --> Word 34 -> 3rd tag; 0th line; 2th word
    4. 010 00 11 --> Word 35 -> 3rd tag; 0th line; 3th word
### Associative Mapping
- Associative memory is used to store the content and addresses of the memory word.
- Any block can go into any line of the cache.
- The word id bits are used to identify which word in the block is needed, but the tag becomes all of the remaining bits.
- This enables the placement of any word at any place in the cache memory.
- It is considered to be the fastest and most flexible mapping form.
- In associative mapping, the index bits are zero.
#### example
- for above example
- Physical address to cache address
    - Block number + Block offset --> Tag + Block offset
    - 7 bits = 5 block no + 2 block offset -->  5 bits tag + 2 bit block offset
- let tag number be 0 and line no be 00 so content in cache is
    1. 00100 00 --> Word 16 -> 4th tag; 0th word
    2. 00100 01 --> Word 17 -> 4th tag; 1th word
    3. 00100 10 --> Word 18 -> 4th tag; 2th word
    4. 00100 11 --> Word 19 -> 4th tag; 3th word

### Set Associative Mapping
- This form of mapping is an enhanced form of direct mapping where the drawbacks of direct mapping are removed.
- Set associative addresses the problem of possible thrashing in the direct mapping method.
- Instead of having exactly one line that a block can map to in the cache, we will group a few lines together creating a set .
- Then a block in memory can map to any one of the lines of a specific set.
- It allows each word that is present in the cache can have two or more words in the main memory for the same index address.
- It combines the best of direct and associative cache mapping techniques.
- In set associative mapping the index bits are given by the set offset bits.
- In this case, the cache consists of a number of sets, each of which consists of a number of lines

----
m = v * k
i= j mod v

where
i = cache set number
j = main memory block number
v = number of sets
m = number of lines in the cache number of sets
k = number of lines in each set

----
#### exmaple
- for above example we will for 2-way set
- Total number of set = $\frac{\text{number of lines}}{k}=\frac{4}{2}=2$
- $B_{0}%2=0;B_{2}%2=0;B_{3}%2=1
- Block 0 resides in set 0 ; block 2 resides in set 0; Block 3 resides in set 1
- Physical address to cache address
    - Block number + Block offset --> Tag + Set number + Block offset
    - 7 bits = 5 block no + 2 block offset -->  4 bits tag + 1 set number + 2 bit block offset
- let tag number be 010 and line no be 00 so content in cache is
    1. 0010 0 00 --> Word 16 -> 2nd tag; 0th line; 0th word
    2. 0010 0 01 --> Word 17 -> 2nd tag; 0th line; 1th word
    3. 0010 0 10 --> Word 18 -> 2nd tag; 0th line; 2th word
    4. 0010 0 11 --> Word 19 -> 2nd tag; 0th line; 3th word
## cache replacement / page replacement
- Replacement algo -> FIFO;LRU;Optimal
- cache miss/cache hit

Write to cache
---
- data is simultaneously updated to cache and memory

Write back
---
- data is updated only in cache
- It is updated in memory when the cache line is ready to be replaced
- Write deffered

Valid bit
---
- indicates wether or not word contains the valid data

Cache initialization
---
- When the power is applied to the computer
- When the main memory is loaded into the computer set of programs from auxiliary memory
- Clearing all valid bits to 0.

# Virtual Memory
