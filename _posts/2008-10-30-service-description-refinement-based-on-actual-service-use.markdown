---

title: Service description refinement based on actual service use
abstract: Techniques are disclosed for generation and refinement of service descriptions based on records of invocations of the services, i.e., service description refinement based on actual service use. For example, a method for describing one or more services in a service-oriented environment comprised of one or more clients invoking the one or more services comprises the following steps. An initial description is established for at least one of the one or more services. Information is collected from one or more service invocations including at least one of a client identity, a value of at least one parameter, a return value, and an execution time. The information is analyzed to refine the description.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08341212&OS=08341212&RS=08341212
owner: International Business Machines Corporation
number: 08341212
owner_city: Armonk
owner_country: US
publication_date: 20081030
---
The present invention relates generally to the automatic description of software artifacts and more particularly relates to the generation and refinement of service descriptions based on records of invocations of the services.

A situational enterprise service is a relatively small primarily browser based intranet scale situational application. In turn a situational application is software created for a small group of users with specific needs. The application typically has a short life span and is often created within the group where it is used sometimes by the users themselves. As the requirements of a small team using the application change the situational application often also continues to evolve to accommodate these changes. Significant changes in requirements may lead to an abandonment of the situational application altogether in some cases it is just easier to develop a new one than to evolve the one in use.

Illustrative embodiments of the invention provide techniques for generation and refinement of service descriptions based on records of invocations of the services i.e. service description refinement based on actual service use. While not limited thereto such techniques are particularly suitable for use with situational enterprise service descriptions.

For example in one embodiment a method for describing one or more services in a service oriented environment comprised of one or more clients invoking the one or more services comprises the following steps. An initial description is established for at least one of the one or more services. Information is collected from one or more service invocations comprising at least one of a client identity a value of at least one parameter a return value and an execution time. The information is analyzed to refine the description.

In another embodiment a method for describing one or more services in a service oriented environment comprised of one or more clients invoking the one or more services comprises the following steps. An initial description is established for at least one of the one or more services. Information is collected from one or more service invocations comprising at least one of a client identity a value of at least one parameter a return value and an execution time by adaptively varying a collection procedure to balance an accuracy of information and system performance. The information is analyzed to refine the description. A classification scheme of tags is derived for classifying services in a hierarchy based on the information. The hierarchy is adaptively modified based on the information.

These and other objects features and advantages of the present invention will become apparent from the following detailed description of illustrative embodiments thereof which is to be read in connection with the accompanying drawings.

While illustrative embodiments will be described herein in the context of situational enterprise service descriptions it is to be understood that principles of the invention are not so limited and are more generally applicable to other appropriate services.

A situational enterprise service typically exposes a REST Representational State Transfer interface through which it is invoked. REST builds on HTTP HyperText Transfer Protocol principles to define a software architectural style where entities containers and behaviors can be seen as resources that are accessible via a uniform interface comprised of a fixed set of verbs. REST was first introduced by Roy T. Fielding in a doctoral dissertation Architectural Styles and the Design of Network based Software Architectures University of California Irvine 2000 the disclosure of which is incorporated by reference herein in its entirety.

More specifically a situational enterprise service does not use a rigorous language such as WSDL Web Services Description Language to define its interface. Thus a formal interface is not required to be defined for a situational enterprise service. Rather informal mechanisms such as a RESTful documentation are used to describe a situational enterprise service.

The RESTful documentation of the interface exposed by a situational enterprise service is a stylized syntactic description of the REST resources exposed by the situational enterprise service. For each resource this description includes information about the data formats of its methods success and error codes as well as typical examples of request and response. One representative example of RESTful documentation is given by Project Zero s RESTdoc tool IBM Corporation Armonk N.Y. .

A situational enterprise service is also typically annotated with tags for the purposes of content sharing and collaborative filtering. Moreover tags are used as a form of informal semantic description of situational enterprise services.

