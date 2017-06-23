---

title: System and method for security planning with hard security constraints
abstract: A method for security planning with hard security constraints includes: receiving security-related requirements of a network to be developed using system inputs and processing components; and generating the network according to the security-related requirements, wherein the network satisfies hard security constraints.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08276192&OS=08276192&RS=08276192
owner: International Business Machines Corporation
number: 08276192
owner_city: Armonk
owner_country: US
publication_date: 20080530
---
This application is a continuation of application Ser. No. 11 484 418 filed Jul. 11 2006 the disclosure of which is incorporated by reference herein in its entirety.

This invention was made with Government support under Contract No. H98230 04 3 0001 awarded by the U.S. Department of Defense. The Government has certain rights in this invention.

The present invention relates to network security and more particularly to security planning with hard security constraints.

A component environment is an environment where entities e.g. data documents machine parts or raw materials are processed by a network or multiple networks of interconnected components e.g. computers business services factory machinery etc. . Each component can consume and produce entities. The components can be connected by delivery channels. If two components are connected all or some of the entities produced by one or both of the components can be consumed by the other component.

The components can also consume entities taken from external e.g. primal sources if a corresponding source component connection is established and the entities produced can be shipped outside the system. The entities shipped outside the system are considered a final product of the component network. The component environment provides the infrastructure necessary for connecting components activating the components and delivery channels and implementing the entire production cycle delivering entities from sources to components and to consumers of the final product.

The main advantage of a component environment is component reuse. For example different networks of components can be composed as needed to generate a final product according to current business requirements. The same component can participate in multiple networks. In some environments for example in computer systems processing data in digital formats entities can be easily copied which further increases potential reuse thereby allowing the entities to be produced once but consumed multiple times by multiple processing components.

In many environments components can be rearranged dynamically to form new networks to adapt to changing conditions such as changing availability of primal sources or introduction of new e.g. more efficient components. Examples of component environments include computer systems such as semantic grid stream processing web services and autonomic computing systems as well as automated production lines and business document flows.

In many applications entities flowing in and out of a component network and between components are considered valuable entities and the value contained in the system must be protected. Value of an entity can be for example 

1 Actual monetary value of a physical object e.g. an entity or replacement value of the entity if the entity is a physical object.

2 An estimate of the loss resulting from making information public or releasing it to another party if for example the entity is a private document or an object containing secrets e.g. trade secrets or personally identifiable information protected under privacy laws .

3 A combination of 1 and 2 when the entity has both monetary value and trade secret aspects e.g. if secrets can be discovered by inspecting or reverse engineering the entity.

Special security procedures are followed in such environments to prevent potential loss of entities. Without loss of generality it can be assumed that the delivery channels between the components are trusted and secure since many well known techniques exist for creating secure delivery channels. For example when the entities consist of data cryptographic techniques can be applied to protect data in transit from being disclosed or modified.

As described above losses can occur at the components if the components leak the entities or at the consumer side if the consumers of the product leak the entities. A method for controlling security risks in these environments is to restrict the set of entities exposed to components and product consumers to the minimum necessary required for system functionality. This can be achieved with the enforcement of access control policies which are also known as hard security constraints. The term hard security constraints is used because the access control policies are strictly enforced and violation of these policies leads to a security risk that cannot be easily quantified. In other words the system satisfies the hard security constraints or it does not.

To prevent losses various security policies for access control are used. The most commonly used policies belong to one of two types Mandatory Access Control MAC and Discretionary Access Control DAC . In DAC policies the principals owning the entities are allowed to grant and revoke access to other principals. In MAC policies entities do not have owners and access to entities is controlled by the environment based on categorization of the entities and clearance levels assigned to the principals. Both classes of access control policies specify a set of formal rules that are used by an enforcement or auditing facility to decide whether a subject can access an object and take appropriate action e.g. deny access or raise an alarm .

