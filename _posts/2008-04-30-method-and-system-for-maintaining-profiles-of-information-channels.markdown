---

title: Method and system for maintaining profiles of information channels
abstract: A method and system are provided for maintaining profiles of information channels available on the Web, wherein the information channels are accessed via pull-only protocols. The method includes monitoring one or more channels by a channel pull action at a monitoring rate, wherein the monitoring rate is determined for the one or more channels based on the number of update events in a previous time period. The method may optimally include filtering the update events in the time period by a novelty measure, wherein the filtering disregards events that do not include significant novel information. The monitoring rate is adapted based on reinforcement learning applying iterative learning rules over time.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07970739&OS=07970739&RS=07970739
owner: International Business Machines Corporation
number: 07970739
owner_city: Armonk
owner_country: US
publication_date: 20080430
---
This invention relates to the field of information management. In particular the invention relates to maintaining profiles of information channels on the Web.

Much of the content on the Web is available through syndication channels which need to be actively monitored to maintain an up to date profile of their published information over time. Such monitoring is essential for next generation of Web 2.0 applications that provide sophisticated search and discovery services over Web information channels. A channel s profile can change over time due to the dynamic nature of the channel. Therefore maintaining a fresh channel profile is extremely difficult especially under the constraint of a limited monitoring budget.

The number of diverse information channels available on the Web is rapidly increasing. It spans many different knowledge domains such as news stock and market reports auctions and more recently channels containing data gathered from Blogs or Wikis. Recent advances in Web technology such as the improved access capabilities to channels and the availability of new data delivery mechanisms for disseminating the channel content have resulted in the emergence of more advanced client side Web applications.

These applications require sophisticated manipulation of channels on the Web including the discovery search and recommendation of relevant channels. Such applications include various Web 2.0 mashups and situational applications in general which integrate data that is gathered from several different possibly inter related channels. An imperative task for developers of such applications is to locate relevant channels that will maximize the benefit gained from their applications.

A crucial step toward the support of such advanced services over channels is the ability to capture the essence of each Web channel. This can be done using channel profiles. A channel profile is a compact representation of the channel content which can be used to summarize and capture the main characteristics of the content published on this channel. Profiles can simplify the way relevant channels can be located and can be used to match application requirements against the available set of channels managed by the system.

Maintaining channel profiles is challenging due to several reasons. First channel content is usually dynamic as in the case of Web feeds where the content is continuously changing sometimes at a daily or even hourly rate. Because the profiles of such channels may continually change over time capturing the dynamic trends of the channel content is extremely difficult.

Second the majority of channels on the Web are available nowadays for access via pull only protocols while most servers refrain from supporting push protocols due to scalability issues. Previous work on novelty detection in data streams and data stream summarization assume that the stream of updates to a channel is pushed into the system. By contrast in a pull based scenario each channel is required to be actively monitored in order to maintain enough snapshots to construct a fresh and reliable profile of its content. The freshness of maintained profiles therefore directly depends on the rate at which channels are monitored. Moreover different channels may have different rates at which novel content is being published on them thus profiles of different channels may change at a different possibly even non regular rate.

Third in the pull based scenario channels may be volatile meaning that novel content published over time has a limited lifespan during which it is available on the channel. Such data volatility is very common in Web feeds where channels have a limited capacity for the number of feed entries that are maintained on the feed. Such limitation is further determined by the feed popularity and the feed provider update policy e.g. an overwrite policy for which the provider maintains only the last newest entries of the feed . Therefore monitoring the channel profiles in a pull setting is challenging where it is hard to predict the moments when novel content which may result in a significant profile change is published on such volatile channels and is still available for access.

Finally channel monitoring can be constrained either due to limited system resources such as bandwidth memory or CPU central processing unit or due to monitoring restrictions set by the channel providers themselves sometimes termed politeness constraints due to heavy workloads imposed by multiple client access. Therefore the number of channels that can be monitored in parallel is further limited and requires efficient utilization of the allocated resources for the maintenance of fresh profiles.

According to a first aspect of the present invention there is provided a method for maintaining profiles of information channels available on the Web wherein the information channels are accessed via pull only protocols the method comprising monitoring one or more channels by a channel pull action at a monitoring rate wherein the monitoring rate is determined for the one or more channels based on the number of update events in a previous time period.

