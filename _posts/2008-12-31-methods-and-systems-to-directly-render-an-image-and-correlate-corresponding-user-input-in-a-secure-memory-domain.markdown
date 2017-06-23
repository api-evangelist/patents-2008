---

title: Methods and systems to directly render an image and correlate corresponding user input in a secure memory domain
abstract: Methods and systems to assign an application and a video frame buffer to a protected memory domain to render an image of a keyboard from the protected memory domain to a random position of the video frame buffer and correlate user input from a pointing device to the rendered keyboard image. The keyboard image may be randomly repositioned following a user input. The keyboard image may be rendered over a secure user image. An acknowledgment image may be rendered from the protected memory domain to a random position of the video frame buffer, and may be randomly repositioned in response to a user input that does not correlate to the acknowledgment image. User inputs that do not correlate to a randomly positioned image may be counted, and one or more processes may be aborted when the number of non-correlated user inputs exceeds a threshold.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08364601&OS=08364601&RS=08364601
owner: Intel Corporation
number: 08364601
owner_city: Santa Clara
owner_country: US
publication_date: 20081231
---
When confidential user information such as electronic payment transaction information is input to a computer system through a mechanical keyboard or pointing device the information may be vulnerable to malware such as spyware which may record keystrokes or input coordinates as they are transmitted to or within the computer system.

An application program associated with receiving of confidential user information may also be vulnerable to malware such as spyware.

In the drawings the leftmost digit s of a reference number identifies the drawing in which the reference number first appears.

At an access protected memory domain is configured within a computer system. Access to the protected memory domain is restricted in accordance with one or more rules to substantially insure that data and instructions within the protected memory domain are inaccessible to processes outside of the protected memory domain. The protected memory domain may include one or more portions of system memory graphics memory and combinations thereof. The protected memory domain may be configured and enforced under control of software hardware and combinations thereof including virtual machine management technology.

At an application is initiated in the protected memory domain. The application may include instructions to cause a processor of the computer system to render a data entry image such as a keyboard image and to correlate subsequent user input with the image in the protected memory domain.

The application may authenticated prior to initiation using software hardware and combinations thereof and may be authenticated in accordance with one or more hashing techniques including code signature hashing techniques which may include a trusted execution technology.

The application may be loaded into the secure memory domain and authenticated in the secure memory domain. Alternatively or additionally the application or a portion thereof may be loaded into another secure memory domain such as access protected firmware associated with a trusted execution technology module.

The protected memory domain and the authenticating of the application alone or in combination with one another may protect the application including code control flow and data structures associated with the application from malicious code including spyware even when a corresponding operating system under which the application is launched is compromised such as by a rootkit virus worm or spyware.

Configuring of the protected memory domain at and or loading authenticating and initiating of the application at may be performed under control of a hypervisor based security visor that protects in memory components from snooping and modification by malicious code.

The hypervisor based security visor may be configured to identify code and or data to measure one or more features associated with the code and or data for authenticity and to protect authenticated code and or data.

The hypervisor based security visor may be configured to operate without modification to an operating system.

The hypervisor based security visor may include an integrity measurement module IMM to run in a protected space outside a boundary of an operating system and thus outside bounds of potential malware in the operating environment. IMM protected space may include protected hardware and or a protected virtual machine VM running above a virtual machine manager VMM . The IMM may be configured to verify an identity and integrity of code of the application against a signature file containing a hash of sections of the code such as a SHA 1 hash and to verify entry points into the code sections and a corresponding relocation table.

The hypervisor based security visor may include a memory protection module MPM to enforce memory access protections and the IMM may be configured to signal the MPM to enforce the memory access protections after the IMM has successfully identified and measured the application.

The MPM may be configured to create one or more protected page tables PPTs and to map the protected code of the application and corresponding data pages to the PPTs and to sever corresponding mapping from active page tables APTs . A memory manager such as a VMM may be configured to manage a list of virtual address range of protected memory and the corresponding physical addresses of protected pages. Upon a page fault the VMM may be configured to compare the virtual address of a destination page with the list of protected page addresses and when a match is found to switch a page table base register PTBR in a virtual machine control structure VMCS to the address of the PPT base address. On return the VMM may be configured to switch the PTBR from the PPT address to the APT base. The VMM may check the list of physical page addresses each time the VMM attempts to add a page to the APTs. When the VMM finds a protected page the VMM may decline to add the protected page to the APT and may generate an error indication. When the memory protections are configured an initialization vector associated with the application may be the first code section to execute within the protected application domain.

