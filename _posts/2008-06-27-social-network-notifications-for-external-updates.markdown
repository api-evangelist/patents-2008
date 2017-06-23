---

title: Social network notifications for external updates
abstract: Various technologies for notifying users of a social network service of updates to services external to the social network service by members of the social network. The external service may be a typical web service, such as blogging, and video and photo sharing services. In one implementation, a member of a social network may register the external service with the social network service. Thereinafter, updates that the user makes on the external service may trigger notifications to members of the user's social network.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07958193&OS=07958193&RS=07958193
owner: Microsoft Corporation
number: 07958193
owner_city: Redmond
owner_country: US
publication_date: 20080627
---
In today s web many services are available that enable users to build and share content among online communities. Some of these services are specific to particular types of content sharing such as blogs and video or photo sharing services. Other services may be more general and aggregate a variety of services.

Social network services typically provide the ability to build and maintain online social networks for communities of people who share interests. Social network services typically include some form of directory and means for users within a social network to connect.

Directories typically include a list of people in a user s social network. Some directories may even be subdivided into categories of people such as former classmates co workers fellow club members etc. The means to connect may include services such as instant messaging email video and voice chat blogging and the like.

Social network services have revolutionized the ways in which we can communicate and share information with people from around the world. Social network services are used by millions of people every day and have become part of the contemporary social fabric.

Described herein are implementations of various technologies for notifying users of a social network service of updates to services external to the social network service by members of the social network. The external service may be a typical web service such as blogging and video and photo sharing services. In one implementation a member of a social network may register the external service with the social network service. Thereinafter updates that the user makes on the external service may trigger notifications to members of the user s social network.

In another implementation when a member of the user s social network logs on to the social network service a means of notification such as an icon may be placed next to the user s identifier in a list viewed by the member. The icon may indicate that the user has made an update to the external service that the member has not yet viewed. The member may view summary data about the external service update by clicking on the icon.

The above referenced summary section is provided to introduce a selection of concepts in a simplified form that are further described below in the detailed description section. The summary is not intended to identify key features or essential features of the claimed subject matter nor is it intended to be used to limit the scope of the claimed subject matter. Furthermore the claimed subject matter is not limited to implementations that solve any or all disadvantages noted in any part of this disclosure.

As to terminology any of the functions described with reference to the figures can be implemented using software firmware hardware e.g. fixed logic circuitry manual processing or a combination of these implementations. The term logic module component or functionality as used herein generally represents software firmware hardware or a combination of these implementations. For instance in the case of a software implementation the term logic module component or functionality represents program code or declarative content that is configured to perform specified tasks when executed on a processing device or devices e.g. CPU or CPUs . The program code can be stored in one or more computer readable media.

More generally the illustrated separation of logic modules components and functionality into distinct units may reflect an actual physical grouping and allocation of such software firmware and or hardware or may correspond to a conceptual allocation of different tasks performed by a single software program firmware program and or hardware unit. The illustrated logic modules components and functionality can be located at a single site e.g. as implemented by a processing device or can be distributed over plural locations.

The terms machine readable media or the like refers to any kind of medium for retaining information in any form including various kinds of storage devices magnetic optical solid state etc. . The term machine readable media also encompasses transitory forms of representing information including various hardwired and or wireless links for transmitting the information from one point to another.

The techniques described herein are also described in various flowcharts. To facilitate discussion certain operations are described in these flowcharts as constituting distinct steps performed in a certain order. Such implementations are exemplary and non limiting. Certain operations can be grouped together and performed in a single operation and certain operations can be performed in an order that differs from the order employed in the examples set forth in this disclosure.

A first user and a second user of the client computer and the client computer respectively may be members of a social network service. The social network service may be provided for the users via the social network host . The address book clearing house may identify members of the first user s and the second user s social networks. That is the address book clearing house may contain a directory of all the users of the social network service and maintain information about the users social networks. In the implementations described herein the first user and the second user may be members of each other s social networks.

The first user may also use a web service such as a photo sharing service provided via the external host . The descriptions that follow use the photo sharing service as an example of a web service that may be provided via the external host. However it should be understood that the photo sharing service is merely one example of a standard web service and is not intended to limit implementations of the various technologies described herein.

