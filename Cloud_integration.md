Section Introduction
· Synchronous between applications can be problematic if there are
sudden spikes of traffic
. What if you need to suddenly encode 1000 videos but usually it's IO?
. In that case, it's better to decouple your applications:
· using SQS: queue model
· using SNS: pub/sub model
· using Kinesis: real-time data streaming model

Amazon SQS - Standard Queue
· Oldest AWS offering (over 10 years old)
· Fully managed service (~serverless), use to decouple applications
· Scales from | message per second to 10,000s per second
· Default retention of messages: 4 days, maximum of 14 days
· No limit to how many messages can be in the queue
· Messages are deleted after they're read by consumers
· Low latency (<10 ms on publish and receive)

Amazon SQS - FIFO Queue
· FIFO = First In First Out (ordering of messages in the queue)
· Messages are processed in order by the consumer
and it's just a feature you need to remember for the exam.

Amazon Kinesis Data Streams
· For the exam: Kinesis = real-time big data streaming
· Managed service to collect, process, and analyze real-time streaming
data at any scale

Amazon SNS
. The "event publishers" only sends message to one SNS topic
. As many "event subscribers" as we want to listen to the SNS topic notifications
. Each subscriber to the topic will get all the messages

Integration Section - Summary
SQS:
· Queue service in AWS
· Multiple Producers, messages are kept up to 14 days
· Multiple Consumers share the read and delete messages when done
· Used to decouple applications in AWS
SNS:
· Notification service in AWS
· Subscribers: Email, Lambda, SQS, HTTP, Mobile ...
· Multiple Subscribers, send all messages to all of them
· No message retention
Kinesis: real-time data streaming, persistence and analysis
Amazon MQ: managed message broker for ActiveMQ and RabbitMQ in the
cloud (MQTT, AMQP .. protocols)

