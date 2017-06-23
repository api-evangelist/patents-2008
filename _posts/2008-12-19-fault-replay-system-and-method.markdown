---

title: Fault replay system and method
abstract: A fault replay system uploads part or all of a log file from a subject system and replays the events detailed within the log file upon physical copies of devices present in the subject system. The replay of the log file events aid the determination of at which event a fault occurred and improves the accuracy of fault determination.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09064043&OS=09064043&RS=09064043
owner: NCR Corporation
number: 09064043
owner_city: Duluth
owner_country: US
publication_date: 20081219
---
The present invention relates to a fault replay system and method. More particularly but not exclusively it relates to a synchronous fault replay system and method. Even more particularly but not exclusively it relates to a synchronous fault replay system and method for a self service terminal SST .

Fault diagnosis in highly complex and heavily used systems such as automated teller machines ATMs is difficult in the situation where all of the applications executed on the system are provided by the system s vendor due to the diverse and complex nature of the interactions between software and hardware. The complexity of these interactions are increased further when applications run on the system are not provided by the system s vendor but are rather provided by the customer operating the system as the vendor has no control of the syntax and command set used by the customer derived application. This results in the diagnosis of faults with a component device of the system or within the system s software stack being extremely difficult to diagnose remotely. In particular if the fault is associated with the system s software stack it could have occurred at any level from the device firmware to the customer derived application software itself. The diagnosis of such faults is notoriously problematic.

Attempts to diagnose these faults often requires an engineer to try and recreate the fault at a test system. This is labor intensive and is not guaranteed to reproduce the fault as there often too many interacting factors such as historical device usage gaps in log entries etc. to allow the engineer to recreate the fault manually.

Another method used to determine the cause of the fault is the manual examination of log data and instrumentation detail from the failed device and log data of the device s software stack. Such manual examination of log data is labor intensive and due to the high volume of data to be reviewed and the interaction of parameters critical events can be overlooked. This can result in the fault being either misdiagnosed or failing to be diagnosed.

According to a first aspect of the present invention there is provided a method of fault replay comprising the steps of 

The method may comprise comparing the activity of the test device to corresponding data in the log file in order to identify differences therebetween.

The software application may use an application programming interface API . The term API is used herein to relate to a software package which specifies an interface and behavior of the identifiers specified in the interface. The API does not control how the behavior is implemented by entities external of the interface. The API may be CEN XFS.

The method may comprise sensing a fault condition in a subject device or application prior to step iii .

The method may comprise delaying the replay of subsequent entries in the log file by a period equal to the period indicated by their respective timestamps. This allows real time play back of events.

The method may comprise delaying the replay of subsequent entries in the log file by a period less than the period indicated by their respective timestamps. This allows accelerated play back of events.

The method may comprise determining whether to export the whole or a portion of the log file to the test system automatically. The method may comprise determining which portion of the log file to export to the test system based upon the nature of a fault sensed. The method may comprise determining which portion of the log file to export at the subject system. The method may comprise determining which portion of the log file to import at the test system. The method may comprise determining which portion of the log file to export based upon rules relating to the nature of a fault sensed. The export of only part of the log file reduces the amount of data transmitted over the network thereby not using unnecessary bandwith.

Furthermore the export of only part of the log file reduces the number of events that are replayed thereby reducing the time required to simulate a fault condition.

According to a second aspect of the present invention there is provided a fault replay system comprising 

The software application may use an application programming interface API . The term API is used herein to relate to a software package which specifies an interface and behavior of the identifiers specified in the interface. The API does not control how the behavior is implemented by entities external of the interface. The API may be CEN XFS.

The subject device may comprise a controller arranged to sense a fault condition in a subject device or application prior to the export of at least part of the log file to the test system.

The test system may be arranged to delay the replay of subsequent entries in the log file by a period equal to the period indicated by their respective timestamps. The test system may be arranged to delay the replay of subsequent entries in the log file by a period less than the period indicated by their respective timestamps.

