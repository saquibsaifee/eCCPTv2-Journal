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
2. findjmp2
3. mona
4. arwin.exe

Mitigation Techniques:
1. Enhanced Mitigation Experience Toolkit (EMET)
2. Address space layout randomization
	1. ![[Pasted image 20221116231041.png]]
	2. Process Explore to verify is ASLR is running or not
	3. !mona modules
	4. !mona noaslr
3. Data Execution Prevention (DEP)
	1. Bypass: Return-Oriented Programming(ROP) https://cseweb.ucsd.edu/~hovav/talks/blackhat08.html
	2. https://www.corelan.be/index.php/security/rop-gadgets/
	3. https://www.corelan.be/index.php/2010/06/16/exploit-writing-tutorial-part-10-chaining-dep-with-rop-the-rubikstm-cube/#buildingblocks
4. Stack canary (stack cookie)
	1. ![[Pasted image 20221116231905.png]]
5. SafeSEH
 
Bypass ASLR:
1. Find module in which ASLR is not enabled
2. Lots of NOP
3. https://www.fireeye.com/blog/threat-research/2013/10/aslr-bypass-apocalypse-in-lately-zero-day-exploits.html
4. 