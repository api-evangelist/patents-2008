---

title: Electronic item management and archival system and method of operating the same
abstract: An electronic item management and archival system for managing and archiving items. Each item includes at least one of image data, audio data, and video data. The system includes a server configured to receive items, archive at least one of the received items to an archive, and retrieve at least one of the archived items from the archive. In some embodiments, the server also includes architecture that supports a pool of threads promoting multiple, independent archive and retrieve operations concurrently.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07752286&OS=07752286&RS=07752286
owner: Fiserv Incorporated
number: 07752286
owner_city: Brookfield
owner_country: US
publication_date: 20080321
---
This application is a divisional of U.S. patent application Ser. No. 10 199 950 filed Jul. 19 2002 which has since issued as U.S. Pat. No. 7 379 978 on May 27 2008 the entire contents of which are incorporated by reference herein.

Individuals businesses government agencies and other institutions of all types issue checks and similar financial documents to make payments in the United States and internationally. There is a well defined and well known process within the banking system that supports checks as a payment mechanism. Included within this process is the practice of imaging checks and performing document management on the imaged checks. Example document management processes include archiving and storing the imaged checks. After the checks are archived and stored later document management processes can include querying the archive and retrieving stored documents from the archive.

Similarly there are countless numbers of other industries that require archiving storing querying and retrieving of images audio recordings or video recordings.

The invention provides an electronic item management and archival system for managing and archiving items. Each item includes at least one of image data audio data and video data. The system includes an item generation device configured to provide items and a server in communication with the item generation device. The server is configured to receive the items from the item generation device archive at least one of the received items to an archive and retrieve at least one of the archived items from the archive. In some embodiments the server includes architecture that supports a pool of threads promoting multiple independent archive and retrieve operations concurrently. Some embodiments of the invention can further include a storage device in communication with the server. The storage device is configured to receive the archived items from the server and store the received items.

The invention also provides a host machine for an electronic item management and archival system. The host machine includes a communications endpoint that receives items a processor connected to the communications endpoint and software executable by the processor. In some embodiments the software includes instructions that create one or more virtual servers. The one or more virtual servers include at least one server that facilitates independent and concurrent communication between multiple Common Object Request Broker Architecture CORBA applications and at least one server that creates and manages an archive.

The invention further provides a method of managing an archive having items. Each item including a virtual object and query data associated with the virtual object. Each virtual object is selected from the group consisting of image data audio data and video data. The method includes providing a plurality of items archiving at least one of the provided items to an archive querying the archive retrieving at least one of the archived items from the archive and repeating one or more of the providing archiving querying and retrieving acts. In some embodiments the method also includes structuring a bus that allows two or more of the providing archiving querying retrieving and repeating acts to occur concurrently.

The invention is not limited in its application to the details of construction and the arrangement of components set forth in the following description or illustrated in the following drawings. The invention is capable of other embodiments and of being practiced or of being carried out in various ways. Also the phraseology and terminology used herein is for the purpose of description and should not be regarded as limiting. The use of including comprising or having and variations thereof herein is meant to encompass the items listed thereafter and equivalents thereof as well as additional items. The terms connected coupled and mounted are used broadly and encompass both direct and indirect connections couplings and mountings. In addition the terms connected and coupled are not restricted to physical or mechanical connections or couplings. As used herein the terms machine computer and server are not limited to a device with a single processor but may encompass multiple devices e.g. computers linked in a system devices with multiple processors special purpose devices devices with various peripherals and input and output devices software acting as a computer or server and combinations of the above.

As used herein the term image data refers to data or a file having data that represents an image of a physical object. For example the physical object can be a document e.g. a financial document and the image is data representing an image of the object. For another example the physical object can be a form having entered information and the image is data representing the completed form. Example original documents include checks e.g. for a demand deposit account DDA signature cards driver s licenses photographs applications e.g. loan applications reports and other related documents. The term video data refers to data or a file having data that represents a plurality of images. The term audio data refers to data or a file having data that represents one or more sounds. The original image plurality of images or sound s are referred to as an actual object and the item includes a virtual object representing the actual object.

Unless specified otherwise the term image is used below to include image data video data or audio data representing an object. For simplifying the description below and unless specified otherwise the EIMA system is described in connection with check processing and the image is an image front or back of the check. However the invention is not limited to check processing and a claim should not be limited to check processing unless check processing is specifically recited within the claim.

Further while an EIMA system is described in detail below not all aspects of the system are required in all embodiments. Rather some embodiments include only some of the components and or perform only some of the operations described below. Additionally other embodiments can include additional components and or include additional operations that are not disclosed below but nonetheless can be incorporated with the EIMA system .

As shown in one embodiment of the invention comprises the EIMA system that includes one or more item input devices one or more host servers one or more workstation computers and one or more peripheral devices . Each of these elements is described below.

In general the item input device provides information regarding a plurality of images e.g. checks to the host server . As used herein the term information is broadly construed to comprise images and data relating to or obtained from the images. For example if the provided information relates to checks then the information may include the front and back images of each check and data e.g. MICR data obtained from the check obtained from each check. The image s and data for one document form an item. Example item input devices also referred to as item generation devices include scanners check transports video generation devices having a camera or similar component sound generation devices having a microphone or similar component and data feeds for receiving data from other devices e.g. web feeds from other devices or feeds that receive previously stored data including items .

The item input device includes a controller configured to control the input device and or to receive input data. The controller is configured to provide one or more threads of data. Additionally although only one item input device is shown in the EIMA system can include multiple item input devices a second is shown in phantom providing multiple threads of information to one or more host servers via a network connection . However unless specified otherwise the description below is for a system having only one item input device and is specifically a check scanner.

In one embodiment the item input device includes a NCR 7780 scanner having multiple scanning components. The scanner scans financial documents e.g. checks and obtains related financial data from the document in a well known manner. For example the related financial data can include magnetic ink character recognition MICR information account numbers check numbers and related data depending on specifics of the documents recorded and the institution requirements optical character recognition OCR information and similar information. The resulting images can be in any format e.g. .jpeg .tif .bit etc. .

The item input device also includes a controller that among other things communicates with the scanner e.g. via a LAN to receive information from the scanner and to communicate the information to other components e.g. to the host server . Example controllers include a computer e.g. a PC having software executed by the computer to configure the computer a specially designed electronic device having programmable logic executed by the electronic device to configure the device or application specific or special purpose circuits.

The item input device also has a sorter e.g. a hard wired sorter or a virtual sorter which may be part of the scanner or the controller. The sorter includes a rule based engine having rules that control the flow of the resulting scanned images and related data. That is checks are provided to the scanner in a commingled relationship the scanner scans the checks to create one or more images the scanner obtains data relating to the checks and the rule based engine performs front end processing on the checks to sort the checks. For a simple example the rule based engine may specify that a check having transit number A be provided on thread A and a check having transit number B be provided on thread B. The rule based engine can include any number of rules to sort the checks. For other embodiments the rule based engine can include rules based on different image or video or audio items e.g. different types of checks different types of financial documents etc. . In yet other embodiments the host server can include the virtual sorter.

The controller further includes one or more connections e.g. an Ethernet connection that connect the scanner to the host server . The connection between the controller and the host server can be a direct connection or an indirect connection e.g. via a network such as an intranet or the Internet .

As will be discussed further below information travels throughout the system using threads. Each thread contains information e.g. a plurality of items having one or more similar characteristics. Because of the similar characteristics the same operations are performed on the information contained in a thread . For example the information can be routed to a specific host server or a specific storage device discussed below . As will become more apparent below the concept of utilizing multiple threads and consequently performing multiple processes can be utilized throughout the whole system .

The EIMA system includes a host server that runs software. As used herein the term software is broadly construed to include computer programs procedures modules data etc. executable by one or more processors. The software includes software modules also referred to herein as applications that are executed by the host server to perform one or more processes or supporting functions. Some of the software modules result in the host server having virtual servers. The host server is a Hewlett Packard V Series server in one embodiment of the invention.

In some embodiments the host server receives information including images and related data from the item input device processes the information archives the information receives instructions or requests from the workstation performs operations based on the received instructions or requests and communicates information to the workstation or to the one or more peripheral devices . An example of such a server is the Titan 4.0 server offered by ImageSoft Technologies of Maitland Fla.

For the EIMA system shown the host computer includes the servers listed in TABLE 1. It should be noted that not all of the servers described below are required for all embodiments and the EIMA system can include additional servers not described below. The titles of the servers and the division of the functions of the servers are for explanatory purposes only. One or more functions performed by the one of the servers may be combined with other servers.

Among other things in some embodiments the servers provide a multiple threaded bus that allows multiple lines of communication to occur between modules of the system. For the embodiment described herein the bus is based on a CORBA architecture. Other architectures can also be used without departing from the invention.

In general the Common Object Request Broker Architecture CORBA is a standard created by the Object Management Group OMG that enables operation between different computers operating systems and programming languages e.g. distributive computing . The CORBA standard generally specifies how client applications may invoke requests on server objects. CORBA specifies the Object Request Broker ORB that allows applications to communicate with one another regardless of where the applications reside on a network. Using a standard Internet Inter ORB Protocol IIOP a CORBA based program from a vendor on almost any computer operating system programming language and network may communicate with a CORBA based program from the same or another vendor on almost any other computer operating system programming language and network. The IIOP specifies how ORBs communicate over networks and can utilize TCP IP implementation of a General Inter ORB Protocol GIOP . The GIOP defines aspects of ORB communication including how messages are sent how bytes are ordered and how parameters are arranged for remote object invocations.

Creation of a distributed computing system based on the CORBA standard can generally begin with an outline of desired functionality and translation of the design into software objects. The objects are expressed in terms of Interface Definition Language IDL interfaces and collected into related modules. In one embodiment of the invention the IDL is utilized for creation of Application Programming Interface API definitions that define how the client and host server systems communicate. One or more IDL files are compiled to generate stub code and skeleton code. The stub code becomes the interface that client applications use to initiate an operation from a server and is programming language independent. The skeleton code provides the interface to object implementations that the host and or virtual servers may provide. Libraries provided through the IDL compilation provide the mechanism for communication between client and host server processes. The CORBA specification ensures that this communication be platform and language independent. Host and or virtual server applications are created for publishing the object references by name through a naming service and upon the request of a client application a reference to a generic CORBA object is returned. This object reference is then narrowed to the stub representation of the remote CORBA object. The client can then invoke operations through the stub reference as if the object was local to the client. Requested operations from the client application are sent to the skeleton reference obtained through the naming service. Using the ORB CORBA IDL stubs and skeletons serve as a connection between client and server application threads. In addition each client and server can have threading definitions defined in a Portable Object Adapter POA which controls the communication to a CORBA Object by associating the object with the ORB. Each POA service may use single threaded or multiple threaded communication protocols and the multiple threaded protocols may be further defined as pools of threads or as a thread per client. The machine independence of the CORBA standard as utilized by embodiments of the invention allows for multiple processes to communicate across machines platforms and languages thereby providing a distributed computing environment.

In another embodiment the CORBA communication protocols are utilized to abstract client and server interactions. Using the IDL APIs are created that separate the architecture logic. Therefore the CORBA communication layer acts to hide or mask the host and virtual servers from the client or business logic. Each server process in the EIMA system can be defined to utilize the multiple threaded pools of threads thereby allowing non blocking calls to be handled from a large number of client applications. Each client application can be handled independently and therefore do not block each other during communication with the servers. The name service and event service defined by the CORBA specification are used to handle name lookups for services and event routing or channeling. In addition a host or virtual server may execute multiple Generic Input Applications GIAs statement prints and exports at the same time all of which may execute independent of each other and interact separately with an archive or database. Implementation of the CORBA bus in this embodiment also includes providing object services for use by multiple distributed object programs. These services include domain independent interfaces such as the naming service a trading service a repository service an indexing service a set service a parameter service a log service an application service and a redundancy replication service. The services are available to CORBA objects and a client may initiate multiple services if desired. For example a client application may invoke multiple services when interfacing data with input output I O devices. Alternatively multiple threads can exist within the services themselves. For example depending on the operation a user or client may invoke multiple threads within the repository service. In some embodiments the EIMA system may also implement a factory concept whereby a server is a service factory that handles queries each time a client connects and requests an individual session. Each session manages its own client and then allows for the abstraction and separation of logic for multiple client applications.

