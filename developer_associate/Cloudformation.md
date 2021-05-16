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
