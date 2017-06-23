---

title: Collecting user attributes and device attributes to target users with promotions
abstract: The present disclosed system is directed toward a communication and management system that dynamically targets network devices for content deployment, such as application programs, device drivers, configuration files, and registry subhives. Moreover, the present system targets users of network devices for promotions, such as advertisements offered by Internet e-commerce sites. Network devices and their users are targeted through user profiles. User profiles are created when network devices register with the system server and are continually updated with information provided by user activity and event logs that are periodically uploaded from each device. A scalable messaging system provides for data transmission between the system server and among the network devices such that it is neutral as to the specific hardware platforms on which it is implemented.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07689672&OS=07689672&RS=07689672
owner: Microsoft Corporation
number: 07689672
owner_city: Redmond
owner_country: US
publication_date: 20080204
---
This application is a divisional of U.S. application Ser. No. 09 519 221 filed Mar. 6 2000 now U.S. Pat. No. 7 392 281 which claims the benefit of U.S. Provisional Application No. 60 185 202 entitled System and Method for Targeting Network Devices for Content Deployment by Chaitanya Kanojia Lee Kamenstky Peter Hall and Ian Copeman filed on Feb. 25 2000. The entire teachings of the above applications incorporated herein by this reference.

Generally under the current state of technology and in the past television has been delivered to the residential home either through radio frequency broadcasts satellite downlink or over coaxial cable television CATV network. Data network communications such as Internet access have been delivered via the telephone networks through dial up connections ISDN Integrated Services Digital Network and DSL Digital Subscriber Line lines or over hybrid broadcast data CATV networks where a portion of the bandwidth transmitted by the coaxial cable is allocated for shared data network functionality using a CSMA CD style transmission protocol. Less commonly data connections to the home are provided via satellite links where data are downloaded via the satellite link and uploads are handled through land lines such as the telephone network. Another technique is to transmit data to the home via wireless CAMA for example links.

Almost universally the clients or network devices in the residences are personal computers. Typically they execute application programs such as email clients and browsers that utilize the data network connectivity offered by one of the above techniques.

The trend however is towards a more ubiquitous computing model where the network devices in the home will be embedded systems designed for a particular function or purpose. This has already occurred to some degree. Today for example CATV network set top boxes typically have limited data communication capabilities. Their main function is to handle channel access issues between residential users and a server on the cable TV network.

In the future the functionality offered by these set top boxes or other embedded platforms such as a game system will be expanded. For example they may offer Internet browsing capabilities and e commerce serving capabilities. Moreover it is anticipated that common household appliances will also have network functionality in which they will be attached to the network to automate various tasks.

The data networks must evolve with deployment of these embedded systems. Where the personal computer can be updated with new network drivers as the network evolves embedded client systems remain relatively static. Moreover the process of installation in the residence must be made less complicated so that a network technician is not required every time a new embedded device is connected onto the network.

One issue that arises in the context of these data networks is a messaging system that is adaptable and can monitor the status of the embedded devices to enable effective communication between the server system and the devices. This issue is particularly critical where communication with and among the embedded devices is sporadic due to the mobile transient nature of these network devices.

The present disclosed system is directed toward a communication and management system that dynamically targets network devices for content deployment such as application programs device drivers configuration files and registry subhives.

Moreover the present system targets users of network devices for promotions such as advertisements offered by Internet e commerce sites. Promotions are generally icons or graphic images with links to host web servers overlaying a video display but also include audio and video clips or data streams.

Network devices and their users are targeted through user profiles. User profiles are created when network devices register with the system server and are continually updated with information provided by user activity and event logs that are periodically uploaded from each device.

The present invention implements a scalable messaging system for data transmission between the system server and among the network devices such that it is neutral as to the specific hardware platforms on which it is implemented.

According to the present invention a message router system is provided that transfers messages to the embedded devices over the data network when those embedding devices are accepting messages. A message store however is also provided that can temporarily store the messages when the destination embedded device is unavailable. The message router can handle delivery at a later time when the network device is active and able to receive messages i.e. the network device is powered on .

In general according to one aspect the invention features a message router system for a server system that communicates with embedded devices over a data network. The router system comprises a router that transfers messages to the embedded devices on the data network when the embedded devices are accepting messages. A message store is also provided that temporarily stores the messages when the embedded devices are not active and stores them until the message devices can accept the messages.

