---

title: Access control decision system, access control enforcing system, and security policy
abstract: An access control enforcing system, method, and computer-readable storage medium, the system including an access control enforcing part enforcing an access control for subject information based on access control information, the access control information indicating a control of an access to the subject information in accordance with a security policy. The security policy regulates an access permit to the subject information, a requirement enforced when the access is allowed, and supplement information indicating character information or image information used to enforce the requirement. The access control enforcing part further includes a requirement capability determining part determining whether or not the requirement to execute the access can be executed, the requirement indicated by the access control information. The access control is enforced for the subject information based on a determination result by the requirement capability determining part to satisfy the requirement, by using the supplement information.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08302205&OS=08302205&RS=08302205
owner: Ricoh Company, Ltd.
number: 08302205
owner_city: Tokyo
owner_country: JP
publication_date: 20081121
---
This application is a divisional application of Ser. No. 10 872 574 filed Jun. 22 2004 now abandoned the entire contents of which is incorporated herein by reference. U.S. Ser. No. 10 872 574 is based upon and claims benefit of priority from the prior Japanese Patent Application Numbers 2003 178033 filed on Jun. 23 2003 2003 315921 filed on Sep. 8 2003 and 2003 315996 filed on Sep. 8 2003.

The present invention generally relates to an access control decision system an access control enforcing system and a security policy in which an organizational security policy can be applied to an information processing system and an organizational security can be improved for not only digitalized documents but also a paper documents.

While office works have been digitalized in business importance of managing a digital document such as a confidential document has been increased. Thus recently an access control for the digital document is conducted in accordance with a predetermined security policy.

In a viewpoint in that the security for the digital document is secured by the security policy being uniformed over an organization a describing method of a security policy and an apparatus for transmitting the security policy is proposed for example refer to Japanese Laid open Patent Application No. 2004 102907 . Moreover for example Japanese Laid open Patent Application No. 2004 094401 discloses a method for distributing the security policy and an apparatus for operating based on the security policy. Furthermore Japanese Patent Application No. 2002 299712 discloses a method and an apparatus for controlling printing a digital document by encrypting and decrypting the digital document in accordance with the security policy.

Moreover since a system which object to sell digital contents mainly such as music data image data and the likes has a problem similar to a company secret management similar technologies are applied to this system for example refer to Japanese Laid open Patent Application No. 8 263441 U.S. Pat. No. 5 715 403 Japanese Laid open Patent Application No. 8 263438 and U.S. Pat. No. 6 236 971 . In particular a system is provided in that a condition should be satisfied when digital data such as the music data the image data and the like which are called digital work relating to a copyright. A protocol is disclosed to confirm whether or not the condition for exercising a security is satisfied. By using this technology it can be realized to use the music data and the image data being distributed under a condition of a payment of referring to and printing the music and the image or a restriction of a term of using without any charge.

However these inventions described above do not take the company secret management at an office into account but do aim at sales of the digital contents. Accordingly these inventions do not consider an access control including a printed matter output by copying the confidential document.

Furthermore a system for conducting various processes for a print for example refer to Japanese Laid open Patent Application No. 2000 122977 and U.S. Pat. No. 6 233 684 . For example Glyphe code can be embedded into a printed matter. However it is required to define information to be embedded for each document.

Furthermore for example Japanese Laid open Patent Application No. 2001 184264 FIG. 1 and FIG. 2 discloses an access control sub system configured by a policy evaluation module for determining an access allowed or not allowed in accordance with a policy an enforcement function verification module and an enforcement module.

However the above described conventional technologies have the following problems such as a lack of flexibility of an operation and a like 

cannot manage related persons for each document since the related persons are variously changed for each document in a case in that a policy regulates Available for Related Persons to Refer 

cannot flexibly correspond to various stamps such as a confidential stamp a top secret stamp an internal use only stamp and a like in a case in that the policy regulates Affix Confidential Stamp for Copy 

cannot change a warning message sentence in response to a type of a document in a case in that the policy regulates Warn Users to Handle with Care 

cannot restrict to use within a zone even if the policy defines the zone to be allowed zone to handle a document and

cannot regulate and enforce a process in a case in that a paper document cannot be identified even if the paper document should be identified to control an operation with respect to the paper document.

Even if these above problems are solved in order to uniformly conduct the access control in accordance with the organizational security policy it is desired to completely separate a part for determining the access control in accordance with the policy from various application systems to share the part for determining the access control with the various application systems and it is desired to separate the part for determining the access control from the part for actually enforcing the access control.

In addition the conventional technologies cannot control an access in accordance with an abstract description such as the organizational security policy.

It is a general object of the present invention to provide an access control decision system an access control enforcing system and a security policy in which the above mentioned problems are eliminated.

A more specific object of the present invention is to provide an access control decision system an access control enforcing system and a security policy in which an organizational security policy can be applied to an information processing system and securities can be secured for a paper document and a digital document.

The above objects of the present invention are achieved by an access control decision system including an abstraction converting part converting first information indicated by an access decision request into second information being abstract higher than the first information when the access decision request for requesting an access control decision for subject information to be accessed is received an access control decision part determining the access control for the subject information by referring a security policy being abstractly regulated based on the second information and a decision result sending part sending a decision result showing the access control for the subject information by said access control decision part to a request originator that sent the access decision request.

In the access control decision system according to the present invention information for determining the access control can be converted into information having abstraction degree similar to an organizational security policy. Accordingly it is possible to determine the access control in accordance with the security policy being abstract.

The above objects of the present invention are achieved by an access control enforcing system including an access control enforcing part enforcing an access control for subject information based on access control information indicating a control concerning an access to the subject information in accordance with a security policy wherein said access control enforcing part further includes a requirement capability determining part determining whether or not a requirement to execute the access can be executed the requirement indicated by the access control information and wherein the access control is enforced for the subject information based on a determination result by the requirement capability determining part so as to satisfy the requirement.

In the access control decision system according the present invention it is determined whether or not the requirement to allow the access to the subject information is executable in accordance with the security policy. Accordingly it is possible to enforce the access control for the subject information so as to satisfy the requirement.

The above objects of the present invention are achieved by a security policy comprising a rule description showing a rule regulating whether or not an operation is allowed based on a first security attribute of subject information directed to the operation and a second security attribute of a user requesting the operation for the subject information wherein the rule description regulates to allow the operation when a requirement is satisfied.

In the security policy according the present invention it is possible to regulate to allow the operation by executing the requirement.

The above objects of the present invention can be achieved by a program code for causing a computer to conduct processes described above in the document processing apparatus or by a computer readable recording medium recorded with the program code.

In the following an embodiment of the present invention according will be described with reference to the accompanying drawings.

A system applying an access control decision system according to an embodiment of the present invention is illustrated as shown in . is a diagram showing a configuration of a system according to the embodiment of the present invention. In the system shown in a security server for conducting an access control with respect to a digital document and a paper document is connected through a network to a document management system for managing digital documents a digital copier including a plurality of different image forming functions served as a copy a fax a scanner and a like and a document viewer for displaying the digital document at a client terminal of a user.

In the document viewer is a predetermined application running for the client terminal . The client terminal accesses a target document maintained in the document management system . The user may make copies of the paper document brought with the user by the digital copier . The system shown in may include a plurality of client terminals and users .

Hereinafter the digital document which is managed by the document management system and to which an access is controlled is referred to as a server document . The paper document which is copied by the digital copier is referred to as a paper document . The digital document which is downloaded from the document management system and stored in a local storage of the client terminal and opened and referred to by the document viewer is referred to as a portable document .

When the user connects to the document management system by using the client terminal and attempts to access to the server document the document management system obtains authentication information from the user and sends a request of a user authentication to the user management server . The document management system sends an access control decision request to the security server based on an authentication result received from the user management server . The document management system accesses the server document based on access control information received from the security server .

Similarly when the user copies the paper document by the digital copier the digital copier obtains the authentication information from the user and sends a request of the user authentication to the user management server . The digital copier sends the access control decision request to the security server based on the authentication result received from the user management server . The digital copier copies the paper document based on the access control information received from the security server .

Similarly when the user executes the document viewer at the client terminal and displays the portable document at the client terminal the document viewer obtains the authentication information from the user and sends the request of the user authentication to the user management server . The document viewer sends the access control decision request to the security server based on the authentication result received from the security server . The document viewer displays the portable document or further outputs the portable document displayed at the client terminal based on the access control information received form the security server .

When the user management server receives the authentication information of the user from the document management system the digital copier or the document viewer the user management server refers to a user management table and authenticates the user . The user management server sends the authentication result to the document management system the digital copier or the document viewer which sent the request of the user authentication.

The security server includes a policy file in that access control rules are described for an organization a user security level table for managing a user security for each user a document profile management table for managing a profile for each document a zone management table for managing the access control for each zone and a print profile management table for managing information concerning a print for each print. The security server corresponds to the access control requests from the document management system the digital copier and the document viewer by using a policy file and these tables through .

In the policy file a rule such as Access Allowed for Related Persons Only is regulated. However a relationship showing who is a related person for which document should be managed. A table complimenting this policy showing this rule is managed in the security server and separated from the policy. If this rule is described in the policy the policy becomes lack of versatility. That is a portion stipulating rule such as a company secret management regulation of the organization is stipulated as the policy and portions being variously set corresponding to each document and for each user are managed by tables. Since a different rule for each organization is managed in a form of the policy file a replacement of each rule becomes possible.

Hereinafter the server document the paper document and the portable document are generically called as a document .

A user who can be the client terminal or the user and accesses the document is called as an initiator .

The document management system the digital copier and the document viewer are generically called as an application system .

In the system the security server is separated from the user management server . However a function serving as the security server and a function serving as the user management server can be included in a single server computer.

An overview of the access control will be described with reference to showing an access control model described in accordance with ISO IEC 10181 3. is a block diagram showing the access control model.

In when the initiator sends an access request for accessing the document to the application system the application system sends a decision request to the security server to have the security server determined whether or not the access from the initiator is allowed after the user authentication. In particular in a case in that the user authentication is not required an access permit can be requested for an anonymous user or a guest user.

The security server determines in accordance with the access control rule policy described in the security file internally maintained in the security server whether or not the user as the initiator has the security to access the document that is whether the user is allowed or prohibited to access the document . If the user is allowed to access the document the security server determines a requirement that should be satisfied to access the document . Then the security server sends information showing that the user is allowed or not allowed and the requirement is satisfied or not as a decision result to the application system .

The application system receives the decision result and processes an access requested from the user if the user is allowed. In this case if the requirement is indicated the application system processes document so as to satisfy the requirement. If the user is not allowed or the requirement is not satisfied the application system denies this access to the document .

Next a hardware configuration and a functional configuration of the security server will be described with reference to and . is a block diagram showing the hardware configuration of the security server according to the embodiment of the present invention.

In the security server is a server computer and includes a CPU Central Processing Unit a memory unit a display unit an input unit a communication unit and a storage unit each of which is connected to a system bus B.

The CPU controls the security server in accordance with a program stored in the memory unit . The memory unit includes a RAM Random Access Memory and a ROM Read Only Memory and stores the program to be executed by the CPU data necessary to process by the CPU and data obtained in the process by the CPU . In addition the memory unit is partially used as a work area used in the process by the CPU .

The display unit displays necessary information by the control of the CPU . The communication unit is a unit to communicate with the application system when connecting to the application system for example through a LAN Local Area Network or a like. The storage unit includes a hardware unit and stores management tables including a policy file a user security level table a document profile management table a zone management table a print profile management table and the like.

The abstraction processing part includes a user security level mapping part a user category mapping part a zone mapping part and a document security attribute mapping part .

