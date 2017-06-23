---

title: Method and system for knowledge diagnosis and tutoring
abstract: The present invention gains better understanding of learner's knowledge status and hence provides more accurate assistance as learner progresses in the curriculum. The present invention can be an add-engine to existing learning management systems working with existing assessment and learning content in any format.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08366449&OS=08366449&RS=08366449
owner: 
number: 08366449
owner_city: Carmel
owner_country: US
publication_date: 20080813
---
The invention relates to the field of knowledge diagnosis and tutoring in e learning for education and knowledge training. More specifically this invention relates to method and system of knowledge diagnosis and tutoring that provide instructors and learners with intelligent teaching and learning assistance in online learning management systems.

In recent decades online learning technology has made significant progress in secondary and higher education corporate trainings and professional development. Typical online learning applications in use today are course management systems homework management systems assessment management systems tutoring applications and hybrids of the former systems.

Course management systems typically focus on providing tools for instructors to deliver course information and course material online and for learners to access course information and online learning content. Homework management systems normally have similar course management functions as a course management system but provide more features in assignment management for online quizzing and practice. Most of homework management systems use one or more internal or external quiz engines to deliver and grade various online assignments.

Typical assessment management systems focus more on assessing learner s learning status. Such systems use a variety of assessment methodologies ranging from summative assessment formative assessments to adaptive assessment. These assessment methodologies largely determined specifically their content format assignment creation assessment delivery and results grading. In recent years a clear trend is to link assessment more closely with learning and has gained significant success in practice with many formative assessment systems.

To date online learning tutoring systems have a much smaller user base in e learning comparing with course management systems homework management systems and assessment management systems. Most tutoring systems fit into the so called intelligent tutoring systems ITS that attempt to provide one to one tutoring experiences to help learners in their study.

Most of today s ITS systems tries to provide detailed step by step practice based instructions to help learner in problem solving or skill building. Some ITS systems try to establish learning environments close to certain specific teaching and learning models in order to better utilize learner s learning behavior to tailor strategies and methods to provide more explanations examples demonstration and practice exercises. Some other ITS systems focus on specific knowledge domain and build intelligence and business logics deeply into their assessment and learning content similar to what many adaptive assessment systems have done. At the same time without a suitable ITS to make up the gap between practice assessment and learning assistance some of the learning management systems add on tutoring features by adding logic rules in quiz content and grading mechanisms to provide certain context specific guidance and help.

Main challenges that today s ITS systems face are also rooted in limitations and risks associated within themselves 

The present invention shares with previous ITS systems in concepts of interactive and personalized learning online learning and in time and context specific feedback. The present invention uses new knowledge model and algorithms for knowledge diagnosis and tutoring. The present invention overcomes many limitations of previous ITS systems. The present invention can be implemented for a wide spectrum of knowledge domain supports different teaching and learning styles allow easy curriculum customization does no need of recreate system specific assessment and learning content can work with other learning management systems and can be used by instructors and learners in their daily activities.

Primary goal of the present invention is to provide method and system that offers effective and cost efficient learning assistance for learners across wide range of knowledge domains teaching and learning styles assessment content and learning resources.

The present invention comprises a method and a system for knowledge diagnosis and tutoring in any knowledge domain. The present invention differs from prior arts with new mathematical knowledge model for knowledge presentation and heuristic algorithms. The knowledge model allows the present invention to be applied to curricula in different knowledge domain quickly and cost effectively. The knowledge model also allows creations of new computational algorithms that provide effective and intelligent knowledge diagnosis and tutoring with minimum requirement on assessment and learning content. As a result the present invention supports curricula in different disciplines and subjects and allows easy curriculum customization for different teaching and learning styles. A preferred embodiment of the present invention can be an add engine to existing learning management systems working with existing assessment and learning content in any format and hence maximizes ROI of existing investment and technology for end users application service providers and content providers.

More specifically the knowledge model invented in the present invention comprises representation frameworks for curriculum and assessment. The curriculum framework manages knowledge to be learned knowledge prerequisite relationship pedagogic categorizations and learning priorities. The assessment framework manages assessment items of the curriculum. It contains information on objectives and prerequisite knowledge of each assessment items and related statistical learning distributions.

Combinatorial and statistical algorithms are used in the present invention for knowledge diagnosis and tutoring. But the general methodology allows other types of algorithms that utilize the same knowledge model to be used in the present invention. The computational algorithms take account a wide variety of research results in algorithms learning patterns data processing and cognitive learning. They utilize not only learner s current performance in a single assessment but also learner s learning history and curriculum knowledge ontology. The algorithms of the present invention allow the system to better understand learner s knowledge master status as learner progress in the curriculum and provide intelligent personalized learning assistance.

The present invention comprises method and system for knowledge diagnosis and tutoring for curriculum in any knowledge domain. Given a curriculum the present method starts from defining a knowledge model for the curriculum then enabling the curriculum by applying the knowledge model on the curriculum. The present method comprises step by step computation method to analysis learner s every assessment submission and evaluates learner s knowledge status. The present method provides intelligent tutoring with study guides based on learner s knowledge status in different phases of learning. The present system can be implemented as add on engine for any online learning management system. is an overview of a preferred embodiment of the present invention with a learning management system.

The present invention differs from prior arts with new knowledge model for knowledge presentation and heuristic algorithm design. The knowledge model allows the present invention to be applied to curricula in different knowledge domain quickly and cost effectively.

The knowledge model includes a curriculum framework for representing a curriculum in a knowledge domain and an assessment framework for representing assessment of the curriculum.

A curriculum can be any learning program for a given course of study in any subject area of a knowledge domain comprising ranges of knowledge to be learned learning goals to be measured instructional and learning materials to be used. In a preferred embodiment a curriculum can be a textbook a manuscript an outline of topics an online course delivered by a learning management system or training sessions ran by a training or tutoring system.

Curriculum objectives often are measurable learning outcomes or learner behaviors and are often called learning objectives or learning goals. Different curricula specify learning objectives in different granularity. When a learning application is designed around the concept of learning objective it faces significant challenge of applying itself consistently across different curricula in different subject area of different knowledge domains.

The present invention uses a content taxonomy to represent hierarchy structure of a curriculum a pedagogic taxonomy to categorize pedagogic attributes of curriculum teaching and learning materials and a resource taxonomy to describe location and asset types of learning resources.

Prior assessment management systems and tutoring systems often have knowledge assessment logic and system user interactions deeply embedded within assessment content and learning content such as various existing formative assessment systems adaptive assessment systems and cognitive tutoring systems which greatly limits where they can be applied restricts curriculum customization and imposes significant enabling cost in new content creation and new system adoption.

