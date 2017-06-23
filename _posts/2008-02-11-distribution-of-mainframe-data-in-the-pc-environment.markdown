---

title: Distribution of mainframe data in the PC environment
abstract: A method of distributing mainframe software and data using PC-based data media is disclosed, comprising a mainframe program for converting a mainframe sequential dataset or all or part of a mainframe library of texts or load modules to a sequential dataset of fixed length records and for reverting these converted records to its original form in the same or another mainframe data center, and procedures for downloading the converted mainframe data to a PC and uploading the PC file to a mainframe. The converted mainframe data downloaded to a PC can be delivered to another mainframe data center using floppy diskettes, recordable CD-ROM, Internet Website, TCP/IP FTP, or email attachment, as an alternative to magnetic tapes. The PC hard disk is used as a backup storage of the mainframe libraries, and a mainframe text library downloaded to a PC can be edited on a local or remote stand-alone PC.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08868515&OS=08868515&RS=08868515
owner: 
number: 08868515
owner_city: 
owner_country: 
publication_date: 20080211
---
This is a divisional of copending application Ser. No. 10 935 464 filed on Sep. 7 2004 which is a continuation of application Ser. No. 09 726 462 filed Nov. 29 2000 now U.S. Pat. No. 6 886 160 B1 claims the benefit thereof and incorporates the same by reference.

The invention relates to the distribution method of mainframe data using PC based data media. More specifically the invention relates to a mainframe program for allowing the file transfer of mainframe sequential datasets and libraries of texts or load modules between a mainframe computer and a PC and between two mainframe computers using floppy diskettes recordable CD ROM Internet world wide web TCP IP FTP and email attachment thus providing an alternative to magnetic tape reels and tape cartridges also allowing the PC hard disk to be used as a backup storage of the mainframe libraries as well as for allowing a mainframe text library which is downloaded to a PC to be edited on a local or remote stand alone PC workstation.

There are currently more than 21 000 mainframe data centers worldwide. More than 2 trillion dollars has been invested in mainframe software around 150 billion lines of COBOL code alone worldwide . Mainframe computers are becoming less expensive 100 000 MIPS in 1992 2 300 MIPS in 2000 and 840 in 2002 . 70 of all business information resides in mainframe databases. The operation costs of the distributed computing based on mini computers are high. More than anything else businesses need machines with enough computative power a need which mini computers cannot satisfy. Mainframes will continue to be the main workhorses for big businesses for the foreseeable future.

Mainframes have been upgraded by replacing the former dumb terminals such as the IBM 3270s terminals which provided little more than a keyboard and a display screen with desktop personal computers PCs . These PCs can also be used as stand alone computers for text editing word processing and other office tasks when not being used as mainframe terminals.

A PC can connect to a mainframe system with the proper software and proper communication link. A PC terminal connects to and communicates with a mainframe through an IBM Systems Network Architecture SNA 3270 protocol emulation software. The PC can operate as a LAN terminal using a LAN server an SNA gateway and a 3270 emulation software e.g. Attachmate Extra Personal Client . The PC can work as a stand alone mainframe terminal through a Synchronous Data Link Control SDLC communication board a leased line modem and a 3270 emulation software such as Attachmate Extra 3270 Elite or Dynacomm Elite . Or an Internet enabled PC can work as a stand alone mainframe terminal through a Telnet server which supports TCP IP application protocol TN3270 clients with TN3270 Telnet SNA 3270 protocol emulation software such as QWS3270 Plus TN3270 Telnet Application of Jolly Giant Software or E Term for IBM of DCSi.

The following procedure Procedure 1 is a PC mainframe connection procedure for an Internet enabled PC with QWS3270 Plus TN3270 application software of Jolly Giant Software 

A PC connected to a mainframe with an IBM SNA 3270 protocol emulation software or the TN3270 Telnet software supports file transfers between the mainframe and the PC using the IBM mainframe program IND FILE . An Internet enabled PC connected to a mainframe FTP server using the TCP IP file transfer protocol FTP also supports the file transfer between the mainframe and the PC.

The three file transfer procedures Procedures 2 4 between a mainframe and a PC are explained as examples. The first procedure Procedure 2 is a file transfer during a TSO session using Attachmate Extra SNA 3270 emulation software 

The second procedure Procedure 3 is for an FTP file transfer started from the Attachmate main screen without a TSO session 

