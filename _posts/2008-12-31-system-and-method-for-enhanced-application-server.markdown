---

title: System and method for enhanced application server
abstract: A flexible, extensile, and dynamically configurable back-end Application Server environment that efficiently supports the ever-increasing range of activities for which mobile subscribers employ their wireless devices. The environment may operate within any number of entities within a messaging ecosystem including for example a service provider.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09209994&OS=09209994&RS=09209994
owner: Sybase, Inc.
number: 09209994
owner_city: Dublin
owner_country: US
publication_date: 20081231
---
The present application is related to concurrently filed U.S. patent application Ser. No. 12 347 354 entitled SYSTEM AND METHOD FOR MESSAGE BASED CONVERSATIONS which is incorporated herein by reference in its entirety.

The present application is related to concurrently filed U.S. patent application Ser. No. 12 347 223 entitled SYSTEM AND METHOD FOR MOBILE USER AUTHENTICATION which is incorporated herein by reference in its entirety.

The present invention relates generally to telecommunications services. More particularly the present invention relates to capabilities that enhance substantially the value and usefulness of various messaging paradigms including inter alia Short Message Service SMS Multimedia Message Service MMS etc.

As the wireless revolution continues to march forward the importance to a Mobile Subscriber MS for example a user of a Wireless Device WD such as a cellular telephone a BlackBerry a Palm Pilot etc. that is serviced by a Wireless Carrier WC of their WD grows substantially.

One consequence of such a growing importance is the resulting ubiquitous nature of WDs i.e. MSs carry them at almost all times and use them for an ever increasing range of activities.

Coincident with the expanding presence of WDs has been the explosive growth of messaging a steady annual increase year over year in the number of SMS MMS etc. messages that have been exchanged by and between WDs. That steady increase shows no sign of abating. For example as reported by the industry group CTIA see ctia.org on the World Wide Web WWW in the U.S. there were over 158 billion SMS messages sent during 2006 representing a 95 increase over 2005 and there were over 2.7 billion MMS messages sent during 2006 representing a 100 increase over 2005 .

Additionally MSs would like to be able to use their WDs to engage in and complete increasingly more complicated activities beyond for example exchanging simple messages with their friends receiving one way news weather financial etc. notifications etc. e.g. inquiring as to the current balance of an account at a financial institution transferring funds between accounts within a financial institution paying a bill etc. Many of those activities require a coordinated exchange of multiple SMS MMS etc. messages supported by a robust back end system.

Given 1 the ubiquitous nature of WDs 2 the popularity of SMS MMS etc. messaging and 3 the need for MSs to use their WDs to engage in and complete increasingly more complicated activities it would be desirable to have a flexible extensile and dynamically configurable back end Application Server AS environment.

Aspects of the present invention facilitate such an AS environment in new creative and unconventional ways and address various of the not insubstantial challenges that are associated with same.

In one embodiment of the present invention there is provided an application server system containing possibly inter alia a gateway at which an incoming message is received an incoming queue on which at least aspects of the incoming message are deposited workflow modules which may a retrieve the aspects of the incoming message from the incoming queue b complete one or more processing steps and c deposit an entry on an outgoing queue a gateway from which at least aspects of the entry is transmitted after the entry is retrieved from the outgoing queue a repository and an administrator.

These and other features of the embodiments of the present invention along with their attendant advantages will be more fully appreciated upon a reading of the following detailed description in conjunction with the associated drawings.

Throughout the drawings a like reference numbers generally indicate identical or functionally similar elements and b the left most digit s of a reference number generally identify the drawing in which the reference number first appears. For example in reference numeral would direct the reader to for the first appearance of that element.

It should be noted that the embodiments that are described below are merely exemplary of the invention which may be embodied in various forms. Therefore the details that are disclosed below are not to be interpreted as limiting but merely as the basis for possibly inter alia a teaching one of ordinary skill in the relevant art how to make and or use the invention and b the claims.

