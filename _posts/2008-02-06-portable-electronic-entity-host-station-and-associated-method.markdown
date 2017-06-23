---

title: Portable electronic entity, host station and associated method
abstract: A host station includes: a first electronic component having a “first” identifier, conforming to a predetermined convention, identifiers according to the convention including a “common” part, common to electronic components of the same family, and a “unique” part specific to each instance of an electronic component in the same family, at least one second electronic component having a “second” identifier conforming to the convention, and the common part of the second identifier being different from the common part of the first identifier, and verification of matching in accordance with a predetermined rule of the unique part of the first identifier with the unique part of the second identifier.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09047457&OS=09047457&RS=09047457
owner: OBERTHUR TECHNOLOGIES
number: 09047457
owner_city: Paris
owner_country: FR
publication_date: 20080206
---
The present invention concerns a portable electronic entity and a host station as well as an associated method.

The host station can be a portable or fixed personal computer a workstation connected to a server a mainframe computer a pocket computer or any other electronic device capable of executing operations.

The portable or removable electronic entity can be an electronic key. It can also be a microcircuit card or an RFID label.

The portable electronic entity includes one or more electronic components. Those electronic components can be for example a non volatile memory and a microcircuit card reader system where applicable comprising a microcircuit card that card being removable or installed permanently.

The portable electronic entity can also include an electronic circuit that can be an integrated circuit including a microprocessor for example. The electronic circuit can be a microcontroller including a microprocessor memories and communication peripherals and where applicable controlling the memory described hereinabove.

It is common practice for electronic components to have identifiers. These are often given by manufacturers to their components. They can be hexadecimal or binary strings or other types of information.

An identifier of this kind often includes a common portion that is identical for all the electronic components of the same design and a unique portion specific to one physical instance of the given component within the family of components of the same design.

Note that the family concept can vary as a function of the electronic component manufacturer for example for some manufacturers identical microcontrollers form part of the same family only if the content of their read only memory is identical although other manufacturers may deem this condition not to be indispensable. The same remark also applies to memory controllers if a read only memory is attached to each memory controller.

Moreover electronic components have functions. In numerous situations one function of a first electronic component is complementary from the point of view of the host station including human or hardware users of the host station to a function of a second electronic component.

The complementarity can for example reside in the fact that the unavailability for example the absence of the function of the second electronic component respectively the first component means that the function of the first electronic component or respectively the second electronic component is inoperative at least partially for example without effect.

For example the function of a first component can be to make available to the host station sensitive data contained in the first component and the function of a second component complementing the function of the first component from the point of view of the host station can be making available to the host station sensitive data contained in the second component and complementary from the point of view of the host station to the sensitive data contained in the first electronic component.

Another example relates to a first component including means for decrypting data stored in a second component. An application executed by the host station reads the data stored in the second component and sends it to the first component which decrypts it and sends it back to the host station.

The present invention addresses the problem that arises in a situation where at least two electronic components are in communication with a host station and the first electronic component includes a function that is complementary from the point of view of the host station to the function of a second of the electronic components.

In a situation of this kind it would be advantageous for the host station to be able to recognize automatically or autonomously which component is complementary to the other for example in order to execute an application using the complementary functions only if the two components are present.

For the moment there is no solution enabling the host station to connect automatically or autonomously the two components having complementary functions so that those functions can therefore be used.

Note that the problem arises in particular when the two electronic components are in the same portable electronic entity.

This problem is encountered in particular in contexts where it is desirable or even imperative for the host station to be able to check on behalf of its user that a component has not been illegitimately replaced by another within the same portable electronic entity.

To solve the above problem in various contexts in accordance with a first definition of the invention the present invention proposes a host station including 

characterized in that said host station further includes means for verification of matching in accordance with a predetermined rule of the unique part of said first identifier with the unique part of said second identifier.

This host station offers the advantage that verification of matching in accordance with a predetermined rule provides information indicating whether matching was achieved or not on which information the execution of an application or communication with a user or with a computer external to the host station can thereafter depend.

