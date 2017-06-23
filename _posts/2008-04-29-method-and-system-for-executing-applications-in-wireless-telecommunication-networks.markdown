---

title: Method and system for executing applications in wireless telecommunication networks
abstract: A method and system allow a mobile device user to automatically execute a service application to provide a requested service. The user may enter a USSD code or initiate a voice call to a special number. The wireless network recognizes the user's act as a request for a specific service and notifies the service provider. The service provider sends an activation command to the mobile device and may also initiate installing the service application.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08311518&OS=08311518&RS=08311518
owner: Esmertec France
number: 08311518
owner_city: Bagneux
owner_country: FR
publication_date: 20080429
---
The present invention relates to the field of value added services in wireless telecommunication networks. More specifically the invention discloses techniques for installing and starting Java applications on mobile stations in a user friendly way.

In wireless telecommunication networks such as GSM and other networks many mobile devices and mobile stations MS such as mobile phones and Personal Digital Assistants may execute Java applications. Such applications are typically converted to the Java byte code format described in U.S. Pat. No. 5 815 661 by Gosling packaged together with data into JAR files and installed in the memory of the MS. Applications typically interact with the MS through standardized sets of Application Programming Interfaces such as the Mobile Information Device Profile MIDP version 2.0 described in JSR 118 by Sun Microsystems. Such applications are called MIDlets.

The graphical user interface of a MIDP compliant MS typically includes means for starting MIDlets such as menus icons or a special application called the MIDlet Manager. It has been found that this method of starting MIDlets has the following limitations which are detrimental to the market acceptance of MIDlets. First in order to start a MIDlet the user must typically press a complex sequence of buttons and or navigate several layers of menus. Second the look and feel of these buttons and or menus is not standardized across different brands and models of mobile devices.

Another method for starting MIDlets is the MIDP Push Registry described in JSR 118 by Sun Microsystems. The Push Registry API allows a MIDlet to be registered with the Push Registry of the MS so that the MS will start the MIDlet automatically whenever a specific triggering event occurs. The triggering event is typically an incoming Short Message SMS containing an Application Port Addressing Information Element as specified by GSM TS 03.40. It should be noted that the Push Registry is not intended to allow the user to start a MIDlet rather service providers typically use the Push Registry to trigger the processing of inbound information such as incoming messages in an Instant Messaging service.

WAP browsers gateways and servers are another feature of wireless telecommunication networks. A user can typically use the WAP browser of a MS to download install and run a MIDlet though this method suffers from the same limitations as the methods mentioned previously. The WAP standard also includes a mechanism called WAP Push. WAP Push allows a service provider to send an SMS that will cause a MS to open and display a WAP address without requiring the user to enter the address manually. There are three kinds of WAP Push messages Service Indication SI messages are encoded in WBXML and contain some text as well as the WAP address Service Loading SL messages are encoded in WBXML and only contain the WAP address clickable SMS are plain text SMS containing the WAP address.

Unstructured Supplementary Service Data USSD is a standard feature of GSM networks and is originally described in GSM TS 02.90 03.90 and 04.90. USSD provides a text only bidirectional interactive and session oriented channel of communication between mobile stations and servers in the Public Land Mobile Network PLMN . A mobile initiated USSD request is typically used to start an interactive dialogue between the user of a MS and an application running on a remote computer such as a HLR or a USSD service platform.

Special Numbers are a feature of telecommunication networks. Most networks can be configured so that whenever a subscriber dials a specific number such as a short number or a non geographic number or a premium number the call will not be routed like a regular voice call and will instead be controlled by a special server. Such behavior is supported for example by the standards INAP described in ITU recommendation Q.1218 and Q.1228 and CAMEL described in 3GPP TS 23.078 .

Another feature of wireless telecommunication networks is the Mobile Telephony API MTA specified in JSR 253 by Sun Microsystems. The MTA allows a MIDlet to be notified of outgoing voice calls and mobile initiated USSD requests.

An object of the invention is to provide a method for installing and starting MIDlets on mobile stations that is easy to remember and familiar for users. A second object is to provide a method that works identically with many brands and models of mobile stations. A third object is to provide a method that works identically with many network operators.

