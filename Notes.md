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

which is also called a backup, at any point of time that you wanted to. The idea is that you will be able to back up the state of it, and even if the EBS volume is terminated later on, you could restore it from that backup. Now to make a backup, it is not necessary to detach the volume prior to doing the backup, but it is recommended just to make sure that everything is clean on your EBS volume.