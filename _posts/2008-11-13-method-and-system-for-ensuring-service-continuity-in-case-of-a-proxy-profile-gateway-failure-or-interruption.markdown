---

title: Method and system for ensuring service continuity in case of a proxy profile gateway failure or interruption
abstract: Aspects of the present invention relate to methods, systems and computer products that guarantee the availability of basic services to subscribers during the failure of a Proxy-Profile Gateway. An independent module equipped with monitoring probes for tracking the actual location of the end-customer, an interface for controlling the Gateway availability, and an active SS7 signaling interface are also provided, in order to initiate the recovery procedures, along with a database for storing the relevant information necessary to apply the restoration procedures.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09264922&OS=09264922&RS=09264922
owner: MOBILEUM INC.
number: 09264922
owner_city: Santa Clara
owner_country: US
publication_date: 20081113
---
This application is a continuation in part of U.S. patent application Ser. No. 10 635 804 titled Method And System For Cellular Network Traffic redirection filed Aug. 5 2003 now U.S. Pat. No. 7 072 651. It is also a continuation in part of U.S. patent application Ser. No. 11 979 537 titled Method and system for providing roaming services to inbound roamers using visited network gateway location register filed Nov. 5 2007 and U.S. patent application Ser. No. 11 979 538 titled Method and system for providing roaming services to outbound roamers using home network Gateway Location Register filed Nov. 5 2007 now abandoned. It is also a continuation in part of U.S. patent application Ser. No. 11 280 862 titled Border Roaming Gateway filed Nov. 17 2005 now abandoned and of U.S. patent application Ser. No. 11 294 329 titled Scalable Messaging Forwarding filed Dec. 6 2005 now abandoned and of U.S. patent application Ser. No. 11 711 681 titled Method and System for Applying Value Added Services on Messages Sent to a Subscriber s Mobile Communication filed Feb. 28 2007 and of U.S. patent application Ser. No. 10 782 681 titled Providing multiple MSISDN numbers in a mobile device with a single IMSI filed Feb. 18 2004 now U.S. Pat. No. 7 277 431 and of U.S. patent application Ser. No. 11 700 964 titled Method and System for Keeping all Phone Numbers Active While Roaming With Diverse Operator Subscriber Identity Modules filed Feb. 1 2007 and of U.S. patent application Ser. No. 10 918 644 titled Multiple IMSI with Multiple Single MSISDN MIMM Service in a Single SIM for Multiple Roaming Parties filed Aug. 13 2004 now abandoned. All of these related patent applications are incorporated herein by this reference in their entirety herein.

Many mobile operators today are deploying or have deployed signaling gateway based value added services in their core network. These signal gateways often need to store the user profile for delivering the expected services. Since these gateways play a role of HLR in regard to VLR and VLR in regard to HLR it is hereafter termed as Proxy Profile Gateway .

As is know in the art see e.g. U.S. patent application Ser. No. 10 782 681 titled Providing multiple MSISDN numbers in a mobile device with a single IMSI filed Feb. 18 2004 U.S. patent application Ser. No. 11 700 964 titled Method and System for Keeping all Phone Numbers Active While Roaming With Diverse Operator Subscriber Identity Modules filed Feb. 1 2007 and U.S. patent application Ser. No. 10 918 644 titled Multiple IMSI with Multiple Single MSISDN MIMM Service in a Single SIM for Multiple Roaming Parties filed Aug. 13 2004 Signal Gateways for multiple numbers have been developed and deployed for mobile operators to offer multiple country numbers for a subscriber with a single IMSI of a home operator multiple numbers of the same operator for a subscriber with a single IMSI multiple devices or IMSI with a single number of the same operator multiple devices and multiple country numbers for a subscriber of a home operator etc. In all these solutions the signal gateway doubles as a virtual HLR to the real VLR and a virtual VLR to the real HLR. This is to ensure that the signal gateway can control and offer value added services for the subscribers located either at a home network or roaming. However the above approach suffers from a serious drawback in that mobile terminated services e.g. calls and SMS will not be available to subscribers when the gateway goes down until the subscribers change VMSC VLR locations. Although the intended service offered by the signal gateway may not be available it is critical that the subscribers continue to have basic services available.

