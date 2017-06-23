---

title: Access network node and method for access network node
abstract: A method for an access network node, and the access network node, to provide a user device access to a service enabled by an IMS network, comprising the steps of:


url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08270417&OS=08270417&RS=08270417
owner: Telefonaktiebolaget L M Ericsson (Publ)
number: 08270417
owner_city: Stockholm
owner_country: SE
publication_date: 20080604
---
The invention relates to an access network node and a method for the access network node to enable a user of a user device to gain access to IMS IP Multimedia Subsystem enabled services.

A multitude of different types of communication terminals or devices have been developed for packet based multimedia communication using IP Internet Protocol . Multimedia services typically involve transmission of media in different formats and combinations over IP networks. For example an IP enabled mobile terminal may exchange media such as visual and or audio information with another IP enabled terminal or may download media from a content server over the Internet.

A network architecture called IMS has been developed by 3GPP 3Generation Partnership Project as a platform for handling and controlling multimedia services and sessions commonly referred to as the IMS network. An IMS network can be deployed to initiate and control multimedia sessions for IMS enabled terminals connected to various access networks regardless of the access technology used. IMS allows rich person to person client to client as well as person to content client to server communications over an IP based network.

It is desirable to generally provide IMS based services for user devices in a limited local or private network such as a residential factory vehicle or office network also referred to as LAN Local Area Network or PAN Personal Area Network . In this description the generic term local network is used to represent any such networks and the term user device is used to represent any host end system capable of IP communication within and or outside a local network.

In order to provide IMS enabled services for non IMS enabled user devices in the local network a multimedia gateway has been suggested that can emulate an IMS terminal from the local network towards the IMS network to access IMS services on behalf of any device in the local network. Such a multimedia gateway has been described in e.g. WO 2007 071282 A1 in which it is referred to as a HiGA Home IMS Gateway . A drawback with the proposed HiGA is that CPE Customer Premises Equipment and CE Consumer Electronics vendors may be hesitant to incorporating IMS specific functionality in their devices to be sold to users of LAN s. The placement of an ISIM supporting IP Multimedia Services Identity Module card and the installation of IMS clients add to the overall cost and complexity of the devices that incorporates the HiGA. On the other hand the ability to deliver IMS multimedia services to local network devices is desired for an operator bearing upon business related to service delivery. So the general problem of gaining access to IMS services for non IMS user devices in a local network still remains if the local network is not provided with a HiGA.

It is thus an object of the invention to enable end users increased accessibility to services enabled by an IMS network.

Another object of the invention is to enable IMS enabled services to a non IMS enabled user device without placing heavy demand on the end user s local network s .

The invention relates to a method for an access network node to provide a user device access to a service enabled by an IMS network. The method comprises the steps of 

sending a registration request comprising an IMPU IP Multimedia Public Identity associated with the user device to an IMS network node for registration of the user device in the IMS network 

receiving a confirmation message from the IMS network node that the user device is authenticated for the service 

sending an authorization confirmation message via the IP tunnel to the user device that the user device is authorized for the service 

sending a service session initiation message to an AS application server associated with the service to start a service session between the user device and the AS.

The method may comprise the step of setting up the IP tunnel between the access network node and a local network node to which the access network node and the user device are connected.

In an embodiment of the method the IP tunnel is a VPN Virtual Private Network tunnel established between a UPnP RA Universal Plug and Play Remote Access server and a UPnP RA client.

In an embodiment of the method the authentication request the response the authorization confirmation message and the service request are be sent as API Application Programming Interface calls.

Another problem of gaining access to IMS services than the one mentioned above is when a user device is roaming outside of its associated local home network i.e. the network of a service provider with whom the user has an agreement. Today in order to access operator services in another operator s network a roaming agreement between the two operators must exist and there are many issues that need to be addressed by the operators before arriving at such a roaming agreement for IMS services 

security relationships between network and user device e.g. integrity protection security negotiation ciphering etc. and network to network e.g. network domain security inter system trust relationships etc. 

mutual authentication IMS level and above serving visited network home network user device serving network user device local network 

common charging model e.g. serving network needs to capture and provide to the local network all needed data items 

common SIP Session Initiation Protocol model e.g. use identical models SIP compression extensions use the same call flows etc. 

common QoS Quality of Service understanding for IMS sessions including authorization and common mapping of different classes 

consistent support for local services emergency calls geographic location services DTMF Dual tone Multi Frequency .

The above list of issues constitutes an obstacle for IMS operators to have roaming agreements. End users on the other hand would like to be able to access their services when outside of their operator s network.

The method may therefore in an embodiment comprise the step of setting up the IP tunnel directly between the access network node and the user device. Hereby is achieved that a user with Internet access that is remote from his local network is allowed to access IMS enabled services in a convenient way without having to take IMS roaming agreements into account.

In embodiments of the method the IP tunnel may be a Hypertext Transfer Protocol over Secure Socket Layer connection.

receiving the service request in the form of a UPnP message and translating the UPnP message to a Session Initiation Protocol message.

The method may in one embodiment comprise the step of receiving a connection request from the user device before the step of setting up an IP tunnel for communication with the user device.

The invention also relates to an access network node for providing a user device access to a service enabled by an IMS network. The access network node comprises 

send a registration request comprising an IMPU associated with the user device to an IMS network node for registration of the user device in the IMS network 

receive a confirmation message from the IMS network node that the user device is authenticated for the service sending an authorization confirmation message via the IP tunnel to the user device that the user device is authorized for the service 

send a service session initiation message to an AS associated with the service to start a service session between the user device and the AS.

The tunnel client may in one embodiment of the access network node be adapted to set up the IP tunnel between the access network node and a local network node to which the user device is connected.

The tunnel client may in one embodiment of the access network node be a UPnP RA client or UPnP RA server.

The tunnel client may in one embodiment of the access network node be adapted to set up the IP tunnel in such a way that it terminates in a first end in the access network node and in a second end in the user device.

The tunnel client may in one embodiment of the access network node adapted to set up a HTTPs Hypertext Transfer Protocol over Secure Socket Layer tunnel.

The access network node may comprise a protocol translation means for translating a message from the user device into a Session Initiation Protocol message to the IMS network node.

