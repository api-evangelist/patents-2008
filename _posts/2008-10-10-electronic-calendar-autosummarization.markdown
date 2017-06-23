---

title: Electronic calendar auto-summarization
abstract: A relativity controller is a scroll bar/window combination that provides a way to see data in relation to both the context of its wholeness and the salience of its contents. To accomplish this, the linear density or other appearance of the scroll bar (acting as a ruler or scale) varies with the density of the document salience (as indicated by different kinds of annotations or marks). It also provides a way to zoom between perspectives. This is usable on many different data types: including sound, video, graphics, calendars and word processors.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08392848&OS=08392848&RS=08392848
owner: MONKEYmedia, Inc.
number: 08392848
owner_city: Austin
owner_country: US
publication_date: 20081010
---
This is a continuation of prior application Ser. No. 11 978 945 filed Oct. 30 2007 which is a continuation of prior application Ser. No. 09 947 196 filed Sep. 4 2001 which is a continuation of prior application Ser. No. 09 451 594 filed Nov. 30 1999 now U.S. Pat. No. 6 335 730 which is a continuation of prior application Ser. No. 08 844 466 filed Apr. 18 1997 now U.S. Pat. No. 6 177 938 which is a continuation of prior application Ser. No. 07 990 339 filed Dec. 14 1992 now U.S. Pat. No. 5 623 588.

This invention relates to a computer system and in particular to computer tools to improve user perspectives and enhance navigation or browsing of information sources stored in or available via the computer.

As computer accessing of large quantities of information increases the ability of users to navigate large information spaces and to maintain visualization or personal perspectives thereof decreases 1 bracketed numbers reference publications identified in Appendix A .

The need for this type of control has been expressed most recently by Furnas 2 Mills 3 Degen 4 and chimera 5 .

Furnas solution to the problem of understanding the limited information available in a window of large information structures is to provide in the window the detailed region to be considered in the context of important preceding or succeeding parts of the large structure. For example to edit lines in the middle of a program the window would also display say declarations at the beginning of the program. No magnification of desired information or shrinkage of undesired information is employed rather the desired program information is normally displayed and many parts of the program are omitted from the display.

Mills et al addressed the issue of giving users access to video data by magnifying time through successive hierarchial extraction of increasingly detailed segments. Each expanded segment view was displayed in a separate window of the display. And each segment view as well as the total video view including the time lines associated therewith were linearly arranged from a temporal standpoint.

Degen et al moved marks on audio tape to a digitized counterpart document scroll bar and let the user change the visual scaling of time within a single window as well as the speed of playback. But again the visual representations whether of the original size or of the zoomed expanded size had a linear temporal structure.

Chimera on the other hand maintained a full display within the window but was unable to provide a zooming feature or expanded segment view of a text listing. Instead Chimera used scroll bars that independent of the original data s representation indicate relative values of list attributes by respectively scaling proportions of list item indicators according to those attributes in the scroll bars.

Furnas shows in a single window multiple fisheye views of document segments. But Furnas doesn t disclose how a user can select which segments to display or the means to magnify certain segments or the means to control the degree of magnification nor does Furnas provided a scroll bar or its equivalent as a convenient interface for the user to manipulate the display.

An object of the invention is a computer system providing improved means to allow users to extract important segments of computer displayed information in the form of video sound graphics or text while maintaining a general view of the information.

Another object of the invention is a computerized system and method to enable users better to navigate or visualize large information spaces.

In accordance with one aspect of the present invention means are provided to enable a user to visibly mark points or segments of displayed information which will enable the user to quickly navigate to the marked displays.

In another aspect of the invention a scroll bar is displayed alongside the information display and the visible mark or marks appears on the scroll bar at locations corresponding to the desired information.

In accordance with a further aspect of the present invention a computerized system provides the user with means to shrink less important or less significant portions of the information displayed with the result of magnifying the portions that the user deems significant. In accordance with this aspect the invention can be viewed as a user friendly relativity controller tool that enables users to specify what is important to them and modify the portion of their perceptual space that that information takes up in a fisheye variant.

In accordance with another aspect of the invention the resultant information can still occupy the same window where originally displayed but with certain segments shrunk and other segments in comparison standing out or becoming more prominent.

In accordance with still other aspects of the invention the relativity controller of the invention is implemented by simply pointing to the screen and actuating a control device. In a preferred embodiment a mouse button is pressed to mark the beginning and end of segments of the information to be marked. A further feature is that multiple segments can be marked in this manner. Thus the relativity controller of the invention not only allows users to mark the scope of one or more salient segments but also will cause the display to simultaneously shrink the non marked portions and in effect zoom into the multiple marked segments in a single step. The result is a non linear display of the available information. As a further feature simultaneously with selective zooming of the information the display of the scroll bar is correspondingly modified to show in the context of the total information the marked and non marked portions of the displayed information.

