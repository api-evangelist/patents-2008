---

title: System and method for minimizing MRI-imaging artifacts
abstract: Methods of, and systems for, simultaneously compensating for external-magnetic-field inhomogeneity as well as radiofrequency magnetic-field inhomogeneity in an MRI system. In one method embodiment, a pulse sequence is applied when the transmitter-reference frequency is delivered on resonance. The pulse sequence includes radiofrequency pulses which may be applied at arbitrary-excitation-flip angles that are not necessarily 90° degrees. The pulse sequence also includes spin-locking pulses applied in concert with a refocusing-composite pulse. In another method embodiment, a pulse sequence is applied when the transmitter-reference frequency is delivered off resonance. This off-resonance-pulse sequence includes radiofrequency pulses which may be applied at arbitrary-excitation-flip angles that are not necessarily 90° degrees. Sandwiched between the excitation-flip angles are at least two off-resonance-spin-lock pulses applied at an inverse phase and frequency from each other.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07705596&OS=07705596&RS=07705596
owner: The Trustees of the University of Pennsylvania
number: 07705596
owner_city: Philadelphia
owner_country: US
publication_date: 20080519
---
The present patent application claims benefit of U.S. Provisional Application Ser. No. 60 930 733 filed on 18 May 2007 which is incorporated herein by reference.

This work was supported by NIH grants R01AR045404 and R01AR051041 and performed at a NIH supported resource center NIH RR02305 . The government may have certain rights in this invention.

The present invention relates to magnetic resonance imaging MRI and more particularly to a system and method for minimizing imaging artifacts produced by MRI systems.

Magnetic Resonance Imaging MRI is an imaging technique based in part on the absorption and emission of energy in the radio frequency range. To obtain the necessary magnetic resonance MR images a patient or other target is placed in a magnetic resonance scanner. The scanner provides a magnetic field that causes target atoms to align with the magnetic field. The scanner also includes coils that apply a transverse magnetic field. Radio frequency RF pulses are emitted by the coils causing the target atoms to absorb energy. In response to the RF pulses photons are emitted by the target atoms and detected as signals in receiver coils.

Radio frequency pulses delivered by the coils are precisely calibrated to deliver the appropriate amount of power to maximize tissue contrast. Emitting RF pulses with too much power however may result in a host of undesired effects such as tissue or cellular damage. Specifically high power RF energy levels may cause an overheating of tissues inside a patient as well as the absorption of harmful levels of radiation. Absorption of electromagnetic energy by the tissue is described in terms of Specific Absorption Rate SAR which is expressed in Watts kg. SAR in MRI is a function of many variables including pulse sequence and coil parameters and the weight of the region exposed. In the United States for example the recommended SAR level for head imaging is 8 Watts kg. Consequently government restrictions are in place limiting how much power may be delivered into a patient s tissues during RF pulses.

Several techniques shown to be useful for pathology diagnosis unfortunately require substantial RF power and consequently SAR levels may be unacceptable for clinical use. Unfortunately reducing the amount of power delivered to patients to meet acceptable SAR levels produces clinical images with artifacts and reduced tissue contrast. Imperfections in magnetic fields of a scanner interfere with the scanner s ability to produce high contrast artifact free images especially at low RF power levels.

One conventional technique used to compensate for these imperfections involves injecting intravenous contrast agents into patients to delineate areas of interest. These contrast agents however are often contraindicated for certain patients and can produce undesirable side effects including the chance for an anaphylactoid reaction among other serious risks.

Thus presently there is no satisfactory way to produce high contrast clinical images free of artifacts within acceptable SAR levels.

To solve these and other problems the present invention described herein introduces a method of and system for simultaneously compensating for external magnetic field inhomogeneity as well as radiofrequency magnetic field inhomogeneity in an MRI system.

In one method embodiment a pulse sequence is applied when the transmitter reference frequency is delivered on resonance. The pulse sequence includes radiofrequency pulses which may be applied at arbitrary excitation flip angles that are not necessarily 90 degrees. The pulse sequence also includes spin locking pulses applied in concert with a refocusing composite pulse.

In another method embodiment a pulse sequence is applied when the transmitter reference frequency is delivered off resonance. This off resonance pulse sequence includes radiofrequency pulses which may be applied at arbitrary excitation flip angles that are not necessarily 90 degrees. Sandwiched between the excitation flip angles are at least two off resonance spin lock pulses applied at an inverse phase and frequency from each other.

