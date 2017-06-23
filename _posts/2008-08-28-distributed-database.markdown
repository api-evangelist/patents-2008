---

title: Distributed database
abstract: The invention relates to a module to be included onboard the equipment of a telecommunication network and comprising: a database storing at least search field values including URL addresses, at least some of said URL addresses being stored in an encrypted form, encryption means capable of encrypting a piece of information received by the module in order to allow an information search in the database by comparison with the encrypted search field values.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09129131&OS=09129131&RS=09129131
owner: XOOLOO
number: 09129131
owner_city: Paris
owner_country: FR
publication_date: 20080828
---
This application is a 371 National Phase Filing of International Patent Application No. PCT FR2008 051541 claiming priority under the Paris Convention to French Application No. 07 06090 filed on Aug. 30 2007.

The invention relates to the field of distributed URL address databases. As shown in it is known to transmit from a central equipment to a distributed equipment a copy of at least a portion of a mother database stored in the central equipment . This database received by and stored in the distributed equipment is called a distributed database an onboard database or a daughter database.

The distributed equipment is capable of being interrogated regarding the content of the daughter database for example by client items of equipment which can comprise user terminals. According to another example the distributed equipment comprises a user interface allowing to interrogate it directly.

The mother and daughter databases are structured with entries each entry comprising at least one search field value and optionally one or more attributes.

During an interrogation step the distributed equipment receives a message comprising a piece of information referenced URL nin . The database is consulted in order to search for this URL ninformation among the search field values of the database. The distributed equipment returns a response referenced AUTH in depending on the result of the search.

For example as shown in the database can store a list of URL Uniform Resource Locator addresses and for each URL an attribute value indicating if the content corresponding to this URL is or is not disapproved for children. The distributed equipment can for example belong to an internet access provider. If the value URL nsent by the client equipment for example a child s computer is found in the database and if the corresponding attribute in the database has a value such that access is not disapproved for children the equipment returns a response AUTH authorising the equipment to display the content corresponding to the value URL n.

The central and the distributed equipment can typically belong to different people. For example the daughter database is sold or leased by a database producer controlling the central equipment to a person for example a software publisher or an internet access provider controlling the distributed equipment. The latter is thus able to use the daughter database for a use other than that foreseen by the database producer. For example the daughter database could be transferred from the distributed equipment to a third party disclosed copied partially or totally reused etc.

The purpose of the invention is to limit uses of the distributed databases other than those foreseen by the database producer.

According to a first aspect the invention relates to a module intended to be embedded in an equipment of a telecommunication network and comprising 

Advantageously all of the search field values of the database are encrypted but it is of course possible to provide for leaving certain search field values in clear.

Provision can be made for the encryption means to be able to use the same algorithm as that used for giving the encrypted search field values possibly with the same key or keys. However any algorithm whatsoever can be used by the encryption means provided that for a given piece of information stored in encrypted form in the database the encryption of this piece of information in clear by the encryption means makes it possible to find the database entry which corresponds to this piece of information.

With the module according to an aspect of the invention it is possible to interrogate the module regarding the content of the database without it being necessary to decrypt search field values of the database. The univocal encryption used allows a consultation of the database whilst retaining its encrypted search field values thus limiting the potential uses of the database other than those foreseen by the producer.

As the search field values of the daughter database are encrypted the daughter database can be transmitted from one secure equipment to another without risk of disclosure. In fact even if a pirate should intercept the database during transmission he would be incapable of using the intercepted database because of the encryption of the search fields. The same would apply even if the pirate succeeded in overcoming the protective measures of a secure equipment and accessing the database stored in that equipment.

The invention can be applied to the field of access control for example the protection of children on the internet. The module according to an aspect of the invention can be included onboard a distributed equipment controlled by a person other than the producer such as for example a software publisher or an internet access provider. Because of the encryption of the search field values of the daughter database the possible uses of the daughter database by this other person are limited. For example the transfer of the daughter database to a third party equipment is relatively difficult insofar as the daughter database cannot be used without the encryption means. Moreover modifying the daughter database from the distributed equipment risks the generation of interference insofar as the search field values cannot be read in clear and insofar as the other person does not know the initial content of the database.

The encryption means can be software means for example an interface of the API Application Programming Interface type and or hardware means for example a smartcard a USB key a CD ROM a hard disk etc.

