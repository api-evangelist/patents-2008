---

title: Apparatus and method for automatically extracting interface of embedded software
abstract: Provided is an apparatus and method for automatically extracting an interface of embedded software. The method defines an interface of embedded software as a test item for test of the interface of the embedded software, and generates an interface symbol corresponding to the defined test item. The location of the interface symbol is determined, and a test case is generated based on the interface symbol and its location in the software. Embodiments of the invention thus facilitate the testing of software at interfaces between layers in the software.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08255874&OS=08255874&RS=08255874
owner: Samsung Electronics Co., Ltd.
number: 08255874
owner_city: Suwon-si, Gyeonggi-do
owner_country: KR
publication_date: 20080123
---
This U.S. non provisional patent application claims priority under 35 U.S.C. 119 of Korean Patent Application No. 10 2007 0040127 filed on Apr. 25 2007 the entire contents of which are hereby incorporated by reference.

The present invention disclosed herein relates to embedded software test and more particularly but not by way of limitation to a method for automatically generating a test case.

Typical embedded software is tested by monitoring and debugging an emulator. The monitoring may be synchronous or asynchronous. In synchronous monitoring a source code debugger such as the remote Kernal GNU DeBugger KGDB is used to stop a program at a certain location in a source code and monitor a value of the corresponding location. In asynchronous monitoring an independent monitoring daemon is used to monitor the entire embedded software which may lead to inaccurate measurement of a source code that is to be monitored.

In both the synchronous monitoring scheme and the asynchronous monitoring technique a code area a data area global variables and a stack area may be monitored. Many such tests are performed on an ad hoc basis rather than on an objective basis because determination of monitoring target symbols and analysis of the results may vary depending on the developers experience knowledge levels. Furthermore simple monitoring techniques focus on test automation rather than identification of a test target i.e. an input of a test case generation of the test case and analysis of the test results.

Embedded software is typically linked with hardware a hardware abstraction layer HAL an OS kernel device drivers and upper level application software. In an embedded system the interfaces between such layers must be tested. This is however difficult to achieve using conventional test technology.

An embodiment of the invention provides an apparatus and method for automatically extracting interface symbols to test an interface of embedded software.

An embodiment of the invention also provides an apparatus and method for automatically generating a test case to test an interface of embedded software.

An embodiment of the invention provides a method for testing software. The method includes identifying an interface test feature associated with the software the interface test feature being associated with an interface symbol the interface symbol enabling measurement of the interface test feature and extracting a location in the software associated with the interface symbol.

An embodiment of the invention provides an apparatus for testing software. The apparatus includes a test target analyzer configured to receive the software identify at least one interface between a plurality of layers in the software and identify a location in the software for the at least one interface and a test case generator coupled to the test target analyzer the test case generator configured to generate a test case for the software based on the identified at least one interface and the location.

Embodiments of the invention thus facilitate the testing of software at interfaces between layers in the software.

Preferred embodiments of the present invention will be described below in more detail with reference to the accompanying drawings. The present invention may however be embodied in different forms and should not be constructed as limited to the embodiments set forth herein. Rather these embodiments are provided so that this disclosure will be thorough and complete and will fully convey the scope of the present invention to those skilled in the art.

An embodiment of the invention provides an apparatus and method for automatically generating a test case for a LINUX based LCD device driver. In this instance an evaluation board can be emulated prior to actual product development. An embodiment of the invention exemplifies an LCD device driver as embedded software.

Referring to a test system for embedded software includes a host system an emulator an evaluation board and a LINUX server . The LINUX server includes embedded software .

The host system generates a test case for testing an interface of the embedded software . In addition the host system controls the emulator to execute the generated test case. The emulator executes the test case generated by the host system and outputs the results. The evaluation board is provided to test the embedded software together with hardware. The LINUX server loads the embedded software into the evaluation board under the control of the emulator .

The host system includes a test target analyzer a test case generator a test executing engine and a result analyzer . The test target analyzer receives a source or object code of the embedded software from the LINUX server . From an executable linker format ELF the test target analyzer automatically identifies a location in the source or object code where an interface symbol corresponding to each interface is mapped. The test case generator generates a test case for testing the interface of the embedded software . The test case is generated in a script format so that it can be executed in the emulator . The test execution engine receives the test case from the test case generator provides the received test case to the emulator and controls the emulator . The result analyzer receives the execution results of the test case from the emulator and analyzes the received execution results.

