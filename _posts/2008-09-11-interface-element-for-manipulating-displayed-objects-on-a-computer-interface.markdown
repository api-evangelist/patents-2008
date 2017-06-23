---

title: Interface element for manipulating displayed objects on a computer interface
abstract: The present invention provides method of manipulating a displayed object capable of interacting with an interface element of a computing interface. The computing interface has a display module for displaying the displayed object in a display area, and which causes the displayed object to interact with the interface element and manipulating the displayed object according to the nature of the input received. The manipulation includes varying the size of the displayed object when the received input results in movement of the displayed object, into, out-of, or through a region of the display area designated as belonging to the interface element.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09047004&OS=09047004&RS=09047004
owner: Smart Internet Technology CRC PTY LTD
number: 09047004
owner_city: Eveleigh NSW
owner_country: AU
publication_date: 20080911
---
The present invention relates generally to interfaces for computing systems and more particularly but not exclusively to a system method and interface for manipulating objects on a computer interface.

Interactive desktop interfaces are known as part of current computer operating systems. In some computing applications it is desirable to have an interactive tabletop interface. An interactive tabletop interface allows for interaction with one or more users on a tabletop display. An interactive tabletop interface facilitates collaborative sharing of objects such as digital photographs by a number of users. Such an interface comprises an image which is projected onto the tabletop display. The image may be projected for example by use of an embedded screen or a data projector. One or more users may interact with the displayed image via an input of the interface in order to for example manipulate objects in the displayed image. Input to the interface is provided by for example a touch sensitive surface of the tabletop onto which the image is projected. This form of computer interface facilitates so called pervasive computing.

However when many objects are displayed on a tabletop computer interface the interface can become cluttered. This can prevent the user from readily interacting with the displayed objects and detract from the user s productivity.

According to a first aspect of the present invention there is provided a method of manipulating a displayed object capable of interacting with an interface element of a computing interface the computing interface having a display module for displaying the displayed object in a display area and an input module for receiving a user input said method comprising 

manipulating the displayed object according to the nature of the input received wherein the manipulation comprises varying the of the displayed object with the interface element.

In one embodiment size of the displayed object when the received input results in movement of the displayed object into out of or through a region of the display area designated as belonging to the interface element.

In one embodiment the user input results in movement of the displayed object within the display area in a manner that results in interaction the user input directly moves the displayed object.

In one embodiment the user input causes the displayed object to move into out of or through the region of the interface element.

In one embodiment the user input causes the region of the interface element to be redefined within the display area which results in interaction of the interface element with the displayed object.

In one embodiment redefining the region of the interface element is in the form of moving the region within the display area.

In one embodiment redefining the region of the interface element is in the form of resizing the region within the display area.

In one embodiment the user input signifies activation of a manipulation property of the interface element which results in interaction of the interface element with the displayed object.

In one embodiment the size of the object is varied according to the direction of movement through the region. Preferably the direction is a radial direction.

In one embodiment the size of the object is reduced as the object is moved towards the centre of the region.

In one embodiment the size of the object is increased as the object is moved away from the centre of the region.

In one embodiment the method comprises manipulating a plurality of displayed objects according to the nature of the input received.

In one embodiment the influence further comprises varying the size of all displayed objects which move into out of or through the region.

In one embodiment the influence further comprises moving all display objects located within the region along with the region when the region is moved.

In one embodiment the influence further comprises moving all display objects located within the region along with the region when the region is moved unless the region encounters a prohibited zone of the display area in which case the region is prevented from entering the prohibited zone and the display objects continue to move according to the received input.

In one embodiment the manipulation further comprises causing all displayed objects in the region to move towards the centre of the region when the user input signifies activation of an manipulation property of the interface element.

In one embodiment the manipulation further comprises causing all displayed objects in the display area to move towards the centre of the region when the user input signifies activation of a manipulation property of the interface element.

In one embodiment the manipulation further comprises causing displayed objects having a selected property to move towards the centre of the region when the user input signifies activation of an manipulation property of the interface element.

In one embodiment the manipulation further comprises causing displayed objects that reach the centre of the region to be hidden.

In one embodiment the manipulation is to cause all displayed objects in the region to move away from the centre of the region when the received input signifies activation of a manipulation property of the interface element.