Advantageously the encryption means are protected such that it is difficult for a person with bad intentions to access the code of the encryption means. It will thus be even more difficult for that person to transfer the module to a third party equipment or to modify the database himself insofar as the encryption used is unknown to him.

The invention is not limited by the way in which this protection is implemented. Software protection can be provided for example encryption of the code of the API or hardware protection for example by choosing encryption means comprising a smartcard.

Alternatively the encryption means can be freely accessible in particular if the encryption means are incapable of decrypting the encrypted values. The method according to an aspect of the invention therefore guarantees non access to the data of the database the values of the search fields being in encrypted form.

The encryption of the search field values can for example be destructive i.e. it is impossible to find the values in clear from the encrypted values thus guaranteeing non disclosure of the search field values. For example the encryption can be carried out by applying a hash algorithm.

The encryption of the search field values can for example be carried out using asymmetric encryption. Asymmetric encryption consists of using different keys for encryption and decryption. The module can thus retain only the encryption key such that even if a person with bad intentions should access the code stored in the encryption means that person would not be able to decrypt the encrypted field values of the database.

It is moreover possible to provide overall encryption of the database the decryption key being stored in a memory of the module. This overall encryption provides an additional level of protection but does not in any way limit the scope of the invention.

The overall decryption key can for example be stored in the API. The API can decrypt the database by using this key for example once only following the installation of the module in the distributed equipment or on each reception of a request message comprising a search field value. In the first case the database is protected from an attack during the transfer to the distributed equipment. In the second case the distributed equipment stores an encrypted database the search field values therefore being doubly protected which further limits non authorized uses of the database.

Advantageously the module comprises a memory storing a first licence number processing means capable of calculating a second licence number as a function of an identifier of the equipment in which the module is embedded and means of communication of the first and second licence numbers to a central equipment.

Thus even if a malicious person should succeed in transferring the module to a third party equipment the module would then inform the central equipment of the first licence number and of a second licence number different from the number expected for this first licence number. The central equipment typically controlled by the database producer would then be able to apply a sanction for example the pure and simple blocking of the transferred database.

The identifier of the equipment making it possible to calculate the second licence number can for example be an identifier of the operating system of the equipment in which the module is included onboard a network address of this equipment for example an IP address etc.

The memory the processing means and the communication means can be integrated in the API carrying out moreover the encryption of the information received for the purpose of a search in the database.

The communication of the licence numbers can be carried out automatically by the API during an updating of the database for example.

According to another aspect the invention relates to a method of the construction of a module in which at least one field value comprising a URL address is encrypted. This encrypted value is stored as a search field value of a database of the module. The database is coupled with encryption means capable of encrypting a piece of information in such a way as to allow a search for this information in the database by comparison with the encrypted search field values.

This method which can be implemented by a databank producer s equipment for example makes it possible to construct a module according to an aspect of the invention.

According to yet another aspect the invention relates to a method of interrogation of a database of URL addresses embedded in an equipment of a telecommunication network comprising the steps consisting of receiving a request message extracting a piece of information from this message and encrypting the extracted information. This encrypted information is searched for in the database by comparison of the encrypted information with of the values of URL addresses encrypted and stored in the database as search field values. Finally a response is sent depending on a result of the search. If the information is found in the database the response sent can optionally comprise the value of one or more corresponding attributes.

This method which can be implemented by an API for example makes it possible to use the database without it being necessary to access the search field values in clear. These values can thus remain encrypted thereby protecting the database from unauthorised uses.

Advantageously the extraction step consists of breaking down a search field value of the request message into elementary portions and generating a set of combinations of the elementary portions each combination of this set constituting a piece of information to be encrypted.

This breakdown makes it possible to store fewer entries in the database. For example if the request message comprises a search field value corresponding to

the database can be satisfied with the encrypted value corresponding to www.foo.net . The value of the request message can thus be attached to a value of the database without it being necessary to store all the variants.

The breakdown can be carried out by locating special characters such as . etc. received in the request message. The elementary portions can include these characters or can start with the character following one of these located characters and or can end with the character preceding one of these located characters.

Moreover for at least one search field value provision can be made for storing in the database an attribute value indicating the nature of this search field value. For example an attribute value site can correspond to the encrypted value corresponding to www.foo.net indicating that all the combinations including the elementary portion www.foo.net are to be attached to this search field value of the database. For example a value exact URL can correspond to the encrypted value corresponding to www.foo.net truc chose.htm indicating that only the encrypted combinations identical to this encrypted value are to be attached to this value.

