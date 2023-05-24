---
title: Power platform custom connector
layout: page
permalink: /custom-connector/power-platform
parent: Create a custom connector
nav_order: 2
---

After creating the Contoso health care API, we can create a **Custom connector** in a specific Power Platform environment.
From the Azure API Management, navigate to `APIs -> Power Platform` in the left blade and select `Create a connector`. This opens configuration page that gives options expose an API to connect to the Power Platform.

![Connector expose](../assets/connector-expose.png)

If you are unable to create a Power platform Connector from Azure API Management, you can also export the API to an `OpenAPI v2 (JSON)` (aka Swagger) specification file that can be imported as a Custom Connector within Power Platform, as shown below.

![APIM export](../assets/apim-export.png)


## Configure custom connector in Power Platform
After exposing the API, go to [Power Apps portal](https://make.powerapps.com){:target="_blank"} and sign in with your organizational account.
Select `Custom connectors` from the left pane to see your generated custom connector to your Azure API Management API.

![PowerApps connector](../assets/powerapps-connector.png)

Now we have the option to further refine and test the connector within Power Platform: Select the `pencil icon` to edit the custom connector.
Within Power Apps portal, we have the following aspects for the custom connector configuration:
- **General**: here one can add an icon and short description, choose HTTP(s) scheme.
- **Security**: define authentication type, multiple options are supported here, such as `no authentication` (bypass the key, only for testing), `basic authentication`, use `API key`, or `OAuth 2.0`.
- **Definition**: refine actions, references, and policies.
- **Code**: optional, custom code transforms request and response payloads beyond the scope of policy templates.
- **Test**: test a specified operation of this custom connector using the selected connection.

On the Definition screen, select the `getAllPatient` action, and in the `Request` section, select `+ Import from sample`. Enter a sample request URL `https://<Your-App-Name>.azure-api.net/Patient`:

![Get patient](../assets/get-all-patient.png)

In the Response section of the getAllPatient action, select the `200 response` and then select `+ Import from sample`. Copy and paste a sample JSON response into the `Body` section of the response. Close the import panel and select `Update connector`.

![Get patient response](../assets/get-all-patient-response.png)

Similiar approach can be used to update further actions. In the `Request` section of the `addPatient` action, select `+ Import from sample`. Enter a sample request URL `https://<Your-App-Name>.azure-api.net/Patient`, copy and paste a sample JSON payload into the `Body` section of the request:

![Add patient](../assets/add-patient.png)

For the response section you can repeat the previous approach to configure a 200 response by importing a sample snippet. Don't forget to select `Update connector` to make all the changes effective.



## Test the custom connector
On the `Test screen`, create a new connection instance in the Connections section. You will be asked to provide an API key for the health care API, which you can extract in the Azure portal of API management. Navigate to `APIs -> Subscriptions` and click on the eclipses `...` to select `Show/hide keys`. Copy and paste this key backto Power Apps portal to finish the connection creation.

![Create connection](../assets/connection.png)

![Subscription key](../assets/subscription-key.png)

After that, you can test each of the operations using the generated connection. 

![Subscription key](../assets/connector-test.png)


{: .highlight }
Now it's time for you to import further operations and refine them in the Power Apps portal.