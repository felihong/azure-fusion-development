---
title: Backend deployment and architecture
layout: page
permalink: /architecture/
nav_order: 3
---

## Environment check

After finishing the [Lab pre-work](https://github.com/felihong/taw-power-apps-power-platform/blob/main/setup/README.md), you should have the following resources deployed in your Azure in the region specified during deployment:
- Resource group 
- API management service
- Cosmos DB account
- App service plan
- App service

![Azure deployed resources](../assets/az-resource.png)

The deployed RESTful API handles two different resources:
- HealthChekcs `<urlroot>/HealthCheck`
- Patients `<urlroot>/Patient`

{: .note }
Initially, there is no data stored in the database. Navigate to `<urlroot>/Patient` and you will receive an empty list, which is fine and indicates a successful deployment.

We have included a [Postman collection](https://github.com/felihong/taw-power-apps-power-platform/blob/main/setup/TAW-PowerApps-Contoso.postman_collection.json){:target="_blank"} to test the API more comprehensively.
- To test the API locally, configure the variable named `urlroot` to `http://localhost:5000`
- Once deployed to Azure, you can test the deployed API by setting the `urlroot` to `https://<YOUR_APP_SERVICE>.azurewebsites.net`

{: .highlight }
Open the Postman collection and get familiar with the API. Discuss with your team and check other methods as below listed:

- [ ] Get all HealthChecks status
- [ ] Get a specific HealthChecks status
- [ ] Add HealthChecks status
- [ ] Get all Patients
- [ ] Get a specific Patient
- [ ] Add a new Patient
- [ ] Modify an existing Patient
- [ ] Delete a Patient


## Lab exercise
Next, we will finish the development of a proof of concept for the case study and prepare to present the demo. 

Consider the layered architecture of **Fusion development** (pro-code & low-code) and disucss with your team on how to design the solution to address customer objectives expanding the use of **Power Apps**. 

![Fusion layered architecture](../assets/fusion-architecture.png)

The following resource might be helpful for you:
- [Microsoft services architecture for APIs](https://learn.microsoft.com/en-us/azure/architecture/microservices/design/gateway){:target="_blank"}
- [Azure Functions with Canvas Power Apps](https://learn.microsoft.com/en-gb/power-platform/guidance/architecture/real-world-examples/azure-function-canvas){:target="_blank"}
- [API developer portal](https://learn.microsoft.com/en-us/azure/api-management/api-management-howto-developer-portal){:target="_blank"}
- [Create custom connectors from APIs](https://learn.microsoft.com/en-us/azure/api-management/export-api-power-platform){:target="_blank"}
- [API management documentation](https://learn.microsoft.com/en-us/azure/api-management/){:target="_blank"}
- [Use a custom connector from a Power Apps app](https://learn.microsoft.com/en-gb/connectors/custom-connectors/use-custom-connector-powerapps){:target="_blank"}