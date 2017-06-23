---

title: Event driven disposition
abstract: This disclosure relates to systems, methods and apparatuses for managing the retention and disposition of data for an event consumer using an Enterprise Retention Management System wherein the management is driven by business events.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08327384&OS=08327384&RS=08327384
owner: International Business Machines Corporation
number: 08327384
owner_city: Armonk
owner_country: US
publication_date: 20080630
---
The present invention relates to systems for the disposition of data. More specifically the present invention relates to technology for retention policy management record management and enterprise integration for data disposition.

Business organizations retain electronic documents records and other data in storage for extended periods of time for a number of reasons including easy access internal policy and regulation compliance among other various reasons. For instance government regulation may require an organization to retain certain securities information for a given duration for SEC compliance. Likewise some organizations retain electronic records of documents for audit and or litigation purposes.

Oftentimes data storage systems involve storing data with an associated retention policy. The retention policy indicates a time period for the retention of the data and when the time period lapse the data is typically disposed of automatically. According to known methods a system administrator must dispose of data manually based on retention policies stored on paper or in other non structured form. Organizations managing a large amount of stored data will incur time consuming and costly expenses in performing data disposition manually.

Furthermore an error in data disposition may result in dire consequences. For instance in cases where data wasn t disposed of too much data has been disposed of or wrong data has been disposed of an organization may incur unwanted legal and business consequences. Therefore there is a need in eliminating human factor from data disposition as much as possible.

There is no uniform view on how to manage disposition of data. This needs to be changed in order to get under control growing storage and legal costs associated with storing unnecessary information. Vendors should start designing their applications with data disposition in mind. To achieve that they need to agree on common ways to manage data disposition.

Different types of data is associated with different retention schedules i.e. rules describing how long the information should be preserved in a certain data source what is the type of event that triggers measuring of the disposition period and what should be done with the information when the disposition period is due . Some data sources can enforce retention schedules e.g. dispose of data using the rules defined by retention schedules some cannot. For the latter type it is hard to build an automated disposition solution using enterprise integration technologies such as integration middleware. This is mainly because retention schedule information is missing in most data sources and because the retention schedule information is a critical part of a solution that defines delays between the time a triggering event occurred and the time when a document should be disposed of.

Enterprise level data retention management is an emerging technology. Currently Enterprise Retention Management systems ERM systems store references to data sources and store retention policies in a structured format. However the retention policies were not utilized in a structured format to affect the disposition of data.

Business events have a substantial effect on how long certain data must legally be retained. Known methods of data retention management for an enterprise system are not designed to use machine readable retention schedules when dealing with the disposition of data. To fill the need for such a system the present invention discloses an Enterprise Retention Management System which considers business events coming from a data source that may result in disposition of documents in another data source.

This disclosure relates to systems methods and apparatuses for managing the retention and disposition of data by an Enterprise Retention Management System. The retention and disposition of data is driven by business events. These business events originate in an event producer. An Enterprise Retention Management System is provided to manage retention and disposition actions. Business events are propagated between the event producer and the Enterprise Retention Management System and the Enterprise Retention Management System translates the business events into Disposition Requests. Event consumers are identified wherein the event consumers include systems and applications having data with retention attributes. The Disposition Requests are propagated between the Enterprise Retention Management System and the event consumers wherein the disposition requests result in the disposition of data.

The business events are propagated between the event producer and the Enterprise Retention Management System in a variety of ways. In some embodiments of the present invention the business events are pushed from the event producer and the Enterprise Retention Management System. In some other embodiments of the present invention the business events are pulled from the event producer to the Enterprise Retention Management System to event producer. In yet other embodiments a business event is manually entered into the Enterprise Retention Management System via a user interface.

In some embodiments of the present invention a direct link is established between an event producer and an Enterprise Retention Management System. In other embodiments one or more connectors are utilized to couple the event producer and the Enterprise Retention Management System. In some embodiments of the present invention the connector is a node comprising software either integrated within the ERM machine or located on another machine within a network coupled with the ERM machine. In yet other embodiments of the present invention the connector is a proxy.

