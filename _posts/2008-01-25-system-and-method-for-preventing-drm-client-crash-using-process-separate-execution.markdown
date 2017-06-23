---

title: System and method for preventing DRM client crash using process separate execution
abstract: A computer system includes a DRM client system in which a plurality of DRM clients are installed, comprising: a virtual OS managing unit that separates a kernel of an actual operating system installed in the DRM client system to generate and manage a virtual operating system; a branch process information managing unit that manages branch process information according to a type of a document that a user attempts to read; and an application program branching unit that analyzes the branch process information and executes DRM client agent for managing the DRM client in an actual OS region or a virtual OS region according to the type of a document that the user attempts to read to allow the user to read the document.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08468543&OS=08468543&RS=08468543
owner: Fasoo.Com.Co.Ltd.
number: 08468543
owner_city: Seoul
owner_country: KR
publication_date: 20080125
---
The present invention relates to a system and method for preventing a DRM client crash using process separate execution and more specifically to a system and method for preventing a crash between DRM clients by using operating system virtualization to separate and execute a process in a case where a plurality of DRM clients are used in a single PC.

Many systems have been established in an enterprise to allow information and knowledge to be shared and as a consequence distribution of documents has been briskly made. Since late 1990s when doing the Internet started to become an everyday activity enterprises have been making an enormous investment on security in order to prevent the external leakage of the crucial company information by outside hackers.

However the information leakage out of the company is mostly due to the carelessness or design of an insider. Accordingly an insider threat management ITM is necessary to prevent the information leakage by insiders.

Methods such as Blocking Content Filtering and Logging have been attempted as technical methods for the ITM. However Blocking has a problem in that it is difficult to prevent the intentional leakage Content Filtering has a problem in that the system capacity may be lowered and it is difficult to perform exact filtering and Logging has a limitation of not being capable of preventing the leakage in advance as it is a postmeasure.

Recently EDRM Enterprise DRM using DRM Digital Right Management developed to protect the copyright of content draws attention as an appropriate solution to a document security method in the enterprise and therefore is introduced by many advanced companies.

The basic concept of DRM is to restrict the use of contents documents files and the like according to a copy right holder s intention and this encrypts and transfers contents and defines how the contents should be used.

DRM may be classified into Consumer DRM CDRM and Enterprise DRM EDRM . CDRM primarily focuses on the copyright protection of contents whereas EDRM primarily focuses on document security of a company.

EDRM maintains document security by constantly controlling users use environments and functions with respect to use of in house documents.

The sub module of an EDRM product is mainly composed of a policy server that determines a security policy a license server that issues a license and a DRM client. The DRM client plays an important role that is the DRM client decrypts an encrypted file transfers the decrypted file to a rendering application and allows the file to be used only within a predetermined range to block the information leakage path.

A technology of realizing the DRM client may be classified into three methods such as Embedding Plug in and Overriding.

Embedding is a method of implementing DRM functions directly in source codes of the rendering application and this is easiest to implement and has a high security level. However Embedding has a restriction in that this may be applicable only in case of being capable of fixing the source codes.

Plug in is a method of restricting the use of the rendering application by using APis provided from the rendering application. This has a limitation in its application since many of rendering applications do not provide the APis and may have a weakness in security because of using public APis.

Overriding is a method of changing the execution codes of the rendering application at runtime in a memory and this is also referred to as Hooking or API Hooking . Although having many difficulties in implementation this method has advantages of being capable of controlling any rendering applications and having superior security and therefore is partially or fully employed by numerous DRM vendors.

The API Hooking technology may be applied to both a user level and a kernel level of an operating system wherein the user level is mainly used. Although various methods are included in the user level API Hooking two types of methods such as an IAT alteration method that alters an execution binary IAT Import Address Table and a code overwriting method that alters an execution binary code are used the most because of being capable of most efficiently supporting functions required for the DRM client module.

However as the EDRM is spread to companies EDRMs from various DRM vendors happened to apply to a company. As DRM client modules from various DRM vendors which have been developed by using an API Hooking technology are installed in a single PC a crash may occur and this may cause it impossible to read encrypted documents malfunction or abnormal end of an application program malfunction of an operating system or lowering in speed.

