---

title: Software framework that facilitates design and implementation of database applications
abstract: An intelligent framework is provided that is disposed between a high-level language environment and a database system environment. According to one embodiment, a software framework infers the need for one or more integrity constraints. The software framework programmatically receives (a) information regarding definitions of a multiple data structures associated with multiple objects participating in a software application, and (b) information regarding relationships among the data structures, where each object represents an instance of a data structure of the multiple data structures. Then, the software framework infers the need for one or more integrity constraints based upon the information regarding definitions of the data structures and the information regarding relationships among the data structures. Finally, the software framework instructs a storage system to apply the one or more integrity constraint.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09009195&OS=09009195&RS=09009195
owner: RPX Corporation
number: 09009195
owner_city: San Francisco
owner_country: US
publication_date: 20080617
---
This application is a continuation of U.S. patent application Ser. No. 10 836 580 filed Apr. 30 2004 which claims the benefit of U.S. Provisional Application No. 60 466 939 filed Apr. 30 2003 both of which are hereby incorporated by reference in their entirety for all purposes.

Contained herein is material that is subject to copyright protection. The copyright owner has no objection to the facsimile reproduction of the patent disclosure by any person as it appears in the Patent and Trademark Office patent files or records but otherwise reserves all rights to the copyright whatsoever.

Embodiments of the present invention generally relate to design and implementation of database applications. More particularly embodiments of the present invention relate to methods and techniques of programmatically managing the creation of database structure populating the database structure and accessing and or manipulating data stored in a database.

Development of database applications currently involves two distinct skill sets typically requiring the involvement of both database engineers and software engineers. An example of current database modeling activities may include the following 1 One or more database engineers capture the requirements of the database application in an entity relationship diagram ERD 2 manually or with the assistance of a database tool such as Oracle9i Designer of Oracle Corporation the database engineer s create an appropriate database schema to support the relationships presented by the ERD 3 the database engineer s convey the requirements of the database application to one or more software engineers 4 the software engineer s capture the requirements in an appropriate form such as uniform modeling language UML diagrams for development of needed data structures e.g. class definitions and 5 the software engineer s create the data structures. Other tasks such as provisioning and providing for access and manipulation of the database typically require similar interactions among the database engineers and the software engineers.

As can be appreciated a software development team composed of both database engineers and software engineers implementing the above database modeling process is costly both in terms of communication overhead and payroll. Consequently a need exists to reduce the complexity of and or automate database design and development tasks thereby allowing application developers with limited or no database skills to efficiently and effectively perform such tasks.

Apparatus and methods are described for providing a software framework that facilitates efficient design and implementation of database applications. According to one embodiment a software framework infers the need for one or more integrity constraints. The software framework programmatically receives a information regarding definitions of a multiple data structures associated with multiple objects participating in a software application and b information regarding relationships among the data structures where each object represents an instance of a data structure of the multiple data structures. Then the software framework infers the need for one or more integrity constraints based upon the information regarding definitions of the data structures and the information regarding relationships among the data structures. Finally the software framework instructs a storage system to apply the one or more integrity constraints.

Other features of embodiments of the present invention will be apparent from the accompanying drawings and from the detailed description that follows.

Apparatus and methods are described for providing a software framework that facilitates efficient design and implementation of database applications. Broadly stated embodiments of the present invention seek to automate the tasks of defining the structure accessing and manipulating a database by abstracting the underlying syntax and semantics of the particular database system being employed. According to one embodiment such abstraction is accomplished by providing an interface layer referred to below as Lentils between a high level programming language environment and the database environment provided by the particular database vendor. For example a Lentils application programming interface API may be provided that programmatically and dynamically generates appropriate data definition data query and or data manipulation expressions which according to one embodiment may be one or more statements from a data definition language data query language and or data manipulation language associated with a database storage system responsive to receipt of information concerning a desired operation and appropriate data structure definitions.

According to one embodiment the Lentils API reduces or eliminates the need for the software developer that is coding in the high level programming language environment to understand SQL. For example storable objects may be read from a database by the software developer creating an instance of a specific type of storable object called the pattern storable optionally associating data values with primitive attributes optionally creating and preparing a DBFilter and making the appropriate API call including the pattern storable and optionally the DBFilter. Within the API call appropriate DQEs are prepared based upon the state of the pattern storable and optional DBFilter thus abstracting the complexities of direct interfaces with the underlying storage system.

In the following description for the purposes of explanation numerous specific details are set forth in order to provide a thorough understanding. It will be apparent however to one skilled in the art that the embodiments of the present invention may be practiced without some of these specific details. In other instances well known structures and devices are shown in block diagram form.

Embodiments of the present invention include various steps which will be described below. Such steps may be performed by hardware components or may be embodied in machine executable instructions which may be used to cause a general purpose or special purpose processor programmed with the instructions to perform the steps. Alternatively the steps may be performed by a combination of hardware and software or firmware.

Embodiments of the present invention may be provided as a computer program product which may include a machine readable medium having stored thereon instructions which may be used to program a computer or other electronic devices to perform a process according to the methods and techniques described herein. The machine readable medium may include but is not limited to floppy diskettes optical disks CD ROMs and magneto optical disks ROMs RAMs EPROMs EEPROMs magnetic or optical cards flash memory or other type of media machine readable medium suitable for storing electronic instructions. Moreover embodiments of the present invention may also be downloaded as a computer program product wherein the program may be transferred from a remote computer to a requesting computer by way of data signals embodied in a carrier wave or other propagation medium via a communication link e.g. a modem or network connection .

While for convenience embodiments of the present invention are described with reference to a relational database and Java the present invention is equally applicable to various other databases and high level programming languages. For example the teachings herein are useful in connection with design and development of database applications involving object oriented databases extensible markup language XML databases and the like. Similarly various other high level languages may be employed to interface with Lentils such as current or future versions of C C C and the like. While the implementation specifics may vary conceptually the embodiments described herein would function in the same manner. While an intermediate layer interposed between a high level language and a database management system is a likely choice for implementation of embodiments of the present invention it is also contemplated that the mechanisms described herein could be incorporated into semantics of a high level language or incorporated into the database management system itself

Brief definitions of terms abbreviations and phrases used throughout this application are given below.

Each table has a set of ascendant tables which is a collection of table objects having an order corresponding to the levels of inheritance of the storable class to which the owning table is associated with. The first table in the set corresponds to the most significant super table.

The term COMMITTED generally refers to a state of a storable object that has been saved at least once before to the database.

The term COMMITTING generally refers to a state of a storable with respect to the database when the storable is undergoing transition. According to one embodiment if the full save cycle is successful the state of the storable will roll forward to COMMITTED.

The terms connected or coupled and related terms are used in an operational sense and are not necessarily limited to a direct physical connection or coupling.

The phrase database application generally refers to a software program that makes use of a database to store access and or manipulate information.

The phrase data definition expression or DDE generally refers to one or more language statements such as data definition language DDL statements that define structure or schema of a storage system.

