---

title: Method, apparatus, and system for capturing data exchanged between a server and a user
abstract: Data exchanged between at least one server and at least one user is intercepted in a capturing module that operates independently from the server and the user. A copy of the intercepted data is stored in a database. The intercepted data that is destined for the server is forwarded to the server, or the intercepted data that is destined for the user is forwarded to the user. The intercepting and storing are performed transparently to the user. Interception of data may be performed continuously, and storing of data may be performed during a predetermined time window or at predetermined time intervals. The intercepted data may include events, attributes, images, user identifications, requests, and/or responses. Only a predetermined portion of the data and/or data that satisfies predefined rules is stored. The user may be a web server or a web browser, and the server may be a web server. The data may be exchanged in the form of an Internet protocol and assembled into a web page view for the user. Interception and storing may be performed concurrently for capturing data exchanged simultaneously between a plurality of servers and the user, the server and a plurality of users, or a plurality of servers and a plurality of users.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07953719&OS=07953719&RS=07953719
owner: Verint Systems Inc.
number: 07953719
owner_city: Melville
owner_country: US
publication_date: 20080512
---
This application is a continuation of U.S. Ser. No. 11 534 410 filed Sep. 22 2006 which is a continuation of U.S. Ser. No. 10 061 469 filed Jan. 31 2002 which are both incorporated herein by reference and is related to commonly assigned U.S. Ser. Nos. 10 061 489 and 10 061 491 both of which were filed on Jan. 31 2002 and are incorporated herein by reference.

The present invention is directed to a method apparatus and system for capturing data. More particularly the present invention is directed to a method apparatus and system for capturing data exchanged between a server and a user.

For systems employing interactions between a user and server it is often desirable to be able to view the interactions ideally in a manner that is transparent to the user. This is particularly desirable in a context such as sales customer service or e commerce where interactions between customers and a service provider are important indicators of customer satisfaction.

Attempts have been made to recreate interactions between a user and a server. For example click stream analysis procedures have been used to recreate interactions between a web user and a web service provider. This type of procedure is analogous to reviewing and analyzing the script to a movie. While this procedure reveals some information about the interaction between the server and the user it does not provide a clear tangible picture of special effects the environment chemistry between the user and the server etc.

Other attempts have been made to replay recorded interactions between a server and a user. However these attempts are typically implemented at the server and are thus suitable only for a particular type of server.

There is thus a need for a way of capturing data exchanged between a server and a user in a manner that is independent of the server and transparent to the user and that provides a full picture of the interaction between the server and the user.

The present invention is directed to a method apparatus and system for capturing data exchanged between at least one server and at least one user.

According to exemplary embodiments data from the user destined for the server or data from the server destined for the user is intercepted in a capturing module that operates independently from the server and the user. A copy of the intercepted data is stored in a database. The intercepted data destined for the server is forwarded to the server or the intercepted data destined for the user is forwarded to the user. The intercepting and storing are performed transparently to the user. Interception may be performed continuously. Storing of data may be performed during a predetermined time window or at predetermined time intervals.

According to exemplary embodiments the intercepted data includes events attributes images user identifications requests and or responses. Only a predetermined portion of the data and or data that satisfies predefined rules may be stored.

According to an exemplary embodiment the user is a web server or a web browser and the server is a web server. The data may be exchanged in the form of an Internet protocol and assembled into a web page view for the user.

Data may be exchanged between a plurality of servers and the user the server and a plurality of users or a plurality of servers and a plurality of users. The intercepting and storing may be performed concurrently for capturing data exchanged simultaneously between the plurality of servers and the user the server and the plurality of users or the plurality of servers and the plurality of users.

Further objects advantages and features of the present invention will become more apparent when reference is made to the following description taken in conjunction with the accompanying drawings.

According to exemplary embodiments data exchanged between a server and a user is captured in a manner that is independent of the server and transparent to the user. In the following description the server is referred to as a web server and the user is referred to as a web browser. It will be appreciated however that the invention may be applicable to other types of servers and users.

The web browser may be implemented in a personal computer a telephone etc. The web server may be implemented as a server supporting any operating system e.g. Unix Linux NT or Windows 2000.

The page capture module is arranged between the web server and the web browser . For security purposes a firewall may separate the web browser and the page capture module .

The page capture module operates independently from the web server and the web browser . Thus the page capture module does not need to be customized for each type of web server but may be used with any web server supporting any operating system.

Although the page capture module operates independently from the web server and the web browser it may be implemented in the same device as the web server or the web browser .

According to an exemplary embodiment the page capture module intercepts data exchanged over the Internet using the HyperText Transfer Protocol HTTP . Both HTTP unsecure and HTTPS secure protocols may be supported by the page capture module . For secure protocols a security certificate is shared between the web server and the page capturing module . In addition other types of data stream protocols may be supported e.g. extensible Markup Language XML and socket based data transfers.

