---

title: Image processing apparatus
abstract: An image processing apparatus includes an input unit configured to obtain image data and to perform an input process on the image data to produce input image data, an input filter configured to control the input process performed by the input unit, an output unit configured to perform an output process on processed image data, an output filter configured to control the output process performed by the output unit, a process filter connecting between the input filter and the output filter to control processing of the input image data, and another output filter configured to control an output process for storing given image data and conditions concerning outputting of the given image data in a storage unit. The other output filter is coupled to one of the input filter and the process filter in response to receiving an instruction to store the given image data.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08189223&OS=08189223&RS=08189223
owner: Ricoh Company, Ltd.
number: 08189223
owner_city: Tokyo
owner_country: JP
publication_date: 20081022
---
In recent years image processing apparatus such as multifunction devices that manage the functions of a printer a copying machine a scanner and a fax machine in one housing generally incorporate a CPU similar to a computer and their functions are realized by controlling applications.

For example an image forming device described in Japanese Patent No. 3679349 Patent Document 1 includes functions used in common by applications as a platform. The applications can be implemented by using an API Application Programming Interface of this platform. According to this image forming device with the commonly used functions provided as a platform redundant implementation of functions in the applications can be avoided which improves development efficiency of the applications as a whole.

With the related art structures however the development efficiency of the applications is sometimes not improved as much as expected if the granularity of the functions or the interface provided by this platform is not appropriately designed.

If this granularity is too high the API is called too often even though the application provides merely a simple service. As a result the source code becomes complicated.

If the granularity is too low on the other hand the platform is required to be modified internally when an application providing a partly modified service is required to be implemented which leads to an increase of development steps. In particular when modules in the platform depend largely on each other not only is a new function required to be added to the platform but an existing part may also require modification. Thus the development process becomes more complicated.

In the case of implementing an existing application with a partly modified service for example an input process of an image it is impossible to call the unmodified part of the application for the unmodified function. Therefore a new application is required to be implemented by writing new source code.

It is an object of at least one embodiment of the invention to provide an image processing apparatus which can simplify customization extension and the like of the functions.

According to one aspect of the invention an image processing apparatus includes an input unit configured to obtain image data and to perform an input process on the image data to produce input image data an input filter configured to control the input process performed by the input unit an output unit configured to perform an output process on processed image data an output filter configured to control the output process performed by the output unit a process filter connecting between the input filter and the output filter to control processing of the input image data and another output filter configured to control an output process for storing given image data and conditions concerning outputting of the given image data in a storage unit. The other output filter is coupled to one of the input filter and the process filter in response to receiving an instruction to store the given image data.

According to another aspect of the invention an image processing apparatus includes an input unit configured to obtain image data and to perform an input process on the image data to produce an input image data an input filter configured to control the input process performed by the input unit an output unit configured to perform an output process on processed image data to produce output image data an output filter configured to control the output process performed by the output unit a process filter connecting between the input filter and the output filter to control processing of the input image data to produce the processed image data and another input filter configured to control an input process for reading out image data stored in a storage unit storing the image data and conditions concerning outputting of the image data. The other input filter is coupled to one of the process filter and the output filter in response to receiving an instruction to read the image data stored in the storage unit.

According to another aspect of the invention an image processing apparatus includes an input unit configured to obtain image data and to perform an input process on the image data to produce an input image data an input filter configured to control the input process performed by the input unit an output unit configured to perform an output process on processed image data to produce output image data an output filter configured to control the output process performed by the output unit a process filter connecting between the input filter and the output filter to control processing of the input image data to produce the processed image data another output filter configured to control an output process for storing given image data and conditions concerning outputting of the given image data in a storage unit and another input filter configured to control an input process for reading out the image data stored in the storage unit. The other output filter is coupled to one of the input filter and the process filter in response to receiving an instruction to store the given image data. The other input filter is coupled to one of the process filter and the output filter in response to receiving an instruction to read the image data stored in the storage unit.

According to at least one embodiment of the invention customization and enhancement of the functions can be simplified and stored image data can be easily re outputted.

The invention employs a software architecture based on an idea called pipes filters in the image processing apparatus thereby the customization enhancement and the like of the functions are simplified. Moreover the invention easily realizes a re output of stored image data.

Hereinafter the idea of pipes filters employed in the image processing apparatus of the invention is described prior to describing the embodiments of the invention. is a diagram showing the idea of pipes filters. P shown in denotes a pipe and F denotes a filter.

The filter is a program which applies a predetermined process to inputted data and outputs a process result. The pipe is a unit which connects the filters. The pipe temporarily holds the process result outputted from the filter connected on an input side of the pipe and then transfers the data to the filter connected on an output side of the pipe. In this manner according to the idea of pipes filters the processes of the filters can be continuous through the pipes.

