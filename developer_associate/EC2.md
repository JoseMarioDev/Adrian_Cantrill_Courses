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

🖥️ EC2 Instance Types

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

- by default no encryption is applied
- applies at rest encryption for volumes and snapshots
- uses KMS to create a CMK
  - can be AWS managed - default
  - or customer managed
- creates Data Encryption Key(DEK)
  - key is encrypted by KMS
  - when needed to encrypt data, EBS asks KMS to decrypt the key
  - then sends key to EC2 host, loaded in memory of EC2 host
  - instance can now use the key to encrypt/decrypt data
- if snapshot is created, it's also encrypted with the DEK

  - any volumes created from snapshot are as well

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4fa46101-9064-45e7-b17c-1ad42b41684e/Screen_Shot_2021-06-14_at_6.53.54_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4fa46101-9064-45e7-b17c-1ad42b41684e/Screen_Shot_2021-06-14_at_6.53.54_PM.png)

Exam Power Up

- accounts can config to set encryption by default - default is CMK
- otherwise choose a CMK to use
- each volume uses 1 unique DEK
- snapshots and future vols use the same DEK
- cant change a vol to not be encrypted once done
- OS isn't aware of the encryption. occurs between EBS and the host
  - uses AES-256

Demo Walk-thru

- go to EC2 services, launch an EC2 instance
- select encryption when choosing storage

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/45134368-128c-4238-a57d-f7f6ba7cabe3/Screen_Shot_2021-06-14_at_6.59.20_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/45134368-128c-4238-a57d-f7f6ba7cabe3/Screen_Shot_2021-06-14_at_6.59.20_PM.png)

- look at volumes from left sidebar
  - will tell you it's encrypted
  - if you create snapshot from vol, notice it's automatically encrypted as well
  - create volume from snapshot, notice it will be encrypted by default as well
  - cannot turn off
  - but can change the master key

---

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

- there are a number of diff EC2 purchase options, with diff mechanics and use cases

On-Demand

- notes

Reserved

- notes

Dedicated Instance

- notes

Dedicated Host

- notes

---

🖥️. Reserved Instances - the rest

Concepts

-

---

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
