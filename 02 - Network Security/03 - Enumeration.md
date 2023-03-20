
NetBIOS = Network Basic Input Output System
is used to share files, folders, and printers to device connected on LAN. NBT is NetBIOS over TCP.

--------------------------------------

SNMP = Simple Network Manager Protocol
used to gather information and configure network device(printer, switches, serves...)
for ex. SNMP can be used to configure the router or check its status

UDP 161
`snmpwalk`

use `snmp-brute` scripts in `nmap` to get more info, especially about the community string.

use `snmpwalk` for further enumeration 

use hydra to crack `smb` creds.

---------------------------------------

SMB = Server Message Block
Lets you share files, disks, directories, printer, and in some cases, even COM ports across a network

Pre 2000 can only ran over NetBIOS port 139
Post 2000 can directly ran on port 445

`nbtscan` can be used for enumeration

`net view` allow us to list domains, computers and resources shared by a computer in the network.

`smbclient` to list and access the shared files

![[Pasted image 20230218200528.png]]
`wininfo` is another tool like Winfigerprint

`DumpSec` is another one

`enum4linux` Linux enumeration tool

use hydra to crack smb dir passwds

use `autoroute` to add pivoting machines

use `sock4a` proxy chain to pivot

