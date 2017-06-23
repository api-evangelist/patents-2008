---

title: Method and apparatus of automatic method signature adaptation for dynamic web service invocation
abstract: A method (and apparatus) for adapting an input parameter, for dynamically invoking target Web services, and for adapting output results, includes receiving an invocation request including an input parameter in a first format. A semantic information representation module MetaWSDL (Meta Web Service Description Language), wherein the MetaWSDL includes a universal XML (eXtended Markup Language) representation which includes semantic information of a Web service method signature, is retrieved from a memory. A MetaWSDL processor is invoked to adapt the input parameter to a second format using the retrieved MetaWSDL. The target Web services are dynamically invoked, using the adapted parameter in the second format, and the output result in the first format is adapted to the second format, using the MetaWSDL.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08326856&OS=08326856&RS=08326856
owner: International Business Machines Corporation
number: 08326856
owner_city: Armonk
owner_country: US
publication_date: 20080219
---
This Application is a Divisional Application of U.S. patent application Ser. No. 10 145 118 filed on May 15 2002 now abandoned.

The present invention generally relates to a dynamic e business applications. More particularly this invention relates to a method and apparatus of automatic method signature adaptation for dynamic Web service invocation.

Dynamic e business is the dynamic adaptation of e business processes and associated systems to support changing business strategies and tactics. It enables enterprise software to be modeled to fit the required business processes rather than the other way around. When companies in an industry use the same enterprise software and adapt their business processes to fit it they inevitably conduct their business in the same way as their competitors. Flexibility in infrastructure design allows new processes to be tried and deployed to develop a competitive advantage by doing it differently than the competition. Dynamic e business offers the same flexibility in business partner integration. Web services technologies enable dynamic e business. The use of Web services as programmable objects with real world actions is fundamental to dynamic e business. By exposing business functions as Web services that can be accessible anywhere over the Internet a company becomes integration ready to jump on any emerging opportunity with a business partner such as to merge business processes in a merger or acquisition.

Web service represents a revolution in e business capabilities it enables a dynamic e business model fosters collaboration with layered services and opens the doors for new business opportunities. Web Service is defined by new technologies like Simple Object Access Protocol SOAP Web Services Definition Language WSDL Web Service Inspection WS Inspection Language WSIL and Universal Description Discovery and Integration UDDI . These technologies include a model for exchanging XML information a language for describing services and a directory for finding new business partners respectively. Together they enable Web services a powerful new paradigm for creating e business applications by integrating reusable software modules supported on the Web.

SOAP defines a model for using simple request and response messages written in XML as the basic protocol for electronic communication. SOAP can be used with any transport protocol HTTP is currently popular. SOAP messaging is often modeled as a platform neutral remote procedure call RPC mechanism but it can be used for the exchange of any kind of XML information. Creating clients to access the SOAP services published in UDDI is a straightforward process if the developer knows the exact interface of a Web Service. Interacting with a document oriented SOAP service requires the use of lower level SOAP API calls. Envelope object containing header and body to be sent must first be created. Another widely used way is interacting with SOAP RPC service.

1. Obtain the interface description of the SOAP service and create a call object. This provides one with the signatures of the methods that one wishes to invoke. Also one can look at a WSDL for the services. The SOAP Call object is the main interface to the underlying SOAP RPC code.

2. Set the target URI and Set the method name that one wish to invoke in the call object and Pass in the URN that the service uses as its identifier in its deployment descriptor.

3. Create the necessary Parameter objects for the RPC call and set them in the Call object using setParams . Ensure one have the same number of parameters of the same types as required by the service.

4. Execute the Call object s invoke method retrieve the Response object and then extract any result or returned parameters.

In the dynamic e business area it is very hard to match the input parameters and output result format in advance for the Web services Invoke in the e business application. Customers marketplaces and search engines can find the company to do business. Upon finding a suitable service provider the company binds to the provider to begin e business transactions. To access a Web service software only gets the WSDL description of interface information. WSDL can be provided to a potential user of a Web service for rapid integration by way of a Web link to the file an e mail attachment or from the UDDI Registry directly. Any companies can publish their own Web Services to any categories in multiple UDDI registries. So the Web Services they published will have different service interfaces which contain different method signatures. The inventors refer to these Web Services as heterogeneous Web Services. 