Complete and reliable descriptions are a pre requisite for the discovery of suitable situational enterprise services. On the other hand it is possible for such descriptions to be incomplete since formal interfaces are not required for situational enterprise services.

However we have realized that it is feasible to infer the various items of RESTful documentation e.g. format parameters by example from successful as well as unsuccessful invocations of a situational enterprise service. In other words given a log of service invocations that include the URL Uniform Resource Locator of the service invocation method format parameter values and success or error codes it is feasible to synthesize the RESTful documentation of a situational enterprise service.

Principles of the present invention thus provide a method for automatic description of software artifacts. In particular principles of the present invention provide a method for the generation and refinement of situational enterprise service descriptions based on records of invocations of the situational enterprise services henceforth referred to as service or services. 

In one embodiment shows a system having features of the present invention. At least one service developer writes at least one service . Services are hosted by at least one service host . At least one service user invokes at least one service hosted on at least one service host . Service users are sometimes referred to as clients.

Service descriptions are critically important for service users to determine which services to invoke. Principles of the invention provide methods for a system to automatically improve and refine service descriptions based on run time information. A service may comprise one or more computer programs. The run time information collected by our system may include but is not limited to information about services invoked by service users one or more parameters passed to a service whether the service fails the time for the service to execute a value returned by a service identity of a service user etc.

In the hosted service environment illustrated in a service manager receives service invocations from service users . The service manager forwards a given invocation to the corresponding service . After the invocation of the service has completed and a response is available the service manager forwards a request response pair corresponding to the invocation to a service description refinement component that is the focus of the invention. The service host also includes a bookmark store and a service description store .

The bookmark store contains bookmarks that refer to services and that are annotated with tags. A bookmark includes the URL of the referred service. Thus it is possible to retrieve all bookmarks that refer to a service given the service s URL.

The description store contains the descriptions of services that have been created or refined by the system in accordance to the invention. A service description includes a syntactic description and a semantic description.

In a preferred embodiment of the invention the syntactic description of a service is expressed as a RESTdoc document. In turn the XML eXtensible Markup Language representation of RESTdoc that is targeted by the invention is given by the following instance schema 

In a preferred embodiment of the invention the semantic description of a service is given by the collection of all tags that may annotate the service. This collection includes tags that may have been directly associated with the service at development or deployment time. We refer to these tags as the immediate tags of the service. This collection also includes any tags that are associated with any bookmark that may refer to the service. We refer to these tags as the bookmark tags of the service.

Referring to the service description refinement component is comprised of 1 a service monitor 2 an invocation log 3 a log processor and 4 a description refiner .

The service monitor receives a service invocation from the service manager as a request response pair that it converts into an invocation log record. In a preferred embodiment the service monitor writes invocation log records to the invocation log directly. The request response pair that the service monitor receives is given by a pair of data structures which are accessible via the following interfaces 

The service monitor takes a pair of request response data structures and converts it into a log record with at least the following contents and writes it to the invocation log 

The log processor is a component that executes in a thread separate from the service monitor . The log processor reads log records in order from the invocation log and invokes the description refiner with each log record.

The description refiner takes an invocation log record and uses it to generate or refine the description of a service. Optionally if a description already exists for a service in the description store as determined by the resource URL of the service as conveyed by the invocation log record then the description refiner reads the service description from the description store and in this case it uses the invocation log record to refine the description of the service. Otherwise the description refiner uses the invocation log record to generate the description of the service.

It is also to be appreciated that service descriptions can be further refined based on information provided by a service developer or service user.

In step the system analyzes the information collected in step . In step the service description is refined based on this analysis note that steps and can be combined into a single step . For example if a service tends to fail frequently this can be included in the service description. If it almost never fails this can also be included in the service description. If certain types of service users also known as clients constitute frequent users of the system this can be added to the service description. Performance information about the service as well as parameters the service is invoked with can be included in the service description.

