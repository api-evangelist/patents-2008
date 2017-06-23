---

title: Tracking of and communication with mobile terminals using a battery-powered wireless network infrastructure
abstract: There is provided a method of reducing energy consumption of network infrastructure nodes in a wireless network, the method comprising: (a) turning a transmitter and a receiver of the network infrastructure node to a power-off state; b) powering-on the transmitter of the network infrastructure node for a limited transmission time frame; c) during the transmission time frame, transmitting a beacon message comprising an identifier of the network infrastructure node, channel characteristics of the network infrastructure node and a powering-on schedule of the receiver of the network infrastructure node, for allowing mobile terminal nodes in the network to communicate with the network infrastructure node, where the mobile terminal nodes are almost continuously in a power-on state; d) powering-on the receiver of the network infrastructure node during a limited reception time frame in accordance with the schedule, for enabling the receiver to receive messages transmitted by the mobile terminal nodes in the network if required; e) repeating steps a) to d) periodically. There is further provided a battery-powered network infrastructure node which reduces energy consumption. There is further provided a battery-powered wireless network with an energy management for network infrastructure node. There is further provided a method of increasing probability of detection of rapidly moving clusters of mobile terminal nodes in a wireless network.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09351242&OS=09351242&RS=09351242
owner: 
number: 09351242
owner_city: 
owner_country: 
publication_date: 20080901
---
The present patent application claims the benefits of priority of Canadian Patent Application No. 2 559 471 filed on Aug. 31 2007 at the Canadian Intellectual Property Office and entitled Underground communication network system for personal tracking and HVAC control .

The present invention generally relates to the field of wireless telecommunication networks. The invention more particularly concerns Tracking of and Communication with Mobile Terminals using a Battery Powered Wireless Network Infrastructure.

With the advent of the Internet and the ever increasing miniaturization and integration of electronic circuits new possibilities have begun to emerge in the field of data communication networks.

Several applications such as industrial automation and monitoring localization of personal and assets and defense and security management have specific requirements that cannot be met with wired networks or existing wireless networks.

In order to provide a solution for these types of applications significant new research has been conducted in the past ten years to develop new and more efficient wireless network systems and protocols.

This research has resulted in the appearance of a plethora of proprietary and non proprietary wireless networking technologies. Some such as WLAN IEEE 802.11 WiMAX IEEE 802.16 Bluetooth IEEE 802.15.1 ZigBee IEEE 802.15 and the upcoming SP100 protocol are standard non proprietary wireless networking protocols. Standard networking technologies generally involve trade offs between numerous competing issues scalability topology energy consumption range frequency etc. . They are therefore difficult to adequately tailor to the specific needs of particular applications. This invention in contrast does not operate on a standard and can be tailored with a high degree of specificity to particular applications. This invention is also different from other proprietary network protocols such as the TSMP from Dust Networks and the SensiNet from Sensicast two other non standard wireless networking protocols.

Beacon based networks have been implemented in some cases. While these networks have facilitated some useful advances they either only operate in star configurations or consume too much energy to be battery powered. Many applications mandate a mesh network that is highly scalable in terms of the maximum number of hops and node density for which the network remains reliable. Many applications also require a network connection time in the order of seconds. Mesh network techniques that rely on central synchronization cannot meet these demands.

Ad hoc communication in mesh networks usually implies local allocation of communication resources without a central host. Low energy consumption must prevail in allocating these resources.

Real time tracking of mobile terminals in underground or confined environments e.g. underground mines navy vessels is challenging because 1 Mobile terminals cannot receive satellite or cellular signals from Wide Area Networks WAN e.g. GPS does not work 2 Deploying Local Area Network LAN infrastructure is prohibitively expensive operationally impractical and or unreliable because a RF signal propagation is non line of sight and confined to tunnels corridors or rooms with waveguide constraints b Power outlets are scarce and installing additional power wiring connectors and adapters is a tedious undertaking c Many sites are in remote areas and or in developing countries where skilled labor for installation and maintenance of telecom networks are in short supply d Wiring is prone to damage.

From the foregoing it appears that there is a need for a novel wireless network technology which obviates the above mentioned drawbacks.

As a first aspect of the invention there is provided a method of reducing energy consumption of network infrastructure nodes in a wireless network the method comprising 

b powering on the transmitter of the network infrastructure node for a limited transmission time frame 

