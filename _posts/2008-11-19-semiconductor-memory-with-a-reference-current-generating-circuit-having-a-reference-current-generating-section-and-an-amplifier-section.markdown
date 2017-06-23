---

title: Semiconductor memory with a reference current generating circuit having a reference current generating section and an amplifier section
abstract: A semiconductor memory capable of storing and reading data in a memory cell for holding the data corresponding to a threshold voltage has a reference current generating circuit having a reference current generating section and an amplifier section.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07751252&OS=07751252&RS=07751252
owner: Kabushiki Kaisha Toshiba
number: 07751252
owner_city: Tokyo
owner_country: JP
publication_date: 20081119
---
This application is based upon and claims the benefit of priority from the prior Japanese Patent Application No. 2007 300268 filed on Nov. 20 2007 the entire contents of which are incorporated herein by reference.

The present invention relates to a semiconductor memory for example a nonvolatile semiconductor memory such as a NOR flash memory including a reference current generating circuit.

A NOR flash memory of the prior art includes for example a reference current generating circuit for supplying a reference current to a sense amplifier for example see Japanese Patent Laid Open No. 2004 103211 . The reference current generating circuit includes for example a reference cell a current mirror circuit connected to the reference cell and an output section which is fed with a current obtained by current mirroring a current passing through the reference cell from the current mirror circuit.

In the reference current generating circuit for example the initial potential of the reference current is a ground potential at the output section. Then the output section is charged by a MOS transistor making up the current mirror circuit.

An amount of charge required for charging is determined by a potential difference the ground potential a direct current potential reached by the output section a parasitic capacitance. In this case charging from the current mirror circuit is interrupted by the discharge of an output MOS transistor which makes up the output section and is diode connected.

Thus the closer to the direct current potential reached by the output section the longer the discharge time. In other words in the prior art the rate of rise of the reference current cannot be increased.

According to one aspect of the present invention there is provided a semiconductor memory capable of storing and reading data in a memory cell for holding the data corresponding to a threshold voltage comprising a reference current generating circuit having a reference current generating section and an amplifier section 

a first MOS transistor of first conductivity type which has one end connected to a power supply and is diode connected 

a reference cell which is connected to an other end of the first MOS transistor and ground has a word line fed with a predetermined voltage and is configured as the memory cell 

a second MOS transistor of the first conductivity type which has one end connected to the power supply and is fed with a current obtained by current mirroring a current passing through the first MOS transistor and

a third MOS transistor of second conductivity type which is connected between an other end of the second MOS transistor and the ground and has a gate connected to the other end of the second MOS transistor 

a fourth MOS transistor of the first conductivity type which has one end connected to the power supply and is diode connected 

a fifth MOS transistor of the second conductivity type which is connected between an other end of the fourth MOS transistor and the ground and has a gate connected to an output terminal 

a sixth MOS transistor of the first conductivity type which has one end connected to the power supply and is fed with a current obtained by current mirroring a current passing through the fourth MOS transistor 

a seventh MOS transistor of the second conductivity type which is connected between an other end of the sixth MOS transistor and the ground and has a gate connected to the gate of the third MOS transistor 

an eighth MOS transistor of the first conductivity type which has one end connected to the power supply and is fed with a current obtained by current mirroring the current passing through the fourth MOS transistor 

a ninth MOS transistor of the second conductivity type which is connected between an other end of the eighth MOS transistor and the ground and has a gate connected to the other end of the eighth MOS transistor 

a tenth MOS transistor of the first conductivity type which has one end connected to the power supply an other end connected to the output terminal and a gate connected to the other end of the sixth MOS transistor and

an eleventh MOS transistor of the second conductivity type which is connected between the other end of the tenth MOS transistor and the ground and has a gate connected to the other end of the eighth MOS transistor 

the amplifier section outputting a reference current from the output terminal to a wire in response to an output of the reference current generating section.

The present invention is applied to for example a nonvolatile semiconductor memory such as a NOR flash memory in which data can be stored in and read from a memory cell for storing data corresponding to a threshold voltage. Thus it is possible to increase the rate of rise of a reference current used for for example reading in the memory cell of the NOR flash memory.