If the communication means and the identifiers conform to the USB standard serving as predetermined convention an identifier includes the following fields vendor identifier VID common to all electronic components manufactured by the same manufacturer or sold by the same vendor product identifier PID common to all electronic components of the same design serial number SN and Product Description String.

According to one particular convention the common portion of the identifier is the concatenation of the VID the PID and the Product Description String the unique portion of the identifier being the SN.

According to another particular convention the common portion of the identifier is the concatenation of the VID and the PID only and the unique portion of the identifier is the concatenation of the Product Description String and the SN.

According to a third particular convention the common portion of the identifier is the concatenation of the VID and PID while the unique portion is the SN the Product Description String not being operative at this level.

In this regard with certain operating systems two USB keys cannot function if their vendor identifiers product identifiers and serial numbers are identical.

Matching in accordance with said predetermined rule is preferably achieved if a predetermined arithmetic equality between a portion of said unique part of the first identifier and the portion of said unique part of said second identifier is achieved.

Said portion preferably comprises a serial number conforming to the USB standard. In this case the predetermined convention conforms to the USB standard.

According to an advantageous feature said verification means comprise a verification application adapted to determine said first identifier.

In one embodiment said identifier assigned to a logical volume corresponding to said first electronic component is obtained using the Windows API command GetVolumeNameForVolumeMountPoint and each identifier assigned to the logical volumes corresponding to the electronic components communicating with said host station via communication means conforming to a predetermined standard is obtained using at least the Windows API commands SetupDiEnumDeviceInfo and GetVolumeNameForVolumeMountPoint.

The host station is preferably characterized in that it further includes means for effecting a search of a plurality of electronic components each having an identifier conforming to said convention and the common part whereof is different from that of said first identifier for an electronic component the unique part of the identifier whereof is matched with the unique part of said first identifier.

This feature identifies or locates an electronic component for which a match is effected from a plurality of components in communication with the host station.

The host station is preferably characterized in that it further includes means for executing a dependent application and means for submitting execution of at least a portion of said application to said verification of said matching.

This enables the information relating to matching to be used in such a manner that it determines the progress of the execution of an application.

The host station is preferably characterized in that said dependent application is adapted to use a first function of said first component and a second function of said second component.

This enables the information relating to matching to be used in such a manner that the application uses the functions of the two components only if they are matched.

The host station can preferably be characterized in that said dependent application comprises an identity verification program the function of the first component comprising making available to said application a first set of biometric or personal data and the function of the second component comprising making available to said application a second set of biometric or personal data.

Alternatively said application comprises a network browser and the function of said first component comprises making said personal data application available and the function of said second component comprises making a cryptographic key available to said application.

Alternatively the connections of the portable entities to a host station can be effected by communication means conforming to the ISO 7816 standard or to the 14443 standard or to any other standard known to the person skilled in the art.

The operating system can be a version of Windows Vista Windows XP Windows NT or alternatively a version of Mac OS Unix Linux or a mainframe system.

According to a second definition of the invention it proposes a portable electronic entity comprising 

characterized in that the unique part of said first identifier and the unique part of said second identifier are matched in accordance with a predetermined rule.

The portable electronic entity preferably further includes means for effecting a verification of matching in accordance with a predetermined rule of the unique portion of said first identifier with the unique portion of said second identifier.

According to a third definition of the invention close to the second definition of the invention the latter proposes a portable electronic entity comprising 

characterized in that the portable electronic entity further includes means for effecting a verification of matching in accordance with a predetermined rule of the unique part of said first identifier with the unique part of said second identifier.

This portable electronic entity offers the advantage that the verification of matching in accordance with a predetermined rule provides information indicating whether matching on which the execution of an application or communication with a user or with a computer external to the host station or to the portable electronic entity can subsequently be made dependent.

The portable electronic entities according to the second and third general definitions of the invention can advantageously be characterized as follows 

Matching in accordance with said predetermined rule is preferably achieved when a predetermined arithmetic equality is achieved between a portion of said unique part of the first identifier and the same portion of said unique part of said second identifier.

Said portion preferably comprises a serial number conforming to the USB standard. In this case the predetermined convention conforms to the USB standard.

