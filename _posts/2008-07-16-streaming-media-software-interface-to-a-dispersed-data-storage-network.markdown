---

title: Streaming media software interface to a dispersed data storage network
abstract: A client computer streams a digital media presentation from a dispersed data storage network including a plurality of slice servers. A dispersed data storage network access component streams data directly from the dispersed data storage network and passes data to a media player, also residing on the client computer.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07962641&OS=07962641&RS=07962641
owner: Cleversafe, Inc.
number: 07962641
owner_city: Chicago
owner_country: US
publication_date: 20080716
---
This patent application is claiming priority under 35 USC 120 as a continuation in part patent application of co pending patent applications 

1. entitled BLOCK BASED ACCESS TO A DISPERSED DATA STORAGE NETWORK having a filing date of Oct. 9 2007 and a Ser. No. 11 973 613 which is incorporated herein by reference 

2. entitled SMART ACCESS TO A DISPERSED DATA STORAGE NETWORK having a filing date of Oct. 9 2007 and a Ser. No. 11 973 622 which is incorporated herein by reference 

3. entitled ENSURING DATA INTEGRITY ON A DISPERSED STORAGE NETWORK having a filing date of Oct. 9 2007 and a Ser. No. 11 973 542 which is incorporated herein by reference 

4. entitled VIRTUALIZED STORAGE VAULTS ON A DISPERSED DATA STORAGE NETWORK having a filing date of Oct. 9 2007 and a Ser. No. 11 973 621 which is incorporated herein by reference 

5. entitled SYSTEM METHODS AND APPARATUS FOR SUBDIVIDING DATA FOR STORAGE IN A DISPERSED DATA STORAGE GRID having a filing date of Sep. 30 2005 and a Ser. No. 11 241 555 which is incorporated herein by reference 

6. entitled BILLING SYSTEM FOR INFORMATION DISPERSAL SYSTEM having a filing date of Apr. 13 2006 and a Ser. No. 11 403 684 which is incorporated herein by reference 

7. entitled METADATA MANAGEMENT SYSTEM FOR AN INFORMATION DISPERSED STORAGE SYSTEM having a filing date of Apr. 13 2006 and a Ser. No. 11 404 071 which is incorporated herein by reference 

8. entitled SYSTEM FOR REBUILDING DISPERSED DATA having a filing date of Apr. 13 2006 and a Ser. No. 11 403 391 which is incorporated herein by reference 

9. entitled REBUILDING DATA ON A DISPERSED STORAGE NETWORK having a filing date of Mar. 31 2008 and a Ser. No. 12 080 042 which is incorporated herein by reference and

10. entitled FILE SYSTEM ADAPTED FOR USE WITH A DISPERSED DATA STORAGE NETWORK having a filing date of Jul. 14 2008 and a Ser. No. 12 218 200 which is incorporated herein by reference.

This application incorporates by reference the following source code files submitted on a compact disc along with this application 

The present invention relates generally to systems apparatus and methods for distributed data storage and more particularly to systems apparatus and methods for distributed data storage using an information dispersal algorithm so that no one location will store an entire copy of stored data and more particularly still to systems apparatus and methods for interfacing a media player application to a dispersed data storage network.

Dispersed data storage networks DDSNs store data as an arbitrary number of data slices generally with each data slice being stored on a separate slice server. Before a collection of data is stored it is segmented into a number of data segments which may be of fixed or variable sizes. Each data segment is then sliced into a predetermined arbitrary number of data slices. Each data slice will generally contain minimal or no usable information by itself but instead must be combined with other data slices to reconstruct a usable data segment. DDSNs offer a number of advantages over traditional storage solutions including greater security and reliability.

Prior art DDSN systems such as those offered by Cleversafe Inc. of Chicago Ill. have generally used an access computer sometimes referred to as a Grid Access Computer or an Accesser . The access computer is generally a high performance server adapted to provide DDSN access to a large number of clients such as an office of 20 or more users. Generally the access computer does not have to be specified to handle the worst case scenario of each client computer accessing a maximum amount of data from the DDSN simultaneously as office use often comes in bursts as a file is read or written. However some types of usage such as streaming media require a continuous stream of data.

Streaming digital media is well known in the art with Adobe Flash Windows Media Audio and Video and QuickTime being well known examples. Streaming media is generally served to clients by a streaming media server which is specified to handle some number of simultaneous streams. Media serving platforms use a number of techniques to share streams across multiple streaming media servers such as round robin allocation. Prior art media serving platforms have not made use of DDSNs and instead have utilized individual or shared Redundant Array of Independent Drives RAID or Storage Area Networks SAN .

One technique used by media providers to improve reliability and quality of service for streaming digital media presentations is the use of Content Delivery Networks CDNs . A CDN is a network of computers that cooperate to deliver content to users. Generally content is replicated among servers on an as needed basis so that a server with the most desirable performance characteristics can serve content to a particular client. Often content is replicated to the network so that it is available from a number of geographic locations based on the assumption that a server located geographically close to a particular client will provide a better quality of service connection if all else is equal.

A particular digital media stream will usually provide a specific quality. For example a digital media presentation may be encoded at 720 pixels by 480 pixels at 30 frames with second with audio provided as 64 kilobits per second MP3. If quality levels are desired to serve users with less modern hardware or slower network connections different media presentations will be encoded at the desired quality levels. Certain streaming media technologies allow a player to scale the frame rate of streamed video by skipping frames. This may result in jerky video but will still allow a viewer to view the presentation.

