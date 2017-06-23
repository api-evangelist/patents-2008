---

title: Information synchronisation
abstract: A technique for synchronizing instances of sets of information stored on different devices may involve comparison of update digests of the different instances and comparisons of version data of information within the different instances of the sets to determine what information may need to be updated and in which of the instances.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09116972&OS=09116972&RS=09116972
owner: Sage Technologies Limited
number: 09116972
owner_city: Dublin
owner_country: IE
publication_date: 20081010
---
This application claims priority from Great Britain Application Serial No. 0817022.7 filed Sep. 17 2008 the entire disclosure of which is incorporated herein by reference.

This invention relates to a method and apparatus for synchronising information across a set of computer applications.

Information used in a computer application can take many forms with an example being financial or accounting data. The information may be sales order information invoice information stock information or any of the other types of financial information that is used.

A problem is encountered when objects that are replicated across several data stores are modified. The ideal situation is that any modification is instantaneously reflected across all replicas such that the information is up to date everywhere. Due to objective constraints such as connection reliability and latency resilience or the desire to keep objects highly available it is not practicable and in most cases not necessary to keep the whole network of applications up to date all the time.

It is therefore considered that the applications interact and exchange information with the aim of achieving a consistent underlying content. This interaction is called synchronisation.

An existing method for synchronising data uses vector clock synchronisation which uses an algorithm for generating a partial ordering of events in a distributed system and detecting causality violations. Interprocess messages contain the state of the sending process s logical clock. A vector clock of a system of N processes is an array of N logical clocks one per process a local copy of which is kept in each process with the following rules for clock updates.

Each time a process experiences an internal event it increments its own logical clock in the vector by one.

Each time a process prepares to send a message it sends its entire vector along with the message being sent.

Each time a process receives a message it compares the vector clock included in the message with its own vector clock. If the vector clock included in the message is strictly greater than the vector clock of the process the process accepts the new state contained in the message and replaces its vector clock by the vector clock contained in the message. If the vector clock included in the message is strictly smaller than the vector clock of the process the process ignores the message. If the two vector clocks are not comparable each one has an entry that it strictly greater than the corresponding entry in the other one the receiving process signals a conflict and applies a conflict handling rule to update its state.

The vector clock is attached to each object in a data store. Synchronisation is achieved by using the algorithm outlined above.

It is an object of the present invention to provide a more efficient method of synchronising data sets.

According to the present invention there is provided an apparatus and method as set forth in the appended claims. Other features of the invention will be apparent from the dependent claims and the description which follows.

According to a first aspect of the present invention there is provided a method of synchronising at least first and second instances of an information set comprising a plurality of entries wherein said first and second instances are located on different nodes of a system the method comprising 

Preferably an existing node value and current logical clock value pair of an entry is deleted and replaced with a new node value and current logical clock value pair when said entry is changed.

A timestamp value may be attached to each data entry when said entry is changed in addition to the node value and current logical clock value pair.

Preferably the synchronisation is performed in a bi directional manner for example from the first instance to the second instance and then from the second instance to the first instance.

Preferably synchronisation is performed for one information set at a time. This feature is advantageous over performing synchronisation one data entry at a time.

The node value and current logical clock value pair and or the digest may be carried by a data feed or syndication feed such as an RSS feed or an Atom feed.

The nodes may be endpoints that carry one instance of the information set. The node values may be URLs.

Two digests may be provided for each synchronisation event which digests may be floor and ceiling digests corresponding to a state of a node before a modification event and after a modification event respectively

The invention extends to a synchronisation device operable to perform the method of the above aspect.

According to another aspect of the invention there is provided a computing system comprising a plurality of nodes wherein each node incorporates an instance of an information set the computing system being operable to synchronise the instances of the information set and comprising at least one synchronisation logic means operable to

The synchronisation logic means may comprise a synchronisation endpoint which may be an interface or service for each node or for each instance of the information set.

The synchronisation logic means may comprise one or more synchronisation engines. The synchronisation engines may be operable to drive exchanges of messages between synchronisation endpoints. The synchronisation engines and synchronisation endpoints may reside on different computers. Alternatively a synchronisation engine may reside on the same computer as a synchronisation endpoint.

Each synchronisation endpoint is preferably operable to perform the attaching and digest generation for its given node.

Preferably the synchronisation engines are operable to communicate with endpoints to perform the synchronisation function.

The nodes may be computer applications running on one computer or may be applications running on different computers.

