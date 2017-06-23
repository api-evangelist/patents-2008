---

title: Relational database method for technology program management
abstract: A Technology Program Management Model (TPMM) for management of technology development. The TPMM is an activities-based model that is subdivided along technology readiness level (TRL) boundaries into phases of technology development that logically progress from concept to operational capability and readiness for transition to the customer/end user. The TPMM provides a standardized approach to technology development that incorporates systems engineering and programmatic principles and practices with transition management in a stage-gated process for TRL-based maturity assessment. The TPMM includes a relational database that relates the activities to one another, to entry and exit criteria for each phase, and to documentation that demonstrates that the activity meets the requirements of each phase.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08010584&OS=08010584&RS=08010584
owner: The United States of America, as represented by the Secretary of the Army
number: 08010584
owner_city: Washington
owner_country: US
publication_date: 20080922
---
This application is related to and claims the benefit of priority to Provisional Application U.S. Ser. No. 60 974 718 entitled Relational Database Method for Technology Program Management by Craver et al. filed Sep. 24 2007 in the U.S. Patent and Trademark Office the contents of which are incorporated herein by reference.

The invention described herein may be manufactured used and licensed by or for the U.S. Government for governmental purposes without payment of any royalties thereon.

The present invention relates generally to management of technology development programs and more particularly to a method for organizing a relational database used for storing data related to the management of technology development programs.

Technology development is often carried out using a stage gate process with a starting point defined stages of development bounded by gates and an ending point. The process requires a logical flow starting at discovery of an idea based upon a need and ending at successful integration into a product or system that satisfies that need.

During a stage money is allocated and work is performed. Each stage has specific characteristics against which it is measured to determine whether the stage has been completed. These characteristics include documentation to be delivered i.e. deliverables funding allocation metrics and goals i.e. stage exit criteria . Once a stage is completed deliverables delivered funding spent goals met and metrics satisfied a decision is made whether to move forward with the program. This is the gate. Each gate is a decision point for the program to move to the next stage and is typified by a program review.

Every science and technology organization faces the challenges of effectively managing technology development and successfully transitioning technologies to a customer or end user. Often the technology manager does not have clear goals established to know when the technology is finished or when the technology is needed by the acquisition customer and sometimes the technologist is still refining the technology when the acquisition customer needs it. Transition may be an afterthought rather than being considered as part of technology development and there may be a lack of customer identification or involvement. In addition programs that attempt to integrate with immature technologies usually face cost growth and schedule delays and design stability is not achievable with immature technologies.

Technology development organizations need to be able to assess the readiness of critical technologies for incorporation into a product or system. The Department of Defense DoD and many commercial organizations have adopted the use of technology readiness levels TRLs for making such an assessment. TRLs are metrics based indicators of any gaps that exist between the current maturity of a technology and the maturity required to be successfully incorporated in a product or system. If a technology does not meet a pre defined TRL score the risks of including the technology in product or system development can be determined and steps can be taken to close the gap.

The TRLs are measured along a scale of 1 to 9 for example with 1 being the lowest level of technology readiness such as an initial paper study and 9 indicating successful use on the intended product or system. The higher the TRL level of key technologies that are included in a product or system the greater the probability of meeting cost schedule and performance requirements. As an example show the TRLs used by the DoD to assess hardware and the documentation typically created or referenced to support the level assigned to the technology. For a more complete description of TRLs as related to the DoD acquisition process see United States Deputy Under Secretary of Defense for Science and Technology Department of Defense May 2005 the contents of which are incorporated herein by reference.

TRL levels are often assigned to particular technologies by forming teams that systematically work through the vague TRL definitions. This can be a very time consuming and subjective process that can sometimes lead to more questions than answers. Often consistent guidance on how to assess TRLs does not exist to support these teams. Technology programs that can confidently describe their technical readiness are at much lower risk of failure to successfully transition or meet the needs of their customers end users.