In the invention the predetermined processes performed by the filters are considered to apply a predetermined conversion to the inputted data. That is each function realized by the image processing apparatus is considered to be continuous conversion processes applied to a document input data in the image processing apparatus of this embodiment. Each function of the image processing apparatus is thought to include input processing and output of the document which is data. In this embodiment each of the input process processing and output process is considered to be a conversion process and a software component which realizes one conversion process is a filter.

In the invention a filter which controls a data input process is called an input filter a filter which controls data processing is called a processing filter and a filter which controls a data output process is called an output filter. Each of these filters is an independent program without dependence among them. Therefore each filter can be independently added installed or deleted uninstalled as a filter unit in the image processing apparatus.

Hereinafter an image processing apparatus of Embodiment 1 of the invention is described with reference to the drawings.

Software realizing the functions of the image processing apparatus has a hierarchical structure including a user interface layer a control layer an application logic layer a device service layer and a device layer . The hierarchical relationship of these layers is based on the relationship of calling between the layers. That is an upper layer calls a lower layer in the drawing.

When a user sends an instruction for the execution of various functions by the user interface layer in the image processing apparatus the user interface layer calls the control layer and controls the application logic layer based on this execution instruction. The application logic layer executes an application which realizes the requested function based on the instruction from the control layer . Based on this execution result the device service layer and the device layer control a hardware resource of the image processing apparatus . In this manner the image processing apparatus obtains an output result corresponding to the function that the user interface layer has received.

The user interface layer incorporates for example a local UI user interface unit to receive an execution instruction to realize various functions of the image processing apparatus . The various functions here are a copying function a printing function a scanning function a facsimile function and the like. The local UI unit may be provided for example in an operating unit not shown where processes executed in the image processing apparatus are operated. This operating unit may be realized by an operations panel or the like having a display area. In the user interface layer the execution instruction received in the local UI unit is transferred to the control layer .

The control layer incorporates functions for controlling the processes to realize each function of the image processing apparatus . In specific terms execution of each filter in the application logic layer is controlled in accordance with the requested function. It is to be noted that a function of the image processing apparatus described in the following embodiments is one service unit from a request input to a final output that the image processing apparatus provides to the user and software wise is the same as an application which provides one service unit.

The application logic layer incorporates various filters as a component group which realizes a part of the functions provided in the image processing apparatus . In the application logic layer one function is realized by using plural filters in combination with control of the control layer . The application logic layer in this embodiment incorporates an input filter a process filter an output filter and an activity unit . Each filter incorporated in the application logic layer is operated and controlled based on the definition of that filter itself. The activity unit is a component which connects each filter in accordance with the function requested in the user interface layer and controls the execution of each filter.

The device service layer incorporates a lower function used in common by each filter incorporated in the application logic layer . The device service layer of this embodiment incorporates an image pipe . The image pipe which realizes the pipe function transfers an output result of one filter to another filter among the filters incorporated in the application logic layer . Here the image pipe may connect for example the input filter with the process filter or the process filter with the output filter .

The device layer incorporates a driver as a program which controls hardware. The device layer of this embodiment incorporates a scanner unit a plotter unit and the like. Each of these control units controls a device of its name.

The input filter of this embodiment controls an input process of data inputted externally to the image processing apparatus . The input filter includes a read filter an email receive filter a facsimile receive filter a PC document receive filter and the like not shown . The read filter for example controls reading of image data by a scanner and outputs the read image data. The email receive filter receives an email in the image processing apparatus and outputs data included in the received email. The facsimile receive filter controls receiving of facsimiles and outputs the received data. The PC document receive filter receives print data from a client PC or the like that is not shown and outputs the print data. A report filter not shown organizes setting data history data or the like of the image processing apparatus into for example a table format and outputs the organized data.

The process filter of this embodiment applies a predetermined process to the image data inputted from the filter on the input side of the process filter and outputs the process result to the filter on the output side of the process filter . The process here is aggregation expansion shrinking rotation or the like of the inputted data.

The output filter controls an output process of the inputted data and outputs the data outside the image processing apparatus . The output filter includes a print filter a preview filter and the like. The output filter shown in includesan email send filter a facsimile send filter a PC document send filter and the like.

The print filter outputs prints the inputted data to the plotter unit . The preview filter causes an operating unit or the like which is not shown included in the image processing apparatus to preview the inputted data. Further the email send filter attaches the data to an email and sends it. The facsimile send filter sends the inputted data by facsimile. The PC document send filter sends the inputted data to a client PC or the like which is not shown.

