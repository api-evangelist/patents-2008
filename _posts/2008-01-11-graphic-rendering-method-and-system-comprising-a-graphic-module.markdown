---

title: Graphic rendering method and system comprising a graphic module
abstract: A method for rendering a three dimensional scene on a displaying screen comprises: generating for a tile of a current scene a hierarchical z-buffer which comprises a plurality of levels organized according to depth values; calculating a minimum depth value d of a submitted primitive; calculating an intersection area associated with said primitive with respect to said tile; providing a multiplicity of aligned regions each associated with a level of the hierarchical z-buffer so that the exact area calculated is suitable to be covered, at least entirely, by the union of such aligned regions; comparing the minimum depth value d of the submitted primitive with corresponding maximum depth values v, v, . . . , vN each read from the levels of the hierarchical z-buffer; discarding said primitive whether the minimum depth value d is bigger than all maximum depth values v, v, . . . , vN.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08456468&OS=08456468&RS=08456468
owner: STMicroelectronics S.r.l.
number: 08456468
owner_city: Agrate Brianza
owner_country: IT
publication_date: 20080111
---
The present disclosure relates to the technical field of graphic rendering and particularly to 3D three dimensional rendering. More particularly the present disclosure can be applied to the sort middle technique.

Computer graphics is the technique of generating pictures with a computer. Generation of pictures or images is commonly called rendering. Generally in three dimensional 3D computer graphics geometry that represents surfaces or volumes of objects in a scene is translated into pixels and then displayed on a display device.

In computer graphics each object to be rendered is composed of a number of primitives. A primitive is a simple geometric entity such as e.g. a point a line a triangle a square a polygon or high order surface.

Two main rendering techniques are known the traditional technique also called immediate mode rendering and the sort middle technique also called tile based rendering .

According to the first rendering technique a graphic pipeline known by those skilled in the art as an immediate mode renderer processes a set of three dimensional 3D primitives by a client server mechanism based on an application programming interface API . Particularly such primitives are processed in the submission order.

Such graphic pipeline operates to process primitives in order to compose an external color buffer or frame buffer a depth buffer and a texture memory of a displayed final scene. Particularly in accordance with the sort middle approach the scene is decomposed into tiles which are rendered one by one. This allows color components and z values of one tile to be stored in small on chip buffers a first color buffer CB and a first depth buffer DB respectively. In this way only the pixels visible in the final scene need to be stored in the external frame buffer .

The applicant observes that in rendering processing a current primitive can occlude or overlap a previously drawn primitive. Hence a pixel on the screen can be drawn several times causing an increasing of the overdraw factor which is indicative of a ratio between the total number of pixels or fragments processed and written into the frame buffer and the frame buffer resolution.

It has been noticed that there is a need in the field in reducing the overdraw factor since this reduction allows to increase the bandwidth connected to the pipeline buffers and limit the access to such graphic pipeline buffers.

generating for a tile of a current scene a hierarchical z buffer which comprises a plurality of levels organized by increasing depth values 

providing a multiplicity of aligned regions each associated with a level of the hierarchical z buffer so that the exact area calculated is suitable to be covered at least entirely by the union of such aligned regions 

comparing the minimum depth value d of the submitted primitive with corresponding maximum depth values v v . . . vN each read from the levels of the hierarchical z buffer 

discarding said primitive whether the minimum depth value d is bigger than all maximum depth values v v . . . vN.

This and other aspects of the disclosure will be apparent upon reference to the attached figures and following detailed description.

As an example the mobile phone can be a cellular phone provided with an antenna a transceiver Tx Rx connected with the antenna an audio circuit unit AU CIRC connected with the transceiver . A speaker and a microphone are connected with the audio circuit unit .

Further the mobile phone is provided with a CPU central processing unit for controlling various functions and particularly the operation of the transceiver and the audio circuit unit according to a control program stored in a system memory MEM connected to the CPU . The graphic module is coupled to and controlled by the CPU . Moreover mobile phone is provided with a display unit provided with a corresponding screen e.g. a liquid crystal display DSPY and a user interface such as an alphanumeric keyboard K B .

The graphic module is configured to perform a set of graphic functions to render an image on the screen of the display . Preferably the graphic module is a graphic engine configured to render images offloading the CPU from performing such task. As used herein the term graphic engine means a device which performs rendering in hardware or software not running on a CPU but on another coprocessor such as a DSP digital signal processor . The terms graphic accelerator and graphic coprocessor also employed in the field are equivalent to the term graphic engine. 

