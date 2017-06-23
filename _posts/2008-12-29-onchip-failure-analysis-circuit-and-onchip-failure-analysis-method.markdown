---

title: On-chip failure analysis circuit and on-chip failure analysis method
abstract: An on-chip failure analysis circuit for analyzing a memory has a memory in which data is stored, a built-in self test unit which tests the memory, a failure detection unit which detects a failure of the output of the memory, a fail data storage unit in which fail data is stored, the fail data including a location of the failure, a failure analysis unit which performs failure analysis using the number of failures detected by the failure detection unit and the location of the failure, the failure analysis unit writing fail data including the analysis result in the fail data storage unit, and an analysis result output unit which outputs the analysis result of the failure analysis unit.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08037376&OS=08037376&RS=08037376
owner: Kabushiki Kaisha Toshiba
number: 08037376
owner_city: Tokyo
owner_country: JP
publication_date: 20081229
---
This application is based upon and claims the benefit of priority from the prior Japanese Patent Application No. 2007 339885 filed on Dec. 28 2007 the entire contents of which are incorporated herein by reference.

The present invention relates to an on chip failure analysis circuit and an on chip failure analysis method particularly to an on chip failure analysis circuit of a semiconductor integrated circuit in which a self test circuit for a memory is built and an on chip failure analysis method.

There is well known a method for detecting failures in a production test in which a built in self test hereinafter referred to as BIST Built In Self Test circuit is built in a semiconductor integrated circuit for embedded memories. Examples of the BIST circuit includes a comparator type BIST circuit which compares written data and read data to make a determination of the existence of a defect and a compressor type BIST circuit which compresses the read result in the BIST circuit to make the determination of the existence of the defect according to the compressed result.

There is also well known a repair technique of utilizing a memory cell having a redundant structure to repair the embedded memory determined as a defective memory. The memory cell having the redundant structure includes a spare row or a spare column. In the simplest case the memory cell includes a set of spare rows or spare columns in each repair unit. In the more complicated case the memory cell includes both the spare row and the spare column the memory cell includes plural spare rows or spare columns or one memory array is divided into plural segments each of which includes the memory cells having the repair structures.

In order to utilize the repair technique in the production of the semiconductor integrated circuit and the memory test it is necessary to perform an analysis using the result of the memory test to obtain a memory defect location and a spare used in repair hereinafter referred to as repair solution and to perform the redundancy allocation according to the obtained repair solution. Generally the repair technique is realized as follows. That is the memory test is performed using a memory tester and a direct access circuit which directly accesses the memory a memory output map is written in a storage unit of the memory tester and a program on the memory tester is started up to perform the analysis.

However in the conventional repair technique because the memory tester having a sufficiently large capacity of a storage unit is required to store pieces of fail data on all bits of the memory it is necessary to use both the memory tester and a logic tester in the test for a system LSI Large Scale Integration including a logic circuit and the memory.

Because many embedded memories are provided on the usual large scale system LSI the direct access circuit is hardly prepared in each of all memories which become a repair object.

A built in redundancy allocation hereinafter referred to as BIRA Built In Redundancy Allocation circuit which performs the analysis and redundancy allocation is well known as the technique of solving the problems see Japanese Patent Application Laid Open Publication No.2003 505814 . The BIRA circuit is used along with the BIST circuit and obtains the repair solution by analyzing the fail data of the memory according to the failure detection result of the BIST circuit to output the obtained repair solution as the analysis result. In a production process of the semiconductor integrated circuit a chip is repaired by programming a fuse device in which the analysis result is stored using a laser blow apparatus. In the case where the repair solution cannot be obtained the BIRA circuit outputs the analysis result indicating that the repair solution cannot be obtained. In such cases the analyzed chip is dealt with as a defective chip. The BIRA circuit can be realized by a relatively small scale logic circuit for the minimum redundant structure having only one set of spare columns.

