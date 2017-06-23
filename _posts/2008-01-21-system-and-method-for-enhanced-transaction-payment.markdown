---

title: System and method for enhanced transaction payment
abstract: An infrastructure that leverages established wireless messaging paradigms (such as, possibly inter alia, Short Message Service, Multimedia Message Service, Wireless Application Protocol, IP Multimedia Subsystem, etc.) to provide, in new and creative ways, an enhanced level of security for the payment element or portion of a transaction—for example, a transaction within Mobile Commerce (M-Commerce, which, broadly speaking, encompasses the buying and selling of merchant-supplied products, goods, and services through wireless devices), a purchase in the checkout lane of a brick-and-mortar store, a purchase at a (fast-food or other) restaurant, etc. The infrastructure may optionally leverage the capabilities of a centrally-located Messaging Inter-Carrier Vendor.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08712375&OS=08712375&RS=08712375
owner: Sybase 365, Inc.
number: 08712375
owner_city: Dublin
owner_country: US
publication_date: 20080121
---
This application claims the benefit of U.S. Provisional Patent Application No. 60 897 843 filed on Jan. 29 2007 which is herein incorporated by reference in its entirety.

The present invention relates generally to telecommunications services. More particularly the present invention relates to capabilities that enhance substantially the value and usefulness of various messaging paradigms including inter alia Short Message Service SMS Multimedia Message Service MMS Internet Protocol IP Multimedia Subsystem IMS Wireless Application Protocol WAP etc.

As the wireless revolution continues to march forward the importance to a Mobile Subscriber MS for example a user of a Wireless Device WD for example a user of a Wireless Device WD such as inter alia a mobile telephone a BlackBerry etc. that is serviced by a Wireless Carrier WC of their WD grows substantially.

One consequence of such a growing importance is the resulting ubiquitous nature of WDs i.e. MSs carry them at almost all times and use them for an ever increasing range of activities.

Within the universe of ever increasing activities one of the specific activities for which MSs would like to employ their WDs encompasses the facilitation completion etc. of the payment element of a transaction purchase etc. for example a transaction within Mobile Commerce M Commerce which broadly speaking encompasses the buying and selling of merchant supplied products goods and services through WDs a purchase in the checkout lane of a brick and mortar store a purchase at a fast food or other restaurant etc.

Consequently the need exists for an infrastructure that allows MSs through their WDs to seamlessly participate in support facilitate complete etc. in new and creative ways payments for transactions across the diverse range of transaction types including among other things transactions that involve very small amounts of money all the way up to transactions that involve very large amounts of money .

The present invention provides such enhanced transaction payment capabilities and addresses in new and innovatory ways various of the not insubstantial challenges that are associated with same.

In one embodiment of the present invention there is provided a method for enhancing the security of a transaction payment in which a request message is received from a mobile subscriber where the request message is associated with a payment portion of a transaction and includes a payment amount.

The amount of the transaction is extracted and based thereon as well as based on information previously supplied by the mobile subscriber an authorization code is generated. The authorization code is then packaged in a response message and dispatched to the mobile subscriber

The request message and the response message may be any one of a a Short Message Service message b a Multimedia Message Service message and or c an IP Multimedia Subsystem message and may further include one or more of a an account identifiers and or b a password.

In accordance with one feature of the present invention the initial request may also initiate one or more of a one or more inquiries to the mobile subscriber b a low or an empty balance replenishment operation and or c mobile subscriber location awareness. The mobile subscriber location awareness may be derived from e.g. one or more of a Location Based Services and or b Global Positioning System.

In accordance with another feature of the present invention the information that is previously supplied by the mobile subscriber is provided during a registration process which may be web based

In accordance with an aspect of the present invention when the mobile subscriber receives the authorization code he she may then supply the code to a merchant with whom the mobile subscriber is transacting. The authorization code may so supplied via one or more of a manual means b Bluetooth c WiFi d Near Field Communication e Uniform Resource Locator and or f Web cookie.

