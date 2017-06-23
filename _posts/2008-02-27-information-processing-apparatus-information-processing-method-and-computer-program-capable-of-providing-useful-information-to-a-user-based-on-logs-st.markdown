---

title: Information processing apparatus, information processing method, and computer program capable of providing useful information to a user based on logs stored in a printing system and improving the usability of each user who operates a printing system
abstract: A printing system includes a storage unit (HD) adapted to store a print logs relating to each of a plurality of print data having been printed, the print log including relevant information relating to the print data; a reception unit adapted to receive relevant information relating to print data to be printed; a search unit adapted to search a print log including the relevant information received by the reception unit from the print logs stored in the storage unit; and a display unit adapted to display information indicating a print apparatus that has printed print data corresponding to the print log found by the search unit, which is extracted from the relevant information included in the print log found by the search unit.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08570551&OS=08570551&RS=08570551
owner: Canon Kabushiki Kaisha
number: 08570551
owner_city: Tokyo
owner_country: JP
publication_date: 20080227
---
The present invention relates to a printing system including an information processing apparatus a method for controlling the information processing apparatus and a computer program.

A recent advanced printing system includes various office automation OA devices such as personal computers and image forming apparatuses which can communicate with each other via a network. In general the printing system provides an environment allowing a plurality of users to commonly use an image forming apparatus.

If a print job is input to a printing system that performs printing the printing system records various logs according to print results. For example the printing system records detailed print setting information as well as fundamental information e.g. user name date time and file name of print data .

The usage of a recorded log is not limited to confirmation of a history of print processing. For example a log is usable for re inputting a print job and usable for accounting.

As discussed in Japanese Patent Application Laid Open No. 2004 118243 to satisfy a requirement of enhancing the security a printing system records a printed image which is appropriately reduced or compressed and if an accident leakage of information occurs traces the leaked information based on the recorded image.

As discussed in Japanese Patent Application Laid Open No. 2006 159565 a printing system uses a log to restrict an operation of each user according to an environment. For example a printing system can restrict the number of color printing sheets during a limited period of time.

The usage of a log in a conventional printing system is mostly limited to the trace of information or restriction of usable functions to improve the usability of an administrator who manages the printing system.

However the above described conventional printing systems do not utilize log s to improve the usability of each user who operates a printing system to execute print processing.

In general the act is useful if many users conduct or follow in similar ways. For example in an environment including two or more printing apparatuses connected to a network users tend to operate a specific printing apparatus having highly advanced functions.

A log stored in a printing system is a history of user s behavior and can be used in a detailed analysis to check other user s act and intent in printing a document.

Exemplary embodiments of the present invention are directed to a printing system capable of providing useful information to a user based on logs stored in a printing system and improving the usability of each user who operates a printing system.

According to an aspect of the present invention a printing system includes a storage unit adapted to store print logs relating to each of a plurality of print data that have been printed the print log including relevant information relating to the print data a reception unit adapted to receive relevant information relating to print data to be printed a search unit adapted to find a print log including the relevant information received by the reception unit from the print logs stored in the storage unit and a display unit adapted to display information indicating a print apparatus that has printed print data corresponding to the print log found by the search unit which is extracted from the relevant information included in the print log found by the search unit.

Further features and aspects of the present invention will become apparent from the following detailed description of exemplary embodiments with reference to the attached drawings.

The following description of exemplary embodiments is illustrative in nature and is in no way intended to limit the invention its application or uses. It is noted that throughout the specification similar reference numerals and letters refer to similar items in the following figures and thus once an item is described in one figure it may not be discussed for following figures. Exemplary embodiments will be described in detail below with reference to the drawings.

A print server a data storage two client personal computers PCs three color multifunction peripherals MFPs and two monochrome multifunction peripherals MFPs can communicate with each other via a local area network LAN a wide area network WAN Internet or a wireless network.

The print server the data storage and the client PCs are information processing apparatuses e.g. personal computers and workstations .

The print server receives print jobs from the client PCs and the MFPs and . The print server transmits print information of a received print job to a designated printing apparatus. The printing apparatus is any type of image forming apparatus having a print function such as color MFP or monochrome MFP illustrated in or a Single Function Peripheral SFP not illustrated. According to an exemplary embodiment of the present invention the print server analyzes logs stored in the data storage and transmits later described recommendable information to the client PC or the MFP or .

The data storage stores logs generated by the print server . The log is information recording a print job having been previously print processed and is information identifying a print object file.

The client PC generates a print job and instructs the print server to execute print processing. The client PC can monitor and control as an auxiliary the devices and jobs managed in the print server .

The color MFPs and the monochrome MFPs are image forming apparatuses having various functions e.g. scan print and copy functions . A user can select a desired MFP according to a requested print job because the color MFPs and the monochrome MFPs are different in processing speed and cost.

The printing system according to an exemplary embodiment of the present invention is a mere example and can be modified in various ways. For example the print server may include functions of the data storage . The image forming apparatus e.g. color MFP or monochrome MFP or the client PC may include functions of the print server .

According to an exemplary embodiment a print job is transmitted to a printing apparatus via the print server . However the client PC can directly transmit a print job to a printing apparatus. In this case the print server as a dedicated server analyzes logs stored in the data storage and sends later described recommendable information to the client PC or the MFP .

An exposure control unit including a laser and a polygonal scanner emits a laser beam modulated based on an image signal i.e. an electric signal converted by the image sensor unit and subjected to later described predetermined image processing toward a photosensitive drum .

A primary charging unit a developing unit a transfer charging unit a pre exposure lamp and a cleaning unit are disposed around the photosensitive drum . In an image forming unit a motor not illustrated rotates the photosensitive drum in a predetermined direction indicated by an arrow . The primary charging unit charges the photosensitive drum to have a desired electric potential.

The exposure control unit emits the laser beam onto the photosensitive drum to form an electrostatic latent image. The developing unit develops the electrostatic latent image formed on the photosensitive drum so that the electrostatic latent image can be visualized as a toner image.

Pickup rollers and successively feed recording papers from a right cassette deck a left cassette deck an upper deck cassette or a lower deck cassette . Paper feeding rollers and convey recording papers to the main body . A pair of resist rollers sends a recording paper to a transfer belt . The transfer charging unit transfers the visualized toner image onto a recording paper.

The cleaning unit removes collects the toner remaining on the photosensitive drum after the toner image is transferred onto a recording paper. The pre exposure lamp erases residual electric charge on the photosensitive drum . A separation charging unit separates the recording paper from the photosensitive drum . The transfer belt conveys the recording paper to a fixing unit . The fixing unit fixes the toner image on the recording paper under applied heat and pressure. A pair of paper discharge rollers discharges a recording paper out of the main body .