The first electronic component is preferably a combination comprising a memory controller and a non volatile memory attached to said memory controller.

Different types of non volatile memory exist and can be used singly or in combination. Examples are non rewritable memory ROM rewritable memory NVRAM for example of EEPROM or Flash RAM type .

In the context of the third general definition of the invention said second communication means preferably comprise a microcircuit card reader.

A reader of this kind can also be present in the portable electronic entity according to the second definition of the invention in particular if one of the components of that portable electronic entity is a microcircuit card. More generally means of communication with the electronic components can be present in the portable electronic entity according to the second definition.

Alternatively the second electronic component is mounted on the same printed circuit as the first component.

A microcircuit card is preferably inserted in said microcircuit card reader and said microcircuit card is preferably personalized with an identifier for example the second identifier.

In the context of the second and third definitions of the invention according to an advantageous feature said means for effecting a verification of matching comprise a verification application adapted to be executed by the host station.

Said verification application is preferably launched automatically after connection of the portable electronic entity to the host station.

According to one embodiment said first electronic component comprising a memory storing the instructions of said verification application said verification application is adapted to determine said first identifier.

Said verification application is preferably adapted to compare an identifier assigned to a logical volume corresponding to the peripheral storing said application with each identifier assigned to the logical volumes corresponding to the electronic components communicating with said host station via communication means conforming to a predetermined standard so as to determine said first identifier.

For example said identifier assigned to a logical volume corresponding to the peripheral storing said application is obtained using the Windows API command GetVolumeNameForVolumeMountPoint and each identifier assigned to the logical volumes corresponding to the electronic components communicating with said host station via communication means conforming to a predetermined standard is obtained using at least the Windows API commands SetupDiEnumDeviceInfo and GetVolumeNameForVolumeMountPoint.

The portable electronic entity preferably further includes means for effecting a search of a plurality of electronic components communicating with the host station each having an identifier conforming to said convention and the common part of the identifier whereof is different from that of said first identifier for an electronic component the unique part of the identifier whereof is matched with the unique part of said first identifier.

These means for executing a search can be an application adapted to be executed on a host station communicating with the portable electronic entity and can in particular be included in the verification application.

This feature identifies or locates an electronic component for which a match has been achieved from a plurality of components in communication with the host station.

It preferably further includes a memory storing instructions of a dependent application adapted to be at least partly loaded onto a host station and means for submitting the execution of at least a portion of said dependent application to said verification of said matching.

Said first electronic component preferably comprises said memory storing instructions of a dependent application.

For simplicity the dependent application and the verification application can be combined one portion of the application providing the search function and or verification function one portion being dependent on the result of the verification.

Said application is preferably adapted to use a first function of said first component and a second function of said second component.

In a preferred embodiment said application comprises a network browser and the function of said first component comprises making personal data available to said application and the function of said second component comprises making a cryptographic key available to said application.

For example said browser is adapted to the Internet network or said browser is adapted to a mobile telecommunications network.

Said navigator is preferably made secure by the use of the security functions of the microcircuit card. And said network browser preferably authorizes access only to predetermined Internet addresses.

According to a different embodiment said application comprises an identity verification program and the function of the first component comprises making a stored identity photograph available to said application and the function of the second component comprises making said identity text data available to said application.

The portable electronic entity is preferably characterized in that it further includes means for determining the identifier of said first electronic component or of the electronic component that comprises said memory storing instructions of an application.

This enables use of an application the code whereof does not include the identifier of the electronic component but which can determine it during its execution. This achieves economies in terms of production of the portable electronic entity because of the number of production steps which is therefore reduced.

Said means for effecting a determination of the identifier of said first electronic component preferably comprise means for using at least one function of an operating system of said host station.

The means for communication with the host station can alternatively also conform to the ISO 7816 standard or conform to the MMC MultiMedia Card or SD Secure Digital card format for example.

The portable electronic entity can also be a telephone a personal digital assistant PDA or an electronic document i.e. a paper document with a microcircuit including communication means for example contactless communication means within the thickness of one of its pages such as an electronic passport.

