---

title: Image sensing apparatus and method which combine a plurality of images obtained from different areas at different time intervals
abstract: An image sensing apparatus has first and second image sensors is provided. In the image sensing apparatus, an optical system forms an optical image on the first and second image sensors; an area-of-interest extracting unit extracts an area of interest from image data output by the second image sensor; an area-of-interest information storage unit stores area-of-interest information indicative of a pixel area in the first image sensor corresponding to the position of the area of interest; a first storage unit stores image data from an entire pixel area of the first image sensor at a time interval; a second storage unit stores image data from the pixel area of the first image sensor indicated by the area-of-interest information, at a shorter time interval; and a combining unit combines the image data stored in the first and second storage units to generate combined image data.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07920170&OS=07920170&RS=07920170
owner: Canon Kabushiki Kaisha
number: 07920170
owner_city: Tokyo
owner_country: JP
publication_date: 20080312
---
The present invention relates to an image sensing apparatus having two image sensors and to an image sensing method.

CCD image sensors and CMOS image sensors are widely known and used as solid state image sensors comprising a semiconductor. A CCD image sensor functions to convert light to signal charge using photoelectric converters placed within pixels read the signal charge out of all pixels simultaneously and transfer the charge then convert the transferred signal charge to an electric signal and output the signal as a video signal.

A CMOS image sensor on the other hand functions to convert light to signal charge using photoelectric converters placed within pixels amplify the signal charge pixel by pixel and output the result as a video signal.

Recent consumer oriented CMOS image sensors have a much higher read out speed in comparison with CCD image sensors of the same kind. For example with a prototype image sensing apparatus having a CMOS image sensor one frame consisting of 6 400 000 pixels can be output 60 times in one second or one frame consisting of 2 760 000 pixels can be output 180 times in one second. This is disclosed by e.g. Satoshi Yoshihara A 1 1.8 6.4M Pixel 60 Frames s CMOS Image Sensor with Seamless Mode Change IEEE International Solid State Circuits Conference February 2006 . In accordance with a CMOS image sensor having this function image sensing with a very large number of pixels at a high frame rate is possible. Accordingly one frame of an image constituting a moving picture can be provided with the resolution necessary for a still image and it is possible for the moving picture and still image to be read out seamlessly with no change in the state of resolution.

Again unlike a CCD image sensor in which image signals from all pixels are read out simultaneously the CMOS image sensor has a random access function i.e. a partial read out function in which only some of the pixels in the image sensor are read out partially. For example in the field of robot vision and vision chips research is being conducted concerning high speed vision systems in which the random access function namely the partial read out function is exploited by taking advantage of the high speed read out function and random access function of the CMOS image sensor. This is disclosed in the specification of Japanese Patent Laid Open No. 2003 319262 and in Ulrich Muehlmann et al. A New High Speed CMOS Camera for Real Time Tracking Applications IEEE International Conference on Robotic amp Automation April 2004 .

In robot vision a high spatial resolution and an excellent real time property are both required in many instances. In this case on the premise that all pixel information generally will not be necessary for computing an image feature quantity only the image signal of an area of interest being observed in a frame image is read out and an area of interest that will be observed in the next frame is updated based upon the information that has been read out. This technique is called an intelligent pixel selection function . Further in the field of consumer cameras as well it has been proposed to exploit the random access function and make the resolution of the image data in an area of interest differ from the resolution of the image data in a peripheral area which is an area other than the area of interest in a frame image. That is the specification of Japanese Patent Laid Open No. 2006 60496 discloses reducing the amount of processing and processing time of a moving picture per frame image by treating an area of interest as a high resolution area and the peripheral area as a low resolution area.

However in a case where a large quantity of moving images are dealt with in an image sensing apparatus having an image sensor capable of such high speed read out the higher the sophistication of a task the more difficult it is to achieve real time high speed processing consistent with the performance of the image sensor. Furthermore there is an increase in the cost of the image sensor. In order to process image data at high speed in real time reducing the amount of information in the image data is desirable. However this results in loss of spatial resolution and a decline in information in detailed portions of the image data.

