---

title: Adjusting communication parameters while inventorying RFID tags
abstract: RFID reader systems, readers, components, software and methods are provided for inventorying RFID tags. In some embodiments, a population of RFID tags begins being inventoried using a first set of communication parameters, and then continues using a second set of communication parameters. This way, some RFID tags can be inventoried faster, without missing tags that require a longer time to read.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07830262&OS=07830262&RS=07830262
owner: Impinj, Inc.
number: 07830262
owner_city: Seattle
owner_country: US
publication_date: 20080604
---
This application claims priority from U.S. Provisional Patent Application Ser. No. 60 934 602 filed on Jun. 14 2007 and U.S. Provisional Patent Application Ser. No. 60 956 171 filed on Aug. 16 2007 the disclosures of which are hereby incorporated by reference in their entirety.

This application is a Continuation In Part of application Ser. No. 11 412 170 filed Apr. 25 2006 now U.S. Pat. No. 7 408 466 B2 issued Aug. 5 2008 entitled ADJUSTING RFID WAVEFORM SHAPE IN VIEW OF DETECTED RF ENERGY commonly assigned herewith.

This application is a Continuation In Part of application Ser. No. 11 411 657 filed Apr. 25 2006 now U.S. Pat. No. 7 417 548 B2 issued Aug. 26 2008 entitled ADJUSTING RFID WAVEFORM SHAPE IN VIEW OF SIGNAL FROM AN RFID TAG commonly assigned herewith.

This application is a Continuation In Part of application Ser. No. 11 412 172 filed Apr. 25 2006 now U.S. Pat. No. 7 391 329 B2 issued Jun. 24 2008 entitled PERFORMANCE DRIVEN ADJUSTMENT OF RFID WAVEFORM SHAPE commonly assigned herewith.

Radio Frequency IDentification RFID systems typically include RFID tags and RFID readers. RFID readers are also known as RFID reader writers or RFID interrogators. RFID systems can be used in many ways for locating and identifying objects to which the tags are attached. RFID systems are particularly useful in product related and service related industries for tracking objects being processed inventoried or handled. In such cases an RFID tag is usually attached to an individual item or to its package.

In principle RFID techniques entail using an RFID reader to interrogate one or more RFID tags. The reader transmitting a Radio Frequency RF wave performs the interrogation. The RF wave is typically electromagnetic at least in the far field. The RF wave can also be predominantly electric or magnetic in the near field.

A tag that senses the interrogating RF wave responds by transmitting back another RF wave. The tag generates the transmitted back RF wave either originally or by reflecting back a portion of the interrogating RF wave in a process known as backscatter. Backscatter may take place in a number of ways.

The reflected back RF wave may further encode data stored internally in the tag such as a number. The response is demodulated and decoded by the reader which thereby identifies counts or otherwise interacts with the associated item. The decoded data can denote a serial number a price a date a destination other attribute s any combination of attributes and so on. Accordingly when a reader reads a tag code data can be learned about the associated item that hosts the tag and or about the tag itself.

An RFID tag typically includes an antenna system a radio section a power management section and frequently a logical section a memory or both. In earlier RFID tags the power management section included an energy storage device such as a battery. RFID tags with an energy storage device are known as active or semi active tags. Advances in semiconductor technology have miniaturized the electronics so much that an RFID tag can be powered solely by the RF signal it receives. Such RFID tags do not include an energy storage device and are called passive tags.

RFID readers operating at the faster 900 MHz range can read the codes of RFID tags more quickly than was possible at the earlier slower frequencies. Such reading of many tags is also called inventorying the tags. A challenge with such inventorying is RF noise in the environment which can make it difficult to read at least some of the tags. Plus in every inventorying scenario some tags can be inherently harder to read than others. When tags are not read for whatever reason operations are hurt.

Briefly the present invention provides RFID reader systems readers components software and methods for inventorying RFID tags. In some embodiments a population of RFID tags begins being inventoried using a first set of communication parameters and then continues using a second set of communication parameters.

The invention offers an advantage that some RFID tags can be inventoried faster without missing tags that require a longer time to read.

These and other features and advantages of the invention will be better understood from the specification of the invention which includes the following Detailed Description and accompanying Drawings.

