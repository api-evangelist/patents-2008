---

title: Printing apparatus and method of controlling printing
abstract: A printing apparatus is configured to perform printing in accordance with a print job and in accordance with a schedule registered before the printing. The printing apparatus includes an authority setting unit configured to, if authority of a user for the print job is authorized, set the authority of the user for the print job; a determination unit configured to, if a command to handle the print job is issued by the user, determine whether the user has the authority to perform the handling based on the authority set by the authority setting unit; and an execution unit configured to, if the determination unit determines that the user has the authority, execute a process according to the handling on the print job.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08477341&OS=08477341&RS=08477341
owner: Canon Kabushiki Kaisha
number: 08477341
owner_city: Tokyo
owner_country: JP
publication_date: 20080725
---
The present invention relates to a printing apparatus and a method of controlling printing and more particularly to a printing apparatus and a method of controlling printing which are advantageous in particular in handling a print job.

Japanese Patent Laid Open No. 2002 202945 discloses a technique in which when a print job is handled i.e. when the print job is controlled in terms of deleting advancing of priority interrupting etc. the handling is permitted or is not permitted in accordance with authority granted to a user for the print job of interest. Note that the term handle is used throughout the present description to express controlling a print job in terms of deleting advancing of priority interrupting and the like. In this technique an access ticket included in a print job input to a device via a network or a console is compared with an access ticket of a user who wants to handle the print job and whether the handling of the print job is permitted or not is controlled according to a result of the comparison.

Japanese Patent Laid Open No. 2002 36631 disclosed a technique to surely delete a print job. In this technique if a request for deleting a print job is issued by an application at a stage where the print job has not yet produced by a print device a printing system is set such that the printing device will delete the print job. In this case when the print job is produced the print device deletes the print job. This makes it possible to surely delete the print job.

In a conventional printing system when a print job is transmitted to a print device via a network and the print job is printed by the print device there can be a problem in terms of preventing a leak of secret information if an output material a printed material is left without being taken. In this respect there is a need for a printing system that ensures that an output material is taken by a user who performs printing. One of such printing systems is that called a pull print system. In the pull print system a client is only allowed to upload a print job and issuing of a print command is performed on a print device. Thus this technique is expected to be capable of suppressing the probability that an output material is left without being taken by a user.

However when the printing operation is controlled in the pull print system according to the technique disclosed in Japanese Patent Laid Open No. 2002 202945 the following problems can occur. For example when a command to delete a print job is issued it is necessary to send the delete command via the same path as a path via which a print command was sent. However in a large scale server system as in the case in a typical pull print system the system includes a plurality of servers and is formed in a cluster configuration to distribute loads among the servers. In this configuration it is difficult to send the command to delete a print job via the same path as the path of the print command.

In a case of conventional printing push printing the same apparatus is used to produce a print job and handle the print job. Therefore it is possible to immediately capture a print job and handle it. In contrast in the pull print system a print job is handled by a device different from a server that produces the print job. Therefore it takes a long time to capture the print job i.e. it takes a long time for the print job to reach the device. Therefore a corresponding time is needed until the handling of the print job is reflected and thus there is a possibility that the handling of deleting the print job is not reflected by a time by which the handling should be reflected.

Furthermore in the technique disclosed in Japanese Patent Laid Open No. 2002 202945 each time a handling operation is performed for a print job checking is performed to determine whether an access ticket authority information embedded in the print job matches an access ticket authority information of a user. Therefore in a case where authority is granted to a user in a complicated manner for example such that domain groups are defined and deleting of a print job is permitted if the user is a member belonging to a particular domain group it takes a long time to perform authentication and thus it is necessary to wait for a long time until it is allowed to delete a print job or change the priority assigned to the print job.

Furthermore in Japanese Patent Laid Open No. 2002 36631 authorization as to authority to delete a print job is not considered as a technique to make it possible to surely delete a print job. Furthermore in the technique disclosed in Japanese Patent Laid Open No. 2002 36631 it is assumed that deleting is performed for a print job printed by a printing system. Therefore in a case where a deleting is performed by a system different from a system used to perform printing as is the case with the pull print system the technique disclosed in Japanese Patent Laid Open No. 2002 36631 cannot be applied.

In view of the above the present invention provides a technique in a pull print system to efficiently handle a print job according to authority granted to an operator.

According to an aspect of the present invention there is provided a printing apparatus configured to perform printing in accordance with a print job and in accordance with a schedule registered before the printing including an authority setting unit configured to if authority of a user for the print job is authorized set the authority of the user for the print job a determination unit configured to if a command to handle the print job is issued by the user determine whether the user has the authority to perform the handling based on the authority set by the authority setting unit and an execution unit configured to if the determination unit determines that the user has the authority execute a process according to the handling on the print job.

According to an aspect of the present invention there is provided a method of controlling printing performed in accordance with a print job and in accordance with a schedule registered before the printing comprising the steps of if authority of a user for the print job is authorized setting the authority of the user for the print job if a command to handle the print job is issued by the user determining whether the user has the authority to perform the handling based on the authority set in the authority setting step and if the determination in the determination step is that the user has the authority executing a process according to the handling on the print job.

According to an aspect of the present invention there is provided a computer readable storage medium storing a program configured to cause a computer to execute a process of performing printing in accordance with a print job and in accordance with a schedule registered before the printing the process comprising the steps of if authority of a user for the print job is authorized setting the authority of the user for the print job if a command to handle the print job is issued by the user determining whether the user has the authority to perform the handling based on the authority set in the authority setting step and if the determination in the determination step is that the user has the authority executing a process according to the handling on the print job.

