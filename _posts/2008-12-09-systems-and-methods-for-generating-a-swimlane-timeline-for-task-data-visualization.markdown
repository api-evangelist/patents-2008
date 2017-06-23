---

title: Systems and methods for generating a Swimlane Timeline for task data visualization
abstract: The Swimlane Timeline application for task data visualization utilizes the Microsoft Visio Application Programming Interface (API) to visualize user specified task data. The task data includes one or more of: task name, task outline number, task start date, and/or task finish date. The application solicits, interprets, and visualizes the data by mapping the user selected top-level outline number “n” as the parent task that defines the timeline and title, the “n.n” child tasks to swim lane rows, and the “n.n.n . . . ” lower level tasks to intervals and milestones within the swim lanes. Task analysis and reporting are enhanced with features including task drill-in, task filtering, and other user visualization preferences.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08402480&OS=08402480&RS=08402480
owner: Visibility.Biz Inc.
number: 08402480
owner_city: Eagan
owner_country: US
publication_date: 20081209
---
This application claims the benefit of priority under 35 U.S.C. 119 e to U.S. Provisional Application No. 61 024 973 filed Jan. 31 2008 entitled Swimlane Timeline Application for Task Data Visualization which is incorporated herein by reference in its entirety.

A portion of the disclosure of this patent document contains material which is subject to copyright protection. The copyright owner has no objection to the facsimile reproduction by anyone of the patent disclosure as it appears in the Patent and Trademark Office patent files or records but otherwise reserves all copyright rights whatsoever. Copyright 2007 Visibility.biz Inc.

Embodiments of the inventive subject matter relate generally to applications to display task data and more particularly to generating a swimlane timeline for task data.

Companies often use project management software to visualize time estimates and progress of projects. One useful visualization mechanism is the swimlane timeline in which various tasks associated with a project or portfolio of projects are placed in vertically stacked horizontal lanes referred to as swimlanes .

In the following detailed description of exemplary embodiments of the inventive subject matter reference is made to the accompanying drawings which form a part hereof and in which is shown by way of illustration specific exemplary embodiments in which the inventive subject matter may be practiced. These embodiments are described in sufficient detail to enable those skilled in the art to practice the inventive subject matter and it is to be understood that other embodiments may be utilized and that logic and other changes may be made without departing from the scope of the inventive subject matter. The following detailed description is therefore not to be taken in a limiting sense.

Companies struggle to gain insight and control of their task data particularly when it is associated with a specific project. Companies also have the need to view tasks within one project in relation to tasks of another project or collection of projects. This is sometimes referred to as a Portfolio view. In addition companies desire a method to drill in on tasks for additional detail as necessary. They also seek methods for filtering on a specific date range and filtering on a specific type of task to focus their attention on key tasks for analysis and reporting.

It is difficult costly and time consuming to manually build task and portfolio reports with data that is constantly changing. The complexity of generating reports multiplies exponentially as the number of source files increases. The swimlane timeline addresses these issues by leveraging existing task data storage methods and generating a task mapped visualization that is accurate timely and easy to decipher for analysis and reporting.

Many users and many applications store task data utilizing a parent child relationship. A parent task can have many associated sub level child tasks. Additionally child tasks can have subtasks associated with them and so on. This parent child relationship is commonly defined and stored in a hierarchical fashion using the outline notation n.n.n . . . and is referred to as an outline number or project task work breakdown structure. Each task may also have an associated start date and or finish date. Tasks can additionally have an associated percent complete value as well as task dependencies defined and often a critical task field. The swimlane timeline tool systems and methods according to their various embodiments has the capability to utilize all of these fields for customized task analysis and report generation.

In some embodiments the Swimlane Timeline Tool is implemented as a Visio add on template that runs on the Microsoft Office Visio 2003 and 2007 Standard or Professional graphics engine and it contains Visio object model methods functions subroutines as well as Visio ShapeSheet algorithms and custom developed Visio Shapes that permit reading the project task data from the source file s applying user selected filters and visualization preference settings and automatically generating a diagram referred to as a swimlane timeline.

The top level timeline of the diagram may be defined by the start and finish date of the user specified top level parent summary task. When multiple source files are selected embodiments of the swimlane timeline system run through each selected source file s parent task and determines the earliest start and latest finish dates that encompass all source files selected. Once the top level timeline start and finish dates are established the timeline is placed at the top of the diagram. The timeline length and time interval selected determines the diagram width. The lowest level interval is user selectable and can be either days weeks months quarters years or Auto. An Auto setting provided in some embodiments allows solution algorithms to determine an interval type best used for the generation of a 3 4 aspect ratio visualization and printing.