In component environments the entities play the role of objects and components play the role of subjects. Access control policies are implemented by assigning labels to objects and subjects and specifying the access rules in terms of the labels. In particular implementation of an access control policy may require that object labels are assigned to entities and subject labels are assigned to components. Further the policy compliance of a network of components can be verified using access control rules defined by the policy.

The literature in the field of access control commonly discusses permissions for subjects to read and write objects which in the context of component environments corresponds to components consuming and producing entities. The write operation is understood as creating a new object e.g. an entity and not as modifying an existing object e.g. the entity . In particular the subject label of each component producing entity has write access to the object label of the produced entity and the subject label of each component consuming an entity has read access to the object label of the consumed entity.

In many access control systems the set of subject labels is partially ordered. For example for any subject label there can be a number of other subject labels that have read access to the same or a smaller set of object labels which at the same time have write access to the same or a larger set of object labels. In other words the subject label assigned to a component can potentially be reduced in this partial order such that the subject label still allows read access to object labels of all consumed entities and write access to object labels of all produced entities and at the same time restrict read access to a smaller set of entities.

In an exemplary embodiment of the present invention a method for security planning with hard security constraints comprises receiving security related requirements of a network to be developed using system inputs and processing components and generating the network according to the security related requirements wherein the network satisfies hard security constraints.

The network is generated using a planning algorithm. The planning algorithm receives a planning task in Planning Domain Definition Language PDDL or Stream Processing Planning Language SPPL format. The hard security constraints are Bell LaPadula constraints Biba integrity constraints Caernarvon model constraints or Role based access control constraints.

The method further comprises receiving descriptions of the system inputs and processing components. The descriptions are metadata. The method further comprises deploying the network that satisfies hard security constraints in a real production system. The network includes a downgrader.

In another exemplary embodiment of the present invention a method for security planning with access control policies comprises receiving descriptions of available external inputs and processing components receiving first security related requirements of a first network to be developed using the available external inputs and processing components and generating the first network according to the security related requirements wherein the first network satisfies access control policies.

Generating the first network according to the security related requirements comprises assigning object and subject labels to system inputs and processing components in the first network and verifying access control policies for the system inputs and processing components in the first network.

The method further comprises receiving second security related requirements of a second network to be developed using the available external inputs and processing components and generating the second network according to the second security related requirements wherein the second network satisfies the access control policies and deploying the first or second networks that satisfy the access control policies in a real production system. The first or second networks that satisfy the access control policies are newly generated networks or modifications of existing networks. The method further comprises translating privacy constraints into access control policies.

In yet another exemplary embodiment of the present invention a computer program product comprising a computer useable medium having computer program logic recorded thereon for security planning with hard security constraints the computer program logic comprises program code for receiving security related requirements of a network to be developed using system inputs and processing components and program code for generating the network according to the security related requirements wherein the network satisfies hard security constraints.

The computer program product further comprises program code for receiving descriptions of the system inputs and processing components and program code for deploying the network that satisfies hard security constraints in a real production system.

In still another exemplary embodiment of the present invention a computer program product comprising a computer useable medium having computer program logic recorded thereon for security planning with access control policies the computer program logic comprises program code for receiving descriptions of available external inputs and processing components program code for receiving first security related requirements of a first network to be developed using the available external inputs and processing components and program code for generating the first network according to the security related requirements wherein the first network satisfies access control policies.

The computer program product further comprises program code for receiving second security related requirements of a second network to be developed using the available external inputs and processing components and program code for generating the second network according to the second security related requirements wherein the second network satisfies the access control policies program code for deploying the first or second networks that satisfy the access control policies in a real production system and program code for translating privacy constraints into access control policies.

The foregoing features are of representative embodiments and are presented to assist in understanding the invention. It should be understood that they are not intended to be considered limitations on the invention as defined by the claims or limitations on equivalents to the claims. Therefore this summary of features should not be considered dispositive in determining equivalents. Additional features of the invention will become apparent in the following description from the drawings and from the claims.

