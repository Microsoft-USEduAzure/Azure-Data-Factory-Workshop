# Introduction to Azure Data Factory Workshop

## Azure Data Factory

In this workshop we will use [Azure Data Factory](https://docs.microsoft.com/en-us/azure/data-factory/introduction) to copy, prepare and enrich data.

Azure Data Factory is a cloud-based ETL and data integration service that allows you to create data-driven workflows for orchestrating data movement and transforming data at scale.  Using Azure Data Factory, you can create and schedule data-driven workflows (called pipelines) that can ingest data from disparate data stores.

### Prerequisites
Access to an Azure Subscription containing the following resources:
- [Azure Data Factory](https://docs.microsoft.com/en-us/azure/data-factory/introduction)
- [Azure Data Lake Storage Gen2](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction) 
### Optional

- [Visual Studio Code](https://code.visualstudio.com/Download)
- [Windows Terminal](https://docs.microsoft.com/en-us/windows/terminal/get-started)
- [Azure Storage Explorer](https://azure.microsoft.com/en-us/features/storage-explorer/)


### Provision Resources

- [Provision Resource Group](provision-resource-group.md)
- [Provision Azure Data Lake Storage Gen2](provision-adlsg2.md)
- [Provision Azure Data Factory](provision-adf.md)

### Metadata driven pipeline

- [Use Azure Data Factory](metadata-driven-pipeline.md) to:
  - Create Linked Servers
  - Create Data Sources
  - ...

### Mapping Data Flow

- [Use Azure Data Factory](mapping-data-flow.md) to:
  - Create Source
  - Create Derived Column
  - ...

### Consume data from API using Azure Functions

- [Use Azure Data Factory](api-pipeline.md) to:
  - Create Linked Servers
  - Create Web Activity
  - ...

### References

- [Create a trigger that runs a pipeline in response to an event](https://docs.microsoft.com/en-us/azure/data-factory/how-to-create-event-trigger)
- [Enable Event Grid resource provider](https://docs.microsoft.com/en-us/azure/event-grid/custom-event-to-eventhub#enable-event-grid-resource-provider)
- [Azure Data Factory - YouTube Channel](https://www.youtube.com/channel/UC2S0k7NeLcEm5_IhHUwpN0g)
