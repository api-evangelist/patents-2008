---

title: Method for centroiding and tracking a distorted optical image
abstract: A centroiding method is provided for an optical tracking system including a laser used for countermeasuring purposes in which a pencil thin laser beam is accurately positioned onto a target through the use of centroiding techniques for ascertaining the position not only of the target but also the laser beam, with the centroiding techniques resulting in a sub-pixel level resolution. The sub-pixel resolution permits utilization of smaller cost-effective focal plane arrays by giving the small focal plane array a resolution associated with much larger focal plane arrays.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08068214&OS=08068214&RS=08068214
owner: BAE Systems Information and Electronic Systems Integration Inc.
number: 08068214
owner_city: Nashua
owner_country: US
publication_date: 20080811
---
This application claims rights under 35 USC 119 e from U.S. Provisional Application Ser. No. 61 010 495 filed Jan. 7 2008 the contents of which are incorporated herein by reference.

This invention was made with United States Government support under Contract No. HSSCHQ 04 C 00342 awarded by the Department of Homeland Security. The United States Government has certain rights in this invention.

This invention relates to providing countermeasure energy in a very tight pencil beam onto an incoming missile target and more particularly to a method for precisely pointing the very tight pencil beam onto the target.

COUNTERMANPAD Applications abound in which countermeasures are used to deflect or defeat an incoming shoulder fired missile. In order to divert or defeat the incoming missile infrared laser radiation is projected towards the target with a so called jam code which confuses the seeker in the missile and causes the missile to be diverted away from its intended target.

Countermeasuring incoming missiles can be accomplished utilizing flares and if the incoming missile is a heat seeking missile then the heat seeking missile will follow all the flares as opposed to the original target.

However if the target is large meaning it has large bright engines which produce a significant IR signature then the incoming missile will home in on the rather large thermal signature from the aircraft such as a 747. If an IR countermeasure laser is used to countermeasure the missile and if its beam is too wide there will not be enough energy on the missile s seeker and the missile will still home in on the bright engine. Thus there is a requirement for a pencil thin laser beam to concentrate sufficiently high energy onto the missile s seeker.

If one had an infinitely high power laser one could tolerate a wide beam. However this is not practical and in order to minimize laser power as well as size it is more appropriate to generate a pencil thin laser beam which concentrates its energy in a very small but intense spot. The intensity of this laser beam is such that it completely drowns out the thermal signature of a large target.

However when generating a pencil thin laser beam pointing accuracy is of utmost importance. For instance for such a pencil thin laser beam there is a requirement that the pointing accuracy be less than a detector s Instantaneous Field of View IFOV which at 8 miles is of less than 4 feet.

Ascertaining where the target is to this pointing accuracy is extremely difficult because the IR image of the target is blurred out on the focal plane array normally used and overlaps numbers of pixels. Normally the resolution is limited to the IFOV of a pixel. For a Focal Plane Array FPA the angular error is associated with the size of a pixel whereas the requirement is on the order of of a pixel s IFOV.

While auto boresighting techniques are utilized to establish the exact position of the laser beam in space the center of energy of the blur is difficult to ascertain especially when utilizing a focal point of array having a resolution limited by the pixel IFOV.

It is therefore important to be able to ascertain laser pointing direction and the IR image center to an accuracy better than that associated with the IFOV of a pixel.

As will be appreciated with a very tight pencil thin laser beam used for concentrating energy in a very small cross section it is exceedingly important to be able to take the blurred out IR missile plume image which can overlap a number of pixels on the focal plane array and determine the exact point at which the laser beam is to be aimed to accuracies greater than the pixel level resolution of the array.

More particularly detector arrays used in countermeasure systems employ a focal plane array onto which energy is imaged. The resolution of the focal plane array is determined by the size of the array and the pixel size. For very large arrays such as 1028 1028 arrays pixel size is very small and resolution is only limited by this small pixel size. In some cases pixel size can be under 10 microns and with improved optics the images can be focused down to such a small spot.

However these large arrays are costly and exceed weight constraints. More importantly the read out of so many pixels simultaneously or in rapid succession is difficult and requires a considerable amount of processing. There is therefore a need to provide the same resolution as a large array in a small affordable 128 128 array. To do this one needs sub pixel resolution.

All things being equal the size of the pixels determine the effective pixel IFOV and up until the present time the resolution that determines the location of the target has been limited by the inability of small arrays to resolve focal plane array images below pixel level.