In specific embodiments the system comprises a system manager executing on the server system which tracks that states of the embedded devices on the data network and whether the embedded devices are able to receive messages. A queue manager can also be provided for facilitating the transfer of messages between the message router and the system manager.

According to other aspects of the preferred embodiments the router retrieves messages from the message store when the system manager indicates that the embedded devices to which the messages are addressed are able to receive the messages.

Moreover to handle the transfer of large files a bulk data transfer manager is provided on the server system with a corresponding bulk data transfer agent on the network device. Typically the bulk data transfer agent requests a file at a specific location which the bulk transfer manager then sends. This interchange happens without any intervention from the router.

In general according to another aspect the invention also features a method for routing messages from a server system to embedded devices over a data network. This method comprises transferring messages to the embedded devices over the network when the embedded messages are accepting messages. The messages are stored when the embedded device is inactive and remain stored until the embedded device can receive the messages.

The above and other features of the invention including various novel details of construction and combinations of parts and other advantages will now be more particularly described with reference to the accompanying drawings and pointed out in the claims. It will be understood that the particular method and device embodying the invention are shown by way of illustration and not as a limitation of the invention. The principles and features of this invention may be employed in various and numerous embodiments without departing from the scope of the invention.

The present invention is a communications and management system executing over a data network for targeting content including promotions to users of network devices whose attributes match the attributes of a group profile along with maintaining those network devices.

The system and methods of the present invention can be implemented over a variety of data network infrastructure including cable satellite Digital Subscriber Lines DSL and wireless networks.

Video content providers as well as Internet content providers i.e. host web servers deliver their audio video data signals to a cable service provider internet service provider CSP ISP data center . The Internet content providers deliver their data to the data center via the Internet . Typically video content providers transmit their video signals to the data center via some broadcast medium such as conventional radio frequency television broadcasting techniques or via a digital satellite downlink.

The CSP ISP data center transmits the audio video data signals to multiple head ends only one being shown for simplicity of illustration . The connection between the data center and the head end is typically a hybrid CATV data connection which is supported by an optical fiber infrastructure. Part of this infrastructure carries the audio video signals which are directed from the data center to the network devices . Part of this network also carries the bi directional data communications associated with network control and internet service provisioning.

The head end distributes the audio video data signals over a cable network of hubs and local nodes to a variety of network devices such as set top boxes web phones and cable modems. Some network devices D such as a web phone have a built in video display and speaker system . Other network devices C are peripherally attached to a video display device and speaker system such as a television .

In one embodiment of the present invention the server system A and B collectively referred to as is located at the CSP ISP data center and the head end of the cable network. Installation of the server system at the data center and the head end allows for scalability. The server system A at the data center typically provides centralized management for configuring group profiles and content deployment options while the server system B at the head end preferably handles the registration user profile updates content deployment and other services among the network devices .

There are alternative schemes for deploying the server system within the cable network infrastructure depending on the capacity of the server system and number of network devices . For example the server system is deployed at the hub level when the population of devices is sufficiently dense to necessitate such distribution of the communication load.

The server system transmits data to the network devices via a satellite uplink device to a satellite which in turn transmits the data to a residential satellite downlink dish . The data are received by the network devices connected to the downlink feed .

For the return upload path the network devices transmit data to the server system through a built in modem other dial up device or a land line system such as ISDN or DSL. The modem connects to a central office or point of presence POP which in turn transmits the return path data over the Internet to the data center .

The server system communicates bi directionally with the network devices via the Internet or closed network connection such as frame relay to a central office or point of presence POP . In one embodiment the Internet connection between the server system and the central office is over a Virtual Private Network VPN providing a private secure encrypted connection tunnel.

The network devices are connected to the Internet by the central office via Digital Subscriber Lines DSL .

In brief overview the server system includes a management console a system manager a data store a queue manager a message router a bulk data transfer manager and an XML file processor . The embedded client system executing in the network devices include a web browser a system agent a promotion notification agent a queue manager a logging agent and a bulk data transfer agent .

In more detail the management console is preferably implemented as a web server. In one embodiment of the present invention the management console is a Microsoft Internet Information Server IIS implementing Active Server Pages ASP .

The management console provides upon request by a system administrator a web page interface for specifying the content to deploy the attributes of a group profile that target a market segment of potential consumers installation information and criteria for activating the content or displaying the promotions at the network devices. Upon submitting the web page the management console communicates with the system manager via an Application Programming Interface API to store the targeted group profile activation criteria and the content and promotions to the data store . In one embodiment the API is a Microsoft COM interface.

