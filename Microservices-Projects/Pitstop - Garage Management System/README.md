# Pitstop - Garage Management System

This section presents the application of the methodology on the Pitstop microservices application. All the necessessary data are provided in the attached folders.

## Table of Contents

* [**Overview**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#Overview)  
* [**FTGO Microservices architecture into a graph**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#FTGO-Microservices-architecture-into-a-graph)  

* [**Graph algorithms execution on Pitstop**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#Graph-algorithms-execution-on-Pitstop)

* [**FTGO result analysis**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#FTGO-result-analysis)

* [**Proposed architecture**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#Proposed-architecture)
    
* [**References**](https://github.com/FrHassan/MicroservicesProjects#References)


## Overview

Pitstop [1] is a microservices application devoted to maintaining the business of a car maintenance garage. Its main role is to support the employees’ daily tasks such as managing vehicles by customers, creating maintenance jobs planning, and ensuring continuous monitoring for each vehicle. Pitstop was mainly introduced to demonstrate several software architectural concepts such as CQRS [2], Event Sourcing [3], DDD [4], and Eventual Consistency [5].

The application was completely built using .NET (ASP.NET Core). Moreover, it utilizes Docker, Kubernetes, Istio, RabbitMQ and others. Figure 23 shows the Pitstop main architecture.

<p align="center">
 <img src="Pitstop microservices architecture (PNG).png" width="70%">
</p>

## FTGO Microservices architecture into a graph

During this phase of the methodology, the architecture associated graph for is generated and shown in the Figure below.

<p align="center">
 <img src="FTGO graph metrics/FTGO associated graph (PNG).png" width="70%">
</p>

## Graph algorithms execution on FTGO

The second phase of the methodology invovles executing the graph algorithms on the FTGO associated graph. The following table presents the obtained results from this execution. The rows highlighted in red show the services that exceed the threshold of the Degree Centrality Afferent Coupling, while for the other algorithms, the metrics for the services that surpass the thresholds are indicated in red with the tiny character '1'. 

<p align="center">
 <img src="FTGO graph metrics/Graph metrics.png" width="70%">
</p>

## FTGO result analysis

The Degree Centrality Afferent Coupling algorithm has identified 3 services (Order, Kitchen, and Restaurant) with differing levels of incoming dependencies, ranging from 4 to 6. This suggests that modifications to any of these services will require corresponding changes in at least 4 services, which refers to an important level of Design-Time Coupling. Additionally, the other algorithms have confirmed the findings of the Degree Centrality Afferent Coupling algorithm, with the 3 services showing significant values for these algorithms except for the "\textit{Restaurant}" service in regards to the LCC algorithm.

## Proposed architecture

In this section involves proposing refactoring actions to reduce the degree of Design-Time coupling in the architecture. The proposed architecture is illustrated in the following Figures.

<p align="center">
 <img src="New proposed architecture graph metrics/FTGO proposed architecture associated graph (PNG).png" width="70%">
</p>

<p align="center">
 <img src="New proposed architecture graph metrics/FTGO proposed architecture ordering graph (PNG).png" width="70%">
</p>

The following step is to execute the graph algorithms on the newly proposed refactored architecture. The following Table presents the metrics of the proposed refactored architecture along with the metrics of the initial architecture. The metrics denoted by a green '1' represent a decrease in comparison to the metrics of the initial architecture. In the following, the proposed refactored architecture's obtained results are analyzed. Then, these results are compared to the findings of the initial architecture to check the variation in the level of Design-Time Coupling.

<p align="center">
 <img src="New proposed architecture graph metrics/New graph metrics.png" width="70%">
</p>

The overall results indicate that the proposed refactored architecture has experienced a decrease in all metrics, without any observed increase. The Degree Centrality Afferent Coupling algorithm has only shown a decrease in the number of incoming dependencies for the Delegate Order" service (previously the "Order" service). However, there have been no increases regarding the metrics of the other services. According to the PageRank algorithm, 9 services were identified as having lower importance rankings based on the number of incoming dependencies, which confirms the reduction in terms of the number of dependencies per service. Hence, the level of Design-Time Coupling between these services decreases. Regarding the Triangle Count algorithm, significant progress has been made in terms of reducing the number of three-sided dependencies across a total of 9 services. Additionally, there is an important decrease across 8 services in terms of the Local Clustering Coefficient with no increase at any service, which indicates that the level of Design-Time Coupling has been reduced in comparison to the initial architecture. However, this new refactored architecture comes with a cost, which is the increase in the number of microservices within the overall architecture.

## References

[1] Pitstop - Garage Management System. [https://github.com/EdwinVW/pitstop/wiki](https://github.com/EdwinVW/pitstop/wiki)  

[2] Pattern: Command Query Responsibility Segregation (CQRS). [https://microservices.io/patterns/data/cqrs.html.]( https://microservices.io/patterns/data/cqrs.html.)  

[3] Pattern: Event sourcing. [https://microservices.io/patterns/data/event-sourcing.html](https://microservices.io/patterns/data/event-sourcing.html)  

[4] EVANS, Eric. Domain-driven design: tackling complexity in the heart of software. Addison-Wesley Professional, 2004.  

[5] NEWMAN, Sam. Building microservices. " O’Reilly Media, Inc.", 2021.  
