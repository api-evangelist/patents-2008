---

title: Shared transport
abstract: A method and apparatus for processing message is described. In one embodiment, messages are received over a plurality of channels from a plurality of applications in a virtual machine. An identifier is coupled to each message. The identifier refers to the application originating the corresponding message. A shared transport is formed and associated with the channels. The messages are processed with the shared transport with the identifier.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08799397&OS=08799397&RS=08799397
owner: Red Hat, Inc.
number: 08799397
owner_city: Raleigh
owner_country: US
publication_date: 20080522
---
Embodiments of the present invention relate to group communication and more specifically to parallel processing of messages.

Group communication protocol designed for multicast communication may be used to communicate messages between endpoints forming a group. Communication endpoints can be processes or objects or any entity that can send and receive messages to from a group.

Messages from different senders are conventionally processed in a First In First Out FIFO order in a single queue for incoming messages by one thread. The messages are processed sequentially in the order they are received. A bottleneck may thus be formed since every message has to wait for its turn to be processed accordingly.

One solution is to use a multiplexer to run multiple building blocks over the same channel thereby reducing the number of channels and threads and thus minimizing memory consumption. However the use of a multiplexer requires different semantics for each channel.

Described herein is a method and apparatus for processing messages. In one embodiment messages are received over a plurality of channels from a plurality of applications in a virtual machine. An identifier is coupled to each message. The identifier refers to the application originating the corresponding message. A shared transport is formed and associated with the channels. The messages are processed with the shared transport with the identifier.

In the following description numerous details are set forth. It will be apparent however to one skilled in the art that the present invention may be practiced without these specific details. In some instances well known structures and devices are shown in block diagram form rather than in detail in order to avoid obscuring the present invention.

Some portions of the detailed descriptions which follow are presented in terms of algorithms and symbolic representations of operations on data bits within a computer memory. These algorithmic descriptions and representations are the means used by those skilled in the data processing arts to most effectively convey the substance of their work to others skilled in the art. An algorithm is here and generally conceived to be a self consistent sequence of steps leading to a desired result. The steps are those requiring physical manipulations of physical quantities. Usually though not necessarily these quantities take the form of electrical or magnetic signals capable of being stored transferred combined compared and otherwise manipulated. It has proven convenient at times principally for reasons of common usage to refer to these signals as bits values elements symbols characters terms numbers or the like.

It should be borne in mind however that all of these and similar terms are to be associated with the appropriate physical quantities and are merely convenient labels applied to these quantities. Unless specifically stated otherwise as apparent from the following discussion it is appreciated that throughout the description discussions utilizing terms such as processing or computing or calculating or determining or displaying or the like refer to the action and processes of a computer system or similar electronic computing device that manipulates and transforms data represented as physical electronic quantities within the computer system s registers and memories into other data similarly represented as physical quantities within the computer system memories or registers or other such information storage transmission or display devices.

The present invention also relates to apparatus for performing the operations herein. This apparatus may be specially constructed for the required purposes or it may comprise a general purpose computer selectively activated or reconfigured by a computer program stored in the computer. Such a computer program may be stored in a computer readable storage medium such as but is not limited to any type of disk including floppy disks optical disks CD ROMs and magnetic optical disks read only memories ROMs random access memories RAMs EPROMs EEPROMs magnetic or optical cards or any type of media suitable for storing electronic instructions and each coupled to a computer system bus.

The algorithms and displays presented herein are not inherently related to any particular computer or other apparatus. Various general purpose systems may be used with programs in accordance with the teachings herein or it may prove convenient to construct more specialized apparatus to perform the required method steps. The required structure for a variety of these systems will appear from the description below. In addition the present invention is not described with reference to any particular programming language. It will be appreciated that a variety of programming languages may be used to implement the teachings of the invention as described herein.

A machine accessible storage medium includes any mechanism for storing or transmitting information in a form readable by a machine e.g. a computer . For example a machine accessible storage medium includes read only memory ROM random access memory RAM magnetic disk storage media optical storage media flash memory devices electrical optical acoustical or other form of propagated signals e.g. carrier waves infrared signals digital signals etc. etc.

The group communication architecture may comprise three parts 1 a channel layer used by application programmers to build reliable group communication applications 2 building blocks which are layered on top of channel and provide a higher abstraction level and 3 a protocol stack which implements the properties specified for a given channel.

Channel is connected to protocol stack . Whenever an application sends a message channel passes it on to protocol stack comprising several protocols . The topmost protocol processes the message and the passes it on to the protocol below it. Thus the message is handed from protocol to protocol until the bottom protocol puts it on the network . The same happens in the reverse direction the bottom transport protocol listens for messages on network . When a message is received it will be handed up protocol stack until it reaches channel . Channel stores the message in a queue until application consumes it.

