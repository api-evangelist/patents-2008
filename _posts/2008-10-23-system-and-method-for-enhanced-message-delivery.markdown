---

title: System and method for enhanced message delivery
abstract: Coincident with the evolution, maturation, etc. of wireless messaging ecosystems an infrastructure that provides for intelligent and dynamic alternate Multimedia Message Service (MMS) message delivery channels. Occasions may arise where a Mobile Subscriber would like to use their Wireless Device to exchange (for example, MMS) messages but circumstances may prohibit or limit same. On such occasions the MMS messages may be appropriately processed and then routed through one or more alternate message delivery channels such as, possibly inter alia, E-Mail. The infrastructure may optionally leverage the capabilities of a centrally-located Messaging Inter-Carrier Vendor.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08620359&OS=08620359&RS=08620359
owner: Sybase 365, Inc.
number: 08620359
owner_city: Reston
owner_country: US
publication_date: 20081023
---
This application claims the benefit of U.S. Provisional Patent Application No. 60 983 708 filed on Oct. 30 2007 which is herein incorporated by reference in its entirety.

The present invention relates generally to telecommunications services. More particularly the present invention relates to capabilities that enhance substantially the value and usefulness of various messaging paradigms including inter alia Multimedia Message Service MMS Electronic Mail E Mail etc.

As the wireless revolution continues to march forward the importance to a Mobile Subscriber MS for example a user of a Wireless Device WD such as a mobile telephone a BlackBerry etc. that is serviced by a Wireless Carrier WC of their WD grows substantially.

One consequence of such a growing importance is the resulting ubiquitous nature of WDs i.e. MSs carry them at almost all times and use them for an ever increasing range of activities.

Coincident with the expanding presence of WDs has been the explosive growth year over year in the number of Short Message Service SMS MMS etc. messages that have been exchanged by and between WDs. That steady increase shows no sign of abating. For example 

1 As reported by the industry group CTIA see ctia.org on the World Wide Web WWW in the U.S. there were over 158 billion SMS messages sent during 2006 representing a 95 increase over 2005 and there were over 2.7 billion MMS messages sent during 2006 representing a 100 increase over 2005 .

2 As reported by the research firm M Metrics see mmetrics.com on the WWW between June 2007 and August 2007 36.0 of MSs aged 18 24 years 27.2 of MSs aged 13 17 years and 26.9 of MSs aged 25 34 sent MMS messages.

It is important to note that WDs are all different e.g. the vendors or manufacturers of WDs such as for example Motorola Samsung Nokia LG etc. supply their WDs with different features functions different size screens support for different color depths varying degrees of support for audio and video information etc. Among other things different WDs provide different levels of native support ranging from no support to some support to full and complete support for different messaging paradigms such as for example SMS and MMS. As just one example Apple s iPhone does not provide native support for MMS.

The specific WD differences that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other differences are easily identified.

Occasions may arise where a MS would like to use their WD to exchange for example MMS messages but circumstances may prohibit or limit same. For example 

1 Their WD may not provide native support for a particular messaging paradigm such as for example MMS .

2 Their physical location may limit the level type etc. of WC supplied service that their WD may enjoy and thus possibly inter alia constrain their ability to fully use their WD s native facilities to for example exchange MMS messages .

On such occasions and on other occasions that would be obvious to one or ordinary skill in the relevant art it would be desirable to deliver in the instant example MMS messages to the WD through one or more alternate message delivery channels such as possibly inter alia E Mail.

The present invention facilitates such alternate message delivery channels and addresses various of the not insubstantial infrastructure etc. challenges that are associated with same.

In one embodiment of the present invention there is provided a method for delivering MMS messages including receiving from a WD of an originating MS a MMS message that is addressed to a WD of a destination MS performing one or more processing step on aspects of the MMS message including at least querying a routing data repository yielding possibly among other things a MMS support descriptor for the destination MS WD and in response to the MMS support descriptor indicating the absence of MMS support on the destination MS WD sending a portions of the original MMS message and or b transcoded portions of the original MMS message through an alternate message delivery channel.

Still in accordance with the embodiment the method may include populating a routing data repository through a a real time query including for example interrogation of a WC network element such as a Home Location Register HLR and or interrogation of a WD through for example the sending of a text only MMS message and or b a data load.

