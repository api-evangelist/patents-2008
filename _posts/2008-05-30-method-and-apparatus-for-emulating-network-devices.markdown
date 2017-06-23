---

title: Method and apparatus for emulating network devices
abstract: Methods, apparatuses, data structures, and computer readable media are disclosed that represent network devices with encapsulated protocol stacks communicating via a common physical port. The encapsulated protocol stacks include variable combinations of a multiple encapsulation protocols.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08264972&OS=08264972&RS=08264972
owner: Spirent Communications, Inc.
number: 08264972
owner_city: Sunnyvale
owner_country: US
publication_date: 20080530
---
The application is related to U.S. patent application filed 30 May 2008 titled METHOD AND DEVICE USING TEST DATA STREAMS BOUND TO EMULATED DEVICES Ser. No. 12 130 944 and U.S. patent application filed 30 May 2008 titled REALTIME TEST RESULT PROMULGATION FROM NETWORK COMPONENT TEST DEVICE Ser. No. 12 130 963. The related applications are incorporated by reference.

The technology relates to scalable testing of complex networks and or complex network devices. Network test equipment to perform such useful scalable testing should emulate a large number and variety of network devices without artificial limits on the overall topology configuration and types of traffic.

Traffic types vary by supported network layer link layer and physical layer protocols such as Internet Protocol Generic Routing Encapsulation Ethernet Virtual Local Area Network 802.1q Multiprotocol Label Switching Point to Point Protocol over Ethernet Point to Point Protocol and Layer 2 Tunneling Protocol WiMAX Provider Backbone Bridge 802.1ah and Asynchronous Transfer Mode. Existing network test equipment places artificial limits on the types of emulated traffic in particular variable combinations of network layer link layer and physical layer protocols.

For example an earlier TestCenter product from Spirent Communications Inc. emulated only a limited number of fixed combinations of network layer link layer and physical layer protocols. These combinations were coded in such a way that the upper layers were aware of the lower layers and therefore fail to take advantage of layering abstraction. The expected improvements to such a product would preserve the already existing support for the limited number of fixed combinations of network layer link layer and physical layer protocols and gradually supplement this limited support with an additional number of fixed combinations of network layer link layer and physical layer protocols perhaps as technological progress resulted in new network layer link layer and physical layer protocols.

In another especially limited example Internet Protocol aliasing adds multiple Internet Protocol addresses to a network interface this example is especially limited because it covers only the single fixed combination of Internet Protocol and Ethernet.

Support for emulating an arbitrarily variable number of combinations of network layer link layer and physical layer protocols would be unexpected because of the significant investment sunk into already existing support for emulating the limited number of fixed combinations of network layer link layer and physical layer protocols and the collectively prohibitive cost of adding incremental support specific to emulating each and every possible combination of network layer link layer and physical layer protocols.

Methods apparatuses data structures and computer readable media are disclosed that represent network devices with encapsulated protocol stacks communicating via a common physical port. The encapsulated protocol stacks include variable combinations of multiple encapsulation protocols.

In some embodiments the physical port is any of Ethernet Packet over Synchronous optical networking Packet over Synchronous Digital Hierarchy Asynchronous Transfer Mode and WiMAX.

In some embodiments the encapsulated protocol stacks communicate with transport and higher layers via Internet Protocol supported sufficiently by an operating system without requiring third party code.

In some embodiments the encapsulated protocol stacks communicate with transport and higher layers via Linux PF PACKET packet interface.

In some embodiments encapsulation protocols of the plurality of encapsulated protocol stacks include at least one of Internet Protocol Generic Routing Encapsulation Ethernet Virtual Local Area Network 802.1q Multiprotocol Label Switching Point to Point Protocol over Ethernet Point to Point Protocol and Layer 2 Tunneling Protocol WiMAX Provider Backbone Bridge 802.1ah and Asynchronous Transfer Mode.

Many embodiments represent the plurality of encapsulated protocol stacks with a tree data structure. In some embodiments the tree data structure includes paths between a root node of the tree structure and leaf nodes of the tree data structure such that paths of the plurality of paths represent encapsulated protocol stacks of the plurality of network devices. Some embodiments have paths between a root node of the tree structure and leaf nodes of the tree data structure such that nodes along the paths represent encapsulation protocols of the encapsulated protocol stacks. In some embodiments nodes are associated with sets of values specific to packet processing of particular encapsulation protocols. In some embodiments identifying a particular node of the tree data structure has a computational cost on the order of a logarithm of a number of nodes of the tree data structure.

Many embodiments emulate the packet sending process of a network device. Some embodiments process the packet with an encapsulated protocol stack corresponding to the network device and send the packet via the physical port. Some embodiments create the packet with a payload part and an additional part having space sufficient to store encapsulated protocol data added by encapsulated protocol stack processing.

