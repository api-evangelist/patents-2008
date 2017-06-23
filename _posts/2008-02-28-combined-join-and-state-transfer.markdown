---

title: Combined join and state transfer
abstract: A method and apparatus for processing messages is described. In one embodiment, an application programming interface provides for a flush protocol to force members of a group to send all of their pending messages prior to a predetermined event. A client sends a request to a coordinator of the group to join the group and to transfer a state of the group to the client. The application programming interface performs a single flush operation on the group in response to the request.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08312084&OS=08312084&RS=08312084
owner: Red Hat, Inc.
number: 08312084
owner_city: Raleigh
owner_country: US
publication_date: 20080228
---
Embodiments of the present invention relate to group communication and more specifically to processing of messages.

Group communication protocol designed for multicast communication may be used to communicate messages between endpoints forming a group. Communication endpoints can be processes or objects or any entity that can send and receive messages to from a group.

A flush protocol forces group members to send all their pending message prior a predetermined event. The process of flushing acquiesces the cluster so that a state transfer operation or a join operation can be achieved. Thus a flush operation is performed on a group when a new member joins the group. Subsequently in to transfer the state of the group to the new member another flush operation needs to be performed. As such two flush operations are required upon a join and state transfer operations. It would be desirable to require only one flush operation for both join and state transfer operations.

Described herein is a method and apparatus for flushing messages in a group. In one embodiment an application programming interface provides for a flush protocol to force members of a group to send all of their pending messages prior to a predetermined event. A client sends a request to a coordinator of the group to join the group and to transfer a state of the group to the client. The application programming interface performs a single flush operation on the group in response to the request.

In one embodiment a JAVA application uses JGroups library in order to achieve group communication between members. Group communication involves message exchange between set of processes in presence of process failures and network interruptions. One powerful feature of JGroups is its flexible protocol stack which allows developers to adapt JGroups to exactly match their application requirements and underlying network characteristics. By mixing and matching protocols multiple application requirements can be satisfied at a minimum cost.

Each group member process in JGroups is represented by JChannel object. The best way to think of a JChannel is a socket like abstraction allowing message sending and receiving. JChannel also allows registration of callback interfaces that are invoked when channel related events occur. Messages exchanged between JChannel instances have a payload and a pair of sender and receiver addresses. A view is an ordered list of member addresses representing current agreed membership of a group cluster. When a new member joins or a member crashes a new view will be installed in all members including the new member. For example if we have a cluster of A B and C the view is V A B C. If a new member D joins then everyone will have view V A B C D. If member A crashes we will have view V B C D. Note that we add members in the order in which they join the group.

The group communication architecture may comprise three parts 1 a channel API used by application programmers to build reliable group communication applications 2 building blocks which are layered on top of channel and provide a higher abstraction level and 3 a protocol stack which implements the properties specified for a given channel.

Channel is connected to protocol stack . Whenever an application sends a message channel passes it on to protocol stack comprising several protocols . The topmost protocol processes the message and the passes it on to the protocol below it. Thus the message is handed from protocol to protocol until the bottom protocol puts it on the network . The same happens in the reverse direction the bottom transport protocol listens for messages on network . When a message is received it will be handed up protocol stack until it reaches channel . Channel stores the message in a queue until application consumes it.

When an application connects to a channel protocol stack will be started and when it disconnects protocol stack will be stopped. When the channel is closed the stack will be destroyed releasing its resources.

To join a group and send messages a process has to create a channel and connect to it using the group name all channels with the same name form a group . The channel is the handle to the group. While connected a member may send and receive messages to from all other group members. The client leaves a group by disconnecting from the channel. A channel can be reused clients can connect to it again after having disconnected. However a channel may allow only one client to be connected at a time. If multiple groups are to be joined multiple channels can be created and connected to. A client signals that it no longer wants to use a channel by closing it. After this operation the channel may not be used any longer.

Each channel has a unique address. Channels always know who the other members are in the same group an list of member addresses can be retrieved from any channel. This list is called a view. In other words a view is an ordered list of all members in a group that every member has the same ordered list of member view. A process can select an address from this list and send a unicast message to it also to itself or it may send a multicast message to all members of the current view. Whenever a process joins or leaves a group or when a crashed process has been detected a new view is sent to all remaining group members. When a member process is suspected of having crashed a suspicion message is received by all non faulty members. Thus channels receive regular messages view messages and suspicion messages. A client may choose to turn reception of views and suspicions on off on a channel basis.

