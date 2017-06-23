---

title: Causing RFID tags to backscatter more codes
abstract: RFID reader systems, readers, components, software and methods for causing RFID tags to backscatter a combination made from at least portions of a first code and a second code stored in tag memory, without transmitting any commands in the interim. In a number of embodiments, therefore, a separate command does not have to be sent for also reading the second code, thereby saving time in inventorying the tags. Plus, the combination can enable reading tag codes during tag manufacturing that are not otherwise readily available to read in the field.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08174367&OS=08174367&RS=08174367
owner: Impinj, Inc.
number: 08174367
owner_city: Seattle
owner_country: US
publication_date: 20080430
---
This application claims priority from U.S. Provisional Application Ser. No. 60 932 699 filed on May 31 2007 the disclosure of which is hereby incorporated by reference for all purposes.

This application claims priority from U.S. Provisional Application Ser. No. 60 932 627 filed on May 31 2007 the disclosure of which is hereby incorporated by reference for all purposes.

This application claims priority from U.S. Provisional Application Ser. No. 61 005 249 filed on Dec. 4 2007 the disclosure of which is hereby incorporated by reference for all purposes.

This application may be found to have aspects in common with commonly assigned U.S. non provisional patent application Ser. No. 12 112 699 entitled RFID TAG CHIPS AND TAGS CAPABLE OF BACKSCATTERING MORE CODES AND METHODS and filed on the same day as the instant application by the same inventor.

The present description addresses the field of Radio Frequency IDentification RFID systems and more specifically to causing such systems to yield their data more expeditiously.

Radio Frequency IDentification RFID systems typically include RFID tags and RFID readers. RFID readers are also known as RFID reader writers or RFID interrogators. RFID systems can be used in many ways for locating and identifying objects to which the tags are attached. RFID systems are particularly useful in product related and service related industries for tracking objects being processed inventoried or handled. In such cases an RFID tag is usually attached to an individual item or to its package.

In principle RFID techniques entail using an RFID reader to interrogate one or more RFID tags. The reader transmitting a Radio Frequency RF wave performs the interrogation. The RF wave is typically electromagnetic at least in the far field. The RF wave can also be predominantly electric or magnetic in the near field. The RF wave may encode one or more commands that instruct the tags to perform one or more actions.

A tag that senses the interrogating RF wave responds by transmitting back another RF wave. The tag generates the transmitted back RF wave either originally or by reflecting back a portion of the interrogating RF wave in a process known as backscatter. Backscatter may take place in a number of ways.

The reflected back RF wave may further encode data stored internally in the tag such as a number. The response is demodulated and decoded by the reader which thereby identifies counts or otherwise interacts with the associated item. The decoded data can denote a serial number a price a date a destination other attribute s any combination of attributes and so on. Accordingly when a reader reads a tag code data can be learned about the associated item that hosts the tag and or about the tag itself.

An RFID tag typically includes an antenna system a radio section a power management section and frequently a logical section a memory or both. In earlier RFID tags the power management section included an energy storage device such as a battery. RFID tags with an energy storage device are known as active or semi active tags. Advances in semiconductor technology have miniaturized the electronics so much that an RFID tag can be powered solely by the RF signal it receives. Such RFID tags do not include an energy storage device and are called passive tags.

A well known problem in RFID systems is expedience in reading the tags especially where it is desired to read more than one of the codes stored in each tag. The problem becomes exacerbated if there are many tags or the host items are moving and thus allow only limited time to read their tags.

Briefly the present invention provides RFID tags and chips for RFID tags that store a first code and a second code in memory. Moreover the tags and chips for tags are capable of backscattering a combination of at least portions of the first code and the second code without receiving any commands in the interim. The present invention also provides RFID reader systems readers components software and methods for causing RFID tags to backscatter the combination without transmitting any commands in the interim.

In a number of embodiments separate reader commands do not have to be sent for reading the first and the second codes. Not sending separate commands can save time in inventorying the tags. Plus it can enable reading of tag codes during tag manufacturing that are not otherwise readily available to read in the field.