The external host may include a central processing unit CPU a system memory a storage a network interface and a system bus that couples various system components to the CPU . Although only one CPU is illustrated in the external host it should be understood that in some implementations the external host may include more than one CPU .

The system bus may be any of several types of bus structures including a memory bus or memory controller a peripheral bus and a local bus using any of a variety of bus architectures. By way of example and not limitation such architectures include Industry Standard Architecture ISA bus Micro Channel Architecture MCA bus Enhanced ISA EISA bus Video Electronics Standards Association VESA local bus and Peripheral Component Interconnect PCI bus also known as Mezzanine bus.

The system memory may include a read only memory ROM a random access memory RAM and a basic input output system BIOS none of which are shown . The BIOS may contain the basic routines that help transfer information between elements within the external host such as during start up.

The storage may include a hard disk drive for reading from and writing to a hard disk a magnetic disk drive for reading from and writing to a removable magnetic disk and an optical disk drive for reading from and writing to a removable optical disk such as a CD ROM or other optical media. The hard disk drive the magnetic disk drive and the optical disk drive may be connected to the system bus by a hard disk drive interface a magnetic disk drive interface and an optical drive interface respectively. The drives and their associated computer readable media may provide nonvolatile storage of computer readable instructions data structures program modules and other data for the external host . Neither the drives nor their respective interfaces are shown in .

Although the external host is described herein as having a hard disk a removable magnetic disk and or a removable optical disk it should be appreciated by those skilled in the art that the external host may also include other types of computer readable media that may be accessed by a computer. For example such computer readable media may include computer storage media and communication media.

Computer storage media may include volatile and non volatile and removable and non removable media implemented in any method or technology for storage of information such as computer readable instructions data structures program modules or other data.

Computer storage media may further include RAM ROM erasable programmable read only memory EPROM electrically erasable programmable read only memory EEPROM flash memory or other solid state memory technology CD ROM digital versatile disks DVD or other optical storage magnetic cassettes magnetic tape magnetic disk storage or other magnetic storage devices or any other medium which can be used to store the desired information and which can be accessed by the external host .

Communication media may embody computer readable instructions data structures program modules or other data in a modulated data signal such as a carrier wave or other transport mechanism and may include any information delivery media. The term modulated data signal may mean a signal that has one or more of its characteristics set or changed in such a manner as to encode information in the signal.

By way of example and not limitation communication media may include wired media such as a wired network or direct wired connection and wireless media such as acoustic RF infrared and other wireless media. Combinations of any of the above may also be included within the scope of computer readable media.

Further the external host may operate in a networked environment using logical connections to one or more remote computers such as the social network host the address book clearing house the client computer and the client computer . The logical connections may include the network interface connected to a network . The network may be any network or collection of networks such as enterprise wide computer networks intranets local area networks LAN and wide area networks WAN . In one implementation the network may be the Internet.

A number of program modules and data may be stored in the system memory and the storage . Specifically the system memory may include an operating system . The operating system may be any suitable operating system that may control the operation of a networked personal or server computer such as Windows Vista Mac OS X Unix variants e.g. Linux and BSD and the like.

The system memory may also include a social network interface and an external service application . The storage may contain content . The content may be data of a type related to the web service provided by the external host . For example the content for the photo sharing web service may be photographs.

The social network interface may send a notification of content updates to the address book clearing house . In one implementation the notification may include an identifier of the user making the update an identifier of the external service and a timestamp of when the update takes place.

Additionally the social network interface may provide a summary of content updates in response to requests from the social network host . In the case of the photo sharing service the summary may include one or two captions accompanying newly posted photos. What is included in the summary may vary according to the web service provided by the external host . In the case of other web services such as a weblog service the summary may include a snippet of text from a new blog entry.

The social network interface may also register the photo sharing service with the address book clearing house in response to a request from the client computer . In one implementation the external service client may send a registration request to the social network interface . In response the social network interface may send a registration message to the address book clearing house . The registration message may identify the registering user and the external host .

