---

title: System and method for enhanced message routing
abstract: Coincident with the evolution, maturation, etc. of (e.g., Short Message Service, Multimedia Message Service, IP Multimedia Subsystem, etc.) wireless messaging ecosystems an infrastructure that provides, in new and creative ways, enhanced message routing capabilities. The dynamic, flexible, and extensible nature of the enhanced message routing capabilities support, among other things, very large volumes of messaging traffic, numerous billing paradigms, different Quality of Service levels and possible charges for same, improved troubleshooting and problem investigation capabilities, etc. The infrastructure may optionally leverage the capabilities of a centrally-located Messaging Inter-Carrier Vendor.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08224361&OS=08224361&RS=08224361
owner: Sybase 365, Inc.
number: 08224361
owner_city: Reston
owner_country: US
publication_date: 20080617
---
This application claims the benefit of U.S. Provisional Patent Application No. 60 945 174 filed on Jun. 20 2007 which is herein incorporated by reference in its entirety.

The present invention relates generally to telecommunications services. More particularly the present invention relates to capabilities that enhance substantially the value and usefulness of various messaging paradigms including inter alia Short Message Service SMS Multimedia Message Service MMS Internet Protocol IP Multimedia Subsystem IMS etc.

As the wireless revolution continues to march forward the importance to a Mobile Subscriber MS for example a user of a Wireless Device WD such as a mobile telephone a BlackBerry etc. that is serviced by a Wireless Carrier WC of their WD grows substantially.

One consequence of the growing importance of WDs is the resulting ubiquitous nature of WDs i.e. MSs carry them at almost all times and use them for an ever increasing range of activities.

Over the past many years that ubiquitousness has driven a steady annual increase year over year in the number of SMS MMS etc. messages that have been exchanged by and between WDs. That steady increase shows no sign of abating. For example as reported by the industry group CTIA see the world wide web site ctia.org in the U.S. there were over 158 billion SMS messages sent during 2006 representing a 95 increase over 2005 and there were over 2.7 billion MMS messages sent during 2006 representing a 100 increase over 2005 .

As the volume of messaging has increased in the past and at present continues to increase it has become more and more important for all of the different entities that process messages e.g. WCs intermediaries enterprises Content Providers CPs Service Providers SPs etc. to route messages in the most flexible and efficient manner possible.

In the past the routing of a message was fairly rigid and may have consisted of examining just the destination address e.g. the destination Telephone Number TN of the message. Today and in the future the routing of a message needs to operate in as optimal a fashion as possible needs to be much more flexible and needs to take into account many more elements beyond just for example a destination TN all to support possibly inter alia very large volumes of messaging numerous billing paradigms different Quality of Service QoS levels and possible charges for same improved troubleshooting and problem investigation capabilities etc.

The challenges that were described above highlight the need for an innovative infrastructure that offers as part of the natural evolution maturation etc. of a wireless messaging ecosystem enhanced message routing capabilities.

The present invention provides such an infrastructure and addresses various of the not insubstantial challenges that are associated with same.

In one embodiment of the present invention there is provided a method for routing a wireless message including receiving at a gateway an incoming message said incoming message containing at least a destination address and having been originally initiated as a wireless message including said destination address performing one or more processing steps on said incoming message including at least a resolving said destination address yielding a resolved destination address and b generating a tag said tag containing at least a digest value said digest value based on at least one or more of aspects of said destination address and aspects of said resolved destination address querying a local cache for the presence of said digest value said local cache preserving for a digest value at least a route selection generating an outgoing message said outgoing message being based on at least said route selection and aspects of said incoming message and dispatching said outgoing message.

In the embodiment said wireless message or outgoing message is one of a a Short Message Service message b a Multimedia Message Service message or c an IP Multimedia Subsystem message and said destination address is one of a a telephone number b a short code c a SIP address or d an e mail address.

Further resolving said destination address includes accessing one or more of a a composite routing database and b a real time query facility.

The tag may contain one or more of a a type indicator b a version number c a digest value and d a qualifier.

Still in accordance with the embodiment the method includes preserving aspects of the addressing of said incoming message as preserved address elements. These preserved address elements may include one or both of a source address information and b destination address information and may further include one or more of a an Internet Protocol address b a Transmission Control Protocol port number and c a User Datagram Protocol port number when said incoming message is received through an Internet Protocol based communication paradigm.

The preserved address elements may still further include one or more of a a point code and b a subsystem number when said incoming message is received through a Signaling System Number 7 based communication paradigm.

