---
title: Bring intelligence using AI builder
layout: page
permalink: /ai-builder/
nav_order: 5
---

In this part we will bring more intelligence to our health care App by enabling AI-empowered automatic `Health card reader`. This is done using the `Power Apps AI Builder`.

AI Builder is a Microsoft Power Platform capability that helps you improve your business performance by automating processes and predicting outcomes. By using AI Builder, you can quickly bring AI to your apps and flows that connect to your business data that is stored in the underlying data platform (Microsoft Dataverse) or in various cloud data sources, such as SharePoint, OneDrive, or Azure.

If you are not familiar with AI builder yet, follow the below link to start a self-paced module which will help you build an AI model from the beginning and will show you how to use it in your business without writing a single line of code:

<a href="https://learn.microsoft.com/en-us/training/modules/get-started-with-ai-builder/1-intro-ai-builder">Introduction to AI Builder</a>

## Create an AI Builder

To start, please create a new screen. The AI Builder components for canvas apps are available in Power Apps Studio and appear on the `Insert` tab when you build your canvas app. Please select `business card reader`. Press `Scan business card`. Now upload a card photo from your Laptop.

Then add a Label and try to select the name form the business card.

![Contoso canvas app](../assets/ai-builder.png)

You can use the AI Builder business card reader component to detect health care card and extract patient basic information. You can take photos directly in the component or load images that you've taken. Data is extracted and identified by using the properties containing:

- FullName
- FirstName
- LastName
- FullAddress
- Email
- MobilePhone
- OriginalImage
- Website
- Text (ext that appears on the button that activates the business card reader)

![Contoso canvas app](../assets/business-card.png)
