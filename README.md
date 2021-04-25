# Bachelor-Thesis: Microservices to extend cloud-based e-commerce applications

Author: Florian Peschke (info@florianpeschke.de)

## Introduction

This repository contains all binaries and a documentation of the implemented prototype of a microservice, as part of my Bachelor-Thesis with the original German title: "Microservices zur Erweiterung von cloudbasierten E-Commerce-Applikationen". Meaningful translated the English title is "Microservices to extend cloud-based e-commerce applications". The thesis was submitted in June 2021 to [FOM Hochschule für Oekonomie & Management](https://www.fom.de), Essen, Germany. 

In chapter 4 of my Thesis, the questions "How can a prototype of a microservice based on Kyma Runtime be implemented to extend the SAP Commerce Cloud?" was posed and should be answered.

Further it was planned to implement a running prototype of a microservice, which is based on the [Kyma](https://kyma-project.io) Runtime provisioned on the [SAP Business Technology Platform (SAP BTP)](https://www.sap.com/germany/products/business-technology-platform.html). Herefor the microservice should be able to extend the monolithic [SAP Commerce Cloud](https://www.sap.com/germany/products/crm/e-commerce-platforms.html) application. The central intentions are to show the concepts of Kyma to extend a SAP Commerce Cloud system and less on the implementation of a specific functionality.


## Use-Case

As the intention of this prototype is the extension of the monolithic e-commerce application SAP Commerce Cloud using microservices, a concrete Use-Case was selected. For the further documentation of the implementation, the use-case will leverage the example of a created order in the e-commerce application. By creating a new order in the SAP Commerce Cloud system, the application should be able to trigger an event to the microservice. The microservice should be able to perform the additional business functionality. 

The concept is summarized in the diagram below.

![](images/-- Use Case Diagram --)

After the implementation of the prototype, the implementation will be evaluated against the in chapter 3 elaborated success of microservices factors by performing interviews with selected topic experts. 


## Related and helpful GitHub Repositories

For the prototype already existing code publicly available code parts have been used. These parts of these repositories have been included in this repository [klouisbrother/ba-kyma-prototype](https://github.com/klouisbrother/ba-kyma-prototype). The original sources are available as documented below and mentioned specifically in the following documentation of the prototyping process.

* [kyma-project/examples/orders-service](https://github.com/kyma-project/examples/tree/main/orders-service)
* [SAP-samples/xf-application-mocks/commerce-mock](https://github.com/SAP-samples/xf-application-mocks/tree/master/commerce-mock)


## Documentation structure

The prototyping process is described in detail in chapter 4.3 of the Bachelor-Thesis. To document the technical details further, as possible in chapter 4.3, the following documentation files (.md) have been created and added to this Repository [klouisbrother/ba-kyma-prototype](https://github.com/klouisbrother/ba-kyma-prototype). 

By following these chapters, you are able to follow the prototyping process and the taken decisions and steps to implement this prototype of Microservice.

* [Chapter 4.3.1: Prerequisites for implementation](https://github.com/klouisbrother/ba-kyma-prototype/blob/main/4.3.1_prerequisites) 
    * Get access to Kyma runtime on SAP Business Technology Platform
    * Setup of the development tools
    * Deploy the SAP Commerce Mock as consuming system into Kyma Namespace

* [Chapter 4.3.2: Implementation of the Microservice](https://github.com/klouisbrother/ba-kyma-prototype/tree/main/4.3.2_implementation) 
* [Chapter 4.3.3: Connection of Microservice and SAP Commerce](https://github.com/klouisbrother/ba-kyma-prototype/tree/main/4.3.3_connection) 
* [Chapter 4.3.4: Testing of the Microservice](https://github.com/klouisbrother/ba-kyma-prototype/tree/main/4.3.4_testing) 