The phrase data manipulation expression or DME generally refers to one or more language statements such as data manipulation language DML statements that are used to cause changes to a database. Exemplary DML statements include but are not limited to INSERT UPDATE and DELETE.

The phrase data query expression or DQE generally refers to one or more language statements such as data query language DQL statements that are used to extract information from a database.

According to one embodiment a dependent table is any table whose associated storable class contains a dependent relational attribute which includes but is not limited to parent and ForeignParent attributes.

Each table has a set of descendant tables which is a collection of table objects having an order corresponding to the levels of inheritance of the storable to which the owning table is associated with. The last table in the set corresponds to the most significant super table.

The term DELETED generally refers to a state of a storable with respect to the database when a full delete cycle has been completed on the storable.

The term DELETING generally refers to a state of a storable with respect to the database when the storable is undergoing transition. According to one embodiment if the full delete cycle is successful the state of the storable will roll forward to DELETED.

The phrases in one embodiment according to one embodiment and the like generally mean the particular feature structure or characteristic following the phrase is included in at least one embodiment of the present invention and may be included in more than one embodiment of the present invention. Importantly such phases do not necessarily refer to the same embodiment.

If the specification states a component or feature may can could or might be included or have a characteristic that particular component or feature is not required to be included or have the characteristic.

An object template generally refers to an instance of a specific type of object of the class desired to be retrieved from a storage system and having a state e.g. one or more data values that are used to extract matching objects from the storage system. An example of an object template is a pattern storable.

According to one embodiment an orphan table is used to create a sub query that identifies super records that are to be deleted. When a storable is deleted the records that are deleted are based on the data values associated with a storable s attributes and the class ID. When the records from a sub table are deleted there is no longer any information that might be necessary to identify which super records should be deleted. According to one embodiment a WHERE NOT IN clause is included in the Primary Key Specification PKS that identifies all still existing sub records and is then used in a NOT IN clause that identifies all the super records that are orphaned. This technique depends on the inclusion of a clause that binds the CLASS column to the class ID value of the storable that is being deleted.

A Primary Key Specification or PKS generally refers to a SELECT sub query which when executed returns a set of rows from a table containing only primary key data. According to one embodiment the structure of the PKS is as follows SELECT primary keys FROM tables WHERE matching record specification. If current table corresponds to a storable that extends some storable the PKS will include conditions where the primary columns of a sub table equal the primary columns of the super table. If the storable contains data values that are associated with primitive attributes via columns associated with the current table and super tables the PKS will include conditions where the columns must equal the data values in storable that are associated with the columns. If the orphan table is defined the PKS will include conditions where the primary columns from the super table are not in a list of existing records in the orphan table which is otherwise referred to as a sub table with respect to the previous iteration of the descendant tables. If the nested WHERE IN clause is defined it is included as an additional clause in the PKS.

The term programmatically generally refers to an automated process the steps of which are executed by one or more computer programs.

The phrase storage system generally refers to a data repository for persisting data. According to various embodiments of the present invention a storage system may be a relational database system RDBS an extensible Markup Language XML database an object oriented database or the like.

The term TRANSIENT generally refers to a state of a storable object that has never been saved to the database.

A software framework that intelligently and efficiently connects software applications to a database system is proposed. This intelligent connection simplifies some of the regular tasks that are commonly associated with designing and implementing database applications such as database modeling provisioning and providing for access and manipulation. These functions are artfully abstracted within Lentils to reduce the skill level required to develop database applications and allow potential reduction in headcount required to staff such development efforts.

On the computer runs an operating system such as UNIX Linux Windows etc. An application such as a database application or software application that relies upon a database to perform its tasks runs within the operating system and the operating system supports a set of database access and services such as a Java Database Connectivity JDBC API an Open DataBase Connectivity ODBC database API etc. which allows the application to create access and manipulate data within the database and otherwise interact with the database . A console input output I O interface and an Internet intranet I O interface facilitate interactions among the application and the console PDA and laptop computer .

Depending upon the particular implementation the application may be simple like an address book or complex for example an order entry application that automatically generates factory orders downloads instructions to machines and schedules production.

As explained above the application runs on the operating system which in turn runs on the computer . The application may interact with users using some form of input output I O through the console terminal connected directly to the computer or through other devices connected to a network such as the Internet a local intranet or both.

An exemplary computer system representing an exemplary computer with which various features of the present invention may be utilized will now be described with reference to . In this simplified example the computer system comprises a bus or other communication means for communicating data and control information and one or more processors such as Intel Itanium or Itanium 2 processors coupled with bus .

Computer system further comprises a random access memory RAM or other dynamic storage device referred to as main memory coupled to bus for storing information and instructions to be executed by processor s . Main memory also may be used for storing temporary variables or other intermediate information during execution of instructions by processor s .

Computer system also comprises a read only memory ROM and or other static storage device coupled to bus for storing static information such as instructions for processor s .

A mass storage device such as a magnetic disk or optical disc and its corresponding drive may also be coupled to bus for storing information and instructions.

One or more communication ports may also be coupled to bus for supporting network connections and communication of information to from the computer system by way of a Local Area Network LAN Wide Area Network WAN the Internet or the public switched telephone network PSTN for example. The communication ports may include various combinations of well known interfaces such as one or more modems to provide dial up capability one or more 10 100 Ethernet ports one or more Gigabit Ethernet ports fiber and or copper or other well known network interfaces commonly used in internetwork environments. In any event in this manner the computer system may be coupled to a number of other network devices clients and or servers via a conventional network infrastructure such as an enterprise s Intranet and or the Internet for example.

Finally removable storage media such as one or more external or removable hard drives tapes floppy disks magneto optical discs compact disk read only memories CD ROMs compact disk writable memories CD R CD RW digital versatile discs or digital video discs DVDs e.g. DVD ROMs and DVD RW Zip disks or USB memory devices e.g. thumb drives or flash cards may be coupled to bus via corresponding drives ports or slots.

An example application is introduced for purposes of explaining and illustrating how one embodiment of Lentils may be used and illustrating the advantages over traditional technologies. The example application is a web portal application. A web portal is an Internet or intranet application that limits user access to the application and further restricts user access to specific pages in the application.

A user interacts with the application using a web browser. To access the application the user must log in providing a domain name username and password. A user is a person that belongs to an organization and has access to the application.

The domain name is a simple word phrase or sequence of characters that uniquely identifies an organization the user belongs to. For example it may be the organization s Internet domain name.

An organization has many persons and demographic information. An organization may have multiple sub organizations. An organization has many page groups. Page groups are described later in this document.

A user is associated with a collection of page groups and has access to any page that belongs to the page groups in the collection. The application restricts the page groups a user may be associated with to the page groups belonging to the organization to which the user belongs.

The application monitors each time a user accesses the application by recording session information. A session begins when a user first logs in and lasts until the user logs out or times out.

The application provides features that are only available to a super user. A super user is a user and typically has the responsibility of interacting with the applications most critical features.

