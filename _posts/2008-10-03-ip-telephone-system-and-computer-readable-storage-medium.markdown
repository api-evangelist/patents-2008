---

title: IP telephone system and computer readable storage medium
abstract: An IP telephone terminal includes an identification data receiving unit that receives, over an Internet, identification data identifying another IP telephone terminal. A communicating unit establishes IP telephone communications with the other IP telephone terminal identified by the identification data via the Internet. An IP telephone function controlling unit controls execution of an IP telephone function used to implement a telephone call with the other IP telephone terminal via a communicating unit that establishes IP telephone communications with the other IP telephone terminal. A terminal data acquiring unit acquires terminal data included in the identification data when acquisition data is determined to be included in the identification data. A process data transmission controlling unit controls transmission of a process data to the other IP telephone terminal, the process data being data used in the function identified by the terminal data acquired by the terminal data acquiring unit.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08233473&OS=08233473&RS=08233473
owner: Brother Kogyo Kabushiki Kaisha
number: 08233473
owner_city: Nagoya-shi, Aichi-ken
owner_country: JP
publication_date: 20081003
---
This application claims priority from Japanese Patent Application Nos. 2007 260217 filed Oct. 3 2007 and 2008 094055 filed Mar. 31 2008. The entire content of each of these priority applications is incorporated herein by reference.

The present invention relates to an IP telephone terminal an IP telephone program an IP telephone collaborative program an IP telephone system a computer readable storage medium.

Internet Protocol IP telephone systems such as Skype have become commonplace in recent years. The IP telephone system can be used simply by installing an IP telephone application on a personal computer or other network terminal where the IP telephone application is software developed by the IP telephone provider for originating and receiving calls and implementing voice communications. Skype which offers a free IP telephone application and free calls has particularly enjoyed much popularity. One factor enabling Skype to offer free calls may be its peer to peer communications which eliminate the need for a server.

Japanese unexamined patent application publications Nos. 2005 192086 and 2005 080025 disclose related technologies for IP telephones.

However IP telephone systems such as Skype cannot recognize data for another IP telephone terminal when communicating with the other terminal via an IP telephone call. Hence even when the other caller is using an IP telephone terminal equipped with functions other than a telephone function the user of the IP telephone terminal cannot take advantage of these functions. In other words the resources of the IP telephone system are not effectively utilized and therefore are wasted.

The Problems to Be Solved by the Invention section of Japanese unexamined patent application publication No. 2005 192086 describes a convenient communication system in which a communication apparatus can execute a function not supported by the communication apparatus itself but possessed by another device. However there is no description of a structure that can resolve the above problem that is how to recognize data for the other device and the functions possessed thereby.

Specifically Japanese unexamined patent application publication No. 2005 192086 describes an IP telephone system having a server that registers information on network terminals. With this system each transceiver terminal is provided with a function for referencing the information registered on the server. Therefore the user can acquire information on other terminals and can transmit data that the other terminals can process.

This technology may be incorporated in an IP telephone system such as Skype by introducing a server into the system in order to register information on external terminals. The server could be referenced to acquire information on the external terminals. However connecting to a server makes the system more complex and expensive which would have a great impact on a system such as Skype that charges little or no usage fees.

The description in 0019 of Japanese unexamined patent application publication No. 2005 080025 asserts that a transmitting device transmitting images and a receiving device receiving the images can identify which communication method is supported by both parties using SDP media stream descriptions expanded by an SIP message but this technology does not sufficiently resolve the problem described above.

In view of the foregoing it is an object of the present invention to provide an IP telephone terminal IP telephone program and IP telephone system capable of effectively utilizing rather than wasting the resources of the IP telephone system by facilitating an IP telephone terminal in utilizing the functions on another IP telephone terminal during IP telephone communications on an IP telephone system such as Skype.

It is another object of the present invention to provide an IP telephone collaborative program IP telephone system and method of controlling an IP telephone system capable of recognizing terminal data on a network terminal itself or on a telephone terminal connected to the network terminal without use of a server even on an IP telephone system such as Skype.

In order to attain the above and other objects the invention provides an IP telephone terminal. An IP telephone terminal includes an identification data receiving unit a communicating unit an IP telephone function controlling unit a determining unit a terminal data acquiring unit and a terminal data acquiring unit. The identification data receiving unit receives over an Internet identification data identifying another IP telephone terminal. The communicating unit establishes IP telephone communications with the other IP telephone terminal identified by the identification data via the Internet. The IP telephone function controlling unit controls execution of an IP telephone function used to implement a telephone call with the another IP telephone terminal via the communicating unit. The determining unit determines the identification data received by the identification data receiving unit. The terminal data acquiring unit acquires terminal data associated with the identification data transmitted from the other IP telephone terminal over the Internet in case the determining unit determines that the terminal data identifying functions that the other IP telephone terminal can control is associated with the identification data received by the identification data receiving unit. The process data transmission controlling unit controls transmission of a process data to the other IP telephone terminal via the IP telephone communications where the process data is data used in the function identified by the terminal data acquired by the terminal data acquiring unit.

According to another aspect the present invention provides a computer readable storage medium. The computer readable storage medium stores a computer executable program for controlling a computer operable to control an IP telephone terminal. The IP telephone terminal includes an identification data receiving unit a communicating unit an IP telephone function controlling unit. The identification data receiving unit receives over an Internet identification data identifying another IP telephone terminal. The communicating unit establishes IP telephone communications with the other IP telephone terminal identified by the identification data via the Internet. The IP telephone function controlling unit controls execution of an IP telephone function used to implement a telephone call with the other IP telephone terminal via the communicating unit. The program includes instructions for functioning the computer as a determining unit a terminal data acquiring unit and a process data transmission controlling unit. The determining unit determines identification data received by the identification data receiving unit. The terminal data acquiring unit acquires terminal data associated with the identification data transmitted from the other IP telephone terminal over the Internet in case the determining unit determines that the terminal data identifying functions that the other IP telephone terminal can control is associated with the identification data received by the identification data receiving unit. The process data transmission controlling unit that controls the transmission of process data to the other IP telephone terminal via the IP telephone communications where the process data is data used in the function identified by the terminal data acquired by the terminal data acquiring unit.

