---

title: Aggregating content from multiple services
abstract: An exemplary embodiment involves receiving, by a processor, a selection of a contact from a requestor. The exemplary embodiment further involves identifying, by the processor, multiple services to which the contact subscribes and to which the requestor subscribes. Subscribing to each service comprises creating a profile comprising authentication information and associating with the profile one or more content items provided by the service. Identifying the multiple services comprises identifying, for each service that a first profile of the contact is associated with a second profile of the requestor. The exemplary embodiment further involves communicating, by the processor, with the multiple services to identify content to identify content that is provided by one or more of the multiples services and that is associated with the contact. The exemplary embodiment further involves generating, by the processor, a preview indicating the content associated with the contact.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08745481&OS=08745481&RS=08745481
owner: Adobe Systems Incorporated
number: 08745481
owner_city: San Jose
owner_country: US
publication_date: 20080227
---
This application is related to U.S. patent application Ser. No. 12 038 480 entitled CONTACT INFORMATION MANAGEMENT filed on the same day as the present application the entire teachings of which are incorporated herein by this reference.

The web has developed dramatically over the past several years. It is now easier than ever for persons all around the world to communicate with each other and exchange personal information.

For example social networking websites are popular ways of enabling persons having similar interests or activities to easily communicate with each other over the world wide web. Social networking services are primarily web based and provide numerous ways for users to interact with each other. Modes of communicating as supported by a social networking service can include chatting messaging emailing video playback voice chatting file sharing blogging discussion groups and so on.

Certain social networking services enable a user to maintain a directory of contacts so that upon visiting the social networking website the user can keep track of his or her friends. Depending on the service a directory can include identities of persons such as a group of former classmates persons that are part of a club chat room friends etc. Thus at least one service provided by a social networking website is the ability to manage a directory of friends or relations that also subscribe to the service. A respective service typically maintains a directory of friends for a corresponding subscriber as a private collection of contact information accessible only by the subscriber.

Although the directory of friends may be private the personal information associated with the persons listed in a directory may be publicly available.

In certain cases a user of a respective service needs a user name and password to log onto a social networking service. After authentication of the user by the service the user can have access to his or her directory of friends. Thus social networking services may provide at least some level of protection for private information even though subscribers profiles are typically publicly available.

In addition to providing access to and use of a directory of friends a social networking service can be configured to enable each of the users of the service to create a corresponding user profile e.g. a web page of information that is accessible by other users of the social networking service. Each subscriber can modify his or her profile to include personal or favorite information associated with the corresponding subscriber. As mentioned above the profile information for each of the subscribers of the service may be publicly available to other users of the social networking service. In certain cases a user profile can include contact information such as telephone e mail address etc. for contacting the user. Special privileges may be required to access the contact information.

A user profile can also include accessible content or content links which the user has chosen to include as a part of his or her profile. For example a profile can include text such as blogs personal information links to other web pages etc. The content may also include various media or links thereto such as audio video FLASH media files and so on.

Upon visiting a social networking service a user can access his or her directory of friends. If desired the user can view profile information associated with the persons listed in the user s directory of friends by retrieving an information page associated with the selected friend or friends.

Conventional management of content and content links suffer from a variety of deficiencies. For example currently there is no efficient way for a user to manage and view content associated with multiple contacts that subscribe to multiple different networking services other than to manually and separately visit each site and if desired manually retrieve the content and or links associated with a given contact for playback. Manually accessing content such as web pages audio clips video clips links etc. associated with multiple contacts from multiple different services can be very tedious and time consuming.

Techniques discussed herein deviate with respect to conventional applications. For example as will be discussed further certain specific embodiments herein are directed to a computer and or network environment in which a user has access to content information associated with different contacts via use of a content information aggregator having access to multiple remote services. As will be discussed the content information aggregator simplifies a user s online experience by enabling the user to more easily view analyze interact with etc. content information associated with his or her contacts.

