---

title: Dealing with rogue RFID readers using reader attributes
abstract: Rogue RFID readers are detected by listening to communication between rogue reader and a tag, capturing a time stamp and/or a channel associated with the communication, and checking the captured time stamp/channel to determine whether it is a result of a command from another legitimate reader. Audible or visible alerts may be issued, flags may be set, or messages transmitted to an administrator upon determining the operation of the rogue RFID reader. Based on the alert(s) affected tags or the rogue reader may be jammed or an effect of the illegal transmission by the rogue reader may be reversed or tags replaced.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07982611&OS=07982611&RS=07982611
owner: Impinj, Inc.
number: 07982611
owner_city: Seattle
owner_country: US
publication_date: 20081117
---
This application claims priority from U.S. Provisional Application Ser. No. 61 003 632 filed on Nov. 19 2007 the disclosure of which is hereby incorporated by reference for all purposes.

This application also claims priority from U.S. Provisional Application Ser. No. 61 021 595 filed on Jan. 16 2008 the disclosure of which is hereby incorporated by reference for all purposes.

This application may be found related to commonly assigned co pending U.S. application Ser. No. 12 272 784 filed on the same day titled DEALING WITH ROGUE RFID READERS USING TAG IDENTIFIERS .

Radio Frequency IDentification RFID systems typically include RFID tags and RFID readers. RFID readers are also known as RFID reader writers or RFID interrogators. RFID systems can be used in many ways for locating and identifying objects to which the tags are attached. RFID systems are particularly useful in product related and service related industries for tracking objects being processed inventoried or handled. In such cases an RFID tag is usually attached to an individual item or to its package.

In principle RFID techniques entail using an RFID reader to interrogate one or more RFID tags. The reader transmitting a Radio Frequency RF wave performs the interrogation. The RF wave is typically electromagnetic at least in the far field. The RF wave can also be predominantly electric or magnetic in the near field. The RF wave may encode one or more commands that instruct the tags to perform one or more actions.

A tag that senses the interrogating RF wave responds by transmitting back another RF wave. The tag generates the transmitted back RF wave either originally or by reflecting back a portion of the interrogating RF wave in a process known as backscatter. Backscatter may take place in a number of ways.

The reflected back RF wave may further encode data stored internally in the tag such as a number. The response is demodulated and decoded by the reader which thereby identifies counts or otherwise interacts with the associated item. The decoded data can denote a serial number a price a date a destination other attribute s any combination of attributes and so on. Accordingly when a reader reads a tag code data can be learned about the associated item that hosts the tag and or about the tag itself.

An RFID tag typically includes an antenna system a radio section a power management section and frequently a logical section a memory or both. In earlier RFID tags the power management section included an energy storage device such as a battery. RFID tags with an energy storage device are known as active or semi active tags. Advances in semiconductor technology have miniaturized the electronics so much that an RFID tag can be powered solely by the RF signal it receives. Such RFID tags do not include an energy storage device and are called passive tags.

A challenge with RFID systems is the possibility of a rogue RFID reader. Rogue RFID readers may be used to surreptitiously alter tag data from their intended legitimate value or to surreptitiously alter the tag itself such as by electronically killing or deactivating some or all of tag s features. The threat exists in many contexts. In a purely commercial context the loss may be financial. In other contexts where food or pharmaceuticals are tagged the loss may be of a different nature.

This summary is provided to introduce a selection of concepts in a simplified form that are further described below in the Detailed Description. This summary is not intended to exclusively identify key features or essential features of the claimed subject matter nor is it intended as an aid in determining the scope of the claimed subject matter.

Briefly embodiments are directed to dealing with a rogue RFID reader by listening to communication between rogue reader and a tag capturing a reader attribute such as a time stamp of reader communication or a channel of reader communication and checking the captured reader attribute to determine whether it is a result of a command from another legitimate reader. According to some embodiments an audible or visible alert may be issued upon determining the operation of the rogue RFID reader. Affected tags or the rogue reader may be jammed through a jamming signal. According to other embodiments an effect of the illegal transmission by the rogue reader may be reversed or tags replaced upon determining which tags are affected.

These and other features and advantages will be apparent from a reading of the following detailed description and a review of the associated drawings. It is to be understood that both the foregoing general description and the following detailed description are explanatory and do not restrict aspects as claimed.

