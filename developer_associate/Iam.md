## 🗒️ Notes

### 👨🏽‍💻 IAM Identity Policies

Concepts

- attach to IAM identities → users, groups, roles
- set of security statements that grants/denies access to resources
- in JSON

What makes up a Statement

1. `SID` - statement id. option. tells what it does
2. `Effect` - either `allow` or `deny`
3. `Action` - format is `[service:operation]`
4. `Resource` - list of resource(s) statement applies to

Priority

Order of priorities

1. Explicit Deny - if something is explicitly denied, then no access
2. Explicit Allow - allowed access to resource, unless there is an explicit deny
3. Implicit Deny (default) - identities start off w/no access to resources. exception is the default root user

if there are multiple policies, all of them are reviewed and permissions are given

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0c67bcc9-f24b-436f-a939-8d360018a749/Screen_Shot_2021-05-17_at_8.00.02_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0c67bcc9-f24b-436f-a939-8d360018a749/Screen_Shot_2021-05-17_at_8.00.02_AM.png)

2 main types of Policies

1. inline
   - apply policy to users individually
   - used for exceptions, special circumstances
2. managed
   - policy is created as own object, then attached to user
   - lower overhead
   - best practice
   - 2 types - AWS managed and custom

---

### 👨🏽‍💻 IAM Users & ARNs

Concepts

- identity used for anything requiring long term AWS access
- ex: humans, applications, or service accounts

Architecture

- principal - user or app needing to access AWS
- needs to be authenticated and authorized
- authentication is when principal proves to IAM it's who it claims to be
  - can be username/password or access keys
  - once authenticated, AWS knows which policies to apply
- authorization is IAM checking policies applied to an authorized identity and applying permissions

Amazon Resource Name (ARN)

- uniquely identify resources within any AWS accounts
- are used in IAM policies
- defined format
- collection of fields split by colon

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/84d4752d-a84c-457e-bf11-ccbe8930785e/Screen_Shot_2021-05-17_at_6.43.24_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/84d4752d-a84c-457e-bf11-ccbe8930785e/Screen_Shot_2021-05-17_at_6.43.24_PM.png)

Exam Power Up

- 5,000 IAM users per account
- IAM user can be a member of 10 groups

---

### 👨‍👩‍👦 IAM Groups

Concepts

- containers for users
- can't log into a group, no creds
- users can belong to multiple groups
- can have policies attached to groups - inlined or managed
- no limit for num of users in a group
- there is no "all members" groups
- no nesting
- limit 300 groups per account
- groups cannot be reference as a principal in a policy - can't be referred to in a policy

---

### 👨‍👩‍👦 IAM Roles - the Tech

Concepts

- type of identity that exists inside AWS
- best suited to be used my multiple principals
- generally used on temp basis
- represents a level of access inside an account
- IAM roles have 2 types of policies

  1. Trust policies
     - identifies who can assume the role
     - can ref diff things
     - generates temp sec creds to access resources inside permissions policy
       - time limited
  2. Permissions policy

     - whatever resources are given access to
     - `sts:AssumeRole` AWS service that generates sec creds

     ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bda6c433-2c07-411c-bf05-0515c76865c7/Screen_Shot_2021-05-18_at_7.46.22_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bda6c433-2c07-411c-bf05-0515c76865c7/Screen_Shot_2021-05-18_at_7.46.22_AM.png)

---

### 👨‍👩‍👦 When to use IAM roles

Examples

- AWS services

  - ex: Lambda functions has no permissions by default
  - you would create a Lambda Execution Role for Lambda functions to access resources

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/daa2fb93-c602-4c87-942c-3bd779b8b019/Screen_Shot_2021-05-18_at_7.50.21_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/daa2fb93-c602-4c87-942c-3bd779b8b019/Screen_Shot_2021-05-18_at_7.50.21_AM.png)

- Emergency or unusual situations

  - ex: if a employee has read only access, but needs to change something because of emergency
  - short time, assign him the role, fix emergency, then role expires

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0872c713-bcc4-43f0-8d59-802068b28d79/Screen_Shot_2021-05-18_at_7.54.46_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0872c713-bcc4-43f0-8d59-802068b28d79/Screen_Shot_2021-05-18_at_7.54.46_AM.png)

- When migrating to AWS

  - when you want to reuse existing accounts in AWS aka Identity Federation
  - ex: Active Directory environment → AWS

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a2f7e31a-63c5-47f8-bc13-3d45f7e4ee85/Screen_Shot_2021-05-18_at_7.55.24_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a2f7e31a-63c5-47f8-bc13-3d45f7e4ee85/Screen_Shot_2021-05-18_at_7.55.24_AM.png)

- Web Identity Federation

  - ex: ride sharing app using SSO to access AWS
  - mobile applications

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8cee422b-cc3a-46eb-bd19-249ca5a8f1db/Screen_Shot_2021-05-18_at_7.58.01_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8cee422b-cc3a-46eb-bd19-249ca5a8f1db/Screen_Shot_2021-05-18_at_7.58.01_AM.png)

- When using multiple accounts

  - cross account access

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ad807908-4d2c-4484-82d8-4342f61a3b8f/Screen_Shot_2021-05-18_at_7.59.56_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ad807908-4d2c-4484-82d8-4342f61a3b8f/Screen_Shot_2021-05-18_at_7.59.56_AM.png)

---

### 🏢 AWS Organizations

Concepts

- how to manage multiple AWS accounts
- takes a single AWS account, create an organization. the account becomes the management account
- invite other accounts to the organization
  - they become member accounts
- hierarchal structure, inverted tree, the top is the organizational root
- can also contain OUs
- individual billings is removed. consolidated billing. single monthly bill     
- consolidation of reservations and volume discounts
- can create new accounts this way
- users can log into 1 account, then use roles to access other accounts

  - or can use identity federation to use existing log in creds

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c877d342-0665-4085-aeb4-55748e89a130/Screen_Shot_2021-05-19_at_6.26.14_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c877d342-0665-4085-aeb4-55748e89a130/Screen_Shot_2021-05-19_at_6.26.14_AM.png)

---

### 🏢 Service Control Policies (SCP)

Concepts

- feature of AWS Organizations which allows restrictions to be placed on member accounts in the form of boundaries
- JSON policy documents that can be attached to the org, OUs, or individual AWS accounts
- policy rules inherit down
- the management is never affected by SCPs

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1a62512c-1886-4293-9c72-2236cf7bee13/Screen_Shot_2021-05-19_at_11.49.56_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1a62512c-1886-4293-9c72-2236cf7bee13/Screen_Shot_2021-05-19_at_11.49.56_AM.png)

Features

- are account permissions boundaries
- limit what the account can do
- they dont grant permissions
- can use in 2 ways

  - allow lists
    - use when you need to be specific on access
    - everything would be denied, you would have to create allow policies
  - deny lists - default
    - by default services are given `FullAWSAccess`
    - you need to create deny policies to deny access
    - need to add restrictions

  ***

### 📊 CloudWatch Logs and CloudTrail

Concepts

next 2 sections covers CW Logs and CloudTrail. I decided to include it in[CloudWatch](https://www.notion.so/CloudWatch-1ed93cac309c45deaf59093ee411648b)
