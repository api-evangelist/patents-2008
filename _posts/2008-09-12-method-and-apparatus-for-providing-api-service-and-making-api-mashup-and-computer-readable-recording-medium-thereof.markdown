---

title: Method and apparatus for providing API service and making API mash-up, and computer readable recording medium thereof
abstract: The present invention provides an open application program interface (API) service. A method of providing the API service includes generating meta-data for executing an API, generating resource data for generating a mash-up of the API, generating description data corresponding to the API, the meta-data, and the resource data, and generating an API package comprising the API, the meta-data, the resource data, and the description data. Accordingly, mash-up contents can be easily generated from various types of APIs.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08549471&OS=08549471&RS=08549471
owner: Samsung Electronics Co., Ltd.
number: 08549471
owner_city: Suwon-si
owner_country: KR
publication_date: 20080912
---
This application claims priority from Korean Patent Application No. 10 2007 0131081 filed on Dec. 14 2007 in the Korean Intellectual Property Office the disclosure of which is incorporated herein in its entirety by reference.

Method and apparatus consistent with the present invention relate to an open application program interface API service and more particularly to a method and apparatus for providing an API service and generating an API mash up and a computer readable recording medium having embodied thereon a program for executing the method.

A mash up service is a technology producing a new API by putting two or more APIs together in a web. The mash up service has advantages in that efforts for realizing a new service are reduced by using an established opened API and in that utility of the established opened API can be maximized.

Referring to firstly a mash up developer plans to produce a particular kind of mash up Operation . Then the mash up developer searches and selects open APIs Operation and Operation that should be used to produce the mash up Operation . If the mash up developer decides to produce a mash up service by using a Google map open API and a Flickr open API the mash up developer analyzes the Google map open API and the Flickr open API and grasps characteristics for example communication protocol data format and input output data format of the open API services Operation . An open API service provider generates user account information Operation and Operation or a user certification key Operation and provides them to the mash up developer.

The mash up developer secures the open APIs embodies a mash up function with reference to manuals provided by open API service providers and determines a layout of a HTML page to complete final mash up contents Operation . Accordingly the mash up developer should take charge of works related to an embodiment of a mash up such as a communication protocol and data format conversion. In particular since a method of providing open API services varies according to the open API service providers firstly the mash up developer should analyze various open API services and learn the related technologies and the mash up depends on the mash up developer s ability.

Also since codes or scripts related to the open APIs consisting of the mash up are made by the mash up developer at his or her discretion it is difficult to renew the open APIs consisting of the mash up or to add a new open API to the established mash up.

Exemplary embodiments of the present invention overcome the above disadvantages and other disadvantages not described above. Also the present invention is not required to overcome the disadvantages described above and an exemplary embodiment of the present invention may not overcome any of the problems described above.

The present invention provides a method and apparatus for providing an application program interface API service and producing an API mash up and a computer readable recording medium used to easily produce mash up contents from various types of APIs.

The present invention also provides a method and apparatus for providing an API service and producing an API mash up and a computer readable recording medium used to easily update mash up contents comprising various types of APIs.

According to an aspect of the present invention there is provided a method of providing an application program interface API service the method including generating meta data for executing an API generating resource data for generating a mash up of the API generating description data corresponding to the API the meta data and the resource data and generating an API package comprising the API the meta data the resource data and the description data.

The method may further include transmitting the API package to a package providing server or an apparatus for producing the API mash up.

The meta data may include information about a communication protocol to communicate with the package providing server or the apparatus for producing the API mash up and information about a data format of the API.

The meta data may further include user account information or a user certification key for using the API.

The resource data may include a configuration data of a user interface to generate the mash up and a tagging information representing an input output data format of the API.

The resource data may further include information about an icon or a thumb nail for executing the mash up of the API in the user interface.

The description data may include information about one of components of the API package a version of the API and a library function for executing the API.

