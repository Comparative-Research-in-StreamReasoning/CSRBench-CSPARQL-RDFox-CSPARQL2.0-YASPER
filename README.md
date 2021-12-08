CSRBench-oracle (extended with RDFox, YASPER, and C-SPARQL2.0)
===================
**Requirements:**
 * Java 7+
 * Maven

**License:**
 * The code is released under the Apache 2.0 license

**The project has five main files:**
* (eu.planetdata.srbench.oracle.engineRDFox.)**RDFoxWrapper**: Simulates the RDF streams and executes the queries with the RDFox engine. Executing this class produces the RDFox answers. To run the RDFox Wrapper, you will need to provide the path to a license-file as command line parameter.
* (eu.planetdata.srbench.oracle.engineCSPARQL2.)**CSPARQL2Wrapper**:  Simulates the RDF streams and executes the queries with the YASPER engine. Executing this class produces the YASPER answers.
* (eu.planetdata.srbench.oracle.engineYASPER.)**YASPERWrapper**:  Simulates the RDF streams and executes the queries with the C-SPARQL2.0 engine. Executing this class produces the C-SPARQL2.0 answers.
* (eu.planetdata.srbench.oracle.repository.)**SRBenchImporter**: Prepares the necessary data for the RDF Repository (is necessary for the Oracle to work).
* (eu.planetdata.srbench.oracle.)**Oracle**: Executes the test queries over the RDF stream, produces the results. If a result to be compared is provided, the Oracle verifies that it is correct.


**Configuration:**
 * The project can be configured editing the setup.properties file. See <https://github.com/dellaglio/csrbench-oracle/wiki/Configuration> for a description of the properties.
 * An additional query parameter, srb.query_i_.rspqlquery is provided. Those queries are used by C-SPARQL2.0 and YASPER in order to provide answers.

**Execute the RDFoxWrapper:**
 * RDFoxWrapper executes the queries that are specified in setup.properties
 * RDFoxWrapper saves the answers into 'src/main/resources/answers/' folder
 * In order to work, the JRDFox.jar must be integrated into the project + a path to a RDFox licence-file must be provided as commandline parameter
 * RDFoxWrapper is able to execute every query after each other correctly, if the execution of every query if configured
 
 
**Execute the CSPARQL2Wrapper:**
 * CSPARQL2Wrapper executes the query specified in setup.properties
 * CSPARQL2Wrapper saves the answers into 'src/main/resources/answers/' folder
 * In order to work, the C-SPARQL2.0 engine must be integrated into the project
 * CSPARQL2Wrapper is only able to execute one query after each other correctly

**Execute the YASPERWrapper:**
* YASPERWrapper executes the query specified in setup.properties
* YASPERWrapper saves the answers into 'src/main/resources/answers/' folder
* In order to work, the YASPER engine must be integrated into the project
* YASPERWrapper is only able to execute one query after each other correctly
 
 
**Setup the repository for the oracle:**
 * It is done through the SRBenchImporter
 * Data should be described in Turtle and it should be stored in the folder data. Filenames should follow the pattern data_xx.ttl, where xx is the application timestamp associated to the triples in the file.

**Execute the Oracle:**
 * Run the Oracle. Depending on the setup configuration, for each query to be executed, two possible behaviours are possible:
  * If there is no answer associated to the query, the oracle produces all the possible answers according to the input configuration;
  * If there is an answer associated to the query, the oracle starts to produce an answer and comparing it with the input one. If it finds a match, it stops, otherwise it repeats.
 * When the Oracle runs, it creates a html-file with a summary of the tests and the results.
