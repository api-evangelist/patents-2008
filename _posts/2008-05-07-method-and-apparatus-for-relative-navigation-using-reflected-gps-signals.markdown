---

title: Method and apparatus for relative navigation using reflected GPS signals
abstract: A method and system to passively navigate an orbiting moving body towards an orbiting target using reflected GPS signals. A pair of antennas is employed to receive both direct signals from a plurality of GPS satellites and a second antenna to receive GPS signals reflected off an orbiting target. The direct and reflected signals are processed and compared to determine the relative distance and position of the orbiting moving body relative to the orbiting target.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07817087&OS=07817087&RS=07817087
owner: The United States of America as represented by the Administrator of the National Aeronautics and Space Administration
number: 07817087
owner_city: Washington
owner_country: US
publication_date: 20080507
---
The embodiments of the invention described herein were made by employees of the United States Government and may be manufactured and used by or for the United States Government for governmental purposes without payment of any royalties thereon or therefor.

The present invention relates to navigating a moving body with the use of GPS signals and more particularly to the use of reflected GPS signals to passively navigate an orbiting body towards an orbiting target.

Spacecraft require equipment that calculates the orbital position velocity time and attitude. The advent of the Global Positioning System GPS increased the desirability of using onboard processing systems for spacecraft position determination.

The GPS satellite system is a collection of satellites that can be used for missile satellite aircraft and terrestrial navigation. Each GPS satellite broadcasts its own ephemeris and time thereby allowing a GPS receiver to determine its position. Typically a GPS receiver calculates its position from the simultaneous observation of any four GPS satellites in order to calculate its position. A civil grade GPS receiver can accurately determine its position within 20 meters determine its velocity within 0.6 meters second and the current time with a 10 nanosecond accuracy. At least twenty four valid GPS satellites are in the GPS constellation at any given time.

A GPS receiver is an autonomous instrument that transforms signals from GPS satellites into point solutions for spacecraft navigation. Current GPS receivers have a radio frequency section for receiving and converting signals received from a spacecraft s antennas. The digitized signals are then forwarded to one or more correlators controlled by the receivers own processor. The correlators look for matches between the incoming signal and the C A code for different satellites. When a satellite lock occurs or the incoming signal matches an internally generated pseudo random noise PRN code the receiver s processor is notified. The processor contains executable code to generate a pseudo range or a line of sight distance to the satellite. The processor may also contain the executable code of an orbit propagator. The pseudo range is a measurement input to the navigation filter that calculates point solutions for determining the orbit of the spacecraft. While such GPS systems may be employed to position and track an orbiting moving body such as the Space Shuttle such systems do not provide the ability to determine the position relative to another orbiting body. Conventional GPS receivers can not passively provide relative navigation or relative position data which are necessary during formation flying docking or other approach of space craft to proximity to another orbiting body.

The space environment poses additional obstacles to that of land based tracking systems. Because of the speeds associated with spacecraft motion GPS satellites are in view for much shorter time periods than when viewed from a ground reference. The appearance and disappearance of GPS satellites from view causes their output signals to slew through the entire range of the 45 kilohertz Doppler shift. Typical space craft formation flying and autonomous rendezvous missions rely on active transmissions schemes such as RADAR RAdio Detection and Ranging and LIDAR Light Detection and Ranging which require specialized hardware requiring additional mass and power consumption. With the extreme weight and power restraints associated with space flight there is a particular need for a reliable navigation positioning system which reduces weight and power consumption requirements as well as taking advantage of free GPS signals.

The use of Reflected GPS signals per se is also known. U.S. patent application publication 2006 0077094 entitled Information Information Gathering Using reflected Signals discloses a method of using reflected signals in a land based application to monitor the presence or absence of an object such as if a vehicle occupies a parking space and is hereby incorporated herein in its entirely. This system is not only ill suited for orbital applications but does not make use of the reflected signal to navigate to a target.

It is also known to use Bistatic Radar Systems where a radar transmitter located remotely from the projectile such as onboard a ship illuminates the target and the reflected returns are received by a receiver located on the projectile. The tracking data from the radar measurements are then used to calculate the proper guidance signals to direct the projectile to the target. An example of a bistatic radar system is discloses ill U.S. Pat. No. 6 653 972 which in incorporated herein it is entirely. These systems require the use and control of an active radar transmitter and do not provide a suitable global positioning function. Rather these systems are employed to simply acquire and hone in on a particular target. Therefore such Bistatic radar systems are not suited for orbital positioning and navigation or have the ability to rely on a passive autonomous system.