An automated method for constructing component networks or modifying existing networks such that the resulting network satisfies a chosen access control policy e.g. a hard security constraint according to an exemplary embodiment of the present invention will now be described.

Referring now to a method for security planning with hard security constraints according to an exemplary embodiment of the present invention is shown. Here descriptions of each available system input and processing component are created . The descriptions may be entered into a database or a knowledgebase computer system for simplified search and data management. The descriptions may include for example security properties as well as specific properties describing the content of entities and functionality of the processing components.

A description of requirements describing results or the desired outcome of the processing are input by a user . In other words security requirements of a network to be developed using the system inputs and processing components is received. The description of the user requirements includes for example a definition of a maximum accepted security risk level. This level may be fixed by a system wide security policy or chosen by the user from a range allowed by the system wide security policy.

After the descriptions of the processing components system inputs and user requirements become available processing components are selected and a network of processing components which satisfy an access control policy is created . The network is created by matching an output of a station or a primal entity to an input of another station or a primal entity and specifying which outputs in the network are the final outputs that contain the product while satisfying the access control policy.

The network is then implemented e.g. deployed and used in a real production system . It should be appreciated that steps and can be repeated several times shown by the dotted line of for constructing an alternative composition e.g. network of processing components that satisfy different user objectives.

Referring now to the process of generating a component network based on information about processing components information about system inputs and product requirements is illustrated. A result produced by the network must match the product requirements while at the same time satisfy access control policies. The network comprises a selection of the processing components system inputs and interconnections between the processing stations and between the system inputs and processing stations .

Now that the method for constructing component networks or modifying existing networks such that the resulting network satisfies an access control policy has been described examples of the access policies hereinafter referred to interchangeably as hard constraints access policies or security policies that must be satisfied when constructing a component network will be described.

First it is to be understood that to implement access control within component environments using hard constraints the following considerations must be addressed 

1 The object network and subject labels must be assigned to entities and components within each component network.

2 Access control rules must be verified for all entities produced or consumed by components. Further if there is a choice in assigning subject and object labels the labels must be assigned to minimize security risk.

A multi level security MLS Bell LaPadula policy with Biba integrity labels will now be described. This policy will also be referred to as MLS .

In a componentized MLS system each of the components is assigned a single access class on which it operates. Each entity is assigned a label that specifies a minimum access class required to receive the entity. A security policy is comprised of three types of rules 

1 Each component cannot accept any entities that require an access class higher than the component s access class.

2 Each component must label all entities that it produces with a minimum access class equal to or higher than the component s access class. This rule ensures that entities are not relabeled with lower access classes or are not contained partially or completely in the outgoing entities that have lower access classes and thus helps to avoids losses. However special purpose components after a mandatory review of their operation can be authorized to violate this rule and assign lower access classes to output without incurring a security risk.

3 The recipient of the products produced by the network of components is also assigned an access class and therefore the products must be entities labeled with the access class of the consumer or lower.

It is to be understood that violation of any of these rules except those by special purpose components according to their permission results in a security risk. In other words if the rules are violated there exists the possibility that the value is lost.

Since a model of the method for constructing component networks or modifying existing networks such that the resulting network satisfies a chosen access control policy builds upon MLS and Biba integrity models the model will be described with respect to information but the model can be easily extended for secure processing of physical objects.

The processing components will be referred to as Processing Elements PEs and one way communication will be modeled between the PEs with streams of data flowing between output and input ports of the PEs. The correctness of this model flows from the correctness results known for MLS and Biba integrity labels.

1 Labeling data objects according to the sensitivity of information contained therein and the integrity of their data.

2 Describing access permissions and restrictions associated with the subject e.g. a user of the PEs .

Security labels are elements of label set on which a partial order is defined. A partial order denoted by is a relation on set if it is 

The partial order is used to control access to objects. Here the necessary condition for allowing read access of a subject having label Lto an object with label Lis that LL. If this condition is not satisfied a read access request will be rejected.

For write requests the reverse relationship must hold. Here the subject having label Lcan be allowed to write an object with label Lonly if LL.

