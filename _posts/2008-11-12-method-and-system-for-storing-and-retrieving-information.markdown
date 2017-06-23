---

title: Method and system for storing and retrieving information
abstract: A method of storing and retrieving a utilization data associated to a sensitive information which requires to be secured in an environment including a plurality of application systems that can use the information, includes:


url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08190635&OS=08190635&RS=08190635
owner: Amadeus s.a.s.
number: 08190635
owner_city: Biot
owner_country: FR
publication_date: 20081112
---
The present invention relates generally to a method and a system for storing and retrieving electronic information. The method and system of the invention are particularly directed to the storage of electronic information that requires to be secured and that must be available for use by various applications. The method also refers to a method for storing and retrieving applicative data that relates to said information.

Securing the storage and the manipulation of sensitive information is a major issue in particular for organizations wherein many applications have to use such sensitive information.

The development of electronic transactions increases the number of transactions requiring sensitive information. Besides in order to facilitate the transactions and to be more attractive for users many organizations strive to obviate the need for re entering all needed data to complete a transaction. This implies to store sensitive information. Yet storing sensitive information can hardly be totally secure. Indeed databases storing sensitive information may possibly be stolen or hacked. Moreover sensitive information may possibly be illegally retrieved during its transmission from the database that stores it to the application that processes it.

To increase the security of the storage some systems allow to split the sensitive information in two parts and to store each part in a respective database.

However these systems have turned out to be not totally satisfactory in particular in an environment where various applications need to process the same sensitive information.

These various applications may be run by a single organization that provides many services. Global Distribution Systems GDS such as AMADEUS or SABRE are typical examples of such organizations that provide many services involving various applications which require sensitive information.

Several distinct companies may also cooperate to provide integrated services to customers. For instance an e merchant and a bank may cooperate to provide customers with easy online purchase solutions. Several merchants can also cooperate to form an organization and provide customers with a wider range of services and products.

It is an object of the invention to provide an efficient and user attractive method for storing and retrieving information in an environment wherein many applications may need to process the same sensitive information.

The invention describes a method of storing and retrieving a utilization data associated to a sensitive information which requires to be secured in a distributed environment comprising a plurality of application systems ASithat can use said information and said utilization data. Typical examples of sensitive information are credit card numbers. Storing said information comprises the below mentioned steps.

A given application system ASof said plurality of application systems ASireceives said information and generates from said information an extracted data and a complementary data. The extracted data and the complementary data are generated in such a manner that 

Further the given application system ASgenerates an encoded information from said information. Then it sends the extracted data and the encoded information to a server system SS.

The server system SS generates an index ID and assigns this index ID to the encoded information and the extracted data. Then the server system SS stores the encoded information the extracted data and the index ID in a database DBassociated to the server system SS. The server system SS further forwards the index ID to the given application system ASof the plurality of application systems ASi.

Then said given application system ASassigns the index ID to an application stored data related to the information. Finally the given application system ASstores the index ID along with said application stored data in a database DBassociated to said given application server AS.

According to a first use case of the invention the utilization data is the information and the application stored data is the complementary data.

Thus the given application system ASonly sends the extracted data and the encoded information. There is no exchange of sensitive information. Besides since the database DBof the given application system ASonly stores the complementary data and the ID and since the database DBof the server system only stores the extracted data the encoded information and the index ID then extracted and complementary data are never stored in the same database. Therefore sniffing the network stealing or hacking any one of the database of the given application system ASor the database of the server system DBdoes not enable to get either complementary and extracted data or the full information. Therefore the information cannot be rebuilt and illegally used.

Besides the index ID is generated by the server system SS and not by the given application system ASwhich receives the information. Thus an index ID is assigned to a single pair formed of encoded information and extracted data. Therefore there is no concurrent index ID related to the same information. In order to exchange data related to a given information the various application systems ASican share the unique index ID associated to said information. Accordingly the invention is particularly convenient to store sensitive information in a distributed environment wherein many application systems ASiuse said sensitive information.

The database DBof the server system SS stores the extracted data along with the encoded information and the index ID. Thus an application system can receive either the extracted data when said application system is provided with the index ID or to receive the index ID when said application system accesses the extracted data and the encoded information. Therefore such method allows to provide the plurality of application systems ASiwith various data that these application systems ASirequire to handle predetermined uses. Accordingly the invention allows secured storage for various operations that the plurality of application systems ASihandles.

