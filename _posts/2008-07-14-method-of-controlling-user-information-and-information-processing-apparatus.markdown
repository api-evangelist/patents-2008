---

title: Method of controlling user information and information processing apparatus
abstract: A method of controlling user information for an information processing apparatus includes the steps of a process of an application program requesting user information controlling unit to obtain an item of said user information, and said user information controlling unit providing the obtained item of said user information to said process. The user information controlling unit obtains the user information requested by the process of the application program and provides the user information to the process. Accordingly, the user information can be shared by the application programs and centrally controlled.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07958140&OS=07958140&RS=07958140
owner: Ricoh Company, Ltd.
number: 07958140
owner_city: Tokyo
owner_country: JP
publication_date: 20080714
---
The present application is a divisional of Ser. No. 10 372 798 filed Feb. 26 2003 now abandoned of which claims priority to Japanese Patent Application No. 2002 050539 filed on Feb. 26 2002 Japanese Patent Application No. 2002 050540 filed on Feb. 26 2002 Japanese Patent Application No. 2002 050547 filed on Feb. 26 2002 Japanese Patent Application No. 2003 039974 filed on Feb. 18 2003 Japanese Patent Application No. 2003 039975 filed on Feb. 18 2003 Japanese Patent Application No. 2003 039976 filed on Feb. 18 2003 Japanese Patent Application No. 2003 039977 filed on Feb. 18 2003 Japanese Patent Application No. 2003 039978 filed on Feb. 18 2003 and Japanese Patent Application No. 2003 039979 filed on Feb. 18 2003 the entire contents of which are hereby incorporated by reference.

The present invention generally relates to a method of controlling user information and an information processing apparatus and more particularly to a method of controlling user information in which the user information is provided to a plurality of application programs and to the information processing apparatus using the same.

An information processing apparatus such as a personal computer and an image forming apparatus can provide users with various information processing functions by executing one or more software programs corresponding to various functions. The information processing apparatus is often connected to other devices via a network and can distribute image data for example to the other devices. The information processing apparatus stores therein user information such as distribution addresses user restrictions and charges.

As an example of the information processing apparatus an image forming apparatus is a system that functions as a copier a printer a facsimile and a scanner hereinafter referred to as a multifunctional apparatus . The multifunctional apparatus is provided with a display unit a printing unit and an image capture unit in the system and is further provided with software programs each corresponding to the function of a copier a printer a facsimile or a scanner. A user can use the multifunctional apparatus as a copier a printer a facsimile or a scanner by switching the software programs.

The image forming apparatus is connected with other image forming apparatuses and computers via a network and distributes the image data for example to the other image forming apparatuses and computers. The image forming apparatus stores therein user information such as addresses and user restriction charges.

The distribution address information is used to manage addressees and senders. The distribution address information is not so often updated it is relatively easily backed up. The number of entries is usually large because the addresses of users that do not directly use the information processing apparatus or the image forming apparatus are included in the distribution address information.

On the other hand the user restriction information and the charge information are used to manage the authorization user restriction of various functions and the usage the number of printed pages for example of the authorized functions by respective users. The user restriction charge information is updated frequently whenever the information processing apparatus is used the creating of its backup copy is not easy. Only users who directly use the information processing apparatus or the image forming apparatus are managed using the user restriction charge information. Therefore the number of users is relatively small.

As described above the distribution address information and the user restriction charge information are different in the easiness of backup and the number of users to be managed thereby. Due to this difference the information storage apparatuses suitable for the respective information sets are also different. The distribution address information requires an information storage apparatus with a large capacity even at the sacrifice of speed and reliability. The user restriction charge information however requires an information storage apparatus of high speed and high reliability at the sacrifice of cost and capacity.

Conventionally an information processing apparatus and an image forming apparatus store the distribution address information in a hard disk drive and store the user restriction charge information in a non volatile random access memory RAM .

The conventional information processing apparatus is provided with one or more application software programs corresponding to each of various information processing functions. Each application program however manages the distribution address information separately. The conventional image forming apparatus is provided with application programs corresponding to user services of intrinsic image forming processing such as printing copying scanning and transmitting facsimile. Each application program however manages the distribution address information separately.

The separate management of user information thus requires hardware resources otherwise unnecessary and increases the risk of bugs in the application programs.

Additionally the distribution address information and the user restriction charge information need to be stored and controlled in a hard disk drive HDD or a non volatile random access memory RAM so that the application programs can access these information sets.

A system initialization module and so forth updates the distribution address information. When registering updating and accessing the distribution address information or the user restriction charge information the system initialization module is required to determine in which the HDD or the non volatile RAM the distribution address information and the user restriction charge information are stored so that the system initialization module can designate appropriate one.

Further in the case of the conventional information processing apparatus and the image forming apparatus a user is required to directly operate an operation panel provided on the information processing apparatus and the image forming apparatus to access or update the distribution address information and the user restriction charge information.

Accordingly the user needs to go to the place where the information processing apparatus and the image forming apparatus are placed in order to access and update the distribution address information and the user restriction charge information.

Additionally since the size of the operation panels differs the amount of information displayed on the operation panel changes apparatus by apparatus. The operation panel provided on an image forming apparatus is usually small. Accordingly depending on the size of the operation panel the amount of information that can be displayed on the operation panel is sometimes not large enough.

Furthermore the user is required to follow a predetermined format and order of the information processing apparatus and the image forming apparatus so as to access or update the distribution address information and the user restriction charge information.

The user needs to make a substantial effort to directly operate the operation panel and so forth provided to the information processing apparatus and the image forming apparatus so as to access the distribution address information and the user restriction charge information.