Still in accordance with the embodiment the method may employ information previously supplied by a MS.

These and other features of the embodiments of the present invention along with their attendant advantages will be more fully appreciated upon a reading of the following detailed description in conjunction with the associated drawings.

It should be understood that these figures depict embodiments of the invention. Variations of these embodiments will be apparent to persons skilled in the relevant art s based on the teachings contained herein.

The present invention may leverage the capabilities of a centrally located full featured MICV facility. Reference is made to 

for a description of a MICV a summary of various of the services functions etc. that may be performed by a MICV and a discussion of the numerous advantages that arise from same.

As illustrated in and reference numeral a MICV is disposed between possibly inter alia multiple WCs WC WC on one side and multiple SPs SP SP on the other side and thus bridges all of the connected entities. A MICV thus as one simple example may offer various E Mail SMS MMS etc. etc. message routing formatting delivery value add etc. capabilities that provide possibly inter alia 

1 A WC and by extension all of the MSs that are serviced by the WC with ubiquitous access to a broad universe of SPs and

2 A SP with ubiquitous access to a broad universe of WCs and by extension to all of the MSs that are serviced by the WCs .

Generally speaking a MICV may have varying degrees of visibility e.g. access etc. to the MS MS MS SP etc. messaging traffic 

1 A WC may elect to route just their out of network messaging traffic to a MICV. Under this approach the MICV would have visibility e.g. access etc. to just the portion of the WC s messaging traffic that was directed to the MICV by the WC.

2 A WC may elect to route all of their messaging traffic to a MICV. The MICV may possibly among other things subsequently return to the WC that portion of the messaging traffic that belongs to i.e. that is destined for a MS of the WC. Under this approach the MICV would have visibility e.g. access etc. to all of the WC s messaging traffic.

While the discussion below will include a MICV it will be readily apparent to one of ordinary skill in the relevant art that other arrangements are equally applicable and indeed are fully within the scope of the present invention.

In the discussion below the present invention is described and illustrated as being offered by a SP. A SP may for example be realized as a third party service bureau an element of a WC or a landline carrier an element of a MICV multiple third party entities working together etc.

In the discussion below reference is made to messages that are sent for example between a MS and a SP. As set forth below a given message sent between a MS and a SP may actually comprise a series of steps in which the message is received forwarded and routed between different entities including possibly inter alia a MS a WC a MICV and a SP. Thus unless otherwise indicated it will be understood that reference to a particular message generally includes that particular message as conveyed at any stage between an origination source such as for example a MS and an end receiver such as for example a SP. As such reference to a particular message generally includes a series of related communications between for example a MS and a WC a WC and a MICV a MICV and a SP etc. The series of related communications may in general contain substantially the same information or information may be added or subtracted in different communications that nevertheless may be generally referred to as a same message. To aid in clarity a particular message whether undergoing changes or not is referred to by different reference numbers at different stages between a source and an endpoint of the message.

To better understand the particulars of the present invention consider for a moment a simple hypothetical example SP SPoffers a service that has been enhanced or augmented as provided through aspects of the instant invention and Mary a MS uses SP s service.

SP Billing Interface BI . A single consolidated interface that SP may use to easily reach possibly inter alia one or more external entities such as a credit card or debit card clearinghouse a carrier billing system a service bureau that provides access to multiple carrier billing systems etc.

SP AS . Facilities that provide key elements of the instant invention which will be described below .

It is important to note that while in the MS WD and MS PC entities are illustrated as being adjacent or otherwise near each other in actual practice the entities may for example be physically located anywhere.

In the exchanges that are collected under the designation Set represent the activities that might take place as Mary completes a registration process with SP 

A Mary uses one of her PCs to visit a WS of SP to possibly among other things complete a service registration process .

B A WS of SP interacts with an AS of SP to possibly among other things commit some or all of the information that Mary provided to a data repository e.g. a database optionally complete a billing transaction etc. .

D After receiving a response from an AS of SP a WS of SP responds appropriately e.g. with the presentation of a confirmation message etc. .

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example the collected information may be reviewed confirmed etc. through one or more manual and or automatic mechanisms. For example the registration process may be completed through any combination of one or more channels including inter alia the WWW via for example a Web site that is operated by SP wireless messaging SMS MMS etc. E Mail messages Instant Messaging IM conventional mail telephone Interactive Voice Response IVR facility etc.

