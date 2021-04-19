With these features in mind, we will:
1. Create a microservice that can expose HTTP endpoints and receive a specific type of events from external applications. It has built-in in-memory storage for storing event details, but it can also work with the external Redis storage.
2. Provision the Redis service through Service Catalog and use it as an alternative database for the microservice.
3. Connect an external mock application to Kyma as an addon. We will use it to send events with order delivery details to the microservice.
4. Create a Function with the logic similar to that of the microservice. You will see how it, too, can be triggered by order events from the mock application and how it can save the order details in the external storage.

Source: https://kyma-project.io/docs/1.20/root/getting-started/ 

-----------------