Accordingly it is a general object of the present invention to provide a novel and useful method of controlling user information and more particularly to provide a method of controlling user information in which the user information is centralized and shared by a plurality of application programs.

Another object of the present invention is to provide a method of controlling user information in which the user information can be updated without designating where the user information is stored.

Yet another object of the present invention is to provide a method of controlling the user information with which the user can easily operate with little effort.

To achieve one of the above objects a method of controlling user information for an information processing apparatus according to the present invention includes the steps of a process of an application program requesting a user information control unit to obtain an item of said user information and said user information control unit providing the obtained item of said user information to said process.

The user information control unit obtains the user information requested by the process of the application program and provides the user information to the process. Accordingly the user information can be shared by the application programs and centrally controlled.

According to another aspect of the present invention an information processing apparatus includes a plurality of information storage units storing user information and a user information control unit that in response to a request from a process of an application program obtains said user information from said information storage units and provides the obtained user information to said process of said application program.

According to yet another aspect of the present invention a method of controlling user information for an information processing apparatus includes the steps of a system initialization module requesting a user information control unit to update user information and said user information control unit updating in response to the request from said system initialization module said user information.

The user information control unit updates the user information in compliance with the request from the system initialization module. Accordingly the system initialization module can update the user information without designating in which information storage unit the user information is stored. The user information is centrally controlled.

According to yet another aspect of the present invention an information processing apparatus includes a plurality of information storage units storing user information therein and a user information control unit that updates in response to a request from a system initialization module said user information stored in said information storage unit.

According to yet another aspect of the present invention a method of controlling user information for an information processing apparatus includes the steps of a user information control unit receiving a request in connection with user information from an external control apparatus connected to said information processing apparatus via a network and said user information control unit processing said request using predefined functions.

The user information can be controlled using the external control apparatus connected to the information processing apparatus via the network. Accordingly the operator can control the user information watching a large screen provided to the external control apparatus instead of a small operation panel provided to the information processing apparatus. The user can handle the user information flexibly and easily. The operator does not need to go to the place where the information processing apparatus is placed. Additionally the user information can be shared with another information processing apparatus.

According to yet another aspect of the present invention an information processing apparatus includes a plurality of information storage units storing user information therein and a user information control unit that receives a request in connection with said user information stored in the information storage units from an external control apparatus through a network and handles said user information using a predefined function corresponding to said request.

According to yet another aspect of the present invention a computer program that causes a computer to control user information includes the steps of requesting an information processing apparatus connected via a network to transmit said user information using a predetermined protocol for exchanging messages expressed in a description language receiving said user information from said information processing apparatus in compliance with said protocol displaying a screen based on the received user information and requesting in response to a request to update said user information input by a user said information processing apparatus to update said user information using said protocol.

The computer program can cause a computer to function as the external control apparatus that can remote control the user information stored in the information processing apparatus.

Other objects features and advantages of the present invention will become more apparent from the following detailed description when read in conjunction with the accompanying drawing.

The preferred embodiments of the present invention will be described in detail by reference to the drawings.

The hardware resources include a memory unit an input unit a display unit and other hardware resources . The software programs include application programs through OS such as UNIX trade mark BIOS device drivers a user information control unit a communication control unit and so forth.

When the power is turned on the information processing apparatus reads OS from a secondary storage unit to the memory unit and executes the OS . When the power is turned on or an instruction is given from an operator the information processing apparatus reads an application program through from the secondary storage unit to the memory unit and executes the read application program through 

The application programs through cause the information processing apparatus to perform various information processing operations. BIOS is a computer program that controls the hardware resources . The device drivers are computer programs that drive peripheral devices included in the hardware resources .

OS the user information control unit and the communication control unit communicate with the application programs through via application program interface API . API includes predefined functions through which the application through can give instructions to OS and the user information control unit .

The user information control unit controls the user information. The communication control unit controls the communication with external control apparatuses to be described later connected with the information processing apparatus through a network.

The user information control unit determines the information storage apparatus in which the user information required by the application program through is stored and provides the user information stored in the determined information storage apparatus to the application program through 

OS controls processes created by the execution of the application programs through the user information control unit and the communication control unit in parallel. OS gives instructions to the hardware resources through BIOS and the device drivers .

The hardware configuration of the information processing apparatus will be described below. is a schematic diagram showing the hardware configuration of the information processing apparatus according to an embodiment. The information processing apparatus is configured by an input unit a display unit a secondary storage unit a memory unit a processing unit and a communication unit all of which are mutually connected via a bus B.

The input unit includes input devices such as a keyboard and a mouse. An operator can give the information processing apparatus various instructions by operating the input unit . The display unit displays various windows and data for the operator. The secondary storage unit stores therein computer programs and various files and data that are needed for the performance of the computer programs. The communication unit communicates with an external control apparatus to be described later that is connected through a network.

The memory unit stores the computer programs retrieved from the secondary storage unit when the power of the information processing apparatus is turned on. The processing unit executes the computer programs stored in the memory unit .

When the information processing apparatus is turned on computer programs read from the secondary storage apparatus are stored in the memory unit . The processing unit runs the computer programs stored in the memory unit .

The information processing apparatus is connected to other computers and distributes image information and so forth to the other computers. The information processing apparatus provided with such a distribution function usually stores the distribution address information and the user restriction charge information as user information. The information processing apparatus that is not provided with such a distribution function may store only the user restriction charge information.

As an example of the information processing apparatus according to an embodiment of the present invention an image forming apparatus will be described below. The image forming apparatus is provided with various functions such as those of a printer a copier a facsimile and a scanner and therefore is called a multifunctional apparatus.

