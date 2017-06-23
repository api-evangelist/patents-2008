---

title: Method and system for remote visualization client acceleration
abstract: A method, system, and program product is disclosed for remote visualization in which a server window contents is displayed remotely at a client. The client creates a 3D rendering surface on a client graphics card to display a server window contents and receives update data from the server relating to the server window contents. The update data is uploaded to the client graphics card and the graphics processing unit (GPU) is used to decode the update data and render the update data to the 3D rendering surface. The graphical processing unit includes general purpose computing on graphics processing unit functionality to provide the decoding processing.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08253732&OS=08253732&RS=08253732
owner: International Business Machines Corporation
number: 08253732
owner_city: Armonk
owner_country: US
publication_date: 20081222
---
This invention relates to the field of remote visualization. In particular it relates to remote visualization client acceleration.

Remote visualization solutions allow the users of a graphical desktop to interact with graphical applications from a remote machine or thin client.

Thin client viewers receive images over the network which are rendered to give the end user the impression that they are using an application locally on their computer or workstation. Various implementations and algorithms are used in remote visualization applications and they normally employ image compression and they usually send only the parts of the screen that recently changed in order to optimize the bandwidth available in the network.

Remote applications such as the Open Source VNC Virtual Network Computing or Microsoft Remote Desktop Microsoft is a trade mark of Microsoft Corporation in the US. and other countries have recently been enhanced to support 3D visualization applications. These applications use graphics APIs application programming interfaces for 3D rendering and due to the complexity of the rendered objects require special hardware inside the graphics cards to accelerate 3D data processing. For example such graphics APIs include OpenGL Open Graphics Library OpenGL is a trade mark of Silicon Graphics Inc. and DirectX DirectX is a trade mark of Microsoft Corporation in the US. and other countries .

OpenGL is the standard cross platform middleware Software Development Kit SDK for developing 3D applications. This SDK allows the application to access in a multi platform and multi vendor environment various 3D rendering primitives and leverages any and all available hardware support and acceleration on the host system.

DirectX is the Microsoft alternative to OpenGL and allows Windows Windows is a trade mark of Microsoft Corporation applications to use various 3D rendering primitives and leverages any hardware support and acceleration available in the host system.

Most remote visualization enablement software works by drawing the desktop image inside the graphics card of the system server either inside the front buffer inside the back memory buffer or both or inside a virtual frame buffer in system memory fetching the image from the draw buffer compressing the image or parts of it and finally transmitting the compressed data over the network to the client where it will be reproduced. Reproducing is the simple step of drawing the received images to specified coordinates on the client display. Mouse movements and keyboard events are relayed back from the client viewer to the server desktop providing a seamless user experience. Remote visualization applications should do all this without any noticeable application performance degradation at the client and typically this requires image updates at frame rates in or close to 25 frames per second.

The main restriction to remote visualization applications is network latency and bandwidth. Various techniques are used for compression and transmission of the images to the rendering client with the aim of reducing the required network bandwidth. These include Sending partial images corresponding to only the changed sectors of the whole desktop between two successive frames Using different compression schemes i.e. JPEG Joint Photographic Experts Group with varying qualities LZW Lempel Ziv Welch lossless data compression algorithm Frame dropping in which one or more frames is not sent in order to reduce network loads Tuning encoder and decoder performance for specific CPU hardware i.e. using performance optimizations provided through special instruction sets available in Intel Intel is a trade mark of Intel Corporation and other vendor CPUs computer processing units Manipulation of image quality allowing the user to choose better or lower quality in a trade off with interactive performance.

According to an embodiment of the present invention there is provided a method for remote visualization in which a server window contents is displayed remotely at a client comprising the client carrying out a method comprising creating a 3D rendering surface on a client graphics card to display a server window contents receiving update data from the server relating to the server window contents uploading the update data to the client graphics card and using the graphics processing unit GPU to decode the update data and render the update data to the 3D rendering surface.

According to another embodiment of the present invention there is provided a client system for remote visualization in which a server window contents is displayed remotely at a client including a client system comprising a graphics card including a graphics processing unit with general purpose computing on graphics processing unit functionality means for creating a 3D rendering surface on the client graphics card to display a server window contents means for receiving update data from the server relating to the server window contents means for uploading the update data to the graphics card and the graphics processing unit including means for decoding the update data and rendering the update data to the 3D rendering surface.

According to another embodiment of the present invention there is provided a computer program product stored on a computer readable storage medium comprising computer readable program code means causing a computer to perform a method comprising creating a 3D rendering surface on a client graphics card to display a server window contents receiving update data from the server relating to the server window contents uploading the update data to the client graphics card and using the graphics processing unit GPU to decode the update data and render the update data to the 3D rendering surface.

The invention applies an approach to remote visualization where use of graphics APIs and modern graphics cards capabilities are combined to optimize costly image decompression at the remote client. This is achieved by off loading decompression tasks to the graphic hardware GPU and then rendering the full remote desktop image inside a window rendered by the 3D graphic API. The invention applies to the full desktop including 2D and 3D parts and allows different compression schemes to be used.

