---

title: Storage controller having virtual volume
abstract: To shorten time necessary for performing backup of data in a virtual volume managed by a storage controller to a backup destination storage device. A secondary volume including storage areas of the same number as the number of first primary virtual areas is created with respect to a primary virtual volume (a virtual logical volume to be an I/O destination from an external device) including plural primary virtual areas. The first primary virtual areas are primary virtual areas to which actual areas are allocated. Data copy is performed from the primary virtual volume to the secondary volume. At the time of backup to the backup destination storage device, data backup is performed from the secondary volume to the backup destination storage device.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08332601&OS=08332601&RS=08332601
owner: Hitachi, Ltd.
number: 08332601
owner_city: Tokyo
owner_country: JP
publication_date: 20081125
---
This application relates to and claims priority from Japanese Patent Application No. 2008 247010 filed on Sep. 26 2008 the entire disclosure of which is incorporated herein by reference.

A capacity expansion technique is known for example JP A 2003 15915 Patent Document 1 . In the capacity expansion technique when write is generated with respect to a certain virtual area in a virtual volume an unallocated actual area in a pool is allocated to the virtual area of a write destination and a data element as a write target is written in the actual area.

Data in logical volumes can be backed up by each volume. In the case that data in virtual volumes are backed up by each volume reading is generated with respect to all virtual areas therefore reading is generated also with respect to virtual areas to which actual areas are not allocated. That is unnecessary reading.

In addition meaningless data elements for example null data elements obtained by the reading are also backed up with significant data elements data elements read from actual areas allocated to the virtual volume . Accordingly meaningless data elements are stored in a backup destination therefore the storage capacity is consumed uselessly.

Furthermore in restore of data in the virtual volume not only significant data elements but also the meaningless data elements are restored therefore actual areas are allocated to all virtual areas included in the restored virtual volume. As a result actual areas will be consumed more than actual areas allocated to the virtual volume at the time of backup in addition longer time is necessary for restore.

In view of the above problems for example a technique disclosed in JP A 2008 181271 Patent Document 2 has been devised.

Data in the virtual volume managed by the storage controller is sometimes backed up to a storage device of a backup destination. It is desirable to shorten time necessary for the backup.

An object of the invention is to shorten time necessary for backup of data in virtual volumes managed by a storage controller in a backup destination storage device.

As an I O destination in accordance with an I O command from a first external device there is a primary virtual volume including plural primary virtual areas. In the case that write occurs with respect to any of primary virtual areas an unallocated actual area in a pool is allocated to the write destination primary virtual area and a data element of a write target is written in the allocated actual area.

The storage controller creates a secondary volume including storage areas of the same number as the number of first primary virtual areas with respect to the primary virtual volume. The secondary volume is for example a secondary virtual logical volume and the storage areas are secondary virtual storage areas. The first primary virtual areas are primary virtual areas to which actual areas are allocated.

The storage controller performs data copy from the primary virtual volume to the secondary volume. Therefore respective data elements stored in respective actual areas allocated to the primary virtual volume are written in the secondary volume for example respective actual areas allocated to the secondary virtual volume .

The first external device is for example a computer. However it is not limited to the computer but other storage devices can be applied.

The storage controller may be for example a storage device including physical storage media as bases of the pool or may be a device existing in a higher order of the storage device having the physical storage media for example a switch device .

At the time of backup to a backup destination storage device a control module performs data backup from the secondary volume to the backup destination storage device. The control module is provided at any of second external devices of the following 1 and 2 .

The control module is realized by for example a computer program executed by a CPU in the second external device.

Hereinafter an embodiment of the invention will be explained with reference to the drawings. In the following explanation processing will be explained by appropriately taking a computer program as a subject in order to prevent the explanation from being redundant however the processing is actually performed by a processor which executes the computer program.

A service server a backup server and a primary storage are connected to a FC SW Fible Channel Switch which forms a storage area network. The backup server is connected to a secondary storage through a communication network or a leased line. The service server the backup server and the primary storage may be connected to other types of communication networks such as a LAN Local Area Network or connected to one another through a lease line and the like.

The service server and the backup server are computers having information processing resources such as a CPU Central Processing Network and a memory which are for example a personal computer a work station a mainframe and the like. In the embodiment only one service server is written however more service servers are allowed to be provided.

