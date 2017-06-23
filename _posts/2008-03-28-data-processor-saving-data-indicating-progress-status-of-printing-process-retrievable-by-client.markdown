---

title: Data processor saving data indicating progress status of printing process retrievable by client
abstract: A data processor and a host device are bi-directionally communicably connected to each other. The data processor includes a process-executing unit and a progress-status-saving unit. The process-executing unit executes a prescribed process when a process-requested file is written in a prescribed folder. The progress-status-saving unit saves progress status data indicating a progress status of the prescribed process so that the progress status data is retrievable by the host device.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09224073&OS=09224073&RS=09224073
owner: BROTHER KOGYO KABUSHIKI KAISHA
number: 09224073
owner_city: Nagoya-Shi, Aichi-Ken
owner_country: JP
publication_date: 20080328
---
This application is a continuation in part application of U.S. application Ser. No. 12 049 919 filed Mar. 17 2008. This application also claims priorities from Japanese patent application Nos. 2007 085187 filed Mar. 28 2007 2007 105538 filed Apr. 13 2007 and 2008 027275 filed Feb. 7 2008. The entire contents of the priority applications are incorporated herein by reference.

The present invention relates to a data processing system and more particularly to a system configured of a device having a server function capable of preparing data regarding the progress status of processes that can be accessed from a device with a client function.

Most personal computers herein Rafter abbreviated as PC of recent years have standard client software installed during the manufacturing stage or when an operating system OS is installed. Examples of client software are Explorer and Microsoft Internet Explorer registered trademarks provided with the Windows registered trademark platform.

Through this standard client software the user of the PC can read files from and write files to a server device acquire filenames or folder names from the server or execute other operations without having to install separate software.

This client software includes a function for displaying a window showing filenames and icons representing the files folder names for folders storing files and icons representing the folders a tree showing the hierarchical structure of the folders and the like as a user friendly way of presenting file and folder data to the user.

Japanese patent application publication No. 2006 227908A discloses a technology involving the installation of an application direct printing program on a PC through which application the user can instruct a printer to print a PDF Portable Document Format file. The PC user can also receive a report through this application indicating whether the printing operation was a success or a failure.

However with the conventional technology described above the user cannot issue a command to print a PDF file or receive a printing report at the PC without installing a prescribed application the direct printing program .

In view of the foregoing it is an object of the invention to provide a technology allowing a user to acquire a user friendly report giving details of a process performed on a data processor when operating a PC with standard client software installed.

The above and other objects will be attained by a data processor bi directionally communicably connected to a host device. The data processor includes a process executing unit that executes a prescribed process when a process requested file is written in a prescribed folder and a progress status saving unit that saves progress status data indicating a progress status of the prescribed process so that the progress status data is retrievable by the host device.

According to another aspect of the invention a data processing system is provided that includes a host device a data processor bi directionally communicably connected to the host device and a progress status saving unit. The data processor includes a process executing unit that executes a prescribed process by writing a process requested file into a prescribed folder. The progress status saving unit saves progress status data indicating the progress status of the prescribed process so that the data is retrievable by the host device. It should be noted that the folders are also referred to as directories.

The concept of the prescribed folder is paths managed by the data processor. Hence it is not necessary to store the process requested file and associated subfolders if any in the prescribed folder on the data processor. This data may be stored on a network storage device or on the host device for example.

The prescribed process may be a process for printing data on a printing unit or the like in which the data written in the prescribed folder is processed. Alternatively the prescribed process may be a process for scanning an original document with a scanning unit or a configuration process for example in which command data written in the prescribed folder is interpreted and the corresponding commands are issued to components of the data processor.

The progress status saving unit may save the progress status data indicating the progress status of the prescribed process in a storage device that the host device can access or may save location data specifying the location of the progress status data so that the host device can access the progress status data via the location data. The progress status saving unit may also create the progress status data when the host device attempts to access this data.

With the data processor of the invention the user of the host device can instruct the data processor to perform the prescribed process. This can be done by for example transmitting the process requested data from the host device to the prescribed folder. Further the host device can acquire the progress status data saved in the data processor and can output a report on the progress status for the user.

The progress status of the prescribed process may be represented by at least one of a filename of the progress status data a folder name in which the progress status data is saved and a file content of the progress status data. With the data processor thus organized the user of the host device can acquire a report on the progress status outputted by the host device by acquiring the filename folder name or file content from the data processor.