The present invention is now described. While it is disclosed in its preferred form the specific embodiments of the invention as disclosed herein and illustrated in the drawings are not to be considered in a limiting sense. Rather these embodiments are provided so that this disclosure will be thorough and complete and will fully convey the scope of the invention to those skilled in the art. Indeed it should be readily apparent in view of the present description that the invention may be modified in numerous ways. Among other things the present invention may be embodied as devices methods software and so on. Accordingly the present invention may take the form of an entirely hardware embodiment an entirely software embodiment an entirely firmware embodiment or an embodiment combining aspects of the above. This description is therefore not to be taken in a limiting sense.

As has been mentioned the present invention provides RFID reader systems readers components software and methods for inventorying RFID tags. The invention is now described in more detail.

Reader and tag exchange data via wave and wave . In a session of such an exchange each encodes modulates and transmits data to the other and each receives demodulates and decodes data from the other. The data is modulated onto and demodulated from RF waveforms.

Encoding the data in waveforms can be performed in a number of different ways. For example protocols are devised to communicate in terms of symbols also called RFID symbols. A symbol for communicating can be a delimiter a calibration symbol and so on. Further symbols can be implemented for ultimately exchanging binary data such as 0 and 1 if that is desired. In turn when the waveforms are processed internally by reader and tag they can be equivalently considered and treated as numbers having corresponding values and so on.

Tag can be a passive tag or an active or semi active tag i.e. having its own power source. Where tag is a passive tag it is powered from wave .

Tag is formed on a substantially planar inlay which can be made in many ways known in the art. Tag includes an electrical circuit which is preferably implemented in an integrated circuit IC . IC is arranged on inlay .

Tag also includes an antenna for exchanging wireless signals with its environment. The antenna is usually flat and attached to inlay . IC is electrically coupled to the antenna via suitable antenna ports not shown in .

The antenna may be made in a number of ways as is well known in the art. In the example of the antenna is made from two distinct antenna segments which are shown here forming a dipole. Many other embodiments are possible using any number of antenna segments.

In some embodiments an antenna can be made with even a single segment. Different points of the segment can be coupled to one or more of the antenna ports of IC . For example the antenna can form a single loop with its ends coupled to the ports. It should be remembered that when the single segment has more complex shapes even a single segment could behave like multiple segments at the frequencies of RFID wireless communication.

In operation a signal is received by the antenna and communicated to IC . IC both harvests power and responds if appropriate based on the incoming signal and its internal state. In order to respond by replying IC modulates the reflectance of the antenna which generates the backscatter from a wave transmitted by the reader. Coupling together and uncoupling the antenna ports of IC can modulate the reflectance as can a variety of other means.

In the embodiment of antenna segments are separate from IC . In other embodiments antenna segments may alternately be formed on IC and so on.

The components of the RFID system of may communicate with each other in any number of modes. One such mode is called full duplex. Another such mode is called half duplex and is described below.

RFID reader and RFID tag talk and listen to each other by taking turns. As seen on axis TIME when reader talks to tag the communication session is designated as R T and when tag talks to reader the communication session is designated as T R . Along the TIME axis a sample R T communication session occurs during a time interval and a following sample T R communication session occurs during a time interval . Of course interval is typically of a different duration than interval here the durations are shown approximately equal only for purposes of illustration.

According to blocks and RFID reader talks during interval and listens during interval . According to blocks and RFID tag listens while reader talks during interval and talks while reader listens during interval .

In terms of actual technical behavior during interval reader talks to tag as follows. According to block reader transmits wave which was first described in . At the same time according to block tag receives wave and processes it to extract data and so on. Meanwhile according to block tag does not backscatter with its antenna and according to block reader has no wave to receive from tag .

During interval tag talks to reader as follows. According to block reader transmits a Continuous Wave CW which can be thought of as a carrier signal that ideally encodes no information. As discussed before this carrier signal serves both to be harvested by tag for its own internal power needs and also as a wave that tag can backscatter. Indeed during interval according to block tag does not receive a signal for processing. Instead according to block tag modulates the CW emitted according to block so as to generate backscatter wave . Concurrently according to block reader receives backscatter wave and processes it.