At the present time even within a specific industry domain there are no industrial standards nor are there unified service definitions. Furthermore neither the service definitions to be unified nor standardized are in the near foreseen future. Therefore heterogeneous Web Services are going to be a fact of life for a while which poses problems for dynamic e business integration. This is because there is always a need for human intervention to read the WSDL for Web Services and then to correctly construct input parameters so that they match properly with the WSDL definitions. Such manual processes take time and cause errors.

The need for a manual process to construct and match input parameters for Web Services is a result of the limited information defined in current WSDL for Web Services interfaces i.e. only the method name and type of parameters which is too generic as well as limited to be adequate for a program to automatically invoke the target Web Service. The current WSDL does not describe semantic information as to how to construct each input parameter i.e. what kind the parameter is representing. For example a WSDL defines an input parameter to be a number i.e. float type which can be interpreted for anything. Is the number representing a measurement e.g. kg pound foot oz or a temperature or is it presenting the amount of money which can be in US dollars or in UK pounds Unless the desired semantic definitions are clearly specified it would not be possible for programs to correctly construct the input parameters for automatic invocation. Similarly problems exist for the need to adapt output results to the correct format and units. Hence there is the need for the manual process in the conventional methods.

In view of the foregoing and other problems drawbacks and disadvantages of the conventional methods and structures an object of the present invention is to provide a method and apparatus of method signature adaptation for dynamic Web Service Invocation for heterogeneous Web Services.

Another object of the invention is to dynamically find Web services that fit the needs of one or more parts of the business process.

Yet another object of the invention is to automatically adapt input and output parameters to eliminate the need for manual adaptation.

Still another object of the invention is to dynamically bind and or invoke Web services by a business application that is part of a business process.

In a first aspect of the present invention a method for adapting an input parameter the method includes receiving an invocation request including an input parameter in a first format retrieving MetaWSDL wherein said MetaWSDL is a universal XML representation which includes semantic information of a Web service method signature and invoking a MetaWSDL processor to adapt the input parameter to a second format using the retrieved MetaWSDL.

In a second aspect of the present invention a method for adapting a Web service output parameter includes receiving an output parameter in a first format retrieving MetaWSDL wherein said MetaWSDL is a universal XML representation which includes semantic information of a Web service method signature providing the output parameter and invoking a MetaWSDL processor to adapt the output parameter to a second format using the retrieved MetaWSDL.

In a third aspect of the present invention a method for method signature adapting an input parameter the method includes parsing the input parameter using MetaData and invoking MetaWSDL to adapt the input parameter.

In a fourth aspect of the present invention a method for generating a MetaClient preference file in a MetaClient library for storing information regarding a preferred set of Web services includes looking up UDDI registries for each preferred Web service and storing the location of each preferred Web service and associated method names in a MetaClient library.

In a fifth aspect of the present invention an apparatus for method signature adaptation the apparatus includes a MetaObject library including self describing objects defined in MetaWSDL a MetaClient library including a preferred library of Web services and a MetaWSDL processor adapted to process MetaWSDL to adapt parameters and to invoke Web services dynamically wherein said MetaWSDL is a universal XML representation which includes semantic information of Web services method signatures.

In a sixth aspect of the present invention a Web service description language for automatic method signature adaptation includes instructions in MetaWSDL which includes semantic information of Web services method signatures.

In a seventh aspect of the present invention a computer readable medium storing instructions for adapting an input parameter which when executed by one or more processors causes the processors to perform receiving an invocation request including an input parameter in a first format retrieving MetaWSDL wherein said MetaWSDL is a universal XML representation which includes semantic information of a Web service method signature and invoking a MetaWSDL processor to adapt the input parameter to a second format using the retrieved MetaWSDL.

In an eighth aspect of the present invention a computer readable medium storing instructions for adapting an output parameter which when executed by one or more processors causes the processors to perform receiving an output parameter in a first format retrieving MetaWSDL wherein said MetaWSDL is a universal XML representation which includes semantic information of a Web service method signature providing the output parameter and invoking a MetaWSDL processor to adapt the output parameter to a second format using the retrieved MetaWSDL.

In a ninth aspect of the present invention a computer readable medium storing instructions for adapting an input parameter which when executed by one or more processors causes the processors to perform parsing the input parameter using MetaData and using MetaWSDL to adapt the input parameter.

