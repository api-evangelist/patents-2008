---

title: Optimizing lock acquisition on transaction logs
abstract: A system, method, and computer program product for improving physical lock acquisition for database transaction logs are described herein. In an embodiment, the method operates by receiving a request for a transaction log page and determining whether a requested log page is newly-allocated or already exists. A determination is made regarding whether the last log page is being modified. A physical lock is taken on the requested log page when it has been determined that the requested log page is not newly-allocated and that the last log page is not being modified. Operations on the last log page are synchronized without a physical lock when it is determined that the requested log page is newly-allocated or that the last log page is being modified.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07899794&OS=07899794&RS=07899794
owner: Sybase, Inc.
number: 07899794
owner_city: Dublin
owner_country: US
publication_date: 20080320
---
The present invention relates generally to databases and more particularly to optimizing acquisition of physical locks in database transaction logs to guarantee cache coherency.

Acquiring physical locks on a transaction log of a database is a resource intensive operation and has performance implications in terms of database scalability. Database applications rely heavily on acquiring physical locks in database transaction logs in order to guarantee cache coherency.

As the number of nodes increase with large database management system DBMS applications physical lock acquisition becomes more expensive.

As the number of nodes in a database environment increases physical lock acquisition and management become more expensive. When a serialized transaction log stream is shared amongst many nodes a performance bottleneck can arise. The resources needed to acquire and manage a large number of transaction log locks across multiple nodes can limit the ability to scale or grow a database. As distributed multi node databases are growing in size and complexity what is needed are methods and systems that efficiently acquire and manage transaction log locks.

Transaction logs are critical resources when it comes to growing or scaling databases. There have been several features and enhancements done in the past to improve the performance of transaction logging. Many database management system DBMS platforms with a cluster comprised of multiple nodes employ shared disks to improve data reliability and to enable features such as database mirroring and data replication. When shared disks are used database transaction logs are even more critical as they are the single point of contention between the nodes in the cluster.

Currently in the art physical locks are taken on all data and transaction log pages of a database. There is overhead associated with taking physical locks on data pages. In order to maintain buffer cache coherency and to synchronize access to data and transaction log pages across multiple nodes a module must take physical locks. The steps involved every time a physical lock is taken on a page often include the following a requester node takes the cache spinlock setting unsetting the cluster specific status bits pertaining to a group of buffers which are controlled together in the cache. A MASS unit may be attached to control a group of buffers. The specific physical lock request goes to Cluster Lock Manager CLM module via a call to the lock multiple physical routine the CLM sends a blocking asynchronous trap BAST request to the BCM thread of the owner node. A BAST request is an asynchronous event issued by a lock manager that manages physical lock requests. After the BAST request is issued the request is queued the owner downgrades its lock as needed and the owner transfers the transaction log page to the requester. Each of these steps requires some execution time and thus impact system performance. There is also space overhead as the physical locks are retention locks. Each successfully taken physical lock consumes a memory location permanently.

Furthermore each time a physical lock is taken it adds a LOCKREC element into the grant convert queue of the CLM which in turn increases the search time for a given LOCKREC. Accordingly what is desired is a means of efficiently acquiring and managing transaction log locks. What is further needed is a protocol that enables more efficient physical lock acquisition for transaction log pages. What is further desired are systems and methods that help eliminate expensive operations during database transaction logging and enables better database scaling.

Accordingly what is needed are methods systems and computer program products that optimize database transaction log lock acquisition. What is further needed are methods systems and computer program products that optimize transaction log lock optimization by avoiding physical lock acquisition for new transaction log page allocations including the last transaction log page.

The present invention includes methods systems and computer program products that optimize transaction log lock acquisition. The method includes the step of appending to a transaction log without acquiring physical locks during new log allocations and on the last transaction log page. The present invention further includes a new protocol used to acquire physical lock on transaction log pages. Significant performance improvements are possible through use of the new protocol. The present invention includes methods systems and computer program products that optimize transaction log lock acquisition by minimizing the need to take physical locks on transaction log streams. The present invention optimizes database transaction logging and enables scaling of databases by reducing resource intensive operations during logging.