Depending upon the embodiment the information regarding relationships among the classes may be contained within the data structures representing the classes or may be provided via a separate configuration file. The configuration file may override or supplement relationships defined in classes or not otherwise provided by the classes.

Table 1 shows exemplary class definitions using pseudo code with syntax similar to that employed by Java or C . These classes contain example members and references for implementing the models shown in .

In the present example the application is required to persist and or otherwise save update read and delete objects the relationships between objects to a storage system and adhere to the implications of the relationships between the objects.

The storage system may be a relational database system RDBS an XML database an object oriented database or the like. Consistent with the intended purpose of this document this example is explained with reference to a relational database system. Those skilled in the art will be able to apply the teachings contained herein to other storage system environments.

This example has been described first with a generic description independent of the assumption that software would be used to implement the application but then quickly transitions from a generic description to UML diagrams to supporting classes. This progression occurs frequently in industry as applications are developed. However it is also a frequent occurrence that the progression starts with a generic description and transitions into a database design space involving entity relationship diagrams ERDs and a schema. Once these elements are stable then software is developed.

As described earlier in the background this leads to a problem frequently experienced in industry. Applications that are both database and software intensive typically require individuals who are skilled in database technology and individuals who are skilled in software development technologies.

Note that if the design of the application was initiated from a database design space the generic description would have to be augmented to support the relationship entities in the ERD . This is called artificial modeling and tends to make it more difficult to understand the design. Using a software centric design space the generic description uses natural modeling and is easier to understand.

Note that if a software developer initially developed the model from a generic description to a UML model to pseudo code some time and coordination must be given for the software developer to communicate the elements of the design to a database developer who then in turn after understanding the requirements creates a schema in agreement with the needs of the software developer. The information that must be communicated includes the content of the objects the relationships between the objects and any constraints associated with the contents and relationships.

It is not always obvious from the ERD or UML diagram what kind of dependencies exists between two primary entities. For example referencing compare the relationship between ACCESS and PAGE GROUP and ORGANIZATION and PAGE GROUP . Both of these relationships show an intermediate entity joining the two primary entities together. ORGANIZATION PAGEGROUPS joins ORGANIZATION and PAGE GROUP and ACCESS PAGEGROUPS joins ACCESS and PAGE GROUP . Structurally the joining entities ORGANIZATION PAGEGROUPS and ACCESS PAGEGROUPS are similar. However there are differences implied by the relationship that govern the dependencies between the data. When an Organization is deleted all Page Groups associated with the Organization should be deleted. When an Access is deleted its relationship to the Page Groups deleted but the Page Groups themselves should be left in tact.

What would be the benefits if the relationships and dependencies between classes could be annotated in a UML diagram and implemented as properties of the classes that embody the relationships and dependencies The information exchange between the software developer and the database developer could be conveyed programmatically.

Further if the creation of a storage structure or schema and query for and manipulation of the data uses some structured process or language the acts of creating the storage structure and querying and manipulating data could be programmatically automated based on the properties of the classes participating in the application.

Relational database systems use SQL to create structure and query and manipulate data and thus is a prime candidate for programmatically automating these processes.

Included herein are a number of sample scenarios and a corresponding description of actions that occur within the example application and supporting RDBS. The purpose is to provide a sense of the complexities involved in accommodating the rules that govern the relationships between the classes and the constraints of the underlying RDBS.

Software implements the requirements of the applications and is the means of accommodating the rules that govern the relationships between the classes and the constraints of the underlying RDBS. The software is implicitly complex. According to one embodiment Lentils may be employed to encapsulate the complexities. In the attached Appendix two techniques for implementing the scenario of saving and organization are compared. The comparison demonstrates at least some of the benefits of using Lentils.

In simple terms a database schema is a collection of database tables and columns. A schema is created by executing CREATE TABLE SQL statements. Other SQL statements may be used to establish indexes foreign key constraints and other constraints or structures.

In accordance with the present example application saving an organization follows a sequence that satisfies the constraints of the underlying database in accordance with the dependencies of the relationships and the intent of saving the state of an object. The order of the sequence will be noted in a lazy fashion.

An organization must be saved. If an organization has a parent organization the parent organization should be saved first. According to the present example the parent organization is saved in accordance with the sequences outlined in this section.

An organization s demographic should be saved before the organization is saved. If there are new relationships between organization and page groups the prior relationships between the organization and page groups are deleted.

Any page group in the prior relationships to organization that are not in the new relationships between organization and page groups are deleted.

The new relationships between organization and page groups are saved after the organization and page groups have been saved.

If there are new relationships between organization and persons the prior relationships between the organization and persons are deleted.

Any person in the prior relationships to organization that are not in the new relationships between organization and persons are deleted.

Each person in the new relationships between organization and persons are saved. The new relationships between organization and persons are saved after the organization and persons have been saved.

For each person being deleted if that person is a user the user is deleted before the person is deleted.

For each access that is deleted any session belonging to the access is deleted before the access is deleted.

For each access that is deleted the relationships between an access and page group is deleted before the access is deleted.

For each page group that is deleted the relationship between the page group and page descriptors are deleted before the page group is deleted.

For each access being saved if there are any sessions associated with the access the sessions are saved after the access is saved.

For each access being saved if there are any pages groups associated with the access the page groups and access are saved before the relationship between the access and page groups are saved.

Collections of data manipulation language DML SQL statements are used to cause the changes to the database. The DML statements may include among other statements INSERT UPDATE and DELETE.

In general if an object or corresponding record pre exists in the database the record is saved using an UPDATE SQL statement otherwise the record is saved using an INSERT SQL statement. Objects records are removed from the database using DELETE SQL statements.

This scenario provides an example where an object is reconstituted as a result of querying the database. In order to use the application a user must provide a username password and organization. The application verifies the user belongs to an organization and has access to the application.

The application reads exactly one Access object where an organization has the given domain name and the organization contains a person that is a user and the user has access having the given username and password.

This scenario provides an example of how an object is deleted and the complex actions that result. Deleting an organization must satisfy the constraints of the underlying database in accordance with the dependencies of the relationships and the intent of deleting an organization i.e. object . The order of the sequence will be noted in lazy fashion.

An organization is deleted. If the organization has any child organizations the child organizations are deleted first. According to the present example the child organizations are deleted in accordance with the sequence outlined in this section.

An organization s demographic profile is deleted after the organization is deleted. Before the organization is deleted its demographic profile should be referenced and cached by the application. The organization contains a reference to its demographic profile. The organization is removed from the database before the demographic profile is. The cached reference to the demographic profile is subsequently used to identify and delete the demographic profile.

Any person belonging to the organization is deleted. Before the organization is deleted each person should be referenced and cached by the application. The relationship information is deleted from the database before the organization is deleted. When person is deleted there are no inherent means to relate person to the organization. The cached reference to person is subsequently used to identify and delete the person.

For each person deleted the relationship between organization and person is deleted before organization and person are deleted.

