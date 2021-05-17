## 🗒️ Notes

Concepts

- discovery service
- IP address to domain names
- uses zone files that holds the domain name and it's IP address
  - file is hosted on a name server

Terms

- _DNS Client_ - your laptop, phone, tablet, PC
- _Resolver_ - software on your device, or a server on the ISP that queries DNS on your behalf
- _Zone-_ part of the DNS database
- _Zonefile-_ physical database for a zone
- _Nameserver- server where zonefiles are hosted_

Structure

- DNS is distributed. data is stored in zonefiles that are stored on nameservers globally
- DNS Root is the starting point
- structured like an upside down tree

Root

- topmost part of DNS. known as DNS Root or Root Zone
- database is hosted on 13 special name servers
- known as root servers
- operated by 12 diff large companies
  - only manage root servers themselves, not the database

Process for finding root servers

- your laptop will query a resolver server
- the OS vendor of the server provides a root hints file
  - list or root servers
- the resolvers communicates with the root servers to find the IP address
- IANA manages the DNS root zone

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d69fef3e-f93a-4c4a-ab71-61d3062745f4/Screen_Shot_2021-05-16_at_10.10.45_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d69fef3e-f93a-4c4a-ab71-61d3062745f4/Screen_Shot_2021-05-16_at_10.10.45_PM.png)

- the resolver communicates with the root servers because there is a trust there
- important to know these servers communicate with each other because they are _authoritative_ or have trust
- IANA delegates the top level domains to other organizations, known as _registries_

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e19a6b1a-6594-446e-8c67-bf9b9fe85c93/Screen_Shot_2021-05-16_at_10.19.52_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e19a6b1a-6594-446e-8c67-bf9b9fe85c93/Screen_Shot_2021-05-16_at_10.19.52_PM.png)

DNS Resolution Visually

- information is distributed
- delegation and trust are used to move you one step closer to the address you need

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4654dd6c-dc8a-4f36-9e97-a6305c5c777c/Screen_Shot_2021-05-16_at_10.22.51_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4654dd6c-dc8a-4f36-9e97-a6305c5c777c/Screen_Shot_2021-05-16_at_10.22.51_PM.png)

Summary

- root hints → config file points at the root servers IPs and addresses
- root servers → host the DNS root zone
- root zone → points at top level domains authoritative servers
- gTLD → generic top level domains. ex: .com, .org
- ccTLD → country-code top level domains. ex: .uk, .eu, .mx

Record Types

DNS is capable of handling a number of diff record types, which perform diff tasks

1. _A -_ maps hosts names to IPv4 addresses
2. _AAAA_ - maps hosts name to IPv6 addresses
3. _CNAME -_ Host to Host record

   ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/76b2008f-a5ce-4e5c-9091-abaf53703f23/Screen_Shot_2021-05-17_at_12.09.48_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/76b2008f-a5ce-4e5c-9091-abaf53703f23/Screen_Shot_2021-05-17_at_12.09.48_AM.png)

4. _TXT -_ add arbitrary text to a domain

   - can be used to prove ownership

     ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2ce0981a-20d6-457a-afc7-795e7f77b31a/Screen_Shot_2021-05-17_at_12.20.21_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2ce0981a-20d6-457a-afc7-795e7f77b31a/Screen_Shot_2021-05-17_at_12.20.21_AM.png)

5. _MX -_ email servers

   - how a server can find a mail server for a specific domain
   - have 2 main parts - value and priority

     ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fead9938-3045-4bfc-8085-035c29b991e4/Screen_Shot_2021-05-17_at_12.18.00_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fead9938-3045-4bfc-8085-035c29b991e4/Screen_Shot_2021-05-17_at_12.18.00_AM.png)

TTL

- can be set on DNS records
- set in seconds
- how long the query results are stored on the resolver
- authoritative results come from the nameserver
- non-authoritative results come from the resolver

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ef3fe4f2-ced5-451b-bbdb-f47b5b5f0d76/Screen_Shot_2021-05-17_at_12.24.01_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ef3fe4f2-ced5-451b-bbdb-f47b5b5f0d76/Screen_Shot_2021-05-17_at_12.24.01_AM.png)