In addition to the software already described above the host server includes additional modules that interact with the one or more workstations to perform additional operations. This suite of modules generally comprise two sets of modules 1 management programs and utilities collectively referred to as management programs and 2 Web based user programs. The management programs allow an administrator to control the host server and more broadly the EIMA System. The Web based programs which run in a Web browser e.g. Internet Explorer are accessed from an EIMA Web site and allow users to perform operations e.g. perform queries print statements export objects etc. on the archive. Various software modules that interact with the workstation are summarized in TABLE 2 and are further discussed in detail in the operation section. Similar to the servers not all of the modules described below are required for all embodiments and the host server can include additional modules not described below. The titles of the modules and the division of the functions of the modules are for explanatory purposes only. One or more functions performed by the modules may be combined with other modules. Additionally the operation section below may include additional modules that are not listed in TABLE 2 but would be apparent based on the description.

A number of the applications summarized above form a Generic Input Application GIA . The GIA is an application that receives data from the scanner performs operations on the data e.g. for consistency and archives the data to one or more databases. The one or more databases form an archive discussed further below . Example operations performed by the GIA include Image Capture Image Match MICR Exit Batch Update and MICR exit.

Before proceeding further it should be noted that an identifier used for identifying a particular component application tool engine operation act button etc. is for identifying that component application tool engine operation act button etc. only and should not be limiting. For example the term Image Capture identifies an application used by the EIMA system for capturing images. Other terms for identifying the application could be used in place of Image Capture. 

The operations of some of the applications in TABLE 2 are briefly described below. A more detailed discussion of these applications are further discussed in the operations section below.

Image Capture allows a user to import images through 1 scanning documents into an archive and then using Image Match discussed below to insert images into the database 2 importing raw files from disk or tape 3 importing TIFFs or other objects or 4 importing text documents using the Import Server.

Image Match verifies the contents of an image database with a user supplied match control file MCF and prepares the images for Image Print. The Image Match process verifies that all images expected for capture were captured and that no extra images exist. Images referenced in the MCF but not found in the database are referred to as missing items. Images in the database but not referenced by the MCF are called free items. After the images are validated by this process they can be printed with statements Match for Print . When Image Match is complete it generates Missing and Free Items reports and appends a record to an Audit report which lists the processing statistics.

The Batch Update feature lets the user update user fields in a query table after the cycle has been ingested into the archive database. In Batch Update the user loads data from a specified source file or tape in a temporary table. This data file can include all or some of the items in a cycle. The EIMA system finds matches in the cycle with items in the file. Only matched items will be updated with the fixed data in the input file. Batch Update is an option that appears at the end of an Image Match session.

Image Print controls the statement printing process. It combines statement text data in the print control file PCF with the images from the image database to produce statements with images instead of original items. The resulting imaged statement can be sent directly to the printer and or to tape for offline printers mainframe printers or selective reprints. When the Image Print process has completed a record that lists the processing statistics is appended to the Audit report.

The archive function is used to store track and access images as they are migrated from one type of storage device discussed below to another. When images are first captured they are initially stored on the fastest retrieval media local hard drive or RAID. After the images have been retained on the hard drive for a designated period of time they are migrated to other media for more permanent storage. The archiving and distribution functions enable the system to store images on optical disk or tape.

Reconciled Export allows the user to export and distribute the results of a query to a CD ROM writer. In one embodiment the exported images are written as compressed tagged image file format TIFF graphic images. You can use Image Library Offline to view and organize the CD ROM images.

The one or more peripheral devices include one or more memory devices for among other things maintaining the archive. The one or more memory devices can include RAID optical storage tape storage and similar storage devices. The one or more memory devices store a plurality of databases that form an archive which can be of various types including local or distributed. As will become more apparent below a distributed archive can include multiple local archives.

An archive is designed to hold any type of item. That being said it is necessary to have routines to pass items to the archive export items from the archive and view items in the archive. In one embodiment the local archive supports three storage media for image storage and one storage media for indexes.

The three media or tiers of the archive are RAID Optical and Tape. The composition of the archive is driven by cost retrieval time and or service agreements. Each media has its advantages and disadvantages. RAID is a random accessible media with the highest cost per byte of storage but it is self recoverable and very fast. The cost of this media is falling but it still remains expensive per byte compared to other media.

Optical is a random accessible media which uses a jukebox to reduce the number of active drives required to provide a level of service. The media is never brought into direct contact with anything that will damage it and as a result it is a very reliable long term storage media for high activity with long life. This media is the best of the three for long term storage and retrievability without a duplicate backup. With the ability to use multiple drives at any point in time this media is highly accessible at a much lower cost per byte stored and can provide the fast access necessary for on line queries.

Tape is a serial media which uses a silo to manage the tape media. This is viewed by many institutions as the preferred media for long term storage even with the need to maintain a duplicate of each media to insure recoverability. The media is brought into contact with the read write heads and as a result is very susceptible to damage if used highly over a period of time. This media is the least expensive per byte stored but it is also the slowest media. The speed of the retrievals from this media is a direct function of the speed of the drives and the technique used to store the data on the media.

Each industry will have its own migration strategies relating to the movement of the images among levels of the archive. There are several methods to achieve this migration. The following discusses the different methods available to the institutions using an archive of the invention. Unlike previous archives the archive of the invention moves images from any archive tier to any other archive tier. Also through the use of different capture processes the objects being received into the archive can be placed on any tier of the archive and any of the distributed archive locations at the same time. There are many considerations to doing this and just because the archive is capable of it does not mean that it is in the institutions best interest to use this capability. Additionally it should be understood that other aspects of the EIMA system can use an archive of the prior art.

This is the traditional method used by institutions and it allows the institution to purchase the least expensive solution while providing a system that supports good response time and the ability to optimize the data that is stored. This method allows the user to do all repair work on the object and deletion of extra objects prior to the migration to the next level of the archive. Some institutions will migrate from the RAID tier once maintenance is complete to both the Optical and Tape tier at the same time. Many institutions have the ability to store the object at capture time on all Tiers of the archive used by the site. This capability is available through the use of the prime pass capture capability but the institution looses the ability to optimize the storage of objects identified later. The institution will inherently use more storage because the objects that are deleted during maintenance remain present on the slower tiers of the archive using space even though they are not accessible due to the deletion of the indexes.

This is available with the archive of the invention. In one implementation the capture controller software takes a match control file MCF file from the mainframe that has the database to which the item is to be sent and the document identification number DIN number of the item as part of the MCF entry. This allows the capture controller to read the MCF populate all the data fields use the DIN number to pull the item images and send the item down the thread to the proper database. An advantage to the institution of this type of activity is that it avoids the time consuming migration process from one media type to another. However a detriment to the institution is that this method does not provide any method of optimizing the way objects are moved to the slower tiers of the archive so as to allow for retrievals that will roughly match the higher speed tiers of the archive.

To avoid the need to go through very time consuming reorganizes of the storage the objects are migrated in large blocks which for example can represent a days capture. Until all the objects in a block have been migrated the block space cannot be freed for the storage of new objects. This method works well for all parts of the archive that have random access and if the long term archive tier is used very sparingly this method will also work for the serial tier of the archive. Because many institutions want to go to two tier archives it has become necessary to provide a migration strategy that will organize the object placed on the serial media in a way that will facilitate the optimal retrieval of the objects from this tier. The following defines this optimal migration strategy.

This method can be used most effectively when an institution has a minimum number of days e.g. 45 days of RAID object storage. In this case the migration takes place over a ten day period for the previous thirty days of items on the archive. One tenth of the previous 30 days is migrated to tape every day so that after ten days all the items have been migrated. Of course a different proportion can be used. These items are organized on the tape according to what data elements are used the most to retrieve the object. Once all the items have been migrated from this 30 day period all the objects are deleted in a way so as to keep the number of days defined in the service level agreement SLA on the high speed tier and the space is freed for the capture of additional objects. Once there is 30 days of un migrated data on RAID the 10 day migration cycle begins again. This method of migration is tailored to the maximum retrieval speed of objects on the long term archive. With 45 days of RAID the user has the long term archive optimized on a 30 day bases and the days of storage are used in the following way 

This capability allows the capture of any object into any database on either a collective basis or an individual object basis. When a capture is started it can be directed into a specific database or through the use of a front end capture routine can route the individual objects to different databases based on the accompanying index data. In the case of an item processing department this means that transit items can go to one database and on us items to a different database. This also means that the banks that process for other banks can route the items for each of its bank customers to its own database.

When an institution outgrows a single site environment or would like to have more than one active system to back up data a distributed archive can be used. The distributed archive feature allows some embodiments of the invention comprising the EIMA system to add data to multiple separate archives at multiple locations while providing many threads of internal archive access. The feature supports maintenance and retrieval of archive data from the various sites in addition to optional long term storage sites within the network. Each location has all the capabilities identified as basic to the local archive but through the distributed archive capabilities appear to each application e.g. Export Statement Print Query etc. as if the plurality of archives are one distributed archive.

In one embodiment the distributed archive is server based and makes full use of the CORBA Bus. The distributed archive server makes all sites look and operate as one. This means that any function that operates at one location can have full access directly to all other locations within the security capabilities allocated to the distributed archive. The speed of the distributed archive is only constrained by the speed of the line connecting the geographically dispersed locations.

To manage the network traffic and to eliminate the delivery of duplicates the distributed archive includes internal rules. Example internal rules include rules for routing request to the fastest service location and rules that allow for the removal of duplicates prior to responding to a query.

As shown earlier through the use of the direct capture to a database capability there is the ability to deliver items to many databases at the same time with each database on different media and locations. An update capability can be used to automate the updating of all locations that house the same item. This capability makes full use of the distributed archive capability of the system to find all locations housing an item that is being updated and then it also is used to update the same items held in different databases as well as at different geographical locations.

In some embodiments the distributed archive provides the institution with the ability to have different geographical locations provides full hot backup for other locations without forcing the purchase of full redundant hardware at each location and or different physical servers in a single location or any combination of physical servers and geographical locations and or provides hot backup for other locations or servers thus leveraging the use of existing and planned hardware. The loss of a single geographical location does not effect the retrieval of requested information from sites that are operational and if the same data is redundant in an alternate location the request is be fully satisfied automatically from the alternate site. If the data is not held at an alternate location or has not arrived at the alternate location the requesting user is provided with all available data and is notified that a site is down that may have additional data and that the user may want to request that data at a later time. When the site that is down comes back on line it will connect back into the network automatically and without the involvement of institution personnel.

If the distributed archive is used with a hot backup strategy then it can be coupled with the appropriate migration strategy. If the institution has enough bandwidth on their network this synchronization is done through the network. If the institution s network is not robust enough to handle the volume created by image data it will be moved via tape. When tape is used to synchronize the archives then when the tape arrives at the remote location and is loaded into the appropriate tier of the archive the indexes at the distributed location are updated and a verification record is forwarded to the originating location identifying the fact that the synchronization tape has arrived and is now in the remote location. If no synchronization record arrives after a period of time a new tape is created to replace the original tape.

Although specific installations may vary on the basis of hardware and or network configuration the functionality remains the same for some embodiments of the invention. The use of CORBA and Java enable the EIMA system to run on any operating system and hardware regardless of platform database operating system programming language or network hardware software used. The distributed architecture is highly scaleable and is sufficiently dynamic to accommodate a verity of potential archive systems. Further the Java programming enables the system to link to other Web centric applications e.g. online banking .

In some embodiments the distributed archive contains multiple sites all of which have the capability of querying across connected sites. A set of user defined rules determines the level of query capability accorded to each user of the system. Query capability is the functionality of being able to search the system indexes on the basis of an individual object attribute or combination of object attributes to find the token necessary to retrieve the desired object. Query capability can be either local or global. Retrieval of an object on the basis of a call with a token argument is not considered query capability it is simply a retrieval operation supported by a low level media specific local index.

Upon the completion of either prime pass capture utilizing Image Import re pass capture MICR repair match and missing free item resolution all of which are discussed further below a captured items index is stored and available for query and retrieval. If any changes occurred in the index data as a result of any of these activities and the objects have already moved to the alternate location s then update index data should automatically be forwarded to all locations now housing the object. Access to these items as well as items captured at other sites within the distributed environment will be facilitated by the appropriate distribution Proxy s . The Proxy Servers provide the ability to submit requests and return responses from multiple distributed locations without any user intervention. This ability to satisfy individual query and retrieval requests by gathering responses from multiple sites is the foundation of Distributed Archive.

Items captured at a particular site can remain at that site on any installed and supported media magnetic disk optical platter or tape for as long a period as is suitable to the needs of the installation. This time period could be as short as one day or could be counted in years. Additionally captured data can be exported in whole or in part to one or more Global Archive Sites at any time and then be deleted from the original source location once it is confirmed that the data has been successfully archived at the new site. This deletion indicator only indicates that the item is eligible for deletion. The actual deletion is governed by the local archive parameters.

In a purely geographically distributed archive indexes reside on the same server as the tables showing the physical address of images on various media. To the system physical locations may appear as a single virtual index.