According to another aspect of the invention there is provided a computer program product comprising instructions which when run on a computer are operable to implement a method of synchronising at least first and second instances of an information set comprising a plurality of entries wherein said first and second instances are located on different nodes of a computer system the method comprising 

In order to address the problems relating to synchronisation referred to above various attributes for a synchronisation scheme have been identified.

Given sufficient interactions between applications and in the absence of modifications a synchronised state between data stores should be achieved.

The scheme should handle conflicts between the states of objects in an algorithmic and rigorous manner.

A scheme has been developed for providing synchronisation of information sets that takes into account the objectives set out above.

A synchronisation protocol is based on vector clock synchronisation the well know technique referred to above and used by several synchronisation replication systems P2P networks replicated file systems etc.

Vector clocks provide an elegant solution to the problem of maintaining several copies of a given object in synchronisation and detecting conflicts.

Assuming that a given object O is replicated on several nodes N1 N2 . . . in a system of connected computing applications the vector clocks are constructed as follows 

O may have different vector clocks at different nodes. The goal of the synchronisation system is to bring O in synchronisation across nodes. When O is fully synchronised its vector clock is the same on all nodes.

By comparing the vectors clocks of O on two nodes the synchronisation algorithm can decide if the versions can be brought in synchronisation and how or if there is a conflict. The following table explains how this comparison works VOj stands for the vector clock of O at node j 

In the description of the vector clock algorithm above the tick is incremented every time an object is modified. This is actually not a requirement and the algorithm works just as well if the tick is incremented every time a synchronisation pass is run rather than every time an object is modified. So the nodes can use either strategy to manage their clocks.

To be precise and to get the same algorithm for the two strategies the clock must actually be managed as follows 

With this convention the tick can be interpreted as the first value that has not been synchronised rather than the last value that has been synchronised when the synchronisation pass is run. This may not be the most natural convention but it makes the algorithm work regardless of whether the tick is incremented at modification time or at synchronisation time.

The algorithm uses a simple mechanism based on priorities and timestamps to resolve conflicts. The idea is the following 

The conflict resolution can be optionally implemented by adding a priority value to the vector clock pairs. The vector clock is now a list of triplets Ni Ti Pi where Ni is the node id Ti is Ni s tick when O was last modified at Ni and Pi is Ni s conflict priority. Also the synchronisation metadata should contain the last modification timestamp of each object. So the synchronisation metadata for object O is the combination of its extended vector clock list of triplets and its last modification timestamp.

The conflict resolution algorithm works as described in the following table the timestamp is reduced to hh mm to keep table clean 

Usually sets of objects tables rather than individual objects records are synchronised. So the scheme uses a variant of the algorithm in which the nodes track the vector clocks at the set level rather than at the object level.

At the object level the scheme s algorithm only tracks the last modification a single Ni Ti pair last modification timestamp.

This is less expensive and easier to implement because the synchronisation metadata can be stored directly into the data table only 3 additional columns for node id tick and timestamp are needed and often the timestamp column will already be there or it can be stored in a separate syncdata table with a simple 1 to 1 join to the data table.

The set level vector clock is called digest in the scheme s terminology. The scheme s digest is actually an extended vector clock made of triplets node id tick conflict priority .

This variant assumes that synchronisation is performed one set at a time rather than one object at a time although it is shown later that it can also be used to propagate changes on individual objects under certain conditions .

The digest of a node can also be interpreted as a summary of the synchronisation states of all the objects of the set at that node. For example if the digest for set S is N1 6 1 N2 7 2 N3 9 3 at node N1 this means that N1 s S set has been synchronised with N2 s S set at tick 7 N1 s state takes into account all changes made on N2 with tick 

The scheme uses two passes to synchronise two nodes Nj and Nk one pass to propagate Nj s changes to Nk and a second pass in the other direction to propagate Nk s changes to Nj.

The following table describes how the algorithm selects objects from N1 when synchronising from N1 to N2 and then selects objects from N2 when synchronising in the other direction.

Conflict detection is slightly more complex than in the original algorithm see 1.1 because the individual objects do not hold a complete vector clock they only hold one pair. But conflicts can still be detected reliably because 4 pieces of information are at hand when an object is synchronised the Nj Tj pairs of the object on both sides but also the vector clocks of the sets on both sides. Conflict detection works as follows 

Scenarios are given below that would lead to the cases above and that justify the results given in the table 

