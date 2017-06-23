---

title: Control method for information storage apparatus, information storage apparatus and computer readable information recording medium
abstract: A control method for an information storage apparatus has the steps of: providing redundancy of information stored in the information storage apparatus; a redundancy failure recording part recording a record of a redundancy failure in a state recording part, when the failure has occurred in keeping of the redundant state of the information; a redundancy monitoring part reading the record of the redundancy failure from the state recording part the record; and a reporting part reporting the redundancy failure when the record of the redundancy failure is read by the redundancy monitoring part.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07962781&OS=07962781&RS=07962781
owner: Fujitsu Limited
number: 07962781
owner_city: Kawasaki
owner_country: JP
publication_date: 20080617
---
The present invention relates to a control method for an information storage apparatus an information storage apparatus a program and a computer readable information recording medium and in particular to a control method for an information storage apparatus having a function of providing redundancy to information stored in the information storage apparatus the information storage apparatus a program for causing a computer to carry out the control method and a computer readable information recording medium storing the program.

In an information storage apparatus mounting hard disk drives in such a manner that redundant hard disk drives are provided for the purpose of improving reliability of information stored therein a redundancy failure may occur in which a hard disk drive providing the redundancy has a light trouble.

For example as shown in an information storage apparatus as a computer called an SVP service processor for managing and controlling a large scale computer mounts two hard disk drives HDD and HDD storing an SVP control program and control data required for achieving a user operation function a maintenance function a testing function a communication function with an external monitoring apparatus and so forth.

The SVP is also provided with an HDD redundancy control part for managing and controlling these two hard disk drives as resources having a redundant duplicated configuration.

The HDD redundancy control part partitions the two hard disk drives in the identical configurations and carries out duplicating control in the thus obtained partition units.

Further when detecting an un restorable trouble in one of these two hard disk drives in the example of the hard disk drive HDD the HDD duplicating control part switches operation of the partition having the trouble in the example of a partition into a non duplicated control state of using only the normal one of the hard disk drives and thus operation of the SVP control program as a host system continues in the state.

In this case the HDD duplicating control part reports the fact that the redundancy of the hard disk drives i.e. the duplicated state thereof has thus partially failed to a maintenance staff.

It is noted that in the specification and claims redundancy fails or redundancy failure means from a state where information is provided with redundancy that is the information is copied thus a plurality of sets of information each having identical contents are created and thus the plurality of sets of information having the identical contents are duplicately stored in a plurality of recording media respectively i.e. a redundant state not all but one of the above mentioned plurality of sets of information having the identical contents has a trouble so that the redundancy fails.

It is noted that in such a redundancy failure the remaining ones of the plurality of sets of information having the identical contents have no trouble thus no actual loss in the information has occurred and thus merely an expected advantage for security of the information from the redundancy thus lowers to a corresponding degree.

That is in the example of a frequency of occurrences of a situation that such an restorable trouble also occurs on the hard disk drive on the normal side for the partition for which partition the duplicated state has thus already failed in the preceding redundancy failure is low. Accordingly it may be said that urgency for an actual exchange work of the trouble hard disk drive which is a cause of the above mentioned redundancy failure is not so high.

However it is not preferable that such a state that the redundancy failure is left un solved for a long period. The possibility that the corresponding partition may have a trouble also in the hard disk drive on the normal side is small but is not zero. When such a situation that the hard disk drive on the normal side also has a trouble occurs the corresponding information may be actually lost and thus operation of the SVP may have to be interrupted. Therefore it is preferable that a maintenance staff rapidly prepares a new hard disk drive and exchange the trouble hard disk drive therefor for a restoration from the redundancy failure to positively avoid such a serious situation.

On one hand the large scale computer which the SVP monitors and controls has numerous devices parts and components as well as many items to be reported for maintenance other than the above mentioned trouble of the hard disk drive of the SVP and occurrence frequencies of these items to be reported are high.

When a light trouble causing a redundancy failure for a partition is detected in the hard disk drive this matter is reported to a maintenance staff from the SVP. However assuming that many other items to be reported having higher priority occur by accident simultaneously these items are simultaneously reported to the maintenance staff and thus the reporting of the above mentioned light trouble in the hard disk drive may be overlooked.

The present invention has been devised in consideration of such a situation and an object of the present invention is to provide a configuration such that when a trouble occurs in keeping redundancy of information stored in an information storage apparatus a measure to solve the trouble can be positively carried out.

According to the present invention a redundancy state of information stored in the information storage apparatus is provided a redundancy failure is recorded by a redundancy failure recording part when the redundancy failure has occurred in keeping the redundant state of the information the record of the redundancy failure is read by a redundancy monitoring part and the redundancy failure is reported by a reporting part when the record of the redundancy failure is read by the redundancy monitoring part.

In the present invention since the record of the redundancy failure is thus read by the redundancy monitoring part and then the record is reported by the reporting part.

