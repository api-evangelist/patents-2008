---

title: Clustering aggregator for RSS feeds
abstract: A method for merging really simple syndication (RSS) feeds. Stories containing one or more terms may be merged into one or more clusters based on one or more links between the stories. A cluster frequency with which the terms occur in each cluster may be determined. A diameter for each cluster may be determined. A cluster that is most similar to one of the clusters may be determined based on the cluster frequency. The most similar cluster with the one of the clusters may be determined based on each diameter, and each cluster frequency.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07958125&OS=07958125&RS=07958125
owner: Microsoft Corporation
number: 07958125
owner_city: Redmond
owner_country: US
publication_date: 20080626
---
Weblogs also known as blogs are attracting a lot of attention due to the rapid growth of really simple syndication RSS technology. A powerful feature of RSS is that users may subscribe to their favorite blogs through RSS feeds. RSS feeds provide users details about updates to blogs without the user having to actually visit the blogs. Today about 11 or about 50 million Internet users are regular blog readers. Approximately 75 000 new RSS feeds and 1.2 million new stories are posted daily.

Described herein are implementations of various technologies for a clustering aggregator for really simple syndication RSS feeds. In one implementation a pool of uniform resource identifiers URIs is aggregated from users that subscribe to RSS feeds and the URIs are aggregated from a number of popular RSS feeds. The RSS feeds may be crawled periodically to determine content that is updated between crawls.

The updated content may also be aggregated and then organized within a hierarchy based on topical relationships between the different items or stories of the aggregated content. The hierarchy may contain several levels of clusters. At the bottom level of the hierarchy the clusters may include stories that are topically related to each other. At higher levels of the hierarchy the clusters may contain lower level clusters that are topically related.

The hierarchy may in turn be analyzed in order to label each cluster with a topic that is appropriate for the cluster. The content of the stories words terms and phrases may be compared to the content of other stories within the same cluster s to determine the appropriate topics.

In another implementation the cluster hierarchy may be refreshed to account for shifts in the topics discussed described or contained within the stories for the RSS feeds. In refreshing the cluster hierarchy stories that age beyond a time window may be purged and the cluster may be reorganized according to the remaining stories.

The above referenced summary section is provided to introduce a selection of concepts in a simplified form that are further described below in the detailed description section. The summary is not intended to identify key features or essential features of the claimed subject matter nor is it intended to be used to limit the scope of the claimed subject matter. Furthermore the claimed subject matter is not limited to implementations that solve any or all disadvantages noted in any part of this disclosure.

As to terminology any of the functions described with reference to the figures can be implemented using software firmware hardware e.g. fixed logic circuitry manual processing or a combination of these implementations. The term logic module component or functionality as used herein generally represents software firmware hardware or a combination of these implementations. For instance in the case of a software implementation the term logic module component or functionality represents program code or declarative content that is configured to perform specified tasks when executed on a processing device or devices e.g. CPU or CPUs . The program code can be stored in one or more computer readable media.

More generally the illustrated separation of logic modules components and functionality into distinct units may reflect an actual physical grouping and allocation of such software firmware and or hardware or may correspond to a conceptual allocation of different tasks performed by a single software program firmware program and or hardware unit. The illustrated logic modules components and functionality can be located at a single site e.g. as implemented by a processing device or can be distributed over plural locations.

The terms machine readable media or the like refers to any kind of medium for retaining information in any form including various kinds of storage devices magnetic optical solid state etc. . The term machine readable media also encompasses transitory forms of representing information including various hardwired and or wireless links for transmitting the information from one point to another.

The techniques described herein are also described in various flowcharts. To facilitate discussion certain operations are described in these flowcharts as constituting distinct steps performed in a certain order. Such implementations are exemplary and non limiting. Certain operations can be grouped together and performed in a single operation and certain operations can be performed in an order that differs from the order employed in the examples set forth in this disclosure.

The computing system may include one or more client computers one or more web servers and an aggregator server . The client computer may provide a user with an interface through which the user may read content that is provided via really simple syndication RSS feeds . The RSS feeds are described in greater detail in the paragraphs below.

Each of the web servers may host one or more websites. A website may be a collection of content such as web pages images videos or other digital assets accessible via the Internet. The web servers may record updates to website content in the RSS feeds .

The aggregator server may aggregate the RSS feeds into a central location for access by the user on the client computer . The aggregator server may further organize content described in the RSS feeds to provide topical information about the content to the user.