The progress status saving unit may save the progress status data in the prescribed folder in which the process requested file is written. With the data processor thus organized the user of the host device can acquire a report on the progress status outputted by the host device simply by accessing the prescribed folder in which the process requested file has been written.

The progress status of the prescribed process may be classified into a plurality of categories and the progress status saving unit may save the progress status data in a folder identified by a category of the process status data. Further the progress status saving unit may create a plurality of folders in one to one correspondence with the plurality of categories. With the data processor thus organized the user of the host device can learn the progress status of a desired category simply by accessing the folder for that category. Also the user of the host device can learn which folder must be accessed in order to view the progress status in a prescribed category simply by checking the folder structure.

A file controlling unit may further be provided in the data processor for preventing the host device from deleting or modifying the process requested file written in the prescribed folder during a period of time from a start of execution until a completion of execution of the prescribed process.

Generally the data processor is provided with a function for deleting and modifying files based on a request to delete or modify files received from the host device. The data processor of the invention can prevent files from being deleted or modified when undergoing a process.

According to yet another aspect of the invention there is provided a computer program product including a computer usable medium having readable program code embodied in the medium the computer program product including a least one component to instruct execution of a prescribed process when a process requested file is written in a prescribed folder of a data processor bi directionally communicably connected to a computer that runs in accordance with the computer program and save progress status data indicating a progress status of the prescribed process and allow the computer to retrieve the progress status data.

With the computer program product of the invention the user of the computer may command the data processor to perform the prescribed process by for example transmitting process requested data to the prescribed folder of the data processor. The user can also acquire a report on the progress status outputted by the computer simply by using the computer to acquire data indicating the progress of a process known by the data processor.

Next embodiments of the present invention will be described while referring to the accompanying drawings.

A data processing system according to a first embodiment of the invention is constructed of a personal computer PC functioning as an external device and a multifunction peripheral functioning as the data processor.

In the first embodiment the user of the PC can issue a direct print command for printing an image file by copying the image file into a prescribed folder on the multifunction peripheral using the file copying function provided standard on the PC .

Upon receiving a direct print command the multifunction peripheral proceeds with the printing process and saves a file indicating the printing progress status in a prescribed folder on the multifunction peripheral .

Using a file browsing function provided standard on the PC the user of the PC can access the file saved in the prescribed folder of the multifunction peripheral in order to view data indicating the stage of progress in the direct printing operation performed on the multifunction peripheral such as currently printing printing cancelled printing completed and unprintable as shown in A D and A D.

In the first embodiment the user can perform direct printing only with image files of the Joint Photographic Experts Group JPEG standard hereinafter referred to as JPEG files and image files created on the multifunction peripheral in the PDF format i.e. PDF files created according to the multifunction peripheral manufacturer s specific format hereinafter referred to as vendor format PDF files .

The data processing system cannot directly print all PDF files but only PDF files of the vendor format. Hence when creating the vendor format PDF files the multifunction peripheral adds header data indicating that the file is a PDF file of the vendor format in order that the type of PDF file can be identified.

Next the hardware structure of the data processing system according to the first embodiment will be described while referring to the accompanying drawings.

An operating system OS such as Windows registered trademark Linux registered trademark or MacOS registered trademark is installed on both the PC and multifunction peripheral to provide basic functions shared by the applications such as input output functions and a function to access storage devices. Functions provided by the OS that are particularly useful in the present invention include a function for sharing folders among devices on the same network and a function for allowing or denying access to the shared files. Since the functions provided by the various OS s described above are well known in the art a detailed description of these functions will not be provided. In the following description it will be assumed that Windows registered trademark is installed on both the PC and multifunction peripheral and provides various functions Application Programming Interface API .

The multifunction peripheral is also provided with a liquid crystal display LCD having a backlight for illuminating the display screen from the back surface.

The CPU is connected through a bus to a RAN for temporarily storing results of computations performed by the CPU a ROM storing BIOS and other programs executed by the CPU and a hard disk drive HDD serving as a data storage device. The ROM and HDD store various programs and the like executed by the CPU to implement the processes described later.

The CPU is also connected via the bus to a communication interface for communicating with the multifunction peripheral and other devices a display control unit for controlling operating screens displayed for the user on the monitor and an input detector connected to the keyboard and mouse for detecting user input on these devices.

