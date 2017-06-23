---

title: Method for loading credentials into a mobile communication device such as a mobile phone
abstract: The invention relates to a personal token () for being associated with a mobile telecommunication device () and for storing credentials for access to an operator's network, characterized that the personal token () is arranged for loading the credentials into a memory () of the mobile telecommunication device (), so that the mobile telecommunication device () is taken away from the personal token () and operative for connecting to the operator's network with the credentials in its memory ().
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08483661&OS=08483661&RS=08483661
owner: Gemalto SA
number: 08483661
owner_city: Meudon
owner_country: FR
publication_date: 20081202
---
The invention relates to mobile communications and to personal tokens carrying credentials for access to such mobile communications.

The invention relates in particular to smart cards and mobile phones associated therewith but many other personal tokens may replace the smart card such as USB tokens mass memory cards USB enabled SIMs. The invention relates in particular to mobile voice communication and to other types of mobile communications such as videoconference mobile internet mobile TV or mobile broadcasting.

The personal tokens used for access to mobile communications are usually considered as representing the operator identity to the end user. They contain the credentials for access to the network of the operator and specific applications of the operator.

Moreover the personal token is usually considered as a device that should be easily separated from the handset and plugged into another. Thanks to the personal token the operator can keep a certain level of independence regarding the handset maker.

From the handset point of view the smart card is a simple external container hosting credentials performing basic cryptographic operations and storing some user specific data such as phonebook entries. For a handset manufacturer the SIM card is just another peripheral performing tasks that he could easily do itself and would like to do itself for reducing the cost and complexity inherent to association of personal tokens with mobile devices.

The invention aims at proposing an alternate scheme to usual personal tokens which alternate scheme allows to keep the portability benefits of usual personal tokens and reduces the cost and complexity inherent to association of personal tokens with mobile devices.

The smart card of is a 7816 3 shaped smart card containing a set of necessary data for connection to a mobile operator s network. The card comprises a secret key which is necessary for responding to a key challenge from the operator. The key challenge consists in a random being sent to the device and a specific response being sent in response using the secret key. The key is well known by the operator having sent the key challenge so that the response to be sent is expected by the operator.

The card comprises the cryptography algorithm which is necessary for computing the response to the key challenge by making use of the secret key.

In addition to the secret key and the authenticating algorithm the card stores a set of administrative data organized in the memory of the smart card in a tree shaped structure.

Those administrative data comprise name of the mobile operator IMSI i.e. International Mobile Subscriber Identifier ICCID MSISDN i.e. subscriber dialing number attached to the card etc. . . . All these administrative data may be named the GSM file system due to its tree shaped type of organization .

IMSI KI ICCID MSISDN and any other data inherent to the specific smart card may be considered as credentials which are necessary for the mobile phone to connect to the network. The remaining usual data necessary for connecting to the network and which are stored in the tree shaped structure are considered as administrative data i.e. data that are not inherent to the particular end user.

The present smart card comprises an engine for loading the different above mentioned administrative data and credentials into a handset i.e. more precisely for copying the said information to the memory of a handset.

For this purpose the card is associated with a handset having a mirror engine . The mirror engine is able to read the credentials and administrative data in the card and store them in a protected area of the memory of the handset which is configured for storing such information. Further fetching of administrative information and credentials is performed by the handset in its own memory at each new power on of the mobile handset and a new connection of the handset to the mobile network is permitted.

The transfer engine of the card fetches the credentials and administrative data from the protected memory of the card and from a particularly secure part of the protected memory which stores the secret key Ki and copies them into a buffer of the card and then activates a modulator for the modulator to modulate the credentials and administrative data on an antenna of the card once a triggering signal and a corresponding magnetic energy is received from the handset .

