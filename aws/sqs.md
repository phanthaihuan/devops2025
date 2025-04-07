### What?
Producers -----> SQS Queue -----> Consumers

Producers send messages to SQS queue.
Consumers poll messages from SQL queue.

#### Standard Queue
1. Unlimited number of messages in queue
2. Default retention of messages: 4 days, maximum of 14 days
3. Low latency: <10 ms on publish and receive
4. Limitation of 256KB/message
5. Can have duplicate messages
6. Can have out of order messages
7. A message is persisted in SQL until a consumer deletes it.
8. Consumers can poll SQS for messages (max 10 messages at a time)
#### FIFO queue
