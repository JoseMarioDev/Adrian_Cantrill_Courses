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
- ex in demo: the bucket name for the bucket we're trying to create is already taken

---

### 🏫 CloudFormation Template and Pseudo Parameters

Concepts

- are two methods to provide input to a template, which can influence what resources are provisioned and the configuration of resources
- [AWS link to docs](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/pseudo-parameter-reference.html)
- let external sources provide input into templates when stack is created or updated
- can be configured with defaults, allowed values, min/max length, and allowed patterns, no echo, and type

Architecture Visually

- template interacts with the choices made by user or uses the default specified in the template

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ed85e2de-21d9-4c23-aa6d-f4b0d81951fc/Screen_Shot_2021-06-25_at_9.55.46_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ed85e2de-21d9-4c23-aa6d-f4b0d81951fc/Screen_Shot_2021-06-25_at_9.55.46_AM.png)

Pseudo Parameters

- AWS makes available that can be used in your template even if you don't define them
- they are created by AWS

  - AWS::Region
  - AWS::StackId
  - AWS::StackName
  - AWS::AccountId

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/be2e6adf-b8d3-414d-b73f-6bee51e4483c/Screen_Shot_2021-06-25_at_9.57.53_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/be2e6adf-b8d3-414d-b73f-6bee51e4483c/Screen_Shot_2021-06-25_at_9.57.53_AM.png)

---

### 🏫 CloudFormation Intrinsic Functions

Concepts

- [AWS doc on intrinsic functions](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference.html)
- CFN provides several built-in functions that help you manage your stacks
- Use intrinsic functions in your templates to assign values to properties that are not available until runtime
- allow access to data at runtime
- intrinsic functions:

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/275515ea-f483-4047-9b17-e1e0b0955743/Screen_Shot_2021-06-28_at_5.14.32_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/275515ea-f483-4047-9b17-e1e0b0955743/Screen_Shot_2021-06-28_at_5.14.32_PM.png)

Ref and GetAtt

- use on template or pseudo parameters to return their value
- !Ref - when used with logical resources, returns physical ID
- !GetAtt - used to retrieve any attribute associated with the resource

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ac9f23bd-78ec-49d9-b482-02acd93be86d/Screen_Shot_2021-06-28_at_5.19.30_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ac9f23bd-78ec-49d9-b482-02acd93be86d/Screen_Shot_2021-06-28_at_5.19.30_PM.png)

GetAZs and Select

- often used together
- returns list of AZs in a region
- use Select fn to reference AZ in a list

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cc9b8cc3-db63-4c52-a65c-f3ccff3cd81b/Screen_Shot_2021-06-28_at_5.22.04_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cc9b8cc3-db63-4c52-a65c-f3ccff3cd81b/Screen_Shot_2021-06-28_at_5.22.04_PM.png)

Join and Split

- used to join and split similar to programming

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a5ae2beb-5da1-46fb-b370-4b0beac6992b/Screen_Shot_2021-06-28_at_5.25.19_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a5ae2beb-5da1-46fb-b370-4b0beac6992b/Screen_Shot_2021-06-28_at_5.25.19_PM.png)

Base64 and Sub

- accepts text and passed output in Base64 encoded text
- sub allows you to do replacement on variables - think dynamic variable ${ variable }

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/39bb9104-dd9d-400e-9599-f8d95bc2ec5f/Screen_Shot_2021-06-28_at_5.27.43_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/39bb9104-dd9d-400e-9599-f8d95bc2ec5f/Screen_Shot_2021-06-28_at_5.27.43_PM.png)

Cidr

- provide CIDR range for VPC to use

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/03cf50b1-b97c-4a7b-929e-53c8f3fa0b12/Screen_Shot_2021-06-28_at_5.29.31_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/03cf50b1-b97c-4a7b-929e-53c8f3fa0b12/Screen_Shot_2021-06-28_at_5.29.31_PM.png)

---

### 🏫 CloudFormation Mappings

Concepts

- optional section matches a key to a set of named values
- can use the intrinsic function `!FindInMap` to retrieve values in a map
- templates can contain a mappings object
  - map keys to value
  - can have one key, or top and second levels
- use case: to retrieve a image id for a particular region
- improve template portability

Visually

- need to provide at least one top level key

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c6160182-0b2a-4bc9-b3d0-9ff7fd492038/Screen_Shot_2021-07-01_at_2.59.54_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c6160182-0b2a-4bc9-b3d0-9ff7fd492038/Screen_Shot_2021-07-01_at_2.59.54_PM.png)

---

### 🏫 CloudFormation Outputs

Concepts

- optional `Outputs` section declares output values that you can import into other stacks to create cross-stack references, return in response(to describe stack calls), or view in the AWS CFN console
- example: you can output the S3 bucket name for a stack to make the bucket easier to find
- provide status info and how to access services in a stack
- entirely optional
- values can be declared in this section
  - visible as outputs when using CLI
  - visible as outputs in console UI
  - accessible from a parent stack when using nesting
  - can be exported, allowing cross-stack references

Visually

- example of outputting a wordpress URL - using a key/value pair and the `!Join` function

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/eadbc47b-cd1f-41da-b0c0-17e38f982fc5/Screen_Shot_2021-07-02_at_8.11.07_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/eadbc47b-cd1f-41da-b0c0-17e38f982fc5/Screen_Shot_2021-07-02_at_8.11.07_PM.png)

---

### 🏫 CloudFormation Conditions

Concepts

- statements that define the circumstances under which entities are created or configured.
  - You might use conditions when you want to reuse a template that can create resources in different contexts, such as a test environment versus a production environment.
- In your template, you can add an `EnvironmentType` input parameter, which accepts either `prod` or `test` as inputs.
- Conditions are evaluated based on predefined pseudo parameters or input parameter values that you specify when you create or update a stack.
  - Within each condition, you can reference another condition, a parameter value, or a mapping. After you define all your conditions, you can associate them with resources and resource properties in the Resources and Outputs sections of a template
- optional. each condition is evaluated to true or false
- processed before resources are created
- uses other intrinsic functions
- associated with logical resources to control if they are created or not
- conditions can be nested

Visually

- ex: `EnvType` to declare if env is `dev` or `prod`

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2d72670a-9f90-462c-b8f4-4f5553bc7ff0/Screen_Shot_2021-07-04_at_3.05.14_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2d72670a-9f90-462c-b8f4-4f5553bc7ff0/Screen_Shot_2021-07-04_at_3.05.14_PM.png)

---

### 🏫 CloudFormation DependsOn

Concepts

- Attribute you can specify that the creation of a specific resource follows another
- when you add `DependsOn` attribute to a resource, the resource is only created after the creation of the resource specified

---

### 🏫 CloudFormation Wait Conditions & cfn-signal

Concepts

- `CreationPolicy`, `WaitConditions`, and `cfn-signal` can all be used together to prevent the status of a resource from reaching complete until AWS CloudFormation receives a specified number of success signals or a timeout period is exceeded
- the cfn-signal helper script signals AWS CloudFormation to indicate whether EC2 instances have been successfully created or updated

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
