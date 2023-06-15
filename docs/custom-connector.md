---
title: Create a custom connector
layout: page
permalink: /custom-connector/
nav_order: 4
has_children: true
---

In this exercise, you will be using the Consoto health care backend that you created in [part three](/azure-fusion-development/architecture/) of this lab. Patient profiles and health check statuses will be stored in the Cosmos database and serve as the primary backing data source for the application.

As a next step, you will configure the health care API gateway in **Azure API management** and export this as a **Power Platform Custom Connector**, so that the Power Apps Canvas app can access real-time patients and health check information. For each of the Patient, you can then search the patient profile and show information about health care status in the Canvas App.