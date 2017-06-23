---

title: System and method for tagging code to determine where the code runs
abstract: A method, system, Web-environment and computer program product for tagging to code to determine a run location. The present includes identifying a plurality of sections of a code, according to runat attributes. Each of the sections of the code is tagged with a runat attribute according to where the section of the code should run. The code can run on the client-side, the server-side or both. The invention preferably operates with a system that allows for JavaScript to be utilized on the server-side.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08914774&OS=08914774&RS=08914774
owner: Appcelerator, Inc.
number: 08914774
owner_city: Mountain View
owner_country: US
publication_date: 20081114
---
This Application claims priority to U.S. Provisional Patent Application No. 60 988 117 filed on Nov. 15 2008 which is hereby incorporated by reference in its entirety.

The present invention is related to development of Web sites and applications. More specifically the present invention relates to facilitated Internet communications between a client side and a server side.

Prior to Rich Internet Applications traditional Web applications involved a client server architecture with all of the processing on the server side and the client side used to display the HTML web pages served by the server. Each time a user desired to view a new Web page a HTTP request was sent to the server and the requested Web page was served to the Web browser on the client side. Such a traditional system is shown in with a Web server on a server side receiving requests over the Internet from a Web browser on a client side.

Rich Internet Applications such as Ajax greatly improved on the traditional client server architecture by allowing the client machine to dynamically render and partially refresh web pages based on an initial set of instructions from the server user input and small amounts of subsequent data dynamically requested from the server. As shown in the client machine processes Ajax instructions to render a Web page for the user.

Early Web applications allowed a user s browser to send a request to a server. The server processed the request and responded to the browser with a Web page. When the user wanted to view a new page another request was sent to the server and the server responded to the browser with a new Web page. Such a process resulted in a waste of bandwidth since much of the Web contents in the first Web page were also contained in the second web page. The need to resend the same information led to a much slower user interface of a Web application than that of a native application.

An emerging technology called Ajax Asynchronous and JavaScript XML was developed for refreshing part of a page instead of refreshing the whole page on every interaction between the user and application. In an Ajax application when a user submits a form in a page a script program usually a JavaScript program resident on the Web browser receives the user s request and sends a XML Extended Markup Language HTTP Hyper Text Transfer Protocol request to the Web server in background so as to retrieve only the needed Web contents instead of the whole page and perform corresponding processing to partly refresh the page when receiving a response from the Web server. In this way the application response time is shortened because the amount of data exchanged between the Web browser and the Web server is greatly reduced. And the processing time of the Web server is saved because much of the processing is performed at the client side.

Ajax is the use of dynamic HTML JavaScript and CSS to create dynamic and usually interactive Web sites and applications. A more detailed explanation of Ajax is set forth in Edmond Woychowsky Prentice Hall 2007 which is hereby incorporated by reference in its entirety.

Applets or Java Applets are mini executable programs named with the .class suffix and are placed on a Web page and provide interactive and multimedia uses.

Application Programming Interface API is a collection of computer software code usually a set of class definitions that can perform a set of related complex tasks but has a limited set of controls that may be manipulated by other software code entities. The set of controls is deliberately limited for the sake of clarity and ease of use so that programmers do not have to work with the detail contained within the given API itself.

An Attribute provides additional information about an element object or file. In a Document Object Model an attribute or attribute node is contained within an element node.

Behavioral layer is the top layer and is the scripting and programming that adds interactivity and dynamic effects to a site.

Binding in a general sense is the linking of a library to an application program usually to prevent repetition of frequently utilized code.

Compiler is a computer program that translates a series of instructions written in one computer language into a resulting output in a different computer language.

Document Object Model DOM Element is an object contained in a Document Object Model DOM . The term DOM is generally used to refer to the particular DOM held in the memory region being used by the Web browser. Such a DOM controls the Graphical Respondent Interface GRI or Graphical User Interface GUI . The DOM is generated according to the information that the Web browser reads from the HTML file and or from direct JavaScript software instructions. Generally there exists a unique DOM element for every unique HTML element. DOM elements are sometimes referred to as HTML DOM elements because the DOM element exists only because HTML code that was read by the Web browser listed some HTML element that had not previously existed and thereby caused the Web browser to create that DOM element. Often specific elements of the greater set of HTML DOM elements are identified by specifying an HTML DOM checkbox element or an HTML DOM text input element. A more detailed explanation of the document object model is set forth in Jeremy Keith friends of 2005 which is hereby incorporated by reference in its entirety.

HyperText Markup Language HTML is a method of mixing text and other content with layout and appearance commands in a text file so that a browser can generate a displayed image from the file.

Hypertext Transfer Protocol HTTP is a set of conventions for controlling the transfer of information via the Internet from a Web server computer to a client computer and also from a client computer to a Web server.