In the abstraction processing part when user identification information access type information document identification information and context information are received from the application system the user security level mapping part obtains an security level abstracted by referring to the user security level table based on the user identification information 1 the user category mapping part obtains a user category that is abstracted by referring to the document profile management table based on the user identification information and shows a related person or any person 2 the access type information is maintained without any change 3 the zone mapping part obtains a zone category that is abstracted by referring to the document profile management table and the zone management table based on the context information and shows in zone or out zone 4 and the document security attribute mapping part obtains a sensitivity level and a document category that are abstracted by referring to the document profile management table and the print profile management table based on the document identification information 5 .

In this embodiment a term may be set in the context information so as to obtain a term segment showing in term or out term.

The mapping parts through may be included in a single abstraction processing part. In this case this single abstraction processing part refers to more than one management table.

Alternatively the security level and the user category can be categorized into a user security attribute the sensitivity level and the document category can be categorized into the document security attribute and the zone category can be categorized into an access environment attribute so that three attributes are used to categorize. Accordingly an abstraction processing part may be provided for each attribute. In this case each abstraction processing part includes more than one mapping processing part and each mapping part refers to more than one table.

The policy base access control decision part receives information being abstracted by the abstraction processing part as a parameter and determines the access control in accordance with the access control rule policy described in the policy file . The policy file can be set from outside. Accordingly it is possible to easily change in response to the organizational security policy.

In this embodiment by processes in two steps of the abstraction processing part and the policy base access control decision part it is possible to determine the access control in accordance with general security policy and by flexibly corresponding to a change of the security policy.

In addition by providing the abstraction processing part it is not required to change a formation of information to provide to the application system when the security policy is changed. Since it is not required to change software for the application system in response to the change of the security policy maintenance in response to the change of the security policy can be easily conducted.

The access control can be conducted so as to allow or prohibit what type of an access for which user by managing an ACL Access Control List for each document. And there is a conventional system U.S. Pat. No. 6 289 450 in that this ACL is called a security policy. However in the conventional system since a policy is defined for each document there is a problem in that it is difficult to know that the security policy is applied in accordance with a company secret management regulation policy of an organization such as confidential matter is allowed only for related persons .

The security server according to the present invention and determining the access control first separates a general decision rule for the access control and a security setting for details of each document maps an attribute of a document or a user to an abstract security attribute and then makes an access decision. In addition since a general decision rule can be described as a policy file the rule is not fixed but becomes replaceable.

There may be one example in that the decision rule may be programmed as one logic in software. However There is no example in that the decision rule can be flexibly defined and set in accordance with the organizational security policy.

The userMap includes a user ID or a group ID shown by a character string by code showing String principalId a type of each entry a character string showing a user a group or a like by code showing String entryType a security level shown by a character string by code showing String levelId .

An entry of userMap for each user using the application system is created in UserMapList and the user is registered.

The docProfile includes an digital document ID shown by a character string by code showing String docId a document category shown by a character string by code showing String DocCategory a sensitivity level shown by a character string by code showing String docLevel a list of a plurality of related persons shown by an array of related persons shown by a character string by code showing String relatedPersons a list of a plurality of zone IDs shown by an array of zone IDs shown by a character string by code showing String zones a nondisclosure date shown by a date by code showing Date nondisclosure a retention date shown by a date by code showing Date retention and a validity date shown by a date by code showing Date validity .

An entry of the DocProfile for each digital document subject for the access control is created in the DocProfileTale and the digital document is registered. The document ID is information to identify each digital document. The document category and the sensitivity level indicates identification information of the document category and the sensitivity level used by the security policy.

User IDs or group IDs of related persons for the digital document are shown in the related person list. Zone IDs specifying zones where an access to the digital document is allowed are indicated in the zone ID list.

The ZoneInfo includes a zone ID shown by a character string by code showing String id a zone name shown by a character string by code showing String name and an address of the zone shown by an array of AddressInfo by codes showing AddressInfo addresses .

A data structure of the AddressInfo written in coded includes an IP address or a MAC address shown by a character string by code showing String address IP or MAC shown by a character string by code showing String addressType and a subnet mask shown by a character string such as 255.255.255.0 when IP address by code showing String netmask .

The zone management table is a table for managing zones allowing an access by a list of zone addresses. A plurality of IP addresses or MAC addresses are assigned to one zone ID.

The PrintProfile includes a print ID shown by a character string by code showing String printId a document ID of the digital document shown by a character string by code showing String docId a printed date shown by a date by code showing String printed UserId and a printed user name shown by a character string by code showing String printedUserName .

Each time the digital document under the access control is printed an entry of the PrintProfile is created and registered in the PrintProfileTable. The print ID is identification information to specify each print. The document ID is identification information showing a document being printed.

In the following a sequence of the access control will be described in detail. The document management system the digital copier and the document viewer will be described.

In and the document management system receives a user ID and a password of the user as well as a login request from the client terminal S .

The document management system sends a user authentication request with the user ID and the password received from the client terminal to the user management server S . The user management server conducts an authenticating process by the user ID and the password S . The user management server sends authentication result information showing a success or failure of the authentication to the document management system S . The authentication result information includes user identification information identifying a user and information showing the success or failure of the authentication.

The document management system conducts a process corresponding to the authentication result information S . When the authentication result information shows the success of the authentication the document management system sends the authentication result information received from the user management server to the client terminal and goes to S. On the other hand when the authentication result information shows the failure of the authentication the documents management system terminates the access control process.

The client terminal sends a document read request for the server document stored in the document management system to the document management system by indicating the document ID S .

The document management system sends the authentication result information of the user and document ID of the server document an access type and context information of the client terminal to the security server to request the access control for the server document S . For example the access type indicates a read access indicated by the document read request.

The security server determines whether or the access is allowed based on information being received S .

The security server sends a decision result to the document management system S . The document management system conducts a process corresponding to the decision result received from the security server S . When the decision result shows Allowed the document management system processes a requirement indicated by the decision result and advances to S. On the other hand when the decision result shows Not Allowed Prohibited the access is prohibited and the access control process is terminated S .

The document management system conducts a process corresponding to an access request sent from the client terminal sends the server document to the client terminal and normally terminates the access control process S .

The user authentication request in S can be sent through the security server . A method for authenticating the user is not limited to a method for authenticating by the user ID and the password. Alternatively a higher technical authentication such as a biometric authentication a challenge response authentication using a master card or a like can be applied.

Next the authenticating process conducted by the user management server will be described with reference to . is a diagram for explaining the authenticating process by the user management server according to the embodiment of the present invention. In the user management server checks the user ID and the password received from the document management system with the user management table to authenticate the user L .

It is checked whether or not the user is successfully authenticated L . When the user is successfully authenticated the user management server obtains a list of group IDs to which the user belongs L and creates the authentication result information by the user ID the user name and the list of group IDs L . The authentication result information includes user identification information identifying a user and information showing the success of the authentication.

The user management server sends the authentication result information to the document management system L and terminates a process conducted when the user is successfully authenticated L . Then the authenticating process is terminated L .

On the other hand when the user fails to be authenticated L the user management server creates the authentication result information showing the failure of the authentication and sends the authentication result information to the document management system L . a process for the failure of the authentication for the user is ended L and terminates the authenticating process L .

Next the decision process conducted by the security server in S will be described with reference to and . and are diagrams for explaining the decision process by the security server in response to a request from the document management system according to the embodiment of the present invention.

In and a process in which an operation for reading the server document of the document management system is conducted at the client terminal and a document read request is sent from the client terminal to the document management system is illustrated. For example there are a property refer an original refer an update a delete and a store as other operations at the client terminal and a property refer request an original refer request an update request a delete request and a store request are sent from the document management system to the security server respectively.

The original reference operation is an access for obtaining the server document being an original managed in the document management system . In addition the document read operation illustrated in through is an access for obtaining the server document which is converted so that only the document viewer being special can open the server document being original.

In the security server receives the authentication result information the document ID the access type the context information from the document management system conducting the decision request L . For example the access type indicates document read for the server document . A type of the document that is server document and a type of the operation that is document read are specified by the access type.

The security server obtains a document profile docProfile corresponding to the document ID docid received from the document management system from the document profile management table L .

The security server obtains the document category docCategory and the sensitivity level docLevel by referring to the document profile docProfile L .

The security server obtains the related persons list by referring to the document profile docProfile L .

The security server checks whether or not the related person list relatedPersons includes the user IDs userId or position groups groups of the authentication result information authInfo L .

When the related person list relatedPersons includes the user IDs userId or position groups groups of the authentication result information authInfo the security server indicates the related persons RELATED PERSONS to the user category userCategory L . On the other hand when the related person list relatedPersons does not include the user IDs userId or position groups groups of the authentication result information authInfo the security server indicates any person ANY to the user category userCategory L .

The security server refers to the user security level table UserMapTable and stores a level corresponding to the user ID or the group ID principalId to the security level userLevel L .

The security server obtains the zone ID list zones by referring to the document profile docProfile L .

The security server refers to the zone management table ZoneInfoTable obtains the IP address or the MAC address corresponding to the zone ID list zones and creates an allowed address list L .

The security server checks whether or not the address included in the context information is included in the allowed address list created in L L .

When the address is included in the allowed address list the security server sets restricted RESTRICTED to the zone zone L . On the other hand when the address is not included in the allowed address list the security server sets any zone ANY to the zone zone L .

The security server loads the security policy file to the memory unit and obtains an array of the access control rule rule L .

The security server repeats processes by the following L through L for each access control rule rule L .

The security server checks whether or not the document category docCategory of the access control rule shows not restricted ANY or corresponds to the document category docCategory of the document profile DocProfile and the document level docLevel of the access control rule rule shows not restricted ANY or corresponds to the document level docLevel of the document profile DocProfile L . When the document category docCategory of the access control rule rule shows not restricted ANY or corresponds to the document category docCategory of the document profile DocProfile and the document level docLevel of the access control rule rule corresponds to not restricted ANY or the document level docLevel of the document profile DocProfile the security server further repeats processes in the following L through L for each access control list Ace of the access control rule rule L .

On the other hand when the above condition is not satisfied L and L the security server goes back to L and repeats the above processes for a next access control rule rule .

When the above condition is satisfied the security server checks whether or not the user category userCategory of the access control list Ace corresponds to not restricted ANY or the user category userCategory set in L or L and the user level userLevel of the access control list Ace corresponds to not restricted ANY or the user level userLevel set in L and the zone zone corresponds to not restricted ANY or the zone zone set in L or L L L and L . When the user category userCategory of the access control list Ace corresponds to not restricted ANY or the user category userCategory set in L or L and the user level userLevel of the access control list Ace corresponds to not restricted ANY or the user level userLevel set in L and the user level userLevel of the access control list Ace corresponds to not restricted ANY or the user level userLevel set in L and the zone zone of the access control list Ace corresponds to not restricted ANY or the zone zone set in L or L the security server repeats the following L through L for each operation Operation of the access control list Ace L .

On the other hand when any one of conditions in L L and L is not satisfied L and L the security server goes back to L and repeats the above processes for a next access control list Ace of the access control rule rule .

When the conditions in L L and L are satisfied the security server checks whether or not an ID of the operation Operation.Id corresponds to an operation operation of the access control list Ace L . When the ID of the operation Operation.Id corresponds to an operation operation of the access control list Ace allowed true is stored to an allowed item of the decision result information decisionInfo L . In addition the security server stores all requirements requirement indicated by the operation operation to the decision result information L and advances to L L .

On the other hand when a condition in L is not satisfied L and L the security server goes back to L and repeats the above processes for a next operation Operation of the access control list Ace .

When the security server ends the process for each operation Operation of the access control list Ace the security server checks whether or not there is a respective operation Operation L . When there is no respective operation the security server stores not allowed false to the allowed item allowed of the decision result information decision Info and goes to L L .

When the security server ends the process in L for each access control list Ace of the access control rule rule security server checks whether or not there is a respective access control list Ace L . When there is no respective access control list Ace the security server stores not allowed false to the allowed item allowed of the decision result information decisionInfo L and advances to L L .

On the other hand when there is a respective access control list Ace the security server advances to L L .

