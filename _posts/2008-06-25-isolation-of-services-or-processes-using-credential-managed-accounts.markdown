---

title: Isolation of services or processes using credential managed accounts
abstract: This disclosure describes methods, systems, and application programming interfaces for creating a credential managed account. This disclosure describes creating a new password managed account, defining the password managed account, wherein the password managed account is to access a service on a managed computing device, identifying the password managed account for a lifecycle, and automatically managing the password managed account by updating and changing a password for the password managed account on a periodic basis.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09501635&OS=09501635&RS=09501635
owner: Microsoft Technology Licensing, LLC
number: 09501635
owner_city: Redmond
owner_country: US
publication_date: 20080625
---
The subject matter relates generally to protecting services and more specifically to provide a credential managed account for primary and trusted computing base services.

There are many services such as Structured Query Language SQL and Microsoft Exchange operating on a local system or on a network service on Windows . Typically these services may authenticate to another computing device causing all of the services to authenticate as the computing device. This creates a problem that any distinction among the different services is lost over the wire. Thus service differentiation is difficult because the services do not have distinct identities over the wire.

Another problem is the administrators for SQL and Microsoft Exchange struggle with security issues and management costs when deploying and configuring these services. The problem occurs when the administrators deploy these services with domain and local accounts and have to manually manage and change the passwords.

Although administrators have attempted to create a solution for managing the service password there is room for improvement. It is desirable to find ways to protect services by managing passwords and improving security.

This summary is provided to introduce a selection of concepts in a simplified form that are further described below in the Detailed Description. This Summary is not intended to identify key features or essential features of the claimed subject matter nor is it intended to be used to limit the scope of the claimed subject matter.

In view of the above this disclosure describes various exemplary systems methods and application programming interfaces for automatically creating and managing a credential managed account for primary services. The disclosure describes creating a new password managed account under a computing device organizational unit defining the password managed account for the computing device wherein the password managed account is to access a service on managed computing devices identifying the password managed account for a lifecycle. Furthermore this disclosure teaches automatically managing the password managed account by updating and changing a password for the password managed account on a periodic basis.

This automatic management of password improves the security and reduces the operation costs when deploying and configuring services. Furthermore there is improved efficiency and convenience of primary services by creating a credential managed account for computing devices. Thus security is improved and the user experience is enhanced.

Many specific details of certain implementations of the subject matter are set forth in the following description and in to provide a thorough understanding of such implementations. One skilled in the art will understand however that the subject matter may have additional implementations or that the subject matter may be practiced without several of the details described in the following description.

This disclosure is directed to primary and trusted computing base services and is shown and described in the context of creating a credential managed account to improve security. This disclosure describes creating a new password managed account under a computing device organizational unit and defining the password managed account for the computing device wherein the password managed account is to access a service on managed computing devices. Furthermore the disclosure describes identifying the password managed account for a lifecycle and automatically managing the password managed account by updating and changing a password for the password managed account on a periodic basis.

This disclosure describes isolating trusted computing base services from other low privilege services running on a Windows system. This disclosure describes isolation of Structured Query Language SQL and Exchange services from other non Trusted Computing Base TCB services by introducing a new privilege that allows the trusted computing base service to impersonate standard users in order to remove these services from a trusted computing base. Benefits to the administrators are improved security minimal management time and reduced cost.

The creation of a credential managed account for primary services described herein are not limited to any particular application but may be applied to many contexts and environments. By way of example and not limitation the creation of a password managed account may be employed in Windows Windows Server System Windows Server 2003 Windows Vista Windows Exchange Server Active Directory centralized computing services and the like. For example creating the password managed account allows automatic updating and changing the password.

The following discussion of an exemplary operating environment provides the reader with assistance in understanding ways in which various subject matter aspects of the system methods and application programming interfaces may be employed. The environment described below constitutes but one example and is not intended to limit application of the subject matter to any one particular operating environment.

The environment may provide a credential managed account as for example but not limited to a tool a method a solver software an application program a service technology resources which include access to the internet and the like. Here the credential managed account is created by an exemplary application program referred to as credential managed account application program .

This credential managed account application program provides a password managed account to protect the primary services SQL and Exchange. The term credential managed account is used interchangeably with password managed account. The credential managed account is operational in a managed Active Directory environment and in a downlevel Domain Controllers DCs such as Windows Server 2003. Furthermore the credential managed account application program addresses Service Principal Name SPN issues associated with service accounts on Windows 7 or higher DC s.

