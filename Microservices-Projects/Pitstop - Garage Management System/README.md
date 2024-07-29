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

This section involves proposing refactoring actions to reduce the degree of Design-Time coupling in the architecture. The proposed architecture is illustrated in the following Figures. Accordifn to the "_Pitstop result analysis_" section, the Customer Management and the Workshop Managementservices are the most important services in the architecture. The primary consideration is the merging of services. Yet, the merging solution is not feasible due to the lack of close interrelation in service functionalities. The second option is to split services through functional decomposition. However, the Customer Management service only caters to a single function, the "RegisterCustomer" command. Hence, there is no scope for further division in this microservice. In contrast, the Workshop Management service encompasses two components: an API for managing workshop schedules and an event handler responsible for processing events and building a read-model used by the API. As a result, a functional decomposition is conducted on the Workshop Management service to extract the Read-model and establish it as an independent service. The following figure displays the proposed architecture after this change has been made.

<p align="center">
 <img src="Pitstop new prop archi graph metrics/Pitstop prop archi associated graph.png" width="70%">
</p>

The following step is to execute the graph algorithms on the newly proposed refactored architecture. The following Table presents the metrics of the proposed refactored architecture along with the metrics of the initial architecture. The metrics denoted by a green '1' represent a decrease in comparison to the metrics of the initial architecture, while the metrics denoted by a red '2' means an increase regarding the value of the algorithm. In the following, the proposed refactored architecture's obtained results are analyzed. Then, these results are compared to the findings of the initial architecture to check the variation in the level of Design-Time Coupling.

<p align="center">
 <img src="Pitstop new prop archi graph metrics/Pitstop new graph metrics.png" width="70%">
</p>

The findings reveal that the proposed refactored architecture has resulted in a decrease in both the number of triangles and the local clustering coefficient, demonstrating a significant reduction in overall complexity. It is worth noting that there has been a rise in degree centrality and affrent coupling within the Workshop Management services. As a result, it can be concluded that the recommended restructuring efforts have effectively simplified the architecture without compromising its level of design-time coupling. Therefore, the original DDD-based architecture of Pitstop is better in terms of design-time coupling.


## References

[1] Pitstop - Garage Management System. [https://github.com/EdwinVW/pitstop/wiki](https://github.com/EdwinVW/pitstop/wiki)  

[2] Pattern: Command Query Responsibility Segregation (CQRS). [https://microservices.io/patterns/data/cqrs.html.]( https://microservices.io/patterns/data/cqrs.html.)  

[3] Pattern: Event sourcing. [https://microservices.io/patterns/data/event-sourcing.html](https://microservices.io/patterns/data/event-sourcing.html)  

[4] EVANS, Eric. Domain-driven design: tackling complexity in the heart of software. Addison-Wesley Professional, 2004.  

[5] NEWMAN, Sam. Building microservices. " O’Reilly Media, Inc.", 2021.  
