---

title: Vehicle control device
abstract: To provide a vehicle control device that improves the accuracy of an automatic follow-up control in an inverted pendulum vehicle, a vehicle control device according to the present invention performs an automatic follow-up running control in an inverted pendulum vehicle so as to automatically follow a preceding vehicle. The vehicle control device is characterized by including: a communication unit that receives running condition data from the preceding vehicle regarding a vehicle speed and a joystick operation amount of the preceding vehicle; an inter-vehicle distance sensor that measures an inter-vehicle distance with the preceding vehicle; and a main control ECU that computes an acceleration command value for following the preceding vehicle, wherein the main control ECU sets one of a first acceleration command value, which is computed based on the vehicle speed of the preceding vehicle acquired through the communication unit and the inter-vehicle distance measured by the inter-vehicle distance sensor, and a second acceleration command value, which is computed based on the joystick operation amount acquired through the communication unit, as a target acceleration command value.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08352147&OS=08352147&RS=08352147
owner: Equos Research Co., Ltd.
number: 08352147
owner_city: Tokyo
owner_country: JP
publication_date: 20081023
---
The present invention relates to a control device for a vehicle that utilizes an inverted pendulum attitude control for example. More specifically the present invention relates to a vehicle control device for performing automatic follow up running in a plurality of vehicles.

Vehicles that utilize an inverted pendulum attitude control hereinafter simply referred to as inverted pendulum vehicles have been drawing attention in recent years. For example Patent Document 1 Japanese Patent Application Publication No. JP A 2004 129435 proposes a conveying apparatus that utilizes an inverted pendulum attitude control.

Meanwhile conventional automatic driving systems are known that automatically drive a vehicle such as an automobile. Under such automatic driving systems it is often more preferable for a plurality of automobiles traveling on an expressway or the like to form a line and travel as a vehicle group rather than as individual vehicles from the standpoints of saving labor mitigating traffic and the like. Therefore various research has been carried out regarding how following vehicles form a line with respect to a preceding vehicle and to what extent follow up running is automatically performed with respect to a preceding vehicle in automatic driving systems. Art related to such follow up running is described in Patent Document 2 Japanese Patent Application Publication No. JP A 2001 273588 for example.

To prevent the vehicle body of an inverted pendulum vehicle from falling over due to inertial force when braking the vehicle an acceleration torque is applied once to the vehicle wheel before braking to incline the vehicle body rearward and then after a predetermined rearward inclination angle has been achieved a braking torque is applied to the vehicle wheel to start braking.

An automatic follow up running control in an inverted pendulum vehicle that behaves as described above during braking will be examined here. In this case an example using two vehicles will be considered for simplicity. Specifically an example in which a following vehicle automatically follows a preceding vehicle in accordance with a rider s driving operation will be considered.

When the preceding vehicle initiates braking an acceleration for inclining the vehicle body rearward is started that increases the wheel rotational acceleration of the preceding vehicle. Thus the difference between the wheel rotational speeds of the preceding vehicle and the following vehicle increases. Consequently an acceleration command value of the following vehicle becomes larger than an immediately prior acceleration command value. When the preceding vehicle subsequently achieves the target vehicle body inclination angle and starts to brake the following vehicle is given a deceleration command to follow such behavior and an acceleration for inclining the vehicle body of the following vehicle rearward is started.

Thus the timing at which the following vehicle initiates braking is delayed with respect to the timing at which the preceding vehicle initiates braking. This results in reduced accuracy of the automatic follow up control in the following vehicle and at worse may result in an inability to perform follow up running.

Note that the same problems may occur in the following vehicle during acceleration of the preceding vehicle and the like.

In summary in preparatory operations before acceleration and braking of inverted pendulum vehicles a counter direction operation is performed namely an operation is performed once in the direction of acceleration in preparation for braking and once in the direction of braking in preparation for acceleration with such operations hereinafter referred to as counter operations . If an automatic follow up running control is performed in the inverted pendulum vehicles for such operations the following vehicle ends up reacting to the preparatory operation for braking or acceleration of the preceding vehicle which causes a delay in the automatic follow up running control of the following vehicle and lowers control accuracy.

In order to solve the above problems an invention according to claim is a vehicle control device controlling a vehicle so as to follow a preceding vehicle performing an inversion control. The vehicle control device is characterized by including a communication unit that receives a vehicle speed of the preceding vehicle and an operation amount of a maneuvering device that maneuvers the preceding vehicle an inter vehicle distance sensor that measures an inter vehicle distance between the preceding vehicle and the vehicle following the preceding vehicle and computation means that computes an acceleration command value of the vehicle following the preceding vehicle wherein the computation means sets one of a first acceleration command value which is computed based on the vehicle speed of the preceding vehicle received by the communication unit and the inter vehicle distance measured by the inter vehicle distance sensor and a second acceleration command value which is computed based on the operation amount of the maneuvering device received by the communication unit as a target acceleration command value.

An invention according to claim is characterized in that in the vehicle control device of claim the computation means sets a smaller value among the first acceleration command value and the second acceleration command value as the target acceleration command value if output of a deceleration command to the preceding vehicle is determined based on the operation amount of the maneuvering device.

An invention according to claim is characterized in that in the vehicle control device of claim or the computation means sets a larger value among the first acceleration command value and the second acceleration command value as the target acceleration command value if output of an acceleration command to the preceding vehicle is determined based on the operation amount of the maneuvering device.

An invention according to claim is a vehicle control device controlling a vehicle so as to follow a preceding vehicle performing an inversion control. The vehicle control device is characterized by including a communication unit that receives a vehicle speed of the preceding vehicle and an operation amount of a maneuvering device that maneuvers the preceding vehicle an inter vehicle distance sensor that measures an inter vehicle distance between the preceding vehicle and the vehicle following the preceding vehicle and computation means that computes an acceleration command value of the vehicle following the preceding vehicle wherein the computation means sets one of a first acceleration command value which is computed based on the vehicle speed of the preceding vehicle received by the communication unit and the inter vehicle distance measured by the inter vehicle distance sensor and a second acceleration command value which is computed based on an acceleration command value of the preceding vehicle received by the communication unit as a target acceleration command value.

