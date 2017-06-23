---

title: Image processing device, image processing method, and computer program product for image processing incorporating pipes and filters
abstract: An image processing device includes an input filter configured to control an input process of data to be input as a subject of an image process, an output filter configured to control an output process of data to be output to an outside of the image processing device, a processing filter configured to process the data between the input filter and the output filter, and a pipe configured to transmit the data among the input filter, the processing filter, and the output filter.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08228536&OS=08228536&RS=08228536
owner: Ricoh Company, Ltd.
number: 08228536
owner_city: Tokyo
owner_country: JP
publication_date: 20080529
---
The present invention generally relates to image processing devices image processing methods and computer program products for image processing. More specifically the present invention can be applied to an image processing device an image processing method and a computer program product for image processing wherein the concepts of pipes and filters are applied.

In recent years image processing devices such as printers copiers scanners facsimiles and multi functional devices configured to perform these functions as well as computers generally have CPUs Central Processing Units . Each function is performed by control of applications.

For example an image forming device described in Japanese Patent No. 3679349 has as a platform a function commonly used by each application. The application can be installed by using an API Application Programming Interface of this platform. According to this image forming device because a function commonly used is installed as a part of the platform it is possible to avoid separately installing the function for every application and to improve development efficiency of all the applications.

However in the platform having the API commonly used if the function provided by this platform or granularity of the interface is not properly designed the development efficiency of the application may be less than expected.

For example if this granularity is too small while the application provides simple services a great number of accesses to the API is required so that the source code may be complex.

On the other hand in a case where the granularity is too large if an application configured to provide service where modification is made to a part of a certain function is expected top be installed it is necessary to modify the platform so that the number of developments may be increased. Especially in a case where each module in the platform strongly depends on the application it is necessary to add a new function in the platform and correct an existing part and therefore the situation may become more complex.

For example if an application is expected to be installed where a part of the service provided by the existing application such as an input process of an image is changed it is not possible to access the existing application in a part other than the changed part. Accordingly it is necessary to rewrite the source code again and install a new application.

Accordingly embodiments of the present invention may provide a novel and useful image processing device image processing method and computer program product for image processing solving one or more of the problems discussed above.

More specifically the embodiments of the present invention may provide an image processing device an image processing method and a computer program product for image processing whereby it is possible to simplify customization or expansion of functions.

One aspect of the present invention may be to provide an image processing device including an input filter configured to control an input process of data to be input as a subject of an image process an output filter configured to control an output process of data to be output to an outside of the image processing device a processing filter configured to process the data between the input filter and the output filter and a pipe configured to transmit the data among the input filter the processing filter and the output filter wherein an application is formed by connecting the input filter the processing filter and the output filter to each other and the pipe receives the reading request of the data including an identifier for identifying the data from the processing filter or the output filter connected to an output side of the pipe so as to transmit the reading request to the input filter or the processing filter respectively connected to an input side of the pipe. According to the above mentioned image processing device it is possible to simplify customization or expansion of functions.

The input filter and or the processing filter may receive the reading request including the identifier and perform a process for generating data where the identifier is provided. According to the above mentioned image processing device it is possible to make an input side filter process data expected to be used by an output side filter with a priority so that demand of the output side can be reflected to an input side.

The identifier may be provided for the data in the input process by the input filter. The image processing device may further include an operations part configured to perform process operations of the image processing device a control part configured to control the pipe and a dependent pipe generation part configured to generate a dependent pipe depending on and provided to the pipe wherein in a case where plural output filters are selected for a single input filter selected by the operations part the control part makes the pipe generate the dependent pipe by using the dependent pipe generation part the control part connects a single pipe or the single dependent pipe to an input side and or an output side of the input filter the processing filter and the output filter so as to perform an output process and the dependent pipe transmits the reading request to the pipe generating the dependent pipe when the reading request is transmitted to the dependent pipe. According to the above mentioned image processing device in multiple outputs in a case where plural output filters are selected each filter can perform the multiple outputs by the same process as a process where a single output filter is selected.

Each of the pipe and the dependent pipe may have a data management part configured to manage the data in the pipe and the dependent pipe respectively the corresponding data management parts may determine whether data corresponding to the identifier included in the reading request exist in the pipe and the dependent pipe and the corresponding data management parts may not send the reading request in a case where the data corresponding to the identifier exist in the pipe and the dependent pipe. According to the above mentioned image processing device the same reading requirement is not transferred to the input side filter in an overlapped manner.

The pipe may include a request management part configured to manage whether the reading request is transmitted to the processing filter or the input filter connected to a front stage of the pipe. According to the above mentioned image processing device it is possible to manage whether the reading requirement received by the pipe is transferred to the input side filter.