The user identification means may in one embodiment of the access network node comprise at least one software ISIM.

In one embodiment of the access network node the user identification means comprises at least one ISIM card.

The invention may also relate to a computer program to provide a user device access to a service enabled by the IMS network said computer program comprising code means which when run on the access network node causes the access network node to receive a connection request from the user device setting up an IP tunnel either directly with the user device or via a local network node to which the user device is connected for communication with the user device sending an authentication request to the user device via the IP tunnel receiving a response to the authentication request from the user device via the IP tunnel authenticating the user device for communication with the access network node based on the response sending a registration request comprising an IMPU associated with the user of the user device to an IMS network node e.g. a CSCF for registration of the user in the IMS network receiving a confirmation message from the IMS network node that the user device is authenticated for the service sending a message via the IP tunnel to the user device that the user device is authorized for the service receiving a request message via the IP tunnel from the user device to start the service and sending a service session initiation message to the AS associated with the service to start a service session between the user device and the AS.

Another aspect of the invention may be a computer program product comprising a computer readable means and the computer program wherein the computer program is stored on the computer readable means. The computer readable means may be a memory in the form of e.g. any non volatile memory such as a ROM Read only Memory an EPROM Erasable Programmable ROM an EEPROM Electrically Erasable Programmable ROM a flash memory a hard disk a DVD a CD etc.

a tunnel client server for setting up an IP tunnel for communication with the access network node and

receive an authentication request from the access network node to the user device via the IP tunnel and forwarding the authentication request to the user device 

receive a response to the authentication request from the user device and forwarding the response to the access network node over the IP tunnel 

receive an authorization confirmation message via the IP tunnel to the user device that the user device is authorized for the service and forwarding the authorization confirmation message to the user device 

receive a service request from the user device and forward the service request via the IP tunnel to the access network node.

The local network node may comprise a UPnP interface towards the user device and an API towards the access network node in order to expose a set of UPnP services and enable access of IMS services over a UPnP protocol stack.

an IMS service gateway control point which adapts the user device to set up and manage media sessions between the user device and an access network node or a local network node having a UPnP ISG UPnP IMS service gateway the IMS service gateway control point also adapting the user device to be able to use the IP address of the access network node to send a connection request via the local network node to the access network node discover the UPnP IMS service gateway receive an authentication request from the access network node via the local network node send a response to the authentication request to the access network node via the local network node receive an authorization confirmation message from the access network node via the local network node that the user device is authorized for the service and send a service request to the access network node via the local network node.

The invention may also relate to a method for providing a user of a user device access to a service enabled by an IMS network comprising the steps of 

sending a connection request from the user device to an access network node either directly from the user device or via a local network node to which the user device is connected 

setting up an IP tunnel between the access network node and either the user device or the local network node 

sending a response to the authentication request from the user device to the access network node via the IP tunnel 

sending a registration request comprising an IP Multimedia Public Identity associated with the user device to an IMS network node e.g. a CSCF Call Session Control Function from the access network node for registration of the user in the IMS network 

sending a confirmation message to the access network node from the IMS network node that the user device is authenticated for the service 

sending an authorization confirmation message from the access network node via the IP tunnel to the user device that the user device is authorized for the service 

sending a service request from the user device to the access network node via the IP tunnel to start the service 

sending a service session initiation message from the access network node to an AS associated with the service to start a service session between the user device and the AS.

The first local network comprises a first local network node here in the form of an RGW Residential Gateway enabling communication with a first access network node of the access network and the second local network comprises a second local network node enabling communication with a second access network node of the access network .

The Access Network is coupled to a service network and it may also be connected to the Internet . The Service Network is in this embodiment an IMS Network .

The IMS network includes an IMS network node comprising a CSCF server which provides session control for subscribers accessing services within an IP Multimedia network. The CSCF server comprises a SIP Server having responsibility for interacting with the access network . The CSCF server may also have responsibility for interacting with an AAA server Access Authorization and Accounting Server for security and with an AS either directly or via a protocol conversion gateway such as an IM SSF IP Multimedia Switching Function in the case of e.g. a CAMEL Customised Applications for Mobile network Enhanced Logic AS.

The local network nodes and enable communication between the local networks and and the access networks nodes and respectively. The functionality allowing a non IMS enabled device in one of the local networks to receive services from the IMS network here resides in the access network . The functionality hence works as an access network based IMS enabling proxy and therefore this functionality will hereinafter be referred to as Access Network IMS proxy or simply ANIP. However the functionality may in alternative embodiments be comprised in a node in an IMS core network.

The first local network may comprise a LAN according to any type of Ethernet IEEE 802.11 and IEEE 802.16 adapted to provide communication between the first local network node and one or several communications devices . The first local network may also allow communication between the individual communications devices using a local area local networking protocol P. Likewise the communication between a user device and the first local network node uses the local networking protocol P. According to an aspect of the invention the local networking protocol P includes communication based on the UPnP Universal Plug and Play architecture.

UPnP is an architecture developed in a multi vendor collaboration called the UPnP Forum for establishing standardized device protocols for the communication between different IP devices in a local network using different access technologies operating systems programming languages format standards and communication protocols. UPnP further provides standardized methods to describe and exchange device profiles that may include capabilities requirements and available services in the devices. When UPnP is used in a local network such as the first local network all UPnP enabled user devices are connected to the same IP sub net and can discover each other.

The UPnP defines devices these are software modules which can be seen as profiles describing the interaction between physical devices that host the UPnP devices. UPnP specifies several profiles that an ISG IMS Service Gateway relies on namely the AV Audio video profile and IGD internet gateway profile. The AV profile specifies how to set up a media session between an MR media renderer device and an MS media server device based on the 2 box or 3 box model. The box models specify if a UPnP CP Control Point resides within the MR 2 box or if it s external to both MR and MS 3 box . The IGD profile among other things specifies the interaction between a CP and an RGW needed for creating NAT Network Address Translation bindings.

According to another aspect of the invention the local networking protocol P includes communication based on Bonjour. Other alternative protocols that may be used for embodying the local networking protocol P include OSGi Jini Zero Configuration Networking Dynamic Host Configuration Protocol and WS Discovery Web Services Dynamic Discovery .