It is of course possible to provide for certain attribute values to have priority over others. Thus if from a same received message several encrypted search field values are recognised in the database the priority given to the corresponding attributes makes it possible to choose one of these encrypted values. For example the attribute value exact address can have priority with respect to the value site . It is thus possible to envisage for example authorising access to the whole of a site except for a specified sub directory of this site and to achieve this with only two entries in the database.

It is thus possible to qualify the data stored in the database relatively precisely and to respond to request messages in a relatively apt manner.

Provision can also be made for the extraction step to comprise the step consisting of generating from a search field value received in the request message that value comprising an initial string of characters a set comprising the initial string of characters and or at least one string of characters obtained by deletion of at least one character at one end and or at the other end of the initial string of characters each string of characters of the set constituting a piece of information to be encrypted. The search step is carried out iteratively by choosing the information to be searched for in order of decreasing string length and the search is ended in the event of success during a given iteration.

The information of the set can be generated at the same time prior to the encryption step or steps. A step of sequencing of the strings of characters of the set in size order can be provided the first string comprising the longest string and the last string comprising the shortest string. The search step is carried out for the first encrypted string and in the event of failure is repeated iteratively by choosing the next string. In the event of success the iteration is ended.

Alternatively provision can be made for generating a string of characters of the set only in the event of failure of the search for the preceding string of characters. If the first iteration is successful the set then comprises a single string of characters.

According to yet another aspect the invention relates to a method of interrogation of a database comprising the steps consisting of

Advantageously the method comprises moreover the step consisting of ending the search in the event of success during a given iteration. Thus the search is ended at the first iteration during which the search is successful such that no search is carried out for shorter strings of characters shorter than the string for which the search was successful .

The invention is in no way limited by this feature. It is for example possible to provide for carrying out the search in order of decreasing string length by repeating the iterations down to for example a predetermined minimum string length set for example at one character or three characters and then choosing a string from among the strings for which the search was successful.

The search method according to this aspect of the invention can make it possible to avoid the steps related to the qualification of a character string.

For example in the case of a method in which following the reception of a search message comprising a URL address a search is carried out only for this exact URL for example

 http www.foo.net truc bidule machin html and or for the site address corresponding to this URL for example http www.foo.net it is then necessary to carry out those steps related to the qualification.

For example the database can be structured according to the attribute values it is then necessary before starting the search to know if a piece of information searched for is an exact address or a site address in order to know which memory zone to carry out the search in.

According to another example the search by comparisons is carried out without preconception regarding the qualification but once a piece of information is found the value of the corresponding attribute in the database is checked. For example for a search field value corresponding to

if only http www.foo.net is found with the attribute exact address it is considered that the search is not successful. A test step regarding the value of the attribute is therefore necessary.

By proposing a systematic search from the longest string to the shortest string the method described above makes it possible to avoid those steps related to the qualification of the string searched for. In fact advantageously when a given iteration proves to be successful no search is carried out for shorter strings.

Moreover this method provides relative flexibility for the creation of databases. With the method described above in which only the exact URL and or the site address can be searched for it is relatively difficult to reference any sub directory or any other intermediate level. For example if it is desired to authorise access to the whole of the site www.foo.net with the exception of the sub directory truc it is necessary to reference all of the exact URL addresses of the sub directory truc.

With the systematic search method it suffices to reference two entries http www.foo.net and http www.foo.net truc . During an iterative search for the value http www.foo.net truc bidule machin.html truc bidule 

the string of characters http www.foo.net truc is recognised before http www.foo.net since it is longer and access to the URL will be refused.

This method makes it possible to avoid heavy workloads related to the qualification of search fields in the database.

Advantageously each iteration can comprise prior to the comparison steps a step of encrypting the string of characters to be searched for. The search fields of the database can in fact be stored in encrypted form in order to limit the possible uses of the database.

Advantageously in each iteration the corresponding information comprises a string of characters obtained by deletion of one or more special characters of the type . etc. or by deletion of non special characters of the letters and figures type preceding or following a special character for example a punctuation character at the start or at the end respectively of the character string of the information searched for during the preceding iteration.

The system of comprises a central equipment storing a mother database . The database is structured with entries each entry comprising in this example a search field value SF1 SF2 etc. and an attribute att1 att2 etc.

