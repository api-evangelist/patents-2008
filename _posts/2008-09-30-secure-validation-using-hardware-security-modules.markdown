---

title: Secure validation using hardware security modules
abstract: Disclosed is secure decryption and business rule validation of encrypted confidential data within a hardware security module (HSM). The validation may include the use of a Bloom filter stored and executing within the HSM. The return order of encrypted data within the HSM as well as requests for external data relating to validation may be randomized to further harden against correlation attacks.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09053480&OS=09053480&RS=09053480
owner: Amazon Technologies, Inc.
number: 09053480
owner_city: Seattle
owner_country: US
publication_date: 20080930
---
Organizations find it necessary to validate data including payment or identification information. Data validation is the process of ensuring that data to be processed is correct free of unnecessary or unwanted data and typically involves testing against a list of valid items or algorithms.

Validation can be computationally intensive create unwanted delays and render confidential information more accessible to compromise. Confidential information may be more accessible to compromise because conventional data validation systems render encrypted confidential information into cleartext for validation within applications that may be subject to compromise.

Given the costs involved with breaches of security organizations demand hardened and more secure validation of data.

As described above data validation requires computational resources as well as presenting the data in a form which can be validated typically into cleartext. Validation of alphanumeric data against business rules encompasses a variety of uses from checking personal identification information e.g. pin numbers social security numbers login names passwords etc. access information e.g. access codes access control lists etc. payment information e.g. credit card numbers bank account numbers loan numbers etc. or otherwise confirming that information input is complete and correct.

This disclosure describes a variety of techniques for using a hardware security module HSM to provide rapid and secure validation of encrypted information. By decrypting confidential information within a hardened HSM the cleartext for validation is shielded from attacks on the host server operating system or applications.

An attacker could attempt to compromise the processing of data within an HSM by monitoring the input and output of the HSM and attempting to find an association between the inputs and the outputs. This may be termed a correlation attack. To harden against this form of attack randomization of the return order or processing order of data within the HSM or the requests for validation data external to the HSM necessary to complete validation processes or both may take place. This randomization thus obscures the association between specific inputs and outputs to the HSM.

Furthermore utilizing an HSM in a validation server improves availability of cryptographic functions necessary to render cleartext for validation processing. This improved availability may reduce time for validation which can be beneficial in a high transaction environment.

A payment processing server has data to be validated. This data may be personal identification information security access information account information payment information or the like. For example the data may be credit card account or bank account numbers.

The payment processing server makes a request for validation of data against business rules. The payment processing server requests validation of the data for business reasons so it may properly complete the payment processing resulting in settlement of funds and shipment of goods. While shown as being external to the validation server payment processing server may be within validation server . If external the request from payment processing server may reach the validation server by a network including any one or combination of multiple different types of networks such as cable networks the Internet wired wireless other local or wide area networks as well as a physical exchange of data stored on memory. If internal the request from payment processing server may be by a program call or otherwise along a system bus.

Validation server receives the request for validation of data . The validation server may encompass a system ranging from a single server at one geographic location to an array of many servers spread across the world.

A validate data module accepts the request for validation and accesses the HSM . The validate data module may access the capabilities of the HSM by way of an adjunct application programming interface API .

An application programming interface API is a set of functions procedures or classes that an operating system library or service provides to support requests made by computer programs stored in memory and executing on a processor. Here the adjunct API provides the programs executing on the validation server with callable hooks to easily utilize the features available within the HSM. The HSM may also have an internal API which may be called by the adjunct API.

HSM receives the request for validation from payment processing server . The HSM may be implemented as a plug in card within a host computer system or as a physically external device such as one connected via Universal Serial Bus USB Small Computer System Interface SCSI fibre channel Ethernet and the like . A HSM may include a tamper resistant physical package a general purpose processor executing cryptographic functions or processor optimized for cryptographic operations. An HSM may have dedicated memory onboard provide secure storage of keys and have functionality for code signing to enforce access control lists ACL . The HSM provides a hardened environment for cryptographic operations. Among others one suitable HSM is the nShield device from nCipher Corporation Ltd of Cambridge United Kingdom and the Luna device from SafeNet Inc. of Belcamp Md. United States.

