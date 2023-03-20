Tunneling and Port Forwarding
https://book.hacktricks.xyz/generic-methodologies-and-resources/tunneling-and-port-forwarding


ProxyChains
Autoroute - Metasploit module
Socks4
SSH Tunnels
Chisel - window tools
plink - window tool
netsh - window in-built CLI binary


---
**Command:** sessions -u 1 --- Upgrade the shell to Meterpreter shell.


---
https://systemweakness.com/bypassing-uac-methods-and-tricks-a536f784cc46

**User Account Control (UAC)** is a windows security feature that forces any new process to run in the security context of a non-privileged account by default regardless if admin or non-admin.

> Working of UAC :

1.  The user requests to run an application as administrator.
2.  A **ShellExecute** API call is made using the **runas** verb.
3.  The request gets forwarded to Appinfo to handle elevation.
4.  The application manifest is checked to see if Auto Elevation is allowed (more on this later).
5.  App info executes **consent.exe**, which shows the UAC prompt on a **secure desktop**. A secure desktop is simply a separate desktop that isolates processes from whatever is running in the actual user’s desktop to avoid other processes from tampering with the UAC prompt in any way.
6.  If the user gives consent to run the application as administrator, the Appinfo service will execute the request using a user’s Elevated Token. Appinfo will then set the parent process ID of the new process to point to the shell from which elevation was requested.

-   here we will be looking into two case study for bypassing UAC