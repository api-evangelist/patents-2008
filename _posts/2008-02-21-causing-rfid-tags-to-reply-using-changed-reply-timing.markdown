---

title: Causing RFID tags to reply using changed reply timing
abstract: RFID reader systems, readers, components, software and methods cause RFID tags to reply using changed reply timing. In a number of embodiments, this timing change is achieved by causing a custom timing command to be transmitted to a tag. In some embodiments, the changed reply timing affects an amount of delay before a tag backscatters a reply.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08072327&OS=08072327&RS=08072327
owner: Impinj, Inc.
number: 08072327
owner_city: Seattle
owner_country: US
publication_date: 20080221
---
This application claims priority from U.S. Provisional Application No. 60 902 745 filed on Feb. 21 2007 the disclosure of which is hereby incorporated by reference for all purposes.

This application claims priority from U.S. Provisional Application No. 61 005 232 filed on Dec. 4 2007 the disclosure of which is hereby incorporated by reference for all purposes.

This application may be found to be related to U.S. patent application Ser. No. 12 035 393 by the same inventors titled RFID TAGS REPLYING USING CHANGED REPLY TIMING filed by the same assignee on the same day as the instant application.

The present description is about Radio Frequency IDentification RFID systems and more specifically for systems where RFID tags reply to readers using changed reply timing.

Radio Frequency IDentification RFID systems typically include RFID tags and RFID readers. RFID readers are also known as RFID reader writers or RFID interrogators. RFID systems can be used in many ways for locating and identifying objects to which the tags are attached. RFID systems are particularly useful in product related and service related industries for tracking objects being processed inventoried or handled. In such cases an RFID tag is usually attached to an individual item or to its package.

In principle RFID techniques entail using an RFID reader to interrogate one or more RFID tags. The reader transmitting a Radio Frequency RF wave performs the interrogation. The RF wave is typically electromagnetic at least in the far field. The RF wave can also be predominantly electric or magnetic in the near field.

A tag that senses the interrogating RF wave responds by transmitting back another RF wave. The tag generates the transmitted back RF wave either originally or by reflecting back a portion of the interrogating RF wave in a process known as backscatter. Backscatter may take place in a number of ways. In addition tags usually have prescribed reply timings for replying by backscattering.

The reflected back RF wave may further encode data stored internally in the tag such as a number. The response is demodulated and decoded by the reader which thereby identifies counts or otherwise interacts with the associated item. The decoded data can denote a serial number a price a date a destination other attribute s any combination of attributes and so on.

An RFID tag typically includes an antenna system a radio section a power management section and frequently a logical section a memory or both. In earlier RFID tags the power management section included an energy storage device such as a battery. RFID tags with an energy storage device are known as active or semi active tags. Advances in semiconductor technology have miniaturized the electronics so much that an RFID tag can be powered solely by the RF signal it receives. Such RFID tags do not include an energy storage device and are called passive tags.

Briefly the present invention provides RFID reader systems readers components software and methods for causing RFID tags to reply using changed reply timing. In a number of embodiments this timing change is achieved by causing a custom timing command to be transmitted to a tag. In some embodiments the changed reply timing affects an amount of delay before a tag backscatters a reply.

The present invention also provides RFID tags and chips for RFID tags that are capable of replying using changed reply timing. In a number of embodiments this timing change is achieved when a tag receives a custom timing command from an RFID reader. In some embodiments the changed reply timing affects an amount of delay before a tag backscatters a reply.

The invention offers the advantage that some tags can be processed differentially from others which can improve the functionality of a whole RFID system that processes RFID tagged items. Additionally the fact that the tags can actually perform the feature can serve as a verification criterion that the tags are not counterfeit. Moreover some embodiments can enhance the privacy of the owners of items tagged with such tags.

These and other features and advantages of the invention will be better understood from the specification of the invention which includes the following Detailed Description and accompanying Drawings.

