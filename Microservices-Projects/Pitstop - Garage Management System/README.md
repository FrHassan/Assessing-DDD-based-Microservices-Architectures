# Pitstop - Garage Management System

This section presents the application of the methodology on the Pitstop microservices application. The results (in csv format) are provided in the attached folders.

## Table of Contents

* [**Overview**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#Overview)  
* [**Pitstop Microservices architecture into a graph**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#Pitstop-Microservices-architecture-into-a-graph)  

* [**Graph algorithms execution on Pitstop**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#Graph-algorithms-execution-on-Pitstop)

* [**Pitstop result analysis**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#Pitstop-result-analysis)

* [**Proposed architecture**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#Proposed-architecture)
    
* [**References**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#References)


## Overview

Pitstop [[1]](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#References) is a microservices application devoted to maintaining the business of a car maintenance garage. Its main role is to support the employees’ daily tasks such as managing vehicles by customers, creating maintenance jobs planning, and ensuring continuous monitoring for each vehicle. Pitstop was mainly introduced to demonstrate several software architectural concepts such as CQRS [[2]](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#References), Event Sourcing [[3]](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#References), DDD [[4]](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#References), and Eventual Consistency [[5]](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Pitstop%20-%20Garage%20Management%20System#References).

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

The obtained results reveals that the Customer Management service exhibit the most significant level of Centrality Afferent Coupling within the system, with 4 inbound dependencies. This is because the service generates a CustomerRegistered event that is utilized by four other services. This results in a Design-Time Coupling between the Customer services and the other services, as modifying the event might necessitate changes in the linked services. The Workshop management, Invoice, and Time services follow a similar pattern, each having 3, 2, and 2 inbound dependencies correspondingly.

The pagerank analysis reveals that Customer management holds a significance of 0.39, while Vehicle services has a score of 0.31. Workshop Management is valued at 0.27, and Invoice at 0.23. These findings highlight the importance of Customer management within the architecture, followed by Vehicle services and Workshop Management. This hierarchy is determined by the extent of dependencies each service has and their criticality to other services in the system.

The results from the Triangle Count algorithm show that the Workshop management service has involvement in 4 triangular relationships, whereas the Customer management service is linked to 3 triangles. This indicates these services are dependent on other services that are also dependent on one another. As a result modification to these services may result in adjustment s to the other services depending on them.

According to the Local Clustering Coefficient algorithm, Customer Management exhibits a coefficient of 0.5, whereas Workshop Management registers a value of 0.4. This indicates that half of the services linked to these two services are also connected. The vehicle service has a value of 1 since the Front-end service calls upon the workshop management service. 

## Proposed architecture

This section involves proposing refactoring actions to reduce the degree of Design-Time coupling in the architecture. The proposed architecture is illustrated in the following Figures.

<p align="center">
 <img src="Pitstop new prop archi graph metrics/Pitstop prop archi associated graph.png" width="70%">
</p>

Based on the results presented in the table above, we opted to conduct a functional decomposition of the Workshop Management service. This particular service holds significance within the overall architecture due to its high scores across all four algorithms. 

As outlined in the official documentation, the functionality of other services in the architecture relies on the Workshop Management service for accessing data. Consequently, we established a distinct service, named "Read Model," devoted to supplying data to these services instead of depending directly on the Workshop Management service. The Workshop Management service keeps the Read Model service up to date via domain events.

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