In comparison to prior systems the present invention is flexible to work with different curricula allows easy curriculum customization for individual instructors work with existing assessment and learning content and hence significantly reduces the cost in time and money to provide knowledge diagnosis and tutoring features to existing learning management systems.

The curriculum framework in the present invention comprises two required taxonomies content taxonomy and pedagogic taxonomy. The content taxonomy of a curriculum comprises a set of controlled hierarchic categories. There is no limitation on the number of different categories in the content taxonomy in the present invention. Each category has one or more terms associated with it. For example a Chapter category may have terms Chapter Preface Introduction and Appendix a Knowledge Point category may have only one term Knowledge Point and a Learning object category may have terms Example Video Calculator . Terms of different categories may or may not have the same name. is an example of content taxonomy hierarchy for a curriculum based on a textbook. illustrates categories and associated terms of a content taxonomy.

Content taxonomy may vary for different curricula and knowledge domains. For a given curriculum subject matter experts need to review the specific curriculum and define an appropriate content taxonomy for the curriculum.

The present invention applies the content taxonomy to a curriculum to represent the hierarchy structure of the curriculum. It does not attempt to categorize all structure or content in a curriculum. The main objective is to identify learning objectives and knowledge points in the curriculum and prerequisite relationships among knowledge points.

The present invention requires that the content taxonomy of a curriculum must have a category Learning Objective or its equivalent. The scope of a learning objective in a curriculum is usually the measurable learner behaviors or skills or fact that the curriculum contains for learning and applying.

The present invention requires that the content taxonomy of a curriculum must have a category Knowledge Point or its equivalent. The scope of a knowledge point in a curriculum is usually the least unit of measurable learner behaviors or skills or fact that the curriculum contains for learning and applying. Knowledge points in the present invention are often in a narrower scope than learning objectives commonly referenced in other applications and situations.

For example in a college algebra curriculum a learning objective of the curriculum can be Forms of linear equation of one variable and knowledge points under this learning objective may be General form Standard form Slop intercept forms Two point form Parametric form and Normal form . It may also be the case that in a similar curriculum Slop intercept forms actually is broke into two knowledge points of X axis formula and Y axis formula .

It is also possible that the learning objective in a curriculum is defined in a more narrow scope than others do and hence a learning objective contains only one knowledge point. In such case a learning objective is equivalent to a knowledge point. For example in an algebra curriculum for business majors Calculate compounded interest rate can be a learning objective and also a knowledge point. demonstrate knowledge points of a learning objective in an algebra curriculum.

The present invention uses a pedagogic taxonomy for categorizing pedagogic attributes of knowledge points in a curriculum and assessment items of the curriculum. The pedagogic categorization is used to guide and analyze learner s learning and inform instructor s teaching.

Similar to the content taxonomy a pedagogic taxonomy used in the present invention comprises a set of hierarchic categories and each category has one or more terms associated with it. Bloom s taxonomy for cognitive learning is a typical pedagogic taxonomy that can be used for a curriculum in the present invention. demonstrate part of a pedagogic taxonomy used for a college algebra curriculum based on Bloom s taxonomy.

Each knowledge point in the curriculum is associated with one or a plurality of pedagogic categories from the pedagogic taxonomy. Categories for a knowledge point should be chosen according to the design and objective of the knowledge point in the curriculum. Furthermore if a pedagogic category is associated with a knowledge point then it will be further assigned with one or a plurality of terms from that category. is an example of pedagogic categories and associated terms of a knowledge point in a curriculum of algebra for the present invention.

Pedagogic taxonomy may vary for different curricula and knowledge domains. For a given curriculum subject matter experts need to review the specific curriculum and define an appropriate pedagogic taxonomy for the curriculum.

The present invention uses learning resources to specify learning and teaching materials of a curriculum. Learning resources can be as precise as what are normally described as learning object the least learning blocks in a curriculum such as a specific format of a definition an example a description of a method a table and its descriptions a video of a class segment. Learning resources can also be as broad as a reading material that covers a wide range of knowledge points of the curriculum or even extend beyond the scope of the curriculum as long as it is supplied by the curriculum. A knowledge point in a curriculum may have one or more learning objects.

The present invention partitions learning content of a curriculum into learning resources. The scope of a learning resource can very as long as it is suitable for learning and mastery of knowledge points specified in the content taxonomy. For example when a curriculum is based on a textbook or a well draft manuscript then most learning resources are learning objects corresponding to the least learning blocks in the textbook. The rest of the learning resources can be reference materials in different format. is an example of different learning resources of a knowledge point in a curriculum.

The present invention does not require all learning resources exist in the same learning management system or in the same format. A learning resource can be a segment of content in a textbook a case study in a book or handout or material online. The present invention makes it possible to reuse any existing learning material available online offline or in different applications.

Resource taxonomy is used to define categories and properties for resource locations and types of learning resources. Various asset and learning related taxonomies existed in the public knowledge domain can be used as template of resource taxonomy.

Resource taxonomy may vary for different curricula and knowledge domain. For a given curriculum subject matter experts need to review the specific curriculum and define appropriate resource taxonomy for the curriculum.

The content framework allows inclusion of other optional metadata taxonomies. For example learning preference taxonomy can be used to classify difficulty levels and priorities for knowledge points and learning resources of a curriculum and semantic metadata taxonomy can be used for purpose such as semantic search in a specific embodiment. Metadata defined by these optional taxonomies can be used to provide instructors and learners more teaching and learning assistance features in a specific curriculum. These taxonomies are not required by the present invention for knowledge diagnosis and tutoring. demonstrate that the learning resources in have other sets of metadata associated with them.

For a given curriculum subject matter experts need to review according to the specific curriculum and desired learning assistance features to define appropriate metadata taxonomy for the curriculum.

The assessment framework of the present invention comprises prerequisite relationships among knowledge points prerequisite relationships between assessment items and knowledge points representation model of such relationships and statistical distributions related to these relationships.

The prerequisite relation among knowledge points is similar to partially ordered relation on a set. Different from traditional knowledge space theory or partially ordered sets the present invention distinguishes the direct prerequisite relationship from the implicit prerequisite relationship among knowledge points. In its visual presentation or data structure the present invention only uses the direct prerequisite relationship for efficiency and clearness. The present invention uses both direct and implicit prerequisite relationships in computation.

In a curriculum a knowledge point A is a prerequisite of another knowledge point B if learners mastery of A requires mastery of B. Knowledge point A is a direct prerequisite of knowledge point B if the knowledge or content of knowledge A is directly utilized in mastery of knowledge point B. For example solving a linear equation of one variable may require learner to mastery direct prerequisite knowledge points such as the method of solving such equations method of adding a real number to an equation method of dividing an equation with real numbers and concept of identifying none solvable equations. On the other hand even though the definition of real number is a prerequisite for methods of adding and dividing equations with real numbers it is not a direct prerequisite of solving linear equation.