In a general example embodiment a content information aggregator receives selection of a contact. In response to selection of the contact the content information aggregator identifies multiple services to which the contact subscribes. The content information aggregator communicates with the multiple services to retrieve content information associated with the contact. By way of a non limiting example the content information can include content and content references available from the contact s profile information residing at the multiple different services. The content information can specify content stored at locations other than the multiple services as well. The content information aggregator retrieves the content information from such services and potentially content and or reference to content from the sources other than the multiple services.

After identifying different content information associated with the contact the content information aggregator generates a preview based on the content information associated with the contact. The preview can include a display of the content information associated with the contact such as the contact s favorite URL Uniform Resource Locator links selectable thumbnails representing retrievable content associated with contact content associated with the contact etc.

In one embodiment the aggregator enables a viewer to initiate play back of content associated with the contact based on input commands with respect to the preview. For example a viewer can select different display regions of the preview to initiate retrieval and playback of corresponding content associated with the contact. Such an embodiment is useful because rather than having to manually visit each of multiple different websites e.g. MySpace Facebook etc. to identify content information associated with a contact a user can use the content information aggregator as described herein to visit one or more services to obtain content information associated with a selected contact and thereafter play back or view content associated with the selected contact.

Thus based on these and other embodiments as further described herein a user can more efficiently manage content information associated with one or more contacts having content information stored at multiple disparate locations over a network. As will be discussed the content aggregator can support additional functions other than just content information aggregation and generation of a preview. Accordingly the content aggregator also can be considered a content information manager.

Embodiments herein provide useful ways for managing information. For example according to embodiments herein a subscriber can quickly view which content his or her friends have also been viewing or content in which his or her friends have indicated as being of interest Inherently a user is likely to have similar tastes and preferences as his or her friends. Based on this premise certain embodiments herein enable a user to conveniently view a preview of content that has been identified as preferred or enjoyable content by one or more of the user s contacts. Thus embodiments herein can provide a more efficient online experience by mitigating the need to blindly peruse the Internet in an attempt to find enjoyable content.

Note that embodiments herein can include a configuration of one or more computerized devices websites hosted services workstations handheld or laptop computers or the like to carry out and or support any or all of the method operations disclosed herein. In other words one or more computerized devices or processors can be programmed and or configured to include a content information aggregator and or related functions as explained herein to carry out different embodiments of the invention.

Another embodiment of the present disclosure is directed to a computer program product that includes one or more tangible computer readable media having instructions stored thereon for supporting operations such as retrieval and display of content information associated with a subscriber s contacts. The instructions and thus method as described herein when carried out by a processor of a respective computer device cause the processor to i receive a selection of a contact ii identify multiple services to which the contact subscribes iii communicate with the multiple services to identify content associated with the contact and iv generate a preview to indicate the content associated with the contact.

Of course the numbering of the above steps has been added for clarity sake these steps may not need to be performed in any particular order.

Also it is to be understood that each of the systems methods etc. herein can be embodied strictly as a software program as a hybrid of software and hardware or as hardware alone such as within a processor or within an operating system or within a software application or via a non software application such a person performing all or part of the operations. Example embodiments of the invention may be implemented in products and or software applications such as those manufactured by Adobe Systems Incorporated of San Jose Calif. USA.

As discussed above techniques herein are well suited for use in software applications supporting aggregation and playback of content associated with multiple contacts and multiple services. However it should be noted that embodiments herein are not limited to use in such applications and that the techniques discussed herein are well suited for other applications as well.

Additionally although each of the different features techniques configurations etc. herein may be discussed in different places of this disclosure it is intended that each of the concepts can be executed independently of each other or in combination with each other. Accordingly the present invention can be embodied and viewed in many different ways.

Note also that this summary section herein does not specify every embodiment and or incrementally novel aspect of the present disclosure or claimed invention. Instead this summary only provides a preliminary discussion of different embodiments and corresponding points of novelty over conventional techniques. For additional details and or possible perspectives of the invention and embodiments the reader is directed to the Detailed Description section and corresponding figures of the present disclosure as further discussed below.

According to embodiments herein via a graphical user interface a user can select a contact from a listing of multiple contacts. The listing of multiple contacts can be derived as a result of collecting contact information from multiple different services to which the user subscribes.