According to still another aspect the present invention provides a computer readable storage medium. The computer readable storage medium stores a computer executable program for controlling a computer operable to control an IP telephone terminal. The IP telephone terminal includes a communicating unit an identification data receiving unit and IP telephone function controlling unit. The communicating unit establishes IP telephone communications over an Internet with another IP telephone terminal possessing identification data receiving unit that receives over the Internet identification data set for each IP telephone terminal. The IP telephone function controlling unit controls the execution of an IP telephone function used to implement a telephone call with the other IP telephone terminal through the communicating unit. The program includes instructions for functioning the computer as a function recognizing unit that recognizes functions that can be controlled by its own IP telephone terminal and a registering unit that registers terminal data identifying the function recognized by the function recognizing unit as data that the other IP telephone terminal can receive through the identification data receiving unit.

According to still another aspect the present invention provides an IP telephone system. The IP telephone system includes another IP telephone terminal and own IP telephone terminal. The another IP telephone terminal is on a network. The own IP telephone terminal includes an identification data receiving unit a communicating unit an IP telephone function controlling unit a determining unit a terminal data acquiring unit and a process data transmission controlling unit. The identification data receiving unit receives over an Internet identification data identifying the other IP telephone terminal. The communicating unit establishes IP telephone communications with the other IP telephone terminal identified by the identification data via the Internet. The IP telephone function controlling unit controls execution of an IP telephone function used to implement a telephone call with the other IP telephone terminal via the communicating unit. The determining unit determines the identification data received by the identification data receiving unit. The terminal data acquiring unit acquires terminal data associated with the identification data transmitted from the other IP telephone terminal over the Internet in case the determining unit determines that the terminal data identifying functions that the other IP telephone terminal can control is associated with the identification data received by the identification data receiving unit. The process data transmission controlling unit controls transmission of process data to the other IP telephone terminal via the IP telephone communications where the process data is data used in the function identified by the terminal data acquired by the terminal data acquiring unit. The another IP telephone terminal includes a function recognizing unit and a registering unit. The function recognizing unit recognizes functions that can be controlled by the another IP telephone terminal. The registering unit registers terminal data identifying functions recognized by the function recognizing unit as data that the own IP telephone terminal can receive through the identification data receiving unit.

According to still another aspect the present invention provides a computer readable storage medium. The computer readable storage medium stores a computer executable IP telephone cooperative program for controlling a computer operable to control a network terminal which installs an IP telephone application program functioning the network terminal as an identification data receiving unit a communicating unit and an IP telephone function controlling unit. The identification data receiving unit receives over an Internet identification data identifying another IP telephone terminal. The communicating unit establishes IP telephone communications with the other IP telephone terminal identified by the identification data via the Internet. The IP telephone function controlling unit controls execution of an IP telephone function used to implement a telephone call with the other IP telephone terminal via the communicating unit. The IP telephone cooperative program includes instructions for functioning the computer as a determining unit that determines identification data received by the identification data receiving unit a terminal data acquiring unit that acquires terminal data associated with the identification data transmitted from the other IP telephone terminal over the Internet in case the determining unit determines that the terminal data identifying functions that the other IP telephone terminal can control is associated with the identification data received by the identification data receiving unit and a process data transmission controlling unit that controls the transmission of process data to the other IP telephone terminal via the IP telephone communications performed by the communicating unit where the process data is data used in the function identified by the terminal data acquired by the terminal data acquiring unit.

According to still another aspect the present invention provides a computer readable storage medium. The computer readable storage medium stores a computer executable IP telephone cooperative program for controlling a computer operable to control an IP telephone terminal functioning the network terminal as an identification data receiving unit a communicating unit and an IP telephone function controlling unit. The identification data receiving unit receives over an Internet identification data identifying another IP telephone terminal. The communicating unit establishes IP telephone communications with the other IP telephone terminal identified by the identification data via the Internet. The IP telephone function controlling unit controls execution of an IP telephone function used to implement a telephone call with the other IP telephone terminal via the communicating unit. The IP telephone cooperative program includes instructions for functioning the computer as a function recognizing unit and a registering unit. The function recognizing unit recognizes functions that can be controlled by its own IP telephone terminal. The registering unit registers into the IP telephone application program terminal data identifying the function recognized by the function recognizing unit as data that the other IP telephone terminal can receive through the identification data receiving unit.

According to still another aspect the present invention provides an IP telephone system. The IP telephone system includes a plurality of IP telephone terminals. A plurality of IP telephone terminals includes an own IP telephone terminal and other IP telephone terminal. The own IP telephone terminal performs IP telephone call with the other IP telephone terminal with a communication unit and own IP telephone application program installed in the own IP telephone terminal the communicating unit establishing IP telephone communications over an Internet with other IP telephone terminal possessing identification data receiving unit. The identification data receiving unit receives over the Internet identification data identifying each IP telephone terminal. The IP telephone application program receiving the identification data identifying each of the IP telephone terminal over the Internet and being configured to control the execution of an IP telephone function used to implement the telephone call with the other IP telephone terminal through the communicating unit. It is preferable that the own IP telephone terminal includes a determining unit a terminal data acquiring unit and a process data transmission controlling unit. The determining unit determines the identification data received by the identification data receiving unit a process data transmission controlling unit. The terminal data acquiring unit acquires terminal data associated with the identification data transmitted from the other IP telephone terminal over the Internet in case the determining unit determines that the terminal data identifying functions that the other IP telephone terminal can control is associated with the identification data received by the identification data receiving unit. The process data transmission controlling unit controls transmission of process data to the other IP telephone terminal via the IP telephone communications performed by the communicating unit provided in the own IP telephone terminal where the process data is data used in the function identified by the terminal data acquired by the terminal data acquiring unit. The other IP telephone terminal includes a function recognizing unit and a registering unit. The function recognizing unit recognizes functions that can be controlled by the other IP telephone terminal. The registering unit registers into an IP telephone application program installed in the other IP telephone terminal terminal data identifying functions recognized by the function recognizing unit as data that the own IP telephone application program can receive.