Alternatively the graphic module can be a graphic processing unit GPU wherein the rendering functions are performed on the basis of hardware and software instructions executed on a dedicated processor such as a DSP. In accordance with a further embodiment some or all the rendering functions are performed by the CPU .

In accordance with the sort middle rendering the screen of the display is divided in a plurality of 2D two dimensional ordered portions i.e. 2D tiles such as for example square tiles. As an example the screen is divided into 2D tiles each having 16 16 pixels or 64 64 pixels.

The graphic engine illustrated in comprises a graphic pipeline . Such pipeline comprises the following modules or stages a driver stage a geometry stage for example of TnL type a pre processing module a rasterizer and a fragment processor .

The driver is a block having interface tasks and is configured to accept commands from programs e.g. application protocol interface API running on the CPU and then translate them into specialized commands for the other blocks of the graphic engine .

The geometry stage is configured to process primitives and applying transformations to them so as to move 3D objects. As defined above a primitive is a simple geometric entity such as e.g. a point a line a triangle a square a polygon or high order surface. In the following reference will be often made to triangles which can be univocally defined by the coordinates of their vertexes without other types of employable primitives.

The pre processing module comprises a tiler stage TILER suitable to exchange data with a scene buffer SB and preferably tiler is arranged to operate as a binner and parser. Particularly the tiler stage acting as a binner stage is adapted to acquire from the geometry stage primitive coordinates and associate them with each tile of the screen . Particularly the binner function of tiler allows to collect lists of instructions called displaying lists suitable to describe how and in which order the primitives have to be processed and to obtain the 3D scene renderized as a collection of renderized independent tiles. Such tiler stage is coupled to the scene buffer which is a memory able to store information provided by the tiler itself. As an example the scene buffer is a memory external to the graphic module and can be the memory system illustrated in .

It should be observed that information stored in the scene buffer are attributes of submitted primitives such as position data particularly a depth information or z value of each primitive with respect an observer color data and context data indicative of operations that the rasterizer stage and the fragment processor have to perform on the primitive itself. In general attributes are data color coordinates position texture coordinate etc. associated with a primitive. As an example a triangle vertex has the following attributes color position coordinates associated with texture. As known to the skilled person a texture is an image e.g. a bitmap image that could be mapped on the primitive.

Acting as parser the tiler stage is responsible for reading for each tile the information stored in the scene buffer and passing such information to the following stages also performing a primitive reordering operation.

The rasterizer stage is configured to perform processing of primitive data received so as to generate pixel information representing images such as the attribute values of each pixel.

The fragment processor is suitable to perform a set of operations on a fragment produced by rasterizer to produce a color to be written into the display memory . Particularly in one embodiment the graphic pipeline operates to process primitives in order to compose an external color buffer or frame buffer a depth buffer and a texture memory comprised in the display memory of a displayed final scene. Particularly the frame buffer stores information indicating the final color of a pixel whether such pixel is viewed onto the screen. The depth buffer is suitable to indicate whether a pixel is viewed or not by memorizing the depth data z values connected to the distance of a primitive from an observer. Usually such depth data are 8 bit words allowing to map different positions starting from a position which is nearest the observer.

In accordance with the sort middle approach the scene is decomposed into tiles which are rendered one by one. This allows the z values and color components of one tile to be stored in small on chip buffers a first depth buffer DB and a first color buffer CB respectively. In this way only the pixels visible in the final scene need to be stored in the external frame buffer .

In operation the user of the mobile phone employs the keyboard in order to select a 3D graphic application such as a video game. As an example such graphic application allows to show on the screen several scenes. The scenes correspond to what is visible for an observer who can move assuming different positions. Accordingly a software module corresponding to said graphic application runs on the CPU and active the graphic module .

The applicant observes that after the tiler some primitives submitted to the rasterizer could be totally occluded then each pixel that belongs to the primitives will be occluded too. Hence totally occluded primitives could be usefully rejected without rasterizing them at all.

In a preferred embodiment the pipeline of comprises a further pre processing module positioned between the tiler stage and the rasterizer stage. Such pre processing module comprises a culling module OC arranged to perform a selection or culling operation on occluded primitives exiting the geometry stage . Particularly such culling module is suitable to interact with a further buffer module or hierarchical z buffer HZ buf to efficiently perform such culling operation at best a primitive should pass fail an occlusion test in one clock cycle . In one embodiment the hierarchical z buffer module is maintained up to date with the content of the first depth buffer each time the first depth buffer is updated the hierarchical z buffer is updated as well. In this way the two z buffers and are kept aligned.