The data management part may determiner based on the request management part whether the reading request is transmitted to the processing filter or the input filter connected to a front stage of the pipe and the data management part may not transmit the reading request to the input filter or the processing filter in a case where the reading request is already transmitted to the processing filter or the input filter connected to the front stage of the pipe. According to the above mentioned image processing device the same reading requirement is not transferred to the input side filter in an overlapped manner.

Another aspect of the present invention may be to provide an image processing method used for an image processing device the image processing device including an input filter configured to control an input process of data to be input as a subject of an image process an output filter configured to control an output process of data to be output to an outside of the image processing device a processing filter configured to process the data between the input filter and the output filter a pipe configured to transmit the data among the input filter the processing filter and the output filter wherein an application is formed by connecting the input filter the processing filter and the output filter to each other the image processing method including the steps of receiving by the pipe the reading request of the data including an identifier for identifying the data from the processing filter or the output filter connected to an output side of the pipe and transmitting the reading request to the input filter or the processing filter respectively connected to an input side of the pipe. According to the above mentioned image processing method it is possible to simplify customization or expansion of functions.

Other aspect of the present invention may be to provide a computer program product for image processing the product having an image processing program the image processing program used for an image processing device the image processing device having a processing device and a storage device the image processing device including an input filter configured to control an input process of data to be input as a subject of an image process an output filter configured to control an output process of data to be output to an outside of the image processing device a processing filter configured to process the data between the input filter and the output filter a pipe configured to transmit the data among the input filter the processing filter and the output filter wherein an application is formed by connecting the input filter the processing filter and the output filter to each other and the image processing program is performed by implementing an image processing method by the processing device the image processing method including the steps of receiving by the pipe the reading request of the data including an identifier for identifying the data from the processing filter or the output filter connected to an output side of the pipe and transmitting the reading request to the input filter or the processing filter respectively connected to an input side of the pipe. According to the above mentioned computer program product it is possible to simplify customization or expansion of functions.

Other objects features and advantages of the present invention will become more apparent from the following detailed description when read in conjunction with the accompanying drawings.

In embodiments of the present invention software architecture based on a technique called pipes and filters is applied to an image processing device so that it is possible to simplify customization or expansion of functions of the image processing device.

Furthermore in the embodiments of the present invention an identifier is given to data and a reading requirement including the identifier is transferred from the output side to the input side and thereby data reflecting the requirement of the output side is read out.

In addition in the embodiments of the present invention in the multiple output process where plural output filters are selected for a single input filter a main pipe forms a dependent pipe and the main pipe and the dependent pipe are connected to each other corresponding to plural output filters. As a result of this output processes in plural output filters are performed simultaneously in parallel.

The filter is a program configured to perform a designated process on input data and output a process result. The pipe is a part configured to connect the filters to each other. The pipe holds a process result having been output from a filter connected to an input side of the pipe for a while and transfers data to a filter connected to an output side of the pipe. Thus according to the concepts of pipes and filters it is possible to continuously perform a process of the filter via the pipe.

In the image processing device of the embodiments of the present invention a designated process by a filter is regarded as a process whereby a designated conversion is applied to input data. In other words in the image processing device of the embodiments of the present invention each function performed by the image processing device is regarded as part of the continuity of a conversion process of a document input data . Each function of the image processing device is regarded to be formed by input processing and output of the document namely data.

Accordingly in the image processing device of the embodiments of the present invention each of input process processing process and output process is regarded as a conversion process and a software component configured to perform a single conversion process is formed as a filter.

In the image processing device of the embodiments of the present invention a filter configured to control an input process of the data is regarded as an input filter. A filter configured to control an processing process of the data is regarded as a processing filter. A filter configured to control an output process of the data is regarded as an output filter. Each of these filters is an independent program and there is no dependency among these filters. Accordingly each filter can be independently installed or uninstalled with a filter unit in the image processing device.

An image processing device of the first embodiment of the present invention is discussed with reference to . Here is a schematic hardware structure view of the image processing device of the first embodiment of the present invention.

As shown in the image processing device includes a scanning device a plotter a drive device an auxiliary storage device a memory device a processing device an interface device and an operations panel . The scanning device the plotter the drive device the auxiliary storage device the memory device the processing device the interface device and the operations panel are connected to each other by a bus B.

The scanning device includes a scanner engine and an engine control part. The scanning device is configured to scan a paper so as to make image data.

The plotter includes a plotter engine and an engine control part. The plotter is configured to print the image data.

The interface device includes a modem a LAN card and other devices and is used for connecting to a network.

The operations panel is used for performing operations with respect to processes of the image forming process . The operations panel includes display functions such as a touch panel.

