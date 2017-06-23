---

title: Information processing apparatus, method and storage medium
abstract: A printer monitoring apparatus includes a setting unit configured to set a display mode of a warning or an error related to a peripheral device, a determination unit configured to determine whether the warning or the error has previously occurred, a display unit configured to display the warning or the error in a case where the warning or the error has previously occurred, and a processing unit configured to continue a process or cancel a process according to the warning or the error based on whether the warning or the error has previously occurred.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08269991&OS=08269991&RS=08269991
owner: Canon Kabushiki Kaisha
number: 08269991
owner_city: Tokyo
owner_country: JP
publication_date: 20080606
---
The present invention relates to a printer monitoring apparatus that monitors a printer more specifically an abnormal status of a printer.

Conventionally there is a computer system where a computer monitors status of a printer to recognize abnormalities such as empty ink or out of paper conditions. Such a computer includes and executes a monitor program for monitoring the printer abnormality. The monitor program is stored in a memory and acquires the latest status of the printer at a predetermined interval of time. It then displays any abnormal status such as an error occurring in the printer. In addition to the abnormal status of the printer the monitor program can also display a warning about various print settings when printing is to be performed or display a warning about a printer setting status.

Moreover there are cases where an operator wishes to avoid an unnecessary printer status to be displayed or a printer status being redundantly displayed with the one on an application window. In such cases as discussed in Japanese Patent Application Laid Open No. 2000 293344 there is a method for allowing an operator to select a status or warning to be notified by a status monitor program. This can in turn prevent unnecessary notification.

However according to Japanese Patent Application Laid Open No. 2000 293344 when an operator sets an abnormal status of a device or a warning to a non display mode the printer may stop without printing a print job or without giving any explanation on the cause. As a result the printer may be stopped in an error status even if another user wishes to print. Further if a user tries to print from a personal computer PC in which a warning is issued the user cannot proceed with printing because the previous job is stopped without being printed.

According to an aspect of the present invention a printer monitoring apparatus includes a setting unit configured to set a display mode of a warning or an error related to a peripheral device a determination unit configured to determine whether the warning or the error has previously occurred a display unit configured to display the warning or the error in a case where the warning or the error has previously occurred and a processing unit configured to continue a process or cancel a process according to the warning or the error based on whether the warning or the error has previously occurred.

According to another aspect of the present invention a printer monitoring apparatus includes a setting unit configured to set a display mode of a peripheral device when a warning or an error occurs and a processing unit configured to continue a process or cancel a process according to the display mode.

Further features and aspects of the present invention will become apparent from the following detailed description of exemplary embodiments with reference to the attached drawings.

Various exemplary embodiments features and aspects of the invention will be described in detail below with reference to the drawings.

A host computer is connected to a printer such as the above described inkjet printer and a monitor . The printer is not limited to an inkjet printer and can be any printer e.g. a laser beam printer.

The host computer includes application software such as a word processor a spread sheet or an Internet browser. The application software issues a group of various rendering commands in which each rendering command indicates an output image i.e. image rendering command text rendering command and graphics rendering command . The various rendering command group is input into a monitor driver via an operating system OS . In a case where printing is to be performed such a rendering command group is also input into a printer driver via the OS . The printer driver and the monitor driver are software that process such a rendering command group and creates print data to be printed by the printer or displayed by the monitor .

In the host computer the above described software is stored in a hard disk HD or a read only memory ROM which is read out by a random access memory RAM and executed by a central processing unit CPU . In the present embodiment a PC is used as the host computer and Microsoft Windows as the OS which are illustrated in . Further an arbitrary application software which includes a printing function is installed in the above described PC that is connected to the monitor and the printer .

Further in the host computer the application software creates output image data using text data classified as text e.g. characters graphics data classified as graphics e.g. figures and image data classified as images e.g. photographic images.

In a case where an image based on the output image data is to be printed the application software issues a print output request to the OS . That is the application software issues to the OS a rendering command group which includes a text rendering command for rendering a text data portion a graphics rendering command for rendering a graphics data portion and an image rendering command for rendering an image data portion.

Upon receiving a print output request from the application software the OS sends the rendering command group to the printer driver . The printer driver responds to the print output request and the rendering command group received from the OS and creates print data that can be printed by the printer . The printer driver then sends the created print data to the printer . The host computer and the printer are connected by an interface such as USB that realizes bi directional communication. A color matching module performs color matching between the monitor and the printer .

