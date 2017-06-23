---

title: Read reference circuit for a sense amplifier within a chalcogenide memory device
abstract: A read reference circuit for a sense amplifier within a chalcogenide memory device is disclosed. The read reference circuit provides a reference voltage level to the sense amplifier for distinguishing between a logical “0” state and a logical “1” state within a chalcogenide memory cell. In conjunction with a precharge circuit, the read reference circuit generates a selectable read reference current to the sense amplifier in order to detect the logical state of the chalcogenide memory cell. The precharge circuit precharges the bitlines of the chalcogenide memory cell before the sense amplifier detects the logical state of the chalcogenide memory cell.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07916527&OS=07916527&RS=07916527
owner: Ovonyx, Inc.
number: 07916527
owner_city: Rochester Hills
owner_country: US
publication_date: 20081126
---
The present application claims benefit of priority under 35 U.S.C. 365 to the previously filed international patent application number PCT US2008 084781 filed on Nov. 26 2008 assigned to the assignee of the present application and having a priority date of Nov. 30 2007 based upon U.S. provisional patent application No. 60 991 412. The contents of both applications are incorporated herein by reference.

The present invention was made with United States Government assistance under Contract No. FA9453 04 C 0052 awarded by the United States Air Force. The United States Government has certain rights in the present invention.

The present invention relates to memory devices in general and in particular to a read reference circuit for a sense amplifier within a chalcogenide memory device.

Phase transformation is a process of changing a phase change material from an amorphous state into a crystalline state or vice versa. Such phase transformation generally occurs when an electrical field is being applied to a phase change material. Because the amorphous state of the phase change material has a different electrical resistance from the crystalline state of the phase change material the two different states can be utilized to represent a logical 0 and a logical 1 respectively for data storage applications.

An alloy known as chalcogenide which includes germanium antimony and tellurium can be made to have phase transformation properties at a relatively low voltage. The electrical properties of chalcogenide are also particularly suitable for data storage applications. Since random access memories made of chalcogenide can easily be integrated with conventional logic circuits chalcogenide random access memories have gradually become one of the more promising technologies for producing a new generation of memory devices especially for light portable electronic devices.

Because of process variations of chalcogenide materials the electrical characteristics of chalcogenide memory cells within a chalcogenide memory device tend to be less uniform than those of their complementary metal oxide semiconductor CMOS counterparts. For example the distribution of set and reset resistance values for chalcogenide memory cells may vary from one memory device to another. As a result a static reference voltage that is commonly utilized by a sense amplifier circuit to determine a logical state of a memory cell within a CMOS random access memory device may not work properly for all chalcogenide memory cells within a chalcogenide memory device.

In accordance with a preferred embodiment of the present invention a read reference circuit is utilized to provide a reference voltage level to a sense amplifier for distinguishing between a logical 0 state and a logical 1 state within a chalcogenide memory cell. In conjunction with a precharge circuit the read reference circuit generates a selectable read reference current to the sense amplifier in order to detect the logical state of the chalcogenide memory cell. The precharge circuit precharges the bitlines of the chalcogenide memory cell before the sense amplifier detects the logical state of the chalcogenide memory cell.

All features and advantages of the present invention will become apparent in the following detailed written description.

Referring now to the drawings and in particular to there is illustrated a current voltage curve of a chalcogenide memory cell as the chalcogenide memory cell is being programmed and read. As shown the chalcogenide material in the chalcogenide memory cell behaves like a quasi linear resistor in a polycrystalline state and the chalcogenide material exhibits a voltage snap back at approximately a threshold voltage Vin an amorphous state.

The chalcogenide memory cell can be placed in a read mode when the applied voltage to the chalcogenide material within the chalcogenide memory cell is lower than the threshold voltage V. Conversely the chalcogenide memory cell can be placed in a program or write mode when the applied voltage to chalcogenide material within the chalcogenide memory cell is higher than the threshold voltage V.

During the program mode the chalcogenide memory cell can be programmed to either a low resistance state i.e. a logical 1 or set or a high resistance state i.e. a logical 0 or reset by utilizing different write current amplitude to heat the chalcogenide material within the chalcogenide memory cell to either the polycrystalline state or the amorphous state respectively as shown in .

