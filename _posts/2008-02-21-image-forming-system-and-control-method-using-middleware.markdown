---

title: Image forming system and control method using middleware
abstract: A job control device, a multifunction device, and an operation method thereof are provided. The job control device includes a middleware unit that supports connection with a multifunction device comprising multiple devices having independent functions, and a job control unit that controls performing of a job by at least one device from among the plurality of devices through the middleware unit. A multifunction device includes a multiple devices that have independent functions and a middleware unit that requests a job call to the job control device. A device, from among the plurality of devices, called from the job control device through the middleware unit executes a corresponding function.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08804164&OS=08804164&RS=08804164
owner: Samsung Electronics Co., Ltd.
number: 08804164
owner_city: Suwon-Si
owner_country: KR
publication_date: 20080221
---
This application claims the benefit of Korean Application No. 2007 63034 filed Jun. 26 2007 in the Korean Intellectual Property Office the disclosure of which is incorporated herein by reference.

Aspects of the present invention relate to a job control device a multifunction device and an operation method thereof. More particularly aspects of the present invention relate to a job control device and a multifunction device designed to easily cope with a change in job control software and an operation method thereof.

In the past the electronic devices that were in use such as printers scanners or facsimile machines generally only had a single function for each single device. Today however multifunction devices which have diverse functions in one unit have become widespread.

The devices are grouped together in the multifunction device to provide functions such as copying and printing. To this end software is required to control the devices in the multifunction device . A piece of software that performs such a task is called a job control unit .

For example if a user inputs a command through a user interface UI unit in order to carry out copying and the input command is received by the job control unit the job control unit directs the scanner to perform scanning and directs the printer to print the scanned data.

The multifunction device provides diverse functions such as N up copying reduced or enlarged copying and transmission of copies to a host server as well as simple copying. Such diverse functions require a change in the job control unit . The job control unit is changed according to the requirements of a user or the situation of a manufacturer. In addition the job control unit is changed to suit multifunction devices whenever the multifunction devices are manufactured.

In order to facilitate the change of the job control unit a solution multifunction device has been described. There are two types of solution multifunction devices. One is installed with a platform inside to download and execute a program suitable for the user environment thereof. The other controls functions in a network environment.

Building a platform and providing an interface environment using such solution multifunction devices is very expensive. In order to build a platform the hardware used includes a high capacity memory and a high performance central processing unit CPU and a test environment for applications is necessary. Furthermore in order to use the network environment a basic environment that uses interface functions of a solution multifunction device on the web such as the Site Open application programming interface SOA has to be built.

An aspect of the present invention provides a job control device to facilitate the change of job control software without additional hardware by controlling jobs between a host and a multifunction device based on a middleware environment.

According to an embodiment of the present invention there is provided a job control device comprising a middleware unit that supports connection with a multifunction device comprising a plurality of devices having independent functions and a job control unit that controls a performing of a job by at least one device from among the plurality of devices through the middleware unit.

According to an aspect of the present invention if the multifunction device requests a job call the job control unit selects and operates a device from among the plurality of devices to perform the job.

According to an aspect of the present invention if two or more devices are needed to perform the job the job control unit selects and sequentially operates the two or more devices according to the order specified by the job.

According to an aspect of the present invention the middleware unit defines interfaces for the plurality of devices and constructs communication mechanism environmental elements of the defined interfaces.

According to another embodiment of the present invention there is provided a method of operating a job control device that controls jobs of a multifunction device comprising a plurality of devices having independent functions the operation method comprising receiving a request for a job call from the multifunction device and selecting and controlling a job of at least one device from among the plurality of devices to execute a function specified by the job through a middleware unit that supports connection with the multifunction device.

According to an aspect of the present invention in the controlling of the job if the multifunction device requests the job call a device to perform the job is selected from among the plurality of devices and is operated.

According to an aspect of the present invention in the controlling of the job if two or more devices are needed to perform the job the job control unit selects and sequentially operates the two or more devices according to the order specified by the job.

According to an aspect of the present invention the operation method further comprises defining interfaces for the plurality of devices and constructing communication mechanism environmental elements of the defined interfaces.

According to an aspect of the present invention the middleware unit executes middleware programming such as Common Object Request Broker Architecture CORBA Remote Method Invocation RMI or Component Object Model COM .