One of the objects of the present invention is to utilize reflected GPS signals to provide passive autonomous relative navigation of an orbiting spacecraft towards an orbiting body.

The present invention is directed to a method and system to passively navigate an orbiting moving body towards an orbiting target using reflected GPS signals. A pair of receive antennae are employed. One to receive direct signals from a plurality of GPS satellites and a second antenna to receive GPS signals reflected off an orbiting target. The direct and reflected signals are processed and compared to determine the relative distance and position of the orbiting moving body relative to the orbiting target.

A preferred embodiment of the invention and the various features and advantageous details thereof are explained more fully with reference to the accompanying drawings and detailed in the following description. It should be noted that the features illustrated in the drawings are not necessarily drawn to scale and descriptions of well known components and processing techniques are omitted so as to not unnecessarily obscure the embodiments of the invention. The examples used herein are intended merely to facilitate an understanding of ways in which the embodiments of the invention may be practiced and to further enable those of skill in the art to practice the embodiments of the invention. Accordingly the examples should not be construed as limiting the scope of the embodiments of the invention.

The present invention is directed to a method and apparatus for passively navigating an orbiting space craft towards and orbiting target using reflected GPS signal. depicts the relative geometry between the space shuttle Hubble space telescope and a GPS satellite. By comparing both signals received directed from the GPS satellite and signals reflected off the Hubble a navigation system employed on the space shuttle can passively and autonomous determine its position relative to the Hubble thereby providing navigational aid passively and autonomously. Acquisition of and tracking of GPS signals are well known in the art and need not be discussed in detail. U.S. published patent application US 2006 0082496 to Winternitz et al. discloses a radiation hardened fast acquisition weak signal tracking system and method and is hereby incorporated herein by referenced in its entirety.

The actual GPS measurements recorded from any of the constellation of satellites are the pseudorange and psuedorange rate. The pseudorange is based on the time of flight between the GPS receiver and the GPS transmit antenna. This is used to form a range measurement and thus solve for a position fix when enough satellites are available. The other measurement available is pseudorange rate that is essentially the rate of change along the line of sight vector to the satellite. The pseudorange rate dot can also be viewed as the Doppler shift on the signal. The pseudorange rate equation is equivalent to the carrier rate which tends to be a less noisy measurement.

The measured pseudorange is the difference between the system time at which the signal left the GPS satellite and the system time at which the signal reached the user. This is given by r is the geometric range is given by r c T T which is the exact time of flight between the user and the GPS satellite. tis the receiver offset from system time is the offset of the satellite from system time and is due to other measurement errors.

The GPS constellation is segmented into 3 parts the user the control and space segment. The three main sources for the space segment are satellite clock stability clock perturbations and selective availability. For the control segment it s primarily ephemeris prediction error. For the user segment it is ionospheric delay multipath receiver noise and resolution.

The GPS satellite clock error is the residual error from a second order polynomial fit adjusting for relativistic effects the clock bias clock drift and frequency drift. The Satellite Clock error is on the order of 3.0 m. The satellite ephemeris error is caused from the deviation in the current satellite ephemeride stored onboard the GPS satellite with the satellite s true position. These ephemeris values are used to form the line of sight vectors from each SV to the user thus each perturbation adds error into the pseudorange. This is normally on the order of 4.2 m for a typical ground based GPS receiver.

The GPS system also experiences relativistic effects due to the gravitational potential differences. Space users also experience ionospheric effects. This is generally seen as a bias in the measurement. The ionospheric effect is modeled off of the path length of the signal traveled through the ionosphere. There are also measurement errors from within the receiver. These are from the tracking loops internal to the GPS receiver. The dominant sources of error introduced here are the thermal noise jitter and dynamic stress error. The secondary sources are given by the hardware and software resolution and clock drift. The last sources are multipath and shadowing effects. For the purposes of rendezvous we are actually interested in tracking these multipath sources in order to solve for a relative position. The GPS pseudorange error budget is on the order of 8.0 m for a standard GPS receiver located on the ground.

The direct pseudorange rate is a measurement of the rate of change of the psuedorange between the user and the GPS satellite. It is given by dot over l s 