According to still another aspect the present invention provides a method of controlling an IP telephone system. The method of controlling an IP telephone system implements an IP telephone call between an own network terminal and another network terminal on a network or another telephone terminal connected to the other network terminal via an own IP telephone application installed on the own network terminal the IP telephone call being performed with a communication unit and own IP telephone application program. The communicating unit establishing IP telephone communications over an Internet with the other network terminal or the other telephone terminal connected to the other network terminal possessing identification data receiving unit that receives over the Internet identification data identifying each the network terminal and the IP telephone application program receiving the identification data identifying each of the IP telephone terminal over the Internet and being configured to control the execution of an IP telephone function used to implement the telephone call with the other network terminal or the other telephone terminal connected to the other network terminal through the communicating unit. It is preferable that in the own network terminal the method includes determining the identification data received by the identification data receiving unit acquiring terminal data associated with the identification data and transmitted from the other IP telephone terminal over the Internet upon determining that terminal data identifying functions that the other network terminal or the other telephone terminal connected to the other network terminal can control is associated with the identification data and controlling transmission of process data to the other network terminal or the other telephone terminal connected to the other network terminal via the IP telephone communications performed by the communicating unit provided in the own network terminal where the process data is data used in the function identified by the terminal data acquired by the terminal data acquiring unit. It is preferable that in the other network terminal or the other telephone terminal connected to the other network terminal the method includes the steps of recognizing functions that can be controlled by the other network terminal or the other telephone terminal connected to the other network terminal and registering into an IP telephone application program installed in the other network terminal or the other telephone terminal connected to the other network terminal terminal data identifying the recognized functions as data that the own IF application program can receive.

Next a first embodiment of an IP telephone terminal IP telephone program IP telephone collaborative program IP telephone system and method of controlling an IP telephone system according to the present invention will be described while referring to .

The IP telephone system in includes a personal computer PC a device connected to the personal computer PC a personal computer PC a device connected to the personal computer PC a personal computer PC a device connected to the personal computer PC and a plurality of personal computers not shown connected to a network.

An IP telephone application and an intermediary application are installed on the personal computer PC. An IP telephone application and an intermediary application are installed on the personal computer PC. An IP telephone application and an intermediary application are installed on the personal computer PC. Here the IP telephone application installed on each personal computer is communication software such as Skype capable of implementing telephone calls between personal computers via the network.

On the personal computer PC the intermediary application registers registration data on the device in a registration data storage area of the IP telephone application . The registration data recorded in the registration data storage area includes function identification data for functions possessed by the device . More specifically if the device possesses a print function a scan function and a save function for saving data on a media card data indicating that the device can implement these functions is recorded in the registration data storage area .

Next a process performed when executing the intermediary application for recording data including the function identification data in the registration data storage area of the device will be described. This process is executed prior to performing a series of IP telephone processes via the network.

When the intermediary application is started the character string adding module acquires the display name yamada from the IP telephone application acquires the PC name pc from the PC data for the personal computer PC generates the character string pc yamada and transmits this character string to the device monitoring module . In order to handle changes in the PC name or display name this process may also be performed periodically or whenever a name is changed.

The device monitoring module stores the character string received from the character string adding module each time a character string is transmitted.

As will be described later the device monitoring module monitors devices connected to the personal computer PC to determine whether the device environment of the personal computer PC has been updated and whether the devices connected to the personal computer PC support an IP telephone. Based on the monitoring results the device monitoring module generates a display name and profile for each monitored device and transmits this data to the character string adding module .

In the example of devices A B and C transmit their respective device names Br mfc Ink330 Br dcp Ink420 and Br mfc laser480 to the device monitoring module .

The device monitoring module recognizes that the three devices support IP telephone communications and transmits the display names pc yamada3devices d Br mfc Ink330 d Br dcp Ink420 d B r mfc laser480 to the character string adding module . In this display name pc yamada3devices indicates that three devices connected to pc yamada have been detected. Further the string dn  where n 1 3 is inserted before each device name.

Since each device name is also recorded as a profile as will be described below it is possible to omit the character string indicating the device name from the display name.

Further the device monitoring module transmits the profile Device Br mfc Ink330 Device Br dcp Ink420 Device Br mfc laser480 to the character string adding module .

The character string adding module references the device data list and acquires functions possessed by the device corresponding to each device name received from the device monitoring module and appends a character string indicating the acquired functions for each device to the corresponding profile received from the device monitoring module .

The character string adding module also references the PC data to acquire functions possessed by the personal computer PC and appends a character string indicating these acquired functions to the profile. Here PC data is a collective designation for data stored in the registry and ini files and the like on the personal computer PC and includes the OS version on the personal computer PC and data for installed applications. The functions possessed by the personal computer PC can be identified from the OS version types of installed applications and the like.

 Device Br mfc Ink330 Print Scan Card FAX Color Ink Device Br dcp Ink420 Print Scan Card Color Ink Device Br mfc laser480 Print Scan FAX

Pc Win XP OCR. In the profile Print indicates a print function Scan indicates a scan function FAX indicates a facsimile function Color and Mono indicates color printing and monochromatic printing functions Ink and Laser indicates an inkjet system and laser system Win XP indicates that the OS on the personal computer is Windows registered trademark XP and OCR indicates an optical character recognition function. The character string adding module also uses the same display name generated by the device monitoring module that is pc yamada3devices d Br mfc Ink330 d Br dcp Ink420 d B r mfc laser480. 

Next the above process for registering device data will be described with reference to . is a flowchart illustrating steps in this process. In the flowchart of the processes in S S and S are performed with the device monitoring module while the processes in S S and S S are performed with the character string adding module .

In S of the device monitoring module determines whether the device environment of the personal computer PC has changed. The device monitoring module advances to S if the environment has been updated S YES and ends the device data registration process if the environment has not changed S NO . If the process is being performed immediately after starting the personal computer PC the device monitoring module determines that the device environment has changed and advances to S.

In S the device monitoring module determines whether or not a device supporting IP telephone communications exists among the updated devices. The device monitoring module advances to S if one of the updated devices support an IP telephone device S YES or ends the device data registration process if an IP telephone device was not involved in the update. When the process is being performed immediately after the personal computer PC was started the device monitoring module determines that an IP telephone device is included in the updated devices and advances to S.

In S the device monitoring module determines whether a device is connected to the personal computer PC. The device monitoring module advances to S when a device is connected S YES and advances to SB when a device is not connected S NO .

In S the device monitoring module adds a character string indicating a connection number of the device to each device name adds the string  dn  where n is a number between 1 and the number of connected devices to the head of each device name and transmits a character string formed by concatenating each device name as the display name to the character string adding module . Subsequently the device monitoring module advances to S.

In S the device monitoring module acquires a device data character string from each device forms a new character string by adding devicen where n is a number between 1 and the number of connected devices to the head of this character string and transmits the new character string to the character string adding module as the profile. Subsequently the process continues from S.

In S the character string adding module acquires a character string indicating the functions of each device transmitted in the profile and the personal computer PC from the device data list and the PC data and subsequently advances to S.

In S the character string adding module appends a character string indicating the functions of acquired devices and the personal computer PC to each device data in the profile and subsequently advances to S.

In S the device monitoring module transmits a character string to the character string adding module as the display name indicating that no devices are connected and subsequently the process advances to S.

In S the character string adding module acquires the functions of the personal computer PC from the PC data and subsequently advances to S.

In S the character string adding module adds a character string indicating the functions of the personal computer PC to the profile and subsequently advances to S.

In S the character string adding module records the display names and the profile in the IP telephone application .

The intermediary application according to the preferred embodiment recognizes functions possessed by the personal computer PC or devices connected to the personal computer PC. The recognized functions are recorded in the IP telephone application as function identification data that can be acquired by other IP telephone applications. The function identification data constitutes at least part of the registration data recorded in the IP telephone application and can be supplied to other personal computers that implement IP telephone communications via another IP telephone application.

On the personal computer PC the intermediary application records registration data including function identification data for functions possessed by the device in a registration data storage area of the IP telephone application . This registration is performed through manual input by the user of the personal computer PC and the like. The intermediary application of the personal computer PC also has a similar function to the intermediary application for recording registration data including function identification data for functions possessed by the device in a registration data storage area not shown of the IP telephone application .

In a plurality of personal computers not shown other than the personal computers PC PC are connected to the network. As with the personal computers PC PC an IP telephone application and an intermediary application are installed on each of these personal computers and devices are connected to the computers. Accordingly registration data including function identification data for functions possessed by each device is recorded in a registration data storage area of the corresponding IP telephone application.

In other words registration data including function identification data identifying functions possessed by each device is recorded in the registration data storage area of each corresponding IP telephone application installed on the personal computers PC PC and the other personal computers.

The registration data stored in the registration data storage area the registration data storage area and the registration storage area of each IP telephone application installed on the plurality of other personal computers is transferred over the network to the IP telephone application in the personal computer PC. This registration data is then stored in a registration data storage area of the IP telephone application .

Next steps in a procedure will be described using the example of data acquired from the device connected to the personal computer PC being subsequently processed by the device connected to the personal computer PC. shows the sequence of steps performed according to an IP telephone program of the preferred embodiment.

First the intermediary application issues a search command to the IP telephone application to search for user devices. The IP telephone application searches for user devices on IP telephone applications the IP telephone application and the like installed on other personal computers. At this time the IP telephone application and the like transmit user device data registration data to the IP telephone application and the IP telephone application stores this registration data in the registration data storage area .

In P the intermediary application performs a process to acquire a contact list based on the registration data received from the other personal computers and stored in the registration data storage area . This process will be described later in greater detail but the process allows the intermediary application to acquire a contact list of user devices registered in the IP telephone applications. The contact list is a list of user devices representing candidates that can be called from the IP telephone application . Hence the IP telephone application stores registration data acquired from IP telephone applications installed on the other personal computers though not shown in the drawings the IP telephone applications and are also provided with a contact list. Further the contact list can be edited outside the IP telephone application.

In P the intermediary application selects the reception terminal and function to be used. While this process will be described later in greater detail after the desired function is selected the intermediary application issues a data acquisition command corresponding to the selected function to the device connected to the personal computer PC.

In P the device acquires data based on the selected function. For example the device transfers scanned image data to the intermediary application of the personal computer PC.

In P the intermediary application generates image data and command data to be transferred. While this process will be described in greater detail below the image data and command data to be transferred are generated based on the type of process to be performed on the destination device with the acquired data.

In P the intermediary application issues a command to transmit the acquired data. The command for transmitting data acquired in P is issued to the IP telephone application . Next the IP telephone application of the personal computer PC issues a command to the IP telephone application of the personal computer PC to confirm data transmission authorization.

In P the intermediary application monitors received data for a command to confirm data transmission authorization. At this time the intermediary application detects such a command when the command is transferred from the IP telephone application and received by the IP telephone application .

In P the intermediary application performs a process to specify a location for saving reception data in response to a command transferred from the IP telephone application to the IP telephone application and subsequently issues a command to the IP telephone application to authorize data transmission and transmits the location specification for saving reception data. The IP telephone application issues a command to confirm data transmission authorization to the IP telephone application .

In P the intermediary application monitors received data for a command to authorize data transmission and detects the data transmission authorization command when such a command is transferred from the IP telephone application to the IP telephone application .

In P the IP telephone application executes a data transmission function. Specifically a file transmission unit provided in the IP telephone application attaches command data corresponding to the function provided on the device to the data acquired in P and transmits this data to a file reception unit provided in the IP telephone application .

In P the intermediary application waits for the transmission data and subsequently receives the data transmitted in P.

In P the intermediary application interprets the command data within the data received from the IP telephone application and outputs a data processing command for the selected function to the device based on the interpreted command data.

In P the device performs a data process using the specified function based on the data processing command.

Through the processes P P described above data for the selected function is acquired from the device and the device performs a data process on the acquired data using the selected function.

The processes in P P constitute a process for transmitting image data and command data from the personal computer PC to the personal computer PC.

The intermediary application according to the preferred embodiment can select a function possessed by the personal computer PC to execute acquire data in a format to be processed by the selected function and direct the IP telephone application to transmit this data. Accordingly the intermediary application can direct the personal computer PC to implement a prescribed function when the IP telephone application installed on the personal computer PC only possesses a function to communicate with other personal computers.

Further since the intermediary application according to the preferred embodiment transmits data identifying a selected function in addition to data to be processed the personal computer PC can process the data received from the intermediary application using the specified function.

Next this process will be described in greater detail. When the user of the personal computer PC inputs an instruction to the intermediary application at a desired timing the user interface of the intermediary application shown in is launched.

The user interface shown in functions to acquire data recorded in the processes of S S in an IP telephone application installed on another PC the IP telephone application for example via the IP telephone application installed on the personal computer PC and to use functions of the other PC and devices connected to the other PC. Hence the user interface of the intermediary application includes a Search for User Devices . . . button for displaying a user interface see to acquire data recorded on an IP telephone application installed on another PC and a Functions Using User Devices . . . button for displaying a user interface see to use functions of the other PC and devices connected to the other PC.

A box labeled Device Data for the Selected User Device in the user interface displays function identification data corresponding to the display name selected in the Contact List the display name highlighted in the contact list with a dotted line . In the example shown in the device name Br DCP 420 and the device functions Printer Scanner and Media Card Slot corresponding to the highlighted user device Br dcp420 sato are displayed as the device data.

The user can execute any of the basic functions possessed by the IP telephone application by pressing the corresponding button Chat . . . Call . . . File Transfer . . . and Search for User . . . listed under Basic Functions of the IP Telephone Application. 

Further pressing on one of the buttons Functions Using User Devices . . . and Search for User Devices . . . under Expanded Functions of the IP Telephone Application launches the corresponding user interface for implementing functions using user devices and for searching for user devices.

In S of the intermediary application acquires device data corresponding to the highlighted display name from the display name and profile.

In S the intermediary application determines whether or not the device data was successfully acquired. The process skips to S when the device data was acquired successfully S YES and advances to S when unsuccessful S NO .

In S the intermediary application acquires data indicating the type of device specified in the highlighted display name and functions possessed by the device from the device data list.

In S the intermediary application displays the device name and device functions acquired above in the Device Data for the Selected User Device box of the user interface shown in and subsequently ends the process.

Here examples have been given for a process to directly extract device data for the highlighted display name from the display name and profile or for indirectly extracting device data by referencing the device data list based on the highlighted display name.

In addition it is possible to extract functions possessed by each device from the registration data for each device and configure the function identification data by individually appending these functions to the corresponding display name of the user device. For example function identification data extracted from the registration data may be deviceA userB printer deviceA userB scanner deviceA userB FAX and deviceA card. 

The user first specifies criteria for searching for user devices from items in the registration data in the 1. Please Select the Search Criteria and then specifies properties of user devices that the user wishes to acquire in a search within the 2. Please Select the Function or Type of Device. After the user presses the Search button the process in S of described later is executed to obtain the user device search results corresponding to the above specifications under User Device Search Results. 

In S of the intermediary application performs a search for user devices supporting an IP telephone application. This process is executed when the user presses the Search button after specifying the function or type of device being searched in the user interface of . The intermediary application acquires user device search results registration data from the IP telephone applications and retrieves and displays the functions or types of devices included in the search results.

In S the intermediary application performs a process to add user devices supporting an IP telephone application from the search results to the contact list. More specifically when the user presses the Insert Selected User Device into Contact List in the user interface of the intermediary application adds the highlighted user device in the user device search results to the contact list provided in the IP telephone application . Subsequently the intermediary application ends the contact list acquisition process.

Next the process for searching for user devices supporting IP telephone applications will be described in detail. is a flowchart illustrating steps in this search process performed in S of .

In S of the intermediary application stores data indicating the user s specification in 1. Please Select the Search Criteria and 2. Please Select the Function or Type of Device in the user interface of in a variable DEV.

In S the intermediary application performs a process to acquire user device search results from the IP telephone application from acquired registration data.

In S the intermediary application performs a process to search user devices. Subsequently the intermediate application ends the process started in S of to search for user devices supporting an IP telephone application.

In S of the intermediary application transmits a user device search command to an Application Programming Interface API of the IP telephone application . In response the IP telephone application searches for user devices according to a procedure defined by IP telephone specifications to acquire registration data.

In S the intermediary application acquires results of this user device search from the IP telephone application via the API of the IP telephone application .

After completing S the intermediary application ends the process to acquire user device search results from the IP telephone application.

In S of the intermediary application acquires a character string from the device data list based on the variable DEV identifying devices targeted for a search. The device data list includes values indicating the functions or types of devices similar to the value stored in the variable DEV and corresponding data in the form of a character string identifying devices having these functions or devices of these types.

In S the intermediary application searches for the character string acquired in S from the user device search results received from the IP telephone application.

In S the intermediary application determines whether or not there exist any user devices corresponding to the character string used in the search. The intermediary application advances to S if such user devices exist S YES and advances to S if no such device exists S NO .

In S the intermediary application extracts all user devices matching the character string used in the search.

In S the intermediary application displays all user devices extracted in S in a list under Results of the user device search in the user interface of . Subsequently the intermediary application ends the user device search process for user devices supporting an IP telephone application.

In S the intermediary application displays a message indicating that the selected user device does not exist. For example the intermediary application outputs the message The selected user device was not found. Either the user device does not exist or is not online. After the user presses OK the intermediary application ends the user device search process for searching for user devices supporting an IP telephone application.

On the personal computer PC incorporating an IP telephone application the intermediary application according to the preferred embodiment can acquire function identification data identifying functions possessed by other personal computers or other devices even in an IP telephone system that does not employ a server. The intermediary application either directly extracts this data from registration data acquired by the IP telephone application or indirectly acquires the data based on this registration data which registration data is recorded in another IP telephone application installed on a network personal computer. Accordingly the intermediary application can identify functions possessed by other personal computers or other devices based on data recorded on the other IP telephone applications.

Further with the intermediary application according to the preferred embodiment the user of the personal computer PC can visually identify a plurality of functions possessed by other personal computers or other telephone terminals.