An invention according to claim is characterized in that in the vehicle control device of claim the computation means sets a smaller value among the first acceleration command value and the second acceleration command value as the target acceleration command value if the acceleration command value of the preceding vehicle is determined to be negative.

An invention according to claim is characterized in that in the vehicle control device of claim or the computation means sets a larger value among the first acceleration command value and the second acceleration command value as the target acceleration command value if the acceleration command value of the preceding vehicle is determined to be not negative.

An invention according to claim is a vehicle control device controlling a vehicle so as to follow a preceding vehicle performing an inversion control. The vehicle control device is characterized by including a communication unit that receives a vehicle speed of the preceding vehicle and an operation amount of a maneuvering device that maneuvers the preceding vehicle an inter vehicle distance sensor that measures an inter vehicle distance between the preceding vehicle and the vehicle following the preceding vehicle and computation means that computes an acceleration command value of the vehicle following the preceding vehicle wherein the computation means sets a second acceleration command value which is computed based on an acceleration command value of the preceding vehicle received by the communication unit as a target acceleration command value.

An invention according to claim is characterized in that in the vehicle control device of any one of claims to the vehicle speed is obtained from a wheel rotational speed.

According to the vehicle control device of claim in the present invention one of a first acceleration command value which is computed based on the vehicle speed of the preceding vehicle received by the communication unit and the inter vehicle distance measured by the inter vehicle distance sensor and a second acceleration command value which is computed based on the operation amount of the maneuvering device received by the communication unit is set as a target acceleration command value. Therefore no delay occurs in the automatic follow up running control of the following vehicle and information regarding braking is transmitted without delay to the following vehicle which can help avoid the risk of collision and realize a highly accurate automatic follow up running control.

According to the vehicle control device of claim in the present invention a smaller value among the first acceleration command value and the second acceleration command value is set as the target acceleration command value if output of a deceleration command to the preceding vehicle is determined. Therefore an automatic follow up running control that enables the following vehicle to avoid a situation that may lead to a collision with the preceding vehicle can be realized.

According to the vehicle control device of claim in the present invention a larger value among the first acceleration command value and the second acceleration command value is set as the target acceleration command value if output of an acceleration command to the preceding vehicle is determined. Therefore an automatic follow up running control that enables the following vehicle to track the preceding vehicle without delay can be realized.

According to the vehicle control device of claim in the present invention one of a first acceleration command value which is computed based on the vehicle speed of the preceding vehicle received by the communication unit and the inter vehicle distance measured by the inter vehicle distance sensor and a second acceleration command value which is computed based on an acceleration command value of the preceding vehicle received by the communication unit is set as a target acceleration command value. Therefore no delay occurs in the automatic follow up running control of the following vehicle and information regarding braking is transmitted without delay to the following vehicle which can help avoid the risk of collision and realize a highly accurate automatic follow up running control.

According to the vehicle control device of claim in the present invention a smaller value among the first acceleration command value and the second acceleration command value is set as the target acceleration command value if the acceleration command value of the preceding vehicle is determined to be negative. Therefore an automatic follow up running control that enables the following vehicle to avoid a situation that may lead to a collision with the preceding vehicle can be realized.

According to the vehicle control device of claim in the present invention a larger value among the first acceleration command value and the second acceleration command value is set as the target acceleration command value if the acceleration command value of the preceding vehicle is determined to be not negative. Therefore an automatic follow up running control that enables the following vehicle to track the preceding vehicle without delay can be realized.

According to the vehicle control device of claim in the present invention a second acceleration command value which is computed based on an acceleration command value of the preceding vehicle received by the communication unit is set as a target acceleration command value. This is effective in cases that place particular importance on the follow up capability of the following vehicle with respect to the preceding vehicle such as when follow up is performed with a short inter vehicle distance.

Hereinafter embodiments of the present invention will be described with reference to the drawings. shows conditions of acceleration with a small angle of inclination achieved through movement of a riding section in an embodiment. In this embodiment the balance inverted state of a vehicle body is maintained by moving the riding section including a rider relatively translationally in a longitudinal direction of the vehicle. Specifically referring to the riding section including the rider is moved translationally in an acceleration direction to maintain a balance of the vehicle body with an anti torque of a drive wheel and inertial force accompanying acceleration acting thereon as a result of acceleration deceleration according to a target running state for example acceleration deceleration or stop based on an operation performed by the rider. Thus the inclination angle of the vehicle body accompanied by the acceleration deceleration can be reduced to provide a comfortable and safe inverted type vehicle.

The above control will be described in the present embodiment. Note that the embodiment may be configured so as to perform a control operation that counters with only movement of the riding section if an acceleration in accordance with the target running state is relatively small and counters using the inclination angle of the vehicle body in addition to movement of the riding section if the acceleration is relatively large.

Referring to the vehicle includes two drive wheels disposed coaxially. The drive wheels are driven by drive motors respectively. Note that one or three or more drive wheels and drive motors may be disposed instead of coaxially disposing two each as described above.

The riding section seat that carries a cargo a rider or other weight body is disposed above the drive wheels a drive wheel to mean both drive wheels collectively the same holds true with other elements hereunder and the drive motor .

The riding section includes the seat cushion portion on which the rider sits the seat back portion and the headrest .

The riding section is supported by the support member via the movement mechanism . The support member is fixed to a drive motor cabinet in which the drive motor is accommodated.

A linear guide system or other linear movement mechanism having low resistance is for example used as the movement mechanism . The position of the riding section relative to the support member is changed through the drive torque of a riding section drive motor.

The linear guide system includes a guide rail fixed to the support member a slider fixed to the riding section drive motor and a rolling body.

The guide rail includes two trackway grooves formed linearly longitudinally in right and left side surface portions of the guide rail.

The slider has a channel shaped cross section. Two trackway grooves are formed inside two mutually opposing side surface portions of the channel shape so as to face the two trackway grooves respectively in the guide rail.

