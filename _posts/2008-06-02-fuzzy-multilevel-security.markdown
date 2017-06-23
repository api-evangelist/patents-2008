---

title: Fuzzy multi-level security
abstract: An access control system and method includes a risk index module which computes a risk index for a dimension contributing to risk. A boundary range defined for a parameter representing each risk index such that the parameter above the range is unacceptable, below the range is acceptable and in the range is acceptable with mitigation measures. A mitigation module determines the mitigation measures which reduce the parameter within the range by mapping the effectiveness of performing the mitigation measures to determine a residual risk after a mitigation measure has been implemented.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08087090&OS=08087090&RS=08087090
owner: International Business Machines Corporation
number: 08087090
owner_city: Armonk
owner_country: US
publication_date: 20080602
---
This application is a Continuation of issued U.S. Pat. No. 7 530 110 issued May 5 2009 incorporated herein by reference in its entirety.

This invention was made with Governmental support under Contract No. TIA H98230 04 3 0001 awarded by U.S. Department of Defense. The Government has certain rights in this invention.

The present invention relates to system security for computer related devices and more particularly to models based on fuzzy logic for multiple security levels.

The traditional multi level secure MLS mandatory access control is based on the Bell LaPadula model See David E. Bell and Leonard J. LaPadula Computer Security model Unified Exposition and Multics Interpretation Technical Report ESD TR 75 306 The MITRE Corporation Bedford Mass. HQ Electronic Systems Division Hanscom AFB MA June 1975 where each subject or object is tagged with a tuple. All such tuples in a system form a partial order relation set where if and only if SL SLand CSCS. Information can flow from a source to a destination only if tag tag the source or destination can be either a subject or object. So a subject can read an object only if tag tag. A subject is usually a person or an application running on behalf of a person its sensitivity level reflects the degree of trust placed on the subject its categories set specifies the categories of objects the subject has a need to know or to access. A subject s sensitivity level is also called the subject s clearance.

An object is usually a data storage element such as a file or data transportation apparatus such as a network connection its sensitivity level indicates how sensitive the data are or the magnitude of the damage incurred by an unauthorized disclosure of the data its categories set specifies the categories to which the data belong.

This kind of traditional MLS model is a time honored tradition that has been in practice since before computers came into wide existence. The model is easy to understand and is also easy to make access control decisions based on the model by simply comparing two tags. If the tags associated with a subject and an object correctly reflect the subject s trustworthiness need to know and the object s sensitivity and categories then the access control decision is likely to avoid leakage of the information in the object and therefore the risk associated with such leakage. In short the model is geared toward risk avoidance.

The traditional MLS model does have some drawbacks however. Especially in today s environment where the need for information is ever greater a subject may not be associated with a proper tag that would grant access to those objects which are needed to complete a job. Since a subject s tag reflects the degree of trust placed on the subject it would be a bad practice to dynamically adjust the tag to a particular job. In other words the policy model may not be flexible enough to permit a system or an organization to fulfill its goals and responsibilities.

A policy model based on sensitivity levels and need to know is disclosed in accordance with preferred embodiment of the present invention. This model may be referred to as a fuzzy MLS model or fuzzy model for ease of reference but should not be limited by such terminology. The fuzzy MLS model preferably provides risk based access control.

One aspect of this fuzzy MLS model is to make access control decisions based on the perceived level of potential risk associated with the requested access. Instead of a binary allow deny decision an access control decision from the fuzzy MLS model would be one of allow deny or allow but with certain risk mitigation measures to be taken against the access . Depending on the perceived levels of risk different risk mitigation measures may be applied for different accesses. This fuzzy MLS model enables non binary versatile fine grained access control decisions to meet demands while keeping the risk in check.

The fuzzy model does so by removing the constraint s imposed by the binary input to the decision process if the partial order relationship holds.

It may seem that this fuzzy model is difficult to realize because it needs quantification of the risk associated with an access which would in turn need accurate prediction of future events that are results of or relevant to the access. While it is generally impossible to predict the future accurately one can usually estimate the risk associated with an action. For example insurance companies determine premiums by estimating risk we often choose to avoid entering a dark alley at night. Likewise the fuzzy MLS model estimates risk using the subject s and the object s tags and decides the course of action based on the estimate. Given the fact that there is and always will be only a limited amount of resources to protect information technology IT systems and information in them an illustrative goal of the fuzzy MLS model may be to deliver reasonable access control decisions in the sense that more resources are applied to security in more risky situations and therefore reduce the likelihood of severe damages and catastrophic events and increase the chance of well being and survival.

An access control system and method includes a risk index module which computes a risk index for a dimension contributing to risk. A boundary range defined for a parameter representing each risk index such that the parameter above the range is unacceptable below the range is acceptable and in the range is acceptable with mitigation measures. A mitigation module determines the mitigation measures which reduce the parameter within the range by mapping the effectiveness of performing the mitigation measures to determine a residual risk after a mitigation measure has been implemented.

An access control system and method includes sensitive objects potentially accessible by one or more subjects such that access to the objects by the subjects have risks associated therewith the risks being defined in one or more risk dimensions. A risk index module which computes a risk index in accordance with the objects and the subjects for each risk dimension. A transformation module converts the risk index into a probability for each dimension. A boundary range is defined for each probability for each dimension such that a probability above the range is unacceptable below the range is acceptable and in the range is acceptable with mitigation measures. A mitigation module which provides a residual risk wherein the probabilities are within the range and includes a mapping of the effectiveness of performing the mitigation measures to determine a residual risk after a mitigation measure has been implemented.