The present invention has been made in consideration of the above situation and its object is to provide an image sensing apparatus having two image sensors and both a high spatial resolution and excellent real time property.

According to the present invention the foregoing object is attained by providing an image sensing apparatus having first and second image sensors comprising 

an area of interest extracting unit configured to extract an area of interest from image data that is output by the second image sensor 

an area of interest information storage unit configured to store area of interest information indicative of a pixel area in the first image sensor corresponding to the position of the area of interest extracted by the area of interest extracting unit 

a first storage unit configured to store image data that is read out from an entire pixel area of the first image sensor at a first time interval 

a second storage unit configured to store image data obtained by reading out only the pixel area of the first image sensor indicated by the area of interest information stored in the area of interest information storage unit at a second time interval shorter than the first time interval and

a combining unit configured to combine the image data that has been stored in the first storage unit and the image data that has been stored in the second storage unit to thereby generate combined image data.

According to the present invention the foregoing object is attained by providing an image sensing method of an image sensing apparatus having first and second image sensors and an optical system for forming an optical image on the first and second image sensors the method comprising 

an area of interest extracting step of extracting an area of interest from image data that is output by the second image sensor 

an area of interest information storage step of storing area of interest information indicative of a pixel area in the first image sensor corresponding to the position of the area of interest extracted in the area of interest extracting step 

a first storage step of storing image data which is read out from an entire pixel area of the first image sensor at a first time interval in a first storage unit 

a second storage step of storing image data in a second storage unit the image data being obtained by reading out only the pixel area of the first image sensor indicated by the area of interest information stored in the area of interest information storage step at a second time interval shorter than the first time interval and

a combining step of combining the image data that has been stored in the first storage unit and the image data that has been stored in the second storage unit to thereby generate combined image data.

Further features of the present invention will become apparent from the following description of exemplary embodiments with reference to the attached drawings .

Preferred embodiments of the present invention will be described in detail in accordance with the accompanying drawings.

As illustrated an optical system is provided between a subject and an image sensor and includes a lens group for forming the optical image a moving image of the subject on the image sensor . It should be noted that the lens group is illustrated in the form of a single lens for the sake of simplicity. Further it is required that the optical system form the optical image moving image of the subject on an image sensor described later as well. A beam splitter for example is included for this reason. Basically however as long as the same optical image moving image can be formed on the image sensor and image sensor it is also possible to provide a lens group that is separate from the lens group of image sensor .

The image sensor is a two dimensional image sensor capable of high speed read out and random access i.e. partial read out. An example of such image sensor is a CMOS image sensor. The image sensor is provided within a package not shown. The image sensor which is a semiconductor device having a photoelectric conversion function converts electric charge conforming to a scene i.e. optical image of a moving image which has been formed by the optical system to an electric signal an analog signal and outputs the signal.

A CDS AGC A D converting circuit is connected to the image sensor and receives the electric signal analog signal from the image sensor . The CDS AGC A D converting circuit applies CDS processing to the analog electric signal amplifies the signal which has undergone CDS processing by an AGC operation and finally converts the analog electric signal to image data a digital signal .

An image data processor is connected to the CDS AGC A D converting circuit a microcomputer a recording circuit and a display unit . As a result the image data processor receives the image data from the CDS AGC A D converting circuit processes the image data based upon a control signal from the microcomputer and supplies the processed image data to the display unit to display the image. When necessary the image data is recorded on a removable recording medium by the recording circuit although this is not illustrated.

The image data processor comprises an image data storage circuit an image data combining circuit an area of interest image data storage circuit a switch and an image data processing circuit .

The image data storage circuit stores one frame of image data which has been obtained from the CDS AGC A D converting circuit when the entire pixel area is read out of the image sensor by control exercised by a driving circuit for driving this image sensor. The stored frame of image data is updated when the next frame of image data is input.

The stored frame image becomes background image data for generating one frame image together with image data of the area of interest partially read out randomly accessed from the image sensor .

