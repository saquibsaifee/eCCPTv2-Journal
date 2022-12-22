1. Symmetric-key cryptography
	- DES/3DES
	- AES
	- RC4
	- Blowfish
2. Asymmetric(Public)-key cryptography 

Classes of algorithms:
	1. Block Cipher: data is handled in blocks, ex: DES, AES.
		- ECB(Electronic Code Book): message is divided into blocks and then encrypted. 
		- CBC (Cipher Block Chaining): each ciphertext block is derived from the previous blocks as well.
	2. Stream Cipher:  data is handled one byte at a time, ex: RC4, A5/1.

Hash:
	Three properties:
	 1. Preimage resistance: hard to resolve message from hash.
	 2. Second Preimage resistance: no two message with same hash
	 3. Collision resistance: same pair of message with same hash

![[Pasted image 20221120203030.png]]


**Windows passwords are stored in Security Accounts Manager (SAM) in Win 2000+**

Passwords are stored in Hash format and is stored as LM(Lan Manager) and NT(New Technology) hash

![[Pasted image 20221130211940.png]]
![[Pasted image 20221130211947.png]]

All passwords from windows 2000 are also stored in NT hashes.

LM hashes are still computed and stored by default up to Windows Vista.

These hashes are stored in the Windows SAM file located at: `C:\Windows\System32\config` But it is not accessible while the  OS is running.

These values are also stored in the registry at `HKEY_LOCAL_MACHINE\SAM` again it is not accessible while the  OS is running and require System privileges.

Tools to dump hashes of the remote system:
![[Pasted image 20221204212122.png]]

Meterpreter shell: run hashdump