These and other features and advantages of the invention will be better understood from the specification of the invention which includes the following Detailed Description and accompanying Drawings.

The present invention is now described in more detail. While it is disclosed in its preferred form the specific embodiments of the invention as disclosed herein and illustrated in the drawings are not to be considered in a limiting sense. Rather these embodiments are provided so that this disclosure will be thorough and complete and will fully convey the scope of the invention to those skilled in the art. Indeed it should be readily apparent in view of the present description that the invention may be modified in numerous ways. Among other things the present invention may be embodied as devices methods software and so on. Accordingly the present invention may take the form of an entirely hardware embodiment an entirely software embodiment an entirely firmware embodiment or an embodiment combining aspects of the above. This description is therefore not to be taken in a limiting sense.

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

In the above an RFID reader interrogator may communicate with one or more RFID tags in any number of ways. Some such ways are described in protocols. A protocol is a specification that calls for specific manners of signaling between the reader and the tags.

One such protocol is called the Specification for RFID Air Interface EPC Radio Frequency Identity Protocols Class 1 Generation 2 UHF RFID Protocol for Communications at 860 MHz 960 MHz which is also colloquially known as the Gen2 Spec . The Gen2 Spec has been ratified by EPCglobal. Version 1.1.0 of the Gen2 Spec is hereby incorporated by reference in its entirety.

In addition a protocol can be a variant of a stated specification such as the Gen2 Spec for example including fewer or additional commands than the stated specification calls for and so on. In such instances additional commands are sometimes called custom commands.

A driver can send to its respective antenna a driving signal that is in the RF range which is why connector is typically but not necessarily a coaxial cable. The driving signal causes the antenna to transmit an RF wave which is analogous to RF wave of . In addition RF wave can be backscattered from the RFID tags analogous to RF wave of . Backscattered RF wave is received by an antenna and ultimately becomes a signal sensed by unit .

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

The chain is used in opposite directions for receiving and transmitting. In a receiving mode wireless waves are received by antenna s as signals which are in turn processed successively by the various modules in the chain. Processing can terminate in any one of the modules. In a transmitting mode initiation can be in any one of these modules. Ultimately signals are routed internally for antenna s to transmit as wireless waves.

The architecture of system is presented for purposes of explanation and not of limitation. Its particular subdivision into modules need not be followed for creating embodiments according to the invention. Furthermore the features of the invention can be performed either within a single one of the modules or by a combination of them.

In timing diagram the reader singulates each tag successively such that only one tag replies at a time while the other tags are silent. While each tag is thus singulated the reader reads its data by having a so called transaction with the tag. Three transactions are described as an example only while tens or hundreds or thousands of such transactions can take place. In addition each of transactions is not necessarily described in full but only some pertinent commands are given. Not shown are commands for example to singulate each tag for its transaction.

Each of transactions is designed so as to read the desired information from the tags. In timing diagram a first code and a second code stored in memories of the tags are read out as follows. In first transaction with one tag a first command CMD elicits a first code CODE from the tag. Then a second command CMD elicits a second code CODE from the tag. Then in transaction with another tag first command CMD is repeated and elicits a first code CODE from the other tag. Then second command CMD is repeated and elicits a second code CODE from the other tag. Then in transaction with an additional tag first command CMD is repeated and elicits a first code CODE from the additional tag. Then second command CMD is repeated and elicits a second code CODE from the additional tag.

The first code and the second code can be any suitable codes. For example the first code can be an Electronic Product Code EPC of the tag associated with a host item to which the tag is attached. The second code can be a TID code of the tag which complies with the Gen2 Spec. Or the second code can be any one or more of a date of expiration of the tag s host item a date by which the host item is to be sold by a date at which the host item was sold a code for a sale of the host item a receipt of the sale an identifier for a retailer that made the sale an identifier for a store through which the sale is made and so on. The second code could also alternately be an identifier for the tag a password for the tag an indicator for how a memory of the first tag is configured and so on. Other codes can equivalently be used for the first and the second codes. In addition what is called first and second codes can be interchanged and so on.

