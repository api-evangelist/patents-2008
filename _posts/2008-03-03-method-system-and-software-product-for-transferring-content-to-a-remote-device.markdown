---

title: Method, system and software product for transferring content to a remote device
abstract: The present invention relates to a method for transferring content to a device, the method including the steps of: receiving a request for content from the device; delivering a uniquely identifiable, ephemeral player to the device; and transferring content to the device, for presentation on the device by the player. The invention has particular application to digital rights management in respect of the distribution of audiovisual content such as film and television programs, advertisements and live event broadcasts over communication networks such as the Internet.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08931105&OS=08931105&RS=08931105
owner: Vividas Technologies Pty. Ltd.
number: 08931105
owner_city: Prahran, Victoria
owner_country: AU
publication_date: 20080303
---
The present invention relates to a method system and software product for transferring content to a remote device. In particular the invention is for use with respect to content that is to be protected from use other than in accordance with the authority of the holder of rights in the content. The invention has particular application to the distribution of audiovisual content such as film and television programs advertisements and live event broadcasts over communication networks such as the Internet.

In this specification where a document act or item of knowledge is referred to or discussed this reference or discussion is not an admission that the document act or item of knowledge or any combination thereof was at the priority date part of common general knowledge or known to be relevant to an attempt to solve any problem with which this specification is concerned.

The creative industries such as those involved in film television program and advertisement production and in the broadcast of live events operate on a basic proposition that holders of rights in the relevant content are remunerated for the use of that content. This promise of sometimes very lucrative remuneration provides an incentive to producers to undertake substantial financial risks involved in the creation of such content. In the traditional distribution chain rights holders receive remuneration through means such as ticket sales physical media sales and rentals advertising revenue and subscription fees.

Internet connection speeds are continually improving as broadband networks are deployed and it is now becoming feasible to use the Internet as a content distribution medium. However whilst it may be technically feasible to distribute content such as film and television programs and live event broadcasts over the Internet commercial considerations associated with protecting rights holders against unauthorised use of their content and thereby providing proper remuneration are yet to be adequately resolved.

Content may be transferred over the Internet either by downloading or streaming. Downloading involves the transfer of an entire file to a device for subsequent viewing by means of pre installed playing software such as the Windows Media Player or Apple s Quicktime whereas streaming involves the simultaneous downloading and playing of a file with the playing software commencing play as soon as it has downloaded sufficient data to do so.

The key advantage of streaming over downloading is that a user need not wait for the complete download of a large file a process which may take some time before commencing a playback session. Downloading is thus generally unsuitable to Internet broadcasts of live events in real time or close to real time which can only be implemented by way of content streaming.

Applicant s previous International Patent Application WO 03 005190 the contents of which are hereby incorporated by reference describes a system and method for content playback using a player which is not saved to the user s machine and which can be effected without reference to the operating system registry. The invention can be applied to both streamed content and saved content eg. content on a physical medium .

Generally when streaming is adopted eg. to broadcast a live event on a pay per view basis vulnerabilities in current streaming software packages can leave open the possibility of unauthorised use of the streamed content. One such vulnerability known as playback control circumvention involves an attacker stripping or modifying content entitlements to gain unauthorised access to the content. This enables an unauthorised user to access content and to possibly redistribute the illegally accessed content thereby denying the rights holder of due compensation.

Another mode of attack involves a user making an exact copy of a specific instance of a media player enabling the user to violate replay limitations.

A further weakness in current web streaming system enables users to steal or reuse a specific session ID allowing them to view the content more often than intended by the rights holder.

It would be advantageous to provide a web streaming system which is less vulnerable to attack through one or more of these modes than the systems which are currently available.

According to a first aspect of the present invention there is provided a method for transferring content to a device the method including the steps of 

In this specification including the claims the term ephemeral refers to a software program which is not installed on the operating system nor saved to non volatile storage of the device on which it runs.

