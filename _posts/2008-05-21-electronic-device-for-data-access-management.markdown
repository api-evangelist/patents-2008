---

title: Electronic device for data access management
abstract: An application makes a processor issue a first file access command to a middleware in order to access a file. In response to the first file access command, the middleware makes the processor periodically determine whether file access operation having a higher priority level than file access operation involved with the first file access command is being performed and, in the case where an affirmative determination is made, issue a second file access command corresponding to the first file access command within redundant bandwidth obtained by subtracting guaranteed bandwidth of the high-priority file access from the maximum bandwidth available for accessing the file storage.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07895373&OS=07895373&RS=07895373
owner: Kyocera Mita
number: 07895373
owner_city: 
owner_country: JP
publication_date: 20080521
---
This application relates to and claims priority rights from Japanese Patent Application No. 2007 135281 filed on May 22 2007 the entire disclosure of which is hereby incorporated by reference herein.

The present invention relates to an electronic device provided with a file storage auxiliary storage unit and particularly to an electronic device in which two or more file accesses to the file storage made conflict with each other.

In the case where two or more file access requests from applications to the same storage means made conflict with each other in an existing file system provided by an operating system the access operations with respect to the storage means are processed in a time division manner in general. shows a file access operation state in a file system in the case where two or more file access requests from applications made conflict with each other. Although shows a portion in which access requests conflict with each other as simultaneous access operations time division control is carried out actually.

In this case two or more file access requests are apparently processed in parallel which is favorable to a multiple application environment. However in the parallel processing the file access speed may decrease and the expected performance may not be attained.

In the case where an image forming apparatus has the configuration as described above for a file access request requiring real time processing such as one relating to a print job it is preferable to process the request under guaranteeing certain level of bandwidth referred to as bandwidth guarantee . Further there may be a case where it is necessary to process a file access request that does not require real time processing such as one relating to a setting value change simultaneously with the file access request requiring real time processing. The bandwidth for file access refers to the amount of accesses transfer data amount to a storage per unit time and is represented as e.g. 1.5 Gbps.

Jpn. Pat. Appln. Laid Open Publication No. 2004 104212 discloses a file system in which in the case where two or more file access requests conflict with each other a file access request having a higher priority level is preferentially processed to thereby guarantee its bandwidth while a file access request having a lower priority level is processed simultaneously.

Development of a file system forming the basis of a computer system of an image forming apparatus imposes a great burden on application vendors. Such a problem occurs not only in an image forming apparatus but also in other electronic device provided with a file storage.

The present invention has been made in view of the above problem and an object of the present invention is to provide an electronic device capable of simultaneously processing a file access request having a higher priority level and a file access request having a lower priority level under guaranteeing bandwidth for the file access having a higher priority level without any modification of an existing file system in the case where two or more file access requests to the same storage made conflict with each other.

According to a first aspect of the present invention there is provided an electronic device including a processor a file storage for storing a plurality of files and a program storage. The program storage stores an application a middleware and an existing file system for instructing the processor to perform file access operation on the file storage. The application the middleware and the file system operate by the processor.

The application makes the processor issue a first file access command to the middleware in order to access any of the plurality of files.

In response to the first file access command the middleware makes the processor periodically determine whether file access operation having a higher priority level than file access operation involved with the first file access command is being performed. In the case where an affirmative determination is made the middleware makes the processor issue to the file system a second file access command corresponding to the first file access command within redundant bandwidth obtained by subtracting guaranteed bandwidth of the high priority file access from the maximum bandwidth available for accessing the file storage.

According to the configuration of the first aspect when two or more file access commands issued from one or more applications to the same file storage conflict with each other the middleware periodically determines that file access operation having a higher priority level is performed by the file system and issues the second file access command which corresponds to the first file access command within redundant bandwidth obtained by subtracting guaranteed bandwidth of the high priority file access from the maximum bandwidth available for accessing the file storage. Thus it is possible to simultaneously process a file access request having a higher priority level and a file access request having a lower priority level under guaranteeing bandwidth for the file access having a higher priority level without any modification of an existing file system in the case where two or more file access requests made to the same storage conflict with each other.

Other objects features and advantages of the present invention will become more readily apparent from the following description.

In the image forming apparatus an EEPROM E an EEPROM E a DRAM D an HDD an operation panel a scanner S a printer P an NIC a facsimile modem and a compressing expanding ASIC Application Specific Integrated Circuit are connected to an MPU through an interface . shows a plurality of interfaces as one block for the sake of simplification.

The EEPROMs E and E are e.g. flash memories. A BIOS Basic Input Output System is stored in the EEPROM E. Softwares to be described later are stored in the EEPROM E. The DRAM D is used as a working area and HDD is used as a data storage area.

The scanner S is used for an image input in scan operation copy operation and facsimile transmission. The printer P as an image output unit has a print engine a fixing unit a sheet supply section a sheet feeding section and a sheet discharge section. In printing operation the printer P forms an electrostatic latent image on the surface of a photoconductor drum as the print engine based on supplied bit map data develops the electrostatic latent image with a toner transfers and fixes a toner image onto a recording sheet and finally discharges the recording sheet onto which the toner image has been fixed.

