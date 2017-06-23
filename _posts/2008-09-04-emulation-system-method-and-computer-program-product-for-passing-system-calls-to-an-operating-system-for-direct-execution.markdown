---

title: Emulation system, method, and computer program product for passing system calls to an operating system for direct execution
abstract: An emulation system, method, and computer program product are provided for passing system calls to an operating system for direct execution. In operation, a file is loaded into memory and instructions associated with the loaded file are emulated. Furthermore, system calls resulting from the emulation are identified. Still yet, at least a portion of the system calls are passed to an operating system for direct execution thereof. In addition, application programming interfaces are provided for external components to access, to monitor and to control the aforementioned system.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08290763&OS=08290763&RS=08290763
owner: McAfee, Inc.
number: 08290763
owner_city: Santa Clara
owner_country: US
publication_date: 20080904
---
The present invention relates to emulation systems and more particularly to emulating sample files for identifying unwanted behavior.

Malware authors compress and encrypt executable programs to obfuscate code of the malicious program and to evade detection from anti malware products. Malware authors also include code to prevent debugging and or code to prevent strict emulation. These techniques force researchers to spend considerable time reverse engineering virus samples and to understand their behavior. There is thus a need for overcoming these and or other issues.

An emulation system method and computer program product are provided for passing system calls to an operating system for direct execution. In operation a file is loaded into memory. Additionally instructions associated with the loaded file are emulated. Furthermore system calls resulting from the emulation are identified. Still yet at least a portion of the system calls are passed to an operating system for direct execution thereof.

The file may include any file with associated instructions or that is capable of being executed. For example in various embodiments the file may include a suspicious executable file a new file to be tested an unknown file and or any other file that meets that meets the above definition. Once the file is loaded instructions associated with the loaded file are emulated. See operation .

The emulation may include emulating any instructions associated with the file. For example in one embodiment the emulation may include emulating regular instructions e.g. binary instructions etc. . As an option the emulation may include emulating instructions associated with sensitive system calls e.g. calls to read to write or to delete files directories registries etc. potentially harmful system calls e.g. calls to create to terminate or to compromise core system processes and services etc. and or any other system calls.

Furthermore system calls resulting from the emulation are identified. See operation . The system calls resulting from the emulation may include any system calls including sensitive system calls and potentially harmful system calls etc. In one embodiment the systems calls that are identified may include system calls with destination addresses outside a sample image associated with the emulation.

Still yet at least a portion of the system calls are passed to an operating system for direct execution thereof. See operation . In this case direct execution refers to execution of system calls by an operating system.

In one embodiment the at least a portion of the system calls may include system calls that are determined to be harmless based on the emulation. In another embodiment the at least a portion of the system calls may include system calls that are determined to be harmless based on a type of system call. For example system calls that do not involve accessing registries files or other sensitive system resources may be determined to be harmless system calls.

More illustrative information will now be set forth regarding various optional architectures and features with which the foregoing technique may or may not be implemented per the desires of the user. It should be strongly noted that the following information is set forth for illustrative purposes and should not be construed as limiting in any manner. Any of the following features may be optionally incorporated with or without the exclusion of other features described.

As shown a sandbox is provided. In the context of the present description a sandbox refers to any security mechanism or space for safely running programs or executing instructions. As an option the sandbox may include any components used to create an environment that mimics or replicates a system e.g. a host system etc. .

In this case the system may include a client or server system. Such server and or client may include any system capable of executing an application or instruction. For example in various embodiments the system may include a desktop computer lap top computer hand held computer mobile phone personal digital assistant PDA peripheral e.g. printer etc. any component of a computer and or any other type of logic.

As shown further in the sandbox includes a sandbox loader a sandbox emulator a sandbox system call and a sandbox quarantine system . It should be noted that in other embodiments the sandbox may include additional functionality including additional hardware and or logic. In one embodiment at least some of the various functionalities illustrated in may be combined.