In the present invention a knowledge point may have one or a plurality of knowledge points as its direct prerequisite. The prerequisite relationship may be reflexive i.e. a knowledge point may be a prerequisite of itself for some of the knowledge points but not necessarily true for all knowledge points. The prerequisite relation is a transitive relation i.e. if the knowledge point A is a prerequisite of knowledge point B and the knowledge point B is a prerequisite of knowledge point C then the knowledge point A is a prerequisite of knowledge point C. But the direct prerequisite relation is often not transitive. The prerequisite relation and direct prerequisite relation both are asymmetric i.e. if knowledge point B is a prerequisite of knowledge point A then knowledge point A cannot be a prerequisite of B.

As illustrated in each of the learning objectives L L L and L is partitioned into a set of knowledge points. Direct prerequisite relationships among knowledge points are represented by directed arcs. If a knowledge point A is a direct prerequisite of knowledge point B then a directed arc is drawn from A to B.

Let K be the set of all knowledge points of a curriculum. The prerequisite diagraph D K of the curriculum has all knowledge points of K as its vertices. A directed arc among two vertices represents a direct prerequisite relationship among two knowledge points. A prerequisite digraph may have loops at most vertices due to the fact that a knowledge point is often a direct prerequisite of itself. Prerequisite digraph defined in the present invention only represents direct prerequisite relations.

If knowledge points A and B are from a curriculum such that B is a direct prerequisite of A then there is a directed arc from B to A in the prerequisite digraph. In the prerequisite digraph knowledge point B will be called an immediate predecessor of A and A will be called an immediate successor of B. If there is a directed path from B to A following directed arcs then B will be called a predecessor of A and A is a successor of B. The distance between two knowledge points is the length of shortest path between them. If there is no direct path among two knowledge points then their distance will be denoted as A.

In a prerequisite digraph the in neighborhood of a knowledge point K denoted by InN K contains all immediate learned predecessors of K. For a given integer n the out neighborhood of K denoted by OutN K contains all immediate successors of K the distanced in neighborhood InN K contains all predecessors of K that have distance exactly n from K. Similarly the distanced out neighborhood OutN K of K contains all successor of K having distance at exactly n from K. The distance 1 in neighborhood and distanc 1 out neighborhood are exactly InN K and OutN K . Both InN K and OutN K can be found using well known breadth first search algorithm on acyclic digraphs.

The knowledge prerequisite distribution in the present invention is a statistical distribution used to describe how likely a learner s failing to mastery a knowledge point is due to learner s inadequacy on a corresponding direct prerequisite knowledge point. The knowledge prerequisite distribution varies according to specific knowledge point in different knowledge domain learning environment teaching and learning style and outcome expectation of related curriculum. It can be a well defined statistical distribution or an empirical distribution.

The present invention bridges assessment and curriculum learning outcomes by prerequisite relations between assessment items and knowledge points. The present invention not only measures learner s learning on curriculum desired learning outcomes but also identifies root cause knowledge point of learner s knowledge deficiency during the learning process.

For a given curriculum the present system can work with assessment items in a textbook a manuscript an assessment bank installed on a desktop computer or an online quiz engine in a learning management system. Assessment items can also be questions in homework a quiz an assessment or manuscripts distributed through training session in class on a device online or any other channel of media or format accessible by learner.

Assessment items included in a curriculum are used either for enhancing learner s mastery of certain knowledge points or assessing learner s mastery level of certain knowledge points. These knowledge points are called objective knowledge points or objectives in short of an assessment item. An item may have one or a plurality of objectives in the curriculum. In some curriculum it is also possible that an identical item may appear in different assessment to server different objectives.

Knowledge points that are explicitly required to solve an assessment item correctly are called prerequisites of the item. For example when an item of solving a one variable linear equation is given the learner must not only need to know correct method and steps for how to solve such equation but also need to be able to apply some previously learned knowledge such as simplifying an algebraic expression simplify a linear equation evaluate additions subtractions divisions and multiplications related to an equation properly.

In knowledge points K Kand Kare prerequisites of an assessment item and Kand Kare objectives of the same item. It is possible that a knowledge point is both an objective and a prerequisite of the same assessment item.

For each assessment item used in a curriculum an objective scalar is assigned to each of its objective. The item objective scalar describes relative importance or preference of an objective to the item. For an assessment item the objective scalars are assigned to its objectives separately.

Objective scalars can be real numbers of values between 0 and 1 but not necessarily probabilities i.e. there is no necessary relationship between objective scalars on different objectives of the same assessment item. Objective scares can be specified by subject matter experts. For simplicity object scalars can be set to 1 if it is cost prohibitive to obtain more precise measure of objective scalars.

Similarly for each assessment item a prerequisite distribution is assigned to its prerequisites. While objective scalars are not probabilities the prerequisite distribution is the conditional probability that the learner has not adequately mastered the corresponding prerequisite if a learner failed on the item. The prerequisite distribution is required for every assessment item that will be assessed.

Quantities used to describing preference of objectives and error causes of prerequisites are not limited to formulas given in the examples. When other measurement is available to describe preference among objectives and error cause among prerequisites appropriate formulas based on different measurements may be used to replace above mentioned quantities.

Giving a curriculum subject matter experts define curriculum framework and assessment framework for the curriculum. And then apply defined frameworks to the curriculum. Main steps to enable a curriculum includes 

The curriculum framework and assessment framework allows removing knowledge points assessment items and related learning resources from a curriculum easily. The only thing instructor needs to be aware of is that removing a set of knowledge points may leave learner without enough prerequisite knowledge for some up coming knowledge points. By providing necessary warnings and options the present system supports customizing a curriculum easily for individual instructors. Instructors may select knowledge points assessment items and learning resources to be used for different course settings. After customization performance analysis reporting and learning assistance can be executed based on remaining knowledge points and assessment items in the customized curriculum.

The present invention analyzes learner s knowledge status every time learner submits results of an assessment or a practice. The only required information on learner s answer for an assessment item is if the learner answered the corresponding item correctly or wrong. Up on receiving assessment result based on specific scenario and type of assessment the present invention calculates learner s current assessment knowledge performance and overall knowledge status. All necessary values needed for future calculation or reporting are tracked by the present invention in learner s knowledge history.

Knowledge diagnosis in the present invention is based on results from instructor assigned or learner created assessment submissions. The present invention evaluates learner s knowledge mastery status using not only latest assessment results but also learner s knowledge history to accurately identify root causes of learner s current knowledge deficiency. Therefore learner s historical knowledge values are not only saved for record keeping purpose they are also used each time learner s knowledge status is updated.