In L when the process for each access control rule rule the security server checks whether or not there is a respective access control rule L . When there is no respective access control rule rule the security server stores not allowed false to the allowed item allowed of the decision result information decisionInfo L and advances to L. On the other hand when there is a respective access control rule rule the security server advances to L.

The security server checks whether or not the allowed item allowed of the decision result information decisionInfo shows not allowed false L . When the allowed item allowed of the decision result information decisionInfo shows not allowed false the security server sends the decision result information to the document management system which sent the decision request L and terminates the decision process L .

On the other hand when the allowed item allowed of the decision result information decisionInfo does not show not allowed false L the security server conducts a compensating process for requirements requirement included in the decision result information decisionInfo L sends the decision result information decisionInfo to the document management system that sent the decision request L and then terminates the decision process L .

A data structure of the context information which is sent from the document management system to the security server will be described with reference to . is a diagram showing the data structure of the context information according to the embodiment of the present invention.

In the context information is information showing an address of the client terminal used by the user . For example the data structure of the context information is defined by a structure ContextInfo and includes an IP address shown by a character string by code showing String ipAddress and a MAC address shown by a character string by code showing String macAddress .

The decision result information decisionInfo which is sent from the security server to the document management system will be described with reference to . is a diagram showing a data structure of the decision result information according to the embodiment of the present invention.

In the decision result information is information showing a decision result of the access control. For example the data structure of the decision result information is defined by a structure DecisionInfo and includes allowance information shown by true or false by code showing Boolean allowed and a plurality of requirements shown by an array of requirements by code showing Requirement requirements .

Moreover each requirement is defined by a structure Requirement and includes a requirement ID for identifying a requirement and being shown by a character string by code showing String requirement a plurality of sets of supplement information shown by an array of the supplement information by code showing Property supplements supplement data shown by an array of bytes by code showing Byte data and a plurality of alternative requirements shown by an array of the requirement by code showing Requirement alternatives .

The supplement information is defines by a structure Property and includes a name shown by a character string by code showing String name and a value shown by a character string by code showing String value .

Next the compensating process for requirements by the document management system will be described with reference to . is a flowchart for explaining the compensating process for requirements by the document management system according to the embodiment of the present invention.

In the document management system repeats from L to L for each set of the supplement information supplement included in the requirement requirement of the decision result information decisionInfo L .

The document management system checks whether or not the name name of a property Property of the supplement information indicates a static image static image L . When the static image static image is indicated the document management system reads out data of a stamp image file indicated in a value value of the property Property of the supplement information from a local hard disk storage unit stores the data of the stamp image file as supplement data of the requirement requirement L and advances to L.

On the other hand when the static image static image is not indicated the document management system advance to L.

The document management system checks whether or not a dynamic image dynamic image is indicated to the name name of the property Property of the supplement information and the operation operation shows print L . When the dynamic image dynamic image is set to the name name of the property Property of the supplement information and the operation operation shows print the document management system creates a new print profile printProfile L . Moreover the document management system encodes a print ID printId of the print profile printProfile to be identification image data L and stores the identification image data to supplement data data of the requirement requirement of the identification image data L . Then the document management system terminates the compensating process for the requirement.

On the other hand the dynamic image dynamic image is not indicated in the name name of the property property of the supplement information or the operation operation does not show print the document management system terminates the compensating process for the requirement.

Next the requirement process conducted by the document management system will be described with reference to and . and are flowcharts for explaining the requirement process according to the embodiment of the present invention.

In the document management system checks whether or not the allowed item allowed of the decision result information decisionInfo shows not allowed false L . When not allowed false is shown the document management system denies the access and terminates the requirement process L .

On the other hand when not allowed false is not shown the document management system repeats from L to L for each requirement requirement of the decision result information decisionInfo L .

The document management system checks whether or not a requirement requirement hereinafter referred to not supported requirement which is not supported by the document management system is indicated L . When the not supported requirement is not indicated the document management system advances to L.

On the other hand when the not supported requirement is indicated the document management system further checks whether or not the alternative requirement alternative of the not supported requirement requirement is an alternative requirement which is not supported hereinafter referred to not supported alternative requirement and is indicated L . When the not supported alternative requirement alternative for the not supported requirement requirement is indicated the document management system denies the access and terminates the requirement process L .

On the other hand when the not supported alternative requirement alternative for the not supported requirement requirement is not indicated the document management system processes the alternative requirement alternative of the not supported requirement requirement L .

Subsequently the document management system checks whether or not a log record record audit data is indicated in the requirement requirement L . When the log record record audit data is indicated the document management system generates log data including the user ID userId the document ID docid the operation operation date and time the context information contextInfo L .

Then the document management system sends the log data to security server L . The document management system checks whether or not the log data is successfully sent to the security server L . When the log data is failed to send the document management system denies the access and terminates the requirement process L . On the other hand when the log data is successfully sent to the security server the document management system advances to L.

Furthermore the document management system checks whether or not an encryption encryption is indicated to the requirement requirement L . When the encryption encryption is indicated the document management system encrypts the document stored therein L . On the other hand when the encryption encryption is not indicated the document management system advances to L.

Subsequently the document management system checks whether or not a protection of integrity of an original of the digital document is indicated in the requirement requirement L . When the protection of integrity of the original of the digital document is indicated the document management system transmits and stores the digital document to an original document integrity protection supporting system L . For example the original document integrity protection supporting system may be a system disclosed in Japanese Laid open Patent Application No. 2000 285024. Alternatively this original document integrity protection supporting system can be provided within the document management system .

On the other hand when the protection of the integrity of an original integrity protection is indicated in the requirement requirement the document management system advances to L.

Moreover the document management system checks whether or not the requirement requirement indicates to allow a multiple authentication multi authentication for an access to the digital document L . When the requirement requirement does not indicate to allow the multiple authentication multi authentication the document management system advances to L.

On the other hand when the requirement requirement indicates to allow the multiple authentication multi authentication the document management system requires for the user using the client terminal to conduct a strict user authentication such as a finger print recognition or a like L . After this strict user authentication the document management system checks whether or not the strict user authentication fails to authenticate the user L . When the strict user authentication fails the document management system denies the access and terminates the requirement process L . On the other hand when the strict user authentication succeeds to authenticate the user the document management system advances to L.

Subsequently the document management system checks whether or not the requirement requirement indicates a version management versioning of the digital document L . When the version management versioning is indicated the document management system stores a revised document as a new version L and advances to L.

Moreover the document management system checks whether or not the requirement requirement indicates a complete deletion of the digital document L . When the complete deletion is indicated the document management system executes a complete deleting process with respect to the digital document being deleted L and advances to L. On the other hand when the complete deletion is not indicated the document management system advances to L.

Subsequently the document management system checks whether or not the requirement requirement indicates an alarm display show alarm L . When the alarm display show alarm is indicated the document management system creates an alarm character string in a character string format indicated in the supplement information supplement of the requirement requirement L and displays the alarm character string by a dialog box to the user L . Then the document management system goes back to L to repeat the above same processes for a next requirement requirement . On the other hand when the alarm display show alarm is not indicated the document management system advances to L.

After the above processes are conducted for all requirements requirement the document management system conducts an access process requested from the client terminal L and terminates the requirement process L .

As described with reference to and the requirements requirement of the decision result information decisionInfo are processed in parallel. However since requirements requirement to be processed are defined for each operation operation it is not required to process all requirements requirement . For example the complete deletion complete deletion of the digital document is indicated only for the server document . For the sake of convenience the above processes are illustrated in and . The document management system conducts the above same processes for the alternative requirement.

As described above the document management system can conduct the access control in accordance with the security policy set in the security server . In this case it is possible to apply an allowable requirement regulated by the security policy. Moreover by including the processes for the supplement information and alternative requirement necessary to satisfy the allowable requirement the requirement process can be flexibly required.

In and the digital copier receives the login request with the user ID and the password from the user S .

The digital copier sends the user ID and the password received from the user to the user management server to make an authentication request S . The user management server conducts the authenticating process by the user ID and the password received from the digital copier S . The user management server sends authentication result information showing success or failure of the authentication to the digital copier S .

The digital copier conducts a process corresponding to the authentication result information S . When the authentication result information shows that the user is successfully authenticated the digital copier sends the authentication result information received from the user management server to the client terminal and advances to S. On the other hand when the authentication result information shows that the user is failed to authenticate the digital copier terminates the access control process.

When the digital copier receives the copy request for the paper document in order to identify the paper document the digital copier cuts out an area for identification from image data obtained by scanning the paper document S .

The authentication information of the user a cut out image the access type and the context information are sent to the security server to request the access control S . For example a copy access for the copy request is indicated as the access type.

The security server determines based on the information received from the digital copier whether the access is allowed or not allowed S . The security server sends a decision result to the digital copier S .

The digital copier conducts a process corresponding to the decision result received from the security server S . When the decision result shows Allowed the digital copier processes a requirement included in the decision result. On the other hand when the decision result shows Prohibited the digital copier terminates the access control process without any access.

The digital copier processes the access request copy request request by the user outputs sheets being copied and terminates the access control process S .

In this example a case in that the access request is the copy request is described. The same process can be conducted for a scan request a fax transmission request and a like. For example when the access request is the scan request image data being scanned is stored in a predetermined storage area. When the access request is the fax transmission request the image data being scanned are sent to a destination indicated by the user .

The user authentication request in S can be sent through the security server . A method for authenticating the user is not limited to a method for authenticating by the user ID and the password. Alternatively a higher technical authentication such as a biometric authentication a challenge response authentication using a master card or a like can be applied.

An authenticating process by the user management server in S is the same as the authenticating process in the access control of the document management system and then explanation thereof will be omitted. In addition a data structure of the authentication result information generated by the user management server is the same as the data structure in the access control of the document management system and then explanation thereof will be omitted.

The decision process conducted by the security server in S will be described with reference to and . and are diagrams for explaining the decision process in the security server in response to a request from the digital copier according to the embodiment of the present invention.

In and a case in which the user conducts the copy request to copy the paper document by the digital copier is illustrated. For example as other operations at the digital copier there are a fax transmission a scan and a like and respective requests are sent from the digital copier to the security system as a fax transmission request a scan request and a like are

An operation for the fax transmission is to send the paper document being scanned by the digital copier to a destination indicated by the user by fax. An operation for a scan is to scan the paper document and store image data in a predetermined storage area.

In the security server receives the authentication result information the document ID the access type the context information from the digital copier that sent the decision request L . For example copy for the paper document is indicated in the access type. A type of the document that is paper document and an type of operation that is copy are specified.

The security server obtains a print ID printId by decoding the cut out image received from the digital copier L .

The security server determines whether or not the cut out image can be decoded L . When the cut out image cannot be decoded the security server sets unknown UNKNOWN to the document category docCategory L sets unknown UNKNOWN to the document level docLevel L sets not restricted ANY to the user category userCategory L and sets not restricted ANY to the zone zone L .

On the other hand when the cut out image can be decoded the security server obtains a print profile printProfile corresponding to the print ID printId by referring to the print profile management table L .

The security server checks whether or not the print profile corresponding to the print ID exists L . When the respective print profile corresponding to the print ID does not exist the security server sets unknown UNKNOWN to the document category docCategory L sets unknown UNKNOWN to the document level docLevel L sets not restricted ANY to the user category userCategory L and sets not restricted ANY to the zone zone L .

On the other hand when the print profile corresponding to the print ID exists L the security server obtains the document ID docid from the print profile printProfile L obtains the document profile docProfile corresponding to the document ID docid by referring to the document profile management table L obtains the document category docCategory and the sensitivity level docLevel by referring to the document profile docProfile L and obtains the related person list relatedPersons by referring to the document profile docProfile L .

