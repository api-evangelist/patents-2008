---

title: Star sensing for an earth imaging sensor
abstract: A star sensor includes (a) a scan mirror for scanning at least one star; (b) a detector array, coupled to the scan mirror, for detecting the one star; and (c) a processor, coupled to the detector array. The processor includes a first filter configured to reduce noise spikes in the detected one star, and provide a detection mask of filtered data. Also included is a second filter configured to reduce non-contiguous samples in the detection mask. A centroid calculator is included to determine a location of the one star, after the first and second filtering. The first filter includes a median filter, followed by an averaging filter, both configured to filter the one star in an along-scan direction of the scan mirror. The first filter includes another median filter, which is configured to filter the detected one star in the cross-scan direction of the scan mirror. An adder is included to subtract (a) output data from the other median filter from (b) output data from the averaging filter and provide filtered star data to the second filter.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08218013&OS=08218013&RS=08218013
owner: Exelis, Inc
number: 08218013
owner_city: McLean
owner_country: US
publication_date: 20080527
---
The invention described herein was made in the performance of work under NASA contract no. NAS5 01119. The government has certain rights in the invention.

The present invention relates in general to a system and method for navigating using star imagery collected by a satellite based imaging system. More specifically the present invention relates to a system and method for detecting stars in a focal plane array FPA of an imager in order to determine a line of sight LOS from a target star to each detector in the FPA.

Star trackers may be used as attitude determination instruments onboard satellites. In essence a star tracker is a camera connected to a microcomputer located in a satellite. Using the camera to capture a sensed image of the sky stars may be located and identified. The orientation of the satellite may be determined based on these observations. A star tracker automatically recognizes the star patterns in the field of view FOV of the camera and calculates the attitude with respect to the celestial sphere being orbited by the satellite.

The performance of a star tracker depends on many parameters. For example performance may depend on the sensitivity to starlight the FOV the accuracy of the star centroiding algorithm the star detection threshold the number of stars in the FOV the internal star catalog and the calibration process.

Star sensors fall into two categories scanners and trackers. Scanners have a linear array of detectors that is scanned across the sky in a direction perpendicular to the span of the array. Trackers view the sky with a 2 dimensional detector array. Both of these systems collect a 2 dimensional image of the star field the scanner by scanning and the tracker by staring.

Most star sensing systems are dedicated to scanning or tracking the sky. They have suitable signal to noise S N ratios and spatial resolutions so that stars may be detected and the images may be properly centroided to provide stellar locations in focal plane coordinates.

Dedicated star scanners trackers typically may use a star sensing algorithm that includes the following steps 

In an article titled Accuracy Performance of Star Trackers A Tutorial by Carl Christian Liebe published by IEEE Transactions on Aerospace and Electronic Systems Vol. 38 No. 2 April 2002 star detection is described. Liebe notes that principal contributors to the background signal noise are typically read noise and inhomogeneity of dark currents in the pixels. It may be possible to estimate the background noise as a standard deviation of all pixel values in a dark frame. A focal plane which may include up to 10pixels may set the detection threshold of a star signal to an average background pixel value plus 5 times the standard deviation to avoid false positives. A star may then be detected if the brightest pixel in the star is above the set threshold.

The brightest pixel of a star depends on a point spread function PSF and position of the star. As an example if the star image has a Gaussian PSF radius of 0.5 pixels and is centered on a pixel then approximately 29 of the signal may be contained in the brightest pixel. If the radius of the Gaussian PSF is 1 pixel and the star is centered on a boundary between 4 pixels however then the brightest pixel may only contain 13 of the signal approximately.

With respect to centroiding Liebe notes that star trackers utilize subpixel centroiding to increase accuracy. In a focused image a star appears as a point source so all photoelectrons from the star are generated in a single pixel. If the optics are slightly defocused however the star may occupy several pixels. Defocusing thus facilitates calculating the center of the star with subpixel accuracy.

Initially the image may be sifted for pixels that are above a predetermined threshold. Once a pixel is detected a region of interest ROI window may be centered around the detected pixel. The average pixel value on the border may be calculated and subtracted from all other pixels in the ROI.

Instruments that are dedicated to perform star tracking and require very accurate pointing knowledge do not tolerate alignment uncertainty between the instrument s focal plane array FPA and the star. Additional algorithms may be necessary to increase accuracy between the instrument s FPA and a line pointing to the star.

When star sensing is performed with an instrument designed for imaging the earth however standard algorithms may not be good enough. Because the instrument s design is driven by requirements for obtaining good earth imagery the ability to perform star sensing may be compromised.