When the user presses the Functions Using User Devices . . . button at an arbitrary timing in the user interface of the intermediary application launches a user interface for functions using user devices shown in and executes the process in P of which will be described later with reference to .

The user interface for functions using user devices in includes boxes for a Contact List and Target User Devices Add and Delete buttons for adding and deleting target users to and from the Target User Devices radio buttons for specifying target data in the contact list for selecting either Scanned Data or Existing Files in the present example radio buttons for specifying functions to be performed on target user devices for selecting either Print Save Image to Media Card or OCR in the present example an OK button for executing a function and a Cancel button for canceling the function.

A target user device is a user device targeted for performing a process based on a selected function. A plurality of target user devices may be specified. To add a user device to the Target User Devices box the user can highlight a user device in the contact list to add to the target user devices and press the Add button. Similarly if the user wishes to delete a user device from the Target User Devices box the user can highlight a user device to be deleted from the Target User Devices box and press the Delete button.

Once the user presses the OK button in the user interface of the intermediary application performs part of the process in P of based on the selected function and the device executes the process in P.

In S of the intermediary application determines whether or not the Add button was pressed. The intermediary application advances to S if the Add button was pressed S YES and advances to S if not pressed S NO .

In S the intermediary application adds the user device highlighted in the contact list to the target user devices.

In S the intermediary application displays the newly added user device in the Target User Devices box of the user interface.

In S the intermediary application determines whether the OK button has been pressed. The intermediary application advances to S if the OK button was pressed S YES and advances to S if not pressed S NO .

In S the intermediary application performs additional processes for such cases as when the user has selected the radio button next to Existing Files under Target Data in the user interface of or when the user has pressed the Cancel button. If the user has selected the radio button next to Existing Files the intermediary application performs a process to specify a file. Subsequently the intermediary application returns to S.

When the user has pressed the Cancel button the intermediary application closes the UI window for functions using user device and cancels all subsequent steps of the process.

In S the intermediary application stores the function to be performed by the target user device in the variable TF. Subsequently the intermediary application issues a data acquisition command based on the desired function the function to be performed by the target user device to the device prompting the device to execute the process of P in . At this point the intermediary application ends the process for selecting a reception terminal and desired function.

Once the device has executed the process of P in and the intermediary application has received data from the device the intermediary application executes the process in P of for generating image data and command data to be transmitted. This process will be described next in greater detail. is a flowchart illustrating steps in the process for generating image data and command data to be transmitted.

In S of the intermediary application selects the function to be performed on the target user device based on the variable TF. The intermediary application advances to S when the selected function is Print advances to S when the selected function is Save to Media Card and advances to S when the selected function is OCR. 

In S the intermediary application converts acquired image data to print data. More specifically the intermediary application converts the image data to a format for printing on the target user device and attaches a code for print control.

In S the intermediary application generates a print command file. Specifically the intermediary application stores print command data in the command data shown in . Subsequently the intermediary application ends the process to generate image data and command data to be transmitted.

In S the intermediary application generates a command data for saving data on a media card. More specifically the intermediary application stores memory card save command data in the command data shown in . Subsequently the intermediary application ends the process to generate image data and command data to be transmitted.

In S the intermediary application performs an image process to convert the acquired image data to OCR supported data. More specifically the intermediary application sets a suitable threshold for OCR and performs binarization on the image data based on this threshold.

In S the intermediary application creates OCR command data and subsequently ends the process to generate image data and command data to be transmitted.

The process of S S described above is executed on all target devices stored in the array of variables TD.

Since the intermediary application according to the preferred embodiment transmits data identifying a desired function to be used in processing data together with the data the other personal computer or other telephone terminal can process received data using the specified function.

Further the intermediary application according to the preferred embodiment can acquire and display at least terminal function identification data identifying a plurality of other personal computers or a plurality of other devices. The user can select the display terminal function identification data for directing one of the other personal computers or devices to process the data.

Further the intermediary application according to the preferred embodiment can display function identification data related to other personal computers or other devices possessing the user specified function.

Further with the IP telephone system and the method of controlling the IP telephone system according to the preferred embodiment the intermediary application can identify functions possessed by other personal computers or other devices by directly or indirectly acquiring function identification data identifying these functions from registration data acquired by the IP telephone application even when the IP telephone system does not employ a server. The registration data is data recorded in another IP telephone application installed on the other personal computer on the network.

In addition functions possessed by another personal computer or another device are recorded in the corresponding other IP telephone application as function identification data that the IP telephone application can acquire. This function identification data constitutes at least part of the registration data recorded in the other IP telephone application. The personal computer PC can acquire this function identification data when performing an IP telephone call via the IP telephone application .

The intermediary application can implement a prescribed function on another personal computer or a device on the network even when the IP telephone application installed on the personal computer PC has only a function for communicating with a personal computer. Specifically the intermediary application can select a function possessed on the other personal computer or other device to be executed acquire data in the format required for processing with the selected function and direct the IP telephone application to transmit this data.

when an IP telephone application including only a function for implementing communications between terminals is already installed on the own network terminal resources of the IP telephone system can be effectively used without requiring a long processing time for replacing the IP telephone application for example.

Further since the intermediary application transmits data identifying the function to be used for processing data together with the data to be processed in the IP telephone system according to the preferred embodiment the other personal computer or other device can process the received data using the specified function.

Data transmitted by one network terminal can be processed on another network terminal using a processing function selected by the network terminal that transmitted the data thereby effectively utilizing resources of both the network terminal on the transmission side and the network terminal on the reception side.

Next a firmware transmission program according to a variation of the embodiment will be described. shows an example of a user interface in the firmware transmission program.

The firmware transmission program is used for transmitting firmware for a prescribed device from the manufacturer that developed the device. In the present variation firmware includes the firmware of the prescribed device itself and an intermediary application operating between the device and the IP telephone application.

The user interface for the firmware transmission program shown in includes a Select User Data selector a Device Type selector a Device Model list a Firmware Selection input line a User Search Results list a Device Data for Selected User sub window a Search button a Transmit button and a Cancel button.