A tool is needed that aids program managers in the planning execution and transition of specific technologies being developed. Such a tool is needed to ensure that the right questions are being asked at the right times during the development of advanced technologies to support successful transition to the customer or end user and to more efficiently and consistently assess the TRL of a particular technology.

The previously described problems are solved by a Technology Program Management Model TPMM . The TPMM is a comprehensive technology management model and as such contains activities and entry exit criteria that cover a wide range of management disciplines including Technical Programmatic and Transition which makes it a multi dimensional tool.

The TPMM is an activities based model that is subdivided along TRL boundaries into phases of technology development that logically progress from concept to operational capability and readiness for transition to the customer end user. The TPMM provides a standardized approach to technology development that incorporates systems engineering and programmatic principles and practices with transition management in a stage gated process for TRL based maturity assessment. This process enables the technology manager to better demonstrate technology maturity and readiness facilitating advancement to the next readiness level and development phase.

The TPMM activity model has been implemented in a relational database. The database houses the systems engineering based activities to be accomplished during each TRL phase of technology development. The relational structure includes multiple tables which are summarized below.

The activities are grouped into categories and subcategories. A Categories table holds descriptors of the types of category. A SubCategories table holds descriptors of the types of subcategory.

A Roles table is used to describe an organization that is responsible for completion of a selected activity.

A Groups table is used to describe a group within the organization that has responsibility for completing the activity. A GroupMapping table is used to link a group to an activity.

Activities that are logical extensions of one another are virtually connected together to form chains of activities i.e. threads . An ActivityThreads table describes a unique identifier of a thread that connects activities. A ThreadTypes table stores information for identifying threads and associating an activity with a particular thread group. An ActivityThreadLinks table is used to link an activity to a thread.

External organizations such as regulatory agencies may impose external criteria on the management process. An ExtCriteria table provides names and unique identifiers for the external criteria. An ExtCriteriaItems table provides descriptor data to define the external criteria. An ExtMapping table is used to link the external criteria to the Activities table.

The TPMM is subdivided along TRL boundaries into phases of technology development. A Phases table is used to identify the distinct phase in which an activity occurs.

The results of each activity are documented by one or more deliverables e.g. a report study plan strategy etc. in any given phase. A Deliverables table stores pointers to the names of the deliverables.

When a selected activity is associated with a deliverable product a template for that deliverable is provided to the user. A Templates table stores data attribution information for the deliverable templates. An ActivityTemplates table is used to link an activity to a template.

Deliverables may be updated in versions. A Versions table is used to provide a unique identifier for a particular version of a deliverable.

A section represents a distinct block within a deliverable. A Sections table stores information about the sections. A SectionVersions table is used to link sections to specific versions.

A Properties table is used to store information that is used repeatedly such as the name of a particular technology project.

A Predecessors table is used to populate dependency data between activities during bulk loading and initialization operations.

A Milestones table is used to provide a way of correlating an activity with a milestone or event during which the deliverable is due to be reviewed or evaluated and typically represents a gate in a phase at which a particular section in a deliverable document must be completed. A MilestoneTypes table is used to identify a type of milestone at which a particular deliverable or version of a deliverable is to be made available. The milestone type typically represents a set of particular milestones of a similar nature that occur across multiple phases.

A VerMethods table stores information about verification methods that may be used to show that an activity is completed successfully. A Verifications table is used to link a verification method to an activity.

An ExitCriteria table stores information about exit criteria which are used to determine whether a deliverable in question meets the requirements of the technology phase in which it is executed.

The database construct is used to relate the activities to one another to required entry and exit criteria necessary to execute each activity and to the documentation necessary to demonstrate that the activity meets the requirements of each phase. Relationships have been established in the data model that link the performance of activities to key deliverable documentation and force critical related activities into consideration. Mechanisms have been designed into the activity model that permit the inclusion of external criteria beyond the standard set for circumstances when such criteria may exist.