The web server may include a central processing unit CPU a system memory a storage a network interface and a system bus that couples various system components to the CPU . Although only one CPU is illustrated in the web server it should be understood that in some implementations the web server may include more than one CPU .

The system bus may be any of several types of bus structures including a memory bus or memory controller a peripheral bus and a local bus using any of a variety of bus architectures. By way of example and not limitation such architectures include Industry Standard Architecture ISA bus Micro Channel Architecture MCA bus Enhanced ISA EISA bus Video Electronics Standards Association VESA local bus and Peripheral Component Interconnect PCI bus also known as Mezzanine bus.

The system memory may include a read only memory ROM a random access memory RAM and a basic input output system BIOS none of which are shown . The BIOS may contain the basic routines that help transfer information between elements within the web server such as during start up.

The storage may include a hard disk drive for reading from and writing to a hard disk a magnetic disk drive for reading from and writing to a removable magnetic disk and an optical disk drive for reading from and writing to a removable optical disk such as a CD ROM or other optical media. The hard disk drive the magnetic disk drive and the optical disk drive may be connected to the system bus by a hard disk drive interface a magnetic disk drive interface and an optical drive interface respectively. The drives and their associated computer readable media may provide nonvolatile storage of computer readable instructions data structures program modules and other data for the web server . Neither the drives nor their respective interfaces are shown in .

Although the web server is described herein as having a hard disk a removable magnetic disk and or a removable optical disk it should be appreciated by those skilled in the art that the web server may also include other types of computer readable media that may be accessed by a computer. For example such computer readable media may include computer storage media and communication media.

Computer storage media may include volatile and non volatile and removable and non removable media implemented in any method or technology for storage of information such as computer readable instructions data structures program modules or other data.

Computer storage media may further include RAM ROM erasable programmable read only memory EPROM electrically erasable programmable read only memory EEPROM flash memory or other solid state memory technology CD ROM digital versatile disks DVD or other optical storage magnetic cassettes magnetic tape magnetic disk storage or other magnetic storage devices or any other medium which can be used to store the desired information and which can be accessed by the web server .

Communication media may embody computer readable instructions data structures program modules or other data in a modulated data signal such as a carrier wave or other transport mechanism and may include any information delivery media. The term modulated data signal may mean a signal that has one or more of its characteristics set or changed in such a manner as to encode information in the signal.

By way of example and not limitation communication media may include wired media such as a wired network or direct wired connection and wireless media such as acoustic RF infrared and other wireless media. Combinations of any of the above may also be included within the scope of computer readable media.

Further the web server may operate in a networked environment using logical connections to one or more remote computers such as the client computer and the aggregator server . The logical connections may include the network interface connected to a network . The network may be any network or collection of networks such as enterprise wide computer networks intranets local area networks LAN and wide area networks WAN . In one implementation the network may be the Internet.

A number of program or data modules may be stored in the system memory and the storage . More specifically the storage may include the web pages and the RSS feed .

The RSS feed may include descriptions of recent updates to the web pages . Updates may include new web pages or additions to existing web pages . The RSS feed may contain a title a description and a uniform resource identifier of the updated content. In one implementation the RSS feed may contain the text of the updated content. The updated content may be described within the RSS feed in a standardized extensible markup language XML file format.

It should be noted that the RSS feed is merely one example of a format of syndicated feeds also known as web feeds . Any data format may be used that provides users with information about frequently updated content whether provided on the Internet or another network.

Additionally the system memory may include an operating system and a web server application . The operating system may be any suitable operating system that may control the operation of a networked personal or server computer such as Windows Vista Mac OS X Unix variants e.g. Linux and BSD and the like.

The web server application may be a computer program that is responsible for accepting hypertext transfer protocol HTTP requests from web clients such as an RSS client . The web server application may then provide HTTP responses that include data content. The data content may include the web pages and or the RSS feeds that the RSS client displays for the user.

The aggregator server may be constructed similarly to the web server . The aggregator server may include a central processing unit CPU a system memory a storage a network interface and a system bus that couples various system components to the CPU .

A number of program modules and data may be stored in the system memory and the storage . More specifically the system memory may include an operating system and a clusgator . The clusgator may be an application that aggregates and organizes the RSS feeds within stories and a cluster hierarchy respectively.

The clusgator may crawl the RSS feeds and aggregate the updated content within the stories . Each story may represent one item of updated content. The stories may include all the information from the RSS feed . In one implementation the stories may include data from the web pages for which the updates are noted in the RSS feeds . Such data may include the text of the update and even hyperlinks within the updated web pages .