During the registration process described above a range of information may be captured from a MS including inter alia 

A Identifying Information. For example possibly among other things name address landline and wireless Telephone Numbers TNs E Mail addresses IM names identifiers a unique identifier and a password etc.

B Personal Information. For example possibly among other things the particulars of a MS WD s including possibly inter alia TN manufacturer model number features and capabilities limitations etc. .

C Billing Information. Different service billing models may be offered including inter alia a fixed one time charge a recurring monthly etc. fixed charge a recurring monthly etc. variable charge a per event charge etc. Different payment mechanisms may be supported including possibly among other things credit or debit card information authorization to place a charge on a MS s phone bill authorization to deduct funds from a MS bank brokerage etc. account etc.

D Other Information. Additional possibly optional information such as for example further Identifying Information further Personal Information etc.

The specific pieces of information that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other pieces of information e.g. scheduled daily weekly etc. reporting desired and or on demand reporting desired etc. are easily possible and indeed are fully within the scope of the present invention.

As noted above the information that Mary provided during the registration process may be preserved in a data repository e.g. a database and may optionally be organized as a MS Profile.

The content of Mary s profile may be augmented by SPto include as just a few examples of the many possibilities internal and or external demographic psychographic sociological etc. data.

As noted above a SP s BI may optionally complete a billing transaction. The billing transaction may take any number of forms and may involve different external entities e.g. a WC s billing system a carrier billing system service bureau a credit or debit card clearinghouse a financial institution etc. . The billing transaction may include possibly inter alia 

1 The appearance of a line item charge on the bill or statement that a MS receives from her WC. Exemplary mechanics and logistics associated with this approach are described in pending U.S. patent application Ser. No. 10 837 695 entitled SYSTEM AND METHOD FOR BILLING AUGMENTATION. Other ways of completing or performing line item billing are easily implemented by those skilled in the art.

In the exchanges that are collected under the designation Set represent the activities that might take place as SP optionally coordinates etc. with one or more external entities such as for example WCs etc. to possibly among other things secure access confirm collected information arrange to receive updates etc. see .

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges including inter alia updates to various of the information in a MS Profile in a SP s repository etc. are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set represent the activities that might take place as an AS of SP dispatches to Mary one or more confirmation E Mail IM etc. messages .

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set represent the activities that might take place as an AS of SP dispatches one or more confirmation SMS MMS etc. IM etc. messages to Mary s WD and Mary optionally replies or responds to the message s . Of interest and note are 

2 The SP may employ a Short Code SC or a regular TN as its source address and to which it would ask users of its service to direct any reply messages . While the abbreviated length of a SC e.g. five digits for a SC administered by Neustar under the Common Short Code CSC program incrementally enhances the experience of a MS e.g. the MS need remember and enter only a few digits as the destination address of a reply message it also by definition constrains the universe of available SCs thereby causing each individual SC to be a limited or scarce resource and raising a number of SC CSC management etc. issues. A description of a common i.e. universal short code environment may be found in pending U.S. patent application Ser. No. 10 742 764 entitled UNIVERSAL SHORT CODE ADMINISTRATION FACILITY. 

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example the messaging sequence and may be repeated any number of times.

The Set Set Set and Set exchanges that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example possibly inter alia the registration information that was described above may subsequently be managed e.g. existing information may be edited or removed new information may be added etc. through any combination of one or more channels including inter alia a SP s WWW facility wireless messaging SMS MMS etc. E Mail messages IM exchanges conventional mail telephone IVR facilities etc.

To continue with our hypothetical example . . . as Mary goes about her daily activities occasions may arise where she would like to use her WD to exchange MMS messages.

As an aside Technical Specification TS 23.140 from the 3GPP presents an MMS Reference Architecture that as illustrated through and reference numeral defines a range of standards based interfaces or channels through which an exchange of MMS messages may be completed 

For example a MM1 interface may be employed by for example an aspect or element of a WC to exchange a MMS message with a MMS User Agent such as for example a WD .