In a tenth aspect of the present invention a computer readable medium storing instructions for generating a MetaClient preference file in a MetaClient library for storing information regarding a preferred set of Web services which when executed by one or more processors causes the processors to perform looking up UDDI registries for each preferred Web service and storing the location of each preferred Web service and associated method names in a MetaClient library.

In an eleventh aspect of the present invention a computer readable medium storing MetaData for describing semantic information for Web services.

In a twelfth aspect of the present invention a MetaWSDL processor for adapting an input parameter the MetaWSDL processor including an input adaptation device which adapts and input parameter in a first format to a second format and a dynamic invocation device for invoking a Web service by providing said input parameter in said second format.

In a thirteenth aspect of the present invention a MetaWSDL processor for adapting an output parameter the MetaWSDL processor including a dynamic invocation device for receiving an output parameter in a first parameter from a Web service and an output adaptation device for adapting said output parameter from said first parameter to a second parameter.

Semantic information for describing and quantifying input parameters is collectively termed MetaData in this invention. For example MetaData definitions can be used to provide unit information for an input which is important especially when conversion between units are required such as between oz and liter foot and meter and Celsius and Fahrenheit. Also MetaData definitions can be used to correctly format the input before the Web Service is invoked without having human intervention. For example a business application receives its input to the Web Services from a user or an external media but the input is in a different format than the one defined in the WSDL. Without manual adaptation of the input the Web Service cannot be correctly invoked nor can the desired results be obtained.

The automatic adaptation of input output parameters issue is by far the most difficult and the least developed area in term of utilizing Web Services where there are toolkits and framework that facilitate both issues 1 and 3 . For issue 1 there are IBM Web Service Toolkit WSTK and UDDI4J toolkits and APIs that alleviate portions of the programming tasks from the application for issue 3 there is Web Service Invocation Framework WSIF that provides dynamic Web Service invocation. However there has been no toolkit or framework for automatically adapting input output parameters but it is the most crucial.

In order to fully realize the potentials of Web Services in Dynamic e Business automatically adapting input output parameters is a must. This is because the dynamic nature of Web Services where many new ones can be published and old ones removed updated at any time. Therefore the ability to dynamically bind invoke newly published updated Web Services is essential absolutely requires the capability of automatically adapting input output parameters.

Adaptation of input parameters ensure that the Web Services can be invoked correctly while adaptation of output parameters ensure that the results from the Web Services are meaningful and not just that the number is correct. This invention proposes a framework to adapt user input as well as output results to the correct format and or units that are required to invoke the target Web Service as well as to return the correct results to the client. This invention can be used by all applications that want to dynamically invoke Web Services and obtain correct as well as meaningful results.

To address the above mentioned e business integration issues an exemplary embodiment of this invention is a method and apparatus of method signature adaptation for dynamic Web Service Invocation for heterogeneous Web Services including the following components 

in MetaWSDL including two types 1 basic MetaObject 2 complex pluggable MetaObject for handling data conversions 

E Framework to use the above components to author and publish MetaWSDLs dynamically adapt input and output method signatures automatically invoke Web Services for dynamic e business integration.

An exemplary embodiment of this invention is a framework and mechanism to automate the process for dynamic Web Services invocation it eliminates the need for manual mapping of input parameters with WSDL method signatures and addresses the issues of automatic adaptation for input parameters and output results of target Web Services which enables dynamic Web Services invocation and obtains the intended results in desired units such as money dollars vs. yens or measurement feet vs. meters oz vs. liter . This automatic adaptation is not possible with the current WSDL definitions. The inventive MetaWSDL a universal XML representation includes additional semantic information of Web Services method signatures which are not part of the current WSDL standards. Using both WSDL and MetaWSDL business application software can not only get the basic service interface definitions from WSDL but also the semantic information about input and output from MetaWSDL which enables the Web Service to be dynamically invoked. In other words using the unit or format information about the parameters in the MetaWSDL the parameters of the method can be correctly constructed.

An exemplary embodiment of the present invention meets the following goals of the method signature adaptation for dynamic Web Service invocation 

