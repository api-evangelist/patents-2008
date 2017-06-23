---

title: Case management system
abstract: A content management system is disclosed for documents and other content for a system operating in legal environment referred to herein as a case management system. The case management system allows attorneys in a legal environment to efficiently store and manage content for their client and case matters. Furthermore, the system encourages attorneys to collaborate with fellow co-workers, clients, and third parties (e.g. expert witnesses) in a secure and confidential environment. The case management system enables attorneys to maintain case files and associated documents more efficiently and thus allow law firms to more productively function as a business that relies heavily upon comprehensive document files.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09224132&OS=09224132&RS=09224132
owner: Leydig, Voit & Mayer, Ltd.
number: 09224132
owner_city: Chicago
owner_country: US
publication_date: 20080204
---
This patent application claims the benefit of U.S. Provisional Patent Application No. 60 887 906 filed Feb. 2 2007 which is incorporated by reference in its entirety including any references contained therein.

The field of the invention is computer systems in general and more particularly content management systems.

In today s modern business world the key to productivity for businesses is their ability to efficiently store manage and reuse information content and work product. Each business has challenges in managing content. Challenges include having a reliable efficient and intuitive organizing system. Also content management systems should accurately handle version control such that the most current version of a document is used for customer correspondence supply purchases or co worker collaboration. Furthermore content management systems not only file documents but also store content of differing media from video to photographs to audio files. Finally a content management system is not merely an electronic file cabinet that employees use to search and retrieve files but a digital vault that secures confidential content from customers suppliers or fellow workers.

A content management system should be easy to use such that a company s employees should only have a short learning curve so as to not lose their productivity. In addition the content management system should make typical tasks more efficient making it worth the investment in time and money for businesses. For example the e mailing of documents as attachments to e mail messages should not be inhibited when sending these same documents from a content management system. No business can trade a content management system for less efficient means for producing daily work product.

In a legal environment content management can be more challenging than other traditional businesses. Attorneys collaborate with each other as well as with clients and third parties e.g. expert witnesses . Due to the nature of the relationship between attorneys and their clients work product and content are kept confidential. Consequently a content management system in a legal environment should provide security and confidentiality among a group of users. Furthermore attorneys strive for efficiency and productivity. Therefore a content management system should be efficient and yield higher productivity for a firm than without investing in a system. Consequently a system should be easy to use and efficiently perform typical tasks in a legal environment. At the same time a system should provide a productive means to collaborate with client third parties and fellow attorneys. Finally a content management system should be compatible with typical daily document processes in a law firm.

The present invention and its embodiments disclose a content management system for documents and other content for a legal environment called a case management system. It allows attorneys in a legal environment to efficiently store and manage content for their client and case matters. Furthermore the system encourages attorneys to collaborate with fellow co workers clients and third parties e.g. expert witnesses in a secure and confidential environment. The case management system enables attorneys to be more efficient individually and allows law firms to be more productive as a business.

A content management system described in this specification contains several components and provides several functions. Components of a content management system include a user interface a web server a document management system an administration utility custom and default templates content data structure a database a document extractor and an e mail publisher. Extension to a base content management system include an integrated administration utility and pre defined templates custom and default . These additions are integrated through an application programming interface API and software development framework SWDF to create content specific to the business using a content management system. Further enhancements include a document extractor utility integrated with a document management system through an API and SWDF to allow users easier access to content from a system. An additional enhancement is an e mail publisher that allows a user to easily store content from an e mail program into a content management system.

The extended document manage system is suitable for a variety of environments. For example in a law firm environment users create and manage content specific to the law firm s client and cases. An exemplary embodiment is directed to a law firm environment alternative embodiments include an administration utility and default and custom templates that support a variety of business enterprise classes including manufacturing banking investing consulting marketing advertising etc. Any business that creates stores and manages content is able to utilize an alternative embodiment.

At the top level of the database tree structure is a Case Management Top Level Data Structure . When accessed by the user interface See it is displayed as a Case Management System Home Page See . The next level of the database tree structure contains both Opinion Top Level and Litigation Top Level data structures . Similar to the system top level these data structures when accessed by the user interface are displayed as a Prosecution Opinion Home Page and a Litigation Home Page respectively See . The next level of the data tree structure underneath a Prosecution Opinion data structure is a level of client data structures . Each client data structure contains case data structures and underneath it corresponding to each opinion matter for the client. Finally the bottom level of the tree structure contains data structures for each case. The bottom level includes data structures that contain official papers and correspondence . Again each data structure when accessed by the user interface is displayed as web pages or web sites. Underneath a Litigation data structure are Litigation matter data structures and . Litigation matter data structures and contain content for each litigation matter stored in the system See . Underneath each Litigation matter data structure and are content data structures typically needed in any litigation. These include Pleadings Discovery and Memoranda data structures. Again each data structure when accessed by the user interface is displayed as web pages or as web sites. The Pleadings Discovery and Memoranda data structures within the Litigation Top Level portion of the database tree are at the same level of the data structure tree as the case sites and in the Prosecution Opinion Top Level portion of the database.

Once data is entered a user has the option to attach a file to the information via an attach file link or simply save the data and close the web page to initiate a new client site creation process via the save and close link . is a general overview of the operation of a system contemplated by an exemplary embodiment. A logged on user Joe Smith through a personal computer creates a new client site by accessing a New Client Site Request New Item Page See . As previously discussed the user interface See is presented by the system web server . After a user Joe Smith enters necessary information into the user interface a user saves information via a save push button to initiate creation of a client site. For the case management system to create a new client site the web server takes the information gathered by the New Client Site Request New Item Page and sends the information to the document management system . Next the document management system prompts the administration utility to create a new client data structure using the custom and default templates . Once the administration utility and templates and create a new client data structure the system stores the new client data structure into its database . A user Joe Smith accesses the new client data structure through the user interface to create and manage content. Some capabilities offered by the system for a client site include storing client documents and client contacts . The new client site also lists cases and a group of site users for a client. Finally the user interface allows a user to extract documents from the case management system .

