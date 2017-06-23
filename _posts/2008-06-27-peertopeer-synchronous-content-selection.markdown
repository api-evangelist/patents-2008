---

title: Peer-to-peer synchronous content selection
abstract: Various technologies for sharing digital images within an instant messaging (IM) session between two users. In one implementation, a first user uploads a set of images to the second user. The set of images may be displayed as thumbnails on the displays of both users. By clicking on one of the thumbnails, either user may make the associated image appear as a larger image on both users' displays. In the event that both users click on different images simultaneously, or near-simultaneously, a protocol may be employed that selects which image is displayed.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08285812&OS=08285812&RS=08285812
owner: Microsoft Corporation
number: 08285812
owner_city: Redmond
owner_country: US
publication_date: 20080627
---
Instant messaging IM is a technology that facilitates real time text based communication between two or more participants over computer networks e.g. the Internet. Although IM typically happens in real time some systems allow the sending of messages to people not currently logged on offline messages thus removing much of the difference between IM and e mail.

Many IM services have additional features such as immediate receipt of acknowledgment group chatting conference services including voice and video and file transfer. In certain cases it is possible to save an IM conversation for later reference. In such cases instant messages are typically logged in a local message history. Logging instant messages may facilitate the ready exchange of unwieldy information like web addresses or document snippets.

Described herein are implementations of various technologies for sharing digital images within an instant messaging IM session between two users. In one implementation a first user uploads a set of images to the second user. The set of images may be displayed as thumbnails on the displays of both users. By clicking on one of the thumbnails either user may make the associated image appear as a larger image on both users displays. In the event that both users click on different images simultaneously or near simultaneously a protocol may be employed that selects which image is displayed.

In another implementation while the images are uploading to the second user s computer the second user may modify a sequence within which the images upload. After the first user initiates the upload the thumbnails may appear on both users displays in the sequence that the images will upload. The second user may click on a thumbnail that is not yet uploaded to move the associated image to the top of an upload queue. In response the sequence of the displayed thumbnails may change on both users displays to reflect the new upload sequence.

In one implementation as each image is uploaded a portion of the associated thumbnail appears as grayed out to indicate a proportion of the image that is uploaded in the fashion of a progress bar.

The above referenced summary section is provided to introduce a selection of concepts in a simplified form that are further described below in the detailed description section. The summary is not intended to identify key features or essential features of the claimed subject matter nor is it intended to be used to limit the scope of the claimed subject matter. Furthermore the claimed subject matter is not limited to implementations that solve any or all disadvantages noted in any part of this disclosure.

As to terminology any of the functions described with reference to the figures can be implemented using software firmware hardware e.g. fixed logic circuitry manual processing or a combination of these implementations. The term logic module component or functionality as used herein generally represents software firmware hardware or a combination of these implementations. For instance in the case of a software implementation the term logic module component or functionality represents program code or declarative content that is configured to perform specified tasks when executed on a processing device or devices e.g. CPU or CPUs . The program code can be stored in one or more computer readable media.

More generally the illustrated separation of logic modules components and functionality into distinct units may reflect an actual physical grouping and allocation of such software firmware and or hardware or may correspond to a conceptual allocation of different tasks performed by a single software program firmware program and or hardware unit. The illustrated logic modules components and functionality can be located at a single site e.g. as implemented by a processing device or can be distributed over plural locations.

The terms machine readable media or the like refers to any kind of medium for retaining information in any form including various kinds of storage devices magnetic optical solid state etc. . The term machine readable media also encompasses transitory forms of representing information including various hardwired and or wireless links for transmitting the information from one point to another.

The techniques described herein are also described in various flowcharts. To facilitate discussion certain operations are described in these flowcharts as constituting distinct steps performed in a certain order. Such implementations are exemplary and non limiting. Certain operations can be grouped together and performed in a single operation and certain operations can be performed in an order that differs from the order employed in the examples set forth in this disclosure.

The computing system may include two client computers that may be peer connected over a network . Each of the client computers may include a central processing unit CPU a system memory a storage a network interface and a system bus that couples various system components to the CPU . Although only one CPU is illustrated in the client computer it should be understood that in some implementations the client computer may include more than one CPU .

The system bus may be any of several types of bus structures including a memory bus or memory controller a peripheral bus and a local bus using any of a variety of bus architectures. By way of example and not limitation such architectures include Industry Standard Architecture ISA bus Micro Channel Architecture MCA bus Enhanced ISA EISA bus Video Electronics Standards Association VESA local bus and Peripheral Component Interconnect PCI bus also known as Mezzanine bus.

Additionally the user may enter commands and information into the client computer through input devices . The input devices may include devices such as a keyboard and pointing device. Other input devices may include a microphone joystick game pad satellite dish scanner or the like. These and other input devices may be connected to the CPU through a serial port interface coupled to the system bus but may be connected by other interfaces such as a parallel port game port or a universal serial bus USB .

One or more output devices may also be connected to the system bus via an interface such as a video adapter. The output devices may include a display monitor or other peripheral output devices such as speakers and printers.