The previous section describes a synchronisation algorithm in the abstract. It does not put many constraints on the actual architecture in which this algorithm will be deployed. For example it does not say whether the synchronisation passes are run from one of the nodes or externally to the nodes. If run from one of the nodes it does not say whether all passes are run from the same node or whether passes may be run from different nodes. It does not say either how the data is accessed direct connection to the databases classical C S architecture service interface SOAP or REST Representational state transfer or others

The algorithm could be deployed in a variety of ways external internal process single multiple processes CS SOA service oriented architecture etc . In this second section an example of a possible deployment is given.

A specific implementation of the scheme is described below which is the specification of a REST protocol for the applicant s applications.

It is necessary to adapt the terminology used in the previous section to terminology used for this implementation example. The following table gives the mapping 

It would have been possible to use the implementation example terminology in the previous section. This was not done to stress the point that the algorithm is independent from the architecture so that it can be reviewed and discussed independently from the architecture.

The mapping between node and endpoint in the previous table needs additional explanation. When the algorithm was described the nature of a node was kept vague a node identifies a location and for example a node could manage several sets.

On the implementation side a slightly restrictive approach is taken an endpoint represents one set at one location one entity in a given service provider rather than the location itself the service provider . So an endpoint is actually an entity URL in a given service provider. This more restrictive interpretation of node does not have any impact on the algorithm if the algorithm works for a node that manages several sets it also works for the simpler case where a node manages a single set.

The following table gives examples of endpoints As the table shows endpoint URLs may include filters. This feature should be used with care. To be on the safe side filters should always create a partition of the entity for example one endpoint per country so that the sets behind two endpoints of the same provider do not overlap. If the filters overlap conflict detection may generate false positives.

In the implemented synchronisation architecture the endpoints are the entry doors into the applications they are the URLs that a synchronisation engine uses to read and write from the application.

The processes that exchange data between applications to bring them in synchronisation are run by components called synchronisation engines .

The implemented architecture is very flexible on the engine side. It supports centralised scenarios in which a central engine drives all the interactions as well as decentralised scenarios where several engines cooperate. This point is developed in 2.9 below.

A synchronisation engine interacts with an application through the endpoints URLs that the application exposes. The engine uses only three types of messages to communicate with the applications as described in the following table where Atom refers to an XML language used for web feeds 

Generally shows how components interact with each other in a synchronisation pass. The process involves 4 steps numbered 1 to 4. All steps are initiated by the synchronisation engine and this figure shows the most general case where the source application the target application the engine and the event logger are distinct components that may eventually reside on different computers.

At 2 the engine sends the target digest to the source. The source uses the two digests its own and the target one to select the resources that need to be transferred to the target it uses the algorithm described in 1.5 . The source returns the delta feed to the engine.

At 3 the engine sends the delta feed to the target. The delta feed is a batch of create update delete instructions that the target provider executes to bring its data store in synchronisation. The delta feed also contains the two digests that have been used to select resources on the source side. The target uses these digests to detect and resolve conflicts it uses the algorithm described in 1.6 . When the batch has been fully processed the target updates its digest to reflect the fact that the delta has been applied. The target returns diagnostic information about the success failure of the operations that have been submitted.

At 4 the engine sends the diagnostics that it just received to the event manager. The event manager logs them and alerts users if configured to do so.

The delta is a feed which is broken in pages using the implementation example paging protocol . So the engine repeats steps 2 3 and 4 on every page of the feed. At step 3 the target digest is only updated at the end of the last page this operation could have been done as a separate step 5 to clearly isolate the loop in steps 2 3 and 4 but then the engine would make an extra roundtrip to the target .

The deployment can be simplified by embedding the engine into one of the endpoints. In this case the communications between the engine and its embedding endpoint can be short circuited they are not required to go through HTTP and URLs . For example if the engine is run from the source application and if the source also handles the diagnostics becomes the set up shown in in which the numerals relate to the same functions mentioned above in relation to .

In this simplified architecture the source is not a service provider any more it has become an application that consumes services exposed by another application.

If bi directional synchronisation is needed between the two applications we can still use the same simplified architecture. To synchronise in the other direction shows the architecture in which again the numerals relate to the same functions mentioned above in relation to .

The simplification exercise above shows that implementation example synchronisation can accommodate both a suite scenario where a central engine coordinates synchronisation passes between services and a disconnected laptop scenario where each laptop runs its own synchronisation engine.

