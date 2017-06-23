---

title: Delivering files to a mobile device
abstract: Among other things, in controlling a download of one or more files from a server to a mobile device, account is taken of at least two of: an urgency of the file, the existence of a user-indicated preference about the download, a power status of the mobile device, and a network connectivity status of the mobile device.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08027671&OS=08027671&RS=08027671
owner: Penthera Partners, Inc.
number: 08027671
owner_city: Pittsburgh
owner_country: US
publication_date: 20080114
---
As shown in consider a client application that delivers files from a remote server to a mobile device . From time to time files are created on the remote server. Shortly after they are created on the remote server these files need to be delivered to the mobile device where they are stored on the device s persistent storage .

In the email service provided on a RIM Blackberry device for example once the software on the mobile device is set up email messages automatically arrive when they are available with no user action required.

In general in an aspect in controlling a download of one or more files from a server to a mobile device account is taken of at least two of a power status of the mobile device a network connectivity status of the mobile device an urgency of the file and the existence of a user indicated preference about the download.

Some implementations include one or more of the following features. The controlling includes suspending a download of a file that is occurring when a power level or network connectivity degrades during the download. The suspending of the download is based on a set of rules or heuristics. The suspended download is resumed when the power level or network connectivity improves during the suspension. The resumed download does not include at least some of the file or files that were downloaded before the suspension. The resumed download does not include one or more pieces of a file that were downloaded before the suspension.

In general in an aspect download of a file from a server to a mobile device through a network is controlled by breaking the file into pieces to be sent separately monitoring conditions of the mobile device and the network with respect to each piece considering suspending download of a subsequent piece if the conditions deteriorate with respect to a piece.

Some implementations include one or more of the following features. The conditions are monitored after each piece is sent and before download of the subsequent piece has begun. A partial download of a file is allowed to continue under deteriorated conditions if predetermined circumstances exist.

In general in an aspect a user of a mobile device to which large files are normally downloaded automatically from a server based on the user s preferences can initiate a download by invoking a sync now option on a user interface of the mobile device.

In general in an aspect at a mobile device a sync signal is received from a server with respect to one or more large files to be downloaded and to the sync signal is responded to by requesting and accepting a download of the one or more large files.

In general in an aspect at a mobile device an indication is displayed to a user of the time when a download of one or more large files to the mobile device is expected to occur.

In general in an aspect an amount of bandwidth used to download one or more large files to a mobile device is adjusted based on a time of day when the download is to occur.

Some implementations include one or more of the following features. The amount of bandwidth used at a given time of the day is governed by an amount paid by a user of the mobile device.

In general in an aspect a log of download activity with respect to one or more large files that are downloaded to the mobile device is sent from a mobile device to a server.

In general in an aspect a user of a mobile device can specify one or more types of files that are to be downloaded to the mobile device and the specification of file types is stored in a server in association with an identification of the mobile device or the user.

In general in an aspect at a server one or more files are selected to be downloaded to a mobile device based on stored preferences of a user of the mobile device and stored information about files that were previously downloaded to the user s device.

In general in an aspect a list of files that are in process of being transmitted to a client mobile device but which have not yet been completely transmitted to the device is displayed to a user of the device

Implementations may include one or more of the following features. The displaying includes showing a percentage of at least one of the listed the files which has been transmitted. The displaying can occur at the mobile device. The displaying can occur on a web page.

These and other features and aspects and combinations may also be expressed as methods apparatus systems program products databases means for performing functions and in other ways.

Other advantages and features will become apparent from the following description and from the claims.

Some of the files in are large. For example a 30 minute audio a 10 minute video file and a collection of 100 web pages may be from 1 MB to 500 MB or larger.

In the technique described here the user of the mobile device never needs to take any explicit action to query for new files on the server nor to fetch the files from the server. Delivery of the new files for example over an IP network can occur automatically and without explicit user action or knowledge. There is no need for example to press any key on the mobile device or to attach a cable to the device to cause the file delivery to occur.

