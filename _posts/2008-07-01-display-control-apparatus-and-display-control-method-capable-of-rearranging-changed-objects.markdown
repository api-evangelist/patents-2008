---

title: Display control apparatus and display control method capable of rearranging changed objects
abstract: A display control apparatus controls display on a display screen and includes an area designation unit configured to designate an area on the display screen, and an extraction unit configured to extract images of objects displayed in the area designated by the area designation unit and to calculate circumscribed rectangular areas circumscribing the respective objects. In addition, a changing unit is configured to, when a first shape of the area designated by the area designation unit changes to a different second shape and at least one of the circumscribed rectangular areas initially falling within the first shaped area is determined not to fall within the second shaped area even if an arrangement change of the respective objects is executed, change the size of the images of the respective objects or spacing between adjacent circumscribed rectangular areas so as to make all of the circumscribed rectangular areas fall within the second shaped area, and execute the arrangement change of the respective changed objects. A display unit displays the images of the respective changed objects after the arrangement change executed by the changing unit.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08780117&OS=08780117&RS=08780117
owner: Canon Kabushiki Kaisha
number: 08780117
owner_city: Tokyo
owner_country: JP
publication_date: 20080701
---
The present invention relates to a display control apparatus and display control method for controlling display on the display screen.

A technique of arranging a character expressed by font data in an arbitrary area on the display screen has been conventionally known and is generally used in a document creation application and the like.

These days an automatic edit function called variable printing has also been proposed. The automatic edit function can arrange a designated character string in a predetermined area in accordance with the size and shape of the area. More specifically the automatic edit function automatically calculates the arrangement and size of characters the spacing between the characters of the character string the line spacing and the like based on the size and shape of the area.

The automatic edit function is also applied to the document creation application. More specifically the document creation application has a function of creating an area for arranging a character string. Even when the shape of the area changes the arrangement of a character string can be automatically adjusted in accordance with the changed shape.

The automatic edit function generally targets a character string expressed by font data and cannot be used for handwritten characters figures and the like having no font data.

In general an automatic edit function implemented for handwritten characters figures and the like is limited. For example Japanese Patent Laid Open Nos. 6 231308 and 7 182449 disclose only a function of changing the position and size of a handwritten character.

To use the automatic edit function the user needs to recognize a handwritten character or the like using a character recognition means or the like and convert the recognized character into font data.

However if no handwritten character can be accurately recognized when trying to use the automatic edit function by recognizing a handwritten character figure or the like no character can be accurately displayed on the display screen. In addition no automatic edit function can be used at all for an object which cannot be recognized as font data such as a handwritten figure or the like other than a character.

A display control apparatus according to the present invention comprises the following arrangement. That is a display control apparatus which controls display on a display screen comprising 

an extraction unit configured to extract images of objects displayed in the area designated by the area designation unit and calculating circumscribed rectangular areas circumscribing the respective objects 

a calculation unit configured to when a shape of the area designated by the area designation unit changes and the circumscribed rectangular areas calculated by the extraction unit are determined not to fall within the shape changed area determine an arrangement of the circumscribed rectangular areas so as to make the circumscribed rectangular areas fall within the shape changed area and calculate positions of the circumscribed rectangular areas and

a display unit configured to display the images of the objects at the positions calculated by the calculation unit.

A display control method according to the present invention comprises the following steps. That is a display control method in a display control apparatus which controls display on a display screen comprising 

an extraction step of extracting images of objects displayed in the area designated in the area designation step and calculating circumscribed rectangular areas circumscribing the respective objects 

a calculation step of when a shape of the area designated in the area designation step changes and the circumscribed rectangular areas calculated in the extraction step are determined not to fall within the shape changed area determining an arrangement of the circumscribed rectangular areas so as to make the circumscribed rectangular areas fall within the shape changed area and calculating positions of the circumscribed rectangular areas and

a display step of displaying the images of the objects at the positions calculated in the calculation step.

The present invention can automatically edit a handwritten object displayed in a predetermined area on the display screen in synchronism with the size and shape of the area.

Further features of the present invention will become apparent from the following description of exemplary embodiments with reference to the attached drawings .

Preferred embodiments of the present invention will now be described in detail in accordance with the accompanying drawings.

In the following description a stroke data arrangement area is the area of a designated object to be edited among handwritten objects displayed on the display screen displayed by stroke input. A temporary data table is a table in which the coordinates of a designated stroke data arrangement area are registered. An input object list is a list in which information character image information and character string structure information on an object contained in the stroke data arrangement area is registered.