Various embodiments are now described. The specific embodiments as disclosed herein and illustrated in the drawings are not to be considered in a limiting sense. Rather these embodiments are provided so that this disclosure will be thorough and complete and will fully convey the scope of the claimed subject matter to those skilled in the art. Indeed it should be readily apparent in view of the present description that the embodiments may be modified in numerous ways. Among other things the claimed subject matter may be embodied as devices methods software and so on. Accordingly the claimed subject matter may take the form of an entirely hardware embodiment an entirely software embodiment an entirely firmware embodiment or an embodiment combining aspects of the above. This description is therefore not to be taken in a limiting sense. While various aspects of the claimed subject matter are described with repeated references to an embodiment this is not an indication that the same embodiment is always referred to.

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

In the above an RFID reader interrogator may communicate with one or more RFID tags in any number of ways. Some such ways are described in protocols. A protocol is a specification that calls for specific manners of signaling between the reader and the tags and vice versa.

One such protocol is called the Specification for RFID Air Interface EPC Radio Frequency Identity Protocols Class 1 Generation 2 UHF RFID Protocol for Communications at 860 MHz 960 MHz which is also colloquially known as the Gen2 Spec . The Gen2 Spec has been ratified by EPCglobal which is an organization that maintains a website at at the time this document is initially filed with the USPTO.

In addition a protocol can be a variant of a stated specification such as the Gen2 Spec for example including fewer or additional commands than the stated specification calls for and so on. In such instances additional commands are sometimes called custom commands.

It was described above how reader and tag communicate in terms of time. In addition communications between reader and tag may be restricted according to frequency. One such restriction is that the available frequency spectrum may be partitioned into divisions that are called channels. Different partitioning manners may be specified by different regulatory jurisdictions and authorities e.g. FCC in North America CEPT in Europe etc. .

Reader typically transmits with a transmission spectrum that lies within one channel. In some regulatory jurisdictions the authorities permit aggregating multiple channels into one or more larger channels but for all practical purposes an aggregate channel can again be considered a single albeit larger individual channel.

Tag can respond with a backscatter that is modulated directly onto the frequency of the reader s emitted CW also called baseband backscatter. Alternatively tag can respond with a backscatter that is modulated onto a frequency developed by tag that is different from the reader s emitted CW and this modulated tag frequency is then impressed upon the reader s emitted CW. This second type of backscatter is called subcarrier backscatter. The subcarrier frequency can be within the reader s channel can straddle the boundaries with the adjacent channel or can be wholly outside the reader s channel.

A number of jurisdictions require a reader to hop to a new channel on a regular basis. When a reader hops to a new channel it may encounter RF energy there that could interfere with communications.

Embodiments of the present disclosure can be useful in different RFID environments for example in the deployment of RFID readers in sparse or dense reader environments in environments with networked and disconnected readers such as where a hand held reader may enter the field of networked readers or in environments with mobile readers. It will be understood that the present embodiments are not limited to operation in the above environments.

Local block is responsible for communicating with the tags. Local block includes a block of an antenna and a driver of the antenna for communicating with the tags. Some readers like that shown in local block contain a single antenna and driver. Some readers contain multiple antennas and drivers and a method to switch signals among them including sometimes using different antennas for transmitting and for receiving. And some readers contain multiple antennas and drivers that can operate simultaneously. A demodulator decoder block demodulates and decodes backscattered waves received from the tags via antenna block . Modulator encoder block encodes and modulates an RF wave that is to be transmitted to the tags via antenna block .

Local block additionally includes an optional local processor . Processor may be implemented in any number of ways known in the art. Such ways include by way of examples and not of limitation digital and or analog processors such as microprocessors and digital signal processors DSPs controllers such as microcontrollers software running in a machine such as a general purpose computer programmable circuits such as Field Programmable Gate Arrays FPGAs Field Programmable Analog Arrays FPAAs Programmable Logic Devices PLDs Application Specific Integrated Circuits ASIC any combination of one or more of these and so on. In some cases some or all of the decoding function in block the encoding function in block or both may be performed instead by processor .

Local block additionally includes an optional local memory . Memory may be implemented in any number of ways known in the art. Such ways include by way of examples and not of limitation nonvolatile memories NVM read only memories ROM random access memories RAM any combination of one or more of these and so on. These can be implemented separately from processor or in a single chip with or without other components. Memory if provided can store programs for processor to run if needed.