The main body includes a deck having a storage capacity for example of 4000 recording papers. The deck includes a lifter that can move upward according to an amount of stored recording papers so that a topmost recording paper constantly contacts a pickup roller . A pair of paper feeding rollers feeds a recording paper into the main body . The main body includes a multi manual feed tray having a storage capacity of 100 recording papers.

In a paper discharge flapper switches the paper conveyance path between a conveyance path and a discharge path . A reversing path reverses a recording paper fed by the paper discharge rollers . A lower conveyance path guides the reversed recording paper to a paper re feeding path .

A pair of paper feeding rollers guides a recording paper from the left cassette deck to the paper re feeding path . A pair of paper re feeding rollers re feeds a recording paper to the image forming unit . A pair of discharge rollers disposed in the vicinity of the paper discharge flapper discharges a recording paper out of the main body when the paper discharge flapper guides the recording paper toward the discharge path .

In a two sided recording two sided copy operation the paper discharge flapper moves upward and guides a copy processed recording paper to the paper re feeding path via the conveyance path the reversing path and the lower conveyance path . In this case a pair of reversing rollers pulls a recording paper sandwiched there between toward the reversing path so that a recording paper including its trailing edge can be wholly extracted from the conveyance path . Then the reversing rollers rotate in the opposite directions to send the recording paper to the conveyance path .

When a reversed recording paper is discharged from the main body the paper discharge flapper moves upward and the reversing rollers stop a recording paper moving toward the reversing path at an intermediate position so that a trailing edge of the paper remains on the conveyance path . Then the reversing rollers rotate in the opposite directions to send the reversed recording paper to the discharge rollers .

A paper discharge processing apparatus has a function of aligning and binding recording papers discharged from the main body . A processing tray receives recording papers successively discharged from the main body . If a predetermined amount of image forming operation is completed a bundle of recording papers is stapled or stitched and output to a paper discharge tray or .

A motor not illustrated moves the paper discharge tray in the up and down direction. Prior to commencement of an image forming operation the paper discharge tray is positioned at a height corresponding to the processing tray . Then the position of the paper discharge tray is gradually lowered so that the topmost discharged recording paper can be constantly positioned at the height corresponding to the processing tray .

Furthermore a tray lower limit sensor not illustrated detects a lower limit position of the paper discharge tray . The paper discharge tray reaches the lower limit position when the paper discharge tray stores approximately 2000 recording papers. A paper tray stores break papers e.g. index sheets to be inserted between discharged recording papers. A Z folding machine folds the discharged recording papers in a Z shape.

A bookbinding machine folds each part of discharged recording papers at their centers and staples or stitches the papers into a book shape. The bookbinding processed papers i.e. bundle of bound papers are discharged to a discharge tray . According to the example illustrated in the image forming processing is an electrophotographic type. However the image forming processing may be an inkjet type or any other type.

The MFP includes a built in memory e.g. a hard disk which can store data of a plurality of jobs. The MFP is an image forming apparatus having a copy function for causing a printer unit to print image data acquired by a scanner via the memory. Furthermore the MFP has a print function for causing the printer unit to process print data output from an external apparatus e.g. a computer .

The MFP is a full color type or a monochrome type although both full color devices and monochrome devices are fundamentally similar in configuration except for color image processing and processed data. The following exemplary embodiments are described based on a full color device and if necessary may include an explanation for a monochrome device.

An image forming apparatus according to an exemplary embodiment of the present invention is a multi functional image forming apparatus that is capable of performing a plurality of functions or a unifunctional image forming apparatus capable of performing a single print function.

In an input image processing unit reads an image of an original i.e. a paper document and performs image processing on the read image data. A facsimile FAX unit performs transmission reception of images via a telephone line. A network interface card NIC unit performs transmission reception of image data and apparatus information via a network.

A dedicated interface unit communicates with an external apparatus to exchange image data or other information. A Universal Serial Bus interface USB I F unit transmits receives image data to from a USB memory i.e. a removable media or a USB device. An MFP control unit can temporarily store image data according to an application installed on the MFP or can determine a route of the image data.

A document management unit includes a memory e.g. hard disk which can store various image data. For example a control unit of the image forming apparatus CPU of the MFP control unit stores image data input via the input image processing unit the NIC unit the dedicated I F unit and the USB I F unit into the hard disk.

The document management unit manages two or more storage areas of a hard disk which are partitioned for each job type or each user. Each of two or more storage areas is referred to as box. The box is for example a user box a system box or a FAX box differentiated according to the type of a stored job. A box number e.g. 1st 2nd . . . 99th is allocated to each user box so that the access right of each user can be managed.

Furthermore the document management unit reads necessary image data from the hard disk transfers the read data to a printer unit i.e. an output unit and controls the printer unit that performs print processing.

Furthermore in response to an instruction from an operator the document management unit transfers the image data read out of the hard disk to an external apparatus e.g. a computer or other image forming apparatus .

The compression expansion unit compresses image data if necessary when the image data is stored in the document management unit . The compression expansion unit expands decompresses image data into the original image data in the process of reading the compressed image data out of the document management unit . The data transmitted via a network include compression data e.g. Joint Photographic Experts Group JPEG Joint Bi level Image Experts Group JBIG and ZIP . Therefore the compression expansion unit expands decompresses input data if the MFP receives compressed data.

Furthermore a resource management unit stores various parameter tables e.g. font color profile and gamma tables which can be commonly used and if necessary invokes a necessary table. The resource management unit can store new parameter tables and correct update the stored tables.

The MFP control unit controls a Raster Image Processor RIP unit that performs Raster Image Processor processing on PDL data and if necessary controls an output image processing unit that performs image processing for a print image to be printed. Furthermore the MFP control unit can control the document management unit to store intermediate data or print ready data i.e. bitmap data for a print or compressed data thereof of the generated image data if necessary.

The image processed print data is sent to the printer unit that performs image formation processing. The printed sheets output from the printer unit are sent to a post processing unit that performs processing for sorting and or finishing the sheets.

The MFP control unit has a role of smoothly processing a job and can switch a job flow path according to a usage of the MFP. Although it is generally known that image data can be stored as intermediate data if necessary the following examples do not express any access except that the document management unit is a start point or an end point. Furthermore to simply express respective job flows the following examples do not include the processing of the compression expansion unit the post processing unit and the MFP control unit .

J Box scan function input image processing unit output image processing unit document management unit

Other example job flows may include various functions e.g. E mail service and Web server functions which are adequately combined.

