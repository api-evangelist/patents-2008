---

title: Document management apparatus, document management program, and recording medium
abstract: A document management apparatus for managing stored documents together with document properties that are attribute information attached to the documents includes a document property continuous setting unit that continuously changes the document properties of each document of a plurality of documents when changing the document properties of the plurality of the documents. The document management apparatus may also include a candidate value attachment unit, a candidate value cancellation unit, and a document list display unit. The candidate value attachment unit automatically displays a candidate value for a document of the plurality of the documents, the properties of which are input based on a previously input value. The candidate value cancellation unit cancels a function of the candidate value attachment unit in accordance with a setting. The document list display unit is configured to display a list of selected documents subjected to property editing.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07895170&OS=07895170&RS=07895170
owner: Ricoh Company, Ltd.
number: 07895170
owner_city: Tokyo
owner_country: JP
publication_date: 20080214
---
This patent application is based on and claims priority under 35 U.S.C. 119 from Japanese Patent Application No. JP2007 034131 filed on Feb. 14 2007 in the Japan Patent Office and Japanese Patent Application No. JP2007 320431 filed on Dec. 12 2007 in the Japan Patent Office the entire contents of each of which are hereby incorporated herein by reference.

Exemplary aspects of the present invention generally relate to a document management apparatus a document management program product and a computer readable recording medium on which is recorded the document management program and more particularly to a document management apparatus a document management program product and a computer readable recording medium on which is recorded a document management program capable of enhancing document properties alteration efficiency.

Conventionally two general ways of modifying document properties are known. One such method selects a single document and then changes the document properties of a document. The other method selects all documents the document properties of which are subjected to change in advance and makes the same change with respect to all documents at once.

However in either method it is difficult to continuously and seamlessly input properties relative to an individual document causing inconvenience to a user. Such inconvenience includes for example that an appropriate change is not made or an unintended change is made. As a result the user is required to bear the burdens and risks of human error.

Furthermore even if it is made possible to continuously and seamlessly input the properties for the individual document it is troublesome to input the same information or values repeatedly upon changing document properties for example.

In addition even if it is made possible to achieve continuous and seamless modification of document properties when editing a large volume of document properties there is an increasing risk of an occurrence of human error as the number of documents increases.

In related art disclosed in Japanese Laid Open Patent Application No. 2004 240488 an optical character reader hereinafter referred to as an OCR automatically converts contents of a document to character data and extract data presumably associated with a date or time from the character data. Subsequently the extracted data is added as a document property to the document.

In the related art the OCR is employed to automatically add information as a document property to the document assuming that there is information already existing in the document. Moreover the document properties to be added are limited to a date and a time.

In view of the foregoing exemplary embodiments of the present invention provide a document management apparatus a document management program product and a computer readable recording medium recorded with the document management program.

In one exemplary embodiment a document management apparatus for managing stored documents together with document properties that are attribute information attached to the documents includes a document property continuous setting unit. The document property continuous setting unit is configured to continuously change the document properties of each document of a plurality of documents when changing the document properties of the plurality of the documents.

The document management apparatus includes a candidate value attachment unit and a candidate value cancellation unit. The candidate value attachment unit is configured to automatically display a candidate value for a document of the plurality of the documents the properties of which are being input based on a previously input value. The candidate value cancellation unit is configured to cancel a function of the candidate value attachment unit in accordance with a setting.

Another exemplary embodiment provides the document management apparatus including a document list display unit. The document list display unit is configured to display a list of selected documents subjected to property editing.

Yet another exemplary embodiment provides a method for managing stored documents together with document properties that are attribute information attached to the documents. The method includes continuously changing the document properties of each document of a plurality of documents when changing the document properties of the plurality of the documents.

Yet another and further exemplary embodiment provides the method including displaying a list of selected documents subjected to property editing.

Still yet another and further exemplary embodiment provides a computer readable recording medium storing a program for causing the computer to execute a method of managing stored documents together with document properties that are attribute information attached thereto. The method includes continuously changing the document properties of each document of a plurality of documents when changing the document properties of the plurality of the documents.

Still yet another and further exemplary embodiment provides a document management apparatus for managing stored documents together with document properties that are attribute information attached to the documents. The document management apparatus includes means for changing the document properties of each document of a plurality of documents when changing the document properties of the plurality of the documents.

