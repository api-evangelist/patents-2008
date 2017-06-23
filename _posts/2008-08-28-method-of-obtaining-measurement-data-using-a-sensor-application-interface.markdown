---

title: Method of obtaining measurement data using a sensor application interface
abstract: A method involves, via a sensor application interface, 1) receiving, from an application, a measurement request associated with a quality-of-service control; 2) in accord with the quality-of-service control, obtaining measurement data from a sensor; and 3) returning to the application i) the measurement data obtained from the sensor, and ii) an indicator of accuracy of the measurement data.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08285504&OS=08285504&RS=08285504
owner: QUALCOMM Incorporated
number: 08285504
owner_city: San Diego
owner_country: US
publication_date: 20080828
---
The present Application for Patent claims priority to U.S. patent application Ser. No. 11 688 824 entitled Method Of Obtaining Measurement Data Using A Sensor Application Interface filed Mar. 20 2007 which claims priority to Provisional Patent Application No. 60 784 608 entitled Sensor Application Interface filed Mar. 20 2006 assigned to the assignee hereof and hereby expressly incorporated by reference herein.

There are many sensors on the market today. These sensors are designed to convert a physical phenomenon into an electrical signal. For example 

Accelerometers are the most widely used MEMS sensors with millions integrated into cars by the automotive industry. As said above the linear accelerometers can sense the linear motion and can provide a measure of tilt. With a 3D accelerometer motion in x y z can be sensed. In addition the direction of the gravity can be used to estimate the roll and pitch see .

Unfortunately in wide number of cases it is difficult to differentiate between a linear motion acceleration in x y z and the change in the orientation of the device and the corresponding change in roll and pitch. Furthermore a change in the heading aka yaw or azimuth can not be sensed by the linear accelerometers at all. For sensing the change in the heading gyroscopes are commonly used. However gyroscopes are expensive large and complex structures and therefore more expensive than accelerometers.

What is needed is a solution which can reliably deliver a measure of linear motion and orientation. This invention discloses a method of integrating two 3D linear accelerometers in order to measure and provide 6D information x y z see . Since accelerometers deliver second momentum the measurements need to be integrated once to get the rate of change and second time to get the absolute measures.

Two 3D accelerometers deployed at opposite corners of the board can sense the linear movement sensors produce similar outputs see and sense orientation changes sensors produce opposing outputs see .

In order to be able to efficiently use sensors in various applications a sensor must provide several functions control capability measurement output and quality control.

An application programming interface API is defined which in addition to the control and common measurement output interface adds a quality control. The quality control has a bi directional purpose. For example on the input quality of service QoS control allows the sensor user application developer to prioritize the time per measurement vs. accuracy of the sensor measurement it can specify how often the measurement is performed periodic and the duration of measurement period define the event triggering the sensor measurement threshold level for sensor output to trigger the measurement processing length of measurement filtering time constant etc. The sensor QoS will add the accuracy measures to the raw measurement values directional information accuracy tilt accuracy acceleration accuracy rate of rotation accuracy pressure accuracy temperature accuracy etc. It can also add specific event outputs such as shock detected e.g. acceleration magnitude above 1000 g was detected etc.

The availability of sensor QoS control functionality facilitates sensor integration and allows successful integration of the measurements from multiple sensors for various applications utilizing sensor measurements.

The previous description of the disclosed embodiments is provided to enable any person skilled in the art to make or use the present invention. Various modifications to these embodiments will be readily apparent to those skilled in the art and the generic principles defined herein may be applied to other embodiments without departing from the spirit or scope of the invention. Thus the present invention is not intended to be limited to the embodiments shown herein but is to be accorded the widest scope consistent with the principles and novel features disclosed herein.