In some embodiments of the present invention the Enterprise Retention Management System includes a routing configuration module allowing the user to configure the ERM based on specific Event Producers and Event Consumers. In some embodiments a Graphical User Interface is provided to facilitate easy manual configuration. In some embodiments of the present invention an event category hierarchy is provided to present event categorization to the user. In other embodiments of the present invention the step of configuration is automatically performed.

In some embodiments of the present invention the Enterprise Retention Management System polls the event consumer to determine information about the event consumer. In some embodiments the polling identifies whether an event consumer is a simple consumer or a retention capable consumer. In some embodiments of the present invention the Enterprise Retention Management System manages a retention schedule for a simple consumer and sends a simple delete instruction to the event consumer. In some embodiments of the present invention a retention capable consumer manages a retention schedule for itself and the Enterprise Retention Management System simply sends the business event message to the consumer to trigger the disposition process.

Those of ordinary skill in the art will realize that the following detailed description of the present invention is illustrative only and is not intended to limit the claimed invention. Other embodiments of the present invention will readily suggest themselves to such skilled persons having the benefit of this disclosure. It will be appreciated that in the development of any such actual implementation numerous implementation specific decisions must be made in order to achieve the developer s specific goals. Reference will now be made in detail to implementations of the present invention as illustrated in the accompanying drawings. The same reference indicators will be used throughout the drawings and the following detailed description to refer to the same or like parts.

Business events have a substantial effect on when it is appropriate to begin tolling a period before data may be disposed of. Known methods of data retention management to not provide an automatic method of capturing a business event turn it into a disposition request and automatically propagate the disposition request to interested event consumers. To fill the need for such a system the present invention discloses an Enterprise Retention Management System which takes into account various business events that may dispose of data related to the event in a data source.

Information Technology infrastructure will benefit from the methods of Event Driven Disposition according to the present invention. The present invention is an Enterprise Retention Management System that allows for automated disposition of information in the Event Consumer data sources based on business events registered in Event Producer data sources and catalog of Retention Schedules and map or data sources maintained by the Enterprise Retention Management System. The Enterprise Retention Management System orchestrates the propagation of business events from event producers to event consumers translates business event parameters that came from an event producer into disposition request parameters understood by an event consumer and enforces retention policies by delaying event propagation to the event consumers which are unable to manage retention policies themselves.

Such a solution will become a common way of orchestrating event driven disposition thus encouraging vendors to build event driven disposition functionality into their products upfront.

Business events are uploaded to an Enterprise Retention Management System hereinafter referred to as an ERM . In some embodiments of the present invention the event producer data source pushes the business event to the ERM . In other embodiments the business event is pulled from the event producer data source into the ERM . In yet other embodiments the business event is manually entered into the ERM .

Once a business event is received by the ERM the ERM identifies a portion of data within an Event Consumer data source . In some embodiments of the present invention an explicit route between particular events from the event producer data source and particular Event Consumer data sources is established. In the present preferred embodiment of the present invention a routing configuration module not shown is provided to establish routes explained below . In some embodiments of the present invention the step of configuration is performed by a routing configuration application with a user interface that is part of the ERM. In other embodiments a stand alone Configuration Application is coupled to the ERM and serves to configure routing information.

Once the business event is routed to an appropriate Event Consumer and the parameters of the event are resolved explained below the ERM then makes data disposition requests to an Event Consumer data source . The Event Consumer data source performs data disposition actions based on the information disposition requests .

The present invention operates according to these basic models. Below the concepts are more specifically defined and the operation of the method is explained in more detail.

Event producers are information systems that contain information about some business events happening at the enterprise. Examples of business events are 

In some embodiments of the present invention event producers are structured information systems. According to the present invention events are recorded within the systems by changing a value of some status field in the database record. E.g. in case on employee termination the field employment status in person table of a Human Resource Management System gets changed to terminated . Although the example of a Human Resource Management System is disclosed it will be readily apparent to those having ordinary skill in the art and the benefit of this disclosure that many other types of Event Producers can utilize the event driven function of the present invention.

Event messages produced by an Event Producer oftentimes contain one or more parameters that describe the event. Typically the parameters comprise a name and a value. For example an event relating to an employee might contain the parameter employee id 21422 . According to the present invention the structure of the parameters is flat i.e. a list of name value pairs or hierarchal where certain parameters contain child parameters .

