---

title: Intrusion resistant apparatus and method
abstract: An intrusion-resistant apparatus may include a magnetic memory array disposed with an enclosure. The magnetic memory may include a plurality of magnetic memory elements, each adapted to store a binary value only in the presence of a predetermined bias magnetic field having a magnetic field strength and direction within predetermined limits. Means for providing the predetermined bias magnetic field and an encryption/decryption engine may be disposed within the enclosure. An encryption/decryption key may be stored in the magnetic memory array. The encryption/decryption key may be used by the encryption/decryption engine to encrypt and decrypt data.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08167057&OS=08167057&RS=08167057
owner: Raytheon Company
number: 08167057
owner_city: Waltham
owner_country: US
publication_date: 20080610
---
This application is a division of application Ser. No. 11 446 534 entitled Intrusion Detection Apparatus and Method filed Jun. 2 2006.

This invention was made with government support. The government has certain rights in this invention.

This disclosure relates to an apparatus to detect hardware intrusion into a protected enclosure without requiring electrical power.

There are numerous applications where it is desirable to be able to detect intrusion into a protected enclosure. The intrusion could be unauthorized opening disassembly or other attempt to gain access to the protected enclosure. The protected enclosure could contain for example proprietary hardware security equipment or fee collection or metering equipment. To provide protection to portable equipment or equipment without applied power such as during storage or shipment the intrusion detection means must also operate without electrical power. Thus there is a need for a cost effective reliable digitally compatible non reversible sensor that can detect intrusion without the need for battery or other electrical power. This invention satisfies all of these requirements.

A first embodiment of the invention consists of an array of at least two magnetic memory elements each of which has two electronically readable stable states in the presence of a bias magnetic field and a means for providing the required bias magnetic field. The term bias magnetic field is intended to describe a magnetic field having a strength and direction within predetermined limits that will sustain the states of the magnetic memory elements. The predetermined limits on field strength may be centered about some finite value or may be centered about zero. In the latter case the magnetic memory elements are configured to maintain two stable states in the absence of an applied magnetic field and to change states if the applied magnetic field exceeds some threshold value.

The magnetic memory elements and the means for providing the bias magnetic field are both located within a protected electronics enclosure and disposed such that any attempt to disassemble the enclosure will cause a change in the bias magnetic field and resultant permanent change to the content stored in the magnetic memory.

Intrusion detection functionality is initialized by electronically writing a binary code into the magnetic memory after the protected volume is completely assembled. Subsequent disassembly will automatically cause the initialization code to erase. Attempted intrusion can be detected by comparing the memory content with the known value of the code at initialization. The reaction to the detected intrusion may be an alarm or alert or a reaction such as erasing data or software causing the protected equipment to lose functionality.

In a preferred embodiment the binary code stored in the magnetic memory at initialization is used as the key to encrypt or decrypt stored data or communications. In this case loss of the encryption code due to attempted intrusion is sufficient to cause the protected equipment to lose functionality.

In a preferred embodiment of the invention the magnetic memory is an array of spin valve magnetoresistive sensor elements. Spin valve sensors are described in U.S. Pat. No. 5 159 513 and have been extensively developed for use in read heads for magnetic disc memory devices

In the case where a finite bias magnetic field is required to maintain the memory states the means for providing the bias magnetic field will preferably be a small permanent magnet. The magnetic memory and the magnet must be mounted within the protected enclosure such that they physically move with respect to each other in any direction if the enclosure is non destructively disassembled

In the case where the magnetic memory is configured to maintain stable states in the absence of an applied magnetic field i.e. the bias field strength limits are centered on zero the protected enclosure is designed to shield the magnetic memory array from external or ambient magnetic fields. Disassembly causes the magnetic memory to be exposed to magnetic fields e.g. the earth s magnetic field resulting in changes to the memory content.

It must be understood that the device illustrated in is an example of a sensor suitable for use in the invention. The asymmetric layer structure of this example device is typical of spin valve devices configured for use with a non zero bias magnetic field. Alternative magnetic sensor constructions are known including an inverted device wherein the antiferromagnetic material is disposed between the lower magnetic film and the substrate. The use of additional magnetic or antiferromagnetic layers deposited over or along side of the spin valve device is a known technique to tailor the characteristics of the spin valve. The characteristics of such devices may be tailored to include stable memory function with zero bias magnetic field.

The effect of the antiferromagnetic layer is to pin the adjacent magnetic layer such that the magnetization of layer does not change in the presence of magnetic field up to very high levels thousands of Gauss but instead always points in one direction along the long axis of the spin valve device

The other magnetic layer called the free layer is not pinned and the direction of magnetization of layer can vary in the presence of a magnetic field. However layer will exhibit a natural tendency to become magnetized in either of two stable states with the direction of magnetization either parallel to and antiparallel to that of the pinned layer .