In one embodiment users of the distributed archive are institutions with multiple facilities that are used for item processing. The institutions typically have network connections between the associated sites e.g. a WAN . However the system configuration can be adapted based on the user s access needs locality of reference and desire to modify existing network connectivity. The network speed and traffic pattern can dictate the objects are moved via sneaker net via the high speed network. An institution having the distributed archive can also be a very large processing center which has many clustered capture platforms each operating independently but to the user being viewed as a single unit.

In some embodiments every location is considered a master location there are no slave or redundant locations. When objects are moved from one location to another that data is imported into the new location and the introduction of a new item into an archive cause no action except the update of the object and index archive. If any index item is read for the purpose of updating a query the index item is set to all locations to determine if that index set is held at a different location. All locations that respond instruct to make this index set read only for the duration of the update operation.

All updates to the indexes are distributed to all locations having the same index set. This is done by monitoring the write operations retaining all the changes to the indexes then issuing a distributed query for the item that was changed and sending the changes to all locations responding that this object is held at the location. If any location fails to respond the update is held until a response is obtained from the location that the item updated is not housed. Once all sites are updated then the read only lock can be removed from all other locations.

Security features exist on two levels in some embodiments 1 within the application and 2 through the login and password features provided by the database management system. The security facility within the application is used in establishing a connection to the database data server.

By consolidating similar objects together the archive reduces the number of tapes involved in retrieval and makes more objects available on a single tape storage media. As an example if a subpoena was received for all items that were received for an account over the previous 4 years this request would be processed as follows 

 Present Process Each cycle is migrated to tape and depending on the size of the tape there can be any number of cycles on a tape. For purposes of this example there will be only one cycle per tape and one required object per tape. With 260 cycles per year this would mean to satisfy this request would mean that it would be necessary to mount 1040 tapes less the number of cycles still on tiers 1 and 2 assuming at least one item is received daily.

 Organized Migration Strategy The number of days of items on a single tape is a function of the number of days of tier 1 storage that the institution has purchased see Organized Migration Strategy earlier in this document . If there are 45 days of tier 1 storage then a single tape will have 30 cycles worth of objects for this account grouped together on a single tape. This would mean that to satisfy the request the system would only have to mount 35 tapes less the number of cycles still on tier 1 and 2. This represents 3.37 of the mounts when compared to the prior art systems and the number of mounts will go down in direct relationship to the number of days of tier 1 storage that is maintained.

In some embodiments the virtual sorter front end to GIA provides the ability to take a feed from any device either prime pass or re pass and route the objects through the use of rules to any database. The database thread to which the item is routed retains its ability to have a MICR exit tied to that thread only. When the transaction exit capability is added to the virtual sorter the institution now has the ability to populate a transaction identification field identified in the class definition for the type of object being captured. The composition of a transaction is defined by rules contained in the exit and is independent of the rules used to route an object to a database. The application of the transaction rules is done prior to the application of the routing rules.

The following example is how item processing can use the above capabilities to maintain the content of a deposit as a transaction 

Once the objects are in the archive the user can make use of the index database and define different views of the archive based on how the user wants to use the items in the archive. The transaction field may or may not be part of the data used to create these specialized views. In most cases these workflow related archive views will be only available for specified periods of time and will be used for very special work processing.

Through the use of this capability the user can structure any views they please of the archive no matter whither the items are held in the archive in different databases at their local facility or at different locations. In the case of the financial institution these views can include all items in Capture Sequence cash letter which can have multiple document types tied together by unique deposit identification on us or account number order route transit number order exception items which can be by type institution etc. high dollar amount etc.

To better manage the distributive archive it may be necessary to provide more and better reports on what is going on within the archive. These reports can take the form of screen and paper reports and can be used to balance the transaction activity within the archive.

As an example of a management report the system can balance the number of items received from a sorter with the number of items sent. Further the system can balance the number of images that should have been sent against the number received and archived by database. In one embodiment these reports address all parts of the system in such a way that there is no function performed in the system without appropriate balancing and management reports. This balancing and management reporting can include capture export print queries and inventory.

The performance of the distributed archive is largely dependent upon the network configuration. The system architecture is designed to minimize the data to be sent over the network by limiting network activity to remote procedure calls and image movement upon query requests only. Large data movement between archive sites is targeted for high volume media such as tape. However nothing in the system design will preclude the use of a network for large scale image movement for institutions who wish to invest in network communications with sufficient bandwidth to support that activity.

Export to a remote archive allows for data captured at any site to be exported to any other location. The export media can be a tape which can then be physically transported to another site. Alternately the network connection can be utilized for an export to a remote site. Export can also be directly to an NFS mounted UNIX file system or a PC based Remote File System RFS .

Once transported to the new site the information can be reingested into the remote archive through the GIA module. Once the data is successfully ingested into the archive a message can be sent to the originating site indicating that the original data has been successfully migrated and it can be deleted when its retention time expires.

Due to the large volumes of data to be exported the exported data will be drawn directly from the local archive as the export is in progress only a catch large enough to insure maximum network transmission speed will be maintained.

An example of a distributed archive configured in accordance with some embodiments of the invention is shown in . Site A sends its data to Site B for backup and Site B sends its data to Site A for backup. Since Site C does not have a tape silo and it keeps only 180 days on raid and optical. Site C sends their data to both Site A and Site B. For this embodiment there are two copies of Site C s information. The end result is that there are two copies of all data. Distributive Archive allows multiple copies to be at multiple locations and allows a site e.g. Site C to search multiple sites. Site C can use the distributed network to obtain the data as fast as possible and based on its location and the network speed to either Site A or Site B.

For a local archive a Repository Proxy Server manages communications with Optical Repository Tape Repository and Disk Repository. For a distributive archive in one configuration each repository creates a Remote Repository Proxy. The Remote Repository Proxy communicates with the local Optical Repository Tape Repository and Disk Repository but it will also log into the remote buses locations and communicate with the Optical Repositories Tape Repositories and Disk Repositories See .

When the Remote Repository Proxy is called it is provided with a list of items needed. The indexes are retrieved without starting actual image retrieval until the user tags the image as needed. A similar proxy can be used for the index database.

As will become apparent below the one or more peripheral devices can include other devices such as a printer e.g. Xerox IBM and HP PCL compatible printers for printing statements an optical disc writer e.g. a CD ROM writer a communications port for sending facsimile transmissions or electronic communication e.g. email transmissions or other known peripheral devices.

In some embodiments the one or more workstations provides an interface between the EIMA system and a user or administrator provides requests or instructions both also referred to as inputs to the host server which are initiated by the user or administrator receives information from the host server e.g. originating from the archive and provides information to the user. An example workstation is a personal computer. However other workstations are possible including Unix machines laptop computers handheld devices Internet appliances and similar devices. The operation of the workstations for initiating an application e.g. a query an export a statement printing etc. are further described in the operations section below.

A diagram of one workstation is shown in . One specific workstation is an Intel based computer employing a Windows operating system and an Explorer browser. Other types of computers with appropriate operating systems can be used.

The workstation includes a communications port for communicating with the host server one or more input devices and a visual display unit . In one embodiment the one or more input devices includes a keyboard and a mouse that allows a user to input data to the workstation . Other data input devices can be used including a keypad trackball touch screen touchpad pointing stick microphone or similar device. The input devices and having a corresponding driver program stored in the workstation allowing the workstation to communicate with the input devices and . The corresponding driver program for the mouse is a pointer driver program that generates a pointer on the display unit . The pointer driver program allows the pointer to be moved on the visual display unit when a user manipulates the mouse and to select items when the user pushes buttons on the mouse in a prescribed order. Of course other input devices can have corresponding driver programs and can perform functionally similar to the mouse .

While the discussion herein relates to scanned documents and specifically checks other objects including video and audio objects can be imported archived and exported. The names of the modules or applications below are for explanatory purposes only. The operations performed by most of the modules described below can be extended to other types of objects. Additionally none of the modules described below are essential to the invention although many embodiments use many of the modules.

Image Capture allows a user to import images through 1 scanning documents into the EIMA archive and then using Image Match discussed below to insert images into the database 2 importing raw files from disk or tape 3 importing TIFFs or other objects or 4 importing text documents using the Import Server.

For checks Image Capture inputs scanned images and associated MICR data and then stores the MICR data in a temporary table. Any records with invalid MICR data are automatically flagged for repair and Repair GUI discussed below is used to validate these records.

Image Match verifies the contents of the image database with a user supplied match control file MCF and prepares the images for Image Print. The Image Match process verifies that all images expected for capture were captured and that no extra images exist. Images referenced in the MCF but not found in the database are referred to as missing items. Images in the database but not referenced by the MCF are called free items. After the images are validated by this process they can be printed with statements Match for Print . When Image Match is complete it generates Missing and Free Items reports and appends a record to an Audit report which lists the processing statistics.

The Batch Update feature lets the user update user fields in a query table after the cycle has been ingested into the archive database. In Batch Update the user loads data from a specified source file or tape in a temporary table. This data file may include all or some of the items in a cycle. The EIMA system finds matches in the cycle with items in the file. Only matched items will be updated with the fixed data in the input file. Batch Update is an option that appears at the end of an Image Match session.

Image Print controls the statement printing process. It combines statement text data in the print control file PCF with the images from the image database to produce statements with images instead of original items. The resulting imaged statement can be sent directly to the printer and or to tape for offline printers mainframe printers or selective reprints. When the Image Print process has completed a record that lists the processing statistics is appended to the Audit report.

The archive function is used to store track and access images as they are migrated from one type of storage device to another. When images are first captured they are initially stored on the fastest retrieval media local hard drive or RAID. After the images have been retained on the hard drive for a designated period of time they are migrated to other media for more permanent storage. The archiving and distribution functions enable the system to store images on optical disk or tape.

Reconciled Export allows the user to export and distribute the results of a query to a CD ROM writer. In one embodiment the exported images are written as compressed tagged image file format TIFF graphic images. Image Library Offline can be used to view and organize the CD ROM images.

Before most EIMA system procedures can be performed the user specifies the document type database and cycle on which the user wants a particular function to be run. However setting the database and cycle is not a prerequisite for all EIMA procedures. For example running Reconciled Export discussed below does not require the user to select a database and cycle. The user can tell which document type database and cycle is currently selected by viewing the text in brackets and that appears after the first three main menu options. In the example shown in the selected document type is Check the database is TestDB  and the cycle is 20010314. The user can change the document type database and cycle by entering text in the appropriate field.

The user verifies that a server is running by checking if the server s abbreviation appears in the List of Servers on the Application Server Termination Program menu . If the server abbreviation appears on the list then the server is running. If the server abbreviation does not appear on the list then the server needs to be started.

To get to the menu of the user selects the File Management Utilities Menu option . At the File Management Utilities Menu the user enters the Drop Application Server s option . This results in the Application Server Termination Program Menu being displayed. The Application Server Termination Program Menu provides information on the status of each virtual server. For the embodiment shown in the Application Server Termination Program Menu uses abbreviations which correspond to the servers shown in TABLE 1 and if the server is listed then the server is running. Further entering the number of a server and then pressing Enter stops that server.

Image Capture should be performed for the desired documents before the user runs Image Match or Image Print. The user can import images into the EIMA system using the following methods 1 Scanning documents into the archive and then using Image Match to insert images into the database 2 importing raw file data from disk or tape raw file import is used for testing only 3 importing objects e.g. TIFF images 4 and importing text documents using the Import Server.

Image Capture transfers the document images and associated information MICR code from the scanning device to the host system reviews each MICR code for correct syntax stores the images and associated information in an image database scans and stores the special images used by Image Print and or adds a record to the Audit report that lists the processing statistics. The images and their associated MICR data are supplied from the scanning device s .

Image Capture requires that the images and associated MICR data for a specific database cycle name and image capture parameters. The parameters that define Image Capture processing requirements are defined in a Default and Override Parameter files. The Default Parameter file is used by Image Capture each time it is executed. It is also used by all databases in the environment.

During Image Capture Quality Monitor can display a sample of the images as they are added to the archive. Quality Monitor displays a new image according to the user specified time increments e.g. seconds . See the discussion for Repair GUI below for more information on using Quality Monitor.

Multiple scanners are supported by executing separate copies of Image Capture software concurrently. The concurrently running copies of Image Capture can be output to separate databases or the same database. Access to a separate Main Menu is required for each software copy of Image Capture.

The user corrects any MICR errors detected by Image Capture by using MICR Repair. The user performs MICR repair any time after Image Capture is started. After Image Capture and MICR Repair have been completed the user is ready to initiate the Image Match process to validate images and associated data against the match control file MCF . After Image Match is complete the user can run the Image Print process to print images and associated data on customer statements.