In still another aspect of the present invention an approval code is generated perhaps by request of the merchant and returned to the merchant who may in turn pass the approval code to the mobile subscriber.

In accordance with another embodiment of the present invention there is provided a method of conducting a commercial transaction including the steps of receiving a single mobile subscriber initiated short message service SMS message the SMS message including a payment amount for a commercial transaction communicating with a billing interface to obtain an authorization code for the payment amount sending a response SMS message to the mobile subscriber the response SMS message including the authorization code receiving the authorization code from a party to the commercial transaction other than the mobile subscriber e.g. a merchant and generating an approval code based on the authorization code payment amount and at least one identifier and supplying the approval code to the party to the commercial transaction other than the mobile subscriber again e.g. the merchant .

In this embodiment the approval code may then be received from the mobile subscriber in an SMS message. In connection with supplying the approval code to the mobile subscriber it may be desirable also to confirm at that time that the mobile subscriber is in a same location as the merchant. In this way both the merchant and the mobile subscriber are confident that the commercial transaction is not fraudulent.

These and other features of the embodiments of the present invention along with their attendant advantages will be more fully appreciated upon a reading of the following detailed description in conjunction with the associated drawings.

It should be understood that these figures depict embodiments of the invention. Variations of these embodiments will be apparent to persons skilled in the relevant art s based on the teachings contained herein.

The present invention may leverage the capabilities of a centrally located full featured MICV facility. Reference is made to U.S. Pat. No. 7 154 901 entitled INTERMEDIARY NETWORK SYSTEM AND METHOD FOR FACILITATING MESSAGE EXCHANGE BETWEEN WIRELESS NETWORKS and its associated continuations for a description of a MICV a summary of various of the services functions etc. that are performed by a MICV and a discussion of the numerous advantages that arise from same. The disclosure of U.S. Pat. No. 7 154 901 along with its associated continuations is incorporated herein by reference.

As illustrated in and reference numeral a MICV is disposed between possibly inter alia multiple WCs WC WC on one side and multiple SPs SP SP on the other side and thus bridges all of the connected entities. A MICV thus as one simple example may offer various routing formatting delivery value add etc. capabilities that provide possibly inter alia 

1 A WC and by extension all of the MSs that are serviced by the WC with ubiquitous access to a broad universe of SPs and

2 A SP with ubiquitous access to a broad universe of WCs and by extension to all of the MSs that are serviced by the WCs .

A MICV may have varying degrees of visibility e.g. access etc. to the MS MS MS SP etc. messaging traffic 

1 A WC may elect to route just their out of network messaging traffic to a MICV . Under this approach the MICV would have visibility e.g. access etc. to just the portion of the WC s messaging traffic that was directed to the MICV by the WC .

2 A WC may elect to route all of their messaging traffic to a MICV . The MICV may possibly among other things subsequently return to the WC that portion of the messaging traffic that belongs to i.e. that is destined for a MS of the WC . Under this approach the MICV would have visibility e.g. access etc. to all of the WC s messaging traffic.

While the discussion below will include a MICV it will be readily apparent to one of ordinary skill in the relevant art that other arrangements are equally applicable and indeed are fully within the scope of the present invention.

In the discussion below the present invention is described and illustrated as being offered by a SP. A SP may possibly inter alia be realized as a third party e.g. a service bureau an element of a WC or a landline carrier an element of a MICV multiple entities working together etc.

To help explain key aspects of the present invention consider the illustrative example that is depicted through and the supporting narrative below.

As indicated in and reference numeral the SMS MMS etc. messaging traffic of numerous WCs WC WC is exchanged with a MICV and the MICV is connected with SP a SP that offers possibly inter alia the present invention.

Within the framework that is illustrated by SP may offer a registration process. During such a process a MS that is interested in using aspects of the present invention may identify herself and provide some range of information. A registration process may be tailored e.g. the range of information gathered the scope of access subsequently granted etc. to the class of user e.g. different types categories etc. of MSs may complete different registration processes.