Event consumers may require all or some parameter values to be passed to them in order to make a disposition. Sometimes the information provided inside parameters is not sufficient for the Event Consumer to perform a disposition. For example a Human Resource Management System serving as an Event Producer produces employee related events with an employee id parameter containing Human Resource Management System internal employee id which looks like emplo000000000012351 whereas an access control system tags employee records using a Global Company Employee ID which looks like pat.rose.xyzcorp.com .

In some embodiments of the present invention there are some manual or automatic ways to resolve parameters provided by the Event Producer into parameters required by the Event Consumer. For example a company may have a centralized unique identifier of the person which can be resolved into unique identifiers of the same person specific to different information systems.

All the above events have a different nature which we call event type . Event types on the examples above are 

Event parameters can be further subdivided into the ones required for all event types by event driven disposition infrastructure infrastructural and the ones that pertain to an event type. For example the following parameters are envisioned for employee termination event type there may be more 

We are expecting that a business event will expose as many parameters as possible so we have enough information for all kinds of consumers. In this example Person Mailbox information may be useful for propagating the event to email archives and Extended Field may contain person s global company ID used by access control system to store person s access records.

These are various types of information systems in a broad sense file systems content management systems document management systems structured applications email servers and archives instant messaging servers and archives file archives etc. that can receive business events and perform data disposition based on these events.

Note that event consumers don t necessarily need to store digital information. For example the event consumer may be an Iron Mountain Acutrack application that manages the storage and disposition of physical assets in Iron Mountain Corporation. Also according to another example Event consumers may be an issue tracking system such as BMC Remedy. Once the issuing tracking system receives a disposition request it issues a service ticket to an IT employee instructing the employee to perform a certain manual disposition task.

Information on event consumer side should be somehow associated with parameter values of the event. For example the document management system that stores employment contracts may have a metadata key value pair employee id 12388 associated with an MS Office Document file indicating that this is the contract between the company and Pat Rose from the example above .

There are many ways of how to tag the information. The way described above is good for document management systems e.g. EMC Documentum that contains semi structured information. If the data source is structured e.g. Training and Certification Management System the information is tagged by having a person identifier field in a database table. For example certifications of Pat Rose can reside in tpt certification table and person id field for all records related to Pat Rose will be set to 12388 .

For our purposes it doesn t matter how the information is tagged as long as one can retrieve and destroy the data related to the event from this data source.

In some embodiments of the present invention a retention schedule is a rule telling how long the document record piece of information should be retained in the data source retention time what the triggering event is after which the retention period starts to be counted and what needs to be done when the retention period is due.

For example the document must be DELETED 5 YEARS after EMPLOYEE TERMINATION or the document must be ARCHIVED 30 DAYS after DOCUMENT CREATION.

Note that triggering events may be related to the stored information itself DOCUMENT CREATION or to some external entity s lifecycle EMPLOYEE TERMINATION .

Retention schedules can be further subdivided into document types. For example retention schedule HR101 requiring documents to be stored for 5 years after employee termination may contain document type 401K and Incentive Stock Option Agreement . Document types may be hierarchical.

In some embodiments of the present invention Records are any pieces of information whose retention cycle we need to manage. This may be the Records as qualified by Records Management professionals or any other piece of information whose retention is worth being managed.

Users interact with ERM on the following stages. The detailed description of certain operations performed on these stages will be provided below 

There are a number of different ways to propagate disposition information between event producers the ERM system and event consumers according to the present invention. illustrates a schematic diagram of the business event propagation between an event producer and the ERM according to various embodiments of the present invention. The ERM is able to receive business events in a variety of ways. In some embodiments of the present invention a business event is Pushed from the event producer to the ERM via data path . According to some embodiments of the presents a business event Pulled by the ERM from the event producer via data path . Furthermore according to some other embodiments a user is able to make a manual entry of a business event through a graphical user interface to the ERM .

In some embodiments of the present invention the event producer is not necessarily a data driven application. For example it can be some issue tracking system where a human operator creates business events. For example employee termination according to the policy may require entering a service ticket into a BMC Remedy issue tracking system. Such a system can be integrated with ERM and serve as event producer .