As described above the PC and multifunction peripheral are connected to each other via a LAN cable USB cable or the like so as to be capable of communicating bi directionally. The PC recognizes the multifunction peripheral as a network drive in the case of a LAN cable or a device having removable storage area in the case of a USB cable and can access the folder structure constructed by the multifunction peripheral . The PC also displays icons corresponding to the folder structure on the multifunction peripheral and possesses a function for copying transmitting files to folders on the multifunction peripheral by dragging and dropping icons corresponding to the files on icons corresponding to the folders.

The multifunction peripheral includes a CPU a ROM a RAM a printer unit a scanner unit an operating unit a communication interface the LCD and a storage media drive C all of which are connected via a bus . The ROM stores various programs executed by the CPU for implementing processes described later. Areas for saving and processing data scanned by the scanner unit and the like are allocated in the RAM . The printer unit and scanner unit implement a printer function and scanner function respectively and together implement a copy function by executing both the printer function and scanner function.

The printer unit has a function for notifying the CPU when an error occurs during printing including a description of the error out of ink and paper jam for example and whether the printer unit can recover from the error. The printer unit also has a function for notifying the CPU when printing succeeded or failed.

The operating unit is configured of a control panel having various buttons and the like that the user can operate to configure settings for direct printing for example. The communication interface implements communications between the multifunction peripheral and the PC or other external device. A storage medium can be inserted into the storage media drive . The storage medium stores the vendor format PDF file.

The multifunction peripheral constructs a folder structure such as that shown in . As described earlier the PC can access this folder structure. The folder structure shown in includes a folder X G signifying the multifunction peripheral and under this folder hierarchically a Print Request folder a Currently Printing folder a Printing Completed folder and an Unprintable folder.

The user of the PC drags and drops image files that the user wishes to print directly with the multifunction peripheral in the Print Request folder. The multifunction peripheral writes image files that car be printed directly in the Currently Printing folder in a format by which the filename can be recognized. The multifunction peripheral writes image files to the Printing Completed folder in a format for recognizing the filename after a direct printing operation has been completed for the image files. The multifunction peripheral writes image files that cannot be printed directly in the Unprintable folder in a format for recognizing the filename.

Next the configuration of windows displayed on the PC according to the first embodiment will be described with reference to the drawings.

In the example of under the folder signifying the multifunction peripheral the Explorer window displays the Print Request folder having the folder name 1. Copy files to be printed here the Currently Printing folder having the folder name 2. Status of files being printed the Printing Completed folder having the folder name 3. Status of printed files and the Unprintable folder having the folder name 4. Status of unprintable files. 

The user of the PC can instruct the multifunction peripheral to perform a direct print by dragging and dropping the image file .ppp for example to the Print Request folder.

Next operations of the PC and multifunction peripheral having the above hardware structure will be described. The following description covers a process executed by the PC and multifunction peripheral for receiving a direct printing request from the user and displaying data indicating the printing progress on the monitor of the PC through Explorer.

At the beginning of the process in the user of the PC has already started Windows and Explorer and has accessed the folder structure on the multifunction peripheral through Explorer to display the window shown in .

In S of the CPU of the PC receives a user operation to select a file that the user wishes to print for example a mouse operation to click on the file and highlights the file based on this operation. In S the CPU receives a user operation to drag and drop the selected file to the Print Request folder see . After receiving this drag and drop operation in S the CPU sequentially transfers data for the file selected by the drag and drop operation in S to the multifunction peripheral .

On the multifunction peripheral side the process in begins after the power to the multifunction peripheral is turned on and the CPU has entered a standby state to wait for an access from an external device.

After the PC has transferred a selected file to the Print Request folder in S in S the CPU sets the transferred file and or the Print Request folder to read only thereby preventing the transferred file from being deleted from the multifunction peripheral . In S the CPU sequentially reads data of each transferred file to the RAM . In S the CPU determines whether the transferred file can be printed based on the extension or header data on the file. In this case the CPU determines that the file can be printed if the transferred file is a JPEG file or a vendor format PDF file the determination process is described later with reference to .

After determining that the transferred file can be printed i.e. that the transferred file is of the JPEG format or the PDF vendor format S YES in S the CPU stores the filename of the transferred file .ppp for example and saves a file .txt in the Currently Printing folder indicating that the file having the filename stored in S is being printed see .

If a file being stored in the Currently Printing folder has the same name as another file already stored in the folder sequential numbers can be added to the filenames for example to avoid duplicate filenames. This same process is performed in the second embodiment when attempting to write a file indicating the progress status of a printing operation when a file with the same filename already exists.