The API Hooking technology such as the IA T alteration method and the code overwriting method is based on a variation of an API call path. That is the operation of an application program is controlled by manipulating parameters and return values of an API that is called by changing and detouring a specific API call path in the call relationship between modules which belongs to the application program and arranging the DRM client module in the detoured path.

The address value of the API to be called should be varied to change the API call path. However a series of processes are performed as follows in the course of loading the process of an application program under control if DRM client modules from two or more different DRM vendors are installed and operated.

 4 Alteration of API call path of modules by DRM client modules loaded in the corresponding application process region.

A process that each DRM client module of each DRM vendor changes an API call address value of the same specific module into its own specific function is performed in the process 4 among the above mentioned processes and this process is sequentially done in an order of loading each DRM client module of each DRM vendor on the application program process region. The API call address value changed with the result of the process 4 is variable according to the loading order of each DRM client of each DRM vendor and the API call address change and management method of each DRM client module. This result may lead to various problems as in Table 1.

In incidence of the above mentioned crash case 3 in Table 1 causes the most serious problem the cause of which is as follows.

A few tens of APIs are used when an application program performs one operation such as reading document and the number of calls of the APis although varying as the case may be reaches a few hundreds or a few thousands. Expected parameters and return values are transferred according to a predetermined order in the course of these series of calls so that the operation may be processed normally.

However multiple API call address values used for an application program are mixed and varied with function address values of DRM client modules from different vendors in case 3 in Table 1 and therefore the series of API calls that come with one operation are done between DRM client modules from different vendors that are implemented in different methods and logics resulting in the failure of some API calls and entrance into unexpected addresses or return of unexpected parameters and result values. Therefore any application program that is not well equipped with an exception process device in this case may give rise to a malfunction or abnormal end. In addition incidence of the malfunction of the application program in the course of interfacing with an operating system through IPC Inter process Communication may have an effect on the function of the operating system thus leading to a malfunction of the system or lowering in speed.

As a result it can be seen that a crash occurring when the DRM clients from various DRM vendors simultaneously operate in a single PC comes from a fact that each DRM client module employs the same technology to control the same application program process at the same time. Making only one DRM client operate when the application program process is operated that is making only one DRM client agent program driving and managing the DRM client operate at one time may be considered most easily as a method to escape from such a crash. This may be done by a method of initiating and ending the DRM client agent program of each DRM vendor through a GUI Graphical User Interface .

This is the method that was attempted two or three years ago when a crash between DRM clients were firstly issued in the domestic information security industries that commercialized and encouraged DRM solutions for the first time in the world and this method was called DRM agent manual switch . This method could be applied without any other additive adverse effects or problems. However this method was not welcome by end users because of inconvenience in use that users should select and drive a DRM client agent of the vendor beforehand to read an encrypted document in the format of a specific DRM vendor and it is impossible to simultaneously read encrypted documents from various DRM vendors and therefore use rate of EDRM system was decreased thus leading to a request of a further advanced method for crash avoidance.

This request created a further improved type of a crash avoidance method in which a predetermined Active DRM vendor is set while the DRM client agents from various DRM vendors are operated at the same time and the format of a document is identified and processed at the time of a user reading the document. This method has a meaning in terms of removal of user s inconvenience because of not requiring user s additive work prior to reading of the document.

This may activate the Active DRM client to allow the document to be read without any other additive work if the document that the user attempts to read is made in the format of the current Active DRM vendor. If the document that the user attempts to read is made in the format of DRM vendors other than the Active DRM vendor the DRM client module from the Active DRM vendor changes the other DRM vendors to be in the Active state and then shows the user an appropriate message to induce the user to reattempt to read the document. At this time if the user attempts to read the document again the format of the document conforms to the Active DRM vendor so that the user may read the document. This method is called DRM agent semiautomatic switch .