The platform further includes the following control services that interpret processing requests from the application programs and control one or more hardware resources a system resource manager SRM that controls one or more hardware resources and arbitrates the requests from the control services and operating system OS .

The control services include one or more service modules such as a system control service SCS an engine control service ECS a memory control service MCS an operation panel control service OCS a facsimile control service FCS a network control service NCS and a user control service .

The platform has an application program interface API that can receive processing requests from the application programs by predefined functions.

The OS is for example UNIX trade mark . The OS executes the software programs of the platform and the application programs as processes in parallel.

The process of SRM controls the system and manages resources together with SCS . For example the process of SRM arbitrates requests from an upper rank layer to use hardware resources such as engines the memory unit files stored in a hard disk drive HDD host input output I O Centronics interface network interface IEEE 1394 interface RS232C interface for example and controls their execution.

In response to a request from the upper rank layer SRM determines whether the requested hardware resource is in use and if not informs the upper rank layer that the requested hardware resource is available for use. SRM schedules the use of hardware resources based on the requests from the upper rank layer. SRM also directly controls the paper transportation and the image forming of the printer engine memory reservation and file generation.

The process of SCS performs application administration operational unit control system screen display LED display resource administration interruption application control and so forth.

The process of ECS controls the engines of the black white laser printer the color laser printer and the hardware resource .

The process of MCS reserves and discharges image memory controls the hard disk drive HDD and compresses and decompresses the image data.

The process of OCS controls the operation panel that helps the multifunctional apparatus to communicate with the operator.

The process of FCS in response to a request from the application layer of the system controller transmits and receives facsimile through PSTN or ISDN for example registers and retrieves various facsimile data stored in the backup SRAM BKM reads documents prints received facsimile and performs multifunctional communication.

The process of NCS provides common services to applications that require communication through a network. The process of NCS distributes data received from the network to corresponding applications programs and intermediates the transmission of data from an application program to the network.

The process of UCS controls the user information by determining the information storage apparatus storing the requested user information and providing the user information from the determined information storage apparatus to the application programs.

The application programs provides users with various user services such as those of a printer a copier a facsimile and a scanner. The application programs includes the following a printer application that causes the multifunctional apparatus to function as a printer supporting page description languages PDL PCL and postscript PS for example a copier application a facsimile application a scanner application a network file application and in line inspection application .

The multifunctional apparatus startup unit performs at first when the multifunctional apparatus is turned on and activates the application programs and the platform . For example the multifunctional apparatus startup unit reads the control services and the application programs from a flash memory to be described later and transfers them to a memory region reserved in SRAM or SDRAM for example for execution.

The operation panel is directly connected to ASIC of the control board . FCU USB interface IEEE1394 interface and the engine unit are connected to ASIC of the control board through a PCI bus and so forth.

The control board is further provided with a CPU a static RAM SRAM a Synchronous DRAM SDRAM a flash memory an HDD a network interface controller that are connected to the ASIC .

CPU controls the entire system of the multifunctional apparatus . CPU and ASIC are connected each other through NB that is a CPU chip set. As described above even if the information of the interface of CPU is not available ASIC can be connected to CPU through NB.

CPU controls the entire operation of the functional apparatus . CPU executes processes of SCS SRM ECS MCS OCS FCS and NCS that are included in the platform under the control of the OS . CPU further runs the printer application the copier application the facsimile application the scanner application the net file application and the in line inspection application that are included in the application .

ASIC is an integrated circuit of which hardware is designed for image processing. The virtual memory spaces of the kernel and the processes of the application programs are mapped over the physical memory space provided by the SRAM and the SDRAM .

The flash memory is a non volatile random access memory that stores therein the application programs of the application the control services of the platform computer programs such as SRM and the user restriction charge information.

HDD is a storage device that stores therein image data computer programs font data form data and the distribution address information.

The operation panel is an input device with which the operator can operate the multifunctional apparatus and at the same time is a display device through which the system displays information to the operator.

The multifunctional apparatus may be connected to another multifunctional apparatus a computer and so forth through a network and thereby distribute image data and so forth. The multifunctional apparatus with such a distribution function stores therein the user information such as the distribution address information and the user restriction charge information. The multifunctional apparatus without such a distribution function may store only the user restriction charge information therein.

The method of controlling user information according to the present invention will be described using the multifunctional apparatus as an example of the information processing apparatus according to the present invention.

The parameters of various services modules and application programs are also stored in the flash memory and are controlled by the system initializing module not showed included in the SCS .

The distribution address information stored in the HDD is used to control the addressees and the senders of distribution information and is configured as showed in . is a table showing the distribution address information for example. The distribution address information of includes data items such as identification No. registration No. user name e mail address and the authorization user restriction for sending. The distribution address information stored in the HDD is controlled by the USC .

The UCS directly controls the distribution address information stored in the HDD and at the same time indirectly controls the user restriction charge information stored in the flash memory through the charge information controlling module .

In the case of the multifunctional apparatus without the distribution function no distribution address information is stored in the HDD . Even in this case the multifunctional apparatus can have the same interface as that of the multifunctional apparatus with the distribution function because the UCS can indirectly control the user restriction charge information stored in the flash memory through the charge information controlling module .

The multifunctional apparatus showed in stores the user restriction charge information in the flash memory and the distribution address information in the HDD . The user restriction charge information the distribution address information or both may be stored in the memory unit included in the FCU . Alternatively the portion of the user restriction charge information or the portion of the distribution address information may be stored in the memory unit included in the FCU .

The case where the facsimile application as an example of the application programs accesses the user information through the UCS will be described by reference to the drawings.

