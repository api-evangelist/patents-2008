---

title: Information processing device and image processing apparatus
abstract: An information processing device includes an input unit configured to input data, a processing unit configured to process the data, an output unit configured to output the data, and an execution unit configured to execute a first process, a second process, and a third process. A function of an application is provided by operating the input unit, the processing unit, and the output unit in conjunction with each other. The first process executes application management software that manages activation and termination of the application. The second process executes basic application software that provides a basic function of the information processing device. The third process executes extended application software that provides an extended function added to the information processing device.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08438567&OS=08438567&RS=08438567
owner: Ricoh Company, Ltd.
number: 08438567
owner_city: Tokyo
owner_country: JP
publication_date: 20081103
---
The present invention relates to an information processing device and an image processing apparatus that provide a function of an application by operating an input unit a processing unit and an output unit in conjunction with each other.

In these years image processing apparatuses such as MFPs Multifunction Peripherals include printer copier scanner and facsimile functions in one physical body and despite limited memory capacity have a CPU Central Processing Unit similar to that of general purpose computers to provide these functions by software application control.

For example Japanese Patent Registration No. 3679349 also published as Japanese Patent Laid Open Publication No. 2002 084383 discloses an image processing apparatus in which a platform includes a function shared by different applications. These applications can be implemented using an API Application Programming Interface for the platform. Since this image processing apparatus is provided with the platform that includes the function shared by the different applications there is no need to include the shared function in each application. Therefore it is possible to improve the efficiency in developing the applications.

Thus this image processing apparatus offers a function desired by a user by adding an application to its system or extending an application in the system.

Currently the Java trademark language of Sun Microsystems Inc. is used for function development of some of such image processing apparatuses. The Java language is independent from the installation environment the type of machines into which a function is installed and therefore is used for development of mobile phones and home appliances as well. Some image processing apparatuses use a process based UNIX trademark based OS Operating System which can split a process into multiple processes in implementation environments.

The first is the system robustness. Highly extensible image processing apparatuses may execute applications that are developed in various environments such as a self developed application that offers basic functions of the system and an application that is developed by another company hereinafter referred to as a third party vendor and is installed later to offer an extended function.

These image processing apparatuses need to prevent basic functions of the system from failing due to installation of the extended function.

In process based OSs it is common to split a process into processes of appropriate sizes to improve the system robustness. However in the case where the Java language is used for development plural applications are executed in a single process JVM Java Virtual Machine and therefore it is not practical to split the process JVM into too many processes JVMs . The JVM needs to be split into at least a JVM for executing the self developed application and a JVM for executing the third party vendor application.

As for the robustness of the Java language based system consideration needs to be given to execution of Native code and memory use. Execution of malicious Native code may cause a crash of the entire system i.e. terminate the entire system abnormally . An application using a large amount of memory may occupy the Java heap and cause an OutOfMemoryError.

The second is the easiness of application development. In the case of splitting a system into plural JVMs it is necessary to minimize the number of components that are to be affected by the multi process architecture.

For customizable systems application development using a SDK Software Development Kit needs to be easy and it is necessary to allow applications to be developed without a need to consider that the applications are to run on plural JVMs.

That is it is necessary to consider a design in which limited components software parts corresponding to a framework are affected by multi process architecture such that applications can be developed without a need to consider the multi process architecture.

In view of the foregoing the present invention is directed toward providing an information processing device and an image processing apparatus which provide a highly robust system that allows easy customization and extension of an application without a need to consider multi process architecture and that prevents basic functions of the system from being affected due to a failure of an extended function.

In an embodiment of the present invention there is provided an information processing device that includes an input unit configured to input data a processing unit configured to process the data an output unit configured to output the data and an execution unit configured to execute a first process a second process and a third process wherein a function of an application is provided by operating the input unit the processing unit and the output unit in conjunction with each other the first process executes application management software that manages activation and termination of the application the second process executes basic application software that provides a basic function of the information processing device and the third process executes extended application software that provides an extended function added to the information processing device.

In another embodiment of the present invention there is provided an information processing device that includes an input unit configured to input data a processing unit configured to process the data an output unit configured to output the data and an execution unit configured to execute a first process and a second process wherein a function of an application is provided by operating the input unit the processing unit and the output unit in conjunction with each other the first process executes application management software that manages activation and termination of the application and basic application software that provides a basic function of the information processing device and the second process executes extended application software that provides an extended function added to the information processing device.

The information processing device of the above described embodiment executes the basic application software self developed application that provides basic functions of the system and the extended application software third party vendor application that provides an added extended function in different processes and perform operations associated with the multi process architecture such as inter process communications using limited components corresponding to a framework i.e. hide the influence of the multi process architecture . Therefore the information processing device of this embodiment can provide a highly robust system that allows easy customization and extension of an application without a need to consider the multi process architecture and that prevents basic functions of the system from being affected due to a failure of an extended function.

Thus the information processing device of this embodiment allows easy development of applications by developers and can stably provide functions.

In still another embodiment of the present invention there is provided an image processing apparatus that comprises a document scanning unit configured to scan a document to obtain image data a printing unit configured to print the image data onto paper and one of the information processing devices of the above described embodiments.

The image processing apparatus of the above described embodiment can provide a highly robust system that allows easy customization and extension of an application without a need to consider the multi process architecture and that prevents basic functions of the system from being affected due to a failure of an extended function.

Thus the image processing apparatus of this embodiment allows easy development of applications by developers and can stably provide functions.

According to an aspect of the present invention it is possible to provide an information processing device and an image processing apparatus which include a highly robust system that allows easy customization and extension of an application without a need to consider multi process architecture and that prevents basic functions of the system from being affected due to a failure of an extended function.

Preferred embodiments of the present invention are described below with reference to the accompanying drawings.

First an exemplary hardware configuration of an image processing apparatus according to a first embodiment of the present invention is described below with reference to .

As shown in the image processing apparatus includes a control unit CPU Central Processing Unit a primary storage unit ROM Read Only Memory RAM Random Access Memory a secondary storage unit HD Hard Disk a network I F an external storage device I F an external device I F a display unit display panel an input unit operations unit a printing unit plotter unit and a scanner unit document scanning unit .

The control unit controls other units of the image processing apparatus and performs arithmetic operations and data processing. More specifically the control unit executes programs stored in the primary storage unit so as to process data received from an input device or a storage device and output the processed data to an output device or the storage device.

The primary storage unit stores or holds the programs such as an OS Operating System as basic software and application software to be executed and data to be processed by the control unit .

The secondary storage unit stores data related to the application software. The secondary storage unit also stores various types of information e.g. user information managed by the image processing apparatus using a DB database function and a FS File System function.

The network I F interfaces the image processing apparatus and peripheral devices that have communication functions and are connected via a network such as a LAN Local Area Network or a WAN Wide Area Network which is implemented by wired and or wireless data transmission channels.

The external storage device I F interfaces the image processing apparatus and an external storage device e.g. a storage medium drive connected via a data transmission line such as a USB Universal Serial Bus .

The external device I F interfaces the image processing apparatus and an external device e.g. a digital camera connected via a data transmission line such as a USB.

The image processing apparatus exchanges data e.g. image data with external devices i.e. sends data to receives data from writes data into and reads data from external devices via these interfaces.

The display unit and the input unit include an LCD Liquid Crystal Display with a touch panel including software keys of a GUI Graphical User Interface and key switches hardware keys respectively and serve as UIs User Interfaces for using functions of the image processing apparatus .

The printing unit outputs or prints an image on a transfer paper printing paper according to CMYK image data by an electrophotographic process including exposure latent image forming developing and transfer steps using laser beams.

The scanner unit includes a line sensor having CCDs Charge Coupled Devices an A D converter and a driving circuit for driving the line sensor and the A D converter. The scanner unit scans a document on a document scanning surface i.e. a contact glass and generates RGB 8 bit digital image data. In other words the scanner unit scans information from a document and converts the information into digital data.

Thus the image processing apparatus causes the control unit to execute the programs stored in the primary storage unit and the secondary storage unit sends control signals control commands to the appropriate units i.e. controls the appropriate units and thereby provides functions such as copier facsimile scanner and printer functions to process information managed by the image processing apparatus and information managed by a system connected to the image processing apparatus .

An exemplary software configuration of the image processing apparatus and an exemplary basic processing procedure for providing a function of the image processing apparatus are described below with reference to .

As shown in the image processing apparatus includes a user interface layer a control layer an application logic layer a device service layer and a device control layer . In the layers are arranged in a hierarchical order where an upper layer calls a lower layer.

The user interface layer offers a UI function for receiving requests for execution of functions e.g. application functions such as copier facsimile scanner and printer functions The user interface layer includes a communication server unit and a local UI unit for example.

The communication server unit receives various requests e.g. a request for a printing operation from for example a client PC Personal Computer not shown which is a peripheral device having a communication device via the network. The local UI unit receives various requests e.g. a request for a copy operation and operation settings via an operations panel not shown .

The control layer offers a function for controlling operations of executing a requested function. The control layer includes a control unit for example. More specifically the control unit connects filters in the application logic layer described below according to a requested function and controls execution of the function based on the connected filters. In this embodiment a function of the image processing apparatus refers to a single unit of service from input of a request to provision of an output that is provided by the image processing apparatus to a user. In terms of software a function of the image processing apparatus refers to an application that provides a single unit of service.

The application logic layer includes a group of parts software parts each of which provides a part of a function of the image processing apparatus . In other words the parts in the application logic layer are selectively combined to provide a function. In this embodiment since the image processing apparatus is based on software architecture called pipes and filters each of the parts is called a filter .