If the user runs Incremental Match the user can scan a batch ticket prior to scanning the corresponding batch of items or type the Batch ID at the Main Menu . A batch ticket is a MICR encoded document that contains a four character ID that uniquely identifies the batch. The batch ID is appended to the Match Control File name when the file is brought into the system using File Load. In this way the scanned images are matched to the correct MCF.

The user begins Image Capture when he is ready to scan a new batch of items. If the user uses the Windows version of Quality Monitor the Quality Monitor program is running on the client. Scanned images are stored in an image database that is identified by a unique combination of database and cycle name. When the user is ready to capture images the user can create a new database and cycle for the new set of images or can append the images to an existing database. The database and cycle names may be predetermined by predefined procedures and the name can be related to a corresponding match control file MCF .

In one embodiment the user performs the following acts to capture document data and images into a database cycle 

If Capture terminates as a result of an user error or system problem such as a server returning an exception the Capture Recovery process can accurately roll back tables and post information regarding the last item correctly ingested. The capture recovery process on the host system is as follows 

The user can import TIFF images from tape CD ROM a UNIX processor or other devices for the purpose of transferring images from a main location to a satellite location or for importing special document types. The TIFF Image Import Utility supports square tape Quarter Inch Cartridge QIC CD ROM UNIX process 8 mm tape Digital Linear Tape DLT Tiff Import using GiaGate imports directly into the archive without using Micr Repair Repair GUI or Image Match and Import from third party applications.

As an alternative to scanning the images directly into the Image Archive database through the Image Capture program the user can use Image Import to convert an existing image database to the format used by Image Archive and use the Import server to import the images into the archive.

Due to the unique aspects of an existing image database each client may need a specialized interface that connects to Archive Import API. The user can also use a Generic Importing Application offered by ImageSoft Technologies of Maitland Fla. The Generic Importing Application GIA resides over the Archive Import API and acts as a socket server to more easily obtain the images from other platforms.

A ScanGate II program resides on the host system and is an import application that receives images from the network and imports them directly into the Archive database using the Archive Import API application. Although ScanGate II can accept images directly from an Image Soft scanner application its main purpose is to receive images from another image system where the images have already been validated and associated with other control information. Images and data that have been ingested by ScanGate II are not sent to the ImageSoft MICR Repair system.

The existing image database may already have assigned names that identify the sets of images but these names need to be converted to the format used by the Archive. During Image Import a database cycle name is assigned to each set of images imported from the image database. For the EIMA system described herein the cycle name should be in the format YYYYMMDD which typically represents the original processing date for the set of images. The database name set name typically represents the customer or business entity owning the images or if desirable this may represent the type of image.

For reconciliation purposes Image Match is used to verify that data in the user provided match control file MCF matches the captured data in the archive. Image Match also allows the user to view free items move items and insert missing items into the archive. The Match Menu also contains an option for clearing the currently selected match file. The Match procedure is performed after the user has scanned MICR data and images and resolved MICR problems and before images can be queried and viewed in an image viewing program such as Net Query discussed below .

Image Match also provides ability to add additional search fields to each of the image records using Batch Update. Batch Update allows the user to update the captured data with additional field data that is not part of the original MICR data. For example the user s company may require that a microfilm number be added as a search field to all the records in the captured data. Image Match further provides the ability to generate match statistics reports.

For the embodiment described herein Image Match is required for Image Archiving and Distribution and Statement Generation. The Print server is used to organize images before statement generation discussed below .

When documents are scanned the data from the MICR line is captured and then ingested into the image capture index in the archive. When Image Match is run data in the MCF is compared to the captured data in the archive. Image Match looks at specific fields in both sets of data and then attempts to verify if the data matches or does not match. Following the Image Match process a match statistics summary that details the results of the match session is displayed onscreen.

Each MCF record preferably contains MICR data including the fields required for Image Match group ID and period in statements and user fields. Each record in the captured data contains information about the corresponding image including MICR data made up of the account number serial number amount transaction code and transit routing number and the fields required for retrieving the image from the database e.g. the image location and the size of the image . The MICR data corresponding to the image may have been changed by a MICR Exit program to conform to the data provided in the MCF.

The Match Control Menu MC option of the Main Menu is used to access the Match Control menu which includes a perform match option on the Match Menu to initiate match. ScanGate II users do not need to run Image Match for archiving and distribution.

For one embodiment two levels of match are run. One level or both levels of match can be processed during Image Match. The user sets parameter to determine which fields are used to perform the match assessment. The actual fields that Image Match uses for data verification vary depending on the user s operational needs.

The first level of Image Match is by account field serial field and amount field. This type of match attempts to match the two sets of data using the account number serial number and amount fields and then optionally by the transaction code field and transit routing number field. If Image Match is unable to make a match against these fields it will try to match the data against the account number field and the serial number field and then optionally using the transaction code field and transit routing number field.

The second level of Image Match is by account field and amount field. This type of match attempts to match the two sets of data by comparing the account number field and amount field and then optionally by the transaction code and transit routing number fields. This match is used only after the other items in an account have been matched by the account number serial number and amount fields. Other criteria of levels for performing a match are possible.

The Image Match process allows captured data and images to be available for query and viewing in the Net Query program. After running Image Match missing and free items are generated and the user can generate a Free Items report a Match Statistics report a Missing Items report and an Audit report. In addition Image Match can perform statement printing.

During an Image Match session the user will have an option to run a batch update. Batch Update allows the user to update the captured data with additional field data that is not part of the original MICR data.

When performing a match the match database and cycle should be selected. Additionally the user should start if not already running the CORBA Name Server the Set Server the Bus Administrator Server the Proxy Index Server the Parameter Server the Disk Repository Server the Log Server and the Repository Proxy Server before performing the match.

The resetting match options clears the temporary match space. For example if user loads the wrong match file resetting match will clear the match file so that the user can load the proper match control file.

If any missing or free items are noted in the onscreen match results summary the user can correct these items and then rerun Match. Free items are extra images that have been noted in the capture data but not in the match control file MCF . Free items indicate that there is a discrepancy between the number of items in the capture data and the number of items in the MCF.

Missing items occur when there are records in the MCF with no corresponding images. There is usually a direct correlation between the number of free items and the number of missing items.

Free items can be the result of scanned items that do not belong in the current database cycle or incorrect MICR data. If a large percentage of free items appear on the report there was likely a mechanical problem during Image Capture. It is possible that the wrong tray was scanned or not all of the trays were scanned. In this case the user runs Image Capture again. If the percentage of free items is small the discrepancies are probably the result of incorrect or illegible MICR data. In this case the user needs to release the images to the MICR Repair workstation for correction. Once the MICR data is repaired the user should be able to run Match again without error. To correct the unmatched items the user performs the following acts in this embodiment of the invention 

If the image data is captured clean i.e. defective data has been repaired and the MICR exit has taken place then after capture takes place the index tables are set as matched. If however the user would still like to verify whether all the items that have passed to GIA are actually stored in the archive then the user can provide a text file containing a user defined set of fields to be matched against. The match fields can be configured through the parameter service. Verify Capture matches items in the file with rows in the Index table and provides reports with results of the match. Verify Capture provides match statistics a list of missing items a list of free items. The differences between Image Match and Verify Capture include Image Match performs match incrementally Verify Capture does not Image Match only matches those items that are marked as unmatched and Verify Capture matches items that are already marked as matched Image Match updates a user specified set of fields from items in the MCF file and Verify Capture does no updates.

To perform Verifying Capture the user navigates from the Main Menu to the Verify Capture option. Upon initiation of Verify Capture the MCF file is loaded and matched against the database and cycle. The match results are displayed. The user can then generate capture reports.

To export a selected group of images to media such as a CD ROM the user can create a text file that includes query criteria and destination specifications. This file is called a Text File Batch Query TFBQ .

The TFBQ can be created on a PC using any ASCII editor that does not embed formatting characters into the file. The file can also be created on a UNIX system using vi the text editor for Unix systems. Once created the user creates the file moves or copies the file to a directory on the host system and then executes the file to locate the images.

Reconciled Export allows the user to export check items and images that meet a specific criteria to a CD ROM writer other method of deliveries are possible . Once the job has been exported to the CD ROM writer the user can create CD ROMs that contain the query results of the TFBQ. The CD ROM s can then be distributed for viewing with an Image Library Offline program. An example Image Library Offline program is offered by ImageSoft Technologies of Maitland Fla. The scope of items that are exported to the CD ROM writer is determined by the Export Job s query criteria. A text file batch query is used to specify each export job s query definition and destination specifications.

Prior to running Reconciled Export the user should verify that the export job s query and export destination parameters are defined in the TFBQ the export job s TFBQ and corresponding match control file MCF are placed in the correct directory the export job s parameters are set in the job control file JCF and then placed in the correct directory and the Export server is running.

During Reconciled Export the user reviews the Job List report that is updated after the user starts the export process. The Job List report shows if any missing items have been found for a particular export job. If missing items have been detected the user should correct these items and then rerun Image Match. A Missing Item report can be generated from the Export Reconciliation Menu. After a successful export the export job is released to the CD ROM writer for CD ROM production.

The Job Control File contains the parameters that are used to process an export job in Reconciled Export. These parameters define the export job s name and the directory locations of the files that contain the query specifications and the MCF and report data. A job control file can contain multiple export jobs. Before running Reconciled Export the job control file parameters should be set. The job control file parameters include JOB NAME TFBQ FILE and MCF FILE parameters which are typically required and REPORT parameters which is optional. The JOB NAME parameter designates the name of the export job which is generated before and after Reconciled Export. The TFBQ FILE points to the location of the text file batch query TFBQ file in EIMA system. The TFBQ file contains the export job s query criteria and the destination specifications. The MCF FILE points to the directory location of the match control file MCF . During Reconciled Export data in the MCF is compared to the captured data in the archive. The MCF contains the MICR data the Group ID and period in statements and the query fields. The REPORT parameters point to the location of an optional report file.

The Job List report is generated and updated during the Reconciled Export process to help the user track the progress of the user s export jobs. The Job List report shows the before and after status of the export jobs. Before items are exported the Job List report lists the number of items that will be exported to the CD ROM writer and if any missing items were detected. After items have been exported to the CD ROM writer the Job List report shows the ID that was assigned to each export job.

The Job List report provides the batch that contains the items and images that will be exported to the CD ROM writer based on the query criteria in the text file batch query TFBQ the Name of the job as specified in the job control file the number of items that met the TFBQ s criteria and the number of items that will be exported to the CD ROM writer the number of items in the batch but missing from the MCF and the number assigned to the export job. This number assigned to the export job can be used to track the progress of the export job. If the user uses the Job Manager or Resource Manager program the same export ID number that appears in the Job List report is shown in both of these programs.

The Reconciled Export process enables the user to export images to a CD ROM writer by loading the job control file that contains the query specifications. If missing items are detected the user has the option of viewing a Missing Item Report.

To delete a database cycle from one or all of the following locations the user performs the following acts 

Deleting a database permanently removes the database from the archive. Before the user deletes a database the user should delete all cycles within the database.

Migrating from RAID to optical allows the user to move a copy of the document data and image files in a particular database cycle from disk RAID to an optical device. The migration process enables the user to free up disk space. After the user has successfully migrated the files from disk to optical the user can delete the database files from disk. The Optical Repository server and the Optical Robotic server need to be running. To migrate images from RAID to Optical the user performs the following acts 

The Restore procedure for multi file backup is the same as the standard restore procedure except that now the system keeps track of cycles that the user has backed up and their corresponding tape Volume IDs. The system will request that the user mount the specific tape Volume ID for the cycle he has selected to restore.

The purpose of the Print Server is to allow the user to retrieve a subset of images from a database cycle for statement printing. For example the user can have a database that contains all items for an entire month or the user may want to pull out items for customers who require statement print. The user uses a match control file to match up the items that he wants to print. The user can then run statement print for the clients that require it.

The print server retrieves the objects directly from the archive database. Any objects received and placed into a new cycle are in a format that is immediately viewable by NetQuery. In addition the Print Server allows the user to export print images to a remote server for printing purposes instead of on the main host system.

The following steps refer to two different servers a main server and a receiving server. To retrieve images using the Print Server the user performs the following acts 

Image Print produces account statements with both text and images in some embodiments of the invention. Image Print retrieves images that are predetermined by Image Match from the image database processes them blocks them on a page and formats them for a particular laser printer with the appropriate header information. It then merges the images with statement text data in an output data stream to a designated printer and or tape drive.

If the user has defined surrogate images they will be printed in place of any missing items during the Image Print process. Parameters for surrogate images may be defined using the Parameter Menu.