Further complications may arise from the fact that stars are relatively dim compared to the high albedo portions of the sunlit earth. Thus an earth imager is typically less sensitive to dim stars than a dedicated star sensor would be. Typical integration times for an earth imager may be 1000 times shorter than those of a dedicated star tracker. Also a limited FOV in the earth imager may place additional constraints on the available stars and the earth imager may have to rely on dimmer stars. Thus the signal to noise ratio SNR of star signals from the earth imager may be lower than the SNR of a dedicated star sensor.

Current algorithms may not be able to reliably detect dim stars. The simple thresholding techniques used by current algorithms do not distinguish between light from stars and spikes due to noise or cosmic rays. These algorithms therefore may have high false alarm rates.

The maximum detector signal from a star is variable since the energy may be split among several detectors. The fraction of the star energy collected by a detector depends on the star s path across the detector array which is both variable and unknown. Current algorithms may use a fixed detection threshold that is perhaps five times the RMS value of the noise. These algorithms may not be able to detect dim stars having an SNR of five or less and may be unreliable when detecting stars with an SNR of 10 or less due to detector signal variations from the scan geometry.

Current algorithms may calculate the centroid of the detector samples within a window of a predetermined size that is expected to include only the star of interest. There may be no certainty however that all the star energy falls within this window. In addition the inclusion of detector samples that contain little or no signal skews the results and diminishes the accuracy.

Furthermore the accuracy of current centroiding techniques may be diminished by noise spikes and may be completely destroyed when including pixels from nearby stars.

Scattered light in the optics or in the atmosphere may introduce background gradients in the detected data depending on the relative positions of the star earth moon and sun. The background gradients may bias the star centroid degrading accuracy for line of sight LOS angles that are relatively far from the sun even 20 30 degrees away . This limits the stars that may properly be centroided with current algorithms.

The present invention addresses the above deficiencies and provides a solution to each one as described below.

To meet this and other needs and in view of its purposes the present invention provides a star sensor including a a detector array for viewing at least one star and outputting star data b a median filter configured to reduce spikes in the outputted star data and provide first filtered star data c an averaging filter configured to low pass filter the first filtered star data and output second filtered star data. A calculator is included for determining a location of the one star in the detector array based on the second filtered star data.

The median filter includes a one row by three columns 1 3 median filter in the along scan direction of the detector array. The averaging filter includes a one row by at least 12 columns 1 12 averaging filter in the along scan direction of the detector array. The averaging filter may be a moving averaging filter configured to move by one column in the one row in order to average filter another at least 12 columns in the along scan direction of the detector array.

The present invention may include another median filter configured to remove noise in the cross scan direction and provide third filtered star data. A summer is configured to subtract the third filtered star data from the second filtered star data and provide fourth filtered star data.

The present invention may include an adder for sequentially adding adjacent rows of the fourth filtered star data and provide the adjacent added rows to the calculator. A threshold module may be configured to output portions of the fourth filtered star data in response to a user defined detection threshold where the outputted portions of the fourth filtered star data is provided as a detection mask to the calculator.

The calculator may include a 1 3 binary opening module and a 1 3 binary closing module configured to receive the detection mask and output reduced non contiguous detected samples in the detection mask. A multiplier is configured to provide a product of the fourth filtered star data with the outputted reduced non contiguous detected samples. A centroid calculator is included for estimating a centroid position of the product outputted from the multiplier to obtain the location of the one star.

In another embodiment of the present invention a star sensor includes a scan mirror for scanning at least one star a detector array coupled to the scan mirror for detecting the one star and a processor coupled to the detector array for executing various algorithms. The processor includes a a first filter configured to reduce noise spikes in the detected at least one star and provide a detection mask of filtered data b a second filter configured to reduce non contiguous samples in the detection mask and c a centroid calculator configured to determine a location of the at least one star.

The first filter includes a median filter followed by an averaging filter where both filters are configured to filter the detected one star in the along scan direction of the scan mirror. The first filter includes another median filter configured to filter the detected one star in the cross scan direction of the scan mirror. An adder is configured to subtract a output data of the other median filter from b output data from the averaging filter to provide filtered star data to the second filter. A threshold module is configured to provide the detection mask to the second filter after thresholding the filtered star data. A multiplier is configured to provide a product of a the filtered star data and b the detection mask. The data provided from the multiplier is sent to the centroid calculator.

The star sensor may include a star identification ID verifier coupled to the centroid calculator for verifying the location of the one star.