Different from existing summative or formative assessment systems that evaluate learner s overall performance on learning outcomes only the present invention evaluates learner performance for both learning outcomes and learning deficiency. Hence the present invention provides not only formative assessment type of analysis and reports but also the knowledge deficiency root analysis for tutoring purpose.

Every time a learner submits assessment results the present invention identify objectives and prerequisites of the assessment. Since all assessment items have been defined with objectives and prerequisites in the given curriculum the objectives of the assessment are defined as the union of objectives of all assessment items in the assessment and the prerequisites of the assessment are defined as union of all prerequisites of all assessment items. Most of the time objectives and prerequisites of an assessment may have nonempty intersection.

Each time an assessment results is submitted the present invention calculate relevant knowledge values for each objective and prerequisite of the submission. For convenience and clarity in the rest of the descriptions of knowledge diagnosis of the present invention assume that it is the n th time that a knowledge point K is to related to an assessment submission i.e. K is an objective or prerequisite of an item in current submission.

Also suppose that q . . . qare all items in current submission. For each item q i 1 . . . M assign a status variable xso that x 1 if learner has answered qcorrectly and x 0 if learner answered qincorrectly. If a knowledge point K is an objective of some items of the submitted assessment denote S K q as the objective scalar of K of item q. If K is a prerequisite of item qthen denote P K q as the prerequisite probability of K for item q.

Similar to formative assessment the present inventions uses objectives of assessment items to evaluate learner s outcome based performance. It measures learner s success rate among all items that have a specific knowledge point as an objective. A typical formula for evaluate learner s current performance on an objective can be as follows 

Let I K q 1 if K is an objective of item qor let I K q 0 if K is not an objective of q. The objective value

Learner s performance towards learning goals can also be measured using objective scalars assigned to assessment items when different preference levels are set for objectives of an item. A weighted version of objective score for knowledge point K as an objective can be calculated as follows. Let I K q 1 if K is an objective of item qor let I K q 0 if K is not an objective of q. The weighted objective value WOV K can be calculated by formula

Formula for weighted objective value of a knowledge point is not limited to the formula given above using objective scalars. When other measurement is available to describe preference among objectives appropriate formulas based on different measurements may be used for the weighted objective values.

Prerequisite distributions on assessment items can be used to evaluate learner s readiness on prerequisites of an assessment. Let J K q 1 if K is a prerequisite of item qand J K q 0 if K is not a prerequisite of item q. The prerequisite value PV K of K is

Formula for prerequisite value of a knowledge point is not limited to the formula given above. When other measurement is available to describe readiness of prerequisites of an item appropriate formulas based on different measurements may be used for the prerequisite values.

The present invention also uses prerequisite distribution to calculated potential error causes for a specific assessment. An exemplary measurement can be obtained as follows Let J K q be defined as before. The assessment error score ES K of K for this submission can be calculated by

This value describes how likely the knowledge point P is a cause of error for the learner in current submission. The larger of the value ES K the more likely the knowledge point K needs learner s attention. Formula for error score of a knowledge point is not limited to the formula given above. When other measurement is available to describe readiness of prerequisites of an item appropriate formulas based on different measurements may be used for the error score.

The present invention provides learner learning assistance based on learner s knowledge status and possible error causes from each assessment. For each assessment submission the present invention generates a suspicious list of prerequisites as possible candidates for learner s learning remediation or enhancement for the specific assessment. In an embodiment such list can be any knowledge point that is a prerequisite of the assessment and has prerequisite score meet for example inequality WOV K ES K 

Formula for deficiency value of a prerequisite is not limited to the formula given above. When other measurement is available to describe readiness of prerequisites of an item appropriate formulas based on different measurements may be used for the deficiency values.

Suppose knowledge point K is an objective or a prerequisite of an assessment item in the assessment. If there are no previous assessment values for a knowledge point K then this is the first time that the present learner has submitted an assessment that has this knowledge point as an objective or prerequisite. The present invention will use assessment values as initial value of its knowledge values in such case. For example the present invention can set the adjusted objective value AOV K OV K and adjusted prerequisite value APV K PV K .

If knowledge point K has been involved in previous assessment submissions suppose AOV K AOV K . . . AOV K are previous adjusted objective values and APV K APV K . . . APV K are previous adjusted prerequisite values. Then the present invention updates current knowledge value taking in count of filtering out learner s accidental mistakes and learner s knowledge learning patterns. The adjusted objective value AOV K and adjusted prerequisite value APV K of K can be for example given by

If knowledge point K is only a prerequisite of the submitted assessment then one can set AOV K AOV K and APV K can be calculated as in 2 above.

The purpose of above calculation is to canceling errors in objective values and prerequisite values due to accident learner responses such learner s guessed answers in assessment submission. Coefficients used above are based on noise filtering techniques cognitive learning models and statistical analysis.

These coefficients used in above formula are not limited by expressions given above. They can be adjusted by subject matter expert for a specific knowledge domain or for a specific learning model if desired. When other techniques are suitable to filter out data noise and accidental responses from learner appropriate formulas based on performance history may be used for adjusted objective and prerequisite values.

The assessment exponential knowledge score captures learner s overall knowledge level based on assessment submission only. If both AOV K and APV K are available this value can be expressed as for example 

Exponential knowledge score is not limited to the formula given above. When other measurement is available or for curriculum from a specific knowledge domain appropriate formulas or methods based on different measurements may be used for exponential knowledge score.

Adjusted objective value adjusted prerequisite value and exponential knowledge score are based on item prerequisite mapping and historical assessment results on individual knowledge points. The present invention also takes in count of prerequisite relations among knowledge points in the underlying curriculum. This allows the present invention to intelligently evaluate learner s knowledge status not only based on one time submission or an isolated assessment item or individual knowledge point but also based on learner s knowledge history.

Let K be a knowledge point related current submitted assessment. The distance i In Neighborhood of K is InN K K K . . . K. The distanced Out Neighborhood of K is OutN K K K . . . K. Let KS K be knowledge status of Kbefore current submission. The current distance i in average of K can be defined by

The largest number i such that distance i in average is larger than 0 is called the in radius of K. If no such number exists then none of the prerequisites of K has score larger than 0 and the in radius of K is 0. Similarly the largest number j such that distanced out average is larger than 0 is the out radius of K.

Suppose that the in radius of K is n and the out radius of K is m. If n 0 the learning score LS K of K that captures how well the learner has mastered prerequisites of K can be defined as

Learning scores and application scores are not limited to the formulas given above. For curriculum from a specific knowledge domain appropriate formulas or methods may be used for these scores.