The user devices may include a telephone D a laptop computer D media server D television box not illustrated which may be referred to as a STB and or a media player not illustrated . There may be a plurality N of devices within the first local network where N is a positive integer.

The user devices D N may be a combination of IMS devices and non IMS enabled devices. Furthermore any non IMS enabled device may or may not be a SIP device. Examples of non IMS but SIP enabled terminals are SIP telephones and PCs whilst examples of non IMS terminals that do not have SIP functionality are legacy telephones including DECT Digital Enhanced Cordless Telecommunications telephones and IP devices with UPnP support such as STBs.

The first memory section comprises a communication start up program as well as a tunnel client which also can be termed as a tunnel server in a client server communication description model . The communication start up program includes a function for receiving a request for a service from one of the user devices comprised in the first local network . When a user device sends a request for a service that request may be received on a port of the first local network node and upon detecting that request the processor will cause the relevant program function in the first memory section to be executed. The reception of the service request will cause the communication start up program to initiate a procedure for establishing secure communication with the IMS network. The procedure for establishing secure communication includes the setting up of the secure tunnel between the first local network node and the first access network node with which it is associated. The setting up and the maintenance of the secure tunnel is performed by executing the tunnel client . A corresponding tunnel client and or server is comprised in the first access network node

The tunnel client will effectively set up the secure tunnel so that an end point of the secure tunnel will be at a local network node tunnel termination point in the first local network node . Secure tunnel communication enabling encrypted packet traffic to be securely communicated between different networks or between a host and a network or between different hosts is well known to a person skilled in the art and need not to be further described herein. The secure tunnel may be set up using different techniques which techniques will be further discusses below with reference to different embodiments of the invention. The encryption of the data run via the secure tunnel can be performed using any known technique such as IPsec IP Security which is a mandatory part of IPv6 and optional for use also with IPv4 Internet Protocol version 4 and implemented by a set of cryptographic protocols for securing packet flows mutual authentication and establishing cryptographic parameters. Thus a secure communication will pass via a first broad band port at the physical location where the first local network is installed. Hence whereas the actual exchange of digital data runs over the broad band port there is in a functional sense a secure tunnel having the local network node tunnel termination point within the local network node

In the second memory section of the logical block there is stored an address . The address stored in the first local network node points at the individual network access node in the access network which is associated with the first local network node . It is to be understood that in a commercial implementation the access network may comprise a large number of access network nodes. This IP address is used to set up the secure tunnel . The address to a particular access network node may also be stored by the individual user device within the first local network

The first local network node may optionally comprise protocol translation means . The protocol translation means can be used to translate the data communicated within the LAN to which the user device belongs to another communication protocol before transmitting it to the first access network node . For example if the data communication within the LAN and received on the port of the first local network node conforms to a networking protocol other than UPnP e.g. Bonjour the first local network node may be arranged to translate the received communication before transmitting it to the first access network node of the access network .

Although the protocol translation means is depicted as a separate block it should be understood that the translation functionality may be implemented by means of computer program code stored in e.g. the first memory section which program code when executed by the processor somewhere in the first local network node can perform conversion between different communications protocols.

According to one embodiment of the invention all the functions of the first local network node are comprised in an RGW. Although the first local network node has been described above as a device comprising a processor and computer code for performing a number of functions it is to be understood that the execution of these and other functions may be distributed within the first local network . According to one embodiment of the invention the communication start up program is performed by a home server which receives the request from a device over the first local network and the setting up of the secure tunnel may be performed by the RGW. In this distributed embodiment of the invention there may be one processor in the home server and a different processor in the RGW. It should thus be understood that the first and second memory sections and illustrated as parts of the logical block as well as the processor and protocol translation means may be distributed amongst various physical nodes devices in the first local network and that the first local network node should not necessarily be considered as a physical device but as a concept for facilitating description of certain functionality residing in the first local network

The first access network node comprises a first communications interface in the form of a second broad band port in communication with an access network tunnel termination point . The access network tunnel termination point is connected via the secure tunnel to the local network node tunnel termination point in the first local network node . The address in an address memory section of the first local network node will be the IP address to the access network tunnel termination point . For the purpose of illustration an address field carrying the IP address A of the access network tunnel termination point is depicted in the drawing. As should be understood by a person skilled in the art the access network tunnel termination point may be implemented in an IP tunnel client being a part of a computer program which when run by a processor in the first access network node causes the access network node to set up the secure tunnel and the access network tunnel termination point .

A data bus may connect the second broad band port for connecting it to the access network tunnel termination point . Accordingly when in operation the communication on the databus will be embedded as secure tunnel communication. Such secure communication will be passed via the second broad band port at a physical location of the access network in which the first access network node is located. Hence whereas the actual exchange of digital data between the first local network node and the first access network node runs over the first and second broad band ports it runs in a functional sense over the secure tunnel having a tunnel termination point at each node.

The access network tunnel termination point includes functionality for decrypting the data received via the secure tunnel and deliver decrypted output data to a connection . Accordingly any message sent by a user device to the first local network node in the first local network will be delivered decrypted on the connection from the access network tunnel termination point .

The system is preferably set up so that the access network tunnel termination point is positioned inside a physically secure environment e.g. a physical security shell designed to prevent unauthorized people from being able to reach the communication as it leaves and enters the secure tunnel . Preferably the complete access network and the plurality of access network nodes comprised therein are confined within such a physically secure environment . However there may be parts of the access network that are placed outside of the physically secure environment .

ANIP functionality of the first access network node is represented by a box in and will for the sake of simplicity sometimes be referred to as if it was a physical entity or device throughout this description. It should however be appreciated that ANIP rather is to be interpreted as a logical module which may or may not be distributed among a plurality of devices in the first access network node

The ANIP is adapted to communicate at one hand with the first local network via the access network tunnel termination point and on the other hand with an IMS network via a second communications interface in the form of a second port which typically connects to a CSCF server of the IMS network e.g. the CSCF server .