Preferably the method includes filtering the update events in the time period by a novelty measure wherein the filtering disregards events that do not include significant novel information.

The monitoring rate may be adapted based on reinforcement learning applying iterative learning rules over time.

The filtering may determine if update events include significant novel information by evaluating an update event s influence on channel cohesion and disregarding update events with high similarity to an information channel s current profile. The method may include setting a threshold parameter to control the amount of novelty filtering. The threshold parameter may be a similarity of an update event to the information channel s current profile below which update events are disregarded.

The method may include monitoring multiple channels wherein the monitoring rate is refined based on inter channel profile similarities.

The method may further include maintaining a similarity matrix with entries corresponding to the average profile similarity between two channels during a given time period.

Where the method includes monitoring multiple channels the M most important channels may be monitored at any moment in time wherein the importance of a channel may be determined as a channel with a higher monitoring rate. Alternatively M randomly selected channels may be monitored at any moment in time.

The length of the previous time period in which the update events are monitored may be varied to optimize the quality of results against resource use.

According to a second aspect of the present invention there is provided a computer software product for maintaining profiles of information channels available on the Web wherein the information channels are accessed via pull only protocols the product comprising a computer readable storage medium storing a computer in which program comprising computer executable instructions are stored which instructions when read executed by a computer perform the following steps monitoring one or more channels by a channel pull action at a monitoring rate wherein the monitoring rate is determined for the one or more channels based on the number of update events in a previous time period.

According to a third aspect of the present invention there is provided a method of providing a service to a client over a network for maintaining profiles of information channels available on the Web wherein the information channels are accessed via pull only protocols the service comprising monitoring one or more channels by a channel pull action at a monitoring rate wherein the monitoring rate is determined for the one or more channels based on the number of update events in a previous time period.

According to a fourth aspect of the present invention there is provided a system for maintaining profiles of information channels available on the Web wherein the information channels are accessed via pull only protocols the system comprising means for determining a monitoring rate for one or more channels based on a number of update events in a previous time period and means for monitoring one or more channels by a channel pull action at a monitoring rate.

The system may include a novelty filter to filter the update events in the time period wherein the novelty filter disregards events that do not include significant novel information. The system may further include means for setting a threshold parameter to control the amount of novelty filtering.

The means for determining a monitoring rate may include a reinforcement learning mechanism to apply iterative learning rules over time.

The means for monitoring may include monitoring multiple channels wherein the means for determining the monitoring rate includes means for refinement based on inter channel profile similarities. The means for monitoring may include monitoring multiple channels wherein the M most important channels are monitored at any moment in time wherein the importance of a channel is determined as a channel with a higher monitoring rate. Alternatively M randomly selected channels may be monitored at any moment in time.

The system may include means for varying the length of the previous time period in which the update events are monitored to optimize the quality of results against resource use.

Most current Web monitoring solutions derive monitoring rates based solely on the raw update rates of Web channels. Thus such solutions may consume superfluous resources and therefore may fail to scale.

The present described method considers also the rate of content change published on these channels to improve the monitoring policy. For this purpose a learning scheme is suggested based on novelty detection for Web channels in pull only settings. More specifically some of the contributions can be stated as follows.

It will be appreciated that for simplicity and clarity of illustration elements shown in the figures have not necessarily been drawn to scale. For example the dimensions of some of the elements may be exaggerated relative to other elements for clarity. Further where considered appropriate reference numbers may be repeated among the figures to indicate corresponding or analogous features.

In the following detailed description numerous specific details are set forth in order to provide a thorough understanding of the invention. However it will be understood by those skilled in the art that the present invention may be practiced without these specific details. In other instances well known methods procedures and components have not been described in detail so as not to obscure the present invention.

Referring to an example embodiment is shown of a system for application of a profile management system for Web channels. illustrates the architecture of such a system shown as monitoring multiple channels for a client .

The system includes pull protocol adapters a profile management system and a service application programming interface API . The profile management system monitors channels and accesses the content published on the channels using the pull protocol adapters e.g. using HTTP Hypertext Transfer Protocol GET calls .

The profile management system includes a monitor a profiler and a search index . The profile management system also includes a means for determining a monitoring rate for applying the methods as described in detail. The means for determining the monitoring rate may include a learning mechanism and a history component which is updated after every monitoring probe as described further below. The means for determining the monitoring rate may also include an optional novelty filter and an optional inter channel comparison mechanism if more than one channel is monitored.