As a result of being able to compensate for both static magnetic and radiofrequency field imperfections high contrast clinical images free of artifacts can be produced at low radio frequency power levels i.e. within acceptable SAR levels. As image artifacts are essentially eliminated in MR images image quality is vastly improved over conventional techniques. Further it may be possible to eliminate the need to inject intravenous contrast agents into patients for certain studies among other benefits.

It is noted that conventional off resonance rotary echoes are not presently used in a clinical environment. Images produced as result of off resonance echoes contain substantial artifacts. As a result of one embodiment of this invention however it is now possible to utilize off resonance rotary echoes in a clinical setting because MR images can now be obtained without artifacts and at low power levels well within acceptable SAR levels.

The foregoing summary provides an exemplary overview of some aspects of the invention. It is not intended to be extensive or absolutely require any key critical elements of the invention. These and other implementations will be described below when read in conjunction with the accompanying drawings.

Described herein is an innovative MRI system and method able to simultaneously compensate for external magnetic field and radiofrequency magnetic field inhomogeneities in an MRI system.

In describing the compensation methods the following terminology will be used in accordance with the definitions set forth below.

As used herein approximately 180 refers to an angle sufficiently close to the 180 but may be slightly less or more than 180 as would be appreciated by those skilled in the relevant art.

As used herein B is an external magnetic field which is typically a Direct Current zero frequency superconducting field.

As used herein cause means to set off an event or action such as the delivery of a signal. As used herein the term causing a pulse to be applied or variations thereof refers to the act of sending instructions to hardware to be described from a control system to be described to deliver radiofrequency energy in a particular manner.

As used herein an inhomogeneity refers to one or more imperfections in either the B or B fields or both. Inhomogeneities in either field give rise to image artifacts.

As use herein off resonance refers to delivering a radiofrequency pulse at a frequency different from the rate of precession of the nuclear spins.

As used herein on resonance refers to a radiofrequency pulse at a frequency identical with the rate of precession of the nuclear spins.

As used herein a refocusing composite pulse refers to one or more combinations of pulses which rewind the effects of field inhomogeneity.

As used herein a spin locking pulse refers to a long B radiofrequency pulse delivered to create either T or T off or other relaxation time types contrast in images.

Reference herein to one embodiment an embodiment or similar formulations herein means that a particular feature structure operation or characteristic described in connection with the embodiment is included in at least one embodiment of the present invention. Thus the appearances of such phrases or formulations herein are not necessarily all referring to the same embodiment. Furthermore various particular features structures operations or characteristics may be combined in any suitable manner in one or more embodiments.

Control system controls hardware components such as RF coil for the transmitting RF pulses there from. Control system may be implemented as a computer or control device which includes at least one processor and memory . Memory may include volatile memory e.g. RAM and or non volatile memory e.g. ROM . It is also possible for other memory mediums not shown having various physical properties to be included as part of control system .

Control system may also include code stored in memory such as software and or firmware that causes MRI system to apply RF pulses and acquire images.

Much of the discussion below will focus on embodiments for performing operations of control system that may be embodied as code used to control MRI system . In particular applying RF pulses to compensate for B and B field imperfections.

As appreciated by those skilled in the art any suitable calibration techniques may be used prior to applying RF pulses. For example in one embodiment MRI scanner calibration may include three operations as follows 

For instance a first calibration step may involve using a scanner frequency calibration to determine the scanner on resonance condition. This is performed by a spectroscopy experiment to determine where the resonant peak of interest occurs relative to the MRI scanner reference frequency used for RF transmission.

A second calibration step may involve using an RF transmitter voltage calibration to determine the voltage flip angle relationship for the scanner object pair.

A third calibration step may involve B field shimming by magnetic field gradient adjustment to improve the homogeneity of the superconducting magnetic field. Both RF transmitter calibration and B field shimming are not ideal and can result in radiofrequency field inhomogeneity and static field inhomogeneity respectively.

Again the present invention describes a system and method for generating contrast independent of artifacts created by field inhomogeneities which in practice occur even with proper calibration.

Method includes blocks and each of the blocks represents one or more operational acts . The order in which the method is described is not to be construed as a limitation and any number of the described method blocks may be combined in any order to implement the method. Furthermore the method can be implemented in any suitable hardware software firmware or combination thereof. Additionally although each module in is shown as a single block it is understood that when actually implemented in the form of computer executable instructions logic firmware and or hardware that the functionality described with reference to it may not exist as separate identifiable block.