In the memory of the backup server for example a computer program hereinafter referred to as a B R software for convenience for controlling backup and restore is stored as a computer program executed by the CPU in the server . The B R software issues various commands to an API Application Programming Interface provided by the primary storage as shown by a dotted arrow. The B R software also performs relay of data transfer from the primary storage to the secondary storage or data transfer from the secondary storage to the primary storage .

The secondary storage includes plural or one tape media a robot moving the tape media and a tape drive which writes or reads data with respect to tape media . The secondary storage is a storage device of backup destination. The secondary storage is not limited to a tape library device as shown in the drawing but it may be other storage devices for example a storage device having the same configuration as the primary storage.

The hardware configuration of the primary storage is shown in for example . The primary storage is a storage device including a controller and plural HDDs Hard Disk Drive it is preferable that other types of physical storage media for example a flash memory can be applied instead of the HDD . The controller includes plural ports a memory a transfer LSI Large Scale Integration a processor and a disk I F . In the plural ports there is a port which receives I O Input Output commands from the service server and there is also a port which receives commands from the backup server . The I O commands are received by a prescribed protocol for example a FC Fible Channel protocol and the commands from the backup server are received by the same protocol or another protocol for example an IP internet Protocol . The memory includes a cache area and data exchanged between the service server and the HDD or data exchanged between the HDD and the backup server are temporarily stored in the cash area. The transfer LSI controls exchange between respective elements in the controller . The disk I F is an interface with respect to the HDDs .

Referring to again the controller strictly the memory includes a backup PG a restore PG and various tables PG is an abbreviation of a program . An API for the backup PG and the restore PG is prepared. The primary storage also includes a primary virtual volume and a pool group . The backup PG and the restore PG will be described later. The pool group includes plural actual areas.

In the embodiment data in the primary virtual volume is not transferred to the backup server but a secondary virtual volume which will be a copy destination of data in the primary virtual volume is created and data in the secondary primary virtual volume is transferred to the backup server . The storage capacity of the secondary virtual volume to be created is not the same as the storage capacity of the primary storage volume but the storage capacity corresponding to one or more actual areas allocated to the primary virtual volume .

The B R software performs data backup from the creased secondary virtual volume to the tape medium in the secondary storage as shown in a solid arrow. In the data backup for example a raw data copy is performed. The raw data copy means data copy in a so called raw mode which is data copy using a function of reading data directly from a sector in the HDD that is copy which is different from copy by each track or by each file .

In the following description the primary virtual volume is referred to as PVOL and the secondary virtual volume is referred to as SVOL .

The pool group is configured by plural pools including a pool and a pool . A pool A is configured by a logical volume pool volume A formed based on a RAID group RG and a pool B is configured by a pool volume B formed based on a RAID group RG which is different from the RG which is the basis of the pool A. Respective pool volumes A B include plural actual areas. Each RAID group includes plural HDDs storing data in a prescribed RAID Redundant Array of Independent or Inexpensive Disks level.

The PVOL includes plural segments virtual areas . The segment and the actual area respectively have a prescribed storage capacity. The capacity of one segment is for example the same as the capacity of one actual area.

According to the example of actual areas and in the pool are allocated to segments and of plural segments. A data element C is stored in the actual area a data element B is stored in the actual area and a data element A is stored in the actual area . Specifically for example in the case that the controller receives a write command designating an address for example LBA Logical Block Address of the segment from the service server when an actual area is not allocated to the segment the unallocated actual area in the pool is allocated to the segment and the data element C as a write target in accordance with the received write command is written in the allocated actual area .

When the SVOL corresponding to the PVOL is created at this time the number of segments included in the SVOL is 3. Because the number of allocated segments in the PVOL is also 3. The allocated segment is a segment to which an actual area is allocated in plural segments. In the following description a segment in the PVOL is referred to as a segment P and a segment in the SVOL is referred to as a segment S .

Data copy is performed from the PVOL to SVOL . One allocated segment P corresponds to one segment S. According to the allocated segment P corresponds to the segment S the allocated segment P corresponds to the segment S and the allocated segment P corresponds to the segment S . Data copy is performed from the allocated segment P to the allocated segment S between segments corresponding to each other. At that time actual areas are allocated to segments S from the pool which is different from the pool having actual areas to be allocated to the PVOL . This is for prevent data copied in the SVOL from being lost if failures occur in the RG . According to an actual area in the pool is allocated to the segment S and the data element C is written in the actual area in the pool by the copy of the data element C from the allocated segment P to the segment S . An actual area in the pool is allocated to the segment S and the data element B is written in the actual area in the pool by the copy of the data element B from the allocated segment P to the segment S . Similarly an actual area in the pool is allocated to the segment S and the data element A is written in the actual area in the pool by the copy of the data element A from the allocated segment P to the segment S .

