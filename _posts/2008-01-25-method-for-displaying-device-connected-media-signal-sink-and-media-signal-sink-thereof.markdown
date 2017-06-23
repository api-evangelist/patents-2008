---

title: Method for displaying device connected media signal sink and media signal sink thereof
abstract: A method for displaying a menu corresponding to one or more devices included in the one or more media signal sources connected to the media signal sink. The method includes checking connection states of the one or more signal sources to the signal sink, displaying menu items of the one or more devices included in one or more signal sources connected to the signal sink in a graphic user interface (GUI) screen, based on a result of the connection state check; selecting a specific one of the menu items displayed in the GUI screen, determining whether a device corresponding to the selected menu item, among the one or more devices included in the one or more signal sources, is in its on or off state, generating a signal for turning-on the corresponding device when it is determined that the corresponding device is in its off state and transmitting the generated turning-on signal to the corresponding device.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09009597&OS=09009597&RS=09009597
owner: LG Electronics Inc.
number: 09009597
owner_city: Seoul
owner_country: KR
publication_date: 20080125
---
The present invention relates to media signal processing and more particularly to a media signal sink having a graphic user interface GUI function and a method for displaying devices connected thereto.

Recently a high definition multimedia interface HDMI standard has been developed and published which transmits a digital video signal and a digital audio signal via a single digital interface with a bandwidth of 5 Gbps or more. The HDMI is a digital audio video interface that can transmit a stream not compressed. This HDMI provides an interface between a compatible digital audio video source and a compatible digital audio video monitor for example a television TV .

Under the condition that an audio video monitor is interfaced with audio video sources in an HDMI manner the user has to control the audio video sources and the audio video monitor individually. For this reason much time and inconvenience are involved in controlling the sources and monitor. As a result there is a need for a user interface environment to control them in an integrated manner.

One approach is to provide a GUI screen through an audio video monitor. However this GUI screen just lists and shows only various output formats for example a component RGB HDMI etc. and various HDMI ports for example HDMI1 HDMI2 etc. of audio video sources.

Moreover in the above mentioned GUI method in order to select a desired mode from the list on the GUI screen the user is required to know which audio video source was pinned to which port of the audio video monitor.

In addition in the case where an audio video source has a plurality of devices the user cannot access the respective devices individually through the GUI screen. Further the user is unable not only to know the type of a currently operable device through the GUI screen but also to easily identify that device.

An object of the present invention devised to solve the problem lies on a media signal sink and a method for displaying devices connected thereto wherein under the condition that various devices are interconnectable in an HDMI manner a GUI screen is provided to enable the user to easily know and control the states of the respective devices in an integrated manner.

The object of the present invention can be achieved by providing in a method for operating a media signal sink connected with one or more signal sources each having one or more devices a method for displaying one or more devices connected to the media signal sink comprising checking connection states of the signal sources to the signal sink and displaying menu items of the devices of the signal sources connected to the signal sink in a graphic user interface GUI screen based on a result of the connection state check.

In the GUI screen menu items of the same type of devices among the devices of the signal sources may be displayed under the condition that they are grouped into one group. Alternatively in the GUI screen menu items of devices corresponding to the same type of signal sources among the devices of the signal sources may be displayed under the condition that they are grouped into one group.

In the GUI screen menu items of devices selectable by a user among the devices of the signal sources and menu items of devices non selectable by the user may be displayed distinguishably from each other.

In the GUI screen a menu item of a device selected by a user among the devices of the signal sources and menu items of the other devices not selected by the user may be displayed distinguishably from each other.

In the GUI screen a menu item of a device currently in operation among the devices of the signal sources and menu items of the other devices not in operation may be displayed distinguishably from each other.

The step of checking the connection states of the signal sources to the signal sink may comprise checking a connection state of each of the devices of the signal sources to the signal sink by identifying a unique address recorded in each of the devices of the signal sources.

The method for displaying the one or more devices connected to the media signal sink may further comprise selecting a specific one of the menu items displayed in the GUI screen generating a command for control of a device corresponding to the selected menu item among the devices of the signal sources and transmitting the generated control command to the corresponding device to operate the corresponding device.

Alternatively the method for displaying the one or more devices connected to the media signal sink may further comprise selecting a specific one of the menu items displayed in the GUI screen determining whether a device corresponding to the selected menu item among the devices of the signal sources is in its on or off state generating a signal for turning on of the corresponding device and a command for control of the corresponding device if it is determined that the corresponding device is in its off state and transmitting the generated turning on signal and control command to the corresponding device to operate the corresponding device.

