
Sniffing:
1. Passive (capture and watch the packets using Wireshark)
2. Active (Mac flooding and ARP poising)


- Mac flooding
	- stress the switch and flood its Content Addressable Memory(CAM) table used to maintain all the info needed to forward the frames to correct port
	- ![[Pasted image 20230219212159.png]]

ARP - Address Resolution Protocol
have ARP table with IP -> MAC and TTL

![[Pasted image 20230219214859.png]]

1. Host Poising 
	1. ![[Pasted image 20230219215426.png]]

2. Gateway Poising
	1. ![[Pasted image 20230219215532.png]]


Dsniff:
![[Pasted image 20230219215638.png]]
![[Pasted image 20230219215651.png]]

---
DHCP Spoofing:
![[Pasted image 20230219220232.png]]


---
![[Pasted image 20230219220438.png]]
![[Pasted image 20230219220533.png]]
`responder` does this

---
Cain & Abel

- host discovery using ARP
- ARP poisoning to capture FTP and SMB creds
- SMB creds can be cracked with Cain & Abel
- Once cracked connect to the service and install abel to get the shell

---
MitM over SSL

Sslstrip


HSTS bypass using Sslstrip+

---

1.  What protocol can be used on the [**http://intranet.sportsfoo.com**](http://intranet.sportsfoo.com/) in order to avoid that credentials are transmitted in clear-text?
    
    -   **SSL**
2.  What protocol or tool can be used as a replacement for the **FTP** service in use on the host [**ftp.sportsfoo.com**](ftp://ftp.sportsfoo.com/)?
    
    -   **SFTP**
3.  What protocol can be used to ensure that all traffic between the file server and any other host on the LAN are encrypted?
    
    -   **IPSEC**
4.  What countermeasure can be implemented in order to protect the network against **ARP** **Poisoning** attacks?
    
    -   **You can use static ARP entries**

---
Responder can be used to capture the NTLMv2 hash.

