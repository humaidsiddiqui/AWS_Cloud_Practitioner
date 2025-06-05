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

So remember going into the exam, customer gateway and virtual private gateway are needed to establish a site-to-site VPN 

Transit Gateway
· For having transitive peering between thousands ofVPC and on-premises, hub-and-spoke (star) connection
· One single Gateway to provide this functionality
· Works with Direct Connect Gateway, VPN connections

VPC Closing Comments
· VPC: Virtual Private Cloud
. Subnets: Tied to an AZ, network partition of the VPC
. Internet Gateway: at the VPC level, provide Internet Access
· NAT Gateway / Instances: give internet access to private subnets
· NACL: Stateless, subnet rules for inbound and outbound
. Security Groups: Stateful, operate at the EC2 instance level or ENI
· VPC Peering: Connect two VPC with non overlapping IP ranges, nontransitive
. Elastic IP -fixed public IPV4, ongoing cost if not in use

VPC Closing Comments
· VPC Endpoints: Provide private access to AWS Services within VPC
· PrivateLink: Privately connect to a service in a 3rd party VPC
· VPC Flow Logs: network traffic logs
· Site to Site VPN: VPN over public internet between on-premises DC and AWS
· Client VPN: OpenVPN connection from your computer into your VPC
. Direct Connect: direct private connection to AWS
· Transit Gateway: Connect thousands ofVPC and on-premises networks together