Referring to an application creates a document and inquires a user interface driver about the functions of the printer system in order to print the document. The application then notifies the print system including a graphical device interface GDI of print start. Upon receiving the notification of print start from the application the GDI notifies the user interface driver of a print event i.e. a print start by the application . The application then supplies print data of the document to be printed to the GDI and continues the printing process.

The print data is stored in a spool file via the GDI . A print processor reads out the print data from the spool file and the print data is then sent to a language monitor via a graphics driver .

The language monitor sends the print data to a printer while bi directionally communicating with the printer . The language monitor receives information about the status of the printer as necessary and informs the status monitor of the present status of the printer or printing based on information received from the printer or on print data to be sent.

The status monitor displays the statuses received from the language monitor on the monitor . Additionally in a case where printing is interrupted for some reason the status monitor displays options for dealing with the interruption to a user. The status monitor then receives a response from the user about dealing with the interruption and sends the response to the language monitor .

The above described software is stored in the HD or the ROM read out by the RAM and executed by the CPU .

The status monitor displays UIs such as those illustrated in . illustrates a main window that is normally activated surely. The main window includes a display portion that displays a remaining amount of ink in an inkjet printer a display portion that briefly displays a printer status and information about the job being printed. illustrates an error dialog which individually displays an error in a printer or a warning about a print setting in detail. For example in a case where an error such as a paper out occurs during printing the language monitor illustrated in acquires a printer status and notifies the status monitor of the information. The status monitor then displays an error dialog when the error has occurred. The error dialog gives a detailed guidance on content of the error and how to clear the error.

Further when printing is started the print data is transferred to the printer via the language monitor . If the language monitor searches content of the print data or is in a state of issuing a warning based on print setting information and printer setting information when printing is started the language monitor temporarily stops print data transfer to the printer and displays a warning dialog.

As illustrated in an example of a status monitor UI in there is a simple UI in the status monitor which allows a user to select notifying or not notifying a dialog depending on a type of status. When a user selects a display menu on the status monitor illustrated in cover open and envelope printing guide menus are displayed. In the example illustrated in there is a mark on cover open . The mark indicates that the status dialog of cover open will be displayed and notified but a guide dialog of envelop printing guide will not be notified to the user.

A process performed by the status monitor when printing is started will be described below with reference to the flowchart illustrated in .

Generally the status monitor is activated when printing is started. In step the status monitor determines whether there is a file for status monitor display setting. At this point the status monitor does not display a main window or an error dialog. In a case where there is no file for status monitor display setting NO in step the process proceeds to step . In step the status monitor displays a status monitor screen on the monitor normally and displays statuses of various printers.

The file for status monitor display setting can be a file that is structured as illustrated in . The file for status monitor display setting sets information that indicates whether a display setting is valid or invalid and information that describes a level indicating whether a dialog about various statuses is set to a display mode or a non display mode.

In the present embodiment the file for status monitor display setting is previously set by a system administrator using a program for making a display setting to the status monitor . Thus the file for status monitor display setting is separately managed from a display setting that can be set on the UI in the status monitor illustrated in .

A method of creating the file for status monitor display setting illustrated in will be described below. The present embodiment provides a setting list as illustrated in so that a setting can be easily made by a system administrator who is not familiar with various types of errors and warnings that are displayed by the status monitor . The setting list illustrated in provides setting values in a form of bit flags as to types of windows or error dialogs that are to be displayed by the status monitor . The system administrator then makes a setting using a program of an application programming interface API for creating the setting file illustrated in . For example in a case where the system administrator desires to display only ink out error and a warning that printing cannot be continued the setting values that correspond to such error and warning are combined as 0x00100010 . The acquired combined setting value is then set to a parameter of the setting file creation API and executed.

Returning to the flowchart illustrated in in step the status monitor determines whether the display setting that is set in the file for status monitor display setting illustrated in is valid . In a case where the display setting is set as invalid NO in step the process proceeds to step in which the status monitor displays normally. On the other hand if the display setting of the file for status monitor display setting is set as valid YES in step the process proceeds to step . In step the status monitor causes the display setting menus of the various dialog display setting UIs in the status monitor to be unselectable.

The UI illustrated in can be set by a user of the status monitor . On the other hand the file for status monitor display setting illustrated in can be set by a system administrator using a display setting program. The setting file illustrated in thus can be set by a system administrator other than a user of the status monitor . The setting file illustrated in is stored in the RAM and the HD .

Therefore if a system administrator sets the file for status monitor display setting the UI illustrated in which a user can operate becomes non operable so that there is no inconsistency in the operation of the status monitor .

