---

title: System, method, and computer program for selecting at least one predefined workflow based on an interaction with a user
abstract: A system, method, and computer program product are provided for selecting at least one predefined workflow based on an interaction with a user. In operation, a plurality of predefined workflows are stored. Additionally, information regarding an interaction with a user is received. Furthermore, at least one of the predefined workflows is selected, based on the information.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09459764&OS=09459764&RS=09459764
owner: Amdocs Software Systems Limited
number: 09459764
owner_city: Dublin
owner_country: IE
publication_date: 20081111
---
The present invention relates to workflows and more particularly to selecting workflows based on user interaction.

Presently most user intensive software systems present a menu of options based on the capabilities that they offer. These systems provide the users with comprehensive screens of data objects and user actions that encompass a wide range of possible needs e.g. frequent needs rare needs etc. . This results in data overload and unnecessary complexity. There is thus a need for addressing these and or other issues associated with the prior art.

A system method and computer program product are provided for selecting at least one predefined workflow based on an interaction with a user. In operation a plurality of predefined workflows are stored. Additionally information regarding an interaction with a user is received. Furthermore at least one of the predefined workflows is selected based on the information.

In the context of the present description a workflow refers to any sequence of tasks to be performed. For example the workflow may include a sequence of operations declared as work of a person work of a simple or complex mechanism work of a group of people work of an organization or other entity and or work of one or more systems or machines etc.

Additionally information regarding an interaction with a user is received. See operation . The information may include any information regarding an interaction with a user.

For example in one embodiment the information may describe user behavior. In another embodiment the information may describe user behavior associated with a plurality of the users. In still another embodiment the information may describe at least one business flow.

Furthermore the information may be collected in real time or near real time. Once the information regarding the interaction with the user is received at least one of the predefined workflows is selected based on the information. See operation .

In one embodiment the selecting may include predicting at least one of the workflows that the user is to perform. In this case the predicting may include examining tasks previously performed by the user in the context of a workflow or other techniques described below. Furthermore the prediction may include utilizing a prediction algorithm e.g. an 80 20 rule etc. .

More illustrative information will now be set forth regarding various optional architectures and uses in which the foregoing method may or may not be implemented per the desires of the user. It should be strongly noted that the following information is set forth for illustrative purposes and should not be construed as limiting in any manner. Any of the following features may be optionally incorporated with or without the exclusion of other features described.

As shown a subsystem is provided. The subsystem includes a plurality of predefined workflows . Additionally the subsystem includes workflow selection logic .

Still yet the subsystem may include memory . The memory may include any memory capable of storing data. As an option the memory may be utilized to store the workflows and or the workflow selection logic .

The subsystem may include any device or system capable of storing workflows and or logic. For example in various embodiments the subsystem may take the form of a desktop computer lap top computer a personal digital assistant PDA device a mobile phone device and various other devices. The subsystem may also include a software system capable of utilizing an application programming interface API to communicate with a user. The user may utilize a graphic user interface GUI to interface with the software system for example.

The subsystem may also be in communication with a network . The network may include a telecommunications network a local area network LAN a wireless network a wide area network WAN such as the Internet peer to peer network cable network and various other networks.

It should be noted that in various embodiments the subsystem may include additional components. Furthermore the components of the subsystem may be included as the same or separate modules. Still yet the inclusion of the components and functionality described in the context of may vary in different embodiments.

In operation the subsystem may be utilized to simplify and streamline a workload of a user by predicting a next most common action and exposing the most likely task path based on actual operational statistics. For example a user interface may be redefined for one or more software systems by dynamically analyzing the operational statistics to determine a series of actions that users e.g. operators etc. are most likely to utilize. By monitoring the detailed behavior of business flows individual behavior and groups of agents a granular approach may be provided for adapting the behavior of the software system to achieve specific business targets. In this way a fast Average Handling Time AHT may be achieved by exposing the next probable actions and data in a manner that will enable optional efficiency of the most common e.g. mainstream etc. workflows while still allowing full access to other possible tasks data though classic designs.

As shown call center operational statistics are obtained. See operation . For example a call center may track information regarding an interaction with a user. In this case the information may include operational statistics. The operational statistics may include any statistics associated with the operation of the user or a group affiliated with the user. The statistics may relate to specific users departments geographical regions the entire operation etc. as required by the business to identify meaningful statistical patterns.

The most probable tasks are then identified. See operation . For example the tasks may include a first set of tasks that are more probable than a second set of tasks.

In one embodiment the most probable tasks may be identified using the 80 20 rule. In the context of the present description the 80 20 rule refers to a rule that in the context of call center agents 20 percent of the activities the agent can do consume 80 percent of the completion time and the remaining 80 percent of the activities the agent can do may be used no more than 20 percent of the completion time. Using the techniques described herein identification optimization and the enabling of a predictive selection of the 20 of the tasks that consume 80 of the agent s time may occur to reduce average handle time AHT where it has the most impact on reducing AHT.

Once the most probable tasks are identified each workflow is analyzed to capture the main stream. See operation . In this case the operational statistics may be analyzed. For example computer code may be provided for analyzing the operational statistics. Another technique is through a variety of other techniques such as user observation questionnaires or optimized processes defined by the business owners.

It should be noted that in one embodiment operations may be automated once an adequate repository of workflows is created. This will allow the creation of automatic alerts when operational statistics change.

Once each workflow is analyzed to capture the main stream current screens are synthesized from the main stream data and or functions. See operation . The key data and or functions are then identified for each data function. See operation .