Even if one or many applications modules ASiare stolen forced or hacked the information cannot be retrieved. Indeed getting the encoding process does not enable to obtain the information since neither the extracted data nor the encoded information are stored in the databases DBassociated to the various application systems ASi. Therefore the invention enhances the information storage security.

According to the invention retrieving the sensitive information at any considered application system ASamongst the plurality of application systems ASicomprises the following steps. Said considered application system ASreceives the index ID and sends the index ID to the server system SS. The server system SS retrieves from the database of the server system SS the extracted data corresponding to said ID. It further sends the extracted data to said considered application system AS. Then the considered application system ASreceives the complementary data and rebuilds the information from the extracted and the complementary data. Thus an application of the considered application system AScan use the information.

The full sensitive information is never exchanged nor stored. The information is only available at the considered application ASsystem when said considered application system AShandles a process that requires said sensitive information. Typically the information is stored in the process memory and nowhere else. Once the use is completed the information is removed. Besides the extracted and complementary data are not stored in the same database. Therefore sniffing the networks or stealing any one of the databases does not enable to obtain the sensitive information.

Since the invention allows to make the sensitive information available through entering a mere index the invention obviates additional re entering or manipulation of the sensitive information. Therefore the invention decreases the risk of loss or theft of said sensitive information when the user manipulates or enters it.

According to a first event of this first use case said considered application system ASis the given application system AS. Thus the step of receiving the complementary data at said considered application system AScomprises receiving the index ID at said given application system ASand retrieving thanks to the index ID the complementary data which is stored in the database DBassociated to the given application system AS.

Thus in case the considered application system ASwhich needs the information has already been provided with this information the complementary data can be retrieved upon reception of the index ID directly from the database DBof the considered application system AS. Moreover sending the index to the server system SS triggers the forwarding of the extracted data from the server system SS. Then the application system ASgets the extracted and complementary data and can obtain the required information.

According to a second event of this first use case said considered application system ASis different from the given application system AS. Besides the considered application ASdoes not comprise a database which indexes the complementary data along with the index ID. Thus the above mentioned step of receiving the complementary data at said considered application system AScomprises receiving the complementary data from the given application system AS.

More particularly when a considered application ASreceives an index ID and requires the information corresponding to this index ID it checks whether this index ID is stored in its associated database DB. In case this database does not comprise this index ID or does not comprise the complementary data corresponding to said index said considered application ASsystem sends a request. This request comprises the index ID for which information is required. The request arrives to the given application system AS. The given application system ASis associated to a database which indexes the complementary data with the index ID.

In response to said request the given application system ASretrieves from its database DBthe complementary data and forwards it to the considered application system AS. Further the considered application ASsystem sends the index to the server system SS in order to receive the extracted data. Thus the considered ASapplication system can combine the complementary data and the extracted data to obtain and use the required information.

The considered application ASsystem may further store the complementary data in its database and index it with the index ID. Thus next time the considered application ASsystem will be able to obtain the information without requiring that the given application ASsystem forwards it the complementary data.

Therefore several distributed application systems can exchange data in order to enable a considered application to obtain the required information though this considered application has never been provided so far with said information.

Accordingly the invention provides a secured method that obviates the need for customers to re enter information once said information has already been entered in any one of the application systems of the distributed environment.

According to a second use case of the invention the utilization data and the application stored data are identical and are applicative data. These applicative data are intended to be used by at least an application of an application system ASi. Besides said applicative data do not require a high level of security. Therefore applicative data can be stored as such in the database of a given application AS. For instance applicative data may relate to a user profile data user loyalty program user preferences flight departure and or arrival service requests associated to the flight hotel or car rental information customer profile data etc. .

Retrieving said applicative data at any considered application system AScomprises the following steps. Said considered application system ASreceives the sensitive information. It generates the extracted data and the encoded information from said information. The considered application system ASsends the extracted data and the encoded information to the server system SS .

Then the server system SS retrieves from the database of the server system DBthe index ID corresponding to the pair formed of both extracted data and encoded information. It forwards the index ID to said considered application system AS.

The considered application system ASreceives the index ID and retrieves the applicative data indexed with the index ID. Thus an application of the considered application system AScan use the applicative data.

Like for the first use case in this second use case the risk of theft of the credit card is significantly reduced since neither the considered application system AS nor the server system keeps the full information. Besides neither is full information ever transmitted in a single transmission between any application system AS iand the server system SS.