The hypervisor based security visor may include a VT Integrity Services for Networking VISN system developed my Intel Corporation.

The application may be configured to pull a video frame buffer corresponding to a graphics adapter into the protected memory domain and to directly render to the video frame buffer. One or more video frame back buffers and or other surfaces may also be assigned to the protected memory domain. While in the protected memory domain the video frame buffer including any back buffers and other surfaces may be substantially protected from write and or read processes initiated by the operating system and other processes outside of the protected memory domain. Correspondingly the video frame buffer including any back buffers and other surfaces may be substantially immune to malware running on the computer system regardless of a privilege level of the malware.

The application may be configured to identify or determine a memory address corresponding to a primary or video frame front buffer and one or more video frame back buffers to remove corresponding pages from APTs associated with an operating system OS and to place the pages in PPTs along with the protected parts of the application and other protected code and data pages. As a result screen scraping applications malware may be precluded from reading from and writing to the protected pages.

The application may be configured to perform direct graphics rendering such as that provided by DirectX and OpenGL in Microsoft Windows and OpenGL in Linux OS. Corresponding libraries may be accessed to find address corresponding to the video frame buffer and to remove read and write restrictions that may exist with respect to applications running under the OS.

The initiation of the application in the protected memory domain at may include protecting at least code and data sections for the code that are responsible for writing to and or reading from the video frame buffer.

Assigning the video frame buffer to the protected memory domain at may include identifying a location of a pointer to the video frame buffer or an APT translation corresponding to the pointer.

Locating a pointer to the video frame buffer may include using an application programming interface API associated with an operating system to determine a virtual address of the pointer. A corresponding physical address may be identified from a page table maintained by an operating system or VMM.

Locating a pointer to the video frame buffer may include obtaining a physical address of the pointer and walking through the corresponding process address space such as a page table to find the physical address and the corresponding virtual address. The physical address of the pointer may be mapped to a known physical address such as address 0XA000. This may include a hypercall for each step.

The virtual address and corresponding physical address may be pulled into one or more PPTs. The pulling of the video frame buffer into the PPTs may include marking the corresponding memory pages as not present in the APTs and marking the memory pages as read write in the PPTs.

At an image of a user input device is rendered to the video frame buffer. The image may include an image of a keyboard which may include one or more of an image of a numeric keyboard an alphabetical keyboard and an alpha numeric keyboard.

The image of the user input device may be loaded and authenticated in the protected memory domain as part of the loading of the application at .

A graphics adaptor may be configured to render from one or more of memory within the graphics adaptor video RAM VRAM in the case discrete graphics adaptors shared system memory system RAM and in the case of an embedded graphics adaptor may be configured share system RAM with a general purpose processor or a combination thereof such with an advance graphics aperture AGP .

A graphics card may be configured to normally use local VRAM and to use system RAM when the local VRAM is insufficient for processes running on the system. A graphics card may render from one or more primary video frame buffers. Content of the video frame back buffers may be blitted to a primary buffer or an application may declare a chain of back buffers and flip the back buffers to the primary buffer in a chain.

For secure input and output a ring 3 application may declare multiple surfaces which may include texture when rendering the keyboard.

At user input is received in the protected memory domain subsequent to the rendering of the input display image. The user input may include a positional indication which may be generated by one or more of a pointing device a cursor device such as a mouse device a touch pad and a touch screen display.

At the user input is correlated with a feature of the input display image. The correlating may include correlating coordinates of the user input with a key of a rendered keyboard image to identify a user selected key of the keyboard.

At an indication of the image feature that correlates to the user input is stored in the protected memory domain. Where the image includes a keyboard image the storing may include storing an indication of a user selected key.

At the stored indication of the user input may be output from the protected memory domain and the video frame buffer may be released from the protected memory.

Method may be invoked to receive confidential user input such as electronic payment information. is a process flowchart of an exemplary method of invoking method to conduct a payment transaction over a network connection.

