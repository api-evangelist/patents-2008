---

title: Communication system, application server and communication method for server cooperation
abstract: A communication entrepreneur has an application server  having message conversion function. The application server  performs service function distribution processing with reference to trigger rule  and message rule . The communication entrepreneur can provide various service functions without notifying individual server addresses to a service entrepreneur.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08656001&OS=08656001&RS=08656001
owner: Hitachi, Ltd.
number: 08656001
owner_city: Tokyo
owner_country: JP
publication_date: 20081219
---
This application claims priority from Japanese Patent Application No. 2008 055700 filed on Mar. 6 2008 the content of which is hereby incorporated by reference into this application.

The technique disclosed in this application relates to a communication device connected to a network a communication system and a communication control method. Particularly it relates to server cooperation at the time that a plurality of communication servers perform mutual communication and message conversion processing. Especially it relates to a communication system to which session control using SIP Session Initiation Protocol is applied and a message conversion method in communication systems in which communication systems for providing Web application are connected mutually.

The 3rd generation mobile communication system is being standardized so as to aim at providing various multimedia services such as voice data and animation at high speed and with high quality. The 3GPP 3rd Generation Partnership Project advances standardization of All IP Base Mobile Communication Network that provides multimedia services such as voice and picture utilizing Internet Protocol IP technique on a packet switching network.

The session control system of the All IP Base Mobile Communication Network is named IMS IP Multimedia Subsystem . The IMS is also adopted in session control technique of NGN Next Generation Network .

The SIP Session Initiation Protocol is utilized as the session control protocol of the IMS for example refer to IETF RFC3261 2002.6 . The SIP is the protocol for controlling session of IP multimedia communication specified by IETF. The SIP controls establishment maintenance and disconnection of session among communication devices.

As the representative service using SIP there is IP telephony service. The IP telephony service is the service for transmitting and receiving voice information through IP network. In the IP telephony service using SIP virtual speech path or channel session is established between communication devices before communication is started. Voice data formed into IP packets is transferred through the established communication path.

Media information such as attributes of voice data is decided upon establishment of session. The communication device notifies the media information using SDP Session Description Protocol contained in SIP message. In the SDP various information concerning session for example IP address port number kind of media and the like can be described. As an example of application service using the SIP protocol there is the third party call control refer to IETF RFC3725 2004.6 for example .

Moreover in order to make it possible to utilize the communication service provided by a communication entrepreneur from Web service investigation of API Application Programming Interface is advanced.

There is the Parlay group as an industrial organization stipulating the API. The Parlay group is deciding on a plan for API named Parlay X . The Parlay group cooperates with ETSI European telecommunication standards institute and 3rd generation mobile telecommunication standardization organization 3GPP . The specifications of the Parlay X are issued from the 3 organizations jointly.

The Parlay X is API of Web service that does not depend on network and vendor and is not limited to language provided therein for the purpose of use in Web service environment. The Parlay X defines open interface abstracted for Web developers but its mounting or implementing method is not prescribed.

In the Parlay X a set of API is stipulated for each service. As service provided using the Parlay X API there is for example 3PCC 3rd Party Call Control starting 2 party conversation service from Web application 4th Draft ES 202 504 2 Parlay X 3.0 2007.8 .

The API for 3PCC stipulates request messages start end call information inquiry to communication system from Web application server and response messages thereto. As an example of application using SIP protocol there is third party call control and a sequence example of SIP message is shown. However mounting method of the Parlay X API and conversion measures of the SIP message is not stipulated.

Accordingly the communication system in which the service entrepreneur utilizes service function of the communication entrepreneur via open API represented by the Parlay X has a problem that the communication entrepreneur is required to specify the server corresponding to the required service function.

It is an object of the present invention to provide measures for making it possible to utilize various service functions without making the communication entrepreneur notify address of individual application server to the service entrepreneur.

According to a representative invention disclosed in this application a communication system includes an application server having conversion function of open API and SIP. The application server performs service function distribution processing with reference to trigger rule and message rule. By providing this function the communication entrepreneur can provide various service functions without notifying address of individual application server to the service entrepreneur.

According to another representative invention disclosed in this application the application server further includes additional information processing function such as customization processing for example additional processing function of parameter in accordance with a request of the service entrepreneur and high speed engine for example high speed engine of transaction processing such as accounting information in accordance with contents of various processing. By providing this function the application server can realize customization and high speed operation of specified processing.

