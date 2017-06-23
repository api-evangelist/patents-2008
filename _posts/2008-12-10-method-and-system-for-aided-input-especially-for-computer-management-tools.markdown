---

title: Method and system for aided input especially for computer management tools
abstract: A method of aided input especially for a computer management tool, the management tool being executed in a computer system possessing an operating system furnished with instrumentation services, the method including the following steps: (a) entering raw data from an exterior source, (b) extracting relevant data from the raw data, (c) using the instrumentation services to transcribe the extracted data to corresponding fields of a preexisting input interface belonging to the management tool, within a view to allowing further inputs and overall validation. Application in particular to the semi-automated input of accounting items such as supplier invoices and the like.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08553993&OS=08553993&RS=08553993
owner: Serensia
number: 08553993
owner_city: Paris
owner_country: FR
publication_date: 20081210
---
This application is a National Phase Entry of International Application No. PCT EP2008 067260 filed on Dec. 10 2008 which claims priority to French Application 0708591 filed on Dec. 10 2007 both of which are incorporated by reference herein.

This invention relates to a method for aided input especially by automatic integration of incoming data in data management software.

The methods of the prior art relate for example to the integration of dataflow accounting records in a computerized accounting system by recognizing optical information contained in accounting records on paper format typically invoices . A concrete example of such a known method is shown in . By referring to it when it is desired to automate data integration in an ERP data it is necessary to produce a stream of structured data that can be integrated into the software package. The flow is usually of two possible types whether it comes from an electronic transmission system of the EDI type with a standard well specified file format EDIFACT XML PDF Text tabular file etc. and then processed to the input specifications of the gateway software package or it comes from an ADR system for Automatic Document Recognition and processed to the input specifications of the gateway software package.

Paper Scanner OCR Field extractions Data structure to be integrated Secure login Data management software.

However it is common in this kind of method to deal with reliability defects scanning error or incomplete data incomplete data and or the presence of specific cases. This is the reason why the incoming data require validation or manual corrections by the operator and or additional manual input by the operator in order to obtain a definitive integration into the structured data flow end point of the software in particular for comparison purposes analytical assignment accounting assignment in the case of management for third parties etc. . So that a second validation is required once the flow is sent to the software to complement and or validate the data integration in the software.

Another type of difficulty arises in the case where the end point software e.g. software package provides only incomplete poor opportunities even non existent in terms of gateway allowing introducing data in the system other than by input in input fields aided by the system keyboard. It is the case for example in a pre existing software the code of which is closed e.g. owner software and the integration capabilities of structured data flow are poor even non existent or poorly documented.

Moreover this type of method offers virtually no feedback on the end point software package on corrections to be carried out concerning raw data. Generally the feedback type of the software package is limited to an error code often in real time without allowing any learning to the validation software. Thus corrections brought about in the software are usually not taken into consideration in the preparation of structured data stream.

This invention has the object of overcoming the limitations of the prior art and in particular to overcome the lack of gateway input of a data management software package or even to overcome the low quality of services or lack of opportunities e.g. lack of gateway feedback from such a gateway should it be present. A further object of this invention is to simplify and optimize the complementary manual inputs that are usually necessary in order to gain productivity time in particular by grouping them together into a single point of the process with the correction step OCR module validation. A further object of this invention is to authorize without complicating the whole process an enriched input. Finally an object of this invention is to capitalize on these enrichments to improve the quality of data extraction intended to feed aided input.

To this effect it is proposed to instrument the software package input interfaces to make them play the triple role of automatic or semi automatic integration gateway of screen allowing additional inputs and finally as an information source namely the data already contained in the management tool and or derived from operator actions to enrich the initial extraction and processing treatments performed on the data raw source to improve permanently these treatments . Thus the invention allows using the software input screen as an automatic or semi automatic incoming gateway in the software. A functional enrichment at the package software input screen is therefore obtained. Indeed the software input screen thus becomes the secure login of the software.

More specifically this invention provides a method for aided input in particular to a computer management tool the management tool being implemented in a computer system with an operating system equipped with instrumentation services characterized in that it comprises the following steps 

 c use of the said instrumentation services to transcribe the said data extracted towards corresponding fields of a pre existing input interface belonging to the management tool in view of allowing additional inputs and a validation as a whole.

By the term instrumentation service it is intended a set of characteristics offered by an operating system and its windowing module or an environment of any whatsoever office. These services comprise several characteristics among which 

the opportunity to explore the software structure of the interface windows to determine their composition through programming for example discover that the window contains a menu an ok button several input fields the fact that such fields or such text contains such value etc. 

the opportunity to determine and or be notified of user actions pressing a key click on a button etc. and

