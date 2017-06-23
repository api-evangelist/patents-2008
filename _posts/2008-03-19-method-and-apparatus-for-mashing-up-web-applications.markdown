---

title: Method and apparatus for mashing up web applications
abstract: Disclosed are a method, apparatus, and computer program, product for mashing up web applications. The method includes: obtaining at least two document object models (DOM) corresponding to at least two web applications respectively; merging nodes of the at least two document object models to obtain a new document object model; connecting, on the new document object model, the nodes belonging respectively to the at least two document object models; and obtaining a new web application from the new document object model after connection.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09122484&OS=09122484&RS=09122484
owner: International Business Machines Corporation
number: 09122484
owner_city: Armonk
owner_country: US
publication_date: 20080319
---
This application is based upon and claims priority from a prior Chinese Patent Application No. 200710088391.7 filed on Mar. 19 2007 the entire disclosure of which is herein incorporated by reference in its entirety.

The present invention relates to the field of information technology and more particularly to web based application aggregation technology.

With the vigorous growth of World Wide Web more and more services are provided to users via web applications. The mashing up among different web applications in a simple and efficient way in order to form new web applications is becoming an increasingly pressing need.

Currently the major approach of mashing up web applications is performed by means of application programming interfaces API . Specifically the owner of a web application needs to expose the relevant API in order to let the web application be mashed up by other users.

For example with the API of Google map a user can integrate customized data e.g. weather forecast on top of Google map.

However owners of many web applications do not explicitly define and expose relevant APIs for reasons such as costs difficulty in transforming an existing application system and the like.

Therefore the aforesaid solution of mashing up web applications using the APIs of web applications has limitation. That is if the owner of a web application does not expose the relevant API then users cannot use the web application for mashing up.

To sum up there is a need to propose a solution of mashing up web applications without depending on the APIs of web applications so as to increase the flexibility and the applicability of mashing up web applications.

It is an object of the present invention to provide a method and apparatus for mashing up web applications which can mash up at least two web applications without depending on the API of any one of the web applications.

To this end the present invention proposes a method for mashing up web applications comprising the steps of obtaining at least two document object models DOM corresponding to at least two web applications respectively merging nodes of said at least two document object models to obtain a new document object model connecting on said new document object model the nodes belonging respectively to said at least two document object models and obtaining a new web application from said new document object model after connection.

The present invention further proposes an apparatus for mashing up web applications comprising a parser for obtaining at least two document object models DOM corresponding to at least two web applications respectively a merger for merging nodes of said at least two document object models to obtain a new document object model a connector for connecting on said new document object model the nodes belonging respectively to said at least two document object models and a creator for obtaining a new web application from said new document object model after connection.

The present invention still further proposes a computer program product containing program instructions for implementing the method described above.

Compared with the existing solutions for mashing up web applications the present invention uses DOMs of web applications to mash up other than invoking APIs of web applications directly. In other words mashing up web applications can be implemented without the support of APIs in the present invention. As a result the flexibility and adaptability of mashing up is improved dramatically as DOMs of web applications can be easily obtained.

Like reference numerals designate the same similar or corresponding features or functions throughout the drawings.

The fundamental idea of the present invention is to use document object models DOM of at least two selected web applications to mash up these web applications so as to obtain a new web application conveniently. According to an embodiment of the present invention DOMs of at least two selected web applications are obtained first. Nodes of DOMs of these web applications are then merged together to obtain a new DOM. Next nodes belonging respectively to DOMs of these web applications are connected on the new DOM. A new web application is obtained from the new DOM after connection.

Of course those skilled in the art should understand that other clients and or servers may be connected on network . Moreover in order to differentiate one another clients and servers may have identifiers capable of identifying them uniquely such as IP addresses and universal resource locators URL .

In this embodiment of the present invention a web application for applying for a job is running on server . When the web application for applying for a job on server is accessed using a browser such as IE Firefox and the like on server client or client a page as depicted in will be displayed on the browser. As depicted in a user can apply for a job on this page for example input name address and other information into the input box about name and address make selection in the checkbox about job skills and fill in the input box about self description. The user can submit his her inputs selection to server by clicking a button not depicted .

A web application for search similar to Google search application is running on server . When the web application for search on server is accessed using a browser such as IE Firebox and the like on server client or client a page that can result in the page as depicted in will be displayed on the browser. As depicted in after a user inputs desired search content foo into the input box and then clicks a button to submit the content for searching None result is obtained. The user can submit his her desired search content to server by clicking a button schematically depicts a button shown as search the web for foo .

As described below server client serves as a client in some cases and serves as a server in other cases.

In this embodiment of the present invention selected web applications are mashed up in server client . When mashing up web applications server client serves as a client.

