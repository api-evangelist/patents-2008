---

title: Method, system, and computer program product for managing routing servers and services
abstract: A method, system, and computer program product for routing network traffic (calls in a Voice over Internet Protocol (VoIP)), which expands the capabilities of existing systems by providing faster and more efficient direction of network traffic, is disclosed. A routing management system includes a routing manager which maintains a list of local routes, establishes and manages connections to the routing server(s), exports routes to the routing server(s), imports disseminated routes from the routing server(s), obtains static global and dynamic routes from the routing server(s), caches those routes for future use, finds all matching routes for a particular number dialed by the user, and prioritizing those routes based on timing, access and ordering information. An additional embodiment contains at least one routing server which provides look-up services for gateway server(s), allows export of local routes from gateway server(s), and distributes translation data; and at least one gateway server which handles calls received on either the Internet protocol (IP) or traditional telephony networks. The gateway server bridges calls between the different kinds of networks, interacts with users, interfaces with the routing system.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09479429&OS=09479429&RS=09479429
owner: CHEMTRON RESEARCH LLC
number: 09479429
owner_city: Dover
owner_country: US
publication_date: 20081125
---
This application is a divisional of U.S. application Ser. No. 09 527 920 filed Mar. 17 2000 issuing as U.S. Pat. No. 7 457 279 which is a continuation in part of U.S. application Ser. No. 09 393 658 filed Sep. 10 1999 issuing as U.S. Pat. No. 6 760 324 which are incorporated by reference herein in their entireties.

Worldwide deregulation and packet switched technology have brought dramatic changes to the telecommunications industry. Voice communication over packet switched networks such as the Internet is now in demand. Voice over the Internet technology is now available which integrates a public switched telephone network PSTN and the Internet. Voice over the Internet technology is also referred to as Voice over Internet Protocol VoIP Voice over Network VON Internet Telephony and Telephony over the Internet. See e.g. G. Held Voice over Data Networks McGraw Hill Series on Computer Communications McGraw Hill Publ. 1998 entire book and T. Sheldon Encyclopedia of Networking Electronic Edition McGraw Hill Publ. 1998 pp. 1047 1050. Both of these references are incorporated in their entirety herein by reference. A PSTN is also referred to as a plain old telephone system POTS . A PSTN can include transmission components links switching components nodes and billing facilities. See e.g. Held chapter 4 Understanding Voice and chapter 5 Telephone Operations and Sheldon at pp. 959 968. The Internet can be any network or combination of networks that support packet switching. Such a network can include but is not limited to a network supporting the Internet Protocol IP and related protocols. See e.g. Held chapter 2 IP and Related Protocols and Sheldon pp. 503 543.

VoIP systems allow a call originating from a PSTN to be carried over the Internet. In this way voice traffic can be carried over the Internet bypassing more expensive long distance carriers. For example Toll Bypass Carrier services multi site corporations and other users use VoIP systems to reduce the cost of long distance telephone calls to a fraction of one cent per minute.

Vendors provide a product or family of products to support VoIP. For example Array Telecom Corp. of Herndon Va. a wholly owned subsidiary of Comdial Company has provided an early generation of products that provide a multi location turn key solution to VoIP Array Tel Series 1000 and 2000 also called versions 1 and 2 . See also B. McConnell How to Build an Internet PBX Aug. 16 1999.

A VoIP system typically relies on gateways to provide an interface between PSTN and IP networks. illustrate how a call is placed over the Internet. As shown in a user calls picks up a telephone and dials a phone number of a phone . The called party at phone answers. A connection is then established through gateways and over IP network . Voice fax and data transmission is then carried out between phones and through this connection. In this way an expensive long distance carrier on a PSTN can be bypassed.

Next gateway contacts destination gateway over IP network . Destination gateway dials the destination phone number over a PSTN line to the destination phone . Gateway then packetizes the voice stream from the PSTN and routes it over IP network to gateway . Destination gateway converts the data packets into a voice stream and sends it over a PSTN line to the called party at phone . By strategically locating gateways such as gateways and in desired calling areas long distance costs are substantially reduced. Indeed a long distance call is essentially replaced by two local phone calls and a low cost IP connection.

Even though VoIP has created an enormous enthusiasm the implementation and success of VoIP networks has been hindered due to at least following four 4 major shortcomings 

absence of advanced applications to offer services such as prepaid calling or carrier class global call routing and

A method system and computer program product that provides gateway routing and database servers with services for voice over the Internet communication VoIP is disclosed herein. In one embodiment the present invention is a VoIP system that includes a gateway server a routing server and a database server. The gateway server handles calls received from a public switched telephone network and a packet switched network. Messages can be sent between the gateway server routing server and database server over the packet switched network. In another embodiment the present invention is a VoIP system that includes an originating gateway server a terminating gateway server and a routing server. Both gateway servers handle calls received from a public switched telephone network and a packet switched network. Messages can be sent between the gateway servers. The routing server is accessed by the gateway servers and provides routing information to the gateway servers over the packet switched network. In another embodiment the present invention is a VoIP system that includes an originating gateway server a terminating gateway server and a database server. Both gateway servers handle calls received from a public switched telephone network and a packet switched network. Messages can be sent between the gateway servers. The database server monitors access and records activity on the gateway servers over the packet switched network.

In addition a provisioning system is coupled to the database server. A management system is also coupled to the gateway server routing server and database server over the packet switched network.

According to one feature a network manager automatically queries a client database to determine an update and sends a message representative of the update to at least one of the gateway server routing server database server and management system over the packet switched network.

According to another feature of the present invention a licensing server is used to support licensing of the VoIP system.

In a further embodiment of the present invention a routing manager component is coupled to each gateway server and a parser subsystem is coupled to each routing manager.

According to one feature of the present invention the gateway server and routing server exchange routes using routing models over a packet switched network.

In one embodiment the present invention includes a gateway server with a routing manager for connecting bridging calls on a packet switched network. The present invention further includes methods for enabling the exchange of route information between gateway server and routing server.

In the present invention routes can be exported from gateway server and routing server to other gateway server and routing server. Additionally routes can be transformed by routing servers for use on other gateway servers.

In one embodiment the present invention includes a route model for local routing and uses local routing to connect gateway servers. The present invention further includes route models for static global routing disseminated routing and or dynamic routing. The present invention can use any number of route models alone or in combination.

According to another feature the routes can be either network or telephony based. In addition the present invention provides for grouping network and telephony routes.

In a further embodiment of the present invention a routing server is connected over a packet switched network to a number of gateway servers and a parser subsystem is included in each routing server. The routing server of the present invention further translates routes based on their origin use and or type.

In one embodiment the present invention includes routines for determining and prioritizing a call address. Call addresses of the present invention can be stored in routes along with other values such as access based on the time of day user account or location which the gateway servers routing servers and other systems of the present invention can use.

According to another feature a database server includes a database access manager a multi database client for communicating with any number of database client s database client s for communicating with database server s database server s with links to database s and database s for storing information. The multi database client provides a middle layer for the relaying of information from any number of connected database clients.

In one embodiment the present invention includes routines for viewing configuring and reviewing user accounts call detail records and event logs. The present invention further includes a management system for configuring component systems.

In one embodiment the present invention includes a graphical user interface that enables a user to configure all the components of the present invention. The present invention further includes a graphical user interface such as in a screen and panel for configuring the identification access line groups routing security database management services licensing and hardware setup properties of the components of the system.

In a further embodiment the present invention includes a graphical user interface for controlling the execution of processes on the gateway servers routing servers and database servers. Additionally a feature of the present invention is the logging of events on each of the gateway servers routing servers and database servers for administrative purposes.

In an embodiment the present invention includes a graphical user interface for configuring the call service properties of a gateway server.

In an embodiment the present invention includes a graphical user interface for listing the country code of a call address maintained by the translation system. The present invention further includes panels for controlling the export of these call addresses as routes. In a further embodiment the present invention includes a graphical user interface for assigning specific line groups to call address as well as controls over the export timing and access provided to that route.

In an embodiment the present invention includes a graphical user interface for adding modifying and deleting routes from gateway servers and routing servers.

In an embodiment the present invention includes a graphical user interface for configuring the features of the gateway server. The present invention further includes panels for assigning the identity and route import export features of the gateway server.

In an embodiment the present invention includes a graphical user interface for listing and or controlling the handling of local routes.

In an embodiment the present invention includes a graphical user interface for listing and or controlling the handling of exported local or dynamic routes.

In an embodiment the present invention includes a graphical user interface for listing and or controlling the handling of static routes.

In an embodiment the present invention includes a graphical user interface for listing and or controlling the handling of disseminated routes.

Further embodiments features and advantages of the present invention as well as the structure and operation of the various embodiments of the present invention are described in detail below with reference to the accompanying drawings.

The present invention will now be described with reference to the accompanying drawings. In the drawings like reference numbers indicate identical or functionally similar elements. Additionally the left most digit s of a reference number identifies the drawing in which the reference number first appears.

The present invention provides a method system and computer program product for providing management of database servers and services in a voice communication over the Internet system. For convenience this method system and or computer program product according to the present invention is also referred to herein as simply a product or family of products. The present invention overcomes the above problems in conventional VoIP systems. In one embodiment there are five basic components 

These components provide a VoIP system with a modular architecture and a scalable configuration. This modular design creates an efficient environment for fast and effective evolution. New capabilities can be added to the system in a fraction of the normal time. This scalable platform accommodates future growth in the number of users and other system demands.

In one example the present invention provides all of the necessary tools to build and operate a large distributed carrier network. The gateway server and database server coordinate to perform calling operations. The routing server facilitates and coordinates interaction between the gateway servers. The management system is used to manage and configure the other components. Smaller networks can operate with a minimum configuration of only the management and gateway servers the remaining components are not required to run such a gateway alone.

All five components can run on the same personal computer PC or on physically separate machines. For example a network could typically include a central management server running on the administrator s PC a number of gateway servers running in various locations and a centralized database server shared between them. The servers PCs running the various components do not have to be on the same local area network LAN as long as they are connected via an IP network.

The present invention is compatible in an open architecture. For example industrial grade IBM compatible workstations and servers can be used as a hardware platform. Microsoft Windows can be the operating software. Dialogic voice boards that are globally recognized can be used. The availability of Dialogic voice boards for the majority of countries around the world allows an embodiment of the present invention to be distributed on a global basis to customers. Lucent SX 7300P can be used as a CODEC voice coders and decoders . Its acceptability industry wide combined with high quality and low bandwidth usage makes it a superior choice. Current interoperability voice communication standards H.323 v2.0 and the voice coders G.723.1 associated with the standard are also used.

This implementation is not intended to limit the present invention however as other types of platforms operating software voice boards CODECs voice communication standards and voice coders can be used as would be apparent to a person skilled in the art given this description. Propriety components can also be used instead of or in addition to the open standards described herein.

The present invention further has a scalable architecture. This allows the system to grow with no limitations to thousands of ports regardless of a monolithic or distributed implementation. Growth is modular. In one example implementation each gateway server module provides up to 4 or more digital boards of T1 T1 PRI or E1 PRI for easy expansion. This advanced design offers 100 availability as modules are enabled to share the traffic in an unlikely event of a failure of a component. Redundancy of services and back up facilities can be built into the design to provide a high level of reliance for mission critical applications.

One shortfall of VoIP in the early 1990s was the poor quality of voice jittery voice and the unacceptable latency caused by the fluctuating and at times less than adequate bandwidth available through the Internet.

According to a further feature of the present invention dynamic jitter buffering DJB is used to resolve the quality of voice over the unpredictable and some time limited bandwidth of the Internet. This capability dynamically adjusts the size of the voice buffer and eliminates the jitter. In addition the present invention utilizes the resources of DSP to support verity of voice improvements. A level of quality at or near toll quality is achieved.

In one example of the present invention the VoIP system is mostly implemented in a distributed fashion to enable low cost long distance calling. As a result the organizations using the present invention can form business structures and organizations that are just as innovative and distributed as the VoIP system. While the business needs of customers are different and every changing they all require systems that are infinitely flexible. For this reason the present invention in one example is developed with maximum flexibility in mind. The architecture of the system allows for the services such as routing database and management servers to reside on one system location or be distributed to several locations. These servers if connected to the same packet network will operate as if they are all in the same location.

Many of the early adoptions of Carrier Class VoIP technology were in the area of prepaid long distance. Service providers were often forced to purchase three 3 major components in order to operate their prepaid services. These components were 

a prepaid application server to conduct registry PIN number generation and validation and account debiting functions and

The present invention can support all of the above prepaid functions in a gateway architecture and offer them to users such as customers at no additional charge.

When the present invention is deployed as a network of gateways around the globe some of the applications and servers can be centralized in one location for ease of operation and savings. Alternatively the applications and servers may be distributes throughout a network. Either way this allocation of servers is effected by end users which come from many different backgrounds and nationalities. In order to provide the best customer service possible one embodiment of the present invention uses a full Interactive Voice Response IVR system in gateways with multi language prompts. This enables the VoIP system of the present invention to speak the language of its users and therefore generate more business or traffic.

According to a further feature the VoIP system of the present invention provides VoIP technology even to users such as businesses who do not have cost effective and reliable Internet connections available to them at this time but wish to start a prepaid application and move to IP transport later. Prior to the present invention operators of a start up VoIP business e.g. a prepaid service provider were unable to use any VoIP Gateway to start their prepaid business. The present invention provides PSTN trunk to PSTN trunk connection no Internet connections in the same manner as a PSTN switch and offers prepaid services at a fraction of cost. This provides an opportunity for prepaid service providers to establish their business with 80 cost savings.

The present invention provides a variety of PSTN and Packet Network connections including but not limited to internet analog PSTN lines frame relay PBX extension lines ATM digital T1 and T1 PRI private leased lines and digital E1 PRI.

The present invention is described in terms of this example environment. Description in these terms is provided for convenience only. It is not intended that the invention be limited to application in these example environments. In fact after reading the following description it will become apparent to a person skilled in the relevant art how to implement the invention in alternative environments known now or developed in the future.

To more clearly delineate the present invention an effort is made throughout the specification to adhere to the following term definitions as consistently as possible.

The terms packet switched network and Internet are used interchangeably to refer to any network that performs packet switching including but not limited to a network that supports a Transmission Control Protocol TCP and or an Internet Protocol IP . The terms packet switched network and Internet are not intended to limit the size of a network and can include but are not limited to a wide area network WAN middle area or campus wide network or local area network LAN or combinations of networks.

The term traffic refers to voice facsimile video multimedia digital information or other data that can be sent between telephony terminal equipment and or network terminal equipment.

The term routes refers to any listing of address information either network or telephony or both which can be used to direct traffic.

The term window and screen are used interchangeably and refer to a graphical user interface for expressing confirming and or altering the configuration and or operation of the present invention.

The term dialog refers to a window or screen which is displayed while interacting with a window or screen in any graphical user interface such that configuration can occur. Dialogs are usually displayed with Ok and Cancel buttons. Dialogs usually return a user to the original window or screen after confirmation or negation.

The term environment collectively refers to the components of the system and the connections among them. Software environment refers to the environment constructed by the various processes and routines of the system.

The use of the terms view and document refer to the objects used in computer programming. A document is an object for storing data. A view is an object for rendering visual representations of a document s data on a display either graphically textually on screen in print or the like. Views are also used to translate user input into the system. For example by recording mouse movements and keyboard messages. A detailed treatment of the properties of these objects can be found in Programming Windows 95 with MFC Part VII The Document View Architecture by Jeff Prosise Microsoft Systems Journal 1995.

Such voice and data traffic can originate at any type of terminal equipment at PSTN . For example a call can be placed on an ordinary telephone or . A call can be placed from an ordinary telephone using a prepaid service and autodialer . Calls can also originate from a speaker or conference type phone through a private branch exchange PBX . Such calls can terminate at an IP phone or an ordinary telephone . These examples are not intended to limit the present invention. As will be apparent to a person skilled in the art given this description any type of computer or telephone equipment can be used to originate and terminate voice calls over the VoIP system .

VoIP system includes Gateway Servers Database Server s Routing Server s Management System s Provisioning System s Network Manager s and License Server s . Each of these components can be interconnected over the IP network as shown in . In one embodiment Provisioning System is coupled to Database Server . Provisioning System is controlled by graphical user interface GUI tools . Similarly Management System is controlled by graphical user interface tools . A relational database such as a SQL Database is further coupled to Database Server .

Another embodiment employs only one Gateway Server with the above components in the same configurations. The lack of second Gateway Server would restrict the economy of the two or more gateway server embodiment since long distance charges are more likely to occur when the same gateway handle incoming and outgoing telephone calls. However a single gateway server would suffice for a working VoIP system and would be feasible in some situations. For instance call center applications which entail the use and tracking of internal telephone networks are one possible implementation of this single gateway embodiment. Others are possible and this implementation is merely an example.

VoIP system is designed to allow voice and fax traffic to be carried over IP network . Voice and fax traffic received from PSTN is coupled through gateway servers and over IP network . In addition to providing simple call termination VoIP system provides a host of enhanced features that enable IP telephony capabilities to be used in a number of different applications. For example since IP telephony typically results in much lower telecommunications costs and can be used between two branch offices to reduce costs. This reduced cost can instead be used to resell long distance service to end users. Another application is to enable IP telephony terminals such as multimedia computers running group meeting software to access traditional services such as a call center. By combining IP telephony with other technologies such as the World Wide Web WWW integrated WWW VoIP system makes these applications possible by acting as a gateway between traditional telecommunication networks such as PSTN and systems and a packet switch network such as IP Network and systems.

In one example implementation there are two main parts to VoIP system a software part and a hardware platform.

An overview of each of the components of VoIP system is now provided. Further descriptions with respect to an example implementation is provided below in Section IV. Gateway Server and Gateway Server are coupled between PSTN and IP Network . Gateway Server can be coupled to any number of Telephone Lines and Network Lines .

Gateway Server includes in one embodiment both software and hardware components. For example as shown in Gateway Server includes a Gateway Server Application Layer Gateway Server Platform software and Gateway Server Hardware . Gateway Application Layer includes Higher Level Application Services . For example these application layer services can include Gateway Service Common Services Auto Forward Services Other Services Higher Level Services and Abstract Services . In one example implementation where the software is written in an object oriented program language such as C each of the Higher Application Layer Services accesses lower level modules also called objects through a Session Manager Application Programming Interface API .

Gateway Server Platform includes Session Manager . Session Manager includes Rule Engine . Session Manager creates and manages Sessions . In general any number of sessions can be managed depending on the resources of the Gateway Server . Each session corresponds to a voice call carried over Gateway Server . Information in a Session or can be further handled by lower level Line Group Manager Routing Manager Database Access Manager Media Manager and Call Rating Manager . Routing Manager is further coupled to a Subsystem . Subsystem can contain various components dealing with the implementation and execution of routes. For instance Local Parsing and Wildcarding can be included in Subsystem . are discussed in the E.164 Parsing section below. Database Access Manager is also coupled to a Subsystem . For example Subsystem can be any cache memory or other storage device for storing routing information. Subsystem can be a relational or nonrelational database.

Line Group Manager coordinates communication between the telephone line side and network line side of Gateway Server for a particular session or call. In this way the Higher Application Layer Services and Session Manager API can be transparent to any particular protocols required by a telephone line or a network line.

Conversion Module then converts a telephone line group to a line group. Conversion Module converts a network line group to a line group. In this way Line Group Manager manages line groups without regard to whether a line group is a particular telephone line or network line. That is the type of line is transparent to the Line Group Manager and any other higher level application services.

Hardware Device Manager is the module or object responsible for managing the connectivity of Gateway Server to traditional telecommunication devices and to conventional internet related networking components. Thus Hardware Device Manager coordinates with different respective modules or drivers to control telephony and network components. For example as shown in Gateway Server Hardware can include a NIC card as part of PC. NIC Card is further supported by Gateway Server Software components to coordinate information sent to Hardware Device Manager . In particular a TCP IP Stack Net Support Module H.323 Stack and H.323 Support Module are used to couple NIC Card and Hardware Device Manager . Similarly for telephony components Gateway Server includes a Dialogic telephony board s that can be coupled to phone lines over PSTN . Gateway Server Hardware can further include an Analogic Brooktrout Digital Signal Processor DSP . Dialogic Telephony Board s are supported by respective Dialogic Drivers and Dialogic Middleware . Similarly Analogic Brooktrout DSP s are supported by a DSP Driver and a respective DSP Middleware Support Module . This example including the specific vendor products are illustrative. Other software and hardware modules supporting internet and telephony services can be provided in Gateway Server as will be apparent to a person skilled in the art given this description.

The embodiments of the present invention are discussed in detail below with reference to the following figures. and are described with respect to the gateway server and its features and components. are described with respect to the routing server and its features and components. are described with respect to the database server and its features and components. are described with respect to the gateway server routing server and their embodiments. are described with respect to the provisioning system and its features and components. are described with respect to the management system and its features and components. are described with respect to the network manager and its features and components.

Furthermore are described with respect to the installation of computer software components of the present invention. are described with respect to the configuration of the features and components of the gateway server routing server and database server. are described with respect to the configuration of driver resources. are described with respect to the configuration of line groups. are described with respect to the service modules. are described with respect to the configuration of features and properties of the gateway server. are described with respect to the configuration of routes. are described with respect to the configuration of the database server and its properties and connections to the other components of the VoIP system.

The operation of Gateway Server is described further below with respect to an example implementation.

Database connection manager and database connection s provide service modules with the appropriate format for sending and receiving requests from database clients and . Database connection manager and database connection retrieve the appropriate formats from Open Database Connectivity ODBC API .

As shown in Gateway Server manages the specialized telephony hardware that is used for interconnection to telecommunications equipment and performs bridging of calls between the traditional telecommunications network and an IP network to which Gateway Server is connected. The key responsibilities of Gateway Server are handling calls received on either IP network or PSTN bridging calls between the two different kinds of networks circuit switched and packet switched . Such bridging can include but is not limited to voice compression echo cancellation control protocol transformation and numerous other complex operations interacting with telephone users using DTMF digits and other methods of telephony signaling in order to collect information such as a target destination number user identification password and more.

Gateway Server is also responsible for interfacing with a routing system described below in order to translate numbers and routing those numbers to the correct destination gateway IP address or telephone number depending on the number dialed. Gateway Server interfaces with Database Server in order to validate user accounts apply charges and keep records of all calls.

Routing Server is used to route calls across IP network and possibly to a final destination on the telephone network. Routing Server is optional in that Gateway Server can route a call based on local information maintained on Gateway Server . However Routing Server according to a further feature of the invention can facilitate the automatic exchange of routes between different gateway servers . This in general can make the administration configuration of call routing much easier.

In this way routing server s can serve the following functions They can look up routes to a particular number they can allow Gateway Server to export local routes for the use of other gateways in the system and Routing Server can further provide Gateway Servers with routes that are specifically intended for that respective gateway server. These functions allow all routes to be configured on the Routing Server only but automatically distributed to the appropriate gateways. Routing Server can also distribute E.164 translation data through a E.164 Parser in Subsystem . This facilitates the exchange of such data eliminating the need to configure it on each Gateway Server individually.

According to a further feature in an enlarged deployment and for reliability it is possible to configure Multiple Routing Servers in the same network. Multiple servers can provide both load balancing across multiple machines and redundancy to protect against the failure of any particular Routing Server .

Thus Routing Server is responsible managing routing clients. In one embodiment Gateway Server s are the routing clients. Routing Server provides new and updated routes to the routing clients to which it is assigned. Routing Server also has the ability to perform searches for a matching routes within its own stored directory of routes. Routing clients can request such searches of Routing Server s .

Database Server manages the users of VoIP system . Database Server supports the restriction of calling privileges to users with valid user accounts. In addition Database Server allows billing for VoIP services to be done in either a postpaid or in a real time manner. Alternatively Gateway Servers can be connected directly to a database such as Database . Preferably however Database Server is provided so that VoIP system can be scalable. As described with respect to Database Server can scale to accommodate any number of databases depending on the number of users and or services provided by VoIP system .

In one example Database Server provides Multi database Client as middleware for interfacing with numerous Gateway Servers while using only a small number of connections to the underlying database s . This allows even very large numbers of Gateway Servers to have access to data contained in a shared database or databases. Multiple Database Servers can be used as shown to provide redundancy and protection against failure.

Management System uses GUI Tools to enable configuration administration of software components for the VoIP system . Management System can connect to gateway servers Routing Server and Database Server s remotely over IP Network . In this way Management System can monitor the current state of these servers and make changes to the configuration of these components. This architecture allows all of the Gateway Servers Routing Server and Database Server in the network to be configured from a single point.

Users can interact with VoIP system with the GUI Tools presented through Management System View . Management System view provides users with the screens windows and displays to modify the VoIP System and forwards configuration information to Management Client . Management Client interacts with Software Environment . In one embodiment Management Client would interact with the Database Server which is a component of Software Environment . If needed Management Client would relay information to Management Client Object and updates to ActiveX OCXs .

ActiveX controls formerly OLE controls are objects that can be inserted into any application that is an ActiveX control container like IE Visual Basic and Delphi. Examples include buttons stock tickers and chart controls. For example Animation GIF ActiveX Control exposes the AniGIF object that you can use to create new applications and programming tools with Animation GIF interface. Many development platforms now support ActiveX Controls. These containers include Visual Basic Visual C Visual Basic for Application 7.0 Visual Foxpro Access Delphi PowerBuilder and many others. OCXs are Object Linking and Embedding Controls and are known commonly as .ocx files.

ActiveX OCXs are stored updated as shown and implemented in management client objects and management controls . Management controls receives implements from ActiveX OCXs and events from management client objects . Management controls manages the configuration of the VoIP system so that conflicts among system components do not occur.

Provisioning System is a tool that allows access to the data managed by Database Server . Management System provides access to the Database Server and allows Database Server to be configured but it is the role of Provisioning System to actually allow interaction with data contained in Database s . In one embodiment Provisioning System performs the following tasks using GUI Tools Provisioning System allows accounts of system users to be added removed or modified Provisioning System enables a user to configure and maintain group records of users and account records of users and Provisioning System also enables call detail records stored by the Gateway Servers to be reviewed. Like Management System Provisioning System operates remotely over IP network and can be used to administer multiple Database Servers .

Users can interact with VoIP System through Provisioning System View . Provisioning System View provides users with the screens windows and displays to modify the VoIP System . Database Client Subsystem is linked to Software Environment . Database Client Subsystem provides data from the database server to requesting components of the VoIP System . Users can access and view this data from Provisioning System view .

Network Manager is a separate application that allows VoIP System to be configured or modified in response to specific client requests. shows a block diagram of one embodiment of Network Manager . A client request made in the form of a change at a Client Database is automatically recognized by Network Manager . Network Manager then formulates and propagates appropriate control signals to Software Environment in order to configure VoIP system accordingly. In this way specific client requests and needs are automatically made to VoIP system .

Licensing Server according to a further feature of the present invention allows licensing of the present invention technology according to license keys. A license key is an encoded string that contains information regarding a particular license. License Server is an essentialized license server that manages licensing for all components in VoIP System . When a component first starts up it will contact License Server to receive necessary license. With this configuration all license keys are configured on a single machine and only one hardware key is required.

Part 1 Basics of the present invention provides basic information that applies to all of the components of the present invention. This part contains three sections 

System Overview Provides an overview of the present invention describing the key components of the present invention and how these components interact to provide flexible IP Telephony services. This section also discusses common concepts that are helpful in order to understand the interaction between present invention components. These concepts include identification security configuration management services and management.

Installation and Setup Describes how to install and configure the present invention. This section discusses hardware board installation hardware driver installation and setup as well as the installation and basic configuration of the present invention software. Only basic setup is covered in this section later sections provide full details on how to configure the present invention.

Getting up and Running Completes the introduction to basic functionality by demonstrating how to get a basic system up and running after it has been installed and set up. Shows how Management System is used to configure operational components how services can be started and stopped and how common functionality such as identification and security can be set up.

Part 2 Operation discusses how to use the functionality provided by the present invention in detail. There are four sections in this section each discussing a specific aspect of functionality provided by VoIP System . The sections are as follows 

Gateway Server Capabilities Provides a detailed description of the gateway server capabilities. This section discusses how to control the interaction of the end users with the system and how to configure items like voice prompts services and numerous others.

The Gateway Application Introduces the main application that runs on the gateway server the gateway application which provides the main service offered by the present invention. Discusses the configuration and operation of the gateway application in detail.

Routing and Number Translation The present invention provides numerous ways to translate digits dialed by the user and to route calls across a network of gateways. This section describes the routing process and explains how this process can be optimally configured for a particular environment and network structure.

Database Basics Provides an introduction to the database servers and describes how the gateway servers makes use of them. This section introduces some of the basic information as a prerequisite to discussion features of which the database server is an integral part in the following sections.

User Management An important requirement particularly for telecommunications service providers is the management of the end users of the system and the maintenance of their accounts. This section discusses user management explains the various information maintained for each user of the system and shows how this information can be used to customize the service provided to the end user.

CDR Collection In order to bill for and have a record of calls the present invention is capable of collecting a Call Detail Record CDR for each call. This section explains the CDR collection process and how it can be customized for a particular environment.