The present invention is now described. While it is disclosed in its preferred form the specific embodiments of the invention as disclosed herein and illustrated in the drawings are not to be considered in a limiting sense. Rather these embodiments are provided so that this disclosure will be thorough and complete and will fully convey the scope of the invention to those skilled in the art. Indeed it should be readily apparent in view of the present description that the invention may be modified in numerous ways. Among other things the present invention may be embodied as devices methods software and so on. Accordingly the present invention may take the form of an entirely hardware embodiment an entirely software embodiment an entirely firmware embodiment or an embodiment combining aspects of the above. This description is therefore not to be taken in a limiting sense.

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

In addition a protocol can be a variant of a stated specification such as the Gen2 Spec for example including fewer or additional commands than the stated specification calls for and so on. In such instances additional commands are sometimes called custom commands.

A driver can send to its respective antenna a driving signal that is in the RF range which is why connector is typically but not necessarily a coaxial cable. The driving signal causes the antenna to transmit an RF wave which is analogous to RF wave of . In addition RF wave can be backscattered from the RFID tags analogous to RF wave of . Backscattered RF wave then ultimately becomes a signal sensed by unit .

Unit also has other components such as hardware and or software and or firmware which may be described in more detail later in this document. Components control drivers and as such cause RF wave to be transmitted and the sensed backscattered RF wave to be interpreted. Optionally and preferably there is a communication link to other equipment such as computers and the like for remote operation of system .

Local block is responsible for communicating with the tags. Local block includes a block of an antenna and a driver of the antenna for communicating with the tags. Some readers like that shown in local block contain a single antenna and driver. Some readers contain multiple antennas and drivers and a method to switch signals among them including sometimes using different antennas for transmitting and for receiving. And some readers contain multiple antennas and drivers that can operate simultaneously. A demodulator decoder block demodulates and decodes backscattered waves received from the tags via antenna block . Modulator encoder block encodes and modulates an RF wave that is to be transmitted to the tags via antenna block .

Local block additionally includes an optional local processor . Processor may be implemented in any number of ways known in the art. Such ways include by way of examples and not of limitation digital and or analog processors such as microprocessors and digital signal processors DSPs controllers such as microcontrollers software running in a machine such as a general purpose computer programmable circuits such as Field Programmable Gate Arrays FPGAs Field Programmable Analog Arrays FPAAs Programmable Logic Devices PLDs Application Specific Integrated Circuits ASIC any combination of one or more of these and so on. In some cases some or all of the decoding function in block the encoding function in block or both may be performed instead by processor .

Local block additionally includes an optional local memory . Memory may be implemented in any number of ways known in the art. Such ways include by way of examples and not of limitation nonvolatile memories NVM read only memories ROM random access memories RAM any combination of one or more of these and so on. Memory if provided can include programs for processor to run if provided.

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

In some embodiments a first command is caused to be transmitted to the RFID tag. The first command is of course encoded in an electromagnetic wave such as wave according to a communication protocol. Such protocols specify a number of such commands and any such command can be considered to be the first command. Such commands can include for example command requesting a handle such as a random number or a more identifying number such as a TID or an EPC. A number of additional possible first commands are also described below in more detail but that is only for example and not for limitation.

In some embodiments a backscattered first reply is received from the tag responsive to the first command having been transmitted. A reply to the first command can be considered as the first reply for purposes of this document. The first reply uses a first reply timing as the reply timing and such tag reply timings are described in more detail later in this document.

The first command can be sent to a tag that has been singulated from a tag population. In other instances the tag has not yet been singulated.

In one class of examples the first command can be any of the commands issued in an exchange for commissioning a tag where data is written in its memory and an acknowledging reply is backscattered. It is known therefore that a tag that has been commissioned has received such a first command and has replied to it.

In some embodiments at optional operation an identifying reply is received as the first reply. These embodiments are preferably where the first command is operation . Again if operation is not performed the first reply can be considered any other reply that a reader has done with a tag.

Operation of flowchart is now described. While the description of operation is somewhat out of turn for the flow of flowchart it is presented at this point in the document so that the description of the additional optional operations of flowchart taking place before operation will make sense.

