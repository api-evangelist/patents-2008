---

title: OOB (out of band) detection circuit and serial ATA system
abstract: The present invention provides an OOB detection circuit capable of making accurate signal determination even in the case where a characteristic fluctuation occurs in an analog circuit, thereby preventing deterioration in the yield of a product. To an amplitude determining circuit, a characteristic adjustment register for changing setting of an amplitude threshold adjustment mechanism for distinguishing a burst and a squelch from each other provided for the amplitude determining circuit is coupled. The characteristic adjustment register is controlled by a self determination circuit. An output of the amplitude determination circuit is supplied to a time determining circuit and also to the self determination circuit. On the basis of the output of the amplitude determining circuit, the self determination circuit controls the characteristic adjustment register.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08199858&OS=08199858&RS=08199858
owner: Renesas Electronics Corporation
number: 08199858
owner_city: Kawasaki-shi
owner_country: JP
publication_date: 20081206
---
The disclosure of Japanese Patent Application No. 2007 316547 filed on Dec. 7 2007 including the specification drawings and abstract is incorporated herein by reference in its entirety.

The present invention relates to an OOB Out Of Band detection circuit in a host and a device of a system using serial advanced technology attachment SATA .

In serial advanced technology attachment hereinbelow called SATA as a communication standard between a host of a computer and a device when a host and a device recover from a power management called PM mode or PM state state in which power consumption is returned or make a reset a specific pattern OOB pattern is transmitted from either the host or device to the other side. The receiver has to recognize that the transmitted pattern is an OOB pattern.

An OOB signal is detected by detecting a burst period and a space period squelch period . The configuration of a conventional OOB detection circuit is disclosed in FIG. 7 of Japanese Unexamined Patent Publication No. 2007 4587 patent document 1 .

As described in the patent document 1 an OOB signal detection circuit is configured as an analog circuit. There is a case such that characteristics fluctuate due to variations in wafer processes temperature and power source voltage and the analog circuit does not satisfy standards for signal determination which is predetermined by SATA. It causes deterioration in the yield of products.

The present invention is achieved to solve such a problem and an object of the invention is to provide an OOB detection circuit capable of performing accurate signal detection and preventing deterioration in the yield of products.

In a first embodiment of the present invention an OOB detection circuit has therein a self adjustment mechanism including an adjustment mechanism for adjusting characteristics of an amplitude determining circuit and a time determining circuit and a feedback mechanism for detecting outputs of the amplitude determining circuit and the time determining circuit and controlling the adjustment mechanism.

According to the embodiment even in the case where a characteristic fluctuation occurs in the amplitude determining circuit and the time determining circuit as analog circuits a threshold and response time in which the fluctuation is absorbed by the feedback control can be set by the self adjustment mechanism. Thus the OOB detection circuit capable of making accurate signal determination and preventing deterioration in the yield of products can be obtained.

Prior to explanation of the present invention the background art on detection of an OOB signal in SATA will be described with reference to .

The SATA performs communication of a differential signal of . Each of the host HS and the device DV has four ports of a Tx port a Tx port an Rx port and an Rx port. The Tx port and the Tx port are transmission side ports and the Rx port and the Rx port are reception side ports.

There are three OOB patterns COMWAKE COMINIT and COMRESET. When reset from a PM mode is desired COMWAKE is output from the host or device to the other side. In the case of hardware reset is desired from the device to the host COMINIT is output. When the host requires resetting the hardware of the device COMREST is output.

As shown in in the case of COMWAKE each of the times T and T is 106.7 ns. In COMINIT and COMRESET the time T is 106.7 ns and the time T is 320 ns.

As shown in an OOB pattern is input to the amplitude determining circuit via the Rx port and the Rx port. After performing the amplitude determination through the time determining circuit any of COMWAKE COMINIT and COMRESET is determined.

In the amplitude determining circuit and the time determining circuit standard values for determining the OOB patterns exist. show the standard values.

As shown in the amplitude range which has to be detected as a burst is 200 mV ppd or higher. The amplitude range which may be determined as burst or squelch is 75 mV or higher and less than 200 mV. The amplitude range which has to be determined as squelch is less than 75 mV ppd. ppd denotes perk to peak differential which is a unit of the signal amplitude of a differential signal.

