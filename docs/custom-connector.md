---
# title: Create a custom connector
title: Import a custom connector
layout: page
permalink: /custom-connector/
nav_order: 3
# has_children: true
---

<!-- In this exercise, you will be using the Consoto health care backend that you created in [part three](/azure-fusion-development/architecture/) of this lab. Patient profiles and health check statuses will be stored in the Cosmos database and serve as the primary backing data source for the application.

As a next step, you will configure the health care API gateway in **Azure API management** and export this as a **Power Platform Custom Connector**, so that the Power Apps Canvas app can access real-time patients and health check information. For each of the Patient, you can then search the patient profile and show information about health care status in the Canvas App. -->

In this exercise, you will be using the Consoto health care backend that provided by the engineering team. Patient profiles and health check statuses will be stored in a database hosted in Azure and serve as the primary backing data source for the application.

As a next step, you will configure the health care API by importing this as a **Power Platform Custom Connector**, so that the Power Apps Canvas app can access real-time patients and health check information. For each of the Patient, you can then search the patient profile and show information about health care status in the Canvas App.

<a href="https://github.com/felihong/azure-fusion-development/blob/main/docs/ContosoHealthCareApp_1_0_0_3.zip">Download Power Apps Solution</a>

After downloading, navigate to the `Solutions/Import Solution` to import the prepared solution to your environment.

![Contoso canvas app](../assets/import-solution.png)

Once the importing is completed, you should be able to see the health care `Custom Connector` which we can use in the next session.

![Contoso canvas app](../assets/after-import.png)