At operation a custom timing command is caused to be transmitted to the tag after receiving the first reply. In response to receiving the custom timing command when the tag later backscatters a second reply that second reply uses a second reply timing that is different from the first reply timing. Again examples of such second replies and such second reply timings are described in more detail later in this document.

It will be appreciated that operation may be performed either by the same reader as the one that transmitted the first command or by a different reader. In either case the tag may or may not have lost power after backscattering the first reply and before receiving the custom timing command. In embodiments where a reader processes a tag that has already been commissioned operation takes place. In addition a first command may or may not have been transmitted. If it has been then it may or may not be operation .

The custom timing command can be generated in any number of ways. For example it can be automatic or triggered by any number of events. Or an instruction can be received by one of the modules of and be obeyed. In some embodiments where operation has taken place the instruction can be generated and received responsive to parsing the identifying reply. In such instances for example it can be discerned from the identifying reply that the tag supports the custom timing command and the instruction is thus generated. Then bits can be received or looked up from a table stored in a memory and so on. These bits can be prepared into one or more packets for transmission and so forth.

In some embodiments the tag is able to backscatter the second reply using the second reply timing regardless of what state it is in at the time it receives the custom timing command of operation .

In other embodiments the tag can have two states namely an enabled state and a disabled state as will be described in more detail later in this document. Briefly if the tag is in the enabled state it can operate as per the above. But if the tag is in the disabled state if it were to receive the custom timing command the second reply timing would not be different from the first reply timing even if it backscattered the second reply.

In embodiments of the latter case at an optional next operation an Enable command can be caused to be transmitted while the tag is in the disabled state. In some instances this would cause the tag to transition internally to the enabled state. In some instances the Enable command can be the first command described above. In these cases therefore the second reply timing is different from the first reply timing responsive to receiving the custom timing command while the tag is in the enabled state.

An optional operation can take place after operation . According to operation a Disable command can be caused to be transmitted to the tag while the tag is in the enabled state. This can cause the tag to transition internally to the disabled state.

As will be realized commands can be configured in any number of ways. For example if Enable command is provided it can be separate from custom timing command . Preferably these are configured as separate standalone commands each occurring at a single one of the communication sessions such as those of time interval of . In addition the tag need not backscatter a reply to any one of them individually.

In addition command plus optionally commands and may be used among other commands that will be transmitted to the tag in question and possibly other tags. Equally the optional first and second replies will be among other replies backscattered by the tag in question and possibly other tags.

In some embodiments a reader system component can perform a method according to flowchart to communicate with a single tag. This can be accomplished if the tag is the only one in its field of view. Or the tag in question can be within a population of tags but it has been singulated. This means that the tag in question is the only one from the population that replies to the reader.

In other embodiments a reader component can perform a method according to flowchart to communicate with more than one tag. For example custom timing command can be transmitted to a population of tags intending that they each backscatter a second reply using the second reply timing either together or at different times or in response to subsequent commands.

In yet other embodiments combinations are possible. For example Enable command might be sent to a population of tags before one of them is singulated. Then custom timing command might be sent to a tag that has been singulated or to whole the population of tags.

Each one of commands can be constructed in any number of ways. In some instances they can be considered as custom commands as not being specified in a particular communication protocol. In some instances they would be standalone commands made by a sequence of bits chosen so that they do not conflict with other commands of the protocol. In other instances they can be commands with a custom payload. Such commands can be known to the protocol or not and the payload can be used to distinguish among different custom commands and optionally further transfer a parameter for the commands.

When commands are used that are known to the protocol a section of their payload can be advantageously used for the purpose of implementing a custom command such as commands . For example it can be an enable payload a disable payload etc. Such a section in the payload can be a mask field according to embodiments. For the Gen2 Spec two such commands are the Select command and the BlockWrite command. Between these two candidate commands it should be considered that the Select command can be transmitted before or after a tag is singulated out of its population while the BlockWrite is better suited for singulated tags. In addition the BlockWrite command is optional to the Gen2 Spec and the tag would probably have to have a controller that can accept it.