The present invention imposes a requirement for a user to download a new player which is itself uniquely identifiable and ephemeral for each and every playback session and in doing so ameliorates the disadvantages of present content delivery systems noted above. In particular pre recorded or live content may be uniquely identified validated and tracked.

One or more separate media files may be delivered as part of a single playback session to be presented on the player for that particular session.

Moreover the requirement for a user to download a new player for each and every playback session also frustrates the attempts of those seeking unauthorised access or replaying of content.

The present invention is particularly suitable for the transfer of content to a device by way of streaming. However it can also be used to protect content that is delivered through downloading.

Typically the unique identifier comprises a session key. According to this embodiment the method may includes the steps of 

It will be realised that the session key is used to uniquely identify the player as well as for validation of content requests. Using a session key for both of these purposes of a dual role session key ensures that content is only delivered to devices with a valid session key or session ID linked to that particular unique player.

This embodiment of the invention alleviates the problem of session cloning where session IDs are obtained and used to view content more often than intended by the rights holder. The problem is particularly apparent in video on demand applications where illegally obtained session IDs deny rights holders due remuneration for repeated viewing of their content and can also result in legitimate users being charged for these unauthorised viewings.

In preferred embodiments the step of validating content requests against the stored key comprises attempting to decrypt the content request using the stored key.

In preferred embodiments the player code comprises one or more libraries that are delivered to the device for operable interaction with one or more graphics systems associated with the device s operating system the libraries being generated by linking one or more object code files that are adapted to execute in the device s native operating system and wherein the unique identifier is included in the player code by incorporation into the object code files whilst or before those files are linked into the libraries.

Preferably the method includes the step of delivering a loader to the device prior to the step of delivering the player the loader being configured to 

Optionally the loader has a predetermined expiry time wherein playback session requests made outside of the expiry time need not be fulfilled.

Optimally the session key is incorporated into a location within the library that is known to the loader.

The method may include the step of delivering and decrypting the content to enable it to be played on the player.

In preferred embodiments the method includes the step of encrypting each content segment with an encryption key specified in the request for content.

Optimally each said encryption key is unique. The use of a unique encryption key in each and every request for content ensures that unauthorised users who may obtain a key will only be able to encrypt the current content segment. Obtaining unauthorised access to the entire content file such as a film would require every authentication key to be obtained which is a far more difficult proposition for an attacker.

The present invention may be used to provide digital rights management to any content including material such as film and television programs live action such as sporting events as well as musical and other works.

The method may also be implemented in any device which may be communicatively coupled to a content server via a suitable network protocol including PCs PDA laptop computers and mobile phone handsets.

According to a second aspect of the present invention there is provided a secure content delivery system comprising 

Preferably the content server includes means for generating unique player code that is executable on the or each device to produce the uniquely identifiable and ephemeral player.

Optionally the means for generating the unique player code comprises means for including a unique identifier in player code.

In preferred embodiments the player code comprises one or more libraries that operatively interact with one or more graphics systems associated with the device s operating system the libraries being generated by linking one or more object code files that are adapted to execute in the device s native operating system and wherein the unique identifier is included in the player code by incorporation into the object code files whilst or before those files are linked into the libraries.

Preferably the content server includes means for delivering a loader to the device prior to delivering the player the loader being configured to 

According to a third aspect of the present invention there is provided a software product executable on a content server and adapted to deliver a uniquely identifiable and ephemeral player to a device in response to each individual playback session requested from the device.

Ideally for streaming video content protection systems should be able to control access to content enforce business rules such as number of plays media expiration sharing rights and publisher rights support hardware encryption where possible ensure confidentiality of communication between user and provider detect or prevent attempts to replay sessions and flexibly and dynamically update client side protection systems.

Use of the present invention enables meeting wholly or at least partially each of the above objectives. A key feature of the architecture of the system of the invention is the enforced separation of the public portion of the player ie. the Java applet loader from the private portion of the player the dynamically generated DLLs and session key . Because the private portion of the player is uniquely generated and validated for each playback session the distributor achieves a high level of assurance that playback sessions are unique and have not been replayed.

