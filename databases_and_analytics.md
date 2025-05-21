Relational Databases: A relational database is a structured way to organize and store data in tables, with rows and columns, where the data points are related to one another.

NoSQL Databases
· NoSQL = non-SQL = non relational databases
· NoSQL databases are purpose built for specific data models and have
flexible schemas for building modern applications.
· Benefits:
· Flexibility: easy to evolve data model
· Scalability: designed to scale-out by using distributed clusters
· High-performance: optimized for a specific data model
. Highly functional: types optimized for the data model
· Examples: Key-value, document, graph, in-memory, search databases
NoSQL is stored in json format

RDS : Relational Database Service is  SQL Query language.
It allowss you to create databases in cloud that are managed by AWS

Advantage over using RDS versus deploying
DB on EC2
· RDS is a managed service:
· Automated provisioning, OS patching
· Continuous backups and restore to specific timestamp (Point in Time Restore)!
· Monitoring dashboards
· Read replicas for improved read performance
· Multi AZ setup for DR (Disaster Recovery)
· Maintenance windows for upgrades
· Scaling capability (vertical and horizontal)
· Storage backed by EBS
. BUT you can't SSH into your instances

Amazon Aurora
· Aurora is a proprietary technology from AWS (not open sourced)
· PostgreSQL and MySQL are both supported as Aurora DB
· Aurora is "AWS cloud optimized" and claims 5x performance improvement
over MySQL on RDS, over 3x the performance of Postgres on RDS
· Aurora storage automatically grows in increments of 10GB, up to 128 TB
· Aurora costs more than RDS (20% more) - but is more efficient
· Not in the free tier

Amazon Aurora Serverless
· Automated database instantiation and auto-scaling based on actual usage
· PostgreSQL and MySQL are both supported as Aurora Serverless DB
· No capacity planning needed
· Least management overhead
· Pay per second, can be more cost-effective
· Use cases: good for infrequent,intermittent or unpredictable workloads.
exam perspective,
if you see Aurora with no management overhead and so on, think of Aurora Serverless.

 Read Replicas:
 . Scale the read workload of your DB
 · Can create up to 15 Read Replicas
 · Data is only read/written to the main database

· Multi-AZ:
· Failover in case of AZ outage (high availability)
· Data is only read/written to the main database
· Can only have I other AZ as failover

So anytime in the exam you see something that says you need an in-memory database, you have to think directly ElastiCache.

Amazon ElastiCache Overview
. The same way RDS is to get managed Relational Databases ...
· ElastiCache is to get managed Redis or Memcached
· Caches are in-memory databases with high performance, low latency
· Helps reduce load off databases for read intensive workloads
· AWS takes care of OS maintenance / patching, optimizations, setup,
configuration, monitoring, failure recovery and backups

DynamoDB 
It is a fully managed, highly available database
with replication across three availability zone. It is part of the NoSQL database family, so it's not a relational database. DynamoDB is one of the flagship product of AWS. It scales to massive workload and it's distributed serverless database, that means that we don't provision any servers.With RDS or with ElastiCache we need to provision a instance type, but with DynamoDB we don't.So it's called a serverless database,
keywords in exam,
such as serverless and low latency.
For example, single digit millisecond latency.

Then we have DynamoDB Accelerator also called DAX.
In the exam both can be used. So it is a fully managed in-memory cache for DynamoDB. So this is a cache that's specific for DynamoDB so it's not like ElastiCache.

Redshift
It is OLAP, or Online Analytic Analytical Processing, which is used to do analytics and data warehousing. So anytime in the exam you're saying a database needs to be a warehouse and to do analytics on it, then Redshift is going to be your answer. With Redshift, you don't load the data continuously. You load it, for example, every hour. And the idea with Redshift that is really, really good at analyzing data and making some computations. So it boasts 10x better performance than other data warehouses and scales to petabytes of data. The data is stored in columns, so it's called a columnar storage of data instead of row-based. So anytime you see columnar, again,