An example of a user interface to a new client site is displayed in . is a diagram of an exemplary user interface of a Client Site Home Page . Similar to the general overview diagram presented in the user interface See provides access to client documents client contacts and client case information . The Client Site Home Page also lists a group of site users and provides a link to the document extractor for a user to access client content from the case management system See .

The following tables list the attributes and method functions that use the document management system s See application programming interface and the .net and asp.net software development framework.

Table 1 lists exemplary attributes for certain user interface features i.e. textboxes error dialog boxes etc. when a user add a new client into the case management system.

Table 2 lists exemplary method functions that are invoked when a user adds a client to the case management system across a user interface. For example the CreateSiteUsingAdminSrvc method creates a client site using the Admin Utility. A further example is the RegisterinSite Directory method which registers the new client site into the data structure of the database.

Table 3 lists exemplary attributes that provide user interface features when a user adds a case into the case management system.

Table 4 lists exemplary method functions that are invoked when a user adds a case to the case management system across a user interface. For example the CreateSubSite method creates a client site using the Admin Utility. A further example is the RegisterinSite Directory method which registers the new case site into the data structure of the database.

Table 5 lists exemplary attributes that provide user interface features when a user adds an opinion case into the case management system.

Table 6 lists exemplary method functions that are invoked when a user adds an opinion case to the case management system across a user interface.

Table 7 lists exemplary attributes that provide user interface features when a user adds a litigation case into the case management system.

Table 8 lists exemplary method functions that are invoked when a user adds a litigation case to the case management system across a user interface.

Table 9 lists exemplary method functions that are implemented to add a user to the case management system.

Table 10 lists exemplary attributes that provide user interface features when a user is interfacing with the Admin Menu.

Table 11 lists exemplary method functions that are implemented when the user is interfacing with the Admin Menu.

Table 12 lists exemplary attributes for the clients data structure within the case management system.

Table 13 lists exemplary method functions for the clients data structure within the case management system.

Table 14 lists an exemplary attribute for Data Access Object DAO that performs database transactions within the case management system.

Table 15 lists exemplary method functions for Data Access Objects that performs database transactions within the case management system.

Table 18 lists exemplary attributes that are used to impersonate a login user within the case management system.

Table 19 lists exemplary method functions that are used to impersonate a login user within the case management system.

Table 20 lists exemplary attributes that are used to determine an unauthorized user of the case management system.

Table 21 lists exemplary method functions that are used to determine an unauthorized user of the case management system.

Table 22 lists exemplary attributes that are used to view cases across a user interface within a case management system.

Table 23 lists exemplary method functions that are used to view cases across a user interface within a case management system.

Table 24 lists exemplary attributes that are used to view clients across a user interface within a case management system.

Table 25 lists exemplary attributes that are used to view clients across a user interface within a case management system.

Table 26 lists exemplary attributes that are used to view litigation cases across a user interface within a case management system.

Table 27 lists exemplary method functions that are used to view litigation cases across a user interface within a case management system.

Table 28 lists exemplary attributes that are used to view opinion cases across a user interface within a case management system.

Table 29 lists exemplary method functions that are used to view opinion cases across a user interface within a case management system.

Table 31 lists exemplary method functions that are used for a cases grid within a case management system.

Table 32 lists exemplary attributes that are for the copy reference utility within a case management system.

Table 33 lists exemplary method functions that are for the copy reference utility within a case management system.

Table 34 lists exemplary attributes that are for the document extractor utility within a case management system.

Table 35 lists exemplary method functions that are for the document extractor utility within a case management system.

Table 40 lists exemplary procedures used with the database application interface within the case management system.

All references including publications patent applications and patents cited herein are hereby incorporated by reference to the same extent as if each reference were individually and specifically indicated to be incorporated by reference and were set forth in its entirety herein.

The use of the terms a and an and the and similar referents in the context of describing the invention especially in the context of the following claims are to be construed to cover both the singular and the plural unless otherwise indicated herein or clearly contradicted by context. The terms comprising having including and containing are to be construed as open ended terms i.e. meaning including but not limited to unless otherwise noted. Recitation of ranges of values herein are merely intended to serve as a shorthand method of referring individually to each separate value falling within the range unless otherwise indicated herein and each separate value is incorporated into the specification as if it were individually recited herein. All methods described herein can be performed in any suitable order unless otherwise indicated herein or otherwise clearly contradicted by context. The use of any and all examples or exemplary language e.g. such as provided herein is intended merely to better illuminate the invention and does not pose a limitation on the scope of the invention unless otherwise claimed. No language in the specification should be construed as indicating any non claimed element as essential to the practice of the invention.

Preferred exemplary embodiments are described herein including the best mode known to the inventors for carrying out the invention. Variations of those preferred embodiments may become apparent to those of ordinary skill in the art upon reading the foregoing description. The inventors expect skilled artisans to employ such variations as appropriate and the inventors intend for the invention to be practiced otherwise than as specifically described herein. Accordingly this invention includes all modifications and equivalents of the subject matter recited in the claims appended hereto as permitted by applicable law. Moreover any combination of the above described elements in all possible variations thereof is encompassed by the invention unless otherwise indicated herein or otherwise clearly contradicted by context.