c during the transmission time frame transmitting a beacon message comprising an identifier of the network infrastructure node channel characteristics of the network infrastructure node and a powering on schedule of the receiver of the network infrastructure node for allowing mobile terminal nodes in the network to communicate with the network infrastructure node where the mobile terminal nodes are almost continuously in a power on state 

d powering on the receiver of the network infrastructure node during a limited reception time frame in accordance with the schedule for enabling the receiver to receive messages transmitted by the mobile terminal nodes in the network if required 

As a further aspect of the invention there is provided a network infrastructure node in a wireless network comprising 

a processing unit configured to turn a transmitter and a receiver of the network infrastructure node to a power off state to power on the transmitter of the network infrastructure node for a limited transmission time frame to transmit during the transmission time frame a beacon message comprising an identifier of the network infrastructure node channel characteristics of the network infrastructure node and a powering on schedule of the receiver of the network infrastructure node for allowing mobile terminal nodes in the network to communicate with the network infrastructure node and to power on the receiver of the network infrastructure node during a limited reception time frame in accordance with the schedule for enabling the receiver to receive messages transmitted by mobile terminal nodes in the network if required.

As another aspect of the invention there is provided a wireless network comprising a plurality of mobile terminal nodes and a plurality of network infrastructure nodes where network infrastructure nodes are configured to be continuously in a power off state except during prescheduled reception and transmission time frames and where mobile terminal nodes are configured to be almost continuously in a power on state where the mobile terminal nodes and network infrastructure nodes exchange messages therebetween in order for each mobile terminal node to be connected to one network infrastructure node in the network.

As another aspect of the invention there is provided a computer readable medium containing instructions for controlling at least one processor to perform a method of reducing energy consumption in network infrastructure node in a wireless network the method comprising 

b powering on the transmitter of the network infrastructure node for a limited transmission time frame 

c during the transmission time frame transmitting a beacon message comprising an identifier of the network infrastructure node channel characteristics of the network infrastructure node and a powering on schedule of the receiver of the network infrastructure node for allowing mobile terminal nodes in the network to communicate with the network infrastructure node where the mobile terminal nodes are almost continuously in a power on state 

d powering on the receiver of the network infrastructure node during a limited reception time frame in accordance with the schedule for enabling the receiver to receive messages transmitted by the mobile terminal nodes in the network if required 

As a further aspect of the invention there is provided a method of increasing probability of detection of rapidly moving clusters of mobile terminal nodes in a wireless network the method comprising 

wherein the plurality of personal mobile terminal nodes connect to a nearest vehicle hybrid infrastructure mobile node among the at least one vehicle hybrid infrastructure mobile node and each one of the at least one vehicle hybrid infrastructure mobile node connect to a nearest network infrastructure node among the at least one network infrastructure node 

exchanging data messages between the nearest vehicle hybrid infrastructure mobile node and the nearest network infrastructure node where the messages comprise data in association with the plurality of personal mobile terminal nodes.

Novel methods devices and systems for Tracking of and Communication with Mobile Terminals using a Battery Powered Wireless Network Infrastructure will be described hereinafter. Although the invention is described in terms of specific illustrative embodiments it is to be understood that the embodiments described herein are by way of example only and that the scope of the invention is not intended to be limited thereby.

Being directed to a network technology comprising different aspects these different aspects shall now be described separately.

The system and method of the present invention are most preferably embodied in a wireless network system and are generally most advantageously applied to networks requiring low energy consumption such as sensor networks. However the system and method of the present invention may be applied to other fields such as but not limited to personal vehicle and asset tracking and mobile communications in underground mines navy vessels and military persistent surveillance field deployments the present invention is not so limited.

The network system of the present invention generally consists of a plurality of substantially structurally identical wireless network infrastructure nodes and mobile terminal nodes. Identical nodes enable more efficient network deployment because any node can be installed at any location without affecting network functioning. Moreover malfunctioning or damaged nodes can be replaced easily and on short notice.

In one embodiment of the invention communication occurs between a network infrastructure node and a mobile terminal node. Each network infrastructure node has its own time and frequency synchronization.

A major distinction of the present invention with respect to the prior art is that a node is not provided with multiple antennas and transceivers. Each node of the present invention is provided with a single antenna and a single transceiver. The ability to be synchronized with more than one clock and with more than one frequency hopping sequence is provided by the proprietary software embedded in each wireless node.

Compared to previous art all the roles in this embodiment have routing capabilities regardless of how frequently they transmit beacons. The role of each node in the network will adapt according to the local radio frequency RF environment node density throughput requirements energy consumption and required routing. Beacon transmission is globally reduced to a minimum in this embodiment of a beacon based mesh network.