For example each task flow or a selected workflow may be analyzed to determine a main set of data. In this case a current user interface may be utilized to determine the main set of data. Key data may then be identified for the main set of data.

Once the key data and or functions are identified for each data function new screens are defined for the key data and other data. See operation . For example new user interfaces may be defined for the key data.

A launch in context of legacy systems is then defined for executions of non mainstream sub flows. This enables the maintaining of an optimized sizing and behavior while enabling the user access to less frequent sub flows and tasks 80 of the systems capabilities that are needed just 20 of the time . See operation . For the mainstream flow an interactive voice response IVR layer is designed to map to the workflows. See operation . In one embodiment the IVR layer may be designed for 20 of the system s workflows. Other less frequent workflows are accessed via the IVR by selecting the option typically defined as the last one e.g. for other needs please press for agent assistance .

Once the IVR layer is designed to map to the workflows the user interface UI is configured to launch the appropriate task on the IVR selection. See operation . As an option operations may be performed on a reoccurring basis.

For example the operations may be performed on a quarterly basis. As another option the operations may be performed on an annual basis. Of course the operations may be performed on any user defined basis.

It should be noted that in one embodiment an automatic alert may be created when operational statistics change and the IVR layer or implementation of the new workflows may be reconfigured. Furthermore the predictive component of identifying the most probable tasks may be based on an analysis of actual operational statistics predicting the most common workflows a call center agent is likely to be required to perform. In the context of the present description an agent refers to any individual or entity capable of functioning as an agent.

As shown a user selects a call reason on an interactive voice response interface. See operation . The interactive voice response interface then passes a customer identifier associated with the user and a request associated with the call reason to a Customer Relationship Management CRM system. See operation .

In other words a user identifier may be communicated to a customer relationship manager. As an option the user identifier may be communicated from the interactive voice response interface as part of an interactive voice response request.

Once this information is passed to the CRM the CRM system locates the task associated with the interactive voice response request. See operation . The task is then launched in the context e.g. of the user customer etc. . See operation .

The agent then completes the task. See operation . It should be noted that in one embodiment the interface may be pre optimized in an implementation stage.

As shown the interface illustrates information including one or more interactive voice response selections made by a user e.g. a customer etc. . Furthermore the interface may be configured such that the user utilizing the interface e.g. the customer in context etc. is the central focus of the interface . The interface may also show the most probable transaction readily available to an agent.

In this case the most probable transaction readily available to an agent may include a transaction associated with activating a new subscription. Using the most probable transaction readily available to the agent the agent may then enter any key data and select continue.

As shown when the agent enters key data and presses continue additional transaction data is presented in an additional window. In this case the additional window may include a window presented in the foreground with the previous window in the background. Additionally the interface may support sub tasks e.g. non mainstream tasks etc. and allow the sub tasks to be launched.

As shown the interface may include additional customer requests that are readily available in the visual workflows repository. For example the additional customer requests that are readily available in the visual workflows repository may include a refill prepay balance. Of course in various other embodiments the additional customer requests that are readily available may include any customer request that is readily available.

Coupled to the network is a plurality of devices. For example a server computer and an end user computer may be coupled to the network for communication purposes. Such end user computer may include a desktop computer lap top computer and or any other type of logic. Still yet various other devices may be coupled to the network including a personal digital assistant PDA device a mobile phone device a television etc.

The system also includes a graphics processor and a display i.e. a computer monitor. In one embodiment the graphics processor may include a plurality of shader modules a rasterization module etc. Each of the foregoing modules may even be situated on a single semiconductor platform to form a graphics processing unit GPU .

In the present description a single semiconductor platform may refer to a sole unitary semiconductor based integrated circuit or chip. It should be noted that the term single semiconductor platform may also refer to multi chip modules with increased connectivity which simulate on chip operation and make substantial improvements over utilizing a conventional central processing unit CPU and bus implementation. Of course the various modules may also be situated separately or in various combinations of semiconductor platforms per the desires of the user.

The system may also include a secondary storage . The secondary storage includes for example a hard disk drive and or a removable storage drive representing a floppy disk drive a magnetic tape drive a compact disk drive etc. The removable storage drive reads from and or writes to a removable storage unit in a well known manner.

Computer programs or computer control logic algorithms may be stored in the main memory and or the secondary storage . Such computer programs when executed enable the system to perform various functions. Memory storage and or any other storage are possible examples of computer readable media.

In one embodiment the architecture and or functionality of the various previous figures may be implemented in the context of the host processor graphics processor an integrated circuit not shown that is capable of at least a portion of the capabilities of both the host processor and the graphics processor a chipset i.e. a group of integrated circuits designed to work and sold as a unit for performing related functions etc. and or any other integrated circuit for that matter.

Still yet the architecture and or functionality of the various previous figures may be implemented in the context of a general computer system a circuit board system a game console system dedicated for entertainment purposes an application specific system and or any other desired system. For example the system may take the form of a desktop computer lap top computer and or any other type of logic. Still yet the system may take the form of various other devices including but not limited to a personal digital assistant PDA device a mobile phone device a television etc.

Further while not shown the system may be coupled to a network e.g. a telecommunications network local area network wireless network wide area network such as the Internet peer to peer network cable network etc. for communication purposes.

While various embodiments have been described above it should be understood that they have been presented by way of example only and not limitation. Thus the breadth and scope of a preferred embodiment should not be limited by any of the above described exemplary embodiments but should be defined only in accordance with the following claims and their equivalents.