The ANIP comprises an ANIP core which comprises functionality allowing non SIP data received from user devices or a communications device connected to the access network via the Internet to communicate with the SIP based IMS network. The ANIP core comprises protocol translation means and is adapted to receive the decrypted data outputted from the access network tunnel termination point whereupon the protocol translation means translates the data to conform to the SIP protocol so that it can be communicated to and interpreted by the IMS network. The ANIP core of the ANIP hence handles interoperability issues like conversion between SIP and non SIP protocols and thus works as what is sometimes referred to as a SIP gateway. The first access network node is thus arranged to receive encrypted data over a secure connection decrypt the received data and convert it to conform to the IMS SIP protocol and transmit SIP messages to the IMS network.

Optionally the ANIP core comprises protocol identification means . Although the data received by the first network access node on the second broad band port typically conform to non SIP protocols it may when originating from an IMS enabled user device be SIP data. The protocol identification means or functionality which typically is implemented as software identifies the communication protocol on which this data is based. If the received data is found to be SIP data the protocol identification means can inform the protocol translation means that no conversion to SIP is needed and hence make sure that the protocol translation process in the ANIP is bypassed. If on the other hand the data output by the access network tunnel termination point is recognized as non SIP data by the protocol identification means it makes sure that the data is run via the protocol translation means which then converts the data stream to SIP data before it is sent to the second port for further transmission to the IMS network. It should be appreciated that there are many ways in which the protocol identification means can indicate whether the received data need to be converted to SIP or not. For example the protocol identification means can be arranged to set a flag indicating whether the data output by the access network tunnel termination point is based on SIP or not and the protocol translation means or other means in the ANIP core can comprise means for identifying said flag. If the flag indicates that the data is non SIP data the protocol translation means converts it to SIP whilst if the flag indicates that the data already is encoded according to the SIP protocol it is forwarded to the second port as is.

Protocol identification functionality such as the protocol identification means may also be included in the optional protocol translation means of the local network node for identifying whether the data received on the port already conforms to the communication protocol that is desired to use for the communication with the access network node

Furthermore the ANIP comprises user identification means . The user identification means serves to identify the user subscriber requesting an IMS service.

The user identification means may be implemented as software ISIM soft ISIM . In such a case the user identification means typically comprises a database storing service subscriber keys IMSIs International Mobile Subscriber Identity each associated with a user credential such as a PIN code linked to a user subscriber in the first local network as well as a SIM software component and processing means for running said component. When a service request is sent from a user device in the first local network the SIM software component is executed. The execution of the software component may involve the step of displaying an IMS login page on the user device screen over a GUI Graphical User Interface asking the user to input user credentials in this example the PIN code. The user credentials are then compared with the user credentials stored in the database and if a match is found the user is authorized to gain access to the ANIP .

The user identification means may also be implemented by means of ISIM cards. As well known in the art an ISIM card is actually an application running on a UICC Universal Integrated Circuit Card smart card. The ISIM holds files regarding a user s subscription level as well as authentication security information and their IMPI IMS private identity held in the form of a NAI Network Access Identifier .

The ANIP may comprise a plurality of such ISIM cards each associated with a user subscriber such as a user associated with the first local network . When the user request an IMS service or automatically when the user connects his user device to the network access control of the user is performed by the user identification means by verifying that the user identity corresponds to the private user identity contained on one of the ISIM cards in the ANIP . By storing ISIM cards associated with the different users user devices of the first local network in the first access network node instead of in each user device the overall cost and complexity of the user devices can be greatly reduced.

The user identification means of the ANIP prevents IMS subscription hijack by intruders who may have gained access to the first local network

Another layer of security could be user device authentication based on certificates. This would limit access to the ANIP to only authorized devices. Copper access security provided by the access network provider could serve as a third level of security. A restriction could be applied so that only devices in e.g. the first local network with a valid IMS subscription could have the permission to access the ANIP .

It should be understood that the functional steps performed by the different entities in the first local network node and the first access network node described above are reversible i.e. that communication between the user device in the first local network and the IMS network is bidirectional. So for example is the ANIP arranged to receive SIP data from the second port and by means of the protocol translation means convert it to conform to a desired non SIP communications protocol which is interpretable by the first local network . The access network tunnel termination point is arranged to encrypt the non SIP data and transmit it via the secure tunnel to the local network node tunnel termination point which in turn decrypts it and passes it on to the user device that has demanded the IMS service.

The first access network node described above allows for a non IMS enabled user device in the first local network to access IMS services. This is achieved by means of the ANIP which acts as a proxy between user devices in the first local network and IMS enabled services.

One major advantage achieved by the ANIP is that contrary to the case when all IMS enabling functionality resides in a local network the ANIP can be used to not only act as a proxy between user devices in the local network and the IMS but also as a proxy between user devices being remote from their local network and the IMS. As will be described in more detail below with reference to this is achieved by establishing a secure connection from the remote user device to the ANIP over e.g. the GPRS General Packet Radio Services WiMAX or HSPA High Speed Packet Access or LTE Long Term Evolution network. This remote IMS access solution is applicable not only to mobile user devices but also fixed devices connected to the Internet without being a part of the first local network

The first access network node comprising an ANIP thus provides an alternative access to IMS services and it does not require any roaming agreements between IMS operators. By creating a secure connection to the ANIP over the GPRS or HSPA network a user e.g. communications device in being remote from his local network can access the IMS services provided by his home IMS operator. The invention thus allows for a travelling user to remotely from his local network access the IMS network in a convenient way. Since no operator roaming agreements are needed the user can also utilize the services to a potentially substantially lower cost. It should however be understood that the proposed ANIP solution for remote IMS access would require that the user device has Internet access and the ability to create a secure connection to the ANIP which can be done over e.g. a GPRS HSPA WiMAX or LTE network.

Another problem solved by the ANIP is that today in order for a user device in a local network to address IMS services data must be converted to and from SIP in the actual user device or at least in some node device in the local network through which user data is communicated to the access network. By providing the ANIP which allows data conversion to take place in the access network the cost associated with providing IMS services to end users is shifted from manufacturers of user near end user equipment to access network operators. This is advantageous in that network operators may be more willing to take the cost associated with implementing IMS enabling functionality for non IMS enabled devices since they should be able to have a good return on investment as end users connects to the access network to utilize the various IMS services.