In step the status monitor determines whether the main window illustrated in which is always displayed when the status monitor is activated is set to a non display mode. The status monitor makes the determination based on the level of the status monitor display setting in the setting file illustrated in . If the main window of the status monitor is set to a display mode NO in step the process proceeds to step and the status monitor is activated in a display mode. On the other hand if the main window is set to anon display mode YES in step the process proceeds to step and the status monitor is activated in a non displaying mode.

After performing the above described process the status monitor monitors changes in the printer status.

In step the status monitor determines whether it is necessary to display a message that an error has occurred in the printer or to display a warning based on a driver setting when printing is started. Normally the status monitor displays error information or content of a warning if an error has occurred in the printer or if it is necessary to issue a warning when printing is started. However in the present embodiment the status monitor confirms the content of the file for status monitor display setting in step .

In step the status monitor then determines whether the type of error or warning that is a display target is set to be displayed. In a case where the target error or warning is set to a non display mode NO in step the process proceeds to step and the status monitor proceeds to perform the process without displaying the error or the warning. On the other hand if the target error or warning is set to a display mode YES in step the process proceeds to step and the status monitor displays an error dialog or a warning dialog normally.

Note that the above description describes activation and display processing of various dialogs performed by the status monitor when a display setting of the status monitor is instructed.

A process performed by the status monitor in a case where a target error dialog is set to a non display mode in step in the flowchart of will be described below with reference to a flowchart illustrated in .

In step when the status monitor is activated the status monitor initializes an information value to be used in a determination process in the process flow illustrated in . That is dwWarning or a value to which a type of error or warning to be displayed by the status monitor is input is cleared in the initialization process.

In step the status monitor confirms whether there is a warning dialog or an error in a printer when printing is started. In step the status monitor then determines whether it is necessary to display the warning or the error dialog. In a case where it is necessary to display the warning or the error dialog YES in step the process proceeds to step .

In step the status monitor determines whether the type of warning or error which needs to be displayed is set to a non display mode in the file for status monitor display setting illustrated in . If the warning or error is set to a non display mode YES in step the status monitor does not display the warning or the error dialog and the print job is not completed. The process is stopped without notifying a user why the print job is not completed. Further even if another user wishes to make prints the next job cannot be started when the job stopped by the error is not completed. The processing of a job in a case where the present job transfer is not completed will be described below.

For example a warning as to an error which is to be determined just before printing belongs to a group of warnings having specifications in which the print data can be transferred to the printer and continued to be printed without much problem. Conventionally when there is such a warning print data transfer is stopped and a warning dialog is displayed. However according to the present embodiment the warning dialog is not displayed so that the print data is transferred to the printer and printing is continued. Further conventionally print data transfer is stopped in a case where a guide dialog is to be displayed. On the contrary the guide dialog is not displayed according to the present embodiment so that print data transfer is continued. Further if a warning or an error indicates that it is impossible to continue printing the print data transfer is stopped until the error is cleared in a conventional case. However according to the present embodiment the error dialog is not displayed and the print job is cancelled. Such instructions are described in the job handling table illustrated in .

The job handling table illustrated in is stored in the HD and a user can edit the job handling table. The job handling processes corresponding to the display contents in the job handling table can be modified by a system administrator using a job handling process modification API so that the job handling table can be freely customized.

Returning to the flowchart illustrated in in step the status monitor confirms whether there is a job handling instruction corresponding to the warning or error in the table illustrated in . In step the status monitor determines whether a job handling is instructed. In a case where a job handling is instructed YES in step the status monitor performs a process according to the content of the instructed job handling e.g. continues printing or cancels printing.

In step the status monitor determines whether the instructed job handling process is to cancel printing. If the job handling instruction is to continue printing instead of canceling the printing NO in step the process proceeds to step and the status monitor clears the value dwWarning. On the other hand if the job handling instruction is to cancel printing YES in step the process proceeds to step .

In step the status monitor determines whether there is a history of displaying the same warning or error in a previous last job. The determination is made based on the value dwWarning. If there is a history of displaying the same error or warning in the previous printing YES in step the process proceeds to step . In step the status monitor proceeds to notify the user that printing has failed due to the same printing error or print setting error without canceling the job while ignoring a state that the status monitor is set to a non display mode. On the other hand if there is no history of the same error or warning in the previous printing NO in step the process proceeds to step and the status monitor performs a process according to the job handling instruction. In step the status monitor updates the value dwWarning to the latest error or warning history.

The flowchart illustrated in of the first exemplary embodiment describes setting various errors and warnings in the status monitor to a display mode or a non display mode. In a case where a system administrator who makes such a setting is not familiar with the specifications of the printer and the printer driver it is desirable to provide the administrator with an easier way of making a setting.

