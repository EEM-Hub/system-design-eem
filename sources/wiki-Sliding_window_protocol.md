---
source: https://en.wikipedia.org/wiki/Sliding_window_protocol
fetched: 2026-06-19
---

Type of error-detection protocol at the data link layer, and transport layer for TCP "Sliding window" redirects here. For use in natural language processing, see [Sliding window based part-of-speech tagging](./Sliding_window_based_part-of-speech_tagging). For Sliding Window Compression, see [LZ77 and LZ78](./LZ77_and_LZ78). For sliding window average, see [moving average](./Moving_average). 
|  | This article includes a list ofgeneral references, butit lacks sufficient correspondinginline citations.Please help toimprovethis article byintroducingmore precise citations.(August 2010)(Learn how and when to remove this message) |
| --- | --- |

 

 

 

A **sliding window protocol** is a feature of packet-based [data transmission](./Data_transmission) [protocols](./Protocol_(computing)). Sliding window protocols are used where reliable in-order delivery of packets is required, such as in the [data link layer](./Data_link_layer) ([OSI layer 2](./OSI_model#Layer_2:_Data_link_layer)) as well as in the [Transmission Control Protocol](./Transmission_Control_Protocol) (i.e., [TCP windowing](./TCP_windowing)). They are also used to improve efficiency when the channel may include high [latency](./Network_delay).

 

Packet-based systems are based on the idea of sending a batch of data, the *packet*, along with additional data that allows the receiver to ensure it was received correctly, perhaps a [checksum](./Checksum). The paradigm is similar to a window sliding sideways to allow entry of fresh packets and reject the ones that have already been acknowledged. When the receiver verifies the data, it sends an [acknowledgment signal](./Acknowledgement_(data_networks)), or ACK, back to the sender to indicate it can send the next packet. In a simple [automatic repeat request](./Automatic_repeat_request) protocol (ARQ), the sender stops after every packet and waits for the receiver to ACK. This ensures packets arrive in the correct order, as only one may be sent at a time.

 

The time that it takes for the ACK signal to be received may represent a significant amount of time compared to the time needed to send the packet. In this case, the overall [throughput](./Throughput) may be much lower than theoretically possible. To address this, sliding window protocols allow a selected number of packets, the *window*, to be sent without having to wait for an ACK. Each packet receives a sequence number, and the ACKs send back that number. The protocol keeps track of which packets have been ACKed, and when they are received, sends more packets. In this way, the window *slides* along the stream of packets making up the transfer.

 

Sliding windows are a key part of many protocols. It is a key part of the TCP protocol, which inherently allows packets to arrive out of order, and is also found in many [file transfer protocols](./File_transfer_protocol) like [UUCP-g](./UUCP#g-protocol) and [ZMODEM](./ZMODEM) as a way of improving efficiency compared to non-windowed protocols like [XMODEM](./XMODEM).  See also [SEAlink](./SEAlink).

 

## Basic concept

 

Conceptually, each portion of the transmission (packets in most data link layers, but bytes in TCP) is assigned a unique consecutive sequence number, and the receiver uses the numbers to place received packets in the correct order, discarding duplicate packets and identifying missing ones.  The problem with this is that there is no limit on the size of the sequence number that can be required.

 

By placing limits on the number of packets that can be transmitted or received at any given time, a sliding window protocol allows an unlimited number of packets to be communicated using fixed-size sequence numbers.
The term *window* on the transmitter side represents the logical boundary of the total number of packets yet to be acknowledged by the receiver. The receiver informs the transmitter in each acknowledgment packet of the current maximum receiver buffer size (window boundary). The TCP header uses a 16-bit field to report the receiver window size to the sender. Therefore, the largest window that can be used is 216 = 64 kilobytes.

 

In slow-start mode, the transmitter starts with a low packet count and increases the number of packets in each transmission after receiving acknowledgment packets from the receiver. For every [ACK packet](./Acknowledgement_(data_networks)) received, the window slides by one packet (logically) to transmit one new packet. When the window threshold is reached, the transmitter sends one packet for each ACK packet received.

 

If the window limit is 10 packets, then in slow start mode, the transmitter may start transmitting one packet, followed by two packets (before transmitting two packets, one packet ACK has to be received), followed by three packets and so on until 10 packets. But after reaching 10 packets, further transmissions are restricted to one packet transmitted for one ACK packet received. In a simulation, this appears as if the window is moving by one packet distance for every ACK packet received. On the receiver side, the window moves one packet for every packet received.

 

The sliding window method ensures that traffic [congestion](./Network_congestion) on the network is avoided. The application layer will still be offering data for transmission to TCP without worrying about the network traffic congestion issues, as the TCP on the sender and receiver sides implement sliding windows of packet buffer. The window size may vary dynamically depending on network traffic.

 

For the highest possible [throughput](./Throughput), it is important that the transmitter is not forced to stop sending by the sliding window protocol earlier than one [round-trip delay time](./Round-trip_delay_time) (RTT).  The limit on the amount of data that it can send before stopping to wait for an acknowledgment should be larger than the [bandwidth-delay product](./Bandwidth-delay_product) of the communications link.  If it is not, the protocol will limit the effective [bandwidth](./Bandwidth_(computing)) of the link.

 

## Motivation

 

In any communication protocol based on [automatic repeat request](./Automatic_repeat_request) for [error control](./Error_control), the receiver must acknowledge received packets.  If the transmitter does not receive an acknowledgment within a reasonable time, it re-sends the data.

 

A transmitter that does not get an acknowledgment cannot know if the receiver actually received the packet; it may be that it was lost or damaged in transmission. If the [error detection](./Error_detection) mechanism reveals corruption, the packet will be ignored by the receiver, and a negative or duplicate acknowledgement will be sent by the receiver. The receiver may also be configured not send any acknowledgement at all. Similarly, the receiver is usually uncertain about whether its acknowledgments are being received. It may be that an acknowledgment was sent, but was lost or corrupted in the [transmission medium](./Transmission_medium).  In this case, the receiver must acknowledge the retransmission to prevent the data from being continually resent, but must otherwise ignore it.

 

## Protocol operation

 

The transmitter and receiver each have a current sequence number *nt* and *nr*, respectively.  They each also have a window size *wt* and *wr*.  The window sizes may vary, but in simpler implementations, they are fixed.  The window size must be greater than zero for any progress to be made.

 

As typically implemented, *nt* is the next packet to be transmitted, i.e., the sequence number of the first packet not yet transmitted.  Likewise, *nr* is the first packet not yet received.  Both numbers are [monotonically increasing](./Monotonically_increasing) with time; they only ever increase.

 

The receiver may also keep track of the greatest sequence number yet received; the variable *ns* is one more than the greatest sequence number on any accepted packet.  This can exceed *ns* by up to *wr*−1, so for simple receivers that only accept packets in order (*wr* = 1), this is the same as *nr*.  Note the distinction: all packets before *nr* have been received, no packets after *ns* have been received, and between *nr* and *ns*, some packets have been received.  Thus, *nr* ≤ *ns* ≤ *nt*.

 

When the receiver receives a packet, it updates its variables appropriately and transmits an acknowledgment with the new *nr*.  The transmitter keeps track of the greatest acknowledgment it has received *na*.  The transmitter knows that all packets up to, but not including *na* have been received, but is uncertain about packets between *na* and *nt*; i.e. *na* ≤ *nr* ≤ *nt*.

 

The sequence numbers always obey the rule that *na* ≤ *nr* ≤ *ns* ≤ *nt* ≤ *na* + *wt*.  That is:

 
- *na* ≤ *nr*: Acknowledgements received by the transmitter cannot exceed those sent by the receiver.
- *nr* ≤ *ns*: The span of fully received packets cannot extend into the range of never-received packets.
- *ns* ≤ *nt*: Packets received cannot exceed packets transmitted.
- *nt* ≤ *na* + *wt*: The greatest packet number sent is limited by the greatest acknowledgement received plus the transmit window size.

 

### Transmitter operation

 

Whenever the transmitter has data to send, it may transmit up to *wt* packets ahead of the latest acknowledgment *na*.  That is, it may transmit packet number *nt* as long as *nt* < *na*+*wt*.  *nt* is incremented to reflect the transmission.

 

In the absence of a communication error, the transmitter soon receives an acknowledgment for all the packets it has sent, leaving *na* equal to *nt*.  If this does not happen after a reasonable delay, the transmitter must retransmit the packet numbered *na*.

 

Techniques for defining "reasonable delay" can be extremely elaborate, but they only affect efficiency; the basic reliability of the sliding window protocol does not depend on the details.  Similarly, the transmitter may choose to retransmit additional packets between *na* and *nt*, but the decision does not affect the protocol's correctness.

 

### Receiver operation

 

Every time a packet numbered *x* is received, the receiver checks to see if it falls in the receive window, *nr* ≤ *x* < *nr*+*wr*.  (The simplest receivers have *wr* = 1, and only accept one possibility.)  If it falls within the window, the receiver accepts it.  If it is numbered *nr*, the receive sequence number is increased by 1, and possibly more if further consecutive packets were previously received and stored.  If *x* > *nr*, the packet is stored until all preceding packets have been received.[[1]](./Sliding_window_protocol#cite_note-1)  If *x*≥*ns*, the latter is updated to *ns*=*x*+1.

 

If the packet's number is not within the receive window, the receiver discards it and does not modify *nr* nor *ns*.

 

Whether the packet was accepted or not, the receiver transmits an acknowledgment containing the current *nr*.  (The acknowledgment may also include information about additional packets received between *nr* and *ns*, but that only helps efficiency.)

 

Note that there is no point having the receive window *wr* larger than the transmit window *wt*, because there is no need to worry about receiving a packet that will never be transmitted; the useful range is 1 ≤ *wr* ≤ *wt*.

 

### Sequence number range required

 Main article: [serial number arithmetic](./Serial_number_arithmetic) [![](//upload.wikimedia.org/wikipedia/commons/thumb/3/32/Sliding_Window.svg/500px-Sliding_Window.svg.png)](./File:Sliding_Window.svg)Sequence numbers modulo 4, with *wr*=1. Initially, *nt*=*nr*=0 

So far, the protocol has been described as if sequence numbers are of unlimited size, ever-increasing.  However, rather than transmitting the full sequence number *x* in messages, it is possible to transmit only *x* mod *N*, for some finite *N*.  (*N* is usually a [power of 2](./Power_of_2).)

 

For example, the transmitter will only receive acknowledgments in the range *na* to *nt*, inclusive.  Since it guarantees that *nt*−*na* ≤ *wt*, there are at most *wt*+1 possible sequence numbers that could arrive at any given time.  Thus, the transmitter can unambiguously decode the acknowledgement sequence number as long as *N* > *wt*.

 

A stronger constraint is imposed by the receiver.  The operation of the protocol depends on the receiver being able to reliably distinguish new packets (which should be accepted and processed) from retransmissions of old packets (which must be discarded, and the last acknowledgment retransmitted).  This can be done given knowledge of the transmitter's window size to infer the transmitter's *na*.  After receiving a packet numbered *x*, the receiver knows that *x* < *nt* ≤ *na*+*wt*, so *na* > *x*−*wt*.  Thus, packets numbered *x*−*wt* or less will never again be retransmitted.

 

The least sequence number we will ever receive in the future is *ns*−*wt*

 

The receiver also knows that the transmitter's *na* cannot be greater than the greatest acknowledgment ever sent, which is *nr*.  So we will never see a sequence number *na*+*wt* ≤ *nr*+*wt* or greater.

 

Thus, there are 2*wt* different sequence numbers that the receiver could receive at any one time.  It might therefore seem that we must have *N* ≥ 2*wt*.  However, the actual limit is lower.

 

The additional insight is that the receiver does not need to distinguish between sequence numbers that are too low (less than *nr*) or that are too high (greater than or equal to *ns*+*wr*).  In either case, the receiver ignores the packet except to retransmit an acknowledgment.  Thus, it is only necessary that *N* ≥ *wt*+*wr*.  As it is common to have *wr*<*wt* (e.g. see [Go-Back-N](./Sliding_window_protocol#Go-Back-N) below), this can permit larger *wt* within a fixed *N*.

 

## Examples

 

### The simplest sliding window: stop-and-wait

 

Although commonly distinguished from the sliding-window protocol, the [stop-and-wait ARQ](./Stop-and-wait_ARQ) protocol is actually the simplest possible implementation of it.  The transmit window is 1 packet, and the receive window is 1 packet.  Thus, *N* = 2 possible sequence numbers (conveniently represented by a single [bit](./Bit)) are required.

 

#### Ambiguity example

 

The transmitter alternately sends packets marked *odd* and *even*.  The acknowledgments likewise say *odd* and *even*.  Suppose that the transmitter, having sent an odd packet, did not wait for an odd acknowledgment and instead immediately sent the following even packet.  It might then receive an acknowledgment saying "expecting an odd packet next".  This would leave the transmitter in a quandary: has the receiver received both of the packets, or neither?

 

### Go-Back-N

 

[Go-Back-N ARQ](./Go-Back-N_ARQ) is the sliding window protocol with *wt*>1, but a fixed *wr*=1.  The receiver refuses to accept any packet but the next one in sequence.  If a packet is lost in transit, following packets are ignored until the missing packet is retransmitted, a minimum loss of one [round-trip time](./Round-trip_time).  For this reason, it is inefficient on links that suffer frequent [packet loss](./Packet_loss).

 

#### Ambiguity example

 

Suppose that we are using a 3-bit sequence number, such as is typical for [HDLC](./HDLC).  This gives *N*=23=8.  Since *wr*=1, we must limit *wt*≤7.  This is because, after transmitting 7 packets, there are 8 possible results: Anywhere from 0 to 7 packets could have been received successfully.  This is 8 possibilities, and the transmitter needs enough information in the acknowledgment to distinguish them all.

 

If the transmitter sent 8 packets without waiting for acknowledgment, it could find itself in a quandary similar to the stop-and-wait case: does the acknowledgment mean that all 8 packets were received successfully, or none of them?

 

### Selective repeat

 

The most general case of the sliding window protocol is [Selective Repeat ARQ](./Selective_Repeat_ARQ).  This requires a much more capable receiver, which can accept packets with sequence numbers higher than the current *nr* and store them until the gap is filled in.

 

The advantage, however, is that it is not necessary to discard following correct data for one round-trip time before the transmitter can be informed that a retransmission is required.  This is therefore preferred for links with low reliability and/or a high bandwidth-delay product.

 

The window size *wr* need only be larger than the number of *consecutive* lost packets that can be tolerated.  Thus, small values are popular; *wr*=2 is common.

 

#### Ambiguity example

 

The extremely popular [HDLC protocol](./High-Level_Data_Link_Control) uses a 3-bit sequence number and has an optional provision for selective repeat.  However, if selective repeat is to be used, the requirement that *wt*+*wr* ≤ 8 must be maintained; if *wr* is increased to 2, *wt* must be decreased to 6.

 

Suppose that *wr* =2, but an unmodified transmitter is used with *wt* =7, as is typically used with the go-back-N variant of HDLC.  Further suppose that the receiver begins with *nr* =*ns* =0.

 

Now suppose that the receiver sees the following series of packets (all modulo 8):

 0 1 2 3 4 5 6 *(pause)* 0 

Because *wr* =2, the receiver will accept and store the final packet 0 (thinking it is packet 8 in the series), while requesting a retransmission of packet 7.  However, it is also possible that the transmitter failed to receive any acknowledgments and has retransmitted packet 0.  In this latter case, the receiver would accept the wrong packet as packet 8.

 

The solution is for the transmitter to limit *wt* ≤6.  With this restriction, the receiver knows that if all acknowledgments were lost, the transmitter would have stopped after packet 5.  When it receives packet 6, the receiver can infer that the transmitter received the acknowledgment for packet 0 (the transmitter's *na* ≥1), and thus the following packet numbered 0 must be packet 8.

 

## Extensions

 

There are many ways that the protocol can be extended:

 
- The above examples assumed that packets are never reordered in transmission; they may be lost in transit ([error detection](./Error_detection) makes corruption equivalent to loss), but will never appear out of order.  The protocol can be extended to support packet reordering, as long as the distance can be bounded; the sequence number modulus *N* must be expanded by the maximum misordering distance.
- It is possible to not acknowledge every packet, as long as an acknowledgment is sent eventually if there is a pause.  For example, TCP normally acknowledges every second packet.

- It is common to inform the transmitter immediately if a gap in the packet sequence is detected.  HDLC has a special REJ (reject) packet for this.

- The transmit and receive window sizes may be changed during communication, as long as their sum remains within the limit of *N*.  Normally, they are each assigned maximum values that respect that limit, but the working value at any given time may be less than the maximum.  In particular:

- It is common to reduce the transmit window size to slow down transmission to match the link's speed, avoiding [saturation](./Saturation_(telecommunications)?action=edit&redlink=1) or [congestion](./Network_congestion).
- One common simplification of selective-repeat is the so-called SREJ-REJ ARQ.  This operates with *wr*=2 and buffers packets following a gap, but only allows a single lost packet; while waiting for that packet, *wr*=1, and if a second packet is lost, no more packets are buffered.  This gives most of the performance benefit of the full selective-repeat protocol with a simpler implementation.

 

## See also

 
- [Alternating bit protocol](./Alternating_bit_protocol)
- [Federal Standard 1037C](./Federal_Standard_1037C)
- [Compound TCP](./Compound_TCP)
- [Serial number arithmetic](./Serial_number_arithmetic)
- [TCP Fast Open](./TCP_Fast_Open)

 

## References

  
1. [↑](./Sliding_window_protocol#cite_ref-1) [Peterson, Larry L.](./Larry_L._Peterson); [Davie, Bruce S.](./Bruce_Davie) (2000). [*Computer Networks: A Systems Approach*](https://book.systemsapproach.org/). Morgan Kaufmann. [ISBN](./ISBN_(identifier)) [1-55860-577-0](./Special:BookSources/1-55860-577-0).

 
- Comer, Douglas E. "Internetworking with TCP/IP, Volume 1: Principles, Protocols, and Architecture", Prentice Hall, 1995. [ISBN](./ISBN_(identifier)) [0-13-216987-8](./Special:BookSources/0-13-216987-8)

 

## External links

 
- RFC 1323 - TCP Extensions for High Performance
- [TCP window scaling and broken routers](https://lwn.net/Articles/92727/), 2004