An instruction inputted from the local UI unit in the user interface layer is transferred through the control layer to the activity unit . The activity unit controls execution of jobs in the input filter the process filter and the output filter .

In the application logic layer each function of the image processing apparatus is realized by using the filters to in combination. According to this configuration various functions can be realized by using the filters and pipes in combination in the image processing apparatus . In specifics the read filter included in the input filter the process filter and the print filter included in the output filter are to be used in combination to realize a copying function for example.

Hereinafter described is a printing process in the image processing apparatus of this embodiment. is a diagram showing a printing process in the image processing apparatus of Embodiment 1.

The control layer in the image processing apparatus in this embodiment sends a job to the activity unit to control execution of a process of each filter S . The image processing apparatus of this embodiment may generate and send a job to this activity unit when for example power of the image processing apparatus is turned on.

Here when an execution request of a printing process is made in the local UI unit the local UI unit transfers this request to the control layer S . Note that the description in this embodiment is made based on the premise that a copying process as one of the printing processes is selected. In this case an operation to select reading and printing of a paper document is performed in the local UI unit .

The activity unit connects a read filter the process filter and a print filter through the image pipes . Note that a read filter included in the read filter is connected to the process filter in actuality. Subsequently the control layer generates a job S to be executed by the read filter a job S to be executed by the process filter and a job S to be executed by the print filter

When the jobs to be executed by filters and are sent from the control layer the activity unit sends an instruction to each filter to execute the corresponding job. Then the read filter reads the paper document from the scanner unit as an input unit and thus the paper document is read in as image data. These image data are outputted from the read filter and transferred to the process filter through the image pipe .

In the process filter a predetermined process set in advance is applied to these image data and the data are outputted as the processed image data. The processed image data are then transferred to the print filter as one of the output filters . In the print filter the processed image data are outputted from the plotter unit as an output unit to realize a copying process.

In this manner the input filter the process filter and the output filter are each independently controlled and no dependence exists among the filters in this embodiment. Therefore when the functions are customized expanded or the like the appropriate filter is to be customized or the like in this embodiment. According to this embodiment customization expansion or the like of the functions can be simplified.

Embodiment 2 of the invention is hereinafter described. Embodiment 2 of the invention is the same as Embodiment 1 with improvement. Thus components with similar functional structures to those in Embodiment 1 are denoted by the same or similar reference numerals and their descriptions are not repeated.

In Embodiment 2 the case of re outputting image data stored in a hard disk or the like in the image processing apparatus is considered see . Note that re outputting in this embodiment means for example when the image data outputted by the print filter are to be re outputted to read out and re print the image data. When the image data outputted by an email send filter are to be re outputted re outputting means to read out and re send these image data by an email.

Assuming that the image data are to be re outputted the image processing apparatus A is required to retain the image data at the same time as outputting the image data so that they can be re outputted anytime. To be specific the image processing apparatus A is required to retain output conditions such as setting conditions or the like with the image data when the image data are outputted. With the output conditions of the image data being retained the image data can be restored to be re outputted based on the output conditions.

A feature of pipes filters is that various functions can be freely realized by using the filters in combination. In this embodiment an image processing apparatus is provided which can retain image data capable of being re outputted without spoiling the freedom of filter combinations and easily re output the retained image data.

The image processing apparatus A of this embodiment includes a document register filter which relates the image data outputted from the output filter with the output conditions of the image data and stores them and a read out filter which reads out the stored image data together with the output conditions of the image data thereby the stored image data can be easily re outputted.

The image processing apparatus A of this embodiment includes an input filter A a process filter an output filter A and a bibliographic data management service unit in an application logic layer A. Moreover the image processing apparatus A of this embodiment includes a request management unit in a device service layer A and a data management unit in a device layer A.

The image processing apparatus A of this embodiment does not include the control layer included in the image processing apparatus of Embodiment 1. In the image processing apparatus A of this embodiment the role of the control layer included in the image processing apparatus of Embodiment 1 is shared by an activity unit A of the application logic layer A and the request management unit of the device service layer A. That is to say the activity unit A of this embodiment originates instructions for connection between the filters and execution of jobs of the filters while the request management unit generates jobs to be executed by the filters and connects between the filters as instructed by the activity unit A.

The input filter A includes the read out filter in addition to the read filter . The read out filter reads out and outputs image data and output conditions of the image data from a storage device such as a hard disk which is described below. The read out filter is described in detail below.

The output filter A includes the document register filter in addition to the print filter . The document register filter outputs the image data and the output conditions of the image data to a storage device and stores the image data and the output conditions of the image data. The document register filter is described in detail below.

The bibliographic data management service unit controls a data management memory or the like which temporarily holds image data and output conditions when the document register filter stores the image data and the output conditions.

