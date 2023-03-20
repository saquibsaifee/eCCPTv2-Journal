dig 



**how to capture LM hashes**
Steps:
1. `msf > use auxiliary/server/capture/smb` setup SMB listener
2. force the victim to send us authentication request, one way to achieve it is ![[Pasted image 20230227192429.png]]
3. IP is our fake server address
4. Listener will catch and save the hash
5. rcracki_mt can be used for rainbow attack against the captured hashes.![[Pasted image 20230227193152.png]]
6. to fasten the process we crack first 8-bytes using rcrack_mt and the remaining using `halflm_second.rb` script inside the `metasploit-framework/tools/password` folder.![[Pasted image 20230227193421.png]]
7. passwd is all UPPERCASE but it might be different in real. so we can use this to find the case sensitive passwd![[Pasted image 20230227193538.png]]



## Post exploitation 

- Metasploit command to check Privileges on windows 
	`getprivs`

- To check the Privileges on Windows (same as above)
	`post/windows/gather/win_privs`

- Post exploitation by bypassing UAC on windows
	`exploit/windows/local/bypassuac_injection`
	
- github.com/hfiref0x/UACME

- Unquoted Service Path exploits

- If session is unstable and getting disconnected, we can use `set AutoRunScript migrate -n svchost.exe` to migrate to `svchost` as soon as we get a shell.

- maintain access:
	- dump hashes: `run hashdump`
	- pass the hash using `psexec`
	- If having problem passing the hashes, we can use this.![[Pasted image 20230301184423.png]]![[Pasted image 20230301184442.png]]https://www.harmj0y.net/blog/redteaming/pass-the-hash-is-dead-long-live-localaccounttokenfilterpolicy/

-  Create a backdoor or add new user
	Meterpreter steps: `exploit/windows/local/persistence`
	![[Pasted image 20230301190610.png]]


Pivoting:

-   [Exploring Hidden Networks with Double Pivoting](https://pentest.blog/explore-hidden-networks-with-double-pivoting/)
-   [Tunneling and Pivoting](https://0xdf.gitlab.io/2019/01/28/pwk-notes-tunneling-update1.html)

Cheat sheets:

-   [eCPPT Field Guide](https://drive.google.com/file/d/1wC7RMTrWjt74rO8u4X-zM89T_hZzF_A5/)
-   [Reverse Shells](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)

 [Heath Adam’s Pentest Report Template](https://github.com/hmaverickadams/TCM-Security-Sample-Pentest-Report)










https://github.com/dn0m1n8tor/ecpptv2/blob/main/ecpptv2/web-app-security.md

https://github.com/dn0m1n8tor/ecpptv2/blob/main/ecpptv2/linux-exploitation.md

https://github.com/dn0m1n8tor/ecpptv2/blob/main/ecpptv2/network-security.md

https://drive.google.com/file/d/1wC7RMTrWjt74rO8u4X-zM89T_hZzF_A5/view

https://gist.github.com/6t2/23ff0b7f27a553eb19c30be2a06d10c

https://ecpptv2.popdocs.net/