In security models that allow the use of downgraders each subject is assigned two labels e.g. a read label and a write label. In the former rule mentioned above the read label of the subject is used in place of the subject label L and the write label is used in place of Lin the latter rule.

The security models described above are referred to as lattice based models where the set is referred to as the lattice.

For each inquiry planning request the credentials of the user making the request uniquely define the user s security label e.g. user label . The user label plays two roles during the construction of a plan graph 

1 As a constraint on the output stream labels. All output stream labels must be less than the user label in partial order.

There are no other uses of the user label. In particular the user label is not used to mark the PEs as belonging to any single user.

Primal Stream and User Request Labels followed by Derived Stream and PE Labels will now be discussed.

Each object entering the stream processing system must have a security label assigned thereto. The following information enters the system 

Each data source specification includes the security label associated with the primal stream produced by the data source. As with all stream labels the primal stream labels must be equal or exceed in partial order the maximum of all possible labels of all objects that may travel via this stream.

The primal stream labels are assigned by Data Acquirers during the process of registering the data source in the stream. The Data Acquirers may use their judgment for assigning the labels or use automated data analysis tools that can assist them in defining the labels based on the data that is coming through the data source. These data analysis tools can be developed independently of security planning.

Inquiry specification including inquiry parameters such as search criteria carries the label of the requesting user. If any values from inquiry specification are supplied to the PE e.g. as execution parameters these values are treated as inputs to the PE for purposes of label computation and thus the output of the PE will normally carry the label identifying at least the requesting user if the PE is not a special purpose trusted PE which is allowed to reduce labels of processed information.

Labels of derived streams are computed using the transformation formula as described in this section. For each PE the following labels can be specified 

2 The output minimum label Land the output maximum label Ufor each output port k of the PE k 1 . . . K assume LU .

Each of these labels may be omitted in each port specification. For generality during computation it is assumed that if the input maximum label is not defined for input port j then C where is the largest label in the partial order i.e. l for all labels l. Similarly if the maximum output label is not defined for port k it is assumed that U . If the output minimum is not specified for output port k then it is assumed that L 0 where 0 is the smallest label in the partial order i.e. 0l for all labels l.

If U for some 1 k K then the PE is considered a special purpose trusted PE that must be trusted to write lower security labels than those assigned to the information it receives. Appropriate code review and certification must be performed before registering this PE in the system to ensure that the PE will not leak sensitive information under lower sensitivity labels.

To compute the output label l for each output port k k 1 . . . K the following additional information is needed 

1 For each input port j j 1 . . . J the label lof the stream connected to that port. The planner must ensure that lC.

2 Additional information regarding input label l. It is assumed that l is equal to the user label if the PE has been configured with parameter values originating from the inquiry specification and l 0 otherwise.

Given a directed acyclic graph representing the workflow this formula can be applied in iteration starting from the sources to compute the label of workflow output based on the labels of workflow inputs.

In the Caernarvon model a security label is a triple L s c i where s is the secrecy level c is the category set and i is the integrity level. Each of these components is defined in more detail below. In addition s s L c c L i i L .

Secrecy level is an integer in the interval between constants Sand S. Secrecy level reflects the sensitivity of the information. For example the higher the sensitivity the higher the secrecy level. Each number in this range corresponds to one of the secrecy labels such as top secret secret confidential or unclassified . It is assumed that the ordering is preserved when the labels are mapped to the integers in the S S interval where Scorresponds to the most sensitive information and Sto the least sensitive information.

In the labels assigned to streams secrecy level corresponds to the maximum secrecy level over all objects that can pass through the stream.

Category set is the set of categories to which the object belongs. An object can belong to zero or more categories. A planning solver can view c as a zero one set membership vector which contains ones for every category that is relevant for the object and zero for all other categories.

In the labels assigned to streams category set corresponds to the union of category sets of all objects that can pass through the stream.