Suppose that KS K is the knowledge status of K before current submission and the in radius of K is s the out radius of K is t. Then the knowledge status of K can be a scalar based on assessment oriented exponential knowledge status and knowledge prerequisite relationships. For example the following can be used to calculate knowledge status of K 

Knowledge status is not limited to the formula given above. For curriculum from a specific knowledge domain appropriate formula or method may be used for knowledge status.

Using pedagogic categories associated with each knowledge point in a curriculum knowledge status for a specific pedagogic category can be calculated. Such cognitive knowledge status can be calculated using the same formulas for calculating knowledge status. For a specific pedagogic category the formula for knowledge status will use only those knowledge points related to the submission and that are associated to the specific category. For example to calculate cognitive knowledge status for synthesis the knowledge status will use learning score

In present invention all information and data needed for calculate and update learner s knowledge value and knowledge status are kept. Besides supporting knowledge diagnosis for assessment submission personal knowledge profile also allows the present invention to provide instructor and leaner teaching and learning assistance based on learners personal knowledge status.

The intelligence of the present invention resides in the personal knowledge profile. Since a learner s knowledge status of a knowledge point evolves when learner progress in the curriculum. The knowledge status represent the latest mastery level of a learner not just what the learner had at the time of taking an assessment.

The personal knowledge profile will have the following knowledge values associated with each knowledge point in the curriculum for each submission 

If cognitive knowledge status is evaluated it will also be saved in the personal knowledge profile along with all values listed above.

The present invention provides assistance to instructional planning to instructors and intelligent tutoring and learning assistance to learners. The main tutoring and learning assistance from the prevent invention is delivered through various reports knowledge map and study guides based on learners knowledge status and knowledge history.

The present invention can generate summative assessment reports on a single assessment a set of assessment or set of assessment items. The following are examples of summative assessment reports that

Such reports are typical in most learning management systems and provide basic information to instructors and learners. illustrates a summative assessment report for a group of learners. illustrates a summative assessment report for a single learner.

The present invention can also provide formative assessment report based on learner s assessment submission and assessment objectives and pedagogic categories.

Formative assessment reports provide learner s performance on learning goals in the curriculum. Objective values calculated above as well as pedagogic categories associated with objectives of assessment items can be used for such reports. The present invention can generate for example not limited to formative type reports as following 

The present invention provides various knowledge reports to assist instruct tor in instructional planning and teaching assist learner in different phases of learning. Knowledge reports focus on learner s knowledge mastery status. They are based on assessment and knowledge values in learner s personal knowledge profile.

Knowledge map of the present invention provides a way to present knowledge prerequisite relationship and knowledge information learner knowledge status in graphic format. A knowledge map of knowledge points is similar to a digraph that has related knowledge points as vertex set and arcs corresponding to prerequisite relationship among the knowledge points. It is provide a visual interface for instructors and learners easily identify a learner s knowledge status and areas that need to be worked on.

The knowledge map allows instructors and learners to trace prerequisites a every knowledge point in the curriculum. Knowledge status information associated with each knowledge points will help easy identification of knowledge deficiency and remediation focus.

A study guide is a paced step by step learning guide with targeted knowledge points and relevant learning resources. A study guide can be produced based on one or multiple assessments a group of selected knowledge points a segment of the curriculum or selected assessment items. A study guide contains knowledge points a learner supposed to mastery and learning resources of these knowledge points. It also contains information on learner s current knowledge status on reach knowledge points.

The following comprises main features and functions of a possible study guide based on knowledge requirement and learner s knowledge status 

It is often that when learner has not mastered a knowledge point adequately it may not be that the learner has difficult in the said knowledge point itself. It often happens that the weakness or lack of understanding of certain prerequisites of the said knowledge pint is the deficiency root cause. Effectively identify learning deficiency root cause is the key focus of the present invention.

Study guide and knowledge map in the present invention can allow learners to trace back to such root causes. In the example of the study guide in the name of each knowledge point is enabled as a hyperlink. When a learner clicks on the name of a knowledge point the present invention provides a similar step by step study guide of all prerequisite knowledge point of the said knowledge point together with learner s latest knowledge status and related learning resources. Similar function is available on the knowledge map.

Based on curriculum framework and learner s knowledge profile the present invention provides teaching and learning assistance in different phases of instructional planning teaching learning pre assessment study and post assessment study. illustrate a typical teaching and learning workflow. The present invention can provide instructors and learners assistance at every learning phase. The following summarizes teaching and learning assistance that are available from the present invention 

Providing assistance to instructors in instructional and assessment planning based on assessment objectives prerequisites pedagogic classifications and learners knowledge mastery status comprising 

The pre assessment learning assistance is available from Two types of study guides can be created for pre assessment study by instructor 

Most learning management systems and quiz engines allow learners to take practice assessment repeatedly until learner mastered required knowledge. The present invention can help learner to identify knowledge deficiency effectively and hence improve learning efficiency.

Each time when leaner submits a practice assessment the present invention can analyze learner s knowledge status and update latest knowledge status. The study guide for the same practice will be updated with learner s latest knowledge status. Then learner can use updated study guide to identify knowledge points not meeting requirement and related learning resources.

Leaner can also further retrieve knowledge status of all prerequisites of the said knowledge point to identify root cause of the deficiency. After identify the root causes learner can focus study guide of the said knowledge point to improve learning.

The present invention provides any learning management system with add on intelligent knowledge diagnosis and tutoring features to learning management system that allows learners to input their assessment results and system to communicate with other system through application programming interface. For learning management systems that allow instructors to create and manage their own assessment the present invention can provide intelligent features to assist instructors in teaching and assessment planning and assist learners in daily study pre assessment preparation and post assessment remediation.

In a preferred embodiment of the present system system functionalities can be partitioned into functional modules that execute different tasks. illustrates a partition of functionality of a preferred embodiment of the present invention. It comprises an application programming interface layer M a Curriculum Module M a Knowledge Module M a Tutoring Module M a Report Module M and a Curriculum and Metadata Management Interface module M .

In a preferred embodiment the Curriculum Module M provides end user interface for learning management systems and programs for business logics supporting learning management system and curriculum management. The Knowledge Module M analyzes learner s assessment submissions for performance analysis and knowledge diagnosis. The Knowledge Module M analyzes and updates learner s knowledge values and knowledge status and support features in Tutoring Module M and Reporting Module M . The Tutoring Module M provides learning assistance based on curriculum requirement and learner s knowledge status. The Report Module M generates and manages learner s performance and knowledge reports. The Curriculum and Metadata management Interfaces Module M provides interface for subject matter experts to create and manage data in curriculum framework and assessment framework. The Application Programming Interface M manages data and information communications between the present invention and supported learning management systems.