In one embodiment the manipulation is to cause all displayed objects in the display area to move away from the centre of the region when the received input signifies activation of a manipulation property of the interface element.

In one embodiment the manipulation further comprises causing displayed objects having a selected property to move away from the centre of the region when the received input signifies activation of a manipulation property of the interface element.

In one embodiment the manipulation further comprises causing displayed objects within the region to be deleted when the received input signifies activation of a manipulation property of the interface element.

In one embodiment the influence further comprises causing displayed objects within the region to be resized when the received input signifies resizing of the interface element. Preferably the resizing of the objects is of the same type and or proportion as the resizing of the interface element. In an embodiment the resizing of the object is in proportion to the size of the region of the interface element.

In one embodiment the manipulation further comprises causing hidden displayed objects within the region to be shown when the received input signifies activation of a manipulation property of the interface element.

In one embodiment a representation of the interface element is displayed within the region. In one embodiment the representation is of a black hole.

According to a second aspect of the present invention there is provided a computer readable storage medium storing a computer program for manipulation a displayed object in a display area that interacts with an interface element of a computing interface said computer program comprising instructions that when executed by a computer cause the computer to 

manipulating the displayed object according to the nature of the input received wherein the manipulation comprises varying the size of the displayed object when the received input results in movement of the displayed object into out of or through a region of the display area designated as belonging to the interface element.

According to a third aspect of the present invention there is provided an apparatus for manipulation a displayed object that interacts with an interface element of a computing interface said apparatus comprising 

manipulating the displayed object according to the nature of the input received wherein the manipulation comprises varying the size of the displayed object when the received input results in movement of the displayed object into out of or through a region of the display area designated as belonging to the interface element.

According to a fourth aspect of the present invention there is provided an apparatus for manipulating displayed objects that interacts with an interface element of a computing interface said apparatus comprising 

means for receiving a user input which causes the displayed object to interact with the interface element 

means for manipulating the displayed object according to the nature of the input received wherein the manipulation comprises varying the size of the displayed object when the received input results in movement of the displayed object into out of or through a region of the display area designated as belonging to the interface element.

According to a fifth aspect of the present invention there is provided an interface element for a computing interface having a display module for creating a display covering a display area and an input module for receiving a user input said element comprising 

an interface element interaction module for designating certain user input that causes the displayed object to interact with the interface element as interface element input 

an object manipulation module for manipulating objects in the display according to the nature of the input received when an interface element input is received wherein the manipulation module is configured to vary the size of displayed objects that the input signifies as moving a displayed object into out of or through the region.

An aspect of the present invention provides a new interface element for reducing screen clutter on a computer interface. In the embodiment described herein the computer interface is displayed on a surface mount display provided by a tabletop computing system. The interface element operates to manipulate or influence objects displayed on the interface based on a user input. In an embodiment manipulating the object comprises varying the size of the displayed object when the received input results in the object being moved into out of or through a region of the display associated with the interface element. For example where a user of the tabletop computer wants to focus their attention on one of ten objects e.g. a digital photograph presently displayed on the user interface they may drag any one or more of the other nine objects towards the interface element to effectively minimize their size.

To carry out the aforementioned functionality and with reference to the tabletop computer comprises computer hardware including a motherboard central processing unit random access memory hard disk and networking hardware . The tabletop computer also includes a display in the form of a projector which projects an image i.e. the user interface onto a tabletop surface. The tabletop computer also includes an input module for receiving a user input from an input device. Using the input device users of the tabletop computer manipulate objects displayed on the user interface.

In addition to the hardware the tabletop computer includes an operating system such as the Microsoft Windows XP operating system which is produced and licensed by Microsoft Corporation that resides on the hard disk and which co operates with the hardware to provide an environment in which the software applications can be executed. In this regard the hard disk of the tabletop computer is loaded with a display module for controlling a video output device which displays the user interface.

In the embodiment described herein the objects are in the form of digital photographs but it will be appreciated that other objects such as text files or computer generated graphical images could equally be displayed and manipulated. In an embodiment input to the interface is provided by a touch sensitive surface of the tabletop onto which the image is projected.

In the embodiment described herein the objects are in the form of digital images displayable on the tabletop. The images may colloquially be referred to as photographs . The photographs are displayed as rectangular objects within the display area. Photographs can be moved across the tabletop by mimicking a dragging motion with a pointer such as a finger pen stylus or cursor. The touch of the pointer is received by the input device and interpreted as an input. The photographs can be manipulated in other ways such as for example moving rotating and resizing depending on the input.