A joint probability can be computed by combining probabilities from all the dimensions and a boundary range can also be defined in terms of the joint probabilities. A boundary range can also be defined in terms of risk indices for a dimension such that an index above the range is unacceptable below the range is acceptable and in the range is acceptable with mitigation measures.

Since the transformation from risk indices to probabilities may be a one to one mapping e.g. a larger risk index is transferred to a higher probability risk indices can be used to define per dimension boundary ranges in a way similar to defining boundary ranges in terms of probabilities.

A method for making access control decisions includes computing a risk index for a plurality of dimensions which contribute to risk using a computer processing machine. A parameter is computed for each dimension for the risk index. A determination is made as to whether the parameter falls within a boundary range defined for the parameter for each dimension such that a risk index above the range is unacceptable below the range is acceptable and in the range are acceptable with mitigation measures.

These and other objects features and advantages will become apparent from the following detailed description of illustrative embodiments thereof which is to be read in connection with the accompanying drawings.

Embodiments of the present invention provides models for multi level security policy such that access control decisions are not simply binary allow deny decisions based on the traditional partial order relations between pairs but on a continuous range of risk indices. In one embodiment sensitivity clearance levels are not discrete levels but a continuous range of positive real numbers. Category sets may be replaced by the relevance to a category concept which is also represented by numbers.

Embodiments of the present invention are based on fuzzy logic e.g. from fuzzy logic set theory described in by Jyh Shing Roger Jang Chuen Tsai Sun and Eiji Mizutani Prentice Hall 1997. One aspect of this new model is to provide much more flexible access control than that provided by the traditional MLS but yet still maintain adequate security.

Embodiments of the present invention can take the form of an entirely hardware embodiment an entirely software embodiment or an embodiment including both hardware and software elements. In a preferred embodiment the present invention is implemented in software which includes but is not limited to firmware resident software microcode etc.

Furthermore the invention can take the form of a computer program product accessible from a computer usable or computer readable medium providing program code for use by or in connection with a computer or any instruction execution system. For the purposes of this description a computer usable or computer readable medium can be any apparatus that may include store communicate propagate or transport the program for use by or in connection with the instruction execution system apparatus or device. The medium can be an electronic magnetic optical electromagnetic infrared or semiconductor system or apparatus or device or a propagation medium. Examples of a computer readable medium include a semiconductor or solid state memory magnetic tape a removable computer diskette a random access memory RAM a read only memory ROM a rigid magnetic disk and an optical disk. Current examples of optical disks include compact disk read only memory CD ROM compact disk read write CD R W and DVD.

A data processing system suitable for storing and or executing program code may include at least one processor coupled directly or indirectly to memory elements through a system bus. The memory elements can include local memory employed during actual execution of the program code bulk storage and cache memories which provide temporary storage of at least some program code to reduce the number of times code is retrieved from bulk storage during execution. Input output or I O devices including but not limited to keyboards displays pointing devices etc. may be coupled to the system either directly or through intervening I O controllers.

Network adapters may also be coupled to the system to enable the data processing system to become coupled to other data processing systems or remote printers or storage devices through intervening private or public networks. Modems cable modem and Ethernet cards are just a few of the currently available types of network adapters. The methods as described herein may be implemented or used on an integrated circuit chip s .

The resulting integrated circuit chips can be distributed by the fabricator in raw wafer form that is as a single wafer that has multiple unpackaged chips as a bare die or in a packaged form. In the latter case the chip is mounted in a single chip package such as a plastic carrier with leads that are affixed to a motherboard or other higher level carrier or in a multichip package such as a ceramic carrier that has either or both surface interconnections or buried interconnections . In any case the chip is then integrated with other chips discrete circuit elements and or other signal processing devices as part of either a an intermediate product such as a motherboard or b an end product. The end product can be any product that includes integrated circuit chips ranging from toys and other low end applications to advanced computer products having a display a keyboard or other input device and a central processor.

A fuzzy MLS model aims to control access to information by managing the risk associated with such accesses. To this end the risk may be defined as the expected value of loss incurred by unauthorized disclosure of information risk value of information probability of unauthorized disclosure 1 

The value of a piece of information is defined to be the value of loss when the piece of information is disclosed in an unauthorized manner. The unit of value may be defined in accordance with the circumstances and assume that the value can be defined for a particular application scenario and environment. A further assumption is that in general there is a way to give at least a reasonable estimate of the value or the upper bound of it.

One difficulty is in determining the probability of unauthorized disclosure. A precise determination is generally impossible since that would require a precise prediction of future events that are relevant to accesses to the information. Instead the fuzzy MLS model strives to develop a way to assign such probabilities that are commensurate with common sense and intuition of which a large part actually comes from prior research done on the traditional MLS model. For example the probability should be very high when a person without security clearance is given access to top secret information but relatively low if the access is given to a person with a top secret clearance. However the problem is much more difficult than the example.

The difficulties may include the following. There are many dimensions contributing to the risk examples are sensitivity and clearance levels categories and need to know etc. These dimensions are usually not orthogonal to one another yet the exact relationship among them cannot be known. Therefore their joint probability distribution cannot be known in general. One reason for estimating the risk is to determine if the risk is too high and therefore to mitigate the risk. If only a quantified risk estimate is available it would be difficult to determine the major contributing dimensions to the risk and therefore the proper mitigation measures.

In addition all probabilities have to be in 0 1 this may not provide enough resolution to differentiate between different levels of risk. This is especially so given the fact that the probabilities are estimates at best. For example a 0.01 difference in probability may not lead to a significant enough difference to alter a decision in practice.

Referring now to the drawings in which like numerals represent the same or similar elements and initially to a block flow diagram shows a method for approximating risk and making an access control decision in accordance with embodiments of the present invention.