According to one aspect of the present invention a method for creating and organizing a relational database used for storing data associated with the management of a technical development program includes creating an activities repository for storing data associated with activities performed during the development of a technology dividing the development program into phases and creating a phases table for storing data associated with phases in which the activities occur and creating a deliverables repository for storing data associated with deliverables generated during the development of a technology.

According to another aspect of the present invention a computer program product has a computer useable medium with computer program logic stored therein for enabling a computer to store data associated with the management of technical development programs. The computer program logic includes a relational database organization having an activities repository for storing data associated with activities performed during the development of a technology a phases table for storing data associated with phases of the development program in which the activities occur and a deliverables repository for storing data associated with deliverables generated during the development of a technology.

According to still another aspect of the present invention a method for using a relational database for accessing and storing data associated with the management of a technical development program includes constructing the database by creating an activities repository for storing data associated with activities performed during the development of a technology dividing the development program into phases and creating a phases table for storing data associated with phases in which the activities occur and creating a deliverables repository for storing data associated with deliverables generated during the development of a technology.

Various aspects and advantages of the invention will become apparent from the following detailed description taken in conjunction with the accompanying drawings wherein like numerals refer to like parts throughout.

Hereinafter embodiments of the present invention with particular application to the Department of Defense DoD Government Acquisition process will be described in detail with reference to the attached drawings. The present invention may however be embodied in many different forms and should not be construed as being limited to the embodiments set forth herein rather these embodiments are provided so that the present disclosure will be thorough and complete and will fully convey the concept of the invention to those skilled in the art. For details regarding the DoD acquisition process see United States Defense Acquisition Agency Department of Defense Defense Acquisition Guidebook July 2006 the contents of which are incorporated herein by reference.

The Technology Program Management Model TPMM is a high fidelity activity model that provides a flexible management tool to guide technology managers in planning managing and assessing their technologies from discovery of an idea through successful transition culminating at integration with an intended product or system. The TPMM provides a standardized approach to technology development that incorporates systems engineering and programmatic principles and practices with transition management in a stage gated process for TRL based maturity assessment. This process enables the technology manager to better demonstrate technology maturity and readiness facilitating advancement to the next readiness level and development phase.

The TPMM activity model as shown in the flow diagram of has been implemented in a relational database which is described in more detail below. The TPMM is subdivided along TRL boundaries into phases of technology development that logically progress from concept to operational capability and readiness for transition to the customer end user. The TPMM is therefore broken down into six distinct phases corresponding with the first six TRL levels Discovery TRL Formulation TRL Proof of Concept TRL Refinement TRL Development TRL and Demonstration Transition TRL .

The TPMM is based upon a stage gate process. Each gate of the TPMM is a Technology Program Review TPR which is conducted at the end of each stage i.e. phase to determine whether a program has met the goals of the current TRL and is to advance to the next phase of development. The TPR includes two individual assessments. The first assessment is a Technology Readiness Assessment TRA which determines whether the program has achieved a specific readiness level. During the TRA the critical technologies are evaluated against the technical criteria of the TPMM at the appropriate TRL for achievement of performance goals. The second assessment is a Technology Advancement Assessment TAA for evaluating the planning efforts for the next phase which considers the programmatic documentation cost schedule funding and risk along with an analysis of the transition planning products in making an advancement decision for the technology program. The outcome of the TAA is a decision to either 1 go to the next stage 2 abandon the program 3 suspend the program or 4 recycle the program back into the current stage to satisfy some unsatisfied criteria. Once a decision to go forward to the next stage has been made funding must be allocated deliverables defined and goals and metrics specified for that stage. Then the work for that stage commences. The TPMM uses the TRL gates as the basis for each stage of its stage gate process.

Rather than considering transition as an afterthought the TPMM applies an integrated transition management focus throughout the development lifecycle with transition mechanisms that document the development effort and form the basis for transitioning the technology. These mechanisms include the TRA the TAA a Technology Development Strategy TDS and a Technology Transition Agreement TTA . The TDS is a plan for maturing promising key technologies including prototypes that will be built and tested performance goals schedule funding specific exit criteria etc. The TTA is an agreement with the customer end user and is divided into three versions INTEREST INTENT and COMMITMENT that document successive levels of commitment between the technology program and the customer end user.