In the above an RFID reader interrogator may communicate with one or more RFID tags in any number of ways. Some such ways are called protocols. A protocol is a specification that calls for specific manners of signaling between the reader and the tags.

One such protocol is called the Specification for RFID Air Interface EPC Radio Frequency Identity Protocols Class 1 Generation 2 UHF RFID Protocol for Communications at 860 MHz 960 MHz which is also colloquially known as the Gen2 Spec . The Gen2 Spec has been ratified by EPCglobal which is an organization that maintains a website at at the time this document is initially filed with the USPTO.

In addition a protocol can be a variant of a stated specification such as the Gen2 Spec for example including fewer or additional commands than the stated specification calls for and so on. In such instances additional commands are sometimes called custom commands. Other commands are in common between protocols and between different versions of the protocol.

According to a comment block can include a command that establishes the communication parameters that are to be used. Such communication parameters can include for example what mode to use a backscatter link frequency BLF or just LF and so on.

In some embodiments commands from the reader include data encoded in terms of a first symbol for data 0 and a second symbol for data 1. In those cases one of the communication parameters can a duration of one of the first and the second symbols or a ratio of their durations. In embodiments of the Gen2 Spec these durations can be communicated by the Tari symbols.

In embodiments of various versions of the Gen2 Spec a Miller parameter MP can also be specified. For example the Miller Parameter MP can be defined consistently with how the Miller parameter M is defined in the Gen2 Spec v.1.1.0. In that version MP and also M can support the values of 1 2 4 and 8.

According to a comment the modulation of block can be according to the communication parameters mentioned in comment . The communication parameters provide for backscattering the same reply. The inventors have found that tags behave differently depending on these communication parameters as described later in this document.

It was described above how reader and tag communicate in terms of time. In addition communications between reader and tag may be restricted according to frequency. One such restriction is that the available frequency spectrum may be partitioned into divisions that are called channels. Different partitioning manners may be specified by different regulatory jurisdictions and authorities e.g. FCC in North America CEPT in Europe etc. .

Reader typically transmits with a transmission spectrum that lies within one channel. In some regulatory jurisdictions the authorities permit aggregating multiple channels into one or more larger channels but for all practical purposes an aggregate channel can again be considered a single albeit larger individual channel.

Tag can respond with a backscatter that is modulated directly onto the frequency of the reader s emitted CW also called baseband backscatter. Alternatively tag can respond with a backscatter that is modulated onto a frequency developed by tag that is different from the reader s emitted CW and this modulated tag frequency is then impressed upon the reader s emitted CW. This second type of backscatter is called subcarrier backscatter. The subcarrier frequency can be within the reader s channel can straddle the boundaries with the adjacent channel or can be wholly outside the reader s channel.

A number of jurisdictions require a reader to hop to a new channel on a regular basis. When a reader hops to a new channel it may encounter RF energy there that could interfere with communications.

Embodiments of the present disclosure can be useful in different RFID environments for example in the deployment of RFID readers in sparse or dense reader environments in environments with networked and disconnected readers such as where a hand held reader may enter the field of networked readers in environments with mobile readers or in environments with other interference sources. It will be understood that the present embodiments are not limited to operation in the above environments but may provide improved operation in such environments.

The inventors further found that when a whole population of tags is considered and read in a reading scenario its tags do not behave identically even if they are made identically to each other. Instead they seem to behave approximately as depicted in curve . So tags in a first subgroup of the population seem easier to read than those of a second subgroup whether the reading scenario is the same or different. This differentiation may be affected by a number of factors such as the exact reading scenario where the readers are a tag s place within the population whether the population is being moved and so on. It may also be related to power delivery to the tags which was documented in . Further this is not to say that it is always the same tags that are easier to read than the others in any given reading scenario. The easier tags could be the same every time or different ones at least some of the times. Curve will be useful to contrast inventorying algorithms of the prior art with the benefits of embodiments of the present invention.

As can be appreciated a bold portion of line is higher than curve for a first subgroup of N of the NT tags which will therefore be read. Moreover remaining portion of line is lower than curve for the remaining subgroup of tags in the population which will thus be missed.

