---

title: System and method for enhanced transaction security
abstract: As individuals increasingly engage in different types of transactions they face a growing threat from, possibly among other things, identity theft, financial fraud, information misuse, etc. and the serious consequences or repercussions of same. Leveraging the ubiquitous nature of wireless devices and the popularity of (SMS, MMS, etc.) messaging, an infrastructure that enhances the security of the different types of transactions within which a wireless device user may participate. The infrastructure may optionally leverage the capabilities of a centrally-located Messaging Inter-Carrier Vendor.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08751394&OS=08751394&RS=08751394
owner: Sybase 365, Inc.
number: 08751394
owner_city: Reston
owner_country: US
publication_date: 20081124
---
This application claims the benefit of U.S. Provisional Patent Application Ser. No. 60 990 652 filed on Nov. 28 2007 which is herein incorporated by reference in its entirety.

The present invention relates generally to telecommunications services. More particularly the present invention relates to capabilities that enhance substantially the value and usefulness of various messaging paradigms including inter alia Short Message Service SMS Multimedia Message Service MMS etc.

As the wireless revolution continues to march forward the importance to a Mobile Subscriber MS for example a user of a Wireless Device WD such as a mobile telephone a BlackBerry etc. that is serviced by a Wireless Carrier WC of their WD grows substantially.

One consequence of such a growing importance is the resulting ubiquitous nature of WDs i.e. MSs carry them at almost all times and use them for an ever increasing range of activities.

Coincident with the expanding presence of WDs has been the explosive growth of messaging a steady annual increase year over year in the number of SMS MMS etc. messages that have been exchanged by and between WDs. That steady increase shows no sign of abating. For example as reported by the industry group CTIA see ctia.org on the World Wide Web WWW in the U.S. there were over 158 billion SMS messages sent during 2006 representing a 95 increase over 2005 and there were over 2.7 billion MMS messages sent during 2006 representing a 100 increase over 2005 .

Concurrent with the positive progress that the wireless revolution has enjoyed society has sadly suffered significant negative progress. Among other things as individuals increasingly engage in different types of transactions such as possibly inter alia the facilitation completion etc. of a payment element of for example an on line purchase an account status e.g. balance available credit etc. inquiry a funds or money transfer operation etc. over different channels or mediums such as for example the WWW etc. with different organizations such as possibly inter alia utility companies financial institutions on line retailers etc. they face a growing threat from possibly inter alia identity theft financial fraud information misuse etc. and the serious consequences or repercussions of same. For example a study by Utica College s Center for Identity Management and Information Protection CIMIP that included among other things an extensive review of U.S. Secret Service case files found that the median actual dollar loss for identity theft victims was 31 356.

The specific examples that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other examples are easily possible and indeed are fully within the scope of the present invention.

Given 1 the ubiquitous nature of WDs 2 the popularity of SMS MMS etc. messaging and 3 an expanding universe of threats it would be desirable to leverage WD based messaging to enhance the security of the different types of transactions within which a MS may participate through the innovatory addition of an artifact that the ATM Industry Association ATMIA has described as an inexpensive and tried and tested method of authenticating a . . . customer s identity for . . . transactions i.e. a Personal Identification Numbers PIN .

The present invention facilitates such enhanced transaction security in new creative and unconventional ways and addresses various of the not insubstantial challenges that are associated with same.

In one embodiment of the present invention there is provided a method for enhanced transaction security including receiving from a WD of a MS a request message the request message indicative of a transaction involving a third party performing one or more processing steps on aspects of the request message using at least in part a information from the request message b registration information previously supplied by the mobile subscriber and c information previously obtained about the third party yielding one or more security policies generating based at least on aspects of the one or more security policies a PIN preserving at least the PIN in a repository and generating a response message to the mobile subscriber the response message containing at least the PIN.

In accordance with the embodiment the MS may use the PIN in the transaction through for example a manual entry b Near Field Communication c infrared communication or d BlueTooth communication and the third party may interact with the repository to at least confirm the PIN.