Embodiments to which the present invention is applied will be described below with reference to the accompanying drawings.

As shown in a semiconductor memory includes a deep power down control circuit a reference potential generating circuit a pump circuit a reference period generating circuit a counter circuit a reference current control circuit a reference current generating circuit a sense amplifier a test leak source a switch circuit and a memory cell .

The deep power down control circuit outputs a deep power down signal DPD for deactivating the pump circuit and the reference period generating circuit to minimize current consumption. The semiconductor memory of the present embodiment has two current saving modes of a deep power down state and a standby state. The deep power down state is defined as a state having smaller current consumption than in the standby state.

The pump circuit boosts a power supply voltage in response to a signal ROSCE and outputs a potential VDDR to be supplied to a word line connected to the memory cell and a word line connected to a reference cell. The pump circuit boosts the potential VDDR to a desired set value based on a reference potential VREF outputted from the reference potential generating circuit . The pump circuit is deactivated in response to the deep power down signal DPD.

The reference period generating circuit outputs a pulse signal REFOSC having a fundamental period of for example 1 us in response to a signal PONEND0B outputted from the pump circuit and a signal RESTART outputted from the reference current control circuit . The reference period generating circuit is deactivated in response to the deep power down signal DPD.

The counter circuit counts the pulse signals REFOSC in response to the signal RESTART and outputs a refresh pulse signal REFRESH for each refresh period e.g. 400 us . The refresh pulse signal REFRESH is a signal for specifying a refresh state for recharging a wire which is fed with a reference current distributed potential IREFNCH.

The counter circuit outputs a signal RTIMER for specifying a predetermined time in this case e.g. 1 us in response to the signal RESTART.

The reference current control circuit outputs a signal REFSW and an enable signal REFENB in response to the refresh pulse signal REFRESH a read signal R ACTIVE for specifying a reading state a verification signal A ACTIVE for specifying a verifying state the signal RTIMER and a signal LAT for specifying a latching operation of the sense amplifier . The reference current control circuit outputs the enable signal REFENB when entering a reading operation a verifying operation and a refreshing state during standby.

The reference current generating circuit is activated in response to the enable signal REFENB and outputs the reference current distributed potential IREFNCH. The reference current generating circuit is deactivated in synchronization with the deactivation of the reference period generating circuit during deep power down and standby.

The sense amplifier compares a cell current Icell passing through the memory cell and a reference current Iref and outputs the comparison result. Based on the comparison result data stored in the memory cell is read. The sense amplifier is deactivated during deep power down and standby.

The switch circuit is connected between the reference current generating circuit and the wire connected to the sense amplifier . The switch circuit is controlled to be turned on off in response to the signal REFSW and can stop the supply of the reference current distributed potential IREFNCH from the reference current generating circuit to the wire .

The memory cell is made up of a nonvolatile transistor for example an EEPROM cell for storing data corresponding to a threshold value. The memory cell has a word line fed with the potential VDDR. When the potential VDDR is applied to the word line the cell current Icell corresponding to the threshold voltage passes through the memory cell .

When the reference current generating circuit is powered on the wire is temporarily charged and the switch circuit is turned off. It is therefore possible to keep the potential of the wire at a desired value. After that when the reference current distributed potential IREFNCH is necessary in a reading operation the potential of the wire is kept to some extent thereby eliminating the need for charging from the ground potential and increasing the rate of rise of the potential.

The potential of the wire may be changed by a leakage current and the like when the switch circuit is turned off. Thus the refreshing operation is necessary in each fixed period.

In the case of a multivalued memory cell for example four threshold value distributions are set for each memory cell. The spacing between the threshold value distributions tends to be smaller than in a binary memory cell. Since the spacing between the threshold value distributions is small in a multivalued memory cell the reference current Iref has to be set more accurately than in a binary memory cell.

Further in a reading operation a difference between the reference current Iref and the cell current Icell of the memory cell is smaller than in a binary memory cell so that it takes a long time to determine data. It is therefore necessary to quickly prepare the reference current IREFNCH to absorb an increased determination time.

