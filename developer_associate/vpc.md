## 🗒️ Notes

### 💻 **Basics**

Concepts

- used to create private networks inside AWS
- used to connect AWS network to onprem network in hybrid env
- virtual network inside a region of AWS
- regionally resilient
- by default is private and isolated from other VPCs
- a region can have multiple VPCs, but there is no way for them to communicate w/each other unless you config

Types

- default VPC - can only have 1, created by default
  - config in a very specific way
  - given a CIDR of 172.31.0.0/16
  - configured to have one subnet in each AZ of region
  - each subnet is given a /20 subnet
  - each VPC is config with a IGW, SG, and NACL
  - by default, anything placed inside each subnet is given a public IPv4 address
- custom VPC
  - you must config everything
  - 100% private by default

---

### ☁️ VPC Sizing and Structure - Part 1

Considerations

- [AWS documentation on VPC design](https://aws.amazon.com/answers/networking/aws-single-vpc-design/)
- IP address scheme for A4L → [https://cloud.google.com/vpc/docs/vpc](https://cloud.google.com/vpc/docs/vpc)
- need to decide on CIDR range
- what size should the VPC be?
- are there other networks we need to use?
  - ranges other networks use
  - try to predict the future
- VPC structure
- VPC minimum size /28(16 IPs)
- VPC maximum /16(65,456 IPs)
- avoid common ranges

---

### ☁️ VPC Sizing and Structure - Part 2

Concepts

- focuses on VPC design and IP planning
- IP address scheme for A4L → [https://cloud.google.com/vpc/docs/vpc](https://cloud.google.com/vpc/docs/vpc)

---

### ☁️ Custom VPCs

Concepts

- [AWS docs on VPC limits](https://docs.aws.amazon.com/vpc/latest/userguide/amazon-vpc-limits.html)
- what we'll be building for this course

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/66123d5d-bab9-42cb-a674-2775c5c5ab27/Screen_Shot_2021-06-09_at_6.32.36_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/66123d5d-bab9-42cb-a674-2775c5c5ab27/Screen_Shot_2021-06-09_at_6.32.36_PM.png)

Architectural Theory

- VPCs are regionally resilient
- nothing is allowed in/out without explicit configuration
- support hybrid networking - other cloud or on-prem
- can select default or dedicated tenancy
  - if you pick dedicated tenancy at VPC level, can be costly
- can use private CIDR and public IPs
- allocated 1 primary private IPv4 CIDR block
- min /28 and max /16
- can add secondary IPv4 blocks
- can use an IPv6 /56 CIDR block
  - IPv6 are public
- VPCs use DNS provided by Route 53
- 2 DNS options that are important
  - `enableDnsHostnames` - gives instances DNS names
  - `enableDNSSupport` - enables DNS resolution in VPC

---

### ☁️ VPC Subnets

Concepts

- add structure to a VPC
- where applications run from in a VPC
- start off as private, need configuration to make public
- subnets are AZ resilient
- one subnet is in one AZ
- is allocated a IPv4 CIDR, that is subset of the VPC CIDR
- optionally, can be allocated an IPv6 CIDR
- can communicate with other subnets in the VPC

Reserved IP addresses

- 5 in total
  - Network address = first address
  - 'network +1' = VPC Router
  - 'network+2' = reserved for DNS
  - 'network+3' = reserved for future use
  - broadcast address = last IP in subnet
- for every VPC a DHCP option set is created
  - can config auto assign IPv4 addresses
  - can config auto assign IPv6 addresses

---

### ☁️ VPC Routing, Internet Gateway & Bastion Hosts

Concepts

- content

---

### ☁️ Network Access Control Lists(NACLs)

Concepts

- content

---

### ☁️ Security Groups(SGs)

Concepts

- content

---

### ☁️ Network Address Translation & NAT Gateway - Part 1

Concepts

- content

---

### ☁️ Network Address Translation & NAT Gateway - Part 2

Concepts

- content