The image processing program of the first embodiment of the present invention is at least a part of various programs configured to control the image processing device . The image processing program is provided by for example distributing a recording medium where the image processing program is recorded or downloading the image processing program from the network.

A recording medium where information is optically electrically or magnetically recorded such as a CD ROM a flexible disk or an optical magnetic disk a semiconductor memory where information is electrically recorded such as a ROM or a flash memory or the like can be used as the recording medium where the image processing program is recorded.

When the recording medium where the image processing program is recorded is set in the drive device the image processing program is installed from the recording medium into the auxiliary storage device via the drive device . The image processing program downloaded from the network is installed in the auxiliary storage device via the interface device .

The image processing device stores not only the installed image processing program but also necessary files data and the like. The memory device reads the image processing program from the auxiliary storage device at the time when the computer starts and loads the image processing program. The processing device following the image processing program being loaded in the memory device performs a function of each part and each process.

In the image processing device the above discussed concepts of pipes and filters are applied to software architecture configured to perform various functions of the image processing device .

The image processing device is a multiple function device configured to perform plural functions such as a printer a copier a scanner and a facsimile machine.

Software configured to perform functions of the image processing device has a layered structure. The software is formed by a user interface layer a control layer an application logic layer a device service layer and a device control layer . Higher and lower relationships of each layer are based on access relationships among the layers. In other words in the example shown in a high order layer accesses a low order layer.

In the image processing device when an order from the user for performing various kinds of functions is received by the user interface layer the user interface layer accesses the control layer so as to control the application logic layer based on this performing request. The application logic layer runs the application configured to perform the function required based on the order from the control layer . Based on the result the device layer and the device control layer control the hardware resources of the image processing device . In the image processing device output results corresponding to the functions received by the user interface layer are retrieved.

The user interface layer includes for example a communication server part and a local UI User Interface part . The interface layer has a function for receiving performing requests for performing each function of the image processing device . Here each function is for example a copier function a printing function a scanning function or a FAX function.

In the user interface layer for example the communication server part may receive the performing request from a client PC Personal Computer not shown in or the like via a network. The local UI part may receive the performing request via for example the operations panel provided in the image processing device . Details of the operations panel are discussed below. The performing request received by the user interface layer is transferred to the control layer .

A function for controlling a process whereby each function of the image processing device is performed is installed in the control layer . More specifically for example the control layer connects each filter in the application logic layer by the pipe corresponding to the requested function and control performing the functions by using the connected filters.

In addition the control layer corresponds to a control part in claims described below and controls the pipe . The control layer controls the pipe based on the performing request received by the user interface layer . Control of the pipe by the control layer is discussed below.

The function of the image processing device discussed in this embodiment means definition of a single unit service provided to the user by the image processing device service from the input of the request to final output . The function of the image processing device is equivalent to an application providing the single unit service from the perspective of software.

Various filters that are component groups configured to perform a part of functions provided in the image processing device are provided in the application logic layer .

In the application logic layer a single function is performed by combining plural filters by control of the control layer . The application logic layer includes an input filter a processing filter and an output filter . Each of these filters is operated based on the same definition and controlled based on the same definition by the control layer . Details of each filter are discussed below.

A lower order function that each filter of the application logic layer commonly uses is installed in the device service layer . A pipe a data management part and others are provided in the device service layer of the image processing device . The pipe performs functions of the pipe discussed above. The pipe transfers the output result of a certain filter among filters provided in the application logic layer to another filter.

User information registered in a database in the image processing device by for example a user or document data or image data where various kinds of processes are applied in the image processing device may be stored in the data management part .

A driver that is a program configured to control hardware is installed in the device control layer of the image processing device of this embodiment. The device control layer includes for example a scanner control part a plotter control part a memory control part a phone line control part a network control part and other parts. Each control part controls each device named in that control part.

In the following explanation each filter provided in the application logic layer is further discussed.

The input filter of the image processing device is configured to control an input process for data being input from outside of the image processing device . The input filter includes a reading filter a stored document reading filter an e mail receiving filter a FX receiving filter a PC document receiving filter a report filter and other filters.

The reading filter is configured to control for example reading the image data input by the scanner and outputting the read image data.

The e mail receiving filter is configured to receive an e mail in the image processing device and to output data included in the received e mail.

The PC document receiving filter is configured to receive printing data from the client PC not shown or the like and to output the printing data.

The report filter is configured to arrange setting information or hysteresis information of the image processing device in for example a table format so as to output the arranged data. Here the stored document reading filter is configured not to read data from an outside of the image processing device but read data stored in for example the data management part in the image processing device or a storage device not shown in of the image processing device so as to output the stored data.

