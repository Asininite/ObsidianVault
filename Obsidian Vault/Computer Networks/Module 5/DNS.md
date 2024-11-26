- host name to IP address translation service
- difficult to remember IP addresses
- DNS resolution ![[Pasted image 20241126175635.png]]

### Steps
- program sends name query to library procedure called (resolver)
- resolver looks up domain name cache for a match
- if no match found, request sent to DNS server
- server looks up name 
- if match found, returns IP address
	  else sends query to higher DNS server
		  continued until result obtained
- return result to program