In S the CPU configures the multifunction peripheral to return any filenames or content in the Currently Printing folder such as the text A shown in when requested from the PC so that the user of the PC can view this data. Hence the user can check the progress of a direct printing operation from the PC side see S . In S the CPU decodes the transferred file according to its format and in S prints the decoded transfer file using the printer unit .

If a non recoverable error such as a paper jam or out of ink error occurs in the printer unit during printing the CPU saves a file in the Currently Printing folder indicating that the printing operation on the transferred file was canceled at that time see . Alternatively the contents of the file already saved in the Currently Printing folder can be updated to indicate that printing was canceled. When a non recoverable error occurs on the printer unit this event is handled as a failed printing process in the determination of S described later.

In S the CPU determines whether the transferred file was printed successfully. If the transferred file was printed successfully S YES then in S the CPU deletes data for the transferred file from the RAM . In S the CPU saves a file in the Printing Completed folder indicating that the transferred file was printed successfully see .

In S the CPU deletes the filename that was saved in the Currently Printing folder in S. The CPU deletes this file a prescribed time after determining in S that the transferred file was printed successfully.

In S the CPU enables the user to view the contents of the Printing Completed folder from the PC see the text C in . Accordingly the user can check the progress status of a direct printing operation from the PC side see S . By performing an operation on the PC the user can also delete a filename or a file that was saved in the Printing Completed folder in S. If the user does not perform an operation to delete the file at this time in S the CPU deletes the filename stored in the Printing Completed folder in S when access by the PC ends thereby preventing the accumulation of unchecked files. Alternatively the CPU may delete a filename when a prescribed time has elapsed since the CPU determined in S that the transferred file was printed successfully.

However if the CPU determines in S that the transferred file cannot be printed i.e. that the transferred file is not a JPEG file or a vendor formal PDF file S NO or if the CPU determines in S that printing of the transferred file failed S NO in S the CPU saves the filename of the transferred file while deleting the data for the transferred file from the RAM and in S saves a file indicating that the file having the filename saved in S could not be printed in the Unprintable folder see .

In S the CPU enables the user to view contents or the Unprintable folder from the PC see the text D in . Accordingly the user can check the progress status of a direct printing operation from the PC side see S .

By performing an operation on the PC the user can delete a filename saved in the Unprintable folder in S. If the user does not perform an operation to delete the file in S the CPU deletes the filename saved in the Unprintable folder in S when access by the PC ends thereby preventing an accumulation of unchecked files. Alternatively the CPU may delete the file upon determining in S that the file cannot be printed or when a prescribed time has elapsed after determining in S that printing of the transferred file failed.

If the printing was cancelled during execution of the steps of the flowchart shown in the execution of the steps may be forcibly interrupted and resumed when the cause of print cancellation is solved.

In this way the data processing system having the hardware structure described above can receive requests from the user to perform direct printing operations and can display data showing the progress of the operation on the monitor of the PC via the standard software Explorer.

Next the method that the multifunction peripheral uses in S to determine whether a file transferred from the PC can be printed whether the file has the JPEG format or the PDF vendor format will be described with reference to . is a flowchart illustrating steps in the process for determining whether a file transferred from the PC can be printed.

In S of the CPU identifying the extension in the target file. In S the CPU determines whether the extension of the target file is an extension for the JPEG format or PDF format. For purposes of description jjj will be used to indicate the extension of a JPEG file and ppp will be used to indicate the extension of a PDF file in the embodiment.

If the extension of the target file is neither a JPEG extension nor a PDF extension S NO then in S the CPU determines that the target file cannot be printed. However if the extension of the target file is a JPEG extension or a PDF extension S YES then in S the CPU determines based on the extension of the target file whether the file is a JPEG format file or a PDF format file.

If the target file is a JPEG file S JPEG in S the CPU determines that the target file can be printed. However if the target file is a PDF file S PDF then in S the CPU verifies the existence of header data in the target PDF file and in S reads the header data from the file see . In S the CPU determines whether the header data read from the target PDF file includes vendor specific data see .

Here a description will be given for the header data and the vendor specific data. shows a sample data structure for a vendor format PDF file. That is a vendor format PDF file is configured of a common PDF file structure including header data such as data indicating the size and creation date added to main data in the PDF format but also includes vendor specific data as header data.

