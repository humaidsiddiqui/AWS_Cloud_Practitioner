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

The first service that is going to be very important for us to deploy a global application is Amazon Route 53. So, Route 53 is a managed DNS or Domain Name System.

Amazon Route 53 Overview 53
· Route53 is a Managed DNS (Domain Name System)
· DNS is a collection of rules and records which helps clients understand how to reach a server through URLs.

AWS Route 53 routing policies: 
https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html

Simple Routing Policy,

which has No health checks. So our Web browser will go into our DNS system, does a DNS query and gets an IPv4 for example as a result, that's a Simple Routing Policy.

Weighted Routing Policy
allows us to distribute the traffic across multiple Institute instances. So in this example, we have to assign weights to our Institute instances, for example, 70, 20, and 10, and then our DNS we'll make sure that our clients have 70% of the traffic onto the first one, 20% of the traffic onto the second one and 10% of the traffic on to the third one. This is effectively some kind of load balancing.

Latency Routing Policy 
we'll look at wherethe user is located. And if they're located close to will connect to that server

Failover Routing Policy
we have a client and we have a primary institute instance and a Failover one. And so our DNS system will do a Health check On the primary. And in case the primary instance fails, then we will be redirected to the failovers. This helps with disaster recovery.

after adding files into s3 bucket, we cannot access because it not public
let's see how we can instead use CloudFront to make these files accessible without making them public.

CloudFront is a global distribution so there's no region selection.

AWS Global Accelerator vs CloudFront
. They both use the AWS global network and its edge locations around the world
· Both services integrate with AWS Shield for DDoS protection.
. CloudFront - Content Delivery Network
· Improves performance for your cacheable content (such as images and videos)
· Content is served at the edge
· Global Accelerator
· No caching, proxying packets at the edge to applications running in one or more AWS Regions.
· Improves performance for a wide range of applications over TCP or UDP
· Good for HTTP use cases that require static IP addresses
. Good for HTTP use cases that required deterministic, fast regional failover