A position rule table is a table which defines a rule line spacing character spacing and the like about the position of an object when the arrangement of an object in the stroke data arrangement area changes upon changing the shape of the stroke data arrangement area. A change rule table is a table which defines a rule priority and the contents of a change when the size of an object in the stroke data arrangement area or the spacing between objects changes upon changing the shape of the stroke data arrangement area.

The display control apparatuses to are connected to the network via network I Fs to be described later with reference to . The display control apparatuses to are respectively connected to display devices to via display device I Fs .

The display control apparatuses to have the same arrangement and thus the display control apparatus will be described in detail below.

The RAM Random Access Memory is used as a temporary storage for various pieces of information e.g. an input object list and temporary data table to be described later transmitted from building elements.

The input device I F is connected to input devices not shown such as a mouse and keyboard and accepts instructions input via these input devices.

The display device I F is used to connect the display device having an image display function made up of a cathode ray tube CRT liquid crystal panel and the like and a digitizer function of detecting position information indicated with a pointing device such as a digitizer pen.

An image to be displayed on the display device is transmitted to the display device via the display device I F . Position information detected by the digitizer function of the display device is received via the display device I F .

The external storage stores a control program for implementing a display control method according to the first embodiment of the present invention and tables e.g. a change rule table and position rule table to be described later used to execute the control program . In other words the external storage functions as a change rule holding means and position rule holding means. In addition the external storage stores drivers not shown and the like for operating various devices input device display device and the like .

As a storage medium for storing these pieces of information a ROM floppy disk CD ROM DVD ROM memory card magneto optical disk and the like are available.

The network I F is connected to the network and can communicate with the remaining display control apparatuses to in the network system .

The display control apparatus having these building elements to operates in response to a predetermined instruction accepted by the input device I F or a predetermined instruction input from the network I F via the network . When a predetermined instruction is input via the input device I F or network I F an interrupt signal is transmitted to the CPU and the CPU reads out the control program stored in the external storage . The CPU executes the control program to implement the display control method according to the first embodiment.

In the above description the external storage stores the control program and the tables the change rule table and position rule table for implementing the display control method according to the first embodiment but the present invention is not limited to this. For example the display control method may also be executed by supplying a storage medium storing the control program and the like to the network system or display control apparatus and reading out the control program and the like from the storage medium by the computer of the display control apparatus .

The input unit accepts via the display device I F stroke input information specifically position information input by designating a position on the display screen of the display device by the operator with a pointing device such as a digitizer pen. The input unit accepts via the input device I F information such as a stroke data arrangement area change instruction input by the operator with an input device.

The display unit generates an image based on the result of edit processing based on the input stroke input information and stroke data arrangement area change instruction and displays the image on the display device via the display device I F .

The input data analysis unit extracts the image of a handwritten character object generated based on the stroke input information accepted by the input unit and creates character image information. The input data analysis unit recognizes characters contained in a series of created character image information as a character string and creates character string structure information. The created character image information and character string structure information are registered as the input object list in the RAM .

The arrangement position calculation unit determines the arrangement of a calculated circumscribed rectangular area so that the calculated circumscribed rectangular area falls within a changed stroke data arrangement area designated by a stroke data arrangement area change instruction accepted by the input unit . The arrangement position calculation unit calculates the position of the circumscribed rectangular area in the determined arrangement. The position of the circumscribed rectangular area is calculated using the input object list and position rule table .

When a changed stroke data arrangement area is small and it is determined that all circumscribed rectangular areas containing handwritten character images in a stroke data arrangement area before change cannot be arranged the arrangement position calculation unit notifies the input data change unit that an overflow has occurred.

Upon receiving the overflow notification from the arrangement position calculation unit the input data change unit changes values in the input object list based on the change rule table .

The arrangement of a display screen capable of inputting a stroke with a digitizer pen and automatically editing a handwritten character obtained by the stroke input by designating a stroke data arrangement area will be explained with reference to . In addition the procedures of an edit operation by the operator to a display screen will be simply described.

In a display area displays handwritten characters obtained by stroke input and operation icons for changing the operation mode. The operation icons include a pencil icon rectangle icon and shape change icon .

When the operator selects the pencil icon the display area can accept a stroke input from him. When the operator selects the rectangle icon the display area can accept an instruction to designate an arbitrary stroke data arrangement area the display area functions as an area designation means . When the operator selects the shape change icon the display area can accept an instruction to change a designated stroke data arrangement area.

