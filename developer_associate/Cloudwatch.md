## 🗒️ Notes

### Basics

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
