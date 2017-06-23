---

title: Method for dynamic updating of an index, and a search engine implementing the same
abstract: In a method for a dynamic updating of an index of a search engine, wherein the index is an inverted index comprising a dictionary, a posting file with a posting list for each keyword of the index and a database log, the documents are inserted in the index in small batches called update generations, a list of all occurrences of keywords in the documents of each update generation is generated, the occurrence list is inserted in the database log, and for each keyword entered in the database a reference to a previous entry of the same keyword is created. This previous entry has a reference stored in the mass storage device as the last added entry of all recently keywords.—A search engine performing the method may be implemented on one or more servers with a mass storage device, and comprises a core search engine with a search subsystem and an indexing subsystem for creating a keyword index stored on the mass storage device and with the index realized as a dynamically updateable index.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08949247&OS=08949247&RS=08949247
owner: Microsoft International Holdings B.V.
number: 08949247
owner_city: Amsterdam
owner_country: NL
publication_date: 20081218
---
This patent application claims priority to Norwegian Patent Application No. 20076596 entitled A METHOD FOR DYNAMIC UPDATING OF AN INDEX AND A SEARCH ENGINE IMPLEMENTING THE SAME filed on Dec. 20 2007 the disclosure of which is incorporated herein by reference.

The present invention concerns a method for dynamic updating of an index of a search engine wherein the search engine is implemented on one or more servers comprising a mass storage device and wherein the index is an inverted index comprising a dictionary a posting file with posting lists for each keyword of the index and a database log.

The present invention particularly discloses a new dynamic free text search index structure and the dynamic updating thereof. The goal is to maintain the same query efficiency of current state of the art solutions while ensuring short and predictable update latency and maximum consistency.

The typical data structure used for free text search in large volumes of text is inverted indexes. An inverted index is stored in a mass storage and is accessed therefrom. Presently an inverted index uses a disk based access method and consists primarily of a lexicon and a posting file stored on and accessed from a disk based storage. The lexicon lists all words available in the index and for each word it stores the location and size of the word in the posting file. In the posting file there is a sorted list of all places document identification and position in document where the word occurs.

Unfortunately the basic inverted index is static and cannot be incrementally updated as documents are added deleted or modified. To handle this dynamic behaviour a typical implementation is using partitioning and merging but with several disadvantages. In the worst case one will have a 100 disk space overhead to handle rebuild of the largest partition. The second problem is the highly varying load on the disk. During merging of the largest partition it will have to read and write the full volume of the index causing lookup in the index to suffer a disk overload. At other times the index update load is minor. The third problem is the cost of switching partitions. When a new partition is introduced all the cache content is discarded and caches need to be reloaded causing a deep temporary performance drop. The last problem is the need to look up in multiple partitions causing potentially multiple disk operations when there could have been only one.

Several projects have tried to overcome these problems as evinced by the prior art publications listed below 

Doug Cutting and Jan Pedersen Optimizations for dynamic inverted index maintenance Proceedings of the 13th International ACM SIGIR Conference on Research and Development in Information Retrieval pp. 405 411 1990 

Anthony Tomasic Hector Garcia Molina and Kurt A. Shoens Incremental Updates of Inverted Lists for Text Document Retrieval SIGMOD Conference 1994 pp. 289 300 

Marc Overmars and Jan van Leeuwen Some principles for dynamizing decomposable searching problems Report RUU CS 80 1 Rijksuniversiteit Utrecht 1980 

Nicholas Lester Justin Zobel and Hugh E. Williams In place versus re build versus re merge index maintenance strategies for text retrieval systems CRPIT 26 Proceedings of the 27th conference on Australasian computer science 2004 pp. 15 23 

Brown E. W. Callan J. P. and Croft W. B. Fast incremental indexing for full text information retrieval Proceedings of the 20th International Conference on Very Large Databases VLDB September 1994 Santiago Chile 

C. Clarke and G. Cormack Dynamic Inverted Indexes for a Distributed Full Text Retrieval System Technical Report MT 95 01 Department of Computer Science University of Waterloo February 1995 

L. Lim M. Wang S. Padmanabhan J. Vitter and R. Agarwal Dynamic maintenance of web indexes using landmarks Proceedings of the Twelfth International World Wide Web Conference Budapest Hungary May 2003.