Therefore even if a maintenance staff misses immediate handling an initial report made when the redundancy failure has occurred and leaves it un solved the record of the redundancy failure is read by the redundancy monitoring part and the record is reported again by the reporting part when the record is thus read by the redundancy monitoring part.

Thus it is possible to positively avoid such a situation that the redundancy failure is left un solved for a long period.

Thus by the present invention when a trouble occurs in keeping redundancy in an information storage apparatus having a function of providing redundancy to information stored in the information storage apparatus it is possible to prevent a redundancy failure state if any from being left un solved for a long period. As a result redundancy of the information stored in the information storage apparatus can be positively maintained and thus it is possible to effectively ensure security of the information stored in the information storage apparatus.

According to the embodiment 1 of the present invention in an apparatus in which hard disk drives having a redundant duplicated configuration are managed and controlled and operation can be continued with a non redundant configuration even when a trouble has occurred in one hard disk drive if the trouble is left unsolved the trouble is detected and reported automatically the unsolved state is detected again and is reported repetitiously periodically and each time power supply to the apparatus is started up.

In the computer system includes a body apparatus which has a system board and around it various sorts of functional units SSM SSX SSX SSU IOP I O and CLK .

A body apparatus consol is a consol for a user to operate various functions which the computer system provides i.e. functions provided by an OS which operates in the system board .

An SVP consol is a consol for operating for a user operation function a maintenance function or a testing function. In a user mode only the user operation function can be operated. In a maintenance mode operation required for maintenance can be made. The maintenance mode is used when user operation is interrupted and maintenance is carried out.

A maintenance terminal is a consol used for a user to operate for functions required for maintenance when maintenance is carried out without interruption of user operation i.e. active maintenance . This consol is connected only when active maintenance is carried out.

An SVP has an MPU microprocessor unit a cache a ROM a RAM hard disk drives which have the above mentioned duplicated configuration an MO drive a flexible disk drive and so forth.

The above mentioned SSU and I O are connected externally to the body apparatus . The SSU is a system storage unit and the I O is an input output unit such as a DASD.

Further the following parts are connected inside of the body apparatus and are controlled or maintained by the SVP 

A SSM SS Mover It is connected to the SSU and carries out data transfer between a main memory and a system memory.

A SCI system consol interface It provides an interface for control and communication made by the SVP for the respective parts in the body apparatus .

The SVP service processor It provides the user operation function the maintenance function the testing function and a communication function for an external monitoring apparatus .

A SCIA SCI adapter It is an adapter which carries out communication and control of the body apparatus via the SCI .

A SCA SVP communication adapter It connects to a LAN for carrying out communication with the external monitoring apparatus or with another SVP .

Software of the SVP has a program providing an SVP internal diagnosis function provided in the ROM and an SVP control program stored in the hard disk drives . The SVP control program has a kernel a frame task an interrupt task an initializing task an error log task and a patrol task .

The initializing task provides a function to detect a trouble of the hard disk drives and the patrol task provides a function to detect an overlooked trouble of the hard disk drives .

The SVP control program further has a hard disk driver a flexible disk driver a LAN port driver a display device control driver a SCI driver and a RS232C part driver .

The above mentioned program provided in the ROM carries out diagnosis of the inside of the SVP . That is the program reads HDD duplicating control information written in header parts partitions of the hard disk drives and develops the contents thereof i.e. HDD duplicating control information in a memory i.e. a RAM . Further this program loads the SVP control program from the hard disk drives .

The kernel carries out state control of the respective tasks which the SVP control program has exclusive control and communication control between the tasks. Further the kernel carries out management and control of memory resources timer resources and files.

The HDD duplicating control part of the hard disk driver carries out control of duplicating i.e. providing redundancy with the hard disk drives with the use of the above mentioned duplicating control information

Further the HDD duplicating control part calls the SCSI control part which then carries out starting up of the hard disk drives stopping the same reading information therefrom writing information thereto or such.

Further the HDD duplicating control part starts up the error log task through a system call when the hard disk drives have a trouble and the error log task carries out reporting of the trouble.

The SCSI control part carries out starting up of the hard disk drives stopping the same setting an operation mode thereof writing information to the hard disk drives reading information therefrom obtaining trouble information therefrom and so forth.

It is noted that the SCSI control part controls the two hard disk drives and as well as the MO drive .

The display device control driver carries out communication control with the consol of the body apparatus and the consol of the SVP .

The RS232C part driver carries out communication control with the maintenance terminal according to RS232C.

The SPC driver carries out communication control with the SPC . By means of the communication with the SPC control for starting of power supply to the computer system and disconnecting the same is carried out.

The initializing task carries out initialization and starting up of each task which the SVP control program has when the SVP is started up and also it carries out check for an overlooked trouble of the hard disk drives . When an overlooked trouble of the hard disk drives is detected by the initializing task the initializing task starts up the error log task which then carries out reporting the trouble.

Further the patrol task is periodically started up and carries out monitoring of a state of the body apparatus and also carries out monitoring an overlooked trouble of the hard disk drives . The patrol task is started up every 500 ms every 60 minutes every day or every week depending on what is monitored.

Monitoring of an overlooked trouble of the hard disk drives by the patrol task is carried out every week. Then when an overlooked trouble of the hard disk drives is detected by the patrol task the patrol task starts up the error log task which then carries out reporting the trouble.

The error log task is started up through a system call by the task which has detected the trouble when the trouble of the body apparatus the trouble of the inside of the SVP or the trouble of the hard disk drives has occurred and then stores an error log displays on a consol or a panel and reports to the monitoring apparatus .

The frame task provides the user operation function and the maintenance function through the SVP consol or the maintenance terminal .

The user operation function corresponds to control functions provided by the body apparatus and corresponds to various functions for example a communication control function for a large scale communication network or such which the computer system should provide to the user as a basic role thereof.

The maintenance function corresponds to a maintenance exchange function for exchanging parts components of the body apparatus and the SVP themselves.

The interrupt task carries out processing for interrupt made from the body apparatus notified of through the SCI .

That is according to the embodiment 1 of the present invention the HDD duplicating control part reads information from the hard disk drives detects a trouble if any of the hard disk drives upon writing information thereto and reports the trouble Step S .

That is when a light trouble of the hard disk drives i.e. a duplication failure i.e. a redundancy failure of a specific partition in the example of a partition is detected the monitoring apparatus or the SVP consol reports this matter to a maintenance staff through a communication LAN LAN .

Further through the function of the patrol task periodic monitoring is carried out and thereby an overlooked trouble of the hard disk drives is detected and reported Step S .

That is when a trouble is left unsolved even after a predetermined period has elapsed since the light trouble of the hard disk drives i.e. the duplication failure of the partition partition occurred the light trouble is thus detected and is again reported to the maintenance staff by means of the monitoring apparatus or the SVP consol through the communication network LAN LAN . In the same manner the state is monitored every predetermined time interval and the light trouble is thus detected and is reported to the maintenance staff rapaciously until the duplicated state is restored i.e. the light trouble is solved .

Further by the function of the initializing task the unsolved trouble of the hard disk drives is detected and reported when the computer system is started up Step S .

That is when a trouble of the hard disk drives i.e. a duplication failure in a partition is left unsolved and is detected even after operation of the system is stopped by the maintenance staff after the duplication failure of the partition is detected and then operation of the system is again started since the light trouble of the hard disk drives i.e. the duplication failure in the partition partition occurred the light trouble is again reported to the maintenance staff by means of the monitoring apparatus or the SVP consol through the communication network LAN LAN .

As a result it is possible to effectively avoid a problematic situation that a light trouble of the hard disk drives is left unsolved for a long period. Thus it is possible to avoid a further problematic situation that operation of the SVP should be interrupted due to multiple troubles in the hard disk drives which may otherwise occur due to the light trouble being left unsolved for a long period. Thus it is possible to provide a high reliable information storage function.

Below a configuration of the SVP concerning the function of providing redundancy to information will be described in further detail.

The two hard disk drives and are partitioned in the same configuration and the identical data is stored in the same position of the respective hard disk drives and .

An area allocated to the same position in each of the two hard disk drives is called a partition and is handled as a unit in the duplicating control.

For each partition identical information is possessed by both a first one i.e. a master one of the two hard disk drives and a second one i.e. a slave one thereof duplicately. That is information of each partition is possessed in a duplicated or a redundant state.

To the two hard disk drives identification numbers are given in an order corresponding to positions at which the hard disk drives are mounted in the body apparatus of the computer system started from . Below the hard disk drives may be referred to as hard disk drives HDD HDD respectively for the sake of convenience of explanation hereinafter.

Further the plurality of partitions are given identification numbers started from in an order corresponding to addresses in the hard disk drives .

The HDD duplicating control information is configured by data tables corresponding to the identification numbers of the partitions.

Further for each table not only the number of a master hard disk drive which has the corresponding partition but also the number of a trouble hard disk drive if any which also has the corresponding partition duplicately may be written.

The HDD duplicating control information is stored in the partitions corresponding to header parts of storage areas of the respective hard disk drives .

The HDD duplicating control information is read from the hard disk drives when power supply to the computer system is started is then developed in the memory and thus a duplicated configuration of the hard disk drives in previous operation is kept.

Further when a state in the hard disk drives changes during operation of the computer system the information developed in the memory is updated accordingly and simultaneously the HDD duplicating control information written in the partitions is updated.