Internet is the worldwide decentralized totality of server computers and data transmission paths which can supply information to a connected and browser equipped client computer and can receive and forward information entered from the client computer.

JavaScript is an object based programming language. JavaScript is an interpreted language not a compiled language. JavaScript is generally designed for writing software routines that operate within a client computer on the Internet. Generally the software routines are downloaded to the client computer at the beginning of the interactive session if they are not already cached on the client computer. JavaScript is discussed in greater detail below.

JSON is JavaScript Object Notation format which is a way of taking data and turning it into valid JavaScript syntax for reconstituting an object at the other end of the transmission protocol.

MySQL is a relational database management system which relies on SQL for processing data in a database.

Parser is a component of a compiler that analyzes a sequence of tokens to determine its grammatical structure with respect to a given formal grammer. Parsing transforms input text into a data structure usually a tree which is suitable for later processing and which captures the implied hierarchy of the input. XML Parsers ensure that an XML document follows the rules of XML markup syntax correctly.

Platform is the combination of a client computer an operating system and a browser which together can support Internet access and in particular the operation of interactive forms.

Presentation layer follows the structural layer and provides instructions on how the document should look on the screen sound when read aloud or be formatted when it is printed.

Rendering engine is software used with a Web browser that takes Web content HTML XML image files and formatting information CSS XSL and displays the formatted content on a screen.

Serialization places an object in a binary form for transmission across a network such as the Internet and deserialization involves extracting a data structure from a series of bytes.

SQL Structured Query Language is a computer language designed for data retrieval and data management in a database.

Structural layer of a Web page is the marked up document and foundation on which other layers may be applied.

User is a client computer generally operated by a human being but in some system contexts running an automated process not under full time human control.

Web Browser is a complex software program resident in a client computer that is capable of loading and displaying text and images and exhibiting behaviors as encoded in HTML HyperText Markup Language from the Internet and also from the client computer s memory. Major browsers include MICROSOFT INTERNET EXPLORER NETSCAPE APPLE SAFARI MOZILLA FIREFOX and OPERA.

Web Server is a computer able to simultaneously manage many Internet information exchange processes at the same time. Normally server computers are more powerful than client computers and are administratively and or geographically centralized. An interactive form information collection process generally is controlled from a server computer to which the sponsor of the process has access.

World Wide Web Consortium W3C is an unofficial standards body which creates and oversees the development of web technologies and the application of those technologies.

XHTML Extensible Hypertext Markup Language is a language for describing the content of hypertext documents intended to be viewed or read in a browser.

XML Extensible Markup Language is a W3C standard for text document markup and it is not a language but a set of rules for creating other markup languages.

There are three types of JavaScript 1 Client side JavaScript 2 Server side JavaScript and 3 Core JavaScript. Client side JavaScript is generally an extended version of JavaScript that enables the enhancement and manipulation of web pages and client browsers. Server side JavaScript is an extended version of JavaScript that enables back end access to databases file systems and servers. Core JavaScript is the base JavaScript.

Core JavaScript includes the following objects array date math number and string. Client side JavaScript and Server side JavaScript have additional objects and functions that are specific to client side or server side functionality. Generally any JavaScript libraries .js files created in core JavaScript can be used on both the client and the server without changes. Client side JavaScript is composed of a Core JavaScript and additional objects such as document form frame and window. The objects in Client side JavaScript enable manipulation of HTML documents checking form fields submitting forms creating dynamic pages and the browser directing the browser to load other HTML pages display messages . Server side JavaScript is composed of Core JavaScript and additional objects and functions for accessing databases and file systems and sending email. Server side JavaScript enables Web developers to efficiently create database driven web applications. Server side JavaScript is generally used to create and customize server based applications by scripting the interaction between objects. Client side JavaScript may be served by any server but only displayed by JavaScript enabled browsers. Server side JavaScript must be served by a JavaScript enabled server but can be displayed by any browser.

United States Patent Application Publication Number 20010037359 describes a system and method for a server side browser including markup language graphical user interface dynamic markup language rewriter engine and profile engine. The system includes a user computer and a destination server computer separated by a server computer hosting a server side browser SSB . The SSB includes a markup language graphical user interface MLGUI a dynamic markup language rewriter engine DMLRE and a profiling engine PE . The SSB may be configured as an intermediary infrastructure residing on the Internet providing customized information gathering for a user. The components of the SSB allow for controlling brokering and distributing information more perfectly by controlling both browser functionality on the client side and server functionality on the destination site side within a single point and without the necessity of incremental consents or integration of either side.