In some embodiments memory stores data read from tags or data to be written to tags such as Electronic Product Codes EPCs Tag Identifiers TIDs tag handles and other data. Memory can also include reference data that is to be compared to the EPC codes instructions and or rules for how to encode commands for the tags modes for controlling antenna and so on. In some of these embodiments local memory is provided as a database.

Some components of local block typically treat the data as analog such as the antenna driver block . Other components such as memory typically treat the data as digital. At some point there is a conversion between analog and digital. Based on where this conversion occurs a whole reader may be characterized as analog or digital but most readers contain a mix of analog and digital functionality.

If remote components are indeed provided they are coupled to local block via an electronic communications network . Network can be a Local Area Network LAN a Metropolitan Area Network MAN a Wide Area Network WAN a network of networks such as the internet or a mere local communication link such as a USB PCI and so on. In turn local block then includes a local network connection for communicating with network .

There can be one or more remote component s . If more than one they can be located at the same location or in different locations. They can access each other and local block via network or via other similar networks and so on. Accordingly remote component s can use respective remote network connections. Only one such remote network connection is shown which is similar to local network connection etc.

Remote component s can also include a remote processor . Processor can be made in any way known in the art such as was described with reference to local processor .

Remote component s can also include a remote memory . Memory can be made in any way known in the art such as was described with reference to local memory . Memory may include a local database and a different database of a Standards Organization such as one that can reference EPCs.

Of the above described elements it is advantageous to consider a combination of these components designated as operational processing block . Block includes those components that are provided of the following local processor remote processor local network connection remote network connection and by extension an applicable portion of network that links connection with connection . The portion can be dynamically changeable etc. In addition block can receive and decode RF waves received via antenna and cause antenna to transmit RF waves according to what it has processed.

Block includes either local processor or remote processor or both. If both are provided remote processor can be made such that it operates in a way complementary with that of local processor . In fact the two can cooperate. It will be appreciated that block as defined this way is in communication with both local memory and remote memory if both are present.

Accordingly block is location agnostic in that its functions can be implemented either by local processor or by remote processor or by a combination of both. Some of these functions are preferably implemented by local processor and some by remote processor . Block accesses local memory or remote memory or both for storing and or retrieving data.

Reader system operates by block generating communications for RFID tags. These communications are ultimately transmitted by antenna block with modulator encoder block encoding and modulating the information on an RF wave. Then data is received from the tags via antenna block demodulated and decoded by demodulator decoder block and processed by processing block .

An RFID tag is considered here as a module by itself. Tag conducts a wireless communication with the remainder via the air interface . It is noteworthy that air interface is really only a boundary in that signals or data that pass through it are not intended to be transformed from one thing to another. Specifications as to how readers and tags are to communicate with each other for example the Gen2 Specification also properly characterize that boundary an interface.

RFID system includes one or more antennas and an RF Front End for interfacing with antenna s . These can be made as described above. In addition Front End typically includes analog components.

System also includes a Signal Processing module . In this embodiment module exchanges waveforms with Front End such as I and Q waveform pairs. In some embodiments signal processing module is implemented by itself in an FPGA.

System also includes a Physical Driver module which is also known as Data Link. In this embodiment module exchanges bits with module . Data Link can be the stage associated with framing of data. In one embodiment module is implemented by a Digital Signal Processor.

System additionally includes a Media Access Control module which is also known as MAC layer. In this embodiment module exchanges packets of bits with module . MAC layer can be the stage for making decisions for sharing the medium of wireless communication which in this case is the air interface. Sharing can be between reader system and tags or between system with another reader or between tags or a combination. In one embodiment module is implemented by a Digital Signal Processor. In some embodiments many of the components of modules and can be implemented in one or more Integrated Circuit IC chips.

System moreover includes an Application Programming Library module . This can include Application Programming Interfaces APIs other objects etc.

All of these functionalities can be supported by one or more processors. One of these processors can be considered a host processor. Such a host processor might include a Host Operating System OS and or Central Processing Unit CPU . In some embodiments the processor is not considered as a separate module but one that includes some of the above mentioned modules of system .

