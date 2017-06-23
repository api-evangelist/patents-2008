---

title: RFID tag chips and tags refraining from participating in a subsequent inventorying attempt and methods
abstract: RFID tags and chips for RFID tags are capable of being inventoried in one or more early attempts. These tags are capable of then refraining from participating in one or more subsequent inventorying attempts. In some embodiments refraining is performed solely by the tag, while in others it is guided by the RFID reader. In some embodiments, an inventoried indicator in the tag becomes updated upon backscattering. The updated value is used by the tag to recognize a subsequent attempt, and thus refrain from participating in it. This permits the subsequent attempt to be used more intensively for inventorying the more elusive, harder-to-read tags, especially in more demanding scenarios.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08279045&OS=08279045&RS=08279045
owner: Impinj, Inc.
number: 08279045
owner_city: Seattle
owner_country: US
publication_date: 20080328
---
This application claims priority from U.S.A. Provisional Application No. 60 920 686 filed on 2007 Mar. 29 the disclosure of which is hereby incorporated by reference for all purposes.

This application claims priority from U.S.A. Provisional Application No. 60 932 627 filed on 2007 May 31 the disclosure of which is hereby incorporated by reference for all purposes.

This application claims priority from U.S.A. Provisional Application No. 61 005 249 filed on 2007 Dec. 4 the disclosure of which is hereby incorporated by reference for all purposes.

Radio Frequency IDentification RFID systems typically include RFID tags and RFID readers. RFID readers are also known as RFID reader writers or RFID interrogators. RFID systems can be used in many ways for locating and identifying objects to which the tags are attached. RFID systems are particularly useful in product related and service related industries for tracking objects being processed inventoried or handled. In such cases an RFID tag is usually attached to an individual item or to its package.

In principle RFID techniques entail using an RFID reader to interrogate one or more RFID tags. The reader transmitting a Radio Frequency RF wave performs the interrogation. The RF wave is typically electromagnetic at least in the far field. The RF wave can also be predominantly electric or magnetic in the near field.

A tag that senses the interrogating RF wave responds by transmitting back another RF wave. The tag generates the transmitted back RF wave either originally or by reflecting back a portion of the interrogating RF wave in a process known as backscatter. Backscatter may take place in a number of ways.

The reflected back RF wave may further encode data stored internally in the tag such as a number. The response is demodulated and decoded by the reader which thereby identifies counts or otherwise interacts with the associated item. The decoded data can denote a serial number a price a date a destination other attribute s any combination of attributes and so on.

An RFID tag typically includes an antenna system a radio section a power management section and frequently a logical section a memory or both. In earlier RFID tags the power management section included an energy storage device such as a battery. RFID tags with an energy storage device are known as active or semi active tags. Advances in semiconductor technology have miniaturized the electronics so much that an RFID tag can be powered solely by the RF signal it receives. Such RFID tags do not include an energy storage device and are called passive tags.

Problems arise when more and more tags are desired to be inventoried in less and less time. There is less time as tags are moving.

An emerging pattern is that some tags are occasionally harder to read than others even with repeated inventorying attempts. Such tags could be for example in the center of a large group. This pattern can become a problem when there is less time to read the group such as when the group is moving past the antennas without stopping.

Briefly the present invention provides RFID tags and chips for RFID tags that are capable of being inventoried in one or more early attempts. These tags are capable of then refraining from participating in one or more subsequent inventorying attempts. In some embodiments refraining is performed solely by the tag while in others it is guided by the RFID reader.

The invention offers the advantage that when these tags refrain from participating in the subsequent attempts they permit these attempts to be used more intensively for inventorying the more elusive harder to read tags especially in more demanding scenarios.

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

One such protocol is called the Specification for RFID Air Interface EPC Radio Frequency Identity Protocols Class 1 Generation 2 UHF RFID Protocol for Communications at 860 MHz 960 MHz which is also colloquially known as the Gen2 Spec . The Gen2 Spec has been ratified by EPCglobal which is an organization that maintains a website at at the time this document is initially filed with the USPTO. Version 1.1.0 of the Gen2 Spec is hereby incorporated by reference in its entirety.

In addition a protocol can be a variant of a stated specification such as the Gen2 Spec for example including fewer or additional commands than the stated specification calls for and so on. In such instances additional commands are sometimes called custom commands.

Circuit includes at least two antenna connections which are suitable for coupling to one or more antenna segments not shown in . Antenna connections may be made in any suitable way such as using pads and so on. In a number of embodiments more than two antenna connections are used especially in embodiments where more antenna segments are used.

