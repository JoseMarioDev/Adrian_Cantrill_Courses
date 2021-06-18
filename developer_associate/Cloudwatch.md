## 🗒️ Notes

### 🌪️ Basics

Concepts

- service that provides metric, log, and event management services
- used by AWS services for health and performance monitoring, log management, and nerveless architectures
- collects and manages operational data
- 3 main services

Metrics

- collection of related data points in a time ordered structure
- data related to AWS products, apps, and onprem
- some metrics are gathered natively
- some need to have cloudwatch agent installed to work

Logs

- allows for collection, monitoring, actions based on logging data

Events

- function as a hook
- when something happens(metric or log action) do something
- do something on a certain time or day or week - schedule

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/40baa583-b1f7-435c-8d8e-81abe211b46f/Screen_Shot_2021-05-16_at_2.41.39_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/40baa583-b1f7-435c-8d8e-81abe211b46f/Screen_Shot_2021-05-16_at_2.41.39_PM.png)

Namespace

- container for monitoring data
- data captured by metrics are stored as datapoints
  - contain 2 parts → timestamp and value

Alarms

- take actions based on metrics
- created and linked to a metric
- based on config, takes action based on metric

---

### 📓 Logs

Concepts

- public service - usable from AWS VPCs or on-prem
- store, monitor, access logging data
  - timestamp and data
- integrates w/AWS services - EC2, VPC flow logs, Lambda, Cloudtrail, R53, etc
- can generates metrics based on logs aka metric filter
- regional service

Architecture

- sources(AWS services, apps, databases, etc) inject data into CW logs
- they create log events
  - timestamp and message
  - stored inside log streams - log events from same source
- log groups - containers for multiple log streams
  - store config settings for log groups
  - define metric filters in log groups
- metric filters → metric → trigger an alarm

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/487d65c8-6b78-4c31-b3e8-0ced5bd968eb/Screen_Shot_2021-05-19_at_12.45.59_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/487d65c8-6b78-4c31-b3e8-0ced5bd968eb/Screen_Shot_2021-05-19_at_12.45.59_PM.png)

---

### 🐌 CloudTrail

Concepts

- product which logs API calls and account events
  - activity is called CloudTrail Events
  - 90 days stored by default
- used to diagnose security or performance issues
- or to provide account level traceability
- enabled by default in AWS accounts
- can be configured to store data indefinitely in S3 or CW Logs
- regional service

Events

- 90 days stored by default in event history
- enabled by default
- 2 types of events
  1. Management Events
     - logged by default
  2. Data Events

Trails

- can be one region or all region
- one region only logs the region it's in
- events are logged in the region they are in
- global services - IAM, R53, STS store their events in `US-EAST-1`
- trails can store events in S3 buckets
  - compressed JSON log files
  - can also store in CW logs
- can create Organizational trails
  - store info for all accounts in Org

Exam Power Up

- enabled by default but only for 90 days; no S3 by default
- Trails are how you configure S3 and CW logs
- management events only are logged by default
- a cost can be associated
- IAM, STS, Cloudront - global service events, log to `us-east-1`
- not real time, up to 15 minute delay

---

### 🔍 CloudWatch Architecture

Concepts

- product that ingests, stores, and manages metrics
  - think metrics
- public service - public endpoint
- need to integrate
- can use CW Agent ex: EC2 use for richer metrics
- can use on prem via agent/api
- can deliver custom metrics
- can provide alarms that react to metrics

Visually

- CW sits in public zone and records metrics
- services in VPCs can publish data into CW
  - via GW or interface endpoint
- alarms can create actions like SNS notifications, ASG scaling, Eventbridge events

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/08f6f702-6c45-4518-990f-bd600b9c36e4/Screen_Shot_2021-06-18_at_1.57.54_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/08f6f702-6c45-4518-990f-bd600b9c36e4/Screen_Shot_2021-06-18_at_1.57.54_PM.png)

Data

-

---

### 🔍 CloudWatch Logs Architecture

Concepts

- Namespace = container for metrics eg: AWS/EC2 or AWS/Lambda
- Datapoint = timestamp, value, unit of measure(optional)
- Metric = time ordered set of data points ex: CPUUtlization, NetworkIn
  - every metric has a MetricName and Namespace
- Dimension = name/value pair

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f0c6f71c-d08f-42d9-b6d3-a9783acd507a/Screen_Shot_2021-06-18_at_2.15.23_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f0c6f71c-d08f-42d9-b6d3-a9783acd507a/Screen_Shot_2021-06-18_at_2.15.23_PM.png)

---

### 🔍 AWS X-Ray

Concepts

- notes