Returning to the flowchart in if the header data in the target PDF file includes vendor specific data and the vendor specific data indicates the specified company S YES then in S the CPU determines that the target file can be printed. However if the header data in the target PDF file does not include vendor specific data or if the vendor specific data does not indicate the specified company S NO then in S the CPU determines that the target file cannot be printed.

In this way the multifunction peripheral determines whether a file transferred from the PC can be printed i.e. whether the file is a JPEG file or a vendor format PDF file.

Next the method of creating a vendor format PDF file on the multifunction peripheral will be described with reference to . is a flowchart illustrating steps in the process by which the multifunction peripheral creates a vendor format PDF file.

At the starting point of the flowchart in the multifunction peripheral is in a standby state waiting for operations from the user. When the user sets an original document in the scanner unit in S the CPU of the multifunction peripheral detects the document. After receiving a user command inputted via the operating unit in S the CPU shifts to the scan to card mode for scanning an original document with the scanner unit storing the scanned data in an external storage medium inserted in the storage media drive . In S the CPU configures settings necessary for scanning resolution format etc. based on user instructions. In S the CPU receives a command inputted by the user to begin scanning and in S activates the scanner unit to perform a scan.

In S the CPU encodes the scanned data acquired in S to create the vendor format PDF file shown in . In S the CPU stores this file data in the storage medium mounted in the storage media drive .

As described in detail above when the user of the PC wishes to directly print an image file and drags and drops the image file on an icon indicating the Print Request folder of the multifunction peripheral that is displayed in Explorer on the PC S the image file is copied transmitted to the Print Request folder provided in the folder structure of the multifunction peripheral S S and the multifunction peripheral performs a direct print of the transferred image file S . In this way the user can instruct the multifunction peripheral to directly print a file from the PC using Explorer which is a standard application of the operating system.

If the user accesses the Currently Printing folder Printing Completed folder or Unprintable folder provided in the folder structure on the multifunction peripheral using Explorer in order to check the progress of the direct printing operation the filename or file content in the accessed folder is copied transmitted from the multifunction peripheral to the PC S S S S S S S S .

Since the user can view the filename or file content copied from the multifunction peripheral on the PC the data processing system allows the user to confirm the progress status of a direct printing operation using the standard application Explorer.

Next a second embodiment of the present invention will be described. The second embodiment differs from the first embodiment in that the multifunction peripheral performs direct printing of files stored in the external storage medium mounted in the storage media drive of the multifunction peripheral .

As in the first embodiment described above the multifunction peripheral according to the second embodiment proceeds with a printing operation upon receiving a direct print command while saving files indicating the progress status for the printing operation in prescribed folders configured on the multifunction peripheral . Accordingly the user of the PC can use a standard file browsing function of the PC to access the files saved in the prescribed folders on the multifunction peripheral in order to view data indicating the stage of progress in the direct printing operation for example current printing printing canceled printing completed unprintable as shown in A D and A D.

As in the first embodiment described above the multifunction peripheral according to the second embodiment allows only JPEG files and vendor format PDF files as the target for direct printing. Also the hardware structure of the PC and multifunction peripheral and the configuration of windows displayed on the PC are identical to those described in the first embodiment.

Operations of the PC and multifunction peripheral according to the second embodiment having the same hardware structure as those in the first embodiment will be described for the process of receiving a direct printing request from the user and displaying data indicating the progress of the direct printing process on the monitor of the PC through the standard software function Explorer.

At the starting point of the flowchart in the CPU of the multifunction peripheral is in a standby state waiting for operations by the user. Upon receiving an operation from the user to shift modes in S the CPU shifts to a media print mode for printing an image file in the storage medium mounted in the storage media drive .

In S the CPU analyzes the extension header data and the like for each image file in the storage medium . In S the CPU determines whether the image files in the storage medium include files that cannot be printed i.e. executes the determination process shown in on each image file.

If the CPU determines that the storage medium includes files that cannot be printed S YES then in S the CPU displays a message on the LCD indicating that the files in question cannot be printed. At this time a window such as a temporary popup window is displayed on the LCD . As shown in the example of the window includes a message such as Only files of the JPEG format or vendor format can be printed. However if the storage medium does not include files that cannot be printed S NO no display is particularly necessary.

In S the CPU of the multifunction peripheral displays on the LCD only files that can be printed directly. For example as illustrated in the CPU displays thumbnail images on the LCD for files that can be printed directly the boxes around alphabetical characters in .