According to a fourth general definition of the invention the latter proposes a method of verification in a host station with which a first electronic component having a first identifier communicates said first identifier conforming to a predetermined convention identifiers according to said convention comprising a common part common to electronic components of the same family and a unique part specific to each instance of an electronic component in the same family characterized in that the method comprises a step of verification of matching in accordance with a predetermined rule of said unique part of said first identifier with the unique part of a second identifier of a second electronic component communicating with said host station said second identifier conforming to said convention and the common part of said second identifier being different from the common part of said first identifier.

Matching in accordance with said predetermined rule is preferably achieved when a predetermined arithmetic equality between a portion of said unique part of the first identifier and the same portion of said unique part of said second identifier is achieved.

Said portion preferably comprises a serial number conforming to the USB standard. In this case the predetermined convention conforms to the USB standard.

The method preferably further includes a step of searching a plurality of electronic components communicating with said host station and each having an identifier conforming to said predetermined convention and the common portion whereof is different from that of said first identifier for an electronic component the unique part of the identifier whereof is matched with the unique part of said first identifier.

The method preferably comprises a step of obtaining the identifier assigned to a logical volume corresponding to the peripheral storing said application using the Windows API command GetvolumeNameForVolumeMountPoint and a step of obtaining each identifier assigned to the logical volumes corresponding to the electronic components communicating with said host station via communication means conforming to a predetermined standard using at least the Windows API commands SetupDiEnumDeviceInfo and GetVolumeNameForVolumeMountPoint.

The method preferably includes a step of execution of an application and a step of submission of at least a portion of said execution to said verification of said matching.

The method preferably includes a step of determination or storage or obtaining of the identifier of said first electronic component preferably using at least one function of an operating system of the host station.

The method according to the invention preferably has features similar to those described hereinabove for the host station according to the invention or the portable electronic entity according to the invention those features being taken individually or in combination.

The method also comprises a step of reading or storage or obtaining an identifier of a microchip card included in said second electronic component said identifier being written into a file in a memory of the microchip card.

According to a fourth general definition of the invention the latter proposes a computer program comprising a series of instructions adapted when they are executed by a microprocessor to execute a method according to the invention.

Referring to a host station comprises a processor a memory a first USB connector and a second USB connector not shown . The host station is a personal computer running an off the shelf operating system in the home of a private person and is connected to the Internet network which enables it to communicate with the remote server of a bank.

A user connects a USB key i.e. a portable electronic entity having means of communication with a host station conforming to the USB standard to the connector . This key contains the personal banking data of the user and was supplied to them by their bank.

A second USB key not shown is connected to the second connector either by mistake or because a number of persons are using the host station simultaneously.

The USB key comprises a flash memory controller a flash memory attached to the controller a microcircuit card reader and a microcircuit card inserted into the reader .

The flash memory controller is a mass storage class device see for example USB Mass Storage Class Specification Overview revision 1.2 USB Implementers Forum Inc. . Its identifier is VID PID SN.

The flash memory has received personal data name forename bank account number personal identifier specific to the holder of the USB key . This data was stored either when the USB key was issued by the bank or subsequently.

The reader is an integrated circuit s cards interface device see for example Specification for Integrated Circuit s Cards Interface Devices rev. 1.1 USB Implementers Forum Inc. .

The microcircuit card is an integrated circuit s card device see for example Specification for USB Integrated Circuit s Card Devices Revision 1.0 USB Implementers Forum Inc. .

In the particular case shown this card is an ID 000 format SIM card conforming to the ISO 7816 standard. The card is personalized differently for each key. An identifier was given to it during an electrical personalization step in the course of which a file was created in the memory of the microcircuit card an identifier being written into the file.

It comes from the same vendor as the controller and its vendor identifier is therefore VID. Its product identifier is that of the microcircuit card family here denoted PID and different from PID. It has been personalized so that its serial number SN is the same as that of the controller . Its identifier is VID PID SN.

An application is stored in the flash memory . It is an Internet browser that can function on the host station . This browser was written for the issuing bank and authorizes access only to authorized Internet address URL in this instance corresponding to the servers of the issuing bank. For this purpose before displaying a page the browser verifies that the address is authorized i.e. that it corresponds to the server of the bank. Browser preferences can be stored in the flash memory when it is initialized or subsequently.

