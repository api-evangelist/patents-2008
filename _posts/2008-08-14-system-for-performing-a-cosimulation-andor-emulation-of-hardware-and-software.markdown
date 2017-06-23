---

title: System for performing a co-simulation and/or emulation of hardware and software
abstract: The present invention relates to a system for performing a co-simulation and/or emulation of hardware and software. The system includes a hardware simulator with an integrated hardware model, a hardware and/or software environment for controlling the hardware simulator and performing a software simulation and/or a direct software application, at least one synchronization facility within the hardware model for indicating a request from the hardware and/or software environment, a receiver for setting the synchronization facility into a predetermined state, and a controller for switching the hardware simulator between a free-running state and a request-handling state.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08352231&OS=08352231&RS=08352231
owner: International Business Machines Corporation
number: 08352231
owner_city: Armonk
owner_country: US
publication_date: 20080814
---
This application claims the priority benefit under 35 U.S.C. 119 of prior European EP application 07115280.5 filed Aug. 30 2007 and incorporated herein by reference.

The present invention relates to a system for performing a co simulation and or emulation of hardware and software.

In a co simulation of hardware and software a hardware simulator or a hardware emulator is provided in order to simulate or emulate respectively a hardware model. Further a software simulator is provided to simulate a model of software or to perform directly said software.

In the verification environment a software simulation environment needs to communicate with a hardware simulator or emulator e.g. a VHDL very high speed integrated circuit hardware description language simulator or accelerator. An inter process communication between the two simulation environments is required.

The software simulator sends asynchronous requests to the VHDL simulator or accelerator. Said requests need to be serviced by the hardware verification environment. However the software simulator is several orders of magnitudes faster than the VHDL accelerator. Thus it is important that the hardware simulator or accelerator runs as fast as possible.

The current implementations of this service rely on a polling mechanism. Said polling mechanism stops the VHDL simulator or accelerator checks for the existence of new commands and restarts the VHDL simulator or accelerator at regular intervals again. The polling mechanism interrupts the simulation even when no requests for a test case are available. Further there is an intensive interaction between the software and the hardware simulator. The request for the test case cannot be serviced immediately since the new request is outstanding until the end of a current poll window.

In one known method the hardware software interaction between the hardware simulator or accelerator on the one hand and the runtime environment on the other hand is reduced by moving the major parts of a driver code into the model by supplying a VHDL provided for simulation only. Said VHDL allows driving the complete transaction sequences with minimum software overhead.

In another known method the hardware software interaction is minimized by making use of hardware breakpoints. Said hardware breakpoints can be set up to react with specific hardware triggers and signal their occurrence to the runtime environment.

An example of such a co simulation environment is known from the article Accelerating system integration by enhancing hardware firmware and co simulation by K. D. Schubert E. C. McCain H. Pape K. Rebmann P. M. West and R. Winkelmann . Vol. 48 No. 3 4 May July 2004 .

Another known example of a co verification for hardware and software is described in the article Accelerated hardware software co verification Cadence Design Systems Inc. 5692C Dec. 5 2005 .

It is an object of the present invention to provide an improved system for performing a co simulation and or emulation of hardware and software.

This and other objects are achieved by a method as laid out in the independent claims. Further advantageous embodiments of the present invention are described in the dependent claims and are taught in the description below.

The advantages of the invention are achieved by the introduction of one or more synchronization facilities and the installation of a hardware breakpoint in the hardware model. The synchronization facilities are inserted into the hardware model before the simulation or emulation respectively.

Therefore the preferred embodiment of the invention is a system for performing a co simulation and or emulation of hardware and software with a hardware simulator with an integrated hardware model a hardware and or software environment for controlling the hardware simulator and performing a software simulation and or a direct software application at least one synchronization facility within the hardware model for indicating a request from the hardware and or software environment a receiver for setting the synchronization facility into a predetermined state and a controller for switching the hardware simulator between a free running state and a request handling state.

The use of the hardware breakpoint allows setting the hardware accelerator in an operation mode with a permanent clock signal. During this time the controller gives up the control. Further the hardware breakpoint is set and triggered by an additional software thread.

At last the hardware simulator leaves the operation mode with the permanent clock signal and the control is returned to the controller again.

The inventive system includes two different channels. A software request channel forwards a software request which is the request from an inter process communication IPC software interface to a hardware model. A hardware request channel forwards a hardware request which is the request from the hardware model to the IPC software interface.

The software request channel comprises a receiver for receiving new requests from the IPC interface and a controller for controlling the hardware simulator or accelerator.

The software request channel includes a receiver and a software request controller . The receiver is connected to the software request controller . The receiver is provided to receive the requests from the IPC software interface.

The software request controller is connected to the hardware accelerator . The software request controller is connected to the hardware accelerator .

The hardware accelerator is a special kind of a hardware simulator. Generally an arbitrary hardware simulator can be used instead of the above hardware accelerator in a similar way. The hardware model comprises a synchronization facility . The receiver is connected to the synchronization facility .

After the startup the software request controller sets the hardware accelerator into a free running state. In this free running state the hardware accelerator is effectively blocking itself. Also the receiver blocks as long as there is not any new request. During this step all software entities are blocked. The hardware accelerator runs at full frequency without any software interaction in this step. In this operation mode the software entities cannot directly interrupt the hardware accelerator .