In the profile management system the content gathered by the monitor is delivered to the profiler that is responsible for updating the channel profile and generating a fresh profile for the channel s content. The profile is then updated in the search index . The profile management system exposes a convenient service API for clients to search and locate relevant channels for their application needs.

The profile management system can further match the client requirements which might also be submitted as a user profile to the system against the current channel profiles available in the system to recommend relevant channels that can satisfy the client s needs.

A mashup application is a web application that combines data from more than one source into a single integrated tool. Clients of a profile management system may consist of various mashup applications that need to discover the most relevant channels to be used as inputs and outputs of the different mashup components. Other clients may consist of different Web feed readers that search for relevant feeds according to their user profile which describes the user s information interests. Moreover the profile management system can recommend new sources for clients helping them discover new relevant channels that they would not be aware of otherwise.

The monitor of the profile management system has a limited amount of available resources for the task of maintaining fresh channel profiles thus it is required to monitor the channels efficiently to maximize system capability and cope with the management of multiple channels. To do so the monitor uses the means for determining the monitoring rate to set the rate at which each channel should be monitored and how to schedule the limited allocated monitoring system resources in the most efficient way. In what follows monitoring policies are described tailored for this specific task i.e. maintaining good representative channel profiles that best reflect the channel content under the constraints of limited computational resources.

Referring to an exemplary system for implementing a profile management system as shown in includes a data processing system suitable for storing and or executing program code including at least one processor coupled directly or indirectly to memory elements through a bus system . The memory elements can include local memory employed during actual execution of the program code bulk storage and cache memories which provide temporary storage of at least some program code in order to reduce the number of times code must be retrieved from bulk storage during execution.

The memory elements may include system memory in the form of read only memory ROM and random access memory RAM . A basic input output system BIOS may be stored in ROM . System software may be stored in RAM including operating system software . Software applications may also be stored in RAM .

The system may also include a primary storage means such as a magnetic hard disk drive and secondary storage means such as a magnetic disc drive and an optical disc drive. The drives and their associated computer readable media provide non volatile storage of computer executable instructions data structures program modules and other data for the system . Software applications may be stored on the primary and secondary storage means as well as the system memory .

The computing system may operate in a networked environment using logical connections to one or more remote computers via a network adapter .

Input output devices can be coupled to the system either directly or through intervening I O controllers. A user may enter commands and information into the system through input devices such as a keyboard pointing device or other input devices for example microphone joy stick game pad satellite dish scanner or the like . Output devices may include speakers printers etc. A display device is also connected to system bus via an interface such as video adapter .

Let T represent an epoch of time and let T T denote a time moment in T. Denote C C C . . . C a set of n channels where each channel C C is defined as an infinite stream of update events C e e . . . starting from the beginning of epoch T. Assume textual streams where each update event e C contains a text message. Further denote life e the period of time during T on which update event e is available on the channel.

For a given time T T and a channel C C a channel snapshot at time T denoted C is given by the set of update events available on the channel at time T that is life 

Let W be a time window in T. Given a channel C C further denote Cthe union of channel snapshots during the time window W C C Channel Profiles

A channel profile represents the textual content of the channel events belonging to the channel snapshot C. Due to the dynamic nature of channels channel snapshots captured during different times may differ resulting in a possible difference in the corresponding channel profiles.

In this work the Bag Of Words BOW model is adopted for representing the channel content. Given a vocabulary of terms D t t . . . t the channel profile at given time T is then defined as a weight vector 

Each weight wcorresponds to a unique term t D which may appear in the textual content of the channel events. If Ccontent does not contain term t then w 0. Each term can be either a word a phrase or a lexical affinity.

Similarly given a window W of k last events captured on the channel i.e. a window of size k define P C as the profile representing the content of those events.

The channel profile is therefore a compact representation of the channel content at a given time and is used to capture the relative importance of each of the terms in the channel at time T or during a time window W .

An increase in profile window size results in more content that is accumulated over a longer period of time and therefore it may require more resources such as in memory. Furthermore the profile window size has an important role from a user s point of view. A user that prefers generality i.e. a wide perspective of the content published on the channel for a long time would require a large window size to satisfy these needs. On the other hand a user that prefers specificity i.e. a narrow perspective of the current content published on the channel would require a small window size.

