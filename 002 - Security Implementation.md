Security Implementation to prevent the exploitation of vulnerabilities such as Buffer overflow.

1. Address Space Layout Randomization (ASLR)
2. Data Execution Prevention (DEP)
3. Stack Cookies (Canary)

1. Address Space Layout Randomization (ASLR)
	It randomize the memory address space of executables, libraries, and stack. It makes it difficult to predict the memory address.
	If activated, OS loads the same executable at different location in memory every time.
	Even after it is activate, some DLL could still be without this protection.
	Use can use Process Explorer or Mona(Immunity Debugger to see the DLL without ASLR protection.

	 One can use Enhanced Mitigation Experience Toolkit (EMET) to deploy security mitigation technologies to all the application.

2. Data Execution Prevention (DEP)
	It prevents the execution of any code which is not explicitly marked as executable. 
	https://web.archive.org/web/20161017015745/https:/support.microsoft.com/en-us/kb/875352

3. Stack Cookies (Canary)
	This implementation places a value next to the return address on the stack. The function prologue loads a value into this location, while the epilogue makes sure that the value in intact.
	When the epilogue runs, it check that the value is still there and that it is correct.