The UCS determines in which the flash memory or the HDD the user information requested by the facsimile application is stored. Then the UCS obtains the requested user information from either the flash memory or the HDD and provides the obtained user information to the facsimile application .

In particular when the facsimile application request for access to the distribution address information the UCS obtains a requested item of the distribution address information from the HDD and provides the obtained item to the facsimile application . When the facsimile application requests for access to the user restriction charge information the UCS obtains the requested item of the user restriction charge information from the flash memory through the charge information controlling module and provides the obtained item to the facsimile application .

Accordingly the facsimile apparatus can obtain a desired item of the user information from the UCS without designating where the desired item of the user information is stored. The initializing process to be performed by the facsimile application will be described below.

The UCS as a server creates a thread and opens a socket to wait for a request. The facsimile application as a client creates a thread and opens a socket to wait for an event. The facsimile application registers its subscription through the socket that the UCS opens.

The inter process communication between the request from the facsimile application received through the socket of the UCS and the event from the UCS received through the socket of the facsimile application enables the facsimile application and the UCS to operate in collaboration with each other.

The operation in which the scanner application displays the distribution address information on the operation panel will be described as an example by reference to the drawings. is a flow chart showing the operation in which an application program accesses the distribution address information.

The scanner application obtains configuration information from UCS using the API step S . The configuration information is information about the configuration of the UCS . The configuration information contains information about incorporation and parameters of the UCS and the charge information controlling module . This step S will be described in more detail later.

Subsequently to the step S the scanner application determines usable functions from the obtained configuration information and registers the functions to be used using the API at the UCS step S . After this registration in the UCS of the functions to be used the scanner application is automatically notified of the updates of the user information.

For example if e mail address information is usable the scanner application registers the e mail address information as a function to be used in the UCS . Subsequently when the e mail address information is updated the UCS informs the scanner application of the update. The step S will be described in more detail later.

Next to the step S the scanner application obtains tag set information and tag information from the UCS through the API step S .

In addition the Frequently Used tag is a special tag that is attached to all tag sets. Tags other than the Frequently Used are not attached to a plurality of tag sets. A more detailed description on this step will be given later.

Subsequent to the step S the scanner application obtains the entries attached to a selected tag from the UCS using the API step S .

Next after step S the scanner application creates an entry selection screen as showed in and displays the entry selection screen on the operation panel step S . is a schematic diagram illustrating the entry selection screen.

The entry selection screen of is created based on the tag set the tags and the entries. An icon in which a small image of three people is showed at the upper right corner indicates a group of accounts. An icon without the small image of three people at the upper right corner indicates an individual account.

Next after step S the scanner application determines whether an entry is selected from the entry selection screen step S . If the scanner application determines that an entry is already selected YES branch of S the scanner application performs step S. If the scanner application determines that no entry is selected yet NO branch of S the scanner application performs step S.

The scanner application obtains the detailed information of the selected entry from the UCS using the API step S and then performs step S. For example the scanner application may display the obtained detailed information of the selected entry in the information display field of the entry selection screen of .

The scanner application determines whether another tag is selected from the entry selection screen step S . If the scanner application determines that another tag is selected YES branch of S the scanner application returns to previous step S. If the scanner application determines that no tag is selected NO branch of S the scanner application performs step S.

The scanner application determines whether it is informed by the UCS of any update in the user information step S . If the scanner application determines that it receives the update information YES branch of S the scanner application returns to previous step S. If the scanner application determines that it has not received the update information NO branch of S the scanner application returns to previous step S.

Furthermore the steps of the flow chart showed in will be described in more detail by reference to the drawings. is a flow chart illustrating the step S of obtaining the configuration information. The scanner application requests the UCS to give the configuration information using the API for obtaining the configuration information step S . illustrates the API for obtaining the configuration information.

After step S the UCS provides the scanner application with the configuration information step S . The UCS creates the configuration information based on the incorporation information the parameters hardware configuration information and charge information configuration obtained from the charge information controlling module . The charge information controlling module sets up the charge information configuration based on the incorporation information the parameters and the hardware configuration information.

The configuration information of contains a service version usable functions and the maximum number of entries to be registered. The service version is incorporation information of the UCS . The usable functions are determined by the UCS based on the hardware configuration information and indicates the existence of the charge information and the e mail address information. The maximum number of entries to be registered is a control parameter of the UCS indicating the maximum number of entries that the UCS can register. An entry is the minimum unit containing the distribution address the sender a chargeable user and so forth and further contains a name and ID number.

The step S for registering functions to be used will be described in more detail. is a flow chart showing the step S for registering functions to be used. The scanner application determines usable functions based on the configuration information obtained in step S step S .

Subsequent to step S the scanner application selects functions to be used from the usable functions determined in step S step S . After step S the scanner application request the UCS to register the functions selected in step S using the API for registering functions to be used step S . illustrates the API for registering functions to be used.

After step S the UCS stores the corresponding relationship between the scanner application that requests for the registration and the registered functions step S . After this step S when the user information is updated the UCS informs the scanner application of the update.

Accordingly since the scanner application is informed of the update in the user information the scanner application can re obtain the updated user information.

A description about step S for obtaining a tag set and a tag will be given next. is a flow chart illustrating step S for obtaining a tag set and a tag.

The scanner application requests for all tag sets of the UCS using the API for obtaining a tag set step S . illustrates an API for obtaining a tag set.

Subsequent to step S the UCS provides all tag sets to the scanner application step S . illustrates a tag set. The tag set of contains data items such as an ID number the number of tags attached to the tag set and attached tags. The ID numbers of tags attached to the tag set are stored in the attached tags field.

