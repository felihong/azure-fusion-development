# Power Platform Lab Setup Instructions

## Pre-requisites

- [.NET 7 SDK](https://dotnet.microsoft.com/download/dotnet/7.0)
- Bicep - [Install from PowerShell](https://learn.microsoft.com/azure/azure-resource-manager/bicep/install#azure-powershell)
- [Azure Az PowerShell Module](https://learn.microsoft.com/powershell/azure/install-az-ps)

## Folder Structure

In this folder, there are two files:

- AzureLabEnvironment.bicep
- Setup-AzureLabEnvironment.ps1

The PowerShell script will run the Bicep template to create the following resources:

- Azure App Service - running .NET 7
- Azure App Service Plan
- Azure Cosmos DB for NoSQL account
- API Management

**NOTE:** If you have to re-run this script multiple times, note that API Management resources are soft deleted. If you get into this situation, check this site for more details: <https://aka.ms/apimsoftdelete>.

The PowerShell script will also set up environment variables for the API to run locally as well as in Azure. It will deploy the API code to the Azure App Service.

## Deploy the Resources

To start, clone/download this repository to your local machine to run the script and deploy the relevant resources to Azure. 

**NOTE:**
Before you run the PowerShell script, log into the Azure portal and get your **Subscription ID** or your **Subscription Name**. You will need this for PowerShell to connect to your Azure account.

As a next step, you can deploy the resources using PowerShell scripts. Depending on the OS platform you use, run the following commands:

#### Windows user
```powershell
Set-Location -Path "<Local path to this repository root>\setup"
.\Setup-AzureLabEnvironment-Win.ps1
```
#### Linux/Mac user
```bash
pwsh
Set-Location -Path "<Local path to this repository root>\setup"
.\Setup-AzureLabEnvironment-Linux.ps1
```

## Run the API locally

You can run the API locally using following commands. Depending on the platform you use: 

#### Windows user
```powershell
cd ..\Contoso.Healthcare
dotnet run
```
#### Linux/Mac User
```bash
cd ../Contoso.Healthcare
dotnet run
```

The output of this command will show you the URL it is running on. By default, it should be `http://localhost:5000`.
Navigate to `http://localhost:5000/Patient`, you should be able to see an empty response returned as [], which indicates a successful test. 


## Testing the API with Postman

We have included a [Postman collection](./TAW-PowerApps-Contoso.postman_collection.json) to test the API.

- There is a variable named `urlroot` that is defaulted to `http://localhost:5000`. This is initially set up to test the API locally.
- Once deployed to Azure, you can set the `urlroot` to the `https://YOUR_APP_SERVICE.azurewebsites.net` URL to test the API in Azure.

## Deployment Troubleshooting

These are situations where you may run into problems and how you can fix them.

### Unable to resolve Nuget packages

Are you seeing this message?
```dotnetcli
Unable to resolve 'Microsoft.Azure.Cosmos (>= 3.31.2)' for 'net7.0' and this one Unable to resolve 'Swashbuckle.AspNetCore (>= 6.2.3)' for 'net7.0'. 
```

This means that Nuget can't get these packages for some reason.
Run this command to see what your Nuget source is:

```dotnetcli
dotnet nuget list source
```
If you do not see any listings for sources, you need to [add the main nuget.org feed](https://learn.microsoft.com/dotnet/core/tools/dotnet-nuget-add-source#examples) with this command:

```dotnetcli
dotnet nuget add source https://api.nuget.org/v3/index.json --name nuget.org
```
Once you add this Nuget source, then you should rerun the Setup script.

### AuthKeyOrResourceToken parameter is set to null

Are you seeing this message?
```dotnetcli
Unhandled exception. System.ArgumentNullException: Value cannot be null. (Parameter 'authKeyOrResourceToken')
```
This means the required environment variables are not set properlly. Which is by default, configured automatically by running the PowerShell script.
Make sure you have the following env variables configured:

```
- PowerAppsLabDatabaseName: HealthCheckDB
- PowerAppsLabContainerName: HealthCheck
- PowerAppsLabAccount: <COSMOS DB URL>
- PowerAppsLabKey: <COSMOS DB PRIMARY KEY>
```
For Windows: 
```
$env:PowerAppsLabDatabaseName ="HealthCheckDB"
$env:PowerAppsLabContainerName= "HealthCheck"
$env:PowerAppsLabAccount = <COSMOS DB URL>
$env:PowerAppsLabKey = <COSMOS DB PRIMARY KEY>
```

### Execute dotnet run command

Problem: Unhandled exception. System.ArgumentNullException: Value cannot be null. (Parameter 'authKeyOrResourceToken')
This means you aren't in the administrator mode of powershell. 
For that please execute on  Windows: 

```
Start-Process powershell -Verb runAs
set-executionpolicy Unrestricted
```