A database server storing information for use by the validation server is shown. The database server contains one or more processors and memory. While shown as being external to the validation server the database server may be within the validation server.

An HSM encrypted secret for example a credit card number is stored in the database server memory in ciphertext. In this example the ciphertext string is 1rigy771s. Validation data is also stored in the database server memory. The validation data may include valid Bank Identification Number BIN ranges comparison strings hash algorithms checksums algorithms and the like. Validation data may be stored encrypted in plaintext or a combination.

HSM decrypts the HSM encrypted secret to produce a cleartext version of the secret a cleartext secret within the HSM for validation. In this example the cleartext secret is represented by the string AMARISE . HSM outputs validation results to validation server and returns the validation results to payment processing server .

Payment processing server may now transmit validated data to the settlement server for settlement of funds. The settlement server may be within the organization or be part of another organization such as a credit card company bank intermediate settlement processing agency and the like. Use of a validation server prior to transmittal to the settlement server offers several advantages. It is common for settlement servers to charge transaction fees for each piece of payment information for which settlement or validation is attempted. For example a credit card company may charge for every card number submitted for settlement regardless of whether the card number is valid. By validating data prior to transmittal an organization can avoid transactional fees for attempting to validate otherwise invalid data. Additionally validation prior to transmittal to a settlement server can increase processing speed of payment information allowing a faster experience to end users of the organization.

All of the computer systems described herein including payment processing server the validation server the HSM and database server may contain one or more processors as well as memory including but not limited to RAM ROM EEPROM flash memory or other memory technology CD ROM digital versatile disks DVD or other optical storage magnetic cassettes magnetic tape magnetic disk storage or other magnetic storage devices or any other computer readable storage medium which can be used to store the desired information and which can be accessed by one or more processors.

A validate data module upon request for data validation received from validation server calls upon the HSM to decrypt and validate the data. This validation may require access of information outside of the HSM internal memory.

When fulfilling a validation request requiring data outside of the HSM the HSM may request an HSM encrypted secret from database server . A determination of which HSM encrypted secret to be accessed may be aided by the use of a previously issued token. A token is used to reference a particular piece of confidential data which may be encrypted or unencrypted but the token itself is not itself necessarily encrypted. A token may contain no information other than that it is a referent. The token may have been previously issued as a result of operations within the HSM .

In some implementations the return order of a plurality of requested HSM encrypted secrets may be randomized . The return order is the sequence in which data is output from the HSM. Randomizing as used in this application includes any operation which results in an output sequence which differs from the original input. A hardware random number generator HRNG or pseudorandom number generator within the HSM may implement randomization. Randomizing the order of data returned by the HSM increases the difficulty of associating a particular input to the HSM with a particular output from the HSM and compromising the confidential data or the system. This renders an attack on the data based correlation of inputs and outputs more difficult thus hardening the system.

For example payment processing server send three requests A B and C to the validation server for validation. Requests A B and C are received and passed along to the HSM for processing. Typically those requests may be processed in the order received first in first out in this example A B and C. However randomization processing order module may change the order of processing. In this example requests may be processed in order C A B thus affecting the order of the output returned. A return order randomization module may take validation results and randomize their order of output from the HSM. The return order randomization module may be used with or instead of the randomizing processing order module.

Within the HSM a process identifier or other identifier is then used to retain the association between the cleartext secret being processed and the validation data being retrieved for validation.

HSM encrypted secret is decrypted by decryption module within the HSM producing cleartext secret . In this example the cleartext string AMARISE is now present within the HSM and available for validation checking.

Validation check module accepts the cleartext and validates the data using a variety of business rule validation tools. In one implementation a Bloom filter may be used by the validation check module to validate data against business rules. Other business rule validation checks that may additionally or alternatively be used include a Luhn mod 10 check a BIN range check checksum a length check and or other relevant checks used to validate payment types including credit cards debit cards charge cards stored value cards electronic benefit transfer cards and the like. Checksums comparison of strings hashing algorithms and the like may also be used to validate data. For example a validation check may compare data to be validated with a list of valid data or apply a hashing algorithm to the data to be validated and compare the resulting hash with a pre determined value.