According to an embodiment of the present invention the communication entrepreneur can provide various service functions without notifying address of individual server to the service entrepreneur. Further the communication entrepreneur can perform customization of processing and high speed operation of specified processing. Thus various services can be provided rapidly in accordance with user s need.

Other objects features and advantages of the present invention will be apparent from the following description of embodiments of the present invention taken in conjunction with the accompanying drawings.

A first embodiment of the present invention is now described with reference to the accompanying drawings.

As a representative example a communication method at the time that the third party call control 3PCC service is utilized is described in detail.

The communication network of the embodiment includes an IP network N and access networks N N Nand N .

In fixed or wired terminals are shown as an example of terminals hereinafter referred to as UE User Equipment . When the terminals are distinguished individually in description the reference numeral thereof is annexed with subscripts a b c and d and described as terminal and terminal for example. Other constituent elements are also described according to the same rule.

The IP network N is connected to the access networks N through access gateway devices AGW . The IP network N may be connected to the access networks N through router or another communication device instead of the access gateway devices . The access gateway devices provide function of transferring IP packets transmitted and received between the terminal and the IP network N.

The IP network N includes SIP server Web server application server and 3PCC server at least. The IP network N may further include presence server . When the IP network N includes the presence server the IP network N can provide presence service.

The Web server has user interface function for starting 3PCC service and presence service function necessary for starting 3PCC service and mutual connection function with application server .

The application server has service function distribution function necessary for utilizing various service functions provided in the communication network and function for controlling customization function.

In the SIP server the Web server the application server the 3PCC server and the presence server are shown singly. However when the present invention is implemented any number of these constituent elements may be provided.

The application server includes interface parts IF having lines connected thereto a CPU a memory and a database DB . These constituent elements are connected through a bus .

The memory stores therein a program for executing protocol processing and a program for receiving message from Web server and performing mutual connection function between the 3PCC server and the application server and between the presence server and the application server . The memory may store therein still another program.

The CPU is a processor for executing programs stored in the memory . In the following description the processing executed by the application server is actually executed by execution of any program by the CPU .

The program for executing protocol processing contains program having function of transmitting or receiving signal between the Web server and the application server and program having function of transmitting or receiving signal between the 3PCC server and the application server and between the presence server and the application server . For example when the Web server and the application server make communication by SOAP over HTTP the communication is made using SOAP control part and HTTP protocol control part. Furthermore when the application server and the 3PCC server make communication by HTTP the communication is made using HTTP protocol control part.

In HTTP and SOAP are shown as communication protocol. However when the present invention is implemented protocol except HTTP and SOAP may be utilized.

The program for performing mutual connection function includes session information table trigger rule message rule parameter rule additional information processing engine service judgment routine and conversion engine . The database may store therein session information table trigger rule message rule and parameter rule .

Provision of trigger rule message rule parameter rule and service judgment routine in the application server can make the application server control service function in accordance with request received from the Web server . The service function is realized by the presence server and the 3PCC server . The service function is sometimes named enabler.

Moreover provision of additional information processing engine in the application server can control customization function and function requiring high speed operation.

The session information table stores therein at least Web server address enabler address and trigger rule in a corresponding manner to Parlay X call session identifier . Moreover the session information table may store therein session state . By providing the trigger rule in the session information table the application server can detect the service function to be started rapidly. By providing the session state in the session information table the application server can hold the session state.

The trigger rule stores therein at least trigger rule and enabler IP address in a corresponding manner to namespace of Parlay X API. When the application server receives a request from the Web server the application server extracts the namespace from the received message and specifies the trigger rule corresponding to the namespace. Furthermore the application server extracts the enable IP address corresponding to the entry and specifies address information of the server having the service function corresponding to the request message.

The trigger rule may store therein information as to whether additional information processing is present or not.

By providing the information as to whether additional information processing is present or not in the trigger rule the application server can specify customization processing and high speed processing for each trigger rule.

The message rule stores therein at least the SIP message corresponding to the Parlay X message . The message rule may store therein flag indicating whether parameter conversion processing is present or not.

By including the flag indicating whether parameter conversion processing is present or not in the message rule the application server can judge whether parameter contained in message is converted or not.

