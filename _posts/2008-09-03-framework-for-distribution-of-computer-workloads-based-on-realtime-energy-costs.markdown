---

title: Framework for distribution of computer workloads based on real-time energy costs
abstract: Energy costs for conducting compute tasks at diverse data center sites are determined and are then used to route such tasks in a most efficient manner. A given compute task is first evaluated to predict potential energy consumption. The most favorable real-time energy costs for the task are determined at the various data center sites. The likely time period of the more favorable cost as well as the stability at the data center are additional factors. A workload dispatcher then forwards the selected compute task to the data center having the most favorable real-time energy costs. Among the criteria used to select the most favorable data center is a determination that the proposed center presently has the resources for the task.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08214843&OS=08214843&RS=08214843
owner: International Business Machines Corporation
number: 08214843
owner_city: Armonk
owner_country: US
publication_date: 20080903
---
A framework for automatic distribution of computer workloads based on real time energy costs is described. Furthermore the overall management system and policies for such computational workload distributions is discussed.

Currently computing workloads are processed within relatively static data centers. Disaster recovery mechanisms exist to transfer data or processing to an alternate site based on an outage at an original data center location. The power costs relating to information technology IT have been steadily increasing causing some experts to predict that power costs will soon overtake computer hardware costs.

Grid computing enables the distribution of compute workloads based on available resources. It does not include methods for the determination of processing location based on real time energy costs.

Equipment power needs are a significant burden for corporate IT budgets. Many servers are underutilized indicating that processing capacity may exist in locations with lower energy costs. Not utilizing this capacity causes unnecessary incurred expense for organizations using status quo redistribution techniques.

This invention relates to a framework for dynamically shifting compute workloads among sites based on real time energy costs.

This invention also provides for dynamically shifting compute workloads among locations. A distribution hub referred to as a workload dispatcher may be used to provide the workload management functionality. This enables flexible addition removal or reassignment of infrastructure components such as data centers energy providers management policies and communications methods among others.

In greater detail the invention relates to a system and method for dynamically shifting compute workloads among data center sites based on real time energy costs. An evaluator is used to determine potential energy consumption for at least one compute task. Then a determination is made as to which of the data center sites provides the most favorable real time energy costs. This is followed by a workload dispatcher forwarding a compute task to a given data center site based upon the determination of the most favorable real time energy costs.

The invention relates to a computer readable medium containing instructions when implemented on a computer for shifting a compute workload among data center sites based on real time energy costs. The invention also relates to a computer product including the medium on which the instructions are recorded.

Likewise the present invention includes the deployment and management by a service provider such as an electric utility of the method for dynamically shifting compute workloads among data center sites based on real time energy costs to provide information technology cost saving services for its customers or clients.

The drawings are not intended to be drawn to scale. Instead the drawings are merely a schematic representation and are not intended to portray specific parameters of the invention. The drawings are intended to depict only typical embodiments of the invention and therefore should not be considered as limiting the scope of the invention.

More specifically illustrates a workload dispatcher which may be used to calculate and compare power costs and then route jobs to the best location based on the comparison. This dispatcher tracks jobs to ensure completion and reroutes jobs in the event of a failure at one location. Multiple tasks 1 2 and 3 identified as and in the drawing all submit compute jobs to the workload dispatcher . The dispatcher requests power costs at and determines whether data center 1 or data center 2 would provide service at the most reasonable price.

The framework may also set standard APIs application programming interfaces and protocols for communication among the workload dispatcher power providers data centers and any other entities.

The work of calculating costs comparing locations and dispatching work may be performed in different ways including those listed below. A preferred embodiment would allow for much of the analysis to be done by the workload dispatcher to ensure consistent methods are used. However such analysis could be accomplished 

The first step predicts or predefines the data center s and computational resources available for accepting workloads.

In the second step the compute processing tasks which are capable of being relocated are evaluated. Compute workloads are often divided into real time and queued batch. This framework may be used for either type of workload.

