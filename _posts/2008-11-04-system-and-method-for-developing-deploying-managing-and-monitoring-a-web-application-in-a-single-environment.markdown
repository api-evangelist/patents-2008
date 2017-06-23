---

title: System and method for developing, deploying, managing and monitoring a web application in a single environment
abstract: A system and method for developing, deploying, managing and monitoring a web application in a single environment is disclosed herein. The single environment is preferably an integrated development environment (“IDE”). The system and method preferably allows for deployment to a cloud provider, and preferably allows for use of Web resources from multiple cloud providers. One preferred IDE is the APTANA® STUDIO IDE. An operator can use a user interface to access the integrated development environment and the cloud manager over the network, specifically the Internet.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07596620&OS=07596620&RS=07596620
owner: Aptana, Inc.
number: 07596620
owner_city: San Mateo
owner_country: US
publication_date: 20081104
---
The present invention relates to cloud computing. More specifically the present invention relates to a system and method for developing deploying managing and monitoring a Web application in a single environment.

In general terms cloud computing provides a developer individual or company to have access to resources for a Web application in particular a web site. Various vendors provide cloud computing to the developer community. Such vendors include JOYENT see joyent.com Amazon Web Services See amazon.com Google App Engine see http code.google.com appengine and others.

Applets or Java Applets are mini executable programs named with the .class suffix and are placed on the web page and provide interactive and multimedia uses.

Application Programming Interface API is a collection of computer software code usually a set of class definitions that can perform a set of related complex tasks but has a limited set of controls that may be manipulated by other software code entities. The set of controls is deliberately limited for the sake of clarity and ease of use so that programmers do not have to work with the detail contained within the given API itself.

Asynchronous Server Side Processing is a means for avoiding having to reload a new page for every request sent by a client and involves placing a intermediary between a client and server in order to send a request to the intermediary i.e. XMLHttpRequest object which sends it to the server for processing and receives the response from the server for passing on to the client.

Boot or Bootstrap refers to loading the first piece of software that starts a computer since the operating system is essential for running all other programs it is usually the first piece of software loaded during the boot process.

A Channel is information about organized content on an intranet or the Internet. Channels enable Web developers to categorize and describe Web site content and make that data available to users on demand.

Cloud computing is generally defined as using computing resources primarily servers owned by a third party provider such as the AMAZON ELASTIC COMPUTE CLOUD JOYENT and GOOGLE APPS such that the user does not need to make a substantial investment in computer hardware and scale resources depending on the user s needs. Cloud computing primarily involves Web applications but can include storage raw computing and other specialized services.

FTP or File Transfer Protocol is a protocol for moving files over the Internet from one computer to another.

HyperText Markup Language HTML is a method of mixing text and other content with layout and appearance commands in a file so that a browser can generate a display from the file.

Hypertext Transfer Protocol HTTP is a set of conventions for controlling the transfer of information via the Internet from a Web server computer to a client computer and also from a client computer to a Web server.

Internet is the worldwide decentralized totality of server computers and data transmission paths which can supply information to a connected client computer and can receive and forward information entered from the client computer.

JavaScript is an object based programming language. JavaScript is an interpreted language not a compiled language. JavaScript is generally designed for writing software routines that operate within a client computer on the Internet. Generally the software routines are downloaded to the client computer at the beginning of the interactive session if they are not already cached on the client computer. JavaScript is discussed in greater detail below.

JSON is JavaScript Object Notation format which is a way of taking data and turning it into valid a representation of program information that can be read by another program.

MySQL is a relational database management system which relies on SQL for processing data in a database.

Parser is a component of a compiler that analyzes a sequence of tokens to determine its grammatical structure with respect to a given formal grammar. Parsing transforms input text into a data structure usually a tree which is suitable for later processing and which captures the implied hierarchy of the input. XML Parsers ensure that an XML document follows the rules of XML markup syntax correctly.

Platform is the combination of a client computer an operating system and a browser which together can support HTTP access and in particular the operation of interactive forms.

Portlet is a Web based component that will process requests and generate dynamic content. The end user essentially sees a portlet as being a specialized content area within a Web page that occupies a small window. One could use this content area the portlet to receive different types of information. The portlet provides users with the capability to customize the content appearance and position of the portlet.

Provisioning is the act of supplying and configuring computing resources primarily servers for a web application.

Pulling or Pull Technology is technology that enables Web browsers to retrieve information from a Web server such as updating information at periodic intervals essentially Web browser initiated activity.

Pushing or Push Technology is technology that initiates delivery of material from a server to a properly configured Web browser such as providing automatic updates to a Web browser.

Serialization places an object in a binary form for transmission across a network such as the Internet and deserialization involves extracting a data structure from a series of bytes.

SQL Structured Query Language is a computer language designed for data retrieval and data management in a database.