After the mainframe file is transferred to a PC the mainframe data stored in a PC can be copied to a PC related data media repeatedly. Ubiquitous PC usage worldwide and the file transfer capability make it possible to send and receive data between mainframe data centers using PCs. Furthermore the rise of PC based technologies in exchanging information such as email attachments using SMTP the Internet world wide web and FTP send receive facility allow data centers to transfer mainframe data using methods which were not previously available.

However mainframe installations still send their mainframe libraries of texts and program load modules to other data centers using the half inch thick 9 track 1600 6250 BPI 1 200 foot 8.5 inch diameter or 2 400 foot 10.5 inch diameter round reel tapes created from IBM 3420 3430 Magnetic Tape Units or 18 track 550 foot 38 000 BPI tape cartridges created from IBM 3480 Magnetic tape Units located in the mainframe computer rooms. There have been no alternatives until now. These magnetic tapes or cartridges require IBM proprietary magnetic tape units.

There are two main reasons for using magnetic tapes exclusively to deliver a mainframe library. First a part or whole of a mainframe library can not be downloaded file transfer from a mainframe to a PC as a whole. Currently each member of the mainframe library can only be downloaded individually one at a time. Therefore a mainframe library can not be delivered to other data centers using PC based data media. At mainframe data centers libraries are processed only by dataset utility programs developed by IBM. Currently IBM does not provide the capacity to distribute a mainframe library via PC related data media.

Second only sequential datasets of fixed length records a flat file in PC terms or text datasets of undefined record format can be delivered to another data center using PC related data media and be safely reverted to its original form at another mainframe data center. While any sequential datasets can be downloaded to a PC a single file at a time not all sequential datasets can be reverted to their original form when uploaded file transfer from a PC to a mainframe at the same or another data center.

During the downloading process each mainframe record is concatenated to the previous record to create a long thread of string and stored upon the PC. The uploading process breaks down this long concatenated string of PC data into separate mainframe records. A text file can be downloaded to a PC in text mode with a carriage return CR hexadecimal value 0D and line feed LF hexadecimal value 0A marker appended to the end of each record as a record separator. This file can then be uploaded to a mainframe and reverted to its original form by detecting the CR LF separator as a marker for the end of each record.

In general any text file or hexadecimal file of fixed length records can be transferred to a PC in binary mode without appending a record end marker and can be reverted to its original form when uploaded to a mainframe in the same binary mode. This is possible only because the length of all records are the same and each record can be separated at the same length even without record separators. Text sequential datasets of undefined record format are rarely in use.

Mainframe load modules are not of fixed length records they are of undefined record format and they contain a lot of non character hexadecimal data. As a result mainframe load modules can not be reverted to their original form when they are uploaded back to a mainframe. Therefore currently mostly text datasets of fixed length records e.g. usually members of text libraries are delivered member by member to other mainframe data centers using PC based data media.

The mainframe library is a partitioned dataset PDS and is equivalent to a PC directory or subdirectory which contains a large number of files as its components. The mainframe library also contains components so called members. There are only two types of mainframe libraries a text library with only text members and a load library with only program load module members. Each member has records in it. Members of a library have common attributes such as the record format maximum record length and length of each record. Each member can be handled as a separate sequential dataset. A single member of a text or load library is simple to process but the processing of a library as a whole is not simple.

Text library members have fixed length records of 80 bytes long and are used for storing program source codes macros procedures PROCs JCL statements help texts instructions manuals documents and letters. Currently only text library members are downloaded to a PC one member at a time and copies of each text member are delivered using PC based data media if necessary. A part or whole of a text library is still delivered using conventional magnetic tapes or cartridges exclusively.

The mainframe program load module is different from text files. The members of a load module library are all executable program load modules the output of the IBM linkage editor IEWL also called a load module and the equivalent of a PC program file with .exe .com or .dll extensions . Each member has individual records in it. Each record of a load module contains mostly non readable non character hexadecimals interspersed with some readable characters. The length of any record can be different from that of any other record. The load library is defined only with the maximum record length at least 256 bytes but usually greater than 12 000 bytes upto 32 760 bytes . Each record can be less than 256 bytes long or longer than 256 bytes up to 32 760 bytes long.

These load modules must be transferred to a PC in binary mode due to the fact that it contains hexadecimal data. A single program load module is handled as a sequential dataset of undefined record format and it is not of fixed length records. Each record of different length must be separated from the next record by an end marker when downloaded to a PC similar to the use of CR LF as mentioned above in the case of the text mode transfer. However this end marker can be confused as normal hexadecimal data and can not be handled correctly when uploaded to a mainframe. So each record of a load module is concatenated at the end of the previous record without a separating marker when downloading. If this concatenated string of data which does not possess a record separator is uploaded to a mainframe in binary mode again the end of each record can not be determined. Therefore the uploaded file will not have its original form and will no longer be executable.

