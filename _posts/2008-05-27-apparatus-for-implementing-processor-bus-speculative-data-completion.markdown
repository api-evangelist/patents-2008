---

title: Apparatus for implementing processor bus speculative data completion
abstract: A method, and apparatus are provided for implementing processor bus speculative data completion in a computer system. A memory controller in the computer system sends uncorrected data from a memory to a processor bus. The memory controller also applies the uncorrected data to error correcting code (ECC) checking and correcting circuit. When a single bit error (SBE) is detected, corrected data is sent to the processor bus a predefined number of cycles after the uncorrected data.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08103930&OS=08103930&RS=08103930
owner: International Business Machines Corporation
number: 08103930
owner_city: Armonk
owner_country: US
publication_date: 20080527
---
The present invention relates generally to the data processing field and more particularly relates to a method and apparatus for implementing processor bus speculative data completion during a memory read for enabling reduced read memory latency in a computer system.

In computer systems an ongoing design goal in developing future computer systems is providing improved performance. The performance of a computer server is one of the key reasons a customer may or may not choose to buy a given system.

One of the key benchmarks server customers use is the benchmark TPC C. Depending on the processor s cycles per instruction CPI the memory CPI can account for more than 50 of the overall CPI. The read memory latency has a direct impact on server performance.

A need exists for an effective mechanism for improving performance in computer systems. It is desirable to provide such a mechanism that enables reduced read memory latency while maintaining effective single bit error SBE detection and correction.

Principal aspects of the present invention are to provide a method apparatus and computer program product for implementing processor bus speculative data completion in a computer system. Other important aspects of the present invention are to provide such method and apparatus for implementing processor bus speculative data completion in a computer system substantially without negative effect and that overcome many of the disadvantages of prior art arrangements.

In brief a method and apparatus are provided for implementing processor bus speculative data completion in a computer system. A memory controller in the computer system sends uncorrected data from a memory to a processor bus. The memory controller also applies the uncorrected data to error correcting code ECC checking and correcting circuit. When a single bit error SBE is detected corrected data is sent to the processor bus a predefined number of cycles after the uncorrected data.

In accordance with features of the invention sending the uncorrected data reduces latency of data transfers by at least one cycle while providing effective SBE checking and correction.

In accordance with features of the invention a memory controller memory management unit MMU in the computer system implements methods for processor bus speculative data completion. Memory controller MMU includes a multiplexer an error correcting code ECC checking and correcting circuit and a control logic function coupled to the multiplexer. Uncorrected data from the memory is applied to a first input of the multiplexer and corrected data from the ECC checking and correcting circuit is applied to a second input of the multiplexer. Normally an output of the multiplexer is the uncorrected data from the memory. When a Single Bit Error SBE is detected the ECC checking and correcting circuit applies a signal to the control logic function. The control logic function applies a control signal to the multiplexer responsive to the detected Single Bit Error SBE for the multiplexer to select the corrected data signal at the second multiplexer input for output of the multiplexer. The output of the multiplexer is sent to the processor bus.

Referring now to the drawings in there is shown a computer system generally designated by the reference character for implementing methods for processor bus speculative data completion in accordance with the preferred embodiment. Computer system includes a plurality of main processors coupled by a processor bus to a memory controller or memory management unit MMU . A system memory and input output I O is coupled to the processor bus by the memory controller MMU . A dotted line labeled PATH OF INTEREST illustrates a data path from the system memory to the processor bus for implementing processor bus speculative data completion in accordance with the preferred embodiment.

Computer system is shown in simplified form sufficient for understanding the present invention. The illustrated computer system is not intended to imply architectural or functional limitations. The present invention can be used with various hardware implementations and systems and various other internal hardware devices for example a single main processor could be used.

In accordance with features of the preferred embodiment the memory controller is provided for implementing methods for processor bus speculative data completion in accordance with the preferred embodiment. The memory controller sends the uncorrected data directly to the processor bus logic providing improved performance over prior art arrangements.

For example as illustrated in in prior art arrangements the memory read data return is applied to a memory controller single bit error correct logic before being sent to the processor interface. This latency is added regardless of whether or not a single bit error SBE occurred.