At a communication session is conducted over a network between a user computer system and another computer system which may be remote relative to the user computer system. The communication session may for example be conducted through a web browser running on the user computer system with a merchant web site or a financial card processor web site over the Internet.

At a prompt for user information received from the remote computer system and detected at the user computer system.

Detecting of the prompt at may include detecting a prompt for electronic payment information such as credit card information debit card information or other payment authorization information.

Detecting of the prompt at may include detecting one or more standardized payment prompts such as an industry standard hypertext mark up language HTML credit card form.

Detecting of the prompt at may include searching incoming web pages for data entry fields that are common to credit card payment transactions such as credit card number fields date fields and monetary denomination fields.

The prompt may be detected by an application running on the user computer system such as a web browser. Computer readable instructions to detect a prompt may be implemented as a browser plug in to work with a browser application and may be implemented relatively seamlessly with little or no modification to a merchant website or a financial card processor web site.

Detecting of the prompt may include intercepting a secure sockets layer SSL channel or transport layer security TLS channel between a browser running on a user computer system and a merchant web site or a financial card processor web site.

At an application is invoked in response to a detected prompt for user information. Invoking of the application at may include performing method or a portion thereof and may include obtaining credit card information and payment authorization from a user in the protected memory domain.

At the prompt is populated with user input data from the protected memory domain and is returned to the requestor.

Returning to rendering at may include rendering the input display image to a relatively random or pseudo random position and may include re rendering the image to another random position following a user input. The random positioning may include one or more of true random positioning pseudo random positioning and positioning to one of a plurality of pre determined positions. Random positioning may help to reduce an ability of spyware or other malicious code to correlate user input with the rendered image.

At a keyboard image is rendered to a random position of the video frame buffer. The keyboard image may have a size that is smaller than a size of the video frame buffer to allow rendering to multiple random positions within the video frame buffer.

At coordinates of the user input are correlated with the rendered keyboard image and corresponding indications of user selected keys are stored in the protected memory such as described above with respect to and in .

At when the user is to provide additional input the keyboard image is re rendered at to another random position in the video frame buffer. The receiving of user input at and the correlating and storing at may be repeated until user data input is complete. The keyboard image may be re rendered to another random position following each user input. For example where the user is to input a multi digit sequence the keyboard image may be re rendered to another random position following each digit entry.

The keyboard image may include an image of a user data entry complete key to permit a user to indicate that data entry is complete.

When user data input is complete at the stored indications of user selected keys may be output from the protected memory domain and the video frame buffer may be released from the protected memory domain at .

Referring back to rendering of the input display image at may include rendering the input display image over a user image. The user image may be selected by the user and associated with the application in advance as a security measure. is a process flowchart of an exemplary method of rendering an input display image over a user image.

At an application is initiated in the protected memory domain such as described above with reference to in .

At a user image or bitmap is loaded into the protected memory domain. The user image may be retrieved as an encrypted user image from a storage device such as a hard drive. The encrypted user image may be loaded and decrypted in the protected memory domain.

Decryption may be performed under control of the application initiated at and a decryption key may be provided to the application by a security visor module upon authentication or validation of code and or static data sections of the application.

At a video frame front buffer and first and second video frame back buffers are assigned to the protected memory domain.

At a keyboard image is rendered to a random position of the first video frame back buffer such as described above with respect to in .

At the user image is rendered to the second video frame back buffer at a position corresponding to the random position of the keyboard image in first video frame back buffer. The user image may have a size that is larger than the size of the keyboard image and smaller than a size of the video frame front buffer.

At the first and second video frame back buffers are merged to the video frame front buffer. The merging may include overlaying a portion of user image with the keyboard image. The merging may be performed as a bit block transfer BitBlt or block image transfer Blit in which multiple bit maps are combined using a rastering operation.

At coordinates of the user input are correlated with the rendered keyboard image and stored in the protected memory such as described above with respect to and in .

At when the user is to provide additional input the keyboard image and the user image are re rendered at to another random position in the corresponding first and second video frame back buffers.

The merging at the receiving of user input at and the correlating and storing at may be repeated until user data entry is complete. The keyboard image and the user image may be re rendered to another random position following each user input.