As shown in in the squelch time standard of COMWAKE the squelch time which may be determined as COMWAKE is 35 nm or longer and less than 175 ns. The squelch time which has to be determined as COMWAKE is 101.3 ns or longer and less than 112 ns. The squelch time which should not be determined as COMWAKE is less than 35 ns and 175 ns or longer.

In the squelch time standards of COMINIT and COMRESET the squelch time which may be determined as COMINIT COMRESET is 175 ns or longer and less than 525 ns. The squelch time which has to be determined as COMINIT COMRESET is 304 ns or longer and less than 336 ns. The squelch time which should not be determined as COMINIT COMRESET is less than 175 ns and 525 ns or longer.

In the device DV since there is a case that the reference clock has to be also stopped in the PM state each of the amplitude determining circuit and the time determining circuit has to be configured by an analog circuit.

As described above each of the amplitude determining circuit and the time determining circuit has to be formed by an analog circuit which does not require a reference clock. There is the case that the standard for signal determination determined by SATA is not satisfied due to the characteristic fluctuations. The present invention is based on the technical idea of providing an adjustment mechanism hereinbelow called adjustment register for adjusting the circuit characteristics of the amplitude determining circuit and the time determining circuit in the OOB detection circuit and also providing in the circuit a feedback mechanism of controlling the adjustment mechanism on the basis of the result of the detection thereby automatically adjusting an adjustment register so that the circuit characteristic fluctuations satisfy the standards. The embodiments will be described below.

As shown in the Rx port and the Rx port are coupled to the amplitude determining circuit via signal paths P and P respectively. Between the signal path P and the ground GND a switch SWA and a termination resistor RTA are interposed. Between the signal path P and the ground GND a switch SWB and a termination resistor RTB are interposed.

The signal paths P and P are coupled to a DC amplitude generation circuit via switches SWA and SWB respectively.

The DC amplitude generation circuit has a voltage generator VG for generating various voltages by dividing the voltage between the power source VCC and the ground GND by a plurality of resistors R and a selector switch SL for selectively outputting the voltages generated by the voltage generator VG to either the signal path P or P. The setting of the selector switch SL is made by data stored in a DC amplitude adjusting register .

To the amplitude determining circuit a characteristic adjustment register adjusting mechanism for changing the settings of an amplitude threshold adjusting mechanism for distinguishing the burst and squelch from each other which is provided for the amplitude determining circuit is coupled. Specifically the amplitude threshold adjusting mechanism adjusts the threshold of amplitude determination by changing a DC reference voltage to be compared with the amplitude of a signal input from the Rx port and the Rx ports by a switch. Setting data of the switch is stored in the characteristic adjustment register . The characteristic adjustment register is controlled by a self determination circuit feedback mechanism as a digital circuit.

An output of the amplitude determining circuit is supplied to the time determining circuit and also to the self determination circuit . The self determination circuit controls the characteristic adjustment register on the basis of an output of the amplitude determining circuit .

The operation will now be described. In the normal SATA communication operation the switches SWA and SWB are in the on state and the switches SWA and SWB are in the off state so that an output of the DC amplitude generating circuit is not supplied to the amplitude determining circuit .

At the time of performing self adjustment the switches SWA and SWB are set to the off state and the switches SWA and SWB are set to the on state and in place of signals from the Rx port and Rx port a DC voltage output from the DC amplitude generating circuit is input as a differential voltage to the amplitude determining circuit .

The OOB pattern which is input in the normal operation is a data pattern in which the burst interval becomes high and low at the speed of 1.5 Gbps. A simple DC signal is used for self adjustment. For example 100 mV is output to the Rx side and 0 mV is output to the Rx side so that there is the difference between the threshold of the burst and squelch determined by the amplitude determination circuit and the threshold for determining whether the amplitude of a DC signal is large or small.

Specifically in the case of setting the threshold of the burst and squelch in the amplitude determining circuit to 125 mV ppd the threshold mV ppd at the DC amplitude is evaluated in advance and the DC amplitude adjustment register is set so as to obtain the DC amplitude. In the normal case when the threshold of the burst and squelch is set to 125 mV ppd the threshold for determining whether the amplitude of a DC signal is large or small is about 75 mV ppd.