Firstly they do not handle the case of crash recovery and consistency. It is trivial to recover from a crash using the partition and merge approach just throw away the partition being built and start over again . On the other hand when doing incremental updates in the index structure it is important that a crash does not corrupt the data structures.

The second issue is the case of fast real time indexing and access. Most of the proposed structures do not have a short and predictable latency from the time when a document is received for indexing until it is searchable.

The third unique issue is multiversioning which is the ability to run a query on a specified version of the index concurrently with other queries running against other versions. This is used to ensure a consistent query over multiple distributed index partitions or a consistent sequence of queries against the same index e.g. refining a result .

Hence an object of the present invention is to provide a method for dynamically updating an index for a search engine such that indexing can take place in approximately real time and with a high frequent stepwise or semi continuous update.

Another object of the present invention is to maintain a high search query processing efficiency combined with short update latency and maximum consistency.

The above objects as well as further features and advantages are realized with a method according to the present invention which is characterized by steps for inserting documents in the index in small batches each batch constituting an update generation of the index generating a list of all occurrences of keywords in the documents of each update generation inserting the occurrence list in the database log and creating for each keyword entered in the database a reference to a previous entry of the same keyword in the database log said previous entry having a reference stored in the mass storage device as the last added entry of all recently added keywords.

The invention keeps the lexicon and posting file from the inverted list index but introduces four new concepts log file generations delta lists and checkpoints. A log file is a file that is written sequentially but can be read randomly. After a while the beginning of the file can be truncated. This is similar to a database log file. A generation is a batch of updates to the index insert delete update document . Generations are sequential and non overlapping i.e. there is a strict order of the generations. A delta list is the incremental postings in the postings file for a word for a given generation. A checkpoint is the process of collecting delta lists from the log file and writing them to the postings file.

Advantageously the following operations are supported by the method according to the present invention.

Obviously and preferably both the main posting and the delta lists can be compressed to save disk space and bandwidth.

Also additional features and advantages of the present invention shall be apparent from the appended dependent claims.

The special part of the description followed below has been divided into Sections 1 8 of which Section 1 sets the general background of the present invention into context Section 2 is a general overview Sections 3 and 4 are detailed discussions of features aspects and embodiments of the method according to the present invention as well as of index structures implemented on a search engine similar to the one shown in Sections 5 and 6 detail further aspects of the invention including its advantages the possibility of a generic updateable index and certain circumstances and aspects that must be taken care of when implementing the method according to the invention while Section 7 sketches some potential improvements to the method of the present invention although they may be considered as presently lying beyond the scope of the present invention as herein disclosed. Finally Section 8 is given to a few concluding remarks.

1.1 The search engine of the present invention shall as known in the art comprise various subsystems . The search engine can access document or content repositories located in a content domain or space wherefrom content can either actively be pushed into the search engine or via a data connector be pulled into the search engine. Typical repositories include databases sources made available via ETL Extract Transform Load tools such as Informatica any XML formatted repository files from file serves files from web servers document management systems content management systems email systems communication systems collaboration systems and rich media such as audio images and video. The retrieved documents are submitted to the search engine via a content API Application Programming Interface . Subsequently documents are analyzed in a content analysis stage also termed a content pre processing subsystem in order to prepare the content for improved search and discovery operations. Typically the output of this stage is an XML representation of the input document. The output of the content analysis is used to feed the core search engine . The core search engine can typically be deployed across a farm of servers in a distributed manner in order to allow for large sets of documents and high query loads to be processed. The core search engine can accept user requests and produce lists of matching documents. The document ordering is usually determined according to a relevance model that measures the likely importance of a given document relative to the query. In addition the core search engine can produce additional metadata about the result set such as summary information for document attributes. The core search engine in itself comprises further subsystems namely an indexing subsystem for crawling and indexing content documents and a search subsystem for carrying out search and retrieval proper. Alternatively the output of the content analysis stage can be fed into an optional alert engine . The alert engine will have stored a set of queries and can determine which queries that would have accepted the given document input. A search engine can be accessed from many different clients or applications which typically can be mobile and computer based client applications. Other clients include PDAs and game devices. These clients located in a client space or domain will submit requests to a search engine query or client API . The search engine will typically possess a further subsystem in the form of a query analysis stage to analyze and refine the query in order to construct a derived query that can extract more meaningful information. Finally the output from the core search engine is typically further analyzed in another subsystem namely a result analysis stage in order to produce information or visualizations that are used by the clients. Both stages and are connected between the core search engine and the client API and in case the alert engine is present it is connected in parallel to the core search engine and between the content analysis stage and the query and result analysis stages .

