---

title: Camera system to facilitate a cascade of imaging effects
abstract: This invention provides for a camera system having a plurality of hand held camera devices connected together in series. Each camera device includes an image input configured to receive image data from a camera device preceding in the series of devices, and an instruction reader configured to read instructions from a card inserted into the camera device, said card having encoded thereon various instructions for the manipulation of the image data. Each camera device also includes a processor unit arranged in communication with the input and the instruction reader, the processor unit configured to perform image manipulation on the image data according to the instructions read from the card. Also included is an image output configured to transmit manipulated image data from the processor to a camera device following in the series of devices, the camera system operatively facilitating a cascade of imaging effects.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08896724&OS=08896724&RS=08896724
owner: Google Inc.
number: 08896724
owner_city: Mountain View
owner_country: US
publication_date: 20080504
---
This application is a continuation application of U.S. patent application Ser. No. 10 666 124 filed Sep. 22 2003 now U.S. Pat. No. 7 375 746 which itself is a continuation application of U.S. patent Ser. No. 09 112 757 filed Jul. 10 1998 now issued U.S. Pat. No. 6 624 848 all of which are herein incorporated by reference. With respect to the present application any disclaimer of claim scope made in the parent application or any predecessor or related application is hereby rescinded. Further any disclaimer of claim scope that may occur in the present application should not be read back into any predecessor or related application.

The following Australian provisional patent applications are hereby incorporated by cross reference. For the purposes of location and identification US patent applications identified by their US patent application serial numbers USSN are listed alongside the Australian applications from which the US patent applications claim the right of priority.

The present invention relates to a data processing method and apparatus and in particular discloses a Multi Artcam System.

The present invention further relates to the field of image processing and to user interface mechanisms for performing image processing.

Recently in Australia Provisional Patent Specification entitled Image Processing Method and Apparatus Art01 filed concurrently by the present applicant a system has been proposed known colloquially as Artcam which is a digital camera having an integral printer for printing out sensed images in addition to manipulations of the sensed image which are manipulated as a result of the insertion of a Artcard having manipulation instructions thereon into the camera.

It is an object of the present invention to provide for a multi effect system to provide enhanced image effects.

In accordance with the first aspect of the present invention as provided a method of creating a manipulated image comprising interconnecting a series of camera manipulation units each of said camera manipulation unit applying an image manipulation to an inputted image so as to produce a manipulated output image an initial one of said camera manipulation units sensing an image from an environment and at least a final one of said camera manipulation units producing a permanent output image.

The preferred embodiment is preferable implemented through suitable programming of a hand held camera device such as that described in Australian Provisional Patent Application entitled Image Processing Method and Apparatus ART01 filed concurrently herewith by the present applicant the content of which is hereby specifically incorporated by cross reference.

The aforementioned patent specification discloses a camera system hereinafter known as an Artcam type camera wherein sensed images can be directly printed out by an Artcam portable camera unit. Further the aforementioned specification discloses means and methods for performing various manipulations on images captured by the camera sensing device leading to the production of various effects in any output image. The manipulations are disclosed to be highly flexible in nature and can be implemented through the insertion into the Artcam of cards having encoded thereon various instructions for the manipulation of images the cards hereinafter being known as Artcards. The Artcam further has significant onboard processing power by an Artcam Central Processor unit ACP which is interconnected to a memory device for the storage of important data and images.

In the preferred embodiment multiple Artcams as described in the aforementioned patent specification are interconnected via their USB ports so as to provide a cascading of imaging effects. Through suitable programming of the internal computer portions of each Artcam a cascading of imaging effects can be achieved.

The preferred arrangement is as illustrated in wherein a series of Artcams e.g. are interconnected via their USB ports. Each Artcam is provided with a corresponding Artcard having a suitable image manipulation program stored thereon. Further the instructions for utilisation in a network environment can be provided on the Artcard . The image sensed by the Artcam is then manipulated by the manipulation program on Artcard with the result being forwarded to Artcam device which applies the image manipulation function provided on Artcard producing a corresponding output which is forwarded to the next Artcam in the series. The chained Artcam has been modified so as to have two USB ports for this purpose. The final Artcam applies its Artcard manipulation stored on Artcard for producing output which is a conglomeration of each of the previous image manipulations.