Additional features and advantages of the present invention will be more fully apparent from the following detailed description of exemplary embodiments the accompanying drawings and the associated claims.

It will be understood that if an element or layer is referred to as being on against connected to or coupled to another element or layer then it can be directly on against connected or coupled to the other element or layer or intervening elements or layers may be present.

In contrast if an element is referred to as being directly on directly connected to or directly coupled to another element or layer then there are no intervening elements or layers present. Like numbers refer to like elements throughout figures. As used herein the term and or includes any and all combinations of one or more of the associated listed items.

Spatially relative terms such as beneath below lower above upper and the like may be used herein for ease of description to describe an element or an element s feature or relationship to another element s or feature s as illustrated in the figures.

It will be understood that the spatially relative terms are intended to encompass different orientations of the device in use or operation in addition to the orientation depicted in the figures.

For example if the device in the figures is turned over elements described as below or beneath other elements or features would then be oriented above the other elements or features. Thus the term such as below can encompass both an orientation of above and below.

The device may be otherwise oriented at various angles i.e. rotated 90 degrees or at other orientations and the spatially relative descriptors used herein are interpreted accordingly.

Although the terms first second etc. may be used herein to describe various elements components regions layers and or sections it should be understood that these elements components regions layers and or sections should not be limited by these terms.

These terms are used only to distinguish one element component region layer or section from another element component region layer or section. Thus a first element component region layer or section discussed below could be termed a second element component region layer or section without departing from the teachings of the present invention.

The terminology used herein is for the purpose of describing particular embodiments only and is not intended to be limiting of the present invention. As used herein the singular forms a an and the are intended to include the plural forms as well unless the context clearly indicates otherwise.

It will be further understood that the terms includes and or including when used in this specification specify the presence of stated features integers steps operations elements and or components but do not preclude the presence or addition of one or more other features integers steps operations elements components and or groups thereof.

In describing exemplary embodiments illustrated in the drawings specific terminology is employed for the sake of clarity. However the disclosure of this patent specification is not intended to be limited to the specific terminology so selected and it is to be understood that each specific element includes all technical equivalents that operate in a similar manner.

In the later described comparative example exemplary embodiment and alternative example for the sake of simplicity of drawings and descriptions the same reference numerals will be given to constituent elements such as parts and materials having the same functions and the descriptions thereof will be omitted unless otherwise stated.

Typically but not necessarily paper is the medium from which is made a sheet on which an image is to be formed. Other printable media are available in sheets and their use here is included. For simplicity this Detailed Description section refers to paper sheets thereof paper feeder etc. It should be understood however that the sheets etc. are not limited only to paper.

Exemplary embodiments of the present invention are now described below with reference to the accompanying drawings.

Referring now to the drawings wherein like reference numerals designate identical or corresponding parts throughout the several views particularly to a document management apparatus according to an exemplary embodiment of the present invention is described.

In the document management apparatus includes at least a user interface a control unit a document property control unit a document list control unit a data management access unit a data management unit a document property continuous setting unit a candidate value attachment unit a candidate value cancellation unit a document property display enhancement unit a document property color change unit a document property font change unit and so forth.

The user interface unit enables a display device for example a display to display various kinds of screens and enables an input device for example a keyboard and a mouse to perform various operations.

Based on setting information set by the document property control unit the document list control unit and the document property continuous setting unit the control unit enables the data management access unit to control a sequence of operations for storing information in the data management unit .

The document property control unit causes the candidate value attachment unit the candidate value cancellation unit the document property display enhancement unit the document property color change unit and the document property font change unit to control a sequence of operations associated with inputting the document properties.

The document list control unit causes a document list display unit a document display enhancement unit a document list color change unit a document list font change unit and a document list icon change unit to control a sequence of operations associated with displaying a document list.

The data management unit stores information with respect to an electronic document and properties attached to the electronic document.

The document property continuous setting unit continuously and seamlessly switches screens for editing the document properties.

The candidate value attachment unit displays candidate values for each item of the document properties currently to be subjected to input based on the values for each item of the document properties input in the past.

The document property control unit determines the items of the document properties to be most likely input by a user. The document property display enhancement unit enhances the visibility of document property items using the document property color change unit and the document property font change unit .

The document property color change unit changes a color of a specific document property so that the visibility is enhanced enabling the user to recognize the document property more easily.

The document property font change unit changes a font of a specific document property so that the visibility is enhanced enabling the user to recognize the document property more easily.

