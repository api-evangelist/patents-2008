---

title: Layered texture compression architecture
abstract: Various technologies for a layered texture compression architecture. In one implementation, the layered texture compression architecture may include a texture consumption pipeline. The texture compression pipeline may include a processor, memory devices, and textures compressed at varying ratios of compression. The textures within the pipeline may be compressed at ratios in accordance with characteristics of the devices in the pipeline that contains and processes the textures.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08508543&OS=08508543&RS=08508543
owner: Microsoft Corporation
number: 08508543
owner_city: Redmond
owner_country: US
publication_date: 20080618
---
Texture mapping is a method for adding detail surface texture or color to a computer generated graphic or 3D model. Texture mapping enhances the visual complexity of the 3D objects with a relatively small increase in computational costs. However the raw textures used in texture mapping consume large amounts of memory and storage space. As such compressed i.e. coded textures are typically used in graphics applications specifically real time rendering. Real time rendering applications can compose images from compressed textures.

For example DirectX Texture Compression which may also be known as DXTn DXTC and S3TC is an index based format that has become the dominant texture compression format in the industry. Indexed based formats may organize textures into blocks of data and use commonalities of those blocks to efficiently compress texture data. DXTn typically provides a compression ratio of 8 1 or 4 1 for 32 bits per pixel bpp Alpha Red Green Blue ARGB textures with little loss in visual quality. Other texture compression formats may employ similar index based compression technologies.

Generally texture compression technologies support random addressing. Further there is generally a trade off between random addressing and compression ratios. In particular the compression ratio may depend on the block size used in compression and the block size may have impacts on the random addressing capability.

It is desirable to achieve ever higher rates of compression especially for storage devices because the low bandwidth resources typical of storage devices can impede the high performance requirements of graphics processing. However textures stored with higher rates of compression typically cannot be directly rendered due to limitations in random addressing introduced by the large block sizes of high compression formats.

Described herein are implementations of various technologies for a layered texture compression architecture. In one implementation the layered texture compression architecture may include a texture consumption pipeline. The texture compression pipeline may include a processor memory devices and textures compressed at varying ratios of compression. The textures within the pipeline may be compressed at ratios in accordance with characteristics of the devices in the pipeline that contains and processes the textures.

The processor may be a graphics processing unit GPU configured for processing textures compressed in an index based compression format. The textures compressed in the index based compression format may be stored in a texture cache for processing by the GPU.

The textures may be loaded into the texture cache from a texture or system memory after decoding from an intermediate compression format. The intermediate compression format may facilitate random addressing by the texture system memory. The intermediate compression format may be on top of the index based compression format which facilitates ready decoding and conserves space in the texture system memory.

The textures may be loaded into the texture memory from a peripheral storage after decoding from a storage compression format. With the storage compression format high ratios of compression may be achieved because the peripheral storage does not use random addressing. Additionally the storage compression format may conserve bandwidth used by transferring the texture from the peripheral storage to the texture or system memory. The storage compression format may be on top of the intermediate compression format which facilitates ready decoding.

In another implementation textures may be compressed from the index based compression format into the intermediate compression format. Textures in the index based compression format typically describe textures according to base color information and color indices. In compressing the textures into the intermediate compression format the base color information may be compressed separately from the color indices. Compressing the base color information may include transforming the base color information from a red green blue RGB space to a luminance chrominance space. The base color information may then be transformed according to a Haar or 4 4 integer transformation.

In compressing the color indices the color indices may be re mapped to represent a color level progression between the base colors. The color indices may then be compressed using a sampling of prediction errors generated for the color indices. The prediction errors may be generated with a texel based prediction method.

In another implementation alpha channel information may be compressed into the intermediate compression format from the index based compression format. Alpha channel information may also be described in two component parts general alpha information and alpha indices. The general alpha information may be compressed using the compression methods described above for the base colors. Similarly the alpha index information may be compressed using the above described methods for compressing color index information.