The box scan function the box print function the box reception function and the box transmission function are processing functions of the MFP that performs writing reading of data using the document management unit . More specifically the MFP writes reads a file or image data into from a box in the document management unit for each job or each user and prints the read image data.

An operation unit enables a user to select one of the above described various job flows and functions and instruct various operations. The operation unit includes a display unit having a higher resolution and capable of displaying a preview image of image data stored in the document management unit and allowing a user to confirm the image before starting a print operation.

In a central processing unit CPU executes control and calculation processing according to a program loaded from a random access memory RAM . The RAM provides a work area into which a program and data can be loaded for each processing and executed. A read only memory ROM stores a system control program and font data. A keyboard control unit KBC receives data entered via a keyboard KB and transmits the received data to the CPU . A printer control unit PRTC controls a printer PRT . The printer is for example a multifunction peripheral MFP a laser beam printer or an inkjet printer.

A display control unit controls a display unit . A disk control unit DKC controls transmission of data. An external storage device is for example a floppy disk FD a hard disk HD a compact disk CDROM or a digital versatile disk DVDROM . The external storage device stores programs and data. The program stored in the external storage device can be referred to or loaded into the RAM if necessary when the CPU executes this program. The data transfer between the above described units can be performed via a system bus .

The information processing apparatus performs operations when the CPU executes a basic input output I O program and an operating system OS . The external storage device or the ROM of the print server or the client PC stores programs of later described flowcharts that the CPU can execute.

The ROM stores the basic I O program and the HD stores the OS. The basic I O program includes an initial program loading IPL function for loading the OS from the HD into the RAM to automatically start the operation of the OS in response to a turning on operation of a user terminal i.e. information processing apparatus .

At step the client PC opens a file i.e. an object to be printed . More specifically predetermined application software operating on the client PC opens a file. The file is for example a document file an image file or a Portable Document Format PDF file.

At step the client PC executes a printer driver in response to a user s instruction. If the printer driver is activated in step the display unit of the client PC displays an example screen illustrated in .

A printer driver setting screen is a screen displayed when an operator transmits print data to a printing apparatus e.g. MFP . In general an operator can select this screen from a print menu of a print application.

A PRINTER NAME pull down list box enables an operator to select a printing apparatus to be used. If an operator selects a desired printing apparatus a STATE field displays a state of the selected printing apparatus a TYPE field displays a type of the selected printer driver a PLACE field displays a setup location of the selected printing apparatus and a COMMENT field displays a comment from an administrator of the selected printing apparatus.

An OUTPUT TO FILE check box enables an operator to output print data to a file without performing printing in a printing apparatus. A PRINT RANGE field includes radio buttons of WHOLE PRESENT PAGE SELECTED PORTION and PAGE DESIGNATION which can be selected by an operator to designate a desirable print range.

If an operator selects the PAGE DESIGNATION radio button the operator can input page number s in an edit box. A PRINT OBJECT pull down list box enables an operator to select an attribute of a document i.e. a print object . A PRINT DESIGNATION pull down list box enables an operator to designate printing of all pages or printing of odd or even page s . A NUMBER OF COPIES field includes a TOTAL COPY NUMBER spin box that enables an operator to input a desired number of copies. The NUMBER OF COPIES field includes a PRINT BY UNIT check box that enables an operator to print a plurality of pages by unit.

An ENLARGE REDUCE field includes a NUMBER OF PAGES PER SHEET pull down list box that enables an operator to designate an N up printing i.e. a print layout of two or more pages on a printing surface . The ENLARGE REDUCE field includes a DESIGNATION OF PAPER SIZE pull down list box that enables an operator to select a desirable paper size relative to the size of an original.

At step the printer driver selects a printing apparatus i.e. a sending destination of the print job . More specifically a user selects a desired printing apparatus via the PRINTER NAME pull down list box illustrated in . The printer driver designates a printing apparatus selected by a user as sending destination of a print job.

At step the printer driver determines print settings of a file i.e. print object . More specifically if a user clicks on a PROPERTY button illustrated in the printer driver causes the client PC to display a print setting screen illustrated in . The print setting screen illustrated in enables a user to select a desired print layout.

The print layout includes settings of output sheet size printing orientation selection between color or monochrome two sided printing or one sided printing and execution of post processing e.g. staple processing . If a user selects a print layout from the screen illustrated in and clicks on an OK button the printer driver determines the settings selected by a user as finalized print layout. The print setting screen illustrated in includes the following setting items.

A FAVORITE pull down list box enables a user to select an optimum page setting among predetermined page setting modes. Two buttons positioned at the left side enable a user to add and edit a favorite selection item.

If a user clicks on a SETTING CONFIRMATION button the setting contents on the print setting screen can be displayed as a list. A page image displayed above the SETTING CONFIRMATION button reflects the print setting contents having been set.

An OUTPUT METHOD pull down list box enables a user to select a desirable output method. More specifically the user can designate ordinary printing or secure printing performed by the printing apparatus e.g. MFP . Furthermore the user can determine whether to store print data in a hard disk of the printing apparatus and whether to execute editing and preview on the printing apparatus.

An ORIGINAL SIZE pull down list box enables a user to select the size of an original i.e. print object . An OUTPUT SHEET SIZE pull down list box enables a user to select the size of an output paper of a printing apparatus. A NUMBER OF COPIES spin box enables a user to input a desirable number of copies.

An ORIENTATION OF PRINT radio button enables a user to select an orientation of a printing paper output from a printing apparatus between PORTRAIT and LANDSCAPE. A PAGE LAYOUT pull down list box enables a user to set N up printing. If a DESIGNATE MAGNIFICATION check box is in a selected state a user can input a desirable enlargement reduction value in a MAGNIFICATION spin box .

If a STAMP check box is in a selected state a user can select a desirable type of stamp displayed in a pull down list box. A STAMP EDITING button enables a user to add a type of stamp and edit the stamp. A USER DEFINED PAPER button enables a user to define a user defined paper. A PAGE OPTION button enables a user to set page options in more details. A RESTORE DEFAULT button enables a user to restore default setting values.

If a user clicks on an OK button after completing print settings of the printer driver the print attributes can be reflected to actual printing. A CANCEL button enables a user to cancel settings on the print setting screen. A HELP button enables a user to display a help screen with respect to print settings.

If a user clicks on an OK button of the screen illustrated in after completing selection of a printing apparatus and determination of a print layout at step the client PC transmits a print job to the print server .

At step the print server receives a print job from the client PC and spools the received job on a spooler.