The handset engine triggers a modulator of the antenna of the handset for sending a modulated magnetic signal to the card which provides the necessary power to the card for sending back the credentials and administrative data. The handset engine further reads the data that are received by the handset and are demodulated by the demodulator of the handset and the engine then routes the credentials and administrative data to corresponding parts of the memory of the handset thereby reconstructing the tree structure in a protected part of the memory of the handset which tree structure comprises the administrative data and the IMSI ICCID MSISDN and other credentials apart from the secret key Ki and placing the Ki value on a particularly secure part of the protected memory . The protected memory is in particular protected against DPA and repetitive type attacks.

Of course many other schemes are possible for a card to make its administrative data and credentials or a copy thereof ready for a transfer to the handset which may comprise use of a buffer or not read commands originating from the handset or not making the data available in the form of packets or in the form of a continuous flow of data requiring an authentication for each packet of data or requiring an authentication for the whole set of data the card may send a signal to the handset indicating that the data are ready or the handset may send a repetitive requiring signal for the data until the data are ready etc.

Both the handset and the card comprise authentication modules for a mutual authentication prior to the credentials and administrative data to be loaded. Authentication of the smart card by the handset allows the handset to protect itself from accepting any information which may be fraudulous into its secured area and prevents the handset from accepting smart cards which may originate from a mobile operator for which the handset is not intended.

Authentication of the handset by the card allows the card to ensure that the handset is a secure and authorized device and not a device originating from a fraudulous entity the purpose of which is to fraudulously use the credentials of the smart card.

The authentication may be based on a handset based list of identifiers for authorized IMSIs and on a smart card based list of authorized handsets for example a list of IMEIs International Mobile Equipment identifiers of authorized handsets.

Once mutual authentication is performed the credentials and the administrative data are read from the card and loaded onto the handset more precisely here copied from card to handset.

In the present embodiment the card is a contactless card i.e. a card having an embedded antenna and able to transfer information by magnetic modulation through this antenna for example by means of an embedded modulator coupled with the antenna.

The handset is enabled for contactless communications with the card i.e. it is equipped here with an antenna and a modulator for receiving and sending information from and to the card.

The communication between the card and the handset may be made through electrical contacts either inside a usual slot for SIM cards either in a specific slot such as a USB female connector for a USB key as a personal token.

The transfer of information through contactless communication is encrypted by means of a common encrypted key particular to the handsets and cards of the consider mobile operator and which is pre memorized in the card and the handset.

In an alternate encryption embodiment for the secured transfer of information a shared secret is created at the time the card and the token get connected each other which consists in a real time created encryption key that is used for such transfer only. Hence the shared secret is not known by any other device so that no other device is able to spy the transfer of information due to the fact that the encryption key has not been pre stored in any memory but has been created especially for the transfer of information at the time of it.

As described above the shared secret is generated for example with a random generator hosted in the handset which may alternately be hosted in the card and which generates a random then adopted as the secret key and transmitted therefore to the card where it is stored in a secure part of the memory of the card.

Once the credentials and the administrative data are loaded onto the handset the card can be taken away from the handset. The credentials and the administrative data are stored in a protected part of the memory of the handset and the secret key Ki is stored in a particularly secure part of the protected memory. The protected memory is protected against different types of attacks such as DPA . . . attacks laser attacks multiple queries attacks etc.

Secure memory hardware for a handset may be bases on the TPM . . . technology or a technology such as the one used in contactless payment applications for mobile phones.

Although the administrative data are loaded onto the card with the credentials in the present example in an alternate embodiment the handset is pre stored with the administrative data for at least one operator. In such case the credentials are the only necessary data to be loaded onto the handset.

The transfer of credentials and or administrative data may be considered as a personalization of the handset in the same way as personalization is performed onto a card in a card manufacturer s factory.

The present card is enabled for depersonalizing the handset by momentarily associating the card with the handset i.e. by getting the card close to the handset.

Preferably for the benefit of interoperability among any type of handset and card data exchanges between the card and the handset as performed during personalization and depersonalization should be done through a generic API application programming interface.

