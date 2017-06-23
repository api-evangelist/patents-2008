---

title: Pattern discovery through reversing time flow
abstract: The present invention provides systems and methods for automatically mining massive intelligence databases to discover sequential patterns therein using a novel combination of forward and reverse temporal processing techniques as an enhancement to well known pattern discovery algorithms.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07945572&OS=07945572&RS=07945572
owner: The Johns Hopkins University
number: 07945572
owner_city: Baltimore
owner_country: US
publication_date: 20080321
---
This application claims the benefit of prior fled U.S. application No. 60 896 070 filed on Mar. 21 2007 which is incorporated herein by reference in its entirety.

This invention was made with U.S. Government support under contract no. 01 C4750. The U.S. Government has certain rights in the invention.

The present invention relates generally to the field of data mining and more particularly to methods and systems for mining one or more structured datasets to automatically extract patterns or associations within the data.

One of the growing critical challenges facing the intelligence community is to produce actionable intelligence from massive and still increasing datasets in a decreasing amount of time. Current analysis tools such as GALE Generic Area Limitation Environment or DCGS Distributed Common Ground Systems enable analysts to examine and confirm or reject hypotheses they have formed. These confirmatory methods and tools are a necessary part of intelligence analysis however they use a trial and error based approach that consumes large amounts of time and they highlight one of the shortcomings of using only the tried and true methods of the previous generations of analysts in today s world.

Previous analysis methods were human centric and as such allowed the extraordinary decision capabilities of the mind to be leveraged in analyzing the pertinent hard to come by intelligence data. With the massive collections of data that occur every day indeed every hour in a region of interest the human mind can only leverage its power on an infinitesimal portion of the collected data. Moreover it is now an extremely complex challenge to know which are the pertinent data buried in the massive amounts of collected data.

A need therefore exists for an automated exploratory data centric mode of analysis capable of discovering patterns creating metadata or simply generating a more concentrated grouping of data to be added to the manual confirmatory human centric mode to facilitate the vast majority of data collected. This data centric mode of analysis must leverage the processing power of computers to assist the analysts in producing critical actionable intelligence needed to facilitate national security.

The present invention provides systems and methods for automatically mining massive intelligence databases to discover sequential patterns therein using a novel combination of forward and reverse temporal processing techniques as an enhancement to well known pattern discovery algorithms.

Rule induction algorithms constitute a well known class of pattern discovery algorithms that can be used to facilitate automated discovery of patterns or associations within structured datasets. The patterns comprise associations of database elements that repeat throughout an examined time pace. One type of rule induction algorithm is known as Sequential Rule Induction SRI which discovers repetitive sequential patterns RSPs . In general SRI discovers RSPs by first amassing candidate patterns and subsequently pruning removing candidate patterns that do not pass one or more statistical thresholds set by the user. The present invention enhances these well known pattern discovery algorithms by incorporating forward and reverse temporal processing in a fully automated capability for efficiently discovering a subset of repetitive sequential patterns RSPs hidden in typically large datasets.

In accordance with one embodiment of the invention there is provided a software tool which implements an automated discovery process based on the aforementioned well known pattern discovery algorithms enhanced by reverse and forward temporal processing techniques. The software tool operates by utilizing sequential rule induction as an underlying algorithm together with reverse and forward temporal processing techniques to mine massive databases to discover sequential patterns being exhibited by the database elements.

In one aspect of the invention techniques for mining massive databases to discover sequential patterns therein using a novel combination of forward and reverse temporal processing techniques comprise the following steps operations. Input is provided to the software tool which includes one or more input data files in conjunction with a set of user defined parameters. In a first processing segment the software tool operates on this input data to output discover a candidate set of patterns. In a second processing segment statistical thresholds are used to prune the candidate set of patterns output from the first processing segment to generate and output the final set of patterns. Using the final set of patterns the final processing segment involves reaching into the original input dataset s and extracting the actual data elements that comprise each of the patterns in the final set. These extracted data elements are then post processed and arranged in the appropriate order that is as described by the patterns. This output can be input to a visualization tool to display the pattern elements. Alternatively visualization can also be a simple tabular listing of the patterns.

Beneficially the present invention provides capabilities for mining massive datasets in an automated fashion and in a timely manner to discover sequential patterns buried within the data Experimental results have indicated typical processing times on commercial off the shelf platforms range from several minutes for large regular datasets to one or two hours when handling large dense datasets.

In the following discussion numerous specific details are set forth to provide a thorough understanding of the present invention. However those skilled in the art will appreciate that the present invention may be practiced without such specific details. In other instances well known elements have been illustrated in schematic or block diagram form in order not to obscure the present invention in unnecessary detail. Additionally for the most part details concerning network communications electromagnetic signaling techniques and the like have been omitted inasmuch as such details are not considered necessary to obtain a complete understanding of the present invention and are considered to be within the understanding of persons of ordinary skill in the relevant art.