U.S. patent application Ser. No. 11 979 537 titled Method and system for providing roaming services to inbound roamers using visited network gateway location register filed Nov. 5 2007 and U.S. patent application Ser. No. 11 979 538 titled Method and system for providing roaming services to outbound roamers using home network Gateway Location Register filed Nov. 5 2007 the entirety of each of which is incorporated by this reference herein propose an advanced gateway location register on the GLR standard 3GPP 23119 to deal with the fail over effects of GLR and to handle stuck handsets due to traffic steering. A Gateway Location Register is a core network element that aims to optimize the signaling exchange between different networks. It is fully described in the ETSI standards ETSI TS.129.120 and TS.123.119 . It is usually deployed in a VPMN network and doubles as a virtual HLR to the real VLR and a virtual VLR to the real HLR. These disclosures use a one on one mapping between a GLR GT and a real VLR GT for the virtual VLRs to the HPMN HLRs and another one on one mapping between a GLR GT and a real HLR GT for the virtual HLRs to the VPMN VLRs. This helps at least for an inbound roamer to receive MT services when the GLR goes down as long as the roamer has not changed VLR VMSC location since its first registration with the VPMN network. Of course subsequent to GLR going down any new VMSC VLR changes will naturally restore the MT service. However these disclosures do not entirely solve the problem of an inbound roaming receiving MT services when the GLR goes down even though the roamer has changed VLR VMSC location since its first registration with the VPMN network.

It is recognized that when the proxy gateway goes down some enhanced services offered by the gateway will not be available to subscribers. However at least the subscribers basic services excluding the enhanced ones provided by the gateway should still be available. Therefore there remains a need in the art for improving the state of the art for assuring the availability of the basic subscriber services even during a downtime of the Proxy Gateway. Further there remains a need in the art for improving the mechanisms for stopping a Proxy Profile Gateway activity as may be required for operations and maintenance purposes.

Aspects of the present invention overcome the above identified problems as well as others by providing systems computer products and that guarantee the availability of the basic services of subscribers during the failure of a Proxy Profile Gateway.

Aspects of the present invention provide a secured mechanism for stopping a Proxy Profile Gateway traffic management in case of operations and maintenance activity.

Aspects of the present invention provide an independent system that is equipped with monitoring probes for tracking the actual location of the end customer an interface for controlling the Gateway availability an active SS7 signaling interface in order to initiate the recovery procedures and a database for storing the relevant information necessary to apply the restoration procedures. The term external module is used interchangeably herein with the term ProxySaver. 

In accordance with aspects of the present invention the ProxySaver sends a sequence of signaling messages to each affected subscriber so to generate a new location update message to ensure both real VLR and real HLR have each other s respective information so that the subscriber can at least have the basic services available when the Proxy Profile Gate goes down. Aspects of the present invention improve on the technique disclosed in U.S. Pat. No. 7 072 651 where a MT call signaling message is generated to hope for a location update. However this earlier art is limited to the case where there is more than one VMSC for a VLR which is generally not the case today. Aspects of the present invention deal not only with the virtual HLR issues in the real VLR but also with all other situations in which the problem arises.

Aspects of the present invention are applicable not only to inbound and outbound roamers but to local subscribers as well. Therefore the term subscriber as used herein refers to a generic subscriber not only limited to home subscribers and can denote inbound and outbound roamers.

Additional advantages and novel features of the invention will be set forth in part in the description that follows and in part will become more apparent to those skilled in the art upon examination of the following or upon learning by practice of the invention.

A Proxy Profile Gateway such as a Gateway Location Register Gateway or a Single IMSI Multiple MSISDN SIMM system stores user profile information in order deliver value added services to the hosting operator. Typically the Proxy Profile Gateway may aim to reduce the number of signaling exchanges between networks by caching the location procedures between VLRs of a distant PLMN or offer multiple MSISDN to a subscriber without the need of deploying several SIM Cards or possessing multiple handsets.

In all cases the Proxy Profile Gateway interchangeably referred to herein as PPG Gateway and Proxy Gateway acts as a proxy MSC VLR from a HLR perspective and as a proxy HLR from a MSC VLR perspective.

The messages referring to operations involving the HPMN HLR may be routed towards the PPG by modifying the destination addresses or by applying tunneling mechanisms e.g. adapting the Translation Type number associated to the Global Titles and encapsulating the messages in IP protocols among other mechanisms.