According to another aspect of the present invention there is provided a method of generating an API mash up the method including obtaining at least two API packages which respectively includes an API meta data for executing the API resource data for generating a mash up of the API and description data corresponding to the API the meta data and the resource data extracting the API the meta data and the resource data from each of the at least two API packages by using the description data and generating a mash up of the at least two API packages by using the API the meta data and the resource data.

The generating the mash up of the at least two API packages may include analyzing an input output data format of the API searching another API package to perform the mash up with the at least two API packages selectively on the basis of the input output data format of the API and generating the mash up by using the at least two API packages and another API package.

The method may further include replacing one of the at least two API packages in the mash up to another API package.

According to another aspect of the present invention there is provided an apparatus for providing an API service the apparatus including a meta data generating unit which generates meta data for executing an API a resource data generating unit which generates resource data for generating a mash up of the API a description data generating unit which generates description data corresponding to the API the meta data and the resource data and an API package generating unit which generates an API package comprising the API the meta data the resource data and the description data.

According to another aspect of the present invention there is provided an apparatus for producing an API mash up the apparatus including an API package obtaining unit which obtains at least two API packages which respectively comprise an API meta data for executing the API resource data for generating a mash up of the API and description data corresponding to the API the meta data and the resource data a data extracting unit which extracts the API the meta data and the resource data from each of the API packages by using the description data and a mash up generating unit which generates a mash up of the API packages by using the API the meta data and the resource data.

The apparatus may further include a package download unit which downloads the API packages from a service provider or a server of a specified location and a storing unit which stores the downloaded API packages.

According to another aspect of the present invention there is provided a computer readable recording medium having embodied thereon a program for executing a method of providing an API service the method including generating meta data for executing an API generating resource data for generating a mash up of the API generating description data corresponding to the API the meta data and the resource data and generating an API package comprising the API the meta data the resource data and the description data.

According to another aspect of the present invention there is provided a computer readable recording medium having embodied thereon a program for executing a method of producing an API mash up the method including obtaining at least two API packages which respectively comprise an API meta data for executing the API resource data for generating a mash up of the API and description data corresponding to the API the meta data and the resource data extracting the API the meta data and the resource data from each of the at least two API packages by using the description data and generating a mash up of the at least two API packages by using the API the meta data and the resource data.

According to another aspect of the present invention there is provided a method of generating an Application Program Interface API mash up the method includes obtaining at least two API packages extracting data from each of the at least two API packages and generating a mash up of the at least two API packages by using the extracted data.

The extracted data may include an API meta data for executing the API resource data for generating a mash up of the API and description data corresponding to the API the meta data and the resource data.

Each of the at least two API packages may include an API meta data resource data and description data corresponding to the API the meta data and the resource data.

Exemplary embodiments of the present invention will now be described in detail with reference to the appended drawings.

Referring to an API package according to an exemplary embodiment the present invention includes meta data resource data an API and description data . The API package which provides API services to an apparatus for producing an API mash up is used to provide information related to an API necessary to produce the mash up in a standardized format.

The meta data includes information necessary to execute the API . The meta data includes communication protocol information used to send data to an API service provider and receive data from the API service provider as a representative example and data format information used to input and output data of the API . The API service provider transmits its own API to the apparatus for producing the API mash up to be described later through a package providing server or transmits it directly. Accordingly the meta data should include the communication protocol information and the data format information that are transmitted to from the package providing server or the apparatus for producing the API mash up. The communication protocol may be JavaScript representational state transfer REST simple object access protocol SOAP and the like and the data format may be XML JSON PHP or the like.

The meta data may further include additional information such as user account information or a user certification key used to provide API services that are specialized according to users so that a mash up developer can use the API.

The resource data is used to produce a mash up of the API . For example the resource data can be used to provide a user interface for producing the mash up. The resource data includes configuration data of the user interface or tagging information representing input output data format of the API .

For example the configuration data includes information about a language a resolution a zoom and the like that are applied to the user interface.

The tagging information represents input output data format of the API . For example if the mash up developer uses a Google map open API the input data format and the output data format may be respectively a specified location and a set of coordinates. On the other hand if the mash up developer uses a Flickr open API the input data format and the output data format may be respectively the name of a place and an image.

