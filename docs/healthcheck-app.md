---
title: Create a health check mobile application
layout: page
permalink: /fusion-application/
nav_order: 5
---

In this part, we will create a Power Apps canvas App that uses the custom connector created before. 
Back in the [Power Apps Editor](https://make.powerapps.com){:target="_blank"}, in the left pane, select `Home`. Under `Start from Blank app` , select `Create Blank canvas app`, enter a name for your app and select a format for it. After that, select `Create`, you will be redirected to an edit mode in the Power Apps Studio. Power Apps will generate a blank app with selected layout and a default screen. 

![Contoso canvas app](../assets/canvas-app.png)

You can design and configure the screen using the [UI conponents](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/power-apps-studio){:target="_blank"}. 
An example screen looks like the following, 

![Example screen](../assets/example-screen.png)



## Add the health care API data source
Now we can add the health care API data source as follows:
- Select `Data` from the left pane and then select `+ Add data` from the drop-down menu.
- Search for the health care API in the search field and choose the connection to the API.
- Enter the API key if asked.

![Add contoso api](../assets/add-contoso-api.png)

Our custom API is now ready for use. We can test an API operation such as `getAllPatient`. The operation returns all existing patients in a list, and we can store the responses as a [collection](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/create-update-collection){:target="_blank"} to be used later. 