License Server In some environments a license server can facilitate the network wide licensing of present invention software. This section provides details on how to set up a license server for the purpose of simplifying license administration.

Part 3 Technical Information provides detailed technical information about the present invention. This information is useful for optimizing the performance or quality of an present invention installation or for integrating external applications with the present invention. There are two appendices in this section 

Database Table Descriptions The structure of database tables used by the database server is described in Appendix A. This information is useful in developing customized applications that interface directly with the data stored in the database.

Designing a Network The quality of any IP Telephony system is heavily dependent on the quality of the underlying IP network used to transport the IP traffic. This section provides a detailed description of the network factors that affect the overall performance of the system and provides information on bandwidth and port numbers necessary to design a network that will deliver maximal quality.

This section provides an overview of an example implementation of the present invention. It describes the components that make up the present invention and how these components co operate in order to deliver IP Telephony services. It describes the basic concepts that are common to all components of the present invention.

The Present Invention. This section describes at a very high level what the present invention is and what it provides the capability to do.

Present Invention Components. This section introduces the components of the present invention. It describes the purpose of each of the components as well as the interaction between those components.

Key Concepts. The key concepts that are common to all components of the present invention are described in this section. The concepts covered include identification security configuration management and licensing. The basic principles of operation such as starting and stopping services are also described in this section.

The present invention is designed to allow voice and fax traffic to be carried over an IP network. This is more commonly referred to as IP Telephony. In addition to providing simple call termination the present invention provides a host of enhanced features that enable IP Telephony capabilities to be used in a number of different applications. Since IP Telephony typically results in much lower telecommunications costs it can be used to reduce telecommunications costs between two branch offices. The reduced communication costs could instead be used to resell long distance calling to end users. A further application is enabling IP Telephony equipped terminals such as multimedia PCs running group meeting software such as but not limited to Microsoft NetMeeting to access traditional services such as a call center. By combining IP Telephony with other technologies such as the World Wide Web integrated WWW call centers are possible. The present invention makes these applications possible by acting as a gateway between traditional telecommunications networks and systems and IP systems.

Software Platform. This is a suite of software components which provide IP Telephony services across an IP network. These components can run as executables or applications on an operating system such as but not limited to processes running on Microsoft Windows . Each of the components of the present invention software is described in detail in the next section of this section.

Hardware Platform. In order to achieve connectivity with traditional telecommunications systems and networks such as legacy phone systems PBXs and the public switched telephone network PSTN a specialized hardware platform according to the present invention is necessary. This hardware platform is used to run the present invention software components of the present invention that handle connectivity to traditional telecommunications devices and consists of a PC containing one or more specialized telephony hardware devices. In addition standard PCs can be used to run other software components of the present invention that do not require a direct connection to the traditional telecommunications equipment.

Each member of the present invention consists of a hardware platform with specific traditional telecommunications equipment connection capabilities as well as software configured for that connection. The present invention supports but is not limited to the following kinds of connections 

In addition to the different types of connectivity supported different members of the present invention provide different connection sizes ranging from two line systems up to multiple T 1 E 1 systems. It is also possible to license the present invention s software independently of the hardware platform as well as to customize hardware platforms to achieve other capabilities of the VoIP system.

The main focus of this section is to explain the present invention in an example software implementation and how it is used to deliver the desired IP Telephony services to the end user.

The present invention software is comprised of a number of independent software components each of which provides some part of the overall functionality provided by the present invention. These components communicate with each other over the IP network that connects them. The different types of components are each discussed below. It is important to note that numerous instances of each type of component may be running simultaneously in different locations.

Each component of the present invention software is an independent application. Once installed these applications can be executed in the same manner as any other application. Directions on interacting with the individual components are provided in the sections later in this document with an overview of the interaction. Each of the components that comprise the present invention software is described in the subsections below.

Gateway Server manages the specialized telephony hardware that is used for interconnection to the telecommunications equipment and performs all bridging of calls between the traditional telecommunications network and the IP network to which the Gateway is connected.

Bridging calls between the two different kinds of networks step . This involves voice compression echo cancellation control protocol transformation and numerous other complex operations 

Interacting with telephone users step using DTMF digits and other methods of telephony signaling in order to collect information such as the target number user identification password and more 

Interfacing with the routing system step described below in order to translate numbers and routing those numbers to the correct destination gateway IP address or telephone number depending on the number dialed 

Interfacing with the database server step in order to validate user accounts apply charges and keep records of all calls.

With multiple gateway servers it is possible to do long distance PSTN switching over an IP network step . This requires two gateway servers one in the originating PSTN zone and one in the terminating PSTN zone. This configuration is shown in . The originating PSTN Zone is coupled to Gateway Server A . Gateway Server A is connected to the Internet . Gateway Server B is also connected to the Internet . Gateway Server B is coupled to terminating PSTN Zone . Calls are denoted by the dotted lines which partially represent the flow of data through the system.

Of course more than two gateways i.e. gateway servers could be connected via the IP network resulting in a wider range of calling areas. Furthermore it is not necessary to restrict calling to the local PSTN zone in which each gateway server is located. For example a single gateway server in New York could handle all calls for North America. If the other gateway servers in the network were located outside of the United States and Canada then this would still represent significant cost savings over the direct dialed long distance rate from the international location.

Routing Server is an optional component in the system that is used to route calls across the IP network and possibly to a final destination on the telephone network. It is not a required component in order to be able to route calls. A gateway server can route a call based on local information maintained on the gateway server. However the use of a routing server can facilitate the automatic exchange of routes between different gateway servers and can in general make the administration and configuration of call routing much easier.

Provide gateway servers with routes that are specifically intended for that gateway server step . This allows all routes to be configured on the server only but automatically distributed to the appropriate gateways 

Providing gateway servers with the ability to look up routes to a particular number steps and . For example a gateway server could ask a routing server for routes to a number such as 1 703 555 1234. The routing server if it has a route would return it to the gateway server which would then use the route to complete the call steps and . Hence the routing server might indicate that there is a gateway server located at IP address 192.168.1.3 that can complete the call to 1 703 555 1234 

Distribute E.164 translation data as shown in and discussed in detail below . An important process is how a string of digits entered by the user is translated into a standard E.164 style address e.g. 00117035551234 1 703 555 1234 . The routing server facilitates the exchange of this data eliminating the need to configure it on each gateway server.

In a large deployment and for reliability it is possible to configure multiple routing Severs in the same network. The use of multiple routing servers can provide both load balancing across multiple machines and redundancy to protect against the failure of any particular routing server.

The present invention software may in many applications need to manage the users of the system. When gateway servers are connected to the PSTN. PSTNs are accessible to by the general public. Thus in a VoIP system connected to the PSTN it is generally necessary to restrict calling privileges to those users with valid user accounts. In addition it is often desirable to bill for services either post paid or in real time. Although the gateway servers could connect directly to a centralized database using Open Database Connectivity ODBC this approach would not be scalable. Conventional database packages support only a relatively small number of concurrent connections to the actual database. Furthermore it would not be secure particularly if the IP network connecting the gateway servers to the database is the Internet. In this environment the actual database would need to be exposed to the Internet in order to provide access to gateway servers. It is often preferable to keep the actual databases protected behind a firewall.

Database Server addresses these problems by providing middleware components that interface with numerous gateway servers yet use a small number of connections to the underlying database. This allows very large numbers of gateway servers to have access to the data contained in a database accessible to Database Server . In one embodiment Database Server supports underlying databases in Microsoft Access format as well as Microsoft SQL Server. The use of a standard underlying database package facilitates integration of external applications with the data that drives the present invention. The present invention is not so limited. Other types of databases and database formats may be used.

Even though only a small number of connections exist between Database Server and the underlying database package a License Agreement may require a separate license for each gateway server that either directly or indirectly uses the services of the database package.

More complex configurations are possible. As with the routing server it is possible to use multiple database servers in a particular network. This is usually done to provide redundancy and protection against the failure of any particular database server.

Management System is a GUI tool that is used to perform configuration and administration of the above present invention software components. It connects to the gateway routing and database servers remotely via the IP network and can be used to monitor the current state of those components as well as to make changes to the configuration of those components. This architecture allows all of the gateway routing and database servers in the network to be configured from a single point. This is critical in environments where the actual servers may not be directly accessible. Furthermore multiple instances of the management system can be run on different machines allowing several administrators to jointly manage the network.

Management System Platform includes Management Controls Management Client Objects Management Client Management System Document and ActiveX OCXs . These components provide the functionality of the management system by interacting with the other components of VoIP System . Management System Hardware includes the elements of Computer System in the PC on which Management System is executed.

From its connection with Software Environment Management Client determines if an update to ActiveX OCXs is required step . Any update to ActiveX OCXs is implemented in both Management Client Objects and Management Controls steps and .

Provisioning System provides GUI Tools that allow access to the data managed by Database Server . Management System provides access to Database Server and allows Database Server to be configured but it is the role of Provisioning System to actually allow interaction with the data contained in the databases. The following are the main tasks of Provisioning System 

Reviewing call detail records CDRs created by the gateway servers and stored within the components of Database Server s .

Provisioning System can be operated remotely just like Management System and can be used to administer multiple Database Servers . In some applications the provisioning system may not be required since external applications can directly modify the data contained in the underlying database. The provisioning system is provided as a tool for those users who don t require the flexibility of a custom external application.

Provisioning System Platform includes Provisioning System Document . Information is obtained through Software Environment from Database Client Subsystem . These components provide the functionality of the provisioning system by interacting with the other components of VoIP System . Provisioning System Hardware includes the elements of Computer System in the PC on which Provisioning System is executed.

The present invention includes a number of utility components that are useful for the initial configuration as well as diagnosis of present invention software components. These components do not necessarily play a large role in the day to day operation of the system. These components are as follows 

Installation Program. This program will install the present invention software components that one can choose on to a particular machine. One normally need only run this once and only if one purchased the software independently of the hardware platform.

Express Configuration. The Express Configuration or ExpressConfig program is designed to allow one to set up a basic configuration for present invention software components in a short period of time. The most common values for advanced features are automatically configured other features are automatically configured based on a simplified set of information that one provide during Express Configuration. After the process is complete the configuration of the system can be fine tuned using the management system.

Control Panel. The control panel is an application that allows one to monitor start and stop the gateway routing and or database server s running on the same machine as the Control Panel utility. It is useful for diagnostic purposes but it has no capability to change any configuration parameters.

As explained in the previous section there are a number of different types of components in the present invention software. In addition it was also explained that there may be many instances of the same type of component running on different machines. Using the gateway server example there might be one gateway server in New York and another gateway server in Los Angeles. These two gateway servers might switch calls over an IP network connecting them allowing inexpensive long distance between New York and Los Angeles.

The term node will often be used to describe an instance of a particular type of component. For example both of the gateway servers in the previous example are distinct nodes even though they are both components of the same type.

It is also possible to run instances of different components on the same machine. In this case each different component is in effect a different node. There is actually no difference in operation regardless of whether components run on the same machine or on different machines except for the utility components which only operate on the local machine. Therefore when nodes are discussed in this document it will be assumed that they could always be running on the same machine. However it is not possible in some cases to run two or more instances of the same component on the same machine. As an example a gateway server and a database server could run on the same machine. However in some cases two routing servers could not run on the same machine.

Operational Components. This refers to the gateway server routing server and database server. These software components provide IP telephony services to the end user and are not interacted with directly by the administrator of the system. Operational components are always running and run in the background with no user interface. Operational components are similar to other software services they can be started or stopped at any time and only provide their services while started. Operational components do not however run as operating system services they are software applications that run in the background on an operating system. Operational components can be administered at any time even while stopped as long as they are running.

Administrative Components. This refers to the management system s and provisioning system s . These components are applications that can be used to interact with the operational components. The management system interacts with all three operational components in order to perform configuration changes the provisioning system interacts only with the database server in order to manipulate data in the database.

Utility Components. This category of components was defined previously and provides programs that operate directly on the local machine.

All present invention software components manage configuration in the same way. The configuration is stored in the operating system s registry under a key. Each individual product component will store configuration in subkeys of this key. When a present invention software component first starts it will read its configuration from the registry. After startup has been completed components will not in general re read the registry. If one makes configuration changes to the present invention software directly by editing the registry one will in general need to restart the component for which one is editing the configuration in order for the configuration change to take effect.

In general one will not need to interact directly with the configuration data stored in the registry. The main purpose for providing this information is to allow one to locate the configuration data so that one can ensure that it is backed up with the rest of an installation.

The security model employed in the present invention employs two main ideas. The first is the idea of identification and authentication and the second is that of access control. Identification and authentication described in this section describes how one component of the present invention usually a server of some sort determines the identity of another component that is requesting some service or data. Once the requesting component has been identified and authenticated access control is then used to determine if the component with that identity should indeed be granted access to the requested data or service.

Identification and authentication are performed through the concept of a security domain. This concept is central in trying to configure the security subsystem of any present invention component. Stated simply a security domain is just a collection of members that are part of that domain. Each member has a unique name within that domain and has some authenticating information that can be used by other members in the domain to verify that it is indeed a valid and legitimate member of the domain. The domain will also have a unique name. When displaying the full name of a member the DOMAIN MEMBER syntax will be used where DOMAIN is the name of the security domain and MEMBER is the name of the member within that domain.

An present invention security domain should not be confused with a operating system s domain. The two types of domains are not related in any way. Making two present invention components part of the same security domain does not make them part of the same operating system domain.

Each instance of an present invention software component previously defined as a node must be a member of at least one security domain. This is always required since all components of the present invention either connect to some node to administer and manage them which must of course pass identification and security checks or else they are connected to by administration management components in which case the connecting component must be identified .

It is possible for a component to be a member of multiple domains. However there are not many situations in which this capability would be necessary.

Also recall that two nodes running on the same machine for example a gateway server and a database server are not considered to be the same node. Therefore despite running on the same machine the two components could be given independent different identities.

Lastly it should be noted that two distinct nodes can be given the same identification. Typically this is used to simplify administration by assigning all components running on a given machine a common identity. However it is generally recommended that different components of the present invention be given identities even if they run on the same machine.

As described in the previous section the security model in the present invention is comprised both of identification and security and access control. Identification and authentication are a prerequisite to access control. The role of access control is to determine what level of access should be provided to a remote node. For example just because a gateway server can determine the identity of a management system it does not imply that the gateway server should automatically allow that management system to administer it.

Access control is required in numerous places in the system. The main places where access controls is required are as follows 

The gateway routing and database servers need to determine whether a particular management system should be allowed to perform administrative operations.

The database server needs to determine whether a particular provisioning system should be allowed to modify the data in the database.

The routing server needs to determine whether a gateway server should be allowed to retrieve call routing data.

The database server needs to determine whether a gateway server should be able to query the user database or insert CDRs.

Although there are access control features between gateway servers they are handled using a different mechanism to allow additional features such as billing of the remote gateway which are not possible using the access control system applied in other areas of the present invention.

Access control in the system is accomplished through an access control list associated with the particular service or resource that can be accessed. This access control list specifies the identifiers such as DOMAIN1 MEMBERA of the members that are permitted to access the service or resource with which the access control list is associated. Each entry in the access control list contains not only the identities of the members that should be associated with that entry but also information concerning the level of access that the identified members should have. For example the routing server allows control over whether or not a gateway server can export routes for the use of other gateways.

The management system component is used to perform the management and administration of the gateway routing and database servers as described previously. This administration and management is fully remote and can be performed from anywhere in the network providing that there is an IP network connection to the node being administered.

Having explained the security model employed by the present invention components it is now possible to explain the basic mechanism by which the management system functions. Each operational component has a management server it allows management operations to be performed by a remote management client. The client in this case is the present invention management system and is discussed previously. In order to manage a remote system the management system first establishes a connection to the operational component. After this connection is established the management system provides identification and authentication information. The operational component checks the information provided by the management system and uses this information to determine whether or not the connecting management system should be granted to access to administer it. If the connecting management system cannot be identified and authenticated or it does not have a matching entry in the Management access control list on the target operational component the connection will be terminated.

Once the connection is successful the management system can be used to administer the operational component. How to use the management system to perform this administration is described in detail below.

In order to use an present invention software component a software license for the component being used must be available. This license can be provided upon the purchase of the software.

According to the present invention licensing is performed via license keys. A license key is an encoded string that contains information regarding a particular license. Each license key provides a fixed number of licenses to a particular component of the present invention software. License keys are only valid for use by the customer to which they were issued. Furthermore license keys are dependent on a hardware key also supplied at the time of purchase. This prevents one s license key from being illegally used by others that may somehow obtain access to this license key. The hardware key attaches to the parallel port of one s computer and allows the license key to be interpreted correctly.

In one example license keys are required only for the gateway server component of the software. One gateway server license must be acquired for each line in the system. However a single license key may contain 10 100 or more licenses so a separate license key is not required for each line . Since multiple license keys may be used simultaneously it is possible to expand a system providing that adequate hardware is installed simply by purchasing additional license keys. This provides the flexibility of acquiring a small number of licenses to begin with and scaling up the number of licenses as traffic requires.

Standalone Mode. In standalone mode each gateway server is required to have its own hardware dongle. A license key is required for each gateway server and must contain sufficient licenses for the use of that gateway server. This model is simple to implement and allows complete independence between Gateways.

Server Mode. In server mode a centralized license server manages licensing for all components in the network. When a component first starts up it will contact the license server to receive the necessary licenses. With this configuration all license keys are configured on a single machine and only one hardware key is required.

Time limited demonstration license keys are also be available to facilitate evaluation of the licensing.

This section describes an example installation and setup of the present invention. This section is divided into three main sections 

Hardware Installation and Setup. This section details how to install the hardware used by the gateway server to interface with the telephone network and how to configure the drivers for that hardware.

Software Installation. This section describes how to install the various present invention software components.

Express Configuration. This section describes the Express Configuration program and how it can be used to configure a default initial configuration for the present invention.

In one example the present invention is a turnkey systems. The hardware driver software and software of the present invention installed and pre configured for a particular environment. Alternatively software can be sold separately. The information in this section pertains only if the present invention software was acquired separately or if the software needs to be re installed.

This section discusses the installation and setup of hardware devices used by the gateway server to interface with the telephone network. Telephony hardware devices are not required in order to operate the routing server database server or any of the other components of the present invention software.

There are two main types of hardware devices that are used by the gateway server. These hardware devices are 

Telephony interface hardware devices. These hardware devices are used to connect the PC on which a gateway server operates to a telephone network. A wide variety of such boards are supported in order to enable connectivity to a variety of hardware devices. Dialogic Corporation manufactures the telephony boards used by the gateway server. The following models of Dialogic hardware are supported 

It is possible to use multiple boards to achieve higher numbers of supported lines within a single chassis. It is also possible in some cases to mix boards of different types.

DSP devices. These devices perform digital signal processing DSP on telephone signals using high performance embedded DSP chips. These devices are required in configurations where a large number of lines need to be handled by the system. Boards from two hardware vendors are supported Analogic Corporation and Brooktrout Technology. The following boards are supported 

Before installing the Dialogic Telephony boards make sure that switches on the board are set correctly. Switches vary from board to board follow the instructions if any corresponding to the board being installed listed below.

All Dialogic telephony boards that are to be installed in the system should be inserted into the machine as per the Quick Install Guide shipped with the boards. The boards must be firmly placed in to the slot. Because the Dialogic boards with the exception of the D 21H are full length boards it is important to ensure that there are no obstructions when inserting the board or else the board might become loose at a later time.

Once the boards have been inserted one must next confirm that each Dialogic board has a unique ID. The ID for each board is set by way of a rotary switch located on the top of the board near the front of the machine into which the board is inserted.

If one has DSP boards they should be installed into the PC in the same manner as the Dialogic Telephony boards and following the directions in the users guide supplied with the DSP board. One will also need to following certain board specific directions when installing DSP boards 

For the Analogic TAP 801 802 check the rotary switches at the bottom of the board near where the board plugs into the ISA bus. There are two small rotary switches that control the I O address of the board. By default this I O address is 0x240 which is specified using a 2 on the first dial and a 4 on the second dial. If one is installing multiple boards he or she must ensure that each board has a unique I O address. 0x250 usually works for the second I O address.

If one is installing DSP boards he or she will also need to install an SCbus cable in order for the system to operate correctly. If one is not using SCbus i.e. using Gatenet 3 then the SCbus cable is not required. One will need an SCbus cable that has at least one drop for each board that is installed in the system. There are several important notes regarding SCbus cables below 

Even if one has a Dialogic board in the system that is not planned to be used one must still connect the SCbus cable. Failing to do so may prevent the Dialogic service from initializing.

Some Analogic TAP 802 boards have a notched SCbus connector that is backwards. In no event should one twist the SCbus cable to fit into this notch If a SCbus cable is in fact notched meaning that one is unable to normally insert it into the connector on the Analogic TAP 802 then a user must either acquire a non notched SCbus cable or remove the notch.

The SCbus cable should run flat across the connectors of all ISA boards in the system. If one is using a PCI DSP board then one will require a longer SCbus cable. However the cable should still be flat there should be no twists in the cable.

Symptoms of an incorrectly connected SCbus cable include not being able to initialize the Dialogic boards even though they are correctly detected and not hearing any audio even though the gateway server answers successfully.

After the hardware boards have been installed and the PC has been restarted it is necessary to install the Dialogic DNA3 drivers in order to verify that the boards are correctly installed and to enable the gateway server to make use of the boards. The following procedure is used to install the Dialogic drivers.

The gateway server operates preferably with Dialogic DNA3 but is not limited to Dialogic DNA3. Previous versions of the Dialogic drivers DNA DNA2 98.02 97.08 or others can be used. The Streams environment is not required in order to install the DNA3 drivers.

First it is necessary to obtain the Dialogic DNA3 drivers. There are several sources from which the Dialogic DNA3 drivers may be obtained 

A CD may be purchased provided with a purchase of the present invention. The Dialogic driver diskette may have accompanied boards if one purchases the hardware separately.

Array Telecom Corp s FTP site at ftp ftp.arraytel.com. The Dialogic DNA3 drivers can be found in the directory Version3 Drivers DNA3 and is supplied under the filename DNA3.zip.

Dialogic Corporation s WWW support site can be access where one will need to follow the links on the web page and provide some information in order to be able to download the DNA3 drivers from the Dialogic web site.

If one downloaded the Dialogic software either from Dialogic one will need to uncompress it into a directory from which one can install it.

After one obtains the Dialogic drivers one will need to run the installation program. If running the installation program manually run SETUP.EXE from the directory containing the Dialogic drivers. If installing from an original Dialogic DNA3 CD the setup program may be started automatically when the Dialogic DNA3 CD is inserted into a CD ROM drive.

A welcome screen appears once the setup program is executed as shown in . Welcome screen contains text concerning general installation parameters as well as Next button and Cancel button . The implementation of these button bullets is well known in the relevant art. A person skilled in the relevant art will recognize these button bullets and their functionality. Button bullets appear throughout the figures which follow and have not always been labeled however their function and implementation conform to those button bullets already labeled and described above.

A user information screen as shown in can appear if the Next button was pressed in the welcome screen . User information window contains user name field and company field as well as Next button Cancel button and Back button .

If one selected custom and selected ISDN one will be prompted to see if ISDN should be installed. If one selected custom one will also need to indicate whether the ISDN Package should be installed. One should answer yes to this question if using the Dialogic D 240SC T1 or Dialogic D 300SC E1 in ISDN mode to connect to telephony equipment or intends to make use of ISDN in the near future and does not wish to reinstall the drivers later. Installing ISDN drivers if ISDN is not in use will not cause problems .

If installing ISDN and connecting to a device that is normally connected to a DMS 100 AT T 4ESS or AT T 5ESS switch select the NT1 protocol. This protocol emulates the network side of an ISDN connection.

Once the installation completes successfully a user will be given the option of viewing the release notes and or running the Dialogic configuration manager. Regardless of whether or not one chooses to read the release notes not necessary in most cases one should choose to run the Dialogic configuration manager.

It is recommended that one not reboot your system immediately after the installation since this is not necessary and one will need to reboot after installing other drivers and software.

Next a dialogic configuration manager screen shown in automatically attempts to detect which boards are installed in a PC. In general boards will be correctly detected providing that they are installed correctly. Screen can show detected boards.

Once boards have been directed a user may need to make configuration changes depending on your system setup. The changes necessary for operation with the gateway server based on a user s board type are as follows. A user may also need other changes depending on the exact environment in which the software is being configured.

If running in Gatenet 3 mode with the Dialogic D 41ESC or D 21H one will need to make changes to the Dialogic configuration. These changes are explained in the next section. Once configuration of the Dialogic drivers is complete the Dialogic service can be started.

It is only necessary to install Gatenet 3 for a low density software only configuration. For hardware DSP processing boards the Gatenet3 must be installed for the software to work correctly.

Dialogic Gatenet 3 is essentially a set of firmware from Dialogic that runs onboard the D 21H and D 41ESC boards. The purpose of the Gatenet 3 package is to provide hardware echo cancellation allowing real time full duplex conversations to take place in an IP Telephony environment.

Installing Gatenet 3 overwrites some files from the Dialogic DNA 3 installation. As with the Dialogic DNA 3 software it is necessary to obtain the Dialogic Gatenet 3 drivers first. These drivers can be obtained from the following locations 

Array Telecom Corp s FTP site at ftp ftp.arraytel.com. The Dialogic DNA3 drivers can be found in the directory Version3 Drivers GN3 and is supplied under the filename GN3.zip.

Once the Dialogic Gatenet 3 drivers are obtained one runs SETUP.EXE in order to install them. One is then greeted with Welcome screen shown in . Welcome screen contains text with general installation information and Next and Cancel buttons.

When a user selects Next he or she may receive a warning screen indicating that the Dialogic Gatenet 3 package overwrites certain files and registry entries and cannot be uninstalled. This means that if a user needs to uninstall Gatenet 3 he or she will be forced to reinstall the Dialogic DNA 3 drivers to have a stable configuration.

A user will next be requested to enter user and company information. Enter this information and click on Next.

The installation options will be confirmed. Verify that the installation options are correct and click next. One should ensure that the directory to which the Dialogic Gatenet 3 drivers are installed matches the directory to which one originally installed the Dialogic DNA 3 drivers. Select Next once the installation options are verified. Setup will then proceed to copy the necessary files.

After optionally reviewing the release notes following a successful installation a user will be given the option of rebooting his or her machine. It is recommended that a machine be rebooted at this time prior to starting the Dialogic service.

After a machine has rebooted one runs the Dialogic Configuration Manager in order to complete the configuration of the Gatenet 3 package. Run the Dialogic Configuration Manager by going to the Start Menu Programs Dialogic System Software DCM.

One can make the following changes using the DCM. The following changes must be made under the properties of each D 21H and or D 41ESC installed in the system 

In addition one should edit gatenet.prm. This file is found by default in C Program Files Dialogic Data. A user may use any standard text editor such as Notepad or Write to make these changes. However the resulting file should be saved in a text format.

Once the above changes are made save the file. One will need to restart the Dialogic service in order for the changes to take effect.

When the Dialogic drivers are installed they are not activated until a user selects to actually start the service. Starting the service also involves verification by the Dialogic drivers that it is possible to start the Dialogic boards.

In order to start the Dialogic drivers use Start Menu Programs Dialogic System Software DCM to start the Dialogic Configuration Manager. If a red button with STOP written in the middle appears in the toolbar then the Dialogic service is already running. Otherwise a Green button should be present in the toolbar which a user can press to start the Dialogic service. Depending on a particular board configuration the Dialogic service can take from between 15 to 60 seconds in order to start.

Once a user has confirmed that the Dialogic service starts correctly he or she may wish to configure it to start automatically whenever the machine starts. In order to do this open the Service menu in the DCM and select Startup mode. One can change the Startup mode between manual and automatic in this menu.

This section will describe an example installation of the Analogic drivers. These drivers are required to support the TAP 801 802 804 DSP boards manufactured by Analogic Corporation.

The Analogic drivers should be installed if the hardware configuration includes Analogic DSP boards. Gatenet3 users can choose not to install Analogic drivers.

The first step in the installation is obtaining the Analogic drivers. One should obtain the correct version of the Analogic drivers. For example one can select the v1.3 drivers.

There are sources from which one can obtain the Analogic drivers a compact disk having v1.3 drivers or Array Telecom Corp s FTP site at ftp ftp.arraytel.com. The Analogic v1.3 drivers can be found in the directory Version3 Drivers Analogic1.3 and is supplied under the filenames TAP H.EXE and TAP D.EXE.

After one has successfully obtained the v1.3 Analogic drivers they may be decompressed so that they can be installed. A CD can contain uncompressed versions of TAP drivers in addition to the compressed version so one does not have to follow these directions if installing from CD.

One should uncompress both the TAP H and TAP D drivers separately. In order to uncompress the TAP H drivers run TAP H.EXE from the location where it was downloaded. One will need to provide the name of a directory to which the TAP H drivers will be decompressed. It is recommended that a user select C TEMP TAP H so that he or she can easily remove the temporary files afterwards. Once a user clicks on OK the files should be uncompressed and ready to use.

If installing from a CD the uncompressed versions of the TAP H and TAP D drivers can be found respectively on the CD. A user can use this in place of C TEMP TAP H and C TEMP TAP D in Steps 3 and 4 below.