SP Billing Interface BI . A single consolidated interface that SPmay use to easily reach inter alia one or more external entities such as a credit card or debit card clearinghouse a carrier billing system a service bureau that provides access to multiple carrier billing systems etc.

SP AS . Facilities that provide key elements of the instant invention which will be further described below .

It is important to note that while in the MS WD and MS PC entities are illustrated as being adjacent or otherwise near each other in actual practice the entities may for example be physically located anywhere.

It is also important to note that in the discussion to follow reference is made to messages that are sent for example between a MS and an SP . As set forth below a given message sent between a MS and a SP may actually comprise a series of steps in which the message is received forwarded and routed between different entities including a WD associated with a MS a WC a MICV and a SP . Thus unless otherwise indicated it will be understood that reference to a particular message generally includes that particular message as conveyed at any stage between an origination source such as a WD of a MS and an end receiver such as a SP . As such reference to a particular message generally includes a series of related communications between for example a MS and a WC the WC and a MICV and the MICV and a SP . The series of related communications may in general contain substantially the same information or information may be added or subtracted in different communications that nevertheless may be generally referred to as a same message. To aid in clarity a particular message whether undergoing changes or not is referred to by different reference numbers at different stages between a source and an endpoint of the message.

In the exchanges that are collected under the designation Set represent the activities that might take place as Mary begins a registration process with SP. For example 

A Mary uses one of her PCs to visit a WS of SP to possibly among other things complete a service registration process see .

B SP s WS interacts with SP s AS to possibly among other things commit some or all of the information that Mary provided to a data repository e.g. a database optionally complete a billing transaction etc. see .

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example the collected information may be reviewed confirmed etc. through one or more manual and or automatic mechanisms. For example the registration process may be completed through any combination of one or more channels including inter alia the indicated WWW facility wireless messaging SMS MMS IMS etc. E mail messages Instant Messaging IM exchanges conventional mail telephone Interactive Voice Response IVR facilities etc.

During the registration process that was described above a range of information may be captured from a candidate user including inter alia 

1 Identifying Information e.g. general information about Mary . For example possibly among other things a unique identifier and a password optionally a pseudonym or handle name age sex etc.

2 Contact Information. For example possibly among other things contact information such as possibly inter alia landline and or wireless Telephone Numbers TNs E mail addresses IM addresses physical addresses etc. .

3 Billing Information. Different service billing models may be offered by SPincluding possibly inter alia free e.g. possibly advertising based a fixed one time charge a recurring e.g. per transaction etc. fixed charge a recurring e.g. per transaction etc. variable charge etc. Different payment mechanisms may be supported by SPincluding possibly among other things credit or debit card information authorization to place a charge on a MS s phone bill etc.

4 Account Information. For example possibly among other things the particulars for one or more internal to SP accounts. The particulars might include possibly inter alia an account identifier account spending funding etc. limits or thresholds one or more funding sources e.g. cash one or more of the mechanisms that were identified in the above Billing Information etc. the particulars including possibly inter alia timing dollar amount source s etc. for periodic scheduled account replenishment or top up actions the particulars including possibly inter alia occurrence frequency size or dollar amount etc. for when additional or extra approval steps should be applied etc.

The specific pieces of information that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other pieces of information e.g. scheduled per transaction or daily weekly etc. reporting that may be desired etc. are easily possible and indeed are fully within the scope of the present invention.

As noted above the information that Mary provided during the registration process may be preserved in a data repository e.g. a database and may optionally be organized as a MS Profile.

The content of Mary s profile may optionally be augmented by SP. For example one or more internal or external sources of consumer demographic geographic psychographic corporate etc. information may be leveraged to selectively enhance or augment elements of Mary s profile.

As noted above a SP s BI may optionally complete one or more billing transactions. A billing transaction may take any number of forms and may involve different external entities e.g. a WC s billing system a carrier billing system service bureau a credit or debit card clearinghouse etc. . A billing transaction may include inter alia 