In summary currently only a sequential dataset of fixed length records e.g. a member of a text library can be delivered to other mainframe data centers using PC related data media. A part or whole library can not be downloaded to a PC as a single unit so magnetic tapes or cartridges are exclusively used for the distribution of a part or whole of a program load library or text library to other mainframe data centers.

A new mainframe program PCFORM converts the content of the whole or a part of any mainframe library of load modules or texts or any sequential dataset of fixed record format undefined record format or variable record format to a sequential dataset of fixed length records . These converted data can be subsequently downloaded to a PC and reverted to their original form in the same or another mainframe data center if uploaded from a PC.

This invention makes it possible for software text and load libraries and VSAM and DB2 datasets which are sequential datasets of undefined record format to be transferred to another data center. Any libraries or any sequential datasets can be transferred to another data center.

This invention allows the mainframe data transfer to be conducted using PC based data media as an alternative to the conventional magnetic tape reels and tape cartridges. The new program PCFORM can be even distributed by a diskette a recordable CD ROM over the world wide web via FTP or as an email attachment and installed at the user s mainframe without having to use the aforementioned tapes. After the installation of PCFORM any kind of library can be transported to that data center via any PC data media.

The PC based data media mentioned above to be used in conjunction with this invention can include any of the following 3.5 inch standard 1.44 MB floppy diskettes 650 700 MB recordable CD ROM s 100 MB or 250 MB ZIP disks 3.5 inch 120 Mbytes SuperDisk diskettes email Internet Website TCP IP FTP or TELNET and any other PC data media technologies which will be widely used in the future such as recordable DVD ROM s.

This invention helps mainframe programmers download their mainframe texts and load modules from expensive mainframe disks to cheap and high capacity PC hard disks. This allows mainframe programmers to use PC hard disk space to store backups of their mainframe work text data and load modules. This avoids the excessive buildup of backup libraries within mainframe disks as well as the external accumulation of magnetic tapes.

By downloading the mainframe text library data to a PC the mainframe programmers can perform routine text editing work on a stand alone PC work station instead of signing on to the mainframe. The copy of the downloaded PC file can be carried to a remote PC where the mainframe programmer can perform any text editing.

The main benefits of this invention are derived from the facts that 1 PCs are ubiquitous and familiar to most mainframe data center users 2 most mainframe data centers already have a file transfer facility between their PC terminals and the mainframe 3 a PC hard disk file of the downloaded mainframe dataset can be used repeatedly 4 copying from a PC hard disk to PC based data media is simpler easier and faster than creating a mainframe magnetic tape 5 delivery is easy and simple 6 emerging CD ROM Internet TCP IP FTP and email can be used 7 PC data media can be a convenient means for the backup storage of a mainframe text library and load library and 8 a PC local or remote can be used as a stand alone working station for mainframe text editing especially for program source codes.

The only requirement to be able to use this invention is that the sender and the receiver of this portable PC data media must have a file transfer facility between a mainframe and a PC. Then the program PCFORM can be installed on their mainframe system using the invention itself without using any magnetic tapes from the start. After the program PCFORM is installed a part or whole of any library or any sequential dataset can be downloaded to a PC delivered to other mainframe computer data centers using PC based data media and uploaded from a PC in those receiving mainframe data centers.

There has been a need to better integrate emerging PC technology with mainframe technology and to use the more convenient and cost effective PC environment data transportation media in mainframe software libraries and data distribution. Also there was a need to use cheap and high capacity PC hard disks for storing mainframe text libraries and use the PC as a stand alone text editing work station for mainframe text library data in the PC hard disk.

The invention provides a method and apparatus for converting a part or whole of a mainframe software load library or text library or a mainframe sequential dataset of fixed record format undefined record format or variable record format to a sequential dataset of fixed length records which can be distributed using PC based data media to other mainframe computer data centers.

One embodiment of the invention provides a method and apparatus for reverting a mainframe software libraries and data delivered via PC based data media to its original form when uploaded to a mainframe computer at the same site or at another site.

