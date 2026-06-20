---
source: https://en.wikipedia.org/wiki/Token_bucket
fetched: 2026-06-19
---

Scheduling algorithm for network transmissions 

The **token bucket** is an [algorithm](./Algorithm) used in [packet-switched](./Packet-switched) and [telecommunications networks](./Telecommunications_network). It can be used to check that [data transmissions](./Data_transmission), in the form of [packets](./Network_packet), conform to defined limits on [bandwidth](./Bandwidth_(computing)) and [burstiness](./Burst_transmission) (a measure of the unevenness or variations in the [traffic](./Network_traffic_measurement) flow). It can also be used as a [scheduling algorithm](./Scheduling_algorithm) to determine the timing of transmissions that will comply with the limits set for the bandwidth and burstiness: see [network scheduler](./Network_scheduler).

 

## Overview

 

The token bucket algorithm is based on an [analogy](./Analogy) of a fixed capacity [bucket](./Bucket) into which [tokens](./Type–token_distinction), normally representing a unit of bytes or a single [packet](./Network_packet) of predetermined size, are added at a fixed rate. When a packet is to be checked for conformance to the defined limits, the bucket is inspected to see if it contains sufficient tokens at that time. If so, the appropriate number of tokens, e.g. equivalent to the length of the packet in bytes, are removed ("cashed in"), and the packet is passed, e.g., for transmission. The packet does not conform if there are insufficient tokens in the bucket, and the contents of the bucket are not changed. Non-conformant packets can be treated in various ways:

 
- They may be dropped.
- They may be enqueued for subsequent transmission when sufficient tokens have accumulated in the bucket.
- They may be transmitted, but marked as being non-conformant, possibly to be dropped subsequently if the network is overloaded.

 

A conforming flow can thus contain traffic with an average rate up to the rate at which tokens are added to the bucket, and have a burstiness determined by the depth of the bucket. This burstiness may be expressed in terms of either a [jitter](./Jitter) tolerance, i.e. how much sooner a packet might conform (e.g. arrive or be transmitted) than would be expected from the limit on the average rate, or a burst tolerance or maximum burst size, i.e. how much more than the average level of traffic might conform in some finite period.

 

## Algorithm

 

