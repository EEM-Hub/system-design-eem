---
source: https://en.wikipedia.org/wiki/Push_technology
fetched: 2026-06-19
---

Method of network communication where requests are sent by the publisher 

**Push technology,** also known as **server push,** is a communication method where the communication is initiated by a [server](./Server_(computing)) rather than a [client](./Client_(computing)). This approach is different from the "[pull](./Pull_technology)" method where the communication is initiated by a client.[[1]](./Push_technology#cite_note-1)

 

In push technology, clients can express their preferences for certain types of information or data, typically through a process known as the [publish–subscribe](./Publish–subscribe_pattern) model. In this model, a client "subscribes" to specific information channels hosted by a server. When new content becomes available on these channels, the server automatically sends, or "pushes," this information to the subscribed client.

 

Under certain conditions, such as restrictive security policies that block incoming [HTTP](./HTTP) requests, push technology is sometimes simulated using a technique called [polling.](./Polling_(computer_science)) In these cases, the client periodically checks with the server to see if new information is available, rather than receiving automatic updates.

 

## General use

 

[Synchronous conferencing](./Synchronous_conferencing) and [instant messaging](./Instant_messaging) are examples of push services. Chat messages and sometimes [files](./Computer_file) are pushed to the user as soon as they are received by the messaging service. Both decentralized [peer-to-peer](./Peer-to-peer) programs (such as [WASTE](./WASTE)) and centralized programs (such as [IRC](./Internet_Relay_Chat) or [XMPP](./Extensible_Messaging_and_Presence_Protocol)) allow pushing files, which means the sender initiates the data transfer rather than the recipient.

 

[Email](./Email) may also be a push system: [SMTP](./SMTP) is a push protocol (see [Push e-mail](./Push_e-mail)). However, the last step—from mail server to desktop computer—typically uses a pull protocol like [POP3](./POP3) or [IMAP](./IMAP). Modern e-mail clients make this step seem instantaneous by repeatedly [polling](./Polling_(computer_science)) the mail server, frequently checking it for new mail. The IMAP protocol includes the [IDLE](./IMAP_IDLE) command, which allows the server to tell the client when new messages arrive. The original [BlackBerry](./BlackBerry) was the first popular example of push-email in a wireless context.[*[citation needed](./Wikipedia:Citation_needed)*]

 

Another example is the [PointCast Network](./PointCast_(dotcom)), which was widely covered in the 1990s. It delivered news and stock market data as a screensaver. Both [Netscape](./Netscape) and [Microsoft](./Microsoft) integrated push technology through the [Channel Definition Format](./Channel_Definition_Format) (CDF) into their software at the height of the [browser wars](./Browser_wars), but it was never very popular. CDF faded away and was removed from the browsers of the time, replaced in the 2000s with [RSS](./RSS) (a pull system.)

 

Other uses of push-enabled [web applications](./Web_application) include software updates distribution ("push updates"), market data distribution (stock tickers), online chat/messaging systems ([webchat](./Webchat)), auctions, online betting and gaming, sport results, monitoring consoles, and [sensor network](./Sensor_network) monitoring.

 

## Examples

 

### Web push

 

The Web push proposal of the [Internet Engineering Task Force](./Internet_Engineering_Task_Force) is a simple protocol using [HTTP version 2](./HTTP/2) to deliver real-time events, such as incoming calls or messages, which can be delivered (or "pushed") in a timely fashion. The protocol consolidates all [real-time](./Real-time_computing) events into a single session which ensures more efficient use of network and radio resources. A single service consolidates all events, distributing those events to applications as they arrive. This requires just one session, avoiding duplicated overhead costs.[[2]](./Push_technology#cite_note-2)

 

Web Notifications are part of the [W3C](./W3C) standard and define an [API](./API) for end-user notifications. A notification allows alerting the user of an event, such as the delivery of an email, outside the context of a web page.[[3]](./Push_technology#cite_note-3) As part of this standard, Push API is fully implemented in [Chrome](./Google_Chrome), [Firefox](./Firefox), and [Edge](./Microsoft_Edge), and partially implemented in [Safari](./Safari_(web_browser)) as of February 2023[[update]](https://en.wikipedia.org/w/index.php?title=Push_technology&action=edit).[[4]](./Push_technology#cite_note-4)[[5]](./Push_technology#cite_note-5)

 

### HTTP server push

 

HTTP server push (also known as HTTP streaming) is a mechanism for sending unsolicited (asynchronous) data from a [web server](./Web_server) to a [web browser](./Web_browser). HTTP server push can be achieved through any of several mechanisms.

 

As a part of [HTML5](./HTML5) the [Web Socket](./WebSocket) API allows a web server and client to communicate over a [full-duplex](./Duplex_(telecommunications)) TCP connection.

 

Generally, the web server does not terminate a connection after response data has been served to a client. The web server leaves the connection open so that if an event occurs (for example, a change in internal data which needs to be reported to one or multiple clients), it can be sent out immediately; otherwise, the event would have to be queued until the client's next request is received. Most web servers offer this functionality via [CGI](./Common_Gateway_Interface) (e.g., Non-Parsed Headers scripts on [Apache HTTP Server](./Apache_HTTP_Server)).[[6]](./Push_technology#cite_note-6)[[7]](./Push_technology#cite_note-7) The underlying mechanism for this approach is [chunked transfer encoding](./Chunked_transfer_encoding).

 

Another mechanism is related to a special [MIME](./MIME) type called `multipart/x-mixed-replace`, which was introduced by [Netscape](./Netscape) in 1995. Web browsers interpret this as a document that changes whenever the server pushes a new version to the client.[[8]](./Push_technology#cite_note-:0-8) It is still supported by [Firefox](./Firefox), [Opera](./Opera_(web_browser)), and [Safari](./Safari_(web_browser)) today, but it is ignored by [Internet Explorer](./Internet_Explorer)[[9]](./Push_technology#cite_note-9) and is only partially supported by [Chrome](./Google_Chrome).[[10]](./Push_technology#cite_note-10) It can be applied to [HTML](./HTML) documents, and also for streaming images in [webcam](./Webcam) applications.

 

The [WHATWG](./WHATWG) Web Applications 1.0 proposal[[11]](./Push_technology#cite_note-11) includes a mechanism to push content to the client. On September 1, 2006, the Opera web browser implemented this new experimental system in a feature called "[Server-Sent Events](./Server-sent_events)".[[12]](./Push_technology#cite_note-12)[[13]](./Push_technology#cite_note-13) It is now part of the [HTML5](./HTML5) standard.[[14]](./Push_technology#cite_note-14)

 

### Pushlet

 

In this technique, the server takes advantage of [persistent HTTP connections](./HTTP_persistent_connection), leaving the response perpetually "open" (i.e., the server never terminates the response), effectively fooling the browser to remain in "loading" mode after the initial page load could be considered complete. The server then periodically sends snippets of [JavaScript](./JavaScript) to update the content of the page, thereby achieving push capability. By using this technique, the client doesn't need [Java applets](./Java_applet) or other plug-ins in order to keep an open connection to the server; the client is automatically notified about new events, pushed by the server.[[15]](./Push_technology#cite_note-15)[[16]](./Push_technology#cite_note-16) One serious drawback to this method, however, is the lack of control the server has over the browser timing out; a page refresh is always necessary if a timeout occurs on the browser end.

 

### Long polling

 

Long polling is itself not a true push; long polling is a variation of the traditional polling technique, but it allows emulating a push mechanism under circumstances where a real push is not possible, such as sites with security policies that require rejection of incoming HTTP requests.[[17]](./Push_technology#cite_note-17)[[18]](./Push_technology#cite_note-18)

 

With long polling, the client requests to get more information from the server exactly as in normal polling, but with the expectation that the server may not respond immediately. If the server has no new information for the client when the poll is received, then instead of sending an empty response, the server holds the request open and waits for response information to become available. Once it does have new information, the server immediately sends an HTTP response to the client, completing the open HTTP request. Upon receipt of the server response, the client often immediately issues another server request. In this way the usual response latency (the time between when the information first becomes available and the next client request) otherwise associated with polling clients is eliminated.[[19]](./Push_technology#cite_note-19)

 

For example, [BOSH](./BOSH_(protocol)) is a popular, long-lived HTTP technique used as a long-polling alternative to a continuous TCP connection when such a connection is difficult or impossible to employ directly (e.g., in a web browser);[[20]](./Push_technology#cite_note-20) it is also an underlying technology in the [XMPP](./XMPP), which Apple uses for its iCloud push support.[*[citation needed](./Wikipedia:Citation_needed)*]

 

### Flash XML Socket relays

 

This technique, used by [chat](./Online_chat) applications, makes use of the [XML Socket](./XMLSocket) object in a single-pixel [Adobe Flash](./Adobe_Flash) movie. Under the control of [JavaScript](./JavaScript), the client establishes a [TCP connection](./TCP_connection) to a [unidirectional](./Unidirectional_network) relay on the server. The relay server does not read anything from this [socket](./Network_socket); instead, it immediately sends the client a [unique identifier](./Unique_identifier). Next, the client makes an [HTTP request](./HTTP_request) to the web server, including this identifier with it. The web application can then push messages addressed to the client to a local interface of the relay server, which relays them over the Flash socket. The advantage of this approach is that it appreciates the natural read-write asymmetry that is typical of many web applications, including chat, and as a consequence it offers high efficiency. Since it does not accept data on outgoing sockets, the relay server does not need to poll outgoing TCP connections *at all*, making it possible to hold open tens of thousands of concurrent connections. In this model, the limit to scale is the TCP stack of the underlying server operating system.

 

### Reliable Group Data Delivery (RGDD)

 

In services such as [cloud computing](./Cloud_computing), to increase reliability and availability of data, it is usually pushed (replicated) to several machines. For example, the Hadoop Distributed File System (HDFS) makes 2 extra copies of any object stored. RGDD focuses on efficiently casting an object from one location to many while saving bandwidth by sending minimal number of copies (only one in the best case) of the object over any link across the network. For example, Datacast[[21]](./Push_technology#cite_note-21) is a scheme for delivery to many nodes inside data centers that relies on regular and structured topologies and DCCast[[22]](./Push_technology#cite_note-22) is a similar approach for delivery across data centers.

 

### Push notification

 See also: [Mobile marketing § Push notifications](./Mobile_marketing#Push_notifications) 

A push notification is a message that is "pushed" from a back-end server or application to a user interface, e.g. mobile applications[[23]](./Push_technology#cite_note-23) or desktop applications. [Apple](./Apple_Inc.) introduced push notifications for [iPhone](./IPhone) in 2009,[[24]](./Push_technology#cite_note-24) and in 2010 [Google](./Google) released "Google Cloud to Device Messaging" (superseded by [Google Cloud Messaging](./Google_Cloud_Messaging) and then by [Firebase Cloud Messaging](./Firebase_Cloud_Messaging)).[[25]](./Push_technology#cite_note-25)
In November 2015, [Microsoft](./Microsoft) announced that the [Windows Notification Service](./Windows_Notification_Service) would be expanded to make use of the Universal Windows Platform architecture, allowing for push data to be sent to [Windows 10](./Windows_10), [Windows 10 Mobile](./Windows_10_Mobile), [Xbox](./Xbox), and other supported platforms using universal API calls and POST requests.[[26]](./Push_technology#cite_note-26)

 

Push notifications are mainly divided into two approaches, local notifications and remote notifications.[[27]](./Push_technology#cite_note-27) For local notifications, the application schedules the notification with the local device's OS. The application sets a timer in the application itself, provided it is able to continuously run in the background. When the event's scheduled time is reached, or the event's programmed condition is met, the message is displayed in the application's user interface.

 

Remote notifications are handled by a remote server. Under this scenario, the client application needs to be registered on the server with a unique key (e.g., a [UUID](./UUID) or Apple *Device Token*). The server then transmits the message against the unique key to deliver it to the client via an agreed client/server protocol such as [HTTP](./HTTP) or [XMPP](./XMPP). When the push notification arrives at the client, it can cause the display of short notifications or messages, set badges on application icons, blink or continuously light up the [notification LED](./Notification_LED), or play alert sounds to attract user's attention.[[28]](./Push_technology#cite_note-28) Push notifications are usually used by applications to bring information to users' attention. The content of the messages can be classified in the following example categories:

 
- Chat messages from a messaging application such as [Facebook Messenger](./Facebook_Messenger) sent by other users.[[29]](./Push_technology#cite_note-29)
- Vendor special offers: A vendor may want to advertise their offers to customers.
- Event reminders: Some applications may allow the customer to create a reminder or alert for a specific time.
- Subscribed topic changes: Users may want to get updates regarding the weather in their location, or monitor a web page to track changes, for instance.

 

Real-time push notifications may raise privacy issues since they can be used to bind virtual identities of social network pseudonyms to the real identities of the smartphone owners.[[30]](./Push_technology#cite_note-30) The use of unnecessary push notifications for promotional purposes has been criticized as an example of [attention theft](./Attention_theft).[[31]](./Push_technology#cite_note-IEEE-31)

 

## See also

 ♦♦♦ Please keep the list in alphabetical order ♦♦♦  
- [BlazeDS](./BlazeDS)
- [BOSH (protocol)](./BOSH_(protocol))
- [Channel Definition Format](./Channel_Definition_Format)
- [Client–server model](./Client–server_model)
- [Comet (programming)](./Comet_(programming))
- [File transfer](./File_transfer)
- [GraniteDS](./GraniteDS)
- [HTTP/2](./HTTP/2)
- [Lightstreamer](./Lightstreamer)
- [Notification LED](./Notification_LED)
- [Pull technology](./Pull_technology)
- [Push Access Protocol](./Push_Access_Protocol)
- [Push email](./Push_email)
- [SQL Server Notification Services](./SQL_Server_Notification_Services)
- [Streaming media](./Streaming_media)
- [WebSocket](./WebSocket)
- [WebSub](./WebSub)

  

## References

  
1. [↑](./Push_technology#cite_ref-1) ["Push Technology"](https://www.techopedia.com/definition/5732/push-technology). *Techopedia*. 2012-11-18. Retrieved 2023-07-23.
2. [↑](./Push_technology#cite_ref-2) M. Thomson, E. Damaggio and B. Raymor (October 22, 2016). ["Generic Event Delivery Using HTTP Push"](https://tools.ietf.org/html/draft-ietf-webpush-protocol-12). *Internet Draft*. Internet Engineering Task Force. Retrieved October 28, 2016.
3. [↑](./Push_technology#cite_ref-3) ["Notifications API Standard"](https://notifications.spec.whatwg.org/). *notifications.spec.whatwg.org*. Retrieved April 30, 2024.
4. [↑](./Push_technology#cite_ref-4) ["Push API"](https://www.w3.org/TR/push-api/). Retrieved April 30, 2024.
5. [↑](./Push_technology#cite_ref-5) ["Push API - Web APIs | MDN"](https://developer.mozilla.org/en-US/docs/Web/API/Push_API). *developer.mozilla.org*. 2023-02-22. Retrieved 2023-05-16.
6. [↑](./Push_technology#cite_ref-6) ["HTTP Push Mechanism"](https://dev.to/azmy/http-push-mechanism-3c3j). *DEV Community*. 2026-01-31. Retrieved 2026-04-14.
7. [↑](./Push_technology#cite_ref-7) ["Server Sent Events"](https://www.enjoyalgorithms.com/blog/server-sent-events/). *www.enjoyalgorithms.com*. Retrieved 2026-04-14.
8. [↑](./Push_technology#cite_ref-:0_8-0) [CGI Programming on the World Wide Web](http://www.oreilly.com/openbook/cgi/ch06_06.html) O'Reilly book explaining how to use Netscape server-push
9. [↑](./Push_technology#cite_ref-9) [Server-Push Documents (HTML & XHTML: The Definitive Guide)](http://victor.transformadora.com/Oreilly/wdesign/xhtml/ch13_03.htm) [Archived](https://web.archive.org/web/20080417004248/http://victor.transformadora.com/Oreilly/wdesign/xhtml/ch13_03.htm) 2008-04-17 at the [Wayback Machine](./Wayback_Machine) O'Reilly book explaining server-push
10. [↑](./Push_technology#cite_ref-10) [Remove support for multipart/x-mixed-replace main resources](https://bugs.chromium.org/p/chromium/issues/detail?id=249132)
11. [↑](./Push_technology#cite_ref-11) ["Web Applications 1.0 specification"](https://www.whatwg.org/specs/web-apps/current-work/#scs-server-sent).
12. [↑](./Push_technology#cite_ref-12) ["Event Streaming to Web Browsers"](http://my.opera.com/WebApplications/blog/show.dml/438711). 2006-09-01. Retrieved 2007-03-23.
13. [↑](./Push_technology#cite_ref-13) ["Opera takes the lead with AJAX support among browsers: More efficient streaming"](https://web.archive.org/web/20070318013327/http://operawatch.com/news/2006/09/opera-takes-the-lead-with-ajax-support-among-browsers-more-efficient-streaming.html). 2006-09-01. Archived from [the original](http://operawatch.com/news/2006/09/opera-takes-the-lead-with-ajax-support-among-browsers-more-efficient-streaming.html) on 2007-03-18. Retrieved 2007-03-23.
14. [↑](./Push_technology#cite_ref-14) ["HTML Standard – Server-sent events"](https://html.spec.whatwg.org/multipage/server-sent-events.html). *html.spec.whatwg.org*. 31 March 2022. Retrieved 1 April 2022.
15. [↑](./Push_technology#cite_ref-15) ["Pushlets introduction"](https://web.archive.org/web/20090805055526/http://www.pushlets.com/doc/whitepaper-toc.html). Archived from [the original](http://www.pushlets.com/doc/whitepaper-toc.html) on 2009-08-05. Retrieved 2008-06-05.
16. [↑](./Push_technology#cite_ref-16) Van Den Broecke, Just (1 March 2000). ["Pushlets: Send events from servlets to DHTML client browsers"](https://www.infoworld.com/article/2076063/pushlets--send-events-from-servlets-to-dhtml-client-browsers.html). *[JavaWorld](./JavaWorld)*. Retrieved 2020-07-13.
17. [↑](./Push_technology#cite_ref-17) ["What is Long Polling and How Does it Work?"](https://www.pubnub.com/guides/long-polling/). *PubNub*. Retrieved 2026-04-14.
18. [↑](./Push_technology#cite_ref-18) ["Long Polling vs WebSockets — How to Achieve Real-Time Communication day 55 of system design"](https://dev.to/vincenttommi/long-polling-vs-websockets-how-to-achieve-real-time-communication-day-55-of-system-design-1nhl). *DEV Community*. 2025-10-13. Retrieved 2026-04-14.
19. [↑](./Push_technology#cite_ref-19) Saint-Andre, Peter; Loreto, Salvatore; Salsano, Stefano; Wilkins, Greg (April 2011). ["RFC6202 - Known Issues and Best Practices for the Use of Long Polling and Streaming in Bidirectional HTTP"](https://tools.ietf.org/html/rfc6202#section-2.1). *tools.ietf.org*. [doi](./Doi_(identifier)):[10.17487/RFC6202](https://doi.org/10.17487%2FRFC6202). Retrieved 2016-05-14.
20. [↑](./Push_technology#cite_ref-20) ["XEP-0124: Bidirectional-streams Over Synchronous HTTP (BOSH)"](http://xmpp.org/extensions/xep-0124.html#intro). Retrieved 2012-06-26.
21. [↑](./Push_technology#cite_ref-21) C. Guo; et al. (November 1, 2012). ["Datacast: A Scalable and Efficient Reliable Group Data Delivery Service For Data Centers"](https://www.microsoft.com/en-us/research/publication/datacast-a-scalable-and-efficient-reliable-group-data-delivery-service-for-data-centers-2/). *Microsoft Research*. ACM. Retrieved Jun 6, 2017.
22. [↑](./Push_technology#cite_ref-22) M. Noormohammadpour; et al. (July 10, 2017). ["DCCast: Efficient Point to Multipoint Transfers Across Datacenters"](https://www.researchgate.net/publication/316921061). USENIX. Retrieved Jun 6, 2017.
23. [↑](./Push_technology#cite_ref-23) Wohllebe, Atilla. (2020). ["Consumer Acceptance of App Push Notifications: Systematic Review on the Influence of Frequency"](https://doi.org/10.3991%2Fijim.v14i13.14563). *International Journal of Interactive Mobile Technologies*. **14** (13): 36–47. [doi](./Doi_(identifier)):[10.3991/ijim.v14i13.14563](https://doi.org/10.3991%2Fijim.v14i13.14563).
24. [↑](./Push_technology#cite_ref-24) ["iPhone push notification service for devs announced"](https://www.engadget.com/2008/06/09/iphone-push-notification-service-for-devs-announced/). *Engadget*. Retrieved 2016-10-18.
25. [↑](./Push_technology#cite_ref-25) ["Google Cloud Messaging for Android (GCM) Unveiled, to Replace C2DM Framework"](https://www.infoq.com/news/2012/08/GoogleCMReplacesC2Dm). *InfoQ*. Retrieved 2016-10-18.
26. [↑](./Push_technology#cite_ref-26) mijacobs. ["Windows Push Notification Services (WNS) overview"](https://docs.microsoft.com/en-us/windows/uwp/controls-and-patterns/tiles-and-notifications-windows-push-notification-services--wns--overview). *docs.microsoft.com*. Retrieved 2017-10-20.
27. [↑](./Push_technology#cite_ref-27) ["Local and Remote Notifications in Depth"](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/). *developer.apple.com*. Retrieved 2016-10-18.
28. [↑](./Push_technology#cite_ref-28) ["Android and iOS Push Notifications – Blog – JatApp"](https://web.archive.org/web/20171020190857/http://jatapp.com/blog/android-ios-push-notifications/). *jatapp.com*. Archived from [the original](http://jatapp.com/blog/android-ios-push-notifications/) on October 20, 2017. Retrieved 2017-10-20.
29. [↑](./Push_technology#cite_ref-29) ["How do I adjust my mobile push notifications from Facebook? | Facebook Help Center | Facebook"](https://www.facebook.com/help/103859036372845?helpref=faq_content). *www.facebook.com*. Retrieved 2016-10-18.
30. [↑](./Push_technology#cite_ref-30) Loreti, Pierpaolo; Bracciale, Lorenzo; Caponi, Alberto (2018). ["Push Attack: Binding Virtual and Real Identities Using Mobile Push Notifications"](https://doi.org/10.3390%2Ffi10020013). *Future Internet*. **10** (2): 13. [doi](./Doi_(identifier)):[10.3390/fi10020013](https://doi.org/10.3390%2Ffi10020013).
31. [↑](./Push_technology#cite_ref-IEEE_31-0) McFedries, Paul (22 May 2014). ["Stop, Attention Thief!"](https://spectrum.ieee.org/stop-attention-thief). *[IEEE Spectrum](./IEEE_Spectrum)*. [Institute of Electrical and Electronics Engineers](./Institute_of_Electrical_and_Electronics_Engineers). Retrieved 9 August 2021.

 

## External links

 
- W3C Push Workshop. A 1997 workshop that discussed push technology and some early examples thereof
- [HTTP Streaming with Ajax](https://web.archive.org/web/20051201013553/http://ajaxpatterns.org/HTTP_Streaming) A description of HTTP Streaming from the Ajax Patterns website
- [The Web Socket API](http://www.w3.org/TR/websockets/) candidate recommendation
- [HTML5 Server-Sent Events](http://www.w3.org/TR/eventsource/) draft specification

 
| vteWeb interfaces |
| --- |
| Server-sideProtocolsHTTPv2v3EncryptionWebDAVCGISCGIFCGIAJPWSRPWebSocketServer APIsC NSAPIC ASAPIC ISAPICOM ASPJakarta ServletcontainerCLI OWINASP.NET HandlerPython WSGIPython ASGIRuby RackJavaScript JSGIPerl PSGIPortletcontainerApache modulesmod_includemod_jkmod_lispmod_monomod_parrotmod_perlmod_phpmod_proxymod_pythonmod_wsgimod_rubyPhusion PassengerTopicsWeb servicevs.Web resourceWOAvs.ROAOpen APIWebhookApplication servercomparisonScripting | Server-side | Protocols | HTTPv2v3EncryptionWebDAVCGISCGIFCGIAJPWSRPWebSocket | Server APIs | C NSAPIC ASAPIC ISAPICOM ASPJakarta ServletcontainerCLI OWINASP.NET HandlerPython WSGIPython ASGIRuby RackJavaScript JSGIPerl PSGIPortletcontainer | Apache modules | mod_includemod_jkmod_lispmod_monomod_parrotmod_perlmod_phpmod_proxymod_pythonmod_wsgimod_rubyPhusion Passenger | Topics | Web servicevs.Web resourceWOAvs.ROAOpen APIWebhookApplication servercomparisonScripting |
| Server-side |
| Protocols | HTTPv2v3EncryptionWebDAVCGISCGIFCGIAJPWSRPWebSocket |
| Server APIs | C NSAPIC ASAPIC ISAPICOM ASPJakarta ServletcontainerCLI OWINASP.NET HandlerPython WSGIPython ASGIRuby RackJavaScript JSGIPerl PSGIPortletcontainer |
| Apache modules | mod_includemod_jkmod_lispmod_monomod_parrotmod_perlmod_phpmod_proxymod_pythonmod_wsgimod_rubyPhusion Passenger |
| Topics | Web servicevs.Web resourceWOAvs.ROAOpen APIWebhookApplication servercomparisonScripting |
| Client-sideBrowser APIsC NPAPILiveConnectXPConnectC NPRuntimeC PPAPINaClActiveXBHOXBAPWeb APIsWHATWGAudioCanvasDOMSSEVideoWebSocketsWeb messagingWeb storageWeb workerXMLHttpRequestW3CDOM eventsEMEFileGeolocationIndexedDBMSESVGWebAssemblyWebAuthnWebGPUWebRTCWebXRKhronosWebCLWebGLOthersGearsWeb SQL Database(formerly W3C)WebUSBTopicsAjaxandRemote scriptingvs.DHTMLBrowser extensionCross-site scriptingandCORSHydrationMashupPersistent dataWeb IDLScripting | Client-side | Browser APIs | C NPAPILiveConnectXPConnectC NPRuntimeC PPAPINaClActiveXBHOXBAP | Web APIs | WHATWGAudioCanvasDOMSSEVideoWebSocketsWeb messagingWeb storageWeb workerXMLHttpRequestW3CDOM eventsEMEFileGeolocationIndexedDBMSESVGWebAssemblyWebAuthnWebGPUWebRTCWebXRKhronosWebCLWebGLOthersGearsWeb SQL Database(formerly W3C)WebUSB | WHATWG | AudioCanvasDOMSSEVideoWebSocketsWeb messagingWeb storageWeb workerXMLHttpRequest | W3C | DOM eventsEMEFileGeolocationIndexedDBMSESVGWebAssemblyWebAuthnWebGPUWebRTCWebXR | Khronos | WebCLWebGL | Others | GearsWeb SQL Database(formerly W3C)WebUSB | Topics | AjaxandRemote scriptingvs.DHTMLBrowser extensionCross-site scriptingandCORSHydrationMashupPersistent dataWeb IDLScripting |
| Client-side |
| Browser APIs | C NPAPILiveConnectXPConnectC NPRuntimeC PPAPINaClActiveXBHOXBAP |
| Web APIs | WHATWGAudioCanvasDOMSSEVideoWebSocketsWeb messagingWeb storageWeb workerXMLHttpRequestW3CDOM eventsEMEFileGeolocationIndexedDBMSESVGWebAssemblyWebAuthnWebGPUWebRTCWebXRKhronosWebCLWebGLOthersGearsWeb SQL Database(formerly W3C)WebUSB | WHATWG | AudioCanvasDOMSSEVideoWebSocketsWeb messagingWeb storageWeb workerXMLHttpRequest | W3C | DOM eventsEMEFileGeolocationIndexedDBMSESVGWebAssemblyWebAuthnWebGPUWebRTCWebXR | Khronos | WebCLWebGL | Others | GearsWeb SQL Database(formerly W3C)WebUSB |
| WHATWG | AudioCanvasDOMSSEVideoWebSocketsWeb messagingWeb storageWeb workerXMLHttpRequest |
| W3C | DOM eventsEMEFileGeolocationIndexedDBMSESVGWebAssemblyWebAuthnWebGPUWebRTCWebXR |
| Khronos | WebCLWebGL |
| Others | GearsWeb SQL Database(formerly W3C)WebUSB |
| Topics | AjaxandRemote scriptingvs.DHTMLBrowser extensionCross-site scriptingandCORSHydrationMashupPersistent dataWeb IDLScripting |
| Related topicsFrontend and backendMicroservicesRESTGraphQLPush technologySolution stackWeb pageStaticDynamicWeb standardsWeb API securityWeb applicationRichSingle-pageProgressiveWeb framework | Related topics | Frontend and backendMicroservicesRESTGraphQLPush technologySolution stackWeb pageStaticDynamicWeb standardsWeb API securityWeb applicationRichSingle-pageProgressiveWeb framework |
| Related topics |
| Frontend and backendMicroservicesRESTGraphQLPush technologySolution stackWeb pageStaticDynamicWeb standardsWeb API securityWeb applicationRichSingle-pageProgressiveWeb framework |

 
| vteWeb syndication |
| --- |
| HistoryBloggingPodcastingVloggingWeb syndication technology |
| Types | ArtBloggernacleClassical musicCorporateDream diaryEdublogElectronic journalFakeFamilyFashionFoodHealthLawLifelogMP3NewsPhotoblogPolicePoliticalProjectReverseTravelWarblog | ArtBloggernacleClassical musicCorporateDream diaryEdublogElectronic journalFakeFamilyFashionFoodHealthLawLifelogMP3NewsPhotoblogPolicePoliticalProjectReverseTravelWarblog |
| ArtBloggernacleClassical musicCorporateDream diaryEdublogElectronic journalFakeFamilyFashionFoodHealthLawLifelogMP3NewsPhotoblogPolicePoliticalProjectReverseTravelWarblog |
| Technology | GeneralBitTorrentFeed URI schemeFeaturesLinkbackPermalinkPingPingbackRebloggingRefbackRollbackTrackbackMechanismThreadGeotaggingRSS enclosureSynchronizationMemeticsAtom feedData feedPhotofeedProduct feedRDF feedWeb feedRSSGeoRSSMRSSRSS TVSocialInter-process communicationMashupReferencingRSS editorRSS trackingStreaming mediaStandardOPMLRSS Advisory BoardUsenetWorld Wide WebXBELXOXO | General | BitTorrentFeed URI scheme | Features | LinkbackPermalinkPingPingbackRebloggingRefbackRollbackTrackback | Mechanism | ThreadGeotaggingRSS enclosureSynchronization | Memetics | Atom feedData feedPhotofeedProduct feedRDF feedWeb feed | RSS | GeoRSSMRSSRSS TV | Social | Inter-process communicationMashupReferencingRSS editorRSS trackingStreaming media | Standard | OPMLRSS Advisory BoardUsenetWorld Wide WebXBELXOXO |
| General | BitTorrentFeed URI scheme |
| Features | LinkbackPermalinkPingPingbackRebloggingRefbackRollbackTrackback |
| Mechanism | ThreadGeotaggingRSS enclosureSynchronization |
| Memetics | Atom feedData feedPhotofeedProduct feedRDF feedWeb feed |
| RSS | GeoRSSMRSSRSS TV |
| Social | Inter-process communicationMashupReferencingRSS editorRSS trackingStreaming media |
| Standard | OPMLRSS Advisory BoardUsenetWorld Wide WebXBELXOXO |
| Form | Audio podcastEnhanced podcastMobilecastNarrowcastingPeercastingScreencastSlidecastingVideocastWebcomicWebtoonWeb seriesAnonymous bloggingCollaborative blogColumnistInstant messagingLivebloggingMicroblogMobile bloggingSpam blogVideo bloggingMotovlogging | Audio podcastEnhanced podcastMobilecastNarrowcastingPeercastingScreencastSlidecastingVideocastWebcomicWebtoonWeb series | Anonymous bloggingCollaborative blogColumnistInstant messagingLivebloggingMicroblogMobile bloggingSpam blogVideo bloggingMotovlogging |
| Audio podcastEnhanced podcastMobilecastNarrowcastingPeercastingScreencastSlidecastingVideocastWebcomicWebtoonWeb series |
| Anonymous bloggingCollaborative blogColumnistInstant messagingLivebloggingMicroblogMobile bloggingSpam blogVideo bloggingMotovlogging |
| Media | Alternative mediaCarnivalsFictionJournalismCitizenDatabaseOnline diarySearch enginesSideblogSoftwareWeb directoryMicromediaAggregationNewsPollReviewSearchVideoAtomAtomPubBroadcatchingHashtagNewsML1G2Social communicationSocial softwareWeb SliceRelatedBlogosphereEscribitionistGlossary of bloggingPay per clickPosting styleSlashdot effectSpam in blogsUses of podcasting | Alternative media | CarnivalsFictionJournalismCitizenDatabaseOnline diarySearch enginesSideblogSoftwareWeb directory | Micromedia | AggregationNewsPollReviewSearchVideoAtomAtomPubBroadcatchingHashtagNewsML1G2Social communicationSocial softwareWeb Slice | Related | BlogosphereEscribitionistGlossary of bloggingPay per clickPosting styleSlashdot effectSpam in blogsUses of podcasting |
| Alternative media | CarnivalsFictionJournalismCitizenDatabaseOnline diarySearch enginesSideblogSoftwareWeb directory |
| Micromedia | AggregationNewsPollReviewSearchVideoAtomAtomPubBroadcatchingHashtagNewsML1G2Social communicationSocial softwareWeb Slice |
| Related | BlogosphereEscribitionistGlossary of bloggingPay per clickPosting styleSlashdot effectSpam in blogsUses of podcasting |

 
| Authority control databases |
| --- |
| International | GND |
| National | United StatesFranceBnF dataIsrael |
| Other | Yale LUX |