Data is backed up from the SVOL to the secondary storage . That is the data elements C B and A are read from the actual areas and in the pool which are allocated to the segments to included the SVOL and the data elements C B and A are backed up to the secondary storage through the backup server . In this case the actual areas are allocated to all segments S included in the SVOL therefore reading is sequentially performed from the first address of the SVOL to the end address thereby reading all data elements to be backed up.

As various tables shown in for example there are a virtual volume management table a segment management table an actual area management table and a SVOL management table. The various tables will be explained below.

The virtual management table is a table prepared for each virtual volume which is a table for managing information concerning the virtual volume. In the virtual volume management table for example a volume ID capacity information and virtual volume information are recorded.

The volume ID is an identifier of a virtual volume referred to as a target virtual volume in explanation of below corresponding to the table . The target virtual volume is for example the PVOL or the SVOL .

The capacity information is information indicating the capacity of the target virtual volume and the capacity thereof is for example a multiplier of the number of segments included in the virtual volume and the capacity of segments the number of segments the segment capacity .

The virtual volume information is information including numbers and LBAs Logical Block Address of respective segments included in the target virtual volume.

The segment management table is a table prepared for each virtual volume which is a table for managing information concerning respective segments of the virtual volume. In the segment management table for example a volume ID is recorded as well as a segment number allocation information and difference information are recorded by each segment.

The volume ID is an identifier of the virtual volume referred to as a target virtual volume in explanation of below corresponding to the table .

The segment number is an identification number allocated to a segment included in the target virtual volume.

The allocation information is information indicating which actual area is allocated to which segment. For example the allocation information includes an allocation flag and information for identifying an allocated actual area for example an actual area number . An allocation flag 1 means that an actual area is allocated to a segment corresponding to the flag and an allocation flag 0 shows that an actual area is not allocated to a segment corresponding to the flag. Information for identifying the allocated actual area is written when the allocation flag is 1 .

The difference information is information indicating whether update write has occurred or not in the segment after the data copy from the PVOL to the SVOL at the time just before in other words the difference information is information indicating whether the data element stored in the actual area allocated to the segment is a difference data element or not . The difference information includes a difference flag of 1 bit. A difference flag 1 means that update has occurred in the segment corresponding to the flag after the data copy at the time just before and a difference flag 0 means that update has not occurred in the segment corresponding to the flag after the data copy at the time just before. A segment corresponding to the difference flag 1 is referred to as a difference segment in the following description. The difference segment is also an allocation segment however the allocation segment is not always the difference segment. When update has occurred in the allocation segment after the data copy the allocation segment will be the difference segment. When update has occurred in a segment other than the allocation segment after the data copy the segment will be the difference segment.

The table is updated by the controller when the actual area is allocated to any of segments or when update occurs first in a certain segment after the data copy.

The actual area management table is a table for managing whether allocation has been performed or not with respect to respective actual areas. The actual area management table is prepared for each pool. In the table a pool number is recorded and a pool volume ID an actual area number and status information are recorded by each actual area. The pool number is an identification number of a pool corresponding to the table . The pool volume ID is an ID of a pool volume in which the actual area exists the actual area number is an identification number of the actual area and the status information indicates whether the actual area has been allocated to the virtual volume for example 1 or has not been allocated for example 0 .

The table is updated when any of actual areas is allocated to a segment or when the allocation of the actual area has been cancelled from any of segments by the controller .

The SVOL management table is a table for managing information concerning data copy from the PVOL to the SVOL . The table is prepared for each PVOL and stores information concerning all SVOLs created with respect to one PVOL .

In the SVOL management table a volume ID of a PVOL hereinafter referred to as a target PVOL in explanation of corresponding to the table is recorded. Also in the table a volume ID of a SVOL date and hour information backup type information copy destination VOL size information copy source segment information copy destination segment information and restore target information are recorded by each SVOL corresponding to the target PVOL namely by each data copy from the target PVOL to the SVOL . Hereinafter the above information will be explained by taking one SVOL hereinafter referred to as a target SVOL in explanation of corresponding to the target PVOL as an example.