Further in the HDD duplicating control information a duplication effective state is recorded which is read when a trouble occurs in the hard disk drive or and thus the trouble hard disk drive should be exchanged with a new one where the trouble hard disk drive should be disconnected for the exchange purpose. The duplication effective state is information which indicates whether or not the hard disk drives are in a duplicated state or in a non duplicated state.

When information is written in the hard disk drives the HDD duplicating control part writes the identical information to corresponding areas of the two hard disk drives which duplicately have the corresponding partitions as mentioned above.

Further when information is read from the hard disk drives the information is read from the area of the master hard disk drive thereof.

When an error has occurred upon the above mentioned writing operation the master hard disk drive or the slave hard disk drive of the hard disk drives allocated for the partition at which the error has occurred is recognized as having a trouble.

When the master hard disk drive allocated for a partition at which information is written or read has a trouble the hard disk drive on the side on which the trouble had not occurred i.e. the slave hard disk drive is then recognized as a new master hard disk drive for the partition.

 4 Reporting of a Trouble of the Hard Disk Drives by the HDD Duplicating Control Part i.e. Step S in 

When a trouble has occurred in the master hard disk or the slave hard disk allocated for a partition the HDD duplicating control part recognizes that a light trouble has occurred in the hard disk drives i.e. a duplication failure has occurred in the partition.

When thus detecting the light trouble of the hard disk drives i.e. the duplication failure of the partition the HDD duplicating control part reports it to a maintenance staff by means of the monitoring apparatus or the SVP consol 10s1 as mentioned above.

The patrol task of the SVP control program carries out periodic monitoring for a trouble which may occur in the hard disk drives . The patrol task is started up at intervals of every week and monitors whether or not a light trouble of the hard disk drives i.e. a duplication failure in a partition exists.

When it is detected that such a light trouble exists the light trouble is reported to a maintenance staff by means of the monitoring apparatus or the SVP consol .

Further the patrol task monitors as to whether or not a light trouble exists in the hard disk drives every week as mentioned above and thus repetitiously reports to a maintenance staff the light trouble until the light trouble is solved i.e. the duplicated state i.e. redundant state of the hard disk drives is restored.

When operation of stopping the computer system is made by a maintenance staff and after that operation of the system is started again the initializing task of the SVP consol program determines whether or not the hard disk drives has a light trouble i.e. whether or not a duplication failure in a partition has occurred.

When detecting such a light trouble in the hard disk drives the initializing task reports to a maintenance staff by means of the monitoring apparatus or the SVP consol .

In the above mentioned duplication effective state indicates the above mentioned duplicated state or non duplicated state of the hard disk drives as below 

When a trouble hard disk drive is disconnected for the purpose that the trouble hard disk drive is exchanged in an active exchange manner a non duplicated operation state with only HDD or non duplicated operation state with only HDD occurs. That is a state in which any one of the hard disk drive operates solely occurs. As a result the duplicated redundant state of the stored information breaks and thus the non duplicated state occurs.

That is when any one of the hard disk drives has a trouble operation is carried out only with the normal one. This state of operation is called non duplicated operation . In such a case the hard disk drive having the trouble is disconnected and then is replaced with a newly prepared hard disk drive in an active state.

 ON RESTORATION INDICATING FLAG in indicates that the hard disk drives are in duplication restoration work as below 

That is when the duplication state breaks i.e. any one of the hard disk drives has a trouble and thus operation is carried out only with the normal one. Then when the depiction state is to be restored information is copied from the normal one to another which is newly prepared replaced with and thus is newly mounted.

 PARTITION n DUPLICATION STATE n . . . indicates whether or not the partition has a duplicated state as below 

In PARTITION n MASTER HDD n . . . indicates a master hard disk drive and a slave hard disk drive for a partition as follows 

That is when the partition has a duplicated state i.e. in the above mentioned PARTITION n DUPLICATION STATE which indicates HDD for the partition has a trouble or such HDD corresponds to an operation hard disk drive and thus acts as a master.

As mentioned above when the partition has a duplicated state indicates HDD for the partition has a trouble or such HDD corresponds to an operation hard disk drive and thus acts as a master.

Here a flow starting from an occurrence of a trouble in the hard disk drives through actual exchange of the trouble hard disk drive will be described.

In this case it is assumed that in the duplicated state of the hard disk drives the hard disk drive HDD acts as a master.

It is noted that HDD duplicating control of the hard disk drives includes handling of the duplicating control information stored in the partition the same as that on the other partitions. However for the sake of convenience of explanation the duplicating control information in the partition is treated as simple information and logical description is omitted therefor.

In when a maintenance staff makes operation to start power supply to the computer system Step S header parts of the hard disk drives are read by means of the above mentioned SVP internal diagnosis function of the program provided in the ROM Step S and the thus read HDD duplicating control information is developed in the memory Step S . This processing will be described later with reference to .

