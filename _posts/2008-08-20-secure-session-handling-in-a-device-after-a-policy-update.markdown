---

title: Secure session handling in a device after a policy update
abstract: A device may update at least one old policy to a new policy, obtain data exchanged between endpoints of an ongoing communication session, apply the new policy to the data and not applying the at least one old policy to the data when a start of the communication session has occurred after the updating, and apply the new policy and the at least one old policy to the data when the start of the communication session has occurred before the updating.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08490149&OS=08490149&RS=08490149
owner: Juniper Networks, Inc.
number: 08490149
owner_city: Sunnyvale
owner_country: US
publication_date: 20080820
---
When a network device receives a packet the network device typically applies a security policy to the packet. Applying the security policy entails matching a known set of signatures e.g. an attack signature to a portion of the packet and performing a specific action e.g. drop the packet if the portion matches one or more of the signatures.

According to one aspect a method may include updating at least one old policy to a new policy obtaining data exchanged between endpoints of an ongoing communication session applying the new policy to the data and not applying the at least one old policy to the data when a start of the communication session has occurred after the updating and applying the new policy and the at least one old policy to the data when the start of the communication session has occurred before the updating.

According to another aspect a device may include a controller and a service module. The controller may generate new policies and distribute the new policies to service modules. The service module may receive the new policies from the controller obtain data in a communication session between two nodes in a network and apply the new policies and old policies to the data when a start of the communication session has occurred before the new policies are received.

According to yet another aspect a device may include means for generating new policies means for updating old policies based on the new policies or deleting the old policies means for obtaining data from packets in a communication session between two endpoints in a network means for applying the new policies and the old policies to the data when a start of the communication session has occurred before the old policies are updated and means for applying the new policies and not the old policies to the data when the start of the communication session has occurred after the old policies are updated.

The following detailed description refers to the accompanying drawings. The same reference numbers in different drawings may identify the same or similar elements. As used herein the term policy may refer to a set of signatures and actions that a device may perform when data matches one or more of the signatures. A signature may include a set of attributes one of which may be a pattern. The term packet as used herein may refer to a packet a datagram or a cell a fragment of a packet a datagram or a cell or other types of data.

As described below a network device may securely handle sessions after a policy update. is a block diagram of exemplary sessions through herein collectively referred to as sessions and individually as session that are administered by a network device not shown . The term session as used herein may include an interactive communication e.g. a dialog between endpoints in a network. The network device may administer session by applying security policies to packets that are exchanged between the endpoints of session when the packets pass through the network device.

For session the network device may apply both old policies and new policies . The network device may begin to apply new policies to session however when certain conditions are met and not at an arbitrary point in time.

Applying both old policies and new policies starting at time t may be preferable to switching from old policies to new policies at time t. If the network device switches from old policies to new policies at time t the network device may be unable to complete the application of old policies to block and consequently may fail to detect signatures that should be detected by applying old policies to entire block and all subsequent blocks that arrive after e.g. .

Applying both old policies and new policies to session may also be preferable to applying only old policies to session . By failing to apply new policies as soon as possible the network device may be unable to detect in packets that are exchanged in session new signatures that are specified in new policies .

By applying both old policies and new policies to session the network device may increase the chance of detecting a potential security threat.

As shown in network may include devices through N individually referred to herein as a device . Device may include for example a router a switch a gateway a server a work station a personal computer etc. Although device may be implemented as any computer like or server like device in the following description device will be described in terms of a router switch.

Controller may include one or more components for managing routes and or types of information that may require centralized processing. For example controller may manage routes e.g. may accept or disseminate routes to other devices in accordance with routing signaling protocols may receive and process statistics related to packets and or may process packet samples from other components of device e.g. from line interfaces .

In another example controller may convert a set of source patterns into a set of compiled patterns e.g. patterns that can be efficiently used by another component to perform pattern matching such as deterministic finite state automata DFA non deterministic finite state automata NFA etc.

