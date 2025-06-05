VPC & Subnets Primer
· VPC - Virtual Private Cloud: private network to deploy your resources (regional resource)
· Subnets allow you to partition your network inside your VPC
(Availability Zone resource)
. A public subnet is a subnet that is accessible from the internet
· A private subnet is a subnet that is not accessible from the internet
· To define access to the internet and between subnets, we use Route Tables.

Internet Gateway & NAT Gatewaay
· Internet Gateways helps our VPC instances connect with the internet
. Public Subnets have a route to the internet gateway.
· NAT Gateways (AWS-managed) &
NAT Instances (self-managed) allow your instances in your Private Subnets to access the internet while remaining private

Network ACL & Security ps
· NACL (Network ACL)
· A firewall which controls traffic from and to subnet
· Can have ALLOW and DENY rules
. Are attached at the Subnet level
· Rules only include IP addresses
· Security Groups
. A firewall that controls traffic to and from an EC2 Instance
· Can have only ALLOW rules
· Rules include IP addresses and other security groups
So just remember going to the exam that pretty much every service has an interface endpoint, but only DynamoDB and Amazon S3 also have a gateway endpoint.