The amplitude determining circuit outputs for example a high level signal when the input amplitude is smaller than the threshold and outputs a low level signal when the input amplitude is larger than the threshold. At the time of performing self adjustment in a state where the DC amplitude adjustment register is set so that the amplitude of the DC voltage output from the DC amplitude generating circuit becomes for example 75 mV ppd the switches SWA and SWB are turned off and the switches SWA and SWB are turned on the DC voltage is input to the amplitude determining circuit .

The self determination circuit controls the characteristic adjustment register to set the determination threshold of the DC signal in the amplitude determining circuit to the lowest. The self determination circuit receives an output of the amplitude determining circuit and determines the level high or low of the output.

Since the determination threshold is initially set to the lowest the output of the amplitude determining circuit is at the low level. The self determining circuit increases the setting of the characteristic adjustment register step by step until an output of the amplitude determining circuit becomes the high level and stops changing the setting with a register value by which the output of the amplitude determining circuit changes from the low level to the high level.

The determination threshold of the DC signal in the amplitude determining circuit set by the register value at this time is an actual threshold in the case where the threshold of burst and squelch is set to 125 mV ppd. Since the value is a value in which the characteristic fluctuations in the amplitude determining circuit are absorbed the register value of the characteristic adjustment register at this time is used in the normal communication operation. In such a manner the threshold of the burst and squelch can be set to a value around 125 mV ppd as a target value.

As described above the amplitude generating circuit for generating a DC signal having an arbitrary amplitude from a DC voltage is provided in the OOB detection circuit . By inputting the generated DC signal as a test signal to the amplitude determining circuit and adjusting a determination threshold by feedback operation even in the case where the circuit characteristics of the amplitude determining circuit fluctuate a threshold in which the fluctuations are absorbed can be obtained.

The example of setting the set value of the characteristic adjustment register so that the determination threshold of the DC signal becomes the lowest and increasing the set value of the characteristic adjustment register step by step has been described. The set value of the characteristic adjustment register may be also set so that the determination threshold of the DC signal becomes the maximum and may be decreases step by step. The set value of the characteristic adjustment register may be set so that the determination threshold of the DC signal becomes an intermediate value between the maximum and minimum values and may be increased or decreased step by step.

As shown in an output signal from the amplitude determining circuit is supplied to the time determining circuit via the input selector SL. The time determining circuit has therein a squelch time measuring circuit configured by an analog circuit and a squelch interval count circuit as a digital circuit.

The squelch time measuring circuit receives an output signal from the amplitude determining circuit sets any of a WAKE SHORT signal a WAKE LONG signal an INIT SHORT signal and an INIT LONG signal to the high level and supplies the resultant signal to the squelch interval count circuit and also to a time measurement count circuit of the self determining circuit feedback mechanism . Response time in the squelch time measuring circuit can be adjusted by for example setting so that a resistance value of a resistor that specifies time constant of an internal RC circuit or a capacitance value of a capacitor can be changed by changing the set value of a characteristic adjustment register adjusting mechanism .

The squelch interval count circuit is a digital circuit for counting that the squelch interval of specific time is input three times or more determines the signal indicating that the squelch interval was input three times or more as any of COMWAKE COMINIT and COMRESET and supplies the determined signal to a predetermined logic circuit. To the squelch interval count circuit an output of the input selector SL is directly supplied.

The self determining circuit has the time measurement count circuit for receiving the WAKE SHORT signal the WAKE LONG signal the INIT SHORT signal and the INIT LONG signal and measuring the low period in each of the signals by using a clock a count value comparing circuit for comparing a count value of the time measurement count circuit and a comparison count value stored in a comparison count value register and a pattern generating circuit for generating a self determination input pattern pulse pattern . The self determination input pattern output from the pattern generating circuit is supplied to the input selector SL but is not selected in the normal operation.

The value of the characteristic adjustment register is set on the basis of a comparison result of the count value comparing circuit .

The operation will now be described. The OOB detection circuit has to determine an OOB pattern input from the Rx port and the Rx port to be any of COMWAKE COMINIT and COMRESET. A specification is set for each of the shorter squelch interval and the longer squelch interval in a pattern to be determined.

Specifically in the OOB pattern as described with reference to in the case of COMWAKE the threshold of the squelch time for determining that the input pattern is COMWAKE has to be 35 ns or longer and less than 101.3 ns on the shorter side and has to be 112 ns or longer and less than 175 ns on the longer side.