When the application server judges that parameter conversion is required as a result of reference to the message rule the application server refers to the parameter rule using Parlay X parameter contained in message as a search key. When relevant entry exists in the parameter rule the application server performs conversion of Parlay X parameter and SIP parameter SIP header .

The 3PCC server includes interface parts IF having lines connected thereto a CPU a memory and a database DB . These constituent elements are connected through a bus .

The memory stores therein program SIP protocol control and HTTP protocol control for executing protocol processing and program program for performing SIP User Agent processing and program for performing 3PCC control processing for executing 3PCC server processing. The memory may store therein still another program.

The CPU is a processor for executing programs stored in the memory . In the following description the processing executed by the 3PCC server is actually executed by execution of any program by the CPU .

The program for executing protocol processing contains program SIP protocol control having function for transmitting or receiving signal between the SIP server and the 3PCC server and program HTTP protocol control having function for transmitting or receiving signal between the application server and the 3PCC server . In HTTP and SIP are shown as communication protocol. However when the present invention is implemented communication protocol except HTTP may be utilized so that the 3PCC server and the application server communicate with each other.

The program for executing 3PCC server processing contains program for performing SIP User Agent processing and program for performing 3PCC control processing. Correspondence information of session identifier on the side of Parlay X and identifier of 3PCC session may be provided in addition to the program for performing 3PCC control processing. Moreover the memory of the 3PCC server may store therein information necessary for 3PCC server processing. The information necessary for 3PCC server processing may be stored in DB .

The presence server includes interface parts IF having lines connected thereto a CPU a memory and a database DB . These constituent elements are connected through a bus .

The memory stores therein program SIP protocol control and HTTP protocol control for executing protocol processing and program program for performing SIP User Agent processing and program for performing presence control processing for executing presence server processing. The memory may store therein still another program. Furthermore the memory may store therein information necessary for presence control processing. The information necessary for presence control processing may be stored in DB .

The CPU is a processor for executing programs stored in the memory . In the following description the processing executed by the presence server is actually executed by execution of any program by the CPU .

The program for executing protocol processing contains program SIP protocol control having function for transmitting or receiving signal between the SIP server and the presence server and program HTTP protocol control having function for transmitting or receiving signal between the application server and the presence server . In HTTP and SIP are shown as communication protocol. However when the present invention is implemented communication protocol except HTTP may be utilized so that the presence server and the application server communicate with each other.

The program for executing presence server processing contains program for performing SIP User Agent processing and program for performing presence control processing. Furthermore correspondence information of session identifier on the side of Parlay X and identifier of presence session may be provided in addition to the program for performing presence control processing.

Referring now to and sequential operation for starting 3PCC service by terminal residing in the access network Nshown in is described.

The sequential operation in case where the user using the terminal in the first embodiment accesses to the Web server S and requests to start 3PCC service between the terminals and is described.

The Web server receives a request for starting 3PCC service from the terminal . The Web server transmits a message makeCallSessionRequest for making a request for establishment of session between the terminals and to the application server S . The message for making the request for establishment of session contains identifiers of terminals and at least.

When the application server receives the session establishment request the application server transmits a response message to the Web server S .

The response message makeCallSessionResponse contains a call session identifier in order to identify session between the Web server and the application server . The application server produces the call session identifier.

The application server searches the session information table using the call session identifier as a search key. When there is no entry the application server selects a new entry and registers address of Web server in Web server address of this entry.

Then the application server starts the service judgment routine . When the application server receives the session establishment request message S the application server searches the trigger rule using namespace contained in the received message as a search key . When there is relevant entry for example entry the application server reads out trigger rule and enabler IP address of the relevant entry and sets them in the enabler IP address and trigger rule of the relevant entry of the session information table . Furthermore when present is set as the information as to whether additional information processing is present or not in the relevant entry of the trigger rule the application server performs additional processing according to namespace . Additional processing contains addition and deletion of expansion parameter and collection of communication log by way of example. By performing additional processing by the application server processing peculiar to service and processing peculiar to the communication entrepreneur can be realized. When not present is set as the information as to whether additional information processing is present or not in the relevant entry of the trigger rule the additional processing is not performed in this step .