The security server further checks whether or not the related person list relatedPersons includes the user IDs userId or position groups groups of the authentication result information authInfo L . When the related person list relatedPersons includes the user IDs userId or position groups groups of the authentication result information authInfo the security server indicates the related persons RELATED PERSONS to the user category userCategory L . On the other hand when the related person list relatedPersons does not include the user IDs userId or position groups groups of the authentication result information authInfo the security server indicates any person ANY to the user category userCategory L and advances to L.

The security server obtains the zone ID list zones by referring to the document profile docProfile L . The security server refers to the zone management table ZoneInfoTable obtains the IP address or the MAC address corresponding to the zone ID list zones and creates an allowed address list L .

The security server checks whether or not the address included in the context information is included in the allowed address list created in L L . When the address is included in the allowed address list the security server sets restricted RESTRICTED to the zone zone L and advances to L. On the other hand when the address is not included in the allowed address list the security server sets any zone ANY to the zone zone L advances to L.

The security server refers to the user security level table UserMapTable and stores a level corresponding to the user ID userId or position groups groups to the user level userLevel l .

The security server loads the security policy file to the memory unit and obtains an array of the access control rule rule L .

The security server repeats processes by the following L through L for each access control rule rule L .

The security server checks whether or not the document category docCategory of the access control rule shows not restricted ANY or corresponds to the document category docCategory of the document profile DocProfile and the document level docLevel of the access control rule rule shows not restricted ANY or corresponds to the document level docLevel of the document profile DocProfile L and L . When the document category docCategory of the access control rule rule shows not restricted ANY or corresponds to the document category docCategory of the document profile DocProfile and the document level docLevel of the access control rule rule corresponds to not restricted ANY or the document level docLevel of the document profile DocProfile the security server further repeats processes in the following L through L for each access control list Ace of the access control rule rule L .

On the other hand when the above condition is not satisfied L and L the security server goes back to L and repeats the above processes for a next access control rule rule .

When the above condition is satisfied the security server checks whether or not the user category userCategory of the access control list Ace corresponds to not restricted ANY or the user category userCategory set in L or L and the user level userLevel of the access control list Ace corresponds to not restricted ANY or the user level userLevel set in L and the zone zone corresponds to not restricted ANY or the zone zone set in L or L L L and L . When the user category userCategory of the access control list Ace corresponds to not restricted ANY or the user category userCategory set in L or L and the user level userLevel of the access control list Ace corresponds to not restricted ANY or the user level userLevel set in L and the zone zone corresponds to not restricted ANY or the zone zone set in L or L the security server repeats the following L through L for each operation Operation of the access control list Ace L .

On the other hand when any one of conditions in L L and L is not satisfied L and L the security server goes back to L and repeats the above processes for a next access control list Ace of the access control rule rule .

When the conditions in L L and L are satisfied the security server checks whether or not an ID of the operation Operation.Id corresponds to an operation operation of the access control list Ace L . When the ID of the operation Operation.Id corresponds to an operation operation of the access control list Ace allowed true is stored to an allowed item of the decision result information decisionInfo L . In addition the security server stores all requirements requirement indicated by the operation operation to the decision result information L and advances to L L .

On the other hand when a condition in L is not satisfied L and L the security server goes back to L and repeats the above processes for a next operation Operation of the access control list Ace .

When the security server ends the process for each operation Operation of the access control list Ace in L the security server checks whether or not there is a respective operation Operation L . When there is no respective operation the security server stores not allowed false to the allowed item allowed of the decision result information decisionInfo L and goes to L L .

When the security server ends the process in L for each access control rule rule security server checks whether or not there is an access control rule rule L . When there is no respective access control rule rule the security server stores not allowed false to the allowed item allowed of the decision result information decisionInfo L and advances to L. On the other hand when there is a respective access control rule rule the security server advances to L.

The security server checks whether or not the allowed item allowed of the decision result information decisionInfo shows not allowed false L . When the allowed item allowed of the decision result information decisionInfo shows not allowed false the security server sends the decision result information to the digital copier which sent the decision request L and terminates the decision process L .

On the other hand when the allowed item allowed of the decision result information decisionInfo does not show not allowed false L the security server conducts a compensating process for requirements requirement included in the decision result information decisionInfo L sends the decision result information decisionInfo to the digital copier that sent the decision request L and then terminates the decision process L .

A data structure of the context information sent from the digital copier to the security server is the same as the data structure of the context information sent from the document management system to the security server and explanation thereof will be omitted.

A data structure of the decision result information sent from the security server to the digital copier is the same as the data structure of the decision result information sent from the security server to the document management system and explanation thereof will be omitted.

The compensating process of the requirement by the digital copier is the same as the compensating process for the requirement by the document management system and explanation thereof will be omitted.

Next the requirement process conducted by the digital copier will be described with reference to and . and are flowcharts for explaining the requirement process by the digital copier according to the embodiment of the present invention.

In the digital copier checks whether or not the allowed item allowed of the decision result information decisionInfo shows not allowed false L . When not allowed false is shown the digital copier denies the access and terminates the requirement process L .

On the other hand when not allowed false is not shown the digital copier repeats from L to L for each requirement requirement of the decision result information decisionInfo L .

The digital copier checks whether or not a requirement requirement hereinafter referred to not supported requirement which is not supported by the digital copier is indicated L . When the not supported requirement is not indicated the digital copier advances to L.

On the other hand when the not supported requirement is indicated the digital copier further checks whether or not the alternative requirement alternative of the not supported requirement requirement is an alternative requirement which is not supported hereinafter referred to not supported alternative requirement and is indicated L . When the not supported alternative requirement alternative for the not supported requirement requirement is indicated the digital copier denies the access and terminates the requirement process L .

On the other hand when the not supported alternative requirement alternative for the not supported requirement requirement is not indicated the digital copier processes the alternative requirement alternative of the not supported requirement requirement L .

Subsequently the digital copier checks whether or not a log record record audit data is indicated in the requirement requirement L . When the log record record audit data is indicated the digital copier generates log data including the user ID userId the document ID docid the operation operation date and time the context information contextInfo L .

Then the digital copier sends the log data to security server L . The digital copier checks whether or not the log data is successfully sent to the security server L . When the log data is failed to send the digital copier denies the access and terminates the requirement process L . On the other hand when the log data is successfully sent to the security server the digital copier advances to L.

Furthermore the digital copier checks whether or not a label print show label is indicated to the requirement L . When the label print show label is indicated the digital copier embeds a stamp image indicated by the supplement information supplement of the requirement by printing to a printed document L . On the other hand when the label print show label is not indicated the digital copier advances to L.

Subsequently the digital copier checks whether or not a user name print show operator is indicated L . When the user name print show operator is indicated the digital copier prints an operator name operator as the user name to a printed document L . On the other hand when the user name print show operator is not indicated the digital copier advances to L.

Moreover the digital copier checks whether or not a record of an image log record image data is indicated L . When the record of the image log record image data is indicated the digital copier generates image log data including the user ID userId the document ID docid the operation operation the date and time the context information contextInfo and document data scan data L . Subsequently the digital copier stores the image log data to an internal hard disk L On the other hand when the record of the image log record image data is not indicated the digital copier advances to L.

Subsequently the digital copier checks whether or not an alarm display show alarm is indicated L . When the alarm display show alarm is indicated the digital copier creates an alarm character string in a character string format indicated in the supplement information supplement of the requirement requirement L and displays the alarm character string at the operation panel to the user L . On the other hand when the alarm display show alarm is not indicated digital copier advances to L.

Furthermore the digital copier checks whether or not an alarm print print alarm is indicated L . When the alarm print print alarm is indicated the digital copier creates an alarm character string in a character string format indicated in the supplement information supplement of the requirement requirement L and prints the alarm character string to embody to the printed document L . On the other hand when the alarm print print alarm is not indicated the digital copier advances to L.

Subsequently the digital copier checks whether or not a receiver restriction address restriction for the fax transmission is indicated L . When the receiver restriction address restriction is indicated the digital copier checks a receiver address indicated by the user with a receiver condition indicated in the supplement information supplement of the requirement requirement L . Moreover the digital copier checks whether or not the receiver address matches with the receiver condition L . When the receiver address does not match with the receiver condition the digital copier displays at an operation panel a message showing that the receiver address does not match with the receiver condition to inform it to the user L denies the access by the user and terminates the requirement process L . On the other hand when the receiver address matches with the receiver condition the digital copier advances to L.

When the digital copier determines in L that the receiver restriction address restriction is not indicated the digital copier advances to L.

Moreover the digital copier decides whether or not a confidential transmission mode private send is indicated L . When the confidential transmission mode private send is indicated the digital copier sets the confidential transmission mode to a sender condition L . Then the digital copier checks whether or not the confidential transmission mode cannot be set L . When the confidential transmission mode cannot be set the digital copier displays at the operation panel a message showing that a receiver cannot receive the confidential transmission to inform it to the user L denies the access and terminates the requirement process L . On the other hand when the confidential transmission can be set the digital copier advances to L.

When the digital copier determines in L that the confidential transmission mode private send is not indicated the digital copier advances to L.

Subsequently the digital copier checks whether or not a visible watermark letter print visible watermark is indicated L . When the visible watermark letter print is indicated the digital copier creates a character string in a character string format indicated by the supplement information supplement of the requirement requirement L and embeds the character string as a watermark to the printed documents L . On the other hand when the visible watermark letter is not indicated the digital copier advances to L.

Furthermore the digital copier checks whether or not a digital watermark digital watermark is indicated L . When the digital watermark is indicated the digital copier creates a character string in a character string format indicated by the supplement supplement of the requirement requirement L and embeds the character string as the digital watermark to scanned data L . Then the digital copier goes back to L and repeats the above processes for a next requirement requirement . On the other hand when the digital watermark is not indicated the digital copier advances to L.

After the above process is conducted for all requirement requirement the digital copier conducts a process corresponding to the access by the client terminal L and terminates the requirement process L .

As described above the digital copier can conduct the access control in accordance with the security policy set in the security server . In this case it is possible to apply the allowable requirement regulated by the security policy. Moreover it is possible to process for the supplement information necessary to satisfy the allowable requirement and apply the process for the alternative requirement.

Since the recognition of the paper document is not perfect at 100 percent a recognition error may be occurred. When the digital copier cannot recognize the paper document when copying the paper document basically the paper document is required to be copied as a regular paper document. For this reason it is required to conduct some kind of security protection in a case in that the paper document cannot be recognized. Accordingly in this embodiment the paper document which is not recognized categorized into UNKNOWN of the document category can be processed in accordance with the security policy.

In and the document viewer receives an open request for opening a file portable document from the user S .

The document viewer checks whether or not the portable document is protected by a security S . The document viewer conducts a process corresponding to a check result in S protected or not protected for the portable document S . When the portable document is not protected the document viewer displays a content of the portable document and terminates the access control process. On the other hand when the portable document is protected the document viewer advances to S.

The document viewer prompts the user to input the user ID and the password and receives the user ID and the password from the user S .

The document viewer conducts a user authentication by sending the user ID and the password from the user to the user management server S .

The user management server conducts the user authentication by the user ID and the password received from the document viewer S and sends authentication result information to the document viewer S .

When the document viewer receives the authentication result information from the user management server the document viewer conducts a process corresponding to the authentication result information S . When the authentication is failed the document viewer displays an authentication error for the user and terminates the access control process. When the authentication is succeeded the document viewer advances to S.

The document viewer retrieves the document ID from the portable document S . Then the document viewer sends the authentication result information the document ID an access type context information for the client terminal on which the document viewer is running to the security server and requests the access control S . For example a read access is indicated as the access type for the open request.

The security server determines whether or not the access is allowed based on information received from the document viewer S . The security server sends a decision result to the document viewer S .

When the decision result shows allowed the document viewer processes a requirement included in the decision result S . When the decision result shows prohibited not allowed the document viewer denies the access and terminates the access control process.

The document viewer processes the access file open requested by the user displays the contents of the portable document S .