However the above mentioned method has some inconveniences in that the DRM client from each vendor should be redistributed by adding a corresponding function with the aid of each DRM vendor used and document reading should be attempted after the application program is ended in a case where the format of the document that the user attempts to read does not conform to the preset Active DRM vendor and encrypted documents from various DRM vendors are still impossible to read at the same time like in the conventional methods.

A number of different methods were designed and attempted to solve the above problems and inconveniences one of which is directed to a method of separating and executing a process of an application program. This process separation method which identifies the format of a document at the time of reading the document to separate and generate the process instance for each and every DRM vendor was evaluated as a more advanced method than existing switch methods for example in view of being capable of reading documents from various DRM vendors at the same time. However this method is known not to have been commercialized because of being not capable of applying to application programs that cannot create two or more process instances having a difficulty in a process when various functions Copy Paste OLE object insertion etc. operate using an IPC between application program processes during which documents from different DRM vendors are opened and not guaranteeing the safety.

An object of the present invention is to provide a system and method for preventing a DRM client crash that is directly applicable without any change and redistribution of DRM client modules by separating and executing a process using operating system virtualization and does not require additional work in order to prevent a crash that may occur when DRM client modules from different DRM vendors which have been developed using an API Hooking technology are installed and used in a single PC.

Another object of the present invention is to provide a system and method for preventing a DRM client crash that allows documents having formats from different DRM vendors to be simultaneously read which was impossible in the conventional methods and may apply even to application programs that cannot create two or more process instances in a single operating system.

To achieve the above objects the system according to the present invention is characterized by a system for preventing a DRM client crash in a PC in which a plurality of different DRM clients are installed including a virtual OS managing unit that separates a kernel of an actual operating system installed in the PC to generate and manage a virtual operating system a branch process information managing unit that manages branch process information according to the type of a document that a user attempts to read and an application program branching unit that analyzes the branch process information and executes an application program in a designated OS region according to the type of a document that the user attempts to read to allow the user to read the document.

To achieve the above objects the method according to the present invention is characterized by a method for preventing a DRM client crash in a PC in which a plurality of different DRM clients are installed including an OS virtualization step that separates a kernel of an actual operating system of the PC to generate a virtual operating system a document reading attempt event generation step that attempts to read a document file in a PC in which the OS virtualization has been done a step of transferring information on a path of the document and an application program to be executed to an application program branching unit according to the document reading attempt event a step of querying for branch process information of the document to determine the type of the document by the application program branching unit and a step of executing an application program in a designated OS region according to the determined type of the document to open the document by the application program branching unit.

To achieve the above objects another method according to the present invention is characterized by a method for preventing a DRM client crash in a PC in which a plurality of different DRM clients are installed including an OS virtualization step that separates a kernel of an actual operating system of the PC to generate a virtual operating system a reading attempt event generation step that attempts to read a document attached to a web page through a web browser in a PC in which the OS virtualization has been done a step of detecting information on a path of the document attached to the web page and an application program according to the reading attempt event by an application program branching unit a step of querying for branch process information of the document to determine the type of the document by the application program branching unit and a step of executing an application program in a designated OS region according to the determined type of the document to open the document by the application program branching unit.

The present invention may be directly applicable without change and redistribution of DRM client modules and thus is fairly well economical compared to existing methods and may be easily used without such user s additional work as the conventional methods in reading the documents from different DRM vendors.

Further the present invention allows documents having different formats from different DRM vendors to be simultaneously read which was impossible in the conventional methods and may apply even to application programs that cannot create two or more process instances in a single operating system.

Moreover the present invention may be stably operated because of not being affected in various operations using IPCs and data exchange between application programs under control since the actual operating system region and the virtual operating system region are completely separated from each other.

The present invention suggests a system and method for preventing a crash between DRM clients from two or more different DRM vendors that are installed in a single PC using operating system OS virtualization.

The OS virtualization is generally separated into a hardware emulation method and an OS partitioning method.

The present invention may originally prevent interference and crashes between DRM clients from two or more different DRM vendors by generating several virtual operating system regions which are securely isolated from each other in a sandbox type in a single PC by the OS partitioning method among the above described OS Virtualization methods and independently executing the DRM client modules over different OS regions.