The procedures of an edit operation by the operator to the display screen when the handwritten characters obtained by stroke input are arranged in a changed stroke data arrangement area designated by a change instruction will be described with reference to .

First the operator selects the pencil icon . Then the display area changes to a state in which a stroke input can be accepted . The operator inputs a stroke by designating a position in the display area with a pointing device such as a digitizer pen. In the example of the operator inputs strokes to array handwritten characters ITALIAN RESTAURANT in line in a predetermined direction.

Upon completion of the stroke input the operator selects the rectangle icon . Then the display area changes to a state in which an instruction can be accepted to designate a stroke data arrangement area. The operator creates a stroke data arrangement area to contain handwritten characters the handwritten characters in this case whose arrangement is to be changed. As a result a stroke data arrangement area containing the handwritten characters is displayed .

Upon completion of designating the stroke data arrangement area the operator selects the shape change icon . Then the display area changes to a state in which the shape of the designated stroke data arrangement area can be changed. An arrow indicating the shape change direction appears . The operator designates a shape changed stroke data arrangement area by operating the arrow indicating the shape change direction and changing the shape of the stroke data arrangement area to a desired one. As a result the handwritten characters arranged can be obtained in accordance with the shape changed stroke data arrangement area the handwritten characters in .

In step S the handwritten characters contained in the stroke data arrangement area acquired in step S are analyzed to perform character image information creation processing and character string structure processing. Character image information obtained by the character image information creation processing and character string structure information obtained by the character string structure processing are registered in the input object list see . Details of these processes will be described with reference to .

In step S the arrangement of circumscribed rectangular areas is determined by referring to the character string structure information so that all the circumscribed rectangular areas containing the images of the handwritten characters acquired in step S fall within the acquired stroke data arrangement area . The positions of the circumscribed rectangular areas are calculated based on the position rule table to be described in detail with reference to . Details of determination of the arrangement and calculation of the position in step S to be referred to as arrangement position calculation processing hereinafter will be described later with reference to .

In step S it is determined whether overflow has occurred as a result of arrangement position calculation processing for the circumscribed rectangular areas in step S. If it is determined in step S that overflow has occurred the process advances to step S. If it is determined that no overflow has occurred the process advances to step S.

In step S it is determined based on the change rule table to be described in detail with reference to whether values in the position rule table or change rule table are changeable. If it is determined in step S that these values are changeable the process proceeds to step S. If it is determined that these values are not changeable the process ends owing to the overflow.

In step S values in the position rule table or input object list are changed and the process returns to step S. Details of the change processing will be described with reference to .

In step S character image information and character string structure information in the input object list are acquired to display the images of the handwritten characters represented by the character image information on the display screen based on the acquired character string structure information.

In step S a handwritten character obtained by stroke input is extracted to calculate a circumscribed rectangular area representing the character size width and height . The circumscribed rectangular area calculation processing is performed using an existing character extraction technique. The width height and position of the calculated circumscribed rectangular area are registered as character string structure information in the input object list .

In step S the image of the handwritten character extracted in step S is registered as character image information in the input object list . The character image information may also be registered as raster graphics or vector graphics by calculating the outline of a character.

In step S the handwritten character extracted in step S is recognized. The recognition result in step S is registered as character string structure information in the input object list . In the example of objects displayed in the circumscribed rectangular areas are recognized as R and E respectively.

In the above description each character is extracted that is a character is processed as an object. However the present invention is not limited to this and a word may also be processed as an object. In this case a character string is recognized using an existing recognition technique to extract a word from the character string. For a European language such as English a word is extracted by breaking a character string at a space blank character . For a language using no space break like Japanese a word is extracted using a technique such as morphological analysis. Even when a word is processed as an object a circumscribed rectangular area can be calculated similarly to the case where a character is processed as an object.

By processing a word as an object line feed wordwrap for each word can be executed even in a language in which no line feed is done midway through a word like English.

In step S temporary data is initialized. In the initialization processing the changed stroke data arrangement area for arranging a circumscribed rectangular area containing a handwritten character image is acquired. Information on the stroke data arrangement area is saved in a temporary data table shown in .

The temporary data table holds an arrangement area for registering the coordinates of an acquired stroke data arrangement area and current coordinates for registering the coordinates of the upper left corner of a circumscribed rectangular area contained in the stroke data arrangement area. The temporary data table further holds items a line width line spacing and character spacing for registering the line width line spacing and character spacing of a circumscribed rectangular area contained in the stroke data arrangement area.

In the initialization processing 0 is registered as the line width . Values acquired from the position rule table to be described in detail with reference to are registered as the line spacing and character spacing .