For each person being deleted if that person is a user the user is deleted before the person is deleted.

For each access that is deleted any session belonging to the access is deleted before the access is deleted.

For each access that is deleted the relationships between an access and page group should be deleted before the access is deleted.

Any page group belonging to the organization is deleted. Before the organization is deleted each page group should be referenced and cached by the application. The relationship information is deleted before the organization is deleted. When page group is deleted there are no inherent means to relate page group to the organization. The cached reference to page group is subsequently used to identify and delete the page group.

For each page group deleted the relationship between organization and page group is deleted before organization and page group are deleted.

For each page group deleted the relationship between page group and page descriptor are deleted before the page group is deleted.

It is assumed that a new organization object was created that has multiple persons a demographic profile and multiple page groups. The person is a user that has access to the application and through that access is associated with the same page groups as the organization.

An understanding of how Lentils works begins with the storable class. According to one embodiment storable is a base class that is extended to implement data classes and is used to retain instances of primitive data and references to other storable objects corresponding to the requirements of a client application. In the example application ACCESS DEMOGRAPHIC ORGANIZATION PAGEDESCRIPTOR PAGEGROUP PERSON SESSION STATE SUPERUSER and USER are all data classes that are derived from storable.

Storable is used to retain instances of primitive data and references to other storable objects. According to one embodiment data values and references are retained in a collection where the data values and references are associated with static attributes or synergistic attributes that are properties of storable sub classes.

A storable sub class uses synergistic attributes to define its structure that includes primitive data relationships to other storable classes and other ancillary information that may be used to describe a relationship with a storage system. According to one embodiment of the present invention a synergistic attribute is a static property of a derived storable class and has one or more of the following characteristics 

Name Ancillary information providing an indication of the string expression that might be used to name an element within a storage system that corresponds to the attribute.

Size Ancillary information providing an indication of how much space should be allocated by the storage system to store values associated with the attribute.

AttributeProfile attributeProfile contains the ancillary information that may be used to describe a relationship with a storage system. This includes the following 

Relational Attribute According to one embodiment a special type of attribute is provided that is used to describe relationships between storable classes called relational. Relational attributes are recognized by the StorageAgent and are used to determine how the storage system should look and be constructed and how to interact with the storage system when saving reading and deleting object data. Relational attributes are defined in recognition of generic relationships found in a software object model and structural constraints of a storage system used in support of the software object model. Relational attributes may include but are not limited to the following 

A data structure or class e.g. a storable class that contains a parent attribute referencing another class is called the child of the referenced storable and the referenced storable is called the parent. The existence of a child storable is dependent on the prior existence of a parent storable. A child storable derives its primary identity from its parent.

A data structure or class e.g. a storable class containing a RecursiveParent attribute references itself through the RecursiveParent attribute. An instance of a storable class that contains a RecursiveParent attribute takes on a role of child to the storable referenced through the RecursiveParent attribute. If the AttributeProfile allows a null relationship a child storable may exist as whole without reference to a parent otherwise the existence of the child is dependent on the prior existence of a parent. In the example application ORGANIZATION has a recursive parent relationship to itself.

A data structure or class e.g. a storable class that contains a ForeignParent attribute referencing a different storable class is called a child and the referenced storable class is called the foreign parent. The existence of a child storable is dependent on the prior existence of its foreign parent storable. A child storable provides its own primary identity. In the described embodiment the child is intrinsically aware of the relationship to the foreign parent but the foreign parent is not. In the example application SESSION has a foreign child relationship to ACCESS.

A data structure or class e.g. storable class that contains a peer attribute referencing a different storable class is called the owner of a peer relationship to the referenced class. Storable objects with peer relationships may exist independent of each other. In the described embodiment all storables associated with a peer relationship provide their own primary identity. In the example application ACCESS owns a peer relationship to PAGEGROUP and PAGEGROUP owns a peer relationship to PAGEDESCRIPTOR.

RecursivePeer relationships differ from peer relationships because the storable class with the RecursivePeer attribute is both the owner and subject of the relationship. Storable objects with RecursivePeer attributes may reference themselves. Storable objects with RecursivePeer attributes may exist independent of each other. All storable objects associated with a RecursivePeer relationship provide their own primary identity.

A data structure or class e.g. a storable class that contains a children attribute referencing a different storable class is called the parent. Children relationships use a peer mechanism to implement the relationship and as such the parent is also the owner of the peer relationship and the child is the subject of the peer relationship. The existence of a child storable referenced by a parent storable is dependent on the existence of a parent storable. The child storable class provides their own primary identity. A child storable class is not intrinsically aware of its relationship to the parent storable class. In the example application ORGANIZATION is the parent in a children relationship to PERSON.

A data structure or class e.g. a storable class that contains a ForeignChild attribute referencing a different storable class is called the parent and the referenced storable class is called the foreign child. The existence of a foreign child storable is dependent on the prior existence of a parent. In the described embodiment a foreign child storable provides its own primary identification but the parent also contains the identity of its foreign child. The parent is intrinsically aware of the foreign child but the foreign child is not aware of its relationship to the parent.

A data structure or class e.g. a storable class that contains a Constant attribute referencing a different storable class considers objects of the referenced class constants. Instances of a storable class containing a Constant reference to a different class depend on the existence of the constant storable. The existence of a storable referenced through a Constant relationship is not dependent on the storable containing the Constant attribute. The storable containing the Constant attribute provides its own identity but also contains the identity of the constant storable. In the example application DEMOGRAPHIC has a constant relationship to STATE.

A data structure or class e.g. a storable class that contains an Extends attribute to a different class must literally extend the very same class. The storable that contains an Extends attribute is called an extended class or sub class. The class from which the storable class is extended is called the super class. In the example application USER extends PERSON and SUPERUSER extends USER.

If a set of rules governing the relationship within a class or between two or more classes is identified and the existing set of relational attributes which reflect governing rules do not accommodate the identified rules then a new relational attribute may be defined that reflects the governing rules. The Storage Agent is then extended or enhanced to accommodate and enforce the set of rules that govern the new relationship.

Table 2 illustrates exemplary Lentils classes that may be used in connection with the example application.

Given the description of storable attribute primitive and the various relational attributes exemplary Lentils storable classes for the example application are shown in Table 2. The classes shown in Table 2 assume the use of language reflection to obtain certain information. For example language reflection is used to determine that SUPERUSER extends USER and USER extends PERSON. The name of each of the attributes is set using language reflection using the member names associated with the attributes. In alternative embodiments language reflection need not be employed and various other methods can be used. Consider the following examples 

Later when describing the Schema class Schema obtains all attributes for a given storable sub class. The classes shown in Table 2 assume the use of language reflection to allow Schema to obtain this information. In alternative embodiments language reflection need not be employed. One technique may require all storables to declare an array containing references to all attributes. For example USER may include the following method to provide an array 

Also Table 2 illustrates how primitive attribute may be used. Other embodiments may be preferred. For example if STRING extends primitive then FIRST attribute in PERSON may be declared in the following way 

