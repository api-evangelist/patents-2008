---

title: Apparatus and method for monitoring and protecting system resources from web browser
abstract: An apparatus and method for preventing an attempt to perform malicious activities using web browser weaknesses are provided. A file protection module monitors attempts to access at least one file resource when the web browser executes a program, and allows or denies access. A registry protection module monitors attempts to access at least one registry resource when the web browser executes a program, and allows or denies access. A process protection module monitors attempts to execute or terminate at least one process when the web browser executes a program, and allows or denies the execution or termination.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08336097&OS=08336097&RS=08336097
owner: Electronics and Telecommunications Research Institute
number: 08336097
owner_city: Daejeon
owner_country: KR
publication_date: 20080911
---
This application claims priority to and the benefit of Korean Patent Application No. 2007 103038 filed Oct. 12 2007 and Korean Patent Application No. 2008 47443 filed May 22 2008 the disclosure of which is incorporated herein by reference in its entirety.

The present invention relates to a web browser execution system and more particularly to an apparatus and method for monitoring and protecting system resources from a web browser by preventing malicious activities through the web browser.

In general a web browser is software for enabling a user computer to access the Internet and read various information or web pages acquired from a web server and includes plug in programs operating in the web browser such as ActiveX Control.

Access to only system resources of a very limited region is basically allowed such that important system resources are not destroyed or exposed according to a web page creator s intentions when processing a web page in the web browser.

Here the system resources accessed by the web browser are present in a computer device to be executed by the web browser and refer to files containing various types of information registries and the like.

On the other hand some of various plug in programs like ActiveX Control to be executed in the web browser are allowed to access system resources for web page processing.

In particular like other general application programs ActiveX Control can access system resources without any limitations.

For this reason attempts by malicious users to perform malicious activities using weaknesses of the plug in program such as ActiveX Control or the web browser are rapidly increasing.

The weaknesses of the web browser including the plug in program such as ActiveX Control are as follows.

First there may be a problem concerning file write for newly generating a malicious file in the system or maliciously updating or deleting existing file content.

Second there may be a problem concerning file read for unlawfully reading and leaking file content stored in the system.

Third there may be a problem concerning registry write for newly generating a registry key and value in the system or maliciously changing or deleting a basic registry key and value.

Fourth there may be a problem concerning registry read for unlawfully reading and leaking a registry key value stored in the system.

Fifth there may be a problem concerning process execution for unlawfully executing a file stored in the system.

Sixth there may be a problem concerning process termination for terminating an arbitrary ongoing process in the system.

The present invention provides an apparatus and method for preventing an attempt to perform malicious activities using web browser weaknesses.

According to an aspect of the present invention there is provided an apparatus for monitoring and protecting system resources from a web browser including a file protection module that monitors attempts to access at least one file resource when the web browser executes a program and allows or denies access a registry protection module that monitors attempts to access at least one registry resource when the web browser executes a program and allows or denies access and a process protection module that monitors attempts to execute or terminate at least one process when the web browser executes a program and allows or denies the execution or termination.

According to another aspect of the present invention there is provided a method for monitoring and protecting system resources from a web browser including monitoring attempts to access at least one file resource when the web browser executes a program determining when the web browser attempts to access the at least one file resource whether the at least one file resource is listed in one of a basically allowed denied file resource list a user s allowed denied file resource list and an always execute list and allowing or denying the web browser access to the at least one file resource according to the determination.

According to still another aspect of the present invention there is provided a method for monitoring and protecting system resources from a web browser including monitoring attempts to access at least one registry resource for program execution by the web browser determining when the web browser attempts to access the at least one registry resource whether the at least one registry resource is listed in one of a basically allowed denied registry resource list a user s allowed denied registry resource list and an always execute list and allowing or denying the web browser access to the at least one registry resource according to the determination.

According to yet another aspect of the present invention there is provided a method for monitoring and protecting system resources from a web browser including monitoring attempts to execute or terminate at least one process for program execution by the web browser determining when the web browser attempts to execute or terminate the at least one process whether the at least one process is listed in one of a basically allowed denied process list a user s allowed denied process list and an always execute list and allowing or denying the web browser execution or termination of the at least one process according to the determination.

Exemplary embodiments of the present invention will be described in detail below with reference to the accompanying drawings. Throughout the drawings the same or similar elements are consistently denoted by the same reference numerals. Descriptions of functions and constructions that are well known by those of ordinary skill in the art are omitted for clarity and conciseness.