After the drivers have been uncompressed one can install the TAP H drivers by running SETUP.EXE from the directory into which he or she uncompressed the TAP H driver. The TAP H driver installs the host libraries necessary for an application such as an example of the present invention software to interact with the DSP board. One should install this driver first before TAP D.

After one runs SETUP.EXE he or she will be greeted with welcome screen as shown in . Welcome screen contains general installation instructions and next back and cancel buttons.

After a user has selected the directory to which the TAP drivers are installed he or she will be asked for the program folder that should be created to hold the TAP H installed programs. A user may accept the default or modify it if a different folder name is preferred.

Following the selection of the folder to which the TAP H drivers are installed the copying of the necessary files will commence. After the copying is complete a user will be advised of the completion and asked to log off and log back on in order for the changes to take effect. Preferably one should not log off since he or she will need to reboot the machine following the installation of the TAP D drivers.

The Analogic TAP H drivers modify environment settings for the currently logged on user. If the gateway server is to be run using a different account the settings made by the TAP H driver will need to be moved from User Variables for to Systems Variables under My Computer Properties Environment. The variables that should be manually copied between the sections are TAP 800 and TAP DIAG DIR .

The TAP D driver is an driver used in addition to TAP H in order to use an Analogic TAP 801 802 804 DSP board. The TAP D driver installs the software to initialize with and communicate with the DSP board. The utilities installed by TAP H are not usually used until TAP D has been installed.

The installation for TAP D is very similar to that for TAP H. SETUP.EXE must be run from the directory to which the TAP D driver was uncompressed. It will prompt a user with welcome screen as shown in . Welcome screen contains general installation information and next back and cancel buttons.

As with TAP H a user will be allowed to select the directory into which the software will be installed. A user should select the same base path as you did for TAP H and click Next. As with TAP H a user will also be allowed to select the folder into which the driver will be installed.

When the installation is completed one will be advised to run drv install and then to reboot the system. One should not follow this procedure precisely since it does not allow one to verify that the board was in fact installed. In order to confirm correct installation of the driver one should follow the procedure below.

If one sees the line above or a line similar to the above it indicates that the board has been located successfully.

After one confirms that the drivers have been correctly installed it is recommended that one reboot his or her system.

This section will describe the installation of the Brooktrout drivers. These drivers support the TR 2001 series of DSP boards manufactured by Brooktrout Technology.

The Brooktrout drivers should be installed if the hardware configuration includes Brooktrout TR 2001 DSP Boards.

The first step in the installation is obtaining the Brooktrout drivers. There are sources from which one can obtain the Brooktrout drivers a compact disk having the Brooktrout drivers.

Array Telecom Corp s FTP site at ftp ftp.arraytel.com. The Brooktrout drivers can be found in the directory Version3 Drivers Brooktrout and is supplied under the filename TR2001.zip.

Run the file TR2001 SDK31.EXE that was obtained in Step 1 above. This will start the installation procedure. The Brooktrout installation will be automatically uncompressed to a temporary location. After this process is complete the setup program will be started automatically.

One will be presented with the option as to where the software should be installed. A user should accept the default location in most cases. After one selects the location to which the software is to be installed the copying process will commence. A series of MS DOS command prompt windows may appear during this process. This is normal.

After the installation is complete a user will be requested to reboot and should reboot his or her computer at this time.

Once the necessary hardware and associated device drivers have been installed a user will be able to proceed with the installation of the present invention software. When installing the software one will be able to install as many instances of the software as one wants. In a fuller example one must have the appropriate numbers of license to actually be able to use the software.

In one example of the present invention software components are all installed from the same installation program. One may select the specific components that are to be installed when the installation program is run. This section will step through the installation of the present invention software and explain the decisions made in the process.

Before a user begins the user obtains the present invention software distribution. Once a user has obtained and uncompressed installation distribution he or she is ready to begin installation. Prior to beginning the actual installation a user should be sure to have the following information available the Customer ID for an organization the Product ID and the License Keys corresponding to the software that is licensed.

From a directory containing the uncompressed installation distribution run a program SETUP.EXE. This will commence the installation process. One will be greeted with welcome screen shown in . Welcome screen contains general installation information and next and cancel buttons.

Following welcome screen one is greeted by information screen that requires one to enter information about him or herself his or her company and information on a license sheet. Information screen is shown in .

After the information screen one will be given a choice of setup types. Two options will be presented complete and custom. displays the installation option screen where these options are displayed in a panel. Complete will install all components of the present invention software on the local machine. Custom will allow the user to select which components should be locally installed. Generally unless one is setting up a test environment it is best to select the components of the software that one will actually require or use.

Gatenet 3 Select this option if one is using only Dialogic D 21H or D 41ESC boards and has the Gatenet 3 package installed.

Brooktrout TR 2001 Select this option if one is using any of the family of Brooktrout TR 2001 boards.

After selecting a DSP configuration one will be asked for a program folder to install the software to. Once the software has been installed one will be able to access it in this folder. Normally the default folder is acceptable. Once a user clicks Next the copy process will begin. displays the installation of a startup menu group in setup and installation screen .

Once the copy process is completed a user will be given the option of viewing a readme file that accompanies the software. This file will usually contain the most up to date information about the software.

It is not necessary to reboot a machine after installing the present invention software. Once the software has been successfully installed a user is ready to move on to the configuration of the present invention software.

This section describes an Express Configuration ExpressConfig program. ExpressConfig can be used to generate an initial configuration for present invention software. It should be used when the software is first installed or when the software needs to be completely reset since it will replace all configuration data. Any configuration changes made prior to running ExpressConfig may be lost.

ExpressConfig performs configuration of the gateway server routing server and database server components of the present invention. It is capable of performing any or all of these components when it is run so it is possible to reset and configure the database server without affecting the configuration of the gateway server or of the routing server. Nonetheless it is necessary to exercise care when running ExpressConfig to ensure that configuration is not unintentionally overwritten.

The ExpressConfig program is divided into three main sections corresponding to different components of the present invention that can be configured. There are some aspects of configuration that are common to all three components that are set up using ExpressConfig these common aspects are discussed in the next section.

With all components there are three possible options with respect to how ExpressConfig will operate on that component. The three choices are presented to the user in the gateway server screen of the ExpressConfig screen shown in .

An inset panel displays the available installation options. Not all of the choices may be shown if one is installing for the first time. An explanation of the choices follows 

Once a user decides which of the above is appropriate he or she can proceed to entering the actual configuration information.

Note that ExpressConfig is a local utility. One cannot use it to remotely configure components located on different machines. This can be accomplished using the management system after the present invention has been installed and set up using ExpressConfig.

This section describes the setup information that is common across the gateway server routing server and database server. The setup information described in this setup pertains to common things such as identification security and management. As described above ExpressConfig will step through a sequence of information screens. The following are the common information screens that a user can interact with for all three components.

An identification panel is used to configure identification and authentication information that will be used by a particular component to verify the entities that connect to it and use its services. Although in principle a user could configure a complete list of all entities on each component in practice this is not necessary. The following list shows for each component what kinds of entities will connect to it and use its services 

With the above list in mind it is only necessary to configure identification authentication information for the entities that will connect to the component that you are configuring. For example when configuring identification authentication information for a gateway server a user need only enter identification authentication information for any management systems that may connect.

When setting up identification authentication information using ExpressConfig it is very important that a user at a minimum provide a configuration that allows for a management system to connect. Otherwise one will may be able subsequently to connect using the management system in order to modify the configuration of the system and may be forced to re run ExpressConfig. shows the identification screen in ExpressConfig.

The Security Domain Settings panel contains a security domain name field a server identity field a listing window of current security domain members and a sub panel for adding additional security domain members.

Specifically the first two parameters a user needs to supply are Security Domain Name and Server Identity. In essence one is naming the security domain that the server will be a member of and is providing the name identity of the server within that domain. The name of the security domain will need to match the name of the security domain of the entities that the server being set up will interact with. For example if one were setting up a gateway server that was managed by a management system in domain TESTDOMAIN and which connected to a routing server in domain TESTDOMAIN then one must use the same domain name TESTDOMAIN. The identity that one gives the server within the domain should be unique. Any components that the server being configured connects to will need to have identification authentication for the identity that one assigns the server.

Once a user has decided on the security domain name and the identity of the server being set up within that domain one will need to provide identification authentication information for the other members of the domain. As mentioned above one only needs to provide this information for entities that make use of the services provided by the server being set up. In order to add to the list of identities that can be identified and authenticated enter the member name and IP address in the boxes provided in a panel or other GUI input. A new entry will appear in the list in the middle of the panel. To remove one of the entries simply select it and click Remove. The principles behind this process are explained in more detail in the next section when the identification authentication model is elaborated upon. Advanced features identity wildcarding the use of netmasks are also explained in the next section.

The Management access control list is reasonably simple because ability to manage is a binary ability all nodes identified on the list are capable of managing and any node not identified will not be allowed to perform any management functions. The means of adding and removing from the management access control list is similar to the identification authentication list. To add a new entry enter the member name of the node that is to be added and click on the Add button. Similarly to remove an entry select the entry and click on Remove. It is assumed during ExpressConfig that any member a user adds will be in the security domain configured during the identification authentication step of the ExpressConfig process.

In one example components of the present invention require licenses in order to provide services. The use of license keys allows one to ensure that he or she is always in compliance with his or her license agreement and that use of the software does not exceed the licenses that have been purchased. During ExpressConfig a user can add license information and an initial license key. A user may add additional license keys as he or she purchases them.

In one example although licensing information can be configured on all of the gateway server routing server and database server only the gateway server actually makes use of licensing information. However licensing capabilities are included on all of the servers to ensure flexibility in creating licensing arrangements that meet customer requirements.

After a user has entered the basic identification information he or she enters licensing information into licensing information panel . There are two modes in which licensing can function. The first is standalone mode where keys are locally configured on each server. If operating in this mode then enter the license key supplied with the system. If on the other hand one is operating in client server mode he or she provides the IP address of a primary license server and a secondary license server if any . More information on setting up licensing is contained in the next section.

This section describes the setup that is specific to the gateway server component of the software. There are three panels used to configure gateway server specific configuration data.

The hardware setup panel provides a user with the means to quickly setup the hardware configuration of the system. It automatically creates configuration entries for the hardware devices were selected and creates matching lines and line groups explained in more detail in Section 5 based on selections.

If the Dialogic boards are being used in the same chassis as a gateway server with an application other than the gateway server the board number that is opened following ExpressConfig completion. ExpressConfig uses boards starting from 1 and progressing upwards.

The DSP configuration of panel is selected by picking one of the three available DSP options. One must select the DSP configuration that corresponds to the version of the software that is installed and to the hardware configuration of an actual system.

For the installed hardware device list of panel there are a number of hardware devices listed. In front of each device there is an editable field showing how many devices of that type are assumed to be present. One needs to fill in the numbers of each device that are present in the system. Note that one may not be able to select Gatenet 3 mode D 41ESCs and D 21Hs if it was indicated that a hardware DSP board based configuration is used. Similarly a user can only select quantities of the above boards if a user selected a Gatenet 3 DSP configuration.

Additionally a user must indicate the type of installed MSI SC boards if any as well as whether the D 240SC T1 boards are configured in robbed bit mode or ISDN PRI mode. A user s selection matches the actual hardware configuration of the machine and the configuration of the Dialogic drivers performed in previous steps. If a user does not install any MSI SC boards or D 240SC T1 boards then the respective settings can be ignored.

A call routing panel is used to allow one to configure the list of routing servers that the gateway server being configured will access in order to obtain routes. There are numerous settings that can be used to customize how a gateway server interacts with a routing server the default values are used for any servers set up during ExpressConfig. Furthermore significant local routing information can be set up on the local Gateway however this information if any should be entered using the management system. A Call Routing page shows a standard list. shows call routing screen . Call Routing screen contains a routing server list panel . In order to add a new routing server to the list enter a name for the routing server provide its hostname or IP address and click on the Add button. To remove a configured routing server select it in the list and click the Remove button.

The database access screen is shown in . The database access screen contains a Database Server List Panel . The Database Server List Panel allows one to set up the list of database servers to which the gateway server being configured will connect. This page is identical to the Call Routing page described above except that it is database servers being set up. In addition ExpressConfig will create default settings for the database services user management CDR collection based on the servers that you configure.

The routing server has a single unique panel in its configuration which is the client setup panel used to configure the list of clients that will be allowed to connect to and use the services of the routing server. The client setup panel is shown in . As mentioned previously these clients are gateway servers however other systems designed to obtain similar information can be connected through this configuration panel.

The setup of the routing servers client access control list is identical to setting up the management access control list. Gateway servers listed in the client access control list will be able to connect to the routing server export routes query for available routes and receive disseminated routes. The exact permissions of a particular client can be modified on a client by client basis using the management system.

There are two panels of information that need to be set up using ExpressConfig for the database server. These panels are Client Setup and Server Login Setup and are described below.

Client setup for the database server is identical to the setup of the client access list for the routing server described above. Just as with the routing server the database server client access list can be manipulated at a later time using the management system.

There are four key pieces of information that are used. The first is the Database Source Name DSN . One creates an ODBC data source using Start Control Panel ODBC with the corresponding name prior to actually running the database server. One follows the directions below in the section on Database Table Setup to ensure that the database is setup with the appropriate tables. Although a user does not need to do this prior to running ExpressConfig it should be done prior to running the database server.

When supplying a DSN in order to allow the database server to connect to the database it may also be necessary to specify login credentials a username and password that are required to access the database. If a username and password are required then a user should enter them in the supplied fields. Finally a user should supply the name of a log file that will be used to record problems in interacting with the underlying database.

If a user will be using the database server component of the present invention software it is necessary to ensure that the underlying database is correctly configured prior to starting the database server. There are three ways that a database can be configured for operation with the database server 

The database tables can be created and configured manually using the schemas provided in Appendix A. This is not preferred unless a user intends to modify an existing database to fit the schema provided in Appendix A.

For example if one is running Microsoft Access a user can use an empty database file that contains all the required tables with no initial data in them. The database file can be installed as part of the installation of the database server or located on a CD in uncompressed form. The present invention is not limited to this database format.

In another example if a user is running Microsoft SQL Server he or she can use a utility installed with the database server. This utility will connect to the specified data source and create the necessary tables. One may use this utility by running setupSQLDB.exe from the directory to which the database server was installed or by running an execution program from a CD. The present invention is not limited to this database server.

This section describes additional setup instructions that should be followed to ensure maximal performance of the present invention in one example implementation.

PCs contain a number of screen savers that can be enabled after a certain period of inactivity. However it should be noted that some of these screen savers can utilize 100 of the available CPU resources since they perform complex graphical rendering. It is recommended that the screen saver be disabled on machines running the present invention software or that a simple non 3D screensaver be selected.

The present invention software runs at elevated priority to handle excessive CPU use by lower priority processes. However it is still recommended that care be taken not to overload the machine running present invention software with other applications unless the performance of the present invention software on that machine is not critical e.g. management system .

Microsoft Office by default installs a file indexer called Find Fast. This allows you to quickly locate Office documents. However it periodically indexes the entire hard drive which can degrade the performance of the entire system while it is running. See the above note regarding CPU utilization under screen savers.

The same is true for Virus Scanners which may be configured to periodically read all files on the hard disk scanning them for viruses.

This section explains how to get present invention system up and running once the basic installation and setup described in the previous section has been completed. In this section one will learn how to start the system and use the management and provisioning systems to interface with the system. One will also learn how to perform operations that are common across different components of the present invention software such as configuring security and management access control.

Control Panel Shows how a Control Panel can be used to monitor and interact with the operational components.

Using the Management System Explains the basic principles necessary to use the management system to interact with a running operational component.

Service Control and Logging Shows how to use the management system to control an operational components service state and how to view and log events generated by that operational component.

Security Domain Configuration Explains how to manipulate the security domain settings for an operational component.

Management Access Describes how management access to a particular operational component can be restricted so as to prevent unauthorized access and modification.

Licensing Covers how licensing works and how license keys can be entered and used with present invention software components.

Using the Provisioning System Explains the use of the provisioning system to interact with data managed by the database server.

Troubleshooting Service Startup In the event that a service cannot be started explains possible causes.

The first step in using the present invention software is to start it. In a Microsoft Windows operating system example once the present invention software is correctly installed a program group can be found under the Windows Start menu containing all present invention software components. From this entry in a start menu one can choose which components to start. is a screenshot of screen and contains an exemplary start menu programs menu . Start menu programs menu contains links to the software of the present invention.

In order to get started one will generally need to run at least two components one operational component such as the gateway server plus the management system which is used to connect to the operational component in order to monitor and administer it.

Once started the operational component will display a small icon in the system tray. Through this icon one can perform very simple operations such as starting and stopping the service provided by the operational component that is running. The small letter in the upper left corner the icon indicates which operational component is being interacted with G represent the gateway server R the routing server and D the database server. Right clicking on the icon will bring up a small popup menu. From this popup menu one will be able to see the about dialog which displays program version information. One will also be presented with the ability to start or stop the service unless the service is already starting or stopping. One can use the Close item to terminate the service completely. Once terminated a service cannot be interacted with in any way until it is started up again. is a screenshot of the service menu popup menu .

Based on the ExpressConfig process that one went through one should be able to load all of the operational components that one configured and use the icon in the system tray to start those services. The state of a service is indicated by the color of its icon. Red represents a stopped service yellow represents a service that is either starting or stopping and green represents a service that is started. If one chooses to start a service and the service fails to start then the color of the icon will return to red. This indicates a configuration error that one will need to correct using the management system prior to being able to start the service. The last section in this section explains how one can troubleshoot such a condition.

When the Control Panel is started a Control Panel screen is provided as shown in . The Control Panel screen provides a means of interacting with locally running operational components without having to go through the Management System . It is provided for convenience and has only limited capabilities for interacting with the operational components. It is capable of interacting with the Gateway Server s Routing Server and Database Server . The Control Panel is started the same way as other present invention components using Start Programs present invention Control Panel.

Tabs along the top of the screen allow one to select which component s panel one wishes to interface with. For example the gateway server tab is shown. This tab contains sub panels for starting and stopping gateway servers configuring service levels and showing event logs.

Connect This button will connect to the service assuming that it is running. If the service is not running then one will not be able to connect successfully. Interacting with a component requires that one first connect to that component.

Start Stop Once one is connected one will have the option to start or stop the service unless it is starting stopping already .

In addition to these controls one will also be provided with diagnostic messages generated by the operational component that one has selected once one has connected to it. These diagnostic messages are used to indicate information that can be useful in determining whether or not the system is functioning correctly. Underneath the event log window which displays these diagnostic messages one will also have several controls that allow one to control the display of these messages. Pressing the Clear button will remove all messages currently displayed in the event log window. Pressing Lock Display will prevent any new messages from being added until one press Unlock Display which appears only when the display is locked . This allows one to read a particular set of events in more detail without worrying that they will be repositioned or disappear because of new events that occur. New events will be collected while the display is locked but one will be able to scroll up and down through the existing events. Finally a message level selector allows one to choose what level of events one are interested in. The lower the level selected the more messages will be displayed

At the bottom of the interface service specific information will be displayed. The information displayed is service dependent and is as follows 

Gateway Server A list of the current sessions is displayed showing the lines that have active calls and the services that are active on those lines.

Routing Server A list of the connected clients gateway servers is displayed along with their IP addresses and connect times. This window is useful for determining whether or not a gateway server is actually able to connect.

Database Server A list of the connected clients either gateway servers or provisioning systems is displayed. The IP address and time of connection is displayed. As with the routing server this is useful for determining if gateway servers are actually able to connect to the database server.

This section introduces the management system used to perform all administrative and management aspects of running an present invention network. The concept of how management is performed was discussed above in this section how to apply those concepts in order to actually manage operational components is discussed.

The management system is a Microsoft Windows GUI application used to connect to and administer operational components of the system. In a Windows example it can be started once the present invention software is installed using Start Programs present invention Management system.

Once one has started the management system one will need to do two things in order to be able to use it to manage your network. Each of these steps is described below.

Security Domain Configuration. Security domains are configured during ExpressConfig for each operational component that one configured. In order for a management system to connect to an operational component it must share a common security domain with that operational component. In addition from a security domain standpoint it is also necessary that the operational component be able to authenticate the management system as a valid member of that domain.

In order to configure the identity of the management system within a security domain one should select the Security item from a Local Identification menu. This will bring up the Security Domain Configuration screen as shown in . From this screen one can list the security domains that the management system is part of.

Clicking on the Add button contained in the Security Domain Configuration screen will allow a new security domain to be added. When adding a security domain the only relevant information is the Domain Name and the Member Name within that domain. Other fields are not required although one can provide a description for future reference.

In order to change a domain it is necessary to first remove the existing domain and a new domain with the same name. The only reason to do this would be to change the member name of the management system within that domain. This is not frequently required. Selecting a particular security domain will provide additional information about that security domain.

It is possible to configure multiple security domains on a given management system. However each security domain must have a unique name. It is not generally necessary to do this unless a particular management system needs to configure operational components located in different security domains.

A management system is capable of administering numerous remote systems. In order to facilitate this process without needing to enter addressing information for a system each time it is necessary to manage that system the management system maintains a remote system list that is permanently stored. The remote system list appears by default on the left side of the management system window and shows all remote systems that have been entered.

There are several ways to manipulate the remote system list. The first is through the Remote Systems menu. When this menu is selected the following additional items appear 

Add New System Upon selecting this option one will be provided with a dialog panel as shown in . This provides a Server Settings panel for creating a new system in the remote system list. The dialog panel needs to be used to add each operational component that will be managed from the management system.

One needs to provide the necessary information in this dialog that pertains to the system being added. The fields required in one example are as follows 

System Name An identifying name for the system that is being added. This name is for local identification purposes only and does not have any impact on connecting to and or managing the remote system being configured. It does not need to match and is in no way related to a member name within a security domain. However it may be easiest to use a nodes security domain member name in this field.

Port Number UDP IP port number that the server is running on. You should normally accept the default setting which is filled in automatically when you select the correct system type.

Description This field allows you to enter arbitrary text that will help to identify this system. It is not required but can be used to record information for reference purposes e.g. Located in New York USA .

Once a user clicks on OK the new remote system will be added and will appear in the remote system list.

The second way of performing these commands is by using the mouse by right clicking in the remote systems list. If one right clicks on a remote system one will be able to connect disconnect from it view its properties or remove it. If one right clicks an empty area in the remote systems list one will be given the option to add a new remote system.

Once one has configured at least one entry in the remote systems list corresponding to the operational component s that one wishes to administer one will need to connect to the operational component. One can do so by issuing the connect command as described above or simply by double clicking on the remote system to which one wishes to connect.

Once connected an additional tree of options will appear beneath the remote system that a user connected to in the remote system list. This tree will allow a user to navigate between the options that are available to configure. The exact makeup of this tree varies from one type of component to the next and also depends on the configuration of a particular operational component.

If one has difficulty connecting to the remote system there are several possible causes. Regardless of the cause a message box will appear indicating that a connection to the remote system could not be established.

If this dialog appears immediately then the remote system that you are trying to administer was contacted but it rejected your attempt to connect to it. This is due to one of two reasons 

A user could not be identified and authenticated by the remote system. A user should check the security domain name and member name of the management system in order to ensure that they are correct. Then a user should confirm that the remote system that he or she is trying to administer is in the same security domain and that the security domain on that remote system is capable of authenticating the user. This process is explained in the section below Security Domain Configuration. As long as a user entered the member name and IP address of the management system when using ExpressConfig this should be taken care of.

The management system was identified and authenticated however it had no entry in the management client access list. Configuring the management client access list of an operational node is discussed in the sections below however as long as the member name of the management system was entered during ExpressConfig it will have an entry in the management access list.

If this dialog takes several seconds to appear then the remote system could most likely not be contacted. This may be due to an error in the IP address of the remote system a temporary network failure or a firewall that is blocking traffic. It may also be caused if the operational component that a user is trying to connect to is not running or if a user selected the wrong type of system when setting up the remote system entry in the remote system list.

The Remote System List window in is in expanding tree view form and shows the remote system list after a connection has been established and the connected node has been expanded. The tree view is navigated in the same way as a tree view presented by many file system viewing applications. Nodes in the tree can be expanded and collapsed by clicking in the boxes beside them. Nodes with a in the box beside them can be expanded. Nodes with a beside them can be collapsed or else do not have any nodes beneath them. Double clicking on the label for a node will bring up a window corresponding to that node the contents depend on which node was selected . Changes to configuration are made using the windows that appear. Future sections describe in detail how to interact with individual components using the management system.

When one uses the management system to connect to an operational component one screen will automatically appear. This screen is the Service Manager screen as shown in . The Service Manager screen is present on all operational components. It contains a Service Status panel an Event Logging panel and a Message field and list window.

First the service state can be modified by either starting or stopping the service assuming that the service is not already in the state of starting or stopping. The current service state is also indicated. Clicking on Start Stop will cause the service to be started or stopped respectively.

Event logging can also be configured from the Service Manager. Clicking on Event Log will bring up the event logging configuration dialog as shown in . Event logging allows events to be logged to disk for subsequent review. Event logging incorporates a circular logging feature that allows the amount of disk space consumed by the log to be managed. An event logging configuration panel allows one to enable or disable the logging of events to disk. Normally logging events to disk is unnecessary unless one is trying to diagnose a problem. If one enables event logging he or she will have the following options 

Debug Level. Selects the level of events that will be logged to disk. Any events that are of a lower level than the level selected will not be stored in the log. This can help to only log events of the relevant level to disk so as to maximize the amount of useful information in the log file.

Maximum File Length. Log files are circular once a particular log file fills up the next log file in sequence will be truncated to zero length and used to store log information until it too is full. The maximum file length parameter is used to control how full a log file is allowed to get before the next log file in the sequence will be used.

Log File List. This list provides the names of the log files that will be used to record events. These log files will be used in a circular pattern using the process described above. One can use the Add Remove buttons to add or remove log files from the list or can set the current log file i.e. the log file into which the next event will be placed by clicking on the Set Current button. Normally the default log filenames will be sufficient.

Clicking OK will make changes to logging configuration permanent pressing Cancel will abort any changes that one made.

Finally the Service Manager window provides a means to monitor events that occur on a particular operational component. Any events that occur on the operational component that is currently connected to will be displayed in the window. However events may be filtered by priority level. The default debug level can be used to control what level of events will be displayed. It is not normally necessary to view debug events and since each message consumes bandwidth it is generally sufficient to leave the debug level on the default setting of only displaying warning level events or higher. The Advanced button allows one to configure event display levels on a type by type basis and is only required for advanced diagnostics. Finally two buttons are provided in order to clear and lock unlock the display.

One of the concepts explained herein is that of security domains. The concept of a security domain is central to understanding how identification and authentication operate in an present invention network.

Nodes in an present invention network need to be in a common security domain in order to exchange services. In order for two nodes in the same security domain to be able to authenticate each other they need to have authentication information that allows them to authenticate each other. There are many possible forms that could be used for the exchange of authentication such as a password. The present invention software is constructed so as to support a variety of methods for identification and authentication. However at this time only a single model for authentication based on member lists is supported.

Security domain names and member names within a security domain are case sensitive. It is imperative that attention be paid to case when entering security domain names and member names.

From the management system a top level node in the tree of the gateway server routing server and database server is the Security and Identification node. Double clicking this node will bring up the Security and Identification screen . shows this setup screen. From this page one can interact with the Security Domains panel and configure the operational component that is being managed. The Security Domains panel contains an expanding tree view window and buttons for adding a domain adding a member removing either a domain or a member and a properties button for displaying the properties of a selected domain or member. A detailed description of these buttons follows.

In a memberlist domain authentication checking is performed by way of a static list of members and corresponding IP addressing information. When a node providing some service receives a new connection requesting access to that service it will check the identity of the requesting node and determine if the IP address of the requesting node matches the corresponding entry in the database. If there is a match then the identity of the requesting node will be accepted. Otherwise the identity will be rejected and the connection will progress as if the requesting node had no identity. Normally this would result in a denial of access to the resource .

In it can be seen that a security domain can be expanded by clicking on the next to the name of the domain. Expanding the domain causes the members of the domain to be shown. The Add Member and Remove buttons can be used to add and remove members from the member list. Clicking on Properties allows the settings for a member of the domain to be configured.

When a new member is added or an existing member is edited Properties screen will appear. shows the Properties screen that is displayed when a new member is added or an existing member is edited. This screen contains two panels .

In the Identification panel is shown. Three settings can be configured for a member of a security domain. The first is the name of the member. When a request is received from a remote node it will present its name. The name that is configured in this dialog must match the name presented by the remote system when it connects. The second piece of information required is the privilege class to be assigned to the remote system. Privilege classes are not currently used by existing components in the software so using the default value of zero suffices. The third field is a description of the node. This is purely for informational and reference purposes and does not affect the functioning of the software in any way.

Once these basic settings have been completed Addresses panel can be displayed. It allows the IP address authentication information to be configured. The Addresses panel is shown in .

