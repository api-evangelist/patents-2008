---

title: Sonoelastographic shear velocity imaging using crawling wave excitation
abstract: Vibration sources are applied to a body or other object to image a region of interest. The mechanical vibrations introduced by the sources interfere in the region of interest to produce a crawling wave, which is detected by an ultrasound probe A relationship between crawling wave phase derivatives and local shear wave velocity is derived with phase derivatives estimated using either one-dimensional (1D) or two-dimensional (2D) autocorrelation-based techniques to image the region of interest.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08267865&OS=08267865&RS=08267865
owner: University of Rochester
number: 08267865
owner_city: Rochester
owner_country: US
publication_date: 20080215
---
The present application claims the benefit of U.S. Provisional Patent Application No. 60 901 643 filed Feb. 16 2007 whose disclosure is hereby incorporated by reference in its entirety into the present disclosure.

The work leading to the present invention was supported by NIH Grant No. 5 R01 AG16317 05. The government has certain rights in the invention.

The present invention is directed to sonoelastography and more particularly to sonoelastography using interfering shear waves to produce crawling waves.

Vibrational sonoelastography is a tissue elasticity imaging technique developed at the University of Rochester which estimates the amplitude response of tissues under harmonic mechanical excitation using ultrasonic Doppler techniques. Due to a mathematical relationship between particle vibrational response and received Doppler spectral variance low frequency 50 to 500 Hz and low amplitude 1 to 100 m shear waves propagating in tissue can be visualized using sonoelastography to detect regions of abnormal stiffness. Low frequency shear waves are used because they are much less attenuated due to damping mechanisms than at higher frequencies. Furthermore given the shear moduli distribution typically encountered in soft tissue more than four orders of magnitude corresponding wavelengths reside in the useful range of millimeters.

Recently it was shown that interfering shear waves produce slowly propagating interference patterns with an apparent velocity much less than but proportional to the underlying true shear velocity. Termed crawling waves they are generated using a pair of mechanical sources vibrating at slightly offset frequencies or by continuously phase shifting one of the source excitation signals.

Sonoelastographic imaging of interference patterns has been used for estimation of the shear velocity of homogeneous biomaterials. However before the present invention it had not been used for imaging of heterogeneous biomaterials.

To achieve the above and other objects the present invention is directed to a novel real time sonoelastographic technique for estimating local shear velocities from crawling wave images. Specifically a relationship between crawling wave phase derivatives and local shear wave velocity is derived with phase derivatives estimated using either one dimensional 1D or two dimensional 2D autocorrelation based techniques. In comparison the 1D sonoelastographic shear velocity estimator has the advantage of being computationally simple whereas the 2D estimation technique provides enhanced performance in terms of minimizing noise artifacts. Thus a fundamental tradeoff between computational time and estimator performance distinguishes these two dedicated shear velocity estimation and imaging algorithms.

The shear wave interference patterns can be visualized in real time using sonoelastographic imaging techniques. In general crawling wave images describe shear wave propagation patterns and allow local estimation of shear velocity distributions. Assuming that the local shear velocity values are proportional to the square root of the shear modulus spatial mapping of either parameter allows production of quantitative tissue elasticity images.

The experimental setup is centered on an ultrasound scanner modified for sonoelastographic imaging that allows real time visualization of crawling wave sonoelastograms. Furthermore sonoelastographic data either image or demodulated data sets i.e. in phase and quadrature signals are utilized for processing shear velocity sonoelastograms.

Two or more preferably two vibration sources are utilized to excite shear wave propagation and to generate shear wave interference patterns i.e. crawling waves . These sources or active vibration regions are placed in appropriate locations such as in direct contact with opposing lateral boundaries of the biomaterial with the long axis and induced shear vibration parallel to and in line with the desired image plane governed by transducer positioning . Vibration can be achieved in a variety of ways e.g. using external vibration sources in contact with the tissue or using an acoustic radiation force on each side of the region of interest to generate the interference patterns. A two channel signal generator produces two monochrome low frequency signals that are typically amplified before being input to the vibration sources. Introducing a frequency offset or phase shifting one of the vibration excitation signals allows spatial translation of shear wave interference patterns i.e. crawling waves across the image plane. If the delta frequency of the vibration sources becomes zero or very small then the crawling wave becomes a fixed interference pattern. Such a fixed interference pattern can also be used with the 1D and 2D estimators of the present invention.