It is further noted that unless indicated otherwise all functions described herein may be performed in either hardware or software or some combination thereof. In a preferred embodiment however the functions are performed by a processor such as a computer or an electronic data processor in accordance with code such as computer program codec software and or integrated circuits that are coded to perform such functions unless indicated otherwise.

It should be appreciated that the present invention can be implemented in numerous ways including as a process an apparatus a system a device a method or a computer readable medium such as a computer readable storage medium or a computer network where program instructions are sent over optical or electronic communication links Several inventive embodiments of the present invention are described below.

The following paragraphs describe a overview of the invention and a software tool for storing and executing software in accordance with an illustrative embodiment of the invention.

As will become apparent the present invention may generally benefit analysts by providing them with interact and leverage on the products of a data centric analysis provided by the present invention which include patterns metadata or simply a more concentrated grouping of data.

As used herein examples and illustrations are intended to be representative and not limiting in nature.

While described below with respect to mining massive databases the present invention provides a generic capability for mining any large dataset and is therefore not limited to any particular dataset type configuration or size.

In accordance with the present invention there are provided herein methods and systems for mining massive datasets to discover repetitive sequential patterns RSPs hidden within the datasets.

Broadly described systems and methods of the invention operate by utilizing sequential rule induction RSI techniques to discover repetitive sequential patterns RSPs by first amassing candidate patterns and subsequently pruning removing candidate patterns that do not pass certain statistical thresholds set by a user. These statistical thresholds provide that only significant patterns are kept as outputs to the SRI process. It should be understood that without these thresholds every sequential combination of elements in the dataset would be considered a valid output thereby making the output effectively useless.

In a preferred embodiment a recurring pattern in a dataset is determined to be statistically significant if it passes two thresholds. Once a pattern is determined to be statistically significant its constituent elements are said to be sequentially associated with each other in a mathematical sense. The two thresholds correspond to the statistical metrics of Support and Confidence as defined below.

As used herein a pattern is defined as a sequential association of database elements that repeat throughout an examined dataset. It is noted that the term element can be equated with entities incidents transactions or any general event. An example of a sequential pattern of elements A A A A and C could be 1234

Where A through A are referred to as antecedents and C is referred to as a consequent. The exemplary pattern above may be described as follows A occurred first antecedent then at some point later elements A and A occurred simultaneously antecedent then at some point later A occurred antecedent and the final element C occurred sometime after that the consequent . It will be understood by the reader that the invention can use any element characteristic selectable by the user as a discovery variable or parameter such as element identification or filter variable.

It should be noted that time stamped elements are not essential to carry out the method. If a dataset does not have timestamp information associated with its elements the order of elements is represented by their position in the dataset. That is the first element in the dataset is considered to be ordered before all others the twenty sixth is considered to be ordered after the twenty fifth and before the twenty seventh and so on.

As used herein a time bin or simply bit describes how a temporal dataset may be divided. For example if a dataset spans 24 hours then the user may decide to split up the dataset into time bins of length 30 minutes each thus Yielding 48 consecutive time bins for the entire dataset.

In an embodiment in which the dataset does not include timestamp information a bit is simply defined by the number of elements to be included in each bin. For example if a dataset consisted of 1000 elements then the user may decide to split the dataset into bins of 30 elements each thus yielding 33 consecutive bins with 30 elements each and the last bin with 10 elements.

As used herein the term Support describes the number of instances a pattern has occurred in a dataset. Support is typically represented as a percentage. In other words support is a statistic describing how many instances of a particular pattern exist in an entire dataset. Support may be calculated in one way as

For example if a pattern occurs appears 36 times in a dataset divided into 48 consecutive bins then the Support for that pattern is calculated as Support 36 48 75 

As used herein a repetitive sequential pattern RSP is a sequential pattern that occurs over and over again in a dataset.

As used herein Confidence describes how many times the final element of a pattern occurred as a percentage of the number of times the first part of the pattern occurred. For example if a pattern has 4 elements occurring in the same order over and over again in the above example the pattern occurs 36 times in the dataset then it should be realized that the first 3 elements of that 4 element pattern will have occurred in that particular order k times ins where k is greater than or equal to 36. So if for example the first 3 elements occurred 40 times appeared in 40 bins then the Confidence would be 90 36 40 that is the last element occurred 36 of the 40 times the first 3 elements occurred in the right order. Confidence is calculated as 