The present invention is a method and system for knowledge diagnosis and tutoring which is not limited by the embodiment illustrated in . There is no restriction on what technologies should be used to construct such an embodiment to deliver functionalities specified by the present invention. There is no limitation that how the system is partitioned in a particular embodiment from an application architecture point of view. The partition of functional modules illustrated in is only a logic representation of functionalities. The functionalities are based on method specified in the present invention. The present method is not bound to a specific embodiment.

A preferred embodiment of the present invention system can work with a wide variety of learning management systems including course management systems homework management system assessment management system and any hybrid of the previously mentioned systems.

An embodiment of the present system can also work as a standalone application using user interfaces inside the present system. The present invention does not require that there must be a learning management system. When there is no learning management system or no online quiz engine to grade learner s assessment results the present invention can provide interface for learner to input any manually grade results.

A preferred embodiment of the present invention can be located as far as in different locations on the network from where the learning management system is or as close as on the same server on which the learning management server resides. The internet protocol such as the ones illustrated in and can be any type of technology that facilitates communication between the present invention the learning management system and the user.

In a preferred embodiment the present invention uses Application Programming Interface API as technology to facilitate exchanging messages or data between the present invention and other learning management systems. If a preferred embodiment of the present invention acts as a standalone application it then uses its own user interfaces and any messaging and data transmission will be executed internally within the present system.

The application programming interface of the present invention can utilize any technology that can act as virtual interface support system level integration of multiple systems and applications. Application programming interfaces and user interfaces provided by the present invention will support a wide range of communications and functions such as customization of curriculum parsing system and user information return messages data and package interfaces to learning management systems.

In a preferred embodiment subject matter experts can use the Curriculum and Metadata Management Module M to input and manage curriculum framework and assessment framework of a curriculum. Curriculum framework and assessment framework data will be saved in the Curriculum Repository M .

2 define resource taxonomy and other relevant metadata taxonomies for the given curriculum and learning content 

3 identify curriculum knowledge points and learning resources of the curriculum and assign each element a unique identifier 

7 identify objectives and prerequisites for assessment items of the given curriculum and assign each assessment item a unique identifier 

Enabling a curriculum generates a wealth set of metadata that associated with the curriculum knowledge points and curriculum assessment items stored in Curriculum Repository M . The Curriculum Repository can be any relational database or non structural data repository or any other data repository that can store and retrieve knowledge related metadata and information.

In a preferred embodiment the Curriculum Module is able to provide the learning management system available curricula in the present system through application programming interface M . Instructors can utilize learning management system interface or interfaces M in the Curriculum Module to select a curriculum for their courses.

The structure and properties of curriculum framework allows removing knowledge points assessment items and related learning resources from a curriculum. The only thing instructor needs to be aware of is that removing a set of knowledge points may leave learner without enough prerequisite knowledge in learning. Therefore by providing necessary warnings and options the present system supports customizing a curriculum easily for individual instructors. Instructors may select knowledge points assessment items and learning resources to be used for different course settings. After customization performance analysis reporting and learning assistance can be executed based on remaining knowledge points and assessment items in the customized curriculum.

In a preferred embodiment the Knowledge Module of the present invention analyzes learner assessment results calculates learner knowledge status and manages learner s knowledge level and knowledge profile.

The Knowledge Module of the present invention accepts learner s graded assessment results from integrated learning management system and analyzes learner s assignment performance on knowledge points covered by the assessment. The only required data for an assessment item in an assessment submission for the present invention is if the learner has answered a question correctly or not.

The Knowledge Module in an embodiment of the present invention can work with one or more learning management systems deployed at different location with different technology and configurations. A learning management system can submit grade assessment results to the Knowledge Module. Learners can complete their assignment in any learning management system that can transmit grade assignment results to the present invention. Also the present invention does not require learners to complete their assignments in a learning management system or even online. Learners can submit their graded results though any devices such as not limited to PDA and cellular phones that are able to transmit assignment results to the present invention using interface M .

In a learning management system supported by an embodiment of the present invention curriculum related assessments are presented to students either as online assessment backed by online quiz engines or as learning activities linked to interfaces for students to submit graded results. Depending on how such assessment will be administered by instructors and completed by learners learner s work may be graded by a quiz engine automatically by an instructor manually or by other process. In a learning management system usually graded results will be transmitted to the Knowledge Module through application programming interface M by the learning management system.

If an assessment is graded by an online quiz engine integrated with the present invention then graded results can be passed to Knowledge Module though application programming interfaces M . If an assessment is graded by instructor manually or other applications that are not integrated with the present invention then the learner can submit graded results through user interfaces M to the Knowledge Module. If an assessment is a learner s self practice and learner has identified his or her own results are correct or wrong the learner can also submit such information to the Knowledge Module.

In a preferred embodiment of the present invention when graded assessment results is transmitted to the present invention the assessment results can be plain or encrypted text string HTML form data XML packages or other data format. For better interoperability with a wide range of learning management systems quiz engines it is desired that the assessment results in submitted to Knowledge Module in XML format. illustrates graded assessment results in XML from a quiz engine.

In a full featured learning management system a learner may take assessment online and submit results for automated or manual grading. Formatted assessment results can then be transmitted to the Knowledge Module M by the learning management system.

If a preferred embodiment of the present invention is used as a standalone system learner may enter and submit graded assessment results using Knowledge Module user interfaces M . The user interface will pass such submission through Application Programming Interface M . Assessment results will be reformatted and then send to the Knowledge Module M .

In a preferred embodiment besides correctness of learner s response on each assessment item the present invention also require some other data form to support integration with learning management system user identification and other security requirement. Formatted assessment results will normally include but not limited to the following information 

2 Assessment information assessment ID assessment source ID assessment type assessment submission time attempt type attempt count etc.

3 Assessment item Information item ID item source ID item type item response correctness item status and item sequence number.

System ID and user ID are for the identification of the system and user from where the submission is originated. Curriculum ID identifies the curriculum that the assessment is associated with. Class ID identifies a specific class that the learner belongs. Customized curriculum ID identifies if and which customized curriculum is used for the class.

The assessment source ID identifies where the assessment is managed and administered to the learner. The assessment ID can be a unique identifier of the assessment in the source system. The assessment type identifies that the assessment is an instructor assigned and allowed submission or a learner s self practice. The submission time identifies when the submission is made. The attempt type indicates that if the submission should be counted for assessment knowledge values or for practice knowledge values. The attempt count identifies that how many times that the learner submitted the same assessment.

