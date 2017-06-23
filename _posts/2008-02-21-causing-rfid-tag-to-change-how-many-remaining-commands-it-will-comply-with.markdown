---

title: Causing RFID tag to change how many remaining commands it will comply with
abstract: RFID reader systems, readers, components, software and methods for causing a custom RFID tag to change how many remaining commands they will comply with. In a number of embodiments, this is achieved by causing a custom limiting command to be transmitted to the tag.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08446258&OS=08446258&RS=08446258
owner: Impinj, Inc.
number: 08446258
owner_city: Seattle
owner_country: US
publication_date: 20080221
---
This application claims priority from U.S.A. Provisional Application Ser. No. 60 902 746 filed on Feb. 21 2007 the disclosure of which is hereby incorporated by reference for all purposes.

This application claims priority from U.S.A. Provisional Application Ser. No. 60 933 222 filed on Jun. 5 2007 the disclosure of which is hereby incorporated by reference for all purposes.

This application may be found to be related to U.S. patent application Ser. No. 12 035 379 by the same inventors titled RFID TAG CHIPS AND TAGS COMPLYING WITH ONLY A LIMITED NUMBER OF REMAINING COMMANDS AND METHODS filed by the same assignee on the same day as the instant application.

The present description is about Radio Frequency IDentification RFID systems and more specifically for systems where RFID tags reply to readers only a limited number of times.

Radio Frequency IDentification RFID systems typically include RFID tags and RFID readers. RFID readers are also known as RFID reader writers or RFID interrogators. RFID systems can be used in many ways for locating and identifying objects to which the tags are attached. RFID systems are particularly useful in product related and service related industries for tracking objects being processed inventoried or handled. In such cases an RFID tag is usually attached to an individual item or to its package.

In principle RFID techniques entail using an RFID reader to interrogate one or more RFID tags. The reader transmitting a Radio Frequency RF wave performs the interrogation. The RF wave is typically electromagnetic at least in the far field. The RF wave can also be predominantly electric or magnetic in the near field.

A tag that senses the interrogating RF wave responds by transmitting back another RF wave. The tag generates the transmitted back RF wave either originally or by reflecting back a portion of the interrogating RF wave in a process known as backscatter. Backscatter may take place in a number of ways.

The reflected back RF wave may further encode data stored internally in the tag such as a number. The response is demodulated and decoded by the reader which thereby identifies counts or otherwise interacts with the associated item. The decoded data can denote a serial number a price a date a destination other attribute s any combination of attributes and so on.

An RFID tag typically includes an antenna system a radio section a power management section and frequently a logical section a memory or both. In earlier RFID tags the power management section included an energy storage device such as a battery. RFID tags with an energy storage device are known as active or semi active tags. Advances in semiconductor technology have miniaturized the electronics so much that an RFID tag can be powered solely by the RF signal it receives. Such RFID tags do not include an energy storage device and are called passive tags.

It is desired to have RFID systems with additional capabilities for improved functionality. For example there are concerns that tags will be counterfeited without authorization. In addition there are security concerns where tags have been attacked so as to unravel their on board passwords bit by bit.

Briefly the present invention provides RFID tags and chips for RFID tags that are capable of complying with only a limited number of remaining commands and methods. In a number of embodiments a counter is adjusted in association with receiving a command and complying with it. The tag complies until the counter reaches a limit and then it can stop complying.

The present invention further provides RFID reader systems readers components software and methods for causing such RFID tags to change how many remaining commands they will comply with. In a number of embodiments this is achieved by causing a custom limiting command to be transmitted to a tag.

RFID tags according to embodiments can thus become non compliant. Non compliance can be by the tags becoming quiet or performing other activities or performing nothing at all or performing only selected activities and so on. In some embodiments non compliance is permanent while in others it is temporary and or restorable.

An advantage of the invention is that this non compliance can help resist having a tag read successively by those who would unravel its password bit by bit. For example tags can be made with a very low remaining number of subsequent commands that will be complied with which will hamper the efforts of tag counterfeiters.

These and other features and advantages of the invention will be better understood from the specification of the invention which includes the following Detailed Description and accompanying Drawings.

