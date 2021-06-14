## 🗒️ Notes

### 🖥️ Basics

Concepts

- provides access to VMs known as instances
- compute power
- IaaS. unit of consumption is the instance
- private AWS service. runs in single VPC subnet
- AZ resilient
- diff sizes and capabilities
- on demand billing - per second
- pay for what you consume
- can use diff types of storage

  - local onhost storage

  [EBS](https://www.notion.so/EBS-4b58a9b890694630a153928aaa013797)

States

- instances are composed of CPU, disk, memory, networking
- running
  - charged for all 4 categories
- stopped
  - **no CPU, memory, network charges**
  - still charged for storage
- terminated
  - no charge for all 4. all are deleted

AMI - Amazon Machine Image

- is image of EC2 instance
- use to create an instance or created from an instance
- similar to server image
- contains:
  - attached permissions
  - can be set as public
  - owner is implicitly allowed
  - can add explicit permissions to specific AWS accounts
- contains root volume
- contains block device mapping
  - mapping between volumes and how OS sees them

Connections

- connect to EC2 instance via:
  - remote desktop on Windows. port 3389
  - SSH on Linux. port 22
- use SSH key pair
  - public and private parts

---

🖥️ Virtualization 101

Concepts

- SAAC02 Shared Content

---

🖥️ EC2 Architecture and Resilience

Concepts

- SAAC02 Shared Content

---

🖥️. Storage Refresher

Concepts

- SAAC02 Shared Content

---

🖥️ Elastic Block Store(EBS) Service Architecture

Concepts

- SAAC02 Shared Content

---

🖥️. EBS Volume Types - General Purpose

Concepts

- SAAC02 Shared Content

---

🖥️. EBS Volume Types - Provisioned IOPS

Concepts

- SAAC02 Shared Content

---

🖥️. EBS Volume Types - HDD Based

Concepts

- SAAC02 Shared Content

---

🖥️. Instance Store Volumes - Architecture

Concepts

- SAAC02 Shared Content

---

🖥️. Choosing Between the EC2 Instance Store and EBS

Concepts

- SAAC02 Shared Content

---

🖥️. Snapshots, Restore, & Fast Snapshot Restore(FSR)

Concepts

- SAAC02 Shared Content

---

🖥️. EBS Encryption(Theory & Demo)

Concepts

- ***

🖥️. Network Interfaces, Instance IPs, and DNS

Concepts

- SAAC02 Shared Content

---

🖥️. Amazon Machine Images(AMI)

Concepts

- SAAC02 Shared Content

---

🖥️. EC2 Purchase Options

Concepts

- ***

🖥️. Reserved Instances - the rest

Concepts

- ***

🖥️. Instance Status Checks & Auto Recovery

Concepts

- SAAC02 Shared Content

---

🖥️. Horizontal & Vertical Scaling

Concepts

- SAAC02 Shared Content

---

🖥️. Instance Metadata(Theory & Demo)

Concepts

-
