What is CloudFormation?
· CloudFormation is a declarative way of outlining your AWS Infrastructure, for any resources (most of them are supported).
· For example, within a CloudFormation template, you say:
· I want a security group
. I want two EC2 instances using this security group
· I want an S3 bucket
· I want a load balancer (ELB) in front of these machines
. Then CloudFormation creates those for you, in the right order, with the exact configuration that you specify.

CloudFormation is going to be used when we have infrastructure as code, when we need to repeat an architecture in different environments, different regions, or even different AWS accounts.

AWS Cloud Development Kit (CDK)
· Define your cloud infrastructure using a familiar language:
· JavaScript/TypeScript, Python, Java, and .NET
· The code is "compiled" into a CloudFormation template (JSON/YAML)
· You can therefore deploy infrastructure and application runtime code together
· Great for Lambda functions
· Great for Docker containers in ECS / EKS

AWS Elastic Beanstalk Overview
· Elastic Beanstalk is a developer centric view of deploying an application on AWS
· It uses all the component's we've seen before: EC2, ASG, ELB, RDS, etc ...
. But it's all in one view that's easy to make sense of!
· We still have full control over the configuration
· Beanstalk = Platform as a Service (PaaS)
· Beanstalk is free but you pay for the underlying instances

Beanstalk does have a full monitoring suite available within the service itself. And so there's going to be a health agent on each EC2 instance within Beanstalk that is going to push metrics to CloudWatch. And then within Beanstalk you can view these metrics, do some monitoring and so on. But it will also check for application health and will publish health events.

AWS CodeDeploy
· We want to deploy our application automatically
· Works with EC2 Instances
· Works with On-Premises Servers
· Hybrid service
· Servers / Instances must be provisioned and configured ahead of time with the CodeDeploy Agent

AWS CodePipeline
. Orchestrate the different steps to have the code automatically pushed to production
· Code => Build =>Test => Provision => Deploy
· Basis for CICD (Continuous Integration & Continuous Delivery)
· Benefits:
. Fully managed, compatible with CodeCommit, CodeBuild, CodeDeploy, Elastic Beanstalk,
CloudFormation, GitHub, 3rd-party services (GitHub ... ) & custom plugins ...
· Fast delivery & rapid updates
CodePipeline: orchestration layer

CodeCommit->CodeBuild->CodeDeploy->Elastic Beanstalk

AWS CodeArtifact
· Software packages depend on each other to be built (also called code dependencies), and new ones are created
· Storing and retrieving these dependencies is called artifact management
· Traditionally you need to setup your own artifact management system
· CodeArtifact is a secure, scalable, and cost-effective artifact management for software development
· Works with common dependency management tools such as Maven, Gradle, npm, yarn, twine, pip, and NuGet
· Developers and CodeBuild can then retrieve dependencies straight from CodeArtifact

from an exam perspective, anytime you see a way to patch your fleet of EC2 instances or On-Premises servers, you have to think about SSM, or if you wanted to run a command consistently across all your servers, again, SSM would be the right way.

AWS Systems Manager (SSM)
· Helps you manage your EC2 and On-Premises systems at scale
· Another Hybrid AWS service
· Get operational insights about the state of your infrastructure
· Suite of 10+ products
· Most important features are:
· Patching automation for enhanced compliance
· Run commands across an entire fleet of servers
· Store parameter configuration with the SSM Parameter Store
. Works for Linux, Windows, MacOS, and Raspberry Pi OS (Raspbian)

if we look at our EC2 instances and on-premise virtual machines, we first have to install the SSM agent on all of these,   and the SSM agent will be reporting back to the SSM service in AWS.As you can see, it is linked to both EC2 instances and On-Premises VM, so this makes it a hybrid service. Now if an instance cannot be controlled by SSM, it's only probably an issue with the agent, and now that the agent is installed on both our servers and our EC2 instances, then we can use the  SSM service to run commands across all these servers, or we can patch them all at once, or we can configure them consistently using the SSM service.

let's create a role.

For a service on AWS, it will be Amazon EC2. Click on next. Then, for permissions, we're going to filter for SSM and we will choose the Amazon SSM managed instance core.

Fleet Manager is a service where all the EC2 instances that are registered with SSM will appear here. So they're called managed nodes.

So that means that using the SSM secure shell, we're able to have indeed a secure shell directly from AWS without having SSH security keys and SSH access.

Systems Manager - SSM Session Manager
· Allows you to start a secure shell on your EC2 and EC2 Instance on-premises servers
. No SSH access, bastion hosts, or SSH keys needed commands
· No port 22 needed (better security) Session Manager
· Supports Linux, macOS, and Windows
· Send session log data to S3 or CloudWatch Logs

EC2 Instance <- Execute commands <- session manager <- IAM Roles <- User.

Systems Manager
Parameter Store
· Secure storage for configuration and secrets
· API Keys, passwords, configurations ...
· Serverless, scalable, durable, easy SDK
· Control access permissions using IAM
· Version tracking & encryption (optional)

Deployment - Summary
· CloudFormation: (AWS only)
· Infrastructure as Code, works with almost all of AWS resources
· Repeat across Regions & Accounts
· Beanstalk: (AWS only)
· Platform as a Service (PaaS), limited to certain programming languages or Docker
· Deploy code consistently with a known architecture: ex, ALB + EC2 + RDS
· CodeDeploy (hybrid): deploy & upgrade any application onto servers
· Systems Manager (hybrid): patch, configure and run commands at scale

Developer Services - Summary
· CodeCommit: Store code in private git repository (version controlled)
· CodeBuild: Build & test code in AWS
· CodeDeploy: Deploy code onto servers
· CodePipeline: Orchestration of pipeline (from code to build to deploy)
· CodeArtifact: Store software packages / dependencies on AWS
· AWS CDK: Define your cloud infrastructure using a programming language

Global Applications in AWS
· Global DNS: Route 53
. Great to route users to the closest deployment with least latency
· Great for disaster recovery strategies
. Global Content Delivery Network (CDN): CloudFront
· Replicate part of your application to AWS Edge Locations - decrease latency
· Cache common requests - improved user experience and decreased latency
· S3 Transfer Acceleration
· Accelerate global uploads & downloads into Amazon S3
· AWS Global Accelerator:
· Improve global application availability and performance using the AWS global network