In a case where the combining of image data is unnecessary i.e. in case of the ordinary read out mode the one frame of image data that has been stored in the image data storage circuit is input as is to the image data processing circuit . However if combining of image data is necessary the one frame of image data that has been stored in the image data storage circuit is input to the image data combining circuit . Accordingly the function of the image data combining circuit is not used see step S below in the case of the operation for reading out the entire pixel area which is the operation in the ordinary read out mode in the image sensor .

The image data combining circuit adopts the one frame of image data which has been stored in the image data storage circuit as image data of the background. The image data combining circuit then aligns the position of the area of interest image data which has been stored in the area of interest image data storage circuit in the one frame of image data that has been stored in the image data storage circuit then synthesizes these two kinds of image data thereby generating one frame of a synthesized image. This is executed by changing over the switch under the control of the microcomputer .

More specifically for the area of interest image data that has been stored in the area of interest image data storage circuit area of interest information which is information on position in the frame i.e. background image has been stored in an area of interest information storage circuit . Accordingly alignment of the aforesaid two kinds of image data is performed by controlling the switch on the basis of this area of interest information thereby one frame of synthesized image data is generated. The generated image data is input to the image data processing circuit .

The area of interest image data storage circuit stores area of interest image data that has been partially read out of randomly accessed from the image sensor . The area of interest image data that will be input to the area of interest image data storage circuit is only area of interest image data in which a specific subject has been extracted and hence one frame of image data cannot be generated only from the area of interest image data. Therefore the area of interest image data is input to the image data combining circuit and synthesized with the one frame of image data stored in the image data storage circuit thereby generating one completed frame of image data.

The image data processing circuit subjects the image data to image processing such as an aperture correction WB correction and correction and outputs the processed image data to the recording circuit or display unit . The recording circuit records the image data output from the image data processing circuit on a removable medium such as a semiconductor memory and the display unit displays the image data that has been output from the image data processing circuit .

The driving circuit is connected to the microcomputer in order to drive the image sensor . Hence the driving circuit drives the image sensor based upon a control signal received from the microcomputer . Specifically the driving circuit generates driving pulses which are for driving the image sensor and supplies the pulses to the image sensor .

A vertical shift register outputs control pulses for reading an electric signal out of pixels for every horizontal output line VSEL to VSELm. The electric signals of each of the pixels selected by the horizontal output lines VSEL to VSELm are read out by vertical output lines VSIG to VSIGn and the electric signals are accumulated in an adding circuit . The electric signals that have accumulated in the adding circuit are read out successively and scanned by a horizontal shift register and the signals are output in a time series.

The image sensor is driven by a driving circuit controlled by the microcomputer and outputs a sensed image signal to a CDS AGC A D converting circuit . Image data from the CDS AGC A D converting circuit is applied to an area of interest extracting circuit . Under the control of the microcomputer the area of interest extracting circuit extracts area of interest information relating to a specific image area of interest from the image data acquired from the CDS AGC A D converting circuit . The area of interest information which is information concerning the position at which extraction was made updates the area of interest information storage circuit successively via the microcomputer .

In order to specify an area of interest initially use may be made of the output of the image sensor . For example the portion of the output of the image sensor that exhibits motion is detected this is adopted as a subject of interest and the area of the image that encompasses this subject is adopted as the area of interest. Alternatively it is possible to investigate the image data that is the output of the image sensor by an area of interest recognition circuit and to specify the area of the image data of the subject that has e.g. specific feature information as the area of interest. In either case area of interest information specifying the position of the area of interest is expressed by an area of pixels obtained by dividing the entire pixel area of the image described later.

The position of an area of interest is thus specified. Next reference will be had to to describe a MOS image sensor usable as the image sensor .

Specifically in the vertical shift register outputs control pulses to horizontal output lines connected to pixels belonging to the area of interest which is the target of partial read out random access among the horizontal output lines VSEL to VSELm. The horizontal shift register outputs control pulses to vertical output lines connected to pixels belonging to the area of interest which is the target of partial read out among the vertical output lines VSIG to VSIGn.

The electric signals of each of the pixels belonging to the area of interest selected by the control pulses of the horizontal output lines are read out to the adding circuit by the control pulses of the vertical output lines the electric signals are accumulated in the adding circuit and they are read out successively by the horizontal shift register.