According to an embodiment of the invention operations on the Last transaction log Page LLP are synchronized through the Last log object lock LLOL at the node level and the Append Log Semaphore at the task level. The method further includes the step of scanning the transaction log to acquire physical locks on the transaction log pages and following the physical lock acquisition both read only scanners such as Database consistency check dbcc log triggers and scanners that modify in between log pages i.e. deferred update dump transaction checkpoint etc . The method divides log scanners into two categories read only scanners such as DBCC LOG operations and scanners that update intermediate log pages such as deferred update operations. According to an embodiment log scanners do not allocate new log pages or append to the transaction log.

In accordance with an embodiment of the invention the method synchronizes read write operations on any other transaction log page through physical locks. According to an embodiment scanners that also modify the transaction log at intermediate points e.g. deferred updates and dump tran operations that modify intermediate pages in the log will additionally take LLOL when modifying particularly the last transaction log page.

The invention also includes a computer program product comprising a computer usable medium having computer program logic recorded thereon for enabling a processor to optimize database transaction log lock acquisition. The computer program logic avoids physical lock acquisition for new transaction log page allocations including the last transaction log page.

The invention additionally includes a system capable of optimizing database transaction log lock acquisition. The system includes a first module to synchronize operations on the LLP through the LLOL at the node level and Append Log Semaphore at the task level a second module to take physical locks on the transaction log pages and subsequently synchronize through physical locks the read write operations on any other log page for read only scanners dbcc log triggers and scanners that modify in between log pages deferred update dump tran checkpoint etc and a third module to take the LLOL when scanners who also modify the transaction log at intermediate pages e.g. deferred update and dump tran operations that modify middle log pages modify the last transaction log page.

Further features and advantages of the invention as well as the structure and operation of various embodiments of the invention are described in detail below with reference to the accompanying drawings. It is noted that the invention is not limited to the specific embodiments described herein. Such embodiments are presented herein for illustrative purposes only. Additional embodiments will be apparent to persons skilled in the relevant art s based on the teachings contained herein.

The present invention will now be described with reference to the accompanying drawings. In the drawings generally like reference numbers indicate identical or functionally similar elements. Additionally generally the left most digit s of a reference number identifies the drawing in which the reference number first appears.

As used herein a physical lock refers to a distributed lock taken in a cluster environment in order to guarantee buffer cache coherency. The present invention optimizes acquisition and synchronization of the last log page in a database transaction log.

 Databases as used herein are collections of one or more data objects. Data objects may include but are not limited to any audio graphical video text or written work encoded in digital form and encapsulated in a computer structure such as a table a database record a data store record a column in a database record a field in a database record a file a message or a shared memory object that a software program can access and manipulate.

A transaction log as used herein refers to the transaction log of a database. A transaction log is a history of actions executed by a database management system DBMS in order to guarantee the Atomicity Consistency Isolation and Durability ACID properties of database transactions in the event of database server crashes unexpected database shutdowns or hardware failures. Physically a transaction log is a file or collection of updates done to the database that is stored in stable storage.

If after a start the database is found in an inconsistent state or not been shut down properly a DBMS reviews the transaction logs for uncommitted transactions and rolls back changes made by these transactions. All transactions that have been previously committed but whose changes were not yet materialized or posted in the database records are re applied. In this way transaction logs ensure atomicity and durability of transactions.

A transaction log is a special object that grows serially without other data manipulation language DML operations such as database record updates and deletes. Transaction log pages can be de allocated and truncated through specific database conditions such as a dump transaction log command or when the database reaches a checkpoint either through an explicit command or as a result of database records all being saved and committed . Before writing transaction log records tasks acquire an end of log semaphore. An end of log semaphore is a lock on the last transaction log object. The last transaction log object knows where the last transaction log page LLP is located i.e. address in memory or on disk . The owner node of last log object lock LLOL flushes the dirty log chain before transferring the LLOL to the requester node. Transaction log pages need to be scanned in read only mode for transaction aborts database consistency checking dbcc of the transaction log or similar operations. No updates to the transaction log pages are performed when they are scanned in read only mode.

Access to the transaction log must be synchronized on the node level and on the task level. In accordance with embodiments of the present invention both levels of synchronization are described below.

At the node level a cluster node that needs to append transaction log records onto the transaction log must take a lock on the last transaction log object. The Last transaction log object is an entity which knows where the last transaction log page is. When the request for last log object lock LLOL is made it goes to the current owner of the LLOL. After current owner is done with its transaction logging it flushes the dirty log chain to disk and downgrades the LLOL so that the requester node can now begin writing its transaction log.

