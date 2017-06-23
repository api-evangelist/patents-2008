---

title: Impersonal mobile communication for internet communities
abstract: The present invention relates to a method and server apparatus for providing an impersonal communication service in a telecommunication network, wherein a user is authenticated by a token-based application programming interface functionality and a temporary virtual number is allocated to an impersonal communication session of the user. The allocated temporary virtual number is then used for a telecommunication of the user.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08606305&OS=08606305&RS=08606305
owner: Nokia Siemens Networks Oy
number: 08606305
owner_city: Espoo
owner_country: FI
publication_date: 20081020
---
The present invention relates to a method and server apparatus for providing an impersonal communication service in a mobile network.

The popularity of Internet communities IC has given rise to a new type of personal identity. Members of ICs often generate themselves a pseudo identity that is relevant only within each respective IC and identified by a pseudonym. By contributing to the discussions and communication within the community they earn credibility and respect for their community identity it becomes an asset However disclosing one s true identity in the Internet has unfortunately proven hazardous because of the inherent nature of Internet communities i.e. worldwide visibility and usually unrestricted access for viewing the communications.

Before the ICs became such a widely adopted communication culture in the Internet there has been no need to provide enhanced impersonal communication facilities in the field of telecommunications and the only means for hiding the true identity has been total anonymity either by hiding the calling subscriber s address number or by hiding the subscriber data related to the calling subscriber s number.

To enable voice calls and SMS messaging between mobile users and Internet communication service clients or web clients mechanisms have been proposed which use temporary numbers in order to route a communication setup signalling through a server where the circuit switched call setup signalling is converted into voice over IP VoIP signalling and forwarded towards the Internet communication service domains. This however requires heavy integration with the Internet communication service s infrastructure.

It is therefore an object of the present invention to provide a complete and simple solution for impersonal telecommunication for Internet communities.

This object is achieved by a method of providing an impersonal communication service in a telecommunication network said method comprising 

Additionally the above object is achieved by a server apparatus for providing an impersonal communication service in a telecommunication network said server apparatus being adapted to authenticate a user by a token based application programming interface functionality to allocate a temporary virtual number to an impersonal communication session of said user and to use said allocated temporary virtual number for a telecommunication of said user.

Further the above object is achieved by a system comprising at least one server apparatus as defined above.

In addition the above object is achieved by a computer program product comprising code means for producing the steps of the above methods when run on a computer device.

Accordingly an impersonal communication service can be supported by the administrators of the Internet community simply as an additional web service for their web sites based on web technology implemented by an impersonal communication service API. This allows easy integration with minor modifications required in web sites of Internet communities. Moreover the fixed or mobile operator s service portfolio can be enhanced by a new and desirable service for fixed or mobile subscribers.

Hence impersonal communication solutions can be used to enable impersonal mobile or fixed communication in the scope of Internet communities. That is people can communicate with their mobile phones or fixed phones as members of a certain Internet community while only the Internet community s identity is known. This allows them to keep in touch and communicate via fixed or mobile phone when they are not online to have a feeling of a closer relationship. Additionally an Internet community member can be contacted anonymously and or private messages not visible to other users can be exchanged with an Internet community member instead of public chatting.

As the impersonal communication solutions can be based on well known web technology e.g. Web 2.0 technology and can be used as a common web service API very minor integration with the Internet community infrastructure is required for example basically only few modifications to the user interface of the IC service s web pages .

The temporary virtual number may be used to provide a mapping between subscriber identities of call parties of the mobile or fixed communication. In a specific but non limiting example the subscriber identities may be MSISDN numbers.

Furthermore the authenticating may comprise validating a subscriber identity and Internet community identity of the user.

Additionally a service web portal of a mobile or fixed network operator may be provided for subscribing to the impersonal communication service.

The authenticating may comprise transmitting a token to the user via the mobile or fixed telecommunication network and using the token to enable the impersonal communication service.

Further an activating means may be added to a web page of the user the activating means being adapted to enable impersonal communication with the user. More specifically the activating means may be a button or link.

The temporary virtual number may be displayed at a display of the user and the temporary virtual number may then be dialed to set up a call.

As an alternative or additional option the temporary virtual number my be received by a short message.

As another alternative or additional option the temporary virtual number may be indicated as an extension number at a display of the user and a service number and said extension number may be dialed to set up the call.

As a further alternative or additional option a code number may be allocated and indicating at a display of the user. A service number and the code number may be dialed and the temporary virtual number may be received in a short message.