1.2 The indexing subsystem of the search engine indexes documents from the document or the content repository and creates the index of the search engine with keywords essentially in the form of all words from the index documents with the exception of stop words. When processing a search query the query or search terms is applied to searching the index finding the keywords of the index matching the search terms and on this basis retrieving the documents forming the result set of the query. The documents of the result set are retrieved from the content repository and as obvious they may not be stored in the search engine memory but instead on servers personal computers and so on that either are located within an enterprise framework or linked to the www. The search engine index itself is stored on mass storage device of the server or servers on which the search engine is implemented and presently such a mass storage device can be equated with magnetic disk memories. However in the following the reference usually will be to mass storage devices in the form of disk memories although it should be understood that the method according to the present invention is by no means limited to indexes stored on disk memories although the concept disk based is frequently invoked but in an exemplifying not limiting sense.

For this document documents are considered to be the units to be indexed. They are uniquely identified with Document IDentifiers DID . A document is a sequence of words or tokens uniquely identified with Word IDentifiers WID . Each word has a position in the document. Multiple words can have the same position.

All changes to indexed data are associated with a Generation Identifier GID . A generation is a consistent logical view of the data at a specific point in time. A query will be executed in the consistent view of a single generation and thus the result will be consistent. The generation concept is defined over the fully distributed platform.

At any time multiple generations might be visible. An open generation is a generation that has not been completely built yet and cannot be used for queries. Concurrently there might be more than one open generation.

An active generation is complete and consistent. New queries should be directed to the most recent active generation. When a new generation becomes active the older generations might be removed when there are no queries running against these generations.

The QR server keeps the GID of the most recent generation and new queries are labelled with this GID. In there are two active queries Query and Query . Query is old and runs against an old generation . The other query is new and recently submitted and tagged with GID 18. No queries will be issued for generation before it is fully installed and active.

GIDs are enumerated with a 64 bit linearly increasing integer which will be virtually inexhaustible. Operations on documents that change the index insert update or delete are given the GID of the current incomplete open generation when they are being fed.

A new generation is started based on either when the current generation has a maximum number of documents a maximum aggregated document size or a certain time interval. The best approach is probably a combination thereof. These parameters must be tuned with respect to two performance parameters indexing latency and indexing throughput. Many small generations means a shorter latency but probably also a higher overhead in the indexing process. Large generations give a better throughput but the time it takes to feed a generation delays the time before a generation becomes active and documents visible to searching.

This section outlines the index structures for an updateable inverted list index with full position information posocc . This index can also be applied to a boolocc and a phraseocc index without major changes. A similar approach can be used for other index formats and this will be described below.

The inverted list index maps from a word or token to a position list. The position list contains a list of documents where the word occurs and all the position in the documents where the word occurs.

Now the following important features and aspects relating to index updating namely the disk structures the main memory structures and the dynamic behaviour shall be discussed.

An index on disk consists of a set of files. All these files should have a common header listing the type of file and a version number. The version number is to ensure the ability to do online upgrade.

The dictionary maps from a word text to a word identifier WID and the position list and delta list for the last checkpointed generation CG. For small words two or less entries in the list the information can be embedded in the dictionary record itself. For collections with Zipf distribution of words this will cover more than 50 of the words according to the theory 65 .

The layout of the data in the dictionary is outlined by the following pseudorcode. The dictionary contains a set of DictionaryEntry records. Embedded inside records of this kind there may be records of the types PositionListRef DeltaPositionListRef Position and EmbeddedPositionList. The brackets denote Begin and End respectively. Comments to the code is placed after the double slash and to the right.

The information in this file must be directly accessible with maximum one disk access. To achieve this one can either 

As described here the WID is probably not needed at all. On the other hand one might replace the use of word somewhere with WID especially if the dictionary can be fit in memory.