Still in accordance with the embodiment the request message and the response message may each be a a Short Message Service message b a Multimedia Message Service message c an IP Multimedia Subsystem message or d an E Mail message.

Still in accordance with the embodiment the PIN may be a generated randomly b generated through a predefined algorithm or formula or c generated sequentially.

Still in accordance with the embodiment the method may employ information previously supplied by a MS.

In another embodiment of the present invention there is provided a method for enhanced transaction security including receiving from a third party an indication of a transaction the indication at least identifying a participant in the transaction performing one or more processing steps on aspects of the indication using at least in part a information from the indication b registration information previously supplied by the participant and c information previously obtained about the third party yielding one or more security policies generating based at least on aspects of the one or more security policies a PIN preserving at least the PIN in a repository and generating a response message to a wireless device of the participant the response message containing at least the PIN.

These and other features of the embodiments of the present invention along with their attendant advantages will be more fully appreciated upon a reading of the following detailed description in conjunction with the associated drawings.

It should be understood that these figures depict embodiments of the invention. Variations of these embodiments will be apparent to persons skilled in the relevant art s based on the teachings contained herein.

The present invention may leverage the capabilities of a centrally located full featured MICV facility. Reference is made to U.S. Pat. No. 7 154 901 entitled INTERMEDIARY NETWORK SYSTEM AND METHOD FOR FACILITATING MESSAGE EXCHANGE BETWEEN WIRELESS NETWORKS and its associated continuations for a description of a MICV a summary of various of the services functions etc. that are performed by a MICV and a discussion of the numerous advantages that arise from same.

As illustrated in and reference numeral a MICV is disposed between possibly inter alia multiple WCs WC WC on one side and multiple SPs SP SP on the other side and thus bridges all of the connected entities. A MICV thus as one simple example may offer various routing formatting delivery value add etc. capabilities that provide possibly inter alia 

1 A WC and by extension all of the MSs that are serviced by the WC with ubiquitous access to a broad universe of SPs and

2 A SP with ubiquitous access to a broad universe of WCs and by extension to all of the MSs that are serviced by the WCs .

Generally speaking a MICV may have varying degrees of visibility e.g. access etc. to the MS MS MS SP etc. messaging traffic 

1 A WC may elect to route just their out of network messaging traffic to a MICV. Under this approach the MICV would have visibility e.g. access etc. to just the portion of the WC s messaging traffic that was directed to the MICV by the WC.

2 A WC may elect to route all of their messaging traffic to a MICV. The MICV may possibly among other things subsequently return to the WC that portion of the messaging traffic that belongs to i.e. that is destined for a MS of the WC. Under this approach the MICV would have visibility e.g. access etc. to all of the WC s messaging traffic.

While the discussion below will include a MICV it will be readily apparent to one of ordinary skill in the relevant art that other arrangements are equally applicable and indeed are fully within the scope of the present invention.

In the discussion below the present invention is described and illustrated as being offered by a SP. A SP may for example be realized as a third party service bureau an element of a WC or a landline carrier an element of a MICV multiple third party entities working together etc.

In the discussion below reference is made to messages that are sent for example between a MS and a SP. As set forth below a given message sent between a MS and a SP may actually comprise a series of steps in which the message is received forwarded and routed between different entities including possibly inter alia a MS a WC a MICV and a SP. Thus unless otherwise indicated it will be understood that reference to a particular message generally includes that particular message as conveyed at any stage between an origination source such as for example a MS and an end receiver such as for example a SP. As such reference to a particular message generally includes a series of related communications between for example a MS and a WC a WC and a MICV a MICV and a SP etc. The series of related communications may in general contain substantially the same information or information may be added or subtracted in different communications that nevertheless may be generally referred to as a same message. To aid in clarity a particular message whether undergoing changes or not is referred to by different reference numbers at different stages between a source and an endpoint of the message.

