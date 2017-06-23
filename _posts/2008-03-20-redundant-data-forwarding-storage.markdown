---

title: Redundant data forwarding storage
abstract: Methods and apparatus, including computer program products, for redundant data forwarding. A method includes, in two or more networks of interconnected computer system nodes, receiving a request from a source system in a first network to store data, directing the data to a first computer memory in a first network, directing a first copy of the data to a second computer memory in a second network, continuously forwarding the data from the first computer memory to other computer memories in the first network without storing on any physical storage device in the first network, and continuously forwarding the first copy of the data from the second computer memory to other computer memories in the second network without storing on any physical storage device in the second network.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08458285&OS=08458285&RS=08458285
owner: Post Dahl Co. Limited Liability Company
number: 08458285
owner_city: Dover
owner_country: US
publication_date: 20080320
---
At least some embodiments disclosed herein relate to data storage and more particularly to redundant data forwarding.

The volume of data that must be stored by individuals organizations businesses and government is growing every year. In addition to just keeping up with demand organizations face other storage challenges. With the move to on line real time business and government critical data must be protected from loss or inaccessibility due to software or hardware failure. Today many storage products do not provide complete failure protection and expose users to the risk of data loss or unavailability. For example many storage solutions on the market today offer protection against some failure modes such as processor failure but not against others such as disk drive failure. Many organizations are exposed to the risk of data loss or data unavailability due to component failure in their data storage system.

The data storage market is typically divided into two major segments i.e. Direct Attached Storage DAS and Network Storage. DAS includes disks connected directly to a server.

Network Storage includes disks that are attached to a network rather than a specific server and can then be accessed and shared by other devices and applications on that network. Network Storage is typically divided into two segments i.e. Storage Area Networks SANs and Network Attached Storage NAS .

A SAN is a high speed special purpose network or subnetwork that interconnects different kinds of data storage devices with associated data servers on behalf of a larger network of users. Typically a SAN is part of the overall network of computing resources for an enterprise. A storage area network is usually clustered in close proximity to other computing resources but may also extend to remote locations for backup and archival storage using wide area WAN network carrier technologies.

NAS is hard disk storage that is set up with its own network address rather than being attached to the local computer that is serving applications to a network s workstation users. By removing storage access and its management from the local server both application programming and files can be served faster because they are not competing for the same processor resources. The NAS is attached to a local area network typically an Ethernet network and assigned an IP address. File requests are mapped by the main server to the NAS file server.

All of the above share one common feature that can be an Achilles tendon in more ways than one i.e. data is stored on a physical medium such as a disk drive CD drive and so forth.

The present invention provides methods and apparatus including computer program products for redundant data forwarding.

In general in one aspect the invention features a method including in two or more networks of interconnected computer system nodes receiving a request from a source system in a first network to store data directing the data to a first computer memory in a first network directing a first copy of the data to a second computer memory in a second network continuously forwarding the data from the first computer memory to other computer memories in the first network without storing on any physical storage device in the first network and continuously forwarding the first copy of the data from the second computer memory to other computer memories in the second network without storing on any physical storage device in the second network.

In another aspect the invention features a system including at least two networks wherein computer system nodes are each adapted to receive data and copies of data and continuously forward the data and copies of data from computer memory to computer memory without storing on any physical storage device in response to a request to store data from a requesting system.

The details of one or more implementations of the invention are set forth in the accompanying drawings and the description below. Further features aspects and advantages of the invention will become apparent from the description the drawings and the claims.

Unlike peer to peer networks which use data forwarding in a transient fashion so that data is eventually stored on a physical medium such as a disk drive the present invention is a continuous redundant data forwarding system i.e. data and copies of data are stored by continually forwarding it from one node memory to another node memory. Copies of data may continuously forwarded in one or more networks.

As shown in an exemplary system includes a user system and a number of network systems . Each of the network systems can be considered to be a node in the system and one such network system may be designated as a central server such as network system which may assume a control position in system . Each of the nodes may be established as a privately controlled network of peers under direct control of the central server . Peered nodes may also be a mix of private and public nodes and thus not under the direct physical control of the central server . The system may also be wholly public where the central server or servers has no direct ownership or direct physical control of any of the peered nodes.

In one example nodes and can be considered a private network. In a private network an administrator controls the nodes and may designate which node is the central server. The system can also include one or more additional nodes. For example nodes and . These nodes and may be considered to be part of one or more public networks in which the administrator has little or no control.

As shown in the user system can include a processor memory and input output I O device . Memory can include an operating system OS such as Linux Apple OS or Windows one or more application processes and a storage process explained in detail below. Application processes can include user productivity software such as OpenOffice or Microsoft Office. The I O device can include a graphical user interface GUI for display to a user .

As shown in each of the network systems such as network system can include a processor and memory . Memory can include an OS such as Linux Apple OS or Windows and a data forwarding process explained in detail below.

In traditional systems application processes need to store and retrieve data. In these traditional systems data is stored on local or remote physical devices and copies of data which are used to provide redundancy are stored locally or on remote physical storage devices such as disk drives. And in some systems this data can be segmented into different pieces or packets and stored locally or remotely on physical mediums of storage. Use of fixed physical data storage devices add cost maintenance management and generate a fixed physical record of the data whether or not that is the desire of the user .

The present invention does not use fixed physical data storage to store data and does not use physical data storage to provide data redundancy. When a request to store data is received by the central server from storage process data is directed to a node in the system where it is then continuously forwarded from node memory to node memory in the system by the data forwarding process in each of the network nodes without storing on any physical storage medium such as a disk drive. The request to store data makes at least one copy of the data which is directed to a node in a secondary private or public network or directed to nodes on more than one network where it too is continuously forwarded from node memory to node memory in the secondary private or public network. The forwarded data resides only for a very brief period of time in the memory of any one node in the system . Data and copies of data are not stored on any physical storage medium in any network node.