The TPMM focuses on activities e.g. programmatics systems engineering transition management risk and verification tasks to be performed for each TRL. The activities can be tailored to any given technology development program. The results of each activity are documented by one or more deliverables in any given phase.

The TPMM activity model has been implemented in a relational database. The database houses the systems engineering based activities for use in each TRL phase of technology development. The database construct is used to relate the activities to one another to required entry and exit criteria necessary to execute each activity and to the documentation necessary to demonstrate that the activity meets the requirements of each phase. Relationships have been established in the data model that link the performance of activities to key deliverable documentation and force critical related activities into consideration. Mechanisms have been designed into the activity model that permit the inclusion of external criteria beyond the standard set for circumstances when such criteria exist. The TPMM including a listing of the activities and deliverables associated with each TRL phase is further described in Craver Jeffrey T. and Michael S. Ellis United States Army Space and Missile Defense Command v.2 2006 which is incorporated herein by reference.

In addition the database facilitates effective program management through the creation of project unique instances of tailored activity sets that implicitly describe standard criteria in conjunction with TRLs for performing TRAs . The technical manager can plan a technology development program for a specific project by tailoring the core activity set in the database and including only those activities that are deemed necessary to accomplish the stated goals.

In the tables PK refers to primary key FK refers to foreign key U refers to unique and I refers to indexed i.e. an index structure is used to access records . A primary key is a unique identifier of data combinations in a table. A foreign key is a reference to a primary key or another unique key of another table. The tables are linked via various one to many relationships. A line drawn between two tables indicates a foreign key relationship. Arrows connect foreign keys to the tables in which the foreign keys are primary keys. An arrow points from a table that contains a foreign key to a table in which the foreign key is a primary key. For example FK in the ActivityThreads table refers to PK in the ThreadTypes table see . The FK I and U symbols also contain a number qualifier such as FK and FK to distinguish between multiple keys of the same type within the same table. The qualifiers are used to number the instance of each type within a table. Some tables have compound primary keys. For example the ActivityTemplates table has a compound primary key that includes an ActivityID and a TemplateID.

Referring to the TPMM is an activity centric data model and as such an Activities table is central to the functionality. Activities are at the core of every behavior and are the primary drivers in the development of deliverables. For each technology project instantiated activities selected from this table form the basis of the work to be performed for that project. The selection of an activity invokes its output i.e. deliverable . Table I defines the fields of the Activities table .

The activities are grouped into categories and subcategories. The categories include for example Programmatics Technical Transition Management and Verification. A Categories table holds a descriptor of the category type. Table II defines the fields of the Categories table . The Programmatics category is divided into the subcategories of Plans Cost Schedule Risk Funding Contracting and Data Management. The Technical category is divided into the subcategories of Analysis Systems Engineering Hardware Development Software Engineering and Software Development. The Transition Management category is divided into the subcategories of Insertion and Transition and the Verification category is divided into the subcategories of Reviews and Testing. A SubCategories table holds a descriptor of the subcategory type. Table III defines the fields of the SubCategories table . An example of a display showing activities by category and subcategory is shown in .

A Groups table is used in conjunction with a GroupMapping table to correlate an activity with a group in an organization having responsibility for completing the activity. Table IV defines the fields of the Groups table . Table V defines the fields of the GroupMapping table .

A Roles table is used to describe the organizational role typically responsible for completion of a selected activity. Roles are tailorable but typically set to common names such as Technology Manager Systems Engineer Test and Evaluation etc. Table VI defines the fields of the Roles table .