In one embodiment of the invention a service provider informs a user that a service can be accessed by dialing a USSD code. When the user dials the USSD code the MS recognizes that the code is a USSD code and sends a USSD message to the PLMN over a wireless connection. The PLMN recognizes that the USSD message is associated with the service and notifies the service provider. The service provider recognizes the notification as an activation request for the service formats a Push Registry trigger message with an Application Port matching that of a previously installed MIDlet and sends it to the MS. Upon receiving the Push Registry trigger message the MS starts the MIDlet.

In another embodiment of the invention a service provider informs a user that a service can be accessed by dialing a Special Number. When the user dials the Special Number the MS initiates a voice call over a wireless connection. The PLMN recognizes that the voice call is associated with the service and notifies the service provider. The PLMN may either reject the voice call or connect it to a pre recorded voice message which will inform the user that his request is being processed. The service provider recognizes the notification as an activation request for the service formats a Push Registry trigger message with an Application Port matching that of a previously installed MIDlet and sends it to the MS. Upon receiving the Push Registry trigger message the MS starts the MIDlet.

Both embodiments can be improved as follows so that the MIDlet will be installed automatically. Upon receiving the activation request from the MS the service provider queries a database to determine whether the MS has already installed the MIDlet. If not the service provider sends a WAP Push to the MS containing the WAP address of a JAD or JAR file containing the MIDlet. The MS receives the WAP Push message downloads the JAD or JAR file and installs the MIDlet. The MIDlet signals to the service provider that it has been successfully installed typically by sending a WAP or HTTP request and the service provider updates the database accordingly.

Both embodiments can also be improved to improve the efficiency of sending the Push Registry trigger message to the MS. The service provider ensures that the Push Registry trigger message is delivered to the MS before the PLMN rejects or terminates the USSD dialogue or the voice call. In this case the PLMN may transmit the SMS message to the MS over a wireless signaling channel such as a SDCCH or a SACCH or a FACCH which is already allocated for the purpose of controlling the USSD dialogue or the voice call hence avoiding the cost of establishing a new signaling channel.

It is expected that both embodiments can be improved by taking advantage of the Mobile Telephony API in order to reduce latency and network traffic. A MIDlet invokes a method for example TelephonyManager.addTelephonyManagerListener to register for receiving service activation requests. Whenever the user dials a service activation request the MTA implementation notifies the MIDlet by invoking TelephonyManagerListener.notifyOutgoingUnstructuredService or TelephonyManagerListener.notifyOutgoingCall . The MIDlet recognizes the notification as a service activation request and behaves accordingly. The MIDlet may also invoke a method for example Call.terminate or UnstructuredService.terminate in order to avoid sending unnecessary messages to the PLMN.

While the invention is described in the context of GSM networks it is understood that some of the inventive aspects can be ported to similar current or future wireless telecommunication networks such as 3 G UMTS networks and CDMA networks.

A method and system are provided for automatically installing and executing appropriate service applications on a mobile device responsive to a user request for a service. The installation process is simplified for the user s convenience and is identical from the user s perspective for different mobile devices and wireless carriers.

A service provider may inform a user that a service can be accessed by dialing a specified USSD code associated with a service for example 100 . When the user dials the USSD code the mobile device transmits the code to the PLMN where it is recognized and forwarded to an associated service provider. The service provider formats a Push Registry trigger message with an Application Port matching that of a previously installed application and sends it to the mobile device. Upon receiving the Push Registry trigger message the mobile device starts an application to provide the requested service.

A mobile device or mobile station may be in wireless communication with a PLMN over a wireless network. The PLMN may be in communication with a service provider . The service provider may provide a requested service to the mobile device .

In a user may input the specified USSD code associated with a requested service such as 100 into the mobile device . The mobile device may transmit the code to the PLMN over the wireless network

In the PLMN may receive the USSD code and invoke a handling routine. For example the PLMN may access a lookup table to determine whether the USSD code is valid and what service is associated with the code.

In the PLMN may determine an appropriate service provider to invoke and transmit a command to the service provider with the user request. The service provider may respond with a response to the PLMN . The response may be an acknowledgement or other message.

In the PLMN may transmit a response to the mobile device starting the application to perform the requested service. For example the response may indicate the mobile device s request has been processed and a response from the service provider is forthcoming. In the mobile device may receive the response from the PLMN .