According to a comment in some instances there is no more time after time T. The tags may have been moved for example. If that happens then returning to a remaining subgroup of tags in the population will be missed. This can happen even though the algorithm was good enough to catch them as evidenced from the remaining portion of line still being higher than curve for the remaining subgroup .

Referring back to data from the tags in subgroup will therefore not be received. And according to a comment the owner of the reader will not know that this otherwise accessible data was missed.

A driver can send to its respective antenna a driving signal that is in the RF range which is why connector is typically but not necessarily a coaxial cable. The driving signal causes the antenna to transmit an RF wave which is analogous to RF wave of . In addition RF wave can be backscattered from the RFID tags analogous to RF wave of . Backscattered RF wave then ultimately becomes a signal sensed by unit .

Unit also has other components such as hardware and or software and or firmware which may be described in more detail later in this document. Components control drivers and as such cause RF wave to be transmitted and the sensed backscattered RF wave to be interpreted. Optionally and preferably there is a communication link to other equipment such as computers and the like for remote operation of system .

Local block is responsible for communicating with the tags. Local block includes a block of an antenna and a driver of the antenna for communicating with the tags. Some readers like that shown in local block contain a single antenna and driver. Some readers contain multiple antennas and drivers and a method to switch signals among them including sometimes using different antennas for transmitting and for receiving. And some readers contain multiple antennas and drivers that can operate simultaneously. A demodulator decoder block demodulates and decodes backscattered waves received from the tags via antenna block . Modulator encoder block encodes and modulates an RF wave that is to be transmitted to the tags via antenna block .

Local block additionally includes an optional local processor . Processor may be implemented in any number of ways known in the art. Such ways include by way of examples and not of limitation digital and or analog processors such as microprocessors and digital signal processors DSPs controllers such as microcontrollers software running in a machine such as a general purpose computer programmable circuits such as Field Programmable Gate Arrays FPGAs Field Programmable Analog Arrays FPAAs Programmable Logic Devices PLDs Application Specific Integrated Circuits ASIC any combination of one or more of these and so on. In some cases some or all of the decoding function in block the encoding function in block or both may be performed instead by processor .

Local block additionally includes an optional local memory . Memory may be implemented in any number of ways known in the art. Such ways include by way of examples and not of limitation nonvolatile memories NVM read only memories ROM random access memories RAM any combination of one or more of these and so on. Memory if provided can include programs for processor to run if provided.

In some embodiments memory stores data read from tags or data to be written to tags such as Electronic Product Codes EPCs Tag Identifiers TIDs and other data. Memory can also include reference data that is to be compared to the EPC codes instructions and or rules for how to encode commands for the tags modes for controlling antenna and so on. In some of these embodiments local memory is provided as a database.

Some components of local block typically treat the data as analog such as the antenna driver block . Other components such as memory typically treat the data as digital. At some point there is a conversion between analog and digital. Based on where this conversion occurs a whole reader may be characterized as analog or digital but most readers contain a mix of analog and digital functionality.

If remote components are indeed provided they are coupled to local block via an electronic communications network . Network can be a Local Area Network LAN a Metropolitan Area Network MAN a Wide Area Network WAN a network of networks such as the interne or a mere local communication link such as a USB PCI and so on. In turn local block then includes a local network connection for communicating with network .

There can be one or more remote component s . If more than one they can be located at the same location or in different locations. They can access each other and local block via network or via other similar networks and so on. Accordingly remote component s can use respective remote network connections. Only one such remote network connection is shown which is similar to local network connection etc.

Remote component s can also include a remote processor . Processor can be made in any way known in the art such as was described with reference to local processor .

Remote component s can also include a remote memory . Memory can be made in any way known in the art such as was described with reference to local memory . Memory may include a local database and a different database of a Standards Organization such as one that can reference EPCs.

Of the above described elements it is advantageous to consider a combination of these components designated as operational processing block . Block includes those that are provided of the following local processor remote processor local network connection remote network connection and by extension an applicable portion of network that links connection with connection . The portion can be dynamically changeable etc. In addition block can receive and decode RF waves received via antenna and cause antenna to transmit RF waves according to what it has processed.