A document 1 A Built In Self Repair Analyzer CRESTA for embedded DRAMs International Test Conference 2000 discloses a BIRA circuit. In the document 1 the BIRA circuit is used to repair the memory including plural spare rows and spare columns. In the document 1 the redundancy allocation is performed to all the possible repair solutions when the failure is detected in running the memory test then a combination which successfully repairs the memory is adopted as an analysis result. Accordingly in the document 1 a Content Addressable Memory CAM in which all the repair solutions are stored is provided on the same integrated circuit.

However in the BIRA circuit because the number of repair solutions is increased as the numbers of spare columns and spare rows are increased sometimes all the repair solutions cannot be stored in CAM. In the case where a new memory is provided for the purpose of the memory test a hardware scale is enlarged and disadvantageously the memory test needs to be run for the newly provided memory.

On the other hand a method for producing a complete fail bitmap of the memory is well known as the conventional memory analysis method.

However in the conventional memory analysis method it takes a long time to produce the complete fail bitmap in the case where information is collected in units of wafer or lot online during volume production. Particularly the complete fail bitmap of the memory is not realistic when a logic tester and the BIST circuit are utilized.

On the other hand in addition to the analysis for enhancing a production yield there is well known a built in self diagnosis hereinafter referred to as BISD Built In Self Diagnosis circuit which diagnoses the data used in the analysis. The BISD circuit makes a determination of a type of the memory failure such as a bit failure row failure column failure or a combination thereof. A location of the defect is not always necessary for the BISD purpose.

A document 2 Test Response Compression and Bitmap Encoding for Embedded Memories in Manufacturing Process Monitoring International Test Conference 2001 discloses a BISD circuit. In the document 2 fail data is compressed on the chip to produce a signature the signature is output to the outside to be expanded and is reconstructed outside to make a determination of the type of the failure. In the document 2 because the data collection result is compressed a data transfer time between the memory and the memory tester can be shortened to realize a type determination function for determining a type of the memory failure.

However BISD circuit disclosed in the document 2 the type determination function depends on an external program disadvantageously not only it takes a long time to analyze the memory like the conventional memory analysis but also an information loss is generated due to the compression.

According to a first aspect of the present invention there is provided an on chip failure analysis circuit for analyzing a memory comprising 

a fail data storage unit in which fail data is stored the fail data including a location of the failure 

an failure analysis unit which performs failure analysis using the number of failures detected by the failure detection unit and the location of the failure to write fail data including the analysis result in the fail data storage unit and

According to a second aspect of the present invention there is provided an on chip failure analysis method for analyzing a memory comprising 

performing failure analysis using the number of detected failures and a location of the failure to store fail data including the analysis result and

Exemplary embodiments of the present invention will be described with reference to the drawings. The following embodiments are described only by way of example and the present invention is not limited to the embodiments.

An on chip failure analysis circuit according to a first embodiment of the present invention will be described below. The on chip failure analysis circuit of the first embodiment of the present invention includes a BIRA circuit. The BIRA unit includes a repair analysis circuit which analyzes necessity of redundancy allocation and redundancy allocation result according to the numbers of spare columns and spare rows of the memory.

A configuration of an on chip failure analysis circuit of the first embodiment of the present invention will be described first.

The on chip failure analysis circuit includes a BIST unit a memory collar and BIRA unit . The on chip failure analysis circuit is connected to a test apparatus .

The BIST unit runs a self test of a memory A. The BIST unit outputs data an address row address and column address and a control signal to the memory A to control the memory A so as to perform a reading operation and a writing operation. The BIST unit outputs an expected value of an output signal hereinafter referred to as memory output in the reading operation of the memory A to a failure detection unit B. The BIST unit outputs the address of the memory A in which a failure is detected to the failure analysis unit A.

The memory A is a semiconductor memory device which has a two dimensional redundant structure including a spare column and a spare row. The memory A performs the reading operation and writing operation according to the data address and control signal which are output from the BIST unit .

The failure detection unit B compares the memory output of the memory A to the expected value output from the BIST unit to detect the failure of the memory output.