The TPMM is a threaded model in which activities that are logical extensions of one another are virtually connected together across phase boundaries and within phases to form a chain of activity i.e. a thread . The threads traverse project stages and form dependencies with predecessor successor relationships throughout the project lifecycle. In this way deliverables can migrate throughout the technology development project lifecycle and activities that are critical to the ultimate success of a thread will not be overlooked or will at least be considered. For example a Program Management Considerations thread includes the activities of 1 perform cost status reporting 2 perform schedule status reporting 3 perform risk management and 4 construct technology funding estimate. An example of a user display showing another thread is illustrated in .

These sets of threaded activities form the basis of the technology development body of knowledge or knowledge base . Basically a knowledge base provides a way to reapply known solutions to current problems that can be used by others less experienced in the problem area. As a knowledge based system the TPMM provides capabilities for direct knowledge management establishment of a common language a mechanism for mentoring new employees and the seeds of a standard process for technology development and readiness maturity assessment.

A ThreadTypes table is used to house the mechanism for identifying threads and associating an activity with a particular thread group. An ActivityThreads table describes the unique identifier of a thread that connects activities. An ActivityThreadLinks table FIB. B is used to link an activity to a thread. Table VII defines the fields of the ThreadTypes table . Table VIII defines the fields of the ActivityThreads table . Table IX defines the fields of the ActivityThreadLinks table .

When a selected activity describes the creation of a deliverable e.g. a report study plan strategy etc. a template for that deliverable is offered to the user as an example of format and content. A Templates table is used to house data attribution for the deliverable templates. An ActivityTemplates table links activities to deliverable templates. Table X defines the fields of the Templates table . Table XI defines the fields of the ActivityTemplates table .

The TPMM allows for the inclusion of external criteria which may be imposed by outside agencies at specified TRL levels e.g. for domain specific development as in Nuclear Regulatory Commission criteria . An ExtCriteria table provides names and unique identifiers for the external criteria. Table XII defines the fields of the ExtCriteria table . An ExtCriteriaItems table provides descriptor data to define the external criteria. Table XIII defines the fields of the ExtCriteriaItems table .

An ExtMapping table is used to link the external criteria to the Activities table . Table XIV defines the fields of the ExtMapping table .

The TPMM is subdivided along TRL boundaries into phases of technology development. A Phases table is used to identify the distinct phase in which an activity occurs. The phases correspond with one of the first six TRL levels Discovery TRL Formulation TRL Proof of Concept TRL Refinement TRL Development TRL and Demonstration Transition TRL . Table XV defines the fields of the Phases table .

When a selected activity describes the creation of a deliverable which is generated on an output device such as a computer display or a printer a Deliverables table houses pointers to the deliverable names. An example of a deliverable is a Feasibility Study produced during the Discovery Phase to document the results of a literature search that is performed to determine whether the technology has already been developed. Table XVI defines the fields of the Deliverables table .

Several deliverables called out in the TPMM are produced in one phase and updated in subsequent phases e.g. the Technology Development Strategy TDS and the Technology Transition Agreement TTA as shown in . The updated deliverables are referred to as versions. A Versions table is used to provide a unique identifier for a version of a deliverable. The version provides a mechanism for working with deliverables that have a lifecycle that spans multiple phases. Table XVII defines the fields of the Versions table .

A section represents a distinct block within a deliverable. A Sections table is used to house the section number identifier referenced by the selected activity of the section within the deliverable which must be unique within a deliverable. This number is provided as part of the header for the section when a deliverable is generated. For example considering the Feasibility Study paper that is produced during the Discovery Phase to document the results of the literature search Section 5 of the paper has the section title Literature Search the Activity to be performed is Perform Literature Search and the section description is A literature search is conducted to ensure the technology doesn t already exist or isn t being developed to determine alternatives to gather supporting data etc. Table XVIII defines the fields of the Sections table .

A SectionVersions table is used to provide a linkage to track a deliverable for an activity to specific document versions. Table XIX defines the fields of the SectionVersions table .