Structural layer of a web page is the marked up document and foundation on which other layers may be applied.

User is a client computer generally operated by a human being but in some system contexts running an automated process not under full time human control.

User Interface or UI is the junction between a user and a computer program. An interface is a set of commands or menus through which a user communicates with a program. A command driven interface is one in which the user enter commands. A menu driven interface is one in which the user selects command choices from various menus displayed on the screen.

Web Browser is a complex software program resident in a client computer that is capable of loading and displaying text and images and exhibiting behaviors as encoded in HTML HyperText Markup Language from the Internet and also from the client computer s memory. Major browsers include MICROSOFT INTERNET EXPLORER NETSCAPE APPLE SAFARI MOZILLA FIREFOX and OPERA.

Web Server is a computer able to simultaneously manage many Internet information exchange processes at the same time. Normally server computers are more powerful than client computers and are administratively and or geographically centralized. An interactive form information collection process generally is controlled from a server computer.

World Wide Web Consortium W3C is an unofficial standards body which creates and oversees the development of web technologies and the application of those technologies.

XHTML Extensible Hypertext Markup Language is a language for describing the content of hypertext documents intended to be viewed or read in a browser.

XML Extensible Markup Language is a W3C standard for text document markup and it is not a language but a set of rules for creating other markup languages.

As shown in a cloud computing system of the prior art generally involves a single cloud provider which is accessed from a user at a user interface over a network such as the Internet. The user can only work with the single cloud provider and is provided very little information about the performance of the web application on the cloud provider . Further in order to scale up the user must repeat the uploading process.

However current technologies fail to provide a system and method for developing deploying managing and monitoring a web application in a single environment.

The Present Invention overcomes the obstacles of the prior art and provides a method and system for developing deploying managing and monitoring a web application in a single environment.

One aspect of the present invention is a system for developing deploying managing and monitoring a web application in a single environment. The system includes an integrated development environment for developing a web application a network a primary cloud provider having a primary plurality of web resources at least one secondary cloud provider having a secondary plurality of web resources a cloud manager having an application programming interface and a user interface. The cloud manager remotely manages the web application. The cloud manager is capable of monitoring the web application to determine if a current level of web resources is appropriate for the web application to perform within a predetermined performance range. The cloud manager is capable of accessing and providing the primary plurality of web resources from the primary cloud provider for the web application and the cloud manager is capable of accessing and providing the secondary plurality of web resources from the secondary cloud provider for the web application. The user interface is for an operator to access the integrated development environment and the cloud manager over the network.

Another aspect of the present invention is a method for developing deploying managing and monitoring a web application in a single environment. The method includes developing a web application in a single environment. The method also includes provisioning the web application. The method also includes deploying the web application to a primary cloud provider having a primary plurality of web resources. The method also includes managing the web application within the single environment determine if a current level of web resources is appropriate for the web application to perform within a predetermined performance range. The method also includes accessing and providing the primary plurality of web resources from the primary cloud provider for the web application. The method also includes accessing and providing a secondary plurality of web resources from at least one secondary cloud provider for the web application. The method also includes monitoring the performance of the web application from the single environment.

Managing the web application preferably comprises temporarily adding web resources from the secondary plurality of web resources during a time period of high demand for the web application. Monitoring the performance of the web application preferably comprises monitoring the load on the web application. Developing the web application at the single environment preferably comprises providing a plurality of libraries a plurality of plugins and a URL.

Monitoring and managing the Web site preferably comprises monitoring the load on the web site and temporarily adding web resources from the secondary plurality of web resources during a time period of high demand for the web site. Developing the web site preferably comprises using client technology languages and server side languages. The client technology languages preferably comprise HTML CSS and JavaScript and the server side languages preferably comprise PHP Ruby Python Java and JavaScript.

The present invention is a new way to think about back office computing needs. Rather than worrying about where to host a Web site how to configure a Web server and how to set up additional services the present invention enables a user to push all of these concerns and worries to someone else and more importantly somewhere else. It s all handled for over the Internet dynamically and completely managed. In short all of a user s technology needs on the back end are handled as a service much like an electric or a telephone bill.

The present invention provides scalable PHP MySQL APACHE and APTANA JAXER app platforms as a service. Production and staging environments are both provided out of the box. In addition multiple software as service solutions are provided supporting the entirety of a user s application lifecycle from development to deployment to management and monitoring. To make this the ultimate in ease these solutions are also integrated directly into the workflows of an IDE. These software services include hosted source control SVN team member management database tools one click backups Web stats and site performance statistics and an active monitoring and alert system that will notify a user of key events in the system when they happen.

Full SSH SFTP and SVN access to a user s site outside of the IDE is provided. PHP mySQL Apache and APTANA JAXER app stacks are all open source app stacks that one can either set up individually or are supported by other hosting service providers as well.