As shown in the display on the LCD may also include a File List button for example. If the user operates a pointer to open the File List button the CPU can be configured to display a list of files that cannot be directly printed as shown in .

Upon receiving input for a desired file selected by the user in S the CPU identifies the image file based on the selection operation and sequentially reads data for the identified file to the RAM . In S the CPU configures settings required for printing the file selected in S such as paper size and resolution.

In S of the CPU stores the filename for the selected file .ppp for example . In S the CPU saves a file .txt in the Currently Printing folder indicating that the file having the filename stored in S is being printed see .

In S the CPU configures the multifunction peripheral to return the filenames and content in the Currently Printing folder see the text A in when a request is received from the PC so that the user can view this data. Hence the user can confirm the state of progress in a direct printing operation from the PC side.

In S the CPU decodes the selected file according to the format. In S the CPU controls the printer unit to print the decoded file. When a non recoverable error such as a paper jam or an out of ink errors occurs during printing on the printer unit the CPU saves a file in the Currently Printing folder indicating that printing of the transferred file has been suspended at that time see . Alternatively the CPU may update the contents of the file already stored in the Currently Printing folder to indicate that printing has been suspended. When a non recoverable error occurs on the printer unit the CPU treats the printing operation as a failed operation in the determination of S described next.

In S the CPU determines whether the selected file was printed successfully. If the selected file was printed successfully S YES in S the CPU deletes data for the transferred file from the PAM . In S the CPU saves a file in the Printing Completed folder indicating that printing of the selected file was completed see .

In S the CPU deletes the filename saved in the Currently Printing folder in S. The CPU may delete the filename when a prescribed time has elapsed after determining in S that the transferred file was printed successfully.

In S the CPU enables the user to view the content of the Printing Completed folder from the PC see the text C in . In this way the user can confirm the progress of a direct printing operation from the PC side.

By performing an operation on the PC the user can also delete a filename saved in the Printing Completed folder in S. If the user does not perform an operation to delete the file in S the CPU deletes the filename saved in the Printing Completed folder in S when access by the PC ends thereby preventing an accumulation of unchecked files. Alternatively the CPU may delete the file when a prescribed time has elapsed after determining in S that the transferred file was printed successfully.

However if the CPU determines in S that printing of the transferred file failed S NO in S the CPU saves the filename of the transferred file while deleting the data for the transferred file from the RAM and in S saves a file in the Unprintable folder indicating that the file having the filename saved in S could not be printed see .

In S the CPU enables the user to view contents of the Unprintable folder from the PC see the text D in . Accordingly the user can check the progress status of a direct printing operation from the PC side.

By performing an operation on the PC the user can also delete a filename saved in the Unprintable folder in S. If the user does not perform an operation to delete the file in S the CPU deletes the filename saved in the Unprintable folder in S when access by the PC ends thereby preventing an accumulation of unchecked files. Alternatively the CPU may delete the file when a prescribed time has elapsed after determining in S that printing of the transferred file failed.

In this way the data processing system having the same hardware structure as described in the first embodiment can receive requests from the user to perform direct printing operations and can display data showing the progress of the operation on the monitor of the PC via the standard software Explorer.

With the data processing system according to the second embodiment described above the user can select an image file stored on the storage medium to be printed directly S and the multifunction peripheral directly prints the selected image file S .

If the user accesses the Currently Printing folder Printing Completed folder or Unprintable folder provided in the folder structure on the multifunction peripheral using Explorer in order to check the progress of the direct printing operation the filename or file content in the accessed folder is copied transmitted from the multifunction peripheral to the PC S S S S S S S S .

Since the user can view the filename or file content copied from the multifunction peripheral on the PC the data processing system of the preferred embodiment allows the user to confirm the progress status of a direct printing operation using the standard application Explorer.

While the invention has been described in detail with reference to specific embodiments thereof it would be apparent to those skilled in the art that many modifications and variations may be made therein without departing from the spirit of the invention the scope of which is defined by the attached claims.

For example when the user issues a request from the PC to the multifunction peripheral to access the folder X G signifying the multifunction peripheral the multifunction peripheral may transfer the filenames and file content in the Currently Printing folder Printing Completed folder or Unprintable folder to the PC . In this way the user can learn the progress status of the printing process all at once without accessing the folder signifying the multifunction peripheral .

