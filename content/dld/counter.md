# asynchronous counter
## up counter

|CLK|Q2|Q1|Q0|
|-|-|-|-|
|1st|0|0|0|
|2nd|0|0|1|
|3rd|0|1|0|
|4th|0|1|1|
|5th|1|0|0|
|6th|1|0|1|
|7th|1|1|0|
|8th|1|1|1|
|9th|0|0|0|
![[UC.png]]

----

![[CLKDW.png]]
## down counter

|CLK|Q2|Q1|Q0|
|-|-|-|-|
|1st|1|1|1|
|2nd|1|1|0|
|3rd|1|0|1|
|4th|1|0|0|
|5th|0|1|1|
|6th|0|1|0|
|7th|0|0|1|
|8th|0|0|0|
|9th|1|1|1|
![[DC.png]]

----

![[CLKUP.png]]

## UP and Down counter

S = 0 -> UP counter
S = 1 -> DOWN counter

![[UDC.png]]
## mod n counter
mod n counter will count from o to n-1A
## mode 6 counter

## mode 10 counter

# synchronous
## up-down counter
M = 0 -> down counting
M = 1 -> up counting
Next state depends upon previous state and M
    4 variable = 0000 -> 1111

<table border = '1px'>
    <tr><th>condition</th><th colspan = '3'>PS</th><th>Mode</th><th colspan = '3'>NS</th><th colspan = '6'>Required excitation</th></tr>
    <tr><th>-</th><th>Q3</th><th>Q2</th><th>Q1</th><th>M</th><th>Q3</th><th>Q2</th><th>Q1</th><th>J3</th><th>K3</th><th>J2</th><th>K2</th><th>J1</th><th>K1</th></tr>
    <tr><th>down</th><th>0</th><th>0</th><th>0</th><th>0</th><th>1</th><th>1</th><th>1</th><th>1</th><th>x</th><th>1</th><th>x</th><th>1</th><th>x</th></tr>
    <tr><th>up</th><th>0</th><th>0</th><th>0</th><th>1</th><th>0</th><th>0</th><th>1</th><th>0</th><th>x</th><th>0</th><th>x</th><th>1</th><th>x</th></tr>
    <tr><th>down</th><th>0</th><th>0</th><th>1</th><th>0</th><th>0</th><th>0</th><th>0</th><th>0</th><th>x</th><th>0</th><th>x</th><th>x</th><th>1</th></tr>
    <tr><th>up</th><th>0</th><th>0</th><th>1</th><th>1</th><th>0</th><th>1</th><th>0</th><th>0</th><th>x</th><th>1</th><th>x</th><th>x</th><th>1</th></tr>
    <tr><th>down</th><th>0</th><th>1</th><th>0</th><th>0</th><th>0</th><th>0</th><th>1</th><th>0</th><th>x</th><th>x</th><th>1</th><th>1</th><th>x</th></tr>
    <tr><th>up</th><th>0</th><th>1</th><th>0</th><th>1</th><th>0</th><th>1</th><th>1</th><th>0</th><th>x</th><th>x</th><th>0</th><th>1</th><th>x</th></tr>
    <tr><th>down</th><th>0</th><th>1</th><th>1</th><th>0</th><th>0</th><th>1</th><th>0</th><th>0</th><th>x</th><th>x</th><th>0</th><th>x</th><th>1</th></tr>
    <tr><th>up</th><th>0</th><th>1</th><th>1</th><th>1</th><th>1</th><th>0</th><th>0</th><th>1</th><th>x</th><th>x</th><th>1</th><th>x</th><th>1</th></tr>
    <tr><th>down</th><th>1</th><th>0</th><th>0</th><th>0</th><th>0</th><th>1</th><th>1</th><th>x</th><th>1</th><th>1</th><th>x</th><th>1</th><th>x</th></tr>
    <tr><th>up</th><th>1</th><th>0</th><th>0</th><th>1</th><th>1</th><th>0</th><th>1</th><th>x</th><th>0</th><th>0</th><th>x</th><th>1</th><th>x</th></tr>
    <tr><th>down</th><th>1</th><th>0</th><th>1</th><th>0</th><th>1</th><th>0</th><th>0</th><th>x</th><th>0</th><th>0</th><th>x</th><th>x</th><th>1</th></tr>
    <tr><th>up</th><th>1</th><th>0</th><th>1</th><th>1</th><th>1</th><th>1</th><th>0</th><th>x</th><th>0</th><th>1</th><th>x</th><th>x</th><th>1</th></tr>
    <tr><th>down</th><th>1</th><th>1</th><th>0</th><th>0</th><th>1</th><th>0</th><th>1</th><th>x</th><th>0</th><th>x</th><th>1</th><th>1</th><th>x</th></tr>
    <tr><th>up</th><th>1</th><th>1</th><th>0</th><th>1</th><th>1</th><th>1</th><th>1</th><th>x</th><th>0</th><th>x</th><th>0</th><th>1</th><th>x</th></tr>
    <tr><th>down</th><th>1</th><th>1</th><th>1</th><th>0</th><th>1</th><th>1</th><th>0</th><th>x</th><th>0</th><th>x</th><th>0</th><th>x</th><th>1</th></tr>
    <tr><th>up</th><th>1</th><th>1</th><th>1</th><th>1</th><th>0</th><th>0</th><th>0</th><th>x</th><th>1</th><th>x</th><th>1</th><th>x</th><th>1</th></tr>
</table>


![[S-U-D-SD.png]]

$\large J_{3} = \overline {Q_{2}.Q_{1}.M} + Q_{2}.Q_{1}.M$
$\large K_{3} = \overline {Q_{2}.Q_{1}.M} + Q_{2}.Q_{1}.M$
$\large J_{3} = \overline {Q_{1}.M} + Q_{1}.M$
$\large J_{3} = \overline {Q_{1}.M} + Q_{1}.M$


![[S-U-D.png]]