After step S the scanner application selects tag sets and tags based on the reference value of the tag sets and the tags that the scanner application contains as the control parameters step S .

Subsequent to step S the scanner application requests for all tags attached to the tag sets selected in step S from the UCS using an API for obtaining tags step S . illustrates the API for obtaining tags.

Subsequent to step S the UCS reads tags from the HDD and provides the tags to the scanner application . illustrates tag information. The tag information of contains data items such as a tag ID number a tag category and a label. The tag category is used to identify whether the tag is frequently used or not.

The next step S for obtaining tag entries will be described below. is a flow chart showing step S for obtaining tag entries.

The scanner application requests the tag entries attached to the tag selected in step S from the UCS using an API for obtaining tag entries step S . illustrates the API for obtaining tag entries.

After step S the UCS reads the tag entries from the HDD and provides the read tag entries to the scanner application step S . illustrates the tag entries. The tag entries of contain data items such as an entry ID number an entry index number an entry category and a user name. The entry index number is attached so that users can easily memorize it. The entry category indicates whether a user is authorized to become an addressee of distribution whether the user is authorized to become a sender and whether the entry is an account or a group of accounts.

It is not necessary to obtain all the tag entries attached to the tag at once. Only tag entries that fit a screen of the operation panel may be obtained at first. The tag entries may be filtered by designating filtering conditions so that only entries having e mail addresses or being authorized to become senders for example are displayed.

The case in which an entry index number is input to a direct input field in the entry selection screen of will be described. is a flow chart showing a step for processing an input of an entry index number.

Using an API for obtaining an entry control number corresponding to an entry index number the scanner application obtains from the UCS an entry control number corresponding to the entry index number input in the direct input field step S . illustrates the API for obtaining an entry control number corresponding to an entry index number.

Subsequent to step S the scanner application using an API for obtaining a tag to which an entry is attached based on the entry control number of the entry obtains from the UCS the tags to which the entry is attached based on the entry control number obtained in step S step S . illustrates the API for obtaining tags to which an entry is attached from its entry control number.

Then the scanner application determines whether the tags obtained in step S is included in the currently selected tag set step S .

If the tags obtained in step S are included in the currently selected tag set YES branch of S the scanner application selects one tag included in the currently selected tag set out of the tags obtained in step S step S . If more than one tags obtained in step S are included in the currently selected tag set one of the tags needs to be selected in compliance with appropriate criteria such as the order of their tag control numbers for example.

On the other hand if none of the tags obtained in step S is included in the currently selected tag set NO branch of S the scanner application select one tag set and one tag in compliance with appropriate criteria step S .

After step S or step S the scanner application obtains from the UCS tag entries attached to the tag selected in step S or step S using the API for obtaining tag entries step S . Then the scanner application creates using the obtained tag entries the entry selection screen as showed in and displays it on the operation panel .

If the order of tag entries is known the step S may be easy. In the case where tag entries can be displayed in one screen of the operation panel and the order of a desired entry is the 20 for example only 12 entries starting with the 13entry may be obtained.

Using an API for obtaining the order of entries the scanner application obtains the order of entries attached to a tag from the UCS . illustrates the API for obtaining the order of entries.

Thanks to this API for obtaining the order of entries it is not necessary to repeat a step for obtaining 12 entries and determining whether the desired entry is included in the obtained entries.

The UCS provides an API for obtaining mail information as well. illustrates the API for obtaining the e mail information. The scanner application can obtain the mail information such as e mail addresses from the UCS using the API for obtaining mail information.

In the above description by reference to the facsimile application creates the screen to be displayed on the operation panel . Another separate module for creating a screen to be displayed on the operation panel may be provided.

As described above the facsimile application and the scanner application can share the screen creating module that is provided separately.

Since the multifunctional apparatus is provided with the UCS a plurality of applications programs such as the facsimile application and the scanner application can share the user information. Whichever the flash memory or the HDD the user information is stored in the application programs can obtain the user information by accessing only the UCS .

In the UCS is included in the control service but the UCS may be included in the application program for example. In addition in the facsimile application and the scanner application access the user information through the API provided by the UCS but the control service may access the user information through the API provided by the UCS for example.

Though the multifunctional apparatus is mainly described in this embodiment those skilled in the art may easily recognize that the present invention is also applicable to the information processing apparatus showed in . In the case of the information processing apparatus the user information processing unit instead of the UCS of controls the user information. In this case no unit corresponding to the SCS is required.

A detailed description of the information processing apparatus according to the second embodiment of the present invention will be given below. The hardware configuration of the information processing apparatus is identical to that of the information processing apparatus according to the first embodiment. The software configuration thereof is also substantially identical to the first embodiment. Accordingly only what is different will be mainly described.

The updating of the user information by the system initialization module included in the SCS using the UCS will be described below.

The UCS determines which the flash memory or the HDD the user information requested by the system initialization module is stored in. The UCS updates the user information stored in the flash memory or the HDD in response to the request from the system initialization module for updating.

In particular the UCS updates the distribution address information stored in the HDD in response to the request from the system initialization module for updating the distribution address information. The UCS also updates the user restriction charge information stored in the flash memory in response to the request from the system initialization module for updating the user restriction charge information. The UCS updates the user restriction charge information stored in the flash memory via the charge information controlling module .

Accordingly the system initialization module can update the user information without designating where the user information desired to be updated is stored. The system initialization module initiates the use of the UCS as follows.

The UCS as a server creates a thread for waiting for a request opens a socket and waits for the request. The system initialization module creates a thread to wait for an event opens a socket and waits for the event. At the same time the UCS registers a subscription through the socket.

