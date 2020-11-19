---
title: "Set up your Azure Cloud Shell"
chapter: false
weight: 414
pre: "<b>4.1.4 </b>"
---

Azure Cloud Shell is an interactive, authenticated, browser-accessible shell for managing Azure resources.

1. In your Azure Portal, click the Azure Cloud Shell button.

![Azure Cloud Shell Button](/images/azure-cloud-shell-button.png)

2. If this is your first time using Azure Cloud Shell, you will be prompted to mount storage to support it. Go ahead and do this by clicking **Create storage**. Ensure the correct subscription is selected. It will take a few minutes to set up the storage.

![Azure Cloud Shell Storage](/images/azure-cloud-shell-storage.png)

![Azure Cloud Shell Ready](/images/azure-cloud-shell-ready.png)

3. Execute the following command to show the default subscription. Ensure that the correct subscription is listed as default.

``
az account show
``

![Azure Account Shpw](/images/az-account-show.png)

4. Execute the following command to create a new Azure Resource group for our workshop. The resources that we create in this workshop will be created in this resource group.

``
az group create --name jfrog-azure-workshop --location westus
``

{{% notice info %}}
A resource group is a container that holds related resources for an Azure solution. The resource group can include all the resources for the solution. Generally, add resources that share the same lifecycle to the same resource group so you can easily deploy, update, and delete them as a group.
{{% /notice %}}