Another obvious advantage achieved by the ANIP solution is that user near end user equipment can be made less complex and smaller in size as it does not need to incorporate all functionality required to access IMS services. Furthermore regarding the user identification means in the ANIP implemented as software and soft ISIM the advantages with a soft ISIM instead of costly hardware UICC s can be utilized in a safer way by the access operators since a soft ISIM in a local network node probably would be more exposed to illegal tampering.

Now turning to three embodiments of the communications network system according to the invention will be described in more detail.

In the user device is a DLNA Digital Living Network Alliance compatible device or any other device comprising an ISG CP IMS Service Gateway Control Point and a UPnP MR with a UI User Interface . Alternatively the ISG CP could be in the first home node not shown .

An ISG CP is a logical module that is a part of the UPnP ISG architecture which will be further described below. The ISG CP is a UPnP entity having a UPnP AV architecture that specifies that the CP features are manufactured dependent on the controlled UPnP device. The CP is designed to set up and manage media sessions between a UPnP ISG which also will be described in more detail below and the user device in which the CP is located. It should be understood that ISG CP should be interpreted as a logical module rather than a hardware device.

A UPnP MR is also a logical module in the UPnP ISG architecture and is a standard UPnP media renderer capable of rendering HTTP HyperText Transfer Protocol or RTP Real time Transport Protocol data.

The DLNA enabled device is a consumer electronics media device and may be e.g. a TV telephone that advantageously has an IP interface a PC e.g. a lap top a PDA media module game console home theatre receiver disc player or the like.

In this embodiment of the invention the UPnP remote access architecture is used for the connection between the local network node and the access network node . UPnP remote access architecture is as such known to a person skilled in the art and is defined by the UPnP Forum for providing a mechanism that allows generic UPnP devices services and control points deployed in remote physical devices to interact with the corresponding UPnP devices services and control points physically attached to the local network. The mechanisms defined in the architecture will allow to extend the local network so that it will logically include the remote devices and thereby all devices will be able to communicate among themselves using various UPnP mechanisms. The desired behaviour of the interactions between the remote device and home devices is to be similar with the one expected as if all devices are located in the same local area network. In order to accommodate the above mentioned goals the UPnP RA architecture provides means to connect the two segments of the extended local network using established mechanisms. Remote access architecture undertakes the provisions needed in order to minimize the adverse effects of the internal and external factors and bring the remote user experience as close as possible to the one available in the local area network. Use of UPnP RA is however new to a person skilled in the art in the way it is used in this embodiment.

In this embodiment of the invention the local network node which could be the first local network node comprises a local network node UPnP remote access agent H RA . The H RA is responsible for setting up and maintaining the secure tunnel to the access network node which could be the first access network node . When doing so the H RA makes use of the address stored in the local network node tunnel termination point and pointing at the access network node tunnel termination point . The secure tunnel is in this embodiment hence established by means of an UPnP RA connection.

The access network node comprises a corresponding access network node UPnP remote access agent A RA which in a way similar to that of the H RA in the local network node serves to establish and maintain the secure tunnel between the tunnel termination points and of the home and access network node respectively.

As previously mentioned the communication between the various devices and between one of the devices and the local network node of the first local network is based on a local networking protocol P which may be any of a plurality of suitable communication protocols. This applies also to this first embodiment. However since the data transmitted over the RA connection is UPnP data the local network node comprises the protocol translation means if the internal communication within the local network conforms to a networking protocol P other than UPnP e.g. the Bonjour protocol. In such a case the protocol translation means serves to convert the non UPnP data received from a user device via the port to UPnP data. As described above the local network node tunnel termination point then typically encrypts the UPnP data and transmits it to the access network node over the secure tunnel .

The encrypted UPnP data is decrypted at the access network tunnel termination point and passed on decrypted to the ANIP via the connection . The UPnP interface of the ANIP is implemented by a UPnP ISG .

The UPnP ISG is a UPnP based logical module that exposes a set of UPnP services which enable access of IMS services over the UPnP protocol stack. The UPnP ISG serves as an intermediate entity between UPnP and the ANIP core and has two interfaces a UPnP interface and an interface to the ANIP core via an API . The UPnP interface is a set of services and corresponding actions that the UPnP ISG advertises to the first local network . The UPnP ISG ANIP core API enables media sessions to be established between IMS entities and UPnP entities. The API takes care of relying information regarding media formats and transport protocols used for establishing media sessions in UPnP and IMS SIP. Besides the UPnP ISG itself the UPnP ISG architecture typically comprises an ISG CP module a UPnP MR module and a UPnP MS module. The two first mentioned modules were briefly described above with reference to the DLNA devices . The last mentioned module UPnP MS serves in the context of the UPnP ISG architecture as an input device for user media data e.g. a UPnP camera microphone etc.

The ANIP allows the UPnP ISG to incorporate a minimum of ISG functionality. In a minimalistic implementation the UPnP ISG would be a modified UPnP CP that is able to set up a media session using the AV profile between a UPnP MR of a DNLA compatible user device in the first local network and the ANIP thus acting as an IMS media termination point. A minimalistic UPnP ISG would besides comprising functionality allowing media sessions to be established using UPnP AV also comprise functionality allowing the UPnP internet gateway IGD profile to be used to create relevant NAT bindings. Thus typically the UPnP ISG of the ANIP can be seen as a modified UPnP CP which supports the UPnP AV and UPnP IGD profiles and has an internal interface to the ANIP .

The access network node according to this embodiment thus comprises means such as the A RA and the access network tunnel termination point for receiving UPnP data over a secure RA connection from the first local network and means such as the ANIP comprising UPnP ISG and ANIP core functionality comprising at least protocol translation means for translating said UPnP data so that it conforms to the SIP protocol and transmitting it to an IMS network. Thereby the access network node allows for a non IMS user device to access IMS services provided by an IMS network by establishing an RA connection to the access network node .