The document viewer sends the authentication result information the document ID the access type the context information of the client terminal on which the document viewer is running to the security server and requests the access control to the security server S . For example a print access corresponding to the print request is indicated as the access type.

The security server determines based on information received from the document viewer whether or not the access is allowed S and sends a decision result to the document viewer S .

When the decision result shows allowed the document viewer processes a requirement included in the decision result S . When the decision result shows prohibited not allowed the document viewer denies the access and terminates the access control process.

The document viewer processes the access print request by the user and outputs printed contents of the portable document S .

The user authentication in S may be requested through the security server . A method for authenticating the user is not limited to a method for authenticating by the user ID and the password. Alternatively a higher technical authentication such as a biometric authentication a challenge response authentication using a master card or a like can be applied.

An authenticating process conducted by the user management server in S is the same as the authenticating process in the access control conducted by the document management system and explanation thereof will be omitted. In addition a data structure of the authentication information in the access control conducted by the document management system and explanation thereof will be omitted.

An decision process conducted by the security server in S and S is the same as the decision process in the access control conducted by the document management system . In addition a data structure of the decision result information is the same as the data structure of the decision result information in the access control conducted by the document management system and explanation thereof will be omitted.

A compensating process for the requirement conducted by the document viewer is the same as the compensating process for the requirement conducted by the document management system and explanation thereof will be omitted.

Next a requirement process conducted by the document viewer will be described with reference to through . and are flowcharts for explaining the requirement process conducted the document viewer according to the embodiment of the present invention.

In the document viewer checks whether or not the allowed item of the decision result information shows false L . When the allowed item shows false the document viewer denies the access and terminates the requirement process L .

On the other hand when the allowed item does not show false the document viewer repeats L through L for each requirement indicated in the decision result information decisionInfo L .

The document viewer checks whether or not a requirement which is not supported by the document viewer hereinafter called not supported requirement is indicated L . When the not supported requirement is not indicated the document viewer advances to L.

On the other hand when the not supported requirement is indicated the document viewer further checks whether or not an alternative requirement which is not supported by the document viewer hereinafter called not supported alternative requirement is indicated L . When the not supported alternative requirement is indicated the document viewer denies the access and terminates the requirement process L .

On the other hand the not supported alternative requirement is not indicated the document viewer processes the alternative requirement alternative for the requirement requirement L 

Subsequently the document viewer checks whether or not a log record record audit data is indicated in the requirement requirement L . When the log record record audit data the document viewer generates log data including the user ID userId the document ID docid the operation operation date and time and the context information contextInfo L .

Then the document viewer sends the log data to the security server L . The document viewer determines whether or not the log data is successfully sent to the security server L . When the log data is failed to send the document viewer denies the access and terminates the requirement process L . On the other hand when the log data is successfully sent the document viewer advances to L.

Furthermore the document viewer checks whether or not the requirement indicates to allow the multiple authentication for the access to the digital document L . When the multiple authentication is indicated to allow the document viewer requires the user of a strict user authentication such as the finger print recognition or the like l . The document viewer further determines whether or not the strict user authentication is failed L . When the strict user authentication is failed the document viewer denies the access and terminates the requirement process L . On the other hand when the authentication is not indicated or when the string user authentication is succeeded the document viewer advances to L.

Subsequently the document viewer checks whether or not the alarm display show alarm is indicated L . When the alarm display is indicated the document viewer creates an alarm character string in a character string indicated in the supplement information supplement of the requirement requirement L and displays the alarm character string L . On the other hand when the alarm display is not indicated the document viewer advances to L.

Moreover the document viewer checks whether or not a private print mode private access is indicated L . When the private print mode is indicated the document viewer advances to L.

On the other hand the document viewer determines whether or not a printer to print out supports the private print mode L . When the private print mode is not supported the document viewer processes the alternative requirement alternative of the requirement requirement L . Then the document viewer determines whether or not the alternative requirement is processed L . When the alternative requirement cannot be processed the document viewer denies the access and terminates the requirement process L . On the other hand when the alternative requirement can be processed the document viewer advances to L.

On the other hand when the private print mode is supported L the document viewer displays a dialog for the user to input the password L sets the password input by the user to a printer driver in order to set the private print mode L . After that the document viewer advances to L.

Subsequently the document viewer checks whether or not the image log record record image data is indicated L . When the image log record is indicated the document viewer further determines whether or not the printer to print out supports the image log record L . When the printer does not support the image log record the document viewer processes the alternative requirement alternative of the requirement requirement L . Then the document viewer determines whether or not the alternative requirement cannot be processed L . when the alternative requirement cannot be processed the access is denied and the requirement process is terminated L . On the other hand when the alternative requirement alternative can be processed the document viewer advances to L.

On the other hand when the image log record is supported L the document viewer generates log data including the user ID userid the document ID docid the operation operation the date and time and the context information contextInfo L . The document viewer sets an image log bibliographic item to the printer driver L and sets an image log record mode to the printer driver L . Then the document viewer advances to L.

Moreover the document viewer checks whether or not the requirement indicates to embed trace information embed trace info L . When the requirement does not indicate to embed the trace information the document viewer advances to L.

When the requirement indicates to embed the trace information the document viewer further determines whether or not a driver of the printer to print out supports a stamp print L . When the driver of the printer supports the stamp print the document viewer sets a barcode image indicated by the supplement information of the requirement to the printer driver to set a stamp print mode L . Then the document viewer advances to L.

On the other hand when the driver of the printer to print out does not support the stamp print the document viewer further determines whether or not the document viewer supports a document edit L . When the document edit is supported the document viewer embeds the barcode indicated by the supplement information supplement of the requirement requirement to each page to be printed by editing the portable document L . On the other hand when the document edit is supported L the document viewer processes the alternative requirement alternative of the requirement requirement L . The document viewer determines whether or not the alternative requirement cannot be processed L . When the alternative requirement cannot be processed the document viewer denies the access and terminates the requirement process L . When the alternative requirement can be processed the document viewer advances to L.

Subsequently the document viewer checks whether or not the requirement indicates to print a label as a stamp show label L . When the requirement does not indicate to print a label as a stamp the document viewer advances to L. When the requirement indicates to print a label as a stamp the document viewer further checks whether or not the driver of the printer to print out supports the stamp print L . When the stamp print is supported the document viewer sets the stamp image indicated by the supplement requirement supplement of the requirement requirement to the printer driver to set the stamp print mode an embedding location is indicated by embedding location item in the supplement information supplement of the requirement requirement L . After that the document viewer advances to L.

On the other hand when the stamp print is not supported the document viewer determines whether or not the document viewer supports the document edit L . When the document edit is supported the document viewer sets the stamp image indicated by the supplement requirement supplement of the requirement requirement to the printer driver to set the stamp print mode an embedding location is indicated by embedding location item in the supplement information supplement of the requirement requirement L .

On the other hand when the document edit is supported the document viewer processes the alternative requirement alternative of the requirement requirement L . Then the document viewer determines whether or not the alternative requirement cannot be processed L . When the alternative requirement cannot be processed the document viewer denies the access and terminates the requirement process L . On the other hand the document viewer advances to L.

Furthermore the document viewer checks whether or not the visible watermark letter print visible watermark is indicated L . When the visible watermark letter print is not indicated the document viewer advances to L.

On the other hand when the visible watermark letter print is indicated the document viewer creates a background character string in a character string indicated by the supplement requirement supplement of the requirement requirement L . Then the document viewer further determines whether or not the driver of the printer to print out supports a combination print L . When the combination print is supported the document viewer sets the background character string as the combination character string to the printer driver L . After that the document viewer advances to L.

On the other hand when the driver of the printer to print out does not support the combination print the document viewer determines whether or not the documents viewer supports the document edit L . When the document edit is supported the document viewer embeds the background character string to a background of the portable document by editing the portable document L .

On the other hand when the document edit is not supported the document viewer processes the alternative requirement alternative of the requirement requirement L . Then the document viewer further determines whether or not the alternative requirement alternative cannot be processed L . When the alternative requirement alternative cannot be processed the document viewer denies the access and terminates the requirement process L . On the other hand when the alternative requirement can be processed the document viewer advances to L.

Subsequently the document viewer determines whether or not the requirement indicates to print an embossed watermark letter anti copy watermark L . When the requirement does not indicate to print the embossed watermark letter the document viewer advances to L.

On the other hand when the requirement indicates to print the embossed watermark letter the document viewer creates a pattern character string in a character string format indicated by the supplement information supplement of the requirement requirement L . The document viewer further determines whether or not the driver of the printer to print out supports a pattern print L . When the pattern print is indicated the document viewer sets the pattern character string to the printer driver L . After that the document viewer advances to L.

On the other hand when the pattern print is not supported the document viewer determines whether or not the document viewer supports the document edit L . When the document edit is supported the document viewer generates a pattern image based on the pattern character string L and embeds the pattern image to the background of the portable document by editing the portable document L .

On the other hand when the document edit is not supported L the document viewer processes the alternative requirement alternative of the requirement requirement L . Then the document viewer determines whether or not the alternative requirement cannot be processed L . When the alternative requirement cannot be processed the document viewer denies the access and terminates the requirement process l . On the other hand when the alternative requirement can be processed the document viewer advances to L.

Moreover the documents viewer determines whether or not the requirement indicates to print an identification pattern identifiable bg pattern L . When the requirement does not indicate to print an identification pattern the document viewer advances to L.

When the requirement indicates to print an identification pattern the document viewer creates the pattern character string by an identification pattern image indicated by the supplement information supplement of the requirement requirement L . Then the document viewer further determines whether or not the driver of the printer to print out supports to repeat the stamp print L . When the driver of the printer supports to repeat the stamp print the document viewer sets the identification pattern image indicated by the supplement information supplement of the requirement requirement to the printer driver to set a repeating stamp print mode L . After that the document viewer advances to L.

On the other hand when the driver of the printer does not support to repeat the stamp print the document viewer further determines whether or not the document viewer supports the document edit L . When the document edit is supported the document viewer repeatedly embeds the identification pattern image indicated by the supplement information supplement of the requirement requirement to the background of the portable document by editing the portable document L . After that the document viewer advances to L.

On the other hand when the document edit is not supported L the document viewer processes the alternative requirement alternative of the requirement requirement L . Then the document viewer determines whether or not the alternative requirement cannot be processed L . When the alternative requirement cannot be processed the document viewer denies the access and terminates the requirement process L . On the other hand when the alternative requirement can be processed the document viewer advances to L.

Subsequently the document viewer determines whether or not the alarm print is indicated L . When the alarm print is not indicated the document viewer goes back to L.

On the other hand when the alarm print is indicated the document viewer creates an alarm character string in a character string format indicated by the supplement information supplement of the requirement requirement L . Then the document viewer further whether or not the driver of the printer to print out supports a header footer print L . When the header footer print is supported the document viewer sets the alarm character string as a header footer to the printer driver L .

On the other hand when the header footer print is not supported the document viewer further determines whether or not the document viewer supports the document edit L . When the document edit is supported the document viewer embeds the alarm character string at the header footer of the portable document L .

On the other hand when the document edit is supported L the document viewer processes the alternative requirement alternative of the requirement requirement L . Then the document viewer further determines whether or not the alternative requirement cannot be processed L . When the alternative requirement cannot be processed the document viewer denies and terminates the requirement process L .

On the other hand when the alternative requirement can be processed the document viewer goes back to L to repeat the above same process for a next requirement requirement .

After the above process is conducted for all requirements requirement the document viewer conducts an access process requested by the user L and terminates the requirement process L .

As described above the document viewer can conduct the access control in accordance with the security policy set in the security server . In this case it is possible to apply the allowable requirement regulated in the security policy. In addition since the process for the supplement information necessary to satisfy the allowable requirement and the process for the alternative requirement can be conducted it is possible to realize a flexible process in accordance with the organizational security policy.

