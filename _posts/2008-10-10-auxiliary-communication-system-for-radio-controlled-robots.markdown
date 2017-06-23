---

title: Auxiliary communication system for radio controlled robots
abstract: A system for providing autonomous capabilities to a radio-controlled robot, comprises two communication boxes, one connected to the robot and the other connected to an operator control unit (OCU). Each communication box comprises two radios that are interoperable with preexisting data radios in the robot; a microprocessor unit; and bidirectional attenuators. The system further comprises a software application that runs on the microprocessor unit of each communications box, to integrate data into existing transmission data stream between the robot and OCU, via preexisting data radios. The system enables the issuance of additional commands besides those issued by the OCU, using the original OCU.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08326461&OS=08326461&RS=08326461
owner: The United States of America as represented by the Secretary of the Army
number: 08326461
owner_city: Washington
owner_country: US
publication_date: 20081010
---
The inventions described herein may be manufactured used and licensed by or for the U.S. Government for U.S. Government purposes.

The present invention generally relates to the field of telecommunications and in particular to a system for providing autonomous capabilities to a radio controlled tele operated robot.

Conventional types of remote controllable robots are linked with operator control units OCUs . An OCU is programmed to perform only certain applications and to transmit data associated therewith. In the event additional functionality is desired a robotic applications developer who wants to add commands or sensor data to the data stream has two main options.

According to a first option the additional information is piggy backed on the existing data stream. For example the developer could insert his her data in the slot reserved for the GPS signal. However this approach has two significant drawbacks 1 It removes some functionality from the robot e.g. the capability of sending GPS information and 2 the user is very limited in the data rate and data format of the data he she sends since it must conform to the format that the robot is expecting for that slot in the data stream.

According to a second option the data is sent over a medium other than the radio signal. For example a module could be placed on the robot to give it autonomous capabilities and the commands sent from this module to the robot s drive arm and gripper motors could be sent to the robot via the robot s fiber optic or wire tether port. However the robot will in general not be able to communicate concurrently via two different media such as radio and wire tether. Therefore while the autonomy module is operating the robot operator cannot communicate with the robot via the radio link. In order to restore radio communication capability the operator would have to turn off the autonomy module and re establish the radio communication link. Thus this type of data integration also removes significant functionality from the robot i.e. it disables radio communication.

What is therefore needed is a communication system capable of transmitting data to a robot without removing functionality from the robot. The communication system should be operable to insert additional data into a preexisting data stream without excessively slowing the overall data rate of the OCU robot communication link. The communication system should also be capable of transmitting the data in a user selectable data format. The need for such a system has heretofore remained unsatisfied.

The present invention satisfies this need and presents a communication system for providing autonomous capabilities to a radio controlled robot that is capable of performing desired functions while effecting little or no impact on the preexisting data transmission system of the robot.

According to a first embodiment of the present invention the present system comprises two communication boxes. A first communication box is connected to the robot and a second communication box is connected to an operator control unit OCU .

Each communication box comprises two radios that are interoperable with preexisting data radios in the robot a microprocessor unit and bidirectional attenuators. The present communication system further comprises a software application that is executed on the microprocessor unit of each communications box to integrate data into existing transmission data stream between the robot and OCU via preexisting data radios.

The system enables the issuance of additional commands besides those issued by the OCU using the original OCU. For example payloads mounted on the robot can be controlled via an extraneous command interface on the OCU. Autonomous processes carried out by the robot can further be initiated via this command interface. Furthermore data from sensors disposed on the robot can be received by an interface on the original OCU.

In the present exemplary embodiment of the robot is illustrated to include a chassis to which the robot communication box A is secured. The chassis is a simplified representation of the electronic electrical optical and mechanical components of an existing robot . The robot further includes a data antenna which is disposed in communication with the robot chassis by means of a data antenna cable and the robot communication box A at a data cable antenna attachment point .

According to the present invention the robot communication box A is readily interposed along the data antenna cable between the data antenna and the data cable antenna attachment point . The connection of the robot communication box A to the robot is external and does not require any other modification to the robot other than possibly having to reprogram some radio settings in the robot data radio Data Radio depending on the type of radio the robot uses. As a result the robot communication box A could be readily and conveniently added in the field by non technical personnel. Also present in the robot communications box is an additional antenna to assist in communications between the OCU and the robot communications box as may be needed.

According to one embodiment of the present invention the OCU communication box B is readily interposed along the data antenna cable between the data antenna and the data cable antenna attachment point . The connection of the OCU communication box B to the processing unit is external and does not require any modification to the processing unit other than possibly having to reprogram some radio settings in the OCU data radio Data Radio depending on the type of radio the robot uses. As a result the OCU communication box B could be readily and conveniently added in the field by non technical personnel.