The ISG CP of the user device is typically pre configured with the IP address of the A RA of the access network node . This allows for a user to connect to the A RA of his home access network node over e.g. a secure Internet connection which could be over a fixed or wireless medium e.g. DSL Digital Subscriber Line GPRS or HSPA even when being remote from his local network . Hence this embodiment is particularly good for giving access of IMS services to a non IMS user device even if it is outside of its local network provided that the user device supports UPnP remote access.

Although this embodiment translate to UPnP as data goes to and from the first network over the secure tunnel a person skilled in the art would appreciate from the description of the embodiment that there could be other analogous possible non UPnP solutions such as Bonjour that in the future could be provided with a remote access extension to a protocol with similar functions as UPnP RA. Such analogous non UPnP solutions could work in the same way as in this embodiment and there would then naturally not be necessary to translate to UPnP before data is sent over the secure tunnel e.g. if Bonjour is provided with remote access means. In such an analogous solution an ISG device corresponding to the UPnP ISG could be termed in this case for illustration purposes only a person skilled in the art would think of e.g. a ZeroConf ISG or Bonjour ISG devices based on the teaching of this embodiment. The local network node and the corresponding access nodes could in such analogous embodiments be provided with Bonjour remote access clients or Zero Conf remote access clients if such are developed.

An alternative implementation to UPnP RA i.e. embodiment A described above could be to have an ISG located in the local network node and use a proprietary protocol between the ISG and the ANIP in the access network node. According to this embodiment of the invention embodiment B only API calls are exchanged between the local network node and the access network node.

A local network node and an access network node according to this embodiment are illustrated in . The local network node and the access network node comprise a respective HTTP application and such as a HTTPs for establishing and maintaining a secure tunnel . That is the secure tunnel is in this embodiment set up as a secure HTTP connection using HTTPs. The HTTP application is here included in the ANIP core .

The local network node is further seen to comprise a UPnP ISG . In accordance with the UPnP ISG in embodiment A the UPnP SG serves as an intermediate entity between UPnP and the ANIP core only now the UPnP ISG is located in the local network node while the ANIP core still resides in the access network node . The API serving as an interface between the UPnP ISG and the ANIP core is hence in this embodiment an interface over the secure HTTP connection where API calls are responsible for ANIP function invocation which will be further described below in conjunction with .

The user devices in the local network comprise also in this embodiment an ISG CP and may of course include an MR and or an MS.

CEA 2014 defines a mechanism that allows user interfaces to be remotely displayed on and controlled by devices or CPs Control Points other than the one hosting the logic. CEA 2014 is composed of three distinct parts a UPnP based framework for locating and rendering user interface content on the local network a UPnP based home user interface server specification and a browser specification employing an XHTML Extensible HyperText Markup Language profile also referred to as CE HTML . CE HTML is constructed upon existing W3C standards including XHTML 1.0 CSS TV Cascading Style Sheets TV and ECMA 262 this standard defines a scripting language for browsers is also known as Javascript . It however goes beyond the W3C foundation in the detailed specification of browser behaviour designed to deliver optimum user experiences on common consumer electronics devices. Using existing web standards for UI content e.g. XHTML and supporting a variety of different consumer client devices STBs TVs mobile phones CEA 2014 allows for dynamic interaction between Remote UI Clients as well as provides timely partial UI updates from a Remote UI Server.

The Open IPTV Forum specifies a common and open end to end platform for supplying variety of internet multimedia and IPTV services to retail based CE either over QoS controlled managed network or over the public Internet. The Open IPTV forum specifies a so called ITF IMS termination function providing functionality which according to this embodiment of the invention also can be provided by the proposed ANIP solution. ITF consists of two main modules relevant to this application the piIPTV DLNA Application Gateway piIPTV DLNA AGw and IMS middleware. The piIPTV DLNA AGw performs the following functions 

The piIPTV DLNA Application Gateway also sets up media sessions on behalf of non SIP UPnP DLNA home devices.

The IMS UA registers with the IMS core using credentials stored on the ISIM. It can register multiple IMS public user identities associated with the ISIM in case it has multiple IPTV clients connected. The Home NAT Control Function will interface the IMS Middleware with any router with NAT functionality if placed between the local network and the delivery network. It will open and close ports for the unicast media streams according to the Internet Gateway Device specification defined by UPnP Forum. The GBA Client is the client which handles the key management in the ITF. More information regarding the GBA Client is found in 3GPP TS 33.220 Generic Authentication Architecture GAA Generic bootstrapping architecture .

Here the user device typically a TV with an STB comprises a CEA 2014 remote user interface UI client RUI C and a media renderer MR while the access network node comprises a CEA 2014 RUI S Remote UI server . The RUI C is responsible for setting up and maintaining a secure tunnel to the access network node over a broadband connection e.g. DSL HFC hybrid fiber coaxial cable HSPA GPRS WiFi WiMax etc. The secure tunnel is in this embodiment established by means of a secure SSL Secure Sockets Layer or TLS Transport Layer Security tunnel . Thereby the user device with help of the RUI C which can be termed as an enhanced browser application can communicate directly with the RUI S even if the user device is remote from the first local network provided that the address or FQDN Fully Qualified Domain Name of the RUI S is known to the user device .

IF B implements a translation function between ITF IMS functionality provided by the ANIP core and CEA 2014. Interface B performs session invocation requests to and from the ANIP core .

An application in is responsible for performing internal tasks in the server corresponding to notifications received from the event notification handlers. IF B would serve as a source of event notifications from the IMS core. These events could for example be a call notification event to be displayed on the user device when there is an incoming call to the ANIP or request for initiating a media session between the RUI S and RUI C . CEA 2014 defines the i box model in the document CEA 2014 Web based Protocol and Framework for Remote User Interface on UPnP Networks and the Internet Web4CE which supports the remote presentation and control of UIs that reside on a non discoverable remote server on the Internet. This paves a way for collocating the RUI S with the ANIP core in the access network .

In this case the ISG CP in the DLNA enabled user device is pre configured with the IP address of the A RA of the access network node i.e. the address . In a first step A a UPnP request message is transmitted from the ISG CP to discover the H RA and a respond message is sent back from the H RA .

In a second step A a message is sent from the ISG CP to the H RA comprising a request for connection to the ANIP .

In a third step A there is an exchange of UPnP messages between the H RA and the A RA setting up the RA connection forming the secure tunnel illustrated as a tunnel in .