The data management unit in the device layer controls the retaining of data in a storage device such as a hard disk included in the image processing apparatus A.

Hereinafter described is an outline of the image data keeping process and the re output process of the image data in the image processing apparatus A of this embodiment. First the image data keeping process in the image processing apparatus A is described. shows the image data keeping process in the image processing apparatus A of Embodiment 2.

In the image processing apparatus A of this embodiment output conditions of image data are retained with the image data when retaining the image data. As a result the image data reflecting the same conditions as set when outputting the image data can be outputted based on the output conditions when re outputting the image data.

Here the document register filter in the image processing apparatus A of this embodiment is further described.

The document register filter of this embodiment includes an output condition generating unit and a relating unit . The output condition generating unit generates output conditions of the image data to be retained. Generation of the output conditions is described in detail below. The relating unit relates the image data to be stored with the output conditions generated by the output condition generating unit . The relating process is described in detail below.

Receiving this instruction the activity unit A selects a filter to generate a job and connects the filters in accordance with the user s settings to realize the requested function. The activity unit A then transfers this setting information to the request management unit for job generation.

The request management unit generates a job to be executed in each filter based on filter connection settings received from the activity unit A and connects the filters. In the read filter a job to read the image data is generated. In process filters A and B jobs to perform a process required to print the image data are generated. In the print filter a job to print the image data is generated. In the document register filter a job to keep the image data in a storage device HDD which is described below is generated.

In the example shown in the activity unit A sends instructions to connect the print filter to the process filter A through the image pipe and to connect the process filter A to the read filter through the image pipe . The request management unit connects the filters based on these connection instructions.

The activity unit A sends instructions to connect the document register filter to the process filter B through the image pipe and to connect the process filter B to the read filter through the image pipe . The request management unit connects the filters based on these connection instructions.

When the filters are connected by the request management unit the activity unit A then instructs the filters A B and to execute the jobs S S S S and S respectively. At this time the output condition generating unit of the document register filter generates output conditions based on the connecting relationships between the filters and the setting conditions of the filters which are described below.

When the jobs are executed the read filter writes out the read image data to the image pipes and . The process filter A reads out the image data written out to the image pipe applies a predetermined process and writes out the image data to the image pipe . The print filter reads out and prints the processed image data written out to the image pipe

The process filter B reads out the image data from the image pipe processes the image data and writes the processed image data out to the image pipe . When the document register filter reads out the processed image data from the image pipe the image data are read out and related with the output conditions by the relating unit and stored in the storage device HDD.

Note that the process filters A and B apply similar processes to the image data written out from the image pipe and the image data written out from the image pipe respectively. Therefore the image data written out from the image pipe by the print filter and the image data written out from the image pipe by the document register filter are similar. As a result the document register filter can retain the image data to be printed.

With reference to the re output of image data by the image processing apparatus A of this embodiment is described. shows the re output of image data by the image processing apparatus A of Embodiment 2.

In the image processing apparatus A when the local UI unit receives an instruction to re output the image data this instruction is transferred to the activity unit S .

Here the re output instruction transferred to the activity unit A is a re output instruction of the printed image data.

When the output conditions are restored by the read out filter in the image processing apparatus A the activity unit A generates jobs to be executed in the read out filter the process filter A and the print filter in order to execute the process to re print the image data. When the jobs are generated the activity unit A connects the filters based on the relationships between the jobs. Here the read out filter and the process filter A are connected while the process filter A and the print filter are connected.

When the filters A and are connected the activity unit A instructs the filters to execute the jobs S S and S respectively. When the jobs are executed in the filters the read out filter writes the image data out from the storage device HDD to the image pipe . The process filter A reads out the image data from the image pipe applies a process to print the image data and writes the processed image data out to the image pipe . The print filter writes out the image data from the image pipe and prints it.

In this manner the image data stored in the storage device HDD can be re outputted by receiving a re output instruction for the image data.

Each of the filters included in the application logic layer A of this embodiment has a configuration shown in . That is each filter included in the application logic layer A of this embodiment is formed of a setting UI where settings of the filter are performed and a logic unit to control job execution.

In the image processing apparatus A of this embodiment the image data and the output conditions are retained after the settings of document registration are made in the document registration filter . Note that the settings of document registration here mean settings of the output conditions and bibliographic data of the image data.

First a setting process of the output conditions in the image processing apparatus A is described. In the example of the output conditions are to aggregate a document of two pages into one page and print both sides.

In the image processing apparatus A an edit setting of the image data is performed in the process UI Aa as a setting UI of the process filter A by an operating device which is described below S . Note that the process filter A is connected between the read filter and the print filter . In step S the edit condition of 2 in 1 two pages are aggregated into one page is set.

