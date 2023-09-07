
+ Authors: **Alejandro Calderón Mateos & Felix García Carballeira**
+ License: [GPLv3.0](https://github.com/wepsim/wepsim.github.io/blob/master/LICENSE)


# Laboratory 2: microprogramming a compact instruction set

The main goal of this laboratory is to learn how to design an instruction set for a computer.
The main knowledge to be practiced are microprogramming, assembly programming and information representation.

For the development of the laboratory, it is necessary to review the following concepts:
  * The representation of integers, character strings, etc.
  * The main aspects of the assembly language.
  * The instruction format and addressing types.
  * The operation of a processor, including the stages of execution, microprogramming, etc.

The student is going to use the WepSIM simulator to be able to exercise in an interactive way the concepts and knowledge indicated above.

This laboratory consists of 2 exercises that you can develop and test in <a href="https://wepsim.github.io/wepsim/">WepSIM</a>.


## Exercise 1
 
The company we are work with request you to **design, implement and test** a new instruction set similar to the RISC-V instruction set, using the WepSIM simulator. Instructions are listed in Table 1. The instructions will be encoded in 32 bits.

<html>
<table style="border: 1px solid black; border-collapse: collapse; border-style: dotted" cellpadding="5">
<tr    style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<th> Instruction </th>
<th> Format </th>
<th> Associated functionality </th>
<th> Status register </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  lui RRE1, U32 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  CO (31-26): 010010<br>RRE1 (25-21)<br>U32 (63-32) </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  BR[RRE1] ← U32 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Not updated </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  sw RRE1, (RRE2) </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  CO (31-26): 010000<br>RRE1 (25-21)<br>RRE2 (20-16) </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Memory[RRE1] ← BR[RRE2] </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Not updated </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  lw RRE1, (RRE2)      </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  CO (31-26): 010011<br>RRE1 (25-21)<br>RRE2 (20-16) </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  BR[RRE1] ←Memory[RRE2] </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Not updated </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  add RRE1, RRE2, RRE3 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  CO (31-26): 011000<br>RRE1 (25-21)<br>RRE2 (20-16)<br>RRE3 (15-11)<br> </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  BR[RRE1]  ← BR[RRE2]  + BR[RRE3]   </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Updated </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  addi RRE1, RRE2, S16 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  CO (31-26): 011010<br>RRE1 (25-21)<br>RRE2 (20-16)<br>S16 (15-0) </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  BR[RRE1] ←BR[RRE2] +S16 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Updated </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  neg RRE1, RRE2 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  CO (31-26): 011011<br>RRE1 (25-21)<br>RRE2 (20-16) </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  BR[RRE1]  ← 0 -  RRE2 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Updated </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  bnz S16 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  CO (31-26): 110011<br>S16  (15-0) </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  IF (SR. Z)<br>PC ← PC + S16 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Not updated </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  beq RRE1, RRE2, S10  </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  CO (31-26): 110100<br>RRE1 (25-21)<br>RRE2 (20-16)<br>S10 (9-0) </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  IF (RRE1  x RRE2)<br>PC ← PC + S10 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Not updated </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  jto RRE1 U16 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  CO (31-26): 100001<br>RRE1 (25-21)<br>U16 (15-0) </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  BR[RRE1] ← PC<br>PC ← U16 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Not updated </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  jr RRE1 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  CO (31-26): 100010<br>RRE1 (25-21) </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  PC ← BR[RRE1] </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Not updated </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  halt </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  CO (31-26): 100011 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  PC ← 0x00<br>SR ← 0x00 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Not updated </td>
</tr>
</table>
</html>

<br>
<html><center><em>Table 1.- RISC-V-like instruction set</em></center></html>

The notation used for the instructions is the following one:
 * U32 refers to a 32-bit unsigned integer.
 * U16 to a 16-bit unsigned integer.
 * S16 to a 16-bit signed integer.
 * S10 to a 10-bit signed integer value. 
 * RRE will be used to denote RISC-V general purpose registers, which in this 32-bit version are 32 registers of 32-bit each. BR will be used to refer to the Register File, and BR[RRE1] to indicate the contents of the RRE1 register. The integers stored in register are two complements 32 bits integers.
 * MEMORY[R] refers to the contents of the memory position whose address is stored in the R register.

The values "S16/S10" indicate that sign extension must be made while in "U16" no sign extension is made (filled with leading zeros).

The following is the mapping between RISC-V registers and WepSIM registers. This association must be indicated in the register section of the microcode of the requested instructions.

<html>
<table style="border: 1px solid black; border-collapse: collapse; border-style: dotted" cellpadding="5">
<tr>
<th colspan="2"> RISC-V </th>
<th> WepSIM register </th>
<th> Meaning </th>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted"> x0 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted"> zero </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted"> R0 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted"> Contains a zero </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted"> x1 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted"> ra </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted"> R1 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted"> Call Return vAddress     </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  x2 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  sp </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  R2 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Stack pointer </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  x3 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  gp </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  R3 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Global pointer </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  x4 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  tp </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  R4 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Thread pointer </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  x5 ... x7 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  t0 ... t2       </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  R5 ... R7 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Temporary Records (1/2)  </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  x8 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  fp </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  R8 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Stack frame </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  x9 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  s1 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  R9 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Record saved </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  x10 ... x11 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  a0 ... a1 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  R10 ... R11 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Argument for functions (1/2) and return values </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  x12 ... x17 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  a2 ... a7 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  R12 ... R17 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Function Argument (2/2)  </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  x18 ... x27 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  s2 ... s11 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  R18 ... R27 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Registers saved </td>
</tr>
<tr style="border: 1px solid black; border-collapse: collapse; border-style: dotted">
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  x28... x31 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  t3 ... t6 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  R28 ... R31 </td>
<td style="border: 1px solid black; border-collapse: collapse; border-style: dotted">  Temporary Records (1/2)  </td>
</tr>
</table>
</html>
<br>
<html><center><em>Table 2.- RISC-V registers</em></center></html>


Each registers has two names and when programming it is possible to use both x0 or zero, x1 or ra, etc.
For the main control registers:
 * The stack pointer register (sp) is the R2 register in the WepSIM elementary processor.
 * The status register is the SR register in the WepSIM processor.
 * The PC registry is the program counter register. 

WepSIM RT1, RT2, and RT3 registers are transparent to the assembler programmer.

In order to pass arguments to a subroutine in our RISC-V assembler, the a0... a7 registers will be used, and the a0 and a1 registers will be used to return results (one value in a0, and for two values a0 and a1). 
In the case of our RISC-V, passing more than eight arguments to a subroutine, from ninth to last of the arguments would be passed on the stack.
Consider that a subroutine has to keep the value within registers s0... s11, sp, fp and ra between calls.

The results of this exercise are related to the design of the microcode (memory of laboratory) and the microcode itself (mc file for WepSIM).
A valid implementation that minimizes the number of clock cycles will be assessed, briefly justifying in memory the design decisions that have been made to achieve this.


## Exercise 2

To test the instructions of the exercise 1 you can encode the programs that you deem appropriate.
However, the company asks us to carry out a program in assembler (in order to make a demonstration) that uses the RISC-V instruction set requested in exercise 1.

The program to be encoded, using the RISC-V statements designed in the previous section, will have the same functionality as that of the following program written in high-level language:

```c++
int32 vector[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 } ;

int sumav ( int32 neltos, int32 *vector )
{
     int32 v0 = 0 ;
     for (int32 i=0; i<neltos; i++) {
            v0 = v0 + vector[i] ;
     }
     return v0 ;
}

int main ( int argc, char *argv[] )
{
     int32 ret = sumav(10, vector) ;
     exit(0) ;
}
```

This program has a **sumav** routine that receives two arguments: the number of elements of an integer vector and the start direction of that integer vector.
The routine returns the sum of the numbers contained in the vector passed by argument. 
There is also a **main** routine that takes care of calling the **sumav** routine and ending the program.
Note the registers used in the convention for argument passing on this RISC-V are described at the end of Exercise 1.

The results of this exercise must be indicated both, the part of the memory corresponding to this exercise and in the file associated with the requested functionality.


# Extra material

### Example
You can find extra material in this example within WepSIM: <a href="https://acaldero.github.io/wepsim/ws_dist/?mode=ep&examples_set=RISCV&example=21">Example 21</a>.


### Save a _checkpoint_ with WepSIM

WepSIM allows you to save the entire working session into a single file. This session can include the requested microcode, the assembly code, the states at different execution points, and a recording of the work session. In this way it is more agile to continue the work or share that work among members of the laboratory group.

To do this you have to use what in the WepSIM simulator is called _checkpoint_. The following are the steps to save a checkpoint:
* In the run mode menu select the _"Checkpoint"_ option.
* Enter the file name in the "File name:" field, then press the "Save" button to save the file.
* **Check that the file has been saved correctly and contains everything ordered in the statement.**