The rolling body is inserted between the abovementioned trackway grooves rolling in the trackway grooves as the guide rail and the slider make linear motions relative to each other.

Additionally the slider includes a return path formed therein connecting both ends of the trackway grooves so that the rolling body circulates through the trackway grooves and the return path.

The linear guide system includes a brake clutch that fixes the movement of the linear guide system. When the movement of the riding section is not required such as when the vehicle is not moving the slider is fixed onto the guide rail with the brake so as to maintain the positions of the support member to which the guide rail is fixed and the riding section to which the slider is fixed relative to each other. When the movement is required the brake is released so that the distance between a reference position on the side of the support member and a reference position on the side of the riding section can be controlled to be a predetermined value.

The input device is disposed beside the riding section . The input device includes the joystick disposed thereon. The rider operates the joystick to issue commands for acceleration deceleration turning on the spot rotation standing still braking and other operations of the vehicle. Although an example using a joystick as a maneuvering device is described in the present embodiment other input devices may be used as the maneuvering device.

The input device according to the present embodiment is fixed to the seat cushion portion . The input device may instead be configured with a wired or wireless remote control or disposed on an armrest additionally provided.

The input device is disposed in the vehicle installed with the vehicle control device of the present embodiment and the vehicle is controlled by the rider operating the joystick of the input device . The vehicle control has two modes a normal running mode that is based on such rider operation and an follow up running mode that follows a preceding vehicle and is not based on rider operation. Although an example of a control device for a vehicle having both a normal running mode and a follow up running mode is described in the present embodiment the vehicle control device of the present invention may also be applied to a vehicle having only a follow up running mode.

Note that if the vehicle is controlled so as to run automatically according to predetermined travel command data a travel command data acquisition section is disposed in place of the input device . The travel command data acquisition section may include for example data reading means acquiring the travel command data from various types of storage media such as a semiconductor memory or and communication control means acquiring the travel command data externally through wireless communications.

In a human is on the riding section . However the vehicle is not necessarily limited to an application of a human rider operating rather the vehicle may carry only a cargo or nothing and run or stop through for example remote control from an external environment or according to travel command data.

The inter vehicle distance sensor is provided in the control unit and measures a distance between the host vehicle and a vehicle traveling in front of the host vehicle. The inter vehicle distance sensor may be formed of a laser radar a millimeter wave radar or an ultrasonic radar for example. When executing the vehicle control of the follow up running mode in the present embodiment inter vehicle distance information detected by the inter vehicle distance sensor is used. However the inter vehicle distance information may also be used for other vehicle controls.

The communication unit is a communication device capable of transmitting information between vehicles and may employ a wireless or wired format. When executing the vehicle control of the follow up running mode in the present embodiment the communication unit acquires predetermined information pertaining to a running condition and the like of the preceding vehicle from the communication unit of the preceding vehicle and provides such information for the vehicle control of the host vehicle.

The control unit is disposed between the riding section and the drive wheel . In the present embodiment the control unit is mounted on the support member .

The control unit may be mounted on a lower surface of the seat cushion portion of the riding section . In this case the control unit is moved in the forward backward direction with the riding section by the movement mechanism .

The vehicle according to the present embodiment includes a battery among other miscellaneous types of devices. The battery disposed on the support member supplies electric power for drive and computational operations to for example the drive motor the riding section drive motor and a control ECU .

In the description given hereunder a drive wheel collectively means the drive wheel and parts fixed to and rotated with the drive wheel a vehicle body means an entire vehicle including a rider but excluding the drive wheel and a riding section means the riding section and parts including the rider fixed to and moved translationally with the riding section .

In the present embodiment the riding section is formed of the riding section the input device and a part of the movement mechanism linear guide . The control unit or the battery may be disposed on the riding section so as to be included in the riding section . This increases the weight of the riding section and a greater effect is thus produced from the movement of the riding section .

The control system of the vehicle control device according to the present embodiment includes the control ECU electronic control unit that functions as running and attitude control means the joystick the vehicle body inclination sensor the inter vehicle distance sensor the drive wheel sensor the drive motor same as the drive motor the riding section sensor the riding section motor riding section drive motor the communication unit and other devices.

The control ECU includes the main control ECU the drive wheel control ECU the riding section control ECU and the communication unit control ECU and performs various types of controls including the vehicle running and attitude control through for example a drive wheel control and a vehicle body control inversion control .

The control ECU is formed of a computer system that includes a ROM that stores therein various programs and data such as the running and attitude control process program in the present embodiment a RAM used as a work area an external storage device and an interface portion.

The main control ECU is connected to the drive wheel sensor the vehicle body inclination sensor the inter vehicle distance sensor the riding section sensor and the joystick as the input device .

The joystick supplies the main control ECU with a running command maneuvering operation amount based on an operation performed by the rider.

With its upright position defined as a neutral position the joystick is tilted in the forward backward direction to command acceleration or deceleration and in the lateral direction to command lateral acceleration during turning. The requested acceleration deceleration or lateral acceleration is greater with a larger tilt angle.

The vehicle body inclination sensor functions as inclination detection means that detects the angle of inclination of the vehicle body and detects an inclination state of the vehicle body in the forward backward direction about an axle of the drive wheel .

The vehicle body inclination sensor includes an acceleration sensor that detects acceleration and a gyro sensor that detects a vehicle body inclination angular velocity. Accuracy of the vehicle body inclination sensor is enhanced by calculating a vehicle body inclination angle from a detected vehicle body inclination angular velocity as well as from a detected acceleration. Instead either one of the sensors may be disposed in the vehicle body inclination sensor and the vehicle body inclination angle and or the angular velocity may be calculated from a value detected thereby.

The inter vehicle distance sensor detects the distance between the host vehicle and a vehicle traveling in front of the host vehicle and is formed of a laser radar a millimeter wave radar or an ultrasonic radar for example. Inter vehicle distance information detected by the inter vehicle distance sensor is used when the vehicle is in the follow up running mode.

The main control ECU functions as target running state acquisition means that acquires the target running state set as a target. Further the main control ECU functions as output determination means that determines the drive torque of the drive wheel and the movement thrust force of the riding section according to the acquired target running state.