In the present invention as described above if authority of a user for a print job is authorized the authority of the user for the print job is set. When a command to handle the print job is issued by the user a determination is made as to whether the user has the authority to perform the handling on the basis of the set authority. If it is determined that the user has the authority a process according to the handling on the print job is executed depending on the authority. Thus even in the pull print system it becomes possible to efficiently handle the print job according to the authority granted to the user.

Further features of the present invention will become apparent from the following description of exemplary embodiments with reference to the attached drawings.

Embodiments of the present invention are described below with reference to the accompanying drawings.

In this printing system as shown in a server computer system for controlling the printing system is mutually connected to a print device and a client computer via a WAN Wide Area Network .

A DBMS DataBase Management System is a server computer system that manages data such as document data print job and print information stored in a storage . The DBMS is adapted to receive an handling operation command such as updating acquiring adding deleting etc. of various kinds of data and execute the received handling operation command. In the case of a large scale printing system the DBMS may be formed in the cluster configuration to distribute loads or in the cluster configuration having redundancy for handling a failure.

The storage may be directly connected as a DAS Direct Attached Storage to the DBMS . Alternatively the storage may be connected as a SAN Storage Area Network to the DBMS via a network.

The print server system is a server computer system adapted to monitor or manage print devices in the printing system and transfer print jobs to the print devices . Note that the notation print devices is used to generically denote print devices A to D. Hereinafter the notation a print device is used to denote a typical print device when it is not necessary to discriminate between the print devices . In a case of a large scale printing system the print server system may also be formed in a cluster configuration to distribute loads or may be formed in a cluster configuration with redundancy. The print server system is mutually connected to the DBMS or a Web server system which will be described later via a LAN Local Area Network A. The print server system is adapted to transmit receive to from the DBMS or the Web server system print job data a print control command information associated with a print job under management etc.

The Web server system transmits print job data managed by the print server system document data managed by the DBMS or the like to front ends clients mutually connected to Web server system via the WAN . The Web server system is a server computer system in the printing system. In a case where the printing system is large in scale the Web server system is usually formed in a cluster configuration to distribute loads or formed in a cluster configuration with redundancy.

The Web server system is adapted to receive a print command or a command to handle a print job from the client and transfer it to the print server system . Furthermore the Web server system manages authentication of login from the client and the print device in cooperation with a directory server that will be described later. The Web server system has user authority information preset by a system designer or a document producer. Examples of user authority information are information associated with authority to access print and or delete a document information associated with authority to perform printing using the print device information associated with authority to delete a print job etc. The user authority information may be stored in the Web server system and managed thereby or may be stored in the DBMS described above and managed thereby.

The directory server is a server adapted to manage authentication of each user by using a combination of user account information a user name and a password. The user authentication may be managed such that each user participates in a particular domain group. In this case for example authority of users participating in a domain group may be set over a range different from authority individually assigned to each user. It may also be possible to make a design such that a user is allowed to participate in a plurality of domain groups.

Print devices A B C and D each used as a printing apparatus are connected to a LAN B or a LAN C via network interface that is not shown in the figure. The LAN B and the LAN C are each connected to the WAN . The print device is capable of communicating with the above described print server system the Web server system and other apparatuses via the LAN B or the C and the WAN .

As for the print device a laser beam printer using electrophotography an ink jet printer using an ink jet technique or other printers may be used as required. The print device includes a schedule application that manages a print schedule described later and a pull print application that issues a print command on the print device . The print device also includes an authentication application configured to log in to the Web server system in response to logging in to the print device . The print device is connected for communication with an information input device for use to log in to the print device .

The clients A B C and D are client computers for performing information processing. Hereinafter these clients A B C and D will be generically denoted by clients and the notation a client is used to describe a typical client when it is not necessary to discriminate between the clients . The clients are connected to the LAN B or the LAN C via a network interface that is not shown in the figure so that the clients are capable of communicating with the print server system the Web server system or the directory server via the WAN . The client may be a computer having a permanent storage device or a thin client having a temporary storage device.

In the present embodiment the print server system is configured so as to distribute loads in a large scale printing system. More specifically the print server system includes a plurality of print servers A to N and a load balancer that is a switch mechanism for distributing loads. The plurality of print servers A to N are mutually connected to the LAN A via the load balancer . Hereinafter these print servers A to N will be generically denoted by print servers and the notation a print server is used to describe a typical print server when it is not necessary to discriminate between the print servers .

The load balancer detects the state in terms of the load for each of the plurality of print servers A to N and controls the distribution of loads such that a request is preferentially sent to a print server on which no large load is imposed. One method of detecting the state in terms of loads is to periodically send a predetermined request to each of the print servers A to N and determine a response time needed for each print server to return a response to the request as the load imposed on the print server . Distributing of requests may be accomplished simply by sending requests in turn to the printer servers A to N. This method is called a round robin method.

The configuration of the print server is explained below. The print servers A to N are similar in configuration and thus the detailed configuration is shown in only for the print server A but the detailed configuration is not shown in for the other print servers B to N.

As shown in the print server includes an API Application Program Interface a DB driver a job manager and an device manager .

The API accepts information such as that described below from the Web server system or other servers that produce a printable document. That is the API accepts a document registration request a document print request print command a print job control request print job handling request etc. Examples of other servers that produce a printable document include a form server adapted to produce a document in a predetermined form a document management server adapted to centrally manage documents of users etc.