In yet another embodiment of the present invention a method of sensing a star includes the steps of a receiving scanned image data of at least one star b filtering the scanned image data in the along scan direction to provide along scanned image data c further filtering the scanned image data in the cross scan direction to provide cross scanned image data d subtracting the cross scanned image data from the along scanned image data to provide filtered star data and e calculating a centroid location of the at least one star based on the filtered star data.

Step b includes median filtering the scanned image data to provide first filtered data and next average filtering the first filtered data to provide the along scanned image data. Step c includes median filtering the scanned image data to provide the cross scanned image data. The method further includes the steps of after subtracting in step d thresholding the subtracted data to provide a detection mask and forming a product of the filtered star data and the detection masks. The formed product is used by the calculating in step e .

The method of the present invention may include the step of verifying the centroid location calculated in step e based on data from a star catalog.

It is understood that the foregoing general description and the following detailed description are exemplary but are not restrictive of the invention.

As will be explained the present invention overcomes sensitivity of star detection to noise by applying median and averaging filters to the detected data in order to eliminate noise spikes and reduce noise. These median and averaging filters permit dim stars to be detected with a higher probability and a lower false alarm rate than conventional star sensing techniques.

As will also be explained the present invention overcomes background and stray light effects by estimating a background gradient from a median filter used for filtering each column in the detector array and then subtracting the filtered column from the same column belonging to a previously averaged row in the detector array.

The present invention overcomes the problem of dividing star signals between detectors. This may be accomplished by adding signals in adjacent rows of the detector array.

The present invention achieves robust performance although it may use a fixed detection threshold. This may be accomplished by combining background estimation and subtraction with added signals of adjacent rows of the detector array.

The present invention reduces loss of centroiding accuracy due to extraneous pixels containing either noise or nearby stars by applying spatial filtering operations to select only samples that are contiguous with the brightest sample and smoothing the edges of the sampled region.

The present invention reduces loss of centroiding accuracy caused by adding together adjacent detector signals. This may be accomplished by centroiding the sampled data values that are obtained prior to adding together the signals of adjacent detectors.

Referring first to there is shown a star sensing system generally designated as . As shown star sensing system includes imager which resides in a satellite orbiting a celestial body such as the earth and ground processing station which is located on the ground. Imager includes scan mirror telescope detector array and communication electronic modules . The ground processing station may include star algorithm s and other algorithms .

Scan mirror may be mounted on a two axis gimbal which selectively positions the scan mirror in the along scan and cross scan axes east west and north south respectively . The scan mirror may move to locate and scan across a predetermined star known from a star catalog. The star catalog may be stored in memory not shown .

The telescope receives the light arriving from scan mirror and forms an image on detector array . The image s may include star light and unwanted scattered light. Various electronic modules designated as may be provided for amplifying and digitizing the detected image s to form star data for transmission to ground processing station . The star data may contain unwanted noise generated by the random arrival rate of the photons and the detector electronics noise sources. The electronic modules may also include the communications command and control required for downlinking detected star data to ground processing station . The electronic modules may also include compression algorithms for compressing detected star data to achieve compatibility with bandwidth limitations of the communications link.

In addition to other algorithms designated as the ground processing station may include various algorithms described later in detail but shown in simply as star algorithm . It will be appreciated however that the star and other algorithms may reside in electronic modules which is shown located in imager residing in the satellite. Accordingly the present invention is not limited to the functional block sequence shown in .

A single star measurement may include using scan mirror to point a line of sight LOS closely to a predicted star location and scan the star with a portion of a visible or an IR detector array such as detector array . The initial location may be calculated from an attitude signal provided by the satellite. During star data collection attitude rate information from the satellite may be used to compensate for satellite motion thereby permitting a reduction in the time required to collect the star data.

The detectors of detector array may be sampled at a high rate relative to the scanning rate of scan mirror so that several hundred samples of a star may be collected in the scan direction. This allows for filtering the background noise without any corresponding loss in centroid accuracy of the detected star.

For star sensing the present invention does not need to collect star data from the entire detector array. The present invention may select only a portion of the detector array that includes contiguous good detectors and then use the scan mirror to center that portion of the detector array on the predicted star location.

There may be times when the satellite s motion more than offsets the orbital motion effectively resulting in a scan away from the target star. A possible solution provided by the present invention may be to use the scan mirror to compensate for the satellite s motion based on attitude rate data received from inertial navigation systems in the satellite.