Block includes either local processor or remote processor or both. If both are provided remote processor can be made such that it operates in a way complementary with that of local processor . In fact the two can cooperate. It will be appreciated that block as defined this way is in communication with both local memory and remote memory if both are present.

Accordingly block is location agnostic in that its functions can be implemented either by local processor or by remote processor or by a combination of both. Some of these functions are preferably implemented by local processor and some by remote processor . Block accesses local memory or remote memory or both for storing and or retrieving data.

Reader system operates by block generating communications for RFID tags. These communications are ultimately transmitted by antenna block with modulator encoder block encoding and modulating the information on an RF wave. Then data is received from the tags via antenna block demodulated and decoded by demodulator decoder block and processed by processing block .

The invention also includes methods. Some are methods of operation of an RFID reader or RFID reader system. Others are methods for controlling an RFID reader or RFID reader system.

These methods can be implemented in any number of ways including the structures described in this document. One such way is by machine operations of devices of the type described in this document.

Another optional way is for one or more of the individual operations of the methods to be performed in conjunction with one or more human operators performing some of them. These human operators need not be collocated with each other but each can be only with a machine that performs a portion of the program.

The invention additionally includes programs and methods of operation of the programs. A program is generally defined as a group of steps or operations leading to a desired result due to the nature of the elements in the steps and their sequence. A program is usually advantageously implemented as a sequence of steps or operations for a processor such as the structures described above.

Performing the steps instructions or operations of a program requires manipulation of physical quantities. Usually though not necessarily these quantities may be transferred combined compared and otherwise manipulated or processed according to the steps or instructions and they may also be stored in a computer readable medium. These quantities include for example electrical magnetic and electromagnetic charges or particles states of matter and in the more general case can include the states of any physical devices or elements. It is convenient at times principally for reasons of common usage to refer to information represented by the states of these quantities as bits data bits samples values symbols characters terms numbers or the like. It should be borne in mind however that all of these and similar terms are associated with the appropriate physical quantities and that these terms are merely convenient labels applied to these physical quantities individually or in groups.

The invention furthermore includes storage media. Such media individually or in combination with others have stored thereon instructions of a program made according to the invention. A storage medium according to the invention is a computer readable medium such as a memory and is read by a processor of the type mentioned above. If a memory it can be implemented in a number of ways such as Read Only Memory ROM Random Access Memory RAM etc. some of which are volatile and some non volatile.

Even though it is said that the program may be stored in a computer readable medium it should be clear to a person skilled in the art that it need not be a single memory or even a single machine. Various portions modules or features of it may reside in separate memories or even separate machines. The separate machines may be connected directly or through a network such as a local access network LAN or a global network such as the Internet.

Often for the sake of convenience only it is desirable to implement and describe a program as software. The software can be unitary or thought in terms of various interconnected distinct software modules.

This detailed description is presented largely in terms of flowcharts algorithms and symbolic representations of operations on data bits on and or within at least one medium that allows computational operations such as a computer with memory. Indeed such descriptions and representations are the type of convenient labels used by those skilled in programming and or the data processing arts to effectively convey the substance of their work to others skilled in the art. A person skilled in the art of programming may use these descriptions to readily generate specific instructions for implementing a program according to the present invention.

Embodiments of an RFID reader system can be implemented as hardware software firmware or any combination. It is advantageous to consider such a system as subdivided into components or modules. A person skilled in the art will recognize that some of these components or modules can be implemented as hardware some as software some as firmware and some as a combination. An example of such a subdivision is now described.

RFID reader system includes one or more antennas and an RF Front End for interfacing with antenna s . These can be made as described above. In addition Front End typically includes analog components.

System also includes a Signal Processing module . In this embodiment module exchanges waveforms with Front End such as I and Q waveform pairs. In some embodiments signal processing module is implemented by itself in an FPGA.

System also includes a Physical Driver module which is also known as Data Link. In this embodiment module exchanges bits with module . Data Link can be the stage associated with framing of data. In one embodiment module is implemented by a Digital Signal Processor.