The DB driver is a module adapted to communicate with the DBMS . If the DB driver receives for example a request for registering a document the DB driver registers the document in the DBMS . On the other hand when the DB driver receives a print request the DB driver sends a document ID indicating print data document to be printed to the DBMS and acquires the print data document from the DBMS .

The job manager has the following functions. When a document registration request is accepted by the API the job manager registers this document in the DBMS via the DB driver . When a print request is accepted by the API the job manager acquires data associated with document data to be printed from the DBMS via the DB driver and manages the acquired data associated with the document as a print job.

The job manager instructs the device manager described below such that the document acquired by the DBMS is printed by a print device that should print this document.

Next the device manager shown in is explained. is a diagram illustrating an example of information device information associated with the a print device managed by the device manager .

The device manager manages device information such as that shown in and more specifically the device manager stores various kinds of information associated with the print device used in the printing. The device information includes a device name a communication address of the device a communication port number a transfer scheme of the print job print data and a status of the print device .

An example of the transfer scheme of the print job is a RAW scheme. In this scheme data is continuously transmitted as a stream using a TCP IP protocol. Other examples of transfer schemes of the print job include a scheme of transmitting the print job using an LPR Line PRinter daemon protocol protocol and that using an HTTP Hyper Text Transfer Protocol protocol.

The device information may be managed not by the device manager but by the DBMS . In this case the device manager acquires the device information via the DB driver as required. As described above there is no particular restriction on a location where the device information is stored.

If the device manager accepts a request from the job manager for transmitting a print job print data then the device manager starts communicating with the schedule application see provided in the print device . The device manager then transfers supplies the print job to the print device and instructs the print device to sequentially perform printing. A method of the printing performed herein will be described in detail later.

The Web server system which is an example of an external apparatus is generally formed in the cluster configuration as described above to distribute loads. Thus in the present embodiment it is assumed that Web server system includes a plurality of Web servers and is formed in the cluster configuration to distribute loads.

The Web server is a server adapted to perform information communication in the WWW World Wide Web system and is implemented by software. The Web server system has the following functions. When a login occurs from a front end such as a client or a print device the Web server system first acquires user account information user name and a password and requests the directory server to perform login authentication.

If the login authentication is passed successfully then the Web server system authorizes the authority of the user login user for the document. According to the authorized authority the Web server system acquires data associated with the document from the DBMS and transmits the acquired data to the login client or the print device . In this process the Web server system transmits the use ID of the login user to the DBMS thereby acquiring from the DBMS the data associated with the document for which the login user has the authority.

If the Web server system receives a command to print the document from the client or the print device the Web server system sends a print command to the print server system together with a document ID identifying the document.

A policy in authorizing the authority is to allow accessing to any document of any user belonging to a domain. An alternative policy is to allow accessing to only documents of the user of interest. The policy in authorizing the authority may be flexibly designed according to a policy of a user who builds the printing system. The policy in approving the authority may be set not only as to the accessing to documents but also as to the authority of printing documents the authority of deleting print jobs the authority of promoting etc. In the present embodiment the authority of the user for the print job includes authority to handle the print job document handling authority authority to handle the document itself and access authority authority to perform an operation to access the document .

The DBMS may be configured to manage data using various kinds of data formats such as card type data relational type data an object type data etc. In the present embodiment by way of example it is assumed that the DBMS is configured to manage relational type of data which is most widely employed in the art.

In the DBMS stores a document table as table information. The information stored in the document table includes information indicating a document ID which is a document identifier a document name a user name who has registered the document and a data path indicating a location at which the document is actually stored.

In the present embodiment as described above the data path is stored in the document table as reference information according to which to access the data associated with document and the actual data is stored at another location. Alternatively the data associated with the document may be directly stored in the document table .

The DBMS is used for example as described below. The DBMS acquires data associated with all documents of a user identical to the user name specified by the Web server system . Furthermore the DBMS acquires data associated with a document having an ID identical to the document ID transmitted from the print server system print server . The DBMS registers a new document transmitted from the print server system print server .

In an image forming unit forms an image on a recording medium such as recording paper by performing a sequence of image forming processes including handing paper transferring an image fixing the image etc. This image forming unit includes for example an ink jet printer or an electrophotographic image forming unit.

An image reading unit includes a scanner or the like and serves to optically read an image of a document and convert it into digital image information. The image reading unit outputs the digital image information to the image forming unit . Thus an image is formed according to the digital image information. The image reading unit transfers the digital image information to a facsimile unit or a network interface unit . This allows the digital image information to be transmitted to the outside via a communication line.

A printing apparatus controller device controller controls the operation of the image forming unit and the operation of the image reading unit for example such that the information of the document read by the image reading unit is copied by the image forming unit . The device controller includes the network interface unit the print processing unit the facsimile unit and the operation unit controller and controls transferring information among these units.

The facsimile unit transmits receives facsimile image information. More specifically the facsimile unit transmits digital image information read by the image reading unit as the facsimile image information and the facsimile unit decodes received facsimile image information. The decoded facsimile image information is recorded by the image forming unit in the form of an image on a recording medium such as recording paper.

The operation unit controller generates a signal in accordance with an operation performed by a user on an operation panel of an operation unit and displays various kinds of data or messages on the operation unit or a display . The print processing unit processes print data input for example via the network interface unit and outputs resultant print data to the image forming unit to request the image forming unit to print the print data. The network interface unit controls transmission reception of data with another communication terminal device via a communication line such as the LAN .

A virtual machine is at a level higher than the device controller and the printing system is configured so that the device controller can be controlled from the virtual machine .