According to a first event of this second use case the considered application system ASis the given application system AS. Thus the applicative data is retrieved from the database DBassociated to the given application system AS.

Thus applicative data can be quickly retrieved once entering the information at any application system. This allows easy and user friendly use of said application.

Besides said retrieval of information is highly secured. Indeed the database of the given application system ASdoes not even have to comprise any of the complementary data extracted data or information. The database of the server system SS does not comprise the complementary data or the information. Only the encoded information and the extracted data and the extracted data are sent to the server system.

Thus the complementary and extracted data are never stored in the same database and the information is only available in the process memory of the application when generating the extracted data and the encoded information. Accordingly sniffing the network stealing or hacking any database turns out to be worthless.

According to a second event of this second use case the considered application system ASis an application system which is different from the given application system AS. Said application system ASdoes not comprise in its associated database DBthe applicative data indexed with the index ID. Thus retrieving the applicative data comprises the steps indicated below. Upon reception of the index ID from the server system the considered application system ASsends said index ID to the given application system AS. Then the given application system ASreceives the index ID and retrieves from its database DBthe applicative data thanks to the index ID. Finally the given application system ASsends the applicative data to the considered application system AS.

This second event of the second case highlights the fact that even in case a considered application system ASdoes not store a required applicative data this considered application system AScan be provided with this applicative data while keeping a high level of security for the sensitive information. Indeed this sensitive information is never stored nor transmitted in a single transmission between any of the application system or between any application system and the server system.

In a preferred embodiment the step of generating complementary data and extracted data includes dividing the information into a first portion and a second portion.

The invention is particularly well convenient for method wherein the information is a credit card number. Then the complementary data can correspond to apparent digits of the credit card number and the extracted data can correspond to concealed digits of the credit card number.

The step of generating an encoded version of the information may include computing a hashed value of the information through a hash function. In a preferred embodiment the hashed function is unknown to the server system SS . Therefore the invention allows to significantly limit the risk that a person may obtain the sensitive information through accessing the encoded version of the information.

The invention also provides a system for storing and retrieving a utilization data associated to an information which requires to be secured in a distributed environment comprising a plurality of application systems ASithat can use said information and said utilization data. The system of the invention includes a server system SS and a given application system ASamongst said plurality of application systems ASi. Said given application system ASis arranged for 

More generally the system according to the invention comprises the server system and the application systems ASi which are arranged for conducting the method described above.

The application system that manipulates the sensitive information comprises a process memory and is arranged so that the information is available only in the process memory.

Once the application system has used the information it deletes said information. Therefore the sensitive information is no more accessible after use. This limits the risks of theft.

In a preferred embodiment the system comprises at least a cache mechanism in the processing means of an application system ASi . The cache mechanism is arranged to store the information during the processing of said information. There is one cache instance per process.

In a preferred embodiment of the invention the system comprises a proxy component which is part of the secured storage system and which is comprised in the application system. The role of the proxy component is to handle at least one of the following steps that are intended to occur at the application system which hosts the proxy component 

Typically the proxy component can be a middleware library. It provides various API Application Programming Interfaces that interface the application of the application system with the server system. The proxy component can also comprise a cache mechanism.

Through handling information processing and data exchanges the proxy component significantly facilitates the integration of any application in the system of the invention.

In another embodiment of the system of the invention the application system does not comprise a proxy component and handles all required actions by its own. Thus such an application system can for instance format read messages from the server system computes the encoded version of the information etc.

In a particular embodiment of the invention the method comprises the following steps at any considered application system AS. The considered application system ASgenerates a request message comprising several indexes ID. Then it sends to the server system said request message. Further the server system searches its database and retrieves each extracted data associated to an index ID comprised in the request message. Then the server system sends a response message comprising the retrieved extracted data.

Then the considered application system ASreceives the response message from the server system SS. Finally the considered application system AScan rebuild all the information for which the extracted data has been received from the server system.

Accordingly with one single transaction an application system can send a list of indexes to the server system in order to receive all the extracted data corresponding to the list of indexes.

Such batch processes can also be used for retrieving applicative data. Indeed a considered application system can send to the server system SS a request message that contains a list of extracted data and encoded versions of the sensitive information. The server system retrieves from its database each index that is assigned to a pair of extracted data and encoded version included in the request message. Then it sends to the considered application system a response message comprising the indexes that have been retrieved. Thus the considered application system can retrieved the applicative data that are indexed with the indexes of the response message.