Next in the same manner by means of the SVP internal diagnosis function the SVP control program is read from a header part of the master hard disk drive HDD of the hard disk drives and is developed in the memory Step S . Thus boot of the kernel is completed Step S .

Next the kernel starts up the initializing task of the SVP control program Step S . The initializing task carries out detection of a trouble if any of the hard disk drives . This processing i.e. the above mentioned processing of Step S will be described later with reference to .

After the initializing processing of the initializing task is properly completed Step S the predetermined user operation function is executed Step S and thus a predetermined operation data file is read from the master hard disk drive HDD Step S .

A case is assumed that a trouble has occurred during the processing of reading the predetermined operation data file from the hard disk drives for the purpose of carrying out the user operation function . That is it is assumed that a trouble has occurred in the master hard disk drive HDD and then a trouble is detected upon reading from the partition thereof Step S .

In this case it is assumed that the HDD duplicating control part tries reading from the partition of the salve hard disk drive HDD and this reading is completed successfully Step S .

The HDD duplicating control part responds thereto and updates the HDD duplicating control information developed in the memory with the contents that the hard disk drive HDD thus has the trouble in its partition Step S . Further the duplicating control part updates with the same contents the contents of the header part partitions of the hard disk drive on the normal side Step S .

Next the HDD duplicating control part reports to the kernel the trouble of the hard disk drive HDD as a light trouble Step S .

Then it is assumed that except the above mentioned reading failure in Step S reading of the above mentioned operation data file has been properly completed Step S .

Then it is assumed that execution of the above mentioned user operation function has been properly completed Step S .

Next in the kernel starts up the error log task which then reports to a maintenance staff the above mentioned occurrence of the light trouble by means of the monitoring apparatus or the SVP consol Step S .

Then after an elapse of one week the kernel starts up the patrol task which then carries out check of the duplicated state of the hard disk drives Step S . This processing will be described later with reference to .

As a result it is detected that the trouble of the hard disk drive HDD for the partition exists Step S .

After the completion thereof Step S the kernel starts up the error log task which then reports to a maintenance staff the light trouble again by means of the monitoring apparatus or the SVP consol Step S .

Further after another elapse of one week the kernel again starts up the patrol task Step S . After that the processing of Steps S through S the same as the above mentioned processing of Steps S through S is carried out.

Then it is assumed that a maintenance staff makes operation to stop power supply to the computer system Step S .

As a result under the control of the kernel by means of the initializing task the hard disk drives are stopped by the HDD duplicating control part Steps S through S . In response thereto the initializing task breaks power supply to the computer system Step S .

Next in when a maintenance staff then makes operation to starts power supply to the computer system the same as the operation starting from Step S mentioned above the SVP internal diagnosis function by the program in the ROM reads the header parts of the hard disk drives Step S . It is noted that as mentioned above in the header parts the trouble of the partition of the hard disk drive HDD is recorded in Step S.

Further the SVP internal diagnosis function develops the HDD duplicating control information thus read in the memory Step S . Then the SVP control program is loaded in the memory Step S and thus boot of the kernel is completed Step S .

Next the kernel starts up the initializing task of the SVP control pogrom Step S and the initializing task carries out processing of detecting a trouble if any of the hard disk drives . As mentioned above this processing i.e. the above mentioned processing of Step S will be described later with reference to .

In this processing the initializing task recognizes the trouble of the partition of the hard disk drive HDD reports the light trouble to a maintenance staff by means of the error log task and also by means of the monitoring apparatus or the SVP consol Steps S S and thus finishes this initializing processing Step S .

After further another elapse of one week the kernel again starts up the patrol task Step S . After that the processing of Steps S through S the same as the above mentioned processing of the Steps S through S is carried out.

Then in it is assumed that a maintenance staff carries out in Step S active exchange of the hard disk drive HDD having the trouble as mentioned above.

In this case by means of the maintenance function of the frame task of the SVP control program the HDD duplicating control information developed in the memory in Step S is read Step S and as a result it is recognized that the hard disk drive having the trouble and thus to be exchanged in an active state i.e. active exchange corresponds to the hard disk drive HDD .

As a result the above mentioned maintenance function provides such instructions to disconnect the hard disk drive HDD from the SVP Step S in response thereto the duplicating control part stops a motor of the hard disk drive Step S and thus an HDD non duplicated operation state only with the hard disk drive HDD on the normal side is entered. Then with the contents that the HDD non duplicated operation state is thus entered the HDD duplicating control information developed in the memory and the HDD duplicating control information in the header parts of the hard disk drive on the normal side are updated Steps S and S . Then the matter that the processing of entering the HDD non duplicated operation state is completed is reported to the above mentioned maintenance function Step S .

After that the maintenance staff actually exchanges the trouble hard disk drive HDD for a new one in an active state and as a result the maintenance function provides such instructions to the HDD duplicating control part as to restore the original duplicated state with the use of the new hard disk drive HDD which is thus exchanged for by the maintenance staff Step S .