In block of a first RF pulse with an arbitrary excitation flip angle is delivered. For example control system instructs hardware components e.g. causes MRI system to deliver the first RF pulse. While a 90 degree flip angle is ideally attempted those skilled in the art having the benefit of this disclosure will appreciate that a 90 degree flip angle is not achievable due to imperfections in the B field. Therefore the first RF pulse is applied at an arbitrary excitation flip angle .

In one embodiment the first RF pulse is delivered in a x direction according to the Cartesian coordinate system. The first RF pulse however is not limited to the x direction and may be delivered in other directions such as y x y etc.

In block a spin locking pulse is applied. For example control system instructs i.e. causes hardware to apply a special RF pulse or spin locking pulse which locks the spin magnetization along the effective RF field with a direction y. As appreciated by those skilled the art the spin locking pulse however is not limited to the y direction and may be delivered in other directions such as x x y etc.

Under the influence of the spin locking pulse delivered in block the magnetization produced by hardware relaxes with a time constant T rather than the typical time relaxation time constant T. This time constant T provides useful contrast when images are obtained through conventional image acquisition techniques during subsequent processing which can distinguish disease. Unfortunately because of RF field imperfections the magnetization may not be perfectly aligned along the spin locking field and will nutate i.e. rotate at a fixed angle to the applied RF field. In addition the spin locking field may not be perfectly aligned along the desired direction because of B imperfections. In a reference frame which rotates at a rate proportional to the B field the magnetization will nutate about a new effective field axis during this spin locking pulse.

In block a refocusing composite pulse is applied perpendicular to the first RF pulse applied in block . That is an approximate 180 degree pulse is applied. This refocusing composite pulse flips the magnetization about the applied pulse direction in the transverse plane. In one embodiment this refocusing composite pulse is delivered along the y direction to refocus i.e. unwind the detrimental effects of B field inhomogeneity. It should be appreciated by those skilled the art that the refocusing composite pulse however is not limited to the y direction and may be delivered in other directions such as x x y depending on the direction of prior pulses in blocks and .

In one embodiment the refocusing composite pulse is a single pulse however it should be appreciated by those skilled in the art that the refocusing composite pulse may consist of more than one pulse with an aggregate direction equivalent to transmitting a single 180 degree pulse.

In block another spin locking pulse is applied. For example control system instructs i.e. causes hardware to apply a special RF pulse or spin locking pulse which locks the spin magnetization along the effective RF field with a direction y. As appreciated by those skilled the art the spin locking pulse however is not limited to the y direction and may be delivered in other directions such as x x y etc. depending on the direction of previous pulses in blocks and .

In block a second RF pulse with an arbitrary excitation flip angle is delivered. For example control system instructs hardware components e.g. causes MRI system to deliver a second RF pulse. This second RF pulse is designed to compensate for B field inhomogeneity reintroduced by the 180 degree pulse of block .

In one embodiment the second RF pulse is delivered in a x direction according to the Cartesian coordinate system. The second RF pulse however is not limited to the x direction and may be delivered in other directions such as y x y etc. depending on the direction of previous pulses in blocks and .

In one embodiment any of the foregoing operations may be repeated using a coronal view. As appreciated by those skilled in the art having the benefit of this disclosure may be included as part of process . Alternatively obtaining images from the perspective of the coronal view may not be performed.

While shows a specific example pulse sequence process it should be understood by those skilled in the art after having the benefit of this disclosure that the pulse sequence may be performed in combination with other RF pulses. Additionally the pulse sequence may be repeated many times. The exact techniques used to deliver these pulses may vary. For example the composite refocusing composite pulse may be achieved by emitting smaller units of the signal over a linked series of pulses that may not necessarily be a part of the same pulse sequence. Thus many modifications to the sequence of operations shown in may achieve the same result.

Alternating the phase of the last 90 pulse in the spin lock pulse cluster aligns the final magnetization along the z axis rather than along the z axis . The alternation of the phase of the final 90 pulse from x to x in the cluster compensates for imperfect flip angles 90 in an inhomogeneous Bfield. The expression for the full pulse propagator is the same as Eq. 22 except for the final phase shift 2 2 2 0 26 

The key feature of Eqs. 26 and 29 is that the final phase shift x to x no longer requires that R R 90 however to completely reduce Eq. 29 to Eq. 20 we still require R 2 R 180 . In this case Eq 29 becomes 

Despite the inability to achieve a perfect 180 flip in practice artifacts are less severe than in the Binsensitive spin lock. In addition the rectangular 180 may be substituted with a composite 180 RF pulse to further reduce these artifacts 26 .