The microcomputer executes overall processing of the overall image sensing apparatus. The microcomputer switches between the ordinary read out mode and high speed read out mode by a mode switch for switching between the ordinary and high speed read out modes. If the mode switch has been changed over to the high speed read out mode then by way of example area of interest information is generated from information extracted by the area of interest extracting circuit of image sensor the generated information is stored in the area of interest information storage circuit and the area of interest information is updated successively.

When read out of the entire pixel area is performed in the image sensor in the high speed read out mode the output destination of the CDS AGC A D converting circuit is changed over to the image data storage circuit by the switch . At the timing at which partial read out random access is performed the output destination of the CDS AGC A D converting circuit is changed over to the area of interest image data storage circuit by the switch . In the ordinary read out mode read out of the entire pixel area is performed at all times and therefore the output destination of the CDS AGC A D converting circuit is kept as the image data storage circuit .

When partial read out random access of the area of interest is performed in the image sensor the area of interest information storage circuit receives the area of interest information of the subject from the microcomputer and inputs this information to the driving circuit that drives the image sensor .

The mode switch for changing over mode between the ordinary and high speed read out modes performs the changeover between the ordinary and high speed read out modes by controlling the driving circuit through the microcomputer . The mode switch which is constituted by a command dial or button is operated by the user.

The image sensor which is separate from the image sensor is provided in close proximity to the optical system outside the package of the image sensor not shown . After the output of the image sensor is converted to image data by the CDS AGC A D converting circuit the image data is input to the area of interest extracting circuit . The information of the image area extracted by the area of interest extracting circuit is input to the microcomputer .

It should be noted that in the following embodiments an image sensing apparatus adopting a photometry method using an external photometer is described however the present invention is not limited to this. An image sensing apparatus adopting a photometry method in which a light beam of an image entered through a single optical system is split into two beams and photometry is performed using one of the split light beams may be utilized.

The image sensor monitors the overall image data at all times. For example the image sensor may constantly monitor the entirety of the image data at regular intervals such as one time per several frames or may be operated only when there is motion of some kind in the image data.

It should be noted that if the image sensor is one that is specialized for detection of motion then any image sensor is usable. For example it is permissible to use an image sensor of the kind that senses infrared radiation or an image sensor that operates on the basis of temperature. Accordingly the number of sensors need not be large. The image sensor for infrared is preferred in view of the fact that it is not much affected by the brightness of the optical image formed and because robust detection is possible. An example in which an image sensor for infrared is used for the image sensor will be described in embodiments.

Next reference will be had to to describe a method of controlling an image sensor in an image sensing apparatus according to a first embodiment of the present invention. is a flowchart illustrating the flow of processing for controlling read out of an image sensor in the image sensing apparatus according to the first embodiment is a conceptual view illustrating delay time in read out of the image sensor and is a conceptual view illustrating timing at which subject detection information is reflected in read out of the image sensor .

For example the area of one frame of the image data is divided into 16 areas in a 4 4 array. Each resulting area is formed from a plurality of pixels. Read out of the image sensor is performed based upon the area of interest of this subject. In the image sensor the entire pixel area of the frame image all of the divided 16 areas are hatched by a stripe pattern is read out in the case of entire pixel area read out and the area of interest part of the divided 16 areas are hatched by a stripe pattern which is the area of the subject to be read out is read out in the case of partial read out random access . The image sensor is not driven for the area which are not hatched by a stripe pattern in .

Finally the combined frame image displayed on the display unit is shown in a time series at the bottom of . The image data is one frame of image data that has been output from the image data storage circuit in case of read out of the entire pixel area in image sensor . On the other hand in case of partial read out random access of the area of interest the image data is one frame of image data which is the result combining of images output from the image data combining circuit in which the background image data is combined with the other image data at a prescribed position thereof.

In assume that the image sensor operates at 60 frames sec in the ordinary read out mode and at 600 frames sec in the high speed read out mode. Further the image sensor for monitoring image data always operates in the ordinary read out mode 60 frames sec in this case .