b Queued A system catalogs each job as it is queued or created and stores those metrics about the job s hardware prerequisites in a database. The system queries the database to locate jobs most suited to relocate.

Table 1 below illustrates one of the tables that may be used by the workload dispatcher to maintain the job queue.

The power costs are monitored in the next step at the respective data centers in real time or based upon predefined schedules.

The method in step will consider a threshold for cost differential and an element of time in determining the optimum location to run a compute job. For example it may move the workload if a one cent 1 differential in price per watt lasts for three weeks whereas it may not move it if it lasts for only one hour.

Relocation of an existing workload will also need to consider the additional overhead cost of relocation.

1. Determine the cost per unit of electrical power such as a watt the duration of that cost per each unit the length of time a job will run and a cost for the relocation of a compute job 

3. Consider the steady state cost of a job for a specified time period and subtract the reduced cost for that job to run in another data center then add the cost to relocate it time delays energy to relocate etc. . . . 

Workload is shifted at between data centers based upon lowest cost decision. Distribution may include new compute workloads or relocation of existing workloads 

Existing workloads to be relocated will also need to be halted and brought to a quiescent state before relocation.

In the last step the workload is stabilized for some period of time to prevent thrashing then resumes the aforementioned steps.

Prevention of Thrashing Constantly moving workloads can cause an inefficient thrashing scenario. Thrash is the term used to describe a degenerate situation on a computer where increasing resources are used to do a decreasing amount of work. This invention includes methods to ensure workload is distributed efficiently and avoids thrashing. This is achieved by 

Job Checkpoint Restart In some instances a job may not be able to be completed in the designated location. In these cases the framework may initiate known or future checkpoint restart methods to relocate the job without having to start over. Such a method may employ a scenario such as the following First a five day compute job is sent to a data center in San Jose Calif. After day two San Jose increases its rates dramatically. The job is paused and relocated to Denver Colo. to complete remaining three days of processing.

This invention provides a business method that performs the workload dispatch services on a subscription advertising and or fee basis. Thus for example a service provider can offer to provide information technology cost savings for its clientele in exchange for consideration to be negotiated by and between the server and individual or collective clients.

Referring now to an exemplary computerized implementation of the invention comprises a system that communicates with the workload dispatcher through an interface . The system includes a computer deployed within a computer infrastructure such as one existing at the information technology center of a business firm a manufacturing company service provider or governmental agency. Thus is intended to demonstrate among other things that the present invention could be implemented within a network environment e.g. the Internet a wide area network WAN a local area network LAN a virtual private network VPN etc. or on a stand alone computer system.

In the case of the internet communication throughout the network can occur via any combination of various types of communication links. For example the communication links can comprise addressable connections that may utilize any combination of wired and or wireless transmission methods.

Where communications occur via the Internet connectivity could be provided by conventional TCP IP sockets based protocol and an Internet service provider could be used to establish connectivity to the Internet. Still yet the computer infrastructure is intended to demonstrate that some or all of the components of implementation could be deployed managed serviced etc. by a service provider who offers to implement deploy and or perform the functions of the present invention for others.

As shown the computer includes a processing unit a memory a bus and input output I O interfaces . Further the computer is shown in communication with external I O devices resources and storage system . In general the processing unit executes computer program code such as the code to implement various components of the system which is stored in memory and or storage system . It is to be appreciated that two or more including all of these components may be implemented as a single component. The memory may also contain the various power costs that the workload dispatcher relies on to make its allocation decisions.

While executing computer program code the processing unit can read and or write data to from the memory the storage system and or the I O interfaces . The bus provides a communication link between each of the components in computer . The external devices can comprise any devices e.g. keyboard pointing device display etc. that enable a user to interact with computer system and or any devices e.g. network card modem etc. that enable computer system to communicate with one or more other computing devices.