The following will describe an example of the configuration of the reference current generating circuit in the semiconductor memory configured thus.

As shown in the reference current generating circuit includes a reference current generating section and an amplifier section for outputting the reference current IREFNCH from an output terminal to the wire in response to the output of the reference current generating section.

The reference current generating section includes pMOS transistors a a a and a nMOS transistors a a and a and a reference cell a.

The pMOS transistor a has the gate fed with the enable signal REFENB and is controlled to be turned on off in response to the enable signal REFENB.

The PMOS transistor a has one end source connected to a power supply via the pMOS transistor a. The pMOS transistor a is diode connected.

The nMOS transistor a has one end drain connected to the other end drain of the pMOS transistor a. The threshold voltage of the nMOS transistor a is set around 0 V. A fixed voltage BIAS not lower than the threshold voltage is applied to the gate of the nMOS transistor a.

The reference cell a is connected between the other end source of the nMOS transistor a and the ground. The potential VDDR is applied to the word line of the reference cell a. The reference cell a is configured as the memory cell . The plurality of reference cells a may be connected in series so as to raise a cell current Icellxn at high speed.

The pMOS transistor a has the gate fed with the enable signal REFENB and is controlled to be turned on off in response to the enable signal REFENB.

The pMOS transistor a has one end source connected to the power supply via the pMOS transistor a and the gate connected to the gate of the pMOS transistor a. Thus the pMOS transistor a is fed with a current Icellxm obtained by current mirroring the current Icellxn passing through the pMOS transistor a.

The nMOS transistor a has one end drain connected to the other end drain of the pMOS transistor a. The threshold voltage of the nMOS transistor a is set around 0 V. The fixed voltage BIAS not lower than the threshold voltage is applied to the gate of the nMOS transistor a.

The nMOS transistor a is connected between the other end source of the nMOS transistor a and the ground. The nMOS transistor a has the gate connected to the other end drain of the pMOS transistor a.

As shown in the amplifier section includes pMOS transistors b b b b b b b and b nMOS transistors b b b b b and b and input MOS transistors b and b.

The pMOS transistor b has the gate fed with the enable signal REFENB and is controlled to be turned on off in response to the enable signal REFENB.

The pMOS transistor b has one end source connected to the power supply via the pMOS transistor b. The pMOS transistor b is diode connected.

The nMOS transistor b has one end drain connected to the other end drain of the pMOS transistor b. The threshold voltage of the nMOS transistor b is set around 0 V. The fixed voltage BIAS not lower than the threshold voltage is applied to the gate of the nMOS transistor b.

The input MOS transistor b is connected between the other end source of the nMOS transistor b and the ground. The gate of the input MOS transistor b is connected to the output terminal . In other words the gate of the input MOS transistor b acts as the non inverting input terminal of the amplifier section

The pMOS transistor b has the gate fed with the enable signal REFENB and is controlled to be turned on off in response to the enable signal REFENB.

The pMOS transistor b has one end source connected to the power supply via the PMOS transistor b and the gate connected to the gate of the pMOS transistor b. Thus the pMOS transistor b is fed with a current Icellxi obtained by current mirroring a current Icellxi passing through the pMOS transistor b.

The nMOS transistor b has one end drain connected to the other end drain of the pMOS transistor b. The threshold voltage of the nMOS transistor b is set around 0 V. The fixed voltage BIAS not lower than the threshold voltage is applied to the gate of the nMOS transistor b.

The input MOS transistor b is connected between the other end source of the nMOS transistor b and the ground. The gate of the input MOS transistor b is connected to the gate of the nMOS transistor a. In other words the gate of the input MOS transistor b acts as the inverting input terminal of the amplifier section

The pMOS transistor b has the gate fed with the enable signal REFENB and is controlled to be turned on off in response to the enable signal REFENB.

The pMOS transistor b has one end source connected to the power supply via the pMOS transistor b and the gate connected to the gate of the pMOS transistor b. Thus the pMOS transistor b is fed with the current Icellxi obtained by current mirroring the current Icellxi passing through the pMOS transistor b.