The NIC is connected to a host computer not shown on a network through a wired or wireless communication medium to be used in a print job E mail transmission reception and Internet facsimile transmission. The facsimile modem is used for the facsimile transmission.

The compressing expanding ASIC is used as a co processor of the MPU . The compressing expanding ASIC has two ports respectively for image compression and image expansion and can execute up to four instructions in parallel.

The image forming apparatus has as software i.e. computer programs a device driver group an OS a middleware and an application group .

The device driver group is located in the lower layer of the OS and composed of a plurality of device drivers corresponding to various hardware devices.

The OS is a versatile operating system such as Linux registered trademark and provides basic functions to the application group .

The middleware is software that resides between the application group and OS and uses various basic functions of the OS through a second API Application Programming Interface which is an aggregation of functions to provide to the application group higher applied functions than the OS does.

The application group includes a print application a copy application and the like and uses various basic functions of the OS through a second API or uses various applicable functions of the middleware through the first API .

The image forming apparatus has various software components in order to achieve bandwidth control according to the present invention. More specifically the image forming apparatus has a device driver for HDD for controlling the HDD in the device driver group a file system for HDD in the OS an access command sorting section a high priority bandwidth controller a low priority bandwidth controller and an access state management section in the middleware and a high priority application and a low priority application in the application group .

Further the image forming apparatus has as callable functions a file access second API in the second API and a file access first API in the first API .

The file system for HDD manages files stored in the HDD . More specifically the file system for HDD has a function for receiving a file access command instructing file input and output file generation or file deletion from the middleware and requesting the device driver for HDD to perform a function corresponding to the command. Further the file system for HDD provides a file protection function based on the access attribute such as Readable writable or Write disabled a check function of access authority according to each user and the like.

An example of the file access command issued from the middleware to file system for HDD includes those fopen fread fwrite having a file interface conforming to ANSI C standard which are included in the file access second API

The access command sorting section receives a file access command for the middleware from the application group and determines according to its priority to which of the high priority bandwidth controller or low priority bandwidth controller the file access command should be transmitted.

An example of the file access command issued from the application group to middleware includes fread Middle for requesting the middleware to perform file read operation and fwrite Middle for requesting the middleware to perform file write operation which are newly created in the present invention. The above file access commands are included in the file access first API

In order to distinguish the file access command issued from the application group to middleware and that issued from the middleware to file system for HDD the former is referred hereinafter to as first file access command and latter as second file access command .

In order to control the sorting of commands a priority level is added to the option of the first file access command issued to the middleware and the access sorting section refers to the option to thereby determine the sorting behavior for example p is set as a high priority option which is used like this fread Middle p Tarou.jpg .

When called by the access command sorting section the high priority bandwidth controller notifies the access state management section of the start of file access and uses a command of the file access second API to request the file system for HDD to perform file access operation such as reading or writing. Further when receiving a notification of the completion of the file access from the file system for HDD the high priority bandwidth controller notifies the access state management section of the completion of the file access.

When called by the access command sorting section the low priority bandwidth controller acquires the access state of the high priority bandwidth controller from the access state management section and uses a command of the file access second API to request the file system for HDD to perform file access operation such as reading or writing while taking the access state of the high priority bandwidth controller into consideration in the manner as described later.

The access state management section manages the access state of the high priority bandwidth controller . Upon reception of the file access start notification the access state management section stores a value of e.g. F 1 in a common memory area of the DRAM D through the OS and device driver group . Upon reception of the file access completion notification the access state management section stores a value of e.g. F 0 in this memory area.

The high priority application is e.g. a print application. This application reads a file stored in the HDD to execute a print job. The application is previously determined to be preferentially executed. The high priority option p is added to the first file access command that the high priority application issues.