Method includes blocks and each of the blocks represents one or more operational acts . The order in which the method is described is not to be construed as a limitation and any number of the described method blocks may be combined in any order to implement the method. Furthermore the method can be implemented in any suitable hardware software firmware or combination thereof. Additionally although each module in is shown as a single block it is understood that when actually implemented in the form of computer executable instructions logic firmware and or hardware that the functionality described with reference to it may not exist as separate identifiable block.

In block of a first RF pulse with an arbitrary excitation flip angle is applied. For example control system instructs hardware components e.g. causes MRI system to deliver the first RF pulse. That is control system sends an instruction to hardware to deliver a radiofrequency pulse of flip angle . Ideally this flip angle has a desired pulse of flip angle angle tan 1 such that the magnetization is flipped parallel to the effective field in a reference frame which rotates at a rate proportional to the B field. In practice however inhomogeneity in the B field will cause this flip angle to deviate from the desired degrees.

In block a first off resonance spin lock pulse is applied. For example control system instructs hardware components to deliver the first off resonance spin lock. That is control system sends an instruction to hardware to deliver a special RF pulse or spin locking pulse which locks the spin magnetization along the effective field with direction y with respect to the transverse plane x y plane and tan 1 with respect to the y z plane. It should be noted that the effective field lies oblique to the transverse plane as result of performing operations associated with block . This condition is known as off resonance spin locking because in addition to delivering an RF pulse of direction y an instruction is also sent to hardware to deliver the RF pulse off resonance. That is the RF pulse frequency is no longer exactly equal to the rate of spin rotation in the B field but deviates by several Hz kHz. Under the influence of the off resonance spin locking pulse the magnetization relaxes with a time constant Trho off rather than the typical relaxation time constant T. This special relaxation time gives useful contrast to the image which can distinguish disease.

While the first off resonance spin lock pulse is applied is delivered in a y direction according to the Cartesian coordinate system. The first off resonance spin lock pulse however is not limited to the y direction and may be delivered in other directions such as x or y etc.

In block a second off resonance spin lock pulse having an inverse phase and frequency from the first off resonance spin lock pulse is applied. For example control system instructs hardware components to deliver the second off resonance spin lock. That is control system sends an instruction to hardware to deliver a special RF pulse or spin locking pulse which locks the spin magnetization along the effective field with direction y with respect to the transverse plane x y plane and tan 1 with respect to the y z plane. It should be noted that this arrangement is different from the spin locking pulse in block because the RF field is delivered off resonance at exactly equal to the inverse of the off resonance condition in block i.e. . It is necessary that both the phase direction and the frequency of this RF pulse are inverted in order to refocus or unwind the detrimental effects of RF field inhomogeneity.

While the second off resonance spin lock pulse is applied is delivered in a y direction according to the Cartesian coordinate system. The second off resonance spin lock pulse however is not limited to the y direction and may be delivered in other directions such as x or y etc. depending on the direction of the previous off resonance spin locking pulse.

In block a second RF pulse with the arbitrary excitation flip angle inverse to the arbitrary excitation flip angle of the first RF pulse of block is applied. For example control system instructs hardware components to deliver the second RF pulse with the arbitrary excitation flip angle inverse to the arbitrary excitation flip angle of the first RF pulse. That is control system sends an instruction to hardware to deliver another RF pulse with amplitude ideally tan 1 but because of RF field inhomogeneity may not be exactly . Because of the compensating effects of block however image artifacts are removed.

One feature of the embodiment of method is the use of the inverse phase and frequency in block . Conventional off resonance spin locking techniques simply extended the duration in block by a factor of 2 however this does not compensate for inhomogeneities in the RF field.

While shows a specific example pulse sequence process it should be understood by those skilled in the art after having the benefit of this disclosure that the pulse sequence may be performed in combination with other RF pulses. Additionally the pulse sequence may be repeated many times. The exact techniques used to deliver these pulses may vary. For example it is possible to make operations performed in blocks and each any binary number of pulses of opposite phase to further compensate for field inhomogeneity.

Exemplary methods and may be described in the general context of computer executable instructions. Generally computer executable instructions include routines programs objects components data structures etc. and the like that perform particular functions or implement particular abstract data types. The described methods may also be practiced in distributed computing environments where functions are performed by remote processing devices that are linked through a communications network. In a distributed computing environment computer executable instructions may be located in both local and remote computer storage media including memory storage devices computer readable media .

The embodiments described herein are to be considered in all respects only as exemplary and not restrictive. The scope of the invention is therefore indicated by the subjoined Claims rather by the foregoing description. All changes which come within the meaning and range of equivalency of the Claims are to be embraced within their scope.