Otherwise the hierarchical z buffer module could be updated from time to time relaxing the hypothesis of being every time consistent with the first depth buffer .

As known by those skilled in the art a hierarchical z buffer could be considered as a z buffer pyramid having a full resolution z buffer at the bottom of the pyramid with lower resolution levels piling on top. For example in a hierarchical z buffer the full resolution z buffer can correspond to a tile for example of 64 64 pixels wherein the pixels are grouped in 2 2 or 4 4 blocks. Each lower resolution z buffer represents a sub tile storing the highest z values depth values of each block included in the tile of full resolution level. For example referring to a 16 pixel snapshot of a hierarchical z buffer using 2 2 blocks is schematically displayed. Particularly such hierarchical z buffer comprises a full resolution buffer a middle buffer and a lowest resolution buffer . The middle buffer stores the highest z values from each of the four 2 2 blocks of the full resolution buffer and the lowest resolution buffer stores the highest value from the 2 2 block of the middle buffer . In other words the lowest resolution z buffer represents the 16 pixels from the full resolution buffer .

If the hierarchical z buffer is updated by a new value then such value has to propagate down to each level to maintain coherence. For example if a new primitive has to be rendered somewhere within the 16 pixels of with a z value of 11 then only the lowest resolution buffer needs be checked to establish that all the pixels within this 16 pixel area already have z values that would occlude the new primitive and hence such new primitive can be discarded.

Otherwise if another primitive having a z value of 8 needs to be rendered on these 16 pixels of the visibility or lack of visibility of such primitive is not assured from checking the lowest resolution buffer but the middle buffer has to be checked. On checking the middle buffer it can be established that at least half of this one will definitely be occluded. Therefore the full resolution buffer still needs to be checked. On checking the full resolution buffer it can be seen that only two pixels need be rewritten to and the full resolution z buffer updated with the new z values 8 for these pixels. With reference to as the full resolution z buffer has been updated the new highest values need to propagate up to the following levels and of the hierarchy.

In a preferred embodiment shows by means of a flow chart a graphic method for rendering primitives on a screen. Particularly the graphic rendering method is performed by the graphic module . More particularly such graphic method is performed by the occlusion culling module OC .

In the following it will be assumed that in the pipeline the primitives for example triangles are preferably submitted in a front to back order i.e. starting from the ones having lower depth values z values . Particularly for a triangle the information processed are the z values of its vertexes.

Assuming the screen is divided into tiles each tile of a current scene stored in the first depth buffer can be organized as a hierarchical z buffer in the corresponding hierarchical z buffer module. For example for a tile of 64 64 pixels organized in 2 2 blocks the lower resolution levels 32 32 16 16 8 8 . . . 1 1 are generated by successively selecting the higher z values of each 2 2 block of the upper level. In this way each element of the 32 32 sub tile is mapped on 4 pixels of the 64 64 tile. In other words for each tile the hierarchical z buffer module maps subsequently the points of regions that are gradually more distant from the observer. In other words each level of the hierarchical z buffer can be associated with a region and such regions can be considered belonging regions for the submitted triangles of the scene i.e. regions where the triangles are mapped.

The graphic rendering method provides a first step of calculating CALC DEPTH a depth value d of each primitive submitted. In general the representative depth value d of the primitive is a floating point value ranging between 0.0 and 1.0. This value d is linearly mapped to the hierarchical z buffer resolution rescaling it to the range 0 2 1 where B is the resolution of the z buffer. Usually assuming that the primitive is a triangle a depth value d of the triangle is chosen corresponding to the minimum depth value between the depth values of the triangle s vertexes.

In a further step the method provides for calculating CALC AREA an exact area in pixels in which to perform an occlusion test. In more detail referring to such an exact area is defined as the intersection area between a current drawing area also defined as a scissor area SCISSOR and a bounding box BB that encloses the triangle T having vertexes v v v . In such intersection area is highlighted with shading. If the scissor area is not enabled then the active scissor area corresponds to the entire area of the 64 64 tile . If the intersection area is empty the triangle T is for sure outside of the current drawing area and it could be discarded. Otherwise the intersection area calculated is considered as the exact area to be provided as an input for further steps of the proposed processing method.