Item source ID identifies where an assessment item is originated. Item ID is from the assessment source system. Correctness indicates that learner has failed or succeeded on the item which is often given by assessment engine during grading. The other parameters are optional for the present invention. Learner s specific response to each assessment item is not required for the present invention. Such information may be used in knowledge analysis but is not always required.

In a preferred embodiment every time an assessment is submitted to the present invention from an integrated learning management system the Knowledge Module M verifies if the assessment has been parsed or not. If the assessment is parsed before then Knowledge Module can retrieve assessment objectives and prerequisites directly and continue to knowledge diagnosis. If the assessment has not been parsed before then Knowledge Module M will parse the assessment results to identify assessment objectives and prerequisites.

When graded assessment results are submitted to Knowledge Module M the first time Knowledge Module retrieves objective and prerequisite knowledge points associated objective scalars and prerequisite distributions from the Curriculum Module M .

The Knowledge Module saves objectives prerequisites objective scalars and prerequisite distributions for each assessment in the Knowledge Repository. When an assessment is submitted again the Knowledge Module will retrieve assessment objectives prerequisites objective scalars and prerequisite distributions from Knowledge Repository M directly.

In a preferred embodiment of the present invention the Knowledge Module calculates learner s knowledge values based on submitted assessment results. Calculated values will be saved to learner s knowledge profile. Reports and learning assistance will then be available through Report Module M and Tutor Module M .

The Knowledge Module performs calculations based on learner s current submission and knowledge history. Different from existing summative or formative assessment systems that evaluate learner s overall performance on the assessment or on specific learning outcomes the present invention evaluates learner performance on both learning outcomes and learning deficiency. Hence the present invention can help learner to identify root causes of errors.

The following knowledge values associated with each knowledge point in the curriculum will be calculated in the Knowledge Module and then saved in the Knowledge Module Repository 

1 Objective Values OV K and Weighted Objective Value WOV K based on permitted assessment or self practice where index n corresponding to the nth such submission 

2 Prerequisite Values PV K based on permitted assessment or self practice where index n corresponding to the nth such submission 

3 Error Values EV K based on permitted assessment or self practice where index n corresponding to the nth such submission 

7 Exponential Knowledge Scores EKS K based on adjusted prerequisite values APV K adjusted objective values AOV K and deficiency values 

9 Application Scores AS K based on exponential knowledge values of knowledge states having K as prerequisites 

Most of learning management systems is able to provide basic summative reports. Some systems also provide more detail reports on item analysis and learning outcome analysis close to formative assessment reports. Some formative assessment systems provide both summative and formative assessment reports. In a preferred embodiment the present invention can provide not only summative and formative assessment reports but also knowledge reports.

In a preferred embodiment upon receiving request from integrated learning management system the Report Module M sends request to the Knowledge Module M to retrieve knowledge values of selected assessments or knowledge points for one or for a group of learners. After receiving response from Knowledge Module the Report Module format received data according to learning management system request and send formatted data back to the learning management system. The learning management system can use such formatted data to construct corresponding reports.

The Report Module User Interfaces M can also generate reports and present to user directly in a preferred embodiment.

In a preferred embodiment the Report Module M can generate summative assessment reports on a single assessment a set of assessment or set of assessment items. The following are examples of summative assessment reports that

Such reports are typical in most learning management systems and provide basic information to instructors and learners. illustrates a summative assessment report for a group of learners. illustrates a summative assessment report for a single learner.

In a preferred embodiment the Report Mudule can also provide formative assessment report based on learner s assessment submission and assessment objectives and pedagogic categories.

Formative assessment reports provide learner s performance on learning goals in the curriculum. Objective values calculated above as well as pedagogic categories associated with objectives of assessment items can be used for such reports. The present invention can generate for example not limited to formative type reports as following 

1 Weighted objective values of objectives in a specific assessment for selected learners This is the most common type of formative assessment report focusing on selected learning goals 

In a preferred embodiment the Report Module can generate various knowledge reports to assist instructor in instructional planning and teaching assist learner in different phases of learning. Knowledge reports focus on learner s knowledge mastery status. They are based on assessment and knowledge values in learner s personal knowledge profile.

In a preferred embodiment integrated with a learning management system instructor can invoke a knowledge report from the learning management system S . The learning management system sends request to Report Module M of the present invention through Application Programming Interface M . The Report Module retrieve knowledge data from the Knowledge Repository M and return data back to learning management system S . Learning management system S then present instructor with knowledge report. illustrates an example of knowledge report for a set of knowledge points. illustrate an example of personal knowledge report that covers all knowledge points in a curriculum.

Knowledge map of the present invention provides a way to present knowledge prerequisite relationship and knowledge information learner knowledge status in graphic format. A knowledge map of knowledge points is similar to a digraph that has related knowledge points as vertex set and arcs corresponding to prerequisite relationship among the knowledge points. It is provide a visual interface for instructors and learners easily identify a learner s knowledge status and areas that need to be worked on.

In a preferred embodiment integrated with a learning management system instructor can invoke a knowledge map from the learning management system S . The learning management system sends request to Report Module M of the present invention through Application Programming Interface M . The Report Module retrieve knowledge data from the Knowledge Repository M and return data back to learning management system S . Learning management system S then present instructor with knowledge report. illustrates a simple knowledge map for a set of knowledge points.

The main tutoring and learning assistant from the prevent invention is study guides generated based on learner s latest performance and knowledge status. In a preferred embodiment the present invention provides various study guides to assist instructors teaching and learner s learning.

In a preferred embodiment a study guide is a paced step by step learning guide with targeted knowledge points and relevant learning resources. A study guide can be produced based on one or multiple assessments a group of selected knowledge points a segment of the curriculum or selected assessment items enabled for the curriculum. A study guide also contains information on past and current knowledge status of a learner or a group of learners. When a study guide is presented to user various controls can be available for user to make changes print out the study guide or create study notes.

The following are main features and functions of a possible study guide based on knowledge requirement and learner s knowledge status 

1 Knowledge point Information on all prerequisite knowledge points that learner is supposed to mastery such as location in the curriculum learning priority current knowledge status relevant importance of study.

2 Learning sequence A recommended learning sequence of knowledge points to ensure that learner has mastered necessary prerequisites of a knowledge point under study 

3 Knowledge status Learner s current knowledge status for each knowledge point in the study guide. This information can be used by learner to identify priority among all knowledge points in learning. If the study guide is a summary guide over the class then knowledge status will represent a class average.

4 Learning resource Information on learning resources of every knowledge point such as type location related study notes. Such information help learner easily identify means and learning resources helpful for learning 

5 Access to knowledge map Knowledge map is a visual representations of related knowledge points prerequisite relationship among knowledge points and information listed above 

6 Access to related knowledge for deficiency root cause Provide user information on related knowledge points of each knowledge point to pinpoint root cause of knowledge deficiency 