Content includes but is not limited to applications device drivers data files registry sub hives and promotions. Promotions are a special type of content that advertise goods and services. Promotions overlay the video display of a network device with a graphic image or animated icon that launches a web browser to a host web server in response to the user clicking or selecting it. Promotions also include audio and video clips or data streams. One or more promotions can be displayed on the video display at one time.

The management console also provides a web page interface to users upon request during the initial registration of their network devices. Users will register through the web page interface providing data about themselves. Upon submitting the web page the management console communicates with the system manager via the COM interface to store the user data as attributes of a user profile. The attributes of the user profile are associated with the attributes of the group profile in order to target potential consumers who would be interested in the content or promotions.

The system manager is an application level process that manages the reading and writing of data to the data store . The system manager through its COM interface allows the management console to store user profiles content including promotions along with associated group profiles installation information and activation criteria. In addition the system manager updates the user and group profiles whenever new attributes are received.

The system manager also interacts with the system agent of the targeted network devices by sending and receiving messages through a messaging protocol. The interaction of the system manager and the system agent implement the scheduling of content deployment as well as installation and activation of the content. In one embodiment the system manager is implemented as a Microsoft COM object.

The queue manager is an application level process that communicates with the message router on behalf of other processes such as the system manager in order to send and receive messages among the embedded client systems . In one embodiment the queue manager is implemented as a C object. The queue manager also manages incoming and outgoing queues on behalf of the other processes in the system server .

The queue manager handles two types of queues persistent queues and volatile queues. Messages whose message type indicates persistent storage are stored such that the message will not be lost during power outages and lost network connections. A persistent queue is stored in persistent flash memory or in a location on the hard disk of the network device. Other messages not intended for persistent storage are stored to volatile queues and might be lost during power outage and lost network connections.

The data store is a database that stores the attributes of the user profiles group profiles content and promotions along with the activation criteria. In addition the data store stores messages intended for network devices that are unavailable during the initial delivery attempt. The data store provides persistence to the data stored such that the content profiles and messages will not be lost during a power outage. In one embodiment the data store is a Microsoft SQL version 7 database. Since the data store stores content it is also known as a content store.

The bulk data transfer manager is an application level process that is responsible for the transfer of bulk data to targeted network devices. Bulk data include large stream oriented data such as a promotions files or registry sub key hives. The bulk data transfer manager does not transmit data over the messaging protocol. Instead it transmits serialized data over a network transport protocol such as TCP IP. The bulk data transfer manager has access to the data store for transmitting content and promotions.

The XML File Processor is an application level process that is responsible for parsing out the user attributes from the raw user activity and event logs and updating the appropriate user profiles. In one embodiment the logs are stored as XML files in the data store .

In more detail of the embedded client system the system agent is an application level process that communicates with the system manager handling various request messages and registration. In handling the various request messages the system agent communicates with the other embedded client system components in order to affect a proper response or behavior. In one embodiment the system agent is implemented as a C object.

As in the system server the queue manager is an application level process that communicates with the message router on behalf of other processes such as the system agent in order to send and receive messages to the system server and other network devices. In one embodiment the queue manager is implemented as a C object. The queue manager also manages incoming and outgoing queues on behalf of the other processes in the embedded client system .

The queue manager handles two types of queues persistent queues and volatile queues. Messages whose message type indicates persistent storage are stored such that the message will not be lost during power outages and lost network connections. A persistent queue is stored in persistent flash memory or in a location on the hard disk of the network device. Other messages not intended for persistent storage are stored to volatile queues and might be lost during power outage and lost network connections.

The bulk data transfer agent is an application level process that handles requests from the system agent to either download content and promotions or upload user activity and event logs. The bulk data transfer agent communicates with the bulk data transfer manager of the system server over a network transport protocol such as TCP IP. The bulk data transfer agent notifies the system agent upon completion or failure of the data transfer. In one embodiment the system agent is implemented as a C object.

The promotion notification agent is an application level process that triggers and handles the display of promotions. The promotion notification agent overlays the promotion or promotions onto the video signal that gets displayed on a monitor connected to a set top box or to a web phone display. The promotion notification agent coordinates the activation of promotions. A promotion notification agent will display the promotion in response to an event invocation by the system manager or scheduling information provided with the promotion itself.