First the pipes and filters architecture is described. In F indicates a filter and P indicates a pipe. As shown in pipes interconnect filters. A filter converts input data and outputs the result. Then a pipe passes the output data to the next filter. That is each function of the image processing apparatus of this embodiment is a series of transformation operations that are performed on information e.g. user information and image data managed by the image processing apparatus . In a sense each function of the image processing apparatus is a combination of operations of inputting processing and outputting information managed by the image processing apparatus . Each of the input processing and output operations is a single transformation operation performed by a software part called a filter . More specifically a filter that performs an input operation is called an input filter input unit . A filter that performs a processing operation is called a process filter processing unit . A filter that performs an output operation is called an output filter output unit . The filters are independent from each other and there is basically no dependency between the filters. Therefore filters may be independently added to installed into or removed from uninstalled from the image processing apparatus .

Referring back to the application logic layer includes input filters process filters and output filters . The input filters include for example a scan filter .

The scan filter controls scanning of image data by the scanner unit and outputs the scanned image data.

The input filters also include a stored document retrieving filter not shown for reading document data image data stored in the secondary storage unit and outputting the read document data an email receiving filter not shown for receiving an email message and outputting data in the received email message a fax receiving filter not shown for receiving a fax message and outputting data in the fax message a PC document receiving filter for receiving print data from a client PC not shown and outputting the received print data and a report filter not shown for outputting setting information and history information of the image processing apparatus in a tabular form for example.

The process filters include for example a document processing filter . The document processing filter performs image processing operations combining scaling etc. on the input data.

The process filters also include a document process filter not shown for converting input PostScript data into bit map data and outputting the bitmap data i.e. performing a rendering operation .

The output filters include for example a print filter . The print filter causes the printing unit to output print input data.

The output filters also include a stored document registration filter not shown for storing input data in the secondary storage unit an email transmission filter not shown for attaching input data to an email message and sending the email message a fax transmission filter not shown for sending input data as a fax message a PC document transmission filter not shown for sending input data to a client PC not shown and a preview filter for displaying a preview of input data on the display unit .

The device service layer includes lower level functions shared by the filters in the application logic layer . The device service layer includes an image pipe and a data management unit for example.

The image pipe provides a function of a pipe that passes output data from a filter to the next filter. The data management unit represents various databases such as a database in which user information is registered and a database in which documents and image data are stored.

The device control layer includes a group of program modules called drivers for controlling hardware devices. For example the device control layer includes a scanner control unit a plotter control unit a memory control unit a memory control unit and an operations device control unit . These control units control devices indicated by their names.

An aspect includes a group of program modules that handle cross sectoral information related to the entire system such as access control information history information and charging information.

A detailed description of a filter is given below. is a diagram illustrating elements of a filter. As shown in a filter includes a filter setting UI filter logic a filter specific lower level service and permanent storage area information. The filter setting UI the filter specific lower level service and the permanent storage area information are optional.

The filter setting UI is a program for displaying a screen for specifying execution conditions of the filter on a display such as the display unit . For example the filter UI of the scan filter displays a screen for setting resolution density and image type. The filter setting UI may be HTML Hypertext Markup Language data or a script for displaying a screen on the display unit

Filter logic is a program with logic that provides a function of the filter. More specifically the filter logic provides a function of the filter using a filter specific lower level service of the filter as an element of the filter a lower level function in the device service layer and or a driver in the device control layer according to the execution conditions specified via the filter setting UI. For example filter logic of the scan filter controls scanning of a document by the scanner unit .

A filter specific lower level service is a library used by the filter logic. The filter specific lower level service is similar to a lower level function in the device service layer or a driver in the device control layer but may be implemented as a part of the filter since it is used only by the filter. For example a function of the scan filter for controlling the scanner unit may be implemented as a filter specific lower level service although the function is implemented as the scanner control unit in the device control unit in this embodiment. That is the scan filter does not have to include a filter specific lower level service.

The permanent storage area information includes a schema definition about data such as filter setting information e.g. default execution conditions that need to be stored in a non volatile memory e.g. a NVRAM Non Volatile RAM . The schema definition is registered in the data management unit upon installation of the filter.

An example of a combination of filters that provides a function of the image processing apparatus of this embodiment is described.

For example a copier function is provided by connecting the scan filter and the print filter . Thus image data scanned from a document by the scan filter are printed by the print filter . If a processing operation such as combining and scaling is requested the document processing filter that provides the processing operation is inserted between the scan filter and the print filter .

Next an exemplary basic procedure performed by the image processing apparatus of this embodiment having the above described software configuration is described with reference to .

Referring first to a user selects an input filter S and specifies execution conditions of the selected input filter S . Similarly the user selects a process filter and an output filter S specifies connection between the filters S and specifies execution conditions of the filters S .

These steps are performed under the control of the local UI unit of the user interface layer using the display unit that provides a touch panel function and the input unit .

When selection of filters is completed YES in step S and a start button is pressed the user interface layer transmits content of a request e.g. names of selected filters and information about operation settings for the filters to the control layer .

The control layer connects the selected filters with pipes according to the content of the request received from the user interface layer S . A pipe is implemented by a memory including the storage area of the secondary storage unit . Different types of memories are used as pipes depending on the types of filters at the opposing ends of the respective pipes. The correspondence between the types of memories and the types of filters is predefined in the secondary storage unit of the image processing apparatus . The control layer connects filters by appropriate pipes according to the predefined correspondence.

After Step S the control layer sends execution requests to the filters in parallel S . In other words the filters are not called in the order of connection but are called at substantially the same time. This is possible because the filters are synchronized by the pipes. More specifically when a filter receives an execution request from the control layer the filter stands by until data are input to a pipe input pipe connected to its input end. As an exception since no input pipe is connected to the input filter the input filter starts its operation as soon as it receives an execution request.

Referring now to the input filter inputs data from an input device S and outputs the input data to a pipe output pipe connected to its output end S . If data are input in multiple sessions e.g. when scanning a document of multiple pages data input to and data output from the pipe are repeated. After outputting all the pieces of the input data YES in step S the operation of the input filter ends.

The process filter starts its operation upon detection of data input to its input pipe. The process filter reads the data from the input pipe S and performs image processing on the input data S . Then the process filter outputs the processed data to its output pipe S . After outputting all the pieces of the input data YES in step S the operation of the process filter ends.

The output filter starts its operation upon detection of data input to its input pipe. The output filter reads the input data from the input pipe S and outputs the read data to an output device S . After outputting all the pieces of the input data YES in step S the operation of the output filter ends.

The following discusses how an application of this embodiment is provided based on the pipes and filter software configuration and the basic procedure.

In order to implement an application that runs on the pipes and filter software configuration and the basic procedure described above an input filter for inputting data a process filter for processing the input data and an output filter for outputting the processed data corresponding to a desired operation to be performed by the image processing apparatus are combined thereby creating a series of operation steps workflow including input processing and output steps. Then these filters input processing and output units are connected with pipes.

Thus the application can pass input data from the input filter to the subsequent process filter and pass the data processed by the process filter to the subsequent output filter . That is the application provides a function by operating the input processing and output components input processing and output software parts of the image processing apparatus in conjunction with each other.

In this manner the image processing apparatus of this embodiment can provide a function of the application by installing input processing and output components corresponding to the function of the application as needed.

As shown in the information processing device of this embodiment includes a control unit CPU a primary storage unit ROM RAM a secondary storage unit HD a network I F an external storage device I F an external device I F an output device I F and an input device I F . Elements of the information processing device shown in corresponding to those of the image processing apparatus of this embodiment shown in are denoted by the same reference numerals and are not described here. The elements of the information processing device different from those of the image processing apparatus are described below.

The output device I F interfaces the information processing device and an output device e.g. a CRT Cathode Ray Tube and an LCD connected via a data transmission line such as a dedicated cable.

The input device I F interfaces the information processing device and an input device e.g. a keyboard and a mouse connected via a data transmission line such as a USB.

Thus the information processing device of this embodiment causes the control unit to execute programs stored in the primary storage unit and the secondary storage unit sends control signals to appropriate units and thereby provides functions of the information processing device . The information processing device is connected to input and output devices that are different from those connected to the image processing apparatus . However similar to the image processing apparatus the information processing device causes the control unit to execute programs to control the appropriate units and thereby process information managed by the information processing device and information managed by a system connected to the information processing device .

That is the minimum hardware elements required for the information processing device to achieve an object the present invitation which is to provide a highly robust system that allows easy customization and extension of an application without a need to consider multi process architecture and that prevents basic functions of the system from being affected due to a failure of an extended function are the same as the minimum required hardware elements of the image processing apparatus is the same as the minimum hardware element required for the image processing apparatus . Accordingly the above described image processing apparatus may correspond to an apparatus including the printing unit the scanner unit and the information processing device . Therefore the information processing device is illustrated in the following description.

Multi process architecture in the pipes and filters software configuration described with reference to is discussed with reference to .

In the information processing device of this embodiment multi process architecture is configured according to the following principles in order to provide a highly robust system that allows easy customization and extension of an application without a need to consider multi process architecture and that prevents basic functions of the system from being affected due to a failure of an extended function.

 Principle 1 Execute self developed basic functions and an extended function developed by a third party vendor in different processes.

 Principle 2 Execute frequently used basic functions of a basic application in the same process the same JVM .

Referring to in order to achieve multi process architecture according to Principle 1 in the information processing device of this embodiment a process activated by an OS e.g. NetBSD is split into a process A first process for executing an application management JVM a process B second process for executing a self developed application basic application JVM and a process C third process for executing a third party vendor application extended application JVM.

A JVM is briefly described below. A JVM forms as a process on the OS address space on the main memory. The address space as used herein indicates a unit of memory management under process management. The OS activates processes by expanding loading programs stored in the secondary storage unit such as a hard disk onto the memory allocates dispatches physical memory to each process and manages usage. An area for expanding a Java application is reserved in the address space of the JVM expanded on the memory.

In the process A application management software system self developed infrastructure software that manages activation and termination of an application is executed. In the process B basic application software that provides basic functions of the information processing device is executed. In the process C extended application software that provides an extended function added to the information processing device is executed.

Thus the information processing device of this embodiment prevents the basic functions of the system from being affected due to a failure of an extended function an installed extended application e.g. prevents a system crash abnormal termination of the system and even if the extended function uses a large amount of memory stably provides functions to users without affecting the application management software.