The present invention may leverage the capabilities of a centrally located full featured MICV facility. Reference is made to U.S. Pat. No. 7 154 901 entitled Intermediary network system and method for facilitating message exchange between wireless networks and its associated continuations for a description of a MICV a summary of various of the services functions etc. that are performed by a MICV and a discussion of the numerous advantages that arise from same. U.S. Pat. No. 7 154 901 and its associated continuations are hereby incorporated by reference in their entirety.

2 Multiple SPs SP SP entities that may possibly inter alia provide a range of services products etc. to MSs on the other side and thus bridges all of the connected entities. A MICV thus as one simple example may offer various routing formatting delivery value add etc. capabilities that provide possibly inter alia 

1 A WC and by extension all of the MSs that are serviced by the WC with ubiquitous access to a broad universe of SPs and

2 A SP with ubiquitous access to a broad universe of WCs and by extension to all of the MSs that are serviced by the WCs .

Generally speaking a MICV may have varying degrees of visibility e.g. access etc. to the MS MS MS SP etc. messaging traffic 

1 A WC may elect to route just their out of network messaging traffic to a MICV. Under this approach the MICV would have visibility e.g. access etc. to just the portion of the WC s messaging traffic that was directed to the MICV by the WC.

2 A WC may elect to route all of their messaging traffic to a MICV. The MICV may possibly among other things subsequently return to the WC that portion of the messaging traffic that belongs to i.e. that is destined for a MS of the WC. Under this approach the MICV would have visibility e.g. access etc. to all of the WC s messaging traffic.

While the discussion below will include a MICV it will be readily apparent to one of ordinary skill in the relevant art that other arrangements are equally applicable and indeed are fully within the scope of the present invention.

In the discussion below aspects of the present invention will be described and illustrated as being offered by a SP i.e. as noted above an entity that may possibly inter alia provide a range of services products etc. to MSs . A SP may for example be realized as an independent service bureau an element of or within some organization such as possibly inter alia a financial institution a retail establishment an on line retailer etc. an element of a WC or a landline carrier an element of a MICV multiple entities such as for example those just listed or aspects of same working together etc.

In the discussion below reference will be made to messages that are sent for example between a MS and a SP. As set forth below a given message sent between a MS and a SP may actually comprise a series of steps in which the message is received forwarded and routed between different entities including possibly inter alia a MS a WC a MICV and a SP. Thus unless otherwise indicated it will be understood that reference to a particular message generally includes that particular message as conveyed at any stage between an origination source such as for example a MS and an end receiver such as for example a SP. As such reference to a particular message generally includes a series of related communications between for example a MS and a WC a WC and a MICV a MICV and a SP etc. The series of related communications may in general contain substantially the same information or information may be added or subtracted in different communications that nevertheless may be generally referred to as a same message. To aid in clarity a particular message whether undergoing changes or not is referred to by different reference numbers at different stages between a source and an endpoint of the message.

To better understand the particulars of the present invention consider for a moment a simple hypothetical example SPoffers a service that has been enhanced or augmented as provided through aspects of the instant invention and Mary a MS uses SP s service.

SP Billing Interface BI . A single consolidated interface that SP may use to easily reach possibly inter alia one or more internal and or external entities such as a credit card or debit card clearinghouse a carrier billing system a service bureau that provides access to multiple carrier billing systems invoicing or billing facilities etc.

SP AS . Facilities that provide key elements of the instant invention which will be described below .

SP Gateway GW . A facility through which SPN may exchange possibly inter alia SMS MMS etc. messages with possibly inter alia a MICV .SP Gateway GW .

It is important to note that while in the MS WD and MS PC entities are illustrated as being adjacent or otherwise near each other in actual practice the entities may for example be physically located anywhere.

In the exchanges that are collected under the designation Set represent the activities that might take place as Mary completes a registration process with SP 

A Mary uses one of her PCs to visit a WS of SP to possibly among other things complete a service registration process see .

B A WS of SP interacts with an AS of SP to possibly among other things commit some or all of the information that Mary provided to one or more data repositories e.g. a databases optionally initiate a billing transaction etc. see .