In another implementation textures compressed into the intermediate compression format may be decompressed to the index based compression format through the inverse application of the methods described above.

The above referenced summary section is provided to introduce a selection of concepts in a simplified form that are further described below in the detailed description section. The summary is not intended to identify key features or essential features of the claimed subject matter nor is it intended to be used to limit the scope of the claimed subject matter. Furthermore the claimed subject matter is not limited to implementations that solve any or all disadvantages noted in any part of this disclosure.

As to terminology any of the functions described with reference to the figures can be implemented using software firmware hardware e.g. fixed logic circuitry manual processing or a combination of these implementations. The term logic module component or functionality as used herein generally represents software firmware hardware or a combination of these implementations. For instance in the case of a software implementation the term logic module component or functionality represents program code or declarative content that is configured to perform specified tasks when executed on a processing device or devices e.g. CPU or CPUs . The program code can be stored in one or more computer readable media.

More generally the illustrated separation of logic modules components and functionality into distinct units may reflect an actual physical grouping and allocation of such software firmware and or hardware or may correspond to a conceptual allocation of different tasks performed by a single software program firmware program and or hardware unit. The illustrated logic modules components and functionality can be located at a single site e.g. as implemented by a processing device or can be distributed over plural locations.

The terms machine readable media or the like refers to any kind of medium for retaining information in any form including various kinds of storage devices magnetic optical solid state etc. . The term machine readable media also encompasses transitory forms of representing information including various hardwired and or wireless links for transmitting the information from one point to another.

The techniques described herein are also described in various flowcharts. To facilitate discussion certain operations are described in these flowcharts as constituting distinct steps performed in a certain order. Such implementations are exemplary and non limiting. Certain operations can be grouped together and performed in a single operation and certain operations can be performed in an order that differs from the order employed in the examples set forth in this disclosure.

Typically the texture mapping process uses a texture consumption pipeline through which texture data passes before being consumed in the texture mapping process. illustrates a block diagram of a texture consumption pipeline in accordance with implementations described herein. The texture consumption pipeline may include a peripheral storage a storage format decoder an intermediate storage an intermediate storage decoder a texture cache and a graphics processing unit GPU .

The peripheral storage may be a computer storage such as CD ROM digital versatile disk DVD or other optical storage magnetic cassette magnetic tape magnetic disk storage or other magnetic storage device or any other medium typical of a peripheral storage device that can be used to store the desired information.

The intermediate storage may be a computer storage medium such as a random access memory RAM . The intermediate storage may also be any other storage medium with random addressability that is typical of a system memory or a texture memory that can be used to store the desired information.

The texture cache may be a typical cache device used by the GPU for texture mapping. The proximity and speed of the texture cache may facilitate efficient data retrieval for the GPU .

Typically the GPU may be configured for texture mapping with texture data compressed to a particular standard. For example DirectX Texture Compression DXTC is a compression standard widely supported by graphics hardware. DXTC compresses texture data to one of several DXTn formats e.g. DXT DXT etc. up to DXT. As such the texture cache may contain a DXTn format texture . The DXTn format texture may include texture data formatted to the DXTC standard for texture mapping by the GPU . In one implementation the DXTn format texture may contain color data for a 4 4 block of texels. It should be understood that the DXTn format is merely an example of an index based compression format. The DXTn format texture may contain textures in any index based compression format.

However before being stored in the texture cache as the DXTn format texture texture data may be retrieved from the peripheral storage passing first through the intermediate storage .

For example when the GPU needs a piece of data for the texture mapping the GPU first looks for the data in the DXTn format texture in the texture cache . If the data is not in the texture cache the GPU may look in the intermediate format texture in the intermediate storage . If the data is not in the intermediate storage the GPU or another processor not shown may retrieve the data from the storage format texture in the peripheral storage . The GPU or other processor may then transfer the data retrieved from the peripheral storage to the intermediate storage and the texture cache .