That is the rate of change of the psuedorange along the line of sight vector and the user. The error is mainly determined by the clock drift component. Generally these measurements are noisy compared to that of the pseudorange.

The constructed measurements for the bistatic ranging problem are the differenced reflected psuedorange and the reflected psuedorange rate. The reflected psuedorange is differenced with the direct signal psuedorange to remove the common mode errors from the measurement. Some of the common mode errors removed are front end jitter receiver bias thermal noise and line bias leaving us primarily with ionospheric effects multipath and jitter error contributions. The psuedorange rate is the additive Doppler shifts along the line of sight vectors between Hubble and the Shuttle and between Hubble and the GPS constellation.

This difference reflected pseudorange measurement is constructed from the difference in the direct path signal and the reflected signal. The equation is given by 

That is the sum of the geometric range from the Shuttle to Hubble Hubble to the GPS satellite and the Shuttle to the GPS satellite plus the residual errors.

The psuedorange rate can be seen as a Doppler shift on the signal. The reflection can be viewed as a retransmission making it an additive process. dot over l s l s

Where the l sis the line of sight vector between the Shuttle and Hubble and l sis the line of sight between Hubble and a GPS satellite. The primary sources of error contributing to the reflected psuedorange rate are the same of that as the direct measurement however the quality of the incoming signal is degraded due to the reflective process and the actual effect is unknown.

Typical GPS receivers use a simple least squares algorithm to determine position and time. It requires at least 4 visible satellites to solve for the four unknowns x y z and the user clock offset from the GPS constellation. In addition to position estimates some also do perform a finite difference of the positions to solve for velocity as well.

In more advanced receivers a Kalman filter may be implemented in order to utilize the dynamic information as well as the measurements to improve the accuracy of the receiver. On orbit the GPS receiver will experience large dynamic stress and motion with respect to the GPS satellites it is almost necessary to filter this heavily to provide a good navigation solution. The method of the present invention implements an extended Kalman filter which will now be described.

The Kalman filter represents an optimal filter for a linear system with additive gaussian noise with zero mean. Since the dynamics of an orbiting body are well understood and their equations are well formulated it is possible to exploit that information when forming the Kalman filter when applied to the relative navigation problem. The canonical form of the Kalman filter is the optimal filter for a linear system incorporating a blending of known dynamics with that of the measurements. The discrete Kalman filter can be broken up into two distinct steps the time update and measurement update.

These equations are continuous and need to be discretized in order to implement them in the Kalman filter.

This relates timestep k 1 to timestep k. In order to calculate the state evolution between timesteps for a linear system the state transition matrix is given by e

This model only concerns the unforced dynamics so without loss of generality B is assigned 0 and is dropped. Now these equations can be applied to the Kalman filter form.

The first step in the Kalman filter is to propagate the measurement from time step k to the time step k 1. This is done by multiplying by the state transition matrix or integrating from to t. circumflex over x 

P is defined as circumflex over x x circumflex over x x it represents the variance in the estimator errors.

The first step of the measurement update is to form the Kalman Gain K. The Kalman gain is the optimal estimate to minimize the errors along the diagonal of the covariance matrix. 

The next step is to apply the gain to the measurement error. The H matrix is the measurement connection matrix it connects the states with the measurement at time step k. circumflex over x circumflex over x 

While die equations are relatively straight forward in the discrete Kalman filter they require a measurement model and the plant dynamics are linear systems. Unfortunately in the real world most systems are nonlinear. In particular GPS has a non linear measurement model.

The solution to a nonlinear measurement model can be done by approximating Y. Given a nonlinear measurement model Y h x 

The last two parts of a Kalman filter are the measurement covariance and process noise matrices R and Q respectively. The measurement covariance matrix consists of the variance of noise on the signal. From the canonical form x it can be shown that R nn 

The process noise matrix is given by the variance un modeled forces in the dynamic model. Assuming we have a model noise actually enters the system as a disturbance on the input. Q E dd 

Unfortunately the equation to describe the matrix Q is difficult to obtain because it requires calculation of . In the simulations Q is treated as a free variable adjusting it to give the optimal performance and reduce the process covariance bounds such that they were roughly equal to the measured variance in R.

In the case of relative navigation it is an essential to be able to solve for your relative position as well as possible. One of the best ways is to improve your solution is to have an accurate dynamic model. This way one can rely on the dynamic model to propagate through measurement outages and noisy measurements. This is especially true in the case of applying reflected GPS measurements.