The storage may include subscriptions the stories the cluster hierarchy and parameters . The users may subscribe to the RSS feeds to keep current with updates to frequently visited websites without having to actually visit the website. The subscriptions may contain one or more users subscriptions in the form of uniform resource identifiers URIs of the websites to which the users subscribe.

The parameters may contain adjustable variables and other data to facilitate the functionalities of the clusgator such as crawling the RSS feeds and organizing the stories into the cluster hierarchy .

In one implementation the parameters may contain URIs of websites not included in the subscriptions . In such an implementation the clusgator may also crawl these additional websites to collect the stories . The parameters are described in greater detail with reference to .

The cluster hierarchy may include one or more levels of topically related clusters . The clusters may each be described with a topic . The lowest level of the cluster hierarchy may include clusters of stories . The upper levels of the cluster hierarchy may include clusters of lower level clusters .

Each cluster within the cluster hierarchy may group stories or clusters that are topically related to each other. In one implementation the cluster may only contain one story or one cluster if the story or cluster is not topically related to other stories or clusters .

The client computer may also be constructed similarly to the web server . The client computer may include a central processing unit CPU a system memory a storage a network interface and a system bus that couples various system components to the CPU .

Additionally the user may enter commands and information into the client computer through input devices . The input devices may include devices such as a keyboard and pointing device. Other input devices may include a microphone joystick game pad satellite dish scanner or the like. These and other input devices may be connected to the CPU through an serial port interface coupled to the system bus but may be connected by other interfaces such as a parallel port game port or a universal serial bus USB .

One or more output devices may also be connected to the system bus via an interface such as a video adapter. The output devices may include a display monitor or other peripheral output devices such as speakers and printers.

A number of program modules may be stored in the system memory . More specifically the system memory may include an operating system and an RSS client . The RSS client may be a user interface that provides information about the RSS feeds through the display of the cluster hierarchy . Additionally the RSS client may enable the user to view the stories identified in the cluster hierarchy by providing links to the stories within the displayed cluster hierarchy .

In one implementation the RSS client displays the clusters and all included stories of the cluster hierarchy that contain the stories from the user s subscribed feeds. Additionally the RSS client may display the upper level clusters within the cluster hierarchy if more than one lower level cluster within the upper level cluster is displayed. In one implementation the display of the clusters includes the topic for the cluster .

Because one RSS feed may describe different stories within the same website and each of the stories may be topically distinct the stories from the same RSS feed may be distributed across several clusters . Advantageously the user may discriminate among stories within a single RSS feed by only viewing stories that are organized into clusters with the topics that interest the user. Additionally the user may discover new RSS feeds because topically related stories in other RSS feeds may be displayed within the same cluster of the cluster hierarchy as the stories in the user s subscribed feeds.

At step the clusgator may crawl the RSS feeds of the websites whose URIs may be contained in the subscriptions and the parameters . When creating the cluster hierarchy the clusgator may perform an initial crawl of the RSS feeds that aggregates updates within a predefined period such as the prior 3 days. The predefined period may be stored within the parameters . When maintaining the cluster hierarchy the clusgator may perform a daily crawl whereby updates within the prior day may be aggregated.

At step the clusgator may cluster the stories . Clustering the stories may create the clusters by merging together the stories that are topically related in the lowest level of the cluster hierarchy . Merging together the clusters that are topically related may create additional levels of the cluster hierarchy . The number of levels within the cluster hierarchy may vary according to the parameters of a particular implementation.

In one implementation the clusgator may periodically purge the stories that are older than the predefined period and refresh the cluster hierarchy by clustering the stories aggregated from the crawl with the stories remaining from within the predefined period.

When crawling the RSS feeds only aggregates updates from the prior day clustering the stories may be an incremental clustering. Incremental clustering may cluster the stories aggregated from the prior day s updates to the lowest level of the existing cluster hierarchy . The clustering methods are described in greater detail with reference to . Incremental clustering specifically is described with reference to .

At step the clusgator may extract topics for the clusters . By extracting the topics the clusgator may provide a descriptive title for each of the clusters within the cluster hierarchy . After incremental clustering only the clusters that are updated to include the stories aggregated from the daily crawl may undergo topic extraction.