In one exemplary preferred embodiment of the present invention the communication system is operable to transmit data from sensors mounted on the robot back to the OCU via the robot existing data signals. As used herein existing data signals mean the original data signals that existed or would have existed before the incorporation of the present communication system . At the OCU the sensor data that is sent via the communication system is extracted from the received data stream by means of a software application or program product in such a manner as to enable the display of such sensor data to the user as desired.

In another exemplary preferred embodiment of the present invention the communication system is operable to transmit commands from an extraneous command interface that is external to the OCU to a payload disposed on the robot . At the robot the extraneous commands that are sent via the communication system are extracted from the data stream by means of a software application or program product and sent to the payload for the implementation of the command.

In yet another exemplary preferred embodiment of the present invention the communication system is operable to receive data from the sensors that are disposed on the robot and using the software application issues commands to the robot to enable it to function in an autonomous manner.

In the exemplary embodiment of the robot of the robot is provided with one or more sensors such as those used to detect information about the robots environment. The sensors may be added to the robot by attaching them externally to the robot chassis in communication with the robot communication box A. Data from the sensors is communicated to the robot microprocessor unit .

In turn the robot microprocessor unit integrates the sensor data SD into the proper location in the VSI data stream via the software program product . The decoded VSI with the sensor data is then sent to data radio within the robot communication box A for encoding and transmission via the robot data antenna to the OCU communication box B.

The decoded VSI is concurrently sent to a data radio within the OCU communication box B for encoding and transmission to the OCU . A bidirectional attenuator is disposed in communication between a data radio within the OCU communication box B and a data radio within the OCU to prevent a strong signal from entering the data radio . Data radio which is the data radio inside the OCU receives the VSI unchanged as it normally would have received the VSI without the communication system .

Another feature of the present invention is the ability to transmit extraneous commands to the robot from the OCU . Such transmission is performed in the following sequence 

Data radio which is the data radio within the OCU normally sends OCU commands OCUC from the OCU to the robot . Data radio normally encodes and or modulates this data in preparation for sending it as a radio signal.

This encoded OCUC is sent to data radio via the bidirectional attenuator which prevents a strong signal from entering data radio .

The OCU microprocessor unit passes the decoded OCUC along with the extraneous commands EC to the data radio of the OCU communication box B for encoding and transmission to the robot .

The encoded OCUC and EC are received by the robot data antenna and data radio of the robot communication box A .

The robot microprocessor unit extracts the EC from the command string en route to the robot and sends them to the payload or payloads on the robot .

Within the robot microprocessor unit autonomy commands for the robot can be integrated into the data stream of OCUC. In particular an autonomy module within the robot microprocessor unit is used with the robot to perform at least some or all of the following exemplary types of functions 

The sensors that are used by the autonomy module of the robot communication box A could be mounted on the robot for transmitting their data to the robot microprocessor unit . Decoded VSI are also sent to the robot microprocessor unit as described earlier. The robot microprocessor unit then selectively extracts data of the VSI that are of interest for the autonomy calculations such as the robot s GPS coordinates or a robot arm encoder data and sends the extracted data of the VSI to an autonomy calculator within the robot microprocessor unit .

In turn the autonomy calculator combines the sensor data and the VSI and calculates trajectories for various robot parts or components. It also determines which commands to send to the robot to make it implement these trajectories. The autonomy calculator then integrates these commands into the data stream of OCUC coming from the OCU.

The OCUC with any autonomy commands AC are sent to data radio of the robot communication box A for encoding. The encoded data stream is then sent via a bidirectional attenuator to data radio within the robot . Data radio receives the OCUC and autonomy commands and sends them to an internal microprocessing unit within the robot for routing to the various parts of the robot .

As indicated earlier the communication system comprises two software program products and that enable the communication system to insert command transmit data within an existing data stream without disrupting the existing data stream remove the data from the existing data stream and decode the data so as to determine and institute the command data. The high level flow diagrams illustrated in illustrate the functional steps taken by the software program products and for enabling the implementation of the afore mentioned features.

The initiation of the autonomous processes is implemented similarly to the extraneous commands explained earlier i.e. via the extraneous command Interface that is disposed on or in communication with the OCU .

Controlling the execution of the autonomous process is done by the autonomy calculator which is a software program contained or integrated in the robot microprocessor unit within the robot communication box A that is mounted on the robot . The software process that the autonomy calculator performs is outlined in .

The data insertion into and extraction from an existing data stream by the present invention will now be described in more detail with respect to .