In a fourth step A there is an exchange of UPnP messages between the ISG CP and the ANIP for discovering the UPnP ISG .

In a fifth step A there is an exchange of API commands between UPnP ISG and the ANIP core which serves to connect the UPnP ISG to the ANIP core .

In a sixth step A a request of the ISG UPnP is sent from the ANIP to the ISG CP for user authentication.

In a seventh step A a GUI request is sent from the ISG CP to the UPnP MR UI to display a login page on the user device .

In an eighth step A a GUI message is sent from the UPnP MR to the ISG CP comprising user credentials inputted by the user.

In a ninth step A an ISG UPnP login message is sent from the ISG CP to the ANIP comprising the input user credentials.

A tenth step A comprises an internal ANIP signalling process in which user authorization is verified based on the received user credentials and an IMPU is selected.

In an eleventh step A a SIP registration request sent from the ANIP to the CSCF server of the IMS network comprising the selected IMPU.

In a twelfth step A a verification of the registration request is sent from the CSCF server to the ANIP indicating that the identified user identified by the IMPU is authorized for IMS service subscription.

A thirteenth step A comprises the sending of an ISG UPnP login OK message from the ANIP to the ISG CP comprising a list of available IMS services.

In a fourteenth step A a GUI message is sent from the ISG CP to the UPnP MR for display of available IMS services on the UPnP MR UI of the user device .

In a fifteenth step A a selected service message is sent from the UPnP MR to the ISG CP comprising information on what service is requested by the user.

In a sixteenth step A an ISG UPnP start service request is sent from the ISG CP to the ANIP comprising information on what service to start based on the received selected service message A.

A seventeenth step A comprises an internal ANIP signalling process in which a PSI Public Service Identity of the selected service is inserted into SIP messages.

In an eighteenth step A a SIP invite message is sent from the ANIP to the AS in the form of a SAS Service Application Server the invite message comprising the PSI of the requested IMS service and inviting the SAS to start said service.

A nineteenth step A indicates service specific interactions between the UPnP MR of the user device and the SAS of the IMS network.

In a twentieth step A an ISG UPnP message is sent from the ISG CP to the ANIP indicating that the IMS service is terminated.

In a twenty first step A a RA teardown message is sent from the ANIP to the A RA initiating teardown of the RA session between the H RA and A RA .

A twenty second step A comprises an exchange of teardown messages between the A RA in the local network node and the H RA in the access network node which serves to teardown the secure tunnel and thereby terminating the IMS session.

In a first step B a UPnP request respond message is transmitted from the ISG CP to discover the ISG .

In a second step B a UPnP message is sent from the UPnP ISG to the HTTP application comprising a request for connection to the ANIP .

A third step B comprises an exchange of messages between the HTTP application of the local network node and the HTTP application of the access network node serving to establish a secure tunnel between the two which secure tunnel may be e.g. an HTTPs connection.

A fourth step B comprises an exchange of API commands between the UPnP ISG and the ANIP core which serves to connect the UPnP ISG to the ANIP core .

In a fifth step B an API command is sent from the ANIP core to the UPnP ISG requesting user authentication.

A sixth step B comprises sending of a UPnP ISG message from the UPnP ISG to the ISG CP forwarding the request for user authentication to the user device .

In a seventh step B a GUI request is sent from the ISG CP to the UPnP MR UI to display a login page on the user device .

In an eighth step B a GUI message is sent from the UPnP MR to the ISG CP comprising user credentials input by the user.

In a ninth step B a UPnP ISG message is sent from the ISG CP to the UPnP ISG comprising the input user credentials.

In a tenth step B an API command is sent from the UPnP ISG to the ANIP core comprising the user credentials.

An eleventh step B comprises an internal ANIP signalling process in which user authorization is verified based on the received user credentials and an IMPU is selected.

A twelfth step B comprises a SIP registration request sent from the ANIP to the CSCF server of the IMS network comprising the selected IMPU.

In a thirteenth step B a verification of the registration request is sent from the CSCF server to the ANIP core indicating that the identified user identified by the IMPU is authorized for IMS service subscription.

In a fourteenth step B a login OK API command message is sent from the ANIP core to the UPnP ISG indicating that the user is authorized for IMS service subscription and comprising a list of available IMS services.

In a fifteenth step B a UPnP ISG login OK message is forwarding the information contained in the login OK API command message from the UPnP ISG to the ISG CP .

In a sixteenth step B a GUI request message is sent from the ISG CP to the UPnP MR for display of available IMS services on the UPnP MR UI of the user device .

In a seventeenth step B a selected service message from the UPnP MR is sent to the ISG CP comprising information on what service is requested by the user.

In an eighteenth step B an UPnP ISG start service request is sent from the ISG CP to the UPnP ISG comprising information on what service to start based on the received selected service message of the seventeenth step A.

In a nineteenth step B an API command is sent from the UPnP ISG to the ANIP core comprising information on what service was chosen by the user and a request to start said service.

A twentieth step B comprises an internal ANIP signalling process in which the PSI of the selected service is inserted into SIP messages.

In a twenty first step B a SIP invite message is sent from the ANIP core to the AS here in the form of a SAS comprising the PSI of the requested IMS service and inviting the SAS to start said service.

A twenty second step B comprises service specific interactions between the user interface of the UPnP MR in the user device and the SAS of the IMS network.

In a twenty third step B a UPnP ISG message is sent from the ISG CP to the ISG indicating that the IMS service should be terminated.

In a twenty fourth step B an API command is sent from the ISG to the ANIP core forwarding the information that the IMS service is terminated.

In a twenty fifth step B a teardown message is sent from the ANIP core to the HTTP application on the access network side initiating teardown of the secure HTTP connection.

A twenty sixth step B comprises an exchange of teardown messages between the HTTP application residing in the ANIP of the access network node and the HTTP application residing in the local network node which serves to teardown the secure tunnel and thereby terminating the IMS session.

In this case the RUI C in the user device is pre configured with the IP address of the RUI S in the ANIP .

A first step C comprises a start message sent from the RUI C to the RUI S comprising a request for starting a UI session.