In the interval of t t t t . . . along the time series t represents 60 frames sec and the interval of tli t 0

According to this embodiment read out of all pixels is performed unconditionally with the exception of the initial frame t by the image sensor in order to update the background image data at the interval 60 frames sec of the ordinary read out mode. At times other than when read out is performed in the ordinary read out mode the data in the image area of the subject is read out in the high speed read out mode 600 frames sec . It should be noted that at t a delay occurs because the image area of the subject extracted from the image sensor is reflected in the image sensor in real time. Therefore the image sensor is not operated and hence a displayed frame of image data does not exist.

Accordingly in this embodiment when area of interest information which is information of detection of the subject is updated as illustrated in a delay of one frame occurs at the interval of 60 frames sec in the ordinary read out mode.

Next the operation of the image sensing apparatus will be described in accordance with the flowchart of showing the flow of processing for controlling read out of the image sensor . At step S the image sensing apparatus accepts information specifying introduction of power. The image sensing apparatus performs a prescribed operation such as initialization in response to the information specifying introduction of power. That is the optical system forms the optical image of the subject on the image sensor .

The image sensor generates electric charge which conforms to the optical image formed and output as an electric signal analog signal . The CDS AGC A D converting circuit applies CDS processing to the analog electric signal amplifies the signal which has undergone CDS processing by an AGC operation and converts the analog electric signal to digital data a digital signal . The image data processor receives the image data and processes the image data based upon a control signal received from the microcomputer .

The image sensing apparatus starts ordinary read out at step S. That is the microcomputer controls the driving circuit and performs ordinary read out of the image sensor . The analog electric signal that has been output from the image sensor is subjected to prescribed processing by the CDS AGC A D converting circuit and is input to the image data processor as image data.

The microcomputer changes over the output destination of the image data of the CDS AGC A D converting circuit to the image data storage circuit by changing over the switch . The image data frame image data that has been output is subjected to prescribed image processing by the image data processing circuit via the image data storage circuit after which the processed image data is displayed on the display unit . The processed image data is further stored on a removable recording medium by the recording circuit .

Basically the image data storage circuit stores one frame of image data which has been obtained from the CDS AGC A D converting circuit when the image sensor undergoes read out of the entire pixel area. At this step however the function of this circuit is not used.

At step S it is determined whether the high speed read out mode has been selected. That is the microcomputer determines whether a signal to start the high speed read out mode has been received from the mode switch that switches between the ordinary and high speed read out modes.

If the high speed read out mode has been selected then the microcomputer connects the area of interest information storage circuit and advances processing to step S. If the signal to start the high speed read out mode has not been received the processing is returned to ordinary read out at step S.

The image sensor infrared image sensor starts extraction of the area of interest of the subject see AREA OF INTEREST INFORMATION OBTAINED FROM IMAGE SENSOR at the top of at step S. That is the area of interest of the subject extracted from the output of the image sensor is mapped to the area of interest of a certain subject as information concerning the location at which the image sensor is driven. As a result the area of interest is associated with the pixel areas divided into 16 areas and is stored in the area of interest information storage circuit as area of interest information see AREA OF INTEREST WITHIN FRAME IMAGE at the middle of . In this embodiment the image sensor is operated in the ordinary read out mode 60 frames sec as mentioned earlier.

At step S the image sensor is driven based upon the area of interest information obtained at step S. That is in a case where all pixels are read out by the image sensor in order to generate image data to serve as background t t t . . . in the output destination of the CDS AGC A D converting circuit is changed over to the image data storage circuit .

At step S data is generated as frame image data which is capable of being displayed on the display unit based upon the image data that has been output at step S. That is assume that read out of all pixels has been performed at step S. In this case t t t . . . in the image data that has been output from the CDS AGC A D converting circuit is already one frame of image data and therefore the image data is input to the image data processing circuit as is without being processed.

Next assume that partial read out random access has been performed by the image sensor . In this case tli t 0

