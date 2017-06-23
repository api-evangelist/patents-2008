---

title: Telecommunications device security
abstract: A terminal () for use with a cellular or mobile telecommunications network () includes authentication means () such as a SIM, USIM, UICC etc. for authenticating the terminal with the network. The terminal further includes a normal execution environment () and a secure execution environment (). An interface controller () is provided in the secure execution environment and intercepts all communications directed to the authentication means to control access to the authentication means by these communications.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09049597&OS=09049597&RS=09049597
owner: VODAFONE GROUP PLC
number: 09049597
owner_city: Newbury, Berkshire
owner_country: GB
publication_date: 20080829
---
The present invention relates to a terminal for use with a cellular or mobile telecommunications network the terminal including authentication means for authenticating the terminal with the network. The present invention also relates to a method of protecting data on the authentication means.

The SIM functions were historically not exposed outside of the closed environment of the GSM UMTS radio unit terminal. However newer U SIMs and UICCs Universal Integrated Circuit Cards are capable of providing a far wider range of possibly security sensitive services to terminal applications. These services could be network related e.g. providing authentication material and cryptographic keys for network access or they could be generic security services such as secure storage or provisioning of data which make use of the security features of a UICC. Due to these additional features that are available on UICCs there has been an increase in the number of terminal applications requiring access to the UICC.

Certain of the UICC access commands are particularly sensitive and access to these commands should be restricted. Examples of such commands include 

In addition access to the UICC could allow a rogue application to launch a denial of service attack on the UICC.

In most terminal implementations access to these sensitive UICC commands is controlled in some way. However as modern mobile terminal operating systems become larger more complex and more prone to security bugs and as we see an increased utilisation of UICC capabilities the risk of unauthorised access to sensitive SIM functions and data is inevitably increased.

A secure channel has previously been proposed to protect communications between the SIM and the terminal and is being standardised through 3GPP SA3 33.110 and ETSI SCP 102.484. A general purpose secure channel may be set up between the UICC and terminal or secure channels may be set up between applications on either side as required.

If a general purpose secure channel is established then this ensures that only an authorised device is able to access the UICC via the secure channel and if sensitive UICC access commands require this channel then this does offer some protection against unauthorised access to these UICC commands. However without adequate protection of the secure channel end point on the terminal side there is no guarantee of protection against a rogue application within the authorised device from accessing sensitive UICC functions.

If an application to application secure channel is established then theoretically only the application end points can access the secure channel. However this relies on the application end points being able adequately to protect their authentication data and keys used to maintain the secure channel. If these are accessible by a rogue application on the device then this rogue application could potentially also have access to the secure channel or could impersonate the authorised application to the UICC.

Therefore the existence of a secure channel does not necessarily guarantee adequate fine grained protection against unauthorised access to sensitive UICC functions.

The technical report 3GPP TR 33.905 issued by 3GPP http www.3gpp.org ftp Specs html info 33905.htm makes recommendations to protect the SIM Application Programming Interfaces APIs in particular those relating to GBA within the terminal. The 3GPP recommendations advocate the use of a server function which acts as a gateway to the UICC card for controlling access to certain specific UICC functions namely GBA I WLAN and credential access.

The Open Mobile Terminal Platform OMTP Application Security Framework v2.0 http www.omtp.org approved.html document describes recommendations for how to manage application access to terminal Application Programming Interfaces APIs . In this framework applications are associated with a level of trust depending whether or not they are certified and if they are certified by whom. Applications certified by operators or manufacturers are the most trusted and unsigned applications are the least trusted.

The Application Security Framework ASF is described in OMTP Application Security Framework v2.0 available from http www.omtp.org approved.html . ASF identifies sets of potentially dangerous APIs and defines the set of APIs that may be accessed by applications at each trust level. For APIs that are accessible at a particular trust level a user prompting regime is also proposed to ensure that dangerous APIs are not used without the user s awareness and permission.