However because the amount of data transferred between storage devices influences the amount of time transferring the data transferring smaller amounts of data i.e. compressed data may be more efficient than transferring larger amounts of data i.e. uncompressed data.

While the DXTn format texture may be compressed it should be noted that the intermediate storage typically provides better performance as the amount of memory used for storage is decreased. However as compression levels increase the ability to access data randomly may be reduced or even eliminated. Accordingly an intermediate format texture may be stored on the intermediate storage . The intermediate format texture may be a more highly compressed version of the DXTn format texture . Additionally the intermediate format texture may be compressed or coded on top of the DXTn format texture . It should be noted that the terms compressed and coded may be used interchangeably herein

By coding the intermediate format texture on top of the DXTn format texture the intermediate format texture may be readily decoded into the DXTn format texture . Formatting the intermediate format texture for ready decoding into the DXTn format texture may ensure that the performance gain of reduced storage on the intermediate storage is not negated by the time used to decode the intermediate format texture . In one implementation the intermediate format texture may be of fixed length.

The intermediate format decoder may decode the intermediate format texture to the DXTn format texture and load the DXTn format texture into the texture cache . The intermediate format decoder is described in greater detail with reference to .

While the intermediate format texture may also be compressed bandwidth between the peripheral storage and the intermediate storage may make transferring the intermediate format texture out of the peripheral storage a bottleneck for the texture mapping process. Because the peripheral device typically does not use random addressability to access data a higher compression ratio may be used for data stored in the peripheral storage . As such the peripheral storage may store a storage format texture which may be a more compressed version of the intermediate format texture .

Because the storage format texture is more compressed than the intermediate format texture the storage format texture may be transferred to the intermediate storage more efficiently than the intermediate format texture and the DXTn format texture . The storage format texture may be coded on top of the intermediate format texture which may facilitate ready decoding into the intermediate format texture .

The storage format decoder may be hardware or software that decompresses the storage format texture into the intermediate format texture then loads the intermediate format texture into the intermediate storage . The storage format decoder is described in greater detail with reference to .

As stated the storage format texture may be the source of texture data passing through the texture consumption pipeline . However because the storage format texture may be compressed on top of the intermediate format texture which is compressed on top of the DXTn format the DXTn format texture may be the source for a compression method that produces the intermediate format texture and in turn the storage format texture .

While the storage format texture may serve as the input to the texture consumption pipeline DXTn format textures may serve as the input to method .

The DXTn format textures may represent a collection of DXTn format textures . As such the DXTn format textures may be arranged in blocks also referred to herein as macro blocks of DXTn format textures . In one implementation the macro block may contain a 4 4 block of DXTn format textures . In a scenario where the DXTn format texture may contain color data for a 4 4 block of texels the macro block may contain color data for a 16 16 block of texels. Of course the block sizes noted here are examples. The actual size of the macro block or individual DXTn format textures may vary in implementations described herein.

DXTn format textures may be input to an intermediate format coding process . The intermediate format coding process may compress DXTn format textures into intermediate format textures . As such the intermediate format coding process may perform the complement of the decoding process performed by the intermediate format decoder . The intermediate format coding process is described in greater detail with reference to .

The intermediate format textures may represent a collection of intermediate format textures . As such the intermediate format coding process may represent the complement of the process performed by the intermediate format decoder .

The intermediate format textures may contain all the compressed macro blocks of the DXTn format textures . To facilitate decoding the intermediate format textures the length of each compressed macro block may be fixed within the intermediate format textures .

The intermediate format textures may be input to a storage format coding process . The storage format coding process may compress the intermediate format textures to storage format textures . As such the storage format coding process may represent the complement of the process performed by the storage format decoder . In one implementation the storage format coding process may use arithmetic entropy coding.