Line interface may include one or more components for receiving packets from devices in network and for transmitting the packets to other devices in network . In addition line interface may forward packets classify packets redirect packets to other components in device manage a table of packet statistics and or sample packets.

Service module may include hardware software or a combination of hardware and software for rendering a particular service for a received packet. In processing the packet service module may select one or more portions of the packet and perform a pattern match to detect one or more features e.g. a virus . After processing the packet service module may drop the packet or direct the packet to another of service modules or one of line interfaces . Examples of service module may include an anti virus service module a firewall service module an intrusion detection service module an encryption decryption service module and or other types of service modules.

Switch fabric may include one or more switches for conveying packets from one of line interfaces and or service modules to another of line interfaces and or service modules .

Processor may include a processor a microprocessor an Application Specific Integrated Circuit ASIC a Field Programmable Gate Array FPGA and or other processing logic capable of controlling component . In some implementations processor may include hardware such as a co processor for matching data to patterns.

Memory may include content addressable memory CAM static memory such as read only memory ROM and or dynamic memory such as random access memory RAM or onboard cache for storing data e.g. patterns and machine readable instructions. Memory may also include storage devices such as a hard disc and or flash memory as well as other types of storage devices. Depending on the implementation portions of memory may be directly addressable via processor or components in processor e.g. a co processor for matching patterns to data .

Communication interface may include any transceiver like mechanism that enables component to communicate with other devices and or systems. Communication data path may provide an interface through which components of component and or device can communicate with one another.

Policy manager may include one or more components e.g. hardware or software component for managing policies. As used herein the term policy may refer to a set of signatures and actions that are associated with the set of signatures. When data e.g. part of a packet matches one or more of the signatures device may perform the actions.

Policy manager may interact with a user or another device in network to transfer create edit and or remove policies. In some implementations policy manager may invoke another component e.g. pattern compiler and or distribute information e.g. distribute compiled patterns to other components e.g. service modules in device 

Pattern compiler may include one or more components for converting e.g. compiling a set of patterns one format to that in another format. In one implementation pattern compiler may convert patterns in signatures of a policy into a compiled pattern database a pattern et . In some implementations the compiled pattern may be encrypted or formatted in a specific manner. The compiled pattern database may be loaded into a pattern matching engine PME for the PME to match data to patterns in the pattern database.

In one implementation pattern compiler may accept one or more pattern files as input. shows an exemplary pattern file . As shown pattern file may include one or more groups of patterns one of which is illustrated as group . As further shown group may include group header and one or more pattern fields . Depending in implementation pattern file may include additional fewer or different headers fields and or types of information that pertain to patterns.

Group header may include information for identifying a group of patterns such as a group name a group identifier etc. Pattern field may include information such as an identifier for identifying a pattern flags for indicating how pattern field is to be compiled e.g. whether the compiled pattern is to be encrypted a name of the pattern and a pattern. The pattern may include a sequence of symbols or an expression e.g. a regular expression .

Given pattern file pattern compiler may convert e.g. compile each of patterns in one format to a database of patterns. For example in one implementation pattern compiler may convert a pattern that is described by a series of symbols to a deterministic finite state automaton DFA . In other implementations pattern compiler may convert a pattern into other types of information such as a non deterministic finite state automaton NFA .

As shown in DFA may include a start state a state and a pattern detected state . Depending on the implementation DFA may include fewer additional or different states.

Given DFA a pattern matching engine may use DFA to detect the pattern ab in data. Using DFA to detect the pattern ab will be described below in greater detail with reference to a pattern matching engine.

PMS client may include hardware and or software components that are associated with sending pattern match requests to PMS receiving a result of matching patterns from PMS and processing the result. In one implementation PMS client may perform these functions by providing support for procedures e.g. threads programs subroutines methods scripts etc. that may be invoked via a set of pattern match application programming interfaces APIs .