the opportunity to determine and or be notified of interface status changes determine the foreground window determine the cursor location determine the function by default when pressing a particular key such as the enter key etc. and

the opportunity to simulate user actions input key mouse click but also moving and changing window size moving the focus point etc.

The joint use of all these operations allows a full instrumentation of an input screen. It is possible to implement these instrumentation services in particular through the operating system function call API Application Programming Interface .

the instrumentation services allow in particular to discover the model and the content of a pre existing input screen and to simulate user actions 

the method comprises before the transcription step a displaying step organized pre input fields of relevant data extracted in view of their pre validation.

the extraction step comprises a paper image scan in digital image or a reading step of a structured file or described according to a predetermined description language.

the extraction step comprises optical character recognition or a document conversion in alphanumerical listed elements and associated coordinates or a lexical and syntactic analysis.

the method further comprises a data qualification validation extracted by using a rules based extraction.

the step b comprises an allocation by using a rules based pre input of the possible values for the various pre input fields.

the transcription step c is performed by calling API functions at the operating system level and at the management tool level to simulate an input in the management tool input module fields.

the method further comprises a manual input step of additional data in the management tool pre existing input module and an enriching step of the pre input rules base and or of the extraction rules base depending on the additional data.

the method comprises a step of simultaneous display of a raw data representation in a first display zone of pre input field in a second display zone and of an input screen of the pre existing input module in a third display zone. The invention also provides a computer system comprising a CPU programme and work memories input devices and a display device characterized in that it contains programmes able to implement the method as defined above.

The invention will now be described in detail by referring to an example of classical application thereof consisting in incorporating automatically the contents of supplier invoices in an ERP. With reference to the incoming aided input data according to the invention involves the following sequence of steps 

b. or by a receiving automaton that reads a structured file for example of the EDIFACT or XML type or even described according to a page description language of the PDF XPS Postscript etc. type.

a. either by an Optical Character Recognition OCR module which is able of finding text elements and their position in the image for the scanned documents 

b. or by conversion programmes e.g. of the PDF2XML type for documents of the PDF text PostScript XPS type which allow transforming a document into a text list of pieces associated to their XY coordinates in the document 

3 Qualification of the data thanks to a pre existing rules base which was fed manually and then enriched by the user through which the programme is able to associate a semantic meaning to each field in isolation from each other with an appropriate confidence level.

If the data is a number with two digits after the decimal point associated with the euro symbol and that the text located to its left is Inclusive of All Taxes this Inclusive of All Taxes data could be qualified with a high confidence level 

If the name of the supplier or his SIREN number French Business Registration Number was identified it is likely that the net amount excluding taxes is located in the same zone on all documents issued by the same supplier.

a. a second rules base related on the input screen operation allows to assign to each input screen field 0 1 or N potential values depending on the result of the previous step 

b. the data thus qualified are offered to the user who can validate them complete them or correct them in a pre input zone by referring to the source displaying zone which contains as the cases may be 

a. when the user decides to validate these data in the pre input screen these values are then transcribed automatically into the corresponding fields of the management software pre existing input screen this transcription is carried out by calling the pre existing functions of the management tool where available or otherwise for example by the following process 

b. on this very pre existing input screen and thus pre filled in some of its fields the user can decide to complete the input before the final validation by using programmes belonging to the management software during these additional inputs the method according to the invention provides advantageously that the pre input module ref. point above is also fed by these additions such as detected for example by the corresponding keyboard actions mouse and this for implementing step 6 below.

a. enrichment of the second rules base above to be able then to formulate to the user richer pre input proposals when a set of similar data arises. For example from the feedback of these additional inputs the pre input module may further deduct an accounting assignment code to be suggested at the next input by automatically associating it to the supplier.

b. enrichment of the first rules base above for example by holding the position of the invoice fields.

a first zone Z containing the graphical representation of the original document with boxed alphanumerical elements A B C D etc. representative of the existence of recovered values at the extraction step 

Of course the skilled in the art can bring about to the invention many variations and modifications. For example it is possible to use semi transparent representation mechanisms on pre input zones and Z and Z inputs to facilitate display and interpretability of these zones. Thus pre input zone Z disappears to come in transparent mask on zone Z in order to obtain a functional enrichment of the input screen.

Some characteristics of zone can also be spread on zone allowing to start from a recognized zone of raw data to be suggested for the input screen fields of the software package as end point fields for example in the shape of a context menu . It is also possible in the display of zone Z to associate a text zone such as a label to a defined zone of the input screen by a mechanism such as the following 

in response to this selection display of a shortcut menu that contains the list of possible pre input screen fields 

