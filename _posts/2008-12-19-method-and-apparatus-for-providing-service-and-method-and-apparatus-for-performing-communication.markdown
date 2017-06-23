---

title: Method and apparatus for providing service and method and apparatus for performing communication
abstract: A method and apparatus for providing an interactive service and a method and apparatus for performing communication are provided. An Open Cable Application Platform (OCAP) application may be directly executed in at least one broadcasting receiving apparatus by determining whether an application for providing the interactive service is independently executable using middleware installed in the broadcasting receiving apparatus and selectively requesting a set-top box to provide data needed for executing the application based on the determination result.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08387101&OS=08387101&RS=08387101
owner: Samsung Electronics Co., Ltd.
number: 08387101
owner_city: Suwon-si
owner_country: KR
publication_date: 20081219
---
This application claims priority from Korean Patent Application No. 10 2008 0007079 filed on Jan. 23 2008 in the Korean Intellectual Property Office the disclosure of which is incorporated herein in its entirety by reference.

Methods and apparatuses consistent with the present invention relate to providing a service and performing communication and more particularly to a method and apparatus for providing an interactive service in a broadcasting receiving apparatus and a method and apparatus for performing communication.

Since a cable broadcasting service provides an interactive function high transmission speed and large capacity transmission it is possible to provide a high quality interactive service. In addition cable broadcasting services are expected to become the most suitable media for broadcasting communication fusion services.

In order to enable a digital cable broadcasting service to be interactive a set top box STB that is a control box for receiving a broadcasting service and embodying various additional functions is necessary.

Since an STB is used to receive a digital broadcasting service with high image quality and high sound quality and provide an interactive service the STB is an important element of the broadcasting service.

The main function of an STB is to receive broadcasting data from a broadcasting data provider. Recently STBs have been developed to have various additional functions such as a communication function a personal video recorder PVR function an electronic program guide EPG function and the like.

The OpenCable standard employed as a domestic digital broadcasting standard is largely divided into hardware and software parts.

First the hardware part is constructed with an STB and a point of deployment POP device obtained by separating a security function and a conditional receiving function from the STB. The software part is the OpenCable Application Platform OCAP standard that is middleware.

The OCAP standard provides a basis for generating an application for providing an interactive service in digital cable broadcasting services. In the OCAP it is possible to support a developed interactive service by providing a web based service for the digital cable broadcasting service. In a method of providing an interactive service using the OpenCable standard application software and contents are shared by using a common middleware platform that is the OCAP.

On the other hand as technology has developed a family home may include a plurality of televisions TVs . Conventionally only a TV which is connected to an STB can receive a digital broadcasting service. Additional STBs have to be provided so that each of the plurality of TVs receive the digital broadcasting service. In order to solve this problem the High Definition Audio Video Network Alliance HANA design guideline has been suggested so as to integrally control devices and share high definition HD contents by connecting a DTV to peripherals through an IEEE 1394 cable. In the HANA design guideline a web browser and a decoder are installed in the DTV and a web server and a control page are installed in the peripherals.

In the aforementioned HANA design guideline digital broadcasting signals and HD contents stored in the peripherals are decoded by the DTV and the peripherals are integrally controlled in a graphical user interface GUI form by using the web browser of the DTV.

In the HANA design guideline it is possible to control all the devices connected to an IEEE 1394 network by using a universal remote control.

HANA compliant products include an HANA DTV a TV node an A V HDD an HANA expandable home theater XHT STB cable network interface unit NIU and the like. The NIU performs the function of the STB. The NIU executes an EPG function a pay per view PPV function a video on demand VOD function and a shopping program function in response to a request of a user or processes transmission and reception of data. The NIU provides the execution result to the DTV in a hypertext markup language HTML format.

However it is impossible for the DTV connected to the HANA solution to provide the interactive service by directly executing an application. In a case where the OCAP middleware is installed in an STB that is connected to an HANA device through the IEEE 1394 standard by using the OpenCable technique a predetermined application that operates on MHP middleware or OCAP middleware is not provided in the HTML format.

Finally the NIU directly executes the application and transmits the execution result to the DTV in the HTML format. Accordingly the DTV may provide the interactive service. In this case a command of the user has to be firstly transmitted to the NIU so that a service is provided to the user after the user requests the service to be provided. Since the DTV and the NIU are connected through a network it takes time to transmit data. Specifically since the NIU has to execute the application according to the command of the user and transmit the execution result to the DTV there is a time difference between a time when the user requests the service to be provided and a time when the service is actually provided to the user.

