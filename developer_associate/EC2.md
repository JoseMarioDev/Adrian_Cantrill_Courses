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