Hereinafter preferred embodiments of the present invention will be described in detail with reference to accompanying drawings. When it is determined that the detailed descriptions of the known techniques or structures related to the present invention depart from the scope of the invention the detailed descriptions will be omitted.

In the meanwhile application programs and DRM clients and from DRM vendor A and DRM vendor B respectively are all installed on an actual operating system of the PC in the preferred embodiment of the present invention shown in .

Referring to the system for preventing a DRM client crash using OS virtualization according to the present invention generally includes a virtual OS managing unit a branch process information managing unit and an application program branching unit and may further include an IPC interface .

The virtual OS managing unit separates the kernel of the actual operating system installed in the PC by the above described OS partitioning method to generate and manage the virtual operating system . At this time it is preferred that the virtual operating system is generated upon a boot of the PC or at any appropriate time similar to this.

In addition the number of the virtual operating systems to be generated is not particularly restricted but preferred to correspond to the number of the DRM clients further installed in the PC. For instance it is preferred to generate two virtual operating systems so that there are included one actual operating system and two virtual operating systems if three different DRM clients are installed in the PC.

In the meanwhile the virtual OS managing unit may have a function to end the application program under operation over the virtual operating system .

The branch process information managing unit manages branch process Information so that the application program branching unit branch processes the execution region of the application program according to the type of a document that a user attempts to read.

The branch process information includes branch object application program a document type and execution OS region information. In addition the branch process information is defined in XML and encrypted for management.

The branch object application program information may include a branch object application program name and an execution file name for example Winword.exe and the document type may be defined and configured for example in such a manner that 1 general document 2 encrypted document of DRM vendor A and 3 encrypted document of DRM vendor B. And the execution OS region information may be defined and configured for example as ROS in case of an actual OS region and as VOS 1 and VOS 2 according to the number of generated virtual OSs in case of a virtual OS region.

As an example the branch process information may be defined as follows in a case where the branch object application program is MS office word of Microsoft corporation the document type is an encrypted document of DRM vendor B and the execution OS region is virtual OS region 1.

The application program branching unit is an application program execution branch process module that queries for the branch process information according to the type of a document for example a general document an encrypted document of DRM vendor A and an encrypted document of DRM vendor B when a user attempts to read the document and executes the application program in a designated OS region actual OS region or virtual OS region to allow the user to read the document.

For instance the application program branching unit activates a DRM client agent which drives and manages a DRM client in the region of the virtual OS so that the application program is executed in the region of the virtual operating system when the encrypted document of DRM vendor B intends to be read as shown in .

In a case where the document intends to be read through the Explorer the application program branching unit is implemented as an extension module by using a Shell execute hook interface IShellExecuteHook among Shell interfaces provided by MS Windows .

The Shell execute hook interface is an interface provided to generate an event when a program is executed through a Windows Shell Explorer Desktop etc. so that a developer may add a function and this is one of Windows Shell extension functions that transfers detailed information of a program execution command to an extension module that implements IShellExecuteHook when a program execution request is made through the Explorer Desktop or system menu and the extension module queries changes or cancels the execution information according to the purpose so that the program may be executed or its execution may be canceled according to the developer s intention.

In the meanwhile the application program branching unit monitors the file input output of the web browser using an API Hooking technology when a document attached to a web page intends to be read through the web browser and determines the type of the document to implement a module to execute the application program in the designated OS region when an event occurs that intends to read the document file attached to the web page.

Accordingly the application program branching unit includes a Shell execute hook extension module for reading a document through the Explorer and an API Hooking module for reading a document through the web browser.

The IPC interface enables communication to be done between application program processes that are executed in the actual OS region and the virtual OS region respectively according to the type of the document. Accordingly functions such as Copy Paste may be used for editing a document between the application program processes that are executed in the actual OS region and the virtual OS region respectively through the IPC interface .

The IPC interface may be implemented through a clipboard a shared memory a Windows socket a synchronization object and the like.