The BIRA unit includes a failure analysis unit A a fail data storage unit B and an analysis result output unit C.

When the failure detection unit B detects the failure the failure analysis unit A performs an analysis using the address output from the BIST unit to write column fail data including a failure location column address and I O Input Output index and the number of failures in the fail data storage unit B. The failure analysis unit A analyzes the number of failures detected by the failure detection unit B with respect to the row address. The failure analysis unit A performs a row repair analysis process according to the analysis result and the number of effective spare columns of the memory A. The failure analysis unit A also performs a column repair analysis process according to the column fail data stored in the fail data storage unit B and the number of effective spare rows of the memory A. The failure analysis unit A includes a repair analysis circuit. The repair analysis circuit analyzes necessity of redundancy allocation and redundancy allocation result in the row repair analysis process and the column repair analysis process to write repair fail data including the analysis result in the fail data storage unit B.

The fail data storage unit B is a circuit that can store the fail data written by the failure analysis unit A and can have plural pieces of data of the same bit.

The analysis result output unit C reads the fail data hereinafter referred to as analysis result including the repaired fail data stored in the fail data storage unit B to output the analysis result to the test apparatus .

The test apparatus which is of an external device controls an input signal of the BIST unit and observes an output signal of the BIST unit . The test apparatus also reads the analysis result output from the analysis result output unit C.

Alternatively in the first embodiment of the present invention the on chip failure analysis circuit may include plural BIRA units .

As shown in the memory A is illustrated in the first embodiment of the present invention. The memory A includes a memory array two spare columns and two spare rows. The memory array has columns C to C and rows R to R where failures are included in some points. Each spare column and each spare row can independently be used for defect repair.

The BIST unit runs a column first test up to predetermined times Step S . The column first test preferentially controls the column address of the memory A.

The failure detection unit B compares the memory output and the expected value output from the BIST unit to detect the failure of the memory output Step S .

The failure analysis unit A performs a row repair analysis process Step S and a column repair analysis process Step S and in a whole repair analysis process Step S and as described later.

The analysis result output unit C reads the analysis result stored in the fail data storage unit B to output the analysis result to the test apparatus Step S .

Alternatively in the first embodiment of the present invention the memory test process may be run once or the memory test process may be run up to the predetermined times.

Additionally in the first embodiment of the present invention in Step S the column first test and the row first test may mutually be run.

Additionally in the first embodiment of the present invention in the case of the plural BIRA units the memory test may simultaneously be processed or the memory test may sequentially be processed.

The failure analysis unit A refers to the number of failures detected in Step S of and the row addresses in which the failures exist to determine whether or not the number of failures on one row is larger than the number of effective spare columns in the row address Step S . When the number of failures on one row is larger than the number of effective spare columns YES in Step S the failure analysis unit A determines that the row address is a row failure Step S .

The failure analysis unit A writes the repaired fail data in the fail data storage unit B Step S . The repaired fail data includes the redundancy allocation result indicating that the spare row is allocated to the row address determined as the row failure in Step S.

The failure analysis unit A masks the failure of the row address indicated by the repaired fail data written in Step S Step S .

On the other hand when the number of failures on the row address is not more than the number of effective spare columns NO in Step S the processes in Steps S to S are not performed to row address.

The failure analysis unit A determines whether or not the processes in Steps S to S to all the rows are completed Step S . When the processes in Steps S to S to all the rows are completed YES in Step S the row repair analysis process of the first embodiment of the present invention is completed.

The failure analysis unit A writes the column fail data in the fail data storage unit B Step S . The column fail data includes the number of failures except for the failure masked in Step S of and the column addresses and the I O indexes in which the failures exist. shows the result in Step S.

The failure analysis unit A determines whether or not the number of failures on one column is larger than the number of effective spare rows in the column address Step S . When the number of failures on one column is larger than the number of effective spare rows YES in Step S the failure analysis unit A determines that the column address and I O index is a column failure Step S .

