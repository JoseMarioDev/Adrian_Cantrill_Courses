## 🗒️  Notes

### 💻  **Basics**

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

- every VPC has a VPC router
    - routes traffic from somewhere to somewhere else
    - runs in every AZ
- routes traffic between subnets in a VPC
- controlled by route table
- created with main route table
    - can only have 1 associated route table
- higher prefix value → more specific → highest priority

Internet Gateway

- regionally resilient gateway
    - has a 1:1 relationship with a VPC
    - runs from border within AWS public zone
- runs from border within AWS public zone
- gateways traffic between the VPC and the internet or AWS Public Zones(S3, SQS, SNS, etc)
- is AWS managed
- using an IGW to connect to internet
    - create IGW
    - attach IGW to VPC
    create custom RT
    - associate RT
    - default routes → IGW
    - subnet allocate IPv4

        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/580f49ff-a226-4065-98d4-5718146d96b0/Screen_Shot_2021-06-13_at_5.35.47_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/580f49ff-a226-4065-98d4-5718146d96b0/Screen_Shot_2021-06-13_at_5.35.47_PM.png)

IPv4 addresses with a IGW

- the IGW changes the source/destination IPs to make packets routable
- IPv6 addresses are publicly routable

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ce23d503-30d2-468d-870d-15c9ddb5c67f/Screen_Shot_2021-06-13_at_5.41.30_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ce23d503-30d2-468d-870d-15c9ddb5c67f/Screen_Shot_2021-06-13_at_5.41.30_PM.png)

Bastion Hosts / Jump Boxes

- is an instance in a public subnet
- incoming management connections arrive there
    - then access internal VPC resources
- often the only way in to a VPC

---

### ☁️ Network Access Control Lists(NACLs)

Concepts

- type of security filter(like firewalls) which can filter traffic as it enters or leaves a subnet
- are attached to subnets and only filter data as it crosses the subnet boundary
- are stateless and see initiation and response phases of connections as 2 separate streams requiring 2 roles - in and out

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