A further embodiment of the invention provides a method and apparatus for storing mainframe text libraries in a PC hard disk and working at a local or remote stand alone PC for text editing of mainframe program source codes macros JCL streams procs manuals documents and letters which were downloaded from a mainframe.

As an example explanation let s assume that a software company a sender wants to deliver a whole text library a program load module and a whole load library of a software package to a customer data center a receiver by tape . This explanation assumes that the name of a sender is BSoft Co. The name of the software package to be delivered is assumed to be CPGM. Receiver of this product CPGM will be referred to as C Co. The JCL streams of JCL Lists 1 and 2 explain how the events of are actually handled in the mainframe data centers. The job control language JCL specifies the program name and the required files for the program. JCL streams or statements are entered to the operating system by the SUBMIT TSO command from the TSO ISPF screen. The OS interprets these JCL statements brings up the program from the step library or system load library allocates the requested files and passes the CPU control to the program.

A sender programmer of a sending site starts a JCL stream of JCL List 1. An IBM utility program IEBCOPY copies a whole text library a program load module and a whole load library to tapes as the output. A computer operator mounts the blank tape on the tape drive units when prompted by a system console . After IEBCOPY finishes copying system console prompts the unloading of tapes .

Receiver programmer receives delivered tapes . Receiver programmer checks the volume serial number of tapes and creates a JCL stream of JCL List 2. Receiver programmer at brings received tapes to a computer room and starts a loading JCL streams in JCL List 2 which requests a tape mount and copies the content of tapes to destination libraries . After a load job finishes the computer operator unloads tapes .

The tape delivery method is characterized by the operator interventions tapes two tape control units in two computer rooms and moving tapes between computer rooms and programmers work areas .

This new PC data media delivery method can be used in two different ways when the receiver with and without the program PCFORM installed.

For both above two situations of Procedures 5 and 6 the first three steps are for sender i.e. a mainframe software vendor company to create PC hard disk file s from a whole or part of program load module library a whole or part of text library or a sequential dataset of a sender s mainframe system.

The last three steps are for receiver i.e. general user mainframe data centers to convert data delivered in PC data media to members of mainframe destination load module library or text library or a sequential dataset . At step if program load module library and or text library already exists in a user data center only the delivered members of libraries will be added or updated in place.

A downloaded mainframe data file in PC hard disk can be copied to a Website and downloaded by authorized mainframe users via the Internet as in . The program can be sent to each email user directly as an email attachment as in . Or receiver programmer can receive the content of sender s mainframe download dataset via TCP IP FTP as in .

The above two different situations and are described in more detail. All blocks except blocks of TSO File Transfer and IND FILE in the figures represent different JCL streams JCL Lists 3 4 6 7 9 and 12 which are explained in more detail. is described first and then are explained.

For this example explanation the JCL streams assume that the name of sender is ASoft Co. the developer of the program PCFORM. The name of the program to be delivered is assumed to be PCFORM. In the example receiver does not have the program PCFORM. Receiver of this product PCFORM will be referred to as C Co. with a mainframe data center . Program PCFORM is assumed to be in the program library ASOFT.LOADLIB at sender . The delivered PCFORM will be installed in C Co. s destination load library C.ASOFT.LOADLIB .

The left side of describes the download procedure for sender to create portable floppy diskette or recordable CD ROM .

The first step of creating download sequential dataset is done by use of an IBM linkage editor program IEWL . The maximum record length of input load module PCFORM in the COPYLIB load library is usually very large e.g. up to 32 760 bytes. The maximum record length of an output temporary load module member in a SYSLMOD temporary load library is defined as 256 bytes as a default this is the recommended length. The BLKSIZE value of SYSLMOD temporary load library must be 256 bytes or greater. But the BLKSIZE of 256 bytes is recommended. Step converts original load module PCFORM into new temporary load module of shorter records. IBM linkage editor IEWL performs this conversion when sender programmer enters a JCL stream of JCL List 3 to the operating system.

Here the SYSLIN control information may be adjusted for each program load module and receiver of this program will use this SYSLIN control information when he uploads the program delivered. Depending on the software program the first SYSLIN line ENTRY control statement may or may not be required and can have a different name from that of the program.

Output temporary load module TEMPTEMP in the SYSLMOD library is still an executable load module which means that the length of each record in the module may be different from the length of others.

At the next step program PCFORM converts temporary load module TEMPTEMP to download sequential dataset of uniform fixed length records. This conversion is necessary because only uniform fixed length records of a load module can be reverted to the original load module status when they are downloaded to a PC and uploaded to a mainframe back again. Program PCFORM is executed by entering a JCL stream of JCL List 4 to the OS 390 by sender programmer at 