At the task level on a particular node access to the transaction log is synchronized via use of a semaphore. A semaphore is a protected variable which is used to restrict access to the shared transaction log resource. According to an embodiment of the present invention the semaphore used to synchronize access to the transaction log may be one or more of a counting semaphore a binary semaphore a flag a variable or a mutex.

In accordance with an embodiment of the present invention an Append Log Semaphore is used to synchronize access to transaction log. According to an embodiment a task writes to its transaction log by flushing its private log cache PLC and taking the append log semaphore. The Append Log Semaphore may also be checked at the end of transaction log synchronization. If a task can not take or obtain the append log semaphore immediately it waits until the task that currently has the semaphore is done with its operations i.e. done writing to end of the transaction log . In accordance with an embodiment the Append Log Semaphore may have an associated queue of processes waiting to write to the transaction log. For example if a process attempts to perform a transaction log write operation on an Append Log Semaphore which has the value zero the process is added to the Append Log Semaphore s queue. When another process increments the Append Log Semaphore by performing a transaction log write operation and there are other processes on the queue one of the processes is removed from the queue and resumes its transaction log write task.

A Physical lock is a mechanism used to maintain cache coherency. In an embodiment cache coherency is maintained by a Buffer Coherency Manager BCM module. Access to pages in the cache is synchronized by acquiring physical locks at the node level. Anytime a transaction log page is requested either for read or for write the task needs to take an appropriate physical lock either a shared physical lock or an exclusive physical lock on the page before the task can begin its operations on the requested transaction log page. In an embodiment a physical lock is a node level locking mechanism.

In accordance with an embodiment at the node level a cluster node who wants to access the page has to first acquire a shared or exclusive physical lock on the transaction log page based on its requirement . When the request for physical lock is made it goes to Cluster Lock Manager CLM module which in turn determines which node is the current owner of the physical lock on this log page. After the CLM identifies the current owner of physical lock on this page it sends a blocking asynchronous trap BAST request to the owner node. Once the owner node is done with its operations on this page it transfers the page to the requesting node flushes the requested page to disk if it is dirty checks if the lock needs to be downgraded and checks for a conflicting lock request such as a shared exclusive SH EX or exclusive exclusive EX EX conflict.

If the CLM can not determine which node holds the physical lock on a requested log page the CLM assumes that this is the first physical lock request on this page and the CLM immediately grants a physical lock to the requesting node. At this time the CLM indicates to the requesting node that the last log page can be read from disk.

According to an embodiment of the present invention many locking steps and methods for synchronizing log appenders are not needed because of use of the last log object lock LLOL and an Append Log Semaphore. Taking a physical lock on a page is an expensive resource intensive operation which involves messaging between the requester node the cluster lock manager and the owner node. Physical locks are retained by the node who requested it until a conflicting lock request arises. Maintaining physical locks is also resource intensive as it involves overhead and memory consumption. Physical lock maintenance also consumes search time to determine which node is the current lock owner and what kind of lock the owner has. Accordingly avoiding taking physical locks where ever possible provides a gain in overall system performance.

The last log page LLP is a database object which is needed at one time or another by database tasks executing data manipulation language DML operations such as inserts deletes and updates. In order to maintain the ACID properties of transactions a transaction log record is appended written to the transaction log for each DML operation. Access to the LLP is very frequent and multiple access requests can arise simultaneously.

In a typical Online transaction processing OLTP application DML operations need to append to transaction logs frequently. According to an embodiment of the invention log scanners do not append to the transaction log. In an embodiment log scanners and other database operations such as dump transaction commands DBCC LOG transactions and database triggers scan the transaction log in read only mode but do not append to the log. In an embodiment log scanners such as deferred update transactions update intermediate log pages but do not write new transaction log pages.

Once the last log object lock LLOL on a node has been acquired there is no need to acquire any physical locks on the new allocated log pages as no other node will request the newly allocated log page before acquiring the LLOL. According to an embodiment LLOL serializes access to newly allocated transaction log pages. In another embodiment physical locks must still be taken for transaction log pages to avoid deadlocks with log scanners i.e. tasks scanning previously allocated pages in the transaction log .

An embodiment of the present invention takes advantage of the above characteristics of transaction log and implements a locking scheme that avoids physical lock acquisition for newly allocated transaction log pages including the last transaction log page.