The date and hour information is information indicating a date and hour when the data copy was performed from the target PVOL to the target SVOL.

The backup type information is information indicating a backup type corresponding to the target SVOL. As the backup type there are full backup and difference backup. The full backup means that data in all allocation segments P in the target PVOL is backed up. The difference backup means that data in a difference segment P of plural allocation segments P in the target PVOL is backed up. When the full backup is designated full is recorded as backup type information and when the difference backup is designated diff is recorded.

The copy destination VOL size information is information indicating the size capacity of the target SVOL. The size of the target SVOL is for example indicated by the number of segments included in the target SVOL.

The copy source segment information is information indicating allocated segments P as data copy sources in the target PVOL.

The copy destination segment information is information indicating segments S of data copy destinations in the target SVOL.

The restore target information is information whether the target SVOL is a restore target or not. In the case that the target SVOL is the restore target 1 is recorded as restore target information and 0 is recorded when the target SVOL is not the restore target.

In the full backup a SVOL hereinafter F SVOL F including segments S of the same number as the number of allocated segments P in the PVOL as described above. Then data copy is performed from all allocated segments P to all segments S. Accordingly the data elements A to C stored in three actual areas actual areas in the pool allocated to three allocated segments P are copied to three actual areas actual areas in the pool allocated to three segments S included in the F SVOL F. All data elements A to C are read from the F SVOL F and the read data elements A to C are backed up in the tape medium in the secondary storage . Specifically for example raw data copy from the F SVOL F to the tape medium is performed.

According to the backup the F SVOL F including only the allocated segments S corresponding to the allocated segments P in the PVOL is created and data backup is performed from the F SVOL F. Therefore high speed backup without unnecessary reading and data transfer can be expected.

Note that the F SVOL F may be deleted after the backup from the F SVOL F to the tape medium is completed.

In the difference backup a SVOL hereinafter D SVOL D including segments S of the same number as the number of difference segments P of the allocated segments P in the PVOL is created as described above. Then data copy is performed from all the difference segments P to all segments S. Accordingly data elements C and D stored in two actual areas actual areas in the pool allocated to two difference segments P of four allocated segments P are copied to two actual areas actual areas in the pool allocated to two segments S included in the D SVOL D. All data elements C and D are read from the D SVOL D and the read data elements C and D are backed up in the tape medium in the secondary storage . Specifically raw data copy from the D SVOL D to the tape medium is performed.

According to the backup the D SVOL D including only the allocated segments S corresponding to difference segments P of the allocated segments P is created and data backup is performed from the D SVOL D. Therefore high speed backup having the lower number of readings and the smaller amount of data can be expected as compared with the full backup.

Note that the D SVOL D may be deleted after the backup from the D SVOL D to the tape medium is completed.

Assume that a PVOL at the point of November 17 23 00 is a restore target and assume that a SVOL corresponding to the restore point is a D SVOL D.

The D SVOL D is the SVOL created at the time of the difference backup therefore even when the D SVOL D is restored from the tape medium in the secondary storage and the data copy is performed from the D SVOL D to the PVOL of the restore destination the PVOL at the time of November 17 23 00 is not restored.

Then the data copy is performed from the SVOLs to the PVOL in the order from a SVOL whose data copy date and hour are older. Specifically first data copy to the restore destination PVOL is performed from the F SVOL F after that data copy is performed to the restore destination PVOL from D SVOL D to D in the order from older date and hour of data copy. According to the series of processing data in the restore destination PVOL will be data in the PVOL at the point of November 17 23 00.

The restore destination PVOL is for example a PVOL having no allocated segment P that is the PVOL including only segments to which any actual area is not allocated in the initial state that is before the data copy from the F SVOL F is performed .

The example of shows a case in which the SVOL corresponding to the restore point is the D SVOL. In the case that the SVOL corresponding to the restore point is for example the F SVOL F shown in the drawing the F SVOL F is restored from the tape medium and data copy from the F SVOL F to the restore destination PVOL is just performed thereby completing the restore of the PVOL at the restore point.

In the embodiment when only the full backup is performed one F SVOL F is restored and data copy is performed from one F SVOL F to the restore destination PVOL for performing the restore therefore high speed restore can be expected. On the other hand when the difference backup is executed in addition to the full backup the number of actual areas consumed at the time of backup and the amount of transferred data can be reduced as compared with the case of full backup.

