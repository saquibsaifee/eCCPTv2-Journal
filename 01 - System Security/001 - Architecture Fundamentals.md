Purpose:
	Fundamentals to improve fuzzing, exploit development, buffer overflows, debugging, reverse engineering and malware analysis.

**CPU, ISA, and Assembly**
Central Process Unit(CPU) is the device in charge of executing machine code of a program.

The machine code, or machine language, is the set of instructions that the CPU processes.

Each instruction is primitive command that execute a specific operation such as move, change execution flow, arithmetic or logic operation and others.

CPU instructions are in HEX and impossible for humans to comprehend.

Therefore, the same machine code gets translated into mnemonic code(more human readable language); this is called as assembly language (ASM). The two most popular are NASM(Netwide Assembler) and MASM (Microsoft Macro Assembler).

![[Pasted image 20220922080024.png]]

Each CPU has its own Instruction Set Architecture (ISA). The ISA is set of instructions that a program (or a compiler) must understand and use to write a program correctly for that specific CPU and machine.
Basically ISA is what a programmer can see: memory, registers, instructions, etc. It provides all the necessary information for who wants to write a program in that machine language.

One of the most common ISA is the x86 instruction set( or architecture) originated from the intel 8086

x86 is an acronym for 32-bit processors, while x86_64 or AMD64 is for 64-bit.

**Registers**
32 or 64 bits refers to the width of the CPU register. Each CPU has its fixed set of register that are accessed when required. You can think it as temp variable used by CPU to get and store data.

Registers are small portions of memory in the CPU and server to store data temporarily.

Eight General Purpose Registers(GPRs)
![[Pasted image 20220922081830.png]]

E means Extended in the register names.

In 64-bit E is replaced with R

Register naming convention between 8, 16, 32, and 64 bit registers
![[Pasted image 20220922082159.png]]

One important additional register is **Extended Instruction Pointer (EIP)**, x86 naming. EIP controls the programing execution by storing a pointer to the address of the next instruction(machine code) that will be executed. It is same as Program Counter (PC).
*It tells the CPU where the next instruction is*

**Process Memory**
![[Pasted image 20220922084212.png]]

The process is divided in 4 regions: Text, Data, The Heap, and the Stack.

**Text region**, or instruction segment, is fixed by the program and contains the program code(instructions). This region is marked as read-only since the program should not change during the execution.

**Data region** is divided into Initialized and uninitialized variable.
Initialized data includes items such as static and global variable that pre-defined and can be modified.
**Uninitialized data**, named as Block Started by Symbol (BSS), also initializes variables that are initialized to zero or do not have explicit initialization. (ex. static int t)

**Heap Region** 
During the execution program can request more space in memory....

**Stack**
Stack is a last in first out(LIFO) block of memory. It is located in the higher part of the memory. You can think of the stack as an array used for saving a function's return address, passing function arguments, and storing local variables.

The purpose of the ESP(Stack pointer) is to identify the top of the stack, and it is modified each time a value is pushed in (PUSH) or popped out(POP)

Stack grows from the end of memory and grows downward(lower address)

A **push** will subtracts 4(32bit) or 8(64bit) and add the values of push there. Subtract as stack grow to lower memory, adding will go toward higher memory.

![[Pasted image 20221008163431.png]]

Pop will do opposite. It will store the value of top of the stack ESP into for e.g. in EAX and increment the by 4/8
![[Pasted image 20221008163818.png]]

**Stack Frames**
Prologue, it sets the stack to be used.
Epilogue, it resets the stack to the prologue settings.

Stack consists of logical stack frames(portions/areas of the stack), that are PUSHed when calling a function and POPed when returning a value.

Whenever a subroutine, a function or a procedure, is started, a stack frame is created and assigned to the current ESP(top of the stack). This allow subroutine to operate independently in its own location in the stack.

When the subroutine ends, two things happen:
1. Program receives the parameter passed from the subroutine.
2. EIP is reset to the location at the time of the initial call.

In other words, the stack frame keep the track of the location where each subroutine should return the control when it terminates.

When the program starts it first push the parameters of function into the stack from right to left.
Now processor PUSHes the content of EIP into the stack and points to the first byte after the CALL instruction. We need the location of next instruction.
Now we have to create a new stack frame for that we need to store the location of the main() stack frame, will do this by initializing ESP and EBP.
![[Pasted image 20221008185005.png]]


**Prologue**
![[Pasted image 20221008185052.png]]

push EBP - saves the old base pointer onto the stack. it will be pointing on the top of the stack of previous stack frame.

mov EBP, ESP - will copy the value of ESP into the EBP.
	in assembly: move means copying value from right to the left placed place.
this creates a new stack frame on top of the stack.

sub ESP, x - increment the stack pointer by x value. sub because we have to subtract by 4/8 from ESP in order to grow as the stack grows toward the lower address.
![[Pasted image 20221008185639.png]]


This is end of prologue now the program will be loaded into the stack.
![[Pasted image 20221008185918.png]]


When the program enters a function, the prologue is executed to create a new stack frame.

**Epilouge:**
Same way, once the program executes a return statement, the previous stack frame is restored by the help of Epilogue.
![[Pasted image 20221008190314.png]]

![[Pasted image 20221008190305.png]]


**Endianness:**

MSB - Most significant bit (leftmost value)
	1 is MSB of 100
LSB - Least significant bit (rightmost value)
	1 is LSB of 001
	
Big and Little Endianness.

In Big endianness the LSB is stored at the highest memory address while MSB is stored at the Lowest memory address.
e.g 0x12345678
![[Pasted image 20221008190935.png]]

It is the other way in little-endian representation.
![[Pasted image 20221008190922.png]]

**NOP**
NOP is No operation instruction. It is assembly language instruction which does nothing. When program encounters a NOP it will skip to the next instruction. In intel x86 it is denoted by x90.
![[Pasted image 20221008191153.png]]