The web browser is an application level process that displays web pages from web host servers such as the management console of the system server enabling registration of user attributes.

The logging agent is an application level component that monitors and logs a variety of user activities and events. In one embodiment the logging agent stores the log files in XML format. User activities and events that are tracked by the logging agent are channel events promotion events power events peripheral events and application events.

Channel events occur whenever the network device stays tuned to a channel for a configurable amount of time. Promotion events occur in response to consumer actions taken with respect to promotions displayed on the video display. For example a promotion event is recorded when the consumer clicks or selects the promotion icon to navigate to the web server hosting the promotion.

The interaction of the server system and the embedded client system provides a system for targeting and scheduling deployment of promotional content to consumers of a targeted market segment for managing the activation of the promotional content and for tracking consumer response to the promotion.

Application level processes such as the system manager of the server system and the system agent of the network device communicate over the data network through messages.

Messages transfer requests for action responses to requests and small data transfers. Messages are transported in the payload of a network transport protocol such as TCP IP. Messages are sent to destinations using a globally unique identifier GUID in order to identify the destination network device or application. This messaging protocol allows application level processes to transmit data without knowing about the network transport interface the device s network address or whether the device is active on the data network.

The interaction of the message router with the queue managers of the source and destination processes implements the messaging protocol. Any queue manager whether it is executing on the system server or the embedded client system communicates with the message router in the same manner.

In step the queue manager stores the message in a queue for the system manager and then attempts to establish a connection with the message router .

In brief overview there are three steps in order for the queue manager to establish a connection to the message router . In step the queue manager determines the IP address of the message router . In step the queue manager creates and opens a socket pair connection to the message router for transmitting serialized data. In step the queue manager sends a message to the message router indicating that the queue manager is alive and connected and ready to transmit serialized data.

In more detail of step the queue manager has one of its properties being the location or name of the message router . Using DNS or IP host name services the queue manager determines the IP address of the message router . If the queue manager cannot resolve the IP address of the message router the queue manager resorts to a broadcasting scheme. The queue manager broadcasts a locator message on its subnet attempting to locate the message router . If there is a message router on that subnet the message router responds back with its IP address. This address is cached by the queue manager for future connections.

In step the queue manager knowing the IP address of the message router creates and opens a socket pair on predetermined known ports for transmitting serialized data.

In step once the socket pair is opened the queue manager sends a message notifying the message router that the queue manager is alive and connected and has socket pairs on which to read or write serialized data.

In step the queue manager writes the message for delivery to the message router through the established TCP IP socket connection

Upon completion of the writing of the message the message router extracts the message type and the destination GUID from the message in step .

In step the message router resolves the destination GUID by looking up the IP address associated with the GUID in the data store .

In step the message is encapsulated in an IP packet with the appropriate destination IP address. In one embodiment the IP address of the network device becomes known to the system server during initial registration of the network device and is stored as an attribute of the user profile.

In step the message router determines the type of the message. The message type indicates the quality of service that the message router provides for delivery of the message.

If the message type is a standard datagram the message router simply transmits the message in step . The message router will not keep track of whether the message was actually received.

If the message type indicates guaranteed delivery the message router will transmit the message and wait for an acknowledgment from the destination device in step .

If no acknowledgment is received after several attempts the destination is deemed unavailable and the message is stored in the data store for later retransmission when the destination is active on the data network in step . Specifically in step the message router waits for the network device to become active in order to deliver the message. In one embodiment the message router is notified that the network device is active by receiving a message from the network device indicating its active status. In an alternative embodiment the message router is notified of the active status of a previously unavailable network device by the system manager which monitors the status of the network devices . When the network device becomes active the message router proceeds back to step to begin the process of delivery again.

If the acknowledgment is received then in step the delivery is complete and the message is removed from the data store if the network device was previously unavailable.

The interaction of the message router and the queue manager for delivering messages occurs whenever a message is sent or received using the messaging protocol.

In order for the server system to target content and promotions to a particular market segment the server system references its stored user profiles each user profile being a collection of user and device attributes associated with a network device. All network devices whose user profiles match the attributes of the group profile targeted by a system administrator are scheduled for content deployment.

However when a network device is connected to the network infrastructure for the first time the system server does not have a user profile for the network device. The present invention provides an automated system and method for initially registering and generating a user profile for a network device.