The purpose of the log file is to record all changes done to the dictionary Section 3.1.1 and the occurrence file as they happen. The idea is to write changes here when the changes are committed and later batch up updates to the other files and do the updates in larger chunks which are more optimal with respect to disk usage.

The log file is mostly written and read sequentially and consists of typed records of varying size. All records have the following fields 

The log file can be organized as a set of memory mapped files. They are written sequentially one by one. When the last one has been filled up it starts over from the oldest one. The aggregated size of the log files limits the size of one checkpoint the log files must contain at least two checkpoints . The log size can be changed on line by adding or deleting log files.

In the beginning of each log file there should be a header listing the most recent checkpoint log record. All checkpoints can be found by following the previous pointer. The checkpoint entry in the header should be identified by a GID and contain the offset in the file. The header should also contain a high water marker showing how far the log has been written the LSN of the first log record in the file and a reference to the previous log file.

A common log file index should list the log files currently used their sizes their individual sequence and the most recently used log file.

The occurrence file consists of a set of position and delta lists. A position list gives all the locations of a given word. The position list is a sorted list of documents sorted by GID . For each document there is a list of positions where the word occurs. With each position there is also an application specific fixed sized occurrence data field e.g. scope information .

A delta list contains the changes to the position list since it was written. It contains one section for each generation where there have been changes to the position list. Each section consists of the GID and the LPL from the MO log record.

The layout of the position list and delta list is outlined by the following pseudocode. PositionList is the record layout of the position list. DocumentInfo contains the information about one document. OccurrenceInfo is the information about every occurrence of the word. DeltaList is the record layout of the delta list. Each entry in the delta list has the record format of DeltaEntry. The brackets denote Begin and End respectively. Comments to the code is placed after the double slash and to the right.

Note there are no GIDs in the position lists as they are only coded in the dictionary. There might be many position lists for the same word in the occurrence file as they will represent different checkpoints. An old position list cannot be removed from the occurrence file as long as it is searchable. The file must be a certain fraction larger than the data it indexes and this can probably be self tuneable.

For large occurrence entries they may be split it into smaller sections each compressed separately e.g. for each document or each n th document . A skip list can make it possible to skip sections not matching any other expressions to speed up composite queries.

The occurrence file will grow over time unless the space of old occurrence entries is reused. To do this a circular buffer strategy can be used. This is illustrated in .

The occurrence file should start with a specified fixed size. The end of the file wraps around to the beginning with the exception of the file header . The occupied part of the file is between two pointers into the file the tail and the head. All new and updated entries are written at the head where the free space shrinks. On the tail used areas are copied to the head and will be part of the current open generation. Unused space will be released and the free space area will increase. To release space it is necessary to know the oldest generation OG that should be searchable.

The occurrence file alone has no information on which areas are unused or not. This must be extracted from the dictionary and the log. Each time one wants to release space it is necessary to do a sequential scan of the log and dictionary. Each such scan is called a garbage collect scan GC scan . This can be done by 

It is possible to have two or more occurrence files. One file can contain frequently changing words while the other more static ones. This may make it more efficient to garbage collect the position lists.

It is possible to increase the size of the occurrence file by just adding space at the end of the file the next time the tail pointer comes to the end of the file. If the space is needed right away it is possible to add it at the end and then set head and tail to point to the start of the new free space and the start of the file respectively.

It is also possible to shrink the occurrence file when the tail reaches the end of the file and wraps around. The file can then be truncated somewhere between the head pointer and the end.

The free space can be automatically adjusted every time the tail reaches the end of the file. Set two threshold values lower and upper given either in bytes or percent of the file size. If the space between the head and the tail exceeds the upper value the file is truncated so the free space is somewhere between the thresholds e.g. the middle . If it drops below the lower value the file is extended to a value between lower and upper. E.g. lower threshold is 20 and upper is 30 .

Since the generation identifier ID is an always increasing variable and can change frequently e.g. once per second it must be large at least 32 bits and leads to a significant space overhead in the index. It is possible to save some of this space using an indirection mechanism. A generation map can map from a short intermediate generation identifier IGID e.g. 16 bit to a larger GID e.g. 64 bit . When all occurrences of an IGID have been removed from the index it can be reused by just modifying the generation map. To do this the log must have rotated once all log records with the old IGID overwritten and the dictionary scanned and all words with old IGIDs refreshed with the newest.