During the Image Print process communications software controls the actual transmission of documents to the output device. The ability to format customer statements for output to a laser printer and merge the statement text with the blocked images is an important Image Print feature.

If the user wants to modify the format of statements by groups of account numbers the user must place all image statements for a set of accounts in a single database and use the Parameter Menu to modify the format parameters. In addition Image Print parameters provides the user with several options for increasing efficiency and controlling presentation of the final output.

Arranges text information on statement and image pages. For images the user can specify page size and margins page numbering duplex support image placement and image bordering. For text data the user can specify font print position and include text lines on image pages. The user can add text such as serial number and amount on or under the images.

The user can use Account Separator Images to separate multiple accounts associated with the same customer for consolidated printed statements. This is necessary when a customer single customer number has several accounts. The user can create up to 99 different line separators by using the Image Match line parameter. The line separator can be a simple as a horizontal line or it can be more elaborate.

Splitting statement printing into batches is a very useful and timesaving function of Image Print. This function enables the user to specify how Image Print processes statement information for maximum efficiency.

Statements identified as having exceeded a user specified ratio of missing or bad images can be processed into a separate file for further processing while good statements continue through the printing process unhampered. For example the user can specify that each statement missing more than three individual images and or more than 10 percent of total images is bad.

Good bad splitting is executed from the Print Control Menu and is controlled by parameters specified in the default and or override parameter file. If the specifications designated by the parameters are exceeded the statements are processed as bad.

The user may find it beneficial to use the Good Bad Split function even if he does not require the statements to be split. This Split function performs many of the same processes as Print but in a fraction of the time. This provides a way to review for errors before running Print.

Statements can be sorted into different print files according to their size volume as defined by the user in the parameters file. This enables the user to use printing and processing hardware in a more efficient manner. The user can direct large volume files grouped for example by zip code to special handling equipment or configure equipment in the fashion which best suits each type of printing session.

The document sets that are produced by Image Print can be grouped into output segments so that one segment can be completed and begin printing while later document sets within the same job are still being formatted.

Statements can be formatted for a variety of Xerox IBM and HP PCL compatible printers. The target printer may have special parameter requirements.

Image Print parameters should be defined Image Print parameters provide information for page formatting headings printer channel assignments splitting routines etc. As many sets of parameters can be maintained as are required to meet different processing requirements. For example a banking institution may require one set of parameters for printing account statements and another for money market accounts. During the initial installation period a trial and error approach to adjusting parameter specifications may be necessary in order to fine tune the statements final presentation.

The Print Control File should be loaded and ready for processing For standard Image Print runs the Print Control File PCF is built by the institution s account processing procedures. The PCF contains the body of the standard statement text and determines the accounts to be printed and their sequence.

Image Match processing for the proposed run should be complete The Image Match process uses information contained in the user produced Match Control File MCF . The MCF is generated by the institution s account processing system and this information is then used for Image Print.

Before printing statements the user defines the print parameters e.g. identifies page formatting headings etc. defines the load parameters e.g. identifies where the files are located PCF exit program to use etc. and defines Capture Match and Archive Parameters. The Capture Match and Archive parameters determine scaling of images levels of matching etc. Additionally the user obtains a Match Control File MCF obtains a Print Control File PCF and retrieves image objects from different cycles. To print directly to HP or IBM printers the user performs the following acts 

In addition to printing directly to HP or IBM Printers the user can print to tape. The user first obtains the image objects MCF and PCF as discussed in the previous section. The user then loads a blank tape into the tape drive. Typically a minimum of two blank tapes one for the index and one for the data is required. After loading the tape the user prints the information to the tape. When this process is complete the user takes the data tape to the printer that the user uses for printing the statements. The user loads the tape into the print controller s tape drive. The user can then print the statements.

An HPIP server processes the print stream in a manner that replicates data as if it came from a tape. The EIMA includes an HPIP board and HPIP software in a workstation allowing the user to print directly to the printer at a faster speed. The user first obtains the image objects MCF and PCF as discussed earlier.

Using the Print Control File options in the Support Menu the user can customize bank information and control printing of separator pages. The user performs the following acts to generate a PCF from the EIMA system instead of loading a specific PCF from another system 

If the print jobs are large and taking up too much space on the hard drive of the workstations the user may want to divide the jobs into segments.

Occasionally individual statements may be damaged or lost after they have been distributed to customers. After processing images some customers delete the images from the database. Deleting the images makes it impossible to recreate the run or perform restarts to reprint lost or damaged statements. Implementing an archiving procedure allows the user to access copies of the text and images required for statement reprinting.

Image Print provides a reprint utility that can be used to reprint statements which is archived to tape at the end of each Image Print run. Each run also creates an index that is saved to tape or disk depending on the selection in the parameters. The archive records are similar to the records written to the statement output file except that each statement is preceded by a header record simplifying the statement identification.

The reprint capability enables the user to print a single statement or a range of statements from an index tape. To reprint statements the user can reprint to a tape first and then print or can reprint directly to the printer.

To get information about specific activities in the EIMA system there are several types of reports the user can run. Reports can be viewed onscreen or printed. The system uses a report browser in some embodiments. TABLE 4 below provides a description of these reports.

Audit reports allow the user to find out information about user and system activity by a particular service. The example shown in shows a sample Audit Report that has been imported into an Excel spreadsheet.

With reference to the type of report column contains the alpha code that indicates the report type. In this example an A indicates that the record contains an audit related message. The date column shows the date and time that the message was generated by the service. The source column lists the service that generated the message.

In Audit reports the message column contains several fields of data and a comma separates each field. The fields in the Message column vary depending on the service that generated the message and the activity that was logged. The six fields in TABLE 5 are found in most Audit report records.

The Filtered Audit report allows the user to get information about user and system activity by a particular service or services. The user is able to select which services messages are included in the report. Information in the Audit report of one embodiment is listed by date message source and message.

Log reports contain informational error and warning messages that have been generated by specific EIMA system services. In one embodiment log report records are designated with the following alpha codes I Indicates that the message is informational E Indicates an error message W Indicates a warning message. These alpha codes appear at the beginning of each record in a log report. The Message field in a Log report record contains the actual message that the service generated.

The Log report lists informational messages that have been issued by services in the EIMA system . Log report data is organized by date the service that generated the message and the log message.

The Filtered Log report lists informational messages that have been issued by a particular service or services in the EIMA system . The user is able to select which services messages are included in the report. Filtered Log report data is organized by date the service that generated the message and the log message.

The Warnings and Errors Log Report lists error and warning messages that have been issued by various services in the EIMA system . Each record in the Warnings and Errors Log Report contains an entry for the date the service that generated the message and the actual warning or error message.

The Filtered Warnings and Errors Log report lists error and warning messages that have been issued by a particular service or services in the EIMA system . The user is able to select which services messages are included in the report. Each record in the Warnings and Errors Log report contains an entry for the date the service that generated the message and the actual warning or error message.

Records in an Audit report can contain a variety of log type values. The log type value indicates the activity that a service recorded. The log type value is listed as a Message field in Audit report records. TABLE 6 below lists the log type values that can appear in Audit and Log reports.

In an Audit report the fields following a log type value will vary depending on what log value is listed. To help understand the information in the Message column of a particular Audit report record the following topics contain descriptions of the fields that follow a specific log type value. These topics are organized by the type of process associated with a particular log type value Login Logout Capture Value GIA Session Value NetQuery Log Type Values Migration Log Values Set Password Value System Admin Values Store Values Export Values Distribute Log Type Values Text Batch Value.

TABLE 7 below provides a description of the fields that follow the Login or Logout log type value in an Audit report record. These fields appear after the log type value in the Message column. Field values are delimited by commas.

TABLE 8 below provides a description of the fields that follow the Capture log type value in an Audit report record. These fields appear after the log type value in the Message column. Field values are delimited by commas.

TABLE 9 below provides a description of the fields that follow the GIA SESSION log type value in an Audit report record. These fields appear after the log type value in the Message column. Field values are delimited by commas.

TABLE 10 below provides a description of the fields that follow a Query log type value in an Audit report record. These fields appear after the log type value in the Message column. Field values are delimited by commas.

TABLE 11 below provides a description of the fields that follow a Query log type value in an Audit report record. These fields appear after the log type value in the Message column. Field values are delimited by commas. The DISPOSITION log type value indicates query activity based on each item that is tagged and retrieved individually for display.

TABLE 12 below provides a description of the fields that follow the MIGRATION log type value in an Audit report record. Migration field values indicate that items have been migrated to a storage device. These fields appear after the log type value in the Message column. Field values are delimited by commas.

The following fields indicate that verification of migration was performed. Please note that there are two verification log entries one is used for the number of images verified and the other is used for verification error count. The only difference between the two is the use of the Images field.

The DELETION log type value below indicates that a cycle has been deleted after migration and migration verification.

TABLE 15 below provides a description of the fields that follow the SET PASSWORD log type value in an Audit report record. The SET PASSWORD value indicates that a login password change occurred. These fields appear after the log type value in the Message column. Field values are delimited by commas.

TABLE 16 below provides a description of the fields that follow the ADD USER GROUP log type value in an Audit report record. These fields appear after the log type value in the Message column. Field values are delimited by commas.

TABLE 17 below provides a description of the fields that follow the DELETE USER GROUP log type value.

These log type values indicate specific details about document and statement storage in the archive. TABLE 24 below provides a description of the fields that follow the STORE DOCUMENT log type value in an Audit report record. These fields appear after the log type value in the Message column. Field values are delimited by commas.

TABLE 25 below provides a description of the fields that follow the STORE STATEMENT log type value in an Audit report record. These fields appear after the log type value in the Message column. Field values are delimited by commas.

TABLE 26 below provides a description of the fields that follow the EXPORT JOBDESTVOL log type value in an Audit report record. These fields appear after the log type value in the Message column. Field values are delimited by commas.

TABLE 27 below provides a description of the fields that follow the DISTRIBUTE log type value in an Audit report record. These fields appear after the log type value in the Message column. Field values are delimited by commas. The DISTRIBUTE value indicates that an export to a remote printer fax was performed.

TABLE 28 below provides a description of the fields that follow the TEXT BATCH log type value in an Audit report record. The TEXT BATCH log type indicates that a text file batch query job was exported. These fields appear after the log type value in the Message column. Field values are delimited by commas. The DISTRIBUTE value indicates that an export to a remote printer fax was performed.

The Free Items Report lists the images contained in a particular batch of a database cycle that have not been requested by the MCF. The report is sorted by time of capture. To view print or delete a Free Items Report the user performs the following acts 

The Missing Items Report lists any items that are present in the MCF but have no corresponding image in the database. The total number of unmatched records appears at the end of the report. To generate a Missing Items Report the user performs the following acts 

The Cycle Location report lists the current location of database cycles by repository. The report indicates if a cycle is located in one or more of the following repositories 

The user can generate an Optical Jukebox Occupancy report to get information about the data that has been migrated to optical. To generate an Optical Jukebox Occupancy report the Optical Administration server should be running. The Optical Administration server and the Optical Repository server should not be running at the same time. The user should stop the Optical Repository Server and then start the Optical Administration server before running the Optical Jukebox Occupancy report.

Tape Repository Reports allow the user to get specific information about tape devices and data that has been migrated to tape. The following tape reports can be run from the Report menu 

The Tape Repository Occupancy report provides a history of database cycles that have been migrated to tape. This report contains the following information 

The Tape Repository Volume Report shows the amount of available storage space on your tape volumes. This report contains the following information 

The Tape Repository Drive Status report provides status information about tape storage devices. This report contains the following information 

The Tape Administration menu contains options for managing tape volumes that contain Titan cycles which have been migrated from RAID to tape. The Tape Administration menu includes tasks for verify tape drive availability mount and unmount tape volumes add and remove tape volumes to and from the tape silo remove tape volume data place a tape drive online or offline and recover a failed tape drive.

While tape volumes are in the tape silo users can query tape data through the NetQuery program. The tape silo s robotic arm transfers tapes into the tape drives as tape volumes are requested for migration and querying purposes. The number of tapes that can be stored in your tape silo depends on the make and model of the equipment.

The user can view the read write capability of tape drives that are not currently in use by selecting the Check drive status option on the Tape Repository Administration Menu. The Drive Status report lists the following information about each available tape drive 

To generate an onscreen Drive Status report that displays tape drive availability the user performs the following acts 

Tape volumes should be mounted to make them accessible for reading or writing. The Mount option on the Tape Administration menu allows the user to instruct the tape silo to load a specific tape volume into a particular tape drive.

Optical Administration is used to transfer images and related database files to and from optical cartridges stored in a jukebox. This transfer is called migration or most commonly optical migration . The Optical Administration application includes an Optical Migration procedure and Optical Administration procedure.