In operation the sandbox loader is capable of loading a sandboxed sample file e.g. a suspicious executable etc. and performing initialization. The sandbox emulator may be utilized to emulate instructions e.g. binary instructions etc. and manage memory associated with the sandbox . The sandbox system call may be utilized to inspect all system calls initiated by the sample file .

Furthermore the sandbox system call may selectively emulate certain system calls e.g. sensitive system calls etc. and pass the remaining system calls e.g. non sensitive system calls etc. to an operating system e.g. a Windows operating system etc. for direct execution. The sandbox quarantine system may be utilized to capture and log all files and registries modified by the sample file . The sandbox quarantine system may also have access to a sandbox secure datastore for logging the captured files and or registries.

Additionally the sandbox may include one or more application programming interfaces API and or hooks that are capable of providing API and callback interfaces for external components to communicate with and or control the sandbox . For example the API and or hooks may allow a detection engine and point product to communicate with and or control the sandbox .

In one embodiment the system may utilize both emulators and native execution sandboxes. For example all regular instructions and sensitive system calls may be emulated by the sandbox . Additionally the non sensitive system calls may be passed to the operating system for direct execution.

In this way the sample file may be executed in a secure and realistic environment. Moreover because the sandbox is able to maintain complete control of the sample file instruction flows the sandbox is able to collect many more behavioral events than the number of events collected utilizing only a native execution sandbox.

As shown a sample file is loaded by a sandbox loader into memory. See operations . In this case an image of the sample file may be stored in memory. A virtual sandbox central processing unit CPU emulator then emulates the instructions included in the sample image in the same way that the sample image would be directly executed in an actual CPU utilized by an operating system for direct processing.

All system calls with destination addresses outside of the sample image may be handled by a sandbox system call emulator based on the nature of the system calls. See operation . For example sensitive and potentially harmful system calls may be captured emulated and overridden. See operation .

System calls related to a file and or a registry may be redirected to a sandbox quarantine system. See operation . The remaining harmless calls may then be passed to the underlying operating system for direct execution. See operation .

In this way the system calls may be classified into different categories and may be processed differently based on an associated category. For example it may be determined whether the system calls include system calls that are at least potentially harmful. In this case the potentially harmful system calls may be emulated and overridden and at least a portion of harmless system calls may be passed to the operating system for direct execution.

The results of the system calls may be identified and returned back to the CPU emulator to continue emulating. Additionally a sandbox quarantine system may capture all file and registry accesses and redirect the file registry modifications into a secured quarantine database. See operation .

As an example it may be determined whether the system calls include file system calls that are related to at least one file e.g. a file including a registry etc. . If it is determined that the system calls include file system calls the file system calls may be quarantined. Furthermore modifications associated with the file system calls may be stored in the quarantine database.

In one embodiment it may also be determined whether the sample file is safe. In this case the modifications may continue to be quarantined if it is determined that the file is not safe. Alternatively the modifications may be committed if it is determined that the file is safe.

For instance the sandbox may capture and redirect all file and registry modifications to the separate secure storage. In this case the quarantine operations may be transparent to the sandboxed sample such that the sample will continue to run as if it were being directly executed in a non virtual system. Thus a host machine will be safe because the file and registry modifications have been redirected to secure storages.

Additionally the quarantined files and registries may be scanned by anti virus software or other security software for known threads. Furthermore if the sample file is determined to be malicious the quarantined files and registries may be easily reverted by removing the quarantine storage. On the other hand if the sample is later determined to be clean the file and registry modifications may be committed into the host system and the sample may be released from the sandbox.

It should be noted that multiple samples may be sandboxed concurrently and quarantined into different quarantine storages without interfering with each other. As an option the functionality and behavior of the sandbox may be extended by a sandbox API layer which provides the programming interfaces for external applications e.g. anti virus and behavioral engines point products etc. to monitor control and intervene the sample file emulation process. For example an interface may be utilized for providing access to the sandbox emulator.