In the service provider may format a Push Registry trigger message with an Application Port matching that of a previously installed application and transmit the message to the mobile device . In the mobile device may receive the message from the service provider .

In the mobile device may trigger the push registry as instructed by the service provider message. In the application such as a MIDlet may be started to provide the requested service.

In an alternative embodiment the service may be accessed by dialing a Special Number. When the user dials the Special Number the mobile device initiates a voice call over a wireless connection. The PLMN recognizes the voice call to the special number and the associated service and notifies the service provider. The PLMN may reject the voice call or connect it to a pre recorded voice message informing the user his request is being processed. The service provider recognizes the activation request for the service formats a Push Registry trigger message with an Application Port matching that of a previously installed MIDlet and sends it to the mobile device. Upon receiving the Push Registry trigger message the mobile device starts the MIDlet.

In an alternative embodiment the efficiency of sending the Push Registry trigger message to the mobile device may be improved. The service provider may ensure the Push Registry trigger message is delivered to the mobile device before the PLMN rejects or terminates the USSD dialogue or the voice call. In this case the PLMN may transmit the SMS message to the MS over a wireless signaling channel such as a SDCCH or a SACCH or a FACCH which is already allocated for the purpose of controlling the USSD dialogue or the voice call hence avoiding the cost of establishing a new signaling channel.

A mobile device or mobile station may be in wireless communication with a PLMN over a wireless network. The PLMN may be in communication with a service provider . The service provider may provide a requested service to the mobile device .

In a user may input the specified USSD code associated with a requested service such as 100 into the mobile device . The mobile device may transmit the code to the PLMN over the wireless network.

In the PLMN may receive the USSD code and invoke a handling routine. For example the PLMN may access a lookup table to determine whether the USSD code is valid and what service is associated with the code.

In the PLMN may determine an appropriate service provider to invoke and transmit a command to the service provider with the user request. The service provider may query an accessible database with a transmitted mobile device identifier to determine whether the required application is already installed on the mobile device. The service provider may respond with a response to the PLMN . The response may be an acknowledgement or an indication that the required application must be installed.

In the PLMN may transmit a response to the mobile device . For example the response may indicate the mobile device s request has been processed and a response from the service provider is forthcoming. In the mobile device may receive the response from the PLMN .

In the service provider may format a WAP Push to the mobile device containing the WAP address of a JAD or JAR file containing the required application such as a MIDlet. In the mobile device may receive the message from the service provider .

In the mobile device may process the received WAP Push message. In the mobile device may automatically start an installed WAP browser and pass the embedded WAP address to the browser. In the browser may attempt to download the required application.

In the service provider may receive the request from the mobile device for the requested application. The requested application in installable form such as a JAD or JAR file may be transmitted to the mobile device .

In the mobile device may receive the install files and install the requested application. In the mobile device may execute the requested application and provided the requested service to the user.

In the mobile device may transmit a message to the service provider indicating the requested application was successfully installed. The service provider may update an appropriate entry in its database.

In upon execution the MIDlet may invoke a method such as TelephonyManager.addTelephonyManagerListener to register for receiving service activation requests from the mobile device .

In the user may dial a service activation request such as a USSD code 100 . The MTA implementation of the mobile device notifies the MIDlet of the request by invoking a method such as TelephonyManagerListener.notifyOutgoingUnstructuredService or TelephonyManagerListener.notifyOutgoingCall .

In the MIDlet receives and recognizes the notification as a service activation request and provides the requested service.

In the MIDlet may also invoke Call.terminate or UnstructuredService.terminate to prevent sending unnecessary messages to the PLMN as the MIDlet is already installed and executing on the mobile device .

It will be appreciated that the above procedures may execute on various types of wireless networks such as GSM networks 3 G UMTS networks and CDMA networks.

A wireless network may be for example a GSM network a 3G UMTS network a CDMA network a data network or any other wireless network configured to provide wireless communications to the mobile device .

A server may be in communication with the mobile device over the wireless network . The server may be configured to administrate the wireless network and route communications between devices both on and off the wireless network .