PMS may include one or more components for queuing pattern match requests from PMS clients relaying the pattern match requests to PME receiving responses to the pattern match requests from PME and distributing the responses to one or more PMS clients .

Pattern database may include one or more sets of compiled patterns e.g. DFA . Presence of one of the compiled patterns in data may indicate that the data poses a security threat to device and or network . For example assume that pattern database includes a DFA that represents the pattern 10111000101111110000. Presence of that particular pattern in data e.g. data string 11110101110001011111100000 may indicate that the data carries a computer virus.

PME may include one or more components for receiving pattern match requests that are relayed by PMS from PMS client matching data to a set of patterns and providing results of matching the data to the pattern. PME may forward the results to PMS which may relay the results to PMS client .

In matching data to patterns PME may use DFAs that are provided in pattern database . For example assume that data includes xyzwabm and pattern database includes DFA that is illustrated in . Furthermore assume that PME can enter any of states through e.g. PME may enter a state by setting specific values to internal variables .

In accordance with DFA PME may begin to match data xyzwabm to pattern ab in start state . Each time PME scans one of first four symbols xyzw in data xyzwabm PME may stay in state as indicated by state transition arc . When PME scans letter a in xyzwabm however PME may transition to state Si as indicated by state transition arc . In state S when PME scans letter b in xyzwabm PME may transition to pattern detected state via state transition arc . If PME does not scan letter b in state S PME may follow state transition are and return to state 

Returning to policy database may include one or more policies. shows an exemplary policy database . As shown policy database may include old policies and new policies e.g. policies after a policy update . In old policies and new policies are depicted as including old policy and new policy .

As further shown each of policies e.g. old policies and new policies may include a policy identifier ID field a patterns field and an actions field . Depending on the implementation each policy in policy database may include fewer additional or different fields than those illustrated in .

Policy ID field may include a value that identifies the policy. Patterns field may include a list of patterns to which PME may match data before device can perform a set of actions that are associated with the policy. Actions field may identify a list of actions that device may perform when data matches patterns that are listed in patterns field .

For example assuming old policy is in effect if a string data e.g. a portion of a packet matches patterns P P or P device may perform actions A e.g. drop the packet that contains P and A e.g. sample the packet . In another example assuming new policy is in effect if data matches patterns Q P or P device may perform action A.

Process may begin at block where policy database may be updated and the time of policy update may be stored block . In one implementation policy manager may modify or create one or more new policies compile new patterns that may be associated with the new policies and distribute the new policies and or patterns to one or more service modules . When service module receives new policies patterns service module may update pattern database and policy database . In addition service module may store the time when service module updates the patterns policies.

The updated patterns and policies may be loaded block . PMS client and or PME may load the updated patterns and or policies into a dynamic memory that may be accessible PME . With the updated patterns in the dynamic memory PME may match data e.g. a portion of a packet to the updated patterns.

Matching data to the patterns may be concluded block . When the policy database is updated PMS client may have been matching via PMS and PME data that match patterns in pattern database . PMS client may conclude matching the data to the patterns.

Returning to starting time of a communication session to which the data belongs may be determined block . For example assume that to apply a policy PMS client obtains data from a packet that belongs to a communication session. In such an instance PMS client may determine the starting time of the communication session.

At block a determination may be made as to whether the policy update has occurred before the start of the communication session block . In one implementation PMS client may compare the time of policy update to the starting time of the communication session. If the policy update has occurred after the start of communication session process may proceed to block .

At block old policies and new policies may be applied block . For example PMS client may search old policies and new policies in policy database for a list of policies whose patterns field includes the list of patterns that match the data see block . For each policy whose patterns field includes the list of patterns PMS client may perform actions that are listed in actions field .