The nMOS transistor b has one end drain connected to the other end drain of the pMOS transistor b. The threshold voltage of the nMOS transistor b is set around 0 V. The fixed voltage BIAS not lower than the threshold voltage is applied to the gate of the nMOS transistor b.

The nMOS transistor b is connected between the other end source of the nMOS transistor b and the ground. The nMOS transistor b has the gate connected to the other end drain of the pMOS transistor b.

The pMOS transistor b has the gate fed with the enable signal REFENB and is controlled to be turned on off in response to the enable signal REFENB.

The pMOS transistor b has one end source connected to the power supply via the pMOS transistor b and the gate connected to the other end drain of the pMOS transistor b. With this configuration a gate voltage inputted to the pMOS transistor b is at the same potential as the gate voltage of the pMOS transistor a and the pMOS transistor b is fed with a current Icellxj equal to the current Icellxn passing through the pMOS transistor a.

The other end drain of the pMOS transistor b is connected to the output terminal . The pMOS transistor b has a larger size than the other pMOS transistors a a b b and b.

The nMOS transistor b has the gate fed with a signal REFEN which is the inverted signal of the enable signal REFENB and is controlled to be turned on off in response to the signal REFEN.

The nMOS transistor b has one end drain connected to the other end drain of the pMOS transistor b. The nMOS transistor b has the other end source connected to the ground via the nMOS transistor b.

The nMOS transistor b has the gate connected to the gate of the nMOS transistor b. Thus the nMOS transistor b is fed with the current Icellxj obtained by current mirroring the current Icellxi passing through the nMOS transistor b. The other end drain of the nMOS transistor b is connected to the output terminal . The nMOS transistor b has a larger size than the other nMOS transistors a b b and b.

In the reference current generating circuit configured thus for example the pMOS transistor a a b b and b are set to have the same size. Further for example the pMOS transistors a a b b and b are set to have the same size. Moreover for example the nMOS transistors a a b b and b are set to have the same size. Further for example the nMOS transistors a b b and b are set to have the same size.

In this case the other end drain of the pMOS transistor b is set at the same potential as a potential IREFPCH1 of the other end drain of the PMOS transistor a by current mirroring. Further the other end drain of the pMOS transistor b is set at the same potential as the potential IREFPCH1 of the other end drain of the PMOS transistor a by current mirroring.

The amplifier section configured thus feeds back a potential to be inputted to the input MOS transistor b from the output terminal such that the potential is equal to a potential IREFNCH0.

The amplifier section controls the potential of the output terminal by charging the output terminal from the PMOS transistor b and discharging the output terminal from the nMOS transistor b.

For example in the case of an overshoot of an output signal the potential of the output terminal from a target the capability of the nMOS transistor b is increased and then a current is drawn. On the other hand in the case of an undershoot of the output signal the potential of the output terminal from a target the capability of the pMOS transistor b is increased and then a current is passed.

Thus high speed control can be achieved as compared with the prior art in which a fixed current is drawn by a current mirror scheme.

As described above the pMOS transistor b and the nMOS transistor b are larger in size than the other MOS transistors with faster operations.

Thus the potential of the output terminal wire can rise faster than in the current mirror scheme of the prior art.

As described above the semiconductor memory of the present embodiment can increase the rate of rise of the reference current. Particularly since the reference current can quickly rise the reading operation can be performed faster in the foregoing multivalued memory cell.

The first Embodiment described an example of the configuration for increasing the rate of rise of the reference current. The present embodiment will particularly describe another example of the configuration of the reference current generating circuit for increasing the rate of rise of the reference current.

As shown in unlike the reference current generating circuit of the first embodiment the reference current generating circuit further includes a potential holding circuit a first oscillation preventing circuit a second oscillation preventing circuit and a bit line resistor . Other configurations are the same as in the reference current generating circuit of the first embodiment.

The pMOS transistor d is connected between a power supply and the gate of a pMOS transistor a. The pMOS transistor d has the gate fed with a signal REFEN which is the inverted signal of an enable signal REFENB and is controlled to be turned on off in response to the signal REFEN.

