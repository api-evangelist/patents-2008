---

title: System and method of consolidated central user administrative provisioning
abstract: In one embodiment the present invention includes a computer-implemented method of reducing a quantity of business application programming interface (BAPI) calls in a hardware client-server environment. The method includes configuring a centralized provisioning system on a hardware server with access definitions for systems. The method further includes receiving, by the centralized provisioning system, a provisioning request for a user of a client to access the systems. The method further includes determining a collected BAPI call according to the access definitions. The method further includes providing access to the user according to the collected BAPI call.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08788666&OS=08788666&RS=08788666
owner: SAP AG
number: 08788666
owner_city: Walldorf
owner_country: DE
publication_date: 20081231
---
The present invention relates to user administrative provisioning and in particular to user administrative provisioning in a heterogeneous computing environment.

Unless otherwise indicated herein the approaches described in this section are not prior art to the claims in this application and are not admitted to be prior art by inclusion in this section.

BAPIs Business Application Programming Interfaces are a set of interfaces to object oriented programming methods that enable a programmer to integrate third party software into the proprietary R 3 enterprise resource planning product from SAP. For specific business tasks such as uploading transactional data BAPIs are implemented and stored in the R 3 system as remote function call RFC modules.

BAPIs play an important role in the technical integration and in the exchange of business data between SAP components and between SAP and non SAP components. BAPIs enable one to integrate these components and are therefore an important part of developing integration scenarios where multiple components are connected to each other either on a local network or on the internet.

BAPIs allow integration at the business level abstracted above the technical level. This provides for greater stability of the linkage and independence from the underlying communication technology. BAPIs allow object oriented access to the SAP system through methods for the business object types. Together with the business object types BAPIs define and document the interface standard at the business level.

One area that involves BAPIs is user access to data. The data may be stored on multiple computer systems so BAPIs help to provide access between the multiple components. The standard way to provide access is to call a BAPI for every system to be accessed.

Embodiments of the present invention improve user access to data by reducing the number of BAPI calls. In one embodiment the present invention includes a computer implemented method of reducing a quantity of business application programming interface BAPI calls in a hardware client server environment. The method includes configuring a centralized provisioning system on a hardware server with access definitions for systems. The method further includes receiving by the centralized provisioning system a provisioning request for a user of a client to access the systems. The method further includes determining a collected BAPI call according to the access definitions. The method further includes providing access to the user according to the collected BAPI call.

The following detailed description and accompanying drawings provide a better understanding of the nature and advantages of the present invention.

Described herein are techniques for user administrative provisioning. In the following description for purposes of explanation numerous examples and specific details are set forth in order to provide a thorough understanding of the present invention. It will be evident however to one skilled in the art that the present invention as defined by the claims may include some or all of the features in these examples alone or in combination with other features described below and may further include modifications and equivalents of the features and concepts described herein.

Provisioning is the process of managing access and entitlement rights to electronic services and resources. These services and resources are those services and resources used in an organization and managed by their information technology support people. The access and entitlement rights are for users and system. Management is a complete lifecycle management process e.g. setup change revoke audit and the like. Provisioning is the act of preparing access and entitlement rights prior to first access.

Although the description below is specifically addressed to BAPIs such references are for brevity. It is to be understood that embodiments of the present invention are also applicable to other types of system integration interfaces such as web services and Common Object Requesting Broker Architecture CORBA interfaces.

In box a centralized provisioning system is provided and the centralized provisioning system is configured with the access definitions of the systems for which the centralized provisioning system is managing access. The centralized provisioning system may be implemented as a computer program executed by a hardware server in the hardware client server computing environment. The access definitions define the characteristics of the systems for which the centralized provisioning system is managing provisioning as further detailed below.

The centralized provisioning system manages access to data stored in the hardware client server computing environment. The centralized provisioning system works with both distributed access systems and consolidated access systems.

In distributed access systems access is defined on one system and the data is federated. Protocols like SOAP formerly Simple Object Access Protocol and Security Assertion Markup Language SAML may be used. SAML is an XML based Extensible Markup Language standard for exchanging authentication and authorization data between systems. Other techniques exist under the rubric of Provisioning System to Provisioning Systems.