As described above even if the requirement can not be realized in the requirement process that determines whether or not the documents viewer supports the document edit it is possible to temporarily edit the contents of the portable document embed necessary information in the portable document and then conduct a process requested by the user .

It is required to encrypt the portable document so that the portable document can be opened only by using the document viewer that realize the access control as described above.

A key for using an encryption decryption may be included in a special document viewer that can realize the above access control. Only if it confirms that the document viewer is a special document viewer capable of enforcing the access control the security server allows transmitting a decryption key to the document viewer .

Accordingly it is possible to protect the portable document from being opened by a regular document viewer that cannot realize the access control.

As described above screen examples for displaying the document viewer at the client terminal will be described with reference to through . The user can know by screens described in the following which requirements will be processed.

Screen examples in a case in that the alarm print is indicated as the requirement will be described with reference to and . is a diagram showing a screen example for displaying settings for the alarm print according to the embodiment of the present invention. is a diagram showing a screen example for displaying detail settings for the alarm print according to the embodiment of the present invention.

In a screen is a screen showing a state in that the alarm print is indicated as the requirement. In the screen a setting area is originally used as an area for a setting to print at a header or footer. In a case in that the alarm print is processed as the requirement to conduct the print request the header footer print is compulsory set and displayed in gray to prohibit the user from changing the setting by the requirement process conducted by the document viewer .

When the user clicks a detail button in the setting area a screen as shown in is displayed at the client terminal .

In the screen is a screen for setting details in a case in that the alarm print is indicated as the requirement In the screen the setting are is originally used for user to set an arrangement location and a format of a character string to print at the header or the footer. In a case in that the alarm print is processed as the requirement to conduct the print request the header footer print is compulsory set and displayed in gray to prohibit the user from changing the setting by the requirement process conducted by the document viewer .

Accordingly the user is prohibited from changing the setting but can confirm that the alarm print is the requirement before printing the portable document . By this confirmation the user determines to actually execute to print the portable document or cancel to the print request.

Screen examples in a case in that the private print is indicated as the requirement will be described with reference to and . is a diagram showing a screen example in that the private print is set according to the embodiment of the present invention. is a diagram showing a screen example for setting the authentication information for the private print according to the embodiment of the present invention.

In a screen is a screen displayed when the private print is indicated as the requirement. In the screen a selecting area for selecting a print method is originally user for the user to select one or more items. In a case in that the private print is processed as the requirement to execute the print request of the user the requirement process conducted by the document viewer compulsory selects the private print display in gray and also controls the selection not to change by the user .

Accordingly the setting can be controlled so that the setting cannot be changed by the user . When the user clicks a detail button in the setting area a screen is displayed as shown in .

In the screen is a screen for detail settings in the case in that the private print is indicated as the requirement. In the screen input areas and are originally used for the user to set the authentication information. The input area is an area for the user to input the user ID and the input area is an area for the user to input the password. The user can output a document being printed from the portable document from the digital copier by inputting at the digital copier the user ID and the password input at the screen .

Accordingly the user is prohibited from changing the setting but can confirm that the stamp print is the requirement before the portable document is printed out. By this confirmation the user can determines to actually print the portable document or to cancel the print request.

Accordingly the user is prohibited from changing the setting but can confirm the visible watermark letter print is the requirement before the portable document is printed out. By this confirmation the user can determine to actually print out the portable document or to cancel the print request.

When the user clicks a button showing ADD IMAGE STAMP in the setting area of the screen displayed at the client terminal a screen is displayed as shown in .

A screen example in a case in that the identification pattern print is indicated as the requirement will be described with reference to . is a diagram showing a screen example showing details in the case in the identification pattern print is indicated as the requirement.

In an image is displayed in a displaying area of a screen when the identification pattern print is indicated. The user is prohibited from changing the setting at the screen but can confirm that the identification print is indicated as the requirement before printing out the portable document . By this confirmation the user can determine to actually print out the portable document or to cancel the print request.

For example the identification pattern is printed by dots as shown in . is a diagram showing an example of magnifying the identification pattern according to the embodiment of the present invention. In for example an identification pattern may be drawn by identification image data 12 dots high 8 dots wide and 3 dots interval that is an image size is 48 32 pixels .

In order to identify a right left top and bottom sides for example the entire of one right column and one bottom row may be dotted and code of 77 bits may be encoded at other 11 7 77 dots. The code can be realized by a simple rule such that a dot is printed when a bit value is 1 and a dot is not printed when the bit value is 0 .

For example in a case in that the user uses a function serving as a printer at the digital copier and prints out the portable document from the document viewer a sequence of the requirement process in S in which is conducted when the private print mode is indicated as the requirement will be described in detail with reference to . is a diagram showing a requirement process sequence in the private print mode according to the embodiment of the present invention.

In when the user conducts the print request for the portable document displayed by the document viewer the document viewer requires the user to input the password S . When the user inputs the password S the document viewer sets the private print mode and the password to a printer driver being installed into the client terminal S . Then the document viewer sends a print instruction to the printer driver S .

The printer driver generates a PDL Page Description Language in response to the print instruction sent from the document viewer S and sends information including the PDS for example RPCS or postscript the private print mode and the password to the digital copier S . After that the printer driver sends a print end to the document viewer S .

On the other hand the digital copier temporarily stores the information including the PDL the private print mode and the password in an internal hard disk S and waits until the user inputs the password.

The user inputs the password to the digital copier to output a document printed from the portable document at the digital copier S .

The digital copier compares the password input by the user with the password received from the printer driver and conducts the print process when both the passwords correspond each other S . When both the passwords do not correspond each other the digital copier does not conduct the print process. By conducting the print process the paper document being printed from the portable document is output from the digital copier S .

By this process sequence in the private print mode it is possible to prevent a user other than the user from seeing the paper document output from the digital copier and also it is possible to prevent the user from taking along with the user.

Moreover in the case in that the user uses the function serving as the printer at the digital copier and prints out the portable document from the document viewer a sequence of the requirement process in S in in a case in that the pattern print mode is indicated as the requirement to print out the portable document will be described in detail with reference to . is a diagram showing a requirement process sequence in the pattern print mode according to the present invention.

In the document viewer determines whether or not the printer driver installed into the client terminal of the user supports the pattern print S . After the document viewer confirms that the printer driver supports the pattern print the document viewer sends information including the pattern print mode and an indicated character string to the printer driver S and conducts a print instruction S .

When the printer driver receives the pattern print mode and the indicated character string and receives the print instruction from the document viewer the print driver generates a PDL S . Then the printer driver sends the PDL including a pattern to the digital copier S .

In the following an abstraction process for corresponding information provided from the application system to the organizational security policy by the security server will be described in detail.

In order to explain the abstraction process conducted by the security server it is assumed that each of tables through manage data as shown in through .

For example by describing in XML extensible Markup Language the user security level table may manage data by a XML file as shown in . is a diagram showing the XML file of the user security level table according to the embodiment of the present invention.

In data managed by the user security level table are described in accordance with the data structure shown in by hierarchical data structure in that structure names and element names shown in the data structure are shown by tags. For example at a lower layer of a tag data concerning a plurality of users are described by tags in parallel. At each of the tags data corresponding to respective elements are described by a tag a tag and a tag.

As described above the document profile management table can be a XML file similar to the user security level table . However in the document profile management table since an entry is created for each document the size of the table becomes bigger. Therefore it is preferable to use a database for the document profile management table .

For example the zone management table may manage data in a XML file shown in by describing in XML. is a diagram showing a XML file of the zone management table according to the embodiment of the present invention.

In data of the zone management table are described in accordance with the data structure shown in by a hierarchical structure in that structure names and element names shown in the data structure are shown by tags. For example in a lower layer of a tag data concerning a plurality of zones by a tag in parallel. In a lower layer of each tag data corresponding to respective elements are described by a tag a and a . The tag further includes a lower layer and data corresponding to respective elements are described by a tag a and a tag. The tag may have a plurality of the tags at a lower layer.

For example in the policy file the access control rule is described as shown in and . and are diagrams showing the access control rule described in the policy file according to the embodiment of the present invention.

In and in the policy file the access control rule is regulated for each document from a description showing a tag to a description showing a tag. For example in the policy file a rule corresponding to a document attribute is shown from a description showing a tag from a description showing a tag and other rule and rule corresponding to other document attributes are shown from other tags to other tags respectively.

The rule will be described in detail. The rule and rule are described in the same method as the rule and explanation thereof will be omitted.

In the rule a description for sales and topsecret shows that the access control rule corresponding to the document attribute in which the document category is sales sales department and the document level shows topsecret top secret is regulated. Next In the document attribute by the description a plurality of the access control rules corresponding to user attributes are regulated by descriptions and from an tag to a tag.

In the description a description of RELATED PERSON manager and RESTRICTED describes the access control rule for the user attribute in that the user category is RELATED PERSON the user level is manager and the zone is RESTRICTED . Moreover in the description a description of RELATED PERSON and ANY describes the access control rule for the user attribute in that the user category is RELATED PERSON and the user level is ANY . The description does not indicate the zone. As described above the access control rule is described for each of a plurality of user attributes with respect to one document attribute.

In the description descriptions and from an tag to a tag indicate operations in which the access control rule is applied.

In the description by a description of read for a document belonging to the document category and the document level indicated by the description the user belonging to the user category the user level and the zone indicated by the description is allowed to read the document .

In addition in the description by a description of print for the document belonging to as described by the description the user belonging to as described by the description is allowed to print out the document in a condition in that requirements described as follows are processed.

In the description three requirements are indicated to print out the document . By a description of private access and private access private print mode is indicated as the requirement to print out the document .

Moreover by a description of print alarm and Printed by u it is indicated to conduct print alarm alarm print by using a alarm character string in a character string format indicated Printed by u as the requirement to print out the document .

Furthermore by a description of identifiable bg pattern and dynamic image it is indicated to conduct identifiable bg pattern identification pattern print by using a pattern character string shown by an identification pattern image indicated by dynamic image .

In these assumptions described above for example in a case in that Taro Yamada leader of a Marketing group in a Sales department of a Comn company prints out a document identified by the document ID 0000000003 the authentication result information as shown in is provided by the user management server to the application system . is a diagram showing an example of the authentication result information.

In for example in accordance with the data structure shown in the authentication result information AuthInfo shows Taro Yamada Sales Com as userId Taro Yamada as userName and Members Sales Com Marketing Sales Com Employee Com and GroupLeaders Sales Com as groups .

Accordingly Taro Yamda is specified by this authentication result information and the security server executes the decision process. In the security server the user security level mapping part searches for Taro Yamda shown in the authentication result information from the user security level table shown in . At first GroupLeaders Sales Com in userId or groups corresponds to Taro Yamda and mapped to manager in .

Subsequently the user category mapping part searches Members Sales Com of relatedPersons of the document identified by the document ID 0000000003 from the document profile management table shown in and determines whether or not the user Taro Yamada is allowed for related persons. The user category mapping part determines that the user Taro Yamada is a related person since the user Taro Yamada belongs to Members Sales Com in .

For example the zone mapping part receives context information as shown in . is a diagram showing an example of the context information according to the embodiment of the present invention. In 192.207.138.64 as ipAddress and 02 36 55 22 78 01 as macAddress are indicated in the context information.

The zone mapping part obtains saleszone01 and saleszone02 as zones of the document identified by the document ID 0000000003 by referring to the document profile management table . Moreover the zone mapping part obtains a list of an IP address and a MAC address included in the zones saleszone01 and saleszone02 . Since an IP address 192.207.138.64 of the context information shown in is included in the zone saleszone01 the zone mapping art determines that the IP address 192.207.138.64 is inside the zone in .

For example the document security attribute mapping part receives document identification information as shown in . is a diagram showing an example of the document identification information according to the embodiment of the present invention. In 0000000003 as docId is indicated in the document identification information.

The document security attribute mapping part determines by referring to the document profile management table that the document category of the document identified by the document ID 0000000003 is sales and the sensitivity level is topsecret in .

