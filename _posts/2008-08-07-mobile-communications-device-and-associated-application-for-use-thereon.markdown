---

title: Mobile communications device and associated application for use thereon
abstract: An application manager configured for use on a resource-limited device, the application manager including: an application engine configured to effect communications between a plurality of applications installed on the resource limited device and one or more external network sites; and a connection manager configured to control and/or coordinate when the plurality of applications are able to attempt to establish communications with the one or more external network sites. The resource-limited device may be a mobile terminal.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08190747&OS=08190747&RS=08190747
owner: Vodafone Group Services Limited
number: 08190747
owner_city: Newbury, Berkshire
owner_country: GB
publication_date: 20080807
---
The system described herein relates to a device with computing capabilities particularly a resource constrained device and a technique for conserving resources associated with the device such as battery capacity memory capacity and or network resources. More particularly the system described herein relates to a mobile terminal.

Mobile terminals such as mobile telephones Personal Digital Assistants PDAs and the like have an ever increasing number of functionalities. Where once a mobile terminal was just for transmitting and receiving communications between two entities now such terminals have innumerable additional functionalities which are enabled by so called Widgets .

In a computing context a Widget is a single function application that performs a specific task or function. A Widget could also be described as an executable file or applet. Most typically Widgets download data from an external network source and use that data to display information to the user. The displayed information may invite the user to act in a number of ways. For instance the user may use graphical components such as buttons dialog boxes pop up windows pull down menus icons scroll bars resizable window edges progress indicators selection boxes windows tear off menus menu bars toggle switches and or forms to interact with the Widget.

It is to be appreciated that the term Widget can also be used to refer to the graphic component rather than its controlling application or to the combination of both.

Many but not all Widgets leverage web technologies to perform a specific task or function and typically display something to the user. An example of one such application is a stock market Widget that displays the share price of certain stocks typically stocks pre designated by the user. A further example is a Widget that is configured to display weather details for one or more pre designated locations.

Today mobile terminals typically have multiple Widgets installed any or all of which can be implemented at any one time. While this provides the mobile terminal with enhanced utility regular and or concurrent use of many of the Widgets unfortunately leads to a greater drain on battery resources. The lifetime of a mobile terminal s battery is an extremely important aspect as users find it undesirable to have to be recharging their terminal s battery with any great regularity or even worse having the terminal shut down unexpectedly due to a lack of battery power.

Further where the Widget is implemented on a mobile terminal since a cellular network is involved a Packet Data Protocol PDP context additionally needs to be created in order to send and receive packet switched data via the General Packet Radio Services GPRS Core Network. Therefore before the Widget Engine transmits the data request to the Internet address via the cellular network a PDP context needs to be set up. The PDP context is a data structure typically stored on both the Serving GPRS Support Node SGSN and the Gateway GPRS Support Node GGSN associated the Radio Network Controller RNC serving the terminal in the cellular network. The PDP context contains the terminal s active session information. For instance when a mobile terminal wants to use GPRS it must first attach and then activate a PDP context. This allocates a PDP context data structure in the SGSN that the subscriber is currently visiting and the GGSN serving the terminal s access point. The PDP context is essentially used by the cellular network to know where to route data intended for the mobile terminal.

In order to send and receive packet switched data the Widget Engine would invoke an HTTP related API which in turn would trigger the afore mentioned PDP context set up. The API would convey the request to the web address via the HTTP Stack which conforms the request according to the Protocol requirements so that it can be transmitted across the Internet.

Ideally the PDP context is dismantled once the required data has been transmitted. However it is to be appreciated that in establishing and dismantling the PDP context more data is required to be transmitted than would be used to transmit the actual content to the terminal. This approach is therefore wasteful and not ideal.

This problem is heightened when multiple widgets are operating at any one time since the PDP contexts may need to be regularly established and dismantled using up a lot of network resources.