In some embodiments of the present invention a push protocol is used to facilitate pushing business events from the event producer to the ERM . A multitude of push protocols can be used for pushing the data into ERM . For example the data can arrive though a SOAP Web Service request through mail server SMTP POP IMAP through any of emerging peer to peer instant messaging style protocols through native API call etc.

Likewise the data can be pulled from event producers through a multitude of pull protocol . In some embodiments of the present invention a standard pull protocol is designed for exchanging business events between event producers and the ERM . In some embodiments of the present invention event producer specific software modules are developed that allow for communication between ERM and disparate event producers .

In some embodiments of the present invention the pull protocol is defined in Connector API that is implemented by the data source Connector. When API calls must result in actions against the data source the Connector acts as a proxy that translates between standardized event driven disposition API calls messages understood by ERM and data source specific API calls messages understood by the event producer .

1. Configuration service exposed by the connector that tells ERM about connector capabilities and required interactions. Namely the configuration service response may contain 

2. Event service that in case of PULL model is called by ERM to retrieve events from the event producer. In case of PUSH model this service will be exposed by ERM and called by the connector.

Although highly desirable Configuration service is not a necessary part of a solution. It can be replaced by setting up the connector information though ERM user interface or through a configuration file uploaded by the user.

In yet other embodiments of the present invention a combination of one or more of these techniques are able to taken advantage to propagate business events between the event producer and the ERM .

According to some embodiments the event consumer connector is a proxy between ERM and Consumer. To perform disposition the Connector translates between standardized ERM side disposition requests initiated by ERM and local API calls messages understood by the event consumer data source. According to these embodiments each call contains a request and response. In request the connector translates a standardized API call to data source specific API call. In response the event consumer connector translates from data source specific API response to standardized API response. This connector will provide 

Although specific types of connectors are disclosed it will be apparent to those having ordinary skill in the art that any connector is available for use so long as they accomplish the desired communication. Likewise although the functionality between two Web Services is split between configuration and disposition a skilled practitioner having benefit of the disclosure will understand that the same functionality may be wrapped in different number of services and or services can have different names so long as they expose the same functionality. Configuration of Consumer parameters in ERM can be also achieved through ERM user interface or uploaded configuration files.

Event consumers have different capabilities when it comes to enforcing document disposition. For example there may be a website application that doesn t have a notion of data retention from which we want to delete a user account once the user closed his credit card or there may be a record management system RMS capable of performing document disposition for a given client account according to the retention policy stored by RMS once it received the client account termination event. The former type of event consumers will be called Simple the latter type will be called Retention capable .

For the sake of clarity let s call the signals coming from ERM to event consumers Disposition requests so we don t confuse them with events that always come from event producer.

Let s further subdivide disposition requests into Immediate Disposition Requests IDR and Scheduled Disposition Requests SDR . IDRs are used for communication with simple event consumers SEC and SDRs are used for communicating with retention capable event consumers REC .

Furthermore in some embodiments of the present invention simple event consumers can be converted into retention capable event consumers by implementing retention policy management logic inside the connector.

Event routing in the ERM is a major part of event driven disposition according to some embodiments of the present invention. Event routing refers to the propagation of events from event producers to event consumers. Event routing setup should answer the questions 

In some embodiments of the present invention the event producer and the event consumer are specifically designed with the ERM in mind. According to these embodiments event routing is easy since the parameters used by the event producer and the event consumer will be identical and the routes are obvious. However in typical application a route must be established for a business event originating in the event producer and propagated to the event consumer.

In the preferred embodiment of the present invention event routing is accomplished explicitly. In explicit routing the user manually identifies which business events need to be propagated from which event producers to which event consumers. In some embodiments of the present invention such identification is achieved by a polling step. However it will be readily apparent to those having ordinary skill in the art that other methods of routing exist. For example in some embodiments the routes between event producers and event consumers are automatically set up using known information about the data sources.

In some embodiments of the present invention event producers are polled by ERM through a Configuration Service. In response the Event Producers return the types of events that they produce. Likewise event consumers are polled by ERM through a Configuration Service exposed by event consumer connector to return the types of disposition requests they can consume as well as the type of event consumer simple vs. retention capable .

