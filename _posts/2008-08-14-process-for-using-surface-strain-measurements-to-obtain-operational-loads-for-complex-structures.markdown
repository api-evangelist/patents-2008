---

title: Process for using surface strain measurements to obtain operational loads for complex structures
abstract: The invention is an improved process for using surface strain data to obtain real-time, operational loads data for complex structures that significantly reduces the time and cost versus current methods.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07715994&OS=07715994&RS=07715994
owner: The United States of America as represented by the National Aeronautics and Space Administration
number: 07715994
owner_city: Washington
owner_country: US
publication_date: 20080814
---
The invention described herein may be manufactured and used by or for the Government of the United States of America for governmental purposes without payment of any royalties thereon or therefor.

The present invention relates generally to processes to obtain externally applied out of plane operational load data using surface in plane strain measurements on complex structures particularly to real time methods to calculate operational loads for complex structures and most particularly an ultra efficient process of calculating externally applied bending and torsional operational loads in real time on complex structures using strain measurements provided by fiber Bragg grating technology.

An important by product of this process is the efficient characterization of out of plane bending and torsional stiffness material properties of the complex structure.

Currently to obtain operational load data for complex structures industry uses a very rigorous and time consuming design methodology that relies heavily on computational methods such as finite element modeling FEM . FEM requires that the structure to be designed analyzed be analytically discretized into very small linear elements. Realistic structures are geometrically complex as are the loads they are exposed to and the boundary conditions that restrain them. Therefore a considerable amount of effort is required to accurately model the structural response of these realistic structures in the loading environment for which they are expected to perform. An extraordinary amount of knowledge of the structural design details is required a priori eg. all the local material and geometric properties of the structure how the skins attach to the spars what the load paths are the nonlinearity of the joined regions how the composite design differs from the as built structure etc . In addition the models are also only as accurate as the material properties assumed in the analysis. These material properties are usually derived from small 1 in 10 in uniaxial coupon tests the results of which are assumed to be appropriate for the three dimensional structure. The development of FEM models is extremely labor intensive and requires costly experimental validation to ensure that the models accurately reflect reality.

More specifically for real time loads associated with aircraft wings the methodology used today relies upon conducting a fairly extensive strain gage loads calibration. This method is built upon technology developed in the 1950s and first involves the installation of a sparsely distributed number of conventional strain gage sensors located on the inside of the wing structure. An extensive series of tests are then required to apply a matrix of independent concentrated loads to the wing surface to calibrate the strain gage response to each particular load applied called influence coefficients. Software is then used to derive loads equations that can be used in real time using the strain gage measurements as input. The drawback to this method is that it involves a considerable amount of labor and cost to perform these strain gage loads calibrations from installing strain gage instrumentation to designing and fabricating load system hardware to assembling the test setup to conducting the tests to reducing the data and deriving the loads equations. A fairly elaborate loading system is required to be designed fabricated and assembled in order to conduct the tests.

Due to the shortcomings of the current real time operational loads analysis discussed above it is desired to provide an improved real time method to calculate operational load data for complex structures and more particularly aircraft wings that significantly reduces time and cost.

The invention is an improved process for using in plane surface strain data to obtain real time externally applied out of plane operational bending and torsional loads data for complex structures that significantly reduces the time and cost versus current methods.

Accordingly it is an objective of this invention to provide real time externally applied out of plane operational loads data bending and torsion for complex structures.

It is another objective of this invention to reduce the time necessary to obtain real time externally applied out of plane operational loads data bending and torsion for complex structures.

It is a further objective of this invention to reduce the cost associated with obtaining real time operational loads bending and torsion for complex structures.

This invention meets these and other objectives related to determining the real time operational loads on complex structures by providing an improved method of obtaining said data that significantly reduces the cost and time associated with the current analysis.

In general the invention comprises installing a very fine spatially refined grid of fiber optic sensors on the complex structure to be analyzed. For bending a single point load is externally applied to the complex structure at the free end to obtain the bending properties of the complex structure to the as built design. Similarly a single force couple moment is applied at the free end of the structure to obtain torsional structural properties of the complex structure. Because the local bending and torsional stiffness properties of the complex structure can be to determined at every fiber optic sensor location the output provides similar spatial resolution to that obtained from the more cumbersome labor intensive and costly FEM. All local bending and torsional properties of the complex structure are then input into computationally efficient highly simplified and accurate analysis methods to accurately capture the real physical response of the structure without the need for apriori knowledge of the structural details of the complex structure. Finally the computationally efficient and highly simplified analysis methods are employed during real time loading of the complex structure in order to obtain real time operational loading data.

This process provides several benefits compared to the current methods described above. First the complexity of the FEM can be reduced. And second a reduced number of degrees of freedom are required in this method. These benefits dramatically reduce the time money required to accomplish the structural analysis and increase the accuracy of the simplified structural models employed.

The present invention is an improved method of using strain data in order to obtain operational loads on complex structures. In general a plurality of fiber optic sensors are placed on a complex structure preferably in a grid type regular pattern. By using fiber optic sensors a large number of sensors may be employed due to the small size and weight of the sensors. The sensors in essence divide the complex structure into a plurality of sections. The present invention assumes that each of these sections which are defined herein as the area from one adjacent fiber optic sensor to another has a consistent structural behavior within each section but the structural behavior may be different in different sections. Because the strain is measured at both edges of each section the section lengths can either be selected to be the same or may vary.

After the fiber optic sensors are installed upon the complex structure bending and torsional loads can be determined as follows. For the bending load a single externally applied point load with a known force is applied to the complex structure normal to the structure s primary axis. Similarly for torsional loads a single force couple moment at the free end of the structure with a known magnitude is applied to the complex structure. The strain is measured at each fiber optic sensor location and due to the above discretization of the complex structure into a plurality of sections closed form analytical solutions for non uniform cantilevered beams may be employed to obtain the bending and torsional structural properties of the cross section of each segment and hence the structural properties of the overall complex structure. This part of the method of the present invention obviates the need to complete extremely difficult and rigorous finite element modeling of the complex structure.

