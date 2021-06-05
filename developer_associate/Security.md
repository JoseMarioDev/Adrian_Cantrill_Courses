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

---

### AWS Permissions Evaluation

Concepts

---

### CloudHSM

Concepts