Steps and can be performed in a loop to continuously refine service descriptions. The steps do not have to be performed discretely in a particular order. For example the system could continuously perform monitoring to collect information. Analysis of the information and service refinement could also be a continuous process.

A key aspect of the invention is that service users can use service descriptions to determine which services to invoke. The descriptions can also be used to develop a classification scheme for services . For example a classification scheme based on tags could be used. The tags could be arranged in a hierarchical fashion. A service could have one or more tags associated with it. The tag hierarchy can be adaptively modified based on the information collected in step .

As depicted in if the source service is known as determined by a client identifier in the log record then the description refiner performs both semantic as well as syntactic description refinement . Otherwise the description refiner performs only syntactic description refinement . Syntactic description refinement is depicted in while semantic description refinement is depicted in .

Referring to the syntactic description refinement first determines if a description already exists for the service referred to by the invocation log record . If this is the not case then an empty description is first created and it uses the items in the invocation log record to populate the description . Each item in the invocation record is added to the syntactic description of the service in accordance with the algorithm in . If a description already exists for the service referred to by the invocation log record then for each item in the invocation log record it is determined whether the syntactic description contains the item . If this is not the case then the item is added to the syntactic description of the service in accordance with the algorithm in . If the syntactic description does contain the item then the item is merged into the syntactic description of the service in accordance with the algorithm in .

Referring to adding an invocation log record item to the syntactic description of a service first determines whether the item to be added is enumerable . In a preferred embodiment an item is enumerable if the number of values it can have is small enough typically O 100 that it is reasonable to collect each individual value as part of the service description. An example of an enumerable item is the format of the invocation request or response or the success or error code of the invocation. An example of a non enumerable item is a request parameter value or a response value. For instance this could be a value of some primitive data type such as a string or a non primitive data typed value such as a JSON JavaScript Object Notation object.

If the item to be added is enumerable then a list for the corresponding item is created in the description of the service and the item value is added to the list .

If the item to be added is not enumerable then a representative schema of any of its values is created for the item in the service description using the item value as a prototype . For example suppose that the following JSON object is the value of the response value in the invocation log record under consideration 

In turn a concise format of this schema referred to as instance schema that would be used for display purposes is as follows 

Any JSON schema that is created in accordance to the invention is intended to follow the rules set forth in the JSON Schema Proposal see JSON Schema Proposal. http groups.google.com group json schema web json schema proposal second draft September 2008 the disclosure of which is incorporated by reference herein in its entirety .

Referring to merging an invocation log record item to the syntactic description of a service first determines whether the item to be merged is enumerable . If the item is enumerable and if the list for the item in the description does not already contain the item value then the item value is added to the list .

If the item to be merged is not enumerable then the schema corresponding to this item in the service description is refined by augmenting it to cover this item value in addition to the set of values it already covers . For example suppose that the following JSON object is the response value of a subsequent invocation log record for the same service 

Notice that since the removedmembers property only appears in the second value then the schema learns it as optional. In turn the concise format of this schema or instance schema that would be used for display purposes becomes 

Referring to the semantic description refinement performs the steps of 1 collecting all tags associated with the source service 2 filtering out not similar enough tags and 3 adding the remaining tags to the target service s description .

To collect the tags associated with a service in particular the source service all bookmarks that may refer to the service are retrieved. In a preferred embodiment retrieval of the bookmarks referring to a service uses the URL of the service to lookup all bookmarks that include said URL. The collection of tags associated with a service is then comprised of the service s immediate tags and the service s bookmark tags. That is the collection contains the tags that may have been directly associated with the service at development or deployment time as well as all the tags in any bookmark that refers to the service.

