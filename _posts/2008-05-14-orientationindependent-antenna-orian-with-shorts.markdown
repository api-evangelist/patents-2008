---

title: Orientation-independent antenna (ORIAN) with shorts
abstract: An orientation-independent antenna that presents a circular polarization characteristic to incoming waves such that these waves are detected regardless or polarization and angle of arrival is provided with shorts across elements thereof that provide for crossed vertical loops and a horizontal loop to lower the VSWR at the lower frequencies of the antenna. The antenna includes crossed vertical loops and a horizontal loop, with the loops being phased to provide the circular polarization characteristic. In one embodiment, the antenna includes a number of elements on the faces of a cube, or the elements are positioned on the surface of a sphere. In another embodiment, the antenna is given both a right hand circular polarization characteristic and a left hand circular polarization characteristic in two different channels to provide for double the data throughput.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07847747&OS=07847747&RS=07847747
owner: BAE Systems Information and Electronic Systems Intergration Inc.
number: 07847747
owner_city: Nashua
owner_country: US
publication_date: 20080514
---
This Application claims rights under 35 USC 119 e from U.S. application Ser. No. 60 937 026 filed Jun. 25 2007 the contents of which are incorporated herein by reference.

This related application claims the only feature of this invention which was made with United States Government support under Contract No. W56 HZV 05 C 0724 awarded by the U.S. Army which comprises the shorts shown in . The other features of the invention which are claimed in a co pending companion application were not made under a United States Government contract.

This invention relates to an orientation independent antenna which presents a circular polarization characteristic to incoming waves such that these waves are detected regardless of polarization and angle of arrival and more particularly to the use of shorts to decrease the VSWR of the antenna at the lower frequencies thereof thus to improve its bandwidth.

Especially with regard to the control of robotic vehicles such as are used in war theatres and the like it is important to be able to robustly communicate with the robotic vehicle from a base station. Presently satellite communication systems Satcom are used where power levels are low and often times are not useful in communicating with terrestrial vehicles especially those having antenna orientations that are not predictable.

For instance as a robotic vehicle moves about terrain or for instance within a building signals arrive at the antenna utilized by the robotic vehicle with a variety of different polarizations and directions.

If for instance the antenna utilized by the robotic vehicle is vertically polarized then it will be insensitive to incoming signals having a horizontal polarization and these signals especially if they are weak will not be detected. Likewise if one utilized a horizontally polarized antenna it would be insensitive to signals coming in with a vertical polarization. Of course signals that are elliptically polarized which have components in both the vertical and horizontal directions would be non optimally received with an antenna whose polarization did not match that of the incoming wave.

It would therefore be desirable to provide an antenna having a characteristic that is independent of the direction of arrival and polarization of an incoming wave. Such antennas are those exhibiting circular polarization as there will be no direction that results in polarization cancellations.

More particularly if one were utilizing a vertical dipole on a robotic vehicle one would have reasonable 360 degree coverage but only for vertically polarized signals. The vertical dipole would therefore be relatively insensitive to horizontally polarized signals. In short the dipole would not be sensitive to anything straight up.

To make matters somewhat more problematic many antennas that are mounted on robotic vehicles have masts that are purposely flexible so that if the antenna hits an object it will bend and not trap the antenna or stop the robot. The antenna with a flexible mast has its vertical or horizontal orientation direction altered by the flexibility of the mast which means that reliable communications cannot be established if the polarization direction of the antenna is not exactly aligned with that of the incoming signal.

In short with a robotic vehicle as it moves through the environment the antenna may tilt at various angles and therefore compromise communications with a base station. Further when robotic vehicles maneuver through a building signals can come in from various different directions due to multi path problems. Since buildings even further attenuate satellite signals optimum antenna orientation is a requirement if one is using anything other than a circularly polarized antenna.

Moreover on robotic vehicles there is a requirement for miniaturization. It is not possible in most instances to provide elongated whips or antennas that are large with respect to the vehicle because of the terrain through which they operate or because of the buildings in which they move. It is therefore important to be able to provide a miniature wide band antenna which has a circular polarization in all directions.