In Addresses panel a user can configure a list of IP addresses from which the named member of the domain will be allowed to connect. If the IP address from which the member connects is not within one of the ranges specified in the list then the identity of the connecting member will be rejected. The list of addresses is manipulated in the usual fashion. Each entry in the list has three pieces of information 

 2 The netmask controlling which IP addresses can be connected from. For example if the IP address field is 192.168.1.33 and the netmask is 255.255.255.0 then connections will be accepted from 192.168.1.0 through 192.168.1.255 

 3 The port number from which the member is allowed to connect. The default value of zero allows a connection from any port and should be used unless it is necessary to override this setting.

Note that multiple address ranges may be configured. It is only necessary for a connecting member to match one of these address ranges in order to be accepted. Thus if the same name is assigned for convenience to two management system nodes one IP address entry could be entered for each node allowing them both to identify themselves as the authorized management system.

It is possible to enter a asterisk for the name of a domain member. If such a wildcard entry exists and no other entries in the list matches the member name presented by a connecting node then if the addressing information for the wildcard entry matches that of the connecting node the identity of the remote node will be accepted as valid. For example configuring an entry with a name and an IP address 192.168.1.0 netmask 255.255.255.0 would allow all nodes from 192.168.1.0 through 192.168.1.255 to connect and their identities to be accepted no matter what is presented.

In addition to configuring the identification and authentication information on a particular operational component to have administration by a remote node access should be granted to the services provided by that operational component. This section describes how to configure access to the Management server built into each operational component.

All operational components have a root level node in their configuration trees titled Management Access. Double clicking on this node will bring up a Management Access dialog. This dialog presents the list of nodes that currently have management access. For each entry in the list the name of the entry description of the entry identification corresponding to the entry and current status of the entry are shown. The status simply shows whether or not management is current enabled for that entry. Entries in the list are called clients in effect they are clients of the internal management server of each operational component. These clients are the management systems that are authorized to connect. shows Management Access screen .

When a new entry is added to the Management Access List within Management Access screen or an existing entry is modified the Client Configuration screen shown in is displayed. This dialog allows properties to be set up for an entry in the management access list. In the dialog of it is possible to configure the General panel and Identities panel . In the General panel the first is the name of the access entry. This name is for informational and logging purposes but must be unique. The second is a description of this entry which is also for informational purposes only. A flag allows an entry to be temporarily disabled. If this flag is set then management systems with an identification matched by this access entry will not be allowed to manipulate the management system.

In the Identities panel a list of identities that is accepted for this management access entry can be configured. The purpose of this list is to specify those nodes that are able to access the management system using this access entry. This list enables multiple distinct remote identities to share a single client configuration. The purpose of this is mainly for future expansion. For example if a management access entry was extended to support the configuration of exactly which screens could be accessed it would be tedious to duplicate this configuration for each management system that needed to be configured. Therefore allowing multiple identities allows the access entry to be shared amongst multiple management systems.

When new identities are added or existing identities are modified a security identification dialog pops up allowing a user to enter the identity being added or modified. The Security Identification screen is shown in .

In the Security Identification panel of the screen the type allows a user to select whether the identity being configured is a remote node or a security group. Security groups are not presently accessible directly by the user so foreign entity should generally be selected. In addition a user should specify the domain name and member name which comprise the identity of the connecting node. The domain name may be selected from one of the security domains that is configured on the operational component that the management system is connected to and the member name should match the name of a member that can be authenticated using the authentication information discussed in the previous section. In addition it is possible to wildcard the member name by entering a single asterisk which allows any valid member of the domain to be recognized under this access entry. Lastly a minimum privilege level can be configured in which case the requesting node must have this level of privilege or higher in order to be granted access. Privilege levels are configured for each domain member when setting up a security domain.

The software licensing model used by present invention components has been described hereinabove. This present section provides further details on how to setup software license keys and elaborates on standalone and client server modes of operation so that it is possible to select the correct choice for a given configuration. Each of the two licensing models and how to configure the software for operation under either of those two models is given below. In one example only the gateway server requires license keys to be entered. However the process for managing licenses is common to all present invention software components that require licensing and in alternative embodiments of the invention can apply in different licensing models.

Regardless of the mode of operation selected for licenses an operational component that uses licensing can have a top level management tree node named Licensing. Double clicking on this node will bring up a License Manager screen as shown in . This screen contains a License Manager Setting panel and a List of encrypted license keys panel .

There are several common pieces of information that are used regardless of the licensing mode actually in use. The ExpressConfig program normally fills in these fields but it may be possible to change these fields at some point. Any changes to the configuration of the License Manager can only be performed by clicking Change Settings button in the License Manager Setting panel and making changes using the dialog that appears. The common settings are as follows 

Mode. This allows the License Manager to be changed in terms of its mode of operation. A user should select the value for this parameter first since certain parameters cannot be edited unless a user is in a particular licensing mode.

Customer ID. A user must enter the customer ID assigned to his or her organization in this field. Each license key issued is keyed to a customer ID. This information is normally printed on a software license certificate issued when a user purchased the software.

Product ID. The product ID is a serial number which identifies the product. Each license key issued is keyed to a Product ID and will only work with this product ID. Like the customer ID the product ID is printed on a software license certificate.

The remaining settings are determined by the licensing mode that a user selects. Each of the available licensing modes is discussed in the following subsections.

In standalone mode all licensing on a particular node in the system is performed independently of all other nodes. All license information required by that node is held locally. In standalone mode each node should have its own hardware dongle in order to decrypt license keys.

License keys can be added and removed from the main License Manager window. This option is provided once standalone has been selected as the mode of operation. A user should select standalone operation and then accept the changes prior to being allowed to enter license keys. Two simple buttons Add and Remove allow a user to add and remove license keys. When a user clicks Add and enters a license key the license key will be verified and it will either be accepted or denied. If it is accepted it will appear in a License Manager window and information associated with that license key will be display. If however it is denied it will not be recorded. If a license key is repeatedly denied then a user should check the following 

Ensure that the license key is typed in exactly as issued. There are no brackets apostrophes or quotation marks in the license keys themselves so if a license key is provided within such delimiters a user should not type them in when entering the license key. For example if an E mail reads 

Case is significant when dealing with license keys. Therefore ABCDEFG1234567 should not be typed in as abcdefg1234567.

Ensure that the customer ID that a user has entered is correct and matches the customer ID on the license certificate or otherwise issued to the user the customer ID may not always be printed on the certificate depending on the restrictions on the key but can generally be found there .

Ensure that the product ID that a user has entered is correct and matches the product ID on the license certificate or otherwise issued to the user. As above the product ID may not always be printed on the certificate .

If a hardware dongle is used hardware dongles are generally used time limited demonstration keys may not use a hardware dongle one must ensure that the dongle is correctly connected to the computer and that it is connected to the correct kind of port on the computer.

If using a limited license restricted to a particular IP address ensure that the IP address of the machine that a user is installing on matches the IP address used to issue the license key.

License keys are time limited and may have expired. Ensure that the system time and date are accurately set and that the license key being entered is presently valid.

In client mode a centralized license server determines the licenses available to a particular operational component a client of the license server . This mode of licensing is suitable in environments where a number of operational components are owned and operated by a single organization. It reduces the necessary administration since licenses can be acquired for multiple operational components and centrally configured rather than needing to enter license keys on each individual node. However license keys issued for use by a license server can only be used by a license server and thus any operational node that no longer operates with the license server will be unlicensed and unable to provide services. For example an organization deploying numerous gateway servers in different areas would benefit from the use of a license server. However if those gateway servers were independently owned and operated the gateway server owners may not want to use a license server. This is since their licenses would effectively be pooled and would not be separable should a gateway server owner decide to leave the association.

Operation in client server mode requires the presence of at least one centralized license server. In addition it is possible to configure a backup server so that if the primary server becomes temporarily inoperable due to hardware or software failure the nodes in the network continue to operate. Setting up the license server is discussed in further detail below. This section deals exclusively with configuring the License Manager and assumes that a primary license server and a secondary license server if required already exists and is running.

Once the licensing mode is changed to Client Server Mode a number of fields must be filled in. These fields are the primary IP address secondary IP address primary port number and secondary port number. The primary IP address and primary port number are mandatory and must be filled in with the IP address and port number of the primary license server. The port number of the license server should be left as the default 6797 unless a user is specifically running the license server on a different port number . The secondary IP address and port are optional and should be filled in with the IP address and port number of the secondary license server if available and 0.0.0.0 port 6797 otherwise.

The provisioning system described above is used specifically for the management of data in the database servers. This section introduces the provisioning system and provides basic information on how to use the provisioning system. The functionality offered by the provisioning system and how to use this functionality is described further below when User Management and CDR Collection via the database server is discussed in detail.

The provisioning system is started in a similar way to the management system using Start Programs Present Invention Provisioning system. Before the provisioning system starts it will require the selection of what type of records will be modified. When starting the provisioning system for the first time simply select User Records. 

The first step in configuring the provisioning system to connect to a database server is to configure its identification information. This process is similar to the process used when setting up the management system. To access the identification configuration of the provisioning system select Security from the Connection menu. A user will be presented with a security domain configuration dialog identical to the one presented by the management system. Use this dialog to enter information about a user s security domain in the same way as for the management system.

Once a user has configured the security domain settings for the provisioning system the next task is to configure the list of database servers with which the provisioning system interfaces. The list of servers is available by selecting List of Remote Servers Available on the Connection menu. An Address Book is shown in with a database servers Address Book panel which lists the remote servers available. The Current Server panel shows the name of the server currently selected.

Database servers can be added and removed from the list of available servers using the Add and Remove button within the database servers Address Book panel . The IP address and port number is required for any database server that a user wishes to add. A user may also change the IP address and port number for database servers that have already been configured. Also one needs to ensure that the identity of the provisioning system is in the client list on the database server or it will not be allowed to connect.

With the provisioning system one of the database servers available should be designated as the active server. The active server will be used to process all requests made through the provisioning system. If a user changes the active server he or she should close any active session and open a new session in order to perform operations. Unlike the management systems the service should be started on the database server before the provisioning system will be able to connect.

Once a database server list and active database server have been configured a user should be able to use the provisioning system to interact with data in the database. By selecting New Session from the file menu and selecting the kind of session that one wishes to create one can establish a connection to the database server and can issue requests and manipulate data. How to use the provisioning system to do so depends however on the type of session and the operations that are being performed. Performing these operations are described in detail in later sections.

This section provides summary information about the possible causes that can prevent a service from starting correctly. First it is necessary to differentiate between not running and not starting. If an operational component cannot run then it will fail to load and no icon will be displayed in the system tray. Possible causes for failing to run are 

Once a service is running there are very few things that could possible prevent it from starting. Failing to start is characterized by a red icon appearing in the system tray and turning yellow while it is attempted to start the service but returning to the red stopped state without turning green. The causes for a failure to start the service depend on the type of service.

There are no known reasons why the Gateway Service would fail to start. Even if hardware devices fail to initialize the Gateway Service should initialize nonetheless.

The Routing Service should start successfully in all cases. There are no known causes that can prevent the routing service from starting successfully.

The Database Service may fail to start in the event that a connection to an ODBC database cannot be established. If this is the case then the management system should be used to correct the ODBC connection information and the service startup should be retried.

This section provides an introduction to the gateway server a component in an present invention network. In one example the gateway server is the largest and most complex component of the present invention software and is the component which brings together the functionality offers by various components of the system and actually makes that functionality available to the end users of the system.

The material in this section is divided into several sections. A brief description of these sections is as follows.

Hardware Support. The present invention gateway server is designed to interact with a variety of underlying hardware in order to support a diverse range of technology for interconnection to traditional telecommunications networks. Because of this configuring hardware support in the software can be complex and is explained in detail in this section. Normally this process is not necessary but information is provided for reference purposes.

Lines and Line Groups. Each line connecting the gateway server to the telecommunications network as well as lines connecting the gateway server to other gateway servers need to be configured. In addition to simplify administration lines are grouped into line groups which allow certain properties to be configured on a number of lines. This section explains lines and line groups and how to perform configuration operations on them.

Services. At the heart of the gateway server is the services that it provides to the end users. The gateway server has an extremely flexible architecture that allows services to be seamlessly integrated with the system added and removed and routed between. An API even allows the development of custom applications that operate with the gateway server. This section describes how services work and how to configure services for use.

Call Rating. The gateway server has the capability to debit for calls explained in more detail in the services section. However in order to charge for calls the gateway server requires call rating information to be supplied which govern how much calls cost. This section explains the call rating process and how to configure call rates.

Voice Prompt Management. The gateway server features customizable voice prompts with support for multiple languages. This section explains how to set up and customize voice prompts for use with the system and provides some additional detail on how voice prompts can be administered.

Some of the capabilities that the gateway server is capable of providing require in the interaction of the routing server and or database server. The use of these components to enhance the services that the gateway server provides is described in later sections.

This section describes how the gateway server supports hardware devices and how to configure the hardware support component of the gateway server.

In order to connect a gateway server to a traditional telecommunications network specialized hardware boards must be used. The gateway server supports a range of such boards each offering different numbers of lines and types of lines. In addition to these telephony boards the gateway server is also capable of making use of DSP processing boards that enable larger numbers of calls to be handled by a single gateway server. The hardware support component of the gateway server is responsible for interfacing with the installed hardware devices and on enabling those devices to co operate in providing IP Telephony services. In addition to supporting telephony devices the gateway server extends the concept to network devices used for interconnection to IP Telephony devices via an IP network. In one example the only physical device installed in the gateway server for this interconnection is an Ethernet card.

In addition to supporting a variety of types of hardware devices the gateway server can also support multiple devices of a single type. For example it is possible to use two Dialogic D 41ESCs each of which is a 4 line telephony boards to achieve 8 lines of capacity.

A Hardware Device Configuration screen as shown in can be accessed by double clicking on Hardware Devices a top level management tree node on the gateway server. This window will display a list of devices that is currently configured and the current status of those devices.

From this screen in individual hardware devices can be started or stopped. By default when the gateway service is started all hardware devices will be started and when the gateway service is stopped all hardware devices will be stopped. Add and Remove buttons can be used to add and remove hardware devices and the Properties button can be used to configured existing hardware devices meaning a hardware device is added where its properties are configured a type specific dialog will appear that allows a user to configure information for that specific hardware device.

The subsections below discuss each hardware device supported by the system. When one chooses to add a hardware device he or she will be prompted to select what kind of hardware device is being added from one of the following devices. Some devices allow multiple instances to be present. Because of this devices are identified by the combination of their type and an instance number assigned to the device when it is added. Prior to discussing each individual board however general information regarding Gatenet 3 vs. DSP modes of operation are provided.

The gateway server uses complex signal processing algorithms in order to minimize the bandwidth required for communication between Gateways while simultaneously preserving a high quality of voice. There are two ways that the required signal processing can be performed 

 1 Echo cancellation the first step in processing voice data is performed on the hardware device that is connected to the telephone equipment. However the CPU of the machine used to run the gateway server is used to apply compression algorithms to the voice data known as a Gatenet 3 configuration allows the use of a single or multiple telephony interface boards without a requirement for a specialized DSP processing board. The drawback to this approach is that there is a limit to the number of simultaneous calls that can be handled by a main CPU of certain types of computer that run the gateway server. A second drawback is that some devices are reduced in terms of the number of lines they can support when echo cancellation is performed onboard. In some cases not intended to limit the invention only certain boards can be operated in Gatenet 3 mode 

 2 Likewise echo cancellation and voice compression are performed on a specialized DSP board that is connected in hardware to the telephony interface board. This provides better performance and scalability but incurs the cost of the specialized DSP board.

The gateway server software is capable of supporting either mode. However since the hardware configuration depends on which mode is selected the mode of operation is normally predetermined.

The Dialogic D 21H operates only in Gatenet 3 mode but is completely compatible with the Dialogic D 41ESC when operated in this mode. Please see the section below on the Dialogic D 41ESC for details on how to configure a Dialogic D 21H.

The Dialogic D 41ESC is a four port analog loop start interface board. It allows a connection to a central office using standard analog telephone lines as well as interconnection with PBXs or other equipment that provide FXO also called IST ports.

The Dialogic D 41ESC is capable of operating either in Gatenet 3 mode or in DSP mode. When operating in Gatenet 3 mode it is only capable of providing two ports of connectivity to telephone equipment otherwise all four ports can be used. Also a D 21H functioning in Gatenet 3 mode is identical to a D 41ESC and can be set up and treated in exactly the same manner.

The first panel displayed is a General panel as shown in . Other panels can be selected by clicking on the Tabs that appear along the top of the dialog. The settings on the General panel are explained below.

Board Number. This is the Dialogic board number of Dialogic D 41ESC being configured and controls which board if more than one D 41ESC is present will be used. Normally the first D 41ESC device added should be assigned board number 1 the second 2 and so forth. However if some boards in the chassis should not be used or are used by other applications this parameter allows explicit specification of which Dialogic board number to open.

Enable GN3 EC Mode. This parameter is used to enable or disable operation in Gatenet 3 mode. See the section on Gatenet 3 vs. DSP compression above to determine how this parameter should be configured.

Number of rings before answering. This controls how many times an inbound call will ring before the gateway server answers the call.

Enable Trunk Channels. This group of buttons allows a user to select specifically which trunk channels will be opened on the D 41ESC. Note that if one enables Gatenet 3 mode one cannot enable trunk channels 3 and 4. Normally one should enable all channels unless using other channels of a particular Dialogic board with a different application.

Enable Voice Channels. This group of buttons is the same as the trunk buttons but control which voice channels are used. Under most circumstances one uses the same settings for voice channels and trunk channels.

Output Gain. This setting allows one to control the output gain. If the volume of voice prompts and speech are too low when making calls then adjusting this option allows the gain to be adjusted. However before using this parameter one should verify that other Dialogic options are set correctly since gain can be applied in several different locations. Also if one uses a separate DSP board for processing this setting will have no effect since the DSP board will apply gain not the D 41ESC.

A call analysis panel is used to configure how the D 41ESC detects the presence of a connection. This call analysis panel is shown in . It is a panel in window and continues to include Tabs .

The parameters on the call analysis panel are passed directly to the corresponding Dialogic modules that make use of these parameters. For a detailed discussion of how the Dialogic D 41ESC performs call analysis refer to the Dialogic documentation. The two most relevant parameters on this page are Enable Voice Detection and Enable Loop Current Signaling. Voice detection should always be enabled except in specialized environments. Voice detection allows the beginning of a call to be determined based on the recognition of speech patterns such as Hello . Loop current signaling allows loop current based answer supervision provided by the telephone network to be interpreted and should only be enabled if supported by the telephone network provider.

The D 41ESC can be configured to wait for a dial tone before it enters digits as shown in panel in . It can also be configured to wait a maximum number of rings on an outbound call before it gives up and assumes that the call will not be answered. This panel allows one to configure settings that affect this process.

Ring Settings Time for Outbound Call Pickup. This parameter controls how long the Dialogic D 41ESC will wait for an outbound call to be picked up before it abandons the call.

Dial Tone Settings Minimum Dial Tone Length. This parameter controls the minimum length of a dial tone before it will be recognized.

Dial Tone Settings Timeout for Dial Tone. This parameter controls how long the Dialogic D 41ESC will wait for a valid dial tone before it abandons the call due to no dial tone.

Dial Tone Settings Maximum Dial Tone Interruption. This parameter controls the maximum break in a dial tone that will be tolerated without considering a particular tone not to be a valid dial tone.

During Call Progress Analysis and also for hang up detection the D 41ESC uses cadence detection to determine when a line is ringing when a user answers when the line is busy and so forth. However many of these tones may not be common from one country to another. As a result it is possible to customize the tones that are used by the Dialogic D 41ESC in order to determine whether or not particular events are happening. The tone definition panel is shown in .

By selecting one of the tones listed and clicking on Edit one is able to modify the frequencies and timings that control how a particular tone is detected. One should determine the information that defines the tones that are used on the particular equipment that one is connecting to the gateway server. When editing each tone a cadence dialog is displayed which asks for settings as shown in .

One should supply the information in the dialog. The parameters are fairly self explanatory. By default dual frequency cadence tones will be detected. If one wishes to detect a single frequency tone then set the second frequency to zero. To detect a continuous tone not a cadence tone one should set the repeat count to zero.

The two most important tones in most cases are the hang up cadence tones. Hang up cadence tones are tone definitions that can trigger the automatic disconnection of a call. In some environments disconnection signaling is only performed by way of cadence tones. In this case it is necessary to enter the appropriate tone information under either the primary or alternate hang up cadence. It is also necessary to enable disconnection upon detecting this tone at the line level.

This board is suitable for customers who require a large number of analog lines connected to a telephone device. The configuration panels for the D 160SC LS are identical to those for the D 41ESC except for general panel which provides a larger number of ports that may be enabled or disabled. The D 160SC LS panel is shown in .

The Dialogic D 240SC T1 is a T 1 interface board that provides 24 channels of digital connectivity to a telephone device with a T 1 interface. Although the Dialogic D 240SC T1 is capable of operating either in ISDN PRI mode or in robbed bit mode the Dialogic D 240SC T1 device in the gateway server refers only to the D 240SC T1 operating in robbed bit mode. If a user is operating the D 240SC T1 in ISDN PRI mode one should add a Dialogic ISDN device described below.

Much of the configuration of the D 240SC T1 is identical to the configuration for the D 41ESC. All of the T 1 specific configuration is contained on general panel as shown in . Tabs contain identical information to the configuration or the D 41ESC.

DTI Board Number. A D 240SC T1 like a D 41ESC provides both T 1 trunk and voice resources. However there are separate logical board numbers for the trunk and voice boards. This parameter allows one to control which DTI board number will be opened for this device.

Voice Board Number. As explained above the Dialogic voice board number for a D 240SC T1 is opened separately from the T 1 trunk. The D 240SC T1 actually emulates independent voice boards. Thus for D 240SC T1 1 the voice board number starts at 1. For D 240SC T1 2 the voice board number starts at 7. Normally one will not need to customize settings made by ExpressConfig however for integration or sharing with other applications this option is provided.

T 1 Signaling Bits. With T 1 robbed bit protocols information is signaled between the telephone equipment and the gateway server using two bits known as the A and B bits. Different patterns for these bits represent different information. Most telephone equipment uses the default settings for the T 1 signaling bits. However the interpretation of bits received from the telephone equipment and the bits that will be sent to the telephone equipment can be customized in this page.

T 1 Network Mode. This mode controls how the T 1 signaling bits defined above will be used. It controls the relative timing and sequence of the bit patterns. One should select the option that corresponds to your telephone equipment.

The Dialogic ISDN device provides support for both T 1 ISDN PRI systems and E 1 ISDN PRI systems. If one has configured either a D 240SC T1 or a D 300SC E1 in ISDN PRI mode then one should install a Dialogic ISDN device. One Dialogic ISDN device is required for each ISDN span 23 lines for T 1 30 lines for E 1 that one has configured in a system.

The configuration of the Dialogic ISDN device is significantly simpler and more understandable than dealing with the cadence tones and settings for some of the other Dialogic devices. This is because with ISDN signaling is explicit out of band and relatively constant between different environments. There are three panels that a user deals with when configuring a Dialogic ISDN device.

General panel of properties screen allows general settings to be configured on the D 240SC T1. shows this panel. Other tabs are show in and discussed in detail below. These settings are explained below.

DTI Board Number Voice Board Number. These parameters are identical to the settings explained for the D 240SC T1. Refer to that section above for an explanation of these parameters.

Board Type. This parameter controls whether the ISDN device in use is a D 240SC T1 or a D 300SC E1. You should select the parameter corresponding to the board that is installed in your system.

Output Gain. Dialogic ISDN devices are almost always used with a DSP voice board so the output gain parameter should not normally be used unless one is involved in a very specialized application.

Channel configuration panel allows one to select which channels will be used on the Dialogic ISDN device. In almost all cases one should disable all voice channels since the voice channels are not used. Although enabling the voice channels does not interfere with the gateway server some ISDN protocols require enough DSP processing power that the voice channels cannot be enabled successfully. In most cases one should enable all of the trunk channels. shows the channel configuration panel.

Unlike conventional telephone devices which signal calls using the hookswitch state and DTMF tones ISDN devices signal calls in a single digital message. The contents of this message do vary between ISDN switches however. Call setup panel allows the correct message for a particular ISDN switch to be sent. shows the call setup parameters panel.

Destination Number Type. Indicates the type of number being transmitted to the ISDN switch. This field needs to match the type required by the ISDN switch one is connected to.

Destination Number Plan. Indicates the numbering plan used for the destination number transmitted to the ISDN switch. This field needs to match the numbering plan required by the ISDN switch being connected to.

Connection Timeout. This controls how long the gateway server will wait for the completion of a particular call. If the call is not completed within this amount of time it will be aborted.

Originating Number Type. Same as the destination number type but for the originating number i.e. the number of the gateway server .

Originating Number. Number sent to the ISDN switch as the number of the party originating the call. Normally when connected to the PSTN this parameter will be ignored since the PSTN switch knows the identity of the originator.

Layer 1 Protocol. Controls the value of the Layer 1 Protocol parameter in the call setup message. This should normally be left at the default value but some specific ISDN switches may require this value to be overridden.

The Dialogic MSI SC boards are analog station interface boards. The MSI SC allows telephones or other equipment that normally plugs into a standard analog line from the PSTN to be connected directly to a gateway server. In essence the MSI SC emulates a line from the PSTN and can be used to connect to PBX trunks in addition to standard telephones. This kind of interface is also known as an FXS interface or station side interface.

There are two variants of Dialogic MSI SC boards those with the ringing option and those without. In order to use the Dialogic MSI SC with the gateway server the ringing option is used in order to make outbound calls.

In addition there are three configurations of an MSI SC an 8 line 16 line and 24 line configuration. These are referred to as the MSI80SC R MSI 160SC R and MSI 240SC R where the R denotes the ringing option. A user needs to know which of these configurations he or she has prior to configuring the MSI SC for use with the gateway server.

Ring Line For Outbound Calls. Indicates whether or not the ringing option is present on the MSI SC board. This option is used in order to make outbound calls.

Unanswered Rings before Aborting. When ringing a particular line the MSI SC will generate a certain number of rings before the call is aborted. This parameter allows the number of rings that will be generated before an abort to be configured.

Output Gain. This parameter allows the gain of the lines connected to the MSI SC to be controlled. This can be used to adjust the volume of the phones connected to the MSI SC.

ANI Information. ANI or Caller ID information can be used by gateway server applications in order to identify a user without asking for identification. Since the lines connected to the MSI SC may be fixed i.e. line 3 is always connected to the phone of a particular user Caller ID information can be associated with each port of the MSI SC. One can use this control to enter Caller ID information for each MSI SC line.

As discussed in a section above the gateway server supports the use of specialized DSP processing boards to achieve high density and consistent call quality. Although boards from different manufacturers are supported the firmware used on the boards is licensed from Mibridge Inc. in all cases. The Mibridge DSP device in the gateway server refers to any of the DSP boards supported by the Mibridge firmware and any quantity of those devices. A user should install only one Mibridge DSP device even if he or she has multiple DSP boards.

There are two simple panels that should be configured for the Mibridge DSP device. The Board Type panel has only one option allowing the type of board to be selected. One should select the board type that corresponds to the actual hardware present in the gateway server. A voice channel configuration panel shown in allows addition options to be configured. The options are explained below.

SCbus PCM Encoding. Depending on the Dialogic devices being used with the Mibridge DSP board the PCM encoding on the SCbus used to connect the Dialogic and DSP boards may be different. If one is using any board except for the D 300SC E1 muLaw encoding is normally used. If however one is using the D 300SC E1 one should select A Law encoding.

Automatic Gain Control. In certain environments it is beneficial to enable automatic gain control to compensate for naturally low input levels. This is controlled via the Automatic Gain Control setting. In most environments however Automatic Gain Control should be disabled.

Fixed Input Output Gain. If automatic gain control is not enabled then a fixed level of gain can be configured. In most environments the default gain of 0 db should be used. However the level of gain can be customized if the default setting is not sufficient.

The Network H.323 device enables communication using the H.323 protocol. This allows calls to be received from and placed to H.323 compatible devices such as Microsoft NetMeeting terminals or multimedia PCs. The only required configuration parameter for the Network H.323 device is the H.323 terminal name that will identify the gateway server to the remote H.323 entities with which it communicates.

The Network Proprietary device enables communication with other present invention gateway servers using a proprietary protocol. This is the normal protocol used for Gateway to Gateway communication. There are two main configuration parameters for the Network Proprietary device. The first is the port range which controls which UDP IP ports will be used for media data transmitted to and from this gateway server. The second is the Local System ID of the gateway server. This name will be presented to remote gateway servers when a call is placed and may be used by the remote gateway server in order to identify and authenticate the originating gateway server. More details on this process are discussed in the User Management section.

The Network Settings tab allows advanced network properties to be configured and tuned. These settings as well as a detailed explanation of the port range feature are found in Appendix B which provides technical network design information.

The hardware support component of the gateway server discussed in the previous section provides support for hardware devices that are located in the PC on which the gateway server runs. However providing actual functionality to the end user involves co operation between different boards. Furthermore lines on different boards may often need to be treated the same way and pooled together. The line and line group component of the gateway server organizes the capabilities provided by underlying hardware devices into virtual lines and allows these lines to be grouped together into line groups. This section explains lines and line groups.