The process is enabled by the transmission of beacons by the network infrastructure nodes. The mobile terminal nodes receive the different beacons and connect to the closest network infrastructure node.

As a first aspect of the invention there is provided a method of energy management of network infrastructure nodes in a wireless network.

According to the preferred embodiment the wireless network consists of an ad hoc battery powered mesh network mounted in an underground area such as mines or in a confined area such as navy vessels. Since physical access to such areas is most of the time very difficult and cable installation is sometimes impossible there is a need for a wireless network that would be battery powered and that would minimize human intervention. The human intervention is minimized if the network is self healing and if the power battery of the network infrastructure nodes can last the longest time possible.

The first purpose of the conceived wireless network in accordance with the preferred embodiment is to track personnel and machinery inside underground mines.

Network infrastructure nodes are mounted in different zones of the underground mine or navy vessel in order to track presence of personal and machinery. Personal and machinery are tagged with battery powered or machine powered mobile terminal nodes which continuously communicate with the nearest network infrastructure node. The process of communication between the mobile terminal node and network infrastructure node is a novel aspect of the present invention since it is conceived to minimize energy consumption of the network infrastructure node.

With reference to the communication protocol between mobile terminal nodes and network infrastructure nodes can be described as follows 

The NETWORK INFRASTRUCTURE NODE IS IN DEEP SLEEP MODE at EXCEPT WHEN EXECUTING THE FOLLOWING PROCESSES at and following 

NEXT TIME SLOT WHEN THE RECEIVER IS ON FOR RANDOM ACCESS TO INITIATE CONNECTION UNIQUE FOR EACH NETWORK INFRASTRUCTURE NODE 

ON DEMAND ALLOCATION OF TIME SLOTS TO SPECIFIC MOBILE TERMINAL NODES FOR BI DIRECTIONAL COMMUNICATIONS I.E. CSMA IS NOT USED ONCE A CONNECTION IS ESTABLISHED 

A beacon is sent once per frame in a pre defined time slot. A frame is a collection of 50 pre defined time slots each lasting 13 ms. The time the beacon is transmitted defines the time synchronization for that network infrastructure node.

The frequency hopping random seed is unique per network infrastructure node. It defines the channel that will be used for communication for each time slot.

2 PERMANENT CONNECTIONS WITH NEIGHBORING NETWORK INFRASTRUCTURE NODES FOR BACKHAUL COMMUNICATIONS TO CENTRAL SERVER USING PRIOR ART LOW POWER STAR OR MESH NETWORKING TECHNOLOGIES 

3 RECEPTION OF 1 CONNECTION AND 2 REQUEST FOR COMMUNICATION TIMESLOTS MESSAGES FROM MOBILE TERMINAL NODES ON RANDOM ACCESS CHANNEL at and 

The mobile terminal node requests for time slot when it needs to send a message to the network infrastructure node.

4 ON DEMAND CONNECTION WITH MOBILE TERMINAL NODES FOR TWO WAY COMMUNICATIONS E.G. PERIODIC HEARTBEAT SENSOR DATA ACKNOWLEDGMENT CONFIGURATION PARAMETERS 

When the network infrastructure node receives a connection attempt from a mobile terminal node at it registers the node at . If the node is of type MOBILE WITH TRACKING at it will guarantee the transmission of the tracking message to the server at . From then on the network infrastructure node will allocate specific time slots for communication as requested by the mobile terminal node or needed by it.

When the mobile terminal node requests for communication time slots at the network infrastructure node sends an allocation message in another pre defined time slot which defines the communication time slots at in which the mobile terminal node may send information at .

When the network infrastructure node wants to send a message it sends an allocation message which specifies the time slot of communication.

5 EVENT DRIVEN TRANSMISSION OF MOBILE TERMINAL NODE CONNECT DISCONNECT MESSAGE BASED ON PRESENCE ABSENCE OF PERIODIC MOBILE TERMINAL NODE HEARTBEAT TO CENTRAL SERVER

The mobile terminal node sends a heartbeat every minute to the network infrastructure node. If 3 are not received in a row at and it is considered not connected. At that point a disconnection message is sent to the server at with a time stamp.

Integrated Hardware Platform Option 1 All processes mentioned hereinabove related to the communications with network infrastructure nodes are implemented using the same microcontroller and transceiver. Power is supplied by a primary battery or an energy harvesting mechanism.