In this example the database stores the search field values SF1 SF2 in clear thus allowing easy operation of the database by a database producer controlling the central equipment . Alternatively provision can be made for the mother database to store the search field values in an encrypted form for example for greater security.

The field values SF1 SF2 etc. are encrypted for example by using a hash function and stored in hashed form as search field values of a daughter database. The hashing can for example be carried out using a well known hash function for example of the Haval type.

This daughter database is transmitted to a distributed equipment in a module comprising moreover encryption means for example an application capable of using this hash function.

If a client equipment interrogates the distributed equipment by sending a request message R the application extracts from this message a piece of information URL and hashes this information. The search among the entries of the daughter database is carried out on the basis of this hashed information.

In fact if the database comprises an entry corresponding to this information URL then one of the hashed search field values H SF1 H SF2 etc. is equal to the value of the hashed information H URL . Provision can be made such that if the hashed information is found the module returns a positive response or also an attribute value corresponding to this hashed information within the database . Provision can be made such that if the hashed information is not found the module returns a negative response such as shown in .

As the search field values of the daughter database are encrypted the daughter database can be transmitted from one secured equipment to another without risk of disclosure.

The invention can thus be applied in the field of the databases of illegal sites in a given country for example paedophilic sites or gambling sites in France. The invention makes it possible to transfer all or part of these databases for example for the purpose of crosschecking between police departments without risking the disclosure of a list of illegal sites to a malicious person. More generally as the invention makes it possible to limit unauthorised uses of these databases the invention makes it possible to offer wider access to these databases for their normal use.

Once the database is installed the distributed equipment can communicate with the central equipment in particular in order to update the daughter database . The database can in fact be refreshed relatively frequently for example every day or every week in order to reflect the latest modifications made to the mother database .

In this example the global encryption algorithm of the daughter database is asymmetrical i.e. the keys Kand K are different but it can of course be arranged otherwise.

Moreover as seen previously the database stores search field values in encrypted form K SL1 K SL2 etc. In this example the encryption of the search field values has been carried out within a central equipment not shown in using an asymmetrical encryption algorithm for example RSA Rivest Shamir Adleman with an encryption key K. The API stores the value of this encryption key Kin a memory in order to be capable of carrying our this same encryption following the reception of a request message. The decryption key corresponding to this encryption Kis not known by the API so that the API is incapable of decrypting the encrypted search field values.

Finally in this example in order to obtain an updated file from the central equipment the module must send two licence numbers in addition to a module identifier and version index pair. The first licence number LIC1 is retained in a memory of the API . This first licence number LIC1 has for example been obtained from the central equipment itself. The API comprises processing means for example a processor capable of reading a memory of the distributed equipment storing a hardware identifier of the equipment for example a serial number HW  . The processing means calculate a second licence number LIC2 from the serial number HW  .

The two licence numbers are sent by communication means which are not shown for example a communications port.

In general the invention is not limited by the form of the processing means the communication means or the memories. For example the component used as processing means can moreover serve as a memory storing the keys K Kand or the number LIC1.

Thus if the module was installed without the authorisation of the central equipment in a third party distributed equipment not shown the second licence number depending on the distributed equipment in which the module is included onboard would be different. Thus during an update request the central equipment is able to detect an unauthorised transfer from the distributed database. The central equipment is then capable of reacting for example by triggering an alarm informing the database producer of the problem by blocking the module installed without authorisation etc.

A central equipment stores an original database storing search field values in clear for example in XML Extensible Markup Language format.

The equipment stores moreover database sub sets . These sub sets are intended to be transmitted for example by downloading to distributed items of equipment. The sub sets are themselves filed within the central equipment on the basis of distributed equipment using a module identifier ID mod.

These sub sets include data coming from the original database in lots or batches . Each batch is structured with entries.

Certain search field values SF8 SF2 etc. stored in the mother database are encrypted according to a first algorithm. These encrypted values K SF8 K SF2 are stored in the sub set as a search field value of a database intended for the distributed equipment corresponding to this sub set .

The sub sets store an identifier of the first algorithm and an identifier of the encryption key Kused and or the encryption key itself . These identifiers and optionally this key are transmitted with the corresponding batch to a distributed equipment which can then be able to form a module comprising encryption means and a distributed database. The distributed equipment then stores the encrypted values K SF8 K SF2 as search field values of a database of the module.

Alternatively the central equipment can couple the sub set with an API capable of carrying out the same encryption. This API constitutes with the sub set a module intended to be transmitted in its entirety to the distributed equipment. In this case within the sub set the encrypted values K SF8 K SF2 are stored as search field values of the module.