According to one embodiment a storage agent acts as an intermediary between storable classes storable objects and the storage system. The particular implementation of a storage agent varies and is dependent on the APIs or access mechanism provided by the storage system. DBAdmin is an instance of StorageAgent and serves an intermediary between storable classes and relational database systems RDBS . The DBAdmin object generates SQL programmatically and dynamically in accordance with its responsibilities as a storage agent and the actions of the client application.

According to one embodiment a relational database schema may be generated by invoking the create method of a DBAdmin object. Note that in this example it is assumed that the DBAdmin object implements StorageAgent. According to this example the creation of a DBAdmin object requires a username password and location for the database and a Schema object. The creation of a Schema object requires an array of storable classes that are used by the application. Therefore the DBAdmin uses a Schema that references the storable classes that are used by the application as illustrated below in Table 3.

In accordance with the present example when a Schema object is instantiated it creates for itself a collection of objects that are used to model the elements found in a database and the relationship between those elements and the storable classes participating in the application.

At block a storable class that is used in the assignment of primary keys is added to the collection of storable classes. The primary key storable PKey is used to record the values of primary keys that have been assigned automatically by Lentils during the runtime of the application.

At block each storable class in the array is prepared and sorted. Certain embodiments assume language reflection is used to specify various properties of the storable class. This includes an ancillary name of the storable class ancillary names of the attributes and information as to whether a storable sub class extends some other storable sub class. The array of storable classes is sorted according to dependent relationships. Storable classes may contain relational attributes. A storable class containing a relational attribute that references some other storable class is located after the referenced storable class.

In block for each storable class a table object is created. At decision block a determination is made regarding whether there are further storable classes to be processed. If so at block the table object is created for the next storable class. Details regarding table object creation are discussed below with reference to . Otherwise if a table object has been created for each storable class then processing continues with block .

At block table objects are retrieved. In block for each table object created any JoinTables associated with the table are created. At decision block a determination is made regarding whether there are further table objects to be processed. If so at block peer relationships are identified. Otherwise if all table objects have been processed then the processing flow continues with block .

For each peer relational attribute in a storable a JoinTable will be created. At decision block a determination is made regarding whether there are further peer relational attributes in the current storable to process. If so a JoinTable object is created at block . Details regarding JoinTable object creation are discussed below with reference to . Otherwise if all peer relational attributes in the current storable have been processed then processing continues with decision block .

At block the tables are made aware of their relationship to other tables. According to one embodiment awareness includes knowledge of what tables are peers providers dependents ascendants and descendants.

If the table is not a root extension then at block for each primary column associated with the super table a reference column is created with a foreign key reference to the super column.

At block the attributes are obtained. In block the attributes obtained for the specific storable class are iterated over. At decision block a determination is made with regard to whether all attributes have been processed. If more attributes remain to be processed the processing continues with decision block otherwise processing is complete.

At decision block the attribute type is determined. If the attribute is of type Name then the name of the table is assigned at block .

If the attribute is of type primitive then at block a column is created and assumes the properties of the attribute and AttributeProfile. This includes the name of the column size if applicable whether it is primary unique or nullable.

If the attribute is one of the following provider types Parent Constant ForeignParent or ForeignChild then at block for each primary column associated with the provider table a reference column is created with a foreign key reference to the provider column.

At block the peer attribute is obtained. At decision block the attribute type is determined. If the peer attribute is of type RecursivePeer then at block for each primary column associated with the owner table a left and right column is created. Each of the left and right columns contain a foreign key reference to the provider column. According to one embodiment for RecursivePeer columns the name of the left column is the concatenation of the owning table name an underscore the name of the peer column an underscore and the letter L . Similarly according to one embodiment for RecursivePeer columns the name of the right column is the concatenation of the owning table name an underscore the name of the peer column an underscore and the letter R .

For all other or simple peer attributes at block for each primary column associated with the owner table a left column is created and contains a foreign key reference to the provider column. For each primary column associated with the peer table a right column is created and contains a foreign key reference to the provider column. By convention in the present example the name of a simple peer column is the concatenation of the provider column s table name an underscore and the name of the provider column. In alternative embodiments other conventions may be employed for establishing the name of a peer column.

The process begins at block by creating a SQL cache or FIFO. This cache is used to store SQL statements in the order they were placed into the cache.

At block the process of generating SQL statements is performed. Details regarding the generation of the create schema SQL sequence are discussed below with reference to . Upon completion of block the cache contains a collection of SQL statements.

In this example in block each SQL statement in the cache is then executed in the order the statements were place in the cache. At decision block a determination is made regarding whether additional SQL statements remain in the cache to be executed. If one or more SQL statements remain in the cache then at block the next SQL statement is executed. If no further SQL statements remain in the cache then processing is complete.

While in the above example all SQL statements are cached in a FIFO in the natural order as a particular action such as creating deleting and saving an object propagates through data and relationships according to an appropriate algorithm in alternative embodiments one or more SQL statements may be executed out of this natural order and or without adding them to the FIFO. For example one or more SQL statements in the FIFO may be executed before completing the propagation. Additionally any SQL statement generated as part of the action that does not present a dependency on the generation of subsequent SQL or the effect of such subsequent SQL can be executed without being added to the FIFO cache and any series of SQL statements contained in FIFO that do not present a dependency on the generation of subsequent SQL or the effect of such subsequent SQL can be executed without completing the propagation.

At block all tables are obtained. In block all tables are iterated over. At decision block a determination is made regarding whether all tables have been processed. If one or more tables remain to be processed at block generation of the appropriate sequence of one or more SQL statements for is started. According to one embodiment the name of the table is used to define the table name in a CREATE TABLE SQL statement.

A table has columns. For each column associated with the table a column definition is added to the CREATE TABLE statement. At block the columns associated with the table are identified.

In block all columns of the current table are iterated over. At decision block a determination is made regarding whether one or more columns of the table remain to be processed. If one or more columns of the table remain to be processed at block the column definition is included within the CREATE TABLE definition. A column has characteristics that include name data type size primary unique null and foreign references. Each of these characteristics is manifested in the CREATE TABLE definition by some means. The exact syntax of the definition varies depending upon the vendor of the database system in use. If supported by the database vendor for each column that is a primary key the column definition will include an expression defining the column as a primary key. Some database vendors do not support the definition of a primary key using this technique. For those vendors additional SQL is included in the cache during the post table create process .

The use of post table create step depends on the type of database vendor in use. For example some database vendors prefer primary key definitions to be declared outside the CREATE TABLE statement. For those vendors this section may create and cache a CREATE INDEX statement. Additionally other database vendors may have their own unique syntax or variation that may be supported by embodiments of the present invention.

For example when provisioning the primary key column ID in table ACCESS. The following DDL statements illustrate the same effect for different database vendors.

Or when provisioning primary key column ACCESS in table SESSION having a foreign key reference to column ID in ACCESS the following DDL statements illustrate the same effect for different database vendors 

