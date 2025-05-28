Amazon CloudWatch Logs
· CloudWatch Logs can collect log from:
· Elastic Beanstalk: collection of logs from application
· ECS: collection from containers
· AWS Lambda: collection from function logs
· CloudTrail based on filter
· CloudWatch log agents: on EC2 machines or on-premises servers
· Route53: Log DNS queries
· Enables real-time monitoring of logs
· Adjustable CloudWatch Logs retention

CloudWatch Logs for EC2
· By default, no logs from your EC2 instance will go to CloudWatch
· You need to run a CloudWatch agent on EC2 to push the log files you want
· Make sure IAM permissions are correct
· The CloudWatch log agent can be setup on-premises too

Amazon EventBridge
. Schema Registry: model event schema
. You can archive events (all/filter) sent to an event bus (indefinitely or set period)
· Ability to replay archived events.

So anytime there is an API call that needs to be looked up CloudTrail is going to be the right answer.
AWS CloudTrail
· Provides governance, compliance and audit for your AWS Account
· CloudTrail is enabled by default!
. Get an history of events / API calls made within your AWS Account by:
· Console
· SDK
· CLI
· AWS Services
· Can put logs from CloudTrail into CloudWatch Logs or S3
· A trail can be applied to All Regions (default) or a single Region.
· If a resource is deleted in AWS, investigate CloudTrail first!

X-Ray really is great when you see, distributed tracing, troubleshooting, and you want to have a service graph.

AWS CodeGuru
. Identify critical issues, security vulnerabilities, and hard-to-find bugs
· Example: common coding best practices,
resource leaks, security detection, input validation
· Uses Machine Learning and automated reasoning
· Hard-learned lessons across millions of code reviews on 1000s of open-source and Amazon repositories
· Supports Java and Python
· Integrates with GitHub, Bitbucket, and AWS CodeCommit

Monitoring Summary
· CloudWatch:
· Metrics: monitor the performance of AWS services and billing metrics
· Alarms: automate notification, perform EC2 action, notify to SNS based on metric
· Logs: collect log files from EC2 instances, servers, Lambda functions ...
· Events (or EventBridge): react to events in AWS, or trigger a rule on a schedule
· CloudTrail: audit API calls made within your AWS account
· CloudTrail Insights: automated analysis of your CloudTrail Events
· X-Ray: trace requests made through your distributed applications
· AWS Health Dashboard: status of all AWS services across all regions
. AWS Account Health Dashboard: AWS events that impact your infrastructure
· Amazon CodeGuru: automated code reviews and application performance recommendations.