By way of example a compensation signal may be generated from the last known satellite s attitude. This signal may be converted to an equivalent scan mirror shaft angle and the shaft angle with an integral value of the converted . satellite s attitude rate may be used to update the shaft angle. In addition a look up table may be uploaded once per day with compensation terms for diurnal thermal and orbit errors. Thus by applying motion compensation terms to the motors of the scan mirror the present invention ensures that the detectors drift across the star at the sidereal rate.

Turning next to there is shown an exemplary star sensing algorithm designated as which may be executed by a computer or microcomputer residing in ground processing station or in imager located in the satellite . Alternatively the algorithm may be executed by a computer or microcontroller located in the satellite but residing externally of imager .

As shown star sensing algorithm may include decompression and calibration module star sample detector FPA location calculator and star ID verifier . It will be appreciated that input and output signals are shown as rhombuses for the following 

It will be understood that the decompression portion of decompression and calibration module may be required if star data is compressed for downlink to ground processing station . If the star sensing is performed on board the satellite however compression and decompression of star data may not be necessary.

The calibration portion of decompression and calibration module may include any process that removes variations in amplitude gains and offsets from digital counts recorded by the detectors. Typically calibration may be accomplished by converting digital counts into radiance units. Calibration may be accomplished for example by viewing targets of known high and low radiances and determining a linear function that relates the known radiances to the digital counts. Calibration may also be necessary to ensure performance is not degraded by sensor artifacts.

After decompression and calibration of star data the star samples detector provides various filters configured to median filter and average filter the star data. The manner in which the star samples detector provides such filtering will be described later with respect to . The star samples detector provides several output data to FPA location calculator . These output data include a detection mask filtered star data and a location of the maximum intensity detector sample. Another output namely star instrument magnitude may be provided to star ID verifier . This star instrument magnitude may be saved for later star verification by star ID verifier .

As will be explained with respect to FPA location calculator receives the detection mask the filtered star data and the location of the maximum intensity signal located in the image and calculates a location of a target star for tracking purposes. The output location of the target star namely i k is shown designated in . This output location may be compared to a known location of the desired star from the star catalog in order to verify the identification ID of the target star.

Referring next to the star sample detector designated as same as star sample detector shown in will now be described. The star sample detector may include 1 3 median filter averaging filter 24 1 median filter and decimator . Additional functions that may be included as shown are summer row pair adder MAX module and thresholding module .

Star data may include data from each of the detectors or pixels selected for star sensing. These may be data from the entire detector array or only a portion of the detector array. Each of the detectors selected for star sensing may be sampled rapidly while the LOS of the mirror slowly scans across the sky forming a data set having many samples of the star or stars in the East West direction direction of drift also referred to herein as the along scan direction.

The star data may first be filtered by 1 3 median filter in the along scan direction. It will be understood that 1 3 designates an array of 1 row by 3 columns of pixels or detector samples . Because cosmic ray and noise spikes tend to be only one sample wide these may be removed from the star data using 1 3 median filter . This 3 sample median filtering may be performed by successively finding the median intensity of the 3 samples as shown in . As shown the pixels in row i may be sampled three columns at a time until all the pixels in row i have been sampled for example a b c etc. . When filtering of row i is completed the 1 3 median filter may similarly sample the next row and so on until the entire data set for example an entire detector array has been filtered.

As another example of a 1 3 median filter contemplated by the present invention there is shown a moving 1 3 median filtering sequence a b c d etc. in . As shown during sequence a pixels 1 2 3 are sampled during sequence b pixels 2 3 4 are sampled during sequence c pixels 3 4 5 are sampled and so on.

After completing the 1 3 along scan median filtering for the entire selected portion of detector array the present invention may perform a 1 123 along scan average filtering. As previously described with respect to and average filter may perform a 1 123 along scan average filtering using a moving average filtering or simply a successive non moving average filtering.

Since the star profiles are slowly varying the present invention may use the 1 123 average filter as a low pass filter to reduce the noise. The present invention may accomplish the low pass filtering by applying a moving average window. The width of the window may be selected to maximize the SNR of the filtered data.

It will be appreciated that the sequence process of first median filtering filter and secondly average filtering filter results in a more accurate estimate of the true value of the star data thereby improving performance. The averaging window may move 10 samples between steps to effectively decimate the data as performed by decimator .

In the window size is given as 123 samples wide but both this window size and the decimation interval may have any value and may be chosen to optimize the SNR while minimizing the amount of data processed in any subsequent steps.