Therefore in the case of the Google map open API the tagging information can be defined in a standardized format for example input location and output coordinates . This is for defining pairs of an input and output of the API with tags because functions of each API are different. Also a plurality of pieces of tagging information can be input.

The resource data may include information about icons or thumb nails for executing a mash up of the corresponding API in a user interface for producing a mash up.

The API which is an entity of an API service includes exemplary embodiments for substituting for arbitrary codes or scripts produced by the mash up developer. The API may be specialized according to development languages such as C or Java and may take the form of an API wrapper based on an extensible markup language XML .

However the API may not only be an open API but also a local API. The local API is not allowed to be used by anybody as is the case with the open API and is only allowed to be used by a special apparatus or a special person. For example the local API is allowed to be used in a cellular phone of A brand and the mash up developer that is a user of the cellular phone can produce the mash up by putting the local API and the open API together or by putting the local API and another local API together. In other words the local API which is a peculiar API package included in an apparatus may be installed inside the apparatus as a standardized package at the time of apparatus development.

The description data includes detailed information about the API the meta data and the resource data . An apparatus for producing an API mash up to be described later can obtain detailed information about the API package through the description data . For example the description data may include components of the API a version of the API a library function necessary to execute the API and details about the meta data or the resource data etc. For example the description data may be generated by an XML.

The above described API package is generated by an API service provider and can be transmitted to the apparatus for producing the API mash up through the package providing server or can be transmitted directly.

Referring to the apparatus for providing the API service includes a meta data generating unit a resource data generating unit a description data generating unit and an API package generating unit .

The meta data generating unit generates meta data for executing the API . The meta data includes information necessary to execute the API . The meta data is transmitted to the API package generating unit .

The resource data generating unit generates resource data for generating a mash up of the API . The resource data is transmitted to the API package generating unit .

The description data generating unit generates description data including detailed information about the meta data transmitted from the API and the meta data generating unit and about the resource data transmitted from the resource data generating unit .

The API package generating unit inputs the meta data that is outputted from the API and the meta data generating unit the resource data that is outputted from the resource data generating unit and the description data that is outputted from the description data generating unit and generates and outputs an API package including those items of data.

Referring to the apparatus for producing the API mash up includes an API package obtaining unit a data extracting unit and a mash up generating unit .

The apparatus for producing the API mash up generates a mash up using the API package received directly or through a package providing server from the apparatus for providing the API service of .

The API package obtaining unit obtains a plurality of API packages received directly or through the package providing server from the apparatus for providing the API service of . For example if the API package obtaining unit obtains a map service of Google an image sharing service of Yahoo and a third service of a third subject the API package obtaining unit can receive a standardized API package provided by each service provider through a specified package providing server or can directly receive the standardized API package provided by each service provider from the apparatus for providing the API service.

As described above each of the API packages includes an API meta data resource data and description data.

The data extracting unit extracts the API the meta data and the resource data from each of the API packages by using information included in the description data.

The mash up generating unit generates a mash up of the API packages by using the API the meta data and the resource data. Since information necessary to generate the mash up is included in the meta data the mash up generating unit can use the information.

The mash up generating unit can determine an input output data format between API services and can determine a method of communicating with a server by using information about the provided communication protocol or data format.

The mash up generating unit realizes a user interface by using the resource data and reflects the API package in mash up contents according to directions input from a user on the basis of the user interface so that different user interfaces can be produced for one mash up. The mash up generating unit can have the same effect as a process in which a developer adds codes on the basis of the user interface and can reflect necessary information from the resource data and the API.

A package download unit downloads an API package from a service provider or a server of a specified location according to a request of a mash up generating unit .

A storing unit stores API packages that is an open API package and a local API package downloaded by the package download unit from a service provider . Also the storing unit stores mash up contents generated by the mash up generating unit .

A data extracting unit extracts API meta data resource data and description data from the API package. Each of the extracted data is transmitted to the mash up generating unit .