First several terms and mechanism are introduced. MetaData is used as a mechanism to communicate the semantic information of the Web Services to business applications so that the applications can invoke Web Services dynamically MetaData is essential to solving the Web Services dynamic invocation problem in e business integration. Method signature adaptation is the process of parsing the MetaData or semantic definitions of the Web Services automatically constructing the input parameters as well as adapting the inputs and outputs to the proper format units. Lastly MetaWSDL a universal XML representation is proposed in this invention to describe MetaData it is complementary to the current WSDL and enriches the semantic definitions of Web Services.

Referring now to the drawings and more particularly to there are shown exemplary embodiments of the method and structures according to the present invention.

Although not shown the user I O may include any number of devices to interface with a user of the system . The user I O may include for example a keyboard a microphone a pointer device such as a mouse trackball or pen or any other user interface device.

The organization of the following description first discusses four components A B C and D of an exemplary embodiment of the present invention as listed below followed by a description of a Framework for the system architecture in which section five uses the four components described before. Together they accomplish the goal of automatic signature adaptation for dynamic Web service invocation in accordance with the present invention.

Referring now to in order to convert input parameters MetaWSDL is created at to include the semantic information which are embodied by MetaObjects. Each MetaObject represents a real life object or notion such as zipcode a state name a measurement unit e.g. kg ounce or a currency USDollar or FrenchFranc etc. and handles data conversions of input parameters and output results.

There are two main types of semantic information for method signature adaptation 1 Specifications for input parameter adaptation many to one mapping. The designated input type to the Web Service is denoted by the keyword unit as specified in unit xsd Kg where a MetaObject of Kg embodies the actual Kilogram unit and handles conversions from itself to other known units such as Pound . The keyword native unit denotes the unit format native to the locale as obtained by the business application. When nativeunit is not the same as unit a MetaWSDL processor automatically performs a conversion converting from nativeunit to unit and the mapping can be many nativeunits to one unit before the Web Service can be successfully invoked.

Further there is 2 Specifications for output result adaptation one to many mapping. When unit is not the same as native unit a MetaWSDL processor automatically performs a conversion converting from unit to native unit and the mapping can be one unit to many native units before the correct result can be returned to the client.

It is important to note that MetaWSDLs are not only useful to automate method signature adaptation using programs but also can serve as guides to application developers as manual adaption of method signatures.

The examples that follow describe two types of input adaptations List 1 using basic MetaObject List 2 using the extensive and pluggable MetaObjects List 5 describes output adaptation using a basic MetaObject.

This is an example extension which allows a description of how to create the native data and invoke a Web Service.

In List 1 in order to perform the method signature adaptation for the input parameters the above MetaWSDL is created to include the semantic information which introduces four MetaObjects in the definitions i.e. the kg pound ounce and ton basic MetaObjects. The unit specifies that the input for the InShippingQuoteRequest Meta Web Service is in kg and the nativeunit which is the input format the application client has and it can be pound ounce or ton for example. Thus a conversion is required to convert from the nativeunit of pound ounce or ton to the unit of kg using the MetaObjects defined in the MetaObject Library for the conversion.

For basic MetaObjects such as kg and pound ounce or ton no conversion mapping is specified in the MetaWSDL a default method supported by the basic MetaObject is used to perform the conversion. Note that there is an extension tag shown in List 1. This is an optional tag which is used to carry more information about the invocation process. For example one can show an example native data within this optional tag.

In List 2 in order to perform the method signature adaptation for the input parameters the above MetaWSDL is constructed to include the semantic information which introduces two complex or custom MetaObjects i.e. USML and String2USML MetaObject in the definition. The unit specifies that the input for the InSearchUDDIRequestMeta Web Service is USML and the native unit specifies that the application client obtains is a regular string.

The conversion mapping specifies the customized MetaObject String2USML MetaObject which will be used to handle the conversion from the nativeunit of string to the unit USML a well formed UDDI Search Markup Language USML string and then invoke a target Web Service of SearchUDDI. The content included within extension tag in List 2 are extracted and shown in List 3.

In List 5 that follows the example shows the output result adaptation for currency. In the example below several basic MetaObjects are defined i.e. USDollar BritishPound JapaneseYen GermanMark and FrenchFranc . These currency units are specified as nativeunit which means the currency is from the locale or country of origin where application client runs and the application can receive any one of such nativeunit s as input the unit denotes that the Web Service output format is USDollar . When unit is not the same as nativeunit MetaWSDL processor automatically performs an adaptation to convert USDollar to whichever currency specified by nativeunit before returning the result back to the application.