The failure analysis unit A writes the repaired fail data in the fail data storage unit B Step S . The repaired fail data includes the redundancy allocation result indicating that the spare column is allocated to the column address and the I O index determined as the column failure in Step S.

The failure analysis unit A masks the failure of the column address and the I O index indicated by the repair fail data written in Step S Step S . shows the result in Step S.

On the other hand when the number of failures on one column address and the I O index is not more than the number of effective spare rows NO in Step S the processes in Steps S to S are not performed to the column address and the I O index.

The failure analysis unit A determines whether or not the processes in Step S to S to all the pieces of column fail data stored in the fail data storage unit B are completed Step S . When the processes in Steps S to S to all the pieces of column fail data are completed YES in Step S the column repair analysis process of the first embodiment of the present invention is completed.

The failure analysis unit A refers to the column fail data stored in the fail data storage unit B to determine that the row address or column address and I O index in which the failure exists is the row failure or column failure Step S .

The failure analysis unit A writes the repaired fail data in the fail data storage unit B Step S . The repaired fail data includes the redundancy allocation result indicating that the spare row or spare column is allocated to the row address or column address and I O index which is determined as the row failure or column failure in Step S.

The failure analysis unit A masks the failure of the row address or column address and I O index which is indicated by the repair fail data written in Step S Step S .

The failure analysis unit A determines whether or not the processes in Steps S to S are performed until there are no spares Step .

When the processes in Steps S to S are performed until there are no spares YES in Step S the flow goes to Step S.

The failure analysis unit A determines whether or not there are no failures NO in Step S . When there is no remaining spare but a failure exists the failure analysis unit A determines that the repair is impossible Step S .

The whole repair analysis process of the first embodiment of the present invention is completed when there are no failures YES in Step S or the whole repair analysis process is completed after the process in Step S. shows the result of the whole repair analysis process.

Alternatively in the first embodiment of the present invention the number of pieces of fail data written in the fail data storage unit B by the failure analysis unit A is variable and the optimum number of pieces of fail data may be selected according to a scale of the memory A and a scale of the BIRA unit .

In accordance with the first embodiment of the present invention the BIRA unit including the failure analysis unit A and the fail data storage unit B performs the repair analysis process of the memory A without producing a complete fail bitmap so that the time to process the memory test of the memory A can be shortened without enlarging the hardware scale. Particularly in accordance with the first embodiment of the present invention the BIRA unit is connected to the BIST unit and performs the failure analysis process according to the failure detected by the BIST unit so that the increase in hardware scale can be restrained to the minimum.

Additionally in accordance with the first embodiment of the present invention the test cost can be optimized when the upper limit of the memory test is fixed.

A second embodiment of the present invention will be described below. The on chip failure analysis circuit of the first embodiment of the present invention includes the BIRA unit having the repair analysis circuit which analyzes the necessity of redundancy allocation and the redundancy allocation result according to the numbers of spare columns and spare rows of the memory. On the other hand an on chip failure analysis circuit of the second embodiment of the present invention includes a BISD unit. The BISD unit includes a fault diagnosis circuit which diagnoses a type of the failure according to the number of failures and a lower limit of the number of failures. The description of the contents similar to those of the first embodiment of the present invention is neglected.

A configuration of an on chip failure analysis circuit of the second embodiment of the present invention will be described first.

The on chip failure analysis circuit includes a BIST unit a memory collar and a BISD unit . The on chip failure analysis circuit is connected to a test apparatus .

The BIST unit runs a self test of a memory A. The BIST unit outputs the data the address row address and column address and the control signal to the memory A to control the memory A so as to perform a reading operation and a writing operation. The BIST unit outputs an expected value of the memory output in the reading operation of the memory A to a failure detection unit B. The BIST unit outputs the address of the memory A in which the failure is detected to the failure analysis unit A.

The memory A performs the reading operation and the writing operation according to the data address and control signal which are output from the BIST unit .

The failure detection unit B compares the memory output of the memory A to the expected value output from the BIST unit to detect the failure of the memory output.