According to another embodiment of the present invention there is provided a multifunction device comprising a plurality of devices that have independent functions and a middleware unit that requests a job call to a job control device wherein a device from among the plurality of devices called from the job control device through the middleware unit executes a corresponding function.

According to an aspect of the present invention the multifunction device further comprises a user interface unit that receives a job execution request signal from a user.

According to an aspect of the present invention the job control device is a user terminal or a job control dedicated device.

According to an aspect of the present invention after the device called from the job control device executes the function the middleware unit informs the job control device of the result of the operation of the device.

According to an embodiment of the present invention there is provided an method of operating a multifunction device comprising a plurality of devices having independent functions the operation method comprising requesting a job call through a middleware unit which supports connection with a job control device and performing a function of a device from among the plurality of devices called from the job control device through the middleware unit.

According to an aspect of the present invention the method further comprises receiving a job execution request signal from a user.

According to an aspect of the present invention the job control device is a user terminal or a job control dedicated device.

According to an aspect of the present invention the middleware unit executes middleware programming such as Common Object Request Broker Architecture CORBA Remote Method Invocation RMI or Component Object Model COM .

According to another embodiment of the present invention there is provided a multifunction device comprising a plurality of devices having independent functions and a job control device comprising a first job control unit that controls a performing of a job by at least one device from among the plurality of devices wherein the job control device includes a first middleware unit that supports connection of the job control unit with the multifunction device to control a performing of a job by at least one device from among the plurality of devices and wherein the multifunction device includes a second middleware unit that supports connection of the multifunction device with the job control device to provide a job call requests to the job control device.

Additional aspects and or advantages of the invention will be set forth in part in the description which follows and in part will be obvious from the description or may be learned by practice of the invention.

Reference will now be made in detail to the present embodiments of the present invention examples of which are illustrated in the accompanying drawings wherein like reference numerals refer to the like elements throughout. The embodiments are described below in order to explain the present invention by referring to the figures.

The job control device and the multifunction device are connected to each other through middleware. Generally the term middleware refers to software that connects two separate pieces of software. Middleware applied to aspects of the present invention may take the form of Common Object Request Broker Architecture CORBA Remote Method Invocation RMI and or Component Object Model COM but is not limited thereto.

The job control device comprises a first middleware unit and a job control unit . If the job control device is a user terminal such as for example a computer a personal digital assistant etc. the job control device can be installed with diverse applications and a printer driver as well as the first middleware unit and a job control unit . Since printer drivers are well known in the related art a detailed description of printer drivers is not repeated. Since the multifunction device also includes a middleware unit in order to differentiate the middleware unit in the job control device and the middleware unit in the multifunction device the middleware in the job control device is referred to as the first middleware unit and the middleware unit in the multifunction device is referred to as the second middleware unit . The first middleware unit and the second middleware unit execute the middleware software.

The first middleware unit mediates a connection between the job control device and the multifunction device . For example the first middleware unit transmits signals from the multifunction device to the job control unit and transmits signals from the job control unit to the multifunction device . The first middleware unit defines interfaces and controls jobs for a plurality of devices in the multifunction device . The definition of the interfaces for the plurality of devices includes the name of the interface a factor to provide when the interface is called and a type of factor.

In order to define interfaces for the plurality of devices an interface definition language IDL is used. If interfaces for the plurality of devices are defined using the IDL a skeleton file which consists of a server dedicated source code and a stub file which consists of a client dedicated source code are generated by compilation using a pre determined programming language. The first middleware unit executes a connection to the plurality of devices using these files.

The job control unit controls at least one device of the multifunction device to perform a certain function. At times two or more devices may be used to execute a single function. For example to perform scanning a document is scanned and printed using the scanner and printer . To perform faxing a fax document is received and printed using the facsimile machine and the printer . The job control unit controls two or more devices in sequence. Control over the sequence of the use of devices is referred to as flow control. 

The job control unit uses the flow control in which one device completes its operation and then another device is made to operate to control a single function of the multifunction device .

