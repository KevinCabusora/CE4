CE4
===

Assembly Language Programming for PRISM

###C3C Kevin Cabusora, Dr. Neebel, ECE281, 3 April 2014
===
Simple Memory Manipulation
===
[Simple Memory Manipulation](Simple Memory Manipulation.psm)

The goal of this program was to store the value $9 in location $B0, $8 in $C4, and $B in $CB.  

In order to implement this program, I first labeled the variables in RAM, using the names A_FIRST, A_SECOND, and A_THIRD.  

I used LDAI, and then used 9 as the first operand.  I did the same with the subsequent values.  

In accordance with the requirement, I made an infinite loop using JMP which just jumped to the last line of the program (which was JMP again).

When tested, the program performed as expected, in that the values in the RAM matched those in the operands.

===
Mathematics
===
[Mathematics](Mathematics.psm)

The goal of this program was retrieve a positive test value from location $B0, double it, subtract 4, and output it to Port 2.  

The first stem was to allow RAM values to be edited.  For my test value, I chose 5.

I then used LDAD to load the operand value of 5 to the accumulator.

I doubled the value by adding the value stored in the operand address to accumulator.  Since the current number stored in the accumulator and the value in the operand address was the same, the value 5 was effectively doubled.  To do this, I used the ADDI function, with 5 as the operand.

The next goal was to subtract 4 from the value in the accumulator.  My process would be to negate the value (10 -> -10), add 4, then negate the value in the accumulator again.

To do this, I took the two’s complement of the value in the accumulator using the NEG function.  

I then added 4 using ADDI with the operand of 4.

Next, I took the two’s complement again with the NEG function to get my final result.

Finally, I used OUT to output the value to Port 2.

Just like the first program, I put a JMP infinite loop at the end.

The program performed as expected, as Port 2 showed the expected result of 6. (5 X 2 – 4 = 6)

===
Loops
===
[Loops](Loops.psm)

The goal for this program was to read a value Input Port 3, display it to Output Port 0, subtract 1 from that value and display it to Port 1, then subtract 1 from Port 1 and display it in Port 2.  The loop would then gradually decrease each Output Port by 1 sequentially.

The first step was to choose Input Port 1, using IN with operand 3.  Next, I made that value output in Port 0 using OUT with operand 0.

The value in Port 0 was then subtracted by 1 by taking the 2’s complement using NEG, using ADDI to add 1, then taking the 2’s complement again and using OUT to display the result in Port 1.

The same process was used in Ports 1 and 2 in sequence.

The next problem was trying to find out the most efficient way of getting a loop of decrements.

To perform this, I would add 1 to the value of OUT 2, then loop back to OUT 0 using the JMP function.

This negated the need for an infinite loop at the end, because the program IS the loop.

When tested the program performed exactly as expected.  Using the test value of 7 in Input 3, the results were 7, 6, 5 for ports 0, 1, and 2, respectively.  Advancing a few more steps led to an output of 6, 5, 4, then 5, 4, 3, then so on.

===
Documentation
===
C3C Kyle Jonas gave some amazing assistance in showing me how an accumulator works, how an operand works, how RAM works, and how all the different functions work.  He gave me these basic tools in order to get started; the programs I wrote are entirely my own.