The following approach may be used to address the difficulties cited above and to produce an approximation of risk as defined by formula 1 . In block for each dimension contributing to the risk define a formula that computes risk indices that are commensurate with intuition such that a larger index indicates a higher chance of unauthorized disclosure. For example define a formula to compute a risk index from sensitivity levels. The risk of information flow from an object s sensitivity level to a subject s clearance level may be defined so that the index increases when the sensitivity level increases or when the clearance level decreases. The range of risk indices is 0 . The risk indices are always greater than zero to reflect the fact that there is always some risk however small it may be.

The index is not capped to provide greater resolution on risk levels. Risk indices are relative measurements of risk. To make them useful they need to be calibrated as described in the next step in block .

In block for each dimension define another formula to convert a risk index into the probability of unauthorized disclosure. The formula should be monotonically increasing with respect to the risk indices. It is preferable that the formula includes tunable parameters so that they can be fine tuned to approximate statistics or intuition. This formula and calibration image a random process that takes a risk index as input and produces a Boolean output to indicate if an unauthorized disclosure happens. This formula may be labeled Probfor a dimension D.

The requirements for Probare lim Prob RI 0 lim Prob RI 1 RI RI Prob RI Prob RI The first requirement can be relaxed to lim Prob RI 0 for some operations.

In block for all dimensions a Hard Boundary HB and a Soft Boundary SB are defined for risk indices such that risk beyond the HB is not acceptable and an access request should be denied and risk below the SB is acceptable. The range between the HB and the SB is a large component of the flexibility provided by the fuzzy MLS model.

In block for each dimension determine a set of risk mitigation measures and their effectiveness such that the effectiveness of a measure m as a mapping efrom a risk index RI to another risk index can be established as RI Residual risk index after applying 3 e RI should be less than RI but greater than zero.

The process of determining risk mitigation measures and their effectiveness is likely to need human involvement or at least human supervision. There is likely to be a set of general risk mitigation measures that can be applied to all dimensions although the effectiveness of a measure may differ in different dimensions. The goal of risk mitigation measures is to bring risk between HB and SB down an acceptable level to be below SB.

In block define a transformation to combine probabilities from different dimensions to approximate their joint probability distribution. It would be preferred that the transformation includes tunable parameters so the parameters can be fine tuned to approximate statistics or intuition. More details of the probability formulas and transformations will be given below.

It should be noted that the steps for the assessment of risk as described above may be applied independently of the decision assessment steps as outlined below. Using the approach described above an access control decision can be made in the following ways 

Referring to in block for each dimension D using the value of the object to which access is requested to compute two risk indices RIand RIthat correspond to the HB and SB through the following inequality value of the object Prob RI 

Also a practical system is most likely to quantize the value of objects to a finite set of levels. Therefore the computation of RIand RIcould be done off line a priori and an on line operation would only need to do a table look up.

In block bring the risk in each dimension down to below the corresponding RIby applying risk mitigation measures. In practice it is likely that a general risk mitigation measure applied to one dimension will have an effect on all dimensions.

In block evaluate formula 1 to see if the residual risk is still too high and grant the access only if the risk can be brought down to an acceptable level by some additional risk mitigation measures.

Embodiments of the present invention can be applied to many kinds of dimensions. For example two kinds of dimensions the kind characterized by sensitivity and clearance levels and the kind characterized by categories and need to know will be illustratively described in accordance with this disclosure. However the present invention should not be construed as limited by the illustrative examples.

Referring to a method for computing risk indexes and combining risk indexes is illustratively shown for one exemplary embodiment. In block formulas that compute risk indices for dimensions e.g. from sensitivity levels and from need to know are provided. Intuition behind these formulas and how they are derived will be discussed hereinafter as well as how to combine risk indices from multiple dimensions into a single risk value.

In block a risk index is computed from sensitivity levels preferably by using a formula that computes the risk index of an information flow based on the sensitivity levels of a subject and an object. The symbols sl and ol will be employed with optional subscripts to represent the sensitivity levels of a subject and an object respectively.

The formula may be described in terms of a function RI sl ol which takes a subject s and an object s sensitivity levels as parameters and computes a risk index on information flow from the object to the subject. For ease of discussion and analysis sl ol and RI sl ol are all positive real numbers and a smaller number represents a lower level of sensitivity or a lower level of risk. This restriction should be reasonable and is consistent with the current practice of implementing MLS systems. There could be countless many ways to define RI but any definition should satisfy the following properties 

S 1 S the set of all allowed values for sl. 1 is chosen for the left bound to avoid division by zero 

Risk indices values may be calculated based on formula 7 or any other suitable formulas. How formula 7 is derived and the physical meaning of an ol or sl as the log of the object value or the trustworthiness of the subject we be described in greater detail below. However one useful form of ol and sl includes log object value log subject trustworthiness 

It is pessimistically assumed that every person has a price and the trustworthiness of a subject is expressed in terms like 

 This person can be trusted with no more than 10 000. There are certainly many other possible ways to define RI but formula 7 has some desirable properties which would be beneficial for any definition of RI. RIis a simple analytical and continuous function simple analysis can show that it not only satisfies formulas 5 and 6 but also provides benefits over S O that are consistent with the intuitions on sensitivity levels. For example 

This implies that a subject s access to an object always carries some risk even if the subject is very trustworthy. It would be a policy decision that some risk mitigation measures should be taken in this case.

The risk index is greater than m ol if slol and it equals m ol if sl ol. This property serves as the link to the traditional Bell LaPadula model based MLS policy in the sense that the Bell LaPadula model is violated if the risk index is greater than m ol .

