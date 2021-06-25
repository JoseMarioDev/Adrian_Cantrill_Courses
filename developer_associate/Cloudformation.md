## 🗒️  Notes

### Basics

Concepts

- is IaC tool
- allows automation of infrastructure creation, updates, and deletes
- uses templates
- written in YAML or JSON

Template Body

- *Resources*
    - what is is your are creating. ex: EC2 instance, S3 bucket, etc
    - resource part is the only part of a template that is mandatory
- *Description*
    - free text field to give details about template
    - Description must immediately AWS template version is using it

    ```jsx
    AWSTemplateFormatVersion
    ```

- *Metadata*
    - control how diff things in template are presented in the console
    - controls how UI presents the template
- *Parameters*
    - add fields to prompt user for more info
- *Mappings*
    - optional - allows to create look up tables
- *Conditions*
    - allow decision making in template
    - create condition, then what
- *Outputs*
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
    - updating or deleting them as a template changes1
- templates are used to create stacks
    - stacks create physical resources from the logical resources in a template

        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1c8618ee-296a-423c-b86f-f340069936c7/Screen_Shot_2021-06-23_at_10.54.47_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1c8618ee-296a-423c-b86f-f340069936c7/Screen_Shot_2021-06-23_at_10.54.47_AM.png)

- can use a template to update a stack
- if you delete stack, the logical resources are deleted, so are the physical

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/256914b1-2e5c-4eab-9553-e233c2301e95/Screen_Shot_2021-06-23_at_10.56.15_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/256914b1-2e5c-4eab-9553-e233c2301e95/Screen_Shot_2021-06-23_at_10.56.15_AM.png)

Demo

- [AWS doc on resource and property types support by AWS CFN](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html)
- demo you will learn the negatives of non-portable templates

---

### 🏫 CloudFormation Template and Pseudo Parameters

Concepts

- are two methods to provide input to a template, which can influence what resources  are provisioned and the configuration of resources
- [AWS link to docs](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/pseudo-parameter-reference.html)

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