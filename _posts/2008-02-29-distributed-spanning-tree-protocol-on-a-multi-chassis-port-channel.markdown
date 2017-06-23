---

title: Distributed spanning tree protocol on a multi chassis port channel
abstract: In one embodiment, a technique for routing traffic in networks represented by logical topologies, such as Multi Chassis Port Channel (MCPC) or Multi Chassis Ether Channel (MCEC) topologies, is provided. By modifying a port priority vector (PPV) to include an additional “Switch ID” field that identifies a designated bridge ID or a local switch ID, depending on whether the corresponding port is used as an MCT, a routing protocol designed to avoid loops in routing paths, such as STP, may avoid blocking MCT ports.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08325630&OS=08325630&RS=08325630
owner: Cisco Technology, Inc.
number: 08325630
owner_city: San Jose
owner_country: US
publication_date: 20080229
---
Embodiments of the present disclosure generally relate to networking and more particularly to controlling the flow of network traffic.

A Multi Chassis Port Channel MCPC or Multi Chassis Ether Channel MCEC has two ends of a port channel termination on two different switches. These switches are commonly referred to as Aggregation Switches. Having multiple ends of a port channel terminate on different channels provides redundancy not only across link failure but also across a single switch failure.

In contrast in a regular Port Channel all links belonging to the Port Channel terminate on a single switch. The Port Channel is treated as a single logical link by Spanning Tree Protocol STP and any hardware operations like setting the port state or MAC flush Age are applied on all member links of the Port Channel. As such STP does not pose any issues on a regular Port Channel.

However operating STP on an MCPC complex presents some challenges as member links of the Port Channel are terminating on different switches. One of these challenges is that STP may block a port used to establish a multi channel trunk MCT between MCPC switches. If an MCT port is blocked the desirable redundancy offered by an MCPC topology may be lost.

One embodiment provides a method. The method generally includes maintaining a multi chassis port channel MCPC priority vector for a port of a switch of an MCPC complex wherein the MCPC priority vector includes a field whose value is determined based on whether or not the port is used to establish a multi chassis trunk MCT in the MCPC and performing spanning tree protocol operations based on the MCPC priority vector to determine whether or not to allow forwarding on the port.

One embodiment provides a switching device. The switching device generally includes a first port for establishing a multi chassis trunk MCT with another switching device for use in multi chassis port channel MCPC communications at least a second port for communicating with a device external to the MCPC logic for maintaining a multi chassis port channel MCPC priority vector for a port of a switch of an MCPC complex wherein the MCPC priority vector includes a field whose value is determined based on whether or not the port is used to establish a multi chassis trunk MCT in the MCPC and logic for performing spanning tree protocol operations based on the MCPC priority vector to determine whether or not to allow forwarding on the port.

One embodiment provides a switching device. The switching device generally includes at least a first port for establishing a multi chassis trunk MCT with another switching device for use in multi chassis port channel MCPC communications at least a second port for communicating with a device external to the MCPC means for maintaining a multi chassis port channel MCPC priority vector for a port of a switch of an MCPC complex wherein the MCPC priority vector includes a field whose value is determined based on whether or not the port is used to establish a multi chassis trunk MCT in the MCPC and means for performing spanning tree protocol operations based on the MCPC priority vector to determine whether or not to allow forwarding on the port.

Embodiments of the present disclosure provide techniques for routing traffic in networks represented by logical topologies such as Multi Chassis Port Channel MCPC or Multi Chassis Ether Channel MCEC topologies. By modifying a port priority vector PPV to include an additional Switch ID field that identifies a designated bridge ID or a local switch ID depending on whether the corresponding port is used as an MCT a routing protocol designed to avoid loops in routing paths such as STP may avoid blocking MCT ports.

As illustrated S and S may be connected via a multi chassis trunk to form an MCPC complex . Each switch in the MCPC complex may participate independently in data forwarding. Because S S and S all have a physical link to each of the switches S and S the MCPC provides redundant paths for traffic between S S and S.

As illustrated in logical MCPC ports MCPC and MCPC are formed between S and S respectively and MCPC . Although each MCPC port terminates on both MCPC switches each MCPC port appears as a single logical link for STP purposes.

In the illustrated example it is assumed that S owns the MCPC meaning that traffic on logical ports MCPC and MCPC will be routed through S. As such S may regularly synchronize MCPC parameters to S via the MCT connection. This regular synchronization may allow S to seamlessly take over control ownership of the MCPC in the event that S fails. Configuration parameters as well as runtime parameters associated with the MCPC may be synchronized to facilitate this switchover.

It may be desirable to run the STP protocol on the illustrated MCPC network topology for example to allow efficient routing and prevent undesirable loops. Unfortunately conventional application of the STP protocol to an MCPC may result in blocking of ports used to establish the MCT between the MCPC switches. The present disclosure presents a technique to allow STP computations while still maintaining MCT link forwarding.

In other words as illustrated in the techniques presented herein may allow STP operations to be run that result in the blocking of port P of S rather than the blocking of port P which would prevent MCT link forwarding. Thus the techniques presented herein may provide the advantages of both MCPC redundancy in the event of physical link and or switch failure and STP. Further blocking P would be insufficient to prevent loops as traffic could still be routed between S to S via the secondary MCPC connection with S.