Hereinafter the processing flow performed in the embodiment will be explained with respect to to . In to step is abbreviated to S .

In S the service server stops the issue of I O commands for example the PVOL of the backup target is umounted . This is performed for example in response to an instruction from the backup server . In this step it is preferable that only the issue of the I O command designating the PVOL to be the backup target is stopped and that the issue of other I O commands designating other logical volumes is performed. The stop of the I O in the service server is notified to the backup server from for example the service server .

In S the B R software of the backup server transmits a SVOL creation command to the API of the primary storage in response to the stop of the I O in the service server . In the SVOL creation command for example full backup as the backup type and an ID of the PVOL primary virtual volume as a volume ID of the backup target are designated hereinafter the PVOL is referred to as a target PVOL in explanation of and . When the API accepts the SVOL creation command the backup PG is called and the SVOL creation command is received.

In S the backup PG detects that the backup type full backup is designated in the SVOL creation command calculating the actual capacity the number of actual storage areas necessary for the F SVOL. The actual capacity is calculated by the storage capacity of one segment the number of allocated segments P . Which segment P is which allocated segment P is specified by referring to allocation information of the segment management table .

In S the backup PG determines whether there is free space for the actual capacity calculated in S in the pool corresponding to the SVOL or not. The free space is calculated by the storage capacity of one actual area the number of unallocated actual areas . As a modification example it is preferable to determine whether there exist the same number of unallocated actual areas as the number of allocated segments P in the pool or not in S and S.

When a result of determination in S is negative NO in S an error is given back to the backup server .

When a result of determination in S is affirmative YES in S the backup PG creates the F SVOL F including segments S of the same number as the allocation segment P in S and data copy is performed from the allocated segments P in the target PVOL to the F SVOL F. The backup PG also updates the SVOL management table corresponding to the target PVOL . Specifically a record including the volume ID of the F SVOL F is added to the SVOL management table as the volume ID of the copy destination. In the added record the followings are recorded.

In S the I O stop in the service server is released and it becomes possible to start issuing I O commands again. The release of the I O stop is performed in response to an instruction by the B R software in the backup server which received the notification of creation completion.

In S the B R software of the backup server recognizes the F SVOL F created in S of . Specifically for example the B R software recognizes the F SVOL F by inquiring information concerning the F SVOL F for example a volume ID the storage capacity and the like which has been created in response to the SVOL creation command issued in S of .

In S the B R software receives an instruction of backup from the F SVOL F to the tape medium by for example an administrator.

In S the B R software executes raw data copy from the F SOVOL F to the tape medium . Specifically for example the B R software reads data from the F SVOL F specifically actual areas allocated to the F SVOL F by transmitting a read command in which the F SVOL F is designated issuing a write command in which the read data is designated as a write target to the secondary storage . At that time the B R software can write backup management information in which a volume ID of the F SVOL F is associated with write destination information for example a number and an LBA range of the tape medium in a storage resource for example a memory in the backup server .

In S the B R software transmits an acquisition command of the SVOL management table to the API of the primary storage .

In S the backup PG transmits information of the SVOL management table for example a copy of the table to the backup server through the API in response to the acquisition command.

In S the B R software in the backup server receives information of the SVOL management table storing the information in a storage resource for example a memory in the server .

In S for example when failures occur in the service server the B R software of the backup server receives an instruction for restoring the SVOL from for example an administrator. At the time of the restore instruction designation of restore information is received. The restore information is for example restoring date and hour indicating which point of the PVOL is restored or a volume ID. The volume ID can be an ID of the PVOL and can be an ID of the SVOL. The volume ID is for example an ID selected from information of the SVOL management table stored in the memory in the backup server .

In S the B R software transmits a creation command of a SVOL for restore to the API of the primary storage . The command includes for example a volume ID of the F SVOL F hereinafter a target SVOL F in explanation of corresponding to restore information and information including the capacity of the target SVOL F the number of segments . The storage capacity is specified for example based on the copy destination VOL size corresponding to the target SVOL F in the information of the SVOL management table. When the API accepts the creation command the restore PG is called and the restore PG receives the creation command.

In S the restore PG determines whether there is free space for the capacity of the F SVOL F or not based on the actual area management table refer to corresponding to a pool which is different from the pool for the PVOL.