The relative magnetization of the two magnetic layers with respect to each other determines the resistance of the nonmagnetic layer . When the magnetization of the free layer points in the same direction as that of the pinned layer the electrical resistance of layer is reduced. Conversely when the magnetization of layers are pointing in opposite directions the electrical resistance of layer is increased. Thus in general two stable resistance states are possible.

The degree of resistance change between states depends on the type of magnetic sensor and design parameters such as layer thicknesses. Spin valve sensor devices typically exhibit a resistance change of approximately 5 measured along the long axis of the nonmagnetic film . Spin tunneling devices are reported to exhibit resistance changes greater than 40 measured across the thickness of the nonmagnetic film

The invention leverages the magnetic memory element s hysteretic behavior. The interrelationship between a magnetic memory element s magnetic field surroundings external magnetic field parameters at any given moment in time and its electrical resistance and the number of resistance values possible is illustrated in .

In essence the magnetic memory element s hysteresis notionally divides the magnetic field range into three zones two single state conditions and one bistable zone . The suitable zone represents the design level for the bias magnetic field plus margin for magnetic variations two stable binary resistance values are possible in this zone. The field strength in the bistable zone may be centered about zero or may be centered on a predetermined non zero value. The single state zones represent the external magnetic field direction and strength caused by intrusion events one and only one resistance value is possible in each of these zones.

In practice an intrusion detection sensor will contain a minimum of two magnetic memory elements. Upon hardware initialization predetermined resistance values can be written to individual spin valves to store a binary resistance security code or encryption key. In the case where the memory has only two elements and can only store two binary bits the possible useful security code values are 01 and 10 either the high or low resistance states can be arbitrarily defined as binary 0 . This code will persist if and only if the applied magnetic field for all spin valves is maintained in the bistable zone. If at any time the applied magnetic field changes into either of the single state zones the security code is erased either all 0s or all 1s depending on which of the two intrusion zones was applied last . The change in the stored security code will occur whether or not power is applied.

In a magnetic shield attached to cover is disposed between the magnetic memory array and magnet . Removing cover displaces the shield changing the magnetic field at memory array and thus changing the security code stored therein.

In the magnetic memory array is adapted to stably store a security code in the absence of a magnetic field and cover and box are constructed of a magnetic shielding material. Removing cover exposes the magnetic memory array to environmental magnetic fields depicted by arrow thus changing the security code stored in the magnetic memory array.

In electronic equipment bearing magnetic memory array is disposed within box and can only be removed by motion in the direction indicated by the arrow . Electronic equipment could be a circuit card or module conventionally mounted in card guides. Removing electronic equipment in direction causes the magnetic memory array to pass in proximity to magnetic thus changing the content stored in memory array .

It should be understood that B C and D illustrate simplistic embodiments of the invention and that many variations are possible within the scope of the invention. The magnetic memory array and the means for providing a magnetic field may be disposed anywhere within the enclosure so long as attempted intrusion results in relative motion between these elements. This relative motion could be caused by removing a cover opening a drawer or door or sliding a circuit module from a rack. Additionally multiple memory arrays magnets or shields could be disposed such that intrusion is detected by relative motion of at least one memory array with respect to at least one magnet or one shield.

While read circuitry will most likely be located in the immediate proximity of magnetic memory array the other elements shown in do not need to be located within the protected enclosure. For example the write circuitry could be external to the enclosure and connected to the magnetic memory array only temporarily to write the security code after the enclosure is assembled. Any or all of the means for establishing the security code the means for verifying the code and the means for reacting to an intrusion event could be located within the protected enclosure or could be external to the protected enclosure and connected by a secure data link.

Throughout this description the embodiments and examples shown should be considered as exemplars rather than limitations on the apparatus and procedures disclosed or claimed. Although many of the examples presented herein involve specific combinations of method acts or system elements it should be understood that those acts and those elements may be combined in other ways to accomplish the same objectives. With regard to flowcharts additional and fewer steps may be taken and the steps as shown may be combined or further refined to achieve the methods described herein. Acts elements and features discussed only in connection with one embodiment are not intended to be excluded from a similar role in other embodiments.

For means plus function limitations recited in the claims the means are not intended to be limited to the means disclosed herein for performing the recited function but are intended to cover in scope any means known now or later developed for performing the recited function.

As used herein whether in the written description or the claims the terms comprising including carrying having containing involving and the like are to be understood to be open ended i.e. to mean including but not limited to. Only the transitional phrases consisting of and consisting essentially of respectively are closed or semi closed transitional phrases with respect to claims.

Use of ordinal terms such as first second third etc. in the claims to modify a claim element does not by itself connote any priority precedence or order of one claim element over another or the temporal order in which acts of a method are performed but are used merely as labels to distinguish one claim element having a certain name from another element having a same name but for use of the ordinal term to distinguish the claim elements.

As used herein and or means that the listed items are alternatives but the alternatives also include any combination of the listed items.