A determination is made as to risk and mitigation of the risk based on sensitivity. In formula 7 the values of ol may be restricted to be less than m. The intuition of m is this If the sensitivity of an object is close to or greater than m then any access to this object ought to be considered extremely risky and be handled with extreme care it may imply extreme risk mitigation measures such as complete physical isolation of the object subject and IT systems or constant human supervision as one form of mitigation. Note that limRI sl ol . Such a large risk index does not necessarily imply denying access to an object. It may however force special attention and caution when making the access control decision.

In block risk index is computed based on need to know. This includes a new category and relevance model being developed that is derived based on fuzzy set membership and treats relevance like sensitivity.

Contrast this with a traditional MLS system where need to know is represented by category sets. A subject has the need to know to an object if and only if the subject s category set is a superset of the object s category set. This is a binary decision since classical set membership is a binary relationship.

By the present disclosure the category and relevance model considers a category to be an information category. An object s relevance to a category is a measure showing how relevant the information in the object is to the category. A subject s relevance to a category is a measure showing how strong a need the subject has to know the information in the category.

The difference between dealing with categories and dealing with sensitivity levels is that a subject or an object has one sensitivity level but may have relevance to more than one category. Dealing with sensitivity levels is a one dimensional problem while dealing with categories is a multi dimensional problem. Regardless of how many categories there are a model is provided which can computer a risk index from a subject s relevance and an object s relevance when information flows from an object to a subject.

Assuming there are n categories C C . . . Cand the subject s and the object s relevance to the categories is represented as vectors r and r then the risk should be low if r r 1 i n otherwise the risk should be high.

In this sense relevance is treated like sensitivity levels. An alternate view is to use the Euclidean distance between rand ras a measure of risk. In this view the following two cases are both considered risky and .

Using the Bell Lapadula view a formula RImay be defined to compute risk indices for a single category. Combined risk indices from sensitivity levels and multiple categories may be computed into a single risk value in block and will be described in greater detail below.

Assuming that relevance to a category is in the range 1 M 1 means totally irrelevant and M means the most relevant . Let be a small positive real number and wbe a positive real number then for a category C RI RI log 12 The range starts from 1 instead of 0 to avoid division by zero it is also meant to avoid a large RI r r value when ris small and ris very small. The term is meant to avoid division by zero. The denominator is meant to bias the risk index toward larger r wis a per category weight to emphasize or de emphasize the importance of a category.

It should be noted that formula 12 could be considered another form of formula 7 if we choose a to be 10 and m to be log M in formula 7. Thus formula 12 retains the properties of formula 7.

Referring to an access control system is illustratively shown in accordance with an embodiment of the present invention. Access control system provides determines or computes security risks based upon subjects e.g. people or accounts and objects pieces of information to determine or assess risk and to mitigate the risk by executing mitigation plans of steps.

System includes a fuzzy MLS model which is programmed into system . A risk index module computes a risk index in accordance with the objects and the subjects for each risk dimension. A transformation module converts the risk index into a probability for each risk dimension. Model includes a boundary range which may be defined for a risk index for each risk dimension a probability for each risk dimension and or a joint probability such that the parameter defined is compared to the boundary range. Parameter values above the range are unacceptable below the range are acceptable and in the range are acceptable with mitigation measures.

A mitigation module which determines the mitigation measures which provide a residual risk wherein the parameter values are within the range. Mitigation module may also provide warnings to system administrators should changes occur or potentially risky behavior be exhibited.

System may include a processor for carrying out computations and works in conjunction with a memory . Memory or a separate secure memory may store objects and subject profiles . Objects include any information that where access is limited. Subject profiles may include information regarding limitations on access to the objects .

The Fuzzy MLS model is NOT RESTRICTED to only sensitivity levels and need to know it can also take into account other risk contributing factors such as information integrity code integrity or other risk contributing factors dimensions .

In one embodiment an implementation chooses two finite discrete sets Sand Oof allowed values of subject and object sensitivity levels or relevance . Because Sand Oare finite and discrete an off line pre computation can be done to compute the values of RI and or RI for every element in S O. This precomputation may be performed by a processor in system or a processor outside of system . The results of the pre computation may be stored in memory . So during run time of system the determination of the risk index for a particular access request becomes a simple table look up from memory . Note that all the desirable properties of RI or RI are still valid over S O.

Risk mitigation module may be included to decide a best course of action under a given set of circumstances. Mitigation action may be restricted based on the application and type of environment. Therefore policies and actions will be selected from a finite set. Mitigation module may also be employed as a warning system for identifying potential risks and suggesting a course of action. An input device may be employed to submit a request for access in system .

The request or requests can be compared to determine which requested access is more risky than the other. Using these principles formulas or algorithms can be devised to compute risk indices which are relative measurements of risk such that a larger risk index indicates a higher level of risk as computed by risk index module .

The Fuzzy MLS model can make a decision based on these risk indices because the range of risk indices can be calibrated to associate different risk indices with different risk mitigation measures. For a risk index the calibration process performed by comparison module examines the parameters of the access request that are used to produce the index and determines the perceived level of risk associated with the index to indicate one of the following conditions 

3 the risk is not too high and the access request can be granted if the risk can be reduced to an acceptable level by applying a certain risk mitigation measure against the access. The exact risk mitigation measure is determined based on the perceived level of risk by mitigation module .

The fuzzy MLS model also allows the perceived levels of risk associated with different accesses to be accumulated so that total level of perceived risk as a result of accesses to information of an application or even an IT information technology system can be determined and such risk can also be capped to be below an acceptable level.