The pMOS transistor d has one end source connected to the power supply and the other end drain connected to the gate of the pMOS transistor a via the diode connected pMOS transistor d.

The pMOS transistor d is connected between the power supply and the gate of a pMOS transistor a. The pMOS transistor d has the gate fed with the signal REFEN which is the inverted signal of the enable signal REFENB and is controlled to be turned on off in response to the signal REFEN.

The pMOS transistor d has one end source connected to the power supply and the other end drain connected to the gate of the pMOS transistor a via the diode connected pMOS transistor d.

The pMOS transistor d is connected between the gate of the pMOS transistor a and the gate of the pMOS transistor a. The pMOS transistor d has the gate fed with the enable signal REEENB and is controlled to be turned on off in response to the enable signal REEENB.

The potential holding circuit configured thus boosts a potential to a predetermined potential in this case the threshold voltage of a power supply voltage VDD pMOS transistor when the reference current generating circuit is deactivated. Thus a reference current generating section can be powered up more quickly.

The pMOS transistor e is connected in parallel with the pMOS transistor b between the pMOS transistor be and the nMOS transistor b.

The pMOS transistor e is connected in parallel with the pMOS transistor b between the pMOS transistor b and the nMOS transistor b. The pMOS transistor e has the gate connected to the gate of the pMOS transistor e and is diode connected.

In this way the first oscillation preventing circuit is configured such that the current mirror circuit of the pMOS transistors e and e is connected in the opposite direction from the current mirror circuit of the pMOS transistors b and b.

With this configuration the gate input signal of the PMOS transistor b can be set high which generates a dead zone on the side of the pMOS transistor b and the side of the nMOS transistor b. Thus it is possible to suppress the oscillation of an output signal a reference current distributed potential IREFNCH .

As shown in the second oscillation preventing circuit includes a switch circuit f having one end connected to an output terminal and a capacitive element f connected between the other end of the switch circuit f and the ground.

The switch circuit f has the gate fed with the enable signal REFENB and is controlled to be turned on when a switch circuit is turned on. Thus a wire and the capacitive element f are electrically connected to each other and the oscillation of the reference current distributed potential IREFNCH is suppressed.

As shown in the bit line resistor is connected between an nMOS transistor a and a reference cell a. The bit line resistor is a metal wire which has the same width and length as a local bit line connected to a memory cell . Thus it is possible to increase the equivalence of a capacitance and generate a reference current Iref with higher accuracy.

As described above the semiconductor memory of the present embodiment can increase the rate of rise of the reference current.

The first and second embodiments described examples of the configuration for increasing the rate of rise of the reference current. The present embodiment will particularly describe an example of control on a reading operation a verifying operation and a refreshing operation for increasing the rate of rise of the reference current.

A reference current control circuit outputs a signal RESTART in synchronization with a change of the read signal R ACTIVE. In response to the signal RESTART a counter circuit changes a signal RTIMER to High . The signal RTIMER is kept at High for a predetermined time e.g. 1 us and then is changed to Low .

In synchronization with the change of the signal RTIMER to High a reference current control circuit changes an enable signal REFENB to Low . Thus a reference current generating circuit is activated.

Next at the completion of latching of data having been determined by a sense amplifier a signal LAT changes to Low . In synchronization with the change of the signal LAT the reference current control circuit changes a signal REFSW to High and turns on a switch circuit so that a wire is charged.

After the read signal R ACTIVE becomes Low at the completion of the reading operation the counter circuit changes the signal RTIMER to Low . The reference current control circuit changes the signal REFSW to Low in synchronization with the change of the signal RTIMER so that the switch circuit is turned off.

After that the reference current control circuit changes the enable signal REFENB to High and deactivates the reference current generating circuit .

In other words the reference current control circuit activates the reference current generating circuit in response to the read signal R ACTIVE and does not open the switch circuit before receiving the signal LAT. The switch circuit is operated after the reading operation after the completion of latching so that the propagation of noise can be suppressed.