To better understand the particulars of the present invention consider for a moment a simple hypothetical example SP SPoffers a service that has been enhanced or augmented as provided through aspects of the instant invention and Mary a MS uses SP s service.

SP Billing Interface BI . A single consolidated interface that SP may use to easily reach possibly inter alia one or more internal and or external entities such as a credit card or debit card clearinghouse a carrier billing system a service bureau that provides access to multiple carrier billing systems invoicing or billing facilities etc.

SP AS . Facilities that provide key elements of the instant invention which will be described below .

It is important to note that while in the MS WD and MS PC entities are illustrated as being adjacent or otherwise near each other in actual practice the entities may for example be physically located anywhere.

In the exchanges that are collected under the designation Set 1 represent the activities that might take place as Mary completes a registration process with SP 

A Mary uses one of her PCs to visit a WS of SP to possibly among other things complete a service registration process .

B A WS of SP interacts with an AS of SP to possibly among other things commit some or all of the information that Mary provided to a data repository e.g. a database optionally complete a billing transaction etc. .

D After receiving a response from an AS of SP a WS of SP responds appropriately e.g. with the presentation of a confirmation message etc. .

The specific exchanges that were described above as residing under the designation Set 1 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example the collected information may be reviewed confirmed etc. through one or more manual and or automatic mechanisms. For example the registration process may be completed through any combination of one or more channels including inter alia the WWW via for example a Web site that is operated by SP wireless messaging SMS MMS etc. Electronic Mail E Mail messages Instant Messaging IM conventional mail telephone Interactive Voice Response IVR facility etc.

During the registration process described above a range of information may be captured from a MS including possibly inter alia 

A Identifying Information. For example possibly among other things name address age landline and wireless Telephone Numbers TNs E Mail addresses IM names identifiers a unique identifier and a password etc.

B Account Information. For example possibly among other things various of the particulars for one or more of a MS accounts with organizations such as possibly inter alia utility companies financial institutions on line retailers etc. . The particulars may include possibly inter alia organization name and contact details account number account access credentials etc.

C Security Service Information. For example possibly among other things the selection of one or more of the different security plans programs etc. that a SP may optionally offer each of which may carry possibly inter alia some type of fee or charge . Such plans programs etc. may provide possibly inter alia alerts to a MS via for example SMS MMS E Mail IM etc. based on various events criteria thresholds etc. additional levels of notification confirmation etc. during a transaction etc.

D Billing Information. For example the particulars such as possibly inter alia name number etc. for financial institution bank brokerage etc. accounts credit cards debit cards etc. As well possibly the selection of one or more of the different service billing models may be offered by a SP including inter alia a fixed one time charge a recurring monthly etc. fixed charge a recurring monthly etc. variable charge a per transaction charge etc. and possibly the selection of one or more of the different payment mechanisms that may be offered by a SP including possibly among other things credit or debit card information authorization to place a charge on a MS s phone bill authorization to deduct funds from a MS bank brokerage etc. account etc. .

The specific pieces of information that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other pieces of information e.g. additional Identifying Information scheduled daily weekly etc. reporting desired and or on demand reporting desired etc. are easily possible and indeed are fully within the scope of the present invention.

As noted above the information that Mary provided during the registration process may be preserved in a data repository e.g. a database and may optionally be organized as a MS Profile.

The content of Mary s profile may be augmented by SPto include as just a few examples of the many possibilities internal and or external demographic psychographic sociological etc. data.

As noted above a SP s BI may optionally complete a billing transaction. The billing transaction may take any number of forms and may involve different external entities e.g. a WC s billing system a carrier billing system service bureau a credit or debit card clearinghouse a financial institution etc. . The billing transaction may include inter alia 

1 The appearance of a line item charge on the bill or statement that a MS receives from her WC. Exemplary mechanics and logistics associated with this approach are described in pending U.S. patent application Ser. No. 10 837 695 entitled SYSTEM AND METHOD FOR BILLING AUGMENTATION. Other ways of completing or performing line item billing are easily implemented by those skilled in the art.