However current technologies that operate Server side JavaScript fail to offer complete interactions which are the hallmark of rich web sites and applications. When writing software it is often convenient to group the code according to the area of functionality it provides. But the group might span code that needs to run on the server code that needs to run on the client code that needs to run on both or run on the server and get stored there and have a proxy for it created on the client etc.

The Present Invention overcomes the obstacles of the prior art. With the present invention one can tag a code in a variety of ways to designate its run related behavior. For example one can designate an entire script block with a runat attribute which then applies to the code in that script block one can programmatically set runat attributes on code such as functions and objects to control behavior at a finer granularity and one can add annotations via JavaScript comments to set the runat attributes without changing the JavaScript or HTML syntactically. Additionally one can use the JavaScript language itself to annotate the functions to define their runat characteristics.

One aspect of the present invention is a method for tagging to code to determine a run location. The method includes writing a code for a web application. The method also includes identifying a plurality of sections of the code according to runat attributes. The method also includes tagging each of the plurality of sections of the code with a runat attribute.

Another aspect of the present invention is a system for tagging code to determine a run location. The system includes a server a client a code written in a scripting language with the code having a plurality of sections identified according to runat attributes and means for tagging each of the plurality of sections of the code with a runat attribute.

Yet another aspect of the present invention is a web environment for tagging code to determine a run location. The web environment includes a server a client a code written in a scripting language with the code having a plurality of sections identified according to runat attributes and means for tagging each of the plurality of sections of the code with a runat attribute.

Yet another aspect of the present invention is a method for tagging to code to determine a run location. The method includes writing a code for a web application. The method also includes identifying a plurality of sections of the code according to runat attributes. The method also includes grouping the code according to an area of functionality. The method also includes tagging each of the plurality of sections of the code with a runat attribute.

Yet another aspect of the present invention is a computer program product for creating a Web application. The computer program product comprises a code written in a scripting language with the code having a plurality of sections identified according to runat attributes and means for tagging each of the plurality of sections of the code with a runat attribute.

Having briefly described the present invention the above and further objects features and advantages thereof will be recognized by those skilled in the pertinent art from the following detailed description of the invention when taken in conjunction with the accompanying drawings.

As shown in a system of the invention generally includes a server side a client side and a network or preferably the Internet . The server side includes a web server a handler and a JavaScript server preferably having a server core and a server framework . The client side includes a Web browser has a client framework a client side JavaScript code and a rendering engine . The server framework accesses filesystems and databases as well as the Internet . A more detailed description of the abilities of the running JavaScript on the server side and client side is disclosed in U.S. patent application Ser. No. 12 270 817 filed Nov. 13 2008 for which is hereby incorporated by reference in its entirety.

In the system is shown during a callback operation. The callback begins at the client side JavaScript code with a callback request sent to the client framework . A HTTP GET request is transmitted over the Internet to the server side and received at the Web server . The HTTP GET request is sent to the server core which sends the HTTP GET request as a callback to the server framework . The server framework receives the callback deserializes performs the get functions invokes serializes and sends the response to the callback to the server core . The server core sends the response to the Web server which sends the response over the Internet to client framework on the Web browser .

In the system is shown during a normal process. The process begins with a HTTP GET request for a Web page sent over the Internet from the Web browser on the client side to the server side . The HTTP Request is sent to the handler server . The HTML web page is then sent to the server architecture . The server core of the server architecture parses the HTML Web page to create a HTML DOM of the HTML Web page. The server core also parses and interprets the JavaScript of the HTML Web page. The server framework accesses databases and filesystems to respond to the Requests for the HTML Web page. The server framework also injects proxies to modify the HTML Web page. The server core serializes the DOM back to the HTML Web page and the web server transmits the HTML Web page to the client side where the Web browser renders the HTML Web page for display for a user.

As shown in the present invention allows the server to execute the JavaScript functions that are set to runat server or runat both . These functions might call databases file systems communicate across network sockets or get session data. And since the server side engine has a HTML DOM just like the browser the HTML page can be manipulated through standard DOM APIs and your favorite Ajax libraries. The present invention also has session objects that can be used to persist data for users during a session or transaction. Any functions set to runat server are stripped from what gets sent to the browser . Specifically at 1 the page executes on the server and a resulting HTML page is sent to the browser .

After server sends the resulting HTML page to the browser at 2 the browser interprets the HTML page and executes the JavaScript within the HTML page. If JavaScript functions tagged to runat server proxy are included then the present invention automatically strips out the bodies of those functions and replaces the bodies with a new functions by the same name that know how to invoke the original function on the server using Ajax calls and return the result either synchronously or asynchronously. Ajax communications do not need to be written using the present invention. Any functions not tagged with a runat attribute or set to runat client or runat both are processed by the browser .