1 The placement of a line item charge on the bill or statement that a MS receives from her WC. Exemplary mechanics and logistics associated with this approach are described in for example pending U.S. patent application Ser. No. 10 837 695 entitled SYSTEM AND METHOD FOR BILLING AUGMENTATION. Other ways of completing or performing line item billing are easily implemented by those skilled in the art.

In the exchanges that are collected under the designation Set represent the activities that might take place as SP optionally coordinates etc. with one or more external entities such as for example one or more credit card clearinghouses etc. to possibly among other things secure access arrange for funds etc. see .

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges including inter alia updates to various of the information in a MS Profile in a SP s repository etc. are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set represent the activities that might take place as SP dispatches to Mary one or more confirmation E mail messages see .

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges including inter alia other types or forms of confirmation messages are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set represent the activities that might take place as SP s AS dispatches one or more confirmation SMS MMS IMS etc. messages to Mary s WD see and Mary replies or responds to the message s see . In the instant example the messages are shown traversing a MICV . SP may employ a Short Code SC or a regular TN as its source address and to which it would ask users of its service to direct any reply messages . While the abbreviated length of a SC e.g. five digits for a SC administered by Neustar under the Common Short Code CSC program incrementally enhances the experience of a MS e.g. the MS need remember and enter only a few digits as the destination address of a reply message it also by definition constrains the universe of available SCs thereby causing each individual SC to be a limited or scarce resource and raising a number of SC CSC management etc. issues. A description of a common i.e. universal short code environment may be found in pending U.S. patent application Ser. No. 10 742 764 entitled UNIVERSAL SHORT CODE ADMINISTRATION FACILITY. 

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

The Set Set Set and Set exchanges that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

The registration information that was described above may subsequently be managed e.g. existing information may be edited or removed new information may be added etc. through any combination of one or more channels including inter alia a SP s WWW facility wireless messaging SMS MMS IMS etc. e mail messages IM exchanges conventional mail telephone IVR facilities etc.

To continue with the explanation of key aspects of the present invention . . . consider one possible use or incarnation of aspects of the present invention. In this simple illustrative use Mary our hypothetical MS completes a registration process e.g. as described above subsequently enters a store completes her shopping in the store and then enters a checkout lane where her purchases are rung.

The simple scenario that was just described is illustrative only and it will be readily apparent to one of ordinary skill in the art that numerous other alternative scenarios are easily possibly and indeed are fully within the scope of the present invention. For example possibly inter alia 

4 Mary may secure services for her automobile at a gas or filling station at a repair or service facility etc.

The simple scenario that was described above i.e. Mary completes a registration process subsequently enters a store completes her shopping and enters a checkout lane where her purchases are rung may be examined further through the illustrative interactions that are depicted in and reference numeral . Of interest and note are the following entities 

SP BI . As noted above a single consolidated interface that a SP may use to easily reach inter alia one or more external entities such as for example a credit card or debit card clearinghouse a carrier billing system a service bureau that provides access to multiple carrier billing systems etc. .

SP AS . Facilities that provide key elements of the instant invention which will be described below .

M Back end System MBS . For example one or more back end billing inventory Point of Sale PoS etc. system s .

In the discussion to follow reference is made to messages that are sent for example between a MS and an SP . As set forth below a given message sent between a MS and a SP may actually comprise a series of steps in which the message is received forwarded and routed between different entities including a WD associated with a MS a WC a MICV and a SP . Thus unless otherwise indicated it will be understood that reference to a particular message generally includes that particular message as conveyed at any stage between an origination source such as a WD of a MS and an end receiver such as a SP . As such reference to a particular message generally includes a series of related communications between for example a MS and a WC the WC and a MICV and the MICV and a SP . The series of related communications may in general contain substantially the same information or information may be added or subtracted in different communications that nevertheless may be generally referred to as a same message. To aid in clarity a particular message whether undergoing changes or not is referred to by different reference numbers at different stages between a source and an endpoint of the message.