In response thereto the HDD duplicating control part updates the HDD duplicating control information developed in the memory and the header part of the hard disk drive on the normal side respectively with the contents that HDD duplication on restoration state is entered Steps S S .

Then in Step S the HDD duplicating control part restores the original HDD duplicated state as a result of the information stored in the hard disk drive HDD currently on operation being copied to the new hard disk drive HDD which is thus exchanged for.

When the copying processing is completed on all the partitions properly the HDD duplicating control information developed in the memory and the HDD duplicating control information in the header parts of both hard disk drives are updated by the contents of normal state Steps S S .

Then the HDD duplicating control part reports to the maintenance function that the HDD duplicated state restoration is thus completed Step S .

In this case since the normal state is recorded in the HDD duplicating control information developed in the memory in Step S this is read and as a result the patrol task returns to the kernel that the processing of checking the HDD duplicated state is normally completed Step S .

Thus according to the embodiment 1 of the present invention by means of the functions of the initializing task and the function of the patrol task if a state in which a duplicated state of the hard disk drives breaks is overlooked this state is reported to a maintenance staff when the SVP is started again and also periodically during operation of the computer system.

Accordingly even if the maintenance staff cannot solve the problem of breakage of the duplicated state in response to the first report after that the maintenance staff s attention can be called again when the computer system is started up again and also periodically during operation of the computer system.

Therefore it is possible to effectively avoid a problematic situation that a loss of a duplicated state of the hard disk drives is left unsolved for a long period.

Next with reference to details of the above mentioned processing of reading the HDD duplicating control information from the header parts of the hard disk drives and developing the same in the memory by the SVP internal diagnosis function of the program stored in the ROM will be described.

In by the above mentioned SVP internal diagnosis function the header part of the hard disk drive HDD is read Step S and when the reading from the header part results in failure a flag indicating it is set Yes in Step S and Step S .

Similarly the header part of the hard disk drive HDD is read Step S and when the reading from the header part results in failure a flag indicating it is set Yes in Step S and Step S .

Next in in Step S by reading the above mentioned flag it is determined whether or not reading from the header parts of both hard disk drives HDD HDD has succeeded.

When reading from the header parts results in failure for both hard disk drives HDD HDD Yes in Step S the operation of the SVP internal diagnosis function of the program of the ROM ends abnormally. In this case the processing is finished without the SVP control program being loaded. The SPC displays an error code indicating a failure of starting up of the SVP on a panel when detecting stoppage of the SVP by a life check function for the SVP. The SPC stops the processing when it is not possible to start up the program of the ROM even after trying starting up three times. 

On the other hand when reading from the header part results in failure only for the hard disk drive Yes in Step S the HDD duplicating control information properly read from the header part of the hard disk drive HDD is developed in the memory Step S .

Similarly when reading from the header part results in failure only for the hard disk drive No in Step S the HDD duplicating control information properly read from the header part of the hard disk drive HDD is developed in the memory Step S .

Further reading from the harder parts has succeeded for both hard disk drives HDD HDD Yes in Step S the following processing is carried out. That is when troubles if any of the partitions corresponding to the header parts of both hard disk drives HDD HDD are recorded in the information thus read from the header parts Yes in Step S Yes in Step S of the operation of the SVP internal diagnosis function of the program of the ROM ends abnormally. In this case the processing is finished without the SVP control program being loaded. The SPC displays an error code indicating a failure of starting up of the SVP on the panel when detecting stoppage of the SVP by a life check function for the SVP. The SPC stops the processing when it is not possible to start up the program of the ROM even after trying starting up three times. 

On the other hand when a trouble if any of the partition is recorded only for the hard disk drive HDD Yes in Step S the HDD duplicating control information properly read from the hard disk drive HDD is developed in the memory Step S .

When a trouble if any of the partition is recorded only for the hard disk drive HDD No in Step S the HDD duplicating control information properly read from the hard disk drive HDD is developed in the memory Step S .

When no trouble of the partitions is recorded for both hard disk drives HDD HDD Step S in is proceeded to.

Then when the current state is a HDD non duplicated operation state with the hard disk HDD Yes in Step S Yes in Step S the HDD duplicating control information read from the header part of the hard disk drive HDD is developed in the memory Step S .

When the current state is a HDD non duplicated operation state with the hard disk HDD Yes in Step S No in Step S the HDD duplicating control information read from the header part of the hard disk drive HDD is developed in the memory Step S .

When the current state is not a HDD non duplicated operation state i.e. the current state is a HDD duplicated operation state No in Step S the HDD duplicating control information read from the header part of the hard disk drive HDD is developed in the memory Step S .