In some embodiments of the present invention the ERM Administrator establishes a route from event producers to event consumers manually by performing the following steps 

3. Choose one or multiple retention schedules or document types hosted by this event consumer that should be disposed of as a result of disposition request 

4. Associate information found in 1 2 and 3 together thus creating an instruction for ERM to forward events coming from a producer to a consumer within the context of a given retention schedule s or a given document type s .

In general names of the parameters coming from the event producer may differ from the names of the parameters required by event consumer when the disposition request is issued. Also not all the parameters coming with the event are needed for a disposition request. For example parameters first name and last name inside Employee terminated event coming from HR management system are not needed to dispose of email in the email archive. Only mailbox parameter is required.

Therefore there is a need in a configuration step when the Administrator maps parameters coming from the event producer to the parameters expected by event consumer inside a disposition request. As a result of such a mapping ERM forwards a value associated with a certain key in event to a certain parameter inside the disposition request.

For example a value user address.com mapped to email key in the employee disposition event coming from an HR management system will be forwarded to the parameter mailbox understood by Email archive connector inside the Delete email disposition request.

Referring again to once the system administrator is presented with the Configuration Application an instruction is sent to the Event Producers asking them about what events the Event Producers produce. The Event Producers report what events they produce to the Configuration Application . Likewise an instruction is sent to the Event Consumers asking them about what disposition requests they understand whether they are a retention capable consumer or conversely a simple consumer . The Event Consumers report this information to the Configuration Application . Next the system administrator facilitates parameter resolution where the capabilities of the Event Producers are matched with the Event Consumers and the parameters associated with the capabilities are resolved or mapped. Furthermore during the step of parameter resolution the retention schedules and or data types within the Event Consumer that are subject to disposition requests for certain business events are identified. Finally the resolved parameter data is stored in the ERM and a route is established in the ERM database .

Although a specific set of steps is disclosed it will be readily apparent to those having ordinary skill in the art that a number of different methodologies may be utilized to establish a route for disposition request from event producers to event consumers.

For example in some embodiments of the present invention the Configuration Service call to the Event Producers and the Event Consumers occurs once during the ERM setup stage as opposed to the Routing Configuration stage.

According to the present invention there are a number of ways to enhance the user interface available to an ERM administrator. Some of the selected options are as follows 

Furthermore there exist numerous other interface enhancements which will become obvious to those having ordinary skill in the art who have the benefit of this disclosure.

In some embodiments of the present invention the ERM maintains a notion of event categories to categorize the types of business events that are used in retention schedules and are traveling from event producers to event consumers.

Event categories can be organized as a hierarchy or as a flat list. The values in the list or leaves in the hierarchical tree are actual event types that must be specified when the user creates a retention schedule.

The nodes in the event hierarchy are event categories groups of similar events. For example an event type is Employee terminated and an event category is Employee related . illustrates a schematic representation of a portion of one possible event category hierarchy according to some embodiments of the present invention. As shown two types of events within the hierarchy are employee related and vendor related . Within the employee related branch two types of events are listed employee terminated and employee transferred . Likewise under the vendor related branch a number of vendor related events are shown.

Of course the routing method described above doesn t require event categorization or even a notion of event types in ERM to operate. Once Administrator connected an event type on an event producer side to a disposition request type on event consumer side ERM gets sufficient information to perform routing. However event categorization by ERM may be necessary for reporting setup and management purposes. For example user may want to see the list of disposition requests caused by employee related events.

Note that event types exposed by event producer connector s Configuration service may not necessarily match the event types setup in ERM. Likewise disposition request types exposed by event consumer connector s Configuration service may not necessarily match the event types setup in ERM.

Therefore during the configuration of event producers and event consumers Administrator must be able to associate event types exposed by connectors to the event types known to ERM. As a result of that users will be able to use event categories and types known by ERM for search and reporting purposes or even trigger some business logic based on event type information.

Event categorization allows for streamlining the process of setting up the route. Since both event types exposed by event producers and disposition requests exposed by event consumers are mapped to event types in ERM event category hierarchy once the administrator chose a business event type inside an event producer ERM can prompt the Administrator about all the event consumers that expose disposition requests associated with the same event type or category as the selected business event type.