Integrated Hardware Platform Option 2 All processes mentioned hereinabove related to communications with mobile terminal nodes are implemented on one microcontroller transceiver pair and all processes related to backhaul communications to a central server are implemented on a 2nd microcontroller transceiver pair. Communications between processes on two microcontrollers is done via SPI UART or RS 232. Power is supplied by a primary battery or an energy harvesting mechanism.

Use 8 different beacon frequencies that are common for all network infrastructure nodes. These frequencies are connection frequencies. The mobile terminal node listens to one of them at a time for a duration that is equal to the period of these connection frequencies. For instance the period could be is 19 frames with 50 time slots of 13 ms 12.350 seconds.

2 USES THE BEACON TO EVALUATE THE RSSI TOF OR OTHER RF LINK PARAMETERS WITH NETWORK INFRASTRUCTURE NODES WHICH HAVE TRACKING ON

The mobile terminal node measures the RSSI of the network infrastructure nodes around it. If one of them has not been evaluated recently and its RSSI is stronger than a threshold or is the strongest it will decide to connection to it for further evaluation.

3 ATTEMPTS TO DETERMINE THE NEAREST NETWORK INFRASTRUCTURE NODE BY CONSIDERING INSTANTANEOUS AND OR HISTORICAL RF LINK DATA WHICH HAS TRACKING ON AND WHOSE RF LINK PARAMETERS MEET THE RF SIGNAL STRENGTH OR TIME OF FLIGHT REQUIREMENTS SPECIFIED IN ITS BEACON at 

The mobile terminal node will make further evaluation of the network infrastructure node while monitoring the other network infrastructure nodes around it. If the RSSI signature meets the requirements of a network infrastructure node that is the closest it will decide to connect to it at and .

4 TRANSMITS 1 CONNECTION OR 2 REQUEST FOR COMMUNICATION MESSAGES ON THE RANDOM ACCESS CHANNEL OF THE SELECTED NEAREST NETWORK INFRASTRUCTURE NODE PREFERABLY OR ANY OTHER NETWORK INFRASTRUCTURE NODE WITH 

While it is connected to it it will monitor its RSSI signature in order to determine if it is going out of range of the coverage area which defined by the Tracking Node Type. If it does it will attempt to send a disconnection message. Then it will go back to step 1.

5 ESTABLISHES TWO WAY CONNECTION WITH THE SELECTED NEAREST NETWORK INFRASTRUCTURE NODE PREFERABLY at OR ANY OTHER NETWORK INFRASTRUCTURE NODE AND EXCHANGES PERIODIC HEARTBEAT at 

Definition of how communication are requested is done in the infrastructure section. Here s a repetition 

The mobile requests for time slot when it needs to send a message to the network infrastructure node at .

When the mobile terminal node requests for communication time slots the network infrastructure node sends an allocation message in another pre defined time slot which defines the communication time slots in which the mobile terminal node may send information.

When the network infrastructure node wants to send a message it sends an allocation message which specifies the time slot of communication.

6 NETWORK INFRASTRUCTURE NODE IS RESPONSIBLE FOR THE GUARANTEED DELIVERY OF THE MOBILE TERMINAL NODE MESSAGES TO THE CENTRAL SERVER

Rechargeable Battery options Lithium ion battery recharged frequently as part of normal operations e.g. miner cap lamp first responder mobile terminal 

Hardware Platform Option 1 All processes mentioned hereinabove related to the mobile terminal nodes are implemented using the same microcontroller and transceiver. Power is supplied by a rechargeable battery line power a primary battery or an energy harvesting mechanism.

From a higher level abstract the activities of the mobile terminal node and network infrastructure node can be illustrated as follow 

1. Network infrastructure node in deep sleep mode periodically wakes up to send a synchronization message every X seconds 

2. Mobile terminal node is able to determine the nearest network infrastructure node by listening to the synchronization messages of network infrastructure nodes 

a. In the preferred embodiment based on Frequency Hopping Spread Spectrum FHSS the mobile terminal node measures the Received Signal Strength RSSI by listening to the synchronization message.

b. In an alternative embodiment based on Chirp Spread Spectrum CSS the mobile terminal node measure Round Trip Time Of Flight RTTOF by listening to the synchronization message.

3. Mobile terminal node listens until it captures the synchronization message required to initiate bi directional communications with the network infrastructure node 