Lines represent a single logical point of connection to the system. A line is capable of handling a single call from a user and represents one complete port of connectivity. There are two kinds of lines telephony lines which are directly related to the telephone lines actually connected to the gateway server and network lines which are created on demand and used to represent connections to other gateway servers or to users on the H.323 network.

Since network lines are created on demand it is not necessary to interact with network lines in most cases. However telephony lines are created in advance and must be created in order for the gateway server to make use of the underlying hardware devices. Telephony lines serve primarily to combine resources supplied by underlying hardware devices in order to deliver the required services to the user. For example a DSP device is not capable of actually connecting to the PSTN but it is capable of performing IVR. On the other hand a telephony board may not be capable of performing IVR but can manage the connection to a user. Telephone lines group these resources together to form a single virtual line that can be used to deliver the services provided by the gateway server.

The actual configuration of a telephony line can be quite complex and is in general not necessary since ExpressConfig will set up suitable default parameters. The configuration of telephony lines is discussed below when the telephony line group is discussed in detail.

Lines are either in the active state the inactive state or switching between the two states. Network lines are always in the active state since they are deleted once they are no longer active. Lines can be activated or deactivated at any time. When the gateway service starts all lines will automatically be activated. When the gateway service stops all lines will be automatically deactivated.

For the purposes of call routing as well as configuration of parameters lines are always organized into groups of lines called line groups. Line groups manage properties that generally do not need to be configured on individual lines. Also the service level of the gateway server may associate application specific properties with line groups that affect how services are provided to the user. For example the service layer could be configured to handle all calls coming in on a particular line group by routing the call to a specific number whereas calls to another line group would be handled using an IVR application.

As with lines there are two kinds of line groups telephony line groups and network line groups. Telephony line groups contain numbers of telephony lines. Network line groups contain network lines and handle the dynamic adding and removal of network lines as calls are established and terminated. The configuration of these two types of line groups differs each will be discussed in a separate section below.

Using the management system a line groups window can be displayed by expanding the top level configuration tree node named Line Groups . This window is shown in . In the top part of the window a line group panel shows that line groups may be selected from one of the available line groups. Typical installations have one network line group and one telephony line group. Once a particular line group is selected the bottom part of the window displays a telephony line group status panel . Panel shows the list of lines that are currently configured on that line group. The state of each of the lines will also be displayed along with any error messages associated with that line. In the top window line groups can be added removed or configured. In the bottom window individual lines can be activated or deactivated and lines can be added removed and configured. The configuration of lines and line groups are discussed in the sections below.

Telephony line groups manage groups of telephony lines and apply parameters and properties that are common across all lines in that group. Telephony line groups also interpret events that occur on lines such as DTMF digits and can assign a meaning to those events. For example a hardware device or line might only be aware that the DTMF digit sequence was pressed however the telephony line group may know that this sequence indicates that the call should be disconnected.

When a telephony line group is added or configured dialog with general panel appears and allows parameters to be customized. Panels can be navigated between using tabs at the top of the dialog . The settings available on the general configuration dialog are shown in and described below.

Maximum Connect Time. If one wishes to limit the maximum duration of a connection to the system it is accomplished using this parameter. Normally one will not need to enable a maximum connect time but depending on the application it may be necessary to do so.

Line Allocation Strategy. The line allocation strategy controls how a line is selected when an outbound call is to be placed using the telephony interface. These strategies are usually used in conjunction with the line allocation strategy used by the telephone equipment to which to the gateway server is connected in order to minimize glare conditions. There are four possible strategies 

Enable Support for DID. Enables the use of DID information on the lines in this line group. This should only be enabled if the telephone equipment to which the gateway server is connected provides DID signaling.

DID is sometimes used to refer to DNIS service provided on an ISDN PRI line. One should not enable DID on an ISDN PRI line. Enabling DID only allows the collection of DID information using DTMF digits sent at the beginning of a connection. ISDN PRI does not signal DNIS sometimes called DID information in this fashion.

DID Min Max Digits Accepted. If DID is enabled controls how many DID digits will be required in order for DID collection to be successful. If the number of digits is between the maximum and minimum inclusive then the DID information will be accepted otherwise DID collection will fail.

DID Collection Time Limit. Specifies how long DID digits will be collected for after the call is answered. Normally one second is sufficient for the transfer of DID digits but this may depend on your particular telephone service.

Hangup settings panel shown in allows the events that cause a user to be disconnected to be configured. In normal environments it is not necessary to configure these settings. However in some environments disconnection is not signaled explicitly by the telephone equipment and must be detected by alternate means.

Silence Triggered Hangup Settings. These settings allow one to configure whether or not a line will automatically be disconnected based on an extended period of silence. Normally this feature is disabled. When enabling the feature one should select whether silence of the local party or silence on both ends of the conversation is required to cause disconnection. One should also specify the time in seconds of continuous silence that is required in order to cause disconnection.

DTMF Triggered Hangup Settings. When integrating with PBXs and other kinds of telephone devices disconnection can sometimes be signaled through the use of DTMF digits. If one enables DTMF triggered hangup one will be required to specify a string of DTMF digits including extended digits such as A B C D that will cause hangup. If these digits are detected in the order specified and within the amount of time specified in the interval field then the call in progress will be disconnected.

The integration digit settings are used for custom applications. One should not modify these settings.

The above describes the settings for the telephony line group. In addition when configuring a line on the line group it is necessary to provide configuration information for that line. In order to understand telephony lines it is necessary to understand how resources are represented in the system. There are three types of resources associated with a telephony line. The trunk resource represents the actual connection to the phone equipment such as the physical analog line or a T 1 channel and so forth. The voice resource represents the DSP processing resource that is used to perform IVR voice compression and so forth. Finally an optional auxiliary resource can be used for call progress analysis cadence detection and other such applications. ExpressConfig normally sets up the resources for each telephony line exactly as required. It is generally not recommended that one modify these settings.

When a telephony line is added or configured the following set of panels can be interacted with in order to configure the telephony line.

The resources panel controls the interaction of the telephony line with the underlying hardware devices. Tabs allow selection of other panels which are discussed in detail below. Panel is configurable from telephony line window which is shown in and explained as follows 

Location Position Information. This field allows one to provide identifying information that can enable you to locate the physical line. It is for descriptive purposes only and is not required.

Trunk Resource Configuration. In this section one needs to specify the hardware device that is associated with this telephony line and the instance of the trunk resource on that device which is to be used. Trunk resources are described above.

Voice Resource Configuration. This section allows one to specify which voice resource should be associated with the trunk resource configured above. Voice resources are described above.

Accept Any Location Location List. These settings are for future expansion and will allow one to address individual lines when routing calls. This enables the development of virtual PBX style applications but is not required for operation with any of the applications currently shipping with the gateway server.

Class of Service. The class of service on each line can be configured on a line by line basis. Class of service constraints allow lines to be disabled to accept only incoming calls to place only outgoing calls or to accept calls in both directions duplex service . The desired class of service can be specified using this setting.

This panel allows you control call analysis settings panel not shown but tabs show tab to access this panel . There are two main settings 

Enable Call Progress Analysis. This parameter determines if call progress analysis should be enabled. If enabled it is also necessary to select which resource will perform the call progress analysis. The correct value for this setting is generally determined by ExpressConfig and depends on a particular hardware configuration.

Enable Cadence Detection. This parameter determines if cadence detection is active during calls. Cadence detection may be used to trigger certain things such as automatic disconnection. If cadence detection is enabled it is necessary to specify which resource will perform the cadence detection.

Auxiliary Resource. If either cadence detection or call progress analysis requires the use of an auxiliary resource the auxiliary resource must also be configured. It is necessary to specify the device and instance of the resource associated with this line just as for trunk and voice resources.

Panel shown in controls how the start of a conversation is detected by the system. There are several options for how this connection detection occurs.

Connect Immediate. If this parameter is enabled all calls are assumed to be connected after they have been dialed without waiting for any signaling from the telephone equipment.

Connect CPR. If enabled this parameter will enable calls to be connected if call progress results are provided by the call analysis resource associated with this line.

Connect LCR. If enabled this parameter will allow loop current reversal events to trigger the connection of a call. In some environments loop current reversal is used for answer supervision.

Connect Cadence 1. Enables connections to be signaled through the use of custom cadence tone 1 which must be defined at the hardware device level. If a call is being placed cadence tone 1 is detected and this parameter is enabled the call will be connected immediately. Note that the process of placing a call may interfere with the use of cadence detection in certain hardware configurations.

The disconnection detection panel panel not shown but tabs show tab to access this panel is very similar to the connection detection panel. However events in this panel are used to detect the disconnection of the user previously connected on a particular telephony line.

Unlike telephony lines network lines are created dynamically by the system as new calls are received and are removed when calls are terminated. Therefore there is no need to configure a list of lines or to set configuration for those lines.

Furthermore the network line group itself has no configuration properties at the line group level. Recall that settings may be associated with line groups at the service level described in the next section . The reason for this is that parameters are associated with the network proprietary device or the network H.323 device.

A second network line group is generally not required. All network calls are processed through the single network line group. However one must have a network line group in order to receive network calls.

The Services component of the gateway server is shown in . This component is responsible for enabling the applications that actually provide services to the end user.

Applications are highly separated from the gateway server platform discussed so far in this section. Applications make use of the numerous capabilities provided by the gateway server platform in order to interact with the user and to deliver enhanced services. In one example all such applications are written using a C API that provides access to functionality provided by the gateway server. Services can interact with each other and transfer control from one service to another creating a flexible environment for constructing applications.

Gateway server applications are contained in DLL files that are linked at run time to the gateway server platform and operate in gateway server Application Layer . However it is possible for third parties to create similar application DLLs. It is also possible to use the gateway server API to write applications that run from a separate process or even a different machine.

The first part of this section will describe the services component of the gateway server platform . The second part of this section describes the applications according to the present invention that are included with the gateway server.

Selecting the Services node in the configuration tree using the management system will access a main service window shown in . The area at the bottom of the window shows a list window of active sessions the line that each session is associated with and the service application that is currently managing that session. The other information presented on this screen is discussed below.

The gateway server is capable of supporting numerous kinds of services and can run any number of instances of a particular service. Because multiple services are present that can handle an incoming call it is necessary to define rules for selecting the service that will be used to handle incoming calls. By default ExpressConfig creates a rule that selects the gateway application to handle all incoming calls. However this behavior can be customized and different services can be selected.

In order to select the service used to handle incoming calls the gateway server provides a rule tree within Rule Engine . When an incoming call is received the gateway server will traverse rule tree until it finds a service that matches the parameters of the incoming call. As previously discussed calls are handled as sessions by the gateway server. Thus incoming calls are a type of session within the system. Information in the incoming call can be used to control the service selection process. For example DID or DNIS information can be used to select which service is activated and with what parameters. This is extremely powerful in creating a flexible single box solution that hosts multiple applications. shows service selection panel and rule list panel . Rule list panel allows rules to be added modified and or removed. This feature is discussed below.

The rule tree consists of a number of rules arranged in a tree like structure. When an incoming call arrives at that gateway server selection begins at the top of the tree. Each rule at the top level of the tree is processed until a rule is found which matches the information contained in the incoming call. If a match is made then that node in the tree is selected. A node in the tree however can either be a final node in which case it contains the name of a service used to handle the call or it can be a subtree. If it is a subtree then the above process is repeated starting at the top of the tree that is beneath the selected node. If the bottom of rule tree is reached and a matching rule is not found then no service will be selected and the incoming call will be rejected.

Each rule in the rule tree contains a condition that must be matched for the rule to be selected. A blank rule allows all incoming calls to be matched. If the rule is a final rule meaning that it directly selects a service then the name of the service and parameters for the invocation of the service are also required. Dialog opens to show settings for any rule. Dialog includes fields as shown in and described below 

Attribute. This field provides the name of the parameter that will be checked to see if this rule should be selected. It names an attribute of the incoming call such as DNIS DID or others.

Relation. This selects the relation that the attribute must have to the value described next in order for this rule to be selected. Possible relations are equals to and not equals to.

Value. This is the value against which the value of an attribute will be compared. For example if an incoming call has DNIS 1234 and the Attribute name is DNIS then 1234 will be compared against the value specified in this field. In the example above if the relation was equals to and the value is 1234 then this rule will be selected. If however the value was 1235 or the relation was not equals to then the rule would not be selected.

Service. If configuring a final rule the name of the service that will be used to handle the call must be specified in this field.

Bindings. In order to customize the behavior of a service it is possible to specify additional bindings to be passed along to the service. Bindings are a list of attribute value pairs that will be interpreted by the service that is invoked. Clearly the bindings list is service dependent. For a list of bindings that can be used to modify the behavior of a service one needs to refer to the documentation for that service. As an example placing Language English as a binding will cause the gateway server to use English as the initial language for voice prompts. This is extremely powerful when combined with rules because it would allow a configuration where calls received with DNIS 1234 are handled using English voice prompts and calls received with DNIS 1235 are handled using Chinese voice prompts.

There are certain parameters that affect services and service selection that are required to differ from one line group to another. For example it might be desirable to allow users calling in on one line group connected to a PBX for example to make calls without entering an identification code whereas calls received on a different line group might require an identification code. Service level settings can be associated with any of the configured line groups. These settings can be viewed by double clicking on the line group nodes in the configuration tree that appear when the service node is expanded. There is one node for each line group that exists in the system. The settings which are common for all line groups are shown in and explained below.

Auto user Lookup using Call Setup Information. Information may be associated with incoming calls that allow a user to be identified automatically without the use of user identification entry. For example a user could be identified using Caller ID information supplied by the telephone equipment. Enabling this field will cause an automatic user lookup to be initiated as soon as the call is received using all information available at the time that the call is received. More details on how user records are managed can be found under the User Management section of this document.

Auto user Assignment using Call Setup Information. In the event that the lookup of a user based on Caller ID or other properties fails or if this feature is not used it is possible to always assign users to a particular user account. Because this is configured on a line group by line group basis it could be used to assign all callers on a particular line group e.g. one connected to a PBX to a particular user account perhaps PBX USERS. On the other hand calls on other line groups would continue to require user identification whereas the users on the PBX interface would be automatically associated with the PBX USERS account. If this field is selected it is necessary to enter the user ID with which the line group will be associated under User ID.

Default Privilege Level. Routes are restricted on the basis of privilege level as will be explained in the section on number translation and call routing. Before a user is identified however they will have a certain privilege level. This parameter can be used to control the default privilege level assigned to an unidentified user. This in turn can be used to restrict calling privileges. For example one route to 1 800 NEWUSER could be assigned a privilege 0 with all other routes requiring privilege 1. A greeting could say If you are a new user please call 1 800 NEWUSER to open an account. Otherwise please enter the number you wish to call . By granting a default privilege level sufficient to make the call to 1 800 NEWUSER it is possible for new users to call in and open accounts using the same system without requiring multiple telephone lines and telephone numbers. Similarly unidentified users on different line groups could have different default privilege levels.

Use DNIS DID Information as Dialed Number. Enabling this parameter causes the gateway application discussed below to treat DNIS DID information as the number that the user wants to call. This can be used to instantly route calls based on the number dialed by the user to access the system. This can be used to provide 800 services for example by routing calls to 1 800 1234567 to customer A s local number of 703 555 1234 and routing calls to 1 800 7654321 to customer B s local number of 416 555 1234. This allows a single line to be used to provide 800 services to multiple customers that are located in different cities reducing their long distance costs for handling calls from customers.

The gateway service in the context of high level applications is a core service that leverages the capabilities of the gateway server platform to deliver calling capabilities to end users. The gateway service is provided by the gateway server. It includes but is not limited to handling calls bridging communications systems and providing access to other systems such as databases routing servers etc. The gateway application service should not be confused with the gateway server service. Because the Gateway Application Layer is complex in its operation and provides a significant degree of functionality it is discussed in the next section.

The autoforward services is a relatively simple service that forwards all calls to a pre determined number. It is capable of playing a greeting immediately before the call is forwarded. This service can be useful in a number of applications. For example a particular DNIS field could select the autoforward service which could announce Please hold and the next available customer service representative will be pleased to serve you and automatically forward the call to the customer service department ACD which could potentially be in a different geographic location.

Autoforward services can be configured by double clicking on the Autoforward node in the configuration tree which can be accessed by expanding the Services root level node. An Autoforward configuration dialog is shown in and described below. Note that one must click on Change in order to confirm changes to the service settings in call address panel and voice prompt panel . These panels are discussed below.

Country Code Area Codes Local Number. These fields specify the number that calls will by default be automatically forwarded to.

Enable Voice Prompt. If enabled this feature causes a voice prompt to be played immediately prior to forwarding the call. The name of the voice prompt to be played see Voice Prompt Management later in this section can also be configured.

In addition to the above configuration parameters the number to be dialed can be overridden by binding the parameter Autoforward CallNumber to the number that is to be called. This allows a different number to be forwarded to based on DNIS DID information or other call setup information.

The gateway server by default has several internal services that are used to accommodate common tasks such as collecting digits and obtaining user identification. These services are not directly selectable but can be used when developing third party applications and may also appear in the list of services that are presently in operation.

The gateway server is capable of assessing charges to user accounts for calls that are made by the user through use of the Call Rating Manager . These charges can either be recorded in call detail records or debited directly from users accounts. This process is explained in greater detail when the gateway application and User Management are explained. However a key part of performing this charging for a call is determining how much to charge for the call. This section explains the operation of call rating and describes how call rating can be configured. The Call Rating Manager of the gateway server is designed to be extensible by application developers. In order to facilitate this there are multiple ways to rate calls known as call rating types. A single standard model for rating calls is built into the software it is possible for third party application developers to add additional means of rating calls. In addition for each call rating type numerous profiles may exist. Different profiles may use different values for how much to charge how often the user is charged and what levels of discounts are applied. The call rating engine supports multiple profiles for each of the call rating types that are present.

The call rating configuration dialog can be found under the General node in the configuration tree. Expanding this node will show the Call Rating node which can be double clicked on in order to bring up a call rating configuration dialog. This dialog is shown in and described below. The billing profiles panel provides a list of currently defined call rating profiles for each call rating type. New profiles can be added to the list and existing entries can either be removed or modified.

When modifying a call rating the dialog that will be displayed depends on the call rating type. For the built in call rating type the following information is included in a Standard panel shown in and described below 

Description. Allows a textual description for reference purposes to be associated with the call rating profile.

Rate Modifier. Routes that are used to place calls contain a rate modifier which is a floating point number. How this number is used for a given rating profile depends on this configuration setting. The rate modifier can be ignored in which case the rate modifier field in the route will have no effect. If the base option is selected then the rate modifier will be used as the base rate for the purposes of rating the call base rates are explained below . If the percentage setting is selected it will be used to adjust the normal base rate to determine the effective base rate.

No Charge Time. This field specifies the time in seconds during which no charge will be applied for the call. Calls of this duration or less will effectively be free. This can be set to zero to begin charging immediately.

Base Rate. This field specifies the base rate for the call in units dollars per minute. The base rate is the nominal charge that will be applied during the entire call. This field is overridden if Base is selected for the Rate Modifier and will be adjusted by the percentage specified in the rate modifier of a route if Percent is selected for the rate modifier.

Granularity. This controls the incremental billing unit. It is used to ensure that all charges are in cents tens of cents dollars etc. This allows currencies such as the Yen which has no fractional components to be used by simply setting the granularity to 1 i.e. all billing is in increments of 1 Yen .

Initial Interval. Specifies the first interval in seconds which will be charged for when making the call. As soon as the no charge time is exceeded the initial interval will be billed for.

Initial Rate . This controls the actual rate that will be used for billing the initial interval. For example if the initial rate is set to 200 and the initial interval is 10 seconds then the first 10 seconds of chargeable time will be billed at a rate of 200 of the base rate. This can be used to provide certain behavior. In the example above if the no charge interval is 10 seconds the initial interval is 10 seconds and the initial rate is 200 then the first 10 seconds are free but after 20 seconds the charge is for 20 seconds worth of the base rate. By doing this calls are effectively charged at a uniform rate but if the caller hangs up in the first 10 seconds no charge will be applied.

Incremental Interval. Once the initial interval has elapsed the user will be billed in incremental units of time specified by this parameter.

Incremental Rate . Each incremental user billed to the user will be billed at that incremental rate percentage times to the base rate for the call. Normally this will be 100 . As an example if the incremental interval is 10 seconds the base rate is 0.60 per minute and in the incremental rate is 100 then the user will be billed for each 10 seconds used or part thereof at 100 of the base rate of 0.60 per minute. Since each 10 seconds used costs 0.10 at 100 of the base rate each 10 seconds or part thereof used by the user would cost them 0.10.

An integral part of providing IVR based services is the management of the voice prompts that are actually played to the user. The voice prompt management system is responsible for managing the voice prompts that are available on the system and allowing those voice prompts to be played. In addition in order to support multilanguage applications multiple languages of a particular voice prompt may need to be supported.

The Media Manager handles all aspects of voice prompt management. It allows the list of voice prompts to be configured via the management system. To view a Media Manager window double click on the Media Manager node in the configuration tree which is visible when the General root level node is expanded. The Media Manager window is shown in .

The Media Manager window shows the list of voice prompts in Media Manager Settings panel . By default when ExpressConfig sets up the default configuration for the gateway server a number of voice prompts are installed. These voice prompts are used by the gateway application in order to interact with the user. A user can modify these voice prompts to change the prompts used by the gateway application. One can also add additional voice prompts that can be used by third party applications or other applications such as Autoforward.

Media Manager buttons for Adding and Removing function differently than a normal list. The reason is that each entry has a number of versions i.e. languages of each voice prompt may be present. When one adds a new media entry New Media Entry dialog for adding a new voice prompt is shown in .

Settings panel allows for configuration of the prompt. The name of a voice prompt should be specified. If one selects the name of an existing voice prompt one should add an available version of that voice prompt or overwrite an existing one . If one enters a new name that does not already exist a new voice prompt will be created and maintained by the media manager.

The version corresponds to the language selection of the user and can also be used for other purposes. When adding a voice prompt or version of a voice prompt one can also specify the default version of a voice prompt. The default version is the version that will play if the requested language is either unspecified or unavailable. The description of the voice prompt is used for informational purposes. Finally one needs to provide a path to a muLaw file that contains the voice data that one wishes to be played. This path is specified in Media Entry File panel in . This file should be in raw muLaw format 8000 samples per second 8 bits per sample mono.

Similarly when one removes a voice prompt a user should select which version is to be removed. One will be provided with a selection of the available versions that can be removed. If one removes the last version of a particular voice prompt then that voice prompt will be removed entirely from the system.

If one needs to make bulk changes to voice prompts it is useful to be able to directly access the voice prompts as they are stored on disk. The filename format for voice prompts managed by the media manager is

where is actually the name of the voice prompt and is actually the version of the voice prompt. The files are stored in the main gateway server directory. Using this information one can do a bulk overwrite of all voice prompts once one has a configured set of voice prompts. However this can only be used to overwrite existing voice prompts not to add new voice prompts or new versions of voice prompts . One should also note that one should restart the gateway server if her or she directly modifies the files on disk in order for changes to take effect.

This section further discusses the gateway application described in the previous section. The gateway application is the main application for delivering calling services on the gateway server platform. It makes use of all of the capabilities provided by the gateway server platform in order to deliver sophisticated calling services to the end user.

Principles of Operation Describes the basic sequence of steps that the gateway application uses in processing a call entered by the user. This allows the basic IVR sequences to be understood. It also allows an understanding of the steps that the gateway application goes through in setting up a call.

Gateway Application Configuration Discusses the configuration options that can customize how the gateway application behaves and how to set those parameters.

Supplementary Application Configuration Discusses the internal applications that affect the behavior of the gateway application and how these applications can be customized.

The gateway application is a separate application from the gateway server that interfaces with the gateway server using the services API provided by the gateway server. However the gateway application is normally loaded in process by the gateway server. This allows the gateway application to integrate with the management and configuration facilities provided by the gateway server in addition to being able to provide services to end users.

The gateway application handles calls and interacts with users in order to collect the necessary information to complete calls on behalf of the user. The gateway application handles both network calls and telephony calls and handles inbound or outbound calls of each of those types.

The following sequence of steps is followed by the gateway application in handling a telephone call from a user as shown in 

Several configuration parameters can control how the gateway application interacts with the end user. These parameters are explained below. The Gateway Application Window can be viewed by opening the GatewayService node in the configuration tree which is visible when the Services root level node of the configuration tree is expanded.

There are three panels accessed from Tabs that allow the configuration of the gateway application. These panels are shown in . The tabs at the top of the window allow these panels to be navigated between.

General Settings panel allows general gateway application configuration options to be configured. There are only three parameters that can be configured on this panel 

Follow on calls. This parameter determines whether or not the user will be allowed to make follow on calls. This refers to the capability of placing a second and third and so forth call after the first call has been disconnected without hanging up and calling back into the system. If the gateway application serves live users this is generally a useful feature however if the gateway server is interfaced to an automated switch then this functionality is generally not necessary.

Maximum number of retries. To limit the length of time that a particular line can be tied up there is a limit to the maximum number of retries that can be entered by a user. This field controls how many times a user can try to unsuccessfully make a call before they will be disconnected by the system.

Call Charge Preferences. This field allows the selection of the strategy for charging calls placed using the gateway application. The possible selections are as follows 

The country area code settings panel shown in allows one to provide information about his or her local calling area to the gateway service. The gateway service is provided by the gateway server. It includes but is not limited to handling calls bridging communications systems and providing access to other systems such as databases routing servers etc. This is used to provide a dialing plan that emulates the dialing plan provided by the local telephone company in that area.

There are four parameters that one needs to configure. As shown in these parameters are the international prefix national prefix country code and area code. The way that these parameters operate is as follows. After the user enters the number it goes through the following three steps prior to being interpreted by the system 

For example if the international prefix was 011 the national prefix was 1 the country code was 81 and the area code was 3 then numbers would be processed as follows 

In the first example nothing was added after the international prefix since dialing the international prefix implies that the country code and area code have been dialed. In the second case the number didn t include the local country code 81 since it was a domestic long distance call so the country code was added prior to processing. In the final example neither the international nor national prefixes were added so it is assumed that the call is to the local area and the country code plus area code were added to the front of the dialed number.

When the dialed number is sent for processing and route resolution it is always required to be in a fully resolved format that contains the country code area code and local number. This way routing information can be shared between gateway servers in different areas without modification. If routes were simply based on digits dialed by users locale differences would prevent this from being possible.

Advanced panel contains settings that do not normally require modification. The settings available on this panel are shown in and discussed below.

Try First Possible Route. By default the gateway application will try to place a call using the optimal route and ask for user identification if necessary. If some users cannot be identified this could cause difficulty since even if multiple routes exist they will not be tried if the user cannot enter their identification code when the first route is tried and requires identification. To circumvent this situation it is possible to enable the first possible route that can be used with the current credentials to be tried first rather than the optimal route.

First Digit Timeout ms . This parameter controls how long the gateway service will wait for the first digit to be dialed when waiting for a number.

Subsequent Digit Timeout ms . This parameter controls how long the gateway service will wait for the second and subsequent digits when waiting for a number.

Identification Mode. Selects when identification information will be requested from the user. There are three possible settings for this parameter 

Always Always prompts the user for their identification after the number has been entered but before the call is actually placed.

At the beginning Always prompts the user for their identification but does so immediately when the user first calls into the system.

On demand Only prompts the user for their identification if it is required in order for the user to have sufficient privilege to access.

In order to facilitate reuse of certain application code by third party application developers the gateway application separates some functionality into separate applications that are used to perform common tasks such as obtaining a valid user identification or obtaining a users authentication code. These supplementary applications are separated from the gateway application and are invoked by the gateway application. This section describes the configuration of supplementary applications invoked by the gateway application.

The user identification application part of Higher Level Services is used to obtain a valid user identification from the user. The user will be prompted for their user identification and will be given several attempts to enter their user identification correctly. The user identification application will automatically consult with the database server to determine if the user identification provided is valid. The user identification settings window can be accessed using the IdentificationService node in the configuration tree visible once the Services node is expanded. Window is shown in and displays Identification Service Settings panel which relates the following information 

Maximum Number of Retries. This parameter controls how many failed attempts to enter their user identification a user will be allowed before they are disconnected.

First Digit Timeout. This parameter determines the amount of time a user will be given to enter the first digit of their user identification.

Subsequent Digit Timeout. This parameter determines the amount of time a user will be given to enter the second and subsequent digits of their user identification.

The user authentication application part of Higher Level Services is almost identical to the user identification application except that it obtains and checks the authentication code for a user. Configuration screen shown in can be accessed using the Authentication Service node in the configuration tree also visible once the Services node is expanded. Authentication Service Settings panel is displayed and relates the following information 

Maximum Number of Retries. This parameter controls how many failed attempts to enter their user authentication code a user will be allowed before they are disconnected.

First Digit Timeout. This parameter determines the amount of time a user will be given to enter the first digit of their authentication code.

Subsequent Digit Timeout. This parameter determines the amount of time a user will be given to enter the second and subsequent digits of their authentication code.

