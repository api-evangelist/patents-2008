---

title: Information processing apparatus, information transmission method, and control program therefor
abstract: An information processing apparatus includes an acquisition unit configured to acquire, from a plurality of image forming apparatuses, application information indicating a type of each application program installed on the plurality of image forming apparatuses, an application selection receiving unit configured to receive selection of an application program corresponding to the acquired application information, a setting information selection receiving unit configured to receive selection of setting information used in the application program whose selection has been received, an apparatus selection receiving unit configured to receive selection of an image forming apparatus as a destination to which to transmit the setting information from among image forming apparatuses installed with the application program whose selection has been received, and a transmission control unit configured to control processing for transmitting, to the image forming apparatus whose selection has been received, the setting information whose selection has been received.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07730225&OS=07730225&RS=07730225
owner: Canon Kabushiki Kaisha
number: 07730225
owner_city: Tokyo
owner_country: JP
publication_date: 20080418
---
The present invention relates to an information processing apparatus configured to communicate with an image forming apparatus allowing an application program to be installed thereon.

Conventionally in most cases software for an image processing apparatus is installed on a real time operating system hereinafter referred to as an RTOS as static and fixed firmware. If such firmware includes a plurality of modules such firmware is stored in a non volatile memory of an image processing apparatus while being statically linked as a whole to a single load module.

When the ROTS is activated such firmware is loaded from a non volatile memory such as a hard disk onto a random access memory RAM to be executed or is executed directly on a non volatile memory such as a read only memory ROM .

In an image processing apparatus discussed in Japanese Patent Application Laid Open No. 11 282684 and Japanese Patent Application Laid Open No. 2003 256216 another software operation environment is provided on and in addition to an RTOS of firmware for a built in system. Thus an image processing apparatus discussed in Japanese Patent Application Laid Open No. 11 282684 and Japanese Patent Application Laid Open No. 2003 256216 supports dynamic characteristics of software such as dynamic loading dynamic linking and dynamic memory operation in the additionally provided software operation environment.

Furthermore Japanese Patent Application Laid Open No. 11 53132 discusses a method using an application download type printer containing a network computer. The method discussed in Japanese Patent Application Laid Open No. 11 53132 downloads a data file to be printed and an application program compliant with the data file from a computer network onto the printer. Furthermore the method discussed in Japanese Patent Application Laid Open No. 11 53132 activates the application program on the network computer to open the data file and convert the data file into a raster image. Japanese Patent Application Laid Open No. 11 53132 further discusses a network computer installed printer which prints the data file and a computer network system including the printer. Moreover Japanese Patent Application Laid Open No. 11 53132 discusses a method using Java applet as the application program.

Japanese Patent Application Laid Open No. 2002 287990 discusses a method for installing an application on a device by accessing the device via a web browser and uninstalling the installed application therefrom. However in a case where a plurality of image forming apparatuses exists on a network and an application program is to be introduced and installed on each of the plurality of image forming apparatuses the following problems may arise.

That is an administrator of the system may bear a heavy burden to install an application program on each image forming apparatus. Furthermore considerable time may be required to install an application program on all of the image forming apparatuses.

Furthermore in a case where the application program was installed on all of the image forming apparatuses in order to use the installed application program under a business environment it is necessary to perform settings for each application program.

In this regard in performing a setting for the application program installed on an image forming apparatus it is necessary for an administrator to know what type of application program was installed on which image forming apparatus on the network. The same applies in the case of changing the settings after installation of the application program.

Moreover it is necessary for an administrator to know what type of application program is installed on which image forming apparatus on the network. In addition it is necessary for an administrator to select each image forming apparatus which is a setting file transmission destination and to perform processing for transmitting a setting file to each selected image forming apparatus. As described above with the conventional method described above an administrator may be required to bear a heavy burden.

The present invention is directed to an information processing apparatus configured to allow a user to easily extract an image forming apparatus that has been installed with an application program that is a target of transmitting a setting file. More specifically the present invention is directed to an information processing apparatus configured to allow a user to transmit a setting file for an application program to an appropriate image forming apparatus with a simple operation.

According to an aspect of the present invention an information processing apparatus configured to transmit setting information used in an application program that operates on an image forming apparatus to the image forming apparatus includes an acquisition unit configured to acquire from a plurality of image forming apparatuses application information indicating a type of each application program installed on the plurality of image forming apparatuses an application selection receiving unit configured to receive selection of an application program corresponding to the application information acquired by the acquisition unit a setting information selection receiving unit configured to receive selection of setting information used in the application program whose selection has been received by the application selection receiving unit an apparatus selection receiving unit configured to receive selection of an image forming apparatus as a destination to which to transmit the setting information from among image forming apparatuses installed with the application program whose selection has been received by the application selection receiving unit and a transmission control unit configured to control processing for transmitting to the image forming apparatus whose selection has been received by the apparatus selection receiving unit the setting information whose selection has been received by the setting information selection receiving unit.

Further features and aspects of the present invention will become apparent from the following detailed description of exemplary embodiments with reference to the attached drawings.

Various exemplary embodiments features and aspects of the present invention will now herein be described in detail with reference to the drawings. It is to be noted that the relative arrangement of the components the numerical expressions and numerical values set forth in these embodiments are not intended to limit the scope of the present invention unless it is specifically stated otherwise.

A first exemplary embodiment of the present invention will be described below. illustrates an example of a configuration of a network system according to an exemplary embodiment.

Referring to a PC which is an example of an information processing apparatus stores and executes a setting file transmission tool.