Another median filter designated as may be used by the present invention to median filter the columns of the desired array portion of detector array . This filtering is performed in the cross scan direction perpendicular to the along scan direction . As an example 24 1 median filter is shown in denoting 24 rows of data in a single column.

As previously described with respect to and the 24 1 cross scan median filtering may include a moving median or simply a successive non moving median. The example of median filter shown in includes 24 detectors to sample the sky but this number may be another number of detectors that adequately covers the star search area.

After decimation by decimator in the along scan direction and after 24 1 median filtering by filter in the cross scan direction summer actually a subtraction module subtracts the median of each column output by median filter from the column values output by averaging filter . This is performed in order to remove any along scan background gradients. The output of summer includes a set of filtered star data shown designated as

In order to obtain a more uniform star signal when the star image may be split between detectors adjacent rows of the data may be added by the present invention using row pair adder . For example rows 1 and 2 may be summed rows 2 and 3 may be summed rows 3 and 4 may be summed etc.

The resulting filtered and row paired star data may be compared to threshold which may be determined by a user from the required probability of detection PD probability of false alarm PFA and noise level . All star data samples that exceed predetermined threshold may be declared to be valid star samples by thresholding module . The output map of these valid star samples from module is referred to herein as the detection mask designated as

An example of detection mask is shown in . It will be appreciated that the star data are highly over sampled in the along scan direction so that when the star data is displayed in image format as shown in the star appears to be horizontally elongated rather than circular.

A module for determining the maximum intensity star in the filtered and row paired star data is shown designated as MAX module . The MAX module provides the maximum filtered star signal as star instrument magnitude which may be saved for later star verification. The pixel location i k of the maximum filtered star signal may also be saved for use in further filtering the detection mask prior to locating the star. The pixel location of i k may be provided as an output signal to fill and filter module shown designated as output

Referring now to there is shown greater detail of the FPA location calculator shown in . As shown in FPA location calculator may include 1 3 opening module 1 3 closing module fill and filter module multiplier and sample centroid calculator . As also shown the location of i k detection mask and filtered star data may be provided as input data. The output data shown in the figure namely the centroid location of the star i k is designated as .

Still referring to and describing it as a flow diagram the present invention first applies 1 3 along scan binary opening and closing operations to detection mask . These operations reduce non contiguous detected samples and fill in single sample holes in the detection mask. These operations ensure that samples close to the threshold value do not skew the final centroid calculations performed by module .

An opening operation reduces positive spikes in the data having widths on the order of 1 3 pixel size for example . Structures in the signal that are larger than some kernel value may be unchanged in size. A closing operation on the other hand fills in negative spikes that may be the size of the kernel and leaves larger structures unchanged in size.

In more detail opening and closing operations may be related to morphology which is a branch of image processing using nonlinear operations to extract shape size and texture information from a signal. Opening and closing operations are analogous to convolution operations. They use a kernel a structuring element that is tailored to alter a signal in a desired manner. Like convolution this morphological kernel has a center which is placed on the pixel of interest. The value of this pixel in the output image is determined by a nonlinear combination of the kernel values and the pixel values.

The opening and closing operations may use any size or shape kernel. A 1 3 structuring element is used herein as an example.

In binary opening and closing operations the values of the pixels are either 1 or 0 . Furthermore an opening operation involves morphologically first erosion and secondly dilation. Erosion in binary is an AND operation on input samples and dilation in binary is an OR operation on input samples. An example of an opening operation is shown in . The pixels in row a may be considered as an input to an erosion operation or AND operation . A 1 3 sliding window a window moving over by one pixel for example may be applied to the input data row a where 3 pixels are shown AND ed together. The output from the erosion operation is shown as the pixels in row b .

Next the pixels in row b may be considered as an input to a dilation operation or an OR ing operation . Another sliding window a window moving over by one pixel for example may be applied to the input data row b where 3 pixels are shown OR ed together. The output from the dilation operation is shown as the pixels in row c .

Examining it may be seen that a binary opening operation removes 1 pixel wide noise spikes and retains features that are 3 pixels wide. After applying a binary opening operation to the detection mask an image may result as shown in . Accordingly most spikes seen in the detection mask may be removed.

Next a closing operation will be described. A closing operation involves morphologically first dilation and secondly erosion. An example of a closing operation is shown in . The pixels in row a may be considered as an input to a dilation operation or an OR operation . A sliding window window moving over by one pixel for example may be applied to the input data row a where 3 pixels are OR ed together. The output from the dilation operation is shown as the pixels in row b .