D After receiving a response from an AS of SP a WS of SP responds appropriately e.g. with the presentation of a confirmation message etc. see .

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example the collected information may be reviewed confirmed etc. through one or more manual and or automatic mechanisms. For example the registration process may be completed through any combination of one or more channels including inter alia the WWW wireless messaging SMS MMS etc. Electronic Mail E Mail messages Instant Messaging IM conventional mail telephone an Interactive Voice Response IVR facility etc.

During the registration process described above a range of information may be captured from a MS including possibly inter alia 

A Identifying Information. For example possibly among other things name address age landline and wireless Telephone Numbers TNs E Mail addresses IM names identifiers a unique identifier and a password etc.

B Account Information. For example possibly among other things various of the particulars for one or more of a MS accounts with organizations such as possibly inter alia utility companies financial institutions on line retailers etc. . The particulars may include possibly inter alia organization name and contact details account number account access credentials etc.

C Security Service Information. For example possibly among other things the selection of one or more of the different security plans programs policies etc. that a SP may optionally offer each of which may carry possibly inter alia some type of fee or charge . Such plans programs etc. may provide possibly inter alia alerts to a MS via for example SMS MMS E Mail IM etc. based on various events criteria thresholds etc. additional levels of notification confirmation etc. during a transaction etc.

D Billing Information. For example the particulars such as possibly inter alia name account routing etc. numbers etc. for financial institution bank brokerage etc. accounts credit cards debit cards etc. As well possibly the selection of one or more of the different service billing models may be offered by a SP including inter alia a fixed one time charge a recurring monthly etc. fixed charge a recurring monthly etc. variable charge a per transaction charge etc. and possibly the selection of one or more of the different payment mechanisms that may be offered by a SP including possibly among other things credit or debit card information authorization to place a charge on a MS s phone bill authorization to deduct funds from a MS bank brokerage etc. account etc. .

The specific pieces of information that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other pieces of information e.g. additional Identifying Information scheduled daily weekly etc. reporting desired and or on demand reporting desired etc. are easily possible and indeed are fully within the scope of the present invention.

As noted above the information that Mary provided during the registration process may be preserved in a data repository e.g. a database and may optionally be organized as a MS Profile.

The content of Mary s profile may be augmented by SP to include as just a few examples of the many possibilities internal and or external demographic psychographic sociological etc. data.

As noted above a SP s BI may optionally complete a billing transaction. The billing transaction may take any number of forms and may involve different external entities e.g. a WC s billing system a carrier billing system service bureau a credit or debit card clearinghouse a financial institution etc. . The billing transaction may include inter alia 

In the exchanges that are collected under the designation Set represent the activities that might take place as SP optionally coordinates etc. with one or more external entities to possibly among other things secure access exchange and or confirm collected information arrange to receive updates etc. see . During such exchanges SP may employ any combination of one or more of possibly inter alia an Application Programming Interface API an interface layer an abstraction layer communication protocols Extensible Markup Language XML documents etc.

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges including inter alia updates to various of the information in a MS Profile in a SP s repository etc. are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set represent the activities that might take place as an AS of SP dispatches to Mary one or more confirmation E Mail messages see .

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges including inter alia the dispatch of multiple E mail messages i.e. multiple instances of the sequence the reply by Mary to a received E mail message etc. are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set represent the activities that might take place as an AS of SP dispatches one or more confirmation SMS MMS etc. messages to a WD of Mary and Mary optionally replies or responds to the message s . Of interest and note are 

2 SPN may employ a Short Code SC or a regular TN as its source address and to which it would ask users of its service to direct any reply messages . While the abbreviated length of a SC e.g. five digits for a SC administered by Neustar under the Common Short Code CSC program incrementally enhances the experience of a MS e.g. Mary need remember and enter only a few digits as the destination address of a reply message it also by definition constrains the universe of available SCs thereby causing each individual SC to be a limited or scarce resource and raising a number of SC CSC management etc. issues. A description of a common i.e. universal short code environment may be found in pending U.S. patent application Ser. No. 10 742 764 entitled Universal Short Code administration facility. 

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