The sub level swim lanes are made up of the child tasks of the parent task and are vertically stacked below the timeline as they are encountered in the data from top to bottom. Milestones at the child task outline level are placed in a special High Level Milestones swim lane.

The lower level intervals and milestones are grandchild tasks and they may be placed vertically within their associated swim lane parent as they are encountered in the source file s from top to bottom and horizontally placed within the swim lane relative to the top level parent timeline. Solution algorithms in some embodiments can automatically adjust a swim lane height to encompass all grandchild tasks encountered. The diagram page height also grows in relation to the swim lanes growth.

A further aspect of various embodiments includes a Change Drawing Generation Information dialogue that solicits user preferences. This dialogue may be presented to the user when the swimlane timeline solution begins. The dialogue can also be accessed after the initial diagram is generated for regeneration purposes. The user preferences in the drawing generation dialogue may include 

A further aspect of various embodiments includes the support of but not limited to the following source file formats 

A further aspect of various embodiments includes the option to select multiple source files for the creation of an ad hoc portfolio view of a group of source files. Each swim lane title in the portfolio view is the source file s name. The source file s Last Modified date can also be shown.

A further aspect of various embodiments includes the ability to show a user selectable Single page outline level depth . The single page outline level depth preference combined with the other available filters can allow an organization to visualize their specific key tasks to track on one single page.

A further aspect of various embodiments is the ability to drill in on a swim lane or interval task. The drill in action creates a new page labeled with the task outline number and name. The new page will be another swim lane timeline with the selected task at the parent task its children tasks as the swim lanes and its grand children tasks as intervals and milestones. A bi directional hyperlink is automatically added by the Swimlane Timeline Tool to aid navigation.

A further aspect of various embodiments includes the option to automatically drill in each swim lane during the initial diagram generation based on the Multi page outline level depth setting.

A further aspect of various embodiments includes the option to Apply custom fields for task short name color and type . When utilized the system will override the swimlane timeline default attributes based on custom fields that reside within the source file s . These fields include a task short name text to display task color number to use for an interval or milestone and task milestone type number. The color numbers are based on the Visio default color palette mapping. The milestone type number mapping is shown below 

A further aspect of various embodiments includes the option to filter tasks visualized. The swimlane timeline code will only display tasks that meet the filter criteria for example if the task associated Critical field or the VisibilityFlag field is set to Yes in the source data .

A further aspect of various embodiments includes the visualization of a Percent Complete field if it exists in the source file s . The percent complete shapes are placed in a Percent Complete layer in Visio. Users have the ability to display or hide the percent complete visualization via Visio s layer control settings. There are a number of various methods that the task percent complete value can be visualized.

A further aspect of various embodiments includes the option to display task dependencies with arrows showing the flow of the dependency between the tasks. Arrows start at either an interval or milestone lower left or lower right side based on the type of dependency either with a beginning point of Start or Finish respectively. Arrows end at either an interval or milestone upper left or upper right based on the type of dependency either from a ending point of Start or Finish respectively. The dependency arrows are placed on a Visio dependency layer so they can be easily shown or hidden. The dependency arrows can be further customized to show dependency lag and lead times. In some embodiments there are four supported types of dependencies 

A further aspect of various embodiments includes the option to override default RGB color assignments and text size settings for swimlane timeline global color and text attributes. There are multiple customizable palettes to edit and select. The user changeable swimlane timeline global attributes in some embodiments include 

A further aspect of various embodiments includes the option to show or hide a Time Interval highlight. Multiple time intervals can have their highlight turned on as desired.

A further aspect of various embodiments includes the option to show or hide Today s Date Indicator that may be a thin red transparent line that runs through all swim lanes for the vertical height of the entire diagram. This feature is accessed from the Visibility pull down menu.

A further aspect of various embodiments includes the option to show or hide a single or multiple Add Date Indicators that may be a thin blue transparent line that runs through all swim lanes for the vertical height of the entire diagram. This feature is accessed from the Visibility pull down menu.

A further aspect of various embodiments includes the option to reposition the task label with a right click action on the task. Possible task label positions for intervals include Wrapped Centered Wrapped Right and Wrapped Left. Possible label positions for milestones includes all of the above and in addition Centered Upper Right Upper Left Centered Right Centered Left Lower Right and Lower Left. Alternatively users can freely reposition the task label using Visio s native Text Block Tool.