In the GUI screen each of the menu items may be indicated by at least one of a device name and an icon.

In another aspect of the present invention provided herein is a media signal sink with a graphic user interface GUI function connected with one or more signal sources each having one or more devices the media signal sink comprising a main processor for checking connection states of the signal sources to the signal sink a GUI screen creator for creating a GUI screen to display menu items of the devices of the signal sources connected to the signal sink based on a result of the connection state check of the main processor and a display device for displaying the GUI screen created by the GUI screen creator.

The media signal sink may further comprise an auxiliary processor for transmitting receiving a GUI frame containing the unique address to from each of the signal sources and outputting the received GUI frame to the main processor.

Reference will now be made in detail to the preferred embodiments of the present invention examples of which are illustrated in the accompanying drawings. Wherever possible the same reference numbers will be used throughout the drawings to refer to the same or like parts. Besides although terms used in the present invention are possibly selected from the currently well known ones some terms are arbitrarily chosen by the inventor in some cases so that their meanings are explained in detail in the following description. Hence the present invention should be understood with the intended meanings of the corresponding terms chosen by the inventor instead of the simple names or meanings of the terms themselves.

Hereinafter for a better understanding of the present invention the overall system of at least one signal source and a media signal sink will be described with reference to .

Referring to the signal sink receives and processes an audio and or video signal from each of the signal sources to and shows a result of the processing through a display device not shown or monitor not shown . The signal sink functioning in this manner may be a video display device such as a television TV projector or monitor. Also the signal sink may include at least one device.

Each of the signal sources to can store reproduce and or process an audio and or video signal. Also each of the signal sources to provides an audio and or video signal to the signal sink and is interfaced with the signal sink via at least one physical port. Each of the signal sources to may include a plurality of devices. Provided that a plurality of signal sources are connected in the form of a composite unit to the signal sink via one physical port a description of the present invention will be given under the condition that the composite unit is regarded as one signal source and the respective signal sources included in the composite unit are regarded as devices.

Applied as each of the signal sources to may be an audio video source such as a set top box STB a personal computer PC a video game system a digital video disc DVD recorder a hard disk drive HDD recorder included in an STB or DVD recorder a home theater system HTS or a video cassette recorder VCR .

The signal sink and the signal sources to are interconnected in an HDMI manner via the lines to for HDMI channels and the HDMI CEC lines to . Although the HDMI channel line and the CEC line are shown to be separated from each other for a better understanding of the present invention it should be noted here that they are integrated into one cable.

Hereinafter the configuration and operation of the signal sink according to one embodiment of the present invention will be described with reference to .

The signal source which corresponds to each of the signal sources to shown in includes a main processor auxiliary processor HDMI transmitter and HDMI connector .

The signal sink which corresponds to the signal sink shown in includes an HDMI connector HDMI receiver main processor auxiliary processor user command input unit GUI screen creator video audio processor display device and speaker .

The auxiliary processor transmits a CEC frame to the signal sink through a pin of the HDMI connector or receives a CEC frame transmitted from the signal sink through the pin and provides a header block and data block of the received CEC frame to the main processor .

The auxiliary processor transmits a CEC frame to the signal source through a pin of the HDMI connector or receives a CEC frame transmitted from the signal source through the pin and provides a header block and data block of the received CEC frame to the main processor .

The pin or can be assigned a No. 13 pin of the HDMI connector or when the HDMI connector or is A type a No. 22 pin when the HDMI connector or is B type and a No. 14 pin when the HDMI connector or is C type.

Each of the auxiliary processors and can use an interrupt of for example a 0.1 ms unit to sample a CEC frame. Although the auxiliary processors and may be included in the main processors and respectively it is preferable that they be present separately from the main processors and because the 0.1 ms unit sampling may act as a load on the operations of other parts. In addition each of the auxiliary processors and performs a CEC line error handling process CEC frame validation determination process and CEC frame re transmission process.

Each of the main processors and processes a CEC protocol layer and application layer. The CEC protocol layer is a middleware layer that implements the operation of a CEC protocol and provides a standard application programming interface API for application development. A porting layer may also be provided in consideration of a hardware modification of the auxiliary processor or etc. The main function of the CEC protocol layer is to configure and manage a device tree with respect to devices connected to the signal link or signal source and manage the status of each device. In particular the CEC protocol layer encapsulates CEC protocol information from the application layer therein.