This problem could be addressed by not dismantling the PDP contexts and relying on the network to time out each PDP context after a particular period of inactivity. This solution is not ideal however since the MSC SGSN can only support a particular number of PDP contexts simultaneously and this approach provides no guarantees that a MSC SGSN will not be supporting PDP contexts of terminals no longer requiring internet access.

In this regard it should also be noted that a cellular network is set up with the expectation that not all terminals will have a PDP context established simultaneously.

According to a first aspect the system described herein provides an application manager configured for use on a resource limited device the application manager including an application engine configured to effect communications between a plurality of applications installed on the resource limited device and one or more external network sites and a connection manager configured to control and or coordinate when the plurality of applications are able to attempt to establish communications with the one or more external network sites.

According to a second aspect the system described herein provides on a resource limited device having an application engine configured to effect communications between a plurality of applications installed thereon and one or more external network sites a method of managing the plurality of applications the method including coordinating when the plurality of applications are able to attempt to establish communications with the one or more external network sites.

These aspects of the system described herein are concerned with conserving network resources and also conserving battery life and memory capacity. Obviously the latter issues may be particularly applicable to mobile devices. The former issue may be particularly applicable to cellular networks.

With reference to a simplified architecture of a widget framework as it currently exists on Mobile Terminals is shown. Each Widget or application is in communication with a Widget Engine . For simplicity only one Widget is shown in but the Widget Engine may be configured to manage multiple Widgets.

In order to minimise their complexity each Widget may be created using a Scripting language. When a Widget is implemented the Widget Engine functionally interprets the script. The script may include a request for information from a web service .

In other words the Widget Engine provides a runtime environment for the independent execution of each of the Widgets. In some embodiments the Widget Engine uses a Javascript runtime environment combined with an XML interpreter however other platforms are possible. Javascript and XML may be used as they are open standards and therefore usable in many different operating systems computer architectures and web browsers.

Several Widget Engine platforms have been developed specifically for small resource constrained devices for instance Asynchronous Javascript XML AJAX based mobile Widget Engines and Java 2 Platform Micro Edition J2ME based mobile Widget Engines.

In addition to script interpretation the Widget Engine may provide each Widget with lifetime management and Application Programming Interfaces APIs such as presentation APIs and HTTP related APIs. Presentation APIs take advantage of today s advanced graphics and allow Widgets to blend fluidly into the Graphical User Interface GUI of the terminal without the constraints of traditional window borders. HTTP related APIs such as XML Interpreters may provide access to the internet and web services via an interface to the HTTP stack. It is to be appreciated that the Hypertext Transfer Protocol HTTP is may be used to convey information about the worldwide web but other protocols could be used. Similarly information may be conveyed in Hypertext Mark up Language HTML or Extended Hypertext Mark up Language XHTML or XML files although again other formats could be used.

Widget is configured such that it seeks access to the web service intermittently for example once every two hours. The Widget Engine may upon receiving the access request interpret the script and seek access the pre determined network address from which to extract the required information. A PDP context would also be created for the terminal.

As indicated previously the framework of is able to support multiple Widgets running concurrently on the terminal with each Widget being able to connect to the associated Web services via the Widget engine. However since the network connections establish and dismantle the PDP context on an independent basis the usage of network resources may be sub optimal. Furthermore as indicated previously it also places an increased load on the battery leading to a reduction in battery life for the device.

To address these issues the system described herein proposes a connection manager as shown in the embodiment. The connection manager may be considered as a component of the Widget Engine or as a stand alone feature.

The connection manager provides a means of coordinating of the Widgets on a mobile terminal. For example the connection manager may schedule the connection of multiple Widgets to the network at a particular time in order to reduce the use of network resources and to minimise terminal battery usage. For instance the connection manager may be configured to make an announcement to all the Widgets when a PDP context has been created and a network connection has been made. The Widgets may then individually decide whether to access the network at that particular point in time. For some Widgets access to the network at that time may not be required and may therefore not react to the notification. For example the Widget may be a television guide that only requires updating every seven days or so.

