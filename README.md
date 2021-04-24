# Bachelor-Thesis: Microservices to extend cloud-based e-commerce applications

Some key and surrounding facts:
* Bachelor-Thesis in Business Informatics (Wirtschaftsinformatik) 
* Original German title: Microserivices zur Erweiterung von cloudbasierten E-Commerce-Applikationen
* Institute: FOM Hochschule für Oekonomie & Management


## Introduction

This repository contains all binaries and documentation of the created Microservice-Prototype, as part of my Bachelor-Thesis with the translated English title "Microservices to extend cloud-based e-commerce applications" at FOM Hochschule für Oekonomie & Management, in Munich, Germany. 

With chapter 4 of this Thesis the questions "How can a prototype of a microservice be implemented based on the Kyma Runtime to extend the SAP Commerce Cloud?" should be answered.

To answer this question the Microservice should be implemented by using the Kyma-Runtime provided via the SAP Business Technology Platform (SAP BTP). The Kyma-based Microservice which should be implemented, should be able to extend the monolithic SAP Commerce Cloud application.

The Bachelor-Thesis and the related Prototype has been created in the time between March and June 2021.


## Use-Case

As the intention of the Prototype is the extension of a monolithic e-commerce application using Microservices, the Use-Case will leverage the example of a created order. The SAP-Commerce-Cloud application should be able to trigger an event to the created Microservice and perform the additional business functionality. The functionality is shown in the use case diagram below.

![](images/-- Use Case Diagram --)

After the implementation of the Microservice-Prototype, the implementation will be evaluated against the in chapter 3 elaborated success factors by performing interviews with topic experts. 


## Related and helpful GitHub Repositories

For the prototype several already existing code publicly available code parts have been used. These parts of these repositories have been included in this Repository [klouisbrother/ba-kyma-prototype](https://github.com/klouisbrother/ba-kyma-prototype). The original sources are available as documented below and mentioned in the created documentation of the prototyping process.

* [kyma-project/examples/orders-service](https://github.com/kyma-project/examples/tree/main/orders-service)
* [SAP-samples/xf-application-mocks/commerce-mock](https://github.com/SAP-samples/xf-application-mocks/tree/master/commerce-mock)


## Documentation structure

The prototyping process of the bachelor-thesis is described in detailed in chapter 4.3. To document the technical details the following documentation file have been created and added to this Repository [klouisbrother/ba-kyma-prototype](https://github.com/klouisbrother/ba-kyma-prototype). By following these chapters, you are able to follow the implementation of the prototype in detail.

* [Chapter 4.3.1: Prerequisites for implementation](https://github.com/klouisbrother/ba-kyma-prototype/blob/main/4.3.1_prerequisites) 
* [Chapter 4.3.2: Implementation of the Microservice](https://github.com/klouisbrother/ba-kyma-prototype/tree/main/4.3.2_implementation) 
* [Chapter 4.3.3: Connection of Microservice and SAP Commerce](https://github.com/klouisbrother/ba-kyma-prototype/tree/main/4.3.3_connection) 
* [Chapter 4.3.4: Testing of the Microservice](https://github.com/klouisbrother/ba-kyma-prototype/tree/main/4.3.4_testing) 