The low priority application is e.g. a setting changing application. This application reads a setting file stored in the HDD to execute a job changing the setting. Although a program relating to the setting change may be included in each application or an operation panel application it is assumed that the program is implemented independently from these applications in the first embodiment.

 S The access command sorting section receives the first file access command. Then when determining that the command option p has been added to the command the access command sorting section passes the command to the high priority bandwidth controller

 S In response to this the high priority bandwidth controller notifies the access state management section of the start of the file access or the high priority bandwidth controller calls the access state management section .

 S In response to the notification the access state management section stores a value of flag F 1 in a common memory area of the DRAM D through the OS and device driver group and notifies the high priority bandwidth controller of this action or the access state management section returns the set flag value to the high priority bandwidth controller .

 S In response to this the high priority bandwidth controller issues a file access request to the file system for HDD. That is the high priority bandwidth controller issues a second file access command corresponding to the first file access command from the high priority application

 S In response to the issued second file access command the HDD file system for HDD performs file access operation corresponding to the command through the device driver for HDD.

 S Upon completion of the processing corresponding to the second file access command the file system for HDD notifies the high priority bandwidth controller of the completion of the processing.

 S In response to this the high priority bandwidth controller notifies the access state management section of the completion of the file access.

 S In response to this the access state management section stores a value of flag F 0 in a common memory area of the DRAM D through the OS and device driver group and notifies the high priority bandwidth controller of this action.

 S The access command sorting section receives the first file access command. Then when determining that the command option p has not been added to the command the access command sorting section passes the command to the low priority bandwidth controller

 S Then in the case where the first file access command is e.g. a file reading request the low priority bandwidth controller repeats the reading operation in the manner as described below until EOF End Of File of a target file is reached. In the case where the first file access command is e.g. a file writing request the low priority bandwidth controller repeats the writing operation in the manner as described below until the file size specified by the command is reached.

 S The low priority bandwidth controller requests the access state management section to return the F value.

 S In response to this the access state management section reads the F value set in a common memory area of the DRAM D through the OS and device driver group and returns the read value to the low priority bandwidth controller

 S The low priority bandwidth controller determines whether the notified F value is 1 or not that is whether the high priority bandwidth controller requests the file system for HDD to perform file access operation. In the case of an affirmative determination the flow advances to the next step S. In the case of a negative determination the flow advances to step S.

 S The low priority bandwidth controller issues a file access command to request the file system for HDD to process only data corresponding to e.g. 256 bytes in the file specified by the first file access command. That is the low priority bandwidth controller issues a second file access command corresponding to the first file access command.

The above wait time T and file access amount corresponding to access time T are determined such that their bandwidth falls within Smax Sa which is redundant bandwidth obtained by subtracting Sa which is bandwidth referred hereinafter to as guaranteed bandwidth for guaranteeing file access made by the high priority application from Smax which is the maximum bandwidth available for accessing the HDD . Using these values the file access bandwidth S for the high priority application can be represented as S Smax T T T Sa with the result that S Sa is satisfied.

 S In response to the issued second file access command the file system for HDD performs file access operation corresponding to the command through the device driver for HDD.

 S After completion of the processing corresponding to the second file access command the file system for HDD notifies the low priority bandwidth controller of the completion of the file access operation.

 S The low priority bandwidth controller repeats the procedure from step S to step S as long as the loop condition of S is true and ends this flow when the loop condition fails.

In the example of the file access from the low priority bandwidth controller is processed first. When the file access from the high priority bandwidth controller is started the low priority bandwidth controller determines that the F value is 1 stops the file access waits for T milliseconds and then performs the file access again for T milliseconds. At the time point when the file accesses from the high priority bandwidth controller and low priority bandwidth controller are overlapped time division parallel processing is performed by the file system for HDD. With this configuration the file access from the low priority bandwidth controller can be executed within a range that does not interfere with the guaranteed bandwidth of file access from the high priority bandwidth controller

With the configuration according to the first embodiment when two or more file accesses from the application group conflict with each other the low priority bandwidth controller in the middleware performs the above bandwidth control so that it is possible to simultaneously process a high priority file access and low priority file access without modification of an existing file system while guaranteeing the high priority file access bandwidth.

Although it has been impossible to change a setting value during operation of a print job in a typical image forming apparatus the present invention allows the setting value change processing and the like to be achieved during a print job without delaying the print job.

It should be understood that the above described embodiment is an example for describing the present invention and that the present invention is not limited to this basic embodiment but all changes and modifications made without departing from the technical scope of the present invention are covered by the present invention.

For example although the bandwidth control of the middleware for the first file access command is performed according to two priority levels High and Low in the first embodiment the file access operation may be performed according to three priority levels High Middle and Low . is a view showing a file access operation state in the file system for HDD according to the three priority levels High Medium and Low . The control operation of the middleware according to a High priority file access command is the same as that shown in . In the control operation of the middleware according to a Middle priority file access command a step in which the start of access operation is notified to the access state management section in the same manner as step S shown in is added before step S of . In response to this the access state management section sets 1 in a flag FF different from the flag F. Further the control operation of the middleware according to a Low priority file access command is performed as follows in the case where the flag F 0 and flag FF 0 the middleware does not perform the bandwidth control but directly passes the access request to the file system for HDD in the case where F 1 and FF 0 or F 0 and FF 1 the middleware performs the same processing as that shown in further determines whether FF 1 in step S and in the case of an affirmative determination advances to step S and in the case where F 1 and FF 1 the middleware performs the same processing as that shown in but waits for a time longer than the T in step S or makes an access request in step S such that access time becomes shorter than the access time T in step S to thereby guarantee High and Middle priority file access bandwidth.

The bandwidth control according to the present invention can be applied not only to an image forming apparatus but also to an electronic device of any type as long as it includes the application group the middleware the file system for HDD the device driver for HDD and the HDD according to the present invention.

Further a target target of file access of the bandwidth control according to the present invention is not limited to the HDD but may also be applied to an auxiliary storage unit such as an MO Magneto Optical disk or a flash memory.

Although the priority is added on an application basis in the first embodiment the priority may be added on a job basis.

Although the image forming apparatus according to the first embodiment is one with multiple applications it may be one having an integrated application capable of executing a plurality of jobs by one application.

Further the functions of the middleware according to the first embodiment may be included in an application itself.

