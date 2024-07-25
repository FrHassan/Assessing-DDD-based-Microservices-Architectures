# Pitstop - Garage Management System

This section presents the application of the methodology on the Pitstop microservices application. The results (in csv format) are provided in the

## Table of Contents

* [**Overview**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#Overview)  
* [**Pitstop Microservices architecture into a graph**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#Pitstop-Microservices-architecture-into-a-graph)  

* [**Graph algorithms execution on Pitstop**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#Graph-algorithms-execution-on-Pitstop)

* [**Pitstop result analysis**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#Pitstop-result-analysis)

* [**Proposed architecture**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#Proposed-architecture)
    
* [**References**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#References)


## Overview

Pitstop [1] is a microservices application devoted to maintaining the business of a car maintenance garage. Its main role is to support the employees’ daily tasks such as managing vehicles by customers, creating maintenance jobs planning, and ensuring continuous monitoring for each vehicle. Pitstop was mainly introduced to demonstrate several software architectural concepts such as CQRS [2], Event Sourcing [3], DDD [4], and Eventual Consistency [5].

The application was completely built using .NET (ASP.NET Core). Moreover, it utilizes Docker, Kubernetes, Istio, RabbitMQ and others. Figure 23 shows the Pitstop main architecture.

<p align="center">
 <img src="Pitstop microservices architecture (PNG).png" width="70%">
</p>

## Pitstop Microservices architecture into a graph

During this phase of the methodology, the architecture associated graph of the Pitstop architecture is generated and shown in the Figure below.

<p align="center">
 <img src="Pitstop graph metrics/Pitstop associated graph (PNG).png" width="70%">
</p>

## Graph algorithms execution on Pitstop

The second phase of the methodology invovles executing the graph algorithms on the Pitstop associated graph. The following table presents the obtained results from this execution.

<p align="center">
 <img src="Pitstop graph metrics/Graph metrics.png" width="70%">
</p>

## Pitstop result analysis

The analysis indicates that the Workshop Management, Notification, and Invoice services exhibit a higher Degree of Centrality Afferent Coupling values, indicating 3 incoming dependencies per service. This  signifies that alterations to these services would necessitate adjustments in three other services, underscoring a significant level of Design-Time Coupling.

The PageRank algorithm results reveal that the services highlited previously by the Degree Centrality Afferent Coupling algorithm (Workshop Management, Notification, and Invoice) have also the higher PageRank score. This finding aligns with the previous algorithm’s results which also emphasized the significance of these services in terms of incoming dependencies.

The Triangle Count algorithm results has shown that the Notification, and Invoice services participates only in 1 triangle, while the Workshop Management service participates in 4 triangles, making the Workshop Management the important service in the architecture.

The results of the Local Clustering Coefficient algorithm show that the Workshop Management has the higher value with a score of 0.4, suggesting that approximately half of the services associated with this service are also connected to each other.

## Proposed architecture

In this section involves proposing refactoring actions to reduce the degree of Design-Time coupling in the architecture. The proposed architecture is illustrated in the following Figures.

<p align="center">
 <img src="Pitstop new prop archi graph metrics/Pitstop prop archi associated graph.png" width="70%">
</p>

The following step is to execute the graph algorithms on the newly proposed refactored architecture. The following Table presents the metrics of the proposed refactored architecture along with the metrics of the initial architecture. The metrics denoted by a green '1' represent a decrease in comparison to the metrics of the initial architecture, while the metrics denoted by a red '2' means an increase regarding the value of the algorithm. In the following, the proposed refactored architecture's obtained results are analyzed. Then, these results are compared to the findings of the initial architecture to check the variation in the level of Design-Time Coupling.

<p align="center">
 <img src="Pitstop new prop archi graph metrics/Pitstop new graph metrics.png" width="70%">
</p>

The overall results indicate that the proposed refactored architecture has experienced a decrease in the majority of the metrics. The Degree Centrality Afferent Coupling algorithm has only shown a decrease in the number of incoming dependencies for the Workshop management service. However, there have been no increases regarding the metrics of the other services. According to the PageRank algorithm, 3 services have shown lower importance rankings based on the number of incoming dependencies, however, there was a slight increase regarding two services (increase with approximatly 0.02). Regarding the Triangle Count algorithm, significant progress has been made in terms of reducing the number of three-sided dependencies across a total of 6 services. Additionally, there is an important decrease across 6 services in terms of the Local Clustering Coefficient with no increase at any service, which indicates that the level of Design-Time Coupling has been reduced in comparison to the initial architecture. However, this new refactored architecture comes with a cost, which is the increase in the number of microservices within the overall architecture.

## References

[1] Pitstop - Garage Management System. [https://github.com/EdwinVW/pitstop/wiki](https://github.com/EdwinVW/pitstop/wiki)  

[2] Pattern: Command Query Responsibility Segregation (CQRS). [https://microservices.io/patterns/data/cqrs.html.]( https://microservices.io/patterns/data/cqrs.html.)  

[3] Pattern: Event sourcing. [https://microservices.io/patterns/data/event-sourcing.html](https://microservices.io/patterns/data/event-sourcing.html)  

[4] EVANS, Eric. Domain-driven design: tackling complexity in the heart of software. Addison-Wesley Professional, 2004.  

[5] NEWMAN, Sam. Building microservices. " O’Reilly Media, Inc.", 2021.  