Defining the necessary components to construct the filter is necessary before beginning formulation of the Kalman filters for the relative navigation problem. Given a dynamical system 

It is thus necessary to define a state vector X. The state vectors used in an absolute model are the absolute positions and velocities of the Shuttle and HST as well as the bias state for the navigation solution. Typically a GPS receiver would include the bias drift as another component. For this simulation since the rendezvous is over a short period of time bias drift can be neglected. x r v r v b 

For a completely relative model Hill s equations are used to propagate the states. This requires formulating the problem entirely in a relative frame. The states in this case are X 

In this formulation is the relative position in hill s frame and is the velocity. Typically the dynamic model is a nonlinear equation given by a f dot f x . In this analysis two different model are examined. The first model is based purely on the 2 body equation of motion given by Hill s equations. This model is a linearized representation of the relative spacecraft dynamics and has the form dot over x Ax. where A is given by the partials of f x evaluated along a reference trajectory.

Hill s model is conveniently linear simplifying the application of the Kalman filter. Hill s model is only valid for close proximity maneuvers and requires a special coordinate frame to operate in centered on a circular orbit for one of the vehicles.

 is the projection of the velocity in the plane perpendicular to circumflex over R and is the direction of angular momentum perpendicular to the orbital plane.

Where r and dot over r are the position and velocity vectors in the IJK reference frame. Since Hill s frame is a relative frame typically one spacecraft is chosen to be the reference orbit. This orbit is ideally circular. In this case the orbit chosen is the space shuttle. This is denoted by r the other spacecraft is typically called the interceptor or r. Hill s equations also known as the Clohessy Wiltshire equations which are the governing forces for relative two body motion. These equations are well known and have an explicit solution. 230 20 0 or by defining

x x dot over x then provides the form dot over x f x . Now taking partials with respect to the states arriving at the canonical linear system form dot over x Ax.

Hill s equations being in a linear form fit well into the linear systems toolset. If we assume a constant A over each discrete time step we can approximate 

This formulation provides a state transition matrix in linear form that can be easily applied to both the state propagation steps and the covariance propagation. Although the relative dynamics are minimal in comparison between spacecraft their actual perturbations on the dynamics are quite significant in low earth orbit. In addition to increasing the fidelity of the dynamic model it allows customization of the orbits and adds other effects such as thruster firing and differences in their drag coefficients.

The coordinate frame used in the high fidelity dynamic model is the Earth Centered Inertial frame. This reference frame was chosen because it greatly simplifies the equations of motion. The ECI coordinate system is also known as the IJK system. Referring to the axis is pointed towards the vernal equinox the axis is 90 to the east along the equatorial plane and the circumflex over K axis extends through the North Pole.

The Jterm is the zonal harmonic constant given by 1082.7 10. is the rotation rate of the earth Ris the radius of the earth m is the objects mass A is the cross sectional area and V is the relative wind. The relative wind is given by the equation

Where 3.275e 12 kg m a is the current altitude ais the reference altitude 400000 m and H is the scaling height 58515 m. Using the same from the simple GPS Kalman filter choosing r as position and v as velocity the equations it is now appropriate to write these equations in terms of first order derivatives to fit the canonical form are dot over r v and 

In this formulation g is the nonlinear force model for the orbital dynamics. Now let the state vector x r v . or

The equations are in the appropriate form to apply the Kalman Filter. Since the Kalman filter s covariance propagation is a linear process it is necessary to formulate the partial derivatives with respect to the state vector. Although the partials are not used to propagate the dynamics they are needed when forming the state transition matrix for the covariance updates.

Hill s equations of motions are conveniently in linear form x A B. The state transition matrix can simply be approximated by the matrix exponential e.

Where A is the linear system A matrix and T is the time interval. In this particular implementation the time step is on the order of 1 second thus T 1 This is both used in the dynamics and the covariance propagation. In the full nonlinear case estimates would diverge after a few iterations using a first order approximation of the system. Thus the state is integrated over time steps of one second. The covariance matrices are propagated linearly using 

Since A is not constant over the time interval t t we cannot rely on the matrix exponential approximation for this integration.

In order to incorporate the variation of the states between time steps the added dynamic equation dot over A is included within the dynamic model propagation. This allows integrating the dynamics and solving for between time steps while varying A with the current state estimates. In order to solve for the initial condition vector of the states and the identity reshaped into a vector is required. The resultant at the end of the integration is then used in the linear propagation of P.