Index based compression technologies such as DXTn typically describe textures in terms of base colors and color indices. In one implementation the base colors may represent 2 color levels referred to herein as C and C. The base colors may represent a range of colors that includes the color levels of all the texels within one DXTn format texture .

Typically a color index for each texel may be included in the DXTn format textures . The color indices may identify a color level for each texel that is within the base color range.

Method for intermediate format coding may compress DXTn format textures by separately compressing the base color data and the color index data in the DXTn format textures . Method may be repeated for each macro block in the DXTn format textures .

The base color coding may be performed in two modes a gray mode and a non gray mode. As such steps may be repeated for each base color coding mode.

At step the base colors may be coded according to the base color coding mode. Gray mode coding may be a lossless compression process for gray and near gray DXTn format textures . Gray mode coding is described in greater detail with reference to . Non gray mode coding may be a lossy compression process for colorized DXTn format textures . Non gray mode coding is described in greater detail with reference to .

Because the intermediate format textures may be of fixed length the color index coding may be constrained to fit the compressed color indices within the bits remaining in the fixed length format after the base color coding. As such at step the number of bits remaining in the fixed length format after the base color coding may be determined.

It should be noted that the base colors and color indices may be further compressed after the respective base color and color index coding. It is this further compression that is used to fit the compressed base colors and color indices into the fixed length format of the intermediate format textures . In one implementation variable length entropy coding may be applied to the base color and color index coding to produce the intermediate format textures . As such an entropy coder may be used to determine the number of bits occupied by the base colors after the base color coding. Accordingly the number of remaining bits for the compressed color indices may be determined based on the length of the fixed length format and the number of bits occupied by the compressed base colors.

Color index coding may employ texel based prediction methods whereby color index values are predicted for each texel. Coding predicted color index values instead of the actual color index values may facilitate ready decoding by the intermediate format decoder . Color index coding is described in greater detail with reference to .

At step color index coding by median texel based prediction may be performed. The median texel based prediction method may predict color index values for each texel based on the color index values of neighboring texels. Median texel based prediction is described in greater detail with reference to .

At step color index coding by directional texel based prediction may be performed. The directional texel based prediction method may predict color index values for each texel based on directional patterns of color levels in neighboring texels. Directional texel based prediction is described in greater detail with reference to .

At step the color index coding with the prediction method that produces the lowest color level sum of absolute difference SAD may be selected. As such each base color coding gray mode and non gray mode may be paired with a color index coding.

Because the actual color indices are not coded into the intermediate format textures the color indices produced by decoding the intermediate format textures may be different than the color indices represented in the DXTn format textures . In this manner the color levels represented by the respective color indices may also differ. However the difference between the coded and decoded color levels may be attenuated by selecting the compressed color indices produced by the color index coding method that produces the smaller difference between coded and decoded color levels.

At step the base color color index coding pair that produces the lowest color level SAD may be selected for compression into the intermediate format textures .

At step the selected base color color index coding pair may be further coded with variable length entropy coding. The variable length entropy coding is described in greater detail with reference to .

Because the intermediate format textures may be a fixed length at step the compressed base colors and color indices produced at step may be padded to the fixed length with stuffing bits.

At step the R component values and the prediction errors for the G and B component values may be converted to high and low pass signals with a Haar transform. The Haar transform facilitates compression by de correlating spatial relationships between the component color values. For each component the following calculations may be used in the Haar transform High pass signal 0 1 Low pass signal 1 1 1.

More specifically the C and C referenced in the above formulas may be the values of the R G and B components of the base colors. The Haar transform may be individually applied to each component.

At step a 4 4 integer transform may be used to perform spatial transformation on the predicted Y UV components of the base colors. The 4 4 integer transform may produce 4 4 coefficients for each of the Y UV components for the macro block.

The 4 4 integer transform may be performed to achieve coefficient energy compaction similar to traditional direct cosine transform DCT . Advantageously the 4 4 integer transform merely involves integer arithmetical operations without loss of accuracy unlike traditional DCT. One typical 4 4 integer transform may be expressed as follows .