A user interface may be coupled to library for accessing the APIs. User interface can be manual automatic or both. It can be supported by the host processor mentioned above or a separate processor etc.

It will be observed that the modules of system form something of a chain. Adjacent modules in the chain can be coupled by the appropriate instrumentalities for exchanging signals. These instrumentalities include conductors buses interfaces and so on. These instrumentalities can be local e.g. to connect modules that are physically close to each other or over a network for remote communication.

The chain is used in opposite directions for receiving and transmitting. In a receiving mode wireless waves are received by antenna s as signals which are in turn processed successively by the various modules in the chain. Processing can terminate in any one of the modules. In a transmitting mode initiation can be in any one of these modules. Ultimately signals are routed internally for antenna s to transmit as wireless waves.

The architecture of system is presented for purposes of explanation and not of limitation. Its particular subdivision into modules need not be followed for creating embodiments according to the invention. Furthermore the features of the invention can be performed either within a single one of the modules or by a combination of them.

Diagram includes shelves where merchandise with RFID tags such as tag may be located. The person with rogue reader may be at any location on the premises or even off the premises.

The system for detecting the rogue reader and possibly remedying any damage may include RFID listening device s which may include RF wave detectors not shown or RFID readers. The RFID readers may include POS station readers such as or may include readers dedicated to the detecting purpose.

In order to accurately determine a location of the rogue reader and to cover the entire premises antennas of the RFID readers e.g. L L L L or the readers themselves may be located in various locations on the premises or even off the premises.

The readers may listen to communication between the tags and readers including a rogue reader and vice versa and provide captured information to monitoring agent which may capture an identifier associated with an affected tag from the communication such as an identifier associated with a command transmitted to the affected tag or from the affected tag and set an alert condition. The determination that the identifier is as a result of an illicit command or from a rogue reader may be made by comparing the identifier to a database of legitimate identifiers.

Monitoring agent may also determine the tag s location or the rogue reader s location jam the tag or the reader or perform other actions based on the set alert condition such as issuing an audible or visible alert sending a message and the like.

RFID reader system may include legitimate reader listening devices through N monitoring agent and database as well as tags . During an example operation rogue reader may transmit an illicit command .

The rogue reader as the other readers communicates over a specifically defined channel typically an assigned frequency. Moreover RFID readers when communicating with tags include a time stamp in their communication such as a time stamp associated with each command. The channel of the communication and the time stamp may be referred to as attributes of the RFID reader. One or more of the tags may reply to the illicit command. The reply may also use the same channel and or include the time stamp.

Meanwhile at least one of the listening devices e.g. a reader or RF wave detector may listen to the communication and capture the channel and or the time stamp associated with the rogue reader communication from the reader transmission or the tag reply .

The captured channel and or time stamp may then be sent to the monitoring agent which may compare it to a database of known or legitimate channels or time stamps. For example the monitoring agent may query legitimate readers for the channel time stamp of their recent communications and if the captured one does not match any of those provided by the legitimate readers it is likely from a rogue reader.

If the communication is determined to be as a result of a command from the rogue reader the monitoring agent may set an alert condition e.g. set a flag as a result of this determination such that the system or an administrator monitoring the system can take appropriate actions.

As discussed above readers may include a time stamp in their communication with tags. A system according to embodiments may capture commands and associated time stamps from readers in the area. Even if a transmitting reader does not include a time stamp the listening device may assign the time stamp itself. Additional information that may saved along with each captured command may include an identifier associated with the command or identification of an antenna through which the communication was captured. The information is illustrated in the figure in form of a table but may be stored in any form.

The first table shows captured commands and time stamps from the listening device . While capturing reader to tag tag to reader communications or both a monitoring agent of the system may also receive information from legitimate readers associated with the system regarding commands they recently transmitted and associated time stamps . This information may be received automatically from the legitimate readers or upon querying the legitimate readers.

The second table illustrates data provided from legitimate readers. Although not shown or needed associated commands or other information may also be stored for additional purposes.

The third table shows a comparison of the captured and provided commands associated time stamps associated antenna locations and the decision based on the comparison .

In the example of the KILL command with identifier DD and time stamp TS is only captured by listening to communications and not provided by any legitimate reader. Therefore the system can determine that this command was from a rogue reader. Furthermore a location of the rogue reader may be estimated from the antenna location information received from the listening device s .

