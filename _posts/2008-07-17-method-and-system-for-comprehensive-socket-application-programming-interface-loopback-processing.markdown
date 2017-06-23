---

title: Method and system for comprehensive socket application programming interface loopback processing
abstract: Methods and systems for comprehensive socket API loopback processing on a computing device. In an exemplary method and system, a socket API processes loopback calls without resort to a TCP/IP protocol stock or lower level systems (e.g. network drivers), reducing overhead requirements and processing burdens imposed on the TCP/IP stack and lower level systems and improving overall computing device performance.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08286197&OS=08286197&RS=08286197
owner: Sharp Laboratories of America, Inc.
number: 08286197
owner_city: Camas
owner_country: US
publication_date: 20080717
---
The present invention relates to loopback networking and more particularly to a loopback networking implementation that reduces computing device overhead and improves computing device performance.

The Internet Protocol IP defines a loopback networking function. Most IP version 4 IPv4 implementations use 127.0.0.1 as the loopback address while IP version 6 IPv6 implementations typically use 1 as the loopback address.

In the loopback function a network application running on a computing device can address and communicate internally with another process running on the computing device using the loopback address. One common use for the loopback function is internal testing for verification of a process s operability and design. For example on a computing device that has a web browser and a web server that hosts a website the website can be accessed by pointing the web browser at the Uniform Resource Locator URL http 127.0.0.1 and tested without exposing the website to an external network.

In current versions of network capable operating systems e.g. Windows vxWorks the loopback address is treated in many ways like an IP address of a remote host. The loopback address has an entry in the routing table and belongs to a valid subnet. When an application calls an internal process using the loopback address the socket application programming interface socket API e.g. Winsock for Windows sockLib for vxWorks passes the call to the Transmission Control Protocol IP TCP IP protocol stack of the operating system which consults the routing table to make a routing decision and then forwards the call to a virtual network device driver within the input output I O subsystem of the operating system en route to the internal process. The virtual network device driver performs additional loopback processing such as buffering data transmitted between the application and the internal process. The loopback function within these operating system architectures which invokes the TCP IP protocol stack and a low level virtual network device driver for loopback processing including routing buffering and housekeeping is thus very inefficient.

The present invention in a basic feature provides comprehensive socket API loopback processing. In accordance with the principles of the present invention loopback processing on a computing device is performed by a socket API without resort to a TCP IP protocol stack or lower level systems e.g. network drivers reducing overhead requirements and processing burdens imposed on the TCP IP stack and lower level systems and improving overall computing device performance.

In one aspect of the invention a network capable computing device comprises an application a socket API operatively coupled with the application and a TCP IP protocol stack operatively coupled with the socket API wherein the socket API receives a call from the application and selectively invokes the TCP IP protocol stack to process the call based on a determination by the socket API of whether the call is a loopback call.

In some embodiments the socket API processes the call without resort to the TCP IP protocol stack in response to determining that the call is a loopback call.

In some embodiments the socket API invokes the TCP IP protocol stack in response to determining that the call is a non loopback call.

In some embodiments processing of the call by the socket API comprises storing data received on the call in a data store of the socket API.

In some embodiments processing of the call by the socket API comprises retrieving data requested on the call from a data store of the socket API and transmitting the data to the application.

In some embodiments the determination comprises determining whether the call is associated with a loopback destination.

In some embodiments the determination comprises determining whether the call is addressed to a loopback address.

In another aspect of the invention a network capable computing device comprises an application a socket API operatively coupled with the application and a TCP IP protocol stack operatively coupled with the socket API wherein the socket API receives a loopback call from the application and processes the loopback call without resort to the TCP IP protocol stack.

In some embodiments the socket API receives a non loopback call from the application and invokes the TCP IP protocol stack to process the non loopback call.

In yet another aspect of the invention a method for loopback processing on a computing device having an application and a TCP IP protocol stack operatively coupled with a socket API comprises the steps of receiving by the socket API from the application a call determining by the socket API whether the call is a loopback call and selectively invoking by the socket API the TCP IP protocol stack to process the call based on an outcome of the determining step.

In some embodiments the socket API processes the call without resort to the TCP IP protocol stack in response to a determination that the call is a loopback call.

In some embodiments the socket API invokes the TCP IP protocol stack to process the call in response to a determination that the call is a non loopback call.