If many photographs are displayed the display area can become cluttered. This can detract from the productivity of the user. The embodiment therefore provides an interface element which can hold objects not currently required by the user. The held objects are resized to assist in reducing clutter. Furthermore one embodiment of the invention allows the interface element to temporarily remove photographs from the display area. In a further embodiment they can be permanently deleted.

Referring to there is shown a screen shot of a tabletop computer user interface displaying the interface element pictorially represented and hereafter referred to as a black hole. The black hole is typically circular in shape as such a shape is instantly recognisable to a user. However it will be understood that the black hole may take any suitable form. The black hole forms part of the interface. The black hole has a region of influence which is part of the user interface . Objects such as the photographs that enter into the region of influence or move within the region are affected by influence characteristics of the black hole . The black hole comprises a centre portion and a periphery which divide up the region of influence. In one embodiment the centre portion has one type of influence and the periphery has another type of influence on objects in the region depending on whether the object is in or touches the centre portion or is in or touches the periphery without touching the centre portion .

Objects moving in the periphery automatically have their size changed according to whether the user input moves them towards or away from the centre of the black hole. The resizing is immediate and in proportion to the movement in order to give real time feedback to the user input which cause the object to be moved. In particular when the object moves towards the centre it is reduced in size and when it moves away from the centre it is enlarged. This continuous feedback gives the appearance of the photograph being sucked into the black hole or spat out of the black hole depending on the direction of movement.

In an embodiment the centre portion hides objects moved within it. In another embodiment objects that touch the centre portion are deleted from the display. The centre portion may be the geometric centre point of the black hole or it may be a small central area.

The interface displays objects by maintaining in memory the position of the objects their scale and their orientation within the display. The display is repeatedly redrawn using a graphics API such as OpenGL. Each time the display is redrawn OpenGL draws a texture for that object as well as decorations at the correct position and orientation. When interaction occurs the interface determines which object was selected and where on the object the selection occurred.

The interface then determines in what way the input manipulates the selected object. This includes determining whether and how the input causes the selected object to be moved. The interface element determines whether the movement of the object causes it to be affected by the black hole. See Appendix A as an example of instructions in the form of C code for implementing this. Alternatively if the black hole is selected the interface element determines whether the manipulation of the black hole affects other objects.

In it can be seen that the user has touched the tabletop or screen or used a cursor directed by a mouse track ball or other input device over the object and has dragged the object into the region of influence of the black hole. The finger pointer moves closer to the centre of the black hole rather than the centre of the object moving closer. The centre of the object just travels with the movement of the pointer. The black hole has recognised that the input has caused the object to move within this region of influence and has caused the object to be diminished in size as it moves. If it reaches the centre portion the photograph becomes hidden. See for example Appendix B below.

Photographs that are placed in the periphery of the black hole can be recovered by simply selecting them and dragging them out. This will cause them to be enlarged back to the size before they were influenced by the black hole.

If the back hole is resized the photographs within the region of influence change their size inverse proportionally. In one embodiment this is due to the scaled size of the object in the region of influence being shrunk in proportion to the size of the black hole thus as the black hole is reduced in size its shrinking effect on the object diminishes. Thus another method to remove photographs from the black hole is to reduce the black hole size such that photographs within the black hole grow in size and can be selected and dragged out from the region of influence of the black hole.

Objects that are placed in the region of influence of the black hole become attached. In other words if the black hole is moved then the objects move with the black hole.

Algorithms are employed to determine layering of photographs around the black hole. One algorithm keeps objects in the black hole as it is moved and another algorithm determines the size of objects within the region of influence based on the size of the image the size of the black hole and the Euclidean distance between the centres of the each image and the black hole.

Another way of removing objects from the black hole is for the user to attempt to move the black hole into a zone of the display area in which the black hole is prohibited from entering such as a personal space. Even though the black hole cannot be moved into the personal space the objects stuck to the black hole can enter the space and will be dragged out as the user continues to move the pen stylus etc. Thus the black hole gets stuck on the border of personal space while the photographs are moved into the personal space.