The present invention is now described. While it is disclosed in its preferred form the specific embodiments of the invention as disclosed herein and illustrated in the drawings are not to be considered in a limiting sense. Rather these embodiments are provided so that this disclosure will be thorough and complete and will fully convey the scope of the invention to those skilled in the art. Indeed it should be readily apparent in view of the present description that the invention may be modified in numerous ways. Among other things the present invention may be embodied as devices methods software and so on. Accordingly the present invention may take the form of an entirely hardware embodiment an entirely software embodiment an entirely firmware embodiment or an embodiment combining aspects of the above. This description is therefore not to be taken in a limiting sense. The invention is now described in more detail.

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

One such protocol is called the Specification for RFID Air Interface EPC Radio Frequency Identity Protocols Class 1 Generation 2 UHF RFID Protocol for Communications at 860 MHz 960 MHz which is also colloquially known as the Gen2 Spec . The Gen2 Spec has been ratified by EPCglobal which is an organization that maintains a website at at the time this document is initially filed with the USPTO. Version 1.1.0 of the Gen2 Spec is hereby incorporated by reference in its entirety.

In addition a protocol can be a variant of a stated specification such as the Gen2 Spec for example including fewer or additional commands than the stated specification calls for and so on. In such instances additional commands are sometimes called custom commands.

Circuit includes at least two antenna connections which are suitable for coupling to one or more antenna segments not shown in . Antenna connections may be made in any suitable way such as using pads and so on. In a number of embodiments more than two antenna connections are used especially in embodiments where more antenna segments are used.

Circuit includes a section . Section may be implemented as shown for example as a group of nodes for proper routing of signals. In some embodiments section may be implemented otherwise for example to include a receive transmit switch that can route a signal and so on.

Circuit also includes a Power Management Unit PMU . PMU may be implemented in any way known in the art for harvesting raw RF power received via antenna connections . In some embodiments PMU includes at least one rectifier and so on.

In operation an RF wave received via antenna connections is received by PMU which in turn generates power for components of circuit . This is true for either or both R T and T R sessions whether or not the received RF wave is modulated.

Circuit additionally includes a demodulator . Demodulator demodulates an RF signal received via antenna connections . Demodulator may be implemented in any way known in the art for example including an attenuator stage an amplifier stage and so on.

Circuit further includes a processing block . Processing block receives the demodulated signal from demodulator and may perform operations. In addition it may generate an output signal for transmission.

Processing block may be implemented in any way known in the art. For example processing block may include a number of components such as a processor memory a decoder an encoder and so on. It may also include a counter as is described later in this document.

In a number of embodiments processing block includes a state machine . State machine retains the state of the tag at least while circuit is powered. The state of the tag dictates which of the subsequently received commands the tag would respond to and how and so on. State machine can be as is called for in the specified communications protocol and adapted to further accommodate a custom limiting command according to embodiments with or without contradicting the operation of the protocol.

Circuit additionally includes a modulator . Modulator modulates an output signal generated by processing block . The modulated signal is transmitted by driving antenna connections and therefore driving the load presented by the coupled antenna segment or segments. Modulator may be implemented in any way known in the art for example including a driver stage amplifier stage and so on.

In one embodiment demodulator and modulator may be combined in a single transceiver circuit. In another embodiment modulator may include a backscatter transmitter or an active transmitter. In yet other embodiments demodulator and modulator are part of processing block .

Circuit additionally includes a memory which stores data . Memory is preferably implemented as a Nonvolatile Memory NVM which means that data is retained even when circuit does not have power as is frequently the case for a passive RFID tag.

At operation a first command is received wirelessly from an RFID reader via an antenna. According to the communication protocol in use this first command calls for the tag to comply by performing a first operation or a set of operations that include the first operation. Examples of such operations are provided later in this document.

At optional next operation it is determined whether a counter has reached a preset limit. If not then at next operation the first command is not complied with. This non compliance can be by the first operation not being performed and possibly others of the operations not being performed. For example the first operation could be that a reply is backscattered but that does not happen. That reply could be a specific reply or a randomly generated reply.

At an optional further operation an Out Of Cycles reply can be backscattered to the first command. The Out Of Cycles reply indicates that the tag no longer responds. The Out Of Cycles reply can be backscattered every time only some of the times only the first time and so on.

If the counter had not reached its limit then at next operation the first command is complied with. In other words the tag performs the first operation and any other operations mandated by the first command.

At next operation the counter is adjusted to advance towards the limit. At this point it will be appreciated that the counter and the limit are merely a mechanism for limiting how many more commands the tag will comply with. Beyond that the tag is out of cycles as will be described in more detail.

