Buffer means area where more than one piece of data is stored.

Overflow means overloading the buffer with data more than it is capable of holding.

strcpy in C is vulnerable. whereas, strncpy takes one more argument which is size.

Windows uses little-endian

Some functions vulnerable to buffer overflow:
![[Pasted image 20221116221342.png]]

![[Pasted image 20221116221405.png]]

![[Pasted image 20221116221426.png]]

Some techniques to find Buffer Overflow (BO):
1. Fuzzing

Scripts to find the offset to crash the programs:
1. Mona (Immunity Debugger)
2. Metasploit:
	1. https://github.com/lattera/metasploit/blob/master/tools/pattern_create.rb
	2. https://github.com/lattera/metasploit/blob/master/tools/pattern_offset.rb

![[Pasted image 20221116223919.png]]

To find JMP ESP/ CALL ESP
1. Immunity Debugger > Search for > Command
2. 