The computer infrastructure is only illustrative of various types of such infrastructures available for implementing the invention. For example in one embodiment the computer infrastructure comprises two or more computing devices e.g. a server cluster that communicate over a network to perform the various process steps of the invention. Moreover the computer is only representative of various possible computers that can include numerous combinations of hardware.

To this extent in other embodiments computer can comprise any specific purpose computing article of manufacture comprising hardware and or computer program code for performing specific functions any computing article of manufacture that comprises a combination of specific purposes and general purpose hardware software or the like. In each case the program code and hardware can be created using standard programming and engineering techniques respectively.

Moreover the processing unit may comprise a single processing unit or be distributed across one or more processing units in one or more locations e.g. on a client and server. Similarly the memory and or the storage system can comprise any combination of various types of data storage and or transmission media that reside at one or more physical locations.

Further I O interfaces can comprise any system for exchanging information with one or more of the external devices . Still further it is understood that one or more additional components e.g. system software math co processing unit etc. not shown in can be included in computer . However if the computer comprises a handheld device or the like it is understood that one or more of the external devices e.g. a display and or the storage system could be contained within the system not externally as shown.

The storage system can be any type of system e.g. a database capable of providing storage for information under the present invention. To this extent the storage system could include one or more storage devices such as a magnetic disk drive or an optical disk drive. In another embodiment the storage system includes data distributed across for example a local area network LAN wide area network WAN or a storage area network SAN not shown . Also although not shown additional components such as cache memory communication systems system software etc. may be incorporated into computer .

Shown in the memory of computer is the processing unit which includes the components and performs the functions discussed above. In the illustrated embodiment the computer communicates with external devices such as the workload dispatcher or another computing system over a path which may be a wired bus as shown or wireless.

While shown and described herein as a method and a system it is understood that the invention further provides various alternative embodiments. For example in one embodiment the invention provides a computer readable useable medium that includes computer program code to enable a computer infrastructure to perform the process steps of the invention. To this extent the computer readable useable medium includes program code that implements each of the various process steps of the invention.

It is understood that the terms a computer readable medium or computer useable medium comprise one or more of any type of physical embodiment of the program code. In particular the computer readable useable medium can comprise program code embodied on one or more portable storage articles of manufacture e.g. a compact disc a magnetic disk a tape etc. or on one or more data storage portions of a computing device such as the memory and or the storage system e.g. a fixed disk a read only memory a random access memory a cache memory etc. .

In another embodiment the invention provides a business method that performs the process steps of the invention on a subscription advertising and or fee basis. That is a service provider could offer to manage the system . In this case the service provider can create maintain and support a computer infrastructure such as the computer infrastructure that performs the process steps of the invention for one or more customers. In return the service provider can receive payment from the customer s under a subscription and or fee agreement and or the service provider can receive payment from the sale of advertising content to one or more third parties.

In still another embodiment the invention provides a computer implemented method for executing the system . In this case computer infrastructure can be provided and one or more systems for performing the process steps of the invention such as the steps shown in can be obtained e.g. created purchased used modified etc. and deployed to the computer infrastructure. To this extent the deployment of a system can comprise one or more of 1 installing program code on a computing device such as computer from a computer readable medium 2 adding one or more computing devices to the computer infrastructure and 3 incorporating and or modifying one or more existing systems of the computer infrastructure to enable the computer infrastructure to perform the process steps of the invention.

As used herein it is understood that the terms program code and computer program code are synonymous and mean any expression in any language code or notation of a set of instructions intended to cause a computing device having an information processing capability to perform a particular function either directly or after either or both of the following a conversion to another language code or notation and or b reproduction in a different material form. To this extent program code can be embodied as one or more of an application software program component software a library of functions an operating system a basic I O system driver for a particular computing and or I O device and the like.

The foregoing description of various aspects of the invention has been presented for purposes of illustration and description. It is not intended to be exhaustive or to limit the invention to the precise form disclosed and obviously many modifications and variations are possible. Such modifications and variations that may be apparent to a person skilled in the art are intended to be included within the scope of the invention as defined by the accompanying claims.