The arrangement on thereby provides the opportunity to apply multiple effects to a single sensed image. Of course a number of further refinements are possible. For example each Artcam could print out its own manipulated image in addition to forwarding the image to the next Artcam in the series. Additionally splitting of paths where one Artcam outputs to two different downstream Artcams which result in different final images being output could also be provided. Additionally loops etc. could be utilised.

It would be appreciated by a person skilled in the art that numerous variations and or modifications may be made to the present invention as shown in the specific embodiment without departing from the spirit or scope of the invention as broadly described. The present embodiment is therefore to be considered in all respects to be illustrative and not restrictive.

The embodiments of the invention use an ink jet printer type device. Of course many different devices could be used. However presently popular ink jet printing technologies are unlikely to be suitable.

The most significant problem with thermal ink jet is power consumption. This is approximately 100 times that required for high speed and stems from the energy inefficient means of drop ejection. This involves the rapid boiling of water to produce a vapor bubble which expels the ink. Water has a very high heat capacity and must be superheated in thermal ink jet applications. This leads to an efficiency of around 0.02 from electricity input to drop momentum and increased surface area out.

The most significant problem with piezoelectric ink jet is size and cost. Piezoelectric crystals have a very small deflection at reasonable drive voltages and therefore require a large area for each nozzle. Also each piezoelectric actuator must be connected to its drive circuit on a separate substrate. This is not a significant problem at the current limit of around 300 nozzles per print head but is a major impediment to the fabrication of pagewide print heads with 19 200 nozzles.

Ideally the ink jet technologies used meet the stringent requirements of in camera digital color printing and other high quality high speed low cost printing applications. To meet the requirements of digital photography new ink jet technologies have been created. The target features include 

All of these features can be met or exceeded by the ink jet systems described below with differing levels of difficulty. 45 different ink jet technologies have been developed by the Assignee to give a wide range of choices for high volume manufacture. These technologies form part of separate applications assigned to the present Assignee as set out in the table below.

The ink jet designs shown here are suitable for a wide range of digital printing systems from battery powered one time use digital cameras through to desktop and network printers and through to commercial printing systems

For ease of manufacture using standard process equipment the print head is designed to be a monolithic 0.5 micron CMOS chip with MEMS post processing. For color photographic applications the print head is 100 mm long with a width which depends upon the ink jet type. The smallest print head designed is IJ38 which is 0.35 mm wide giving a chip area of 35 square mm. The print heads each contain 19 200 nozzles plus data and control circuitry.

Ink is supplied to the back of the print head by injection molded plastic ink channels. The molding requires 50 micron features which can be created using a lithographically micromachined insert in a standard injection molding tool. Ink flows through holes etched through the wafer to the nozzle chambers fabricated on the front surface of the wafer. The print head is connected to the camera circuitry by tape automated bonding.

Eleven important characteristics of the fundamental operation of individual ink jet nozzles have been identified. These characteristics are largely orthogonal and so can be elucidated as an eleven dimensional matrix. Most of the eleven axes of this matrix include entries developed by the present assignee.

The complete eleven dimensional table represented by these axes contains 36.9 billion possible configurations of ink jet nozzle. While not all of the possible combinations result in a viable ink jet technology many million configurations are viable. It is clearly impractical to elucidate all of the possible configurations. Instead certain ink jet types have been investigated in detail. These are designated IJ01 to IJ45 above.

Other ink jet configurations can readily be derived from these 45 examples by substituting alternative configurations along one or more of the 11 axes. Most of the IJ01 to IJ45 examples can be made into ink jet print heads with characteristics superior to any currently available ink jet technology.

Where there are prior art examples known to the inventor one or more of these examples are listed in the examples column of the tables below. The IJ01 to IJ45 series are also listed in the examples column. In some cases a printer may be listed more than once in a table where it shares characteristics with more than one entry.

Suitable applications for the ink jet technologies include Home printers Office network printers Short run digital printers Commercial print systems Fabric printers Pocket printers Internet WWW printers Video printers Medical imaging Wide format printers Notebook PC printers Fax machines Industrial printing systems Photocopiers Photographic minilabs etc.

The information associated with the aforementioned 11 dimensional matrix are set out in the following tables.