The system memory may include a read only memory ROM a random access memory RAM and a basic input output system BIOS none of which are shown . The BIOS may contain the basic routines that help transfer information between elements within the client computer such as during start up.

The storage may include a hard disk drive for reading from and writing to a hard disk a magnetic disk drive for reading from and writing to a removable magnetic disk and an optical disk drive for reading from and writing to a removable optical disk such as a CD ROM or other optical media. The hard disk drive the magnetic disk drive and the optical disk drive may be connected to the system bus by a hard disk drive interface a magnetic disk drive interface and an optical drive interface respectively. The drives and their associated computer readable media may provide nonvolatile storage of computer readable instructions data structures program modules and other data for the client computer . Neither the drives nor their respective interfaces are shown in .

Although the client computer is described herein as having a hard disk a removable magnetic disk and or a removable optical disk it should be appreciated by those skilled in the art that the client computer may also include other types of computer readable media that may be accessed by a computer. For example such computer readable media may include computer storage media and communication media.

Computer storage media may include volatile and non volatile and removable and non removable media implemented in any method or technology for storage of information such as computer readable instructions data structures program modules or other data.

Computer storage media may further include RAM ROM erasable programmable read only memory EPROM electrically erasable programmable read only memory EEPROM flash memory or other solid state memory technology CD ROM digital versatile disks DVD or other optical storage magnetic cassettes magnetic tape magnetic disk storage or other magnetic storage devices or any other medium which can be used to store the desired information and which can be accessed by the client computer .

Communication media may embody computer readable instructions data structures program modules or other data in a modulated data signal such as a carrier wave or other transport mechanism and may include any information delivery media. The term modulated data signal may mean a signal that has one or more of its characteristics set or changed in such a manner as to encode information in the signal.

By way of example and not limitation communication media may include wired media such as a wired network or direct wired connection and wireless media such as acoustic RF infrared and other wireless media. Combinations of any of the above may also be included within the scope of computer readable media.

Further the client computer may operate in a networked environment using logical connections to one or more remote computers such as another client computer . The logical connections may include the network interface connected to the network . The network may be any network or collection of networks such as enterprise wide computer networks intranets local area networks LAN and wide area networks WAN . In one implementation the network may be the Internet.

A number of program or data modules may be stored in the system memory and the storage . More specifically the storage may contain original media . The original media may contain images or other media that a user may share with another user during an instant messaging IM session. The original media may be stored in a format suitable for capturing quality image data. In one implementation the original media may be stored as 1024 768 pixel images.

The system memory may contain an operating system an IM application thumbnail media display media and an upload queue . The operating system may be any suitable operating system that may control the operation of a networked personal or server computer such as Windows Vista Mac OS X Unix variants e.g. Linux and BSD and the like.

The IM application may be any software that conducts an IM session between two or more client computers such as Windows Live Messenger. Typically a host user initiates an IM session with one or more guest users.

The IM application may include a photoshare application . The photoshare application may enable both the host and the guest to share the original media on the host s and guest s respective client computers with the other user during the IM session. The photoshare application is described in greater detail with reference to .

The thumbnail media may include reduced size versions of the original media that the host guest may share with the other user. The thumbnail media may be stored in a format that is suitable for rapid transfer over the network . In one implementation the thumbnail media may be stored as 50 15 pixel images. The thumbnail media may be displayed on the output device of both client computers during the IM session. The thumbnail media are described in greater detail with reference to .

Like the thumbnail media the display media may also include versions of the original media in a reduced size format. However the display media may be stored in a format that facilitates transfer over the network and viewing on the output device . An example of the display media is illustrated in .

When sharing images from the original media the host or guest may upload associated display media to the other user s client computer . For clarity the client computer of the user that shares the media is referred to as the source. Similarly the client computer of the user with whom the media is shared is referred to as the destination.

The upload queue may include the display media that the photoshare application has not yet completed uploading. The upload queue is described in greater detail with reference to .

At step the photoshare application may receive a selection to upload the original media that the host guest is sharing. However because the original media may be in a format that is not conducive to ready transfer during the IM session the original media may be converted to a more suitable format before uploading to the destination.

As such at step the photoshare application may create the display media version of the original media that is selected. During the upload of the display media the photoshare application may present the contents of the upload queue by displaying the thumbnail media associated with the display media being uploaded. In one implementation the sequence within which the display media is uploaded may be presented by displaying the thumbnail media in the same sequence as the associated display media are uploaded. Accordingly at step the thumbnail media associated with the selected original media may be created.

At step the photoshare application may upload the thumbnail media to the destination. In one implementation the thumbnail media may be uploaded in the same sequence that the respective display media is uploaded.

At step the photoshare application may update the upload queue on the source to reflect the sequence in which the display media are uploaded to the destination. At step the display media may be uploaded to the destination in the sequence recorded in the upload queue .

As stated previously the host or guest may upload the display media to the destination. For the sake of clarity the following implementations are described under a scenario where the host uploads the display media to the guest s client computer . In other words the host s client computer is the source and the guest s client computer is the destination. It should be understood that the roles as described in the following implementations may be reversed when the guest uploads the display media to the host s client computer .