Channels may be similar to BSD sockets messages are stored in a channel until a client removes the next one pull principle . When no message is currently available a client is blocked until the next available message has been received.

A channel may be implemented over a number of alternatives for group transport. Therefore a channel is an abstract class and concrete implementations are derived from it e.g. a channel implementation using its own protocol stack or others using existing group transports such as Jchannel and EnsChannel. Applications only deal with the abstract channel class and the actual implementation can be chosen at startup time.

The properties for a channel may be specified in a colon delimited string format. When creating a channel JChannel a protocol stack will be created according to these properties. All messages will pass through this stack ensuring the quality of service specified by the properties string for a given channel.

Channels are simple and primitive. They offer the bare functionality of group communication and have on purpose been designed after the simple model of BSD sockets which are widely used and well understood. The reason is that an application can make use of just this small subset of JGroups without having to include a whole set of sophisticated classes that it may not even need. Also a somewhat minimalistic interface is simple to understand a client needs to know about 12 methods to be able to create and use a channel and oftentimes will only use 3 4 methods frequently .

Channels provide asynchronous message sending reception somewhat similar to UDP. A message sent is essentially put on the network and the send method will return immediately. Conceptual requests or responses to previous requests are received in undefined order and the application has to take care of matching responses with requests.

Also an application has to actively retrieve messages from a channel pull style it is not notified when a message has been received. Note that pull style message reception often needs another thread of execution or some form of event loop in which a channel is periodically polled for messages. JGroups offers a push style as well. Push style is easier to use from JAVA application perspective. Application receives a callback as messages arrive rather than having to actively pull message in an event loop.

JGroups offers building blocks that provide more sophisticated APIs on top of a Channel. Building blocks either create and use channels internally or require an existing channel to be specified when creating a building block. Applications communicate directly with the building block rather than the channel. Building blocks are intended to save the application programmer from having to write tedious and recurring code e.g. request response correlation.

All messages sent and received over the channel have to pass through the protocol stack. Every layer may modify reorder pass or drop a message or add a header to a message. A fragmentation layer might break up a message into several smaller messages adding a header with an id to each fragment and re assemble the fragments on the receiver s side.

The composition of the protocol stack i.e. its layers is determined by the creator of the channel a property string defines the layers to be used and the parameters for each layer . This string might be interpreted differently by each channel implementation in JChannel it is used to create the stack depending on the protocol names given in the property.

Knowledge about the protocol stack is not necessary when only using channels in an application. However when an application wishes to ignore the default properties for a protocol stack and configure their own stack then knowledge about what the individual layers are supposed to do is needed. Although it is syntactically possible to stack any layer on top of each other they all have the same interface this wouldn t make sense semantically in most cases.

Data is sent between members in the form of messages. A message can be sent by a member to a single member or to all members of the group of which the channel is an endpoint. illustrates an example of a structure of a message .

A list of headers can be attached to a message. Anything that should not be in the payload can be attached to message as a header. Methods putHeader getHeader and removeHeader of message can be used to manipulate headers .

The destination address may include the address of the receiver. If null the message will be sent to all current group members.

The source address may include the address of a sender. It can be left null and will be filled in by the transport protocol e.g. UDP before the message is put on the network .

The payload may include the actual data as a byte buffer . The message class contains convenience methods to set a serializable object and to retrieve it again using serialization to convert the object to from a byte buffer.

The message may be similar to an IP packet and consists of the payload a byte buffer and the addresses of the sender and receiver as addresses . Any message put on the network can be routed to its destination receiver address and replies can be returned to the sender s address.

A message usually does not need to fill in the sender s address when sending a message this is done automatically by the protocol stack before a message is put on the network. However there may be cases when the sender of a message wants to give an address different from its own so that for example a response should be returned to some other member.

The destination address receiver can be an Address denoting the address of a member determined e.g. from a message received previously or it can be null which means that the message will be sent to all members of the group. A typical multicast message sending string Hello to all members would look like this 