Web feeds are usually used by content providers to publish content on the Web. Those feeds are dynamic channels supported by pull only protocols e.g. available for access through HTTP GET calls where the set of published items on each feed changes over time and items are volatile in most cases.

A Web feed such as RSS Really Simple Syndication or Atom feed is an XML Extensible Markup Language file that contains a set of feed items where each item links to some Web resource e.g. an HTML HyperText Markup Language file and contains summarized details of the resource such as title and description. The items that are published on the feed over time comprise the dynamic feed channel. Therefore every new item published on feed C is treated as an update event e C. The set of terms appearing in the item text title and description comprise the item bag of terms B e .

The terms weights in a Web feed profile are determined using the well known tf idf weighting scheme. Given C the set of items that are available on feed C during the time window W the term frequency of a term t tf t C is the number of occurrences of t in C. To calculate the inverse document frequency of a term t idf t first count all items gathered from the feeds C C from the beginning of the epoch until the end of the time window W denoted C T . Then count the number of items in C T that include at least one occurrence of term t C T . Then the idf of term t is calculated by 

While the tf of a given term t in the profile represents a the temporary local importance of the term in the channel during the given time window the idf of a term represents its global importance by considering also the occurrence of the term in items that appeared on the different channels during the history. Since channel profiles are used to represent the dynamic textual content of the channel common terms appearing in many channel items are less important in representing the channel content in a given time frame. Therefore common terms with low idf value will be weighted lower compared to the rarest terms.

Two measures are defined over channel profiles. The first is a profile similarity which is used to evaluate the similarity between two channel profiles. The profile similarity will be used to evaluate how the channel content is changed over time by measuring the difference between channel profiles in different time periods. The second is a channel cohesion measure that further can be used to compare different channels with regard to the average rate of change of their content over time.

Given a pair of channel profiles P P define the similarity between the two profiles as their vector space model cosine similarity 

It is worth noting that the similarity between profiles of the same channel in two different time windows reflects the amount of changes in content of the channel over time.

Channel cohesion measures the cohesion of the textual content in the channel over time. A channel with a low cohesion is one for which new published events dynamically change the channel content as reflected by the corresponding channel profile. Such a low cohesive channel will require a higher monitoring rate in order to keep its profile up to date.

A higher cohesive channel is one where new items cause only minor change in its profile. This is typical of channels with many duplicate or near duplicate items or when items are focused on the same topic for a long period of time. For such channels a low monitoring rate will suffice.

DEFINITION 1 CHANNEL COHESION . Given a channel C C the channel cohesion during the epoch T T T is calculated as 

Channel cohesion measures the average profile similarity in a given time period T T . If the channel profiles significantly differ over the time period the cohesion will be low. In practice one can approximate the cohesion metric to measure the relative profile change per update event. Given N update events that occurred during epoch T and assuming that the initial profile is empty all terms weights are zero Equation 2 is modified to 

A monitoring policy s task is to maintain accurate channel profiles by deciding which channels to probe at any given time. A probe is a channel pull action. A channel monitoring task is considered to consist of several costs such as opening a TCP IP connection to the Web channel provider capturing its current snapshot by downloading its content refreshing the channel profile and updating the index. A constrained monitoring setting is assumed where the monitoring policy is allowed to probe up to M

Given a channel C C denote the optimal profile at time T T P C as the profile obtained by monitoring the channel after each update event in the channel. Given a channel monitoring policy pol further denote P C as the profile obtained by the monitoring policy at time T which in general will be sub optimal due to some missing non monitored events caused by policy decisions. The profile monitoring quality obtained by policy pol over the set of channels C is given by 

This quality measure provides an indication of how good the policy pol is with respect to the optimal policy. It measures the average similarity between the optimal profiles obtained by the optimal policy to the profiles obtained by pol over time and over the full set of channels.

This section describes the proposed framework for single channel monitoring. In this simplified case the number of channels to monitor by the policy in Equation 4 is reduced to n 1.

Off line and on line channel monitoring is distinguished. In the off line case a policy is applied that monitors the channel in a uniform monitoring rate with respect to the average update rate of the channel.