The BISD unit includes a failure analysis unit A a fail data storage unit B and an analysis result output unit C.

When the failure detection unit B detects the failure the failure analysis unit A performs an analysis using the address output from the BIST unit to write column fail data in the fail data storage unit B. The column fail data includes a failure location column address and I O index and the number of failures. The failure analysis unit A includes a fault diagnosis circuit. The fault diagnosis circuit analyzes the number of failures detected by the failure detection unit B with respect to the row address. The fault diagnosis circuit performs a row fault diagnosis process according to the analysis result and a lower limit of the number of row failures. In the row fault diagnosis process the fault diagnosis circuit makes a determination of the type of the row failure. The fault diagnosis circuit analyzes the number of failures with respect to the column address and I O index after the row fault diagnosis process. The fault diagnosis circuit performs a meta fault diagnosis process according to the analysis result and a lower limit of the number of meta failures. In the meta fault diagnosis process the fault diagnosis circuit determines whether or not the failure is the meta failure. The fault diagnosis circuit analyzes the number of failures with respect to the column address and I O index after the meta fault diagnosis process. The fault diagnosis circuit performs a column fault diagnosis process according to the analysis result and a lower limit of the number of column failures. In the column fault diagnosis process the fault diagnosis circuit makes a determination of the column failure or a combination of the failure types. The fault diagnosis circuit writes analysis result in the fail data storage unit B. The analysis result includes pieces of diagnosis result information indicating the determination results. The analysis result includes not only the determination results of the row failure meta failure and column failure but also the combination of the failure types including the bit failure.

The fail data storage unit B is a circuit that can store the fail data written by the failure analysis unit A and can have plural pieces of data of the same bit.

The analysis result output unit C reads the analysis result stored in the fail data storage unit B and outputs the analysis result to the test apparatus .

The test apparatus which is of an external device controls an input signal of the BIST unit and observes an output signal of the BIST unit . The test apparatus also reads the analysis result output from the analysis result output unit C.

Alternatively in the second embodiment of the present invention the on chip failure analysis circuit may include plural BISD units .

In the second embodiment of the present invention as shown in an upper limit Nrf of the number of row failures an upper limit Ncf of the number of column failures and an upper limit Nmf of the number of meta failures are predetermined circuit parameters and it is assumed that Nrf 2 Ncf 2 and Nmf 2.

The BIST unit runs a column first test up to predetermined times Step S . The first column test preferentially controls the column address of the memory A.

The failure detection unit B compares the memory output and the expected value output from the BIST unit to detect the failure of the memory output Step S .

The failure analysis unit A performs a row fault diagnosis process Step S of a meta fault diagnosis process Step of and a column fault diagnosis process Step S of as described later.

The analysis result output unit C reads the analysis result stored in the fail data storage unit B and outputs the analysis result to the test apparatus Step S .

Alternatively in the second embodiment of the present invention the memory test process may be run once or the memory test process may be run up to the predetermined times.

Additionally in the second embodiment of the present invention in Step S the first column test and the first row test may mutually be run.

Additionally in the second embodiment of the present invention in the case of the plural BISD units the memory test may simultaneously be processed or the memory test may sequentially be processed.

The failure analysis unit A refers to the number of failures detected in Step S of and the row addresses in which the failures exist to determine whether or not the number of failures is larger than the upper limit Nrf of the number of row failures Step S . When the number of failures is larger than the upper limit Nrf of the number of row failures YES in Step S the failure analysis unit A determines that the row address has a row failure Step S .

The failure analysis unit A writes the diagnosis result information in the fail data storage unit B Step S . The diagnosis result information includes the determination result indicating that the row address determined as the row failure in Step S is the row failure.

The failure analysis unit A masks the failure of the row address indicated by the diagnosis result information written in Step S Step S . shows the state in Step S.

On the other hand when the number of failures is not more than the upper limit Nrf of the number of row failures NO in Step S the processes in Steps S to S are not performed to row address.