The inter process communication between the request from the system initialization module and the event from the UCS through the socket of UCS and the socket of the system initialization module respectively enables the system initialization module and the UCS to collaborate.

Next the operation of the system initialization module to update the user information will be described by reference to another drawing. is a flow chart showing the updating operation of the distribution address information.

The system initialization module obtains the configuration information of the UCS using an API step S . The configuration information is information about the configuration of the UCS and includes the incorporation information and the setup parameter information of the UCS and the charge information controlling module .

Next to step S the system initialization module determines usable functions based on the obtained configuration information and registers the functions to be used in the UCS using an API step S .

Subsequent to step S the system initialization module creates a menu screen for system initialization and displays the menu screen on the operation panel step S . is a schematic diagram of the menu screen for the system initialization.

The menu screen for system initialization of includes one or more menu buttons corresponding to processing to update the user information. A user can select a desired operation by pressing a menu button displayed in the menu screen for system initialization on the operation panel .

After step S the system initialization module determines whether a menu item has been selected step S . If the system initialization module determines that a menu item has been selected from the system initialization menu screen YES branch of S the system initialization module processes the selected menu item step S . A detailed description on step S will be given later.

On the other hand if the system initialization module determines that no menu item has been selected from the system initialization menu yet NO branch of S the system initialization module repeats step S.

Step S will be described in detail by reference to the drawings below. If an item USER ADDRESS REGISTRATION UPDATE DELETION is selected from the system initialization menu the system initialization module displays an entry information updating screen as showed in on the operation panel . The system initialization module obtains information that is needed to create the entry information updating screen such as tag set information tag information and tag entries attached to a tag from the UCS using an API.

The entry information update screen of includes a tag set including one or more tags an entry display field displaying tag entries attached to the selected tag a new item button with which the user can open a new screen to create and register new entry information an update button for updating an entry information that is already registered and a deletion button for deleting a selected entry information.

The tag set is an ordered set of tags such as FREQUENTLY USED and AB . The tag is a labeled ordered set of entries. In the entry information updating screen of a tag AB is selected and 7 entries attached to the tag AB are displayed in an entry display field .

If the new entry button is selected the system initialization module displays an entry information registration screen as showed in on the operation panel so that the user can create a new entry and register it. is a schematic diagram showing the entry information registration screen.

The entry information registration screen of includes a field to input user name address a field to input the index number tag buttons to set a tag to which the entry is attached a user code button to enter a screen for inputting a user code a mail address button to enter a screen for inputting a mail address a facsimile number button to enter a screen for inputting a facsimile number a group button to enter a screen for setting a group and a registration button to register the entry information.

A user sets a user address name an index number and a tag to which the user is attached in the entry information registration screen. The user inputs the user code in the displayed screen for setting the user code by selecting the user code button . The user code is information indicating the restrictions on functions that the user can use.

The user can input the mail address by selecting the mail address button and displaying a screen for setting the mail address on the operation panel . The user further can input the facsimile address by selecting the facsimile number button and displaying a screen for inputting the facsimile number on the operation panel . Furthermore the user can select a group to which the entry is to be attached by selecting the group button and displaying a screen for setting a group on the operation panel .

After setting all information that is required for an entry the user selects the registration enter button of the entry information registration screen of . The system initialization module requests the UCS to update the entry information using various APIs.

The system initialization module requests the UCS to create the entry using an API showed in . illustrates an API for creating an entry. The UCS creates an entry in response to this API. When a new entry is created the new entry is displayed in the entry display field of the entry information updating screen for example.

The system initialization module also requests the UCS to set an entry tag to which the entry is to be attached using an API as showed in . illustrates the API for setting entry tag to which an entry is to be attached. The UCS sets the entry tag in response to the API for setting the entry tag to which the entry is to be attached.

Using an API showed in the system initialization module request the UCS to set a usercode. illustrates an API for setting the usercode. The UCS sets the usercode in compliance with the API.

Using an API as showed in the system initialization module requests the UCS to set a mail address. illustrates the API for setting the mail address. The UCS sets the mail address in compliance with the API for setting the mail address.

Using an API the system initialization module requests the UCS to set a facsimile number destination . The UCS sets the facsimile number destination in compliance with the API.

The system initialization module using an API as showed in determines whether the index number set in the entry information registration screen is already registered. If the index number is already registered the system initialization module requests the UCS to obtain an unused index number close to the already registered index number.

When the update button in the entry information updating screen of is selected the system initialization module displays the entry information registration screen for updating already registered entry information as showed in on the operation panel . The entry information registration screen showed when the update button is selected is different from the entry information registration screen showed when the new entry button is selected in that already registered entry information is displayed.

Using various APIs the system initialization module displays already registered entry information in the entry information registration screen. The system initialization module obtains a group to which an entry is attached from the UCS using an API showed in . illustrates an API for obtaining a group to which an entry is attached.

The description of the registration of information in the entry information registration screen will be omitted since the registration of information in the entry information registration screen displayed when the update button is selected is the same as that in the entry information registration screen displayed when the new entry button is selected.

After inputting all information needed to update the entry information the user selects the enter button . In response to the selection the system initialization module requests the UCS to update the entry information using various APIs.

For example the system initialization module uses an API as showed in to request the UCS to update the entry. illustrates the API for updating the entry. The UCS updates the entry in compliance with the API.

On the other hand when an entry in the entry display field of the entry information updating screen of is selected and then the delete button is selected the system initialization module deletes the entry using an API of . illustrates the API for deleting an entry.