where X denotes an input 4 4 matrix Y denotes an output 4 4 matrix that contains the transformed coefficients and Mis the transpose of the matrix M. In one implementation the matrix M may be as follows 

At step the coefficients produced from the 4 4 integer transform may be quantized. Quantization typically employs a divisor before rounding the divided coefficient value to an integer value.

QP may represent a value that is varied to produce multiple quantizations for a particular 4 4 integer transform. The multiple quantizations may be produced in order to find a quantization that facilitates jointly optimizing the base color and color index coding. As such step may be repeated for each QP value.

In one implementation the QStep calculation may be replaced by a look up table indexed by QP values. The look up table may incorporate a post scaling factor that makes the 4 4 integer transform orthogonal.

In one implementation the DXTn format textures may include DXT format textures. It should be noted that alpha channel information may be included in DXT format textures. Alpha channel information may denote the transparency opaqueness of the texels in the DXT format texture. Specifically the DXT format texture may include two 8 bit main alpha values. In such an implementation the two 8 bit main alpha values may also be coded according to the steps described above in methods and .

Typically texel based prediction assumes a progressive representation of color levels in the color index values. In other words as the color index value increases the color levels represented by the associated color indices increase or progress from base color C to base color C. However the color levels represented by the color indices in the DXTn format textures may not be progressive representations of color levels.

As shown color level progression may proceed as follows C C C and C. However in typical DXTC the color index values may proceed as follows 0 2 3 and 1. In this manner the index values may not be progressive representations of color levels. As such at step the color indices for each texel may be re mapped to progressively represent color levels.

Accordingly all texels with a color index value of 2 may be re mapped to a color index value of 1.Similarly all texels with a color index value of 3 may be re mapped to a color index value of 2 etc. illustrates a correspondence between re mapped color index values and color level progression according to implementations described herein.

Referring back to at step the texel based prediction method may be queried to determine whether the method is employing directional prediction or median prediction. If directional prediction is employed at step a prediction direction may be estimated.

In directional prediction the color index prediction for each texel may be based on a direction of color level patterns within the macro block. As such the directional prediction incurs an overhead cost to record the direction used for directional prediction in the compressed color indices. In one implementation one direction prediction may be used for the entire macro block. However by limiting the entire macro block to one direction prediction accuracy may be compromised. Accordingly in another implementation the overhead may be limited by adjusting the block size of the macro block in balance with prediction accuracy. In this manner the prediction direction may be estimated based on an adaptively sized macro block whereby the size of the macro block may be determined based on an optimal balance of overhead and prediction accuracy.

At step the color indices for all texels within the macro block may be predicted according to median or directional texel based prediction. As stated in median texel based prediction the color index for a texel may be predicted based on the color index of neighboring texels.

In this example a and b may be the color indices of texels a and b respectively. In a scenario where texels a or b are not within the boundaries of the macro block a default value such as 0 may be substituted for their respective color indices.

Referring back to directional texel based prediction may be alternately employed at step . The directional texel based prediction may be based on the prediction direction that is estimated at step . There are four possible prediction directions direct current DC left up and up left.

Referring back to at step the prediction errors of the predicted color indices may be sampled. The sampling may determine whether coded prediction errors are included in the compressed color indices. In this manner each texel s prediction error may be designated as a skipped or refreshed. Refreshed prediction errors may be included in the compressed color indices skipped prediction errors may not. The designation may facilitate decoding the intermediate format texture . The prediction errors for each texel may be the difference between the predicted color index and the re mapped color index as determined at step . Sampling is described in greater detail with reference to .

In the implementation where the DXTn format textures include DXT format textures the DXT format textures may include 3 bit alpha indices for each texel.

In another implementation the DXTn format textures may include DXT format textures. Typically DXT format textures may include 4 bit alpha indices for each texel. In such implementations the alpha indices may also be coded according to the steps described above for the method .

