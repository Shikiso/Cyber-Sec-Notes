AAA - Authentication, Authorization and Accounting/Auditing

AAA is a authentication method that uses a database of credentials.
This database can be local or remote.

To configure a local AAA service to authenticate admin access:
1. Add usernames and passwords to local router database
2. Enable AAA on the router
3. Configure AAA parameters on the router
4. Confirm and troubleshoot the AAA configuration

TACACS+ AND RADIUS are both authentication protocols used to communicate with AAA servers.
Differences:  https://www.cloudradius.com/tacacs-vs-radius-which-is-better-for-you/

To configure a server based AAA authentication:
1. Globally enable AAA to use all of AAA elements
2. Specify the server that will provide AAA services for the router (TACAS+ or RADIUS)
3. Configure encryption key needed to encrypt the data transfer between the network device and AAA server
4. Configure AAA authentication method list to refer to the TACACS+ or RADIUS server. If possible configure more than one server for redundancy.