Hereinafter a system for reading a web page through a web browser according to an exemplary embodiment of the present invention will be described with reference to .

Referring to a web browser includes a plug in program such as ActiveX Control or the like and accesses at least one file resource for performing a file write read.

The web browser accesses at least one file resource for performing the file write read and accesses at least one system resource for managing process execution termination .

An apparatus for monitoring and protecting system resources from the web browser monitors whether the web browser accesses at least one system resource and performs a function for allowing or disallowing the web browser to access at least one system resource.

The apparatus monitors whether the web browser executes or terminates at least one process and performs a function for allowing or disallowing the web browser to execute or terminate the process.

Here the apparatus can operate inside or outside the web browser and perform a function for monitoring whether the web browser accesses system resources or allowing or disallowing the web browser to access the system resources using conventional techniques such as an application programming interface API hooking technique and the like.

In the exemplary embodiment of the present invention an example in which the apparatus uses the API hooking technique has been described. Of course any technique capable of intercepting an execution flow of a function called by the web browser to access system resources is applicable within the technical scope of the present invention.

Referring to the apparatus includes a file protection module for managing access to the at least one file resource such that the web browser performs the file read write a registry protection module for managing access to at least one registry resource such that the web browser performs the registry read write and a process protection module for managing the process execution termination such that the web browser executes terminates at least one process.

The file protection module includes a file access supervisor a file access blocker a basically allowed denied file list and a user s allowed denied file list .

Here the file access supervisor acquires file resource information by intercepting functions called to access file resources from the web browser and provides the acquired file resource information to the file access blocker .

When the file resource information is received from the file access supervisor the file access blocker determines whether the received file resource information is listed in one of the basically allowed denied file list and the user s allowed denied file list .

When the corresponding file resource information is listed in either one of the basically allowed denied file list and the user s allowed denied file list the file access blocker allows or disallows the web browser to access the corresponding file resource information.

The basically allowed denied file list includes a basically allowed file list and a basically denied file list. The basically allowed file list includes files and folders of Temporary Internet Files Favorites Cookies and the like to which access is allowed in order for the web browser to operate normally.

The basically denied file list includes files and folders of Start Program and the like to which access by the web browser is denied for security reasons.

The user s allowed denied file list includes the user s allowed file list and the user s denied file list and includes file and folder information explicitly or implicitly added by the user for allowing or denying access by the web browser .

The registry protection module includes a registry access supervisor a registry access blocker a basically allowed denied registry list and the user s allowed denied registry list .

The registry access supervisor acquires registry information by intercepting functions called to access registry resources by the web browser and provides the acquired registry resource information to the registry access blocker .

When the registry information is received from the registry access supervisor the registry access blocker determines whether the received registry information is listed in one of the basically allowed denied registry list and the user s allowed denied registry list .

When the corresponding registry information is listed in either one of the basically allowed denied registry list and the user s allowed denied registry list the registry access blocker allows or disallows the web browser to access corresponding registry resources.

The basically allowed denied registry list includes a basically allowed registry list and a basically denied registry list. The basically allowed registry list includes registries to which access is allowed in order for the web browser to operate normally.

The basically denied registry list includes registries to which access by the web browser is denied for security reasons. At this time the registries included in the basically denied registry list can be HKLM SOFTWARE Microsoft Windows CurrentVersion run HKLM SOFTWARE Microsoft Windows CurrentVersion RunServices HKLM SOFTWARE Microsoft Windows CurrentVersion RunOnce HKCU SOFTWARE Microsoft Windows CurrentVersion Run and HKCU SOFTWARE Microsoft Windows CurrentVersion Runonce .

The user s allowed denied registry list includes the user s allowed registry list and the user s denied registry list and includes registry information explicitly or implicitly added by the user for allowing or denying access by the web browser .

The process protection module includes a process access supervisor a process access blocker a basically allowed denied process list and the user s allowed denied process list .

The process access supervisor acquires process information by intercepting functions called for process execution by the web browser and provides the acquired process information to the process access blocker .

When the process information is received from the process access supervisor the process access blocker determines whether the received process information is listed in one of the basically allowed denied process list and the user s allowed denied process list .

When the corresponding process information is listed in either one of the basically allowed denied process list and the user s allowed denied process list the process access blocker allows or disallows the web browser to execute or terminate a corresponding process.