In the exchanges that are collected under the designation Set represent the activities that might take place as Mary while in the checkout lane receives from M possibly inter alia the dollar amount of her purchase see . The information may be conveyed to Mary manually e.g. verbally through a messaging exchange etc. and or automatically e.g. via Bluetooth via WiFi etc. .

It is important to note the Set exchanges that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible e.g. in an M Commerce environment information may be conveyed through possibly inter alia cookies Uniform Resource Locators URLs etc. and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set represent the activities that might take place as Mary users her WD see to compose and dispatch a SMS MMS etc. request message see the message is routed by Mary s WC to a MICV see and then directed by the MICV to SP see and the message is received and processed by SP specifically by an AS of SP .

To provide context for the next portion of our example we take a brief detour and describe an illustrative SP AS.

A dynamically updateable set of one or more Gateways GW GW in the diagram handle incoming SMS MMS IMS etc. messaging etc. traffic and outgoing SMS MMS IMS etc. messaging etc. traffic . Incoming traffic is accepted and deposited on an intermediate or temporary Incoming Queue IQ IQ in the diagram for subsequent processing. Processed artifacts are removed from an intermediate or temporary Outgoing Queue OQ OQ in the diagram and then dispatched .

A dynamically updateable set of one or more Incoming Queues IQ IQ in the diagram and a dynamically updateable set of one or more Outgoing Queues OQ OQ in the diagram operate as intermediate or temporary buffers for incoming and outgoing traffic .

A dynamically updateable set of one or more WorkFlows WorkFlow WorkFlow in the diagram remove incoming traffic from an intermediate or temporary Incoming Queue IQ IQ in the diagram perform all of the required processing operations explained below and deposit processed artifacts on an intermediate or temporary Outgoing Queue OQ OQ in the diagram . The WorkFlow component will be described more fully below.

The Database that is depicted in is a logical representation of the possibly multiple physical repositories that may be implemented to support inter alia configuration word catalog calculation etc. information. The physical repositories may be implemented through any combination of conventional Relational Database Management Systems RDBMSs such as Oracle through Object Database Management Systems ODBMSs through in memory Database Management Systems DBMSs or through any other equivalent facilities.

An Administrator provides management or administrative control over all of the different components of an AS through as one example a Web based interface. It will be readily apparent to one of ordinary skill in the relevant art that numerous other interfaces e.g. an Application Programming Interface API a data feed etc. are easily possible.

Through flexible extensible and dynamically updatable configuration information a WorkFlow component may be quickly and easily realized to support any number of activities. For example WorkFlows might be configured to support a registration process to support the receipt and processing of incoming SMS MMS IMS etc. messages to support the generation and processing of billing events to support the generation and dispatch of outgoing confirmation update etc. messages to support the generation of scheduled and or on demand reports etc. The specific WorkFlows that were just described are exemplary only it will be readily apparent to one of ordinary skill in the relevant art that numerous other WorkFlow arrangements alternatives etc. are easily possible.

A SP may maintain a repository e.g. a database into which selected details of all administrative messaging processing etc. activities may be recorded. Among other things such a repository may be used to support 

1 Scheduled e.g. daily weekly etc. and or on demand reporting with report results delivered through SMS MMS IMS etc. messages through E mail through a WWW based facility through IM through an IVR facility etc.

2 Scheduled and or on demand data mining initiatives possibly leveraging or otherwise incorporating one or more external data sources with the results of same presented through visualization Geographic Information System GIS etc. facilities and delivered through SMS MMS IMS etc. messages through E mail through a WWW based facility trough IM through an IVR facility etc.

Over time as ever more messages are presented to a SP the SP may continuously expand the depth and or the breadth of its internal repositories and possibly inter alia consequently incrementally refine improve etc. the quality etc. of its reporting etc. activities.