The document list display unit displays a list of documents subjected to a property editing regardless of an existing window or a new window.

The document display enhancement unit enhances the visibility of the document of which property the user has input on the document list screen.

The document list color change unit changes a color of a specific document on the document list screen so that the visibility is enhanced enabling the user to recognize the document property more easily.

The document list font change unit changes a font of a specific document on the document list screen so that the visibility is enhanced enabling the user to recognize the document property more easily.

The document list icon change unit employs a certain icon relative to a specific document on the document list screen so that the visibility is enhanced enabling the user to recognize the document property more easily.

Referring now to there is provided a flowchart showing an exemplary procedure of the candidate value attachment processing performed by the document management apparatus .

In the exemplary process shown in first in step S the control unit verifies whether or not the candidate value attachment unit is valid when an edit screen for the document properties is displayed. The verification is performed because the candidate value attachment cancellation unit may cancel the validity of the candidate value attachment unit and thus the validity of the candidate value attachment unit may vary between VALID and INVALID .

When the result is YES in step S that is the result indicates VALID whether the property currently being edited is of a subsequent third document or beyond is verified in step S.

When the document is the third document or beyond that is the result is YES in step S subsequently in step S whether or not there is regularity for example the exact same value for prefix postfix is confirmed for each item based on the value input by the user in the past.

When it is determined that there is regularity that is the result is YES in step S the candidate value is displayed on the screen based on the regularity in step S.

Referring now to there is provided a flowchart showing an exemplary procedure of changing the font of the document properties in document management apparatus .

In the exemplary process shown in when the edit screen for the document properties is displayed the control unit verifies whether the document the property of which is currently edited is a second document or beyond in step S.

When the document is the second document or beyond that is the result is YES in step S subsequently an item of the document input in the past is displayed in a manner easily recognizable by the user in step S. In other words the item is displayed in a different font.

Referring now to there is provided a diagram illustrating a display example of the edit screen for the document properties using the document property font change unit .

In this example the document property font change unit distinguishes the value for the document title Meeting Material 2 from other values by displaying the document title in italics for example.

Referring now to there is provided a diagram illustrating a display example of the edit screen for the document properties using the document list icon change unit .

In this example the document list icon change unit provides the document Meeting Material.txt with an icon indicating that the change has been made. In the exemplary embodiment a circled word COMPLETED for example is displayed to indicate that the change has been completed.

According to the exemplary embodiments of the present invention the efficiency of changing the document properties can be enhanced and the operation processes can be reduced. Accordingly the risk of human error can be mitigated.

Referring now to there is provided a diagram illustrating a display example of the document list screen.

The document list screen shown in includes at least a screen PN and a screen PN. The screen PN is a screen to display a tree structure of folders. The screen PN is a screen to display using an icon at least one document stored in the folder selected in the screen PN.

In a folder is selected. Two documents with the document titles aaa and aab stored in the folder are displayed in icons PP and PP respectively.

As shown in the document aaa is selected in this case. Therefore a property dialogue screen as shown in for example is displayed and the property information of the document aaa is displayed.

The property dialogue screen includes at least a BACK button BB a NEXT button BB an OK button BB a CANCEL button BB and so forth that can be operated by the user. The buttons BB and BB are provided at the upper right and the buttons BB and BB are provided at the bottom.

When the user operates the button BB that is the NEXT button the document files stored in the selected folder are sequentially selected according to the order of display displayed on the document list screen. The property information of the selected document is sequentially displayed on the property dialogue screen.

Accordingly when the user wishes to change the document the property information of which the user wishes to display the user need not close the property dialogue screen to select the next document and display the property dialogue screen again. As a result the operability of the user is enhanced.

Furthermore as shown in when the user presses the button BB NEXT button and the displayed content of the property dialogue screen has been changed a dialogue screen requesting the user to confirm whether or not the changed content is applicable is displayed.

Referring now to there is provided a flowchart showing an exemplary procedure of the operation of the property dialogue screen.

In when the user operates the operation item displayed on the property dialogue screen that is the result is YES in step S whether the operation item is the OK button BB or the CANCEL button BB or the NEXT button BB or any other operation item is determined in steps S S and S.

When the OK button BB is operated and the result is YES in step S the operation contents are saved in step S and subsequently the screen is closed in step S.