The contact selected from the listing can have content information available from one or more different services such as multiple social networking websites to which the selected contact subscribes. In response to selection of the contact from the listing a content aggregator communicates with the multiple different services over a network to retrieve content information associated with the contact. By way of a non limiting example the retrieved content information from the multiple services can specify content links content references etc. associated with the contact.

The content aggregator processes the content information from the multiple services and initiates display of the content information associated with the contact.

As further discussed below aggregation and display of content information associated with a selected contact in this way enables a user to more easily view content associated with a contact than conventional methods which require the user to manually and individually visit each of multiple different social networking services to view such information.

More specifically is an example diagram illustrating a network environment supporting aggregation of content information and generation of preview information according to embodiments herein.

As shown network environment includes network subscriber subscriber system graphical user interface content information aggregator repository and services . Services include service service and so on.

In the example configuration in the content information aggregator includes a contact handler content information retriever and preview generator . The repository includes a listing of identified contacts e.g. contact contact . . . contact N and associated services to which the contacts subscribe. Additionally each of the services maintains at least one contact profile associated with a corresponding contact . For example contact profile is associated with contact contact profile is associated with contact . . . contact profile N is associated with contact N. By way of a non limiting example each of the contact profiles can represent personal information managed by a respective contact for rendering of a corresponding web page associated with a contact.

More specifically each contact profile can include content and corresponding display rules associated with its associated contact . As shown contact in service can include content A11 and content B11. By way of a non limiting example the content as specified by a corresponding contact profile can include or provide a link to information such as video data audio data images etc. Additionally each contact profile can include corresponding display rules indicating how to display the corresponding content associated with a profile when the profile and related information is displayed to a viewer.

Note that for the example configuration of the content nomenclature is defined as follows Content ID Service ID Contact ID. That is for example at least a portion of content associated with contact profile in service is denoted as content A21. The letter A in A21 indicates a content ID of A. The number 2 in A21 indicates a service ID of 2. The number 1 in A21 indicates a contact ID of 1.

The display rules nomenclature is defined as follows Service ID Contact ID. Thus as an example the display rules for contact profile in service are denoted as display rules 12. The number 1 in 12 indicates a service ID of 1. The number 2 in 12 indicates a contact ID of 2. Details and use of the display rules are discussed further below with respect to .

In a similar manner as discussed in related application Ser. No. 12 038 480 entitled CONTACT INFORMATION MANAGEMENT filed on a same day as the present application the content information aggregator of the current disclosure of communicates with the services to identify contacts associated with the subscriber . The content information aggregator initiates display of a listing of the multiple contacts to the subscriber . The listing of contacts can be displayed in graphical user interface . Accordingly the subscriber can view identities of different contacts.

The subscriber selects a contact from the listing of contacts. In this example the selected contact is denoted by selection . In turn the subscriber system transmits the selection to the content information aggregator over network . Logical path represents transmission of the selection to the content information aggregator .

Assume for this example embodiment that the selection indicates that the subscriber selected contact for viewing of content information associated with selected contact .

The contact handler of content information aggregator receives and processes the selection transmitted from subscriber system . In order to determine the services associated with the selection the contact handler queries repository . The repository in the example configuration of maintains contact data that cross references contacts with his or her respective service subscriptions. In other words the repository stores contact information indicating which different services to which the corresponding contacts subscribe. Based on this information the content information aggregator can identify which services to initiate communications for retrieval of content information associated with a selected contact .

In the present example the data entry for contact in repository indicates that contact subscribes to service and . Each of these identified services therefore should have corresponding content information associated with the contact .

To retrieve content information from a respective service for the selection the content information aggregator may need password and username information. In one embodiment the repository includes appropriate authentication information such as without limitation a username password etc. for each service so that the content information aggregator can gain access to content information at the different services for the selection . In such an embodiment the authentication information can be the same information that a the subscriber would manually log onto a respective service and view via a web browser profile information associated with the selected contact.

Assume in this example that the contact handler of the content information aggregator accesses repository and identifies that the selected contact has corresponding content information available from service and service as mentioned above. The contact handler saves this information as contact information .