The major benefits is to allow users to quickly navigate through a large information space and to control the salience of the displayed information in the context of the full display while conserving display area sometime called desktop real estate. Moreover maintaining a single window for the data and giving users the ability to visually navigate across the whole data via the scroll bar together with the ability to select the salient segments as well as the level of zoom all in a single step greatly enhances the ability of the user to cope intelligently and rapidly with large information structures containing large numbers of objects.

The above and further objects details and advantages of the present invention will become apparent from the following detailed description of preferred embodiments thereof when read in conjunction with the accompanying drawings.

 Object means any representation of information or of a data structure that can be displayed on the monitor screen and includes one or more text characters one or more sound representations such as a digital sample a video representation such as a video frame and in general any graphic s element.

 Control device means devices manipulated by users to move cursors around a screen and include a mouse and keyboard.

 Pointing to an object on screen means actuating the control device to move the cursor so that it is over or adjacent the object. When the cursor is a pointer such an arrow it means moving the arrow tip close to the object.

 Clicking on an object means to press and quickly release a switch on the control device such as a button on a mouse when the cursor is pointing to the object.

 Dragging means to click on the object and while holding the switch activated to manipulate the control device to move the object to a new screen location and then to release the switch to fix the new screen location of the object.

 Double clicking an object on screen is by pointing to the object and clicking twice rapidly often used for special control purposes.

 Shrinking the display of objects means reducing the time or space normally allocated to display the objects and includes shrinking them to the point where they essentially disappear from the display.

A scroll bar is a common control device displayed alongside a window having typically at opposite ends small arrowed scroll boxes or buttons that when clicked on by the user causes the window contents to scroll.

A thumb is a button or box on the scroll bar between its ends which moves and whose location on the scroll bar corresponds to the location in the whole information of the current view.

The first example concerns a sound representation. As illustrated in on top a user can sample audio into a computer as described in the Macintosh user s manual or alternatively record audio onto tape and then sample into the computer . The computer processes the sound data into a visual representation based for example on cochlear models principal component analysis or Fast Fourier Transforms as shown in . The result is displayed on the monitor screen and can also be heard by the user. The typical monitor screen contains a scroll bar for scrolling through the sound representation using a left arrow button to scroll to the left and a right arrow button to scroll to the right. A thumb representation or button which is displayed on the scroll bar shows by its location the portion of the sound representation displayed in the context of the whole sound. In other words if the thumb is at the center of the scroll bar then the sound displayed is at the middle of the recording.

In a usual GUI display a horizontal title bar is located on top and a vertical menu or tool bar is displayed at the left side. Clicking on any of the icons displayed in the tool bar will invoke appropriate software routines to carry out the function indicated by the icon. In this particular example the user desires to annotate the sound representation and the icons can represent an EDIT function or a DRAW function including certain graphic symbols to be pasted into the sound representation.

In accordance with an aspect of the present invention the computer has been trained or customized to recognize meaningful objects and mark them. In this particular case a meaningful object can be any sound representation above a certain amplitude i.e. loud sounds but the computer can choose instead certain frequencies or ranges or certain sound sequences. Marking means with respect to the data structure representing the object to add a tag bit or other data representing a marked time or space position or point. If it is desired to mark a segment meaning a temporal sequence of objects then one tag data can represent the beginning of the marked segment and another data bit can represent the end of the marked segment.

In accordance with another aspect of the present invention the mark is displayed on the display. In a diamond mark is shown to indicate the temporal position of the large amplitude sound . When marks are displayed at the salient points the user can quickly fast forward through the unmarked areas and then stop at or slowly play the marked points or segments by observing the mark or by programming the computer to automatically stop at marked points.

In accordance with another aspect of the invention the scroll bar temporal representation is modified to display the marked points or segments. In the embodiment illustrated in a density representation on the scroll bar is modified with high density regions representing unmarked segments and low density regions representing marked segments. Thus while only a portion of the whole stored sound representation may be displayed in the window shown the scroll bar in the window shown will show the positions of the marked segments or salient points relative to the whole set of objects stored. Thus the user can quickly navigate to the salient points by the conventional fast forward or rewind buttons to reach and observe the annotated regions. illustrates the customized annotation added by the user to the sound representation. These annotations are also useful for indexing hyper navigation and multi sound catalogs. It is understood that marking on the scroll bar can be used separately or together with marking on the document display.

It will also be observed that the scope or range of the marked objects is visible on the scroll bar by the width of low density segments .

In accordance with a further feature of the invention means can be provided to execute a relativity controller function. This can be implemented automatically whenever a marking of salient points is made or it can be implemented by for example pointing to the scroll bar clicking and then dragging the mouse perpendicular to the scroll bar or it can be implemented as explained later by clicking on a special button added to the scroll bar and then dragging the mouse. In the flow charts described later an option key is also used when clicking on the scroll bar. When the relativity controller function is activated the computer modifies the linear temporal representation of the sound into a non linear representation with the non marked segments shrunken in time and the marked segments expanded in time into the resultant empty regions and thus magnified. This is also illustrated in which displays a large portion containing marked segments indicated by the arrows and unmarked segments . If the user then plays through that portion of recorded sound it will play at normal speed through the marked segments but will fast forward at say twice the normal speed through the unmarked segments . In the resultant display the marked segments having been expanded in time show actual digital samples whereas the unmarked segments condense the samples into black bars.

