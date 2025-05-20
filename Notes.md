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

Auto Scaling Groups - Scaling Strategies
. Manual Scaling: Update the size of an ASG manually
. Dynamic Scaling: Respond to changing demand
· Simple / Step Scaling
· When a CloudWatch alarm is triggered (example CPU > 70%), then add 2 units
· When a CloudWatch alarm is triggered (example CPU < 30%), then remove |
· Target Tracking Scaling
. Example: I want the average ASG CPU to stay at around 40%
· Scheduled Scaling
· Anticipate a scaling based on known usage patterns
. Example : increase the minimum capacity to 10am to 5pm on firday

Predictive Scaling.
So this one uses Machine Learning to predict future traffic ahead of time so there's some algorithms, they will look at the past traffic patterns, and it will forecast what will happen to traffic based on the past patterns. And so the idea is that it's called predictive because we predict what the load will be over time, and maybe the load is just on a daily basis it peaks for three hours. So this is the kind of things that Predictive Scaling will pick up, okay. And it will automatically provision the right number of EC2 instances in advance to match that predicted period. So this is what the graphs you see on the right hand side. This is very helpful when you have time-based patterns and you just want to have an easy, without any intervention type of scaling trust strategies that is powered by Machine Learning, then that would be Predictive Scaling.

high availability
means that you are having your applicationsacross multiple availability zone.
Vertical scaling means that you're increasing the size of an instance.
And horizontal scaling, is that you are increasing the number of instances.
Elasticity is the ability to scale up and down based on demand. And agility is a concept of the Cloud that is going to be able to make you work faster, because you can create and delete resources very, very quickly.

load balancers, or ELB, are allowing us to distribute traffic across backend EC2 instances, and they can be spread out across multiple availability zones. We support health checks to make sure that the backend EC2 instances are indeed healthy.

auto scaling groups that allow us to implement elasticity for our application, therefore spreading our load across multiple AZ and scaling accordingly. So we scale these EC2 instances based on the demand on your system, and we can replace unhealthy instances.

AMAZON S3 BUCKET: 
· Amazon S3 allows people to store objects (files) in "buckets" (directories)
· Buckets must have a globally unique name (across all regions all accounts)
· Buckets are defined at the region level
· S3 looks like a global service but buckets are created in a region
· Naming convention
· No uppercase, No underscore
· 3-63 characters long
· Not an IP
· Must start with lowercase letter or number

Amazon S3 - Objects
· Objects (files) have a Key
· The key is the FULL path:
· s3://my-bucket/my_file.txt
· s3://my-bucket/my_folderl/another_folder/my_file.txt
· The key is composed of prefix + object name
· s3://my-bucket/my_folderl/another_folder/my_file.txt
. There's no concept of "directories" within buckets
(although the UI will trick you to think otherwise)
keys are just very, very long names that contain slashes and keys are made of a prefix and an object name.

Amazon S3 - Security
· User-Based
. IAM Policies - which API calls should be allowed for a specific user from IAM
· Resource-Based
· Bucket Policies - bucket wide rules from the S3 console - allows cross account
· Object Access Control List (ACL) - finer grain (can be disabled)
· Bucket Access Control List (ACL) - less common (can be disabled)
· Note: an IAM principal can access an S3 object if
. The user IAM permissions ALLOW it OR the resource policy ALLOWS it
. AND there's no explicit DENY
encryption is can be done in s3 bucket object.

S3 Bucket Policies
· JSON based policies
· Resources: buckets and objects
· Effect: Allow / Deny
. Actions: Set of API to Allow or Deny
Principal: 
The account or user to apply the policy to
· Use S3 bucket for policy to:
· Grant public access to the bucket
· Force objects to be encrypted at upload
· Grant access to another account (Cross
Account)