In centralized access systems access is defined on a centralized system and the access data to other systems is maintained on the centralized system. The other systems then access the centralized system for the access data. This may also be referred to as Central User Administration CUA . A CUA layout is one CUA and many child systems. Furthermore there can be multiple CUAs in a client server environment for example different vendors of systems different versions of systems etc.

In provisioning the most complex landscape of systems is a mix of at least one CUA having child systems and at least one system without a parent CUA system in the CUA system level configuration. Furthermore in addition to the multiple CUAs there may also be non CUA distributed systems in the landscape. Further details regarding configuration of the centralized provisioning service are provided below.

In box the centralized provisioning system receives a provisioning request. The request may result from a system administrator configuring the centralized provisioning system as discussed in more detail below. The request may be received from a client in the client server environment in response to a user request to access data. This may be contrasted with many existing client systems which generate a multitude of BAPI calls in response to a provisioning request when the data is managed by a multitude of systems. 

In box the centralized provisioning system determines the BAPI calls involved in meeting the provisioning request and produces a collected BAPI call. To make this determination the centralized provisioning system uses the access definitions see box . The centralized provisioning system then makes the collected BAPI call. Further details regarding box are provided with reference to .

In box the client accesses the data as provisioned according to the collected BAPI call see box . The data may include application data from an application server database data from a database server etc. according to a three tier architecture. For example the provisioning may include access to a particular application stored or executed by the application server or access to particular data stored by the database server.

In box for each system in the provisioning request see box the centralized provisioning system determines whether the access definitions see box are configured for that system. If so the centralized provisioning system proceeds to box . If not the centralized provisioning system proceeds to box .

In box the centralized provisioning system determines whether the system in the request is participating in central user administration CUA . If so the centralized provisioning system proceeds to box . If not the centralized provisioning system proceeds to box .

In box the centralized provisioning system determines whether a global CUA is defined. If so the centralized provisioning system proceeds to box . If not the centralized provisioning system proceeds to box .

In box the centralized provisioning system collects in a map of the CUA system to the child recipient systems. A specific example of this process is provided below. The centralized provisioning system proceeds to box .

In box the centralized provisioning system performs non CUA provisioning for the system by making a BAPI real time agent RTA call. This may be referred to as an uncollected BAPI call to differentiate from the collected BAPI call discussed below. The centralized provisioning system proceeds to box .

In box the centralized provisioning system determines whether the request includes additional systems that have not yet been evaluated according to the process. If so the centralized provisioning system returns to box . If not the centralized provisioning system proceeds to box .

In box using the map generated in box the centralized provisioning system makes a provisioning call to the parent sending CUA system by passing on all the child systems information in a collected RTA call.

Consider the following example. Eight systems are present and are referred to as System1 System2 System3 System4 System5 System6 System7 and System9. A map of a CUA system to the child systems may contain the parent sending system as the key and all the child receiving systems for a particular parent sending system in a list as a value for this key.

Assume that System5 is the global CUA system that there is no configuration defined for System1 and System3 that for System2 System4 System6 and System7 that the configuration is defined that System9 is the parent system for System4 System6 and System 7 and that System2 is not participating in CUA.

Applying the process of to the example starting with System1 determine if a configuration exists box . If the result of box is yes then determine whether System1 is participating in CUA box . If the result of box is no then add System1 to the list of non CUA systems for non CUA provisioning box . If the result of box is yes then box create a list and store System1 in the list. Fetch the parent system of System1 and store the parent of System1 as the key and the list information as the value in the map.

If the result of box is no then determine whether a global CUA is defined box . If the result of box is no then add System1 to the list of non CUA systems for non CUA provisioning box . If the result of box is yes then box fetch the list of child systems that are associated with the global CUA system. If there is no child system associated with the global CUA system then create a new list and store System1 in the list and add the global CUA system as a key in the map and the list of child systems for the global CUA system as the value.