Communication between RFID readers and tags is accomplished utilizing predefined channels. Each channel has a center frequency and a band around the center frequency where the transmission can occur. Typically a portion of the RF spectrum is allocated for RFID communications with a number of available channels. The width of the spectrum the number of channels the width of each channel as well as other parameters are commonly dictated by the regulations in a given country or region.

Diagram shows a listing of channels allowed for RFID communications in the U.S. The allowed spectrum begins with channel centered around 902.75 MHz and a channel width of 500 kHz. Each channel after that is 500 kHz away from the previous one totaling 50 channels. European spectrum used by the EU countries as well as other countries in the region is located between 865.0 MHz and 868.0 MHz with 200 kHz apart channels total 15 each channel having a 200 kHz width.

The first table shows captured commands and associated communication channels from the listening device . While capturing reader to tag tag to reader communications or both a monitoring agent of the system may also receive information from legitimate readers associated with the system regarding commands they recently transmitted and associated channels . This information may be received automatically from the legitimate readers or upon querying the legitimate readers.

The second table illustrates data provided from legitimate readers. Although not shown or needed associated commands or other information may also be stored for additional purposes.

The third table shows a comparison of the captured and provided commands associated channels associated antenna locations and the decision based on the comparison .

In the example of the KILL command with identifier DD transmitted on channel is only captured by listening to communications and not provided by any legitimate reader. Therefore the system can determine that this command was from a rogue reader. Furthermore a location of the rogue reader may be estimated from the antenna location information received from the listening device s .

The invention additionally includes programs and methods of operation of the programs. A program is generally defined as a group of steps or operations leading to a desired result due to the nature of the elements in the steps and their sequence. A program is usually advantageously implemented as a sequence of steps or operations for a processor such as the structures described above.

Performing the steps instructions or operations of a program requires manipulation of physical quantities. Usually though not necessarily these quantities may be transferred combined compared and otherwise manipulated or processed according to the steps or instructions and they may also be stored in a computer readable medium. These quantities include for example electrical magnetic and electromagnetic charges or particles states of matter and in the more general case can include the states of any physical devices or elements. It is convenient at times principally for reasons of common usage to refer to information represented by the states of these quantities as bits data bits samples values symbols characters terms numbers or the like. It should be borne in mind however that all of these and similar terms are associated with the appropriate physical quantities and that these terms are merely convenient labels applied to these physical quantities individually or in groups.

The invention furthermore includes storage media. Such media individually or in combination with others have stored thereon instructions of a program made according to the invention. A storage medium according to the invention is a computer readable medium such as a memory and is read by a processor of the type mentioned above. If a memory it can be implemented in a number of ways such as Read Only Memory ROM Random Access Memory RAM etc. some of which are volatile and some non volatile.

Even though it is said that the program may be stored in a computer readable medium it should be clear to a person skilled in the art that it need not be a single memory or even a single machine. Various portions modules or features of it may reside in separate memories or even separate machines. The separate machines may be connected directly or through a network such as a local access network LAN or a global network such as the Internet.

Often for the sake of convenience only it is desirable to implement and describe a program as software. The software can be unitary or thought in terms of various interconnected distinct software modules.

This detailed description is presented largely in terms of flowcharts algorithms and symbolic representations of operations on data bits on and or within at least one medium that allows computational operations such as a computer with memory. Indeed such descriptions and representations are the type of convenient labels used by those skilled in programming and or the data processing arts to effectively convey the substance of their work to others skilled in the art. A person skilled in the art of programming may use these descriptions to readily generate specific instructions for implementing a program according to the present invention.

Embodiments of an RFID reader system can be implemented as hardware software firmware or any combination. It is advantageous to consider such a system as subdivided into components or modules. A person skilled in the art will recognize that some of these components or modules can be implemented as hardware some as software some as firmware and some as a combination. An example of such a subdivision is now described together with the RFID tag as an additional module.

According to some embodiments a method for dealing with a rogue RFID reader communicating with an RFID tag includes capturing attributes associated with RFID readers by listening to tag to reader communications reader to tag communications or both receiving attribute information from legitimate RFID readers determining whether a captured attribute belongs to a rogue RFID reader by comparing the captured attributes and the received attributes and if a rogue RFID reader is detected setting an alert condition.