The relationship between the disk mass storage and main memory structures is shown in . The double framed boxes are disk based. The numbers in the boxes are GIDs. Numbers in parenthesis are implicit. The two numbers in the MD log records denote respectively the generation of the position list and the generation when the dictionary entry was changed.

The log buffer consists of all log files mapped into main memory. The log records can be accessed by logical pointers pointing into the log files. Such a logical pointer consists of a file number and an offset into the file which can be used to compute the physical address.

The dictionary cache caches the entries from the dictionary file. It will reside in the regular heap and have a maximum size parameter number of entries . Most systems should be able to cache the whole dictionary. Only systems with small main memories or an extremely high number of words should need to access the disk as part of a dictionary lookup.

All access to entries in the dictionary cache must go through the word cache. It must therefore always exist a word cache entry as long as the dictionary cache entry is present.

The replacement strategy might be LRU Least Recently Used . Each time an entry is accessed it is placed on the end of an LRU chain.

The word cache is a variable sized main memory structure caching information about words in the index. The entries are looked up using the word itself as a key. The cache entry contains two parts 

The cache is organized as an LRU structure with the ability to lock entries in the cache e.g. using reference counters . The entries are locked as long as the word is part of an incomplete checkpoint it has a pointer to an MO log record or if there exists a dictionary cache entry for the word.

The cache must have an entry for each word in the current incomplete checkpoint. Therefore there cannot be an upper limit on the size of the word cache. Instead there should be a preferred size. The cache should be allowed to grow above this if necessary but shrink again as soon as it is not required any more.

The index updates come in as log file entries from the indexing pipeline MO or GC log records . They are assigned an LSN number and copied to the memory mapped file log buffers. When a GC log record has been copied the log file is flushed to disk. When the log record has been written the log file header is updated with the new high water mark and written to disk. When the flush is complete the generation is searchable.

When an MO log record has been received and copied to the log the word is entered into the MOptr field in word cache and locked there. If it is already there check if it points to another log entry for the same word. If the new log entry belongs to the same checkpoint as the previous log record chain it into the previous list.

If there are more than one search node that are querying using the same index files e.g. sharing files over a NAS only one of them has to update the index. The other ones only need to track the changes. The updater will open the index files as read write the trackers only need to open them read only. An external entity takes the decision on which node is the updater.

A tracking search node tracks the new MO and MD log entries in the log and as they are added he updates the MOptr and the CkptMDptr fields in the word cache. CkptMOptr is not used. If one reads a CP log record the MOptr and the CkptMDptr fields are reset all entries in the word cache are unlocked and the dictionary cache entries removed for that word to invalidate the entry.

Only the updater nodes need to update the index files based on the index update log records. This process is called a checkpoint. A checkpoint starts after a specified time interval since last checkpoint or when the volume of the MO log records in the log since the last checkpoint exceeds a certain limit. A checkpoint is performed as follows 

If the position list fits in the dictionary entry the position list does not have to be written to the occurrence file. The dictionary entry should not be deleted if the position list becomes empty. It may be garbage collected later after one cycle through the log files. 

For systems with large main memories the whole dictionary and log will fit in memory. For the rest one needs to optimize the disk access pattern. The following measures are proposed 

A query comes in with a word and the generation identifier the query runs in QGID . The following procedure applies 

When a node starts it reads the headers of all log files and finds the location of the latest checkpoint. From the checkpoint it reads the log sequentially and re populates the word cache using the MO log records. Any MD log records in the log are just ignored. Generations are recorded as the log is read. Now the node can be opened for new queries.

An updater starts a new checkpoint based on the last GC log record if it does not already exist . It then registers with the indexing pipeline that it is ready to receive log record entries. It provides the GID of the last GC log record as a starting point. The indexer will potentially resend the log records of an incomplete generation but it does not matter since the log records are idempotent.

The updater node will wait until a GC log record is received. It will then stop all new queries and start a checkpoint. When the checkpoint has completed it will terminate the node.