An administrator at the manufacturer for firmware support launches the user interface in at a desired timing selects criteria for the user device search from the registration data using the 1. Please Select the Search Criteria selector Display name is selected in this example selects the type of device to search for with the Device Type selector Inkjet printer multifunction device is selected in this example and selects the model of the device to search for from the Device Model list MFC 420CN is selected in this example . The selectors have the same functions as those in . When the administrator subsequently presses the Search button the intermediary application executes the process described in to search for user devices supporting an IP telephone application and displays display names and the like of user devices matching the searched device type in the User Device Search Results box.

Further the process of is executed when there is any change in the highlighted device of the search results to display the name of the highlighted user device and the functions possessed by the device. When the administrator inputs a filename for the firmware to be transmitted in the Firmware Selection input line and presses the Transmit button the firmware specified by the filename is transmitted to the user devices displayed in the User Device Search Results box. Upon receiving this firmware the user devices update their firmware.

In this way the intermediary application can update the firmware on network terminals or telephone terminals possessing an IP telephone application based on data recorded in their IP telephone applications. Sometimes a manufacturer creates and updates firmware for each function of a device. With the variation of the embodiment the intermediary application can verify functions possessed by user devices and transmit the correct firmware for updates.

Next an IP telephone terminal IP telephone program and IP telephone system of the present invention will be described according to a second embodiment while referring to .

In the IP telephone system of the second embodiment like parts and components to those of the IP telephone system in the first embodiment shown in are designated with the same reference numerals to avoid duplicating description.

While the IP telephone application and intermediary application were installed on the personal computer PC in the first embodiment an IP telephone application is installed on the personal computer PC of the second embodiment. The IP telephone application is a program capable of implementing the functions of both the IP telephone application and the intermediary application described in the first embodiment.

Similarly an IP telephone application is installed on the personal computer PC of the second embodiment where the IP telephone application is a program capable of implementing both the functions of both the IP telephone application and intermediary application described in the first embodiment.

While the IP telephone application and IP telephone application have the same operations and effects in the second embodiment different reference numerals are used in the following description for convenience.

Further the character string adding module and device monitoring module see are integrated in both the IP telephone applications and for implementing the device data registration process see on the personal computer PC and personal computer PC. However since the character string adding module and the device monitoring module and the device data registration process are identical to those described in the first embodiment a description of these modules and process will not be repeated.

As shown in the personal computer PC is provided with a CPU a ROM a RAM and a hard disk drive HDD . The personal computer PC is also provided with an audio interface capable of connecting to an audio device for implementing IP telephone communications with another IP telephone terminal specified by a display name via an Internet a network interface and a USB interface capable of connecting with an external device. The personal computer PC is also provided with other components such as a monitor not shown for displaying the user interfaces described with reference to and the like although a description of these devices has been omitted.

The CPU controls the components of the personal computer PC based on fixed values and programs stored on the ROM RAM and HDD . The IP telephone application described above is stored on the HDD .

While the personal computer PC is connected to a device via a USB connection in the example of it should be apparent that the personal computer PC can control a device connected on a LAN.

Next a process will be described in which data acquired from the device connected to the personal computer PC is processed on the device connected to the personal computer PC.

The IP telephone application and the like return user device data registration data including display names an example of identification data to the IP telephone application and the IP telephone application stores this registration data in the registration data storage area see .

Some systems may be provided with a special user device called a supernode for managing registration data of all IP telephone applications. In this case the supernode returns the registration data for each IP telephone application in response to a search performed on the IP telephone application .

If a supernode exists in the system described in the first embodiment the supernode would return registration data for each IP telephone application in response to a search performed by the IP telephone application .

In P the IP telephone application of the personal computer PC performs a process to acquire a contact list based on registration data from other personal computers recorded in the registration data storage area . This process is substantially the same as the process described with reference to and in the first embodiment and will not be repeated here.

However since the contact list acquisition process according to the first embodiment is performed with the intermediary application the intermediary application acquires user device search results from the IP telephone application as described in S of . In the case of the second embodiment the IP telephone application can directly search for user devices supporting an IP telephone application without going through the intermediary application.

In P the IP telephone application performs a process to select a reception terminal and a desired function. This process is substantially identical to that described with reference to in the first embodiment and will not be repeated here. However the process described in is executed with the intermediary application while the process of the second embodiment is performed with the IP telephone application.

After the desired function is selected in this process the IP telephone application issues a data acquisition command based on this function to the device connected to the personal computer PC.

In P the device acquires data to be processed with the selected function. For example the device may transfer image data scanned by the device to the IP telephone application of the personal computer PC

In P the IP telephone application performs a process to generate image data and command data to be transferred. This process was described with reference to and will not be repeated here. However the process described in was executed with the intermediary application while the process in the second embodiment is executed with the IP telephone application.

In P the IP telephone application generates image data and command data to be transmitted based on the type of data to be processed on the destination device.

In P the IP telephone application issues a command to the IP telephone application of the device to confirm data transmission authorization.

In P the IP telephone application monitors incoming data for a command to confirm data transmission authorization. At this time the IP telephone application detects such a command when the command is transferred from the IP telephone application and received by the IP telephone application .

In P the IP telephone application performs a process to specify a location for saving reception data in response to detecting a command to confirm data transmission authorization received from the IP telephone application . Next the IP telephone application issues a command to the IP telephone application to authorize data transmission.

In P the IP telephone application monitors incoming data for a command authorizing data transmission and detects the data transmission authorization command when such a command is received from the IP telephone application .

In P the IP telephone application executes a data transmission function. Specifically the IP telephone application in transmits the data acquired in P with attached command data indicating the function provided on the device from the file transmission unit of the IP telephone application to the file reception unit of the IP telephone application via IP telephone communications. In this way the personal computer PC can transmit data that will be effectively used on the destination device.

In P the IP telephone application waits for the transmission data and subsequently receives the data transmitted in P.

In P the IP telephone application interprets the command data within the data received from the IP telephone application and outputs a data processing command for the selected function to the device based on the interpreted command.

In P the device performs a data process using the specified function based on the data processing command.

The program can display data related to another network terminal possessing a user specified function and can effectively utilize processing resources indicated in the displayed data.

