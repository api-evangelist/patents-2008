---

title: Methods and systems for consistently replicating data
abstract: Techniques for maintaining consistent replicas of data are disclosed. By way of example, a method for managing copies of objects within caches, in a system including multiple caches, includes the following steps. Consistent copies of objects are maintained within the caches. A home cache for each object is maintained, wherein the home cache maintains information identifying other caches likely containing a copy of the object. In response to a request to update an object, the home cache for the object is contacted to identify other caches which might have copies of the object.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09317432&OS=09317432&RS=09317432
owner: International Business Machines Corporation
number: 09317432
owner_city: Armonk
owner_country: US
publication_date: 20080109
---
The present application relates to data processing systems and more particularly to techniques for consistently replicating data in such data processing systems.

In data processing systems such as distributed computer systems wherein nodes comprise multiple memories problems occur when it is desirable to access the same data by independent nodes. Multiple copies may be replicated across different nodes. However problems occur when updates to the objects occur. Maintaining consistent replicas of the objects can be difficult.

By way of example only and not intended to be a comprehensive list some types of distributed computing system that may experience this type of problem include Web based systems distributed memory multiprocessors distributed file systems and distributed databases. Those ordinarily skilled in the art associated with each of these exemplary systems will readily appreciate how maintaining consistent replicas of objects can be difficult.

By way of example in one aspect of the invention a method for managing copies of objects within caches in a system comprised of multiple caches comprises the following steps. Consistent copies of objects are maintained within the caches. A home cache for each object is maintained wherein the home cache maintains information identifying other caches likely containing a copy of the object. In response to a request to update an object the home cache for the object is contacted to identify other caches which might have copies of the object.

The method may further comprise the steps of maintaining information on one of accesses and updates to an object and using said information to select a home cache for the object.

Also the method may also further comprise the step of selecting a cache n as a home cache for the object wherein said maintained information indicates that cache n frequently accesses or updates said object.

Further the method may further comprise the step of in response to said home cache identifying a cache n as likely containing a copy of said object contacting cache n to one of invalidate and update its copy of said object.

Still further the step of maintaining consistent copies of objects within the caches may further comprise using a plurality of methods for maintaining consistent copies of objects wherein different methods incur different trade offs between a level of consistency and a level of overhead. The plurality of methods may comprise at least one of a strong consistency method an invalidation messages without waiting for acknowledgements method and an expiration times method.

These and other objects features and advantages of the present invention will become apparent from the following detailed description of illustrative embodiments thereof which is to be read in connection with the accompanying drawings.

Illustrative embodiments of the present invention will be described below in the context of a distributed data processing system however it is to be understood that principles of the invention are generally applicable to any system in which it would be desirable to maintain consistent replicas of data.

The term cache as used herein broadly refers to a memory or storage area within a computing system. A cache can include all or part of the main memory of a computing node. A cache can also include all or part of a persistent storage device such as a disk.

The term object as used herein broadly refers to any entity which can be stored in a cache. By way of example only and not intended to be a comprehensive list some types of such entities include Web pages whole database tables parts of database tables files and database query results.

The cache may optionally have an application programming interface API which allows application programs to explicitly control its content. In each cache resides on a separate node i.e. node node node . Several variations are possible within the spirit and scope of the invention. For example multiple caches may exist on a same node. Different caches could be associated with different processes which may or may not be on the same node etc.

Nodes and or caches may optionally exchange heart beat messages for maintaining availability information. Heart beat messages are sent at periodic intervals. If a node n fails to receive an expected heart beat message from node n at an appropriate time it can conclude that there is a system failure n may be down. Alternatively there could be a network failure preventing n from properly sending messages to n. After detecting a failure the system can take appropriate recovery actions. A key point is that the use of heart beat messages at regular intervals allows failures to be detected in a timely fashion.

An approach that would result in strong consistency would state that no replica copy of an object can be updated until after all other replicas are invalidated. However this type of approach typically results in high overhead across the nodes and caches.

Another approach would utilize invalidation messages such that when an object is updated invalidation messages are sent to caches containing copies of the object. This approach has the advantage that a new copy of the object may be sent with the invalidation message a form of prefetching . Also expiration times may be established by using the heart beats to bound the amount of time an object can be obsolete in the event of failures.

Yet another approach would provide that objects have explicit expiration times after which they are no longer valid.

Still further a trade off approach would trade off between the level of consistency and the level of performance the trade off being that stronger consistency generally results in more overhead.

The caches in the system shown in could implement one of these approaches or some other suitable approach. These approaches will be further discussed below in the context of step of .

An object would typically have a home cache . The properties of home caches are summarized in . A home cache would typically access and or update an object more frequently than other caches would. A home cache for an object o would normally either have the most current version of o or not have a copy stored of o at all.

As illustrated in a home cache of an object o maintains a list referred to as cachelist o which identifies other caches storing o. In some cases cachelist o would not be completely accurate however a cache identified by cachelist o would normally have a greater than average probability of containing o.

Statistics may be maintained on access and or updates to object o to determine its home cache . In addition the home cache may vary depending on the access and or updates to o.

As further depicted in caches maintain directories for cached objects. Cached objects are indexed by a key identifying the object.

The directory contains the value of a cached object o and may optionally include a version number for o. If the cache is the home cache for o then the directory also stores cachelist o and a list of other caches thought to be storing o. Otherwise if the cache is not the home cache for o then the directory stores the home cache of o.

The directory may also store updatestatus o which would indicate how o could be updated. For example it may be possible for any cache to update o. It may only be possible for the home cache of o to update o. Object o may be read only and hence not updatable.