Optical Administration allows the user to migrate your data from RAID to Optical Optical to RAID Optical to Optical Optical to Tape and Tape to Optical. Optical Administration Procedure allows the user to add and remove cartridges from the jukebox.

Each jukebox has its own Optical Administration database. Each jukebox has an assigned identifier e.g. OR OR OR etc . Each jukebox s optical system uses three servers which are listed below 

The optical system supports two types of optical cartridges reusable Erasable Optical Cartridge and write once read many WORM . The user uses the Erasable Optical Cartridges for data that he does not require permanently. Once the user no longer require that data on a reusable optical cartridge he can erase it and reuse the cartridge. Alternatively the user uses WORM cartridges when he requires a permanent record of the data. A Jukebox Occupancy Report is available to describe the contents of your system jukeboxes.

While Section B describes operating one embodiment of the EIMA system other methods of operation can be used as well. Additionally the sections below describe other applications that are used by other embodiments of the invention.

System Administration is a utility that system administrators can use to control user access and activities in the EIMA system . The administrator must have administrative rights to log on to System Administration.

When a user logs on to the EIMA system the system checks the user s password and capabilities and then grants access to programs based on the user s security level or capabilities. The system administrator is responsible for assigning capabilities to each group. Users cannot log on to the system until the system administrator has added the user account to System Administration.

The administrator can perform the following tasks in System Administration 1 create and manage user accounts 2 create and manage groups 3 assign groups to users 4 set group permissions 5 create filters to control data access 6 define weekends and holidays in the calendar and 7 create decision making windows.

The table below lists the hardware and software requirements of a workstation for one embodiment that calls System Administration.

The first time the administrator logs on to the EIMA Web site the administrator will be prompted to download and install the Java Plug in if it is not already installed on your computer. The Java Plug in is required to run the System Administration applet.

To begin logging on to the EIMA system specifically the host server the administrator enters the address of the EIMA Web site in the Address bar of the Web browser. After the login information has been authenticated the administrator is able to access System Administration and any other EIMA applications for which the administrator has been granted permissions to use. The administrator must have administrator capabilities to use System Administration.

After the user launches System Administration the System Administration Main Screen loads in the Web browser. For the embodiment shown the System Administration screen is divided into two panes the left pane and the right pane . A split bar separates these two panes. Of course other arrangements are possible.

The currently selected option in the left pane controls the content of the right pane . The left pane contains five main menu items. Double clicking a menu item in the left pane expands or collapses the options under the menu item. The following main menu items are available in the left pane 

The right pane displays the tab or tabs for the selected option in the left pane. Clicking a menu item option changes the content of the right pane .

The split bar is the horizontal line that separates the left pane and the right pane . The administrator can adjust the size of the right and left panes by clicking and dragging the split bar to the right or left.

In one embodiment System Administration is a Web based Java applet that is embedded in HTML although other architectures can be used as well. The System Administration applet runs in a Web browser and is part of the EIMA system Web page. To run System Administration the Java Plug in should be installed on the client workstation .

The administrator can view user accounts and their descriptions in the Users List. The User Name column contains the account name the Description column provides more details about the account.

A user is an individual who can log on to the EIMA Web site and perform specified activities in EIMA applications. Users with similar access rights are usually members of the same group however a user may belong to more than one group. Group membership designates the activities that a user can perform in the EIMA system.

The administrator can begin to add a new user by clicking the Add User option under User Admin in the left navigation pane. The administrator supplies the following information for each new user account 1 name of the account 2 description 3 password and 4 group assignment. To assign a group to a user the administrator should have already added the group to System Administration.

The administrator can print a report that lists all the users and groups in the EIMA system . The first part of the report contains a list of current users the second part of the report lists group information. The following data is included in the report user name and description group names and password and account status of each group.

The administrator can permanently delete a user account using System Administration. Deleting a user account prevents the user from logging on to the EIMA system. User accounts are deleted in the Users card.

There are two ways to change a user s password. As the system administrator she can change a user s password from the Users card. Users also can change their own passwords.

The User Information card is where user account information is entered and modified. The User Information card is comprised of the User and Group cards. The following table contains a description of the fields and options in the User card 

The Groups card is where the administrator assigns or unassigns a group or groups to a user account. The following table contains a description of the Groups card s fields and options 

A group is a collection of users with common capabilities and limitations. Groups allow the administrator to control user access and activity in the EIMA system . The Group Admin menu is located in the left pane and contains options for creating and managing groups. In one embodiment the administrator can double click Group Admin option to expand or collapse its options.

A capability restricts or permits the activities that members of a group can perform in the EIMA system . Capabilities also control what applications a user can access. Capabilities are assigned at the group level.

There are several predefined capabilities available in the Capabilities card of the Group Information tabbed pane . Capabilities are assigned when the administrator creates or modifies a group.

The following table defines each of the predefined capabilities listed in the Capabilities card of the Group Information tabbed pane.

The administrator can delete a group from the EIMA system. The administrator performs the following steps to remove a group 

The Group Information card is where group account information is entered and modified. The Group Information card contains the following cards Group card Users card Documents card Databases card and Capabilities card.

The Group Control card is where the operator enters or views the name description and available query dates for a group account. The Group Control card is located in the Group Information card. The following table contains a description of the Group Control card s fields and options 

The Users card is where the administrator assigns users to and remove users from a group and is located in the Group Information card. The following table contains a description of the Users card s fields and options 

The Documents card is where the administrator assigns a document type to or remove a document type from a group. The Documents card is located in the Group Information card. The following table contains a description of the Documents card s fields and options 

The Databases card is where the administrator assigns a database to or remove a database from a group. The Databases card is located in the Group Information card. The following table contains a description of the Databases card s fields and options 

The Capabilities card is where the administrator assigns capabilities to or remove capabilities from a group. The Capabilities card is located in the Group Information panel. The following table contains a description of the Capabilities card s fields and options 

A query filter selectively screens a group of users from querying specific data in a database cycle. The administrator can use query filters to limit a group s ability to retrieve and view only items that meet the conditions of the filter. Query filters are assigned at the group and document type levels. The administrator can use query filters when it is appropriate to limit user access to just a portion of the document items in a database.

For example the administrator may not want a user group to be able to view all document items in a check cycle. To prevent the user group from querying and retrieving every document in the cycle the administrator can create a query filter that limits the group to retrieving only document items within a range of routing numbers. This filter will be applied to each database that is assigned to the user group and contains the same document type.

Query filter conditions define the query restrictions of a filter. A condition places a restriction that limits the values users can retrieve from a query field. A condition can be as simple as restricting a group from querying a range of account numbers or as complex as restricting a group from querying specific values in several query fields. The administrator can place several conditions in the same query filter.

Conditions are entered in the Filter Conditions card. Prior to setting query filter conditions the operator should select the following items the range of document items that you want to prevent the group from retrieving the range of document items that you want the group to be able to retrieve the query fields that will be affected by the conditions and how the conditions will be constructed in the Filter Conditions grid. The administrator can use both comparison and logical operators to set field conditions. An operator is text that specifies what operation can be performed on the elements in a condition.

By using comparison and logical operators in query filter conditions the administrator can restrict users from retrieving records that contain a particular query field value. Comparison and logical operators can be added to a query filter condition in the Filter Conditions grid.

A comparison operator compares two values and then returns an answer that is based on the result of the comparison. Comparison operators are available in the first column of the Filter Conditions table. Clicking a cell in this column opens a drop down list of the following logical operators 

A logical operator tests if a particular argument is true or false and then performs an action based on the result. Logical operators are available in the Operators column in the Filter Conditions table. The administrator uses the following logical operators in a filter condition 

The administrator can view a list of existing query filters in the Query Filters card. The administrator performs the following acts to display the query filters list 

The administrator can view existing query filters in the Filter Information card . The Filter Information card contains the Query Filters and Filter Conditions tabs. The Query Filter tab contains the following information name and description of the query filter and group and document type assignment.

The Filter Conditions tab contains the condition of the query filter. The administrator performs the following acts to view the settings for an existing query filter.

The administrator can create a query filter to limit members of a group from querying and viewing certain documents. Query filters are added from the Query Filter List card. The administrator can set multiple conditions in the same query filter. The administrator performs the following acts to create a query filter 

The administrator can change the definition of a query filter. The following query filter settings can be modified description group document type and conditions.

The Query Filter Information card is where query filter information and conditions are entered and modified. The Query Filter Information card includes the Query Filter and Filter Condition cards.

The Query Filter card is where the administrator enters query filter settings. The following table contains a description of the fields in the Query Field card 

 iii Overview of the Filter Conditions Card After setting up the name description group and document type for a query filter the administrator can define the filter s conditions. Filter conditions allow the administrator to restrict the document items that a group can query and view. Filter conditions are entered in the Filter Conditions grid.

A condition limits the values users can retrieve from a query field by specifying criteria on a particular query field in a table. Conditions are applied to any databases that are assigned to the selected group and contain the selected document type and query field.

The decision calendar is an electronic calendar that is used to schedule a company s decision making and non decision making days in the EIMA system. The calendar works with decision windows to control when users can make decisions on positive pay products in the NetQuery program.

Decision windows rely on the electronic calendar s settings to determine decision and non decision making days. The administrator defines the company s calendar year on the electronic decision calendar before creating a decision window.

The administrator does not need to set the decision calendar if an institution is not using NetQuery s positive pay module.

On the Decision Control Calendar each square block e.g. square designates a day of the month. Calendar days are highlighted white green blue or red. Of course other colors or indicators can be used. The color of a square indicates whether the day is a business day holiday Saturday or Sunday. The legend to the right of the calendar identifies what each color represents. In the embodiment described herein the Table below defines each color.

By default the following days are scheduled as decision making days on the calendar Monday Tuesday Wednesday Thursday and Friday. The administrator can change the status of a day by activating its square on the calendar. Changes are applied to the current month by clicking the Modify Current Month Definition button . The administrator can reverse edits by clicking the Reset Calendar button .

By default users are unable to make decisions on Saturdays Sundays and holidays. To allow users to make decisions on Saturdays Sundays or holidays the administrator should change the day s color to white.

A decision window defines the time frame that a group can make pay or no pay decisions on exception items in the NetQuery program. Decision windows allow the administrator to control the exact dates and times that a group can make decisions on positive pay items.

When the administrator creates a decision window he will need to provide the following information name and description of the decision window group and document type assignment conditions of the window start and end times and possible override conditions.

The administrator can view existing decision windows in the Decision Window List . The following information is shown the name of the decision window description and the assigned document type and group. The administrator performs the following acts to display all decision windows 

A window condition sets the duration of a decision window by defining the window s start and end times. The administrator enters window conditions in the Window Conditions card.

The administrator enters the number of days from today s date forward on which the administrator wants the decision window to go into effect. Entering 0 applies the decision window immediately today . Weekends and holidays are not counted toward the start delay time.

The start time determines the time that users can begin to make decisions on exception items in NetQuery. The administrator enters the exact time that he wants the decision window to be applied and then selects AM or PM from the drop down list to the right of the field.

The Days Open and Time Open text boxes work together to calculate the duration of a decision window. In the Days Open text box the administrator enters the total number of days that he wants the decision window to last.

If the administrator wants to extend the length of a decision window by a few or several hours he enters the number of hours in the Time Open text box. This entry is based on a 24 hour clock.

This text box defaults to the current date. This value is used to calculate the start date of the decision window in the Translation of Decision Window text box.

This text box is for viewing purposes. After entering values in the Window Condition section the administrator has the option of clicking the Go button to display a summary of his decision window settings in the Translation of Decision Window text box. If there is an error in the summary he can make the appropriate corrections.

The administrator can override or supersede the conditions of a decision window by entering an exception time in the Override Condition section of the Window Conditions card. An override condition extends the decision making time frame of a decision window.

The following paragraphs define the fields in the Override Condition section of the Window Conditions card.

The administrator enters the date that he wants to be used to calculate the start date for the override.

The administrator enters the number of days forward from the date displayed in the Date text box on which you want the override to go into effect.

The start time determines the time that the override condition begins. The administrator enters the exact time that he wants the override to be applied to the decision window and then select AM or PM from the drop down list to the right of the field.

The Days Open and Time Open text boxes work together to calculate the duration of the override condition. In the Days Open text box the administrator enters the total number of days that he wants the override condition to last.

If the administrator wants to extend the length of an override condition by a few or several hours he enters the number of hours in the Time Open text box.

The administrator can begin to create a decision window by clicking the Add Decision Window option under Decision Window Admin in the left pane. The administrator should supply the following information for the decision window name and description group and document type assignment window permissions start date and duration of the window and possible override conditions.