At step the print server refers to the received print job and identifies a designated printing apparatus. Then the print server interrogates the identified printing apparatus about a present status. If the printing apparatus can accept an entry of a new job the print server transmits a print job to the printing apparatus. If the printing apparatus cannot accept an entry of a print job the print server maintains a spool state.

At step the printing apparatus spools the received print job on its spooler until the printing apparatus can start print processing of this job.

At step the printing apparatus executes the print job. At step the printing apparatus transmits a print result to the print server .

At step the print server transmits the print result received from the printing apparatus to the client PC .

At step the client PC receives the print result from the print server and terminates the processing of this routine.

At step the MFP accepts a log in request from a user. At step the MFP selects a print object file from a box thereof. More specifically the MFP selects a file according to instructions entered by a user via screens illustrated in .

In an exemplary embodiment boxes may be present in a storage device accessible via a network or a hard disk of another MFP connected via a network. In this case the screens illustrated in display box information of other MFP.

The screen illustrated in includes a document list indicating files stored in the box and an arrow key that enables a user to select a print object file from the document list . A user can also select a print object file by touching a desired document name on a touch panel. A PRINT button enables a user to instruct a print of a file selected from the document list .

A MOVE COPY button enables a user to move or copy a file selected from the document list . A DETAILED INFORMATION button enables a user to display detailed information of a document selected from the document list . A READ ORIGINAL button enables a user to scan a paper original with the scanner and store acquired data in a box.

A DELETE button enables a user to delete a document selected from the document list . A SEND button enables a user to transmit a document selected from the document list for example as an attached file of an electronic mail. An EDIT MENU button enables a user to edit attributes of a selected document i.e. a highlighted document in the document list . A CLOSE button enables a user to terminate a box operation.

If a user selects a print object file and inputs print settings via the screens illustrated in the processing flow proceeds to step .

If the printer unit completes the print processing the processing flow proceeds to step . At step the MFP transmits a print result to the print server .

At step the print server executes log generation processing based on the print result received from the MFP.

At step the MFP displays the print result on the touch panel and terminates the processing of this routine.

The print server generates a log of a print job in the following manner. According to an exemplary embodiment if the printing apparatus completes print processing the print server generates a log relating to the print job. Then the print server transmits the generated log to the data storage and manages the log.

The items are roughly classified into two groups i.e. items acquired from an apparatus e.g. client PC or the MFP which requests print processing and items generated from the print server .

The items acquired from an apparatus that requests print processing include user ID storage place file name type of file output destination printer and layout . The items generated from the print server include job ID job input date time security level keyword and relevant job ID .

The user ID is identification information capable of identifying a user who performs print processing. For example a user inputs a user ID in a log in process of the client PC if the user operates the client PC that processes a print request. Similarly a user inputs a user ID in a log in process of the MFP if the user operates the MFP that performs print processing. The user ID is for example numerical data or a character string that can identify a user.

The storage place indicates a place where a print object file is stored. For example the storage place is path information of a storage area if a print object file is stored in a predetermined storage area of the client PC . For example if a web page on Internet is a print object the storage place is URL of the web page web site .

The file name is a file name of a print object file. The type of file is a format of a print object file. For example an extension of file name indicates a type of file that can be identified by the print server . The type of file is for example word processor data graphic data or text data. The output destination printer is identification information capable of identifying a printing apparatus that executes print processing.

The output destination printer is for example apparatus name IP address or Media Access Control MAC address that can identify a printing apparatus. The layout indicates print setting contents designated by a user. For example the layout includes information relating to paper size two sided printing staple processing etc.

The job ID is identification information of a print job subjected to print processing and is a unique ID allocated to each job so that the print server can identify a log. The job input date time indicates date time when the print job has been input from client PC to the print server . If print processing for a file stored in a box of the MFP is performed the job input date time is time when the print server receives a completion notice of the print processing. The print server includes a timer not illustrated that provides date time information.

The security level is information indicating a security level of a print object file. The security level of a file can be determined according to predetermined rule s . For example a print object file has a lower security level if the storage place is a web page on Internet i.e. a place where everyone can access . On the other hand a print object file has a higher security level if the storage place is a local disk in the client PC . The security level can be changed according to a type of file or a user ID. If an access right to a file is set a higher security level is allocated to this file.

The keyword is keyword s that the print server can extract from a print object file. Exemplary keyword extraction processing is described later. The relevant job ID is information enabling a user to identify relevancy of two or more files consecutively subjected to print processing. More specifically the relevant job ID includes a Prev field and a Next field that can record two or more consecutively executed jobs in a time series order.

It is now assumed that A B and C files have been consecutively printed. In this case the relevant job ID in a print job log of file A records a print job ID of file B in the Next field and records nothing in the Prev field. The relevant job ID in a print job log of file B records a print job ID of file C in the Next field and stores a print job ID of file A in the Prev field. The relevant job ID in a print job log of file C records nothing in the Next field and stores the print job ID of file B in the Prev field.

In a log of the first job the relevant job ID records Nothing in the Prev field because this job is a head job of the consecutively executed jobs. Furthermore the relevant job ID records 1000052 i.e. job ID of the second job to be next executed in the Next field. Similarly in a log of the second job the relevant job ID records 1000023 i.e. job ID of the first job having been previously executed in the Prev field and records 1000068 i.e. job ID of the third job to be next executed in the Next field. In a log of the third job the relevant job ID records 1000052 i.e. job ID of the second job having been previously executed in the Prev field and records Nothing in the Next field because the third job is a final job of the consecutively executed jobs.

At step the CPU newly generates and registers a record of a log having the format illustrated in . In this case the CPU stores a pointer of the generated record into a parameter newLog. 

At step the CPU records various information job ID input date time user name security level storage place file name type of file printer layout and keyword into respective items of the newLog. The CPU records the items of user name storage place file name type of file printer and layout based on information included in a print job received from the client PC or based on information included in a print completion notice received from the MFP. Respective items of job ID input date time and security level are not included in a print job or a print completion notice. Therefore the CPU records these items based on values generated by the print server .

Subsequently at step sub routine the CPU extracts keyword s from a print object file. The CPU executes the keyword extraction processing according to a flowchart illustrated in .

Processing of steps to is processing for recording items of the relevant job ID in a log. At step the CPU determines whether a log group recorded in the data storage includes any log having a user ID similar to the user ID of the newLog. If the CPU determines that there is a log having the same user ID YES in step the CPU stores a pointer of the detected log into a parameter oldLog.

If there are two or more logs having a user ID similar to the user ID of the newLog the CPU identifies a log which is latest in the input date time and stores a pointer of the identified log into the parameter oldLog. Then the processing flow proceeds to step .