In step the system agent of the network device generates and transmits a registration request message containing a number of device attributes to the system manager .

The device attributes describes the network device and is configured during the manufacturing process of the device itself. For example the network device may be configured with a model number attribute for a particular group of network devices such as intelligent set top boxes version 1.0.

In step the system manager receives the registration request message and in response retrieves a globally unique identifier GUID from an available pool of GUIDs stored in the data store .

In step the system manager generates and transmits a registration response message containing the assigned GUID to the system agent of the registering device.

The assigned GUID is used by the network device to identify itself in messages transmitted to the system server and to other network devices. The assigned GUID is also used by the system server to associate the network device with a user profile within the data store .

In step the system agent launches a web browser . The web browser transmits an HTTP request to the URL Uniform Resource Locator of the management console for a registration web page. The assigned GUID is included in the URL string in order to identify the registering network device.

In step the management console receives the HTTP request. In response the management console makes a call via the COM interface of the system manager to retrieve the device and user attributes if any associated with the GUID of the registering network device. The management console generates the registration web page customized for the registering network device. The web page is transmitted via HTTP to the web browser .

In step the web browser displays the registration web page wherein the user submits information which will be used to generate a user profile of user attributes associated with the network device. Such information includes but is not limited to name and address information channels frequently watched requests for installation of optional value add services and applications and various demographic and personal information. Upon submitting the registration data the web browser transmits the user attributes represented as HTML data via HTTP to the management console .

In step the management console interprets the HTML data stream and makes calls via the COM interface of the system manager to update the user profiles in the data store with the provided user attributes.

In step the system manager updates the user profile of the registering network device with the user attributes on the data store . After updating the user profile the system manager associates the user profile with group profiles whose attributes match user attributes of the user profile.

For example the user profile will be added to the group profile for network devices with the same model number attribute. The user profile is added to any number of group profiles that target particular attributes of the registered user or network device. These group profiles are used by the system manager for targeting consumers of particular market segments for various e commerce promotions or application services.

Once the network device is registered and is associated with a user profile the device is capable of being targeted for deployment of content or promotions.

Before content can be deployed to a targeted device the content must be stored in the data store along with a group profile and an activation schedule. The group profile indicates the attributes of network devices to target. The activation schedule indicates when to activate the content or promotions. Activation can be event driven scheduled from the system server or initiated by the system manager .

In step a system administrator with access to the management console populates a server based web page indicating the content to deploy as well as the criteria with which to define the group profile. Additionally the system administrator indicates when to activate the content. Upon submitting the data the management console makes a call to the COM interface of the system manager to generate a group profile in the data store with user profiles whose attributes match the criteria defined by the system administrator.

In step the system manager updates the data store creating the group profile and populating the group profile with user profiles with matching attributes.

In step the management console make a call through the COM interface of the system manager to download the content or promotion to the data store .

The system manager is configured to schedule deployment of content during off peak hours when bandwidth utilization is typically at a minimum. For example during the hours of 3 00 AM and 5 00 AM more bandwidth is available for efficient deployment of content and promotions. Alternatively the system manager monitors network utilization and is configured to schedule deployment of content when the detected bandwidth utilization falls below a predetermined level.

In step the system manager sends a download and install request message to each of the system agents of the network devices whose user attributes match the attributes of the group profile. The download and install message informs the system agent to download install the content or promotion referenced by a GUID.

Alternatively the system manager sends a download install and start request message which indicates in addition when or under what event conditions the content should be activated i.e. promotion displayed or an application launched .

In step the system agent makes a C object method call to the bulk data transfer agent to download the content having the provided GUID.

In step the bulk data transfer agent sets up a TCP IP socket connection to the bulk data transfer manager of the server system to initiate the delivery of the application.

In step the bulk data transfer manager delivers the requested content to the bulk data transfer agent through the TCP IP socket connection. In cases where the connection is broken the bulk data transfer agent and the bulk data transfer manager can detect that a connection was broken and will continue the download the content from the point in the transfer where the break occurred.

In step the bulk data transfer agent notifies the system agent the result of the data transfer via an C object method call.

In step the system agent sends a message to the system manager indicating the result of the data transfer.

After the content is installed on the targeted network device the present invention provides a system and method for activating that content. Activation allows the user to interact with the installed content such as playing a game or initiating an e commerce transaction.

