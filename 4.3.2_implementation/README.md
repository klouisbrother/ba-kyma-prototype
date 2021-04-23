# Chapter 4.3.2: Implementation of the Microservice

Within this chapter the following steps will be performed and are described below:

* Create new "orders-service" namespace and deploy the Microservices "orders-service"
* Expose the microservice to other ressources outsite of the cluster
* Optional: Enhancement with permanent database storage

These steps are documented further below.


## Create new "orders-service" namespace and deploy the Microservices "orders-service" 

Firstly a new namespace for the new Microservice has to be created in Kyma.

1. Create a new namespace with the name "orders-service" with the following command and the command line.

```
kubectl create ns orders-service
```

2. Check that the Namespace was set up. This is indicated by performing the following command. The response will reflect the status of the Namespace with `Active`.

```
kubectl get ns orders-service -o=jsonpath="{.status.phase}"
```

![](images/02_01_Kyma_CreateNamespace_orders-service.png)

3. Create a Deployment that provides the microservice definition and enables you to run it on the cluster. The Deployment uses the `eu.gcr.io/kyma-project/pr/orders-service:PR-162` image. This Docker image exposes the `8080` port on which the related Service is listening.

```
kubectl apply -f https://raw.githubusercontent.com/kyma-project/examples/master/orders-service/deployment/orders-service-deployment.yaml
```

4. Check if the ressources definied in the deployment file have been created. Deployment status will be readyReplicas `1`.

```
kubectl get deployment orders-service -n orders-service -o=jsonpath="{.status.readyReplicas}"
```

5. Deploy the Kubernetes Service in the "orders-service" Namespace to allow other Kubernetes resources to communicate with your microservice.

```
kubectl apply -f https://raw.githubusercontent.com/kyma-project/examples/master/orders-service/deployment/orders-service-service.yaml
```

![](images/02_02_Kyma_Deploy_orders-service.png)

6. The successful deployment and running pods is also reflected Kyma Runtime Environment User Interface, as shown below.

![](images/02_03_Kyma_UI_Namespace_orders-service.png)


## Expose the microservice to other ressources outsite of the cluster

Until now a standalone and in a closed-environment microservice was deployed, now we have to allow to make is available to other ressources outsite of the cluster via an API Rule, this time via the Kyma Runtime Environment UI.

1. Select the namespace "orders-service" and go to "Discovery and Network" -> "API Rules" and create a new API Rule. 

2. Enter a specific name and hostname for the API rule. In this case "orders-service" can used as well. As Service "orders-service (port: 80)" shoud be selected, to indicate the Service name for which you want to create the API Rule.

3. As access stratgy select as handler "noop" and allow only "GET" and "POST" methods. This allows to send the orders to the Service and retrieve orders from it without any token. The configuration is shown below. Click on "create", to create and save the rules, as shown below.

![](images/02_04_Kyma_UI_Configure_APIrule.png)

4. The API rule status will be "OK" and you can access the Service by by selecting the HTTPS link under Host and adding the `/orders` endpoint at the end of it. For this case: `https://orders-service.c-293e5fa.kyma.shoot.live.k8s-hana.ondemand.com/orders`

![](images/02_05_Orders-service_Access.png)

5. To quickly test the availability of the microservice from external perform a POST request to the Microservice using the URL `https://orders-service.c-293e5fa.kyma.shoot.live.k8s-hana.ondemand.com/orders` and a sample orders similar as seen below.

```
{
    "orderCode": "762727210",
    "consignmentCode": "76272725",
    "consignmentStatus": "PICKUP_COMPLETE"
}
```

6. By further performing the following command, you will get back the processed order data as seen below. 

```
curl -ik https://orders-service.c-293e5fa.kyma.shoot.live.k8s-hana.ondemand.com/orders
```

![](images/02_06_Orders-service_Orderdata.png)


## Optional: Enhancement with permanent database storage

After some first tests, it was clear that by now the microservice uses an in-memory storage. This means every time on of the related pods of the microservice "orders-service" will be terminated, the data will be erased. To avoid this and be able to permanently store the collected data, this optional enhancement step of integration of a database via the Kyma Service Catalog can been performed. 

To overcome this point, the initial idea was to integrate a custom Redis service, which provides the possibilities to use a [Redis Database](https://redis.io/), as further described on the [Kyma-Project: Getting Started, Version 1.21 (latest): Add the redis service](https://kyma-project.io/docs/root/getting-started#getting-started-add-the-redis-service) guide.

After some quick review of the guide and some initial configurations, it was not possible to add the [Redis Database](https://redis.io/) service. 

By checking with the [SAP Community](https://answers.sap.com/answers/13349083/view.html), Marco Dorn (username) brought up the answer and reasion that the Kyma Runtime Environment on SAP BTP, in Version 1.21, does currently not provide a full cluster access. Due to this adding a custom service is not possible at the moment, but should be available in the future.

Further Jamie Cawley (username) as members of the [SAP Community decribed an alternative](https://answers.sap.com/answers/13350157/view.html) to use as direct replacement a [MS SQL database](https://github.com/SAP-samples/kyma-runtime-extension-samples/tree/master/database-azure-mssql) provided by Microsoft Azure via the Open Service Broker.

As for this a provisioning of a Microservice Azure Account would be needed, which is not available at this time and also not the central part to answer the question of this chapter, the enhancement with a permanent database storage was not implemented and can be seen as optional enhancement to the Microservice.


## Sources

* Guide: [Kyma-Project: Getting Started, Version 1.21 (latest)](https://kyma-project.io/docs/root/getting-started/#getting-started-create-a-namespace) 
* Repository: [kyma-project/examples/orders-service](https://github.com/kyma-project/examples/tree/main/orders-service) and cloned into this Repository under [ba-kyma-prototype/4.3.2_implementation/orders-service](https://github.com/klouisbrother/ba-kyma-prototype/tree/main/4.3.2_implementation/orders-service)
* Helpful input: [SAP Blogs: SAP Cloud Platform, Kyma runtime: Mock Applications](https://blogs.sap.com/2020/06/17/sap-cloud-platform-extension-factory-kyma-runtime-mock-applications)
* Very helpful input :thumbsup:: [SAP Community: Add external Service to Kyma not possible in Trial](https://answers.sap.com/questions/13348971/add-external-service-to-kyma-not-possible-in-trial.html?childToView=13350157#answer-13350157)
* Repository: [SAP-samples/kyma-runtime-extension-samples/database-azure-mssql](https://github.com/SAP-samples/kyma-runtime-extension-samples/tree/master/database-azure-mssql)


## Summary and next step

With this chapter the Microservice was implemented, is available and running. Further it was made available to the outsite. Also the optional step of implementing a MS Azure database was performed. As next step the connection between the Microservice and SAP Commerce has to be done.

[Next - Chapter 4.3.3: Connection of Microservice and SAP Commerce](https://github.com/klouisbrother/ba-kyma-prototype/tree/main/4.3.3_connection) 