---

title: Memory registration caching
abstract: A method for memory registration caching comprising enumerating a first process for a first process, in response to a memory registration cache being activated; finding an import table for the first module, wherein one or more pointers, in the import table, refer to memory management routines in a first library; changing the pointers so that the pointers refer to memory management routines in a second library; overloading routines that refer to the memory management routines in the first library so that the routines refer to the memory management routines in the second library; intercepting memory allocation requests, wherein the size of the request is forwarded to the memory registration cache; and de-registering freed memory from the memory registration cache.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07941629&OS=07941629&RS=07941629
owner: Intel Corporation
number: 07941629
owner_city: Santa Clara
owner_country: US
publication_date: 20080228
---
A portion of the disclosure of this patent document contains material which is subject to copyright protection. The owner has no objection to the facsimile reproduction by any one of the patent document or the patent disclosure as it appears in the Patent and Trademark Office patent file or records but otherwise reserves all copyrights whatsoever.

Certain marks referenced herein may be common law or registered trademarks of third parties affiliated or unaffiliated with the applicant or the assignee. Use of these marks is for providing an enabling disclosure by way of example and shall not be construed to limit the scope of this invention to material associated with such marks.

The present disclosure relates generally to memory registration in a computing environment and more particularly to memory registration caching in an operating system based on intercepting memory management calls.

An application may send and receive messages over a network allocating memory as needed through memory registration. Memory registration causes an operating system to allocate memory for the application and provide address translation for the network s interface card NIC reserving the memory until the memory is no longer needed by the application i.e. when the allocated memory is de registered .

Particularly in high speed networks e.g. Infiniband Myrinet memory registration and de registration operations are slow compared to other network operations such as high speed data transfers. Therefore a caching scheme may be implemented to increase network performance by reducing the number of memory registration and de registration operations that would be otherwise necessary.

In certain operating systems e.g. the Microsoft Windows operating system in order to take advantage of the caching the operating system has to rebuild the target application by explicitly importing each external variable and bounding each variable to the dynamic library that declares that variable. Since a substantial amount of overhead is associated with rebuilding the application the performance benefits associated with the above noted caching scheme are effectively rendered worthless.

For the above reasons systems and methods are needed that can facilitate a memory registration caching scheme that automatically monitors memory management in an operating system without having to rebuild the target application.

Features elements and aspects of the invention that are referenced by the same numerals in different figures represent the same equivalent or similar features elements or aspects in accordance with one or more embodiments.

The present invention is directed to methods and systems for memory registration caching based on intercepting memory management calls.

For purposes of summarizing certain aspects advantages and novel features of the invention have been described herein. It is to be understood that not all such advantages may be achieved in accordance with any one particular embodiment of the invention. Thus the invention may be embodied or carried out in a manner that achieves or optimizes one advantage or group of advantages without achieving all advantages as may be taught or suggested herein.

In accordance with one embodiment a method for memory registration caching is provided. The method comprises enumerating a first module for a first process in response to a memory registration cache being activated finding an import table for the first module wherein one or more pointers in the import table refer to memory management routines in a first library changing the pointers so that the pointers refer to memory management routines in a second library overloading routines that refer to the memory management routines in the first library so that the routines refer to the memory management routines in the second library intercepting memory allocation requests wherein the size of the request is forwarded to the memory registration cache and de registering freed memory from the memory registration cache.

In accordance with another embodiment a computer program product comprising a computer useable medium having a computer readable program is provided. The computer readable program when executed on a computer causes the computer to perform the functions and operations associated with the above disclosed methods. In accordance with yet another embodiment a system comprising one or more logic units is provided. The one or more logic units are configured to perform the functions and operations associated with the above disclosed methods.

One or more of the above disclosed embodiments in addition to certain alternatives are provided in further detail below with reference to the attached figures. The invention is not however limited to any particular embodiment disclosed.

Referring to in accordance with one embodiment exemplary system may comprise application operating system and memory registration cache . Operating system may comprise an application program interface API library and other libraries . System may be connected to network by way of network interface card NIC .

An API is a specification that allows two programs to communicate with each other. API library may comprise a set of routines protocols or tools for building an application that is able to communicate with operating system . Application may call routines in API library to request services from operating system for example.

Other libraries may comprise a message passing interface MPI library. MPI is a language independent communication standard commonly implemented in computing systems with parallel processing capabilities. The MPI library may comprise API routines that allow one process to communicate with another process that is running at the same time. Application may send and receive messages to another application in another computing system not shown over network using MPI library for example.

In one embodiment other libraries may also comprise a network communication interface library e.g. direct access programming library DAPL . A network communication interface library may allow an application to run on different types of network fabrics e.g. Infiniband Myrinet . Application may be compatible with networks not shown other than network for example.