More particularly flowchart illustrates the steps by which the locking method for new transaction log pages including the last transaction log page is performed according to an embodiment of the present invention. Note that the steps in the flowchart do not necessarily have to occur in the order shown.

The method begins at step where an evaluation is made regarding whether a log page request has been made for a newly allocated transaction log page including the last log page . If it is determined that an existing log page has been requested control is passed to step . If it is determined that the request is for a new allocation of a log page including the last log page then control is passed to step .

In step an evaluation is made regarding whether a last log page LLP allocation is being made. If it is determined that a LLP allocation is being made control is passed to step . If it is determined that a log page allocation is not being made for a log scanner control is passed to step .

In step an evaluation is made regarding whether a modification to the last log page LLP or an intermediate portion of the transaction log is being made. If it is determined that the transaction log is not being modified at the LLP or in an intermediate page of the log control is passed to step . If it is determined that the transaction log is being modified at the LLP or to an intermediate page of the log control is passed to step .

In step physical locks are taken on existing transaction log pages. In accordance with an embodiment of the present invention log scanners will still take physical locks on the log pages when the log modification occurs at the LLP or to an intermediate page of the log. In step read only log scanners and database operations such as database consistency check dbcc log commands and database triggers will take physical locks on existing transaction log pages. In step log scanners and database operations that modify transaction logs in between log pages such as deferred updates dump transaction and checkpoint operations may also take physical locks on existing transaction log pages. According to an embodiment in step read write operations on log pages besides the LLP and newly allocated log pages are synchronized by taking physical locks. After physical locks for existing log pages are acquired by log scanners in step the method ends in step .

In step an evaluation is made regarding whether the new log page allocation is occurring at the node or task level. If it is determined that the new log page allocation is occurring at the node level then control is passed to step . If it is determined that the log page allocation is occurring at the task level control is passed to step .

In step operations on said LLP are synchronized through the Last Log Object Lock LLOL for operations at the node level in accordance with an embodiment of the present invention and the process ends in step .

In step operations on the LLP at the task level are synchronized through the Append Log Semaphore according to an embodiment of the invention and the process ends instep .

In certain cases log scanners that modify intermediate pages of the transaction log e.g. deferred updates and dump tran operations will additionally take the last log object lock LLOL when modifying particularly the last transaction log page. However in accordance with an embodiment of the invention log scanners will not append to the transaction log.

The following paragraphs detail how these cases are addressed in accordance with embodiments of the present invention.

According to an embodiment of the present invention the locking method for the last transaction log page does not take physical locks on the freshly allocated log pages. In an embodiment operations on the Last transaction log Page LLP are synchronized through the Last Log Object Lock LLOL at the node level and via use of the Append Log Semaphore at the task level. Section 2.2 gives a specific example of and details how tasks that append to transaction logs i.e. log appenders can use LLOL and the Append Log Semaphore to avoid taking physical locks for newly allocated transaction log pages according to an embodiment of the invention.

According to an embodiment when multiple nodes need to append to a transaction log access to the last log page LLP is synchronized by steps of a method. A timeline for synchronizing access to the LLP is described in Table 1 in accordance with an embodiment of the invention.

The steps synchronizing access to the LLP include but are not limited to those listed and described in . is a flowchart illustrating steps by which locks on new and last transaction log pages are acquired in accordance with an embodiment of the present invention.

More particularly flowchart illustrates the steps by which synchronization of access to the LLP amongst multiple nodes is achieved according to an embodiment of the present invention. Note that the steps in the flowchart do not necessarily have to occur in the order shown.

The method begins at step where the LLOL is requested by a node that needs to append to the transaction log.

In step the LLOL request from step is handled by the Buffer Coherency Manager BCM thread of a receiving node. According to an embodiment the receiving node in step is the current owner of the LLOL.

In step according to an embodiment the receiving node takes the Append Log Semaphore in order to synchronize access to the LLP with other local tasks waiting to write to the transaction log.

In step the receiving node examines the log and flushes any dirty transaction log pages to disk. In accordance with an embodiment of the present invention the current owner of the LLOL flushes any dirty log pages in the transaction log chain before transferring the LLOL to node that requested the LLOL in step .

In step the LLOL is transferred to the node that requested it in step and the requesting node becomes the owner of the LLOL. After the LLOL is transferred to the requesting node control is passed to step .