Here the credential managed account application program provides isolation of services by introducing a new privilege. The new privilege allows the service to impersonate standard users in order to remove these services from the TCB and reduce the same. The impersonations based on service requirements include removing SeImpersonatePrivilege and impersonate at an identity level use limited impersonation token to impersonate standard users and reduce exposure of impersonation by reducing an open handle lifetime. Furthermore administrators can not be impersonated and the token is filtered.

The isolation of services improves security by isolating services that hold user data including but not limited to social security numbers credit card numbers email accounts and the like. Thus the services from other non Trusting Computing Base TCB services are isolated. This isolation occurs in an Active Directory environment.

The credential managed account application program in conjunction with the services provide functionality to allow computing devices to connect to a domain controller a server and a central directory database . The domain controller manages security related aspects between the users and domain interactions centralizing security and administration. The server provides physical and virtual resources. Implementations include but are not limited to a server for load balancing a server for managing the system a server for database a server for applications and the like. The central directory database provides stored information and may or may not be a separate component.

The user can log on at a terminal and run applications access data databases network resources and the like through the primary services . Each log in or terminal session is independent. Advantages of using the credential managed account include facilitate sharing of technologies administering managing and password account that is maintained or upgraded automatically every thirty days and providing a complete graphical user interface including operating system desktop and support for a variety of input devices.

The credential managed account is secure as domain accounts with good password strength complexity and recycle requirements. Policies are in place to control how frequently the passwords are recycled while using the same netlogon setting. The following is an example using the same netlogon setting HKEY LOCAL MACHINE SYSTEM CurrentControlSet Services Netlogon Parameters MaximumPasswordAge.

A benefit is there is no additional cost for a service logon with the credential managed account . The logon cost is similar to a logon cost for a domain service account. Furthermore there is minimal overhead on the system for managing these credential managed accounts .

There are measures for failure and recovery pertaining to the credential managed account . In one instance if a computing device is not able to connect to the DC in the domain the services should be able to complete a cached logon using the credential managed account .

In another instance if the password is updated recently by the TCB component and the password is not replicated to all the DCs then the TCB component should be able to do a logon with N 1 password against DCs which do not have the new password. This is similar to the N 1 password logon logic in netlogon today.

In another instance if the password is out of sync with the password on the DCs because of a system restore for example the service administrator with the necessary rights should be able to reset the password with the new password and proceed with the logon. There is a command line tool in addition to the API for resetting the password on the domain controller and the local system . Note that this is an option in the existing sc.exe or a new tool. An administrator with the necessary permissions should be able to run this tool remotely.

In an implementation there are many versions of Microsoft Windows operating systems run by a logical group of computers known as a Windows Server domain that share a central directory database. This central directory database Active Directory contains the user accounts and security information for resources in the Windows Server domain. In this scenario the credential managed account application program sets up the credential managed account with a password that is updated automatically and managed by Microsoft Windows . The credential managed account application program relies on changes in the Service Control Manager SCM in making the whole scenario occur. The specific changes required from SCM are to call logon user with special flags for the password managed account scenario. The Active Directory administrator provides Object Identifiers OIDs for the new attributes that are stamped on these Password managed accounts .

Illustrated in is an exemplary credential managed account architecture configured for setting up a credential managed account and to isolate services using sub machine accounts. The architecture illustrates three boundaries for creating the credential managed account a process boundary a computing device boundary and a trust boundary .

Turning first to the components to create a credential managed account in the process boundary includes an application process and a set of public Application Programming Interfaces APIs as shown on the left side of . The APIs allow the application process and or administrators to create update delete or overall manage the credential managed account . A more detailed discussion of the APIs follows in .

Shown in the lower half of the process boundary also includes features such as windows Service Control Manager SCM or any process with a Trusted Computing Base TCB privilege . As previously mentioned isolation of services occurs by introducing a new privilege. This new privilege allows the service to impersonate standard users in order to remove these services from the TCB and reduce the same. The impersonations based on service requirements include removing SeImpersonatePrivilege and impersonate at an identity level use limited impersonation token to impersonate standard users and reduce exposure of impersonation by reducing an open handle lifetime. Furthermore administrators cannot be impersonated or the token is filtered. There is improved efficiency and convenience of primary services by isolating services from low privileged services for users on computing devices.

Turning to a Local Security Authority LSA LogonUser function which is part of the computing device boundary . The credential for each credential managed account is stored as LSA secret. The name of the secret has to be unique as to not overlap with other secrets on the computing device and map uniquely to the account that it is created for. In an implementation a name of the secret may be as follows M GUID..

The LSA LogonUser function is modified to accommodate for the credential managed account logon. A contract is established between the callers and the LSA LogonUser as follows 

The LSA side of the LogonUser call checks the Password parameter and if set to the string described above the LSA LogonUser function will open the LSA secret storing the password for that account and use it to complete the logon. This is performed before dispatching the call to the authentication packages to allow for transparency to the packages operation.

