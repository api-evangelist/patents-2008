---

title: Information processing apparatus having printer driver and sheet parameter setting method for printer driver
abstract: It is necessary to switch print settings and color processing tables to optimum ones in accordance with a type of sheet which is used in a printer. In the case of enabling a new sheet to be used, a setting can be easily added without newly forming a whole printer driver. Print set information regarding the new sheet is set into a media script and fetched into a media block via a compiler. Control is made so as to store the print set information from a media database API into a media database. When the new sheet is selected on a driver display screen, the media database is searched from the media database API and print data is formed on the basis of the print set information.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07929169&OS=07929169&RS=07929169
owner: Canon Kabushiki Kaisha
number: 07929169
owner_city: Tokyo
owner_country: JP
publication_date: 20080516
---
This application is a division of U.S. patent application Ser. No. 11 781 501 filed Jul. 23 2007 now pending which is a division of U.S. patent application Ser. No. 10 614 096 filed Jul. 8 2003 now U.S. Pat. No. 7 339 693 issued Mar. 4 2008.

The invention relates to an information processing apparatus having a printer driver and a sheet parameter setting method for the printer driver and more particularly to a method for allowing a printer driver to newly use sheet parameter information adapted to a new media.

Hitherto there is software called a printer driver which is installed into a computer and converts data that is outputted by application software into a command train that can be interpreted by a printer.

In the case of performing color printing by a printer of an ink jet type the printer driver needs to switch various parameters such as printing method resolution color processing table and the like in accordance with media type of paper as a print target so that an optimum print result can be obtained. For this purpose a parameter group depending on those media is installed in the printer driver proper parameters are selected from it in accordance with the media selected by the user and the printing is executed.

Since the parameter group to be used has previously been installed in the printer driver as mentioned above in the case of adding a new media the printer driver itself needs to be updated.

It is an object of the invention to realize addition replacement deletion or the like of a media without changing a printer driver main body by raising a degree of freedom of handling of a parameter group which depends on the media that is by making the parameter group independent of the printer driver main body.

To accomplish the above object according to the invention there is provided a printer driver for forming print data to a designated printer in accordance with a request of application software comprising holding means which has a structure that can be accessed independently of the printer driver main body and holds print set information according to a type of sheet that is necessary when the print data is formed obtaining means for when it receives a print instruction from the application software obtaining the print set information corresponding to the instructed sheet type from the holding means and forming means for forming the print data on the basis of the print set information obtained by the obtaining means wherein the holding means has an input unit for adding and changing the print set information from the outside.

According to the invention there is provided a sheet parameter setting method comprising a forming step of forming information regarding a print setting according to a type of sheet which can be used by a printer a converting step of converting the formed print set information into a format which is used by a printer driver of the printer a fetching step of fetching the converted print set information into a database in which the print set information of each sheet of the printer driver has been stored and a forming step of searching the selected print set information of the sheet from the database and forming print data on the basis of the print set information.

Other features and advantages of the present invention will be apparent from the following description taken in conjunction with the accompanying drawings in which like reference characters designate the same or similar parts throughout the figures thereof.

To set the parameters of the media into the printer driver first the media script corresponding to the media to be supported is formed by an external computer or the like. shows an example of a media script of a certain media plain paper . S denotes a line for designating the media ID . S denotes a line for designating the character string of the name and plain paper is described here. S denotes a line for designating the paper feeding method and cassette paper feed and manual paper feed are described here. S denotes a line for designating the paper delivering method and standard paper delivery is described here. S to S designate the parameters shown on the right side from the print quality A in . S denotes the resolution and 300 dpi is designated here. S denotes the halftone process A and error diffusion is designated here. S denotes the color processing table and a binary file put in a certain location is designated here. In a manner similar to the above S to S designate the parameters shown on the right side from the print quality B and S to S designate the parameters shown on the right side from the print quality C.

As mentioned above the media script for one certain media is formed and converted into the media block by using the compiler . Subsequently the media block is implemented into the media DB by using the database managing tool . By repeating those processes a plurality of media blocks to be supported are implemented as shown in . In this example three types of media blocks of plain paper coating paper and glossy paper have been installed.

The compiler and the DB managing tool can be executed by the user or can be also executed from the printer driver.

When the printer driver is activated it obtains a list of the media IDs of the sheets to be supported by itself from the media DB by using the media DB API .

When the user selects an arbitrary media type on the display screen of the printer driver obtains the parameter group corresponding to the media from the media DB via the media DB API .

When all print settings are completed and the user starts the printing by clicking an OK button the printer driver obtains a table necessary when a color process is executed to the print data.

As described above the printer driver obtains the various parameters regarding the media from the media DB and executes the printing.

Subsequently an example in the case of adding a media to the media DB or deleting a specific media will be described.

First as described in the first embodiment the media script corresponding to the new media to be added is prepared. It is now assumed that OHP film is added as a new media. A script and a color processing table regarding OHP film are formed by a computer or the like and they are converted into the media block by using the compiler .

The media block of the formed new media is added to the media DB by using the DB managing tool . The DB managing tool disconnects a link of a pointer set from the media block of glossy paper to the terminal so far and inserts the media block of OHP film into such a link. The link of a pointer set from the media block of OHP film to the terminal is set. In the case of deleting the media block of coating paper as an unnecessary media a link of a pointer of the media block of plain paper so far is disconnected and it is newly connected to a link of a pointer to the media block of glossy paper .

By executing the above processes when the printer driver obtains the list of the media IDs included in the media DB next time three types of media plain paper glossy paper and OHP paper can be obtained. Therefore the contents of the selecting item of the media type in can be changed without changing the printer driver at all.

The invention can be applied to a system constructed by a plurality of devices for example a host computer an interface device a reader a printer and the like or can be also applied to an apparatus for example a copying apparatus a facsimile apparatus or the like comprising one device.

The object of the invention is also accomplished by a method whereby a memory medium or a recording medium in which program codes of software for realizing the functions of the embodiments mentioned above have been recorded is supplied to a system or an apparatus and a computer or a CPU or an MPU of the system or the apparatus reads out and executes the program codes stored in the memory medium.

In this case the program codes themselves read out from the memory medium realize the functions of the embodiments mentioned above and the program codes themselves and the memory medium in which the program codes have been stored construct the invention.

The invention incorporates not only a case where a computer executes the read out program codes so that the functions of the embodiments mentioned above are realized but also a case where an operating system OS or the like which is operating on the computer executes a part or all of actual processes on the basis of instructions of the program codes and the functions of the embodiments mentioned above are realized by those processes.

Further the invention incorporates a case where the program codes read out from the memory medium are written into a memory provided for a function expanding card inserted into a computer or a function expanding unit connected to a computer thereafter a CPU or the like provided for the function expanding card or the function expanding unit executes a part or all of actual processes on the basis of instructions of the program codes and the functions of the embodiments mentioned above are realized by those processes.

As many apparently widely different embodiments of the present invention can be made without departing from the spirit and scope thereof it is to be understood that the invention is not limited to the specific embodiments thereof except as defined in the appended claims.

As described above according to the invention by providing the database for storing the print set information per sheet independent of the printer driver main body a process such as addition replacement deletion or the like of the sheet which is supported by the printer driver can be freely changed without changing the printer driver itself so that the work regarding the updating of the driver can be efficiently executed.