The present invention is preferably built to compliment computing utilities. The present invention not only preferably provides on demand scalability from such computing utilities it also provides pre configured app stacks ready to run apps management tools integrated right into the IDE and access to hosted source control and staging servers that help a user work more efficiently with others.

With the present invention the inefficiencies of working with VPS and traditional hosts are a thing of the past. Instead of mere FTP or SSH accounts to a server with fixed capacities the present invention provides on demand scalability of Cloud computing plus services like source control team management and staging that integrate right into the IDE and workflow.

The present invention works with JOYENT which serves over one billion page views a month including some of the largest Facebook apps. Currently there are over 4000 PHP apps running on JOYENT. Each Cloud site created with the present invention has a static IP address.

Having briefly described the present invention the above and further objects features and advantages thereof will be recognized by those skilled in the pertinent art from the following detailed description of the invention when taken in conjunction with the accompanying drawings.

The present invention provides a novel system and method for a user to develop a Web application such as a Web site deploy the Web application for access over the Internet manage and monitor the Web application to ensure adequate resources are provided during times of heavy traffic such as heavy viewing of a Web site.

As shown in a system generally includes an IDE a cloud manager having a cloud manager API a primary cloud provider a secondary cloud provider and a second secondary cloud provider . A web application is located at the primary cloud provider . The cloud manager communicates over a network shown by dashed lines directly with the Web application the primary cloud provider the secondary cloud provider and the second secondary cloud provider . Those skilled in the pertinent art will recognize that the system may only include one cloud provider or more than three cloud providers. A developer user operating from a user interface also communicates over the network . Preferably the network is the Internet however those skilled in the pertinent art will recognize that the network may be an Intranet or like network. The user interface preferably communicates with the cloud manager through the IDE . However as discussed herein once a Web application is deployed the user interface preferably communicates directly with the cloud manager .

A user interface also referred to as UI is typically a computer which includes a processing means for interacting with various input and output devices I O devices and various networks. The I O Devices can be drives a keyboard a display a scanner a mouse and the like. The processing means typically includes a CPU such as an INTEL PENTIUM processor or the like. The processing means also preferably includes a memory random access memory and read only memory and interfaces for communicating with networks and the I O Devices.

The IDE provides a user with the tools necessary to build a Web application such as a Web site. One such IDE is set forth at aptana.com which is hereby incorporated by reference in its entirety. The APTANA IDE is an open source cross platform JAVA script focused development environment for preferably building AJAX applications. However those skilled in the pertinent art will recognize that other IDEs may be utilized without departing from the scope and spirit of the present invention. An IDE is provided to facilitate the development of software applications or other software programs by one or more software developers. The IDE can include one or more servers work stations and other components as well as languages compliers editors and other tools used by developers in the development environment. The IDE is preferably confined to a single geographic location or alternatively can be distributed across a plurality of geographic locations. A geographically diverse configuration would typically include one or more communication channels networks or otherwise among the various development locations to allow for a collaborative work environment. The IDE includes a suite of tools to assist in Web application development projects. Various aspects of a preferred IDE are described below.

The primary cloud provider first secondary cloud provider and second secondary cloud provider and any other cloud providers each provide Web resources that may be used for the Web application . The Web resources are primarily servers owned by a third party provider such as the AMAZON ELASTIC COMPUTE CLOUD JOYENT and GOOGLE APPS such that the user does not need to make a substantial investment in computer hardware and can scale resources depending on the user s needs.

The cloud manager automatically manages the Web resource needs of the Web application . The cloud manager provisions the Web application syncs the Web application and automatically provides scalability for the Web application . A more detailed explanation of the cloud manager is provided below.

The flow preferably involves the initial portal index page requesting a list of portlets from portlal portlets. The IDE returns a list of configured portlets and URL to request a bootstrap JavaScript code e.g. portlets cloud . The portal index page executes the bootstrap code to alter the model and the user interface as appropriate per portlet. The portlet can continue to request new files and resources from for example portlets portlet id sub urls portlets cloud images cloud portlet banner.png .

The MyCloud Servlets involve comet architecture that specifies channels for publishing and subscription. A common model involves a client subscribing to a client id specific channel but publishing on a generic channel. For example a client subscribes to portal.portlets.a1234564 the client publishes to portal portlets with published implicitly including the client ID. The return messages are routed to the specific channel subscribed to by the user. Alternatively the return messages are routed to a global broadcast channel such as projects.

The portal is preferably an AJAX Web application that operates on top of the internal Jetty server and communicates with the IDE through comet . End users access the portal through IDE buttons and the basics of starting up and debugging are briefly discussed below. In order to ensure that no XHR requests remain unterminated or waiting to time out when the portal is closed and then re opened the IDE completely terminates the internal JETTY server every time that a user closes the portal view. As such the portal needs to use a different port every time starting with 8500 and incrementing by 1 each subsequent time the portal is loaded. Similarly the cometd server runs on its own port starting with 8600. For the portal to load properly the portal should preferably be requested as follows http localhost port number index.html port comet port number . For debugging the portal the log output contains every major action logged preferably using FIREBUG. Therefore a review of the log output should identify the problem.