An MFP is an example of an image forming apparatus having various functions such as a facsimile transmission function a copying function and a function as a printer. An MFP and an MFP respectively have substantially similar functions as those of the MFP except for installed applications and a stored setting file.

A network NET is an example of a communication medium. The PC and each of the MFPs through can transmit various information and perform data communication via the NET .

Prerequisites for an environment of each of the MFPs through will be described below with reference to . An application platform hereinafter simply referred to as a platform is an additionally provided software operation environment. The application platform is implemented on a Real Time Operating System RTOS .

The platform includes an interpreter a group of application programming interfaces hereinafter referred to as APIs and a group of frameworks. The platform provides a pseudo operating system OS or a computing platform for software operating on the platform .

The interpreter successively reads interprets and executes a series of command lines including commands included in a predetermined command set. In the case where the command set is used in the same manner as a command set for a central processing unit CPU of hardware the interpreter is especially called a virtual machine .

The APIs and the frameworks provide an access to a resource provided by an actual RTOS existing in a lower layer of the software operation environment or to various resources obtained by abstraction of hardware resources for software operating under the software operation environment. The resources include a context for executing a command by a processor a memory a file system and various input and output units I Os such as a network interface.

Here with respect to the command execution context the software operation environment can manage the command execution context on the interpreter regardless of a multi task mechanism provided by an actual CPU and RTOS. With respect to the memory the software operation environment can independently manage the memory.

The software operating on the platform is serially read interpreted and executed by the interpreter. Thus the command line can be monitored during the processing by the interpreter which can suppress occurrence of an operation that may affect the operation of the system. Furthermore with respect to the access from the software on a software execution environment to various resources an access operation that may affect the operation of the system can be suppressed because the resources are indirectly operated via the APIs and the group of frameworks provided by the platform.

Accordingly an approach of providing in firmware an interpreter and a layer of an environment for executing software including the APIs and the group of frameworks is very useful in partially introducing dynamic software characteristics on firmware in a low cost built in system which is basically required to be statically and fixedly configured.

On the platform an application and an application are provided. The application and the application are executed using an API of the platform .

A setting file transmission tool is a program for transmitting a setting to the MFPs through and operates on an object code execution environment.NET .

Furthermore the PC includes an OS . The MFPs through include the application and the application which operate on the application platform . The application and the application can be a FeliCa authentication application which will be described below. Furthermore the MFPs through include a file receiving module . The file receiving module has a function for receiving a setting file from the setting file transmission tool .

Moreover the MFPs through include an application management module . The application management module manages a status of the application the application and the file receiving module and manages a life cycle of the applications through such as activation and suspension thereof.

Each file utilized by a program for transmitting a setting file used by the application program according to an exemplary embodiment will be described with reference to . In the present exemplary embodiment the file is described in eXtensible Markup Language XML format. The type and the main content of the file will be described below.

A device list file includes information about a device detected on the network using a device information search function . The device information includes data items and values therefor as illustrated in .

The data items primarily include a device detection mode a device status an update date and time a port number a device ID device unique information MAC address an IP address a serial number and a product name firmware information a device name a device spec ID and installed application information. The installed application information is especially significant in the present exemplary embodiment.

The installed application information indicates an installed application program hereinafter simply referred to as an application which has already been installed on the image forming apparatus. More specifically the installed application information includes an application ID an application version an application name an installation date and time an application status and an application type. The installed application information further includes a presence or absence of license and a license status as license information.

The information processing apparatus setting file transmission tool issues a request to the image forming apparatus for sending a device list file. Thus the information processing apparatus can acquire the device list file from the image forming apparatus. The information processing apparatus refers to the received device list file to recognize and manage what type of application program has been installed on each of the MFPs through .

A group list file includes information about a device group. The group list file is generated inside the information processing apparatus to be managed therein. The group list file describes a group name a group description and a device list a device name and a device ID . The information processing apparatus can manage the MFPs through as a group.

An application list file describes application information sent from the image forming apparatus on the network. The application list file is generated inside the information processing apparatus to be managed therein. The application list file describes an application ID an application version an application name an application type and license information as the application information acquired by referring to the device list file. An administrator can further include in the application list file an application description and information about each resource.

A transmission target application file includes information about an application program to which the information processing apparatus transmits a setting file therefor an application version and information about a file to be transmitted. The transmission target application file is previously generated inside the information processing apparatus to be managed therein.

A transmission history file is a history file describing a result of control by the information processing apparatus for transmitting a setting file. The transmission history file is generated when transmission control is performed by the information processing apparatus to be thereafter managed as will be described in detail below. The PC is an example of the information processing apparatus.

As illustrated in the PC can transmit the following four types of setting files to the image forming apparatus.

The setting file in a plaintext format unique to a transmission target application is described in a KEY VALUE format.

The setting file in a ZIP format unique to a transmission target application is described in a KEY VALUE format.

The setting file 3DES encrypted file unique to a transmission target application is described in a KEY VALUE format.

The authentication table file includes user data information described in a comma separated value CSV format.

When the PC has selected any of the above files 1 through 4 as a file to be transmitted that file is restored into a plaintext format. Then it is determined whether the file is appropriate as a file to be transmitted. If it is determined that the file is appropriate as a file to be transmitted then the PC transmits the file. More specifically the determination as to whether the file is appropriate as a file to be transmitted is performed by determining whether a required license key is provided to the transmission target application installed on the MFP.

Referring to the setting file transmission tool of the PC setting file sending apparatus includes a device information search function a device information management function a transmission target application management function a setting file transmission function and a transmission result management function .