When a result of determination in S is affirmative YES in S the restore PG creates the SVOL for restore having the same capacity as the target SVOL F transmitting notification of creation completion to the backup server in S. The number of segments S included in the SVOL for restore is the same as the number of segments S included in the target SVOL F. Also the same volume ID as the volume ID of the restore target F SVOL F is added to the SVOL for restore. Numbers of segments S included in the SVOL for restore are also the same as numbers of segments S included in the restore target F SVOL F. The SVOL for restore includes only segments S to which actual areas are not allocated however it is also preferable that actual areas are allocated to all segments S included in the SVOL for restore at the time of creation.

In S the B R software recognizes the SVOL for restore created in S in response to the notification of creation completion.

In S the B R software executes data copy restore from the tape medium to the SVOL for restore created in S. Specifically for example the B R software specifies at which tape medium and at which position in the tape medium the data backed up from the target SVOL F exists transmitting a read command designating the specified position to the secondary storage . Accordingly the B R software issues a write command to the primary storage which designates the SVOL for restore recognized in S with the data read from the secondary storage data stored in the target SVOL F as a write target.

In S the B R software transmits information of the SVOL management table stored in the memory of the backup server to the primary storage .

In S the restore PG receives information of the SVOL management table storing the information in the memory .

In S the B R software transmits a restore command to the restore PG which is an instruction of data copy from the SVOL for restore to the restore destination PVOL . In the restore command for example at least one volume ID of the SVOL for restore and the restore destination PVOL is designated.

In S the restore PG performs data copy from the SVOL for restore to the restore destination PVOL by referring to information of the SVOL management table in response to the restore command. At that time the copy source of data is segments S of the data copy destination which are specified from information of the SVOL management table and the copy destination of data is segments P corresponding to the segments P segments P of the data copy source which are specified from information of the SVOL management table . Actual areas are allocated to the segments P with the data copy and data elements in the actual areas allocated to the copy source segments S are written in the actual areas. At that time the restore PG updates the segment management table corresponding to the restore destination PVOL .

In S the service server mounts the restore destination PVOL . Thereby it is possible to transmit an I O command designating the restore destination PVOL from the service server .

In S the B R software transmits a SVOL creation command to the API of the primary storage in response to the stop of the I O in the service server . In the SVOL creation command for example difference backup as the backup type and an ID of the PVOL as the volume ID of the backup target are designated hereinafter the PVOL is referred to as a target PVOL in explanation of and .

In S the backup PG detects that difference backup is designated as the backup type in the SVOL creation command calculating the actual capacity necessary for the D SVOL the number of actual areas . The actual capacity can be calculated by the storage capacity of one segment the number of difference segments P . Which segment P is which difference segment P corresponds is specified by referring to difference information of the segment management table .

In S the backup PG determines whether there is free space or not for the actual capacity calculated in S in the pool corresponding to the SVOL.

When a result of determination of S is affirmative Yes in S the backup PG creates the D SVOL D including segments S of the same number as the difference segments P in S. The backup PG performs data copy from difference segments P in the target PVOL to the D SVOL D. The backup PG also updates the SVOL management table corresponding to the target PVOL . Specifically a record including a volume ID of the D SVOL D as the copy destination volume ID is added to the SVOL management table . The following information is recorded in the added record 

In S the backup PG resets all difference information in the SVOL management table namely updates all values to 0 .

In S the stop of I O in the service server is released and it becomes possible to start issuing I O commands again.

In the processing flow of backup from the D SVOL in the primary storage to the secondary storage is shown.

In S the B R software receives an instruction of backup from the D SVOL D to the tape medium from for example an administrator.

In S the B R software executes raw data copy from the D SVOL D to the tape medium . At that time the B R software can write backup management information in which a volume ID of the D SVOL D is associated with write destination information for example a number and an LBA range of the tape medium to a storage resource for example a memory in the backup server .

In S the B R software in the backup server transmits an acquisition command of the SVOL management table to the API of the primary storage .

In S the backup PG transmits information of the SVOL management table for example a copy of the table to the backup server through the API in response to the acquisition command.

In S the B R software of the backup server receives information of the SVOL management table and stores the information in the storage resource for example the memory in the server .

In S for example when failures occur in the service server the B R software of the backup server receives a restore instruction of the SVOL from for example an administrator. At the time of restore instruction designation of restore information can be received. The restore information is for example restoring date and hour indicating which point of the PVOL is restored or a volume ID.

