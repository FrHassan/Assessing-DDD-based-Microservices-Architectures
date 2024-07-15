# Food to Go (FTGO)

This section provides a graph analysis for the FTGO microservices application. All the charts and figures appearing below are provided within the application project possibly in different formats. In the following we present only the necessary set of information about the graph metrics. However, the application project may contain addition figures and data about the concerned application analysis.

## Table of Contents

* [**Overview**](https://github.com/FrHassan/MicroservicesProjects#Introduction)  
* [**FTGO Graph Analysis**](https://github.com/FrHassan/MicroservicesProjects#Problematic)  
   - [**Application Associated Graph**](https://github.com/FrHassan/MicroservicesProjects#Platform-and-Tools)  
   - [**Graph Metrics**](https://github.com/FrHassan/MicroservicesProjects#Analysis-Process)  
* [**Discussion: Microservices Projects**](https://github.com/FrHassan/MicroservicesProjects#DataSet:-Microservices-Projects)   
* [**References**](https://github.com/FrHassan/MicroservicesProjects#References)


## Overview

Food to Go (FTGO) [[1]](https://github.com/microservices-patterns/ftgo-application) is a java example microservices application presented by Chris Richardson in his famous book "Microservices patterns: with examples in Java" [[2]](https://github.com/FrHassan/MicroservicesProjects/edit/main/Microservices-Projects/Food%20to%20Go%20(FTGO)/README.md#references). FTGO is considered as a reference example regarding the adoption of microservices good practices. The application covers a lot of concepts and patterns, heading from the decomposition and services identification strategies to deployment techniques and patterns. The figure below illustrate the FTGO microservices architecture.  

<p align="center">
 <img src="FTGO microservices architecture (PNG).PNG" width="70%">
</p>

FTGO is a good starting point to understand microservices patterns. For its services identification the application uses the Domain-Driven Design (DDD) approach presented by Eric Evans [[3]](https://github.com/FrHassan/MicroservicesProjects/edit/main/Microservices-Projects/Food%20to%20Go%20(FTGO)/README.md#references). DDD is a well known and respectful strategy regarding decomposition or services identification. The approach can reflect perfectly the business logic of the application and transform it into inter-connected collaborative services.

In term of interprocess communication. FTGO uses a combination of synchronous and asynchronous messaging. Synchronous communication is mainly adopted using REST. However,  asynchronous communication is implemented using Event Sourcing along with Command Query Responsibility Segregation (CQRS) pattern. Regarding the data management, the application operates with Saga transactions to maintain data consistency.

FTGO application is well documented by the book of Chris Richardson [[2]](https://github.com/FrHassan/MicroservicesProjects/edit/main/Microservices-Projects/Food%20to%20Go%20(FTGO)/README.md#references), which is a recommended reference for practitioners interested in microservices patterns.

## FTGO Graph Analysis

This section presents the graph analysis performed on the FTGO application. The analysis process starts with the graph generation of the project. Then, the obtained results from the execution of the graph algorithms on the application associated graph will be presented in the form of charts and comments.

### Application associated Graph: 

The following figure illustrate the FTGO associated graph generated using Neo4j Bloom.

<p align="center">
 <img src="FTGO associated graph (PNG).PNG" width="70%">
</p>

A slight modification has been performed on the figure to highlight text and provide a key to the different type of microservices and interaction styles present within the architecture.

The graph above shows 3 types of microservices along with their databases. Regarding the communication between services, we can distinguish between 5 types of interactions, including the database adapter relationship. 

**Note:** The following graph analysis is performed on the FTGO graph without considering the databases relationships.

### Graph metrics:

* **Degree centrality:** Measures the number of edges a node has.

<p align="center">
 <img src="./Degree/FTGO Degree and Degree_Out (PNG).PNG" width="70%">
</p>

The chart illustrates the global degree (light blue) for each microservice along with the efferent degree (Outgoing relationships - Dark blue).

* **Triangles Count:** Calculate the number of three sided relationships a node participates in.

<p align="center">
 <img src="./Triangles Count/FTGO TrianglesCount (PNG).PNG" width="70%">
</p>

Triangles count is presented for each microservice, from the most participant nodes to the less.

* **Local Clustering Coefficient:** Measures the tightness of a group of nodes

<p align="center">
 <img src="./Local Clustering Coefficient/FTGO Local_Clustering_Coefficient (PNG).PNG" width="70%">
</p>

Figure above present the Local Clustering Coefficient for each microservice.

* **PageRank:** Measures the relative importance of a node in agaraph.

<p align="center">
 <img src="./PageRank/FTGO PageRank (PNG).PNG" width4050%">
</p>

The algorithm shows the most important microservices in term of dependencies.

* **Closeness centrality:** Measures the  importance of a node based on the shortest distances from all other nodes.

<p align="center">
 <img src="./Closeness/FTGO Closeness (PNG).PNG" width="40%">
</p>

Closeness centrality gives an indicator on key nodes in the architecture.

* **Louvain:** Detect clusters in a graph 

<p align="center">
 <img src="./Louvain/FTGO Louvain (PNG).PNG" width="40%">
</p>

The figure shows nodes, which tend to have tight dependencies between them.

* **Betweenness centrality:** Helps detecting bridges between communities.

<p align="center">
 <img src="./Betweenness/FTGO Betweenness (PNG).PNG" width="40%">
</p>

The chart presents nodes that control the data flow in the architecture.

## Discussion  
                                                                Soon

## References

[1] [https://github.com/microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application)  

[2] RICHARDSON, Chris. Microservices patterns: with examples in Java. Simon and Schuster, 2018.  

[3] EVANS, Eric. Domain-driven design: tackling complexity in the heart of software. Addison-Wesley Professional, 2004.  