A Properties table is used to house information concerning property to which one or more sections may be associated. In other words the Properties table stores information that is repeated such as Project Name in multiple sections throughout the documentation of a technology project. Properties are recurrent data items that the user is required to enter once and that are automatically supplied wherever the data are referenced. Table XX defines the fields of the Properties table .

A Predecessors table is used to populate dependency data between activities during bulk loading and initialization operations. Table XXI defines the fields of the Predecessors table .

A Milestones table is used to provide a way to correlate an activity with the milestone or event during which the deliverable is due to be reviewed or evaluated. A milestone typically represents the particular stage gate in a phase at which a particular section in a deliverable document must be completed. Table XXII defines the fields of the Milestones table .

A MilestoneTypes table is used to identify a milestone type at which a particular Deliverable or version of a deliverable will be required to be made available. The milestone type typically represents a set of particular milestones of a similar nature that occur across multiple phases. Examples include System Design Review Test Readiness Review TRR Technology Readiness Assessment TRA etc. Table XXIII defines the fields of the MilestoneTypes table .

A VerMethods table is used to house a unique identifier of a verification method. One or more verification methods may be used to show that an activity is completed successfully. Table XXIV defines the fields of the VerMethods table .

A Verifications table is used to link a verification method to an activity. Table XXV defines the fields of the Verifications table .

The model provides exit criteria as a mechanism to evaluate whether the deliverable of the activity in question meets the requirements of the technology phase in which it is planned to be executed. The exit criteria are assessed during the Technology Readiness Assessment TRA see . An example of the exit criteria for Section 5 of the Feasibility Study that is produced during the Discovery Phase to document the results of the literature search is literature search relevant to the identified need demonstrates that this concept has potential and is not a duplication of other efforts. An ExitCriteria table provides a pointer and descriptor data to define the exit criteria. Table XXVI defines the fields of the ExitCriteria table .

The ActivityID field is included in the Activities table the GroupMapping table the ActivityTemplates table the ExtMapping table the SectionVersions table and the Verifications table . The ActivityID field is a unique identifier for each activity.

The CategoryID field is included in the Categories table and the SubCategories table . The CategoryID field is a unique identifier for the category to which an activity belongs.

The SubCategoryID field is included in the SubCategories table and the Activities table . The SubCategoryID field is the ID of the subcategory to which an activity belongs.

The GroupID field is included in the Groups table and the GroupMapping table . The GroupID field is the ID of the group to which a corresponding activity belongs.

The RoleID field is included in the Roles table and the Activities table . The RoleID field is the unique identifier for a role to which one or more activities may be assigned.

The ActivityThreadID field is included in the ActivityThreads table and the ActivityThreadLinks table . The ActivityThreadID field is the unique identifier of a thread that connects activities.

The ThreadTypeID field is included in the ThreadTypes table and the ActivityThreads table . The ThreadTypeID field is the unique identifier of a thread type.

The TemplateID field is included in the Templates table and the ActivityTemplates table . The TemplateID field is the ID of the template that is associated with a corresponding activity.

The ExtCriteriaID field is included in the ExtCriteria table and the ExtCriteriaItems table . The ExtCriteriaID field is the unique identifier of an external criteria set.

The ExtCriteriaItemID field is included in the ExtCriteriaItems table and the ExtMapping table . The ExtCriteriaItemID field is the unique identifier of an external criterion that can be mapped to one or more activities.

The PhaseID field is included in the Phases table the Versions table the Milestones table and the ExitCriteria table . The PhaseID field is the unique identifier for a phase.

The DeliverableID field is included in the Deliverables table the Versions table and the Sections table . The DeliverableID field is the unique identifier for a deliverable.

The VersionID field is included in the Versions table the SectionVersions table and the Predecessors table . The VersionID field is the unique identifier for a version of a deliverable.

The SectionID field is included in the Sections table the SectionVersions table the Predecessors table and the ExitCriteria table . The SectionID field is the unique identifier of a section which represents a distinct block within a deliverable.