To put it another way depending on how much jam energy one wants to put on the target the efficiency of the jamming is related to how large the aircraft is because the larger the aircraft the brighter the engine. The brighter the engine the more energy that must be focused onto the target to sufficiently increase the jam to signal ratio or J to S. Depending on the platform one uses one has to generate a considerable J to S for bright engines.

One can either spread energy out into the environment like a big flashlight beam but it is very weak compared to the bright engine. Thus in order to project sufficient energy onto the target one has to shrink the beam to pencil thinness thus to concentrate the energy into a small spot. This means that track accuracy is very tight or the spot will miss the target.

In order to reduce the tracking error and to overcome the resolution associated with a small focal plane array the subject invention calculates the center of energy or centroid of the IR image namely the rocket plume and utilizes this center of energy point as the aiming point for the system.

It has been found with the subject algorithm that one can locate the center of energy of the target image by interpolation to an accuracy better than 0.25 of a pixel. This means that one can narrow the effective IFOV of a pixel and thus determine target position more accurately and in fact accurately enough to put the pencil thin laser beam directly on the missile seeker head.

The ability to interpolate to better than a pixel level is dependent upon the signal to noise ratio of the system with the larger the signal to noise ratio the better the subject interpolation algorithm works.

In one embodiment the subject interpolation algorithm is utilized both to ascertain the centroid of the laser beam which is quite narrow to begin with and then applies the same algorithm to detect the centroid of the infrared target image.

Using the subject technique the point at which the laser is aimed in space can be ascertained to accuracies in excess of pixel level accuracy as can be the center of energy of the infrared target image.

Having successfully ascertained the laser pointing direction utilizing the subject technique and having then used the subject algorithm to ascertain the center of energy of the infrared target image one can drive the center of energy of the target image to coincide with the pointing direction of the laser. At this point the laser beam will be projected onto the target with an error corresponding to a 0.25 pixel effective IFOV.

The algorithm describing the detection of the centroid of the laser beam or IR target image will be described hereinafter.

Essential for the subject algorithm is the overlapping of the image with a number of pixels and this is normally the case. If the image is too tightly focused it will not overlap adjoining pixels. If such is the case the system is set up with the focal plane array slightly offset from the focal plane to provide the necessary defocus.

To provide sub pixel level resolution in a small array in essence the subject algorithm considers only a portion of the focal point array for instance a 3 3 array. The algorithm then obtains the values of the overlapping image along three vertical lines corresponding in position to the center of the respective pixels. Those values are summed and divided by the sum of the values to provide an average value in the X direction. Likewise in the Y direction for horizontal rows running through the centers of the three pixels one can determine by the subject averaging technique the average position of the image in the Y direction.

This being the case it is possible to obtain the position of the centroid of the image to an accuracy less than a 0.25 pixel width thus to give a laser pointing error of less than 0.25 pixel effective IFOV. This permits accurate determination of both the position of the laser beam and the position of the target to such accuracy that a thin laser beam can be projected directly onto the target.

Referring now to an incoming missile having a seeker head is shown traveling towards its intended target. In order to countermeasure the missile a pencil thin laser beam is directed towards the missile head. This beam carries a jam code that includes a jamming sequence. The position in space of the pencil thin beam needs to be directly on seeker head to an accuracy of less than a pixel IFOV. Should the angular error exceed more than a pixel IFOV it is possible that the pencil thin beam may miss its target completely.

More particularly the effective instantaneous field of view IFOV of a singe pixel is shown at and subtends an angle greater than one which would intercept the missile. However by techniques described herein despite pixel overlap of the IR target image the effective resolution of a single pixel can be increased fourfold. This means that the effective IFOV can be cut by to subtend a 0.25 effective IFOV angle as shown at . The result with this accuracy is that a pencil thin laser beam spot will hit jam head .

Referring now to a typical countermeasure system includes a laser modulated with a jam code projected towards a laser beam combiner which redirects the beam from laser to out along axis towards an incoming missile .

The position of optical axis and therefore the direction of the outgoing beam is determined by directing a portion of the laser output towards a focal plane array from which the position in space of the outgoing beam is ascertained using auto boresighting techniques.

Thereafter an IR image of the hot rocket exhaust of missile is imaged onto the focal plane array so that the position of the incoming missile may be ascertained.