The subject system may be arranged to determine whether to export the whole or a portion of the log file to the test system automatically. The test system may be arranged to determine whether to import the whole or a portion of the log file automatically. The determination of whether to export the whole or a portion of the log file may be based upon the nature of a fault sensed. The determination of whether to export the whole or a portion of the log file may be based upon rules relating to the subject device in which a fault is sensed.

The system may comprise a network arranged to place the subject system and the test system in communication.

According to a third aspect of the present invention there is provided a test system comprising at least one device or application that is a copy of at least one of a respective subject devices and or applications present on a subject system wherein the test system is arranged to receive at least a portion of a log file exported from a subject system the log file comprising request data issued from a software application to one of subject devices or applications of the subject system and at least one of response data and event data returned to the software application wherein each entry in the log file is coupled to a timestamp 

the test system is arranged to replay at least a portion of the exported log file on the test system with a delay between subsequent entries in the log file proportional to the period indicated by their respective timestamps such that activity of the test device or application follows that of the subject device or application recorded on in the log file.

The test system may be arranged to delay the replay of subsequent entries in the log file by a period equal to the period indicated by their respective timestamps. The test system may be arranged to delay the replay of subsequent entries in the log file by a period less than the period indicated by their respective timestamps.

The test system may be arranged to determine whether to import the whole or a portion of the log file automatically. The determination of whether to export the whole or a portion of the log file may be based upon the nature of a fault sensed. The determination of whether to export the whole or a portion of the log file may be based upon rules relating to the subject device in which a fault is sensed.

According to a fourth aspect of the present invention there is provided software which when executed upon a processor of a subject system causes the subject system to generate a log file comprising request data issued from a software application to a subject device or application of a subject system and at least one of response data and event data returned to the software application 

The software may be arranged to sense a fault condition in a subject device or application prior to causing the processor to export at least a portion of the log file to the test system. The software may be arranged to trigger the export of at least part of the log file upon sensing the fault condition.

The software may be arranged to trigger the export of at least part of the log file upon the processor receiving a request from the test system.

The software may be arranged to determine whether to export the whole or a portion of the log file to the test system automatically. The method may comprise determining which portion of the log file to export to the test system based upon the nature of a fault sensed. The method may comprise determining which portion of the log file to export based upon rules relating to the subject device in which a fault is sensed.

According to a fifth aspect of the present invention there is provided software which when executed upon a processor of a test device causes the test system to receive at least a portion of a log file exported from a subject system the log file comprising request data issued from a software application to one of the subject devices or applications of the subject system and at least one of response data and event data returned to the software application wherein each entry in the log file is coupled to a timestamp the software further causing the test system to replay at least a portion of the exported log file on the test system with a delay between subsequent entries in the log file proportional to the period indicated by their respective timestamps such that activity of a test device or application of the test system follows that of the subject device or application recorded in the log file.

The software may cause the test system to delay the replay of subsequent entries in the log file by a period equal to the period indicated by their respective timestamps. The software may cause the test system to delay the replay of subsequent entries in the log file by a period less than the period indicated by their respective timestamps.

The software may cause the test system to determine whether to export the whole or a portion of the log file automatically. The determination of whether to export the whole or a portion of the log file may be based upon the nature of a fault sensed. The determination of whether to export the whole or a portion of the log file may be based upon rules relating to the subject device in which a fault is sensed.

The ATM comprises a controller a data storage device a number of peripheral devices and a network connection . Typically the control processor is a PC core operating under a Microsoft Windows operating system. Normally the data storage device is a magnetic disc and may form part of the controller in some embodiments.

The controller is typically a PC core running the Microsoft Windows XP system. The controller comprises a BIOS stored in non volatile memory a microprocessor and associated main memory .

Typical peripheral devices found in the ATM comprise but are not limited to a card reader device a receipt printer device a display and associated function display keys FDKs an encrypting keypad and a dispenser device