The device information search function is a function for searching for an MFP on the network and acquiring the device information from the detected MFP. The device information management function is a function for generating a device list file for each of the MFPs through based on the acquired device information and managing the generated device list file.

The transmission target application management function is a function for generating an application list file based on the application information acquired from the MFPs through and managing the generated application list file and a previously generated transmission target application file.

The setting file transmission function is a function for transmitting a setting file that has been designated by a user to an MFP that has been designated by the user. The transmission result management function is a function for generating a transmission history file describing a result of transmission processing performed using the setting file transmission function and managing the generated transmission history file.

The file receiving module of the MFP setting file receiving apparatus includes an application control function a file receiving function and a file writing function .

The application control function is a function for activating an installed application acquiring information about a storage destination a directory or a file path of the application by communicating with the application and exiting from the application. The file receiving function is a function for performing a data communication by establishing a session with the information processing apparatus to receive a setting file. The file writing function is a function for writing the setting file sent from the information processing apparatus to the storage destination of the setting file whose information has been acquired from the application by communicating therewith.

Referring to in step S the setting file transmission tool issues a request for acquiring device information to the PC using a predetermined search protocol. After receiving the device information acquisition request from the setting file transmission tool the PC executes the device information search function to perform the processing of step S.

In step S the MFP sends device information and application information to the PC . More specifically the MFP sends the information illustrated in to the PC via the NET . The setting file transmission tool of the PC updates the device list file using the information acquired in step S.

In step S the setting file transmission tool transmits the file receiving module to the MFP and instructs the MFP to install the transmitted file receiving module thereon. A modification related to the above processing will be described below.

In step S the MFP sends an installation result to the PC . The setting file transmission tool updates the device list file based on the received installation result.

In this regard for example when the file receiving module is successfully installed on the MFP the setting file transmission tool writes information describing that the file receiving module has been successfully installed on the MFP into an entry for the MFP in the device list file. On the other hand if the file receiving module has not been successfully installed on the MFP the setting file transmission tool writes information describing that the file receiving module has not been successfully installed on the MFP in an entry for the MFP in the device list file. The above information can be displayed on a display of the PC .

In step S the setting file transmission tool sends a command for changing a status of the transmission target application to the application in the MFP . For example the setting file transmission tool issues an instruction for suspending a service currently run by the application for reading the setting file.

In step S the MFP sends a result of the status change to the PC . For example the MFP sends to the PC a result indicating that the service has not been successfully suspended or that the service has been successfully suspended. After step S the device list file is updated and at least one setting file is selected at the PC . In step S an application ID a file name an MD5 encryption flag and a setting file are sent from the PC to the MFP . After step S the transmitted files are stored in a target application area. Optionally an application to be transmitted is activated in the MFP . In step S a result is transmitted from the MFP to the PC . Then in step S an instruction for suspending a file receiving module is sent from the PC to the MFP . In step S a transmission result is transmitted from the MFP to the PC .

The device list screen is displayed when the user selects a device list tab or immediately after the setting file transmission tool is activated. When the setting file transmission tool is activated the setting file transmission tool performs the processing in steps S through S and updates the device list file.

In the device list screen all of the MFPs whose information has been acquired in step S and step S via the network are displayed as a list. Here the MFPs through are included in the list of MFPs displayed on the device list screen .

When the user arbitrarily selects the MFP in the device list applications already installed on the selected MFP are displayed as a list in an installed application list field . The displayed installed application list is based on the device information particularly the application information described therein acquired from the MFPs through .

That is the user can recognize and find the applications installed on the selected device using the device on the network as a key. More specifically when the user selects the MFP the PC extracts the information related to the installed applications i.e. information such as an application name from the device list file which has been previously acquired and then displays the extracted information.

As illustrated in it can be known that an IC Card Authentication FeliCa Ver. 3.10 and Ver. 1.10 application are installed on the MFP although the name of the installed application is partially abbreviated in .

When the user selects or presses an application list tab the application list screen is displayed based on a content of the application list file stored by the device information management function . The applications are displayed as any of three types of applications namely a login application an install application or a general application based on a value for the application type stored in the application list file.

When the user selects an application name displayed in a pane displayed in a leftmost portion of the screen information about the selected application is acquired from among the application list in and then the acquired application information is displayed in an upper right portion of the screen.

In a lower right display field of the screen a list of MFPs on which the currently selected application has already been installed is displayed whose information can be acquired with reference to the device list file.

That is the user can recognize and find the MFP on which the selected application has already been installed using the application as a key. More specifically the application list is previously provided on the PC and the PC displays the applications in the application list in the pane . When the user selects any of the displayed applications the PC can extract an MFP on which the application in the device list has been installed and can display the extracted MFP using the selected application as a key.

When the user presses a setting item list tab the setting item list screen displays contents of the application list file classified based on information about a transmission target application. Using an application that uses a setting file to be transmitted as a key the setting item list screen displays a list of MFPs on which the application that uses the setting file to be transmitted has been installed.

Thus the user can easily select an MFP transmission destination from among the MFPs that have been installed with the selected application displayed in the application list. That is when the user selects the setting file the setting file transmission tool detects the selected setting file. Then the setting file transmission tool acquires a name of a path to the detected setting file.

Then the setting file transmission tool searches the transmission target application file to determine which application name the path name of the setting file corresponds to. When the application name is determined the setting file transmission tool serially searches the installed application information using the determined application name as a key to identify a name of the device on which the application having the determined application name is installed.