The fuzzy MLS model provides much more flexibility in making access control decisions compared to traditional MAC model while still keep the risk associated with accesses to information at an acceptable level.

1. Determine the risk contributing factors dimension . Each dimension assigns a measurement to a subject or an object . For example for the information sensitivity dimension a subject and an object are assigned a sensitivity level which indicated how sensitive the information is.

2. For each dimension define a formula or a method that computes a risk index using a subject s measurement an object s measurement and optionally other relevant parameters such as the direction of the flow of information from the subject to the object or from the object to the subject or the mode of the requested access. The subject and the object are the ones involved in an access request in other words the subject requests to access the object in certain way. This may be performed by risk index module .

3. For each dimension determine a Hard Boundary HB such that a risk index greater that is greater than or equal to the HB indicates a risk that is too high and the access should be denied. The Hard Boundary can be infinity to indicate no risk in this dimension is considered too high. The hard boundaries are stored in comparison module .

4. For each dimension determine a Soft Boundary SB such that a risk index that is less than or equal to the SB indicates a risk that is low enough so no further action regarding this dimension for this requested access need to be taken. Of course the SB should be less than or equal to the HB. The soft boundaries are stored in comparison module .

For a dimension the range between its HB and SB is the flexibility provided by the fuzzy MLS model in this dimension. If the SB is equal to the HB then it means there is no flexibility in this dimension.

5. For each dimension determine a set of one or more risk mitigation measures in mitigation module and for each risk mitigation measure m determine its effectiveness as mapping efrom one risk index to another risk index such that for a risk index RI e RI is less then or equal to RI. A combination of two or more risk mitigation measures should generally be treated as a new risk mitigation measure because the effectiveness of the combination would depend heavily on its component measures and the way they are combined.

6. Determine a way to combine risk indices from all dimensions to produce an assessment of the overall risk associated with the requested access. This is optional although it is desirable and may be performed by the risk index module the transformation module or the comparison module .

The configuration of the access control system is operational. When a subject requests to access an object in certain modes ways an access control decision regarding this request is made through the following way 

For the requested access and for a dimension the risk index RI is computed by risk index module and a comparison is performed by module then 

Referring to blocks refer to combining risk indices from different dimensions. One goal of combining risk indices from different dimensions is to compute an overall probability of unauthorized disclosure in formula 1 as a function of these indices and thus to compute the risk. This function may be very hard to determine in practice. However a way to approximate the distribution under certain assumptions can be performed. The approximation assigns higher probability to intuitively more risky situations.

In block for each dimension compute or assign probabilities of unauthorized disclosures to risk indices from that dimension D . For each dimension imagine a random process which takes a risk index as input and outputs a 0 1 random variable such that the value 1 means an unauthorized disclosure will happen as the result of the risk from that dimension. The probability distribution of the random variable is the Probfunction formula 2 discussed above.

A boundary range can also be defined in terms of risk indices or corresponding probabilities for a dimension such that an index above the range is unacceptable below the range is acceptable and in the range is acceptable with mitigation measures. Also It should be noted that a joint probability can be computed by combining probabilities from all the dimensions and a boundary range can also be defined in terms of the joint probabilities.

In block if a risk mitigation measure is applied then the residual risk index after mitigation e RI should be used when evaluating Prob i.e. evaluating Prob e RI .

By examining or even by conjecturing the relationship among Prob s of different dimensions their joint probability can be computed in block as the final probability of unauthorized disclosure.

This approach is a process of making educated guesses. However as stated one goal is not to have accurate probabilities but to have risk estimations that are commensurate with intuition and common sense so a larger portion of limited resources are applied to mitigate more risky situations so as to increase the chance of well being and survival.

An illustrative example for combining risk indices from sensitivity levels and need to know will now be presented. Sensitivity levels may be viewed as one dimension and each category as one dimension. One choice for Probis the sigmoid function. Let RI be the risk index and RI 0 then Prob RI 1 1 exp RI mid 13 The value of this function formula 13 increases very slowly when RI is much smaller than mid it increases much faster when RI is closer to mid and saturates as RI becomes much larger than mid. The value mid is the risk index value where the probability is deemed to be 0.5 it is a tunable parameter. The value k is also a tunable parameter that controls the slope of the function. A dimension may have its own values for mid and k.

The choice of mid has a significant effect on the probabilities computed and that the probabilities become 1 or very close to 1 when the value of an object is at least two orders of magnitude or a hundred times larger than the trustworthiness of the subject. This observation is consistent with our pessimistic view of human nature. It should be noted that by choosing formula 13 the first requirement for Probdiscussed above is changed to be RI limProb RI 0

This is fine since the risk at such a low level is usually well within the acceptable range. If it is desirable to take risk mitigation into consideration the formula 13 becomes Prob RI 1 1 exp RI mid 14 

A further assumption may be made that the Probfor sensitivity levels and the Probfor a category are independent of each other. The rationale behind this assumption includes 

View the risk computed from sensitivity levels as the risk of being tempted in other words the risk of a subject disclosing sensitive information intentionally for its own gain. The more sensitive the information or the less trustworthy the subject the higher the risk is. The risk computed from a category may be viewed as the risk of inadvertent disclosure or use . It is generally very hard to divide a piece of information into the need to know and no need to know partitions while still maintaining the original context of the information. Therefore once a subject even a very trusted one absorbs some information which it has no strong need to know there is a chance the subject will inadvertently disclose or use the information.

A practical example that highlights this kind of risk includes Chinese Walls which are often used to isolate different groups of programmers where each group has the need to access its own set of specific intellectual property.