In one implementation the registration message may also identify roles. The roles may define access controls to the content . For example the roles may include a reader role and an administrator role. The reader role may limit access to viewing the content . In contrast the administrator role may allow more expansive access such as allowing a user to make updates to the content .

The external service application may be software that works in concert with an external service client on the client computer to provide the web service to the first user. For example the external service application may download the photographs from the client computer in response to a request from the external service client . Additionally the external service application may enforce the access controls by role.

The address book clearing house may be constructed similarly to the external host . The address book clearing house may include a central processing unit CPU a system memory a storage a network interface and a system bus that couples various system components to the CPU .

A number of program modules and data may be stored in the system memory and the storage . Specifically the system memory may include an operating system an address book server application and an external service application programming interface API . The storage may contain a directory and the notifications .

The address book server application may maintain a directory of users of the social network service. Additionally the address book server application may facilitate interaction between members of the same social network. For example the address book server application may track an online status for each user of the social network service and make the online status available to other members of the same social network. In this manner members of the same social network may be alerted that other network members are online and initiate interactions with the online members.

The directory may contain information about each user of the social network service including contact information and the external services registered for each user. The directory may also identify all the members of each user s social network. In one implementation the user may define the role assigned to each member for a particular external service.

The external service API may be an API invoked by the social network interface that registers the photo sharing service for the first user. Additionally the external service API may be invoked to process the notification sent by the social network interface . Processing the notification may include determining the social network of the updating user. Processing may also include storing multiple notifications one notification for each member of the updating user s social network.

The social network host may be constructed similarly to the external host . The social network host may include a central processing unit CPU a system memory a storage a network interface and a system bus that couples various system components to the CPU .

A number of program modules and data may be stored in the system memory and the storage . Specifically the system memory may include an operating system a social network service application and an external service interface . The storage may contain user preferences .

The social network service application may be software that facilitates interaction between members of the social network service. For example the social network service application may be an instant messaging IM application. To access the IM application the first user and the second user may use the social network client on the client computer and the client computer respectively .

In one implementation the social network client may display a member list of each user s social network. The member list may include a handle or user id that readily identifies each member to the user. The social network client may also identify the members that are currently online.

Additionally the social network client may identify each member in the user s social network member list with recent updates to external services. In such an implementation the social network client may display a means of notification such as an icon next to the user id of each member that has made updates to external services. The means of notification may also be referred to herein as a gleam. The presence of the gleam may indicate that the member with the gleamed user id has made updates to external services. Additionally the presence of the gleam may indicate that the user has not yet viewed the updates.

For example after the first user posts new photographs on the external client the second user may view a gleam next to the first user s user id on the second user s social network member list. In one implementation the second user may click on the gleam to view the summary of the first user s updates.

In response to receiving the click the social network client may send a view request to the external service interface . In response to receiving the view request from the social network client the external service interface may retrieve the summary of the content that has been updated from the external host . The external service interface may then send the summary to the client computer . In one implementation the social network client may display the summary.

In an alternate implementation the social network interface may provide an alternate client not shown to the social network host . The alternate client may be used by the social network host to display summary information about the content that has been updated. The external service interface may store the alternate client in the user preferences .

The system memory may contain more than one social network service application . For example in addition to the IM application the social network host may provide a blogging application. The blogging application may enable users of the social network to create content not shown internal to the social network host . In one implementation updates to internal content may also be gleamed on the social network client .

The client computer may be constructed similarly to the external host . The client computer may include a central processing unit CPU a system memory a storage a network interface and a system bus that couples various system components to the CPU . The system memory may contain an operating system the external service client and the social network client .

Additionally the first user may enter commands and information into the client computer through input devices . The input devices may include devices such as a keyboard and pointing device. Other input devices may include a microphone joystick game pad satellite dish scanner or the like. These and other input devices may be connected to the CPU through an serial port interface coupled to the system bus but may be connected by other interfaces such as a parallel port game port or a universal serial bus USB .

One or more output devices may also be connected to the system bus via an interface such as a video adapter. The output devices may include a display monitor or other peripheral output devices such as speakers and printers.