There are two types of activation that the present invention implements scheduled activation and event driven activation. Scheduled activation allows the system administrator to specify when to activate the content whereas event driven activation allows the system administrator to specify an event which triggers the activation of the content.

Scheduled activation is implemented in two ways predetermined scheduling and activation by the system server.

In step when the group profiles are configured and the content is downloaded to the data store the system administrator also specifies the date and time to activate the content. Where the content is a promotion a duration period is specified along with the activation date and time.

In step the system manager sends the download install and start request message to the system agent of a targeted network device. In addition to requesting the system agent to install content the message indicates the date and time to activate the installed content.

If the content is a not a promotion the system agent waits for the specified activation date and time in step .

If the content is a promotion the system agent transfers the predetermined date time and duration to the promotion notification agent in step .

In step the promotion is activated by the promotion notification agent at the specified activation date and time.

If the promotion is a icon or graphic linked to a URL of a host web server the promotion notification agent overlays the promotion on a portion of the video display built in or attached to the network device. If the promotion is audio clip or data stream the audio is played through a speaker built in or attached to the network device. If the promotion is a video clip or data stream the video overlays a portion of the video display built in or attached to the network device.

As described previously the content is installed on the network device in step with no activation information.

In step upon request of the system administrator the system manager sends a start message to the system agent specifying the installed content to activate.

If the installed content is not a promotion the system agent activates the content in response to receiving the message in step . This may include but not limited to launching an application installed within the network device.

If the installed content is a promotion the system agent notifies the promotion notification agent via a C object method call to activate the specified promotion in step .

Event driven activation is particularly suited for coordinating the activation of content with a particular event or a particular moment in a corresponding analog and or digital video stream.

Event activation has advantages associated with high scalability. The content can be loaded in the days or weeks proceeding the general time period when it is to be displayed.

In one embodiment events that trigger content activation are channel events power events and peripheral events. A power event is an event relating to the power supply such as the network device being powered on or off. A peripheral event is an event relating to peripheral devices being connected or disconnected from the network device such as a joy stick or other gaming console. A channel event is an event relating to the channel being watched by the user.

In step when the group profiles are configured and the content is downloaded to the data store the system administrator also specifies an event map. An event map associates events to content indicating when to activate the content. Where the content is a promotion a duration period is specified as well.

In step the system manager sends the event map in a message such as a download install and start message to the system agent of a targeted network device.

If the content is not a promotion the system agent waits for the specified event or events that trigger the activation of the content in step .

Conversely if the content is a promotion the system agent transfers the event map to the promotion notification agent in step .

In step the promotion notification agent activates the promotions associated with the event or events that occurred.

An example of event driven activation is where the event map provides for the activation of promotions involving sporting goods when the potential consumer has been watching a particular sports channel for a period of time. The watching of the sports channel for a period of time triggers a channel event. The channel event triggers the activation of the promotion or promotions.

The present invention provides an additional implementation of event driven activation involving technology from ATVEF Advanced Television Enhancement Forum . ATVEF provides a standard for embedding HTML tags within a video signal.

The promotion content agent monitors the video signal for the embedded triggers such as the HTML tag. The capture of this embedded trigger causes the activation of one or more promotions in real time coinciding with the video signal.

Such a system has advantages in that very little video signal editing is required. Only a small trigger has to be embedded in the video signal requiring little analog video editing capabilities at the data center.

The content is simultaneously activated on all of the network devices allowing high levels of synchronization to the video signal. For example the promotion can be synchronized to occur during a television commercial.

The provider of the commercial simply embeds an initialization or start HTML tag within its video signal. In response to the promotion notification agent capturing the HTML tag the promotion notification agent activates the appropriate promotion or promotions specified in the event map for that HTML tag.

The promotion content agent of the embedded client system monitors the video stream for the embedded trigger signal. When the trigger signal is detected the promotion content agent inserts the associated graphical promotion content indicated in the event map into the analog or digital video stream to the display of the television . As a result the promotion appears on the display screen overlaying the video.

User selection of this promotion through a selecting device such as a remote control device sends a URL to the web browser bringing the browser window to the forefront of the display of the television . In this way user selection of the promotion allows the user to receive and view data from the URL enabling e commerce transactions.

Therefore the event driven activation as well as the other scheduling options presents promotions in an appropriate context to further increase the likelihood of consumer e commerce transactions.