Here a plurality of device names can be determined. In the MFP installed with the IC card authentication FeliCa Ver. 3.0 which is upwardly compatible with IC card authentication FeliCa Ver 2.10 has been determined.

As a rule with respect to a setting for a top tree the application list is fixedly displayed on a top tree node of compliant application .

As a rule with respect to a major item the major item tree field displays an application name in Japanese characters of a setting file transmission target application. With respect to the application name to be displayed an application display name of the compliant application file is set. In a bottom layer a non compliant application is fixedly displayed.

As a rule with respect to a medium item the medium item tree field displays an application name bundle and an application version . An application version that is not a setting file transmission target is displayed and controlled in the following manner.

With respect to a lower order version application the application name and the application version are grayed out indicating that the application version is not the target of the setting file transmission. With respect to a higher order version the application name and the application version are effectively displayed to indicate that the application version is the target of the setting file transmission.

The content of checking performed when the setting file to be transmitted is selected is based on a latest version that has been registered as a compliant application. In determining whether an application version is a higher order version or a lower order version an earliest version and a latest version of the application that has been registered in the transmission target application file are compared with the version of the application that the setting file corresponds to.

As a rule with respect to a minor item the minor item displays a setting file name . The setting file name to be displayed corresponds to the application version of the compliant application file . The setting file transmission tool acquires the setting file name and displays the acquired setting file name. A plurality of setting file names can be displayed.

As a rule with respect to a non compliant application tree the non compliant application tree displays all the applications not existing in the compliant application file in a grayed out state. When the user selects any of the application name displayed in the leftmost field of the screen application information about the selected application is acquired from the application list file and then the acquired application information is displayed in the upper right field of the screen. In a lower right portion of the screen a content of the transmission history file is displayed.

That is a pane leftmost portion of the screen displays a list of applications and the upper right field of the screen displays information about the selected application. A lower right field displays history information about a result of a latest transmission of the selected setting file.

Via the screen in the user can search for and transmit an application to which the selected setting file can be transmitted from among the applications on the network. When a value no good NG is displayed as a result of a latest transmission the user can retransmit the setting file by pressing a retransmit button. When a value NG is not displayed as a result of a latest transmission the retransmit button is grayed out the user cannot press the retransmit button .

Referring to in step S the setting file transmission tool receives selection of the file name of the file to be transmitted. Here the setting file transmission tool detects that the setting item list tab has been selected by the user. Thus the setting file transmission tool detects that the file name of the setting file to be transmitted has been selected by the user. More specifically the user selects the item .

In step S the setting file transmission tool detects that the setting file to be transmitted has been selected by the user from a tool bar via a screen illustrated in .

When the user selects the setting file name via a setting file selection screen and presses a next button the setting file transmission tool recognizes an application name of an application compliant with the selected setting file an application version of the selected application and the selected setting file to be transmitted. Then the screen returns to the screen in .

In step S the setting file transmission tool performs processing for checking the setting file. When the user presses the next button the processing in step S starts.

More specifically in step S using the transmission target application management function the setting file transmission tool compares a content of the selected setting file with information about the setting file described in the transmission target application file to determine if the setting files match each other. In the case of an encrypted file the setting file transmission tool decrypts the file and checks the content of the file using the transmission target application management function .

If it is determined that the setting files do not match each other in step S then the setting file transmission tool displays an error dialog using the transmission target application management function . In this case the setting file transmission tool cannot transmit a file with respect to which an error has been determined.

In the case where the selected application version is later than the version stored in the transmission target application list in comparing the contents of the setting files the setting file transmission tool uses information about an application included in the transmission target application list whose version is closest to the selected application version for comparison. Thus the setting file transmission tool is not required to frequently update the list at every updating of an application.

In step S the setting file transmission tool performs processing for displaying the transmission destination device via the screen . Here the setting file transmission tool reads the selected file. In this processing using the transmission target application management function the setting file transmission tool reads the device list file that has previously been acquired from the MFP. Further the setting file transmission tool using the transmission target application management function displays a list of devices on which the selected application has been installed. Users can input a Service Management Service SMS password described below via a password dialog .

When the user selects a group name the setting file transmission tool using the transmission target application management function reads the group list file to filter the device list to be displayed. That is the setting file transmission tool extracts a device belonging to a specific group name from the device list file.

In step S the setting file transmission tool performs processing for detecting a selected transmission destination device. In this processing the user selects a device to which the setting file is to be transmitted from among the list of devices to which the setting file can be transmitted. Here the user is required to enter a password to select the device to which the setting file is to be transmitted. More specifically the user is required to enter a Service Management Service SMS password registered on the device listed in the device list .

When the user enters the SMS password the setting file transmission tool communicates with the selected device using the device information management function to check if the entered SMS password is appropriate. If the user is not successfully authenticated with the entered SMS password the setting file transmission tool does not determine that the selected device is the target of the setting file transmission.

In step S the setting file transmission tool performs processing for transmitting a setting file. When the user presses the next button via the screen a screen is displayed. The screen displays a setting file transmission dialog . The setting file transmission dialog displays a device to which the selected setting file can be transmitted. In this processing the setting file transmission tool transmits the selected setting file to the file receiving module of the setting file transmission destination device.

In step S the setting file transmission tool performs processing for receiving a transmission result. In this processing the setting file transmission tool receives a transmission result from the file receiving module . The setting file transmission tool updates the transmission history file based on the received transmission result.