The communications network comprises a secure network over which transactions data for transactions executed at the ATM passes to an authorization host not shown and can also connect the ATM to test system via the network connection .

The test system comprises a controller a data storage device at least one peripheral device for example an encrypting keypad and a network connection . The controller of the test system is analogous to that of the ATM except that the controller runs software to replay the events contained in the log file.

In use the ATM controller loads an operating system kernel and an ATM application program for example the APTRA XFS platform available from NCR Corporation of Dayton Ohio into the main memory . The ATM application program acts as an API mediating communications between the controller and the peripheral devices .

The application program comprises a suite of routines and objects for controlling the operation of the ATM such as providing the sequence of screens used in each transaction. The application program also comprises a number of service providers in the case of APRTA XFS these will be CEN XFS service providers. The service providers control at least one possibly many of the peripheral devices and or applications running on the ATM . For example the service provider relates to the encrypting keypad drives requests for both an encryptor device and a keyboard device that comprise the keypad . The service providers drive requests from the controller to the peripheral devices . For example the service provider relates to the encrypting keypad drives requests for both an encryptor device and a keyboard device that comprise the keypad

Typically the driving of requests involves translating any proprietary communications command data and or response data required to drive the peripheral device and monitor its performance. In an exemplary embodiment utilizing the CEN XFS standard the standard defines a programming standard for communicating with each individual class of CEN XFS service provider such that expected requests excepted responses and events associated with each service provider are defined.

The application program also comprises a trace log routine that logs trace points in a log file . The trace points comprising the log file are indicative of data sent between the service providers and the ATM application and the data sent between the service providers and the peripheral devices that has been converted into suitable respective formats for use by device drivers of the peripheral devices . The log file is stored on the data storage device .

Thus from the above exemplary trace point it can be determined that on 4 Sep. 2008 at 11 48 30.983 the XFS PIN Service Provider Device control created a MultiState controller for session 19 and request id 2292. The line of code running was at line in source file ControllerImpl.cpp. The log file contains trace points for each request response and event handled by the application and consequently may run to hundreds of thousands of trace points.

In the event of a device failure the application flags the device failure and the controller opens a communications channel via the ATM s network connection and the network to the test system . In one embodiment of the present invention an operator of the test system determines whether to upload all of the trace file or part of the log file from the data storage device based upon their experience. In an alternative embodiment the determination whether to upload part or all of the log file may be made automatically by the controller of the test system . Such an automated determination may be based upon the nature of the fault or the device upon which the fault occurred. For example a fault with the card reader may require only those log entries relating to the use of the card reader immediately prior to the fault and the fault occurrence of the card reader and controller to be uploaded. In a further example a certain fault with the keypad may require the upload of log entries relating to a series of uses of the keypad components both the encryptor device and the keypad along with their respective communications to and from the controller due to the sequential nature of keypad usage and card reader data as the data from the card reader can feed into controller operations related to the keypad

The test system is configured with at least some of the peripheral devices present at the ATM . In some instances the test system will comprise copies of all of the peripheral devices present at the ATM . In other instances only copies of those peripheral devices considered to be required to emulate the device failure are present at the test system .

As noted hereinbefore the controller of the test system is analogous to that of the ATM except in that it runs a software routine that allows the replay of entries in the log file Thus when run the software routine causes all system calls request response and event detailed in the trace points that comprise the part of log uploaded to the test system to be carried out in a synchronous manner. The controller of the test system reads trace points in from the log and issues commands to the attached peripheral devices such that the peripheral devices execute those commands in a synchronous manner. The controller logs the responses received from the attached peripheral devices such that a comparison is executed between the responses received from the peripheral devices and those in the log file received from the ATM with any difference being flagged by the controller . Typically the controller generates a file containing details of the differences such as the device to which the differences relates and the line of the source code to which the action relates. This is because any difference between the responses and the log file is indicative of a fault at the ATM. In a preferred embodiment the controller identifies the point of failure from these difference. The ability to recognize faults can be present in the controller as produced or the recognition of patterns of faults may be learnt as an expert system. In an alternative or additional embodiment. These differences can be used by an engineer to determine what the fault is this speeds up the fault determination process over the previous solution of scanning the whole log file.