In the case where the WAKE SHORT signal output from the squelch time measuring circuit is at the low level it expresses that the squelch time has not reached the thresholds on the shorter side. In the case where the WAKE SHORT signal is at the high level it expresses that the squelch time exceeds the threshold value on the shorter time. Therefore the WAKE SHORT signal is a signal which should become the high level within time which is 35 ns or longer and less than 101.3 ns since the squelch interval starts since the input becomes the high level .

When the WAKE LONG signal is at the low level it shows that squelch time has not reached the threshold on the longer side. When the WAKE LONG signal becomes the high level it shows that the squelch time exceeds the threshold on the longer side. Therefore the WAKE LONG signal is a signal which should becomes the high level after 112 ns and before 175 ns since the squelch starts.

Therefore in the case where the WAKE SHORT signal is at the high level and the WAKE LONG signal is at the low level the input pattern is COMWAKE.

The INIT SHORT signal and the INIT LONG signal output from the squelch time measuring circuit are used for determining COMINIT and COMRESET. The threshold value on the short side of the squelch time for determining whether an input pattern is COMINIT COMRESET or not has to be 175 ns or longer and less than 304 ns. The threshold value on the long side has to be 336 ns or longer and less than 525 ns.

The INIT SHORT signal at the low level expresses that the squelch time has not reached the threshold on the short side. The INIT SHORT signal at the high level expresses that the squelch time exceeds the threshold on the short side. Therefore the INIT SHORT signal is a signal which should become the high level after 175 ns and before 304 ns since the squelch interval starts since the input signal becomes high .

The INIT LONG signal at the low level expresses that the squelch time has not reached the threshold on the long side. The INIT LONG signal at the high level expresses that the squelch time exceeds the threshold on the long side. Therefore the INIT LONG signal is a signal which should become the high level after 336 ns and before 525 ns since the squelch starts.

Therefore in the case where the INIT SHORT signal is at the high level and the INIT LONG signal is at the low level it expresses that the input pattern is COMINIT or COMRESET.

Since the squelch time measuring circuit is an analog circuit the operation may fluctuate according to process temperature and voltage and there is a case that all of the signals do not lie in the standard. The configuration of absorbing the influence of fluctuations in the circuit characteristics is the self adjusting mechanism.

In the case of performing the self adjustment an input pattern for self determination generated by the pattern generating circuit in the self determining circuit is selected by the input selector SL and input to the squelch time measuring circuit .

In the input pattern for self determination is a pattern in which the period of known time T first period is at the low level. The WAKE SHORT signal has a pattern in which the period of time T second period is at the low level. The WAKE LONG signal has a pattern in which the period of time T second period is at the low level. The INIT SHORT signal has a pattern in which the period of time T second period is at the low level. The INIT LONG signal has a pattern in which the period of time T second period is at the low level. The time T is the shortest and the time T is the longest. In the above example the times T to T show the period in which the potential is at the low level. Alternatively the times T to T may show the period of the high level.

For example in the WAKE SHORT signal the time T is time obtained by adding the known time T given by the input pattern for self determination and time determined by the circuit characteristic of the squelch time measuring circuit 35 ns or longer and less than 101.3 ns . When the time T becomes longer than that it means that the circuit characteristic of the squelch time measuring circuit changes and response time becomes longer and does not meet the standard.

Consequently the count values of the times T to T in the case where the response time meets the standard are pre stored in the comparison count value register . By comparing the count value in the time measurement count circuit with the value stored in the comparison count value register in the count value comparing circuit whether the response time meets the standard or not is determined. If the response time does not meet the standard the set value of the characteristic adjustment register is changed to adjust the response time of the squelch time measuring circuit .

Concretely first in a state where the characteristic adjustment register is set so that the response time of the squelch time measuring circuit becomes the shortest the input pattern for self determination is supplied from the pattern generating circuit to the squelch time measuring circuit .

The times T to T in the four signals WAKE SHORT WAKE LONG INIT SHORT and INIT LONG output from the squelch time measuring circuit are counted by the time measurement count circuit .

In practice it is unnecessary to count all of the four signals but is sufficient to count the time T in the signal WAKE LONG and the time T in the signal INIT LONG.

The count comparing circuit compares the count result with the value of the comparison count value register .