System additionally includes a Media Access Control module which is also known as MAC layer. In this embodiment module exchanges packets of bits with module . MAC layer can be the stage for making decisions for sharing the medium of wireless communication which in this case is the air interface. Sharing can be between reader system and tags or between system with another reader or between tags or a combination. In one embodiment module is implemented by a Digital Signal Processor.

System moreover includes an Application Programming Interface module which is also known as API Modem API and MAPI. In some embodiments module is itself an interface for a user.

All of these functionalities can be supported by one or more processors. One of these processors can be considered a host processor. Such a processor would for example exchange signals with MAC layer via module . In some embodiments the processor can include applications for system . In some embodiments the processor is not considered as a separate module but one that includes some of the above mentioned modules of system .

A user interface may be coupled to API . User interface can be manual automatic or both. It can be supported by a separate processor than the above mentioned processor or implemented on it.

It will be observed that the modules of system form something of a chain. Adjacent modules in the chain can be coupled by the appropriate instrumentalities for exchanging signals. These instrumentalities include conductors buses interfaces and so on. These instrumentalities can be local e.g. to connect modules that are physically close to each other or over a network for remote communication.

The chain is used in opposite directions for receiving and transmitting. In a receiving mode wireless waves are received by antenna s as signals which are in turn processed successively by the various modules in the chain. Processing can terminate in any one of the modules. In a transmitting mode initiation can be in any one of these modules. Ultimately signals are transmitted internally for antenna s to transmit as wireless waves.

The architecture of system is presented for purposes of explanation and not of limitation. Its particular subdivision into modules need not be followed for creating embodiments according to the invention. Furthermore the features of the invention can be performed either within a single one of the modules or by a combination of them.

An economy is achieved in the present document in that a single set of flowcharts is used to describe methods in and of themselves along with operations of hardware and or software and or firmware. This is regardless of how each element is implemented.

Flowchart is described in terms of distinct operations which may occur in different orders than is shown. A Start operation is designated as mostly a convenient starting point for this description. But flowchart can actually start at any one of these operations and indeed it will be recognized that execution could cycle along these operations more than once.

At operation one or more receive filters are optionally set or adjusted for the reader. This operation preferably takes place when communication parameters have been changed such that a different tag data rate has been defined. As will be recognized as values for the communication parameters are updated the tag data rate may change or remain the same.

The receive filter can be made in any way known in the art. The overall receive filters can include analog filters which are a first line of defense against noise and digital filters to further reject noise. The latter can be programmable for further refinement of operation.

The analog filters can include a Low Pass Filter which removes high frequency noise. It can be used with very slow tag data rates to accommodate maximum tag sensitivity. Additional analog filters are now described in terms of diagrams where amplitude is plotted over frequency.

Referring briefly to a frequency response of a sample Anti Aliasing Filter AAF is plotted. This can be a wide filter going up to about 1 MHz and is intended to primarily limit the noise going into an Analog to Digital Converter. When applied to communication using the Gen2 Spec it may work for all modes.

In addition a frequency response of a sample High Pass Filter HPF is plotted. This can remove low frequency noise. When applied to communication using the Gen2 Spec it can be used with Miller backscattering with the Miller Parameter having values of MP 2 4 or 8 but not baseband FM or MP 1.

In addition a frequency response of a sample Band Pass Filter BPF is plotted. This can help remove high frequency noise and low frequency noise. Plus it can be used for frequencies consistent with those called for in the Gen2 Spec v.1.1.0 and using a Miller parameter MP consistent with how M is defined in the Gen2 Spec v.1.1.0. In those cases the BPF can be designed to optimize a Signal to Noise Ratio best for the value of MP 4 less well for a value of MP 8 even less or not at all for a value of MP 2 or MP 1. In some embodiments it might not work at all for MP 2 or MP 1.

Returning to at next operation values are caused to be established for communication parameters that will be used for inventorying. Many communication parameters are possible. For example one of the communication parameters can be the above mentioned Miller parameter MP. If communication is according to Gen2 Spec v.1.1.0 then the Miller parameter MP coincides with the Miller parameter M defined in that version.

Another possible communication parameter whose value is thus established can be the backscatter link frequency designated as LF or BLF. In communication protocols that are consistent with the Gen2 Spec v.1.1.0 in that regard the BLF can assume values between 40 kHz and 640 kHz.