Integrity level describes trustworthiness of the information. It is an integer in the interval I I . It can correspond for example to an integrity level in the Biba integrity model.

A partial order is defined as follows. Label L s c i precedes label L s c i in the partial order and LLis written if and only if each of the following conditions is satisfied 

The following notation is used to represent such a security label assuming letters A Z denote available categories 

The combination operations on the labels for any two labels L s c c and L s c i are defined as L L maxs s c c mini i and symmetrically L L mins s c c maxi i .

Now that several access control policies have been described the implementation of security planning with hard constraints will be discussed.

The implementation of security planning with hard constraints requires representing the user data source and PE labels as predicates in the planning domain. The methods for representing these labels typically depend of the expressivity of the planning task description language and on the nature of the labels. Two exemplary methods will be described below.

It is to be understood that both examples consider security labels of the Caernarvon model described above. One of the examples uses Planning Domain Definition Language PDDL representation for planning tasks and the other uses Stream Processing Planning Language SPPL representation. Depending on the representation different planners can be used to construct plans. Although various planners exist for both PDDL and SPPL if the planning task is described correctly e.g. such that the security policy rules described above for general labels from the lattice are expressed and enforced by the planner the resulting workflows will be compliant with the security policy independent of which planner is used.

It should also be understood that elements of the description of the planning task given below are necessary but not sufficient and other constraints such as input output data type compatibility between communicating PEs etc. can be added.

A PDDL encoding of Bell LaPadula policy with Biba integrity labels in which each processing component is represented by a PDDL action and a stream is represented by a PDDL object will now be described.

A general workflow planning problem in PDDL uses a straightforward approach representing each stream by a stream object. For simplicity it is assumed that the composition rules in the system are represented by a system of types. As long as a stream contains a type required by an input port of the component the stream can be connected to the port resulting in a valid workflow. More complex rules including various optimization criteria can also be implemented. Since all objects to be used are of type stream one PDDL type is defined as follows 

One predicate has type X s stream is defined for each type X. If true in some state it means that stream s carries type X in that state. In addition it is needed to keep track of initialized streams so that newly created streams do not overwrite a description of the streams produced by other actions. Therefore a predicate unused s stream is defined which if true in some state means that stream object s is not yet an instantiated stream in that state and it is safe to use it as an output stream of an action. A special predicate goal reached is introduced that holds in the goal state. Here is an example predicate definition for the planning domain 

A goal reaching action is also introduced. The precondition of this action can be used to describe conditions the end user requirements place on the output stream. Within the model of composition rules these conditions are given in the form of type requirements just like action preconditions. This action has a single effect of setting the goal reached predicate.

As will be shown in this example each action specifies required types of input ports in the precondition and the produced types are assigned to new streams in the effect statement. Also it is required that each output stream is not used before the action is applied and is to be marked as used in the effect of the action making them unchangeable by other actions after this action initializes the objects.

The above statements describe the planning domain. To describe the planning problem objects and initial and goal states need to be described. First enough stream objects are introduced so that the total number of available objects would be sufficient for any practical workflow created by the planner. In this example 200 stream objects are created. In PDDL each object must have a name therefore arbitrary names are assigned to the objects. These names are later used to establish connections between input and output ports.

Initial state describes the types of primal streams and marks every non primal stream object as un initialized.

The domain and problem description introduced above represent the workflow composition problem in PDDL. Any solution e.g. valid plan constructed for this problem can be directly mapped to a valid workflow achieving the goal. In practical implementations domain specific optimization criteria and or resource constraints may be added to require that the best possible solution is produced.

However the resulting workflow may not be compliant with the security policy. Thus a set of predicates describing security labels assigned to the streams needs to be introduced. The predicates are as follows 

1 For each category X a predicate no category X s stream is introduced where s is a variable that represents a stream object. If in any state this predicate is true for stream s the category set of the label assigned to stream s does not contain category X in that state.

2 For each secrecy level V which by definition is an integer in a limited range a predicate secrecy below V s is introduced which if true in some state means that a secrecy level of the label assigned to stream s is less than V in that state.