The approach of replacing the network nodes Global Titles by Gateway managed addresses is denominated the dummy GT method. The benefit of modifying the addresses has been shown in U.S. patent application Ser. No. 11 979 537 titled Method and system for providing roaming services to inbound roamers using visited network gateway location register filed Nov. 5 2007 and U.S. patent application Ser. No. 11 979 538 titled Method and system for providing roaming services to outbound roamers using home network Gateway Location Register filed Nov. 5 2007.

Alternatively the methods that do not require any modification of the Global Title addresses e.g. based on Translation Type modification are referred to as Tunneling methods.

The analysis is split into 2 sub sections as the routing design may have an impact on the current state of the art limitations. Three cases must be evaluated in case of PPG unavailability 

1. no end user movement before the Gateway unavailability the end user remains attached to the same VLR 

For each of the case the impact on the service must studied for the Mobile Originated activity e.g. initiation of a voice call or a SMS or for the Mobile Terminated activity e.g. reception of a voice call or a SMS .

The operator decides to use dummy GT when establishing dialogues between the Gateway and the other network nodes. It defines VLR dummy GT and HLR dummy GT. This architecture is presented in .

The operator defines dummy GT for each of its VLR. The dummy GT real VLR GT mapping may be based on straightforward numbering modification e.g. real VLR CCNDC000xyz dummy GT CCNDC100xyz.

Once the Profile Proxy function activated the HLR records the dummy VLR after the successful processing of the first update location.

Similarly a Global Title modification is also applied to the HLR address. The mapping between the dummy and real is generally dynamic as the Proxy Gateway may not always be aware of the HLR addresses that its Proxy Gateway may face mainly in the case of roaming value added services.

In order to determine the role of the ProxySaver it is necessary to review the Mobile Terminated scenario and Mobile Originated scenario 

No End User Movement Before the Gateway Unavailability The End User Remains Attached to the Same VLR 

The HLR may acquire MT related information e.g. send the MAP Provide Roaming Number message by polling the network operator using the dummy GT address.

The operation can successfully executed at condition that the network operator is able to define for each of the dummy VLR GT a second route that points to the corresponding actual VLR.

The end user moves from VLR1 to VLR2 while the Gateway is up and running. The HLR has recorded the dummy GT of VLR1 since the subsequent movements are cached by the Gateway.

The HLR may acquire MT related information i.e. send the MAP Provide Roaming Number message by polling the network operator using the dummy GT VLR1 address.

At reception of the MAP PRN the VLR1 may provide a MSRN and invoke a restoration procedure. The call may be unsuccessfully connected since the end user is not under coverage of the MSC VLR1. At best a Call Forward under Out of Reach condition takes place.

In the case of a SMS MT the restoration procedure is not invoked and the MSC VLR returns an Absent Subscriber error to the Home SMS C.

In this case the network operator STP detects the unavailability of the Gateway at the time the end user moves. The Update Location messages are directly routed to the HLR which in return records the actual and latest VLR location. It is assumed that the VPMN is able to detect the Gateway unavailability and route the message to the HPMN E.214 MGT. For example the VLR can use a prefix E.214 MGT for routing to the message to the Gateway. In case of failure the STP strips the prefix away and route the message to the HLR E.214 on it secondary route.

The first successful location update initiated by a VLR is performed using the E.214 i.e. IMSI derived address MGT of the roaming partner. However the VLR stores the E.164 address of the responding HLR and the subsequent interactions between the VLR and the HLR are based on this address. In the Gateway context the VLR recorded information is the dummy HLR GT.

As previously indicated the dummy HLR address may be associated dynamically by the Gateway. Indeed it is unlikely the VPMN knows in advance all the real HLR GT of all its roaming partners in the case of roaming related services. Therefore the dummy GT allocation is rather done on the fly. The STP cannot be configured in advance to map the dummy GT and the real GT of the HLR.

In case the VLR needs to contact the HLR it uses the stored E.164 address. The subsequent interactions can end user initiated e.g. Supplementary Service interaction USSD interaction or VLR initiated e.g. for a periodical Update Location for requesting authentication parameters notifying HLR readiness for receiving SMS etc. . In the case of Gateway unavailability this may fail as the dummy E.164 GT cannot be mapped to the original HLR E.164 dynamically at the STP level.

One resolution would be to fall back to the E.214 address on the STP secondary route. However this requires specific address modification capability at the STP level since it must recreate the SCCP E.214 address based on the end user IMSI information in the MAP message part.

If this is not the case authentication failures may occur after the inbound end user has used all the previously received authentication triplets for example. USSD based services will also be affected typically USSD call back services for prepaid roamers.