Another communication parameter whose value can thus be established can be a true false value of whether or not a pilot tone will also be backscattered. For example one of the communication parameters can include a pilot tone indication which indicates whether or not one of the replies should be preceded by a pilot tone. In those cases the true false value can be the pilot tone indication. Accordingly one of the backscattered replies can be preceded by a pilot tone or not in accordance with the pilot tone indication. In some protocols the true false value is a parameter TRextend which can be defined consistently with the TRext of the Gen2 Spec v.1.1.0 in that regard.

One more possible communication parameter whose value is thus established can relate to the duration of symbols. For example the inventorying commands from the reader can be encoded in terms of at least a first symbol for data 0 and a second symbol for data 1. So in some embodiments one of the communication parameters can indicate the duration of the first or the second symbol. In some embodiments one of the communication parameters can indicate a ratio of durations between the first and the second symbols.

These communication parameters can be established in any number of ways. In many embodiments they are communicated by the reader to the tag according to the applicable protocol. For example they can be either in a preamble or in an explicit command. These communication parameters are used by either the commands ultimately transmitted by a reader as will be explained with reference to operation or by the replies backscattered by the tags as will be explained with reference to operation or both.

One time that operation is executed can be considered a first time where a first set of such values becomes established for these communication parameters. Another subsequent such time that operation is executed can be considered a second time where a second or updated set of such values becomes established.

At next operation inventorying commands are caused to be transmitted for inventorying the RFID tags. The commands are ultimately transmitted by a reader system and can be as per the applicable protocol. One time that operation is executed can be considered a first time causing first such inventorying commands to be transmitted. Another subsequent such time that operation is executed can be considered a second time causing second such inventorying commands to be transmitted.

At next operation responsive to the inventorying commands of the previous operation replies are received which are backscattered from some of the RFID tags in the population. One time that operation is executed can be considered a first time causing first such replies to be received. Another subsequent such time that operation is executed can be considered a second time causing second such replies to be received.

At optional next operation it is considered whether frequency channel or the antenna should be switched. As mentioned above a reader may hop on to a new channel as possibly required by regulations and implemented by portions of its programmed algorithm. In addition a reader might start using a different antenna e.g. one of antennas shown in as implemented by portions of its programmed algorithm. If so then at optional next operation a new channel is hopped on to or a new antenna is transmitted out of.

Operation may be performed or not. Then execution can continue for example by transferring to operation or or next optional operation and so on. Plus if operation is not performed then execution can proceed to next optional operation .

At optional next operation it is determined whether to change a value of one or more of the communication parameters that were established at operation . The determination may be made in any number of ways some of which are described later in this document. Plus operation is optional in that it need not be performed strictly speaking. Changing the parameter value may be caused automatically i.e. without requiring a determination or not at all. If at operation it is determined that no values are to change then execution can return to operation .

If at operation the value of even one of these parameters is to change then the whole set of applicable values can be considered that it is to change. In other words the whole set is considered to be adjusted even if most of its values will remain the same. Then execution can return to optional operation to maybe reset the filters then to operation to cause the updated parameter values to become established and then to operation . Plus the new values can be preset or can be determined from attributes of the backscattered replies that were received at operation .

Accordingly in flowchart execution may loop around a number of times. Each next time the same or different communication parameter values can be established per operation then inventorying commands may be transmitted per operation and replies received per operation . Of those either or both of the commands and the replies can take place using the latest communication parameter values.

In embodiments where execution loops to repeat operations the antenna may or may not have been switched for multiple repetitions. In other words in some embodiments there is transmission out of a single antenna without having transmitted out of another. Moreover the frequency channel may or may not have been switched. In other words in some embodiments there is transmission in a single channel without having transmitted in another.

This principle can then be used for inventorying a population of RFID tags that exhibit the behavior of curve . In other words tags can be read using different values for the communication parameters.

In some optional embodiments with each next pass of flowchart one or more of the tags that have already been inventoried are not addressed again for reading. Preferably but not necessarily all of the tags that have already been inventoried are not addressed again for reading. Such embodiments are preferred if the time to read is limited and each next pass is slower due to the increased tag read sensitivity.