By mapping processes conducted by the user security level mapping part and the zone mapping part it is possible to abstract parameters such as manager as the user security level related person as the user category print as the access type inside zone as the zonecategory sales as the document category and topsecret as the sensitivity level.

Based on these abstract parameters the policy base access control decision part determines to allow or prohibit in accordance with the access control rule policy described in the policy file shown in . As a result by the descriptions and the document belonging to sales and topsecret is allowed for related persons in manager class to print . However since private access private print mode print alarm alarm print and identifiable bg pattern identification pattern print are regulated as the requirements the access control decision result as shown in is returned.

In the access control rule in the policy file Printed by u is described. u is variable and is replaced with Taro Yamada by the compensating process.

In addition in the access control rule in the policy file in a case in that dynamic image is described and the access type is print an entry for a new print profile is created in the print profile management table as shown in . is a diagram showing an example of the print profile management table according to the embodiment of the present invention. In by creating the entry for the new print profile a value of printId is obtained. Then the value of printId is encoded to create identification image data and the identification image data is stored in data as the binary image data.

For example the identification image data are overlaid and printed on a sheet when the document is printed out so that the identification image data can be utilized to identify or trace the document . is a diagram showing an example of the identification pattern being printed according to the embodiment of the present invention. For example as shown in the identification pattern shown in is overlaid.

A case in which another user conducts the print request for the same document from the same client terminal and is specified as Hanako Satoh by the authentication result information as shown in will be described. is a diagram showing another example of the authentication result information according to the embodiment of the present invention.

In for example the authentication result information shows in accordance with the data structure shown in in that Hanako Satoh Sales Com is indicated as userId Hanako Satoh is indicated as userName and Members Sales Com Marketing Sales Com and Employee Com are indicated as groups .

The user Hanako Satoh is specified by this authentication result information and then the security server executes the decision process. By executing the decision process since the user security level indicates regular the user category indicates related person the access type indicates print the zone category indicates inside zone the document category indicates sales and the sensitivity level is topsecret the security server determines in accordance with the access control rule policy described in the policy file . As a result the access control decision result shows that the user Hanako Satoh is not allowed to print out the document .

Moreover in a case in that the user Taro Yamada attempts to read a document specified by the document ID 0000000001 the access control rule policy does not regulates this access read for the document . As a result the access control decision result indicates that the user Taro Yamada is not allowed to read the document .

Furthermore in a case in that a paper document to which the document is copied by the user Taro Yamada is copied by the digital copier the digital copier sends the access decision request to the securing server based on image data generated by scanning the paper document .

The security server receives document identification information as shown in or from the digital copier .

The document identification information will be described with reference to and . is a diagram showing an example of the document identification information in a case in that image data itself is actually sent to the security server according to the embodiment of the present invention. In docId and printId are not indicated and the image data is stored in binary in image as binary image data .

When the security server receives the image data in binary as shown in from the digital copier the security server obtains p000000001 as printId . Based on printId the security server refers to the print profile and obtains 0000000003 as docId . Then the security server conducts the access control decision in accordance with the access control rule policy regulating a case in that the access type indicates copy similarly to a case or print by Taro Yamada .

According to the present invention for example in a description of a policy requiring a print of a name of the user when the user prints out the portable document that is when the portable document is output as the paper document outside a control of the document viewer by conducting an operation for printing out the portable document the policy can regulate so as to improve a suppression effect for a leak of information with respect to the user attempting to print out the portable document . Therefore it is possible to maintain a security of the portable document .

Moreover in the description of the policy since it is possible to regulate the requirement to print the user name of the user attempting to print out a regular paper document when the regular paper document is printed out it is possible to maintain a security of the paper document that copies the regular paper document and is output from the digital copier by printing the user name of the user to the paper document .

Furthermore in the description of the policy since it is possible to regulate the requirement to record a log when the server document is read out from the document management system it is possible to keep the log showing that the server document is read out. Accordingly it is possible to prevent the user who read out the server document from leaking information and maintain a security of the server document .

In the description of the policy since the requirement to allow an operation can be regulated so as to conduct a process for maintaining the security after the operation it is possible to consistently maintain the security of the document before and after the operation.

In a conventional security for the document the security of the document cannot be maintained after the operation is conducted.

However according to the present invention it is possible to consistently maintain the security of the document even after the operation is conducted for the document .

In the following the operations the requirements the supplement information in the access control rule regulated in the policy file will be described in detail.

Since there are operations having the same name for the server document the paper document and the portable document the following prefixes are additionally provided at the beginning of an operation identification to distinguish each other.

xxxx shows an English word for an operation. In the following a title of each section shows the operation identification.

For example this is an operation to request storing the document to the document management server . This operation is used to store the document to a repository storage unit such as the document management system the digital copier or the like in that a security management can be conducted for a document file this operation may be called new creation or new registration .

As adaptable requirements record audit data explicit authorization encryption integrity protection and show alarm can be indicated. Each of these requirements will be described later.

For example this is an operation to request to refer to a property of the document stored in the document management system . Instead of referring to obtaining contents of the document attribute information such as a file size a created date and time and an owner of the document is referred to by this operation. When this operation is not allowed an existence of the document cannot be recognized.

As adaptable requirements record audit data explicit authorization multi authentication and show alarm can be indicated. Each of these requirements will be described later.

For example this is an operation to request to refer to read out the document stored in the document management system and to refer to download contents of the document in the document management system . A protected document file is downloaded.

As adaptable requirements record audit data explicit authorization multi authentication and show alarm can be indicated. Each of these requirements will be described later.

The document file being downloaded is called portable document . Since an access to the portable document is required to be controlled the portable document to be downloaded by the operation sdOpe read is protected protected document file .

For example this is an operation to refer to read out an original file of the document stored in the document management system . The operation sdOpe read conducts to download the document file without any protection and this operation sdOpe get org conducts to download the original document file without any protection.

As adaptable requirements record audit data explicit authorization multi authentication and show alarm can be indicated. Each of these requirements will be described later.

For example this is an operation to request to revise the document stored in the document management system . This operation is used to open edit and revise the document stored in the document management system by an editor or replace resave the document stored in the document management system .

As adaptable requirements record audit data explicit authorization multi authentication versioning and show alarm can be indicated. Each of these requirements will be described later.

For example this is an operation to request to delete the document stored in the document management system . The document stored in the document management system is deleted by this operation.

As adaptable requirements record audit data explicit authorization multi authentication complete deletion and show alarm can be indicated. Each of these requirements will be described later.

This is an operation to request to refer to open the portable document . A file of the portable document is open by this operation.

As adaptable requirements record audit data explicit authorization multi authentication and show alarm can be indicated. Each of these requirements will be described later.

This is an operation to request to print out the portable document . Contents in a file is printed out by this operation.

As adaptable requirements record audit data explicit authorization private access record image data embed trace info show label visible watermark anti copy watermark trusted bg pattern identifiable bg pattern and show alarm can be indicated. Each of these requirements will be described later.

This is an operation to request to send the portable document by fax. The contents of the file are directly transmitted by fax by this operation. This operation corresponds to a process for printing out by a printer object corresponding to the fax.

As adaptable requirements record audit data explicit authorization address restriction private send record image data show label visible watermark show alarm and print alarmcan be indicated. Each of these requirements will be described later.

This is an operation to request to copy the paper document . The document being papers is copied by this operation.

As adaptable requirements record audit data explicit authorization show label show operator owner only record image data show alarm and print alarmcan be indicated. Each of these requirements will be described later.

This is an operation to request to transmit the paper document by fax. The document being papers is transmitted by fax by this operation.

As adaptable requirements record audit data explicit authorization address restriction private send record image data show label visible watermark show alarm and print alarmcan be indicated. Each of these requirements will be described later.

This is an operation to request to scan the paper document . The document being papers is read out by scanner and digitalized to be a digital file by this operation.

As adaptable requirements record audit data explicit authorization record image data digital watermark be indicated. Each of these requirements will be described later.

In the following each requirement is explained. A title of each section shows an identification of the requirement. Each requirement is differently processed. A process for the requirement is conducted by the application system .

This requirement requires recording a log. For example a log may be recorded for each page when the document is copied by the digital copier . Alternatively a log is recorded for the document being copied by grouping by each security ID.

This requirement requires allowing by a document management administrator. In a case in that this requirement is regulated in the policy when it is not explicitly indicated to the security server that an operation requiring this requirement is allowed the operation is not allowed. When the security server recognizes result that this requirement is regulated by a determination obtained in the decision process the security server checks whether or not a permit is issued. When the permit is issued requirements showing allowed true and excluding explicit authorization are sent to the application system as the determination result by the decision process. When the permit is not issued allowed false as the determination result is sent to the application system .

This requirement requires encrypting a digital document. When this requirement is regulated by the policy a server administrator is not wanted to read contents of the digital document. Accordingly the application system is required to encrypt the digital document so that even the server administrator cannot read it. That is it is required to store a decryption key for decrypting this encryption so that the server administrator of the application system cannot use the decryption key.

This requirement requires securing integrity of the digital document integrity of an original . When this requirement is regulated in the policy the application system protects the original of the digital document from being tampered. The application system may store the digital document to a document protection area by itself. Alternatively the application system may request the security server to store the original to the document protection area.

The security server stores the original document file before converting into PDF received from the application system and a secured PDF file being converted to the document protection area. An original document ID of the original document stored in the document protection area is recorded as application data of the document profile management table .

In a case in that the document protection area is not setup in the security server storing to the document protection area causes an error. The security server records a log having a higher security level even if a serious error occurs.

In the requirement process the application system requests storing to the document protection area to the security server . The security server stores to the document protection area when receiving the request.

This requirement requires the multiple authentication for an access to the digital document. When this requirement is regulated in the policy for example the application system is required to conduct the multiple authentication such as a finger print recognition or an iris recognition in addition to a regular user authentication. The application system can determine to use which authentication method. The access may not be allowed when a further authentication is conducted successively after the regular user authentication and is failed. Alternatively the further authentication may be conducted after being requested to the user when this requirement is returned.

In a case in that this requirement is regulated in the policy instead of saving a revised digital document to the original the application system is required to conduct the version management. When the application system does not support a function of the version management the application system must not revise the digital document since the requirement is not satisfied.

This requirement requires conducting a perfect deletion of the digital document. In a case in that this requirement is regulated in the policy the application system not only delete an entry of the digital document simply but also conduct a perfect deleting process by writing random data on a disk area where the digital document was stored.

This requirement requires using the private print mode. In order for other persons not to take printed paper sheets away the printed paper sheets are output when the user printing the digital document is confirmed by using an operation panel of a printer. In a case in that this requirement is regulated in the policy the application system is required to print out the digital document by using the private print mode. If the print does not support the private print mode the application system does not allow for the user to print out the digital document. However if the print does not support the private print mode but an environment of the printer has less possibility in that other persons take the printed paper sheets away the user probably wants to print out the digital document at the printer. In this case show alarm is indicated as the alternative requirement of this requirement private access in the policy so that an alarm is displayed and the user is allowed to print out the digital document.

This requirement requires recording an image log. A print image and a copy image themselves are recorded and maintained. In a case in that this requirement is regulated in the policy the application system indicates an image data record to a printer adapter of a printer to print out the digital document with a print instruction. When this requirement is regulated as the requirement of a copy an image copying an original paper document is stored in a hard disk document box in the digital copier .

This requirement requires embedding trace information to print out the digital document. When the digital document is printed out identification information identifying the digital document is embedded to a paper sheet and the printed paper sheet is output. As the trace information a two dimensional barcode is used.