In the exchanges that are collected under the designation Set 2 represent the activities that might take place as SP optionally coordinates etc. with one or more external entities to possibly among other things secure access confirm collected information arrange to receive updates etc. see .

The specific exchanges that were described above as residing under the designation Set 2 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges including inter alia updates to various of the information in a MS Profile in a SP s repository etc. are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set 3 represent the activities that might take place as an AS of SP dispatches to Mary one or more confirmation E Mail messages .

The specific exchanges that were described above as residing under the designation Set 3 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set 4 represent the activities that might take place as an AS of SP dispatches one or more confirmation SMS MMS etc. messages to a WD of Mary and Mary optionally replies or responds to the message s . Of interest and note are 

2 The SP may employ a Short Code SC or a regular TN as its source address and to which it would ask users of its service to direct any reply messages . While the abbreviated length of a SC e.g. five digits for a SC administered by Neustar uder the Common Short Code CSC program incrementally enhances the experience of a MS e.g. the MS need remember and enter only a few digits as the destination address of a reply message it also by definition constrains the universe of available SCs thereby causing each individual SC to be a limited or scarce resource and raising a number of SC CSC management etc. issues. A description of a common i.e. universal short code environment may be found in pending U.S. patent application Ser. No. 10 742 764 entitled UNIVERSAL SHORT CODE ADMINISTRATION FACILITY. 

The specific exchanges that were described above as residing under the designation Set 4 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

The Set 1 Set 2 Set 3 and Set 4 exchanges that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example possibly inter alia the registration information that was described above may subsequently be managed e.g. existing information may be edited or removed new information may be added etc. through any combination of one or more channels including inter alia a SP s WWW facility wireless messaging SMS MMS etc. E Mail messages IM exchanges conventional mail telephone IVR facilities etc.

To continue with our hypothetical example . . . as Mary goes about her daily activities there may arise numerous instances where she engages in transactions and would like to enhance the security of those transactions. For example 

2 Mary may wish to complete the payment portion of a purchase from for example an on line retailer etc. .

3 Mary may wish to transfer money between various of her bank brokerage credit card etc. accounts transfer money from one of her bank brokerage credit card etc. accounts to someone else transfer money to someone else perhaps another MS with the amount of the transfer along with for example charges fees etc. appearing on her WC statement etc.

The specific examples that were cataloged above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other examples are easily possible and indeed are fully within the scope of the present invention.

SP BI . A single consolidated interface that SP may use to easily reach possibly inter alia one or more internal and or external entities such as a credit card or debit card clearinghouse a carrier billing system a service bureau that provides access to multiple carrier billing systems invoicing or billing facilities etc.

SP AS . Facilities that provide key elements of the instant invention which will be described below .

Third Party 3P . An organization such as possibly inter alia a utility company a financial institution an on line retailer an employer etc.

In the exchanges that are collected under the designation Set 1 represent the activities that might take place as Mary perhaps in connection with or in anticipation of some type of transaction composes on her WD a SMS MMS etc. request message. In the instant example the request message is shown traveling through a MICV and arriving at an AS of SP see . Mary s request message may be directed to any number of addresses including possibly inter alia a SC a TN etc. .

A request message may possibly inter alia indicate a MS desire for enhanced security within a transaction contain various identification e.g. account name account number etc. authorization e.g. access credentials etc. etc. artifacts identify a specific 3P etc.

The specific exchanges that were described above as residing under the designation Set 1 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set 2 represent the activities that might take place as an AS of SP possibly inter alia a completes a series of processing steps and b dispatches one or more response SMS MMS etc. messages to Mary .

During its processing steps an AS may employ any combination of a number of automated e.g. through software solutions and or manual e.g. through human intervention actions techniques capabilities etc. to possibly inter alia 

A Extract one or more data elements from a received request and optionally perform various edit validation etc. operations on the extracted data element s .