The HDMI transmitter of the signal source receives audio video data from the main processor and transmits the received audio video data to the signal sink through the HDMI connector . At this time the audio video data is transmitted over a transition minimized differential signaling TMDS link which is also called a channel link. A TMDS clock is a clock for TMDS.

The HDMI receiver of the signal sink receives audio video data transmitted from the signal source through the HDMI connector and outputs the received audio video data to each of the main processor and video audio processor . The user command input unit receives a command inputted by the user and outputs the received command to the main processor .

In the case where the user command input unit is implemented with a remote controller a hotkey can be arranged in the remote controller in the form of a button. The hotkey is pushed by the user when the display of a GUI screen is requested by the user.

The main processor controls the respective parts and of the signal sink . The video audio processor performs an audio signal and or video signal processing operation respectively with respect to audio and or video data received from the HDMI receiver under the control of the main processor .

A result of the video signal processing operation of the video audio processor is visually provided to the user through the display device and a result of the audio signal processing operation of the video audio processor is aurally provided to the user through the speaker .

The GUI screen creator creates a GUI screen under the control of the main processor and outputs the created GUI screen to the video audio processor . The video audio processor mixes processes the GUI screen created by the GUI screen creator with a video signal inputted from the HDMI receiver and displays a result of the processing through the display device .

The signal source shown in may receive an audio video signal from the signal source and deliver the received audio video signal to the signal sink or otherwise may process the audio video signal from the signal source by itself. That is provided that the signal source has the respective parts of the signal sink shown in it may act as a signal sink for the signal source .

Hereinafter a signal sink operating method for a GUI function according to the present invention will be described with reference to . For a better understanding of the present invention the signal sink operating method is assumed to be performed by the signal sink shown in but the present invention is not limited thereto.

The main processor determines whether a GUI request command from the user has been inputted from the user command input unit Step .

Upon determining that the GUI request command from the user has been inputted the main processor determines whether there is a signal source connected to the signal sink Step .

As stated previously the signal source may have one device but may also have a plurality of devices. As a result at step the main processor checks connection states of all devices thereto.

In order to assist this role of the main processor the auxiliary processor receives a CEC frame or GUI frame from the signal source and outputs a header data block of the received CEC frame to the main processor .

The main processor can check a connection state of a device thereto using a unique address contained in the header of the CEC frame. This unique address is an inherent logical address or physical address that each device has uniquely.

Based on the unique address that is the logic address or physical address the main processor can identify each device and check a connection state of each device thereto.

The signal sink may create a unique address in a vendor specific data block VSDB and deliver the created unique address to a corresponding signal source and check a connection state of a given device by identifying the unique address.

The main processor outputs a result of the device connection state check to the GUI screen creator Step .

Using the check result provided from the main processor the GUI screen creator creates a GUI screen showing a connection state of each device and outputs the created GUI screen to the video audio processor Step .

The video audio processor processes the GUI screen created by the GUI screen creator and displays a result of the processing through the display device . At this time as a result of the processing menu items indicating the connection states of the respective devices are displayed in the GUI screen Step .

If there is no device connected to the signal sink the GUI screen creator may create a GUI screen having menu items indicating such a situation but may create a separate message for example No device connected as a GUI screen Step .

Hereinafter a method for creating a GUI screen in the GUI screen creator and the created GUI screen will be described with reference to and .

As shown in in the GUI screen each menu item can be indicated by at least one of a device name TV DISC VCR HDD or the like and an icon. As a result the user can recognize a device connection situation more easily through the GUI screen.

In the GUI screen menu items corresponding to functions selectable by the user and menu items corresponding to functions non selectable by the user can be displayed distinguishably from each other. For example as shown in the letters of menu items and corresponding to functions selectable by the user may be displayed with a bright color and the letters of a menu item not so may be displayed with a gray color .

If the signal source connected to the signal sink has a device HDD Recorder the letters of the menu item are displayed with the bright color to indicate that the user can select an HDD Recorder Appreciation function. In contrast if the signal source connected to the signal sink has no device VCR the letters of the menu item are displayed with the gray color to indicate that the user cannot select a VCR Appreciation function.

In another embodiment of the present invention menu items corresponding to functions selectable by the user may be visible in the GUI screen and menu items corresponding to functions non selectable by the user may be invisible in the GUI screen.

On the other hand in the GUI screen a menu item corresponding to a function selected by the user and menu items corresponding to functions not selected by the user can be displayed distinguishably from each other. For example as shown in the menu item corresponding to the function selected by the user may be displayed with a background color different from that of the other menu items and .