In step the requesting node reads the LLP from disk and writes its log records to the transaction log. After the requesting node has written its log records to the log control is passed to step .

In step an evaluation is made regarding whether there are local tasks waiting to write their log records to the transaction log. If it is determined in step that local tasks are waiting to write their log records to the transaction log control is returned to step and steps are repeated. This process is repeated until there are no more local tasks waiting to write their log records to the transaction log.

If it is determined that there are no more local tasks waiting to write their log records to the transaction log control is passed to step where the process ends.

There are scenarios with a partially filled last transaction log page that need special attention to avoid the possibility of transaction log page corruption. The following paragraphs detail how embodiments of the present invention address these scenarios to avoid transaction log page corruption.

Transaction log page P is not being updated by nodes or at time T . At time T node performs a log scan via a deferred update and node initiates an append operation . Append operation initiated by node attempts to write log records LR and LR to partially filed transaction log page P but must instead write log records LR LR to new page P because at time T node holds a physical lock on transaction log page P containing log record LR.

There is no potential for transaction log corruption or deadlocking until deferred update which initiates a log scanner operation on Node attempts to modify transaction log records at a subsequent time beginning from the last transaction log page P . As is currently known in the art corruption can occur in transaction log page in P when nodes and write to P simultaneously. The solution to this log page corruption problem is discussed below with reference to .

At time T node initiates transaction log append . As a result of log append node writes new log records LR and LR into partially filled log page P allocates new log page P and then continues writing new log records. At this point node is the current owner of last log object lock LLOL .

At time T node requests the last log object lock LLOL by issuing LLOL request and node handles the LLOL blocking asynchronous trap BAST request.

At time T node downgrades the LLOL thus making it available to node . Then at time T node flushes any dirty log pages to disk .

At time T deferred update executes on node and the update begins to modify log page P . After reading page P from disk node then performs the following steps depicted as pseudo code 

Once the last log page P is updated successfully the Append Log Semaphore is immediately released by node so that any pending requests for LLOL can be subsequently served.

According to one embodiment of the present invention the cmcc lastlogrefresh function performs the activities depicted in on last log page. For example the cmcc lastlogrefresh function is called when a log scanner operation such as dump transaction log or deferred update attaches to last log page P in order to modify it but log scanner operations will not write new transaction log records or append to the transaction log.

In an embodiment newly allocated transaction log page P is marked as private to node by setting the PRIVATE TO NODE status indicator flag using the MARK MASS PRIVATETONODE mass ptr Application Programming Interface API . According to an embodiment a MASS is a group of buffers which are controlled together in the cache. For example a MASS may be an attached unit used to control a group of buffers. Once a MASS is marked as being private to node the BCM does not take a physical lock on newly allocated transaction log page P . In accordance with an embodiment a MASS with PRIVATE TO NODE status is visible to local tasks on node and is not visible to the cluster lock manager or any other node such as node .

As long as a transaction log page such as P remains the last transaction log page the PRIVATE TO NODE status indicator flag is not cleared. The moment a new last transaction log page is allocated such as P the PRIVATE TO NODE status indicator flag is cleared for the previous last transaction log page. In an embodiment the PRIVATE TO NODE status flag is cleared done by a call to the bufdbtlastlog function.

If the private log cache PLC flush log write is requested on a existing last transaction log page the access to it is granted through a new simplified function cmcc getlastlogbp nolock which returns the last transaction log page buffer without acquiring the physical lock.

In accordance with an embodiment of the present invention all log scanners and log modifiers such as dump tran and deferred update operation in addition to read only log scanners e.g. DBCC log still take physical locks when they access existing transaction log pages such as P . For example transaction log access is still synchronized through physical locks as depicted in . Node that needs to scan the log via scan operation at time T in read only mode will take a shared physical lock on log page P and any modifiers of the log such as node will take and exclusive physical lock.

At time T node performs log scan while node initiates deferred update operation . Node is the owner of the LLOL at this time and node has allocated three transaction log pages P P and P with P being a partially filled page.

Log scan is not prevented from taking a physical lock on log page P as scanners sometimes takes a physical lock on the last log page. Scenario depicted in may arise which can result in transaction log page corruption.

Also at time T node gets the LLOL and node flushes its log pages to disk. Then node reads the last log page P from disk. Transfer of the LLOL does not happen at this time because neither node has a physical lock on any of the log pages.

