---
title: Create a custom connector
layout: page
permalink: /custom_connector/
nav_order: 4
---

In this exercise, you will be using the Consoto health care API with Azure API management instance that you created in [part three](/taw-power-apps-power-platform/architecture/) of this lab. Patient profiles and health check statuses will be stored in the Cosmos database and serve as the primary backing data source for the application.

As a next step, you will configure the health care API gateway in **Azure API management** and export this as a **Power Platform Custom Connector**, so that the **Canvas App** can access real-time patients and health check information. For each of the Patient, you can then search the patient profile and show information about health care status in the Canvas App.


## API Management
An API represents a set of operations that can be invoked. New APIs are defined, and then the desired operations are added. An API is added to a product and can be published; it may then be subscribed to and used by developers.

Navigate to the APIs blade on the left menu, you will see all existing APIs. Here one has various options to create a new API, either to create an API from scratch, or to import an API from Azure resource:
- [Add an API manually](https://learn.microsoft.com/en-us/azure/api-management/add-api-manually){:target="_blank"}
- [Import an OpenAPI specification](https://learn.microsoft.com/en-us/azure/api-management/import-api-from-oas?tabs=portal){:target="_blank"} (aka Swagger)
- [Import an Azure Web App as an API](https://learn.microsoft.com/en-us/azure/api-management/import-app-service-as-api){:target="_blank"}
- [Import an Function App as an API](https://learn.microsoft.com/en-us/azure/api-management/import-function-app-as-api){:target="_blank"}
- [Import a Logic App as an API](https://learn.microsoft.com/en-us/azure/api-management/import-logic-app-as-api){:target="_blank"}

As we have deployed our Contoso health care .NET system to Azure App service, in the following, we will show you how to import an Azure Web App to API management. And test the imported API using the Azure portal.
Azure App Service is an HTTP-based service for hosting web applications, REST APIs, and mobile backends. API developers can use their preferred technology stacks and pipelines to develop APIs and publish their API backends as Web Apps in a secure, scalable environment. Then, use API Management to expose the Web Apps, manage and protect the APIs throughout their lifecycle, and publish them to consumers.

API Management is the recommended environment to expose a Web App-hosted API, for several reasons:
- Decouple managing and securing the front end exposed to API consumers from managing and monitoring the backend Web App
- Manage web APIs hosted as Web Apps in the same environment as your other APIs
- Apply policies to change API behavior, such as call rate limiting
- Direct API consumers to API Management's customizable developer portal to discover and learn about your APIs, request access, and try them


## Import a Web App hosted in App Service 
Follow the next steps to import and publish the Contoso health care backend API:
- Navigate to your API Management service in the Azure portal and select APIs blade from the menu. And select `App Service` from the list.

![APIM app service](../assets/app-service.png)
![APIM creation](../assets/apim-creation.png)

- Select `Browse` to see the list of App Services in your subscription. Select an App Service. If an OpenAPI definition is associated with the selected Web App, API Management fetches it and imports it. If an OpenAPI definition isn't found, API Management exposes the API by generating wildcard operations for common HTTP verbs.
- Add an `API URL suffix`. The suffix is a name that identifies this specific API in this API Management instance. It has to be unique in this APIM instance.
- Publish the API by associating the API with a product. In this case, the "Unlimited" product is used. If you want the API to be published and be available to developers, add it to a product. You can do it during API creation or set it later.

{: .note }
> Products are associations of one or more APIs. You can include many APIs and offer them to developers through the developer portal. Developers must first subscribe to a product to get access to the API. When they subscribe, they get a subscription key that is good for any API in that product. 
> If you created the APIM instance, you are an administrator already, so you are subscribed to every product by default.
>
> By default, each API Management instance comes with two sample products:
> - Starter
> - Unlimited

- Enter other API settings. You can set the values during creation or configure them later by going to the Settings tab. For more information of the settings check [Import and publish](https://learn.microsoft.com/en-us/azure/api-management/import-and-publish#import-and-publish-a-backend-api){:target="_blank"}

![APIM creation](../assets/apim-config.png)

- Verify and modify all the operations in the design blade. The following examples showcase two methods: `GetAllPatient` and `AddPatient`. For the post request, don't forget also to define request content types (in our case application/json), examples and schemas. You may configure the methods as follows:

![APIM creation](../assets/apim-get.png)

![APIM creation](../assets/apim-post.png)


## Test the API in the Azure portal
After the configuration, we can now test the new API in the Azure portal. Select the API you created in the previous step. Then select the `Test` tab. Select an operation to be tested, the page displays fields for query parameters, fields for the headers, and request body. After entering all data, press `Send` button, when the test is successful, the backend responds with HTTP 200 OK status and some data.

![APIM creation](../assets/apim-test-post.png)

![APIM creation](../assets/apim-test-get.png)



{: .highlight }
> Discuss with your team and add further operations from the health care backend API:
>
> - [ ] Get all HealthChecks status
> - [ ] Get a specific HealthChecks status
> - [ ] Add HealthChecks status
> - [ ] Get all Patients
> - [ ] Get a specific Patient
> - [ ] Add a new Patient
> - [ ] Modify an existing Patient
> - [ ] Delete a Patient


## Create a custom connector
From the existing Star Wars API Api in Azure API Management, click the ellipsis … and select the Create Power Connector option to generate a custom connector in your Power Platform environment.