A view is a ordered list of all members in a group where every member has the same ordered list of members view. It consists of a ViewId which uniquely identifies the view see below and a list of members. Views are set in a channel automatically by the underlying protocol stack whenever a new member joins or an existing one leaves or crashes . All members of a group see the same sequence of views.

Note that there is a comparison function which orders all the members of a group in the same way. Usually the first member of the list is the coordinator the one who emits new views . Thus whenever the membership changes every member can determine the coordinator easily and without having to contact other members.

The code below shows how to send a unicast message to the first member of a view error checking code omitted 

Whenever an application is notified that a new view has been installed e.g. by membershipListener.viewAccepted or Channel.receive the view is already set in the channel. For example calling Channel.getView in a viewAccepted callback would return the same view or possibly the next one in case there has already been a new view .

A ViewId is used to uniquely number views. It consists of the address of the view creator and a sequence number. ViewIds can be compared for equality and put in a hashtable as they implement equals and hashCode methods.

Whenever a group splits into subgroups e.g. due to a network partition and later the subgroups merge back together a MergeView instead of a View will be received by the application. The MergeView class is a subclass of View and contains as additional instance variable the list of views that were merged. As an example if the group denoted by view V split into subgroups V and V the merged view might be V . In this case the MergeView would contains a list of 2 views V and V .

When a channel is first created at it is in the unconnected state . An attempt to perform certain operations which are only valid in the connected state e.g. send receive messages will result in an exception. After a successful connection by a client it moves to the connected state . Now channels will receive messages views and suspicions from other members and may send messages to other members or to the group. Getting the local address of a channel is guaranteed to be a valid operation in this state see below . When the channel is disconnected it moves back to the unconnected state . Both a connected and unconnected channel may be closed which makes the channel unusable for further operations. Any attempt to do so will result in an exception. When a channel is closed directly from a connected state it will first be disconnected and then closed.

A channel can be created in two ways an instance of a subclass of Channel is created directly using its public constructor e.g. new JChannel or a channel factory is created which upon request creates instances of channels. We will only look at the first method of creating channel by direct instantiation. Note that instantiation may differ between the various channel implementations. As example we will look at JChannel.

It creates an instance of JChannel. The properties argument defines the composition of the protocol stack number and type of layers parameters for each layer and their order .

When a client wants to join a group it connects to a channel giving the name of the group to be joined 

The group address is a string naming the group to be joined. All channels that are connected to the same group same name form a group. Messages multicast on any channel in the group will be received by all members including the one who sent it 3 .

The method returns as soon as the group has been joined successfully. If the channel is in the closed state see an exception will be thrown. If there are no other members i.e. no other client has connected to a group with this name then a new group is created and the member joined. The first member of a group becomes its coordinator. A coordinator is in charge of multicasting new views whenever the membership changes.

Method getLocalAddress returns the local address of the channel. In the case of JChannel the local address is generated by the bottom most layer of the protocol stack when the stack is connected to. That means that depending on the channel implementation the local address may or may not be available when a channel is in the unconnected state.

This method does not retrieve a new view message from the channel but only returns the current view of the channel. The current view is updated every time a view message is received when method receive is called and the return value is a view before the view is returned it will be installed in the channel i.e. it will become the current view.

Calling this method on an unconnected or closed channel is implementation defined. A channel may return null or it may return the last view it knew of.

The first send method has only one argument which is the message to be sent. The message s destination should either be the address of the receiver unicast or null multicast . When it is null the message will be sent to all members of the group including itself . The source address may be null if it is it will be set to the channel s address so that recipients may generate a response and send it back to the sender .

The second send method is a helper method and uses the former method internally. It requires the address of receiver and sender and an object which has to be serializable constructs a Message and sends it.

If the channel is not connected or was closed an exception will be thrown upon attempting to send a message.

A channel receives messages asynchronously from the network and stores them in a queue. When receive is called the next available message from the top of that queue is removed and returned. When there are no messages on the queue the method will block. If timeout is greater than 0 it will wait the specified number of milliseconds for a message to be received and throw a TimeoutException exception if none was received during that time. If the timeout is 0 or negative the method will wait indefinitely for the next available message.

A regular message. To send a response to the sender a new message can be created. Its destination address would be the received message s source address. Method Message.makeReply is a helper method to create a response.

