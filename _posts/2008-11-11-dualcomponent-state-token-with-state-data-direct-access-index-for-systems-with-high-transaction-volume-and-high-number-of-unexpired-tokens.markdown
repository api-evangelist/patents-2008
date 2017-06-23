---

title: Dual-component state token with state data direct access index for systems with high transaction volume and high number of unexpired tokens
abstract: Access to state data by a client process such as state data in an Online Transaction Processing arrangement is controlled through generation of and exchanging of a dual-component token. The first component of the token is an Index value which indirectly points to a block of state data assigned to process or user. The second component of the token is a sequence value, such as a Random Unique Sequence value, which is also associated with the block of state data for a process. With each transaction request, a user process provides the token to the OLTP server, which then verifies the sequence numbers of the state data and the token match before allowing access to the data.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07689701&OS=07689701&RS=07689701
owner: International Business Machines Corporation
number: 07689701
owner_city: Armonk
owner_country: US
publication_date: 20081111
---
This application is a continuation of U.S. patent application Ser. No. 10 844 635 filed on May 13 2004 now U.S. Pat. No. 7 512 693 by James Lewis Hollingsworth which is currently under allowance.

The related patent application Ser. No. 10 844 635 filed on May 13 2004 by James Lewis Hollingsworth is hereby incorporated by reference in its entirety.

This application is a continuation of U.S. patent application Ser. No. 10 844 635 filed on May 13 2004 by James Lewis Hollingsworth which is currently under allowance. This invention relates to state data management methods and systems for client server and transaction processing computing arrangements.

IBM originally developed Customer Information Control System CICS to provide online transaction processing OLTP programs for its mainframe computer systems. Today together with COBOL programming language a very large number of legacy applications still use the COBOL CICS applications and environment to process transactions by accessing business data such as orders inventory records and customer data.

CICS controls the interaction between application programs and the users of the system and CICS allows programmers to develop screen displays without detailed knowledge of the terminals which will be used by the users. Using an application programming interface API developers can write programs to access business data in a database to maintain data integrity. In fact current business application programs written in billions of COBOL lines facilitate more than 20 billion online transactions per day. Despite the attention in the computing industry being made to newer languages such as C and Sun Microsystems Java COBOL CICS actually still has the largest installed base of applications. Therefore it is still important for the CICS computing environment to be advanced to meet new customer requirements and needs.

The CICS products can reside on many types of operating systems such as OS 390 and UNIX running on a wide variety of computing hardware platforms such as IBM s iSeries Enterprise servers or IBM compatible Personal Computers. The latest IBM CICS Transaction Server for z OS Version 2.3 offers an array of features and functionalities. It provides an efficient and effective environment for applications written in COBOL PL I C C and Java. This version strengthens application development capabilities enables enhanced re use of 3270 applications and enables applications to be accessed as Web Services within a services oriented architecture SOA .

The CICS Transaction Server provides a robust high performance environment for enterprise applications written in Java as well as COBOL. In other words it supports Enterprise Java Beans EJB session beans that provide another dimension for application architects. Where an EJB component needs to incorporate procedural logic modules to accomplish its business function CICS enables this mixed language component to run in a single execution environment with good isolation from other components improving robustness and manageability.

In addition CICS allows for a run time environment optimized for business logic written as EJBs that can run alongside and interoperate with business logic written in other languages such as COBOL. Both EJB and COBOL applications can access existing and new databases such as DB2 IMS and VSAM data concurrently and with complete integrity.

Furthermore CICS Transaction Server contains enhancements for applications that use TCP IP communication for e business enablement. These offer a range of benefits in terms of management and improved scalability and performance. Enhancements such as DB2 facilities provide a significant improvement in performance and greater level of availability. In summary CICS assists in the evolution to on demand computing through integration open architecture autonomic computing and virtualization.

Turning to a CICS environment and process is depicted in a general or high level manner which a number of client systems consoles or terminals are provided processing by an OLTP server via a communications network and a web server . Each OLTP process or instance of an OLTP process is associated with one or more state data blocks. State data blocks may store transaction data session data or combinations of the two. The associated web server blocks can provide some business logic as well as user interface functions e.g. forms screens etc. .