More recent advances in encoding technology allow a single presentation to scale across a number of quality levels. For example Flexible Block Wavelet encoding allows a streaming media presentation to scale across an arbitrary number of resolutions based on the bandwidth available to a particular client and the ability of the client to process data.

Accordingly it is an object of this invention to provide a system apparatus and method for accessing streaming digital media stored by a DDSN.

Another object of the invention is to provide a system apparatus and method for accessing streaming digital media stored by a DDSN in a cross platform manner.

Another object of the invention is to provide a system apparatus and method for implementing a high performance streaming digital media player plugin to access streaming digital media stored by a DDSN.

Another object of the invention is to provide a system apparatus and method for accessing streaming digital media stored by a DDSN from a client computer as opposed to from an access computer.

Another object of the invention is to provide a system apparatus and method for accessing streaming digital media stored by a DDSN from a client computer that is resilient to interruptions of network service disabling a portion of the DDSN.

Another object of the invention is to provide a system apparatus and method for accessing streaming digital media stored by a DDSN so that the quality of the presentation scales with the robustness of the DDSN.

Other advantages of the disclosed invention will be clear to a person of ordinary skill in the art. It should be understood however that a system method or apparatus could practice the disclosed invention while not achieving all of the enumerated advantages and that the protected invention is defined by the claims.

The disclosed invention achieves its objectives by providing a system for streaming a digital media presentation to a client computer from a dispersed data storage network. The dispersed data storage network includes a plurality of slice servers each of which may be located in a separate facility. The digital media presentation is broken into a plurality of data segments and each data segment may only be reconstructed by combining data slices from more than one of the plurality of slice servers. Within the system a client computer such as a personal computer or a cellular telephone is coupled to a network with access to the dispersed data storage network. A dispersed data storage network access component reads data segments from the dispersed data storage network and passes them to a media player operating on the client computer which presents the streamed digital media presentation to a user.

In one embodiment both the media player and the dispersed data storage network access component are implemented using a cross platform technology. Where this is not possible the dispersed data storage network access component may be implemented as a cross platform component and interfaced to the media player with a plugin. The plugin may interface with the dispersed data storage network access component using a socket or Java Native Interface. Alternatively the dispersed data storage network component may be implemented as a native component and interfaced to the plugin using static or dynamic linking.

In a further embodiment the streamed digital media presentation may be encoded using a scalable technology so that as slice servers become unavailable due to network outages or other reasons the quality of the streamed digital media presentation degrades but is otherwise still accessible.

Turning to the Figures and to in particular a client computer accessing a streaming media presentation is depicted. This architecture represents the simplest way to serve streaming digital media from a DDSN to a client computer using any type of media player. The client computer is coupled to a LAN or the Internet using any type of network technology such as an Ethernet port or a Wireless Network port. A media server contains stream definitions for one or more streaming media presentations. The media server is coupled to a LAN or the Internet using any type of network technology. It should be noted that network and network could be the same network or a different network. The media server accesses streaming digital media through an access computer from a plurality of slice servers coupled to the Internet or some other type of Wide Area Network . Access computer such as those available from Cleversafe Inc. present the DDSN to the streaming media server as a local or networked file system so no interface software would be required for the streaming media server . An example of a refinement that is not depicted would be to integrate the media server with the access computer . This would potentially allow for better performance as network latency would not slow down communications between the media server and the access computer .

The approach of would effectively support all prior art streaming media systems. Further the implemented system would provide for resiliency to network outages across a portion of the DDSN as access to an arbitrary predetermined number of slice servers could be lost and the streaming presentation would still be available to be served to clients. In addition many of the advantages of a content delivery network would be retained as a DDSN generally includes geographically dispersed servers. Further as outlined in U.S. patent application Ser. No. 11 973 622 entitled SMART ACCESS TO A DISPERSED DATA STORAGE NETWORK filed on Oct. 9 2007 assigned to Cleversafe Inc. and hereby incorporated by reference in its entirety slice servers holding applicable content would be ranked by various performance criteria to ensure that the accessing client would receive a high quality of service without the replication of content required with a CDN. However a network failure between the client computer and the streaming media server or between the streaming media server and the access computer would still disable access to the streaming media presentation.

In addition the segmentation process employed by the DDSN can be adapted to provide better performance for streaming video. Specifically the data segments including data from the beginning of the streaming media presentation can be encoded as smaller segments than those later in the streaming media presentation. This will allow a stream to begin presentation quicker.

It should be understood that while this invention has been explained in the context of a software operating on a personal computer system it could be implemented on a variety of different platforms. For example a wireless mobile unit such as a cellular telephone could implement any of the embodiments described by . For example a BREW compliant player could interface with a DDSN access library to stream digital media to a cellular telephone. All such systems would fall within the definition of client computer as used above. Furthermore while the term streaming has been used throughout it should also be understood that the disclosed invention could apply to a progressive download system equally well.

The foregoing description of the invention has been presented for purposes of illustration and description and is not intended to be exhaustive or to limit the invention to the precise form disclosed. The description was selected to best explain the principles of the invention and practical application of these principles to enable others skilled in the art to best utilize the invention in various embodiments and various modifications as are suited to the particular use contemplated. It is intended that the scope of the invention not be limited by the specification but be defined by the claims set forth below.