The administrator can make exceptions to the duration of a decision window by entering override conditions in the Override Condition section of the Window Conditions card. The administrator should have already created or started creating a decision window. The Window Conditions card should be open. In the Override Condition section the administrator performs the following acts to add override conditions to a decision window 

The administrator can edit the definition of an existing decision window. To begin editing a decision window the administrator double clicks the decision window row in the Decision Window List or clicks the decision window row and then click the Modify Decision Window button .

The Decision Window Information card is where decision window information and conditions are entered and modified. The Decision Window Information card is comprised of the Decision Window and Window Conditions cards.

The Decision Window card is where the administrator enters or views the name description and other settings for a decision window. The Decision Window card is located in the Decision Window Information card. The following table contains a description of the fields and options in the Decision Window card 

The Window Conditions card is where the administrator enters criteria settings for a decision window and is located in the Decision Window Information card. The following table explains the fields and options in the Window Conditions card of the Window Conditions section 

The functions of the Repair GUI are similar to the MICR Repair and Quality Monitor modules in that Repair GUI helps control the quality of the Image Capture process by allowing the user to view images as well as correct MICR field data. The Repair GUI may also be customized to meet specific needs.

The Repair GUI has two operating modes Repair mode and Monitor mode. When the user logs into the Repair GUI the user chooses whether to use its monitor or repair capabilities. The user enters the Repair mode to correct any scanning errors that corrupted MICR data. The user may also use it after the image matching Image Match process to correct free items. The fields that appear in the Repair GUI are defined by a system administrator.

During Image Capture the user can enter Monitor mode to display samples of the images as they are scanned. If the user spots scanning errors the scanner can be adjusted enabling immediate correction.

In general UNIX menus refer to databases and cycles while some PC applications including Repair GUI refer to set names and set dates. In general the following terms are defined as below.

Repair mode is used for correcting any scanning errors detected by Image Capture or Image Match. The corrections are made to the database index which is where the data is stored. The database index contains the image location MICR data and any other data associated with the image. Repair is usually performed any time after Image Capture has detected faulty data or to correct free items remaining after Image Match.

During Image Capture the scanner scans the items documents such as checks and reads the MICR data. MICR data is the record of field values for a number of variables printed in magnetic ink in specific locations on the original document. Field values may include account numbers check numbers and related data depending on specifics of the documents recorded and the customer requirements. The scanned digital images and associated MICR data are sent to the UNIX host where Image Capture stores the images in an image database and records the image location and associated field value data in the database index.

Image Capture passes the data through a series of validations. Validation fails if there is one or more unreadable characters a missing field or the number of characters is incorrect. The data may fail validation because the scanner did not read it correctly. Situations that may result in unreadable data include a document is fed at an angle into the camera area labels are incorrectly placed or the image has marks or scratches across the MICR data area.

If any of these situations should occur it becomes necessary to fix the data contained in the database index file. The index is flagged for each image that has a detected problem.

During repair each index item needing repair is displayed on the workstation one at a time. The operator enters the missing or corrected data. The scanned images themselves are not changed. Instead the data stored in the database index is corrected.

Before starting a Repair GUI session on the workstation the user should first start the repair server. Starting the repair server was discussed earlier. After the user is finished with the Repair GUI session the user kills i.e. stops the repair server.

The Repair GUI Repair mode can be used anytime after Image Capture identifies an item with duplicate or unreadable data. If the user needs to enter data for an empty field or to edit other data that the system has not tagged as needing repair he creates a Repair Set while in Monitor mode. From the workstation the user initiates Repair by performing the acts below 

The Repair GUI main screen contains the image s and the image s respective associated field data. The user can cycle through the images and change field data by use of various image controls. The screen includes two image windows. The image displayed in the first window defaults to the object s front view. The image displayed in the second image window defaults to the back view. The user can force the image back view to appear in the first window by selecting Options Swap Image. The user may also specify a third image window.

The user can also enlarge and shrink the image windows and arrange them as desired by clicking and pulling on the window s borders. Further the user can also click and drag the mouse to zoom in on a specific rectangular section of an image.

The user can browse through the images and further manipulate them by clicking on image manipulation buttons. The following table explains the navigational functions of the various buttons in the image windows 

Repair GUI contains two separate types of keyboard shortcuts Old Style Shortcuts and Stored Field Values shortcuts. Old Style Shortcuts are shortcuts that are set by the software. Stored Field Value shortcuts are created by the user.

Stored Field Value shortcuts are useful if the user uses certain fields that consistently contain the same values. Simple keystroke shortcuts allow the user to enter the field values he sets for each keyboard shortcut. For the embodiment described herein the shortcuts involves pressing the key and a single digit number. For instance the user can define a stored field value so that when he hits 1 the field is filled with the pre set Value.

After the user selects the repair set he can resize the image by dragging the borders of the window. The user can also resize the Fields window so that the fields are more visible.

For each image the user examines the field data in the information line and edit that data as needed. The user may define special characters that appear in place of unclear and missing characters using the parameters file that is associated with each database. For instance the user might use an to appear in place of unclear characters and an M in place of missing characters.

The user clicks the Update button to save changes and move to the next item. If the user is uncertain whether the item needs updating the user can click Skip to move the current item to the end of the file. If an item does NOT need updating the user clicks Update without making changes so the item does not reappear.

If certain fields have been defined as Mandatory the user will not be able to proceed if a Mandatory field contains no data. If the user clicks Update the user will receive a warning message. e.g. This operation will permanently remove this item. Continue You will be unable to proceed to the next item until you select either es or o. 

The Fields window s title bar lists the errors contained in the current batch. When the user clicks the Update button this number decreases.

When there is no longer a number in the title bar of the Fields window the current batch has been totally repaired. Additionally no images will appear on screen.

To delete the current image along with its accompanying data the user clicks the Delete button. Since this will permanently delete the item from the database a confirmation request message appears. The item is removed from the database when the user confirms the request.

Within repair GUI the user has options to customize the application. These are available from the Options menu. These options are available for both Repair and Monitor modes. The following is a list of available options 

For the embodiment described herein these preferences are automatically saved to the registry so that next time you run the application they will be loaded.

Repair GUI s Monitor mode is used in conjunction with the UNIX based Image Capture program to monitor the documents scanned into database files. This option helps to ensure the accuracy of the data. The user can compare the data recorded from the scanning operation to the data on the associated image. By doing spot checks the user can detect scanning errors or burned out scanner light bulbs and reset the scanner if necessary.

There are two ways to use the monitor capability while the items are being scanned and after items have been scanned into a database. The Repair GUI should not be started until after capture has begun. This is because the capture process creates the Batch ID that the Repair GUI needs in order to retrieve the images.

The Monitor mode timer can be set to display a new scanned image at intervals integer seconds controlled by the user. To set the timer the user should already have selected a SetName SetDate and Batch repair set. If the timer is set when the scanner is not running then the same image will be refreshed over and over as long as the button remains active.

The process is the same as for reviewing scanning images Initiating Image Capture except there is no need to start the scanner. Additionally there is no need to set the timer since all the images have already been scanned. The user can use the navigation buttons to view the images.

In one embodiment the Field portion of the screen is greyed out when in Monitor mode instead of having a white background as during Repair mode . This is to prevent the user from editing fields in Monitor Mode. Instead the user is simply viewing the images and their associated data. If there is a need to edit field data the user uses the Repair mode.

For the system described herein there are two methods available for updating field data Batch Update discussed earlier and Repair GUI. Repair GUI allows the user to create repair sets. Repair sets let the user mark a subset of items in a cycle for repair. The user creates the repair sets while in Monitor mode but the repair sets the user creates are accessed and modified in Repair mode.

The repair set process works in much the same way as a query filter. The user may want to repair only images that have amounts between 100 and 500 for instance or to repair images that have only a particular serial number or series of serial numbers . If an item in a cycle fits the criteria defined for the repair set it is tagged as having an error. The user can delete the repair set later and subsequently un tag the items.

If the user selects equal to or not equal to a Range check box will appear for specifying a range of values. To specify a range for the field click the Range check box. The window is then enhanced with a pair of data entry windows so the user can enter the minimum and maximum values in the spaces provided. For convenience in the window space below the range values the Amount window will display any previously entered ranges from which the user may select.

For example if the user needs to create a repair set that includes all capture dates between Jan. 1 and Jan. 15 2000. In this example the user selects the Operator equals and clicks the Range check box that appears. When the user clicks the Range box two unlabeled data entry windows will also appear. In the left data entry window the user enters 0000000020000101 year 2000 1month 1day . In the right data entry window the user enters 0000000020000115 year 2000 1month 15day .

The Class Groups option enables the user to define the fields that appear for each document or image class in the system.

Each user that is allowed to perform repairs must be assigned permission to do so through the use of class groups. The system administrator defines class group fields that certain user groups may view via the assigned class groups. The user can add and delete class groups. Inadequate class groups cannot be modified only deleted and recreated added .

Reconciliation provides for manual batch reconciliation of Free Items and matching Missing Items into the archive.

Free Items are images scanned during the capture process that the system is unable to match with any item from the Match Control File MCF . The client site provides MCFs. The MCF is used to enable the system to link images and Magnetic Ink Character Recognition MICR data read from the images to the respective object s data that is stored in the MCF. The MCF theoretically should contain the correct information for every object captured.

Missing items are those items identified in the client supplied Match Control File MCF that do not have identified object images and MICR data with which they can be matched. This usually occurs because the images captured have faulty MICR fields that the system could not read or the matching image objects were not scanned in.

In one embodiment reconciliation runs on the client using Java Runtime Environment JRE Java Advanced Imaging JAI and CORBA. Other environments are possible.

Reconciliation displays each Free Item along with the most likely missing items from the Match Control File MCF for that batch. When a user chooses and confirms the Match Control File row that is appropriate for a free item the data for the Free Item is modified to equal that Match Control File data. The application then marks that image as Matched and that image is immediately available for querying and other archive functions such as export and statement print. In order for the Missing Item Report Free Item Report and Match Statistics to be updated the user must also select the Update Match Reports option from the UNIX Match Menu.

The Batch Selection window provides access to three levels of nested folders. This is a hierarchical window where the user can expand and contract the tree structure. A Database Icon contains one or more Cycle Icons each of which contains one or more Batch Icons.

The user double clicks a Database Icon to display its available cycles. The user double clicks a Cycle Icon to display its available batches. The user double clicks a Batch Icon to reconcile that batch.

The information in parenthesis located to the right of the batch ID number 0000 in the example in indicates the number of free items and missing items contained in that batch.

Clicking one of the arrows results in extreme movement of the image border in the direction of the arrow clicked. For example if in the image above the user clicks the window adjustment arrow that points to the right the border will move to the right edge of the application window enlarging the front view of the check while the back of the check will be hidden. To view only the back of the check the user would click the left pointing arrow.

Matching deleting skipping options and other controls are available through a right click menu. Right click anywhere on the screen to access this menu.

An Options Dialog window is accessed by either right clicking on the View Image window. The Options Dialog window is made up of three tabs that allows the user to adjust the following qualities 

The user then clicks the OK button when the font Height Width and Magnification Factor is properly set. The Options Dialog window closes and the magnifying glass now uses the height width and magnification chosen.

NetQuery is a Web based program that allows a user to query and view document information and images in a Web browser such as Internet Explorer or Netscape Navigator. The client side of the application uses Java Applets that is embedded in HTML. By entering the address of the EIMA system Web site in the Address bar of the Web browser the user is able to log on to the Web site and then start NetQuery.

There are three main screens that make up the NetQuery applet Query screen Result screen and Image screen. Queries are created in the Query screen query results are displayed in the Result screen and query documents are displayed in the Image screen.

Table 70 lists the hardware and software requirements for one embodiment of a workstation utilizing NetQuery.

The operator should log on to the EIMA system Web page before launching NetQuery. After the operator s login information has been authenticated the operator has access to NetQuery and other programs that they have permission to use.

To run NetQuery the Java Plug in should be installed at the client. The Java Plug in is part of the Java 2 Runtime Environment Standard Edition download. The Java Plug in is an accessory program that allows the client to run Java applets and JavaBeans components in Internet Explorer or Netscape Navigator.

A query is a request for document items in a particular database cycle. Queries are defined and executed from the Query screen. To retrieve specific document records the user must set criteria for the query. Criteria is a set of limiting conditions that retrieves a specific set of records. The user can construct a simple or advanced query in the Query screen. A simple query allows the user to search for documents using a comparison operator. An advanced query allows the user to search for documents using both comparison and logical operators. The user can also set criteria on the same field multiple times. When the user executes a query the query request is sent to the server. The server searches for records in the specified database s and then returns only those records that meet the criteria. Query results are displayed in the Results screen.