The failure analysis unit A determines whether or not the processes in Steps S to S to all the rows are completed NO in Step S . When the processes in Steps S to S to all the rows are completed YES in Step S the row fault diagnosis process of the second embodiment of the present invention is completed.

The failure analysis unit A determines whether or not the number of column failures is larger than an upper limit Nmf of the number of meta failures Step S . When the number of column failures is larger than an upper limit Nmf of the number of meta failures YES in Step S the failure analysis unit A determines that the memory A has the meta failure Step S .

The failure analysis unit A writes the diagnosis result information in the fail data storage unit B S . The diagnosis result information includes the determination result indicating that the memory A has the meta failure.

On the other hand when the number of column failures is not more than an upper limit Nmf of the number of meta failures NO in Step S the processes in Steps S and S is not performed.

The failure analysis unit A writes the column fail data in the fail data storage unit B Step S . The column fail data includes the number of failures except for the failure masked in Step S of and the column addresses and the I O index in which the failures exist. shows the result in Step S.

The failure analysis unit A refers to the column fail data written in Step S to determine whether or not the number of failures on the column address and I O index is larger than an upper limit Ncf of the number of column failures Step S . When the number of failures on the column address and I O index is larger than the upper limit Ncf of the number of column failures YES in Step S the failure analysis unit A determines that the column address and I O index has a column failure Step S .

The failure analysis unit A writes the diagnosis result information in the fail data storage unit B Step S . The diagnosis result information includes the determination result indicating that the column address and the I O index determined as the column failure in Step S is the column failure.

The failure analysis unit A masks the failure of the column address and the I O index indicated by the diagnosis result information written in Step S Step S . shows the result in Step S.

On the other hand when the number of failures is not more than the upper limit Ncf of the number of column failures NO in Step S the processes in Steps S to S are not performed to the column address and the I O index.

The failure analysis unit A determines whether or not the processes in Steps S to S to all the pieces of column fail data stored in the fail data storage unit B are completed Step S . When the processes in Steps S to S to all the pieces of column fail data are completed YES in Step S the column fault diagnosis process of the second embodiment of the present invention is completed.

The failure which is not determined as any one of types of the failures row failure meta failure and column failure in the processes of is determined as the bit failure.

Alternatively in the second embodiment of the present invention the number of pieces of fail data written in the fail data storage unit B by the failure analysis unit A is variable and the optimum number of pieces of fail data may be selected according to a scale of the memory A and a scale of the BISD unit .

In accordance with the second embodiment of the present invention the BISD unit including the failure analysis unit A and the fail data storage unit B performs the fault diagnosis process of the memory A independently of an external program and without compressing the fail data so that the time to process the memory test of the memory A can be shortened without enlarging the hardware scale. Particularly in accordance with the second embodiment of the present invention the BISD unit is connected to the BIST unit and performs the fault diagnosis process according to the failure detected by the BIST unit so that the increase in hardware scale can be restrained to the minimum.

Additionally in accordance with the second embodiment of the present invention the test cost can be optimized when the upper limit of the memory test is fixed.

A third embodiment of the present invention will be described below. In the on chip failure analysis circuits of the first and second embodiments of the present invention one of the repair analysis circuit and the fault diagnosis circuit is connected to the BIST unit. On the other hand in an on chip failure analysis circuit of the third embodiment of the present invention both the repair analysis circuit and the fault diagnosis circuit are connected to the BIST unit. The description of the contents similar to those of the first and second embodiments of the present invention is neglected.

The on chip failure analysis circuit includes a BIST unit a memory collar and a BIRA and BISD unit . The on chip failure analysis circuit is connected to a test apparatus .

The BIST unit runs a self test of a memory A. The BIST unit outputs the data the address row address and column address and the control signal to the memory A to control the memory A so as to perform a reading operation and a writing operation. The BIST unit outputs an expected value of the memory output in the reading operation and writing operation of the memory A to a failure detection unit B. The BIST unit outputs the address of the memory A in which the failure is detected to failure analysis units A and B.