At step the CPU acquires input date time information of the oldLog. If the CPU determines that there is not any log having the same user ID NO in step the CPU terminates the processing of this routine.

At step the CPU calculates a time difference between the input date time of the oldLog and the input date time of the newLog.

At step the CPU determines whether the calculated time difference is equal to or less than a threshold value. In this case the threshold value is a predetermined value set beforehand for the print server and if necessary changeable by a system administrator.

If the CPU determines that the elapsed time is greater than the threshold value NO in step the processing flow returns to step . At step the CPU again retrieves a log having a user ID similar to the user ID of the newLog.

If the CPU determines that the elapsed time is equal to or less than the threshold value YES in step the processing flow proceeds to step . At step the CPU records the job ID of the newLog into the Next field of the relevant job ID in the oldLog.

At step the CPU records a job ID of the oldLog into the Prev field of the relevant job ID in the newLog.

After completing the processing of step the processing flow returns to step . If the CPU determines that there is not any log having a user ID similar to the user ID of the newLog NO in step the CPU terminates the processing of this routine.

Through the above described processing the print server can generate a log of each print job. The print server stores the generated log into the data storage .

In the example processing illustrated in the CPU compares a job input interval with the predetermined threshold value to identify consecutively input jobs. However the CPU can use other methods. For example the CPU can regard two or more jobs as consecutive jobs if a logging on state of the client PC or the MFP is maintained during the entry of these jobs.

At step the CPU analyzes print data. At step the CPU determines whether the analyzed print data are all image data. If the CPU determines that the analyzed print data are image data only YES in step the processing flow proceeds to step .

At step the CPU performs Optical Character Reader OCR processing on the print data to extract character string information from the image data. If the CPU determines that the analyzed print data include some data other than the image data NO in step or if the CPU completes the processing of step the processing flow proceeds to step .

At step the CPU detects keyword s from the extracted character string information. More specifically the CPU verifies the extracted character string information with reference to keyword data stored beforehand in the external storage device of the print server . Namely the CPU extracts the keyword data involved in the extracted character string information. If the processing of step is completed the CPU terminates the processing routine illustrated in . The keyword data in the print server can be prepared by an administrator or stored according to an appropriate method.

At step the user operating the client PC identifies a print object document and activates the printer driver. In this case the client PC displays the printer driver screen illustrated in on its screen. Furthermore at step the user operating the MFP designates a desired box number on the screen illustrated in via the operation unit of the MFP and then selects a desired document on the screen illustrated in .

If a desired document is selected the client PC or the MFP transmits reference information and user information to the print server . In this embodiment the reference information refers to information including a storage place a file name and a type of file of the selected print data. The user information refers to information including a user ID and a security level of the user.

A user can instruct transmission of the reference information and the user information by clicking on a recommendable information acquisition button not illustrated if provided on the screen of or . In other words the recommendable information acquisition button enables a user to determine whether to acquire the recommendable information.

At step the print server executes relevant document retrieval processing. This processing is for retrieving any file printed together with a file similar to the file transmitted in step if the printing system has ever printed the same file. illustrates the details of the processing performed in step . The recommendable information obtained in this processing is useful for a user who performs print processing in the following situations.

For example if a conference designates materials to be used each attendant of this conference prepares and carries a print of the required materials. If a combination of these materials is identified based on print job log s the printing system can display a combination of documents as recommendable information when another user attending the same conference prints the materials.

For example a user prints a first web page that publicly introduces a new technology together with a second web page that introduces a relevant technology. In this case their print job logs remain in the printing system. If the second web page introducing the relevant technology can be notified as recommendable information based on the logs when another user prints the first web page this user can additionally obtain useful information relating to the newly introduced technology.

At step the print server executes recommendable printer retrieval processing. This processing is for retrieving a printer that has printed a file similar to the file transmitted in step if the printing system has ever printed the same file. illustrates the details of the processing performed in step . The recommendable information obtained in this processing is useful for a user who performs print processing in the following reasons.

For example a user designates a high quality color machine for printing data including high quality images an image forming apparatus fully supported by post processing apparatuses for printing data requiring special post processing and a high speed image forming apparatus for printing data including many pages.

If information including a recommendable image forming apparatus i.e. recommendable information based on the log s is available for a user the user can properly select an image forming apparatus to be used for print processing of a document.

At step the print server executes recommendable layout retrieval processing. This processing is for retrieving a layout of a file similar to the file transmitted in step if the printing system has ever printed the same file. illustrates the details of the processing performed in step . The recommendable information obtained in this processing becomes useful for a user who performs print processing for the following reasons.

A document may be printed according to a predetermined print layout e.g. bookbinding printing or allocation printing. If recommendable layout information i.e. information recommending a desirable layout for a document to be printed can be notified based on the log a user can appropriately perform print layout setting.

At step the print server transmits a result of retrieval processing performed in steps through to the client PC or the MFP.

At step the client PC or the MFP displays the result of retrieval processing i.e. information received from the print server on its screen.

The screen illustrated in can display information relating to three items i.e. a relevant document corresponding to the processing of step S a recommendable printer corresponding to the processing of step S and a recommendable layout corresponding to the processing of step S. If a user clicks on a FOR DETAILS button or the screen displays the details of the relevant document the recommendable printer or the recommendable layout .

A user can click on a PRINT TOGETHER button to instruct print processing for the relevant document retrieved by the processing of step in addition to a presently selected document. If a user clicks on a CHANGE SELECTED PRINTER the output destination printer illustrated in is changed to the printer retrieved by the processing of step . If a user clicks on a CHANGE LAYOUT button the print layout layout set in is changed to the layout retrieved by the processing of step .

The screen illustrated in can display information relating to three items i.e. a relevant document corresponding to the processing of step S a recommendable printer corresponding to the processing of step S and a recommendable layout corresponding to the processing of step S. If a user clicks on a FOR DETAILS button or the screen displays the details of the relevant document the recommendable printer or the recommendable layout .

A user can click on a PRINT TOGETHER button to instruct print processing for the relevant document retrieved by the processing of step in addition to a presently selected document. If a user clicks on a CHANGE SELECTED PRINTER the output destination printer is changed to the printer retrieved by the processing of step . If a user clicks on a CHANGE LAYOUT button the print layout is changed to the layout retrieved by the processing of step . The printer drivers and the screens of the MFP illustrated in can be modified in various ways.

At step if a user instructs print processing the client PC or the MFP transmits a print job to the print server . In this embodiment the print job includes print information in addition to the above described reference information and user information. The print information includes print data generated based on a selected file together with print setting information layout and output destination printer information.