As shown in the components of the layers are disposed in the three processes three JVMs which are split to have appropriate sizes as described with reference to so as to be executed in the processes.

The user interface layer includes components that serve as a framework of UIs for all the functions. Since these components have system wide characteristics the user interface layer is disposed in the process A for executing the application management software. Application specific UIs are disposed in the process B and the process C for executing the basic application self developed application and the extended application third party vendor application respectively.

The control layer includes components software components for request management and session management that control operations of applications and components software components for plug in management and apparatus monitoring that provide functions related to all the components. Since these components have system wide characteristics the control layer is disposed in the process A for the application management software.

The application logic layer includes components that provide the functions of the information processing device . In order to allow easy execution of operations of adding modifying and deleting functions the application logic layer is not disposed in the process A but is disposed in the process B for the basic application and the process C for the extended application.

The device service layer includes components that provide common services used by the components of the application logic layer . Since the components of the application logic layer are disposed in units of operations in the process B and the process C the services required by the components of the application logic layer are disposed in the process B and the process C that execute the corresponding components.

The device control layer includes components corresponding to devices handled by the system and greatly affects the performance of the information processing device . Therefore the device control layer is disposed in the process A for the application management software and the process B for the basic application that provides the functions of the information processing device .

The aspect includes components that handle cross sectoral information related to the entire system. Since these components have system wide characteristics the aspect is disposed in the process A for the application management software.

In this manner in the information processing device of this embodiment the components of the layers are disposed in appropriate processes in consideration of the characteristics of the layers. Further according to Principle 2 the components of each of the input filters the process filters and the output filters that are used for providing frequently used functions of the application such as a copier function of the information processing device are executed in the same process.

Thus the information processing device of this embodiment can stably provide the frequently used functions of the system to users.

The arrangement of the components of the layers in the multiple processes based on characteristics of the layers is described above with reference to . The following describes with reference to arrangement of components in smaller units i.e. in units of filters in the pipes and filters architecture and in units of activities that are provided by connecting filters in multiple processes.

In the activity based type component configuration as shown in one or more filter components required by an activity component are disposed in a process including the activity component such that an activity is executed within a single process single JVM .

On the other hand in the filter based type component configuration as shown in a single filter component is disposed in a single process such that an activity uses filters across plural processes plural JVMs .

Since the activity based type has the advantages in that malfunction of a component of the extended application does not affect execution of other activities and in that since a series of operations from selecting a function specifying operation settings to executing an activity is performed within a single process there is no need to perform inter process communications and therefore it is possible to reduce the number of components that implement inter process communications and to prevent performance degradation due to overhead of inter process communications the activity based type is employed to achieve suitable multi process architecture in the pipes and filters of the information processing device .

That is the information processing device of this embodiment employs according to Principle 3 the activity based type component configuration in which one or more filter components required by an activity component are disposed in a process including the activity component such that an activity is executed within a single process and thereby provides a highly robust system that allows easy customization and extension of an application without a need to consider multi process architecture and that prevents basic functions of the system from being affected due to a failure of an extended function.

Thus the information processing device of this embodiment is configured such that limited components corresponding to the framework perform inter process communications between processes JVMs in the multiple process environment thereby hiding the influence of multi process architecture on applications. This allows designing and developing an application without a need to consider the multiple process environment.

The following discusses with reference to how to execute the basic functions and the extended function of the information processing device of this embodiment having the process configuration and the layer arrangement that are described with reference to i.e. how to execute applications in the multiple process environment.

The information processing device of this embodiment includes an execution unit for executing three processes three JVMs shown in .

With reference to the execution unit executes the following three processes. The execution unit may be the OS for example.

The process A executes application management software that manages activation and termination of an application. The process A stays resident after activation of the information processing device .

The process B executes components that are preinstalled in the information processing device and that serve as an input filter a process filter and or an output filter i.e. components that provide standard functions of the information processing device .

The process C executes components that are added to the information processing device for function extension and that serve as an input filter a process filter and or an output filter

The process B and the process C are executed by the execution unit when necessary such as when an operations request is received from a user.

In this manner in the information processing device of this embodiment memory space is split into space for executing the system space for executing basic application software that provides basic functions and space for executing extended application software that provides an extended function thereby achieving multi process architecture in which processes do not affect each other.

In the three processes executed by the execution unit although the component configuration that minimizes inter process communications is employed according to Principle 3 inter process communications for operations requests operation settings and execution requests need to be performed between the application management software and the basic application software and between the application management software and the extended application software .

Therefore the information processing device of this embodiment includes proxy components that exchange data between the application management software executed in the process A and application software executed in the process B or the process C

In the example shown in the application management software calls applications AP. In the example shown in the applications AP call the application management software.

Normally when the application management software calls the application AP or AP a call event is sent from a system wide framework FW component to the application AP or AP using inter process communications. On the other hand when the application AP and AP call the application management software call events are sent from the application AP and AP to the system wide framework FW component using inter process communications. Therefore the applications AP need to be developed in consideration with inter process communications.

In this embodiment the proxy component is disposed in each of the process B for executing the extended application software and the process C for executing the application AP. The proxy components exchange data between the application management software between the application AP by performing inter process communications between the application management process A and the application process B and between the application management process A and the application process C thereby hiding inter process communications remote call function .

Thus the applications AP can exchange events with the application management software using local calls as in the case where the applications AP are executed in single processes.

In this way in the information processing device of this embodiment limited components corresponding to the framework FW perform inter process communications between processes in the multiple process environment thereby hiding the influence of the multi process architecture. This allows designing and developing the applications AP without a need to consider the inter process communications with the application management software i.e. without a need to consider the multiple process environment .

Components that need to perform inter process communications between the process A for the application management software and the process B for the basic application software or the process C for the extended application software and that have system wide characteristics include the local UI unit of the user interface layer the control unit of the control layer the data management unit of the device service layer the scanner control unit the plotter control unit and the memory control unit of the device control layer .

Therefore proxy components which are shown by dotted lines in of these components are disposed in the process B and the process C.

The following describes how the information processing device of this embodiment makes a request for an operation of the application AP a request for operation settings of the application AP and a request for execution of the application AP upon execution of the application AP in the multiple process environment.

According to the information processing device of this embodiment operations performed by a user using the UI screen to execute the application AP include selecting the application AP to be executed i.e. making an operations request specifying operation settings of input processing input filters of the selected application AP and instructing execution of the application AP i.e. making an execution request in this order.

Therefore in the multiple process environment the application management software needs to transmit an event based on a user instruction to a component that performs the subsequent operation in each operation step. That is the application management software needs to determine the process that executes the component which performs the subsequent operation.

Therefore the information processing device of this embodiment includes an operations request transmission unit an operation setting request transmission unit and an execution request management unit .

The operations request transmission unit is configured to transmit when an instruction for selecting an application AP to be executed is received the received operations request to the process for executing the application AP.

The operation setting request transmission unit is configured to transmit when a request for specifying the operation settings of an application AP is received the received operation setting request to the process for executing the application AP.

The execution request management unit arranges the registered execution request in a schedule and instructs the process for the application AP when it is ready to execute the application AP.

The operations request transmission unit the operation setting request transmission unit and the execution request management unit are described below in greater detail.

First the operations request transmission unit is described. The operations request transmission unit is a function of the local UI unit of the application management software. Upon receiving an instruction for selecting an application AP to be executed through a UI the operations request transmission unit determines a process for executing the application AP based on information for determining the process for executing the selected application AP and transmits the received operations request to the determined process.

Information for determining processes for executing applications AP is generated according to a method shown in and is stored in the memory by the application management software.

Referring to when an application AP is installed an application identification information piece e.g. activity name for identifying the application AP and a process identification information piece e.g. process ID for identifying a process for executing the application AP are sent to the application management software through a proxy component of the local UI unit .

For example when a copy application is installed a copy activity UI of the copy application sends information pieces indicating activity name Copy and process ID Process B to the application management software as registration information pieces through a proxy component . When a third party vendor application is installed a vendor activity UI of the third party vendor application sends information pieces indicating activity name Vendor and process ID Process C to the application management software as registration information pieces through a proxy component .

Thus the application management software collects an application identification information piece for identifying an application AP and a process identification information piece for identifying a process for executing the application AP from each process through inter process communications with the proxy component associates the collected application identification information piece and the process identification information piece with each other in the data structure as shown in for example and temporarily stores as the correspondence relationship data in the memory.

The operations request transmission unit sends the received operations request to the process determined from the application identification information piece of the selected application AP based on the correspondence relationship data in which application identification information pieces are associated with the process identification information pieces.

Referring back to the operation setting request transmission unit is described. The operation setting request transmission unit is a function of the local UI unit of the application management software. When the operation setting request transmission unit receives an operation setting request of an application AP instruction for specifying the operations settings of an application AP from a user through a UI the operation setting request transmission unit determines a process for executing the application AP based on information for determining the processes for executing the application AP and transmits the received operation setting request to the determined process.

After selecting the application AP to be executed i.e. making an operations request the user specifies operation settings of input processing input filters of the selected application AP. Therefore the application management software needs to transmit an instruction for generating and displaying a UI screen for receiving operation settings of the application AP from the user to activity UIs and filter UIs which are components that generate UI elements i.e. objects . The operations device control unit of the application receives operation events through the displayed UI screen and transmits the received events to appropriate processes. That is the application management software needs to determine the processes in which the activity UIs and the filter UIs are executed.

Information for determining processes for executing the application management software activity UIs and filter UIs is stored by the application management software as correspondence relationship data shown in for example.

As shown in the application management software stores UI control component identification information pieces for identifying components hereinafter referred to as UI control components that control activity UIs and filter UIs and generate UI elements screen element identification information pieces for identifying UI elements of applications AP that are generated by the UI control components and are displayed on the display screen and process identification information pieces for identifying processes that execute the activities and filters as destinations of requests. The application management software stores these information pieces in combination with each other in the memory.