If a transmission history of the selected setting file exists in the transmission history file then the setting file transmission tool erases the existing transmission history and overwrites the transmission history with the received transmission result. Further the setting file transmission tool updates the transmission result in the device list file. A transmission result includes information about a status of installation of an application on the device success or failure of the install and the application version of the installed application .

In step S the setting file transmission tool performs processing for acquiring a path to the setting file. In this processing the setting file transmission tool acquires a path to the setting file set by the user via the setting file selection screen .

In step S the setting file transmission tool performs processing for checking the file path. More specifically the setting file transmission tool using the transmission target application management function determines whether the setting file path acquired in step S has been set. If it is determined in step S that the setting file path acquired in step S has not been set PATH NOT SET in step S then the setting file transmission tool advances to step S. In step S the setting file transmission tool displays an error dialog error message .

In this regard in terms of security the user may desire to change the path to location of the setting file for the application installed on the MFP. Accordingly in the present exemplary embodiment the location of the setting file path to the setting file can be changed.

In step S the setting file transmission tool performs processing for determining whether the setting file exists. More specifically the setting file transmission tool using the transmission target application management function determines whether the setting file exists in the path acquired in step S. If it is determined in step S that the setting file does not exist in the path acquired in step S DOES NOT EXIST in step S then the setting file transmission tool advances to step S. In step S the setting file transmission tool displays an error dialog.

In step S the setting file transmission tool determines whether the setting file is empty. More specifically the setting file transmission tool checks the content of the file which has been determined to exist in step S using the transmission target application management function . If it is determined in step S that the setting file is empty 0 BYTE in step S then the setting file transmission tool advances to step S. In step S the setting file transmission tool displays an error dialog.

In step S the setting file transmission tool performs processing for determining whether the application version of the selected application is a higher order version. More specifically the setting file transmission tool determines the version of the selected application matches any application version described in the transmission target application file.

If it is determined in step S that the version of the selected application does not match any application version described in the transmission target application file HIGHER ORDER APPLICATION in step S then the setting file transmission tool advances to step S. On the other hand if it is determined in step S that the version of the selected application matches an application version described in the transmission target application file then the setting file transmission tool acquires the setting information transmission target application file information from the transmission target application file.

In step S the setting file transmission tool sets the latest version application as a check reference version application. The setting file transmission tool using the transmission target application management function compares the version of the selected application with the version information described in the transmission target application file to acquire the setting information transmission target application file information based on which the setting file transmission tool performs the transmission processing.

If it is determined in step S that the version of the selected application is later than the latest version of the application described in the transmission target application file the latest version is set for the setting information. More specifically if versions 2.0 2.1 and 3.0 exist as versions of the transmission target file and if the version of the selected application is 4.0 then the setting file transmission tool acquires the setting information for version 3.0.

If it is determined in step S that the version of the selected application is later than an earliest version and earlier the latest version of the application described in the transmission target application file the setting file transmission tool acquires the setting information for a version immediately earlier than the version of the selected application. More specifically if versions 2.0 2.1 and 3.0 exist as versions of the transmission target file and if the version of the selected application is 2.3 then the setting file transmission tool acquires the setting information for version 2.1.

In step S the setting file transmission tool performs processing for acquiring the setting information. In this processing the setting file transmission tool acquires the setting information determined in steps S and S.

In step S the setting file transmission tool checks the file for error. In this processing the setting file transmission tool using the transmission target application management function checks the content of the file acquired in step S based on the setting information acquired in step S. If it is determined in step S that the file is defective a case where the file includes no key or other errors ERROR FOUND in step S then the setting file transmission tool advances to step S. In step S the setting file transmission tool displays an error dialog.

In step S the setting file transmission tool performs processing for displaying the transmission destination device selection screen. In this processing the setting file transmission tool using the transmission target application management function reads the device list file and displays a list of devices installed with the selected application based on the information acquired by reading the device list file. When the user selects a group name the setting file transmission tool using the transmission target application management function reads the group list file and filters the list of devices to be displayed based on the information acquired by reading the group list file.

Referring to in step S the setting file transmission tool performs processing for acquiring a transmission destination device. In this processing the setting file transmission tool using the transmission target application management function acquires a list of transmission destination device selected by the user via the setting file selection screen.

In step S the setting file transmission tool performs processing for generating a Message Digest algorithm 5 MD5 value. In this processing the setting file transmission tool using the transmission target application management function generates an MD5 value for the setting file selected by the user via the setting file selection screen.

In step S the setting file transmission tool using the transmission target application management function calls the setting file transmission function to transmit the setting file to the transmission destination device.

In step S the setting file transmission tool performs processing for checking for a file receiving module for its presence. In this processing the setting file transmission tool using the transmission target application management function checks whether the file receiving module is installed on the transmission destination device. If it is determined in step S that no file receiving module is installed on the transmission destination device then the setting file transmission tool advances to step S. In step S the setting file transmission tool displays an error dialog.

In step S the setting file transmission tool performs processing for checking for a status of the transmission destination application. In this processing the setting file transmission tool using the transmission target application management function checks for a status of the transmission destination application.

Whether the setting file can be transmitted is determined based on a value for a transmission type in the transmission target application file. More specifically if the value for the transmission type is set at 0 in the case other than cases where the application has been suspended or installed then the setting file transmission tool advances to step S to display an error dialog. On the other hand if the value for the transmission type is set at 1 in the case other than cases where the application has been already activated or suspended after its restart then the setting file transmission tool advances to step S to display an error dialog.