Variations to the embodiment illustrated in are possible. For example a server other than a LINUX server may be used and code formats other than those specified above may also be used according to design choice. Likewise the emulator must not necessarily be a TRACE32 emulator as indicated in and as described below.

The present invention tests the structure of embedded software i.e. an LCD device driver loaded into an embedded system for example a mobile application AP and tests an interface in an LCD emulation test.

Referring to the embedded system includes a physical hardware layer a hardware abstraction layer HAL an operation system OS layer and an application layer . The OS layer includes embedded software and kernel software .

The embedded system may include a variety of device drivers for supporting physical devices mounted on the evaluation board examples of which include data transfer related device drivers such as a USB driver and a serial bus driver and audio related device drivers such as Audio code 1997 AC97 and Infrared Data Association IrDA links.

The embedded software runs in such a way that software units in respective layers are tightly coupled with each other. The software units in the respective layers are classified into a kernel dependent software unit SU a device dependent software unit SU and a processor dependent software unit SU . An exemplary SUis an OS application program interface for providing an OS service. An exemplary SUis software of an LCD controller for supporting a physical device. An exemplary SUis software of the HAL which is dependent on a target processor such as for hardware device initialization and configuration.

Referring to the embedded software is tightly coupled with hardware units as well as with the software units mentioned above. The software units are directly connected to the hardware units when a desired value needs to be read and written through a random access memory RAM or a register. The hardware units are subdivided into a hardware unit d HU and a hardware unit i HU depending on their structures for coupling with the software units. Examples of the HUinclude RAMs and registers that can be directly read written from software to hardware. Examples of the HUinclude universal asynchronous receiver transmitters UARTs universal serial buses USBs and watchdog timers WDTs whose read write operations are indirectly controlled through an address of the hardware unit d HU. Hardware dependent Part Interfaces HPI s are divided into HPIand HPI. Using an HPI the SUor the SUaccesses the HUto read write an expected value. Using an HPI the SUor the SUcontrols the HUthrough the address of the HU.

Referring to for analysis of an interface with the OS layer a control flow of the OS varies depending on the types of OS services such as process management inter process communication and synchronization exception handling virtual memory management physical memory management time management interrupt handling IO management networking and file system management. That is on the basis of a control flow for each OS service OS dependent Part Interfaces OPI s are divided into an OPI an OPI and an OPI. Using the OPI the SUor the SUcalls an SUirrelevant to HU HUcontrol. In this case the SUcorresponds to an application programming interface API for process management inter process communication and exception handling. Using the OPI the SUor the SUcalls a SUrelevant to HUcontrol. In this case the SUcorresponds to an API for virtual memory management. Using the OPI the SUor the SUcalls a SUrelevant to the HU HUcontrol. In this case the SUcorresponds to an API for physical memory management time management interrupt handling IO management networking or file system management.

The five interfaces illustrated in become the criteria of test coverage for testing an interface of the embedded software. Each interface is associated with a symbol for test case selection and pass fail determination and is further associated with a monitoring location for detecting the cause s of a fault in a debugging process. Interface test coverage requires testing of all applicable interfaces. The applicable interfaces are determined according to interface characteristics in the embedded software being tested.

An OS of an exemplary LCD device driver is based on LINUX. Therefore the device driver follows the LINUX standard file operations and upper level application software can invoke or enable the device driver only through standard file operations such as a function open a function close a function read a function write a function mset and a function ioctl .

An interface of the LCD device driver is a unit where functions defined in LCD file operations are present between the software unit SU SU SUand the hardware unit HU HUin a call relationship.

Referring to a function fb write invoked by a function write uses an HPIto write a desired value in a RAM through a function get con display and uses an OPIto write a user input value in the RAM through a function copy from user .

The LCD device driver includes a total of 74 interfaces for a function s3c2440fb init a function fb open a function fb release a function fb read a function fb write a function fb mmap and a function fb ioctl . The 74 interfaces are classified into 32 HPI s 2 HPI s and 40 OPI s based on the interface pattern.

Table 2 illustrates the interface test characteristics of the LCD device driver and interface symbols that must be monitored for the respective characteristics.

From an executable linker format ELF file of a target source the test target analyzer identifies a location where an interface symbol of the interface test characteristics of the LCD device driver which is shown in Table 2 is mapped in a test target source code. The ELF file is used to store all information on a source that is programmed by the developer for the use of a debugger. When a call stack is difficult to identify for example by backtrace objdump is a command for identifying a source address and readelf is a command for indicating ELF file format information.