The LRECL value of output download sequential dataset specified by OUT ddname must be the same as the BLKSIZE value 256 bytes is recommended and is used as the default of IN temporary load library created by a JCL stream of JCL List 3. The disk SPACE value of OUT download sequential dataset is approximately the same as the size of original program load module when the value of its LRECL is near 256.

Original program load module library itself can be used directly as the IN dataset of above JCL stream JCL List 4 . In this case linkage editor IEWL step which was necessary in the previous case can be eliminated. But because the LRECL value of OUT download sequential dataset must be the same as the BLKSIZE value of the IN dataset and due to the large BLKSIZE of original load library e.g. up to 32 760 the LRECL value of OUT download sequential dataset becomes correspondingly very large. Thus the total output size to transfer between a mainframe and a PC and between two mainframe data centers can be very large. This is not recommended. The smaller the LRECL value of the OUT dataset the smaller the amount of the data which needs to be transferred. This is why the minimum allowable value 256 bytes is recommended as the default value.

Sender programmer at transfers the content of mainframe download sequential dataset DOWNLOAD.WORK to PC as C pcform.exe in Binary mode using Procedure 2 3 or 4.

Sender programmer at copies C pcform.exe to a PC data transportation medium e.g. a floppy diskette A pcform.exe or a recordable CD ROM D pcform.exe.

This dataset data can include letters installation guides installation JCLs help information manuals and other documents.

A downloaded load module file in PC hard disk can be copied to a Website and downloaded by authorized mainframe users via the Internet as in . The program can be sent to each email user directly as an email attachment as in . Or receiver programmer can receive the content of sender s mainframe download dataset via TCP IP FTP as in .

The right side of describes the functional event flow at receiver s mainframe site referred to as the upload procedure for the user data center.

Receiver programmer at of mainframe site receives floppy diskettes or CD ROM mailed from sender and saves the content of diskettes or CD ROM to the hard disk of PC . Receiver programmer at copies A pcform.exe or D pcform.exe to C ASOFT pcform.exe.

Receiver programmer at submits a JCL stream in JCL List 5 to the mainframe operating system to create upload sequential dataset destination program load library and destination text library which will receive the data delivered.

The LRECL value 256 of FILE1 upload sequential dataset must be the same value as the LRECL value 256 bytes recommended and used as the default of download sequential dataset of sender .

The BLKSIZE value 32 760 of FILE2 destination load library is the maximum allowed value and is the value which is recommended to use for the transfer. This value can be changed to any number equal to 256 bytes or greater.

Receive r programmer at transfers delivered data in PC C ASOFT pcform.exe to mainframe upload sequential dataset UPLOAD.WORK in Binary mode using Procedures 2 3 or 4.

Receiver programmer at submits a JCL stream in JCL List 6. JCL List 6 then calls IBM dataset utility program IEBGENER and copies the content of SYSUT1 upload sequential dataset into a temporary member TEMPTEMP of SYSUT2 destination load library .

Temporary output member TEMPTEMP or of SYSUT2 destination load library is not executable. Its only purpose is to be used as the input for linkage editor IEWL in a next JCL stream of JCL List 7.

Receiver programmer at then submits a JCL stream in JCL List 7 which calls IBM utility program linkage editor IEWL and converts non executable member TEMPTEMP of COPYLIB library to an executable load module member PCFORM in the SYSLMOD destination load library.

JCL List 7 creates an executable final load module member PCFORM which was delivered in a converted form via diskette or CD ROM in SYSLMOD destination load library .

This example description illustrates how single load module PCFORM was delivered via floppy diskette or CD ROM without having to use conventional magnetic tape and is installed just using the available IBM utility programs at mainframe user data center even without the help of the program PCFORM.

In summary this invention will now allow a general mainframe user company e.g. C Co. to receive any library and any sequential datasets from any mainframe software company using any kind of PC based data media without any need whatsoever for the conventional magnetic tapes which are being currently used for such transfers.

A situation in which both sender and receiver have program PCFORM will now be explained. In this scenario both sender a software company and receiver a general mainframe data center have installed program PCFORM by the method depicted in and as explained above.

