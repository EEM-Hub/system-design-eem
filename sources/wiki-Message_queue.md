---
source: https://en.wikipedia.org/wiki/Message_queue
fetched: 2026-06-19
---

Means of interprocess communication in software engineering 
|  | This articleneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sources. Unsourced material may be challenged and removed.Find sources:"Message queue"–news·newspapers·books·scholar·JSTOR(May 2009)(Learn how and when to remove this message) |
| --- | --- |

 

In [computer science](./Computer_science), **message queues** and **mailboxes** are [software-engineering](./Software_engineering) [components](./Software_componentry) typically used for [inter-process communication](./Inter-process_communication) (IPC), or for inter-[thread](./Thread_(computing)) communication within the same process. They use a [queue](./Queue_(data_structure)) for [messaging](./Message_(computer_science)) – the passing of control or of content.  [Group communication systems](./Group_communication_system) provide similar kinds of functionality.

 

The message queue paradigm is a sibling of the [publisher/subscriber](./Publish–subscribe_pattern) pattern, and is typically one part of a larger [message-oriented middleware](./Message-oriented_middleware) system. Most messaging systems support both the publisher/subscriber and message queue models in their [API](./Application_programming_interface), e.g. [Java Message Service](./Java_Message_Service) (JMS).

 

Competing Consumers pattern enables multiple concurrent consumers to process messages on the same message queue. [[1]](./Message_queue#cite_note-1)

 

## Remit and ownership

 

Message queues implement an [asynchronous communication pattern](./Asynchronous_method_invocation)  NEED TO SYNCH THIS WITH THE SECTION BELOW. ON IT.  between two or more processes/threads whereby the sending and receiving party do not need to interact with the message queue at the same time. Messages placed onto the queue are stored until the recipient retrieves them.  Message queues have implicit or explicit limits on the size of data that may be transmitted in a single message and the number of messages that may remain outstanding on the queue.[[2]](./Message_queue#cite_note-2)

 

### Remit

 

Many implementations of message queues function internally within an [operating system](./Operating_system) or within an [application](./Application_software). Such queues exist for the purposes of that [system](./System) only.[[3]](./Message_queue#cite_note-3)[[4]](./Message_queue#cite_note-4)[[5]](./Message_queue#cite_note-5)

 

Other implementations allow the passing of messages between different computer systems, potentially connecting multiple applications and multiple operating systems.[[6]](./Message_queue#cite_note-6)  These message queuing systems typically provide [resilience](./Resilience_(network)) functionality to ensure that messages do not get "lost" in the event of a system failure.  Examples of commercial implementations of this kind of message queuing [software](./Software) (also known as [message-oriented middleware](./Message-oriented_middleware)) include [IBM MQ](./IBM_MQ) (formerly MQ Series) and Oracle Advanced Queuing (AQ).  There is a [Java](./Java_(programming_language)) standard called [Java Message Service](./Java_Message_Service), which has several [proprietary](./Proprietary_software) and [free software](./Free_software) implementations.

 

[Real-time operating systems](./Real-time_operating_system) (RTOSes) such as [VxWorks](./VxWorks) and [QNX](./QNX) encourage the use of message queuing as the primary inter-process or inter-thread communication mechanism.  This can result in integration between message passing and CPU scheduling.  Early examples of commercial RTOSes that encouraged a message-queue basis to inter-thread communication also include [VRTX](./Versatile_Real-Time_Executive) and [pSOS](./PSOS_(real-time_operating_system))+, both of which date to the early 1980s. The [Erlang programming language](./Erlang_(programming_language)) uses *processes* to provide concurrency; these processes communicate asynchronously using message queuing.

 

### Ownership

 

The message queue software can be either proprietary, open source or a mix of both. It is then run either on premise in private servers or on external cloud servers ([message queuing service](./Message_queuing_service)).

 
- Proprietary options have the longest history, and include products from the inception of message queuing, such as [IBM MQ](./IBM_MQ), and those tied to specific operating systems, such as [Microsoft Message Queuing (MSMQ)](./Microsoft_Message_Queuing). Cloud service providers also provide their proprietary solutions such as [Amazon Simple Queue Service](./Amazon_Simple_Queue_Service) (SQS), StormMQ, [Solace](./Solace_Corporation), and [IBM MQ](./IBM_MQ).
- Open source choices of messaging [middleware](./Middleware) systems includes [Apache ActiveMQ](./Apache_ActiveMQ), [Apache Kafka](./Apache_Kafka), [Apache Qpid](./Apache_Qpid), [Apache RocketMQ](./Apache_RocketMQ), [JBoss Messaging](./JBoss_Messaging), [RabbitMQ](./RabbitMQ), [Sun Open Message Queue](./Open_Message_Queue), and [Tarantool](./Tarantool).

 

Examples on hardware-based [messaging middleware](./Message_oriented_middleware) vendors are [Solace](./Solace_Corporation), [Apigee](./Apigee), and [IBM MQ](./IBM_MQ).

 

## Usage

 

In a typical message-queueing implementation, a [system administrator](./System_administrator) installs and configures message-queueing software (a [queue manager](./Queue_manager) or broker), and defines a named message queue. Or they register with a [message queuing service](./Message_queuing_service).

 

An application then registers a software routine that "listens" for messages placed onto the queue.

 

Second and subsequent applications may connect to the queue and transfer a message onto it.

 

The queue-manager software stores the messages until a receiving application connects and then calls the registered software routine.  The receiving application then processes the message in an appropriate manner.

 

There are often numerous options as to the exact semantics of message passing, including:

 
- Durability – messages may be kept in memory, written to disk, or even committed to a [DBMS](./Database) if the need for reliability indicates a more resource-intensive solution.
- Security policies – which applications should have access to these messages?
- Message purging policies – queues or messages may have a "[time to live](./Time_to_live)".
- Message filtering – some systems support filtering data so that a subscriber may only see messages matching some pre-specified criteria of interest.
- Delivery policies – do we need to guarantee that a message is delivered at least once, or no more than once?
- Routing policies – in a system with many queue servers, what servers should receive a message or a queue's messages?
- Batching policies – should messages be delivered immediately?   Or should the system wait a bit and try to deliver many messages at once?
- Queuing criteria – when should a message be considered "enqueued"?  When one queue has it?  Or when it has been forwarded to at least one remote queue?  Or to all queues?
- Receipt notification – A publisher may need to know when some or all subscribers have received a message.

 

These are all considerations that can have substantial effects on transaction semantics, system reliability, and system efficiency.

 

## Standards and protocols

 

Historically, message queuing has used proprietary, closed protocols, restricting the ability for different operating systems or programming languages to interact in a heterogeneous set of environments.

 

An early attempt to make message queuing more ubiquitous was [Sun Microsystems](./Sun_Microsystems)' [JMS](./Java_Message_Service) specification, which provided a [Java](./Java_(software_platform))-only abstraction of a client [API](./Application_programming_interface). This allowed Java developers to switch between providers of message queuing in a fashion similar to that of developers using [SQL](./SQL) databases. In practice, given the diversity of message queuing techniques and scenarios, this wasn't always as practical as it could be.

 

Three standards have emerged which are used in open source message queue implementations:

 
1. [Advanced Message Queuing Protocol](./Advanced_Message_Queuing_Protocol) (AMQP) – feature-rich message queue protocol, approved as ISO/IEC 19464 since April 2014
2. [Streaming Text Oriented Messaging Protocol](./Streaming_Text_Oriented_Messaging_Protocol) (STOMP) – simple, text-oriented message protocol
3. [MQTT](./MQTT) (formerly MQ Telemetry Transport) – lightweight message queue protocol especially for embedded devices

 

These protocols are at different stages of standardization and adoption. The first two operate at the same level as [HTTP](./HTTP), MQTT at the level of [TCP/IP](./TCP/IP).

 

Some proprietary implementations also use HTTP to provide message queuing by some implementations, such as [Amazon](./Amazon.com)'s [SQS](./Amazon_Simple_Queue_Service). This is because it is always possible to layer asynchronous behaviour (which is what is required for message queuing) over a synchronous protocol using request-response semantics. However, such implementations are constrained by the underlying protocol in this case and may not be able to offer the full fidelity or set of options required in message passing above.

 

## Synchronous vs. asynchronous

  WEIRD SECTION, SHOULD THIS NOT BE PUT INTO THE ASYNCHRONOUS ARTICLE

SECTION SHOULD BE DELETED. DOES NOT ADD FACTS  

Many of the more widely known [communications protocols](./Communications_protocol) in use operate [synchronously](./Synchronization_(computer_science)).  The HTTP protocol – used in the [World Wide Web](./World_Wide_Web) and in [web services](./Web_service) – offers an obvious example where a user sends a request for a web page and then waits for a reply.

 

However, scenarios exist in which synchronous behaviour is not appropriate.  For example, [AJAX](./AJAX) ([Asynchronous](https://en.wiktionary.org/wiki/asynchronous) [JavaScript](./JavaScript) and [XML](./XML)) can be used to asynchronously send text, JSON or XML messages to update part of a web page with more relevant information.  [Google](./Google) uses this approach for their Google Suggest, a search feature which sends the user's partially typed queries to Google's servers and returns a list of possible full queries the user might be interested in the process of typing. This list is asynchronously updated as the user types.

 

Other asynchronous examples exist in event notification systems and [publish/subscribe](./Publish–subscribe_pattern) systems.

 
- An application may need to notify another that an event has occurred, but does not need to wait for a response.
- In publish/subscribe systems, an application "publishes" information for any number of clients to read.

 

In both of the above examples it would not make sense for the sender of the information to have to wait if, for example, one of the recipients had crashed.

 

Applications need not be exclusively synchronous or asynchronous. An interactive application may need to respond to certain parts of a request immediately (such as telling a customer that a sales request has been accepted, and handling the promise to draw on inventory), but may queue other parts (such as completing calculation of billing, forwarding data to the central accounting system, and calling on all sorts of other services) to be done some time later.

 

In all these sorts of situations, having a subsystem which performs message-queuing (or alternatively, a broadcast messaging system) can help improve the behavior of the overall system.

 

## Implementation in UNIX

 

There are two common message queue implementations in [UNIX](./Unix). One is part of the SYS V API, the other one is part of [POSIX](./POSIX).

 

### SYS V

 

UNIX SYS V implements message passing by keeping an array of linked lists as message queues. Each message queue is identified by its index in the array, and has a unique descriptor. A given index can have multiple possible descriptors. UNIX gives standard functions to access the message passing feature.[[7]](./Message_queue#cite_note-The_Design_of_the_UNIX_Operating_System-7)

 `msgget()`This system call takes a key as an argument and returns a descriptor of the queue with the matching key if it exists. If it does not exist, and the `IPC_CREAT` flag is set, it makes a new message queue with the given key and returns its descriptor. `msgrcv()`Used to receive a message from a given queue descriptor. The caller process must have read permissions for the queue. It is of two types.[[8]](./Message_queue#cite_note-Operating_Systems_Concepts-8) 
- Blocking receive puts the child to sleep if it cannot find a requested message type. It sleeps until another message is posted in the queue, and then wakes up to check again.
- Non-blocking receive returns immediately to the caller, mentioning that it failed.

 `msgctl()`Used to change message queue parameters like the owner. Most importantly, it is used to delete the message queue by passing the `IPC_RMID` flag. A message queue can be deleted only by its creator, owner, or the superuser. 

### POSIX

 

The POSIX.1-2001 message queue API is the later of the two UNIX message queue APIs. It is distinct from the SYS V API, but provides similar function. The unix man page `mq_overview(7)` provides an overview of POSIX message queues.

 

## Graphical user interfaces

 

[Graphical user interfaces](./Graphical_user_interface) (GUIs) employ a message queue, also called an *event queue* or *input queue*, to pass [graphical input actions](./Event_(computing)), such as [mouse clicks](./Mouse_click), keyboard events, or other user inputs, to the [application program](./Application_program).[[9]](./Message_queue#cite_note-9) The windowing system places messages indicating user or other events, such as timer ticks or messages sent by other threads, into the message queue. The GUI application removes these events one at a time by calling a routine called `getNextEvent()` or similar in an [event loop](./Event_loop), and then calling the appropriate application routine to process that event.[[10]](./Message_queue#cite_note-10)

 

## See also

  
- [Advanced Message Queuing Protocol](./Advanced_Message_Queuing_Protocol) (AMQP)
- [Amazon Simple Queue Service](./Amazon_Simple_Queue_Service)
- [Apache ActiveMQ](./Apache_ActiveMQ)
- [Apache Qpid](./Apache_Qpid)
- [Celery (software)](./Celery_(software))
- [Gearman](./Gearman)
- [IBM Integration Bus](./IBM_Integration_Bus)
- [IBM MQ](./IBM_MQ)
- [Java Message Service](./Java_Message_Service)
- [MQTT](./MQTT)
- [Message-oriented middleware](./Message-oriented_middleware), [(category)](./Category:Message-oriented_middleware)
- [Microsoft Message Queuing](./Microsoft_Message_Queuing) (known colloquially as MSMQ)
- [NATS](./NATS_Messaging)
- [Oracle Messaging Cloud Service](./Oracle_Cloud)
- [RabbitMQ](./RabbitMQ)
- [Redis](./Redis)
- [TIBCO](./TIBCO) Enterprise Message Service
- [ZeroMQ](./ZeroMQ)

  

## References

  
1. [↑](./Message_queue#cite_ref-1) Gorton, Ian (2022). *Foundations of Scalable Systems*. O'Reilly Media. [ISBN](./ISBN_(identifier)) [9781098106034](./Special:BookSources/9781098106034).
2. [↑](./Message_queue#cite_ref-2) Dive Into Queue Module In Python. [Overview of POSIX message queues](http://linux.die.net/man/7/mq_overview) 
3. [↑](./Message_queue#cite_ref-3) Win32 system message queues. ["About Messages and Message Queues"](https://web.archive.org/web/20120317065349/http://msdn.microsoft.com/en-us/library/ms644927(VS.85).aspx). *Windows User Interface*. Microsoft Developer Network. Archived from [the original](http://msdn.microsoft.com/en-us/library/ms644927(VS.85).aspx) on March 17, 2012. Retrieved April 21, 2010.
4. [↑](./Message_queue#cite_ref-4) Linux and POSIX message queues. [Overview of POSIX message queues](http://linux.die.net/man/7/mq_overview) [Archived](https://web.archive.org/web/20120504002336/http://linux.die.net/man/7/mq_overview) 2012-05-04 at the [Wayback Machine](./Wayback_Machine) at linux.die.net
5. [↑](./Message_queue#cite_ref-5) Using Linux Message Queues. [Linux message queue functions](http://www.civilized.com/files/msgfuncs.txt) [Archived](https://web.archive.org/web/20120408091327/http://www.civilized.com/files/msgfuncs.txt) 2012-04-08 at the [Wayback Machine](./Wayback_Machine) at www.civilized.com
6. [↑](./Message_queue#cite_ref-6) For example, the MSMQ product. ["Message Queuing (MSMQ)"](https://msdn.microsoft.com/en-us/library/ms711472.aspx). *Network Communication*. Microsoft Developer Network. Retrieved May 9, 2009.
7. [↑](./Message_queue#cite_ref-The_Design_of_the_UNIX_Operating_System_7-0)  Bach, M.J. (1986). [*The Design of the UNIX Operating System*](https://archive.org/details/designofunixoper00bach). Prentice-Hall. [ISBN](./ISBN_(identifier)) [9780132017992](./Special:BookSources/9780132017992). 
8. [↑](./Message_queue#cite_ref-Operating_Systems_Concepts_8-0)  Abraham Silberschatz, Peter B. Galvin (1994). *Operating Systems Concepts*. Addison-Wesley. [ISBN](./ISBN_(identifier)) [9780201504804](./Special:BookSources/9780201504804). 
9. [↑](./Message_queue#cite_ref-9) Cartwright, Corky. ["GUI Programming"](https://www.cs.rice.edu/~cork/newBook/node89.html). *Rice University:Robert (Corky) Cartwright*. Retrieved June 27, 2020.
10. [↑](./Message_queue#cite_ref-10) Nystrom, Robert (2014). [*Game Programming Patterns*](https://gameprogrammingpatterns.com/event-queue.html). Genever Benning. [ISBN](./ISBN_(identifier)) [978-0990582908](./Special:BookSources/978-0990582908). Retrieved June 27, 2020.

 
| vteInter-process communication |
| --- |
| Dataexchange amongthreadsincomputer programs |
| Methods | FileMemory-mapped fileMessage passingMessage queue and mailboxNamed pipeAnonymous pipePipeSemaphoreShared memorySignalSocketsNetworkUnix |
| Protocolsandstandards | Apple eventsCOM+CORBAD-BusDDSDCEICEOpenBinderSun RPCPOSIX(various methods)SOAPRESTThriftTIPCXML-RPC |
| Software librariesandframeworks | D-BuslibeventSIMPLLINX |