The screen element information pieces are numbers automatically assigned to the UI elements generated by the UI components the activity UIs or the filter UIs of the selected application AP. The local UI unit including the proxy components adds the screen element identification information pieces to the correspondence relationship data in combination with the process identification information pieces.

For example referring to in the case where a copy application is installed a screen element ID is assigned to a UI element generated by the UI control component the copy activity UI of the copy application. Then the local UI unit and the proxy component in the process B b associate the screen element ID with the process B that executes the copy activity UI . Information pieces related to a scan filter UI and a print filter UI that provide a copy application function are added to the correspondence relationship data in the same manner as described above. In the case where a third party vendor application is installed a screen element ID is assigned to a UI element generated by the UI control component the vendor activity UI of the third party vendor application. Then the local UI unit and the proxy component in the process C associate the screen element ID with the process C that executes the vendor activity UI . Information pieces related to a vendor filter UI and a print filter UI that provide a vendor application function are added to the correspondence relationship data in the same manner as described above.

In this way the application management software causes the local UI unit including the proxy components to associate the generated screen element identification information pieces and the process identification information pieces in combination with each other and temporarily stores them as the correspondence relationship data in the memory.

Thus in the case where a display device with a touch panel function is connected to the output device I F of the information processing device of this embodiment when a user touches a screen displayed on the display device to specify operation settings of the application AP the application management software determines a screen element a screen display region touched on the screen and determines the screen element identification number of the determined screen element.

The process that executes corresponding activities UI and filter UIs are determined from screen element identification information pieces based on the correspondence relationship data in which the screen element identification information pieces are associated with process identification information pieces. Then the operation setting request transmission unit delivers an operation settings request which is received by the operations device control unit to the determined process.

Referring back to the execution request management unit is described. The execution request management unit provides two major functions. The first is an execution request registration function provided using the local UI unit including the proxy components of the application management software. The second is an execution start instructing function provided using the control unit .

The execution request management unit provides the execution request registration function for registering an execution request which is received by the local UI unit into the control unit . More specifically when the an execution request of the application AP is received execution request management unit determines a process for executing the application AP based on information for determining the processes for the application AP and transmits the received execution request to the determined process.

After specifying the operation settings of input processing and output filters of the selected application AP the user instructs execution i.e. makes an execution request of the application AP.

When the user instructs execution i.e. makes an execution request of the application AP the operations device control unit receives an operation event including the corresponding screen element ID. If the execution request is made by pressing a hardware key a tart key of the image processing apparatus an Enter key of the information processing device etc. the operation event includes the screen element ID of the screen element displayed on the front side of the currently displayed screen.

The execution request management unit uses the execution request registration function to refer to the correspondence relationship data of and determines the component as the destination of the execution request and determines the process that executes the component. Then the execution request management unit transmits the operation event to a proxy component using inter process communications the proxy component reports the screen element to the to the UI control component activity UI corresponding to the application AP to be executed . The UI control component registers the execution request including information about operation settings that are currently applied on the reported screen element.

The execution request management unit provides an execution start instructing function for arranging the received execution request in a schedule and instructing execution of the application AP when it is ready to execute the request. More specifically when an execution request of the application AP is received the execution request management unit queues the received request using a predetermined method. Then the execution request management unit transmits the request to the application AP when it is ready to execute the request based on queuing information.

Since plural processes generate requests the requests generated by the processes need to be centrally managed queued . Therefore the requests registered in the control unit by the UI control components are transmitted to the application management process A via the proxy components and are centrally managed by the control unit in the application management process A . Since an executable request needs to be transmitted to the application AP data as shown in need to be stored in the memory as information for determining the process for executing the application AP that generated the request.

Referring to the application management software holds execution request identification information pieces for identifying received execution requests of the applications AP to be registered into the control unit and process identification information pieces for identifying processes for executing the applications AP as destinations of the requests.

The execution request identification pieces are automatically generated for example in the order of reception upon reception of the execution requests of the applications AP. The control unit adds the generated execution request information pieces and the process identification information pieces in combination with each other to the correspondence relationship data .

For example referring to when an execution request of the copy application is received the control unit and the proxy component in the process B associate a request ID which is generated upon reception of the execution request for identifying the execution request with the process B for executing the copy application and add these information pieces to the correspondence relationship data . When an execution request of the third party vendor application is received the control unit and the proxy component in the process B associate a request ID which is generated upon reception of the execution request for identifying the execution request with the process B for executing the third party vendor application and add these information pieces to the correspondence relationship data .

In this way the application management software causes the control unit including the proxy components to associate the generated execution request identification information pieces and the process identification information pieces in combination with each other and temporarily stores them as the correspondence relationship data in the memory.

The execution request management unit uses the execution start instructing function to transmit an instruction for starting execution of a request to the proxy component in the process for the application AP wherein the process is determined from the execution request identification information piece of the executable request based on the correspondence relationship data in which execution request identification information pieces are associated with process identification information pieces and reports it to the application AP in the process that executes the proxy component .

In this way the execution request management unit instructs starting execution of the application AP according to the execution request received from the user using the above described two functions.

The information processing device of this embodiment executes the above described units in the multiple process environment using the following steps to execute an application.

The information processing device receives an operations request from a user via the local UI unit of the application management software.

Upon receiving the operations request instruction for selecting the application AP to be operated the information processing device causes the operations request transmission unit of the local UI unit to transmit the received operations request to the process determined from the application identification information piece based on the correspondence relationship data in which application identification information pieces are associated with process identification information pieces stored in the memory.

The information processing device receives a request for specifying operation settings of an application AP from a user via the local UI unit of the application management software.

Upon receiving the request for specifying operation settings of the application AP to be performed the information processing device causes the operation setting request transmission unit of the local UI unit to transmit the received operation setting request to the process determined from the screen element identification information piece based on the correspondence relationship data in which the screen element identification information pieces are associated with the process identification information pieces stored in the memory.

The information processing device receives a request for execution of the application AP from a user via the local UI unit of the application management software.

Upon receiving the request for execution of the application AP the information processing device uses the execution request transmission function which is provided by the execution request management unit using the local UI unit to send the received execution request to the process determined from the execution request information piece based on the correspondence relationship data in which screen element identification information pieces are associated with process identification information pieces stored in the memory. Then the information processing device uses the execution start instructing function which is provided by the execution request management unit using the control unit to send the executable execution request to the process determined from the execution request information piece based on the correspondence relationship data in which execution request identification information pieces are associated with process identification information pieces stored in the memory.

In this way the information processing device of this embodiment can stably perform operations such as selecting an application AP specifying operation settings and executing a function in the multiple process environment using Steps 1 through 3 described above. That is the information processing device of this embodiment can stably provide functions to users.

A specific procedure for application execution in the information processing device of this embodiment is described below with reference to by taking a procedure to provide a copier function as an example.

The information processing device of this embodiment expands for example application management software and a basic application program self developed application program stored in the secondary storage unit such as a hard disk of the information processing device and an installed extended application program third party vendor application program into the memory and causes the control unit to execute the programs. The procedures shown in are performed in the corresponding user operation stages. The user operation stages as used here indicate operations performed by a user using the UI screen to execute the application AP including operations for selecting the application AP to be executed i.e. making an operations request specifying operation settings of input processing input filters of the selected application AP and instructing execution of the application AP i.e. making an execution request .

According to the information processing device of this embodiment in the process A for the application management software executed by the execution unit upon receiving an operations request from a user based on an instruction for selecting an application AP copier function the operations device control unit transmits the received UI event operations request to the local UI unit S .

The local UI unit causes the operations request transmission unit to determine the process B that is executed by the execution unit and executes the copier function based on the correspondence relationship data in which application identification information pieces are associated with process identification information pieces stored in the memory and to send the UI event operations request to the determined process B using inter process communications S .

In the process B the UI event operations request received via a proxy component of the local UI unit i.e. a local UI unit in the process B shown by dotted lines in is sent to the copy activity UI of the copier function to be executed S .

Upon receiving the UI event operations request the copy activity UI generates its UI element and sends the received UI event to the scan filter UI and the print filter UI that provide the copy application S .

Upon receiving the UI event operations request the scan filter UI and the print filter UI generate their UI elements. The generated UI elements are sent to the proxy component of the local UI unit . The local UI unit assigns screen element identification information pieces to the UI elements and stores the screen element identification information pieces in combination with process identification information pieces in the correspondence relationship data stored in the memory. The registered UI elements are sent to and displayed by the operations device control unit .

In this way the information processing device of this embodiment can display a UI screen for specifying operation settings of the application AP to be executed in response to the operations request from the user.

According to the information processing device of this embodiment in the process A for the application management software executed by the execution unit upon receiving an operation setting request from a user based on an instruction for specifying operation settings of an application AP the operations device control unit transmits the received UI event operation setting request to the local UI unit S .

The local UI unit causes the operation setting request transmission unit to determine the process B that is executed by the execution unit and executes the copier function based on the correspondence relationship data in which screen element identification information pieces are associated with process identification information pieces stored in the memory and to send the UI event operation setting request to the determined process B using inter process communications S .

In the process B based on screen element identification information pieces contained in the UI event operation setting request received via the proxy component of the local UI unit i.e. the local UI unit of the process B shown by dotted lines in components that have generated the UI elements namely the copy activity UI and the scan filter and print filter UIs and that provide the copy application are determined. Then the operation settings are sent to the copy activity UI the scan filter UI and the print filter UI S .

The copy activity UI the scan filter UI and the print filter UI apply the corresponding operation settings to a copy activity logic a scan filter logic and a print filter logic respectively S .

In this way the information processing device of this embodiment can apply the operation settings specified by the user to the components that provide the functions of the application AP to be executed.

According to the information processing device of this embodiment in the process A for the application management software executed by the execution unit upon receiving an execution request from a user based on an instruction for executing the application AP the operations device control unit transmits the received UI event execution request to the local UI unit S .

The local UI unit causes the execution request management unit to determine the process B that is executed by the execution unit and executes the copier function based on the correspondence relationship data in which screen element identification information pieces are associated with process identification information pieces stored in the memory and to send the UI event to the determined process B using inter process communications S .