It is noteworthy that in the following one or more concepts or embodiments may be disclosed as related to or as applicable to the Windows operating system. Such references are by way of example however and as such this disclosure and the concepts disclosed herein may be equally applicable to any other type of operating system or system architecture in accordance with other embodiments or depending on implementation.

Referring to in accordance with one embodiment memory management calls initially refer to a first library e.g. Windows API library . When memory registration cache is activated S a second library e.g. MPI library enumerates or lists the modules of a first process that is loaded S . For each module the library finds the module s import table S which contains pointers to API routines and changes one or more pointers so that the pointers refer to memory management routines in the second library e.g. MPI library instead of the first library e.g. Windows API library S .

The second library e.g. MPI library overloads routines that refer to the memory management routines in the first library e.g. Windows API library so that the routines refer to the memory management routines in the second library e.g. MPI library S . Moved up 

When application requests memory to be allocated the second library e.g. MPI library intercepts the request and forwards the size of memory requested to memory registration cache thereby performing memory registration S . Memory registration cache uses the size information to de register the allocated memory when the memory is freed S .

Referring to in accordance with one embodiment once the algorithm provided in is applied process module may call one or more memory management routines. Since the pointers have been changed if for example process module calls an API routine e.g. VirtualFree HeapFree HeapRealloc or VirtualAlloc from the first library e.g. Windows API library a corresponding API routine e.g. VirtualFree hook HeapFree hook HeapRealloc hook or VirtualAlloc hook from the second library e.g. MPI library will be called instead.

If process module calls a memory routine that allocates memory e.g. VirtualAlloc hook for example the registration routine for memory registration cache will also be called. If process module calls a memory routine that frees memory e.g. VirtualFree hook HeapFree hook or HeapRealloc hook for example the de registration routine for memory registration cache will also be called.

If for example process module attempts to load a dynamic library e.g. by calling LoadLibrary a corresponding API routine e.g. LoadLibrary hook from the second library e.g. MPI library will be called instead. If for example process module attempts to directly obtain a process address e.g. by calling GetProcAddress a corresponding API routine e.g. GetProcAddress hook from the second library e.g. MPI library will be returned instead.

In one embodiment the changed pointers and the overloaded routines may be restored to their original state so that the changed pointers and the overloaded routines may be referenced by a third library e.g. DAPL if the restoring occurs after the third library s finalization.

Depending on implementation it is possible that the present invention can take the form of an entirely hardware embodiment an entirely software embodiment or an embodiment containing both hardware and software elements. A software embodiment may include but not be limited to to firmware resident software microcode etc.

Furthermore the invention can take the form of a computer program product accessible from a computer usable or computer readable medium providing program code for use by or in connection with a computer or any instruction execution system. For the purposes of this description a computer usable or computer readable medium can be any apparatus that can contain store communicate propagate or transport the program for use by or in connection with the instruction execution system apparatus or device.

A data processing system suitable for storing and or executing program code will include at least one processor coupled directly or indirectly to memory elements through a system bus. The memory elements can include local memory employed during actual execution of the program code bulk storage and cache memories which provide temporary storage of at least some program code in order to reduce the number of times code must be retrieved from bulk storage during execution.

Other components may be coupled to the system. Input output or I O devices including but not limited to keyboards displays pointing devices etc. can be coupled to the system either directly or through intervening I O controllers. Network adapters e.g. modem cable modem Ethernet cards may also be coupled to the system to enable the data processing system to become coupled to other data processing systems or remote printers or storage devices through intervening private or public networks.

It should be understood that the logic code programs modules processes methods and the order in which the respective elements of each method are performed are purely exemplary. Depending on the implementation they may be performed in any order or in parallel unless indicated otherwise in the present disclosure. Further the logic code is not related or limited to any particular programming language and may be comprise one or more modules that execute on one or more processors in a distributed non distributed or multiprocessing environment.

The method as described above may be used in the fabrication of integrated circuit chips. The resulting integrated circuit chips can be distributed by the fabricator in raw wafer form that is as a single wafer that has multiple unpackaged chips as a bare die or in a packaged form. In the latter case the chip is mounted in a single chip package such as a plastic carrier with leads that are affixed to a motherboard or other higher level carrier or in a multi chip package such as a ceramic carrier that has either or both surface interconnections of buried interconnections .

In any case the chip is then integrated with other chips discrete circuit elements and or other signal processing devices as part of either a an intermediate product such as a motherboard or b and end product. The end product can be any product that includes integrated circuit chips ranging from toys and other low end applications to advanced computer products having a display a keyboard or other input device and a central processor.

Therefore it should be understood that the invention can be practiced with modification and alteration within the spirit and scope of the appended claims. The description is not intended to be exhaustive or to limit the invention to the precise form disclosed. These and various other adaptations and combinations of the embodiments disclosed are within the scope of the invention and are further defined by the claims and their full scope of equivalents.