The processing filter of the image processing device is configured to apply a designated process to data input from an input side pipe of the processing filter and to output the process result to an output side filter of the processing filter . The processing filter includes a document processing filter a document conversion filter and other filters.

The document processing filter is configured to apply a designated image conversion process to input data so as to output the result. This image conversion process may be for example an aggregation process an expansion process a contraction process or the like of the input data.

The document conversion filter applies a rendering process to the input data so as to output the results. In other words Post Script data input to the document conversion filter is converted into bit map data so as to be output.

The output filter of the image processing device is configured to control the output process for the input data and output the results to the outside of the image processing device . The output filter includes a printing filter a stored document registration filter an e mail transmitting filter a FAX transmitting filter a PC document transmitting filter a preview filter and other filters.

The printing filter is configured to make the plotter output print the input data. The e mail transmitting filter is configured to attach the input data to an e mail and send the e mail.

The FAX transmitting filter is configured to make FAX transmission of the input data. The PC document transmitting filter is configured to transmit the input data to a client PC not shown in .

The preview filter is configured to preview the input data using the operations panel of the image processing device .

The data being output from the document registration filter are exceptionally output to not the outside of the image processing device but the storage device or the data management part in the image processing device so as to be stored.

In the application logic layer each filter is combined so that each function of the image processing device is performed. According to the above discussed structure in the image processing device it is possible to perform various functions based on the combination of the filters and the pipe. More specifically for example in a case where the copier function is expected to be performed the reading filter the document processing filter and the printing filter may be combined.

Before explaining the operations of the image processing device of this embodiment basic operations of the image processing device where the concepts of pipes and filters are applied are discussed with reference to .

The input filter inputs data from the input device in step S and outputs the data to the pipe connected to the output side in step S. In a case where the data are input at plural time intervals such that plural sheets of paper are scanned input of the data and output of the result to the pipes are repeated.

When a process of all input data is completed YES in step S the process of the input filter is completed.

When the processing filter detects input of the data to the pipe connected to the input side the process starts.

First the data are read from the pipe in step S and the image processing is applied to the data in step S.

Next the data as process results are output to the pipe connected to the output side in step S. When a process of inputting all the data to the input side pipe is completed YES in step S a process of the processing filter is completed.

When the output filter detects input of the data to the pipe connected to the input side the output filter starts a process.

First the output filter reads the data from the pipe in step S. Then the output filter outputs the read data by using an output device in step S. After processing all the data input to the input side pipe YES in step S the process of the output filter is completed.

Thus in the image processing device each function is performed by using each corresponding filter as a component. Accordingly it is possible to simply customize or expand the functions. In other words because there is no functional dependence among the filters and independence is maintained it is possible to easily develop new functions applications by newly adding a filter or changing a combination of the filters. Hence when installation of a new application is requested if a part of a process of the application is not installed only a filter configured to perform the part of the process may be developed and installed.

Accordingly it is possible to decrease the frequency of modification generated corresponding to equipment of the new application for a layer lower than the control layer and the application logic layer . Therefore it is possible to provide a stable platform.

Because of this it is possible to improve the development efficiency of the application without an influence of functions provided by the platform or the granularity of the interface. In addition if an application is expected to be installed where a part of the service provided by the existing application is to be changed only that part of the filter providing this service need be changed. Hence there is no need to write new source code and it is possible to improve the development efficiency.

In the image processing device of this embodiment of the present invention operations for transmitting the reading request by the pipe including an identifier of the data from the output side to the input side are performed in addition to the basic operations discussed above.

The input filter of this embodiment includes a function for providing an identifier for identifying data to the input data in the input process. The identifier of the data in this embodiment may be provided in the order where for example the input filter retrieves the data. For example in a case where data are read by the scanning device the number may be provided in the sequential order where the scanning device reads and this number may be the identifier.

This identifier is not limited to the sequential order where the data are retrieved as discussed above as long as the input data can be identified. In addition a method for providing the identifier may not be limited to the above mentioned method. For example the identifier may be provided based on the size of the input data or the like.

When the output filter of this embodiment receives information for specifying the data to be output by the operations panel or the like the output filter includes this information as an identifier of the data in the reading request. In addition the output filter transmits the reading request of the data including the identifier of the data to the pipe connected to a front stage of the output filter .

It is preferable that in the image processing device of this embodiment an identifier provided for the data in the input filter and information for specifying the data retrieved by the output filter correspond to each other.

For example in a case where the copying process is performed in the image processing device the number of the retrieved data item is regarded as the identifier in the input filter . The number of pages retrieved by the operations panel is regarded as information for specifying the data in the output filter .