In the process B the UI event execution request received via the proxy component of the local UI unit i.e. the local UI unit of the process B shown by dotted lines in is sent to a UI control component to be executed namely the copy activity UI of the copier function S .

The copy activity UI registers the received UI event execution request into a proxy component of the control unit i.e. a control unit of the process B shown by dotted lines in S .

The proxy component of the control unit in the process B connects the scan filter logic and the print filter logic that provide the copy application function with the image pipe S . The proxy component of the control unit generates an execution request identification information piece for the received UI event execution request . After Step S the proxy component of the control unit sends the UI event execution request to the process A using inter process communications S .

In the process A the control unit queues the UI event execution request . The control unit arranges the registered execution request in a schedule and sends an instruction for starting execution to the proxy component in the process for the application AP wherein the process is determined from an execution request identification information piece of the executable execution request S . This embodiment is described by taking the copier function as an example. Therefore if an execution request of a copier function is executable the execution request is sent to the determined process B to instruct the copy application to start execution.

In the process B the proxy component of the control unit transmits the received execution request to the copy activity logic S . The copy activity logic transmits the execution request to the scan filter logic and the print filter logic that provide the copy application function S .

Upon receiving the execution request the scan filter logic instructs the image pipe which is connected to the filters in Step S to reserve memory space for storing an image to be scanned S . The image pipe causes the memory control unit to reserve predetermined memory space according to the instruction for reserving memory space S .

Then according to the received execution request the scan filter logic instructs the scanner control unit to scan an image S . The scanner control unit scans an image according to the scan instruction S and writes the scanned image data into the reserved predetermined memory space S . The scan filter logic instructs the image pipe to transmit storage location information address information of the written image data S .

On the other hand upon receiving the execution request the print filter logic requests the image pipe for the storage location information of the written image data and acquires the storage location information from the image pipe if the image data are written into the memory in Step S S .

Then the print filter logic instructs the plotter control unit to print plot the image data based on the acquired storage location information S . The plotter control unit reads the image data via the memory control unit based on the storage location information S and prints the read image data onto paper S .

Then the print filter logic instructs based on the storage location information the image pipe to release the memory space that is reserved in Step S S .

In this way the information processing device of this embodiment can execute the application AP according to an execution request from a user.

A specific procedure for application execution in the information processing device of this embodiment is described below with reference to by taking a procedure to provide a vendor extended function of the extended application software as an example. The extended application software third party vendor application software described below with reference to provides an extended function by connecting an input filter developed by a third party vendor and an output filter pre installed in the information processing device with an image pipe .

According to the information processing device of this embodiment in the process A for the application management software executed by the execution unit upon receiving an operations request from a user based on an instruction for selecting an application AP vendor function the operations device control unit transmits the received UI event operations request to the local UI unit S .

The local UI unit causes the operations request transmission unit to determine the process C that is executed by the execution unit and executes the vendor function based on the correspondence relationship data in which application identification information pieces are associated with process identification information pieces stored in the memory and to send the UI event operations request to the determined process C using inter process communications S .

In the process third process C the UI event operations request received via a proxy component of the local UI unit i.e. a local UI unit of the process C c shown by dotted lines in is sent to the vendor activity UI of the vendor function to be executed S .

The vendor activity UI generates its UI element and sends the received UI event to a vendor input filter UI hereinafter referred to as a vendor filter UI and the print filter UI that provide the third party vendor application S .

Upon receiving the UI event operations request the vendor filter UI and the print filter UI generate their UI elements. The generated UI elements are sent to the proxy component of the local UI unit . The proxy component assigns screen element identification information pieces to the UI elements and stores the screen element identification information pieces in combination with process identification information pieces in the correspondence relationship data stored in the memory. The registered UI elements are sent to and displayed by the operations device control unit .

According to the information processing device of this embodiment in the process A for the application management software executed by the execution unit upon receiving an operation setting request from a user based on an instruction for specifying operation condition settings of an application AP the operations device control unit transmits the received UI event operation setting request to the local UI unit S .

The local UI unit causes the operation setting request transmission unit to determine the process C that is executed by the execution unit and executes the vendor function based on the correspondence relationship data in which screen element identification information pieces are associated with process identification information pieces stored in the memory and to send the UI event operation setting request to the determined process C using inter process communications S .

In the process third process C based on screen element identification information pieces contained in the UI event operation setting request received via the proxy component of the local UI unit i.e. the local UI unit in the process C shown by dotted lines in components that have generated the UI elements namely the vendor activity UI the vendor and print filter UIs and that provide the third party vendor application are determined. Then the operation settings are sent to the vendor activity UI the vendor filter UI and the print filter UI S .

The vendor activity UI the vendor filter UI and the print filter UI apply the corresponding operation settings to a vendor activity logic a vendor input filter logic hereinafter referred to as a vendor filter logic and a print filter logic respectively S .

According to the information processing device of this embodiment in the process A for the application management software executed by the execution unit upon receiving an execution request from a user based on an instruction for executing the application AP the operations device control unit transmits the received execution request to the local UI unit S .

The local UI unit causes the execution request management unit to determine the process C that is executed by the execution unit and executes the vendor function based on the correspondence relationship data in which screen element identification information pieces are associated with process identification information pieces stored in the memory and to send the UI event operation request to the determined process C using inter process communications S .

In the process C the UI event execution request received via the proxy component of the local UI unit i.e. the local UI unit in the process C shown by dotted lines in is sent to a UI control component to be executed namely the vendor activity UI of the vendor function S .

The vendor activity UI registers the received UI event execution request into a proxy component of the control unit i.e. a control unit in the process C shown by dotted lines in S .

The proxy component of the control unit in the process C connects the vendor filter logic and the print filter logic that provide the vendor application function with the image pipe S . The proxy component of the control unit generates an execution request identification information piece for the received UI event execution request . After Step S the proxy component of the control unit sends the UI event execution request to the process A using inter process communications S .

In the process A the control unit queues the UI event execution request . The control unit arranges the registered execution request in a schedule and sends an instruction for starting execution to the proxy component in the process for the application AP wherein the process is determined from an execution request identification information piece of the executable execution request S . This embodiment is described by taking the vendor function as an example. Therefore if an execution request of a vendor function is executable the execution request is sent to the determined process C to instruct the third party vendor application to start execution.

In the process C the proxy component of the control unit transmits the received execution request to the vendor activity logic S . The vendor activity logic transmits the execution request to the vendor filter logic and the print filter logic that provide the vendor application function S .

Upon receiving the execution request the vendor filter logic instructs the image pipe which is connected to the filters in Step S to reserve memory space for storing an image to be scanned S . The image pipe causes the memory control unit in the process B to reserve predetermined memory space via a proxy component of the memory control unit i.e. a memory control unit in the process C shown by dotted lines in according to the instruction for reserving memory space S and S .

Then according to the received execution request the vendor filter logic inputs image data via the network I F of the information processing device or from a memory card via the external storage device I F for example S . The vendor filter logic writes the input image data into the reserved predetermined memory space via the proxy component of the memory control unit S . The vendor filter logic instructs the image pipe to transmit storage location information of the written image data S .

On the other hand upon receiving the execution request the print filter logic requests the image pipe for the storage location information of the written image data and acquires the storage location information from the image pipe if the image data are written into the memory in Step S S .

The print filter logic instructs the plotter control unit in the process C to print the image data based on the acquired storage location information via a proxy component of the plotter control unit i.e. a plotter control unit in the process C shown by dotted lines in S and S The plotter control unit reads the image data via the memory control unit based on the storage location information S and prints the read image data onto paper S .

Then the print filter logic instructs based on the storage location information the image pipe to release the memory space that is reserved in Step S S .

The image pipe causes the memory control unit of the process B to release the reserved predetermined memory space via the proxy component of the memory control unit i.e. the memory control unit in the process C shown by dotted lines in according to the instruction for releasing memory space S and S .

The suitable distributed arrangement of components that are executed in processes is described above with reference to . The above description shows that the activity based type is more suitable than the filter based type.

In view of this the procedures for application execution based on the component arrangement of the activity based type are described above with reference to .

The following describes component arrangement of the filter based type and procedures for application execution based on the component arrangement of the filter based type with reference to .

The filter based type is different from the activity based type in that the processes are split on a per filter basis which is the characteristic of the filter based type.

Comparing the activity based component arrangement of with the filter based component arrangement of for example in the case of an extended function provided by the extended application software third party vendor application software by connecting an input filter developed by a third party vendor and an output filter pre installed in the information processing device with an image pipe the components related to a print filter as the output filter pre installed in the information processing device are disposed in each of the process B and the process C in the activity based type of while the components related to a print filter are not disposed in the process C but only components related to the input filter developed by the third party vendor are disposed in the process C in the filter based type of .

That is in the filter based type component arrangement filters shared by the basic application software and the extended application software are not disposed in the process for executing the extended application software . In other words different processes do not include the same filter components.

A procedure for application execution based on the filter based type component arrangement of is described below.

According to the information processing device of this embodiment in the process A for the application management software executed by the execution unit upon receiving an operations request from a user based on an instruction for selecting an application AP vendor function the operations device control unit transmits the received UI event operations request to the local UI unit S .

The local UI unit causes the operations request transmission unit to determine the process C that is executed by the execution unit and executes the vendor function based on the correspondence relationship data in which application identification information pieces are associated with process identification information pieces stored in the memory and to send the UI event operations request to the determined process C using inter process communications S .

In the process C the UI event operations request received via a proxy component of the local UI unit i.e. a local UI unit in the process C shown by dotted lines in is sent to the vendor activity UI of the vendor function to be executed S .

The vendor activity UI generates its UI element and sends the received UI event to a vendor filter UI that provides the third party vendor application S . Upon receiving the UI event operations request the vendor filter UI generates its UI element.

The vendor activity UI transmits the received UI event operations request from the proxy component of the local UI unit in the process C to a proxy component of the local UI unit in the process B i.e. a local unit in the process B shown by dotted lines in using inter process communications S and S .