In P and P described above the device processes data acquired from the device with the selected function. As a result the resources of the IP telephone terminals on the data transmission side and data reception side can be effectively utilized.

As in the first embodiment described above the personal computer PC according to the second embodiment displays the user interface described with reference to when the user inputs an instruction in the IF telephone application at a desired timing. Since the user interface of the second embodiment is identical to that in the first embodiment differing only in that the user interface is displayed by the IP telephone application rather than the intermediary application the user interface of the IP telephone application has been omitted from this description and the drawings.

Further the process described in is executed each time the highlighted display name for the user device changes in the user interface of .

Here the process of according to the second embodiment will be described. As in the first embodiment described above in S of the IP telephone application acquires device data for the display name of the highlighted user device from the display name and profile.

In S the IP telephone application determines whether or not the device data was successfully acquired. The IP telephone application advances to S when the device data was successfully acquired S YES and advances to S when unsuccessful S NO .

When the display name includes a PC name such as pc  and device indicating a device name is included as described with reference to there is a high likelihood that the ensuing portion of the display name will include a PC name and device name.

If the display name includes an extraction character string S YES i.e. when the IP telephone application determines that a PC name and device name are associated with the display name in S the IP telephone application removes extracts the device name from the character string immediately following the extraction character string.

In S the IP telephone application acquires an extraction character string B corresponding to the extraction character string A detected in the display name and determines whether the extraction character string B exists in the profile.

If the profile includes the extraction character string B S YES in S the IP telephone application removes the device data from the character string immediately following this extraction character string and returns to S of . As described above a character string indicating the functions possessed by the device have been added to the device data see .

In other words through the above process the IP telephone application can acquire a device name associated with a display name received from another IP telephone terminal over the Internet and can identify functions that the other IP telephone terminal having this display name can control based on the device name. Hence the IP telephone application can acquire the device name through a simple process of extracting the device name from the display name avoiding unnecessary use of processing resources.

However if the IP telephone application makes a negative determination in either S or S S N or S NO i.e. when device data could not be acquired the IP telephone application returns to S of .

Although device data is included in the profile in the preferred embodiments described above the device data may be included in the display name instead for example. In this case rather than determining whether or not the profile includes the extraction character string B in S the IP telephone application may determine whether or not the display name includes the extraction character string B. When the display name includes the extraction character string B in S the IP telephone application can be configured to remove the device data from the character string in the display name immediately following the extraction character string B.

In S the IP telephone application determines whether or not a device name stored in the device data list see is included in the highlighted display name and if so acquires the device data corresponding to this device name from the device data list.

If the display name does not include a device name stored in the device data list S NO the process ends. However if the display name includes one of the device names stored in the device data list S YES in S the IP telephone application extracts the device name from the display name. The process in S is an example of the terminal data acquiring means.

In S the IP telephone application acquires device data corresponding to the extracted device name from the device data list and subsequently returns to S of .

Since the device name is also included in the profile in the preferred embodiment it is possible to determine in S whether or not the profile includes the device name rather than whether or not the display name includes the device name.

It is also possible to determine whether or not the device name is included in the profile in the first embodiment.

As in the first embodiment described above in S the IP telephone application displays the device name and device functions acquired in the Device Data for the Selected User Device of the user interface shown in and subsequently ends the process.

As with the personal computer PC according to the first embodiment the personal computer PC according to the second embodiment can easily use functions of other IP telephone terminals to effectively utilize the resources of the IP telephone system.

The other IP telephone terminal enables the own IP telephone terminal to receive terminal data identifying functions that can be controlled by the other IP telephone terminal. Therefore the user of the own IP telephone terminal can be notified of functions that can be controlled by the other IP telephone terminal and therefore can effectively utilize these functions.

While the invention has been described in detail with reference to specific embodiments thereof it would be apparent to those skilled in the art that many modifications and variations may be made therein without departing from the spirit of the invention the scope of which is defined by the attached claims.

For example while the devices connected to the personal computer are described as a scanner and printer in the preferred embodiments the present invention may also be applied to a facsimile machine or other device.

The device may also be provided with a voice I O function such as a speaker and microphone. The user uses the speaker and microphone provided in the device to make a telephone call on an IP telephone and the device data for the device implementing the telephone call is registered in the IP telephone application.

In this case the IP telephone application outputs voice data received from another IP telephone terminal through the speaker of the device and transmits voice data inputted into the microphone of the device to the other IP telephone terminal.

In addition the IP telephone application and the device are configured to transmit an event message to the intermediary application and the intermediary application relays event messages from the IP telephone application to the device and messages from the device to the IP telephone application.

For example when the IP telephone application receives a call request from another IP telephone terminal the IP telephone application transfers a call request event to the device via the intermediary application. If the user operates the device to indicate acceptance of the call this acceptance event is conveyed to the IP telephone application after which the telephone call begins.

When the intermediary application acquires an instruction from the device indicating acceptance of the call the application may assume all determinations in S S of are YES and in S S may record the device data of the device from which the instruction to accept the call originated in the IP telephone application.

On the other hand if the user operates the device to input an instruction to search for other user devices the device conveys a search instruction event to the IP telephone application via the intermediary application and the IP telephone application transmits a request over the Internet to search for user devices. After receiving a contact list as a result of this search the IP telephone application transfers the contact list to the device via the intermediary application and the device displays this list on a display unit.

At this time the user can operate the device to select a call destination from the displayed contact list. When the user inputs a call instruction after selecting a contact the device conveys a call request event to the IP telephone application via the intermediary application and the IP telephone application transmits a call request to the IP telephone terminal at the call destination and subsequently waits for permission to implement the call.

Upon obtaining an instruction from the device requesting a telephone call the intermediary application assumes that all determinations in S S of are YES and in S S records device data for the device from which the instruction requesting a telephone call originated in the IP telephone application.

Further the user interfaces in may be incorporated in the device. In this case the user operates the user interface in or provided in the device to input instructions which instructions are transferred to the IP telephone application via the intermediary application for performing searches and the like. The user may also operate the user interface in provided on the device to input instructions for using a function provided on another IP telephone terminal and the instruction is transferred to the intermediary application.

