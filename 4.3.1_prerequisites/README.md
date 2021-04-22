# Chapter 4.3.1: Prerequisites for implementation

The following steps will be performed to made the necessary prerequisities for the further implementation available: 

* Access to Kyma runtime on SAP Business Technology Platform
* Setup of the development tools
* Deploy the SAP Commerce Mock as consuming system into a Kyma Namespace

The setup is explained and documented in the follow further.


## Access to Kyma runtime on SAP Business Technology Platform

As the Kyma Runtime Environment on SAP Business Technology Platform (SAP BTP) should be used, the access to a system needs to be available. For this prototype a ([trial account of SAP BTP](https://www.sap.com/cmp/td/sap-cloud-platform-trial.html)) will be used. To access this account and activate the Kyma Runtime, the following steps have been performed:

1. Registration to the [trial version of SAP BTP](https://www.sap.com/cmp/td/sap-cloud-platform-trial.html)and creation of a new SAP S-User Account.

2. Login to the [trial version of SAP BTP](https://www.sap.com/cmp/td/sap-cloud-platform-trial.html) with the created S-User.

3. Enter your "Trial environment", go to "trial account" and click on "Enable Kyma". Enter a name for the new Kyma environment and click on "create" to create to Kyma environment. After around 30 minutes, the Kyma environment is provisioned and available on the SAP Business Technology Platform.

4. To be able to access the Kyma environment with the in newly created S-User account, access rights have to be granted as discribed under [Getting Started in the Kyma Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d1abd18556f24fb091d081b2e3454b8b.html).

5. Herefore two new roles "KymaRuntimeNamespaceAdmin" and "KymaRuntimeNamespaceDeveloper" have to be created and added to the role collection "Kyma_Admin_Role".

6. By further accessing the SAP BTP "Trust Configuration", select "Default identity provider", enter the S-User account id and assign the role collect "Kyma_Admin_Role" to it.

7. Go back to "Overview" and access the Kyma Environment in your Subaccount "trial" -> Kyma Environment -> "Link to dashboard". The Kyma Runtime Environment will be started and is ready.


## Setup of the development tools

The following tools have to be available, installed and configured for further administration and development with the Kyma Runtime Environment:

* Code editor, in this case Visual Studio Code is used.
* Command-line tool, in this case PowerShell is used.
* Further kubectl needs to be installed on the local machine and the ~.kube/config file needs to be configured with the Kubeconfig settings from the Kyma Runtime (Available under Kyma Environment -> Account -> Get Kubeconfig in the Kyma Environment).

**Note:** The further shown setup steps can be in the most cases performed by command-line and via the Kyma Runtime Environment User Interface.


## Deploy the SAP Commerce Mock as consuming system into a Kyma Namespace

To have a consuming e-commerce application, especially a SAP Commerce Cloud available, a mock version of it will be used. With this pre-configured and varkes-based [SAP-Commerce-Mock](https://blogs.sap.com/2020/06/17/sap-cloud-platform-extension-factory-kyma-runtime-mock-applications/) it is possible to trigger Events, send and receive data to and from the kyma-based Microservice. 

### Installation via Command Line

1. Create a new namespace with the following command in Kyma, dedicated for the SAP-Commerce-Mock.

```
kubectl create namespace sap-commerce-mock
```

2. Perform the following command, to deploy the [k8s.yaml](https://raw.githubusercontent.com/SAP/xf-application-mocks/master/commerce-mock/deployment/k8s.yaml) from the Github Repository [SAP-samples/xf-application-mocks](https://github.com/SAP-samples/xf-application-mocks/tree/master/commerce-mock) into the new namespace. This source code is also available in this repository under [ba-kyma-prototype/4.3.1_prerequisites/sap-commerce-mock/commerce-mock](https://github.com/klouisbrother/ba-kyma-prototype/tree/main/4.3.1_prerequisites/sap-commerce-mock/commerce-mock).

```
kubectl apply -f https://raw.githubusercontent.com/SAP/xf-application-mocks/master/commerce-mock/deployment/k8s.yaml -n sap-commerce-mock

```

3. Perform the following command, to deploy the [kyma.yaml](https://raw.githubusercontent.com/SAP/xf-application-mocks/master/commerce-mock/deployment/kyma.yaml) from the Github Repository [SAP-samples/xf-application-mocks](https://github.com/SAP-samples/xf-application-mocks/tree/master/commerce-mock) into the new namespace.

```
kubectl apply -f https://raw.githubusercontent.com/SAP/xf-application-mocks/master/commerce-mock/deployment/kyma.yaml -n sap-commerce-mock
```

4. After some minutes, the SAP-Commerce-Mock application is ready and can be accessed via the URL under "Discovery and Network" -> "API Rules" as displayed in the following screenprint.

![](images/01_01_SAP-Commerce-Mock-Start.png)


## Sources

* Guide: [SAP Blogs: SAP Cloud Platform, Kyma runtime: Mock Applications](https://blogs.sap.com/2020/06/17/sap-cloud-platform-extension-factory-kyma-runtime-mock-applications)
* Repository: [SAP-samples/xf-application-mocks/commerce-mock](https://github.com/SAP-samples/xf-application-mocks/tree/master/commerce-mock) and cloned into this Repository under [ba-kyma-prototype/4.3.1_prerequisites/sap-commerce-mock/commerce-mock](https://github.com/klouisbrother/ba-kyma-prototype/tree/main/4.3.1_prerequisites/sap-commerce-mock/commerce-mock)


## Summary and next step

With this chapter the SAP Commerce Mock as consuming and monolithic e-commerce application was provisioned. As next step the implementation of the Microservice will be performed.

[Next - Chapter 4.3.2: Implementation of the Microservice](https://github.com/klouisbrother/ba-kyma-prototype/tree/main/4.3.2_implementation/4.3.2_implementation.md) 