A service provider may be in communication with the server and be configured to provide a requested service to mobile devices. For example the service may include providing user selected content to a user s mobile device . The service provider may include software data and logic required to provide the requested service.

It will be appreciated that the service provider may be configured to provide more than one type of requested service. It will be appreciated that any number of service providers may exist in the system to provide any number of requested services.

An installation database may be configured to store information regarding whether a service application has been installed on the mobile device . Additional information such as a version number of the installed application a date and time of install and other information may also be stored.

It will be appreciated that in a multiple service multiple mobile devices environment the database may store information regarding what applications are installed on which mobile devices.

It will be appreciated that a system may include any number of mobile devices wireless networks servers service providers and installation databases.

In the server may receive a user request for service activation from a mobile device. The user may input the request as a USSD code or dialing a special number as discussed above. The mobile device may be a cellular device.

In the server may optionally test whether a service application is installed and available on the mobile device. Alternatively the server may simply forward the request to the service provider which will then test whether the service application is installed and available on the mobile device. The service application may be a MIDlet.

In the server or service provider may execute a remote installation of the required service application if required. For example a WAP address may be provided to the mobile device from where the required service application may be downloaded and installed.

In the server or service provider may optionally update an installation status of the service application on the mobile device in an installation database. The installation database may store the install status of a plurality of service applications on a plurality of mobile devices in the system and eliminate redundant installs on the mobile devices.

In the server or service provider may transmit an activation command to the mobile device activating the service application and providing the requested service. If the service application is not yet executing on the mobile device the command may execute the service application. The activation command may be a MIDP Push Registry.

An example embodiment of the present invention is a method. The method may include responsive to a user service request at a mobile device determining if an appropriate service application is available on the mobile device. The method may include if the appropriate service application is not available on the mobile device transmitting an installation request to a service provider over a wireless network. The method may include receiving an installation command for a requested service. The method may include activating the requested service on the mobile device with the installation command. The method may include downloading the appropriate service application over the wireless network. The method may include executing the downloaded service application. The wireless network may be a Public Land Mobile Network. The mobile device may be a cellular device. The installation command may be a WAP Push message. The service application may be a MIDlet. The installation command may include a WAP address where the service application is available for installation. The service activation request may be a mobile initiated USSD request. The service activation request may be an outgoing call from the mobile device to a Special Number.

Another example embodiment of the present invention may be a method. The method may include responsive to receiving a user request for service activation over a wireless network from a mobile device determining whether an appropriate service application is available on the mobile device. The method may include if the appropriate service application is not available on the mobile device execute a remote installation of the appropriate service application. The method may include transmitting an installation command to the mobile device the installation command configured to execute the appropriate service application on the mobile device. The installation command may include a download address where the appropriate service application is available. The download address may be a WAP address. The method may include updating an installation status of the appropriate service application on the mobile device. The installation command may be a WAP Push Registry message. The wireless network may be a Public Land Mobile Network. The mobile device may be a cellular device. The service application may be a MIDlet. The service activation request may be a mobile initiated USSD request. The service activation request may be an outgoing call from the mobile device to a Special Number.

Another example embodiment of the present invention may be a system. The system may include a wireless network. The system may include a service provider in communication with the wireless network. The service provider may be configured to responsive to receiving a user request for service activation received over the wireless network transmitting an installation command. The system may include a mobile device in communication with the service provider over the wireless network. The mobile device may be configured to responsive to a user service request at a mobile device determining if an appropriate service application is available on the mobile device. The mobile device may be configured to if the appropriate service application is not available on the mobile device transmitting an installation request to the service provider over the wireless network and activating the requested service on the mobile device with a received installation command. The system may include a database storing a list of service applications installed on the mobile device. The system may include a server in communication with the wireless network and the service provider wherein the server forwards information between the mobile device and the service provider. The wireless network may support at least one of data communications and voice communications.

It will be appreciated to those skilled in the art that the preceding examples and embodiments are exemplary and not limiting to the scope of the present invention. It is intended that all permutations enhancements equivalents combinations and improvements thereto that are apparent to those skilled in the art upon a reading of the specification and a study of the drawings are included within the true spirit and scope of the present invention. It is therefore intended that the following appended claims include all such modifications permutations and equivalents as fall within the true spirit and scope of the present invention.

