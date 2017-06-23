---

title: Hybrid pressure and vector sensor towed array
abstract: The invention as disclosed is of a combined acoustic pressure and acoustic vector sensor array, where multiple acoustic pressure sensors are integrated with an acoustic vector sensor in a towed array as a means of resolving the left-right ambiguity of the multiple acoustic pressure sensors.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07599253&OS=07599253&RS=07599253
owner: The United States of America as represented by the Secretary of the Navy
number: 07599253
owner_city: Washington
owner_country: US
publication_date: 20080724
---
The invention described herein may be manufactured and used by or for the Government of the United States of America for governmental purposes without the payment of any royalties thereon or therefore.

The present invention is directed to underwater acoustic sensors. In particular the present invention is directed to hydrophones in towed arrays for use with underwater vehicles.

Underwater vehicles currently utilize n element towed arrays of acoustic pressure hydrophone sensors. Each hydrophone in the towed array has an omni directional acoustic beam response. When a hydrophone towed array is designed the linear array demonstrates an axial symmetric beam pattern. Because of this axial symmetric response a target signal coming from either the left or the right has the same array response. The inability to distinguish between a left or right array response is referred to as the left right ambiguity . An n element towed array beam pattern is shown in where the towed direction is along the x axis and the y axis is at the starboard direction and z axis is upward.

An acoustic vector sensor either particle velocity sensor or accelerometer sensor detects the acoustic information from sound wave particle velocity or acceleration. A single acoustic vector sensor demonstrates a cosine beam pattern independent of the sound wave frequency. To resolve the left right ambiguity one could form a vector sensor towed array where all hydrophone elements of the towed array are replaced by vector sensors or combined pressure vector sensors. However this approach introduces a higher level of complexity in regard to the design and operation of the towed array. In order to have a successful working array made of all combined vector sensors the three dimensional orientations for each vector sensor in the array must be known. Instead of forming an n element vector sensor towed array what is needed is a means to resolve the left right ambiguity in towed arrays of hydrophone sensors through the use of a single combined pressure vector sensor package where a pressure hydrophone sensor is integrated with an acoustic vector sensor.

It is a general purpose and object of the present invention to resolve the left right ambiguity in towed arrays of hydrophone sensors by hybrid technique.

The above object is accomplished with the present invention through the use of a combined pressure vector sensor package where a pressure hydrophone sensor is integrated with an acoustic vector sensor of tri axes.

The towed array design of the present invention is a hybrid towed array where only one element is a combined vector sensor and the rest are all hydrophone sensors. illustrates an example of a hybrid linear towed array of n sensor elements where one of the sensor elements is a combined vector sensor located at the acoustic center of the array while the other n elements are pressure sensors i.e. hydrophones distributed throughout the array.

Within the hybrid towed array the n element pressure sensor array shows a beam pattern D similar to the beam pattern illustrated in based on the following equation where i is square root over 1 is the bearing and is elevation and depression angles respectively and p is a normalization constant which equals to the maximum of p for all and 

where w w w and are weighting coefficients for the hydrophone and tri axial vector sensor respectively. The tri axial vector sensor will provide beam patterns on all three axis x direction y direction and z direction. shows an x direction oriented vector sensor beam pattern D in a two dimensional and contour plot where w 1 and w w w 0. shows a single slice at equals zero degree beam pattern from D in a polar plot for the x direction vector sensor. shows a y direction oriented vector sensor beam pattern D in a two dimensional and contour plot where w 1 and w w w 0. shows a single slice at equals zero degree beam pattern from D in a polar plot for the y direction vector sensor. shows a combined hydrophone and y direction oriented vector sensor beam pattern D in a two dimensional and contour plot where w w and w w 0. shows a single slice at equals zero degree beam pattern from D in a polar plot for the combined hydrophone and y direction vector sensor where w w and w w 0.

A multiplication operation in signal processing for the n elements of pressure sensors and the combined vector sensor provides the new hybrid towed array beam pattern based on the following equation 

The advantage of the present invention is that it resolves the left right ambiguity for conventional towed arrays of hydrophone sensors without a complete redesign and fabrication of the towed array. Instead of implementing an entirely new towed array of n element tri axial orientation sensitive vector sensors and processing the signals in three dimensions the design of the present invention only implements a single vector sensor with know orientation into the existing towed array of pressure sensors because the sensor signal from a single vector sensor is sufficient to resolve the left right ambiguity. This greatly reduces the fabrication difficulties system complexity data processing and cost involved in resolving the left right ambiguity in prior art towed arrays of pressure sensors.

While it is apparent that the illustrative embodiments of the invention disclosed herein fulfill the objectives of the present invention it is appreciated that numerous modifications and other embodiments may be devised by those skilled in the art. Additionally feature s and or element s from any embodiment may be used singly or in combination with other embodiment s . Therefore it will be understood that the appended claims are intended to cover all such modifications and embodiments which would come within the spirit and scope of the present invention.