For the on line case an adaptive learning scheme is provided to derive the channel update rate which is used to derive a monitoring rate as in the off line case. Experimentally it can be shown how the effectiveness of the learning scheme converges to the same uniform monitoring rate as determined in the off line case.

The policy is further extended to consider the content published on the channel. This extension estimates the rate of novel update events that appear on the channel. This work shows that monitoring based on the novel update rate provides a high quality channel profile with significant reduction in the system resources required for the monitoring task.

Referring to a flow diagram shows the general method of determining a channel monitoring rate. Monitoring of a channel is carried out at an initial monitoring rate and a set of captured update events to the channel is obtained and recorded in a time interval . Optionally a novelty filtering is applied to the set of events to filter out the events which provide a significant novel content to the channel. Learning rules are applied to the monitoring rate based on the set of captured update events and a new monitoring rate is determined . Monitoring of the channel is then carried out at the new monitoring rate . The method loops and the new monitoring rate is used in the next cycle. A method of determining a channel monitoring rate may be applied to more than one channel in parallel.

In the case of off line monitoring for a given channel C C the set of all update events e C and their corresponding content is known in advance for a given epoch T. This mode is of course only possible in retrospect. In practice only the on line case is a realistic one for which the set of update events is unknown in advance.

Let T denote the update rate for channel C at time T T and let T denote the monitoring rate of channel C at that same time. The off line monitoring rate of channel C C is derived as the average update rate in the epoch T. That is given that channel C has N update events during T then for each time T T the off line monitoring rate is determined as the uniform rate

It is worth noting that the off line uniform monitoring rate T serves as a first order approximation to the real non uniform update rate of the channel T .

In the on line case due to the volatile nature of the channels and especially in the case of Web feeds the rate at which we monitor the channel determines how many update events may be captured. With limited system resources for channel monitoring the monitoring rate should be selected wisely maximizing the profile quality while minimizing the monitoring rate.

In on line monitoring the next monitoring time is derived from the current on line monitoring rate. Denote Tthe last time that the channel was monitored and T be the current online monitoring rate. Thus choose to monitor the channel again at time

An adaptive scheme is provided based on Reinforcement Learning for deriving the monitoring rate of a channel. For this purpose we use Boltzman Learning.

Equation 5 provides the iterative learning rules that we use assuming that the learning process starts at the beginning of epoch T. Let 0 be the initial monitoring rate selected arbitrarily and let T 0 denote the beginning time of epoch T. Let C denote the set of captured update events between two consecutive probes to channel C that occurred at times Tand T respectively where define W T T and W T T . Then the learning rule is given

 is a learning parameter that controls the tradeoff between the amount of exploitation and exploration of the learning process. The larger is the more the current monitoring rate T is relied upon learned from history exploitation and the less the local observed rate exploration is relied upon. The G parameter controls the rate of learning where larger values imply a slower learning process. For experiments 0.1 and G 100 chosen by trial and error using the full set of Web feeds.

Experiments demonstrate that the on line monitoring rate as learned by the learning scheme converges to the off line monitoring rate.

Note that the off line rate expresses the average rate of updates on the channel while the on line rate continuously adapts to the dynamic update rate of the channel. When the update rate is changed over time the on line rate will adapt to those changes in a local manner.

A channel monitoring scheme is now described based on novelty detection. The idea behind this scheme is based on the observation that many new events are redundant in terms of providing novel information and do not cause any significant change to the channel profile. Moreover the rate of new novel events differs from channel to channel therefore it is beneficial to learn the update rate of novel events and then use it as the monitoring rate for the channel. Since novel update rate is usually smaller than the complete update rate and since a policy based on the novel update rate is expected to provide high quality channel profiles valuable system resources can be saved.

The described novelty detection scheme works as follows. Similarly to the Learning On line Monitoring Rate let C denote an ordered set of captured update events between two consecutive probes to channel C that occurred at times Tand T respectively hence W T T . Furthermore let coh C T be the cohesion calculated given the last N captured events on the channel up to time T T as determined by Equation 3. First calculate for each event e C its marginal influence on the channel cohesion given by 

Further determine the standard deviation of the channel cohesion using the following unbiased estimator 

Otherwise the event is considered novel following its dissimilarity to the channel profile and its potential for significant influence on the profile.