Many embodiments emulate the packet receiving process of a network device. Some embodiments receive a packet via the physical port and process the packet with an encapsulated protocol stack corresponding to the network device. Some embodiments identify the encapsulated protocol stack based on at least sets of values corresponding to the encapsulated protocol stack. The sets of values specific to packet processing of particular encapsulation protocols.

Many embodiments emulate the broadcast packet receiving process of a network device. Some embodiments receive either a broadcast packet or a multicast packet via the physical port process the packet with an encapsulated protocol stack corresponding to the network device such that the encapsulated protocol stack is in a broadcast domain. This includes identifying the broadcast domain of only a subset of the encapsulated protocol stacks and based on the broadcast domain decreasing processing of the packet with encapsulated protocol stacks outside of the broadcast domain.

Some embodiments store statistics based on packets processed by the plurality of encapsulated protocol stacks.

Some embodiments emulate network layer communication of the plurality of network devices with a socket Application Programming Interface.

Various methods apparatuses data structures and computer readable media are directed to the disclosed embodiments.

The VIF manages operations such as send a packet and receive a packet. The VIF is a small structure representing a single protocol layer maintained and organized in operating system kernel memory. Examples of protocol layers are Internet Protocol e.g. versions 4 and 6 Generic Routing Encapsulation Ethernet e.g. 10 MBit s 100 MBit s 1 Gbit s 10 Gbit s Virtual Local Area Network 802.1q Multiprotocol Label Switching Point to Point Protocol over Ethernet Point to Point Protocol and Layer 2 Tunneling Protocol e.g. versions 2 and 3 WiMAX Provider Backbone Bridge 802.1ah and Asynchronous Transfer Mode e.g. adaptation layers 1 5 .

The VIF has a protocol value specifying the protocol type. The VIF also has a set of values specific to the protocol type. An exemplary XML template listing such sets of values follows 

The tree data structure allocates one node per VIF. The root node of the tree is a special VIF representing the physical interface PHY such as a port for Ethernet or a port for Packet over SONET SDH. In this particular view as a result of tree operations the tree grows down as children nodes representing encapsulation protocols are added to emulate network devices that do not exist physically. The tree has a depth equivalent to that of the tallest encapsulated protocol stack.

The process of sending a packet from an emulated device begins at a leaf node of the tree and the process of receiving a packet at an emulated device begins at the root node of the tree. All children nodes of a particular node are unique to prevent ambiguity about the recipient emulated device. In one embodiment to ensure such uniqueness the protocol specific set of values associated with each child node is unique with respect to the protocol specific set of values associated with all other peer nodes. A simple embodiment just assigns a unique name.

At any given node the collection of child nodes has properties of a red black tree such that the node can have any number of children. Accordingly child lookup has efficient performance of O logn with n being the number of potentially consulted nodes in the lookup.

Shown are the business layer logic BLL and instrument layer logic IL of a test device communicating with a device under test DUT . The test device includes hardware and software that implement features described herein. The test device may include one or more of logic arrays memories analog circuits digital circuits software firmware and processors such as microprocessors field programmable gate arrays FPGAs application specific integrated circuits ASICs programmable logic devices PLDs and programmable logic arrays PLAs . The hardware may be found in the chassis card rack or integrated unit. It may include or operate with the console or the general purpose computer in communication with the test device. The test device may include a number of separate units that are clustered together as shown in or remote from one another. For some levels of testing and some components of an overall test setup the test control may be implemented on a computer such as a personal computer server or workstation.

Typically the BLL has been hosted on a laptop or PC and provided a user interface and control for a test chassis that included both general purpose CPUs and FPGAs. The FPGAs have been dynamically configured to optimize test packet generation. Some combination of hardware supports the BLL and IL logic.

The IL logic depicts an operating system view divided into kernel space and user space. An exemplary division reserves kernel space for operating system kernel kernel extensions and some device drivers and permits user mode applications to reside in user space.

An ifsetup message sets up the interface and is shown in the figure sending requests from a protocol plug in in BLL to a VIF library in user space which in turn makes ioct1 system calls to a dynamically loaded VIF kernel module in kernel space.

The kernel module creates the tree data structure as discussed in shown with a VIF representing the physical port as the root node. Also as shown the kernel module does not have to create a net device at each layer and instead creates one net device e.g. eth00 . . . eth0 xxx at each leaf node which supports the BSD socket API and can take advantage of any built in command line utilities of the operating system. Because the kernel model sandwiches protocol specific VIFs the kernel model hides complexity of the encapsulated protocols from the OS and upper layer utilities in the IL and BLL.

The operating system is non limiting and can be e.g. embedded Linux other Unix derivatives such as BSD VxWorks IOS by Cisco etc.