Since the response time of the squelch time measuring circuit is set to the shortest the count value becomes smaller than the register value. In this case feedback control is performed in such a manner that the setting of the characteristic adjustment register is changed to increase the response time of the squelch time measuring circuit .

The first stage of the response time of the squelch time measuring circuit various among the times T to T and is for example about 3 ns in the time T about 8 ns in the time T about 12 ns in the time T and about 25 ns in the time T.

As described above in the case of counting only the time T or T the characteristic adjustment register is configured so that when the setting in the time T is changed by one stage the setting in the time T changes by one stage and when the setting in the time T is changed by one stage the setting in the time T changes by one stage. The configuration of the characteristic adjustment register can be simplified.

After changing the setting of the characteristic adjustment register the pattern for self determination is supplied again to the squelch time measuring circuit counting of the times T to T in the four signals output from the squelch time measuring circuit and comparison of the count values are repeated and the changing of the setting is stopped with a register value when the count value exceeds the register value. The response time of the squelch time measuring circuit set by the register value at this time is response time in which the influence of fluctuations in the circuit characteristics is absorbed.

Therefore by using the set value of the characteristic adjustment register at this time for the normal communication operation all of the four output signals WAKE SHORT WAKE LONG INIT SHORT and INIT LONG from the squelch time measuring circuit can be set to response time meeting the standard.

As described above the input pattern for self determination is generated in the OOB generation circuit and is supplied to the squelch time measuring circuit in the time determining circuit and the response time of the squelch time measuring circuit is adjusted by the feedback control. As a result even in the case where the circuit characteristics of the time determining circuit fluctuate the response time in which the fluctuations are absorbed can be set.

The example where the set value of the characteristic adjustment register is set so that the response time of the squelch time measuring circuit becomes the shortest and the setting of the characteristic adjustment register is changed step by step has been described. It is also possible to set so that the response time of the squelch time measuring circuit becomes the longest and change the setting of the characteristic adjustment register step by step. It is also possible to set so that the response of the squelch time measuring circuit becomes an intermediate value between the shortest and longest times and change the setting of the characteristic adjustment register step by step.

The squelch interval count circuit in the post stage of the squelch time measuring circuit is a conventional digital circuit for counting that the squelch interval of specific time is input three times or more and is not the object of self adjustment of the invention. Consequently the squelch interval count circuit will not be described.

As described above in the OOB detection circuit of the first embodiment of the present invention by adding the self adjustment mechanism to each of the amplitude determining circuit and the time determining circuit even in the case where a characteristic fluctuation occurs in the amplitude determining circuit and the time determining circuit as analog circuits a threshold and response time in which the fluctuation is absorbed by feedback control can be set. Therefore the OOB detection circuit capable of making accurate signal determination and preventing deterioration in the yield of products can be obtained.

Although each of the amplitude determining circuit and the time determining circuit has the self adjustment mechanism in the above description the self adjustment mechanism may be added to only one of the amplitude determining circuit and the time determining circuit . By providing the self adjustment mechanism for one of the circuits in which the characteristic fluctuation occurs more frequently an effect similar to the above can be produced.

The self adjustment operation of the OOB detection circuit may be performed on start of operation of an LSI or at a proper timing in the operation.

In a second embodiment of the present invention in the SATA system having the OOB detection circuit described in the first embodiment self adjustment of the amplitude determining circuit and the time determining circuit in the OOB detection circuit is performed. A CPU Central Processing Unit recognizes a result of the self adjustment and starts SATA communication.

As shown in the microcomputer has an MPU Micro Processing Unit module MP a register group RS for transmitting receiving a predetermined set value to from a CPU via a bus controller in the MPU module MP a code memory as a RAM or ROM CM storing a program for the bus controller and an SATA module SM.

The self determination circuit in the OOB detection circuit described with reference to is included in the SATA module SM and the self determination circuit and the register group RS are coupled to each other. The register group RS includes an SATA communication start bit register RS a self adjustment execution flag register RS and the characteristic adjustment registers and shown in . These are capable of being accessed from the CPU via the bus controller .

In the SATA module SM a Tx driver for outputting an SATA Tx signal to the Tx port and the Tx port is shown.

The MPU module MP is provided with an interrupt port P for receiving a self adjustment completion interrupt pulse signal PS output from the self determination circuit .

