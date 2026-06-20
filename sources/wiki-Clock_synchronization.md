---
source: https://en.wikipedia.org/wiki/Clock_synchronization
fetched: 2026-06-19
---

Coordination of independent clocks For broader coverage of this topic, see [Clock network](./Clock_network). 

**Clock synchronization** is a topic in [computer science](./Computer_science) and [engineering](./Engineering) that aims to coordinate otherwise independent [clocks](./Clock). Even when initially set accurately, real clocks will differ after some amount of time due to [clock drift](./Clock_drift), caused by clocks counting time at slightly different rates. There are several problems that occur as a result of clock rate differences and several solutions, some being more acceptable than others in certain contexts.[[1]](./Clock_synchronization#cite_note-1)

 

## Terminology

 

In [serial communication](./Serial_communication), clock synchronization can refer to [clock recovery](./Clock_recovery), which achieves frequency synchronization, as opposed to full [phase synchronization](./Phase_synchronization). Such clock synchronization is used in [synchronization in telecommunications](./Synchronization_in_telecommunications) and [automatic baud rate detection](./Automatic_baud_rate_detection).[[2]](./Clock_synchronization#cite_note-2)

 

[Plesiochronous](./Plesiochronous) or [isochronous](./Isochronous) operation refers to a system with frequency synchronization and loose constraints on phase synchronization. [Synchronous](./Synchronous) operation implies a tighter synchronization based on time perhaps in addition to frequency.

 

## Problems

 

As a result of the difficulties managing time at smaller scales, there are problems associated with [clock skew](./Clock_skew) that take on more complexity in [distributed computing](./Distributed_computing) in which several computers will need to realize the same global time. For instance, in [Unix](./Unix) systems, the *[make](./Make_(software))* command is used to [compile](./Compile) new or modified code and seeks to avoid recompiling unchanged code. The *make* command uses the clock of the machine it runs on to determine which source files need to be recompiled. If the sources reside on a separate [file server](./File_server) and the two machines have unsynchronized clocks, the *make* program might not produce the correct results.[[3]](./Clock_synchronization#cite_note-3)

 

Synchronization is required for accurate reproduction of [streaming media](./Streaming_media). Clock synchronization is a significant component of [audio over Ethernet](./Audio_over_Ethernet) systems.

 

## Solutions

 

In a system with a central server, the synchronization solution is trivial; the server will dictate the system time.  [Cristian's algorithm](./Cristian's_algorithm) and the [Berkeley algorithm](./Berkeley_algorithm) are potential solutions to the clock synchronization problem in this environment.

 

In distributed computing, the problem takes on more complexity because a global time is not easily known. The most used clock synchronization solution on the Internet is the [Network Time Protocol](./Network_Time_Protocol) (NTP), which is a layered client-server architecture based on [User Datagram Protocol](./User_Datagram_Protocol) (UDP) message passing. [Lamport timestamps](./Lamport_timestamps) and [vector clocks](./Vector_clock) are concepts of the [logical clock](./Logical_clock) in distributed computing.

 

In a [wireless network](./Wireless_network), the problem becomes even more challenging due to the possibility of collision of the synchronization [packets](./Network_packet) on the wireless medium and the higher drift rate of clocks on low-cost wireless devices.[[4]](./Clock_synchronization#cite_note-Miklós-4)[[5]](./Clock_synchronization#cite_note-Panta-5)

 

### Berkeley algorithm

 Main article: [Berkeley algorithm](./Berkeley_algorithm) 

The Berkeley algorithm is suitable for systems where a [radio clock](./Radio_clock) is not present. This system has no way of making sure of the actual time other than by maintaining a global average time as the global time. A [time server](./Time_server) will periodically fetch the time from all the time clients, average the results, and then report back to the clients the adjustment that needs be made to their local clocks to achieve the average.  This algorithm highlights the fact that internal clocks may vary not only in the time they contain but also in the [clock rate](./Clock_rate).

 

### Clock-sampling mutual network synchronization

 

Clock-sampling mutual network synchronization (CS-MNS) is suitable for distributed and mobile applications. It has been shown to be scalable over mesh networks that include indirectly-linked non-adjacent nodes and is compatible with [IEEE 802.11](./IEEE_802.11) and similar standards. It can be accurate to the order of a few microseconds but requires direct physical wireless connectivity with negligible link delay (less than 1 microsecond) on links between adjacent nodes, limiting the distance between neighboring nodes to a few hundred meters.[[6]](./Clock_synchronization#cite_note-6)

 

### Cristian's algorithm

 Main article: [Cristian's algorithm](./Cristian's_algorithm) 

Cristian's algorithm relies on the existence of a time server.[[7]](./Clock_synchronization#cite_note-7)  The time server maintains its clock by using a radio clock or other accurate time source, then all other computers in the system stay synchronized with it.  A time client will maintain its clock by making a [procedure call](./Procedure_call) to the time server.  Variations of this algorithm make more precise time calculations by factoring in network [radio propagation](./Radio_propagation) time.

 

### Satellite navigation systems

 

In addition to its use in navigation, the [Global Positioning System](./Global_Positioning_System) (GPS) can also be used for clock synchronization. The accuracy of GPS time signals is ±10 nanoseconds.[[8]](./Clock_synchronization#cite_note-8) Using GPS (or other [satellite navigation](./Satellite_navigation) systems) for synchronization requires a receiver connected to an antenna with unobstructed view of the sky.

 

### Inter-range Instrumentation Group time codes

 

[IRIG timecodes](./IRIG_timecode) are standard formats for transferring timing information. Atomic frequency standards and GPS receivers designed for precision timing are often equipped with an IRIG output. The standards were created by the Telecommunications Working Group of the United States military's [Inter-Range Instrumentation Group](./Inter-Range_Instrumentation_Group) (IRIG), the standards body of the Range Commanders Council. Work on these standards started in October 1956, and the original standards were accepted in 1960.[[9]](./Clock_synchronization#cite_note-9)

 

### Network Time Protocol

 

[Network Time Protocol](./Network_Time_Protocol) (NTP) is a highly robust protocol, widely deployed throughout the Internet. Well tested over the years, it is generally regarded as the state of the art in distributed time synchronization protocols for [unreliable networks](./Unreliable_network). It can reduce synchronization offsets to times of the order of a few milliseconds over the public Internet and to sub-millisecond levels over [local area networks](./Local_area_network).

 

A simplified version of the NTP protocol, [Simple Network Time Protocol](./Simple_Network_Time_Protocol) (SNTP), can also be used as a pure single-shot stateless [primary/secondary](./Master/slave_(technology)) synchronization protocol, but lacks the sophisticated features of NTP, and thus has much lower performance and reliability levels.

 

### Precision Time Protocol

 

[Precision Time Protocol](./Precision_Time_Protocol) (PTP) is a master/slave protocol for delivery of highly accurate time over local area networks.

 

### Reference broadcast synchronization

 

The [Reference Broadcast Time Synchronization](./Reference_Broadcast_Time_Synchronization) (RBS) algorithm is often used in wireless networks and sensor networks. In this scheme, an initiator broadcasts a reference message to urge the receivers to adjust their clocks.

 

### Reference Broadcast Infrastructure Synchronization

 

The [Reference Broadcast Infrastructure Synchronization](./Reference_Broadcast_Infrastructure_Synchronization) (RBIS)[[10]](./Clock_synchronization#cite_note-10) protocol is a master/slave synchronization protocol, like RBS, based on a receiver/receiver synchronization paradigm. It is specifically tailored to be used in IEEE 802.11 wireless networks configured in infrastructure mode (i.e., coordinated by an access point). The protocol does not require any modification to the access point.

 

### Synchronous Ethernet

 

[Synchronous Ethernet](./Synchronous_Ethernet) uses Ethernet in a [synchronous manner](./Synchronous_serial_communication) such that when combined with synchronization protocols such as PTP in the case of the [White Rabbit Project](./White_Rabbit_Project), sub-nanosecond synchronization accuracy is achieved.

 

### Wireless ad hoc networks

 

Synchronization is achieved in [wireless ad hoc networks](./Wireless_ad_hoc_network) through sending synchronization messages in a [multi-hop](./Multi-hop_routing) manner and each node progressively synchronizing with the node that is the immediate sender of a synchronization message. Examples include Flooding Time Synchronization Protocol (FTSP),[[4]](./Clock_synchronization#cite_note-Miklós-4) and Harmonia,[[5]](./Clock_synchronization#cite_note-Panta-5) both able to achieve synchronization with accuracy on the order of microseconds.

 

### Huygens

 

Researchers from Stanford and Google introduced Huygens, a probe-based, end-to-end clock synchronization algorithm. Huygens is implemented in software and thus can be deployed in [data centers](./Data_center) or in [public cloud](./Public_cloud) environments. By leveraging some key aspects of modern data centers and applying novel estimation algorithms and signal processing techniques, the Huygens algorithm achieved an accuracy of tens of nanoseconds even at high network load.[[11]](./Clock_synchronization#cite_note-11) The findings of this research are being tested in financial market applications.[[12]](./Clock_synchronization#cite_note-12)

 

## See also

 
- [Einstein synchronisation](./Einstein_synchronisation)
- [International Atomic Time](./International_Atomic_Time)
- [Network Identity and Time Zone](./NITZ)
- [Synchronization (computer science)](./Synchronization_(computer_science))
- [Time and frequency transfer](./Time_and_frequency_transfer)
- [Time signal](./Time_signal)
- [Time standard](./Time_standard)
- [Reference Broadcast Infrastructure Synchronization](./Reference_Broadcast_Infrastructure_Synchronization)

 

## References

  
1. [↑](./Clock_synchronization#cite_ref-1) [Tanenbaum, Andrew S.](./Andrew_S._Tanenbaum); van Steen, Maarten (2002), *Distributed Systems : Principles and Paradigms*, [Prentice Hall](./Prentice_Hall), [ISBN](./ISBN_(identifier)) [0-13-088893-1](./Special:BookSources/0-13-088893-1)
2. [↑](./Clock_synchronization#cite_ref-2) Norman Matloff (September 3, 2001), [*Transmission on a Serial Line*](http://heather.cs.ucdavis.edu/~matloff/Networks/Serial/Serial.pdf) (PDF), retrieved 2018-04-17
3. [↑](./Clock_synchronization#cite_ref-3) Marco Platania (2018-06-03). ["Clock Synchronization"](http://www.dsn.jhu.edu/~platania/index_files/clock_sync.pdf) (PDF). p. 11.
4. [1](./Clock_synchronization#cite_ref-Miklós_4-0) [2](./Clock_synchronization#cite_ref-Miklós_4-1) Maróti, Miklós; Kusy, Branislav; Simon, Gyula; Lédeczi, Ákos (2004). "The flooding time synchronization protocol". *Proceedings of the 2nd international conference on Embedded networked sensor systems*. SenSys '04. New York, NY, USA: ACM. pp. 39–49. [doi](./Doi_(identifier)):[10.1145/1031495.1031501](https://doi.org/10.1145%2F1031495.1031501). [ISBN](./ISBN_(identifier)) [1581138792](./Special:BookSources/1581138792). [S2CID](./S2CID_(identifier)) [9897231](https://api.semanticscholar.org/CorpusID:9897231).
5. [1](./Clock_synchronization#cite_ref-Panta_5-0) [2](./Clock_synchronization#cite_ref-Panta_5-1) Koo, Jinkyu; Panta, Rajesh K.; Bagchi, Saurabh; Montestruque, Luis (2009). "A tale of two synchronizing clocks". *Proceedings of the 7th ACM Conference on Embedded Networked Sensor Systems*. SenSys '09. New York, NY, USA: ACM. pp. 239–252. [doi](./Doi_(identifier)):[10.1145/1644038.1644062](https://doi.org/10.1145%2F1644038.1644062). [ISBN](./ISBN_(identifier)) [9781605585192](./Special:BookSources/9781605585192). [S2CID](./S2CID_(identifier)) [8242938](https://api.semanticscholar.org/CorpusID:8242938).
6. [↑](./Clock_synchronization#cite_ref-6) Rentel, Carlos H.; Kunz, Thomas (March 2005), "A clock-sampling mutual network time-synchronization algorithm for wireless ad hoc networks", *IEEE Wireless Communications and Networking Conference, 2005*, vol. 1, IEEE Press, pp. 638–644, [doi](./Doi_(identifier)):[10.1109/WCNC.2005.1424575](https://doi.org/10.1109%2FWCNC.2005.1424575), [ISBN](./ISBN_(identifier)) [0-7803-8966-2](./Special:BookSources/0-7803-8966-2), [S2CID](./S2CID_(identifier)) [1340072](https://api.semanticscholar.org/CorpusID:1340072)
7. [↑](./Clock_synchronization#cite_ref-7) Cristian, F. (1989), "Probabilistic clock synchronization", *Distributed Computing*, **3** (3), Springer: 146–158, [doi](./Doi_(identifier)):[10.1007/BF01784024](https://doi.org/10.1007%2FBF01784024), [S2CID](./S2CID_(identifier)) [3170166](https://api.semanticscholar.org/CorpusID:3170166)
8. [↑](./Clock_synchronization#cite_ref-8) ["Common View GPS Time Transfer"](https://web.archive.org/web/20121028043917/http://tf.nist.gov/time/commonviewgps.htm). [National Institute of Standards and Technology](./National_Institute_of_Standards_and_Technology). Archived from [the original](http://tf.nist.gov/time/commonviewgps.htm) on 2012-10-28.
9. [↑](./Clock_synchronization#cite_ref-9) Josh Matson (May 2013). ["Choosing the correct Time Synchronization Protocol and incorporating the 1756-TIME module into your Application"](http://literature.rockwellautomation.com/idc/groups/literature/documents/wp/enet-wp030_-en-e.pdf) (PDF). Rockwell Automation. Retrieved 2019-08-13.
10. [↑](./Clock_synchronization#cite_ref-10)  Cena, G.; Scanzio, S.; Valenzano, A.; Zunino, C. (June 2015), "Implementation and Evaluation of the Reference Broadcast Infrastructure Synchronization Protocol", *IEEE Transactions on Industrial Informatics*, **11** (3), IEEE Press: 801–811, [Bibcode](./Bibcode_(identifier)):[2015ITII...11..801C](https://ui.adsabs.harvard.edu/abs/2015ITII...11..801C), [doi](./Doi_(identifier)):[10.1109/TII.2015.2396003](https://doi.org/10.1109%2FTII.2015.2396003), [S2CID](./S2CID_(identifier)) [17867070](https://api.semanticscholar.org/CorpusID:17867070)
11. [↑](./Clock_synchronization#cite_ref-11) [*Exploiting a Natural Network Effect for Scalable, Fine-grained Clock Synchronization*](https://www.usenix.org/conference/nsdi18/presentation/geng). 2018. pp. 81–94. [ISBN](./ISBN_(identifier)) [9781939133014](./Special:BookSources/9781939133014).
12. [↑](./Clock_synchronization#cite_ref-12) John Markoff (June 29, 2018). ["Time Split to the Nanosecond Is Precisely What Wall Street Wants"](https://www.nytimes.com/2018/06/29/technology/computer-networks-speed-nasdaq.html). *New York Times*.

 

## Further reading

 
- Govindan Kannan, Pravein.; Joshi, Raj.; Chan, Mun Choon. (Apr 2019), "Precise Time-synchronization in the Data-Plane using Programmable Switching ASICs", *Proceedings of the 2019 ACM Symposium on SDN Research*, ACM, pp. 8–20, [doi](./Doi_(identifier)):[10.1145/3314148.3314353](https://doi.org/10.1145%2F3314148.3314353), [ISBN](./ISBN_(identifier)) [9781450367103](./Special:BookSources/9781450367103), [S2CID](./S2CID_(identifier)) [85518997](https://api.semanticscholar.org/CorpusID:85518997)
- [*Exploiting a Natural Network Effect for Scalable, Fine-grained Clock Synchronization*](https://www.usenix.org/conference/nsdi18/presentation/geng), [ISBN](./ISBN_(identifier)) [9781939133014](./Special:BookSources/9781939133014), retrieved 2021-10-19