The Set Set Set and Set exchanges that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example possibly inter alia aspects of the registration information that was described above may subsequently be managed e.g. existing information may be edited or removed new information may be added etc. through any combination of one or more channels including inter alia a WWW facility wireless messaging SMS MMS etc. E Mail messages IM exchanges conventional mail telephone IVR facilities etc. Additionally aspects of the registration information may be exchanged with one or more entities such as possibly inter alia a 3P such as a financial institution a retail establishment an on line retailer an employer a utility company etc. another SP etc. .

To continue with our hypothetical example . . . as Mary goes about her daily activities there may arise numerous instances where she would like to use her WD to perform some activity. For example 

2 Mary may wish to complete the payment portion of a purchase from for example an on line retailer etc. .

3 Mary may wish to transfer money between various of her bank brokerage credit card etc. accounts transfer money from one of her bank brokerage credit card etc. accounts to someone else transfer money to someone else perhaps another MS with the amount of the transfer along with for example charges fees etc. appearing on her WC statement etc.

The specific examples that were cataloged above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other examples are easily possible and indeed are fully within the scope of the present invention.

Third Party 3P . An organization such as possibly inter alia a financial institution a retail establishment an on line retailer an employer a utility company etc.

As noted previously while the discussion below presents aspects of the instant invention as being offered by a SP working together with a 3P it will be readily apparent to one of ordinary skill in the relevant art that numerous other arrangements e.g. all of the activities that are described below being supported just by a SP all of the activities that are described below being supported just by a 3P various of the activities that are described below being supported by one or more SPs working together with one or more 3Ps etc. are equally applicable and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set represent the activities that might take place as Mary employs her WD to initiate conduct conclude etc. an activity with a 3P see e.g. perform an account balance inquiry request a funds transfer operation pay a bill etc. During her activity Mary may optionally include information such as access credentials e.g. user identification and password .

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example the sequence may be repeated any number of times.

In the exchanges that are collected under the designation Set represent the activities that might take place as 3P completes a range of internal processing activities including possibly inter alia validating any supplied information such as for example access credentials determining the need for enhanced security interacting with external entities etc. During its processing activities 3P may among other things possibly leverage 

1 One or more repositories containing information about Mary e.g. as previously collected during a registration process as previously received from one or more external entities etc. .

2 A body of dynamically updateable configuration information or data for among other things the different types of supported transactions available security policies mappings for different levels of authentication etc. .

3 Bodies of flexible extensible and dynamically configurable logic or rules capturing among other things the particulars when how etc. governing the application of different levels of security .

In instant example 3P may interact with an AS of SP see . Such an interaction may employ among other things any combination of one or more of possibly inter alia an API an interface layer an abstraction layer communication protocols XML documents etc. and may include among other things information about Mary such as for example identifier access credentials the address e.g. TN of her WD etc. etc.

AS of SP may complete a range of internal processing activities after which one or more message requests may be directed to a GW of SP see where one or more SMS MMS etc. messages containing possibly inter alia updates information etc. may be dispatched to a WD of Mary see .

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example among other things 

1 SP may obtain the address e.g. the TN of the WD of Mary through any number of means including for example from 3P as described above from one or more repositories within SP possibly leveraging registration information that was provided by Mary and which was supplied to SP either directly or indirectly etc.

2 In any dispatched messages SP may employ any number of addresses including possibly inter alia a SC a TN etc. to which it would ask users to direct any reply messages.

3 SP may optionally confirm to 3P and or one or more other entities the dispatch of one or more SMS MMS etc. messages.

4 A dispatched message may optionally contain possibly inter alia descriptive or explanatory text confirmation information contact information a request to call e.g. a help center at a particular TN etc.

5 Mary may optionally reply to one or more of the received SMS MMS etc. messages. Based on any received replies SP may optionally complete one or more additional processing steps.

The Set and Set exchanges that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example 