A view change signalling that a member has joined left or crashed. The application may or may not perform some action upon receiving a view change e.g. updating a GUI object of the membership or redistributing a load balanced collaborative task to all members . Note that a longer action or any action that blocks should be performed in a separate thread. A MergeView will be received when or more subgroups merged into one. Here a possible state merge by the application needs to be done in a separate thread.

Flushing forces group members to send all their pending messages prior to a certain event. The process of flushing acquiesces the cluster so that state transfer or a join can be done. It is also called the stop the world model as nobody will be able to send messages while a flush is in process. Flush is used 

State transfer when a member requests state transfer it tells everyone to stop sending messages and waits for everyone s ack. Then it asks the application for its state and ships it back to the requester. After the requester has received and set the state successfully the requester tells everyone to resume sending messages.

View changes e.g. Join before installing a new view V flushing would ensure that all messages sent in the current view V are indeed delivered in V rather than in V in all non faulty members . This is essentially Virtual Synchrony.

FLUSH is designed as another protocol positioned just below the channel e.g. above STATE TRANSFER. STATE TRANSFER and GMS protocol request flush by sending a SUSPEND event up the stack where it is handled by the FLUSH protocol. The SUSPEND OK ack sent back by the FLUSH protocol let s the caller know that the flush has completed. When done e.g. view was installed or state transferred the protocol sends up a RESUME event which will allow everyone in the cluster to resume sending.

Channel can be notified that FLUSH phase has been started by turning channel block option on. By default it is turned off. If channel blocking is turned on FLUSH notifies application layer that channel has been blocked by sending EVENT.BLOCK event. Channel responds by sending EVENT.BLOCK OK event down to FLUSH protocol. In push mode application that uses channel can perform block logic by implementing MembershipListener.block callback method.

FLUSH makes sure that all members flush their pending messages and then stop sending new ones until the join or state transfer is over. However FLUSH does not make sure that on JOIN all members have seen the same set of messages before installing a new view. Example P sends M but immediately after sending M crashes. If another member Q received M but R didn t see M then with the current FLUSH R will not see M.

We need to run a messages exchange phase as part of FLUSH which makes sure that all member have seen the same set of messages in the same view before installing a new view. Whether to run this or not could be made configurable. If enabled we could piggyback the message exchange on START FLUSH FLUSH OK etc.

A simple but costly solution would be to simply multicast all messages received from other members before multicasting the FLUSH OK. A better solution would be to exchange digests with highest sequence numbers seen for all members and then only multicast the missing messages. In such cases additional message exchange phase is completed before flush phase is over.

In one embodiment an additional property e.g. connect String group name boolean fetch state String state id may be added to Channel so that joining and state transfer can be combined into one operation. As a result this would require only one FLUSH phase. The state would be returned either via pulling with Channel.receive or pushing the setState method in a registered Receiver MessageListener. In one embodiment the JOIN REQ contains the boolean. The algorithm in GMS is the same as the two described above except that before multicasting the new view and sending the JOIN RSPs and LEAVE RSPs we ask the application for its state GET APPLSTATE and when received GET APPLSTATE OK we send it back to the joining member s and the RESUME sending messages.

At step client finds initial members and determines coordinator of group . At step client sends a join with state transfer request to coordinator . At step coordinator initiates a flush quiets cluster and then sends a new view to everyone including client at step . However coordinator does not stop flush as it usually does for regular join requests. Client after it receives a first view sends a get state event to coordinator at step . After client receives the state client stops the flush and everyone proceeds as usual. At this point connect method invoked by a user returns.

The exemplary computer system includes a processing device a main memory e.g. read only memory ROM flash memory dynamic random access memory DRAM such as synchronous DRAM SDRAM or Rambus DRAM RDRAM etc. a static memory e.g. flash memory static random access memory SRAM etc. and a data storage device which communicate with each other via a bus .

Processing device represents one or more general purpose processing devices such as a microprocessor central processing unit or the like. More particularly the processing device may be complex instruction set computing CISC microprocessor reduced instruction set computing RISC microprocessor very long instruction word VLIW microprocessor or processor implementing other instruction sets or processors implementing a combination of instruction sets. Processing device may also be one or more special purpose processing devices such as an application specific integrated circuit ASIC a field programmable gate array FPGA a digital signal processor DSP network processor or the like. The processing device is configured to execute the processing logic for performing the operations and steps discussed herein.

