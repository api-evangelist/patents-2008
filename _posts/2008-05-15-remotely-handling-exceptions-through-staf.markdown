---

title: Remotely handling exceptions through STAF
abstract: An apparatus for communicating between a child test program and a parent test program in a test environment. A child test framework is provided to catch an exception thrown by the child test program. In addition, a marshalling component is provided in communication with the child test program and the child test framework. The marshalling component converts exception data for the exception into a format for transmission by a communication means to a parent test framework.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08239837&OS=08239837&RS=08239837
owner: International Business Machines Corporation
number: 08239837
owner_city: Armonk
owner_country: US
publication_date: 20080515
---
The present invention relates to a technology for controlling parent and child tests in test suites and in particular for enabling failures in child tests to be more efficiently handled.

One of the hardest things to do in test environments is to know how to handle test failures. Some tests may fail for a variety of reasons some of which may be acceptable or even expected as for example in testing the correctness of a program s response to incorrect inputs and others are not. Generally this is handled with return codes. Return codes are very difficult to manage. If tests are calling other tests then the higher level tests will often need to know how to handle a great number of different return codes in different situations. Generally this is ignored and tests end up returning only a pass fail value and losing a lot of information in how the test failed. To find out exactly how a specific test failed may require a parse of its logs which is both difficult and time consuming.

It would thus be desirable to have a technology for controlling parent and child tests in test suites and in particular for enabling failures in child tests to be more efficiently handled.

In one aspect of the invention an apparatus is provided for communicating between a child test program and a parent test program in a test environment. A child test framework operable to catch an exception thrown by the child test program is provided. In addition a marshalling component operable in communication with the child test program and the child test framework is provided to convert exception data for the exception into a format for transmission by a communication means to a parent test framework.

In another aspect of the invention a method is provided for communicating between a child test program and a parent test program in a test environment. A child test framework catches an exception thrown by the child test program. Thereafter a marshalling component in communication with said child test program and the child test framework converts exception data for the exception into a format for transmission by a communication means to a parent test framework.

In yet another aspect of the invention a computer program comprising computer program code is provided to when loaded into a computer system and executed thereon cause the computer system to communicate between a child program and a parent test program. Computer code in the form of program test code is provided to catch an exception thrown by the child test program. In addition program code in communication with the program test code is provided to convert exception data for the exception into a format for transmission by to a parent test framework. Conversion of the exception data is performed by a marshalling component operable in communication with the child test program and the child test framework. The conversion converts exception data for the exception into a format for transmission by a communication means to a parent test framework. In addition instructions are provided to return exception data communicated to the parent test for identifying a cause of failure in the child test program.

Preferred embodiments of the invention thus contemplate in their broadest aspect a technology for controlling parent and child tests in test suites and in particular for enabling failures in child tests to be more efficiently handled.

A preferred embodiment of the invention is suitably implemented in a test environment in which a harness or framework is provided using for example the well known Software Testing Automation Framework or STAF .

In test environments controlled by a STAF framework the presently known process performed by one test executing another test and retrieving its success disposition is 

A use exception is an informative mechanism used to state the causes of test failures. If a test provided with exception facilities ends without throwing an exception then it has passed otherwise it fails. This gives the following significant advantages 

1. Test can pass failures upwards without explicitly writing code to do so simply by not handling exceptions of that type.

2. Test can handle failures in a very generic way via inheritance so higher level tests don t need to worry about specifics of lower level tests.

Environments such as STAF do a lot of the hard work involved in automating test suites and so are very attractive to use for launching tests. They provide services such as process invocation inter process communication semaphores logging and so on.

However these environments conventionally do not have a mechanism to allow exceptions to escalate upwards because the runtime frameworks for tests isolate the tests from one another. If a process launched under STAF terminates as a result of an exception the exception may or may not appear in the standard error output. The owning process also known as the parent test is not notified and is thus not enabled to take any action on the basis of the child exception.

In one embodiment exceptions are allowed to be marshalled that is wrapped up into the STAF return data to be picked up safely at the other end into the STAF process return message and then translated back into exceptions and thrown in the calling process. This would then look as if the exception had happened locally and everything was running in one place simplifying everything greatly for the test case writer.

However this solution is not trivial as it requires the exceptions to be caught. The encapsulation provided by STAF itself does not allow processes such as child tests access to their marshalled return data. Furthermore at the parent test program end the exceptions must be reconstructed and re thrown smoothly so as not to have significant time delay and to ensure that the parent test program does in fact receive the exceptions instead of just ignoring them.