At step the print server executes processing for retrieving a relevant document based on keyword s . The processing performed in step is processing for retrieving other print data including keyword s extracted from print data that is included in the print job transmitted by the processing of step from print data printed in previous print processing. illustrates the details of the processing performed in step .

The recommendable information obtained through the above described processing is useful for a user who performs print processing in the following situations. For example it may be desirable for a user to simultaneously print a plurality of documents belonging to a specific category e.g. budget related materials for the next fiscal year . It is desirable to analyze the contents of each document and record extracted keyword s in a log. If another user requests a print of a document belonging to the same category it is useful to present recommendable information including relevant document s so that the user can know the presence of any relevant materials. The usability can be improved.

At step the print server transmits print data to the MFP printer that executes print processing i.e. the output destination printer included in the received print job .

At step the print server transmits a notice of retrieval result obtained by the processing of step to the client PC or the MFP.

At step the client PC or the MFP receives the notice of retrieval result from the print server and displays the received retrieval result on its screen.

There are various methods for transmitting a notice step and displaying information step . For example a print completion screen illustrated in can display a result of the processing performed in step .

The screen illustrated in is an example print completion screen of the printer driver which includes a field that displays a result of retrieval processing obtained by the processing of step and a field that displays relevant document s retrieved based on the keyword s obtained by the processing of step .

As another method a box print completion screen including recommendable information similar to the information illustrated in can be displayed on a touch panel. As another method an electronic mail can be transmitted if an electronic mail address of a user is registered beforehand in the print server . As another method previous recommendable information can be displayed when the printer driver screen is opened again.

Similarly previous recommendable information can be displayed when the box print screen is opened on the touch panel. As another method any application constantly operating on a PC can be used. If software application capable of monitoring recommendable information is installed the print server can asynchronously inform the PC of any presence of recommendable information.

There are various methods for notifying and displaying recommendable information. It is desirable to enable a user to select one or more desirable methods for notifying and displaying recommendable information so that the notification display processing can be performed according to user s preference e.g. a method registered beforehand in the server .

To realize each step illustrated in the CPU of the print server executes a program loaded from the HD or the ROM.

In the following description it is assumed that the data storage stores the logs and illustrated in . The storage place of a file transmitted in step illustrated in is BOX89 078937 2006. The file name is design drawing for living room . The security level of user is C. 

At step the CPU accesses the data storage and retrieves log s similar in file name and storage place i.e. part of the received information . In this exemplary embodiment the CPU performs retrieval processing by comparing each one of a plurality of logs stored in the data storage with the received information with respect to the file name and the storage place.

At step the CPU determines whether there is any log having the same storage place and the same file name. If the CPU determines that there is a log having the same storage place and the same file name YES in step the processing flow proceeds to step . In the above described example the CPU retrieves a log having the file name design drawing for living room and the storage place BOX89 078937 2006 among the logs illustrated in . As a result the CPU detects the log .

At step the CPU determines whether any value is set in the Next or Prev field of the relevant job ID item of the found log. If the CPU determines that there is not any value set in the Next or Prev field NO in step the processing flow returns to step in which the CPU executes processing for retrieving another log. If the CPU determines that there is a value set in the Next or Prev field YES in step the processing flow proceeds to step .

At step the CPU checks the Prev field and identifies a head of consecutively printed jobs according to the log. According to the example illustrated in the log includes the job ID 1000023 recorded in the Prev field of the relevant job ID. Therefore as a result of retrieval processing the CPU detects the log which has the same ID.

Similarly the CPU checks the Prev field of the relevant job ID in the log . As the log records Nothing in the Prev field of the relevant job ID the CPU determines that the log is a log of a head job of the consecutively input jobs.

At step the CPU calculates an elapsed time based on a difference between the present date time and the input date time of a job corresponding to the log identified by the processing of step . The CPU can refer to a timer not illustrated provided in the print server to determine the present date time.

At step the CPU compares the elapsed time calculated by the processing of step with a predetermined threshold value set for the print server . The threshold value is a value determined by an administrator of the printing system and registered according to an appropriate flowchart not illustrated .

If the CPU determines that the calculated difference is greater than the threshold value NO in step the processing flow returns to step in which the CPU executes processing for retrieving another log. If the CPU determines that the calculated difference is equal to or less than the threshold value YES in step the processing flow proceeds to step .

At step the CPU checks the log retroactively from the head of the consecutively input jobs obtained by the processing of step . Then the CPU inspects an appropriate job referring to the file storage place and the security level. If there is an appropriate job the CPU records this job as relevant job information notification information .

If the storage place of a file corresponding to the log is a local storage of a PC of the user who inputs the file the CPU does not notify any relevant job information. Similarly if the security level of the log is higher than the security level of a user who performs print processing the CPU does not notify any relevant job information.

According to the above described example the storage place of the head job i.e. job corresponding to the log is a file server accessible via network and the security level of this job is set to E. The security level of a user who performs print processing is C. The security level E is lower than the security level C. Therefore the CPU notifies the relevant job information.

Then the CPU inspects the Next field of the relevant job ID in the log and detects the job ID 1000052 of the next executed job. Therefore the CPU checks the log having the same job ID. However the file of the log is similar to the print object file and is inappropriate as relevant job. Accordingly the CPU does not notify the log as relevant job information.

Next the CPU inspects the Next field of the relevant job ID in the log and detects the job ID 1000068 of the next executed job. Therefore the CPU checks the log having the same job ID. Similarly the CPU inspects the storage place and the security level of a file of the log .

The storage place of the file in the log is the local storage of a PC and is inappropriate as relevant job. Accordingly the CPU does not notify the file of the log as relevant job information. Then the CPU detects Nothing recorded in the Next field of the relevant job ID and determines that the job corresponding to log is the final job of the consecutively executed jobs.

After completing the processing of step the processing flow returns to step in which the CPU executes processing for retrieving another log. If the CPU determines that there is not any log having the same storage place and the same file name NO in step the processing flow proceeds to step .

At step the CPU determines whether there is any recorded job as notification information resulting from the processing of step . If the CPU determines that there is not any recorded information NO in step the CPU sends a message informing that there is not any relevant job and terminates the processing illustrated in .

If the CPU determines that there is recorded information YES in step the processing flow proceeds to step . At step the CPU registers the recorded information as information to be transmitted in step illustrated in and terminates the processing of this routine.

According to the example illustrated in the CPU notifies a log satisfying a plurality of conditions as a relevant job. Namely even if there is a log having the same storage place and the same file name the CPU does not notify any information if there is not any relevant job satisfying the determination condition of step .