In contrast to text documents the stories from RSS feeds may have natural link structure. Though the links may be sparse the natural link structure may provide a basis for creating an initial set of the clusters . Given a set of n stories these stories can be represented by a graph G V E where vertices V may represent the stories and edges E may represent the links between stories . Since the link structure may be highly sparse the graph G may be composed of a set of m connected sub graphs. Suppose all these m sub graphs are G G G . . . G. If graph G G V E has size n then it may be that

However the link clustering may create clusters with noisy links. The noisy links may be links between the stories that are not topically related. In other words the noisy link may merge unrelated stories within the same cluster .

At step the clusgator may remove the noisy links. By removing the noisy links the clusgator may refine the topical relationship between the stories within each of the clusters . The method for removing noisy links is described in greater detail with reference to .

Steps may be repeated for each level of the cluster hierarchy . The link clustering may also present another problem missing links. The missing links may represent the stories that are topically related but do not have links between them. In other words the missing link problem may leave topically related stories in different clusters . To resolve the missing links at step the clusgator may merge the clusters that are topically related.

The first pass of steps may address the missing link issue by creating a second level of the cluster hierarchy where the clusters that are topically related are merged. Additional levels within the cluster hierarchy may then be created in subsequent passes whereby the clusters merged in a prior pass may be merged into larger clusters . The method for merging clusters is described in greater detail with reference to .

At step terms for all of the stories may be determined. The terms may include all the words within the titles and descriptions for the stories . The terms may then be pared down by removing stopwords. The terms may also be stemmed.

Steps may be repeated for each of the stories . At step a vector of weights may be determined for all of the terms. The weights may be assigned according to a Term Frequency and Inverse Document Frequency algorithm.

Steps may be repeated for each link between the stories . At step the similarity between two linked stories may be determined. In one implementation the similarity may be determined using a cosine similarity formula as follows 

where vand vrepresent term vectors for stories i and j respectively and Sim v v is the similarity between stories i and j.

At step the similarity may be compared to a global threshold. If the similarity between vectors i and j is less than the global threshold at step the cluster containing stories i and j may be split. The global threshold may be defined within the parameters . In one implementation the global threshold 0.415 where 0

In another implementation the global threshold may be determined by producing an average similarity for each of the clusters . The average similarity for one cluster may be the average similarity of every link within the cluster . In such an implementation the global threshold may be determined to be the smallest of the average similarities for all the clusters .

Steps may be repeated for each of the clusters in one level of the cluster hierarchy . At step a centroid vector for the cluster may be determined. The centroid vector also referred to herein as the centroid may be a term vector for the cluster that contains the average weights of the term vectors for every story in the cluster . In other words the average weight may be the total amount of weights for all the stories in the cluster divided by the total amount of stories in the cluster .

The cluster diameter r may be the maximum similarity with which 100 percent of stories in the cluster may have a similarity with cthat is greater than r. The similarity may be determined according to the formula described with respect to . According to the above described formula each of the clusters may have a different diameter. The cluster diameter is described in greater detail in the paragraphs below.

It should be noted that may be one of the parameters whereby the cluster diameters may be customized for each particular implementation. The may be customized according to an expectation that 100 1 percent of the stories remaining after removing noisy links within each of the clusters may be noisy.

Steps may be repeated for each of the clusters . At step the clusgator may determine which of the clusters in the same hierarchy level as the current cluster is most similar to the current cluster i.

The clusgator may determine the similarity between the cluster i and the other clusters according to the formula described in wherein the centroid of each of the clusters is used in place of the term vectors. The cluster that is most similar may be the cluster j that has the highest similarity.

At step if the centroids of the cluster i and the cluster j may not belong to each other s cluster the method may return to step . For the centroids of clusters i and j to be able to belong to each other the centroids of clusters i and j may be within each other s diameter and the similarity of the clusters i and j may be greater than the global threshold. In other words Sim maxmin r

If the centroids of the clusters i and j may belong to each other at step the clusters i and j may be merged.

At step the centroid of the cluster produced by merging the clusters i and j may be determined. The cluster resulting from the merging of the clusters i and j may be referred to herein as the new cluster . At step a simple diameter calculation may be used to determine the diameter of the new cluster . The simple diameter calculation may be used in place of the formula described at step in order to attenuate computational costs of the method . The simple diameter calculation for the new cluster may be min r r .

At step the diameters of all the newly merged clusters may be re calculated according to the formula described with reference to step . The method may then be repeated to create higher levels within the cluster hierarchy . In one implementation at each recursion of the method the global threshold parameter may be reduced to account for the reduced similarity between the clusters merged at higher and higher levels of the cluster hierarchy .