The JCL streams of this diagram also assumes for the sake of convenience as in the explanation that the name of sender a mainframe software company is assumed to be BSoft Co. A client company of BSoft Co. is assumed to be C Co. The name of a mainframe software package to be delivered to C Co. is CPGM. The load modules and related texts of the mainframe software package CPGM reside in the libraries BSOFT.CPGM.LOADLIB and BSOFT.CPGM.TEXTLIB at BSoft Co. They will be installed into the destination libraries C.CPGM.LOADLIB and C.CPGM.TEXTLIB of C Co. Program PCFORM is assumed in the program library BSOFT.ASOFT.LOADLIB at BSoft Co. and C.ASOFT.LOADLIB at C Co.

This example diagram is based on the use of 3.5 inch standard 1.44 MB floppy diskettes and . Using recordable CD ROM media is simpler than floppy diskettes.

We will begin by detailing the download procedure for sender to create portable floppy diskettes containing the data to be transferred.

Sender programmer at creates a JCL stream in JCL List 8 for creating download sequential dataset of fixed length records.

The primary and secondary quantity of CYLinders may be different depending on the size of each target load library or text library to be delivered and whether a whole or part of the library or just a single member is to be delivered. One cylinder can hold approximately 650 K bytes of data. In the above example the SPACE parameter specifies a maximum of 160 cylinders and an approximate maximum of 104 million bytes equivalent to approximately 7 2400 ft magnetic tape reels . Download sequential dataset is used repeatedly so SPACE parameter should be allocated a high enough value to fit all the libraries to be sent out.

The LRECL value of texts is fixed at 80 bytes. There is no variety and thus no confusion about the LRECL value for a text library. But for program load modules sender programmer at can choose any fixed LRECL value of 80 or greater for download sequential dataset DOWNLOAD.WORK 52. Receiver programmer at of mainframe site must use this same LRECL value to create upload sequential dataset . In order to avoid any confusion the LRECL value of download sequential dataset can be fixed at 80 bytes long as a default value for both the program load modules and texts. The LRECL value 80 is strongly recommended. And this default value of 80 bytes length is used in this example explanation. This dataset of 80 bytes record length can be used for both text libraries and load libraries.

When program load modules are sent out to users sender programmer may notify receiver programmer about the BLKSIZE value of original load module library e.g. BSOFT.CPGM.LOADLIB . Receiver programmer can create destination program load module library with the BLKSIZE value suggested by sender programmer or greater up to the maximum allowed BLKSIZE value of 32 760 which can receive any BLKSIZE value of original load library .

Sender programmer at submits the above IBM dataset utility program IEFBR14 JCL stream JCL List 8 to create download sequential dataset DOWNLOAD.WORK .

Download sequential dataset and other download work datasets which will be created later will be used repeatedly for each library download. Therefore the full procedure from the submission of PCFORM program to the completion of the file transfer to a PC must be done separately for each library whether it is a load library or a text library. A library is downloaded to a PC one library at a time.

Sender programmer at creates a JCL stream JCL List 9 which will bring up program PCFORM from the STEPLIB library. The IN DD statement identifies original text or load library to be delivered. The OUT dataset is download sequential dataset .

The DUMP CONTROL command without any member makes program PCFORM dump whole records in IN input original text or load library to OUT output download sequential dataset .

The CONTROL control command DUMP converts the content of IN original library to OUT download sequential dataset records. The DUMP command starts at column and can be followed by any number of library member names in this case only the named members will be dumped to download sequential dataset . More than one member list lines can follow the DUMP control command line but the first column must be blank. Using DUMP control command without any member names as shown in the above sample JCL stream will convert the whole content of original library to download sequential dataset records.

Let s start with the download of load library first. The download procedure of a text library will be repeated after the completion of the load library download.

Sender programmer at submits above PCFORM program JCL stream JCL List 9 to dump the software package in original load library to download sequential dataset .

If output download sequential dataset is too big for a standard 1.44 MB floppy diskette the records in download sequential dataset must be divided into smaller sequential datasets in order to use 1.44 MB floppy diskettes as the transportation media. This division is necessary only for 1.44 MB floppy diskettes. If a recordable CD ROM is used this division is not necessary. Also if the data is to be transferred over the world wide web or the TCP IP FTP this division is not necessary.

If a text member or a part or whole of a text library is downloaded to a PC sometimes it can be edited in the PC using a PC word processor or an ASCII editor. Therefore it is handy to keep the text file small enough to edit in the PC using ASCII editor. Some ASCII editors can not handle larger files.

For load modules this division can be done only in the mainframe. But for texts this division can be done in the mainframe or in a PC with PC word processors or ASCII text editors.

