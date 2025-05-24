ECS
· ECS = Elastic Container Service
· Launch Docker containers on
AWS
· You must provision & maintain the infrastructure (the EC2 instances)
· AWS takes care of starting / stopping containers
. Has integrations with the Application Load Balancer

Fargate
· Launch Docker containers on
AWS
· You do not provision the
infrastructure (no EC2 instances
to manage) - simpler!
· Serverless offering
· AWS just runs containers for
you based on the CPU / RAM
you need


ECR
· Elastic Container Registry
· Private Docker Registry on AWS
· This is where you store your Docker images so they can be run by ECS or Fargate

Amazon EKS
· EKS = Elastic Kubernetes Service
· Allows you to launch managed Kubernetes clusters on AWS
· Kubernetes is an open-source system for management, deployment, and scaling of containerized apps (Docker)
· Containers can be hosted on:
· EC2 instances
· Fargate (Serverless)
· Kubernetes is cloud-agnostic
(can be used in any cloud - Azure, GCP ... )

Difference between EC2 and Lambda

EC2
. Virtual Servers in the Cloud
· Limited by RAM and CPU
· Continuously running
· Scaling means intervention to add / remove servers

LAMBDA
· Virtual functions - no servers to manage!
. Limited by time - short executions
· Run on-demand

Benefits of AWS Lambda
· Easy Pricing:
· Pay per request and compute time
· Free tier of 1,000,000 AWS Lambda requests and 400,000 GBs of compute time
. Integrated with the whole AWS suite of services
· Event-Driven: functions get invoked by AWS when needed
· Integrated with many programming languages
· Easy monitoring through AWS CloudWatch
· Easy to get more resources per functions (up to 10GB of RAM!)
. Increasing RAM will also improve CPU and network!

 Lambda pricing
is based on calls and duration.
AWS Lambda Pricing: example
· You can find overall pricing information here:
https://aws.amazon.com/lambda/pricing/
· Pay per calls:
· First 1,000,000 requests are free
· $0.20 per I million requests thereafter ($0.0000002 per request)
· Pay per duration: (in increment of | ms)
· 400,000 GB-seconds of compute time per month if FREE
· == 400,000 seconds if function is IGB RAM
· == 3,200,000 seconds if function is 128 MB RAM
. After that $1.00 for 600,000 GB-seconds
. It is usually very cheap to run AWS Lambda so it's very popular


    AMAZON API GATEWAY:
· Fully managed service for developers to easily create, publish, maintain,
monitor, and secure APIs
· Serverless and scalable
· Supports RESTful APls and WebSocket APIs
· Support for security, user authentication, API throttling, API keys, monitoring ...

AWS Batch
· Fully managed batch processing at any scale
· Efficiently run 100,000s of computing batch jobs on AWS
· A "batch" job is a job with a start and an end (opposed to continuous)
· Batch will dynamically launch EC2 instances or Spot Instances
. AWS Batch provisions the right amount of compute / memory
. You submit or schedule batch jobs and AWS Batch does the rest!
· Batch jobs are defined as Docker images and run on ECS
· Helpful for cost optimizations and focusing less on the infrastructure

Batch vs Lambda
· Lambda:
· Time limit
· Limited runtimes
. Limited temporary disk space
· Serverless
· Batch:
· No time limit
· Any runtime as long as it's packaged as a Docker image
· Rely on EBS / instance store for disk space

Amazon Lightsail
· Virtual servers, storage, databases, and networking
· Low & predictable pricing
· Simpler alternative to using EC2, RDS, ELB, EBS, Route 53 ...
· Great for people with little cloud experience!
· Can setup notifications and monitoring of your Lightsail resources
· Use cases:
· Simple web applications (has templates for LAMP, Nginx, MEAN, Node.js ... ]
· Websites (templates for WordPress, Magento, Plesk, Joomla)
· Dev / Test environment
· Has high availability but no auto-scaling, limited AWS integrations