In contrast typical files delivered to mobile devices today such as email messages audio files and individual web pages are typically in the 10 KB to 200 KB range each.

Delivering a file that is tens or hundreds of megabytes to a mobile device presents challenges that are absent in delivering smaller files. With large files a complete download may take tens of minutes or even hours depending on the speed of the connection. During this time conditions may change. For example at the start of the download the mobile device may be within an area with excellent wireless network coverage but as the download progresses the network conditions may degrade.

Also as the download progresses the device s battery may lose its charge to a level at which continuing the file downloading risks depleting the battery. Generally speaking small file applications music downloads email web browser are not and need not be sensitive to these issues. In other words downloading a file that is large may entail a time delay that implicates one or more other factors in the strategy used to determine the manner and timing of the download.

In the technique described here an application manages the delivery of these large files from the remote server to the mobile device in a way that is sensitive to the following considerations 

Network. The mobile device has one or more network interfaces e.g. GPRS EDGE CDMA EVDO WiFi Bluetooth or USB cable tethered to a host computer each of which can take advantage of a network resource for connecting to the Internet or other communication network . This connection is the last hop for data traveling over the IP network from the server to the device. The availability of one or more of these network resources will vary from time to time as for example the mobile device moves in and out of network hotspots. For example at one moment WiFi and EDGE may be available a few minutes later only EDGE may be available.

Power. The mobile device s power status varies from time to time depending for example on whether the device is charging or how long it has been on battery.

Timeliness. Certain files are time sensitive and may need to be delivered right away e.g. a stock ticker update . Other files are relatively time insensitive and a delay of hours in delivery may be acceptable e.g. a movie trailer . Each file stored on the remote server may be annotated with an urgency parameter which may be assigned by a creator of the file content or determined based on some other policy.

These considerations are sometimes interrelated. For example a mobile device attempting to receive data over a poor quality network connection can cause a significant drain on its battery.

We shall denote by sync ing the process of copying a file from the remote server to the mobile device.

We describe a method for sync ing that is sensitive to the above considerations. The method takes into account a set of factors two or more in determining a sync ing policy by which we mean whether and how often to sync. In some implementations there is a particular algorithm used to take into account these factors to implement a sync ing policy.

As shown in an example of the technique described here includes three parts a client a server and a file repository. The client is a software application that resides on the mobile device . The server is comprised of a set of software components including a web portal a sync module a log upload module and a database . The file repository includes a file system storing files for subsequent delivery to devices and an application that manages the delivery of those files over an IP network an example of such an application is the Apache HTTP server http httpd.apache.org .

The client may be installed by the device manufacturer OEM before delivery to the retail outlet which sells or delivers the device we sometimes refer to the mobile device simply as a device to the end user. Alternatively the client may be installed by the end user after he has acquired the device by downloading the software application from the Internet.

The application performs these steps transparently to the user. That is the user need not take any action to cause the steps to be performed and the user need not be made aware of any of the steps occurring. New files are delivered hourly daily weekly directly to the mobile device. No user action is required. This is similar to the behavior of a home Digital Video Recorder DVR .

Once the files have been downloaded they can be stored on the device s file system. For example on a Windows Mobile device the files could be stored in the My Documents folder. The user can access them manually using existing tools on the mobile device e.g. a File Manager application on a Windows Mobile device .

However because user access to a device file system is not always available e.g. on many Java based phones and because even when such access is available it is not always intuitive the client may include an application that provides a user friendly access to a list of downloaded and currently available files. The application may enable the user to view information about the available files and . As shown in the application display a menu containing an option to manually force a sync ing with the server. The application may also allow the user to view files that are scheduled for delivery and or in transit but not yet fully downloaded. The application may also allow for users to change some aspects of the behavior of the client application and show some details about the version and copyright information of the application .