Although it has been assumed in that only the application programs that is not subjected to a branch are executed or general documents or encrypted documents of DRM vendor A are executed in the actual OS region as they are and encrypted documents of DRM vendor B are executed in the virtual OS region the OS region where each of them is to be executed may be arbitrarily varied according to the branch process information .

Referring to firstly the virtual OS managing unit separates the kernel of the actual operating system of the PC according to the OS partitioning method to generate the virtual operating system S . At this time it is preferred that the virtual operating system is generated upon a boot of the PC or at the appropriate time similar to this.

In the meanwhile although the number of the virtual operating systems to be generated is not particularly restricted it is preferred to correspond to the number of the DRM clients that are additionally installed in the PC. For instance it is preferred to generate two virtual operating systems so that there are provided one actual operating system and two virtual operating systems if three different DRM clients are installed in the PC.

If an event is generated that intends to read a document through the Explorer after the virtual operating system has been generated for example by double clicking on the document or selecting and entering the document S a path of the document and an application program to be executed are transferred to the Shell execute hook extension module of the application program branching unit S .

The Shell execute hook extension module queries for the branch process information of the document to determine which type the document belongs to for example a general document an encrypted document of DRM vendor A and an encrypted document of DRM vendor B S .

The branch process information which is managed by the branch process information managing unit includes a branch object application program a document type and execution OS region information. The branch process information is defined in XML and encrypted for management.

If the application program that is not subjected to a branch is executed or the document is a general document or encrypted document of DRM vendor A as the result of determination the application program is executed in the actual operating system as it is S . Accordingly the application program is executed in the actual OS region to open the document.

If the document is an encrypted document of DRM vendor B as the result of determination the Shell execute hook extension module interrupts the application program to be executed in the region of the actual operating system and executes a command that enables the document to be opened through the application program in the region of the virtual operating system and therefore the application program is executed in the region of the virtual operating system to open the document S .

In the meanwhile communication may be made through the IPC interface between the application program processes that are executed in the actual OS region and the virtual OS region respectively according to the type of the document S . Accordingly functions such as Copy Paste may be used for editing a document between the application program processes that are executed in the actual OS region and the virtual OS region respectively.

The IPC interface may be implemented through the clipboard the shared memory the Windows socket the synchronization socket and the like.

Referring to firstly the virtual OS managing unit separates the kernel of the actual operating system of the PC according to the OS partitioning method to generate the virtual operating system S . At this time it is preferred that the virtual operating system is generated upon a boot of the PC or at the appropriate time similar to this.

In the meanwhile although the number of the virtual operating systems to be generated is not particularly restricted it is preferred to correspond to the number of the DRM clients that are additionally installed in the PC. For instance it is preferred to generate two virtual operating systems so that there are provided one actual operating system and two virtual operating systems if three different DRM clients are installed in the PC.

If an event is generated that intends to read a document attached to the web browser through the web browser after the virtual operating system has been generated S the API Hooking module of the application program branching unit that operates over the web browser detects the path of the document and an application program to be executed S .

The API Hooking module queries for the branch process information of the document to determine which type the document belongs to for example a general document an encrypted document of DRM vendor A and an encrypted document of DRM vendor B S .

The branch process information which is managed by the branch process information managing unit includes a branch object application program a document type and execution OS region information. The branch process information is defined in XML and encrypted for management.

If the application program that is not subjected to a branch is executed or the document is a general document or encrypted document of DRM vendor A as the result of determination the application program is executed in the actual operating system as it is S . Accordingly the application program is executed in the actual OS region to open the document.

If the document is an encrypted document of DRM vendor Bas the result of determination the API Hooking module interrupts the application program to be executed in the region of the actual operating system and executes a command that enables the document to be opened through the application program in the region of the virtual operating system and therefore the application program is executed in the region of the virtual operating system to open the document S .

In the meanwhile communication may be made through the IPC interface between the application program processes that are executed in the actual OS region and the virtual OS region respectively according to the type of the document S . Accordingly functions such as Copy Paste may be used for editing a document between the application program processes that are executed in the actual OS region and the virtual OS region respectively.

The IPC interface may be implemented through the clipboard the shared memory the Windows socket the synchronization object and the like.

