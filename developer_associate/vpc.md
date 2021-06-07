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

- content

---

### ☁️ Custom VPCs

Concepts

- content

---

### ☁️ VPC Subnets

Concepts

- content

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