The parameter is a threshold parameter that is used to control the amount of filtering for novelty detection. It controls the tradeoff between monitoring rate and profile quality. A high means low filtering most events will be considered novel. Conversely a low will cause only a few events to be considered as novel but this will in turn cause insufficient monitoring followed by degradation in channel quality.

Using the novelty detection filter for off line monitoring is straightforward apply the filter on the complete set of events and calculate the off line monitoring rate while considering only novel events.

In the on line case shows a flow diagram of the process of updating the on line monitoring rate using the novelty detection filter. The different equations involved in the calculation are also given next to their relevant components.

Starting from the leftmost component update events e are captured and suppose that Nnew update events are captured between two consecutive monitoring times Tand T which are kept in the buffer C in . The update events eare input into a novelty filter . The novelty filter also has an input of the parameter to control the amount of filtering.

Further suppose that prior to time T a total of Nevents were captured thus resulting in a total of N N Nevents at time T. Then update Equation 3 to maintain the channel cohesion value on line 

A history component maintains both the last calculated channel cohesion value and the novel monitoring rate and is updated after every monitoring probe. The coh C T value is taken from the history component and a cohesion calculator calculates the new cohesion value which is input to the novelty filter and input to the history component .

The novelty filter uses the previous and the new cohesion values to calculate the standard deviation of the channel cohesion using Equation 6. It then applies the filtering rule of Equation 7 on the new Nupdate events captured at time T. The output of the novelty filter is C which is then used to derive the observed novelty update rate at time T which is combined 450 with the history learned rate T according to the adaptive rules of Equation 5 where C C. This provides the current monitoring rate T which is also returned to the history component .

It is worth noting that by using this on line scheme the expensive complexity in maintaining channel cohesion is reduced where only the current buffer of captured events is considered in T T for novelty detection filtering.

A performance analysis study carried out provides empirical evidence that using the proposed content based scheme compared to the content free scheme can maintain high quality channel profiles with a significant savings in the number of probes required for this task. For example the proposed content based scheme reduces the number of times it probes channels by 50 while losing no more than 5 in quality.

For this purpose a simulation using a set of Web feeds was carried out. Each feed was monitored twice once using the content free monitoring scheme and once using the content based monitoring scheme. The quality obtained was measured by applying each monitoring scheme on each feed according to Equation. 4. In addition the total number of probes was recorded by monitoring each feed according to each scheme. Using these two measures it was further calculated for each feed the ratio of quality loss and probe cutoff gain between the two monitoring schemes as follows. Given a feed C C let Q C free and K C free denote the quality and number of probes of the content free scheme and let Q C content and K C content denote the quality and number of probes of the content based scheme. Then calculate the quality loss as

The effect of the filtering threshold on profile quality was first studied. It was observed that increasing increases the average quality per channel feed . Obviously larger values imply that more events are considered novel and thus the corresponding monitoring rate is larger and increases quality. Moreover for 0.1 the average quality among the different monitored channels is at least 95 from optimal. Finally the 98 percentile curve of the channel profiles quality shows that for 0.25 at least 98 of the monitored channels have at least 95 of the optimal profile quality.

Using the same off line case the novelty detection scheme s trade off between monitoring quality and saving monitoring resources has further been explored. The relative cutoff was measured in the number of probes compared to the loss in quality resulting from the cutoff. It has been shown that a small loss in quality compared to significantly fewer probes for reasonable values. For instance for 0.1 5 in average profile quality was lost while cutting down a third of the probes 50 gain .

The effect of the profile window size Win terms of the number of update events is considered for profile calculation on the quality budget trade off in the on line monitoring setting. In this experiment the threshold parameter is fixed 0.1 that was learned in the off line analysis.

It was observed that the quality loss is directly affected by the profile window size W. As the window size increases the profile provides a wider perspective of the channel and therefore there is less chance of missing update events and deviating from the optimal profile hence the quality loss is reduced.

Using the evaluation results presented in this section it is concluded that the monitoring scheme based on novelty detection indeed provides better utilization of the monitoring budget while producing high quality channel profiles. This observation will be supported in the next section that further explores the multi channel monitoring case.