Returning to our hypothetical example . . . one or more limitations may preclude Mary from completing her MMS message exchange. For example 

2 Mary s physical location may limit the level type etc. of WC supplied service that her WD may enjoy and thus possibly inter alia constrain her ability to fully use her WD s native facilities for the exchange of MMS messages.

The specific examples that were cataloged above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other examples are easily possible and indeed are fully within the scope of the present invention.

Under the sort of circumstances that were cataloged above and under other circumstances that would be readily apparent to one of ordinary skill in the relevant art an alternate message delivery channel such as possibly inter alia E Mail may be leveraged to complete Mary s MMS message exchange.

SP . SP a SP that possibly inter alia offers a service that has been enhanced or augmented as provided through aspects of the instant invention

MMS Gateway GW . A MMS messaging facility e.g. a gateway a MMS Center MMSC etc. that is provided by WC.

SP AS . Facilities that provide key elements of the instant invention which will be described below .

SP Composite Routing Data CRD . A repository of possibly inter alia WC TN etc. information that may be populated and updated through any number of mechanisms e.g. static dynamic both and which possibly among other things supports the proper routing of messages. The CRD will be described further below.

In the exchanges that are collected under the designation Set represent the activities that might take place as MSs e.g. MS MS of WC compose MMS messages to Mary as a MS MS MS of WC and subsequently dispatch the messages .

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example a WC may optionally respond to a received message complete various processing steps etc.

In the exchanges that are collected under the designation Set represent the activities that might take place as the MMS messages leave WC travel through a MICV via and ultimately arrive at an AS of SP via .

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set represent the activities that might take place as an AS of SP possibly inter alia completes a series of processing steps. During its processing steps an AS may employ any combination of a number of automated e.g. through software solutions and or manual e.g. through human intervention techniques activities etc. to possibly inter alia 

A Extract one or more data elements from a received message and optionally perform various edit validation etc. operations on the extracted data elements. The data elements may include possibly inter alia a message s destination address e.g. TN .

B Using a destination address query a CRD via to identify possibly inter alia i the WC that presently services the destination address and ii if native MMS support is present on the WD that is associated with the destination address . If the destination address is not found within the CRD then one or more additional processing steps described in detail below may optionally be initiated before proceeding on to the next step.

C Based on the identified capabilities features limitations etc. of the destination WD determine if it is possible to natively deliver the MMS message to the destination WD. If it is possible then arrange to dispatch the MMS message to the MMS GW of WC as the MMS messaging facility of destination WC WC . If it is not possible then possibly inter alia transcode the content or the body of the MMS message as appropriate and as required construct an E Mail message containing possibly among other things the possibly transcoded MMS message content and arrange to dispatch the E Mail message to the E Mail GW of WC as the E Mail facility of destination WC WC .

The catalog of processing steps that was described above is illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other processing steps are easily possible and indeed are fully within the scope of the present invention.

Additionally various of the processing steps that were described above may leverage information that was collected from a MS during an optional registration process.

As well various of the processing steps that were described above may have associated with it possibly inter alia an optional set of weighting scoring confidence etc. factors that may be used either individually or together to develop possibly among other things the desired results.

As described above a CRD may be queried to identify key items including for example 1 the WC that presently services a destination address e.g. TN and the presence absence of native MMS support on the WD that is associated with the destination address . A CRD query may include and or trigger any combination of one or more mechanisms including possibly inter alia 

1 Data Load. A SP may receive a data feed data dump etc. from one or more external sources such as possibly inter alia WCs on a real time basis on a periodic e.g. scheduled or dynamic basis on an on demand e.g. as needed basis etc. The received information may contain possibly inter alia the TNs of various of a WC s MSs along with as just one example the particulars e.g. feature function capabilities limitations etc. of the WD that is associated with a TN. Aspects of the received information following optional internal processing etc. may be preserved in the CRD by as just one example associating the information to the TN s entry entries in the CRD for subsequent query.

2 WC Query. For a particular TN a SP may initiate inquiries against one or more external sources such as possibly inter alia different elements of the WC that services the TN such as a HLR a provisioning facility a billing facility etc. . Such inquiries may return possibly inter alia the particulars e.g. feature function capabilities limitations etc. of the WD that is associated with the TN. Aspects of the received particulars following optional internal processing etc. may be preserved in the CRD by as just one example associating the information to the TN s entry entries in the CRD for subsequent query.