B Leverage information that may have been previously collected from a MS during an optional registration process such as possibly inter alia Identifying Information Account Information Security Service Information Billing Information etc. .

C Leverage information that a SP may optionally maintain about a 3P such as possibly inter alia definitional information details concerning the 3P s security policies and procedures etc. .

D Apply one or more rules bodies of logic etc. from for example a flexible extensible and dynamically configurable pool of same to possibly among other things identify a MS identify a 3P identify all of the different security policies and procedures that might be applicable in the instant circumstance etc.

E Based on flexible extensible and dynamically configurable rules that may govern possibly inter alia format length content strength etc. generate preserve etc. an appropriate PIN. A PIN may be generated randomly be derived from a predefined algorithm or formula be generated sequentially from an internal base value etc.

F Interact with one or more external entities such as possible inter alia a 3P etc. to for example exchange information with an entity s token password access etc. service update an entity etc.

The catalog of processing steps that was described above is illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other processing steps are easily possible and indeed are fully within the scope of the present invention.

Various of the techniques strategies capabilities etc. that were described above may leverage one or more internal and or external repositories such as possibly inter alia geographic data demographic data etc.

Each of the techniques strategies capabilities etc. that were described above may have associated with it possibly inter alia an optional set of weighting scoring confidence etc. factors that may be used either individually or together to develop results.

After completing its processing steps SP may possibly inter alia dispatch one or more response SMS MMS etc. messages to Mary s WD . In the instant example response messages are shown traversing a MICV .

A response message may contain possibly inter alia a PIN descriptive or explanatory text confirmation information contact information a request to call e.g. a help center at a particular TN etc.

Mary may optionally reply to a response message. Based on any received replies SP may optionally complete one or more additional processing steps.

During the activities that were described above an SP may offer any number of other optional services capabilities etc. including possibly inter alia 

1 An SP may complete any number of billing transactions of the type nature etc. described previously .

2 An SP may track a MS usage aggregate same optionally offer to the MS to external entities such as a 3P etc. discounts rebates surcharges etc. based on the tracked usage etc.

The specific exchanges that were described above as residing under the designation Set 2 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set 3 represent the activities that might take place as Mary after for example receiving a PIN via a response message employs the PIN via to initiate continue etc. a transaction via .

Mary may use any combination of a range of mechanisms including possibly inter alia manual entry Near Field Communication NFC InfraRed IR Bluetooth data transfer etc. to employ the PIN.

The specific exchanges that were described above as residing under the designation Set 3 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example Mary may optionally provide other information including for example identification information access credentials etc. during her initiation continuance etc. of a transaction via .

In the exchanges that are collected under the designation Set 4 represent the activities that might take place as 3P possibly inter alia interacts with AS of SP to possibly among other things confirm authenticate etc. a received PIN see .

The specific exchanges that were described above as residing under the designation Set 4 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set 5 represent the activities that might take place as 3P continues completes etc. a transaction with Mary provides confirmation to Mary etc. via optionally incorporating possibly inter alia additional instances of the and exchanges .

The specific exchanges that were described above as residing under the designation Set 5 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

The Set 1 Set 2 Set 3 Set 4 and Set 5 exchanges that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

SP BI . A single consolidated interface that SP may use to easily reach possibly inter alia one or more internal and or external entities such as a credit card or debit card clearinghouse a carrier billing system a service bureau that provides access to multiple carrier billing systems invoicing or billing facilities etc.

SP AS . Facilities that provide key elements of the instant invention which will be described below .

3P . An organization such as possibly inter alia a utility company a financial institution an on line retailer an employer etc.

In the exchanges that are collected under the designation Set 1 represent the activities that might take place as Mary initiates continues etc. a transaction with a 3P via . Within this context Mary may supply a range of information including for example identification information access credentials an explicit request for enhanced transaction security etc. .

The specific exchanges that were described above as residing under the designation Set 1 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set 2 represent the activities that might take place as 3P possibly inter alia interacts with AS of SP to possibly among other things request enhanced transaction security see .