These and other features of the embodiments of the present invention along with their attendant advantages will be more fully appreciated upon a reading of the following detailed description in conjunction with the associated drawings.

It should be understood that these figures depict embodiments of the invention. Variations of these embodiments will be apparent to persons skilled in the relevant art s based on the teachings contained herein.

Aspects of the present invention may be offered as a value add service by a centrally located full featured MICV facility. Reference is made to U.S. Pat. No. 7 154 901 entitled INTERMEDIARY NETWORK SYSTEM AND METHOD FOR FACILITATING MESSAGE EXCHANGE BETWEEN WIRELESS NETWORKS and its associated continuations for a description of a MICV a summary of various of the services functions etc. that are performed by a MICV and a discussion of the numerous advantages that arise from same. The disclosure of U.S. Pat. No. 7 154 901 along with its associated continuations is incorporated herein by reference.

As illustrated in and reference numeral a MICV is disposed between possibly inter alia multiple WCs WC WC on one side and multiple SPs SP SP on the other side and thus bridges all of the connected entities. A MICV thus as one simple example may offer various routing formatting delivery value add etc. capabilities that provide possibly inter alia 

1 A WC WC WC and by extension all of the MSs that are serviced by the WC WC WC with ubiquitous access to a broad universe of SPs SP SP and

2 A SP SP SP with ubiquitous access to a broad universe of WCs WC WC and by extension to all of the MSs that are serviced by the WCs WC WC .

Generally speaking a MICV may have varying degrees of visibility e.g. access etc. to the MS MS MS SP etc. messaging traffic 

1 A WC may elect to route just their out of network messaging traffic to a MICV. Under this approach the MICV would have visibility e.g. access etc. to just the portion of the WC s messaging traffic that was directed to the MICV by the WC.

2 A WC may elect to route all of their messaging traffic to a MICV. The MICV may possibly among other things subsequently return to the WC that portion of the messaging traffic that belongs to i.e. that is destined for a MS of the WC. Under this approach the MICV would have visibility e.g. access etc. to all of the WC s messaging traffic.

While aspects of the present invention may be offered by a MICV it will be readily apparent to one of ordinary skill in the relevant art that numerous other arrangements are equally applicable e.g. aspects of the present invention may be offered by a third party service bureau by an element of a WC or a landline carrier by an enterprise by a SP or by a CP by multiple third party entities working together etc. and indeed are fully within the scope of the present invention.

To help illustrate aspects of the present invention consider the simplified MPI that is presented in and reference numeral . A MPI may exist within any or all entities such as possibly inter alia a MICV a WC an enterprise a SP or a CP etc. In brief a MPI may interact with Entities E E . . . E such as possibly inter alia a MICV or a WC or an enterprise or a CP or a SP or a etc. to 

1 Receive incoming SMS MMS etc. messages over any combination of one or more communication paradigms or channels including possibly inter alia IP SS7 etc. .

3 Send outgoing SMS MMS etc. messages over any combination of one or more communication paradigms or channels including possibly inter alia IP SS7 etc. 

1 A Gateway . Behind the facade of a single consolidated Gateway a dynamically updateable set of one or more software processes not explicitly depicted in the diagram handle incoming traffic and outgoing traffic. Incoming traffic is accepted and deposited on an intermediate or temporary Incoming Queue IQ IQ in the diagram for subsequent processing. Processed artifacts are removed from an intermediate or temporary Outgoing Queue OQ OQ in the diagram and then dispatched.

2 Incoming Queues IQ IQ . A dynamically updateable set of one or more IQs IQ IQ operate as intermediate or temporary buffers for incoming traffic.

3 WorkFlows WF WF . A dynamically updateable set of one or more WFs WF WF remove incoming traffic from an intermediate or temporary IQ IQ IQ perform all of the required processing operations and deposit processed artifacts on an intermediate or temporary OQ OQ OQ . The WF component will be described more fully below.

4 Outgoing Queues OQ OQ . A dynamically updateable set of one or more OQs OQ OQ operate as intermediate or temporary buffers for outgoing traffic.

5 An Administrator . An Administrator provides possibly inter alia management or administrative control over all of the different system components e.g. IQs IQ IQ WFs WF WF OQs OQ OQ etc. a facility through which configuration information for possibly inter alia one or more system components may be dynamically updated etc. An Administrator may provide as one example a Web based interface it will be readily apparent to one of ordinary skill in the relevant art that numerous other interfaces e.g. a data feed an Application Programming Interface API etc. are easily possible.