In step S it is determined whether unprocessed character image information exists in the input object list to be described with reference to . If it is determined that unprocessed character image information exists the process advances to step S. If it is determined that no unprocessed character image information exists the process ends.

In step S character string structure information for the unprocessed character image information is acquired from the input object list .

In step S a circumscribed rectangular area containing a handwritten character image represented by the character image information is arranged in the stroke data arrangement area.

In the arrangement processing the current coordinates are acquired from the temporary data table shown in . Then the circumscribed rectangular area is arranged using the current coordinates as the coordinates of the upper left corner of the circumscribed rectangular area containing the handwritten character image represented by the character image information acquired in step S. An example of the arrangement of the circumscribed rectangular area will be explained with reference to . In the current coordinates are .

A case where a circumscribed rectangular area containing a handwritten character image R in is arranged will be described. The circumscribed rectangular area containing the handwritten character image R has a width 30 and height 40 . As a result of arranging the circumscribed rectangular area its coordinates are at the upper left corner and at the lower right corner.

In step S it is determined whether the circumscribed rectangular area falls within the stroke data arrangement area acquired in step S as a result of the processing in step S. If it is determined in step S that the circumscribed rectangular area falls within the stroke data arrangement area the process advances to step S.

In step S the current coordinates in the temporary data table are updated. New current coordinates are calculated by adding to the current coordinates the product of the width of the circumscribed rectangular area calculated in step S and the value of the character spacing in the temporary data table.

An example of updating the current coordinates will be explained with reference to and . Assume that the coordinates of a circumscribed rectangular area are calculated in step S as shown in . In this case the width of the circumscribed rectangular area is 30 the character spacing is 1.0 and thus the current coordinates in are updated to those shown in .

In step S the line width in the temporary data table is updated. In the line width updating processing the line width is acquired from the temporary data table.

It is determined whether the acquired line width is larger than the height of the circumscribed rectangular area. If it is determined that the line width is smaller than the height of the circumscribed rectangular area the line width in the temporary data table is updated to the value of the height of the circumscribed rectangular area.

If it is determined in step S that the circumscribed rectangular area does not fall within the stroke data arrangement area the process advances to step S to perform line feed processing for changing the line feed position. First the line width the line spacing and an x coordinate representing the left end of the arrangement area are acquired from the temporary data table. Then the current coordinates in the temporary data table are updated. The update value of the x coordinate of the current coordinates is the acquired x coordinate representing the left end of the arrangement area in the stroke data arrangement area .

The update value of the y coordinate of the current coordinates is a value calculated by adding the product of the line width and line spacing to the y coordinate of the current coordinates before update. After updating the current coordinates the line width value in the temporary data table is reset to 0.

A concrete example of the line feed processing will be explained with reference to . In the case of since the current coordinates are x y the line width is 40 and the line spacing is 1.0 the y coordinate of new current coordinates is the old y coordinate line width line spacing 400 40 1.0 440. The x coordinate of the current coordinates is the same as the x coordinate of the stroke data arrangement area so new current coordinates are x y .

In step S it is determined whether the circumscribed rectangular area falls within the stroke data arrangement area acquired in step S as a result of the processing in step S. If it is determined that the circumscribed rectangular area falls within the stroke data arrangement area the process advances to step S. If it is determined that the circumscribed rectangular area does not fall within the stroke data arrangement area it is notified as a processing result that an overflow has occurred and the process ends.

In step S it is determined whether changeable items are listed in the change rule table shown in . If it is determined in step S that no changeable item is listed the process ends. If it is determined that changeable items are listed the process advances to step S.

In step S an item whose data is to be changed is determined from priority in the change rule table shown in . In a change item having priority 1 is character image so it is determined to change a handwritten character image in this case a smaller priority value represents a higher priority level .

In step S the value of the item determined in step S is changed. The change processing is done based on a change rate in the change rule table shown in . If the change item is character image the value in the input object list is updated.

If the change item is line spacing or character spacing the value in the position rule table is updated. The case in will be exemplified. Since the change item is character image and the change rate is 2 the values of a character width and character height in the input object list are decreased by 2 .

The handwritten character image is reduced in accordance with the decreased character width and character height. The handwritten character image is reduced using an existing image reduction technique. In this manner when the change item is character image a handwritten character image is reduced. When the change item is line spacing or character spacing the spacing between handwritten character images is narrowed.

In step S a current value in the change rule table shown in is decreased by the change rate . If the decreased current value equals a minimum value an item whose value has reached the minimum value is deleted from the change rule table .