The specific exchanges that were described above as residing under the designation Set 2 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set 3 represent the activities that might take place as SP possibly inter alia a completes a series of processing steps b dispatches one or more response SMS MMS etc. messages to Mary and c optionally replies to 3P .

An illustrative catalog of processing steps was described above in connection with the discussion of Set 2 of .

After completing its processing steps SP may possibly inter alia dispatch one or more response SMS MMS etc. messages to Mary s WD . In the instant example response messages are shown traversing a MICV .

A response message may contain possibly inter alia a PIN descriptive or explanatory text confirmation information contact information a request to call e.g. a help center at a particular TN etc.

Mary may optionally reply to a response message. Based on any received replies SP may optionally complete one or more additional processing steps.

During the activities that were described above an SP may offer any number of other optional services capabilities etc. including possibly inter alia 

1 An SP may complete any number of billing transactions of the type nature etc. described previously .

2 An SP may track a MS usage aggregate same optionally offer to the MS to external entities such as a 3P etc. discounts rebates surcharges etc. based on the tracked usage etc.

The specific exchanges that were described above as residing under the designation Set 3 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set 4 represent the activities that might take place as Mary after for example receiving a PIN via a response message employs the PIN via to initiate continue etc. a transaction via .

Mary may use any combination of a range of mechanisms including possibly inter alia manual entry NFC IR Bluetooth data transfer etc. to employ the PIN.

The specific exchanges that were described above as residing under the designation Set 4 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set 5 represent the activities that might take place as 3P possibly inter alia interacts with AS of SP to possibly among other things confirm authenticate etc. a received PIN see .

The specific exchanges that were described above as residing under the designation Set 5 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set 6 represent the activities that might take place as 3P continues completes etc. a transaction with Mary provides confirmation to Mary etc. via optionally incorporating possibly inter alia additional instances of the and exchanges .

The specific exchanges that were described above as residing under the designation Set 5 are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

The Set 1 Set 2 Set 3 Set 4 Set 5 and Set 6 exchanges that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

Under the illustrative frameworks that were presented through and numerous alternative exchanges arrangements etc. are easily possible including possibly inter alia 

1 A MS may optionally need to acknowledge a response message by for example replying to same to activate or otherwise confirm a PIN. Such an acknowledgement may optionally need to occur within a defined period of time after which an unacknowledged PIN may possibly inter alia go stale and not be usable .

3 A PIN may optionally carry a lifetime indicator. Such a value may identify a specific period of time e.g. from a beginning date and time to an ending date and time during which a PIN may be usable identify a specific number of uses or invocations after which a PIN may go stale and not be usable identify a cumulative transaction amount e.g. in a currency such as dollars beyond which a PIN may go stale and not be usable etc.

4 A SP may incorporate additional factors criteria tests etc. during various of its processing activities e.g. the confirmation authentication etc. of a PIN etc. including possibly inter alia MS Location Based Service LBS and or Global Positioning System GPS information biometric information etc.

The confirmation response etc. message s that were described above may optionally contain an informational element e.g. a relevant or applicable factoid etc. The informational element may be selected statically e.g. all generated messages are injected with the same informational text randomly e.g. a generated message is injected with informational text that is randomly selected from a pool of available informational text or location based i.e. a generated message is injected with informational text that is selected from a pool of available informational text based on the current physical location of the recipient of the message as derived from as one example a LBS GPS etc. facility .

The confirmation response etc. message s that were identified above may optionally contain advertising e.g. textual material if an SMS model is being utilized or multimedia images of brand logos sound video snippets etc. material if an MMS model is being utilized. The advertising material may be selected statically e.g. all generated messages are injected with the same advertising material randomly e.g. a generated message is injected with advertising material that is randomly selected from a pool of available material or location based i.e. a generated message is injected with advertising material that is selected from a pool of available material based on the current physical location of the recipient of the message as derived from as one example a LBS GPS etc. facility .