The memory A is a semiconductor memory device having a two dimensional redundant structure including a spare column and a spare row. The memory A performs the reading operation and the writing operation according to the data address and control signal which are output from the BIST unit .

The failure detection unit B compares the memory output of the memory A to the expected value output from the BIST unit to detect the failure of the memory output.

The BIRA and BISD unit includes the failure analysis units A and B a fail data storage unit C and an analysis result output unit D.

When the failure detection unit B detects the failure the failure analysis unit A performs an analysis using the address output from the BIST unit to write column fail data in the fail data storage unit C. The column fail data includes a failure location column address and I O index and the number of failures. The failure analysis unit A analyzes the number of failures detected by the failure detection unit B with respect to the row address. The failure analysis unit A performs the row repair analysis process according to the analysis result and the number of effective spare columns of the memory A. The failure analysis unit A performs the column repair analysis process according to the column fail data stored in the fail data storage unit C and the number of effective spare rows of the memory A. The failure analysis unit A includes a repair analysis circuit. The repair analysis circuit analyzes the necessity of redundancy allocation and the redundancy allocation result in the row repair analysis process and the column repair analysis process to write the repair fail data including the analysis result in the fail data storage unit C.

When the failure detection unit B detects the failure the failure analysis unit B performs an analysis using the address output from the BIST unit to write the column fail data in the fail data storage unit C. The column fail data includes the failure location column address and I O index and the number of failures. The failure analysis unit B includes a fault diagnosis circuit. The fault diagnosis circuit analyzes the number of failures detected by the failure detection unit B with respect to the row address. The fault diagnosis circuit performs the row fault diagnosis process according to the analysis result and the lower limit of the number of row failures. In the row fault diagnosis process the fault diagnosis circuit makes a determination of the type of the row failure. The fault diagnosis circuit analyzes the number of failures with respect to the column address and I O index after the row fault diagnosis process. The fault diagnosis circuit performs the meta fault diagnosis process according to the analysis result and the lower limit of the number of meta failures. In the meta fault diagnosis process the fault diagnosis circuit determines whether or not the failure is the meta failure. The fault diagnosis circuit analyzes the number of failures with respect to the column address and I O index after the meta fault diagnosis process. The fault diagnosis circuit performs the column fault diagnosis process according to the analysis result and the lower limit of the number of column failures. In the column fault diagnosis process the fault diagnosis circuit makes a determination of the column failure or a combination of the failure types. The fault diagnosis circuit writes analysis result in the fail data storage unit C. The analysis result includes pieces of diagnosis result information indicating the determination results. The analysis result includes not only the determination results of the row failure meta failure and column failure but also the combination of the failure types including the bit failure.

The BIST unit the memory collar the fail data storage unit C and the analysis result output unit D and the information stored in the fail data storage unit C are shared by the failure analysis units A and B.

The fail data storage unit C is a circuit that can store the fail data written by the failure analysis units A and B and can have plural pieces of data of the same bit.

The analysis result output unit D reads the fail data including the repair fail data or diagnosis result information stored in the fail data storage unit C. Then the analysis result output unit D selectively outputs the repair fail data or the diagnosis result information to the test apparatus .

The test apparatus which is of an external device performs a predetermined test according to the fail data output from the analysis result output unit D.

Alternatively in the third embodiment of the present invention the on chip failure analysis circuit may include plural BIRA and BISD units .

The memory test of the third embodiment of the present invention is similar to those of the first and second embodiments of the present invention so that the description is neglected.

In according with the third embodiment of the present invention the BIST unit the memory collar the fail data storage unit C and the analysis result output unit D and the information stored in the fail data storage unit C are shared by the failure analysis units A and B. Therefore the time to process the test of the memory A can be shortened without enlarging the hardware scale. The test includes the on chip analysis of the repair analysis and fault diagnosis. Particularly in the third embodiment of the present invention the repair analysis process and the fault diagnosis process are performed by the one BIRA and BISD unit so that the time to process the memory test can be largely shortened.

