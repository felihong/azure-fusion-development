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


## View custom connector in Power Platform
After exposing the API, go to [Power Apps portal](https://make.powerapps.com){:target="_blank"} and sign in with your organizational account.
Select `Custom connectors` from the left pane to see your generated custom connector to your Azure API Management API.

![APIM export](../assets/powerapps-connector.png)

Now we have the option to further refine and test the connector within Power Platform: Select the `pencil icon` to edit the custom connector. 
On the Definition screen, we need to define a search query string for people so that the Power App can search for character records by name. Select the GetPeople action, and in the Request section, select + Import from sample. Enter a sample request URL with the search query string: