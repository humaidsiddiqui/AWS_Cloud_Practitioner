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

Amazon EMR
· EMR stands for"Elastic MapReduce"
· EMR helps creating Hadoop clusters (Big Data) to analyze and process
vast amount of data
· The clusters can be made of hundreds of EC2 instances
· Also supports Apache Spark, HBase, Presto, Flink ...
· EMR takes care of all the provisioning and configuration
· Auto-scaling and integrated with Spot instances
· Use cases: data processing, machine learning, web indexing, big data ...

Amazon Athena.
So from an exam perspective,
whenever you see serverless analyze data in S3
use SQL, then think Amazon Athena.

Amazon Athena is a serverless query service to perform analytics against your objects stored in Amazon S3.
So the idea is that you would use the SQL query language to create these files, but you don't need to load them. They just need to be in S3 and Athena will do the rest. So these files can be formatted in different ways, such as CSV, JSON, ORC, Avro, and Parquet and the Athena is built on the Presto engine

Amazon QuickSight.

So it's a serverless, machine learning-powered business intelligence service to create interactive dashboards. So behind this very complicated tagline, all you have to remember is that Amazon QuickSight allows you to create dashboards on your databases so we can visually represent your data and show your business users the insights they're looking for, okay. So QuickSight allows you to create all these kind of cool graphs, charts, and so on. So it's fast, it's automatically scalable. It's embeddable and there's per-session pricing, so you don't have to provision any servers.

we have DocumentDB, which is an Aurora version for MongoDB.
compatible with MongoDB.

So MongoDB is used to store query and index JSON data, and you have the same similar deployment concept as Aurora with DocumentDB. So that means it's a fully managed database, it's highly available. Data is replicated across three availability zones and DocumentDB storage automatically will grow in increments of 10 gigabytes, and DocumentDB has been engineered so it can scale to workloads with millions of requests per second.

Neptune 
Neptune is a fully-managed graph database. Neptune is a great choice of database when it comes to graph datasets.
 exam perspective,
anytime you see anything related to graph databases, think no more than Neptune.

Amazon Timestream
· Fully managed, fast, scalable, serverless time
series database
· Automatically scales up/down to adjust
capacity
· Store and analyze trillions of events per day
. 1000s times faster & 1/10th the cost of
relational databases

Amazon QLDB
· QLDB stands for "Quantum Ledger Database"
· A ledger is a book recording financial transactions
· Fully Managed, Serverless, High available, Replication across 3 AZ
. Used to review history of all the changes made to your application data over time
· Immutable system: no entry can be removed or modified, cryptographically verifiable

So the difference between QLDB and Managed Blockchain is that QLDB has a central authority component and it's a ledger, whereas managed blockchain is going to have a de-centralization component as well. So that's it, anytime you see financial transactions and ledger, think QLDB.

AMAZON MANAGED BLOCKCHAIN
So from an exam perspective, if you see anything related to Blockchains or Hyperledger fabric or Ethereum, you have to think Amazon managed Blockchain which is also a decentralized Blockchain, okay? So make sure you remember that and that's it, all you want to know for the exam

Glue 
is a managed extract, transform, and load service,or ETL, and from an exams perspective, that's all you need to know.

DATA MIGRATION:
how do you migrate data from one database to another? 
For this we can use DMS which is properly named the Database Migration Service. So we use source database and once we extract the data so we'll run an EC2 instance that will be running the DMS software. We'll extract the data from the source database and then DMS will insert the data back into a target database that will be somewhere else. So with DMS we get a quick and secure database migration

Databases & Analytics Summary in AWS
· Relational Databases - OLTP: RDS & Aurora (SQL)
· Differences between Multi-AZ, Read Replicas, Multi-Region
· In-memory Database: ElastiCache
· Key/Value Database: DynamoDB (serverless) & DAX (cache for DynamoDB)
· Warehouse - OLAP: Redshift (SQL)
· Hadoop Cluster: EMR
· Athena: query data on Amazon S3 (serverless & SQL)
· QuickSight: dashboards on your data (serverless)
· DocumentDB: "Aurora for MongoDB" (JSON - NoSQL database)
· Amazon QLDB: Financial Transactions Ledger (immutable journal, cryptographically verifiable)
· Amazon Managed Blockchain: managed Hyperledger Fabric & Ethereum blockchains
· Glue: Managed ETL (Extract Transform Load) and Data Catalog service
· Database Migration: DMS
. Graph Database: Neptune
. Timestream database: Time-series database.