When the edit condition is set in the process UI Aa this edit condition is set in the process logic unit Ab as well S . Then the process logic unit Ab advises the activity logic unit Ab that the edit condition is changed into 2 in 1 S .

The activity logic unit Ab also causes the process filter B to set a similar edit condition based on the edit condition set in the process UI Aa S . Note that the process filter B is connected between the read filter and the document register filter . The process logic unit Bb of the process filter B advises the activity logic unit Ab that the edit condition is changed into 2 in 1 S .

Subsequently a print condition is set in a print UI as a setting UI of the print filter by the operating device S . The print condition set here is to print both sides. When the print condition is set the print UI sets this print condition in a print logic unit as well S . The print logic unit tells the activity logic unit Ab that the print condition is changed into print both sides S .

Here the edit condition and the print condition of the image data that is the output conditions of the image data are set in the image processing apparatus A.

Next setting the bibliographic data of the image data by the document register filter is described. After the output conditions are set the bibliographic data of the image data to be retained with the output conditions can be set in the image processing apparatus A of this embodiment.

When an instruction to set the bibliographic data in a document register UI of the document register filter S is made by the operating device the document register UI sends an instruction to set the bibliographic data to a document register logic unit S . Note that in this embodiment the bibliographic data are set when a file name of the image data is set as the bibliographic data of the image data.

In this manner the bibliographic registration is set in the image processing apparatus A of this embodiment.

When the output conditions and the document registration are set in the image processing apparatus A the activity unit A generates a job to be executed in each filter. The process as shown in is performed after the jobs to be executed in the filters are generated by the activity unit A.

The document register filter of this embodiment performs a process to relate the image data with the output conditions and store them in the storage device HDD through the bibliographic data management service unit . Hereinafter the keeping process of the output conditions is described with reference to . is a sequence diagram showing the keeping process of the output conditions in the image processing apparatus A of Embodiment 2. is a diagram showing settings of the output conditions.

When the document registration is set in the image processing apparatus A the activity logic unit Ab transfers an instruction to keep the output conditions to the document registration logic unit S . Receiving this keeping instruction the output condition generating unit generates a keeping table which is described below and tells the activity logic unit Ab about the table generation S .

The keeping table shown in is generated and stored on a storage device included in the image processing apparatus A. The keeping table contains a file name of the image data which is set in the document register UI a filter name through which filter the image data pass during the interval from input to output in the image processing apparatus A and a filter ID. Note that in the process filter A the print filter and the filter ID are stored however only the process filter A is retained in the keeping table at the point of S in . Moreover the filter name and ID of each filter may be set in advance in the image processing apparatus A. In this embodiment the process filter A has a filter ID of 65 and the print filter has a filter ID of 52.

In the activity logic unit Ab instructs the process logic unit Bb to keep the edit condition set in the process UI Aa S . Receiving this instruction the process logic unit Ba generates an edit condition table which is described below S and stores the edit condition set in the process UI Aa in the bibliographic data management service unit S .

In when the process logic unit Bb is instructed to retain the edit condition S the process logic unit Bb reports to the activity logic unit Ab that the edit condition is retained S .

The activity logic unit Ab sends a registration instruction to the document register logic unit to relate the ID of the process filter A stored in the keeping table and the edit condition stored in the edit condition table S . Here the relating unit of the document register filter relates the process filter A and the edit condition set in the process filter A.

The activity logic unit Ab sends an instruction to the print logic unit to retain the print condition set in the print UI S . Receiving this instruction the print logic unit generates a print condition table which is described below S and retains the print condition set in the print UI in the bibliographic data management service unit S . Note that the filter name and the filter ID of the print filter may be stored in the keeping table .

In when the print logic unit is instructed to retain the print condition S the print logic unit advises the activity logic unit Ab that the print condition is retained S .

The activity logic unit Ab sends a keeping instruction to the document register logic unit to relate the ID of the print filter stored in the keeping table with the print condition stored in the print condition table S and retain them. Here the print filter and the print condition set in the print filter are related.

As described above the edit condition related to the process filter A and the print condition related to the print filter are used as output conditions in this embodiment. Here the document register filter relates the keeping table the edit condition table and the print condition table by using the relating unit .

The document register filter of this embodiment stores and retains the output conditions and the image data with a set file name in the storage device HDD through the bibliographic data management service . In this embodiment therefore the output conditions of the image data can be read out as well when reading out the stored image data. Thus the image data reflecting the conditions set in each filter when outputting the image data can be restored in this embodiment.

Note that the description has been made on the case where the image data are outputted only from the print filter however the invention is not limited to this. In the case where there are plural output filters which output the same image data the paths through which the image data are outputted from the output filters may be stored as output conditions.