However the OMTP ASF describes how to restrict access to terminal functionality and is not geared towards protection of the UICC functions.

In one aspect the present invention provides a terminal for use with a cellular or mobile telecommunications network the terminal including at least one trusted component for providing trusted services a normal execution environment and a trusted area wherein the terminal further includes an interface controller provided in the trusted area operable to intercept all communications directed to the or each trusted component and further operable to control access to the or each trusted component by the said communications.

The interface controller may also be operable to control access to trusted services provided by the or each trusted component.

The trusted area itself may also provide at least one trusted service. Where this holds the interface controller may be operable to intercept all communications directed to the at least one trusted service provided in the trusted area and further operable to control access to the trusted services provided in the trusted area. The interface controller may then be operable to redirect communications requesting access to at least one trusted service on the or each trusted component to the trusted service provided in the trusted area.

Alternatively or additionally the interface controller may be operable to redirect communications requesting access to trusted services provided in the trusted area to a trusted service on said at least one trusted component.

Advantageously said at least one trusted service provided in the trusted area may be functionally equivalent to at least one of the trusted services of the or each trusted component. In these circumstances communications requesting access to said at least one trusted service on the or each trusted component may be redirected to the functionally equivalent trusted service provided in the terminal and vice versa.

It is noted that while a service may be requested it may not actually be provided in the trusted component or trusted area to which a request has first been directed. In such cases it is advantageous to allow the redirection of the request to a functionally equivalent trusted service that is present on another trusted component or trusted area.

Furthermore the interface controller may be operable to redirect requests from one trusted service to a functionally equivalent trusted service on the same trusted component or indeed from one trusted service in the trusted area to a functionally equivalent trusted service that is also provided in that same trusted area.

Where more than one trusted component is present the interface controller may then be operable to redirect requests from one trusted component to another trusted component. Likewise where more than one trusted area is present the interface controller may then be operable to redirect requests for a trusted service in one trusted area to a trusted service in another trusted area.

The trusted services may include authenticating the terminal with the network. Additionally or alternatively the trusted services may include storage of sensitive data.

The interface controller may be implemented in software which is preferably run in a secure execution environment or may be implemented in hardware.

There may be a plurality of normal execution environments a plurality of trusted areas secure execution environments and or a plurality of trusted components. The interface controller may control access to any one of the trusted components and trusted services provided by the trusted components and may also control access to trusted components services available through any one of the trusted areas secure execution environments.

The trusted component may comprise authentication means such as a smart card SIM USIM or UICC and may operate in accordance with the GSM and or 3G Standards. In one embodiment the interface controller is a trusted secure UICC gateway that filters all communications to the UICC. The trusted component may be a separate in built security chip and a secure channel may be established to protect the data bus between the interface controller and the trusted component.

Also in the embodiment the main operating system of the terminal is provided in the normal execution environment. The operating system provides a gateway to the interface controller trusted secure UICC gateway. The operating system is operable to pass communications towards the interface controller trusted secure UICC gateway.

The gateway provided by the operating system to the interface controller trusted secure UICC gateway may be a virtual interface controller UICC gateway which passes a request to the interface controller trusted secure UICC gateway. The virtual interface controller UICC gateway in the embodiment is provided in the normal execution environment of the mobile terminal which is less secure than the trusted area secure execution environment. Any application requesting data from the interface controller trusted secure UICC gateway in the embodiment requests this information via the operating system and virtual interface controller UICC gateway. The requesting application may therefore not be aware of the environment in which the interface controller trusted secure UICC gateway resides.

The interface controller may be transparent to the communications so that the sender of the communications believes that they are received directly by the trusted component authentication means UICC.

The interface controller may control all access to the trusted component authentication means if present where access may originate from an application in any terminal execution environment

All execution environments may have a virtual interface or gateway through which communication attempts with the trusted component authentication means are passed to the actual interface controller in a secure environment in such a way that the calling application need not know the location of the interface controller or the trusted component authentication means being called.