Circuit includes a section . Section may be implemented as shown for example as a group of nodes for proper routing of signals. In some embodiments section may be implemented otherwise for example to include a receive transmit switch that can route a signal and so on.

Circuit also includes a Power Management Unit PMU . PMU may be implemented in any way known in the art for harvesting raw RF power received via antenna connections . In some embodiments PMU includes at least one rectifier and so on.

In operation an RF wave received via antenna connections is received by PMU which in turn generates power for components of circuit . This is true for either or both R T and T R sessions whether or not the received RF wave is modulated.

Circuit additionally includes a demodulator . Demodulator demodulates an RF signal received via antenna connections . Demodulator may be implemented in any way known in the art for example including an attenuator stage an amplifier stage and so on.

Circuit further includes a processing block . Processing block receives the demodulated signal from demodulator and may perform operations. In addition it may generate an output signal for transmission.

Processing block may be implemented in any way known in the art. For example processing block may include a number of components such as a processor memory a decoder an encoder and so on.

Circuit additionally includes a modulator . Modulator modulates an output signal generated by processing block . The modulated signal is transmitted by driving antenna connections and therefore driving the load presented by the coupled antenna segment or segments. Modulator may be implemented in any way known in the art for example including a driver stage amplifier stage and so on.

In one embodiment demodulator and modulator may be combined in a single transceiver circuit. In another embodiment modulator may include a backscatter transmitter or an active transmitter. In yet other embodiments demodulator and modulator are part of processing block .

Circuit additionally includes a memory which stores data . Memory is preferably implemented as a Nonvolatile Memory NVM which means that data is retained even when circuit does not have power as is frequently the case for a passive RFID tag.

It will be recognized at this juncture that the shown components of circuit can be those of a circuit of an RFID reader according to the invention with or without needing PMU . Indeed an RFID reader can be powered differently such as from a wall outlet a battery and so on. Additionally when circuit is configured as a reader processing block may have additional Inputs Outputs I O to a terminal network or other such devices or connections.

In terms of processing a signal circuit operates differently during a R T session and a T R session. The different operations are described below in this case with circuit representing an RFID tag.

Version A shows as relatively obscured those components that do not play a part in processing a signal during a R T session. Indeed PMU may be active but only in converting raw RF power. And modulator generally does not transmit during a R T session. Modulator typically does not interact with the received RF wave significantly either because switching action in section of decouples the modulator from the RF wave or by designing modulator to have a suitable impedance and so on.

While modulator is typically inactive during a R T session it need not be always the case. For example during a R T session modulator could be active in other ways. For example it could be adjusting its own parameters for operation in a future session.

Version B shows as relatively obscured those components that do not play a part in processing a signal during a T R session. Indeed PMU may be active but only in converting raw RF power. And demodulator generally does not receive during a T R session. Demodulator typically does not interact with the transmitted RF wave either because switching action in section decouples the demodulator from the RF wave or by designing demodulator to have a suitable impedance and so on.

While demodulator is typically inactive during a T R session it need not be always the case. For example during a T R session demodulator could be active in other ways. For example it could be adjusting its own parameters for operation in a future session.

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

Each inventorying attempt . . . includes at least one command. The commands and the replies that the tags may give in response to them are part of the applicable communication protocol assuming that both follow the same protocol. Each set of commands and replies might result in reading a code of the tag preferably after singulating the tag from the remainder of the tag population. Each inventorying attempt . . . attempts to read all the tags.

The shape of each of reading curves is approximate and also shown in U.S. patent application Ser. No. 11 210 384 published as Document Number 2005 0280505A1 which is incorporated by reference in its entirety. of that other document shows a succession of inventory rounds which are one inventorying attempt. of that other document shows the tags being read in a dashed reading curve numbered in that document as a Q parameter is being varied.

Returning to the present invention for purposes of knowing about all the tags a thicker cataloguing line shows which tags become known to reader and when. Tags become inventoried by being read at least the first time at which time they also become catalogued. So cataloguing line starts at a value NS which represents the number of tags that are to be inventoried and is reduced to zero by the first reading curve alone. After that the subsequent reading curves add no new information and cataloguing line remains at zero. In that sense subsequent inventorying attempts are redundant in this case. In practice subsequent inventorying attempts are provided to ensure that all tags have been read even the harder ones to read that might be missed by first inventorying attempt .