Next the complex structure is subjected to operational loading. The light weight and small size of the fiber optic sensors allows for operational loading without significant variance due to sensor equipment. From the structural property information for each section and the strain data obtained from the sensors during operational loading the bending moment shear and loads at each section may be calculated at various time intervals selected by the user.

A more detailed description of the method of the present invention follows for the bending load. An analogous description can also be shown for the torsional load. As an example of the method for determining bending load the basic displacement equations will be developed for a complex structure comprising a uniform cantilever beam with constant cross sectional properties. The method is built upon the classical bending equation for the uniform beam

where y is the vertical displacement x is the span wise coordinate M x is the bending moment E is the Young s modulus or elastic modulus and I is the moment of inertia. Equation 1 can be re written for the non uniform beam as

where x is the strain c x is the distance from a strain sensor on the surface of the structure to the neutral axis which is the half depth for symmetric sections both expressed as functions of the span wise coordinate x.

Referring to the spatial domain of the complex structure is discretized by dividing the structure into sections with strain sensing stations i 0 1 2 3 . . . n installed at section junctures x x e.g. station i 0 at x x 0 and station i n at x x 1.

Using a simple structure of length l and half depth c x the sections are defined to be l l n distances apart.

The first step in the invention is to install a plurality of fiber optic strain sensors on the complex structure surface in such a way as to measure bending strains at desired locations. In a preferred embodiment of the invention the fiber optic strain sensors are Fiber Bragg Grating FBG sensors. These sensors are preferred because they are minimally obtrusive ultra lightweight easily installed accurate immune to EMI and inherently safe no joule heating sparking . The most preferred configuration and use of FBG sensors for the present invention employ the Optical Frequency Domain Reflectometry OFDR technique with hardware architecture described in U.S. Pat. Nos. 5 798 521 and 6 566 648 which are incorporated herein by reference. This approach uses low reflectivity gratings all with the same center wavelength and a tunable laser source. The FBGs are preferably located on a single optical fiber. This allows hundreds of strain sensors to be located down the length of the fiber a common configuration is to use 480 FBGs on a single 20 ft optical fiber spaced at 1 FBG cm. This configuration allows strain measurements to be acquired at much higher spatial resolution than other current sensor technologies making it flexible enough to employ a user selected grating density depending on the type of application.

The number and spacing of the fiber optic sensors depend upon the overall length of the complex structure as well as the expected variance of the structural properties of the complex structure and may be selected by one skilled in the art. As an example for an aircraft wing a user may employ a fiber optic sensor about every half inch.

Referring to the next step is to perform a simple test calibration via a single point load of a known force. For a beam of length l discretized into xsections each with section lengths of l and subjected to a tip load of P that places the beam in bending the flexural rigidity of the beam can be experimentally determined at each measurement location i. Substituting M P l l and solving for bending stiffness EI equation 3 becomes 

The product of elastic and section modulus in equation 5 can be determined by calibration at every cross section by the formula

In order to obtain operational loads data for the complex structure is measured while the structure is in operation preferably with the same sensors used during calibration and ES in equation 6 has been determined via a single point calibration then the bending moment at each station M can then be determined for any general set of loads applied during operation. Equation 3 becomes

From the equilibrium of moments the shear loads. V at each x can then be determined using the following equation

The following examples are provided to further illustrate the present invention note that the following examples employ finite element analysis in place of experimental results to further demonstrate the invention . Referring to a cantilever beam with constant cross section length l 160 in. and subjected to a concentrated tip load P of 1000 lb. is depicted.

Table 1 below shows the results at each station i obtained from a finite element analysis FEA and those calculated using the method of the present invention. FEA results are being used in place of the experimental strains to demonstrate the method of the present invention. The table shows excellent comparison between the flexural rigidity EI calculated from the following equation

The value obtained from the example analytical calibration above is then used along with the strains from FEA to determine the structure s moment shear and applied loads from equations 8 10 and 11 respectively.

Table 1 further shows that the moment from equation 8 compares well with those computed from M P l x P l i x P l i l .

Table 1 also shows that the shear from equation 10 and the loads from equation 11 compares well with those from statics.

Referring to a cantilever beam with a tapered cross section length l 160 in. and subjected to a tip load P of 1000 lb. is depicted.

Table 2 below shows the results at each station i obtained from the finite element analysis FEA and those calculated using the present invention. The table shows excellent comparison between the flexural rigidity EI calculated from the following equation

The value obtained from the analytical calibration above is then used along with the strains from FEA to determine the structure s moment shear and applied loads from equations 8 10 and 11 respectively.

Table 2 also shows that the shear from equation 10 and the loads from equation 11 compares well with those from statics.

Referring to a cantilever beam with a constant with constant cross section length l 160 in. and subjected to a distributed load P of 800 lb. is depicted.

The value obtained from the analytical calibration in Table 1 is then used along with the strains from FEA to determine the structure s moment shear and applied loads from equations 8 10 and 11 respectively. Table 3 shows that the loads from equation 11 compares well with the applied as shown in .

Referring to a cantilever beam with a tapered cross section length l 160 in. and subjected to a distributed load of 800 lb. is depicted. The value obtained from the analytical calibration in Table 2 is then used along with the strains from FEA to determine the structure s moment shear and applied loads from equations 8 10 and 11 respectively.

What is described are specific examples of many possible variations on the same invention and are not intended in a limiting sense. The claimed invention can be practiced using other variations not specifically described above.