The basically allowed denied process list includes a basically allowed process list and a basically denied process list. The basically allowed process list includes processes to which access is allowed in order for the web browser to operate normally.

Here the processes listed in the basically allowed process list include a process of notpad.exe and the like to be executed when the user views a source of the web browser and the like.

The basically denied process list includes processes to which access by the web browser is denied for security reasons.

Here the basically denied process list is frequently used to prevent malicious activities and includes cmd.exe mshta.exe and the like which are not substantially needed for normal use of the web browser .

The user s allowed denied process list includes the user s allowed process list and the user s denied process list and includes process information explicitly or implicitly added by the user for allowing or denying access by the web browser .

Next a method for preventing malicious activities using the apparatus for monitoring and protecting system resources from the web browser according to an exemplary embodiment of the present invention will be described in detail with reference to .

Referring to when the web browser attempts to access a system resource in order to process a web page upon visiting the web page the apparatus detects the access attempt in step and goes to step .

In step the apparatus identifies information of the system resource that the web browser is attempting to access.

Here the system resource can be one of the file resource the registry resource and the process execution termination .

When identifying the system resource that the web browser is attempting to access in step the apparatus determines whether the system resource is listed in a basically allowed system list in step .

Here the basically allowed system list can be one of the basically allowed file list the basically allowed registry list and the basically allowed process list . When the system resource that the web browser is attempting to access is the file resource in step the basically allowed system list can be the basically allowed file list . In the case of the registry resource the basically allowed system list can be the basically allowed registry list . When process execution termination is detected the basically allowed system list can be the basically allowed process list .

Upon determining that the system resource that the web browser is attempting to access is listed in the basically allowed system list in step the apparatus goes to step .

Upon determining that the system resource that the web browser is attempting to access is not listed in the basically allowed system list in step the apparatus goes to step .

In step the apparatus determines whether the system resource that the web browser is attempting to access is listed in a basically denied system list.

Here the basically denied system list can be one of the basically denied file list the basically denied registry list and the basically denied process list . When the system resource that the web browser is attempting to access is the file resource the basically denied system list can be the basically denied file list . In the case of the registry resource the basically denied system list can be the basically denied registry list . When the process execution termination is detected the basically denied system list can be the basically denied process list .

Upon determining that the system resource that the web browser is attempting to access is listed in the basically denied system list in step the apparatus goes to step .

In step the apparatus disallows the web browser to access the corresponding system resource and notifies the user that access by the web browser to the corresponding system resource is denied by displaying an access denied message as shown in .

Upon determining that the system resource that the web browser is attempting to access is not listed in the basically denied system list in step the apparatus goes to step .

In step the apparatus determines whether the system resource that the web browser is attempting to access is listed in the user s allowed system list.

Here the user s allowed system list can be one of the user s allowed file list the user s allowed registry list and the user s allowed process list . When the system resource that the web browser is attempting to access is the file resource the user s allowed system list can be the user s allowed file list . In the case of the registry resource the user s allowed system list can be the user s allowed registry list . When the process execution termination is detected the user s allowed system list can be the user s allowed process list .

Upon determining that the system resource that the web browser is attempting to access is listed in the user s allowed system list in step the apparatus goes to step to allow the web browser to access a corresponding system resource.

Upon determining that the system resource that the web browser is attempting to access is not listed in the user s allowed system list in step the apparatus goes to step .

In step the apparatus determines whether the system resource that the web browser is attempting to access is listed in the user s denied system list.

Here the user s denied system list can be one of the user s denied file list the user s denied registry list and the user s denied process list . When the system resource that the web browser is attempting to access is the file resource the user s denied system list can be the user s denied file list . In the case of the registry resource the user s denied system list can be the basically denied registry list . When process execution termination is detected the user s denied system list can be the user s denied process list .

Upon determining that the system resource that the web browser is attempting to access is listed in the user s denied system list in step the apparatus goes to step to deny the web browser access to the corresponding system resource.

Upon determining that the system resource that the web browser is attempting to access is not listed in the user s denied system list in step the apparatus goes to step to determine whether access to the corresponding system resource by the web browser is always allowed.

Upon determining that access to the corresponding system resource by the web browser is always allowed in step the apparatus goes to step to allow the web browser to access the corresponding system resource.

