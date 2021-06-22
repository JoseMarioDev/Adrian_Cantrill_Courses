## 🗒️ Notes

### Basics

Concepts

- is IaC tool
- allows automation of infrastructure creation, updates, and deletes
- uses templates
- written in YAML or JSON

Template Body

- _Resources_
  - what is is your are creating. ex: EC2 instance, S3 bucket, etc
  - resource part is the only part of a template that is mandatory
- _Description_

  - free text field to give details about template
  - Description must immediately AWS template version is using it

  ```jsx
  AWSTemplateFormatVersion;
  ```

- _Metadata_
  - control how diff things in template are presented in the console
  - controls how UI presents the template
- _Parameters_
  - add fields to prompt user for more info
- _Mappings_
  - optional - allows to create look up tables
- _Conditions_
  - allow decision making in template
  - create condition, then what
- _Outputs_
  - presents what is being created, updated, or deleted

How it works

- creates a stack of resources based from template
- keeps logical and physical resources in sync

---

### 🏫 CloudFormation Physical & Logical Resources

Concepts

- CFN defines physical and logical resources within templates
- using either YAML or JSON
- logical resource defines WHAT and leave the HOW up to the CFN product
- a CFN stack creates a physical resource for every logical resource
  - updating or deleting them as a template changes

---

### 🏫 CloudFormation Template and Pseudo Parameters

Concepts

- notes

---

### 🏫 CloudFormation Intrinsic Functions

Concepts

- notes

---

### 🏫 CloudFormation Mappings

Concepts

- notes

---

### 🏫 CloudFormation Outputs

Concepts

- notes

---

### 🏫 CloudFormation Conditions

Concepts

- notes

---

### 🏫 CloudFormation DependsOn

Concepts

- notes

---

### 🏫 CloudFormation Wait Conditions & cfn-signal

Concepts

- notes

---

### 🏫 CloudFormation Nested Stacks

Concepts

- notes

---

### 🏫 CloudFormation Cross-Stack References

Concepts

- notes

---

### 🏫 CloudFormation Stack Sets

Concepts

- notes

---

### 🏫 CloudFormation Deletion Policy

Concepts

- notes

---

### 🏫 CloudFormation Stack Roles

Concepts

- notes

---

### 🏫 CloudFormation Init (CFN-INIT)

Concepts

- notes

---

### 🏫 CloudFormation cfn-hup

Concepts

- notes

---

### 🏫 CloudFormation ChangeSets

Concepts

- notes

---

### 🏫 CloudFormation Custom Resources

Concepts

- notes

---
