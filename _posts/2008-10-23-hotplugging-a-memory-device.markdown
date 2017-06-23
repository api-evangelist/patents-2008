---

title: Hot-plugging a memory device
abstract: An extensible firmware interface (EFI) framework is to enable hot-plugging and hot-removal of memory devices. The security phase of the EFI may enable a cache to operate as RAM (CAR mode) to support execution of pre-EFI (PEI) tasks. In one embodiment, the PEI phase may move the memory reference code (MRC) as a driver to the driver execution phase and hand-over the CAR information to the driver execution environment (DXE). The MRC driver may be registered as a run-time API, which may be called by the operating system to receive a dynamically created memory map. In other embodiment, the PEI phase executes the MRC and may hand-over the memory information and a memory pointer to the MRC to the DXE. The OS may call the DMD driver provisioned in the DXE, which in turn may call the MRC provisioned in the PEI to dynamically create a memory map.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08145893&OS=08145893&RS=08145893
owner: Intel Corporation
number: 08145893
owner_city: Santa Clara
owner_country: US
publication_date: 20081023
---
This application claims priority to Indian Patent Application Number 2239 DEL 2007 titled HOT PLUGGING A MEMORY DEVICE filed Oct. 26 2007.

A computer system may be booted up by a basic input output system BIOS during a power ON or restart phase. As a part of the boot process the BIOS uses a memory reference code MRC to detect and configure a main memory in the computer system. A memory reference code generates a memory map of one or more memory devices coupled to the computer system. The BIOS may run the MRC once during each boot process and the memory map may not change until the computer system is booted up again.

The following description describes hot plugging a memory device. In the following description numerous specific details such as logic implementations resource partitioning or sharing or duplication implementations types and interrelationships of system components and logic partitioning or integration choices are set forth in order to provide a more thorough understanding of the present invention. It will be appreciated however by one skilled in the art that the invention may be practiced without such specific details. In other instances control structures gate level circuits and full software instruction sequences have not been shown in detail in order not to obscure the invention. Those of ordinary skill in the art with the included descriptions will be able to implement appropriate functionality without undue experimentation.

References in the specification to one embodiment an embodiment an example embodiment indicate that the embodiment described may include a particular feature structure or characteristic but every embodiment may not necessarily include the particular feature structure or characteristic. Moreover such phrases are not necessarily referring to the same embodiment. Further when a particular feature structure or characteristic is described in connection with an embodiment it is submitted that it is within the knowledge of one skilled in the art to affect such feature structure or characteristic in connection with other embodiments whether or not explicitly described.

Embodiments of the invention may be implemented in hardware firmware software or any combination thereof. Embodiments of the invention may also be implemented as instructions stored on a machine readable medium which may be read and executed by one or more processors. A machine readable medium may include any mechanism for storing or transmitting information in a form readable by a machine e.g. a computing device .

For example a machine readable medium may include read only memory ROM random access memory RAM magnetic disk storage media optical storage media flash memory devices electrical optical acoustical or other forms of propagated signals e.g. carrier waves infrared signals and digital signals . Further firmware software routines and instructions may be described herein as performing certain actions. However it should be appreciated that such descriptions are merely for convenience and that such actions in fact result from computing devices processors controllers and other devices executing the firmware software routines and instructions.

An embodiment of a computer system which may support hot plugging of memory devices is illustrated in . In one embodiment the computer system may comprise a hardware a cache a main memory a hot plug memory a firmware an extensible firmware interface EFI an OS loader and an operating system .

In one embodiment the hardware may comprise a processor a chipset BIOS integrated circuit and similar other components. In one embodiment such a processor may be coupled to the cache . Also the hardware may be coupled to the firmware . In one embodiment the chipset may comprise a memory controller hub and an I O controller hub. In one embodiment the main memory may be coupled to the memory controller hub. In one embodiment the main memory may support the operating system OS . In one embodiment the hot plug memory may be plugged into the computer system after the computer system is booted up.

In one embodiment the cache may comprise fast memory which may support higher access speeds. In one embodiment the cache may comprise a SRAM memory. In one embodiment the cache may support the extensible firmware interface EFI . In one embodiment the size of the cache may be chosen to support the firmware and the EFI during the boot up phase. In one embodiment the size of the cache may equal 1 MB.

In one embodiment the firmware may comprise read only memory ROM such as programmable ROM electrically programmable ROM and such other similar devices. The firmware may support components such as an extensible firmware interface EFI BIOS legacy BIOS a system abstraction layer and a hardware abstraction layer. The components of the firmware may perform functions such as machine check abort handling and other processor functions which may be dependent on the characteristics of the hardware . In one embodiment the firmware may be coupled to the extensible firmware interface EFI .