In one embodiment of the present invention a test framework is provided to wrap up the process invocation and control methods to provide a simple mechanism to pass exceptions between entities.

In a preferred embodiment of the present invention parent test program goes through the following stages 

Once step d is complete without itself failing the test may return to step a again or end successfully.

The following is pseudo code written in Java Java and all Java related trademarks and logos are trademarks of Sun Microsystems Inc. in the United States of America and other countries . The method exposed to the parent test program to launch a child test program in one embodiment comprises 

The difference between the runTestInSequence and runTestInParallel methods is as follows. In one embodiment if a child test program is to be run synchronously the runTestInSequence method is called and this is translated to the STAF request as follows 

START COMMAND java PARMS com.ibm.staf.framework.Framework testcasename ASYNC SAMECONSOLE RETURNSTDOUT RETURNSTDERR NOTIFY ONEND WAIT 

Running a test in parallel is very similar to running a test in sequence. In one embodiment the method used is called for example runTestInParallel and it returns immediately with a process ID. The parent test program then needs to explicitly wait for the process itself afterwards using the following method 

The test is allowed to wait for more than one process to end using a different method . In all cases if there is a failure a return code is not used and instead an exception is thrown of a subtype of TestFrameworkException. If the test passes then an object of type ProcessReturnData is returned this is simply an object containing the marshalled up STAF information.

Turning now to child test program is being executed via STAF within the thin layer of the framework . The child test program can exit in one of two ways 

For exemplary purposes assume the child test program throws an exception. At this point a new facility within the framework around the child test program catches the exception at FLOW . As mentioned above it is desirable to be able to marshall up all the data from the exception into the STAF return data and return that. However in a conventional system the marshalled data is not accessible to the child test as it is owned by the service that executed it. The only way it can be communicated to the parent process is through standard out error which is picked up by the process service and marshalled up and returned to the parent.

The framework of the preferred embodiment encodes the exception data in the STAF return data. Therefore the information contained in the exception is now converted to a string format and printed out in the standard error stream. However if the child test program that has been run has thrown an exception this will also appear in the standard error output. Therefore before any exception can be output the system must print out a delimiter that limits the scope of any later search for exceptions in the standard error output to just the relevant process. This is because a child test program may itself run a further test process a grandchild test which may have returned an exception that has been handled. The original parent needs to be able to distinguish such a grandchild exception in the error output so that it can ignore it and only deal with the exception thrown by its own child.

The framework in which the child process executed then terminates and STAF picks up the marshalled data at FLOW .

The Return code is picked up from STAF by the parent process. Finally the PROCESS command returns to the parent test program with the marshalled data. The framework in which the parent test program is executing picks this information up FLOW and decodes it back into an exception. The parent framework picks up the standard error stream and searches backwards through it until either 

If an exception is found the framework parses it and may then create a new exception of the same type but filling in all the data the same as the original exception and then throwing it. This occurs in the example from the method call runTestInSequence to invoke the test if the invocation was done synchronously or from the waitForProcess method if the invocation was done asynchronously . Otherwise those methods just return the marshalled data to the parent test program at FLOW .

In one embodiment of the present invention in the form of an apparatus or arrangement of apparatus advantageously addresses the problem of providing a technical means for controlling parent and child tests in test suites and in particular for enabling failures in child tests to be efficiently handled.

In child framework child test program is in communication with both the child framework and with marshaller which is operable to marshall the exception data and pass it to transmitter which communicates it via STAF to the parent framework . In parent framework unmarshaller receives the marshalled data and unmarshalls it passing the unmarshalled data to exception returner component which then returns the unmarshalled exception data to parent test program for processing.

Turning now to there are shown in flowchart form the steps of a method or logic arrangement according to a preferred embodiment of the present invention.

In the method or logic arrangement includes steps beginning at START step . At step the parent test framework is started and at step the parent test program is started. At step a request to run a child test program is issued and the child test program begins execution inside a child framework. At decision step if no an exception has been thrown in the child test the process of handling exceptions ends. If however an exception is thrown in the child test at step the child framework catches the exception and at step marshalls the exception data. At step the exception data and a delimiter to limit the scope of the later search for exception data in the output to the scope of the parent s child process are output. At step the child framework terminates as it has completed its work of providing a runtime environment for the now terminated child test. At step the parent framework receives and unmarshalls the exception data delimited as within the scope of the child test. At step the corresponding exception is thrown in the parent test. The method according to the preferred embodiment then completes at END step .