As described in a co pending application entitled Orientation Independent Antenna ORIAN by John T. Apostolos assigned to the assignee hereof incorporated herein by reference and filed on even date herewith while satisfactory performance over the majority of the bandwidth of this antenna has been achieved lowering the VSWR especially at the lower frequencies has been a problem. For instance while in one embodiment of the orientation independent circularly polarized antenna less than 2.5 1 VSWR is achievable between 245 MHz and 450 MHz the VSWR of the antenna exceeds 2.5 1 between 225 MHz and 245 MHz. Note that at these lower frequencies a transmitter may throttle down in the face of high VSWR and may even stop transmitting thus limiting the useful bandwidth of the antenna.

An orientation independent circularly polarized antenna that uses crossed vertical loops and a horizontal loop is provided with an increased bandwidth by providing shorts between adjacent elements. When a cube is provided with triangular shaped elements 4 each to a side of the cube shorts between the bases of adjacent triangular shaped elements on adjacent vertical faces of the cube provide for an extension of bandwidth at the low end of the antenna s operating range. In one embodiment for an 8 inch cube shorts down 0.95 from a top corner of the cube result in less than a 2.5 1 VSWR across the entire bandwidth of the antenna. For a Satcom antenna this means acceptable operation between 225 MHz and 245 MHz in an antenna that has a frequency range from 225 MHz to 450 MHz. Thus low frequency operation is not precluded. The type of antenna for which the subject shorts are effective is now described.

In order to provide an antenna which has a circularly polarized characteristic at all directions a pair of crossed vertical loops at 90 degrees to each other are driven in quadrature or at a 90 degree phase difference so that one has pure circular polarization at the zenith and pure vertical polarization at the horizon. As one progresses from the zenith to the horizon the circular polarization degrades. Moreover when using square loops for the vertical loops a better approximation of circular polarization can be obtained by driving the four loop segments at 0 90 180 and 270 to provide for progressive phase excitation of the loops.

By inserting a horizontal loop at 90 degrees to both of the vertical loops and by also phasing the horizontal loop segments at 0 90 180 and 270 it has been found that one obtains a circular polarization over an entire hemisphere and down to 45 degrees below the horizon. This is because when the vertical crossed loops are fed in quadrature there is good circular polarization at the zenith i.e. 90 degrees elevation. The axial ratio degrades as the elevation angle decreases until at 0 deg elevation there is only vertical polarization. The missing horizontal polarization at 0 deg is filled in by the horizontal loop. Note that the horizontal loop legs are progressively fed in 90 degree increments. The reason for this type of feed is that the vertically polarized wave from the vertical crossed loops has a progressive phase as a function of azimuth. The horizontal loop must have a progressive phase that matches the progressive phase of the wave from the vertical crossed loops. Furthermore the phase of the horizontal loop must be offset 90 degrees from that of the vertical crossed loops.

In one embodiment this triple loop orientation independent antenna is implemented utilizing pairs of bowties on the six faces of a cube with the pairs of bowties being implemented as triangular shaped conductive elements.

The cubic implementation of the three crossed loops provides an orientation independent antenna in which the field from this antenna is circularly polarized at all angles of arrival within a hemisphere.

Thus at any position on a hemisphere surrounding the antenna one has circular polarization with magnitudes or amplitudes that are equal regardless of the point in space at which a signal comes in.

This permits robust receipt of signals regardless of angle of arrival and regardless of how the signals are either originally polarized or have their polarization altered before they arrive at the antenna.

In one embodiment the miniature antenna is provided by having triangular shaped metallic elements on a cube so as to form four opposed triangular elements on each side of the cube.

It will be appreciated that given a face of the cube and appropriate phasing of a pair of triangular shaped elements for one loop one can achieve circular polarization in a direction normal to the face of the cube both in the forward and rearward directions. This is accomplished by driving the two orthogonal sets of opposed triangular elements on the given face to yield circular polarization normal to the face of the cube.

Note that one has either a vertical polarization or a horizontal polarization out the edge of this face.

By using the various faces of the cube and forming the horizontal loop with four legs so that the legs of the loop are driven at 0 90 180 and 270 offset by 90 from the vertical loops one can fill in the circular polarization out the edge of the face. For instance for a cube side perpendicular to the face of the cube discussed above its circular polarization directions being normal to this face are also normal to the circular polarization directions of the first face. This provides a full 360 degrees of circular polarization in the horizontal phase.

Likewise the top face of the cube being perpendicular to the front face provides circular polarization in the vertical direction. This when combined with the circular polarization in the horizontal direction now achieves circular polarization in a full 180 degree arc so that the combined faces provide circular polarization throughout a hemisphere in which the cubical antenna resides at its center. The subject antenna does provide better than hemispherical coverage in that its coverage extends downwardly by about 45 degrees.