When the user holds a selected position on the black hole this can activate one or more manipulations of black hole. In one embodiment the manipulation characteristic causes all the objects in the region of influence to be permanently deleted. In a further embodiment the manipulation characteristic may also cause other images on the tabletop to move continuously towards black hole providing an appearance of gravity . One such other manipulation characteristic is to have images within a black hole move radially and other images on the tabletop to move away from the black hole providing an appearance of anti gravity . Another is for the gravity to only affect objects with specifics characteristics.

Various other manipulation characteristics will be readily apparent to the person skilled in the field invention. Such manipulation characteristics provide the user with intuitive feedback.

In some embodiments the continuous movement occurs at a constant velocity. In another embodiment the continuous movement accelerates while the input is active. The objects may then be given virtual momentum and subjected to virtual friction as described below in relation to flicking . In an embodiment the continuous movement is along a tangent to the central region of the black hole. In an embodiment the velocity of the movement for each object is proportional to the inverse of the distance between the centre points of the black hole and the object.

Objects on the tabletop may be subjected to flicking . Flicking provides an object with an associated momentum which is counteracted by a virtual frictional force. Flicking is described in Margaret R. Minsky. Manipulating simulated objects with real world gestures using a force and position sensitive screen. 18 3 195 203 1984. ISSN 0097 8930. doi http doi.acm.org 10.1145 964965.808598 which is incorporated herein by reference .

When an image is flicked in the direction of a black hole and it encounters the region of influence a virtual gravitational force can be simulated which causes the object to accelerate towards the centre portion of the black hole. The algorithm employed maintains the momentum of the object and applies acceleration towards the centre of the black hole. The algorithm can closely model the physics of gravity to maintain a realistic feedback to the actions of the user. Thus the object does not simply disappear but rather as the object hits the black hole it will spiral inwards towards the centre of the black hole.

It is possible for the object to remain in an ongoing orbit. However the algorithm can have a term included such that when the component wise change in velocity is in the opposite direction to the velocity the acceleration towards the centre is increased. This causes the path of objects to favour spiralling in towards the centre of the black hole even where the object was not intently aimed directly towards the centre. As an object encounters the centre portion it is captured and hidden. Thus an image can be flicked generally towards the black hole and it will be sucked into the black hole even if the aim is not entirely accurate. In other words the object need not be directed to the central region as long as it encounters the region of influence it will be drawn in. This can allow a user to delete an object even if the back hole is not within reach. See for example Appendix C D.

If the flick of the object is too hard and the object has sufficient momentum the object will pass the black hole without being drawn into the black hole. This can result in a gravitational slingshot effect. However further modifications can be made to the algorithm to prevent sling shotting.

In one embodiment black holes are prevented from being flicked. That is they will not gain momentum even though the object can be moved across the tabletop. Once the black hole is released it will simply stop where it was released. However objects within the black hole can maintain momentum. Therefore when the black hole stops objects within it can keep moving by virtue of their momentum and with thus fall out of the black hole. Alternatively objects within the black hole can maintain stationary inertia and thus when the black hole is moved too quickly the objects tend to move less quickly and will fall out of the black hole.

When an object is in central portion of the black hole the displayed scale is altered after processing the desired scale as follows 

There is a transformation from world coordinates to screen coordinates in order to display an object.

Two notions of layering are used to determine the final draw order of objects z coordinate and layer. Objects drawn last will be shown occluding any objects below it unless parts of the object are partially or wholly transparent. The black hole for example is transparent around its edges opaque in the centre with a transparency gradient between. The z coordinate of the object determines the final draw order objects are drawn in order of decreasing z coordinate .

Whenever an object is selected it is given the lowest z coordinate of any object in the same layer thus it appears on top of those objects. Special objects such as the black hole are given a higher layer. Thus the black hole is always shown on top of other objects and it is never obscured.

Objects can be flipped over as if they were physical photographs placed on the table. In the touch interface this was accomplished by for example placing two fingers on the image one each in adjacent photo corners and then dragging the fingers across the image to flip it. Alternative flipping techniques can also be employed such as selecting a hot spot for example triangles superimposed on the corner of each object and dragging it over the rest of the image.

The technique for flipping an object is shown in Appendix E to H. They take as arguments the x y pixel coordinate on screen that is the current control point used for the flip e.g. the location of the stylus or finger. The first step is to convert this to object coordinates using the cached inverse transformation matrices used to position the object being flipped in the virtual environment but before any flipping rotation transformation took place in the draw procedure . The x coordinate is normalised to make it comparable with the y coordinate i.e. they are given equal weighting to determine the initial direction to flip .

