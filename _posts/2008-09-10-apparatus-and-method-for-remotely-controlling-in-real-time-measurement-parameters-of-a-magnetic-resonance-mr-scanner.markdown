---

title: Apparatus and method for remotely controlling in real time measurement parameters of a magnetic resonance (MR) scanner
abstract: Apparatus for remotely controlling parameters of an image scanning apparatus includes a software interface for translating commands from an external application for providing scanner control commands to a scanner control machine for control of the parameters; and the software interface includes syntax software for translating the commands from the external application into a given syntax for providing the scanner control commands.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08094909&OS=08094909&RS=08094909
owner: Siemens Aktiengesellschaft
number: 08094909
owner_city: München
owner_country: DE
publication_date: 20080910
---
Specific reference is hereby made to copending U.S. Provisional Patent Application No. 60 978 425 filed Oct. 9 2007 in the names of inventors CORINNA MAIER KLAUS J. KIRCHBERG PETER SPEIER and CHRISTINE LORENZ and entitled An apparatus to remotely real time control measurement parameters of an MR scanner and whereof the disclosure is hereby incorporated herein by reference and whereof the benefit of priority is claimed.

The present invention relates generally to the field of imaging apparatus and more particularly to magnetic resonance imaging MRI apparatus and control apparatus for such imaging apparatus.

Magnetic Resonance Imaging MRI is a known technique for obtaining 2 dimensional 2D and 3 dimensional 3D images of a patient based upon nuclear magnetic resonance NMR principles. MRI is widely used in medicine for the examination and diagnosis of internal medical conditions in a patient. Detailed descriptions of MRI systems are widely available in the literature. Briefly an MRI system generally includes an electromagnet for producing an intense magnetic field for covering at least a portion of a patient s anatomy. Typically an MRI system also includes a radio frequency field generator a receiving system coupled to a coil surrounding a portion of the patient s anatomy under study and a magnetic gradient system to localize in space a particular portion of the patient s anatomy under study. Generally an MRI system or scanner also includes a computer based image processing system for receiving signals from the coil and for processing the signals into interpretable data such as visual images for viewing by a physician or other radiology analyst. Generally the system includes MR scanner control apparatus for controlling operation and operating and measurement parameters of the system.

Various arrangements including control arrangements are known in the MRI art. For example U.S. Pat. No. 6 157 194 entitled CONTROL OF MRI SYSTEM and assigned to Fonar Corporation discloses an arrangement wherein a generic MR Host for controlling multiple types of MPCUs such as a WordProgram the Host can communicate with multiple types of printers. Thus the scanner control in this patent controls a plurality of devices.

In another example U.S. Pat. No. 6 198 285 entitled IN ROOM MRI DISPLAY TERMINAL AND REMOTE CONTROL SYSTEM and assigned to Hitachi Medical Corporation discloses an arrangement for controlling a piece of equipment in an MR room by way of an infrared receiver. In this arrangement the control path is contained within a room.

It is herein recognized that the foregoing documents do not contemplated controlling a scanner by multiple types of input applications. Furthermore at least in the aforementioned U.S. Pat. No. 6 198 285 operation is restricted to within a room. No means are disclosed for controlling scanner parameters remotely.

A prior development was to allow the prototype application Interactive Front End to control a real time measurement on the scanner remotely. See the publication by C. H. Lorenz K. J. Kirchberg S. Zuehlsdorff P. Speier M. Caylus W. Borys T. Moeller and M. A. Guttman entitled Interactive Frontend IFE A platform for Graphical MR Scanner Control and Scan Automation Proc. Intl. Soc. Mag. Reson. Med. 13 2005 2170 whereof the disclosure is hereby incorporated herein by reference. Authors Kirchberg Speier and Lorenz are also named inventors in the present application for patent.

The MriProtAccess d .dll uses the OLE Automation which was used by the Syngo architecture and is disclosed in German patent document No. DE 1962584 to which reference is made for further information. OLE stands for Object Linking and Embedding this is a Microsoft Corporation software technology that generally allows Windows programs to exchange information and work together. The definition of OLE already includes remote control and this existed in the initial NUMARIS 4 software. NUMARIS is a software package application applicable to MR from Siemens AG also under the name SYNGO MR.

In accordance with an aspect of the present invention a scanner is controllable by a plurality of types of input applications.

In accordance with an aspect of the present invention a scanner is controllable by a plurality of types of inputs applications which may be situated in locations outside the scanner room.

In accordance with an aspect of the invention apparatus in accordance with the present invention is adapted to remotely control available measurement parameters of an MR scanner.

In accordance with an aspect of the invention apparatus in accordance with the present invention remotely controls measurement parameters of an MR scanner.

In accordance with an aspect of the invention apparatus in accordance with the present invention remotely controls at least a portion of the available measurement parameters of an MR scanner.

In accordance with an aspect of the invention apparatus in accordance with the present invention remotely controls available measurement parameters of an MR scanner by means of an external application.

In accordance with an aspect of the invention the external application runs on the MR scanner control apparatus.