But the architecture allows many more variants because all the interactions go through URLs and the location of the components is not of great significance all that is required is that the engine can access the other component s URLs . Flexibility is particularly important on the error reporting side and nothing prevents the engine from sending the diagnoses to more than one diagnostic endpoint. In the context of an application suite this is usually not required because the suite has a central event management facility but when the applications do not belong to a suite the implementation example allows the system to be configured to report errors in one of the applications or in the other or in both or sometimes in one sometimes in the other depending on the direction for example . This decision should be dictated by product considerations and the implementation example architecture should be able to accommodate the various needs of product integration scenarios.

The engine described above works in catch up mode. Synchronisation is done in passes which may be run by a scheduler or launched manually. The synchronisation passes use the following logic 

In a number of scenarios it is important to propagate changes as soon as possible instead of having to wait for a synchronisation pass. This immediate mode involves a slightly different process 

The implementation example synchronisation protocol is designed to handle the two modes under a common protocol. Of course the source implementation will be different in the two modes in catch up mode the source needs to provide an entry point to query the delta in immediate mode the source needs to be able to detect changes but the protocol is designed so that the target side can handle both modes in a uniform way the target does not need to be aware of which mode is used .

Also the implementation example synchronisation protocol is designed to support a mix of the two modes. This feature is important because the immediate mode is challenging. For example one of the applications may be offline or the target application may be down when the source tries to propagate changes. This can be solved by introducing a queue to guarantee delivery but this has drawbacks queue needs to remain active if source application is closed queue may end up wasting lots of resources especially is a target is never reachable etc. . An alternative is to consider that the immediate mode is only a best effort to propagate changes and to use the catch up mode to ensure that systems will be brought back in synchronisation periodically even if some immediate synchronisation requests have been lost.

In immediate mode the architecture is typically as shown in which shows a typical configuration for immediate synchronisation. The source application pushes its changes to a target application. The main difference with the catch up mode is the elimination of a roundtrip to query the target digest. This configuration is more efficient to propagate changes than the catch up configuration depicted in but a real system would probably combine both configurations so that it can revert to catch up mode when the immediate mode fails.

The main difference with the catch up mode is that the engine does not read the target digest any more this would involve an extra roundtrip it only pushes the delta to the target.

The implementation example protocol handles the immediate mode and the mix of modes by using a rich selfdescribing delta message. The implementation example delta message contains 

The process is to include two digests that delimit the delta change in the feed. These two digests are called the floor and ceiling digests. They are set as follows 

With this refinement the target knows precisely what the delta contains. The target checks if the tick intervals defined by the floor and ceiling are contiguous to its own tick values the target digest . If the intervals are contiguous the target can update its digest. Otherwise if there is a gap between the tick interval defined by floor digest and the target digest the target knows that at least one immediate synchronisation has been missed and it does not update its digest. The next catch up synchronisation will close the gap.

The rationale for having two digests in the message is to make the feeds more self describing . They do not contain only the changes they also contain information about the two digests that bracket the changes. This is useful in immediate mode because it allows the target to check if the range of changes sent by the source is contiguous with the changes that have already been incorporated on the target. If the range of changes is contiguous the target can incorporate them and update its digest. If they are not this happens if a previous immediate synchronisation message has not been delivered to the target the target should discard the request.

The implementation protocol is designed so that the target side can handle the catch up mode and the immediate mode with the same logic. This is why the same message feed is used for both modes with two digests in the message. This make the protocol more robust for example in the unlikely scenario where the target node is restored from an old backup between the time the source queried its digest and the time the source sends its changes .

The scheme described above allows for an advantageous reduction in the data that is appended to each record or object because only a last node tick pair is added with the remainder of the clock vector being sent with the digest. The scheme allows the same efficiency and conflict detection as existing schemes but with much reduced overhead.

Attention is directed to all papers and documents which are filed concurrently with or previous to this specification in connection with this application and which are open to public inspection with this specification and the contents of all such papers and documents are incorporated herein by reference.

All of the features disclosed in this specification including any accompanying claims abstract and drawings and or all of the steps of any method or process so disclosed may be combined in any combination except combinations where at least some of such features and or steps are mutually exclusive.

Each feature disclosed in this specification including any accompanying claims abstract and drawings may be replaced by alternative features serving the same equivalent or similar purpose unless expressly stated otherwise. Thus unless expressly stated otherwise each feature disclosed is one example only of a generic series of equivalent or similar features.

The invention is not restricted to the details of the foregoing embodiment s . The invention extends to any novel one or any novel combination of the features disclosed in this specification including any accompanying claims abstract and drawings or to any novel one or any novel combination of the steps of any method or process so disclosed.