When the CANCEL button BB is operated and the result is YES in step S the procedure advances to step S and the screen is closed.

When the NEXT button BB is operated and the result shows YES in step S the NEXT button processing described later is performed in step S.

In a case where the operation item other than the NEXT button BB is operated and when the result is NO in step S the process corresponding to the operated item is executed in step S.

First whether or not the property value is changed is determined in step S. When the result is YES in step S in step S the document property control unit displays the confirmation dialogue requesting the user to confirm whether or not the change is applicable.

When the user selects a dialogue Apply change in the confirmation dialogue screen that is the result is YES in step S the document property control unit obtains the changed property value and requests the data management access unit to update the property through the control unit in step S.

The control unit requests the document list control unit to obtain an ID of the next document in step S. Based on the obtained ID of the next document the control unit requests the data management access unit to obtain the property information of the subject document in step S.

Accordingly the data management access unit returns the document property information obtained from the data management unit to the control unit in step S.

Subsequently the control unit provides the document property control unit with the obtained document property information and requests the document property control unit to update the display of the dialogue in step S.

Accordingly the document property control unit displays on the property dialogue screen the received information of the document properties in step S. As a result the property information of the next document is displayed on the property dialogue screen.

According to the exemplary embodiments the document the document ID and the document property information are saved in the data management unit and are transmitted to the control unit through the data management access unit .

Alternatively the document the document ID and the document property information can be saved in an external server connected to the document management apparatus through a network or the like. Based on the requirements of the document management apparatus the document the document ID and the document property information can then be retrieved from the server through the network or the like.

According to the exemplary embodiments the document properties can be continuously changed without closing the screen. Thus the number of operation processes can be reduced thereby enhancing operating efficiency.

Furthermore based on the value previously input by the user regularity can be found thereby being able to display the candidate values. Thus operability can be improved and the risk of human error and the like can be mitigated.

Furthermore the document properties most likely to be subjected to input are displayed in a manner easily recognizable by the user. Accordingly the possibility of omission of input by the user can be reduced if not prevented entirely.

Furthermore elements and or features of different exemplary embodiments may be combined with each other and or substituted for each other within the scope of this disclosure and appended claims.

The number of constituent elements locations shapes and so forth of the constituent elements are not limited to any of the structure for performing the methodology illustrated in the drawings.

Still further any one of the above described and other exemplary features of the present invention may be embodied in the form of an apparatus method system computer program and computer program product. For example of the aforementioned methods may be embodied in the form of a system or device including but not limited to any of the structure for performing the methodology illustrated in the drawings.

One or more embodiments of the present invention may be conveniently implemented using a conventional general purpose digital computer programmed according to the teachings of the present specification as will be apparent to those skilled in the computer art.

Appropriate software coding can readily be prepared by skilled programmers based on the teachings of the present disclosure as will be apparent to those skilled in the software art.

One or more embodiments of the present invention may also be implemented by the preparation of application specific integrated circuits or by interconnecting an appropriate network of conventional component circuits as will be readily apparent to those skilled in the art.

Any of the aforementioned methods may be embodied in the form of a system or device including but not limited to any of the structure for performing the methodology illustrated in the drawings.

Furthermore any of the aforementioned methods may be embodied in the form of a program. The program may be stored on a computer readable media and is adapted to perform any one of the aforementioned methods when run on a computer device a device including a processor . The program may include computer executable instructions for carrying one or more of the steps above and or more aspects of the invention.

Thus the storage medium or computer readable storage medium is adapted to store information and is adapted to interact with a data processing facility or computer device to perform the method of any of the above mentioned embodiments.

The storage medium may be a built in medium installed inside a computer device main body or a removable medium arranged so that it can be separated from the computer device main body. Examples of a built in medium include but are not limited to rewriteable non volatile memories such as ROMs and flash memories and hard disks.

Examples of a removable medium include but are not limited to optical storage media such as CD ROMs and DVDs magneto optical storage media such as MOs magnetism storage media such as floppy disks trademark cassette tapes and removable hard disks media with a built in rewriteable non volatile memory such as memory cards and media with a built in ROM such as ROM cassettes.

Example embodiments being thus described it will be obvious that the same may be varied in many ways. Such exemplary variations are not to be regarded as a departure from the spirit and scope of the present invention and all such modifications as would be obvious to one skilled in the art are intended to be included within the scope of the following claims.