Preventing tags from being read again in the subsequent pass can be accomplished in any number of ways with proper selection of commands. For example the inventorying commands can be suitable for continuing inventorying at least some those of the RFID tags in the population that have not replied yet but not one or more or all of those that have. In some embodiments this is accomplished while continuously powering the tags in the population i.e. powering them from the first and the second inventorying commands and causing them to not lose power during a transition between the first and the second inventorying commands.

In some embodiments sessions are used for inventorying. For example v.1.1.0 of the Gen2 Spec defines sessions S0 S1 S2 and S3. Embodiments can use sessions defined consistently with these sessions even if a different version or a different protocol is being used. For example the first inventorying commands can be transmitted while a current session has been established. The current session has been selected from one of available sessions S0 S1 S2 and S3 which are defined consistently with respective sessions S0 S1 S2 and S3 that are defined in the Gen2 Spec v.1.1.0. A certain RFID tag can include a current session flag for the current session. This session flag can be capable of having one of two states A and B and the state can be flipped as the certain RFID tag becomes inventoried by the first inventorying commands. This defines the certain RFID tag to be in the first subgroup. Then the second inventorying commands can be transmitted without having caused the current session flag to be further changed from when it was thus flipped during the subsequent transition between the first inventorying commands and the second inventorying commands. This way the certain tag of the first subgroup will become inventoried as part of the first subgroup and will be kept from participating also in the second subgroup.

An algorithm according to can result in improved performance for reading the tags. This is illustrated below.

As will be appreciated tag read sensitivity line can remain above curve for all tags NT. As such it is plotted in bold typeface to be better understood in relation to the earlier described horizontal lines and .

As such reading according to the operations of can be faster. Referring to according to comment all tag data has been received which is better performance than is shown in . In addition they have been received faster than time T which is faster than for the algorithm of and sometimes critical if there is a problematic time constraint like one is shown in .

Each one of sets can thus be accumulated as corresponding to a different horizontal segment of tag read sensitivity line . Line is shown as having a total of five horizontal segments each at increasing sensitivity. Of these the first one reads up to tag N the second up to tag N and so on. Depending on the population different numbers of segments will be needed before there is high confidence that the entire population has been read. In some instances this confidence is attained after a horizontal segment of a high enough sensitivity returns no more tags.

In addition the shown horizontal segments need not be implemented as shown in the example of . For example the first horizontal segment reading up to tag N could be preceded by an earlier segment which we shall call zeroth segment only to preserve the numbering sequence. Accordingly commands can be sent with parameters corresponding to that segment with or without receiving corresponding replies. Even if replies are received then the first segment can be done repeating or not the tags that already replied.

Each one of sets can be accumulated with a different iteration of . Attention is now drawn to transitions which are the points between iterations. These transitions can have different time durations.

Referring to transitions of can happen at operation or automatically etc. As shown in the example of B it is suggested that these transitions occur only when all tags of a subgroup that could be read have indeed been read and where if line were to continue extending horizontally it would move under curve . Indeed transitions can occur upon exhausting the tags that can be read at the current sensitivity parameters but that is not necessary. In some embodiments these transitions can occur prior to so exhausting at operation of .

Examples are now described for performing optional operation . In all examples a determination is made whether or not to change parameters and execution proceeds as shown in flowchart in accordance with the determination.

As already mentioned the second set of values can be caused to be established before detecting that there are no more first replies. In fact in some embodiments it can be caused to be established while first replies would still be expected.

At next operation it is determined whether or not the first replies do not account for the entire population estimate. In these embodiments the second set of values can be caused to be established responsive to determining that the first replies do not account for the entire population estimate.

Numerous details have been set forth in this description which is to be taken as a whole to provide a more thorough understanding of the invention. In other instances well known features have not been described in detail so as to not obscure unnecessarily the invention.

The invention includes combinations and subcombinations of the various elements features functions and or properties disclosed herein. The following claims define certain combinations and subcombinations which are regarded as novel and non obvious. Additional claims for other combinations and subcombinations of features functions elements and or properties may be presented in this or a related document.