3 WD Query. For a particular TN a SP may interrogate the WD that is associated with the TN. As just one example 

a A SP may dispatch to the WD i.e. to the TN an MMS message containing just a textual message such as for example Your request is being processed . . . .

c After the MMS message is delivered by a WC to the WD a message delivery report may be returned to the SP.

d A received message delivery report may as defined by the applicable 3GPP standards contain possibly inter alia various of the particulars e.g. feature function capabilities limitations etc. of the WD.

e Aspects of the received particulars following optional internal processing etc. may be preserved in the CRD by as just one example associating the information to the TN s entry entries in the CRD for subsequent query.

Various of the activities that were described above may employ a UAProfile e.g. a UAProfile may be returned to a SP in a e.g. delivery report etc. message a UAProfile may be retrieved from one or more public or private manufacturer etc. repositories based on possibly inter alia WD manufacturer model etc. information that may be returned to a SP etc. As illustrated by and reference numeral a UAProfile is a small Extensible Markup Language XML file that is defined by the World Wide Web Consortium W3C and which describes the particulars of a WD. A UAProfile may include possibly inter alia details for vendor model screen size messaging capabilities multimedia support character set support etc.

The catalog of mechanisms that was described above is illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other mechanisms are easily possible and indeed are fully within the scope of the present invention.

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set represent the activities that might take place as an AS of SP possibly inter alia dispatches the MMS message to Mary as a MS MS MS of WC 

2 If an alternate message delivery channel is employed then as in the instant example an E Mail message to E Mail GW of WC via .

In the instant example the messages are shown traversing a MICV . The messaging sequence or may be repeated any number of times.

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention.

In the exchanges that are collected under the designation Set represent the activities that might take place as the message is delivered to Mary as a MS MS MS of WC from MMS GW via or from E Mail GW via . The messaging sequence or may be repeated any number of times.

The specific exchanges that were described above as residing under the designation Set are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example a MS may optionally respond or reply to a received message in which case the reverse of the activities that were described above would take place .

The Set Set Set Set and Set exchanges that were described above are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other exchanges are easily possible and indeed are fully within the scope of the present invention. For example during various of the activities that were described above an SP may offer any number of other optional services capabilities etc. including possibly inter alia 

1 If an alternate message delivery channel is employed a SP may generate an artificial MM4 forward.RES message for delivery back to an originating WC so that it appears to the originating WC that the MMS message was in fact delivered natively to the destination WD .

2 If an alternate message delivery channel is employed a SP may generate other artificial messages such as possibly inter alia MM4 delivery report. MM4 read reply report. etc. as appropriate and as required.

3 An SP may augment the CRD query activities that were described above to include possibly inter alia information on a WD s current physical location and given same various of the particulars of the WC supplied service s that the WD currently enjoys. Such information may be developed through any combination of one or more facilities like Location Based Service LBS Global Positioning System GPS variations on the WC Query mechanism that was described above etc.

The confirmation delivery etc. message s that were described above may optionally contain an informational element e.g. a relevant or applicable factoid etc. The informational element may be selected statically e.g. all generated messages are injected with the same informational text randomly e.g. a generated message is injected with informational text that is randomly selected from a pool of available informational text or location based i.e. a generated message is injected with informational text that is selected from a pool of available informational text based on the current physical location of the recipient of the message as derived from as one example a LBS GPS etc. facility .

The confirmation delivery etc. message s that were identified above may optionally contain advertising e.g. possibly textual material if an SMS model is being utilized possibly multimedia images of brand logos sound video snippets etc. material if an MMS model is being utilized etc. The advertising material may be selected statically e.g. all generated messages are injected with the same advertising material that is for example selected from a pool of available material randomly e.g. a generated message is injected with advertising material that is for example randomly selected from a pool of available material or location based i.e. a generated message is injected with advertising material that is for example selected from a pool of available material based on the current physical location of the recipient of the message as derived from as one example a LBS GPS etc. facility . Third parties such as for example advertising agencies brands etc. may contribute advertising material to a SP s pool of advertising material.