The confirmation response etc. message s that were identified above may optionally contain promotional materials e.g. still images video clips etc. .

A dynamically updateable set of one or more Gateways GW GW in the diagram handle incoming SMS MMS etc. messaging etc. traffic and outgoing SMS MMS etc. messaging etc. traffic . Incoming traffic is accepted and deposited on an intermediate or temporary Incoming Queue IQ IQ in the diagram for subsequent processing. Processed artifacts are removed from an intermediate or temporary Outgoing Queue OQ OQ in the diagram and then dispatched .

A dynamically updateable set of one or more Incoming Queues IQ IQ in the diagram and a dynamically updateable set of one or more Outgoing Queues OQ OQ in the diagram operate as intermediate or temporary buffers for incoming and outgoing traffic .

A dynamically updateable set of one or more WorkFlows WorkFlow WorkFlow in the diagram remove incoming traffic from an intermediate or temporary Incoming Queue IQ IQ in the diagram perform all of the required processing operations and deposit processed artifacts on an intermediate or temporary Outgoing Queue OQ OQ in the diagram . The WorkFlow component will be described more fully below.

The Database that is depicted in is a logical representation of the possibly multiple physical repositories that may be implemented to support inter alia configuration profile monitoring alerting etc. information. The physical repositories may be implemented through any combination of conventional Relational Database Management Systems RDBMSs such as Oracle through Object Database Management Systems ODBMSs through in memory Database Management Systems DBMSs or through any other equivalent facilities.

An Administrator that is depicted in provides management or administrative control over all of the different components of an AS through as one example a WWW based interface . It will be readily apparent to one of ordinary skill in the relevant art that numerous other interfaces e.g. a data feed an Application Programming Interface API etc. are easily possible.

Through flexible extensible and dynamically updatable configuration information a WorkFlow component may be quickly and easily realized to support any number of activities. For example WorkFlows might be configured to support a registration process to support interactions with external entities to support various internal processing steps as described above including possibly inter alia 1 the evaluation of received request messages 2 the generation of PIN values and 3 the generation and dispatch of response messages to support the generation and dispatch of confirmation etc. messages to support various billing transactions to support the generation of scheduled and or on demand reports etc. The specific WorkFlows that were just described are exemplary only it will be readily apparent to one of ordinary skill in the relevant art that numerous other WorkFlow arrangements alternatives etc. are easily possible.

A SP may maintain a repository e.g. a database into which selected details of all administrative messaging etc. activities may be recorded. Among other things such a repository may be used to support 

1 Scheduled e.g. daily weekly etc. and or on demand reporting with report results delivered through SMS MMS etc. messages through E Mail through a WWW based facility etc.

2 Scheduled and or on demand data mining initiatives possibly leveraging or otherwise incorporating one or more external data sources with the results of same presented through Geographic Information Systems GISs visualization etc. facilities and delivered through SMS MMS etc. messages through E Mail through a WWW based facility etc.

It is important to note that while aspects of the discussion that was presented above referenced the use of SCs and TNs it will be readily apparent to one of ordinary skill in the relevant art that other message address identifiers are equally applicable and indeed are fully within the scope of the present invention.

The discussion that was just presented referenced two specific wireless messaging paradigms SMS and MMS. These paradigms potentially offer an incremental advantage over other paradigms in that native support for SMS and or MMS is commonly found on a WD that a potential MS would be carrying. However it is to be understood that it would be readily apparent to one of ordinary skill in the relevant art that other paradigms such as for example Internet Protocol IP Multimedia Subsystem IMS IM E Mail Wireless Application Protocol WAP etc. are fully within the scope of the present invention.

It is important to note that the hypothetical example that was presented above which was described in the narrative and which was illustrated in the accompanying figures is exemplary only. It is not intended to be exhaustive or to limit the invention to the specific forms disclosed. It will be readily apparent to one of ordinary skill in the relevant art that numerous alternatives to the presented example are easily possible and indeed are fully within the scope of the present invention.