Implementing the filter with Hill s model is fairly straightforward. Since Hill s model is in the relative frame the shuttle s position is implicitly included in the states any parameters derived from the position can be assumed to be provided by the GPS receiver s navigation solution.

The subscripts stand as the Shuttle to Hubble Hubble to a GPS satellite and A GPS satellite to the Shuttle respectively. The GPS satellites position is known from the ephemeredes and Shuttle s position is known from the receiver s navigation solution. If we define X X that is the relative position between the Hubble and Shuttle and rotate into Hill s frame we arrive at is our relative position vector to Hubble in the ECI frame and part of the state vector. Now taking partials with respect to we arrive at 

For the nonlinear full dynamics implementation measurements are given by the measurement equations as a function of the states of the system such that y h x . In this formulation there are 4 different measurements pseudorange differenced reflected pseudorange pseudorange rate and reflected pseudorange rate. In order to use these measurements in our Kalman filter design we must linearize the measurements in order to form the canonical H matrix.

The direct psuedorange measurement is given by the equation neglecting the ionospheric receiver ephemeris and other errors T the measurement can expressed in terms of a range and bias.

The differenced reflected pseudorange provides information about the absolute shuttle and Hubble position states. Its measurement equation is given as follows 

The bias terms difference out as well as many of the other common mode errors greatly simplifying the calculation and the algebra. The subscripts sh hg and gs signify the range from shuttle to Hubble Hubble to GPS transmitter and shuttle to GPS transmitter. These are equivalently square root over square root over square root over square root over square root over square root over square root over square root over square root over 

In order to form the H vector equation we must first linearize the measurement equation. The partial with respect to the Shuttle s position 

Now substituting in the range definitions and taking partials of HST s y and z components we arrive at the H vector 

The measurement is simply the relative velocity along the line of sight vector between the GPS transmitter and the Shuttle.

Because there is no information contained in the pseudorange rate about the state vector of the Hubble the partials with respect to Hubble s states are 0.

The reflected pseudorange measurement is essentially the sum of the Doppler shift along the paths of the signal. This is given by dot over l s l s

From this we need to take the partials with respect to the state vector components. For the shuttle position states in the x direction 

This simply leaves the line of sight vector to the Hubble expanding this into the x y and z components 

Now taking the partial with respect to the Hubble s velocity we simply get a relation involving the line of sight vectors.

The measurement matrix corrects the Kalman Filter s dynamic estimates with the current measurement estimates. The measurement matrix is stacked up in the same order as the measurements.

The process noise matrix Q describes the covariance error associated with the model. It generally describes the model errors and un modeled force inputs. In our case since Q is difficult to obtain it is treated as a tuning matrix to adjust the performance of the filter.

The R matrix represents the variance in the measurements. Ideally the variance is uncorrelated white gaussian noise. Since we can estimate the variance of the measurements with relative accuracy this matrix is essentially fixed.

The use of reflected GPS signals as a navigational tool may be particularly useful when navigating toward an orbiting target such as the Hubble Space Telescope HST in order to perform repairs replace critical parts or otherwise service an orbiting device. The ability to passively and autonomously navigate to perform servicing missions could lead to unmanned service missions as well as reduced weight and power consumption. The following description relates to navigating the space shuttle to the HST.

The space shuttle will incorporate a GPS receiver such as that disclosed and describe in US 2006 0082496 to Winternitz et al. which is incorporated herein in its entirely. The 496 receiver is particularly suited for implementing the method of the present invention using reflected GPS signals by having the ability to acquire and track weak GPS signals. The navigation system will include two antennas a Right Handed and Left Handed Circular Polarized LHCP RHCP antennas. The GPS receiver will be powered on as it approaches the HST within 1000 m from Hubble. The Shuttle s position can be estimated with conventional methods of navigation using direct GPS signals and a dynamic orbit model. The receiver onboard the Space Shuttle will be acquiring the direct signals as it approaches the HST which will be received by the RHCP GPS antenna. A convenient feature about a RHCP signal is that when reflected off of a surface such as the HST it reverses polarization and becomes left hand circularly polarized. This gives it a nearly perfect rejection for a reflected signal. Therefore the LHCP Antenna is well suited to pick up the reflected signals.