The multifunction device comprises the second middleware unit a user interface unit and the plurality of devices . In order to execute a job the second middleware unit requests a job call to the job control device . When a job execution request signal is input from a user through the user interface unit or is input from the job control device a job is executed. A job execution request signal is input from the job control device through a printer driver installed in the job control device and is received by the multifunction device via a network interface. For example the job execution request signal can be received through a cable connecting the multifunction device and the job control device or can be received wirelessly.

If the middleware is implemented as CORBA the second middleware unit in the multifunction device can request a job call to the first middleware unit in the job control device through an object request broker ORB . An ORB is a program that acts as a broker from when a client requests a service from a distributed object until the completion of that request.

The user interface unit receives a job execution request signal from a user. The user can input a job execution request signal using a menu provided with the multifunction device or through a dedicated key but is not limited thereto.

The plurality of devices comprises devices having an independent function such as a printer a scanner a facsimile machine and a medium . These devices are given as examples and the possible range of devices is not limited thereto. Accordingly other devices may be included among the plurality of devices or one or more of the devices named above may be excluded and other functionalities such as copying can be provided.

The printer prints print data provided from the job control device or print data stored in the multifunction device . The scanner scans a document input to the multifunction device and generates a scan image. The facsimile machine transmits fax data to other multifunction devices or other facsimile machines over a telephone network or receives fax data from other multifunction devices or other facsimile machines over the telephone network.

The medium stores data used or generated by other devices. The medium may be a storage medium such as a hard disk drive HDD a secure digital card SD optical media or a smart card. The medium may store data initially generated in the flow control of the job control unit .

For example in order to perform copying the job control unit operates the scanner to generate a scan image confirms whether the scanner has completed its operation and operates the printer . The medium temporarily stores the scan image between the completion of the scanning and the beginning of the printing.

The job control system in has a similar structure to the job control system described with reference to so identical elements in the two embodiments are designated with the same reference numerals. Furthermore the description of identical elements is not repeated and only new elements are explained below.

The job control device comprises the first middleware unit and a first job control unit . The job control device may be a user terminal or a job control dedicated device. The first middleware unit has the same function as the first middleware unit of and the first job control unit has the same function as the first job control unit of .

The multifunction device comprises the second middleware unit a user interface unit a plurality of devices and a second job control unit . The second middleware unit the user interface unit and the plurality of devices have the same functions as the corresponding devices of .

The second job control unit performs functions of the conventional job control unit shown in . Accordingly the plurality of devices can be controlled selectively by the first job control unit in the job control device or by the second job control unit in the multifunction device .

When the plurality of devices is controlled by the second job control unit in the multifunction device the first middleware unit and the second middleware unit are not used so that the controlling by the second job control unit in the multifunction device has a more rapid processing speed than the controlling by the first job control unit in the job control device .

However it is difficult to change the software of the second control unit so if a change in software is needed the change in software can be accomplished by changing the first job control unit . Accordingly the first job control unit or the second job control unit can be selectively used.

After receiving the job call through the first middleware unit the job control unit determines what devices are needed to process the job from among the plurality of devices . If it is determined in operation S Y that two or more devices are needed to process the job the job control unit operates the first of the two or more devices in the order of job execution through the first middleware unit in operation S.

In operation S the device that executed the corresponding job by control of the job control unit informs the job control unit of the result of its operation through the second middleware unit and the job control unit is notified of the result of the operation of the device through the first middleware unit .

Subsequently in operation S the job control unit operates another of the two or more devices to perform the next function according to the flow control that is in the order of the execution of the job.

In operation if it is determined in operation S N that only a single device is needed to perform the job the job control unit executes the single device needed to perform the job in operation S without the need for the flow control.

If the job execution request signal is input the second middleware unit requests a job call to the job control device in operation . The job control device receives the request for the job call from the multifunction device through the first middleware unit .

Subsequently in operation S if the second middleware unit receives an interface call for a device from the job control device the device performs its function.

As can be appreciated from the above description a job control device a multifunction device and an operation method thereof facilitate the change of job control software without additional hardware by controlling jobs between a host and a multifunction device based on a middleware environment.

Furthermore the host utilizes a middleware environment to control the multifunction device so a rapid response speed is provided.

Although a few embodiments of the present invention have been shown and described it would be appreciated by those skilled in the art that changes may be made in this embodiment without departing from the principles and spirit of the invention the scope of which is defined in the claims and their equivalents.