For example a bank may have several teller consoles located throughout the bank. The teller consoles which are the end user clients in this scenario can be used to establish a new banking account for a new bank customer. In this example a teller uses a console to enter information into screens or forms which drive an OLTP process to create the new bank account entering information such as the customer s personal data name address telephone number etc. and account options e.g. checking savings investment etc. . Forms and screens may be created and provided by the web server process associated with the teller console being used. The data however is stored in state data which is associated with OLTP process and web process . The information which the teller inputs is accumulated in the state data block. In this example the OLTP process creates or generates a state data token that is associated with the state data. The state data token is passed to the client and is returned with subsequent requests from the client to assure that only the appropriate client device is allowed to use the state data associated with that client.

Although the existing technology relating to state data token generation and state data management fulfills much of online transaction processing needs in the industry it does not handle high transaction volumes as effectively or efficiently as possible. In fact current methods do not scale as well as possible with high transaction loads which adversely affects response time.

Contributing factors to poor scalability may be attributed to either instruction path length or I O overhead in a state data access method or the need for process or resource serialization.

Randomly generated tokens used as keys to access state data in an indexed data base require the data base to employ an index search algorithm and record update locking technique. The record locking technique is a form of resource serialization.

Methods employing state data chained in main memory require process serialization for token generation state data access and purging of expired state data.

For these reasons there exists a need to provide a state data access control mechanism which exhibits improved scalability to handle a high volume of transactions in a system or OLTP environment such as CICS.

Access to state data by a client process such as state data in an Online Transaction Processing arrangement is controlled through generation of and exchanging of a dual component token.

The dual component token structure contains a random unique sequence number and an index that provides direct access to the state data index array entry. The state data index array entry contains a pointer to the state data block in main memory.

Upon each transaction request an end user process returns a token to the OLTP server preferably via a web server. Upon receipt of the returned token the OLTP system verifies the sequence numbers of the state data block and the dual component token match before allowing access to the state data.

Minimal process serialization is required to achieve the logical processes of the invention thereby allowing improved scalability of the new process for larger volume OLTP environments.

According to one aspect of a preferred embodiment the tokens are exchanged over a communications network in a displayable code format to avoid incorrect translation of the tokens by intermediary servers operating systems or protocols which may otherwise incorrectly translate or modify a binary format token.

According to other aspects of the invention a separate process periodically performs automatic asynchronous purging of expired state data. Purged state data blocks are cleared and marked as available for re use. An attempt to access an expired state data block before it has been purged by the asynchronous purge process results in an immediate purge of the state data block.

Our new Dual Component Token DCT in conjunction with the methods and systems for generating and using our DCTs effectively provides a secure method for end user client processes in an OLTP environment to access the proper state data blocks with its unique identifiers while requiring minimal processing overhead thereby allowing the method to be highly scalable in high volume OLTP environments.

Through use of randomized sequence values predictability of our dual component tokens is minimized and avoids token duplications either malicious or accidental. In addition our state data access control method reduces access and response times. This combination of powerful aspects of our invention provides extensible scalability without regard to transaction volume or number of unexpired tokens.

Turning to the diagram illustrates the preferred embodiments of the various data structures according to our invention. The Dual Component Token DCT comprises two components a an Index and b a Random Unique Sequence RUS number. The Index element is used to directly index into our State Data Index array .

The RUS number is also distinctive across all generated tokens both expired and unexpired for a period of time which is lengthened or shortened depending on transaction rate. The Random Unique Sequence RUS can not be duplicated until after 16 777 215 have been generated in the preferred embodiment. On the average it will be twice this number or 33 554 430. This might represent several days in a typical system.

Our State Data Index SDI array entry consists of two components or fields as well. First it contains an address which points to a portion of memory or State Data Block SDB each portion of memory storing the actual state data for a particular OLTP process e.g. application program or instance of an OLTP process. The address in the State Data Index array is typically set to a null value for a State Data Block which was previously released.

