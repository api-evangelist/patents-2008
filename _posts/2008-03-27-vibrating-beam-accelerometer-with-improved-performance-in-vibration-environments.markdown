---

title: Vibrating beam accelerometer with improved performance in vibration environments
abstract: An accelerometer that has a cross coupling coefficient due to pendulum droop of the proof mass that is approximately equal and opposite in sign to a cross coupling coefficient due to resonator nonlinearity. The accelerometer includes a proof mass, a housing having at least two opposing interior walls, and one or more flexures for flexibly connecting the proof mass at a first end to a first one of the opposing walls of the housing. A first resonator is connected to a first surface of the proof mass at an end of the proof mass opposite the first end and to the housing wall that is not attached to the flexure. A second resonator is connected to a second surface of the proof mass and the housing wall that receives the first resonator. The second surface is on an opposite side of the proof mass as the first surface.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08117917&OS=08117917&RS=08117917
owner: Honeywell International Inc.
number: 08117917
owner_city: Morristown
owner_country: US
publication_date: 20080327
---
The invention described herein was made in the performance of work under U.S. Government Contract No. FA9453 05 C 0241. The Government Agency is Air Force Research Laboratories AFRL . The Government may have rights to portions of this invention.

Accelerometers used in guidance navigation and control systems have to meet performance specifications in spite of structural and acoustic vibration environments. These systems typically output accelerometer values at relatively slow data rates on the order of 100 Hz and slower. This is sufficient for aircraft navigation or missile guidance and control. Structural and acoustic vibrations on the other hand are typically much higher in the 100 to 100 000 Hz range.

The average output from an accelerometer taken over enough samples would ideally be zero in a vibration environment as described above. The vibration environment being equally positive and negative in direction with an average acceleration of zero and no net change in velocity.

However real accelerometers do not respond identically to positive and negative accelerations. That is their output is not perfectly linear over the and range. As a result their average output does not average to zero under vibration. Instead they suffer a bias offset in vibration an error that is referred to as vibration rectification error or VRE. VRE is typically a significant problem for precision accelerometers in guidance navigation and control systems.

One source of accelerometer nonlinearity contributing to VRE is called cross coupling sensitivity. This refers to changes in the primary input axis sensitivity of the accelerometers as a function of cross axis accelerations. In particular the cross coupling coefficient K input axis sensitivity coupling with pendulous axis input can be very large and contributes significantly to nonlinearity and to VRE.

In pendulous vibrating beam accelerometers the cross coupling coefficient Kcomes from two sources. First the pendulum displaces under acceleration causing the center of mass to move with respect to the supporting flexures or pivot. This causes a change in pendulous axis sensitivity which then by definition is a cross coupling sensitivity K. This source for Kis typically referred to as pendulum droop.

A second source for Kis from the nonlinear force frequency relationship in the vibrating beam force sensor. The terms vibrating beam force sensor force sensor and resonator are used interchangeably . Because of this nonlinearity input axis accelerations change pendulous axis sensitivity and vice versa resulting in Kby definition.

1 Droop Kis positive. That is for positive accelerations along an input axis the angular droop of the pendulum will increase the sensitivity along a pendulous axis .

2 Vibrating beam Kis also positive. That is for positive accelerations along the pendulous axis both resonators go into compression which by the nonlinear force frequency relationship of the resonator will increase the input axis sensitivity.

In summary Knonlinearity results in accelerometer bias errors in vibration environments VRE . Kin vibrating beam pendulous axis accelerometers is driven both by pendulum droop and by the nonlinear force frequency behavior of the vibrating beam force sensor.

The present invention provides an accelerometer that has a cross coupling coefficient due to pendulum droop of the proof mass that is approximately equal and opposite in sign to a cross coupling coefficient due to resonator nonlinearity.

The accelerometer includes a proof mass a housing having at least two opposing interior walls and one or more flexures for flexibly connecting the proof mass at a first end to a first one of the opposing walls of the housing. A first resonator is connected to a first surface of the proof mass at an end of the proof mass opposite the first end and to the housing wall that is not attached to the flexure. A second resonator is connected to a second surface of the proof mass and the housing wall that receives the first resonator. The second surface is on an opposite side of the proof mass as the first surface.

This invention eliminates or reduces the cross coupling coefficient Kto reduce VRE and improve accelerometer performance in vibration environments.

This invention solves the above problem by canceling pendulum droop Kwith Kfrom the vibrating beam force frequency nonlinearity. These two sources for Kare made to be opposite in sign by this invention and or to be exactly equal and opposite to substantially cancel one another.

This invention is unique from prior art in the orientation of the vibrating beam force sensors relative to the pendulous proof mass and unique in the specific sizing of the proof mass and flexure support system relative to the vibrating beam force sensors. The orientation allows for the droop Kto be opposite in sign from the vibrating beam K. The sizing relationship allows the two error terms to exactly cancel.

2 Positive accelerations motion of housing to right on page along the pendulous axis puts both resonators into tension and by the nonlinear force frequency relationship of the resonator will decrease the input axis sensitivity resulting in a negative K.

In order for the two Kerrors to exactly cancel the following design relationships must be maintained in addition to orienting the resonators as described above 

1 Kfrom pendulum droop is calculated as the angular displacement of the proof mass center of gravity relative to the flexure hinge center of rotation for 1 G input axis acceleration and

2 Kfrom resonator nonlinearity is calculated by K 2KK where Kand Kare for individual resonators and Kis the pendulous axis sensitivity and Kis the second order input axis sensitivity.

3 The above calculations are made by structural analysis methods typically involving finite element analysis or other suitable methods.

The design is adjusted until the two Kip error sources are equal and opposite in sign so as to cancel one another.

Equation 1 is a polynomial approximation of resonator frequency vs. force. Fis axial force on resonator. aand aare functions of the resonator geometry and material properties. 2 2 3 

Bis a function of proof mass and hinge geometry and material properties. Brelates accelerations along the input axis A to resonator force with units for example of Newtons per G. For example in through the diameter of is 1.7 inches and the thickness is 0.25 inches. The flexures are 0.050 inches by 0.020 inches by 0.003 inches thick. In this case Bi is approximately 0.1 Newtons per G.

Equation 11 is polynomial approximation of resonator frequency vs. force. The second order terms are not necessary to show cross coupling from pendulum droop.

Fis axial force on resonator. ais a function of the force resonator geometry and material properties. 12 

Bis a function of proof mass and hinge geometry and material properties. Brelates accelerations along the input axis A to resonator force.

The B s are functions of the proof mass geometry and material properties. The a s are functions for the resonator geometry and material properties. These are best determined using finite element analysis or other methods of mechanical analysis.

While the preferred embodiment of the invention has been illustrated and described as noted above many changes can be made without departing from the spirit and scope of the invention. Accordingly the scope of the invention is not limited by the disclosure of the preferred embodiment. Instead the invention should be determined entirely by reference to the claims that follow.