The term synchronous as used herein relates to the execution of actions corresponding trace point entries in the log file in the order that they were carried out at the ATM and where time periods between the execution subsequent actions corresponding to entries in the log file are proportional to the actual time period defined by difference in timestamps of respective entries in the log file.

Typically but not exclusively the events contained in the log file will be replayed in real time where the time periods between the execution subsequent actions corresponding to entries in the log file are equal to the actual time period defined by difference in timestamps of respective entries in the log file. The replay of events contained in the log file at the test system allows the fault that occurred at the ATM to be recreated locally at the test system . Typically the test system is remote from the ATM for example it may be in a different city or even country from the ATM .

The log file and the test log file can be compared to look for differences in the responses issued by the peripheral devices to the requests issued from the controller .

Furthermore updated software can be cross checked prior to release by verifying that the execution of updated software on the test system generates the same trace point data as a previous version that is known to execute on an ATM. This can be effected by storing a trace point log file relating to the previous software release executed on the ATM locally at the test system .

Referring now to a method of fault replay comprises generating a log file comprising request data issued from a software application to a subject device or application of a subject system and at least one of response data and event data returned to the software application Step . Each entry in the log file is coupled with a timestamp Step . A portion of the log file is exported to a test system which comprise a test device or application similar to a corresponding subject device or application present in the subject system Step . At least a portion of the exported log file is replayed on the test system with a delay between subsequent entries in the log file proportional to the period indicated by their respective timestamps such that activity of the test device or application follows that of the subject device or application recorded in the log file Step .

It will be appreciated that the log file may be retained locally at the ATM subsequently downloaded on to a data carrier such as a USB drive CD or DVD. The data carrier is then used to load the log file on to the test system for replay. Although the embodiments of the present invention detailed hereinbefore are described with reference to an encrypting key pad the skilled person will realize that the teachings of the present invention are applicable to any peripheral device or application driven via a service provider of the ATM application.

It will be appreciated that although described with reference to a single ATM the present invention is equally applicable to a network of ATMs in which data to be replayed at the test system is selectively downloaded from a specific ATM in the event of a fault or failure of a peripheral device and or application of said ATM.

It will be further appreciated that although described with reference to an ATM the present invention is applicable to any suitable self service terminal SST or network of SSTs. Examples of suitable SSTs include but are not limited to an information kiosk a financial services centre a bill payment kiosk a lottery kiosk a postal services machine a check in and or check out terminal such as those used in the retail hotel car rental gaming healthcare and airline industries or the like.

It will also be appreciated that the steps of the methods described herein may be carried out in any suitable order or simultaneously where appropriate. The methods described herein may be performed by software in machine readable form on a tangible storage medium or as a propagating signal.

As described herein the SST comprises one or more modules each of which is operable to perform at least one specific function. Typically the module implements its function either in response to a customer action and or a command received from a PC core which is also a module of the SST. Non limiting examples of modules include display card reader journal printer rear operator panel encrypting keypad PC core cash dispenser etc.

Typically each module comprises a processor to enable the module to perform its function and a communications facility to enable the module to communicate with the controller but in some instances this may not be essential.

Each module comprises one or more devices that contributes to the execution of the module s respective function. Typically each device comprises a replaceable part within the module. Non limiting examples of devices include for the display module a display panel a display panel housing and the like for a cash dispense module a note thickness sensor a pick unit a presenter unit and the like.

Each device comprises one or more components configured to enable the device to contribute to the execution of the module s function. Non limiting examples of components include for a motorized card reader module a width switch a shutter a pre read magnetic head a magnetic stripe reading head and the like.

Various modifications may be made to the above described embodiment without departing from the spirit and the scope of the invention.