As can be seen each command takes time each reply takes time and there can be many transactions. And the time to read the tags can be constrained if the host items are moving. The invention addresses this timeliness problem.

Circuit includes at least two antenna connections which are suitable for coupling to one or more antenna segments not shown in . Antenna connections may be made in any suitable way such as using pads and so on. In a number of embodiments more than two antenna connections are used especially in embodiments where more antenna segments are used.

Circuit includes a section . Section may be implemented as shown for example as a group of nodes for proper routing of signals. In some embodiments section may be implemented otherwise for example to include a receive transmit switch that can route a signal and so on.

Circuit also includes a Power Management Unit PMU . PMU may be implemented in any way known in the art for harvesting raw RF power received via antenna connections . In some embodiments PMU includes at least one rectifier and so on.

In operation an RF wave received via antenna connections is received by PMU which in turn generates power for components of circuit . This is true for either or both reader to tag R T and tag to reader T R sessions whether or not the received RF wave is modulated.

Circuit additionally includes a demodulator . Demodulator demodulates an RF signal received via antenna connections . Demodulator may be implemented in any way known in the art for example including an attenuator stage an amplifier stage and so on.

Circuit further includes a processing block . Processing block receives the demodulated signal from demodulator and may perform operations. In addition it may generate an output signal for transmission.

Processing block may be implemented in any way known in the art. For example processing block may include a number of components such as a processor memory a decoder an encoder and so on.

Circuit additionally includes a modulator . Modulator modulates an output signal generated by processing block . The modulated signal is transmitted by driving antenna connections and therefore driving the load presented by the coupled antenna segment or segments. Modulator may be implemented in any way known in the art for example including a driver stage amplifier stage and so on.

In one embodiment demodulator and modulator may be combined in a single transceiver circuit. In another embodiment modulator may include a backscatter transmitter or an active transmitter. In yet other embodiments demodulator and modulator are part of processing block .

Circuit additionally includes a memory which stores data. Memory is preferably implemented as a Nonvolatile Memory NVM which means that the stored data is retained even when circuit does not have power as is frequently the case for a passive RFID tag. The data stored in memory can be a first code and a second code as per the above.

Processing block is able to cause first code to be backscattered if command CMD is received. In some embodiments processing block is further able to cause second code to be backscattered responsive to command CMD . In other embodiments second code cannot be caused to be backscattered explicitly. These embodiments depend on the nature of second code . For example some tags could be programmed to provide sale information responsive to a command while not providing a password responsive to any command.

To improve over the process of processing block is additionally able to receive a third command and in response cause to be backscattered a combination made from at least portions of the first code and the second code. This combination can be backscattered without receiving any commands in the interim while the combination is being backscattered. There are many possibilities for the third command and for the combination which are described later in this document.

The invention also includes methods. An economy is achieved in the present document in that a single description is sometimes given for both methods according to embodiments and functionalities of devices made according to embodiments. Plus a single set of flowcharts is sometimes used to describe methods in and of themselves along with operations of hardware and or software and or firmware where applicable. This is regardless of how each element is implemented.

Some methods of the invention are for the operation of RFID tags and of chips that are intended for use with RFID tags whether IC chips or made from organic semiconductors etc. These methods can be implemented in any number of ways including the structures described in this document. Examples are now given.

Other methods of the invention are for an operation or controlling an operation of an RFID reader or an RFID reader system or an RFID reader system component or for related software. These methods can be implemented in any number of ways including the structures described in this document. In addition individual operations of such methods may be practiced by different readers at different phases of the lifetime of an RFID tag with or without interruptions between them and so on. Examples are now given.