In similar ways by specifying implicit explicit and ancillary properties of storable classes and their attributes i.e. primitive and relational appropriate data definition expressions DDE are programmatically generated containing proper syntax for a given database vendor. The DDE are used to provision elements of a schema including but not limited to tables columns column data types column size and integrity constraints including but not limited to primary keys unique keys foreign keys and whether null values are allowed and performance characteristics including but not limited to indexes.

Regardless of the database vendor the creation of a table includes the appropriate combination of SQL statements to create a table assign indexes to the columns having primary keys and declare foreign key references to provider columns. At block once all columns have been processed the appropriate combination of SQL statements generated by blocks are cached in the FIFO for subsequent execution. At block optional post TABLE CREATE SQL statements are cached in the FIFO for execution.

In this example the structural relationship for a primitive attribute is illustrated in each of application space Lentils space and database space . Application space refers to the context or perspective of a database application e.g. a software application that utilizes Lentils to facilitate access to a database system. Lentils space refers to the context or perspective of the Lentils software. Database space refers to the context or perspective of the database system e.g. an RDBS.

In application space a database application not shown has created an instance A of a storable class not shown . The storable class included a primitive attribute primitive . Lentils space programmatically receives the definition of the storable class from the database application via DBAdmin an instance of a StorageAgent . In Lentils space the storable object A is represented as a table table A having a column corresponding to primitive . Database space creates a table object table A having a column reference column responsive to appropriate instructions e.g. one or more SQL statements or storage system API calls by Lentils software.

In the present example in application space storable class B extends a storable class A having primitive attribute primitive . In Lentils space this is represented in an intermediate form as a first table object table A corresponding to storable class A having a column reference and a second table object table B corresponding to storable class B having a column reference .

Finally in database space two tables table A and table B corresponding to table A and table B respectively are created. An extended column corresponding to column reference is created in table which contains a foreign key reference to a primary column super column of table A corresponding to the column reference .

In the present example in application space a parent attribute of a storable class B references a storable class A which has a primary primitive attribute . In Lentils space this is represented in an intermediate form as a first table object table A corresponding to storable class A having a column reference and a second table object table B corresponding to storable class B having a column reference .

Finally in database space two tables table A and table B corresponding to table A and table B respectively are created. A column is created in table that contains a foreign key reference to a primary column super column of table A corresponding to the column reference .

In the present example in application space a storable class A has a RecursiveParent attribute and a primary primitive attribute . In Lentils space this is represented in an intermediate form as a table object table A having a first column reference corresponding to the primary primitive attribute and a second column reference corresponding to the RecursiveParent attribute .

Finally in database space a table A is created having a primary column corresponding to column reference and a recursive column corresponding to column reference . The recursive column contains a foreign key constraint to the primary column .

In the present example in application space a Foreign Parent Foreign Child or Constant attribute of a storable class B references a storable class A which has a primary primitive attribute . Storable class B also has a primary primitive attribute . In Lentils space this is represented in an intermediate form as a first table object table A corresponding to storable class A having a column reference and a second table object table B corresponding to storable class B having a first column reference corresponding to the Foreign Parent Foreign Child or Constant attribute and a second column reference corresponding to the primary primitive attribute .

Finally in database space two tables table A and table B corresponding to table A and table B respectively are created. A column is created in table A corresponding to the column reference . A first column is created in table B corresponding to the column reference and a reference column is created in table B that contains a foreign key constraint to column .

In the present example in application space a peer or children attribute of a storable class B references a storable class A which has a primary primitive attribute . Storable class B also has a primary primitive attribute . In Lentils space this is represented in an intermediate form as a first table object table A corresponding to storable class A having a column reference corresponding to the primary primitive attribute a second table object table B corresponding to storable class B having a first column reference corresponding to the primary primitive attribute and a third table object JoinTable BA having a first column reference corresponding to column reference and a second column reference corresponding to column reference .

Finally in database space three tables table A table B and table BA corresponding to table A table B and JoinTable BA respectively are created. A column is created in table A corresponding to the column reference . A column is created in table B corresponding to the column reference . A first column is created in table BA with a foreign key constraint referencing column of table B and a second column is created in table BA with a foreign key constraint referencing column of table A .

In the present example in application space a storable class A has a recursive peer attribute and a primary primitive attribute . In Lentils space this is represented in an intermediate form as a table object table A having a column reference corresponding to the primary primitive attribute and a join table object JoinTable AA corresponding to the recursive peer attribute having a left column reference i.e. column L and a right column reference i.e. column R both referencing column reference .

Finally in database space two tables table A corresponding to table A and table AA corresponding to JoinTable AA are created. A column is created in table A corresponding to column reference . A left column is created in table AA corresponding to left column reference and having a foreign key constraint referencing column in table A . A right column is created in table AA corresponding to right column and having a foreign key constraint referencing column in table A .

The process begins at block where a SQL cache or FIFO is created. This cache is used to store SQL statements in the order they were placed into the cache.

At block the process of generating SQL statements to save the storable is performed. Details regarding generation of data manipulation language statements to save the state of a storable object are discussed below with reference to . Similar statement generation methodologies may be employed for other forms of data manipulation expressions.

After block the cache contains a collection of SQL statements and each SQL statement in the cache is executed in the order the statements were place in the cache. At decision block a determination is made regarding whether more SQL statements remain in the cache. If so at block the next SQL statement is executed. Otherwise if there are no further SQL statements in the cache to be executed then processing continues with block where the rollback states of the storables are set to COMMITTED.

At block the process begins by obtaining a set of ascendant tables for the current storable. The current storable is of a certain type and Schema maps the class type to the table.

The ascendant tables are iterated over. The current table corresponds to the table of a given iteration cycle. At decision block a determination is made regarding whether more ascendant tables remain to be processed. When all ascendant tables have been processed processing branches to block where the rollback state of the current storable is set to COMMITTING.

If one or more ascendant tables remain to be processed then at block the provider relationships are traversed. According to one embodiment a provider has its records manipulated before any dependent records are manipulated to satisfy foreign key constraints. Details regarding provider traversal processing are discussed below with reference to .

At decision block a determination is made regarding whether the current table is the first table in the ascendant collection. If the current table is the first table in the ascendant collection then the current storable is prepared at block . After block and for each subsequent table in the ascendant collection processing continues with block .

At block the current storable is persisted. Persisting a storable may result in the creation of an INSERT or UPDATE SQL data manipulation language statement depending on the state of the storable. Details regarding processing relating to persisting a storable are discussed below with reference to . Similar persisting processing statement generation methodologies may be employed for other forms of data manipulation expressions.

At block peer relationships are traversed. Details regarding processing relating to peer relationship traversal are discussed below with reference to .

At block all provider attributes for the current table are obtained. The attributes are only those that belong to the specific storable class corresponding to the current table. All provider attributes are then iterated over.