The network interface unit is configured such that the network interface unit can be directly used by the device controller and by the virtual machine and such that that the device controller and the virtual machine can independently access to the outside via the network interface unit .

At a higher level than the virtual machine there is an application described in a programming language having a capability of handling API Application Programming Interface provided by the virtual machine . This application is capable of indirectly interacting with the device controller via the virtual machine and is capable of operating the image forming unit or the image reading unit .

In the present embodiment the applications include a schedule application a pull print application an authentication application and other applications . Any of these applications may be uninstalled or installed as a new application by the virtual machine .

In the present embodiment it is assumed that the applications are installed as software in the print device . Alternatively one or all of the applications may be installed as hardware. Instead of the application described above an application installed in an external computer connected via a communication line to the print device may be used.

An external storage device controller is configured such that when image data read by the image reading unit is converted into a data format storage in an external storage device by the image forming unit external storage device controller stores the image data in the external storage device. The external storage device controller is also adapted to read image data stored in the external storage device. The image data read from the external storage device is subjected to a printing process performed by the image forming unit or is transmitted to the outside via the network interface unit .

In the present embodiment as an example of a login device used by a user to log in to the print device an IC card reader is connected to the print device such that communication is possible between them. It is possible to supply user account information to the authentication application via the IC card reader . The login unit may be realized by other devices. For example an ID card reader may be used as the login unit or a user is allowed to log in to the print device by performing an inputting operation on a device panel controlled by the operation unit controller .

As shown in the schedule application includes a communication manager a job manager and a device manager .

The communication manager receives a connection request from the print server system print server . The communication manager is also adapted to transfer a notification of a change in the status of a print job received from the device controller to the outside. The printing sequence will be described in detail later.

The job manager is a module adapted to perform scheduling of a print job accepted from the print server system print server and manage the print job so that the printing is performed according to the schedule. The job manager is also adapted to accept a command to handle a print job such as a command to delete the print job or a promotion command a priority change command from the printer server or the pull print application described later and control the print job according to the accepted command.

The device manager is a module that communicates with the device controller and serves as a driver that deletes a print job and detects a change in the status of a print job.

In schedule information includes a job ID of a print job a document name a user name an acceptance date time a document ID a print job status and authorized authority information that is one of features of the present embodiment. This schedule information basically includes information commonly included in the job information managed by the print server system print server . A duplicated explanation of such common information is omitted herein see .

The authorized authority information includes information indicating whether or not a user logging in to the print device currently has the authority to control the print job identified by the job ID . More specifically for example information indicating whether deleting of a print job is permitted information indicating whether accessing to detailed information of the print job is permitted information indicating whether promoting changing of priority processing order of the print job is permitted etc. are stored as the authorized authority information . Acquisition and updating of the authorized authority information will be explained in detail later.

The authentication application acquires information associated with an IC card from the IC card reader that is connected to the print device such that communication is possible between them and acquires a user ID identifying a user from a user management table managed by the authentication application . The user management table is a 2 dimensional table in which information associated with an IC card is stored in association with a corresponding user ID.

The authentication application sends the acquired user ID to the pull print application described later thereby notifying the pull print application of the login. The authentication application is also adapted to detect a logout of a user and notify the pull print application of the logout. The authentication application may detect a logout for example by detecting pressing down of a hard key disposed on the print device . When a predetermined time has elapsed without detecting any operation performed by a user the authentication application may determine that the user has logged out.

As shown in the pull print application includes a print job screen a pull print screen a pull print controller and a screen activation module . The screen activation module receives a login notification or a logout notification from the authentication application and transfers the notification to the pull print controller . If the pull print controller receives the login notification the pull print controller initializes or newly produces the print job screen and the pull print screen . A more detailed explanation of the print job screen and the pull print screen will be given later. When the pull print controller receives a logout notification the pull print controller discards the produced print job screen and pull print screen .

Next a processing flow associated with printing and that associated with handling of a print job are described below.

First referring to an explanation is provided as to an example of a print sequence performed between the print server system print server and the print device schedule application and device controller .

Note that although not shown in the figure when the schedule application is started schedule application performs an event registration in the device controller so that when a change in status occurs in the print job of the print device managed by the device controller the change is notified to the schedule application .

A document print request sent to the print server includes a document ID and a name or an address of the print device to be used in printing. In accordance with the notified document ID the job manager acquires data associated with the document from the DBMS via the DB driver . Next the device manager identifies the print device to be used in printing. Thereafter printing is performed according to the sequence described below.

First in step S the print server and the schedule application establish a communication session. The establishment of the communication session is accomplished by using a communication protocol such as TCP IP or HTTP.

Next in step S the print server sends a connection request to the schedule application . The schedule application accepts this connection request by the communication manager .

Next in step S the print server registers an event notification request in the schedule application so that a notification is provided to the print server when the status of the print job or the print device changes.

Next in step S the print server acquires a list of schedule information currently managed by the job manager of the schedule application . This list of schedule information may be sent to another application server connected to for example the print server . Alternatively the list of schedule information may be sent to a console for managing the print server . It is possible to realize a function of provide information associated with a print job to the client via the Web server system . However such a function is not related to the present invention a further detailed description thereof is omitted herein.

Next in step S the print server issues a schedule request as to the print job to the schedule application . Note that the schedule request includes job information .

Next in step S on receiving the schedule request the schedule application adds information based on the schedule request to the schedule information managed by the job manager . The schedule application then issues a new job ID and registers it. This job ID is notified to the print server .