In order to solve this problem the OCAP middleware may be extended or modified and re installed in the DTV. However if the OCAP middleware is modified or extended a license used for a case where the OCAP is applied is too expensive or it is too expensive to customize the OCAP middleware.

The present invention provides a method of providing a service and a method for performing communication so as to efficiently provide an interactive service by using a broadcasting receiving apparatus and a broadcasting receiving apparatus and a set top box for efficiently providing an interactive service.

According to an aspect of the present invention there is provided a method of providing an interactive service by using a broadcasting receiving apparatus for receiving a broadcasting service through a set top box the method comprising determining whether an application for providing the interactive service is independently executable by using installed middleware and selectively requesting the STB to provide data needed for executing the application based on the determination result.

In the determining whether the application is independently executable it may be determined whether the application calls a first application programming interface API that is to be processed by the STB and wherein in the selectively requesting the STB to provide the data when the application calls the first API the STB is requested to process the first API.

The method of providing an interactive service may further comprise receiving the result obtained by processing the first API from the STB and executing the application by using the processed result.

The middleware may be defined in the OCAP standard or the MHP standard and wherein the application is an OCAP middleware based application or an MHP middleware based application.

The STB may be connected to at least one device including the broadcasting receiving apparatus through a home network and wherein the broadcasting receiving apparatus is a digital TV set.

According to another aspect of the present invention there is provided a communication method for providing an interactive service to a broadcasting receiving apparatus for receiving a broadcasting service through a set top box the communication method comprising receiving a request for processing an API that is not independently processable by using the broadcasting receiving apparatus from the broadcasting receiving apparatus for executing an application for providing the interactive service calling the API corresponding to the request acquiring data by processing the called API and transmitting the acquired data to the broadcasting receiving apparatus.

The STB may be connected to at least one device including the broadcasting receiving apparatus through a home network and wherein the broadcasting receiving apparatus is a digital TV set.

Middleware defined in the OCAP standard or the MHP standard may be installed in the STB and wherein the application is an OCAP middleware based application or an MHP middleware based application.

Middleware that is the same as the middleware installed in the STB may be installed in the broadcasting receiving apparatus.

According to another aspect of the present invention there is provided an apparatus for receiving a broadcasting service through a set top box and providing an interactive service the apparatus comprising an execution unit executing an application for providing the interactive service by using installed middleware a determination unit determining whether the application is independently executable and a data request unit selectively requesting the STB to provide data needed for executing the application based on the determination result.

According to another aspect of the present invention there is provided an apparatus for performing communication so as to provide an interactive service to a broadcasting receiving apparatus the apparatus comprising an API processing request receiving unit receiving a request for processing an API that is not independently processable by using the broadcasting receiving apparatus from the broadcasting receiving apparatus for executing an application for providing the interactive service and calling the requested API an API processing unit acquiring data by processing the called API and a data transmission unit transmitting the data acquired by the API processing unit to the broadcasting receiving apparatus.

Hereinafter the present invention will be described in detail by explaining exemplary embodiments of the invention with reference to the attached drawings.

Referring to the system according to the current exemplary embodiment includes an HANA TV and an OCAP network interface unit NIU . The system enables an OCAP application to be executed on the HANA TV .

The HANA TV includes an OCAP API a Java virtual machine JVM a porting layer an IEEE 1394 channel and an operating system OS .

The JVM serves to analyze an API written in Java by using a virtual computer and apply the API so that the API is processed by the OS . In the current exemplary embodiment the JVM applies the API suitably for the OS so that the OCAP API can be processed by the HANA TV . The OCAP API and the JVM constitute middleware throughout the specification. The OCAP API operates on the JVM . An apparatus including the JVM can process the OCAP API without additional modification.

The porting layer allocates system resources such as memories so as to process the API called by the JVM . The API is processed by using the allocated system resources.

The local call is a module for processing APIs which are independently processed by the HANA TV . The independently processable APIs are mainly related to graphic processing. The APIs process graphics and display the graphics in a GUI form. That is the local call processes only APIs for which it is unnecessary to externally receive data.

On the other hand like a case where data has to be processed through an external network or a case where data has to be received through the external network an API that uses system resources for example a tuner in the API and the OCAP NIU which have to externally receive data is processed by the OCAP NIU through the remote call to be described later. The local call is functionally the same as an NIU porting layer in the OCAP NIU . Accordingly a module of the NIU porting layer may be reused for the local call .