The code of the application includes the product identifier PID of the controller to which the read only memory is attached and the identifier PID which designates the family of microcircuit cards as already stated.

Finally the controller automatically launches the application on the host station by means of an autorun mechanism known to the person skilled in the art.

Consider now the case where the USB key not shown sourced from the same manufacturer as the USB key comprises a flash memory controller with identifier VID PID SN and a flash memory .

The flash memory controller has a product identifier different from the product identifier of the flash memory controller because the content of the read only memory of the controller differs from the content of the read only memory of the controller . The product identifier PID is therefore different from PID. It is also different from PID.

Moreover the flash memory received its identifier after the controller and has the same serial number SN. It is important that the serial number SN is different from the serial number SN.

The USB key also comprises a microcircuit card reader containing a microcircuit card sourced from the same manufacturer and that has been personalized so that its serial number is the same as that of the controller i.e. SN. Its identifier is therefore VID PID SN.

An application is stored in the flash memory . The application can be another browser limiting access to the server of a bank where appropriate identical to the bank issuing the USB key .

The application which is stored in the memory of the USB key as already stated is loaded automatically and is executed by the central unit . From this time onwards it communicates with the electronic components and via communication means conforming to the USB standard using encryption of communications in a manner known to the person skilled in the art and useful in the device described.

In a first step the application searches the connected electronic components for those for which the product identifier is equal to PID. It reads their serial numbers and stores them.

In a second step the application searches the connected electronic components for those for which the product identifier is equal to PID.

To do this the application creates a list of all the microcircuit card readers connected to the host station for example using the method that is part of the Windows SCardListReaders API.

Then for each reader from this list the application sends a series of APDU format commands requesting the identifier of the card contained in the reader. It receives in return an APDU format response containing that identifier. It compares it to PID and retains the microcircuit card reader if that identifier is indeed equal to PID.

In a third step the application selects from the components identified in the second step only those for which the serial number is equal to the serial numbers stored in the first step.

In a fourth step the application uses the data made available by the components identified in the third step to effect communication with the remote server via the network.

In the first step the application finds only the controller . It then reads the serial number of the controller i.e. SN and stores it.

In the third step the application selects from the components and all those for which the serial number is equal to SN and so finds only the card .

In the fourth step the application uses conjointly the data made available to it by the microcircuit card and the flash memory to set up a secure connection via the network with the remote server .

Exchanges between the browser and the server are encrypted using cryptographic means available in the microcircuit card .

The application uses the security functions available in the microcircuit card known to the person skilled in the art and useful in the device described. It uses in particular a cryptographic key or other cryptographic means specific to each microcircuit card or each cardholder.

The application makes communication with the server secure with the aid of an identifier and a secret element for example a cryptographic key that are different for each key or key holder. The secret element is stored in the card for example where appropriate with various cryptographic means.

The application uses the personal data name forename bank account number personal identifier contained in the flash memory to communicate with the server in a personalized fashion.

Verifying the identity of the serial numbers prevents the application accessing or using data present in the memory which must remain confidential because it does not belong to the holder of the key .

Symmetrically the application of the second card can use another identifier and another secret element stored in the card and does not access the data present in the memory .

The solution proposed here also avoids having to give the controller an identifier specific to each holder and therefore late on in the process of fabrication of the device. Only the card is personalized and this personalization is carried out at low cost. This achieves substantial savings.

The data is then stored when the USB key is used after personalization. It may consist of the preferences of the user of the key history data for the connection to the remote server or user account management data.

In an alternative embodiment the host station can be a portable computer a personal digital assistant or a mobile telephone communicating with the remote server via a mobile telecommunications network.

In a variant of the first embodiment described the product identifier PID of the controller is not included in the code of the application .

Once launched the application searches for the identifier of the electronic component from which it was launched. It uses functions of the operating system for this.

In a first step as soon as it is launched the application obtains the current path in the file system which is that from which it was launched.