URL parameters are used to have the portal load with specific content rather than the default Home page. A specific tab is loaded with a query string pram tab having possible values of my aptana or my cloud for example http localhost 8500 index.html port 8600 tab my cloud. To a load a specific site in My Cloud query string param siteId with possible values of any site Id for the logged in user for example http localhost 8500 index.html port 8600 tab my cloud siteId 1234.

To deploy a project to the Cloud query string param project. Possible Values are any undeployed project url encoded case sensitive for example http localhost 8500 index.html port 8600 project MyCoolProject.

To start at a specific product in My Aptana query string param product. Possible Values are studio plugins jaxer and cloud. For example http localhost 8500 index.html port 8600 product plugins.

The servlet listing returns JSON data. Preferably JSON data will be parsed not evaluated. Model API directly on cloud manager or have channels like project create .

Studio centric requests involve license information preferences and projects date time last updated .

The core model object interfaces with an ILocationObject. Each object has a unique location that is used to obtain and update the remote model for the object. The core model object also interfaces with the ISynchronizableObject. Each object has a core set of methods to synchronize with the remote model. The core set of methods include the following commit update perform action and delete. The core model object interfaces with the ITransformObject. Each object is able to serialize and de serialize itself from either the remote format received from the Site Manager or the format obtained from the local data store when the Site Manager is unreachable. The core model object further interfaces with the IModifiableObject. Each object is able to detect changes in the model and notify listeners when model changes occur. The core model object implements the interfaces. The core group object extends the core model objects and allows encapsulation of grouped objects that are obtained from a single web service call. The group as a whole may be synchronized or alternatively individual objects in the group may be synchronized.

The first step in deploying a project to Cloud is to set up a Web site name. By way of example the user who is deploying project gullwing is asked to enter a preferred Web site name for project gullwing such as cars90210. APTANA Cloud then determines whether the preferred Web site name cars90210 is available. At step two the user selects among various service plans available for the Cloud project. During the third step in deploying a project to Cloud the user sets up enters his user information or sets up a new user account. Additional steps in deploying a project to Cloud include setting up billing information accepting the Cloud services agreement and confirming and placing the order. Upon placement of the order the Web page is displayed notifying the user that the site is being provisioned. Provisioning the site preferably includes the following steps 1 contacting APTANA Cloud 2 setting up the necessary servers and 3 configuring the Web site.

Once a site has been provisioned on APTANA Cloud a user may monitor the status of that Web site. illustrates the particular My Cloud information for a selected site that is displayed to the user. For example in the Web page in the details of the cars90210 site are displayed under the Overview tab. Details include the particular service plan selected for the site a graph illustrating the number of hits for the site over a selected period of time the local project name for the site the local main and staged site URLs the server IP address and the SVN location. In addition an Events window may display any alerts regarding the site such as a warning that the site is nearing its servers capacity.

A user may add or invite additional users to the particular Cloud project. Users may be designated as either admin or developer. Developers may sync projects folders and files to the site. Admins have the ability to add or remove users for the site as well as sync projects folders and files.

One of the benefits of APTANA Cloud is that it provides to the user valuable information regarding popularity of the project site such as Hits Last 35 Days for the project site cars90210. 

With APTANA Cloud a user may incorporate GOOGLE Analytics to further monitor the project site. For example the user may set up GOOGLE Analytics for the project site cars 90210. Once the site has been set up with GOOGLE Analytics future displays under the Analytics may be similar to that shown in the Web page in including graphical and numerical data regarding site usage.

When the user modifies a project the local site must then be synced with the stage site. illustrates the synching of local site gullwing to project site cars90210 with view of a Web site overview and a project view . The Web page shown in provides further details regarding the syncing of the gullwing local site to the cars90210 project site.

A detailed example of a preferred embodiment of the operation of the present invention is set forth below.

changes icl feature id label label newVersion new version oldVersion old version provider provider . . . 

Return Data action serviceEvent id site id name service name version service version status service status 

From the foregoing it is believed that those skilled in the pertinent art will recognize the meritorious advancement of this invention and will readily understand that while the present invention has been described in association with a preferred embodiment thereof and other embodiments illustrated in the accompanying drawings numerous changes modification and substitutions of equivalents may be made therein without departing from the spirit and scope of this invention which is intended to be unlimited by the foregoing except as may appear in the following appended claim. Therefore the embodiments of the invention in which an exclusive property or privilege is claimed are defined in the following appended claims.