Writing a logical 1 requires a lower current amplitude and a relatively long cooling time. In contrast writing a logical 0 requires a higher current amplitude and a much shorter cooling time.

An extrapolation of the linear region of the current voltage curve in to the x axis yields a point known as a holding voltage V. In order to exit the program mode the applied voltage to the chalcogenide memory cell must be less than the holding voltage V.

With reference now to there is illustrated a block diagram of a read reference circuit in accordance with a preferred embodiment of the present invention. As shown a read reference circuit is coupled to a sense amplifier circuit and a set of chalcogenide memory cells . Each of chalcogenide memory cells can be placed in an amorphous state or a crystalline state which is utilized to represent a logical 0 and a logical 1 respectively. The state of each of chalcogenide memory cells can be changed from one to another via the application of an electrical field accordingly.

Sense amplifier circuit serves to detect the logical states of chalcogenide memory cells based on a reference voltage as is well known in the art. However because of process variations of chalcogenide materials the electrical characteristics of chalcogenide memory cells tend to be less uniform than those of their complementary metal oxide semiconductor CMOS counterparts. For example the distribution of set and reset i.e. 1 and 0 resistance values for chalcogenide memory cells may vary from one chip to another. As a result a static reference voltage that is commonly utilized by a sense amplifier circuit to determine a logical state i.e. 1 or 0 of a memory cell within a CMOS random access memory device may not work properly for all chalcogenide memory cells .

As such read reference circuit is configured to provide a dynamic sense amplifier reference current or voltage to sense amplifier circuit for the purpose of discerning logical states of chalcogenide memory cells . After determining the precharge voltage level read reference circuit generates an analog sense reference override signal to sense amplifier circuit .

As shown in read reference circuit includes a current level generation circuit and a precharge circuit . Current level generation circuit further includes a current tuning circuit and a reference level adjustment circuit .

Reference level adjustment circuit includes a digital reference current input and an analog reference override input . Analog reference override input allows the reference current to sense amplifier to be changed dynamically during the performance of a margin test. During a margin test the sense amplifier reference current can be set at above or below a built in reference current in order to determine a margin for programming chalcogenide memory cells . Any one of chalcogenide memory cells that has a lower margin can be replaced by an available redundant memory cell. During normal operations a switch Kassociated with analog reference override input is left open. Current can be supplied to digital reference current input via a current mirror circuit not shown .

An analog reference override input is an external control signal to reference level adjustment circuit . During normal operations analog reference override input is grounded in order to disable the override function. During a margin test analog reference override input is shmooed in the range that is greater than a predetermined Vthreshold. The Vthreshold provides a noise margin in case there is noise on the override input. Basically analog reference override input allows the measurements of ones and zeros across chalcogenide memory cells quickly since it uses sense amplifier and digital output path and no analog measurements are necessary.

Precharge circuit precharges the bitlines of chalcogenide memory cells before sense amplifier detects the logical state chalcogenide memory cells . Preferably precharge circuit precharges the bitlines to approximately 200 400 mV. Precharge circuit is enabled by a precharge control signal. Precharge circuit is also controlled by a reference set point Vin order to ensure that the bitlines are changed enough that logical 0 can be read normally. For example Vneeds to be much greater than the threshold voltage Vof a chalcogenide cell during a read operation.

Read reference circuit may provide a range of sense amplifier reference currents for reading the resistances of different chalcogenide memory cells . Current tuning circuit is implemented with capacitors and cascaded current mirror structures to provide a high noise rejection. Current tuning circuit includes multiple switches for programming read reference circuit to the desired current for a given distribution of set and reset resistance values within chalcogenide memory cells . For example three switches SA SA are included within current tuning circuit as well as precharge circuit to provide eight different reference current levels. Any of SA SA can be open or close to provide different reference current levels for respective chalcogenide memory cells based on characterization information.

As has been described the present invention provides a read reference circuit for a sense amplifier within a chalcogenide memory device.

While the invention has been particularly shown and described with reference to a preferred embodiment it will be understood by those skilled in the art that various changes in form and detail may be made therein without departing from the spirit and scope of the invention.