A further aspect of various embodiments includes the option to lock the timeline and swimlane titles. This option allows the user to navigate anywhere in the diagram and still see the time interval and swimlane titles. To activate right click in the diagram white border area and select Toggle Title Lock On Off .

A further aspect of various embodiments includes the full support of Visio native features including but not limited to color control text control line types fill types print controls save as web pan and zoom window keyboard shortcuts layer control and selecting multiple shapes and changing settings for all.

Various source files may be used to provide data for the swimlane timeline application . Examples of such source files include one or more of the following 

The time interval highlight feature is accessed via a right click on a time interval in the timeline. When selected a highlighted and transparent time interval band that is the width of the interval is displayed throughout all swim lanes and for the vertical height of the entire diagram.

In addition to the examples provided above various embodiments provide a shading style to be applied based on a percentage complete of a task. In some embodiments there are two Shading Styles to choose from Percent Complete and Percent Progress default . The percent complete shading style uses the MS Project Complete value directly to determine what percent of the interval to shade. The percent progress uses the following formula to determine the percent shading Percent Progress min today s date finish start finish start SPI where SPI is the Schedule Performance Index showing the ratio of the budgeted cost of work performed BCWP to the budgeted cost of work scheduled BCWS or BCWP BCWS .

At block a system implementing the method processes the task data. In some embodiments the task data is processed according to user preferences and display settings. In some embodiments the placement and layout of tasks for the generation of the swimlane timeline diagram based on the task outline numbers or alternatively a work breakdown structure field. The text field values for task outlines may be represented as n.n.n . . . values. A value of 0 indicates the top level summary task. A value of 1 n represents the sublevel child tasks of the summary task. A value of n.1 n represents the lower level grandchild tasks of the summary task and it also represents the children of the sublevel tasks.

If a single source file received at block then the task outline numbers are interpreted in the following manner 

If multiple source files are received at block then the task outline numbers are interpreted in the following manner 

User custom preferences for the swimlane timeline visualization is supported via source file s custom task fields in some embodiments 

User preferences are preserved in an XML file stored in the Microsoft Windows user Application Data Visibility.biz sub directory. User preferences are restored with subsequent openings of the source file selection dialogue. Stored preferences may include 

In some embodiments various combinations of the following additional user preferences may be supported by the Swimlane Timeline application 

At block a swimlane timeline diagram is output according to the processed task data and further according to a diagramming software format. In some embodiments a Microsoft Visio format may be used.

User selected task drill in on a single task creates a new Visio page in the same Visio VSD file. The new page name is the user selected task name preceded with the task outline number in parenthesis. The swimlane timeline application uses the selected task outline number as the starting outline number for the new swimlane timeline generated and the diagram will be visualized and interpreted described above.

Simultaneous drill in of multiple swim lane tasks is a user preference. When selected separate swimlane timeline pages will be generated as described above. The drill in process is repeated for the number of levels specified.

In the various embodiments any of the components of system can include hardware firmware and or software for performing the operations described herein. Machine readable media includes any mechanism that provides e.g. stores and or transmits information in a form readable by a machine e.g. a computer server etc. . For example tangible machine readable media includes read only memory ROM random access memory RAM magnetic disk storage media optical storage media flash memory machines etc. Machine readable media also includes any media suitable for transmitting software over a network.

Thus systems and methods to generate swimlane timeline diagrams with the Swimlane Timeline application have been described. Although the present inventive subject matter has been described with reference to specific example embodiments it will be evident that various modifications and changes may be made to these embodiments without departing from the broader spirit and scope of the inventive subject matter. The swimlane timeline may be implemented in various document object models according to various example embodiments. While the Visio object model has been described herein the inventive subject matter is not limited to only a Visio object model. Accordingly the specification and drawings are to be regarded in an illustrative rather than a restrictive sense. Many other embodiments will be apparent to those of skill in the art upon review of the above description.

In this detailed description reference is made to specific examples by way of drawings and illustrations. These examples are described in sufficient detail to enable those skilled in the art to practice the inventive subject matter and serve to illustrate how the inventive subject matter can be applied to various purposes or embodiments. Other embodiments are included within the inventive subject matter as logical mechanical electrical and other changes can be made to the example embodiments described herein. Features or limitations of various embodiments described herein however essential to the example embodiments in which they are incorporated do not limit the inventive subject matter as a whole and any reference to the invention its elements operation and application are not limiting as a whole but serve only to define these example embodiments. This detailed description does not therefore limit embodiments of the invention which are defined only by the appended claims.

Each of the embodiments described herein are contemplated as falling within the inventive subject matter which is set forth in the following claims.