The pipe of this embodiment transmits a reading request of the data including the identifier of the data from the output side of the pipe to the input side of the pipe by functions of the above mentioned input filter and the output filter .

Accordingly in the image processing device of this embodiment even if the sequential order where the input filter retrieves the data and the sequential order of the data required by the output filter in actual image processing are different from each other regardless of the sequential order where the input filter retrieves the data it is possible to specify the data requested by the output filter and retrieve the data.

Accordingly in the image processing device of this embodiment the reading request of the output side is transmitted to the input side so that entire process speed can be improved.

The input filter inputs data from the input device and provides an identifier for identifying data to the input data in step S. The input filter correlates the data and the identifier provided to the data to each other and outputs the data with the identifier to the pipe connected to the output side of the input filter in step S.

When data are input at plural times such that plural sheets of papers are scanned input of the data and output of the result to the pipe are repeated. After a process for all input data are completed YES in step S a process of the input filter is completed.

When the processing filter receives the reading request including the identifier of the data from the pipe connected to the output side of the processing filter the processing filter transmits the reading request of the data corresponding to the identifier to the pipe connected to the input side of the processing filter in step S.

The processing filter reads the data corresponding to the identifier from the pipe in step S and performs a process for processing written data in step S.

In addition the processing filter correlates the data after the process is applied and the identifier of the data to each other so as to write them in the pipe connected to the output side in step S. In a case where there are no data corresponding to the identifier in the input side pipe YES in step S the process of the processing filter is completed.

The output filter transmits the reading request including the identifier for identifying the data specified as the data to be output to the pipe connected to the input side of the output filter in step S.

In the image processing device of this embodiment by operating the operations panel for example the data to be output may be determined. More specifically for example in a case where the printing process from page through page is selected by the operations panel the output filter may regard the specified data as image data from page through page and may regard the identifier of the specified data as page through page .

The output filter reads the data linked to the identifier from the pipe connected to the front stage of the output filter in step S. The data to be read are data already processed by the processing filter . The output filter outputs the data being read in step S. In a case where there are no data corresponding to the identifier in the input side pipe YES in step S the output filter completes the process of the output filter .

Next a flow of transmission of the reading request in the image processing device of this embodiment is discussed with reference to .

In an example shown in the input filter the reading filter and the FAX receiving filter are provided. In this example the sequential order of input of the data is determined. The input filter provides the sequential order where data are input as the identifier to the data.

In the image processing device the input filter and the processing filter are connected to each other by the pipe . The processing filter and the output filter are connected to each other by the pipe

In the image processing device when the data are input from outside the input filter provides the identifier to the input data relates the data and the identifier to each other and writes the data and the identifier into the pipe in step S.

When the output filter receives the performing request of the output process of the specified data in step S the output filter transmits the reading request including the identifier for identifying the data specified as the data to be output to the pipe connected to the front stage of the output filter in step S. The pipe transmits the reading request including the identifier of the data to the process filter connected to the input side of the pipe in step S.

Because the process filter performs the processing process on the data corresponding to the identifier included in the reading request the process filter transmits the reading request to the pipe in step S. The data corresponding to the identifier are written in the pipe . When the pipe receives the reading request from the processing filter the data corresponding to the identifier included in the reading request are written in the processing filter in step S.

The processing filter performs the processing process on the written data and outputs the processed data to the pipe in step S. The output filter detects that the data are written in the pipe and reads the data written in the pipe in step S. The output filter performs the output process to the read data so as to output the data.

In an example shown in similar to a stored document reading filter the data stored in the storage device in the image forming device such as a hard disk drive are written in advance in the pipe . In the example shown in because the identifier is provided in the data so as to be stored in the storage device the input filter can write optional data to the pipe

The processes from step S to step S in are the same as those from step S to step S in . When the pipe receives the reading request including the identifier in step S the pipe transmits the reading request to the input filter in step S.

The input filter writes the data corresponding to the identifier included in the reading request in the pipe in step S. When the processing filter detects that the data corresponding to the identifier are written in the pipe the processing filter reads the data from the pipe in step S. The processes of step S and step S are the same as those of step S and step S in .

Accordingly in the image processing device of this embodiment the reading request from the output side is transmitted to the input side so that entire process speed can be improved.

In addition according to the image processing device of this embodiment various functions can be performed by combining the filters and the pipes. Hence it is possible to simplify the customization or expansion of the functions.

In the second embodiment of the present invention a multi output process is applied to the image processing device of the first embodiment of the present invention. Accordingly a process corresponding to multiple outputs is discussed in the second embodiment of the present invention and in through parts that are the same as the parts shown in through are given the same reference numerals and explanation thereof is omitted.

In the image processing device there is a case where data input from a single input filter may be output by plural output filters by different output methods.

