---

title: Method and apparatus for securely invoking a rest API
abstract: An embodiment of the present invention provides a system that enables a user to securely invoke a REST (Representational State Transfer) API (Application Programming Interface) at an application server. A client can establish a secure communication channel with an application server, and can send a request to the application server to invoke the REST API. The client can then receive a security token from an authentication system in response to authenticating the user with the authentication system. Next, the client can receive a nonce and a timestamp from the application server. The client can then determine a security token digest using the security token, the nonce, and the timestamp. Next, the client can resend the request to the application server to invoke the REST API with the security token digest. The application server can invoke the REST API if the security token digest is valid.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08621598&OS=08621598&RS=08621598
owner: Intuit Inc.
number: 08621598
owner_city: Mountain View
owner_country: US
publication_date: 20080312
---
The World Wide Web WWW or web for short has permeated almost all aspects of our lives from buying cameras to buying real estate and from reading a newspaper to watching a movie. Unfortunately the web can also be a very dangerous place where even savvy users can compromise highly sensitive information or suffer substantial financial loss.

Hence providing secure access to web services is an important security problem. However this problem is particularly challenging for at least two reasons. First the Internet is inherently insecure because it is a public network. As a result systems and techniques to provide secure access to web services over the Internet need to address a wide variety of security issues. Second the web owes much of its phenomenal success to its highly scalable architecture and to its user friendly interface e.g. the web browser. Hence it is important to ensure that a security solution is both scalable and user friendly. In other words creating systems and techniques that provide secure access to web services can be very challenging because these systems and techniques need to be highly secure scalable and user friendly.

One embodiment of the present invention provides a system that enables a user to securely invoke a REST Representational State Transfer API Application Programming Interface at an application server.

During operation a client can establish a secure communication channel with an application server. Next the client can use the secure communication channel to send a request to the application server to invoke a REST API. The client can then receive a security token from an authentication system in response to the user authenticating with the authentication system. Specifically the security token can be a SAML Security Assertion Markup Language token a UniAuth token an asymmetric key or a Kerberos ticket. Next the client can receive a nonce and a timestamp from the application server. The client can then determine a security token digest using the security token the nonce and the timestamp. Specifically the client can determine the security token digest by applying a cryptographic hash function to the security token the nonce and the timestamp. Next the client can send another request to the application server to invoke the REST API with the security token digest. If the security token digest is successfully validated by the application server the client can then receive data from the application server which is associated with the REST API invocation. Next the client can store the data and may display the data to the user.

In some embodiments the secure communication channel can be an HTTPS Hypertext Transfer Protocol over Secure Socket Layer session and the REST API can be specified using a URL Uniform Resource Locator .

In some embodiments the client can receive a redirection message from the application server. The redirection message can cause the client to establish a secure communication channel with the authentication system and to authenticate the user with the authentication system.

In one embodiment the client can establish a secure communication session with the application server. Next the application server can receive a request from the client to invoke a REST API. The application server can then send a nonce and a timestamp to the client. Next the application server can receive a security token digest from the client. The application server can then validate the security token digest. If the security token digest is valid the application server can invoke the REST API and send the resulting output data to the client.

The following description is presented to enable any person skilled in the art to make and use the invention and is provided in the context of a particular application and its requirements. Various modifications to the disclosed embodiments will be readily apparent to those skilled in the art and the general principles defined herein may be applied to other embodiments and applications without departing from the spirit and scope of the present invention. Thus the present invention is not limited to the embodiments shown but is to be accorded the widest scope consistent with the principles and features disclosed herein.

The data structures and code described in this detailed description are typically stored on a computer readable storage medium which may be any device or medium that can store code and or data for use by a computer system. The computer readable storage medium includes but is not limited to volatile memory non volatile memory magnetic and optical storage devices such as disk drives magnetic tape CDs compact discs DVDs digital versatile discs or digital video discs or other media capable of storing computer readable media now known or later developed.

The methods and processes described in the detailed description section can be embodied as code and or data which can be stored in a computer readable storage medium as described above. When a computer system reads and executes the code and or data stored on the computer readable storage medium the computer system perform the methods and processes embodied as data structures and code and stored within the computer readable storage medium.

Furthermore the methods and processes described below can be included in hardware modules. For example the hardware modules can include but are not limited to application specific integrated circuit ASIC chips field programmable gate arrays FPGAs and other programmable logic devices now known or later developed. When the hardware modules are activated the hardware modules perform the methods and processes included within the hardware modules.

An embodiment of the present invention assures confidentiality integrity and non repudiation in REST web services and avoids the security vulnerabilities of conventional techniques for providing a REST API.