The approach of the invention largely eliminates the risks associated with the most common attack vectors particularly player cloning and key extraction. Although complete security against the most determined attackers is seldom if ever guaranteed the invention makes attack in almost all modes sufficiently difficult and thus expensive to reduce the likelihood of such attack significantly. Notably 

Turning to as diagrammatically illustrated a process in accordance with the present invention operates over the Internet and supplies users with media content such as films television programs or live event broadcasts by streaming the content from a content server to the device through which the Internet connection is made. The content server may form part of a larger server installation that includes authentication and payment gateways that in combination provide content protected media streaming to viewers.

The present invention may be implemented on any device that enables Internet connectivity including PCs laptops mobile phones personal data assistants and digital set top boxes.

A schematic illustration of a suitable device is provided in . The device is a general purpose computing device which includes a main memory on which a suitable operating system is installed. As known to those skilled in the art the operating system provides Application Programming Interfaces APIs for application programs to access the devices hardware components such as hard drive graphics card sound card optical drive and the like.

An Internet browser is also installed along with a virtual machine such as the Java JVM for executing byte code compiled programs such as Java applets. The virtual machine includes a secure sandbox area for safely running untrusted programs.

Referring now to the steps of the method for content delivery to the device shown in are illustrated. At step the content server receives a request to commence a playback session from a device over the Internet . In response at step the content server delivers a Java Archive JAR file referred to as a player shim that has been digitally signed by the vendor of the content delivery software running on the content server to the requesting device . Of course other ActiveX objects could be used instead of files in the JAR format.

As known to those skilled in the art digitally signed software has progressed through a trust chain operated by a trust provider to give an assurance to users that the software emanates from a known source. The user is then free to decide whether to run the software on their own system depending on their knowledge of that source.

The player shim is a small 60 KB file which once downloaded requests permission from the operating system to execute code outside of the virtual machine security sandbox .

In the event that permission is granted the player shim which contains a Java applet at step requests delivery of a unique and ephemeral player to play the content which the user has requested from the content server.

At step the requested player is generated on the content server. The player is generated by linking object files which are pre compiled to be executable in the particular operating system environment of the requesting device into one or more suitable dynamic link libraries DLLs . Compiled player object code is maintained on the content server for all major operating systems Windows Linux Mac etc . Details of the device s operating system are provided to the content server in the request for delivery of a player so that the correct player is served to the device.

A unique session key is incorporated into the DLLs as part of the process of linking object files into DLLs. The session key serves as a unique identifier for the player and thereby establishes a one to one mapping between playback sessions and the player for that session. The location of the session key is known to the requesting player shim . However the linking process is such that the location of the session key is difficult to determine and the key never leaves designated context inside the DLL .

The session key is also stored at the content server in a session database in order to identify the playback session in accordance with the authentication process described below.

The player shim is programmed so as to expire within a few minutes of receipt on a device . Accordingly it is necessary to download a new shim if a request for a player is not made within the expiry time. These temporally limited Java applets narrow the window an attacker might have to break individual session keys.

At step the generated DLLs with the embedded session key are delivered to the device. The DLLs are directly loaded into the main memory of the device under the control of the player shim . The DLLs however are not installed on the operating system or written to the device s non volatile storage and are thus ephemeral in the sense used in this specification.

The DLLs once installed hook into the operating system graphics subsystems via suitable API s to actually display the requested content which is streamed to the device in step .

After the player shim downloads the DLLs the session key is extracted from the location that is known to or obtainable by the player shim . As described in further detail below with reference to the session key is used by the player in playing the streamed content which occurs by way of a segmented delivery and playback of individual segments of media data.

Turning to at step the player generates a unique encryption key known as the working key for use in encrypting the content that will be streamed to the player.