The purpose of the MetaObject Library is to assist in method signature adaptation. The MetaWSDL Processor to be discussed next uses the MetaObject Library to perform required data conversions of input parameters and output results. The MetaObject Library provides a set of data transformation objects which can be implemented as Java Classes or other application packages to handle format unit conversions XML translation script plug in modules and so on.

These data transformation objects handle simple conversions of measurement temperature date currency etc no conversion mapping needs to be specified For example the units of weight may be kilogram or pound. The units of measurement can be mile or foot oz or liter. The units of temperature are Celsius or Fahrenheit. Date formats include USDate EuropeanDate Week and Day. The units of currency are USDollar BritishPound JapaneseYen RMB and so forth. The address includes StreetNumber City and Zipcode. No conversion mapping is specified for Basic MetaObject as conversion functions for these Basic MetaObjects are defined in MetaObject themselves.

The MetaObject library comes with several extensible MetaObjects and a user can define their own MetaObjects that get plugged into the MetaObject library. The conversion mapping must be specified for the custom MetaObjects. These are MetaObjects that are customizable and pluggable. For example Math MetaObjects for Math Markup Language MML are defined to process MML when present and to perform Math calculations using the specified conversion.

Another example may be the USML MetaObject for UDDI Search Markup Language USML which is a MetaObject that constructs USML script using the input parameters from the application client. A Weather MetaObject is yet another example of a MetaObject defined to construct a specialized XML request for a Weather Web Service for weather information. Other MetaObjects can also be defined to handle other kinds of data transformation and processing.

The purpose of the configuration file XML or text etc. is to define all the MetaObjects that the MetaWSDL processor knows about. The MetaObjects can be simple extensible or user defined. Whenever there are new user defined MetaObjects simple or custom pluggable they must be added to the configuration file for the MetaWSDL processor to be able to invoke them at runtime. The configuration file is a mechanism that the custom MetaObjects can be plugged into the MetaObject library and be known to the system without any code changes.

List 6 below shows three examples of MetaObjects Celsius the basic type USML the complex type provided by the MetaObject Library and the UserDefinedMetaObject which is also a complex type but is provided by a user and gets plugged in to the MetaObject Library.

The MetaWSDL processor is the runtime central control of this framework. Its main functions are to process MetaWSDL to adapt parameters and to invoke Web Services dynamically. The MetaWSDL processor uses other components of the framework e.g. MetaWSDL and MetaObject Library to accomplish these functions. The details of how the MetaWSDL Processor works are described in the System Architecture below and shown in and include 

The MetaClient Library provides APIs to invoke an advanced UDDI search engine to lookup UDDI registries retrieving a preferred set of Web Services. Meanwhile it stores the location of WSDLs and the method names. Preferences are defined in a preference file text or XML . The Library may provide a set of default preference files. For example the default preference files may be based on the locale e.g. European North America South America Africa Asia etc. see examples below . An application developer can also make modifications as needed. A MetaClient Preference Library is built using the Web Service name WSDL location and method name. The MetaClient Library APIs store events and updates one or multiple UDDI registries i.e. when a new Web Service is published or an existing Web Service is unpublished the MetaClient Preference Library is updated with the latest information about Web Services. The MetaClient Library APIs should be invoked prior to invoking the MetaWSDL processor to keep the client side information up to date. The MetaClient Library APIs provides a mechanism for the application to parse its input based on the MetaWSDL and thus simplifies the input parameter passing to the Web Services and eliminates the manual matching process.

The MetaClient library can be tailored to different applications by customizing the search criteria for the advanced UDDI search engine. For example shipping planning applications may be interested in transportation Web services while financial applications may be interested in statistical Web Services.

Furthermore in dynamic e business applications an application client does not always know which Web Service will be invoked at all times because different Web Services will be invoked based on different business rules context or preferences. If the rules or preferences are defined the application client can use an advanced UDDI search Engine such as BE4WS Business Explorer for Web Services to find the correct Web Services for a business context. For example if the cost of shipping an order is bigger than 100 Transportation Service A may be selected and invoked otherwise the Transportation Service B will be invoked instead. Also when the shipping order status tracking is needed the Tracking Web Service may be invoked.