Therefore such batch processes allow substantially simplifying and speeding up the retrieval of information for many users. Accordingly the invention provides a method that enhances services offered to application s users. Such batch processes are particularly useful when new applications are migrating to the storage system of the present invention. Indeed when conducting migrations large amount of data have to be stored quickly and easily.

According to the above mentioned embodiment both extracted data and encoded information are sent to the server system in order to retrieve the index. Sending both extracted data and encoded information allows reducing significantly the risk to retrieve a wrong index.

According to an alternative embodiment only the encoded information is sent to the server system in order to receive the index at the application system. Although the risk to get a wrong index with this embodiment is higher than when both extracted data and encoded information are in the request said risk remains very low. Such alternative embodiment is particularly useful when dealing with large amount of data. Indeed it avoids manipulating and sending heavy extracted data to the server system.

Information can be constituted by numbers letters symbols or combination of the three. As designated in the present invention information is not limited to numbers. Extracted data and complementary can also include numbers letters symbols or combination of the three. Applicative data may comprise any nature of data and kind of files such as numbers letters symbols pictures videos etc.

The system may also comprise additional security means. These security means are arranged for reinforcing the security of the exchanges between the various application systems and between the application systems and the server system. These security means can check whether the sender of each message is actually authorized. They can discard messages sent by non authorized senders. For instance access to the server system may be limited to a limited number of authorized applications systems.

In practical security means perform encryption and decryption of exchanged messages between the various components of the system. Security means may also comprise means for triggering a warning when an abnormal operation is attempted. They can also include means for monitoring and recording exchanges transactions and processing of data.

The following detailed description of the invention refers to the accompanying drawings. While the description includes exemplary embodiments other embodiments are possible and changes may be made to the embodiments described without departing from the spirit and scope of the invention.

The system comprises n application systems which are referenced AS AS. . . AS. . . AS. Each application system is associated to a database DB DB. . . DB. . . DB. The application systems comprise applications that are intended to use sensitive information. They are run by an organization constituted of several companies that cooperate or by an organization like a GDS. To enhance efficiency of the services provided to users the organization strives to obviate the need for a user to re enter same data each time a transaction is conducted.

This also decreases the risk of loss or theft of sensitive information when the user manipulates or enters said sensitive information.

The system also includes a secured storage system which comprises a server system SS and a database DBassociated to this server system SS.

The system also comprises a communication network such as internet that interconnects each application system ASwith the server system SS. The communication network also allows the applications systems ASto exchange information together in a distributed environment. Advantageously the various components of the system are remotely located.

The components of the information storage system execute processes that provide secure storage and retrieval of sensitive or valuable information.

The secured storage and retrieval of sensitive information will be detailed below through illustrative use cases. In these use cases the sensitive information is a credit card number CC . Usually credit card number is formed of sixteen digits.

At step an application system ASamongst the plurality of application systems ASireceives a credit card number CC . Typically this credit card number is received after the user has entered it through a conventional interface such a keyboard for instance. This credit card number must be easily available for use at a later stage without requiring the user to re enter it. Therefore this credit card number has to be stored. The application system ASwhich handles the storage of the credit card number is designated first application system ASin the following.

The first application system ASdivides the credit card number CC into a first portion and a second portion. The first portion corresponds in this illustrative example to the first six digits and to the last four digits of the credit card number. This first portion will remain available at the application ASj. The second portion corresponds to the remaining six digits. This second portion will not remain available at the application system AS. In the following the first and second portion are respectively designated apparent digits A CC and concealed digits C CC .

The first application system ASalso generates an encoded version H CC of the credit card number CC . More particularly the first application system AScomputes a hashed value of the credit card number CC .

At step the first application system ASsends the concealed digits C CC and the encoded credit card number H CC to the server system SS.

The server system SS receives the concealed digits C CC and the encoded credit card number H CC . It generates an index ID and assigns this index ID to the encoded credit card number H CC and to the concealed digits C CC . Then the server system SS stores the encoded credit card number H CC the concealed digits C CC and the index ID in a database DBSS associated to the server system SS step . The server system SS generates the index ID once it has checked in its database DBSS which index ID is available step . If the two uplet H CC C CC is already stored by the server system SS then the index ID assigned to this two uplet H CC C CC is retrieved and is returned to the application system. Thus the check operated by the server system SS is not limited to checking the availability of the index ID.