The Connection Manager can coordinate the Widgets in a number of ways. For example the connection manager may schedule a connection at a specific time of the day and make this connection available to each of the Widgets or can react to a specific request from a Widget and notify the others that it has now opened a connection which they could also exploit or a combination of both may be employed. The frequency at which a Widget needs to connect is dependent on the type of information being retrieved and presented by the Widget. For example a Weather Widget may be set with a frequency of once per day whilst a stock Widget may be configured to fire after 15 mins .

In order to allow the Connection Manager to communicate with the individual Widgets an interface may be defined therebetween. Each Widget is configured to support the interface so that they can communicate with the connection manager.

In general the interface may be of an abstract type and may specify a set of behaviours or methods that a Widget supporting the interface implements. The interface may be implemented in any appropriate programming language such as Java or C . Javascript may be used.

Since all Widgets support the interface the Connection Manager may be able to iteratively call one or more appropriate functions defined by the interface across the set of active widgets. What each Widget does in response to the function s being called however is Widget specific and may be defined by the developer of the Widget at design time.

Referring to three widgets are illustrated as in communication with the Widget Engine and the Connection manager . It is appreciated that this number of Widgets is for illustration purposes only and any number of Widgets may in fact be implemented. Consider the example of Widget being a widget configured to provide stock market results widget being a widget configured to provide a weather update and widget being a widget configured to perform some other function.

Widget has an internal timer that fires for example every 1 hour. This timer calls the function getStockPrice . This function sends a request to a specific URL parses the response and displays the latest share price to the user. When the timer fires the resultant HTTP request will trigger the setup of a PDP context thereby enabling the request and response to be sent at least partially over a wireless network.

More specifically referring to the steps shown in every time the timer within Widget fires getStockPrice is called which creates a request and sends this to the URL specified within the script step . The script interpreter within the Widget Engine determines that a widget is attempting to access the Internet step and the script interpreter signals this to the Connection Manager step . The Connection Manager iterates through the collection of active widgets executing the IConnectionManager OnConnectNotify function in each Widget steps and . The action that each widget performs when this function is called is dependant on the Widget s script contents which is specific to each Widget.

Where a notified Widget determines that the current point in time is suitable to upload data from its pre designated URL it proceeds with sending the request to the URL without the terminal additionally requiring to set up the PDP context since this will have already been set up when the first Widget initiated the network communication.

An advantage of this embodiment of the system described herein is that the use of network resources can be reduced and terminal battery usage minimised through the connection manager controlling the scheduling of Widget connections.

According to a further embodiment of the system described herein a user defined Widget connection policy exists which defines when the terminal is able to connect to the network. To effect this embodiment the connection manager has the functionality of being able to determine if the user has set a Widget connection policy defining a specific time or times when each Widget can or cannot connect to the network. This connection policy may be implemented as a behaviour method that is available to all Widgets via the Widget Engine.

These user defined times may override any Widget specific timings. In this way a user of a terminal is able to control network connection times and thereby conserve battery memory and network resources as required.

According to a further embodiment the policy may also allow a user to prohibit Widgets from updating when roaming or when battery levels are particularly low.

According to a still further embodiment of the system described herein the Connection Manager supports the ability to reject a connection request from a Widget. In order to allow Widget developers to handle this case a custom HTTP 5xx response code may be used. When the Connection Manager refuses a connection request it will respond to the connection request with this response code this allows the Widget developer to program an appropriate behaviour for the Widget.

When a connection becomes available again the Connection Manager may use the appropriate interface function to signal this to the Widget.

Although the embodiments of the system described herein are particularly applicable to small resource constrained devices such as mobile terminals and PDAs the system described herein may also be applied to other devices with computing capabilities such as desktop computers laptop computers and set top boxes. Obviously where such devices do not require part of the information retrieval to take place over a wireless network the PDP context set up may not apply.