The previous section discussed the concept of session bindings in particular how they relate to customizing how a service application behaves. This section discusses the session bindings that can be used to manipulate the behavior of the gateway application.

The gateway application uses several session bindings that are set up automatically by the gateway server platform in order to provide the appropriate behavior based on the type of call being handled. At this time there is only one parameter that can be directly used to customize the behavior of the gateway application. This parameter is shown in the table below.

Version of media prompts that will be played by default until the user is identified. Once the user is identified voice prompt language will be determined by the user profile

This section describes how to configure routing and number translation according to the present invention. This is a critical aspect of the overall operation of the VoIP system. There are numerous ways that calls can be routed across the network in the present invention and selecting the optimal approach for a particular configuration is important in ensuring the performance and manageability of the network. This section presents the concepts behind routing and numbers translation and describes how routing affects the functionality of the overall system and explains available choices for how calls will be routed.

Routing in the context of the present invention software refers to call routing not IP routing. IP routing which handles the routing of IP packets sent on the underlying IP network is a separate issue and it is assumed that the present invention components are running on a network in which the IP routing is configured correctly.

This section is divided into several sections each covering a different aspect of call routing. These sections are as follows 

Number Translation. As a prelude to discussing actual routing one should consider how the present invention software translates digits dialed by the user into a call address that can be routed. This section describes the number translation process.

Routes and Route Information. Describes the concepts of routes and how routes are used in order to complete calls. The information that is contained in each route and how that information affects the behavior of the system is also discussed.

Routing Models. Explains the different types of routing models that exist based on how routing information is distributed in the network. Local routes static global disseminated and dynamic routes are all discussed.

Routing Manager. Having discussed the principles behind a route this section discusses how routes are managed and general settings that are used to control the routing process.

Routing Servers. To facilitate the exchange of routing information between different gateway servers the present invention provides routing servers. Routing servers can be used to centralize the administration of call routing in the network.

The gateway application normally collects digits from the user to determine what number they wish to call. However the routing system is based on routing numbers in a specific format. Specifically the routing system in the present invention is based on routing E.164 numbers comprised of a country code an area code a local number and an optional extension. These E.164 numbers also called E.164 addresses are usually displayed as follows 

In the above CC would be replaced with the country code AC with the area code LN with the local number and EEE with the extension. The routing system is capable of routing numbers in this format so the string dialed by the user is translated into the format shown above. For example the following translation would be used to make a call 

Although the above example is quite simple certain countries have complex system for number translation. In these situations the number of digits in the area code and local number may be variable. The subsections below explain the method used by the system to perform number translation.

The E.164 Parser shown as element in is part of Subsystem of the Routing Manager in the gateway server. The E.164 Parser is responsible for translating the digits entered by the user into E.164 form. The E.164 Parser operates using tables that are locally defined on each gateway server. However it is possible to allow E.164 Parser data to be synchronized automatically to prevent the need to update E.164 Parser tables on all gateway servers each time a change is to be made. The synchronization process is described in the next section and is shown in .

A parser subsystem is maintained locally on both the gateway server as a subsystem of the Routing Manager and the routing server. These two components maintain a connection with each other. Each parser maintains a listing of translation patterns steps and . Each parser maintains a local table for parsing addresses steps and . If synchronization is enabled steps and the two components connect steps and and the parser on the routing server sends new and or updated parsing information data to the parser on the gateway server steps and . In this way numerous gateway servers can be synchronized with the latest parsing data from a centralized location.

The E.164 Parser operates by matching patterns in the E.164 Parser table with the digits dialed by the user. Each table entry specifies the pattern of dialed digits that should be matched as well as information on how to translate those digits. Table entries are organized by country codes table entries within each country should be set up for which numbers can be parsed. The gateway server is installed with a default set of tables but E.164 parsing information should be provided for countries not set up by default. It is also necessary to update E.164 parsing information to reflect actual changes to the numbering system in the world.

The country list is a standard list selecting a country will allow its entries to be added or removed country codes may also be added. Once a country is selected a user is able to configure the table for that country as well as configuration settings for that country. As shown in general panel for a country allows one to enter the country code and country name for the country that her or she is configuring. General Panel is one of two Tabs in screen . The country code cannot be changed however once the country has been added.

Address List panel shown in allows the actual translation table for the country to be set up. All existing configured patterns are listed and can be modified or removed. Additional entries can be also be added.

There are two pieces of information that need to be configured for each entry in the E.164 Parser table. The first is the actually pattern specifying addresses that will match. This information is configurable under the Address panel when configuring a table entry and is shown in . Address panel is shown in screen . Screen has two Tabs .

Country Code. This is the country code to which the entry pertains and is not editable since the country which entries are being added to is already selected. When checking a number entered by the user the E.164 Parser starts at the left of the entered digits and attempts to find a matching country code for the first digit entered. If it fails it tries again for the first two digits then the first three digits and so forth. Once a country code is selected the E.164 Parser proceeds to the area code checking step.

Area Code. The digits following the country code will be compared against the area code field. If the digits following the country code match the value entered in the area code field then checking will progress to the local number stage. Since it is not desirable to enter every conceivable area code it is possible to wildcard the area code. Wildcarding is accomplished by entering A in the place of a digit that is to be matched and will allow any digit to be matched. For example the pattern 4AA will match any three digit sequence starting with the digit 4. However once one uses a wildcard digit all digits to the right of that point should also be a wildcard. Using the above example 4AA is a valid entry for the area code field but 4A4 is not.

Local Number. If the area code field matches then checking will proceed to the local number stage. At this point the digits following the area code will be compared against the digits specified in the local number and a match will be checked for. If the digits match then the checking will proceed to the extension stage. As with the area code it is possible to supply wildcard digits in the local number field by using the symbol N . Thus 123NNNN will match any seven digit local number as long as it begins with 123 . Additionally it is possible to specify optional digits using a lowercase n . For example 123NNnn would match numbers starting with 123 with between 5 and 7 total digits. Note that all characters to the right of an N should either be another N or an n and that all characters to the right of an n should also be an n . Finally if one uses optional wildcards the extension field should be blank.

Extension. For certain applications it is desirable to allow an extension to be explicitly represented. For example a gateway server connected directly to a PBX whose main number is 1 703 555 1234 might want to terminate calls to 17035551234 followed by any four digits assuming four digit extensions on the PBX . The extension field is optional and be left blank in which case extension checking is bypassed. If present the extension field specifies digits that must be matched in the digits dialed by the user that follow the local number. As with the local number field it is possible to use E as a required wildcard character and e as an optional wildcard character.

These wildcard characters form the basis of the call matching and prioritization features. shows the E.164 Parsers on gateway server although the parser routing manager and other components are available on all gateway servers . show the parsing and wildcard embodiment of parsing respectively. In receiving call information data step the E.164 Parser performs the steps of determining the country code step retrieving the pattern information step determining the area code step determining the local number step determining the extension step . During this time the E.164 Parser can utilize the wildcard routine to assign priority and structure to the matching routes found above.

Wildcarding is shown in and is described above with respect to the use of large and small letters to substitute for missing numbers in a E.164 address. Specifically wildcarding allows for the prioritization of partially matched routes by sorting based on fewest wildcards of the lowest degree. This prioritization is described in detail in the next section. The parser does high level parsing of the route and provides the parsed address information step . The parser then attempts to match the values for the area code based on the parsed country code step . The parser then moves to the phone number step and extension step respectively. The results are prioritized based on the fewest wildcards which correlates to the most matching digits step . The results are outputted as matched E.164 addresses step .

The second panel under a pattern entry for a particular country Extra Settings allows one to configure the number of extra digits that will be matched with the pattern. If a pattern matches the dialed number but additional contains extraneous digits then the extra digits setting will be consulted. If there are fewer extra digits than specified in this setting then the pattern will be considered to match and the extra digits will be discarded. Otherwise the digits entered by the user will not be matched.

Another important concept in understanding E.164 translation according to the present invention is that of prioritization. There may be multiple entries that match a particular number dialed by the user. The E.164 Parser selects the table entry that has the greatest number of matching digits. For example if the number dialed is 17035551234 consider the following entries exist in the table for country code 1 

The matching table entry selected will be 1 703 555NNNN because it has the most digits matching. Note that although 1 70 35NNNNNN also matches the dialed digits fewer specific digits match in other words there are more wildcard substitutions . Also note that the result of using 1 70 35NNNNNN would have been different since it would have resulted in an area code of 70 and an eight digit local number.

91NNNN 8 digit excluding country code numbers beginning with 814295 will be considered to be in the 429 area code whereas numbers beginning with 814291 will be considered to be in the 42 area code. This true example taken from Japan illustrates how local number digits can actually alter the determination of what area code a number falls into.

The sections above discussed how E.164 pattern tables are used to translate numbers to an E.164 form. The E.164 Parser system is based on emulating the telephone number interpretation typically performed by PSTN switches. However this is not necessarily appropriate for all applications. For example when terminating traffic to a foreign area with variable length area codes it may be known only that all numbers are 9 digits in length when the area code and local number are combined. In such situations it is possible to forgo specifying the area codes and simply to treat the entire sequence of digits entered by the user as a long local number. In this case the area code field would be left blank and the local number would be NNNNNNNNN 9 wildcards . With this entry it would not be possible to know the area code that was actually dialed but this knowledge is not always required and using this approach can avoid the otherwise tedious task of creating a list of all existing area codes.

Note however that any routes configured on the gateway servers would also have to be for a nine digit local number with no area code.

The above sections described a key element the E.164 pattern tables that are used to control how digits entered by the user are parsed into a standard address form. However the tables that are used in doing this are relatively large and furthermore may change frequently if they are used to reflect the way that numbers are translated by the PSTN since PSTN carriers make frequent changes to the ways that area codes are assigned. In order to ensure that gateway servers continue to be practical to maintain it is possible to synchronize E.164 Parser data with a centralized source. Whenever a change is made to the centralized version of the data maintained on a routing server discussed below the change will automatically be propagated to the gateway servers that are synchronized with that version of the parser data as shown in discussed above .

On a gateway server E.164 Parser data synchronization is configured on the E.164 Translation node described above in the section on the E.164 Parser. In the box labeled Synchronization Mode there is a button labeled Change that can be used to control how synchronization is performed. There are three options 

No Synchronization. In this mode E.164 Parser data must be configured independently on the gateway server. Changes to E.164 Parser data elsewhere in the network will not affect the way that the gateway server being configured parsers E.164 numbers.

Client Synchronized. In this mode E.164 Parser data will be synchronized with a server that provides E.164 Parser data. This mode should only be selected on gateway servers not routing servers described below except in specialized cases. In this mode the contents of the local E.164 Parser tables will be kept consistent with those of a listed server. Whenever a change is made to the data on the server the local gateway server will automatically receive those changes and update its local database. Because the local database is maintained the number translation process remains very fast so that overall call setup time is not impacted. The IP address and port number of the server are required when selecting this mode of operation.

Server Synchronized. This synchronization mode is not generally useful for gateway servers. For routing servers described below this mode allows gateway servers to synchronize with the contents of the local E.164 Parser tables. Any changes made to the local tables will be propagated to the gateway servers that list the routing server being configured as their server during Client Synchronization mode setup. Additional setup needs to be performed in order to control which gateway servers are allowed to connect and retrieve data this is described when the routing server is discussed.

An important concept in understanding how calls are routed by the system is that of a route. A route at a simple level is a grouping of information that tells the gateway server how to make a particular call. For example a route could tell the gateway server to make calls to a particular area code via the gateway server located at IP address 192.168.1.3. Similarly a route could tell a gateway server that in order to make calls to a particular number it should use a particular set of telephone lines and dial a specific sequence of digits. In general most calls involve the use of two routes. On the originating Gateway a route will exist supplying the address of the terminating Gateway. At the terminating Gateway a route will exist supplying the actual number to send to the attached telephone equipment and allowing the call to be placed. The former being a network route and the latter being a telephony route.

The information actually contained in a route is significantly more complex that the simple description above. Information on prioritization timing and access control are also contained in a single route. This section describes the key information contained in a route.

There are four main groups of information that are contained in every route that can be configured which deal with different aspects of routing. These groups are as follows 

Additional information may be contained in a route depending on the type of the route. The sections below discuss the information that is common to all routes regardless of their type. The screens shown in are for locally defined routes. However the panels are common to other types of routes as well. One may expand the Routing root level configuration tree node and double click on the Local Routes window. From the local routes window one can either add a new route or modify an existing one.

The routing address panel shows the list of addresses that will be matched by a particular route. For example if an address matches 1 703 NNNNNNN then whenever the user dials a number with country code 1 area code 703 and 7 digits in the local number field it will be handled by this route unless there is another matching route of higher priority . shows the address list panel in screen . Tabs allow access to other panels discussed in detail below.

Under normal conditions a route will only have a single address entry associated with it. The reason that additional address entries are allowed is to provide flexibility in addressing very specific applications.

Remember that E.164 translation happens prior to routing. Therefore numbers will already be in CC AC LN EXT format before the routing process commences. This provides increased flexibility since it is not necessary to specify how the number is to be interpreted. For example a route could exist for 1 Aaa NNNnnnn. This would match any number in country code 1 with a 1 3 digit area code and a 3 7 digit local number. It is not practical to do this at the E.164 translation stage since a number like 1703555 could be interpreted as 1 703 555 1 70 3555 1 7 03555 and so forth. However at the routing stage it makes addressing highly flexible even a country with a complex area code system like Japan could be routed to with a single route for 81 Aaaaa NNNnnnnn.

When a new route address entry is added or an existing route address entry is modified Routing Entry Properties dialog will appear for configuring the route address entry. The fields in this dialog are shown in and explained below 

Call Address. This group of fields specify the address pattern that must match the address entered by the user in order for this route to be selected. In one example only E.164 addresses are supported however other types may be supported. For E.164 addresses it is necessary to provide the country code area code local number and extension of the addresses that should be matched. The same wildcards described when E.164 translation was discussed could be used. However as discussed above some restrictions regarding the use of wildcards are relaxed. Specifically using optional wildcard characters does not require that all subsequent fields in the address use only optional wildcards. For example Aaa can be used in the area code field without requiring that the local number field consist solely of n s. However restrictions within a field fixed digits must precede required wildcards which must precede optional wildcards still exist.

Line Group Type Instance. When the gateway server is placing a call using a particular route it is necessary for a line group to be selected in order to make that outbound call. The line group type and instance allow a particular line group to be identified in which case calls using this route will only be placed using that line group. In addition if the line group type is set to dynamic then an appropriate line group will automatically be selected based on the contents of the route and availability of individual lines.

Rate Modifier. The gateway server is capable of rating calls and charging for those calls. The section on call rating in the gateway server Capabilities section describes the rate modifier and how it is used in determining the cost of a call to the user. The value entered in this field as the rate modifier will be passed to the call rating function when determining the charge for a call.

Disable Route. In order to allow calls to specific numbers to be restricted it is convenient to create routes that prohibit access to the number instead of allowing it. The Disable Route field is used for this purpose. A disabled route will be treated like a normal route and prioritized as if it was a normal route. However when the list of routes is prepared all routes lower in priority than the highest priority disabled route will automatically be rejected. For example it is possible to reject calls to all numbers beginning with 911 in North America with just a single route for 1 AAA 911nnnn with Disable Route selected.

Device Type. Two kinds of underlying devices can be used to place a call based on a route telephony devices and network devices. The kinds of information used by a network device to place a call is obviously different than the information required by a telephony device. This field allows the type of routing information being supplied to be specified. Note that specific fields may change depending on the type of device selected. This field could sometimes be referred to as the route type e.g. network routes and telephony routes but is not referred to this way herein to avoid confusion with route distribution types local dynamic etc. .

Remapped Number Station Address. This field appears for Telephony Routing device types only. The remapped number field allows one to specify the digits that will actually be sent to the connected telephone equipment when a call is placed using this route. The remapped number may contain the same wildcards used in specifying the address of the call but may not exceed the number of wildcards contained in the address. For example if the area code field reads AAA then a remapped number of AA would result in the first two digits leftmost of the area code being sent to the connected equipment. A remapped number of AAA would send all three area code digits to the connected equipment and a remapped number of AAAA would be invalid. Placing optional wildcards in the remapped number will result in a substitution if a matching digit exists in the actual address and no digits if no such digit exists. The format of the station address field is identical. However the station address is used to select a particular line for placing the call and does not affect the digits sent to the connected equipment.

Host IP Port. This field appears for Network Routing device types only. This field is used to specify the IP address and port number of a gateway server or H.323 terminal that will complete calls to a particular number. The default port numbers should generally be used unless otherwise required.

Enable Voice Fax. Controls the kinds of calls that will be enabled. These fields are optional. Voice calls should always be enabled voice calls are dynamically switched to fax when the appropriate tones are detected.

Proprietary H.323. This field appears for Network Routing device types only. Since the gateway server supports multiple protocols for actually placing a network call it is necessary to specify which protocol will be used. Calls handled by other present invention gateway servers should select the Proprietary protocol or non proprietary protocol whereas calls to H.323 terminals such as Microsoft NetMeeting should select the H.323 protocol.

The ordering information panel for a route shown in is very simple and provides parameters that govern the order in which a route is selected. Two parameters can be modified through this page preferability and a cost estimate. Both of these parameters affect the order in which routes are selected however the exact relationship between these parameters and order is determined based on configurable parameters that are discussed under the General Settings section below.

It is possible to restrict the times of the day as well as the days of the week during which a particular routing entry may be used. Possible applications of this capability were already discussed above. shows timing information panel .

Route timing restrictions apply to use of the route which occurs when the call is initiated. In one example if a call extends beyond the time in the call route it will not be automatically disconnected. For example for a route enabled from 9 00 am to 5 00 pm a call placed using that route at 4 59 pm will be allowed to continue indefinitely past 5 00 pm.

Use Timing. This flag controls whether or not route timing restrictions will be used. If disabled a route can be used at any time of day. Otherwise the time restriction table will be used to determine if the route can be used.

Use Local Time Time Zone. If selected use local time means that timing information in the route will be assumed to be for the local time zone. If such routes are transferred between different systems then the timing information will be interpreted according to the local time on the gateway server that uses the route. This may or may not be the desired behavior. For example consider a route is valid between 9 00 am and 5 00 pm local time distributed to two gateway servers one on the east coast Eastern Standard Time and one on the west coast Pacific Standard Time . The east coast gateway server would allow use of this route between 9 00 am and 5 00 pm EST and the west coast gateway server would allow use of this route between 9 00 am and 5 00 pm PST. However if local time zone is not checked then the time zone relative to GMT can be selected. For example if the time zone in the example above was GMT 5 00 EST then the east coast gateway server would allow calls between 9 00 am and 5 00 pm EST but the west coast gateway server would only allow calls to be made between 6 00 am and 2 00 pm PST.

Allowed Usage Times. A list of allowed usage times is managed for each route that has timing information enabled. Each entry in the list specifies a time range during which the route may be used. An arbitrary number of entries may be added. Each range entry specifies a starting day and time and a finishing day and time. If at least one matching timing entry exists at the time and day of week that a route is considered then the route will be used.

The access control panel shown in allows restrictions on users that can and cannot use a route to be configured. The access control system is highly flexible allowing a wide range of conditions to be implemented.

The list allows an arbitrary number of access control entries to be configured. When considering whether or not a particular user is allowed to make use of a route the system begins with the first route in the list and proceeds through the access control list until it finds a matching entry.

Route Access Type. Each route access entry can either grant access or deny access to user. Since the first matching entry in the route access list will be used to determine whether the route will be accepted or denied it is possible to set up complex restrictions. For example it would be possible to grant access to a particular group of users but to deny access to one particular member in that group using two route access entries. The first which occurs higher in the list would deny access to the particular member. The second would grant access to the group. Since the first entry in the list is processed first the deny access result would occur for the particular member for whom it was desired to deny access.

Call Charging. This option determines how call charging should be performed for calls that are placed using this route and when this route access entry was selected. For example consider a user placed a call using a route and granted access under an access entry that specified that Debit is required. In this case the user would be required to have debit enabled on their account as well as a sufficient balance in order for the call to occur. A detailed description of the options for call charging are described in the section on gateway server Capabilities in the section on Call Rating.

Call Rating Type Profile. This selects the call rating type and profile used to actually bill the call if the call is to be billed. These parameters are also explained fully in the section on gateway server Capabilities in the section on Call Rating.

Requirements. This list specifies conditions that should be met in order for a route access entry to be selected. If any of the conditions in this list are not true then the route access entry will not be selected and the next route access entry in the route access entry list will be considered. This is a standard list allowing individual requirements to be added and removed. There are several kinds of requirements that can be configured 

From the previous section it is clear that there is a significant amount of information contained in each route. Because of this it is highly desirable to minimize the number of times that the same routing information must be entered. In order to provide flexibility while keeping administration to a minimum the present invention software supports four models for how routing information can be distributed around the network. These models are not exclusive in other words one does not need to select a single model. Routes of all four types can be used on a particular gateway server.

Locally defined routes more commonly referred to as local routes are routes that are defined on a single gateway server. Shown in they are not by default transferred to other gateway servers or shared with a routing server. The route exists locally on that gateway server.

The benefit of a locally defined route is that it is simple to configure since it does not require a routing server to be used. It is also efficient since it is available locally to the gateway server so it can be found immediately without making a request to a distant routing server. The Routing Manager queries for matching local routes step and is either provided with a route and provides it so that the call can be connected steps and or it looks for routes elsewhere step . The drawback to a local route is that if there are a large number of gateway servers it becomes difficult to administer local routes on each gateway server.

Steps in are replicated as steps in steps to in and steps in . These steps allow for various routing models to be used in combination. If the system does not find a matching route it will attempt to use other routing models step . If other models are not available steps the system will provide a lack of service notice to the gateway which can pass this information along to other parts of the system. If other models are available then they will be implemented step .

However local routes are an important part of the dynamic route scheme described below. Local routes can be exported to a routing server. Exported routes are not an exact duplicate of the locally defined route and are considered to be a different kind of route. However dynamic routes exported local routes are derived from the information contained in a local route. Dynamic routing is defined in more detail below and how a local route is transformed into a dynamic route is described in the section on routing servers. Export configuration panel is specific to local routes. Shown in panel determines whether or not a particular route will be exported and transformed into a dynamic route. This panel appears when creating or modifying local routes and includes the following information 

Enable Export. If this flag is selected then the route will be exported to the routing servers listed in the export list.

Export List. This list contains the names of the routing servers to which the route should be exported. Routing servers and exporting routes is described further in the section on routing servers below.

Static global routes are routes that are statically defined on a routing server. Shown in they are very similar to local routes but since they are defined on a routing server numerous gateway servers can query them. Static global routes are not downloaded to the gateway server rather when a gateway server wishes to place a call to a particular number Routing Manager on the gateway server will ask the routing server for any routes that match the number entered by the user step . The routing server will determine if there are any matches step and return any static global routes that match the query in addition to any dynamic routes described below step . The Routing Manager will then check for matches step and provide them to the gateway server for connecting step . The Routing Manager will perform any other searches for which it is configured steps and .

The advantage of using static global routes is that it simplifies administration even across a relatively large number of gateway servers. Static global routes generally require consistency between the configuration of routing servers and the configuration of gateway servers. For example if a routing server directs all calls to a particular number to a gateway server a network route that gateway server will need a matching telephony route enabling it to place the call on the telephony network. In some cases however gateway servers should query the routing server at the time of the call in order to obtain those routes which can increase call setup time.

Shown in disseminated routes are routes that are defined on the routing server but distributed to gateway servers at the time that the gateway server connects.

The advantage of using disseminated routes is that a single route can be disseminated to multiple gateway servers without requiring any work for each gateway server that is to be disseminated to. Any change made is automatically propagated to all gateway servers. At the same time because each gateway server has a local copy of the disseminated route routing remains highly efficient. However in some cases when using static routes and disseminated routes there is a need to maintain consistency between the routes for the originating gateway server a network route and the terminating gateway server a telephony route .

Dynamic routes are routes that are exported dynamically by gateway servers to the routing server as shown in . show the routines for receiving exported local routes transforming local exported routes respectively. shows a component flowchart of the steps involved in exporting a local route and is described in detail below.

When a local route is marked for export it is transformed into a dynamic route and is available on the routing server to be queried by other gateway servers. shows a flowchart diagram of the exportation process. Upon connection the routing server requests any exportable local routes from connected Gateway Servers . . . step . The routing server receives these exported routes step and after performing transformation and storage steps and updates its listing of routes step from previous exportation so that no dead or otherwise duplicative and or out of date routes are retained and possibly used by the system.

The transformation process step is shown in block diagram form in . After receiving the local exported routes step the routing server checks the route s address entry step . The route s timing information step and access entry step as well as its ordering information step are also checked. The routing server then adds a unique identity to the route step and adds the identity of the exporting gateway server step . The routing server also add a date and time stamp which denotes when the route was obtained from the gateway server step .

A more detailed illustration of the present process is shown in . The Routing Manager connects to pre configured routing servers step . Any exportable local routes are exported steps and . The exported local routes are transformed into dynamic routes steps and . The Routing Manager queries for matching routes step and is provided with matching dynamic routes steps and which are cached by the Routing Manager step in a dynamic cache discussed below.

There are several advantages to using dynamic routing. Firstly it simplifies administration since routes can be shared between gateway servers effortlessly. Secondly it does not have the consistency problem of static and disseminated routes whereby the pair of network and telephony routes must match. This is because the exported route will normally be transformed from a telephony route into a network route but all other information in the route will remain the same. Thirdly it improves the resilience of the routing process to the failure of a gateway server if a gateway server fails its routes will automatically no longer be available and other gateway servers will route calls as if the gateway server that crashed did not exist. Normally gateway servers would try to route to the failed gateway server and only after a timeout occurred would they fallback to alternate routes. The disadvantage however of using dynamic routes in some cases is that the gateway server must query the routing server at the time of the call increasing call setup time.

It is not necessary to actually set up dynamic routes since gateway servers export them based on information in a local route. The parameters that affect the transformation process are shown in and discussed below as well as in the section on routing servers which follows.

Above the four types of routes were presented. Among those types static routes and dynamic routes had the disadvantage that it is necessary to query the routing server on a per call basis to obtain the routes for that call. This increases the call setup time which may be critical in some applications. To reduce the impact on call setup time introduced by these two types of routes the Routing Manager built into each gateway server is capable of caching routes that are obtained dynamically for the routing server. This feature is discussed when describing the routing manager below.

The following table presents a comparison between the four different kinds of routes and is a summary of their benefits and disadvantages in certain examples 

The Routing Manager is a built in component of the gateway server. It is responsible for making all routing decisions and for managing all the routes used by the gateway server. The Routing Manager has the following responsibilities as shown in 

The main configuration screen for the Routing Manager is found under the Routing root level node of the configuration tree. Expanding this node will show the other options available. Window as shown in appears as described below 

Clicking on the Change button allows the general settings to be modified. There are three parameters that can be configured as follows 

Dynamic Routing Usage. Selects when a query is issued to the routing server in order to obtain routes dynamically. This includes obtaining statically configured global routes not just dynamic routes . There are five options as follows 

In ordering routes By Address refers to how many exact digit matches occur in the address. For example if the user dialed 1 703 5551234 a route to 1 703 555NNNN would receive a score of 7 whereas a route to 1 703 NNNNNNN would only receive a score of 4. Higher scores are more preferable.

Routing Server List. This list shows the routing servers that the Routing Manager interacts with and shows the current state of the connection to that routing server. Routing servers can be added and removed or their settings can be modified. When adding or modifying a routing server entry a significant amount of configurable parameters can be specified. These parameters are discussed below.

Local routes were already described at length previous sections and how to configure a local route has been explained. In order to access the local route list double click on the Local Routes node under the Routing root level configuration tree node. This will display the local routes screen . Screen contains a list from which local routes can be added removed or modified. The local route list screen is shown in .

The Dynamic Cached Routes window not shown which can be viewed by double clicking on the Dynamic Cached Routes node under the Routing node shows the dynamic routes that are currently cached by the Routing Manager. This screen provides caching information.

When adding or modifying a routing server a large number of configuration parameters are available. These configuration parameters are split into seven panels shown as Tabs in screen of each of which are described below. Note when viewing the configuration for a routing server that it is necessary to click on the change button in order to modify the configuration.

The general panel shown in is used to specify general information about the routing server. Each of the parameters is discussed below.

Server Name. Defines a local name for the server. This name is used when identifying which servers local routes should be exported to. Note that the server name cannot be modified once a server has been added.

IP Address Port Number. Defines the IP address of the routing server. The port number should be left at the default unless one is specifically running a routing server on a different port number.

Send Exported Routes to Server. This parameter can be used to prevent any routes from being exported to the server. If this parameter is not enabled then no routes will be exported even if individual routes indicate that the route should be exported.

Accept Disseminated Routes from Server. If checked then any routes disseminated by this routing server will be accepted. Otherwise routes will not be accepted from the routing server. If dealing with a routing server that is not trusted disseminated routes should not be accepted since they can instruct a gateway server to place long distance calls via the telephone equipment to anywhere.

Use Imported Route Parameters for Disseminated Routes. If checked then the parameters from imported routes will be used when the routes are disseminated. Route parameters include ordering access and other information. Local routing patterns may differ from the place of the route s origin. If so then this should be unchecked.