Next self adjustment result recognizing operation in the microcomputer will be described with reference to and using a timing chart of .

Until the CPU sets an SATA communication start bit in the SATA communication start bit register RS the SATA module SM does not respond even if an SATA Rx signal is received from the Rx port and Rx port so that the SATA communication does not start.

On the other hand when the SATA communication start bit register RS is set the SATA module SM transmits COMRESET COMINIT as the SATA Tx signal to the Tx port and the Tx port to start the SATA communication.

Therefore by executing a self adjustment work before the SATA communication start bit is set in the SATA communication start bit register RS the OOB detection circuit can be adjusted before the SATA communication starts.

Specifically before the SATA communication start bit is set the CPU sets a self adjustment execution flag in the self adjustment execution flag register RS on the basis of the program. The self determination circuits and described with reference to adjust the amplitude determining circuit and the time determining circuit respectively. During execution of self adjustment the set values in the characteristic adjustment registers and change as the process advances. For example a set value which is a before the self adjustment becomes a set value b c and d and finally becomes a set value e .

In the self determination circuits and a self adjustment sequence is assembled in a digital circuit. When the sequence reaches the final process the self adjustment is completed. Consequently the self determination circuits and automatically clear the self adjustment execution flag in the self adjustment execution flag register RS and output the self adjustment completion interrupt pulse PS to the MPU module MP.

After detection of the self adjustment completion interrupt pulse PS the CPU can recognize the set value e of the characteristic adjustment register as a self adjustment result. When it is determined that there is no problem the CPU sets the SATA communication start bit in the SATA communication start bit register RS transmits COMRESET COMINIT and starts the SATA communication.

In the case where there is a problem in the adjustment result the CPU can rewrite the set value of the characteristic adjustment register .

As described above by employing the configuration that the self adjustment of the amplitude determining circuit and the time determining circuit in the OOB detection circuit is performed and the CPU recognizes the self adjustment result and starts the SATA communication the self adjustment can be performed automatically prior to the SATA communication. Occurrence of a communication error due to a characteristic fluctuation in the amplitude determining circuit and the time determining circuit can be prevented.

The microcomputer described in the second embodiment employs the configuration that the CPU recognizes the self adjustment result and starts the SATA communication. In a third embodiment a configuration that the SATA communication can be started without recognition of the self adjustment result by the CPU will be described.

As shown in the microcomputer has the SATA communication start bit register RS as a register which can be accessed from the CPU . The self determination circuit in the OOB detection circuit described with reference to has the self adjustment execution flag register RS and the characteristic adjustment register shown in . The characteristic adjustment register may be provided on the outside of the self determination circuit as shown in .

The microcomputer also has an SATA logic circuit LG for setting the self adjustment execution flag in the self adjustment execution flag register RS in response to the setting of the CPU to the SATA communication start bit register RS.

The self adjustment operation of the microcomputer will now be described by using the timing chart of with reference to .

When the CPU sets the SATA communication start bit in the SATA communication start bit register RS the SATA logic circuit LG as hardware automatically sets the self adjustment execution flag in the self adjustment execution flag register RS. In response to the setting the self determination circuits and described with reference to adjust the amplitude determining circuit and the time determining circuit respectively. During execution of self adjustment the set values of the characteristic adjustment registers and change as the process advances. For example a set value which is a before the self adjustment becomes a set value b c and d and finally becomes a set value e .

Even if an SATA Rx signal is received from the Rx port and the Rx port the SATA module SM does not respond to the signal until the self adjustment execution flag of the self adjustment execution flag register RS is cleared. Consequently the SATA communication is not started.

The SATA logic circuit LG has the function of automatically clearing the self adjustment execution flag in the self adjustment execution flag register RS in response to end of the self adjustment sequence in the self determination circuits and . After clearing the self adjustment execution flag the SATA logic circuit LG transmits COMRESET COMINIT as the SATA Tx signal to the Tx port and the Tx port.

As described above in the microcomputer after setting the SATA communication start bit the CPU does not perform the self adjustment work. During a predetermined period the CPU determines the end of the self adjustment work in the SATA module SM and starts the SATA communication as soon as the self adjustment is finished. The program stored in the code memory CM does not have to include a program related to the self adjustment work so that it is earlier for the user to develop a program.