Additional disclosure is found in the following publications which are hereby incorporated by reference in their entireties into the present disclosure 

Preferred embodiments of the invention will now be set forth in detail with reference to the drawings in which like reference numerals refer to like elements or steps throughout.

Shear wave interference displacement fields u m n excited using a pair of monochromatic mechanical sources can be expressed as standing wave patterns 2exp cos 2 cos 2 1 

where m and n are integer values denoting row and column matrix indices i.e. spatial coordinates respectively A is the excitation source amplitude is the shear wave attenuation coefficient D is the excitation source separation distance Tdenotes the spatial sampling interval along the n axis i.e. shear wave propagation axis or lateral direction and kand kdenote the shear wave number and difference respectively. Note that eqn 1 assumes that the shear wave displacement data are parallel to a line of sight connecting the vibration sources. Moreover eqn 1 assumes plane wave conditions and can be realized in practice by imaging in the far field of the shear wave sources. For discrete shear wave displacement data the analytic signal m n of u m n is defined as 2 

The shear velocity in 1D space can be estimated by evaluating the phase of the 1D autocorrelation function circumflex over n of the analytic signal m n 

at lag n 1 and where denotes the complex conjugation operator. For the above discussion it has been assumed that the observation window consists of N lateral discrete samples n 0 1 . . . N 1 i.e. the data kernel is taken parallel to the shear wave interference pattern axis. Finally the 1D mean shear velocity estimate is given as follows 

which indicates that the local shear velocity can be estimated from spatial shear wave interference patterns or crawling wave image frame given knowledge of the source vibration frequencies and spatial sampling rate. Since eqn 5 produces a local shear velocity estimate 2D spatial distributions for a given region of interest are obtained by one sample shifting the kernel throughout the shear wave displacement field. The resultant matrix is imaged and termed a shear velocity sonoelastogram.

Analogous to the approach just introduced the shear velocity in 2D space can be estimated by evaluating the phase of the 2D autocorrelation function circumflex over m n of the analytic signal m n 

at lags m 1 n 0 and m 0 n 1 Equation 6 assumes that the observation window consists of M axial samples m 0 1 . . . M 1 and N lateral samples n 0 1 . . . N 1 . Lastly the mean shear velocities and as estimated independently and relative to the m axis and n axis respectively are given by the following expressions 

Consideration of eqns 7 and 8 allows definition an angular component see showing a two dimensional description of the mean shear velocity vectors in relation to a representative shear wave interference pattern 

Introduction of eqn 9 allows realization of a 2D mean shear velocity estimate D by projecting the 2D shear velocity vector onto the n axis sin 10 

indicating that the 2D local shear velocity can be estimated from the spatial shear wave interference patterns given knowledge of the source vibration frequencies and spatial sampling rate. In the derivation of eqn 12 we assume that within the region defined by our kernel size that the tissue property is approximately homogeneous and that the shear wave interference patterns can be approximated as plane waves. Since eqn 12 produces a local shear velocity estimate 2D spatial distributions are obtained by one sample shifting the kernel throughout the shear wave displacement field.

A summary of the shear velocity imaging strategies outlined in the above sections is illustrated schematically in . In step the shear wave propagation is excited using the vibration sources and to the biomaterial A or B. In step of imaging the shear wave interference pattern motion a sonoeleastographic imaging system produces a crawling wave sonoelastogram . In step of imaging the shear velocity distribution an analytic sonoelastogram is formed as described above and is applied to 1D shear velocity estimation or 2D shear velocity estimation to produce a shear velocity sonoelastogram . Notice that the only major difference between the 1D and 2D shear velocity imaging techniques is in the numerical techniques utilized to process the analytic crawling wave sonoelastograms. Although the developed estimation technique is premised on crawling wave excitation this novel real time autocorrelation based technique can be modified for processing and imaging tissue elasticity information from data acquired using holographic wave excitation and magnetic resonance elastography MRE . In general where changes in spatially varying shear wave displacement feeds are imaged and governed by the true underlying biomaterial elastic properties.

The invention has been shown to be useful in lesion contrast and detection and in muscle tissue characterization.

While preferred embodiments of the present invention have been set forth above those skilled in the art who have reviewed the present disclosure will readily appreciate that other embodiments can be realized within the scope of the invention. For example numerical values are illustrative rather than limiting as are disclosures of specific uses. Therefore the present invention should be construed as limited only by the appended claims.