Hence if there is any log having the same storage place and the same file name the CPU can extract a user name recorded in the log and notify any other file having been printed by this user as relevant document. In this case the CPU retrieves a log from the data storage based on the extracted user name. Similar to step the CPU can notify any retrieved log if it satisfies conditions with respect to the storage place and the security level as relevant document information.

To realize each step illustrated in the CPU of the print server executes a program loaded from the HD or the ROM.

In the following description it is assumed that the data storage stores logs through illustrated in . The storage place of a file transmitted in step illustrated in is BOX89 078937 2006. The file name is design drawing for living room . The type of file is graphic data. The security level of user is C. 

At step the CPU accesses the data storage and retrieves log s similar in type of file i.e. part of the received information . In this exemplary embodiment the CPU performs retrieval processing by comparing each one of a plurality of logs stored in the data storage with the received information with respect to the type of file.

At step the CPU determines whether there is any log having the same type of file. If the CPU determines that there is a log having the same type of file YES in step the processing flow proceeds to step . In the above described example the CPU retrieves a log having the type of file graphic data among the logs illustrated in . As a result the CPU detects the logs and .

At step the CPU calculates an elapsed time based on a difference between the present date time and the input date time of a job corresponding to the log detected by the processing of step . The CPU can refer to a timer not illustrated provided in the print server to determine the present date time.

At step the CPU compares the elapsed time calculated by the processing of step with a predetermined threshold value set for the print server . The threshold value is a value determined by an administrator of the printing system and registered according to an appropriate flowchart not illustrated . If the CPU determines that the calculated difference is greater than the threshold value NO in step the processing flow returns to step in which the CPU executes processing for retrieving another log.

If the CPU determines that the calculated difference is equal to or less than the threshold value YES in step the processing flow proceeds to step . For example according to the example illustrated in if the present date time is 2006 12 5 18 45 45 and the threshold value having been set is one week the CPU determines that the log satisfies the determination condition of step and determines that the log does not satisfy the determination condition of step .

At step the CPU refers to the printer field of a log which has been subjected to the determination processing of step . According to the example illustrated in the CPU refers to a printer 32 OA iRC3220 in the log . Then in step S the CPU registers the referred printer name as recommendable printer. In this case if the same printer is already registered as a recommendable printer the CPU increments a counter value.

By executing a comparison between the calculated time difference and the threshold value steps and the CPU can extract only the printer having been recently used as recommendable information. Namely the CPU does not notify any old printer as recommendable information. However the processing of steps and can be omitted if extracting a recommendable printer regardless of old and new is preferable.

Then the processing flow returns to step in which the CPU executes processing for retrieving another log. If the CPU determines that there is not any log having the same type of file NO in step the processing flow proceeds to step .

At step the CPU determines whether the printer i.e. recommendable printer registered in step is present on the network. More specifically the print server transmits via the network a retrieval packet including a keyword printer name registered as recommendable printer.

If there is a printer corresponding to the keyword the CPU determines that the recommendable printer is present on the network.

If the CPU determines that the recommendable printer is present YES in step the processing flow proceeds to step . If the CPU determines that the recommendable printer is not present NO in step the CPU terminates the processing of this routine.

At step the CPU determines whether the counter value recorded by the processing of step is equal to or greater than a predetermined threshold value. The threshold value is a value determined by an administrator of the printing system and registered according to an appropriate flowchart not illustrated .

If there is not any printer satisfying the above determination condition NO in step the CPU determines that there is no recommendable printer and terminates the processing of this routine. If there is a printer satisfying the above determination condition YES in step the processing flow proceeds to step .

At step the CPU registers notification information to transmit a notification indicating that the identified printer is a recommendable printer to the client PC or the MFP. In this case if two or more printers are detected by the processing of step the CPU can specify a printer having a highest counter value as recommendable printer.

Alternatively the CPU can notify each printer satisfying the determination condition of step together with its counter value to enable a user to know a printer which has been frequently used.

In steps and of the example processing illustrated in the CPU retrieves a log based on the type of file. Thus a user can know a printer frequently used for printing a file similar in type to the file that a user wants to print.

However the retrieval key used in step is not limited to the type of file. For example the CPU can use a file name and a storage place as retrieval keys in the processing of step . In this case a user can know a printer frequently used for printing a file similar in file name and storage place to the file that a user wants to print.

To realize each step illustrated in the CPU of the print server executes a program loaded from the HD or the ROM.

In the following description it is assumed that the data storage stores the logs through illustrated in . The storage place of a file transmitted in step illustrated in is fileserver1 2006. The file name is budget for fiscal 2006. The security level of user is C. 

At step the CPU accesses the data storage and retrieves log s similar in file name and storage place i.e. part of the received information . In this exemplary embodiment the CPU performs retrieval processing by comparing each one of a plurality of logs stored in the data storage with the received information with respect to the file name and the storage place.

At step the CPU determines whether there is any log having the same file name and the same storage place. If the CPU determines that there is a log having the same storage place and the same file name YES in step the processing flow proceeds to step . In the above described example the CPU retrieves a log having the file name budget for fiscal 2006 and the storage place fileserver1 2006 among the logs illustrated in . As a result the CPU detects the logs and .

At step the CPU calculates an elapsed time based on a difference between the present date time and the input date time of a job corresponding to the log detected by the processing of step . The CPU can refer to a timer not illustrated provided in the print server to determine the present date time.

At step the CPU compares the elapsed time calculated by the processing of step with a predetermined threshold value set for the print server . The threshold value is a value determined by an administrator of the printing system and registered according to an appropriate flowchart not illustrated .

If the CPU determines that the calculated difference is greater than the threshold value NO in step the processing flow returns to step in which the CPU executes processing for retrieving another log. If the CPU determines that the calculated difference is equal to or less than the threshold value NO in step the processing flow proceeds to step .

For example according to the example illustrated in if the present date time is 2006 12 5 18 45 45 and the threshold value having been set is one week the CPU determines that the log satisfies the determination condition of step and determines that the log does not satisfy the determination condition of step .

At step the CPU refers to the layout field of a log which has been subjected to the determination processing of step . According to the example illustrated in the CPU refers to a layout 2 in 1 two sided in the log . Then in step S the CPU registers the referred layout as recommendable layout. In this case if the same layout is already registered as recommendable layout the CPU increments a counter value.

By executing a comparison between the calculated time difference and the threshold value steps and the CPU can extract only the printer having been recently used as recommendable information. However the processing of steps and can be omitted if unnecessary.

Then the processing flow returns to step in which the CPU executes processing for retrieving another log. If the CPU determines that there is not any log having the same storage place and the same file name NO in step the processing flow proceeds to step .