In one implementation a threshold value may be varied to control a rate of compression. A low threshold value may produce a low rate of compression and a high threshold value may produce a high rate of compression. As such steps may be repeated by varying the threshold value to vary the rate of compression for the color indices. Sampling for each threshold value may be performed by repeating steps for each texel.

At step a color level distortion may be determined. The color level distortion may be the difference between the color level associated with the texel s re mapped color index and the color level for the texel s predicted color index.

At step the color level distortion may be compared to the threshold value. If the color level distortion is greater than the threshold value at step the prediction error for the color index may be sampled for coding. If the color level distortion is not greater than the threshold value at step the prediction error for the color index may be skipped for coding.

In one implementation the DXTn format texture may be a DXT format texture. Typically DXT format textures include an alpha channel that is based on the color levels of the base colors C and C. The alpha channel may denote whether a texel is transparent or opaque. For example if the actual color index for a texel is not 3 the texel may be opaque. However if the actual color index for a texel is 3 the color levels of the base colors C and C may be compared. If the color level of C is less than the color level of C the texels with a color index of 3 may be transparent otherwise the texels may be opaque.

In lossy index compression obvious visual artifacts may be introduced in a texture if a transparent texel is changed to opaque or vice versa. As such the sampling step at may include a second test that may ensure that prediction errors are sampled in cases where a skipped prediction error may introduce a change in the alpha channel. In other words if the predicted color index changes the alpha channel from that represented by the actual color index the prediction error may be sampled for coding.

After all the texels have been evaluated for sampling at step the number of bits used for compressing the sampled color indices may be determined. In one implementation an entropy coder may determine the number of bits used for the compression.

At step the number of bits used for compressing the color indices may be compared to the number of remaining bits after base color coding. If the number of bits used by color index compression is greater than the number of remaining bits the threshold value may be increased and method may be repeated. In this manner the color index coding may be produced such that the color index coding for each macro block fits within the fixed length of the intermediate format textures .

In the implementations where the DXTn format textures may include DXT and DXT textures method may be used for alpha index coding. As such the bits used for both color index and alpha index coding may need to fit within the remaining bits. In one implementation the allocation of color index coding and alpha index coding bits may be determined by jointly minimizing the SAD for both color index and alpha index coding according to the following formula min min 

In the above formula SADmay denote the joint sum of absolute difference. SADmay denote the SAD between the uncoded and decoded color levels associated with the color indices. SADmay denote the difference between the uncoded and decoded alpha channel. c may be a constant that favors minimizing SADover SADbecause distortions in the alpha channel incur a heavier visual impact in the decoded textures than distortions in the RGB channels.

At step a bit for the base color coding mode may be written to the bit stream. The bit may indicate gray mode or non gray mode base color coding.

At step the base color coding mode may be queried to determine whether the macro block is compressed using gray mode. If so at step steps may be repeated for each of the high and low pass values for each of the R G and B component of the base colors.

At step a zero non zero bit may be written. The zero non zero bit may indicate whether the high low pass value is a zero value. At step non zero values may be written using variable length Exp Golomb code representations.

If the base color coding mode is non gray mode at step the QP determined during base color coding may be written using 6 bits. Steps may be repeated for each of the Y U and V components of the base colors.

At step the quantized coefficients of the Y U V components may be written using run length coding representations.

At step a prediction bit may be written. The prediction bit may indicate whether the texel based prediction method used in color index coding is directional or median prediction.

At step if the texel based prediction method used in color index coding is not directional prediction method may proceed to step .

If the texel based prediction method used in color index coding is directional prediction method may proceed to step . At step a multi directional bit may be written. The multi directional bit may indicate whether the same direction is used for directional prediction for the entire macro block.

At step if the same direction is used for directional prediction for the entire macro block method proceeds to step . At step direction bits may be written. The direction bits may indicate the direction used for the directional prediction.