The mash up generating unit generates mash ups of the API packages by using the API the meta data and the resource data. When another API package is required besides the API packages downloaded from the package download unit in order to generate the mash up the mash up generating unit requests the package download unit to download the corresponding API package. An example of the case in which another API package is required will be described later.

Referring to an apparatus for providing an API service generates meta data for executing an API Operation . The API may be an open API or a local API. The meta data includes information about a communication protocol to communicate with a package providing server or an apparatus for producing the API mash up and information about a data format of the API. The meta data may further include user account information or a user certification key for using the API.

The apparatus for providing the API service generates resource data for generating a mash up of the API Operation . The resource data comprises a configuration data of a user interface to generate the mash up and a tagging information representing an input output data format of the API The resource data may further include information about an icon or a thumb nail for executing a mash up of an API in the user interface.

The apparatus for providing the API service generates description data regarding the API the meta data and the resource data Operation . For example the description data may include information about components of an API package a version of the API or a library function for executing the API.

The apparatus for providing the API service generates an API package comprising the API the meta data the resource data and the description data Operation .

The apparatus for providing the API service transmits the API package to a package providing server or an apparatus for producing the API mash up Operation .

Referring to an apparatus for producing the API mash up obtains at least two or more API packages which respectively comprise an API meta data resource data and description data Operation . The API may be an open API or a local API.

The apparatus for producing the API mash up can obtain the API packages from a package providing server storing a plurality of API packages provided by a plurality of API packages or can directly receive the API packages from an apparatus for providing an API service.

The meta data includes information about a communication protocol to communicate with the package providing server or the apparatus for producing the API mash up and information about a data format of the API. The meta data may further include user account information or a user certification key for using the API.

The resource data comprises a configuration data of a user interface to generate the mash up and a tagging information representing an input output data format of the API. The resource data may further include information about an icon or a thumb nail for executing a mash up of the API in the user interface.

The description data may include information about components of the API package a version of the API or a library function for executing the API.

The apparatus for producing the API mash up extracts the API the meta data and the resource data from each of the API packages by using the description data Operation .

The apparatus for producing the API mash up generates a mash up of the API packages by using the API the meta data and the resource data Operation 

The apparatus for producing the API mash up may replace one of the API packages in the mash up with another API package or may add another API package to the mash up or may remove a part of the API packages from the mash up Operation .

Referring to an apparatus for producing the API mash up analyzes an input output data format of an API Operation . For example if a mash up developer performs a mash up on a Google map open API and a Flickr open API the input data format and the output data format of the Google map open API may be a specialized location and coordinates of the map respectively. Also the input data format and the output data format of the Flickr open API may be the name of a place and an image respectively.

For example the input output data formats may be analyzed by using data format information of an API and meta data or tagging information of resource data.

The apparatus for producing the API mash up searches another API package to perform the mash up with the API packages selectively on the basis of the input output data format of the API Operation . As described above since the output data format of the Google map open API is a set of coordinates and the input data format of the Flickr open API is the name of a place the mash up cannot be performed on the Google map open API and the Flickr open API as it is. Accordingly the apparatus for producing the API mash up searches other API packages in which the input data format is a set of coordinates and the output data format is the name of a place. For example the apparatus for producing the API mash up can search the corresponding API through the above described package providing server. Also the apparatus for producing the API mash up can search an open API or a local API stored in a storing unit.

The apparatus for producing the API mash up generates a mash up by using API packages and another API package Operation .

The present invention can also be embodied as computer readable code on a computer readable recording medium. The computer readable recording medium is any data storage device that can store data which can be thereafter read by a computer system. Examples of the computer readable recording medium include read only memory ROM random access memory RAM CD ROMs magnetic tapes floppy disks optical data storage devices and flash memory.

According to the present invention a standardized format of an API package including an API meta data resource data and description data is provided and a mash up is generated using the API package so that mash up contents can be easily generated from various types of APIs and can be easily updated.

While the present invention has been particularly shown and described with reference to exemplary embodiments thereof it will be understood by one of ordinary skill in the art that various changes in form and details may be made therein without departing from the spirit and scope of the present invention as defined by the following claims.