Advantageously the client equipment is capable of transmitting distributed databases updating data. The sub sets can in fact be arranged in such a way as to be used for updating purposes. For example the sub sets include a version number for example 200704281. Moreover each batch entry comprises an operation field defining if this entry must be added to the distributed database deleted or updated for example.

During an updating of the distributed database the distributed module interrogates the central equipment in order to check if an update is available download changes from the server equipment and include these changes in the local database . Each module has an identifier ID mod allowing the central equipment to recognise the database sub set which is intended for this module.

For a given module identifier version index pair the central equipment is therefore capable of listing the possible revisions that have occurred since this version.

According to the module identifier version index pair the central equipment is able to generate a file containing the changes that have occurred since this version.

Thus when a distributed equipment interrogates the central equipment regarding possible modifications the equipment transmits a module identifier ID mod and an index representative of the latest version received from the central equipment as well as possibly two licence numbers LIC1 LIC2. The central equipment then returns in response a file M containing the changes that have occurred since this version the search field values being stored in an encrypted form in this file. The file M can comprise a sub set or can be obtained from a sub set etc.

The file M can undergo a compression of the zip type for example and or be encrypted before the transmission.

The sub sets can comprise other fields for example a field specifying the type of the search fields in this case URLs a date of creation field a source entity field a field for the overall encryption algorithm used if necessary and fields for possible comments the batch identifier the date on which the batch can be ignored in ISO 8601 format etc.

It will be noted that a batch can have several destinations i.e. that it can be possible for a batch to be transmitted to several distributed items of equipment.

The batch is structured with entries each entry being able to comprise several fields a internal identification field for the producer which is of course optional a URL address or any other information in encrypted form digest it being possible for the encryption algorithm to be specified in a header an attribute whose value indicates the nature of the URL for example site page or domain an attribute defining for example a right of access to the URL for certain persons like children adolescents employees of a company etc.

Then during a step the exact address is broken down into elementary portions P P . . . Pn for example 

Following a step during which a set of combinations of one or more of these elementary portions is generated for example 

It is therefore possible to make provision for retaining in the set of combinations only certain plausible combinations. For example the combinations for which the letters www appear relatively late of the type

Each combination of the retained set of combinations indexed i in constitutes a piece of information to be encrypted during an encryption phase .

This phase implements a loop with the index i. Each combination of the set of combinations retained is hashed during a step .

The database can then be searched during a search phase implementing for example a loop with the index i on the basis of comparisons of the hashed combinations and search field values encrypted during comparison steps .

If a comparison shows that a hashed combination is equal to one of the encrypted search field values then this encrypted value is stored during a step with the corresponding possible attributes.

The search can be stopped after the first encrypted value storage or all of the combinations can be scanned before stopping the search such as shown in .

In this latter case it is possible that several encrypted values have been stored. The filing of these found values according to the value of their attribute for example site exact URL etc. can be envisaged.

A priority can be allocated to the possible values of this attribute. For example the value exact URL can have priority over the value site .

Which entry to recognise among the entries stored in step is therefore chosen according to the attribute value of highest priority.

A response can be sent indicating for example if the search is successful and or indicating a value of one or more attributes corresponding to the recognised entry for example authorised site .

A string search variable is allocated the value of this initial string of characters during a step . An iterative search referenced then follows during which comparisons of this string variable with search field values stored in the database are carried out.

These comparisons can be carried out using values in clear or as shown in using encrypted values. A step for encryption for example by hashing and a search step using encrypted values are then provided.

In the event of failure during a step a new string of characters is generated by deletion of one or more characters at one and and or at the other end of the current string of characters. These iterative generations constitute extractions of information to be encrypted during step .

In the event of success it is considered that the search is successful and the iterations are ended during a step .

It is moreover possible to provide one or more test steps that are not shown following the generation step during which step or steps it is checked that the new string generated is still plausible. For example if two successive strings end with a letter an additional character is deleted and this procedure is repeated until the new string ends with a special character.

For example if the new string no longer contains any special characters it is considered that the string is too short and the search is ended. In this latter case provision can be made for returning a response of the ABSENT type. According to an embodiment which is not shown the generation of all of the strings is carried out at one time prior to the iteration.

The optional hashing step can also be carried out prior to the iteration all of the strings then being retained in a temporary memory in hashed form.