In a case in that this requirement is regulated in the policy in the decision process the security server sends this requirement embed trace info and also the supplement information showing to dynamically generate the trace information. That is the security server sends the supplement information supplement indicating dynamic image. When the security server recognizes that the policy regulates the supplement information supplement of dynamic image the security server obtains an embedding image from the document profile management table and sends the requirement embed trace info and also the embedding image as the supplement information supplement as a returned value of the decision process of the security server refer to a section of the supplement information dynamic image . The application system embeds the embedding image received from the security server to the paper sheet to be printed.

In the requirement process the security server obtains the embedding image from the document profile management table and the application system actually embeds the embedding image while printing.

This requirement requires printing a label such as secret as a stamp. In a case in that this requirement is regulated in the policy the security server sends a bitmap data of a label stamp as the supplement information supplement with this requirement show label by a returned value of the decision process. Information showing that which stamp is printed for what kind of the document is set to the security server beforehand. In the policy information concerning an ID of the label stamp and a location to stamp a label is regulated. A bitmap file corresponding to the ID is stored in a local hard disk of the security server . The security server read out the bitmap file and sends the supplement information supplement shown by a byte array to an upper layer.

If the bitmap file corresponding to the ID of the label stamp regulated in the policy only the ID of the label stamp is included in the supplement information supplement and the requirement is sent without the bitmap data refer to a section of static image .

A stamp image is not assumed to dynamically generate. The security server sends the requirement and the supplement information supplement themselves to the application system . The application system overlays and print out the received stamp image.

In the requirement process the security server provides the stamp image and the application system digital copier stamps the label stamp to the paper sheets.

This requirement requires printing the visible watermark letter on a background of a paper sheet. In a case in that this requirement is regulated in the policy the security server sends a character string format for printing as a watermark as the supplement information supplement with this requirement visible watermark by a returned value of the decision process. As the supplement information supplement of this requirement information showing that what kind of the document requires which character string format in the policy. The security server sends this requirement and the supplement information supplement themselves to the application system . The application system generates a watermark character string in accordance with the character string format received from the security server refer to a section of string format .

As the requirement that cannot be indicated simultaneously conflicting requirement there are anti copy watermark trusted bg pattern and identifiable bg pattern.

In the requirement process the security server provides the character string format and the application system digital copier prints out the character string to the paper sheet.

This requirement requires printing an embossed watermark letter. The embossed watermark letter is embossed when a paper sheet having this embossed watermark letter is copied. In a case in that this requirement is regulated in the policy the security server sends a character string format for printing a watermark as the supplement information supplement with this requirement anti copy watermark by a returned value of the decision process. Information showing that what kind of the document requires which character string format is regulated as the supplement information supplement of this requirement in the policy. The security server sends the requirement and the supplement information themselves to the application system . The application system generates and print out a watermark letter in accordance with the character string format received form the security server refer to a section of the supplement information string format .

As the requirement that cannot be indicated simultaneously conflicting requirement there are visible watermark trusted bg pattern identifiable bg pattern.

In the requirement process the security server provides a character string format and the application system prints a character string on a paper sheet.

In a case in that this requirement is regulated in the policy the security server sent information showing that this requirement identifiable bg pattern and the supplement information is required to dynamically generate as a returned value in the decision process. When the security server recognizes that a dynamic image generation supplement information dynamic image is indicated the security server obtains an identification pattern from the document profile management sends this requirement identifiable bg pattern and the supplement information by the returned value of the decision process refer to a section of supplement information dynamic image .

The application system prints the identification pattern received from the security server on the background of the paper sheet to be printed out.

As the requirement that cannot be indicated simultaneously conflicting requirement there are visible watermark anti copy watermark trusted bg pattern.

In the requirement process the security server obtains the identification pattern from the document profile management table and the application system actually prints the identification pattern on the background of the paper sheet.

This requirement requires displaying an alarm. An alarm such as Give attention to handle top secret is displayed to warn the user . This requirement aims to display the alarm at a display or an operation panel. Another requirement print alarm is used when the alarm is required to print to a paper sheet. Information showing that what kind of the document is required to display which character string is regulated as the supplement information supplement of the requirement in the policy. The security server sends the requirement and the supplement information themselves to the application . The application system generates and displays the character string in accordance with the character string format received from the security server .

In the requirement process the security server provides the character string format to display and the application system display the alarm in the character string format.

This requirement requires printing an alarm. An alarm such as RRR Internal Use Only is printed to warn the user . This requirement aims to print the alarm on a paper sheet. Another requirement show alarm is used to display the alarm at a display or an operation panel.

Information showing that which character string is printed for what kind of the document is regulated as the supplement information of this requirement in the policy. The security server provides a character string format to display the alarm and the application system displays the alarm. The security server sends this requirement and the supplement information supplement themselves to the application system . The application system generates and prints the character string in accordance with the character string format received from the security server .

As the necessary supplement information there is string format and string position. There is no requirement that cannot be indicated simultaneously conflicting requirement .

In the requirement process the security server provides the character string format to print and the application system prints the alarm in the character string format.

This requirement requires using the confidential transmission mode. The confidential transmission mode is used so that other persons cannot take a paper sheet transmitted by fax away. A fax transmission process is not conducted for a fax which does not support the confidential transmission mode.

If the fax does not support the confidential transmission mode but an environment of the fax has less possibility in that other persons take the faxed paper sheets away the user probably wants to fax. In this case show alarm is indicated as the alternative requirement of this requirement private receive in the policy so that an alarm is displayed and the user is allowed to fax.

This requirement requires printing a user name printing. In a case in that this requirement is regulated in the policy the security server sends a character string format to print with this requirement show operator by a returned value of the decision process. Information showing that which character string is printed for what kind of the document is regulated as the supplement information supplement of the requirement in the policy.

The security server sends the requirement and the supplement information supplement themselves. The application system generates the character string in accordance with the character string format received from the security server and prints the character string on a printed paper sheet.

In the requirement process the security server provides the character string format to print that is regulated in the policy and the application system prints the character string in accordance with the character string format when the document is printed.

This requirement requires only for the user printing the document to copy. In a case in that this requirement is regulated in the policy the security server sends the requirement owner only by a returned value of the decision process. When the security server recognizes this requirement the security server obtains the user ID of the user printing a copied document from the document profile management table and compares a user attempting to copy and a user who printed the document . When both the users are the same person the security server sends a result of the decision process expect for this requirement owner only. when both the users are not the same person the security server sends the result of the decision process showing allowed false .

In the requirement process the security server sends not allowed when the both users are not the same person.

This requirement requires masking not to read the document . When the document is copied in order to warn the user that the document is not allowed to copy this requirement masks the document by printing the entire of the document in gray so that the document cannot be read.

There is no requirement that cannot be indicated simultaneously conflicting requirement . Even if the conflicting requirement such as show label is indicated this requirement ends up being meaningless.

This requirement requires embedding a digital watermark in image data. In a case in that this requirement is regulated in the policy the security server sends a character string format to embed as the digital watermark with this requirement digital watermark by a returned value of the decision process. Information showing that which character string format is used for what kind of the document is regulated as the supplement information of this requirement in the policy. The security server sends the supplement information supplement itself to the application system . The application system generates an embedding character string in accordance with the character string format received from the security server and embeds as the digital watermark to the image data of the document refer to a sections of the supplement information string format and watermark type .

As the requirement that cannot be indicated simultaneously conflicting requirement there are anti copy watermark trusted bg pattern and identifiable bg pattern.

In the requirement process the security server provides the character string format and the application system embeds the digital watermark in accordance with the character string format received from the security server .

The requirement may require the supplement information. A method for indicating the supplement information is defined as follows. A title of each section shows an identification of the supplement information.

This supplement information is used to indicate fixed image data. As the fixed image data for example there is a stamp image to use for the requirement of the label display show label . Since the fixed image data are not stored in the policy file an identification label identifying a fixed image data file is indicated in the policy file . At the beginning of the identification label ref is provided to indicate the identification label.

In a case in that this supplement information is indicated in the policy file as described above when the a policy decision result is returned in an decision process method of the security server the policy decision result is returned as follows 

As described above when ref is indicated as the supplement information the security server reads out a file corresponding to the identification label and conducts an including process for including the file as binary data as the supplement information.

This supplement information is used to indicate dynamic image data. As the dynamic image data for example there are a barcode image used for the requirement of the tracing information embedding embed trace info and an identification pattern image used for the requirement of the identification pattern identifiable bg pattern .

Since these image data are dynamically generate by the document a description for the image data cannot be included in the policy file . The policy file indicates a type of information dynamically generated as the supplement information for example type of information such as the document ID and the user ID .

A format of this supplement information is dyn info type . Only a section ID SecId can be indicated in info type.

In a case in that this supplement information is indicated in the policy file as described above when the policy decision result is returned in the decision process method of the security server the security server do not conduct any process but the policy decision result is returned as follows 

Then the security server receiving decision result information dynamically generates necessary image data and sends the following as a result of the decision process.

This supplement information is sued to indicate an embedding location of an image. In a case of embedding partially instead of embedding the image to the entire of a page this supplement information is indicated by an embedding requirement such as show label . In a case of embedding the entire of the page embedding a tile a different requirement identifiable bg pattern or the like is used.

A format of this supplement information is position id position id selectively indicates one of five location upper right lower right upper left lower left and center.

The security server sets the supplement information in the decision result information to send back to a request originator.

This supplement information is used to indicate a character string format. The character string format is indicated for the requirement such as the watermark visible watermark . A format of this supplement information is format string . The character string format is indicated in the policy file as follows format string indicates a combination of the followings and any character string.

The security server sets this supplement information to the decision result information to send back to a request originator. The requirement may have a limitation of a maximum character number for example 32 characters for the requirement visible watermark . Characters over the maximum character number are not used.

This supplement information is used to indicate an embedding location of a character string. This supplement information is used for the embedding requirement embedding partially print alarm or a like but not embedding the character string on a background. In a case of embedding the character string on the background a different requirement visible watermark or a like . The embedding location is indicated by the identification label in the policy file .

A format of this supplement information is position id . position id is selectively set from six positions upper right lower right upper left lower left upper center lower center and upper lower center.

The security server sets this supplement information in the decision result information to send back to a request originator.

This supplement information is used to indicate a color. This supplement information is indicated for the requirement of a copy suppression pattern anti copy watermark .

A format of the supplement information is color id . color id indicates either one of cyan and magenta.

The security server sets this supplement information to the decision result information to send back to a request originator.

This supplement information is used to indicate a watermark type. This supplement information is indicated by the requirement of a digital watermark digital watermark .

A format of this supplement information is watermark type id . watermark type id indicates traceability integrity and steganography. traceability indicates the digital watermark for a tracing purpose integrity indicates the digital watermark for a tamper detection purpose and steganography indicates the digital watermark for an information transmission purpose.

The security server sets this supplement information to the decision result information to send back to a request originator.

As described above according to the present invention it is possible for the security server to abstract information provided from the application system in order to correspond to the organizational security policy. That is it is possible to convert information which provided from the application system and has a lower abstraction into different information having a higher abstraction degree that the information received from the application system in order to correspond to the security policy having a higher abstraction degree. Accordingly it is possible to secure the security of both digital document and paper document in accordance with the organizational security policy.

The document management system and the document viewer conduct the access control for the digital document such as the server document and the portable document and the security process for securing the portable document is conducted in accordance with the policy when the portable document is printed from the document viewer . Therefore the user printing the portable document is required to properly handle the paper document to which the portable document is printed in accordance with the policy.

In addition when the paper document to which the portable document is printed is copied by the digital copier the copying process can be controlled in accordance with the policy.

Therefore in a general office it is possible to sufficiently maintain the security of the paper document and the digital document such as the server document and the portable document .

The present invention is not limited to the specifically disclosed embodiments and variations and modifications may be made without departing from the scope of the present invention.

The present application is based on the Japanese Priority Applications No. 2003 178033 filed on Jun. 23 2003 No. 2003 315921 filed on Sep. 8 2003 and No. 2002 315996 filed on Sep. 8 2003 the entire contents of which are hereby incorporated by reference.