In an example shown in the data being read by the reading filter included in the input filter are output as four kinds of output data by using four output filters namely the printing filter the stored document registration filter the e mail transmission filter and FAX transmission filter included in the output filter . Thus a process where data are input from a single input filter and are output from plural output filters is called a multiple output process.

It is relatively easy to perform the multiple output process in the image processing device where the concepts of pipes and filters are applied. However depending on the design of the pipe the memory capacity provided in the image processing device may have an influence. In addition operations of start interruption restart and stop of the process in the image processing device may not be controlled for every output filter. In addition an independence of the process in each filter may not be maintained due to the multiple output process.

In this embodiment a parent child relationship is made to the pipe in the case of the multiple output process so that the above mentioned problem can be solved in addition to the effect achieved by the first embodiment of the present invention.

In the second embodiment of the present invention the pipe A is made to have the function of a parent pipe and the parent pipe is made to generate a child pipe in the multiple output process. The child pipe performs the same operations as those in a single output process where a single output filter is selected compared to a single input filter . The parent pipe controls the status of both parent pipe and the child pipe and performs management.

Furthermore in the image processing device of the second embodiment of the present invention the parent pipe and the child pipe and plural output filters correspond to each other and are connected to each other. The parent pipe corresponds to a pipe in the claims below. The child pipe corresponds to a dependent pipe in the claims below.

With this structure in the multiple output process a certain parent pipe or a certain child pipe is connected to a front stage of the output filter. In addition each filter is connected to the front stage and the subsequent stage of the parent pipe and the child pipe. In other words the connection status of the pipe and the filter is the same as that in a case of the single output process. Because of this in the second embodiment of the present invention it is possible to control of the filter in the multiple output process in the same manner as the single output process.

In the second embodiment of the present invention when plural output filters are selected by the operations panel so that execution of the process is ordered the control layer starts control of the pipe.

The control layer generates the child pipe by a child pipe generation function of the pipe A that is a parent pipe. Details of the function of the pipe A as the parent pipe are discussed below.

When the child pipe is generated the control layer determines which filter is connected to which pipe based on the selected input filter and the output filter .

The control layer connects the input filter to the front stage of the pipe A as the parent pipe. The control layer also connects a single output filter to the pipe A and the child pipe . In this case the control layer may be set in advance so that proper connection can be selected depending on kinds of the filter and the pipe. Furthermore in the control layer in a case where the processing filter is provided between the input filter and the output filter a single pipe is connected to the front stage and the subsequent stage of the processing filter.

Functions of the pipe A of the second embodiment of the present invention are discussed with reference to .

The pipe A is for example a memory HDD Hard Disk Drive . Each function of the pipe A discussed below may be performed by a program stored in this memory.

The pipe A includes a child pipe generation part a pipe management part a data management part a retrieval status table a request management table and a reference data storage part .

The child pipe generation part works so that the pipe A as the parent pipe generates the child pipe and corresponds to a dependent pipe generation part of claims below.

The pipe management part works so that the pipe A controls and manages the status of the pipe A and the child pipe

The data management part is configured to manage actual data being output from the filter connected to the front stage of the pipe A. In addition the data management part determines whether data corresponding to the identifier included in the reading request exist in the pipe A so as to manage the reading request based on the result of the determination. The data management part corresponds to a data management part in claims below.

Information indicating the reference status of the actual data in the pipe A and the child pipe is stored in the retrieval status table .

The request management table is configured to manage the reading request of the data corresponding to the filter connected to the front stage of the pipe A. The request management table corresponds to a request management part in claims below.

Reference data indicating a reference subject of the actual data are stored in the reference data storage part .

The data management part is configured to determine whether data corresponding to the identifier included in the reading request is in the child pipe so as to manage the reading request based on the result of determination. The data management part corresponds to a data management part in claims below.

The reference data as well as the reference data of the pipe A are stored in the reference data storage part .

In the example shown in there are two output filters selected in the multiple output process. A single output filter is connected to the subsequent stage of the pipe A parent pipe and the subsequent stage of the child pipe . The filter to be connected to the front stage of the pipe A may not be an input filter but instead a processing filter. In addition a filter of the subsequent stage of the pipe A and the child pipe may not be an output filter but instead a processing filter.

In the pipe A when the data are output from the front stage filter the data management part writes actual data which are output data to a memory controlled by the memory control part . In addition the data management part writes reference data to the reference data storage part of the pipe A.

The reference data are used for referring to actual data written in the memory. The reference data are information indicating for example a place where the actual data are written. It is possible to access the actual data written in the memory by following the reference data. The reference data may be provided from for example the memory control part to the pipe A.