The identifier may also be captured from only the communication from the rogue RFID reader to the RFID tag or only from the backscattering by the RFID tag. The captured attribute may be forwarded to a database for determining whether the attribute belongs to a rogue RFID reader. According to other embodiments the method may further include listening to the reader to tag communications while preventing from transmitting at least one legitimate reader listening to the reader to tag communications while causing at least one legitimate reader to desist from transmitting a legitimate command to improve the listening for the rogue reader or listening to the reader to tag communications while causing at least one legitimate reader to transmit a legitimate command.

The attribute may include a time stamp associated with the captured RFID reader communication that may be compared to an authorized time window for legitimate RFID readers. Then the captured attribute may be determined as associated with a rogue RFID reader if it is outside the time window for legitimate RFID readers. The time stamp may be associated with a command transmitted by each RFID reader.

The attribute may also be a channel associated with the captured RFID reader communication that is compared to an authorized channel for legitimate RFID readers. The determination whether the captured channel is associated with a rogue RFID reader may be made based on the captured channel not matching a list of authorized channels provided by legitimate RFID readers. The channel may include a transmit frequency employed by each RFID reader. The attribute may further be a pattern of communication associated with a reader and the determination whether or not the reader is a rogue reader may be made based on whether or not the pattern matches one assigned to a legitimate reader. The communication pattern may be a sequence of commands or a timing of commands.

The attribute may also be a time stamp associated with a captured channel of the RFID reader communication and the method may include comparing the captured time stamp and channel to an authorized time stamp and channel combination for legitimate RFID readers.

The alert condition may be set respective to a certain location within premises where the RFID tag is located. A handle transmitted by the tag may also be captured and the certain location determined from the captured handle.

According to further embodiments the method may also include issuing an audible alert issuing a visible alert issuing an electronic alert or setting a flag if the alert condition is set. The issued alert may be located remotely enough from a certain location where the RFID tag is located so that the issued alert is not detectable at the certain location. On the other hand the issued alert may be located proximately enough to a certain location where the RFID tag is located so that the issued alert is detectable at the certain location. Issuing the alert may also include sending a message to an operator. The issued alert itself may designate the certain location where the RFID tag is located.

According to yet other embodiments the method may include causing a jamming signal to be transmitted so as to jam the tag to rogue reader communications or to jam the rogue reader from communicating with tags. The method may also include recording transmissions by the readers or the RFID tags at a certain location if the alert condition is set where recording the transmissions may include recording a reader identification number with each recorded RFID reader transmission. One of the recorded transmissions may be determined as having been transmitted illegally by the rogue reader and the RFID tag identified from the illegal transmission. Then an effect of the illegal transmission on the RFID tag may be reversed or an item on which the RFID tag is hosted identified and the RFID tag replaced with another RFID tag on the host item.

Further embodiments may include a system including an RFID listening device and one or more monitoring agents for performing the operations described above as well as an interface converter operable to control a utility of a reader that includes the operations discussed above.

An economy is achieved in the present document in that a single set of flowcharts is used to describe methods in and of themselves along with operations of hardware and or software and or firmware. This is regardless of how each element is implemented.

According to optional operation a system comprising RFID reader s controller s and or RF wave detector s is configured to detect illicit commands In the subsequent operation one of the RFID readers or the RF wave detector begins listening to tag to reader reader to tag or both communications.

At next optional operation a command is detected as a result of the listening operation. This operation is followed by operation where a time stamp or channel e.g. frequency associated with the detected command is captured. According to other embodiments the time stamp channel may be associated with other information included in the communication and not necessarily a command.

At decision operation following operation a determination is made whether the captured time stamp channel is as a result of a command from a legitimate reader. This determination may be made by a number of ways as discussed previously. If the decision is affirmative the detected command is legitimate and processing returns to operation . If the decision is negative the detected command is illicit because the captured time stamp or channel is not associated with a legitimate reader and processing continues to operation .

At operation an alert condition is set based on the determination that the captured time stamp channel did not result from communication of a legitimate reader. The system may perform a number of actions such as those discussed previously following the setting of the alert condition. Processing returns to operation from operation to continue listening to further tag to reader communications reader to tag communications or both.

The operations included in process are for illustration purposes. Dealing with rogue readers using reader time stamps and or communication channels may be implemented by similar processes with fewer or additional steps as well as in different order of operations using the principles described herein.