When user data input is complete at the stored indications of user selected keys may be output from the protected memory domain and the video frame buffer may be released from the protected memory domain at .

When user data entry is complete an acknowledgment image may be rendered to a random position to permit a user to complete a corresponding transaction.

At an acknowledgment image is rendered to a video frame buffer in a protected memory domain. The acknowledgment image may be rendered over a user image such as described above with respect to .

At where the coordinates of the user input correlate to the acknowledgment image corresponding user input data such as indications of user selected keys may be output from the protected memory domain and the video frame buffer may be released from the protected memory domain at .

Where the coordinates of the user input do not correlate to the acknowledgment image at one or more actions may occur. For example the acknowledgement image may include one or more of a cancel transaction image and an edit data image to permit a user to elect to cancel the transaction or edit the transaction.

One or more methods described above may include counting user inputs that do not correlate to a rendered image and aborting a transaction when the number of non correlated inputs exceeds a threshold. This may help to thwart click everywhere attacks.

At an image is rendered to a random position of a video frame buffer. The image may include one or more of an input display image an acknowledgement image and a user image.

Where the user input correlates to the rendered image at processing proceeds to where the user input is processed in accordance with the correlation. This may include one or more of correlating at in correlating at in correlating at in and correlating at in .

Where the user input does not correlate to the rendered image processing proceeds to where an error count is incremented.

At when the error count is below a threshold the image may be re rendered to another random position at and processing may return to to receive another user input.

When the error count is above the threshold at one or more processes may be halted or terminated at . This may include one or more of terminating a corresponding network connection excising contents of the video frame buffer and or previously entered user data sending an alert or report to an administrator and terminating the application.

At an encrypted or otherwise protected user image is loaded and decrypted in a secure memory domain. The secure memory domain may be configured using one or more protected page tables. The user image may be similar to a site key.

At a keyboard image is rendered on top of the user image to a random location on a secure display screen. The keyboard image may be blitted on top of the user image. The combination of the keyboard image and the underlying user are referred to herein as a secure input screen.

At when a user clicks over the keyboard image a corresponding keystroke is recorded and displayed in an output area on the secure display screen and the secure input image is randomly relocated to another position. This may protect against guessing attacks from an attacker.

The user may enter a credit card bank card number through the secure input screen. Alternatively or additionally the user may enter a personal identification number PIN to access a secure value of information such as a credit card number. The secret value may be secured with an access key such as described above with respect to an encrypted user image. The access key may be secured as a security visor secret platform key to be revealed to an authenticated application. The application may be configured to use the PIN to unlock the secret value. This may reduce the amount of data to be entered by a user and may increase security of a transaction.

At upon completion of user data entry an acknowledgment image is rendered to the secure display screen to prompt the user to acknowledge the transaction parameters. The acknowledgment image may be rendered over the user image as described above. The combination of the acknowledgment image and the underlying user image are referred to herein as a secure acknowledgment screen.

The secure acknowledgement screen may be viewed as another surface in the protected memory domain which is rendered when the user has completed entry of credential and transaction information. The secure acknowledgement screen may include transaction information such as a merchant name monetary value of the transaction date and credentials to be sent to the merchant or card processor site. The secure acknowledgement screen may include one or more lines to display information.

At when the user clicks over the acknowledgement image the previously entered keystrokes or other corresponding user information may be output from the secure memory domain. The keystrokes or other user information may be output to a merchant network site or credit card processor network site.

The keystrokes or other user information may be encrypted and signed prior to outputting. The transaction information may be encrypted such as with a public key of the merchant or card processor and may be signed with a private key of the user. A hashing function may be applied to one or more of a monetary value of the transaction a credit card number entered by the user a transaction count and merchant information to generate a secure transaction value. The secure transaction value may be sent to the merchant or card processor.

The merchant or card processing network site may be authenticated at the user computer such as by a certificate. This may help to thwart phishing attacks.

The acknowledgement image may be randomly positioned and may be randomly repositioned following a user click that does not correlate to the acknowledgment image. This may preclude an attacker from determining a location of the acknowledgement image from an analysis of previous clicks. The transaction may be aborted when a number of uncorrelated user clicks exceed a threshold number. This may help to thwart brute force click everywhere attacks.