Returning to . . . under the Set exchanges Mary s SMS MMS etc. message may be directed to an appropriate destination address e.g. a TN or a SC as provided specified identified etc. by possibly inter alia M or SP and may contain any number of elements or data items including possibly inter alia the dollar amount of the purchase an optional account identifier e.g. if perhaps for convenience and or flexibility Mary maintains more than one account an optional MS password or identifier code the current date and time etc.

It is important to note the Set exchanges that are illustrated in and which were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example 

A Extracting from a received message and optionally validating etc. various data elements including inter alia the Source Address SA such as for example the TN of Mary s WD the Destination Address such as for example the destination SC the message content or body that might contain as just one possible example the transaction amount etc.

The processing activities that are depicted under the designation Set in represent the activities that might take place as the SP s AS completes all of the required processing activities including possibly inter alia as appropriate and as required one or more billing events via SP s BI to possibly among other things generate an Authorization Code AuC see .

It is important to note the Set exchanges that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example 

A A received request may be applied to or passed against one or more of a MS accounts for example possibly inter alia in a SP defined and or MS defined order or sequence .

B A received request may for example based on SP defined and or MS defined criteria such as possibly inter alia occurrence frequency individual or aggregate dollar amount etc. optionally trigger one or more additional check approval etc. steps or actions. Such steps or actions may result in possibly inter alia a pause in or suspension of a transaction further approval sequences utilizing any combination of one or more channels including possibly inter alia WWW E mail IM IVR SMS MMS etc. phone mail etc. etc.

C A MS account s may be found to contain insufficient funds to support the successful processing of a received request. Under such a circumstance a transaction may for example be rejected paused suspended etc. one or more notifications may be issued to a MS utilizing any combination of one or more channels including possibly inter alia WWW E mail IM IVR SMS MMS etc. phone mail etc. etc.

In the exchanges that are collected under the designation Set represent the activities that might take place as SP dispatches one or more SMS MMS etc. positive response messages see the message s is are routed by a MICV to Mary s WC see and the message s is are received by Mary on her WD see .

The positive response message s may contain possibly inter alia an AuC value a date time stamp etc. Additionally Mary may optionally reply to a any of the response message s .

It is important to note the Set exchanges that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible e.g. one or more negative response messages might be generated and dispatched if a MS account s contained insufficient funds etc. and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set represent the activities that might take place as Mary conveys the received AuC along possibly with other information to M see . The information may be conveyed to M manually e.g. verbally through a messaging exchange etc. and or automatically e.g. via Bluetooth via WiFi etc. .

It is important to note the Set exchanges that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible e.g. in an M Commerce environment information may be conveyed through possibly inter alia cookies URLs etc. and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set represent the activities that might take place as M optionally interacts with various back end systems. Possibly inter alia M may submit a request containing possibly among other things an AuC value the dollar amount of a purchase a date time stamp a merchant identifier a merchant password or code etc. see the MBS may complete all of the required processing activities including possibly inter alia as appropriate and as required interacting with a SP s AS to possibly among other things generate an Approval Code ApC see and the MBS may return a response to M containing possibly among other things an ApC see .

It is important to note the Set exchanges that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set represent the activities that might take place as M conveys possibly inter alia the ApC to Mary see . The information may be conveyed to Mary manually e.g. verbally through a messaging exchange etc. and or automatically e.g. via Bluetooth via WiFi etc. .

It is important to note the Set exchanges that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible e.g. in an M Commerce environment information may be conveyed through possibly inter alia cookies URLs etc. and indeed are fully within the scope of the present invention.

It is important to note the exchanges that were described above as residing under the designation Set Set in are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

The simple scenario that was described above i.e. Mary completes a registration process subsequently enters a store completes her shopping enters a checkout lane where her purchases are rung and employs aspects of the present invention for payment is illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other arrangements are easily possible and indeed are fully within the scope of the present invention. For example 

1 A MS may optionally dispatch to a SP one or more additional SMS MMS etc. messages containing possibly inter alia an ApC value to close the loop as a further security check.