In step S the setting file transmission tool performs processing for activating the file receiving module . In this processing the setting file transmission tool using the transmission target application management function activates the file receiving module installed on the transmission destination device to start the transmission of the setting file. If the file receiving module is not successfully activated then the setting file transmission tool determines that an activation error has occurred and advances to step S. In step S the setting file transmission tool displays an error dialog. On the other hand if it is determined in step S that the file receiving module has been successfully activated then the setting file transmission tool advances to step S.

In step S the setting file transmission tool performs processing for acquiring an authentication character string. In this processing the setting file transmission tool performs an SMS user authentication for the transmission destination device before transmitting the setting file thereto. The setting file transmission tool acquires an authentication character string required in performing the authentication.

In step S the setting file transmission tool performs SMS user authentication processing. In this processing the setting file transmission tool using the transmission target application management function performs processing for authenticating the user for the transmission destination device based on the authentication character string acquired in step S and an SMS password entered by the user. If the user is not successfully authenticated then the setting file transmission tool determines that an authentication error has occurred and advances to step S. In step S the setting file transmission tool displays an error dialog.

In step S the setting file transmission tool transmits the selected setting file. In this processing the setting file transmission tool using the transmission target application management function transmits the setting file to the file receiving module of the transmission destination device.

In this processing the setting file transmission tool sends information such as the application ID the file name file path the MD5 value and an encryption flag in addition to the selected setting file to the file receiving module of the transmission destination device.

Here the file receiving module of the transmission destination device receives the above information and the setting file and then transmits the received setting file to the transmission destination application based on the received information. Then the file receiving module sends a result of the transmission information about whether the transmission has been successfully completed to the setting file transmission tool .

If a value NG is indicated in the list of transmission results field displayed when the user selects the setting item list tab then the user can click the retransmit button displayed on the current screen. On the other hand if a value NG is not indicated in the list of transmission results field the retransmit button is displayed in a grayed out state. In this case the user cannot click the retransmit button.

Referring to in step S the user selects the name of the setting file to be transmitted. In this processing the user can click the setting item list tab and then select the name of the setting file to be transmitted. Then the user selects the retransmit button.

The following information and file are set to be displayed on the setting file selection screen which is displayed when the user selects the retransmit button. That is the setting file selection screen displays the name of the selected application the version of the selected application the selected file to be transmitted and the information about the device for which the value NG is described in the displayed list of transmission results.

In step S the setting file transmission tool checks the status of communication with the transmission destination device. When the user selects the retransmit button the setting file transmission tool using the transmission target application management function checks for the communication status with respect to the NG device the device for which the value NG is described in the displayed list of transmission results to which the setting file is to be transmitted. If the communication with the retransmission destination device is not available the setting file transmission tool displays an error dialog.

In step S the user selects the file to be transmitted. More specifically in this processing the user selects the setting file to be transmitted from among the setting files stored in the MFP on which the setting file transmission tool is installed via the setting file selection screen.

At this time the setting file transmission tool displays a previously acquired previously transmitted file path which is stored in the transmission history file in a default state. After selecting the setting file to be transmitted the user selects the next button.

In step S the setting file transmission tool performs processing for checking the setting file. More specifically in this processing the setting file transmission tool using the transmission target application management function compares the content of the selected setting file with the information described in the setting file which is described in the transmission target application file to determine if the setting files match each other. Here if the setting file has been encrypted the setting file transmission tool decrypts the encrypted setting file before checking its content. If the setting files do not match each other then the setting file transmission tool displays an error dialog. In this case the setting file transmission tool does not transmit the selected setting file.

In the case where the selected application version is later than the version stored in the transmission target application list in comparing the contents of the setting files the setting file transmission tool uses information about the application included in the transmission target application list whose version is closest to the selected application version for the comparison. Thus the setting file transmission tool is not required to frequently update the list at every updating of an application.

In step S the setting file transmission tool displays the transmission destination device. After the user has selected the setting file to be transmitted the setting file transmission tool using the transmission target application management function reads the device list file and displays the list of devices installed with the selected application based on the information acquired by reading the device list file. Here the device whose communication with the information processing apparatus has been determined available in step S is already set as a transmission destination device and can be excluded from the transmission destination device list.

In step S the user selects the transmission destination device. In this processing the user verifies the device list displayed in step S all of the devices in the device list are set as a transmission destination device in a default state and then selects the next button.

In step S the setting file transmission tool receives a result of the transmission from the file receiving module . The setting file transmission tool updates the transmission history file based on the received transmission result. Here the setting file transmission tool overwrites only the information about the device to which the setting file has been retransmitted with the information described in the received transmission result. Then the setting file transmission tool updates the device list file based on the received information described in the transmission result.

The following setting information can be easily set by the user in the case of the above described application program for performing a user authentication with an integrated circuit IC card.

Authentication server setting information includes information such as a computer name and address of an authentication server that makes an inquiry about whether a login name and a password read from the IC card are appropriate. Here an authentication server timeout refers to a wait time until an error is detected based on a timeout occurring when no reply is sent from the authentication server.

As the setting information the administrator of the system can perform a setting for authentication server setting information an authentication server timeout and the following information.

 Card reading position information describes information about a position of the IC card at which the information required for user authentication is read by the above described IC card authentication application program installed on the MFP. A polling time refers to information about a time interval for issuing a request for reading the IC card with an IC card reader. A user code start refers to an address at which the reading of the user ID starts. Another address is provided with respect to the password.

A user code length refers to information about the length of the character string of the user ID. Another length is provided with respect to the password. The above information is a mere example and a larger volume of setting information is required in an actual operation of the system.