Steps may be repeated for each of the stories newly aggregated during the daily crawl described with reference to . At step the clusgator may determine the term vector for the story .

At step if the story has links to the stories within any of the clusters at step the cluster containing the story that is most similar may be determined.

At step if the similarity between the story and the centroid of the cluster is greater than the global threshold at step the story may be added to the cluster . As stated previously the similarity may be determined according to the formula described with reference to . At step the centroid for the cluster may be re calculated to account for adding the story to the cluster .

Alternately if the similarity of the story to the cluster does not exceed the global threshold the method may proceed to step . Similarly if at step the story does not have links to any of the clusters the method may proceed to step .

At step the cluster with the centroid most similar to the story may be determined. If the similarity between the story and the centroid is greater than the global threshold the method may proceed to step described above.

If the similarity between the story and the most similar centroid is not greater than the global threshold at step a new cluster may be created that contains the story . The method may then return to step .

After all the stories newly aggregated have been evaluated for incremental clustering at step the diameters of the clusters in the upper levels of the cluster hierarchy may be re calculated. The diameters may be determined according to the formula described with reference to at step .

At step the clusgator may determine all two term phrases for all the stories . Steps may then be repeated for each of the stories . At step a bi gram vector may be determined for the story . The bi gram vector may be a vector of weights accorded to each two term phrase in the story . The weights in the bi gram vector may be determined according to the Term Frequency and Inverse Document Frequency algorithm.

Steps may then be repeated for each of the clusters . At step an inter class scatter matrix may be determined for the cluster referred to herein as cluster G. The inter class scatter matrix may provide the average story distance between the cluster Gand all of the cluster s sibling clusters. The sibling clusters may be all the clusters merged with the cluster Gto form an upper level cluster. The sibling clusters are also referred to herein as G. The average story distance may be an approximation of how many of the two term phrases are shared between the cluster Gand its sibling clusters. In order to attenuate the likelihood that the topics are duplicated the clusgator may maximize the average story distance between the cluster Gand its sibling clusters.

is the mean of all the siblings of the cluster G and nis the number of stories in one of the clusters G.

At step the clusgator may determine an intra class scatter matrix for the cluster G. The intra class scatter matrix may provide the average story distance between the all the children clusters within the cluster G. The children clusters may be all the clusters that are merged to form the cluster G. Depending on the level of the cluster Gwithin the cluster hierarchy the children clusters within the cluster Gmay be stories or clusters . In order to increase the likelihood that the topic determined for the cluster Grelates to all the children clusters the clusgator may minimize the average story distance between the children clusters of the cluster G. The intra class scatter matrix may be determined as follows 

where vmay be the bi gram vector of the stories within the cluster G or the centroid of bi gram vectors for children clusters.

At step the clusgator may determine the topic for the cluster . In order to maximize the average story distance between the sibling clusters and the cluster G and minimize the average story distance between the children clusters of the cluster G the clusgator may determine the largest element in traceS i S i . Because the trace function is the sum of the elements on the main diagonal the diagonal from the upper left to the lower right the largest element in traceS i S i may be determined by the largest element in S i S i . As such the clusgator may determine that the topic to be the two term phrase in the associated bi gram vector that is in the same dimension as the largest element in S i S i .

It should be understood that the various technologies described herein may be implemented in connection with hardware software or a combination of both. Thus various technologies or certain aspects or portions thereof may take the form of program code i.e. instructions embodied in tangible media such as floppy diskettes CD ROMs hard drives or any other machine readable storage medium wherein when the program code is loaded into and executed by a machine such as a computer the machine becomes an apparatus for practicing the various technologies. In the case of program code execution on programmable computers the computing device may include a processor a storage medium readable by the processor including volatile and non volatile memory and or storage elements at least one input device and at least one output device. One or more programs that may implement or utilize the various technologies described herein may use an application programming interface API reusable controls and the like. Such programs may be implemented in a high level procedural or object oriented programming language to communicate with a computer system. However the program s may be implemented in assembly or machine language if desired. In any case the language may be a compiled or interpreted language and combined with hardware implementations.

Although the subject matter has been described in language specific to structural features and or methodological acts it is to be understood that the subject matter defined in the appended claims is not necessarily limited to the specific features or acts described above. Rather the specific features and acts described above are disclosed as example forms of implementing the claims.