Second our SDI contains a status indicator for each of the State Data Blocks having at least three possible conditions available in use and reserved . A status of available indicates that the SBD to which it points is available for use by a new OLTP process or instance of a process to serve an end user process requests. The state data address may either point to a previously allocated State Data Block which was previously purged or the address may be null.

A status of in use indicates that a currently running OLTP process is using the SDB to which the address points. While the OLTP process is still running the state data may not be purged and is not available to another OLTP task or process.

A status of reserved indicates that our access control logic has reserved the SDB for a particular client process and that it will remain reserved until it is explicitly released by an OLTP process associated with the particular client or until it expires. When the SDB s expiration time is reached before an OLTP process accesses the SDB again the state data is preferably automatically purged following which the status becomes available. However if the SDB is accessed again before its expiration time is reached the status changes to in use while the SDB is being accessed. If the Expiration time has been reached the state data is immediately purged the state data block is cleared and the status is changed from Reserved to Available .

Continuing with reference to our State Data Available array SDA contains indices of available e.g. unused or unallocated entries in the SDI array. Each index value contained in the SDA is an index to an entry in the SDI which is available for use in a new DCT . When a new token is generated an index value is selected and used from the SDA and that selected index value is removed from the SDA to avoid its re use in another token. When a state data block is purged the index for that DCT is recovered and placed back into the SDA for use in another token some time in the future. These processes are described in more detail in the following paragraphs.

The State Data Block SDB comprises three parts for each block a an RUS value b an expiration time and or date and c the actual state data. The state data component of a SDB contains data to support a particular client s transactions and conversations with an OLTP process. Typically an OLTP process ends after it transmits a response to the client. When the client transmits a subsequent request containing the state data token a new OLTP process is started or instanciated.

The RUS for the state data block is matched to the DCT token RUS which has been provided or assigned to the client which uses the state data. Generally speaking when an end user client processes needs to continue processing transactions on a particular block of state data it submits a transaction request including a DCT which was originally provided to the client by the OLTP system. The token is passed from the client through one or more web servers and intermediary servers and eventually to the OLTP server.

Upon receipt by the OLTP server the DCT is examined to determine if the RUS it contains matches the RUS stored in the SDB before access to the state data is allowed. A non match may indicate that the SDB was previously used by a conversation whose expiration time has lapsed and the state data has already been purged. Or a non match may indicate a fraudulent attempt to access state data for another end user client. More details of this aspect of the invention are provided in the following paragraphs.

The expiration time for each state data block indicates the deadline beyond which state data can be or should be purged if no OLTP process has recently accessed or used the data. This allows the system to recover state data memory space when transaction processing is sufficiently old or stale.

When an end user client process submits an initial request for OLTP processing a new Dual Component Token is generated by the OLTP server and an associated state data block is allocated. This new DCT is transmitted with the response to the requesting end user client process such that the end user client process can return it to the OLTP server with future processing requests.

According to one aspect of the present invention the generation of a new dual component token comprises a three phase process the logic of which is illustrated in a general sense in and . Referring first to an available index value from the SDA is selected preferably the last entry in the SDA. This selected index is used to reserve an entry in the SDI array which in turn points or will point to a state data block .

If entries in the SDA array already exist a Next Available Index variable is decremented by 1 the last entry in the SDA array is retrieved and saved as the new token Index component . The entry in the SDA array from which the Index was retrieved is set to 0 thereby removing that Index value from availability for use in other tokens.

If however no entries are available in the SDA array e.g. all Index values are currently in use the SDI array high water mark variable is incremented e.g. to make room for an additional Index value and that value is saved as the Index value in the new DCT token . This Index component insures that each token across all unexpired tokens is unique.

It is worth noting that in a multi processor environment process serialization may be required to prevent multiple OLTP tasks running on different processors from updating either the Next Available Index the State Data Index array high water mark and or the Random Unique Sequence described later values at the same time. In such an environment process serialization is only required around the instructions used to decrement the Next Available Index to increment the State Data Index array High Water Mark or to increment the Random Unique Sequence value. In many programming languages each of these operations can be accomplished with a single instruction and as such serialization of these individual instructions do not significantly detract from scalability or load capacity of the OLTP system. However because IBM s CICS dispatches application tasks whose programs are defined with COncurrency quasirent on the single Quasi Reentrant QR TCB ENQ serialization should not be necessary as long as no CICS API commands are coded between serialization points.