Upon determining that access to the corresponding system resource by the web browser is not always allowed in step the apparatus goes to step to display a message for specifying whether the web browser is allowed to access the system resource as shown in or .

First when the system resource is the file resource the apparatus displays a message for specifying whether the web browser is allowed to access the system resource as shown in in step .

Then the user selects one of Allow this time only Deny this time only Always allow Always deny Always allow folder and Always deny folder as shown in .

Here when the user selects Always allow or Always allow folder the apparatus determines it in step and goes to step to allow the web browser to access the file resource .

Then the apparatus adds a file or folder of the file resource that the web browser is attempting to access to the user s allowed file list and automatically allows the web browser to access the corresponding file resource .

However upon determining that the user has selected Always deny or Always deny folder in step the apparatus goes to step to disallow the web browser to access the file resource and add a file or folder of the file resource that the web browser is attempting to access to the user s denied file list . Thereafter when the web browser attempts to access the corresponding file resource access is automatically denied.

Upon determining that the user has selected Allow this time only in step the apparatus goes to step to allow the web browser to access the file resource .

Upon determining that the user has selected Deny this time only in step the apparatus goes to step to disallow the web browser to access the file resource .

On the other hand when the system resource is the registry resource the apparatus displays a message for identifying whether the web browser is allowed to access the registry resource as shown in in step .

Then the user selects one of Allow this time only Deny this time only Always allow Always deny Always allow key and Always deny key as shown in .

At this time when the user selects Always allow or Always allow key the apparatus determines it in step and goes to step to allow the web browser to access the registry resource .

Then the apparatus adds the registry resource or the registry key of the registry value that the web browser is attempting to access to the user s allowed registry list .

Thereafter when the web browser re attempts to access the corresponding registry resource the apparatus automatically allows the web browser to have access. Access to all lower registry keys and values within the added registry key is also automatically allowed.

However upon determining that the user has selected Always deny or Always deny key in step the apparatus goes to step to disallow the web browser to access the registry resource .

Then the apparatus adds the registry resource or the registry key of the registry value that the web browser is attempting to access to the user s denied registry list .

Thereafter when the web browser re attempts to access the corresponding registry resource the apparatus automatically disallows the web browser to have access. Access to all lower registry keys and values within the added registry key is also automatically denied.

Upon determining that the user has selected Allow this time only in step the apparatus goes to step to allow the web browser to access the registry resource .

Upon determining that the user has selected Deny this time only in step the apparatus goes to step to disallow the web browser to access the registry resource .

On the other hand upon determining that the web browser has attempted the process execution termination in step the apparatus displays a message for identifying whether a process is allowed as shown in .

The user selects one of Allow this time only Deny this time only Always allow and Always deny shown in .

At this time when the user selects Always allow the apparatus determines it in step and goes to step to allow the process execution termination of the web browser .

The apparatus adds a process that the web browser has attempted to execute terminate to the user s allowed process list . Thereafter the attempt by the web browser for the corresponding process execution termination is automatically allowed.

However upon determining that the user has selected Always deny in step the apparatus goes to step to deny the process execution termination of the web browser and adds a process that the web browser has attempted to execute terminate to the user s denied process list .

When the web browser re attempts the corresponding process execution termination the apparatus automatically denies the process execution termination of the web browser .

On the other hand upon determining that the user has selected Allow this time only in step the apparatus goes to step to allow the process execution termination of the web browser .

However upon determining that the user has selected Deny this time only in step the apparatus goes to step to deny the process execution termination of the web browser .

As described above the apparatus for monitoring and protecting system resources from a web browser according to exemplary embodiments of the present invention monitors attempts by the web browser to access system resources and allows or denies access to the system resources according to a preset process.

According to exemplary embodiments of the present invention access to system resources by the web browser is allowed or denied as desired by a user.

The present invention can prevent malicious activities through a web browser and safely operate a web browser system by monitoring web browser access to system resources and allowing web browser access to only predefined or user allowed system resources.

The present invention can prevent malicious activities using weaknesses of the web browser by monitoring and protecting system resources from the web browser.

Although exemplary embodiments of the present invention have been disclosed for illustrative purposes those skilled in the art will appreciate that various modifications additions and substitutions are possible without departing from the scope of the present invention. Therefore the present invention is not limited to the above described embodiments but is defined by the following claims along with their full scope of equivalents.