It should be understood that a discovered pattern will have a calculated Support and Confidence value associated with it. For examples if a 4 element pattern such as the one discussed above had elements then a pattern may be represented as 75 90 

A user sets the thresholds for both Support and Confidence. These thresholds determine which patterns should be pruned in question and which should be provided as outputs as described above. The user can set both thresholds from 0 to 100 however it should be understood that if a user sets the thresholds to 0 then every combination of elements will be considered valid patterns and provided as outputs because even if a pattern occurs only once and even if the last element occurs only once relative to the first part of the pattern it still qualifies as a valid pattern.

Because datasets are typically large relative to the size of each bin there are a large number of bins in a dataset. Therefore the Support threshold is typically set low in case the data elements are not overly repetitive in nature. This threshold is related fairly closely to the nature of the data and hence the user does not have as much freedom with this threshold.

The confidence is typically set very high for two reasons. First it is desirable that the last element of a pattern be almost always present when the first part of the pattern occurs to provide a fairy good predictive aspect to the pattern. In other words by setting the confidence parameter high if the first part of the pattern occurs then there is a very strong likelihood that the last element will occur within a given timeframe. Secondly because the Support threshold is typically set low out of necessity if the Confidence threshold is also set low then there will be a lot of patterns passing both thresholds and hence being provided as output. Hence the Confidence threshold becomes one of the key pruning criteria to keep the output pattern list bounded.

A key feature of the invention as will be described in detail below pertains to the concept of reverse temporal processing which involves inverting the temporal order of the elements in a dataset to be mined. This is generally achieved by determining the maximum value for the timestamps of each element and then subtracting each element s timestamp from the maximum value. This results in a new set of reverse timestamps that are substituted for the regular timestamps. It should therefore be understood that what was formerly the chronologically last element in the dataset i.e. the element with the maximum timestamp will now have a reverse timestamp of 0 and consequentially be the first element in the new temporally inverted dataset. Further the chronologically first element of the original dataset i.e. that with the smallest timestamp will have the maximum reverse timestamp and therefore be the last element in the inverted dataset.

Referring first to there is shown a timeline of data elements that comprise exemplary dataset to be provided as input to process to discover sequential patterns therein using a novel combination of forward and reverse temporal processing techniques as will be described below.

Dataset is shown to include 24 data elements that is data elements through or DE through DE where each data element is represented by one of 4 distinct identifications i.e. A through D.

It should be appreciated that the number of data elements of dataset is greatly reduced for ease of explanation as compared with a typical massive dataset for which the invention is well suited.

Referring now to the data elements of dataset are listed in tabular form including forward time stamp information. As will be described below this time stamp information is used by process of to initially organize the respective data elements A D of dataset into chronological order to facilitate forward and reverse processing in a manner to be described.

With reference now to there is shown a process for mining massive datasets to discover repetitive sequential patterns RSPs hidden within those datasets.

At step one or more input files are provided as input. The input files may comprise for example but not limited to criminal activity data credit card transactions rental agreements intelligence data or combinations of these.

At step the input dataset undergoes an initial data preparation stage which may include operations such as but not limited to normalizing original formats of date time latitude longitude values to a standard format setting types discarding blanks selecting dates selecting times and excluding specified elements.

At step The ID of each element is prepared across all datasets. Because element identifications are symbolic in nature numeric identifiers need to be preprocessed correctly. Also because of the variability that could exist across the multiple input files element identifiers need to be processed to ensure compatibility when the input files are fused together.

At step a determination step it is determined whether there are multiple input datasets. If so the process continues at step followed by step otherwise the process bypasses step and continues at step .

At step a determination step to determine whether the data elements of the input data set includes time stamp information. If yes the process continues at step otherwise the process continues at step .

At step the input data is arranged in chronological order based on timestamp information associated with the data. This is shown by way of example in in graphical form and in tabular form in . In this example twenty four data items DE through DE which are made up of A elements B elements C elements and D elements are arranged in chronological order based on time stamp information as shown in column two of the table of . It should be understood that the number of data elements shown in the table of represents a small percentage of the actual totality of data elements that make up dataset . This is done for ease of explanation and is not meant to indicate any restrictions or limitations of the present application.

At step the ordered elements are then split into consecutive time bins. In accordance with the present time stamp example the time space of dataset comprises 2.5 hours of time. illustrates the splitting of time space for dataset . In particular the time space of dataset is shown to be divided into ten consecutive user defined bins where the user has defined each bin to be 15 minute segments of the 2.5 hour time space. It should be appreciated that when choosing the length of time for the bins it is wise to consider the domain being analyzed. For example the bin length chosen if analyzing earthquake data might be very different than the bin length chosen if analyzing department purchase data.

