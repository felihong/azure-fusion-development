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
An example screen looks like the following, consisting of components such as `text label`, `rechtangle`, `image`, [control gallery](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/controls/control-gallery){:target="_blank"} and a [control button](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/controls/control-button){:target="_blank"}. 
In addition, a dataverse table is created as data source for the control gallery, consisting information of health care categories like title, subtitle, logos and so on. 

![Example screen](../assets/example-screen.png)

Now we can add the health care API data source as follows:
- Select `Data` from the left pane and then select `+ Add data` from the drop-down menu.
- Search for the health care API in the search field and choose the connection to the API.
- Enter the API key if asked.

![Add contoso api](../assets/add-contoso-api.png)



## Get all patient records
Our custom API is now ready for use. We can test an API operation such as `getAllPatient`. The operation returns all existing patients in a list, and we can store the responses as a [collection](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/create-update-collection){:target="_blank"} to be used later. To archieve this, we need to define the control logic of the gallery component. 

Create a new screen in addition to the default one, rename it to for example `PatientProfileScreen`, this will be used to present the API call results. 
Select the `>` symbol of the vertical gallery, in the left pane drop-down menu, select the `OnSelect` action that will be executed when a user selects a category item from the gallery.
Navigate to `fx` input section and call the health care API function based on current context, navigate to the next screen and save the response as a collection:

```
Switch(
    ThisItem.Name, 
    "Get all patients", ClearCollect(patientCollection, ContosoHealthCareAPI.getAllPatient()); Navigate(PatientProfileScreen),
    false
);
```
The action result will be stored in a collection named `patientCollection`, you can check this results in the left panel, select `(X) -> Collections` and select the elipses to `View Table`. 

![Add contoso api](../assets/view-collection.png)

We will use this collection to present all patients' data in the `PatientProfileScreen`. Navigate to `Insert` on the top bar and select `Vertical gallery`. Choose the collection `patientCollection` as the data source. Modify the layouts and items to be presented in the control gallery. The following examples shows patient ID and name for each of the patient record. 

![Get patient result](../assets/get-result.png)



## Create a new patient record
Similarly, we can use the health care API post operation `addPatient` to generate a new patient profile. Create a new screen e.g. `AddPatientScreen` and design the screen layout with UI components. The following example uses `text label`, `rechtangle`, `image`, `control button`. In addition, [text input](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/controls/control-text-input){:target="_blank"} is used to handle user inputs containing patient information. 

To submit a post request, we need to modify the control button. Select again the `OnSelect` attribute of the button and define the activity as follows. 
This allows us to call the `addPatient` method of health care API, with colelcted patien Id and name as request payload. A `Reset` function is additionally used to clear up the user inputs. 

```
Navigate(HomeScreen);

ContosoHealthCareAPI.addpatient({
    patientid: input_patientid.Text,
    name: input_firstname.Text & " " & input_lastname.Text
});

Reset(input_patientid);
Reset(input_firstname);
Reset(input_lastname);
```

![Add patient request](../assets/post-request.png)


You can check whether the post request has been successfully handled by navigating to the `PatientProfileScrren`, there you should be able to see the freshly generated patient record. 


{: .highlight }
> So far, you have designed your health care App using `getAllPatient` and `addPatient` methods. Now try to finalize the App by extending with other API methods. 
> 
> Note that you need to modify the custom connector from both Azure API Management and Power Platform endpoints, and update the connection to your App.
>
> Good luck! :) 

