---

title: Personal token having enhanced abilities for delivering HTML data
abstract: The invention relates to a personal token storing a javacard application code lying over an area of the memory of the personal token, the personal token being able to run such javacard application so as to deliver HTML page data to an external device for the external device to display an HTML page on the basis of the such delivered HTML page data, said personal token further storing data to be used as a constructing part of the HTML page, characterized in that the data to be used as a contributing part of the HTML page are in at least one file which is separate from the memory area over which the Javacard application code is lying, and the personal token is programmed for opening the at least one file storing the contributing part of the HTML page when such data are requested for delivering said HTML page data to said external device.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08381235&OS=08381235&RS=08381235
owner: Gemalto SA
number: 08381235
owner_city: Meudon Cedex
owner_country: FR
publication_date: 20080122
---
The invention relates to personal security tokens when hosting Javacard applications for delivering html pages to an envisioning device. Such personal tokens are generally known as personal tokens including a web or HTML server.

Personal tokens are used for authenticating a user when such user accesses to a limited or a private resources equipment such as a mobile telecommunication network a bank facility or network a remote server storing secret data or even a protected area with limited physical access thereto.

The mostly known device of this type is the IC card such as for example a SIM card Subscriber Identification Module or a credit card but it can also be a USB key a mass memory card or any kind of token carrying some necessary credentials. Such tokens are typically compliant with international standard ISO7816.

The envisioning device is typically the mobile terminal in a mobile telephony network but can also a hosting PC or a remote terminal in an IT network either the internet or a company internal network.

Javacard is a language and programming system which is derived from Java i.e. with simplified functionalities due to the reduced abilities of smart cards but retaining the main aspects of Java such as downloading of .cap file instantiation registering using application Ids and more importantly a selected group of the original Java language instructions which make Javacard keep the object oriented nature of original Java. Javacard enabled smart cards or USB dongles are well known.

Oftentimes Javacard is used for delivering HTML data to a hosting device which hosting device runs an HTML engine which engine reads the such delivered HTML data and constructs an HTML page departing on such delivered data. The delivered HTML data are sufficient data for describing the content to be found in the HTML page i.e. static objects dynamic objects and a template for organizing the static and dynamic objects in the page.

Javacard applications are loaded into security tokens either over the air either by wired means i.e. in the factory while customizing the token or even at a selling point by means of a local computer with some dedicated connections and a driver for that purpose. Javacard applications are difficult to update. Some Javacard data which are already present in the token are oftentimes impossible to modify which means that the whole application has to be downloaded in a new version which encompasses the modified data. This also means that the token has to be either brought back to factory or to a selling point or that a new downloading of the complete application code i.e. of the .cap file has to be carried out over the air which is long and fastidious for the operator and requires difficult memory management in the token.

This appears to be particularly true for application codes which are dedicated to delivering HTML page data when it appears necessary to amend the HTML page.

For example changing an object in the HTML page or amending the template of the HTML page for emphasizing a particular object rather than another one requires the Javacard application to be downloaded again in the card and interpreted again by the card in its modified version.

The purpose of the invention is to solve this problem e.g. to propose an implementation of a Javacard application in a personal token which eases the process of amending HTML pages to be displayed when a personal token is implied. Such purpose is achieved by the invention though the features as recited in the appended claims. Other aspects aims and advantages of the invention will appear through the following description.

As represented on for hosting a Javacard application such as a game e purse or phonebook application a SIM card according to the prior art is first downloaded with a .cap file i.e. a set of Javacard instructions which have previously been compiled and converted inside a remote server. Such .cap file still has to be interpreted so as to be rendered executable i.e. the .cap file has to be instantiated by a Javacard Virtual Machine which Javacard Virtual Machine was present in the card prior to downloading. The .cap file then becomes what is called a Javacard applet as represented under reference on .

This Javacard applet is made of a series of instructions which are now coupled to parameters thanks to the performed instantiation step which parameters were downloaded also inside the .cap file but initially not coupled to the corresponding instructions.

The instructions of the Javacard applet describe HTML data to be transmitted to the mobile terminal hosting the SIM card once an HTML page is required by an end user. Such HTML page may be a welcoming Screensaver intended to be displayed when the end user powers his mobile on or a menu allowing the end user to choose among several functionalities implemented in the SIM card .

Those HTML data in the Javacard applet comprise template data which describe the overall shape of the HTML page as well of the places some objects must have in the page i.e. each place reserved for a static object or for a dynamic object in the page.

The Javacard applet also comprises instructions for building dynamic objects of the page which may typically result from a calculation or from a particular state of the Javacard applet at the time the page is requested by the end user.

The Javacard applet also comprises static objects data i.e. data that describe objects which are not intended to change nor to be adapted in the course of running the Javacard applet.

A SIM card running a Javacard application according to an embodiment of the invention will now be described in reference to .

The SIM card of hosts an instantiated and registered Javacard applet The original .cap file is represented on but does no more operationally exist in the card after the Javacard applet is instantiated.

The Javacard applet is saved in a part of the memory of the SIM card which is usually dedicated to Javacard applets. This dedicated part is located inside the non volatile portion of the memory of the card usually implemented as EEPROM memory Electrically Erasable Programmable Read Only Memory .

On the right side of another physical part of the non volatile memory is represented which hosts a series of contiguous files . Each of these files is in the TLV format i.e. is made of three parts. A first part of each TLV file a Tag part the following part is a Length part which includes a Length amount and the last part of the TLV file is a Value part which comprises a value which volume thereof determines the length as placed in the preceding Length part of the TLV file.