More particularly in one illustrative embodiment the loops are provided by the triangular shaped elements on various faces of a cube with their apecies pointing inwardly to a point at the center of the face of the cube. In one embodiment one pair of the crossed vertical loops is provided by sides and and triangular elements on each face. The orthogonal vertical loop is comprised of sides and and elements on each face.

In order to provide for the feeding of the crossed pair of loops the 3 4 elements on sides and are fed progressively at 90 increments with the 1 2 elements on sides and being driven at 90 with respect to the first loop. Additionally each of the legs of each vertical loop are excited at 0 90 180 and 270 . The horizontal loop is driven by driving the 1 2 elements on vertical sides and progressively at 0 90 180 and 270 offset 90 from the vertical loops.

While the phasing of the various legs of the various loops might require different phasing boxes for each of the loops it has been found that the appropriate phasing of each of the legs of each of the loops can be accomplished utilizing a specialized feed network utilizing 6 hybrids. By feeding selected pairs of triangular elements on each side of the cube utilizing these 6 hybrids one can simultaneously provide the appropriate phasing for each of the legs of each of the three loops.

In one embodiment in order to provide feeds for the triangular shaped elements on the various faces of the cube a number of combiners and or hybrids are used. The combiners hybrids establish the appropriate phase relationships. The first combiner functions as a summer to take the antenna feed and divide it into a feed that is associated with one corner of the cube which corresponds to the feeding of one of the aforementioned crossed loops.

The combiner summer also splits off a signal which feeds a diametrically opposite corner of the cube to form the feed for the second of the crossed loops.

In an embodiment in which the combiners are not housed within the cube for the crossed loop associated with one corner of the cube a combiner splits the incoming signal and passes it to three separate hybrids with each of the separate hybrids driving a set of coaxial feeds having their outer braids bonded to respective triangular elements as the coax extends towards an apex of an associated triangular element.

Each of the adjacent sections for instance and on for instance sides and of the cube are fed in this phased manner.

The result of the phased drive of sections and on sides and of the cube are pairs of crossed loops with one loop formed at sides and and with the orthogonal loop formed at sides and . When driven appropriately the result is the aforementioned circular polarization characteristic of the antenna that is independent of angle of arrival.

In one embodiment the sides are connected to each other with matching and balancing impedances Z. Note that the cube is centered in a spherical coordinate system in which the impedances are parallel combinations of capacitance and meanderlines.

With appropriate excitation the field associated with the cubic antenna in the upper hemisphere is close to being proportional to i exp i i Eq. 1 where and are the spherical coordinate basis vectors.

From this equation it can be seen that an observer sees a circularly polarized wave from any vantage point in the hemisphere.

Note that a small error associated with the component is present since the fields associated with that direction deviate from sinusoidal. The maximum deviation from 1 of the axial ratio is 0.8. If a sphere is used instead of a cube then the worst case axial ratio is 0.95.

For an internally fed antenna in one embodiment each side of the cube is fed with two ferrite coaxial transmission lines. For each vertical loop this leads to four pairs of coaxial cables converging at the center of the cube to form a beam former. All four excitation pairs are driven at 0 or 90 depending on which vertical loop is driven. The four pairs are combined in an eight way summer so that the two vertical loops can be driven albeit with a 90 phase shift provided by hybrids. The hybrids can be made up of wide band surface mounted components confined to a metal enclosure at the center of the cube with equipment embedded in such a volumetric based antenna not compromising performance. Note that the input ferrite loaded coax feeding the beam former can enter the antenna via one of the corners.

In an alternative embodiment it is possible to feed the antenna without penetrating the interior. This type of feed is useful when the antenna interior is used as a space for other parts of the system and where the transmitter or receiver to be connected to the antenna is external to the antenna.

Note that in this embodiment pairs of coaxial lines feed selected sides of the vertical loops. The outer conductor of each coaxial line is bonded directly to the associated triangular element. The inner coax conductors cross over at the end of the coax to feed the adjacent triangular elements at the gaps between the feed vertices with the feed forming a so called infinite balun. The three pairs of coax converge to the nearest corner of the cubical antenna. At this corner ferrite loading is applied to the coaxial lines as the lines leave the antenna surface.