Consequently according to a second exemplary embodiment a management table which groups each error and warning into various levels as illustrated in is provided for use by such a system administrator. Moreover according to a second embodiment a table as illustrated in is provided in which errors and warnings are categorized. By using the above described tables a system administrator who is not familiar with the printer and the printer driver specifications can easily make settings as to errors and warnings.

The flowchart illustrated in in the first exemplary embodiment describes an example of a process in which the status monitor displays an error or a warning by ignoring the non display setting of the status monitor in a case where the same error or warning display status is repeated. A third exemplary embodiment describes a process of customizing an allowable number of cases where a same error or a warning display state may repeatedly occur. Such a process performed by the status monitor is illustrated in a flowchart of .

In step the status monitor initializes a data i.e. dwWarning which stores an error or warning information that has caused job canceling. In addition the status monitor initializes a value N which stores a count value acquired by counting the cases where the statuses are the same.

Steps to are similar to steps to described in the flowchart illustrated in and further description about these steps are omitted. In step if it is determined that the same warning or error had occurred in the previous job YES in step the process proceeds to step in which the status monitor increments the count value N.

In step the status monitor determines whether the count value N has become greater than or equal to a predetermined number i.e. greater than or equal to an allowable number of failures . For example if the allowable number of failures is defined as five times and if a job is consecutively canceled five times due to the same cause YES in step the process proceeds to step . In step the status monitor displays the error or the warning by ignoring the non display setting. On the other hand if the count value is less than the allowable number of failures NO in step the process proceeds to step and the status monitor then performs a process according to the job handling process.

In step the status monitor updates the value dwWarning to new warning information and clears the count value N.

The exemplary embodiments of the present invention are described based on an example of a status monitor which displays a warning or an error in a printer. However the present invention can be applied to a status monitor that displays a warning or an error related to a scanner and other peripheral devices.

As described above according to an exemplary embodiment of the present invention a job which cannot be printed due to an abnormal status or a warning that is set to a non display state can be processed according to a job handling table.

Further according to an exemplary embodiment of the present invention it is determined whether a job handling process is repeatedly performed due to a same cause. In a case where the same job handling process is repeatedly performed due to the same cause a trouble shooting guide can be displayed even if a non display setting is made.

Further in a computer that includes a printer monitoring function printer abnormality and print setting warning display can be notified to a user according to the user request. Therefore displaying of unnecessary notices can be decreased and excellent usability can be achieved.

Further according to an exemplary embodiment of the present invention a notification which an operator does not need can be set to a non display mode. As a result a print job is prevented from stopping without any explanation and start of a next job is not hindered or another user is not prevented from making prints.

Therefore according to an exemplary embodiment of the present invention printing is prevented from stopping due to a same error even in a case where a warning or an error is set to a non display state.

Further printing can be appropriately processed even in a case where a warning or an error is set to a non display state.

The present invention can also be achieved by providing a storage medium which stores software program code for implementing functions of the above described exemplary embodiments to a system or an apparatus. The program code stored in the storage medium can be read and executed by a computer central processing unit CPU or micro processing unit MPU of the system or the apparatus.

In this case the software program code itself realizes the functions of the above described exemplary embodiments. The software program code itself and the storage medium which stores the software program code constitute the present invention.

The storage medium can be for example a floppy disk a hard disk a magneto optical disk a compact disc read only memory CD ROM a CD recordable CD R a CD rewritable CD RW a digital versatile disc DVD ROM a DVD RAM a DVD RW a DVD RW a magnetic tape a nonvolatile memory card or a ROM. Further such software program code can be downloaded via a network.

Furthermore the above described exemplary embodiments can be not only realized by executing software program code read by a CPU. An operating system OS or the like working on a computer can also perform a part or the whole of processes according to instructions of the software program code and realize functions of the above described exemplary embodiments.

Furthermore software program code read from a storage medium can be stored in a memory equipped in a function expansion board inserted in a computer or a function expansion unit connected to a computer and a CPU in the function expansion board or the function expansion unit can execute all or a part of the processing based on the instructions of the software program code to realize the functions of the above described exemplary embodiments.

While the present invention has been described with reference to exemplary embodiments it is to be understood that the invention is not limited to the disclosed exemplary embodiments. The scope of the following claims is to be accorded the broadest interpretation so as to encompass all modifications equivalent structures and functions.

This application claims priority from Japanese Patent Application No. 2007 151424 filed Jun. 7 2007 which is hereby incorporated by reference herein in its entirety.