It is to be noted however that the appended drawings illustrate only example embodiments of the invention and are therefore not considered limiting of its scope for the invention may admit to other equally effective embodiments.

For a better understanding of the present invention together with other and further features and advantages thereof reference is made to the following description taken in conjunction with the accompanying drawings and the scope of the invention will be pointed out in the appended claims.

It will be readily understood that the components of the present invention as generally described and illustrated in the Figures herein may be arranged and designed in a wide variety of different configurations. Thus the following more detailed description of the embodiments of the apparatus system and method of the present invention as represented in is not intended to limit the scope of the invention as claimed but is merely representative of selected embodiments of the invention.

Reference throughout this specification to one embodiment or an embodiment or the like means that a particular feature structure or characteristic described in connection with the embodiment is included in at least one embodiment of the present invention. Thus appearances of the phrases in one embodiment or in an embodiment in various places throughout this specification are not necessarily all referring to the same embodiment.

The illustrated embodiments of the invention will be best understood by reference to the drawings wherein like parts are designated by like numerals or other labels throughout. The following description is intended only by way of example and simply illustrates certain selected embodiments of devices systems and processes that are consistent with the invention as claimed herein.

Referring to a system is provided for remote visualization. A server system is provided on which a graphics application is executed. A remote client system is connected to the server system via a network and receives graphics from the graphics application of the server system over the network for reproducing and display at the client system .

The server system is a data processing system and includes a CPU central processing unit on which the graphics application executes using a graphics API . The server system also includes a graphics card also referred to as a video card graphics accelerator card or display adapter which includes a GPU graphics processing unit including means for rendering the output of the graphics application . The server system also includes a local display means on which the rendered output may be displayed locally.

The server system includes an encoder for encoding the graphics application output updates. The encoding may include compression of the graphics application output updates or conversion in some other form for transmission. The encoder may be processed by the CPU or the GPU or may be partitioned among the two units. The server system includes a network interface for transmitting the encoded graphics application output updates to the remote client system for display via the network .

The client system is a data processing system and includes a CPU . The client system includes a network interface and a graphics API for receiving the graphics application output updates from the server system over the network .

The client system includes a graphics card with a GPU with programming functionality. The GPU may be a GPGPU general purpose computing on graphics processing unit processor. The GPU includes a decoder for decoding the encoded graphics application output updates from the server system . If the graphics application output updates are compressed the decoder is a decompression means. Optionally the decoder may be partitioned between the CPU of the client system and the GPU .

The graphics card includes a rendering means and a full screen 3D rendering surface using the graphics API . The graphics card also includes a memory including an update store for received updates and a cache of previously rendered frames.

The client system has a display for display of the output from the graphics card in the form of the received output from the graphics application executing on the server system .

The client system creates a full screen 3D rendering surface inside the graphical hardware of the graphics card using a graphics API such as OpenGL or DirectX . All the rendering on the client side is performed to this surface . Since the underlying hardware is the same it does not matter what method is used to create this surface .

A connection is established between the client system and a server system which is running something the client wishes to view remotely. The method of communication used is unimportant so long as the client system can receive information from the server system .

Updates to the display on the server side are encoded and sent to the client system for display on the client s display . The type encoding and the method chosen by the server system do not matter so long as an appropriate means to decode the information exists. The programmable nature of the graphics hardware at the client system allows the methods chosen to be essentially pluggable and changeable as required.

The reception of information from the server system is handled by the client system s CPU and hardware which then passes the data to the graphics card hardware for processing. The updates typically contain information about which region of the display to update the size of the updated area the method of compression used along with the actual data.

The first update from the server system is likely to be the slowest as the entire server display must be sent and decoded. Subsequent updates require only changes to the display to be sent and processed.

The data received by the client system is transferred to the graphics card hardware for processing. Typically the data will be stored as in an update store for example as a texture map in the graphics hardware which can then be accessed by the GPU for processing.

The decoder selects an appropriate GPU program to decode and display the server updates. The decoder may upload decoder or decompression algorithms to the GPU . Typically fragment programs are used for image decompression but vertex programs may also be used for example to draw line data which could have been sent as a series of end points. The pluggable nature of these programs allows new methods of transferring data from the server system to the client system to be used not just traditional image compression algorithms.

Again the API used to define these programs is irrelevant so long as the hardware supports the features and capabilities required. Thus the programs may be low level vertex and fragment programs or just as easily shaders written in a high level language such as Cg C for Graphics HLSL High Level Shader Language or GLSL OpenGL Shading Language . The decompression uses the GPU for both 3D and 2D parts of the display.

The chosen GPU program processes the region updates provided by the server system and outputs the results to the 3D rendering surface where they are displayed. Results from previous renders may be cached in a cache and reused in subsequent updates. In such a case only the relevant motion detail need be sent by the server system thus allowing a window to overlay others and be moved without requiring a full update from the server system for the underlying data.

