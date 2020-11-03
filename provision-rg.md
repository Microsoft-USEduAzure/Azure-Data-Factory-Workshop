# Provision Resource Group

## Task: Create resource group using Azure CLI

We will create a Resource Group called **rg-adf-workshop** - please select the nearest data center


1. In Azure Portal, open Cloud Shell

1. Execute the following command using Bash

    ```
    az group create -n rg-adf-workshop -l <ENTER_LOCATION_NAME>
    ```

## Next task: [Provision Azure Data Lake Storage Gen2](provision-adlsg2.md)