2 A SP may optionally leverage Location Based Service LBS Global Positioning System GPS facilities to provide an additional level of security by possibly inter alia matching the physical location of a MS as determined through LBS GPS or similar facilities and the physical location of M.

3 A M may optionally allow a MS to bypass a conventional checkout process and might possibly inter alia leverage the capabilities of facilities like Near Field Communication NFC RFID etc. to quickly scan all of a MS items and subsequently automatically launch the initial exchanges that are illustrated in .

4 Various of the information that is conveyed between a MS and a M may be exchanged via one or more of any number of mechanisms including for example NFC.

5 A SP may optionally alert a MS to a low account balance condition e.g. when the balance of an account drops below a threshold level previously specified by the MS etc. . A SP may optionally allow a MS to top up an account with possibly inter alia cash a credit card a debit card etc. through possibly inter alia an appropriate exchange of SMS MMS etc. request approval confirmation etc. messages.

6 A SP may optionally offer various data mining services to possibly inter alia Ms MSs WCs etc. Such services might include for example transaction trends or patterns historical summaries etc. may include numerous aggregations e.g. by MS by geographic region by time interval etc. and may be presented through any combination of one or more channels including inter alia WWW E mail IM SMS MMS etc. mail etc.

A SP may optionally offer periodic reports on a scheduled basis on demand etc. that summarize account activity e.g. possibly inter alia funding events purchase transactions payments etc. Such reports may be delivered through any combination of one or more channels including inter alia WWW E mail IM IVR SMS MMS etc. phone mail etc. and may offer various optional enhancements such as possibly inter alia drill down capability .

8 For Ms and or MSs that so elect various of the exchanges that are illustrated in e.g. Set Set Set etc. may optionally be completed automatically perhaps for an incremental fee or charge to a M and or a MS with an appropriate set of confirmation approval etc. SMS MMS etc. IM E Mail IVR mail etc. messages.

The catalog of processing steps that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other processing steps are easily possible and indeed are fully within the scope of the present invention.

The various confirmation response approval report etc. message s that were described above may optionally contain an informational element e.g. a service announcement a relevant or applicable factoid etc. The informational element may be selected statically e.g. all generated messages are injected with the same informational text selected randomly e.g. a generated message is injected with informational text that is randomly selected from a pool of available informational text or location based i.e. a generated message is injected with informational text that is selected from a pool of available informational text based on the current physical location of the recipient of the message as derived from as one example a LBS GPS facility .

A SP may optionally allow advertisers to register and or provide e.g. directly or through links references to external sources advertising content.

The provided advertising content may optionally be included in various of the above described message s e.g. textual material multimedia images of brand logos sound video snippets etc. material etc. The advertising material may be selected statically e.g. all generated messages are injected with the same advertising material selected randomly e.g. a generated message is injected with advertising material that is randomly selected from a pool of available material or location based i.e. a generated message is injected with advertising material that is selected from a pool of available material based on the current physical location of the recipient of the message as derived from as one example a LBS GPS facility .

The above described message s may optionally contain promotional materials coupons etc. via possibly inter alia text still images video clips etc. .

It is important to note that while aspects of the discussion that was presented above focused on the use of SCs and TNs it will be readily apparent to one of ordinary skill in the relevant art that other message address identifiers are equally applicable and indeed are fully within the scope of the present invention.

The discussion that was just presented referenced the specific wireless messaging paradigms SMS and MMS. However it is to be understood that it would be readily apparent to one of ordinary skill in the relevant art that other messaging paradigms IMS WAP E mail etc. are fully within the scope of the present invention.

It is important to note that the hypothetical example that was presented above which was described in the narrative and which was illustrated in the accompanying figures is exemplary only. It is not intended to be exhaustive or to limit the invention to the specific forms disclosed. It will be readily apparent to one of ordinary skill in the relevant art that numerous alternatives to the presented example are easily possible and indeed are fully within the scope of the present invention.