The token bucket algorithm can be conceptually understood as follows:

 
- A token is added to the bucket every     1  /  r   {\displaystyle 1/r}  ![{\displaystyle 1/r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2ab96580d23ec5eff6bb0e666531eccb7a8035d6) seconds.
- The bucket can hold at the most     b   {\displaystyle b}  ![{\displaystyle b}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f11423fbb2e967f986e36804a8ae4271734917c3) tokens. If a token arrives when the bucket is full, it is discarded.
- When a packet (network layer [PDU](./Protocol_data_unit)) of *n* bytes arrives,

- if at least *n* tokens are in the bucket, *n* tokens are removed from the bucket, and the packet is sent to the network.
- if fewer than *n* tokens are available, no tokens are removed from the bucket, and the packet is considered to be *non-conformant*.

 

### Variations

 

Implementers of this algorithm on platforms lacking the clock resolution necessary to add a single token to the bucket every     1  /  r   {\displaystyle 1/r}  ![{\displaystyle 1/r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2ab96580d23ec5eff6bb0e666531eccb7a8035d6) seconds may want to consider an alternative formulation.  Given the ability to update the token bucket every S milliseconds, the number of tokens to add every S milliseconds =     ( r ∗ ∗  S )  /  1000   {\displaystyle (r*S)/1000}  ![{\displaystyle (r*S)/1000}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8346b25098bc785ea08018e719e9073e308d1bed).

 

### Properties

 

#### Average rate

 

Over the long run the output of conformant packets is limited by the token rate,     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538).

 

#### Burst size

 

Let     M   {\displaystyle M}  ![{\displaystyle M}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f82cade9898ced02fdd08712e5f0c0151758a0dd) be the maximum possible transmission rate in bytes/second.

 

Then      T  max   =   {    b  /  ( M − −  r )     if   r < M     ∞ ∞      otherwise           {\displaystyle T_{\text{max}}={\begin{cases}b/(M-r)&{\text{ if }}r<M\\\infty &{\text{ otherwise }}\end{cases}}}  ![{\displaystyle T_{\text{max}}={\begin{cases}b/(M-r)&{\text{ if }}r<M\\\infty &{\text{ otherwise }}\end{cases}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e7fce5b7de61b4f43e6c6df9654acfaf1a81c425) is the maximum burst time, that is the time for which the rate     M   {\displaystyle M}  ![{\displaystyle M}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f82cade9898ced02fdd08712e5f0c0151758a0dd) is fully utilized.

 

The maximum burst size is thus      B  max   =  T  max   ∗ ∗  M   {\displaystyle B_{\text{max}}=T_{\text{max}}*M}  ![{\displaystyle B_{\text{max}}=T_{\text{max}}*M}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0e9c6b65e67d65dc2da82aa5c6dad401ea9c0a20)

 

### Uses

 

The token bucket can be used in either [traffic shaping](./Traffic_shaping) or [traffic policing](./Traffic_policing_(communications)). In traffic policing, nonconforming packets may be discarded (dropped) or may be reduced in priority (for downstream traffic management functions to drop if there is congestion). In traffic shaping, packets are delayed until they conform. Traffic policing and traffic shaping are commonly used to protect the network against excess or excessively bursty traffic, see [bandwidth management](./Bandwidth_management) and [congestion avoidance](./Congestion_avoidance). Traffic shaping is commonly used in the [network interfaces](./Network_interface_controller) in [hosts](./Host_(network)) to prevent transmissions being discarded by traffic management functions in the network.

 

The token bucket algorithm is also used in controlling database IO flow.[[1]](./Token_bucket#cite_note-Scylla_IO_sched-1) In it, limitation applies to neither [IOPS](./IOPS) nor the bandwidth but rather to a [linear combination](./Linear_combination) of both. By defining tokens to be the normalized sum of IO request weight and its length, the algorithm makes sure that the [time derivative](./Time_derivative) of the aforementioned function stays below the needed threshold.

 

## Comparison to leaky bucket

 

The token bucket algorithm is directly comparable to one of the two versions of the [leaky bucket](./Leaky_bucket) algorithm described in the literature.[[2]](./Token_bucket#cite_note-Turner-2)[[3]](./Token_bucket#cite_note-Tanenbaum-lbaq-3)[[4]](./Token_bucket#cite_note-ATMF-GCRA-4)[[5]](./Token_bucket#cite_note-ITU-T-GCRA-5) This comparable version of the leaky bucket is described on the relevant Wikipedia page as the [leaky bucket algorithm as a meter](./Leaky_bucket#As_a_meter). This is a mirror image of the token bucket, in that conforming packets add fluid, equivalent to the tokens removed by a conforming packet in the token bucket algorithm, to a finite capacity bucket, from which this fluid then drains away at a constant rate, equivalent to the process in which tokens are added at a fixed rate.

 

There is, however, another version of the leaky bucket algorithm,[[3]](./Token_bucket#cite_note-Tanenbaum-lbaq-3) described on the relevant Wikipedia page as the [leaky bucket algorithm as a queue](./Leaky_bucket#As_a_queue). This is a special case of the leaky bucket as a meter, which can be described by the conforming packets passing through the bucket. The leaky bucket as a queue is therefore applicable only to traffic shaping, and does not, in general, allow the output packet stream to be bursty, i.e., it is jitter free. It is therefore significantly different from the token bucket algorithm.

 

These two versions of the leaky bucket algorithm have both been described in the literature under the same name. This has led to considerable confusion over the properties of that algorithm and its comparison with the token bucket algorithm. However, fundamentally, the two algorithms are the same, and will, if implemented correctly and given the same parameters, see exactly the same packets as conforming and nonconforming.

 

## Hierarchical token bucket

 

The hierarchical token bucket (HTB) is a faster replacement for the [class-based queueing](./Class-based_queueing) (CBQ) [queuing discipline](./Queuing_discipline) in [Linux](./Linux).[[6]](./Token_bucket#cite_note-Linux_HTB-6) It is useful for limiting each client's [download](./Download)/[upload](./Upload) rate so that the limited client cannot saturate the total bandwidth.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/8/88/Link-bandwidth.jpg/250px-Link-bandwidth.jpg)](./File:Link-bandwidth.jpg)Three clients sharing the same outbound bandwidth. 

 

Conceptually, HTB is an arbitrary number of token buckets arranged in a hierarchy. The primary egress queuing discipline (*qdisc*) on any device is known as the root qdisc. The root qdisc will contain one class. This single HTB class will be set with two parameters, a *rate* and a *ceil*. These values should be the same for the top-level class and will represent the total available bandwidth on the link.

 

In HTB, *rate* means the guaranteed bandwidth available for a given class and *ceil* (short for ceiling) indicates the maximum bandwidth that class is allowed to consume. When a class requests a bandwidth more than guaranteed, it may borrow bandwidth from its parent as long as both ceils are not reached. Hierarchical Token Bucket implements a classful queuing mechanism for the Linux traffic control system, and provides rate and ceil to allow the user to control the absolute bandwidth to particular classes of traffic as well as indicate the ratio of distribution of bandwidth when extra bandwidth becomes available (up to ceil).

 

When choosing the bandwidth for a top-level class, traffic shaping only helps at the bottleneck between the LAN and the Internet.  Typically, this is the case in home and office network environments, where an entire LAN is serviced by a DSL or [T1](./T-carrier#Transmission_System_1) connection.

 

## See also

 
- [Rate limiting](./Rate_limiting)
- [Traffic shaping](./Traffic_shaping)
- [Counting semaphores](./Semaphore_(programming))

 

## References

  
1. [↑](./Token_bucket#cite_ref-Scylla_IO_sched_1-0) ["Implementing a New IO Scheduler Algorithm for Mixed Read/Write Workloads"](https://www.scylladb.com/2022/08/03/implementing-a-new-io-scheduler-algorithm-for-mixed-read-write-workloads/). 3 August 2022. Retrieved 2022-08-04. 
2. [↑](./Token_bucket#cite_ref-Turner_2-0) Turner, J., *New directions in communications (or which way to the information age?)*. IEEE Communications Magazine 24 (10): 8–15. [ISSN](./ISSN_(identifier)) [0163-6804](https://search.worldcat.org/issn/0163-6804), 1986.
3. [1](./Token_bucket#cite_ref-Tanenbaum-lbaq_3-0) [2](./Token_bucket#cite_ref-Tanenbaum-lbaq_3-1) Andrew S. Tanenbaum, *Computer Networks, Fourth Edition*, [ISBN](./ISBN_(identifier)) [0-13-166836-6](./Special:BookSources/0-13-166836-6), Prentice Hall PTR, 2003., page 401.
4. [↑](./Token_bucket#cite_ref-ATMF-GCRA_4-0) ATM Forum, The User Network Interface (UNI), v. 3.1, [ISBN](./ISBN_(identifier)) [0-13-393828-X](./Special:BookSources/0-13-393828-X), Prentice Hall PTR, 1995.
5. [↑](./Token_bucket#cite_ref-ITU-T-GCRA_5-0) ITU-T, *Traffic control and congestion control in B ISDN*, Recommendation I.371, International Telecommunication Union, 2004, Annex A, page 87.
6. [↑](./Token_bucket#cite_ref-Linux_HTB_6-0) ["Linux HTB Home Page"](http://luxik.cdi.cz/~devik/qos/htb/). Retrieved 2013-11-30.

 

## Further reading

 
- John Evans, Clarence Filsfils (2007). *Deploying IP and MPLS QoS for Multiservice Networks: Theory and Practice*. Morgan Kaufmann. [ISBN](./ISBN_(identifier)) [978-0-12-370549-5](./Special:BookSources/978-0-12-370549-5).
- Ferguson P., Huston G. (1998). *Quality of Service: Delivering QoS on the Internet and in Corporate Networks*. John Wiley & Sons, Inc. [ISBN](./ISBN_(identifier)) [0-471-24358-2](./Special:BookSources/0-471-24358-2).