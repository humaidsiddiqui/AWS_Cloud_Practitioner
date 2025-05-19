a little bit of IT terminology before we get started, the network is a bunch of cables, routers, and servers that are going to be connected with each other, and the router is a specific device that will forward the data packets between computer in the networks, and they will know where to send your packets on the internet,

just like your post delivery service. Now when we have a packet and it arrives as a destination, there's a switch, and the switch will send the packet to the correct clients on your network.

So if we put all these things together, it looks like this. Our client will send the data to a router, the router will find it's way all the way to a switch, and the switch will know to which computer in your network to send the data to.

cloud computing is the on-demand delivery of compute power database storage, application, and other IT resources.

IAM:  IAM stands for identity and access management. It is a global service because in IAM, we are going to create our users and assign them to group.

a AWS role is a way to give AWS entities permissions to do stuff on AWS.
IAM Summary: summary for IAM. We've seen IAM users and they should be mapped to an actual physical user within your company. And this user will have a password for the AWS console. Now we can group these users into groups and therefore users only. We can attach policies or share JSON documents that outline the permission for users or groups. And we can also create roles and these roles will be identities, but this time for maybe EC2 instances or other AWS services. We assume that for security we can enable multi-factor authentication so MFA and also set a password policy for our users. We can use the CLI to manage your services using the command line or the SDK to manage your AWS services, using a programming language. Finally, we can create access keys to access AWS using the CLI or the SDK. And finally, we can audit our IAM usage by creating an IAM credentials report and also using the IAM access advisor service.

SECTION 5 
EC2 INSTANCE:
https://aws.amazon.com/ec2/instance-types/ REFER THIS LINK FOR ALL ABOUT EC2 INSTANCES MODULES

SECTION 6:
An EBS Volume stands for Elastic Block Store. It's a network drive that you can attach to your instances while they run, and we've been using them without even knowing. So this EBS Volumes allow us to persist data, even after the instance is terminated. And so that's the whole purpose, we can recreate an instance and mount to the same EBS Volume from before and we'll get back our data.

So these EBS Volumes, at the CCP level, can only be mounted to one instance at a time!!! And when you create an EBS Volume, it is bound to a specific availability zone

EBS VLOUMES: are netowrk drive, it will be using the network.And because the network is used, there may be a bit of latency from one computer to reach to another server. It's attached through the network. Finally, it is possible for us to create EBS Volumes and leave them unattached they don't need to be necessarily attached to an ECG instance, they can be attached on demand
So by default, as we can see, the root EBS Volume

the root EBS Volume is deleted alongside the instance being terminated. So it's enabled and the default any other attached EBS Volume is not deleted because it's disabled by default.But obviously as we can see in this UI, we can control if you want to enable or disable delete on termination. And so use case right, would be for example, if you want to preserve the root volume, when an instance is terminated, So you can take your EBS volumes and make a snapshot,

which is also called a backup, at any point of time that you wanted to. The idea is that you will be able to back up the state of it, and even if the EBS volume is terminated later on, you could restore it from that backup. Now to make a backup, it is not necessary to detach the volume prior to doing the backup, but it is recommended just to make sure that everything is clean on your EBS volume. we can also copy snapshots across availability zones or regions, and the idea is that you would be able to transfer some of your data in a different region on AWS to leverage the global infrastructure. an EBS snapshot archive. So it allows you to move your snapshots to another storage tier called an archive tier, and that tier is 75% cheaper. So your snapshot is going to be moved, it takes you between 24 to 72 hours to restore from the archive. So on deleting the snapshots, it would go into recycle bin.

AMI stands for Amazon machine image and they represent a customization of an EC2 instance.
You can customize it into your own and what is in an AMI. if we create our own AMI

we're going to get a faster boot time and configuration time because all the software that we want to install onto our EC2 instance is going to be prepackaged through the AMI. So we have to build our own AMIs and they can be built for a specific region and then they can be copied across region if we wanted to use it and leverage the AWS global infrastructure.

EC2 Image Builder.It is used to automate the creation of virtual machines or container images.That means that you're gonna be able with EC2 Image Builder
to automate the creation, maintain, validate and test AMIs for EC2 instances.
Next, EC2 Image Builder can be run on a schedule.

So you can define a weekly schedule or you can say you can run whenever packages are updated or you can run it manually, et cetera, et cetera. And it is a free service, so you're only going to pay for the underlying resources.

EC2 Instance Store
· EBS volumes are network drives with good but "limited" performance
· If you need a high-performance hardware disk, use EC2 Instance Store
· Better I/O performance
. EC2 Instance Store lose their storage if they're stopped (ephemeral)
· Good for buffer / cache / scratch data / temporary content
· Risk of data loss if hardware fails
. Backup and replication are your responsibility
from an exam perspective anytime you see very high performance hardware attached volumefor your EC2 Instances, think local EC2 Instance Store.
That's it.