In some embodiments of the present invention events need to be propagated to a consumer only when a certain condition is true. For example user email can be stored in multiple email archives. For example email coming to from Registered Brokers in an investment bank may be segregated from emails sent received by the rest of the employees.

Within an ERM this may be represented as multiple routes from a Human Resource Management system to multiple archives each containing conditional logic a Filter Application that allows routing of events to a particular archive only for the users who belong to a proper employee category.

A Filter Application is an application that performs some actions based on values of parameters contained inside incoming business events and makes the decision whether the event should be resolved into a disposition request.

Consider the example of a Human Resource Management System HRMS being used with the ERM. The HRMS is set up for a business having two types of employees normal employees and Registered Brokers. The HRMS also comprises an Event Source that deals with Employee Termination. Using this example suppose that regulations require that trading transaction records must be kept about Registered Brokers and their activities in a record management system.

Likewise the ERM is coupled with a Data Source comprising a record management system which contains all the records for the Registered Brokers. According to the present invention the ERM propagates disposition requests to the record management system when an appropriate business event occurs. For example when an employee is terminated the ERM will forward a disposition request to the record management system. However it is preferable to provide a Filter Application such that the ERM will only propagate the request if the employee is a Registered Broker.

Therefore according to some embodiments of the present invention a Filter Application is provided that is programmed with conditional logic that will determine whether the disposition request relates to a Registered Broker.

In some embodiments of the present invention the Filter Application is implemented as a stand alone application. In some other embodiments of the present invention the Filter Application resides inside the ERM in the form of custom code that is injected in the ERM. In some embodiments the custom code is written by implementation consultants in an interpreted scripting language such as BeanShell.

In some embodiments of the present invention the Filter applications are declared in ERM during the setup step. When an Administrator establishes a route she associates the incoming event with a filter application.

According to these embodiments when the Administrator attaches a filter application to the event she maps event parameters to input parameters declared by the filter application so ERM knows which parameters from the incoming event should be forwarded to which input parameters in the filter application.

In some embodiments of the present invention filter applications all have a common interface which accepts a number of input parameters and returns single value telling ERM whether to proceed with the disposition request.

In other embodiments when the Filter Application is a stand alone application the types of input parameters it requires are obtained by ERM via a Configuration Service exposed by the Filter Application.

In yet other embodiments injected Filter Application may declare their input parameters types through a pre agreed application programming interface. Also this can be achieved through user interface or configuration file.

Described above are producer connectors consumer connectors filter applications and parameter resolvers. In some embodiments of the present invention process of describing and or self describing the capabilities of the applications and or connectors is accomplished via the same mechanisms selected from among a configuration service a user interface a configuration file an Application programming interface API call and combinations thereof. In other embodiments multiple mechanisms are separately utilized for the describing and or self describing of the producer connectors consumer connectors filter applications and parameter resolvers.

Sometimes there is not enough information inside the business event for a particular Event Consumer to perform a disposition. As a result ERM needs to find this information elsewhere before compiling the disposition request. A typical situation is a global user ID that is not stored in HR management system but used in other applications that store information about users.

ERM should be able to find this information using external applications. After this information is found it should be added to the event parameters so that it can be forwarded to the disposition request.

Parameter resolution can be done by calling a Parameter Resolver application which is an external application responsible for deriving missing parameters based on information provided in business event. Alternatively this application may reside inside ERM in a form of custom code most likely written by implementation consultants in an interpreted scripting language such as BeanShell that can be injected into ERM.

Resolvers must be declared in ERM during setup. When Administrator tries to establish a route she needs to be able to associate the incoming event with a resolver application. Once the event is associated it will appear as if it has more event parameters those coming originally from the event and those coming from the resolver .

When Administrator attaches the resolver to the event she needs to map event parameters to input parameters of the resolver so ERM knows which parameters from the incoming event should be forwarded to which input parameters in the resolver.

All resolvers must have the same interface that accepts multiple input parameters and returns multiple output parameters both names and values .

In some embodiments resolvers declare the parameters they accept through the same mechanism as the Filter Application i.e. a Configuration Service or a predefined API .