In addition to the initial registration process the present invention includes a system and method for updating user profiles through uploading distributed user activity and event logs to the system server parsing out the user and device attributes from the logs and updating the user profiles in the data store .

The logs provide useful information because the logs track a variety of information which the system can use in order to more accurately target users for content and promotional deployment. In one embodiment the logs track channel events and e commerce transactions initiated through the display of promotions. In another embodiment the logs track peripheral events such as the addition of a joystick and console for gaming purposes power events application events and promotion events. Continuous updating of user profiles through this system and method improves the targeting of consumers for content deployment and in particular for promotional content deployment.

In brief overview the network device includes a logging component that monitors and logs user activity and events in an generic file format. For example the logging component monitors user activity at a user interface device such as the television remote channel control. In one embodiment the generic file format is Extensible Markup Language XML . The format of the log files using XML corresponds to the structure of the user profiles in the data store . This allows for processing of the logs in an automated fashion.

In addition the user activity and event logs include a description of the structure of the document itself. Using XML the description of the structure of the document is the Document Type Definition DTD . Providing a description of the document structure within the logs themselves allows for the server system to process logs with different document structures. This avoids the necessity of having to update the server system every time a new document structure is used within the logs.

The uploading and parsing of these user activity and event logs will provide additional user attributes for targeting consumers including information regarding responses to prior promotions. If the logs indicate that a user is interested in a particular type of promotion the system server modifies the user attributes of his user profile such that they match the attributes of a group profile associated with that type of promotion.

In step the system manager sends a message to the system agent to upload its activity logs to the server system.

In step the system agent makes a C object method call to the bulk data transfer agent to upload the user activity and event logs.

In step the bulk data transfer agent sets up a TCP IP socket connection to the bulk data transfer manager of the server system to initiate the delivery of the logs.

In step the bulk data transfer agent delivers the logs to the bulk data transfer manager through the TCP IP socket connection where they are stored in the data store .

In cases where the connection is broken the bulk data transfer agent and the bulk data transfer manager can detect that a connection was broken and will continue the download the content from the point in the transfer where the break occurred.

In step the bulk data transfer agent notifies the system agent the result of the data transfer via a C object method call.

In step the system agent sends a message to the system manager indicating the result of the data transfer.

In step the system manager makes a call to the XML file processor to update the user profiles from the user activity and event logs.

In step an XML file processor at the server system parses the logs stored on the database and updates the user attributes of the user profile of the network device. This system and method for scheduling remote uploads of the user activity and event logs provides improves the efficiency for targeting consumers for content and promotion.

There are situations where a user will change the hardware configuration of a network device in order to expand its capabilities. In that situation the present invention provides a system and method by which the network device notifies the server system of a change to its hardware configuration and in return receives the appropriate device drivers to support the new hardware configuration.

Specifically the dynamic driver installation process is triggered when the user installs a peripheral device on a network device for which the network device requires a driver. In the typical example the process occurs when the user plugs in a peripheral device such as a joy stick into a port such as a serial port or USB universal serial bus port.

In step the system agent intercepts the plug and play string from the peripheral device when it is attached to the USB port.

In step the system agent then sends this plug and play string to the system manager via the message router and the queue managers along the path between the system agent and the system manager .

In step the system manager then searches for a matching driver in its data store . Specifically it compares the plug and play string received from the network device to plug and play strings of supported operating systems and supporting peripheral devices for which drivers are available.

In step assuming the valid device driver has been located the system manager sends a message to the system agent to download the driver providing its location in the data store .

In step the system agent requests the bulk data transfer agent on the network device to download the driver. The bulk data transfer agent then contacts the bulk data transfer manager and downloads and stores the device driver on the network device. In parallel the system manager instructs the system agent on how to install the device driver on the network device.

In step in the typical implementation the device driver is dynamically loaded onto the network device.

In step when the driver has been successfully installed the system agent notifies the system manager . The system manager in turn updates the status of the network device in the system manager s data store .

In step the system agent is notified when the peripheral is disconnected by the user from the network device.

In step typically the bulk data transfer agent obtains the uninstalled program from the bulk data transfer manager .

In step upon the successful uninstall the system agent notifies the system manager that the driver has been installed and the system manager updates the network device s status.

While this invention has been particularly shown and described with references to preferred embodiments thereof it will be understood by those skilled in the art that various changes in form and details may be made therein without departing from the scope of the invention encompassed by the appended claims.

