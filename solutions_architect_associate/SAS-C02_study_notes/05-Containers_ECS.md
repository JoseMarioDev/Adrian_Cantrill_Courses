### Introduction to Containers and Demo

#

- virtualization runs multiple OSs on same hardware
- causes the problem of using same resource over and over. in pic, the Guest OS is the same on each VM
- why do we need multiple copies then?

  ![Alt text](img/virtualization.png 'problem of virtualization')

- solution is to use containers (ex: Docker)

  - container runs as a process within OS, only need one installation of OS

  ![Alt text](img/containerization.png 'difference with container')

- container is a running copy of a docker image

  - made up of multiple layers
  - stacks of layers
  - docker file creates image
  - file has lines that creates layers of image

    ![Alt text](img/dockerimage.png 'layers of docker image')

- images are used for creating docker containers
  - container has read/write layers
  - allows containers to run
  - images can create multiple containers
  - only difference between containers is the read/write layer
- containers registry are hubs of container images
  - can be private/public
  - download/upload images
- key concepts

  ![Alt text](img/containerkeyconcepts.png 'layers of docker image')

### ECS - Concepts

#

Elastic Container Service

- product that allows you to use docker containers inside AWS environment
  - done 2 modes: Fargate and EC2 mode
  - ECS lets you create clusters
  - create container definition to tell ECS where your container is
  - task definition is the application information in that container
    - store resources use by the application
    - stores task role. IAM role used to interact with AWS resources
- service definition
  - provides scalability and HA
- Tasks and Services are what is deployed into Cluster
- key points
  - Container definition: defines image and ports used for container
  - Task Definition - applies to the application as a whole. specify the security(role), containers, resources
  - Task Role: IAM role with the Task assumes
  - Service: How many copies, HA, restarts, scaling. use if business critical

### ECS - Cluster Mode

#

- 2 modes: EC2 and Fargate
- define what part you manage/AWS manages
- cost difference each mode
- EC2 mode:
  - runs in ECS cluster in a VPC
  - users registry to store images (ex: docker hub)
  - images deployed by tasks/services
- great middle ground, uses EC2 instances

  ![Alt text](img/ec2mode.png 'ec2mode with ec2 instances being deployed by registry')

- Fargate mode:

  - removes overhead
  - dont have to manage EC2 instances
  - paying for instances whether you're using them or not
  - AWS maintains the platform
  - still uses clusters and vpc
  - no servers to manage, little like serverless?

  ![Alt text](img/ec2fargate.png 'fargate uses a farmlike approach,shared by all but private')

- three main options: know the difference:
  - EC2 vs ECS(ec2) vs ECS(fargate)
  - if your business uses containers already, use ECS
  - ECS(ec2) large workload or price conscious
  - fargate - large workload or want less overhead
    - fargate good for small/burst workloads
    - same for batch periodic workloads