When a new request is detected by the receiver then the receiver resumes the operation and alters the synchronization facility in the hardware model . The synchronization facility acts as a synchronization point between the software and the hardware. The synchronization facility has been inserted into the hardware model for this purpose. Then the receiver returns into the blocking state. The change of the value in the synchronization facility is detected by the hardware accelerator and triggers a breakpoint. Said breakpoint forces the hardware accelerator to leave the free running mode. Further the hardware accelerator returns the control to the software request controller .

The software request controller decodes the request. Then the software request controller services the request by applying a sequence of clock signals and alter commands to the hardware accelerator . Once the request has been serviced then the software request controller again puts the hardware accelerator into the free running state and blocks. If any new request is received while the hardware accelerator is handling requests said new request is stored for a later handling without any interception.

The hardware request channel includes a hardware request controller and a transmission controller . The hardware request controller is connected to the transmission controller .

In the hardware request channel an additional breakpoint is installed. Said breakpoint is defined on an already existing notification facility within the hardware model . This notification facility indicates the availability of new requests from the hardware accelerator .

The hardware request controller sets the hardware accelerator into the free running state. The control is completely handed over to the hardware accelerator . If the hardware model receives a new request then the notification facility will be set and the breakpoint will be triggered. The hardware request controller will resume the operation in a similar way as for the software request channel . This time the hardware request controller reads the request from the hardware model .

Then the request is forwarded to the IPC software interface by the hardware request controller . The request is picked up almost instantly since the software simulator runs much faster the hardware simulation environment. Thus no performance is lost. At last the hardware request controller returns to the free running state again.

The hardware accelerator is set into the free running state as often as possible. Said free running state is merely left to hand the control over the software when a request from either the hardware model or the software simulator exists. The introduction of the special hardware trigger facility and the use of the breakpoints allow the maximum throughput of requests and the maximum accelerator performance.

The hardware simulator includes the hardware accelerator with the hardware model the synchronization facility and a software interface . The hardware simulator includes further the receiver and the software request controller . The receiver is connected to the synchronization facility . The receiver is provided to set the synchronization facility . The software request controller is connected to the software interface . The software request controller sends a permanent clock signal to the software interface during the handling of the request until the hardware model will send a response that the test case has been done.

The software simulator includes a test case command sequence . The software simulator is connected to the hardware simulator via a network socket . The commands are sent via the network socket .

The synchronization facility is inserted into the hardware model before the simulation or emulation respectively. The use of the hardware breakpoint allows setting the hardware accelerator in an operation mode with the permanent clock signal. During this time the software request controller gives up the control. The hardware breakpoint is set and triggered by the receiver . The hardware accelerator leaves the operation mode with the permanent clock signal and the control is returned to the software request controller again.

The hardware accelerator comprises the hardware model . The AIX workstation includes an IBM AIX operating system a host adapter driver an accelerator application a programming interface the receiver and the software request controller . Optionally the AIX workstation includes a simulation environment . In this embodiment the AIX workstation includes four PCI Peripheral Component Interconnect host adapters.

The TCP IP enabled workstation includes an operating system a software simulator application and software under test . Said software under test represents the test case. The software under test is connected to the receiver and to the software request controller . The software under test sends the requests to the receiver and is controlled by the software request controller .

The hardware accelerator is a special hardware which may be requested by the AIX workstation via the PCI host adapters. The AIX workstation loads the hardware model from a data base and prepares it. Then the AIX workstation transmits said hardware model to the hardware accelerator . Further the AIX workstation acts as a control station for the whole simulation process. The clocking requests and the access functions are transmitted from the AIX workstation to the hardware accelerator .

A control program runs on the AIX workstation and provides a software API Application Programming Interface . With said software API an external simulation code may control the hardware accelerator . The receiver and the software request controller are special examples for such an external simulation code.

In a simple implementation the software request controller may control the hardware accelerator as well as the communication with the software simulator application . In this case the software simulator application may run on a further workstation.

The synchronization facility may be realized by a piece of wire during building the model after the synthesizing the original logic circuit. Thus the whole process is transparent to the logic designer. In a later step of the simulation a breakpoint may be installed on the synchronization facility .

In the beginning of the simulation the software request controller installs the breakpoint on the synchronization facility . The breakpoint is activated as soon as the synchronization facility gets the logical value 1 . Since the hardware accelerator initializes the synchronization facility at the logical value 0 the synchronization facility gets the logical value 1 only then if the receiver externally sets this value via the API of the hardware accelerator .

In the first group the network socket is started in a first step. A second step blocks the reading. If the system receives any data then in a third step the interrupt facility is set. The data are queued in the fourth step of the first group.

In the second group the simulation is started in a first step. A second step simulates the clock signal and third step evaluates the model. In a fourth step it is checked if the interrupt facility is set. If the interrupt facility is set then the simulation is stopped in the fifth step. The data are handled in the sixth step of the second group.

The inventive method requires no polling anymore. The number of the interrupts during the simulation process is reduced to a minimum. The full control of the simulation process is given to the hardware accelerator by the permanent clock signal. This allows a maximum speed of the hardware accelerator .

The present invention can also be embedded in a computer program product which comprises all the features enabling the implementation of the methods described herein. Further when loaded in computer system said computer program product is able to carry out these methods. More particularly such computer program product is stored on a computer usable medium in particular a tangible medium such as a magnetic or optical disk and comprises computer readable program means for causing a computer to implement the system of the invention.

Although illustrative embodiments of the present invention have been described herein with reference to the accompanying drawings it is to be understood that the present invention is not limited to those precise embodiments and that various other changes and modifications may be performed therein by one skilled in the art without departing from the scope or spirit of the invention. All such changes and modifications are intended to be included within the scope of the invention as defined by the appended claims.