In S the B R software searches date and hour information corresponding to the backup type full which is prior as well as nearest to the restore point specified from restore information namely the F SVOL which is prior as well as nearest to the restore point is searched by referring to information of the SVOL management table .

In S the B R software transmits a creation command of a SVOL for restore to the API of the primary storage . The command includes for example information indicating the copy destination VOL size corresponding to the specified date and hour information namely the capacity of the target SVOL the number of segments S and a volume ID of the target SVOL corresponding to the date and hour information. When the API accepts the creation command the restore PG is called and the restore PG receives the creation command. The target SVOL is a F SVOL when it is just after S and is a D SVOL when it is just after S.

In S the restore PG determines whether there is free space for the capacity of the target SVOL or not based on the actual area management table refer to corresponding to a pool which is different from the pool for the PVOL.

When a result of determination in S is affirmative YES in S the restore PG creates the SVOL for restore having the same capacity as the target SVOL in S transmitting notification of creation completion to the backup server .

In S the B R software recognizes the SVOL for restore created in S in response to the notification of creation completion executing data copy restore from the tape medium to the SVOL for restore created in S. The B R software updates restore target information corresponding to the target SVOL in the SVOL management table to 1 .

In S the B R software determines whether all SVOLs until the restore point have been restored or not. Specifically for example the B R software determines not only whether restore target information corresponding to the F SVOL hereinafter the nearest F SVOL which is prior as well as nearest to the restore point is 1 but also whether restore target information is 1 or not which corresponds to a D SVOL hereinafter the latest D SVOL corresponding to the restore point and all other D SVOLs whose copy dates and hour are between copy date and hour corresponding to the nearest F SVOL and copy date and hour corresponding to the latest D SVOL.

When a result of determination in S is negative No in S the B R software specifies a next D SVOL in S. The next D SVOL is a D SVOL corresponding to copy date and hour nearest to the copy date and hour of the nearest F SVOL which is the D SVOL whose restore target information is 0 .

According to the processing flow S is executed whenever the SVOL for restore corresponding to the target SVOL is created however it is also preferable that for example S is performed once instead of the above. Specifically the B R software calculates the capacity of all target SVOLs and notifies the result to the restore PG and the restore PG determines whether there is free space for the capacity.

In S the B R software transmits information of SVOL management table stored in the memory of the backup server to the primary storage . The restore PG receives the information and stores it in the memory .

In S the B R software transmits a restore command to the restore PG which is an instruction of data copy from the SVOL for restore to the restore destination PVOL . The restore command designates for example at least one of volume IDs of all SVOLs for restore created in the processing of or the restore destination PVOL .

In S the restore PG specifies the SVOL for restore corresponding to the nearest F SVOL in response to the restore command by using information of the SVOL management table received in S.

In S the restore PG performs data copy from the specified SVOL for restore to the restore destination PVOL by referring to information of the SVOL management table . In this case the specified SVOL for restore is the SVOL for restore corresponding to the nearest F SVOL when it is just after S and is the SVOL for restoring the D SVOL when it is just after S.

In S the restore PG determines whether data copy from all SVOLs for restore created in the processing of to the restore destination PVOL has been completed or not.

When a result of determination of S is negative No in S the restore PG specifies the next SVOL for restore in S. The next SVOL for restore is a SVOL for restore corresponding to a D SVOL corresponding to copy date and hour nearest to copy date and hour corresponding to the nearest F SVOL which is the SVOL for restore whose data copy in S has not been performed.

The preferred embodiment of the invention has been described above however it goes without saying that the invention is not limited to the embodiment and can be variously modified in the scope not departing from the gist thereof.

For example it is preferable that a computer system shown in is applied as the computer system. That is it is preferable that the back server does not exist and the B R software is provided in a secondary storage .

In addition the difference is not limited to the difference with respect to the data copy at the time just before and it may be the difference with respect to the data copy corresponding to full backup at the time just before. In other words when update does not occur in a segment P after the data copy data copy from the PVOL to the D SVOL concerning the difference backup was completed the segment P is not a difference segment P however when update has occurred in the segment P even once after the data copy concerning the full backup at the time just before was completed the segment P may be the difference segment P as it is even when update has not occurred in the segment P after the data copy concerning difference backup was completed.