EFS:
So, before we had an EBS volume attached to only one EC2 instance at a time.But with an EFS drive, you can mount it onto hundreds of EC2 instances.
EFS - Elastic File System
· Managed NFS (network file system) that can be mounted on 100s of EC2
· EFS works with Linux EC2 instances in multi-AZ
· Highly available, scalable, expensive (3x gp2), pay per use, no capacity planning

DIFFERENCES BETWEEN EBS AND EFS:
So, with EBS, say we had EC2 instance in one AZ and another one.Then the EBS volume can only be attached to one instance in one specific AZ. And the EBS volumes are bound to specific availability zones. But if we wanted to move over the EBS volume from one AZ to another, we could create a snapshot, it would create an EBS snapshot and then restore that snapshot into a new availability zone. And effectively we would've moved the EBS volume over. But this is a copy, this is not an in-sync replica.This is a copy, and that would mean that this drive can now be used by another EC2 instance. 

EFS is a network file system. That means that whatever is on the EFS drive is shared by everything that is mounted to it. we have many instances in Availability Zone 1 on one or many instances as well on Availability Zone 2. At the same time, all these instances can mount the same EFS drive, okay, using a mount target, and they will all see the same files. So, that makes it a shared file system.

EFS Infrequent Access (EFS-IA)
· Storage class that is cost-optimized for files not
accessed every day
· Up to 92% lower cost compared to EFS Standard
· EFS will automatically move your files to EFS-IA
based on the last time they were accessed
· Enable EFS-IA with a Lifecycle Policy
· Example: move files that are not accessed for 60
days to EFS-IA
. Transparent to the applications accessing EFS

AWS RESPONSIBILITY:
AWS, of course, is responsible for their infrastructure, but also because in the technical specification of EBS, EFS, the tell you the data is replicated across many hardware, it is AWS responsibility to perform that replication. So that if one day some hardware is not working, you as a customer is not impacted.
Also, anytime an EBS drive would fail, or one part of it would fail. It is obviously AWS responsibility to replace that faulty hardware.

MY RESPONSIBILTIY:
setting up any backup or snapshot procedures
Well, setting up any backup or snapshot procedures and guidelines is very important to ensure that you don't lose your data. Setting up data encryption is another layer of protection to ensure that people cannot have access to your data, you need to understand the risks that are associated with it, which is that you can lose the drive if somehow there's a faulty hardware, or that if you stop or terminate the EC2 instance that has an instant store,then the data will be lost.So again, it would be responsibility to back it up in the first place.

AMAZON FSX: which is a managed service to get third-party high-performance file systems on AWS. high-performance file systems on AWS. So in case you don't wanna use EFS or S3, and you want something else, then you can use FSX

Amazon FSx for Windows File Server
 A fully managed, highly reliable, and scalable windows native shared file system, Built on Windows File Server
 Supports SMB protocol & Windows NTFS
 Integrated with Microsoft Active Directory
 Can be accessed from AWS or Corporate data center your on-premise infrastructure

Amazon FSx for Lustre
· A fully managed, high-performance, scalable file storage for High Performance
Computing (HPC)
· The name Lustre is derived from "Linux" and "cluster"
· Machine Learning, Analytics, Video Processing, Financial Modeling, ...
· Scales up to 100s GB/s, millions of IOPS, sub-ms latencies

EC2 Instance Storage - Summary
 EBS volumes:
· network drives attached to one EC2 instance at a time
. Mapped to an Availability Zones
· Can use EBS Snapshots for backups / transferring EBS volumes across AZ
AMI: create ready-to-use EC2 instances with our customizations
EC2 Image Builder: automatically build, test and distribute AMIs
EC2 Instance Store:
· High performance hardware disk attached to our EC2 instance
· Lost if our instance is stopped / terminated
EFS: network file system, can be attached to 100s of instances in a region
EFS-IA: cost-optimized storage class for infrequent accessed files
FSx for Windows: Network File System for Windows servers
ESx for Lustre: High Performance Computing Linux file system

Vertical Scalability
· Vertical Scalability means increasing the size
of the instance
· For example, your application runs on a
t2.micro

Horizontal Scalability: It means increasing the number of instances / system for your applition.
it implies to distributed file system and common for web applications
high availability is an example for horizontal scaling

Why use a load balancer?
· Spread load across multiple downstream instances
· Expose a single point of access (DNS) to your application
· Seamlessly handle failures of downstream instances
· Do regular health checks to your instances
· Provide SSL termination (HTTPS) for your websites
· High availability across zones

types of load balancers :
Application load balancer, Network Load balancer, gateway load balancer

Auto Scaling:
· In real-life, the load on your websites and application can change
. In the cloud, you can create and get rid of servers very quickly
. The goal of an Auto Scaling Group (ASG) is to:
· Scale out (add EC2 instances) to match an increased load
· Scale in (remove EC2 instances) to match a decreased load
· Ensure we have a minimum and a maximum number of machines running
· Automatically register new instances to a load balancer
· Replace unhealthy instances
. Cost Savings: only run at an optimal capacity (principle of the cloud)