Next in step S the job manager controls a printing order in accordance with the order of the list of the schedule information . When a print job in the schedule information is given to a turn the job manager issues a print permission command to a print server that has registered this print job. The printing order may be controlled simply in accordance with the order registered in the list of the schedule information or in accordance with the priority set in the print job.

If the print server receives the print permission command then in step S the print server sends a print job transfer start notification to the schedule application . Thereafter in step S the print server starts transferring the print job to the device controller . The transferring of the print job is performed according to the transfer scheme set in the device information shown in . If the schedule application receives the print job transfer start notification the schedule application changes the status of the schedule information associated with this print job into the being transferred status.

Next in step S the device controller sequentially analyzes the print job received from the print server and starts printing.

Next in step S to change the status of the print job under management into the being printed status the device controller sends a notification of the change in the status to print started to the schedule application that has registered the event notification request. That is the device controller notifies the schedule application that printing has started.

If the schedule application receives this notification via the device manager then in step S the schedule application sends a print start notification to the print server that has registered the event notification request. Thus the print server is capable of recognizing the status of the print job the print command for which has been issued by the print server .

If the print server completes the transfer of the print job then in step S the print server notifies the schedule application that the transfer of the print job has been completed. If the schedule application receives this notification then as at the time at which transferring of the print job was started the schedule application changes the status into transfer completed of the schedule information of the print job that has been transferred.

Thereafter in step S the print device ends the printing operation. If the printing is completed in the above described manner then in step S the device controller notifies the schedule application that the printing is completed as at the time at which the printing was started. If the schedule application receives this notification then in step S the schedule application sends a print end notification to the print server .

When the print server receives this notification if all print jobs to be processed have been completed then in step S the print server releases registration of the event notification request in the schedule application . Next in step S the print server sends a disconnection request to the schedule application . If the registration of the event notification request is released and if the disconnection request arrives at the schedule application the schedule application performs a process of ending the communication with the print server .

Finally in step S the print server and the schedule application close release the session established in step S.

Thus the print server is capable of performing printing using the print device via the schedule application in the above described manner.

First if in step S shown in the authentication application receives a login of a user from the IC card reader then in step S the authentication application acquires user account information user ID associated with the user who has performed the login. The authentication application sends a login notification to the pull print application .

If the pull print application receives the login via the screen activation module the pull print application produces the print job screen . In this process the pull print application displays a user name according to the acquired user account information the user ID in a login user name field of the print job screen .

Next in step S the pull print application establishes a communication session between the schedule application . The establishment of the communication session is accomplished by using a communication protocol such as TCP IP or HTTP. Note that this communication is performed in the virtual machine by using a method called loop back and thus data transmitted in the communication does not go to the outside.

Next in step S the pull print application sends a connection request to the schedule application . The schedule application receives this connection request via the communication manager .

Next in step S the pull print application registers an event notification request in the schedule application so as to receive a notification when the status of the print job changes.

Next in step S the pull print application acquires a list of schedule information currently managed by the job manager of the schedule application .

If the pull print application acquires the list of the schedule information the pull print application displays the content of the acquired list in a print job list field of the print job screen . In this process the total number of acquired lists print jobs is displayed in a number of print jobs field . In a case where the total number of records included in the acquired list the total number of print jobs is too great to display the entire contents of the acquired list print jobs in the print job list field at a time the pull print application performs a paging process as shown in . Note that in the example shown in the print job lists are described over 5 pages.

Next in step S the schedule application newly performs scheduling of print jobs for example in accordance with a command given by the print server . In this case in step S the schedule application sends a schedule to the pull print application . Upon receiving the schedule the pull print application appends new job information at the end of the print job list thereby updating the print job screen .

In a case where printing is started or ended as is the case in step S S S or S the status of the print job is updated as described below. For example if the schedule application receives a print start notification or a print end notification the schedule application sends a notification of the change in the status of the print job to the pull print application from which the event notification request has been registered step S or S . Upon receiving the notification of the change in the status of the print job the pull print application updates the status of this print job in the print job list on the print job screen .

If the details button on the print job screen is operated by a user so as to be pressed then the pull print application displays on another screen detailed information associated with print jobs checked in the print job list .

Thereafter in step S if the authentication application detects a logout performed by the user for example by pressing a hard key then in step S the authentication application sends a notification of the logout of the user to the pull print application . Upon receiving this notification the pull print application releases the registration of the event notification request in the schedule application and then the pull print application sends a disconnection request to the schedule application steps S and S . Finally the pull print application closes the session with the schedule application step S .

A process performed when a promote button priority change button on the print job screen is pressed and a process performed when a delete button is pressed will be described later.

First if in step S of the authentication application receives a login of a user from the IC card reader then in step S the authentication application acquires user account information user ID associated with the login user. The authentication application sends a login notification to the pull print application .

The pull print application accepts the login via the screen activation module and produces a pull print screen . In this process the pull print application displays a user name according to the acquired user account information user ID in a login user name field of the pull print screen .

Next in step S the pull print application sends a login notification to the Web server system . In this process the user account information user ID acquired from the authentication application is used as information for the login. To achieve improved security in addition to the user account information user ID a password may be used. In this case the authentication application may internally manage each pair of a password and user ID or may perform authentication using a password by communicating with the external directory server . Alternatively instead of using the IC card reader in performing login the login may be performed by inputting the user ID of the password via a screen.

If the Web server system receives the login notification from the pull print application then in step S the Web server system requests the directory server to provide authentication information.

Next in step S the directory server performs authentication using pre registered user information. If the authentication is successful then in step S the directory server returns as the authentication information user information and information indicating a domain group to which the user belongs to the Web server system . On the other hand if the authentication fails the directory server returns a message indicating the authentication failure to the Web server system . In this case the login fails.

