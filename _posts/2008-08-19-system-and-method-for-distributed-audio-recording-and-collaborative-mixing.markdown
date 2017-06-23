---

title: System and method for distributed audio recording and collaborative mixing
abstract: Two or more wireless devices can be independently controlled by their respective users, a mixer component, or a leader wireless device to perform audio recording, convert the recorded audio into a standard or proprietary audio stream format, and transmit the audio stream to a server. The real-time clocks of two or more participating wireless devices can be synchronized. A wireless device can insert timestamps into the audio stream to facilitate the mixing operation. Mixing of the two or more audio streams recorded by wireless devices can be performed by a mixer component either in real time (contemporaneously with the recording) or asynchronously with respect to the recording. The mixing can be performed in a fully automated mode, and/or in an operator-assisted mode.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08301076&OS=08301076&RS=08301076
owner: Syracuse University
number: 08301076
owner_city: Syracuse
owner_country: US
publication_date: 20080819
---
This application claims priority under 35 U.S.C 119 e of the following provisional application U.S. Ser. No. 60 965 581 filed Aug. 21 2007 entitled SYSTEM AND METHOD FOR DISTRIBUTED AUDIO RECORDING AND COLLABORATIVE MIXING the content of which is incorporated herein by reference.

The disclosed invention was made with government support under a grant awarded by the National Science Foundation under Grant No. 0227879. The United States Government has certain rights in the invention.

This invention relates generally to wireless devices capable of audio recording and more specifically to distributed audio recording and collaborative mixing by two or more wireless devices.

Wireless devices such as laptop computers personal digital assistants PDAs cellular phones etc. bring new resources to distributed computing. In addition to typical computational resources such as CPU disk space and applications wireless devices increasingly employ cameras microphones GPS receivers and other types of sensors. A wireless device by definition has at least one wireless communication interface e.g. cell radio frequency Wi Fi or Bluetooth . Users increasingly take wireless devices with them to new places in both their personal and professional lives. The ability of wireless devices to form ad hoc grids allows using the available resources in a collaborative manner by aggregating information from the range of input output interfaces found in wireless devices by leveraging the locations and contexts in which wireless devices are located and finally by leveraging the mesh network capabilities of wireless devices. Wireless grids allow coordinated collaboration of heterogeneous inherently unreliable devices across unreliable network connections. The inherent unreliability of wireless devices is primarily caused by the fact that those devices are due to their mobile nature battery powered. Thus reducing the power consumption and mitigating the inherent unreliability are two goals of a paramount importance. Thus there is a need in distributed systems and applications which can assist in achieving both goals by off loading processing and data management to non mobile devices or to wireless devices which can be reachable with less transmitter power.

There is provided a system for distributed audio recording and collaborative mixing by combining audio streams from two or more sources into a single stream that is composed of two or more channels. Leveraging the spatial location of the devices allows the producing of high quality multi channel sound e.g. stereo sound or surround sound .

Two or more wireless devices can be located near a sound source e.g. at a business meeting symphony concert or a live lecture. The wireless devices can be independently controlled by their respective users by a mixer component or by a leader wireless device. The wireless devices can convert the recorded audio into a standard or proprietary audio stream format and transmit the audio stream to a mixer component which can run on a remote computer.

The real time clocks of two or more participating wireless devices can be synchronized. A wireless device can insert timestamps into the audio stream to facilitate the mixing operation.

Mixing of the two or more audio streams recorded by wireless devices can be performed by a mixer component either in real time contemporaneously with the recording or asynchronously with respect to the recording. The mixing can be performed in a fully automated mode and or in an operator assisted mode.

The drawings are not necessarily to scale emphasis instead generally being placed upon illustrating the principles of the invention. In the drawings like numerals are used to indicate like parts throughout the various views.

There is provided a system for distributed audio recording and collaborative mixing by combining audio streams from multiple sources into a single stream that is composed of multiple channels. Leveraging the spatial location of the devices allows to produce high quality multi channel sound e.g. stereo sound or surround sound .

The wireless devices can have a user interface and or an application programming interface API allowing to at least start and stop the audio recording and streaming operations. In one embodiment the wireless devices can be independently controlled by their respective users via a user interface. In another embodiment the wireless devices can register with and be controlled by a mixer component not shown in .

The mixer component can run on a remote computer . A computer herein shall refer to a programmable device for data processing including a central processing unit CPU a memory and at least one communication interface. A computer can be provided e.g. by a personal computer PC running the Linux operating system.

Computer can be connected to network . While different networks are designated herein it is recognized that a single network as seen from the network layer of the Open System Interconnection OSI model can comprise a plurality of lower layer networks e.g. what can be regarded as a single IP network can include a plurality of different physical networks .

In one aspect wireless device can be provided by a PDA and can connect to network via a wireless access point . In another aspect wireless device can be provided by a cellular phone and can connect to network via General Packet Radio Service GPRS gateway .

The mixer component can transmit control messages to the wireless devices . The control messages can be encapsulated into e.g. Blocks Extensible Exchange Protocol BEEP . The control messages can include a start recording message and a stop recording command.

Upon receiving a start recording command the wireless device can activate its microphone to start recording. In one embodiment the wireless device can start transmitting the recorded audio stream back to the mixer component in real time synchronously with the recording . In another embodiment the wireless device can buffer the audio stream being recorded and asynchronously with respect to the recording transmit the buffered stream back to the mixer component. In a yet another embodiment the wireless device can store the recorded audio stream in its memory for later transmission to a mixer component.