The image data combining circuit performs a combining operation by adopting the frame image data which has been stored in the image data storage circuit as a background image and fitting the area of interest image data which has been stored in the area of interest image data storage circuit in the background image at the appropriate location thereof thereby generating one frame of image data. The one frame of image data thus synthesized is input to the image data processing circuit .

At step S the frame data generated at step S is displayed on the display unit see ONE DISPLAYED FRAME OF IMAGE DATA at the bottom of . That is the one frame of synthesized image data that has been subjected to prescribed image processing by the image data processing circuit is output to the display unit .

At step S the microcomputer determines whether a signal ending the high speed read out mode has been received from the ordinary high speed read out changeover mode switch . In a case where a signal ending the high speed read out mode has been received control returns to step S and a transition is made to the ordinary read out mode.

In a case where a signal ending the high speed read out mode has not been received control returns to step S detection of the area of interest of a subject is performed and steps S to S are repeated until the end signal is received. Image data of the area of interest that is updated successively is small in size and the amount of information is suppressed. As a result the time needed for image processing is curtailed.

In accordance with the first embodiment of the present invention described above it is possible to provide an image sensing apparatus in which both high spatial resolution and an excellent real time property are achieved within the limits of processing performance of an image sensor that is capable of high speed read out based upon recognition of an area of interest by the image sensor.

Reference will now be had to to describe a method of controlling an image sensing apparatus according to a second embodiment of the present invention. is a flowchart illustrating the flow of processing for controlling read out of the image sensor in the image sensing apparatus is a conceptual view illustrating delay time in read out of the image sensor and is a conceptual view illustrating timing at which area of interest information of a subject is reflected in read out of the image sensor .

For the structural views of the image sensing apparatus according to the second embodiment of the invention reference may be had to and these need not be described again. Further components similar to those of the first embodiment need not be described again. The description that follows will focus on portions that differ from those of the first embodiment.

The second embodiment differs from the first embodiment in that pre shooting is performed in order to generate image data that will serve as background and the image data to serve as background is prepared in advance. As a result updating of area of interest information from the image sensor can be executed at the interval 600 frames sec of the high speed read out mode rather than at the interval 60 frames sec of the ordinary read out mode. This makes it possible to improve high speed tracking and to exploit the advantages of high speed read out.

The second embodiment will be described with reference to . The basic operation is similar to that of the first embodiment described in conjunction with . In the second embodiment the shooting operation is divided into pre shooting and actual shooting described later. In T of the T time series shown at the left corresponds to pre shooting . Further t t t t . . . of the t time series shown on the right correspond to actual shooting .

In a manner similar to the first embodiment the second embodiment also is such that read out of all pixels from the image sensor is performed unconditionally in order to update the image data that will serve as background at the interval 60 frames sec of the ordinary read out mode of image sensor . Further in the first embodiment when area of interest information of the subject which is extracted information representing the subject is updated a delay equivalent to one frame occurs and the interval becomes 60 frames sec of the ordinary read out mode.

In this embodiment however background image data is acquired in advance by pre shooting . As a result the amount of delay produced when the area of interest information of the subject is updated is small the time required is only the physical time between detection of motion of the subject and arrival of the area of interest information which is required to drive the image sensor at the driving circuit .

In other words if motion of the subject has been detected it is possible to update the area of interest information of the subject without waiting for next timing for unconditional entire pixel area read out performed after the detection. That is if motion of the subject is detected at any of times t tli t t. . . updating of the area of interest information of the subject is possible in time 0

Next operation of the image sensing apparatus will be described in accordance with the flowchart of illustrating processing for controlling read out of the image sensor in the image sensing apparatus. Since the details of processing are similar to the processing of the first embodiment only the difference will be described.

At step S the image sensing apparatus accepts information specifying introduction of power. The image sensing apparatus performs a prescribed operation such as initialization in response to the information specifying introduction of power.

The image sensing apparatus starts ordinary read out of the image sensor at step S. The pre shooting mentioned earlier is performed at this stage. That is when pre shooting is performed by the image sensor at step S the image data storage circuit stores the background image data T in necessary in the high speed read out mode.