In the second phase of logic as shown in the saved Index component of the DCT being generated is retrieved and used to directly access the SDI array entry to which it points. The status of the indicated entry in the SDI array is changed from Available to Reserved . If the State Data address is null or there were no entries in the SDA array a state data block is allocated and the address is placed in the SDI array entry . This completes the SDI array entry reservation process. In the third phase of token generation as shown in the logic of the invention generates a Random Unique Sequence RUS value for the new DCT token. The logic retrieves the last used RUS value e.g. the RUS value of the most recently created DCT token and obtains a new non zero random value from a random number generator . The new random value is used to modify the previously used RUS value such as by adding the two values to each other to generate a new random value which is by definition not the same as the previous RUS value e.g. because it has been modified using a non zero random value . Finally according to our preferred embodiment an expiration date and or time is stored in the State Data Block .

There are three methods employed to insure that the RUS component is not predictable according to our preferred embodiment. First when the system is initialized the initial RUS component is seeded with a sufficiently large e.g. 8 byte random binary value. Second for each new token a random value is added to the preceding RUS so that a new random value is used for each new token generated. Third the newly generated RUS is preferably scrambled using a factorial algorithm before being exposed for external use.

This insures a unique token across all generated tokens both expired and unexpired over a reasonable amount of time depending on transaction rate. The RUS cannot be duplicated until after 16 777 215 have been generated according to a preferred embodiment even though typically it will be twice this number or 33 554 430. This might represent several days in a typical OLTP system. Assuming a high water mark of 10 000 concurrent unexpired tokens there will be only a 1 in 2 560 000 probability of a newly generated token matching an expired token that was generated over 16 777 215 tokens ago. Therefore duplication is minimized and exclusivity is achieved.

This new RUS value becomes the RUS value for the new DCT token e.g. it is stored in the DCT being created it is saved as the previous RUS e.g. to avoid re using the RUS value in the next DCT token and it is stored in the corresponding State Data Block which has been allocated to the OLTP process to which the new DCT will be assigned. The expiration time is also placed in the State Data block at this time.

At this point following these three phases the generation of a new Dual Component Token is complete including an Index value and a Random Unique Sequence value and the appropriate data structures are complete such as that the Index can be used to access an allocated state data block. Further the allocated state data block has been created so as to include the RUS which can be used during future access attempts to verify authorization by a client or process to access the data as described in the following paragraphs .

It will be recognized by those skilled in the art that these three phases may be performed in different orders and with varying details of implementation so as to achieve the same products e.g. achieve the described DCT token and data structures without departing from the spirit and scope of the present invention.

Prior to providing this new DCT token to a client device it is preferably converted to a displayable data format such as a 16 character display format from an 8 character binary format for reasons described in more detail in the following paragraphs.

During transaction processing on behalf of a client device the DCT token is employed to restrict access to state data stored by the server to only the client to whom the state data belongs e.g. more precisely to the OLTP process and instance of process which is being executed on behalf of the specific client .

According to another aspect of our invention the logical processes employed to access state data consists of restore and save processing as depicted in a general sense in .

A multi step process is preferably used in our state data Restore logic as shown in . A DCT token received from a client associated with a processing request.

This should be the same token which was supplied to the client by the OLTP when the session or transaction was started

According to our preferred embodiment the DCT is converted from a 16 character display format to an 8 character binary format using a modulo 26 algorithm and the Random Unique Sequence from the token is unscrambled using a factorial algorithm . As previously mentioned in this disclosure regarding DCT generation our preferred embodiment provides for the exchange of DCT tokens in a converted displayable data format. There is a potential data translation problem for information which is transmitted across computing platforms having a variety of file systems and operating systems. For example if the DCT were exchanged between the end user client and the OLTP server as a binary value then any translation process would have know where the DCT was located in the message in order to leave the DCT untranslated thus preserving the DCT value. Other business data in displayable format would be translated from one codepage to another e.g. from ASCII to EBCDIC . By converting the DCT to a displayable value ASCII to EBCDIC translation may be performed on the message without regard to special handling of the DCT.