Thus in the first reading operation after recovery from a standby state the reference current generating circuit is not connected to the sense amplifier the switch circuit is turned off and the reading operation is performed with a charge held on the wire .

In this case the activation period of the reference current generating circuit is 1 us which sufficiently recovers the potential of the wire to a predetermined potential.

As shown in a verification signal A ACTIVE becomes High and the semiconductor memory is placed in a verified state.

In synchronization with the change of the verification signal A ACTIVE the reference current control circuit outputs the signal RESTART. In response to the signal RESTART the counter circuit changes the signal RTIMER to High .

In synchronization with the change of the signal RTIMER the reference current control circuit changes the enable signal REFENB to Low so that the reference current generating circuit is activated.

After a predetermined delay e.g. 100 ns from when the enable signal REFENB changes to Low to when the reference current generating circuit is powered up the reference current control circuit changes the signal REFSW to High and turns on the switch circuit so that the wire is charged.

After that in this case three clocks after the verification signal A ACTIVE changes to High a signal A SAENB changes to Low and the sense amplifier performs a sensing operation. When the signal A SAENB changes to High the sensing operation of the sense amplifier is completed.

After that the verification signal A ACTIVE becomes Low and the verifying operation of the semiconductor memory is completed.

The counter circuit changes the signal RTIMER to Low thereafter. The reference current control circuit changes the signal REFSW to Low in synchronization with the change of the signal RTIMER so that the switch circuit is turned off.

The reference current control circuit changes the enable signal REFENB to High and deactivates the reference current generating circuit .

In other words the reference current control circuit activates the reference current generating circuit thereafter in response to the verification signal A ACTIVE indicating a verified state and opens the switch circuit after a lapse of 100 ns. After that the sense amplifier is activated three clocks later after the verification signal A ACTIVE changes to High .

Thus it is possible to prevent noise caused by the opening of the switch circuit from affecting the verifying operation.

Also in this example the activation period of the reference current generating circuit is 1 us which sufficiently recovers the potential of the wire to the predetermined potential.

As shown in first a refresh pulse signal REFRESH becomes High and the refreshing operation is started.

The reference current control circuit outputs the signal RESTART in synchronization with the change of the refresh pulse signal REFRESH. The counter circuit changes the signal RTIMER to High in response to the signal RESTART.

In synchronization with the change of the signal RTIMER the reference current control circuit changes the enable signal REFENB to Low so that the reference current generating circuit is activated.

After a delay of 100 ns the reference current control circuit changes the signal REFSW to High and turns on the switch circuit so that the wire is charged.

After that 1 us after the signal RTIMER changes to High the counter circuit changes the signal RTIMER and the refresh pulse signal REFRESH to Low . The reference current control circuit changes the signal REFSW to Low in synchronization with the change of the signal RTIMER so that switch circuit is turned off.

After that the reference current control circuit changes the enable signal REFENB to High and deactivates the reference current generating circuit .

In other words the reference current control circuit activates the reference current generating circuit in response to the refresh pulse signal REFRESH and opens the switch circuit after a lapse of 100 ns.

Also in this example the activation period of the reference current generating circuit is 1 us which sufficiently recovers the potential of the wire to the predetermined potential.

As described above the semiconductor memory of the present embodiment can increase the rate of rise of the reference current while reducing the influence of noise on the reference current.

As described above the first and second embodiments described examples of the configuration for increasing the rate of rise of the reference current. In order to quickly respond to a reading operation immediately after power is turned on a reference current distributed potential IREFNCH has to reach a desired level before the reading operation.

The present embodiment will describe an example in which the rise of a reference current is controlled after power is turned on. The following will particularly describe an example in which the reference current distributed potential IREFNCH is caused to reach a desired level in a power on time e.g. 500 us after being boosted to the set value of the voltage VDDR.

A signal ROSCE becomes High at that time so that a pump circuit starts a boosting operation. When the potential VDDR reaches a set value e.g. 6.0 V the signal ROSCE becomes Low so that the boosting operation of the pump circuit is stopped time t . Thus the potential VDDR decreases with the passage of time.