The interface controller may impose access control functions on all communications to the trusted component authentication means and can restrict or filter communications to the trusted component authentication means

If certain functionality e.g. secure storage of the trusted component authentication means is available in the terminal or on a different component then the interface controller may interchange this functionality of the trusted component authentication means with the trusted functionality of the terminal alternate component depending on availability. This may be transparent to calling applications.

The interface controller in the trusted area secure execution environment may control all access to a trusted service where access may originate from an application in any terminal execution environment.

All other execution environments may have a virtual interface or gateway through which communication attempts with a trusted service are passed to the actual interface controller in the trusted area secure execution environment in such a way that the calling application need not know the location of the interface controller or the trusted service being called.

The interface controller may impose access control functions on communications to a trusted service and can restrict or filter communications to the service.

A trusted service may be provided by the UICC e.g. trusted functionality or secure authenticated storage .

The trusted service could be provided by a function in a secure execution environment on the terminal or another trusted component.

If the trusted service is implemented on a removable component then the interface controller may advantageously establish a secure channel to the trusted service or component hosting the trusted service. However trusted components can also be implemented as separate in built or embedded security chips and it may also be advantageous to establish a secure channel to protect the data bus between the interface controller and that in built class of trusted component.

The interface controller may interchange functionally equivalent trusted services i.e. may route communications to any equivalent trusted service if functionally equivalent trusted services exist and dependent on availability. This may be transparent to calling applications.

The present invention also provides a method of controlling access to a trusted component as defined in claim onwards.

The elements of a conventional mobile or cellular telecommunications network will first be briefly described with reference to .

A first telecommunications terminal is registered with a GSM GPRS or UMTS 3G mobile telecommunications network . The telecommunications terminal may be a handheld mobile telephone a personal digital assistant PDA or a laptop computer equipped with a datacard. The telecommunications terminal communicates wirelessly with mobile telecommunications network via the radio access network RAN of the mobile telecommunications network comprising in the case of a UMTS network a base station Node B and a radio network controller RNC . Communications between the telecommunications terminal and the mobile telecommunications network are routed from the radio access network via GPRS support nodes SGSN which may be connected by a fixed cable link to the mobile telecommunications network .

In a conventional manner a multiplicity of other telecommunications terminals are registered with the mobile telecommunications network . These telecommunications terminals include second and third telecommunications terminals . The second and third telecommunications terminals communicate with the mobile telecommunications network in a similar manner to the telecommunications terminal that is via an appropriate Node B RNC and SGSN .

The mobile telecommunications network includes a gateway GPRS support node GGSN which enables IP based communications with other networks such as the Internet or other IP network via an appropriate link .

Each of the telecommunications terminals and is provided with a respective subscriber identity module or UICC . The UICC is a trusted component trusted by the mobile telecommunications network and provides trusted services. During the manufacturing process of each UICC authentication information is stored on the UICC under the control of the mobile telecommunications network . The mobile telecommunications network itself stores details of each of the UICCs issued under its control. In operation of the mobile telecommunications network each of the telecommunications terminals is authenticated for example when the user activates the telecommunications terminal in the network with a view to making or receiving calls by the network sending a challenge to the telecommunications terminal incorporating a UICC in response to which the UICC calculates a reply dependent on the predetermined information held on the UICC typically an authentication algorithm and a unique key Ki and transmits it back to the mobile telecommunications network . The mobile telecommunications network includes an authentication processor which generates the challenge and which receives the reply from the telecommunications terminal .

Using pre stored information identifying the relevant UICC the authentication processor calculates the expected value of the reply from the telecommunications terminal . If the reply received matches the expected calculated reply the UICC and the associated telecommunications terminal are considered to be authenticated.

It should be understood that such an authentication process can be performed for any telecommunications terminal provided with a UICC under control of the mobile telecommunications network . In the embodiment each telecommunications terminal communicates wirelessly with the mobile telecommunications network via the network s radio access network although this is not essential. For example the telecommunications terminal may communicate with the network via the fixed telephone network PSTN via a UMA access point and or via the Internet.