The MilestoneID field is included in the Milestones table and the Versions table . The MilestoneID field is the unique identifier for a milestone.

The MilestoneTypeID field is included in the MilestoneTypes table and the Milestones table . The MilestoneTypeID field is the unique identifier for the type of milestone.

The VerMethodID field is included in the VerMethods table and the Verifications table . The VerMethodID field is the unique identifier of a verification method.

The PropertyCode field is included in the Properties table and the Sections table . The PropertyCode field is the unique code for a property.

Also the Activities table is related to the Phases table through the DefaultPhaseID field FK in the Activities table and the PhaseID field PK in the Phases table .

The Activities table and the ActivityThreadLinks table are related through the InitialActivityID field FK and the TerminalActivityID field FK in the ActivityThreadLinks table and the ActivityID field PK in the Activities table .

The ExitCriteria table and the VerMethods table are related through the VerEventID field FK in the ExitCriteria table and the VerMethodID field PK in the VerMethods table .

The SectionVersions table and the Predecessors table are related through the SectionID field FK and the PredSectionID field FK in the Predecessors table and the SectionID field PK in the SectionVersions table and through the VersionID field FK and the PredVersionId field FK in the Predecessors table and the VersionID field PK in the SectionVersions table .

In addition the Activities table has internal linkage between the ParentActivityID FK and the ActivityID PK which allows for hierarchy.

The SectionVersions table has two internal linkages. The first is between the compound foreign key RefSectionId FK and RefVersionID FK to the compound primary key SectionID PK and VersionID PK . The second internal linkage is between the compound foreign key DepSectionID FK and DepVersionID FK to the compound primary key SectionID PK and VersionID PK .

Those of ordinary skill in the art should recognize that methods involved in managing technology program development using a relational database may be embodied in a computer program product that includes a computer usable medium. For example such a computer usable medium can include a readable memory device such as a solid state memory device a hard drive device a CD ROM a DVD ROM or a computer diskette having stored computer readable program code segments. The computer readable medium can also include a communications or transmission medium such as a bus or a communications link either optical wired or wireless carrying program code segments as digital or analog data signals.

The TPMM database is preferably implemented using Microsoft SQL Server . In addition in a preferred embodiment the application environment is Microsoft Windows Desktop the code base is Microsoft .NET Framework and the development environment is Microsoft Visual Studio 2005.

The TPMM provides an objective systems engineering approach to assessing maturing managing and transitioning technologies that is reliable and repeatable. The basic structure of the TPMM allows it to be adapted as a tool in any stage gate process used to develop a product or system. Within the science and technology community the TPMM provides several benefits such as 1 defining phases of technology development in terms of TRLs 2 establishing consistent exit criteria and deliverable documents for each phase 3 applying system engineering principles and practices 4 focusing on successful technology transition activities and 5 providing the criteria supporting early and ongoing Technology Transition Agreements which includes all stakeholders early in the development process. In addition the TPMM provides a common language set for TRL interpretation and management decision metrics and confidence in the estimation of the maturity through Technology Readiness Assessment TRA results .

The TPMM with its activity centric architecture provides a TRL based threaded activity tool set for planning assessing and quantifying technology readiness levels in an understanding of technology development maturity and system readiness. With the inclusion of the multi dimensional features of Systems Engineering Programmatics and Transition Management the TPMM insures that technologies meet the needs of acquisition programs and transition for insertion on time.

The present invention has been described with respect to the DoD acquisition process. However the invention can be applied to any product system development process particularly to those technology development efforts occurring in stages phases e.g. automobiles aircraft computers etc. by tailoring the core activity set in the database and including only those activities that are deemed necessary to accomplish the stated goals e.g. if the program has no software the software specific tasks would be eliminated from the criteria set and by populating the ExitCriteria table and the Deliverables table .

Thus it will be appreciated by those skilled in the art that modifications and variations of the present invention are possible without departing from the principles and spirit of the invention the scope of which is defined in the appended claims and their equivalents.

