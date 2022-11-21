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