In the GUI screen a menu item corresponding to a function currently in operation and the other menu items can be displayed distinguishably from each other. For example as shown in if a TV View function is currently in operation the menu item may further have a chevron marking differently from the other menu items to . The user can recognize through the marking that a television is in operation.

Also in the GUI screen menu items of the same function provided from the same type of devices can be sequentially displayed according to the user s selection under the condition that they are grouped into one group.

Alternatively in the GUI screen menu items of the same function provided from devices corresponding to the same type of signal sources namely devices are different in type but signal sources thereof are the same in type may be sequentially displayed according to the user s selection under the condition that they are grouped into one group.

That is when the same type or different types of devices providing the same function are connected to the signal sink menu items of the same function provided from the devices can be sequentially displayed in the GUI screen according to the user s selection.

For example assume that different types of signal sources providing the same type of devices DISC are a combi recorder and an HDD DVD recorder . Here the combi recorder is one signal source that provides two devices DVD DISC and VTR and the HDD DVD recorder is one signal source that provides only one device DVD DISC.

In this case if the user operates a left right key shown in using a mouse or remote controller a menu item is changed from Combi Recorder Disc Appreciation to HDD DVD Recorder Disc Appreciation in the same menu Disc Appreciation as shown in . That is the menu item in is changed to a menu item in .

In other words menu items of the same function provided from the same type of devices of different types of signal sources can be displayed in the GUI screen under the condition that they are grouped into one group thus providing convenience to the user.

From it can be seen that a chevron marking on a menu item of a function TV View currently in operation is kept displayed in a GUI screen even while a menu item corresponding to a function selected by the user and menu items corresponding to functions not selected by the user are displayed distinguishably from each other with background colors.

If different types of devices for example a DVD home theater and an HDD DVD recorder are connected to the signal sink menu items and of the same function for example DISC Appreciation provided from the devices can be changed from to as the user operates the left right key as stated previously.

Also if the same type of devices for example blu ray home theaters are connected to the signal sink menu items and of the same functions for example VCR Appreciation 1 and VCR Appreciation 2 provided from the devices can be changed from to as the user operates the left right key as stated previously.

If the user operates the left right key shown in using a mouse or remote controller a menu item is changed from Listen to TV to Listen to Home Theater in the same function Speaker Change as shown in . That is the menu item in is changed to a menu item in . Provided that a specific function for example HDD Recorder Appreciation is performed by only one of the devices connected to the signal sink a menu item of the HDD Recorder Appreciation function has no left right key as shown in .

The GUI screens as shown in and can be operated by the remote controller in various ways. For example the user may scroll menu items in the GUI screen left right up down by operating a left right up down direction key shown in or may select a desired menu item in the GUI screen by pushing a confirm button .

Also the remote controller may include a cancel key for turning on off popup of the GUI screen. In addition when the hotkey is pushed when there is no input from the user until a predetermined time for example 40 seconds elapses or when a different menu for example TV Guide is activated the GUI screen may vanish from the display device . In this manner various embodiments can be applied to operate the GUI screen through the remote controller.

The main processor determines whether a menu item displayed in a GUI screen has been selected by the user Step .

If a menu item is selected through the user command input unit the main processor generates a command for control of a device that provides a function corresponding to the selected menu item and transmits the generated command to the device through the auxiliary processor Step .

On the other hand the main processor determines through the auxiliary processor whether the device providing the function corresponding to the menu item selected in the GUI screen by the user is in its off or on state.

If it is determined that the device is in its off state the main processor generates a signal for turning on of the device and transmits the generated signal to the device through the auxiliary processor . After tuning on the device the main processor controls the device such that the device provides the function of the menu item selected by the user.

According to the present invention the signal sink may further include a storage unit not shown for storing media data and various information. The storage unit includes all types of storage devices or recording media that store data readable by various media systems and computer systems. For example the storage unit may include a ROM RAM CD ROM HDD magnetic tape floppy disk optical data storage device or Internet Web hard.

As apparent from the above description according to the present invention connection states of devices to a signal sink are displayed on a GUI screen in an integrated manner so that the user does not need to in advance recognize which device was connected to which port of the signal sink. Further the GUI screen is created and expressed by giving the first consideration to devices not signal sources. Therefore even though a signal source which is in the form of a composite unit having a plurality of devices is connected to the signal sink the user can recognize control a desired one of the devices on the GUI screen and conveniently and easily operate a desired function through the GUI screen. In addition it will be possible to display connection states etc. of signal sources of various forms to be introduced in future on the GUI screen.