The main control ECU functions as target attitude determination means that determines a vehicle body inclination angle and a riding section position set as targets according to the target running state based on a signal from the joystick .

Additionally the main control ECU functions as feedforward output determination means that determines a feedforward output of each actuator the drive motor and the riding section motor according to the target running state and a target attitude the target vehicle body inclination angle and the target riding section position .

Further the main control ECU functions as feedback output determination means that determines a feedback output of the drive motor according to a deviation in the vehicle body inclination angle between a target value and an actually measured value and a feedback output of the riding section motor according to a deviation in the riding section position between a target value and an actually measured value.

When the vehicle is in the follow up running mode the main control ECU determines an acceleration command in accordance with a running condition and the like of the preceding vehicle and determines a drive torque command of the drive wheel based on the acceleration command. In addition when the vehicle is in the follow up running mode the main control ECU determines the acceleration command in accordance with a running condition and the like of the preceding vehicle and determines the target running state and the target attitude.

The main control ECU functions with the drive wheel control ECU and the drive motor as drive means and a drive wheel control system is formed by further including the drive wheel sensor with the drive means.

The drive wheel sensor detects a drive wheel rotation angle rotation angular velocity that represents a rotation state of the drive wheel and supplies the main control ECU with the drive wheel rotation angle. The drive wheel sensor of the present embodiment is formed of a resolver rotary encoder or the like detecting the drive wheel rotation angle. The rotation angular velocity is calculated using this drive wheel rotation angle.

The main control ECU supplies the drive wheel control ECU with a drive torque command value and the drive wheel control ECU supplies the drive motor with an input voltage drive voltage corresponding to the drive torque command value. The drive motor functions as a drive wheel actuator that applies to the drive wheel the drive torque according to the input voltage.

Additionally the main control ECU forms the riding section control system with the riding section control ECU the riding section sensor and the riding section motor .

The riding section sensor functions as a position detector that detects a relative position of the riding section and supplies data that represents the detected riding section position movement speed to the main control ECU . The riding section sensor of the present embodiment is formed of an encoder detecting the riding section position. The movement speed of the riding section is calculated from a detected value of the riding section position.

The main control ECU supplies the riding section control ECU with a riding section thrust force command value. The riding section control ECU supplies the riding section motor with an input voltage drive voltage corresponding to the riding section thrust force command value. The riding section motor functions as a riding section actuator that applies a thrust force for moving the riding section translationally according to the input voltage.

Additionally the main control ECU forms the communication control system with the communication unit control ECU and the communication unit . The communication unit performs vehicle to vehicle data communication in a wireless format for example. Through the communication unit control ECU the communication unit inputs received data to the main control ECU and transmits predetermined data output from the main control ECU .

A running and attitude control process performed by the vehicle having the above arrangement will be described below. is a flowchart of the running and attitude control in the vehicle control device according to the embodiment of the present invention.

The running and attitude control according to the present embodiment achieves the target running state while maintaining the balance of the vehicle body by controlling the vehicle body inclination or the riding section position according to the running state set as the target including for example acceleration deceleration and stop.

Once the process of the flowchart is initiated at step S in the main control ECU first determines how the vehicle is moved according to an intention of the rider specifically the running target of the vehicle steps S to S .

The process proceeds to step S where the main control ECU next determines a vehicle body target attitude the target vehicle body inclination angle and the target riding section position at which the balance of the vehicle body is maintained makes the vehicle take an inverted attitude under the determined running target.

By optimizing the vehicle body inclination amount and the riding section position as described above the rider can feel an appropriate acceleration while minimizing the vehicle body inclination to prevent riding comfort from being degraded.

At steps S to S the main control ECU then determines output values of the drive motor and the riding section motor required for achieving the vehicle running state and the vehicle attitude set as targets. In accordance with the output values actual outputs of the drive motor and the riding section motor are controlled using the drive wheel control ECU and the riding section control ECU .

At step S the main control ECU acquires the maneuvering operation amount running command of the joystick operated by the rider.

The process then proceeds to step S where the main control ECU determines a target value of vehicle acceleration vehicle target acceleration based on the acquired operation amount. A value proportional for example to the forward backward operation amount of the joystick is defined as the value of the vehicle target acceleration .

At step S using the determined vehicle target acceleration the main control ECU calculates a target value of the drive wheel angular velocity drive wheel target angular velocity .

Note that a symbol n represents a derivative of n with respect to time. For example the vehicle target acceleration is integrated with respect to time and divided by a predetermined drive wheel ground contact radius to arrive at a value as the drive wheel target angular velocity .

Next at step S the main control ECU determines the target values of the vehicle body inclination angle and riding section position. Specifically the target value of the vehicle body inclination angle target vehicle body inclination angle is determined using Formulas 1 to 3 given below according to the magnitude of the vehicle target acceleration determined at step S.

Then based on the determined target vehicle body inclination angle the target value of the riding section position riding section target position is determined using Formulas 4 to 6 according to the magnitude of the vehicle target acceleration . sin sin cos 

 is the vehicle target acceleration G . is a set value representing the maximum riding section movement amount.

A threshold value is the vehicle target acceleration when in Formula 5 specifically when the riding section has been moved to its stroke limit. The threshold value is a preset value but cannot be obtained analytically. The threshold value is therefore determined for example through iterative calculation or with an approximate expression.

If the vehicle target acceleration falls within a range of the threshold value the target vehicle body inclination angle is determined using Formula 2 and the riding section target position is determined using Formula 5 .

As a result in the range of the rider can feel an appropriate acceleration while maintaining the balance of the vehicle body by moving the riding section to with the vehicle body inclined at .

As such movement of a gravity center position required for achieving the vehicle target acceleration is accomplished in the range of the threshold value by both inclination of the vehicle body and movement of the riding section. Herein the amounts of movement of the gravity center borne by the inclination of the vehicle body and movement of the riding section are determined by a rider acceleration sensation coefficient Cin Formulas 2 and 5 . The value of Cis preset to fall within a range of 0 C 1.