Additionally an engine may be deployed to scan the sample memory image in the middle of execution. As another example a behavior detection engine may be utilized to model and classify run time behavior patterns based on various events generated by the sandbox e.g. system calls file and registry accesses long jumps exceptions etc. .

Furthermore in various embodiments additional functionality may be included with the sandbox. For example in one embodiment dynamic code guards driven by a sandbox API and data files may be provided. In this case the code guards may ensure that vital program code is not patched. Furthermore these code guards may perform and verify checksums on critical code sections. In another case buffer overflow exploits could be detected and blocked through bounds and memory integrity checking. As an option this functionality may be implemented by inspecting trace logs.

In another embodiment a user mode dataflow trace may be included for key presses and message loops. In this case the dataflow trace may identify DLLs and modules e.g. browser objects etc. that have experienced key presses. As an option this feature may utilize the sandbox emulator to trace and report which DLLs log key presses thereby providing a chain of custody audit.

In yet another embodiment robust change revision control may be included. In this case the revision control may allow the management of Internet sessions beyond wiping and resetting the quarantine folder. Thus the sandbox may be implemented as a component for behavior scanners. In this way the sandbox may allow revision if the behavior is not detected in time.

In still another embodiment a code trace may be implemented for network traffic registry access and file access. In another embodiment a close integration of anti virus and anti malware software may be implemented. In this case when detection occurs an anti virus engine may instruct the sandbox to revert to a previous clean state. Additionally when new processes or files are created the sandbox may inform the anti virus engine to scan the files.

As an option application level snapshot and rollback may be implemented. For example configuration data of an application may be saved between sessions. In this way the configuration may be used for rollback.

As another option the sandbox quarantine system and or quarantine folder may be encrypted. In this case the sandbox quarantine system and or quarantine folder may be encrypted utilizing any suitable encryption technology. For example in one embodiment Safeboot technology may be utilized to encrypt the sandbox quarantine system and or quarantine folder.

In one embodiment behavior of an application may be extended or limited via scripts. For example it is often desired to have different levels of access control depending on the situation. Table 1 illustrates an example of some different levels of access control in different situations.

As an option the different access levels illustrated in Table 1 may be controlled and customized utilizing a script for specific applications. The scripts may grant different access depending on the resource which is requested. For instance if the resource requested is outside the sandbox access may be denied.

Utilizing these techniques sandboxing of applications may be implemented to prevent identity theft and malware installations by redirecting file and registry operations to a secure managed environment. Furthermore the sandboxed application may run in this environment without modifying the host system. When malicious behavior is suspected or detected a user can wipe or roll back the environment to a previous snapshot or a known clean state.

Coupled to the networks are servers which are capable of communicating over the networks . Also coupled to the networks and the servers is a plurality of clients . Such servers and or clients may each include a desktop computer lap top computer hand held computer mobile phone personal digital assistant peripheral e.g. printer etc. any component of a computer and or any other type of logic. In order to facilitate communication among the networks at least one gateway is optionally coupled therebetween.

The workstation shown in includes a Random Access Memory RAM Read Only Memory ROM an adapter for connecting peripheral devices such as disk storage units to the bus a user interface adapter for connecting a keyboard a mouse a speaker a microphone and or other user interface devices such as a touch screen not shown to the bus communication adapter for connecting the workstation to a communication network e.g. a data processing network and a display adapter for connecting the bus to a display device .

The workstation may have resident thereon any desired operating system. It will be appreciated that an embodiment may also be implemented on platforms and operating systems other than those mentioned. One embodiment may be written using JAVA C and or C language or other programming languages along with an object oriented programming methodology. Object oriented programming OOP has become increasingly used to develop complex applications.

Of course the various embodiments set forth herein may be implemented utilizing hardware software or any desired combination thereof. For that matter any type of logic may be utilized which is capable of implementing the various functionality set forth above.

While various embodiments have been described above it should be understood that they have been presented by way of example only and not limitation. Thus the breadth and scope of a preferred embodiment should not be limited by any of the above described exemplary embodiments but should be defined only in accordance with the following claims and their equivalents.