At step the server system SS further forwards the index ID to the first application system ASof the plurality of application systems ASi .

Then the first application system ASassigns the index ID to the apparent digits A CC . Finally the first application system ASstores the index ID along with apparent digits A CC in its database DB step .

Thus the first application system ASonly sends the concealed digits C CC and the encoded H CC credit card number. There is no exchange of the full credit card number CC . Besides since the database DBof the first application system ASonly stores the apparent digits A CC and the ID and since the database DBof the server system only stores the concealed digits C CC the encoded H CC credit card number and the index ID then concealed C CC and apparent digits A CC are never stored in the same database. Therefore sniffing the network stealing or hacking any one of the database of the first application system ASor the database of the server system DBdoes not enable to get both apparent A CC and concealed digits C CC or the full credit card number CC . Therefore the credit card number CC cannot be rebuilt and illegally used.

Besides the hashed processing is conducted at the server application AS. Thus the function remains unknown to the server system SS. Therefore the invention allows to significantly limit the risk that a person obtains the credit card number CC through accessing the encoded version of the credit card number CC .

Moreover since no data sent by the application system ASare stored in the database DBof said application system AS then sent data cannot be reconciled with stored data. Therefore it is also useless to both hack the database DBof the application system AS and sniff the message transmitted by this application system AS in order to get the information e.g. the credit card number CC .

Concealed digits C CC generated by each application system ASare all stored together in the database DBof the server system. Yet these concealed digits are mandatory to rebuild the full credit card number CC . Thus resources allocated to securing the sensitive information can be concentrated on the server system SS and its dedicated database DBss. The invention obviates the need to spread these resources between the various application systems ASi. Therefore security can be significantly enhanced at the server system SS and at it associated database DBin order to prevent any kind of theft. This aspect is particularly advantageous in a distributed environment wherein the various application systems ASiand the various databases DBassociated to application systems are all remotely located and or in a distributed environment wherein the various application systems ASiand the various databases DBare remotely located from the server system SS and its database DB.

Besides the index ID is generated by the server system SS and not by any application system AS. Thus an index ID is assigned to a single credit card number CC . Therefore there is no concurrent index ID for the same credit card number CC . In order to exchange data related to a given credit card number CC the various application systems ASican share the unique index ID associated to said credit card number CC . Accordingly the invention is particularly convenient to store credit card number CC in a distributed environment wherein many application systems ASiuse said credit card number CC .

For instance various application systems of an organization may share data to obviate the need for a user to re enter its credit card number at any application system ASonce the full credit card number has already been entered at the first application system AS. This use case will be detailed below with reference to .

Therefore the invention contributes to enhance the efficiency of the services provided to application users.

With reference to a use case illustrating the retrieval of the credit card number CC is detailed below.

To this end at step the first application system ASreceives the index ID from its database. Then at step it sends the index ID to the server system SS. The server system SS retrieves from its database DBthe concealed digits C CC indexed with said index ID steps and . The server system SS further sends the concealed digits C CC to the first application system AS step .

First application system ASretrieves from its database DBthe apparent digits A CC which is indexed with the index ID. Finally the first application system AScombines the apparent digits A CC and the concealed digits C CC received from the server system SS in order to rebuild the credit card number CC step .

The various applications systems ASiare typed depending on the kind of service they provide. These application systems ASiknow each other and are able to identify the type of data they respectively require. When a first application system ASreceives a data that is useful for other application systems then the first application system ASsends this data to said other application systems.

The transmission of useful data may be operated automatically once said data is available at the first application system AS.

For example once apparent digit A CC is generated by ASand once index ID is received at ASfrom the server system SS then ASsends both apparent digit A CC and index ID to all the application systems that are typed as requiring apparent digit A CC and index ID steps .

Then each application system that is provided with said useful data can use it. For instance as soon as second application system ASreceives both apparent digit A CC and index ID step from ASit can obtain the credit card number CC . More precisely upon reception of index ID second application system ASsends this index ID to the server system SS step . The server system SS retrieves from its database DBthe concealed digits C CC indexed with said index ID steps and . The server system SS further sends the concealed digits C CC to second application system AS step . Then second application system AScombines the apparent digits A CC received from first application system ASand the concealed digits C CC received from the server system SS in order to rebuild the credit card number CC step . Finally the application of the second application system AScan use the card number CC .