In a second step the application determines the specific identifier called the globally unique identifier guid assigned by the operating system to the logical volume or peripheral corresponding to the path found in the first step.

In a third step the application creates the list of all the USB class physical peripherals connected to the station .

In the case described hereinabove it finds the memory controllers and and the microcircuit card readers and .

In a fourth step the application lists all the logical peripherals associated with each physical peripheral found in the third step. It then determines and stores for each logical peripheral found in this way the path in the corresponding file system.

In a fifth step the application determines and stores for each of the paths in the file system determined during the preceding step the specific identifier assigned by the operating system to the corresponding logical volume or peripheral .

In a sixth step the application compares the specific identifier obtained in the second step with the specific identifiers obtained in the fifth step and thus finds the only physical peripheral with which the specific identifier obtained in the second step is associated.

Finally the application stores the vendor identifier and the product identifier of the physical peripheral found in this way.

The above steps are carried out by means of commands of the Windows application programming interface API listed hereinafter 

In a second embodiment the invention detects falsification of an electronic passport including communication means conforming to the USB standard.

Referring to the customs or police computer includes a processor and a memory . An identity check application that can be executed on the computer is stored in the memory or on a medium such as a hard disk .

An electronic passport includes a hub to which are connected a microcircuit card reader containing a microcircuit card and a flash memory controller itself connected to a flash memory .

All these components come from the same manufacturer whose identifier is VID. Alternatively they can come from different manufacturers.

This manufacturer has given the product identifier PID to the flash memory controllers and the product identifier PID to the microcircuit cards.

The identifier of the flash memory controller is therefore VID PID SN SN being the serial number of the flash memory controller .

The microcircuit card was personalized after assigning the serial number to the flash memory controller and has the same serial number as the flash memory controller . Its identifier is VID PID SN.

The card contains identity information in text form for the bearer of the passport name forename date of birth .

The flash memory contains a photograph of the bearer of the passport in a portion of the memory that is write protected or not modifiable by the bearer.

A first falsification that can be envisaged is to move the flash memory from a first key to a second key whose microcircuit card contains different identity information in text form.

A second falsification that can be envisaged consists in moving the microcircuit card from a first key to a second key whose flash memory contains a different photograph.

On passing through customs or in the event of an identity check an operator connects the passport key to the computer .

As execution of this embodiment continues communication between the host station and the key is made secure by the use of the cryptographic means available in the microcircuit card to encrypt and sign the information transferred from one entity to the other in particular the identifiers.

In a first step the application searches the microcircuit cards for electronic components having the product identifier PID. It finds the card . It authenticates the microcircuit card with the aid of its cryptographic means.

The application then searches the flash memory controllers for electronic components having the product identifier PID. It finds the memory controller .

The application also authenticates the memory controller with the aid of the cryptographic means of the microcircuit card .

In a second step the application reads the serial number of the electronic components identified during the first step i.e. the memory controller and the microcircuit card .

If they are different then the key has been falsified and the application informs the operator of this usually the customs officer.

If they are identical the application then loads the photograph into the memory of the computer and displays the photograph on the screen of the computer .

The customs officer compares the photo with the appearance of the bearer and reads on the screen the text information on the identity of the bearer contained in the microcircuit card .

Verifying the connection between the serial numbers here their identity ensures that the information in the flash memory and the information in the microcircuit card are well matched i.e. functionally complementary to each other and that the identity verification that uses the two sources of information can be carried out correctly.

The present invention is not limited to the embodiment described hereinabove and represented in the drawing. It also concerns all variants evident to the person skilled in the art.

The person skilled in the art can adapt the embodiments described as a function of their general knowledge. In particular they can use other types of components member of a class of USB electronic components or not and other applications. The interface and the communication means can conform to the ISO 7816 standard the ISO 14443 standard or any other standard or specification.

The invention can also be implemented by comparing the concatenation of a product description string and a serial number of the identifiers conforming to the USB standard of the two electronic components.

The person skilled in the art can also adapt the invention by using it in a situation in which the identifier is in a rewritable memory area. They also know how to adapt it to a situation in which the vendor identifiers of the various electronic components are not equal.