The preferred embodiment of the present invention in the form of a method or logic arrangement thus advantageously addresses the problem of providing a technical means for controlling parent and child tests in test suites and in particular for enabling failures in child tests to be more efficiently handled.

The method in one embodiment receives by a first parent test framework component the converted exception data from the communication means converts by a second parent test framework component the exception data back from the format for transmission and returns the converted exception data for processing by the parent test. The parent test program and the child test program form a portion of a hierarchy of a plurality of tests and wherein the child test framework and the parent test framework form a portion of a hierarchy of a plurality of test frameworks. In one embodiment the parent test program invokes the child test program in synchronous mode. Similarly in one embodiment the communication means communicates using a standard error output stream and inserts the exception data and one of a marker or a delimiter into the standard error output stream. The marker or delimiter comprises an indication that exception data relates to a child test program of a determined parent test.

It will be clear to one of ordinary skill in the art that all or part of the method of the preferred embodiments of the present invention may suitably and usefully be embodied in a logic apparatus or a plurality of logic apparatus comprising logic elements arranged to perform the steps of the method and that such logic elements may comprise hardware components firmware components or a combination thereof.

The apparatus further comprises a first parent test framework component operable to receive the converted exception data from the communication means a second parent test framework component operable to convert the exception data back from the format for transmission and an exception return component for returning the converted exception data for processing by the parent test. In one embodiment the child test framework and the parent test framework comprise a modified STAF. Furthermore in one embodiment parent test program and the child test program form a portion of a hierarchy of a plurality of tests and wherein the child test framework and the parent test framework form a portion of a hierarchy of a plurality of test frameworks. The parent test program may be operable to invoke the child test program in synchronous mode. In one embodiment the communication means is operable to communicate using a standard error output stream and wherein the communication means inserts the exception data and a marker or a delimiter into the standard error output stream. In one embodiment the marker or delimiter comprises an indication that exception data relates to a child test program of a determined parent test.

It will be equally clear to one of skill in the art that all or part of a logic arrangement according to the preferred embodiments of the present invention may suitably be embodied in a logic apparatus comprising logic elements to perform the steps of the method and that such logic elements may comprise components such as logic gates in for example a programmable logic array or application specific integrated circuit. Such a logic arrangement may further be embodied in enabling elements for temporarily or permanently establishing logic structures in such an array or circuit using for example a virtual hardware descriptor language which may be stored and transmitted using fixed or transmittable carrier media.

It will be appreciated that the method and arrangement described above may also suitably be carried out fully or partially in software running on one or more processors not shown in the figures and that the software may be provided in the form of one or more computer program elements carried on any suitable data carrier also not shown in the figures such as a magnetic or optical disk or the like. Channels for the transmission of data may likewise comprise storage media of all descriptions as well as signal carrying media such as wired or wireless signal carrying media.

The present invention may further suitably be embodied as a computer program product for use with a computer system. Such an implementation may comprise a series of computer readable instructions either fixed on a tangible medium such as a computer readable medium for example diskette CD ROM ROM or hard disk or transmittable to a computer system via a modem or other interface device over either a tangible medium including but not limited to optical or analogue communications lines or intangibly using wireless techniques including but not limited to microwave infrared or other transmission techniques. The series of computer readable instructions embodies all or part of the functionality previously described herein.

Those skilled in the art will appreciate that such computer readable instructions can be written in a number of programming languages for use with many computer architectures or operating systems. Further such instructions may be stored using any memory technology present or future including but not limited to semiconductor magnetic or optical or transmitted using any communications technology present or future including but not limited to optical infrared or microwave. It is contemplated that such a computer program product may be distributed as a removable medium with accompanying printed or electronic documentation for example shrink wrapped software pre loaded with a computer system for example on a system ROM or fixed disk or distributed from a server or electronic bulletin board over a network for example the Internet or World Wide Web.

In an alternative the preferred embodiment of the present invention may be realized in the form of a computer implemented method of deploying a service comprising steps of deploying computer program code operable to when deployed into a computer infrastructure and executed thereon cause the computer infrastructure to perform all the steps of the method.

In a further alternative the preferred embodiment of the present invention may be realized in the form of a data carrier having functional data thereon said functional data comprising functional computer data structures to when loaded into a computer system and operated upon thereby enable said computer system to perform all the steps of the method.

It will be clear to one skilled in the art that many improvements and modifications can be made to the foregoing exemplary embodiment without departing from the scope of the present invention.