3 For each integrity level U which also is an integer from a limited range a predicate integrity above U s is introduced. This predicate if true in some state means that in that state stream s has label with an integrity level higher than U.

1 For each primal stream S its security label L s c i is translated to the predicates defined above. In particular the following additional predicates must be included in the init statement 

2 For each action corresponding to a component labels corresponding to input ports C 1 j J and labels corresponding to output ports L U 1 k K are reflected in action description as follows 

As can be gleaned the workflow constructed by the planner for the updated problem representation will satisfy the security policy. The predicates introduced for implementing the security model uniquely describe labels assigned to streams in the composed workflow.

A similar approach can be used to describe the workflow composition problem using SPPL. This will now be described.

The type matching predicates in SPPL are defined as part of the CLEAR logic group and stream variables and unused predicates are no longer necessary 

Description of action describes preconditions and effects on every input and output port correspondingly. In SPPL goal reaching action is no longer needed.

Since declaring explicit stream objects are not needed in SPPL the only declarations that must be present in problem definition are goal and init statements. One init statement per primal stream and one goal statement per output stream are required.

The problem described in SPPL can be solved by a suitable solver which will produce a feasible workflow. However for the workflow to satisfy security constraints additional security predicates must be introduced. The predicates are defined as part of an AND logic predicate propagation group by specifying andlogic in the predicate declaration statement. For each security predicate defined in PDDL a similar predicate is defined in SPPL but without the stream parameter. In particular 

1 For each category X a predicate no category X is introduced. If in any state this predicate is true for a stream the category set of the label assigned to stream s does not contain category X in that state.

2 For each secrecy level V which by definition is an integer in a limited range a predicate secrecy below V is introduced which if true in some state means that a secrecy level of the label assigned to the stream is less than V in that state.

3 For each integrity level U which also is an integer from a limited range a predicate integrity above U is introduced. This predicate if true in some state means that in that state the stream has a label with an integrity level higher than U.

Similarly to PDDL encoding the use of the predicates in the SPPL problem and domain description are defined as 

1 For each primal stream its security label L s c i is translated to the predicates defined above. In particular the following additional predicates must be included in the init statement 

2 For each action corresponding to a component labels corresponding to input ports C 1 j J and labels corresponding to output ports L U 1 k K are reflected in an action description as follows 

It is to be understood that this SPPL domain and problem description can be used to compose workflows complying with the security policy with or without plan quality optimization and or resource constraints. Additional constraints and optimization objectives may be added but any plan feasible in this description will comply with the policy.

A list of assumptions needed to have an effective algorithm for planning using hard constraints is as follows 

1 Workflow composition based on type matching and security hard constraints as used in PDDL and SPPL representations above is an NP complete decision problem.

2 In the absence of trusted components e.g. if there are no components with U the composition problem can be solved efficiently in time O m where m is the number of available components.

3 Assume that for all inputs of all components there are no security preconditions e.g. for all components C . In the following cases efficient algorithms exist 

Although the embodiments of the present invention have been described above as using MLS access policies for security planning an alternative embodiment employing a multi set attribute policy MSA in conjunction with the aforementioned hard constraints can also be used for security planning.

Here the translation of MSA policy and MSA metadata into Caernarvon policy and metadata followed by the application of the planning methods described in this invention will be described. First the structure of MSA policy rules will be briefly discussed and then an outline of the process of translating MSA labels to Caernarvon labels will be given.

MSA uses labels to annotate objects and subjects. Each MSA label consists of 0 1 or more attribute risk pairs where 1 attribute is the name of an attribute denoting a category of privacy sensitive information and 2 risk is the value characterizing the likelihood of deriving this information from the data annotated by the label.

At most one attribute risk pair for each attribute is allowed in a label. In addition to the pairs the MSA label may contain an integrity level value.

In an MSA model the privacy policy can also specify input attribute combination constraints as part of the subject label or labels. However here a restricted version of an MSA model is considered where such constraints are not specified.