The above described feature can be implemented by a so called utility of an RFID reader. For example a utility can include one or more of the above described components operational processing blocks an article of manufacture etc. The invention further provides interfacing to expose a functionality of this utility to an agent as is described in more detail below.

More particularly utility includes capture of time stamps channels from listened to tag to reader communications reader to tag communications or both and determination of whether or not the communication or a command included in the communication is from a legitimate reader based on the captured identifier.

Architecture additionally includes an interface converter and an agent . Agent interface converter and utility can be implemented in any way known in the art. For example each can be implemented in hardware middleware firmware software or any combination thereof. In some embodiments agent is a human.

The invention also includes embodiments of interface converter and methods of operation of an interface converter such as interface converter . Interface converter thus enables agent to control utility . Interface converter is so named because it performs a conversion a change as will be described in more detail below.

Between interface converter and agent and utility there are respective boundaries . Boundaries are properly called interfaces in that they are pure boundaries as is the above described air interface.

In addition it is a sometimes informal usage to call the space between boundaries and which includes interface converter an interface . Further it is common to designate this space with a double arrow as shown with an understanding that operations take place within the arrow. So while interface is located at a boundary between agent and utility it is not itself a pure boundary. Regardless the usage of interface is so common for interface converter that this document sometimes also refers to it as an interface. It is clear that embodiments of such an interface can be included in this invention if they include an interface converter that converts or alters one type of transmission or data to another as will be seen below.

Agent can be one or more layers in a layered architecture. For example agent can be something that a programmer programs to. In alternative embodiments where agent is a human interface converter can include a screen a keyboard etc. An example is now described.

Returning to interface converter can be implemented in any number of ways. One such way is as a software Application Programming Interface API . This API can control or provide inputs to an underlying software library and so on.

Transmissions can be made between agent interface converter and utility . Such transmissions can be as input or can be converted using appropriate protocols etc. What is transmitted can encode commands data etc. Such transmissions can include any one or a combination of the following a high down transmission HDNT from agent to interface converter a low down transmission LDNT from interface converter to utility a low up transmission LUPT from utility to interface converter and a high up transmission HUPT from interface converter to agent . These transmissions can be spontaneous or in response to another transmission or in response to an input or an interrupt etc.

Commands are more usually included in transmissions HDNT and LDNT for ultimately controlling utility . Controlling can be in a number of manners. One such manner can be to install utility or just a feature of it. Such installing can be by spawning downloading etc. Other such manners can be to configure enable disable or operate utility or just a feature of it. These commands can be standalone or carry parameters such as data etc. In some embodiments interface converter can convert these commands to a format suitable for utility .

Data is more usually included in transmissions HUPT and LUPT. The data can inform as to success or failure of executing an operation. The data can also include tag data which can be both codes read from tags and data about reading tags such as time stamps date stamps etc. The data can also include listened to reader to tag communications tag to reader communications or both. In some embodiments interface converter can convert the data to a format suitable for agent including in some cases aggregating filtering merging or otherwise altering the format or utility of the data.

It should be noted that what passes across a single pure boundary can be unchanged by the mere definition of what is a pure boundary. But what passes through interface converter can be changed or not. More particularly high down transmission HDNT can be being encoded similarly to or differently from low down transmission LDNT. In addition low up transmission LUPT can be being encoded similarly to or differently from high up transmission HUPT. When different it can be attributed to interface converter which performs a suitable change or conversion of one transmission to another. The change or conversion performed by interface converter is for exposing the functionality of utility to agent and vice versa. In some embodiments a command is converted but a parameter is passed along without being converted. Plus what is not converted at one module may be converted at another. Such modules taken together can also form an interface converter according to embodiments.

Agent interface converter and utility can be implemented as part of a reader or as a different device. For being implemented as part of a reader suggests a scheme where agent interface converter and utility can be implemented in connection with respective reader modules or listener modules that are suitable depending on the requirements.

The above specification examples and data provide a complete description of the manufacture and use of the composition of the embodiments. Although the subject matter has been described in language specific to structural features and or methodological acts it is to be understood that the subject matter defined in the appended claims is not necessarily limited to the specific features or acts described above. Rather the specific features and acts described above are disclosed as example forms of implementing the claims and embodiments.