6 In Memory Databases In Memory Database In Memory Database . A dynamically updateable set of one or more instances of an in memory database facility In Memory Database In Memory Database may provide possibly inter alia very high performance access to possibly among other things a a local cache and b aspects of the information that is maintained in a Composite Routing Database CRD .

7 A Real Time Query Facility RTQF . When it is necessary to retrieve information about a destination address e.g. a destination TN a RTQF may employ any combination of one or more channels such as SS7 User Datagram Protocol UDP IP Electronic Numbering ENUM Transmission Control Protocol TCP IP etc. to complete such retrievals. Reference is made to U.S. Pat. No. 7 154 901 entitled INTERMEDIARY NETWORK SYSTEM AND METHOD FOR FACILITATING MESSAGE EXCHANGE BETWEEN WIRELESS NETWORKS and its associated continuations for a description of how such a facility may provide possibly among other things support for the authoritative determination of a servicing WC given a TN a for any country i.e. any TN numbering scheme around the world and b that fully accounts for complexities such as Mobile Number Portability MNP regimes.

8 A CRD . A consolidated repository that maintains possibly inter alia raw processed etc. authoritative routing data.

It will be readily apparent to one of ordinary skill in the relevant art that numerous other components and or numerous alternative component arrangements are possible. For example 

1 The different database environments that are depicted in FIG. e.g. the In Memory Databases In Memory Database In Memory Database and the CRD are logical representations of the possibly multiple physical repositories that might be implemented. The physical repositories may be implemented through any combination of conventional Relational Database Management Systems RDBMSs such as Oracle through Object Database Management Systems ODBMSs through in memory Database Management Systems DBMSs or through any other equivalent facilities.

2 A Gateway may maintain a repository e.g. a database into which selected details of all administrative processing etc. activities may be recorded. Among other things such a repository may be used to support scheduled e.g. daily weekly etc. and or on demand reporting with report results delivered to for example an Entity E E . . . E through possibly inter alia any combination of one or more channels such as the World Wide Web WWW via for example a dedicated Web site wireless messaging SMS MMS etc. Electronic Mail E Mail messages Instant Messaging IM conventional mail telephone Interactive Voice Response IVR facility etc.

Through flexible extensible and dynamically updatable configuration information a WF component may be quickly and easily realized to support any number of activities. For example WFs might be configured to support various internal processing steps please see below to support the generation and dispatch of response etc. messages to support various billing transactions to support the generation of scheduled and or on demand reports etc. The specific WFs that were just described are exemplary only it will be readily apparent to one of ordinary skill in the relevant art that numerous other WF arrangements alternatives etc. are easily possible.

An illustrative internal processing sequence that may be realized as a WF might include the following steps 

2 Based on a set of flexible extensible and dynamically configurable rules extract various data elements from the incoming message and preserve the data elements in an IMO. Such rules will preferably employ leverage etc. aspects of Feature Extraction i.e. means for possibly inter alia the flexible extraction and aggregation of data from dynamic content as taught in U.S. patent application Ser. No. 10 709 475 and its continuations. For purposes of illustration consider the following two examples 

A As illustrated in and reference numeral an incoming SMS message is received via the Short Message Peer to Peer SMPP communication paradigm. Using and reference numeral as one possible scenario data elements or fields in the IMO are populated with values from the data elements or fields from the incoming IP TCP SMPP message 

B As illustrated in and reference numeral an incoming SMS message is received via SS7. Using and reference numeral as one possible scenario data elements or fields in the IMO are populated with values from the data elements or fields from the incoming SS7 Message Signal Unit MSU 

Numerous other examples dealing with possibly inter alia the receipt of other message types such as for example MMS etc. the use of other communication paradigms such as for example Computer Interface to Message Distribution Version 2 CIMD2 External Machine Interface EMI Universal Computer Protocol UCP etc. and the user of other transit protocols such as for example UDP etc. are obviously easily possible.

3 Based on a set of flexible extensible and dynamically configurable rules process the IMO. For example through possibly inter alia the CRD resolve the Source Address to identify possibly inter alia a source WC and or the Destination Address to identify possibly inter alia a destination WC .

4 Based on a set of flexible extensible and dynamically configurable rules generate a Tag and preserve the Tag within the IMO i.e. IMO Tag . For a general description of a Tag see U.S. patent application Ser. No. 10 709 475 and its continuations. As illustrated in and reference numeral a Tag may contain possibly inter alia a Type value e.g. possibly M for message a Version Number e.g. possibly 0 for backwards compatibility a Digest Value e.g. possibly the output of a one way or hash function such as a modified version of MD5 or LOOKUP3 and a Qualifier e.g. an optional value that ensures the uniqueness of the Tag . It will be readily apparent to one of ordinary skill in the relevant art that numerous other Tag elements and or numerous alternative Tag element arrangements are easily possible. For purposes of illustration consider the following two examples 

