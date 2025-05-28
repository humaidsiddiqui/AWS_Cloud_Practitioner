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