The contact handler makes the contact information available to the content information retriever . By way of a non limiting example the contact information can include an identity of the selection the identity of any associated services associated with the contact pointer or location address for each service authentication information for each service etc.

As its name suggests the content information retriever retrieves content information associated with the selection . Thus based on use of the contact information the content information retriever is able to identify locate and log on to the specific services associated with the selection .

Typically each service has an Application Programming Interface API that enables the content information aggregator to communicate with and access content from each service.

Recall in this example that contact profile represents content information associated with contact . Content information associated with the selection is therefore available from both service and service .

Based on the contact information the content information retriever communicates with each of services and to retrieve content information associated with the selection . For example the content information retriever requests service to provide content information associated with the selection . The content information retriever also requests service to provide content information associated with the selection . By way of a non limiting example the content information can include any content information associated with the selection such as links to information associated with the contact such as the contact s favorite web pages links to retrievable content playable content metadata audio files video files display rules indicating how to present content information to a viewer etc.

In this example the content information retriever can retrieve any or all of the content information associated with the selection such as content A11 content B11 display rules 11 content D21 content A21 display rules 21 etc. from the services as specified by contact information .

In response to retrieving the content information from the services the content information retriever stores the retrieved content information as content information . The preview generator utilizes the content information as retrieved from services to create a preview for viewing by the subscriber . Logical path in indicates transmission of any data required to initiate display of preview on graphical user interface .

Upon receiving the preview the subscriber system renders preview information such as preview A11 preview B11 preview D21 and preview A21 etc. in graphical user interface .

Preview A11 displayed in graphical user interface represents a preview of content A11 associated with the selected contact as retrieved from service preview B11 represents a preview of content B11 associated with the selected contact as retrieved from service preview D21 represents a preview of content D21 associated with the selected contact as retrieved from service preview A21 represents a preview of content A21 associated with the selected contact as retrieved from service and so on.

Thus in response to selection of a particular contact such as contact the content information aggregator can initiate retrieval of content information associated with the selected contact from multiple services. The content information aggregator initiates via preview generator display of one or more previews of the content information associated with the selected contact in graphical user interface .

Note that display rules for indicating how to display the content information in the previews can be obtained from a number of different sources such as the subscriber and or contact. For example the subscriber can provide display rules indicating how to display content information associated with a selected contact.

As another example the content information retriever can retrieve in addition to content information such as content and or content links associated with the selection as stored at services the content information retriever can retrieve display rules 11 and or display rules 21 that have been pre defined by the contact to be used for generating the preview of the contact s content in graphical user interface . Thus the contact can have some control as to how to present the contact s content information to a viewer.

It should be appreciated that retrieval of content information associated with one or more contacts from multiple services the content information aggregator alleviates the need for the subscriber to perform a piecemeal login to each of multiple different services to manually retrieve content associated with a given contact for viewing.

As will be discussed further with respect to each preview can include selectable references that enable the subscriber to choose which if any content associated with the contact the subscriber wishes to retrieve and view in their entirety. Thus in one embodiment the preview information displayed in graphical user interface may only be a summary view specifying different content associated with a respective contact.

As shown service list includes services . By way of a non limiting example service can represent a service such as FACEBOOK service can represent a service such as MYSPACE service can represent a service such as LINKEDIN and so on.

For those services to which the subscriber subscribes the content information aggregator communicates with each service to identify the subscriber s contacts at those services . This is described in related United States patent Application entitled CONTACT INFORMATION MANAGEMENT as incorporated by reference above.

In the context of the present example contact list includes contacts such as contact Katerina Darling contact Sawyer Griffin contact Jonah Hill contact Jolie Hu contact Vegas Lory and so on. These entries in contact list represent different contacts that can be selected by the subscriber for viewing corresponding content information. Each of the contacts in contact listing can have corresponding content information stored at one or more of the same or different services as discussed above.

In the context of the example embodiment of assume that the user has made selection such as by clicking on contact Vegas Lory in contact listing in order to view the more detailed information regarding this contact.

