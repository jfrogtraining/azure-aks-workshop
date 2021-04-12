---
title: "Set up your Azure Cloud Shell"
chapter: false
weight: 414
pre: "<b>4.1.4 </b>"
---

Azure Cloud Shell is an interactive, authenticated, browser-accessible shell for managing Azure resources.

1. In your Azure Portal, click the Azure Cloud Shell button.

![Azure Cloud Shell Button](/images/azure-cloud-shell-button.png)

2. You will be prompted for a shell type. Choose **Bash**.

![Azure Cloud Shell Bash](/images/azure-cloud-shell-bash.png)

3. If this is your first time using Azure Cloud Shell, you will be prompted to create storage to support it. Go ahead and do this by clicking **Create storage** with the provided subscription. It will take a few minutes to set up the storage.

![Azure Cloud Shell Storage](/images/azure-cloud-shell-storage.png)

4. Click on **Show advanced settings**.

5. Use the existing **jfrog-azure-resource-xxx** group. Specify new unique values for storage and file share.

![Azure Cloud Shell Advanced](/images/azure-cloud-shell-advanced.png)

6. Click **Create storage**. Wait a few moments for the Azure Cloud Shell to be set up.

![Azure Cloud Shell Ready](/images/azure-cloud-shell-ready.png)

5. Execute the following command to list your Azure Resource groups. 

``
az group list
``

![Azure Resource Group Workshop](/images/azure-resource-group-workshop.png)

6. Note the resource group named _jfrog-azure-workshop-xxxx_ and the region/location. Copy these values. The resources that we create in this workshop will be created in this resource group and region.

7. Set environment variables for your resource group and region.

``
export REGION=<region/location>
``

``
export RESOURCE_GROUP=<resource group>
``

![Azure Environment Vars](/images/azure-env-vars.png)

{{% notice info %}}
A resource group is a container that holds related resources for an Azure solution. The resource group can include all the resources for the solution. Generally, add resources that share the same lifecycle to the same resource group so that you can easily deploy, update, and delete them as a group.
{{% /notice %}}