With reference to the process of the OCU microprocessor unit starts at step by receiving the formatted sensor data that is sent to the OCU at step over data radio and by extracting the sensor data from the VSI. At step the OCU microprocessor unit formats the sensor data that was extracted at step in a predetermined manner that is required by the sensor data display user interface . Thereafter at step the OCU microprocessor unit sends the formatted sensor data to the sensor data display user interface .

With reference to the process of the OCU microprocessor unit acquires the extraneous commands from the extraneous command interface at step . It then formats the acquired extraneous commands at step for example by means of an analog to digital conversion or JAUS format. Thereafter at step the OCU microprocessor unit inserts the formatted extraneous commands into an OCU command string and sends it to the robot via data radio .

With reference to the process of the robot microprocessor unit starts at step by receiving the formatted extraneous commands that is sent from the OCU at step over data radio and by extracting the extraneous commands from the command string. At step the robot microprocessor unit formats the extraneous commands that were extracted at step in a predetermined manner that is required by the payload . Thereafter at step the robot microprocessor unit sends the formatted extraneous commands to the payload .

Process is explained with reference to illustrating the inputted and outputted data from the autonomy calculator . At step process determines the present state of the robot parameters such as the location or orientation of the robot its arm position etc. The decoded vehicle status information VSI received from the data radio and the sensor data received from the sensors on robot are sent to the autonomy calculator .

At step process determines the desired state of the robot parameters. The sensor data from the sensors on the robot is sent to the autonomy calculator .

At decision step process determines if the present state of stop is sufficiently close to the desired state of step . If it is then process completes the autonomy process at step .

Otherwise if the present state of step is not sufficiently close to the desired state of step then process proceeds to step where it calculates the trajectory for moving the present state closer to the desired state by a specified amount. The preprogrammed software in the autonomy calculator calculates the trajectory using the VSI and sensor data obtained in steps and .

At step process implements the trajectory calculated at step by sending the appropriate commands to the various parts or components of the robot . The autonomy commands calculated by the autonomy calculator are sent to the robot via data radio .

An exemplary insertion of data into the OCU to robot data stream is the implementation of an autonomous process such as autonomous arm motion. In this example the autonomy calculator issues commands to the robot s lower and upper arm e.g. in order to implement the calculated arm trajectory. The issuance of the commands which is executed as described in step of proceeds as follows 

 1 The lower arm and the upper arm commands are encoded according to an applicable standard such as the Joint Architecture for Unmanned Systems JAUS standard.

 3 The value of the parameters in the lower and upper arm control data fields in that string are set to the desired values.

 4 The modified data string which includes the autonomous arm commands is then sent to the data radio for transmission to the robot .

 5 The autonomous commands are inserted into each command string sent to the robot as long as the autonomous arm motions need to be commanded.

Other autonomous commands generated by the autonomy calculator such as driving commands or pan tilt camera motions can be integrated into the data stream in the same manner. Further extraneous commands sent from an interface connected to the OCU may be integrated into the OCU to robot data string in the same manner.

An example of insertion of data into the robot to OCU data stream is sending data from the sensors mounted on the robot back to the OCU . In this case the robot microprocessor unit receives the sensor data and conditions it as necessary. It then formats the data according to an applicable standard such as the Department of Defense Common Chemical Biological Radiological and Nuclear Sensor Interface CCSI Standard.

Thereafter the next data string that contains data sent from the robot to the OCU is captured. The formatted data string is appended to the end of that robot to OCU data string. The modified data string which includes the sensor data is then sent to the data radio for transmission to the OCU . This process is repeated for each data string sent from the robot to the OCU as long as the sensor data needs to be sent.

The communication system is quite readily integratable into the robot and the OCU . The entire integration effort includes disconnecting the robot antenna and inserting the robot communication box A in series with the robot antenna and disconnecting the OCU antenna and inserting the OCU communication box B in series with the OCU antenna .

The communication system provides numerous new capabilities to existing radio controlled robots without having to reprogram the robot s internal microprocessors. For example if one desires to add capabilities to a commercial robot whose microprocessors and their computer code is inaccessible the communication system enables new capabilities to be added to the robot without interfering with the regular operation of the robot .

The following are some exemplary types of new capabilities to be added to the robot that could be added by the communication system 

a. Autonomous reaching and grasping of objects mounted on the robot or objects in the proximity of the robot.

In addition the communication system enables integration of other additional sensors onto and in communication with the robot .

It is to be understood that the specific embodiments of the invention that have been described are merely illustrative of certain applications of the principle of the present invention. Numerous modifications may be made to the communication system described herein without departing from the spirit and scope of the present invention.