For example in a path through which the image data are outputted from the print filter the edit condition set in the process filter A and the print condition set in the print filter are stored as output conditions . In a path through which the image data are outputted from the email send filter the edit condition set in the process filter C and the email send condition set in the email send filter are stored as output conditions .

In this manner output conditions of each path can be retained when there are plural output paths of the image data in the image processing apparatus A of this embodiment.

In this embodiment therefore the image data can be restored based on the output conditions of each path.

Hereinafter described is the restoring of the image data in the image processing apparatus A of this embodiment. In this embodiment the image data start being re outputted when the image data to be re outputted are selected.

First a selecting process of the image data to be re outputted in the image processing apparatus A of this embodiment is described with reference to . In this embodiment the image data selected from the image data stored in the storage device HDD can be re outputted.

When an instruction to select the image data to be re outputted in the read out filter of the read out UI is made through the operating device S the read out UI sends the selection instruction to the read out logic unit

In the image processing apparatus A of this embodiment when the instruction to re output the image data is received through the operating device all the image data stored in the storage device HDD may be displayed. An operations display A shown in listing all the stored image data is displayed on the operating device. Note that a re output instruction button to re output the image data is not visible on the operations display A since the image data to be re outputted have not been selected.

In when the image data to be re outputted are selected a read out logic unit searches for the selected image data in the storage device HDD by using the bibliographic data management service unit S . When the image data are found the read out logic unit compares the image data with the related output conditions S . The read out logic unit determines if the set output conditions include the re output of the image data to be re outputted S .

In the case where the output conditions including the re output of the image data are set in step S the read out logic unit advises the read out UI about it S . The read out UI updates the operations display A of the operating device so that a re output instruction can be made S .

The operations display B shown in indicates that the re output instruction can be made. In the operations display B an image data set is selected as an object to be re outputted. As the image data set can be re outputted in the example shown here the re output instruction button to generate a re output instruction of the image data set is visible. Pressing or touching the re output instruction button on the operations display B starts the re output process of the selected image data set .

With reference to restoring the output conditions of the image data as an object to be re outputted is described. shows another example of a display of the operating device included in the image processing apparatus A of Embodiment 2. is a sequence diagram showing the restoring process of the output conditions in the image processing apparatus A of Embodiment 2.

When the re output instruction for the selected image data is made the operating device of the image processing apparatus A of this embodiment displays an operations display A showing output paths capable of being restored as shown in . The operations display A shows that it is possible to restore a path to re output the image data from the print filter and a path to re output the image data from the email send filter . When the operations display A is displayed on the operating device the image processing apparatus A starts the restoring process of the output conditions shown in .

When the output conditions of the image data to be re outputted are displayed on the operating device the image processing apparatus A instructs the read out UI to expand the output conditions S . The read out UI sends this instruction to the read out logic unit S .

The read out logic unit advises the activity logic unit Ab about receiving the instruction to expand the output conditions S . The activity logic unit Aa restores the output condition of each filter based on the output conditions compared when searching for the image data to be re outputted see S in .

In the activity logic unit Ab restores the edit condition of the process filter A from the output conditions. The activity logic unit Ab once again causes the process logic unit Ab to restore the edit condition related to the filter ID of the process filter A included in the output conditions S . Receiving the instruction to restore the edit condition from the activity logic unit Ab the process logic unit Ab checks the edit condition related to the filter ID of the process filter A stored in the storage device HDD through the data management unit S . Then the process logic unit Ab sets the edit condition checked in the storage device HDD and advises the process UI Aa that the edit condition is changed S .

Subsequently the activity logic unit Ab restores the print condition of the print filter from the output conditions. The activity logic unit Ab causes the print logic unit to restore the print condition related to the filter ID of the print filter included in the output conditions S . Receiving the instruction to restore the print condition from the activity logic unit Ab the print logic unit checks the print condition related to the filter ID of the print filter stored in the storage device HDD through the data management unit S . Then the print logic unit sets the print condition checked in the storage device HDD and advises the print UI that the print condition is changed S .

In the image processing apparatus A of this embodiment the output conditions are restored as described above. When the output condition of each filter is restored in the image processing apparatus A the operations display B shown in is displayed on the operating device. The operations display B displays the edit conditions restored in the process filter A and the print conditions restored in the print filter

When the output conditions are restored and the condition of each filter is set jobs to be executed in the filters are generated by the activity unit A and a re output process of the image data is performed in the image processing apparatus A of this embodiment. The re output process of the image data after the jobs are generated to be executed in the filters is as shown in .