In the example of the current value is 100 the change rate is 2 and thus the new current value is 98 .

The priority represents the priority of a change item. As the value is smaller the priority is higher. The change item represents an item whose value is to be changed.

The change rate represents the rate of change. For example when the change rate is 2 the value of a change item is decreased by 2 .

The current value represents a value decreased from an initial value. For example when the current value is 75 this means that the value decreases from the initial value to 75 .

The minimum value represents a minimum value to which the value can be decreased. For example when the minimum value is 50 the value is permitted to be decreased up to half the initial value.

The input character represents a result of recognizing a handwritten character. The character width represents the width of a circumscribed rectangular area containing a handwritten character image. The character height represents the height of a circumscribed rectangular area containing a handwritten character image.

The character position represents coordinates for specifying the circumscribed rectangular area of a handwritten character. The character position is defined by the coordinates of the upper left and lower right corners of a circumscribed rectangular area. For example a handwritten character image I is a circumscribed rectangular area defined by x y and x y .

The character image information is a handwritten character image. The handwritten character image may also be held as raster graphic data or vector graphic data by calculating the outline of a character. The handwritten character image may also undergo compression or the like.

Character string information is represented in the order along the line. In the example of a character string ITALIAN RES . . . is expressed. The result of character recognition is represented as a character string but another representation is also available as long as the order of handwritten character images is expressed.

In other words the processing in the first embodiment can be achieved as long as the order of handwritten character images can be held without performing character recognition. Even when character recognition fails the arrangement of handwritten character images can be changed in accordance with the shape of the stroke data arrangement area. For example even when symbols such as and are handwritten and input the first embodiment can be implemented as long as pieces of character image information representing and and the order of these pieces of character image information are held.

The line spacing represents a spacing in line feed. A value 1.0 represents a state in which adjacent lines do not overlap each other. As the value decreases the line spacing narrows.

The character spacing represents a spacing between characters. A value 1.0 represents a state in which adjacent characters do not overlap each other. As the value decreases the spacing between characters narrows.

In this case the line spacing and character spacing are set but rules such as Japanese word wrapping at the beginning and end of a line may also be applied to characters recognized from handwritten character images.

As is apparent from the above description according to the first embodiment when the operator designates a stroke data arrangement area handwritten character images displayed in the area are extracted and rectangular areas circumscribing the handwritten character images are calculated.

When no circumscribed rectangular area falls within the stroke data arrangement area as a result of changing the stroke data arrangement area the arrangement of the circumscribed rectangular areas can be changed to fall within the stroke data arrangement area.

When an overflow cannot be prevented by only changing the arrangement it can be done by changing the size of a handwritten character image or the spacing between circumscribed rectangular areas.

That is even a handwritten character figure and the like can be automatically edited in synchronism with the stroke data arrangement area.

The present invention may also be applied to a system including a plurality of devices for example a host computer interface device reader and printer or an apparatus for example a copying machine or facsimile apparatus formed by a single device.

The object of the present invention is also achieved by supplying to a system or apparatus a recording medium which records software program codes for implementing the functions of the above described embodiment. In this case these functions are achieved by reading out and executing the program codes recorded on the recording medium by the computer or the CPU or MPU of the system or apparatus. In this case the recording medium which records the program codes constitutes the present invention.

The recording medium for supplying the program codes includes a floppy disk hard disk optical disk magneto optical disk CD ROM CD R magnetic tape nonvolatile memory card and ROM.

The present invention is not limited to a case where the functions of the above described embodiment are implemented when the computer executes the readout program codes. Also the present invention includes a case where an OS Operating System or the like running on the computer performs some or all of actual processes based on the instructions of the program codes and thereby implements the functions of the above described embodiment.

Furthermore the present invention includes a case where the functions of the above described embodiment are implemented after the program codes read out from the recording medium are written in the memory of a function expansion board inserted into the computer or the memory of a function expansion unit connected to the computer. That is the present invention also includes a case where after the program codes are written in the memory the CPU of the function expansion board or function expansion unit performs some or all of actual processes based on the instructions of the program codes and thereby implements the functions of the above described embodiment.

While the present invention has been described with reference to exemplary embodiments it is to be understood that the invention is not limited to the disclosed exemplary embodiments. The scope of the following claims is to be accorded the broadest interpretation so as to encompass all such modifications and equivalent structures and functions.

This application claims the benefit of Japanese Patent Application No. 2007 186328 filed on Jul. 17 2007 which is hereby incorporated by reference herein in its entirety.