The computer system may further include a network interface device . The computer system also may include a video display unit e.g. a liquid crystal display LCD or a cathode ray tube CRT an alphanumeric input device e.g. a keyboard a cursor control device e.g. a mouse and a signal generation device e.g. a speaker .

The data storage device may include a machine accessible storage medium on which is stored one or more sets of instructions e.g. software embodying any one or more of the methodologies or functions described herein. The software may also reside completely or at least partially within the main memory and or within the processing device during execution thereof by the computer system the main memory and the processing device also constituting machine accessible storage media. The software may further be transmitted or received over a network via the network interface device .

The machine accessible storage medium may also be used to store combining module . Combining module may also be stored in other sections of computer system such as static memory .

While the machine accessible storage medium is shown in an exemplary embodiment to be a single medium the term machine accessible storage medium should be taken to include a single medium or multiple media e.g. a centralized or distributed database and or associated caches and servers that store the one or more sets of instructions. The term machine accessible storage medium shall also be taken to include any medium that is capable of storing encoding or carrying a set of instructions for execution by the machine and that cause the machine to perform any one or more of the methodologies of the present invention. The term machine accessible storage medium shall accordingly be taken to include but not be limited to solid state memories optical and magnetic media and carrier wave signals.

It will be apparent however to one skilled in the art that the present invention may be practiced without these specific details. In some instances well known structures and devices are shown in block diagram form rather than in detail in order to avoid obscuring the present invention.

Some portions of the detailed descriptions which follow are presented in terms of algorithms and symbolic representations of operations on data bits within a computer memory. These algorithmic descriptions and representations are the means used by those skilled in the data processing arts to most effectively convey the substance of their work to others skilled in the art. An algorithm is here and generally conceived to be a self consistent sequence of steps leading to a desired result. The steps are those requiring physical manipulations of physical quantities. Usually though not necessarily these quantities take the form of electrical or magnetic signals capable of being stored transferred combined compared and otherwise manipulated. It has proven convenient at times principally for reasons of common usage to refer to these signals as bits values elements symbols characters terms numbers or the like.

It should be borne in mind however that all of these and similar terms are to be associated with the appropriate physical quantities and are merely convenient labels applied to these quantities. Unless specifically stated otherwise as apparent from the following discussion it is appreciated that throughout the description discussions utilizing terms such as processing or computing or calculating or determining or displaying or the like refer to the action and processes of a computer system or similar electronic computing device that manipulates and transforms data represented as physical electronic quantities within the computer system s registers and memories into other data similarly represented as physical quantities within the computer system memories or registers or other such information storage transmission or display devices.

The present invention also relates to apparatus for performing the operations herein. This apparatus may be specially constructed for the required purposes or it may comprise a general purpose computer selectively activated or reconfigured by a computer program stored in the computer. Such a computer program may be stored in a computer readable storage medium such as but is not limited to any type of disk including floppy disks optical disks CD ROMs and magnetic optical disks read only memories ROMs random access memories RAMs EPROMs EEPROMs magnetic or optical cards or any type of media suitable for storing electronic instructions and each coupled to a computer system bus.

The algorithms and displays presented herein are not inherently related to any particular computer or other apparatus. Various general purpose systems may be used with programs in accordance with the teachings herein or it may prove convenient to construct more specialized apparatus to perform the required method steps. The required structure for a variety of these systems will appear from the description below. In addition the present invention is not described with reference to any particular programming language. It will be appreciated that a variety of programming languages may be used to implement the teachings of the invention as described herein.

A machine accessible storage medium includes any mechanism for storing or transmitting information in a form readable by a machine e.g. a computer . For example a machine accessible storage medium includes read only memory ROM random access memory RAM magnetic disk storage media optical storage media flash memory devices electrical optical acoustical or other form of propagated signals e.g. carrier waves infrared signals digital signals etc. etc.

Thus a method and apparatus for configuring a flush protocol has been described. It is to be understood that the above description is intended to be illustrative and not restrictive. Many other embodiments will be apparent to those of skill in the art upon reading and understanding the above description. The scope of the invention should therefore be determined with reference to the appended claims along with the full scope of equivalents to which such claims are entitled.