In response to the selection of contact Vegas Lory from contact list the subscriber system sends the selection to content information aggregator as mentioned above in . Based on the selection the content information aggregator retrieves content information from services subscribed to by Vegas Lory and then populates the corresponding display region in the screenshot of with content information associated with the selection namely contact Vegas Lory in this example.

By way of a non limiting example display region includes a first preview region illustrating a preview of example photo content associated with Vegas Lory. Display region includes a second preview region including video content associated with Vegas Lory. To view content information associated with another contact the subscriber makes another selection such as by clicking on another contact in contact listing . Accordingly the subscriber can view content information associated with any selected contact.

As shown network environment includes network contacts e.g. contact . . . contact N and associated contact systems . Contact systems include contact system . . . contact system N such as a computer laptop workstation etc. providing access to network and services . Network environment further includes content information aggregator with associated content information retriever and preview generator .

Services include service service . . . service M. By way of a non limiting example the services can represent social networking services repositories web pages etc. through which the contacts manage and or store his or her content information.

In the context of the present example a contact represents an entity that has a corresponding contact profile stored with a corresponding service. In other words each of the contacts subscribes to one or more services that store content information associated with the respective contact. Such services can be configured to enable the contacts users to manage his or her corresponding content information.

Via communications over network a contact user can upload and or create content information for inclusion in his or her corresponding contact profile. For example assume that a contact user uploads his or her favorite songs or movies or links to his or her favorite songs or movies to a corresponding MYSPACE profile. By doing so other users of the MYSPACE service having access to the contact user s profile can identify which songs or movies are preferred by the contact user.

Thus in the context of contact user provides over network content information including content A11 content B11 and display rules 11 to the contact user s corresponding contact profile on service . Contact profile includes content information associated with another contact in network environment .

In this particular embodiment service has a service interface enabling the contacts and subscriber to access contact profiles associated with different entities such as contacts . Logical path represents a communications path enabling contact to manage his or her content information in his or her respective contact profile at service .

In a similar manner as discussed above for contact each of the contacts in network environment can manage his or her profile information at the different services .

In accordance with the previous example embodiments the content information retriever of content information aggregator communicates with the appropriate services associated with a given contact to retrieve content information associated with the contact. For example the content information retriever communicates with service to access contact profile to retrieve content information such as content A11 content B11 display rules 11 etc. Logical path represents such an access.

In a manner as discussed above the content information retriever retrieves the content information associated with the given contact from multiple services having a contact profile associated with the given contact. Based on the retrieved content information associated with the given contact the preview generator of content information aggregator creates a corresponding view by communicating over network with the subscriber system as discussed above in .

More specifically the first example preview configuration includes a first column for indicating content information associated with contact and a second column for indicating content information associated with contact . Each contact column is further delineated by the services subscribed to by each respective contact. For example contact includes corresponding regions for displaying content information retrieved from service and service . Similarly contact includes corresponding regions for indicating content information retrieved from service and content information retrieved from service .

In this non limiting example preview information A B E and F are of a content type such as music preview C D G and H are of a content type such as photos and preview J and K are of a content type such as videos. As shown when content information associated with multiple contacts is shown in accordance with preview configuration the content information is first categorized by service. Then for each service the preview information is sorted and displayed by type.

Preview configuration is similar to preview configuration except that the content previews are not initially delineated by service. Instead the content preview information is first assorted by type regardless of the service from which the corresponding content information is retrieved. This configuration may provide a more unified representation since the previews are grouped irrespective of the services from where they originated. It should be noted however that the associated service identity may still be indicated for respective preview information so that a view can identify from which service the preview information pertains.

More specifically screenshot includes first preview second preview and third preview . Preview indicates content information associated with a first selected contact preview indicates content information associated with a second selected contact preview indicates content information associated with a third selected contact and so on.

In one example embodiment a subscriber can select the three contacts such as Katerina Sawyer and Jonah from the contact list in order to invoke the corresponding previews for each contact in screenshot . Each of the previews and can correspond to a different contact. For example profile can include information associated with Katerina Darling profile can include information associated with Sawyer Griffin and profile can include information associated with Jonah Hill.