A monitoring policy is allowed to monitor at most M channels in parallel. Thus the profile quality obtained for multi channel monitoring depends on the policy s on line decisions of which channels to monitor over time. In the following a simple classification scheme for multi channel monitoring policies is introduced. Inter channel profile similarities are also introduced as a means of further refining the monitoring rates. Finally an empirical evaluation study is discussed on the performance of these policies

The importance of a channel is defined during time to be relative to its monitoring rate as derived by the learning scheme presented previously. A channel with higher monitoring rate is considered more important. Note that the relative importance of a channel is changed dynamically over time according to the change in the derived monitoring rate.

The monitoring policies can be classified according to two main properties. The first property classifies the policies as either greedy or fair. A greedy monitoring policy monitors the most M important channels at any moment in time. It is worth noting that policies assume the availability of a given update model while the present method learns the model on line. Furthermore it is noted that the described monitoring rate learning methods can be easily integrated with any other monitoring solution that requires an update model as input. Therefore the analysis for the multi channel case also provides a proof of concept for the ease of usage of the described methods by a wide range of other possible monitoring policies. A fair policy on the other hand selects M channels at random according to the distribution induced by the channel relative importance values.

The second property relates to the policy attention to the content of the update events. A policy that ignores content is termed a content free policy while a policy that considers content is termed a content based policy. When the content is ignored the monitoring rates are learned as described in Equation 5. When the content is also considered the monitoring rate of each channel is calculated using the novelty detection filter. Since the monitoring rates of the channels determine their relative importance a certain channel might have different importance values under content free or content based policies due to the difference in monitoring rates.

Based on the classification described above experiments have been made with four policy types content free greedy content free fair content based greedy and content based fair . The four policy types represent a wide range of possible policies for multi channel monitoring.

A regularization scheme is proposed that can be used to further refine the channel monitoring rates based on inter channel profile similarities. Using this scheme a channel s monitoring rate can be refined according to its profile similarity to other channels profiles without actually having to probe that channel. For example suppose a channel s profile has high similarity with the profile of another channel that has just been monitored and therefore its monitoring rate has been updated . Therefore an increase in the last channel s monitoring rate will cause an increase in the first channel s monitoring rate as well.

For this propose we maintain an n n similarity matrix S where a matrix entry Scorresponds to the average profile similarity between channel Cprofile and channel Cprofile during a given time period T which is calculated as follows 

Every row i of matrix S is normalized by dividing each entry Sby the total sum of values on that row. A definition is provided of the relationship between each pair of Web feeds as was determined by a human assessment either an inclusion denoted C C or a similarity denoted C C . For example the content published on the NY TIMES.TECHNOLOGY.Circuits Web feed is almost completely contained in the content that is published on the NY TIMES.TECHNOLOGY Web feed resulting in very high profile similarity .

How the similarity matrix S is used to refine the monitoring rates is now discussed. Let right arrow over T . . . denote a vector of channel monitoring rates at time T and let S T denote the normalized similarity matrix as calculated at time T.

It is worth noting that a channel Cwhose profile is not similar to any of the other channel profiles will have S 0 and S 1 and therefore after applying Equation. 10 its monitoring rate will remain unchangeable and depend solely on the channel s own update events content . Otherwise the channel shares some profile similarity with other channels in the system and therefore its monitoring rate is determined by the relative similarity its profile has with the other channel profiles and the current channel monitoring rates. As is shown later such refinement can further improve the quality of maintained channel profiles.

An empirical evaluation has been carried out of the different policies that have been proposed in the monitoring policies using varied parameter settings. In general the two content based policies dominated their content free counterparts. It is show that the monitoring rates refinement scheme of inter channel profile similarities can further help to improve the performance.

The obvious observation from is that the quality obtained by the policies increases as the monitoring budget increases. Furthermore the empirical results reveal two interesting observations. First both content based policies dominate the content free policies at every budget level. These results support the empirical observations made on single channel monitoring. The results further suggest that considering the content for the derivation of channel monitoring rates and using them to determine the relative channel importance can improve the quality obtained by content based policies.

Second it is observed that while fairness provides better quality over greediness for the content free policies this is not the same for the content based policies. The content based greedy policy dominates the other three policies. This observation implies that when content is not considered it is preferable to fairly share the budget between the different channels and avoid making local greedy decisions. On the other hand these results further imply that content based policies may benefit from some greedy decisions when the budget is spread more efficiently among the different channels. Nevertheless fairness might still be the preferred choice for example when the policy monitors channels where most of them have high novel content rates.