In accordance with an aspect of the invention the external application runs on an external personal computer PC coupled with the MR scanner control apparatus by the hub of an internal scanner network.

In accordance with an aspect of the invention apparatus in accordance with the present invention is embodied in a single software application.

In accordance with an aspect of the invention apparatus in accordance with the present invention is adapted for receiving commands from an external application regarding the retrieval the setting or manipulation of scan parameters.

In accordance with an aspect of the invention apparatus in accordance with the present invention utilizes a software interface which is part of the MR scanner control software to translate received commands into a certain syntax in accordance with another aspect of the present invention and into scanner control commands.

In accordance with an aspect of the invention after a transaction apparatus in accordance with the present invention sends feedback to a requesting application of the transaction.

In accordance with an aspect of the invention apparatus in accordance with the present invention provides an interface for an application to modify a protocol on the MR scanner in a generic manner.

In accordance with an aspect of the invention a method in accordance with the present invention provides for remotely controlling scan parameters without knowledge of the OLE APIs of the Scanner Software and by an application on an external machine. API stands for Application Programming Interface generally software that an application program uses to request and carry out lower level services performed by for example a computer s operating system.

In accordance with an aspect of the present invention the invention is adapted to be used by an application which requires updated measurement control parameters. The apparatus and method of the invention include the use of the apparatus and or the method by an external application.

An object of the present invention is to provide for manipulation of any or all available parameters of an open protocol without restriction to particular parameters.

Still another object of the present invention is that the method and apparatus in accordance with present invention are generally not restricted to particular parameters but can manipulate available parameters of an open protocol.

In accordance with an aspect of the present invention apparatus in accordance with the present invention is made available to be used by an external application.

In accordance with an aspect of the present invention apparatus for remotely controlling parameters of an image scanning apparatus includes a software interface for translating commands from an external application for providing scanner control commands to a scanner control machine for control of the parameters and the software interface includes syntax software for translating the commands from the external application into a given syntax for providing the scanner control commands.

In accordance with an aspect of the invention the external application runs on at least one of a the scanner control machine and b an external machine the external machine being coupled to the scanner control machine.

In accordance with an aspect of the invention the scanner control machine comprises a hub of an internal scanner network and the external machine is coupled to the scanner control machine by at least one of a the syntax software and b the hub.

In accordance with an aspect of the invention apparatus for remotely controlling parameters of an image scanning apparatus in real time comprises a scanner control machine for control of the parameters wherein the scanner control machine includes scanner control software for providing the control of the parameters and an external application for providing commands the external application running on at least one of a the scanner control machine and b an external machine coupled to the scanner control machine.

In accordance with an aspect of the invention apparatus for controlling parameters of an image scanning apparatus including a scanner control machine comprises memory means for storing a program and other data and processor means in communication with the memory means and being operative with the program to perform processing commands from an external application by a software interface the software interface comprising syntax software for translating the commands into a syntax for providing scanner control commands and supplying the scanner control commands to scanner control software in the scanner control machine for controlling the parameters.

In accordance with an aspect of the invention a method for remotely controlling parameters of an image scanning apparatus comprises processing in a software interface including a user interface commands from an external application and wherein the processing comprises a step of translating the commands into a given syntax for providing scanner control commands to a scanner control machine for control of the parameters.

In accordance with an aspect of the invention a method for controlling parameters of an image scanning apparatus comprises running a software application for remotely controlling the parameters including scanner control commands on at least one of a scanning control apparatus associated with the image scanning apparatus and b a computer external to the image scanning apparatus coupled to the scanning control apparatus applying the external control commands to the software application for providing commands to the image scanning apparatus for controlling the parameters including at least one of retrieving scan parameters and manipulating scan parameters and running a software interface on the scanning control apparatus for translating the external control commands into a command syntax and thence into the scanner control commands.

In accordance with an aspect of the invention the step of running the software application comprises at least one of a running the software application independently of any Application Programming Interface API of software running on the scanning control apparatus b running the software application independently of an application running on a machine associated with the controlling parameters c running the software without constraint of particular parameters for the external control commands and such that parameters of an open protocol can be manipulated and d running the software without constraint of particular parameters for the external control commands and such that parameters of an open protocol can be manipulated.

In accordance with an aspect of the invention a computer program product comprises a computer useable medium having computer program logic recorded thereon for program code for controlling parameters of an image scanning apparatus comprising the steps of translating commands from an external application for providing scanner control commands to a scanner control machine for control of the parameters and utilizing syntax software for translating the commands from the external application into a given syntax for providing the scanner control commands.

The present invention is for an apparatus and system and a method for remotely controlling preferably in real time measurement parameters of a scanning apparatus such as an MR scanner. Briefly the present invention is for a method and system enabling remote control of all or a subset of available measurement parameters of an MR scanner by means of an external application running either on the MR scanner control machine or an external PC coupled to the MR scanner control machine typically by way of the hub of an internal scanner network.

The apparatus is realized in preferably a single software application and can receive commands from an external application or from external applications regarding the retrieval or manipulation of scan parameters an external application herein is external to and independent of the MR software that is the software controlling the image scanning apparatus.