Any functions set to runat server proxy can now be called from the browser . The function is called as if it were running on the browser and the present invention automatically via XHR communications with the server marshals the parameters to the server where the function executes calling databases getting info from the session data etc. . . . and returns the result to the browser . The server proxy functions can be invoked either synchronously or asynchronously. At 3 the browser calls the server asynchronously for new information.

The server computer program of the present invention is pre configured for preferable use as a plug in to the APACHE 2.x web server. To provide standards compliant JavaScript and DOM capabilities server side the server computer program is built on the MOZILLA engine which is the same engine used in the popular FIREFOX browser. The server computer program of the present invention is layered into APACHE as an input and output filter for use to modify dynamic pages created by other languages such as PHP or Ruby.

The server computer program of the present invention is preferably a combination of C C Core code and a server side JavaScript Framework. The server core provides the JavaScript parser and runtime HTML parser and DOM engine and an event architecture that calls the server framework as the

On the server side a developer s JavaScript environment is enhanced by the server framework which provides access to the database e.g. MySQL file system network the HTTP Request and Response data and the external server side platforms such as Java PHP and Ruby.

An example of code written by a developer and prior to processing by the present invention is set forth below.

Processing of the code by the present invention results in the code being formatted as set forth below 

As shown in a server computer contains server architecture . The server architecture includes the server core and the server framework . The server core includes a JavaScript parser . The server computer is preferably a conventional server computer available from IBM HP APPLE DELL and SUN.

As shown in a user computer contains a Web browser . The Web browser preferably includes the client framework client side JavaScript code and the rendering engine . The user computer is preferably a conventional user computer such as a PC available from HP DELL and GATEWAY or a MAC available from APPLE. The Web browser is preferably MICROSOFT INTERNET EXPLORER NETSCAPE APPLE SAFARI MOZILLA FIREFOX or OPERA.

A general method of the present invention is shown in . At block code for a web application is written. At block specific code is identified according to a runat location. At block the specific code is tagged with runat attributes. illustrates components of tagging the code with runat attributes. illustrates components of identifying the specific code according to runat locations.

A more specific method of the present invention is shown in . At block code for a web application is written. At block the code is grouped according to an area of functionality. At block specific code is identified according to a runat location. At block the specific code is tagged with runat attributes. The components of apply equally for the step of tagging the code with runat attributes of block . The components of apply equally for the step of identifying the specific code according to runat locations of block .

Code runs on the server architecture of the present invention. To define and or execute any code server side a runat attribute is added to a block. The attribute has several possible values and the values determine where the code will execute whenever the page is served and the other actions that will automatically occur when the code is executed. The Table One provides a description of each value for the basic attributes.

Although most use cases are covered by the basic attributes listed in Table One one can use the runat values listed in Table Two on tags.

Special function object properties are declared on the individual function objects and control how the special function object properties are managed. When these are specified the property value will override the containing script block runat setting for the individual function. This allows more granular control and prevents the need to break scripts out into separate files depending on their runat target. Table Three illustrates some of these properties.

The following example illustrates one simple way of using the runat and proxy options in a typical code scenario. Group all the server side code in one script block and explicitly designate a subset of function to be proxied. Then all client side code goes in a different script block where there isn t even the option of programmatically changing it by setting a different runat or proxy value . Of course those skilled in the pertinent art may choose different ways of organizing the code. Further for large amounts of code one has the option to extract the code into reusable external JavaScript files.

The following illustrates code for the example. The  login.js file referenced in the example contains some functions that explicitly override the runat server directive specified on the script tag used to load the file.

The following is an illustration of object inside an Aptana namespace to allow the proxy functions to be declared in a single group within JavaScript code.

This code is presented in such a way that it is executed by the server prior to DOM serialization. One can also use this code to remove the proxied functions by setting the value to null. Also Aptana.proxies is not a complete collection of the functions being proxied by the server it is just a convenient way to express the myFunc.proxy true syntax for multiple function references.

The runat attribute applies to everything within the block. Individual functions within the block are changed to a different runat value by adding a runat proxy property to them and setting it to the appropriate string value for example myFunction.runat both . The one exception is for blocks that don t have a runat attribute or have runat client since such blocks are not executed at all on the server setting runat properties within those blocks will not take place on the server so the behavior of functions within them cannot be changed from within them.

From the foregoing it is believed that those skilled in the pertinent art will recognize the meritorious advancement of this invention and will readily understand that while the present invention has been described in association with a preferred embodiment thereof and other embodiments illustrated in the accompanying drawings numerous changes modification and substitutions of equivalents may be made therein without departing from the spirit and scope of this invention which is intended to be unlimited by the foregoing except as may appear in the following appended claim. Therefore the embodiments of the invention in which an exclusive property or privilege is claimed are defined in the following appended claims.

