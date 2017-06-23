---

title: Generation of query language parameter file
abstract: Some aspects include determination of a data structure including a plurality of query language configuration parameters and at least two values associated with each of the plurality of query language configuration parameters, and generation, based on the data structure, of a first structured language query associated with a first value associated with one of the plurality of query language configuration parameters, and a second structured language query associated with a second value associated with the one of the plurality of query language configuration parameters. Also included are determination of a first expected query result associated with the first structured language query and a second expected query result associated with the second structured language query, query of a data source with the first structured language query and the second structured language query, reception of a first query result associated with the first structured language query and a second query result associated with the second structured language query, determination that the first query result matches the first expected query result and that the second query result does not match the second expected query result, and addition, to a query language configuration parameter file associated with the data source, of the one of the plurality of query language configuration parameters in association with the first value.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08386474&OS=08386474&RS=08386474
owner: SAP France S.A.
number: 08386474
owner_city: Levallois-Perret
owner_country: FR
publication_date: 20081124
---
A conventional business software application accesses data from disparate data sources. These data sources may include different types of relational database management systems RDBMSs legacy software systems and or other software systems. Ideally differences between the data sources are transparent to the business software application. In other words to provide simplicity and efficiency mechanisms are provided to enable the business software application to access each data source in an identical manner.

A software application typically accesses stored data by calling some type of middleware. This middleware in turn interacts with a connection server which is in communication with any number of different data sources. More particularly the connection server provides a common Application Programming Interface which is accessed by the middleware to access data of the different data sources.

Data source is a relational data source e.g. a RDBMS which supports structured query language i.e. SQL queries. However the particularities of the SQL supported by data source may differ from the particularities of the SQL supported by another data source. As an example some data sources support SQL and some do not.

Since the engine of query technique is generic regardless of the data source the system requires configuration information to address differences in the data sources such as that described above. Query language parameter file may address such differences by describing particularities of the SQL supported by data source . Parameter file is typically and primarily composed of three parts parameters which describe SQL syntax particularities e.g. case sensitive SORT BY syntax available operators e.g. addition subtraction and different kinds of supported functions e.g. CONCAT COUNT . Connection server may therefore use the information of parameter file to generate queries which conform to the particularities of the SQL supported by data source .

A new parameter file is required for each new data source to be added to system . Conventionally this file is manually created by analyzing documentation to determine whether the data source supports each parameter operator and function and by manually testing the data source to see how each parameter operator and function is supported. Many workdays are required to write and suitably test such a parameter file and the process is repeated for each new data source to be supported.

The following description is provided to enable any person in the art to make and use the described embodiments and sets forth the best mode contemplated for doing so. Various modifications will remain readily apparent to those in the art.

Data source may comprise any data source which is responsive to SQL queries. Data source may comprise a RDBMS from any vendor that is or becomes known. Embodiments may operate to generate a parameter file associated with data source . The parameter file may describe particularities of the query language supported by data source . Accordingly that a connection server may utilize the parameter file to generate SQL queries suitable for data source .

PRM tool may comprise executable program code to generate such a parameter file. As will be described in more detail below PRM tool generates queries and transmits the queries to data source via Java Database Connector JDBC although any relational middleware API e.g. Open Database Connectivity ODBC Object Linking and Embedding Database OLE DB etc. may be used in conjunction with some embodiments. PRM tool generates the queries based on information contained in master parameter data .

Master parameter data comprises a data structure including many query language configuration parameters and two or more values associated with each parameter. In some embodiments master parameter data aggregates two or more known parameter files which are respectively associated with two or more data sources. Master parameter data may include all known query language configuration parameters and all known values for each query language configuration parameter.

Master parameter data may comprise an eXtensible Markup Language XML file. As mentioned above each parameter of master parameter data may be associated with more than one value. According to some embodiments each parameter of master parameter data is defined as follows 

In a specific example it is known that some data sources support as the CONCAT operator and some data sources support as the CONCAT operator. Based on the foregoing XML schema master parameter data defines the CONCAT parameter as follows 

A parameter file may also include parameters associated with operators and functions. In another example a NUMBER TO CHAR x function is provided by to char x in some Oracle databases and by CAST X as CHAR in some Teradata databases. Accordingly master parameter data may include 

PRM tool generates queries based on master parameter data and also generates expected results associated with the generated queries. Generation of queries expected results according to some embodiments will be described below with respect to .