A greater preset value Crelative to the vehicle target acceleration results in a larger target vehicle body inclination angle Formula 2 and a smaller riding section target position Formula 5 .

Ccorresponds to the degree of acceleration the rider feels. Specifically if C 1 the target vehicle body inclination angle 0 Formula 2 so that the vehicle body is not inclined at all. The rider therefore directly feels inertial force as a result of acceleration or deceleration of the vehicle.

If C 0 tan so that the vehicle body is inclined to an equilibrium inclination angle angle between the resultant force of gravity and inertial force . As a result the rider feels no inertial force though the downward force increases relative to the rider .

For example if C 1 the movement of the gravity center position required for achieving the vehicle target acceleration is accomplished by only the movement of the riding section and the vehicle runs with the vehicle body controlled to maintain an upstanding position.

When the riding section movement amount reaches the stroke limit specifically if the vehicle target acceleration is the balance is maintained by further inclining the vehicle body as shown in Formulas 1 and 3 .

Note that if the riding section movement amount has not reached the stroke limit the vehicle body inclination angle may be limited instead.

 Modified Example of Determination of the Target Vehicle Body Inclination Angle and the Riding Section Target Position 

In the above embodiment a case was described in which the target vehicle body inclination angle and the riding section target position are determined by selecting from the relationship between the vehicle target acceleration and the threshold value any one of Formulas 1 to 3 and any one of Formulas 4 to 6 .

The target vehicle body inclination angle and the riding section target position may instead be determined through a target value determination process shown in .

At step S using the determined and Formula 5 the main control ECU calculates the riding section target position and at step S determines whether the obtained falls within the range of over which the riding section can move.

If the calculated value falls within the range over which the riding section can move step S Y the main control ECU determines obtained at step S to be the target vehicle body inclination angle and obtained at step to be the riding section target position respectively step S before terminating the process.

If the calculated value falls outside the range over which the riding section can move step S N the main control ECU determines the maximum riding section movement amount to be the riding section target position step S .

The main control ECU again calculates that corresponds to the vehicle target acceleration using Formula 1 or 3 and determines this to be the target vehicle body inclination angle step S before terminating the process.

According to the target value determination process described above the target vehicle body inclination angle and the riding section target position can be determined without using the threshold value for determining which expression to use among Formulas 1 to 3 and Formulas 4 to 6 .

In the present embodiment Formulas 1 to 6 that are strictly theoretical expressions are used to determine the vehicle body target attitude. A simpler expression may be used instead. For example linearized formulas of Formulas 1 to 6 may be used. Further instead of using the expressions a map may be prepared in advance representing a relationship between the vehicle target acceleration and the vehicle body target attitude and the vehicle body target attitude may be determined using that map.

A more complicated relational expression may also be used. For example a relational expression may be established with which if an absolute value of the vehicle target acceleration is equal to or smaller than a predetermined threshold value the riding section is moved without inclining the vehicle body at all and inclination of the vehicle body starts as the absolute value exceeds the predetermined threshold.

Note that in the present embodiment the maximum forward movement amount of the riding section from a reference position is equal to the maximum rearward movement amount of the riding section from the reference position. However these movement amounts may be different from each other. For example if the maximum rearward movement amount is greater than the maximum forward movement amount braking performance can be improved over acceleration performance. In this case a similar control as described above can be easily achieved by correcting the threshold value to correspond to each of the limit values.

Returning to the running and attitude control process at step S the main control ECU uses each of the determined target values to calculate remaining target values.

Specifically each target value is differentiated with respect to time or integrated with respect to time to calculate a drive wheel rotation angle target value W a vehicle body inclination angular velocity target value and a riding section movement speed target value .

The main control ECU uses the following Formula 7 to determine a feedforward output that is estimated to be required for achieving the vehicle target acceleration . Note that M in Formula 7 represents a gross mass of the vehicle in which a rotational inertia component of the drive wheel is also incorporated.

Additionally Formula 8 is used to determine a feedforward output Sof the riding section motor from each of the target values. Scorresponds to the riding section thrust force required to prevent the riding section from being moved by gravity so as to stay at the target position at the target vehicle body inclination angle . Expression 1 Formula 7 sin Formula 8 where . Expression 2 

Each state quantity can be more accurately controlled by applying the feedforward outputs obtained by Formulas 7 and 8 .

Note that this method is particularly effective in decreasing steady state deviation of the state quantity. However an integral gain may be given in a feedback control step S instead.

At step S the main control ECU next acquires each state quantity from each sensor. Specifically the drive wheel rotation angle rotation angular velocity is acquired from the drive wheel sensor the vehicle body inclination angle inclination angular velocity is acquired from the vehicle body inclination sensor and the riding section position movement speed is acquired from the riding section sensor .

Additionally at step S the main control ECU calculates remaining state quantities. Specifically the drive wheel rotation angle rotation angular velocity the vehicle body inclination angle inclination angular velocity and the riding section position movement speed are integrated or differentiated with respect to time to calculate the remaining state quantities.

Specifically Formula 9 is used to determine a feedback output of the drive motor and Formula 10 is used to determine a feedback output Sof the riding section motor based on a deviation between each target value and actual state quantity.

In Formulas 9 and 10 each K value is a feedback gain and for example an optimum regulator value is preset for each feedback gain K. In addition an integral gain may be introduced to eliminate the steady state deviation as described earlier. Formula 9 Formula 10 

Some of the feedback gains may be zeroed to simplify the expressions. For example K K may be used in place of Formula 9 and S K may be used in place of Formula 10 .

Finally at step S the main control ECU gives each element control system a command value and returns to a main routine.

Specifically the main control ECU supplies the drive wheel control ECU with a sum of the feedforward output determined at step S and the feedback output determined at step S as a drive torque command value . Further the main control ECU supplies the riding section control ECU with a sum S S of the feedforward output SFF and the feedback output Sas a riding section thrust force command value S.

Accordingly the drive wheel control ECU supplies the drive motor with an input voltage drive voltage corresponding to the drive torque command value to thereby apply the drive wheel drive torque .