The apparatus uses a software interface which is generally part of the MR scanner control software to translate the received commands into a certain syntax which forms a part of the present invention into scanner control commands in accordance with an embodiment of the invention. After a transaction the apparatus sends feedback to the requesting application. Thus the apparatus or system of the present invention provides an interface for an application to modify a protocol on the MR scanner in a generic way.

In the description which follows the invention is described most conveniently and clearly without loss of generality by exemplary embodiments including the use of software code and or pseudocode which is familiar and understood in the art to which it pertains to describe and illustrate steps and functions of the invention.

Reference is made to which shows data flow in a block schematic diagram of apparatus in accordance with the present invention. The host system HOST is shown enclosed within a dotted line and is associated with the machine controlling the image scanning apparatus not shown . An examination task card in the host system is associated with the MR Control Software controlling the image scanning apparatus to which it communicates parameters of the image scanning apparatus including scanner control commands in the parameters. Examination task card also communicates with a user .

Block represents an external application running on the host system and communicating by way of a Remote Protocol Modifier . An external application runs on an external machine in the same network as the host and communicates with the host system by way of Remote Protocol Modifier which provides for data interchange over TCP IP and which interchanges data with examination task card by way of a link ProtAccess providing access protocols for the data interchange. The implementation of ProtAccess link in the described present embodiment comprises a User Interface as shown for example in as will be further explained in reference to .

It is noted that application application Remote Protocol Modifier and ProtAccess link are identified as being particularly pertinent to illustrating modes of operation of the described embodiment of the present invention.

Briefly the method of operation of an embodiment of the invention is as follows. In the embodiment of the present invention a method is provided for controlling parameters of an image scanning apparatus. The steps of the method comprise 

Protocol A set of parameters controlling the MR measurement which is available on the MR scanner User Interface

In further reference to characteristics of the User Interface display include as shown by the respective section or panel labels on the display and as numbered in 

Minutes idle Time after which ReModProt will auto Terminate and a with message box If the box is checked the user will get a message box to confirm or cancel pending termination.

The communication from the external application to the apparatus is realized with TCP IP sockets. It is possible to change the port number during execution.

We distinguish between a a set scenario and b a get scenario . a will set a value for a certain parameter into the open online protocol b will retrieve the current value all possible values and the parameter label from the open online protocol.

The name tag sg.0.ext orientation is an exception. Using this name tag the orientation is in a more reasonable format for the external application. It substitutes the name tags sg.0.pe dir sg.0.ori descr sg.0.ori alpha sg.0.ori beta sg.0.rot

The four float values represent an axis of rotation followed by the angle of right handed rotation about that axis in radians.

The reference for the rotation is a transversal plane in the patient LPH coordinate system left posterior head .

Feedback exists for each protocol parameter manipulation. This data is displayed in the Scan Command Feedback Stream see . In the get scenario this data is additionally sent over the socket to the external application using the following syntax 

To set a value for an optional parameter the option number must be set and not the option string e.g. sg.1.ori descr 8 and NOT ori descr T C 

As will be apparent the present invention for an apparatus and method for remotely controlling in real time measurement parameters of for example a magnetic resonance MR scanner is best intended to be implemented with the use and application of imaging equipment in conjunction with a programmed digital computer. shows in general terms and in basic schematic form a digital processor coupled for two way data communication with an input device an output device and a memory device for storing a program and other data. The input device is so designated in broad terms as a device for exchanging data for example relating to an image or images or commands for processing in accordance with the present invention. For example an input may be from an imaging device such as a device incorporated in a CATSCAN X ray machine an MRI or other device or a stored image or by communication with another computer or device by way of direct connection a modulated infrared beam radio land line facsimile or satellite as for example by way of the World Wide Web or Internet or any other appropriate source of such data. The output device may be for data commands and or it may include a computer type display device using any suitable apparatus such as a cathode ray kinescope tube a plasma display liquid crystal display and so forth and serve as a user interface as utilized in the described exemplary embodiment or it may or may not include a device for rendering an image and may include a memory device or part of the memory device of for storing an image or measurement parameters or commands for further processing or for viewing or evaluation as may be convenient or it may utilize a connection or coupling including such as are noted above in relation to the input device. The processor is operative with a program set up in accordance with the present invention for implementing steps of the invention. Such a programmed computer may interface readily through communications media such as land line radio the Internet and so forth for image data acquisition and transmission.

The invention may be readily implemented at least in part in a software memory device and packaged in that form as a software product. This can be in the form of a computer program product comprising a computer useable medium having computer program logic recorded thereon for program code for performing the method of the present invention.

The present invention has also been explained in part by way of examples using illustrative exemplary embodiments. It will be understood that the description by way of exemplary embodiments is not intended to be limiting and that while the present invention is broadly applicable it is helpful to also illustrate its principles without loss of generality by way of exemplary embodiments relating to an important field of application for the present invention namely to computer vision and imaging. For example the described embodiments typically illustrate operation in real time this being generally the preferred mode of operation.

It will also be understood that various changes and substitutions not necessarily herein explicitly described may be made without departing from the spirit and scope of the invention which is defined by the claims following.