When a request to retrieve data is received by the central server from storage process the requested data which is being forwarded from node memory to node memory in the system is retrieved.

Data forwarded in this manner can be segmented and segments forwarded as described above. Sill the segmented data is not stored on any physical storage medium in any network node but merely forwarded from the memory of one node to the memory of another node.

As shown in storage process includes sending a request to a central server to store or retrieve data. If the request is a retrieve data request storage process receives the requested data from the central server or node in the network.

If the request to the central server is a store data request storage process receives first address of a node and a second address of a node from the central server and forwards the data to the node memory represented by the received first address and a copy of the data to the node memory represented by the received second address.

As shown in data forwarding process includes receiving a request from a source system in a first network to store data.

Process directs the data to the first computer memory in a first network and directs a first copy of the data to a second computer memory in a second network. Directing may be to node memories in one or more networks both private and or public.

Process continuously forwards the data from the first computer memory to other computer memories in the first network without storing on any physical storage device in the first network.

Continuously forwarding includes detecting a presence of the data in memory of the specific node of the first network and forwarding the data to another computer memory of a node in the first network of interconnected computer system nodes without storing any physical storage device.

Process continuously forwards the first copy of the data from the second computer memory to other computer memories in the second network without storing on any physical storage device in the second network.

Continuously forwarding includes detecting a presence of the first copy of data in memory of the specific node of the second network and forwarding the first copy of the data to another computer memory of a node in the second network of interconnected computer system nodes without storing any physical storage device.

In one specific example at the point of entry to a node data undergoes an encrypted handshake with the node or central server or user. This can be a public or private encryption system such as the Cashmere system which can use public private keys. Cashmere decouples the encrypted forwarding path and message payload which improves the performance as the source only needs to perform a single public key encryption on each message that uses the destination s unique public key. This has the benefit that only the true destination node will be able to decrypt the message payload and not every node in the corresponding relay group. Cashmere provides the capability that the destination can send anonymous reply messages without knowing the source s identity. This is done in a similar way where the source creates a reply path and encrypts it in a similar manner as the forwarding path.

New nodes and node states may be added and or deleted from the system based upon performance. Users may have access to all nodes or may be segmented to certain nodes or node states by the central server s or via the specific architecture of the private public or private public network.

Individual nodes nodes states and supernodes may also be extranet peers wireless network peers satellite peered nodes Wi Fi peered nodes broadband networks and so forth in public or private networks. Peered nodes or users may be used as routing participants in the system from any valid peer point with the same security systems employed as well as custom solutions suitable for the rigors of specific deployments such as wireless encryption schemes for wireless peers and so forth.

In process rather than have data cached or held in remote servers hard drives or other fixed storage medium the data and copies of data are passed routed forwarded from node memory to node memory. The data and copies of data are never downloaded until the authorized user calls for the data. A user on the system may authorize more than one user to have access to the data.

A primary goal in process is to generate a redundant data storage and management system where the redundant data is never fixed in physical storage but in fact is continually being routed forwarded from node memory to node memory. The path of the nodes to which redundant data is forwarded may also be altered by the central server to adjust for system capacities and to eliminate redundant paths of data that may weaken the security of the network due to the increased probability of data path without this feature.

The invention can be implemented to realize one or more of the following advantages. One or more networks create redundant data storage without caching or downloads. Redundant data storage and management are accomplished via a constant routing of the redundant data.

Embodiments of the invention can be implemented in digital electronic circuitry or in computer hardware firmware software or in combinations of them. Embodiments of the invention can be implemented as a computer program product i.e. a computer program tangibly embodied in an information carrier e.g. in a machine readable storage device or in a propagated signal for execution by or to control the operation of data processing apparatus e.g. a programmable processor a computer or multiple computers. A computer program can be written in any form of programming language including compiled or interpreted languages and it can be deployed in any form including as a stand alone program or as a module component subroutine or other unit suitable for use in a computing environment. A computer program can be deployed to be executed on one computer or on multiple computers at one site or distributed across multiple sites and interconnected by a communication network.

Method steps of embodiments of the invention can be performed by one or more programmable processors executing a computer program to perform functions of the invention by operating on input data and generating output. Method steps can also be performed by and apparatus of the invention can be implemented as special purpose logic circuitry e.g. an FPGA field programmable gate array or an ASIC application specific integrated circuit .

Processors suitable for the execution of a computer program include by way of example both general and special purpose microprocessors and any one or more processors of any kind of digital computer. Generally a processor will receive instructions and data from a read only memory or a random access memory or both. The essential elements of a computer are a processor for executing instructions and one or more memory devices for storing instructions and data. Generally a computer will also include or be operatively coupled to receive data from or transfer data to or both one or more mass storage devices for storing data e.g. magnetic magneto optical disks or optical disks. Information carriers suitable for embodying computer program instructions and data include all forms of non volatile memory including by way of example semiconductor memory devices e.g. EPROM EEPROM and flash memory devices magnetic disks e.g. internal hard disks or removable disks magneto optical disks and CD ROM and DVD ROM disks. The processor and the memory can be supplemented by or incorporated in special purpose logic circuitry.

It is to be understood that the foregoing description is intended to illustrate and not to limit the scope of the invention which is defined by the scope of the appended claims. Other embodiments are within the scope of the following claims.