The REST web service model is commonly used in web applications because it is easier to implement and to use by passing parameters and business data in the HTTP Hypertext Transfer Protocol request or response. SOAP which is a protocol for exchanging XML extensible Markup Language based messages has a security standard. Unlike SOAP REST does not have an existing security standard and most implementations are done over HTTP with no security. Some service providers add authentication to REST web service invocation over HTTP by using a proprietary security token. However since each service provider has its own token its own key management distribution mechanism and its own proprietary security processing logic a user has to keep track of multiple applications for accessing web services.

Furthermore conventional approaches are vulnerable since they embed the security token in the HTTP request. Specifically REST API invocation over HTTP has no security at all. REST API invocation over HTTPS Hypertext Transfer Protocol over Secure Socket Layer is still vulnerable to message replay and to spoofing attacks. Also REST API invocation over HTTP may not support integrity and non repudiation.

For example a REST API invocation such as http rest.api.intuit.com restapi CallName GetAccountBalance SecurityToken 3A68...EF07 UserId johndoe can be easily intercepted using network sniffers or security testing tools and hackers can perform a replay by modifying or guessing customer data. This can be an important security issue for both customers and service providers because without authentication integrity and non repudiation sensitive business transactions will not be adequately protected.

An embodiment of the present invention provides systems and techniques for REST web services that can assure confidentiality e.g. via authentication integrity e.g. the data cannot be tampered with and non repudiation e.g. the parties cannot deny that the business transaction took place . Specifically an embodiment includes the creation of a security tokenizer and a security processing mechanism that assures confidentiality integrity and non repudiation.

The security tokenizer encapsulates security credentials. Depending on the security requirements of the business transaction the security tokenizer can encapsulate different types of tokens. For example the security tokenizer can encapsulate a SAML token which is typically used in an SSO Single Sign On process. A SAML token can assure authentication and integrity. The SAML token is usually created and passed by an identity provider during the SSO process. Since the SAML token is not stored locally on the client the SAML token can obviate key management issues.

Alternatively the security tokenizer can encapsulate Intuit s UniAuth ticket which is used by some Intuit applications. A UniAuth ticket can assure authentication within the pre defined time duration. The ticket is typically created by a UniAuth server upon user login and has an expiry time that is usually less than one hour.

In another embodiment the security tokenizer can tokenize asymmetric keys which are used for generating a digital certificate. This approach can assure authentication integrity and non repudication. These properties can be important for exchanging data with a third party and for assuring a high level of protection.

The security processing mechanism creates a digest of the security token and sends the digest when invoking the REST web service over a secure channel e.g. over an HTTPS session. Specifically the security processing mechanism can use a cryptographic hash function e.g. SHA 1 to generate the digest.

In one embodiment when the client application invokes a REST API the server returns a nonce. The nonce is a unique random value created by the server for creating a message digest. The client then retrieves the security tokenizer in base 64 encoding and creates a message digest. For example the system can use a standard SHA 1 hashing algorithm to create a digest from the security token nonce and the system timestamp. The client can then resubmit the REST service request over HTTPS with the digest.

Since an embodiment of the present invention uses the security tokenizer digest over HTTPS the embodiment can assure the integrity of business transactions and service requests. Further if the embodiment uses asymmetric keys the security tokenizer which encapsulates the asymmetric keys can also digitally sign the REST API invocation request. This approach can have the added advantage of providing non repudiation capabilities.

Specifically an embodiment of the present invention makes REST API invocation requests secure because of the following reasons. First the embodiment uses HTTPS to ensure that communication between the client and the server is encrypted. Second the security tokenizer digest assures confidentiality and protects against message replay spoofing and brute force attacks. Third the embodiment can use digital signatures to assure non repudiation.

In addition to the above described security features embodiments of the present invention have additional advantages when compared to conventional approaches for providing REST services. Since the security tokenizer can encapsulate different kinds of tokens the application doesn t have to be re written or changed when switching from one type of security token to another. Moreover the security tokenizer doesn t reinvent the wheel because it reuses security infrastructures e.g. the single sign on infrastructure for SAML tokens the PKI Public Key Infrastructure for digital certificates etc. Further since a security token can be managed dynamically the token doesn t have to be stored locally. Additionally embodiments of the present invention can be implemented with a web browser client or a desktop client. Since a SAML token can include an access rights profile which can be received from an identity provider infrastructure an embodiment of the present invention can use the access rights profile to determine access rights for a user.

Computer comprises processor memory and storage device . Computer can be coupled with display keyboard and pointing device . Storage device can store web browser application and operating system . During operation computer can load operating system into memory . Next user can load web browser into memory and use it to browse the World Wide Web.