Thus in the embodiment 1 of the present invention when the HDD duplicating control information is to be read from the header parts of the hard disk drives HDD HDD in Step S of or Step S of the HDD duplicating control information read from the header part of the hard disk drive on the side on which reading has succeeded is developed in the memory Steps S through S the HDD duplicating control information read from the header part of the hard disk drive on the side on which the partition has no trouble is devolved in the memory Steps S through S or the HDD duplicating control information read from the header part of the hard disk drive on the side on operation is devolved in the memory Steps S through S when reading from the header part of one hard disk drive results in failure when a trouble of the partition in which the header part is stored is recognized from the contents of the header part thus read or when the current state is an HDD non duplicated operation state.

As a result it is possible to develop the HDD duplicating control information which is more reliable one in the memory .

Next with reference to and details of the processing of checking a HDD duplicated state Steps S S S S of Steps S S of or Steps S S of which is carried out upon initializing processing Steps S S of or Steps S S of or periodically every week.

First the kernel starts up the initializing task upon initializing processing and the processing of checking the HDD duplicated state is carried out Step S of .

Similarly in the processing of checking the HDD duplicated state carried out periodically every week the kernel starts up the initializing task upon initializing processing and the processing of checking the HDD duplicated state is carried out Step S of .

In when the HDD duplicating control information thus developed in the memory is read Step S as a number of the hard disk drive to be read at this time i.e. HDD is set Step S .

Then when the current state is a HDD non duplicated operation state with the hard disk drive other than the thus set hard disk drive HDD i.e. the current state is a HDD non duplicated operation state with the hard disk drive HDD Yes in Step S it is reported to the kernel that the hard disk drive HDD has a trouble Step S .

On the other hand when the current state is other than an HDD non duplicated operation state i.e. the current state is a HDD duplicated operation state No in Step S the number of a partition to be read is set as Step S . Then when a trouble is recorded for the partition in the above mentioned HDD duplicating control information TROUBLE in Step S this matter is reported to the kernel Step S .

Then the number of a partition to be read is incremented by one Step S and then it is determined whether or not all the partitions have been checked Step S . Then until all the partitions are checked COMPLETED in Step S the number of a partition to be read is incremented in sequence Step S and thus the respective partitions are checked as to whether or not it has a trouble Step S . When a partition has a trouble this matter is reported to the kernel in each case Step S .

When all the partitions are thus checked COMPLETED in Step S the number of a hard disk to be checked is incremented by one Step S and thus the other hard disk drive that is HDD is checked and a trouble thereof if any is reported to the kernel in the same manner Steps S through S .

Next with reference to details of a flow of the processing of active exchange of the trouble hard disk drive starting from Step S of will be described.

In in Step S the above mentioned maintenance function reads the HDD duplicating control information developed in the memory and displays the contents thereof to a display device provided on the maintenance terminal to a maintenance staff Step S .

When in response thereto the maintenance staff makes operation on the maintenance terminal to disconnect the trouble hard disk drive Step S the function of the HDD duplicating control part disconnects the trouble hard disk drive from the SVP and a completion of this operation is reported to the maintenance function via the HDD duplicating control part .

The maintenance function responds thereto and updates the HDD duplicating control information of the head part of the on operation hard disk drive and the memory by the matter that from the above mentioned operation a non duplicated operation state is entered Step S .

Further the maintenance function urges the maintenance staff from the display device of the maintenance terminal to actually exchange the trouble hard disk drive Step S .

Next in when the maintenance staff actually carries out exchanging of the trouble hard disk drive for a new one and provides instructions to connect the new hard disk drive the maintenance function carries out operation to connect the new hard disk drive to the SVP Step S and updates the HDD duplicating control information of the on operation hard disk drive and the memory by the matter that an HDD duplication on restoration state is entered Step S .

Then by means of the HDD duplicating control part such a display is made from the display device of the maintenance terminal to the maintenance staff that such operation is started that information stored in the on operation hard disk drive is copied to the new hard disk drive and thus the original duplicated state is to be restored Step S .

After that the operation for restoring the original HDD duplicated state by copying the information stored in the on operation hard disk drive to the new hard disk drive is carried out in sequence Step S . At this time on the display device of the maintenance terminal the progress of the operation of copying the stored information is displayed Step S .

When the operation of copying the information for restoring the HDD duplicated state has been completed for all the partitions the maintenance function updates the HDD duplicating control information of the hard disk drives and the memory by the matter that the HDD duplicated state is entered by means of the HDD duplicating control part Step S .

Then on the display device of the maintenance terminal such a display is made that the active exchange of the trouble hard disk drive has been completed Step S .

When maintenance is made during the user operation being under suspension the SVP consol is operated by a maintenance staff so that a maintenance mode is entered and after that the trouble part can be exchanged in the same manner.

The embodiment 2 of the present invention has a configuration the same as that of the embodiment 1 described above and what is different from the embodiment 1 is that the number of hard disk drives for providing redundancy is three or more while the number of hard disk drives for providing redundancy is two in the embodiment 1.