Otherwise if o is not found in c then in step the home cache for o h is determined. Note that it is possible for h to be c. If h contains o then the value of o obtained from h is obtained. If h does not contain o then cachelist o is examined to see if o might be stored in another cache. Other caches on cachelist o are examined until the value of o is obtained. If the value of o is not obtained after examining all caches on cachelist o the system returns that o was not found.

A cache may become populated with objects in step on cache misses. Alternatively a cache may also be populated by explicitly adding objects to the cache using the cache API depicted in .

A method for updating cached objects is depicted in . In step a request to update an object would be received by a cache c. The request would include a key k identifying the object and a new value v for the object.

In step the request would be handled in one of multiple ways. The system would first look for k in the directory for c. If k is not found the system would have the option of storing k in the system and assigning it an appropriate home cache updatestatus and storing the object in an initial set of caches. It could assign parameters for the object and select the initial set of caches based on parameters in the request and or default values.

If k is found and corresponds to an object o the system would determine how to proceed based on the updatestatus o parameter. If updatestatus o indicates that o is read only o is not updated and step returns with an appropriate return value.

If updatestatus o indicates that o can be updated by any cache then c can perform the update. If updatestatus o indicates that o can only be updated by its home cache then the home cache for o must perform the update.

Let u be the cache assigned to perform the update in step . In step u performs the update using one of several consistency policies. There are several possible consistency schemes that could be used. These include but are not limited to the following 

In general higher degrees of consistency result in more overhead and vice versa. Therefore consistency policies can be made based on the degree of consistency required and the overhead an application is willing to tolerate. Strong consistency generally results in the most overhead but the highest degree of consistency.

Note that it is possible to tailor consistency policies to specific objects. Some objects need much higher levels of consistency than others. In addition consistency policies can be based on the resources available to the system. If system resources are plentiful then a stronger consistency policy can be applied. When system resources are scarce e.g. it is desirable to reduce message traffic a consistency policy which conserves resources e.g. expiration times in which lifetimes are not too short may be desirable even if this results in lower degrees of consistency.

In step cachelist o contained on the home cache for o is used to identify caches storing o. That way such caches can be updated in accordance with the consistency policy.

Before describing how a home cache may be determined in the context of we now describe a strong consistency approach an invalidation message approach and an expiration time approach .

In step caches are supposed to send acknowledgements to c after they invalidate their copy of o. Note that c may fail to receive an acknowledgement due to a cache and or network failure. Failure detection schemes such as those based on heart beats can be used to bound the amount of time c needs to wait for acknowledgements. After a sufficient time out interval c can proceed with an update even if it has not received all acknowledgements.

Objects may optionally have expiration times associated with them which would bound the time that an object would be obsolete in a cache due to a lost invalidation message.

Returning to a method for determining a home cache for an object o is shown. In general the home cache for an object should be located on a node which frequently accesses and or updates the object. In many cases the vast majority of accesses and updates to an object will be by a single node n. In that case a cache c on n should be the home cache for o. Most of the accesses and updates would be handled by c. Only a small percentage of accesses and updates would be handled by caches on other nodes since the other nodes access and update o much less frequently.

In step the system maintains statistics on updates and accesses to an object o. In step the home cache for o is determined based on these statistics. A home cache is selected for o which resides on a node making many accesses and or updates to o. There are several specific methods for selecting a home cache for o within the spirit and scope of the invention including but not limited to the following 

Let N be the number of times o was updated in the last c time units. For all times Acorresponding to when o was accessed in the last c time units and all times Ucorresponding to when o was updated in the last c time units 

Note that step can be applied to dynamically change the home cache of o after it already has a home cache. This could occur if the patterns of accesses and updates to o change making a new home cache a better choice. A key feature of this invention is the ability to change the home cache of an object in response to a change in workload. The new home cache will correspond to a node which frequently accesses and or updates the object.

A data processing system suitable for storing and or executing program code such as the computing system shown in may include at least one processor coupled directly or indirectly to memory element s through a system bus . The memory elements can include local memory employed during actual execution of the program code bulk storage and memories which provide temporary storage of at least some program code to reduce the number of times code is retrieved from bulk storage during execution. Input output or I O device s including but not limited to keyboards displays pointing devices etc. may be coupled to the system either directly or through intervening I O controllers. Network interface s may be included to enable the data processing system to become coupled to other data processing systems or remote printers or storage devices through intervening private or public networks. Modems cable modem and Ethernet cards are just a few of the currently available types of network adapters.

It is to be appreciated that the term processor as used herein is intended to include any processing device such as for example one that includes a CPU central processing unit and or other processing circuitry. It is also to be understood that the term processor may refer to more than one processing device and that various elements associated with a processing device may be shared by other processing devices. Thus software components including instructions or code for performing the methodologies described herein may be stored in one or more of the associated memory devices e.g. ROM fixed or removable memory and when ready to be utilized loaded in part or in whole e.g. into RAM and executed by a CPU.

It is to be understood that one or more of the nodes and caches shown in could be implemented via the computing system shown in .

Further it is to be understood that while the methods described herein for managing objects across multiple caches can be implemented in one or more of the nodes of the data processing system on which the caches reside a separate dedicated computing system e.g. as shown in that is coupled to each cache and or node could implement the management methods described herein.

Although illustrative embodiments of the present invention have been described herein with reference to the accompanying drawings it is to be understood that the invention is not limited to those precise embodiments and that various other changes and modifications may be made by one skilled in the art without departing from the scope or spirit of the invention.