This scenario highlights similar issues as the ones presented in the previous section and also demonstrates that the need for enhancing the state of the art.

In this case the network operator STP detects the unavailability of the Gateway at the time the end user moves. The Update Location messages are directly routed between the VLR and HLR which in return records the actual and latest location information. The MO scenario takes place seamlessly.

From the previous analysis we see that there is a need for both MO and MT scenario in order to secure the roaming services in the context of an implementation based on a Dummy GT configuration.

The operator decides to use a Tunneling Method e.g. a Translation Type modification approach for establishing dialogues between the Gateway and the other network nodes. This architecture is presented in as previously indicated. In this scenario the VLR and HLR addresses are recorded transparently respectively in the HLR and the VLR.

In order to determine the role of the ProxySaver it is necessary to review the limitations of the current state of the art in the context of a Mobile Terminated scenario and Mobile Originated scenario 

No End User Movement Before the Gateway Unavailability the End User Remains Attached to the Same VLR 

The HLR will intend to get MT related information e.g. send the MAP Provide Roaming Number message by polling the network operator using the real GT address.

The operation can successfully executed at condition that the network operator is able to define a second route that points to the corresponding actual VLR.

The end user moves from VLR1 to VLR2 while the Gateway is up and running. The HLR has recorded the real GT of VLR1 since the subsequent movements are cached by the Gateway.

The HLR will intend to get MT related information i.e. send the MAP Provide Roaming Number message by polling the network operator using the GT VLR1 address.

At reception of the MAP PRN the VLR1 will invoke provide a MSRN and a restoration procedure. The call will be unsuccessfully connected since the end user is not under coverage of the MSC VLR1. At best a Call Forward under Out of Reach condition takes place.

In the case of a SMS MT the restoration procedure is not invoked and the MSC VLR returns an Absent Subscriber error to the Home SMS C.

In this case the network operator STP detects the unavailability of the Gateway at the time the end user moves. The Update Location messages are directly routed to the HLR which in return records the actual and latest VLR location. The MT scenario takes place seamlessly.

No End User Movement Before the Gateway Unavailability the End User Remains Attached to the Same VLR 

The first successful location update initiated by a VLR is performed using the E.214 i.e. IMSI derived address MGT of the roaming partner. However the VLR stores the E.164 address of the responding HLR and the subsequent interactions between the VLR and the HLR are based on this address.

Because the Tunneling approach enables the storage of the HLR addresses transparently i.e. the VLR always contains the real HLR address of the end user.

The unavailability of the Gateway has no impact for reaching the actual HLR under the assumption that a second route is defined and available for reaching the end user s HLR.

As above it appears that there is no impact on this scenario when using the translation type approach.

In this case the network operator STP detects the unavailability of the Gateway at the time the end user moves. The Update Location messages are directly routed to the HLR which in return records the actual and latest VLR location. The MO scenario takes place seamlessly.

The ProxySaver is an independent system that is equipped with monitoring probes for tracking the actual location of the end customer an interface for controlling the Gateway availability an active SS7 signaling interface in order to initiate the recovery procedure and a database for storing the relevant information necessary to apply the restoration procedure.

This enables the collection of the required information for the proxied profiles and enable storing for each subscriber that is controlled by the proxy the IMSI MSIDN actual VLR MSC and HLR and the proxy VLR MSC and HLR addresses.

This enables the ProxySaver to track movements of customer during a recovery procedure and to optimize it accordingly. As shown above users getting attached to a new MSC VLR after a GLR failure are not subject to MO MT service availability.

This also enables tracing the completion of the restoration procedure and detecting the procedure failure e.g. in case of Steering of Roaming applied by the Home Operator temporary SS7 connectivity issue . In case of unsuccessful procedure completion the ProxySaver can re initiate it.

Depending on the technical system architecture the following issues may identified in case of GLR failure a resulting from the MSC VLR address recorded in the HLR and b resulting from the HLR address recorded in the VLR.

Addresses stored in the VLR and in the HLR must be modified. It may by invoking an Update Location procedure from the VLR where the end user is located. However because the Update Location cannot be performed using the E.164 dummy address stored in the system it is necessary to develop a strategy that erases the subscriber information.

