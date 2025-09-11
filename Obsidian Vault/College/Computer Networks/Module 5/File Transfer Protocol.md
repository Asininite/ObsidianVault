- mechanism provided by TCP/IP to copy files from one host to another
- two systems use different methods to store files (exFAT vs btrfs)
- Port 21 for control connection
	  Port 20 for data connection

### FTP Client
![[Pasted image 20241126195519.png]]

### communication over control conn.
- FTP uses same approach as SMTP
- 7-bit ascii character set
- commands and responses
- ![[Pasted image 20241126200437.png]]

### communi. over data conn.
- server to client : retrieving file RETR
- client to server : storing file STOR
- list of file names from server to client : LIST
- ![[Pasted image 20241126200604.png]]