As described above validation may require the use of validation data stored outside of the HSM. Because memory in an HSM is generally smaller than that of a dedicated database server 200 MB compared to terabytes for example requests to external data sources may occur. Thus validate check module may send a request for validation data stored outside of the HSM . However in other implementations the HSM may include sufficient memory that requests to external data sources are not necessary.

A randomization access module varies the sequence of data access by the HSM to further obscure what data is being validated within the HSM . A request for validation data from the HSM to database server returns validation information to the HSM .

Certain acts in need not be performed in the order described may be modified and or may be omitted entirely depending on the circumstances. For example only the randomization of processing order may take place or randomizing access to validation data blocks or both as described above.

At a request for validation of data is received by a validate data module which calls on functions in the HSM . At an HSM encrypted secret is received from external storage in the database server .

At the processing order of a plurality of HSM encrypted secrets is randomized. This randomization obscures the relationship between data being input into the HSM and data being output from the HSM to further harden security of the system.

At the requested validation data blocks external to the HSM which are necessary to validate the cleartext are randomized. This randomization obscures the relationship between data being input into the HSM and data being output from the HSM to further harden security of the system. The requests are passed to the database server which returns the requested validation data .

At a validation check on the cleartext is performed. This validation data may utilize one or more of a variety of validation methods including but not limited to those described below.

At a Bloom filter is shown for validation. A Bloom filter is a space efficient probabilistic data structure used to test whether an element is a member of a set. Because of the space efficient nature of the Bloom filter the Bloom filter function and data structure may be stored entirely within the HSM memory to further safeguard data with validation occurring within the HSM and without reference to data external within the HSM. The HSM may also use a learning Bloom filter. A learning Bloom filter accepts known good data or defined exceptions and builds a data structure for validation of unknown data to be validated.

At B the Bank Identification Number BIN range may be checked for validity in the case of credit cards debit cards charge cards stored value cards electronic benefit transfer cards and the like.

At C the length of a data to be validated may be checked i.e. 16 digits required for a valid credit card number.

At N other validation procedures may be used including hash functions string comparison and so forth.

Certain acts in method need not be performed in the order described may be modified and or may be omitted entirely depending on the circumstances. For example the randomization of processing order may occur before HSM encrypted secrets are read . As another example the validation check on cleartext data may take place and then request data from external storage which would then call on randomizing access to validation data blocks . Also only the randomization of processing order may take place or randomizing access to validation data blocks or both as described above.

The validation server is shown encompassing validate data module . The validate data module is coupled to the HSM .

Data blocks are data blocks indicating what validation data is necessary to complete validation in the HSM . For example data blocks may include blocks A B and C listed in the sequence generated for processing.

A randomization access module varies the sequence in which data is accessed by the HSM to further obscure what information is being validated within the HSM . In this example the randomization access module changes the order of blocks requested.

The order of data blocks requested is randomized the randomized order now being B C and A. Randomization may include varying the order of data blocks inserting blocks for data not undergoing validation or the like.

Randomized data block request is sent to the database server . The database server returns the requested validation data to the HSM .

Certain acts in method need not be performed in the order described may be modified and or may be omitted entirely depending on the circumstances. For example the method may feedback all or a portion of the order of requested blocks into the randomization access module .

Moreover any of the acts of any of the methods described herein may be implemented at least partially by a processor or other computing device based on instructions stored on one or more computer readable media. Computer readable media can be any available media that can be accessed by a processor. By way of example and not limitation computer readable media may comprise volatile and nonvolatile removable and non removable media implemented in any method or technology for storage of information such as computer readable instructions data structures program modules or other data. Computer storage media includes but is not limited to RAM ROM EEPROM flash memory or other memory technology CD ROM digital versatile disks DVD or other optical storage magnetic cassettes magnetic tape magnetic disk storage or other magnetic storage devices or any other medium which can be used to store the desired information and which can accessed by the processor. Combinations of the any of the above should also be included within the scope of computer readable media.

Although the subject matter has been described in language specific to structural features and or methodological acts it is to be understood that the subject matter defined in the appended claims is not necessarily limited to the specific features or acts described. Rather the specific features and acts are disclosed as illustrative forms of implementing the claims. For example the methodological acts need not be performed in the order or combinations described herein and may be performed in any combination of one or more acts.