In scenario the easier reading conditions are apparent because first inventorying attempt alone resulted in reading curve that read all the tags. Subsequent inventorying attempts contributed no new tags being inventoried. A more demanding scenario is now described.

A cataloguing line shows the progress in inventorying the tags. First reading curve will read all the easier tags. The reading curves of the subsequent attempts will contribute a few more of the harder to read tags. A problem is when not all have been inventoried by the time they leave the field of view. Another problem is when they have to all be inventoried at least twice to guard against the inclusion of inadvertent stray reads which could be one time only.

Memory also stores an inventoried flag . Flag is Boolean in that it is capable of having only two states. Operations of the tag many flip the state from the one value to the other. Some of these operations may be inventorying operations both in terms of selecting a subgroup of tags in the first place and also in terms of commanding or not the state of flag to be flipped upon the tag becoming inventoried. Such an inventoried flag is specified for example in the Gen2 Spec as one of the S S S S inventoried flags whose values can be namely A or B. It should be noted that the Gen2 Spec permits only one of these flags to be used in a session for inventorying.

Memory further stores an inventoried indicator INV ID . Inventoried indicator is updated in conjunction with backscattering the code. As such it can help control whether a tag will participate in a subsequent inventorying attempt or refrain to allow others a better chance. It should be noted that inventoried indicator is distinct from the Select Flag of the Gen2 Spec which does not become updated in conjunction with backscattering the code.

While code inventoried flag and inventoried indicator are shown stored in memory they are not necessarily stored in the same part of the memory. They can each be stored under different conditions. For example code can be stored in a non volatile memory that needs no power to be refreshed even for years. In embodiments according to the Gen2 Spec inventoried flag would have persistence as specified in its Table 6.14. And inventoried indicator has persistence as can be discerned by the person skilled in the art in view of this disclosure.

Flowchart may be repeated a number of times as a loop. For example the tag may go through that loop once for every inventorying attempt such as for the inventorying attempts described above. That is why although the individual operations flowchart will be described in a certain order they may take place in a different order.

At operation a first attempt to read the code is detected. The first attempt can be an inventorying attempt as per the above. The first attempt agrees with a current state of the flag in that it calls for it exactly or does not call for a condition that would contradict it.

At optional next operation it is determined whether the inventoried indicator as has been most recently updated meets a participation condition. Examples of the participation condition will be described later in this document. The inventoried indicator can be updated at a later operation .

If the participation condition is not met the tag will refrain according to embodiments. This means that execution may return to operation waiting to detect the onset of another inventorying attempt that agrees with a current state of the flag. Along with returning to operation the tag may backscatter an error code indicating that it is present but will not fully properly participate. Or it may backscatter nothing. If however the participation condition is indeed met then the tag may participate plus update its inventoried indicator as per the below.

At optional next operation the tag becomes singulated from the population of tags it is with. This can be performed by the reader and the tag performing steps appropriate for the applicable communication protocol. Singulation will thus ensure that all the other tags in the population will not be responding so that the reader can discern the forthcoming backscatter from the tag.

At next operation the inventoried indicator is updated in conjunction with backscattering the code. In terms of exact operation the inventoried indicator can be updated after backscattering the code or concurrently with it or before it.

At next operation the state of the inventoried flag is flipped or not responsive to the first attempt. For example the first attempt may include an instruction to flip or not flip the inventoried flag. Or it may not include such an instruction but by its structure it might cause the inventoried flag to be flipped or not.

At optional next operation the updated inventoried indicator becomes reset such that the inventoried indicator now meets the participation condition. This operation may also take place at other times in flowchart for example if after operation it has been determined to refrain from participating.

Resetting may take place in any number of ways. In some embodiments this can be automatic after enough time passes. For example there can be a preset time that elapses from an event and then there is reset. Alternately a suitable Reset command can be receiving wirelessly.

Execution then can return to operation . Or since operation is optional execution can return to operation after operation instead. Operation may be reached either without losing power in the tag since operation was executed or with losing and regaining power.

Once back at operation a second inventorying attempt can be detected which can agree with a current state of the flag. Then again according to operation it is again determined whether the inventoried indicator updated at operation meets the participation condition. It might not meet it due to the update. If it does then the above sequence of operations can be repeated and so on.

In some embodiments the reader also transmits a serial number in association with the first attempt and the tag receives it. The serial number can be transmitted and received in any suitable way. One suitable way for transmitting it is via a Select command or a BlockWrite of the Gen2 Spec as is described later in this document.