The remote call induces APIs which are not independently processable on the HANA TV to be processed by the OCAP NIU . The remote call requests the OCAP NIU to process the APIs by using a remote procedure call RPC and receives the processed result. The RPC is used to call a function to be executed in a first device by using a second device. If the second device calls a desired function through the RPC the first device processes the function and returns the processed result to the second device.

The APIs which are not independently processable on the HANA TV are mainly related to processing of data. For example in the APIs like the interactive service data generated by the HANA TV has to be processed by an external server and transmitted to the HANA TV again. In addition even in a case where the API has to use shared resources such as a tuner cable card the API has to be processed by the OCAP NIU .

The IEEE 1394 channel is a type of a data cable for connecting the OCAP NIU to the HANA TV . The IEEE 1394 channel can embody a fast home network as compared with a local area network LAN .

The OCAP NIU connects at least one HANA TV to peripherals through the IEEE 1394 cable. The OCAP NIU serves to receive broadcasting data with a format of MPEG 2 TS and electronic program guide EPG information and transmit the broadcasting data and the EPG information or serves to perform a series of operations related to a broadcasting service such as a tuning service for tuning a channel to a desired broadcasting channel. In addition data for providing an interactive service to the HANA TV is requested and received through an external communication network.

The OCAP NIU includes an OCAP API a JVM a remote API handler an NIU porting layer an IEEE 1394 channel and an OS . In the OCAP NIU the OCAP API the JVM the IEEE 1394 channel and the OS perform the same functions as corresponding elements in the HANA TV . Accordingly descriptions thereof are not provided.

The remote API handler calls an API which is requested through the remote call to be processed. Since the same middleware is installed in the OCAP NIU and the HANA TV it is possible to easily call the API called by the remote call without additional mapping information.

The NIU porting layer processes the API called by the remote API hander and transmits the processed result to the HANA TV .

In the exemplary embodiment it is possible to execute an application in the HANA TV by installing OCAP middleware and in the HANA TV without modifying or extending middleware according to the OCAP standard. However in a case where the API is not independently processable on the HANA TV it is possible to execute the application by processing the API by using the remote call in the OCAP NIU .

More specifically the user selects a desired device from among devices connected to a home network. In a case where the user selects the OCAP NIU by using an interface of the HANA TV in order to receive a service from the OCAP NIU is assumed. If the user selects the OCAP NIU a list of OCAP applications provided by the OCAP NIU is displayed on the HANA TV . If the user selects a desired OCAP application the application is downloaded to the HANA TV . The downloaded OCAP application is registered in an OCAP monitor application not shown in the HANA TV . The OCAP monitor application not shown is an API for monitoring types and execution information of an application to be executed on the HANA TV . The downloaded OCAP application is executed in the HANA TV .

The OCAP application indicates an OCAP based application throughout the specification. The OCAP application may be previously downloaded to the HANA TV through the OCAP NIU .

In operation S the OCAP application calls a necessary OCAP API . The OCAP API calls the JVM . The JVM calls the TV porting layer sin order to process the called API.

In operation S the TV porting layer determines whether the called API is independently processable in the HANA TV and selectively requests the OCAP NIU to process the API. That is in a case where the called API is independently processable on the HANA TV the local call directly processes the API. However in a case where the called API is not independently processable on the HANA TV for example a case where the called API has to consume resources on the OCAP NIU or process data through a network the OCAP NIU is requested to process the API through the remote call . A method of requesting the API to be processed by using the remote call may be performed by the RPC.

In operation S the remote API handler calls an API corresponding to a request of the remote call . The NIU porting layer processes the called API.

Referring to the service providing apparatus according to the current exemplary embodiment of the present invention includes an execution unit a determination unit a data request unit and a data receiving unit . The service providing apparatus is one of a plurality of devices connected to an STB through a home network. In this regard the service providing apparatus may be an HANA based digital TV set.

The execution unit executes an application for providing an interactive service by using middleware installed in the service providing apparatus .

In a case where the STB receives broadcasting data through a cable middleware defined in an OCAP standard is installed in the STB and the service providing apparatus . On the other hand in a case where the STB receives broadcasting data through a satellite antenna middleware defined in the MHP standard is installed in the STB and the service providing apparatus .

If the OCAP middleware is installed in the service providing apparatus the execution unit executes the OCAP based application by using the OCAP middleware. The execution unit calls an API needed for executing an application as shown in the exemplary embodiments of and processes the called API through the JVM and the porting layer. The result obtained by processing the API may be transmitted to the application or displayed to the user.