The final image is displayed on the client display utilising the combination of previous frame displays plus any recent updates. The use of the GPU to control the rendering and the use of pluggable means of image decoding frees the client system CPU resources for other tasks.

All client side rendering of the remote visualization application occurs within a single window . In one embodiment the window is an OpenGL window. Within this OpenGL context a single 2D plane will be created upon which received 2D images received from the server system will be rendered. Decoding or decompression of the received images will also be passed through to the GPU resulting in nearly all of the remote visualization s client processing occurring with the GPU . This allows a remote client system to make use of the maximum hardware resources available to it to accelerate the tasks of remote visualization and allow optimum resource availability to the running applications of the client system .

The programmable nature of modern GPUs allow them to serve as a parallel processor to the main CPU s and due to their hardware design they are uniquely suited to performing image processing.

By utilizing the programmable hardware capabilities of the GPU the encoding might not be just compressed image fragments but can include encoded drawing commands. For example an area fill operation can be encoded as a binary command with the following operands position and size on screen pixel colour. An appropriate GPU program can be selected to directly draw the rectangular area with the specified colour instead of forcing the server to compress an image of a uniform coloured rectangle. This allows further bandwidth savings.

Referring to an exemplary system for implementing the server system and client system is described. The systems are both of the form of a data processing system suitable for storing and or executing program code including at least one central processing unit coupled directly or indirectly to memory elements through a bus system . The memory elements can include local memory employed during actual execution of the program code bulk storage and cache memories which provide temporary storage of at least some program code in order to reduce the number of times code must be retrieved from bulk storage during execution.

The memory elements may include system memory in the form of read only memory ROM and random access memory RAM . A basic input output system BIOS may be stored in ROM . System software may be stored in RAM including OS software . Software applications may also be stored in RAM .

The data processing system may also include a primary storage means such as a magnetic hard disk drive and secondary storage means such as a magnetic disc drive and an optical disc drive. The drives and their associated computer readable media provide non volatile storage of computer executable instructions data structures program modules and other data for the system . Software applications may be stored on the primary and secondary storage means as well as the system memory .

The computing system operates in a networked environment using logical connections to one or more remote computers via a network adapter .

Input output devices can be coupled to the system either directly or through intervening I O controllers. A user may enter commands and information into the system through input devices such as a keyboard pointing device or other input devices for example microphone joystick game pad satellite dish scanner or the like . Output devices may include speakers printers etc.

A display device is also connected to system bus via a graphics card . Referring to the procedure for remote visualization operations on the viewer are described with reference to a flow diagram .

A client application is started and tests that the GPU supports GPGPU functionality. If it does not support GPGPU functionality the process ends . If it does support GPGPU functionality the process proceeds.

In the client application a graphics API window is created . A 3D rendering surface is created on the GPU to display the remote desktop contents.

Remote region update information is received from the server via the network using the client system s CPU. Each region update typically contains coordinates size of the region and the encoded data.

The received update data is uploaded to the GPU hardware typically as a texture map. An appropriate GPU program is set up and chosen to process the data for output. The program is used to decode the data and display on the 3D rendering surface. Existing display content plus any received updates make up the final image displayed on the client.

It is determined if there are more updates being received and if so the process loops to receive remote region update information using the system CPU . If there are no further updates the process ends .

Programmable GPUs allow multiple independent encoding or compression methods to be used for each update as appropriate. For example predominantly 2D information that is seldom updated may be compressed via a loss less method while rapidly changing images or 3D image data from the server might be compressed via an aggressive lossy algorithm.

Since all images are to be drawn on a 2D plane in a 3D space varying the sizes of images may be layered to produce the final image. This allows for efficient transport of delta images from the server.

With the client using the GPU resources at its disposal to decode and display updates passed form the server the client s system CPU resources are freed for other tasks. This technique is independent of the graphical API used i.e. OpenGL DirectX etc. 

It can be used for either full or partial screen remote rendering i.e. only remote 3D content or remote 3D and 2D content.

The invention can take the form of an entirely hardware embodiment an entirely software embodiment or an embodiment containing both hardware and software elements. In a preferred embodiment the invention is implemented in software which includes but is not limited to firmware resident software microcode etc.

The invention can take the form of a computer program product accessible from a computer usable or computer readable medium providing program code for use by or in connection with a computer or any instruction execution system. For the purposes of this description a computer usable or computer readable medium can be any apparatus that can contain store communicate propagate or transport the program for use by or in connection with the instruction execution system apparatus or device.

The medium can be an electronic magnetic optical electromagnetic infrared or semiconductor system or apparatus or device or a propagation medium. Examples of a computer readable medium include a semiconductor or solid state memory magnetic tape a removable computer diskette a random access memory RAM a read only memory ROM a rigid magnetic disk and an optical disk. Current examples of optical disks include compact disk read only memory CD ROM compact disk read write CD R W and DVD.

Improvements and modifications can be made to the foregoing without departing from the scope of the present invention.

