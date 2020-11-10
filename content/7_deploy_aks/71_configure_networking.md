---
title: "Configure AKS Cluster Networking"
chapter: false
weight: 71
pre: "<b>7.1 </b>"
---

Before deploying an AKS cluster for the NPM application, we must first set up the require networking with the following steps.

1. On your build machine in your Azure Cloud Shell, let's first set some common environment variables. Execute the following.

```
REGION_NAME=westus
RESOURCE_GROUP=azureworkshop
SUBNET_NAME=aks-subnet
VNET_NAME=aks-vnet
```

2. Next, execute the following command to create a virtual network for the AKS cluster.

```
az network vnet create \
    --resource-group $RESOURCE_GROUP \
    --location $REGION_NAME \
    --name $VNET_NAME \
    --address-prefixes 10.0.0.0/8 \
    --subnet-name $SUBNET_NAME \
    --subnet-prefixes 10.240.0.0/16
```

3. Retrieve and store the resultant subnet ID in an environment variable.

```
SUBNET_ID=$(az network vnet subnet show \
    --resource-group $RESOURCE_GROUP \
    --vnet-name $VNET_NAME \
    --name $SUBNET_NAME \
    --query id -o tsv)
echo $SUBNET_ID
```