To filter out tags the term not similar enough is defined with respect to some measure of similarity. In a preferred embodiment the measure of similarity used is a function of semantic distance as given by the lexical meaning of a tag in a public lexical database such as WordNet. More specifically as explained for example in S. Zhao N. Du A. Nauerz X. Zhang Q. Yuan and R. Fu Improved Recommendation based on Collaborative Tagging Behaviors In Proceedings of the International ACM Conference on Intelligent User Interfaces IUI2008 Canary Islands Spain 2008 the disclosure of which is incorporated by reference herein in its entirety the similarity of two tags is inversely proportional to the WordNet distance between the two tags where the WordNet distance is the shortest path length between the meanings of the two tags. If the semantic distance between a source tag and a target tag is greater than some configurable value we say that the source tag is not similar enough to the target tag and we filter out the source tag. Filtering out not similar enough tags takes each tag from the collection of tags associated with the source service and compares it with all tags in the collection of tags associated with the target service.

A source tag that is similar enough is added to the target service s description by 1 determining that it does not already exist in the collection of tags associated with the target service and 2 adding the source tag to the target s collection.

In an example of classification a classification scheme could be used that is based on at least one parameter used in the invocation of the service. The actual parameter to be used could be indicated by a user or a tool. If the parameter to be used is enumerable as defined previously for instance request format then services could be classified into an enumeration of categories one category per parameter value. For instance if a request format parameter can take values JSON and XML then services that use request format as a parameter could be classified into either a JSON category or an XML category. If the parameter to be used is not enumerable for instance a request parameter value then services could be classified based on whether the corresponding instance schemas for the given parameter value are similar for some definition of instance schema similarity. From our previous example suppose that service A returns the following JSON object as its response value 

Lastly illustrates a computer system in accordance with which one or more components steps of the techniques of the invention may be implemented. It is to be further understood that the individual components steps may be implemented on one such computer system or on more than one such computer system. In the case of an implementation on a distributed computing system the individual computer systems and or devices may be connected via a suitable network e.g. the Internet or World Wide Web. However the system may be realized via private or local networks. In any case the invention is not limited to any particular network.

Thus the computer system shown in may represent one or more service developers one or more service hosts one or more service users one or more servers or one or more other processing devices capable of providing all or portions of the functions described herein. In one particular example the computer system of is used to implement service description refinement component and its constituent components .

The computer system may generally include a processor memory input output I O devices and network interface coupled via a computer bus or alternate connection arrangement.

It is to be appreciated that the term processor as used herein is intended to include any processing device such as for example one that includes a CPU and or other processing circuitry. It is also to be understood that the term processor may refer to more than one processing device and that various elements associated with a processing device may be shared by other processing devices.

The term memory as used herein is intended to include memory associated with a processor or CPU such as for example RAM ROM a fixed memory device e.g. hard disk drive a removable memory device e.g. diskette flash memory etc. The memory may be considered a computer readable storage medium.

In addition the phrase input output devices or I O devices as used herein is intended to include for example one or more input devices e.g. keyboard mouse etc. for entering data to the processing unit and or one or more output devices e.g. display etc. for presenting results associated with the processing unit.

Still further the phrase network interface as used herein is intended to include for example one or more transceivers to permit the computer system to communicate with another computer system via an appropriate communications protocol.

Accordingly software components including instructions or code for performing the methodologies described herein may be stored in one or more of the associated memory devices e.g. ROM fixed or removable memory and when ready to be utilized loaded in part or in whole e.g. into RAM and executed by a CPU.

In any case it is to be appreciated that the techniques of the invention described herein and shown in the appended figures may be implemented in various forms of hardware software or combinations thereof e.g. one or more operatively programmed general purpose digital computers with associated memory implementation specific integrated circuit s functional circuitry etc. Given the techniques of the invention provided herein one of ordinary skill in the art will be able to contemplate other implementations of the techniques of the invention.

Although illustrative embodiments of the present invention have been described herein with reference to the accompanying drawings it is to be understood that the invention is not limited to those precise embodiments and that various other changes and modifications may be made by one skilled in the art without departing from the scope or spirit of the invention.