The laser pointing head is gimballed such that the laser beam from laser is centered on the infrared target image. This is accomplished by imaging the laser beam on the focal plane array and moving the infrared target image detected by the focal plane array to the sensed position of the laser beam.

However as mentioned above for small arrays the infrared image of the plume from the target extends over multiple pixels on the focal plane array. Its center of energy which determines the point in space where the missile is located must be ascertained typically to a resolution better than the single pixel resolution of the array. In one embodiment the subject system improves this single pixel resolution fourfold.

Referring to a portion of the focal plane array here a 3 3 portion is indicated at . Auto boresighting techniques and corrections to be discussed herein provide the precise and corrected position of the laser beam. Also indicated is the detected IR image which as can be seen straddles four pixels namely pixels and of array .

It is the purpose of the interpolation algorithm to find the center of energy of blur here illustrated at . As illustrated by arrow this permits moving the detected center of energy to coincide with the auto boresight position. This is done by gimbaling the laser to move the direction of the projected laser beam to end up on the target whose position is ascertained by the detected center of energy of the blur. Put another way the detected center of energy of the blur is moved to be coincident with the auto boresight corrected position .

As can be seen at in one embodiment the target blur is smeared out in a Gaussian fashion such that it overlaps more than one pixel. The resolution of the array is determined by the pixel size of pixel in one embodiment 30 microns on a side.

It is the purpose of the subject invention to provide aiming accuracy better than a single pixel IFOV at least for a 128 128 array having 30 micron pixels.

For the X direction one measures detected radiation along three columns x xx which are centered on the respective pixels through which the columns pass.

The radiation incident on vertically spaced pixels along columns x x and xis summed with the sum of the sums being divided by the sum of all of the detected radiation on the pixels of the array. The same is true for the Y direction.

This scenario has been described by the aforementioned centroiding equations. These equations locate the center of energy of the detected blurred image so that even though the blur overlaps numbers of pixels its center can be ascertained to less than a pixel width in accuracy.

Referring to the same technique is utilized to determine the center of energy of the outgoing laser beam which is shown at to overlap at least three pixels.

While the image of the laser beam on the focal plane array is quite a bit smaller than the blurred image of the target it is important in the subject invention to be able to ascertain with sub pixel level accuracy its position.

Thus when the detected center of energy of the target blur is made coincident with the center of energy of the target laser beam less than pixel level accuracy is achieved.

Referring now to in one operative embodiment a focal plane array with a 1 1 detection kernel with guardband is positioned behind optical assembly which focuses infrared radiation from a missile onto the focal plane array. Here sensor processor assembly processes the output of the focal plane array.

Laser is coupled to an optical parametric oscillator OPO via a fiber optic interface with the output of the OPO being re directed by a prism in a module through a laser beam combiner and onto a re directing prism which re directs the laser beam back to the laser beam combiner and then to the focal plane array. The position of the laser beam image on the focal plane array specifies the aiming direction of the laser and this position is refined by the subject interpolation algorithm.

The position of laser beam in space is thus first determined by picking off a portion of the laser beam from the optical parametric oscillator and determining its position again through the utilization of the subject interpolation algorithm.

Likewise the infrared return from missile passes through the laser beam combiner and onto the focal plane array as the aforementioned blur.

As will be discussed hereinafter the utilization of the laser beam combiner degrades the signal to noise ratio of the system due to aperture blockage. To the extent that this blockage is minimized the signal to noise ratio is increased. The above reduction of the effective single pixel IFOV in one embodiment requires a signal to noise ratio greater than 20.

Referring now to what is seen are graphs of the IR tracking error and laser boresight error graphed against signal to noise ratio.

To the right of is a three dimensional representation of the target blur intensity indicating a fairly pronounced center region and side lobes.

It can be seen from the graph of that a signal to noise ratio of 20 provides a tracker error of less than one pixel width and in this case 0.25 of the pixel leading to an effective 0.25 IFOV for the pixel.

Note that if the signal to noise ratio less than about 8 there is no advantage with the subject interpolating algorithm.

Likewise referring to although the laser beam has a considerably better defined cross section and shape with a signal to noise ratio of about 100 the tracker laser boresight error is again less than one pixel width and in this case is also 0.25 of the pixel.

 Removing the background from the target intensity total intensity total intensity average background 

It can therefore be seen that the laser aiming accuracy is critically dependent upon reducing the effective pixel IFOV which improves the resolution of the focal plane array thus to more accurately direct the pencil thin laser beam onto the target.