For example in the first embodiment described above the user issues a request from the PC to perform a direct print by copying an image file into the Print Request folder. However the multifunction peripheral may be configured to acquire the image file and print the file directly when a file describing the location URL of an image file stored on a PC or other device is copied to the Print Request folder.

The multifunction peripheral may also be configured to perform a direct printing operation when an image file or a file describing the location of an image file is copied to the folder signifying the multifunction peripheral .

Further while in the second embodiment displays the filenames of files that cannot be directly printed the display may include the actual thumbnail images of files that cannot be directly printed.

In the embodiments described above if an image file cannot be printed on the multifunction peripheral S NO the CPU deletes data for the image file from the RAM S . However the CPU may instead preserve the image file data rather than deleting this data from the RAM .

In the embodiments described above after the CPU of the multifunction peripheral determines that printing succeeded or failed S S the CPU deletes data for the image file targeted in this determination from the RAM S S S and S . However the CPU may instead preserve the image file data rather than deleting this data from the RAN .

By preserving data for image files targeted for direct printing rather than deleting this data from the RAM the multifunction peripheral can transmit data of the image file targeted for direct printing to the PC after completing the direct printing operation. It can be particularly useful to return the image file targeted for direct printing to the PC even though the image file was initially transferred from the PC if the user mistakenly moves or deletes the image file on the PC .

In the embodiments described above the folder structure of the multifunction peripheral shown in has a Currently Printing folder Printing Completed folder and Unprintable folder arranged beneath the folder X G signifying the multifunction peripheral and the multifunction peripheral is configured to save files indicating progress of the printing processes in these respective folders in S S S S S S and the like.

Alternatively it is possible to provide a notification folder for saving notification files immediately beneath the folder X G signifying the multifunction peripheral as shown in the folder structure of and to configure the multifunction peripheral to save files indicating the progress status of the printing processes in the notification folder in S S S S S S and the like. With this configuration the user of the PC can easily confirm the status of a printing process by accessing the notification folder.

The same effects can be obtained without the notification folder simply by saving the files indicating the progress status of printing processes in the folder signifying the multifunction peripheral .

Alternatively the multifunction peripheral may be configured to save files indicating the progress status of printing processes in the Print Request folder. With this construction the user of the PC can easily confirm the status of printing processes simply by reaccessing the same Print Request folder accessed to request a direct printing operation.

As shown in it is also possible to provide a text file with the filename currently printing.txt and to write content the text A B or the like indicating the printing status of an image file currently printing or printing canceled for example in this text file. Another text file may be provided with the filename printing completed.txt with the date processing system configured to write content the text C for example indicating the printing status of the image file printing completed for example to this text file. Another text file may be provided with the filename unprintable.txt with the multifunction peripheral configured to write content the text D for example indicating the printing status of the image file unprintable to this text file.

With this configuration the user of the PC can easily confirm the progress status simply by displaying the content of the text files.

Even when using these text files the multifunction peripheral may be configured to save the text files in the respective Currently Printing folder Printing Completed folder and Unprintable folder. Also the multifunction peripheral may be configured to save these text files in the notification folder the folder signifying the multifunction peripheral or the printing request folder.

With the above configuration text indicating the printing status of an image file is added to each text file in the processes of S S S S S S and the like. In this case the user of the PC can easily confirm the status for a plurality of printing processes at the same time simply by displaying the content of the text files.

While the multifunction peripheral is configured to save files having filenames indicating the printing status of image files in S S S S S S and the like the multifunction peripheral may certainly also be configured to save folders having folder names indicating the printing status of image files. The configuration for saving folders having such folder names is not limited to that described in the embodiments. Many modifications and variations are possible.

The present invention may also certainly be applied to devices other than the multifunction peripheral such as a scanner having a shared server function. In this case a file describing scanner settings and a destination for transferring data is copied to a folder on the scanner itself and the scanner scans an original document according to the settings in the file and transfers the scanned image data to the transfer destination.

In this example the scanner may transfer progress data to a computer possessing a shared client function as file access data. This progress data may indicate whether an original document to be scanned has been set in the scanner whether scanning was performed successfully whether communication with the specified transfer destination was established and whether the image data was transferred successfully for example.

The present invention may also be applied to a scanner that scans an original document based on settings specified in a file and transmits the image data to the specified transfer destination when a storage medium storing a file describing the scanner settings and transfer destination is inserted in a memory slot of the scanner.

The present invention can be applied to a technology for preparing data indicating the stages of progress in data processing.