1 A MS may optionally need to acknowledge a received message by for example replying to same . Such an acknowledgement may optionally need to occur within a defined period of time after which an unacknowledged message may possibly inter alia go stale and not be usable .

2 A SP may incorporate additional factors criteria tests etc. during various of its processing activities e.g. confirmation authentication etc. including possibly inter alia MS Location Based Service LBS and or Global Positioning System GPS information biometric information etc.

3 During its different activities an SP may complete any number of billing reporting etc. transactions.

4 An SP may track a MS usage aggregate same optionally offer to the MS to external entities such as a 3P etc. discounts rebates surcharges etc. based on the tracked usage etc.

5 During its processing steps an AS may employ any combination of a number of automated e.g. through software solutions and or manual e.g. through human intervention actions techniques capabilities etc. and each of the techniques strategies capabilities etc. that were described above may have associated with it possibly inter alia an optional set of weighting scoring confidence etc. factors that may be used either individually or together to develop results.

The catalog of processing steps activities etc. that was described above is illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other processing steps activities etc. are easily possible and indeed are fully within the scope of the present invention.

The notification confirmation response etc. message s that were described above may optionally contain an informational element e.g. a relevant or applicable factoid etc. The informational element may be selected statically e.g. all generated messages are injected with the same informational text randomly e.g. a generated message is injected with informational text that is randomly selected from a pool of available informational text or location based i.e. a generated message is injected with informational text that is selected from a pool of available informational text based on the current physical location of the recipient of the message as derived from as one example a LBS GPS etc. facility .

The notification confirmation response etc. message s that were identified above may optionally contain advertising e.g. textual material if an SMS model is being utilized or multimedia images of brand logos sound video snippets etc. material if an MMS model is being utilized. The advertising material may be selected statically e.g. all generated messages are injected with the same advertising material randomly e.g. a generated message is injected with advertising material that is randomly selected from a pool of available material or location based i.e. a generated message is injected with advertising material that is selected from a pool of available material based on the current physical location of the recipient of the message as derived from as one example a LBS GPS etc. facility .

The notification confirmation response etc. message s that were identified above may optionally contain promotional materials e.g. still images video clips etc. .

A dynamically updateable set of one or more Gateways GW GW in the diagram handle incoming SMS MMS etc. messaging management calls administrative calls programmatic calls function or service invocations etc. traffic and outgoing SMS MMS etc. messaging management calls administrative calls programmatic calls function or service invocations etc. traffic . Incoming traffic and or outgoing traffic may encompass among other things any combination of one or more of possibly inter alia an APIs interface layers abstraction layers communication protocols XML documents raw or unformatted data etc. For example a GW may support the receipt of incoming SMS MMS etc. messaging traffic and the dispatch of outgoing SMS MMS etc. messaging traffic via any combination of one or more of the available public and or proprietary messaging paradigms including possibly inter alia Short Message Peer to Peer SMPP Computer Interface to Message Distribution CIMD External Machine Interface EMI Universal Computer Protocol UCP Signaling System Seven SS7 Mobile Application Part MAP MM4 MM7 etc.

Incoming traffic is accepted and deposited on an intermediate or temporary Incoming Queue IQ IQ in the diagram for subsequent processing. Processed artifacts are removed from an intermediate or temporary Outgoing Queue OQ OQ in the diagram and then dispatched .

A dynamically updateable set of one or more Incoming Queues IQ IQ in the diagram and a dynamically updateable set of one or more Outgoing Queues OQ OQ in the diagram operate as intermediate or temporary buffers for incoming and outgoing traffic .

A dynamically updateable set of one or more WorkFlows WorkFlow WorkFlow in the diagram possibly inter alia remove incoming traffic from an intermediate or temporary Incoming Queue IQ IQ in the diagram perform all of the required processing operations and deposit processed artifacts on an intermediate or temporary Outgoing Queue OQ OQ in the diagram . The WorkFlow component will be described more fully below.