Advantageously the second application system ASstores in its database DBthe apparent credit card number A CC indexed with the index ID step . Thus next time the second application system ASwill be able to obtain the credit card number CC without requiring that the first application system ASforwards the apparent digits A CC .

This embodiment implies that apparent digit A CC and index ID are transmitted together. This embodiment is particularly advantageous in an environment wherein all the applications are run by a single organization and wherein the interactions between the various applications are totally user transparent. In particular the final user card holder is not supposed to access the index ID assigned to his credit card number CC .

As illustrated in the use cases of the full credit card number CC is never exchanged nor stored. The credit card number CC is only available during its use at a considered application system ASwhen said considered application system AShandles a process that requires said credit card number CC . Typically the credit card number CC is stored in the process memory and nowhere else. Once the use is completed the credit card number CC is removed. Besides the apparent digits A CC and concealed digits C CC are not stored in the same database. Therefore sniffing the network or stealing any one of the databases does not enable to obtain the credit card number CC .

Use cases of also illustrate that several distributed application systems can exchange data in order to enable a considered application ASto obtain the required credit card number CC though this given application has never been provided so far with said credit card number CC or with apparent digits A CC . Accordingly the invention provides a secured method that obviates the need for customers to re enter credit card number CC once said credit card number CC has already been entered in any one of the application systems of the distributed environment. Besides the exchange of data between various application systems is totally user transparent.

With reference to a use case illustrating the retrieval of an applicative data related to the credit card number CC is detailed below. These applicative data are intended to be used by at least an application system. Besides said applicative data do not require a high level of security. Therefore applicative data can be stored as such in the database of the given application. For instance applicative data may relate to a user profile data user s loyalty program user s preferences user s photo etc. 

At step the first application system ASreceives the credit card number CC . Then it generates the concealed digits C CC and the encoded credit card number H CC from said credit card number CC . At step it sends the concealed digits C CC and the encoded credit card number H CC to the server system SS. Then the server system SS retrieves from its database DBthe index ID corresponding to both concealed digits C CC and encoded credit card number H CC steps and . Then the server system SS forwards the index ID to the first application system AS step . Upon reception of the index ID the first application system ASretrieves the applicative data indexed with the index ID step and . Finally the application of the first application system AScan use the applicative data.

At step the second application system ASreceives a credit card number CC . Steps are substantially identical to steps detailed above. At step the second application system ASreceives the index ID from the server system SS. After having checked that its database DBASdoes not store an applicative data indexed with the received index the second application system ASsends this index ID to the first application system AS step . The first application system ASsearches its database DBand retrieves the applicative data indexed with the index ID steps and . Then the first application system ASforwards the applicative data to the second application system AS step . Finally the applicative data is available for use at an application of the second application system ASk.

Advantageously the second application system ASstores in its database DBASk the applicative data indexed with the index ID.

Thus applicative data can be quickly retrieved provided the applicative data has already been indexed and stored in any database and provided that the credit card number has already been entered once.

This allows easy and user friendly usage of applicative data rendering therefore applications more attractive for users. Besides the exchange of data between various application systems is totally user transparent.

Like for the use cases that relates to credit card number retrieval in use cases addressing applicative data retrieval the risk of theft of the credit card is significantly reduced since neither an applicative system AS AS nor the server system SS keeps the full credit card number CC . Besides neither is full credit card number CC ever transmitted in a single transmission between any application system ASiand the server system SS or between two application systems AS AS.

In a preferred embodiment the storage system comprises at least a processing and transaction module at an application system. As illustrated on the particular embodiments of the system comprises a proxy component at each application system. According to another embodiment only some of the application systems may be associated to a proxy component. The proxy component is part of the secured storage system. The proxy handles at least some of the following steps that are intended to occur at an application system wherein said proxy component is included 

Typically the proxy component can be a middleware library. It provides various API Application Programming Interfaces that interface the application software of the application system with the server system. The proxy component can also comprise a cache mechanism. The cache mechanism is arranged to store the credit card number CC during the processing of said credit card number CC . There is one cache instance per process so that the credit card number CC is no more available once it has been used by the application of the application system.

Through handling credit card number CC processing and data exchanges the proxy component significantly facilitates the integration of any application in the system of the invention.

