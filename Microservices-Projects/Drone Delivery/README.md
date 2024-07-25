# Drone Delivery

This section presents the application of the methodology on the Drone Delivery microservices application. All the necessessary data are provided in the attached folders.

## Table of Contents

* [**Overview**](#Overview)  
* [**Drone Delivery Microservices architecture into a graph**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Drone%20Delivery#Drone-Delivery-Microservices-architecture-into-a-graph)  

* [**Graph algorithms execution on Drone Delivery**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Drone%20Delivery#Graph-algorithms-execution-on-Drone-Delivery)

* [**Drone Delivery result analysis**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Drone%20Delivery#Drone-Delivery-result-analysis)

* [**Proposed architecture**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Drone%20Delivery#Proposed-architecture)
    
* [**References**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Drone%20Delivery#References)

## Overview

The Drone Delivery [1] application is a microservices-based system featured in the official documentation [59] of Microsoft Azure. It demonstrates the identification of microservices boundaries through Domain-Driven Design (DDD) [2]. The application is specifically designed to facilitate drone-based deliveries for businesses. It comprises 10 microservices, each addressing various essential aspects of the delivery process such as scheduling pickups and drones, managing user accounts, tracking packages, and archiving historical data for analytical purposes.

<p align="center">
 <img src="Drone Delivery microservices architecture (PNG).png" width="70%">
</p>

## Drone Delivery Microservices architecture into a graph

During this phase of the methodology, the architecture associated graph of the Drone Delivery architecture is generated and shown in the Figure below.

<p align="center">
 <img src="Drone Delivery graph metrics/Drone Delivery associated graph (PNG).png" width="70%">
</p>

## Graph algorithms execution on Drone Delivery

The second phase of the methodology invovles executing the graph algorithms on the Drone Delivery associated graph. The following table presents the obtained results from this execution.

<p align="center">
 <img src="Drone Delivery graph metrics/Graph metrics.png" width="70%">
</p>

## Drone Delivery result analysis

According to the Degree Centrality Afferent coupling algorithm, all services in the architecture have a small number of incoming dependencies. This suggests that modifications made to these services will only have a limited effect on other parts of the system. Therefore, there is a low level of Design-Time coupling among the services.

According to the PageRank algorithm, the Scheduler service holds significant importance in the architecture as it has attained the highest Degree Centrality Afferent coupling score among all services. However, as the Degree Centrality Afferent coupling indicates the level of Desing-Time coupling is low regarding this services with the others.

The Triangle Count algorithm has revealed the absence of any triangles in the architecture. This indicates that the dependencies within the architecture are simple and reflect a low degree of Design-Time coupling. Therefore, the architecture can be considered to be simple in its design and structure.

The results of the Local Clustering Coefficient algorithm has also a 0 value for all services, suggesting that the connectivity between services are simple. This as well refeer to a simple degree of Design-Time coupling.

Note: the Scheduler service is an orchestration service that arranges and organizes complex functionalities that invoke
multiple services. Consequently, the Scheduler service may receive multiple calls from other services as it orchestrate and provide data easly. As a result, As a result, these type of services are not taken into consideration in the evaluation of \textit{Design-Time Coupling}, as they tend to have multuple incoming dependencies by nature.

## References

[1] Example: Defining microservices for the Drone Delivery application. [https://learn.microsoft.com/thth/azure/architecture/microservices/model/microservice-boundaries](https://learn.microsoft.com/thth/azure/architecture/microservices/model/microservice-boundaries)  

[2] [4] EVANS, Eric. Domain-driven design: tackling complexity in the heart of software. Addison-Wesley Professional, 2004.  