The counter can be implemented in any number of ways. For example the counter can be adjusted by being incremented up to a limit or being decremented down to a limit. In some embodiments the counter can start with a positive value and be adjusted by being decremented down to a limit of zero which is also the example that will be used later in this document. The counter can be a single counter. Or there can be a combination of two or more counters with equal or different coefficients. One or more of these counters can be adjusted according to a deterministic process. Or according to a non deterministic process instead. For example the counter can permit only one decrement but that has to happen according to a condition that can be met at random and so on. In addition the counter can be implemented in any number of ways that are equivalent to the above as will be evident to a person skilled in the art in view of the present description.

Any one of the adjustments of operation can cause the counter to reach the limit in which case the decision at operation could be different. Once the limit is reached a flag can be set or a state machine can transition to a different state. Accordingly operation can be performed by checking the flag or a current state of the state machine.

In some embodiments the first command includes an attempted password as specified by the protocol. Examples include the Kill command which can kill a tag or the Access command which can access more sensitive functions of the tag. Such commands include an attempted password which the tag must deem valid before it complies with the command.

An optional operation can be performed within flowchart . If it is determined that the attempted password is valid flowchart can be performed as before. But if it is determined that the attempted password is not valid then the counter can be further adjusted as a penalty. Operation is useful if someone without authorization is trying to gain access to the sensitive functions of the tag and lacks the password that a legitimate owner would have for their protection.

The validity or not of the attempted password can be determined by checking the received bits of the attempted password as they correspond to respective bits of a password stored in tag memory. In addition the counter can be adjusted by an amount in relation to how many of the attempted password bits differ from their corresponding bits of the first password. This way someone who misses only one bit e.g. due to interference would be penalized by less than someone who attempts a password at random.

Operations and can be implemented in different orders according to embodiments. One such example is shown in as flowchart .

The operations of flowchart and others result in the tag having in some embodiments only a limited number of remaining commands it will comply with. Many examples are now described which tags according to embodiment may implement individually or in combination.

A horizontal behavior line shows what a prior art tag does. Namely according to a comment a tag replies to all commands as long as they are not themselves disabling commands like the Kill command. The number of remaining compliances is independent of how many commands are received and the tag can comply indefinitely. Here the sign of infinity is used as the intercept of behavior line to denote that the number of commands could be a very large one without compliance ever stopping.

A behavior line shows a behavior of a sample tag made according to embodiments. The tag starts with an initial number of remaining compliances NC before having received any commands. With each command that is then received and complied with behavior line is decremented by one. Decrementing may take place using the above described counter. After a limited number of commands NF behavior line drops down to zero. According to a comment the tag then stops complying with commands received after that.

In the example of behavior line is decremented by one for every command received. This is a specific example of a case where the counter is adjusted by the same amount for all commands. As such NF is equal to NC or a number very close to it. This need not be the case. For example different commands can result in different adjustments. Two examples are now given.

In some instances of the above examples when a tag receives a first command shown as an intercept in the horizontal axis either it complies with it and adjusts the counter or it does not comply with it depending on whether the counter had reached the limit by prior such adjusting.

As will be seen in the examples of behavior lines lack of compliance can continue for at least some more of the commands received afterwards. This lack of compliance can be specific to some commands or indiscriminately to all subsequently received commands.

In a number of embodiments not complying can include that the tag no longer performs the first operation even when called for by subsequent commands. That first operation could be backscattering a reply transitioning to a certain state and so on. But it could perform other operations or comply with other commands.

In a number of embodiments not complying can include that the tag no longer complies with subsequent commands even if they are different than the first command and or call for an operation to be performed that is different than the first operation. In some of these embodiments the tag has been killed. In others this lack of compliance is temporary and a later received command is indeed complied with even if it is the same as the first command.

The temporary lack of compliance can be implemented by resetting the counter to an updated value or temporarily reversing how the counter counts or equivalently using a different counter and so on. This updated value could be determined in any number of ways. For example it could be determined at random or from a preset initial value stored in tag memory.

In some embodiments the counter is reset because it has reached the limit and then a suitable intervening number of commands have since then been received. An example is now described.

In behavior line the pause can be implemented by the tag. For example the tag can include a pause counter counter after which the first counter is reset to the limit NC.

In other embodiments compliance stops and can be restored by the reader instead. An example is now described.

