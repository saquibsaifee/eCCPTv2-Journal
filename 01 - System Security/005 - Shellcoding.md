https://fuzzysecurity.com/tutorials/expDev/6.html

Can be executed through EIP and Structured Exception Handling

SEH holds the address to jump when there is an exception, ex. divide by zero

Type of Shellcodes:
1. Local: used for priv esc
2. Remote: bind/reverse shell and socket reuse
3. Staged
	1. Egg hunt: Egg hunter(small) shellcode hunter for where to put the Egg(actual/big shellcode)
	2. Omelet: small multiple eggs
4. Download and execute shellcodes

Shell Encoding:
1. Null bytes, can fail the shellcode
	- xor eax, eax instead of mov eax, 0
2. Non-alnum
	- Self-modifying code(SMC): the code is prepended with a small decoder which will encode the shellcode and decode and execute the main body.

How to shellcode:
1. Find the address of function using arwin. ![[Pasted image 20221118153120.png]]
2. Write the asm file and compile it ![[Pasted image 20221118153249.png]] ![[Pasted image 20221118153306.png]]
3. Use to objdump to get the machine code. ![[Pasted image 20221118153347.png]]
4. Convert it into binary by adding `\x` in front of every code and remove spaces.                                                              ![[Pasted image 20221118153448.png]]

`\x68` == PUSH of word/dword
`\6A` == PUSH of byte  
	Push opcodes: https://c9x.me/x86/html/file_module_x86_id_269.html
`\x00` == NULL for termination
`\x20` == Space


Msfvenom: Shellcode generator

![[Pasted image 20221118210630.png]]

How to achieve NULL-free shellcode:
1. Manually remove null bytes with other operations, such as  xor eax, eax.
2. subtract 11111111 and then add back after
	![[Pasted image 20221118211814.png]]
3. Msfvenom to encode the shellcode:
	1. ![[Pasted image 20221118212019.png]]
	2. ![[Pasted image 20221118212042.png]]
	3. Del 000a(new line) from python generated code
	4. Specify bad char in Msfvenom with `-b` 
	5. ![[Pasted image 20221118212228.png]]
4. 