Similarly the riding section control ECU supplies the riding section motor with an input voltage drive voltage corresponding to the riding section thrust force command value Sto thereby move the riding section.

The parameters of the vehicle attitude control are organized below. is a drawing that shows a dynamic model of a vehicle attitude control system.

The entire vehicle control process of the follow up running mode will be outlined next. is a drawing that shows a control model in the vehicle control device according to the embodiment of the present invention and shows block diagrams of a control system in the follow up running mode of the vehicle control device according to the embodiment of the present invention.

In the present embodiment a case is described in which both the preceding vehicle and the following vehicle are inverted pendulum vehicles. However the control of the vehicle control device according to the present invention may also be applied to a case in which the following vehicle is an ordinary four wheel vehicle or the like provided that the preceding vehicle is an inverted pendulum vehicle.

Hereinafter a vehicle control in which a following vehicle B running in the follow up running mode follows a preceding vehicle A running in the normal running mode as shown in will be described. assumes a condition in which the preceding vehicle A is driven and operated by a rider and the following vehicle B automatically follows without being driven or operated the preceding vehicle A in the follow up running mode.

It is an object of the vehicle control device of the present embodiment to determine a target acceleration command value of the target acceleration in the follow up running mode.

The control system block diagram in represents that of the preceding vehicle A and the control system block diagram in represents that of the following vehicle B. Note that the control system block diagrams shown in are based on the control system block diagram shown in .

In the follow up running mode the following vehicle B acquires running condition data of the preceding vehicle A through the communication unit from the preceding vehicle A. More specifically vehicle speed information of the preceding vehicle A and the operation amount of the joystick of the preceding vehicle A are acquired as running condition data. In addition the following vehicle B acquires an inter vehicle distance d according to the measurement of the inter vehicle distance sensor .

In the present embodiment the target acceleration is computed based on the running condition data vehicle speed and joystick operation amount of the preceding vehicle A acquired through the communication unit and the inter vehicle distance d measured by the inter vehicle distance sensor . Therefore the following vehicle B can track the preceding vehicle A without delay and a highly accurate automatic follow up running control can be realized.

Note that the vehicle speed here is obtained using a wheel rotation angle. Specifically the wheel rotation angle is detected and a differential value of the wheel rotation angle is used as the wheel rotational speed. The vehicle speed is then obtained from this rotational speed.

After acquiring the above parameters the main control ECU of the following vehicle B calculates two acceleration command values as candidates for the command value of the target acceleration based on Formula 11 for calculating a first acceleration command value and Formula 12 for calculating a second acceleration command value. is an acceleration command value calculated using the first acceleration command value and is an acceleration command value calculated using the second acceleration command value. Formula 11 Formula 12 

In Formulas 11 and 12 is the acceleration of the preceding vehicle A kis the inter vehicle distance gain d is the inter vehicle distance measured by the inter vehicle distance sensor d is the target inter vehicle distance kis the speed gain vis the vehicle speed of the preceding vehicle A vis the vehicle speed of the following vehicle B kis the operation amount gain and Jis the joystick operation amount of the preceding vehicle A.

The main control ECU calculates both of the two acceleration command values and and performs a control so as to utilize the appropriate value among these acceleration command values depending on the estimated behavior of the preceding vehicle A.

More specifically if the preceding vehicle A is accelerating it is determined based on the joystick operation amount of the preceding vehicle A whether such accelerating is a normal acceleration or an acceleration as a counter operation in preparation for braking. Depending on this determination the appropriate acceleration command value from among the two acceleration commands and is utilized as the acceleration command value of the target acceleration.

Thus the following vehicle B determines the acceleration command value depending on the joystick operation amount information of the preceding vehicle A. Therefore no delay occurs in the automatic follow up running control of the following vehicle B and the accuracy of the automatic follow up running control can be improved. Conversely by configuring the control such that the joystick operation amount of the preceding vehicle A is not used except at times of deceleration the following vehicle B is not affected by minute adjustment operations performed by the driver of the preceding vehicle and can travel in a stable manner.

When the preceding vehicle A brakes the joystick operation amount is transmitted from the preceding vehicle A to the following vehicle B so that information regarding the preceding vehicle A braking can be transmitted without delay to the following vehicle B to help avoid the risk of collision.

As described above in the present embodiment the vehicle speed information of the preceding vehicle A and the operation amount of the joystick of the preceding vehicle A are communicated from the preceding vehicle A to the following vehicle B as running condition data. Thus the accuracy of the automatic follow up running control can be improved.

The control process of the follow up running mode in the following vehicle B will be described next. is a flowchart of the automatic follow up control process in the vehicle control device according to the embodiment of the present invention.

Once the automatic follow up control process is initiated at step S in the process proceeds to step S where the communication unit is used to receive the vehicle speed information and the joystick operation amount of the preceding vehicle A running condition data .

At step S the received vehicle speed of the preceding vehicle A is stored in a storage portion not shown of the main control ECU . At step S the main control ECU calculates the acceleration of the preceding vehicle A from information regarding the vehicle speed that is cumulatively stored in the storage portion.

At step S the vehicle speed of the host vehicle following vehicle B is measured by the drive wheel sensor . Next at step S the inter vehicle distance d between the host vehicle following vehicle B and the preceding vehicle A is measured by the inter vehicle distance sensor .

At step S the first acceleration command value of the host vehicle is calculated using Formula 11 from the acceleration and the vehicle speed vof the preceding vehicle A the vehicle speed vof the host vehicle and the inter vehicle distance d. At step S the second acceleration command value of the host vehicle is calculated using Formula 12 based on the joystick operation amount Jof the preceding vehicle A.

At step S it is determined whether the operation of the preceding vehicle A is a deceleration command based on the joystick operation amount J of the preceding vehicle A. If the determination result at step S is YES the process proceeds to step S if the determination result at step S is NO the process proceeds to step S.

