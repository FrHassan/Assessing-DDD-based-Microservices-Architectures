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

The analysis indicates that the Workshop Management, Notification, and Invoice services exhibit a higher Degree of Centrality Afferent Coupling values, indicating 3 incoming dependencies per service. This  signifies that alterations to these services would necessitate adjustments in three other services, underscoring a significant level of Design-Time Coupling.

The PageRank algorithm results reveal that the services highlited previously by the Degree Centrality Afferent Coupling algorithm (Workshop Management, Notification, and Invoice) have also the higher PageRank score. This finding aligns with the previous algorithm’s results which also emphasized the significance of these services in terms of incoming dependencies.

The Triangle Count algorithm results has shown that the Notification, and Invoice services participates only in 1 triangle, while the Workshop Management service participates in 4 triangles, making the Workshop Management the important service in the architecture.

The results of the Local Clustering Coefficient algorithm show that the Workshop Management has the higher value with a score of 0.4, suggesting that approximately half of the services associated with this service are also connected to each other.

## References

[1] Example: Defining microservices for the Drone Delivery application. [https://learn.microsoft.com/thth/azure/architecture/microservices/model/microservice-boundaries](https://learn.microsoft.com/thth/azure/architecture/microservices/model/microservice-boundaries)  

[2] [4] EVANS, Eric. Domain-driven design: tackling complexity in the heart of software. Addison-Wesley Professional, 2004.  
