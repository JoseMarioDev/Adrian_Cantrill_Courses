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

- Namespace = container for metrics eg: AWS/EC2 or AWS/Lambda
- Datapoint = timestamp, value, unit of measure(optional)
- Metric = time ordered set of data points ex: CPUUtlization, NetworkIn
  - every metric has a MetricName and Namespace
- Dimension = name/value pair

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f0c6f71c-d08f-42d9-b6d3-a9783acd507a/Screen_Shot_2021-06-18_at_2.15.23_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f0c6f71c-d08f-42d9-b6d3-a9783acd507a/Screen_Shot_2021-06-18_at_2.15.23_PM.png)

- Resolution = standard(60s granularity). min time period you can get one datapoint for
- Retention = see slide
- Statistics = aggregate data over a period /image
- Percentile = relative standing of data in a value set

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/60c26693-5997-40ad-a22c-a4944a3a4e3a/Screen_Shot_2021-06-18_at_2.22.12_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/60c26693-5997-40ad-a22c-a4944a3a4e3a/Screen_Shot_2021-06-18_at_2.22.12_PM.png)

Alarms

- watches a metric over a given time period
- state will either be `Alarm` or `OK`
- can be config with one or more action
- can specify alarm resolution

Alarms Visually

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3af3aba3-82f8-405e-a1c2-cafb1b2f87d5/Screen_Shot_2021-06-18_at_2.25.54_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3af3aba3-82f8-405e-a1c2-cafb1b2f87d5/Screen_Shot_2021-06-18_at_2.25.54_PM.png)

---

### 🔍 CloudWatch Logs Architecture

Concepts

- is a product which can store, manage, provide access to logging data for on-prem and AWS environments including systems and apps
- has 2 sides - ingestion and subscription
- via subscription, can also filter streams of data to Lambda, Elasticsearch, Kinesis and firehose
- metric filters can be used to generate metrics with CW, alarms, and events with Eventbridge

Ingestion

- supports AWS services natively, but if you want to ingest data from apps, need to use CWAgent
- can support VPC, Cloudtrail, Elastic Beanstalk, ECS, API GW, Lambda, Route 53

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ffb24b4d-89d7-4291-9fed-11ff91ea627a/Screen_Shot_2021-06-19_at_10.52.44_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ffb24b4d-89d7-4291-9fed-11ff91ea627a/Screen_Shot_2021-06-19_at_10.52.44_AM.png)

Architecture

- sends data to the region it's in
- log events consist of timestamp and message
- events are stored in log streams
- log streams are in a log group - log events from same source
- set retention, permissions, encryption on log groups
- metric filters defined on log groups, can trigger alarms
- can export to S3, but not in real time

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6aee9616-d9dc-44da-9ce0-e602b9bbc7cb/Screen_Shot_2021-06-19_at_10.56.55_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6aee9616-d9dc-44da-9ce0-e602b9bbc7cb/Screen_Shot_2021-06-19_at_10.56.55_AM.png)

Subscriptions

- can use subscriptions for real time or near real time logging
- log group sends data to a subscription
- subscription sends data to other sources like Kinesis, Lambda, Elasticsearch

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aabebbca-4947-4aae-aaeb-25645dcdf69f/Screen_Shot_2021-06-19_at_10.59.37_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aabebbca-4947-4aae-aaeb-25645dcdf69f/Screen_Shot_2021-06-19_at_10.59.37_AM.png)

Aggregation

- can use subscriptions to aggregate data from multiple logs

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3e6cdec2-94f3-42f8-93e5-174e489ce4a2/Screen_Shot_2021-06-19_at_11.00.48_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3e6cdec2-94f3-42f8-93e5-174e489ce4a2/Screen_Shot_2021-06-19_at_11.00.48_AM.png)

Summary

- for any log solutions should default to CW logs
- can export to S3 but not real time
- for real time use subscriptions to Kinesis datastream or Lambda
- near realtime use Kinesis Firehose
- can also send to Elasticsearch using Lambda
- can use metric filters

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ccea43a3-0269-4c80-9f5a-4968e8346c45/Screen_Shot_2021-06-19_at_11.02.40_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ccea43a3-0269-4c80-9f5a-4968e8346c45/Screen_Shot_2021-06-19_at_11.02.40_AM.png)

---

### 🔍 AWS X-Ray

Concepts

- notes