An exemplary embodiment of the system architecture of method signature adaptation for dynamic Web Service invocation is shown in . There are five major processes and they use the main components described above such as MetaWSDL MetaWSDL Object Library etc. 

The resulting MetaWSDL is referenced by a Web Service Inspection Language WSIL document or other documents such as a regular text file. In this invention the inventors used WSIL document to reference the MetaWSDL. There are at least two ways to locate and retrieve the MetaWSDL 

The reason the inventors choose WSIL document WS Inspection for carrying MetaWSDL .mws is that the information contained within the description elements are extensible and customizable. These elements can be used to point to service description documents of various forms to allow users to process only the ones that they find useful.

One example of such elements contains the referencedNamespace attribute which identifies the name space to which the referenced document belongs. An example of the value of a referencedNamespace attribute for a description element that points to a WSDL document would be http schemas.xmlsoap.org wsdl see List 5 Example WSIL document below for details . The referencedNamespace attribute helps the users of WS Inspection documents to determine if the referenced description document is of interest to them. The optional location attribute is used to provide the actual reference to the description element.

One extensibility element that this invention proposes to add under the description element is to provide a pointer to MetaWSDL which includes semantic information needed for method signature adaptation. The document name space specified by the referencedNamespace attribute is http schemas.xmlsoap.org metawsdl .

In an example WSIL shown in List 7 below two services are listed enclosed between the and tags. Each service contains two description elements with one having a referencedNamespace attribute of WSDL and one of MetaWSDL. The location attributes indicate where the WSDL or MetaWSDL can be retrieved respectively.

One primary function provided by the WS Inspection specification is to define the locations where one can access WS Inspection documents. There are two conventions that make the retrieval of WS Inspection documents easy 

The fixed name for WS Inspection documents is inspection.wsil. A document with this name can be placed at common entry points for a Web site. For example if the common entry point is http invocation4WS.com then the location of the WS Inspection document would be http invocation4WS.com inspection.wsil.

References to WS Inspection documents may also appear within different content documents such as HTML pages.

The combination of the WSDL MetaWSDL and the Web Service Inspection Language WSIL has the potential to satisfy the dynamic invocation pattern for a Web Service request. As mentioned prior a MetaWSDL carries all semantic information for a method signature that is not included in the WSDL which carries the basic method signature information for a Web Service. WSIL provides links to the location of MetaWSDLs.

As usual Web Services deployed on SOAP server are required to have their interfaces published to a UDDI registry or to a WSIL document on a Web Server. The hyperlink of the WSDLs are assigned by the Web server or UDDI registry server.

Furthermore MetaWSDL WSIL documents and WSDL can be published on different servers. In addition all MetaObjects defined by MetaWSDL schema should be stored in the MetaObject Library .

The method signature adaptation includes two types of adaptations. The first one is input parameter adaptation . For example if there is unit or format information about the input parameters of the method in the MetaWSDL the input parameters can be correctly constructed. There are at least two ways to perform the adaptation 1 manual construction and 2 automatic construction. When the business application invokes the MetaWSDL processor proposed in this invention automatic construction is always performed which refers to the automatic data transformation by a MetaObject in the MetaObject Library based on the conversion schema. For instance if a method of a Web Service requires a specific XML string as input the application client needs to convert a set of input strings to the required XML string for the method invocation. Manual construction means that the application developer needs to manually construct the input parameters based on the description and guide described in MetaWSDL.

At this stage the MetaWSDL processor will invoke the method requested by the application client using input parameters already adapted using MetaWSDL. The invocation mechanism can be either the regular SOAP RPC client or the Web Service Invocation Framework WSIF client.

This stage adapts the output to the correct unit or format as defined in the MetaWSDL following the Dynamic invocation step described next. For example if the unit of a stock quote from a Web Service invocation is USDollar but the desired unit for the quote for an UK application is UKPound the quote is automatically converted to UKPound based on the MetaWSDL before returning it back to the application client .

In this case the overview URL of the business is given by the application client directly. The process of signature adaptation and invocation is described above in relation to the system architecture of .

In this case the application client needs to submit the UDDI search via USML to the MetaWSDL Processor which will look up the desired Web Service in UDDI and then find the overview URL for the business in the system architecture.

In both cases the application client must be able to specify to the MetaWSDL Processor the desired method name to be invoked dynamically as in most cases there are multiple method names defined within a single WSDL. This scenario is ensured by following the MetaClient Library mechanism as described above.

