DDOS Protection on AWS
· AWS Shield Standard: protects against DDOS attack for your website and applications, for all customers at no additional costs
· AWS Shield Advanced: 24/7 premium DDOS protection
· AWS WAF: Filter specific requests based on rules
· CloudFront and Route 53:
· Availability protection using global edge network
. Combined with AWS Shield, provides attack mitigation at the edge
· Be ready to scale - leverage AWS Auto Scaling
ss
AWS Network Firewall
· Protect your entire Amazon VPC
· From Layer 3 to Layer 7 protection
· Any direction, you can inspect
· VPC to VPC traffic
· Outbound to internet
· Inbound from internet
· To / from Direct Connect & Site-to-Site VPN

penetration testing is when you're trying to attackyour own infrastructure to test your security.A customer of AWS is welcome to carry out these security assessments and penetration testing against your own infrastructure without prior approval for eight services.

Amazon GuardDuty
. Intelligent Threat discovery to protect your AWS Account
· Uses Machine Learning algorithms, anomaly detection, 3rd party data
· One click to enable (30 days trial), no need to install software
GuardDuty is a very good tool to protect you against cryptocurrency attacks  because there is a dedicated finding for it.

Amazon Macie
· Amazon Macie is a fully managed data security and data privacy service that uses machine learning and pattern matching to discover and protect your sensitive data in AWS.
. Macie helps identify and alert you to sensitive data, such as personally identifiable information (PII)

Amazon Detective
. GuardDuty, Macie, and Security Hub are used to identify potential security issues, or findings
· Sometimes security findings require deeper analysis to isolate the root cause and take action - it's a complex process
· Amazon Detective analyzes, investigates, and quickly identifies the root cause of security issues or suspicious activities (using ML and graphs)
· Automatically collects and processes events from VPC Flow Logs, CloudTrail, GuardDuty and create a unified view

AWS Abuse
· Report suspected AWS resources used for abusive or illegal purposes
· Abusive & prohibited behaviors are:
· Spam - receving undesired emails from AWS-owned IP address, websites & forums spammed by AWS resources
· Port scanning - sending packets to your ports to discover the unsecured ones
· DoS or DDOS attacks - AWS-owned IP addresses attempting to overwhlem or crash your servers/softwares
· Intrusion attempts - logging in on your resources
· Hosting objectionable or copyrighted content - distributing illegal or copyrighted content without consent
· Distributing malware - AWS resources distributing softwares to harm computers or machines
· Contact the AWS Abuse team: AWS abuse form, or abuse@amazonaws.com

Root user privileges
. Root user = Account Owner (created when the account is created)
· Has complete access to all AWS services and resources
· Lock away your AWS account root user access keys!
· Do not use the root account for everyday tasks, even administrative tasks
. Actions that can be performed only by the root user:
· Change account settings (account name, email address, root user password, root user access keys)
· View certain tax invoices
· Close your AWS account
· Restore IAM user permissions
· Change or cancel your AWS Support plan
· Register as a seller in the Reserved Instance Marketplace
· Configure an Amazon S3 bucket to enable MFA
· Edit or delete an Amazon S3 bucket policy that includes an invalidVPC ID or VPC endpoint ID
· Sign up for GovCloud

Section Summary: Security & Compliance
. Shared Responsibility on AWS
· Shield: Automatic DDOS Protection + 24/7 support for advanced
· WAF: Firewall to filter incoming requests based on rules
· KMS: Encryption keys managed by AWS
· CloudHSM: Hardware encryption, we manage encryption keys
· AWS Certificate Manager: provision, manage, and deploy SSL/TLS Certificates
· Artifact: Get access to compliance reports such as PCI, ISO, etc ...
. GuardDuty: Find malicious behavior with VPC, DNS & CloudTrail Logs
· Inspector: find software vulnerabilities in EC2, ECR Images, and Lambda functions
· Network Firewall: Protect VPC against network attacks
· Config: Track config changes and compliance against rules
· Macie: Find sensitive data (ex: PII data) in Amazon S3 buckets
· CloudTrail: Track API calls made by users within account
· AWS Security Hub: gather security findings from multiple AWS accounts
· Amazon Detective: find the root cause of security issues or suspicious activities
· AWS Abuse: Report AWS resources used for abusive or illegal purposes
· Root user privileges:
· Change account settings
· Close your AWS account
· Change or cancel your AWS Support plan
· Register as a seller in the Reserved Instance Marketplace
· IAM Access Analyzer: identify which resources are shared externally