A second step C comprises an exchange of commands between the RUI S and the ANIP core which serves to connect the RUI S to the ANIP core .

A fourth step C comprises an exchange of messages between the RUI C of the user device and the RUI S of the ANIP in the access network node serving to establish the secure tunnel between the RUI C and RUI which secure tunnel may be set up using SSL or TLS and hence form e.g. a HTTPs connection.

A fifth step C is a user authentication request from the RUI S to the RUI C telling it to effect display of a login page on the GUI of the user device .

In a sixth step C a GUI request is sent from the RUI C to the MR UI for display of a login page on the user device .

In a seventh step C is a GUI message from the MR to the RUI C comprising user credentials input by the user.

An eighth step C comprises a login script message sent from the RUI C to the RUI S comprising the input user credentials and a request for executing a login script on the RUI S .

In a ninth step C a user authorization command is sent from the RUI S to the ANIP core comprising the user credentials.

A tenth step C comprises an internal ANIP signalling process in which user authorization is verified based on the received user credentials and an IMPU is selected.

In an eleventh step C a SIP registration request is sent from the ANIP to the CSCF server of the IMS network.

In a twelfth step C a verification of the registration request is sent from the CSCF server to the ANIP core indicating that the identified user is authorized for IMS service subscription.

In a thirteenth step C a login OK command message is sent from the ANIP core to the RUI S indicating that the user is authorized for IMS service subscription and comprising a list of available IMS services.

In a fourteenth step C a service scrip message is sent from the RUI S to the RUI C notifying the RUI C that login is OK and comprising a list of available IMS services.

In a fifteenth step C a GUI request message is sent from the RUI C to the MR for display of available IMS services on the MR UI of the user device .

In a sixteenth step C a selected service message is sent from the MR to the RUI C comprising information on what service is requested by the user.

In a seventeenth step C start service script message is sent from the RUI C to the RUI S comprising information on what service to start based on the received selected service message of the sixteenth step C.

In an eighteenth step C a command is sent from the RUI S to the ANIP core comprising information on what service was chosen by the user and a request to start said service.

A nineteenth step C comprises an internal ANIP signalling process in which the PSI of the selected service is inserted into SIP messages.

In a twentieth step C a SIP invite message is sent from the ANIP core to the AS in the form of a SAS comprising the PSI of the requested IMS service and inviting the SAS to start said service.

A twenty first step C indicates service specific interactions between the user interface of the MR in the user device and the SAS of the IMS network.

In a twenty second step C a service terminated script message is sent from the RUI C to the RUI S indicating that the IMS service is terminated.

A twenty third step C comprises an exchange of teardown messages between the RUI C in the user device and the RUI S in the ANIP of the access network node which serves to teardown the secure tunnel and thereby terminating the IMS session.

With reference to and a method for the ANIP for providing a non IMS enabled user device access to IMS services via ANIP functionality in an access network node will be described. In a first step S the ANIP receives a connection request from a non IMS enabled user device e.g. in the first local network . This step is performed in the respective embodiments A B and C by transmission and reception of the signals of the steps A A B B and C C illustrated in .

In a second step a secure tunnel is set up between the ANIP and the local network node or directly between the ANIP and the user device Embodiment C . This step correspond to step A in step B in step C in . Depending on the network system design the communication between the ANIP and the user device may be direct communication embodiment C pass via a UPnP ISG and two UPnP remote access agents A RA H RA embodiment A or pass via two HTTPs clients and an ISG embodiment B .

In a third step S the ANIP performs user authentication This step is performed in the respective embodiments A B and C by transmission and reception of the signals A A B B and C C illustrated in . The signalling diagrams in all illustrates the alternative in which the user has to input user credentials which in some of the ways mentioned above when describing the optional user identification means with reference to are verified by the ANIP . However it should be appreciated that there are many other ways than the one illustrated in in which a user or user device can be authorized to gain access to the ANIP . For example the user device may comprise a user device identity and be arranged to attach user device credentials to the message with which it initiates the entire IMS session whereupon the ANIP can be arranged to determine whether the user device is authorized for ANIP access based on the attached user device credentials.

If the user user device is authorized by the ANIP the ANIP proceeds with a fourth step S in which a public identity in the form of an IMPU is selected for the user and transmitted to the CSCF server of the IMS network for registration. If the user user device is found to be unauthorized by the ANIP access to the ANIP and thus to services via the IMS network is denied by the ANIP. This step corresponds to step A of step B of and step C of .

Nodes in the IMS network determine whether the user is authorized for IMS subscription based on the received IMPU from the ANIP . This is as such known to a person skilled in the art and therefore not described in detail. If the user user device is authenticated the ANIP in a fifth step S receives a confirmation message typically a 200 OK message from the CSCF. This step corresponds to step A in step B in in .

When the user has been accepted for at least one IMS service the ANIP sends a message in a sixth step S to the user device that the user has successfully logged in and is authorized to use the IMS service or services. This corresponds to step A in B in FIG. B and C C in .

In a seventh step S the ANIP receives a request message to start an IMS enabled service that has been selected by the user based on the information sent by the ANIP in the sixth step S. This step corresponds to steps A A in B B in and steps C in .

In an eighth step S a service session initiation message is sent from the ANIP to the AS . The service session initiation message is here in the form of a SIP INVITE message comprising the PSI of the requested service and inviting the AS to start service communication with the user device . This step corresponds to steps A A of B B of FIGS. B and C C of .

Throughout this document three different main embodiments of a communications network have been described each utilizing various communication techniques for connecting the user device to the access network . We have seen that the functionality residing in the user devices the home local network and the access network respectively differs in parts between the different embodiments. However in all embodiments an access network node comprises means such as the access network tunnel termination point for receiving non SIP data over a secure tunnel connection and ANIP core functionality comprising protocol translation means for translating said data so that it conforms to the SIP protocol before transmitting it to an IMS network. Thereby all the embodiments of the inventive ANIP network architecture described herein have in common that the ANIP functionality allowing non IMS enabled user devices to access SIP based IMS services resides in the access network. Thereby the need for incorporating all IMS enabling functionality in the user devices or nodes in the user s private local network is eliminated.