Amazon S3 - Versioning
· You can version your files in Amazon S3
. It is enabled at the bucket level
· Same key overwrite will change the "version": 1, 2, 3 ....
· It is best practice to version your buckets
· Protect against unintended deletes (ability to restore a version)
· Easy roll back to previous version
· Notes:
. Any file that is not versioned prior to enabling versioning will
have version "null"
· Suspending versioning does not delete the previous versions

S3 Storage Classes
· Amazon S3 Standard - General Purpose
· Amazon S3 Standard-Infrequent Access (IA)
· Amazon S3 One Zone-Infrequent Access
· Amazon S3 Glacier Instant Retrieval
· Amazon S3 Glacier Flexible Retrieval
· Amazon S3 Glacier Deep Archive
· Amazon S3 Intelligent Tiering
· Can move between classes manually or using S3 Lifecycle configurations


S3 Bucket Encryption:
What is server-side encryption?
Well, the user uploads an object into Amazon S3,
and then that object when it arrives in the bucket
is going to be encrypted by Amazon S3 for security purposes.
The idea is that the server is doing the encryption,
and therefore we call this server-side encryption.
On the opposite, we have client-side encryption.
This is when the user will actually take the file,
will encrypt it before uploading it,
so the lock is done by the user,
and then put it in the bucket.
And that's called client-side encryption.

IAM Access Analyzer for Amazon S3, this is a monitoring feature

for your Amazon S3 buckets to ensure

that only the intended people have access

to your S3 buckets.

So, how does that work?

Well, it's going to analyze your Bucket Policies,

your S3 ACLs, your S3 Access Point Policies,

and so on, and is going to surface to you

which buckets are going to be publicly accessible,

which buckets have been shared

with other AWS accounts and so on.

And the idea is that you can review this and say, okay,

this is normal, this is expected, or this looks a bit

as a security issue because I did not intend

to share this bucket with these people,

and therefore, you can take action.

And this is powered by IAM Access Analyzer,

S3 BUCKET SHARED RESPONSIBILITY: 
        AWS
· Infrastructure (global secur
durability, availability, sustair
concurrent loss of data in
two facilities)
· Configuration and
vulnerability analysis
· Compliance validation

        USER
· S3 Versioning
· S3 Bucket Policies
· S3 Replication Setup
· Logging and Monitoring
· S3 Storage Classes
· Data encryption at rest and in
transit

AWS Snowball.

So it's a highly secure and portable device that allows you to collect and process data at the edge and migrate data in and out of AWS.
So if you have a migration of say, petabytes of data, Snowball may be a good use case. So we have two kind of Snowball edge devices. One is called the Edge Storage Optimized, and the other one is called the Edge Compute Optimized. And the difference lies in their storage.
As you can see, one has 210 terabytes and the other one has 28 terabytes. Amazon S3 as a standalone service, but it is possible for you to use it in a hybrid cloud type of setting. So AWS wants you to bridge between your on-premises environment to AWS and that's called a hybrid cloud. So part of your infrastructure is going to be on-premises and the rest is going to be on the cloud. summarize the storage options on AWS, the block storage would be EBS or an EC2 instance store. The file storage would be a network file system so Amazon EFS, and object storage would be Amazon S3 or Glacier. And where does the Storage Gateway fit in all this? Well, the Storage Gateway is going to be bridging your on-premises data and cloud data in AWS.

Amazon S3 - Summary
· Buckets vs Objects: global unique name, tied to a region
· S3 security: IAM policy, S3 Bucket Policy (public access), S3 Encryption
· S3 Websites: host a static website on Amazon S3
· S3 Versioning: multiple versions for files, prevent accidental deletes
· S3 Replication: same-region or cross-region, must enable versioning
· S3 Storage Classes: Standard, IA, IZ-IA, Intelligent, Glacier (Instant, Flexible, Deep)
· Snow Family: import data onto S3 through a physical device, edge computing
· OpsHub: desktop application to manage Snow Family devices
· Storage Gateway: hybrid solution to extend on-premises storage to S3