Embodiments of the present disclosure may facilitate the running of STP on MCPC networks by utilizing a modified form of an STP port priority vector PPV referred to herein as an MCPC PPV. The MCPC PPV may include an additional field whose value may be determined based on whether or not the corresponding port is used for MCT. The format for a conventional PPV is as follows 

In an initialized state all ports may be blocked with ports transitioning to unblocked states that allow forwarding as STP is run and converges. The BPDU packet sent from S may include a proposal bit set to change a port that is currently blocking to forwarding for example to establish a path between S and S. Upon receiving the proposal before sending back an agreement to S S may synchronize port P.

For example as illustrated in S may send out a proposal message on P to allow forwarding on P . This proposal message may include modified port priority vectors MCPC PPVs for P and P as follows 

Internal logic running STP on the MCPC switches may determine the difference in the local switch ID and the Switch ID field is an indication that the corresponding port P is used in MCT. Conversely the internal logic may determine the same values of the local switch ID and the Switch ID field is an indication that the corresponding port P is not used in MCT. Based on these determination this logic may select the role for port P to be the root port and select the role for port P to be Alternate despite the higher root cost associated with port P relative to port P 2 versus 1 .

As illustrated in S may block the MCPC ports and send an agreement back to S. As illustrated in upon receiving the agreement from S S may send an agreement back to S accepting S s proposal to make its blocking port forwarding. Upon receiving the Agreement from S S unblocks its port making its port Forwarding. A final converged state is shown in with port P of S blocking and the MCPC ports unblocked. By blocking port P of S an unwanted loop through S that would have been created through the alternate MCPC connection between S and S is prevented.

As previously described the MCPC switches S and S may periodically synchronize parameters allowing S to take over control of the MCPC in the event of a switch failure to S or a link failure. Communications on the MCT established between S and S may be accomplished utilizing an internal protocol VSL INBAND with messages encapsulated with a header e.g. a DBUS header . For communications between the MCPC switches there is no need to strip off this header but for external communications the DBUS header may be stripped.

To maintain current spanning trees devices running STP periodically exchange BPDUs. In the case of MCPC topologies running STP BPDUs may need to be transmitted not only between the MCPC switches but also on the logical ports MCPC and MCPC . However to prevent confusion it may be desirable to transmit BPDUs for a logical port on the same physical link each time.

For example as illustrated in BPDUs for MCPC may always be sent on the physical link between S and S while BPDUs for MCPC may always be sent on the physical link between S and S. Using the same physical interface each time may prevent confusion for example by allowing a Packet Manager to get the same selection value such as a hash value on a port channel for BPDU Tx when querying an interface database. The same selection value may help guarantee the same port channel member will be selected.

STP logic on S may send a BPDU to MCPC using some type of packet manager API. This logic may query an interface database and set values of a DBUS header for the MCPC destined BPDU S as the source index and MCPC as the destination index . If these header values result in the selection of the port linking S to S the DBUS header may be stripped and the BDPU sent to S as shown in . If for some reason the port linking S and S is down however the BPDU may be forwarded out on the MCT port as illustrated in . S may receive the BPDU packet with the DBUS header strip the DBUS header and send the MCPC BDPU to S.

For BPDUs transmitted between the MCPC switches on the MCT internal source and destination indexes may be utilized in DBUS headers. For example STP logic on S may send a BPDU on its MCT port with a DBUS header having a source index e.g. S SUP used to indicate the BPDU came on the local MCT port. The DBUS header may also include a destination index e.g. S SUP to ensure the message will be routed correctly on S. To allow this approach of BPDU transport over the MCT Destination indexes may be unique across the MCPC switches.

When the MCPC receives a BPDU on a switch that does not have ownership the BPDU may be relayed to the peer switch that does have ownership with the source index preserved. As illustrated in still assuming S owns MCPC a BPDU received via an alternate link e.g. received on port P of S should eventually be delivered to S DBUS BPDU as having been received on MCPC. In this case when the BPDU is received on P of S port logic may realize that MCPC is owned by S and forward the BPDU on the MCT. The BPDU may be forwarded with a DBUS header indicating MCPC as the Source index and S SUP as the destination index. As a result upon receiving this BPDU logic on S may forward it to STP logic as being received on MCPC.

As illustrated above in in the event of a link failure the MCPC may transmit BPDUs utilizing the alternate physical link allowing the MCPC to continue to operate. In the event of a switch failure the MCPC may also continue to operate with the peer switch taking over ownership.

As illustrated in once switch S fails S will take over ownership and begin sending BPDUs for both MCPC and MCPC. The STP parameters are updated to reflect this change in ownership. These updated STP parameters for S are shown in table B with S designated as the root and the SwitchID fields of priority vectors for MCPC MCPC are updated to reflect this. In some cases the root cost may also need to be updated depending on the topology. In the illustrated example however the root cost for MCPC and MCPC remains the same as S has a direct link to root node S.

By allowing STP to run on MCPC topologies embodiments of the present disclosure provide the advantages of both technologies. For example the MCPC allows redundant switching paths between devices while running STP provides optimum path selection while avoiding loops.

While the foregoing is directed to embodiments of the present disclosure other and further embodiments of the disclosure may be devised without departing from the basic scope thereof and the scope thereof is determined by the claims that follow.