In one embodiment the EFI operating system EFI OS loader may load the installed operating system such as the operating system in response to receiving a load signal from the EFI . In one embodiment the EFI OS loader may represent a last EFI application before the EFI phase is complete.

In one embodiment the operating system may comprise processes that manage the allocation of resources of the computer system . In one embodiment the operating system may comprise Windows XP Linux Unix MacOS operating systems. Typically after the completion of the boot up phase the OS may receive the memory map from the firmware . The memory map does not change thereafter until the computer system is re booted as the memory reference code MRC does not run again to detect the change in the memory. As a result the OS may not recognize memory devices that may be hot plugged. To recognize the hot plugged memory devices the computer system may be re booted and the BIOS may generate a new memory map comprising the memory information the hot plugged memory device. However re booting the computer system may consume processing cycles as the BIOS is to be re run and the OS and the applications is to be reloaded. Such an approach may also consume time may not allow the physical memory to be increased or replace a non functional memory without re booting the computer system .

In one embodiment the operating system may comprise a command or an application or a hardware interrupt to initiate memory hot plugging. In one embodiment memory hot plugging may refer to plugging in the memory device such as the hot plug memory while the computer system is ON or running. In one embodiment the operating system may initiate a task to allow highest access grant and may call memory reference code MRC registered as a runtime application programming interface API discover hot plug memory and re calculate the memory map. In one embodiment the operating system may receive a memory table in response to calling the MRC runtime API.

In one embodiment the memory table may comprise a list of memory devices such as the main memory detected during the boot up and a list of memory devices such as the hot plug memory which may be hot plugged. In one embodiment the operating system may use the list of hot plugged memory devices in the memory table to re map the memory configuration. In one embodiment the re mapping of the memory configuration may enable the operating system to detect the hot plugged and hot removed memory devices without having to re boot the computer system .

In one embodiment the extensible firmware interface EFI framework may provide an interface between the firmware and the operating system . In one embodiment the EFI may support modular approach and may use high level languages such as the C programming language. As a result the EFI may provide a scalable flexible and hardware independent approach to boot the computer system . In one embodiment the EFI may operate in three different phases such as a security phase a pre EFI initialization PEI phase and a driver execution environment DXE phase.

An embodiment of the computer system operating in a boot phase to enable hot plugging of memory is illustrated in . In block the security block while in the security phase may enable the cache to operate as RAM cache as RAM CAR mode . In one embodiment the security block may enable a large portion e.g. 1 2 MB of the cache as RAM for supporting execution of PEI operations.

In block the PEI may move the MRC as a driver MRC driver D to the driver execution environment DXE . In one embodiment the operation of cache in CRAM mode may enable the MRC to be moved as the MRC driver D.

In block the PEI may pass the CAR information to the DXE . In one embodiment the CAR information may comprise the address range of the region of the cache that may be available for the DXE and may also comprise the address range of the region of the cache used by the PEI . In one embodiment the PEI may pass the CAR information as a hand off block HOB list to the DXE .

In block the DXE may initialize the DXE components such as the boot services on the cache . In one embodiment the DXE may initialize the mandatory drivers on the cache . In one embodiment the boot services may comprise a scheduler drivers and the MRC driver D.

In block the boot services may run the MRC driver D. In one embodiment the scheduler may execute the MRC driver D as the first driver. In one embodiment the execution of the MRC driver D may be set as a dependency for the execution of the drivers . In one embodiment the scheduler may initiate execution of the MRC driver D before executing the other mandatory drivers of the drivers .

In one embodiment the MRC driver D may discover the memory devices coupled to the computer system . In one embodiment the available memory devices may comprise memory devices such as the main memory coupled to the computer system before the boot up phase.

In block the boot services may execute the drivers to re map the stack variables public data and such other similar data stored in the cache to the discovered memory such as the main memory .

In block the boot services may register the MRC driver D as a run time application programming interface API . In one embodiment the run time services may comprise a dynamic memory detection DMD block . In one embodiment the MRC driver D may be registered as a run time API with the DMD block of the run time services .

In one embodiment after registering the MRC driver D as a run time API the drivers may execute ExitBootServices command to terminate the boot services phase. After termination of the boot services phase the boot services may become unavailable to the OS .

An embodiment of the computer system operating in a run time phase which detects hot plugging of a memory is illustrated in .

In block the operating system may initiate memory hot plug detection feature. In one embodiment the hot plugged memory may be plugged into the computer system after the boot up phase is completed. In one embodiment the OS may comprise a command or an application or a hardware interrupt to initiate memory hot plugging.