a. In the preferred embodiment based on FHSS the synchronization message has the random seed of the communication channels i.e. frequencies and time slots . Its time of reception gives the asynchronous time base of the network infrastructure node.

4. In order to maximize its sleep time the network infrastructure node allocates specific time slots for communications with the mobile terminal node. One time slot is always allocated for tracking messages. This time slot will be referred to as the random access time slot 

a. In the preferred embodiment based on FHSS the network infrastructure node allocates both frequency channels and time slots for communications

5. After interpreting the RSSI and or RTTOF measurements the mobile terminal node decides whether to send a tracking message to the network infrastructure node in the random access time slot.

a. In the preferred embodiment the interpretation is made with a log of previous RSSI measurements which can be made at different frequencies or channels from surrounding network infrastructure nodes. The tracking message contains the time of occurrence of tracking the network address of the mobile terminal node and qualitative RSSI information.

6. Network infrastructure node forwards the tracking message to the battery powered wireless mesh network router for transmission to a central server.

As a further aspect of the invention there is provided a method to increase probability of detection of rapidly moving clusters of mobile terminal nodes in a battery powered mesh network.

Hybrid infrastructure mobile terminal node on vehicle to track clusters of mobile terminal nodes moving at high speed 

NEXT TIME SLOT WHEN THE RECEIVER IS ON FOR RANDOM ACCESS TO INITIATE CONNECTION UNIQUE FOR EACH NETWORK INFRASTRUCTURE NODE 

ON DEMAND ALLOCATION OF TIME SLOTS TO SPECIFIC MOBILE TERMINAL NODES FOR BI DIRECTIONAL COMMUNICATIONS

3B ON DEMAND CONNECTION WITH MOBILE TERMINAL NODES FOR TWO WAY COMMUNICATIONS E.G. PERIODIC HEARTBEAT SENSOR DATA ACKNOWLEDGMENT CONFIGURATION PARAMETERS 

4B EVENT DRIVEN TRANSMISSION OF MOBILE TERMINAL NODE CONNECT DISCONNECT MESSAGE BASED ON PRESENCE ABSENCE OF PERIODIC MOBILE TERMINAL NODE HEARTBEAT TO CENTRAL SERVER VIA WIRED PORT E.G. SPI. RS 232 TO MOBILE TERMINAL NODE PART PORTION OF HYBRID DEVICE

2B USES THE BEACON TO EVALUATE THE RSSI TOF OR OTHER RF LINK PARAMETERS WITH NETWORK INFRASTRUCTURE NODES WHICH HAVE BACKHAUL NETWORKING AND TRACKING ON

3B SELECTS THE NEAREST NETWORK INFRASTRUCTURE NODE WHICH HAS BACKHAUL NETWORKING AND TRACKING ON AND WHOSE RF LINK PARAMETERS MEET THE MINIMUM RF THRESHOLDS SPECIFIED IN ITS BEACON 

4B RECEPTION OF MESSAGES FROM NETWORK INFRASTRUCTURE NODE PART PORTION OF HYBRID DEVICE VIA WIRED PORT E.G. SPI. RS 232 

5B TRANSMITS MESSAGES ON THE RANDOM ACCESS CHANNEL OF THE SELECTED NEAREST NETWORK INFRASTRUCTURE NODE PREFERABLY OR ANY OTHER NODENETWORK INFRASTRUCTURE NODE WITH 

6B ESTABLISHES TWO WAY CONNECTION WITH THE SELECTED NEAREST NETWORK INFRASTRUCTURE NODE PREFERABLY OR ANY OTHER NETWORK INFRASTRUCTURE NODE AND EXCHANGES PERIODIC HEARTBEAT 

Hardware Platform Option 1 All processes in Flow Chart 3 are implemented using the same microcontroller and transceiver. Power is supplied by a rechargeable battery line power a primary battery or an energy harvesting mechanism.

Hardware Platform Option 2 All processes related to the mobile terminal node part portion are implemented on the same hardware platform as a normal mobile terminal node and all processes related to the network infrastructure node part portion are implemented on the same hardware platform as a normal network infrastructure node. Both hardware platforms are inter connected by a wired SPI UART or RS 232 port. Power is supplied by a rechargeable battery line power a primary battery or an energy harvesting mechanism.

While illustrative and presently preferred embodiments of the invention have been described in detail hereinabove it is to be understood that the inventive concepts may be otherwise variously embodied and employed and that the appended claims are intended to be construed to include such variations except insofar as limited by the prior art.