Next the Index component of the DCT token is used to check the corresponding entry in the SDI . If the status of the entry in the SDI is not reserved or if the address in the SDI entry is null or if the State Data RUS does not match the token RUS then the access is denied .

Otherwise the SDB is accessed according to the address in the indicated SDI entry and if the state data is expired this DCT token is not a valid token for the SDB e.g. fraudulent attempt to access the state data is being made so the access request is rejected .

Otherwise the expiration time is checked in the SDB . If it has expired the state data is immediately purged by clearing the state data block changing the status to available and placing the index as the last entry in the SDA array.

If Expiration time remains and the RUS values match then access to the state data proceeds by altering the status of the SDB in the SDI from Reserved to In Use and allowing the state data to be accessed e.g. read or modified . When access to the state data is completed the status of the SDB is returned to reserved .

Preferably expired state data is also purged by a state data purge task that is timer triggered to run periodically. This housekeeping task takes care of purging expired state data when a client has not attempted access that would have caused an immediate state data purge as described above. The state data purge by the housekeeping task is performed by setting the status to Available and the Index is placed as the last entry in the SDA array as described in the following paragraphs.

Our state data Save function as shown in is also a multi step process similar to the Restore process. The Index component is retrieved from the DCT token and used to directly access the SDI array entry where the status of the entry is changed from In Use to Reserved . Next the SDB is addressed using the address from the entry in the SDI array and the expiration timer is set . Finally the RUS portion of the token is scrambled preferably using a factorial 4 algorithm and the binary format is converted to a display format preferably from an 8 character binary format to a 16 character display format using a modulo 26 algorithm. The display formatted token will be the external token sent back to the client.

According to another aspect of the preferred embodiment and as previously mentioned expired SDB data is preferably automatically purged and the state data block recovered asynchronous to any access requests. Occasionally or periodically the SDI array is browsed from beginning to end. This browse only considers entries that have a Reserved status . Then the expiration time of each reserved SDB is checked against the current system time and or date. If the expiration time within an SDB has been reached or passed then the state data is immediately purged the status is changed from Reserved to Available and the corresponding Index is placed as the last entry in the SDA array to be re used in a new DCT token.

The present invention may be realized in part or in its entirety as electronic circuitry such as in a Application Specific Integrated Circuit. In such a realization some of the logical steps described in the foregoing paragraphs may be performed simultaneously rather than sequentially as is possible in logic circuits. Therefore the steps and processes described may not in some implementations be implemented in the sequence or serially as described but which is within the scope of the present invention nonetheless.

The present invention may also be realized in part or whole as a feature or addition to the software already found present on well known computing platforms such as personal computers web servers and web browsers and such as the IBM CICS software environment.

These common computing platforms can potentially include portable computing platforms such as personal digital assistants PDA web enabled wireless telephones and other types of personal information management PIM devices provided they have the necessary computational bandwidth memory and communications capabilities.

Therefore it is useful to review a generalized architecture of a computing platform which may span the range of implementation from a high end web or enterprise server platform to a personal computer to a portable PDA or web enabled wireless phone.

Turning to a generalized architecture is presented including a central processing unit CPU which is typically comprised of a microprocessor associated with random access memory RAM and read only memory ROM . Often the CPU is also provided with cache memory and programmable FlashROM . The interface between the microprocessor and the various types of CPU memory is often referred to as a local bus but also may be a more generic or industry standard bus.

Many computing platforms are also provided with one or more storage drives such as a hard disk drives HDD floppy disk drives compact disc drives CD CD R CD RW DVD DVD R etc. and proprietary disk and tape drives e.g. Tomega Zip and Jaz Addonics SuperDisk etc. . Additionally some storage drives may be accessible over a computer network.

Many computing platforms are provided with one or more communication interfaces according to the function intended of the computing platform. For example a personal computer is often provided with a high speed serial port RS 232 RS 422 etc. an enhanced parallel port EPP and one or more universal serial bus USB ports. The computing platform may also be provided with a local area network LAN interface such as an Ethernet card and other high speed interfaces such as the High Performance Serial Bus IEEE 1394.