In the process B upon receiving the UI event operations request via the proxy component of the local UI unit the print filter UI generates its UI element S .

The generated UI elements are sent to the proxy component of the local UI unit . The proxy component assigns screen element identification information pieces to the UI elements and stores the screen element identification information pieces in combination with process identification information pieces in the correspondence relationship data stored in the memory. The registered UI elements are sent to and displayed by the operations device control unit .

According to the information processing device of this embodiment in the process A for the application management software executed by the execution unit upon receiving an operation setting request from a user based on an instruction for specifying operation settings of an application AP the operations device control unit transmits the received UI event operation setting request to the local UI unit S .

The local UI unit causes the operation setting request transmission unit to determine the process C that is executed by the execution unit and executes the vendor function or the process B that is executed by the execution unit and executes the printer function based on the correspondence relationship data in which screen element identification information pieces are associated with process identification information pieces stored in the memory and to send the UI event operation setting request to the determined process C or process B . If the process B that executes the printer function is determined the UI event operation setting request is sent to the determined process B using inter process communications S .

In the process C based on screen element identification information pieces contained in the UI event operation setting request received via the proxy component of the local UI unit i.e. the local UI unit in the process C shown by dotted lines in components that have generated the UI elements namely the vendor activity UI and the vendor filter UI that provides the third party vendor application are determined. Then the operation settings as the UI event are sent to the vendor activity UI and the vendor filter UI S .

The vendor activity UI and the vendor filter UI apply the corresponding operation settings to the vendor activity logic and the vendor filter logic respectively S .

Meanwhile in the process B the UI event operations request received via the proxy component of the local UI unit i.e. the local UI unit in the process B shown by dotted lines in is sent to the print filter UI of the print function to be executed S .

According to the information processing device of this embodiment in the process A for the application management software executed by the execution unit upon receiving an execution request from a user based on an instruction for executing the application AP the operations device control unit transmits the received execution request to the local UI unit S .

The local UI unit causes the execution request management unit to determine the process C that is executed by the execution unit and executes the vendor function based on the correspondence relationship data in which screen element identification information pieces are associated with process identification information pieces stored in the memory and to send the UI event operation request to the determined process C using inter process communications S .

In the process C the UI event execution request received via the proxy component of the local UI unit i.e. the local UI unit in the process C shown by dotted lines in is sent to a UI control component to be executed namely the vendor activity UI of the vendor function S .

The vendor activity UI registers the received UI event execution request into a proxy component of the control unit i.e. a control unit in the process C shown by dotted lines in S .

The proxy component of the control unit in the process C connects the vendor filter logic and the print filter logic which provide the vendor application function in cooperation with each other using inter process communications via a proxy component in the process B i.e. a control unit in the process B shown by dotted lines in with the image pipe S through S The proxy component of the control unit generates an execution request identification information piece for the received execution request. After Steps S through S the proxy component of the control unit sends the execution request to the process A using inter process communications S .

In the process A the control unit queues the execution request. The control unit arranges the registered execution request in a schedule and sends an instruction for starting execution to the proxy component in the process for the application AP wherein the process is determined from an execution request identification information piece of the executable execution request S . This embodiment is described by taking the vendor function as an example. Therefore if an execution request of a vendor function is executable the execution request is sent to the determined process C to instruct the third party vendor application to start execution.

In the process C the proxy component of the control unit transmits the received execution request to the vendor activity logic S . The vendor activity logic transmits the execution request to the vendor filter logic that provides the vendor application function S .

The vendor activity logic transmits the received operations request from the proxy component of the control unit in the process C to the proxy component of the control unit in the process B i.e. the control unit in the process B shown by dotted lines in using inter process communications S and S .

In the process B the execution request is transmitted to the print filter logic via the proxy component of the control unit S .

Upon receiving the execution request the vendor filter logic instructs the image pipe which is connected to the filters in Steps S through S to reserve memory space for storing an image to be scanned via a proxy component of the image pipe in the process C i.e. an image pipe in the process C shown by dotted lines in S . The image pipe causes the memory control unit of the process B to reserve predetermined memory space via a proxy component of the memory control unit i.e. a memory control unit in the process C shown by dotted lines in according to the instruction for reserving memory space received via the proxy component of the image pipe S and S .

Then according to the received execution request the vendor filter logic inputs image data via the network I F of the information processing device or from a memory card via the external storage device I F for example S . The vendor filter logic writes the input image data into the reserved predetermined memory space via the proxy component of the memory control unit S . The vendor filter logic instructs the image pipe to transmit storage location information of the written image data via the proxy component of the image pipe S and S .

On the other hand according to the execution request transmitted in S the print filter logic requests the image pipe for the storage location information of the written image data and acquires the storage location information from the image pipe if the image data are written into the memory in Step S S .

Then the print filter logic instructs the plotter control unit to print the image data based on the acquired storage location information S . The plotter control unit reads the image data via the memory control unit based on the storage location information S and prints the read image data onto paper S .

Then the print filter logic instructs based on the storage location information the image pipe to release the memory space that is reserved in Steps S and S S .

As described above according to the first embodiment of the present invention the information processing device of this embodiment can execute the basic application software that provides basic functions of the system and the extended application software that provides an added extended function in different processes and can perform operations associated with the multi process architecture such as inter process communications using limited components corresponding to a framework FW i.e. hide the influence of the multi process architecture .

Therefore the information processing device of this embodiment can provide a highly robust system that allows easy customization and extension of an application AP without a need to consider the multi process architecture and that prevents basic functions of the system from being affected due to a failure of an extended function.

According to a second embodiment of the present invention there is provided an information processing device having a process configuration in which in multi process architecture in which a basic application that provides basic functions and an extended application that provides an added extended function are executed in different processes application management software that manages activation and termination of an application and basic application software that provides a basic function of the information processing device are executed in a first process and extended application software that provides an extended function added to the information processing device is executed in a second process. Thus the information processing device provides a highly robust system that allows easy customization and extension of an application without a need to consider the multi process architecture and that prevents basic functions of the system from being affected due to a failure of the extended function.

The second embodiment is different from the first embodiment in which three processes are provided such that the application management software is executed in the first process the basic application software is executed in the second process and the extended application software is executed in the third process in that two processes are provided such that the application management software and the basic application software is executed in the first process and the extended application software is executed in the second process.

Elements of the second embodiment corresponding to those of the first embodiment are denoted by the same reference numerals and are not further described here. The differences from the first embodiment are described below with reference to .

As in the case of the multi process architecture in the pipes and filters software configuration described with reference to in the information processing device of the second embodiment multi process architecture is configured according to Principles 1 through 3 of the first embodiment in order to provide a highly robust system that allows easy customization and extension of an application without a need to consider multi process architecture and that prevents basic functions of the system from being affected due to a failure of an extended function.

Referring to in order to achieve multi process architecture according to Principle of the first embodiment in the information processing device of this embodiment a process activated by an OS is split into a process A for executing a JVM for application management software and a self developed application and a process B for executing a third party vendor application.

In the process A the application management software that manages activation and termination of an application AP and the basic application software that provides basic functions of the information processing device are executed. That is in this embodiment a system as self developed infrastructure software and the basic application software that provides basic functions are executed in the same memory space. In the process B the extended application software that provides an extended function added to the information processing device is executed.

Thus the information processing device of this embodiment prevents the basic functions the basic application software of the system from being affected due to a failure of an extended function the installed extended application software e.g. prevents a system crash an abnormal termination of the system and even if the extended function the installed extended application software uses a large amount of memory stably provides functions to users without affecting the application management software.

As shown in the components of the layers are disposed in the two processes two JVMs which are split to have appropriate sizes as described with reference to so as to be executed in the processes.

In the second embodiment the components that are disposed in the process for the basic application software in the first embodiment are disposed in different places. The component arrangement of the layers including such components is described below.

The UIs of the basic application software in the user interface layer and the components of the basic application software in the application logic layer are disposed in the process A for the application management software and the basic application software .

In this manner in the information processing device of this embodiment the components of the layers are disposed in appropriate processes in consideration of the characteristics of the layers. Further according to Principle 2 of the first embodiment the components of each of the input filters the process filters and the output filters that are used for providing frequently used functions of the application AP such as a copier function of the information processing device are executed in the same process.

Thus the information processing device of this embodiment can stably provide the frequently used functions of the system to users. In the information processing device of the first embodiment since the application management software and the basic application software are executed in different processes data are exchanged among processes using inter process communications. On the other hand in the information processing device of the second embodiment since the application management software and the basic application software are executed in the same process there is no influence of inter process communications on the system and the architecture.

The following discusses with reference to how to execute the basic functions and the extended function of the information processing device of this embodiment having the process configuration and the layer arrangement that are described with reference to i.e. how to execute applications AP in the multiple process environment.

The functional configuration of the second embodiment is different from that of the first embodiment in that an execution unit for executing two processes is provided and in that proxy components for exchanging data between the application management software and the basic application software are not provided. The following describes these points.

The information processing device of this embodiment includes an execution unit for executing two processes shown in .

With reference to the execution unit executes the following two processes. The execution unit may be the OS for example.

The process A executes application management software that manages activation and termination of an application and components that are preinstalled in the information processing device and that serve as an input filter a process filter and or an output filter i.e. components that provide standard functions of the information processing device . The process A stays resident after activation of the information processing device .

The process B executes components that are added to the information processing device for function extension and that serve as an input filter input unit a process filter and or an output filter

The process B is executed by the execution unit when necessary such as when an operations request is received from a user.

In this manner in the information processing device of this embodiment memory space is split into space for executing the system self developed infrastructure software and basic application software that provides basic functions and space for executing extended application software that provides an extended function thereby achieving multi process architecture in which processes do not affect each other.

In the two processes executed by the execution unit although the component configuration that minimizes inter process communications is employed according to Principle 3 of the first embodiment inter process communications for operations requests operation settings and execution requests need to be performed between the application management software and the extended application software .

