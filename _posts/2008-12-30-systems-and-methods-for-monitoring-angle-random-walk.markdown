---

title: Systems and methods for monitoring angle random walk
abstract: A gyroscope for determining an angular rate output. The gyroscope includes a first demodulator configured to demodulate an angular rate measurement at a first bias modulation frequency to determine the angular rate signal and a second demodulator configured to demodulate the angular rate measurement at a second bias modulation frequency to provide a signal with ARW information. The gyroscope further includes an ARW estimator that provides an output that is proportional to ARW that is then stored in a memory. The second bias modulation frequency is an even order harmonic of the first bias modulation frequency.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07889351&OS=07889351&RS=07889351
owner: Honeywell International Inc.
number: 07889351
owner_city: Morristown
owner_country: US
publication_date: 20081230
---
The invention described herein was made in the performance of work under U.S. Government Contract No. N00030 05 C 0063 awarded by the United States Navy. The Government may have rights to portions of this invention.

An important requirement for a fiber optic gyro FOG is the ability to monitor its health status or accuracy for health diagnostics. For most navigation systems including FOGs angle random walk ARW is a major contributor to navigation errors. ARW is measured in units of degrees per root unit time that directly affects angular rate calculations independent from other types of error e.g. scale factor or bias error .

ARW monitors can provide valuable information for health diagnostics. Current systems and methods utilized to monitor ARW indirectly only monitor parameters affecting ARW instead of actual ARW. These indirect ARW determinations can lead to additional support costs as well accuracy issues including false alarms or false negatives. These systems also require a large number of parameter monitoring devices that negatively increase system size weight and power consumption.

The present invention relates to a gyroscope for measuring an angular rate output. In accordance with one aspect of the invention the gyroscope includes a first component configured to demodulate an angular rate measurement at a first modulation frequency to determine the angular rate output and a second component configured to demodulate the angular rate measurement at a second modulation frequency to determine an ARW output. The gyroscope also includes a memory configured to store the ARW output.

In accordance with another aspect of the invention the second modulation frequency is an even order harmonic of the first modulation frequency.

In accordance with a further aspect of the invention the gyroscope also includes a filter for filtering an angular rate measurement input of the second demodulator.

The present invention is a gyroscope having a component for measuring angle random walk ARW of an angular rate output. illustrates a simplified closed loop architecture of a Fiber Optic Gyroscope FOG formed in accordance with an exemplary embodiment of the present invention. The FOG includes a rotation sensing loop having an integrated optics circuit IOC . The FOG also includes a photodetection circuit PDC a signal processing circuit SPC with an ARW monitor and an integrated optics drive circuit IODC .

The FOG measures an angular velocity or a velocity about a particular axis of rotation by determining a difference in phase between two beams of light travelling in opposite directions e.g. clockwise CW and counterclockwise CCW directions around fiber optic coils of the IOC . An analog phase output signal from the IOC is communicated to the PDC . The PDC amplifies and converts the analog phase output signal to modulated digital phase shift data. The digital phase shift data of the PDC is then communicated to the SPC . The SPC demodulates monitors for ARW integrates and then communicates the integrated result to the IODC . The IODC converts the signal received from the SPC to analog phase shift data amplifies it and then communicates the amplified analog phase shift data to the IOC through a feedback loop. The IOC then utilizes the received analog phase shift data to cancel a phase shift between the two beams of light travelling around the optical coils of the IOC .

In an embodiment both the rate demodulator and the ARW demodulator receive the digital phase shift data from the PDC . The ARW demodulator is biased at a predetermined modulation frequency such that no adverse rotational rate or mechanical vibrational signals affect the signal being demodulated. By biasing the ARW demodulator at this predetermined frequency the only noise affecting a modulated signal received from an IOC is related to ARW. The precise selection of the predetermined modulation frequency is critical to determining real ARW because the frequency band surrounding the bias modulation frequency of the rate demodulator is corrupted by real rotation rates whereas much higher frequency bands are corrupted by mechanical vibrations.

Depending on the application the rotation rates can be from baseband to a few hertz or DC to hundreds of hertz. Vibration signals can range from a few hertz to a couple of kilohertz. Acoustic induced signals can range from tens of hertz to several kilohertz. All of these ranges are about the bias modulation frequency or odd harmonics of the bias modulation frequency.

At even harmonics frequencies of the bias modulation frequency a noise measurement of a demodulated signal is essentially void of rotation or vibration signals. Therefore by selecting a bias modulation frequency within narrow bands surrounding these even harmonics a demodulated signal can provide real ARW information. In an embodiment the ARW demodulator is biased at two times the bias modulation frequency of the rate demodulator . In another embodiment the ARW demodulator is biased at four times the bias modulation frequency of the rate demodulator .

As shown in the ARW Output from the ARW demodulator is not a signal that is proportional to ARW but rather it s root variance standard deviation is proportional to ARW. Therefore to get a signal that is proportional to ARW an additional function is performed to the output of the ARW demodulator . In one embodiment the added function could be a standard deviation calculation or some other similar method that is related to the variance such as a Fast Fourier Transform based spectral density. This function can reside in either the gyro processor SPC a system processor not shown gyros integrated into a bigger system such as an inertial navigation unit IMU or in a customer s system not shown . The ARW estimator performs the function that gives an output that is proportional to ARW. Then the output of the ARW estimator is sent to memory. It is unlikely but possible that the output of the ARW demodulator will go directly to memory because the data rates at this point are very high 40 kHz or higher and therefore would require too much memory.

In one embodiment the memory is included in an external health monitoring device not shown where the received proportional ARW output is tracked to determine the overall health of the FOG .

The signal from the ARW demodulator is filtered to select out a predetermined frequency band to further reduce any influence from corrupting signals. For example the ARW monitor may have some corrupting signals at very low frequencies well below 1 Hz due to optical glitches caused by the IOC . The filter has a pass band that is optimized to pass only those frequency components that has ARW information void of corrupting signals.

In another embodiment the filter includes processing circuitry that facilitates application of a fast Fourier transform FFT to transform received data between the time and frequency domains. The bandpass filter or FFT help to reduce unwanted signal components related to real rotation and vibration information and modulation induced errors such as optical glitches from the IOC.

While the preferred embodiment of the invention has been illustrated and described as noted above many changes can be made without departing from the spirit and scope of the invention. Accordingly the scope of the invention is not limited by the disclosure of the preferred embodiment. Instead the invention should be determined entirely by reference to the claims that follow.