Thus three provisioning BAPI calls may be made as a result of processing the example. One call provisions the user in System5 and subsystems i.e. System1 and System3 . A second call provisions the user in System9 and subsystems i.e. System4 System6 and System7 . A third call provisions the user in System2 i.e. the non CUA system .

These three calls may be contrasted with the seven calls that may be required in existing systems i.e. not according to embodiments of the present invention . This reduces network traffic to backend systems. Furthermore an embodiment of the present invention supports the provisioning of both CUA and non CUA systems in a single request.

The server includes a centralized provisioning system . The server may be dedicated to the centralized provisioning system or the server may also implement other server side database application programs databases or data. The centralized provisioning system may be implemented as a computer program executed by the server . The centralized provisioning system may implement all or part of the method see .

As discussed above an end user submitting a request for provisioning is abstracted from the complexities of the access scenarios e.g. distributed access centralized access CUA non CUA etc. The user may generate a single request for provisioning. The centralized provisioning service may then consolidate this request as described above allowing provisioning to happen with greater ease and security.

As discussed above the centralized provisioning service supports multiple CUA environments as well as both CUA and non CUA environments. This is achieved according to an embodiment by functionality to configure a CUA at a global level functionality to specify CUA at the system level and functionality to define a system that is not participating in CUA. According to an embodiment the defined system level takes precedence if no value is defined at the system level the centralized provisioning service uses the global level settings.

When the centralized provisioning service gets the call to provision to different systems the centralized provisioning service uses the process of to determine the optimal Business API BAPI calls. For each system that should be provisioned based on the global and system level settings it is determined whether it is part of a CUA or not and the grouping or consolidation happens at the parent CUA system level. After the grouping BAPI calls are made to the parent CUA systems by sending information regarding all the child systems associated with that CUA system for provisioning. For non CUA systems BAPI calls are made directly to these systems.

The centralized provisioning system may be configured in the manner further detailed below. An administrator has the ability to configure global settings and system settings. In the global settings the administrator can identify a global CUA system which is the CUA used for systems in a provisioning request that have not been otherwise provisioned as a CUA system or as a non CUA system . In the system settings the administrator can define each individual system for provisioning as a CUA system or as a non CUA system.

If the system is designated as a non CUA system then the centralized provisioning system uses the appropriate BAPI for provisioning a non CUA system when providing access to that system.

If the system is designated as a CUA system then the administrator may further designate the CUA with which that system is to be associated. According to an embodiment when a system is associated with a CUA system the centralized provisioning system inserts the CUA system data into the CUA table CHILD DATA and updates the function template related data in the Function table BAPI MAP SYS . The structure for these tables is shown in .

Once a system has been defined in the system settings the administrator can edit the information for that system or may delete that system from the system settings.

The configuration module manages the access definitions for the systems for which the centralized provisioning system is managing access. An administrator may interact with the configuration module to define global settings to define system settings to edit the settings for a system to delete a system from the access definitions etc.

The processing module receives a provisioning request and generates a collected BAPI call according to the access definitions . The processing module may execute the processes described above in or . The processing module may then provide the collected BAPI call to the server e.g. server in to use when provisioning access to a user.

The user provisioning process may be enhanced according to a further embodiment of the present invention. The user provisioning information may be included in the collected BAPI call discussed above see .

An end user when submitting a request for provisioning can submit the request for provisioning into multiple systems. The type of provisioning that works for one system might not be applicable to the other system. In general there are two ways of assignment of roles to the user directly and indirectly. In direct provisioning the roles are assigned directly to the user. Whereas in indirect provisioning roles will be assigned to an organization level parameter like position and position will be assigned to the user. If the employee changes there is no need to assign the role to the new employee again but only the position. In this way the new employee automatically receives the roles assigned indirectly through the position. Other organization level parameters like Job OrgUnit may also be considered besides position. In a complex scenario the type might change from one system to another as shown below in TABLES 1 2.

TABLE 1 defines a global settings example scenario. The global settings define that the provisioning is indirect and that the provisioning parameter is the user s position. The global settings are then applied when a particular system is provisioned.