At next operation responsive to causing the third command to be transmitted there is received backscattered from the first tag a combination. No commands are caused to be transmitted in the interim while the combination is being backscattered. The combination is made from at least a portion of the first code and at least a portion of the second code. It will be recognized that this combination can be what is backscattered by the tag at operation described above.

In a number of embodiments therefore a separate command does not have to be sent for reading also the second code after the first code is read. This can save time in inventorying tags. An example is now described which is best understood by contrasting with the earlier described .

Timing diagram proceeds downward along a vertical axis TIME with commands transmitted by the reader alternating with replies backscattered by the tags. In the example of diagram the reader singulates each tag successively such that only one tag replies at a time while the other tags are silent. While each tag is thus singulated the reader reads its data by having a transaction with the tag. Three transactions are described as an example only while many more such transactions can take place. In addition each of transactions is not necessarily described in full but only some pertinent commands are given. Not shown are commands for example to singulate each tag for its transaction.

In first transaction with one tag a third command CMD elicits a combination of the tag. Combination as per the above includes at least a portion of the first code and the second code stored in the tag memory. Then in transaction with another tag third command CMD is repeated and elicits a combination of the other tag. Then in transaction with an additional tag third command CMD is repeated and elicits a combination of the additional tag.

As can be seen by comparing to transactions can take less time than respective transactions . In the embodiment of diagram according to a comment first code CODE and second code CODE were not backscattered in different installments and with an intervening command in the interim as they were in corresponding transaction of .

The nature of the third command is now described in more detail. In some embodiments the third command is different from the first command. In other embodiments the third command is identical to the first command which can be convenient from the design point of view.

In some of embodiments the tags backscatter the combination whenever they get the third command. In others the tags have a Gush mode above and beyond what is specified in the applicable communication protocol. While in the Gush mode the tags backscatter the combination if they receive the third command which can be different or even the same as the first command.

In some embodiments the tags enter the Gush mode by a series of custom steps. In other embodiments the tags enter the Gush mode by receiving a custom Gush command in connection with the third command. In that case the combination is backscattered responsive to receiving the custom Gush command and the third command. An example is shown in where optional Gush command is transmitted and prior to the optional singulation.

In some embodiments the tags are always capable of the Gush mode. In other embodiments the Gush mode can operate only after it is enabled and or no longer operate after it is disabled. This can be accomplished in any number of ways. One such way is by additional commands. For example in a custom Enable Gush command precedes the Gush command and a custom Disable Gush command follows receipt of all combinations and .

This feature can also be useful in testing the programming of tags produced in large numbers. In those cases the second code can be of the type that is not made otherwise readily available to users. The combination can include for example a programmed EPC along with a passwords or the like for confirmation of programming. Plus the feature can be disabled for shipping the confirmed tag in the field for use by others.

The backscattered combination is now described in more detail. The combination is a code that is made from at least a portion of the first code and a portion of the second code. Accordingly the combination can include the first code in whole or in part scrambled or not scrambled. By scrambled it is meant with its bits interchanged or encoded according to some key. Additionally the combination can include the second code in whole or in part with its bits scrambled or not scrambled. Plus the included bits of the first code can be intermingled with those of the second or not. Moreover a single error correcting code can be generated for the combination for checking the accuracy of the received backscatter.

In some embodiments the combination is always formed by the tag in the same way from the bits of the first code and the second code. In other embodiments the combination can be formed in different ways. In some of those the combination is further configured responsive to the custom Gush command.

In a number of embodiments the combination includes the first code or its portion and the second code or its portion with their bits not intermingled or scrambled. The first code or its portion can be before or after the second code or its portion. Examples are now described.

In the example of the duration value is a two bit field code . Here the duration value is shown with the possible values it can take. Each value results in a different duration DT namely one of DT1 DT2 DT3 DT4. The duration DT can be expressed in number of clock cycles in a number of RF cycles or in other units of time convenient for this purpose. Thus duration DT can have values chosen among the values of 0 4 msec 8 msec and 12 msec. In addition such a delay should not be too long because then other communication may start taking place. According to comment where DT1 0 that is the case of no interim pause.