At step Sequential Rule Induction is applied to the chronologically ordered elements to produce a set of forward repetitive sequential patterns. As described above the repetitive sequential patterns are sequential associations of dataset elements e.g. DE through DE that repeat throughout the examined timespace.

At step a determination step to determine whether the data elements of the input data set includes time stamp information. If yes the process continues at step otherwise the process continues at step .

At step a maximum time value is determined for the entire dataset defined herein as T MAX. This time value is identified by the data element s timestamp. In the present example T MAX is equal to 2 28 the timestamp associated with last occurrence of element B.

At step the reverse time space is created. In the instant example the value of T MAX e.g. 2 28 is used to subtract the time stamps of every other element in data set to create the reverse time space. Column of the table of illustrates by way of example a result of creating a reverse time space on dataset .

At step the elements of data set are arranged in chronological order based on the reverse time stamp information.

At step the data elements are separated into bins. For time stamped data this separation is based on the reverse time space information for non time stamped data the order of elements in dataset is simply reversed. illustrates a tabular representation of time binning as applied to the reverse chronologically ordered elements of the example dataset.

At step Sequential Rule Induction is applied to the reverse chronologically ordered elements to produce a set of repetitive sequential patterns in a reverse timespace.

At step the order of elements in each discovered pattern is reversed to yield patterns in correct forward temporal flow.

At step the two sets of patterns one set from the forward discovery process and one set from the reverse discovery process are merged.

At step duplicate patterns are removed. The forward and reverse discovery processes have the chance of yielding some patterns that are identical in these cases only one example is kept for final output.

It should be understood that in the present exemplary embodiment the steps associated with forward processing i.e. steps through can be performed substantially in parallel with the steps associated with reverse processing i.e. steps through . However forward processing may precede reverse processing or vice versa in other embodiments.

The invention provides advantages in pattern discovery by reversing the flow of time in a dataset to be examined as an adjunct to utilizing a conventional forward flow analysis. It should be understood that the advantage lies in the statistical results e.g. Support and Confidence and not in the statistical calculations which do not change irrespective of whether the dataset is analyzed in forward or reverse time flow. The preparation for this beneficial adjunct analysis is best illustrated with reference again to .

Referring again to the temporal dataset is shown to be divided into ten bins to facilitate processing in both the forward and reverse directions. The Support statistic was previously defined above as the number of times a pattern occurs in the dataset typically represented as a percentage a pattern such as pattern A B CD of bin of . Recall that the support statistic is calculated as 

It should be understood that the reverse temporal dataset of does not affect the support statistic for a pattern such as pattern A B CD This is true because the pattern elements remain the same just in reverse order. Hence the number of times the whole pattern occurs does not change.

In accordance with a conventional forward temporal processing approach as described in the flowchart of Support is calculated to be 10 because the full pattern A B CD is present in only 1 of the 10 bins i.e. bin . In the example illustrated in Confidence is calculated at 20 because the last element D is present in only 1 of the 5 bins i.e. bin in which the first 3 elements A B C of the patter are present. Equation 2 above describes an equation for calculating Confidence. Confidence 1 5 100 20 

Therefore using Sequential Rule Induction SRI techniques to discover the pattern e.g. A B CD SRI would set the thresholds below 10 and 20 for Support and Confidence respectively. For a large but regular dataset these values would generate many discovered patterns possibly thousands or more.

It should therefore be understood that when the SRI algorithm processes the temporal dataset in the reverse direction as shown at step of the flowchart the Support statistic can be set to less than 10 but Confidence can be set much higher than in the forward direction. It must in fact be set at 100 and the pattern e.g. A B CD is still discovered.

It is noted that in actuality it is the reverse pattern that is actually discovered in accordance with a reverse processing approach. Accordingly it is necessary to invert the discovered pattern to its correct causal order. This is true in general of all patterns discovered during reverse processing. In fact fixing the Confidence at 100 is a necessary condition for reverse temporal processing due to the inversion of the patterns after discovery. The reason for this is that there is no possibility of causality for reverse patterns whose last element is not always present because this translates to the first element of the pattern not being present when the pattern is inverted.

It has therefore been shown that forward processing support can be set to a small value and confidence to a value close to 100 or as high as desired so as not to discover a huge set of patterns and this will discover a manageable set of significant patterns but not pattern A B C D of the example . For reverse processing support again can be set to a small value however confidence must be fixed at 100 . This will also discover a manageable set of significant patterns including pattern A B C D of the example that indeed might have been missed by forward processing.

While the invention has been described with reference to an example embodiment it will be understood by those skilled in the art that a variety of modifications additions and deletions are within the scope of the invention as defined by the following claims.