This section evaluates the potential performance of the new index. We assume a Zipf distribution of words in documents and identical distribution for words in queries. The important parameter is the total number of word occurrences not the number of documents or words per document.

For a large number of words the 5000 most frequent words are about 90 of the total number of word occurrences. This is fairly independent of the total number of documents. See Table 2. 

For the rest of this chapter a stable index with 10 000 000 000 words and an update rate of 10 000 000 words per checkpoint are assumed. With an average 1 000 words per document one will have respectively 10 000 000 and 10 000 documents.

There will be 5 000 000 different words in the dictionary and each entry will be approx 50 bytes. Assuming a space overhead of 100 in the B tree the size of the dictionary will be 500 MB.

The log must be large enough to fit all log records after the penultimate checkpoint. Calculating approximate sizes for the log records we end up with less than 200 MB per checksum i.e. 400 MB. This must fit in main memory.

Use a 5 in place growth margin for the 5000 largest entries the occurrence file. This will give a static overhead of 4.5 . This will require 50 checkpoints in average before the extra space overflows and the full entry must be written to a new location. It is assumed that the garbage collection in most cases already has rewritten it before this happens. The last 10 of the words will be written sequentially at the head. Some of these words will be updated in multiple generations and have to be written multiple times. It is assumed an overhead of 1 due to these updates.

According to the Zipf distribution the most frequently occurring word will be 10 of the total volume in the occurrence file. The file must be able to store this word twice leading to an overhead of 10 . Adding another 10 for a safety margin and space for garbage collection we end up with a total overhead of 30 . This margin can be reduced if stop words are removed.

For optimal performance the dictionary and the part of the log since the last checkpoint must reside in main memory.

The dictionary will be 500 MB but a main memory cache version can be done much more compact say 300 MB.

A working space for the garbage collect process and query processing is needed. The most frequent word will be 10 of the total volume in the occurrence file. This can be copied processed in smaller chunks so moderately sized buffers should be sufficient e.g. 10 100 MB per thread .

Read 158 000 delta lists randomly the number is probably much lower this is a worst case number . If one can order the accesses by increasing disk position this will be half way sequential. The most frequently occurring words will probably be cached they will probably also have the largest delta lists .

Sequentially read the area of the disk that is being garbage collected picking up the position and delta lists that are being moved. Randomly read the delta lists not collocated with their position list. In the worst case a sequential read of the complete occurrence file. Sequentially write the new position and delta lists at the head.

Sequentially write new MD log records. Update the dictionary in the worst case sequentially rewriting the whole dictionary .

In most cases it should be possible to retrieve a term with only one sequential disk access. Only in the cases when the word has been changed since the last garbage collect and the position list and the delta list are not collocated it will be necessary with two disk accesses. For the numbers given above one is talking about less than 10 of the cases. The two disk accesses can be done in parallel.

If the dictionary does not fit in memory we will need an additional disk access to read the dictionary entry.

If the log does not fit in memory there might in the worst case be one extra disk access per MO log record. The accesses will be random but will be within a smaller restricted area on the disk the part of the log file since the last checkpoint started .

The updateable inverted list index described above can be generalized to most index types. In the generic case the following files are required 

For the inverted list the dictionary is the directory and the occurrence file the data file. The directory represents an indirection step that shall enable the maintenance of multiple versions of the same data. For each indexed element there has to be a pointer into the data file and a generation identifier. The log file will contain the identical log records and checkpointing will be the same.

An attribute vector may be taken as an example. Presently a vector attribute is accessed using the document identifier as a key. All elements have the same size and the position in the file can directly be computed. For an updateable attribute vector the position can be directly computed in the directory instead all entries in the directory will have the same size . Reading the entry in the directory a pointer to the attribute value in the data file will be found and it is GID. Each time the attribute value is changed a log record is written to the log. At checkpoint time the new value is written to a new location in the data file.

On the other hand it enables the dynamic update capability and doesn t require the vector elements to have a fixed size.

If there are many attribute vectors they can share the same directory and this reduces the space overhead.

The dictionary contains the document and occurrence count of a word only for the entries in the position lists. To get the exact numbers for a given generation it is necessary to combine it with info in the delta list. Unfortunately this will be difficult if a document is deleted or updated it will be necessary to subtract the old instance .