The Database that is depicted in is a logical representation of the possibly multiple physical repositories that may be implemented to support inter alia configuration profile monitoring alerting etc. information. The physical repositories may be implemented through any combination of conventional Relational Database Management Systems RDBMSs such as Oracle through Object Database Management Systems ODBMSs through in memory Database Management Systems DBMSs or through any other equivalent facilities.

An Administrator that is depicted in provides management or administrative control over all of the different components of an AS through as one example a WWW based interface . It will be readily apparent to one of ordinary skill in the relevant art that numerous other interfaces e.g. a data feed an API etc. are easily possible. Among other things an Administrator may control launch start quiesce halt etc. various of an AS components e.g. IQ OQ WorkFlow etc. .

Through flexible extensible and dynamically updatable configuration information a WorkFlow component may be quickly and easily realized to support any number of activities. For example WorkFlows might be configured to support a registration process to support interactions with external entities to support various internal processing steps to support the generation and dispatch of confirmation etc. messages to support various billing transactions to support the generation of scheduled and or on demand reports to support the generation validation etc. of security credentials etc. The specific WorkFlows that were just described are exemplary only it will be readily apparent to one of ordinary skill in the relevant art that numerous other WorkFlow arrangements alternatives etc. are easily possible.

1 A WorkFlow component may leverage one or more dynamically updateable XML repositories for possibly inter alia configuration startup operation etc. information.

2 A WorkFlow component may optionally automatically re start itself whenever some portion of its configuration information is altered.

3 A WorkFlow component may for example be stateless be thread safe offer a range of lifecycle administrative logging performance reporting etc. programmatic interfaces etc.

4 A WorkFlow component may be derived from a base or underlying class or set of classes that provide possibly inter alia fundamental lifecycle e.g. start stop initialization termination etc. logging administration and management identification and location performance monitoring reporting etc. capabilities.

5 A WorkFlow s base or underlying class may implement an Interceptor fa ade which possibly inter alia wraps or encapsulates a WorkFlow allowing for the selective interception of information that flows in to and or out of a WorkFlow to for example allow for selective extensions enhancements etc. .

For purposes of exposition and reference numeral depict an illustrative AuditService class that might reside within a portion of an AS as realized under aspects of the present invention and and reference numeral present an illustrative Java language code snippet from a service factory through which an instance of for example an aspect of a WorkFlow might be secured under a factory paradigm .

A SP may maintain a repository e.g. a database into which selected details of all administrative messaging etc. activities may be recorded. Among other things such a repository may be used to support 

1 Scheduled e.g. daily weekly etc. and or on demand reporting with report results delivered through SMS MMS etc. messages through E Mail through a WWW based facility etc.

2 Scheduled and or on demand data mining initiatives possibly leveraging or otherwise incorporating one or more external data sources with the results of same presented through Geographic Information Systems GISs visualization etc. facilities and delivered through SMS MMS etc. messages through E Mail through a WWW based facility etc.

Various aspects of the present invention can be implemented by software firmware hardware or any combination thereof. illustrates an example computer system in which the present invention or portions thereof such as described above under paragraphs 38 76 paragraphs 82 105 and paragraphs 110 127 can be implemented as computer readable code. Various embodiments of the invention are described in terms of this example computer system . After reading this description it will become apparent to a person skilled in the relevant art how to implement the invention using other computer systems and or computer architectures.

Computer system includes one or more processors such as processor . Processor can be a special purpose processor or a general purpose processor. Processor is connected to a communication infrastructure for example a bus or a network .

Computer system also includes a main memory preferably Random Access Memory RAM containing possibly inter alia computer software and or data .

Computer system may also include a secondary memory . Secondary memory may include for example a hard disk drive a removable storage drive a memory stick etc. A removable storage drive may comprise a floppy disk drive a magnetic tape drive an optical disk drive a flash memory or the like. A removable storage drive reads from and or writes to a removable storage unit in a well known manner. A removable storage unit may comprise a floppy disk magnetic tape optical disk etc. which is read by and written to by removable storage drive . As will be appreciated by persons skilled in the relevant art s removable storage unit includes a computer usable storage medium having stored therein possibly inter alia computer software and or data .