The UICC used by each telecommunications terminal may be a UICC of the type defined in the GSM or UMTS standards specifications or may be a simulation of a UICC that is software or hardware that performs a function corresponding to that of the UICC.

As shown in the mobile terminal includes a main Execution Environment EE including a main operating system OS similar to that found on a conventional mobile terminal. The mobile terminal further includes a trusted area in the embodiment a secure or semi trusted Execution Environment in which a secure operating system is implemented.

An application wishing to access the UICC requests this access from the main OS or execution environment EE in which it is operating. The OS EE provides a UICC interface gateway for applications above it.

If the OS EE is highly trusted by the issuer of the UICC then this gateway may have direct access to the UICC otherwise this gateway is a virtual UICC gateway which passes the request to trusted secure UICC gateway that does have direct UICC access.

The trusted secure UICC gateway which has direct UICC access resides in the secure EE on the terminal and other virtual gateways reside in non secure or less secure areas e.g. . These virtual gateways are provided so that applications need not know in which environment the actual UICC gateway resides.

The virtual UICC access gateways may perform some initial filtering of UICC access requests e.g. the main OS may determine that the application does not have sufficient privileges to access the UICC but the ultimate access control is governed by the trusted UICC gateway . Since this gateway is securely implemented there is little chance that these controls may be bypassed.

If a secure channel to the UICC is required then the trusted UICC gateway negotiates a secure channel with the UICC and since all UICC access passes through the trusted UICC gateway all communications would be secured. Since the trusted UICC gateway is securely implemented the sensitive credentials and key material on the UICC necessary for secure channel setup and maintenance are well protected.

The trusted secure UICC gateway provides a single trusted control point in the terminal for access to the UICC functions. This control point filters all communications to the UICC and imposes any policy restrictions required.

The security policy maintained by the trusted secure UICC gateway takes into consideration the trustworthiness or trust level or an application requiring access e.g. whether it is a signed application or whether it is privileged in the ASF of the operating system and the UICC access required.

The security policy maintained by the trusted secure UICC gateway could therefore be seen as an ASF for UICC functions and the policy need not be restricted to only access granted or access denied but may also include the option to prompt the user at runtime for access control decisions as is the case in the OMTP ASF for terminal functions.

For example an untrusted application may not be granted access to highly sensitive UICC functions such as network authentication commands but may be granted access to moderately sensitive UICC functions subject to user prompting.

The trusted secure UICC gateway may also provide an interface to applications on the terminal even if the functional services are not provided by the UICC but are provided by other trusted services within the terminal such as secure storage facility an Mobile Trusted Module MTM or even a software UICC SIM and this would be hidden from the application.

For example an application may wish to securely store some data and sends the instruction SecurelyStore X to the trusted secure UICC gateway . The trusted secure UICC gateway may then store data object X with a secure storage facility on the terminal or may transmit X via a secure channel to the UICC for storage depending on what facilities are available.

A software trusted secure UICC gateway should be implemented in a trusted area of the terminal such as a secure execution environment where it is less vulnerable to attack. In addition a software trusted secure UICC gateway may be protected by mechanisms such as a secure boot process. This reduces the risk of bypassing or disabling the trusted secure UICC gateway . It also provides added security for secure channels which may be established with the UICC and the storage and manipulation of associated keys.

Having a single end point for the secure channel being specified in ETSI SCP offers a simpler terminal architecture. The trusted secure UICC gateway may then offer applications access to virtual secure channels which would use the general purpose secure channel to protect against external attacks but where different virtual or logical channels would be managed in a trusted way by the trusted secure UICC gateway to protect against internal attacks.

The access commands providing access to sensitive UICC functions and data are protected by residing in a trusted area of the terminal . Such an architecture provides better control over the access to the UICC and therefore better control over the UICC s assets.

