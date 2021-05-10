## 🗒️ Notes

---

🧑🏻 Accounts

- Creating an AWS account requires an account name, unique email, and credit card for billing
- A root user is created after creating an account
  - Root user has full control over this AWS account and any resources inside the account and cannot be restricted
- IAM users, groups, and roles can also be created and given full or restricted permissions
  - by default, no permissions are given to IAM users
  - you have to explicitly grant permissions
- will be creating a general and production AWS accounts

---

🔐 Mulit-Factor Authentication

- using MFA

  - a diff piece of evidence used to prove identity
  - makes it harder to get hacked because to successfully log in you need to be verified twice suing 2 diff methods:
    - something I know(my password)
    - something I have(mfa device/app)
    - ex: Google Authenticator, 1password, Authy

  ***

💲 Billing

- create billing alerts to notify you of spending/usage
- can be doing using billing preferences or new Budget service

---

💁🏽. IAM Basics

- IAM identities start with no permissions on an AWS Account, but can be granted permissions (almost) up to those held by the Account Root User.
- Globally resilient service
- can create three different types of identity objects
  - users - humans or apps that need access to your acct
  - groups - collection of related users
  - roles - used by AWS services(ex: EC2) or for granting external access to your account
- can also create policy documents
  - used to allow/deny access to AWS services
- IAM has three main jobs:
  - manage identities
  - authenticate
  - authorize
- best practice is to not use the root user - create a new user w/appropriate permissions
- IAM Access Keys