In accordance with features of the preferred embodiment in parallel with sending uncorrected data directly to the processor bus logic the memory controller MMU determines if a single bit error SBE occurred and indicates this to the processor bus. Because returning a cache line of data takes multiple cycles or beats on both the memory and processor bus scenarios must be handled where the first beats are good but a subsequent beat includes an SBE. If an SBE occurs then on the data interface between the memory controller and processor bus corrected data is sent a predefined number of cycles after the uncorrected data such as 2 cycles later.

Referring to there is shown the memory controller MMU of the computer system for implementing methods for processor bus speculative data completion in accordance with the preferred embodiment. Memory controller MMU includes a multiplexer MUX an error correcting code ECC checking and correcting circuit and a control logic function coupled to the MUX . Uncorrected data from the memory is applied to a first input of MUX as indicated at a line UNCORRECTED DATA and corrected data from the ECC checking and correcting circuit is applied to a second input of MUX as indicated at a line CORRECTED DATA . When a Single Bit Error SBE is detected the ECC checking and correcting circuit applies a signal to the control logic function as indicated at a line SBE DETECTED . The output of MUX is sent to the processor bus as indicated at a line MC XX DATA SIGNAL as shown in the timing diagrams of .

Typically the MC XX DATA signal is the uncorrected data signal applied to the first input of MUX . When a Single Bit Error SBE is detected then the MC XX DATA signal is the corrected data signal applied to the second input of MUX from the ECC checking and correcting circuit . The control logic function applies a control signal to the MUX when the Single Bit Error SBE is detected for the MUX to select the corrected data signal at the second MUX input.

Referring to and there are shown timing diagrams illustrating operation of the memory controller MMU implementing methods for processor bus speculative data completion in accordance with the preferred embodiment. The following Table 2 provides a description of the illustrated signals of provided by the memory controller MMU .

FPVAL signal indicates that valid data will be flowing from Memory a number of X cycles such as sixteen 16 cycles after this signal is asserted.

FPSBE indicates whether or not a Single Bit Error SBE which is correctable has occurred within the Memory Data. This signal is asserted in conjunction with the associated Memory Data.

MC XX DATA is Data from the memory controller MMU that is being sent to the Processor Bus logic . This data is usually the uncorrected memory data but is switched to the corrected data as necessary as shown and described with respect to in .

Q.DRDY is a Processor Bus signal that indicates that valid data is being transferred on the processor bus. Note that this signal is asserted for two bus clocks for every cache line of data transferred.

Referring now to the respective above described signals are shown for a memory read operation without a Single Bit Error SBE . The Q.DRDY signal is asserted for two consecutive bus clocks with the Q.DAT processor bus data signals.

In the respective above described signals are shown for two memory reads with a Single Bit Error SBE in the first 16 bytes of the first memory read. The SBE in the first 16 bytes of the first memory read is indicated by XX within line representing the MC XX DATA data output of the memory controller MMU . The second FPSBE signal is asserted to indicate that a Single Bit Error SBE has occurred within the Memory Data and that the second transfer is from the ECC check and correct circuit . The Q.DRDY signal is asserted for two consecutive bus clocks with the Q.DAT processor bus data signals.

In the respective above described signals are shown for two memory reads with a Single Bit Error SBE in the second 16 bytes of the first memory read. The second FPSBE signal is asserted to indicate that the Single Bit Error SBE has occurred within the Memory Data and that the data transfer is from the ECC check and correct circuit . The Q.DRDY signal is asserted for two consecutive bus clocks with the Q.DAT processor bus data signals.

In the respective above described signals are shown for two memory reads with a Single Bit Error SBE in the third 16 bytes of the first memory read. The second FPSBE signal is asserted to indicate that the Single Bit Error SBE has occurred within the Memory Data and that the third transfer is from the ECC check and correct circuit . The Q.DRDY signal is asserted for two separated bus clocks for the valid Q.DAT processor bus data signals.

In the respective above described signals are shown for two memory reads with a Single Bit Error SBE in the fourth 16 bytes of the first memory read. The second FPSBE signal is asserted to indicate that the Single Bit Error SBE has occurred within the Memory Data and that the fourth transfer is from the ECC check and correct circuit . The Q.DRDY signal is asserted for two separated bus clocks for the valid Q.DAT processor bus data signals.

While the present invention has been described with reference to the details of the embodiments of the invention shown in the drawing these details are not intended to limit the scope of the invention as claimed in the appended claims.