The contents concerning this difference will now be described and thus duplicate description is omitted appropriately.

In this case 1 as a configuration of hard disk drives for providing redundancy the same as that of the embodiment 1 described above all the hard disk drives are partitioned in the same configuration and the same data is stored in the corresponding positions of the respective hard disk drives.

Further the same as the above mentioned embodiment 1 areas allocated to the corresponding positions in all the hard disk drives are called partitions which are regarded as units for the redundancy control.

Each partition is duplicately possessed by one master hard disk drive and one or more slave hard disk drives.

 2 As HDD redundancy control information corresponding to the above mentioned HDD duplicating control information identification numbers corresponding to mounting positions are given in order from to the plurality of hard disk drives.

Further to the plurality partitions identification numbers are given from in an order of addresses in the hard disk drives.

The HDD redundancy control information is configured by data tables corresponding to these partition numbers.

In each table the number of the master hard disk drive which possesses the partition and the number of a trouble hard disk drive if any which also possesses the partition may be written. The redundancy control information is stored in the partition .

The HDD redundancy control information is developed in a memory of an SVP from the hard disk drive when power supply to a computer system is started and the HDD redundant state in the previous operation is thus kept.

When the state of the hard disk drives providing the redundancy changes during operation the HDD redundancy control information in the memory is updated accordingly and simultaneously the HDD redundancy control information in the partitions of the hard disk drives are updated.

 3 In processing of writing into the hard disk drives by means of an HDD redundancy control part corresponding to the HDD duplicating control part in the embodiment 1 the identical data is written in all the areas of the hard disk drives having each partition.

In processing of reading from the hard disk drives data is read from the area of the master hard disk drive having each partition.

When an error occurs in the above mentioned writing processing the master hard disk or the slave hard disk having the partition is recognized as having a trouble.

When an error occurs in the above mentioned reading processing the master hard disk having the partition is recognized as having a trouble.

When the master hard disk drive having the partition has a trouble during reading processing or writing processing any hard disk drive having the corresponding partition duplicately having no trouble is allocated as a new master hard disk drive for the partition.

 4 In processing of reporting a trouble of a hard disk drive by means of the HDD redundant control part when a predetermined number of hard disk drives among the master and slave hard disk drives which duplicately or redundantly possess corresponding ones of each partition have troubles it is determined that the hard disk drives providing redundancy have a light trouble i.e. a redundancy failure in the partition .

Then when the light trouble redundancy failure in the partition is detected the light trouble is reported to a maintenance staff.

 5 A patrol task corresponding to the patrol task in the embodiment 1 having a function of periodically monitoring a trouble of the hard disk drives is periodically started up and therewith it is monitored as to whether or not a light trouble redundancy failure in a partition exists in the hard disk drives.

When a light trouble is detected in this processing the light trouble is reported to a maintenance staff. Then further every elapse of a predetermined period it is checked as to whether or not a light trouble exists in the hard disk drives. Thus until the original redundant state of the hard disk drives is restored as a result of the light trouble being solved reporting of the light trouble to a maintenance staff is repeated.

 6 In processing of detecting a trouble if any of the hard disk drives in initializing processing detecting a light trouble redundancy failure in a partition of the hard disk drives if any is carried out when operation of the SVP is started by a maintenance staff after the operation is stopped.

When a light trouble is detected in this processing the light trouble is reported to a maintenance staff.

Thus in the embodiment 2 of the present invention in a condition where redundancy of information is provided by a plurality of hard disk drives that is in a condition where the plurality of hard disk drives duplicately or redundantly store the identical information and thus security of the information thus stored is improved since even if the stored information is lost in one or some hard disk drives the number of which is smaller than the number of all the hard disk drives originally providing the redundancy among the plurality of hard disk drives the identical information is still stored in the remaining hard disk drives a matter that information stored in one or a predetermined number of hard disk drives is lost if any which number is smaller than the number of all the hard disk drives which originally provides the redundancy is automatically reported to a maintenance staff and also the reporting is carried out every time when the SVP is started up and also every predetermined intervals during operation.

As a result even if a maintenance staff misses carrying out appropriate processing i.e. exchanging the trouble hard disk or such immediately after receiving an initial report the same report is given each time when the SVP is started up and also every predetermined intervals during operation automatically. Thus it is possible to effectively avoid such a problematic situation that a state in which the redundant state is lost i.e. a redundancy failure is left unsolved for a long period.

While the invention herein disclosed has been described by means of specific embodiments and applications thereof numerous modifications and variations could be made thereto by those skilled in the art without departing from the scope of the invention set forth in the claims.

The present application is based on Japanese Laid Open Patent Application No. 2006 346213 filed on Dec. 22 2006 the entire contents of which are hereby incorporated herein by reference.