The present invention is not limited to the above described exemplary embodiment. That is the present invention can be implemented as a system an apparatus a program or a storage medium. More specifically the present invention can be applied to a system including a plurality of devices and to an apparatus that includes one device.

Furthermore to achieve a higher security level the application program installed on the MFP can be installed on each of the MFPs through in a mutually different directory path. However in this case since it is necessary for the administrator of the system to know in which directory path the transmission target application program is installed with respect to each of the MFPs through it may be inappropriate to send the setting files at once to the plurality of MFPs the MFPs through .

In order to address this the present invention can provide a method for saving an administrator of the system from taking the trouble of searching for an MFP installed with the application program to which the setting file is to be transmitted and a method for transmitting the setting file for the application program to an appropriate MFP with a simple operation.

A second exemplary embodiment of the present invention will be described below. In the first exemplary embodiment it is assumed that the MFP to which the setting file is to be transmitted is previously equipped with the file receiving module before the setting file transmission tool sends the setting file for the application thereto. However the present invention can transmit the file receiving module itself to an MFP that does not previously include the file receiving module .

A modification for transmitting a setting file and the file receiving module will be described in detail below with reference to a flow chart illustrated in .

Referring to in step S the setting file transmission tool determines whether the transmission destination MFP previously includes the file receiving module . More specifically in this processing the setting file transmission tool using the transmission target application management function determines whether the file receiving module has been already installed on the transmission destination MFP. If it is determined that the file receiving module has been already installed on the transmission destination MFP then the setting file transmission tool further checks the version of the installed file receiving module .

If it is determined in step S that no file receiving module has been installed on the transmission destination MFP or if the version of the installed file receiving module is old then the setting file transmission tool advances to step S. On the other hand if it is determined in step S that the file receiving module of an appropriate version has been installed on the transmission destination MFP then the setting file transmission tool advances to step S.

In step S the setting file transmission tool transmits the file receiving module to the transmission destination MFP.

In step S the setting file transmission tool performs processing for checking for a status of the transmission destination application. In this processing the setting file transmission tool using the transmission target application management function checks for a status of the transmission destination application.

Whether the setting file can be transmitted is determined based on a value for a transmission type in the transmission target application file. More specifically if the value for the transmission type is set at 0 in the case other than cases where the application has been suspended or installed then the setting file transmission tool determines that an error has occurred. In this case the setting file transmission tool advances to step S to display an error dialog. On the other hand if the value for the transmission type is set at 1 in the case other than cases where the application has been already activated or suspended after its restart then the setting file transmission tool determines that an error has occurred. In this case the setting file transmission tool advances to step S to display an error dialog. If it is determined in step S that no error has occurred then the setting file transmission tool advances to step S.

In step S the setting file transmission tool performs processing for activating the file receiving module . In this processing the setting file transmission tool using the transmission target application management function activates the file receiving module installed on the transmission destination device to start the transmission of the setting file. If the file receiving module is not successfully activated then the setting file transmission tool determines that an activation error has occurred and advances to step S. In step S the setting file transmission tool displays an error dialog. On the other hand if it is determined in step S that the file receiving module has been successfully activated then the setting file transmission tool advances to step S.

In step S the setting file transmission tool performs processing for acquiring an authentication character string. In this processing the setting file transmission tool performs an SMS user authentication for the transmission destination device which is required for performing the transmission. The setting file transmission tool acquires an authentication character string required in performing the authentication. If the authentication character string has not been successfully acquired then the setting file transmission tool advances to step S. In step S the setting file transmission tool displays an error dialog. On the other hand if the authentication character string has been successfully acquired then the setting file transmission tool advances to step S.

In step S the setting file transmission tool performs SMS user authentication processing. In this processing the setting file transmission tool using the transmission target application management function performs processing for authenticating the user for the transmission destination device based on the authentication character string acquired in step S and an SMS password entered by the user. If the user is not successfully authenticated then the setting file transmission tool determines that an authentication error has occurred and advances to step S. In step S the setting file transmission tool displays an error dialog. On the other hand if the user is successfully authenticated then the setting file transmission tool advances to step S.

In step S the setting file transmission tool transmits the selected setting file. In this processing the setting file transmission tool using the transmission target application management function transmits the setting file to the file receiving module of the transmission destination device.

In this processing the setting file transmission tool sends information such as the application ID the file name file path the MD5 value and an encryption flag in addition to the selected setting file to the file receiving module of the transmission destination device.

Here the file receiving module of the transmission destination device receives the above information and the setting file and then transmits the received setting file to the transmission destination application based on the received information. Then the file receiving module sends a result of the transmission information about whether the transmission has been successfully completed to the setting file transmission tool .

Now a modification of the above described exemplary embodiment for installing the file receiving module the processing performed in step S in will be described in detail below. is a flow chart illustrating an example of processing for transmitting the file receiving module .

Each of and illustrates an example of a display screen provided by the setting file transmission tool which is displayed on the PC . The setting file transmission tool performs the processing in the following manner.

Referring to in step S the setting file transmission tool displays a list of devices detected as a result of the search for devices. In the device list a device that is not installed with the file receiving module is displayed with an icon for the device MFP as illustrated in to indicate that the MFP corresponding to such an icon is not installed with the file receiving module .

In step S the setting file transmission tool detects that the user has selected a device that is not installed with the file receiving module . Here the user selects the device from among those in the device list. As illustrated in an MEAP installed machines filed in a triangular mark is provided with respect to the device that is not installed with the file receiving module .