The following steps describe the exemplary process flow as illustrated in . In step the application client invokes the MetaClient Library to store a preferred set of Web sServices in the MetaClient Preference Library by looking up UDDI registries and selecting based on a preference file or a default file with modifications if desired for the locale e.g. European North America Asia etc. see details in MetaClient Library Section above . The Overview URL is found in one of two ways Steps 1 If the Overview URL of the WSDL is not known the system retrieves it which can be done via a UDDI search engine e.g. BE4WS which parses incoming search requests specified as USML script searches multiple UDDI sources aggregates search results and returns a target Web Service and 2 the Overview URL of the WSDL is known before the invocation.

Steps invoke MetaClient Library APIs to retrieve the corresponding MetaWSDL for the desired WSDL found in step . The input is parsed. That is MetaClient Library APIs are used to parse input based on the MetaObjects defined in the MetaWSDL.

Step the parameters in MetaObjects type method name locations of overview URL MetaWSDL and preference file for output adaptation are passed.

In step A the input parameter is adapted using MetaObject Library. Then to invoke the Web Service in step B Steps either SOAP RPC client or WSIF client can be used passing the adapted input parameters and receive results.

In step C Step the output results are adapted using MetaObject Library to match the correct unit format as specified in the MetaWSDL and return the adapted output to the application client.

The following example is used to illustrate why a MetaWSDL is needed and how to create a MetaWSDL for a real Web Service. Meanwhile the output adaptation for get Temperature Web Service is also shown as follows 

The WSDL only defines the parameter numbers and types for the getTemperature Web Service. There is no other information associated with the parameters.

The output type of getTemperature Web Service is float. But there is no unit information or formats about this output result.

In order to perform the method signature adaptation for the input parameters the inventors constructed the following MetaWSDL to include the semantic information which introduces two MetaObjects in the definitions i.e. the Zipcode and the Day Basic MetaObjects. The first parameter is Zipcode MetaObject for the US zipcode format and the second is the Day MetaObject for number of days.

The keyword unit specifies the MetaObject Zipcode is used in the input to the getTemperature method. The keyword nativeunit means what kind of the native format the input obtained by the business application. When nativeunit is not the same as unit a conversion needs to take place to convert from the nativeunit to unit before the method can be invoked. In this case the nativeunit is also in the same MetaObject Zipcode and State format. Therefore no conversion is needed.

In order to perform the method signature adaptation for the output result the inventors constructed the MetaWSDL as shown in List 10 above to include the semantic information which introduces two MetaObjects in the definitions i.e. the Celsius and the Fahrenheit basic MetaObjects. The unit specifies that the output from the getTemperature Web Service is in Fahrenheit and the nativeunit requires it to be in Celsius. Thus a conversion is required to convert from unit of Fahrenheit to nativeunit of Celsius. Another possible conversion is from Fahrenheit to Kelvin if the application s native unit is Kelvin.

The output result from the Web Service invocation is 77.0 Fahrenheit. But the application client is using a different unit for example Celsius. So the MetaWSDL Processor automatically converts the original result with unit Fahrenheit into the required output with unit Celsius using the MetaObject defined in the MetaObject Library.

As shown in the system for automatic method signature adaptation for dynamic Web service invocation is preferably implemented on a programmed general purpose computer. However the system can also be implemented on a special purpose computer a programmed microprocessor or microcontroller and peripheral integrated circuit elements an ASIC or other integrated circuit a hardwired electronic or logic circuit such as a discrete element circuit a programmable logic device or the like. In general any device on which a finite state machine capable of implementing the method described herein can be used to implement the method for automatic method signature adaptation for dynamic Web service invocation.

While the invention has been described above in relation to a WSIL document it is understood that this is only one exemplary embodiment of the invention. One of ordinary skill in the art understands that the invention is applicable to any other comparable mechanism to retrieve a network accessible document like MetaWSDL which describes the semantic information of the WSDL.

It is to also be understood that the MetaObjects described above which form a portion of the invention may be co located or dispersed. The components of the invention may be stored or processed anywhere within an apparatus such as a distributed process network and still form a part of the invention

While the invention has been described in terms of several exemplary embodiments those skilled in the art will recognize that the invention can be practiced with modification within the spirit and scope of the invention.