8 Other relevant controls Study guides are likely generated online or on a computer in a preferred embodiment. The study guide may have search editing print functions associated to it.

In a preferred embodiment integrated with a learning management system instructors and learners can invoke a study guide from the learning management system S . The learning management system sends request to Tutor Module M of the present invention through Application Programming Interface M . The Tutor Module retrieve knowledge data from the Knowledge Repository M and return data back to learning management system S . Learning management system S then present instructor with knowledge report. illustrates a simple study guide for a set of knowledge points.

It is often that when learner has not mastered a knowledge point adequately it may not be that the learner has difficult in the said knowledge point itself. It often happens that the weakness or lack of understanding of certain prerequisites of the said knowledge pint is the deficiency root cause. Effectively identify learning deficiency root cause is the key focus of the present invention.

Study guide and knowledge map in the present invention can allow learners to trace back to such root causes. In the example of the study guide in the name of each knowledge point is enabled as a hyperlink. When a learner clicks on the name of a knowledge point the Tutor Module of the present invention provides a similar step by step study guide of all prerequisite knowledge point of the said knowledge point together with learner s latest knowledge status and related learning resources. Similar function is available on the knowledge map.

In a preferred embodiment the Tutor Module provides data and information for learning management system to construct a Study Guide Editor. The learning management system can create its own user interface for the study guide editor or can embed user interface delivered by the Tutor Module through the application interface. A Study Guide Editor allows instructor and learners to create and manage study guides for a class or for an individual. Instructors can manage assignment specific study guides or study guides based on selected knowledge points or questions learners can create and manage self study guide based his or her own knowledge status learning needs and learning style.

The Study Guide Editor retrieves curriculum structure assessment items and learning resource information from the Curriculum Module M . Study guide data will be saved in Study Guide Repository M in the Tutoring Module.

In a preferred embodiment based on curriculum framework and learner s knowledge profile the present invention provides teaching and learning assistance in different phases of instructional planning teaching learning pre assessment study and post assessment study.

1 Instructional and assessment planning Provide assistance to instructors in instruction and assessment planning based on assessment objectives assessment prerequisite pedagogic categories and learners knowledge mastery status 

2 Everyday learning assistance Provide everyday learning assistance to learners with step by step study guide and learning resources based on curriculum requirement 

3 Pre assessment learning assistance Provide intelligent pre assessment assistance to instructors and learners in practices based on assessment objectives assessment prerequisites pedagogic categories and learner s knowledge mastery status 

4 Post assessment learning assistance Provide post assessment remediation assistance to learners based on assessment objectives knowledge prerequisites pedagogic classifications assessment performance and current knowledge mastery status 

5 Self practice assistance Provide instant knowledge analysis knowledge report and knowledge status based study guide that intelligently help learner focus on knowledge deficiency.

In a preferred embodiment instructor can use various reports provided by the present invention to assist instructional and assessment planning based on curriculum requirement and learners knowledge status comprising 

1 Select curriculum content assessment content and pedagogic categories to identify objective and prerequisite knowledge points for teaching Instructor can invoke a knowledge report or knowledge map from the learning management system S .

2 Generate study guides based on identified knowledge points with information on step by step study plans learning priorities learners performance history knowledge mastery status relevant teaching and learning resources and pedagogic categories 

3 Generate reports on learners performance history knowledge mastery status relevant teaching and learning resources learning priorities and pedagogic categorizations of any knowledge points in the curriculum.

1 Instructor creates study guide according to teaching plan for selected topics or assessment that may or may be online with or without curriculum enabled assessment items. Such study guide can be standalone without associated with an online assessment in the learning management system or can be online within a learning management system. When such study guide is available to learner it will have learner s knowledge status and learning priorities for related knowledge points.

2 Instructor creates study guide for a specific assessment comprises identified curriculum content or assessment items. Each time after creating an assessment instructor can request a companion study guide. Learner can study such guide to prepare for corresponding assessment based on personal knowledge status and learning priorities on related knowledge points.

3 Leaner can create study guide for self study based on selected knowledge points. These knowledge points can be selected according learner s knowledge profile for remediation purpose or can be selected from the curriculum for preview or preparation of an up coming assessment.

The pre assessment learning assistance is available from Two types of study guides can be created for pre assessment study by instructor 

1 Study guide for a specific assessment comprises identified assessment items In a preferred embodiment when an instructor creates an assessment in the learning management system with assessment items enabled in the curriculum he may request for a companion study guide for learners. The learning management system then sent assessment item IDs and related information such as class ID assessment ID instructor ID and other related information to Tutor Module through application programming interface M . The Tutor Module will pass assessment information and assessment item IDs to the Knowledge Module to extract objectives and prerequisites of assessment items. Assessment objectives and prerequisites will be saved in the Knowledge Repository with the assessment information. Finally the Tutor Module will notify the learning management system that a study guide is ready for the corresponding assessment. A means such as hyperlink will be available to an eligible user to access the study guide at proper location and time controlled by the learning management system.

2 Study guide for a set of specified knowledge points for review target for learners Instructor may select a segment of the curriculum and request the system to generate a companion study guide. The system will generate a study guide according to knowledge points covered by the content and generate a study guide based on related knowledge points.

1 After knowing what topics will be covered the assessment the learner can request a study guide according to the topics. The system will generated a study guide according to knowledge points covered by those topics.

2 After knowing what topics will be covered by the assessment the learner may identify knowledge points that he has not mastered well and request a study guide for selected knowledge points. The system will generate a study guide according to selected knowledge points

1 Generating remediation study guide based on assessment report Since the system generates detailed assessment report instructor and learners can request remediation study guide based on specific assessment report. The system will generate study guide based on related knowledge pints with information of learner s knowledge status.

2 Generating remediation study guide base on knowledge status Instructor and learner can request study guide base on specific knowledge points for remediation. Such knowledge points may be selected directly from the cumulative knowledge report.

Most learning management systems allow learners to take practice assessment repeatedly until learner mastered required knowledge. The present invention can help learner to identify knowledge deficiency effectively and hence improve learning efficiency.

In a preferred embodiment each time when leaner submits a practice assessment the learning management system can send learner s result to Knowledge Module through application programming interface. The Knowledge Module analyzes learner s knowledge status and update latest knowledge status. The study guide for the same practice will be updated with learner s latest knowledge status. Then learner can use updated study guide from the Tutor Module to identify knowledge points not meeting requirement and related learning resources.

Leaner can also further retrieve knowledge status of all prerequisites of the said knowledge point to identify root cause of the deficiency. After identify the root causes learner can focus study guide of the said knowledge point to improve learning.