According to this embodiment the output conditions set for each output path of the image data are related to the image data when the image data are retained. Therefore the image data reflecting the output conditions can be re outputted by only reading out the image data to be re outputted and the output conditions related to the image data. According to this embodiment an image processing apparatus can be provided which can maintain image data in a state capable of being re outputted and can easily re output the stored image data without spoiling the freedom of filter combination.

The image processing apparatus A of this embodiment can select the output condition to retain when storing the image data with the output conditions. In this embodiment for example an operations display A shown in may be displayed on the operating device before the keeping process of the output conditions shown in starts. shows an example of the operations display A displayed on the operating device.

The operations display A shows the case where there are two output paths of the image data. One path is a print path where the image data are to be outputted from the print filter and the other path is an email send path where the image data are to be outputted from the email send filter . In the operations display A in this case the user can select to keep both the output conditions of the print path and those of the email send path keep one of these or keep none of these. In the image processing apparatus A the image data can be related and retained with the output conditions selected on the operations display A. Thus the user can retain only the necessary output conditions.

The image processing apparatus A of this embodiment can restore only the selected output conditions from the stored conditions when restoring the output conditions. For example in this embodiment the operations display A shown in may be displayed on the operating device before the restoring process of the output conditions shown in starts. shows another example of an operations display A displayed on the operating device.

The operations display A shows the case where there are two output conditions related to one image data set. One output condition is set in the print path where the image data are to be outputted by the print filter and the other output condition is set in the email send path where the image data are to be outputted by the email send filter . In this embodiment only the output conditions selected on the operations display A can be restored.

Note that when the output conditions to be restored are selected on the operations display A only the data of the selected output condition may be displayed on the operations displays A and B shown in respectively.

Moreover when re outputting the image data through plural paths a judgment by a human can be made whether the image data are to be re outputted through each of the selected paths or not.

When the idea of pipes filters is applied as in the image processing apparatus A of this embodiment filters can be easily installed or uninstalled. Therefore when the image data are to be re outputted there is a possibility that a filter set as an output condition has been uninstalled.

In the image processing apparatus A of this embodiment a determination is made whether all the filters set as the output conditions exist when outputting the image data. is a flowchart describing a process to determine the existence of the filters of Embodiment 2.

Reading out the output conditions set in all the paths requested to re output the image data S the image processing apparatus A determines whether all the filters included in the output conditions of all the paths exist S . When all the filters included in the output conditions in all the paths do not exist NO in step S the output conditions are not restored and the image data are not re outputted.

The image processing apparatus A of this embodiment includes an application management unit not shown where the activity unit and the filters are registered. The application management unit is incorporated in the application logic layer A and manages the activity unit and the filters. The activity unit and the filters are registered in the application management unit when the image processing apparatus A is activated and the registration is deleted from the application management unit when the power of the image processing apparatus A is shut down. In this embodiment therefore the determination can be made whether all the filters included in the output conditions exist by searching the application management unit when activating the image processing apparatus A.

When all the filters included in the output conditions in all the paths are determined to exist in step S the image processing apparatus A performs the restoring process of the output conditions S . The restoring process of the output conditions is performed as described above. In this embodiment the processes of S and S are performed for each output path of the image data S .

In this manner the image data are restored only when the restoration is possible with settings similar to the output conditions of storing the image data. Therefore the output conditions can be restored without mistakes and an improper output such as re outputting the image data with wrong conditions can be prevented.

When the output condition is changed during the re output of the image data in the image processing apparatus A of this embodiment the user can select whether to keep the changed output conditions.

The case where the output condition is changed during the re output is for example the case where a part of the output conditions is canceled while continuing the output. For a specific example for example when a re output of the image data is performed with the output conditions to perform a staple process after printing by the image processing apparatus A the staple process only is temporarily cancelled as the staples run out.

When the output process of the image data starts to be executed in the image processing apparatus A S the image processing apparatus A determines whether there is a change in the output conditions during execution of the process S . The change in the output conditions here means a change of a setting for a filter in a path through which the image data are to be outputted for example. To be specific there are examples such as a change in an edit setting of the process filter A and a change in a print setting in the print filter . When there is a change in the output conditions in step S the image processing apparatus A sets a flag signaling that there is a change in the output conditions S .

Subsequently the image processing apparatus A determines whether the flag of the change in the output conditions is set when storing the image data S . When there is a flag of the change in the output conditions set in step S the image processing apparatus A displays an operations display A on the operating device asking whether to keep the changed output conditions S . shows an example of the operations display A asking whether to keep the changed output conditions.

In when the user selects to keep the changed output conditions on the operations display A in step S the image processing apparatus A retains the changed output conditions.

In step S when the user selects not to keep the changed output conditions the image processing apparatus A deletes the settings set in the filters where the output conditions have been changed and displays a message of deletion on the operations display A of the operating device S .