The delivered files may be of various types. For example web pages e.g. HTML audio files e.g. MP3 video files e.g. h.264 or WMv9 or Flash and so on. The application need not itself provide rendering playout presentation for any or all of these file types. Instead the application may interface with existing applications web browser media player etc. on the device through standard application programming interface API calls. Once the user selects a file from the list or from the native file browser the appropriate external application is launched to render the file .

The server s behavior need not be a synchronous step by step process but rather can be a set of tasks that occur asynchronously as the server is contacted by various mobile devices and web based terminals . The server s behavior in some implementations includes the following with reference again to 

When a mobile device queries the sync module about the presence of new files the sync module performs a multi step process to determine if any such files are present. In some implementations that process includes the following 

Instead of performing only a one time check to decide whether to sync or not prior to a download and then downloading one or more files the protocol also checks the device s conditions power network during the download. To accomplish this in some examples the file in may be split into pieces and which are sent individually and The client checks the conditions after every piece is received and then continues or not the download at its discretion. The constituent pieces of each file are reassembled at the client as they arrive or alternatively when the final piece is downloaded. Should conditions deteriorate and force the client to suspend downloading the download will resume from the suspended point as opposed to from the beginning of the file when conditions are suitable.

The protocol also allows for the client to continue downloading for some limited period of time even if conditions have deteriorated.

The protocol allows for a sync we sometimes refer to a sync ing procedure simply as a sync to be initiated in several ways.

One way is to use a timer on the client when the timer expires the client queries the server for the presence of new files. In the sample algorithm set forth below the proposed counter starts at 300 seconds. To perform the count down the client application must be always running on the device. This is much like a standard mobile application e.g. a game which is either active or closed and when closed does not consume any random access memory on the device. In these implementation the client application must be auto started when the device is booted and it must persist while the device is on. This is analogous to a home DVR which is always on.

A second way to initiate a sync is in response to a user request. The client application may provide a Sync Now button or link. If user selects it the application may 

 2 Evaluate the downloadAllFiles variable in the below algorithm based on current conditions. If the variable evaluates to true then the sync is performed. If not the cause for failure may be presented to the user with a prompt e.g. The battery is only full. Sync ing may drain the battery further and risk draining it altogether. Do you wish to sync anyway 

A third way to initiate a sync is from the server. In some settings the client may be capable of receiving asynchronous messages directly from the server. For example a RIM Blackberry device provisioned to use a Blackberry Enterprise Server BES can receive signals directly from the server through an MDS component. Therefore the client application need not continuously poll the server for new files nor remain active. The application can instead be inactive until the server signal arrives and causes the device to launch the application.

The features described above and other features in various combinations can be implemented in a wide variety of algorithms. Among other things different algorithms may specify different techniques for suspending and subsequently resuming file downloads as conditions change. We provide one example of an algorithm below. We first introduce several terms and parameters that are relevant to the example.

Voice and SMS traffic generate more revenue per bit to the owner of a mobile network than generic data traffic. Therefore during daytime hours e.g. 9 AM 7 PM when voice and SMS traffic is high and spare capacity limited network owners are likely to discourage network intensive applications. On the other hand most cellular networks are latent during off peak hours such as 9 PM 6 AM. During this time window mobile network owners are likely to be more receptive to network intensive applications.

In short bandwidth on a wireless radio access network e.g. EDGE or EVDO is a commodity whose value to the network owner varies over time.

The application can accommodate this constraint by disabling sync activity altogether during daytime hours when sync ing requires mobile network access. The result is that users may only receive updates during the evening hours.

Alternatively the application can throttle its mobile network bandwidth usage to an acceptable level during the daytime hours by waiting a specified period of time between downloading chunks of data. For example the application can cut by 50 its bandwidth usage by pausing for timeForThisChunk seconds after the chunk e.g. a piece of a file has been downloaded. Similarly the application can cut by 67 its bandwidth usage by pausing for twice this amount of time.

A network operator can offer a tiered level of service to its customers in which those customers who pay for a premium service are permitted higher throughput for during the day downloads over the mobile network. The application used by premium customers would not be forced to pause as long or at all between chunk downloads.