Note there is a complimentary set of three pairs of coaxial lines on the opposite side of the antenna. Sides and are fed by these complimentary pairs. The lines converge at the corner diagonally situated with respect to the nearest corner. The two sets of three pairs of lines are brought together and coupled into a beam former.

The subject antenna can be fed for either right or left hand circular polarization. For optimal operation both polarizations can be monitored simultaneously to effect polarization diversity. This can provide double the data throughput.

The above describes the construction and phasing of an orientation independent circularly polarized antenna. To lower the VSWR in the lower frequency range shorts are provided to provide synergistic coupling between the elements thus to lower the VSWR at the lower antenna frequencies.

In summary an orientation independent antenna presenting a circular polarization characteristic and having both crossed vertical loops and a horizontal loop is provided with improved bandwidth by the use of shorts between adjacent antenna elements to lower the VSWR of the antenna especially at the lower frequency range of the antenna. In one embodiment the antenna elements are on the vertical faces of a cube.

Prior to describing the improved performance afforded by the subject shorts the basic orientation independent antenna with circular polarization is now described.

Referring to the importance of having an orientation independent antenna is illustrated. Here a robot carries an antenna which has an antenna polarization characteristic of a whip antenna. As can be seen the robot is traversing stairs within a building having walls which in general attenuate signals for instance from a satellite as the signal goes through wall and arrives at antenna .

As illustrated the transmitted signal polarization is illustrated by a double ended arrow which as can be seen does not line up with double ended arrow corresponding to the polarization of the whip antenna. This means that the signals from the satellite which may not be very powerful and which are further attenuated through the walls of the building may not be robustly received if there is a mismatch in the polarization directions of the incoming wave and the antenna on the robot. In point of fact it is possible that these signals could be cross polarized and therefore result in no energy being received by the transceiver within the robot.

Referring to robot is shown traversing terrain which has a hill that may block signals from satellite . Moreover the signal from robot may be reflected by building and may be received at antenna with a polarization direction altered as illustrated at .

Signals from satellite come direct from the satellite as illustrated at but may be attenuated as they pass through mound or hill such that they arrive at antenna with an unknown polarization direction and somewhat attenuated. Signals from satellite may be reflected by foliage and redirected towards antenna again with a polarization direction that may not match the polarization of antenna .

What this shows is that in order for the robust receipt of signals as weak as they may be it is important that the antenna be able to respond to whatever is the polarization direction of the incoming signal.

It is part of the subject invention that the antenna utilized on the robot has a circular polarization characteristic such that it is insensitive to the polarization direction of incoming waves.

While the subject antenna will be described in connection with robots other applications or orientation independent antenna are within the scope of this invention. For instance the use on ships avoids the use of whip antennas which sometimes interferes with aircraft.

As can be seen in robot is provided with the subject antenna which is in the form of a cube. Not only is the cube small but its volumetric characteristics make it a wide band width antenna as well.

The antenna elements of the cube which will be described hereinafter as being triangular are phased by phasing module such that as far as receiver is concerned the signals arriving at antenna will be received regardless of their polarization. This is because for antennas that are given a circular polarization there will be no angle at which a polarized wave will not be detected.

Put another way no matter what the point of view within hemisphere the in phase and quadrature components will be identical and will be at right angles to each other with these two vectors orthogonal and having equal magnitudes. This is characteristic of circular polarization and from antenna s point of view its polarization characteristic is circular no matter the angle of arrival of the incoming signal.

How to construct such an orientation independent circularly polarized antenna which preserves its circular polarization 360 around the azimuth and 180 from horizon to horizon can best be explained by the manner in which antenna is meant to operate.

Referring to in order to provide a truly circularly polarized antenna or at least when having a circular polarization response throughout a hemisphere with the antenna at its center one utilizes crossed vertical loops and . In one embodiment each of these loops have 4 legs and are mounted orthogonal one to the other. Assuming that the currents Iand Iare constant along the loop for circular polarization Iand Iare in quadrature exhibiting a 90 phase difference. This is shown by the phasing circuit in which currents Iand Iare 90 out of phase.

The characteristic of crossed vertical loops driven in this manner is that one has a circular polarization at the zenith and a vertical polarization at the horizon. Thus from the zenith as one progresses to the horizon the circular polarization degrades.

