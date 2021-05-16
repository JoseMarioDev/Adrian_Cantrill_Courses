## 🗒️ Notes

### 🌐 Public vs Private Services

Concepts

- services can be categorized into 2 categories: Public and Private
- applies to networking - no permissions by default. difference is connectivity
- examples of an AWS public service:

  [S3](https://www.notion.so/S3-5e32496717774522a0d49036cec3f866)

Private Zone

- no connections are allowed to private zone by anywhere else by default
- examples:

  [VPC](https://www.notion.so/VPC-b9469cde682c4a66b4bf25169fae705c)

  [EC2](https://www.notion.so/EC2-33b59c5db2b340c2b767143caaf427d7)

- can config private services so they have public access
- what you're doing is taking a private service(ex: EC2) and putting it in a public zone

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8413534c-2155-4bf5-b932-559dd98cc3de/Screen_Shot_2021-05-16_at_10.27.43_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8413534c-2155-4bf5-b932-559dd98cc3de/Screen_Shot_2021-05-16_at_10.27.43_AM.png)

---

### 🌐 AWS Global Infrastructure

Concepts

- [https://www.infrastructure.aws/](https://www.infrastructure.aws/)
- regions
  - AWS major locations across the globe
  - separate geographically - isolated fault domain
  - location control
  - geopolitical separation
- edge locations
  - smaller than regions, but spread out across the country more
  - low latency, high speed distribution
  - CDNs
- availability zones
  - zones inside regions
  - regions have multiple AZs
  - isolated infrastructure inside a region

Resilient Levels

- Globally resilient

  - few of these inside AWS
  - service is global, no concept of picking a region.

  [IAM](https://www.notion.so/IAM-9c1b80238e8845cb924ee006a779ed86)

  [Route 53](https://www.notion.so/Route-53-862cb3558c3144c09c3766ea05a0a169)

- Regionally resilient
  - operate in separate services in each region
    - ex: US-east-1, ohio, asia, eu, etc
    - can replicate data to multiple AZs in that region
- AZ resilient
  - services that run in a single AZ
  - if the AZ service is running in fails, the service fails
  - are prone to failure

---

### 🖥️ VPC Basics

Link to VPC doc

[VPC](https://www.notion.so/VPC-b9469cde682c4a66b4bf25169fae705c)

---

[EC2](https://www.notion.so/EC2-33b59c5db2b340c2b767143caaf427d7)

[S3](https://www.notion.so/S3-5e32496717774522a0d49036cec3f866)

[CloudFormation](https://www.notion.so/CloudFormation-7c4b82bdc704488bbda0e1be958134a7)

[CloudWatch](https://www.notion.so/CloudWatch-1ed93cac309c45deaf59093ee411648b)

### 🌐 High-Availability vs Fault Tolerance vs Disaster Recovery

[DNS](https://www.notion.so/DNS-643527873fdc4442a611bd4b1c506b4c)

[Route 53](https://www.notion.so/Route-53-862cb3558c3144c09c3766ea05a0a169)