Then the inventoried indicator can be updated by being set to a new value. The new value can be the serial number itself or another number determined from the serial number. In some of these embodiments the participation condition can refer to whether the updated inventoried indicator differs from the new value. So when a new attempt is detected if it corresponds to the same serial number the tag will know to refrain and the participation condition can be defined accordingly so as to effectuate the refraining for example by returning to operation directly from operation . If the new attempt corresponds to a different serial number there will be participation. The new attempt could be from a different reader or from the same reader that wants to inventory again all the tags in its field of view. The latter embodiment can take place if the reader is confident that it has inventoried all tags and does not need any of them to refrain from the second attempt.

The serial number can be specific to a group of forthcoming attempts by a reader. Plus if two readers are cooperating they could use the same serial number. This way once a tag is inventoried by one of the readers it will refrain from being read also by the other. The serial number could also be specific to the reader which is useful if two readers have overlapping fields of view. This way once a tag is inventoried by one of the readers it will refrain from being read by it. But it will not refrain from being read by the other reader. In some of these embodiments the tag can maintain a list of such serial numbers so as to be able to refrain from being read by multiple readers.

In fact in this example reading curve returned no new tags. As such there was a Reset command and then another reading curve starting again from all the tags.

The reading curves and cataloguing line of can be caused by any number of operations by the reader. Two alternative examples are now described with reference to .

According to comment attempt returned no new tags. A command can transmit a second serial number SN for the next forthcoming group. Command can operate as Reset command . Then another attempt can result in another reading curve and so on.

According to comment attempt returned no new tags. Then another attempt can result in another reading curve and so on. Attempt can include the second serial number SN of its own group and thus no Reset command is needed.

Returning to it will be observed that each tag was inventoried only once and tags were not read again until there was confidence that all tags had been inventoried. Sometimes however it is desired to read tags more than once for example so as to validate against a tag code arising spuriously. In some sample instances a rule can be implemented that unless a tag is read redundantly for example at least twice it will be considered a stray read and thus not counted. The invention can help in such instances by having tags refrain from being counted more than twice. Examples are now described which can be different from where the inventoried indicator was a serial number.

In some embodiments the inventoried indicator is a number which is stored in a counter. For example register would store that number. Updating the inventoried indicator can be performed by adjusting the number in the counter and the participation condition is that the number in the counter has not reached a limit. This can be implemented in many ways. For example the number in the counter can be adjusted by being incremented up to some limit. Or the number in the counter can be adjusted by being decremented down to a limit. In some of these embodiments that limit can be zero.

In some embodiments this feature operates autonomously. In others assistance from the reader is called for. The reader can enable the feature or disable it if that is called for. Optionally the reader can transmit and the tag can receive a participation parameter. Then a number initially stored in the counter or the limit can be determined from the received participation parameter. The participation parameter can be received via a Select command or a BlockWrite of the Gen2 Spec or other suitable commands.

The number in the counter and the limit thus determine in how many attempts the tag will participate before it starts refraining. For example if the number in the counter starts from 1 and counts down to zero the tag will participate only once and the profile of will result. A different example is now described where each tag participates twice.

In some embodiments a tag refrains from being inventoried in subsequent rounds as per the above. In others it does that only when the tag is in an enabled state as opposed to a disabled state. An example is now described.

In some embodiments enabled state and disabled state are provided in a way that does not define additional states in the underlying protocol. For example for the Gen2 Spec the initial Ready state can be disabled state while one or more of the other states can be enabled states . Or some of the other states can also be characterized as disabled state .

In other embodiments either one or both of enabled state and disabled state can be provided as states different from and in addition to what is required by the Gen2 Spec.

As will be realized commands can be configured in any number of ways. For example if Enable Refraining command is provided it can be separate from command . Preferably these are configured as separate standalone commands each occurring at a single one of the communication sessions such as those of time interval of . In addition the tag need not backscatter a reply to any one of them individually.

In addition command plus optionally commands and may be used among other commands that will be transmitted to the tag in question and possibly other tags. Equally the optional first and second replies will be among other replies backscattered by the tag in question and possibly other tags.

At operation a first attempt to read the code is caused to be transmitted wirelessly which agrees with a current state of the inventoried flag and includes a first participation parameter. The first participation parameter can be any suitable parameter. In some embodiments for example it is a serial number that is associated with the first attempt as per the above. In other embodiments the inventoried indicator includes a number stored in a counter which is determined from the received participation parameter. In other words the first participation parameter is used to help determine the number in the counter. The first participation parameter can be caused to be transmitted in any suitable way for example as part of a command a parameter of a command and so on. For implementations of the Gen2 Spec such can be a Select command a BlockWrite command and so on.