It is further noted that an expiration time for the allocated temporary virtual number may be adjustable from one time usage to permanent usage.

The embodiments will now be described in connection with a mobile impersonal communication for Internet communities. According to the embodiments a complete solution for mobile impersonal communication can be provided which enables impersonal mobile communication for Internet Communities. The proposed complete solution according to the embodiments comprises an API functionality based on API keys and authentication of users request and allocation of temporary virtual numbers and mobile communication voice and or video call SMS MMS etc. with temporary virtual numbers.

More specifically the proposed embodiments serve to mobilize Internet community users. Thus an Internet community user can be reached on his her mobile phone for voice call SMS messaging etc. by anonymous or other Internet community users. It is however noted that the present invention is not intended to be restricted to mobile communication. It can be applied to any telecommunication network including fixed networks.

This solution enables impersonal mobile communication voice call SMS etc. by mapping temporary numbers with call parties MSISDN numbers. This mapping is achieved by an impersonal communication server provided in an operator network and accessible by means of an impersonal communication API. Call parties MSISDN numbers thus do not have to be disclosed. Call parties are identified by their Internet Community identities or optionally the caller can remain anonymous. The proposed impersonal communication service may thus be implemented as a common web based service API e.g. web 2.0 based service API . Hence very minor integration with Internet community service is required.

As possible pre conditions the Internet community X supports the impersonal communication service offered by the mobile operator. The Internet community X has got an API key from the mobile operator it has implemented the API and provides access to the impersonal communication service from the Internet community service web pages. The mobile operator offers the impersonal communication service to mobile subscribers from an impersonal communication service web portal. A user B is a member of the Internet community X and wants to activate the impersonal communication service for his her IC X identity.

The activation procedure may comprise the following steps. User B accesses the mobile operator s impersonal communication service web portal and subscribes to the service. He she selects the Internet community X among the set of Internet Communities supporting the impersonal communication service and provides his her IC X identity e.g. alice dogs.com . A mini token e.g. a short alpha numerical string is sent by SMS to user B s mobile phone. Then user B performs a login to the web page of the Internet community X in order to enable the impersonal communication service. User B clicks on an enable ImpComm button or link and he she is re directed to the mobile operator s web page where he she is requested to enter the mini token previously received by SMS. It is noted that this step is needed to verify the mapping and the ownership of the MSISDN and IC X identity provided by the user B.

The user B is now re directed back to the IC X web page. The IC X service requests via impersonal communication API method e.g. as shown in an authentication token to the impersonal communication service. This token can be included every time the IC X service makes a request for a new impersonal communication session for the user B. Basically the token creates a mapping between the API key assigned to the IC X service the user B s IC X identity and the user B s MSISDN number. At this phase the impersonal communication service activation is successfully completed.

Once the Impersonal communication service has been activated for the user B s IC X identity the IC X service may add the ImpComm button in the user B s account web page. Henceforth anyone e.g. a user A visiting user B s web page in the IC X web site could click on the ImpComm button in order to have an impersonal communication with user B.

The first and second use cases 1 and 2 assume that when the ImpComm button is clicked the user A is requested to enter his her MSISDN number. Thus the MSISDN number is known by the impersonal communication server. The difference between the first and second use cases 1 and 2 is that in the first use case 1 the allocated temporary number is shown on user A s PC display and user A manually dials to call. In the second use case 2 user A receives the temporary number by a flash SMS and merely has to press the green button on its mobile phone to call.

In the third use case 3 instead of a temporary number an extension number is allocated which univocally maps to user B s MSISDN number. The user A has to dial a impersonal communication service number shown on IC X web page and enter an extension number via DTMF on his her mobile phone. It is noted that the extension number is allocated by the impersonal communication server after user A clicked the ImpComm button in user B s IC X web page. The extension number is reserved for this impersonal communication session with user B and cannot be simultaneously re used for other Impersonal communication sessions .

In the fourth use case 4 a temporary number is allocated like in the first and second use cases 1 and 2 with the difference that user A is not requested to enter his her MSISDN number. Instead the impersonal communication server generates an extension code e.g. a short numerical string that univocally maps to user B s MSISDN. Such code can be shown on user A s PC display. User A may dial an impersonal communication service number and enter the extension code via DTMF . This allows the impersonal communication server to map the user A s MSISDN number to user B s MSISDN number and allocate a temporary number like in the first and second use cases 1 and 2 . The temporary number is then sent to user A s mobile phone in form of a Flash SMS.