One 3.5 inch floppy diskette can deliver 1.4 million bytes or up to approximately 17 000 records of 80 byte length mainframe records. But let s use the number 15 000 as an example for simplicity. If the library to be downloaded is a text library it is recommended to divide the library into smaller datasets which are easier for PC text editors to handle.

If download sequential dataset DOWNLOAD.WORK contains more than 15 000 records of 80 byte long it is necessary to create more than one smaller temporary work sequential datasets e.g. DOWNLOAD.WORK1 and DOWNLOAD.WORK2 and so on until the whole library can be divided into approximately 15 000 80 byte records per each smaller dataset. These temporary smaller datasets are created using the same DCB parameters as download sequential dataset that is DSORG PS RECFM FB LRECL 80 BLKSIZE 8000 but with a different SPACE parameter SPACE CYL 1 1 for example.

And sender programmer at divides the content of download sequential dataset DOWNLOAD.WORK into smaller datasets of 15 000 records for each dataset using the TSO ISPF EDIT panel or another software program. For an explanation let s assume that download sequential dataset was divided into four smaller datasets DOWNLOAD.WORK1 DOWNLOAD.WORK2 DOWNLOAD.WORK3 and DOWNLOAD.WORK4.

Sender programmer at transfers mainframe download sequential datasets to the hard disk of PC individually in Binary mode using Procedure 2 3 or 4 

1. if download sequential dataset itself is to be downloaded download DOWNLOAD.WORK to the PC file C CPGM.exe or

Now whole original load library is stored in the hard disk of PC . It is ready to be delivered to any client user data center e.g. including C Co. in this example.

Now let s repeat the full download procedure for text library . As mentioned before the download for each individual library starts with the submission of program PCFORM JCL stream JCL List 10 .

This time the IN dataset of PCFORM program is a text library . Same download sequential dataset is used repeatedly as the OUT dataset. So the previous content of download sequential dataset will be overwritten with new content every time after this step .

After PCFORM program is finished successfully the content of download sequential dataset can be divided into smaller work datasets e.g. DOWNLOAD.WORK1 DOWNLOAD.WORK2 DOWNLOAD.WORK3 DOWNLOAD.WORK4 and so on using the same method as used for the load library above.

As the final step of the text library download sender programmer transfers the mainframe datasets to the hard disk of PC individually in Text mode using Procedure 2 3 or 4 

1. if download sequential dataset itself is to be downloaded download DOWNLOAD.WORK to the PC file C CPGM.txt or

Now whole program load library and or whole text library are stored in the hard disk of PC . They are ready to be delivered to any client user data center e.g. C Co. in this example.

Sender programmer at copies all parts of the downloaded libraries from the hard disk of PC to PC data media . In the case of the example below the libraries are copied to 1.44 MB floppy diskettes 

This data will be accompanied with letters installation guides installation JCLs help information manuals and other documents.

As like the explanation of diagram downloaded load module and text files in PC hard disk can be copied to a Website and downloaded by authorized mainframe users via the Internet as in . The files can be sent to each email user directly as an email attachments as in . Or receiver programmer can receive the content of sender s mainframe download dataset via TCP IP FTP as in .

The right side of the show the upload procedure for each user data center which received the diskettes of a library.

Receiver programmer submits a JCL stream in JCL List 11 to create required datasets destination load library destination text library and upload sequential datasets e.g. UPLOAD.WORK1 UPLOAD.WORK2 UPLOAD.WORK3 and UPLOAD.WORK4 to receive the data delivered.

The LRECL value of upload sequential datasets UPLOAD.WORKN must be the same value as LRECL value of download sequential dataset DOWNLOAD.WORK at sender s site . The LRECL value of 80 bytes is the default value for the sender. But sender may use a different value so receiver must be careful about this LRECL value.

The disk space parameters of destination load library and destination text library must be carefully decided. This space must be sufficient to receive all the data delivered. Mostly sender supplies this information. Upload sequential datasets are used repeatedly for each upload of both the text and load library data so it is recommended to allocate enough D space to fit all situations.

At the above the BLKSIZE value 32 760 of destination load library C.CPGM.LOADLIB is the maximum allowed value and is recommended and set as the default value. This value can be changed to any value equal to or greater than the BLKSIZE value of original load library at sender which is usually supplied by sender .

Like the download procedure of each library the whole upload procedure from the first step of the file transfer step to the completion of loading the final library is also performed repeatedly for each individual library delivered. Each library must be uploaded separately individually.