There are a number of ways of implementing the Restore command. For example it may be implemented with a restore password and be obeyed only if it also encodes the valid restore password. The restore password can be a separate password or derived from other passwords stored on the tag such as an access password or a kill password. In addition the Restore command can include a value from which the updated value is determined for resetting the counter. Other such ways are described later in this document.

In some embodiments the counter is reset responsive to receiving a reset command. Importantly a Reset command can be implemented before the tag has reached the end of its compliance. An example is now described.

In some embodiments not only the counter is reset but also the manner of how the counter is adjusted. As will be seen in the example of behavior line starts with the profile of behavior line but it continues with the profile of behavior line responsive to the Reset command.

In some optional embodiments an Inquire command is received by the tag as part of a custom limiting command subset. If the counter had not been reached the limit a reply can be backscattered that indicates a state of the counter with respect to the limit. This way a reader will know when to send the Reset command for maximum effect.

In some embodiments the whole feature of limiting the number of compliances is disabled. An example is now described.

Disabling the feature can be implemented in any number of ways. For example the counter can be disabled or be no longer adjusted or no longer be paid any attention as to whether it reached or exceeded the limit and so on.

In some embodiments a tag starts without the feature of limiting the number of compliances but then that feature is enabled. An example is now described.

A driver can send to its respective antenna driving signal that is in the RF range which is why connector is typically but not necessarily a coaxial cable. The driving signal causes the antenna to transmit an RF wave which is analogous to RF wave of . In addition RF wave can be backscattered from the RFID tags analogous to RF wave of . Backscattered RF wave then ultimately becomes a signal sensed by unit .

Unit also has other components such as hardware and or software and or firmware which may be described in more detail later in this document. Components control drivers and as such cause RF wave to be transmitted and the sensed backscattered RF wave to be interpreted. Optionally and preferably there is a communication link to other equipment such as computers and the like for remote operation of system .

Local block is responsible for communicating with the tags. Local block includes a block of an antenna and a driver of the antenna for communicating with the tags. Some readers like that shown in local block contain a single antenna and driver. Some readers contain multiple antennas and drivers and a method to switch signals among them including sometimes using different antennas for transmitting and for receiving. And some readers contain multiple antennas and drivers that can operate simultaneously. A demodulator decoder block demodulates and decodes backscattered waves received from the tags via antenna block . Modulator encoder block encodes and modulates an RF wave that is to be transmitted to the tags via antenna block .

Local block additionally includes an optional local processor . Processor may be implemented in any number of ways known in the art. Such ways include by way of examples and not of limitation digital and or analog processors such as microprocessors and digital signal processors DSPs controllers such as microcontrollers software running in a machine such as a general purpose computer programmable circuits such as Field Programmable Gate Arrays FPGAs Field Programmable Analog Arrays FPAAs Programmable Logic Devices PLDs Application Specific Integrated Circuits ASIC any combination of one or more of these and so on. In some cases some or all of the decoding function in block the encoding function in block or both may be performed instead by processor . Local block additionally includes an optional local memory . Memory may be implemented in any number of ways known in the art. Such ways include by way of examples and not of limitation nonvolatile memories NVM read only memories ROM random access memories RAM any combination of one or more of these and so on. Memory if provided can include programs for processor to run if provided.

In some embodiments memory stores data read from tags or data to be written to tags such as Electronic Product Codes EPCs Tag Identifiers TIDs and other data. Memory can also include reference data that is to be compared to the EPC codes instructions and or rules for how to encode commands for the tags modes for controlling antenna and so on. In some of these embodiments local memory is provided as a database.

Some components of local block typically treat the data as analog such as the antenna driver block . Other components such as memory typically treat the data as digital. At some point there is a conversion between analog and digital. Based on where this conversion occurs a whole reader may be characterized as analog or digital but most readers contain a mix of analog and digital functionality.

If remote components are indeed provided they are coupled to local block via an electronic communications network . Network can be a Local Area Network LAN a Metropolitan Area Network MAN a Wide Area Network WAN a network of networks such as the internet or a mere local communication link such as a USB PCI and so on. In turn local block then includes a local network connection for communicating with network .

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

Methods are now described more particularly according to embodiments. Such methods may be practiced by different embodiments including but not limited to RFID reader system components as described above. In addition individual operations of such methods may be practiced by different readers at different phases of the lifetime of an RFID tag with or without interruptions between them and so on.