If the same direction is not used for directional prediction for the entire macro block method proceeds to step . At step direction bits may be written for each direction used for the directional predictions.

At step base color and color index information may be decoded from the intermediate format texture with a variable length entropy decoder. The variable length entropy decoder may determine for the base colors the base color coding mode the high and low pass signals of the base color components the quantized coefficients of the transformed base color components and the Quantization Parameter QP .

The variable length entropy decoder may determine for the color indices the color index prediction method and the run length coded prediction errors for each texel in the intermediate format texture .

At step the base color information may be further decoded based on the base color coding mode. In the case of gray mode coded base colors an inverse Haar transform may be performed to determine the each of the RGB base color components as follows 1 1 1 0 1

In the case of non gray mode coded base colors the quantized coefficients may be dequantized using the QP. An inverse 4 4 integer Transform may be performed on the dequantized coefficients to determine each of the Y UV base color components. Additionally the determined Y UV base color components may be converted back to RGB values using the following formulas clip 298 409 128 8 clip 298 100 208 128 8 clip 298 516 128 8 wherein clip means that the calculated value may be constrained within the rang 0 to 255.

At step the color index information may be decoded using a run length decoder. The run length decoder may produce the sampled prediction errors for each texel in the intermediate format texture .

At step the original color indices for the texels may be determined from the sampled prediction errors based on the prediction method used to code the color indices. Color indices may be predicted based on the median or directional prediction method used to compress the color index information. The predicted color indices may then be modified by the sampled prediction errors. The original index representation may then be determined by re mapping the modified color indices from a color level progression representation to an original index representation.

At step the alpha channel information may be decoded based on the coding mode and prediction method used to code the alpha channel. The decoding of the alpha channel may be the same decoding that is described above in steps .

At step the base color color index and alpha channel information determined in the steps described above may be formatted into an appropriate DXTn format to generate the DXTn format texture .

The processing environment may include various volatile and non volatile memory such as a RAM and read only memory ROM as well as one or more central processing units CPUs . The processing environment may also include one or more GPUs . The GPU may include a texture cache . Image processing tasks can be shared between the CPU and GPU . In the context of the present disclosure any of the decoding functions of the system described in may be allocated in any manner between the CPU and the GPU . Similarly any of the coding functions of the method described in may be allocated in any manner between the CPU and the GPU .

The processing environment may also include various media devices such as a hard disk module an optical disk module and the like. For instance one or more of the media devices can store the DXTn format textures the intermediate format textures and the storage format textures on a disc.

The processing environment may also include an input output module for receiving various inputs from the user via input devices and for providing various outputs to the user via output device . The processing environment may also include one or more network interfaces for exchanging data with other devices via one or more communication conduits e.g. networks . One or more communication buses may communicatively couple the above described components together.

It should be understood that the various technologies described herein may be implemented in connection with hardware software or a combination of both. Thus various technologies or certain aspects or portions thereof may take the form of program code i.e. instructions embodied in tangible media such as floppy diskettes CD ROMs hard drives or any other machine readable storage medium wherein when the program code is loaded into and executed by a machine such as a computer the machine becomes an apparatus for practicing the various technologies. In the case of program code execution on programmable computers the computing device may include a processor a storage medium readable by the processor including volatile and non volatile memory and or storage elements at least one input device and at least one output device. One or more programs that may implement or utilize the various technologies described herein may use an application programming interface API reusable controls and the like. Such programs may be implemented in a high level procedural or object oriented programming language to communicate with a computer system. However the program s may be implemented in assembly or machine language if desired. In any case the language may be a compiled or interpreted language and combined with hardware implementations.

Although the subject matter has been described in language specific to structural features and or methodological acts it is to be understood that the subject matter defined in the appended claims is not necessarily limited to the specific features or acts described above. Rather the specific features and acts described above are disclosed as example forms of implementing the claims.