If the Web server system receives the authentication information from the directory server then in step S the Web server system sends a communication session start notification to the pull print application . In this process together with the notification the authentication information acquired in step S is also transferred to the pull print application .

Next in step S on the basis of the acquired authentication information the pull print application requests the Web server system to provide a list of documents. In this step a narrowing condition may be set for example such that only a list of documents registered by a user ID is requested or such that a list of all documents of a domain group to which the user belongs to is requested. In the present embodiment by way of example it is assumed that the list of documents registered by the user ID is requested.

If the Web server system receives the request for acquisition of the document list then in step S the Web server system acquires the list of documents with IDs identical to the user ID from the DBMS and transfers the acquired list to the pull print application .

If the pull print application acquires the list of documents the pull print application displays the list in the document list field of the pull print screen . In this process the pull print application also displays the total number of acquired documents in the number of documents field . In a case where the total number of records in the acquired list the total number of documents is too great to display the entire contents of the acquired list documents in the document list field of the pull print screen at a time the pull print application performs a paging process. In the example shown in the contents of the acquired list documents are displayed in the document list field of the pull print screen for all documents at a time on one page .

If the details button on the pull print screen is operated by a user so as to be pressed then the pull print application displays on another screen detailed information associated with documents checked in the document list In a case where the delete button on the pull print screen is operated by a user so as to be pressed then the pull print application requests the Web server system to delete the documents. If the Web server system receives the document delete request the Web server system deletes the documents requested to be deleted of the documents managed by the DBMS .

In step S if the authentication application detects a logout performed by the user for example by pressing a hard key then in step S the authentication application sends a notification of the logout of the user to the pull print application . If the pull print application receives this notification then in step S the pull print application sends a notification of the logout to the Web server system . Finally in step S the pull print application closes the session with the Web server system .

Next referring to a description is given of an example of a sequence performed when the print button on the pull print screen is pressed.

If the print button is pressed the pull print application acquires a document ID identifying a document checked in the document list of pull print screen . In step S the pull print application sends a print command to the Web server system . The print command includes the acquired document ID and information associated with the print device in which the pull print application is installed. Examples of the information associated with the print device include an address of the print device and a device type.

Next in step S the Web server system identifies the print device . In this identification step the Web server system identifies the print device from the device information managed by the DBMS or the print server in accordance with the information associated with the print device transmitted in step S.

Next in step S the Web server system performs authorization as to whether the user who has issued the print command has the authority for printing of the document specified by the user. If the authorization fails the Web server system notifies the pull print application that the printing is not permitted.

On the other hand if the authorization is passed successfully then in step S the Web server system sends a print command to the print server . This print command includes the device information associated with the print device identified in step S and the document ID transmitted in step S.

If the print server receives the print command then in step S the print server acquires from the DBMS a document corresponding to the document ID included in the print command.

Thereafter printing is performed according to the sequence described above with reference to steps S to S .

The information associated with the schedule registered in step S by the schedule application is sent in step S from the schedule application to the pull print application . If the pull print application receives this information the pull print application updates the contents of the print job list on the print job screen in accordance with the received information.

Next an explanation is provided below as to authorize the authority to handle a print job registered in the print job list on the print job screen .

The authorization as to authority for handling a print job can be realized by adding an authorization sequence to the sequence of producing the print job screen described above with reference to . The realization of the authorization sequence may be based on one of two methods described below. In the following explanation it is assumed that in the sequence of producing the print job screen described above with reference to the process of logging in to the pull print application in steps S and S has already been performed.

First referring to an explanation is provided below as to a first example of a sequence of authorizing the authority to handle a print job registered in the print job list of the print job screen .

First in step S the pull print application establishes a communication session with the schedule application . The establishment of the communication session is accomplished by using a communication protocol such as TCP IP or HTTP. Note that this communication is performed in the virtual machine by using a method called loop back and thus data transmitted in the communication does not go to the outside.

Next in step S the pull print application sends a connection request to the schedule application . The schedule application accepts this connection request via the communication manager .

Next in step S the pull print application registers an event notification request in the schedule application so that a notification will be provided to the pull print application when a change occurs in the status of the print job.

Next in step S the pull print application acquires a list of schedule information currently managed by the job manager of the schedule application . The pull print application stores the acquired list as a print job list .

Next in step S the pull print application requests the Web server system to approve the print job of the schedule information acquired in step S. The requesting for the authorization is performed by sending information associated with a user logging in to the pull print application and a document ID of the print job or an print job ID to the Web server system .

In this process the authorization may be requested for all print jobs or for particular print jobs satisfying a particular condition.

For example the particular condition may be that the status of print job indicates that the transfer of the print job has been started or the print job is in a status following that. That is print jobs for which the authorization is requested may be limited to those in a particular status such as those which are being transferred those which have been transferred or those which are being printed. For a print job that has not yet been transferred even if authorization is performed after a print job delete command is issued the deleting command is executed because it takes a time to start printing.

Another example of the condition is that print jobs having an owner name identical to the user name logging in. This condition is based on the policy that any print job requested to be quickly deleted must be of the owner.

As described above print jobs to be subjected to the authorization of the authority can be determined by comparing information set to print jobs such as the status or the user name of print jobs with the information indicating the preset condition.