The above mentioned commands can be constructed in accordance with the applicable communication protocol. Moreover custom commands can be used for the third command and those of the Gush command the Enable Gush command the Disable Gush command and the Tune command. These custom commands can be constructed in any number of ways. In some instances they can be considered as custom commands not being specified in a particular communication protocol. In some instances they would be standalone commands made by a sequence of bits chosen so that they do not conflict with other commands of the protocol. In other instances they can be commands with a custom payload. Such commands can be known to the protocol or not and the payload can be used to distinguish among different custom commands and optionally further transfer a parameter for the commands.

When commands are used that are known to the protocol a section of their payload can be advantageously used for the purpose of implementing one of the custom commands. Such a section in the payload can be a mask field according to embodiments. For the Gen2 Spec two such commands are the Select command and the BlockWrite command. Between these two candidate commands it should be considered that the Select command can be transmitted before or after a tag is singulated out of its population while the BlockWrite is better suited for singulated tags. In addition the BlockWrite command is optional to the Gen2 Spec and the tag would probably have to have a controller that can accept it.

Each one of the custom commands can thus be constructed as an implementation of this Select command or the BlockWrite command. An example is now described in terms of the Select command but would apply equally to the BlockWrite command.

The Feature Enabling Field FEF enables the tag to verify that it is a proper recipient for the command by comparing the transmitted FEF value against a value in Membank. In this case Membank can be EPC TID or USER memory. As can be seen the FEF can be further partitioned into subfields for better clarity. Such subfields might include for example if Membank is TID memory as described in Gen2 v1.1.0 a Class Identifier the MDID and an Indicator Bit.

The Class Identifier can be two bits. For example EPCglobal can correspond to a value of 10. This would allow the custom command to apply for example only to EPCglobal tags.

The MDID is the tag manufacturer s ID which is stored in the tag s TID memory. For Impinj tags this number is 000000000001 or 100000000001. The MDID allows a reader to select tags of only the manufacturer of interest. So even if this Select command is transmitted and received before singulation the Select command can select also according to the tag manufacturer s ID. This will cause the manufacturer s tags to be selected and thus the reader can ensure prior knowledge of the tag manufacturer s identification.

The Indicator Bit can be set to 0 or 1. In the Gen2 spec a tag model number follows the MDID. A bit of this model number can serve as the Indicator Bit and can be interpreted as follows If it is 0 the tags can interpret the command as an ordinary Select and execute it per the Gen2 spec. Else if it is 1 the tags can interpret the Select command as a custom instruction and execute according to the FCF.

The Feature Command Field FCF can have a command code that indicates the number of the custom instruction. For example a command code of 00000 could be the Gush command. A 5 bit field permits 32 possible custom commands. A command code of 11111 could indicate an extended command field that extends into the subsequent data field allowing more than 32 custom commands.

The data field can contain data needed to implement the custom instruction if any. Not all commands will use it. The data field can be variable in size. Its meaning will derive from the command code. For example the duration value of the Tune command can be encoded as data in the FCF subfield shown in .

In some embodiments the tag may ignore the Target and Action field in the Select command depending on whether these fields are relevant. In other embodiments the tag may also set the appropriate Target flag.

In preferred embodiments the entire Select command must be valid for the tag to accept and execute the custom command. That means valid values for Membank Length Pointer Mask CRC 16 etc. An example is now described.

Everything described above in terms of readers and reader components finds some correspondence with tags and tag chips. In some instances some of the above also describe features and behavior of tag chips.

Numerous details have been set forth in this description which is to be taken as a whole to provide a more thorough understanding of the invention. In other instances well known features have not been described in detail so as to not obscure unnecessarily the invention.

The invention includes combinations and subcombinations of the various elements features functions and or properties disclosed herein. The following claims define certain combinations and subcombinations which are regarded as novel and non obvious. Additional claims for other combinations and subcombinations of features functions elements and or properties may be presented in this or a related document.