The determination unit determines whether the application is independently executable in the service providing apparatus based on a type of the API called by the application. If the application calls a first API that has to be processed by the STB it is determined that the application is not independently processable in the service providing apparatus .

The first API includes APIs which have to use resources on the STB such as a tuner and a cable card and APIs for processing data through a network in an application for providing an interactive service.

For example it is assumed that the user executes an application for purchasing a product. If the user selects a corresponding application an API for displaying an initial window for purchasing a product or displaying product information is called. Since the API performs a graphic process irrelevant to data processing the execution unit independently processes the API and displays the initial window for purchasing the product or the product information.

Subsequently if the user selects a desired product an API for paying for the product is called. The API for paying for the product is the first API that is not independently processable by using the execution unit . The determination unit determines that the application is not independently processable.

The data request unit selectively requests the STB to provide data needed for executing the application based on the determination result of the determination unit . That is if the application calls the first API the data request unit requests the STB to process the first API.

Middleware that is the same as the middleware installed in the service providing apparatus may be installed in the STB .

If the middleware installed in the STB is different from the middleware installed in the service providing apparatus the data request unit has to further include additional mapping information so that the STB calls the API with the same function as the first API. However if the middleware installed in the STB is the same as the middleware installed in the service providing apparatus the data request unit can easily request the first API to be processed without additional mapping information. The data request unit can induce the STB to call the first API by using the RPC.

The execution unit executes the application by using the result obtained by processing the first API which is received by the data receiving unit .

Referring to the communication apparatus according to the current exemplary embodiment of the present invention includes an API processing request receiving unit an API processing unit and a data transmission unit . The communication apparatus is connected to devices including at least one broadcasting receiving apparatus through a home network. The broadcasting receiving apparatus may be an HANA based digital TV.

The API processing request receiving unit receives a request for processing an API that is not independently processable by using the service providing apparatus from the broadcasting receiving apparatus for executing an application for providing an interactive service and calls the requested API. The API processing request receiving unit may receive a request for processing the API by using the RPC from the service providing apparatus .

The data transmission unit transmits the data acquired by the API processing unit to the service providing apparatus .

The middleware defined in the OCAP or MHP standard may be installed in the communication apparatus . At this time an application for providing an interactive service may be an OCAP middleware based application or an MHP middleware based application. Specifically the same middleware is installed in the communication apparatus and the service providing apparatus so that the broadcasting receiving apparatus request the communication apparatus to process the API without additional mapping information.

In operation S it is determined whether an API called by the application is a first API. As described above the first API indicates an API that is not independently processable in the broadcasting receiving apparatus. If it is determined that the API called by the application is the first API the API is not independently processable in the broadcasting receiving apparatus. Accordingly an STB is requested to process the first API by performing operation S. However in a case where it is determined that the API called by the application is not the first API the API is independently processed in the broadcasting receiving apparatus by performing operation S.

In operation S the STB is requested to provide data needed for executing the application. If the application calls first API data the result data obtained by processing the first API may be data needed for executing the application.

In operation S if the API called by the application is not the first API the called API is independently processed in the broadcasting receiving apparatus.

In operation S a request for processing an API that is not independently processable by using the broadcasting receiving apparatus is received from the broadcasting receiving apparatus for executing an application for providing an interactive service.

It is possible for at least one broadcasting receiving apparatus to directly execute an OCAP application by installing the OCAP middleware in the at least one broadcasting receiving apparatus.

In addition it is possible to use existing OCAP middleware by installing the OCAP middleware in the broadcasting receiving apparatus without extending or modifying the OCAP middleware. Accordingly it is possible to reduce costs used for customizing an OCAP.

In addition it is possible to increase usability of an expandable home theater XHT based solution and to activate an XHT standard by enabling an OCAP application to be executed in at least one broadcasting receiving apparatus connected to an STB through a home network.

The exemplary embodiments of the present invention can be written as computer programs and can be implemented in general use digital computers that execute the programs using a computer readable recording medium.

Examples of the computer readable recording medium include magnetic storage media e.g. ROM floppy disks hard disks etc. optical recording media e.g. CD ROMs or DVDs and other storage media.

While the present invention has been particularly shown and described with reference to exemplary embodiments thereof it will be understood by those skilled in the art that various changes in form and details may be made therein without departing from the spirit and scope of the invention as defined by the appended claims. The exemplary embodiments should be considered in descriptive sense only and not for purposes of limitation. Therefore the scope of the invention is defined not by the detailed description of the invention but by the appended claims and all differences within the scope will be construed as being included in the present invention.