A simplifying assumption may be made that the object is monolithic and therefore information of all categories will be disclosed together if the content of the object is disclosed. Thus the probability of inadvertent disclosure PROBis PROB maxProb RI is a category 1 15 

Call the value of Probcomputed from sensitivity levels PROB and the probability of unauthorized disclosure in formula 1 PROB then PROB PROB PROB PROB PROB 16 

Formula 1 can be evaluated with PROBnow. If Probis the same for all categories then PROBcan be easily computed by feeding Probthe largest risk index among the categories.

A general approach for combining risk indices from multiple dimensions to produce a single risk value may be performed in many ways. It seems worthwhile to try to divide the dimensions into groups such that the risk relationship among members of the same group is known or can be conjectured. Then the joint probability can be computed for each group and the final PROBcan be computed by assuming the groups are independent of one another.

For risk indices to be meaningful they should be translated in to concrete decisions deny allow or allow with risk mitigation measures. The goal of risk mitigation measures is to mitigate risk so the risk will stay within an acceptable level e.g. to be below the soft boundary. From RI formula 7 the following observation may be made on risk mitigation that is consistent with intuition.

To reduce the risk we would need to reduce the value of the object i.e. to decrease ol. Such reduction usually implies changing the content of an object to make it less sensitive. In MLS terminology such change is done by a downgrader.

To reduce the risk we need to increase the trustworthiness of the subject i.e. to increase sl. In general a subject cannot be made more trustworthy instantly. But measures can be taken to make the subject less likely to do the wrong things. Such measures usually fall into two categories strong deterrence and detection and prevention which are discussed below.

In addition prevent repair or limit the damages may also be attempted. The following types of risk mitigation measures may be implemented 

Prevention to prevent real damage from happening. Examples of this kind of measures are sandboxing and other types of intrusion prevention systems.

Repair Recovery to detect that damages have happened and to repair and recover from the damages. Examples of this kind of measures are combinations of auditing audit log analysis software patching back up and restoration.

Deterrence to provide strong disincentives for wrong doings. For example detailed auditing and audit log analysis may be used to identify the wrong doers and set the stage for administrative or legal action.

Limiting Damage to assume that detrimental things will happen and take precautionary measures to limit the potential damage. Examples include limiting the input and output rate of a process reduced scheduling priority etc.

Value Reduction to use downgraders. One would generally prefer preventive measures. However no such measures or any combination of them would be perfect so other measures are necessary to ensure or just to increase the survivability of a system.

Common risk mitigation measures are illustratively described herein. While risk mitigation measures are likely to be highly dependent on the particular operation environment the application scenario and the dimension some measures that may be generally applicable include 

Intrusion Detection and Intrusion Prevention systems IDS IPS this has been a field of active research for many years. Many commercial and academic products or systems are available e.g. see the BlueBox IDS IPS in by Suresh N. Chari and Pau Chen Cheng ACM Transactions on Information and System Security 6 2 May 2003.

Rate Limiting limit the rate a subject can consume or output information to limit the magnitude of potential information leakage.

Auditing during and after an access. The coverage of the auditing could include types of activities parameters attributes of these activities resolution of time stamps of activities etc.

Decrease the access privileges of the subject after an access. This could mean temporarily reducing some of the subject s relevance to some categories temporarily decreasing the subject s sensitivity level so subsequent access from the subject would be deemed more risky and need more effective risk mitigation measures etc.

Decrease the access privileges of the subject if the subject has already accessed a large amount of sensitive information. This means if a subject knows too much then it becomes a potential weak point and therefore a higher level of precaution is needed against its actions.

Referring again to mitigation module may include one or more mitigation models for risk mitigation measures. A very simple model will now be described for illustrative purposes for a risk mitigation measure. A risk mitigation measure m is assigned a mapping ethat represents the effectiveness of m emaps a risk index RI to another risk index such that 0

A risk mitigation measure could have a cost associated with it. The costs could be used to select a measure if more than one measure can meet the risk reduction requirement.

In a real world environment e.g. in a security access system things may still happen even if risk mitigation measures are taken because the risk mitigation measures are never 100 effective and their effectiveness could be over estimated. So it would be prudent to have some safe guards in place such that bad things could be detected and their progress be stopped as soon as possible. Thus the damages could still be confined although the damages may be more serious than expected. Such safe guards provide the opportunity to continuously fine tune the risk mitigation measures without the very unpleasant wake up calls from catastrophic incidents.

To facilitate the fine tuning process and to deal with the damage caused by inaccurate estimates the risk mitigation measures implemented by module or system and the overall system design should have at least some of the following desirable characteristics 

1 detect damages before it is too late. This may mean for example real time IDS IPS or continuous analysis of audit logs in the background.

2 be able to either confine the damage or at least enable the system to survive and recover from such damage. For example auditing may not prevent damages but an audit log with enough information can tell what happened so an administrator can determine the appropriate steps for repair and recovery.

3 produce and retain enough information to show how a risk mitigation decision is made. Such information will be the input for the fine tuning process.

The formula for computing RIand RIand the implications of these boundaries on risk mitigation measures will now be described. Let V denote the object value and B denote the boundary on risk the following inequality is to be satisfied for an access to be granted probability of unauthorized disclosure 

Mitigation module therefore determines based on computed RI s whether to allow deny or allow but with certain risk mitigation measures to be taken against the access .

The fuzzy MLS model and risk management system may include many features. Some of the features to be considered are enumerated here. System may need to make a determination of subject object clearance sensitivity levels and relevance need to know . This determination may be made automatically or semi automatically including tracking the behavior and usage patterns to fine tune the levels and relevance assigned subjects and objects.