At step S it is determined whether the high speed read out mode has been selected by the mode switch . If the high speed read out mode has been selected then the microcomputer connects the image data storage circuit and the area of interest information storage circuit and advances processing to step S. If the signal to start the high speed read out mode has not been received processing returns to step S.

At step S the image sensor infrared image sensor starts extraction of the area of interest of the subject see AREA OF INTEREST INFORMATION OBTAINED FROM IMAGE SENSOR at the top of . Here the image sensing apparatus starts actual shooting .

At step S the image sensor is driven based upon the area of interest information obtained at step S and stored in the area of interest information storage circuit .

At step S one frame of image data displayable by the display unit is generated by the combining operation in the image data combining circuit based upon the image data that has been read out at step S.

At step S the one frame of image data generated at step S is displayed on the display unit see ONE DISPLAYED FRAME OF IMAGE DATA at the bottom of .

At step S the microcomputer determines whether a signal ending the high speed read out mode has been received from the mode switch . In a case where a signal ending the high speed read out mode has been received control returns to step S and a transition is made to the ordinary read out mode. In a case where a signal ending the high speed read out mode has not been received control returns to step S extraction of the area of interest of a subject is performed and steps S to S are repeated until the end signal is received.

In accordance with the second embodiment updating of area of interest information from the image sensor is executed at the interval 600 frames sec of the high speed read out mode rather than at the interval 60 frames sec of the ordinary read out mode unlike the first embodiment. Further if the image sensor is caused to operate at an interval shorter than the read out interval of the ordinary read out mode then the amount of delay from extraction of the area of interest of the subject to read out of the image sensor is reduced further and it is possible to perform read out at a speed close to real time.

The present invention can be implemented by supplying a software program which implements the functions of the foregoing embodiments directly or indirectly to a system or apparatus reading the supplied program code with a computer of the system or apparatus and then executing the program code. In this case so long as the system or apparatus has the functions of the program the mode of implementation need not rely upon a program.

Accordingly since the functions of the present invention are implemented by computer the program code installed in the computer also implements the present invention. In other words the claims of the present invention also cover a computer program for the purpose of implementing the functions of the present invention.

In this case so long as the system or apparatus has the functions of the program the program may be executed in any form such as an object code a program executed by an interpreter or script data supplied to an operating system.

Examples of storage media that can be used for supplying the program are a floppy disk a hard disk an optical disk a magneto optical disk a CD ROM a CD R a CD RW a magnetic tape a non volatile type memory card a ROM and a DVD DVD ROM and a DVD R .

As for the method of supplying the program a client computer can be connected to a website on the Internet using a browser of the client computer and the computer program of the present invention or an automatically installable compressed file of the program can be downloaded to a recording medium such as a hard disk. Further the program of the present invention can be supplied by dividing the program code constituting the program into a plurality of files and downloading the files from different websites. In other words a WWW World Wide Web server that downloads to multiple users the program files that implement the functions of the present invention by computer is also covered by the claims of the present invention.

It is also possible to encrypt and store the program of the present invention on a storage medium such as a CD ROM distribute the storage medium to users allow users who meet certain requirements to download decryption key information from a website via the Internet and allow these users to decrypt the encrypted program by using the key information whereby the program is installed in the user computer.

Besides the cases where the aforementioned functions according to the embodiments are implemented by executing the read program by computer an operating system or the like running on the computer may perform all or a part of the actual processing so that the functions of the foregoing embodiments can be implemented by this processing.

Furthermore after the program read from the storage medium is written to a function expansion board inserted into the computer or to a memory provided in a function expansion unit connected to the computer a CPU or the like mounted on the function expansion board or function expansion unit performs all or a part of the actual processing so that the functions of the foregoing embodiments can be implemented by this processing.

While the present invention has been described with reference to exemplary embodiments it is to be understood that the invention is not limited to the disclosed exemplary embodiments. The scope of the following claims is to be accorded the broadest interpretation so as to encompass all such modifications and equivalent structures and functions.

This application claims the benefit of Japanese Patent Application No. 2007 067595 filed on Mar. 15 2007 which is hereby incorporated by reference herein in its entirety.