Referring to in order to detect a location where the memory related interface test characteristics of an HPIis mapped to the source code the size and address of a symbol are extracted from an ELF file generated by a command objdump t and the type of the symbol is extracted from an ELF file generated by a command readelf wi.

An HPIstatic memory map boundary check is performed to test whether a static global variable ranges over a physical memory map boundary as illustrated in . Thus the address and size of the static global variable are an interface of the HPI.

An HPIkernel stack collision test is used to test whether a static global variable collides with a kernel stack as indicated by a dotted line in . Thus the address size and type of the static global variable are an interface of the HPI.

An HPIuser stack collision test is used to test whether a static global variable collides with a user stack as indicated by a dotted line in . Thus the address size and type of the static global variable are an interface of the HPI.

In order to detect a location where the timer related interface test characteristics of an HPIare mapped to a source code a symbol related to a timer of a frame buffer is extracted from an ELF file generated by a command objdump t.

An HPIframe buffer response time test measures the time for a function fb mmap enabled by a function mset of an application to test a frame buffer response time. The time taken from the start of the function fb mmap to the return of the function fb mmap i.e. completion of memory mapping is measured. Thus the called address of the function fb mmap is an interface of the HPI.

In order to detect a location where the interrupt memory management related interface test characteristics of an OPIare mapped to a source code an address for an interface symbol of the OPIis extracted from an ELF file generated by a command objdump IS.

An OPIinterrupt context recovery test is used to test whether a context executed before the occurrence of an interrupt is correctly recovered after the execution of the interrupt. As illustrated in the called addresses of the register storage and recovery commands stmia and ldmia of do IRQ after the call of  irq svc are an interface of the OPI.

The OPIinterrupt latency test is used to measure the time taken from the storage of a context to the recovery of the stored context after the occurrence of an interrupt. Thus the called addresses of the register storage and recovery commands stmia and ldmia of do IRQ are an interface of the OPI.

An OPInormal interrupt service routine test is used to test whether an interrupt service routine ISR for a generated interrupt is correctly executed. As illustrated in when do IRQ is called due to the generation of an interrupt an IRQ number is identified from an RO register and an ISR corresponding to the IRQ number is called by irq desc irq .action handler. Thus the called address of do IRQ is an interface of the OPI.

An OPIabnormal interrupt service routine test is used to test whether an ISR corresponding to an excessive interrupt is correctly executed as many times as the number of generated interrupts as illustrated in . Thus the called address of do IRQ is an interface of the OPI.

An OPIdynamic memory map boundary check is performed to test whether a symbol dynamically allocated by a function kmalloc ranges over a physical memory map boundary as illustrated in . Thus the called address of the function kmalloc is an interface of the OPI.

An OPIkernel stack collision test is used to test whether there is a collision with a kernel stack in the case of access to a kernel space by a function  arch copy from user a function  arch strncpy from user and a function get user as indicated by a solid line in . Thus the called addresses of the function  arch copy from user the function  arch strncpy from user and the function get user are an interface of the OPI.

An OPIuser stack collision test is used to test whether there is a collision with a user stack when data of a kernel space move into a user space by a function copy to user a function put user and a function  arch clear user as indicated by a solid line in . Thus the called addresses of the function copy to user the function put user and the function  arch clear user are an interface of the OPI.

An OPIheap collision test is used to test a collision between symbols in a kernel data segment when a function memset a function  memzero and a function memcpy are called as indicated by a solid line in . Thus the called addresses of the function memset the function  memzero and the function memcpy are an interface of the OPI.

An OPImemory leakage test is used to test whether an address allocated by the function kmalloc is released by a function kfree . Thus the called address of the function kmalloc is an interface of the OPI.

In the case of an OPImemory free latency test because a function kfree in a function kmem cache free one disconnects a link of an actual memory when the function kfree is called as illustrated in the time taken from the call of the function kfree to the call of the function kmem cache free one corresponds to a memory free latency. Thus the called addresses of the function kfree and the function kmem cache free one are an interface of the OPI.

In the case of an OPImis align check because an alignment must be performed on a word basis to be able to prevent a page fault when a code is loaded into a memory the virtual addresses of symbols in an init section a code section and a data section must end with 0 4 8 or C as illustrated in . Thus the addresses for the symbols in the sections are an interface of the OPI.

An OPIcritical region test is used to test whether a critical region is protected from a fast interrupt request FIQ . As illustrated in the call addresses of commands mrs orr and msr for disabling the FIQ simultaneously with critical region entry and the call addresses of commands mrs bic and msr for enabling the FIQ simultaneously with critical region release are an interface of the OPI.