Uncertainty in subject object clearance sensitivity levels and relevance can be dealt with by a process of estimation for determining these levels and relevance. There may be built in uncertainty in the outcomes. A good security policy model should take the uncertainty into account.

Evaluation of the effectiveness and cost of risk mitigation measures should be considered to make automatic or semi automatic evaluations including fine tuning the effectiveness and cost over time.

Transformations from risk indices to probabilities should be determined and fine tuned and risk indices computed from other dimensions from the ones described above e.g. integrity. Other risk indices and ways of combining them may be considered and new and improved risk mitigation measures may be determined. Estimates and management of aggregated risk should be performed for example what to do if too much top secret data are placed into one file.

A hypothetical scenario will be presented to demonstrate how formulas for computing risk indices and their corresponding probabilities can be determined. The scenario will include the basic settings and assumptions formulas for computing risk indices from sensitivity levels and need to know and formulas for computing probabilities from risk indices.

The scenario involves a very reputable and prestigious investment firm which has access to a lot of very sensitive and privileged information about its clients and the companies it invests in. An unauthorized disclosure of any such information would potentially cause great damage to the firm such as lost business opportunities broken relationships with major clients legal liabilities and ultimately the firm s most important asset its reputation and credibility. Therefore providing its employees access to such information carries great risk yet such access is necessary for the employees to do their jobs. The firm implements a risk management system based on information sensitivity and need to know.

Sensitivity levels risk indices and probabilities are determined. The first step is to determine how to assign sensitivity levels to objects and subjects. To this end a rationale is provided for the sensitivity levels. First the firm determines that the risk associated with an access to information should be represented as the expected value of loss damage risk value of information probability of information misuse or compromise 19 

The value of a piece of information is the value of potential damage that will be incurred if the information is misused or compromised. It is assumed that the investment firm has a way to estimate the values of objects based on their information content.

The rationale for computing the probability of misuse compromise will now be shown. This rationale will lead to the rationale for sensitivity levels and RI. It should be noted that there are other reasonable definitions of value such as one based on usefulness. The concern here is risk and potential damage which is the basis for selecting the present definition for sensitivity levels.

If the misuse or compromise of a piece of information incurs no damage then it could be made public and declared risk free .

The investment firm takes a paranoid and pessimistic view that every person has a price. In other words the trust placed on any person is limited. The trust is expressed in the form S is trusted to handle at most T amount of dollars. The intuition is that if S is given an object whose value is greater than T the probability of misuse compromise increases quickly as the value of the object increases. If the object s value is less than T the probability decreases quickly as the value decreases. If V is the value of the object then the following formula is consistent with the intuition probability 1 exp 20 

1 The same V T ratio generates the same probability. In reality one would think a 1 000 000 object is much more tempting than a 10 000 object. Therefore the firm wants to emphasize the risk when V is larger. 2 The formula 20 does not capture the notion of a risk threshold. If an object s value is close to or larger than the risk threshold then any access to the object is considered extremely risky and should be handled with extreme caution if the access would be permitted at all. In which case the firm wants the value of probability V T to be 1 regardless of the value of T so as to highlight the extreme risk.

The term log M V in the denominator of the exponent emphasizes the risk when V is large and de emphasizes the risk when v is small. Using a log function provides that the emphasis on larger V would not be too strong and effects the way sensitivity levels are computed from values and how RIis derived.

The investment firm is not counting nickels and dimes or even a few dollars. The estimate and comparison of value is more in terms of orders of magnitude . For example 15 000 is an order of magnitude larger than 1 200. Therefore it is natural to represent orders of magnitude of a value using log value . The formula 21 can be represented in the following way Let log log log10 then log RI 22 This is the rationale behind formula 7 and provides an illustrative example of the meaning of sensitivity levels i.e. sensitivity level log value 

As an example the risk indices RIvalues and their corresponding probabilities without risk reduction can be computed. The probability becomes 1 or very close to 1 when the value of an object is at least two orders of magnitude or a hundred times larger than the trustworthiness of the subject. This result is consistent with our pessimistic view of human nature. The formula for risk indices namely RI has been derived from the formulas that compute probabilities of bad things . However once RI is derived and proven to have nice desirable properties it is possible to define alternate formulas to compute the probability in terms of risk indices.

Note that probability mid 0.5 for formula 23 the exact value of mid would have to be determined through heuristics or statistics. Formula 23 is a sigmoidal function that may be employed in Fuzzy Logic and artificial neural networks.

The assignment of sensitivity levels and estimation of risk resulting from information flow between two sensitivity levels has been described. Estimation of risk resulting from information flow between two levels of need to know will now be described. The Category and Relevance concept will be used to develop a set of formulas that can be used to do the risk estimation. The simplified view of this kind of risk results from a subject s inadvertent use of information whose relevance is more than the subject s need to know. The word inadvertent is emphasized to make it clear that the risk of malicious misuse of information is not considered in this example such risk is already covered above.

Once a piece of information is in a person s brain or in a process s address space then it is generally very hard if not impossible to absolutely guarantee that the information will not be used in unintended ways and the more relevant the information the more likely such uses will happen. For a category C the likelihood of inadvertent use should reflect the ratio r r object relevance subject relevance and be biased toward large r. Therefore a modified version of formula 22 is chosen to be the formula for risk indices 

Assuming that relevance to a category is in the range 1 M 1 means totally irrelevant and M means the most relevant . Let be a small positive number then RI log 24 The range starts from 1 instead of 0 so as to avoid division by zero it is also meant to avoid a large RI r r value when ris small and ris very small. The term is meant to avoid division by zero. Alternative View on Risk from Need to Know