At step the CPU determines whether there is any layout registered as recommendable layout in step . If the CPU determines that a recommendable layout is present YES in step the processing flow proceeds to step . If the CPU determines that there is not any recommendable layout NO in step the CPU terminates the processing of this routine.

At step the CPU determines whether the counter value recorded by the processing of step is equal to or greater than a threshold value. The threshold value is a value determined by an administrator of the printing system and registered according to an appropriate flowchart not illustrated .

If the CPU determines that there is no layout having a count value exceeding the threshold value i.e. if there is not any recommendable layout NO in step the CPU terminates the processing of this routine. If the CPU determines that there is a layout having a count value exceeding the threshold value i.e. if there is a recommendable layout YES in step the processing flow proceeds to step .

At step the CPU registers notification information to transmit a notification indicating that the identified printer is a recommendable printer to the client PC or the MFP. In this case if two or more printers are detected by the processing of step the CPU can specify a printer having a highest counter value as recommendable printer.

Alternatively the CPU can notify each printer satisfying the determination condition of step together with its counter value to enable a user to know a printer which has been frequently used.

To realize each step illustrated in the CPU of the print server executes a program loaded from the HD or the ROM.

In the following description it is assumed that the data storage stores the logs through illustrated in . The keywords extracted as a result of the keyword extraction processing illustrated in are 2006 fiscal year budget and equipment cost. 

At step the CPU accesses the data storage and retrieves log s similar in keyword i.e. information extracted from the print object file . In this exemplary embodiment the CPU performs retrieval processing by comparing each one of a plurality of logs stored in the data storage with the received information with respect to the keyword.

At step the CPU determines whether there is any log having a keyword similar to the extracted keyword. If the CPU determines that there is a log having the same keyword YES in step the processing flow proceeds to step . In the above described example the CPU retrieves a log that records 2006 fiscal year budget and equipment cost in the keyword among the logs illustrated in . As a result the CPU detects the logs and .

At step the CPU calculates an elapsed time based on a time difference between the present date time and the input date time of a job corresponding to the log detected by the processing of step . The CPU can refer to a timer not illustrated provided in the print server to determine the present date time.

At step the CPU compares the elapsed time calculated by the processing of step with a predetermined threshold value set for the print server and determines whether a difference between compared values is equal to or less than a threshold value. The threshold value is a value determined by an administrator of the printing system and registered according to an appropriate flowchart not illustrated .

If the CPU determines that the difference is greater than the threshold value NO in step the processing flow returns to step in which the CPU executes processing for retrieving another log. If the CPU determines that the difference is equal to or less than the threshold value YES in step the processing flow proceeds to step .

For example according to the example illustrated in if the present date time is 2006 12 5 18 45 45 and the threshold value is set to one week the CPU determines that the logs and satisfy the determination condition of step and the log does not satisfy the determination condition of step .

At step the CPU checks whether the job obtained by the processing of step is appropriate as notification information with reference to the information recorded in the file storage place and the security level . If the job is appropriate the CPU records this job as relevant job information notification information .

The processing of step is similar to the processing of step illustrated in . In the above described example if the security level of a user who performs print processing is B the CPU determines that a job corresponding to the log is appropriate as notification information.

If the processing of step is completed the processing flow returns to step in which the CPU executes processing for retrieving another log. If the CPU determines that there is not any log having the same keyword NO in step the processing flow proceeds to step .

At step the CPU determines whether there is any recorded job as notification information resulting from the processing of step . If the CPU determines that there is not any recorded information NO in step the CPU sends a message informing that there is not any relevant job and terminates the processing illustrated in .

If the CPU determines that there is recorded information YES in step the processing flow proceeds to step . At step the CPU registers the recorded information as information to be transmitted in step illustrated in and terminates the processing of this routine.

As described above exemplary embodiments of the present invention enable a user performing print processing to know various recommendable information relating to a print object file.

In particular if the printing system has ever printed file s similar to a print object file an exemplary embodiment enables a user to know another file s printed together with the similar file s . Thus a user can easily find file s relevant to the print object file.

In an exemplary embodiment the printing system can identify a printer that has been frequently used to print files similar to a print object file. Thus a user can easily find a printer suitable for printing the print object file.

In an exemplary embodiment the printing system can identify a print layout having been used for files similar to a print object file. Thus a user can easily find a print layout suitable for printing the print object file.

In an exemplary embodiment the printing system can identify another files including keyword s of a print object file. Thus a user can easily find file s relevant to the print object file.

In an exemplary embodiment the printing system enables a user to obtain part of the above described four types of recommendable information. In this case the printer driver operation screen illustrated in or the box operation screen illustrated in includes an additional button that a user can operate to select recommendable information if necessary.

For example a user can obtain only the recommendable printer information or obtain only the recommendable layout information.

The present invention can be applied to a system including two or more devices host computer interface device reader printer etc. and also applied to a single device copy machine facsimile apparatus etc. .

Furthermore software program code for realizing the functions of the above described exemplary embodiments can be supplied to a system or an apparatus including various devices. A computer or CPU or micro processing unit MPU in the system or the apparatus can execute the program to operate the devices to realize the functions of the above described exemplary embodiments. Accordingly the present invention encompasses the program code installable on a computer when the functions or processes of the exemplary embodiments can be realized by the computer.

In this case the program code itself can realize the functions of the exemplary embodiments. The equivalents of programs can be used if they possess comparable functions. In this case the type of program can be any one of object code interpreter program and OS script data.

Furthermore the present invention encompasses supplying program code to a computer with a storage or recording medium storing the program code. A storage medium supplying the program can be selected from any one of a floppy disk a hard disk an optical disk a magneto optical MO disk a compact disk ROM CD ROM a CD recordable CD R a CD rewritable CD RW a magnetic tape a nonvolatile memory card a ROM and a DVD DVD ROM DVD R .

Moreover an operating system OS or other application software running on a computer can execute part or the whole of actual processing based on instructions of the programs.

Additionally the program code read out of a storage medium can be written into a memory of a function expansion board equipped in a computer or into a memory of a function expansion unit connected to the computer. In this case based on an instruction of the program a CPU provided on the function expansion board or the function expansion unit can execute part or the whole of the processing so that the functions of the above described exemplary embodiments can be realized.

While the present invention has been described with reference to exemplary embodiments it is to be understood that the invention is not limited to the disclosed exemplary embodiments. The scope of the following claims is to be accorded the broadest interpretation so as to encompass all modifications equivalent structures and functions.

This application claims priority from Japanese Patent Application No. 2007 053053 filed Mar. 2 2007 which is hereby incorporated by reference herein in its entirety.