In block all attributes are iterated over. At decision block a determination is made regarding whether all attributes have been processed. If one or more provider attributes remain to be processed then processing continues with block where the provider storable for the current storable is obtained. At decision block a determination is made regarding whether the current storable has a provider storable. If so the provider storable is saved at block . As above the current SQL cache is used to collect SQL statements necessary to save the provider storable. If the current storable does not have a provider storable then processing continues with decision block .

At block all primitive attributes that represent primary values are obtained. In block the primary primitive attributes are iterated over.

At decision block a determination is made regarding whether there are additional attributes to process. If so it is determined at decision block whether a value is assigned to the next attribute. If a value is not assigned to the attribute then at block a unique value is obtained and associated with the attribute. According to one embodiment DBAdmin tracks the next values to be assigned to an attribute that serves as a primary key. Next values are cached in association with PKey storable objects. The PKey storable contains attributes associated with a table column and a range of values. When DBAdmin assigns all the values from the range of values the PKey storable s range of values is advanced and the PKey storable is saved. DBAdmin saves PKey storables so that if the application is restarted DBAdmin initializes its next values from the records associated with PKey and is guaranteed to assign unique values.

Using this technique the storable s primary values that uniquely identify the storable are guaranteed to be available to the application immediately after the storable has been saved.

Once the current storable s primary key values have been fully assigned the SQL necessary to persist the current storable can be generated.

At decision block a determination is made regarding the state of the current storable. If the state of the current storable is TRANSIENT then at block the data values are stored using an INSERT SQL statement. The INSERT is created and placed into the SQL cache.

If the state of the current storable is COMMITTED then at block the data values are stored using an UPDATE SQL statement. The UPDATE is created and placed into the SQL cache.

If the current storable has any state other than TRANSIENT or COMMITTED no SQL will be generated or cached.

At decision block a determination is made regarding whether more attributes remain to be processed. If so then processing continues with decision block . At decision block a determination is made regarding whether peer storables are defined. The current peer attribute is skipped if peer storables are not defined or otherwise specified.

At decision block a determination is made regarding whether the attribute is of type children. If the attribute is of type children then the update process for children is performed at block .

At block the peer storables associated with the current peer attribute are obtained from the current storable. In block the peer storables obtained are iterated over. The current peer storable corresponds to the peer storable of a given iteration cycle. At decision block a determination is made regarding whether more peer storables remain to be processed. If so the current peer storable is saved at block . According to one embodiment because of foreign key references in the join table all peer storables are first saved in the database. The current SQL cache is used to collect the SQL necessary to save the current peer storable.

Once the SQL cache includes statements to persist the collection of peer storables a DELETE is created and added to the cache at block . The DELETE will remove all current existing records from the join table where the columns in the join table corresponding to the current peer attribute contain rows corresponding to the current storable s primary data values.

At block the peer storables associated with the current peer attribute are obtained from the current storable. In block the peer storables associated with the current peer attribute are iterated over. The current peer storable corresponds to the peer storable of a given iteration cycle.

At decision block a determination is made regarding whether further peer storables associated with the current peer attribute remain to be processed. If so at block an INSERT is created and added to the SQL cache that records in the join table the relationship between the current storable and the current peer storable.

At the end of the peer traversal process the SQL cache contains statements that will result in the replacement of prior relationships to the current storable with the current specified peer relationships.

At block the current children storables collection is obtained. At block the children storables that are not part of the current specified collection are read.

In block each storable read is deleted. At decision block a determination is made with regard to whether more storables remain to be deleted. If so at block the next storable is deleted.

The process begins at block by creating a SQL cache or FIFO. This cache is used to store SQL statements in the order they were placed into the cache.

At block the process of generating SQL statements to delete the storable is performed. Details regarding generation of data manipulation language statements to delete a storable object are discussed below with reference to . Similar statement generation methodologies may be employed for other forms of data manipulation expressions.

In block each SQL statement in the cache is executed in the order the statements were place in the cache. At decision block a determination is made regarding whether more SQL statements remain to be executed. If so at block the next SQL statement form the cache is executed. When execution of all SQL statements from the cache has been completed processing continues with block where the rollback state of the current storable is set to DELETED.

At block the set of ascendant tables for the current storable is obtained. The storable is of a certain type and Schema maps the class type to the table.

In block the ascendant tables are iterated over. The current table corresponds to the table of a given iteration cycle.

At decision block a determination is made regarding whether there are more tables to process. If so then at block the Primary Key Specification PKS is pushed onto the PKS Stack a new PKS is created the orphan table is assigned and a DELETE is created and retained for later inclusion in the SQL cache. The DELETE matches the primary keys of the current table to the current PKS.

At block the RecursiveParent relationships are updated. Details regarding processing associated with updating RecursiveParent relationships are discussed below with reference to .

At block dependent relationships are updated. These include parent and ForeignParent relationships. Details regarding processing associated with updating dependent relationships are discussed below with reference to .

At block peer relationships are updated. Details regarding processing relating to peer relationship traversal are discussed above with reference to .

At block ForeignChildren relationships are updated. Details regarding processing associated with updating ForeignChildren relationships are discussed below with reference to .

At block the previous PKS is popped off the PKS Stack and descendant table iteration continues with decision block .

As some databases do not support self referencing sub queries an alternate technique for generating a collection of SQL statements to delete a storable and its corresponding records is also provided. According to this alternative technique rather than using a hierarchy of nested SELECT sub queries to identify affected records the PKS of this algorithm does not use self referencing sub queries and emphasizes the use of primary key values to identify affected records.

According to the alternate technique that emphasizes the use of primary key values to identify affected records the following processing is substituted for that described above with reference to block . The current Primary Key Specification is pushed onto a PKS Stack and a new PKS is generated that contains a list of primary key values corresponding to the records to be deleted in the current table. If the current table is the super table the PKS primary key values are obtained using a SELECT statement based on the data values associated with the storable being deleted. The storable class may consist of multiple levels of inheritance and the storable being deleted may have data values associated with inherited tables. If so the SELECT statement that retrieves the primary key values includes terms to bind the data values to their respective columns and tables and terms to bind the primary columns of a sub table to the primary columns of the super table. If the current table is not the super table then the new PKS is generated binding the values of the previously saved PKS to the primary columns of the current table. A DELETE statement is created and retained for later inclusion in the SQL cache. When executed the DELETE statement will remove all records from the current table whose primary key values are included in the PKS.

At block all RecursiveParent attributes are obtained for the current table. In block all obtained RecursiveParent attributes are iterated over. At decision block a determination is made regarding whether more attributes remain to be processed. If so processing continues with decision block .

At decision block a determination is made regarding whether the attribute allows a null reference. If so at block an UPDATE is created and cached that sets the foreign key references in the child records to NULL.

If however the attribute does not allow a null reference then at block all child storables of the current storable are read.

In block each child storable read is deleted. The current SQL cache is used to collect the SQL necessary to delete each storable read. At decision block a determination is made regarding whether more storables remain to be deleted. If so at block the SQL statements for deleting the next storable are stored in the current SQL cache.