Node continues appending to the log as a result of deferred update operation . Deferred update then fills page P and allocates a new log page such as P depicted in .

Node then scans the log pages and takes a physical lock on all of the log pages it scans including page P .

At the same time node begins a scan and requests a physical lock on page P . At this point a problem can arise as a part of node s physical lock request such as the old image of page P should not be transferred from node to node . This can result in page corruption and the solution to this potential problem is depicted in and described below.

As log scanners are not prevented from taking physical locks on log pages scanners sometimes take physical locks on the last log page but do not append to the log the following situation depicted in may arise which can result in transaction log page corruption. A solution to the log page corruption involving partially filled log pages is described below with reference to .

At time T node initiates append operation . Append operation attempts to write to partially filled log page P as pages P and P are full.

At time T node sends a LLOL request to node . At this time node identifies that a page transfer has been requested on log page P whose next page pointer is NULL and it immediately cancels the transfer request. At this point node sets a flag or variable accessible to node wherein the flag or variable indicates that the node could not transfer the requested log page. In an embodiment of the invention node sends a TXCANCEL cookie to requester node which indicates that node cannot transfer the page.

Also at time T after node receives a flag indicating that page P cannot be transferred node may attempt to read P from disk but the read operation is prevented when the page is dirty. In an embodiment the flag received by node is the TXCANCEL cookie sent by node .

At time T node requests a physical lock on page P and the Cluster Lock Manager CLM redirects the request to node .

After a physical lock is requested for page P nodes and then perform the following steps depicted as pseudo code 

At time T node initiates log scan of log pages P P and P . At time T log scan is initiated by node . Log scan operation scans log pages P and P .

The solution to the problem depicted in lies in the lock manager design. According to an embodiment when a node such as takes physical lock for the first time on a transaction log page such as P the page time stamp PTS value of the page being locked is set in the lock value block. In an embodiment of the present invention this operation is performed by the brfinish routine. When node subsequently requests a physical lock on the same page P the lock manager compares its PTS timestamp value with the timestamp set within the lock value block and does not initiate a transfer when the PTS timestamp value of page P on requester node is newer than the PTS within the lock value block.

In accordance with an embodiment if a call to the cmcc bufgetphysicallock function does not go through bufread and hence brfinish the page transfer can still happen and can still result in log page corruption. This page corruption scenario can happen when the last log page P is already cached in node and scan operation begins on node . Scan operation acquires a physical lock without reading the page P from disk. According to an embodiment scan operation does not write new transaction log records or append to the transaction log.

This subsection describes a case in which presence of a partially filled transaction log page in cache can result in a broken log sequence which can in turn result in wrong log page errors. A solution to the broken log sequence problem is described below with reference to .

At time T node initiates append operation . At this time node is the owner of the LLOL and writes log pages P P and P P is partially filled . Append operation writes to partially filled log page P as pages P and P are full.

At time T node scans log pages P P and P and acquires physical locks on them. At time T node does not write new transaction log records or append to the transaction log when scanning log pages P P and P .

At time T node initiates append operation . Append operation fills log page P and allocates a new log page P .

A potential problem arises at this point if node begins a forward scan such as a dump tran operation identifying the range of log pages that need to be de allocated . This problem exists when a scan on node starts at page P and it can not go beyond page P as the link between P and P does not exist. The presence of a partially filled log page such as P within a cache can result in a broken chain and can cause a broken log sequence error. Solutions to the broken log sequence error are described below with continued reference to .

When a dump tran operation identifies a broken log sequence the log sequence is not necessarily also broken on disk . It is possible that a broken log sequence exists only in the cache and that disk still has a valid log sequence. To solve this broken log sequence problem when a forward log scanner such as scan detects broken log sequence scan attempts to re read page P from disk . In the example of page P still points to P on disk and the log sequence is not broken on disk .

According to an embodiment to prevent broken log situations from arising when a node such as does not own the LLOL the method avoids keeping the last log page in cache longer than it is needed by node . In accordance with an embodiment when no node is working on the last log page it is removed from the cache.

In accordance with an embodiment of the present invention a bufnewpage function is called when a new transaction log page such as P is allocated. The bufnewpage call immediately marks a newly allocated transaction log page such as P as private to a node node in the example embodiment of .