At step S it is determined whether . If the determination at step S is YES the process proceeds to step S where the smaller value among the first acceleration command value and the second acceleration command value is utilized as the target acceleration command value . If the determination at step S is NO the process proceeds to step S where the smaller value among the first acceleration command value and the second acceleration command value is utilized as the target acceleration command value . At step S the drive torque command is executed based on the utilized acceleration command value. Following step S the process returns to step S and loops again. Note that this flowchart assumes looping of the process until the follow up running mode is canceled.

At step S it is determined whether . If the determination at step S is YES the process proceeds to step S where the larger value among the first acceleration command value and the second acceleration command value is utilized as the target acceleration command value . If the determination at step S is NO the process proceeds to step S where the larger value among the first acceleration command value and the second acceleration command value is utilized as the target acceleration command value . At step S the drive torque command is executed based on the utilized acceleration command value. Following step S the process returns to step S and loops again. Note that this flowchart assumes looping of the process until the follow up running mode is canceled.

The determination at step S serves as material for enabling the following vehicle B to distinguish between whether the acceleration operation of the preceding vehicle A is a normal acceleration operation or an acceleration operation counter operation in preparation for braking.

If the determination result at step S is YES the preceding vehicle A is attempting to brake and therefore the smaller value among the first acceleration command value and the second acceleration command value is utilized as the acceleration command value of the target acceleration. Thus the following vehicle B can avoid a situation that may lead to a collision with the preceding vehicle A.

If the determination result at step S is NO the preceding vehicle A is attempting to accelerate and therefore the larger value among the first acceleration command value and the second acceleration command value is utilized as the acceleration command value of the target acceleration. Thus the following vehicle B can track the preceding vehicle A without delay.

According to the present invention the vehicle speed information of the preceding vehicle A and the joystick operation amount of the preceding vehicle A is communicated from the preceding vehicle A to the following vehicle B as running condition data which can improve the accuracy of the automatic follow up running control.

Although an example was described with the present embodiment in which a vehicle follows a preceding vehicle the same control can be achieved when a vehicle travels side by side with the preceding vehicle.

A second embodiment of the present invention will be described next. In the previous embodiment while in the follow up running mode the following vehicle B uses the communication unit to acquire the vehicle speed information of the preceding vehicle A and the joystick operation amount of the preceding vehicle A. However in the present embodiment the following vehicle B uses the communication unit to acquire the vehicle speed information of the preceding vehicle A and an acceleration command value of the preceding vehicle A. Note that in the present embodiment as well the following vehicle B acquires the inter vehicle distance d measured by the inter vehicle distance sensor .

According to the present embodiment after acquiring the above parameters the main control ECU of the following vehicle B calculates two acceleration command values as candidates for the command value of the target acceleration based on Formula 11 for calculating a first acceleration command value which is the same as that used in the previous embodiment and Formula 13 for calculating a second acceleration command value which is unique to the present embodiment. Here is an acceleration command value calculated using the first acceleration command value and is an acceleration command value calculated using the second acceleration command value.

In this other embodiment as described above the target acceleration is computed based on the running condition data vehicle speed and acceleration command value of the preceding vehicle A acquired through the communication unit and the inter vehicle distance d measured by the inter vehicle distance sensor . Therefore the following vehicle B can track the preceding vehicle A without delay and a highly accurate automatic follow up running control can be realized.

Note that the vehicle speed here is obtained using a wheel rotation angle. Specifically the wheel rotation angle is detected and a differential value of the wheel rotation angle is used as the wheel rotational speed. The vehicle speed is then obtained from this rotational speed.

According to the present embodiment after acquiring the above parameters the main control ECU of the following vehicle B calculates two acceleration command values as candidates for the command value of the target acceleration based on Formula 11 for calculating a first acceleration command value which is the same as that used in the previous embodiment and Formula 13 for calculating a second acceleration command value which is unique to the present embodiment. Here is an acceleration command value calculated using the first acceleration command value and is an acceleration command value calculated using the second acceleration command value. Formula 11 Formula 13 

In Formulas 11 and 13 is the acceleration of the preceding vehicle A kis the inter vehicle distance gain d is the inter vehicle distance measured by the inter vehicle distance sensor d is the target inter vehicle distance kis the speed gain vis the vehicle speed of the preceding vehicle A vis the vehicle speed of the following vehicle B and is the acquired acceleration command value of the preceding vehicle A.

kis the acceleration command value gain and k 1. kis defined as the margin for surely stopping the vehicle. Although kmay be set to 1 in theory kis a gain used for ensuring safety in actuality.

The main control ECU calculates both of the two acceleration command values and and performs a control so as to utilize the appropriate value among these acceleration command values depending on the estimated behavior of the preceding vehicle A.

More specifically if the preceding vehicle A is accelerating it is determined based on the acceleration command value calculated within the main control ECU whether such accelerating is a normal acceleration or an acceleration as a counter operation in preparation for braking. Depending on this determination the appropriate acceleration command value from among the two acceleration commands and is utilized as the acceleration command value of the target acceleration.

Thus the following vehicle B determines the acceleration command value depending on the acceleration command value of the preceding vehicle A. Therefore no delay occurs in the automatic follow up running control of the following vehicle B and the accuracy of the automatic follow up running control can be improved. Conversely by configuring the control such that the acceleration command value information of the preceding vehicle A is not used except at times of deceleration the following vehicle B is not affected by minute adjustment operations performed by the driver of the preceding vehicle and can travel in a stable manner.

When the preceding vehicle A brakes the acceleration command value is transmitted from the preceding vehicle A to the following vehicle B so that information regarding the preceding vehicle A braking can be transmitted without delay to the following vehicle B to help avoid the risk of collision.

As described above in the present embodiment the vehicle speed information of the preceding vehicle A and the acceleration command value of the preceding vehicle A are communicated from the preceding vehicle A to the following vehicle B as running condition data. Thus the accuracy of the automatic follow up running control and riding comfort can be improved.

The control process of the follow up running mode in the following vehicle B will be described next. is a flowchart of an automatic follow up control process in the vehicle control device according to a second embodiment of the present invention. Once the automatic follow up control process is initiated at step S in the process proceeds to step S where the communication unit is used to receive the vehicle speed information and the acceleration command value of the preceding vehicle A running condition data .

