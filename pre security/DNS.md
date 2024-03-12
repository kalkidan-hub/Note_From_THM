(Domain Name System)
A system that saves us from typing the unmemorable ip address of the servers by letting us to just recall the catchy name of them.
Domain Hierarchy
=
#### TLD(Top Level Domain)
the right most part of a domain name
- Generic gTLD
- Country Code ccTLD

#### Second Level Domain
obtained when registered to a TLD.  This name shouldn't exceed 63 characters and should contain only alphanumeric character with the in between nonconsecutive hyphens.
#### subdomain
Resides to the left of second-level domain, period separated.

DNS request
=
This is what happen when a DNS request is made...
1. you made a domain name request, your computer checks for the local cache. If not there, the request is sent to Recursive DNS
2. If the request is on the local cache again - this cache is accumulated from local other requests - your request is responded, else the request is sent to root DNS server
3. from here the request is redirected to the correct TLD server
4. the TLD server finds the authoritative(nameserver) server to answer the request
5. the authoritative server, where DNS records are stored and updated, responds back to the recursive server from its entry. Recursive server caches the response for the future use until the TTL(time to live) of the entry comes to an end.

Command to use
=
```
nslookup --type=<DNS type> <domain name>

```