The ProxySaver sends a MAP CANCEL LOCATION in order erase temporarily the user. Subsequently the ProxySaver sends a MAP PROVIDE ROAMING NUMBER in order to restore the user profile in the actual VLR. Because the user profile was deleted from the VLR with the MAP CANCEL LOCATION the VLR may initiate the MAP RESTORE DATA procedure with the E.214 address and therefore the dialogue with the HLR will be established seamlessly.

As mentioned in 123.007 the VLR will now have the user profile in its register. The associated flags Subscriber Information Confirmed by HLR and Location Information Confirmed in HLR are marked as Confirmed while the Confirmed by Radio Contact set to Not Confirmed. 

Once the profile restoration is completed the ProxySaver sends MAP RESET to the VLR in order to re initialize the Location Information Confirmed in HLR to Not Confirmed. 

There is no modification of the Subscriber Data confirmed by HLR and the Confirmed by Radio Contact flag status.

The ProxySaver may initiate a Mobile Terminated Short Message a Subscriber Location Request or a Network Initiated USSD command towards the real MSC hosting the end user.

At reception of the MAP MT FORWARD SM or MAP PROVIDE SUBSCRIBER LOCATION or MAP PROCESS UNSTRUCTURED SS REQUEST at the real MSC a paging occurs and upon successful paging procedure completion a MAP PROCESS ACCESS REQUEST is sent from the MSC to the VLR. Consequently the VLR checks at reception of the MAP PROCESS ACCESS REQUEST the state of the Location Information Confirmed in HLR . As the flag is set to Not Confirmed the VLR initiates an Update Location procedure which results in the recording of the actual VLR MSC address information in the HLR and the actual HLR address information in the VLR.

As noted in the Gateway failure discussion the tunneling relation restoration procedure only needs to modify the VLR MSC information stored in the HLR. This is due to the end point transparency offered by this kind of implementation.

Two approaches are proposed for solving the issue. The first is completely managed by the ProxySaver while the second is initiated by the ProxySaver and then handled by the VLR hosting the end user.

While both approaches solve the issue with the same effectiveness dimensioning issue may lead the operator to prefer one approach to the other.

When needed the ProxySaver fires an Update Location to the real HLR of the end user. While the addressing parameters SCCP Calling Party refer to the ProxySaver address the message content indicates the real VLR MSC addresses of the node hosting the user.

When needed the ProxySaver fires a MAP RESET message to the real VLR hosting the end user. Subsequently the ProxySaver sends a MAP MT FORWARD SM or MAP PROVIDE SUBSCRIBER LOCATION or MAP PROCESS UNSTRUCTURED SS REQUEST to the real MSC. A paging occurs then and upon successful paging procedure completion a MAP PROCESS ACCESS REQUEST is sent from the MSC to the VLR. Consequently the VLR checks at reception of the MAP PROCESS ACCESS REQUEST the state of the Location Information Confirmed in HLR . As the flag was set to Not Confirmed at the MAP RESET reception the VLR initiates an Update Location procedure which results in the recording of the actual VLR MSC address information in the HLR and refreshes the actual HLR address information in the VLR. illustrates this mechanism.

The above two methods may also be used in case of Dummy GT integration. However in this case it only guarantees that MT activity is restored.

The ProxySaver is independent from the Profile Proxy Gateway. In order to avoid any disruptive action from the ProxySaver a handshake mechanism is available between the two entities. It enables the Gateway to inform the ProxySaver about its state.

The detection of a Gateway failure is based on two approaches. The Gateway itself may detect itself is malfunction and inform the ProxySaver through their communication link. The ProxySaver also monitors the links between the connected to the Gateway and may identify a service malfunction no messages one way messaging etc. 

Once the failure is detected the ProxySaver parses its database contained all the profiles of the proxied users. It then applies the most appropriate method as described earlier for restoring the end user services.

In the course of the restoration procedures for the complete set of end user stored in its internal database the ProxySaver continues to monitor the Update Location activity between the STP and the HLR. It can thereby detect any Location Update triggered by a natural movement of the end user. Upon success of this mobile initiated procedure it may remove the corresponding end user from the set of users to be restored. Therefore by identifying these end users that performs a MS initiated Location Update the system optimizes the recovery procedure and delay.

While the present invention has been described in connection with various aspects of the present invention it will be understood by those skilled in the art that variations and modifications of the aspects of the present invention described above may be made without departing from the scope of the invention. Other aspects will be apparent to those skilled in the art from a consideration of the specification or from a practice of the invention disclosed herein.