At step the player issues a request over the Internet to the content server for a segment of media data. The working key generated in step is included in the request for the media data segment and is therefore also forwarded to the content server .

At step the device receives the requested media segment from the content server which in step is played on the player . The most recently received media data segment may be loaded immediately into the player for playback or queued on the device for playback after older segments have been played.

After a predetermined polling interval the size of which is dependent on the length of the media data segments the method returns to step with the player generating a new working key to be used in a new request for a segment of media data. This new request which contains the new working key is encrypted using the existing session key .

The process continues until the requested media content has been played in its entirety on the media player .

The process of playing a media data segment described in step above is described in detail with reference to . At step the received segment of media data is decrypted using working key which was generated in step above and specified in the request to the media server for that media data segment.

At step the decrypted data is decoded via a routine supplied with the DLLs . The particular decoding routine that is used will of course depend on the format in which the media content was originally encoded. Any suitable codec may be used with the present invention such as On2 s VP6 code.

At step the media data segment is played by the media player by supplying the stream of decoded video data to appropriate operating system API s which in turn pass the data to drivers for video display hardware whereupon it is displayed for the user.

As described in WO 03 005190 providing a decryption routine with a media player allows video content to be played on a device without requiring the decryption routine or any other media player components to be previously entered on the operating system . The media player delivered to the device in response to each individual playback session can thus be made ephemeral.

Referring again to a test is performed at step to determine whether the current segment is the final segment to be played as part of the requested playback session. The process terminates in the event that the current segment is the final segment and otherwise returns to the decryption step to process a later received media segment.

After playing the final segment at step the player including the shim DLLs and session key are wiped from the devices main memory .

The steps carried out on the media server in fulfilling requests for media content are described by reference to . At step the content server receives a request for a media data segment as per step above. A test is performed at step to determine whether a further media data segment is available or whether the requested content has been completed.

Where further segments are available for delivery a test is performed at step to determine whether there is a valid and current session key associated with the requesting playback session. The test involves retrieving a session key from the session database and attempting to decrypt the received request.

As noted above each request for a media segment is encrypted using the session key for the relevant playback session. Accordingly any failure of the server to successfully decrypt the request for content equates to an unauthorised reuse of an expired session key whereupon no content is delivered in response to that request.

Conversely a successful decryption of a content request equates to the presence of a valid and current session key.

At step the working key included in the request as per step above is extracted from the request and used at step to encrypt the requested media data segment.

The encrypted media data segment is then delivered at step to the user device over the Internet via the HTTPS protocol.

The sequence diagram of provides and overview of the operation described above illustrating the message and data flow between the user s browser the player shim the ephemeral player referred to as the Vividas player the content server and the authorisation gateway.

As discussed above the invention serves to overcome a number of disadvantages of the prior art. In particular the feature of an enforced separation between the public half of the player the player shim and the private half the dynamically generated DLLs and session key which is uniquely generated and validated for each playback session provides a high level of assurance to rights holders that playback sessions are unique and have not been replayed.

Moreover because the player is unique and receives media in randomised and encrypted segments after which the player is lost from the main memory of the device the chances of an attacker stripping or modifying content entitlements to gain unauthorised access to the content are reduced.

Furthermore because the dynamically generated working keys are also never saved to the device s secondary storage the keys cannot be easily extracted and copied and used to obtain unauthorised access to the content.

Finally because a standalone media player is delivered in response to each unique play back session any vulnerabilities in the player itself may be conveniently addressed. This is not the case for installed media players where updates must be made through software patches delivered to each instance of the player.

Modifications and improvements to the invention will be readily apparent to those skilled in the art. Such modifications and improvements are intended to be within the scope of this invention

The word comprising and forms of the word comprising as used in this description and in the claims do not limit the invention claimed to exclude any variants or additions. Modifications and improvements to the invention will be readily apparent to those skilled in the art. Such modifications and improvements are intended to be within the scope of this invention.

