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