In this embodiment the information processing device includes proxy components for exchanging data between the application management software and the extended application software by performing inter process communications between the application management process A for executing the application management software and the application process B for executing the extended application software .

Since the basic application software is executed in the same process A as the application management software there is no need to perform inter process communications for operations requests operation settings and execution requests between the application software and the basic application software . Therefore proxy components for inter process communications between the application software and the basic application software are not provided.

The functional configuration of the second embodiment is the same as the functional configuration of the first embodiment except these points. Therefore technical features of the components of the operations request transmission unit the operation setting request transmission unit and the execution request management unit and procedures of execution of the application AP by the components are not further described here.

Component arrangements of the activity base type and the filter based type in the process configuration of the information processing device of this embodiment are described with reference to respectively.

The component arrangement of the second embodiment is different from that of the first embodiment as mentioned in the description of the functional configuration. More specifically in the first embodiment as shown in since the application management software and the basic application software are executed in different processes the proxy components of the local UI unit the control unit and the data management unit are provided. On the other hand in the second embodiment since the application management software and the basic application software are executed in the same process A these proxy components are not provided.

The functional configuration of the second embodiment is the same as that of the first embodiment except this point and therefore a description of the component arrangement of the second embodiment is omitted.

The component arrangement of the second embodiment is different from that of the first embodiment as mentioned in the description of the activity based type. More specifically in the first embodiment as shown in since the application management software and the basic application software are executed in different processes the proxy components of the local UI unit the control unit and the data management unit are provided. On the other hand in the second embodiment since the application management software and the basic application software are executed in the same process A these proxy components are not provided.

The functional configuration of the second embodiment is the same as that of the first embodiment except this point and therefore a description of the component arrangement of the second embodiment is omitted.

In the first embodiment the basic procedure for application execution in the case of the activity based type component arrangement is described with reference to and the basic procedure for application execution in the case on the filter based type component arrangement is described with reference to .

The basic procedure for application execution of the second embodiment is different from that of the first embodiment in that events and data are exchanged between application management software and the basic application software without using the proxy components . In this embodiment the local UI unit and the control unit of the application management software and the activity UI activity logic the filter UI and the filter logic of the basic application software directly exchange data.

The basic procedure for application execution of the second embodiment is the same as that of the first embodiment except this point and therefore is not further described here.

As described above according to the second embodiment of the present invention the information processing device of this embodiment can execute the basic application software that provides basic functions of the system and the extended application software that provides an added extended function in different processes and can perform operations associated with the multi process architecture such as inter process communications using limited components corresponding to a framework FW i.e. hide the influence of the multi process architecture .

Accordingly the information processing device of this embodiment can achieve the same effect as the information processing device of the first embodiment.

According to a third embodiment of the present invention there is provided an information processing device having a process configuration in which in multi process architecture in which a basic application that provides basic functions and an extended application that provides an added extended function are executed in different processes if the process for executing the extended function is abnormally terminated the abnormally terminated process is isolated from the system in order to allow the basic functions to remain operable. Thus the information processing device provides a highly robust system that allows easy customization and extension of an application without a need to consider the multi process architecture and that prevents basic functions of the system from being affected due to a failure of the extended function.

The third embodiment is different from the first and second embodiments in that an abnormal termination of a process for executing an extended function is detected and the abnormal termination is reported to components of the application management software i.e. a process abnormal termination detection reporting function is provided .

Elements of the third embodiment corresponding to those of the first and second embodiments are denoted by the same reference numerals and are not further described here. The differences from the first and second embodiments are described below with reference to .

The following discusses how the information processing device of this embodiment detects an abnormal termination and sends information indicating the abnormal termination to the application management software with reference to . In the following description the configuration of the first embodiment in which application management functions basic functions and an extended function are executed in different processes is used as an example of a multi process environment in which the process abnormal termination detection reporting function is executed.

The functional configuration of the third embodiment is different from those of the first and second embodiments in that a detection unit for detecting an abnormal termination of processes excluding a process for executing the application management software and reporting units for reporting the detection result to the components of the application management software are provided.

All the processes in the multi process architecture are created by duplicating a certain process. For example in a UNIX environment as in this embodiment a system call called fork is used to create a new process. A process created using fork is a child process of a parent process that called fork. The child process inherits the conditions of the parent process such as file handle variables and environmental variables of the parent process.

In the example shown in a process A a process B and a process C for executing application management functions basic functions and an extended function respectively are created as child processes of a parent process.

In general if a child process that is created using fork is terminated abnormally the child process sends a signal SIGCHLD indicating the abnormal termination to its parent process. Thus the parent process can determine whether its child process is alive i.e. whether its child process is operating properly 

In this embodiment the parent process includes the detection unit for detecting abnormal terminations of the child processes and the reporting unit for sending information indicating the abnormal termination to the process A i.e. the child process for the application management software thereby providing a process abnormal termination detection reporting function.

Further in this embodiment the process A as a child process includes a reporting unit for sending in response to information indicating detection of an abnormal termination from the parent process information indicating detection of an abnormal termination to all the components of the application management software. In order to prevent an application AP that is not operating properly from affecting other applications AP that are operating properly management information pieces related to the application AP that is executed in the abnormally terminated process are made mutually consistent i.e. data related to the application AP that is executed in the abnormally terminated process are deleted by the components. Since unnecessary information are deleted the information processing device of this embodiment can efficiently use memory resources and can prevent malfunction of an application that is not operable due to an abnormal termination.

A specific procedure for detection reporting of a process abnormal termination in the information processing device of this embodiment is described below with reference to by taking as an example the case where the process C for executing the extended application software is abnormally terminated.

In the information processing device of this embodiment the detection unit of the parent process receives a signal SIGHLD and thus detects an abnormal termination of the process C which is a child process S and sends the detection result to the reporting unit executed in the parent process S .

Based on the received detection result the reporting unit sends information indicating detection of the abnormal termination to the process A i.e. the child process for the application management software using inter process communications such as sockets and message queues S .

Having received the information the application management software causes the reporting unit to send information indicating detection of the abnormal termination to all the components the number of components n of the application management software S through S .

For example having received the information indicating detection of the abnormal termination from the reporting unit the local UI unit of the application management software refers to the correspondence relationship data in which activities are associated with processes that execute the activities and deletes relevant data based on the process identification information piece e.g. process ID of the abnormally terminated process C S .

Then the local UI unit refers to the correspondence relationship data in which UIs are associated with processes that generate the UIs and deletes relevant data S .

Further having received the information indicating detection of the abnormal termination from the reporting unit the control unit of the application management software refers to the correspondence relationship data in which requests are associated with processes that generate the requests and deletes relevant data based on the process identification information piece e.g. process ID of the abnormally terminated process C S .

Deletion of relevant data performed in Steps S through S is described with reference to . In the following deletion of relevant data is described by taking as an example the case where the process C for executing the extended application software is abnormally terminated.

In Step S the local UI unit refers to the correspondence relationship data shown in in which activities are associated with processes that execute the activities and deletes relevant data in the information item activity name enclosed by dotted lines based on the process ID process C of the abnormally terminated process C

Then in Step S the local UI unit refers to the correspondence relationship data shown in in which UIs are associated with processes that generate the UIs and deletes relevant data in the information items UI control component ID and screen element ID enclosed by dotted lines based on the process ID process C .

In these steps the local UI unit not only deletes relevant data from the correspondence relationship data and the correspondence relationship data but also deletes graphic parts e.g. icons constituting a menu as a selection screen of the application AP or changes the display attribute of the graphic parts to half brightness grayed out .

Then in Step S the control unit refers to the correspondence relationship data shown in in which requests are associated with processes that generate the requests and deletes relevant data in the information item request ID enclosed by dotted lines based on the process ID process C of the abnormally terminated process C

In this step the control unit reports the deleted request using various reporting methods such as displaying on the screen printing out a status report sending e mail to an administrator and sending e mail to a user who requested a job. The control unit may store information about the deleted request in the secondary storage unit such as a hard disk as permanent information to allow re execution of the request based on the permanent information upon the next successful activation.

In this manner the information processing device of this embodiment can isolate if the process for executing the extended function is abnormally terminated the abnormally terminated process from the system in order to allow the basic functions to remain operable. Thus the information processing device can continue to provide a function provision service to a user on a smaller scale. For example the information processing device can continue to provide only basic functions.

The process abnormal termination detection reporting function described above has a configuration in which the detection unit and the reporting unit for providing the detection reporting function are executed in the parent process. This configuration is advantageous in that an abnormal termination can immediately be detected through inter process communications using signals. This configuration is however disadvantageous in that function implementation in the multi process environment is complex.

An example that enables function implementation with a configuration simpler than the above described functional configuration is described below with reference to .

In the modified example of the process A for executing the application management software includes a detection unit and a reporting unit and each of the process B and the process C for executing applications AP which are managed by the application management software has a transmission unit for sending a process status information piece.

The first is a method that causes the detection unit of the process A to regularly request the other processes for process status information pieces and causes the transmission units of the other processes to respond to the request thereby determining whether the other processes are alive. The second is a method that causes the transmission units of the other processes to regularly send process status information pieces heartbeat to the process A and causes the detection unit of the process A to receive the process status information pieces thereby determining whether the other processes are alive.

In this modified example the process abnormal termination detection reporting function is provided using inter process communications between the child processes in this manner.

A specific procedure for detection reporting of a process abnormal termination in the information processing device of the modified example is described below with reference to by taking as an example the case where the process C for executing the extended application software is abnormally terminated.

In the information processing device of this modified example the detection unit of the process A regularly determines whether the other processes are alive. More specifically the detection unit requests the process B for a status information piece of the process B . In response to the request the transmission unit of the process B sends a status information piece of the process B S . The detection unit then requests the process C for a status information piece of the process C . In response to the request the transmission unit of the process C sends a status information piece of the process C S .

Based on the response results from the process B and the process C the detection unit detects a process abnormal termination S . For example in the case where the process C is abnormally terminated the transmission unit of the process C cannot respond to the request for a status information piece. Then the detection unit determines that the process C from which no response is sent is abnormally terminated and thus detects an abnormal termination of the process C . A process abnormal termination may be determined based on an error in inter process communications between the child processes.