At block the current table s dependent tables are obtained. In block the dependent relationships obtained are iterated over. At decision block a determination is made regarding whether more dependent relationships remain to be processed. If so at decision block a determination is made regarding whether the AttributeProfile allows a null reference. If so at block an UPDATE is created that sets the foreign keys of the dependent records to NULL.

If the AttributeProfile does not allow a null reference then at block a nested WHERE IN clause is pushed onto a stack and a new nested WHERE IN clause is created.

The nested WHERE IN clause is an expression where the foreign key columns of the dependent table are in the set of values implied by the current PKS. Note in the context of this step the PKS is a SELECT sub query that represents the rows of primary columns from the current a.k.a. parent or provider table are affected by the delete operation. Therefore the nested WHERE IN clause will be used to identify the affected records in the dependent table across the relationship. The nested WHERE IN clause identifies records in all tables that are related to the dependent table through inheritance relationships of the dependent table s associated storable class.

According to the alternate technique that emphasizes the use of primary key values to identify affected records the following processing is substituted for that described above with reference to block . The PKS for the current table is pushed onto the PKS Stack and a new PKS is created containing primary key values identifying records to be deleted from all tables associated with the dependent relationship. The primary key values for the new PKS are obtained using a SELECT statement containing terms that binds the primary key values of the saved PKS to the foreign columns of the dependent table and binds the primary columns of all tables in the dependent inheritance hierarchy to the primary columns of their super table and returns primary key values from the dependent table s root table.

At block the extensions of the dependent table are traversed and updated. Details regarding processing associated with extension traversal are discussed below with reference to .

At block the nested WHERE IN clause is popped off the stack and dependent table iteration processing continues with decision block . Alternatively if the primary key value based on the PKS is being used then the previously saved PKS is popped off the PKS Stack.

At block the table extensions for the dependent table are obtained. In block the table extensions obtained are iterated over. At decision block a determination is made regarding whether more table extensions remain to be processed. If so at block inheritance a specific storable class has extending from storable and containing attributes there is a corresponding table.

Blocks and are performed in application space. At block the pattern storable is prepared. At block an optional DBFilter is prepared.

At block the table corresponding to the pattern storable is obtained. At block all columns are obtained for the table corresponding to the pattern storable. All columns include the columns from the related super tables.

In block the columns are iterated over. At decision block a determination is made regarding whether more columns remain to be processed. If so processing continues with decision block .

At decision block it is determined if the column is a sub column. If the column is a sub column having a foreign key reference to its super column then at block a WHERE EQUAL clause is added to the DBFilter that binds the sub column to the super column.

At decision block it is determined if the column corresponds to a primitive attribute and if the pattern storable contains a data value associated with the primitive attribute. If so then at block a WHERE EQUAL clause is added to the DBFilter that binds the column corresponding to the primitive attribute to the data value.

Once all columns have been iterated over at block the rows are read using the class corresponding to the pattern storable called the pattern class and the DBFilter. The result set of the database read operation creates a collection of storables that are returned to the application.

At block the SELECT is executed and a result set is obtained. In block the result set is iterated over. At decision block a determination is made regarding the current storable is pushed onto a stack. Additionally a new default current storable is created from the extended table. The table is aware of its storable class and using this knowledge a default storable may be created. The newly created storable has no data values associated with it other than its class ID. Note that at this step the nested WHERE IN clause sufficiently identifies affected records in the dependent table which then will be used to identify records in the extended table.

At block the current default storable is deleted. The current SQL cache is used to collect the SQL necessary to delete the default storable.

At block the current storable is popped off the stack. The current orphan table is also popped off the stack. Then table extension iteration processing continues with decision block .

Alternatively if the primary key value based on the PKS is being used then the current table is pushed onto a stack. The table extensions for the dependent table are obtained. The table extensions are iterated over. A determination is made regarding whether more table extensions remain to be processed. If so the extended table is assigned as current table and delete processing continues at block .

At block ForeignChild attributes are obtained from the current table. At block all the parent storable records are read using the PKS. The parent storables intrinsically contain all child proxy storables.

In block The ForeignChild attributes are iterated over. At decision block a determination is made regarding whether more ForeignChild attributes remain to be processed. If so for each parent storable and ForeignChild attribute the corresponding child storable is deleted. At decision block a determination is made regarding whether parent storables remain to be processed.

If one or more parent storables remain to be processed then at block the ForeignChild proxy is obtained from the next parent. At block The current SQL cache is used to collect the SQL necessary to delete the ForeignChild proxy storable.

Alternatively using value based PKS ForeignChild attributes are obtained for the current table. All ForeignChild attributes are iterated over. A determination is made regarding whether more ForeignChild attributes remain to be processed. If so the current PKS is pushed onto the PKS Stack and a new PKS is created containing primary key values identifying records to be deleted from the tables associated with the ForeignChild attribute. The primary key values for the new PKS are obtained using a SELECT statement containing terms that binds the primary key values of the saved PKS to the foreign columns of the ForeignChild table and binds the primary columns of all tables in the ForeignChild inheritance hierarchy to the primary columns of their super table and returns primary key values from the ForeignChild table s root table. The extensions for the corresponding ForeignChild table are traversed and updated. Using value based PKS the previously saved PKS is popped off the PKS Stack.

At block all columns are obtained for the table corresponding to the pattern class. In block the columns obtained for the table corresponding to the pattern class are iterated over. At decision block a determination is made regarding whether more columns remain to be processed.

If more columns remain to be processed then at decision block it is determined whether the column is a sub column. If so then there is no data in the result set and the column is ignored as a sub column references the same information that is associated with a super column. The super column will contain the necessary information.

At decision block it is determined if the result set for the column is null data. If so then the column is ignored.

At decision block it is determined if the column represents the CLASS column. If so then a new storable is created of a type corresponding to the class associated with the class ID data. The new storable is of the correct type when the original storable was last saved.

At decision block it is determined if the column is a reference column. If the column is a reference column then the column references a primary key component of another storable object. At decision block it is determined if a proxy storable exists. If the current storable contains a storable object associated with the attribute corresponding to the column then the data value is assigned to the referenced storable object. Note that this referenced storable object is called a proxy because it will contain primary identification data values and will be of the correct type corresponding to the relational attribute but will not contain full data values and may not be the correct class type with respect to inheritance. Thus it is only a proxy.

If a proxy storable does not exist then at block a proxy storable is created based on the class type associated with the table that the reference column belongs to. This proxy is then associated with the relational attribute of the current storable.

If the column corresponds to a primitive attribute then at block the data value or the result set is associated with the primitive attribute of the current storable.

In the foregoing specification the present invention has been described with reference to specific embodiments thereof. It will however be evident that various modifications and changes may be made thereto without departing from the broader spirit and scope of the invention. The specification and drawings are accordingly to be regarded in an illustrative rather than a restrictive sense.