The process of sending a packet is described as follows. In the IL the data to be sent is generated by a protocol daemon. The socket API communicates the data to be sent to kernel space. Then within kernel space the socket abstraction one of the protocol stacks IP protocol stacks PF INET or PF INET packet driver PF PACKET sends a partially built packet from the emulated device. As the partially built packet is processed by each encapsulated protocol of the emulated device protocols headers are added until the packet is complete and ready to send via the physical port.

Some embodiments create partly formed packets with sufficient headroom to store additional header data added by each subsequent encapsulated protocol to prevent wasteful copying and reallocating of memory.

Some embodiments allow the MPLS encapsulated protocol PPPoE encapsulated protocol and the Ethernet encapsulated protocol to determine and communicate the destination address of a peer.

The process of receiving a packet follows oppositely ordered iterative steps of the sending process. However the receive process has the ambiguity about how a parent node determines which of multiple children nodes is an immediate destination following any processing by the parent node. This ambiguity is resolved by the VIF kernel module with the unique node data discussed in connection with . The particular encapsulated protocol of a candidate child node extracts key fields from the packet. If comparison between key fields of the received packet matches the unique data of a child node the encapsulated protocol continues processing such as validating the packet and removing header data corresponding to that encapsulated protocol. However if the match process fails then the packet is discarded.

Broadcast multicast packets are treated specially to prevent the prohibitive expense of repeated processing of the same packet by a large number of emulated devices.

In one mechanism a special case handler determines the broadcast domain of the packet and sends copies of the packet to only nodes that belong to that broadcast domain.

In another mechanism for Ethernet VLAN 802.1q a hash is consulted which was developed to determine whether any leaf nodes in the tree belong to the same broadcast domain. This hash prevents traversal of the entire tree.

1 Broadcast IPv4 packet IPv4 broadcasts are received one time at the first VIF in a broadcast domain.

3 Unicast IPv4 packet IPv4 unicasts are received by only the VIF with that address. Besides eliminating non broadcast domain packets this eliminates other leaf VIFs without that IP address.

ARP Address Resolution Protocol has a special rule as well. An ARP broadcast is received only at VIFs with matching IP addresses.

Some operating systems such as Linux allow the maintenance a net device multicast list. The multicast list may be consulted to eliminate VIFs outside that broadcast domain.

User interface input devices may include a keyboard pointing devices such as a mouse trackball touchpad or graphics tablet a scanner a touchscreen incorporated into the display audio input devices such as voice recognition systems microphones and other types of input devices. In general use of the term input device is intended to include all possible types of devices and ways to input information into computer system or onto computer network .

User interface output devices may include a display subsystem a printer a fax machine or non visual displays such as audio output devices. The display subsystem may include a cathode ray tube CRT a flat panel device such as a liquid crystal display LCD a projection device or some other mechanism for creating a visible image. The display subsystem may also provide non visual display such as via audio output devices. In general use of the term output device is intended to include all possible types of devices and ways to output information from computer system to the user or to another machine or computer system.

Storage subsystem stores the basic programming and data constructs that provide the functionality of certain embodiments. For example the various modules implementing the functionality of certain embodiments may be stored in storage subsystem . These software modules are generally executed by processor .

Memory subsystem typically includes a number of memories including a main random access memory RAM for storage of instructions and data during program execution and a read only memory ROM in which fixed instructions are stored. File storage subsystem provides persistent storage for program and data files and may include a hard disk drive a floppy disk drive along with associated removable media a CD ROM drive an optical drive or removable media cartridges. The databases and modules implementing the functionality of certain embodiments may be stored by file storage subsystem .

Bus subsystem provides a mechanism for letting the various components and subsystems of computer system communicate with each other as intended. Although bus subsystem is shown schematically as a single bus alternative embodiments of the bus subsystem may use multiple busses.

Computer readable medium can be a medium associated with file storage subsystem and or with network interface . The computer readable medium can be a hard disk a floppy disk a CD ROM an optical medium removable media cartridge or electromagnetic wave. The computer readable medium is shown storing program instructions performing the described technology.

Computer system itself can be of varying types including a personal computer a portable computer a workstation a computer terminal a network computer a television a mainframe or any other data processing system or user device. Due to the ever changing nature of computers and networks the description of computer system depicted in is intended only as a specific example for purposes of illustrating the preferred embodiments. Many other configurations of computer system are possible having more or less components than the computer system depicted in .

While the present invention is disclosed by reference to the preferred embodiments and examples detailed above it is to be understood that these examples are intended in an illustrative rather than in a limiting sense. It is contemplated that modifications and combinations will readily occur to those skilled in the art which modifications and combinations will be within the spirit of the invention and the scope of the following claims.