In some embodiments processing of the call by the socket API comprises storing data received on the call in a data store of the socket API.

In some embodiments processing of the call by the socket API comprises retrieving data requested on the call from a data store of the socket API and transmitting the data to the application.

In some embodiments the determining step comprises determining whether the call is associated with a loopback destination.

In some embodiments the determining step comprises determining whether the call is addressed to a loopback address.

These and other aspects of the invention will be better understood by reference to the following detailed description taken in conjunction with the drawings that are briefly described below. Of course the invention is defined by the appended claims.

User interface receives inputs from a user of computing device via one or more input devices and displays outputs to the user via one or more output devices. Output devices include a display such as a liquid crystal display LCD organic light emitting diode OLED display. Input devices include for example a finger or stylus operated touch screen a scroll wheel or ball a keypad and or voice command module.

Network interface is a wired or wireless communication interface for transmitting and receiving information to from other network capable devices over wired or wireless communication links. Network interface may be for example a wired Ethernet interface cellular network interface wireless Ethernet WiFi interface or Worldwide Interoperability for Microwave Access WiMAX interface.

Processor executes in software operations supported by computing device . Turning to the software elements of computing device that are executable by processor include an application a socket API a TCP IP protocol stack and a network device driver . Importantly socket API includes a loopback processor and a loopback data store . The software elements that are executable by processor are stored in memory which includes one or more random access memories RAM and one or more read only memories ROM . In some embodiments socket API TCP IP stack and network device driver are integral to an embedded operating system.

Application is a network oriented application such as a web browser that is capable of issuing loopback calls and non loopback calls. These calls may be initiated by a user on user interface or generated by application without user intervention.

Socket API is a network API that interfaces with application and TCP IP stack and enables application to communicate with loopback processes on computing device via the loopback function as well as with remote computing devices via conventional TCP connections. Socket API receives calls from application creates sockets that provide endpoints for the calls binds the sockets to destination addresses and removes the bindings and closes the sockets when they are no longer needed. Sockets may include one or more loopback sockets bound to a well known loopback destination address for example 127.0.0.1 and one or more conventional TCP sockets bound to non loopback destination addresses associated with remote computing devices.

Loopback processor is a software subsystem of socket API that enables computing device to support the loopback function without resort to TCP IP stack or other lower level systems e.g. network drivers . Loopback processor processes loopback calls from application that reference a loopback socket. Attendant to processing loopback calls loopback processor interfaces with called internal processes and may temporarily store in loopback data store data sourced by called internal processes en route to application as well as data sourced from application en route to called internal processes.

TCP IP stack is a protocol stack that interfaces with socket API and network device driver and enables application to communicate with remote computing devices via conventional TCP connections. TCP IP stack transmits appropriately formatted data between socket API and network device driver and provides TCP session and IP datagram services.

Network device driver is software that interfaces between TCP IP stack and network interface and enables application to communicate with remote computing devices via conventional TCP connections. Network device driver transmits appropriately formatted data between TCP IP stack and network interface and in some embodiments provides Media Access Control MAC and Logical Link Control LLC services.

Referring to in conjunction with a method for loopback processing on computing device is described and shown in some embodiments of the invention. Socket API receives a socket API call from application . In response to the socket API call socket API attempts to map the call to an existing socket . If a socket does not exist for the call socket API creates a socket and binds the socket to a destination address . Socket API proceeds to determine whether the identified socket is a loopback type socket . If the identified socket is a loopback type socket the call is processed on loopback processor of socket API without resort to TCP IP stack or other lower level systems e.g. network drivers . On the other hand if the identified socket is a non loopback socket e.g. a conventional TCP socket socket API forwards the call to TCP IP stack for additional processing . In some embodiments whenever a new socket is created and bound loopback processor is invoked to determine whether the socket is a loopback socket by checking whether the destination address is a loopback address and if a determination is made that a socket is a loopback socket loopback processor flags the socket so that subsequent calls received on the socket are easily identified for processing by loopback processor .

It will be appreciated by those of ordinary skill in the art that the invention can be embodied in other specific forms without departing from the spirit or essential character hereof. The present description is therefore considered in all respects to be illustrative and not restrictive. The scope of the invention is indicated by the appended claims and all changes that come with in the meaning and range of equivalents thereof are intended to be embraced therein.