A subsequent step of the rendering method comprises providing PROV N a multiplicity of fixed aligned regions for example N regions so that the intersection area is suitable to be entirely covered by the union of such aligned regions which may also extend beyond the intersection area .

The method further comprises a step of performing the occlusion test OT . Particularly such occlusion test comprises a multiplicity of occlusion queries performed by comparing the depth value d of the triangle T with reference data i.e. corresponding depth values v v . . . vN read from the levels of the hierarchical z buffer associated with such multiplicity of N aligned regions.

As indicated above depth values v v . . . vN are assumed to be the maximum depth values of each aligned region used to map the triangle T i.e. the N regions that entirely cover the intersection area . Therefore by executing N occlusion queries if the minimum depth value d of the triangle T the closest vertex is bigger than all maximum values vi with i 1 2 . . . N such triangle T is totally occluded hence it can be discarded at early stage of the pipeline before the rasterizer . Otherwise if some values vi are bigger while others are smaller with respect the minimum depth value d of the triangle such primitive is partially visible. Then it is forwarded to the rasterizer stage and the visibility determination will be solved by the fragment processor stage i.e. at pixel level.

With reference to assuming to use only one region that entirely covers the intersection area for example the region corresponding to the 32 32 level of the hierarchical z buffer the maximum depth value v of such region can fall into a portion of the region that is outside the intersection area itself . Therefore in this case performing an occlusion test would be meaningless.

Otherwise according to the proposed graphic rendering method three aligned regions can be selected that entirely cover the intersection area as indicated in . For example a first region corresponding to the 16 16 level of the hierarchical z buffer and two adjacent second regions corresponding to the 8 8 level. Particularly such first and second regions are of lower hierarchical level with respect the region . In this case three different occlusion queries are performed.

When a triangle pass the test the first depth buffer is updated and the content of the hierarchical z buffer is updated consequently.

Advantageously the occlusion queries OT for all the N aligned regions selected can be performed in parallel.

Advantageously the proposed method ensures that totally visible or partially visible primitives always pass the test and a totally occluded primitive is most of the times rejected.

Advantageously the proposed method is able to increase the number of occluded primitives culled before rasterization compared to current known methods. It means lowering the workload of the rasterizer in particular the triangle setup phase of the rasterizer itself.

The applicant noticed that such method is able to effectively decrease the workload of the rasterizer and fragment processor up to 50 .

In addition the cost in terms of bandwidth due to the introduction into the pipeline of the occlusion culling module is balanced by a relevant reduction of the external bandwidth for the frame buffer and depth buffer .

It should be observed that the graphic module of fully and correctly implements all the specifications of OpenGL ES 1.1. Particularly the method hereby described has been proved to pass all the 1.1 OpenGL ES conformance tests.

Moreover in order to test the performances of module several OpenGL games and applications for example Quake II Quake III TuxRacer etc. have been used as typical inputs. Meaningful results were obtained from the game Quake III.

In this scenario the results obtained in terms of external bandwidth are also relevant the sort middle architecture SMR has a total external bandwidth of 157 Mbytes s while a traditional renderer immediate mode renderer IMR needs 815 Mbytes s as evident in the scheme of .

Table in provides a measure of impact of the proposed occlusion culling method OC assuming different dimensions of screen blocks. The occlusion culling function operates on the basis of primitive screen coordinates. By introducing occlusion culling would eliminate for those occluded geometries the need of both fragment generation and triangle formation.

The table of presents the external bandwidth pointing out the contribution of each stage of pipeline . Two scenarios are analyzed with 30 fps VGA resolution with anti aliasing 4 RGSS and QVGA resolution 320 340 without anti aliasing. IMR refers to immediate mode renderer and SMR refers to sort middle renderer of . Symbol used in indicates that the immediate mode renderer does not comprise the binner and parser functions.

The various embodiments described above can be combined to provide further embodiments. All of the U.S. patents U.S. patent application publications U.S. patent applications foreign patents foreign patent applications and non patent publications referred to in this specification and or listed in the Application Data Sheet are incorporated herein by reference in their entirety. Aspects of the embodiments can be modified if necessary to employ concepts of the various patents applications and publications to provide yet further embodiments.

These and other changes can be made to the embodiments in light of the above detailed description. In general in the following claims the terms used should not be construed to limit the claims to the specific embodiments disclosed in the specification and the claims but should be construed to include all possible embodiments along with the full scope of equivalents to which such claims are entitled. Accordingly the claims are not limited by the disclosure.

