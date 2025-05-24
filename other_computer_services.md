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