Preview displays content information associated with a first contact. By way of a non limiting example preview includes first content type region to display weather information second content type region to display PHOTOSHOP content information third content type region to display ADOBE MEDIA PLAYER content information and fourth content type region to display thumbnails of movie trailers.

Preview displays content information associated with a second contact. By way of a non limiting example second preview includes first content type region to display weather information second content type region to display ADOBE DIGITAL EDITIONS content third content type region to display music content and fourth content type region to display concert content.

Preview displays content information associated with a third contact. By way of a non limiting example third preview further includes first content type region to display financial information second content type region to display PHOTOSHOP content third content type region to display ADOBE DIGITAL EDITIONS content and fourth content type region to display proximity content.

As shown each of profiles and for different respective contacts in can include different types of content information in accordance with content information associated with the contacts at the different services.

Also note again that the content information in screenshot is shown as a non limiting example and that previews can vary depending on the information retrieved from the different services for the contacts. Thus embodiments herein are not limited to the example configuration provided by screenshot in .

In the present example the display region of preview includes content preview content preview and content preview . Similarly display region of profile includes content preview content preview and content preview .

Each of the content previews and correspond to content that is retrievable by the viewer clicking on the corresponding content preview. In other words each preview can have a corresponding associated link in which to retrieve content as represented by the preview. Thus underlying each selectable content preview can be a link to the content. Both the link and corresponding image displayed in a preview can be obtained from one of the multiple services.

Additionally note that the services can provide content information specifying a remote location from which to retrieve content for display in screenshot . For example the information displayed in preview can include information from a remote website as specified by the content information for a given contact. Accordingly each of the previews for different contacts can be generated based on content received from the services as well as other sources in a network.

Note that a service from where the content preview originated is typically but not necessarily one in which both the subscriber and the different contacts have subscribed. In other words a contact can select a number of favorite links to websites and or content available on the Internet. As mentioned this information can be displayed in the contact s profile page. Embodiments herein enable retrieval of information from the different services so that a respective subscriber can more easily keep track and or maintain of favorite content associated with the different contacts.

Note that in certain embodiments the collection or aggregation command to obtain content information associated with one or more contacts isn t necessarily a direct command input by subscriber but is rather more of a passive pre set scheduled setting whereby the content information aggregator performs aggregation of content information associated with one or more contacts on a regular or random basis such as once a day once a week etc. Thus in such embodiments when aggregation occurs repeatedly over time as a result of scheduling the subscriber can be apprised of the most up to date contact information without having to repeatedly issue collection or aggregation commands to collect content information.

Such a scheduled setting can reside in the content information aggregator or remotely with respect to the content . The scheduled settings can indicate the times in which the contact information manager is to initiate communications with the multiple services .

By way of a non limiting example the user can configure the content information aggregator via schedule settings to automatically collect or aggregate contact information from the services on a scheduled basis. In other words a user can create a schedule indicating when to perform collection of content information associated with one or more contacts.

As an alternative non limiting example a source other than the user such as a network administrator scheduling policy etc. can configure the content information aggregator to automatically perform a collection or aggregation of contact information from the services on a scheduled basis.

Note that the following discussion provides a basic embodiment indicating how to carry out functionality associated with the content information aggregator as discussed above and below. However it should be noted that the actual configuration for carrying out the content information aggregator can vary depending on a respective environment. For example as previously discussed computer system can include one or multiple computers that carry out the processing as described herein.

Note also that each of subscriber system services etc. as previously discussed also can be configured as one or more computers including a processor and corresponding instructions to carry out the operations as described herein.

As shown computer system of the present example includes an interconnect that couples a memory system a processor I O interface and a communications interface .

I O interface provides connectivity to peripheral devices if such devices are present such as a keyboard mouse display screen etc. In one embodiment the computer system is a server that manages and aggregates contact information and content information as described herein.

Communications interface enables the content information aggregator process of computer system to communicate over network to receive input from a subscriber access content information associated with one or more contacts initiate display of a content preview etc.

As shown memory system is encoded with content information aggregator application that supports functionality as discussed above and as discussed further below. Content information aggregator application and or other resources as described herein can be embodied as software code such as data and or logic instructions such as code stored on a tangible computer readable medium media etc. Execution of the code supports processing functionality according to different embodiments described herein.