While circular cross vertical loops provide circular polarization at the zenith as shown in legs and of loop are excited such that the legs have a progressively stepped phasing. This means that assuming leg has a 0 phase with respect to leg leg will have a phase shift of 90 leg will have a phase shift of 180 and leg will have a phase shift of 270 .

Likewise for crossed loop assuming leg has a 0 phase with respect to leg leg will be shifted by 90 leg will be shifted by a 180 phase and leg will be shifted by leg 270 .

While starting off with constant current in the vertical crossed loops progressive leg phasing is utilized in the crossed loops because it gives a better approximation to circular polarization. Furthermore progressively phasing the legs of the vertical loops provides circular polarization not only over the hemisphere but also below the horizon down to approximately 45 degrees. Thus as the progressive phase excitation of the legs of the vertical loops yields a better approximation to circular polarization.

Referring now to assuming that one has properly excited and phased the vertical loops horizontal loop is utilized to fill in the circular polarization from the zenith to the nadir. As can be seen horizontal loop is mounted orthogonal to vertical loop and and in general is driven at 90 our of phase with respect to the signals applied to the vertical loops. Thus a signal at source is applied to a hybrid which drives the horizontal loop with a 90 phase shift with respect to a signal on line that is applied to a hybrid . It can be seen that the hybrid passes the 0 phase shifted signal to loop and phase shifts the signal to loop by 90 .

As will be seen horizontal loop is provided with legs or segments and which are excited with progressive 90 phase shifts such that if leg has a 0 phase shift leg is progressively shifted by 90 leg by 180 leg by 270 with respect to leg .

The vertically polarized wave from the vertical crossed loops has a progressive phase as a function of azimuth. The horizontal loop must have a progressive phase that matches the progressive phase of the wave from the vertical crossed loops. Note also that the phase of the horizontal loop must be offset 90 from that of the vertical crossed loops.

A volumetric antenna which can provide for the two crossed vertical loops and the horizontal loop is implemented utilizing a cubic structure in which the cube carries four triangular shaped conductive elements on each face.

As illustrated in cube has a side on which are disposed triangular elements and respectively elements and . This structure is duplicated on each of the sides of the cube with the pairs of opposed triangular elements being phased to provide for the aforementioned three loops.

Having constructed this antenna as illustrated in various of the triangular shaped elements can be driven so as to provide vertical crossed loop which is the first of the orthogonally mounted vertical loops.

In this figure cube Sides and are driven utilizing coaxial cable having a center conductor and an outer braid attached to opposed apexes of opposed triangular elements. In this figure as far as Side is concerned coax has its outer braid connected to the apex of triangular element with the center conductor coupled to the apex of triangular element . As to Side coax has its center conductor coupled to the apex of element on Side and its outer braid connected to the apex of triangular element .

Likewise for Side coax has its center conductor connected to the apex of triangular element whereas the outer braid at is connected to triangular element . Finally for Side coax has its center conductor coupled to the apex of triangular element whereas the outer braid is coupled to the apex of triangular element .

Coaxes and are phased by a phasing box or module to provide the indicated phasing. This corresponds not only to the creation of Loop but also provides Loop with the stepped phasing 0 90 180 and 270 for the legs as illustrated at .

Referring now to the formation of Loop has associated triangular shaped elements on Sides and . Here as to Side coax has its center conductor coupled to element whereas the outer braid is coupled to element . As to Side coax as a center conductor coupled to element with the outer braid coupled to element .

As to Side coax has its center conductor coupled to triangular element whereas the outer braid is coupled to triangular element .

Finally coax has a center conductor coupled to element whereas the outer braid is coupled to element .

Phasing module establishes the indicated phasing on the noted coaxial lines and provides Loop with the stepped phasing from 0 through 270 for the various legs thereof.

Referring now to the horizontal loop is established by sections and on Sides and of antenna with coax having it center conductor connected to element and its outer braid connected to element . For Side coax has its center conductor connected to element and its outer braid connected to element .

The same is true for Side where coax has its center conductor connected to element and its outer braid connected to element .

Finally coax has its center conductor connected to element whereas its outer braid is connected to element .

Here phasing module phases the coax lines as illustrated with the phasing providing the stepped 90 leg phasing on the horizontal loop as illustrated.

The above phasing of the elements of the cubic antenna to provide angle independent circular polarization requires sophisticated phasing circuitry or phasing modules.

