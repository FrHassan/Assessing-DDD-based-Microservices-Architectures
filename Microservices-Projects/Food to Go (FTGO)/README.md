# Food to Go (FTGO)

This section presents the application of the methodology on the FTGO microservices application. The results (in csv format) are provided in the attached folders.

## Table of Contents

* [**Overview**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#Overview)  
* [**FTGO Microservices architecture into a graph**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#FTGO-Microservices-architecture-into-a-graph)  

* [**Graph algorithms execution on FTGO**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#Graph-algorithms-execution-on-FTGO)

* [**FTGO result analysis**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#FTGO-result-analysis)

* [**Proposed architecture**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#Proposed-architecture)
    
* [**References**](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#References)


## Overview

Food to Go (FTGO) [[1]](https://github.com/microservices-patterns/ftgo-application) is an enterprise Java-based application designed for managing restaurants and food delivery. The main feature of FTGO lies in the utilization of DDD [[2]](https://github.com/FrHassan/Assessing-DDD-based-Microservices-Architectures/tree/main/Microservices-Projects/Food%20to%20Go%20(FTGO)#References) to identify and decompose its set of services. The approach results in the establishment of separate sub-domains, each with its own defined Bounded Context. These contexts were subsequently utilized to identify the application services, including Order, Consumer, and Delivery. Each service within FTGO adheres to a single responsibility and is characterized by a small granularity, encompassing only the necessary entities for optimal functionality. This enables them to be developed by dedicated smaller teams.

<p align="center">
 <img src="FTGO microservices architecture (PNG).PNG" width="70%">
</p>

## FTGO Microservices architecture into a graph

During this phase of the methodology, the architecture associated graph of the FTGO architecture is generated and shown in the Figure below.

<p align="center">
 <img src="FTGO graph metrics/FTGO associated graph (PNG).png" width="70%">
</p>

## Graph algorithms execution on FTGO

The second phase of the methodology invovles executing the graph algorithms on the FTGO associated graph. The following table presents the obtained results from this execution. The rows highlighted in red show the services that exceed the threshold of the Degree Centrality Afferent Coupling, while for the other algorithms, the metrics for the services that surpass the thresholds are indicated in red with the tiny character '1'. 

<p align="center">
 <img src="FTGO graph metrics/Graph metrics.png" width="70%">
</p>

## FTGO result analysis

The Degree Centrality Afferent Coupling measures the number of services that directly depend on a particular service. In the case of the Order service, it has a value of 6 incoming dependencies, indicating that there are 6 other services that directly depend on the data provided by the Order service. This creates a Design-Time Coupling between these services, indicating that any changes made to the Order service may require subsequent modifications to 6 other services. Similar dependencies exist for the Kitchen and Restaurant services, with 4 incoming dependencies each. This indicates a significant degree of Design-Time Coupling between these services (Order, Kitchen, and Restaurant) and the other services that depend on them.

The PageRank algorithm results reveal a significant score for the services identified previously by the Degree Centrality Afferent Coupling algorithm (Order, Kitchen, and Restaurant). This finding aligns with the previous algorithm’s results which also emphasized the significance of these services in terms of incoming dependencies. Additionally, a high score of the PageRank algorithm indicates that these services depend on other important services. This is expected as the Order, Kitchen, and Restaurant services all depend on one another (refer to Figure 5). These findings validate the considerable degree of Design-Time Coupling present between these 3 services and the others that depend on them.

The Triangle Count algorithm results regarding the services emphasized through the Degree Centrality Afferent Coupling algorithm indicate that the Order service is involved in 14 three-sided dependencies. This finding signifies that modifications made to the Order service are not only affecting the 6 services that rely directly on it (as demonstrated by the Degree Centrality Afferent Coupling algorithm) but may also affect additional services associated with those 6 services. The Kitchen and Restaurant services share common concerns as they are involved in 7 triangles, with 4 incoming dependencies each. This indicates an important degree of Design-Time Coupling between the 3 services and their surroundings.

The results of the Local Clustering Coefficient algorithm show that the Order service is 0.5, suggesting that approximately half of the services associated with the Order service are also connected. Similarly, the LCC of the Kitchen service is 0.7, indicating that 70\% of the services connected to it are also dependent on each other, in contrast to the Restaurant which shows a low value of the LCC. This indicates that the Order service and the Kitchen service present a significant degree of Design-Time Coupling. The Restaurant service has an important level of this type of coupling. However, it is lower than the other two services, meaning that changes to the Restaurant service have less effect than the Order and the Kitchen services.

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

[1] [https://github.com/microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application)  

[2] EVANS, Eric. Domain-driven design: tackling complexity in the heart of software. Addison-Wesley Professional, 2004.  

