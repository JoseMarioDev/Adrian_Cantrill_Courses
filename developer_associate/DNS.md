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