Both of the antennae will receive the raw RF stream mixed down to IF 35.42 MHz and then sampled at 8.192 MS s. This data will be processed as previously described to compare the direct and reflected signals to estimate the position of the Shuttle relative to the HST.

The use of ever increasing speeds of computers microprocessor and FPGAs complex signal processing algorithms will be used to apply the aforementioned filtering techniques and signal acquisition methods to determine the structure and composition of the reflected signals.

The GPS receiver used to record and process the data is the Navigator GPS. The GPS receiver is running at 65.536 MHz using a General Dynamics Coldfire processor and has three application specific Actel AX2000 FPGA s. The enhanced capabilities of this receiver are aided by the application specific FPGAs that implement an algorithm developed to acquire weak signals in real time as disclosed 496 to Winternitz et al. This algorithm is an FFT based acquisition algorithm that operates in the frequency domain. It is able to acquire and track signals down to 25 dB Hz. This is approximately 10 dB more sensitive than current off the shelf GPS receivers. This will enable the Navigator to acquire the weaker reflected signals off of the HST.

The Navigator receiver will be configured to track 24 channels 12 of them connected to the LHCP antenna and the remaining 12 connected to the RHCP antenna. While tracking a direct signal the reflected channels will be directed to search in a time delayed space with approximately the same Doppler frequency. This will tremendously aid acquisition of the weaker reflected signals.

The aforementioned extended Kalman filter will run on the navigation processor taking in the RHCP and LHCP measurements. Thus the Navigation system will be able to estimate the position of the Shuttle in orbit and the relative position of the HST by comparing the directed and reflected signals of a plurality of GPS satellites as previously discussed. Using a receiver to receive both direct and reflected GPS signals and comparing processing the embedded ranging data time delay etc. coupled with the dynamic model in the extended Kalman filter the navigation system of the present invention can passively and autonomously track a relative position of an orbiting spacecraft Shuttle to an orbiting target HST . The ability to passively and autonomously passively navigate a space craft toward a target not only reduces weight and power consumption but also paves the way for potential precise passive navigation of space craft for unmanned service missions.

A simulation and implementation of the method of the present invention will now be discussed in regards to a Shuttle mission approaching the Hubble Telescope.

The Hubble Rendezvous truth scenarios are chosen such that the initial conditions will result in a near collision of the Shuttle and Hubble. The truth model is generated with STK using a high fidelity orbit propagator.

The Space Shuttle may approach Hubble from the aft end with its bay doors pointed towards Hubble. This allows the Shuttle to dock cleanly with Hubble.

During the servicing mission the left and right handed GPS Antennae will be placed on the MULE inside the bay of the shuttle looking outwards.

The model focuses on simulating the uncontrolled motion of the two bodies. In order to represent the docking initial conditions were chosen such that the two space craft come within close proximity to each other.

The model was created using STK given a set of initial conditions and propagated over an orbit period. The STK model chosen was a 21 order gravity model with atmospheric drag on both the Shuttle and Hubble the coefficients of drag chosen as to represent the relative mass and area ratios.

The visibility of each GPS satellite is determined by the geometry of the GPS constellation with respect to the location of Hubble and the Shuttle. The satellite visibility is essential to determining how many measurements both direct and reflected are available. This number of measurements available influences the absolute and relative position accuracies.

The GPS constellation is constructed and propagated using the keplerian elements given by an almanac file. The almanac file is generated and uploaded to each GPS satellite. It represents a limited set of the keplerian orbits in order to provide a rough position estimate of the all of GPS satellites. These orbits are then propagated in time providing a good estimate of the satellites orbits. This is purely used to generate a moving rough estimate of the GPS constellation for the simulation.

In practice the GPS constellation is closely monitored and each satellite has a new ephemeris updated every 3 hours. In addition to updating their GPS Almanac files every 12 hours.

Since we are only interested in observing those GPS Satellites with a reflected pair and since the relative distance is so small we can assume that any GPS satellite seen by the space Shuttle can also be seen by the Hubble.

The visible signals are done by masking out those GPS satellites whose main lobes cross through the earth or are not in view of the shuttle. This is done by calculating the angle between the line of sight vector and position vector of the shuttle as seen in . If is greater than 13.9 and less than 21.3 then it is within the main lobe and just over the lim of the earth. If is less than 13.9 then we need to check to make sure the signal does not pass through the earth. Thus the dot product of the two vectors should be negative.

This equation is used to determine the maximum range to the target. However rearranging terms it is possible to pose this in the form of SNR received.

