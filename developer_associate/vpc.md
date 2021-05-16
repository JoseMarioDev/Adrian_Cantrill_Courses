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