During operation of one embodiment processor accesses memory system via the use of interconnect in order to launch run execute interpret or otherwise perform the logic instructions of the content information aggregator application . Execution of the content information aggregator application produces processing functionality in content information aggregator process . In other words the content information aggregator process represents one or more portions of the content information aggregator performing within or upon the processor in the computer system .

It should be noted that in addition to the content information aggregator process that carries out method operations as discussed herein other embodiments herein include the content information aggregator application itself. The content information aggregator application may be stored on a computer readable medium such as a floppy disk hard disk or in an optical medium. According to other embodiments the content information aggregator application can also be stored in a memory type system such as in firmware read only memory ROM or as in this example as executable code within the memory system . Memory system can be configured as RAM Random Access Memory .

In addition to these embodiments it should also be noted that other embodiments herein include the execution of the content information aggregator application in processor as the content information aggregator process . Thus those skilled in the art will understand that the computer system can include other processes and or software and hardware components such as an operating system that controls allocation and use of hardware resources.

Functionality supported by computer system and more particularly functionality associated with content information aggregator will now be discussed via flowcharts in . For purposes of the following discussion the content information aggregator or other appropriate entity generally performs steps in the flowcharts.

More particularly is an example flowchart illustrating operations associated with a content information aggregator according to embodiments herein. Note that flowchart of and corresponding text below may overlap with and refer to some of the matter previously discussed with respect to . Also note that the steps in the below flowcharts need not always be executed in the order shown.

In step the content information aggregator receives a selection of a contact. For example a user of the content aggreagator can be presented with a list of from which to choose and then the user selects a specific contact from the contact list.

In step content information aggregator identifies multiple services to which the selected contact subscribes.

In step the content information aggregator communicates with the multiple services to identify content information associated with the contact. As previously mentioned a services can include an Application Programming Interface API that enables the content information aggregator to communicate with and access data from the services. As previously discussed in one embodiment the content information aggregator logs onto a service using authentication information and accesses contact information as if the user had logged on themselves.

In step the content information aggregator generates a preview to indicate the content associated with a selected contact.

In step the content information aggregator retrieves a set of content information such as content content references etc. from a first service of the multiple services to identify first content associated with a selected contact.

In step the content information aggregator retrieves a set of content references such as content content references etc. from a second service of the multiple services to identify second content that has been associated with the selected contact.

In step the content information aggregator initiates display of preview information associated with the first content and preview information associated with the second content in a graphical user interface.

In step the content information aggregator communicates with multiple services to retrieve content information associated with a selected contact.

In step the content information aggregator retrieves a first link from a first service of the multiple services. Assume that the first link points to a corresponding portion of content associated with the selected contact. By way of a non limiting example the first link can be a uniform resource locator.

In sub step the content information aggregator renders the preview to include a first selectable display region.

In sub step the content information aggregator associates the first link with the first selectable display region such that subsequent selection of the first display region enables retrieval and playback of the content via use of the first link. In other words if a user selects the first display region in the preview the content information aggregator initiates retrieval of the content as specified by the first link. The content information aggregator initiates playback in a graphical user interface.

Note that the content information aggregator can retrieve additional links from the services. For example in furtherance of the embodiment above the content information aggregator can communicate with the multiple services to retrieve a second link from a second service of the multiple services. Assume that the second link points to another corresponding portion of content associated with the selected contact. Based on the second link the content information aggregator then generates the preview to include a rendition of the window that includes a second selectable display region and an association between the second link and the second selectable display region such that the subsequent selection of the second display region enables retrieval and playback of content via use of the second link. In this way a preview window as generated by the content information aggregator can include any number of content references for respective contacts.

Those skilled in the art will understand that there can be many variations made to the operations of the user interface explained above while still achieving the same objectives of the invention. Such variations are intended to be covered by the scope of this invention. As such the foregoing description of embodiments of the invention are not intended to be limiting. Rather any limitations to embodiments of the invention are presented in the following claims.