Two alternate views on computing risk indices from need to know based on the category and relevance model are presented. The first is a two dimensional view of category and relevance. Let the values of rand rrepresent the X and Y coordinates in a two dimensional space as shown in . Then for an access and a category C we have a vector v r r .

Referring to let be the angle between vand the x axis and mbe the magnitude of v. If the access with respect to C is normal then 4. So we could use the value 4 to estimate the relative degree of abnormality and mto estimate the amount information or the lack of it if r r involved in the abnormality. If r

of course when using the lump representation we should also look at the mean deviation of from 4 which is number of categories so we would not be fooled by the case when two abnormal vectors are lumped together and become a normal one.

Computing the angle from r r may be too time consuming during run time. However given that is determined only by the ratio r r we can do a pre computation by calibrating the arc from 0 to 2 and build a table 

We use r r r instead of r rto avoid division by zero and overflow when ris too small. We could define to be 4 when r r 0 and thus implies a vector with zero magnitude and its equals 4.

There are some potential advantages by treating each category as a separate dimension and view the problem in a multi dimensional space.

If there are N categories of interest numbered from 1 to N then each subject and each object is assigned an N dimensional relevance vector vsuch that its ith element vis the subject s or the object s relevance to category i. If a subject s is initially assigned a relevance vector vand its accesses to objects are recorded over a period of time then the relevance vectors of the objects accessed by s can be mined and divided into clusters. These clusters would represent the access pattern of s and may be used in several ways 

Referring to an illustrative embodiment will be described where hard and soft boundaries are determined based on a per object value. In block a subject is assigned a clearance level which is a number between zero and Cthat indicates the degree of trust placed on the subject. Let s use cl to denote a clearance level. Note that the Cis the maximum trust that the embodiment would place on a subject and it does not mean absolute trust .

In block an object is assigned a sensitivity level which is a number between zero and Othat indicates the degree of sensitivity of the object. Let s use ol to denote a sensitivity level.

In block the formula to compute a risk index in the information sensitivity dimension for a read access may include RI the number a can be any number that is greater than one. In this embodiment we choose a to be 10. The number m can be any number that is greater than O. In this embodiment we chose m to be O 1 . The roles of cl and ol are switched for a write access. Also the number m should be greater than Cin this case. In other words the roles of subject and object should be switched for a write access when applying the formula.

In block a subject is assigned a relevance level which is a number between zero and Nthat indicates the degree of need the subject has to access information in the category. Let s use nl to denote this subject relevance level.

In block an object is assigned a relevance level which is a number between zero and Rthat indicates the degree of relevance that object has to the category. Let s use rl to denote this object relevance level.

In block the formula to compute a risk index for relevance in a category for a read access is RI log 

the number R can be any number that is greater than R. In this embodiment we chose m to be R 1 . w is a per category weight for a category i. The roles of nl and rl are switched for a write access. Also the number Rshould be greater than N in this case. In other words the roles of subject and object should be switched for a write access when applying the formula.

Risk may be combined in block . To combine risk in this example indices are combined from different dimensions to produce an assessment of the overall risk. The following concepts are defined 

An object has a value which is a measurement of the damage if the object is disclosed in an unauthorized way e.g. a way that violates the fuzzy MLS model and the hard and soft boundaries. The value could be monetary or be measured in other units.

A new formula is defined to characterize a random process that takes a risk index as input and produces a Boolean output where a true output means an unauthorized disclosure will happen. The formula computes the probability in block for a true output. The formula may include probability of an unauthorized disclosure 1 1 exp RI mid 25 The number k is a positive number and is a tunable parameter. The number mid is a positive number and is a tunable parameter it is the risk index where the probability is deemed to be 0.5.

It is possible to use other formulas to compute these probabilities. Any such formula may have the following properties 

A An object is monolithic and can only be disclosed in its entirety. B The probability computed for the information sensitivity dimension is independent of the probability computed for a category C Based on the assumptions the overall joint probability for an unauthorized disclosure is Psuch that 26 Pis the probability computed for the information sensitivity dimension. Pis the probability computed using the maximum risk index among all the Categories. This probability is chosen based on assumption A. This formula assumes that Pand Pare independent of each other based on assumption B.

The overall risk is the expected value of damage in other words overall risk value of the object 27 .

In block boundaries are defined. There are many possible ways to determine the hard and soft boundaries for a dimension a nonexclusive list is given below.

In block use the two probabilities computed in step and the formula 25 to compute the two corresponding risk indices. These two indices can be used as the hard and soft boundaries or they can be increased some to take into account the accumulation effect of formula 26 .

In block go to step and pick another object value of concern and repeat steps until all object values of concern are gone through.

Here it is assumed that there is a threshold object value such that accesses to an object whose value is greater than or equal to the threshold is considered too risky and ought to be handled with extreme caution and special care that is outside the access control system.

The steps outlined above will need the hard and soft boundaries for risk indices to be determined on a per object value basis. This is not too cumbersome in practice since it is very likely that the values of objects will be quantized into a finite set of numbers in practice. A table of hard boundary soft boundary pairs indexed by object values can be pre computed in an on line operation and can use a simple table look up.

Having described preferred embodiments of a system and method for fuzzy multi level security which are intended to be illustrative and not limiting it is noted that modifications and variations can be made by persons skilled in the art in light of the above teachings. It is therefore to be understood that changes may be made in the particular embodiments disclosed which are within the scope and spirit of the invention as outlined by the appended claims. Having thus described aspects of the invention with the details and particularity required by the patent laws what is claimed and desired protected by Letters Patent is set forth in the appended claims.