Next the pixels in row b may be considered as an input to an erosion operation or an AND ing operation . Another sliding window window moving over by one pixel for example may be applied to the input data row b where 3 pixels are AND ed together. The output from the erosion operation is shown as the pixels in row c .

Examining it may be seen that a binary closing operation fills in noise holes. Applying a binary closing operation after the opening operation shown in results in an image shown in . Accordingly most noise holes may end up being filled.

Returning to the present invention first applies 1 3 binary opening and closing operations modules and to the detection mask as an example. These operations may reduce non contiguous detected samples and may fill in single sample holes in the detection mask. This ensures that samples close to the threshold do not skew the later performance of centroid calculator .

It will be appreciated that it is possible to obtain more than one detected blob in the star data. This may be due to a noise burst or to a nearby star that exceeds the detection threshold. A bright object avoidance criteria may be used by the present invention to ensure that the target star is the brightest object in the collected field. Median and moving average filtering in the detection algorithm of the invention makes it less likely that a noise burst will exceed the target star signal. However it may still be possible that noise or dimmer stars will exceed the detection threshold and produce additional blobs in the detection mask. Since the maximum sample value is likely produced by the target star the present invention may use the maximum sample value as a seed to fill the detection blob. Any remaining blobs may be discarded.

Accordingly fill and filter module may be used by the present invention as shown with the maximum sample value located at i k as a seed to fill the detection blob. After filling and filtering by module exemplary output data is shown in the input data is the image shown in . It will be appreciated that the extra 2 blobs in image are eliminated in image . A final example of a detection blob outline laid over a photographic negative of the star intensity image is shown in

Next in the flow process multiplier multiplies filtered star data with the resulting detection mask outputted from module to obtain star sample intensities that exceed the detection threshold. Note that the filtered star data is the data prior to adding the adjacent detector samples together as shown in . Next module calculates the centroid of these valid samples to determine the location k of the star blur spot in the focal plane array coordinates i k . Note that since the array is scanning in the i direction but is oriented along the k direction icorresponds to the time at which the star is centered on the detector and kcorresponds to the cross scan location of the star on the array at that time. The output location i k of the target star is designated as shown in .

There are many centroiding algorithms that may be used by the present invention including but not limited to thresholding windowing correlation quad cell and first moment calculations. Regardless of which centroiding algorithm may be selected the performance of the selected algorithm is enhanced by the processing steps of the present invention.

Having detected and located the target star the measured magnitude of the target star at position i may be compared with predicted values. Accordingly the measured position at i k may be compared with the FPA coordinates predicted for the target star. If the difference between the measured and the predicted positions is too large the star may be rejected as the target star.

The maximum star signal may also be compared to the predicted instrument magnitude of the star. If the difference exceeds the accuracy of the measurement for example three times the RSS of the RMS measurement precision and RMS prediction precision the star may be rejected as the target star. The comparison may be made by star ID verifier using input data of the magnitude at i location and the star instrument magnitude .

Although illustrated and described herein with reference to certain specific embodiments the present invention is nevertheless not intended to be limited to the details shown. Rather various modifications may be made in the details within the scope and range of equivalents of the claims and without departing from the spirit of the invention. For example the present invention may be used in the following additional applications 

Wavefront sensing includes estimating the shape of the phase of an optical beam and using this information to compensate for aberrations and improve the imaging performance of an optical system. There are various methods for accomplishing wavefront sensing. One of them known as Hartmann Shack includes placing a lenslet array over a detector array and using the locations of the resulting focused spots one spot for each lenslet to estimate the tilt of the phasefront as a function of location.

It will be appreciated that the process of determining the focused spot locations is analogous to determining the location of a star during star sense. Thus the present invention may be used to improve performance of wavefront sensors or any other sensor used for determining the location of a focused spot of light.

Stellar photometry requires accurate spatial integration of light received from a star and at the same time it requires reducing noise and unwanted background. In addition star intensity measurements need to be less dependent on the position of the star image relative to the detector centers. The present invention may be used to better position the star image and to reduce noise and unwanted background.

Astrometry requires determining an accurate star location and processing stellar images with accurate centroiding algorithms. The present invention may be used to improve star detection and location in astrometry.

Optical link acquisition systems locate the source of a laser beam and use that information to point both a receiving sensor and an illuminating transmitter at the laser beam source see for example U.S. Pat. No. 6 469 815 . Like star sensing this may be considered a point source detection and location problem. Like star scanning systems optical link acquisition systems are scanned across the detector array although in optical link acquisitions sysytems it may be the source that scans not the receiver. The present invention may be used to improve optical link acquisition systems.

