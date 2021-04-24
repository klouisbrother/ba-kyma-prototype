# Chapter 4.3.4: Testing of the Microservice

Within this part the implemented and exposed Sap-Commerce-Mock will be tested:

* Test the microservice by triggering an event from the SAP-Commerce-Mock
* Validating the event data stored in the microservice

The validation is documented further below.

## Test the microservice by triggering an event from the SAP-Commerce-Mock

To test the setup and the configruration of the microservice, one of the "SAP Commerce Cloud - Events" must be triggered. In the further case, is will be demonstrated by using the earlier used business case by triggering the Event `order.created.v1`. To send an event from the SAP-Commerce-Mock to the microservice "orders-service" perform the following steps.

1. Go to the "sap-commerce-mock" namespace and access the SAP-Commerce-Mock via the Host-URL under "Discovery and Network" -> "API Rules". 

2. Switch to the "Remote API" tab and select "SAP Commerce Cloud - Events" which have been configured earlier.

3. From the Event Topic dropdown, select the `order.created.v1` event type and the following payload will be automatically proposed.

```
{
	"orderCode": "76272727"
}
```

4. To test also the further fields, we enhance the payload as followed shown and select Send Event to trigger the Event. A short message in the UI will confirm that the event was sent to the Microservice.

```
{
    "orderCode": "29081995",
    "consignmentCode": "08154711",
    "consignmentStatus": "PICKUP_OPEN"
}
```

5. The successful triggering of the event is shown below.

![](images/04_01_Trigger_order.created.v1_event.png)


## Validating the event data stored in the microservice

1. By sending the following command, we can verify that the event details were saved in the microservice.

```
curl -ik "https://orders-service.c-293e5fa.kyma.shoot.live.k8s-hana.ondemand.com/orders"
```

2. The sent events data is stored in the pods in-memory database as shown below.

![](images/04_02_Verify_order.created.v1_event.png)


## Sources

* Guide: [Kyma-Project: Getting Started, Version 1.21 (latest): Test the trigger](https://kyma-project.io/docs/1.20/root/getting-started#getting-started-trigger-the-microservice-with-an-event-test-the-trigger)


## Summary and next step

With this chapter the microservice has been tested by triggering an "Create Order" event. There for the question "How can a prototype of a microservice be implemented based on the Kyma Runtime to extend the SAP Commerce Cloud?" was answered. Within the next part of the Bachelor-Thesis, the implemented prototype of this microservice will be evaluated against the in chapter 3 elaborated success factors, by performing interviews with topic experts. 

[Go back to start](https://github.com/klouisbrother/ba-kyma-prototype)