Upon receiving a stop recording command the wireless device might stop recording audio stream. In one embodiment the wireless device might further stop any synchronous transmission of the audio stream to the mixer component. In another embodiment the wireless device can further complete any asynchronous transmission of a buffered audio stream to a mixer component.

In another embodiment the wireless devices can elect a leader wireless device which will coordinate the recording by other participating wireless devices. The leader election can be performed e.g. using an algorithm described in A Leader Election Protocol For Fault Recovery In Asynchronous Fully Connected Networks by M. Franceschetti and J. Bruck available at http caltechparadise.library.caltech.edu 31 00 etr024.pdf.

A skilled artisan would appreciate the fact that any other suitable algorithm of the leader election can be used without departing from the scope and spirit of the invention.

The wireless devices can convert the recorded audio into a standard or proprietary audio stream format e.g. MPEG 3 RealAudio Windows Media Audio etc. The resulting audio stream can be stored by the recording device locally and or transmitted to a remote computer via a wireless access point and network . Wireless devices with no direct connection to wireless access point can leverage the mesh network capability of a group of wireless devices e.g. by establishing a wireless mesh network defined in IEEE 80211s.

In one embodiment wireless devices can have their real time clocks unsynchronized. In another embodiment the real time clocks of two or more participating wireless devices can be synchronized using e.g. Network Time Protocol NTP by Network Working Group available at ftp ftp.rfc editor.org in notes rfc1305.pdf. A wireless device can insert timestamps into the audio stream to facilitate the mixing operation.

Mixing of the two or more audio streams recorded by wireless devices can be performed by a mixer component not shown in running on a remote computer . The mixing can be performed either in real time synchronously with the recording or asynchronously with respect to the recording. Wireless devices can also receive the mixed audio stream back from the mixer thus allowing the users of wireless devices to listen to the mixed stream.

Operation of the mixer component in a fully automated mode is now described with reference to . In one embodiment the mixing can be performed based upon timestamps included into the audio streams recorded by the individual wireless devices. The wireless device upon receiving a start recording command from a mixer component at time can transmit to the mixer component a message containing the start time timestamp followed by one or more messages containing the audio stream being recorded. Upon receiving a stop recording command from the mixer component at time the wireless device can stop recording and continue transmitting the buffered audio stream. Upon completing the transmission of the buffered audio stream at time the wireless device can transmit a message containing the timestamp corresponding to time when it stopped the recording. Thus the mixer component can use the start time and end time of the audio stream file received for synchronizing it with other audio stream files. The mixer component can also calculate a time stamp for any intermediate point of the data stream file by linearly interpolating the start time and end time timestamps.

In another embodiment where the real time clocks of the participating wireless devices can not be synchronized reliably the individual recordings can be synchronized in time based upon one or more clearly distinguishable events present in all the recordings being synchronized. A clearly distinguishable event can be e.g. a change in the signal amplitude at a given frequency range where the amplitude level changes by a value exceeding a pre defined amplitude threshold within a time period not exceeding a pre defined duration.

The operation of the mixer component in an operator assisted mode is now described. Graphical representations of the sound waves over two or more sound channels e.g. graphs of the audio signal amplitude over time can be presented to the user via a graphical user interface GUI as shown in . The GUI can include two or more graph windows . Each of the graph windows can show a waveform graph of an audio signal received from a wireless recording device. The GUI can further include two or more scroll bars using which a user can scroll the respective graphs along the time axis. The GUI can further have two or more text output fields where the timestamp corresponding to the start of the audio stream fragment being displayed in the respective graph window can be automatically displayed according to the position of the respective scroll bar within the recorded audio stream file. The GUI can further have two or more text output fields where the timestamp corresponding to the end of the audio stream fragment being displayed in the respective graph can be automatically displayed according to the position of the respective scroll bar within the recorded audio stream file.

The user can choose a common point of visual distinction e.g. a point of rapid signal amplitude change and align the graphs using the view slide controls and then pressing the Sync button so that two or more sound channels are synchronized at the common point 

two or more wireless devices capable of audio recording wherein said two or more wireless devices are located near a sound source to be recorded 

wherein each wireless device of said two or more wireless devices having an interface allowing at least start and stop audio recording and streaming operations 

wherein each wireless device of said two or more wireless devices being configured to transmit a recorded audio stream to a mixer component and

a mixer component configured to combine two or more audio streams received from said two or more wireless devices into a multi channel audio stream by synchronizing in time said two or more audio streams said synchronization being performed based upon one or more clearly distinguishable events present in all said two or more audio streams.

wherein said two or more wireless devices are located near a sound source to be recorded each wireless device of said two or more wireless devices having an interface allowing at least start and stop audio recording and streaming operations each wireless device of said two or more wireless devices being configured to transmit a recorded audio stream to a mixer component each wireless device of said two or more wireless devices having a real time clock each wireless device of said two or more wireless devices being further configured insert timestamps into said recorded audio stream and

a mixer component configured to combine two or more audio streams received from said two or more wireless devices into a multi channel audio stream by synchronizing in time said two or more audio streams based upon said timestamps.

While the present invention has been particularly shown and described with reference to certain exemplary embodiments it will be understood by one skilled in the art that various changes in detail may be affected therein without departing from the spirit and scope of the invention as defined by claims that can be supported by the written description and drawings. Further where exemplary embodiments are described with reference to a certain number of elements it will be understood that the exemplary embodiments can be practiced utilizing less than the certain number of elements.

