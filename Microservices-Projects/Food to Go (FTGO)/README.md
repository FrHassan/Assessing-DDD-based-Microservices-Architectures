# Food to Go (FTGO)

This section presents the application of the methodology on the FTGO microservices application. All the necessessary data are provided in the attached folders.

## Table of Contents

* [**Overview**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#Overview)  
* [**FTGO Microservices architecture into a graph**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#FTGO-Microservices-architecture-into-a-graph)  

* [**Graph algorithms execution on FTGO**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#Graph-algorithms-execution-on-FTGO)

* [**FTGO result analysis**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#FTGO-result-analysis)

* [**Proposed architecture**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#Proposed-architecture)
    
* [**References**](https://github.com/FrHassan/MicroservicesProjects#References)


## Overview

Food to Go (FTGO) [[1]](https://github.com/microservices-patterns/ftgo-application) is an enterprise Java-based application designed for managing restaurants and food delivery. The main feature of FTGO lies in the utilization of DDD to identify and decompose its set of services. FTGO implements DDD by following the steps presented in section 2-1. This approach leads to the creation of distinct sub-domains, each having its own defined Bounded Context. Figure 1 presents some of the FTGO’s sub-domains such as Order, Consumer, and Delivery sub-domains. In the case of FTGO, each Bounded Context corresponds to one microservice. Each of these services has a single responsibility and is considered small in terms of granularity, containing only the needed entities to ensure their functioning, allowing to be developed by dedicated small teams.

<p align="center">
 <img src="FTGO microservices architecture (PNG).PNG" width="70%">
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

## References

[1] [https://github.com/microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application)  