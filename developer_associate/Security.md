## 🗒️ Notes

3 examples of policy interpretation

### Policy Interpretation Deep Dive - Example 1

Concepts

- step through IAM policy examples and learn how to interpret them, understand their effects
- policy evaluation → [https://github.com/acantril/aws-dev-associate/blob/main/08_Security/PolicyEvaluation/policy1_holidaygifts.json](https://github.com/acantril/aws-dev-associate/blob/main/08_Security/PolicyEvaluation/policy1_holidaygifts.json)

Steps to understanding a policy document

1. identify how many statements make up policy document
   1. either single or list of statements - square brackets
   2. can be a list of objects
2. identify the effect of each statement
   1. what it actually does
   2. `Effect` is either `allow` or `deny`
   3. `Resource` identifies what is being affected
      1. wild card means all objs inside bucket
   4. example 1 has a `Condition` block

---

### Policy Interpretation Deep Dive - Example 2

Concepts

- learn how to restrict usage of regions via IAM policies and learn about `NotAction` conditions
- policy evaluated → [https://github.com/acantril/aws-dev-associate/blob/main/08_Security/PolicyEvaluation/policy2_region.json](https://github.com/acantril/aws-dev-associate/blob/main/08_Security/PolicyEvaluation/policy2_region.json)
- example uses inverse logic by using not operations
- deny policies are usually accompanied by an allow policy
  - because by default, things are denied

---

### Policy Interpretation Deep Dive - Example 3

Concepts

- how to secure S3 based on home folders and IAM policy variables
- policy evaluated → [https://github.com/acantril/aws-dev-associate/blob/main/08_Security/PolicyEvaluation/policy3_homefolders.json](https://github.com/acantril/aws-dev-associate/blob/main/08_Security/PolicyEvaluation/policy3_homefolders.json)
- AWS documentation on variables and tags

[IAM policy elements: Variables and tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_variables.html)

- this policy performs a prefix condition check to interact inside home folder only
  - using`${aws:username}` variable

---

### AWS Permissions Evaluation

Concepts

- policy evaluation process AWS uses for single and multi-account access scenarios
- same process is used each and every time an identity attempts to access a resource

Considerations

1. Organization SCPs
2. Resource policies
3. IAM identity boundaries
4. Session policies - when using roles
5. identity policies

Flow to evaluate permissions

1. first checks to see if there is an explicit deny. if so, game over
2. are there any SCPs?
   1. do they allow the action? if not, implicit deny
3. is there a resource policy?
   1. if yes, all good
4. are there any permission boundaries?
5. are there any session policies?
6. identity policies?

Visually

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/76997cf6-5498-4151-a5a3-002b4ec99434/Screen_Shot_2021-06-06_at_10.39.35_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/76997cf6-5498-4151-a5a3-002b4ec99434/Screen_Shot_2021-06-06_at_10.39.35_AM.png)

Multiple Accounts Evaluation Logic

- require applicable allow from account A and Account B

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/541ed849-05a1-4ed1-9905-ca3b540aa6fc/Screen_Shot_2021-06-06_at_10.41.56_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/541ed849-05a1-4ed1-9905-ca3b540aa6fc/Screen_Shot_2021-06-06_at_10.41.56_AM.png)

---

### CloudHSM

Concepts
