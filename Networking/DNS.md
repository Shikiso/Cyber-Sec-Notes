DNS or Domain Name System is responsible for converting domain names into IP addresses. Since people have a hard time remembering numbers and can remember words much easier, when you want to go to a website instead of using the IP address you use the domain name. For example you would enter google.com instead of 142.250.66.206.

# Domain Hierarchy
![[/Images/domain_hierachy.png]]
## Top-Level Domain
The most right hand part of a domain name. For example in google.com **.com** is the TLD. There are two types of TLD, gTLD (Generic Top Level Domain) and ccTLD (Country Code Top Level Domain).

## Second-Level Domain
This is the part before the TLD so in google.com **google** is the Second Level Domain.

## Subdomain
A subdomain sits on the left-hand side of the Second-Level Domain using a period to separate it. For example in the name australia.google.com **australia** is the subdomain.

# DNS Record Types
DNS isn't just for websites though, and multiple types of DNS record exist. We'll go over some of the most common ones that you're likely to come across.

## **A Record**
These records resolve to IPv4 addresses, for example 104.26.10.229
## **AAAA Record**
These records resolve to IPv6 addresses, for example 2606:4700:20::681a:be5
## **CNAME Record**
These records resolve to another domain name, for example, TryHackMe's online shop has the subdomain name [store.tryhackme.com](http://store.tryhackme.com) which returns a CNAME record [shops.shopify.com](http://shops.shopify.com). Another DNS request would then be made to [shops.shopify.com](http://shops.shopify.com) to work out the IP address.
## **MX Record**
These records resolve to the address of the servers that handle the email for the domain you are querying, for example an MX record response for [tryhackme.com](http://tryhackme.com) would look something like [alt1.aspmx.l.google.com](http://alt1.aspmx.l.google.com). These records also come with a priority flag. This tells the client in which order to try the servers, this is perfect for if the main server goes down and email needs to be sent to a backup server.
## **TXT Record**
TXT records are free text fields where any text-based data can be stored. TXT records have multiple uses, but some common ones can be to list servers that have the authority to send an email on behalf of the domain (this can help in the battle against spam and spoofed email). They can also be used to verify ownership of the domain name when signing up for third party services.

# DNS Request
1. Computer checks local cache for address, if not there request is sent to your Recursive DNS server.
2. Recursive DNS Server (usually provided by ISP) checks local cache, if found it sends it back to you else forwards request to root DNS server
3. Root server sends request to TLD server based on the TLD
4. TLD server sends request to the authoritative server
5. Authoritative DNS server stores DNS records for a specific domain name and sends the DNS records back to the recursive DNS server