Each one of commands can thus be constructed as an implementation of this Select command or the BlockWrite command. In addition to responding to the payload implementing the custom command the tag may further or may not also respond to the underlying Select command or BlockWrite command. An example is now described in terms of the Select command but would apply equally to the BlockWrite command.

The Feature Enabling Field FEF enables the tag to verify that it is a proper recipient for the command by comparing the transmitted FEF value against a value in Membank. In this case Membank can be EPC TID or USER memory. As can be seen the FEF can be further partitioned into subfields for better clarity. Such subfields can include a Class Identifier the MDID and an Indicator Bit.

The Class Identifier can be two bits. For example EPCglobal can correspond to a value of 10. This would allow the custom command to apply for example only to EPCglobal tags.

The MDID is the tag manufacturer s ID which is stored in the tag s TID memory. For Impinj tags this number is 000000000001 or 100000000001. The MDID allows a reader to select tags of only the manufacturer of interest. So even if this Select command is transmitted and received before singulation the Select command can select also according to the tag manufacturer s ID. This will cause the manufacturer s tags to be selected and thus the reader can ensure prior knowledge of the tag manufacturer s identification.

The Indicator Bit can be set to 0 or 1. In the Gen2 spec a tag model number follows the MDID. A bit of this model number can serve as the Indicator Bit and can be interpreted as follows If it is 0 the tags can interpret the command as an ordinary Select and execute it per the Gen2 spec. Else if it is 1 the tags can interpret the Select command as a custom instruction and execute according to the FCF.

The Feature Command Field FCF can have a command code that indicates the number of the custom instruction. For example a command code of 00000 could be the custom timing command. This permits 31 possible custom commands. In addition a command code of 11111 could indicate an extended command code that extends into the subsequent data field.

The data field can contain data needed to implement the custom instruction if any. Not all commands will use it. The data field can be variable in size. Its meaning will derive from the command codes.

In some embodiments the tag may ignore the Target and Action field in the Select command depending on whether these fields are relevant to the CI. In other embodiments the tag may also set the appropriate flag.

In preferred embodiments the entire Select command must be valid for the tag to accept and execute the custom command. That means valid values for Membank Length Pointer Mask CRC 16 etc. An example is now described.

Everything described above in terms of readers and reader components finds some correspondence with tags and tag chips. In some instances some of the above also describe features and behavior of tag chips.

Circuit includes at least two antenna connections which are suitable for coupling to one or more antenna segments not shown in . Antenna connections may be made in any suitable way such as using pads and so on. In a number of embodiments more than two antenna connections are used especially in embodiments where more antenna segments are used.

Circuit includes a section . Section may be implemented as shown for example as a group of nodes for proper routing of signals. In some embodiments section may be implemented otherwise for example to include a receive transmit switch that can route a signal and so on.

Circuit also includes a Power Management Unit PMU . PMU may be implemented in any way known in the art for harvesting raw RF power received via antenna connections . In some embodiments PMU includes at least one rectifier and so on.

In operation an RF wave received via antenna connections is received by PMU which in turn generates power for components of circuit . This is true for either or both R T and T R sessions whether or not the received RF wave is modulated.

Circuit additionally includes a demodulator . Demodulator demodulates an RF signal received via antenna connections . Demodulator may be implemented in any way known in the art for example including an attenuator stage an amplifier stage and so on.

Circuit further includes a processing block . Processing block receives the demodulated signal from demodulator and may perform operations. In addition it may generate an output signal for transmission.

Processing block may be implemented in any way known in the art. For example processing block may include a number of components such as a processor memory a decoder an encoder and so on.

In a number of embodiments processing block includes a state machine . State machine retains the state of the tag at least while circuit is powered. The state of the tag dictates which of the subsequently received commands the tag would respond to and how and so on. State machine can be as is called for in the specified communications protocol and adapted to further accommodate the custom timing command with or without contradicting the operation of the protocol.