A An SMS message is received from a WD with TN 703 555 1234 that is serviced by WC XYZ and addressed to the WD with 202 555 9876 that is serviced by WC ABC . The Digest Value is defined to consist of the source WC i.e. XYZ and the destination WC i.e. ABC . The Tag might consist of 

B An SMS message is received from a WD with TN 703 555 1234 that is serviced by WC XYZ and addressed to the WD with 202 555 9876 that is serviced by WC ABC . The Digest Value is defined to consist of the source WC i.e. XYZ and the destination TN i.e. 202 555 9876 . The Tag might consist of 

Numerous other examples dealing with possibly inter alia different data elements or fields etc. are obviously easily possible.

It will be readily apparent to one of ordinary skill in the relevant art that numerous other local cache elements and or numerous alternative local cache element arrangements are easily possible. Does the Digest Value of the instant Tag exist in the local cache If yes then retrieve the value of the preserved Route Selection and proceed to Step 7.

6 Using a set of flexible extensible and dynamically configurable rules complete a Route Selection process. Such a process may include or consider possibly inter alia any number of data elements or fields in an IMO system configuration information such as defined delivery paths constraints such as Day of Week DoW Time of Day ToD etc. factors such as current system loads and QoS levels paradigms such as Least Cost Routing LCR etc. Such a process may include one or more defined hooks to support possibly inter alia various billing events. The generated Route Selection may be preserved by possibly inter alia placing it in the local cache e.g. by associating it with the instant Digest Value recording it in a Message Detail Record MDR repository e.g. by associating it with the instant Tag value etc.

7 From the IMO construct an outgoing message and based on possibly inter alia the Route Selection deposit the outgoing message on an OQ. Various of the particulars of the outgoing message may be preserved by possibly inter alia updating one or more entries in a MDR repository.

The specific processing activities that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other processing activities are easily possible and indeed are fully within the scope of the present invention. For example 

1 The Header and or Body of an IMO may contain other data elements or fields over and above what were depicted in and reference numeral and and reference numeral including possibly inter alia one or more date and time values data value encoding flags priority indicators etc. For example the IMO that was presented in and reference numeral contains just one Destination IP Address field. Alternatively such an IMO might contain multiple Destination IP Address fields e.g. a Initial Destination IP Address field that might be populated with for example the value of IP Packet Destination IP Address from an incoming message one or more Intermediate Destination IP Address fields that might be populated with for example the IP Address of each of the different systems that contribute to the routing and processing of the instant IMO and a Final Destination IP Address field that might be populated with for example the IP Address of the recipient system of a dispatched outgoing message . In a similar fashion such an IMO might contain multiple Destination Port Number fields e.g. a Initial Destination Port Number field one or more Intermediate Destination Port Number fields and a Final Destination Port Number field. In like fashion in the case of the SS7 based IMO that is presented in and reference numeral multiple Destination Point Code fields might be defined.

2 As noted above numerous other Tag elements and or numerous alternative Tag element arrangements are easily possible. Additionally a Tag s Digest Value may be defined to consist of any combination of a number of items e.g. a destination WC and a QoS level a destination WC and a DoW indicator and a ToD indicator etc.

3 A MDR repository may preserve a wide range of information for each message that is processed including for example IMO data elements or fields such as Tag value source and destination address TN Short Code etc. date and time etc. portions of constructed outgoing messages etc. and may as one possible example be keyed or indexed by Tag value.

4 Numerous alternative supporting facilities are easily possible within a MPI. For example a Service ID might be defined to encompass possibly inter alia a particular class of messaging for a specific WC e.g. Standard SMS messaging from Carrier XYZ Standard SMS messaging to Carrier XYZ etc. a repository of Service IDs that are defined configured etc. within an infrastructure might be maintained and Service ID might be included a as a data element or field within an IMO b as a Tag element c within the flexible extensible and dynamically configurable rules d etc. As another example a Destination ID might be defined to encompass possibly inter alia a particular message transit channel for a specific WC e.g. Message channel 819 from Carrier ABC Message channel 237 to Carrier ABC etc. a repository of Destination IDs that are defined configured etc. within an infrastructure might be maintained and Destination ID might be included a as a data element or field within an IMO b as a Tag element c within the flexible extensible and dynamically configurable rules d etc. Numerous other supporting facilities are obviously easily possible. It will be readily apparent to one of ordinary skill in the relevant art that such supporting facilities may possibly inter alia be combined in any number of ways e.g. a Service ID might subsume one or more Destination IDs a Tag s Digest Value might be defined to include Service ID and Destination ID etc.