When writing the actual data in the memory and writing the reference data in the reference data storage part are completed in the pipe A the pipe A writes the reference data in the reference data storage part of the child pipe . The reference data written in the reference data storage part of the child pipe are the same as the reference data written in the reference data storage part of the pipe A.

Thus in the second embodiment of the present invention the actual data being output from the filter of the front stage of the pipe A are stored for a while in the memory which is a storage device outside the pipe A. Access from the pipe parent pipe A and the child pipe to the memory can be made by storing the reference data corresponding to the actual data in both the pipe parent pipe A and the child pipe

Because of this in this embodiment even if the number of pipes is increased by the multiple output process the amount of the actual data actually written in the memory is the same. Accordingly the memory is not pressed by execution of the multiple output process. While the amount of the data is increased by the reference data written in each pipe in the multiple output process the amount of the reference data is extremely small compared to the amount of the actual data. Hence it is not necessary to consider the amount of the reference data.

Next basic operations in a case where the data are read from the pipe A and pipe by the filter of the subsequent stage of the pipe A and the child pipe as shown in are discussed with reference to .

When the pipe A receives an order for reading the data from the filter of the subsequent stage the pipe A refers to the reference data written in the reference data storage part . The pipe A retrieves the actual data written in the memory based on the reference data so as to transmit the retrieved actual data to the filter of the subsequent stage.

When the child pipe receives the order for reading the data from the filter of the subsequent stage the child pipe retrieves the actual data written in the memory based on the reference data written in the reference data storage part . The child pipe transmits the retrieved actual data to the filter of the subsequent stage. In other words the child pipe performs the same operations as the pipe A.

Next basic operations of the pipe A and the child pipe after reading the data from the pipe A and the child pipe by the filter is completed as shown in are discussed with reference to .

As shown in when the data are read at the filter of the subsequent stage of the child pipe the child pipe reports that the data have been read to the pipe A. When the pipe A receives this report in a case where the data written in the memory are already referred to by both the pipe A and the child pipe the actual data are destroyed by the data management part .

Next destruction of the actual data is discussed with reference to . is a sequential diagram for explaining a process of destroying the actual data.

In an example shown in a filter of a subsequent stage of the pipe A is defined as an output and a filter of a subsequent stage of the child pipe is defined as an output .

Based on the order for reading from the output the pipe A refers to the reference data and reads the actual data in step S. The pipe A destroys the reference data with respect to the actual data written in the reference data storage part in step S.

Next based on the order for reading from the output the pipe refers to the reference data and reads the actual data in step S. The pipe destroys the reference data with respect to the actual data written in the reference data storage part in step S. The child pipe reports that the actual data have been read to the pipe A in step S.

When the pipe A confirms that the actual data have been read based on the reference data and have been retrieved by both the pipe A and the child pipe the data management part of the pipe A destroys the actual data from the memory in step S.

In addition the pipe A of the second embodiment of the present invention manages the retrieval status of the actual data in the pipe A and the child pipe by using the retrieval status table .

The pipe A of the second embodiment of the present invention uses the retrieval status table and manages the retrieval status of the actual data of the pipe A and the child pipe

The pipe A manages by using the retrieval status table the reference status of the reference data and the retrieval status of the actual data in the pipe A and the child pipe . In a case where the reference data are referred to by both the pipe A and the child pipe and then destroyed the pipe A determines that the actual data have been read from the pipe A and the child pipe and retrieved. When the actual data are retrieved from both the pipe A and the child pipe the actual data are deleted from the memory by the data management part .

In the pipe A the data management part destroys the actual data written in the memory based on the retrieval status table .

In the retrieval status table shown in the actual data are retrieved by both the pipe A and the child pipe . In this case in the retrieval status table information indicating that the actual data are already retrieved in the pipe A and the child pipe is stored as the retrieval status with respect to the actual data . Accordingly the data management part destroys the actual data based on this information.

In the retrieval status table shown in the actual data are retrieved from the pipe A and not retrieved yet from the pipe . In this case the retrieval status table shows as the retrieval status of the actual data information of already retrieved with respect to the pipe A and information of not retrieved yet with respect to the child pipe are stored. Accordingly the data management part keeps the actual data based on this information.

Thus the data management part destroys the actual data when the actual data are retrieved by both the pipe A and the child pipe namely all pipes having the reference data with respect to the actual data. Accordingly in the second embodiment of the present invention the actual data already retrieved are not kept for a long time and the memory can be efficiently used.

Furthermore in the second embodiment of the present invention each of the pipe A and the child pipe has the reference data storage part. Accordingly the filter of the front stage of the pipe A can write the data to the pipe A at an optional timing. The subsequent filter of the pipe A and the pipe can read the data from the pipe A at an optional timing. In addition the subsequent filter of the child pipe can read the data from the child pipe at an optional timing.