PRM tool generates new parameter file based on queries expected results . New parameter file is associated with data source and may be used to facilitate querying of data source in a system such as but not limited to system of . New parameter file may comprise an XML file associating a single value to each of many query language parameters. For example if data source does not support backquotes new parameter file may include the tag N.

According to some embodiments PRM tool also generates data source tests . Data source tests may include the queries used to generate new parameter file and the result of each query. Accordingly the queries of data source tests may be applied against a new data source and by comparing the results received from the new data source with the associated results stored in data source tests PRM tool may determine whether the new data source reflects the same SQL particularities as data source .

A data structure is initially determined at . The data structure includes a plurality of query language configuration parameters and at least two values associated with each of the plurality of query language configuration parameters. The data structure may comprise master parameter data of system . The data structure may be created prior to or during by obtaining parameter files associated with several data sources aggregating all parameters of the obtained parameter files and aggregating all values associated with each aggregated parameter.

For example the data structure may be created by obtaining an Oracle parameter file including the parameter NUMBER TO CHAR x in association with value to char x and a Teradata parameter file including the parameter NUMBER TO CHAR x in association with value CAST X as CHAR . The data structure aggregates the foregoing by associating the values to char x and CAST X as CHAR with the parameter NUMBER TO CHAR x . The aggregation may be represented in an XML structure as described above.

Next at a first structured language query is generated based on the data structure. The first structured language query is associated with a first value associated with one of the plurality of query language configuration parameters of the data structure. also includes generating a second structured language query that is associated with a second value associated with the one of the plurality of query language configuration parameters.

An example of is now provided with respect to the parameter CONCAT. It is assumed that the data structure includes the parameter CONCAT in association with values and . As described above the data structure may store an XML representation of this association as follows 

According to this example the first structured language query generated at may be SELECT a b and the generated second structured language query may be SELECT a b .

A first expected query result associated with the first structured language query is determined at and a second expected query result associated with the second structured language query is also determined at . Continuing with the above example both the first and second expected query results are indicators of success. The data source is queried with the first structured language query and with the second structured language query at e.g. using JDBC and first and second query results are received at . The first query result is associated with i.e. results from the first structured language query and the second query result is associated with the second structured language query.

According to process it is determined at that the first query result matches the first expected query result and that the second query result does not match the second expected query result. In the present example the first query was successful and the second query was unsuccessful. More specifically the data source uses for the CONCAT operator and does not use 

Depending on the queries and the data source may comprise a determination that the first query result does not match the first expected query result and that the second query result matches the second expected query result. Of course both or neither of the first query result and the second query result may match their corresponding expected query results.

The query language configuration parameter is added in association with the first value to a query language configuration parameter file at . The query language configuration parameter file is associated with the queried data source and may comprise new parameter file in some embodiments. To complete the current example the XML code may be added to the file at .

Flow may return to to process another parameter and associated values from the data structure. A parameter and one or more associated values are added to the parameter file during each iteration of process .

In some embodiments each query and query result generated during process is stored in data source tests . Data source tests thereby define the behavior of the data source in response to the queries. is a block diagram of system including data source and data source tests which were generated by applying process to a different data source. System may be used to determine whether new data source behaves similarly to the different data source.

More particularly testing tool e.g. a software application may read a query and its associated expected result from data source tests . Testing tool may apply the query against data source using JDBC . Testing tool receives a corresponding query result and compares the result to the expected result that was read from data source tests . Results of the comparison may be stored in test results . Test results may therefore indicate differences between the particularities of the query language supported by data source and those of the query language supported by the data source from which data source tests were generated.

The data structure of process may also include parameters representing operators and functions. For each operator or function of the data structure embodiments of process may employ the following strategy 

If the query succeeds the function f with the translation FMis supported. The function and the translation are therefore added to the query language configuration parameter file at . Of course a function supported by the data source cannot be added to the query language configuration parameter file if the function is not specified in the initial data structure e.g. master parameter data . Similarly process will not add a parameter to the parameter file if the parameter is not present in the initial data structure.

Comparison tool also receives new parameter file which may be intended for use with the particular data source. Comparison tool compares test parameter file and new parameter file and outputs the results of the comparison to comparison results . System thereby provides a determination of the suitability of new parameter file with the particular data source.

The embodiments described herein are solely for the purpose of illustration. Those in the art will recognize that other embodiments may be practiced with modifications and alterations limited only by the claims.