The processing activities that were described above may be implemented through and consequently supported by any combination of a number of technologies etc. For example 

1 An IMO may be implemented through any combination of a number of facilities including possibly inter alia flat files in memory data structures etc. For example within a Java Message Service JMS environment an IMO might be implemented as a JMS message with possibly inter alia the different data elements or fields that were described above realized as individual JMS message properties.

2 The flexible extensible and dynamically configurable rules that were described above e.g. for data element extraction for IMO processing for Tag generation for Route Selection processing etc. may be implemented through any combination of a number of facilities including possibly alia conventional programming constructs such as for example C Java C Perl etc. regular expressions custom or proprietary solutions etc.

The advantages benefits etc. of the message routing model that has been described above include possibly inter alia 

1 Performance. For example subsequent Route Selection retrievals from a local cache may be completed very quickly. This benefit is particularly valuable in a Peer to Peer P2P messaging environment where there is traditionally a balance of trade i.e. if MSsends a message to MSthen it is likely that MSwill reply to MS after which MSwill likely send another message to MSand MSwill again reply after which etc.

2 Value add services. For example as noted previously a Gateway may maintain a repository e.g. a database into which selected details of all administrative processing etc. activities may be recorded to support the subsequent generation of scheduled e.g. daily weekly etc. and or on demand reports. Additionally aspects of the present invention including possibly inter alia the extraction of data elements from an incoming message the processing of an IMO the generation of a Tag value etc. may support enhanced troubleshooting problem investigation etc. capabilities through possibly inter alia the preservation and exposure of a plethora of data elements and those capabilities may as just one example be associated with different offered QoS levels and possible charges for same e.g. one may pay more for the faster etc. routing of a message and pay less for the slower etc. routing of a message .

3 Flexibility and extensibility. For example dynamically configurable sets of rules for as an example the extraction of data elements from an incoming message the processing of an IMO the generation of a Tag value etc. contribute significantly to a responsive open etc. MPI.

During the processing steps that were described above one or more billing transactions may optionally be completed e.g. for each request that is received for various of the processing steps that are performed for each response returned etc. A billing transaction may take any number of forms and may involve different external entities e.g. a WC s billing system a carrier billing system service bureau a credit or debit card clearinghouse etc. . A billing transaction may include possibly inter alia 

1 The appearance of a line item charge on the bill or statement that for example an Entity may receive from their WC. Exemplary mechanics and logistics associated with this approach are described in pending U.S. patent application Ser. No. 10 837 695 entitled SYSTEM AND METHOD FOR BILLING AUGMENTATION. Other ways of completing or performing line item billing are easily implemented by those skilled in the art.

The report etc. messages that were described above may optionally contain an informational element e.g. a relevant or applicable factoid etc. The informational element may be selected statically e.g. all generated messages are injected with the same informational text randomly e.g. a generated message is injected with informational text that is randomly selected from a pool of available informational text or location based i.e. a generated message is injected with informational text that is selected from a pool of available informational text based on the current pysical location of the recipient of the message as derived from as one example a Location Based Service LBS facility .

The report etc. messages may optionally contain advertising e.g. textual material if a simple channel is being utilized or multimedia images of brand logos sound video snippets etc. material if a more capable channel is being utilized. The advertising material may be selected statically e.g. all generated messages are injected with the same advertising material randomly e.g. a generated message is injected with advertising material that is randomly selected from a pool of available material or location based i.e. a generated message is injected with advertising material that is selected from a pool of available material based on the current physical location of the recipient of the message as derived from as one example a LBS facility .

The report etc. messages may optionally contain promotional materials e.g. still images video clips etc. .

The discussion that was just presented referenced two specific wireless messaging paradigms SMS and MMS. These paradigms potentially offer an incremental advantage over other paradigms for example native support for SMS and MMS is commonly found on a WD that a potential MS would be carrying. However it is to be understood that it would be readily apparent to one of ordinary skill in the relevant art that numerous other paradigms such as possibly inter alia IMS etc. are fully within the scope of the present invention.

The foregoing disclosure of the preferred embodiments of the present invention has been presented for purposes of illustration and description. It is not intended to be exhaustive or to limit the invention to the precise forms disclosed. It will be readily apparent to one of ordinary skill in the relevant art that numerous alternatives to the presented embodiments are easily possible and indeed are fully within the scope of the present invention.