Returning now to description of the service control routine is continued. The application server refers to the message rule decided in step . The message rule is provided for each trigger rule and is identified by a value in entry of the trigger table . The message rule stores therein at least correspondence information of the SIP message corresponding to Parlay X message and the information as to whether parameter conversion is present or not. The application server performs message conversion processing in accordance with the message rule . Furthermore when present is set as the information as to whether parameter conversion is present or not the application server searches the parameter rule using parameter contained in the received message as a search key . When there are a plurality of parameters all parameters are confirmed as to whether relevant entry is present or not. When the relevant entry exists the parameter contained in the message is converted in accordance with the entry .

When conversion of message and parameter is completed the application server refers to the session information table and reads out enabler IP address e.g. 3pcc ip from the entry produced upon reception in step S. Here the application server may set the state of service being started in the session state of the entry .

Then the application server transmits message and parameter converted message SIP application server starting request to the enabler IP address which is an address of the 3PCC server S . The SIP application server starting request contains Parlay X call session identifier.

When the application server receives response message from the enabler 3PCC server S this routine is ended .

In steps and when there is no entry error processing is performed and this routine is ended . In step when the application server cannot receive response within a fixed time the error processing is performed and this routine is ended .

That is in the application server which has received the request in S refers to the message rule and converts Parlay X message makeCallSessionRequest into SIP message INVITE . Furthermore the application server refers to the parameter rule and converts parameter contained in the makeCallSessionRequest into parameter contained in SIP INVITE for example converts parameter callParticipant for setting identifiers of terminals and into Request URI . The application server utilizes the conversion engine upon conversion of message and parameter. The application server transmits SIP application server starting request containing converted message to the 3PCC server .

Returning now to description of the sequential operation is continued. When the 3PCC server receives the SIP application server starting request S the 3PCC server starts 3PCC control and performs 3PCC control of SIP base for example. The 3PCC server produces 3PCC identifier for identifying communication between terminals and . The 3PCC server holds the 3PCC identifier while session is established.

3PCC service is provided by 3PCC control SIP User Agent control and SIP protocol control. 3PCC server requests terminal to establish session S S . For example INVITE is utilized as SIP message for requesting to establish session. When terminal receives the session establishment request the terminal responds to the request with OK. The 3PCC server transmits response acknowledge ACK to the terminal

Next the 3PCC server requests terminal to establish session S S . Further the 3PCC server requests the terminal to update media information between the terminals and S S . According to the above processing communication between terminals and can be made S .

The 3PCC server transmits acknowledge signal ACK to session establishment response in step S and then notifies the session to the application server with session establishment notification signal S . The session establishment notification S contains Parlay X call session identifier received in step S. The application server searches for Parlay X call session identifier contained in the notification of step S and changes session state in relevant entry of the session information table to session being established .

When the application server receives the signal the application server transmits the session establishment notification response S to the reception acknowledge signal of S to the 3PCC server .

The Web server transmits a state inquiry request getCallSessionInformationRequest to the application server in order to confirm the state of the 3PCC service S . The transmission timing of the request depends on a set value on the side of Web server.

The application server searches the session information table using call session identifier contained in the request as a search key. The application server reads out the session state from the relevant entry and transmits response message getCallSessionInformationResponse containing the session state to the Web server S .

Here in order to confirm that communication between terminals and is made normally while terminals and communicate with each other the 3PCC server may transmit message to terminals periodically. SIP INVITE message for example is utilized as the message transmitted periodically. shows sequential operation in case where the 3PCC server transmits the SIP INVITE message to terminals periodically. The 3PCC server transmits INVITE message to terminal via SIP server S S . When the terminal receives the message the terminal transmits response message S S . The 3PCC server transmits acknowledge message S S to the response message. This sequential operation is repeatedly performed between 3PCC server and terminal periodically for example timer T S S . Thus it is confirmed that the communication is made normally. Timer value T is decided using SIP message upon session establishment.

The same messages are transmitted and received between the 3PCC server and the terminal S S S S . Timer value T is decided using SIP message upon message establishment.

In the embodiment SIP is used as communication protocol for establishment of session. When the present invention is implemented communication protocol except SIP may be utilized to make communication between the 3PCC server and the terminals .

Referring now to processing at the time of end of communication is described. The case where the terminal transmits a communication end request to the Web server is described. The communication end request is started or issued by selecting a communication end button on Web display screen provided by the Web server by the user utilizing the terminal for example S .

The Web server transmits 3PCC communication end request endCallSessionInformationRequest to the application server S . The message contains Parlay X call session identifier.