In the subsequent procedure in Steps S through S which is similar to the procedure in Steps S through S of the reporting unit receives the detection results from the detection unit and sends the information indicating detection of the abnormal termination to all the components of the application management software.

In the information processing device of this modified example the transmission unit and the transmission unit of the process B and the process C regularly send status information pieces heartbeat of the process B and the process C to the process A respectively. More specifically the transmission unit and the transmission unit regularly acquire status information pieces of the process B and the process C respectively Sand S and send the status information pieces to the process A Sand S . Then the detection unit of the process A receives the status information pieces.

Based on the reception results from the process B and the process C the detection unit detects a process abnormal termination S . For example in the case where the process C is abnormally terminated the process C cannot regularly send a status information piece. Then the detection unit determines that the process C from which no status information piece is sent within a certain time period is abnormally terminated and thus detects an abnormal termination of the process C

In the subsequent procedure in Steps S through S which is similar to the procedure in Steps S through S of the reporting unit receives the detection results from the detection unit and sends the information indicating detection of the abnormal termination to all the components of the application management software.

In the third embodiment including the above described modified example when the local UI unit receives information indicating detection of an abnormal termination from the reporting unit a screen W shown in or B is displayed on a display device connected to the information processing device via the output device I F for example.

The display screen W of or is displayed by the application management UI. Similar to the local UI unit the application management UI is disposed in the user interface layer of the process A Upon receiving information indicating detection of an abnormal termination the local UI unit requests the application management UI to generate a screen. In response to the request the application management UI generates UI elements and returns the generated UI elements to the local UI unit . Then a screen is displayed in the same manner as the UIs of the application AP in the first embodiment.

The display screen W of includes a list of applications AP installed in the information processing device .

The list of applications AP includes various information items such application status enabled disabled application name version date of update and process for executing the application AP.

This list display area includes various types of action buttons such as buttons for specifying whether to enable disable the applications AP buttons for updating re installing the applications AP and buttons for deleting uninstalling the applications AP. Users can perform operations of specifying whether to enable the applications AP updating the applications AP and deleing the applications AP by selecting these buttons.

For example if a user selects the Enable button of the application AP with the name Print the status of Print is changed from a disabled state to an enabled state.

The display screen W also includes an operations area for specifying whether to enable processes for executing the applications AP to allow users to specify whether to enable disable the processes.

For example if a user selects the Enable button of the process with the name Process B the status of Process B is changed from a disabled state to an enabled state.

The application AP corresponding to the request that is executed immediately before a process abnormal termination can be determined from the information item Status in the list of the applications AP.

In since the process C is abnormally terminated plural applications AP corresponding to the abnormally terminated process C have in Status . In indicates the application AP that has been executed in the abnormally terminated process and indicates the application AP that is executed immediately before the abnormal termination.

It is highly likely that the request to the application AP that is executed immediately before the abnormal termination is the cause of the abnormal termination. Displaying the application AP that is executed in the abnormally terminated process immediately before the abnormal termination in a manner distinguishable from the other applications AP that are executed in the abnormally terminated process on the display screen W is useful in determination of the cause. The application AP that is determined to be the cause of the abnormal termination can be disabled or deleted uninstalled by selecting an appropriate action button.

In this way it is possible to take a proper action on an abnormally terminated process easily on the display screen W and thus to restore the multi process environment to a stable state.

The display screen W of is for indicating detection of an abnormal termination of a process and prompting a user to disable the process. The abnormally terminated process may be disabled using such a simple display screen W.

If the abnormally terminated process is disabled or the application AP that is the cause of the abnormal termination is uninstalled the multi process environment may automatically be rebooted.

As described above the information processing device of this embodiment an abnormal termination of a process for an application AP managed by the application management software is detected. Then the application management software sends information indicating detection of the abnormal termination to all the components of the application management software and in order to prevent the application AP that is not operating properly from affecting operations of other applications AP causes the components to make management information pieces related to the application AP which is executed on the abnormally terminated process consistent with each other. In this way the application management software performs application management.

Accordingly the information processing device of this embodiment can achieve the same effect as the information processing devices of the first and second embodiments and can isolate if the process for executing an extended function is abnormally terminated the abnormally terminated process from the system in order to allow the basic functions to remain operable.

In the third embodiment the configuration in which three different processes are provided for executing application management functions basic functions and an extended function respectively is used as an example of a multi process environment on which the process abnormal termination detection reporting function is executed. However it is apparent that the process abnormal termination detection reporting function may be executed in the configuration of the second embodiment in which two processes are provided.

The functions of the information processing devices in the above described embodiments are provided by causing a computer to execute an application execution program including the procedures of and encoded in programming language corresponding to the operating environment i.e. platform . The application execution programs may be stored in a computer readable storage medium.

The image processing apparatus of the first embodiment includes the scanner unit for scanning a document to obtain image data the printing unit for printing the image data onto paper and one of the information processing devices of the first and second embodiments and therefore can achieve the same effect as the information processing devices of the first and second embodiments.

The number of the processes executed by the execution unit in the above described embodiments does not limit the scope of the present invention. More specifically the present invention may include embodiments in which the process A for application management and one or more processes for applications are provided.

The present invention is not limited to the above described embodiments and variations and modifications may be made without departing from the scope of the invention.

an execution unit configured to execute a first process a second process and a third process wherein a function of an application is provided by operating the input unit the processing unit and the output unit in conjunction with each other the first process executes application management software that manages activation and termination of the application the second process executes basic application software that provides a basic function of the information processing device and the third process executes extended application software that provides an extended function added to the information processing device 

a reporting unit configured to send information indicating the abnormal terminations of the second and third processes detected by the detection unit to the first process configured to execute the application management software 

 2 An application execution method for use in an information processing device including an input unit configured to input data a processing unit configured to process the data and an output unit configured to output the data wherein a function of an application is provided by operating the input unit the processing unit and the output unit in conjunction with each other the application execution method comprising 

a step of executing application management software that manages activation and termination of the application basic application software that provides a basic function of the information processing device and extended application software that provides an extended function added to the information processing device in different processes.

 3 An application execution method for use in an information processing device including an input unit configured to input data a processing unit configured to process the data and an output unit configured to output the data wherein a function of an application is provided by operating the input unit the processing unit and the output unit in conjunction with each other the application execution method comprising 

a step of executing application management software that manages activation and termination of the application and basic application software that provides a basic function of the information processing device in a first process and

a step of executing extended application software that provides an extended function added to the information processing device in a second process.

 4 An application execution method for use in an information processing device including an input unit configured to input data a processing unit configured to process the data and an output unit configured to output the data wherein a function of an application is provided by operating the input unit the processing unit and the output unit in conjunction with each other the application execution method comprising 

a step of executing a first process for executing application management software that manages activation and termination of the application 

a step of executing a second process for executing a component program that functions as an input unit a processing unit and or an output unit and is preinstalled in the information processing device and

a step of executing a third process for executing a component program that functions as an input unit a processing unit and or an output unit and is added to the information processing device for function extension.

 5 An application execution method for use in an information processing device including an input unit configured to input data a processing unit configured to process the data and an output unit configured to output the data wherein a function of an application is provided by operating the input unit the processing unit and the output unit in conjunction with each other the application execution method comprising 

a step of executing a first process for executing application management software that manages activation and termination of the application and a component program that functions as an input unit a processing unit and or an output unit and is preinstalled in the information processing device and

a step of executing a second process for executing a component program that functions as an input unit a processing unit and or an output unit and is added to the information processing device for function extension.

 6 A computer readable recording medium storing an application execution program for use in an information processing device the information processing device including an input unit configured to input data a processing unit configured to process the data and an output unit configured to output the data wherein a function of an application is provided by operating the input unit the processing unit and the output unit in conjunction with each other the application execution program including computer executable instructions for executing a method comprising 

a step of executing application management software that manages activation and termination of the application basic application software that provides a basic function of the information processing device and extended application software that provides an extended function added to the information processing device in different processes.

 7 A computer readable recording medium storing an application execution program for use in an information processing device the information processing device including an input unit configured to input data a processing unit configured to process the data and an output unit configured to output the data wherein a function of an application is provided by operating the input unit the processing unit and the output unit in conjunction with each other the application execution program including computer executable instructions for executing a method comprising 

a step of executing application management software that manages activation and termination of the application and basic application software that provides a basic function of the information processing device in a first process and

a step of executing extended application software that provides an extended function added to the information processing device in a second process.

 8 A computer readable recording medium storing an application execution program for use in an information processing device the information processing device including an input unit configured to input data a processing unit configured to process the data and an output unit configured to output the data wherein a function of an application is provided by operating the input unit the processing unit and the output unit in conjunction with each other the application execution program including computer executable instructions for executing a method comprising 

a step of executing a first process for executing application management software that manages activation and termination of the application 

a step of executing a second process for executing a component program that functions as an input unit a processing unit and or an output unit and is preinstalled in the information processing device and

a step of executing a third process for executing a component program that functions as an input unit a processing unit and or an output unit and is added to the information processing device for function extension.

 9 A computer readable recording medium storing an application execution program for use in an information processing device the information processing device including an input unit configured to input data a processing unit configured to process the data and an output unit configured to output the data wherein a function of an application is provided by operating the input unit the processing unit and the output unit in conjunction with each other the application execution program including computer executable instructions for executing a method comprising 

a step of executing a first process for executing application management software that manages activation and termination of the application and a component program that functions as an input unit a processing unit and or an output unit and is preinstalled in the information processing device and

a step of executing a second process for executing a component program that functions as an input unit a processing unit and or an output unit and is added to the information processing device for function extension.

The present application is based on Japanese Priority Application No. 2007 290214 filed on Nov. 7 2007 and Japanese Priority Application No. 2008 222129 filed on Aug. 29 2008 with the Japanese Patent Office the entire contents of which are hereby incorporated herein by reference.