When the signal ROSCE becomes Low a counter circuit outputs a refresh pulse signal REFRESH and a signal RTIMER in response to a signal PONED0B outputted from the pump circuit . As a result a reference current control circuit changes an enable signal REFENB to Low in response to these signals. Thus a reference current generating circuit is activated.

After that the reference current control circuit changes a signal REFSW to High and turns on a switch circuit so that a wire is charged.

The reference current control circuit changes the signal REFSW to Low thereafter so that the switch circuit is turned off.

After that the reference current control circuit changes the enable signal REFENB to High and deactivates the reference current generating circuit time t .

The above operations allow the reference current distributed potential IREFNCH to reach the desired level in a power on time e.g. 500 us after being boosted to the set value of the voltage VDDR.

After that in order to recharge refresh the wire the reference current generating circuit is activated for example every 400 us times t to t .

After that also at the completion of the second boosting operation of the pump circuit the reference current control circuit is activated times t to t .

Thus the wire can be recharged refreshed in a state in which the predetermined voltage VDDR is applied to a reference cell a. In other words the wire can be kept at a predetermined potential.

In this way the wire for distributing the reference current distributed potential IREFNCH to a sense amplifier is previously charged immediately after the semiconductor memory is turned on. Thus the reference current distributed potential IREFNCH has been prepared at the start of a reading operation.

It is therefore possible to eliminate the need for a time period during which the reference current distributed potential IREFNCH is raised and prepared from the start the reading operation. Thus the reading operation can be performed faster.

Also in this example the activation period of the reference current generating circuit is 1 us which sufficiently recovers the potential of the wire to the predetermined potential.

As in the third embodiment in the first reading operation after the semiconductor memory is turned on the reference current generating circuit is not connected to a sense amplifier the switch circuit is turned off and the reading operation is performed with a charge held on the wire .

As described above the semiconductor memory of the present embodiment can increase the rate of rise of the reference current while reducing the influence of noise on the reference current. Particularly the reading operation of the semiconductor memory can be performed faster.

As described above the first and second embodiments described examples of the configuration for increasing the rate of rise of the reference current. The present embodiment will particularly describe an example of control on a reading operation a verifying operation and a refreshing operation for increasing the rate of rise of a reference current.

As shown in first a deep power down signal DPD changes to High and a semiconductor memory is placed into the deep power down state time t .

At this point since a pump circuit is deactivated a voltage VDDR drops. Further the pump circuit changes a signal PONEND0B to High so that a reference period generating circuit and a counter circuit are stopped.

Moreover a reference current control circuit changes an enable signal REFENB to High based on the change of the deep power down signal DPD. Thus the reference current control circuit is also deactivated.

Next the deep power down signal DPD changes to Low and the semiconductor memory recovers from the deep power down state time t . At this point since the pump circuit is activated a boosting operation is started and the potential VDDR increases.

After that when the voltage VDDR is boosted to a set value the pump circuit stops the boosting operation of the potential VDDR and changes the signal PONEND0B to Low time t . In response to the signal PONEND0B the reference period generating circuit and the counter circuit are powered up. Then the counter circuit outputs a refresh pulse signal REFRESH and changes a signal RTIMER to High .

In response to the refresh pulse signal REFRESH and the signal RTIMER the reference current control circuit changes the enable signal REFENB to Low so that a reference current generating circuit is activated.

Next the reference current control circuit changes a signal REFSW to High to turn on a switch circuit after a predetermined delay e.g. 100 ns so that the wire is recharged.

After that the reference current control circuit changes the signal REFSW to Low so that the switch circuit is turned off.

In response to the changes of the refresh pulse signal REFRESH and the signal RTIMER the reference current control circuit changes the enable signal REFENB to High and deactivates the reference current generating circuit time t .

As described above the semiconductor memory recovers from the deep power down state and the pump circuit starts boosting the voltage VDDR. Before a lapse of a predetermined time times t to t e.g. 75 us after the start of the boosting operation the wire can be recharged refreshed with the boosted voltage VDDR.

In other words after the recovery from the deep power down state the wire can be kept at a predetermined potential in a state in which the predetermined voltage VDDR is applied to a reference cell.