Search Order. Multiple routing servers can be configured. Search order controls the order in which routing servers are used to obtain routes dynamically. All routing servers marked First will be searched first. If all routing servers fail to find any routes then all routing servers marked Second will be searched. This progresses until either routes are found or no more routing servers are available to be searched.

The exported routes usage panel shown in allows one to override the settings of local routes that are exported to the routing server. This is part of the transformation process that a local route undergoes when it is transformed into a dynamic route. Exported routes will usually have their usage information changed in Usage Info panel . IP Address and port number information as well as protocol preference can be set in the Network Route Setting panel . The Routing Manager makes these changes before the route is sent to the routing server.

The exported route access panel shown in allows the route access settings in a local route to be replaced. Normally it is desirable to remove route access settings sent to the routing server since each gateway server will determine what route access conditions should apply. Configuration of the route access settings is identical to the configuration performed when defining the local route.

When exporting a route to the routing server it may be desirable to customize ordering information prior to actually exporting the route. The exported routes ordering panel shown in allows one to do this and includes the following information 

Preferability. If one is overriding the ordering information contained in the route this field allows one to specify the preferability parameter that will be applied to the exported route.

Cost Estimate. If overriding the ordering information contained in the route this field allows one to specify the cost estimate that will be applied to the exported route.

The import route usage panel shown in allows filtering of the types of routes that will be accepted from a routing server. This can be used for example to ensure that telephony routes are not accepted from an untrustworthy routing server since such routes could cause the gateway server that receives them to make long distance calls on attached telephone devices. shows this panel. Panel contains the following 

Routes Info These fields allow you to specify which types of routes will be accepted from the routing server.

Usage Info This field allows you to configure how usage information in the route will be modified if at all. Modification may be enabled to change the rate modifier field of the route. The other route usage information parameters cannot be specified for imported routes.

The imported route access panel shown in is used to replace the route access information on routes imported from the routing server. Often each individual gateway server may define its own users and its own set of permissions on what calls can be made by the user. However routes from the routing server will typically not contain access settings that implement the desired behavior. This panel allows route access information to be overridden to implement the local policy for route access. Configuring the route access information is identical to configuring the route access table for a local route.

The imported routes ordering panel is identical to the exported routes ordering panel and is shown in . However it is used to modify imported routes obtained through a dynamic query.

The above sections described the principles of routing in the present invention and discussed the Routing Manager that is part of the gateway server. An important component that was referenced significantly in the above discussion is the routing server. The routing server is a critical component in facilitating the exchange of routing information between different gateway servers and for centralizing and simplifying the administration of routes.

This section describes the routing server and how it can be used to deliver the routing capabilities described above. The sections below describe different aspects of the routing server.

The main routing server configuration window can be viewed by double clicking on the Routing root node of the configuration tree when connected to a routing server. Window is shown in and allows client setup to be performed.

The top part of window in contains List of Clients panel . Panel can be used to configure the list of routing clients that are allowed to access the routing server. Groups of Aliases panel contains a listing of groups of clients. This feature allows for easier management of clients. These clients are gateway servers that are set up to connect to the routing server. Unless a client entry exists for a connecting gateway server the connection will be denied.

When adding or modifying a client entry in the client list several settings can be configured. These settings are described below. The configuration of each client is divided into four panels.

General panel shown in is used to specify general settings regarding the client. General Settings panel contains 

Disseminate Routes to this Client. This field controls whether or not any routes can be disseminated to this client and must be enabled to allow routes to be disseminated. If disabled this parameter overrides the dissemination settings in individual routes.

Local Alias. Routing clients may have a local alias. Multiple clients may share a single local alias. The purpose of this local alias is to provide a simplified means for identifying a client or multiple clients. Aliases are the first level of grouping and all clients are required to have an alias. If one does not require the first level of grouping then one should simply use the client name as the alias name.

Description. The description allows text to be entered for informational purposes only. This information is not used by the system.

List of Identities. This field contains the list of identities that are associated with this client entry. The configuration of the identities is identical to the configuration explained herein when setting up the management client access list. The same procedure should be followed when setting up a routing client entry the only difference is that this list controls the gateway servers that can access the routing client for routing purposes. Placing an identity in this list does not allow that entity to connect for administrative management purposes.

Groups Belonging To. This list provides an easy way to add the client being configured into routing groups which are described below. It also provides a simplified way of determining which groups the client is already a member of. However it is necessary to take care when modifying group membership since ALIASES are members of groups not individual clients thus removing group membership removes the membership of the entire alias.

The routing usage panel allows usage information in routes exported by the client to be replaced with specific routing information. Normally this is used if the exporting gateway server is not fully trusted and it is desired to ensure that all exported routes received from that gateway server are directed to the IP address of the exporting gateway server. The operation of this panel however is identical to the one found when configuring the Routing Manager component of the gateway server and is described in the previous section.

The routing access information supplied in routes exported by individual gateway servers may not match the routing access information that it is desirable to export network wide. For example a gateway server might define route access settings that only apply to its local users the network wide scheme might specify different route access settings. Routing Access panel an example of which is shown in allows the route access information supplied in routes exported by the gateway server to be overridden using settings that are defined on the server. The route access list is defined exactly the same way as for a local route.

Similar to usage information it is possible to override the ordering information supplied in a route exported by a gateway server. This panel allows this to be performed in an identical manner to the way it is performed by the Routing Manager on the gateway server side.

The routing server allows the definition of groups of aliases. Wherever an alias name can be supplied such as in the list of gateway servers to which a route can be disseminated it is possible to use a routing group name instead. This permits large scale operation of the routing server. For example consider a routing server that manages routing across four carriers each of which has 10 Gateways in each of three countries. This is a total of 120 gateway servers. Each one would have a client entry allowing it to connect to the routing server. For each carrier three aliases would be defined one for each country served by that carrier. At the group level each carrier would have the aliases for each country grouped into a single group entry for that carrier. This would allow a route exported by one carrier to be available by the three other carriers but would still allow a particular route to be disseminated to all the Gateways in one particular country.

Routing groups can be added and removed from the general panel shown above. The only thing required to create a routing group is the name of the group. Once created members can be added or removed from the routing group.

The Exported Routes window is available by double clicking the Exported Routes node under the Routing root node in the configuration tree. This window displays all exported routes that are currently present on the routing server and the name of the gateway servers that exported those routes. Window is shown in and described below. One should not make any configuration changes using this window but it is possible to use this window to verify that routes are being exported successfully.

Static Routes can be configured on the routing server by double clicking the Static Routes node located below the Routing root node in the configuration tree. As shown in window in the list of routes statically defined on the routing server will be displayed. The route list is a standard list that allows routes to be added removed or modified.

When adding or modifying entries in the route list the route properties page is identical to that for a local route except that the export list is not present.

Disseminated routes can be configured in the same way as Static Routes. The dynamic route list is available by double clicking on the Disseminated Routes node located below the Routing root node in the configuration tree. The Disseminated Routes window which is almost identical to that for static routes is shown in .

When adding or modifying routes that are contained in the disseminated routes list additional Properties window will appear that allows control over the clients to which the route will be disseminated. Panel is shown in and includes the following information 

Disseminate to All. If selected this flag will cause routing data to be disseminated to all clients that do not explicitly disable dissemination of routes.

Dissemination List. This list provides the name of all aliases and groups that are defined on the routing server to which this route will be disseminated. Unless disseminate to all is selected only clients in this list will receive the route being configured.

Alias Group List. This list provides a list of all aliases and groups to which this route is currently not disseminated. Entries can be moved from this list to the dissemination list to add it to the dissemination list or vice versa to remove it from the dissemination list .

The exported routes are transformed on the routing servers steps as described in . These exported local routes are then stored on the routing servers as dynamic routes. As discussed above in disseminated routes are imported to the gateway servers from the routing servers steps and . For practical purposes the gateway servers are now ready to handle calls and simply wait for them to come in steps and .

In response to call related information the Routing Manager would make a query for a route step . Depending on the configuration of the system various routing models can be used to provide potential routes. As discussed previously dynamic and static global routes are cached step . The matching routes are prioritized step . Similar operations are being performed on other Routing Managers In response to call related information other Routing Managers would make a query for a route step . Depending on the configuration of the system various routing models can be used to provide potential routes. As discussed previously dynamic and static global routes are cached step . The matching routes are prioritized step .

This section introduces the basic principles of operation behind the database server as well as how gateway servers access the database server. This section provides the background knowledge necessary to understand and configure the services that depend on the database server which are discussed in the following sections.

This section is divided into two sections as follows. The first section deals with database issues on the gateway server side. The second with general issues on the database server side.

Gateway Access to Database Servers. Describes how a gateway server can be configured to access multiple database servers and how multiple database servers can be used with each of the services provided via the database servers.

Database Server General Setup. Explains the use of the management system to modify general database server settings.

Database Server Access Control. Describes how to configure the clients of the database server a necessary step in order to allow gateway servers and provisioning systems to connect to and make use of the database server.

Similar to the Routing Manager component of the gateway server discussed in the previous section a Database Manager component also exists as part of the gateway server. This component is responsible for managing access to database servers and for coordinating requests issued to multiple database servers. Double clicking on the Database Server Access root level node of the configuration tree accesses the Database Manager configuration screen . These directions should be performed when connected to a gateway server not when connected to a database server. shows the Database Manager configuration screen .

The database server list is like the routing server list. It is a list of the database servers that the gateway server has been configured to access. When adding or modifying an entry in the database server list dialog represented by will be displayed allowing one to enter information about the server.

Server Name. Name of the server being configured. This name will be used to identify this server entry when configuring the services that make use of database servers. Once the server has been added the name assigned to it cannot be changed.

Host Name Port Number. The hostname or IP address and port number of the database server that is being configured. The port number should be left at the default value unless you are specifically operating a database server on a different port number.

The Database Manager component allows Database services described in the following two sections to access any of the servers that are available. The configuration of how servers are accessed is similar to that for routing. Like routing ordering information can be supplied that determines what order the servers are used in. database servers are organized into groups much like routing servers are placed into ordering levels. Operations are performed on every database server in group 1. If none of them handle the operation then the operation is retried on every database server in group 2. This continues until no more groups are defined or until at least one database server processes the operation successfully. There are two main differences however between database server request processing and routing server request processing 

A database server can be in more than one group. For example Group 1 could contain Server A and Server C and Group 2 could contain Server B and Server C.

Ordering Grouping information is configured on a service by service basis. For example the User Management service could use a different set of servers than the CDR Collection service.

The ExpresConfig program was used to perform the initial set up of the database server. In the event that a change to the configuration of the database server is necessary the management system should be used to make the change. Using the management system to administer such items as the management access control list or identification authentication configuration was discussed in above. However it may also be necessary to make changes to the data source configuration that controls how the database server establishes a connection to the underlying Database.

When connected to a database server using the management system double clicking on the Database root level node will display the main Database Server Window as shown in . By clicking on a Change Settings button within the Server Settings Panel it is possible to modify the general server settings that define the data source and database settings. Note that one should not change the port number under normal circumstances. The list of Clients gateway servers is shown in panel .

The database server manages a significant amount of critical data. User records and call records are essential to the correct operation of the system and significant possibilities for fraud exist if an unauthorized user is able to obtain access to modify or even just to view the data that is managed by the database server. For this reason it is necessary to control access to the database server.

Database server access control works in the same way as management access control and routing server access control. Like the routing server it is necessary to create a client entry for each gateway server that connects to the database server. It is also necessary to create a client entry for every provisioning system that accesses the database server. The client list can be modified through the bottom portion of the main database window.

This section covers the management of end users of the present invention and describes the aspects of the system that are specific to handling details associated with the end users of the present invention. All aspects of user account setup grouping of user accounts accounting for calls made by users setting up of debit information for users and other such information is discussed in this section.

This section is divided into several sections that deal with different aspects of user management. The sections are as follows.

User Management Concepts. Discusses the main ideas of user management in the present invention. The main types of records that are maintained for the purpose of user management are discussed and the interaction between these records is explained.

Gateway Server Access to Users. Describes the user management service that is part of the gateway server and how it needs to be set up to obtain user records from the database server.

Managing User Records. Describes how the provisioning system can be used to set up and manage user accounts.

Managing Account Records. Demonstrates the setup and management of account records including debit capability.

This section begins with a description of the fundamental purpose behind user management. Most importantly user management is not necessary for certain applications. Most often the purpose of user management is to allow an operate to charge for services provided by the present invention. For many enterprise applications the identity of the user that is making a call using the present invention is unimportant as is collecting records of all calls made by particular users. However in providing a revenue generating commercial service user management is critical.

Identification and authentication of users. Without management of users it would not be possible to distinguish between legitimate users and unauthorized users of the system. Sometimes the telephone equipment connected to the gateway server accomplishes this but generally user management is required in order to perform user verification.

Classes of service. In order to offer different classes of service differentiated by numbers that can be called or the quality of routes used to call those numbers it is necessary to differentiate between users. User management is required in order to do this. For example it may not be desirable to provide all users with the capability to call internationally.

User specific behavior. Some preferences and configuration may vary from one user to another. An example is the language preference of the user. This parameter may differ from user to user and hence it is necessary to differentiate between users.

Billing and Accounting. In applications where it is necessary to charge for services it is necessary to identify the users that should be charged for the service unless there is only one user of the system which is usually not the case .

Debit Capability. When the debit capability of the gateway server is being used it is necessary to manage users and their balances.

In the present invention system all records associated with user management are stored on the database server. Other components of the system such as the gateway server must communicate with the database server in order to obtain those user records. This simplifies control over access to the underlying database and allows multiple gateway servers to share the user database. Of course since multiple database servers can be operated it is not necessary for all gateway servers to use only a single database of users.

In order to provide the services described above it is necessary to maintain a record of each legitimate user of the system. With that record it is necessary to store information such as their language preference. A user record is the piece of data that contains most of the information that is relevant to the user. It contains things such as 

Additional identifying information such as Caller ID that can be used to automatically identify or authenticate the user 

An important piece of information in the above list is that only limited billing and accounting settings are stored in the user record. Most billing and accounting related settings are actually stored in account records which may be associated with multiple users. The purpose of separating accounting information into a separate account record described below is to allow a single account to be shared by a group of users. For example a corporate calling account might allow a group of users to be billed jointly while still providing individual users with their own IDs and passwords.

Group records are closely related to user records. The purpose of group records is to allow classes of users to be defined. A user may be part of either no group or one group. If a user is part of a group then certain settings in the user record may be left undefined and specified instead by the group record By taking this approach rather than specifying all information directly in the user record it is possible to make changes that affect a group of users simultaneously. For example consider issuing a batch of 2000 demonstration calling cards. If these calling cards need to have an expiration date and each calling card had a separate user account associated with it then it would be necessary to specify the expiration date for each one of those calling cards. If it was desired to change the expiration date for that entire batch of calling cards then every record would need to be updated or specialized tools for provisioning the database would need to be used. Instead it is possible to create a group record associated with the user record for each card and to make a single change to the group record.

For certain fields in the user record it is possible to specify that the value in the associated group record should be used as the value of that field. For example the expiration date in a user record could be set to use group record settings . With this setting the group record would determine what the expiration date of the account was. These settings can be made on a field by field user by user basis. For example consider two user records associated with the same group record. User record 1 could specify an expiration date of Jan. 1 2002 but with privilege levels defined by the group record. User record 2 could have a group specified expiration date but with a privilege level of 2. This provides the flexibility of using group records to represent default settings while permitting specific changes and exceptions on a user by user basis.

Much of the information in a user record can be left unspecified and determined by the values in the corresponding group record. These fields include but are not limited to 

In general because the use of group records in no way restricts the customization of each individual user record it is recommended that group records are used to specify options that are common across a group of users.

Account records provided the basis for real time debit in the present invention system. Although account records can be used in post paid applications it is often not necessary to do so. This is because a third party billing application that prepares bills using the call detail records is provided with data that identifies the exact user that made a particular call. From this point the third party billing application could use its own rules regarding whether the call should be billed to the user to a shared account directly to a credit card or in some other manner.

However for real time billing using the debit capability of the software it is necessary to define an account record. Account records define properties that are used for billing and may be associated with credit records to limit the amount of credit extended to a user or with debit records which are used to provide real time billing. Credit and debit information maintained by the system is always associated with an account record.

It is desirable to apply many of the capabilities provided by user management to gateway servers as well as to end users. For example it might be desirable to have a debit account for a particular gateway server or to control the permission levels granted to different gateway servers. In order to facilitate this the gateway server is capable of associating a user account with remote gateway servers that request calls.

The mechanism for performing this association is by using the Remote System ID a configurable parameter on each gateway server. This ID is used as if it was Caller ID information and is used to look up a matching user record. Details on setting this up are described below in the section on managing user records. It is also possible to use authentication information in the user record to verify the IP address of the remote gateway server.

This section describes how to set up the user management service on the gateway server. As described in the previous section database services each supply an independent list of the database servers that are to be used grouped according to the order in which they should be used to obtain user records. For gateway servers performing user management the principle type of operation used is that of obtaining a user record from the database server. It is generally not necessary for this kind of operation to perform the operation on multiple database servers at the same time. However it may be desirable to fallback to an alternate database server to obtain the user record if the normal database server that provides user records are obtained is not available. This section describes how to perform such a configuration of the user management service on the gateway server.

The server access settings for the user management service can be viewed by double clicking the User Management Service node visible when the Database Server Access root level node is expanded. The Server Settings window will be displayed as shown in .

In this window it is possible to see the definition of groups and the members i.e. database servers that are members of each group. For the reasons explained above there should normally be one database server configured in each group. The primary server from which user records are obtained should be in Group 1. The secondary server should be in Group 2 and so forth. It is possible to add the name of a database server that is in a particular group by selecting the Group then clicking on Add Member. The names entered for database servers must be selected from the list of configured database servers.

The provisioning system is used to manage all user records. In order to use the provisioning system to access the user records managed by a database server it is necessary to ensure that one has a user management session open in the provisioning system. Once a user management session is open one is presented with Query screen shown in .

From screen one is able to use Query Options panel to query the database of existing users add new users remove users and modify existing users. Note that there are two buttons User Properties which is used to get details about a particular user and Modify which is used to change an existing user record.

When adding or modifying a user record one will be provided with a user information dialog that consists of a number of panels. This is discussed in the subsections below. However prior to modifying a user record you will need to query for the records that you wish to modify. This is also required if one wishes to remove a user record. First using the interface shown above to query existing user records is discussed.

The Query screen is the main interface to user management capabilities on the provisioning system. Screen allows user records to be searched based on various criteria.

In order to query available user records one or more query options can be specified. User records can be queried by a variety of fields including name ID and authentication code. When specifying the search criteria it is possible to use as a wildcard that will match any string. For example entering 12 as the User ID search criteria will find all user records beginning with 12. Once the search criteria are entered the ordering parameter for results should be selected. This controls the order in which the results are displayed. Once this parameter has been set clicking on Query will begin the search for matching user records.

Once the query is complete the results will be displayed and the Close Query button will become selectable. The Close Query will close the query and allow a new query to begin. Once a query is closed it is no longer possible to travel forward and backward through the results. However any user records displayed in the result window can still be selected and viewed or edited. If there are more user records matching the query than can be displayed at a time the Next and Previous buttons will allow scrolling through the matching user records.

Group Account Record panel allows for the review of group and account records related to a queried user. User list window displays a list of found users based on a query entered and performed in panel .

Whether or not a query is active it is possible to add a user by clicking on the Add User button. However the other operations require that a user record in the result window of a query be selected. Once selected the user record can be removed viewed or modified.

Identification panel contains information that is used to identify and authenticate the user as well as some general settings for the user account as shown in and described below.

Name. Name of the user. This field is used for information purposes. The name field is optional but once a user has been added the name for that record cannot be modified.

Numeric ID. This is the ID of the user. Since users generally access the system using a telephone it is required that the ID only contain numbers that can be entered using DTMF tones. The ID of the user must be unique.

Authentication. This group of fields specify whether it is automatically necessary for the user to specify their authentication code. Before a user enters their authentication code they will be assigned their normal privilege level. Once their authentication code has been entered they will be granted their authenticated privilege level. If a user is required to always enter their authentication code they will be prompted to do so regardless of whether or not the service that they are accessing actually requires that privilege level. Otherwise if they are not required to always enter their authentication code they will only be asked for their authentication code if it is necessary in order to make use of a service that they have requested access to. It is possible to use the settings defined in the associated group record for this field by choosing Use Group .

Language Preference. Specifies the language preference for the user if left blank the default language will be used.

E mail Address. Used to record the E mail address of the user. Available for information purposes only and can be left blank.

Home Phone. Home telephone number of the user. Available for information purposes only and can be left blank.

Online Announcements. Specifies which announcements the user wishes to hear when making debit calls. If debit balance is selected then the user will be told their remaining balance each time they place a call. If time left is selected then the user will be told the maximum duration of a call each time a call is placed. If use group is selected then debit balance time left prompting will be performed based on the group record setting for the value.

Permissions panel is used to configure the access level and account active dates for the user account. Permission panel is shown in and described below 

Account Status. This field allows an account to be enabled or disabled. Group settings can also be used to determine whether or not an account is enabled.

Activation Date Time. Sets the date and time when the account will become active. The account may only be used on or after the time specified. It is possible to use the group value for this setting.

Expiration Date Time. Sets the date and time when the account will expire and become unusable. The account may not be used after the specified time. It is possible to use the group value for this setting.

Caller ID Identification panel shown in allows additional identifying information about the user to be entered. When a user accesses the system identifying information may be available. Examples include Caller ID information signaled by the telephone equipment the H.323 terminal name of an H.323 user or the remote system name of a calling gateway server. Any of this information can be used to automatically identify a user without requiring them to enter their ID. This panel shown in allows you to configure the information that can be used to automatically identify a user.

In order to add new identifying information for a user type the value associated with that information in the New String field. For example if the Caller ID string that should be used to identify the user is 7035551234 then enter this string in the New String field. Once the string has been entered click Add. A new entry in the table with the corresponding string will be added. Once it has been added click on the lookup type column for that string. One will be able to select what type of identification the new string corresponds to. The available options are 

Caller ID ANI. The entered string will be matched against Caller ID information provided by the connected telephone equipment.

H.323 terminal name. The entered string will be matched against the H.323 terminal name supplied by the user when connecting using the H.323 protocol.

Remote system name. The entered string will be matched against the system name supplied by a remote gateway server.

Note that identifying information must be unique in other words the same Caller ID string and type cannot be associated with more than one user record. This is clearly necessary since the information is used to uniquely identify a particular user.

Caller ID Authentication panel shown in is the analog of identification panel but applies to authentication of the user. It is configured in a manner that is very similar to the identification panel discussed above.

As with the identification panel it is necessary to type in the authentication string and click on Add in order to add an authentication record with that string. Then click on the lookup type column to specify what the lookup type for that string should be. There are numerous authentication types some of which are for expansion purposes.

Caller ID ANI. This allows caller ID information to be used to authenticate the user. This allows a single Caller ID string to be associated with multiple users and allows Caller ID to bypass password checking. For example it is possible to set up a calling card account that when used from the users home requires only the users ID to be entered but when used from a payphone requires both the user ID and authentication code.

IP address and port. Must be entered in 192.168.1.3 port 6789 format and will authenticate the user only if their IP address and port number match the specified values.

IP address only. Must be entered in 192.168.1.3 format and will authenticate the user only if their IP address matches the specified IP address.

PIN code. This authentication type is not presently used since the authentication code is contained in the basic user record settings.

Text password. Not currently used for authentication purposes designed for enhanced applications in the future.

Note that the reason that there are some additional types is that third party applications could make use of these types even though they are not directly used a gateway application.

As with the identification panel authentication entries can be removed by selecting the entry and clicking on Remove .

The account record status panel is used to display information about the account record that is associated with this user record. It allows an account record to be selected or created and is shown in and described below.

Clicking Select New will allow the selection of an account record that is associated with the current user record. It is possible to select either an existing account record or to create a new account record associated with the user record. When select new is selected the account record query window will be displayed allowing existing account records to be searched. This process is described in greater detail when account records are discussed below.

The Detach Account button will remove the association between the account record and the user record.

The parent group panel shown in displays information about the group associated with this user record if any and allows the group association to be changed.

Clicking Select New will allow the selection of a group record that is associated with the current user record. It is possible to either select an existing group record or to create a new group record. This is done by way of the group record query window which will allow you to search for the group record that you wish to add. The group record query screen is discussed in greater detail below.

The Detach Group will remove the association between the user account and the group record with which the user account is currently associated.

The management of group records is very similar to the management of user records since group records mainly provide default values for user record fields. The group record query screen from which group record operations can be performed is accessed via the user record query screen by clicking on the Group Records button in panel . The group record query screen is discussed in the sections that follow and shown in .

Through Query Options panel queries of the available group records on the system is done. Querying works very similarly to querying user records. The first step is to specify the search criteria by entering information into the fields on the left that correspond to the group records that you wish to retrieve. As with user records it is possible to use wildcards when searching for group records. Ordering parameters can also be set following which it is possible to query for group records.

Once results have been returned in a list within Account Records panel group records work identically to user records it is possible to close the query scroll forward and backwards using the Next and Previous buttons respectively and to add remove view modify group records.

The information available in the group record is a simplified set of the information contained in the user record since not all user record fields can be left as defined by the group record. There are two panels that provide access to the fields contained in the group record each of which is described below.

Most settings are available on general panel shown in screen of . For an explanation of any of the parameters shown refer to the corresponding parameter in the user record where the parameter is actually described. User records will only use values specified in the group records if the corresponding user record values indicate that the group record should be used to determine the value.

The account ID setting works identically to that for the user record but will establish an association between the group record and the account record.

The only group record specific information is the Group Info field which allows descriptive information about the group to be entered. This information is for descriptive purposes only and does not affect the behavior of the system.

Management of account records can be performed through the account record query screen accessible by clicking on Account Records when viewing the user record query screen in the provisioning system. This brings up the account record query window shown in .

The account record query window functions in the same manner as for user records and group records. The first step is to input query information in the fields in query panel also select ordering settings and click on the Query button. Like user and group records it is possible to scroll through found account records shown in Account Records panel using the Previous and Next buttons.

The Add New button allows new records to be added once a query result has been selected the Remove Properties and Modify allow the account record to be deleted viewed or modified respectively.

General panel shown in allows general account record information to be configured. Tabs allow for switching between General Panel and Profiles and Restrictions panel . An explanation of the fields of panel follows.

Account ID. Specifies the ID of the account. This ID is referenced by user records and or group records and must be unique. If account records are uniquely associated with a user record or group record it may make sense to adopt a scheme where the account ID and user group ID are identical.

Has Debit Record. Indicates whether or not a debit record is associated with this account record. This is required in order to provide debit capability.

Balance. If a debit record is associated with this account record then this field specifies the balance in dollars of the account.

Maximum Negative Debit. Specifies the maximum amount that the account record can be in deficit. Normally this parameter will be set to zero but if it is necessary to grant an account the capability to go into debt then this can be set to a non zero value.

Max Connections. Controls how many concurrent uses of this account are possible. This is used to restrict how many users may simultaneously make use of a single account. For group calling cards it may be desirable to allow many users to simultaneously make use of the account but in some cases it is desirable to prevent multiple users from using the account at the same time. Note that even if concurrent usage is allowed fraud is not possible through making concurrent calls both calls will be debited in real time from the account.

Account Information. This is an informational field that can be used to record comments about the account.

The profiles and restrictions panel shown in is used to control the rating of calls and modes of operation which are supported on this account.

Rating Profile. This parameter is an optional parameter for rating profile information for the billing rating process.

Enable Debit. Enables debit to be used on this account. Requires that an associated debit record exists in order to actually enable debit.

Enable Billing Exempted. If set this flag exempts the account record from being charged for any use of services.

This section presents call detail record CDR collection and explains how this task is accomplished in the present invention.

CDR collection is essential in any environment in which charges are applied for the services provided by the present invention. A gateway server will create a CDR for every call that is placed through the system. CDR collection is the process of collecting the CDRs across multiple gateway servers and storing them in a centralized database. As such CDR collection involves the database server as well as the gateway server.

Querying CDRs on a Database Server. Explains how the provisioning system is used to access the CDRs that are available on a database server.

Gateway Server Collection of CDRs. Describes the process by which the gateway server collects CDRs and how it transmits these CDRs to a database server or to multiple database servers.

Database Server Failure Handling. Describes how the gateway server handles inserting CDRs in light of a temporary failure of the database server to which the CDR is inserted.

Similar to the operation of user management it is possible to use the provisioning system to access the CDRs that are contained in the database managed by a database server. This is not the only way to access CDR information it is also possible to directly access the underlying database.

In order to query CDR information it is necessary to establish a CDR session with the database server using the provisioning system. Once such a session has been established the CDR query screen will be displayed as shown in .

From window CDRs can be queried in a manner that is similar to that used for querying user group and account records described in the previous section. Search criteria can be entered in the available fields of Query Options panel . After search criteria is entered the ordering parameter should be selected. Then clicking Query will display a list of CDRs that match the query in panel . It is possible to use the Next and Previous buttons to scroll through the available CDRs. The Close Query button should be used if it is desired to make an other query.