The following label mapping procedure can be used during the mapping of MSA policy to Caernarvon policy. Once a set of categories is created the labels are processed for each component separately to define the labels C Uand Lfor each component. The procedure is as follows 

1 Create a new MLS category for every unique combination of attribute risk used in any MSA label. All MSA labels used in the description of components user credentials or sources should be considered during this operation. For simplicity the MLS category attribute risk corresponds to the MSA pair attribute risk .

4 All MSA SELECTION and ADDITION labels are translated to output minimum labels L such that for all outputs k 

5 For all MSA WRITE labels the Llabel is computed similarly to the ADDITION labels and Uis chosen to be equal to L.

Due to the similarity of propagation and access rules it is straightforward to verify that after the labels are mapped if the rules of the Caernarvon policy are enforced in the resulting system the rules of MSA model will be enforced automatically. Thus a Caernarvon policy and an MSA policy can be enforced simultaneously within the same workflow using the method described in the embodiments above. To enforce both policies it is necessary to ensure that the categories created by the mapping procedure do not overlap with the original set of categories. In addition the computation of MLS labels must start not from empty category set but from the category set defined by the Caernarvon metadata and the secrecy levels must be set based on the same metadata.

According to an exemplary embodiment of the present invention a network can be automatically constructed based on metadata describing components sources and product requirements wherein the network satisfies the specified requirements and complies with an access control policy. By constructing a network according to an exemplary embodiment of the present invention security risks can be managed and mitigated automatically as compared to existing manual or single level security methods. Thus analysis of the network can be increased potential human errors resulting from manually constructing such a network can be decreased and entities of multiple security levels can be processed. In addition a secure large scale system that is composed of hundreds or even thousands of networks can be verifiably constructed.

By automatically constructing networks after necessary reviews and certification the planner can act as a trusted component thus reducing the need for employing trusted personnel for composing the networks that involve sensitive e.g. valuable sources or components. For example users with low access rights can request workflows processing data from sensitive sources or using sensitive algorithms provided that the data is downgraded during processing. As compared to traditional systems these users would need assistance from users with higher privileges to achieve this thus resulting in delays. In addition the metadata describing the components and entities can be sensitive e.g. valuable thus providing additional trust requirements to the planner.

It is to be understood that the present invention may be applied to any lattice based secrecy model or any lattice based secrecy model augmented by a lattice based data integrity model. The present invention may also be applied with or without trusted components such as secrecy downgrades and integrity upgraders.

It should also be understood that the present invention may be implemented in various forms of hardware software firmware special purpose processors or a combination thereof. In one embodiment the present invention may be implemented in software as an application program tangibly embodied on a program storage device e.g. magnetic floppy disk RAM CD ROM DVD ROM and flash memory . The application program may be uploaded to and executed by a machine comprising any suitable architecture.

It is to be further understood that because some of the constituent system components and method steps depicted in the accompanying figures may be implemented in software the actual connections between the system components or the process steps may differ depending on the manner in which the present invention is programmed. Given the teachings of the present invention provided herein one of ordinary skill in the art will be able to contemplate these and similar implementations or configurations of the present invention.

It should also be understood that the above description is only representative of illustrative embodiments. For the convenience of the reader the above description has focused on a representative sample of possible embodiments a sample that is illustrative of the principles of the invention. The description has not attempted to exhaustively enumerate all possible variations. That alternative embodiments may not have been presented for a specific portion of the invention or that further undescribed alternatives may be available for a portion is not to be considered a disclaimer of those alternate embodiments. Other applications and embodiments can be implemented without departing from the spirit and scope of the present invention.

It is therefore intended that the invention not be limited to the specifically described embodiments because numerous permutations and combinations of the above and implementations involving non inventive substitutions for the above can be created but the invention is to be defined in accordance with the claims that follow. It can be appreciated that many of those undescribed embodiments are within the literal scope of the following claims and that others are equivalent.