By default the Query screen does not contain any information. The user creates the query by performing the following acts 

The Query screen opens after the user launches NetQuery from the main menu . The user creates saves opens and executes queries from the Query screen. In this screen the user can also print a copy of the current settings access help about the program and navigate to other query sets.

The upper portion of the Query screen is where the user selects the document type database and date range for a query. The lower portion of the Query screen contains the Query Definition Grid . Of course different arrangements are possible.

The Query Definition Grid is where the user establishes search criteria for a query. For the embodiment shown the grid is located below the From Date and To Date text boxes in the Query screen. Each row in the Query Definition Grid contains a query field where the user can set up your search criteria. The Query Definition Grid contains the following columns 

When the Query screen is in Advanced mode an Op column appears in the Query Definition Grid. The Op column contains a drop down list of logical operators.

The user can set criteria on any field in the Query Definition Grid. Search criteria is set by selecting a comparison operator from the Op or Operators columns and then typing a search value in the Value1 and Value2 fields.

The user selects a comparison operator in the Query Definition Grid . A comparison operator compares two values and then returns a query result that is based on the outcome of the comparison. The following operators are available from the Operators column in the Query Definition Grid 

The operator can switch the Query screen between Simple mode and Advanced mode. Simple mode is used to create basic queries and is the Query screen s default setting. Advanced mode is used to create complex queries that contain logical statements.

The user can query several databases at the same time. In one embodiment only databases that contain the currently selected document type are displayed in the Available Databases list box.

Once the user has defined a query in the Query screen the user can save the query settings to a file. Saving a query to a file enables the user to reuse the query definition in future queries.

The user can delete existing queries that have been saved under a group of which he is a member. Queries are deleted from an Open Query Definition dialog box.

The user can open an existing query file and then execute or modify the query as needed. Query file availability is based on group membership.

The user can print a copy of the current settings in the Query screen. In one embodiment the following fields are printed name of the query file query mode advanced or simple document type selected query databases and the query s date range.

The user can adjust the print setup including the orientation e.g. print images in portrait or landscape set the margins set the resolution and set the text properties font size etc. .

An advanced query is a request that contains one or more logical operators in its search criteria. The user can set search criteria on the same field multiple times in an advanced query. When the Query screen is set to Advanced mode the Op column is available in the Query Definition Grid. Clicking a cell in the Op column opens a drop down list of logical operators.

A query set is inclusive of the Query Result and Image screens and contains the following information query definition result set and image set. The user can have multiple query sets open in the same session. With reference to the Query Set text box displays the number of the open query set as well as the total number of query sets. The navigational buttons to the right and left of the Query Set text box allows the user to move between query sets. The Query Set text box and navigational buttons are located in the Query Result and Image screens. For example if there are three query sets open and the second query set is active the Query Set text box displays 2 of 3. 

Query results are the matching document records returned by a query. When the user executes a query any records that match the search criteria of the query are displayed in the Result screen . In the Result screen query results are organized into rows. The column labels at the top of each column identify the column data. Each row represents a record in the query results set and each row contains field data.

The user can perform the following actions on query results tag items for viewing and print tagged items. The Tag column is used to select an item for viewing or printing. Query results are not returned in the following situations there is no database selected the user does not have permissions to query items in the selected date range or there are no items that match the search criteria.

The user can perform the following tasks in the Results screen view items in the results set tag items sort the results set retrieve item images navigate between query results sets and print items.

The user can right click on the results grid to display the Results Screen menu . The menu has the following options 

After a query is executed matching items are displayed in the Result screen. To view images the user should tag any items that he wants to view. To tag an item click in the checkbox next to the item. Tagging an item places a checkmark in the Tag column. After items have been tagged the user is ready to submit an image query. An image query retrieves the documents for all tagged items and displays the images in the Image screen. The user should execute a query and receive query results before retrieving images.

The user can change how items in the results set are sorted. The sort feature allows the user to organize items by a particular field or fields. A field can be sorted in ascending or descending order. Clicking the Sort button opens the Sort Result dialog box where sort fields are selected. The user can sort using one or more fields e.g. sort using a first field and then sort using a second field . Different sort fields include but is not limited to Transit Routing Account Master Account Serial Transaction Code Amount Posting Date DIN Exception Code and Decision Type.

For printing or viewing purposes the user may want to change the order of columns in the Results screen. The user can rearrange columns by clicking and dragging a column label to a new position in the results list.

The user can print a list of the currently tagged items and or the items themselves. In one embodiment the fields that print under the image are defined in a Sybase table user settings.

A Print Setup window can be used to control the format of the hard copy. The window shown includes an orientation section a text properties section a logo section a margins section a print quality section and an options section .

Additionally field information can print under each image. The number of image info lines parameter defined in user settings tells the system how many fields to print fax under check images. If this parameter is not defined in user settings then the default is 3. The fields the user chooses to be printed must be a subset of the items selected for the results list.

The navigational buttons at the top of the Result screen allow the user to move through the pages of query results for one query set. The navigational buttons at the lower left corner of the Result screen allows the user to switch between query sets. Clicking one of these buttons displays the results of the selected query set. Of course other locations for the buttons is possible.

The Image screen displays document images for any items the user has tagged. This screen opens after the user submits an image query from the Result screen .

The user can perform the following tasks in the Image screen adjust image magnification rotate images on the screen invert or reverse image colors print images to a local network printer or a remote printer on the UNIX system view document information access help about NetQuery and navigate between query sets.

The user can view document information for images in the Image screen . The document information window contains the field data for the current image and is displayed in a separate window at the lower end of the Image screen . The Document Information window contains two rows The first row consists of field labels the second row contains the corresponding field values for the image.

The navigational buttons at the top of the Image screen allow the user to move between and display images in a query set. The Next Item button displays the next image in the query set. The Previous Item button displays the previous image in the query set. The Last Item button displays the last image in the query set. The First Item button displays the first image in the query set.

Most items or images are comprised of more than one view. For example a check is made up of both a front view and a back view. Each view of an image is displayed on a separate page in the Image screen. The Next button displays the next view of the image. The Previous button returns to the previous view of the image.

Support adds the capability to NetQuery to manage pay no pay pay amounts and other factors for documents with fields that trigger the capture program s Exception Code generator. Decision Support allows the user to access items with an Exception Code greater than zero and change pay no pay decisions. The user can then update the database using this changed information.

Index fields added to NetQuery to accommodate Decision Support include Exception Codes Decision Type Codes New Pay Amount and New Serial. These index fields are editable with Decision Support turned on and in Image mode where the user can see the document and the database information at the same time.

If an item matches any qualifiers the item has an Exception Code of 1 or greater. Items that do not match any of the qualifiers have an Exception Code of 0. The user s policy may be that items will only be reviewed for payment decisions if the items match one of your qualifiers such as high dollar amount stale payment date invalid signature and or endorsement missing.

Decision Support provides a set of Decision Type codes to accommodate pay no pay decisions. The number of codes can be expanded to provide for each institution s particular needs. Decision Type code values are available for editing when Decision Support is active and the Image screen is displayed.

Standard check related Decision Type codes are pay post dated stale dated pay w new account pay w new serial pay w new amount stop payment endorsement irregular signature irregular check altered and amounts differ. The user may have additional or different Decision Type codes available.

If required the user can distribute the changed information by print or fax. The user can distribute the changed information by tagging desired items in the Results screen and clicking the Remote Print Fax button.

Manual Update allows simple manual adjustments to document MICR data. When the user makes manual changes and then clicks the Go button the database is updated with the changes the user has made.

By right clicking the Query screen Image screen or the Result screen the user can access the Grid Configuration panel. The Grid Configuration panel allows the user to set the display factors discussed below for the specific display screen.

Clicking the Go button applies all your changes and saves all the parameters. When the font is changed the width of all the columns is recalculated to be able to display the information. The only grid that may not be adjusted optimally is the Query Definition grid. This is because the grid is not allowed to grow beyond the bounds of the applet. All other grids are contained in a scroll pane and are allowed to grow past the edge of the applet.

In another application the object checks are encoded with a secured seal that contains specific information e.g. check value payee date check number branch name MICR information etc. about a check. When the check is presented at the bank for payment the scanner includes an application that deciphers the secured seal to allow for verification that the check was properly issued and has not been altered. An example application for obtaining information from a seal or watermark is offered by Signum Technologies. In one specific embodiment data is encoded and printed as a seal watermark diagram picture illustration stamp figure or similar item collectively referred to as a seal . Upon scanning the image the application enlarges the seal and obtains the encoded data using a key. The application then decodes the obtained data.

In one embodiment the obtained from the seal is imported into the host server as an XML file along with the associated check image. A character recognition engine processes the check image by recognizing the payee and CAR amount of the check. The recognized results are then validated against the seal along with other check data passed by the scanner. The results are viewed via a document query application e.g. NetQuery and displayed in a standard report. Another embodiment is schematically shown in .

The import utility service captures the document data and images into the EIMA system for the recognition process. The import service essentially locates the document image files from the network accessible directory places the document image files in a specified location for recognition and inserts the corresponding document data into the database for processing. In one embodiment the document data that is inserted into the database for processing contains the following information 

Once the import process is initialized the application is in an In Process mode and the screen displays the XML filename date and time of the import process and the number of documents that are being imported to EIMA system . To stop the import process or clear the display the user clicks the stop or clear list buttons or . When all the files have been imported to the database the application continues to check the source directory and imports documents that are available from that directory. This window can be minimized so the import process application runs in the background.

An invalid form id error occurs when the form id in the XML file does not correspond to the form id defined in the application. When this happens an error message is displayed. The user has the option to continue with the import process or stop the process. Selecting the former resumes the import process and the next document in the XML file is selected for processing. Selecting the latter stops the import process.

An image file error occurs when the image file Tiff image and associated XML data does not exist in the directory. When this happens an error message is displayed. The user has the option to continue with the import process or stop the process. Selecting the former resumes the import process and the next document in the XML file is selected for processing. Selecting the latter stops the import process.

Network failures performance or licensing issues are some incidents that can cause a database transaction error to occur. When this happens the import application raises the specific error and the import process is halted. The user should fix the error before resuming the process.

The Recognition application processes the document images that are ready for recognition. In one embodiment the application processes the images on a FIFO First In First Out basis. FIFO is determined by the order of the documents imported into the host system . Character recognition is performed on the specified zones on a document and the necessary data is updated in the database.

The document query application displays images and data for specific documents that have passed or failed the data validation process. Document records that have gone through the recognition process are marked as either pass or fail depending on the validation of the recognized and actual data values from the seal. Each specific document whether it passes or fails can be viewed in the document query application for a limited period of time e.g. 15 days prior to the current date .

Each toolbar on the Query Viewer screen is associated with a hot key of the user keyboard. The user uses the hot key to review the document. Of course other keys or other methods can be used to perform the specialized tasks below.

The Error Viewer application contains document record s resulting from a recognition error. A recognition error occurs when an image that is corrupted or does not exist in the directory is introduced in the host system . When this happens the document record is flagged and routed to the error viewer application. The user cannot make any corrections or modifications to the document data but can only save or mark the document record for deletion.

The maintenance application provides the system administrator the capability to add and update the user profile information as well as view the list of active and inactive users. A user can also generate reports from the maintenance application. The reports display the results of the document data that have gone through recognition and subsequent validation in the Atlantis system. There are three basic reports that can be generated from the application.

Only the system administrator has the capability to add new users to the system. From the user maintenance window the user selects the new button . The user details window is displayed. The administrator can then enter the user s first and last name assign a username and password and Designate the level and status of the user.

To update current users the user selects a user and clicks the details button from the user maintenance window. The user can then update the profile information.

From the maintenance window the user can click on the reports button to create a report. The reports window is displayed to the user. The user can then select a report. In one embodiment an Excel file is generated from the list of reports. The user can also save the report to a directory. An example report is shown in . The following items can be indicated in some reports.

The Database Maintenance Plan application is used to help an institution set up the core maintenance tasks that are necessary to ensure that their database performs well is regularly backed up in case of system failure and is checked for inconsistencies. The Database Maintenance Plan application creates a Server job that performs these maintenance tasks automatically at scheduled intervals.

The results generated by the maintenance tasks can be written as a report to a text file HTML file or even e mailed to an administrator. One or more of the tasks performed by the Database Maintenance Plan application are discussed above in connection with other applications. However the Database Maintenance Plan application provides an administrator with a single tool to coordinate all of the tasks.

As can be seen from the above the invention provides a new nonobvious and useful electronic item management and archival system and method of operating the same. Various features and advantages of the invention are set forth in the following claims.

