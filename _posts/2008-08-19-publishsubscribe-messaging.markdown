---

title: Publish/subscribe messaging
abstract: The invention relates to a message brokering system for connecting a client in a local publish/subscribe messaging system to a remote message broker. The system comprises a message broker in said local publish/subscribe messaging system and a metabroker application means representing said remote message broker. The local message broker comprises publish/subscribe means for proxying messages between the client and the metabroker application means. The metabroker application means comprises publish/subscribe means for proxying messages between the local broker and the remote broker.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08065372&OS=08065372&RS=08065372
owner: International Business Machines Corporation
number: 08065372
owner_city: Armonk
owner_country: US
publication_date: 20080819
---
This application is a continuation of application Ser. No. 10 547 724 filed Sep. 1 2005 now U.S. Pat. No. 7 437 417.

Publish and Subscribe is an effective way of disseminating information to multiple users. Publish Subscribe pub sub applications can help to enormously simplify the task of getting business messages and transactions to a wide dynamic and potentially large audience in a timely manner.

In the field of this invention it is known that pub sub applications are typically written so that a community of clients with a common purpose all connect in to a particular broker to enable them to send and receive messages amongst themselves. An obvious example is producer consumer applications where one set of clients produce data and another set consume that data. Another example is in online gaming where individual clients connect into a central hub to gain access to common services like billing game updates high scores etc.

However a problem with this arrangement is that the pub sub architecture is static things become difficult if one of the clients needs to get access to some data which is being published to a different broker somewhere else in the world for example if it only occasionally needs to go to update some data table e.g. average rainfall in some city over a year or perhaps if an online gaming client needs to report a bug to the game manufacturer or publish a new high high score for global recognition.

On the World Wide Web a user can easily jump off the current web server and go to a different one simply by following a hyperlink. With Web Services a user can look up the connection information for a service that the user wishes to make use of. However heretofore such alternate sourcing of information has not been possible for pub sub.

It is possible for a client to disconnect from its current broker and reconnect to a different one but that assumes that all clients have external connectivity to allow them to reach the remote brokers and in the closed world of say an online gaming system that is often not the case and there are reasons such as security why the clients should not be given such general access . So the problem to be solved is gaining pub sub access to a remote broker given the restricted environment of a closed community pub sub system.

A need therefore exists for users of a closed pub sub community connected to a central broker facility to be able to exchange pub sub messages with other remote brokers without gaining a direct connection to those brokers wherein the abovementioned disadvantage s may be alleviated.

In accordance with one illustrative embodiment a message brokering system connects a client in a local publish subscribe messaging system to a remote message broker. The message brokering system comprises a processor and a storage medium storing a metabroker application for representing the remote message broker. The metabroker application is a client of a community broker that is local to a plurality of clients and comprising a publish subscribe system for proxying messages between the plurality of clients and the remote message broker. The metabroker application when executed by the processor causes the processor to receive a message originating at a given client within the plurality of clients and destined for the remote message broker by subscribing to the community broker in order to receive messages addressed to the remote message broker and forward the received message to the remote message broker. The metabroker application when executed by the processor causes the processor to publish a message received from the remote message broker to the community broker. Publishing the message received from the remote message broker to the community broker comprises indicating that the message is destined for a subset of clients within the plurality of clients having subscribed to receive messages from the remote message broker and enabling the subset of clients to subscribe to the community broker to receive messages from the remote message broker.

In accordance with another illustrative embodiment a computer program product comprises a computer readable storage medium having a computer readable program stored thereon. The computer readable program when executed on a computing device causes the computing device to connect a client in a local publish subscribe messaging system to a remote message broker. A metabroker application is a client of a community broker that is local to a plurality of clients and represents said remote broker. The computer readable program comprises computer instructions for using a publish subscribe messaging system to proxy messages received at the metabroker application between the plurality of clients and the remote message broker. Proxying messages between the plurality of clients and the remote message broker comprises receiving a message originating at a given client within the plurality of clients and destined for the remote message broker by subscribing to the community broker in order to receive such messages and forwarding the received message to the remote message broker. Proxying messages between the plurality of clients and the remote message broker further comprises publishing a message received from the remote message broker to the community broker using a topic designated as a topic for remote broker messages thereby enabling a subset of clients within the plurality of clients to subscribe to the topic at the community broker in order to receive messages from the remote message broker.

Referring to a pub sub messaging system has a number of pub sub clients three of which and are shown are each connected to their local community broker . A metabroker application is also a client to the community broker and is permanently connected and subscribes to the wildcard topic metabroker where is the topic wildcard symbol so that it receives all messages that have topics prefixed with the name metabroker e.g. metabroker a b.

When a client application wishes to gain access to a remote broker it requests a connection to the metabroker Java Message Service JMS service Java and all Java based trademarks are trademarks or registered trademarks of Sun Microsystems Inc. in the United States other countries or both. 

