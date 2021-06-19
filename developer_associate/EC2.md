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
- aka Launch Types

On-Demand

- default - average of everything
- per-second billing while instance is running
- associated resources such as storage are billed
- no interruption
- no capacity reservation
- predictable pricing
- no upfront costs
- no discount
- best for:

  - short term workloads
  - unknown workloads
  - apps which cant be interrupted
  -

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e9ea3195-1765-44f9-95b3-8fa4908b595b/Screen_Shot_2021-06-17_at_4.45.08_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e9ea3195-1765-44f9-95b3-8fa4908b595b/Screen_Shot_2021-06-17_at_4.45.08_PM.png)

Spot

- is AWS selling unused EC2 host capacity for up to 90% discount
- spot price is based on the spare capacity at any given time
- if spot price is higher than your max price, your instances are terminated
- never use for workloads that can't tolerate interruptions
- good for non time critical
- anything that can be rerun
- burst capacity needs
- cost sensitive workloads
- anything that is stateless

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aaaf216b-2b66-41df-b295-8e675d0c88b5/Screen_Shot_2021-06-17_at_4.51.01_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aaaf216b-2b66-41df-b295-8e675d0c88b5/Screen_Shot_2021-06-17_at_4.51.01_PM.png)

Reserved

- for long term instance usage
- reduce per-second cost or remove it entirely
- need to plan appropriately, you pay for any non-usage
- can commit for either 1 year or 3 years
- diff payment structures

  - no upfront - some savings for agreeing to the terms
  - pay all upfront - greater discount
  - partial upfront - middle ground

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fe5d8665-e847-43e7-a93b-ae967c69bd12/Screen_Shot_2021-06-17_at_4.57.08_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fe5d8665-e847-43e7-a93b-ae967c69bd12/Screen_Shot_2021-06-17_at_4.57.08_PM.png)

Dedicated Host

- Host that is allocated to you in it's entirety
- pay for host itself
- come with all resources you'd expect from a machine
- you pay for the host - no per-second charge
- you manage the capacity
- use for license based software
- use for host affinity

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f569f5ee-c615-4ee2-8092-9a25b70a775d/Screen_Shot_2021-06-17_at_4.59.47_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f569f5ee-c615-4ee2-8092-9a25b70a775d/Screen_Shot_2021-06-17_at_4.59.47_PM.png)

Dedicated Instance

- middle ground - instances run on EC2 hosts that you have for yourself
- pay hourly fee
- fee for instances

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7ed73b0a-1393-4e6f-a08a-59320938c93c/Screen_Shot_2021-06-17_at_5.02.10_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7ed73b0a-1393-4e6f-a08a-59320938c93c/Screen_Shot_2021-06-17_at_5.02.10_PM.png)

---

🖥️. Reserved Instances - the rest

Scheduled Reserved Instances

- ideal for long term usage which doesn't run constantly
- slightly cheaper, can only use during time window you specify

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a96dc296-05de-4124-9586-6262ed7aa9e9/Screen_Shot_2021-06-17_at_5.06.25_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a96dc296-05de-4124-9586-6262ed7aa9e9/Screen_Shot_2021-06-17_at_5.06.25_PM.png)

Capacity Reservations

- can reserve instances in a region
- can pick zonal reservation - in a specific AZ
- on demand capacity reservations - ensure you always have access to capacity in AZ

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2f4e6cfa-4c59-4b84-9b14-d38416531dc6/Screen_Shot_2021-06-17_at_5.09.51_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2f4e6cfa-4c59-4b84-9b14-d38416531dc6/Screen_Shot_2021-06-17_at_5.09.51_PM.png)

EC2 Savings Plan

- hourly commitment for 1 or 3 year term
- can make a reservation of general compute $ amounts
- or a specific EC2 savings plan - flexible on size and OS

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/963d543b-8871-4927-8886-ce4ad22ed2c7/Screen_Shot_2021-06-17_at_5.11.54_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/963d543b-8871-4927-8886-ce4ad22ed2c7/Screen_Shot_2021-06-17_at_5.11.54_PM.png)

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

- SAAC02 Shared Content

---

🖥️. Bootstrapping EC2 using User Data

Concepts

- SAAC02 Shared Content

---

🖥️. EC2 Instance Roles & Profile

Concepts

- SAAC02 Shared Content

---

🖥️. SSM Parameter Store

Concepts

- SAAC02 Shared Content

---

🖥️. System and Application Logging on EC2

Concepts

- SAAC02 Shared Content

---

🖥️. EC2 Placement Groups

Concepts

-

---

🖥️. Enhanced Networking & EBS Optimized

Concepts

-
