Port numbers are used to specific where to send packets. Think of your computer like a apartment complex. your IP address is the address but the port number is the floor and room number. So the delivery driver knows exactly where to go.

Well-known port numbers 0-1,023:
	- 80 http
	- 443 https
	- 22 ssh
	- Reversed for common services	

Registered port 1024-49151:
	- Assigned by IANA to requesting entity to use with specific processes or application
	- Port registered with a company

Private and/or dynamic ports 49152-65535:
	- Clients OS assign port numbers dynamically when a connection to a service is initialized

Ports on browsers are randomly generated and can not be the same.