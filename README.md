# Using Graph Theory for Assessing Domain-Driven Design-based Microservices Architectures.


This repository offers supplementary information to assist in the research presented in the paper titled "_Using Graph Theory for Assessing Domain-Driven Design-based Microservices Architectures_". It contains technical specifications and findings related to implementing the proposed approach on four microservices projects based on DDD principles.

## Table of Content-

* [**Project Selection**](https://github.com/FrHassan/MicroservicesProjects#Project-Selection)
* [**Project Analysis**](https://github.com/FrHassan/MicroservicesProjects#Project-Analysis)  
   - [**Platform and Tools**](https://github.com/FrHassan/MicroservicesProjects#Platform-and-Tools)  
   - [**Application of the Methodology**](https://github.com/FrHassan/MicroservicesProjects#Application-of-the-Methodology)  
* [**DataSet: Microservices Projects**](https://github.com/FrHassan/MicroservicesProjects#DataSet:Microservices-Projects)  
* [**Your contribution**](https://github.com/FrHassan/MicroservicesProjects#Your-contribution)  
* [**References**](https://github.com/FrHassan/MicroservicesProjects#References)


## Project Selection

The projects on which the approach is implemented are chosen based on two primary criteria:

* **Decomposition strategy:** The microservices project follow the DDD principle [[3]](https://github.com/FrHassan/MicroservicesProjects#References) for their microservices boundaries identification.

* **Documentation:** The chosen projects have thorough documentation and provide information on their design and implementation."

## Project Analysis
### Platform and Tools

The main utilized tool to apply the methodology is Neo4j [[4]](https://neo4j.com/).

Neo4j offers three main tools to perform graph manipulate graphs: 

* **Neo4j Browser [[5]](https://neo4j.com/developer/neo4j-browser/):** A tool to interact and manipulate graphs. 
* **Neo4j Bloom [[6]](https://neo4j.com/product/bloom/):** A tool to interact visually with the graph.
* **Neo4j NEuler [[7]](https://neo4j.com/developer/graph-data-science/neuler-no-code-graph-algorithms/):** A playground to execute graph algorithms.

### Application of the Methodology

To apply the methodology, we kindly request that you adhere to the provided instructions below.

**1.** Install _Neo4j Desktop_ following the instructions mentioned in [[8]](https://neo4j.com/docs/desktop-manual/current/installation/download-installation/).  
**2.** Use _Neo4j Desktop_ to create a new graph database.  

<p align="center">
 <img src="Assets/Images/Neo4j Desktop Create DB.png" width="70%">
</p>

**3.** Under the database "_Plugins_" section, install "_APOC_" and "_Graph Data Science Library_". 
   - _Awesome Procedures On Cypher (APOC)_ [[9]](https://neo4j.com/labs/apoc/) adds a lot of useful_ Cypher_ functionalities that help manipulating the data. 
   - _Graph Data Science Library_ [[10]](https://neo4j.com/docs/graph-data-science/current/) will make it easier for us to execute the available Neo4j graph algorithms.

<p align="center">
 <img src="Assets/Images/Neo4j Desktop Plugins.PNG" width="70%">
</p>

**4.** Click on the "_Start_" button to run the database.  
   - Whenever the database is operational, Neo4j will indicate an active state with a green color.


<p align="center">
 <img src="Assets/Images/Neo4j Desktop DB Start.PNG" width="70%">
</p>

<p align="center">
 <img src="Assets/Images/Neo4j Desktop DB Starting.PNG" width="70%">
</p>

<p align="center">
 <img src="Assets/Images/Neo4j Desktop DB Running.PNG" width="70%">
</p>

**5.** Under the "_Open_" list, open _Neo4j Browser_.  
**6.** Create the microservices architecture associated graph using the "_Cypher_"  [[11]](https://neo4j.com/docs/cypher-manual/current/clauses/create/) (You can take inspiration from the code escorted to each existing project in this repository).
   - Now you can manipulate as you want the graph using _Cypher Query Language_ [[12]](https://neo4j.com/developer/cypher/).  

<p align="center">
 <img src="Assets/Images/Neo4j Desktop Create Graph.PNG" width="70%">
</p>

<p align="center">
 <img src="Assets/Images/Neo4j Desktop Match Graph.PNG" width="70%">
</p>

**7.** Under the "_Graph Apps_" section, open "Graph Data Science Playground" aka _NEuler_.  
   - In case _NEuler_ is absent from the list, you can install it using this url:: [https://neo.jfrog.io/neo/api/npm/npm/neuler](https://neo.jfrog.io/neo/api/npm/npm/neuler)
   - Copy the url and click on "Install".
<p align="center">
 <img src="Assets/Images/Neo4j Desktop Graph Apps.PNG">
</p>

**8.** With _NEuler_, you have the ability to utilize all the graph algorithms that are currently at your disposal.
   - Ensure that you activate the "Store result?" checkbox and make a note of the "Write Property" option as it will be utilized later to save the acquired outcomes.
   - The official documentation provides comprehensive information on all the Neo4j graph algorithms that are available [[13]](https://neo4j.com/docs/graph-data-science/current/algorithms/).

<p align="center">
 <img src="Assets/Images/NEuler Graph Algorithms.PNG" width="70%">
</p>

<p align="center">
 <img src="Assets/Images/Neo4j Desktop DB result.PNG">
</p>

<p align="center">
 <img src="Assets/Images/NEuler Algorithm Result.PNG" width="70%">
</p>

**9)** When accessing Neo4j Browser, employ the _Cypher_ match query [[14]](https://neo4j.com/docs/cypher-manual/4.4/clauses/match/) to retrieve the desired results. Following that, you have the option to export the results in a format of your choice, typically CSV.


<p align="center">
 <img src="Assets/Images/Neo4j Export CSV.PNG" width="70%">
</p>

**10)** Using the (.csv) file, you have the option to utilize a suitable tool in order to produce visual representations of your architectural data. 
   - In our case, we use _Microsoft Power BI Desktop_ [[15]](https://www.microsoft.com/fr-fr/download/details.aspx?id=58494) to generate our charts.
   - Example of a chart: [Food to Go (FTGO) - Degree analysis](https://github.com/FrHassan/MicroservicesProjects/blob/main/Microservices-Projects/Food%20to%20Go%20(FTGO)/Degree/FTGO%20Degree%20and%20Degree_Out%20(PNG).PNG)
   
<p align="center">
 <img src="https://github.com/FrHassan/MicroservicesProjects/blob/main/Microservices-Projects/Food%20to%20Go%20(FTGO)/Degree/FTGO%20Degree%20and%20Degree_Out%20(PNG).PNG" width="70%">
</p>

**Note**: _Neo4j Bloom_ will give you the possibility to explore and visualize your graph interactively. You can use it to provide a visual representation of your graph.

## DataSet:Microservices-Projects

The following table presents a comprehensive list of the current microservices projects. It also furnishes all the relevant details required for selecting a specific project.


Application name | Reference | Size | Languages | Used patterns | Known anti-patterns | Graph analysis (Link) | Comment (General info about decomposition technique or the style of communication used).

| Application name | Reference <sup>(Link)</sup> | Size | Languages | Known patterns | Known anti-patterns and notes  | Graph analysis <sup>(Link)</sup> | Comment |
| :---             |            :---:            | :---:|   :---:   |     :---:      |        :---:        |               :---:              | :---    |
| Food to Go (FTGO) | [**Ref:** FTGO](https://github.com/microservices-patterns/ftgo-application) | 14 | Java | <sup>Multiple patterns</sup> | <sup>Slight indicators on chattiness [[16]](https://github.com/FrHassan/MicroservicesProjects#References)</sup> | [**FTGO**](https://github.com/FrHassan/MicroservicesProjects/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)) | <sup>A reference example on microservices patterns implementation</sup> |
| Pitstop - Garage Management System | [**Ref:** Pitstop](https://github.com/EdwinVW/pitstop) | 8 | .NET and ASP.NET Core | <sup>CQRS, Event Sourcing, DDD</sup> | <sup>Slight indicators on thightness between Workshop Management and Costumer services</sup> | [**Pitstop**](https://github.com/FrHassan/MicroservicesProjects/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System) | <sup>Well documented and easy to understand</sup> |

## Your contribution

This repository functions as an open invitation extended to all practitioners, inviting them to actively contribute with their own microservices projects. We strongly urge you to join the community and share your valuable applications, playing a crucial role in the advancement of microservices architecture.

To disseminate your project, kindly adhere to the guidelines presented in the [_Project Analysis - Analysis Process_](https://github.com/FrHassan/MicroservicesProjects#analysis-process) section for project analysis. Subsequently, we request that you furnish, to the best of your ability, the specified information type outlined in the provided table. 




Another important piece of information is the name you want to be known with, in order to leave your mark as a participant in this work (^-^).

All data must be sent to at least one of the following emails: 
* HASSAN FARSI : <farsi.hassan@inpt.ac.ma> | <farsihassan.ing@gmail.com>
* ALLAKI DRISS : <d.allaki@inpt.ac.ma>

## References

[1] JAMSHIDI, Pooyan, PAHL, Claus, MENDONÇA, Nabor C., et al. Microservices: The journey so far and challenges ahead. IEEE Software, 2018, vol. 35, no 3, p. 24-35. 

[2] RICHARDSON, Chris. Microservices patterns: with examples in Java. Simon and Schuster, 2018.  

[3] EVANS, Eric. Domain-driven design: tackling complexity in the heart of software. Addison-Wesley Professional, 2004.  

[4] [https://neo4j.com/](https://neo4j.com/)  

[5] [https://neo4j.com/developer/neo4j-browser/](https://neo4j.com/developer/neo4j-browser/)  

[6] [https://neo4j.com/product/bloom/](https://neo4j.com/product/bloom/)  

[7] [https://neo4j.com/developer/graph-data-science/neuler-no-code-graph-algorithms/](https://neo4j.com/developer/graph-data-science/neuler-no-code-graph-algorithms/)  
[8] https://neo4j.com/docs/desktop-manual/current/installation/download-installation/  

[9] https://neo4j.com/labs/apoc/   

[10] https://neo4j.com/docs/graph-data-science/current/  

[11] https://neo4j.com/docs/cypher-manual/current/clauses/create/   

[12] https://neo4j.com/developer/cypher/  

[13] https://neo4j.com/docs/graph-data-science/current/algorithms/  

[14] https://neo4j.com/docs/cypher-manual/4.4/clauses/match/  

[15] https://www.microsoft.com/fr-fr/download/details.aspx?id=58494  

[16] FARSI, Hassan, ALLAKI, Driss, EN-NOUAARY, Abdeslam, et al. Following Domain Driven Design principles for Microservices decomposition: is it enough?. In : 2021 IEEE/ACS 18th International Conference on Computer Systems and Applications (AICCSA). IEEE, 2021. p. 1-8.  