Computing platforms such as wireless telephones and wireless networked PDA s may also be provided with a radio frequency RF interface with antenna as well. In some cases the computing platform may be provided with an infrared data arrangement IrDA interface too.

Computing platforms are often equipped with one or more internal expansion slots such as Industry Standard Architecture ISA Enhanced Industry Standard Architecture EISA Peripheral Component Interconnect PCI or proprietary interface slots for the addition of other hardware such as sound cards memory boards and graphics accelerators.

Additionally many units such as laptop computers and PDA s are provided with one or more external expansion slots allowing the user the ability to easily install and remove hardware expansion devices such as PCMCIA cards SmartMedia cards and various proprietary modules such as removable hard drives CD drives and floppy drives.

Often the storage drives communication interfaces internal expansion slots and external expansion slots are interconnected with the CPU via a standard or industry open bus architecture such as ISA EISA or PCI. In many cases the bus may be of a proprietary design.

A computing platform is usually provided with one or more user input devices such as a keyboard or a keypad and mouse or pointer device and or a touch screen display . In the case of a personal computer a full size keyboard is often provided along with a mouse or pointer device such as a track ball or TrackPoint . In the case of a web enabled wireless telephone a simple keypad may be provided with one or more function specific keys. In the case of a PDA a touch screen is usually provided often with handwriting recognition capabilities.

Additionally a microphone such as the microphone of a web enabled wireless telephone or the microphone of a personal computer is supplied with the computing platform. This microphone may be used for simply reporting audio and voice signals and it may also be used for entering user choices such as voice navigation of web sites or auto dialing telephone numbers using voice recognition capabilities.

Many computing platforms are also equipped with a camera device such as a still digital camera or full motion video digital camera.

One or more user output devices such as a display are also provided with most computing platforms. The display may take many forms including a Cathode Ray Tube CRT a Thin Flat Transistor TFT array or a simple set of light emitting diodes LED or liquid crystal display LCD indicators.

One or more speakers and or annunciators are often associated with computing platforms too. The speakers may be used to reproduce audio and music such as the speaker of a wireless telephone or the speakers of a personal computer. Annunciators may take the form of simple beep emitters or buzzers commonly found on certain devices such as PDAs and PIMs.

These user input and output devices may be directly interconnected to the CPU via a proprietary bus structure and or interfaces or they may be interconnected through one or more industry open buses such as ISA EISA PCI etc. The computing platform is also provided with one or more software and firmware programs to implement the desired functionality of the computing platforms.

Turning to now more detail is given of a generalized organization of software and firmware on this range of computing platforms. One or more operating system OS native application programs may be provided on the computing platform such as word processors spreadsheets contact management utilities address book calendar email client presentation financial and bookkeeping programs.

Additionally one or more portable or device independent programs may be provided which must be interpreted by an OS native platform specific interpreter such as Java scripts and programs.

Often computing platforms are also provided with a form of web browser or micro browser which may also include one or more extensions to the browser such as browser plug ins .

The computing device is often provided with an operating system such as Microsoft Windows UNIX IBM OS 390 OS 2 LINUX MAC OS or other platform specific operating systems. Smaller devices such as PDA s and wireless telephones may be equipped with other forms of operating systems such as real time operating systems RTOS or Palm Computing s PalmOS .

A set of basic input and output functions BIOS and hardware device drivers are often provided to allow the operating system and programs to interface to and control the specific hardware functions provided with the computing platform.

Additionally one or more embedded firmware programs are commonly provided with many computing platforms which are executed by onboard or embedded microprocessors as part of the peripheral device such as a micro controller or a hard drive a communication processor network interface card or sound or graphics card.

As such describe in a general sense the various hardware components software and firmware programs of a wide variety of computing platforms suitable for realization of the present invention.

While many details of preferred and optional embodiments have been disclosed in order to illustrate the present invention it will be recognized by those skilled in the art that certain variations and modifications from the disclosed examples may be made without departing from the spirit and scope of the present invention. Therefore the scope of the invention should be determined by the following claims.