There are several universal constants from this particular implementation. is the wavelength of the GPS L1 signal. The GPS L1 signal is transmitted at 1575.42 MHz giving it a wavelength of 0.1903 m. Boltzmann s constant is given by 1.3806503 10J K. Fand Fare the pattern propagation factors these factors describe the loss due to transmission in an unclean environment. Fand Fcan be estimated at around 2 dB total for the ionospheric effects.

The bi static radar cross section is calculated in much the same way as the standard radar cross section. However the transmit angle needs to be taken into account as well as properties limited only to the bi static scenario.

Since the Hubble can be approximated as a cylinder and the approach profile is towards the aft end. The Hubble can approximated by the reflective properties of a circular flat plate combined with a cylindrical surface normal to the flat plate. In physical optics the equation describing the RCS for a metallic circular disk is 

Where A is given as the physical area of the disk d is the diameter and J x is the Bessel function of the first kind of order one. is the wavelength.

This would represent the monostatic cross sectional area of the Hubble space telescope with the observer looking perpendicular to the aft end. Thus the maximum possible cross sectional area looking at the aft end is 36.81 dB sqm. It is interesting to note that the GPS signal will get gain from the reflections. If the observer was oriented perpendicular to Hubble it would appear as a cylinder to the viewer. In this case the RCS is given by 

Where a 2.1 m is the radius l 14.2 m is the length of the Hubble k is the wave number and is the wavelength. This provides a predictable radar cross section. With the assumption since at the extremes of both of these figures the RCS drops off significantly and effectively take the maximum RCS. Of the two plots the side of the cylinder offset by 90 to form a combined RCS model for the cylinder over 180 . Since a cylinder is symmetrical this is effectively models the full cylinder over 360 .

In order to account for the bi static nature of the problem it is necessary to define a new angle called the bi static angle. This angle is defined as the difference between the receive and transmit antennae the bisection of this angle is used to approximate the Bi static RCS . The bi static RCS can be grouped into 3 sections the pseudo monostatic RCS region the forward scatter RCS region and the bi static RCS region. In the pseudo monostatic region the Crispin and Seigal monostatic bi static equivalence theorem predicts that for a sufficiently small angle the RCS is equivalent to the monostatic RCS measured the bisector of the bistatic angle. This theorem applies to a sufficiently smooth surface such as a sphere a cylinder or cone. Some empirical data for a cylinder performed at 35 GHz the pseudo monostatic region extends to roughly 20 while the bistatic is within 20 140 and forward scatter at 140 .

The bi static region begins where the pseudo monostatic region ends it is where the theorem fails to predict an accurate RCS. Unfortunately there is no empirical formula for this equation. Experimental data shows a downward trend from 2 dB to 15 dB in this case. It should suffice to use a linear approximation in dB .

The third bi static region is the forward scattered region this occurs when the bi static angle approaches 180 o . The forward scatter can be approximated by treating the shadow area as a uniformly illuminated antenna aperture. The roll off can be approximated when dot over is substituted for the angle off aperture normal. This function closely matches J x x where J x is the Bessel function of order 0. In our situation many of the GPS satellites will lie in this area due to being below the constellation. This is to our benefit allowing us to pick up signals being at such an odd orientation. Luckily due to the change in polarization of the reflected signal this will provide us with isolation from the direct signal from the satellite.

From these bi static regions we can now form a full approximation for the bi static radar coefficient. The plot below represents with the flat face of the cylinder oriented towards the receiver. This should provide a reasonable fit for a perfectly reflecting disk.

The antennae chosen for this mission are two hemispherical antennas. The antenna gain is given as 3 dBic. Built into each antenna is the low noise amplifier. The LNA has a gain of 26 dB with a noise figure of 2.8. This can be used to calculate the system noise temperature. This equation is given as 10 log 1 

Where Tis the temperature at the antenna. Since the LNA is at the antenna the line losses are included in the analysis. From the spec sheet the NF of the antenna is given as 2.8 dB. A conservative approximation for this noise figure is to use the temperature at the antenna T as room temperature or 290 K. This approximation holds because the antennae are lying on the MULE. The MULE will be heated in order to keep the electronics from freezing. From this equation we find that the receiver noise temperature is 24.4 dB K.