The TLV files of that part of the memory are usually used for storing communication parameters as listed and required in the telecommunication standards.

In addition to such purpose those TLV files are here used for storing data which are intended to the Javacard applet and aimed at constructing the HTML page data. The Javacard applet is programmed for fetching those HTML data in the TLV files during the course of execution of the applet .

Here the HTML data such stored in the TLV files are of two types. Some TLV files store HTML template data i.e. HTML data which describe the shape and overall construction of the page.

One TLV file describes one template several templates being presently described in several respective TLV files in the present case. As well one TLV file describes one static object several static objects being presently described in several respective TLV files in the present case.

In each static object TLV file each Value portion of the file is an HTML string which describes the content of the static object itself each Length portion stores the actual length of the such HTML string and each Tag portion stores an identifier of the static object itself which identifier is used for retrieving the proper static object which is looked after.

A string in Javacard is a set of alphanumerical characters comprised between which describes a visual object such as a static object to be placed in an HTML page.

Different formats of files might be considered for the storage of the HTML templates and the HTML static objects from binary to BER TLV formats. BER TLV is the preferred format. A standard lightweight format is more generally favored.

For the purpose of retrieving the template data and the static objects data the card hosts and runs an API application programming interface referenced . The API reads the template data parses them and transmits data either to the mobile terminal or back to the Javacard applet depending on the processing that has to be done on the considered data.

For example when the template comprises static data and also identifies necessity for dynamic data by means of identifiers the static data are transferred by the API directly to the mobile terminal and the dynamic data identifiers are transmitted to the application for further processing and rendering of such dynamic data.

On steps referenced from A to E are represented which correspond to the successive tasks performed by the mobile terminal the Javacard applet the API . also represents the data retrieved from the TLV files in the process of gathering the HTML page data.

As a first step A the mobile terminal makes an HTTP request to the application . The code of the application includes a part which is dedicated to processing the HTTP request. This HTTP request processing part invokes as step B the API . The API then reads as step C the template file in the corresponding TLV data file which template here comprises static data including static strings some of them describing respective static objects but which may also identify static data in other TLV files which static data may describe static objects.

The template API or templating engine then parses the template file into static data as step D and into dynamic identifiers which identify dynamic objects to be created. The API passes directly the static data to the mobile terminal and transfers the dynamic identifiers to the application .

Application comprises a template callback module which generates the identified dynamic objects when invoked by the template API . Application implements this way a callback interface. For invoking the callback module the template API transfers the dynamic data identifiers as well as the HTTP request object to the template callback module as step E .

At step F the template callback module generates the identified dynamic data based on the dynamic data identifiers and on the HTTP request object and on the basis of any additional application specific data source. In other words the application logic uses the information received from the API as well as its own sources in order to generate the dynamic data. The dynamic data are then automatically added to the output HTML page.

The invention has been described in the case where static objects and template are stored in locations which are not embedded in the application code.

In the frame of the invention the Javacard application code may include the static objects data embedded therein only the template data being stored in a separate location. On the contrary and still in the frame of the invention a Javacard application may fetch data in a separate location for retrieving static object data but encompass the template data inside the application code.

In this alternate embodiment the static objects used by the application are stored in one or several separate files dedicated to such strings and each string is identified by an identifier for example a scalar. A Javacard API similar to the previously described API allows the applet to retrieve the static object data in the separate file in the form of a bytearray constituting the string by using the identifier of such string. The API opens the file containing such a static string resource and gets a bytearray from an identifier of the string as extracted from the application.

In those different embodiments the advantages are the following ones Building dynamic HTML pages previously required heavy string manipulations and concatenations. Most of the strings used in dynamic web pages are actually static. The only possibility for describing a string was a bytearray in the application code. Static parts of HTML pages had to be described in static bytearrays and be hardcoded in the JavaCard application. For example static strings used for building HTML pages were hardcoded in the application source code they could not be easily updated for customization internationalization purposes. Customization of static strings is also useful for instance for fixing a bug.

Apart from reinstalling a new .cap file with updated constants internationalization was also achieved by hardcoding the different languages strings within the applet s code or by managing several versions of the same application in the token.

Nor did Javacard provide any efficient way for concatenating static strings for building complex HTML pages. Therefore application logic was in charge of concatenating the string bytearrays with dynamic elements in order to build the dynamic content. Due to lack of support for bytearray concatenation in Javacard and comprising no separate string object as proposed here building a dynamic HTML page required a lot of manual buffer operations and was therefore very slow.

In terms of code size and performances the described API which fetches string resources allows to limit bytearray manipulation in JavaCard applications. In addition constant scalar identifiers are used in place of static bytearray strings in the application which reduces code size and increases performances.

The strings included in the separate resource files can be customized according to customer requirements. For instance one string containing the operator name might be easily changed without amending the application code.

Static string files can be updated remotely through classical remote file management techniques in order to fix potential bugs or slightly update the application.

Several internationalization resource files can exist on the card one for each national language. The JavaCard application can choose the one adapted to current user language preferences. New languages might also be easily deployed post issuance as downloaded updates of static objects in corresponding files.

Due to the storing of the template in a separate file location a template can be processed internally by the API using native services. This also reduces the need for buffer manipulation in JavaCard and improves performances.

Templates can be easily customized based on customer requirements without changing the application code.

Templates can be updated remotely through classical remote file management techniques in order to fix potential bugs or slightly update the look of the application.

Several templates can exist on the card one for each national language. JavaCard application can choose the one adapted to current user language preferences. New languages might also easily be deployed post issuance as downloaded new language templates in a corresponding file.