At optional next operation an identifying reply is backscattered in response to the command to identify. The identifying reply can help the reader in identifying the tag or its manufacturer and therefore determine whether the feature of limiting the number of replies exists and therefore on whether to send or not the command of the next operation.

At next operation a custom limiting command is caused to be transmitted to the tag. The tag therefore changes the remaining number of compliances above and beyond an adjustment of the remaining number responsive to receiving the custom limiting command. The custom limiting command can be any one or any combination of the Restore Reset Disable and Enable commands. Such commands would be intermingled with other commands used to perform tag operations and work with tags in view of the declining number of compliances.

In some embodiments the Inquire command is caused to be transmitted. The received reply can be used to determine whether and when to send the custom limiting reply.

In the above a number of custom limiting commands were mentioned such as Restore Reset Inquire Disable Enable and so on. Such commands can be considered as custom commands by not being specified in a particular communication protocol.

Such custom commands can be constructed in any number of ways. In some instances they would be standalone commands made by a sequence of bits chosen so that they do not conflict with other commands of the protocol. In other instances they can be commands with a custom payload. Such commands can be known to the protocol or not and the payload can be used to distinguish among different custom commands and optionally further transfer a parameter for the commands.

When commands are used that are known to the protocol a section of their payload can be advantageously used for the purpose of implementing the custom command. For example it can be a custom limiting payload such as a restore payload a reset payload an inquire payload a disable payload an enable payload etc. Such a section in the payload can be a mask field according to embodiments. For the Gen2 Spec two such commands are the Select command and the BlockWrite command. Between these two candidate commands it should be considered that the Select command can be transmitted before or after a tag is singulated out of its population while the BlockWrite is better suited for singulated tags. In addition the BlockWrite command is optional to the Gen2 Spec and the tag would probably have to have a controller that can accept it.

Each one of the custom commands can thus be constructed as an implementation of this Select command or the BlockWrite command. In addition to responding to the payload implementing the custom command the tag may further or may not also respond to the underlying Select command or BlockWrite command. An example is now described in terms of the Select command but would apply equally to the BlockWrite command.

The Feature Enabling Field FEF enables the tag to verify that it is a proper recipient for the command by comparing the transmitted FEF value against a value in Membank. In this case Membank can be EPC TID or USER memory. As can be seen the FEF can be further partitioned into subfields for better clarity. Such subfields can include a Class Identifier the MDID and an Indicator Bit.

The Class Identifier can be two bits. For example EPCglobal can correspond to a value of 10. This would allow the custom command to apply for example only to EPCglobal tags.

The MDID is the tag manufacturer s ID which is stored in the tag s TID memory. For Impinj tags this number is 000000000001 or 100000000001. The MDID allows a reader to select tags of only the manufacturer of interest. So even if this Select command is transmitted and received before singulation the Select command can select also according to the tag manufacturer s ID. This will cause the manufacturer s tags to be selected and thus the reader can ensure prior knowledge of the tag manufacturer s identification.

The Indicator Bit can be set to 0 or 1. In the Gen2 Spec a tag model number follows the MDID. A bit of this model number can serve as the Indicator Bit and can be interpreted as follows If it is 0 the tags can interpret the command as an ordinary Select and execute it per the Gen2 Spec. Else if it is 1 the tags can interpret the Select command as a custom instruction and execute according to the FCF.

The Feature Command Field FCF can have a command code that indicates the number of the custom instruction. For example a command code of 00000 could be the custom timing command. This permits 31 possible custom commands. In addition a command code of 11111 could indicate an extended command code that extends into the subsequent data field.

The data field can contain data needed to implement the custom instruction if any. Not all commands will use it. The data field can be variable in size. Its meaning will derive from the command codes.

In some embodiments the tag may ignore the Target and Action field in the Select command depending on whether these fields are relevant to the CI. In other embodiments the tag may also set the appropriate flag.

In preferred embodiments the entire Select command must be valid for the tag to accept and execute the custom command. That means valid values for Membank Length Pointer Mask CRC 16 etc. An example is now described.

Numerous details have been set forth in this description which is to be taken as a whole to provide a more thorough understanding of the invention. In other instances well known features have not been described in detail so as to not obscure unnecessarily the invention.

The invention includes combinations and subcombinations of the various elements features functions and or properties disclosed herein. The following claims define certain combinations and subcombinations which are regarded as novel and non obvious. Additional claims for other combinations and subcombinations of features functions elements and or properties may be presented in this or a related document.