Here the application server searches the session information table using Parlay X call session identifier as a search key. The enabler IP address and the trigger rule are read out from the entry and the session state is updated to being disconnected .

Next when the application server receives the message the application server starts the service judgment routine . The application server refers to the trigger rule using namespace contained in the message as a search key. When relevant entry exists the application server refers to the information as to whether additional information processing is present or not of the entry. When present is set in the entry the application server performs additional processing in accordance with namespace.

Moreover the application server refers to the message rule table corresponding to trigger rule. The application server searches the trigger rule table using Parlay X message received in step S as a search key. Here relevant SIP message name BYE and information as to whether parameter conversion is present or not not present are read out from the relevant entry . Next the application server utilizes the conversion engine to convert message and parameter. Then the application server transmits an end request message after conversion of message to a destination 3pcc ip set in the enabler IP address S .

When the 3PCC server receives the request the 3PCC server transmits response message end request response to the application server . Further the 3PCC server transmits session end message BYE of SIP to terminals and S to S .

When the 3PCC server ends session between terminals and 3PCC server the 3PCC server notifies session disconnection to the application server session disconnection notification message S . The message contains Parlay X call session identifier. When the application server receives the message the application server searches the session information table using Parlay X call session identifier as a search key. The application server searches for the entry and changes the session state to disconnection end . Next the application server transmits response message S to the message S to the 3PCC server .

Then the application server holds the relevant entry of session information entry for a fixed period after the fixed period the entry is deleted .

When the application server receives information inquiry getCallSessionInformationRequest S from the Web server while the application server holds the entry the application server searches the session information table using call session identifier contained in the message as a search key. The application server reads out value of session information of the entry and transmits response message getCallSessionInformationResponse S containing session state disconnection end to the Web server .

When the application server receives getCallSessionInformationRequest S after the lapse of fixed time after the entry of session information table is deleted there is no entry in session information table. In this case the application server transmits response message getCallSessionInformationResponse S containing session state no relevant item to the Web server . The transmission timing of the request S depends on set value on the side of Web server .

In the embodiment the 3PCC server is utilized as enabler by way of example. When the present invention is implemented SIP application server except the 3PCC server may be utilized as enabler. There is the presence server for example as enabler except the 3PCC server.

In the first embodiment the application server the 3PCC server and the presence server may be realized in an apparatus having the same housing like blade server.

According to the first embodiment of the present invention the application server includes trigger rule and parallel rule and conversion of message and parameter can be performed between different messages for example Parlay X message and SIP message . Moreover the trigger rule table is used to make judgment as to whether additional information processing is present or not so that the application server can perform additional information processing such as expansion of original parameter and high speed processing of message. Consequently the communication entrepreneur and the service provider can provide services flexibly.

In the first embodiment the application server provides the message rule and the parameter rule. In contrast in the second embodiment the presence server and the 3PCC server include the message rule and the parameter rule. By providing the message rule and the parameter rule in the presence server and the 3PCC server the application server can concentrate on service function distribution processing and high speed processing of additional function.

The communication network of the second embodiment of the present invention is the same as that of the first embodiment and accordingly description thereof is omitted refer to . Hereinafter only different points of the second embodiment of the present invention from the first embodiment are described.

In the second embodiment the memory does not include message rule parameter rule and conversion engine. These functions are provided in the presence server and the 3PCC server . The application server includes a service judgment routine instead of the service judgment routine .

In the embodiment the application server can concentrate on service function distribution processing and the high speed processing of additional function.

By providing message rule parameter rule and conversion engine in the 3PCC server the application server can concentrate on service function distribution processing and high speed processing of additional function. In the embodiment the system operator can add function peculiar to 3PCC service such as parameter expansion for 3PCC service without influencing the application server .

By providing the message rule the parameter rule and the conversion engine in the presence server the application server can concentrate on service function distribution processing and high speed processing of additional function. In the embodiment the system operator can add function peculiar to presence service such as parameter expansion for presence service without influencing the application server .

In the second embodiment sequential operation for starting 3PCC service by terminal residing in the access network Nshown in is described. Since the sequential diagram is the same as that of the first embodiment only different part of the sequential operation of the second embodiment from that of the first embodiment is described with reference to and .