Note further in how the user s marked segments of video get longer and the scroller above and below mark gets lighter as the spacing between marks condenses and darkens when the user scales perspective by moving the mouse upwards toward the top of the mouse pad. Also note how the scroll bar appearance changes to reflect the size of the marks in relation to the length of the whole video.

Marking of the video can occur in the same manner as the audio such as pressing a mouse button when the cursor is on the video to mark the beginning of a segment and releasing the button to mark the end of the segment. The resultant marks can be displayed on the video or in the scroll bar or on both.

In this aspect of the invention not only is the user allowed to select and display the scope of salient segments but as a further feature allows the user to vary the degree of magnification of the salient segments. It will also be understood that besides size other scroll bar changes can be used to represent the salient segments and or different levels of magnification. For example different colors can be used to represent on the scroll bar the salient and non salient segments selected at different times or by different users and if desired the intensity of the color used to illustrate level of magnifications.

The relativity controller application program will not interfere with the normal functions available in programs such as Apple QuickTime while providing the additional functions described above. A listing of available functions for a preferred embodiment which is not meant to be limiting appears below to be used with for example an EDIT menu as depicted in .

The edit menu allows the user to perform the normal functions on displayed information as well as the ability to remove any marks made by the user on the screen display or the scroll bar. what appears below is a description of functions available to the user to carry out the invention. One way of implementing these functions in software are shown in the program flow charts illustrated in . The functions included are for the video of but obviously can be modified and applied to audio or text. Also in the description of these button functions the relativity controller has also been referred as the scale perspective button.

As is conventional in the Macintosh the left button on the scroll bar represents the play button which then converts to pause during play. The right button can thus be used by clicking as a play segment or mark button.

Also listed below is a summary of a few data types with examples of how the invention can be applied 

Implementation of the various forms of the invention will be evident to those skilled in the art. Reference is made to Inside Macintosh published by Addsion Wesley which provides the code for developers for various kinds of interface constructs such as scroll bars control bars slide controls and boxes used therein as well as how to display them in different colors or appearances and how to invoke program routines when a user clicks on a box or icon and how to change the appearance of an icon when a routine is executed. See also U.S. Pat. No. 4 931 783 which describes operation of a system with the Apple Graphical User Interface whose contents are herein incorporated by reference.

To further assist those skilled in the art are flow charts of one form of program suitable to implement a user selecting and displaying in accordance with the invention desired salient of a video presentation.

The person skilled in the art will have no trouble in understanding and implementing the flow charts illustrated. Virtually all of the statements printed in the flow chart boxes are understandable and no need exists to repeat the text herein. However certain statements require some explanation. The statements in the blocks indicated by double lines such as block in represent calls to subroutines as labeled that are detailed in another of the figures. Thus the Track Thumb routine flow chart is shown in . In the labels button refers to the mouse button a pressed button as in the Macintosh changes its 3 d appearance to appear pressed an unpressed button is the reverse. Play segment refers to the right button in . The examples given are with a colored scroll bar to represent the marked segments. Zoom designates magnification level. Stamp cursor means that when the screen cursor is moved within the movie displays the cursor shape changes to resemble a rubber hand stamp indicating to the user that by clicking he or she can mark stamp the document to indicate a salient point. Play speed refers to play speed of the video. Update scroller means to redo the scroll bar to show user selections. Conducting tests are indicated in the boxes by question marks Y or N indicates the test was or was not successful.

As a further alternative the user can press an option key and click on the scroll bar which will jump the thumb to the pointer position and simultaneously allow the user to scroll by moving the mouse horizontally and to change scale or magnification by moving the mouse perpendicularly vertically to the scroller. These changes will be visible on the screen display as well as on the scroll bar.

Since the program of the invention runs as an application clicking on the document display can readily be used to add to the document data structure in memory the time or spatial position of the salient marked display portion when where the pointer rested.

Marking data structures will be evident to those skilled in the art. For text documents adding a mark is generally similar to adding a formatting or printing code to the stored text. Marking video is similar to text marking except that remembering character position is replaced by remembering time position and storing it in the user data portion of the movie.

As further marking alternatives for video the mouse button for marking can be held depressed while the video plays and released to define a marking point or segment. For text the salient text can be highlighted and a menu dropped to select a marking function.

Although there have been described what are at present considered to be the preferred embodiments of the invention it will be understood that the invention may be embodied in other specific forms without departing from the essential characteristics thereof. The present embodiments are therefore to be considered in all respects as illustrative and not restrictive. This scope of the invention is indicated by the appended claims rather than by the foregoing description.

