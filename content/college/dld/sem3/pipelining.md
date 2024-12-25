# Multiprocessing
- Multiprocessor systems have multiple processors working in parallel and share the computer clock, memory, bus, peripheral devices etc.
- To improve the performance of a CPU we have two options:
    1. Improve the hardware by introducing faster circuits.
    2.  Arrange the hardware such that more than one operation can be performed atthe same time.
- There is a limit on the speed of hardware and the cost of faster circuits is quite high.


# Multiprogramming
- It is a rudimentary form of parallel processing in which several programs run at the same time on a uniprocessor system.
- The purpose of multiprogramming is to maximise CPU time

## Types of Multiprocessors

1. Symmetric Multiprocessors
---
- Each processor contains a similar copy of the operating system and they all communicate with each other.
- All the processors arein a peer to peer relationship i.e. no master-slave relationship exists between them.

---
2. Asymmetric Multiprocessors
---
- In asymmetric systems, each processor is given a predefined task.
- There is a master processor that gives instruction to all the otherprocessors.
- It contains a master slave relationship

---
# pipelining
- Pipelining is a technique of decomposing a sequential process into sub-operations.
- Here each sub-process is being executed in a segment that operates concurrently with all other segment.
- Simultaneous execution of more than one instruction takes place in a pipelined processor.
- Pipelining improves system performance.

3 stages of Instruction pipeline
---
- Fetch
- Decode
- Execute


## operations in each pipeline stage

example :- $A_{i} \times B_{i}+C_{i}$ for i = 10 times

1. Segment 1 :- $A_{i}\to R_{1};B_{i}\to R_{2}$
2. Segment 2 :- $R_{1}\times R_{2}\to R_{3};C_{i}\to R_{4}$
3. Segment 3 :- $R_{3}+R_{4}\to R_{5}$

<table>
    <tr><td rowspan= "2">Clock pulse number</td><td colspan="2">Segment 1</td><td colspan="2">Segment 2</td><td colspan="2">Segment 3</td></tr>
    <tr><td>R1</td><td>R2</td><td>R3</td><td>R4</td><td colspan="2">R5</td></tr>
    <tr><td>1</td><td>A1</td><td>B1</td><td>--</td><td>--</td><td colspan="2">--</td></tr>
    <tr><td>2</td><td>A2</td><td>B2</td><td>A1*B1</td><td>C1</td><td colspan="2">--</td></tr>
    <tr><td>3</td><td>A3</td><td>B3</td><td>A2*B2</td><td>C2</td><td colspan="2">A1*B1+C1</td></tr>
    <tr><td>4</td><td>A4</td><td>B4</td><td>A3*B3</td><td>C3</td><td colspan="2">A2*B2+C2</td></tr>
    <tr><td>5</td><td>A5</td><td>B5</td><td>A4*B4</td><td>C4</td><td colspan="2">A3*B3+C3</td></tr>
    <tr><td>6</td><td>A6</td><td>B6</td><td>A5*B5</td><td>C5</td><td colspan="2">A4*B4+C4</td></tr>
    <tr><td>7</td><td>A7</td><td>B7</td><td>A6*B6</td><td>C6</td><td colspan="2">A5*B5+C5</td></tr>
    <tr><td>8</td><td>--</td><td>--</td><td>A7*B7</td><td>C7</td><td colspan="2">A6*B6+C6</td></tr>
    <tr><td>9</td><td>--</td><td>--</td><td>--</td><td>--</td><td colspan="2">A7*B7+C7</td></tr>
</table>

## General Four-Segment Pipeline
- Each segment consists of a combinational circuit Si that performs a suboperation over the data stream flowing through the pipe.
- The segments are separated by registers Ri that hold the intermediate results between the stages.

## space-time diagram
- The behavior of a pipeline can be illustrated with a space-time diagram.
- This is a diagram that shows the segment utilization as a function of time.
- Ex: Four segments and six tasks. The time required to complete all the operations is 4 + (6 - 1) = 9 clock cycles.
    1. The diagram shows six tasks T1 through T6 executed in four segments.
    2. Initially, task T1 is handled by segment 1.
    3. After the first clock, segment 2 isbusy with T1, while segment 1 is busy with task T2.
    4. Continuing in this manner, the first task T1 is completed after the fourth clock cycle.

|Segment\Clock cycle|1|2|3|4|5|6|7|8|9|
|--|--|--|--|--|--|--|--|--|--|
|1|T1|T2|T3|T4|T5|T6|--|--|--|
|2|--|T1|T2|T3|T4|T5|T6|--|--|
|3|--|--|T1|T2|T3|T4|T5|T6|--|
|4|--|--|--|T1|T2|T3|T4|T5|T6|

# pipeline speed up
1. for pipelined
---
- the first task t1 requires time -> $k\times t_{p}$
- now remaining (n-1) task require -> $(n-1)\times t_{p}$
- to complete n tasks with k segment pipeline -> $k+(n-1)$ clock cycle
---
2. for non-pipelined
---
- time required to complete each task -> $t_{n}$
- time required to complete n task -> $n\times t_{n}$

$$\large
\begin{align}
\text{Speed up} &= \frac{n\times t_{n}}{[k+(n-1)]t_{p}}\\
\text{(Speed up)}_{max} &= \frac{t_{n}}{t_{p}}
\end{align}
$$