In this way the wire for distributing a reference current IREFNCH to a sense amplifier is charged beforehand after the semiconductor memory recovers from the deep power down state. Thus the reference current distributed potential IREFNCH has been prepared at the start of a reading operation which eliminates the need for a time period for starting and preparing the reference current distributed potential IREFNCH from the start of the reading operation. Thus the reading operation can be performed more quickly.

Also in this example the activation period of the reference current generating circuit is 1 us which sufficiently recovers the potential of the wire to the predetermined potential.

As described above the semiconductor memory of the present embodiment can increase the rate of rise of the reference current while reducing the influence of noise on the reference current. Particularly the reading operation of the semiconductor memory can be performed more quickly.

As shown in a wire fed with a reference current distributed potential IREFNCH is separated from a reference current generating circuit by a switch circuit . In the event of a defect on an element composing the switch circuit leakage current reduces the potential of the wire and may cause problems in a reading operation and a verifying operation.

As described above the wire is recharged refreshed by activating the reference current generating circuit for example every 400 us. For example a reading operation may be performed to conduct a test slightly before the recharge. However it takes quite a long time to conduct a test on a memory cell in a semiconductor memory .

The present embodiment will describe an example of a configuration for checking the presence or absence of leakage current which is caused by the switch circuit on the wire in a shorter time.

As shown in the semiconductor memory includes the test leak source . The test leak source is connected to a contact between the switch circuit and a sense amplifier .

The wire is deliberately discharged by the test leak source during a test and the potential of the contact is reduced in a shorter period than a refresh period e.g. 400 us .

For example the test leak source reduces the potential of the wire to level L at which leakage caused by the switch circuit is absent in the refresh period 400 us and then a test is conducted on a reading operation thereby reducing a test time. In this case when the elements of the switch circuit do not have any defects the potential of the wire does not decrease below the level L. Thus when the potential of the wire is lower than the level L it is decided that an element of the switch circuit is defective.

As described above the semiconductor memory of the present embodiment can check the presence or absence of leakage current which is caused by the switch circuit on the wire in a shorter time.

The following will describe an example in which the semiconductor memory NOR flash memory having the foregoing configuration and functions is mounted in a semiconductor chip. The same explanation is applicable to the semiconductor memories described in the foregoing embodiments.

As shown in the semiconductor chip includes in the same package a NAND flash memory a spacer the NOR flash memory a spacer a pseudo static random access memory PSRAM and a controller which are sequentially stacked on a substrate .

The NAND flash memory has for example a plurality of memory cells capable of storing multivalued data. The semiconductor chip may include a synchronous dynamic random access memory SDRAM instead of the PSRAM.

Of these memories the NAND flash memory is used as for example a data storing memory according to a use of a memory system. The NOR flash memory is used as for example a program storing memory. The PSRAM is used as for example a work memory.

The controller mainly controls the input and output of data and manages data for the NAND flash memory . The controller has an ECC correcting circuit not shown which adds an error correction code ECC when data is written and analyzes and processes the error correction code during reading.

The NAND flash memory the NOR flash memory PSRAM and the controller are bonded to the substrate with wires .

Solder balls provided on the underside of the substrate are electrically connected to the wires . As a package shape for example a surface mounting ball grid array BGA is used which is a two dimensional arrangement of the solder balls .

The following will describe the case where the semiconductor chip is applied to a mobile phone which is an example of electronic equipment.

A CPU not shown mounted in the mobile phone accesses the semiconductor chip via an interface not shown and transfers data and so on. For example the mobile phone uses the NAND flash memory as a storage region of user data and the NOR flash memory as a program storage region of firmware and so on.

In such a memory system the NOR flash memory is demanded of a shorter reading time of data. Further the amount of program data to be stored has increased with the functionality of application software.

The NOR flash memory of the first embodiment which is an aspect of the present invention includes a memory cell capable of holding multivalued data and is configured to quickly raise a reference current thereby solving the foregoing problem.

The semiconductor chip is applicable to electronic equipment such as a personal computer a digital still camera and a PDA as well as the above mobile phone.