If the flip has not already begun the direction xflip is determined as the direction with the larger component i.e. most distant from the centre of the image . And it is a reverse flip if we are to the left of centre for a horizontal flip or below centre for a vertical flip. The distance to flip dist is twice the position component as points initially extend from 0.5 to 0.5 so dist lies in the range 1.0 1.0 . The angle to flip is the arccosine of the dist. We maintain state to continue a flip in the same direction once initiated and to determine whether we are flipping to the reverse side or back to the front side. The flipping of the image itself occurs in the draw procedure.

If the object flipped is the black hole the hidden contents of the black hole can be displayed. This allows the user to select and drag objects out of the black hole.

The flipping technique described above is the subject of a related Australian provisional patent application entitled A System and Method for Manipulating Digital Images on a Computer Display filed in the name of Smart Internet Technology CRC Pty Ltd and accorded provisional filing number AU2007 904927 which is incorporated herein by reference.

Consider the following scenario a user plugs their digital camera into a computer loaded with an interface in accordance with an embodiment of the present invention. It holds a large number of photos taken from a recent holiday so an object containing thumbnails for the photos is loaded. Sometimes the thumbnail is insufficient quality to judge whether an image is the one desired to discuss or to decide between two closely related photos. Dragging a thumbnail off the object causes a higher quality copy of the thumbnail to be created. However the user decides that they no longer need this copy so they wish to delete it.

On a traditional computing interface the user might drag the icon to a Trash Can or Recycle Bin but in a virtual environment this has a number of problems. The trash is usually located at a fixed position on the display. On a physically large virtual interface a user might not be able to reach the location of the object and so they may wish to flick the object in the direction of the trash alternatively they may wish to move the trash object around the environment. There may be multiple users and the trash may only be oriented or easily accessible by a single user. Opening the trash to retrieve something is impractical on a tabletop computing system particularly where an interface is designed to be intuitive to users not familiar with standard computer conventions. Offering a confirmation dialogue to confirm deletion or a context menu to move an item to trash is also impractical. The trash may be obscured and an inexperienced user may inadvertently move an item over the trash accidentally deleting it. An object may be displayed on a screen much larger than the trash object and without a mouse cursor it might not be clear how to indicate that something should be moved to the trash. The user may also wish to partially hide the image without deleting the image.

To delete a photograph image i.e. an object using the black hole the user drags the object e.g. with a finger or stylus towards the black hole. Once the user s finger i.e. not the centre of the image regardless of where it was touched is within the influence of the black hole bhd

The user may also wish to move the black hole. They do this simply by dragging it the black hole and all its contents including items on its periphery or fringes which may still be visible are moved to the new location maintaining their relative positions. As the black hole moves objects which come near the black hole are affected if their centres enter the fringe. If the black hole is then released the objects influenced by the black hole are captured by the black hole allowing the black hole to be used in a manner akin to a vacuum cleaner on the virtual environment.

After being released into the black hole objects can be retrieved. Techniques for this vary depending on the distance into the Black hole the image is placed. If the object is on the fringe of the black hole the object may be able to be moved out provided some of the object pokes out from underneath the black hole. If no part of the object sticks out the black hole may be made smaller decreasing its effect on the object i.e. as the black hole scale s is reduced bhd becomes larger . When the object on the fringe becomes larger and can then be moved away. However a limit may be imposed on how small the black hole can be made. If an object is very near the black hole centre it can be retrieved by moving the black hole to a dumping ground such as a personal space where the black hole is not allowed to travel. Alternatively repeatedly flicking the black hole can cause the images within the black hole to be left behind.

Although not required the embodiments described with reference to the Figures can be implemented via an application programming interface API or as a series of libraries for use by a developer and can be included within another software application such as a terminal or personal computer operating system or a portable computing device operating system. Generally as program modules include routines programs objects components and data files that perform or assist in the performance of particular functions it will be understood that the functionality of the software application may be distributed across a number of routines objects and components to achieve the same functionality as the embodiment and the broader invention claimed herein. Such variations and modifications are within the purview of those skilled in the art.

It will be understood to persons skilled in the art of the invention that many modifications may be made without departing from the spirit and scope of the invention.