This JMS service is in practice a software library comprising a JMS API Application Programming Interface a metabroker JMS TopicConnectionFactory TCF and a community JMS TCF running on the client which gives the client application the impression that it is making a connection to a remote broker but is in fact making use of the normal existing connection to the community broker to send special messages to the metabroker by publishing messages to the community broker which the metabroker receives as a subscriber. The metabroker in turn connects to the required remote broker and proxies messages back and forth to the client application all via pub sub through the community broker . In effect this may considered as pub sub over pub sub .

When creating the JMS connection object the client application passes as parameters an identifier for the remote broker service the user wishes to make use of. This might be explicit as an IP address and port or a domain name and port or it might be a service name which would be treated as a Web Service service name and a UDDI lookup is performed to resolve the connection information for that broker service. It will be understood that there are a number of ways of mapping from service names to physical connection details UDDI being simply an example.

The JMS implementation for the metabroker service uses the existing connection to the community broker to which the client is usually attached to flow messages to and from the metabroker application. This might be through a JMS interface or some other messaging capability which supports a publish subscribe messaging model.

Below there is described one possible implementation of topics and message structures which could be used to implement a pub sub messaging model through the metabroker application through a pub sub messaging system. In the following description it is assumed that message bodies would use a suitably structured data representation e.g. XML or name value pairs. When the action of the client is described it is to be understood that this is the client side implementation of the metabroker JMS service typically implemented as a library which the client application accesses. The action of the metabroker application is explained where needed for clarification. The client application will simply make the usual JMS API calls to publish and subscribe to data on the remote broker to which it is logically attached unaware of the proxying via the community broker which is happening in the JMS library layer i.e. in the FIGURE .

In other words the client application already knows how to reach the community broker or knows which directory to ask for instructions on how to connect e.g. Java Naming and Directory Interface lookup . The community broker communicates with the metabroker application using publish subscribe and the meta broker application makes the connection to the remote broker.

Upon successful address resolution and connection to the remote broker the metabroker application publishes a message to the community broker 

Assuming a successful connection indicated by the return code the client un subscribes in the community broker from 

The client receives the response message from the metabroker due to its subscription and is able to notify the application of the outcome of the request through the appropriate JMS return code.

When the message has been successfully published by the metabroker application to the remote broker the metabroker publishes a message to the community broker 

The client receives this message due to its subscription and is able to notify the application of the outcome of the request through the appropriate JMS return code.

The metabroker receives this message and subscribes to the requested topic s on behalf of the client.

When the remote subscription is acknowledged the metabroker publishes a message to the community broker 

The client receives this message due to its subscription and is able to notify the application of the outcome of the request through the appropriate JMS return code.

When the metabroker receives a message from the remote broker which is destined for one of the community broker clients that has a remote broker session through the metabroker application it determines using a lookup table and possibly a publication matching engine not shown which client this message is for and publishes a message to the community broker 

The client application receives the message and invokes the appropriate mechanism to notify the application that an incoming message has been received which matches the subscription that was placed earlier.

Note the remote broker sends a copy of a publication message to each client that has registered an interest subscribed . The metabroker application is one such subscribe and has subscribed on behalf of its clients based on their subscribe request s via the community broker.

Some brokers or rather some connection protocols allow messages to be held for a subscriber even if they re not actually connected at that time. Thus the metabroker might if it was using such a protocol subscribe to some topics on behalf of one of its clients and then get disconnected and come back later to the broker and collect the messages that match its subscription and then can forward them to its clients. IBM s WebSphere MQ is one such protocol. Such subscriptions are known as durable subscriptions i.e. they last even when the client disconnects and they have to be explicitly cancelled unsubscribed when no longer required.

When the client requests a disconnection from the remote broker the client libraries publish the message 

After disconnecting from the remote broker the metabroker publishes a message to the community broker 

The client receives this message due to its subscription and is able to notify the application of the outcome of the request through the appropriate JMS return code.

It will be understood that the heterogeneous multi broker proxying on demand system with message broker web services described above provides the following advantages 

Clients connected to the community broker can gain access to a remote pub sub broker without needing a direct network connection to it by making use of its single existing connection to the community broker.

Several clients connected to the community broker can make use of a single connection from the metabroker to the remote broker which is useful if there are scalability connectivity or firewall issues they can be dealt with by the metabroker on behalf of all the clients.

The remote broker service may be described and advertised through Web Services mechanisms such as WSDL UDDI etc. which gives a convenient way of locating and finding out how to establish a connection to the remote brokers.

It will be appreciated that the method described above for publish subscribe messaging may be carried out in software running on a processor not shown and that the software may be provided as a computer program element carried on any suitable data carrier also not shown such as a magnetic or optical computer disc.

In summary it will be understood that the heterogeneous multi broker proxying on demand system with message broker web services described above provides the advantage that clients connected to a community broker can gain access to a remote pub sub broker without needing a direct network connection to it by making use of its single existing connection to the community broker. Also several clients connected to a community broker can make use of a single connection from the metabroker to the remote broker which is useful if there are scalability connectivity or firewall issues they can be dealt with by the metabroker on behalf of all the clients. The remote broker service may be described and advertised through Web Services mechanisms such as WSDL UDDI etc. which gives a convenient way of locating and finding out how to establish a connection to the remote broker s .