Moreover referring to with only six standard hybrids or 4 way quadrature power dividers one can simultaneously phase the vertical loops 90 apart provide for the stepped leg phasing and also phase the horizontal loop 90 from the vertical loops and at the same time provide the legs of the horizontal loop with the stepped phasing. Note that for a reverse circular polarization one selects the conjugate phase shift shown in parenthesis.

It can be shown that with the hybrids of one can provide the hemispheric circular polarization characteristic for the antenna and also provide for coverage below the horizon down to 45 .

The hybrids of are in accordance with the table of that refers to the phasing between elements and the elements on the indicated sides.

Moreover as can be seen in the overall gain with respect to elevation angles is substantially constant over a wide bandwidth of 225 450 MHz making this antenna a relatively wide bandwidth antenna.

Referring now to if it is not desirable to provide the hybrids within the confines of the cube the antenna may be driven exteriorly with the hybrids attaching to respective coax feeds that emanate from a corner of the cube and run down the triangular elements with the exterior braid bonded to the respective triangular element as illustrated. Here antenna is shown having coaxes and running down respective edges of triangular elements and with these coaxes coupled to hybrids .

What can be seen is that the appropriate phasing can be accomplished by externally driving half of the triangular elements from one corner of the cube as illustrated using three hybrids with an opposed corner not shown driven by a second set of hybrids so as to provide for the drive and phasing to produce the orthogonal oriented vertical loops and an orthogonally oriented horizontal loop to give the antenna its circular polarization characteristic.

Note that the subject antenna is right hand and left hand polarization capable. For optimal operation both modes can be simultaneously monitored to obtain the advantages of polarization diversity. In fact the two polarization modes may be used as two separate channels. The additional polarization mode is obtained referring to by utilizing a second 6 way combiner and feeding it with the unused output of ports of the six 90 degree hybrids.

It will be appreciated that the cubic geometry can be altered to a spherical configuration with the 24 triangles laid out on a sphere. The feed methodologies are the same as those of the cubic version. The sphere reduces an error present in the cube due to a deviation from ideal sinusoidal excitation. The worst case axial ratio improves from 0.8 for the cube to 0.95 for the sphere.

Referring now to antenna is provided with a number of triangular shaped elements on the various six faces of the antenna. As mentioned above at least for satellite communications purposes it is important to have the frequency response of the antenna be for instance between 225 MHz and 450 MHz. In order for the antenna to properly operate especially when coupling the antenna to a transmitter the VSWR is required to be less than 2.5 1.

While the antenna described hereinbefore is generally satisfactory when one goes below 245 MHz the VSWR rapidly exceeds 2.5 1. What happens at this point is that a transmitter will throttle down its output and will quickly shut off in the face of rising VSWR. Thus in order to extend the transmitter operating range of the antenna it is important to reduce the VSWR at these lower frequencies.

This has been accomplished in the subject invention by providing shorts between adjacent antenna elements and more particularly between the bases of triangular elements on adjacent vertical sides of a cube.

These shorts are illustrated in at and are generally located a short distance from the top corners of the cube.

In one embodiment with a cube eight inches on a side the shorts are positioned 0.95 inches from the adjacent top corner of the cube.

This offset for the short from the cube corner was arrived at empirically and provides good results for short placement within an eighth of an inch.

It is noted that the antenna cube and the offset for the shorts are scalable such that the short offset is 0.11875 with respect to the length of a side of the cube.

With the empirically derived positioning of the shorts the antenna exhibits less than a 2.5 1 VSWR so that the antenna can work down to 225 MHz.

In adapting the cubic antenna of to be more broad banded it was necessary to provide additional synergy between the sides of the cube and more importantly between the elements thereon. It will be appreciated that the shorts provide a small amount of extra coupling between the sides of the cube with the extra coupling being effective to reduce the VSWR.

While the exact position of the shorts with respect to the corners of the cube were derived empirically the subject invention is not limited to the exact positioning of the shorts but is rather broad enough to encompass positioning shorts between adjacent antenna elements.

Moreover when utilizing a spherical shape for the antenna shorts between laterally adjacent elements on the surface of the sphere are within the scope of this invention.

While the present invention has been described in connection with the preferred embodiments of the various figures it is to be understood that other similar embodiments may be used or modifications or additions may be made to the described embodiment for performing the same function of the present invention without deviating therefrom. Therefore the present invention should not be limited to any single embodiment but rather construed in breadth and scope in accordance with the recitation of the appended claims.