When an application connects to a channel protocol stack will be started and when it disconnects protocol stack will be stopped. When the channel is closed the stack will be destroyed releasing its resources.

To join a group and send messages a process has to create a channel and connect to it using the group name all channels with the same name form a group . The channel is the handle to the group. While connected a member may send and receive messages to from all other group members. The client leaves a group by disconnecting from the channel. A channel can be reused clients can connect to it again after having disconnected. However a channel may allow only one client to be connected at a time. If multiple groups are to be joined multiple channels can be created and connected to. A client signals that it no longer wants to use a channel by closing it. After this operation the channel may not be used any longer.

Each channel has a unique address. Channels always know who the other members are in the same group a list of member addresses can be retrieved from any channel. This list is called a view. A process can select an address from this list and send a unicast message to it also to itself or it may send a multicast message to all members of the current view. Whenever a process joins or leaves a group or when a crashed process has been detected a new view is sent to all remaining group members. When a member process is suspected of having crashed a suspicion message is received by all non faulty members. Thus channels receive regular messages view messages and suspicion messages. A client may choose to turn reception of views and suspicions on off on a channel basis.

Channels may be similar to BSD sockets messages are stored in a channel until a client removes the next one pull principle . When no message is currently available a client is blocked until the next available message has been received.

A channel may be implemented over a number of alternatives for group transport. Therefore a channel is an abstract class and concrete implementations are derived from it e.g. a channel implementation using its own protocol stack or others using existing group transports. Applications only deal with the abstract channel class and the actual implementation can be chosen at startup time.

The properties for a channel may be specified in a colon delimited string format. When creating a channel a protocol stack will be created according to these properties. All messages will pass through this stack ensuring the quality of service specified by the properties string for a given channel.

Channels are simple and primitive. They offer the bare functionality of group communication and have been designed after the simple model of BSD sockets which are widely used and well understood. The reason is that an application can make use of just this small subset without having to include a whole set of sophisticated classes that it may not even need. Also a somewhat minimalistic interface is simple to understand a client needs to know about 12 methods to be able to create and use a channel and oftentimes will only use 3 4 methods frequently .

Channels provide asynchronous message sending reception somewhat similar to UDP. A message sent is essentially put on the network and the send method will return immediately. Conceptual requests or responses to previous requests are received in undefined order and the application has to take care of matching responses with requests.

Also an application can retrieve messages from a channel pull style . Also channels offer push style message reception. Pull style message reception often needs another thread of execution or some form of event loop in which a channel is periodically polled for messages.

The presently described group architecture offers building blocks that provide more sophisticated APIs on top of a Channel. Building blocks either create and use channels internally or require an existing channel to be specified when creating a building block. Applications communicate directly with the building block rather than the channel. Building blocks are intended to save the application programmer from having to write tedious and recurring code e.g. request response correlation.

Protocol stack as illustrated in includes the following protocols CAUSAL GMS MERGE FRAG UDP . All messages sent and received over the channel have to pass through the protocol stack. Every layer may modify reorder pass or drop a message or add a header to a message. A fragmentation layer might break up a message into several smaller messages adding a header with an id to each fragment and re assemble the fragments on the receiver s side.

The composition of the protocol stack i.e. its layers is determined by the creator of the channel a property string defines the layers to be used and the parameters for each layer . This string might be interpreted differently by each channel implementation. It is used to create the stack depending on the protocol names given in the property.

Knowledge about the protocol stack is not necessary when only using channels in an application. However when an application wishes to ignore the default properties for a protocol stack and configure their own stack then knowledge about what the individual layers are supposed to do is needed. Although it is syntactically possible to stack any layer on top of each other they all have the same interface this wouldn t make sense semantically in most cases.

Data is sent between members in the form of messages. A message can be sent by a member to a single member or to all members of the group of which the channel is an endpoint. An example of a structure of a message is illustrated in .

A list of headers can be attached to a message. Anything that should not be in the payload can be attached to message as a header. Methods putHeader getHeader and removeHeader of message can be used to manipulate headers .

The destination address may include the address of the receiver. If null the message will be sent to all current group members.

The source address may include the address of a sender. It can be left null and will be filled in by the transport protocol e.g. UDP before the message is put on the network .

The payload may include the actual data as a byte buffer . The message class contains convenience methods to set a serializable object and to retrieve it again using serialization to convert the object to from a byte buffer.

The message may be similar to an IP packet and consists of the payload a byte buffer and the addresses of the sender and receiver as addresses . Any message put on the network can be routed to its destination receiver address and replies can be returned to the sender s address.

A message usually does not need to fill in the sender s address when sending a message this is done automatically by the protocol stack before a message is put on the network. However there may be cases when the sender of a message wants to give an address different from its own so that for example a response should be returned to some other member.