Alternatively the condition may be set in terms of the number of print jobs. For example print jobs within a particular range of the printing order from the first position to a predetermined number th position for example print jobs within a range from the first place to a predetermined number th place in the registration order in which the schedule information was registered may be subjected to the authorization process. For example in a case where the print job list is described over a plurality of pages authorization may be performed for all print jobs included in the first and second pages. If it is detected that a user has advanced the page authorization may be performed for print jobs described on the third page.

In the present embodiment as described above the authorization request unit is realized by executing the process in step S.

If the Web server system receives the authorization request the Web server system authorizing the authority of the user logging in to the pull print application for the print job of interest in accordance with the preset policy. Examples of authority are authority to delete a print job authority to promote the priority of the print job and authority to access detailed information of the print job. The Web server system returns the authorized authority information indicating the authorized authority to the pull print application .

Next in step S the pull print application sets the acquired authorized authority information in the schedule information managed by the schedule application . In the present embodiment as described above the authority setting unit is realized by executing the process in step S.

In r in the authorized authority information indicates that the user has the authority for the detailed information of the print job. w indicates that the user has the authority to delete the print job and x indicates that it is allowed to advance the priority such that printing is performed ahead of other print jobs. For example a user currently logging in to the pull print application does not have any authority for a print job with a document ID of 0000 0000 0000 0005 but has the authority in terms of all handling operations i.e. deleting accessing to detailed information and advancing the priority for a print job with a document ID of 0000 0000 0000 0004 .

Referring again to if a schedule of a new print job occurs in step S then in step S the schedule application notifies the pull print application of the schedule.

If the pull print application receives the notification of the schedule then in step S requesting for authorization for a print job which has newly occurred is performed in a similar manner to step S. In step S the pull print application sets the acquired authorized authority information in the schedule application in a similar manner to step S. In the present embodiment as described above the authorization request unit is realized by executing the process in step S and the authority setting unit is realized by executing the process in step S.

Instead of performing authorization for a print job which has newly occurred authorization may be performed for a print job whose transfer has been started. The authorized authority information associated with the print job should be set according to the authorization method in steps S and S described above. For example when the authorization is performed according to the paging of the print job list the authorization process in steps S and S is performed in response to detecting advancing of the page performed by a user.

If a logout from the pull print application occurs then in step S the pull print application releases the registration of the event notification request in the schedule application . Thereafter in step S the pull print application requests the schedule application to delete the authorized authority information . In response the schedule application deletes the authorized authority information .

In step S the pull print application sends a disconnection request to the schedule application . In step S the pull print application closes the communication session with the schedule application .

The schedule application sets and deletes the authorized authority information included in the schedule information the schedule application manages in the manner described above. Thus the print job can be processed in accordance with the authority indicated by the authorized authority information .

Next referring to an explanation is provided below as to a second example of a sequence of authorizing the authority to handle a print job registered in the print job list of the print job screen .

First in step S the pull print application establishes a communication session with the schedule application . The establishment of the communication session is accomplished by using a communication protocol such as TCP IP or HTTP Note that this communication is performed in the virtual machine by using a method called loop back and thus data transmitted in the communication does not go to the outside.

Next in step S the pull print application sends a connection request to the schedule application that is the pull print application logs in to the schedule application . In this login process the pull print application sends user account information a user ID to the schedule application . The schedule application accepts the login via the communication manager .

If the schedule application accepts the login then in step S the schedule application requests the Web server system to authorize the authority for the print job of the currently stored schedule information . The requesting for the authorization is performed by sending the information associated with the login accepted in S the user account information the use ID and a document ID of the print job to the Web server system .

The authorization is performed in a similar manner to step S in . The print jobs to be subjected to the authorization process are selected in a similar manner as described above with reference to step S in . That is if the Web server system receives the authorization request the Web server system authorizes the authority of the user logging in to the pull print application for the print job of interest in accordance with the preset policy. The Web server system returns the authorized authority information indicating the authorized authority to the pull print application .

After the authorization is completed in the above described manner the schedule application sets the authorized authority information transmitted from the Web server system in the schedule information stored in the schedule application in a similar manner to step S in .

In the present embodiment as described above the authorization request unit and the authority setting unit are realized by executing the process in step S.

Next in step S the pull print application registers an event notification request in the schedule application so that a notification will be provided to the pull print application when a change occurs in the status of the print job.

Next in step S the pull print application acquires a list of schedule information currently managed by the job manager of the schedule application . The pull print application stores the acquired list as a print job list .

If a schedule of a new print job occurs in step S then in step S the schedule application issues a request for authorization for a print job which has newly occurred in a similar manner to step S. The schedule application then sets the authorized authority information transmitted from the Web server system in the schedule information stored in the schedule application in a similar manner as to step S. In the present embodiment as described above the authorization request unit and the authority setting unit are realized by executing the process in step S.

Instead of authorizing the authority for a print job which has newly occurred authorization may be performed for a print job whose transfer has been started. The authorized authority information associated with the print job should be set according to the authorization method in step S described above. For example when the authorization is performed according to the paging of the print job list the authorization process in steps S and S is performed in response to detecting advancing of the page performed by a user.

If a logout from the pull print application occurs then in step S the pull print application releases the registration of the event notification request in the schedule application . In step S the pull print application sends a disconnection request to the schedule application that is the pull print application sends a logout notification to the schedule application .

If the schedule application receives the logout notification then In step S the schedule application deletes all authorized authority information registered in the schedule information stored in the schedule application . In the present embodiment as described above the deleting unit is realized by executing the process in step S.

In step S the pull print application closes the communication session with the schedule application .

As described above in response to the login or logout of the user to from the pull print application the schedule application sets or deletes the authorized authority information in from the schedule information the schedule application manages. Thus the print job can be processed in accordance with the authority indicated by the authorized authority information .