To support the Active Directory environment with multiple Domain Controllers DCs reliably new code is added to the LogonUser call that will attempt to use the previous password for the account if the logon with the current password failed with error WRONG PASSWORD. Next the LSA LogonUser interacts with Netlogon modifications which is also in the computing device boundary .

The Netlogon modifications may update the credentials on the credential managed account periodically such as every thirty days. In some implementations the credentials may be managed on a periodic basis based on environment needs typically ranging from at least every fifteen days to at most every sixty days. The Netlogon modifications are changed to accommodate this new feature by using a high level algorithm. The high level algorithm used includes 

As shown in the upper middle section of the diagram the Netlogon modifications illustrates how a password change is relayed to an Active Directory . Alternatively these components may reside in multiple other types of environments.

In an implementation the credential managed account is represented in the Active Directory as a new object class MSSEC CredManagedAcct which will derive from the computer class. The default state of the object on creation is 

Turning back to the Active Directory notifies operational changes to a Lightweight Directory Access Protocol LDAP Operations which stores account information and makes retrieval quick and easy. LDAP Operations may add modify search and or delete passwords along with other account type information. LDAP Operations relays any additions modifications searches and or deletions to the credential managed account back to Netlogon modifications .

The architecture includes an audit log to identify who has changed the password on these credential managed accounts. Thus there are ways to view who can change the password on these accounts. For example this information is available by looking at the Access Control List ACL on the object. The accounts are created under computing device accounts. The parent computing device account can be located anywhere in the Active Directory .

While this implementation is shown in the Active Directory environment there are two modes of operation that organizations may deploy in the credential managed account. These two modes of operation include a locked down environment and a decentralized environment for lifecycle management reasons.

Traditionally a locked down environment limits a certain set of users or groups including but not limited to Domain administrators specialized accounts and the like to create the credential managed account Some versions allow the Domain administrators to create an account shell for the credential managed account under the computing device and provide necessary access rights to a service administrator. The access rights may include but is not limited to SetPassword ValidatedWriteSPN and the like.

The process for the locked down environment includes service setup or management tools to call the new credential managed account APIs . Shown in block the call is to set additional properties for identifying the credential managed account created by the Domain administrator creating a strong random password and setting the same in the Active Directory and creating a LSA secret decorated in a LSA store.

In block the service setup or management tools registers the service with the SCM and configures the service to run under the credential managed account in the service setup management tools.

In block the SCM will call NetIsServiceAccount which is an API to query for the credential managed account . If the query indicates the account does not exist in a logon store a return value is considered false or not true the SCM will ignore the message . However if the process flows such that the NetIserviceAccount indicates there is a credential managed account then the query will return true and the SCM will mark this service as using a credential managed account .

In block the SCM calls LogonUser with the decorated LSA secret as the password. LSA picks up the secret and logon to the credential managed account builds the token and provides the same to the SCM. The SCM starts the service with the resulting token from the above handshake. In an exemplary implementation this phase may range from at least fifteen to at most thirty seconds.

Shown in block is where the TCB component in LSA automatically changes and manages the password for these accounts on a periodic basis. The automatic management may include configuring a Service Principal Name SPN or a host record for client access.

A decentralized environment allows authenticated users and the like to create a credential managed account . For example in block a service administrator configures the service to run under the credential managed account .

The process for the decentralized environment includes service setup or management tools to call a new credential managed account APIs . Shown in block the call is to create the new credential managed account if the account does not exist. The call in block is also to set additional properties for identifying the credential managed account created by the service administrator to create a strong random password and to set the same in the Active Directory and to create a LSA secret decorated in a LSA store.

In block the service setup or management tools registers the service with the SCM and configures the service to run under the credential managed account in the service setup management tools.

In block the SCM calls NetIsServiceAccount which is an API to query for the credential managed account . If the query indicates the account does not exist in a logon store a return value is false or not true the SCM will ignore the message . However if the process flows such that the NetIsServiceAccount indicates there is a credential managed account then the query will return true and the SCM will mark this service as using a credential managed account .

In block the SCM calls LogonUser with the decorated LSA secret as the password. LSA picks up the secret and logons to the credential managed account builds the token and provides the same to the SCM. Next the SCM starts the service with the resulting token from the above handshake. In an exemplary implementation this phase may range from at least fifteen to at most thirty seconds.

Shown in block is where the TCB component in LSA changes and manages the password for these accounts on a periodic basis. This periodic basis may range from at least fifteen days to at most sixty days. The automatic management may include configuring a Service Principal Name SPN or a host record for client access.