In some embodiments of the present invention the parameters for a set of Event Consumers and a set of Event Producers are resolved automatically.

Routes can be established after event produces already issued some events. ERM can either propagate only the events that entered ERM or occurred after the route has been established or it can also propagate old events to the newly established route.

This behavior can also be dynamically configured on the application level and will apply to all the routes created afterwards. Or it can be decided during the route setup by offering the user to propagate old events and even allowing her to choose particular events that need to be propagated.

The Structure of a Disposition Request When It Comes to Passing Retention Schedule Information to Event Consumers

The architecture of event driven disposition may either require ERM to pass a reference to a retention schedule and document type to event consumers or may allow it as an option or may require the entire retention schedule object to be sent or may not allow this possibility at all. Some possible scenarios of propagating retention schedules are presented below 

In this architecture when a disposition request is created it is always associated to an intersection of event consumer and retention schedule s or document types s . In a body of disposition request the consumer always receives the following information 

When such a request comes to the event consumer the event consumer should be able to locate the records based on some retention schedule IDs or retention schedule document type IDs.

Note that in such architecture event consumer is expected to expose a single disposition request type that will receive retention schedule ID as a parameter along with other parameters of the disposition request.

In this architecture instead of accepting a retention schedule ID as a parameter the consumer s connector can just expose multiple disposition event types one per retention schedule.

Likewise the ERM expose three disposition request types wherein each doesn t require retention schedule ID as a parameter because each is mapped to a single retention schedule by design of the connector.

The latter approach gives a few benefits 1. Disposition event types are easier to categorize and browse in ERM 2. There is no problem with optional parameters.

In the former approach all parameters except retention schedule id were optional but they became required depending on the value of retention schedule ID chosen. Such logic is harder to define in configuration service and harder to implement. In this approach parameters are highly relevant to the disposition request type and easy to understand by Administrator during setup. However for certain types of consumers such as Record Management Systems capable of being setup at runtime to manage multiple retention schedules such architecture may become suboptimal from the software design standpoint because clients will have to modify the connector code each time a new document type is added to the record management system.

In some scenarios it still makes sense to provide retention schedule and document type IDs during the disposition request call. For example the event consumer that stores various types of contracts may expose two disposition request types one for HR documents requiring person id as a parameter another one for client documents requiring client ID as a parameter.

However inside HR document disposition request the connector may require the document type ID so it can distinguish between 401K and Employment contracts. Obviously such a connector can be re designed to expose two HR related disposition requests but it might make more sense to provide retention information as an argument in this particular scenario.

In this architecture connector can specify in the response to Configuration service request whether it needs retention schedule or document type information as an argument for a particular type of disposition request.

In this architecture the entire retention schedule object not only id is passed to the connector during the disposition request. In spite of higher network traffic requirements this may be a valid option because it does not require a retention capable event consumer to know anything upfront about the retention schedules it needs to enforce.

The flipside of this solution is problems with change propagation when retention schedule parameters such as retention period have changed after the disposition request has been communicated to the connector.

The ERM of the present invention makes it feasible to implement event driven disposition on an enterprise scale and cuts the cost of disposition by reducing the headcount needed for performing the disposition. Furthermore the ERM of the present invention increases the accuracy of disposition through reducing the dependency on human factor. This may result in less legal costs.

Furthermore the ERM of the present invention provides standardized protocols for event producers to communicate the events and event consumers to receive disposition requests thus allowing information system vendors to build event disposition functionality into their products upfront. The proposed method makes it possible to automate disposition for both retention policy capable event consumers that can count the retention period and trigger disposition in future and simple event consumers that can only perform immediate disposition.

Furthermore the ERM of the present invention may become a retention policy enforcement layer for the data sources that are otherwise not capable of executing data disposition based on retention policy information.

The present invention has been described in terms of specific embodiments incorporating details to facilitate the understanding of the principles of construction and operation of the invention. Such reference herein to specific embodiments and details thereof is not intended to limit the scope of the claims appended hereto. It will be apparent to those skilled in the art that modifications can be made in the embodiment chosen for illustration without departing from the spirit and scope of the invention. Specifically it will be apparent to one of ordinary skill in the art that the device and method of the present invention could be implemented in several different ways and have several different appearances.