According to exemplary embodiments the page capture module acts as a redirection or proxy server from the user s perspective. The page capture module listens on a specified port such as port for HTTP or port for HTPPS and then redirects all browser requests to the web server which is configured to listen on a port other than ports or . Of course if the page capture module is implemented in the same device as the web server the web server may listen on the same port. Web server responses are intercepted by the page capture module and redirected back down to the web browser .

The page capture module captures pages and other data exchanged between the web server and the browser . Pages and other data may be captured continually or at designated intervals or time windows. The page capture module may also record these pages and other data or recording may be performed in a separate recorder server connected to the page capture module.

Each web browser is assigned a unique machine identity ID by the web server . A persistent machine ID cookie may be created by the web server and stored at the web browser for this purpose. All pages served to a particular web browser are identified and grouped by the machine ID.

Although the module is described as a page capture module according to exemplary embodiments other types of data may also be captured. For example events and attributes may be captured. Attributes may be captured in a manner similar to that in which pages are captured as described above.

For event capturing according to an exemplary embodiment an event capture module captures user side events and delivers these to the page capture module . The event capture module may be implemented as an applet that is downloaded to the web browser . Although shown as a separate component the event capture applet is stored at the browser with parameters such as the web browser machine ID the host Internet Protocol IP address and the current page name. The event capture applet may be notified for example by JavaScript embedded in the current page whenever an event needs to be recorded. The event capture applet records events such as page load page unload page scroll page resize and browser exit. The event capture applet sends captured events to the page capturing module via for example a Transmission Control Protocol Internet Protocol TCP IP socket connection on port or port for secure exchanges .

For event capturing an HTTP request header containing a unique signature or identifier may be used to send a captured event to the page capture module . The unique signature may take the form of an application defined request header. Captured event data may include a browser machine ID a page name an event type ID and event data.

According to an exemplary embodiment the page capture module intercepts HTTP requests that are identified as event captured HTTP requests and does not send the event captured HTTP request to the web server .

According to an exemplary embodiment each captured page is assigned a unique page ID and is associated with a specific browser user machine ID. Each page may also contain the date and time that the page was captured and the page status recording processing playback etc. After pages are captured this information is extracted from the captured page and a new record is inserted into a database .

The page preprocessor acts as a recorder server and stores the captured data in a device such as a database . The pages are passed on to the page post processor . Alternatively the page capture module may perform this recording. To reduce the amount of storage necessary only predetermined portions of data may be stored e.g. the request portion or the response portion. Also only data satisfying predetermined rules e.g. rules indicating timing may be stored. When the captured pages are recorded identifying information may also be recorded e.g. a session record ID a date time of recording a machine ID etc.

The post processing module determines which captured data satisfies predefined rules e.g. business rules and records this data in a file such as a Java ARchive JAR file. The database is updated to indicate what captured data has been selected and recorded for playback. An exemplary post processor is described in more detail in the afore mentioned application entitled Method Apparatus and System for Processing Data Captured During Exchanges Between a Server and a User .

A playback tool selects recorded data from the database using the information in the database . An exemplary playback tool is described in more detail in the afore mentioned application entitled Method Apparatus and System for Replaying Data Selected From Among Data Captured During Exchanges Between a Server and a User .

Although not shown in the interest of simplifying the illustrations it will be appreciated that the system in may also include other components e.g. configuration files used for processing and log files use for storing information for debugging etc.

If the cookie or other persistent ID is created successfully or the browser machine ID cookie exists a determination is made whether event capturing is enabled e.g. whether the event capture applet has been notified that an events needs to be recorded at step . If not the page is sent to the page preprocessor at step . Otherwise the event is captured at step .

An exemplary process for recording captured requests and responses is shown in . The process begins at step at which a page preprocess thread is created. At step a determination is made whether there is an event type request header. If not the last page ID for the current browser machine ID is obtained at step and the captured event is recorded at step . If there is an event type request header a page table entry for the captured page is inserted at step and stored e.g. in the database . At step the next available page ID is retrieved. At step the captured data e.g. page and attributes are recorded.

According to exemplary embodiments a user interaction with a server is captured. For a web user and a web server this information may be used to recreate the web experience of the user. For example in a customer service context the flow of customer inputs and the text and images that are displayed on the pages that are viewed by the customer may be captured and recorded. In such a context this recreation will provide contact center personnel the ability to observe the customer s experience for the purpose of analyzing how well service was delivered and whether or not the needs of the customer were met. The invention may also be useful in other contexts such as sales or e commerce.

According to exemplary embodiments all the user actions within a browser session may be captured without degrading the performance of the browser session or web host environment. Also all captured data may be transmitted efficiently with low network bandwidth utilization. Thousands of concurrent users may be supported simultaneously with the recording of a large number of sessions that are simultaneously occurring on different web sites provided by various web servers.

It should be understood that the foregoing description and accompanying drawings are by example only. A variety of modifications are envisioned that do not depart from the scope and spirit of the invention. The above description is intended by way of example only and is not intended to limit the present invention in any way.