In this manner when there is a change in the output conditions during the re output process of the image data the user can select whether to keep the changed output conditions in this embodiment. Therefore it is possible to prevent an improper operation cancelling a part of the output conditions by mistake during the re output process of the image data.

In this embodiment even when a part of the restored output conditions cannot be executed when re outputting the image data the re output can be performed by executing the other output conditions.

To be specific a case where a part of the output conditions cannot be executed is for example where staples are not supplied in the image processing apparatus A when a staple process after printing is set as an output condition. In this case the staple process as a part of the output conditions cannot be executed.

In the image processing apparatus A of this embodiment the output conditions can be executed except for the output conditions which cannot be executed. is a flowchart showing an operation of the case when a part of the output conditions cannot be executed in the image processing apparatus A of Embodiment 2.

When the output conditions are restored S the image processing apparatus A determines whether the re output can be executed based on the restored output conditions S . In the case where there is an output condition which cannot be executed in step S the image processing apparatus A sets a flag of impossible execution S . The image processing apparatus A performs the processes of S through S on all the filters of each output path.

Next the image processing apparatus A determines whether a flag signaling that the output condition cannot be executed is set S . When there is a flag in step S the image processing apparatus A displays on the operating device an operations display A as shown in asking a question whether to restore the output condition which cannot presently be executed S . The image processing apparatus A performs the processes of S through S on all the output paths.

In this manner even when a part of the output conditions cannot be executed the other output conditions can be executed to perform a re output in the image processing apparatus A of this embodiment. In the image processing apparatus A of this embodiment it is possible to retain the output condition which cannot be executed. Therefore the output conditions can be retained without a change when the impossible execution problem can be easily solved for example cases where no staples are supplied no printing paper is supplied in a paper tray and the like. In such cases the impossible execution problem can be solved by supplying staples or printing paper.

In the image processing apparatus A of this embodiment the image data before processing by the process filter that is the image data right after the output from the input filter A can be stored as well.

In the image processing apparatus A the activity unit A connects the document register filter in a subsequent stage of the read filter when the image data before processing are set to be retained. The document register filter reads out and stores the image data read by the read filter

At this time the document register filter is required to store only the conditions set in the print filter and the email send filter as the output filters through which the image data are to be outputted. Therefore in the example shown in the document register filter stores in the keeping table A the filter names and filter IDs of the print filter and the email send filter as the output filters through which the image data are to be outputted. The document register filter forms a print condition table not shown set for the print filter and an email send condition table not shown set for the email send filter which are related to the image data and stored.

In this embodiment when re outputting the image data stored before being processed either of the read out filter and the output filter may be connected without interposing the process filter . For example the email send filter is connected in a subsequent stage of the read out filter . In this case the image data read out from the storage device HDD by the read out filter may be outputted from the output filter .

Further the procedures to realize the various functions in the embodiments may be stored in a memory medium as a program which can be read and executed by computers.

The image processing apparatus A for example includes a CPU a hard disk a memory an operating unit a scanner unit a communicator unit a memory medium read in unit and a plotter unit . The CPU is an arithmetic processing unit which performs operations and processes executed in the image processing apparatus A. The hard disk HDD is a storage device which stores data which are an application operating in the image processing apparatus A data formed by this application and the like. The storage device described in this embodiment may be the hard disk . The memory holds various set values related to the image processing apparatus A operating results of the CPU and the like.

The operating unit is an operations panel or the like having a display function at which operations display of operating states and the like of the image processing apparatus A are performed. Note that the operating device of this embodiment may be the operating unit .

The scanner unit which reads in a document to form image data is formed of a scanner engine an engine controller and the like. The communicator unit is a network control unit or the like through which the image processing apparatus A communicates with external devices. The memory medium read in unit reads in data programs and the like stored in various memory media which is a floppy registered trademark disk drive for example. The plotter is formed of a plotter engine an engine controller and the like which prints out the image data.

The memory medium stores the image processing program which realizes various functions of this embodiment. This image processing program is read in by the memory medium read in unit and executed by the CPU . The memory medium may be for example a floppy registered trademark disk a CD ROM Compact Disk Read Only Memory or any medium which can be read by the image processing apparatus A. Further the image processing program may be received by the communicator unit through a network and stored in the hard disk or the like.

Although the invention has been described with respect to specific embodiments for a complete and clear disclosure the appended claims are not to be thus limited but are to be construed as embodying all modifications and alternative constructions that may occur to one skilled in the art that fairly fall within the basic teachings herein set forth.

This patent application is based on Japanese Priority Patent Application No. 2007 276729 filed on Oct. 24 2007 the entire contents of which are hereby incorporated herein by reference.