When the editing tags is selected in the system initialization menu of the system operates as follows. When the editing tags is selected the system initialization module displays a tag editing screen on the operation panel . The tag editing screen includes the tag sets identical to that of the entry information updating screen of . Using an API the system initialization module obtains tag set information and tag information that are needed to create the tag editing screen from the UCS .

After inputting all information required to update tags the user selects the enter button of the tag editing screen for example. In response to the selection the system initialization module requests the UCS to update the tags using an API as showed in . illustrates an API for updating the tags. The UCS updates the tags in compliance with the API.

When changing entry order is selected in the system initialization menu screen the system operates as follows. When changing entry order is selected the system initialization module displays an entry order change screen on the operation panel . The entry order change screen includes as the entry information updating screen does a tag set and an entry display field in which entries attached to the selected tag are displayed. The system initialization module obtains the tag set information and tag information that are required for creating the entry order change screen from the UCS using an API.

The user changes the order of entries displayed in the entry display field for example as desired and selects the enter button of the entry order change screen for example. The system initialization module requests the UCS to change the order of entries using an API as showed in . illustrates an API for changing the order of entries. The UCS changes the order of entries in compliance with the API.

The UCS can support the following API. illustrates an API for setting sender authentication. The system initialization module requests the UCS to set the sender authentication information using the API for setting sender authentication. The sender authentication information is a password for example that can be used to identify a sender.

The numbers of entries accounts groups mail addresses and usercodes are used to create a screen to update the information of the entries the accounts the groups the mail addresses and the usercodes for example.

As described above since the UCS that controls the user information is provided the system initialization module can update the user information without designation of where the user information is stored.

In the UCS is included in the control service but the UCS may be included in the application program for example. In addition in and so forth the system initialization module requests the UCS to update the user information using the API provided by the UCS but the present invention is not limited to this example. The application programs such as the facsimile application may request the UCS to update the user information using the API provided by the UCS for example.

Though the multifunctional apparatus is mainly described in this embodiment those skilled in the art may easily recognize that the present invention is also applicable to the information processing apparatus showed in . In the case of the information processing apparatus the user information processing unit instead of the UCS of controls the user information. In this case no unit corresponding to the SCS is required.

The method of controlling the user information according to the third embodiment of the will be described below. The multifunctional apparatus will be mainly described as an example of the information processing apparatus according to the present invention.

A remote interface in the UCS and an external control apparatus communicates through the NCS and the network using the simple object access protocol SOAP for exchanging messages expressed in the extensible markup language XML .

The remote interface has one or more web service functions WSF for realizing web services. The external control apparatus remotely controls the user information by remotely accessing the WSF externally provided by the remote interface using SOAP.

The XML purser determines whether the WS request follows the documents type definition DTD analyzes the syntax of the DTD and converts the WS request into a tree shaped parse that the conversion library can use. The conversion library converts the parse provided by XML parser into WS requests. The WSF are functions provided by the method of the UCS that realized the web service.

The PROXY of the external control apparatus converts the WS request into XML and transmits the WS request expressed in XML to the NCS of the multifunctional apparatus . The NCS distributes the WS request expressed in the XML to XML parser in compliance with the uniform resource locator URL .

The XML parser converts the WS request expressed in XML to a tree shaped parse that the conversion library can use and then provides the WS request to the conversion library . The conversion library converts the parse provided by the XML parser into the WS request and identifies the WSF for example corresponding to the converted WS request. The UCS provides the external control apparatus with the web service such as the access to or the updating of the user information.

The PROXY the conversion library and the WSF are constructed based on the web service interface specification as showed in described in the web service description language WSDL . show the interface specification written in the WSDL. describes the web service to obtain a generation number.

A descriptive portion of the specification indicates that the input parameter used to obtain the generation number is ticket and the data type is binary. A descriptive portion of the specification indicates that the output parameter used to obtain the generation number is returnValue and generation out the data type of returnValue is enumeration and the data type of generation out is non negative integer.

A descriptive portion indicates which parameter the method corresponding to the obtaining of the generation number uses. In addition of the descriptive portion corresponds to WSF for example.

Next the access to the user information using the remote control will be described below by reference to the drawings. is a flow chart showing the access to the user information using the remote control.

The external control apparatus remote accesses the method provided by the remote interface and uses the web service for obtaining the configuration information. Input output parameters as showed in are used for the web service for obtaining the configuration information. illustrates the input output parameters used for the web service for obtaining the configuration information. illustrates the configuration information.

Subsequent to step S the external control apparatus remotely accesses the method provided by the remote interface and uses a web service for authenticating a user or an administrator step S . The web service for authenticating a user or an administrator uses input output parameters as showed in . illustrates the input output parameters used for the web service for authenticating a user or an administrator.

The web service receives a password from the external control apparatus as an input and outputs authentication information to the external control apparatus . The authentication information indicates that the user or the administrator is authenticated. The web service for accessing and updating the user information requires the authentication information as an input parameter. This requirement prohibits unauthenticated person from accessing the user information.

After step S the external control apparatus remotely accesses the method provided by the remote interface and uses a web service for obtaining generation number step S . The web service for obtaining the generation number uses the input output parameters as showed in .

Subsequent to step S the external control apparatus remote accesses the method provided by the remote interface and uses a web service for obtaining the tag set step S . Input output parameters as showed in are used in the web service for obtaining the tag set. illustrates the input output parameters used in the web service for obtaining the tag set.

The web service for obtaining the tag set receives the authentication information and the generation number as input parameters and outputs the generation number and an array structured as the tag set information to the external control apparatus as an output. illustrates the data structure of a tag set.

After step S the external control apparatus remotely accesses the method provided by the remote interface and uses a web service for obtaining tags for each tag set obtained in step S. The input output parameters as showed in are used in the web service for obtaining tags. illustrates the configuration of the input output parameters used in the web service for obtaining tags.