Circuit additionally includes a modulator . Modulator modulates an output signal generated by processing block . The modulated signal is transmitted by driving antenna connections and therefore driving the load presented by the coupled antenna segment or segments. Modulator may be implemented in any way known in the art for example including a driver stage amplifier stage and so on.

In one embodiment demodulator and modulator may be combined in a single transceiver circuit. In another embodiment modulator may include a backscatter transmitter or an active transmitter. In yet other embodiments demodulator and modulator are part of processing block .

Circuit additionally includes a memory which stores data . Memory is preferably implemented as a Nonvolatile Memory NVM which means that data is retained even when circuit does not have power as is frequently the case for a passive RFID tag.

As already mentioned above in some embodiments the custom timing command works only when the tag is in an enabled state as opposed to a disabled state. An example is now described.

In some embodiments enabled state and disabled state are provided in a way that does not define additional states in the underlying protocol. For example for the Gen2 Spec the initial Ready state can be a disabled state while one or more of the other states can be enabled states . Or some of the other states can also be disabled state .

In other embodiments either one or both of enabled state and disabled state can be provided as states different from and in addition to what is required by the Gen2 Spec. It should be remembered however that the invention may also be practiced with embodiments where the tag is always enabled to respond appropriately to the custom timing command by changing its reply timing and has no disabled state.

Methods for RFID tags and tag chips are now described. These methods may be practiced by different embodiments including but not limited to the tag embodiments described above. Such methods may be performed by a number of tags concurrently or by a single tag alone in a field of view or singulated from a population as has already been described above. In addition it will be recognized that such methods will be performed largely in response to reader methods such as those of flowchart .

In some embodiments a first command is received from an RFID reader. This would be the first command described above as having been transmitted towards the tag.

Then a first reply is backscattered optionally by the tag responsive to receiving the first command. The first reply can be any reply specified by an applicable protocol for the first command. The first reply uses a first reply timing which is typically a reply timing specified by the protocol but can be any other reply timing.

According to optional operation a command to identify is received which is the command caused to be transmitted at optional operation . In some embodiments the command to identify can be considered to be the above mentioned first command.

At optional operation an identifying reply is backscattered in response to the command which is the reply received at operation . The identifying reply can be for example a random number an Electronic Product Code EPC a TID or other code stored in memory that identifies the tag or item it is attached to or its capabilities to change its reply timing. In some embodiments the identifying reply can be considered to be the above mentioned first reply.

Operation of flowchart is now described. While the description of operation is somewhat out of turn for the flow of flowchart it is presented at this point in the document so that the description of the additional optional operations of flowchart taking place before operation will make sense.

At operation a custom timing command is received by the tag. The custom timing command is as described elsewhere in this document. Operation may be performed either at the same time as receiving the first command or at a different time e.g. by a different reader. For example the first command may be received at a time that the tag is commissioned while the custom timing command may be received months or years later. In such cases the tag may have lost power after backscattering the first reply and before receiving the custom timing command. In other instances operation takes place during the same exchange as receiving the first command without even losing power.

At a later operation the tag backscatters a second reply which uses a second reply timing. The second reply timing is different from the first reply timing of the first reply because the custom timing command has been received. This can be accomplished by the tag making appropriate internal adjustments in operating its modulator. In addition some of these adjustments may involve setting an internal flag adjusting an internal state machine and so on.

In some embodiments the second reply is backscattered in response to receiving the custom timing command. In other embodiments one or more intervening commands are received after the custom timing command and the second reply is backscattered in response to receiving the one of these intervening commands.

In some embodiments the reply timing is changed by the custom timing command only for the second reply and the tag then reverts to using the first reply timing. In other embodiments the reply timing is changed for more than one of the subsequent replies. For example the tag could then receive a third command and backscatter a third reply with the third reply using a third reply timing different from the first reply timing. The third reply timing could be the same as or different than the second reply timing.

The effect of the custom timing command may or may not survive an interim loss of power after the custom timing command is received. In some embodiments the reply timing is changed permanently while in others if power is lost the tag will reset to replying using the first reply timing.