The Land Land receiver and transmit system losses respectively will be taken into account as a total system loss. A general approximation of loss in a communications system is about 2 dB. Usually this value is measured quantitatively but without a complete system to test it is difficult to arrive at a true figure. The noise bandwidth Bis generally taken as 1 T where T is the pre integration period. For Navigator it has an adjustable preintegration period however the nominal case is 1 ms. Other losses occur such as Polarization mismatch contributing 3 dB and in the case of a reflection there is an efficiency which is dependent on the reflectivity of the object. In the case of the Hubble which is coated in mylar it will have a high reflectivity coefficient this is typically 90 98 depending on the quality.

The range calculations Ris simply the geometric distance between the Shuttle and the Hubble while Ris simply the geometric distance between each GPS Satellite and the Hubble. Factoring the free space loss due to range the equations 

At each time step for each visible GPS satellite each range value is calculated. With the assumption that the Shuttle is oriented with its bay doors towards the aft bulkhead of Hubble it is possible to estimate the angle and which surface of the cylinder the reflection is striking. The truth positions were generated from a file that is the simple 2 body relative motion coupled with some thruster firing for a realistic closing profile. This produces an expected satellite visibility given the aforementioned conditions. It should be noted that the model does not take into account the reflections from the solar panels and assumes an orientation with the antennae directly facing the aft bulkhead.

The direct signal is generated using the truth positions of the Shuttle and Hubble. A receiver bias is added on top of the signal as well as the ionospheric error given by the equation

TEC is the total electron content given by 2e17. Fis the carrier frequency 1.57542 GHz and EL is the elevation of the GPS satellite over the horizon.

The direct signal pseudorange rate is generated by the rate of change of the line of sight vectors. In practice most GPS receivers rely only on the pseudorange measurements or use carrier phase to generate the velocities. The pseudorange rate measurements are generally noisy and actually degrade the performance of the filter.

A variance of 5 meters was chosen for the direct pseudo ranges and 25 cm s for the pseudo range rates. It is composed of the clock drift ephemeris errors phase noise and other unmodeled sources. The ionospheric bias was neglected in this simulation as it would have been differenced out in the measurement generation. The pseudo range variance may be increased by a nominal amount 0.25 m to reflect the ionospheric model discrepancies.

The differenced reflected measurements were constructed from the total path lengths between the GPS Satellite Hubble and the Shuttle. The noise added is from the loss in signal quality due to the reflective properties and small ionospheric error. Since the measurement is a differenced reflected signal with that of the direct path the bias and the ionospheric terms become small and are negligible. In addition to the ionospheric error practically canceling out the front end bias clock bias thermal jitter and other common mode errors also disappear.

A variance of 25 meters was chosen for the reflected pseudo ranges and 50 cm s for pseudo range rates. Although the true variance is unknown it is extremely difficult to model on the earth. Future tests will include an anechoic chamber testing or data reduction of the rendezvous experiment.

While the method and apparatus of the present invention has yet to be tested oil a service mission simulations have proven the viability and utility of the use of comparing reflected and directly received GPS signals to passively navigate spacecraft to an orbiting target. The present invention is currently scheduled to fly in August 2008 on Hubble Servicing Mission 4. A further discussion of such simulations can be found in Ian Cohen s thesis entitled Relative Navigation for Hubble Mission Using Reflected GPS signals published by the University of Maryland in May 2007 and is hereby incorporated herein by reference in its entirety.

One additional use of the method of using reflected GPS signals as a passive navigation system is to compliment existing navigation tools. This passive system can not only provide an extra measurement tool offering additional redundancy it could also be used to navigate a space craft to within sufficient proximity of an orbiting target reducing the amount of time active systems such as LIDAR and RADAR are powered. Because this method and system of the present invention may be employed by simply adding the second LHCP antenna and loading the algorithmic complexity onto existing systems redundancy and reduced power consumption can be achieved with little modifications to existing equipment.

The foregoing description of the specific embodiments will so fully reveal the general nature of the invention that others can by applying current knowledge readily modify and or adapt for various applications such specific embodiments without departing from the generic concept and therefore such adaptations and modifications should and are intended to be comprehended within the meaning and range of equivalents of the disclosed embodiments. It is to be understood that the phraseology or terminology employed herein is for the purpose of description and not of limitation. Therefore while the embodiments of the invention have been described in terms of preferred embodiments those skilled in the art will recognize that the embodiments of the invention can be practiced with modification within the spirit and scope of the appended claims.