The confirmation delivery etc. message s that were identified above may optionally contain promotional materials e.g. still images video clips etc. .

A dynamically updateable set of one or more Gateways GW GW in the diagram handle incoming E mail SMS MMS etc. IM etc. messaging etc. traffic and outgoing E mail SMS MMS etc. IM messaging etc. traffic . Incoming traffic is accepted and deposited on an intermediate or temporary Incoming Queue IQ IQ in the diagram for subsequent processing. Processed artifacts are removed from an intermediate or temporary Outgoing Queue OQ OQ in the diagram and then dispatched .

A dynamically updateable set of one or more Incoming Queues IQ IQ in the diagram and a dynamically updateable set of one or more Outgoing Queues OQ OQ in the diagram operate as intermediate or temporary buffers for incoming and outgoing traffic .

A dynamically updateable set of one or more WorkFlows WorkFlow WorkFlow in the diagram remove incoming traffic from an intermediate or temporary Incoming Queue IQ IQ in the diagram perform all of the required processing operations and deposit processed artifacts on an intermediate or temporary Outgoing Queue OQ OQ in the diagram . The WorkFlow component will be described more fully below.

The Database that is depicted in is a logical representation of the possibly multiple physical repositories that may be implemented to support inter alia routing such as CRD configuration profile etc. information. The physical repositories may be implemented through any combination of conventional Relational Database Management Systems RDBMSs such as Oracle through Object Database Management Systems ODBMSs through in memory Database Management Systems DBMSs or through any other equivalent facilities.

An Administrator that is depicted in provides management or administrative control over all of the different components of an AS through as one example a WWW based interface . It will be readily apparent to one of ordinary skill in the relevant art that numerous other interfaces e.g. a data feed an Application Programming Interface API etc. are easily possible.

Through flexible extensible and dynamically updatable configuration information a WorkFlow component may be quickly and easily realized to support any number of activities. For example WorkFlows might be configured to support a registration process to support interactions with external entities such as for example different elements of a WC such as a HLR a provisioning facility a billing facility etc. to support the population of a CRD to support various internal processing steps as described above including possibly inter alia 1 the extraction of data elements from received messages and the optional editing validating etc. of same 2 the querying of a CRD and optional inquiries to external entities 3 the generation and dispatch of outgoing messages to support the generation and dispatch of confirmation etc. messages to support various billing transactions to support the generation of scheduled and or on demand reports etc. The specific WorkFlows that were just described are exemplary only it will be readily apparent to one of ordinary skill in the relevant art that numerous other WorkFlow arrangements alternatives etc. are easily possible.

A SP may maintain a repository e.g. a database into which selected details of all administrative messaging etc. activities may be recorded. Among other things such a repository may be used to support 

1 Scheduled e.g. daily weekly etc. and or on demand reporting with report results delivered through SMS MMS etc. messages through E Mail through a WWW based facility etc.

2 Scheduled and or on demand data mining initiatives possibly leveraging or otherwise incorporating one or more external data sources with the results of same presented through Geographic Information Systems GISs visualization etc. facilities and delivered through SMS MMS etc. messages through E Mail through a WWW based facility etc.

It is important to note that while aspects of the discussion that was presented above referenced the use of TNs SCs etc. it will be readily apparent to one of ordinary skill in the relevant art that other message address identifiers are equally applicable and indeed are fully within the scope of the present invention.

The discussion that was just presented referenced several specific messaging paradigms including MMS E Mail etc. These paradigms potentially offer an incremental advantage over other paradigms in that native support may be commonly found on a WD that a potential MS would be carrying. However it is to be understood that it would be readily apparent to one of ordinary skill in the relevant art that numerous other paradigms such as for example SMS IM Internet Protocol IP Multimedia Subsystem IMS Wireless Application Protocol WAP etc. are easily possible and indeed are fully within the scope of the present invention.

It is important to note that the hypothetical example that was presented above which was described in the narrative and which was illustrated in the accompanying figures is exemplary only. It is not intended to be exhaustive or to limit the invention to the specific forms disclosed. It will be readily apparent to one of ordinary skill in the relevant art that numerous alternatives to the presented example are easily possible and indeed are fully within the scope of the present invention.