To explore the effect of profile window size on the four different policies the monitoring budget was fixed to be M 6 and the simulation run using different profile window size W values. It was observed that as the profile window size is increased the quality obtained by all four policies is improved yet again with less remarkable improvement for the content free greedy policy. It is also observed that the two content based policies still dominate the two other content free policies and manage to better utilize the monitoring budget for every profile window size. Overall the two content based policies show almost similar performance suggesting that any type of content based policy whether fair greedy or in between may achieve better performance than any possible content free policy.

The effect of the novelty filtering threshold on the performance of the two content based policies was also evaluated. Again the monitoring budget was fixed to M 6 and fixed the profile window size to W 20. As values increase less update events get filtered and the two content based policies behave differently. For 0 more novelty filtering it is observed that overall the two policies keep their same performance level where the greedy policy further dominates the fair policy. On the other hand for 0 less novelty filtering it is observed that the two policies show opposite trends. While the fair policy remains quite robust and even improves slightly with the increase in the filtering threshold the greedy policy performance completely deteriorates almost to the level of quality obtained by its content free counterpart greedy policy.

This can be explained as follows as less update events are filtered the monitoring rates are less affected by the novelty filter and the two policies behave similarly to their content free counterpart policies. Therefore the content based fair policy dominates the content based greedy policy in a similar way the content free fair dominates the content free greedy policy in .

To conclude overall the simulation results clearly show that taking content into consideration by the multi channel monitoring policies improves the overall obtained quality of the channel profiles.

Finally the inter channel profile similarities refinement scheme was evaluated. For this purpose the content based fair policy was experimented with using different levels of novelty filtering thresholds . For 0 the content based fair policy dominates the content based greedy policy and therefore an aim is to improve its performance furthermore by utilizing inter channel profile similarities.

It is observed that in general the refinement scheme manages to improve the baseline performance of the policy for all budget levels where the highest improvement is by 15 . Furthermore it is observed that the improvement is much better when mild novelty filtering is used 0.2 . To explain a more aggressive novelty filtering may result in lower inter channel profile similarities and therefore a channel s monitoring rate is less effected by the other channels monitoring rates.

It is concluded that indeed inter channel profile similarities can be efficiently utilized to further refine the channel monitoring rates and improve the overall performance.

Some measures of profile monitoring quality have been described. Using these measures it is demonstrated the necessity for methods for maintaining channel profiles. Both off line and on line monitoring cases are discussed and the challenges in monitoring profiles on line. For the on line case a monitoring scheme is proposed based on reinforcement learning for the derivation of channel monitoring rates. An extension of this monitoring scheme is further presented by considering the content that is published on the channel. A novelty detection filter is proposed that refines the monitoring rate according to the rate at which novelty content is expected to be produced on the channel. It is also demonstrated how inter channel profile similarities can be utilized to refine more the monitoring rates.

Using real world data of Web feeds the performance of the on line monitoring scheme has been studied for single and multi channel monitoring. The empirical study showed that the monitoring rates learning combined with the on line novelty detection can guarantee high quality channel profiles while significantly cutting down the monitoring budget which in turn improve the overall performance. Finally it was showed that inter channel profile similarities can be utilized to improve more the performance.

The invention can take the form of an entirely hardware embodiment an entirely software embodiment or an embodiment containing both hardware and software elements. In a preferred embodiment the invention is implemented in software which includes but is not limited to firmware resident software microcode etc.

The invention can take the form of a computer program product accessible from a computer usable or computer readable medium providing program code for use by or in connection with a computer or any instruction execution system. For the purposes of this description a computer usable or computer readable medium can be any apparatus that can contain store communicate propagate or transport the program for use by or in connection with the instruction execution system apparatus or device.

The medium can be an electronic magnetic optical electromagnetic infrared or semiconductor system or apparatus or device or a propagation medium. Examples of a computer readable medium include a semiconductor or solid state memory magnetic tape a removable computer diskette a random access memory RAM a read only memory ROM a rigid magnetic disk and an optical disk. Current examples of optical disks include compact disk read only memory CD ROM compact disk read write CD R W and DVD.

Improvements and modifications can be made to the foregoing without departing from the scope of the present invention.