At step the guest s photoshare application may receive the thumbnail media from the source. At step the photoshare application may display the thumbnail media on the output device in the sequence in which the thumbnail media are received.

In some cases the guest may want to change the sequence in which the display media are uploaded. For example the guest may see an image of interest in one of the thumbnail media that is at the end of the upload queue .

In one implementation the guest may click on the thumbnail media of interest. In response the corresponding display media may be moved to the top of the upload queue . In this manner the corresponding display media may be the next item uploaded to the destination. Accordingly at step the guest s photoshare application may receive a selection of one of the thumbnail media .

At step the guest s photoshare application may send the selection to the source. In one implementation the selection may indicate the display media associated with the selected thumbnail media to move to the top of the upload queue .

At step the guest s photoshare application may update the display of the thumbnail media to reflect the new sequence of the display media in the upload queue .

The thumbnail region may display the thumbnail media that are uploaded to the destination. In this example the thumbnail region includes three thumbnail media labeled A B and C. In one implementation the thumbnail region may include a scroll bar to accommodate viewing multiple thumbnail media .

Additionally referring back to during the upload of the display media the corresponding thumbnail media may be displayed in the fashion of a progress bar. In this fashion a grayed out portion of the thumbnail may indicate a proportion of the media that is uploaded. This grayed out portion may show the progress of the upload. Once the upload of the display media is complete the thumbnail media image may appear without additional effects.

The photoshare application may display the display media in the display region based on a user selection in the thumbnail region . In other words in response to the host or guest clicking on one of the thumbnail media the photoshare application may display the display media that corresponds to the thumbnail media selected. The same display media may be displayed in both the host s and guest s display regions . The display region is described in greater detail with reference to .

Although the guest and host can independently scroll through the thumbnail media in their respective thumbnail regions a selection by either user as described above may modify the thumbnail region of the other. For example in response to the host clicking on one of the thumbnail media the same thumbnail media displayed in the host s thumbnail region may then be displayed in the guest s thumbnail region .

In some circumstances the guest may want copies of the original media that corresponds to the display media uploaded to the destination. In one implementation the photoshare application may enable the guest to request a copy of the original media . For example in response to a mouse over action in the display region the photoshare application may display a context menu not shown that includes a download icon not shown . The guest may click on the download icon to download a copy of the original media that corresponds to the display media in the display region .

In another implementation the context menu may include a download album icon not shown . In response to the guest s click on the download album icon the photoshare application may download the original media that corresponds to all the display media that the host uploads to the guest s client computer during the current IM session.

The user interface may also enable the host to remove the display media that are uploaded to the guest s client computer . In one implementation the photoshare application may display a context menu that includes a delete icon not shown in response to the host s mouse over action on one of the thumbnail media . In response to the host clicking on the delete icon the photoshare application may delete the thumbnail media corresponding to the thumbnail media mouse over and the corresponding display media from the guest s client computer .

At step a change request may be received by the client computer . The change request may be a request to change the display media in the display region . In one implementation the change request may include sequence parameters that may indicate a conflict from simultaneous or near simultaneous change requests from both the host and the guest.

The change request may be sent by the guest to the host or by the host to the guest. To facilitate synchronous displays of the display media one user s change requests may be prioritized over the other user s change requests in the event of simultaneous or near simultaneous change requests. In one implementation the prioritized user may be the host. For example at step if the change request is sent by the host the method proceeds to step . At step the photoshare application may display the display media identified in the change request in the display region.

If the change request is not sent by the host the method proceeds to step . At step if the request sent by the guest is sent in sequence the method proceeds to step . In the event that the guest sends the change request nearly simultaneously with the host sending a second change request the guest s request may be out of sequence. If the guest s change request is sent out of sequence i.e. before the guest receives the host s near simultaneous change request the method proceeds to step . At step the change request may be ignored.

It should be understood that the various technologies described herein may be implemented in connection with hardware software or a combination of both. Thus various technologies or certain aspects or portions thereof may take the form of program code i.e. instructions embodied in tangible media such as floppy diskettes CD ROMs hard drives or any other machine readable storage medium wherein when the program code is loaded into and executed by a machine such as a computer the machine becomes an apparatus for practicing the various technologies. In the case of program code execution on programmable computers the computing device may include a processor a storage medium readable by the processor including volatile and non volatile memory and or storage elements at least one input device and at least one output device. One or more programs that may implement or utilize the various technologies described herein may use an application programming interface API reusable controls and the like. Such programs may be implemented in a high level procedural or object oriented programming language to communicate with a computer system. However the program s may be implemented in assembly or machine language if desired. In any case the language may be a compiled or interpreted language and combined with hardware implementations.

Although the subject matter has been described in language specific to structural features and or methodological acts it is to be understood that the subject matter defined in the appended claims is not necessarily limited to the specific features or acts described above. Rather the specific features and acts described above are disclosed as example forms of implementing the claims.