Next operations in a case where the specific data are read in the second embodiment of the present invention are discussed with reference to .

In the example shown in a filter connected to an input side of the pipe A is defined as an input a filter connected to an output side of the pipe A is defined as an output and a filter connected to an output side of the child pipe is defined as an output .

The pipe A and the child pipe of the second embodiment of the present invention transmit the reading request including the identifier of the data from the output or the output to the input .

When the pipe A receives the reading request including the identifier from the output in step S the pipe A transmits the reading request including the identifier to the input in step S. When the input receives the reading request including the identifier the input outputs data corresponding to the identifier in step S. When the data corresponding to the identifier is output from the input the data management part in the pipe A writes the identifier and the actual data which are output data into a memory controlled by the memory control part in step S.

In addition the data management part writes the identifier and the reference data for referring to the actual data written in the memory to the reference data storage part of the pipe A in step S.

Next the data management part writes the identifier and the reference data to the reference data storage part of the child pipe in step S. Based on the reference data and the identifier the pipe A writes the actual data corresponding to the identifier to the output in step S.

Next a case where the child pipe receives the reading request including the identifier from the output is discussed.

When the child pipe receives the reading request including the identifier from the output in step S the data management part searches the reference data of the identifier from the reference data storage part in step S. In a case where there are corresponding reference data in the reference data storage part the existence of the data is reported to the output without transmitting the reading request to the pipe A by the child pipe so as to write the actual data of the identifier to the output based on the reference data in step S.

In the second embodiment of the present invention the input does not receive the same reading request twice. Therefore the input may correspond to only the reading request from the pipe A and perform the same process as the single output process.

Next a case where the request management table is used in the second embodiment of the present invention is discussed with reference to .

In an example shown in the output and the input are connected to the pipe A and the output is connected to the child pipe

Information indicating whether the reading request is transmitted from the pipe A to the input is stored in the request management table for every identifier.

In the request management table shown in the reading request of the data corresponding to the identifier is already transmitted to the input . The reading request of the data corresponding to the identifier through the identifier is not transmitted to the input yet.

When the reading request of the data including the identifier is transmitted from the output to the pipe A in step S the pipe A refers to the request management table by the data management part so as to determine whether the reading request of the data corresponding to the identifier has been transmitted to the input in step S.

In a case where the reading request has not been transmitted to the request management table the pipe A transmits the reading request to the input in step S. The pipe A renews the request management table so as to show that the reading request of the data to the identifier is transmitted.

Processes from step S to step S are processes for writing data corresponding to the identifier to the output after the reading request is transmitted to the input and the same as the processes from step S to step S in . Therefore explanation of the processes from step S to step S is omitted.

Next a case where the reading request including the identifier is transmitted from the output to the child pipe is discussed.

When the reading request is transmitted from the output to the child pipe in step S the child pipe reports receipt of the reading request to the pipe A in step S. The pipe A receiving this report refers to the request management table and determines whether the reading request of the data of the identifier has been transmitted to the input .

For example in the request management table shown in the reading request of the data of the identifier is already transmitted to the input . Accordingly the pipe A notifies the child pipe that the reading request is already transmitted to the input without transmitting the reading request to the input in step S.

The child pipe receiving the notification refers to the reference storage part in step S. The child pipe writes the actual data of the identifier based on the reference data to the output in step S.

Thus by using the request management table the pipe A can determine whether the reading request received by the pipe A and the child pipe is transmitted to the input . Accordingly the pipe A can transmit only the reading request not transmitted to the input to the input .

Because of this the input does not receive the same request twice and therefore may write the data requested when the reading request is received from the pipe A. In other words the input may perform the same operations as the single output process.

In addition by using the request management table for example before writing data from the input to the pipe A is completed even if the child pipe receives the reading request of the data of the same identifier it is possible to determine whether the reading request has been transmitted to the input .

As discussed above according to the second embodiment of the present invention it is possible to reflect the reading request from the output side to the input side and improve the process speed. Furthermore according to the second embodiment of the present invention it is possible to prevent from overlapping with the filter of the input side of the pipe and performing the reading request of the data. Hence it is possible to perform control of the filter in the multiple output process as well as the single output process.

Although the invention has been described with respect to specific embodiment for a complete and clear disclosure the appended claims are not to be thus limited but are to be construed as embodying all modifications and alternative constructions that may occur to one skilled in the art that fairly fall within the basic teachings herein set forth.

This patent application is based on Japanese Priority Patent Application No. 2007 156668 filed on Jun. 13 2007 the entire contents of which are hereby incorporated herein by reference.