When a caller clicks the ImpComm button or link the procedure checks whether the caller is an IC X user. If not the caller ID is set to an anonymous state and the caller is requested to enter his her MSISDN and a caller number parameter is set to the MSISDN number. If the caller is an IC X user his her caller ID is set to indicate this and it is checked whether the caller is a user of the impersonal communication service. If not the caller is requested to enter his her MSISDN and the caller number parameter is set to the MSISDN number. If the caller is already a user of the impersonal communication service the caller number parameter is set to a predefined value or state e.g. 1 to indicate that the MSISDN can be fetched from a database of the impersonal communication server. Finally a service API method is started which gets the number of the caller.

It is noted that the caller s e.g. user A s MSISDN is thus provided to the impersonal communication server so that it can allocate a temporary number that is univocally mapped to user A s and user B s MSISDN numbers. The combination of user A s MSISDN number and this temporary number univocally identifies the impersonal communication session that is going to be setup. The same temporary number can be simultaneously re used for other impersonal communication sessions initiated by other users.

When a caller clicks the ImpComm button or link the procedure checks whether the caller is an IC X user. If not the caller ID is set to an anonymous state and a caller number parameter is set to a first predefined value or state e.g. 0 to indicate that the MSISDN cannot be fetched from the database of the impersonal communication server. If the caller is an IC X user his her caller ID is set to indicate this and it is checked whether the caller is a user of the impersonal communication service. If not the caller number parameter is set to the above first predefined number or state. If the caller is already a user of the impersonal communication service the caller number parameter is set to a second predefined value or state e.g. 1 to indicate that the MSISDN can be fetched from the database of the impersonal communication server. Finally a service API method is started which gets the number of the caller.

All the above first to fourth use cases 1 to 4 provide different user experience using the proposed impersonal communication service.

Hence according to the above embodiments any Internet community that wants to enrich its own web services by supporting an impersonal communication service may register its own service application on a mobile or fixed network operator s web portal in order to get an API key. Such an API key may be a parameter required in API based calls. The Internet community can then implement the impersonal communication API by a few user interface UI modifications in the Internet community s web pages with few additional buttons links pop up windows or the like in order to facilitate access to the implemented impersonal communication service.

In order to activate an impersonal communication service a user of the Internet community can subscribe to the network operator s impersonal communication service and may provide its MSISDN number and his her Internet community identity ID e.g. alice dogs.com assuming that the respective Internet community e.g. www.dogs.com supports the impersonal communication service by implementing the API of the impersonal communication service.

A user may even activate an impersonal communication service with more than one Internet community which support the impersonal communication service where he she belongs too.

When an impersonal communication service has been activated for a certain user within a certain Internet community web site anyone visiting the IC user s web page could request for example by a click on an allocated button e.g. Impersonal communication or the like or by activating an allocated link to establish a temporary impersonal communication session voice call short message service SMS messaging etc. with that IC user. The click on the allocated button or link or the like in the IC user s web page can be used to trigger the Internet community service to call the impersonal communication API method that forwards the request to an impersonal communication server which may be located in the operator s network.

Temporary numbers are used to route the call setup or SMS messaging through the impersonal communication server responsible for mapping the temporary numbers to call parties MSISDN numbers which are not disclosed . Basically a caller calls or sends an SMS to a temporary number allocated by the impersonal communication server. A call request or SMS reaches the impersonal communication server which forwards it to the callee s MSISDN number replacing the caller s MSISDN with another temporary number which is then shown on callee s phone display . The impersonal communication server can be adapted to allocate a temporary number later provided to the caller that shall be used instead of the real MSISDN that cannot be disclosed in order to call or send an SMS to the IC user s terminal device or user equipment e.g. mobile phone . Moreover the impersonal communication server may be adapted to resolve a mapping between temporary numbers and call parties MSISDN numbers and to route the mobile communication setup signaling between call parties mobile phones.

In case a caller is a member of the same Internet community and logged in to the IC service when a request for impersonal communication is made the impersonal communication server obtains information about the caller s IC identity e.g. jeff dogs.com which can then be provided to the callee e.g. by SMS .

To summarize a method and server apparatus for providing an impersonal communication service in a telecommunication network have been described wherein a user is authenticated by a token based application programming interface functionality and a temporary virtual number is allocated to an impersonal communication session of the user. The allocated temporary virtual number is then used for a telecommunication of the user.

It is to be noted that the present invention is not restricted to the specific embodiment described above but can be implemented in any network environment and impersonal communication functionality. The embodiments may thus vary within the scope of the attached claims.

