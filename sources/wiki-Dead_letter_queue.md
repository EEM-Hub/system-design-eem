---
source: https://en.wikipedia.org/wiki/Dead_letter_queue
fetched: 2026-06-19
---

Term used in message queueing 

In [message queueing](./Message_queue) a **dead letter queue** (DLQ), or **dead letter topic** (DLT) in some messaging systems,  is a service implementation to store messages that the messaging system cannot or should not deliver.[[1]](./Dead_letter_queue#cite_note-1) Although implementation-specific, messages can be routed to the DLQ for the following reasons:

 
1. The message is sent to a queue that does not exist.[[2]](./Dead_letter_queue#cite_note-redkar-2)[[3]](./Dead_letter_queue#cite_note-3)
2. The maximum queue length is exceeded.
3. The message exceeds the size limit.
4. The message expires because it reached the [TTL (time to live)](./Time_to_live)[[4]](./Dead_letter_queue#cite_note-4)
5. The message is rejected by another queue exchange.[[5]](./Dead_letter_queue#cite_note-rabbitmq-5)
6. The message has been read and rejected too many times.[[6]](./Dead_letter_queue#cite_note-6)

 

Routing these messages to a dead letter queue enables analysis of common fault patterns and potential software problems.[[7]](./Dead_letter_queue#cite_note-amazon-7) If a message consumer receives a message that it considers invalid, it can instead forward it an Invalid Message Channel,[[8]](./Dead_letter_queue#cite_note-8) allowing a separation between application-level faults and delivery failures. 

 

Management of dead letter queues typically involves monitoring and alert systems. Organizations may implement specialized handlers for automated remediation or manual processing of DLQ messages.

 

Queueing systems that incorporate dead letter queues include [Amazon EventBridge](./Amazon_EventBridge?action=edit&redlink=1),[[9]](./Dead_letter_queue#cite_note-amazoneb-9) [Amazon Simple Queue Service](./Amazon_Simple_Queue_Service),[[7]](./Dead_letter_queue#cite_note-amazon-7) [Apache ActiveMQ](./Apache_ActiveMQ), [Google Cloud Pub/Sub](./Google_Cloud_Platform),[[10]](./Dead_letter_queue#cite_note-10) [HornetQ](./HornetQ), [Microsoft Message Queuing](./Microsoft_Message_Queuing),[[2]](./Dead_letter_queue#cite_note-redkar-2) Microsoft Azure Event Grid and Azure Service Bus,[[11]](./Dead_letter_queue#cite_note-11) [WebSphere MQ](./WebSphere_MQ),[[12]](./Dead_letter_queue#cite_note-12) [Solace Platform](./Solace_Corporation),[[13]](./Dead_letter_queue#cite_note-13) [Rabbit MQ](./Rabbit_MQ),[[5]](./Dead_letter_queue#cite_note-rabbitmq-5) Confluent Cloud[[14]](./Dead_letter_queue#cite_note-confluent_cloud-14) and [Apache Pulsar](./Apache_Pulsar?action=edit&redlink=1).[[15]](./Dead_letter_queue#cite_note-pulsardoc-15)[[16]](./Dead_letter_queue#cite_note-pulsarpip22-16)

 

## See also

 
- [Poison message](./Poison_message)
- [Dead letter mail](./Dead_letter_mail)

 

## References

  
1. [↑](./Dead_letter_queue#cite_ref-1) ["Dead Letter Channel"](https://www.enterpriseintegrationpatterns.com/patterns/messaging/DeadLetterChannel.html). *www.enterpriseintegrationpatterns.com*.
2. [1](./Dead_letter_queue#cite_ref-redkar_2-0) [2](./Dead_letter_queue#cite_ref-redkar_2-1) Redkar, Arohi (2004). *Pro MSMQ: Microsoft Message Queue Programming*. Apress. p. 148. [ISBN](./ISBN_(identifier)) [1430207329](./Special:BookSources/1430207329).
3. [↑](./Dead_letter_queue#cite_ref-3) ["Dead-letter queues"](http://pic.dhe.ibm.com/infocenter/wmqv7/v7r1/index.jsp?topic=%2Fcom.ibm.mq.doc%2Fic10420_.htm). IBM. Retrieved 23 February 2014.
4. [↑](./Dead_letter_queue#cite_ref-4) ["Dead Letter Exchanges — RabbitMQ"](https://www.rabbitmq.com/dlx.html). *www.rabbitmq.com*. Retrieved 2020-12-06.
5. [1](./Dead_letter_queue#cite_ref-rabbitmq_5-0) [2](./Dead_letter_queue#cite_ref-rabbitmq_5-1) RabbitMQ dead letter queue ["Dead Letter Exchanges"](https://www.rabbitmq.com/dlx.html). [Archived](https://web.archive.org/web/20160505104043/http://www.rabbitmq.com/dlx.html) from the original on 2016-05-05. Retrieved 2016-05-06.
6. [↑](./Dead_letter_queue#cite_ref-6) ["Amazon SQS dead-letter queues"](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-dead-letter-queues.html). AWS. [Archived](https://web.archive.org/web/20230414162538/https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-dead-letter-queues.html) from the original on 2023-04-14. Retrieved 2023-04-14.
7. [1](./Dead_letter_queue#cite_ref-amazon_7-0) [2](./Dead_letter_queue#cite_ref-amazon_7-1) ["Using Amazon SQS Dead Letter Queues"](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/SQSDeadLetterQueue.html). Amazon. Retrieved 23 February 2014.
8. [↑](./Dead_letter_queue#cite_ref-8) ["Invalid Message Channel"](https://www.enterpriseintegrationpatterns.com/patterns/messaging/InvalidMessageChannel.html). *www.enterpriseintegrationpatterns.com*. [Archived](https://web.archive.org/web/20230414162539/https://www.enterpriseintegrationpatterns.com/patterns/messaging/InvalidMessageChannel.html) from the original on 2023-04-14. Retrieved 2023-04-14.
9. [↑](./Dead_letter_queue#cite_ref-amazoneb_9-0) ["Amazon EventBridge announces support for Dead Letter Queues"](https://aws.amazon.com/it/about-aws/whats-new/2020/10/amazon-eventbridge-announces-support-dead-letter-queues). Amazon. [Archived](https://web.archive.org/web/20241217225540/https://aws.amazon.com/it/about-aws/whats-new/2020/10/amazon-eventbridge-announces-support-dead-letter-queues/) from the original on 2024-12-17. Retrieved 2020-10-30.
10. [↑](./Dead_letter_queue#cite_ref-10) ["Forwarding to dead-letter topics | Cloud Pub/Sub"](https://cloud.google.com/pubsub/docs/dead-letter-topics). *Google Cloud*. Retrieved 2020-12-26.
11. [↑](./Dead_letter_queue#cite_ref-11) spelluru. ["Compare Azure messaging services"](https://docs.microsoft.com/en-us/azure/event-grid/compare-messaging-services?toc=%2fazure%2fservice-bus-messaging%2ftoc.json). *docs.microsoft.com*. Retrieved 2020-01-17.
12. [↑](./Dead_letter_queue#cite_ref-12) Böhm-Mäder, Johannes (14 December 2011). *WebSphere MQ Security: Tales of Scowling Wolves Among Unglamorous Sheep*. BoD. p. 68. [ISBN](./ISBN_(identifier)) [978-3842381506](./Special:BookSources/978-3842381506).
13. [↑](./Dead_letter_queue#cite_ref-13) ["Solace Dead Message Queues"](https://docs.solace.com/Configuring-and-Managing/Setting-Dead-Msg-Queues.htm).
14. [↑](./Dead_letter_queue#cite_ref-confluent_cloud_14-0) ["Confluent Cloud documentation"](https://docs.confluent.io/cloud/current/connectors/dead-letter-queue.html). [Archived](https://web.archive.org/web/20210304102205/https://docs.confluent.io/cloud/current/connectors/dead-letter-queue.html) from the original on 2021-03-04. Retrieved 2021-02-12.
15. [↑](./Dead_letter_queue#cite_ref-pulsardoc_15-0) ["Apache Pulsar documentation"](https://pulsar.apache.org/docs/en/concepts-messaging/#dead-letter-topic).
16. [↑](./Dead_letter_queue#cite_ref-pulsarpip22_16-0) ["Apache Pulsar PIP-22:Dead Letter Topic"](https://github.com/apache/pulsar/wiki/PIP-22:-Pulsar-Dead-Letter-Topic). *[GitHub](./GitHub)*.