One or more features disclosed herein may be implemented in hardware software firmware and combinations thereof including discrete and integrated circuit logic application specific integrated circuit ASIC logic and microcontrollers and may be implemented as part of a domain specific integrated circuit package or a combination of integrated circuit packages. The term software as used herein refers to a computer program product including a computer readable medium having computer program logic stored therein to cause a computer system to perform one or more features and or combinations of features disclosed herein.

Computer system includes memory which may include one or more of video memory or VRAM and physical system memory or random access memory RAM which may include advanced graphics processing AGP aperture memory . AGP aperture memory may be used by GPU in addition to VRAM .

Memory may include a computer readable medium having computer program product logic or instructions stored thereon to cause one or more of processor and GPU to perform one or more functions in response thereto.

Physical addresses of memory or portions thereof may be virtualized with respect to one or more operating environments and applications. Memory mappings between virtual to physical memory addresses may be maintained in one or more active page tables APTs .

One or more access protected memory domains may be configured within memory and corresponding memory address mappings may be maintained in one or more protected page tables PPTs .

APTs and PPTs may be configured and enforced within a security visor environment under control of an access control manager .

Protected memory domain includes application logic which may be authenticated such as described above with respect to in .

Application logic may include video frame buffer identify and protect logic to cause processor identify a location or address mapping corresponding to a video frame buffer or of a pointer to the video frame buffer and to access protect the video frame buffer such as described above with respect to in . In the example of a video frame buffer is illustrated within protected memory domain . Video frame buffer may include one or more back buffers through and a primary or front buffer .

Application logic may include user image decrypt logic to cause processor to retrieve an encrypted user image into protected memory domain and to decrypt the user image such as described above with respect to in . In the example of a decrypted user image is illustrated within protected memory domain .

Application logic may include random render logic to cause processor to render an input display image to a random position of video frame buffer such as described above with respect to . Random render logic may include logic to cause processor to render input display image and decrypted user image to a random position in back buffers and respectively and to merge or blit the images from back buffers and to front buffer such as described above with respect to .

Random render logic may include logic to cause processor to render an acknowledgment image to a random position of video frame buffer such as described above with respect to in . Random render logic may include logic to cause processor to render acknowledgment image and decrypted user image to a random position in back buffers and respectively and to merge or blit the images from back buffers and to front buffer such as described above with respect to .

Application logic may include correlate logic to cause processor to correlate user input with rendered images and to store corresponding user input in protected memory domain as user input data such as described above with respect to and respectively in

Application logic may include abort logic to cause processor to count user inputs that do not correlate to a rendered image and to abort one or more portions of application logic when a number of non correlated user inputs exceeds a threshold such as described above with respect to .

Application logic may include logic to cause processor to retrieve an encrypted user value such as credit card information into protected memory domain and to decrypt the user value such as described above with respect to . In the example of a decrypted user value is illustrated within protected memory domain .

Memory may include browser logic to cause processor to interface with one or more remote computer systems over a network. Browser logic may include prompt detect logic to cause processor to detect a prompt from a remote computer system such as a prompt for electronic payment information such as described above with respect to in . Browser logic may include application initiation logic to cause processor to initiate application logic in protected memory domain and to populate the prompt with user input data such as described above with respect to in . One or more of prompt detect logic and application initiation logic or portions thereof may be implemented within a VMM.

Methods and systems disclosed herein may be implemented with respect to other devices that are configurable to communicate information to a computer system including without limitation biometric scanners.

Methods and systems are disclosed herein with the aid of functional building blocks illustrating the functions features and relationships thereof. At least some of the boundaries of these functional building blocks have been arbitrarily defined herein for the convenience of the description. Alternate boundaries may be defined so long as the specified functions and relationships thereof are appropriately performed.

One skilled in the art will recognize that these functional building blocks can be implemented by discrete components application specific integrated circuits processors executing appropriate software and combinations thereof.

While various embodiments are disclosed herein it should be understood that they have been presented by way of example only and not limitation. It will be apparent to persons skilled in the relevant art that various changes in form and detail may be made therein without departing from the spirit and scope of the methods and systems disclosed herein. Thus the breadth and scope of the claims should not be limited by any of the exemplary embodiments disclosed herein.