Prior art systems may use many inverted list indices at the same time. For this new updateable index it is also possible to maintain separate dictionary and occurrence files. On the other hand for best performance one should probably have a single shared log for each partition. The updates coming in to these multiple indices can then be written into the log with a single write saving a lot of disk head movements.

If an updater node crashes this must be detected and another node e.g. a tracking node must become an updater. It must perform recovery and has to wait for the indexing stream to be directed towards it.

There may be many indexing pipelines directing updates to the same updater node. If there are multiple updates to the same document they should be forwarded by the same pipeline.

An updater node must await generation complete from all indexing pipelines before it can write generation complete to its own log.

A log file can be added by just putting it into the list of log files. It should be put into the sequence after the log file currently being written to. Before it is added the log file should have a valid log file header. The file must also be mapped into the memory.

A log file can be removed when it is the next in the sequence to be written to. First the all checkpoints in the file have to be removed from the checkpoint index. Then the file can be removed from the list of log files and the file unmapped and closed.

If a user wants to remove a specific log file the user must enqueue it for removal and wait until it becomes the next file. This might take a log time if there are few or no index updates going on.

If one chooses to store the dictionary in a B tree it will automatically grow when data is inserted into it. Shrinking it becomes more difficult but may not be necessary.

The current indexing strategy with multiple generations handles crashes during indexing well. If there is a crash before the index is complete one just starts over again.

Care has been taken to keep this behaviour with new updateable index of the present invention. The log file enables redoing an operation if it fails. The largest problem is when in place updating of data on disk is performed. The following scenario might occur.

If there is an advanced storage array step 4 will not happen. But it might occur on cheaper storage solutions. The problem is that one cannot recreate the new data any more by reading the two sectors and applying the log record since the data is corrupted. The solution is either 

For the updateable index the problem arises for a delta list immediately following the occurrence list. It might be updated in place multiple times.

It might be possible to allow multiple computers to do checkpoints and garbage collection concurrently on the same index structure by partitioning the words range partitioning will probably be best . The start and stop of a checkpoint the allocation of space at the head of the occurrence file and update of the dictionary must be coordinated. The log file can be partitioned.

Occurrence lists for stop words will be very large and will be expensive to read from disk run matching against and update. Most often stop words are only valuable for phrase searches. A posocc file supports phrase searches but is much more expensive when stop words are present in the query than using a dedicated phrase search file.

It is possible to split the occurrence lists for stop words into smaller occurrence lists. Instead of indexing the stop word alone it is indexed with the following word. E.g. instead of indexing the one should index the camel the car and the cat etc.

Compression has not been discussed here. Compression should be considered both in the occurrence file position and delta lists the dictionary and the log. It might be just as important to compress the data when it is in memory as on disk. Caching it in a compressed form will increase CPU consumption for access to this data but will increase cache hit ratios and reduce disk I O.

Multiple occurrence files may be present depending on word size and update frequency. This might make it possible to optimize file system parameters in big storage arrays and garbage collection strategies. Non collocated delta lists may also be placed in their own occurrence file.

The method of the present invention works for index structures of an updateable inverted list index with full position information posocc . It can also be applied to a boolocc and a phraseocc index without major changes. A similar approach can be used for other index formats.

Altogether the present invention encompasses a hitherto uncharted territory with regard to indexes and index updating such that for instance the statistical aspects of document properties may lead to unexpected effects. The method of the invention appears more complex than previous indexing methods and provides for a more complex index structure and in order to achieve its goal it is important that there is adequate memory for the database log and dictionary. However the complexity of the inventive method and index and capacity requirements for its implementation on a mass storage device such as a disk memory shall in the long run be considered marginal factors. They are more than outweighed by the manly advantages of the method according to the present invention. An index generated and updated according to the method of the present invention shall always yield a very good freshness and be highly consistent while having a much lower storage overhead than current indexes. Moreover there is only one partition and this implies fewer memory accesses during a query term lookup. Furthermore the present invention supports multithreading during garbage collection and checkpoints shared file systems NAS with one updater and a plurality of searchers. Finally the dynamic updateable index realized by applying the method of the present invention shall enable long running searches without stalling indexing and hurting the freshness of the index.