The test case generator generates a test case that covers a test target LCD device driver interface detected by the test target analyzer . The test case is constructed to include an interface symbol corresponding to an input which is to be monitored in each interface data of the interface symbol and an expected output.

A test case for each of the LCD device driver interface characteristics is determined according to each LCD device driver interface location and type. Table 3 shows expected output reference locations that can be used instead of expected output values. The reason for this is that an output value changes every time it is monitored through operation of the emulator .

Test cases generated by the test case generator are constructed in the format of a test script suitable for batch run by the emulator . An interface symbol in Table 3 is a location for setting a break point BP of a test script and an expected output reference location in Table 3 is a location that is to be monitored for determination of pass fail at the location of the interface symbol.

Referring to BPs are set at the called addresses of functions  arch copy from user  arch strncpy from user and get user . A value obtained by adding the size from an R2 register in the emulator must not collide with a stack pointer SP of a kernel stack at the set location. At this point a stack point SP of the kernel stack is monitored by a debugger of the emulator using the value of an R13 SVC register.

An exemplary embodiment of the present invention provides a method for automatically generating an interface test case for the interface test of a LINUX based LCD device driver. The LINUX based LCD device driver is exemplified as being developed on an S3C2440 board having a TRACE32 ICD emulator and an ARM processor.

Referring to in an automatic test case generation method for the interface test of an LCD device driver a test target analyzer automatically identifies interface test characteristics specified in a test model and an interface symbol where each of the interface test characteristics is mapped in an object code. The test case generator receives the identified interface symbol and automatically generates a test case using pass fail criteria based on the input interface symbol.

Referring to the LINUX server provides an object code of the LCD device driver to the test target analyzer step . The LINUX server may also provide a source code of the LCD device driver to the test target analyzer . From the object code of the LCD device driver the test target analyzer generates an ELF file using ARM processor based commands objdump t objdump I S and readelf wi.

The test target analyzer identifies a layer of the LCD device driver step . That is the test target analyzer identifies an inter layer interface of the LCD device driver according to classified definitions. For example it is determined whether the structure of sub functions of the LCD device driver corresponds to the interface defined in Table 1. The test target analyzer identifies the call relationship of the LCD device driver step . That is only sub functions called between interfaces are selected as a test target.

For the sub functions called between interfaces the test target analyzer identifies an interface of the LCD device driver which is defined in Table 2 and an interface symbol to be tested in the interface step . In order to automatically identify a location where the interface symbol is mapped in the source code the test target analyzer maps the interface symbols of the LCD device driver corresponding to HPI HPI OPI OPIand OPIfrom the ELF file and the object code of the LCD device driver step . The test target analyzer extracts a location of the mapped symbol and the test case generator sets each break point in the interface extracted by the test target analyzer step . The test case generator sets each break point as an input of a test case step . The test case generator determines monitoring symbols that are to be monitored for determination of pass fail for each interface step . Based on this an expected output of a corresponding interface is set step . That is a test case is generated using the input and the expected output. At this point the test case is generated in a script format suitable for batch run in the emulator step .

The method for generating the test case for the interface test of the LINUX based LCD device driver according to the present invention combines the debugging monitoring function of the emulator with the interface testing function thereby supporting fault detection and fault cause estimation and automating the test for the LINUX based LCD device driver.

Accordingly the present invention automatically identifies the interface symbols for software of all layers that are organically linked with the LCD device driver including the LINUX based LCD device driver and the kernel related thereto.

In addition the present invention automatically generates the test case for the interface test of the LINUX based LCD device driver. The present invention automatically identifies the test case covering the interface of the identified LINUX based LCD device driver and adds a function for automatically determining the pass fail of a test input symbol to the test case thereby determining the test pass fail automatically when the generated test case is executed.

As described above the present invention makes it possible to automatically generate a test case for the interface test of a device driver.

In addition the present invention can automatically identify the test case covering the interface of the device driver and can add the function for automatically determining the pass fail of the test input symbol to the test case thereby making it possible to automatically determine the test pass fail when the generated test case is executed.

The above disclosed subject matter is to be considered illustrative and not restrictive and the appended claims are intended to cover all such modifications enhancements and other embodiments which fall within the true spirit and scope of the present invention. Thus to the maximum extent allowed by law the scope of the present invention is to be determined by the broadest permissible interpretation of the following claims and their equivalents and shall not be restricted or limited by the foregoing detailed description.

