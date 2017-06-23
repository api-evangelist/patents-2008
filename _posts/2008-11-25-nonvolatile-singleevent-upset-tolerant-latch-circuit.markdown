---

title: Non-volatile single-event upset tolerant latch circuit
abstract: A non-volatile single-event upset (SEU) tolerant latch is disclosed. The non-volatile SEU tolerant latch includes a first and second inverters connected to each other in a cross-coupled manner. The gates of transistors within the first inverter are connected to the drains of transistors within the second inverter via a first feedback resistor. Similarly, the gates of transistors within the second inverter are connected to the drains of transistors within the first inverter via a second feedback resistor. The non-volatile SEU tolerant latch also includes a pair of chalcogenide memory elements connected to the inverters for storing information.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07965541&OS=07965541&RS=07965541
owner: Ovonyx, Inc.
number: 07965541
owner_city: Rochester Hills
owner_country: US
publication_date: 20081125
---
The present application claims benefit of priority under 35 U.S.C. 365 to the previously filed international patent application number PCT US2008 084714 filed on Nov. 25 2008 assigned to the assignee of the present application and having a priority date of Nov. 30 2007 based upon U.S. provisional patent application No. 60 991 390. The contents of both applications are incorporated herein by reference.

The present invention was made with United States Government assistance under Contract No. FA9453 04 C 0052. The United States Government has certain rights in the present invention.

The present invention relates to memory devices in general and in particular to chalcogenide memory devices. Still more particularly the present invention relates to a non volatile single event upset tolerant latch circuit.

In certain environments such as satellite orbital space in which the level of radiation is relatively intense memory devices such as static random access memories SRAMs are more susceptible to single event upsets SEUs or soft errors than they would have in terrestrial environments. These SEUs are typically caused by electron hole pairs created by and travelling along the path of a single energetic particle as it passes through the memory cells of the SRAMs. Should the energetic particle generate a critical charge within a storage node of an SRAM cell the logic state of the SRAM cell will be upset. By the same token other circuits used in conjunction with SRAMs are also susceptible to SEUs.

In the existing re programmable SRAM based field programmable gate arrays FPGAs a device configuration is typically stored in the volatile SRAM cells and must be reloaded at each power up. Non volatile FPGAs having flash memories can be utilized to store device configurations but the flash memory cells are not radiation tolerant either and there are reliability limitations for flash memory cells.

In accordance with a preferred embodiment of the present invention a non volatile single event upset SEU tolerant latch is utilized to store device configurations. The non volatile SEU tolerant latch includes a first and second inverters connected to each other in a cross coupled manner. The gates of transistors within the first inverter are connected to the drains of transistors within the second inverter via a first feedback resistor. Similarly the gates of transistors within the second inverter are connected to the drains of transistors within the first inverter via a second feedback resistor. The non volatile SEU tolerant latch also includes a pair of chalcogenide memory elements connected to the inverters for storing information.

All features and advantages of the present invention will become apparent in the following detailed written description.

Referring now to the drawings and in particular to there is illustrated a block diagram of a field programmable gate array FPGA system in accordance with a preferred embodiment of the present invention. As shown a FPGA system includes a FPGA unit coupled to non volatile single event upset SEU tolerant latches . FPGA unit includes a FPGA array. Non volatile SEU tolerant latches includes a bank of SEU tolerant latches capable of functioning as a configuration management unit for storing data from a static random access memory unit not shown and for retaining the data after system shut down. For example device configurations from FPGA unit can be stored in non volatile SEU tolerant latches before system shut down and can be reloaded from non volatile SEU tolerant latches back to FPGA unit at each power up.

With reference now to there is depicted a circuit diagram of one of non volatile SEU tolerant latches in accordance with a preferred embodiment of the present invention. As shown a non volatile SEU tolerant latch includes two cross coupled complementary metal oxide semiconductor CMOS inverters. The first inverter includes a p channel transistor connected in series with an n channel transistor . The second inverter includes a p channel transistor connected in series with an n channel transistor . The gates of transistors and are connected to the drains of transistors and via a feedback resistor and the gates of transistors and are connected to the drains of transistors and via a feedback resistor . The resistances of feedback resistors and are greater than zero ohm. The higher the resistance values the more tolerant non volatile SEU tolerant latch towards SEU.

The first inverter is connected to ground via a chalcogenide memory element . Similarly the second inverter is connected to ground via a chalcogenide memory element . Chalcogenide which preferably includes germanium antimony and tellurium can be made to have phase transformation properties at a relatively low voltage. Thus each of chalcogenide memory elements and can be placed in an amorphous state or a crystalline state which is utilized to represent a logical 0 and a logical 1 respectively. The state of each of chalcogenide memory elements and can be changed from one to another via the application of a current field accordingly. For the present application the logical states of chalcogenide memory elements and are always complementary to each other.

The device configuration information can be loaded from FPGA units and into chalcogenide memory elements and respectively for the purpose of storage. During system start up the stored device configuration information is automatically reloaded from chalcogenide memory elements and back to FPGA units and respectively.

State set up modules and determine the initial state of non volatile SEU tolerant latch . For example the initial state of non volatile SEU tolerant latch can be reset by utilizing state set up modules and before the device configuration information is loaded from FPGA units and

Referring now to there is depicted a circuit diagram of a non volatile SEU latch in accordance with an alternative embodiment of the present invention. As shown chalcogenide memory element along with state set up module are connected between Vand p channel transistor . Similarly chalcogenide memory element along with state set up module are connected between Vand p channel transistor . The functionalities of non volatile SEU latch circuit are identical to those of non volatile SEU latch in .

As has been described the present invention provides a non volatile SEU tolerant latch for storing device configurations. Since the cross coupled CMOS inverters are SEU tolerant and chalcogenide memory elements are immune to SEU the entire FPGA system is SEU tolerant.

While the invention has been particularly shown and described with reference to a preferred embodiment it will be understood by those skilled in the art that various changes in form and detail may be made therein without departing from the spirit and scope of the invention.