In the above if more than one policy whose patterns field includes the list of patterns is found and if actions that are specified in different policies are inconsistent PMS client may perform the action that may be considered more extreme or restrictive than other actions. For example an action under one policy may specify device to terminate a communication session and another action may specify device to log data that is exchanged during the communication session. In such an instance device may terminate the communication session.

Returning to block if the policy update has occurred before the start of communication session process may proceed to block where the new policies may be applied block . For example PMS client may search new policies for a list of policies whose patterns field includes the list of patterns that match the data see block . For each policy whose patterns field includes the list of patterns PMS client may perform actions that are listed in actions field .

Patterns may be unloaded or deleted block . Eventually all communication sessions that began before the policy update and packet processing associated with the communication session may be terminated. In such an instance patterns that are associated with the old policies and not with the new policies may be unloaded from the dynamic memory as the patterns may no longer be used. In addition the old policies may be unloaded or deleted from the dynamic memory.

In the above blocks through can be understood within context of a timeline that spans lifetime of a communication session. Assume that old policies are updated at t tas depicted in and . In addition assume that PMS client is receiving data and enforcing old policies just before the old policies are updated.

From the perspective of PMS client at this point PMS client may continue to match patterns until the pattern matching for the data is completed. In this is illustrated as matching portion to patterns and in as block .

Once PMS client concludes matching patterns for portion PMS client may determine whether the session to which portion belongs has started after the policy update e.g. session or before the policy update e.g. session . PMS client may determine this by comparing the starting time of the communication session to which the data belongs to the time of policy update see blocks and . If the communication session has started after the policy update PMS client may apply new policies block . Otherwise PMS client may apply both new and old policies block .

In the above after the policies are updated PMS client may complete the application of the old policies to portion before PMS client applies both the new and old policies. Thus there is a gap in time between the time of policy update and the time when the new policies are applied. In the gap may be determined as t t.

If pattern database includes DFAs as compiled patterns for PME completing the application of the old policies for portion may be equivalent to arriving at an end state of a DFA. This is illustrated in which depicts session and a DFA that corresponds to a pattern in pattern database . Assume that the old policies have been updated before t t. For PME completing pattern matches for block may be equivalent to traversing states in DFA until PME arrives at an end state where a pattern match is terminated e.g. a matching pattern is found or not found . At a state within a DFA e.g. starting state PMS client may begin to apply both the old policies and new policies.

In the above applying both the old policies and the new policies may be preferable to immediately switching from old policies to new policies at the time of update. If device switches from the old policies to the new policies without completing interrelated pattern matches e.g. pattern matches for portion device may be unable to detect patterns that should be detected by applying old policies to entire block .

Applying both the old policies and the new policies to session may also be preferable to applying only the old policies which may be out of date at the time when the old policies are updated.

By applying both the old policies and the new policies device may increase the security of network and device 

The foregoing description of implementations provides illustration but is not intended to be exhaustive or to limit the implementations to the precise form disclosed. Modifications and variations are possible in light of the above teachings or may be acquired from practice of the teachings.

For example while series of blocks have been described with regard to exemplary processes illustrated in the order of the blocks may be modified in other implementations. In addition non dependent blocks may represent acts that can be performed in parallel to other blocks.

It will be apparent that aspects described herein may be implemented in many different forms of software firmware and hardware in the implementations illustrated in the figures. The actual software code or specialized control hardware used to implement aspects does not limit the invention. Thus the operation and behavior of the aspects were described without reference to the specific software code it being understood that software and control hardware can be designed to implement the aspects based on the description herein.

Even though particular combinations of features are recited in the claims and or disclosed in the specification these combinations are not intended to limit the invention. In fact many of these features may be combined in ways not specifically recited in the claims and or disclosed in the specification.

No element act or instruction used in the present application should be construed as critical or essential to the implementations described herein unless explicitly described as such. Also as used herein the article a is intended to include one or more items. Where one item is intended the term one or similar language is used. Further the phrase based on is intended to mean based at least in part on unless explicitly stated otherwise.