Block illustrates an API to create the credential managed account. In an implementation the API is NetAddServiceAccount. The parameters may include 

The behavior of the API is if the account already exists in the Active Directory and the RefCount on the account is 0 which will be the case of a centralized environment where domain administrator precreates the account then the account will be reset to a Default account state and a new password will be set. Otherwise if RefCount is greater than 0 the RefCount will be incremented and no additional work will be done.

If the account does not exist in Active Directory the account will be created initialized to the Default account and a new password will be set. In all cases the RefCount will be incremented.

Block illustrates an API to remove the credential managed account. If an application service administrator changes the service account from a Credential Managed Account to a non Credential Managed Account and no other services on the system are using that Credential Managed Account then in an implementation RemoveCredentialManagedAccount should be called to do the following 

In another implementation an API to remove the account is NetRemoveServiceAccount. The parameters may include 

The behavior of the API is that the reference count on the account will be decremented. If the count is greater than 0 no additional work will be done. Otherwise the account will be deleted from Active Directory the locally stored LSA secret will be deleted as well as the state stored in the Netlogon registry store.

Block illustrates an API to query for a credential managed account . In an implementation the API to identify the credential managed account to query is NetIsServiceAccount. The parameters may include 

The behavior for this API is if the account specified exists in the Netlogon store the return value will be true otherwise it will be false.

Block illustrates an API to identify the credential managed account on a computing device. In an implementation the API to create enumerating service accounts is NetEnumerateServiceAccounts. The parameters may include 

The behavior of the API is to enumerate all the accounts in the Netlogon store and return an array of structures describing these accounts.

Memory may store programs of instructions that are loadable and executable on the processor as well as data generated during the execution of these programs. Depending on the configuration and type of computing device memory may be volatile such as RAM and or non volatile such as ROM flash memory etc. . The terminal server may also include additional removable storage and or non removable storage including but not limited to magnetic storage optical disks and or tape storage. The disk drives and their associated computer readable media may provide non volatile storage of computer readable instructions data structures program modules and other data for the computing devices.

Memory removable storage and non removable storage are all examples of computer storage media. Computer storage media includes volatile and non volatile removable and non removable media implemented in any method or technology for storage of information such as computer readable instructions data structures program modules or other data. Memory removable storage and non removable storage are all examples of computer storage media. Additional types of computer storage media that may be present include but are not limited to RAM ROM EEPROM flash memory or other memory technology CD ROM digital versatile disks DVD or other optical storage magnetic cassettes magnetic tape magnetic disk storage or other magnetic storage devices or any other medium which can be used to store the desired information and which can accessed by the terminal server or other computing device.

Turning to the contents of the memory in more detail may include an operating system one or more application programs or service for implementing the credential managed account program . In one implementation the memory includes a manager module and a protocol management module . The manager module includes but is not limited to identifying and tracking a session. The protocol management module stores and manages storage of information such as session identifier session state computing devices of the user and the like and may communicate with one or more local and or remote databases or services.

The memory further includes a user interface module and a session module . The user interface module presents the user with the user interface to log in or log off in and out of a session and the like. The session module includes but is not limited to tracking a state of the computing devices logging in or logging off connecting or disconnecting and the like. The session module performs connections disconnections search functions such as performing searches to identify the client devices that are logged on logged off state of the client devices the status of the user and the like.

The memory may include application programming interface APIs module and an internal interface module . The APIs help support requests for creating the credential managed account removing the credential managed account identifying the account to be queried an enumerating the account made by the credential managed account application program .

The processing functionality may also contain communications connection s that allow the processing functionality to communicate with a stored database another computing device or server the user terminals and or other devices on the network. Communications connection s is an example of communication media. Communication media typically embodies computer readable instructions data structures and program modules. By way of example and not limitation communication media includes wired media such as a wired network or direct wired connection and wireless media such as acoustic RF infrared and other wireless media. The term computer readable media as used herein includes both storage media and communication media.

The processing functionality may also include input device s such as a keyboard mouse pen voice input device touch input device etc. and output device s such as a display speakers printer etc. The processing functionality may include a database hosted on the processing functionality including but is not limited to session data network addresses list of computing devices and the like. All these devices are well known in the art and need not be discussed at length here.

The subject matter described above can be implemented in hardware or software or in both hardware and software. Although the subject matter has been described in language specific to structural features and or methodological acts it is to be understood that the subject matter defined in the appended claims is not necessarily limited to the specific features or acts described above. Rather the specific features and acts are disclosed as exemplary forms of implementing the claimed subject matter. For example the methodological acts need not be performed in the order or combinations described herein and may be performed in any combination of one or more acts.