Moreover a new web application obtained from mashing up is running on server client at which point server client serves as a server.

In this embodiment of the present invention it is intended to obtain such a web application when client accesses the web application obtained from mashing up on server client using a browser such as IE Firefox and the like a page that can result in a page as depicted in will be displayed on a browser.

As depicted in when a user inputs name address and other information Eric into the input box about name and address on the left results from searching the input information Eric will be displayed on the right. That is to say the web application obtained from mashing up combines and connects the web application on server and the web application on server .

First the web application for applying for a job on server and the web application for search on server are accessed via their respective URLs so as to obtain two corresponding web pages step .

For example the web pages may be parsed by means of the following JavaScript codes so as to obtain corresponding DOMs.

For another example the DOM of a web page may be obtained using the DOM Inspector tool in the Firebox browser.

In this embodiment of the present invention all input nodes of the DOMs can be found by means of such a JavaScript function as document.getElementsByTags input .

In step a new DOM is formed by merging desired nodes of respective DOMS which are obtained from searching.

Those skilled in the art should understand that nodes of respective DOMs may be merged in various ways to form a new DOM. As a result there is only difference in the display effect of the page of the web application corresponding to the new DOM on the browser but the function remains the same.

Of course those skilled in the art should understand that step is optional. In other words a new DOM may be formed by merging all nodes of the DOMs depicted in without performing a search.

In step corresponding nodes that belong to different DOMs e.g. the two DOMs depicted in are connected on the new DOM. Through connection new function can be realized on the basis of respective source web applications.

A conventional connection approach is an intrusive approach i.e. modifying codes of original web applications adding new codes to some triggering points and thereby achieving the connection between different web applications.

Different from the conventional connection approach connection is achieved by a non intrusive monitoring mechanism in this embodiment of the present invention.

Under this mechanism a global monitor is initialized first. This monitor can monitor not only conventional user events such as a click of a node e.g. button node of the DOM and movement of the mouse but also triggering of any function. Therefore with the monitor a developer can dynamically add a custom extra function before or after any function is triggered and without modifying codes of the original web applications.

The codes mean when sourceFunction of sourceApplication is triggered targetFunction of targetApplication is also triggered.

Furthermore through setting parameters developers can also set whether targetFunction is triggered before or after sourceFunction takes place. In the case that targetFunction is triggered before sourceFunction takes place values of input parameters of the sourceFunction can be changed via an extra function before sourceFunction takes place.

With such a mechanism it is able to connect different web applications in a flexible and non intrusive way and thereby achieve rapid non intrusive mashing up without depending on APIs.

Nodes belonging to respective DOMs can be connected on the new DOM depicted in using the following codes 

Where passvalue is a user custom additional function which takes place before SearchForm.SearchSubmit.onClick is triggered. The codes thereof is as follows 

And the function thereof is to pass the value input into the name input box in JobApplication to KeyWordInput of SearchForm.

More specifically when it is monitored that OnChange event of NameInput takes place the value of NameInput is passed to KeywordInput and Onclick event of Submit is triggered.

In this way when a user inputs the name Eric into the input box about name and address on the left results from searching the input name Eric are displayed on the right.

Returning to again a new web application is obtained from the connected new DOM in step . Since codes written in various languages and for obtaining a web application from DOM already exist in the prior art details thereof are omitted here.

Apparatus for mashing up web applications may be a tool written in JavaScript and based on a browser.

As depicted in apparatus for mashing up web applications comprises a parser for obtaining at least two document object models corresponding to at least two web applications respectively a merger for merging nodes of the at least document object models to obtain a new document object model a connector for connecting nodes belonging to said at least two document object models on said new document object model and a creator for obtaining a new web application from the new document object model after connection.

Apparatus for mashing up web applications may further comprise a searcher for searching at least two document object models to retrieve desired nodes and that merger merges nodes of said at least two document object models is implemented by merging the desired nodes that have been retrieved.

Connector may connect nodes belonging to said at least two document object models based on the aforesaid non intrusive way.

It should be noted that in order to facilitate easier understanding of the present invention the foregoing description omits some detailed technical details that are well known to those skilled in the art and might be indispensable to the implementation of the present invention.

The specification of the present invention has been presented for purposes of illustration and description and is not intended to be exhaustive or limited to the invention in the form disclosed. Many modifications and variations will be apparent to those of ordinary skill in the art.

For example those skilled in the art should understand that in the previously described embodiments the number of web applications that are mashed up to form a new web application is not limited to two but may be three or more.

Therefore the embodiments were chosen and described in order to best explain the principles of the invention the practical application thereof and to enable those of ordinary skill in the art to understand that all modifications and alterations made without departing from the spirit of the present invention fall into the protection scope of the present invention as defined in the appended claims.