In alternative implementations secondary memory may include other similar means for allowing computer programs or other instructions to be loaded into computer system . Such means may include for example a removable storage unit and an interface . Examples of such means may include a program cartridge and cartridge interface such as that found in video game devices a removable memory chip such as an Erasable Programmable Read Only Memory EPROM or Programmable Read Only Memory PROM and associated socket and other removable storage units and interfaces which allow software and data to be transferred from the removable storage unit to computer system .

Computer system may also include an input interface and a range of input devices such as possibly inter alia a keyboard a mouse etc.

Computer system may also include an output interface and a range of output devices such as possibly inter alia a display one or more speakers etc.

Computer system may also include a communications interface . Communications interface allows software and or data to be transferred between computer system and external devices. Communications interface may include a modem a network interface such as an Ethernet card a communications port a Personal Computer Memory Card International Association PCMCIA slot and card or the like. Software and or data transferred via communications interface are in the form of signals which may be electronic electromagnetic optical or other signals capable of being received by communications interface . These signals are provided to communications interface via a communications path . Communications path carries signals and may be implemented using wire or cable fiber optics a phone line a cellular phone link a Radio Frequency RF link or other communications channels.

As used in this document the terms computer program medium computer usable medium and computer readable medium generally refer to media such as removable storage unit removable storage unit and a hard disk installed in hard disk drive . Signals carried over communications path can also embody the logic described herein. Computer program medium and computer usable medium can also refer to memories such as main memory and secondary memory which can be memory semiconductors e.g. Dynamic Random Access Memory DRAM elements etc. . These computer program products are means for providing software to computer system .

Computer programs also called computer control logic are stored in main memory and or secondary memory . Computer programs may also be received via communications interface . Such computer programs when executed enable computer system to implement the present invention as discussed herein. In particular the computer programs when executed enable processor to implement the processes of aspects of the present invention such as the steps discussed above under paragraphs 38 76 paragraphs 82 105 and paragraphs 110 127. Accordingly such computer programs represent controllers of the computer system . Where the invention is implemented using software the software may be stored in a computer program product and loaded into computer system using removable storage drive interface hard drive or communications interface .

The invention is also directed to computer program products comprising software stored on any computer useable medium. Such software when executed in one or more data processing devices causes data processing device s to operate as described herein. Embodiments of the invention employ any computer useable or readable medium known now or in the future. Examples of computer useable mediums include but are not limited to primary storage devices e.g. any type of random access memory secondary storage devices e.g. hard drives floppy disks Compact Disc Read Only Memory CD ROM disks Zip disks tapes magnetic storage devices optical storage devices Microelectromechanical Systems MEMS nanotechnological storage device etc. and communication mediums e.g. wired and wireless communications networks local area networks wide area networks intranets etc. .

It is important to note that while aspects of the discussion that was presented above referenced the use of SCs and TNs it will be readily apparent to one of ordinary skill in the relevant art that other address identifiers such as for example Session Initiation Protocol SIP Address Uniform Resource Locator URL etc. are equally applicable and indeed are fully within the scope of the present invention.

The discussion that was just presented referenced two specific wireless messaging paradigms SMS and MMS. Those paradigms potentially offer an incremental advantage over other paradigms in that native support for SMS and or MMS is commonly found on a WD that a potential MS would be carrying. However it is to be understood that it would be readily apparent to one of ordinary skill in the relevant art that numerous other paradigms such as for example Internet Protocol IP Multimedia Subsystem IMS IM E Mail WAP etc. are fully within the scope of the present invention.

It is important to note that the hypothetical example that was presented above which was described in the narrative and which was illustrated in the accompanying figures is exemplary only. It is not intended to be exhaustive or to limit the invention to the specific forms disclosed. It will be readily apparent to one of ordinary skill in the relevant art that numerous alternatives to the presented example are easily possible and indeed are fully within the scope of the present invention.