The web service for obtaining tags receives the authentication information the generation number and the tag set index number as input parameters and outputs the generation number and the array structured as a tag to the external control apparatus as output parameters. illustrates the data structure of a tag.

Subsequent to step S the external control apparatus remotely accesses the method provided by the remote interface and uses a web service for obtaining tag entries for each tag obtained in step S step S . Input output parameters as showed in are used in the web service for obtaining tag entries. illustrates the input output parameters used in the web service for obtaining tag entries.

The web service for obtaining tag entries receives the authentication information the generation number the tag index number filtering condition entry offset and the maximum number of tag entries to be obtained simultaneously as input parameters. On the other hand the web service for obtaining tag entries outputs the generation number the number of entries that satisfy the condition whether all entries that satisfy the condition are obtained and the array of entry information to the external control apparatus . illustrates the filter conditions. illustrates the data structure of entry.

In the case of filtering members showed in are usable. If a plurality of members are set on it means the logical sum of the on members. If all is on all entries are obtained whatever the other members are. If only mail addressee and user code are on entries having mail addresses or usercodes are obtained for example.

After step S the external control apparatus remotely accesses the method provided by the remote interface and uses a web service for obtaining detailed entry information step S .

In the case where account information is obtained as the detailed entry information the web service for obtaining account information uses input output parameters as showed in . illustrates input output parameters used for the web service for obtaining the account information. The web service for obtaining the account information receives the authentication information the generation number the array of entry ID numbers and the designation of members to be obtained from the external control apparatus as input parameters and outputs the generation number and the array of account information to the external control apparatus as output parameters. illustrates the data structure of an account. illustrates the data structure of a mail address. illustrates the data structure of facsimile destination information. illustrates the data structure of the usercode information.

In the case of obtaining group information as the detailed entry information a web service for obtaining the group information uses input output parameters as showed in . shows the input output parameters used in the web service for obtaining group information. The web service for obtaining the group information receives as input parameters the authentication information the generation number the array of entry index numbers the designated member to be obtained from the external control apparatus and outputs the generation number the array of group information to the external control apparatus .

After step S the external control apparatus creates a screen as showed in based on the information obtained in steps S S step S . illustrates the screen created in step S.

The screen of has four tabs with which the user can choose information about the number of printed pages by user CHARGE INFO the user restriction by the user USER RESTRICTION the e mail addresses E MAIL INFO and the facsimile addresses FAX INFO . illustrates the case where the e mail addresses are displayed.

After step S the external control apparatus displays the screen created in step S. Since the user information is accessible using the external control apparatus instead of the operation panel of the multifunctional apparatus more items of the user information can be displayed simultaneously.

The updating of the user information through the remote access will be described by reference to the drawings. After displaying the screen in compliance with the flow chart of for example the external control apparatus remotely accesses the method provided by the remote interface to realize the following a web service for displacing tag information of a tag set a web service for displacing entries of a tag a web service for deleting an entry having a designated ID number a web service for adding an account a web service for updating account information a web service for adding a group a web service for updating the group information and so forth.

Next the backup and restoring of the user information using remote control will be described below by reference to the drawings. The backup of the user information can be performed by using the access operation to the user information described above. The external control apparatus obtains the user information using the access operation of the user information and then stores the obtained user information in a storage device so as to backup it.

On the other hand the restoring of the user information is realized by following the steps described in the flow chart of for example. shows a flow chart of the restoring operation of the user information using remote control for example.

The external control apparatus remotely accesses the method provided by the remote interface and uses the web service for processing before the restoring step S .

After step S the external control apparatus remotely accesses the method provided by the remote interface and uses the web service for deleting all entries step S . The charge information stored in the flash memory however is not deleted.

After step S the external control apparatus remotely accesses the method provided by the remote interface and uses the web service for displacing tags in a tag set that is backed up already step S .

After step S the external control apparatus remotely accesses the method provided by the remote interface and uses the web service for adding all groups that are already backed up step S .

After step S the external control apparatus remotely accesses the method provided by the remote interface and uses the web service for adding all accounts that are already backed up step S .

Subsequent to step S the external control apparatus remotely accesses the method provided by the remote interface and uses the web service for displacing entries in a tag that is already backed up step S .

After step S the external control apparatus remotely accesses the method provided by the remote interface and uses the web service for processing after the restoring step S .

Following the steps of the external control apparatus can restore the user information stored in the flash memory or the HDD using the backup user information. As described above thanks to the remote interface the user can remotely control the user information stored in the multifunctional apparatus according to this embodiment of the present invention.

In the case of the configuration showed in the UCS is included in the control service but the present invention is not limited to this configuration. The UCS may be provided in the application programs .

Though the multifunctional apparatus is described in this embodiment those skilled in the art may recognize that the present invention is easily applicable to the information processing apparatus . In the case of the information processing apparatus the user information control unit instead of the UCS controls the user information. In this case no component corresponding to the SCS is required.

This patent application is based on Japanese priority patent applications No. 2002 050539 filed on Feb. 26 2002 No. 2002 050540 filed on Feb. 26 2002 No. 2002 050547 filed on Feb. 26 2002 No. 2003 39974 filed on Feb. 18 2003 No. 2003 39975 filed on Feb. 18 2003 No. 2003 39976 filed on Feb. 18 2003 No. 2003 39977 filed on Feb. 18 2003 No. 2003 39978 filed on Feb. 18 2003 and No. 2003 39979 filed on Feb. 18 2003 the entire contents of which are hereby incorporated by reference.