At step S the received vehicle speed of the preceding vehicle A is stored in the storage portion not shown of the main control ECU . At step S the main control ECU calculates the acceleration of the preceding vehicle A from information regarding the vehicle speed that is cumulatively stored in the storage portion.

At step S the vehicle speed of the host vehicle following vehicle B is measured by the drive wheel sensor . Next at step S the inter vehicle distance d between the host vehicle following vehicle B and the preceding vehicle A is measured by the inter vehicle distance sensor .

At step S the first acceleration command value of the host vehicle is calculated using Formula 11 from the acceleration and the vehicle speed vof the preceding vehicle A the vehicle speed vof the host vehicle and the inter vehicle distance d. At step S the second acceleration command value of the host vehicle is calculated using Formula 13 based on the vehicle speed v the vehicle speed vof the host vehicle the inter vehicle distance d and the acceleration command value of the preceding vehicle A.

At step S it is determined whether the acceleration command value of the preceding vehicle A is negative deceleration based on the acceleration command value of the preceding vehicle A. If the determination result at step S is YES the process proceeds to step S if the determination result at step S is NO the process proceeds to step S.

At step S it is determined whether . If the determination at step S is YES the process proceeds to step S where the smaller value among the first acceleration command value and the second acceleration command value is utilized as the target acceleration command value . If the determination at step S is NO the process proceeds to step S where the smaller value among the first acceleration command value and the second acceleration command value is utilized as the target acceleration command value . At step S the drive torque command is executed based on the utilized acceleration command value. Following step S the process returns to step S and loops again. Note that this flowchart assumes looping of the process until the follow up running mode is canceled.

At step S it is determined whether . If the determination at step S is YES the process proceeds to step S where the larger value among the first acceleration command value and the second acceleration command value is utilized as the target acceleration command value . If the determination at step S is NO the process proceeds to step S where the larger value among the first acceleration command value and the second acceleration command value is utilized as the target acceleration command value . At step S the drive torque command is executed based on the utilized acceleration command value. Following step S the process returns to step S and loops again. Note that this flowchart assumes looping of the process until the follow up running mode is canceled.

The determination at step S serves as material for enabling the following vehicle B to distinguish between whether the acceleration operation of the preceding vehicle A is a normal acceleration operation or an acceleration operation counter operation in preparation for braking.

If the determination result at step S is YES the preceding vehicle A is attempting to brake and therefore the smaller value among the first acceleration command value and the second acceleration command value is utilized as the acceleration command value of the target acceleration. Thus the following vehicle B can avoid a situation that may lead to a collision with the preceding vehicle A.

If the determination result at step S is NO the preceding vehicle A is attempting to accelerate and therefore the larger value among the first acceleration command value and the second acceleration command value is utilized as the acceleration command value of the target acceleration. Thus the following vehicle B can track the preceding vehicle A without delay.

According to the present invention the vehicle speed information of the preceding vehicle A and the acceleration command value of the preceding vehicle A is communicated from the preceding vehicle A to the following vehicle B as running condition data which can improve the accuracy of the automatic follow up running control.

Although an example was described with the present embodiment in which a vehicle follows a preceding vehicle the same control can be achieved when a vehicle travels side by side with the preceding vehicle.

A third embodiment of the present invention will be described next. In the present embodiment as well the following vehicle B uses the communication unit to acquire the vehicle speed information of the preceding vehicle A and the acceleration command value of the preceding vehicle A. The second acceleration command value is obtained based on the acceleration command value acquired from the preceding vehicle A. In this case the previous Formula 13 may be used as the formula for calculating the second acceleration command value.

In the second embodiment the main control ECU calculates both of the two acceleration command values and as the acceleration command value of the following vehicle B and a control is performed so as to utilize the appropriate value among these acceleration command values depending on the estimated behavior of the preceding vehicle A. In the present embodiment a control is performed such that the second acceleration command value is utilized as the acceleration command value of the following vehicle B. Specifically in the third embodiment . Thus a control can be achieved without the determination of a deceleration command or the like.

The control process of the follow up running mode in the following vehicle B according to the third embodiment will be described next. is a flowchart of an automatic follow up control process in the vehicle control device according to the third embodiment of the present invention. Once the automatic follow up control process is initiated at step S in the process proceeds to step S where the communication unit is used to receive the vehicle speed information and the acceleration command value of the preceding vehicle A running condition data .

At step S the vehicle speed of the host vehicle following vehicle B is measured by the drive wheel sensor . Next at step S the inter vehicle distance d between the host vehicle following vehicle B and the preceding vehicle A is measured by the inter vehicle distance sensor .

At step S the second acceleration command value of the host vehicle is calculated using Formula 13 based on the vehicle speed v the vehicle speed vof the host vehicle the inter vehicle distance d and the acceleration command value of the preceding vehicle A.

At step S the second acceleration command value is utilized as the target acceleration command value .

At step S the drive torque command is executed based on the utilized acceleration command value. Following step S the process returns to step S and loops again. Note that this flowchart assumes looping of the process until the follow up running mode is canceled.

According to the present invention by calculating only to obtain the acceleration command value of the following vehicle B and setting a control can be achieved without the determination of a deceleration command or the like which is effective in cases that place particular importance on the follow up capability of the following vehicle B with respect to the preceding vehicle A such as when follow up is performed with a short inter vehicle distance.

Although an example was described with the present embodiment in which a vehicle follows a preceding vehicle the same control can be achieved when a vehicle travels side by side with the preceding vehicle.

According to the vehicle control device of the present invention when automatic follow up running is performed in a vehicle that utilizes an inverted pendulum attitude control no delay occurs in the automatic follow up running control of the following vehicle and information regarding braking is transmitted without delay to the following vehicle which can help avoid the risk of collision and realize a highly accurate automatic follow up running control. It is often more preferable for a plurality of vehicles to form a line and travel as a vehicle group from the standpoints of saving labor mitigating traffic and the like. Thus a vehicle control such as that performed by the vehicle control device of the present invention has significant industrial applicability.