Computer can be coupled with network which can enable computer to communicate with application server and authentication system . Network can generally comprise any type of wire or wireless communication channel capable of coupling together network nodes. This includes but is not limited to a local area network a wide area network or a combination of networks or other network enabling communication between two or more computing systems. In one embodiment of the present invention network comprises the Internet.

User may use web browser to communicate with application server which may support an online application. Device may also be used for web browsing or for invoking a REST API. Device may be coupled with network via a wire or wireless communication channel. For example device may be coupled with network via a Wi Fi channel shown using a solid line . In addition device may also be coupled directly with computer via a wire or wireless communication channel shown using a dashed line . For example device may be coupled with computer via USB Universal Serial Bus and or Bluetooth.

A client can receive a security token from an authentication system in response to authenticating the user with the authentication system step . The authentication system can include one or more computers which are used for authentication purposes. For example the authentication system can be an identity provider server and the security token can be a SAML token that is generated during a single sign on process. Alternatively the authentication system may include a Kerberos authentication server and a Kerberos ticket granting server and the security token can be a Kerberos ticket.

Next the client can establish a secure communication channel with an application server step . For example the client can set up an HTTPS session with the server. Note that not all SSL Secure Socket Layer implementations check the server s digital certificate and hence they are vulnerable to man in the middle attacks.

The client can then send a request to the application server to invoke the REST API wherein the request is sent using the secure communication channel step . For example the REST API can be invoked using a URL and the request can be sent as an HTTP GET message over the HTTPS session.

Next the client can receive a nonce and a timestamp from the application server step . The nonce can be a pseudo random number that is generated by the application server and the timestamp can be the application server s system time.

The client can then determine a security token digest using the security token the nonce and the timestamp step . Specifically the system can generate the security token digest by applying a cryptographic hash function to the security token the nonce and the timestamp. In one embodiment the cryptographic hash function can be SHA 1.

Next the client can send another request to the application server to invoke the REST API wherein the request includes the security token digest and wherein the request is sent using the secure communication channel step .

The client can then receive data from the application server which is associated with the REST API invocation step . For example the data can be included in an HTTP response message which is received over the HTTPS session.

Next the client can store the data step . For example the client can store the data in memory or in another computer readable storage medium.

An application server can establish a secure communication channel with a client step . Next the application server can receive a request from the client to invoke the REST API wherein the request is received using the secure communication channel step .

The application server can then send a nonce and a timestamp to the client step . Next the application server can receive a security token digest from the client step .

The application server can then determine whether the security token digest is valid step . Specifically the application server can validate the security token digest using the security token the nonce and the timestamp.

If the security token digest is valid the application server can send data to the client which is associated with the REST API invocation step .

Otherwise if the security token digest is invalid the application server can send an error message to the client step .

These descriptions have been presented for purposes of illustration and description and are not intended to limit the present invention to the forms disclosed. Accordingly many modifications and variations will be apparent to practitioners skilled in the art. For example in one embodiment in response to receiving a request to invoke a REST API the application server can send a redirection message to the client to redirect the client to an authentication system. The redirection message can cause the client to establish a secure communication channel with the authentication system. Next the client can use the secure communication channel to authenticate a user with the authentication system and receive a security token. The client can then generate a security token digest and use the digest to securely invoke the REST API. After the user authenticates with the authentication system the authentication system may send a redirection message to the client to redirect the client to the application server. In one embodiment the redirection message may cause the client to send the security token to the application server.

Client authentication system and application server can communicate with one another using a network. In one embodiment authentication server can be an identity provider server.

The process can begin when a user uses client to authenticate with authentication server and receives security token step .

Next client can invoke a REST API at application server step . For example client can invoke a REST API by sending an HTTP GET request to application server .

Application server can then send a nonce and a timestamp to client step . In a variation on this embodiment application server may send only a timestamp to client . Next client can generate security token digest by applying a cryptographic hash function to security token the nonce and the timestamp.

Application server may then verify security token digest with authentication server step . In one embodiment application server can verify security token digest using JAAS Java Authentication and Authorization Service . Java is a trademark of Sun Microsystems Inc. which may be registered in the United States and or other countries. 

Once the security token digest is verified application server can process the REST API invocation to generate output data . For example application server may perform a database query to generate output data .

Next application server can send output data to client step . Client can then display output data to the user.

The foregoing descriptions of embodiments of the present invention have been presented only for purposes of illustration and description. They are not intended to be exhaustive or to limit the present invention to the forms disclosed. Accordingly many modifications and variations will be apparent to practitioners skilled in the art. Additionally the above disclosure is not intended to limit the present invention. The scope of the present invention is defined by the appended claims.