The destination address receiver can be an Address denoting the address of a member determined e.g. from a message received previously or it can be null which means that the message will be sent to all members of the group. A typical multicast message sending string Hello to all members would look like this 

If those transports happen to be the same all 4 channels use UDP for example then only 1 shared instance of UDP is created. That transport instance is created and started only once when the first channel is created and is deleted when the last channel is closed.

Each channel created over a shared transport has to join a different cluster. An exception will be thrown if a channel sharing a transport tries to connect to a cluster to which another channel over the same transport is already connected.

When there are three channels C connected to cluster C connected to cluster and C connected to cluster sending messages over the same shared transport the cluster name with which the channel connected is used to multiplex messages over the shared transport a header with the cluster name cluster is added when C sends a message.

When a message with a header of cluster is received by the shared transport it is used to demultiplex the message and dispatch it to the right channel C in this example for processing.

To use shared transports a property singleton name is added to the transport configuration of transport . All channels with the same singleton name share the same transport.

FLUSH protocol is used to flush out old messages before installing a new view. STATE ensures that state is correctly transferred from an existing member usually the coordinator to a new member. GMS is a membership protocol that is responsible for joining leaving members and installing new views. NAKACK is a protocol that ensures a message reliability and b FIFO. Message reliability guarantees that a message will be received. If not the receiver s will request retransmission. FIFO guarantees that all messages from sender P will be received in the order P sent them. FD is a protocol for failure detection based on heartbeats and are you alive messages in a ring form between members . It generates notification if a member fails. MERGE2 is a protocol for merging subgroups back into one group. It kicks in after a cluster partition. PING is a protocol that uses IP multicast by default to find initial members. Once found the current coordinator can be determined and a unicast JOIN request will be sent to it in order to join the cluster. PROXY PROTOCOL is a protocol that adds an identifier to the message and identifies the application originating the message and the transport . In one embodiment a property singleton name is added to the transport configuration of transport . All channels with the same singleton name share the same transport.

In another embodiment the shared transport includes a transport protocol for sending and receiving messages to and from a network coupled to the virtual machine. The shared transport protocol enables to share a default thread pool and an out of bound thread pool. The thread pools send the messages up the transport protocol stack to a corresponding channel of a channel layer a building block layered on top of the channel layer and an application programming interface layered on top of the building block.

The exemplary computer system includes a processing device a main memory e.g. read only memory ROM flash memory dynamic random access memory DRAM such as synchronous DRAM SDRAM or Rambus DRAM RDRAM etc. a static memory e.g. flash memory static random access memory SRAM etc. and a data storage device which communicate with each other via a bus .

Processing device represents one or more general purpose processing devices such as a microprocessor central processing unit or the like. More particularly the processing device may be complex instruction set computing CISC microprocessor reduced instruction set computing RISC microprocessor very long instruction word VLIW microprocessor or processor implementing other instruction sets or processors implementing a combination of instruction sets. Processing device may also be one or more special purpose processing devices such as an application specific integrated circuit ASIC a field programmable gate array FPGA a digital signal processor DSP network processor or the like. The processing device is configured to execute the processing logic for performing the operations and steps discussed herein.

The computer system may further include a network interface device . The computer system also may include a video display unit e.g. a liquid crystal display LCD or a cathode ray tube CRT an alphanumeric input device e.g. a keyboard a cursor control device e.g. a mouse and a signal generation device e.g. a speaker .

The data storage device may include a machine accessible storage medium on which is stored one or more sets of instructions e.g. software embodying any one or more of the methodologies or functions described herein. The software may also reside completely or at least partially within the main memory and or within the processing device during execution thereof by the computer system the main memory and the processing device also constituting machine accessible storage media. The software may further be transmitted or received over a network via the network interface device .

The machine accessible storage medium may also be used to store shared transport protocol configurations . Shared transport protocol configurations may also be stored in other sections of computer system such as static memory .

While the machine accessible storage medium is shown in an exemplary embodiment to be a single medium the term machine accessible storage medium should be taken to include a single medium or multiple media e.g. a centralized or distributed database and or associated caches and servers that store the one or more sets of instructions. The term machine accessible storage medium shall also be taken to include any medium that is capable of storing encoding or carrying a set of instructions for execution by the machine and that cause the machine to perform any one or more of the methodologies of the present invention. The term machine accessible storage medium shall accordingly be taken to include but not be limited to solid state memories optical and magnetic media and carrier wave signals.

It is to be understood that the above description is intended to be illustrative and not restrictive. Many other embodiments will be apparent to those of skill in the art upon reading and understanding the above description. The scope of the invention should therefore be determined with reference to the appended claims along with the full scope of equivalents to which such claims are entitled.