TABLE 2 defines a combination settings example scenario. The provisioning for Systems 1 2 is direct according to the global direct setting. The provisioning for System 3 is indirect with the user s job as the provisioning parameter and for System 4 is indirect with the user s position as the provisioning parameter.

To accommodate these different scenarios an embodiment of the present invention implements a system with two ways of configuration. The first way is a global setting that applies if no other setting is defined for a particular system. The second way is a system setting that may be used to override the global setting on a system by system basis. All the options that are available at the global level may be available at the system level also. The most common scenario followed may be defined as part of the global settings and the exceptional cases may be configured in the system level settings. According to an alternative embodiment provisioning for each of the systems may be defined in the system level settings itself. In the above scenarios for the first scenario TABLE 1 defining Direct Provisioning at the global level should work fine. But for the second scenario TABLE 2 Direct Provisioning may be defined at the global level the system level configuration for System 3 and System 4 may be defined as Indirect Provisioning with the parameters Job and Position respectively specified as the provisioning parameters. During provisioning a provisioning service evaluates the settings for each system in the request as shown in .

In box for a particular system in the provisioning request the centralized provisioning system determines whether a system level setting is defined. If so the process proceeds to box . If not the process proceeds to box . For example using the scenario of TABLE 2 for System 1 or System 2 no system level setting is defined for System 3 or System 4 a system level setting is defined.

In box the centralized provisioning system uses the defined system level settings to determine the provisioning parameters. For example using the scenario of TABLE 2 for System 3 the defined system level setting is to use the user s Job as the provisioning parameter for System 4 the defined system level setting is to use the user s Position as the provisioning parameter.

In box the centralized provisioning system uses the defined global level settings to determine the provisioning parameters. For example using the scenario of TABLE 2 for System 1 the global setting is to use direct provisioning. The system level settings and global level settings may be referred to collectively as access settings . 

In box for each other system in the provisioning request the centralized provisioning system returns to box and performs the boxes for that system.

Once the centralized provisioning system has used the access settings for each system to determine the provisioning parameters the centralized provisioning system provisions access for the user according to the provisioning parameters. These provisioning parameters may be included in the collected BAPI call see .

The configuration module manages the access settings for the systems for which the centralized provisioning system is managing access. An administrator may interact with the configuration module to define global level settings to define system level settings to define provisioning parameters to edit the settings for a system to delete a system from the access settings etc.

The processing module receives the provisioning request and determines the provisioning parameters according to the access settings . The processing module may execute the processes described above in . The processing module may include the provisioning parameters in the collected BAPI call see .

Computer system may be coupled via bus to an output device such as a cathode ray tube CRT or liquid crystal display LCD for displaying information to a computer user. An input device such as a keyboard and or mouse is coupled to bus for communicating information and command selections from the user to processor . The combination of these components allows the user to communicate with the system. In some systems bus may be divided into multiple specialized buses.

Computer system also includes a network interface coupled with bus . Network interface may provide two way data communication between computer system and the local network . The network interface may be a digital subscriber line DSL or a modem to provide data communication connection over a telephone line for example. Another example of the network interface is a local area network LAN card to provide a data communication connection to a compatible LAN. Wireless links is also another example. In any such implementation network interface sends and receives electrical electromagnetic or optical signals that carry digital data streams representing various types of information.

Computer system can send and receive information including messages or other interface actions through the network interface to an Intranet or the Internet . In the Internet example software components or services may reside on multiple different computer systems or servers and across the network. A server may transmit actions or messages from one component through Internet local network and network interface to a component on computer system .

According to an embodiment the client see may be implemented by the computer system . The server see may be implemented by the server which may include internal components similar to those of the computer system .

The above description illustrates various embodiments of the present invention along with examples of how aspects of the present invention may be implemented. The above examples and embodiments should not be deemed to be the only embodiments and are presented to illustrate the flexibility and advantages of the present invention as defined by the following claims. Based on the above disclosure and the following claims other arrangements embodiments implementations and equivalents will be evident to those skilled in the art and may be employed without departing from the spirit and scope of the invention as defined by the claims.