As described above at the end of the transfer of the credentials and administrative data the card also gets locked into a state which prevents the card from personalizing any other handset. The card can be unlocked into the original state i.e. the state where the card is available for personalizing a handset only if it is associated again with the personalized handset . The handset gets depersonalized by such new associating step.

Preventing the card from personalizing another handset prevents a potential thief of the card to personalized a plurality of handset which would become a fraudulous handset for each of them.

Locking of the handset from being depersonalized prevents that the handsets looses its unlocking ability which would induce that the card can no more be used because no more possibility would exist to use it for personalizing of a new handset.

Furthermore locking the handset prevents a thief from being tempted to steel the handset in order to sell it for being used with new credentials. The handset would then refuse any further personalization and the account of the end user corresponding to original credentials would be locked at the operator s size thereby definitely blocking the personalized and locked handset.

A flag is stored in a secure memory of the card which flag can not be reached by any non authorized device which flag gets into a status which indicates to the processor of the card that is no more able to transfer any credential to any external device.

The same mechanism exists in the handset i.e. a flag in a secure part of the memory of the handset indicates to the processor of the handset that it is not authorized to get rid of the credentials which are stored in the memory of the handset.

For the handset the locking flag can be modified only if the card which has been associated therewith is once again associated therewith. For the card the locking flag can be modified only if the handset which has been associated therewith is once again associated therewith again.

Any of these two lockings is independent of the other and in alternate embodiments only one of these two lockings or not lockings may be implemented.

In order to depersonalize the handset the card is brought in close area to the handset in the same way as a contactless card in brought close to a contactless reader and the depersonalizing process starts immediately.

For the purpose of securing the depersonalizing of the handset the card and the handset generate a shared secret key while they are associated for the personalizing and this shared secret is memorized inside the handset and the card. The shared secret is generated only for the purpose of the associated one time personalizing and the associated one time depersonalizing of the handset i.e. it is generated at the time the card and handset are associated for the first time and it did not exist prior to the association of the card with the handset.

Once the card is in close vicinity with the handset the handset detects presence of the card and then checks whether the card stores the shared secret. The handset sends a random data to the card and waits for the result of a predetermined calculation which makes use of the shared secret which result is already known by the handset because it stores the same shared secret. If the result sent by the card to the handset is the one which is expected then the card is recognized by the handset .

In a same way the card checks whether the handset stores the shared secret. The card sends a random data to the handset and waits for the result of a predetermined calculation which makes use of the shared secret which result the card already knows because the card stores the same shared secret. If the result sent by the handset to the card is the one which is expected then the handset is recognized by the card.

After this mutual recognition the credentials and or administrative data are extracted from the handset i.e. the credentials get deleted from the memory of the handset . The credentials and or administrative data may be written back into memory of the card or may be simply deleted from the memory of the handset especially in the present case where credentials and or administrative data were not suppressed from the memory of the card at the original transfer of credentials and or administrative data from card to handset.

In addition a transfer of personal data is carried out at the depersonalization step which consists in copying personal data from card to handset and deleting them from the handset. These personal data are generated during the use of the handset while being used under personalization with the current card.

Such personal data comprise entries of a phonebook as stored by the end user in the memory of the handset contents of SMSs received and sent content of MMS photo portfolios etc. . . . Such use of the card for backing up personal data allows to provide the same portability as a usual card hosted inside a handset. When the owner of the present card associates the card with a new phone the credentials administrative data and personal data are transferred to the new phone in the frame of the personalization of the new handset.

In the present embodiment the memory of the card comprises a section which is dedicated to storing applications such as java applets gathered in java packages or any kind of midlets. The content of this section of the memory of the card is downloaded into the memory of the handset during the above described personalization and a considered downloaded application is activated by the handset for example when the operator sends an activating command to the handset at any time after personalization.

The such applications content is deleted from the handset at the above described depersonalization step.