At time T Node initiates transaction log append operation . Append operation appends to partially filled log page P At this time node is the owner of the LLOL and writes to partially filled log page P as pages P and P are full.

At time T node sends a LLOL request for P to a receiving node node in the example of . At this time node has the LLOL.

At time T node scans log pages P P and P and acquires physical locks on them. At time T node does not allocate new log pages when scanning log pages P P and P .

At time T node initiates an append operation that fills log page P . At this time new log page P is allocated.

Various aspects of the present invention can be implemented by software firmware hardware or a combination thereof. illustrates an example computer system in which the present invention or portions thereof can be implemented as computer readable code. For example the method illustrated by flowcharts and of can be implemented in system . Various embodiments of the invention are described in terms of this example computer system . After reading this description it will become apparent to a person skilled in the relevant art how to implement the invention using other computer systems and or computer architectures.

Computer system includes one or more processors such as processor . Processor can be a special purpose or a general purpose processor. Processor is connected to a communication infrastructure for example a bus or network .

Computer system also includes a main memory preferably random access memory RAM and may also include a secondary memory . Secondary memory may include for example a hard disk drive a removable storage drive and or a memory stick. Removable storage drive may comprise a floppy disk drive a magnetic tape drive an optical disk drive a flash memory or the like. The removable storage drive reads from and or writes to a removable storage unit in a well known manner. Removable storage unit may comprise a floppy disk magnetic tape optical disk etc. which is read by and written to by removable storage drive . As will be appreciated by persons skilled in the relevant art s removable storage unit includes a computer usable storage medium having stored therein computer software and or data.

In alternative implementations secondary memory may include other similar means for allowing computer programs or other instructions to be loaded into computer system . Such means may include for example a removable storage unit and an interface . Examples of such means may include a program cartridge and cartridge interface such as that found in video game devices a removable memory chip such as an EPROM or PROM and associated socket and other removable storage units and interfaces which allow software and data to be transferred from the removable storage unit to computer system .

Computer system may also include a communications interface . Communications interface allows software and data to be transferred between computer system and external devices. Communications interface may include a modem a network interface such as an Ethernet card a communications port a PCMCIA slot and card or the like. Software and data transferred via communications interface are in the form of signals which may be electronic electromagnetic optical or other signals capable of being received by communications interface . These signals are provided to communications interface via a communications path . Communications path carries signals and may be implemented using wire or cable fiber optics a phone line a cellular phone link an RF link or other communications channels.

In this document the terms computer program medium and computer usable medium are used to generally refer to media such as removable storage unit removable storage unit and a hard disk installed in hard disk drive . Signals carried over communications path can also embody the logic described herein. Computer program medium and computer usable medium can also refer to memories such as main memory and secondary memory which can be memory semiconductors e.g. DRAMs etc. . These computer program products are means for providing software to computer system .

Computer programs also called computer control logic are stored in main memory and or secondary memory . Computer programs may also be received via communications interface . Such computer programs when executed enable computer system to implement the present invention as discussed herein. In particular the computer programs when executed enable processor to implement the processes of the present invention such as the steps in the methods illustrated by flowcharts of of discussed above. Accordingly such computer programs represent controllers of the computer system . Where the invention is implemented using software the software may be stored in a computer program product and loaded into computer system using removable storage drive interface hard drive or communications interface .

The invention is also directed to computer program products comprising software stored on any computer useable medium. Such software when executed in one or more data processing device causes a data processing device s to operate as described herein. Embodiments of the invention employ any computer useable or readable medium known now or in the future. Examples of computer useable mediums include but are not limited to primary storage devices e.g. any type of random access memory secondary storage devices e.g. hard drives floppy disks CD ROMS ZIP disks tapes magnetic storage devices optical storage devices MEMS nanotechnological storage device etc. and communication mediums e.g. wired and wireless communications networks local area networks wide area networks intranets etc. .

While various embodiments of the present invention have been described above it should be understood that they have been presented by way of example only and not limitation. It will be understood by those skilled in the relevant art s that various changes in form and details may be made therein without departing from the spirit and scope of the invention as defined in the appended claims. It should be understood that the invention is not limited to these examples. The invention is applicable to any elements operating as described herein. Accordingly the breadth and scope of the present invention should not be limited by any of the above described exemplary embodiments but should be defined only in accordance with the following claims and their equivalents.