CDRs collected by the gateway server contain a large amount of information. This section will help one to understand the fields in an example CDR. The present invention is not limited to this example CDR and information can be added or removed from the CDR depending upon a particular billing service or system requirements.

Outbound Intf. Identifies the outbound line group used to place the outbound portion of the call. May be unknown if the call was never placed.

Outbound Line. Identifies the specific line on the outbound line group that was used to place the call.

Called Addr. Indicates the address that was called. This field will generally be in E.164 form but is prefixed with the e164 tag to identity E.164 numbers.

User Connect Time. Indicates the time as collected by the submitting gateway server at which the user connected to the system.

Call Connect Time. Indicates the time as collected by the submitting gateway server at which the call placed by the user was connected to the destination party.

Call Duration. Specifies the duration in seconds of the call. This is the time between the called party answering the call until the time that the call was disconnected.

IVR Duration. Specifies the amount of time in milliseconds that the user spent in the IVR process entering their ID the number to call and so forth.

Setup Duration. Specifies the amount of time in milliseconds required to set up the call. This includes searching for routes obtaining a line to place the call contacting a remote Gateway and other overhead.

Dial Duration. Specifies the amount of time in milliseconds that the call was placed for before it was either terminated or until the called party answered.

Call Attempt. Depending on the configuration of the gateway server it may be possible to make multiple calls on a single call into the system. This field indicates the call attempt number within a single call into the system.

Succeed. Provides a success code indicating whether or not the call was successful and if the call was unsuccessful provides a cause code.

RemoteSystem. Indicates whether the call was originated by a remote gateway server or a local user of the system.

Group ID. Stores the group ID if available of the group account associated with the user when the call was made.

Account ID. Specifies the account ID if available associated with the user at the time that the call was made.

Session ID. Provides a unique call ID that identifies this call. The session ID can be used to correlate the CDR collected by the originating gateway server and the terminating gateway server.

CDR collection is a capability that is provided by the gateway server platform. The gateway application makes use of this capability to create a CDR for every call that it processes. CDRs are inserted regardless of whether or not the call was successful the success code explained above is used to record the actual success of the call.

On the gateway server side the configuration of CDR collection involves specifying the database servers list and groups that are used in CDR collection. Double clicking on the CDR Service node can access the CDR collection configuration dialog. This node is visible when the Database Access root level node in the configuration tree is expanded and is shown in CDR Service window of . Note that one should use the management system to configure these parameters and that one should be connected to a gateway server in order to do so.

The server settings for the collection of CDRs is configured as described above. For the CDR service specifically it is useful to understand how concurrency and fallback work. If two or more database servers are placed in the same group then both of them will receive a copy of the CDR when it is inserted. Only if all database servers in that group fail to receive a copy of the CDR will the next group be used. This can be used to achieve redundancy by always logging CDRs to multiple database servers. However there is still some resilience to database server failures even in the absence of such a configuration as described in the next section . Configuring independent groups allows a secondary database server to receive CDRs in the event that the normal database server is not available.

In the event that none of the database servers are available to log a CDR collected by a gateway server it remains important that the CDR not be lost as this would represent lost revenue. Therefore for CDRs that cannot be successfully transmitted to a database server a local queue is maintained. While the database server remains unavailable any CDRs collected will be stored in this queue. Once the database server becomes available the CDRs in the queue will be transmitted to the database server and then removed from the queue. This queue is maintained persistently on disk so that even if a gateway server undergoes a temporary failure while the database server is unavailable it will continue to try to insert CDRs once it recovers from the temporary failure.

The Licensing Server is an additional optional software component according to the present invention. The License Server is designed to simplify the administration of a VoIP system according to the present invention by allowing all licenses to be managed from a single centralized server. This eliminates the need to configure license keys manually on individual components. Furthermore it allows licenses to be purchased in large blocks and then distributed amongst gateway servers rather than needing to purchase large numbers of small quantities of licenses for each gateway server.

It is possible to operate a secondary License Server for backup a purpose which is capable of allowing a network to continue to operate in the event that the primary license server becomes unavailable.

This appendix is intended to provide a description of the database tables used by the database server. The purpose of this description is to allow third party applications to be written which interface with the data maintained by the database server. Examples of such applications include billing systems or customer account creation tools. These database tables are an examples of the present invention and do not necessarily limit the present invention. Different fields can be added or removed from the database tables as would be apparent to a person skilled in the relevant art given this description.

Each of the tables created in the database are described in the sections that follow. For information about how the database server uses the information in these tables refer to the sections on User Management and CDR Collection.

The account record table is used to store the list of accounts that are available for use on the system. For a description of the interaction between account records and user group records see the section on User Management.

Account IDNumeric ID representing this particular account type. The primary key for the table should be unique. 

Concurrent MaxMaximum number of users groups that can access this account type concurrently i.e. at the same time .

User ID This field will contain either one specific user ID or a 0 zero . If there is only one user associated with this account ID the corresponding user ID appears in this field. If there are multiple or NO users associated with this account ID a 0 zero displays in this field. The individual user IDs of users associated with this account ID because of their group association will not display. Examples If user ID 999 is the ONLY user associated with this account user ID 999 is not associated with any group 999 without quotations appears in this field. Although there is only one individual user associated with the account there may also be groups which are associated with the account as well see group ID below. If user ID 123 is a member of group ID 456 which is associated with this account see GROUP RECORD table one would NOT enter user ID 123 or any other member of group ID 456 in this field. All users groups associated with an Account ID SHARE billing if in the above example one wanted to provide INDIVIDUAL billing for user 123 and all of the members of group ID 456 one would NOT associate the group 456 with any account but would create a separate account ID for EACH user ID in which case in each account ID entry this field would contain the associated user ID. If there is more than one user ID associated with this account who are not part of the same group a 0 would display in this field to indicate multiple user IDs. If there are NO individual user IDs associated with this account again this does not include users who are part of a group associated with this account a 0 would display in this field to indicate NO individual user IDs.

Group ID This field will contain either one specific group ID or a 0 zero . If there is only one group associated with this account ID the corresponding group ID will appear in this field. If there are multiple or NO groups associated with this account ID a 0 zero displays in this field. If a group is associated with an account the corresponding account ID appears in the group s entry in the GROUP RECORD table. Once a group is associated with an account ID all members users of the group automatically become linked to the same account ID. Examples If only group ID 111 was associated with this account 111 without quotations appears in this field. If both group ID 111 and group ID 222 are associated with this account a 0 displays in this field to indicate multiple group IDs. Remember that ALL users groups associated with an Account ID SHARE billing. To provide separate billing for each group all group members are lumped together create a separate account ID for EACH group ID in which case in each account ID entry this field would contain the associated group ID. To provide separate billing for each member of a group instead of lumping them together do NOT associate the group with an account. Instead create a separate account ID for EACH user ID see User ID field above. 

Time Stamp. Leave blank DB will enter information as required to ensure mutual exclusion on modifications.

Has Debit Record. A boolean type value where TRUE account is using an online debit plan. FALSE no associated debit balance.

Has Credit Record. A boolean type value where TRUE account is using the credit billing plan. FALSE not on credit plan. Speeds up internal DB operation DB server looks at this field first to determine if it needs to fetch the credit record. 

Locking By. Leave blank DB will enter information as required to ensure mutual exclusion on modifications.

Billing Flags. Binary data indicating which billing method is used debit prepaid credit usage based or exempted not charged . This field cannot be edited manually. If entering information DIRECTLY into the SQL Access database enter NULL.

The User ID and Group ID fields are closely related. These two fields will contain either a specific user group ID respectively or a 0 zero . The value of zero 0 means that there isn t one specific user group ID associated with this account ID there could be several users groups associated with this account ID or there could be none.

In one example one of these fields User ID or Group ID should have a value of 0 zero at all times. This means one should not have one individual user AND one group associated with the account at the same time.

If a user is associated with a group ID which is in turn associated with a particular account ID you do NOT have to enter the individual user ID in the User ID field the user will be associated with the account by group association. All users groups associated with a particular account ID are under ONE single billing plan. To provide individual separate user billing do NOT associate the group with an account instead create a separate account ID for each user ID. This does not mean you cannot still associate the user with the group a user can be associated with a group but have its own account ID for billing purposes. However a user cannot be a member of a group which IS associated with a particular account ID and have its own account ID at the same time.

The AUTHENTICATE ID table is used to hold authentication information for both user records and group records. Since a particular user or group record may have multiple authentication entries associated with it it is not possible to store this information within the user record or group record itself.

User OR Group. ID The user ID or group ID which will be authenticated by the information contained in the Authenticate ID field below. If you enter a group ID all members of the group will share the same authentication information each member still has their own numeric user ID. If one wishes to assign separate authentication information to each user in a group create a separate entry in this table for each user ID. A user can be a person remote Gateway or H.323 user.

Authenticate ID. Enter the information that will be used to authenticate the user or group. This information corresponds to the authentication method indicated in the Lookup Type field below.

Examples If the user group is authenticated by entering a numeric code such as 666 this field should contain 666 no quotations . If the user group is authenticated by their ANI information this field should contain the area code and phone number no brackets or spaces from which they are authorized to call e.g. 4167360901. If the user Gateway is authenticated by its IP address this field should contain the IP address from which the remote Gateway will be allowed access. Enter the IP address as follows 255.255.255.255 If the user Gateway is authenticated by its IP address plus port this field should contain the IP address from which the remote Gateway will be allowed access and the port through which the communication will be delivered. Enter the IP address and port as follows 255.255.255.255 port 0

Is User Entry. This field indicates whether or not this entry is for an user as opposed to a group . A boolean value where 0 zero indicates this entry is for a user. 1 indicates this is a group entry.

Lookup Type This field contains an integer value identifying the authentication method to be used. For example if this field contains a 0 zero the user or group specified in the above User OR Group ID field will be authenticated by the ANI information contained in the above Authenticate ID field.

The call record table is used to store call records for a number of Gateways. These call records can be used for post paid billing purposes and allow custom billing applications to be developed which interface with the system. The CALL RECORD table is updated continuously as calls are completed.

Session ID High. Unique identifier for the call that is consistent between CDRs inserted from both Gateways involved in the actual call. Can be used to correlate call records from the originating and terminating Gateways. Contains the high 32 bits of the 64 bit call ID.

Setup Duration ms . Length of time required to make the call. This is the time required for the Gateway to answer the user s initial call call connect receive the number entered by user authenticate user locate matching network call route route the call via the IP network have the second remote Gateway dial the number until a call connected signal indicates call has connected to called party User Connect Time to Call Connect Time . 

Dial Duration ms . Time required for second remote Gateway to dial outbound number and wait for call to connect.

Call Attempt. Number of consecutive calls made by the user. Example When called party hangs up the Gateway returns control to the initiating user prompting the user for another number. If the user enters another number to make a 2nd call the call record for the first call will have Call Attempt 1 and the 2nd call record will show Call Attempt 2.

Is Identified. A boolean value reflecting whether a user ID was entered. TRUE no user ID entered typically this displays when call record is written by remote Gateway 0 user ID was entered typically this displays when call record is written by initiating Gateway .

User Name. User NAME. If the initiating Gateway writes the call record the user name of the CALLER will display. If the remote Gateway writes the call record the initiating Gateway s System Name will display. If the user Gateway was not identified unknown will display.

User ID. User ID of the caller or Gateway if applicable . If user Gateway was not identified unknown will display.

Caller IDANI. Information of the caller IF this service is available on the phone lines connected to the Gateway . This information only displays on call records from the initiating Gateway.

Route Used. Identifies how the Gateway routed the call. If the Gateway routed call out over the network interface to a remote Gateway the IP address of the terminating Gateway will display here. If the Gateway dialed the number out over its phone lines telephony interface the phone number dialed will display here.

The call detail record table is updated continuously as call records are inserted. Ensure that any applications that access this table do not depend on a static database table state between queries.

A debit record table is used to maintain information about accounts on the system that have an associated debit record.

Debit ID. ID representing this online debit balance this value should be the same as the account ID whose members will use this balance .

Debit Reserved. For internal use only. Before a call is made the database server reserves a number of credits for the call reserved credit is not available for other calls. At the end of the call the ACTUAL credit used is deducted from the account s debit balance and the remaining unused reserved credits are released and are available for another call.

Debit Sessions Num. For internal use only. Indicates number of online debit sessions under this debit ID currently in progress.

Debit Max Negative. This defines the MAXIMUM credit that can be overdrawn from this debit ID balance. This field must have a value that is equal to or greater than zero. For example if this field has a value of 100 the system will once the debit balance has been used up allow 100 worth of calls to be made overdrawn before disabling the account. If you do not want to allow ANY calls after the debit balance has been used up enter 0 zero .

This table DEBIT RECORD and the ACCOUNT RECORD table are linked by their Debit ID and Account ID fields respectively. An account is linked to the DEBIT RECORD entry whose Debit ID field has the SAME VALUE as that contained in its Account ID field. To assign an online debit balance to an account you create a new entry in the DEBIT RECORD table and enter the account ID in the Debit ID field. For example to assign an online debit balance to account ID 1234 one creates a new entry in the DEBIT RECORD table and enter 1234 in the Debit ID field. This means that ALL members of account ID 1234 will use the online debit balance defined under the Debit ID 1234 .

If entering online debit balance information directly into the SQL Access database instead of via the provisioning system enter information in the Debit ID Debit Balance and Debit Max Negative fields. The remaining fields should be left blank.

All members of an account can SHARE the SAME online debit balance. To assign a separate online debit balance to each user create a separate account ID and corresponding debit entry for EACH user.

The group record table allows users to be grouped and to use default values for certain fields in the user records that are defined by the group record.

Concurrent Max. Maximum number of users that can access the Gateway under this group name concurrently i.e. at the same time . If this group is associated with an account the Concurrent Max field value in the ACCOUNT RECORD table will be used.

Normal Privilege. Privilege assigned to the user after they enter their numeric user ID or when they have been identified by an alternative identification method such as via ANI information .

Auth Privilege. Privilege assigned to the user once they have been identified AND authenticated by whatever methods the Gateway administrator has defined for the user . Normal and Authenticated privilege level can be the same.

Account ID. If this group is associated with a particular account the account ID will display here if there is NO associated account this field will contain a 0 zero .

Time StampLeave blank DB will enter information as required to ensure mutual exclusion on modifications.

Locking By. Leave blank. The DB server sets and unsets this field according to usage if account is being accessed via the provisioning system the account will be locked.

Acct Disabled. Through the provisioning system user interface administrators can disable access for the group by checking the disable box in the Account Status section on the Permissions panel. This field contains a boolean value where 1 or TRUE account disabled 0 or FALSE account active. If the group record is disabled the Gateway will not allow calls from members of this group ID. 

Force Auth. Authentication is not always required it is based on the required privilege of the desired route. Through the provisioning system user interface administrators can force Gateways to always identify and authenticate users by simply checking a box. This field will display a boolean value where 1 or TRUE box checked user MUST be authenticated 0 or FALSE box not checked authentication only when required based on privilege. For example if using calling card numbers as the user ID one would want to force the user to also enter their PIN i.e. authentication . 1 would display in this field.

Restrict Time. This field indicates whether or not call time restrictions apply to this group i.e. group members are restricted to making calls during certain time periods. This field contains a boolean value where 1 or TRUE time restrictions apply Gateway will check the Allow Times field below 0 or FALSE no time restrictions users can make calls at anytime.

Allow Times. This field contains binary data specifying those times during which members of this group can make calls.

User Flags. This field contains binary data. There are 64 generic flags defined available for use but only 2 flags have been assigned in one example. The first bit specifies whether group members when initiating a call prefer to hear the dollar amount remaining in the online debit account. The second bit specifies whether group members when initiating a call prefer to hear how much calling time remains in their online debit account. 

The USER RECORD table is used to store user accounts. Users can actually be added to or removed from the system by modifying this table directly. However it is important to take care to ensure that references to other tables such as group and account records 

User ID. Numeric user ID for this user enter up to 15 digits. Users are identified and assigned privileges based on this numeric ID. 

User Auth. Numeric authentication code for the above user. Users may be required to enter this 2nd code to make a call. 

User Phone. Contact phone number for this account. This field is informational only it is not used by the DB server. 

User Email. Contact email address for this account. This field is informational only it is not used by the DB server. 

Acct Disabled. Through the provisioning system user interface administrators can disable access for the user by checking the disable box in the Account Status section on the Permissions panel. This field contains a boolean value where 1 or TRUE account disabled 0 or FALSE account active. If account is disabled the Gateway will not allow calls using the specified user ID. 

Force Auth. Authentication is not always required it is based on the required privilege of the desired route. Through the provisioning system user interface administrators can force Gateways to always identify and authenticate users by simply checking a box. This field will display a boolean value where 1 or TRUE box checked user MUST be authenticated 0 or FALSE box not checked authentication only when required based on privilege. For example if are using calling card numbers as the user ID one would want to force the user to also enter their PIN i.e. authentication . 1 would display in this field.

Restrict Time. This field indicates whether or not call time restrictions apply to this user i.e. user is restricted to making calls during certain time periods. This field contains a boolean value where 1 or TRUE time restrictions apply Gateway will check the Allow Times field below 0 or FALSE no time restrictions users can make calls at anytime.

Allow Times. This field contains binary data specifying those times during which members of this group can make calls.

Concurrent MaxMaximum number of users that can access the Gateway under this user ID concurrently i.e. at the same time . If this user ID is associated with an account the Concurrent Max field value in the ACCOUNT RECORD table will be used.

Normal Privilege. Privilege assigned to the user after they enter their numeric user ID or when they have been identified by an alternative identification method such as via ANI information .

Auth Privilege. Privilege assigned to the user once they have been identified AND authenticated by whatever methods the Gateway administrator has defined for the user . Normal and Authenticated privilege level can be the same.

Time StampLeave blank DB will enter information as required to ensure mutual exclusion on modifications

Locking ByLeave blank. The DB server sets and unsets this field according to usage if account is being accessed via the provisioning system the account will be locked.

Group ID. If this user is associated with a particular group the group ID will display here if there is NO associated group type this field will contain a zero O .

Account ID. If this user is associated with a particular account the account ID will display here if there is NO associated account type this field will contain a zero O .

User Flags. This field contains binary data. There are 64 generic flags defined available for use but only 2 flags have been assigned in one example. The first bit specifies whether the user when initiating a call prefers to hear the dollar amount remaining in their online debit account. The second bit specifies whether the user when initiating a call prefers to hear how much calling time they have left in their online debit account. 

This section provides information to assist in designing and organizing a network in order to improve performance. It also provides some information and suggestions with regard to how the components of the present invention s could be organized.

Three main components are used in the present invention the gateway server database server and routing server. This section explains the network requirements of each of the components so that the appropriate network bandwidth and performance can be allocated to achieve the desired degree of performance. Each component and the type of communication used by that component is described separately.

The gateway server runs on UDP IP port 6789 for control data. Additional UDP IP ports are used for media data. These additional ports can be allocated anywhere within a specified range. By default the range of ports that can be used is 1025 to 65535. However the port range can be specified to match a user s requirements.

The main kind of communication made by the gateway server is communication to other gateway servers for the purpose of completing a call. A small amount of control traffic is exchanged to set up the call. After this point actual media data is exchanged throughout the call. Because the present invention employs silence compression to reduce the required bandwidth during periods of silence the media data is not a continuous stream. However with the default frame size of 60 ms per packet one 66 byte frame will be sent every 60 ms during active conversation. During silence no data will be transmitted. In addition a UDP IP header of 28 bytes will also be present on each transmitted frame. Overall this results in a data rate of 94 bytes per 60 ms or 1 557 bytes per second. Expressed in bits per second this is 12 533 bits per second or 12.5 kbps. In addition the underlying network frame relay ATM etc. may add additional framing data further increasing the actual data rate that must be allowed for on the network. Note that this is the transmission capability required from the sender to the receiver. When both the sender and the receiver are talking simultaneously this much bandwidth must be available in both directions. Often network bandwidth is symmetric. A 33.6 kbps modem can carry 33.6 kbps of data in both directions simultaneously similarly a T 1 can carry 1.544 Mbit s in both directions at the same time. However in the case that asymmetric bandwidth is available it is important to be aware that the bandwidth requirements of the system are bi directional.

Another critically important aspect of network performance on the communication between two gateway servers is that of latency and jitter. Latency the delay introduced on packets from one gateway server to another will be perceived by the end users of the system as a delay in the response of a remote user. Some latency is introduced by the gateway server itself in processing and decoding the media data. However network latency should be kept to a minimum to ensure that the conversation between end users is a natural one.

Even more serious than latency is the problem of jitter. Jitter is the variation in latency from one packet to another. For example if packets always arrived 50 ms after being transmitted then there would be a 50 ms latency and no jitter. As another example however if packet 1 arrived 100 ms after transmission packet 2 arrived 50 ms after transmission and packet 3 arrived 150 ms after transmission there would be an average jitter of 33 ms. The reason that jitter is more critical than latency is because it can cause a packet to arrive too late to be useful. The effect is that the packet may be delayed enough that the end user will hear a pause in the voice that is talking to them which is very unnatural if it occurs during the middle of a word or sentence. Jitter typically occurs when the network utilization is too high and packets are being queued causing delivery times to become unpredictable. The Internet because of it s complex structure is often subject to varying degrees of jitter. The present invention software compensates for network jitter. Furthermore handling jitter comes at the expense of latency since the only way to handle jitter is to buffer additional data so that when the data arrives exceptionally late continuous playback to the end user can be maintained.

In addition to gateway server to gateway server traffic the gateway server also communicates with the routing and database servers and is managed by the management system. Network factors related to these components are discussed below.

The routing server is involved in routing calls between gateway servers. However the routing server is optional routing information can be configured statically on individual Gateways.

When routing server is used there are two modes that it can be used in. Depending on which mode is used the networking requirements between Routing and gateway servers will vary. Routing modes are explained in detail in the call routing section however there are two basic modes of operation from a network standpoint

Served based Static Routing and Dynamic Routing. In these modes each time a Gateway need to make a call it will query the routing server for a route. This occurs once at the beginning of a conversation. Routes are typically quite small and do not require additional bandwidth to be allocated since the bandwidth during the call will be higher than during the call routing stage . However it is important nonetheless since network latency will add to the call setup time and the end user will be waiting for the system to initiate the call. Normally this latency is not a problem. However if the latency is on the order of 500 ms and call setup time is critical then this may be a consideration. An important aspect of dynamic routing is the caching of routes. With dynamic route caching not all calls will require a query to the server. However there will still be calls which require the server to be queried and these calls will incur the latency penalty.

Disseminated Routing. With disseminated routing the routing server distributes the necessary routing data to each gateway server when it firsts connects. This is typically when the system is starting up. In this model the Gateway will use a large amount of bandwidth during the initial connection as the routes are disseminated from the server. However after this point there will be no subsequent queries and no latency will be added on a per call basis.

The selection of a routing model will be explained in more detail in the section on call routing. However it is useful to keep the network requirements in mind when considering what routing model to use.

The first kind of traffic is due to communication with the gateway servers. There are two reasons for this traffic user management and call detail record collection. On a call by call basis this traffic is not very significant. However when a single database server is used to provide service to a large number of Gateways this traffic will be concentrated to a single point. Therefore if a single centralized database server will be used it is sensible to locate it at a network hub so that the traffic from all gateway servers will not overload a single network link.

The second kind of traffic is that between the database server and the underlying Database implementation. The database server is capable of running on a different machine than the one that runs the database. From a network standpoint there may be motivation to do this if a database server needs to be exposed to the Internet for the purpose of CDR insertion with the actual database which might hold other sensitive data not accessible directly via the Internet. If however the database server and underlying database are not run on the same machine then there will be network communication between the two machines. The volume of this traffic will depend directly on the load placed on the database server but it will be similar in volume to the aggregated database related traffic of all the gateway servers that the database server supports. Therefore if possible without violating security requirements it is recommended that the database server be run on the same machine as the underlying database or in a LAN environment. Using an underlying database connected in a WAN environment with low available bandwidth may cause performance problems.

Using the management system to administer any of the other components of the system does not typically require a significant amount of bandwidth. The only exceptions to this are when large lists of routes are being manipulated in which case the initial query of the routing database may require the routes to be downloaded to the management system. Although this should not normally be a problem using a routing server that is connected to the management system either locally or via a LAN connection can alleviate the problem. Even if the routing server is operated remotely the use of a routing server allows only one connection the one between the routing server and management system to become heavily utilized during the start of routing table administration.

The provisioning system interfaces exclusively with database servers. The network requirements of this interaction depend on the types of operations being performed. Clearly obtaining and modifying a user record do not require significant amounts of bandwidth since the amount of data contained in a single user record is relatively small. However when doing bulk record fetching such as fetching one hundred user records for summary display or several hundred call records the amount of data transferred between the database server and provisioning system may be large. If one will be using the provisioning system to interact with large amounts of data then it is recommended that the database server be located on the same LAN or even the same machine as the provisioning system. If it is necessary to locate the database server and provisioning system across a WAN connection then care should to be taken to ensure sufficient capacity and to prevent a conflict with time sensitive voice data.

The network requirements of the present invention components were explained above in order to guide the formation of a network topology. However regardless of the network topology selected additional information can be used by capable routers in order to prioritize the different kinds of traffic. The following table shows the various port numbers that can be used to prioritize traffic in one example 

From the above table it can be observed that control oriented data originating from a particular component always originates from a single UDP IP port. All components of a VoIP system in the present invention can have a single unique port number as follows 

This information can be used to prioritize traffic if the underlying routers are capable. Typically it is desirable to ensure that Gateway to Gateway media data has the highest priority time sensitive control data Gateway to Database routing servers has medium priority and management provisioning traffic has the lowest priority. This policy may of course need to be combined with the policies for other types of traffic on the same network.

An example of a computer system is shown in . Computer system s can execute software to carry out any of the functionality described above with respect to VoIP system including any of the servers and systems and and Management System Provisioning System and network manager .

Computer system represents any single or multi processor computer. Single threaded and multi threaded computers can be used. Unified or distributed memory systems can be used.

Computer system includes one or more processors such as processor . One or more processors can execute software implementing all or part of VoIP system as described above. Each processor is connected to a communication infrastructure e.g. a communications bus cross bar or network . Various software embodiments are described in terms of this exemplary computer system. After reading this description it will become apparent to a person skilled in the relevant art how to implement the invention using other computer systems and or computer architectures.

Computer system also includes a main memory preferably random access memory RAM and can also include secondary memory . Secondary memory can include for example a hard disk drive and or a removable storage drive representing a floppy disk drive a magnetic tape drive an optical disk drive etc. The removable storage drive reads from and or writes to a removable storage unit in a well known manner. Removable storage unit represents a floppy disk magnetic tape optical disk etc. which is read by and written to by removable storage drive . As will be appreciated the removable storage unit includes a computer usable storage medium having stored therein computer software and or data.

In alternative embodiments secondary memory may include other similar means for allowing computer programs or other instructions to be loaded into computer system . Such means can include for example a removable storage unit and an interface . Examples can include a program cartridge and cartridge interface such as that found in video game devices a removable memory chip such as an EPROM or PROM and associated socket and other removable storage units and interfaces which allow software and data to be transferred from the removable storage unit to computer system .

Computer system can also include a communications interface . Communications interface allows software and data to be transferred between computer system and external devices via communications path . Examples of communications interface can include a modem a network interface such as Ethernet card a communications port etc. Software and data transferred via communications interface are in the form of signals which can be electronic electromagnetic optical or other signals capable of being received by communications interface via communications path . Note that communications interface provides a means by which computer system can interface to a network such as the Internet.

The present invention can be implemented using software running that is executing in an environment similar to that described above with respect to . In this document the term computer program product is used to generally refer to removable storage unit a hard disk installed in hard disk drive or a carrier wave or other signal carrying software over a communication path wireless link or cable to communication interface . A computer useable medium can include magnetic media optical media or other recordable media or media that transmits a carrier wave. These computer program products are means for providing software to computer system .

Computer programs also called computer control logic are stored in main memory and or secondary memory . Computer programs can also be received via communications interface . Such computer programs when executed enable the computer system to perform the features of the present invention as discussed herein. In particular the computer programs when executed enable the processor to perform the features of the present invention. Accordingly such computer programs represent controllers of the computer system .

In an embodiment where the invention is implemented using software the software may be stored in a computer program product and loaded into computer system using removable storage drive hard drive or communications interface . Alternatively the computer program product may be downloaded to computer system over communications path . The control logic software when executed by the one or more processors causes the processor s to perform the functions of the invention as described herein.

In another embodiment the invention is implemented primarily in firmware and or hardware using for example hardware components such as application specific integrated circuits ASICs . Implementation of a hardware state machine so as to perform the functions described herein will be apparent to persons skilled in the relevant art s .

While specific embodiments of the present invention have been described above it should be understood that they have been presented by way of example only and not limitation. It will be understood by those skilled in the art that various changes in form and details may be made therein without departing from the spirit and scope of the invention as defined in the appended claims. Thus the breadth and scope of the present invention should not be limited by any of the above described exemplary embodiments but should be defined only in accordance with the following claims and their equivalents.