The client computer may be constructed similarly to the client computer . The client computer may include a central processing unit CPU a system memory a storage a network interface and a system bus that couples various system components to the CPU . The system memory may contain an operating system and the social network client .

Additionally the client computer may include input devices and output devices connected to the system bus .

As stated previously the social network interface may send a notification to the address book clearing house when a user makes updates to the content . As such at step the external service API may receive a notification from the external host . The notification may identify the user making the update the external host and a timestamp of when the update takes place.

In one implementation the notification may also indicate whether the update is available for viewing to other members of the updating user s social network i.e. whether the update is gleamable. An update that is not gleamable may be an update that the updating user does not want members of the social network to be made aware of via a gleam as described in . In other words if the update is not gleamable the notification may not be sent to the members of the updating user s social network. In some implementations a gleamable flag may be defined according to role.

At step if the update is available for viewing to the updating user s social network at step the external service API may determine all the members of the social network for the updating user.

At step the external service API may store the notification for each member of the updating user s social network. In one implementation the address book clearing house may encompass a multitude of server computers. As such the directory may be distributed across the multitude of server computers. In such an implementation storing one notification for each member of the updating user s social network may implicate an update that is fanned out to numerous server computers. Accordingly the external service API may schedule a batch process on each of the server computers containing the directory entries for the members of the updating user s social network. The batch processes may then store the notification on each server that hosts directory entries for each member of the updating user s social network.

At step the address book server application may receive a request for a social network list which may also be referred to as a buddy list from the social network client . The social network client may display the list to facilitate interactions with members of the user s social network.

At step the address book server application may determine the members of the requesting user s social network. In one implementation the directory may identify all the members of the requesting user s social network.

At step the address book server application may determine which members have made updates to external services. In doing so the address book server application may retrieve the notifications for each of the members in order to determine whether the members have made updates to the external services.

At step the address book server application may determine whether the requesting user has viewed the members external service updates yet. In one implementation the directory may include a timestamp indicating when the requesting user last viewed external service content for each member of the requesting user s social network.

At step the address book server application may send the social network list to the social network client . For external service updates that the requesting user has not yet viewed the social network list may also include notifications for each of the members of the social network whose external service updates the requesting user has not viewed. The social network list may also identify the external host for each unviewed update.

At step the external service interface may receive a request to view the summary of the content that has been updated. The request may be received from the social network client on the client computer .

At step the external service interface may send a request to the external service application to retrieve the summary of the content that has been updated. In one implementation the social network client may display the two most recent updates made by the updating user. The updates may include updates made internally to the social network host and updates made to the external host .

At step the summary or summaries depending on the implementation may be received. At step the external service interface may send the summary to the requesting user on the client computer . In one implementation the summary may be displayed within the social network client . Alternately the summary may be displayed within a user interface provided by the external service application as described with reference to .

In order to prevent previously viewed content from being perceived as new or unviewed at step the notification for which the summary is viewed may be updated. In one implementation the external service interface may send an update message to the address book clearing house . The update message may indicate a timestamp of when the content update is viewed by the second user. The address book server application may then update the notification to indicate that the requesting user has viewed the associated summary.

It should be understood that the various technologies described herein may be implemented in connection with hardware software or a combination of both. Thus various technologies or certain aspects or portions thereof may take the form of program code i.e. instructions embodied in tangible media such as floppy diskettes CD ROMs hard drives or any other machine readable storage medium wherein when the program code is loaded into and executed by a machine such as a computer the machine becomes an apparatus for practicing the various technologies. In the case of program code execution on programmable computers the computing device may include a processor a storage medium readable by the processor including volatile and non volatile memory and or storage elements at least one input device and at least one output device. One or more programs that may implement or utilize the various technologies described herein may use an application programming interface API reusable controls and the like. Such programs may be implemented in a high level procedural or object oriented programming language to communicate with a computer system. However the program s may be implemented in assembly or machine language if desired. In any case the language may be a compiled or interpreted language and combined with hardware implementations.

Although the subject matter has been described in language specific to structural features and or methodological acts it is to be understood that the subject matter defined in the appended claims is not necessarily limited to the specific features or acts described above. Rather the specific features and acts described above are disclosed as example forms of implementing the claims.