Let s start with the upload of the load library data delivered. The upload procedure for the text library data will be repeated later after the completion of the upload of the load library data.

Receiver programmer now transfers PC files of original load library to mainframe upload sequential datasets in binary mode using Procedure 2 3 or 4.

Receiver programmer has to load all the contents of upload sequential dataset to destination load library by running program PCFORM . A PCFORM program JCL stream in JCL List 12 is submitted and program PCFORM loads all the data in IN upload sequential datasets to OUT destination program load library .

Here the CONTROL control command LOAD converts the content of upload sequential datasets to the members of destination library . The LOAD command starts at column and can be followed by any number of library member names. More than one member list lines can follow the LOAD control command line but the first column of the following lines must be blank. In this case only the named members are picked up from upload sequential datasets and loaded to destination library . The LOAD control command without any member names as shown as in the above sample JCL stream will load the whole content of upload sequential datasets to destination library .

Now delivered original load library or load modules were loaded into destination program load module library . This was done without the use of magnetic tape.

The upload of a part or whole of a text library also can be done in just the same way. At first the PC files of delivered text data are transferred to mainframe upload sequential datasets and the content of upload sequential datasets are loaded to destination text library by a program PCFORM JCL stream JCL List 13 .

Receiver programmer transfers the PC files of original text library to mainframe upload sequential datasets in Text mode using Procedure 2 3 or 4.

Receiver programmer loads all the transferred content to destination text library by running program PCFORM JCL stream shown in JCL List 13 which is just the same as above load library upload procedure except for the OUT library name. The IN dataset is upload sequential dataset and OUT dataset is final destination text library .

Text members or a whole text library were loaded into destination text library . JCL Lists 12 and 13 are similar except the OUT datasets.

Any sequential dataset of fixed record format undefined record format or variable record format can be transferred to another mainframe using PC based data media and can be reverted to its original form when uploaded as depicted in .

The events in can be explained using JCL streams of JCL Lists 14 and 15 which are similar to JCL Lists 9 or 10 and JCL Lists 12 or 13 with only small differences. The IN dataset in JCL stream of JCL List 14 at the sender s site and the OUT dataset in JCL List 15 at the receiver s site are sequential datasets of fixed record format undefined record format or variable record format respectively. The block size of both IN and OUT sequential datasets must be the same when they are of undefined record format or variable record format. The logical record length of both IN and OUT sequential datasets must be same when they are of fixed record format. Download and upload procedures of are exactly the same as in .

If two mainframe data centers have the program PCFORM one data center can send any sequential dataset and a part or whole of a load library or a text library using PC based data transportation media. Any data center can be a sender or a receiver of mainframe data.

If the receiver does not have the program PCFORM it can only receive a single load module but it can not receive a library or other dataset. This feature is useful to send the program PCFORM to other mainframe data centers using PC based data media.

This invention solves the download and upload problems of a single load module a part or whole of a load module library a part or whole of a text library and a sequential dataset by converting to a download sequential dataset of fixed record format.

Fixed record format means that each record has the same length. As the explanation in the section of the Discussion of Related Art only a sequential dataset of fixed record format can be downloaded to a PC and uploaded to a mainframe from a PC into its original form. A dataset which is not of fixed record format must be converted to a sequential dataset of fixed record format first to be delivered to another mainframe data center. The download sequential dataset of the sender and the upload sequential dataset of the receiver are defined as a fixed record format and their logical record length must be the same.

For undefined record format dataset only the block size is given and each block has only one record in it. So the block size is the maximum length of the records. Minimum record length can be 1 byte long. Each record can have different record length of from 1 byte to the maximum record length defined. This type of dataset cannot be reverted to its original form if downloaded to a PC and uploaded back to a mainframe. This type of dataset must first be converted to a sequential dataset of fixed record format to be delivered to another mainframe data center.

Many VSAM datasets and DB2 datasets are of undefined type record format. For VSAM dataset it s not called undefined record format but it does have undefined record lengths. In many VSAM datasets its maximum record length and average record length are given. Here average record length is just an average value not a minimum value. Each record length can be from 1 byte long to the maximum record length defined. When these VSAM datasets are copied to a sequential dataset the sequential dataset must be of an undefined record format.

Although the invention has been described with reference to a particular arrangement of events features sequences and the like these are not intended to exhaust all possible arrangements or features and indeed many other modifications and variations will be ascertainable to thoseof skill in the art.