In step S the user issues an instruction for transmitting the file receiving module . In this processing the user presses a transmit receiving module button to instruct the transmission of the file receiving module .

In this case the setting file transmission tool displays a dialog to allow the user to verify whether to start the processing. If the user presses a YES button then the setting file transmission tool continues the processing. On the other hand if the user presses a NO button then the setting file transmission tool ends the processing.

In step S the setting file transmission tool transmits the file receiving module to the selected transmission destination device to be installed thereon.

If the file receiving module has been successfully installed as a result of the installation processing in step S then the setting file transmission tool updates the device list and an MEAP installed machines field for the selected transmission destination device as illustrated in to allow the user to verify that the file receiving module is successfully installed on the selected transmission destination device. After this processing the setting file transmission tool continues the processing in step S and subsequent steps .

Referring to a CPU is in communication with each unit and apparatus via an internal bus . The CPU controls the MFP MFP and MFP . The CPU loads programs shown in into a memory .

A display apparatus displays a user interface on a touch panel operation panel provided thereon. A user can issue an instruction for performing desired processing via a user interface displayed on the display apparatus .

A communication apparatus sends and receives information to perform data communication with the PC via the NET . A scanner apparatus reads a paper document.

The CPU loads information and data program from a memory which is a mass storage device that can temporarily store various programs stored on the MFPs through on a random access memory RAM not illustrated and executes the loaded program.

Referring to each component of the PC is mutually connected via a system bus . The software block of the PC is stored on a hard disk . The program is read and executed with a CPU when necessary.

The CPU performs processing according to a control program stored on a program memory PMEM the hard disk or a floppy disk FD .

The CPU selects and loads a program for transmitting a setting file as necessary from the hard disk onto the PMEM . Then the CPU executes the program on the PMEM . Data input via a keyboard is stored on the PMEM which is also a text memory as code information.

An image memory IMEM temporarily stores image data. An image input output control unit performs control of input and output of image data and user setting information sent to and received from a facsimile machine .

The PC via a network interface I F receiving unit that connects the PC to the NET sends and receives information and data such as a setting file with the MFPs through . The facsimile machine is connected to an image input output control unit which is connected to the image input output control unit .

User setting information read by the facsimile machine is temporarily stored on the PMEM . Then the user setting information is converted into data of a format adapted to be displayed on a screen of the PC and loaded on a video random access memory VRAM . Then the user setting information is displayed on a cathode ray tube CRT . Data of document to be sent is rasterized on the IMEM as bitmap data. Then the image input output control unit performs control for outputting the bitmap data to the image input output unit connected to the facsimile together with function designation information.

Input devices such as the keyboard and a pointing device PD are connected to an input control unit . The operator administrator or user of the PC operates the keyboard to issue an operation command for the system.

The PD includes a mouse via which the user can select process instruct image information graphic data text data or numeric data via the CRT . The user can arbitrarily move a mouse cursor displayed on the CRT in X and Y directions to select a menu or select or edit image data graphic data text data or numeric data.

Data displayed on the CRT is rasterized on the VRAM as bitmap data. In the case of graphic data a graphic pattern corresponding to the location and attribute information of the graphic data is rasterized on the VRAM . The graphic data can be displayed on the CRT by software according to an operation performed via a cursor for selecting graphic data directly in a display area of the VRAM .

The PC further includes an external storage device control unit the hard disk and the FD which store various data such as image data graphic data text data or numeric data.

The CPU loads from the hard disk or the FD a control program such as the setting file transmission tool on the VRAM and executes the read program.

As described above according to an exemplary embodiment the PC which is an example of an information processing apparatus transmits setting information for an application program operating on the MFP which is an example of an image forming apparatus to the MFP .

Components such as an acquisition unit an apparatus selection receiving unit a setting information selection receiving unit an apparatus selection receiving unit and a transmission control unit can be implemented as a program. For example an apparatus selection receiving unit a setting information selection receiving unit an apparatus selection receiving unit and a transmission control unit can be implemented as an apparatus selection receiving module a setting information selection receiving module an apparatus selection receiving module and a transmission control module respectively. Furthermore a transmission history management unit and a receiving function program transmission unit can be implemented as a program as a transmission history management module and a receiving function program transmission module respectively.

Moreover a retransmission destination device selection receiving unit can be implemented as a program as retransmission destination device selection receiving module. Furthermore the setting file transmission tool transmits an application that operates on the image forming apparatus.

According to an exemplary embodiment having the above described configuration a user can easily extract an image forming apparatus that has been installed with an application program that is a target of transmitting a setting file. Furthermore according to an exemplary embodiment a user can transmit the setting file for the application program to an appropriate image forming apparatus with a simple operation.

According to an exemplary embodiment of the present invention even in the case where the image forming apparatus does not have a function for receiving the setting file a function module for receiving a setting file is previously transmitted to and installed on the image forming apparatus. Accordingly the present invention can be applied to an image forming apparatus that is not compliant with a setting file receiving function.

Thus the present invention can be implemented on various types of image forming apparatuses in various different user environments which can reduce operation costs for the image forming apparatus.

While the present invention has been described with reference to exemplary embodiments it is to be understood that the invention is not limited to the disclosed exemplary embodiments. The scope of the following claims is to be accorded the broadest interpretation so as to encompass all modifications equivalent structures and functions.

This application claims priority from Japanese Patent Application No. 2007 111936 filed Apr. 20 2007 which is hereby incorporated by reference herein in its entirety.