At next operation the backscattered code is received from the tag responsive to the first attempt. Concurrently with the first attempt the tag may further update the inventoried indicator in conjunction with backscattering the code and flip or not the state of its inventoried flag as also per the above.

At next operation a second attempt to read the code is caused to be transmitted wirelessly. This second inventorying attempt agrees with a current state of the inventoried flag.

At optional next operation it is determined whether a participation condition is met. The participation condition refers to whether the updated inventoried indicator differs from the first participation parameter. The inventoried indicator may have been updated concurrently with receiving the backscattered code at operation .

If at operation the participation condition is met then at optional next operation the backscattered code is received responsive to the second attempt as it was also received in operation . Else at optional next operation the backscattered code is not received as per the above.

Returning to each one of commands can be constructed in any number of ways. In some instances they can be considered as custom commands as not being specified in a particular communication protocol. In some instances they would be standalone commands made by a sequence of bits chosen so that they do not conflict with other commands of the protocol. In other instances they can be commands with a custom payload. Such commands can be known to the protocol or not and the payload can be used to distinguish among different custom commands and optionally further transfer a parameter for the commands.

When commands are used that are known to the protocol a section of their payload can be advantageously used for the purpose of implementing a custom command such as commands . Such a section in the payload can be a mask field according to embodiments. For the Gen2 Spec two such commands are the Select command and the BlockWrite command. Between these two candidate commands it should be considered that the Select command can be transmitted before or after a tag is singulated out of its population while the BlockWrite is better suited for singulated tags. In addition the BlockWrite command is optional to the Gen2 Spec and the tag would probably have to have a controller that can accept it.

Each one of commands can thus be constructed as an implementation of this Select command or the BlockWrite command. An example is now described in terms of the Select command but would apply equally to the BlockWrite command.

The Feature Enabling Field FEF enables the tag to verify that it is a proper recipient for the command by comparing the transmitted FEF value against a value in Membank. In this case Membank can be EPC TID or USER memory. As can be seen the FEF can be further partitioned into subfields for better clarity. Such subfields can include a Class Identifier the MDID and an Indicator Bit.

The Class Identifier can be two bits. For example EPCglobal can correspond to a value of 10. This would allow the custom command to apply for example only to EPCglobal tags.

The MDID is the tag manufacturer s ID which is stored in the tag s TID memory. For Impinj tags this number is 000000000001 or 100000000001. The MDID allows a reader to select tags of only the manufacturer of interest. So even if this Select command is transmitted and received before singulation the Select command can select also according to the tag manufacturer s ID. This will cause the manufacturer s tags to be selected and thus the reader can ensure prior knowledge of the tag manufacturer s identification.

The Indicator Bit can be set to 0 or 1. In the Gen2 Spec a tag model number follows the MDID. A bit of this model number can serve as the Indicator Bit and can be interpreted as follows If it is 0 the tags can interpret the command as an ordinary Select and execute it per the Gen2 spec. Else if it is 1 the tags can interpret the Select command as a custom instruction and execute according to the FCF.

The Feature Command Field FCF can have a command code that indicates the number of the custom instruction. For example a command code of 00000 could be the custom command. This permits possible custom commands. In addition a command code of 11111 could indicate an extended command code that extends into the subsequent data field.

The data field can contain data needed to implement the custom instruction if any. Not all commands will use it. The data field can be variable in size. Its meaning will derive from the command codes.

In some embodiments the tag may ignore the Target and Action field in the Select command depending on whether these fields are relevant to the CI. In other embodiments the tag may also set the appropriate flag.

In preferred embodiments the entire Select command must be valid for the tag to accept and execute the custom command. That means valid values for Membank Length Pointer Mask CRC 16 etc. An example is now described.

Everything described above in terms of readers and reader components finds some correspondence with tags and tag chips. In some instances some of the above also describe features and behavior of tag chips.

Numerous details have been set forth in this description which is to be taken as a whole to provide a more thorough understanding of the invention. In other instances well known features have not been described in detail so as to not obscure unnecessarily the invention.

The invention includes combinations and subcombinations of the various elements features functions and or properties disclosed herein. The following claims define certain combinations and subcombinations which are regarded as novel and non obvious. Additional claims for other combinations and subcombinations of features functions elements and or properties may be presented in this or a related document.