Then the application server starts the service judgment routine . When the application server receives session establishment request message S the application server searches trigger rule using namespace contained in received message as a search key . When there is relevant entry for example entry trigger rule and enabler IP address of the entry are read out and set to enabler IP address and trigger rule of the entry of the session information table . Furthermore when information as to whether additional information processing is present or not of the relevant entry of the trigger rule is set to present the application server performs additional processing in accordance with namespace . Addition processing contains addition and deletion of expansion parameter and collection of communication log by way of example. By performing additional processing by the application server function peculiar to service and function peculiar to the communication entrepreneur can be realized.

When the information as to whether additional information processing is present or not of the relevant entry of the trigger rule is set to not present the additional processing in this step is not performed . In step when there is no relevant entry error processing is performed and this routine is ended.

Then the application server reads out enabler IP address for example 3pcc ip from entry of the session information table produced upon reception in step S. Here the application server may set the state service being started in the session state of the entry .

The application server transmits SIP application server starting request S to the enabler IP address 3PCC server . The SIP application server starting request contains Parlay X call session identifier.

When the 3PCC server receives the SIP application server starting request S the 3PCC server starts the message parameter conversion routine .

The 3PCC server refers to the message rule in the memory . The message rule stores therein correspondence information of Parlay X message SIP message and information as to whether parameter conversion is present or not at least. The 3PCC server performs conversion processing of message in accordance with the message rule . When message is converted the 3PCC server may utilize the conversion engine .

When present is set in the information as to whether parameter conversion is present or not the 3PCC server searches the parameter rule using parameter contained in the received message as a search key . When there are plural parameters whether relevant entry exists or not is confirmed for all parameters. When relevant entry exists the parameter contained in the message is converted in accordance with parameter conversion table .

When conversion of message and parameter is ended the 3PCC server ends this routine . In step when there is not relevant message rule error processing is performed and this routine is ended .

Then the 3PCC server starts 3PCC control to perform 3PCC control of SIP base for example. The following processing from steps S to S is the same as in the first embodiment.

Referring now to only different part of the processing upon end of communication from the first embodiment is described.

When the application server receives endCallSessionInformationRequest S the application server starts the service judgment routine . The application server refers to the trigger rule using namespace contained in the message as a search key. When there is relevant entry the application server refers to the information as to whether additional information processing is present or not of the entry. When present is set in the entry the application server performs additional information processing in accordance with the namespace. Then the application server reads out enabler IP address from the relevant entry of the session information table and transmits end request message to destination 3pcc ip set thereto S .

When the 3PCC server receives the end request message S the 3PCC server starts message parameter conversion routine .

First the 3PCC server refers to the message rule table using Parlay X message received in step S as a search key. The 3PCC server reads out SIP message BYE and information as to whether parameter conversion is present or not not present from relevant entry . When it is not necessary to change parameter this routine is ended. Next the 3PCC server utilizes the conversion engine to convert message. Then the 3PCC server transmits session end message BYE of SIP to terminals and S to S . The following processing is the same as that of the first embodiment. shows an example of configuration of message rule in 3PCC server of the embodiment and shows an example of configuration of parameter rule in 3PCC server .

In the embodiment the 3PCC server is utilized as the enabler by way of example. When the present invention is implemented SIP application server except 3PCC server may be utilized as enabler. There is the presence server for example as the enabler except 3PCC server. In this case tables referred to at the time that the presence server starts message parameter conversion routine are message rule and parameter rule .

According to the second embodiment of the present invention the application server includes the trigger rule and the presence server and the 3PCC server provide the message rule and the parameter rule. Thus the application server can concentrate on service function distribution processing and high speed processing of additional function. Processing for example addition of special parameter peculiar to SIP application server can be realized only by 3PCC server or presence server . Thus the communication entrepreneur and the service provider can perform addition and expansion of service. That is service can be provided rapidly and customized.

Further in the second embodiment the application server the 3PCC server and the presence server may be realized in the apparatus having the same housing like blade server.

The foregoing description has been made to the embodiments although the present invention is not limited thereto and it is apparent to those skilled in the art that various changes and modifications can be made without departing from the sprit and the scope of claims of the invention.

According to the present invention the communication entrepreneur and the service provider can provide service flexibly. Concretely the application server includes the trigger rule and the parameter rule and conversion of message and parameter can be made between different messages for example Parlay X message and SIP message . Furthermore the trigger table is used to judge whether additional information processing is present or not so that the application server can perform additional information processing such as expansion of original parameter and high speed processing of message.

