# Consume data from API using Azure Functions

## Azure Data Factory integration with Azure Functions
In this workshop we will use [Azure Data Factory](https://docs.microsoft.com/en-us/azure/data-factory/introduction) and [Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview) to copy, prepare and enrich data.

Azure Data Factory is a cloud-based ETL and data integration service that allows you to create data-driven workflows for orchestrating data movement and transforming data at scale.  Using Azure Data Factory, you can create and schedule data-driven workflows (called pipelines) that can ingest data from disparate data stores.

Azure Functions is a serverless solution that allows you to write less code, maintain less infrastructure, and save on costs. Instead of worrying about deploying and maintaining servers, the cloud infrastructure provides all the up-to-date resources needed to keep your applications running.

You focus on the pieces of code that matter most to you, and Azure Functions handles the rest.

### Prerequisites
Access to an Azure Subscription containing the following resources:
- [Azure Data Factory](https://docs.microsoft.com/en-us/azure/data-factory/introduction)
- [Azure Storage Account](https://docs.microsoft.com/en-us/azure/storage/common/storage-introduction) 
- [Azure Function App](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview)

### Provisioning Resources
- [Provision Resource Group](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal)
- [Provision Azure Storage Account](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-create?tabs=azure-portal)
- [Provision Azure Function App with Node.js stack](https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-first-azure-function)
- [Provision Azure Data Factory](https://docs.microsoft.com/en-us/azure/data-factory/quickstart-create-data-factory-portal)

### Objectives
The goal of this workshop is to provide a step-by-step guidance for creating an ADF pipeline that integrates with an Azure Function to process calls to an API and saves the resultsto a blob storage container. Data is then ingested to an Azure SQL database and processed.

## Task List
 - Create Azure Function
 - Install npm packages 
 - Configure Blob Storage Connection
 - Test code
 - Create ADF Pipeline
 - Run the pipeline


---
**Make sure that when you created your Azure Function App the Node.js stack was selected**
![Azure Function node.js stack](media/api-Image001.png)
---

### Create Azure Function
1. Log into your Azure Portal and navigate to the Azure function APP you created in the pre-requesites section. 

2. Once on your Function App, on the left blade select functions
![Add New Function](media/api-image-create-function.png)
 
3. Your will see an empty azure function template
![Function Empty Function Template](media/api-newfunction.png)
  
4. Replace the template code with the code below
  ```javascript
const fetch = require('node-fetch');
const request = require('request');

async function fetch_donations (context) {
    let donations = '';
    
    var options = {
        'method': 'GET',
        'url': 'https://apidemolgbac.azurewebsites.net/api/donations',
        'headers': {
                    'Content-Type': 'application/json',
                    'Cookie': 'ARRAffinity=16e562c458425ec1d6a20aaca9e7bd954e17407cc0191509cea5131e8c76a472; ARRAffinitySameSite=16e562c458425ec1d6a20aaca9e7bd954e17407cc0191509cea5131e8c76a472'
                   }//,
        //body: JSON.stringify({"name":"api demo","isComplete":true})
        };
    
    let url = '';
    url = 'https://apidemolgbac.azurewebsites.net/api/donations';
    
    context.log('url', url);
    await fetch(url, options).then(async response =>{
               const json  = await response.json();               
               donations = json;    
               })

.catch((error) => {
     context.log("error",error);    
      });
return [donations];
}

module.exports = async function (context, req) {
    context.log('JavaScript HTTP trigger function processed a request.');
    const responseMessage = await fetch_donations (context);
    context.log(responseMessage[0]);
    context.bindings.outputBlob = responseMessage[0];

    const endStatus = "This HTTP triggered function executed successfully. File saved to storage";
    context.res = {
      status: 200,
      body: endStatus
    };  
    context.done();
}
```
5. Save your function code
![Save function code](media/api-new-function-code.png)


## Back to workshop overview: [Introduction to Azure Data Factory Workshop](readme.md)
