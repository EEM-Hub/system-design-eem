---
source: https://en.wikipedia.org/wiki/Leaky_bucket
fetched: 2026-06-19
---

Network traffic shaping and policing algorithm This article is about the computer algorithm. For the metaphor in economic redistribution, see [Leaky bucket (economics)](./Leaky_bucket_(economics)). 

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/7/77/Leaky_bucket_analogy.svg/250px-Leaky_bucket_analogy.svg.png)](./File:Leaky_bucket_analogy.svg)The leaky bucket analogy. Water can be added intermittently to the bucket, which leaks out at a constant rate until empty, and will also overflow when full. 

The **leaky bucket** is an algorithm based on an [analogy](./Analogy) of how a [bucket](./Bucket) with a constant [leak](./Leak) will overflow if either the [average](./Average) rate at which water is poured in exceeds the rate at which the bucket leaks or if more water than the capacity of the bucket is poured in all at once. It can be used to determine whether some sequence of discrete events [conforms](./Conformance_testing) to defined limits on their average and peak rates or frequencies, e.g. to limit the actions associated with these events to these rates or delay them until they do conform to the rates. It may also be used to check conformance or limit to an average rate alone, i.e. remove any variation from the average. 

 

It is used in [packet-switched computer networks](./Packet-switched_computer_network) and [telecommunications networks](./Telecommunications_network) in both the [traffic policing](./Traffic_policing_(communications)), [traffic shaping](./Traffic_shaping) and [scheduling](./Network_scheduler) of [data transmissions](./Data_transmission), in the form of [packets](./Network_packet),[[a]](./Leaky_bucket#cite_note-packet-1) to defined limits on [bandwidth](./Bandwidth_(computing)) and [burstiness](./Burst_transmission) (a measure of the variations in the [traffic](./Network_traffic_measurement) flow).

 

A version of the leaky bucket, the [generic cell rate algorithm](./Generic_cell_rate_algorithm), is recommended for [Asynchronous Transfer Mode](./Asynchronous_Transfer_Mode) (ATM) networks[[1]](./Leaky_bucket#cite_note-UPC_NPC-2) in [UPC and NPC](./UPC_and_NPC) at [user–network interfaces](./User–network_interface) or inter-network interfaces or [network-to-network interfaces](./Network-to-network_interface) to protect a network from excessive traffic levels on connections routed through it. The generic cell rate algorithm, or an equivalent, may also be used to shape transmissions by a [network interface card](./Network_interface_card) onto an ATM network.

 

At least some implementations of the leaky bucket are a mirror image of the [token bucket](./Token_bucket) algorithm and will, given equivalent parameters, determine exactly the same sequence of events to conform or not conform to the same limits.

 

## Overview

 

Two different methods of applying this leaky bucket analogy are described in the literature.[[2]](./Leaky_bucket#cite_note-Turner-3)[[3]](./Leaky_bucket#cite_note-Tanenbaum-lbaq-4)[[4]](./Leaky_bucket#cite_note-ATMF-GCRA-5)[[5]](./Leaky_bucket#cite_note-ITU-T-GCRA-6) These give what appear to be two different algorithms, both of which are referred to as the leaky bucket algorithm and generally without reference to the other method. This has resulted in confusion about what the leaky bucket algorithm is and what its properties are.

 

In one version, the bucket is a counter or variable separate from the flow of traffic or schedule of events.[[2]](./Leaky_bucket#cite_note-Turner-3)[[4]](./Leaky_bucket#cite_note-ATMF-GCRA-5)[[5]](./Leaky_bucket#cite_note-ITU-T-GCRA-6) This counter is used only to check that the traffic or events conform to the limits: The counter is incremented as each packet arrives at the point where the check is being made or an event occurs, which is equivalent to the way water is added intermittently to the bucket. The counter is also decremented at a fixed rate, equivalent to the way the water leaks out of the bucket. As a result, the value in the counter represents the level of the water in the bucket. If the counter remains below a specified limit value when a packet arrives or an event occurs, i.e., the bucket does not overflow, that indicates its conformance to the bandwidth and burstiness limits or the average and peak rate event limits. This version is referred to here as * the leaky bucket as a meter*.

 

In the second version, the bucket is a queue in the flow of traffic.[[3]](./Leaky_bucket#cite_note-Tanenbaum-lbaq-4) This queue is used to directly control that flow: Packets are entered into the queue as they arrive, equivalent to the water being added to the bucket. These packets are then removed from the queue ([first come, first served](./FIFO_(computing_and_electronics))), usually at a fixed rate, e.g., for onward transmission, equivalent to water leaking from the bucket. This configuration imposes conformance rather than checking it, and where the output is serviced at a fixed rate (and where the packets are all the same length), the resulting traffic stream is necessarily devoid of burstiness or [jitter](./Jitter). So in this version, the traffic itself is the analogue of the water passing through the bucket. This version is referred to here as *leaky bucket as a queue*.

 

The leaky bucket as a meter is exactly equivalent to (a mirror image of) the [token bucket](./Token_bucket) algorithm, i.e. the process of adding water to the leaky bucket exactly mirrors that of removing tokens from the token bucket when a conforming packet arrives, the process of leaking of water from the leaky bucket exactly mirrors that of regularly adding tokens to the token bucket, and the test that the leaky bucket will not overflow is a mirror of the test that the token bucket contains enough tokens and will not *underflow*. Thus, given equivalent parameters, the two algorithms will see the same traffic as conforming or nonconforming. The leaky bucket as a queue can be seen as a special case of the leaky bucket as a meter.[[6]](./Leaky_bucket#cite_note-McDysan-Spohn-7)

 

## As a meter

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/4/4c/Leaky_bucket_as_a_meter-policing.JPG/500px-Leaky_bucket_as_a_meter-policing.JPG)](./File:Leaky_bucket_as_a_meter-policing.JPG)[Traffic policing](./Traffic_policing_(communications)) with a leaky bucket as a meter 

[Jonathan S. Turner](./Jonathan_S._Turner) is credited[[7]](./Leaky_bucket#cite_note-Tanenbaum-turner-8) with the original description of the leaky bucket algorithm and describes it as follows: "A counter associated with each user transmitting on a connection is incremented whenever the user sends a packet and is decremented periodically. If the counter exceeds a threshold upon being incremented, the network discards the packet. The user specifies the rate at which the counter is decremented (this determines the average bandwidth) and the value of the threshold (a measure of burstiness)".[[2]](./Leaky_bucket#cite_note-Turner-3) The bucket (analogous to the counter) is, in this case, used as a meter to test the conformance of packets, rather than as a queue to directly control them.

 

Another description of what is essentially the same meter version of the algorithm, the [generic cell rate algorithm](./Generic_cell_rate_algorithm), is given by the [ITU-T](./ITU-T) in recommendation I.371 and in the [ATM Forum](./ATM_Forum)'s [UNI](./User–network_interface) specification.[[4]](./Leaky_bucket#cite_note-ATMF-GCRA-5)[[5]](./Leaky_bucket#cite_note-ITU-T-GCRA-6) The description, in which the term *cell* is equivalent to *packet* in Turner's description[[2]](./Leaky_bucket#cite_note-Turner-3) is given by the ITU-T as follows: "The continuous-state leaky bucket can be viewed as a finite capacity bucket whose real-valued content drains out at a continuous rate of 1 unit of content per time unit and whose content is increased by the increment *T* for each conforming cell... If at a cell arrival the content of the bucket is less than or equal to the limit value *τ*, then the cell is conforming; otherwise, the cell is non-conforming. The capacity of the bucket (the upper bound of the counter) is (*T* + *τ*)".[[5]](./Leaky_bucket#cite_note-ITU-T-GCRA-6) These specifications also state that, due to its finite capacity, if the contents of the bucket at the time the conformance is tested is greater than the limit value, and hence the cell is non-conforming, then the bucket is left unchanged; that is, the water is simply not added if it would make the bucket overflow.

 

David E. McDysan and Darrel L. Spohn provide a commentary on the description given by the ITU-T/ATM Forum. In this, they state, "In the leaky bucket analogy, the [ATM] cells do not actually flow through the bucket; only the check for conforming admission does".[[6]](./Leaky_bucket#cite_note-McDysan-Spohn-7) However, uncommonly in the descriptions in the literature, McDysan and Spohn also refer to the leaky bucket algorithm as a queue, going on, "Note that one implementation of traffic shaping is to actually have the cells flow through the bucket".[[6]](./Leaky_bucket#cite_note-McDysan-Spohn-7)

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/7/76/Leaky_bucket_as_a_meter-shaping.JPG/500px-Leaky_bucket_as_a_meter-shaping.JPG)](./File:Leaky_bucket_as_a_meter-shaping.JPG)[Traffic shaping](./Traffic_shaping) with a leaky bucket as a meter 

In describing the operation of the ITU-T's version of the algorithm, McDysan and Spohn invoke a "notion commonly employed in [queueing theory](./Queueing_theory) of a fictional *gremlin*".[[6]](./Leaky_bucket#cite_note-McDysan-Spohn-7) This gremlin inspects the level in the bucket and takes action if the level is above the limit value *τ*: in *traffic policing*, it pulls open a trap door, which causes the arriving packet to be dropped and stops its water from entering the bucket; in [traffic shaping](./Traffic_shaping), it pushes up a flap, which delays the arriving packet and prevents it from delivering its water, until the water level in the bucket falls below *τ*.

 

The difference between the descriptions given by Turner and the ITU-T/ATM Forum is that Turner's is specific to traffic policing, whereas the ITU-T/ATM Forum description is applicable to both traffic policing and traffic shaping. Also, Turner does not state that the contents of the counter should only be affected by conforming packets, and should only be incremented when this would not cause it to exceed a limit, i.e. Turner does not explicitly state that the bucket's capacity or counter's maximum value is finite.[[b]](./Leaky_bucket#cite_note-defalign-9)

 

### Concept of operation

 

A description of the concept of operation of the leaky bucket algorithm as a meter that can be used in either traffic policing or traffic shaping may be described as a fixed capacity bucket, associated with each virtual connection or user. The bucket leaks at a fixed rate. If the bucket is empty, it stops leaking. For a packet to conform, it has to be possible to add a specific amount of water to the bucket. The specific amount added by a conforming packet can be the same for all packets or can be proportional to the length of the packet. If this amount of water would cause the bucket to overflow, then the packet does not conform, and the water in the bucket is left unchanged.

 

### Uses

 

The leaky bucket as a meter can be used in either traffic shaping or [traffic policing](./Traffic_policing_(communications)). For example, in ATM networks, in the form of the generic cell rate algorithm, it is used to compare the bandwidth and burstiness of traffic on a [virtual channel](./Virtual_channel) (VC) or virtual path (VP) against the specified limits on the rate at which cells may arrive and the maximum jitter, or variation in inter-arrival intervals, for the VC or VP. In traffic policing, cells that do not conform to these limits (nonconforming cells) may be dropped or may be reduced in priority for downstream traffic management functions to drop if there is congestion. In traffic shaping, cells are delayed until they conform. Traffic policing and traffic shaping are commonly used in UPC and NPC to protect the network against excess or excessively bursty traffic. (See [bandwidth management](./Bandwidth_management) and [congestion avoidance](./Congestion_avoidance).) Traffic shaping is commonly used in the network interfaces in [hosts](./Host_(network)) to prevent transmissions from exceeding the bandwidth or jitter limits and being discarded by traffic management functions in the network. (See [scheduling (computing)](./Scheduling_(computing)) and [network scheduler](./Network_scheduler).)

 

The leaky bucket algorithm as a meter can also be used in a leaky bucket counter to measure the rate of [random (stochastic) processes](./Stochastic_process). A Leaky bucket counter can be used to indicate, by its overflowing when the average or peak rate of events increases above some acceptable background level.[[8]](./Leaky_bucket#cite_note-lbcounter-10) For example, such a leaky bucket counter can be used to detect when there is a sudden burst of correctable memory errors or when there has been a gradual, but significant, increase in the average rate, which may indicate an impending correction failure.[[9]](./Leaky_bucket#cite_note-intelseverboard-11)

 

The use of the leaky bucket algorithm in a leaky bucket counter is similar to that in traffic management, in that it is used as a meter. Essentially, the events replace the packets in the description, with each event causing a quantity of water to be added to the bucket. If the bucket would overflow, as a result of the event, then the event should trigger the action associated with an out-of-limits event. Some implementations[[8]](./Leaky_bucket#cite_note-lbcounter-10) seem to parallel Turner's description,[[2]](./Leaky_bucket#cite_note-Turner-3) in that there is no explicit limit on the maximum value that the counter may take, implying that once the counter has exceeded the threshold, it may not return to its previous state until a period significantly greater than the equivalent of the emission interval has passed, which may be increased by what would otherwise be conforming events. However, other implementations may not increment the counter while it is overflowed, allowing it to correctly determine whether the following events conform or not.

 

### Parameters

 

In the case of the leaky bucket algorithm as a meter, the limits on the traffic can be bandwidth and the burstiness of the output.[[4]](./Leaky_bucket#cite_note-ATMF-GCRA-5)[[5]](./Leaky_bucket#cite_note-ITU-T-GCRA-6)[[c]](./Leaky_bucket#cite_note-shapelimit-12) The bandwidth limit and burstiness limit for the connection may be specified in a [traffic contract](./Traffic_contract). A bandwidth limit may be specified as a packet rate, a [bit rate](./Bit_rate), or as an [emission interval](./Leaky_bucket#Emission_interval) between the packets. A limit on burstiness may be specified as a [delay variation](./Leaky_bucket#Delay_variation_tolerance) tolerance, or as a [maximum burst size](./Leaky_bucket#Maximum_burst_size) (MBS).

 

Multiple sets of contract parameters can be applied concurrently to a connection using multiple instances of the leaky bucket algorithm, each of which may take a bandwidth and a burstiness limit: see [Generic cell rate algorithm § Dual Leaky Bucket Controller](./Generic_cell_rate_algorithm#Dual_Leaky_Bucket_Controller).

 

#### Emission interval

 

The rate at which the bucket leaks will determine the bandwidth limit, which is referred to as the average rate by Turner[[2]](./Leaky_bucket#cite_note-Turner-3) and the inverse of which is referred to as the emission interval by the ITU-T. It is easiest to explain what this interval is where packets have a fixed length. Hence, the first part of this description assumes this, and the implications of variable packet lengths are considered separately.

 

Consider a bucket that is exactly filled to the top by preceding traffic, i.e. when the maximum permitted burstiness has already occurred, i.e., the maximum number of packets or cells have just arrived in the minimum amount of time for them to still conform to the bandwidth and jitter limits. The minimum interval before the next packet can conform is then the time it takes for the bucket to leak exactly the amount of water delivered by a packet, and if a packet is tested and conforms at that time, this will exactly fill the bucket once more. Thus, once the bucket is filled, the maximum rate that packets can conform is with this interval between each packet.

 

Turner[[2]](./Leaky_bucket#cite_note-Turner-3) refers to this rate as the average, implying that its inverse is the average interval. There is, however, some ambiguity in what the average rate and interval are. Since packets can arrive at any lower rate, this is an upper bound, rather than a fixed value, so it could at best be called the maximum for the average rate. Also, during the time the maximum burstiness occurs, packets can arrive at smaller intervals and thus at a higher rate than this. So, for any period less than infinity, the actual average rate can be (but is not necessarily) greater than this and the average interval can be (but is not necessarily) less than the emission interval. Hence, because of this ambiguity, the term emission interval is used hereafter. However, it is still true that the minimum value that the long-term average interval can take tends to be the emission interval.

 

For variable-length packets, where the amount added to the bucket is proportional to the packet length, the maximum rate at which they can conform varies according to their length: the amount that the bucket must have leaked from full for a packet to conform is the amount the packet will add, and if this is proportional to the packet length, so is the interval between it and the preceding packet that filled the bucket. Hence, it is not possible to specify a specific emission interval for variable-length packets, and the bandwidth limit has to be specified explicitly, in bits or bytes per second.

 

#### Delay variation tolerance

 

It is easiest to explain delay variation tolerance for the case where packets have a fixed length. Hence, the first part of this description assumes this, and the implications of variable packet lengths are considered separately.

 

The ITU-T defines a limit value, *τ*, that is less than the capacity of the bucket by *T* (the amount by which the bucket contents is incremented for each conforming cell), so that the capacity of the bucket is *T* + *τ*. This limit value specifies how much earlier a packet can arrive than it would normally be expected if the packets were arriving with exactly the emission interval between them.

 

Imagine the following situation: A bucket leaks at 1 unit of water per second, so the limit value, *τ*, and the amount of water added by a packet, *T*, are effectively in units of seconds. This bucket starts off empty, so when a packet arrives at the bucket, it does not quite fill the bucket by adding its water *T*, and the bucket is now *τ* below its capacity. So when the next packet arrives, the bucket only has to have drained by *T* – *τ* for this to conform. So the interval between these two packets can be as much as *τ* less than *T*.

 

This extends to multiple packets in a sequence: Imagine the following: The bucket again starts off empty, so the first packet to arrive clearly conforms. The bucket then becomes exactly full after a number of conforming packets, *N*, have arrived in the minimum possible time for them to conform. For the last (the *N*th) packet to conform, the bucket must have leaked enough of the water from the preceding *N* – 1 packets ((*N* – 1) × *T* seconds' worth) for it to be exactly at the limit value *τ* at this time. Hence, the water leaked is (*N* – 1) × *T* – *τ*, which, because the leak is one unit per second, took exactly (*N* – 1) × *T* – *τ* seconds to leak. Thus, the shortest time in which all *N* packets can arrive and conform is (*N* – 1) × *T* – *τ* seconds, which is exactly *τ* less than the time it would have taken if the packets had been arriving at exactly the emission interval.

 

However, packets can only arrive with intervals less than *T* when the bucket is not filled by the previous packet. If it is filled, then the bucket must have drained by the full amount *T* before the next packet conforms. So once this bucket space has been used up by packets arriving at less than *T*, subsequent frames must arrive at intervals no less than *T*. They may, however, arrive at greater intervals, when the bucket will not be filled by them. Since the bucket stops leaking when it is empty, there is always a limit (*τ*) to how much tolerance can be accrued by these intervals greater than *T*.

 

Since the limit value *τ* defines how much earlier a packet can arrive than would be expected, it is the limit on the difference between the maximum and minimum delays from the source to the point where the conformance test is being made (assuming the packets are generated with no jitter). Hence, the use of the term cell delay variation tolerance (CDVt) for this parameter in ATM.

 

As an example, a possible source of delay variation is where a number of streams of packets are multiplexed together at the output of a switch. Assuming that the sum of the bandwidths of these connections is less than the capacity of the output, all of the packets that arrive can be transmitted eventually. However, if their arrivals are independent, e.g., because they arrive at different inputs of the switch, then several may arrive at or nearly at the same time. Since the output can only transmit one packet at a time, the others must be queued in a buffer until it is their turn to be transmitted. This buffer then introduces an additional delay between a packet arriving at an input and being transmitted by the output, and this delay varies, depending on how many other packets are already queued in the buffer. A similar situation can occur at the output of a host (in the [network interface controller](./Network_interface_controller)) when multiple packets have the same or similar release times, and this delay can usually be modelled as a delay in a virtual output buffer.

 

For variable-length packets, where the amount of water added by a given packet is proportional to its length, *τ* can not be seen as a limit on how full the bucket can be when a packet arrives, as this varies depending on the packet size. However, the time it takes to drain from this level to empty is still how much earlier a packet can arrive than is expected when packets are transmitted at the bandwidth limit. Thus, it is still the maximum variation in transfer delay to the point where the conformance test is being applied that can be tolerated, and thus the tolerance on maximum delay variation.

 

#### Maximum burst size

 

The limit value or delay variation tolerance also controls how many packets can arrive in a burst, determined by the excess depth of the bucket over the capacity required for a single packet. Hence, MBS is also a measure of burstiness or jitter, and it is possible to specify the burstiness as an MBS and derive the limit value *τ* from this or to specify it as a jitter or delay variation tolerance or limit value, and derive the MBS from this.

 

A burst or clump of packets can arrive at a higher rate than determined by the emission interval *T*. This may be the line rate of the [physical layer](./Physical_layer) connection when the packets in the burst will arrive back-to-back. However, as in ATM, the tolerance may be applied to a lower rate, in that case, the [Sustainable Cell Rate](./Sustainable_Cell_Rate) (SCR), and the burst of packets (cells) can arrive at a higher rate, but less than the line rate of the physical layer, in that case, the [Peak Cell Rate](./Peak_Cell_Rate?action=edit&redlink=1) (PCR). The MBS may then be the number of cells needed to transport a higher layer packet (see [Segmentation and reassembly](./Segmentation_and_reassembly)), where the packets are transmitted with a maximum bandwidth determined by the SCR and cells within the packets are transmitted at the PCR; thus allowing the last cell of the packet, and the packet itself, to arrive significantly earlier than it would if the cells were sent at the SCR: transmission duration = (MBS-1)/PCR rather than (MBS-1)/SCR. This bursting at the PCR puts a significantly higher load on shared resources, e.g., switch output buffers, than does transmission at the SCR, and is thus more likely to result in buffer overflows and network congestion. However, it puts a lesser load on these resources than would transmitting at the SCR with a limit value, *τSCR*, that allows MBS cells to be transmitted and arrive back-to-back at the line rate.

 

If the limit value is large enough, then several packets can arrive in a burst and still conform: if the bucket starts from empty, the first packet to arrive will add *T*, but if, by the time the next packet arrives, the contents is below *τ*, this will also conform. Assuming that each packet takes *δ* to arrive, then if *τ* (expressed as the time it takes the bucket to empty from the limit value) is equal to or greater than the emission interval less the minimum interarrival time, *T* – *δ*, the second packet will conform even if it arrives as a burst with the first. Similarly, if *τ* is equal to or greater than (*T* – *δ*) × 2, then 3 packets can arrive in a burst, etc.

 

The maximum size of this burst, *M*, can be calculated from the emission interval, *T*; the maximum jitter tolerance, *τ*; and the time taken to transmit/receive a packet, *δ*, as follows:[[4]](./Leaky_bucket#cite_note-ATMF-GCRA-5)

     M =  ⌊  1 +   τ τ   T − −  δ δ      ⌋    {\displaystyle M=\left\lfloor 1+{\frac {\tau }{T-\delta }}\right\rfloor }  ![{\displaystyle M=\left\lfloor 1+{\frac {\tau }{T-\delta }}\right\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/7f3a6a23fa83ba8bbf0d48018d18f706a3be0a3a) 

Equally, the minimum value of jitter tolerance *τ* that gives a specific MBS can be calculated from the MBS as follows:[[4]](./Leaky_bucket#cite_note-ATMF-GCRA-5)

     τ τ  =  (  M − −  1  )   (  T − −  δ δ   )    {\displaystyle \tau =\left(M-1\right)\left(T-\delta \right)}  ![{\displaystyle \tau =\left(M-1\right)\left(T-\delta \right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bd7919ef97201e0f0022104cf1cef69046bb0cad) 

In the case of ATM, where technically MBS only relates to the SCR tolerance, in the above equation the time it takes each packet to arrive, *δ*, is the emission interval for cells at the PCR *TPCR*, and the emission interval, *T*, is the emission interval for the SCR *TSCR*. Where MBS is to be the number of cells required to transport a segmented packet, the limit value in the above, *τ*, should be that for the SCR *τSCR*. However, at the UNI or an [NNI](./Network-to-network_interface), where cells at the PCR will have been subjected to delay variation, it should be the limit value for the SCR plus that for the PCR *τSCR* + *τPCR*.

 

For variable-length packets, the maximum burst size will depend on the lengths of the packets in the burst, and there is no single value for the maximum burst size. However, it is possible to specify the total burst length in bytes, from the byte rate of the input stream, the equivalent byte rate of the leak, and the bucket depth.

 

### Comparison with the token bucket algorithm

 

The leaky bucket algorithm is sometimes contrasted with the [token bucket](./Token_bucket) algorithm. However, the above [concept of operation](./Leaky_bucket#Concept_of_operation) for the leaky bucket as a meter may be directly compared with the token bucket algorithm, the description of which is given as follows:

 
- A token is added to the bucket every 1/*r* seconds.

 
- The bucket can hold at most *b* tokens. If a token arrives when the bucket is full, it is discarded.

 
- When a packet (network layer [PDU](./Protocol_data_unit)) [*[sic](./Sic)*][[a]](./Leaky_bucket#cite_note-packet-1) of *n* bytes arrives, *n* tokens are removed from the bucket, and the packet is sent to the network.

 
- If fewer than *n* tokens are available, no tokens are removed from the bucket, and the packet is considered to be non-conformant.

 

This can be compared with the leaky bucket, repeated from above:

 
- A fixed capacity bucket, associated with each virtual connection or user, leaks at a fixed rate.

 
- If the bucket is empty, it stops leaking.

 
- For a packet to conform, it has to be possible to add a specific amount of water to the bucket: The specific amount added by a conforming packet can be the same for all packets or can be proportional to the length of the packet.

 
- If this amount of water would cause the bucket to exceed its capacity, then the packet does not conform, and the water in the bucket is left unchanged.

 

As can be seen, these two descriptions are essentially mirror images of one another: one adds something to the bucket on a regular basis and takes something away for conforming packets down to a limit of zero; the other takes away regularly and adds for conforming packets up to a limit of the bucket's capacity. Both are effectively the same, as these are the same basic algorithm described differently.

 

## As a queue

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/e/e1/LeakyBucket.png/250px-LeakyBucket.png)](./File:LeakyBucket.png)The leaky bucket as a queue This is not the best possible drawing, as it could be interpreted as showing multiple packets arriving concurrently and being converted to parallel outputs with a common phase, rather than, as it should show, a single sequential stream of packets with variable interarrival times, which the leaky bucket queue then converts to a single sequential stream of packets with fixed intervals.  

The leaky bucket as a queue is essentially a way of describing a simple [FIFO](./FIFO_(computing_and_electronics)) buffer or queue that is serviced at a fixed rate to remove burstiness or jitter. A description of it is given by [Andrew S. Tanenbaum](./Andrew_S._Tanenbaum), in (an older version of) his book *Computer Networks* as "The leaky bucket consists of a finite queue. When a packet arrives, if there is room in the queue, it is appended to the queue; otherwise, it is discarded. At every clock tick, one packet is transmitted (unless the queue is empty)".[[3]](./Leaky_bucket#cite_note-Tanenbaum-lbaq-4) An implementation of the leaky bucket as a queue is therefore always a form of traffic shaping function.

 

As can be seen, this implementation is restricted in that the packets are only ever transmitted at a fixed rate. To underline this, Tanenbaum also states that "The leaky bucket algorithm enforces a rigid output pattern at the average rate, no matter how bursty the [input] traffic is."[[10]](./Leaky_bucket#cite_note-Tanenbaum-no_jitter_out-13) However, this assertion is only strictly true as long as the queue does not become empty: if the average arrival rate is less than the rate of clock ticks, or if the input is sufficiently bursty that the losses bring the rate of the remainder below the clock tick rate (i.e. gaps in the input stream are long enough and the queue is small enough that it can become empty), there will be gaps in the output stream.

 

The tunable parameter for this algorithm is the bandwidth of its output.[[10]](./Leaky_bucket#cite_note-Tanenbaum-no_jitter_out-13)[[c]](./Leaky_bucket#cite_note-shapelimit-12) The bandwidth limit for the connection may be specified in a [traffic contract](./Traffic_contract). A bandwidth limit may be specified as a packet or [frame rate](./Frame_rate), a byte or [bit rate](./Bit_rate), or as an [emission interval](./Leaky_bucket#Emission_Interval) between the packets.

 

Limiting variable-length packets using the leaky bucket algorithm as a queue is significantly more complicated than it is for fixed-length packets. Tanenbaum gives a description of a "byte-counting" leaky bucket for variable-length packets as follows: "At each tick, a counter is initialized to n. If the first packet on the queue has fewer bytes than the current value of the counter, it is transmitted, and the counter is decremented by that number of bytes. Additional packets may also be sent, as long as the counter is high enough. When the counter drops below the length of the next packet on the queue, transmission stops until the next tick, at which time the residual byte count is reset [to n] and the flow can continue".[[3]](./Leaky_bucket#cite_note-Tanenbaum-lbaq-4) As with the version for fixed-length packets, this implementation has a strong effect on the phase of transmissions, resulting in variable end-to-end delays, and unsuitability for real-time traffic shaping.

 

The leaky bucket as a queue can only be used in shaping traffic to a specified bandwidth with no jitter in the output.[[10]](./Leaky_bucket#cite_note-Tanenbaum-no_jitter_out-13) It may be used within the network, e.g. as part of bandwidth management, but is more appropriate to traffic shaping in the network interfaces of hosts. The leaky bucket algorithm is used in [Nginx](./Nginx)'s *ngx_http_limit_req_module* module for limiting the number of [concurrent requests](./Concurrent_user) originating from a single [IP address](./IP_address).[[11]](./Leaky_bucket#cite_note-14)

 

## Comparison between the two versions

 
|  | This sectionmay beconfusing or unclearto readers.Please helpclarify the section. There might be a discussion about this onthe talk page.(November 2025)(Learn how and when to remove this message) |
| --- | --- |

 

Analysis of the two versions of the leaky bucket algorithm shows that the version as a queue is a special case of the version as a meter.

 

Imagine a traffic shaping function for fixed-length packets that is implemented using a fixed-length queue, forming a delay element, which is serviced using a leaky bucket as a meter. Imagine also that the bucket in this meter has a depth equal to the amount added by a packet, i.e., has a limit value, *τ*, of zero. However, the conformance test is only performed at intervals of the emission interval, when the packet at the head of the queue is transmitted and its water is added. This water then leaks away during the next emission interval (or is removed just prior to performing the next conformance test), allowing the next packet to conform then or at some subsequent emission interval. The service function can also be viewed in terms of a token bucket with the same depth, where enough tokens for one packet are added (if the bucket is not full) at the emission intervals. This implementation will then receive packets with a bursty arrival pattern (limited by the queue depth) and transmit them on at intervals that are always exact (integral) multiples of the emission interval.

 

However, the implementation of the leaky bucket as a meter (or token bucket) in a traffic shaping function described above is an exact equivalent to the description of the leaky bucket as a queue:[[3]](./Leaky_bucket#cite_note-Tanenbaum-lbaq-4) the delay element of the meter version is the bucket of the queue version; the bucket of the meter version is the process that services the queue, and the leak is such that the emission interval is the same as the tick interval. Therefore, for fixed-length packets, the implementation of the leaky bucket as a queue is a special case of a traffic shaping function using a leaky bucket (or token bucket) as a meter in which the limit value, *τ*, is zero and the process of testing conformance is performed at the lowest possible rate.

 

The leaky bucket as a queue for variable packet lengths can also be described as equivalent to a special case of the leaky bucket as a meter. The suggested implementation[[3]](./Leaky_bucket#cite_note-Tanenbaum-lbaq-4) can, like the fixed-length implementation, be seen as traffic shaping function in which the queue is a delay element, rather than the bucket, and the function that services the queue is, in this case, explicitly given as a token bucket: it is decremented for conforming packets and incremented at a fixed rate. Hence, as the leaky bucket as a meter and token bucket are equivalent, the leaky bucket as a queue for variable packet lengths is also a special case of a traffic shaping function using a leaky bucket (or token bucket) as a meter.

 

There is an interesting consequence of seeing the leaky bucket as a queue for variable packet lengths as a specific implementation of the token bucket or leaky bucket as a meter in traffic shaping. This is that the bucket of the meter has a depth, *n*, and, as is always the case with the token bucket, this depth determines the burstiness of the output traffic (perhaps in relation to the average or minimum number of tokens required by the packets). Hence, it is possible to quantify the burstiness of the output of this *byte counting* leaky bucket as a meter, unless all packets are of the maximum length, when it becomes pointless. However, this ability to define a burstiness for the output is in direct contradiction to the statement that the leaky bucket (as a queue) necessarily gives an output with a rigid rate, no matter how bursty the input.

 

## See also

 
- [Fluid queue](./Fluid_queue)
- [Generic cell rate algorithm](./Generic_cell_rate_algorithm)
- [Traffic contract](./Traffic_contract)
- [UPC and NPC](./UPC_and_NPC)

 

## Notes

  
1. [1](./Leaky_bucket#cite_ref-packet_1-0) [2](./Leaky_bucket#cite_ref-packet_1-1) In traffic management, the leaky bucket is normally applied to the equivalent of [OSI layer 2](./OSI_layer_2) [PDUs](./Protocol_data_unit), e.g. ATM [cells](./Asynchronous_Transfer_Mode#The_structure_of_an_ATM_cell) and [Ethernet frames](./Ethernet_II_framing), which are called [frames](./Frame_synchronization). It may be argued then that the description of this algorithm should be given in terms of *frames* not *packets*, which are, in the ISO-OSI 7-layer model, layer 3 [Network Layer](./Network_Layer) PDUs. However, the term packet is commonly used generically in the descriptions of this algorithm in the literature, and this convention is also applied here. It is not, however, intended to imply that the leaky bucket algorithm is applied exclusively to Network Layer PDUs.
2. [↑](./Leaky_bucket#cite_ref-defalign_9-0) To make Turner's description clearly aligned with ITU-T, the statement "If the counter exceeds a threshold upon being incremented, the network discards the packet" would have to be changed to something like "If the counter would exceed a threshold [equivalent to the bucket depth, T + *τ*, in the ITU-T description] upon being incremented, the network discards the packet and the counter is not incremented", i.e. it is only incremented when it is less than or equal to the limit value, *τ*, or at least T less than the bucket depth in the ITU-T description.
3. [1](./Leaky_bucket#cite_ref-shapelimit_12-0) [2](./Leaky_bucket#cite_ref-shapelimit_12-1) Traffic shaping functions include a queue that is necessarily of finite size. Hence, if the input stream exceeds some level of burstiness dependent on the length of the queue or consistently exceeds the bandwidth limit being imposed on the output stream, the queue will overflow, and packets will (normally) be discarded: see [Traffic shaping#Overflow condition](./Traffic_shaping#Overflow_condition). Therefore, traffic shaping functions can be seen as applying traffic policing to the input connection and traffic shaping to the output. They should, therefore, take a parameter for the burstiness limit on the input, in addition to those for the leaky bucket. However, this input burstiness limit may be defaulted to a value that is not expected to impact on normal traffic (the queue is assumed to be deep enough for all normal circumstances), and not always specified explicitly.

 

## References

 
1. [↑](./Leaky_bucket#cite_ref-UPC_NPC_2-0) ITU-T, *Traffic control and congestion control in B ISDN*, Recommendation I.371, International Telecommunication Union, 2004, page 17
2. [1](./Leaky_bucket#cite_ref-Turner_3-0) [2](./Leaky_bucket#cite_ref-Turner_3-1) [3](./Leaky_bucket#cite_ref-Turner_3-2) [4](./Leaky_bucket#cite_ref-Turner_3-3) [5](./Leaky_bucket#cite_ref-Turner_3-4) [6](./Leaky_bucket#cite_ref-Turner_3-5) [7](./Leaky_bucket#cite_ref-Turner_3-6) Turner, J., *New directions in communications (or which way to the information age?)*. IEEE Communications Magazine 24 (10): 8–15. [ISSN](./ISSN_(identifier)) [0163-6804](https://search.worldcat.org/issn/0163-6804), 1986.
3. [1](./Leaky_bucket#cite_ref-Tanenbaum-lbaq_4-0) [2](./Leaky_bucket#cite_ref-Tanenbaum-lbaq_4-1) [3](./Leaky_bucket#cite_ref-Tanenbaum-lbaq_4-2) [4](./Leaky_bucket#cite_ref-Tanenbaum-lbaq_4-3) [5](./Leaky_bucket#cite_ref-Tanenbaum-lbaq_4-4) [6](./Leaky_bucket#cite_ref-Tanenbaum-lbaq_4-5) Andrew S. Tanenbaum, *Computer Networks, Fourth Edition*, [ISBN](./ISBN_(identifier)) [0-13-166836-6](./Special:BookSources/0-13-166836-6), Prentice Hall PTR, 2003., page 401.
4. [1](./Leaky_bucket#cite_ref-ATMF-GCRA_5-0) [2](./Leaky_bucket#cite_ref-ATMF-GCRA_5-1) [3](./Leaky_bucket#cite_ref-ATMF-GCRA_5-2) [4](./Leaky_bucket#cite_ref-ATMF-GCRA_5-3) [5](./Leaky_bucket#cite_ref-ATMF-GCRA_5-4) [6](./Leaky_bucket#cite_ref-ATMF-GCRA_5-5) ATM Forum, The User Network Interface (UNI), v. 3.1, [ISBN](./ISBN_(identifier)) [0-13-393828-X](./Special:BookSources/0-13-393828-X), Prentice Hall PTR, 1995.
5. [1](./Leaky_bucket#cite_ref-ITU-T-GCRA_6-0) [2](./Leaky_bucket#cite_ref-ITU-T-GCRA_6-1) [3](./Leaky_bucket#cite_ref-ITU-T-GCRA_6-2) [4](./Leaky_bucket#cite_ref-ITU-T-GCRA_6-3) [5](./Leaky_bucket#cite_ref-ITU-T-GCRA_6-4) ITU-T, *Traffic control and congestion control in B ISDN*, Recommendation I.371, International Telecommunication Union, 2004, Annex A, page 87.
6. [1](./Leaky_bucket#cite_ref-McDysan-Spohn_7-0) [2](./Leaky_bucket#cite_ref-McDysan-Spohn_7-1) [3](./Leaky_bucket#cite_ref-McDysan-Spohn_7-2) [4](./Leaky_bucket#cite_ref-McDysan-Spohn_7-3) McDysan, David E. and Spohn, Darrel L., *ATM : Theory and Application*, [ISBN](./ISBN_(identifier)) [0-07-060362-6](./Special:BookSources/0-07-060362-6), McGraw-Hill series on computer communications, 1995, pages 358–9.
7. [↑](./Leaky_bucket#cite_ref-Tanenbaum-turner_8-0) Andrew S. Tanenbaum, *Computer Networks, Fourth Edition*, [ISBN](./ISBN_(identifier)) [0-13-166836-6](./Special:BookSources/0-13-166836-6), Prentice Hall PTR, 2003, Page 400.
8. [1](./Leaky_bucket#cite_ref-lbcounter_10-0) [2](./Leaky_bucket#cite_ref-lbcounter_10-1) ["Leaky bucket counter"](http://encyclopedia2.thefreedictionary.com/leaky+bucket+counter). *The Free Dictionary*.
9. [↑](./Leaky_bucket#cite_ref-intelseverboard_11-0) Intel, Intel Server Board S5400SF: *Technical Product Specification*, September 2007, [http://download.intel.com/support/motherboards/server/s5400sf/sb/s5400sf_tps_rev2_01.pdf](http://download.intel.com/support/motherboards/server/s5400sf/sb/s5400sf_tps_rev2_01.pdf).
10. [1](./Leaky_bucket#cite_ref-Tanenbaum-no_jitter_out_13-0) [2](./Leaky_bucket#cite_ref-Tanenbaum-no_jitter_out_13-1) [3](./Leaky_bucket#cite_ref-Tanenbaum-no_jitter_out_13-2) Andrew S. Tanenbaum, *Computer Networks, Fourth Edition*, [ISBN](./ISBN_(identifier)) [0-13-166836-6](./Special:BookSources/0-13-166836-6), Prentice Hall PTR, 2003, page 402.
11. [↑](./Leaky_bucket#cite_ref-14) ["Module ngx_http_limit_req_module"](https://nginx.org/en/docs/http/ngx_http_limit_req_module.html).