As also mentioned above in some embodiments the tag is able to backscatter the second reply using the second reply timing regardless of what state it is in at the time it receives the custom timing command according to operation . In other optional embodiments the tag can have two states namely an enabled state and a disabled state as described with reference to .

At optional operation the tag can receive an Enable command such as the one transmitted at operation . At next operation the tag transitions internally to enabled state . This can be done in preparation of operation when the custom command is received.

At optional operation the tag can receive a Disable command such as the one transmitted at operation . At next operation the tag transitions internally back to disabled state . This can be done after operation to cause the tag to revert to using the first reply timing in its further replies. The Disable command is not necessary to be implemented. For example the tag could be automatically disabled after the second reply or after a few replies or upon reverting to another one of the specified states such as the Ready state of the Gen2 spec.

In addition in the event that any of the received commands such as the custom timing command the Enable command and the Disable command are implemented by the Select command of the tag can respond properly to it in addition to what is described with reference to the reply timings. For example the tag can set or unset an internal selected flag and so on. Plus the tag may or may not issue a reply since the Select command does not call for a reply. But it might in a custom embodiment.

The reply timing can be changed in many different ways as will be evident to a person skilled in the art in view of the present description. In many such embodiments the reply timing is a delay before the tag starts backscattering after receiving its most recent command namely the command it is responding to. This works at least in the Gen2 Spec which calls for the vast majority of tag replies to be received within a specified time window after finishing transmitting a command. Accordingly readers may have a time window during which to receive tag replies. Changing the delay may thus cause the tag reply to fall outside the window of readers that do not know better as would be unauthorized readers. As such practicing embodiments of the invention could increase privacy. Examples are now given.

Diagram shows an other command which finishes being transmitted at the same time T for comparison only with that of diagram . Diagram also shows a second reply backscattered in response to other command and which starts being transmitted at time T. The most recent command for second reply has thus been other command and thus second reply is has the second delay between times T and T.

The reply timing has changed from diagram to diagram because the delay up to T is different than the delay up to T by an amount DT. It should be noted that in this example the delay up to T is longer than that up to T although that need not be the case. In fact it could be the other way around. The changed reply timings can be used to enhance the privacy of using the tag by making it harder to read by unauthorized readers.

Other command could be either the custom timing command or a command that intervenes being sent after the custom timing command. In fact the custom timing command itself could call for no reply at all.

In addition second reply encodes the same functional content as first reply . In other words second reply does the same function as first reply except that it is subject to a different delay. This can be accomplished in a number of ways. For example second reply can be identical to first reply having the same bits. Or the bits can be substantially similar from what they would be with only a few added or changed for further preventing second reply from being read by unauthorized readers. Or the bits can be totally different but still accomplish the same function.

A Tune command is caused to be transmitted by the reader and received by the tag. Tune command can be any convenient command such as the first command the custom timing command or other command in the communication. Tune command encodes a time indicating parameter. The time indicating parameter can be encoded as data in the FCF subfield shown in . The second reply timing is thus determined from the time indicating parameter. In an embodiment of a reader component the time indicating parameter can be looked up from a desired value for the second reply timing.

In the example of the time indicating parameter is a two bit field code . Here it is shown with the possible values it can take. Each value results in a different delay DT namely one of DT DT DT and DT. These values for delay DT can optionally be used in embodiments of the invention such as those of . The delay DT can be expressed in number of clock cycles in a number of RF cycles or in other units of time convenient for this purpose. Thus in one example delay DT can have values chosen among 4 msec 8 msec 12 msec and 16 msec. In addition such a delay should not be too long because then other communication may start taking place.

Numerous details have been set forth in this description which is to be taken as a whole to provide a more thorough understanding of the invention. In other instances well known features have not been described in detail so as to not obscure unnecessarily the invention.

The invention includes combinations and subcombinations of the various elements features functions and or properties disclosed herein. The following claims define certain combinations and subcombinations which are regarded as novel and non obvious. Additional claims for other combinations and subcombinations of features functions elements and or properties may be presented in this or a related document.