Next referring to an explanation is provided below as to an example of a sequence performed when the promote button on the print job screen is pressed and as to an example of a sequence performed when the delete button is pressed.

Steps S to S in are similar to steps S to S in the printing sequence performed between the print server and the schedule application described above with reference to . Steps S to S correspond to steps S to S in the authorization sequence described above with reference to . Steps S and S correspond to steps S and S in the authorization sequence described above with reference to .

In step S if the promote button or the delete button on the print job screen is operated by a user so as to be pressed the pull print application performs the following process. That is depending on the pressed button in step S the pull print application sends a print job promote request or a print job delete request to the schedule application . When the request is sent a print job ID and information indicating the handling operation type such as promoting or deleting are sent together with the request.

If the schedule application receives the promote request or the delete request the schedule application makes a determination as to the authority on the basis of the preset authorized authority information . If it is determined that the authority is granted then in step S the schedule application requests the print server to perform the promoting or the deleting. In the present embodiment as described above the determination unit is realized by executing the process in step S.

The determination as to the authority of deleting is made simply by checking whether the authority is granted or not. In contrast the determination as to the authority of promoting is made for example as follows. That is a determination is made as to whether a print job requested to be promoted is allowed to be advanced in schedule to a point prior to a print job currently scheduled to be printed before the print job requested to be promoted. In accordance with a result of the determination the print job is promoted to an allowable earliest point in schedule. Alternatively only when the print job has the authority to get ahead of all print jobs currently scheduled to be printed before the print job requested to be promoted the print job may be promoted but otherwise the print job may not be promoted the promotion fails .

Thus as described above the pull print application is capable of directly and efficiently requesting the schedule application to perform a handling operation such as promoting or deleting on a print job.

In the present embodiment as described above a request for setting the user authority for a print job scheduled in the schedule information is issued from the print device to the Web server system . Upon receiving the request the Web server system performs the authorization as to the authority requested to be set according to the preset policy. If the authority is authorized the print device sets the authorized authority information indicating the authorized authority in the schedule information . Thereafter if a command to perform an operation such as pull printing on the print job is issued on the print device the print device determines whether the authority for the operation is granted or not on the basis of the authorized authority information . If the result of the determination indicates that the authority is granted the print device performs the requested operation. Thus the pull print system is capable of efficiently handling the print job according to the authority granted to the user.

In the above described embodiments of the present invention the printing apparatus the units included in the printing system and steps of the method of controlling printing according to the above described embodiments of the invention may be realized by executing a program stored in a RAM or a ROM on a computer. Note that the program and a computer readable storage medium in which the program is stored fall within the scope of the present invention.

The present invention may be embodied for example in the form of a system an apparatus a method a program or a storage medium. More specifically the present invention may be applied to a system including a plurality of apparatuses devices or the like or may be applied to a single apparatus.

In the present invention a software program for realizing a function of any embodiment described above a program corresponding to any of the flow charts shown in and may be directly or remotely supplied to a system or an apparatus. The function of any embodiment of the present invention may be realized by a computer disposed in the system of the apparatus by reading and executing the supplied program code.

Thus the program code installed on the computer to realize one or more functions according to any of the above described embodiments of the invention on the computer also falls within the scope of the present invention. That is the computer program for realizing one or more functions according to any of the above described embodiments of the invention also falls within the scope of the present invention.

In this case there is no particular restriction on the form of the program as long as it functions as a program. That is the program may be realized in various forms such as an object code a program executed by an interpreter script data supplied to an operating system etc.

Specific examples of storage media by which to supply the program include a floppy registered trademark disk a hard disk an optical disk a magneto optical disk an MO disk a CD ROM disk a CD R disk a CD RW disk etc. A magnetic tape a non volatile memory card a ROM a DVD DVD ROM DVD R disk or the like may also be used as the storage medium for the above described purpose.

The program may also be supplied such that a client computer is connected to an Internet Web site via a browser and an original computer program or a file including a compressed computer program and an automatic installer is downloaded into a storage medium such as a hard disk of the client computer thereby supplying the program.

The program code of the program according to an embodiment of the present invention may be divided into a plurality of files and respective files may be downloaded from different Web sites. Thus a WWW server that provides to a plurality of users a program file that realizes one or more functions according to any embodiment of the invention on a computer also falls within the scope of the present invention.

The program according to the present invention may be stored in an encrypted form on a storage medium such as a CD ROM and may be distributed to users. Particular authorized users are allowed to download key information used to decrypt the encrypted program from a Web site via the Internet. The decrypted program may be installed on a computer using the downloaded key information thereby achieving the one or more functions according to any embodiment of the present invention.

One or more functions according to any embodiment of the present invention may be realized by a computer by executing the program. Furthermore one or more functions according to any embodiment of the present invention may be realized by an OS or the like running on a computer by executing part or all of a process.

A program may be read from a storage medium and loaded into a memory of a function extension board inserted in a computer or into a memory of a function extension unit connected to the computer and a CPU or the like disposed in the function extension board or the function extension unit may perform part or all of the process according to the loaded program thereby achieving one or more functions according to any embodiment of the invention.

While the present invention has been described with reference to exemplary embodiments it is to be understood that the invention is not limited to the disclosed exemplary embodiments. The scope of the following claims is to be accorded the broadest interpretation so as to encompass all modifications equivalent structures and functions.

This application claims the benefit of Japanese Application No. 2007 197740 filed Jul. 30 2007 which is hereby incorporated by reference herein in its entirety.