In block the operating system may call dynamic memory detection DMD API. In one embodiment the DMD API may be supported by the run time services .

In block the dynamic memory detection DMD API supported by the run time services may call the MRC driver D which may be registered as a run time API. In one embodiment in response to being called by the DMD API the MRC driver D may generate a new memory map which may comprise the memory map of the hot plugged memory .

In one embodiment the MRC driver D may comprise a flag to indicate the boot time and run time portions of the code. In one embodiment the MRC driver D may skip boot time portion of the code and execute the run time portion of the code to recognize the memory devices that are hot plugged or hot removed. In one embodiment the MRC may comprise a list of memory devices detected during the boot up phase and a list of memory devices hot plugged or hot removed.

In one embodiment the MRC driver D may create a GCD memory table or E table or may use an advanced configuration power interface ACPI driver to create a memory table. In one embodiment the GD memory table may be generated if the OS is an EFI aware OS. In one embodiment the E memory table may be generated by a legacy OS. In one embodiment the run time services may provide a dynamically updated new memory map to the EFI OS loader . In one embodiment GCD memory table E memory table may be loaded to the OS by the EFI OS loader . In one embodiment after remapping the MRC driver D and the drivers may reside in a reserved memory area which is not used by the operating system .

In block the operating system may use the memory map generated by the MRC driver D to remap the memory configuration.

An embodiment of a computer system supporting hot plugging of memory device is illustrated in . The differences between the embodiment of the computer system of and the computer system of are described below. In one embodiment during the PEI phase the PEI may execute the MRC as compared to moving the MRC from the PEI to the DXE in . In one embodiment the memory information detected by the MRC and a memory pointer to the MRC may be passed to dynamic memory detection DMD block of the DXE . In one embodiment during the boot up phase the dynamic memory detection DMD may be registered as a run time API with the run time services .

An embodiment of the computer system operating during the boot up phase is described in . In block the security block while in the security phase may enable the cache to operate as RAM cache as RAM CAR mode . In one embodiment the security block may enable a large portion e.g. 1 2 MB of the cache to operate as RAM for supporting execution of PEI operations.

In block the PEI may execute the MRC . A memory map may be generated by executing the MRC . In one embodiment the memory map may comprise a map of the main memory .

In block the PEI may pass the memory information of the main memory and a memory pointer of the MRC to the DXE . In one embodiment the memory information may comprise the address range of a region in the main memory that may be available for the DXE and may also comprise the address range of a region of the main memory used by the PEI . In one embodiment the PEI may pass the memory information and the memory pointer as a hand off block HOB list to the DXE .

In block the DXE may initialize the DXE components such as the boot services in the main memory . In one embodiment the DXE may initialize the mandatory drivers in the main memory . In one embodiment the boot services may comprise a scheduler drivers and the DMD driver .

In block the boot services may run the DMD driver to register the DMD as a run time API. In one embodiment the scheduler may execute the DMD driver as the first driver. In one embodiment the execution of the DMD driver may be set as a dependency for the execution of the drivers . In one embodiment the scheduler may initiate execution of the DMD driver before executing the other mandatory drivers of the drivers . In one embodiment on being called the DMD driver may call the MRC which may discover the memory devices coupled to the computer system .

An embodiment of the computer system operating in a run time phase which detects hot plugging of a memory is illustrated in .

In block the operating system may initiate memory hot plug detection feature. In one embodiment the hot plugged memory may be plugged into the computer system after the boot up phase is completed. In one embodiment the OS may comprise a command or an application or a hardware interrupt to initiate memory hot plugging.

In block the operating system may call dynamic memory detection DMD API. In one embodiment the DMD driver which may be registered as an API with the run time services may be supported by the DXE . In one embodiment the run time services may call the DMD driver in response to receiving a call from the OS .

In block the DMD driver may call the MRC resident in the PEI . In one embodiment in response to being called by the DMD driver the MRC may generate a new memory map which may comprise the memory map of the hot plug memory . In one embodiment the MRC may create a GCD memory table or E table or may use an advanced configuration power interface ACPI driver to create a memory table. In one embodiment the GD memory table may be generated if the OS is an EFI aware OS. In one embodiment the E memory table may be generated by a legacy OS. In one embodiment the run time services may provide a dynamically updated new memory map to the EFI OS loader .

In block the operating system may use the memory map generated by the MRC to remap the memory configuration.

Certain features of the invention have been described with reference to example embodiments. However the description is not intended to be construed in a limiting sense. Various modifications of the example embodiments as well as other embodiments of the invention which are apparent to persons skilled in the art to which the invention pertains are deemed to lie within the spirit and scope of the invention.

